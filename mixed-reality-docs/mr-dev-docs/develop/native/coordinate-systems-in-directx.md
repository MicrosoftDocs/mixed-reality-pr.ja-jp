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
# <a name="coordinate-systems-in-directx"></a><span data-ttu-id="4c16f-105">DirectX の座標系</span><span class="sxs-lookup"><span data-stu-id="4c16f-105">Coordinate systems in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="4c16f-106">この記事は、従来の WinRT ネイティブ Api に関連しています。</span><span class="sxs-lookup"><span data-stu-id="4c16f-106">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="4c16f-107">新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](openxr-getting-started.md)** を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4c16f-107">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="4c16f-108">[座標系](../../design/coordinate-systems.md) は、Windows Mixed Reality api によって提供される空間を理解するための基礎となります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-108">[Coordinate systems](../../design/coordinate-systems.md) form the basis for spatial understanding offered by Windows Mixed Reality APIs.</span></span>

<span data-ttu-id="4c16f-109">現在の接続されている VR または単一の部屋の VR デバイスは、追跡領域に1つの主要な座標系を確立します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-109">Today's seated VR or single-room VR devices establish one primary coordinate system for their tracked space.</span></span> <span data-ttu-id="4c16f-110">HoloLens のような Mixed Reality デバイスは、大規模な未定義の環境向けに設計されています。デバイスを検出し、ユーザーが説明するように、その環境について学習します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-110">Mixed Reality devices like HoloLens are designed for large undefined environments, with the device discovering and learning about its surroundings as the user walks around.</span></span> <span data-ttu-id="4c16f-111">デバイスは、ユーザーの部屋に関する知識を継続的に向上させるように調整されますが、アプリケーションの有効期間中に相互に関係が変化する座標系が得られます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-111">The device adapts to continually improving knowledge about the user's rooms, but results in coordinate systems that change their relationship to one another over the apps lifetime.</span></span> <span data-ttu-id="4c16f-112">Windows Mixed Reality では、世界中に接続されている参照フレームによって組み込まれたイマーシブヘッドセットから、さまざまなデバイスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4c16f-112">Windows Mixed Reality supports a wide spectrum of devices, ranging from seated immersive headsets through world-attached reference frames.</span></span>

>[!NOTE]
><span data-ttu-id="4c16f-113">この記事のコードスニペットでは、 [C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)で使用される c + c++ 17 準拠の c++/WinRT ではなく、c++/cx の使用方法を現在説明しています。</span><span class="sxs-lookup"><span data-stu-id="4c16f-113">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="4c16f-114">概念は C++/WinRT プロジェクトに相当しますが、コードを変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-114">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="spatial-coordinate-systems-in-windows"></a><span data-ttu-id="4c16f-115">Windows の空間座標系</span><span class="sxs-lookup"><span data-stu-id="4c16f-115">Spatial coordinate systems in Windows</span></span>

<span data-ttu-id="4c16f-116">Windows での実際の座標系の理由として使用されるコア型は <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>です。</span><span class="sxs-lookup"><span data-stu-id="4c16f-116">The core type used to reason about real-world coordinate systems in Windows is the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialcoordinatesystem" target="_blank">SpatialCoordinateSystem</a>.</span></span> <span data-ttu-id="4c16f-117">この型のインスタンスは任意の座標系を表します。変換行列データを取得するためのメソッドを提供します。このデータを使用して、それぞれの詳細を理解することなく、2つの座標系の間で変換を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-117">An instance of this type represents an arbitrary coordinate system, providing a method for getting transformation matrix data that you can use to transform between two coordinate systems without understanding the details of each.</span></span>

<span data-ttu-id="4c16f-118">空間情報を返すメソッドは、SpatialCoordinateSystem パラメーターを使用して、返される座標に最も適した座標系を決定できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-118">Methods that return spatial information will accept a SpatialCoordinateSystem parameter to let you decide the coordinate system in which it's most useful for those coordinates to be returned.</span></span> <span data-ttu-id="4c16f-119">空間情報は、ユーザーの周囲のポイント、線、またはボリュームとして表され、これらの座標の単位は常にメートル単位になります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-119">Spatial information is represented as points, rays, or volumes in the user's surroundings, and the units for these coordinates will always be in meters.</span></span>

<span data-ttu-id="4c16f-120">SpatialCoordinateSystem には、デバイスの位置を表すものを含む、他の座標系との動的な関係があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-120">A SpatialCoordinateSystem has a dynamic relationship with other coordinate systems, including those that represent the device's position.</span></span> <span data-ttu-id="4c16f-121">どの時点でも、デバイスは他の座標系を検出できません。</span><span class="sxs-lookup"><span data-stu-id="4c16f-121">At any point, the device can locate some coordinate systems and not others.</span></span> <span data-ttu-id="4c16f-122">ほとんどの座標系では、アプリは特定の期間内に配置できない期間を処理する準備ができている必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-122">For most coordinate systems, your app must be ready to handle periods of time during which they cannot be located.</span></span>

<span data-ttu-id="4c16f-123">アプリケーションで直接 SpatialCoordinateSystems を作成するのではなく、認識 Api を介して使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-123">Your application shouldn't create SpatialCoordinateSystems directly - rather they should be consumed via the Perception APIs.</span></span> <span data-ttu-id="4c16f-124">認識 Api には3つの主要なソースがあり、それぞれが [ [座標系](../../design/coordinate-systems.md) ] ページで説明されている概念に対応しています。</span><span class="sxs-lookup"><span data-stu-id="4c16f-124">There are three primary sources of coordinate systems in the Perception APIs, each of which map to a concept described on the [Coordinate systems](../../design/coordinate-systems.md) page:</span></span>
* <span data-ttu-id="4c16f-125">参照の静止フレームを取得するには、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> を作成するか、現在の <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>から取得します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-125">To get a stationary frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstationaryframeofreference" target="_blank">SpatialStationaryFrameOfReference</a> or obtain one from the current <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference" target="_blank">SpatialStageFrameOfReference</a>.</span></span>
* <span data-ttu-id="4c16f-126">空間アンカーを取得するには、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>を作成します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-126">To get a spatial anchor, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor" target="_blank">SpatialAnchor</a>.</span></span>
* <span data-ttu-id="4c16f-127">アタッチされた参照のフレームを取得するには、 <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>を作成します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-127">To get an attached frame of reference, create a <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocatorattachedframeofreference" target="_blank">SpatialLocatorAttachedFrameOfReference</a>.</span></span>

