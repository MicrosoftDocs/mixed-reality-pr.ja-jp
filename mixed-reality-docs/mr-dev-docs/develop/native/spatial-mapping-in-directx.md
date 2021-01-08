---
title: DirectX の空間マッピング
description: DirectX アプリで空間マッピングを実装する方法と、ユニバーサル Windows プラットフォーム SDK で空間マッピングサンプルアプリケーションを使用する方法について説明します。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Windows mixed reality, 空間マッピング, 環境, 相互作用, directx, winrt, api, サンプルコード, UWP, SDK, チュートリアル
ms.openlocfilehash: bcd78487e96aaf09707aa4bf58917223cc2e8583
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006712"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="2d7d6-104">DirectX の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="2d7d6-104">Spatial mapping in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="2d7d6-105">この記事は、従来の WinRT ネイティブ Api に関連しています。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="2d7d6-106">新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](openxr-getting-started.md)** を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-106">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)**.</span></span>

<span data-ttu-id="2d7d6-107">このトピックでは、DirectX アプリで [空間マッピング](../../design/spatial-mapping.md) を実装する方法について説明します。これには、ユニバーサル Windows プラットフォーム SDK でパッケージ化された空間マッピングサンプルアプリケーションの詳細な説明が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-107">This topic describes how to implement [spatial mapping](../../design/spatial-mapping.md) in your DirectX app, including a detailed explanation of the spatial mapping sample application packaged with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="2d7d6-108">このトピックでは、 [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP コードサンプルのコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-108">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="2d7d6-109">この記事のコードスニペットでは、 [C++ holographic プロジェクトテンプレート](creating-a-holographic-directx-project.md)で使用される c + c++ 17 準拠の c++/WinRT ではなく、c++/cx の使用方法を現在説明しています。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-109">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="2d7d6-110">概念は C++/WinRT プロジェクトに相当しますが、コードを変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-110">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="2d7d6-111">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="2d7d6-111">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d7d6-112"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="2d7d6-112"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="2d7d6-113"><a href="../../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d7d6-113"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="2d7d6-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="2d7d6-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="2d7d6-115"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d7d6-115"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2d7d6-116">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="2d7d6-116">Spatial mapping</span></span></td>
        <td><span data-ttu-id="2d7d6-117">✔️</span><span class="sxs-lookup"><span data-stu-id="2d7d6-117">✔️</span></span></td>
        <td><span data-ttu-id="2d7d6-118">✔️</span><span class="sxs-lookup"><span data-stu-id="2d7d6-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a><span data-ttu-id="2d7d6-119">DirectX 開発の概要</span><span class="sxs-lookup"><span data-stu-id="2d7d6-119">DirectX development overview</span></span>

