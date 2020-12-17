---
title: DirectX の座標系
description: DirectX の座標系と、空間ロケーター、参照フレーム、空間アンカーを使用した Mixed Reality について説明します。 SpatialStage を使用して、アンカーの損失の追跡、アンカーの保存と読み込み、およびイメージの安定化を行います。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: 混合現実、空間ロケーター、空間参照フレーム、空間座標システム、空間ステージ、サンプルコード、イメージの安定化、空間アンカー、空間アンカーストア、追跡の損失、チュートリアル、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実のヘッドセット
ms.openlocfilehash: 7bf2309f3fb6264d6b1a5232f7ead78b771c1649
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613116"
---
# <a name="coordinate-systems-in-directx"></a>DirectX の座標系

> [!NOTE]
> この記事は、従来の WinRT ネイティブ Api に関連しています。  新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](openxr-getting-started.md)** を使用することをお勧めします。

[座標系](../../design/coordinate-systems.md) は、Windows Mixed Reality api によって提供される空間を理解するための基礎となります。

現在の接続されている VR または単一の部屋の VR デバイスは、追跡領域に1つの主要な座標系を確立します。 HoloLens のような Mixed Reality デバイスは、大規模な未定義の環境向けに設計されています。デバイスを検出し、ユーザーが説明するように、その環境について学習します。 デバイスは、ユーザーの部屋に関する知識を継続的に向上させるように調整されますが、アプリケーションの有効期間中に相互に関係が変化する座標系が得られます。 Windows Mixed Reality では、世界中に接続されている参照フレームによって組み込まれたイマーシブヘッドセットから、さまざまなデバイスをサポートしています。

>[!NOTE]
>この記事のコードスニペットでは、 [C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)で使用される c + c++ 17 準拠の c++/WinRT ではなく、c++/cx の使用方法を現在説明しています。  概念は C++/WinRT プロジェクトに相当しますが、コードを変換する必要があります。

## <a name="spatial-coordinate-systems-in-windows"></a>Windows の空間座標系

Windows での実際の座標系の理由として使用されるコア型は <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>です。 この型のインスタンスは任意の座標系を表します。変換行列データを取得するためのメソッドを提供します。このデータを使用して、それぞれの詳細を理解することなく、2つの座標系の間で変換を行うことができます。

空間情報を返すメソッドは、SpatialCoordinateSystem パラメーターを使用して、返される座標に最も適した座標系を決定できます。 空間情報は、ユーザーの周囲のポイント、線、またはボリュームとして表され、これらの座標の単位は常にメートル単位になります。

SpatialCoordinateSystem には、デバイスの位置を表すものを含む、他の座標系との動的な関係があります。 どの時点でも、デバイスは他の座標系を検出できません。 ほとんどの座標系では、アプリは特定の期間内に配置できない期間を処理する準備ができている必要があります。

アプリケーションで直接 SpatialCoordinateSystems を作成するのではなく、認識 Api を介して使用する必要があります。 認識 Api には3つの主要なソースがあり、それぞれが [ [座標系](../../design/coordinate-systems.md) ] ページで説明されている概念に対応しています。
* 参照の静止フレームを取得するには、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> を作成するか、現在の <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>から取得します。
* 空間アンカーを取得するには、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>を作成します。
* アタッチされた参照のフレームを取得するには、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>を作成します。

これらのオブジェクトによって返されるすべての座標系は、右ききで、+ y が上、+ x が右、+ z の後方になります。 正の x 方向の左側または右側の指をポイントし、正の y 方向に curling することによって、正の z 軸の方向を思い出すことができます。 親指が指している方向は、自身に向かうかまたは離れる方向のいずれかとなり、その座標系の z 軸の正の向きが指す方向となります。 次の図は、これらの 2 つの座標系を示しています。

![左側および右側の座標系](images/left-hand-right-hand.gif)<br>
*左側および右側の座標系*

<a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>クラスを使用して、HoloLens への接続されたフレームまたは静止したフレーム参照を、HoloLens の位置に基づいて SpatialCoordinateSystem に作成します。 このプロセスの詳細については、次のセクションに進んでください。

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a>空間ステージを使用して、世界中にホログラムを配置する

不透明な Windows Mixed Reality イマーシブヘッドセットの座標系には、static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference:: Current</a> プロパティを使用してアクセスします。 この API は次のものを提供します。

* 座標系
* Windows media player が装着されているか、モバイルデバイスであるかに関する情報
* プレーヤーがモバイルであるかどうかを調べるための安全な領域の境界
* ヘッドセットが指向性であるかどうかを示す値。 
* 空間ステージを更新するためのイベントハンドラー。

まず、空間ステージを取得し、それに対する更新をサブスクライブします。 

**空間ステージの初期化** のコード