<span data-ttu-id="4c16f-128">これらのオブジェクトによって返されるすべての座標系は、右ききで、+ y が上、+ x が右、+ z の後方になります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-128">All of the coordinate systems returned by these objects are right-handed, with +y up, +x to the right and +z backwards.</span></span> <span data-ttu-id="4c16f-129">正の x 方向の左側または右側の指をポイントし、正の y 方向に curling することによって、正の z 軸の方向を思い出すことができます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-129">You can remember which direction the positive z-axis points by pointing the fingers of either your left or right hand in the positive x direction and curling them into the positive y direction.</span></span> <span data-ttu-id="4c16f-130">親指が指している方向は、自身に向かうかまたは離れる方向のいずれかとなり、その座標系の z 軸の正の向きが指す方向となります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-130">The direction your thumb points, either toward or away from you, is the direction that the positive z-axis points for that coordinate system.</span></span> <span data-ttu-id="4c16f-131">次の図は、これらの 2 つの座標系を示しています。</span><span class="sxs-lookup"><span data-stu-id="4c16f-131">The following illustration shows these two coordinate systems.</span></span>

<span data-ttu-id="4c16f-132">![左側および右側の座標系](images/left-hand-right-hand.gif)</span><span class="sxs-lookup"><span data-stu-id="4c16f-132">![Left-hand and right-hand coordinate systems](images/left-hand-right-hand.gif)</span></span><br>
<span data-ttu-id="4c16f-133">*左側および右側の座標系*</span><span class="sxs-lookup"><span data-stu-id="4c16f-133">*Left-hand and right-hand coordinate systems*</span></span>

<span data-ttu-id="4c16f-134"><a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a>クラスを使用して、HoloLens への接続されたフレームまたは静止したフレーム参照を、HoloLens の位置に基づいて SpatialCoordinateSystem に作成します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-134">Use the <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocator" target="_blank">SpatialLocator</a> class to create either an attached or stationary frame of reference to bootstrap into a SpatialCoordinateSystem based on the HoloLens position.</span></span> <span data-ttu-id="4c16f-135">このプロセスの詳細については、次のセクションに進んでください。</span><span class="sxs-lookup"><span data-stu-id="4c16f-135">Continue to the next section to learn more about this process.</span></span>

## <a name="place-holograms-in-the-world-using-a-spatial-stage"></a><span data-ttu-id="4c16f-136">空間ステージを使用して、世界中にホログラムを配置する</span><span class="sxs-lookup"><span data-stu-id="4c16f-136">Place holograms in the world using a spatial stage</span></span>

<span data-ttu-id="4c16f-137">不透明な Windows Mixed Reality イマーシブヘッドセットの座標系には、static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference:: Current</a> プロパティを使用してアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4c16f-137">The coordinate system for opaque Windows Mixed Reality immersive headsets is accessed using the static <a href="https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current" target="_blank">SpatialStageFrameOfReference::Current</a> property.</span></span> <span data-ttu-id="4c16f-138">この API は次のものを提供します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-138">This API provides:</span></span>

* <span data-ttu-id="4c16f-139">座標系</span><span class="sxs-lookup"><span data-stu-id="4c16f-139">A coordinate system</span></span>
* <span data-ttu-id="4c16f-140">Windows media player が装着されているか、モバイルデバイスであるかに関する情報</span><span class="sxs-lookup"><span data-stu-id="4c16f-140">Information about whether the player is seated or mobile</span></span>
* <span data-ttu-id="4c16f-141">プレーヤーがモバイルであるかどうかを調べるための安全な領域の境界</span><span class="sxs-lookup"><span data-stu-id="4c16f-141">The boundary of a safe area for walking around if the player is mobile</span></span>
* <span data-ttu-id="4c16f-142">ヘッドセットが指向性であるかどうかを示す値。</span><span class="sxs-lookup"><span data-stu-id="4c16f-142">An indication of whether the headset is directional.</span></span> 
* <span data-ttu-id="4c16f-143">空間ステージを更新するためのイベントハンドラー。</span><span class="sxs-lookup"><span data-stu-id="4c16f-143">An event handler for updates to the spatial stage.</span></span>

<span data-ttu-id="4c16f-144">まず、空間ステージを取得し、それに対する更新をサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="4c16f-144">First, we get the spatial stage and subscribe for updates to it:</span></span> 

<span data-ttu-id="4c16f-145">**空間ステージの初期化** のコード</span><span class="sxs-lookup"><span data-stu-id="4c16f-145">Code for **Spatial stage initialization**</span></span>

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

<span data-ttu-id="4c16f-146">OnCurrentChanged メソッドでは、アプリは空間ステージを調べて、プレーヤーエクスペリエンスを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-146">In the OnCurrentChanged method, your app should inspect the spatial stage and update the player experience.</span></span> <span data-ttu-id="4c16f-147">この例では、ステージの境界と、ユーザーによって指定された開始位置、およびステージのビューの範囲および移動プロパティの範囲の視覚エフェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-147">In this example, we provide a visualization of the stage boundary and the start position specified by the user and the stage's range of view and range of movement properties.</span></span> <span data-ttu-id="4c16f-148">また、ステージを提供できない場合は、独自の静止座標系にフォールバックします。</span><span class="sxs-lookup"><span data-stu-id="4c16f-148">We also fall back to our own stationary coordinate system, when a stage cannot be provided.</span></span>


<span data-ttu-id="4c16f-149">**空間ステージの更新** のコード</span><span class="sxs-lookup"><span data-stu-id="4c16f-149">Code for **Spatial stage update**</span></span>

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

<span data-ttu-id="4c16f-150">ステージの境界を定義する頂点のセットは、時計回りの順序で提供されます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-150">The set of vertices that define the stage boundary are provided in clockwise order.</span></span> <span data-ttu-id="4c16f-151">Windows Mixed Reality シェルでは、ユーザーがアプローチするときに境界にフェンスが描画されますが、自分の目的に合わせて triangularize 領域を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-151">The Windows Mixed Reality shell draws a fence at the boundary when the user approaches it, but you may want to triangularize the walkable area for your own purposes.</span></span> <span data-ttu-id="4c16f-152">次のアルゴリズムを使用して、ステージを triangularize できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-152">The following algorithm can be used to triangularize the stage.</span></span>


<span data-ttu-id="4c16f-153">**空間ステージ triangularization** のコード</span><span class="sxs-lookup"><span data-stu-id="4c16f-153">Code for **Spatial stage triangularization**</span></span>

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

