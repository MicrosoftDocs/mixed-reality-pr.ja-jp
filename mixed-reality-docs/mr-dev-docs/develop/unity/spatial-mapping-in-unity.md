---
title: Unity の空間マッピング
description: Unity mixed reality アプリで、実際のジオメトリを使用してレンダリングや衝突を管理する方法について説明します。
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、空間マッピング、レンダラー、collider、メッシュ、スキャン、コンポーネント、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: a713497e0c5f061e9e81bf66197b3e2116218219
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759748"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="71cd5-104">Unity の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="71cd5-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="71cd5-105">[空間マッピング](../../design/spatial-mapping.md) を使用すると、HoloLens デバイスを中心に世界中のサーフェイスを表す三角形のメッシュを取得できます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-105">[spatial mapping](../../design/spatial-mapping.md) lets you retrieve triangle meshes that represent the surfaces in the world around a HoloLens device.</span></span> <span data-ttu-id="71cd5-106">配置、遮蔽、およびルーム分析に surface データを使用して、Unity プロジェクトに immersion の線量を追加できます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-106">You can use surface data for placement, occlusion, and room analysis to give your Unity projects an extra dose of immersion.</span></span>

<span data-ttu-id="71cd5-107">Unity には、次の方法で開発者に公開される空間マッピングの完全なサポートが含まれています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-107">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>
1. <span data-ttu-id="71cd5-108">MixedRealityToolkit で使用可能な空間マッピングコンポーネント。これは、空間マッピングを開始するための便利で迅速なパスを提供します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-108">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="71cd5-109">フルコントロールを提供し、より高度なアプリケーション固有のカスタマイズを可能にする、下位レベルの空間マッピング Api</span><span class="sxs-lookup"><span data-stu-id="71cd5-109">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application-specific customization</span></span>

<span data-ttu-id="71cd5-110">アプリで空間マッピングを使用するには、Package.appxmanifest で spatialPerception 機能を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-110">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="device-support"></a><span data-ttu-id="71cd5-111">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="71cd5-111">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="71cd5-112"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="71cd5-112"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="71cd5-113"><a href="/hololens/hololens1-hardware"><strong>HoloLens (最初の世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="71cd5-113"><a href="/hololens/hololens1-hardware"><strong>HoloLens (first gen)</strong></a></span></span></td>
        <td><span data-ttu-id="71cd5-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="71cd5-114"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="71cd5-115"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="71cd5-115"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="71cd5-116">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="71cd5-116">Spatial mapping</span></span></td>
        <td><span data-ttu-id="71cd5-117">✔️</span><span class="sxs-lookup"><span data-stu-id="71cd5-117">✔️</span></span></td>
        <td><span data-ttu-id="71cd5-118">✔️</span><span class="sxs-lookup"><span data-stu-id="71cd5-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="71cd5-119">SpatialPerception 機能の設定</span><span class="sxs-lookup"><span data-stu-id="71cd5-119">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="71cd5-120">アプリで空間マッピングデータを使用するためには、SpatialPerception 機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-120">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="71cd5-121">SpatialPerception 機能を有効にする方法:</span><span class="sxs-lookup"><span data-stu-id="71cd5-121">How to enable the SpatialPerception capability:</span></span>
1. <span data-ttu-id="71cd5-122">Unity エディターで、 **[プレーヤーの設定** ] ウィンドウを開きます (> プロジェクトの設定を編集し > player)</span><span class="sxs-lookup"><span data-stu-id="71cd5-122">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="71cd5-123">[ **Windows ストア** ] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-123">Select on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="71cd5-124">[**発行の設定]** を展開し、 **[機能]** ボックスの一覧の **"SpatialPerception"** 機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-124">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

> [!NOTE]
> <span data-ttu-id="71cd5-125">Unity プロジェクトを Visual Studio ソリューションに既にエクスポートしている場合は、新しいフォルダーにエクスポートするか、 [Visual studio の package.appxmanifest でこの機能](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)を手動で設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-125">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="71cd5-126">空間マッピングでは、少なくとも10.0.10586.0 の MaxVersionTested が必要です。</span><span class="sxs-lookup"><span data-stu-id="71cd5-126">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>
1. <span data-ttu-id="71cd5-127">Visual Studio のソリューションエクスプローラーで package.appxmanifest を右クリックし、[**コードの表示**] を選択し **ます。**</span><span class="sxs-lookup"><span data-stu-id="71cd5-127">In Visual Studio, right-click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="71cd5-128">**TargetDeviceFamily** を指定する行を探し、 **maxversiontested = ""** を **maxversiontested 済み = "10.0.10586.0"** に変更します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-128">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="71cd5-129">Package.appxmanifest を **保存** します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-129">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="71cd5-130">Unity の組み込みの空間マッピングコンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="71cd5-130">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="71cd5-131">Unity には、アプリに空間マッピングを簡単に追加するためのコンポーネントとして、 **空間マッピングレンダラー** と **空間マッピング Collider** の2つのコンポーネントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-131">Unity offers two components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="71cd5-132">空間マッピングレンダラー</span><span class="sxs-lookup"><span data-stu-id="71cd5-132">Spatial Mapping Renderer</span></span>

