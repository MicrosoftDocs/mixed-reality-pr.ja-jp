---
title: DirectX でのレンダリング
description: Windows Mixed Reality の holographic レンダリングについて説明します。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, ホログラム, レンダリング, 3D グラフィックス, HolographicFrame, レンダリングループ, 更新ループ, チュートリアル, サンプルコード, Direct3D
ms.openlocfilehash: 90d665e8054a185969a95e6ff6415979e728e9ab
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613186"
---
# <a name="rendering-in-directx"></a>DirectX でのレンダリング

> [!NOTE]
> この記事は、従来の WinRT ネイティブ Api に関連しています。  新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](openxr-getting-started.md)** を使用することをお勧めします。

Windows Mixed Reality は DirectX 上に構築されており、ユーザーに対して豊富な3D グラフィカルエクスペリエンスを生み出します。 レンダリングの抽象化は DirectX のすぐ上にあり、システムによって予測された holographic シーンオブザーバーの位置と向きに関するアプリの理由を示します。 開発者は、各カメラに基づいてホログラムを見つけることができます。これにより、アプリは、ユーザーが移動するときに、さまざまな空間座標系でこれらのホログラムをレンダリングします。

メモ: このチュートリアルでは、Direct3D 11 での holographic レンダリングについて説明します。 Direct3D 12 Windows Mixed Reality アプリテンプレートには、Mixed Reality アプリテンプレート拡張機能も用意されています。

## <a name="update-for-the-current-frame"></a>現在のフレームの更新

ホログラムのアプリケーションの状態を更新するには、次のようにします。
* 表示管理システムから <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> を取得します。
* レンダリングが完了したら、カメラビューが配置されるの現在の予測でシーンを更新します。 Holographic シーンでは、複数のカメラを使用できます。

Holographic カメラビューにレンダリングするには、アプリがフレームごとに1回、次のようになります。
* カメラごとに、システムのカメラビューと投影行列を使用して、現在のフレームのシーンをレンダリングします。

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a>新しい holographic フレームを作成し、予測を取得する

<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>には、アプリが現在のフレームを更新して表示するために必要な情報が含まれています。 アプリは、 **Createnextframe** メソッドを呼び出すことによって、各新しいフレームを開始します。 このメソッドが呼び出されると、予測は、使用可能な最新のセンサーデータを使用して作成され、 **currentprediction** オブジェクトにカプセル化されます。

レンダリングされた各フレームは、瞬時に有効であるため、新しいフレームオブジェクトを使用する必要があります。 **Currentprediction** プロパティには、カメラの位置などの情報が含まれています。 この情報は、フレームがユーザーに表示されることが予想される正確な時点に対して推定されます。

次のコードは、 **Appmain:: Update** から抜粋ですされています。

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a>カメラの更新の処理

バックバッファーはフレーム間で変更される可能性があります。 アプリでは、各カメラのバックバッファーを検証し、必要に応じてリソースビューと深度バッファーを解放して再作成する必要があります。 予測に含まれる一連の設定が、現在のフレームで使用されているカメラの権限の一覧になっていることに注意してください。 通常、この一覧を使用して、カメラのセットを反復処理します。

**Appmain:: Update** から:

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

**DeviceResources:: EnsureCameraResources** から:

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a>描画の基準として使用する座標系を取得します。

Windows Mixed Reality を使用すると、アプリは、物理的な世界での場所を追跡するために、接続された、静止した参照フレームなどのさまざまな [座標系](coordinate-systems-in-directx.md)を作成できます。 これにより、アプリはこれらの座標系を使用して、各フレームのホログラムのレンダリングを行うことができます。 API から座標を要求するときは、その座標を表現する <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> を常に渡す必要があります。

**Appmain:: Update** から:

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

これらの座標系を使用して、シーンにコンテンツをレンダリングするときに、ステレオビュー行列を生成できます。

**CameraResources:: UpdateViewProjectionBuffer** から:

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a>プロセスの宝石とジェスチャの入力

手書き入力と [手動](hands-and-motion-controllers-in-directx.md)入力は時間ベースでは [なく、](gaze-in-directx.md) **steptimer** 関数で更新する必要はありません。 ただし、この入力は、アプリが各フレームを確認する必要があります。

### <a name="process-time-based-updates"></a>プロセス時間ベースの更新