<span data-ttu-id="2d7d6-120">空間マッピングのネイティブアプリケーション開発では、 [Windows](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) のような名前空間の api を使用します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-120">Native application development for spatial mapping uses the APIs in the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="2d7d6-121">これらの Api を使用すると、空間マッピング Api が [Unity](../unity/spatial-mapping-in-unity.md)によって公開されるのと同じ方法で、空間マッピング機能を完全に制御できます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-121">These APIs give you full control of spatial mapping functionality, in the same way that spatial mapping APIs are exposed by [Unity](../unity/spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="2d7d6-122">認識 Api</span><span class="sxs-lookup"><span data-stu-id="2d7d6-122">Perception APIs</span></span>

<span data-ttu-id="2d7d6-123">空間マッピング開発の主な種類は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-123">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="2d7d6-124">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) は、SpatialSurfaceInfo オブジェクトの形式で、ユーザーの近くにある、アプリケーションで指定された領域内のサーフェイスに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-124">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="2d7d6-125">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) は、一意の ID、境界ボリューム、最後の変更の時間など、1つの既存空間サーフェスを表します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-125">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="2d7d6-126">要求に応じて非同期的に SpatialSurfaceMesh を提供します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-126">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="2d7d6-127">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) には、SpatialSurfaceInfo から要求された SpatialSurfaceMesh オブジェクトをカスタマイズするために使用されるパラメーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-127">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="2d7d6-128">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) は、1つの空間サーフェスのメッシュデータを表します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-128">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="2d7d6-129">頂点の位置、頂点の法線、三角形のインデックスのデータは、メンバーの SpatialSurfaceMeshBuffer オブジェクトに含まれています。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-129">The data for vertex positions, vertex normals, and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="2d7d6-130">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) は、単一の種類のメッシュデータをラップします。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-130">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="2d7d6-131">これらの Api を使用してアプリケーションを開発する場合、基本的なプログラムフローは次のようになります (以下で説明するサンプルアプリケーションで示すように)。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-131">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="2d7d6-132">**SpatialSurfaceObserver を設定する**</span><span class="sxs-lookup"><span data-stu-id="2d7d6-132">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="2d7d6-133">[Requestaccessasync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)を呼び出して、ユーザーがアプリケーションにデバイスの空間マッピング機能を使用するためのアクセス許可を与えられていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-133">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="2d7d6-134">SpatialSurfaceObserver オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-134">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="2d7d6-135">空間サーフェスに関する情報が必要な領域を指定するには、 [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-135">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="2d7d6-136">今後、この関数を呼び出して、これらのリージョンを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-136">You may modify these regions in the future by calling this function again.</span></span> <span data-ttu-id="2d7d6-137">各リージョンは、 [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx)を使用して指定されます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-137">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="2d7d6-138">[ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx)イベントに登録します。これは、指定した領域の空間サーフェスに関する新しい情報が利用可能になるたびに起動されます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-138">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you've specified.</span></span>
- <span data-ttu-id="2d7d6-139">**ObservedSurfacesChanged イベントの処理**</span><span class="sxs-lookup"><span data-stu-id="2d7d6-139">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="2d7d6-140">イベントハンドラーで、 [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) を呼び出して、SpatialSurfaceInfo オブジェクトのマップを受信します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-140">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="2d7d6-141">このマップを使用して、 [ユーザーの環境内に存在](../../design/spatial-mapping.md#mesh-caching)する空間サーフェスのレコードを更新できます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-141">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](../../design/spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="2d7d6-142">各 SpatialSurfaceInfo オブジェクトに対して、 [Trygetbounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) に対してクエリを実行し、選択した [空間座標系](../../design/coordinate-systems.md) で表現されるサーフェスの空間範囲を決定することができます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-142">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](../../design/coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="2d7d6-143">空間サーフェスのメッシュを要求する場合は、 [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-143">If you decide to request,  mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="2d7d6-144">三角形の密度、および返されるメッシュデータの形式を指定するオプションを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-144">You may provide options specifying the density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="2d7d6-145">**メッシュの受信と処理**</span><span class="sxs-lookup"><span data-stu-id="2d7d6-145">**Receive and process mesh**</span></span>
  - <span data-ttu-id="2d7d6-146">TryComputeLatestMeshAsync を呼び出すたびに、1つの SpatialSurfaceMesh オブジェクトが非同期に返されます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-146">Each call to TryComputeLatestMeshAsync will asynchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="2d7d6-147">このオブジェクトから、含まれている SpatialSurfaceMeshBuffer オブジェクトにアクセスできます。これにより、メッシュの三角形のインデックス、頂点位置、および頂点法線を要求した場合にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-147">From this object, you can access the contained SpatialSurfaceMeshBuffer objects, which gives you access to the triangle indices, vertex positions, and vertex normals of the mesh if you request them.</span></span> <span data-ttu-id="2d7d6-148">このデータは、メッシュのレンダリングに使用される [Direct3D 11 api](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) と直接互換性がある形式になります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-148">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="2d7d6-149">ここから、アプリケーションでメッシュデータを必要に応じて分析または [処理](../../design/spatial-mapping.md#mesh-processing) し、 [レンダリング](../../design/spatial-mapping.md#rendering) や物理的な [raycasting と競合](../../design/spatial-mapping.md#raycasting-and-collision)に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-149">From here your application can optionally analyze or [process](../../design/spatial-mapping.md#mesh-processing) the mesh data, and use it for [rendering](../../design/spatial-mapping.md#rendering) and physics [raycasting and collision](../../design/spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="2d7d6-150">注意すべき重要な点の1つは、メッシュの頂点位置 (メッシュのレンダリングに使用される頂点シェーダーなど) にスケールを適用して、バッファーに格納されている最適化された整数単位からメーターに変換する必要があることです。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-150">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they're stored in the buffer, to meters.</span></span> <span data-ttu-id="2d7d6-151">このスケールを取得するには、 [Vertexpositionscale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-151">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="2d7d6-152">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="2d7d6-152">Troubleshooting</span></span>
* <span data-ttu-id="2d7d6-153">[SpatialSurfaceMesh スケール](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)によって返されるスケールを使用して、頂点シェーダー内のメッシュ頂点の位置を必ずスケーリングしてください。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-153">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="2d7d6-154">空間マッピングコードサンプルのチュートリアル</span><span class="sxs-lookup"><span data-stu-id="2d7d6-154">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="2d7d6-155">[Holographic 空間マッピング](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)コードサンプルには、サーフェイスメッシュを管理および表示するためのインフラストラクチャを含む、アプリへのサーフェイスメッシュの読み込みを開始するために使用できるコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-155">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="2d7d6-156">ここでは、DirectX アプリに surface マッピング機能を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-156">Now, we walk through how to add surface-mapping capability to your DirectX app.</span></span> <span data-ttu-id="2d7d6-157">このコードを [Windows Holographic アプリケーションテンプレート](creating-a-holographic-directx-project.md) プロジェクトに追加することも、前に説明したコードサンプルを参照して操作することもできます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-157">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="2d7d6-158">このコードサンプルは、Windows Holographic アプリケーションテンプレートに基づいています。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-158">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="2d7d6-159">SpatialPerception 機能を使用するようにアプリを設定する</span><span class="sxs-lookup"><span data-stu-id="2d7d6-159">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="2d7d6-160">アプリで空間マッピング機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-160">Your app can use the spatial mapping capability.</span></span> <span data-ttu-id="2d7d6-161">これが必要になるのは、空間メッシュがユーザーの環境を表しているためです。これは、プライベートデータと見なされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-161">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="2d7d6-162">この機能をアプリの package.appxmanifest ファイルで宣言します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-162">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="2d7d6-163">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-163">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="2d7d6-164">この機能は、 **uap2** 名前空間から取得されます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-164">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="2d7d6-165">マニフェスト内のこの名前空間へのアクセスを取得するには、パッケージの> 要素に *xlmns* 属性として含め &lt; ます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-165">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="2d7d6-166">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-166">Here's an example:</span></span>

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="2d7d6-167">空間マッピング機能のサポートを確認する</span><span class="sxs-lookup"><span data-stu-id="2d7d6-167">Check for spatial mapping feature support</span></span>

<span data-ttu-id="2d7d6-168">Windows Mixed Reality は、空間マッピングをサポートしていないデバイスを含む幅広いデバイスをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-168">Windows Mixed Reality supports a wide range of devices, including devices, which don't support spatial mapping.</span></span> <span data-ttu-id="2d7d6-169">アプリで空間マッピングを使用できる場合、または空間マッピングを使用して機能を提供する場合は、使用する前に空間マッピングがサポートされていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-169">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="2d7d6-170">たとえば、混合の現実のアプリで空間マッピングが必要な場合、ユーザーが空間マッピングを使用せずにデバイスで実行しようとすると、その効果に関するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-170">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="2d7d6-171">または、アプリでユーザーの環境の代わりに独自の仮想環境をレンダリングすることができます。これは、空間マッピングが使用可能であった場合に発生するようなエクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-171">Or, your app can render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="2d7d6-172">どのような場合でも、この API によって、アプリは空間マッピングデータを取得せず、適切な方法で応答するタイミングを認識できます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-172">In any event, this API allows your app to be aware of when it won't get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="2d7d6-173">現在のデバイスでの空間マッピングのサポートを確認するには、最初に UWP コントラクトがレベル4以上であることを確認してから、SpatialSurfaceObserver:: IsSupported () を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-173">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="2d7d6-174">[Holographic 空間マッピング](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping)コードサンプルのコンテキストでこれを行う方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-174">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="2d7d6-175">アクセスを要求する直前にサポートが確認されます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-175">Support is checked just before requesting access.</span></span>

<span data-ttu-id="2d7d6-176">SpatialSurfaceObserver:: IsSupported () API は、SDK バージョン15063以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-176">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="2d7d6-177">必要に応じて、この API を使用する前に、プロジェクトをプラットフォームバージョン15063に再ターゲットします。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-177">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

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

<span data-ttu-id="2d7d6-178">UWP コントラクトがレベル4より小さい場合は、デバイスが空間マッピングを実行できるかのようにアプリを続行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-178">When the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="2d7d6-179">空間マッピングデータへのアクセスを要求する</span><span class="sxs-lookup"><span data-stu-id="2d7d6-179">Request access to spatial mapping data</span></span>

<span data-ttu-id="2d7d6-180">アプリケーションは、surface オブザーバーを作成する前に、空間マッピングデータにアクセスするためのアクセス許可を要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-180">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="2d7d6-181">次に、このページで後ほど詳しく説明する、Surface マッピングのコードサンプルに基づく例を示します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-181">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

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

### <a name="create-a-surface-observer"></a><span data-ttu-id="2d7d6-182">Surface オブザーバーを作成する</span><span class="sxs-lookup"><span data-stu-id="2d7d6-182">Create a surface observer</span></span>

<span data-ttu-id="2d7d6-183">**Windows::P erception:: 空間::** surface 名前空間には、 [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)クラスが含まれています。このクラスは、 [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx)で指定した1つ以上のボリュームを監視します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-183">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="2d7d6-184">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx)インスタンスを使用して、リアルタイムでサーフェイスメッシュデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-184">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="2d7d6-185">**Appmain** から:</span><span class="sxs-lookup"><span data-stu-id="2d7d6-185">From **AppMain.h**:</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="2d7d6-186">前のセクションで説明したように、アプリで使用できるようにするには、空間マッピングデータへのアクセスを要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-186">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="2d7d6-187">このアクセスは、HoloLens に自動的に付与されます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-187">This access is granted automatically on the HoloLens.</span></span>

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

<span data-ttu-id="2d7d6-188">次に、特定の境界ボリュームを観察するように surface オブザーバーを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-188">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="2d7d6-189">ここでは、座標系の原点を中心とした、20x20x5 メートルの箱があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-189">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

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

<span data-ttu-id="2d7d6-190">代わりに、複数の境界ボリュームを設定できます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-190">You can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="2d7d6-191">*これは擬似コードです。*</span><span class="sxs-lookup"><span data-stu-id="2d7d6-191">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="2d7d6-192">また、ビューを視するビューや、軸に沿っていない境界ボックスなど、他の境界図形を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-192">It's also possible to use other bounding shapes - such as a view frustum, or a bounding box that isn't axis aligned.</span></span>

<span data-ttu-id="2d7d6-193">*これは擬似コードです。*</span><span class="sxs-lookup"><span data-stu-id="2d7d6-193">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="2d7d6-194">Surface マッピングデータを使用できない場合にアプリの動作を変える必要がある場合は、 [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) が **許可** されていない場合に応答するコードを記述できます。たとえば、デバイスにデバイスが搭載されていても、空間マッピング用のハードウェアがないため、このようなデバイスは許可されません。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-194">If your app needs to do anything differently when surface mapping data isn't available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) isn't **Allowed** - for example, it won't be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="2d7d6-195">これらのデバイスでは、代わりに、ユーザーの環境とデバイスの構成に関する情報を空間ステージに依存させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-195">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="2d7d6-196">Surface メッシュコレクションの初期化と更新</span><span class="sxs-lookup"><span data-stu-id="2d7d6-196">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="2d7d6-197">Surface オブザーバーが正常に作成された場合、surface メッシュコレクションの初期化を続行できます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-197">If the surface observer was successfully created, we can continue to initialize our surface mesh collection.</span></span> <span data-ttu-id="2d7d6-198">ここでは、プルモデル API を使用して、現在観察されているサーフェスのセットをすぐに取得します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-198">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

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

<span data-ttu-id="2d7d6-199">Surface メッシュデータを取得するために使用できるプッシュモデルもあります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-199">There's also a push model available to get surface mesh data.</span></span> <span data-ttu-id="2d7d6-200">プルモデルのみを使用するようにアプリをデザインすることもできます。選択した場合は、(たとえば、フレームごとに1回、またはゲームのセットアップ中など、特定の期間に) データをポーリングします。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-200">You're free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="2d7d6-201">その場合は、上記のコードが必要です。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-201">If so, the above code is what you need.</span></span>

<span data-ttu-id="2d7d6-202">このコードサンプルでは、教育目的目的で両方のモデルを使用する方法を説明しました。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-202">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="2d7d6-203">ここでは、システムが変更を認識するたびに、最新の表面メッシュデータを受け取るイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-203">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="2d7d6-204">このコードサンプルは、これらのイベントに応答するようにも構成されています。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-204">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="2d7d6-205">では、その方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-205">Let's walk through how we do this.</span></span>

<span data-ttu-id="2d7d6-206">**注:** これは、アプリがメッシュデータを処理するための最も効率的な方法ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-206">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="2d7d6-207">このコードはわかりやすくするために記述されており、最適化されていません。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-207">This code is written for clarity and isn't optimized.</span></span>

<span data-ttu-id="2d7d6-208">Surface メッシュデータは、key 値として[Platform:: guid](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx)を使用して[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx)オブジェクトを格納する読み取り専用マップで提供されます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-208">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="2d7d6-209">このデータを処理するために、まずコレクションに含まれていないキー値を検索します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-209">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="2d7d6-210">サンプルアプリでのデータの格納方法の詳細については、このトピックの後半で説明します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-210">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

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

<span data-ttu-id="2d7d6-211">Surface メッシュコレクションに含まれていても、システムコレクションには存在しないサーフェスメッシュを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-211">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="2d7d6-212">これを行うには、メッシュを追加および更新するために説明したのとは逆の操作を行う必要があります。アプリのコレクションでループし、システムコレクションに含まれている **Guid** があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-212">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="2d7d6-213">システムコレクションに含まれていない場合は、私たちから削除します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-213">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="2d7d6-214">AppMain のイベントハンドラーから、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-214">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="2d7d6-215">RealtimeSurfaceMeshRenderer でのメッシュ排除の実装は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-215">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="2d7d6-216">Surface メッシュのデータバッファーを取得して使用する</span><span class="sxs-lookup"><span data-stu-id="2d7d6-216">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="2d7d6-217">Surface メッシュ情報の取得は、データコレクションをプルし、そのコレクションに更新を処理するのと同じように簡単でした。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-217">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="2d7d6-218">ここでは、データの使用方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-218">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="2d7d6-219">このコード例では、レンダリングにサーフェイスメッシュを使用することを選択しました。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-219">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="2d7d6-220">これは、実際のサーフェイスの背後にある occluding ホログラムの一般的なシナリオです。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-220">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="2d7d6-221">また、メッシュをレンダリングしたり、処理したバージョンをレンダリングして、アプリまたはゲームの機能の提供を開始する前に、どの領域がスキャンされるかをユーザーに示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-221">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="2d7d6-222">このコードサンプルでは、前のセクションで説明したイベントハンドラーから表面メッシュの更新を受信したときにプロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-222">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="2d7d6-223">この関数の重要なコード行は、surface *メッシュ* を更新するための呼び出しです。今回はメッシュ情報を既に処理したため、必要に応じて頂点とインデックスのデータを取得しようとしています。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-223">The important line of code in this function is the call to update the surface *mesh*: by this time we have already processed the mesh info, and we're about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="2d7d6-224">RealtimeSurfaceMeshRenderer から:</span><span class="sxs-lookup"><span data-stu-id="2d7d6-224">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

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

<span data-ttu-id="2d7d6-225">このサンプルコードは、データクラス **SurfaceMesh** がメッシュデータの処理とレンダリングを処理するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-225">Our sample code is designed so that a data class, **SurfaceMesh**, handles mesh data processing and rendering.</span></span> <span data-ttu-id="2d7d6-226">これらのメッシュは、 **RealtimeSurfaceMeshRenderer** が実際にマップを保持しているものです。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-226">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="2d7d6-227">各ファイルには、SpatialSurfaceMesh が送信元のものへの参照があるため、メッシュの頂点またはインデックスバッファーにアクセスしたり、メッシュの変換を取得したりする必要があるときに、いつでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-227">Each one has a reference to the SpatialSurfaceMesh it came from, so you can use it anytime you need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="2d7d6-228">ここでは、更新が必要であるとしてメッシュにフラグを付けます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-228">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="2d7d6-229">SurfaceMesh から:</span><span class="sxs-lookup"><span data-stu-id="2d7d6-229">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="2d7d6-230">次にメッシュがそれ自体を描画するように要求されたときに、最初にフラグをチェックします。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-230">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="2d7d6-231">更新が必要な場合は、頂点バッファーとインデックスバッファーが GPU 上で更新されます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-231">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

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

<span data-ttu-id="2d7d6-232">まず、生データバッファーを取得します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-232">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="2d7d6-233">次に、HoloLens によって提供されるメッシュデータを使用して、Direct3D デバイスバッファーを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-233">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

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

<span data-ttu-id="2d7d6-234">**注:** 前のスニペットで使用した CreateDirectXBuffer ヘルパー関数については、「Surface Mapping のコードサンプル: SurfaceMesh, GetDataFromIBuffer. h」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-234">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="2d7d6-235">これで、デバイスリソースの作成が完了し、メッシュが読み込まれ、更新とレンダリングの準備が整っていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-235">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="2d7d6-236">サーフェイスメッシュの更新とレンダリング</span><span class="sxs-lookup"><span data-stu-id="2d7d6-236">Update and render surface meshes</span></span>

<span data-ttu-id="2d7d6-237">SurfaceMesh クラスには、特殊な更新関数があります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-237">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="2d7d6-238">各 [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) には独自の変換があり、このサンプルでは、 **SpatialStationaryReferenceFrame** の現在の座標系を使用して変換を取得します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-238">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="2d7d6-239">次に、GPU のモデル定数バッファーを更新します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-239">Then it updates the model constant buffer on the GPU.</span></span>

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

<span data-ttu-id="2d7d6-240">サーフェイスメッシュをレンダリングする時間があれば、コレクションをレンダリングする前にいくつかの準備作業を行います。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-240">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="2d7d6-241">現在の表示構成にシェーダーパイプラインを設定し、入力アセンブラーステージを設定します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-241">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="2d7d6-242">Holographic カメラヘルパークラス **CameraResources** は、既にビュー/プロジェクション定数バッファーを設定しています。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-242">The holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="2d7d6-243">**RealtimeSurfaceMeshRenderer:: Render** から:</span><span class="sxs-lookup"><span data-stu-id="2d7d6-243">From **RealtimeSurfaceMeshRenderer::Render**:</span></span>

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

<span data-ttu-id="2d7d6-244">この処理が完了したら、メッシュをループし、それぞれを描画するように指示します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-244">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="2d7d6-245">**注:** このサンプルコードは、任意の種類の視錐カリングを使用するように最適化されていませんが、アプリにこの機能を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-245">**NOTE:** This sample code isn't optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

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

<span data-ttu-id="2d7d6-246">個々のメッシュは、頂点とインデックスバッファー、ストライド、およびモデル変換の定数バッファーを設定します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-246">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="2d7d6-247">Windows Holographic アプリテンプレートの回転するキューブと同様に、インスタンス化を使用してステレオスコピックバッファーにレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-247">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="2d7d6-248">From **SurfaceMesh::D raw**:</span><span class="sxs-lookup"><span data-stu-id="2d7d6-248">From **SurfaceMesh::Draw**:</span></span>

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

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="2d7d6-249">サーフェイスマッピングでの選択肢の表示</span><span class="sxs-lookup"><span data-stu-id="2d7d6-249">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="2d7d6-250">Surface Mapping のコードサンプルでは、表面メッシュデータのオクルーリングのみのレンダリング、および表面メッシュデータの画面表示のためのコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-250">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="2d7d6-251">どちらのパスを選択するか、または両方とも、アプリケーションによって異なります。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-251">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="2d7d6-252">このドキュメントでは、両方の構成について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-252">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="2d7d6-253">**Holographic effect のオクルージョンバッファーのレンダリング**</span><span class="sxs-lookup"><span data-stu-id="2d7d6-253">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="2d7d6-254">まず、現在の仮想カメラのレンダーターゲットビューをクリアします。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-254">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="2d7d6-255">AppMain .cpp から:</span><span class="sxs-lookup"><span data-stu-id="2d7d6-255">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="2d7d6-256">これは "事前レンダリング" パスです。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-256">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="2d7d6-257">ここでは、メッシュレンダラーに深度だけを表示するように求めることによって、オクルージョンバッファーを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-257">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="2d7d6-258">この構成ではレンダーターゲットビューをアタッチせず、メッシュレンダラーはピクセルシェーダーステージを **nullptr** に設定して、GPU がピクセルを描画しないようにします。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-258">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="2d7d6-259">ジオメトリが深度バッファーにラスタライズされ、グラフィックスパイプラインがそこで停止します。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-259">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

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

<span data-ttu-id="2d7d6-260">Surface マッピングのオクルーバッファーに対する追加の深度テストを使用して、ホログラムを描画できます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-260">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="2d7d6-261">このコードサンプルでは、画面の背後にある場合は、キューブのピクセルが異なる色で表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-261">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="2d7d6-262">AppMain .cpp から:</span><span class="sxs-lookup"><span data-stu-id="2d7d6-262">From AppMain.cpp:</span></span>

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

<span data-ttu-id="2d7d6-263">SpecialEffectPixelShader のコードに基づいて次のようにします。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-263">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

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

<span data-ttu-id="2d7d6-264">**注:\*\*\*\*GatherDepthLess** ルーチンについては、「Surface Mapping のコードサンプル: SpecialEffectPixelShader」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-264">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="2d7d6-265">**画面にサーフェイスメッシュデータをレンダリングする**</span><span class="sxs-lookup"><span data-stu-id="2d7d6-265">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="2d7d6-266">また、表面メッシュをステレオディスプレイバッファーに描画するだけでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-266">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="2d7d6-267">全面を照明付きで描画することを選択しましたが、ワイヤーフレームの描画、レンダリング前のメッシュの処理、テクスチャマップの適用などを自由に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-267">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="2d7d6-268">ここでは、このコードサンプルでは、コレクションを描画するようにメッシュレンダラーに指示しています。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-268">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="2d7d6-269">ここでは、深度のみのパスを指定していません。ピクセルシェーダーをアタッチし、現在の仮想カメラに指定したターゲットを使用してレンダリングパイプラインを完成させます。</span><span class="sxs-lookup"><span data-stu-id="2d7d6-269">This time we don't specify a depth-only pass, it'll attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2d7d6-270">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d7d6-270">See also</span></span>
* [<span data-ttu-id="2d7d6-271">ホログラフィック DirectX プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="2d7d6-271">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="2d7d6-272">Windows... 空間 API</span><span class="sxs-lookup"><span data-stu-id="2d7d6-272">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