<span data-ttu-id="71cd5-133">空間マッピングレンダラーを使用すると、空間マッピングメッシュを視覚化できます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-133">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Unity の空間マッピングレンダラー](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="71cd5-135">空間マッピング Collider</span><span class="sxs-lookup"><span data-stu-id="71cd5-135">Spatial Mapping Collider</span></span>

<span data-ttu-id="71cd5-136">空間マッピングの Collider を使用すると、領域マッピングメッシュを使用して、物理などの holographic コンテンツ (または文字) の操作を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-136">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Unity の空間マッピング Collider](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="71cd5-138">組み込みの空間マッピングコンポーネントの使用</span><span class="sxs-lookup"><span data-stu-id="71cd5-138">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="71cd5-139">物理サーフェスを視覚化して操作する場合は、両方のコンポーネントをアプリに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-139">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="71cd5-140">Unity アプリでこれらの2つのコンポーネントを使用するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-140">To use these two components in your Unity app:</span></span>
1. <span data-ttu-id="71cd5-141">空間サーフェスメッシュを検出する領域の中央にある [ユーザー] オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-141">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="71cd5-142">[インスペクター] ウィンドウで、**コンポーネント**  >  **XR**  >  **空間マッピング Collider** または **空間マッピングレンダラー** を追加します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-142">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="71cd5-143">これらのコンポーネントの使用方法の詳細については、 <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity ドキュメントサイト</a>を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71cd5-143">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="71cd5-144">組み込みの空間マッピングコンポーネント以外に</span><span class="sxs-lookup"><span data-stu-id="71cd5-144">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="71cd5-145">これらのコンポーネントを使用すると、空間マッピングを簡単に開始できるように、ドラッグアンドドロップ操作を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-145">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span>  <span data-ttu-id="71cd5-146">詳細に進むには、次の2つの主要なパスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="71cd5-146">When you want to go further, there are two main paths to explore:</span></span>
* <span data-ttu-id="71cd5-147">独自の下位レベルのメッシュ処理を行うには、以下の「低レベルの空間マッピングスクリプト API について」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="71cd5-147">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="71cd5-148">上位レベルのメッシュ分析を行うには、 <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>の SpatialUnderstanding ライブラリに関する以下のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="71cd5-148">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="71cd5-149">低レベルの Unity 空間マッピング API の使用</span><span class="sxs-lookup"><span data-stu-id="71cd5-149">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="71cd5-150">空間マッピングレンダラーおよび空間マッピング Collider コンポーネントが提供するよりも制御が必要な場合は、低レベルの空間マッピング Api を使用します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-150">If you need more control than the Spatial Mapping Renderer and Spatial Mapping Collider components offer, use the low-level Spatial Mapping APIs.</span></span>

<span data-ttu-id="71cd5-151">**名前空間:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="71cd5-151">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="71cd5-152">**型**: *SurfaceObserver*、 *SurfaceChange*、 *SurfaceData*、 *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="71cd5-152">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="71cd5-153">以下のセクションでは、空間マッピング Api を使用するアプリケーションの提案されたフローについて説明しました。</span><span class="sxs-lookup"><span data-stu-id="71cd5-153">We've outlined the suggested flow for an application that uses the spatial mapping APIs in the sections below.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="71cd5-154">SurfaceObserver を設定する</span><span class="sxs-lookup"><span data-stu-id="71cd5-154">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="71cd5-155">空間マッピングデータが必要な、アプリケーションで定義された領域の領域ごとに1つの SurfaceObserver オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-155">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

 void Start () {
     surfaceObserver = new SurfaceObserver();
 }