リアルタイムレンダリングアプリでは、時間ベースの更新を処理するために何らかの方法が必要です。 Windows Holographic アプリケーションテンプレートでは、DirectX 11 UWP アプリケーションテンプレートに用意されている StepTimer と同様に、 **steptimer** 実装が使用されます。 このサンプルヘルパークラスは、固定された時間ステップの更新、時間の経過に伴う時間の更新、既定のモードは変動する時間のステップを提供します。

Holographic のレンダリングでは、タイマー関数を固定の時間ステップとして構成できるので、タイマー関数にあまり多くを入れないことを選択しました。 フレームごとに複数回呼び出される場合があります。また、フレームによっては、holographic データの更新がフレームごとに1回行われる必要があります。


**Appmain:: Update** から:

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a>座標系でのホログラムの位置と回転

1つの座標系で運用している場合は、テンプレートが **SpatialStationaryReferenceFrame** を使用しているため、このプロセスは3d グラフィックスで使用していたものとは異なります。 ここでは、立方体を回転させ、固定の座標系の位置に基づいてモデルマトリックスを設定します。

**SpinningCubeRenderer:: Update** から:

```cpp
// Rotate the cube.
// Convert degrees to radians, then convert seconds to rotation angle.
const float    radiansPerSecond = XMConvertToRadians(m_degreesPerSecond);
const double   totalRotation = timer.GetTotalSeconds() * radiansPerSecond;
const float    radians = static_cast<float>(fmod(totalRotation, XM_2PI));
const XMMATRIX modelRotation = XMMatrixRotationY(-radians);

// Position the cube.
const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

// Multiply to get the transform matrix.
// Note that this transform does not enforce a particular coordinate system. The calling
// class is responsible for rendering this content in a consistent manner.
const XMMATRIX modelTransform = XMMatrixMultiply(modelRotation, modelTranslation);

// The view and projection matrices are provided by the system; they are associated
// with holographic cameras, and updated on a per-camera basis.
// Here, we provide the model transform for the sample hologram. The model transform
// matrix is transposed to prepare it for the shader.
XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(modelTransform));
```

**高度なシナリオに関する注意:** 回転するキューブは、1つの参照フレーム内にホログラムを配置する方法の簡単な例です。 同時に、レンダリングされた同じフレームで [複数の SpatialCoordinateSystems を使用](coordinate-systems-in-directx.md) することもできます。

### <a name="update-constant-buffer-data"></a>定数バッファーデータの更新

コンテンツのモデル変換は、通常どおりに更新されます。 ここまでで、レンダリングする座標系の有効な変換を計算しました。

**SpinningCubeRenderer:: Update** から:

```cpp
// Update the model transform buffer for the hologram.
context->UpdateSubresource(
    m_modelConstantBuffer.Get(),
    0,
    nullptr,
    &m_modelConstantBufferData,
    0,
    0
);
```

ビューとプロジェクションの変換について 最良の結果を得るために、描画呼び出しの準備が整うまで待機してから、これらを取得します。

## <a name="render-the-current-frame"></a>現在のフレームをレンダリングします

Windows Mixed Reality でのレンダリングは、2D mono ディスプレイでのレンダリングとは大きく異なりますが、いくつか違いがあります。
* Holographic フレーム予測は重要です。 予測に近いほど、フレームが表示されるときに、ホログラムが見やすくなります。
* Windows Mixed Reality は、カメラビューを制御します。 Holographic フレームによって後で表示されるため、それぞれにレンダリングします。
* レンダーターゲット配列に描画するインスタンスを使用して、ステレオレンダリングを行うことをお勧めします。 Holographic アプリテンプレートでは、レンダーターゲット配列に描画するための推奨される方法を使用しています。レンダーターゲット配列は、レンダーターゲットビューを **Texture2DArray** に使用します。
* ステレオのインスタンス化を使用せずにレンダリングする場合は、2つの非配列 RenderTargetViews を作成する必要があります。 各 RenderTargetViews は、システムからアプリに提供される **Texture2DArray** 内の2つのスライスのうちの1つを参照します。 これは、通常、インスタンス化を使用するよりも低速であるため、推奨されません。

### <a name="get-an-updated-holographicframe-prediction"></a>更新された HolographicFrame 予測を取得する