```
SpatialStageManager::SpatialStageManager(
    const std::shared_ptr<DX::DeviceResources>& deviceResources, 
    const std::shared_ptr<SceneController>& sceneController)
    : m_deviceResources(deviceResources), m_sceneController(sceneController)
{
    // Get notified when the stage is updated.
    m_spatialStageChangedEventToken = SpatialStageFrameOfReference::CurrentChanged +=
        ref new EventHandler<Object^>(std::bind(&SpatialStageManager::OnCurrentChanged, this, _1));

    // Make sure to get the current spatial stage.
    OnCurrentChanged(nullptr);
}
```

OnCurrentChanged メソッドでは、アプリは空間ステージを調べて、プレーヤーエクスペリエンスを更新する必要があります。 この例では、ステージの境界と、ユーザーによって指定された開始位置、およびステージのビューの範囲および移動プロパティの範囲の視覚エフェクトを提供します。 また、ステージを提供できない場合は、独自の静止座標系にフォールバックします。


**空間ステージの更新** のコード

```
void SpatialStageManager::OnCurrentChanged(Object^ /*o*/)
{
    // The event notifies us that a new stage is available.
    // Get the current stage.
    m_currentStage = SpatialStageFrameOfReference::Current;

    // Clear previous content.
    m_sceneController->ClearSceneObjects();

    if (m_currentStage != nullptr)
    {
        // Obtain stage geometry.
        auto stageCoordinateSystem = m_currentStage->CoordinateSystem;
        auto boundsVertexArray = m_currentStage->TryGetMovementBounds(stageCoordinateSystem);

        // Visualize the area where the user can move around.
        std::vector<float3> boundsVertices;
        boundsVertices.resize(boundsVertexArray->Length);
        memcpy(boundsVertices.data(), boundsVertexArray->Data, boundsVertexArray->Length * sizeof(float3));
        std::vector<unsigned short> indices = TriangulatePoints(boundsVertices);
        m_stageBoundsShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(boundsVertices),
                    indices,
                    XMFLOAT3(DirectX::Colors::SeaGreen),
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageBoundsShape);

        // In this sample, we draw a visual indicator for some spatial stage properties.
        // If the view is forward-only, the indicator is a half circle pointing forward - otherwise, it
        // is a full circle.
        // If the user can walk around, the indicator is blue. If the user is seated, it is red.

        // The indicator is rendered at the origin - which is where the user declared the center of the
        // stage to be during setup - above the plane of the stage bounds object.
        float3 visibleAreaCenter = float3(0.f, 0.001f, 0.f);

        // Its shape depends on the look direction range.
        std::vector<float3> visibleAreaIndicatorVertices;
        if (m_currentStage->LookDirectionRange == SpatialLookDirectionRange::ForwardOnly)
        {
            // Half circle for forward-only look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 9, XM_PI);
        }
        else
        {
            // Full circle for omnidirectional look direction range.
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.25f, 16, XM_2PI);
        }

        // Its color depends on the movement range.
        XMFLOAT3 visibleAreaColor;
        if (m_currentStage->MovementRange == SpatialMovementRange::NoMovement)
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::OrangeRed);
        }
        else
        {
            visibleAreaColor = XMFLOAT3(DirectX::Colors::Aqua);
        }

        std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);

        // Visualize the look direction range.
        m_stageVisibleAreaIndicatorShape =
            std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    visibleAreaColor,
                    stageCoordinateSystem);
        m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
    }
    else
    {
        // No spatial stage was found.
        // Fall back to a stationary coordinate system.
        auto locator = SpatialLocator::GetDefault();
        if (locator)
        {
            m_stationaryFrameOfReference = locator->CreateStationaryFrameOfReferenceAtCurrentLocation();

            // Render an indicator, so that we know we fell back to a mode without a stage.
            std::vector<float3> visibleAreaIndicatorVertices;
            float3 visibleAreaCenter = float3(0.f, -2.0f, 0.f);
            visibleAreaIndicatorVertices = CreateCircle(visibleAreaCenter, 0.125f, 16, XM_2PI);
            std::vector<unsigned short> visibleAreaIndicatorIndices = TriangulatePoints(visibleAreaIndicatorVertices);
            m_stageVisibleAreaIndicatorShape =
                std::make_shared<SceneObject>(
                    m_deviceResources,
                    reinterpret_cast<std::vector<XMFLOAT3>&>(visibleAreaIndicatorVertices),
                    visibleAreaIndicatorIndices,
                    XMFLOAT3(DirectX::Colors::LightSlateGray),
                    m_stationaryFrameOfReference->CoordinateSystem);
            m_sceneController->AddSceneObject(m_stageVisibleAreaIndicatorShape);
        }
    }
}
```