```

<span data-ttu-id="71cd5-156">SetVolumeAsSphere、SetVolumeAsAxisAlignedBox、SetVolumeAsOrientedBox、または Setvolumeassphere を呼び出すことによって、各 SurfaceObserver オブジェクトがデータを提供する領域を指定します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-156">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="71cd5-157">これらのメソッドのいずれかを再度呼び出すだけで、後で領域の領域を再定義することができます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-157">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
void Start () {
    ...
     surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="71cd5-158">SurfaceObserver () を呼び出す場合は、空間マッピングシステムに新しい情報が格納されている SurfaceObserver の領域領域の各空間サーフェスに対して、ハンドラーを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-158">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="71cd5-159">このハンドラーは、1つの空間サーフェスに対してを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-159">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
 {
    //see Handling Surface Changes
 }
```

### <a name="handling-surface-changes"></a><span data-ttu-id="71cd5-160">サーフェイスの変更の処理</span><span class="sxs-lookup"><span data-stu-id="71cd5-160">Handling Surface Changes</span></span>

<span data-ttu-id="71cd5-161">処理される主なケースがいくつかあります。これは、同じコードパスを使用したり、削除したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-161">There are several main cases to handle - added and updated, which can use the same code path, and removed.</span></span>
* <span data-ttu-id="71cd5-162">追加および更新されたケースでは、このメッシュを表す SurfaceData オブジェクトをディクショナリから追加または取得し、必要なコンポーネントを含む構造体を作成します。次に、RequestMeshDataAsync を呼び出して、シーン内のメッシュデータと位置を設定します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-162">In the added and updated cases, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="71cd5-163">削除された場合は、このメッシュを表すオブジェクトをディクショナリから削除し、破棄します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-163">In the removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects = 
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

   private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
   {
       switch (changeType)
       {
           case SurfaceChange.Added:
           case SurfaceChange.Updated:
               if (!spatialMeshObjects.ContainsKey(surfaceId))
               {
                   spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                   spatialMeshObjects[surfaceId].transform.parent = this.transform;
                   spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
               }
               GameObject target = spatialMeshObjects[surfaceId];
               SurfaceData sd = new SurfaceData(
                   //the surface id returned from the system
                   surfaceId,
                   //the mesh filter that is populated with the spatial mapping data for this mesh
                   target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                   //the world anchor used to position the spatial mapping mesh in the world
                   target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                   //the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                   target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                   //triangles per cubic meter requested for this mesh
                   1000,
                   //bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                   true
                   );

               SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
               break;
           case SurfaceChange.Removed:
               var obj = spatialMeshObjects[surfaceId];
               spatialMeshObjects.Remove(surfaceId);
               if (obj != null)
               {
                   GameObject.Destroy(obj);
               }
               break;
           default:
               break;
       }
   }
```

### <a name="handling-data-ready"></a><span data-ttu-id="71cd5-164">データの準備完了</span><span class="sxs-lookup"><span data-stu-id="71cd5-164">Handling Data Ready</span></span>

<span data-ttu-id="71cd5-165">OnDataReady ハンドラーは、SurfaceData オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-165">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="71cd5-166">WorldAnchor、MeshFilter、および (必要に応じて) MeshCollider オブジェクトには、関連付けられている空間サーフェスの最新の状態が反映されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-166">The WorldAnchor, MeshFilter, and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="71cd5-167">必要に応じて、MeshFilter オブジェクトのメッシュメンバーにアクセスして、メッシュデータを分析および [処理](../../design/spatial-mapping.md#mesh-processing) します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-167">Optionally, analyze and/or [process](../../design/spatial-mapping.md#mesh-processing) the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="71cd5-168">最新のメッシュを使用して空間サーフェスをレンダリングし、必要に応じて物理衝突と raycasts に使用します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-168">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="71cd5-169">SurfaceData の内容が null でないことを確認することが重要です。</span><span class="sxs-lookup"><span data-stu-id="71cd5-169">It's important to confirm that the contents of the SurfaceData aren't null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="71cd5-170">更新の処理を開始します</span><span class="sxs-lookup"><span data-stu-id="71cd5-170">Start processing on updates</span></span>

<span data-ttu-id="71cd5-171">SurfaceObserver () は、すべてのフレームではなく、遅延時に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-171">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start () {
    ...
     StartCoroutine(UpdateLoop());
}

 IEnumerator UpdateLoop()
    {
        var wait = new WaitForSeconds(2.5f);
        while(true)
        {
            surfaceObserver.Update(OnSurfaceChanged);
            yield return wait;
        }
    }
```