フレーム予測を更新すると、イメージの安定化の効果が向上します。 ホログラムがより正確に配置されるのは、予測とフレームがユーザーに表示される時間が短くなるためです。 レンダリングの直前にフレーム予測を更新するのが理想的です。

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a>各カメラにレンダリングする

一連のカメラでループし、予測を行い、このセット内の各カメラにレンダリングします。

**レンダリングパスを設定する**

Windows Mixed Reality は、ステレオスコピックレンダリングを使用して奥行の錯覚を強化し、stereoscopically をレンダリングします。そのため、左と右の両方の表示がアクティブです。 ステレオスコピックレンダリングでは、2つのディスプレイの間にオフセットがあります。これは、脳が実際の深さとして調整できます。 このセクションでは、Windows Holographic アプリテンプレートのコードを使用して、インスタンス化を使用したステレオスコピックレンダリングについて説明します。

各カメラは、独自のレンダーターゲット (バックバッファー) と、ビューおよび投影マトリックスを holographic 空間に持ちます。 アプリでは、カメラごとに、深度バッファーなどの他のカメラベースのリソースを作成する必要があります。 Windows Holographic アプリテンプレートでは、これらのリソースを DX:: CameraResources にまとめてバンドルするヘルパークラスを提供しています。 まず、レンダーターゲットビューを設定します。

**Appmain:: Render** から:

```cpp
// This represents the device-based resources for a HolographicCamera.
DX::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

// Get the device context.
const auto context = m_deviceResources->GetD3DDeviceContext();
const auto depthStencilView = pCameraResources->GetDepthStencilView();

// Set render targets to the current holographic camera.
ID3D11RenderTargetView *const targets[1] =
    { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, depthStencilView);

// Clear the back buffer and depth stencil view.
if (m_canGetHolographicDisplayForCamera &&
    cameraPose.HolographicCamera().Display().IsOpaque())
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::CornflowerBlue);
}
else
{
    context->ClearRenderTargetView(targets[0], DirectX::Colors::Transparent);
}
context->ClearDepthStencilView(
    depthStencilView, D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);
```

**予測を使用して、カメラのビューおよび投影行列を取得します。**

各 holographic カメラのビューおよび投影マトリックスは、すべてのフレームで変更されます。 各 holographic カメラの定数バッファーのデータを更新します。 この操作は、予測を更新した後、そのカメラの描画呼び出しを行う前に行います。

**Appmain:: Render** から:

```cpp
// The view and projection matrices for each holographic camera will change
// every frame. This function refreshes the data in the constant buffer for
// the holographic camera indicated by cameraPose.
if (m_stationaryReferenceFrame)
{
    pCameraResources->UpdateViewProjectionBuffer(
        m_deviceResources, cameraPose, m_stationaryReferenceFrame.CoordinateSystem());
}

// Attach the view/projection constant buffer for this camera to the graphics pipeline.
bool cameraActive = pCameraResources->AttachViewProjectionBuffer(m_deviceResources);
```

ここでは、カメラによってどのように行列が取得されるかを説明します。 このプロセスでは、カメラの現在のビューポートも取得します。 座標系をどのように提供しているかに注意してください。これは、宝石を理解するために使用したものと同じ座標系であり、回転しているキューブの配置に使用したものと同じです。


**CameraResources:: UpdateViewProjectionBuffer** から:

```cpp
// The system changes the viewport on a per-frame basis for system optimizations.
auto viewport = cameraPose.Viewport();
m_d3dViewport = CD3D11_VIEWPORT(
    viewport.X,
    viewport.Y,
    viewport.Width,
    viewport.Height
);

// The projection transform for each frame is provided by the HolographicCameraPose.
HolographicStereoTransform cameraProjectionTransform = cameraPose.ProjectionTransform();

// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);

// If TryGetViewTransform returns a null pointer, that means the pose and coordinate
// system cannot be understood relative to one another; content cannot be rendered
// in this coordinate system for the duration of the current frame.
// This usually means that positional tracking is not active for the current frame, in
// which case it is possible to use a SpatialLocatorAttachedFrameOfReference to render
// content that is not world-locked instead.
DX::ViewProjectionConstantBuffer viewProjectionConstantBufferData;
bool viewTransformAcquired = viewTransformContainer != nullptr;
if (viewTransformAcquired)
{
    // Otherwise, the set of view transforms can be retrieved.
    HolographicStereoTransform viewCoordinateSystemTransform = viewTransformContainer.Value();

    // Update the view matrices. Holographic cameras (such as Microsoft HoloLens) are
    // constantly moving relative to the world. The view matrices need to be updated
    // every frame.
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[0],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Left) *
            XMLoadFloat4x4(&cameraProjectionTransform.Left))
    );
    XMStoreFloat4x4(
        &viewProjectionConstantBufferData.viewProjection[1],
        XMMatrixTranspose(XMLoadFloat4x4(&viewCoordinateSystemTransform.Right) *
            XMLoadFloat4x4(&cameraProjectionTransform.Right))
    );
}
```

