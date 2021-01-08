---
title: DirectX でのレンダリング
description: Windows Mixed Reality の DirectX アプリケーションでコンテンツを更新して表示する方法について説明します。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows Mixed Reality, ホログラム, レンダリング, 3D グラフィックス, HolographicFrame, レンダリングループ, 更新ループ, チュートリアル, サンプルコード, Direct3D
ms.openlocfilehash: aafead61b45550f499405ae63bda7d7f8e79d224
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006722"
---
# <a name="rendering-in-directx"></a><span data-ttu-id="7c370-104">DirectX でのレンダリング</span><span class="sxs-lookup"><span data-stu-id="7c370-104">Rendering in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="7c370-105">この記事は、従来の WinRT ネイティブ Api に関連しています。</span><span class="sxs-lookup"><span data-stu-id="7c370-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="7c370-106">新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](openxr-getting-started.md)** を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7c370-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="7c370-107">Windows Mixed Reality は DirectX 上に構築されており、ユーザーに対して豊富な3D グラフィカルエクスペリエンスを生み出します。</span><span class="sxs-lookup"><span data-stu-id="7c370-107">Windows Mixed Reality is built on DirectX to produce rich, 3D graphical experiences for users.</span></span> <span data-ttu-id="7c370-108">レンダリングの抽象化は DirectX のすぐ上にあり、システムによって予測された holographic シーンオブザーバーの位置と向きに関するアプリの理由を示します。</span><span class="sxs-lookup"><span data-stu-id="7c370-108">The rendering abstraction sits just above DirectX, which lets apps reason about the position and orientation of holographic scene observers predicted by the system.</span></span> <span data-ttu-id="7c370-109">開発者は、各カメラに基づいてホログラムを見つけることができます。これにより、アプリは、ユーザーが移動するときに、さまざまな空間座標系でこれらのホログラムをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="7c370-109">The developer can then locate their holograms based on each camera, letting the app render these holograms in various spatial coordinate systems as the user moves around.</span></span>

<span data-ttu-id="7c370-110">メモ: このチュートリアルでは、Direct3D 11 での holographic レンダリングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7c370-110">Note: This walkthrough describes holographic rendering in Direct3D 11.</span></span> <span data-ttu-id="7c370-111">Direct3D 12 Windows Mixed Reality アプリテンプレートには、Mixed Reality アプリテンプレート拡張機能も用意されています。</span><span class="sxs-lookup"><span data-stu-id="7c370-111">A Direct3D 12 Windows Mixed Reality app template is also supplied with the Mixed Reality app templates extension.</span></span>

## <a name="update-for-the-current-frame"></a><span data-ttu-id="7c370-112">現在のフレームの更新</span><span class="sxs-lookup"><span data-stu-id="7c370-112">Update for the current frame</span></span>

<span data-ttu-id="7c370-113">ホログラムのアプリケーションの状態を更新するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="7c370-113">To update the application state for holograms, once per frame the app will:</span></span>
* <span data-ttu-id="7c370-114">表示管理システムから <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> を取得します。</span><span class="sxs-lookup"><span data-stu-id="7c370-114">Get a <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> from the display management system.</span></span>
* <span data-ttu-id="7c370-115">レンダリングが完了したら、カメラビューが配置されるの現在の予測でシーンを更新します。</span><span class="sxs-lookup"><span data-stu-id="7c370-115">Update the scene with the current prediction of where the camera view will be when render is completed.</span></span> <span data-ttu-id="7c370-116">Holographic シーンでは、複数のカメラを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7c370-116">Note, there can be more than one camera for the holographic scene.</span></span>

<span data-ttu-id="7c370-117">Holographic カメラビューにレンダリングするには、アプリがフレームごとに1回、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7c370-117">To render to holographic camera views, once per frame the app will:</span></span>
* <span data-ttu-id="7c370-118">カメラごとに、システムのカメラビューと投影行列を使用して、現在のフレームのシーンをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="7c370-118">For each camera, render the scene for the current frame, using the camera view and projection matrices from the system.</span></span>

### <a name="create-a-new-holographic-frame-and-get-its-prediction"></a><span data-ttu-id="7c370-119">新しい holographic フレームを作成し、予測を取得する</span><span class="sxs-lookup"><span data-stu-id="7c370-119">Create a new holographic frame and get its prediction</span></span>

<span data-ttu-id="7c370-120"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>には、アプリが現在のフレームを更新して表示するために必要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c370-120">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> has information that the app needs to update and render the current frame.</span></span> <span data-ttu-id="7c370-121">アプリは、 **Createnextframe** メソッドを呼び出すことによって、各新しいフレームを開始します。</span><span class="sxs-lookup"><span data-stu-id="7c370-121">The app begins each new frame by calling the **CreateNextFrame** method.</span></span> <span data-ttu-id="7c370-122">このメソッドが呼び出されると、予測は、使用可能な最新のセンサーデータを使用して作成され、 **currentprediction** オブジェクトにカプセル化されます。</span><span class="sxs-lookup"><span data-stu-id="7c370-122">When this method is called, predictions are made using the latest sensor data available, and encapsulated in **CurrentPrediction** object.</span></span>

<span data-ttu-id="7c370-123">レンダリングされた各フレームは、瞬時に有効であるため、新しいフレームオブジェクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-123">A new frame object must be used for each rendered frame as it is only valid for an instant in time.</span></span> <span data-ttu-id="7c370-124">**Currentprediction** プロパティには、カメラの位置などの情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c370-124">The **CurrentPrediction** property contains information such as the camera position.</span></span> <span data-ttu-id="7c370-125">この情報は、フレームがユーザーに表示されることが予想される正確な時点に対して推定されます。</span><span class="sxs-lookup"><span data-stu-id="7c370-125">The information is extrapolated to the exact moment in time when the frame is expected to be visible to the user.</span></span>

<span data-ttu-id="7c370-126">次のコードは、 **Appmain:: Update** から抜粋ですされています。</span><span class="sxs-lookup"><span data-stu-id="7c370-126">The following code is excerpted from **AppMain::Update**:</span></span>