## <a name="place-holograms-in-the-world-using-a-stationary-frame-of-reference"></a><span data-ttu-id="4c16f-154">静止した参照フレームを使用して、世界中にホログラムを配置する</span><span class="sxs-lookup"><span data-stu-id="4c16f-154">Place holograms in the world using a stationary frame of reference</span></span>

<span data-ttu-id="4c16f-155">[SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx)クラスは、ユーザーが移動するときに、ユーザーの周囲を基準にして静止した[まま](../../design/coordinate-systems.md#stationary-frame-of-reference)になる参照のフレームを表します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-155">The [SpatialStationaryFrameOfReference](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialstationaryframeofreference.aspx) class represents a frame of reference that [remains stationary](../../design/coordinate-systems.md#stationary-frame-of-reference) relative to the user's surroundings as the user moves around.</span></span> <span data-ttu-id="4c16f-156">この参照フレームでは、デバイスの近くで座標が安定していることが優先されます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-156">This frame of reference prioritizes keeping coordinates stable near the device.</span></span> <span data-ttu-id="4c16f-157">SpatialStationaryFrameOfReference の主な用途は、ホログラムをレンダリングするときに、レンダリングエンジン内で基になるワールド座標系として機能することです。</span><span class="sxs-lookup"><span data-stu-id="4c16f-157">One key use of a SpatialStationaryFrameOfReference is to act as the underlying world coordinate system within a rendering engine when rendering holograms.</span></span>

<span data-ttu-id="4c16f-158">SpatialStationaryFrameOfReference を取得するには、 [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) クラスを使用して、 [createokary](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-158">To get a SpatialStationaryFrameOfReference, use the [SpatialLocator](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.aspx) class and call [CreateStationaryFrameOfReferenceAtCurrentLocation](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatiallocator.createstationaryframeofreferenceatcurrentlocation.aspx).</span></span>

<span data-ttu-id="4c16f-159">Windows Holographic アプリテンプレートのコードから:</span><span class="sxs-lookup"><span data-stu-id="4c16f-159">From the Windows Holographic app template code:</span></span>

```
           // The simplest way to render world-locked holograms is to create a stationary reference frame
           // when the app is launched. This is roughly analogous to creating a "world" coordinate system
           // with the origin placed at the device's position as the app is launched.
           referenceFrame = locator.CreateStationaryFrameOfReferenceAtCurrentLocation();
```
* <span data-ttu-id="4c16f-160">静止参照フレームは、全体の領域を基準とした最適な位置を提供するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="4c16f-160">Stationary reference frames are designed to provide a best-fit position relative to the overall space.</span></span> <span data-ttu-id="4c16f-161">その参照フレーム内の個々の位置は、少しずつ移動できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-161">Individual positions within that reference frame are allowed to drift slightly.</span></span> <span data-ttu-id="4c16f-162">これは、デバイスが環境に関する詳細を学習するため、正常です。</span><span class="sxs-lookup"><span data-stu-id="4c16f-162">This is normal as the device learns more about the environment.</span></span>
* <span data-ttu-id="4c16f-163">個々のホログラムが正確に配置されている必要がある場合は、SpatialAnchor を使用して、個々のホログラムを実際の世界の位置に固定する必要があります。たとえば、ユーザーが特別な関心を持っていることを示すポイントなどです。</span><span class="sxs-lookup"><span data-stu-id="4c16f-163">When precise placement of individual holograms is required, a SpatialAnchor should be used to anchor the individual hologram to a position in the real world - for example, a point the user indicates to be of special interest.</span></span> <span data-ttu-id="4c16f-164">アンカーの位置はずれませんが、修正することができます。アンカーは、修正が発生した後、次のフレームから始まる修正された位置を使用します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-164">Anchor positions don't drift, but can be corrected; the anchor will use the corrected position starting in the next frame after the correction has occurred.</span></span>

## <a name="place-holograms-in-the-world-using-spatial-anchors"></a><span data-ttu-id="4c16f-165">空間アンカーを使用して、世界中にホログラムを配置する</span><span class="sxs-lookup"><span data-stu-id="4c16f-165">Place holograms in the world using spatial anchors</span></span>

<span data-ttu-id="4c16f-166">[空間アンカー](../../design/coordinate-systems.md#spatial-anchors) は、実際の世界の特定の場所にホログラムを配置するための優れた方法であり、システムによって、アンカーが時間の経過と共に維持されるようにします。</span><span class="sxs-lookup"><span data-stu-id="4c16f-166">[Spatial anchors](../../design/coordinate-systems.md#spatial-anchors) are a great way to place holograms at a specific place in the real world, with the system ensuring the anchor stays in place over time.</span></span> <span data-ttu-id="4c16f-167">このトピックでは、アンカーを作成して使用する方法と、アンカーデータを操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-167">This topic explains how to create and use an anchor, and how to work with anchor data.</span></span>

<span data-ttu-id="4c16f-168">選択した SpatialCoordinateSystem 内の任意の位置と向きで、SpatialAnchor を作成できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-168">You can create a SpatialAnchor at any position and orientation within the SpatialCoordinateSystem of your choosing.</span></span> <span data-ttu-id="4c16f-169">デバイスはその時点でその座標系を特定できる必要があり、空間アンカーの限界に達していないことが必要です。</span><span class="sxs-lookup"><span data-stu-id="4c16f-169">The device must be able to locate that coordinate system at the moment, and the system must not have reached its limit of spatial anchors.</span></span>

<span data-ttu-id="4c16f-170">定義が完了すると、SpatialAnchor の座標系は、初期位置の正確な位置と向きを維持するために継続的に調整されます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-170">Once defined, the coordinate system of a SpatialAnchor adjusts continually to keep the precise position and orientation of its initial location.</span></span> <span data-ttu-id="4c16f-171">その後、この SpatialAnchor を使用して、ユーザーの環境で固定されている、その正確な場所で固定されているホログラムをレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-171">You can then use this SpatialAnchor to render holograms that will appear fixed in the user's surroundings at that exact location.</span></span>

<span data-ttu-id="4c16f-172">アンカーの位置を維持する調整の効果は、アンカーからの距離に合わせて拡大されます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-172">The effects of the adjustments that keep the anchor in place are magnified as distance from the anchor increases.</span></span> <span data-ttu-id="4c16f-173">アンカーの原点から約3メートルを超えるアンカーに対しては、コンテンツを表示しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-173">You should avoid rendering content relative to an anchor that is more than about 3 meters from that anchor's origin.</span></span>

<span data-ttu-id="4c16f-174">[CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx)プロパティは、アンカーに相対的にコンテンツを配置できる座標系を取得します。これにより、デバイスがアンカーの正確な位置を調整するときにイージングが適用されます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-174">The [CoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.coordinatesystem.aspx) property gets a coordinate system that lets you place content relative to the anchor, with easing applied when the device adjusts the anchor's precise location.</span></span>

<span data-ttu-id="4c16f-175">[RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx)プロパティとそれに対応する[RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx)イベントを使用して、これらの調整を自分で管理します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-175">Use the [RawCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystem.aspx) property and the corresponding [RawCoordinateSystemAdjusted](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.rawcoordinatesystemadjusted.aspx) event to manage these adjustments yourself.</span></span>

### <a name="persist-and-share-spatial-anchors"></a><span data-ttu-id="4c16f-176">空間アンカーを保持および共有する</span><span class="sxs-lookup"><span data-stu-id="4c16f-176">Persist and share spatial anchors</span></span>

<span data-ttu-id="4c16f-177">[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)クラスを使用してローカルで SpatialAnchor を永続化し、同じ HoloLens デバイスで今後のアプリセッションに戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-177">You can persist a SpatialAnchor locally using the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx) class and then get it back in a future app session on the same HoloLens device.</span></span>

<span data-ttu-id="4c16f-178"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用すると、ローカル SpatialAnchor から持続性のあるクラウドアンカーを作成できます。これにより、アプリは複数の HoloLens、IOS、Android デバイスで検索できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-178">By using <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a>, you can create a durable cloud anchor from a local SpatialAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="4c16f-179">複数のデバイスで共通の空間アンカーを共有することにより、各ユーザーは、そのアンカーに対して相対的にレンダリングされたコンテンツを、同じ物理的な場所にリアルタイムで表示できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-179">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location in real time.</span></span> 

<span data-ttu-id="4c16f-180"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、HoloLens、iOS、および Android デバイス間での非同期ホログラム永続化を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-180">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="4c16f-181">持続性のあるクラウド空間アンカーを共有することにより、複数のデバイスが同時に存在しない場合でも、同じ永続化されたホログラムを時間の経過とともに観察できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-181">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="4c16f-182">HoloLens アプリでの共有エクスペリエンスの構築を開始するには、5分間の <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空間アンカー HoloLens クイックスタート</a>をお試しください。</span><span class="sxs-lookup"><span data-stu-id="4c16f-182">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="4c16f-183">Azure 空間アンカーを使用して実行すると、 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens でアンカーを作成して検索</a>できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-183">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="4c16f-184">チュートリアルは <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android と iOS</a> でも使用できます。これにより、すべてのデバイスで同じアンカーを共有できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-184">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

### <a name="create-spatialanchors-for-holographic-content"></a><span data-ttu-id="4c16f-185">Holographic コンテンツの SpatialAnchors を作成する</span><span class="sxs-lookup"><span data-stu-id="4c16f-185">Create SpatialAnchors for holographic content</span></span>

<span data-ttu-id="4c16f-186">このコードサンプルでは、 **押さ** れたジェスチャが検出されたときにアンカーを作成するように Windows Holographic アプリテンプレートを変更しました。</span><span class="sxs-lookup"><span data-stu-id="4c16f-186">For this code sample, we modified the Windows Holographic app template to create anchors when the **Pressed** gesture is detected.</span></span> <span data-ttu-id="4c16f-187">次に、レンダーパス中にキューブがアンカーに配置されます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-187">The cube is then placed at the anchor during the render pass.</span></span>

<span data-ttu-id="4c16f-188">ヘルパークラスでは複数のアンカーがサポートされているため、このコードサンプルを使用するのと同じ数のキューブを配置できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-188">Since multiple anchors are supported by the helper class, we can place as many cubes as we want to use this code sample!</span></span>

> [!NOTE]
> <span data-ttu-id="4c16f-189">アンカーの Id は、アプリで制御するものです。</span><span class="sxs-lookup"><span data-stu-id="4c16f-189">The IDs for anchors are something you control in your app.</span></span> <span data-ttu-id="4c16f-190">この例では、アプリのアンカーのコレクションに現在格納されているアンカーの数に基づいて、シーケンシャルな名前付けスキームを作成しました。</span><span class="sxs-lookup"><span data-stu-id="4c16f-190">In this example, we have created a naming scheme that is sequential based on the number of anchors currently stored in the app's collection of anchors.</span></span>

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

### <a name="asynchronously-load-and-cache-the-spatialanchorstore"></a><span data-ttu-id="4c16f-191">SpatialAnchorStore を非同期に読み込み、キャッシュします。</span><span class="sxs-lookup"><span data-stu-id="4c16f-191">Asynchronously load, and cache, the SpatialAnchorStore</span></span>

<span data-ttu-id="4c16f-192">次のような、この永続化の処理に役立つ SampleSpatialAnchorHelper クラスを記述する方法を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="4c16f-192">Let's see how to write a SampleSpatialAnchorHelper class that helps handle this persistence, including:</span></span>
* <span data-ttu-id="4c16f-193">Platform:: String キーによってインデックス付けされたインメモリアンカーのコレクションを格納します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-193">Storing a collection of in-memory anchors, indexed by a Platform::String key.</span></span>
* <span data-ttu-id="4c16f-194">システムの SpatialAnchorStore からアンカーを読み込んでいます。これは、ローカルのメモリ内コレクションとは別に保持されます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-194">Loading anchors from the system's SpatialAnchorStore, which is kept separate from the local in-memory collection.</span></span>
* <span data-ttu-id="4c16f-195">アプリによって選択されたときに、アンカーのローカルメモリ内コレクションを SpatialAnchorStore に保存します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-195">Saving the local in-memory collection of anchors to the SpatialAnchorStore when the app chooses to do so.</span></span>

<span data-ttu-id="4c16f-196">[SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)オブジェクトを[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)に保存する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-196">Here's how to save [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) objects in the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="4c16f-197">クラスが起動すると、SpatialAnchorStore が非同期に要求されます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-197">When the class starts up, we request the SpatialAnchorStore asynchronously.</span></span> <span data-ttu-id="4c16f-198">これには、API がアンカーストアを読み込むときのシステム i/o が含まれます。 i/o がブロックされないように、この API は非同期になります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-198">This involves system I/O as the API loads the anchor store, and this API is made asynchronous so that the I/O is non-blocking.</span></span>

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

<span data-ttu-id="4c16f-199">アンカーを保存するために使用できる SpatialAnchorStore が与えられます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-199">You'll be given a SpatialAnchorStore that you can use to save the anchors.</span></span> <span data-ttu-id="4c16f-200">これは、文字列であるキー値と SpatialAnchors のデータ値を関連付ける IMapView です。</span><span class="sxs-lookup"><span data-stu-id="4c16f-200">This is an IMapView that associates key values that are Strings, with data values that are SpatialAnchors.</span></span> <span data-ttu-id="4c16f-201">このサンプルコードでは、ヘルパークラスのパブリック関数を介してアクセスできるプライベートクラスメンバー変数にこれを格納します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-201">In our sample code, we store this in a private class member variable that is accessible through a public function of our helper class.</span></span>

```
   SampleSpatialAnchorHelper::SampleSpatialAnchorHelper(SpatialAnchorStore^ anchorStore)
   {
       m_anchorStore = anchorStore;
       m_anchorMap = ref new Platform::Collections::Map<String^, SpatialAnchor^>();
   }
```

>[!NOTE]
><span data-ttu-id="4c16f-202">忘れずに suspend/resume イベントをフックして、アンカーストアを保存して読み込みます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-202">Don't forget to hook up the suspend/resume events to save and load the anchor store.</span></span>

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

### <a name="save-content-to-the-anchor-store"></a><span data-ttu-id="4c16f-203">コンテンツをアンカーストアに保存する</span><span class="sxs-lookup"><span data-stu-id="4c16f-203">Save content to the anchor store</span></span>

<span data-ttu-id="4c16f-204">システムによってアプリが中断された場合は、空間アンカーをアンカーストアに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-204">When the system suspends your app, you need to save your spatial anchors to the anchor store.</span></span> <span data-ttu-id="4c16f-205">また、アプリの実装に必要であると考えられるように、アンカーストアにアンカーを他のタイミングで保存することもできます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-205">You may also choose to save anchors to the anchor store at other times, as you find to be necessary for your app's implementation.</span></span>

<span data-ttu-id="4c16f-206">インメモリアンカーを SpatialAnchorStore に保存する準備ができたら、コレクションをループ処理して、各コレクションを保存してみてください。</span><span class="sxs-lookup"><span data-stu-id="4c16f-206">When you're ready to try saving the in-memory anchors to the SpatialAnchorStore, you can loop through your collection and try to save each one.</span></span>

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

### <a name="load-content-from-the-anchor-store-when-the-app-resumes"></a><span data-ttu-id="4c16f-207">アプリの再開時にアンカーストアからコンテンツを読み込む</span><span class="sxs-lookup"><span data-stu-id="4c16f-207">Load content from the anchor store when the app resumes</span></span>

<span data-ttu-id="4c16f-208">保存されているアンカーを AnchorStore に復元するには、アプリケーションの再開時または任意の時点で、アンカーストアの IMapView から SpatialAnchors のメモリ内のデータベースに転送します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-208">You can restore saved anchors in the AnchorStore by transferring them from the anchor store's IMapView to your own in-memory database of SpatialAnchors when your app resumes or at any time.</span></span>

<span data-ttu-id="4c16f-209">SpatialAnchorStore からアンカーを復元するには、必要なものをそれぞれメモリ内コレクションに復元します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-209">To restore anchors from the SpatialAnchorStore, restore each one that you're interested in to your own in-memory collection.</span></span>

<span data-ttu-id="4c16f-210">作成した SpatialAnchors に文字列を関連付けるには、SpatialAnchors の独自のメモリ内データベースが必要です。</span><span class="sxs-lookup"><span data-stu-id="4c16f-210">You need your own in-memory database of SpatialAnchors to associate Strings with the SpatialAnchors that you create.</span></span> <span data-ttu-id="4c16f-211">このサンプルコードでは、Windows:: Foundation:: Collections:: IMap を使用してアンカーを格納することを選択します。これにより、SpatialAnchorStore で同じキーとデータ値を簡単に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-211">In our sample code, we choose to use a Windows::Foundation::Collections::IMap to store the anchors, which makes it easy to use the same key and data value for the SpatialAnchorStore.</span></span>

```
   // This is an in-memory anchor list that is separate from the anchor store.
   // These anchors may be used, reasoned about, and so on before committing the collection to the store.
   Windows::Foundation::Collections::IMap<Platform::String^, Windows::Perception::Spatial::SpatialAnchor^>^ m_anchorMap;
```

>[!NOTE]
><span data-ttu-id="4c16f-212">復元されるアンカーは、すぐには見つからない場合があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-212">An anchor that is restored might not be locatable right away.</span></span> <span data-ttu-id="4c16f-213">たとえば、アンカーが別の部屋にある場合や、別の建物に配置される場合があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-213">For example, it might be an anchor in a separate room or in a different building altogether.</span></span> <span data-ttu-id="4c16f-214">AnchorStore から取得したアンカーは、使用前に locatability をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-214">Anchors retrieved from the AnchorStore should be tested for locatability before using them.</span></span>

<br>

>[!NOTE]
><span data-ttu-id="4c16f-215">このコード例では、AnchorStore からすべてのアンカーを取得します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-215">In this example code, we retrieve all anchors from the AnchorStore.</span></span> <span data-ttu-id="4c16f-216">これは必須ではありません。アプリでは、実装にとって意味のある文字列キー値を使用して、アンカーの特定のサブセットを選択して選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-216">This is not a requirement; your app could just as well pick and choose a certain subset of anchors by using String key values that are meaningful to your implementation.</span></span>

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

### <a name="clear-the-anchor-store-when-needed"></a><span data-ttu-id="4c16f-217">必要に応じてアンカーストアをクリアする</span><span class="sxs-lookup"><span data-stu-id="4c16f-217">Clear the anchor store, when needed</span></span>

<span data-ttu-id="4c16f-218">場合によっては、アプリの状態をクリアして新しいデータを書き込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-218">Sometimes, you need to clear app state and write new data.</span></span> <span data-ttu-id="4c16f-219">[SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx)を使用してこれを行う方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-219">Here's how you do that with the [SpatialAnchorStore](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchorstore.aspx).</span></span>

<span data-ttu-id="4c16f-220">ヘルパークラスを使用すると、Clear 関数をラップする必要がほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="4c16f-220">Using our helper class, it's almost unnecessary to wrap the Clear function.</span></span> <span data-ttu-id="4c16f-221">このサンプル実装では、ヘルパークラスに SpatialAnchorStore インスタンスを所有する役割が与えられているため、このようにします。</span><span class="sxs-lookup"><span data-stu-id="4c16f-221">We choose to do so in our sample implementation, because our helper class is given the responsibility of owning the SpatialAnchorStore instance.</span></span>

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

### <a name="example-relating-anchor-coordinate-systems-to-stationary-reference-frame-coordinate-systems"></a><span data-ttu-id="4c16f-222">例: アンカー座標系を静止参照フレーム座標系に関連付ける</span><span class="sxs-lookup"><span data-stu-id="4c16f-222">Example: Relating anchor coordinate systems to stationary reference frame coordinate systems</span></span>

<span data-ttu-id="4c16f-223">アンカーがあるとします。アンカーの座標系にあるものを、他のコンテンツに対して既に使用している SpatialStationaryReferenceFrame に関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-223">Let's say you have an anchor, and you want to relate something in your anchor's coordinate system to the SpatialStationaryReferenceFrame you’re already using for your other content.</span></span> <span data-ttu-id="4c16f-224">[Trygettransformto を](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx)使用すると、アンカーの座標系から、固定の参照フレームの変換を取得できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-224">You can use [TryGetTransformTo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.trygettransformto.aspx) to get a transform from the anchor’s coordinate system to that of the stationary reference frame:</span></span>

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

<span data-ttu-id="4c16f-225">このプロセスは、次の2つの方法で役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-225">This process is useful to you in two ways:</span></span>
1. <span data-ttu-id="4c16f-226">2つの参照フレームが互いに相対的に認識されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-226">It tells you if the two reference frames can be understood relative to one another, and;</span></span>
2. <span data-ttu-id="4c16f-227">含まれている場合は、ある座標系から別の座標系に直接進む変換を提供します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-227">If so, it provides you a transform to go directly from one coordinate system to the other.</span></span>

<span data-ttu-id="4c16f-228">この情報を使用すると、2つの参照フレーム間のオブジェクト間の空間リレーションシップについて理解できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-228">With this information, you have an understanding of the spatial relation between objects between the two reference frames.</span></span>

<span data-ttu-id="4c16f-229">レンダリングのために、多くの場合、元の参照フレームまたはアンカーに従ってオブジェクトをグループ化することで、より良い結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-229">For rendering, you can often obtain better results by grouping objects according to their original reference frame or anchor.</span></span> <span data-ttu-id="4c16f-230">グループごとに個別の描画パスを実行します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-230">Perform a separate drawing pass for each group.</span></span> <span data-ttu-id="4c16f-231">ビュー行列は、同じ座標系を使用して最初に作成されたモデル変換を持つオブジェクトに対してより正確です。</span><span class="sxs-lookup"><span data-stu-id="4c16f-231">The view matrices are more accurate for objects with model transforms that are created initially using the same coordinate system.</span></span>

## <a name="create-holograms-using-a-device-attached-frame-of-reference"></a><span data-ttu-id="4c16f-232">デバイスに接続された参照のフレームを使用してホログラムを作成する</span><span class="sxs-lookup"><span data-stu-id="4c16f-232">Create holograms using a device-attached frame of reference</span></span>

<span data-ttu-id="4c16f-233">デバイスの場所に [まだアタッチさ](../../design/coordinate-systems.md#attached-frame-of-reference) れているホログラムをレンダリングする必要がある場合があります。たとえば、デバッグ情報を含むパネルや、デバイスが領域内の位置ではなく向きだけを判断できる場合に、情報メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-233">There are times when you want to render a hologram that [remains attached](../../design/coordinate-systems.md#attached-frame-of-reference) to the device's location, for example a panel with debugging information or an informational message when the device is only able to determine its orientation and not its position in space.</span></span> <span data-ttu-id="4c16f-234">これを実現するには、関連付けられている参照のフレームを使用します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-234">To accomplish this, we use an attached frame of reference.</span></span>

<span data-ttu-id="4c16f-235">SpatialLocatorAttachedFrameOfReference クラスは、実際の環境ではなく、デバイスに対して相対的な座標系を定義します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-235">The SpatialLocatorAttachedFrameOfReference class defines coordinate systems, which are relative to the device rather than to the real-world.</span></span> <span data-ttu-id="4c16f-236">このフレームには、参照フレームの作成時にユーザーが直面していた方向を示す、ユーザーの周囲を基準とした固定の見出しがあります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-236">This frame has a fixed heading relative to the user's surroundings that points in the direction the user was facing when the reference frame was created.</span></span> <span data-ttu-id="4c16f-237">その後、ユーザーがデバイスを回転させる場合でも、この参照フレーム内のすべての向きは、その固定の見出しに対して相対的になります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-237">From then on, all orientations in this frame of reference are relative to that fixed heading, even as the user rotates the device.</span></span>

<span data-ttu-id="4c16f-238">HoloLens の場合、このフレームの座標系の原点は、ユーザーの頭の回転の中心にあります。そのため、その位置はヘッドローテーションの影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="4c16f-238">For HoloLens, the origin of this frame's coordinate system is located at the center of rotation of the user's head, so that its position is not affected by head rotation.</span></span> <span data-ttu-id="4c16f-239">アプリでは、この点を基準としたオフセットを指定して、ユーザーの前にホログラムを配置できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-239">Your app can specify an offset relative to this point to position holograms in front of the user.</span></span>

<span data-ttu-id="4c16f-240">SpatialLocatorAttachedFrameOfReference を取得するには、SpatialLocator クラスを使用して CreateAttachedFrameOfReferenceAtCurrentHeading を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-240">To get a SpatialLocatorAttachedFrameOfReference, use the SpatialLocator class and call CreateAttachedFrameOfReferenceAtCurrentHeading.</span></span>

<span data-ttu-id="4c16f-241">これは、Windows Mixed Reality デバイスの範囲全体に適用されます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-241">This applies to the entire range of Windows Mixed Reality devices.</span></span>

### <a name="use-a-reference-frame-attached-to-the-device"></a><span data-ttu-id="4c16f-242">デバイスにアタッチされている参照フレームを使用する</span><span class="sxs-lookup"><span data-stu-id="4c16f-242">Use a reference frame attached to the device</span></span>

<span data-ttu-id="4c16f-243">これらのセクションでは、この API を使用してデバイスに接続された参照のフレームを有効にするために、Windows Holographic アプリテンプレートで変更された内容について説明します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-243">These sections talk about what we changed in the Windows Holographic app template to enable a device-attached frame of reference using this API.</span></span> <span data-ttu-id="4c16f-244">この "接続済み" ホログラムは、固定されたホログラムと共に動作します。また、デバイスが世界での位置を一時的に見つけることができない場合にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-244">This "attached" hologram will work alongside stationary or anchored holograms, and may also be used when the device is temporarily unable to find its position in the world.</span></span>

<span data-ttu-id="4c16f-245">まず、SpatialStationaryFrameOfReference の代わりに SpatialLocatorAttachedFrameOfReference を格納するようにテンプレートを変更しました。</span><span class="sxs-lookup"><span data-stu-id="4c16f-245">First, we changed the template to store a SpatialLocatorAttachedFrameOfReference instead of a SpatialStationaryFrameOfReference:</span></span>

<span data-ttu-id="4c16f-246">**HolographicTagAlongSampleMain** から:</span><span class="sxs-lookup"><span data-stu-id="4c16f-246">From **HolographicTagAlongSampleMain.h**:</span></span>

```
   // A reference frame attached to the holographic camera.
   Windows::Perception::Spatial::SpatialLocatorAttachedFrameOfReference^   m_referenceFrame;
```

<span data-ttu-id="4c16f-247">**HolographicTagAlongSampleMain** から:</span><span class="sxs-lookup"><span data-stu-id="4c16f-247">From **HolographicTagAlongSampleMain.cpp**:</span></span>

```
   // In this example, we create a reference frame attached to the device.
   m_referenceFrame = m_locator->CreateAttachedFrameOfReferenceAtCurrentHeading();
```

<span data-ttu-id="4c16f-248">更新中に、フレーム予測を使用してから取得したタイムスタンプで座標系を取得できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="4c16f-248">During the update, we now obtain the coordinate system at the time stamp obtained from with the frame prediction.</span></span>

```
   // Next, we get a coordinate system from the attached frame of reference that is
   // associated with the current frame. Later, this coordinate system is used for
   // for creating the stereo view matrices when rendering the sample content.
   SpatialCoordinateSystem^ currentCoordinateSystem =
       m_referenceFrame->GetStationaryCoordinateSystemAtTimestamp(prediction->Timestamp);
```

### <a name="get-a-spatial-pointer-pose-and-follow-the-users-gaze"></a><span data-ttu-id="4c16f-249">空間ポインターのポーズを取得し、ユーザーの宝石に従います。</span><span class="sxs-lookup"><span data-stu-id="4c16f-249">Get a spatial pointer pose, and follow the user's Gaze</span></span>

<span data-ttu-id="4c16f-250">この例では、holographic シェルがユーザーの見つめに従う方法と同様に、ユーザーの [宝石](../../design/gaze-and-commit.md)に従うように、ホログラムの例を使用します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-250">We want our example hologram to follow the user's [gaze](../../design/gaze-and-commit.md), similar to how the holographic shell can follow the user's gaze.</span></span> <span data-ttu-id="4c16f-251">そのためには、同じタイムスタンプから SpatialPointerPose を取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-251">For this, we need to get the SpatialPointerPose from the same time stamp.</span></span>

```
SpatialPointerPose^ pose = SpatialPointerPose::TryGetAtTimestamp(currentCoordinateSystem, prediction->Timestamp);
```

<span data-ttu-id="4c16f-252">この SpatialPointerPose には、 [ユーザーの現在の見出し](gaze-in-directx.md)に従ってホログラムを配置するために必要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4c16f-252">This SpatialPointerPose has the information needed to position the hologram according to the [user's current heading](gaze-in-directx.md).</span></span>

<span data-ttu-id="4c16f-253">ユーザーに快適に使用するために、線形補間 ("lerp") を使用して、一定期間内の変化を滑らかにします。</span><span class="sxs-lookup"><span data-stu-id="4c16f-253">For user comfort, we use linear interpolation ("lerp") to smooth the change in position over a period of time.</span></span> <span data-ttu-id="4c16f-254">これは、ホログラムを見つめにロックするよりも、ユーザーにとってより使いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-254">This is more comfortable for the user than locking the hologram to their gaze.</span></span> <span data-ttu-id="4c16f-255">タグに沿ったホログラムの位置を Lerping することで、動きをダンパーすることによって、ホログラムを安定させることもできます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-255">Lerping the tag-along hologram's position also allows us to stabilize the hologram by dampening the movement.</span></span> <span data-ttu-id="4c16f-256">このダンパーを実行しなかった場合、通常はユーザーの頭のなるべくな動きと見なされるため、ユーザーにはホログラムのジッターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-256">If we didn't do this dampening, the user would see the hologram jitter because of what are normally considered to be imperceptible movements of the user's head.</span></span>

<span data-ttu-id="4c16f-257">From **StationaryQuadRenderer::P ositionhologram**:</span><span class="sxs-lookup"><span data-stu-id="4c16f-257">From **StationaryQuadRenderer::PositionHologram**:</span></span>

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
><span data-ttu-id="4c16f-258">デバッグパネルの場合は、表示が妨げされないように、ホログラムを少し左に移動することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-258">In the case of a debugging panel, you might choose to reposition the hologram off to the side a little so that it doesn't obstruct your view.</span></span> <span data-ttu-id="4c16f-259">その方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-259">Here's an example of how you might do that.</span></span>

<span data-ttu-id="4c16f-260">StationaryQuadRenderer の場合 **::P ositionhologram**:</span><span class="sxs-lookup"><span data-stu-id="4c16f-260">For **StationaryQuadRenderer::PositionHologram**:</span></span>

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

### <a name="rotate-the-hologram-to-face-the-camera"></a><span data-ttu-id="4c16f-261">ホログラムを回転してカメラに面します</span><span class="sxs-lookup"><span data-stu-id="4c16f-261">Rotate the hologram to face the camera</span></span>

<span data-ttu-id="4c16f-262">ホログラムを配置するだけでは十分ではありません。この場合は、クワッドです。また、ユーザーに対してオブジェクトを回転させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-262">It isn't enough to position the hologram, which in this case is a quad; we must also rotate the object to face the user.</span></span> <span data-ttu-id="4c16f-263">この種類の billboarding では、ホログラムがユーザーの環境の一部として保持されるため、このローテーションはワールド空間で行われます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-263">This rotation occurs in world space, because this type of billboarding allows the hologram to remain a part of the user's environment.</span></span> <span data-ttu-id="4c16f-264">ホログラムが画面の向きにロックされるため、ビュースペースの billboarding は快適ではありません。その場合、ステレオレンダリングを中断しないビュー領域のビルボード変換を取得するために、左右のビュー行列を補間する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-264">View-space billboarding isn't as comfortable because the hologram becomes locked to the display orientation; in that case, you would also have to interpolate between the left and right view matrices to acquire a view-space billboard transform that doesn't disrupt stereo rendering.</span></span> <span data-ttu-id="4c16f-265">ここでは、X 軸と Z 軸を回転させてユーザーを中心にしています。</span><span class="sxs-lookup"><span data-stu-id="4c16f-265">Here, we rotate on the X and Z axes to face the user.</span></span>

<span data-ttu-id="4c16f-266">**StationaryQuadRenderer:: Update** から:</span><span class="sxs-lookup"><span data-stu-id="4c16f-266">From **StationaryQuadRenderer::Update**:</span></span>

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

### <a name="render-the-attached-hologram"></a><span data-ttu-id="4c16f-267">添付されたホログラムをレンダリングします</span><span class="sxs-lookup"><span data-stu-id="4c16f-267">Render the attached hologram</span></span>

<span data-ttu-id="4c16f-268">この例では、ホログラムを SpatialLocatorAttachedReferenceFrame の座標系でレンダリングすることも選択しています。これは、ホログラムを配置した場所です。</span><span class="sxs-lookup"><span data-stu-id="4c16f-268">For this example, we also choose to render the hologram in the coordinate system of the SpatialLocatorAttachedReferenceFrame, which is where we positioned the hologram.</span></span> <span data-ttu-id="4c16f-269">(別の座標系を使用してレンダリングすることにした場合は、デバイスに接続されている参照フレームの座標系から、その座標系に変換を取得する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="4c16f-269">(If we had decided to render using another coordinate system, we would need to acquire a transform from the device-attached reference frame's coordinate system to that coordinate system.)</span></span>

<span data-ttu-id="4c16f-270">**HolographicTagAlongSampleMain:: Render** から:</span><span class="sxs-lookup"><span data-stu-id="4c16f-270">From **HolographicTagAlongSampleMain::Render**:</span></span>

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

<span data-ttu-id="4c16f-271">以上で作業は終了です。</span><span class="sxs-lookup"><span data-stu-id="4c16f-271">That's it!</span></span> <span data-ttu-id="4c16f-272">ホログラムは、ユーザーの見つめ方向の前に2メートルの位置を "追跡" するようになります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-272">The hologram will now "chase" a position that is 2 meters in front of the user's gaze direction.</span></span>

>[!NOTE]
><span data-ttu-id="4c16f-273">この例では、追加のコンテンツも読み込まれます。 StationaryQuadRenderer を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c16f-273">This example also loads additional content - see StationaryQuadRenderer.cpp.</span></span>

## <a name="handling-tracking-loss"></a><span data-ttu-id="4c16f-274">追跡損失の処理</span><span class="sxs-lookup"><span data-stu-id="4c16f-274">Handling tracking loss</span></span>

<span data-ttu-id="4c16f-275">デバイスが世界中で見つからない場合、アプリでは "損失の追跡" が発生します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-275">When the device can't locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="4c16f-276">Windows Mixed Reality アプリは、位置指定追跡システムの中断を処理できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="4c16f-276">Windows Mixed Reality apps should be able to handle such disruptions to the positional tracking system.</span></span> <span data-ttu-id="4c16f-277">既定の SpatialLocator で Locatの変更イベントを使用することにより、これらの中断を監視し、応答を作成できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-277">These disruptions can be observed, and responses created, by using the LocatabilityChanged event on the default SpatialLocator.</span></span>

<span data-ttu-id="4c16f-278">**Appmain:: SetHolographicSpace から:**</span><span class="sxs-lookup"><span data-stu-id="4c16f-278">From **AppMain::SetHolographicSpace:**</span></span>

```
   // Be able to respond to changes in the positional tracking state.
   m_locatabilityChangedToken =
       m_locator->LocatabilityChanged +=
           ref new Windows::Foundation::TypedEventHandler<SpatialLocator^, Object^>(
               std::bind(&HolographicApp1Main::OnLocatabilityChanged, this, _1, _2)
               );
```

<span data-ttu-id="4c16f-279">アプリが Locat信頼性変更イベントを受け取ると、必要に応じて動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-279">When your app receives a LocatabilityChanged event, it can change behavior as needed.</span></span> <span data-ttu-id="4c16f-280">たとえば、PositionalTrackingInhibited 状態では、アプリは通常の操作を一時停止し、警告メッセージを表示する [タグに沿ったホログラム](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) をレンダリングすることができます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-280">For example, in the PositionalTrackingInhibited state, your app can pause normal operation and render a [tag-along hologram](coordinate-systems-in-directx.md#create-holograms-using-a-device-attached-frame-of-reference) that displays a warning message.</span></span>

<span data-ttu-id="4c16f-281">Windows Holographic アプリケーションテンプレートには、既に作成されている Locat信頼性変更ハンドラーが付属しています。</span><span class="sxs-lookup"><span data-stu-id="4c16f-281">The Windows Holographic app template comes with a LocatabilityChanged handler already created for you.</span></span> <span data-ttu-id="4c16f-282">既定では、位置追跡が使用できない場合、デバッグコンソールに警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-282">By default, it displays a warning in the debug console when positional tracking is unavailable.</span></span> <span data-ttu-id="4c16f-283">このハンドラーにコードを追加して、アプリから必要な応答を提供できます。</span><span class="sxs-lookup"><span data-stu-id="4c16f-283">You can add code to this handler to provide a response as needed from your app.</span></span>

<span data-ttu-id="4c16f-284">**Appmain .cpp から:**</span><span class="sxs-lookup"><span data-stu-id="4c16f-284">From **AppMain.cpp:**</span></span>

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

## <a name="spatial-mapping"></a><span data-ttu-id="4c16f-285">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="4c16f-285">Spatial mapping</span></span>

<span data-ttu-id="4c16f-286">[空間マッピング](spatial-mapping-in-directx.md)api は、座標系を使用して、サーフェスメッシュのモデル変換を取得します。</span><span class="sxs-lookup"><span data-stu-id="4c16f-286">The [spatial mapping](spatial-mapping-in-directx.md) APIs make use of coordinate systems to get model transforms for surface meshes.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c16f-287">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c16f-287">See also</span></span>
* [<span data-ttu-id="4c16f-288">座標系</span><span class="sxs-lookup"><span data-stu-id="4c16f-288">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="4c16f-289">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="4c16f-289">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* <span data-ttu-id="4c16f-290"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="4c16f-290"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* [<span data-ttu-id="4c16f-291">DirectX でのヘッド視線入力とアイ視線入力</span><span class="sxs-lookup"><span data-stu-id="4c16f-291">Head and eye gaze in DirectX</span></span>](gaze-in-directx.md)
* [<span data-ttu-id="4c16f-292">DirectX での手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="4c16f-292">Hands and motion controllers in DirectX</span></span>](hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="4c16f-293">DirectX の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="4c16f-293">Spatial mapping in DirectX</span></span>](spatial-mapping-in-directx.md)