ビューポートは、各フレームに設定する必要があります。 通常、頂点シェーダー (少なくとも) は、ビュー/プロジェクションデータへのアクセスを必要とします。


**CameraResources:: AttachViewProjectionBuffer** から:

```cpp
// Set the viewport for this camera.
context->RSSetViewports(1, &m_d3dViewport);

// Send the constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    1,
    1,
    m_viewProjectionConstantBuffer.GetAddressOf()
);
```

**カメラのバックバッファーにレンダリングし、深度バッファーをコミットし** ます。

ビュー/プロジェクションデータを使用する前に **Trygetviewtransform** が成功したことを確認することをお勧めします。これは、座標系の位置が正しくない (たとえば、追跡が中断された) 場合、アプリはそのフレームではレンダリングできないためです。 **CameraResources** クラスが正常に更新されたことを示している場合、このテンプレートは回転しているキューブに対してのみ **Render** を呼び出します。

Windows Mixed Reality には、開発者やユーザーが配置したホログラムをどこに配置しても、 [イメージを安定化](../platform-capabilities-and-apis/hologram-stability.md) させておくための機能が含まれています。 イメージの安定化は、ユーザーに最適な holographic エクスペリエンスを確保するために、レンダリングパイプラインに固有の待機時間を非表示にするのに役立ちます。 さらに、イメージの安定化をさらに強化するためにフォーカスポイントを指定することも、最適化されたイメージ安定化をリアルタイムで計算するために深度バッファーを指定することもできます。

最良の結果を得るために、アプリは <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API を使用して深度バッファーを提供する必要があります。 Windows Mixed Reality は、深度バッファーからのジオメトリ情報を使用して、イメージの安定化をリアルタイムで最適化できます。 Windows Holographic アプリテンプレートでは、アプリの深度バッファーが既定でコミットされるため、ホログラムの安定性が最適化されます。

**Appmain:: Render** から:

```cpp
// Only render world-locked content when positional tracking is active.
if (cameraActive)
{
    // Draw the sample hologram.
    m_spinningCubeRenderer->Render();
    if (m_canCommitDirect3D11DepthBuffer)
    {
        // On versions of the platform that support the CommitDirect3D11DepthBuffer API, we can 
        // provide the depth buffer to the system, and it will use depth information to stabilize 
        // the image at a per-pixel level.
        HolographicCameraRenderingParameters renderingParameters =
            holographicFrame.GetRenderingParameters(cameraPose);
        
        IDirect3DSurface interopSurface =
            DX::CreateDepthTextureInteropObject(pCameraResources->GetDepthStencilTexture2D());

        // Calling CommitDirect3D11DepthBuffer causes the system to queue Direct3D commands to 
        // read the depth buffer. It will then use that information to stabilize the image as
        // the HolographicFrame is presented.
        renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
    }
}
```

>[!NOTE]
>Windows は GPU で深度テクスチャを処理するため、深度バッファーをシェーダーリソースとして使用できるようにする必要があります。 作成する ID3D11Texture2D は、型が指定されていない形式である必要があり、シェーダーリソースビューとしてバインドされている必要があります。 イメージの安定化のためにコミットできる深度テクスチャを作成する方法の例を次に示します。

**CommitDirect3D11DepthBuffer の深度バッファーリソースの作成** コード:

