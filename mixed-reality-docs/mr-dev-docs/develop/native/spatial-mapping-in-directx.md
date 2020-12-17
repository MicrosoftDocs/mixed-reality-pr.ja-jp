---
title: DirectX の空間マッピング
description: ユニバーサル Windows プラットフォーム SDK に付属する空間マッピングサンプルアプリケーションを含め、DirectX アプリで空間マッピングを実装する方法について説明します。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows mixed reality, 空間マッピング, 環境, 相互作用, directx, winrt, api, サンプルコード, UWP, SDK, チュートリアル
ms.openlocfilehash: fa372473939222ef4be7ca36076a17241173c441
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612916"
---
# <a name="spatial-mapping-in-directx"></a>DirectX の空間マッピング

> [!NOTE]
> この記事は、従来の WinRT ネイティブ Api に関連しています。  新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](openxr-getting-started.md)** を使用することをお勧めします。

このトピックでは、DirectX アプリで [空間マッピング](../../design/spatial-mapping.md) を実装する方法について説明します。これには、ユニバーサル Windows プラットフォーム SDK でパッケージ化された空間マッピングサンプルアプリケーションの詳細な説明が含まれます。

このトピックでは、 [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP コードサンプルのコードを使用します。

>[!NOTE]
>この記事のコードスニペットでは、 [C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)で使用される c + c++ 17 準拠の c++/WinRT ではなく、c++/cx の使用方法を現在説明しています。  概念は C++/WinRT プロジェクトに相当しますが、コードを変換する必要があります。

## <a name="device-support"></a>デバイス サポート

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>機能</strong></td>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>空間マッピング</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a>DirectX 開発の概要

空間マッピングのネイティブアプリケーション開発では、 [Windows](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) のような名前空間の api を使用します。 これらの Api を使用すると、空間マッピング Api が [Unity](../unity/spatial-mapping-in-unity.md)によって公開されるのと同じ方法で、空間マッピング機能を完全に制御できます。

### <a name="perception-apis"></a>認識 Api

空間マッピング開発の主な種類は次のとおりです。
* [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) は、SpatialSurfaceInfo オブジェクトの形式で、ユーザーの近くにある、アプリケーションで指定された領域内のサーフェイスに関する情報を提供します。
* [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) は、一意の ID、境界ボリューム、最後の変更の時間など、1つの既存空間サーフェスを表します。 要求に応じて非同期的に SpatialSurfaceMesh を提供します。
* [SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) には、SpatialSurfaceInfo から要求された SpatialSurfaceMesh オブジェクトをカスタマイズするために使用されるパラメーターが含まれています。
* [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) は、1つの空間サーフェスのメッシュデータを表します。 頂点の位置、頂点の法線、三角形のインデックスのデータは、メンバーの SpatialSurfaceMeshBuffer オブジェクトに含まれています。
* [SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) は、単一の種類のメッシュデータをラップします。

これらの Api を使用してアプリケーションを開発する場合、基本的なプログラムフローは次のようになります (以下で説明するサンプルアプリケーションで示すように)。
- **SpatialSurfaceObserver を設定する**
  - [Requestaccessasync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)を呼び出して、ユーザーがアプリケーションにデバイスの空間マッピング機能を使用するためのアクセス許可を与えられていることを確認します。
  - SpatialSurfaceObserver オブジェクトをインスタンス化します。
  - 空間サーフェスに関する情報が必要な領域を指定するには、 [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) を呼び出します。 今後、この関数を呼び出して、これらのリージョンを変更することができます。 各リージョンは、 [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)を使用して指定されます。
  - [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx)イベントに登録します。これは、指定した領域の空間サーフェスに関する新しい情報が利用可能になるたびに起動されます。
- **ObservedSurfacesChanged イベントの処理**
  - イベントハンドラーで、 [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) を呼び出して、SpatialSurfaceInfo オブジェクトのマップを受信します。 このマップを使用して、 [ユーザーの環境内に存在](../../design/spatial-mapping.md#mesh-caching)する空間サーフェスのレコードを更新できます。
  - 各 SpatialSurfaceInfo オブジェクトに対して、 [Trygetbounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) に対してクエリを実行し、選択した [空間座標系](../../design/coordinate-systems.md) で表現されるサーフェスの空間範囲を決定することができます。
  - 空間サーフェスのメッシュを要求する場合は、 [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx)を呼び出します。 三角形の密度、および返されるメッシュデータの形式を指定するオプションを指定できます。
- **メッシュの受信と処理**
  - TryComputeLatestMeshAsync を呼び出すたびに、1つの SpatialSurfaceMesh オブジェクトが非同期に返されます。
  - このオブジェクトから、含まれている SpatialSurfaceMeshBuffer オブジェクトにアクセスできます。これにより、メッシュの三角形のインデックス、頂点位置、および頂点法線を要求した場合にアクセスできます。 このデータは、メッシュのレンダリングに使用される [Direct3D 11 api](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) と直接互換性がある形式になります。
  - ここから、アプリケーションでメッシュデータを必要に応じて分析または [処理](../../design/spatial-mapping.md#mesh-processing) し、 [レンダリング](../../design/spatial-mapping.md#rendering) や物理的な [raycasting と競合](../../design/spatial-mapping.md#raycasting-and-collision)に使用することができます。
  - 注意すべき重要な点の1つは、メッシュの頂点位置 (メッシュのレンダリングに使用される頂点シェーダーなど) にスケールを適用して、バッファーに格納されている最適化された整数単位からメーターに変換する必要があることです。 このスケールを取得するには、 [Vertexpositionscale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)を呼び出します。

### <a name="troubleshooting"></a>トラブルシューティング
* [SpatialSurfaceMesh スケール](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)によって返されるスケールを使用して、頂点シェーダー内のメッシュ頂点の位置を必ずスケーリングしてください。

## <a name="spatial-mapping-code-sample-walkthrough"></a>空間マッピングコードサンプルのチュートリアル

[Holographic 空間マッピング](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)コードサンプルには、サーフェイスメッシュを管理および表示するためのインフラストラクチャを含む、アプリへのサーフェイスメッシュの読み込みを開始するために使用できるコードが含まれています。

ここでは、DirectX アプリに surface マッピング機能を追加する方法について説明します。 このコードを [Windows Holographic アプリケーションテンプレート](creating-a-holographic-directx-project.md) プロジェクトに追加することも、前に説明したコードサンプルを参照して操作することもできます。 このコードサンプルは、Windows Holographic アプリケーションテンプレートに基づいています。

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>SpatialPerception 機能を使用するようにアプリを設定する

アプリで空間マッピング機能を使用できます。 これが必要になるのは、空間メッシュがユーザーの環境を表しているためです。これは、プライベートデータと見なされる場合があります。 この機能をアプリの package.appxmanifest ファイルで宣言します。 次に例を示します。

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

この機能は、 **uap2** 名前空間から取得されます。 マニフェスト内のこの名前空間へのアクセスを取得するには、パッケージの> 要素に *xlmns* 属性として含め &lt; ます。 次に例を示します。

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a>空間マッピング機能のサポートを確認する

Windows Mixed Reality は、空間マッピングをサポートしていないデバイスを含む幅広いデバイスをサポートしています。 アプリで空間マッピングを使用できる場合、または空間マッピングを使用して機能を提供する場合は、使用する前に空間マッピングがサポートされていることを確認する必要があります。 たとえば、混合の現実のアプリで空間マッピングが必要な場合、ユーザーが空間マッピングを使用せずにデバイスで実行しようとすると、その効果に関するメッセージが表示されます。 または、アプリでユーザーの環境の代わりに独自の仮想環境をレンダリングすることができます。これは、空間マッピングが使用可能であった場合に発生するようなエクスペリエンスを提供します。 どのような場合でも、この API によって、アプリは空間マッピングデータを取得せず、適切な方法で応答するタイミングを認識できます。

現在のデバイスでの空間マッピングのサポートを確認するには、最初に UWP コントラクトがレベル4以上であることを確認してから、SpatialSurfaceObserver:: IsSupported () を呼び出します。 [Holographic 空間マッピング](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)コードサンプルのコンテキストでこれを行う方法を次に示します。 アクセスを要求する直前にサポートが確認されます。

SpatialSurfaceObserver:: IsSupported () API は、SDK バージョン15063以降で使用できます。 必要に応じて、この API を使用する前に、プロジェクトをプラットフォームバージョン15063に再ターゲットします。

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

UWP コントラクトがレベル4より小さい場合は、デバイスが空間マッピングを実行できるかのようにアプリを続行する必要があります。

### <a name="request-access-to-spatial-mapping-data"></a>空間マッピングデータへのアクセスを要求する

アプリケーションは、surface オブザーバーを作成する前に、空間マッピングデータにアクセスするためのアクセス許可を要求する必要があります。 次に、このページで後ほど詳しく説明する、Surface マッピングのコードサンプルに基づく例を示します。

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a>Surface オブザーバーを作成する

**Windows::P erception:: 空間::** surface 名前空間には、 [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)クラスが含まれています。このクラスは、 [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)で指定した1つ以上のボリュームを監視します。 [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)インスタンスを使用して、リアルタイムでサーフェイスメッシュデータにアクセスします。

**Appmain** から:

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

前のセクションで説明したように、アプリで使用できるようにするには、空間マッピングデータへのアクセスを要求する必要があります。 このアクセスは、HoloLens に自動的に付与されます。

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

次に、特定の境界ボリュームを観察するように surface オブザーバーを構成する必要があります。 ここでは、座標系の原点を中心とした、20x20x5 メートルの箱があることを確認します。

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

代わりに、複数の境界ボリュームを設定できます。

*これは擬似コードです。*

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

また、ビューを視するビューや、軸に沿っていない境界ボックスなど、他の境界図形を使用することもできます。

*これは擬似コードです。*

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

Surface マッピングデータを使用できない場合にアプリの動作を変える必要がある場合は、 [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) が **許可** されていない場合に応答するコードを記述できます。たとえば、デバイスにデバイスが搭載されていても、空間マッピング用のハードウェアがないため、このようなデバイスは許可されません。 これらのデバイスでは、代わりに、ユーザーの環境とデバイスの構成に関する情報を空間ステージに依存させる必要があります。

### <a name="initialize-and-update-the-surface-mesh-collection"></a>Surface メッシュコレクションの初期化と更新

Surface オブザーバーが正常に作成された場合、surface メッシュコレクションの初期化を続行できます。 ここでは、プルモデル API を使用して、現在観察されているサーフェスのセットをすぐに取得します。

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

Surface メッシュデータを取得するために使用できるプッシュモデルもあります。 プルモデルのみを使用するようにアプリをデザインすることもできます。選択した場合は、(たとえば、フレームごとに1回、またはゲームのセットアップ中など、特定の期間に) データをポーリングします。 その場合は、上記のコードが必要です。

このコードサンプルでは、教育目的目的で両方のモデルを使用する方法を説明しました。 ここでは、システムが変更を認識するたびに、最新の表面メッシュデータを受け取るイベントをサブスクライブします。

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

このコードサンプルは、これらのイベントに応答するようにも構成されています。 では、その方法について説明します。

**注:** これは、アプリがメッシュデータを処理するための最も効率的な方法ではない可能性があります。 このコードはわかりやすくするために記述されており、最適化されていません。

Surface メッシュデータは、key 値として[Platform:: guid](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx)を使用して[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)オブジェクトを格納する読み取り専用マップで提供されます。

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

このデータを処理するために、まずコレクションに含まれていないキー値を検索します。 サンプルアプリでのデータの格納方法の詳細については、このトピックの後半で説明します。

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

Surface メッシュコレクションに含まれていても、システムコレクションには存在しないサーフェスメッシュを削除する必要があります。 これを行うには、メッシュを追加および更新するために説明したのとは逆の操作を行う必要があります。アプリのコレクションでループし、システムコレクションに含まれている **Guid** があるかどうかを確認します。 システムコレクションに含まれていない場合は、私たちから削除します。

AppMain のイベントハンドラーから、次のようにします。

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

RealtimeSurfaceMeshRenderer でのメッシュ排除の実装は次のとおりです。

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a>Surface メッシュのデータバッファーを取得して使用する

Surface メッシュ情報の取得は、データコレクションをプルし、そのコレクションに更新を処理するのと同じように簡単でした。 ここでは、データの使用方法について詳しく説明します。

このコード例では、レンダリングにサーフェイスメッシュを使用することを選択しました。 これは、実際のサーフェイスの背後にある occluding ホログラムの一般的なシナリオです。 また、メッシュをレンダリングしたり、処理したバージョンをレンダリングして、アプリまたはゲームの機能の提供を開始する前に、どの領域がスキャンされるかをユーザーに示すこともできます。

このコードサンプルでは、前のセクションで説明したイベントハンドラーから表面メッシュの更新を受信したときにプロセスを開始します。 この関数の重要なコード行は、surface *メッシュ* を更新するための呼び出しです。今回はメッシュ情報を既に処理したため、必要に応じて頂点とインデックスのデータを取得しようとしています。

RealtimeSurfaceMeshRenderer から:

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

このサンプルコードは、データクラス **SurfaceMesh** がメッシュデータの処理とレンダリングを処理するように設計されています。 これらのメッシュは、 **RealtimeSurfaceMeshRenderer** が実際にマップを保持しているものです。 各ファイルには、SpatialSurfaceMesh が送信元のものへの参照があるため、メッシュの頂点またはインデックスバッファーにアクセスしたり、メッシュの変換を取得したりする必要があるときに、いつでも使用できます。 ここでは、更新が必要であるとしてメッシュにフラグを付けます。

SurfaceMesh から:

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

次にメッシュがそれ自体を描画するように要求されたときに、最初にフラグをチェックします。 更新が必要な場合は、頂点バッファーとインデックスバッファーが GPU 上で更新されます。

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

まず、生データバッファーを取得します。

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

次に、HoloLens によって提供されるメッシュデータを使用して、Direct3D デバイスバッファーを作成します。

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

**注:** 前のスニペットで使用した CreateDirectXBuffer ヘルパー関数については、「Surface Mapping のコードサンプル: SurfaceMesh, GetDataFromIBuffer. h」を参照してください。 これで、デバイスリソースの作成が完了し、メッシュが読み込まれ、更新とレンダリングの準備が整っていると見なされます。

### <a name="update-and-render-surface-meshes"></a>サーフェイスメッシュの更新とレンダリング

SurfaceMesh クラスには、特殊な更新関数があります。 各 [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) には独自の変換があり、このサンプルでは、 **SpatialStationaryReferenceFrame** の現在の座標系を使用して変換を取得します。 次に、GPU のモデル定数バッファーを更新します。

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

サーフェイスメッシュをレンダリングする時間があれば、コレクションをレンダリングする前にいくつかの準備作業を行います。 現在の表示構成にシェーダーパイプラインを設定し、入力アセンブラーステージを設定します。 Holographic カメラヘルパークラス **CameraResources** は、既にビュー/プロジェクション定数バッファーを設定しています。

**RealtimeSurfaceMeshRenderer:: Render** から:

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

この処理が完了したら、メッシュをループし、それぞれを描画するように指示します。 **注:** このサンプルコードは、任意の種類の視錐カリングを使用するように最適化されていませんが、アプリにこの機能を含める必要があります。

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

個々のメッシュは、頂点とインデックスバッファー、ストライド、およびモデル変換の定数バッファーを設定します。 Windows Holographic アプリテンプレートの回転するキューブと同様に、インスタンス化を使用してステレオスコピックバッファーにレンダリングします。

From **SurfaceMesh::D raw**:

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a>サーフェイスマッピングでの選択肢の表示

Surface Mapping のコードサンプルでは、表面メッシュデータのオクルーリングのみのレンダリング、および表面メッシュデータの画面表示のためのコードを提供します。 どちらのパスを選択するか、または両方とも、アプリケーションによって異なります。 このドキュメントでは、両方の構成について説明します。

**Holographic effect のオクルージョンバッファーのレンダリング**

まず、現在の仮想カメラのレンダーターゲットビューをクリアします。

AppMain .cpp から:

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

これは "事前レンダリング" パスです。 ここでは、メッシュレンダラーに深度だけを表示するように求めることによって、オクルージョンバッファーを作成します。 この構成ではレンダーターゲットビューをアタッチせず、メッシュレンダラーはピクセルシェーダーステージを **nullptr** に設定して、GPU がピクセルを描画しないようにします。 ジオメトリが深度バッファーにラスタライズされ、グラフィックスパイプラインがそこで停止します。

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

Surface マッピングのオクルーバッファーに対する追加の深度テストを使用して、ホログラムを描画できます。 このコードサンプルでは、画面の背後にある場合は、キューブのピクセルが異なる色で表示されます。

AppMain .cpp から:

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

SpecialEffectPixelShader のコードに基づいて次のようにします。

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

**注:****GatherDepthLess** ルーチンについては、「Surface Mapping のコードサンプル: SpecialEffectPixelShader」を参照してください。

**画面にサーフェイスメッシュデータをレンダリングする**

また、表面メッシュをステレオディスプレイバッファーに描画するだけでもかまいません。 全面を照明付きで描画することを選択しましたが、ワイヤーフレームの描画、レンダリング前のメッシュの処理、テクスチャマップの適用などを自由に行うことができます。

ここでは、このコードサンプルでは、コレクションを描画するようにメッシュレンダラーに指示しています。 ここでは、深度のみのパスを指定していません。ピクセルシェーダーをアタッチし、現在の仮想カメラに指定したターゲットを使用してレンダリングパイプラインを完成させます。

```cpp
// Spatial Mapping mesh rendering pass: Draw Spatial Mapping mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a>関連項目
* [ホログラフィック DirectX プロジェクトを作成する](creating-a-holographic-directx-project.md)
* [Windows... 空間 API](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