ステージの境界を定義する頂点のセットは、時計回りの順序で提供されます。 Windows Mixed Reality シェルでは、ユーザーがアプローチするときに境界にフェンスが描画されますが、自分の目的に合わせて triangularize 領域を作成することもできます。 次のアルゴリズムを使用して、ステージを triangularize できます。


**空間ステージ triangularization** のコード

```
std::vector<unsigned short> SpatialStageManager::TriangulatePoints(std::vector<float3> const& vertices)
{
    size_t const& vertexCount = vertices.size();

    // Segments of the shape are removed as they are triangularized.
    std::vector<bool> vertexRemoved;
    vertexRemoved.resize(vertexCount, false);
    unsigned int vertexRemovedCount = 0;

    // Indices are used to define triangles.
    std::vector<unsigned short> indices;

    // Decompose into convex segments.
    unsigned short currentVertex = 0;
    while (vertexRemovedCount < (vertexCount - 2))
    {
        // Get next triangle:
        // Start with the current vertex.
        unsigned short index1 = currentVertex;

        // Get the next available vertex.
        unsigned short index2 = index1 + 1;

        // This cycles to the next available index.
        auto CycleIndex = [=](unsigned short indexToCycle, unsigned short stopIndex)
        {
            // Make sure the index does not exceed bounds.
            if (indexToCycle >= unsigned short(vertexCount))
            {
                indexToCycle -= unsigned short(vertexCount);
            }

            while (vertexRemoved[indexToCycle])
            {
                // If the vertex is removed, go to the next available one.
                ++indexToCycle;

                // Make sure the index does not exceed bounds.
                if (indexToCycle >= unsigned short(vertexCount))
                {
                    indexToCycle -= unsigned short(vertexCount);
                }

                // Prevent cycling all the way around.
                // Should not be needed, as we limit with the vertex count.
                if (indexToCycle == stopIndex)
                {
                    break;
                }
            }

            return indexToCycle;
        };
        index2 = CycleIndex(index2, index1);

        // Get the next available vertex after that.
        unsigned short index3 = index2 + 1;
        index3 = CycleIndex(index3, index1);

        // Vertices that may define a triangle inside the 2D shape.
        auto& v1 = vertices[index1];
        auto& v2 = vertices[index2];
        auto& v3 = vertices[index3];

        // If the projection of the first segment (in clockwise order) onto the second segment is 
        // positive, we know that the clockwise angle is less than 180 degrees, which tells us 
        // that the triangle formed by the two segments is contained within the bounding shape.
        auto v2ToV1 = v1 - v2;
        auto v2ToV3 = v3 - v2;
        float3 normalToV2ToV3 = { -v2ToV3.z, 0.f, v2ToV3.x };
        float projectionOntoNormal = dot(v2ToV1, normalToV2ToV3);
        if (projectionOntoNormal >= 0)
        {
            // Triangle is contained within the 2D shape.

            // Remove peak vertex from the list.
            vertexRemoved[index2] = true;
            ++vertexRemovedCount;

            // Create the triangle.
            indices.push_back(index1);
            indices.push_back(index2);
            indices.push_back(index3);

            // Continue on to the next outer triangle.
            currentVertex = index3;
        }
        else
        {
            // Triangle is a cavity in the 2D shape.
            // The next triangle starts at the inside corner.
            currentVertex = index2;
        }
    }

    indices.shrink_to_fit();
    return indices;
}
```

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a>静止した参照フレームを使用して、世界中にホログラムを配置する

[SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx)クラスは、ユーザーが移動するときに、ユーザーの周囲を基準にして静止した[まま](../../design/coordinate-systems.md#stationary-frame-of-reference)になる参照のフレームを表します。 この参照フレームでは、デバイスの近くで座標が安定していることが優先されます。 SpatialStationaryFrameOfReference の主な用途は、ホログラムをレンダリングするときに、レンダリングエンジン内で基になるワールド座標系として機能することです。

SpatialStationaryFrameOfReference を取得するには、 [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) クラスを使用して、 [createokary](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx)を呼び出します。

Windows Holographic アプリテンプレートのコードから:

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* 静止参照フレームは、全体の領域を基準とした最適な位置を提供するように設計されています。 その参照フレーム内の個々の位置は、少しずつ移動できます。 これは、デバイスが環境に関する詳細を学習するため、正常です。
* 個々のホログラムが正確に配置されている必要がある場合は、SpatialAnchor を使用して、個々のホログラムを実際の世界の位置に固定する必要があります。たとえば、ユーザーが特別な関心を持っていることを示すポイントなどです。 アンカーの位置はずれませんが、修正することができます。アンカーは、修正が発生した後、次のフレームから始まる修正された位置を使用します。

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a>空間アンカーを使用して、世界中にホログラムを配置する

[空間アンカー](../../design/coordinate-systems.md#spatial-anchors) は、実際の世界の特定の場所にホログラムを配置するための優れた方法であり、システムによって、アンカーが時間の経過と共に維持されるようにします。 このトピックでは、アンカーを作成して使用する方法と、アンカーデータを操作する方法について説明します。

選択した SpatialCoordinateSystem 内の任意の位置と向きで、SpatialAnchor を作成できます。 デバイスはその時点でその座標系を特定できる必要があり、空間アンカーの限界に達していないことが必要です。

定義が完了すると、SpatialAnchor の座標系は、初期位置の正確な位置と向きを維持するために継続的に調整されます。 その後、この SpatialAnchor を使用して、ユーザーの環境で固定されている、その正確な場所で固定されているホログラムをレンダリングできます。

アンカーの位置を維持する調整の効果は、アンカーからの距離に合わせて拡大されます。 アンカーの原点から約3メートルを超えるアンカーに対しては、コンテンツを表示しないようにする必要があります。

[CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx)プロパティは、アンカーに相対的にコンテンツを配置できる座標系を取得します。これにより、デバイスがアンカーの正確な位置を調整するときにイージングが適用されます。

[RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx)プロパティとそれに対応する[RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx)イベントを使用して、これらの調整を自分で管理します。

### <a name="persist-and-share-spatial-anchors"></a>空間アンカーを保持および共有する

[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)クラスを使用してローカルで SpatialAnchor を永続化し、同じ HoloLens デバイスで今後のアプリセッションに戻すことができます。

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用すると、ローカル SpatialAnchor から持続性のあるクラウドアンカーを作成できます。これにより、アプリは複数の HoloLens、IOS、Android デバイスで検索できます。  複数のデバイスで共通の空間アンカーを共有することにより、各ユーザーは、そのアンカーに対して相対的にレンダリングされたコンテンツを、同じ物理的な場所にリアルタイムで表示できます。 

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、HoloLens、iOS、および Android デバイス間での非同期ホログラム永続化を行うこともできます。  持続性のあるクラウド空間アンカーを共有することにより、複数のデバイスが同時に存在しない場合でも、同じ永続化されたホログラムを時間の経過とともに観察できます。

HoloLens アプリでの共有エクスペリエンスの構築を開始するには、5分間の <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空間アンカー HoloLens クイックスタート</a>をお試しください。

Azure 空間アンカーを使用して実行すると、 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens でアンカーを作成して検索</a>できます。  チュートリアルは <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android と iOS</a> でも使用できます。これにより、すべてのデバイスで同じアンカーを共有できるようになります。

### <a name="create-spatialanchors-for-holographic-content"></a>Holographic コンテンツの SpatialAnchors を作成する

このコードサンプルでは、 **押さ** れたジェスチャが検出されたときにアンカーを作成するように Windows Holographic アプリテンプレートを変更しました。 次に、レンダーパス中にキューブがアンカーに配置されます。

ヘルパークラスでは複数のアンカーがサポートされているため、このコードサンプルを使用するのと同じ数のキューブを配置できます。

> [!NOTE]
> アンカーの Id は、アプリで制御するものです。 この例では、アプリのアンカーのコレクションに現在格納されているアンカーの数に基づいて、シーケンシャルな名前付けスキームを作成しました。

```
   // Check for new input state since the last frame.
   SpatialInteractionSourceState^ pointerState = m_spatialInputHandler->CheckForInput();
   if (pointerState != nullptr)
   {
       // Try to get the pointer pose relative to the SpatialStationaryReferenceFrame.
       SpatialPointerPose^ pointerPose = pointerState->TryGetPointerPose(currentCoordinateSystem);
       if (pointerPose != nullptr)
       {
           // When a Pressed gesture is detected, the anchor will be created two meters in front of the user.

           // Get the gaze direction relative to the given coordinate system.
           const float3 headPosition = pointerPose->Head->Position;
           const float3 headDirection = pointerPose->Head->ForwardDirection;

           // The anchor position in the StationaryReferenceFrame.
           static const float distanceFromUser = 2.0f; // meters
           const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

           // Create the anchor at position.
           SpatialAnchor^ anchor = SpatialAnchor::TryCreateRelativeTo(currentCoordinateSystem, gazeAtTwoMeters);

           if ((anchor != nullptr) && (m_spatialAnchorHelper != nullptr))
           {
               // In this example, we store the anchor in an IMap.
               auto anchorMap = m_spatialAnchorHelper->GetAnchorMap();

               // Create an identifier for the anchor.
               String^ id = ref new String(L"HolographicSpatialAnchorStoreSample_Anchor") + anchorMap->Size;

               anchorMap->Insert(id->ToString(), anchor);
           }
       }
   }
```

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a>SpatialAnchorStore を非同期に読み込み、キャッシュします。

次のような、この永続化の処理に役立つ SampleSpatialAnchorHelper クラスを記述する方法を見てみましょう。
* Platform:: String キーによってインデックス付けされたインメモリアンカーのコレクションを格納します。
* システムの SpatialAnchorStore からアンカーを読み込んでいます。これは、ローカルのメモリ内コレクションとは別に保持されます。
* アプリによって選択されたときに、アンカーのローカルメモリ内コレクションを SpatialAnchorStore に保存します。

[SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)オブジェクトを[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)に保存する方法を次に示します。

クラスが起動すると、SpatialAnchorStore が非同期に要求されます。 これには、API がアンカーストアを読み込むときのシステム i/o が含まれます。 i/o がブロックされないように、この API は非同期になります。

```
   // Request the spatial anchor store, which is the WinRT object that will accept the imported anchor data.
   return create_task(SpatialAnchorManager::RequestStoreAsync())
       .then([](task<SpatialAnchorStore^> previousTask)
   {
       std::shared_ptr<SampleSpatialAnchorHelper> newHelper = nullptr;

       try
       {
           SpatialAnchorStore^ anchorStore = previousTask.get();

           // Once the SpatialAnchorStore has been loaded by the system, we can create our helper class.

           // Using "new" to access private constructor
           newHelper = std::shared_ptr<SampleSpatialAnchorHelper>(new SampleSpatialAnchorHelper(anchorStore));

           // Now we can load anchors from the store.
           newHelper->LoadFromAnchorStore();
       }
       catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while loading the anchor store: ") +
               exception->Message->Data() +
               L"\n"
               );
       }

       // Return the initialized class instance.
       return newHelper;
   });
```

アンカーを保存するために使用できる SpatialAnchorStore が与えられます。 これは、文字列であるキー値と SpatialAnchors のデータ値を関連付ける IMapView です。 このサンプルコードでは、ヘルパークラスのパブリック関数を介してアクセスできるプライベートクラスメンバー変数にこれを格納します。

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
>忘れずに suspend/resume イベントをフックして、アンカーストアを保存して読み込みます。

```
   void HolographicSpatialAnchorStoreSampleMain::SaveAppState()
   {
       // For example, store information in the SpatialAnchorStore.
       if (m_spatialAnchorHelper != nullptr)
       {
           m_spatialAnchorHelper->TrySaveToAnchorStore();
       }
   }
```

```
   void HolographicSpatialAnchorStoreSampleMain::LoadAppState()
   {
       // For example, load information from the SpatialAnchorStore.
       LoadAnchorStore();
   }
```

### <a name="save-content-to-the-anchor-store"></a>コンテンツをアンカーストアに保存する

システムによってアプリが中断された場合は、空間アンカーをアンカーストアに保存する必要があります。 また、アプリの実装に必要であると考えられるように、アンカーストアにアンカーを他のタイミングで保存することもできます。

インメモリアンカーを SpatialAnchorStore に保存する準備ができたら、コレクションをループ処理して、各コレクションを保存してみてください。

```
   // TrySaveToAnchorStore: Stores all anchors from memory into the app's anchor store.
   //
   // For each anchor in memory, this function tries to store it in the app's AnchorStore. The operation will fail if
   // the anchor store already has an anchor by that name.
   //
   bool SampleSpatialAnchorHelper::TrySaveToAnchorStore()
   {
       // This function returns true if all the anchors in the in-memory collection are saved to the anchor
       // store. If zero anchors are in the in-memory collection, we will still return true because the
       // condition has been met.
       bool success = true;

       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           for each (auto& pair in m_anchorMap)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;

               // Try to save the anchors.
               if (!m_anchorStore->TrySave(id, anchor))
               {
                   // This may indicate the anchor ID is taken, or the anchor limit is reached for the app.
                   success=false;
               }
           }
       }

       return success;
   }
```

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a>アプリの再開時にアンカーストアからコンテンツを読み込む

保存されているアンカーを AnchorStore に復元するには、アプリケーションの再開時または任意の時点で、アンカーストアの IMapView から SpatialAnchors のメモリ内のデータベースに転送します。

SpatialAnchorStore からアンカーを復元するには、必要なものをそれぞれメモリ内コレクションに復元します。

作成した SpatialAnchors に文字列を関連付けるには、SpatialAnchors の独自のメモリ内データベースが必要です。 このサンプルコードでは、Windows:: Foundation:: Collections:: IMap を使用してアンカーを格納することを選択します。これにより、SpatialAnchorStore で同じキーとデータ値を簡単に使用できるようになります。

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
>復元されるアンカーは、すぐには見つからない場合があります。 たとえば、アンカーが別の部屋にある場合や、別の建物に配置される場合があります。 AnchorStore から取得したアンカーは、使用前に locatability をテストする必要があります。

<br>

>[!NOTE]
>このコード例では、AnchorStore からすべてのアンカーを取得します。 これは必須ではありません。アプリでは、実装にとって意味のある文字列キー値を使用して、アンカーの特定のサブセットを選択して選択することもできます。

```
   // LoadFromAnchorStore: Loads all anchors from the app's anchor store into memory.
   //
   // The anchors are stored in memory using an IMap, which stores anchors using a string identifier. Any string can be used as
   // the identifier; it can have meaning to the app, such as "Game_Leve1_CouchAnchor," or it can be a GUID that is generated
   // by the app.
   //
   void SampleSpatialAnchorHelper::LoadFromAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Get all saved anchors.
           auto anchorMapView = m_anchorStore->GetAllSavedAnchors();
           for each (auto const& pair in anchorMapView)
           {
               auto const& id = pair->Key;
               auto const& anchor = pair->Value;
               m_anchorMap->Insert(id, anchor);
           }
       }
   }
```

### <a name="clear-the-anchor-store-when-needed"></a>必要に応じてアンカーストアをクリアする

場合によっては、アプリの状態をクリアして新しいデータを書き込む必要があります。 [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)を使用してこれを行う方法を次に示します。

ヘルパークラスを使用すると、Clear 関数をラップする必要がほとんどありません。 このサンプル実装では、ヘルパークラスに SpatialAnchorStore インスタンスを所有する役割が与えられているため、このようにします。

```
   // ClearAnchorStore: Clears the AnchorStore for the app.
   //
   // This function clears the AnchorStore. It has no effect on the anchors stored in memory.
   //
   void SampleSpatialAnchorHelper::ClearAnchorStore()
   {
       // If access is denied, 'anchorStore' will not be obtained.
       if (m_anchorStore != nullptr)
       {
           // Clear all anchors from the store.
           m_anchorStore->Clear();
       }
   }
```

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a>例: アンカー座標系を静止参照フレーム座標系に関連付ける

アンカーがあるとします。アンカーの座標系にあるものを、他のコンテンツに対して既に使用している SpatialStationaryReferenceFrame に関連付ける必要があります。 [Trygettransformto を](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx)使用すると、アンカーの座標系から、固定の参照フレームの変換を取得できます。

```
   // In this code snippet, someAnchor is a SpatialAnchor^ that has been initialized and is valid in the current environment.
   float4x4 anchorSpaceToCurrentCoordinateSystem;
   SpatialCoordinateSystem^ anchorSpace = someAnchor->CoordinateSystem;
   const auto tryTransform = anchorSpace->TryGetTransformTo(currentCoordinateSystem);
   if (tryTransform != nullptr)
   {
       anchorSpaceToCurrentCoordinateSystem = tryTransform->Value;
   }
```

このプロセスは、次の2つの方法で役に立ちます。
1. 2つの参照フレームが互いに相対的に認識されるかどうかを示します。
2. 含まれている場合は、ある座標系から別の座標系に直接進む変換を提供します。

この情報を使用すると、2つの参照フレーム間のオブジェクト間の空間リレーションシップについて理解できます。

レンダリングのために、多くの場合、元の参照フレームまたはアンカーに従ってオブジェクトをグループ化することで、より良い結果を得ることができます。 グループごとに個別の描画パスを実行します。 ビュー行列は、同じ座標系を使用して最初に作成されたモデル変換を持つオブジェクトに対してより正確です。

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a>デバイスに接続された参照のフレームを使用してホログラムを作成する

デバイスの場所に [まだアタッチさ](../../design/coordinate-systems.md#attached-frame-of-reference) れているホログラムをレンダリングする必要がある場合があります。たとえば、デバッグ情報を含むパネルや、デバイスが領域内の位置ではなく向きだけを判断できる場合に、情報メッセージが表示されます。 これを実現するには、関連付けられている参照のフレームを使用します。

SpatialLocatorAttachedFrameOfReference クラスは、実際の環境ではなく、デバイスに対して相対的な座標系を定義します。 このフレームには、参照フレームの作成時にユーザーが直面していた方向を示す、ユーザーの周囲を基準とした固定の見出しがあります。 その後、ユーザーがデバイスを回転させる場合でも、この参照フレーム内のすべての向きは、その固定の見出しに対して相対的になります。

HoloLens の場合、このフレームの座標系の原点は、ユーザーの頭の回転の中心にあります。そのため、その位置はヘッドローテーションの影響を受けません。 アプリでは、この点を基準としたオフセットを指定して、ユーザーの前にホログラムを配置できます。

SpatialLocatorAttachedFrameOfReference を取得するには、SpatialLocator クラスを使用して CreateAttachedFrameOfReferenceAtCurrentHeading を呼び出します。

これは、Windows Mixed Reality デバイスの範囲全体に適用されます。

### <a name="use-a-reference-frame-attached-to-the-device"></a>デバイスにアタッチされている参照フレームを使用する

これらのセクションでは、この API を使用してデバイスに接続された参照のフレームを有効にするために、Windows Holographic アプリテンプレートで変更された内容について説明します。 この "接続済み" ホログラムは、固定されたホログラムと共に動作します。また、デバイスが世界での位置を一時的に見つけることができない場合にも使用できます。

まず、SpatialStationaryFrameOfReference の代わりに SpatialLocatorAttachedFrameOfReference を格納するようにテンプレートを変更しました。

**HolographicTagAlongSampleMain** から:

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

**HolographicTagAlongSampleMain** から:

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

更新中に、フレーム予測を使用してから取得したタイムスタンプで座標系を取得できるようになりました。

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a>空間ポインターのポーズを取得し、ユーザーの宝石に従います。

この例では、holographic シェルがユーザーの見つめに従う方法と同様に、ユーザーの [宝石](../../design/gaze-and-commit.md)に従うように、ホログラムの例を使用します。 そのためには、同じタイムスタンプから SpatialPointerPose を取得する必要があります。

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

この SpatialPointerPose には、 [ユーザーの現在の見出し](gaze-in-directx.md)に従ってホログラムを配置するために必要な情報が含まれています。

ユーザーに快適に使用するために、線形補間 ("lerp") を使用して、一定期間内の変化を滑らかにします。 これは、ホログラムを見つめにロックするよりも、ユーザーにとってより使いやすくなります。 タグに沿ったホログラムの位置を Lerping することで、動きをダンパーすることによって、ホログラムを安定させることもできます。 このダンパーを実行しなかった場合、通常はユーザーの頭のなるべくな動きと見なされるため、ユーザーにはホログラムのジッターが表示されます。

From **StationaryQuadRenderer::P ositionhologram**:

```
   const float& dtime = static_cast<float>(timer.GetElapsedSeconds());

   if (pointerPose != nullptr)
   {
       // Get the gaze direction relative to the given coordinate system.
       const float3 headPosition  = pointerPose->Head->Position;
       const float3 headDirection = pointerPose->Head->ForwardDirection;

       // The tag-along hologram follows a point 2.0m in front of the user's gaze direction.
       static const float distanceFromUser = 2.0f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * headDirection);

       // Lerp the position, to keep the hologram comfortably stable.
       auto lerpedPosition = lerp(m_position, gazeAtTwoMeters, dtime * c_lerpRate);

       // This will be used as the translation component of the hologram's
       // model transform.
       SetPosition(lerpedPosition);
   }
```

>[!NOTE]
>デバッグパネルの場合は、表示が妨げされないように、ホログラムを少し左に移動することを選択できます。 その方法の例を次に示します。

StationaryQuadRenderer の場合 **::P ositionhologram**:

```
       // If you're making a debug view, you might not want the tag-along to be directly in the
       // center of your field of view. Use this code to position the hologram to the right of
       // the user's gaze direction.
       /*
       const float3 offset = float3(0.13f, 0.0f, 0.f);
       static const float distanceFromUser = 2.2f; // meters
       const float3 gazeAtTwoMeters = headPosition + (distanceFromUser * (headDirection + offset));
       */
```

### <a name="rotate-the-hologram-to-face-the-camera"></a>ホログラムを回転してカメラに面します

ホログラムを配置するだけでは十分ではありません。この場合は、クワッドです。また、ユーザーに対してオブジェクトを回転させる必要があります。 この種類の billboarding では、ホログラムがユーザーの環境の一部として保持されるため、このローテーションはワールド空間で行われます。 ホログラムが画面の向きにロックされるため、ビュースペースの billboarding は快適ではありません。その場合、ステレオレンダリングを中断しないビュー領域のビルボード変換を取得するために、左右のビュー行列を補間する必要もあります。 ここでは、X 軸と Z 軸を回転させてユーザーを中心にしています。

**StationaryQuadRenderer:: Update** から:

```
   // Seconds elapsed since previous frame.
   const float& dTime = static_cast<float>(timer.GetElapsedSeconds());

   // Create a direction normal from the hologram's position to the origin of person space.
   // This is the z-axis rotation.
   XMVECTOR facingNormal = XMVector3Normalize(-XMLoadFloat3(&m_position));

   // Rotate the x-axis around the y-axis.
   // This is a 90-degree angle from the normal, in the xz-plane.
   // This is the x-axis rotation.
   XMVECTOR xAxisRotation = XMVector3Normalize(XMVectorSet(XMVectorGetZ(facingNormal), 0.f, -XMVectorGetX(facingNormal), 0.f));

   // Create a third normal to satisfy the conditions of a rotation matrix.
   // The cross product  of the other two normals is at a 90-degree angle to
   // both normals. (Normalize the cross product to avoid floating-point math
   // errors.)
   // Note how the cross product will never be a zero-matrix because the two normals
   // are always at a 90-degree angle from one another.
   XMVECTOR yAxisRotation = XMVector3Normalize(XMVector3Cross(facingNormal, xAxisRotation));

   // Construct the 4x4 rotation matrix.

   // Rotate the quad to face the user.
   XMMATRIX rotationMatrix = XMMATRIX(
       xAxisRotation,
       yAxisRotation,
       facingNormal,
       XMVectorSet(0.f, 0.f, 0.f, 1.f)
       );

   // Position the quad.
   const XMMATRIX modelTranslation = XMMatrixTranslationFromVector(XMLoadFloat3(&m_position));

   // The view and projection matrices are provided by the system; they are associated
   // with holographic cameras, and updated on a per-camera basis.
   // Here, we provide the model transform for the sample hologram. The model transform
   // matrix is transposed to prepare it for the shader.
   XMStoreFloat4x4(&m_modelConstantBufferData.model, XMMatrixTranspose(rotationMatrix * modelTranslation));
```

### <a name="render-the-attached-hologram"></a>添付されたホログラムをレンダリングします

この例では、ホログラムを SpatialLocatorAttachedReferenceFrame の座標系でレンダリングすることも選択しています。これは、ホログラムを配置した場所です。 (別の座標系を使用してレンダリングすることにした場合は、デバイスに接続されている参照フレームの座標系から、その座標系に変換を取得する必要があります)。

**HolographicTagAlongSampleMain:: Render** から:

```
   // The view and projection matrices for each holographic camera will change
   // every frame. This function refreshes the data in the constant buffer for
   // the holographic camera indicated by cameraPose.
   pCameraResources->UpdateViewProjectionBuffer(
       m_deviceResources,
       cameraPose,
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp)
       );
```

以上で作業は終了です。 ホログラムは、ユーザーの見つめ方向の前に2メートルの位置を "追跡" するようになります。

>[!NOTE]
>この例では、追加のコンテンツも読み込まれます。 StationaryQuadRenderer を参照してください。

## <a name="handling-tracking-loss"></a>追跡損失の処理

デバイスが世界中で見つからない場合、アプリでは "損失の追跡" が発生します。 Windows Mixed Reality アプリは、位置指定追跡システムの中断を処理できる必要があります。 既定の SpatialLocator で Locatの変更イベントを使用することにより、これらの中断を監視し、応答を作成できます。

**Appmain:: SetHolographicSpace から:**

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

アプリが Locat信頼性変更イベントを受け取ると、必要に応じて動作を変更できます。 たとえば、PositionalTrackingInhibited 状態では、アプリは通常の操作を一時停止し、警告メッセージを表示する [タグに沿ったホログラム](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) をレンダリングすることができます。

Windows Holographic アプリケーションテンプレートには、既に作成されている Locat信頼性変更ハンドラーが付属しています。 既定では、位置追跡が使用できない場合、デバッグコンソールに警告が表示されます。 このハンドラーにコードを追加して、アプリから必要な応答を提供できます。

**Appmain .cpp から:**

```
   void HolographicApp1Main::OnLocatabilityChanged(SpatialLocator^ sender, Object^ args)
   {
       switch (sender->Locatability)
       {
       case SpatialLocatability::Unavailable:
           // Holograms cannot be rendered.
           {
               String^ message = L"Warning! Positional tracking is " +
                                           sender->Locatability.ToString() + L".\n";
               OutputDebugStringW(message->Data());
           }
           break;

       // In the following three cases, it is still possible to place holograms using a
       // SpatialLocatorAttachedFrameOfReference.
       case SpatialLocatability::PositionalTrackingActivating:
           // The system is preparing to use positional tracking.

       case SpatialLocatability::OrientationOnly:
           // Positional tracking has not been activated.

       case SpatialLocatability::PositionalTrackingInhibited:
           // Positional tracking is temporarily inhibited. User action may be required
           // in order to restore positional tracking.
           break;

       case SpatialLocatability::PositionalTrackingActive:
           // Positional tracking is active. World-locked content can be rendered.
           break;
       }
   }
```

## <a name="spatial-mapping"></a>空間マッピング

[空間マッピング](spatial-mapping-in-directx.md)api は、座標系を使用して、サーフェスメッシュのモデル変換を取得します。

## <a name="see-also"></a>関連項目
* [座標系](../../design/coordinate-systems.md)
* [空間アンカー](../../design/spatial-anchors.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* [DirectX でのヘッド視線入力とアイ視線入力](gaze-in-directx.md)
* [DirectX での手とモーション コントローラー](hands-and-motion-controllers-in-directx.md)
* [DirectX の空間マッピング](spatial-mapping-in-directx.md)