```cpp
// Create a depth stencil view for use with 3D rendering if needed.
CD3D11_TEXTURE2D_DESC depthStencilDesc(
    DXGI_FORMAT_R16_TYPELESS,
    static_cast<UINT>(m_d3dRenderTargetSize.Width),
    static_cast<UINT>(m_d3dRenderTargetSize.Height),
    m_isStereo ? 2 : 1, // Create two textures when rendering in stereo.
    1, // Use a single mipmap level.
    D3D11_BIND_DEPTH_STENCIL | D3D11_BIND_SHADER_RESOURCE
);

winrt::check_hresult(
    device->CreateTexture2D(
        &depthStencilDesc,
        nullptr,
        &m_d3dDepthStencil
    ));

CD3D11_DEPTH_STENCIL_VIEW_DESC depthStencilViewDesc(
    m_isStereo ? D3D11_DSV_DIMENSION_TEXTURE2DARRAY : D3D11_DSV_DIMENSION_TEXTURE2D,
    DXGI_FORMAT_D16_UNORM
);
winrt::check_hresult(
    device->CreateDepthStencilView(
        m_d3dDepthStencil.Get(),
        &depthStencilViewDesc,
        &m_d3dDepthStencilView
    ));
```

**Holographic コンテンツの描画**

Windows Holographic アプリテンプレートは、インスタンス化されたジオメトリをサイズ2の Texture2DArray に描画するための推奨される方法を使用して、ステレオでコンテンツをレンダリングします。 ここでは、こののインスタンス化の部分と、それが Windows Mixed Reality でどのように動作するかを見てみましょう。

**SpinningCubeRenderer:: Render** から:

```cpp
// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

各インスタンスは、定数バッファーから異なるビュー/プロジェクション行列にアクセスします。 次に示すのは、2つの行列の配列である定数バッファー構造です。

**VPRTVertexShader** に含まれる **VertexShaderShared** から:

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

レンダーターゲットの配列インデックスは、ピクセルごとに設定する必要があります。 次のスニペットでは、viewId が **SV_RenderTargetArrayIndex** セマンティックにマップされています。 これには、オプションの Direct3D 11.3 機能がサポートされている必要があります。これにより、任意のシェーダーステージからレンダーターゲットの配列インデックスセマンティックを設定できます。

**VPRTVertexShader** から:

```HLSL    
// Per-vertex data passed to the geometry shader.
struct VertexShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;

    // The render target array index is set here in the vertex shader.
    uint        viewId  : SV_RenderTargetArrayIndex;
};
```

**VPRTVertexShader** に含まれる **VertexShaderShared** から:

```HLSL
// Per-vertex data used as input to the vertex shader.
struct VertexShaderInput
{
    min16float3 pos     : POSITION;
    min16float3 color   : COLOR0;
    uint        instId  : SV_InstanceID;
};

// Simple shader to do vertex processing on the GPU.
VertexShaderOutput main(VertexShaderInput input)
{
    VertexShaderOutput output;
    float4 pos = float4(input.pos, 1.0f);

    // Note which view this vertex has been sent to. Used for matrix lookup.
    // Taking the modulo of the instance ID allows geometry instancing to be used
    // along with stereo instanced drawing; in that case, two copies of each 
    // instance would be drawn, one for left and one for right.
    int idx = input.instId % 2;

    // Transform the vertex position into world space.
    pos = mul(pos, model);

    // Correct for perspective and project the vertex position onto the screen.
    pos = mul(pos, viewProjection[idx]);
    output.pos = (min16float4)pos;

    // Pass the color through without modification.
    output.color = input.color;

    // Set the render target array index.
    output.viewId = idx;

    return output;
}
```

この描画方法を使用して、既にインスタンス化されている描画手法をステレオレンダーターゲット配列に使用する場合は、通常持っているインスタンスの数を2倍にします。 シェーダーでは、 **入力した instId** を2で除算して元のインスタンス ID を取得します。これは、オブジェクトごとのデータのバッファーにインデックスを付けることができます。 `int actualIdx = input.instId / 2;`

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a>HoloLens でのステレオコンテンツのレンダリングに関する重要な注意事項

Windows Mixed Reality では、任意のシェーダーステージからレンダーターゲットの配列インデックスを設定する機能がサポートされています。 通常、これは、Direct3D 11 に対してセマンティックが定義されているため、ジオメトリシェーダーステージでのみ実行できるタスクです。 ここでは、頂点とピクセルシェーダーの両方のステージを設定してレンダリングパイプラインを設定する方法の完全な例を示します。 シェーダーコードは前述のとおりです。

**SpinningCubeRenderer:: Render** から:

```cpp
const auto context = m_deviceResources->GetD3DDeviceContext();