## <a name="higher-level-mesh-analysis-spatialunderstanding"></a><span data-ttu-id="71cd5-172">高レベルのメッシュ分析: SpatialUnderstanding</span><span class="sxs-lookup"><span data-stu-id="71cd5-172">Higher-level mesh analysis: SpatialUnderstanding</span></span>

<span data-ttu-id="71cd5-173"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a>は、Unity の holographic api 上に構築された holographic 開発用のユーティリティコードのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="71cd5-173">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of utility code for holographic development built on Unity's holographic APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="71cd5-174">空間の理解</span><span class="sxs-lookup"><span data-stu-id="71cd5-174">Spatial Understanding</span></span>

<span data-ttu-id="71cd5-175">ホログラムを物理的な世界に配置する場合、多くの場合、空間マッピングのメッシュとサーフェス平面を超えることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="71cd5-175">When placing holograms in the physical world, it's often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="71cd5-176">Procedurally の配置が完了したら、より高いレベルの環境を理解することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="71cd5-176">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="71cd5-177">これには通常、floor、天井、および壁面の決定を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-177">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="71cd5-178">また、配置の制約のセットに対して最適化を行い、holographic オブジェクトに最適な物理的な場所を決定することもできます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-178">You also have the ability to optimize against a set of placement constraints to determine the most best physical locations for holographic objects.</span></span>

<span data-ttu-id="71cd5-179">この問題は、若い Conker とフラグメントの開発中に、部屋のソルバーを開発することによって発生します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-179">During development of Young Conker and Fragments, Asobo Studios faced this problem head on by developing a room solver.</span></span> <span data-ttu-id="71cd5-180">これらの各ゲームにはゲーム固有のニーズがありましたが、中心的な空間認識テクノロジを共有しています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-180">Each of these games had game-specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="71cd5-181">HoloToolkit ライブラリは、このテクノロジをカプセル化しています。これにより、壁上の空のスペースをすばやく検索したり、オブジェクトを天井に配置したり、文字の位置を識別したり、その他の多くの空間を理解したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-181">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="71cd5-182">すべてのソースコードが含まれているので、ニーズに合わせてカスタマイズし、その機能強化をコミュニティと共有することができます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-182">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="71cd5-183">C++ ソルバーのコードは、UWP dll にラップされ、MixedRealityToolkit 内に含まれている drop in prefab を使用して Unity に公開されています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-183">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="71cd5-184">モジュールについて</span><span class="sxs-lookup"><span data-stu-id="71cd5-184">Understanding Modules</span></span>

<span data-ttu-id="71cd5-185">モジュールによって公開される3つの主要なインターフェイスとして、単純な surface と空間クエリのトポロジ、オブジェクト検出のための構造、およびオブジェクトセットの制約ベースの配置に対するオブジェクト配置ソルバーがあります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-185">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint-based placement of object sets.</span></span> <span data-ttu-id="71cd5-186">以下で、これらのそれぞれについて説明します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-186">Each of these is described below.</span></span> <span data-ttu-id="71cd5-187">3つの主要なモジュールインターフェイスに加えて、射線のキャストインターフェイスを使用してタグ付きサーフェス型を取得し、カスタムの watertight playspace メッシュをコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-187">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="71cd5-188">射線のキャスト</span><span class="sxs-lookup"><span data-stu-id="71cd5-188">Ray Casting</span></span>