```cpp
// The HolographicFrame has information that the app needs in order
// to update and render the current frame. The app begins each new
// frame by calling CreateNextFrame.
HolographicFrame holographicFrame = m_holographicSpace.CreateNextFrame();

// Get a prediction of where holographic cameras will be when this frame
// is presented.
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="process-camera-updates"></a><span data-ttu-id="7c370-127">カメラの更新の処理</span><span class="sxs-lookup"><span data-stu-id="7c370-127">Process camera updates</span></span>

<span data-ttu-id="7c370-128">バックバッファーはフレーム間で変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-128">Back buffers can change from frame to frame.</span></span> <span data-ttu-id="7c370-129">アプリでは、各カメラのバックバッファーを検証し、必要に応じてリソースビューと深度バッファーを解放して再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-129">Your app needs to validate the back buffer for each camera, and release and recreate resource views and depth buffers as needed.</span></span> <span data-ttu-id="7c370-130">予測に含まれる一連の設定が、現在のフレームで使用されているカメラの権限の一覧になっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="7c370-130">Notice that the set of poses in the prediction is the authoritative list of cameras being used in the current frame.</span></span> <span data-ttu-id="7c370-131">通常、この一覧を使用して、カメラのセットを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="7c370-131">Usually, you use this list to iterate on the set of cameras.</span></span>

<span data-ttu-id="7c370-132">**Appmain:: Update** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-132">From **AppMain::Update**:</span></span>

```cpp
m_deviceResources->EnsureCameraResources(holographicFrame, prediction);
```

<span data-ttu-id="7c370-133">**DeviceResources:: EnsureCameraResources** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-133">From **DeviceResources::EnsureCameraResources**:</span></span>

```cpp
for (HolographicCameraPose const& cameraPose : prediction.CameraPoses())
{
    HolographicCameraRenderingParameters renderingParameters = frame.GetRenderingParameters(cameraPose);
    CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();
    pCameraResources->CreateResourcesForBackBuffer(this, renderingParameters);
}
```

### <a name="get-the-coordinate-system-to-use-as-a-basis-for-rendering"></a><span data-ttu-id="7c370-134">描画の基準として使用する座標系を取得します。</span><span class="sxs-lookup"><span data-stu-id="7c370-134">Get the coordinate system to use as a basis for rendering</span></span>

<span data-ttu-id="7c370-135">Windows Mixed Reality を使用すると、アプリは、物理的な世界での場所を追跡するために、接続された、静止した参照フレームなどのさまざまな [座標系](coordinate-systems-in-directx.md)を作成できます。</span><span class="sxs-lookup"><span data-stu-id="7c370-135">Windows Mixed Reality lets your app create various [coordinate systems](coordinate-systems-in-directx.md), like attached and stationary reference frames for tracking locations in the physical world.</span></span> <span data-ttu-id="7c370-136">これにより、アプリはこれらの座標系を使用して、各フレームのホログラムのレンダリングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7c370-136">Your app can then use these coordinate systems to reason about where to render holograms each frame.</span></span> <span data-ttu-id="7c370-137">API から座標を要求するときは、その座標を表現する <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> を常に渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-137">When requesting coordinates from an API, you'll always pass in the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a> within which you want those coordinates to be expressed.</span></span>

<span data-ttu-id="7c370-138">**Appmain:: Update** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-138">From **AppMain::Update**:</span></span>

```cpp
pose = SpatialPointerPose::TryGetAtTimestamp(
    m_stationaryReferenceFrame.CoordinateSystem(), prediction.Timestamp());