// Each vertex is one instance of the VertexPositionColor struct.
const UINT stride = sizeof(VertexPositionColor);
const UINT offset = 0;
context->IASetVertexBuffers(
    0,
    1,
    m_vertexBuffer.GetAddressOf(),
    &stride,
    &offset
);
context->IASetIndexBuffer(
    m_indexBuffer.Get(),
    DXGI_FORMAT_R16_UINT, // Each index is one 16-bit unsigned integer (short).
    0
);
context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach the vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
);
// Apply the model constant buffer to the vertex shader.
context->VSSetConstantBuffers(
    0,
    1,
    m_modelConstantBuffer.GetAddressOf()
);

// Attach the pixel shader.
context->PSSetShader(
    m_pixelShader.Get(),
    nullptr,
    0
);

// Draw the objects.
context->DrawIndexedInstanced(
    m_indexCount,   // Index count per instance.
    2,              // Instance count.
    0,              // Start index location.
    0,              // Base vertex location.
    0               // Start instance location.
);
```

### <a name="important-note-about-rendering-on-non-hololens-devices"></a>非 HoloLens デバイスでのレンダリングに関する重要な注意事項

頂点シェーダーにレンダーターゲット配列インデックスを設定するには、グラフィックスドライバーがオプションの Direct3D 11.3 機能 (HoloLens がサポート) をサポートしている必要があります。 アプリがレンダリング用のその手法だけを安全に実装でき、すべての要件が Microsoft HoloLens で実行されるようになります。

HoloLens エミュレーターも使用する場合があります。これは、holographic アプリ用の強力な開発ツールであり、windows 10 Pc に接続されている Windows Mixed Reality イマーシブヘッドセットデバイスをサポートします。 非 HoloLens レンダリングパスのサポート-すべての Windows Mixed Reality で、Windows Holographic アプリケーションテンプレートにも組み込まれています。 テンプレートコードには、開発用 PC の GPU で holographic アプリを実行できるようにするコードがあります。 **DeviceResources** クラスで、このオプションの機能のサポートを確認する方法を次に示します。

**DeviceResources:: CreateDeviceResources** から:

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

このオプションの機能を使用せずにレンダリングをサポートするには、アプリで geometry シェーダーを使用してレンダーターゲットの配列インデックスを設定する必要があります。 このスニペットは、 **VSSetConstantBuffers** の *後*、前のセクションで説明したコード例の **pssetshader** の *前* に追加されます。これは、HoloLens でのステレオのレンダリング方法を説明するものです。

**SpinningCubeRenderer:: Render** から:

```cpp
if (!m_usingVprtShaders)
{
    // On devices that do not support the D3D11_FEATURE_D3D11_OPTIONS3::
    // VPAndRTArrayIndexFromAnyShaderFeedingRasterizer optional feature,
    // a pass-through geometry shader is used to set the render target 
    // array index.
    context->GSSetShader(
        m_geometryShader.Get(),
        nullptr,
        0
    );
}
```

**HLSL メモ**: この例では、TEXCOORD0 など、常に許可されているシェーダーセマンティクスを使用して、レンダーターゲットの配列インデックスを geometry シェーダーに渡す若干変更された頂点シェーダーも読み込む必要があります。 ジオメトリシェーダーは、作業を行う必要はありません。テンプレートジオメトリシェーダーは、すべてのデータを処理します。ただし、render ターゲットの配列インデックスは除き、SV_RenderTargetArrayIndex セマンティックを設定するために使用されます。

**GeometryShader** のアプリテンプレートコード:

```HLSL
// Per-vertex data from the vertex shader.
struct GeometryShaderInput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint instId         : TEXCOORD0;
};

// Per-vertex data passed to the rasterizer.
struct GeometryShaderOutput
{
    min16float4 pos     : SV_POSITION;
    min16float3 color   : COLOR0;
    uint rtvId          : SV_RenderTargetArrayIndex;
};