<span data-ttu-id="71cd5-189">部屋のスキャンが完了すると、床、天井、壁面などの表面にラベルが内部的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-189">After the room scan is completed, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="71cd5-190">"PlayRaycastResult Eraycast" 関数は、射線を受け取り、光線が既知の表面と競合している場合は、その表面に関する情報を "" の形式で返します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-190">The “PlayspaceRaycast” function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a “RaycastResult”.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology, 
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and 
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface, 
                    //  but vertical surface that looks like a 
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown 
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="71cd5-191">内部的には、raycast は、playspace の計算済みの 8 cm キューブ voxel 表現に対して計算されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-191">Internally, the raycast is computed against the computed 8-cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="71cd5-192">各 voxel には、処理されたトポロジデータを含む surface 要素のセットが含まれています (「」)。</span><span class="sxs-lookup"><span data-stu-id="71cd5-192">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="71cd5-193">交差する voxel セルに含まれているが比較され、トポロジ情報を検索するために使用される最適な一致が比較されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-193">The surfels contained within the intersected voxel cell is compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="71cd5-194">このトポロジデータには、"SurfaceTypes" 列挙型の形式で返されるラベルと、交差するサーフェイスの表面領域が含まれます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-194">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="71cd5-195">Unity のサンプルでは、カーソルは各フレームに射線をキャストします。</span><span class="sxs-lookup"><span data-stu-id="71cd5-195">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="71cd5-196">まず、Unity の colliders に対して行います。</span><span class="sxs-lookup"><span data-stu-id="71cd5-196">First, against Unity’s colliders.</span></span> <span data-ttu-id="71cd5-197">2つ目は、モジュールのワールド表現を理解することです。</span><span class="sxs-lookup"><span data-stu-id="71cd5-197">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="71cd5-198">最後に、UI 要素を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-198">And finally, again UI elements.</span></span> <span data-ttu-id="71cd5-199">このアプリケーションでは、UI の優先順位を取得し、結果を理解した後、Unity の colliders を取得します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-199">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="71cd5-200">SurfaceType は、カーソルの横にテキストとして報告されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-200">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="71cd5-201">![Surface の種類がカーソルの横に表示される](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="71cd5-201">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="71cd5-202">*Surface の種類がカーソルの横に表示される*</span><span class="sxs-lookup"><span data-stu-id="71cd5-202">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="71cd5-203">トポロジクエリ</span><span class="sxs-lookup"><span data-stu-id="71cd5-203">Topology Queries</span></span>

<span data-ttu-id="71cd5-204">DLL 内では、トポロジマネージャーは環境のラベル付けを処理します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-204">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="71cd5-205">前述のように、データの大部分は、voxel ボリューム内に含まれる、1つのデータに格納されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-205">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="71cd5-206">さらに、"Playspace 情報" 構造体は、再生スペースに関する情報を格納するために使用されます。これには、ワールドアラインメント (下記の詳細情報)、floor、および天井高さが含まれます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-206">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="71cd5-207">ヒューリスティックは、floor、シーリング、および壁面を決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-207">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="71cd5-208">たとえば、1 ~ m2 の表面領域を持つ最大値と最小値の水平方向の表面は、床と見なされます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-208">For example, the largest and lowest horizontal surface with greater than 1-m2 surface area is considered the floor.</span></span> 

> [!NOTE]
> <span data-ttu-id="71cd5-209">スキャン処理中のカメラパスは、このプロセスでも使用されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-209">The camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="71cd5-210">トポロジマネージャーによって公開されるクエリのサブセットは、dll を通じて公開されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-210">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="71cd5-211">公開されているトポロジクエリは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="71cd5-211">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="71cd5-212">各クエリには、クエリの種類に固有のパラメーターのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-212">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="71cd5-213">次の例では、必要なボリュームの最小の高さ & 幅、床の上の最小配置高さ、およびボリュームの前面にある最小のクリアランスの量をユーザーが指定しています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-213">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="71cd5-214">すべての測定値は、メーターで計算されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-214">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="71cd5-215">これらの各クエリは、"TopologyResult" 構造体の事前に割り当てられた配列を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-215">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="71cd5-216">"LocationCount" パラメーターは、渡された配列の長さを指定します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-216">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="71cd5-217">戻り値は、返された場所の数を報告します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-217">The return value reports the number of returned locations.</span></span> <span data-ttu-id="71cd5-218">この数は、渡された "locationCount" パラメーターよりも大きくありません。</span><span class="sxs-lookup"><span data-stu-id="71cd5-218">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="71cd5-219">"TopologyResult" には、返されたボリュームの中央の位置、フェーシングの方向 (通常は)、および検出された領域のサイズが含まれます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-219">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult 
{ 
    DirectX::XMFLOAT3 position; 
    DirectX::XMFLOAT3 normal; 
    float width; 
    float length;
};
```

> [!NOTE]
> <span data-ttu-id="71cd5-220">Unity のサンプルでは、これらの各クエリは仮想 UI パネルのボタンにリンクされています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-220">In the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="71cd5-221">サンプルでは、これらの各クエリのパラメーターを妥当な値にハードコーディングしています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-221">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="71cd5-222">その他の例については、サンプルコードの SpaceVisualizer.cs を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71cd5-222">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="71cd5-223">クエリのシェイプ</span><span class="sxs-lookup"><span data-stu-id="71cd5-223">Shape Queries</span></span>

<span data-ttu-id="71cd5-224">Dll では、図形アナライザー ("ShapeAnalyzer_W") がトポロジアナライザーを使用して、ユーザーが定義したカスタム図形と照合します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-224">In the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="71cd5-225">Unity のサンプルでは、図形のセットを定義し、[図形] タブ内の [アプリ内クエリ] メニューを使用して結果を表示します。その目的は、ユーザーが独自のオブジェクト図形のクエリを定義し、アプリケーションの必要に応じてそれらを利用できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="71cd5-225">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="71cd5-226">図形の分析は、水平方向のサーフェイスでのみ機能します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-226">The shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="71cd5-227">たとえば、ソファは、平らな座席の表面とソファの上面によって定義されています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-227">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="71cd5-228">Shape クエリでは、特定のサイズ、高さ、および縦横範囲の2つのサーフェスが検索され、2つのサーフェスがアラインされ、接続されています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-228">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="71cd5-229">Api の用語を使用して、ソファ座席と背面は形状コンポーネントであり、アラインメント要件はシェイプコンポーネントの制約です。</span><span class="sxs-lookup"><span data-stu-id="71cd5-229">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="71cd5-230">"Sittable" オブジェクトの Unity サンプル (ShapeDefinition.cs) で定義されているクエリの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-230">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="71cd5-231">各図形クエリは、一連の図形コンポーネントによって定義されます。各図形コンポーネントには、一連のコンポーネント制約と、コンポーネント間の依存関係を示す一連の図形制約があります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-231">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="71cd5-232">この例では、1つのコンポーネント定義に3つの制約が含まれており、コンポーネント間に図形の制約はありません (コンポーネントは1つだけです)。</span><span class="sxs-lookup"><span data-stu-id="71cd5-232">This example includes three constraints in a single component definition and no shape constraints between components (as there's only one component).</span></span>

<span data-ttu-id="71cd5-233">これに対し、ソファ図形には、2つの図形コンポーネントと4つのシェイプ制約があります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-233">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="71cd5-234">コンポーネントは、ユーザーのコンポーネントリスト内のインデックスによって識別されます (この例では0と 1)。</span><span class="sxs-lookup"><span data-stu-id="71cd5-234">Components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="71cd5-235">カスタム図形の定義を簡単に作成するために、Unity モジュールにラッパー関数が用意されています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-235">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="71cd5-236">コンポーネントとシェイプの制約の完全な一覧は、"ShapeComponentConstraint" 構造と "ShapeConstraint" 構造内の "SpatialUnderstandingDll.cs" にあります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-236">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="71cd5-237">![四角形の形状がこの画面にあります](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="71cd5-237">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="71cd5-238">*四角形の形状がこの画面にあります*</span><span class="sxs-lookup"><span data-stu-id="71cd5-238">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="71cd5-239">オブジェクト配置のソルバー</span><span class="sxs-lookup"><span data-stu-id="71cd5-239">Object Placement Solver</span></span>

<span data-ttu-id="71cd5-240">オブジェクト配置のソルバーを使用して、オブジェクトを配置する物理的な部屋内の理想的な場所を識別できます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-240">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="71cd5-241">ソルバーは、オブジェクトのルールと制約を指定して最適な場所を見つけます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-241">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="71cd5-242">また、オブジェクトクエリは、オブジェクトが "Solver_RemoveObject" または "Solver_RemoveAllObjects" の呼び出しで削除されるまで保持され、制約された複数オブジェクトの配置が可能になります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-242">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="71cd5-243">オブジェクト配置クエリは、3つの部分で構成されます。パラメーターを持つ配置の種類、規則の一覧、および制約の一覧です。</span><span class="sxs-lookup"><span data-stu-id="71cd5-243">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="71cd5-244">クエリを実行するには、次の API を使用します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-244">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="71cd5-245">この関数は、オブジェクト名、配置定義、および規則と制約の一覧を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-245">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="71cd5-246">C# ラッパーは、規則と制約の構築を簡単にするための構築ヘルパー関数を提供します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-246">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="71cd5-247">配置定義には、次のいずれかのクエリの種類が含まれます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-247">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
public enum PlacementType
            {
                Place_OnFloor,
                Place_OnWall,
                Place_OnCeiling,
                Place_OnShape,
                Place_OnEdge,
                Place_OnFloorAndCeiling,
                Place_RandomInAir,
                Place_InMidAir,
                Place_UnderFurnitureEdge,
            };
```

<span data-ttu-id="71cd5-248">各配置型には、型に固有のパラメーターのセットがあります。</span><span class="sxs-lookup"><span data-stu-id="71cd5-248">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="71cd5-249">"ObjectPlacementDefinition" 構造体には、これらの定義を作成するための静的ヘルパー関数のセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-249">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="71cd5-250">たとえば、床にオブジェクトを配置する場所を見つけるには、次の関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-250">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="71cd5-251">public static Objectplacement Ementdefinition Create_OnFloor (Vector3 半 Dims) 配置の種類に加えて、一連のルールと制約を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-251">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="71cd5-252">規則に違反することはありません。</span><span class="sxs-lookup"><span data-stu-id="71cd5-252">Rules cannot be violated.</span></span> <span data-ttu-id="71cd5-253">型とルールを満たす配置場所は、最適な配置場所を選択するために、一連の制約に対して最適化されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-253">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="71cd5-254">各ルールと制約は、指定された静的作成関数によって作成できます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-254">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="71cd5-255">ルールと制約の構築関数の例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-255">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="71cd5-256">次のオブジェクト配置クエリは、表面の端に半分のメーターキューブを配置する場所を探しています。これは、以前に配置された他のオブジェクトから、部屋の中心付近に向かっています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-256">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
List<ObjectPlacementRule> rules = 
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints = 
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f), 
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="71cd5-257">成功した場合は、配置位置、次元、および向きを含む "Objectplacement Ementresult" 構造体が返されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-257">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions, and orientation is returned.</span></span> <span data-ttu-id="71cd5-258">また、配置は、配置されたオブジェクトの dll の内部リストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-258">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="71cd5-259">後続の配置クエリでは、このオブジェクトが考慮されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-259">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="71cd5-260">Unity サンプルの "LevelSolver.cs" ファイルには、クエリの例が多数含まれています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-260">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="71cd5-261">![オブジェクトの配置の結果](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="71cd5-261">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="71cd5-262">*図 3: 青色のボックスを使用して、カメラの位置ルールから離れた場所にあるフロアクエリの結果を確認する*</span><span class="sxs-lookup"><span data-stu-id="71cd5-262">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="71cd5-263">レベルまたはアプリケーションのシナリオで必要とされる複数のオブジェクトの配置場所を解決する場合、は、領域が見つかる確率を最大化するために、最初に不可欠なオブジェクトとラージオブジェクトを解決します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-263">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="71cd5-264">配置順序は重要です。</span><span class="sxs-lookup"><span data-stu-id="71cd5-264">Placement order is important.</span></span> <span data-ttu-id="71cd5-265">オブジェクトの配置が見つからない場合は、制限の少ない構成を試してください。</span><span class="sxs-lookup"><span data-stu-id="71cd5-265">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="71cd5-266">一連のフォールバック構成を設定することは、多くの部屋構成で機能をサポートするために不可欠です。</span><span class="sxs-lookup"><span data-stu-id="71cd5-266">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="71cd5-267">ルームスキャンプロセス</span><span class="sxs-lookup"><span data-stu-id="71cd5-267">Room Scanning Process</span></span>

<span data-ttu-id="71cd5-268">HoloLens によって提供される空間マッピングソリューションは、問題のある領域全体のニーズに対応できるように設計されていますが、空間認識モジュールは、2つの特定のゲームのニーズをサポートするように構築されています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-268">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="71cd5-269">このソリューションは、次に示すように、特定のプロセスと想定のセットに基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-269">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process – 
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace. 
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="71cd5-270">ユーザー駆動型の playspace "描画" –スキャンフェーズ中に、ユーザーは再生速度を移動して見て、含まれる必要がある領域を効果的に描画します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-270">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas, which should be included.</span></span> <span data-ttu-id="71cd5-271">生成されたメッシュは、このフェーズでユーザーからのフィードバックを提供するために重要です。</span><span class="sxs-lookup"><span data-stu-id="71cd5-271">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="71cd5-272">屋内で home または office セットアップ–クエリ関数は、フラットなサーフェイスと壁面を中心に設計されています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-272">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="71cd5-273">これは、ソフトな制限です。</span><span class="sxs-lookup"><span data-stu-id="71cd5-273">This is a soft limitation.</span></span> <span data-ttu-id="71cd5-274">ただし、スキャンフェーズでは、主要軸と補助軸に沿ってメッシュテセレーションを最適化するために、主軸分析が完了します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-274">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="71cd5-275">含まれている SpatialUnderstanding.cs ファイルは、スキャンフェーズプロセスを管理します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-275">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="71cd5-276">次の関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-276">It calls the following functions.</span></span>

```
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan – 
    Called each frame to update the scanning process. The camera position and 
    orientation is passed in and is used for the playspace painting process, 
    described above.

GeneratePlayspace_RequestFinish – 
    Called to finalize the playspace. This will use the areas “painted” during 
    the scan phase to define and lock the playspace. The application can query 
    statistics during the scanning phase as well as query the custom mesh for 
    providing user feedback.

Import_UnderstandingMesh – 
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by 
    the module and placed on the understanding prefab will periodically query the 
    custom mesh generated by the process. In addition, this is done once more 
    after scanning has been finalized.
```

<span data-ttu-id="71cd5-277">"SpatialUnderstanding" 動作によって実行されるスキャンフローは、InitScan を呼び出し、その後、各フレームに対してアップデートを実行します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-277">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="71cd5-278">統計クエリによって適切なカバレッジが報告されると、ユーザーは、ユーザーが RequestFinish を呼び出して、スキャンフェーズの終了を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-278">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="71cd5-279">戻り値が dll の処理を完了したことを示すまで、アップデートを引き続き呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-279">UpdateScan continues to be called until its return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="71cd5-280">メッシュについて</span><span class="sxs-lookup"><span data-stu-id="71cd5-280">Understanding Mesh</span></span>

<span data-ttu-id="71cd5-281">Dll を理解することで、内部的には、playspace を 8 cm サイズの voxel キューブのグリッドとして格納します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-281">The understanding dll internally stores the playspace as a grid of 8 cm sized voxel cubes.</span></span> <span data-ttu-id="71cd5-282">スキャンの初期部分では、主要なコンポーネント分析が完了して、部屋の軸が決定されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-282">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="71cd5-283">内部的には、これらの軸に合わせて voxel 領域を格納します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-283">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="71cd5-284">メッシュは、voxel ボリュームから isosurface を抽出することによって、約1秒ごとに生成されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-284">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span> 

<span data-ttu-id="71cd5-285">![Voxel ボリュームから生成されたメッシュを生成しました](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="71cd5-285">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="71cd5-286">*Voxel ボリュームから生成されたメッシュを生成しました*</span><span class="sxs-lookup"><span data-stu-id="71cd5-286">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="71cd5-287">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="71cd5-287">Troubleshooting</span></span>
* <span data-ttu-id="71cd5-288">[SpatialPerception](#setting-the-spatialperception-capability)機能が設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-288">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="71cd5-289">追跡が失われると、次の OnSurfaceChanged イベントによってすべてのメッシュが削除されます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-289">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="71cd5-290">混合 Reality ツールキットでの空間マッピング</span><span class="sxs-lookup"><span data-stu-id="71cd5-290">Spatial Mapping in Mixed Reality Toolkit</span></span>
<span data-ttu-id="71cd5-291">混合 Reality Toolkit v2 での空間マッピングの使用の詳細については、MRTK ドキュメントの「 <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">空間認識」セクション</a> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71cd5-291">For more information on using Spatial Mapping with Mixed Reality Toolkit v2, see the <a href="https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/spatial-awareness/spatial-awareness-getting-started.md" target="_blank">Spatial Awareness section</a> of the MRTK docs.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="71cd5-292">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="71cd5-292">Next Development Checkpoint</span></span>

<span data-ttu-id="71cd5-293">Unity の開発に関する体験に従っている場合は、MRTK コアのビルディングブロックを調べています。</span><span class="sxs-lookup"><span data-stu-id="71cd5-293">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="71cd5-294">ここから、次の構成要素を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-294">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> <span data-ttu-id="71cd5-295">[[テキスト]](text-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="71cd5-295">[Text](text-in-unity.md)</span></span>

<span data-ttu-id="71cd5-296">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="71cd5-296">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="71cd5-297">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="71cd5-297">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="71cd5-298">いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="71cd5-298">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="71cd5-299">関連項目</span><span class="sxs-lookup"><span data-stu-id="71cd5-299">See also</span></span>
* [<span data-ttu-id="71cd5-300">座標系</span><span class="sxs-lookup"><span data-stu-id="71cd5-300">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="71cd5-301">Unity の座標系</span><span class="sxs-lookup"><span data-stu-id="71cd5-301">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="71cd5-302"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="71cd5-302"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="71cd5-303"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine. MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="71cd5-303"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="71cd5-304"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine. MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="71cd5-304"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="71cd5-305"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine。境界</a></span><span class="sxs-lookup"><span data-stu-id="71cd5-305"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>