```

<span data-ttu-id="7c370-139">これらの座標系を使用して、シーンにコンテンツをレンダリングするときに、ステレオビュー行列を生成できます。</span><span class="sxs-lookup"><span data-stu-id="7c370-139">These coordinate systems can then be used to generate stereo view matrices when rendering the content in your scene.</span></span>

<span data-ttu-id="7c370-140">**CameraResources:: UpdateViewProjectionBuffer** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-140">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

```cpp
// Get a container object with the view and projection matrices for the given
// pose in the given coordinate system.
auto viewTransformContainer = cameraPose.TryGetViewTransform(coordinateSystem);
```

### <a name="process-gaze-and-gesture-input"></a><span data-ttu-id="7c370-141">プロセスの宝石とジェスチャの入力</span><span class="sxs-lookup"><span data-stu-id="7c370-141">Process gaze and gesture input</span></span>

<span data-ttu-id="7c370-142">手書き入力と [手動](hands-and-motion-controllers-in-directx.md)入力は時間ベースでは [なく、](gaze-in-directx.md) **steptimer** 関数で更新する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7c370-142">[Gaze](gaze-in-directx.md) and [hand](hands-and-motion-controllers-in-directx.md) input aren't time-based and don't have to update in the **StepTimer** function.</span></span> <span data-ttu-id="7c370-143">ただし、この入力は、アプリが各フレームを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-143">However this input is something that the app needs to look at each frame.</span></span>

### <a name="process-time-based-updates"></a><span data-ttu-id="7c370-144">プロセス時間ベースの更新</span><span class="sxs-lookup"><span data-stu-id="7c370-144">Process time-based updates</span></span>

<span data-ttu-id="7c370-145">リアルタイムレンダリングアプリでは、時間ベースの更新を処理するために何らかの方法が必要です。 Windows Holographic アプリケーションテンプレートでは、DirectX 11 UWP アプリケーションテンプレートに用意されている StepTimer と同様に、 **steptimer** 実装が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7c370-145">Any real-time rendering app will need some way to process time-based updates - the Windows Holographic app template uses a **StepTimer** implementation, similar to the StepTimer provided in the DirectX 11 UWP app template.</span></span> <span data-ttu-id="7c370-146">このサンプルヘルパークラスは、固定された時間ステップの更新、時間の経過に伴う時間の更新、既定のモードは変動する時間のステップを提供します。</span><span class="sxs-lookup"><span data-stu-id="7c370-146">This StepTimer sample helper class can provide fixed time-step updates, variable time-step updates, and the default mode is variable time steps.</span></span>

<span data-ttu-id="7c370-147">Holographic のレンダリングでは、タイマー関数を固定の時間ステップとして構成できるので、タイマー関数にあまり多くを入れないことを選択しました。</span><span class="sxs-lookup"><span data-stu-id="7c370-147">For holographic rendering, we've chosen not to put too much into the timer function because you can configure it to be a fixed time step.</span></span> <span data-ttu-id="7c370-148">フレームごとに複数回呼び出される場合があります。また、フレームによっては、holographic データの更新がフレームごとに1回行われる必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-148">It might get called more than once per frame – or not at all, for some frames – and our holographic data updates should happen once per frame.</span></span>


<span data-ttu-id="7c370-149">**Appmain:: Update** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-149">From **AppMain::Update**:</span></span>

```cpp
m_timer.Tick([this]()
{
    m_spinningCubeRenderer->Update(m_timer);
});
```

### <a name="position-and-rotate-holograms-in-your-coordinate-system"></a><span data-ttu-id="7c370-150">座標系でのホログラムの位置と回転</span><span class="sxs-lookup"><span data-stu-id="7c370-150">Position and rotate holograms in your coordinate system</span></span>

<span data-ttu-id="7c370-151">1つの座標系で運用している場合は、テンプレートが **SpatialStationaryReferenceFrame** を使用しているため、このプロセスは3d グラフィックスで使用していたものとは異なります。</span><span class="sxs-lookup"><span data-stu-id="7c370-151">If you're operating in a single coordinate system, as the template does with the **SpatialStationaryReferenceFrame**, this process isn't different from what you're otherwise used to in 3D graphics.</span></span> <span data-ttu-id="7c370-152">ここでは、立方体を回転させ、固定の座標系の位置に基づいてモデルマトリックスを設定します。</span><span class="sxs-lookup"><span data-stu-id="7c370-152">Here, we rotate the cube and set the model matrix based on the position in the stationary coordinate system.</span></span>

<span data-ttu-id="7c370-153">**SpinningCubeRenderer:: Update** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-153">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="7c370-154">**高度なシナリオに関する注意:** 回転するキューブは、1つの参照フレーム内にホログラムを配置する方法の簡単な例です。</span><span class="sxs-lookup"><span data-stu-id="7c370-154">**Note about advanced scenarios:** The spinning cube is a simple example of how to position a hologram within a single reference frame.</span></span> <span data-ttu-id="7c370-155">同時に、レンダリングされた同じフレームで [複数の SpatialCoordinateSystems を使用](coordinate-systems-in-directx.md) することもできます。</span><span class="sxs-lookup"><span data-stu-id="7c370-155">It's also possible to [use multiple SpatialCoordinateSystems](coordinate-systems-in-directx.md) in the same rendered frame, at the same time.</span></span>

### <a name="update-constant-buffer-data"></a><span data-ttu-id="7c370-156">定数バッファーデータの更新</span><span class="sxs-lookup"><span data-stu-id="7c370-156">Update constant buffer data</span></span>

<span data-ttu-id="7c370-157">コンテンツのモデル変換は、通常どおりに更新されます。</span><span class="sxs-lookup"><span data-stu-id="7c370-157">Model transforms for content are updated as usual.</span></span> <span data-ttu-id="7c370-158">ここまでで、レンダリングする座標系の有効な変換を計算しました。</span><span class="sxs-lookup"><span data-stu-id="7c370-158">By now, you'll have computed valid transforms for the coordinate system you'll be rendering in.</span></span>

<span data-ttu-id="7c370-159">**SpinningCubeRenderer:: Update** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-159">From **SpinningCubeRenderer::Update**:</span></span>

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

<span data-ttu-id="7c370-160">ビューとプロジェクションの変換について</span><span class="sxs-lookup"><span data-stu-id="7c370-160">What about view and projection transforms?</span></span> <span data-ttu-id="7c370-161">最良の結果を得るために、描画呼び出しの準備が整うまで待機してから、これらを取得します。</span><span class="sxs-lookup"><span data-stu-id="7c370-161">For best results, we want to wait until we're almost ready for our draw calls before we get these.</span></span>

## <a name="render-the-current-frame"></a><span data-ttu-id="7c370-162">現在のフレームをレンダリングします</span><span class="sxs-lookup"><span data-stu-id="7c370-162">Render the current frame</span></span>

<span data-ttu-id="7c370-163">Windows Mixed Reality でのレンダリングは、2D mono ディスプレイでのレンダリングとは大きく異なりますが、いくつか違いがあります。</span><span class="sxs-lookup"><span data-stu-id="7c370-163">Rendering on Windows Mixed Reality isn't much different from rendering on a 2D mono display, but there are a few differences:</span></span>
* <span data-ttu-id="7c370-164">Holographic フレーム予測は重要です。</span><span class="sxs-lookup"><span data-stu-id="7c370-164">Holographic frame predictions are important.</span></span> <span data-ttu-id="7c370-165">予測に近いほど、フレームが表示されるときに、ホログラムが見やすくなります。</span><span class="sxs-lookup"><span data-stu-id="7c370-165">The closer the prediction is to when your frame is presented, the better your holograms will look.</span></span>
* <span data-ttu-id="7c370-166">Windows Mixed Reality は、カメラビューを制御します。</span><span class="sxs-lookup"><span data-stu-id="7c370-166">Windows Mixed Reality controls the camera views.</span></span> <span data-ttu-id="7c370-167">Holographic フレームによって後で表示されるため、それぞれにレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="7c370-167">Render to each one because the holographic frame will be presenting them for you later.</span></span>
* <span data-ttu-id="7c370-168">レンダーターゲット配列に描画するインスタンスを使用して、ステレオレンダリングを行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7c370-168">We recommend doing stereo rendering using instanced drawing to a render target array.</span></span> <span data-ttu-id="7c370-169">Holographic アプリテンプレートでは、レンダーターゲット配列に描画するための推奨される方法を使用しています。レンダーターゲット配列は、レンダーターゲットビューを **Texture2DArray** に使用します。</span><span class="sxs-lookup"><span data-stu-id="7c370-169">The holographic app template uses the recommended approach of instanced drawing to a render target array, which uses a render target view onto a **Texture2DArray**.</span></span>
* <span data-ttu-id="7c370-170">ステレオのインスタンス化を使用せずにレンダリングする場合は、2つの非配列 RenderTargetViews を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-170">If you want to render without using stereo instancing, you'll need to create two non-array RenderTargetViews, one for each eye.</span></span> <span data-ttu-id="7c370-171">各 RenderTargetViews は、システムからアプリに提供される **Texture2DArray** 内の2つのスライスのうちの1つを参照します。</span><span class="sxs-lookup"><span data-stu-id="7c370-171">Each RenderTargetViews references one of the two slices in the **Texture2DArray** provided to the app from the system.</span></span> <span data-ttu-id="7c370-172">これは、通常、インスタンス化を使用するよりも低速であるため、推奨されません。</span><span class="sxs-lookup"><span data-stu-id="7c370-172">This isn't recommended, as it's typically slower than using instancing.</span></span>

### <a name="get-an-updated-holographicframe-prediction"></a><span data-ttu-id="7c370-173">更新された HolographicFrame 予測を取得する</span><span class="sxs-lookup"><span data-stu-id="7c370-173">Get an updated HolographicFrame prediction</span></span>

<span data-ttu-id="7c370-174">フレーム予測を更新すると、イメージの安定化の効果が向上します。</span><span class="sxs-lookup"><span data-stu-id="7c370-174">Updating the frame prediction enhances the effectiveness of image stabilization.</span></span> <span data-ttu-id="7c370-175">ホログラムがより正確に配置されるのは、予測とフレームがユーザーに表示される時間が短くなるためです。</span><span class="sxs-lookup"><span data-stu-id="7c370-175">You get more accurate positioning of holograms because of the shorter time between the prediction and when the frame is visible to the user.</span></span> <span data-ttu-id="7c370-176">レンダリングの直前にフレーム予測を更新するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="7c370-176">Ideally update your frame prediction just before rendering.</span></span>

```cpp
holographicFrame.UpdateCurrentPrediction();
HolographicFramePrediction prediction = holographicFrame.CurrentPrediction();
```

### <a name="render-to-each-camera"></a><span data-ttu-id="7c370-177">各カメラにレンダリングする</span><span class="sxs-lookup"><span data-stu-id="7c370-177">Render to each camera</span></span>

<span data-ttu-id="7c370-178">一連のカメラでループし、予測を行い、このセット内の各カメラにレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="7c370-178">Loop on the set of camera poses in the prediction, and render to each camera in this set.</span></span>

<span data-ttu-id="7c370-179">**レンダリングパスを設定する**</span><span class="sxs-lookup"><span data-stu-id="7c370-179">**Set up your rendering pass**</span></span>

<span data-ttu-id="7c370-180">Windows Mixed Reality は、ステレオスコピックレンダリングを使用して奥行の錯覚を強化し、stereoscopically をレンダリングします。そのため、左と右の両方の表示がアクティブです。</span><span class="sxs-lookup"><span data-stu-id="7c370-180">Windows Mixed Reality uses stereoscopic rendering to enhance the illusion of depth and to render stereoscopically, so both the left and the right display are active.</span></span> <span data-ttu-id="7c370-181">ステレオスコピックレンダリングでは、2つのディスプレイの間にオフセットがあります。これは、脳が実際の深さとして調整できます。</span><span class="sxs-lookup"><span data-stu-id="7c370-181">With stereoscopic rendering, there's an offset between the two displays, which the brain can reconcile as actual depth.</span></span> <span data-ttu-id="7c370-182">このセクションでは、Windows Holographic アプリテンプレートのコードを使用して、インスタンス化を使用したステレオスコピックレンダリングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7c370-182">This section covers stereoscopic rendering using instancing, using code from the Windows Holographic app template.</span></span>

<span data-ttu-id="7c370-183">各カメラは、独自のレンダーターゲット (バックバッファー) と、ビューおよび投影マトリックスを holographic 空間に持ちます。</span><span class="sxs-lookup"><span data-stu-id="7c370-183">Each camera has its own render target (back buffer), and view and projection matrices, into the holographic space.</span></span> <span data-ttu-id="7c370-184">アプリでは、カメラごとに、深度バッファーなどの他のカメラベースのリソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-184">Your app will need to create any other camera-based resources - such as the depth buffer - on a per-camera basis.</span></span> <span data-ttu-id="7c370-185">Windows Holographic アプリテンプレートでは、これらのリソースを DX:: CameraResources にまとめてバンドルするヘルパークラスを提供しています。</span><span class="sxs-lookup"><span data-stu-id="7c370-185">In the Windows Holographic app template, we provide a helper class to bundle these resources together in DX::CameraResources.</span></span> <span data-ttu-id="7c370-186">まず、レンダーターゲットビューを設定します。</span><span class="sxs-lookup"><span data-stu-id="7c370-186">Start by setting up the render target views:</span></span>

<span data-ttu-id="7c370-187">**Appmain:: Render** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-187">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="7c370-188">**予測を使用して、カメラのビューおよび投影行列を取得します。**</span><span class="sxs-lookup"><span data-stu-id="7c370-188">**Use the prediction to get the view and projection matrices for the camera**</span></span>

<span data-ttu-id="7c370-189">各 holographic カメラのビューおよび投影マトリックスは、すべてのフレームで変更されます。</span><span class="sxs-lookup"><span data-stu-id="7c370-189">The view and projection matrices for each holographic camera will change with every frame.</span></span> <span data-ttu-id="7c370-190">各 holographic カメラの定数バッファーのデータを更新します。</span><span class="sxs-lookup"><span data-stu-id="7c370-190">Refresh the data in the constant buffer for each holographic camera.</span></span> <span data-ttu-id="7c370-191">この操作は、予測を更新した後、そのカメラの描画呼び出しを行う前に行います。</span><span class="sxs-lookup"><span data-stu-id="7c370-191">Do this after you updated the prediction, and before you make any draw calls for that camera.</span></span>

<span data-ttu-id="7c370-192">**Appmain:: Render** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-192">From **AppMain::Render**:</span></span>

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

<span data-ttu-id="7c370-193">ここでは、カメラによってどのように行列が取得されるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="7c370-193">Here, we show how the matrices are acquired from the camera pose.</span></span> <span data-ttu-id="7c370-194">このプロセスでは、カメラの現在のビューポートも取得します。</span><span class="sxs-lookup"><span data-stu-id="7c370-194">During this process, we also obtain the current viewport for the camera.</span></span> <span data-ttu-id="7c370-195">座標系をどのように提供しているかに注意してください。これは、宝石を理解するために使用したものと同じ座標系であり、回転しているキューブの配置に使用したものと同じです。</span><span class="sxs-lookup"><span data-stu-id="7c370-195">Note how we provide a coordinate system: this is the same coordinate system we used to understand gaze, and it's the same one we used to position the spinning cube.</span></span>


<span data-ttu-id="7c370-196">**CameraResources:: UpdateViewProjectionBuffer** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-196">From **CameraResources::UpdateViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="7c370-197">ビューポートは、各フレームに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-197">The viewport should be set each frame.</span></span> <span data-ttu-id="7c370-198">通常、頂点シェーダー (少なくとも) は、ビュー/プロジェクションデータへのアクセスを必要とします。</span><span class="sxs-lookup"><span data-stu-id="7c370-198">Your vertex shader (at least) will generally need access to the view/projection data.</span></span>


<span data-ttu-id="7c370-199">**CameraResources:: AttachViewProjectionBuffer** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-199">From **CameraResources::AttachViewProjectionBuffer**:</span></span>

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

<span data-ttu-id="7c370-200">**カメラのバックバッファーにレンダリングし、深度バッファーをコミットし** ます。</span><span class="sxs-lookup"><span data-stu-id="7c370-200">**Render to the camera back buffer and commit the depth buffer**:</span></span>

<span data-ttu-id="7c370-201">ビュー/プロジェクションデータを使用する前に **Trygetviewtransform** が成功したことを確認することをお勧めします。これは、座標系の位置が正しくない (たとえば、追跡が中断された) 場合、アプリはそのフレームではレンダリングできないためです。</span><span class="sxs-lookup"><span data-stu-id="7c370-201">It's a good idea to check that **TryGetViewTransform** succeeded before trying to use the view/projection data, because if the coordinate system isn't locatable (for example, tracking was interrupted) your app can't render with it for that frame.</span></span> <span data-ttu-id="7c370-202">**CameraResources** クラスが正常に更新されたことを示している場合、このテンプレートは回転しているキューブに対してのみ **Render** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7c370-202">The template only calls **Render** on the spinning cube if the **CameraResources** class indicates a successful update.</span></span>

<span data-ttu-id="7c370-203">Windows Mixed Reality には、開発者やユーザーが配置したホログラムをどこに配置しても、 [イメージを安定化](../platform-capabilities-and-apis/hologram-stability.md) させておくための機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c370-203">Windows Mixed Reality includes features for [image stabilization](../platform-capabilities-and-apis/hologram-stability.md) to keep holograms positioned where a developer or user puts them in the world.</span></span> <span data-ttu-id="7c370-204">イメージの安定化は、ユーザーに最適な holographic エクスペリエンスを確保するために、レンダリングパイプラインに固有の待機時間を非表示にするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7c370-204">Image stabilization helps hide the latency inherent in a rendering pipeline to ensure the best holographic experiences for users.</span></span> <span data-ttu-id="7c370-205">さらに、イメージの安定化をさらに強化するためにフォーカスポイントを指定することも、最適化されたイメージ安定化をリアルタイムで計算するために深度バッファーを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="7c370-205">A focus point may be specified to enhance image stabilization even further, or a depth buffer may be provided to compute optimized image stabilization in real time.</span></span>

<span data-ttu-id="7c370-206">最良の結果を得るために、アプリは <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API を使用して深度バッファーを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-206">For best results, your app should provide a depth buffer using the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer" target="_blank">CommitDirect3D11DepthBuffer</a> API.</span></span> <span data-ttu-id="7c370-207">Windows Mixed Reality は、深度バッファーからのジオメトリ情報を使用して、イメージの安定化をリアルタイムで最適化できます。</span><span class="sxs-lookup"><span data-stu-id="7c370-207">Windows Mixed Reality can then use geometry information from the depth buffer to optimize image stabilization in real time.</span></span> <span data-ttu-id="7c370-208">Windows Holographic アプリテンプレートでは、アプリの深度バッファーが既定でコミットされるため、ホログラムの安定性が最適化されます。</span><span class="sxs-lookup"><span data-stu-id="7c370-208">The Windows Holographic app template commits the app's depth buffer by default, helping optimize hologram stability.</span></span>

<span data-ttu-id="7c370-209">**Appmain:: Render** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-209">From **AppMain::Render**:</span></span>

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
><span data-ttu-id="7c370-210">Windows は GPU で深度テクスチャを処理するため、深度バッファーをシェーダーリソースとして使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-210">Windows will process your depth texture on the GPU, so it must be possible to use your depth buffer as a shader resource.</span></span> <span data-ttu-id="7c370-211">作成する ID3D11Texture2D は、型が指定されていない形式である必要があり、シェーダーリソースビューとしてバインドされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-211">The ID3D11Texture2D that you create should be in a typeless format and it should be bound as a shader resource view.</span></span> <span data-ttu-id="7c370-212">イメージの安定化のためにコミットできる深度テクスチャを作成する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7c370-212">Here is an example of how to create a depth texture that can be committed for image stabilization.</span></span>

<span data-ttu-id="7c370-213">**CommitDirect3D11DepthBuffer の深度バッファーリソースの作成** コード:</span><span class="sxs-lookup"><span data-stu-id="7c370-213">Code for **Depth buffer resource creation for CommitDirect3D11DepthBuffer**:</span></span>

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

<span data-ttu-id="7c370-214">**Holographic コンテンツの描画**</span><span class="sxs-lookup"><span data-stu-id="7c370-214">**Draw holographic content**</span></span>

<span data-ttu-id="7c370-215">Windows Holographic アプリテンプレートは、インスタンス化されたジオメトリをサイズ2の Texture2DArray に描画するための推奨される方法を使用して、ステレオでコンテンツをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="7c370-215">The Windows Holographic app template renders content in stereo by using the recommended technique of drawing instanced geometry to a Texture2DArray of size 2.</span></span> <span data-ttu-id="7c370-216">ここでは、こののインスタンス化の部分と、それが Windows Mixed Reality でどのように動作するかを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="7c370-216">Let's look at the instancing part of this, and how it works on Windows Mixed Reality.</span></span>

<span data-ttu-id="7c370-217">**SpinningCubeRenderer:: Render** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-217">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="7c370-218">各インスタンスは、定数バッファーから異なるビュー/プロジェクション行列にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="7c370-218">Each instance accesses a different view/projection matrix from the constant buffer.</span></span> <span data-ttu-id="7c370-219">次に示すのは、2つの行列の配列である定数バッファー構造です。</span><span class="sxs-lookup"><span data-stu-id="7c370-219">Here's the constant buffer structure, which is just an array of two matrices.</span></span>

<span data-ttu-id="7c370-220">**VPRTVertexShader** に含まれる **VertexShaderShared** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-220">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

```HLSL
// A constant buffer that stores each set of view and projection matrices in column-major format.
cbuffer ViewProjectionConstantBuffer : register(b1)
{
    float4x4 viewProjection[2];
};
```

<span data-ttu-id="7c370-221">レンダーターゲットの配列インデックスは、ピクセルごとに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-221">The render target array index must be set for each pixel.</span></span> <span data-ttu-id="7c370-222">次のスニペットでは、viewId が **SV_RenderTargetArrayIndex** セマンティックにマップされています。</span><span class="sxs-lookup"><span data-stu-id="7c370-222">In the following snippet, output.viewId is mapped to the **SV_RenderTargetArrayIndex** semantic.</span></span> <span data-ttu-id="7c370-223">これには、オプションの Direct3D 11.3 機能がサポートされている必要があります。これにより、任意のシェーダーステージからレンダーターゲットの配列インデックスセマンティックを設定できます。</span><span class="sxs-lookup"><span data-stu-id="7c370-223">This requires support for an optional Direct3D 11.3 feature, which allows the render target array index semantic to be set from any shader stage.</span></span>

<span data-ttu-id="7c370-224">**VPRTVertexShader** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-224">From **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="7c370-225">**VPRTVertexShader** に含まれる **VertexShaderShared** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-225">From **VertexShaderShared.hlsl**, included by **VPRTVertexShader.hlsl**:</span></span>

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

<span data-ttu-id="7c370-226">この描画方法を使用して、既にインスタンス化されている描画手法をステレオレンダーターゲット配列に使用する場合は、通常持っているインスタンスの数を2倍にします。</span><span class="sxs-lookup"><span data-stu-id="7c370-226">If you want to use your existing instanced drawing techniques with this method of drawing to a stereo render target array, draw twice the number of instances you normally have.</span></span> <span data-ttu-id="7c370-227">シェーダーでは、 **入力した instId** を2で除算して元のインスタンス ID を取得します。これは、オブジェクトごとのデータのバッファーにインデックスを付けることができます。 `int actualIdx = input.instId / 2;`</span><span class="sxs-lookup"><span data-stu-id="7c370-227">In the shader, divide **input.instId** by 2 to get the original instance ID, which can be indexed into (for example) a buffer of per-object data: `int actualIdx = input.instId / 2;`</span></span>

### <a name="important-note-about-rendering-stereo-content-on-hololens"></a><span data-ttu-id="7c370-228">HoloLens でのステレオコンテンツのレンダリングに関する重要な注意事項</span><span class="sxs-lookup"><span data-stu-id="7c370-228">Important note about rendering stereo content on HoloLens</span></span>

<span data-ttu-id="7c370-229">Windows Mixed Reality では、任意のシェーダーステージからレンダーターゲットの配列インデックスを設定する機能がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7c370-229">Windows Mixed Reality supports the ability to set the render target array index from any shader stage.</span></span> <span data-ttu-id="7c370-230">通常、これは、Direct3D 11 に対してセマンティックが定義されているため、ジオメトリシェーダーステージでのみ実行できるタスクです。</span><span class="sxs-lookup"><span data-stu-id="7c370-230">Normally, this is a task that could only be done in the geometry shader stage because of the way the semantic is defined for Direct3D 11.</span></span> <span data-ttu-id="7c370-231">ここでは、頂点とピクセルシェーダーの両方のステージを設定してレンダリングパイプラインを設定する方法の完全な例を示します。</span><span class="sxs-lookup"><span data-stu-id="7c370-231">Here, we show a complete example of how to set up a rendering pipeline with just the vertex and pixel shader stages set.</span></span> <span data-ttu-id="7c370-232">シェーダーコードは前述のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7c370-232">The shader code is as described above.</span></span>

<span data-ttu-id="7c370-233">**SpinningCubeRenderer:: Render** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-233">From **SpinningCubeRenderer::Render**:</span></span>

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

### <a name="important-note-about-rendering-on-non-hololens-devices"></a><span data-ttu-id="7c370-234">非 HoloLens デバイスでのレンダリングに関する重要な注意事項</span><span class="sxs-lookup"><span data-stu-id="7c370-234">Important note about rendering on non-HoloLens devices</span></span>

<span data-ttu-id="7c370-235">頂点シェーダーにレンダーターゲット配列インデックスを設定するには、グラフィックスドライバーがオプションの Direct3D 11.3 機能 (HoloLens がサポート) をサポートしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-235">Setting the render target array index in the vertex shader requires that the graphics driver supports an optional Direct3D 11.3 feature, which HoloLens does support.</span></span> <span data-ttu-id="7c370-236">アプリがレンダリング用のその手法だけを安全に実装でき、すべての要件が Microsoft HoloLens で実行されるようになります。</span><span class="sxs-lookup"><span data-stu-id="7c370-236">Your app may can safely implement just that technique for rendering, and all requirements will be met for running on the Microsoft HoloLens.</span></span>

<span data-ttu-id="7c370-237">HoloLens エミュレーターも使用する場合があります。これは、holographic アプリ用の強力な開発ツールであり、windows 10 Pc に接続されている Windows Mixed Reality イマーシブヘッドセットデバイスをサポートします。</span><span class="sxs-lookup"><span data-stu-id="7c370-237">It may be the case that you want to use the HoloLens emulator as well, which can be a powerful development tool for your holographic app - and support Windows Mixed Reality immersive headset devices that are attached to Windows 10 PCs.</span></span> <span data-ttu-id="7c370-238">非 HoloLens レンダリングパスのサポート-すべての Windows Mixed Reality で、Windows Holographic アプリケーションテンプレートにも組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="7c370-238">Support for the non-HoloLens rendering path - for all of Windows Mixed Reality - is also built into the Windows Holographic app template.</span></span> <span data-ttu-id="7c370-239">テンプレートコードには、開発用 PC の GPU で holographic アプリを実行できるようにするコードがあります。</span><span class="sxs-lookup"><span data-stu-id="7c370-239">In the template code, you'll find code to enable your holographic app to run on the GPU in your development PC.</span></span> <span data-ttu-id="7c370-240">**DeviceResources** クラスで、このオプションの機能のサポートを確認する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7c370-240">Here's how the **DeviceResources** class checks for this optional feature support.</span></span>

<span data-ttu-id="7c370-241">**DeviceResources:: CreateDeviceResources** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-241">From **DeviceResources::CreateDeviceResources**:</span></span>

```cpp
// Check for device support for the optional feature that allows setting the render target array index from the vertex shader stage.
D3D11_FEATURE_DATA_D3D11_OPTIONS3 options;
m_d3dDevice->CheckFeatureSupport(D3D11_FEATURE_D3D11_OPTIONS3, &options, sizeof(options));
if (options.VPAndRTArrayIndexFromAnyShaderFeedingRasterizer)
{
    m_supportsVprt = true;
}
```

<span data-ttu-id="7c370-242">このオプションの機能を使用せずにレンダリングをサポートするには、アプリで geometry シェーダーを使用してレンダーターゲットの配列インデックスを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-242">To support rendering without this optional feature, your app must use a geometry shader to set the render target array index.</span></span> <span data-ttu-id="7c370-243">このスニペットは、 **VSSetConstantBuffers** の *後*、前のセクションで説明したコード例の **pssetshader** の *前* に追加されます。これは、HoloLens でのステレオのレンダリング方法を説明するものです。</span><span class="sxs-lookup"><span data-stu-id="7c370-243">This snippet would be added *after* **VSSetConstantBuffers**, and *before* **PSSetShader** in the code example shown in the previous section that explains how to render stereo on HoloLens.</span></span>

<span data-ttu-id="7c370-244">**SpinningCubeRenderer:: Render** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-244">From **SpinningCubeRenderer::Render**:</span></span>

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

<span data-ttu-id="7c370-245">**HLSL メモ**: この例では、TEXCOORD0 など、常に許可されているシェーダーセマンティクスを使用して、レンダーターゲットの配列インデックスを geometry シェーダーに渡す若干変更された頂点シェーダーも読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-245">**HLSL NOTE**: In this case, you must also load a slightly modified vertex shader that passes the render target array index to the geometry shader using an always-allowed shader semantic, such as TEXCOORD0.</span></span> <span data-ttu-id="7c370-246">ジオメトリシェーダーは、作業を行う必要はありません。テンプレートジオメトリシェーダーは、すべてのデータを処理します。ただし、render ターゲットの配列インデックスは除き、SV_RenderTargetArrayIndex セマンティックを設定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="7c370-246">The geometry shader doesn't have to do any work; the template geometry shader passes through all data, with the exception of the render target array index, which is used to set the SV_RenderTargetArrayIndex semantic.</span></span>

<span data-ttu-id="7c370-247">**GeometryShader** のアプリテンプレートコード:</span><span class="sxs-lookup"><span data-stu-id="7c370-247">App template code for **GeometryShader.hlsl**:</span></span>

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

## <a name="present"></a><span data-ttu-id="7c370-248">存在</span><span class="sxs-lookup"><span data-stu-id="7c370-248">Present</span></span>

### <a name="enable-the-holographic-frame-to-present-the-swap-chain"></a><span data-ttu-id="7c370-249">Holographic フレームでスワップチェーンを表示できるようにします</span><span class="sxs-lookup"><span data-stu-id="7c370-249">Enable the holographic frame to present the swap chain</span></span>

<span data-ttu-id="7c370-250">Windows Mixed Reality では、システムによってスワップチェーンが制御されます。</span><span class="sxs-lookup"><span data-stu-id="7c370-250">With Windows Mixed Reality, the system controls the swap chain.</span></span> <span data-ttu-id="7c370-251">次に、システムは、各 holographic カメラへのフレームの表示を管理して、高品質なユーザーエクスペリエンスを実現します。</span><span class="sxs-lookup"><span data-stu-id="7c370-251">The system then manages presenting frames to each holographic camera to ensure a high-quality user experience.</span></span> <span data-ttu-id="7c370-252">また、イメージの安定化や Mixed Reality のキャプチャなどのシステムの側面を最適化するために、各カメラの各フレームを更新するためのビューポートも用意されています。</span><span class="sxs-lookup"><span data-stu-id="7c370-252">It also provides a viewport update each frame, for each camera, to optimize aspects of the system such as image stabilization or Mixed Reality Capture.</span></span> <span data-ttu-id="7c370-253">そのため、DirectX を使用している holographic アプリは、DXGI スワップチェーンでは **を呼び出す** ことができません。</span><span class="sxs-lookup"><span data-stu-id="7c370-253">So, a holographic app using DirectX doesn't call **Present** on a DXGI swap chain.</span></span> <span data-ttu-id="7c370-254">代わりに、 <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> クラスを使用して、フレームを描画した後、そのすべてのスワップチェーンを表示します。</span><span class="sxs-lookup"><span data-stu-id="7c370-254">Instead, you use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class to present all swapchains for a frame once you're done drawing it.</span></span>

<span data-ttu-id="7c370-255">From **DeviceResources::P** 再送信します。</span><span class="sxs-lookup"><span data-stu-id="7c370-255">From **DeviceResources::Present**:</span></span>

```
HolographicFramePresentResult presentResult = frame.PresentUsingCurrentPrediction();
```

<span data-ttu-id="7c370-256">既定では、この API はフレームが終了するまで待機してから制御を戻します。</span><span class="sxs-lookup"><span data-stu-id="7c370-256">By default, this API waits for the frame to finish before it returns.</span></span> <span data-ttu-id="7c370-257">Holographic アプリは、新しいフレームで作業を開始する前に、前のフレームが終了するまで待機する必要があります。これにより、待機時間が短縮され、Holographic フレーム予測の結果が向上します。</span><span class="sxs-lookup"><span data-stu-id="7c370-257">Holographic apps should wait for the previous frame to finish before starting work on a new frame, because this reduces latency and allows for better results from holographic frame predictions.</span></span> <span data-ttu-id="7c370-258">これは難しいルールではなく、1つの画面の更新をレンダリングするのに時間がかかるフレームがある場合は、HolographicFramePresentWaitBehavior パラメーターを使用して <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">Current予測</a>を実行することで、この待機を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="7c370-258">This isn't a hard rule, and if you have frames that take longer than one screen refresh to render you can disable this wait by passing the HolographicFramePresentWaitBehavior parameter to <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction" target="_blank">PresentUsingCurrentPrediction</a>.</span></span> <span data-ttu-id="7c370-259">この場合、GPU に継続的な負荷を維持するために、非同期レンダリングスレッドを使用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-259">In this case, you would likely use an asynchronous rendering thread to maintain a continuous load on the GPU.</span></span> <span data-ttu-id="7c370-260">HoloLens デバイスのリフレッシュレートは 60 hz で、1つのフレームの期間は約16ミリ秒です。</span><span class="sxs-lookup"><span data-stu-id="7c370-260">The refresh rate of the HoloLens device is 60 hz, where one frame has a duration of approximately 16 ms.</span></span> <span data-ttu-id="7c370-261">イマーシブヘッドセットデバイスは、60 hz から 90 hz までの範囲で指定できます。ディスプレイを 90 hz で更新すると、各フレームの期間は約11ミリ秒になります。</span><span class="sxs-lookup"><span data-stu-id="7c370-261">Immersive headset devices can range from 60 hz to 90 hz; when refreshing the display at 90 hz, each frame will have a duration of approximately 11 ms.</span></span>

### <a name="handle-devicelost-scenarios-in-cooperation-with-the-holographicframe"></a><span data-ttu-id="7c370-262">HolographicFrame と連携して、Devicのシナリオを処理します</span><span class="sxs-lookup"><span data-stu-id="7c370-262">Handle DeviceLost scenarios in cooperation with the HolographicFrame</span></span>

<span data-ttu-id="7c370-263">DirectX 11 アプリは通常、DXGI スワップチェーンの **present** 関数によって返された HRESULT を確認して、 **devicループ** エラーが発生したかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="7c370-263">DirectX 11 apps would typically want to check the HRESULT returned by the DXGI swap chain's **Present** function to find out if there was a **DeviceLost** error.</span></span> <span data-ttu-id="7c370-264"><a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a>クラスはこれを処理します。</span><span class="sxs-lookup"><span data-stu-id="7c370-264">The <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframe" target="_blank">HolographicFrame</a> class handles this for you.</span></span> <span data-ttu-id="7c370-265">返された <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> を調べて、Direct3D デバイスとデバイスベースのリソースを解放して再作成する必要があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="7c370-265">Inspect the returned <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicframepresentresult" target="_blank">HolographicFramePresentResult</a> to find out if you need to release and recreate the Direct3D device and device-based resources.</span></span>

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

<span data-ttu-id="7c370-266">Direct3D デバイスが失われ、再作成した場合は、新しいデバイスの使用を開始するように <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> に指示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-266">If the Direct3D device was lost, and you did recreate it, you have to tell the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a> to start using the new device.</span></span> <span data-ttu-id="7c370-267">スワップチェーンは、このデバイスに対して再作成されます。</span><span class="sxs-lookup"><span data-stu-id="7c370-267">The swap chain will be recreated for this device.</span></span>

<span data-ttu-id="7c370-268">**DeviceResources:: InitializeUsingHolographicSpace** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-268">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

```
m_holographicSpace.SetDirect3D11Device(m_d3dInteropDevice);
```

<span data-ttu-id="7c370-269">フレームが表示されたら、メインのプログラムループに戻り、次のフレームに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="7c370-269">Once your frame is presented, you can return back to the main program loop and allow it to continue to the next frame.</span></span>

## <a name="hybrid-graphics-pcs-and-mixed-reality-applications"></a><span data-ttu-id="7c370-270">ハイブリッドグラフィックス Pc と mixed reality アプリケーション</span><span class="sxs-lookup"><span data-stu-id="7c370-270">Hybrid graphics PCs and mixed reality applications</span></span>

<span data-ttu-id="7c370-271">Windows 10 の作成者更新 Pc は、離散 Gpu と統合 Gpu の **両方** で構成できます。</span><span class="sxs-lookup"><span data-stu-id="7c370-271">Windows 10 Creators Update PCs may be configured with **both** discrete and integrated GPUs.</span></span> <span data-ttu-id="7c370-272">これらの種類のコンピューターでは、ヘッドセットが接続されているアダプターが Windows によって選択されます。</span><span class="sxs-lookup"><span data-stu-id="7c370-272">With these types of computers, Windows will choose the adapter the headset is connected to.</span></span> <span data-ttu-id="7c370-273">アプリケーションでは、作成する DirectX デバイスで同じアダプターが使用されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-273">Applications must ensure the DirectX device it creates uses the same adapter.</span></span>

<span data-ttu-id="7c370-274">一般的な Direct3D サンプルコードでは、既定のハードウェアアダプターを使用して DirectX デバイスを作成する方法を示しています。このハードウェアアダプターは、ヘッドホンで使用されているものと同じではない場合があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-274">Most general Direct3D sample code demonstrates creating a DirectX device using the default hardware adapter, which on a hybrid system may not be the same as the one used for the headset.</span></span>

<span data-ttu-id="7c370-275">問題を回避するには、いずれかの<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>の<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterID</a>を使用します。PrimaryAdapterId () または<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>。AdapterId ()。</span><span class="sxs-lookup"><span data-stu-id="7c370-275">To work around any issues, use the <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicadapterid" target="_blank">HolographicAdapterID</a> from either <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace" target="_blank">HolographicSpace</a>.PrimaryAdapterId() or <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay" target="_blank">HolographicDisplay</a>.AdapterId().</span></span> <span data-ttu-id="7c370-276">この adapterId を使用すると、IDXGIFactory4 を使用して適切に DXGIAdapter を選択できます。</span><span class="sxs-lookup"><span data-stu-id="7c370-276">This adapterId can then be used to select the right DXGIAdapter using IDXGIFactory4.EnumAdapterByLuid.</span></span>

<span data-ttu-id="7c370-277">**DeviceResources:: InitializeUsingHolographicSpace** から:</span><span class="sxs-lookup"><span data-stu-id="7c370-277">From **DeviceResources::InitializeUsingHolographicSpace**:</span></span>

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

<span data-ttu-id="7c370-278">**IDXGIAdapter を使用するように DeviceResources:: CreateDeviceResources を更新** するコード</span><span class="sxs-lookup"><span data-stu-id="7c370-278">Code to **update DeviceResources::CreateDeviceResources to use IDXGIAdapter**</span></span>

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

<span data-ttu-id="7c370-279">**ハイブリッドグラフィックスとメディアファンデーション**</span><span class="sxs-lookup"><span data-stu-id="7c370-279">**Hybrid graphics and Media Foundation**</span></span>

<span data-ttu-id="7c370-280">ハイブリッドシステムでメディアファンデーションを使用すると、メディアファンデーションがシステムの動作を既定にするため、ビデオがレンダリングされない、またはビデオテクスチャが破損する問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-280">Using Media Foundation on hybrid systems may cause issues where video won't render or video texture are corrupt because Media Foundation is defaulting to a system behavior.</span></span> <span data-ttu-id="7c370-281">場合によっては、マルチスレッドをサポートするために個別の ID3D11Device を作成する必要があり、適切な作成フラグが設定されます。</span><span class="sxs-lookup"><span data-stu-id="7c370-281">In some scenarios, creating a separate ID3D11Device is required to support multi-threading and the correct creation flags are set.</span></span>

<span data-ttu-id="7c370-282">ID3D11Device を初期化するときは、D3D11_CREATE_DEVICE_VIDEO_SUPPORT フラグを D3D11_CREATE_DEVICE_FLAG の一部として定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7c370-282">When initializing the ID3D11Device, D3D11_CREATE_DEVICE_VIDEO_SUPPORT flag must be defined as part of the D3D11_CREATE_DEVICE_FLAG.</span></span> <span data-ttu-id="7c370-283">デバイスとコンテキストが作成されたら、 <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">Setmultithreadprotected</a> を呼び出してマルチスレッドを有効にします。</span><span class="sxs-lookup"><span data-stu-id="7c370-283">Once the device and context is created, call <a href="https://docs.microsoft.com/windows/desktop/api/d3d10/nf-d3d10-id3d10multithread-setmultithreadprotected" target="_blank">SetMultithreadProtected</a> to enable multithreading.</span></span> <span data-ttu-id="7c370-284">デバイスを <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">Imfdxgidevicemanager</a>に関連付けるには、 <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">Imfdxgidevicemanager:: resetdevice</a> 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="7c370-284">To associate the device with the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nn-mfobjects-imfdxgidevicemanager" target="_blank">IMFDXGIDeviceManager</a>, use the <a href="https://docs.microsoft.com/windows/desktop/api/mfobjects/nf-mfobjects-imfdxgidevicemanager-resetdevice" target="_blank">IMFDXGIDeviceManager::ResetDevice</a> function.</span></span>

<span data-ttu-id="7c370-285">**ID3D11Device を IMFDXGIDeviceManager に関連付ける** コード。</span><span class="sxs-lookup"><span data-stu-id="7c370-285">Code to **associate a ID3D11Device with IMFDXGIDeviceManager**:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7c370-286">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c370-286">See also</span></span>
* [<span data-ttu-id="7c370-287">DirectX の座標系</span><span class="sxs-lookup"><span data-stu-id="7c370-287">Coordinate systems in DirectX</span></span>](coordinate-systems-in-directx.md)
* [<span data-ttu-id="7c370-288">HoloLens エミュレーターを使用する</span><span class="sxs-lookup"><span data-stu-id="7c370-288">Using the HoloLens emulator</span></span>](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