// This geometry shader is a pass-through that leaves the geometry unmodified 
// and sets the render target array index.
[maxvertexcount(3)]
void main(triangle GeometryShaderInput input[3], inout TriangleStream<GeometryShaderOutput> outStream)
{
    GeometryShaderOutput output;
    [unroll(3)]
    for (int i = 0; i < 3; ++i)
    {
        output.pos   = input[i].pos;
        output.color = input[i].color;
        output.rtvId = input[i].instId;
        outStream.Append(output);
    }
}
```

## <a name="present"></a>存在

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a>Holographic フレームでスワップチェーンを表示できるようにします

Windows Mixed Reality では、システムによってスワップチェーンが制御されます。 次に、システムは、各 holographic カメラへのフレームの表示を管理して、高品質なユーザーエクスペリエンスを実現します。 また、イメージの安定化や Mixed Reality のキャプチャなどのシステムの側面を最適化するために、各カメラの各フレームを更新するためのビューポートも用意されています。 そのため、DirectX を使用している holographic アプリは、DXGI スワップチェーンでは **を呼び出す** ことができません。 代わりに、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> クラスを使用して、フレームを描画した後、そのすべてのスワップチェーンを表示します。

From **DeviceResources::P** 再送信します。

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

既定では、この API はフレームが終了するまで待機してから制御を戻します。 Holographic アプリは、新しいフレームで作業を開始する前に、前のフレームが終了するまで待機する必要があります。これにより、待機時間が短縮され、Holographic フレーム予測の結果が向上します。 これは難しいルールではなく、1つの画面の更新をレンダリングするのに時間がかかるフレームがある場合は、HolographicFramePresentWaitBehavior パラメーターを使用して <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">Current予測</a>を実行することで、この待機を無効にすることができます。 この場合、GPU に継続的な負荷を維持するために、非同期レンダリングスレッドを使用する可能性があります。 HoloLens デバイスのリフレッシュレートは 60 hz で、1つのフレームの期間は約16ミリ秒です。 イマーシブヘッドセットデバイスは、60 hz から 90 hz までの範囲で指定できます。ディスプレイを 90 hz で更新すると、各フレームの期間は約11ミリ秒になります。

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a>HolographicFrame と連携して、Devicのシナリオを処理します

DirectX 11 アプリは通常、DXGI スワップチェーンの **present** 関数によって返された HRESULT を確認して、 **devicループ** エラーが発生したかどうかを調べます。 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>クラスはこれを処理します。 返された <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> を調べて、Direct3D デバイスとデバイスベースのリソースを解放して再作成する必要があるかどうかを確認します。

```cpp
// The PresentUsingCurrentPrediction API will detect when the graphics device
// changes or becomes invalid. When this happens, it is considered a Direct3D
// device lost scenario.
if (presentResult == HolographicFramePresentResult::DeviceRemoved)
{
    // The Direct3D device, context, and resources should be recreated.
    HandleDeviceLost();
}
```

Direct3D デバイスが失われ、再作成した場合は、新しいデバイスの使用を開始するように <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> に指示する必要があります。 スワップチェーンは、このデバイスに対して再作成されます。

**DeviceResources:: InitializeUsingHolographicSpace** から:

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

フレームが表示されたら、メインのプログラムループに戻り、次のフレームに進むことができます。

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a>ハイブリッドグラフィックス Pc と mixed reality アプリケーション

Windows 10 の作成者更新 Pc は、離散 Gpu と統合 Gpu の **両方** で構成できます。 これらの種類のコンピューターでは、ヘッドセットが接続されているアダプターが Windows によって選択されます。 アプリケーションでは、作成する DirectX デバイスで同じアダプターが使用されるようにする必要があります。

一般的な Direct3D サンプルコードでは、既定のハードウェアアダプターを使用して DirectX デバイスを作成する方法を示しています。このハードウェアアダプターは、ヘッドホンで使用されているものと同じではない場合があります。

問題を回避するには、いずれかの<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>の<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterID</a>を使用します。PrimaryAdapterId () または<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>。AdapterId ()。 この adapterId を使用すると、IDXGIFactory4 を使用して適切に DXGIAdapter を選択できます。

**DeviceResources:: InitializeUsingHolographicSpace** から:

```cpp
// The holographic space might need to determine which adapter supports
// holograms, in which case it will specify a non-zero PrimaryAdapterId.
LUID id =
{
    m_holographicSpace.PrimaryAdapterId().LowPart,
    m_holographicSpace.PrimaryAdapterId().HighPart
};

// When a primary adapter ID is given to the app, the app should find
// the corresponding DXGI adapter and use it to create Direct3D devices
// and device contexts. Otherwise, there is no restriction on the DXGI
// adapter the app can use.
if ((id.HighPart != 0) || (id.LowPart != 0))
{
    UINT createFlags = 0;

    // Create the DXGI factory.
    ComPtr<IDXGIFactory1> dxgiFactory;
    winrt::check_hresult(
        CreateDXGIFactory2(
            createFlags,
            IID_PPV_ARGS(&dxgiFactory)
        ));
    ComPtr<IDXGIFactory4> dxgiFactory4;
    winrt::check_hresult(dxgiFactory.As(&dxgiFactory4));

    // Retrieve the adapter specified by the holographic space.
    winrt::check_hresult(
        dxgiFactory4->EnumAdapterByLuid(
            id,
            IID_PPV_ARGS(&m_dxgiAdapter)
        ));
}
else
{
    m_dxgiAdapter.Reset();
}
```

**IDXGIAdapter を使用するように DeviceResources:: CreateDeviceResources を更新** するコード

```cpp
// Create the Direct3D 11 API device object and a corresponding context.
ComPtr<ID3D11Device> device;
ComPtr<ID3D11DeviceContext> context;

const D3D_DRIVER_TYPE driverType = m_dxgiAdapter == nullptr ? D3D_DRIVER_TYPE_HARDWARE : D3D_DRIVER_TYPE_UNKNOWN;
const HRESULT hr = D3D11CreateDevice(
    m_dxgiAdapter.Get(),        // Either nullptr, or the primary adapter determined by Windows Holographic.
    driverType,                 // Create a device using the hardware graphics driver.
    0,                          // Should be 0 unless the driver is D3D_DRIVER_TYPE_SOFTWARE.
    creationFlags,              // Set debug and Direct2D compatibility flags.
    featureLevels,              // List of feature levels this app can support.
    ARRAYSIZE(featureLevels),   // Size of the list above.
    D3D11_SDK_VERSION,          // Always set this to D3D11_SDK_VERSION for Windows Runtime apps.
    &device,                    // Returns the Direct3D device created.
    &m_d3dFeatureLevel,         // Returns feature level of device created.
    &context                    // Returns the device immediate context.
);
```

**ハイブリッドグラフィックスとメディアファンデーション**

ハイブリッドシステムでメディアファンデーションを使用すると、メディアファンデーションがシステムの動作を既定にするため、ビデオがレンダリングされない、またはビデオテクスチャが破損する問題が発生する可能性があります。 場合によっては、マルチスレッドをサポートするために個別の ID3D11Device を作成する必要があり、適切な作成フラグが設定されます。

ID3D11Device を初期化するときは、D3D11_CREATE_DEVICE_VIDEO_SUPPORT フラグを D3D11_CREATE_DEVICE_FLAG の一部として定義する必要があります。 デバイスとコンテキストが作成されたら、 <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">Setmultithreadprotected</a> を呼び出してマルチスレッドを有効にします。 デバイスを <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">Imfdxgidevicemanager</a>に関連付けるには、 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">Imfdxgidevicemanager:: resetdevice</a> 関数を使用します。

**ID3D11Device を IMFDXGIDeviceManager に関連付ける** コード。

```cpp
// create dx device for media pipeline
winrt::com_ptr<ID3D11Device> spMediaDevice;

// See above. Also make sure to enable the following flags on the D3D11 device:
//   * D3D11_CREATE_DEVICE_VIDEO_SUPPORT
//   * D3D11_CREATE_DEVICE_BGRA_SUPPORT
if (FAILED(CreateMediaDevice(spAdapter.get(), &spMediaDevice)))
    return;                                                     

// Turn multithreading on 
winrt::com_ptr<ID3D10Multithread> spMultithread;
if (spContext.try_as(spMultithread))
{
    spMultithread->SetMultithreadProtected(TRUE);
}

// lock the shared dxgi device manager
// call MFUnlockDXGIDeviceManager when no longer needed
UINT uiResetToken;
winrt::com_ptr<IMFDXGIDeviceManager> spDeviceManager;
hr = MFLockDXGIDeviceManager(&uiResetToken, spDeviceManager.put());
if (FAILED(hr))
    return hr;
    
// associate the device with the manager
hr = spDeviceManager->ResetDevice(spMediaDevice.get(), uiResetToken);
if (FAILED(hr))
    return hr;
```

## <a name="see-also"></a>関連項目
* [DirectX の座標系](coordinate-systems-in-directx.md)
* [HoloLens エミュレーターを使用する](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
