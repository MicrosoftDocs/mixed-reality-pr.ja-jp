---
title: Unreal での空間マッピング
description: Unreal で空間マッピングを使用するためのガイド
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, 空間マッピング, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 878eae5f5fd0b7a1630511faa23c1477455ed988
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354382"
---
# <a name="spatial-mapping-in-unreal"></a><span data-ttu-id="09fc4-104">Unreal での空間マッピング</span><span class="sxs-lookup"><span data-stu-id="09fc4-104">Spatial Mapping in Unreal</span></span>

<span data-ttu-id="09fc4-105">空間マッピングを使用すると、HoloLens の周囲の世界を見せることで、物理的な世界の表面にオブジェクトを配置できるようになります。これにより、ホログラムがユーザーにとってより現実的に見えるようになります。</span><span class="sxs-lookup"><span data-stu-id="09fc4-105">Spatial mapping makes it possible to place objects on surfaces in the physical world by showing the world around the HoloLens, which makes holograms seem more real to the user.</span></span> <span data-ttu-id="09fc4-106">また、空間マッピングでは、実際の奥行きの手掛かりを利用して、ユーザーの世界にオブジェクトを固定します。これにより、これらのホログラムが実際に空間に存在することをユーザーに納得させることができます。空間に浮かんでいるホログラムやユーザーと一緒に動くホログラムは、それほどリアルではありません。</span><span class="sxs-lookup"><span data-stu-id="09fc4-106">Spatial mapping also anchors objects in the user's world by taking advantage of real world depth cues. This helps convince the user that these holograms are actually in their space; holograms floating in space or moving with the user will not feel as real.</span></span> <span data-ttu-id="09fc4-107">できるだけ快適さを追求してアイテムを配置したいと考えています。</span><span class="sxs-lookup"><span data-stu-id="09fc4-107">You want to place items for comfort whenever possible.</span></span>

<span data-ttu-id="09fc4-108">空間マッピングの品質、配置、オクルージョン、レンダリングなどの詳細については、[空間マッピング](../../design/spatial-mapping.md) に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="09fc4-108">You can find more information on spatial mapping quality, placement, occlusion, rendering, and more, in the [Spatial mapping](../../design/spatial-mapping.md) document.</span></span>

## <a name="enabling-spatial-mapping"></a><span data-ttu-id="09fc4-109">空間マッピングの有効化</span><span class="sxs-lookup"><span data-stu-id="09fc4-109">Enabling Spatial Mapping</span></span>

<span data-ttu-id="09fc4-110">HoloLens で空間マッピングを有効にするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="09fc4-110">To enable spatial mapping on HoloLens:</span></span>
- <span data-ttu-id="09fc4-111">**[編集] > [プロジェクトの設定]** を開いて、 **[プラットフォーム]** セクションまで下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="09fc4-111">Open **Edit > Project Settings** and scroll down to the **Platforms** section.</span></span>    
    + <span data-ttu-id="09fc4-112">**[HoloLens]** を選択し、 **[空間認知]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="09fc4-112">Select **HoloLens** and check **Spatial Perception**.</span></span>

![空間認知が強調表示されている HoloLens プロジェクト設定機能のスクリーンショット](images/unreal-spatial-mapping-img-01.png)

<span data-ttu-id="09fc4-114">HoloLens ゲームで空間マッピングをオプトインし、 **[MRMesh]** をデバッグするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="09fc4-114">To opt into spatial mapping and debug the **MRMesh** in a HoloLens game:</span></span>
1. <span data-ttu-id="09fc4-115">**[ARSessionConfig]** を開き、 **[ARSettings] > [ワールド マッピング]** セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="09fc4-115">Open the **ARSessionConfig** and expand the **ARSettings > World Mapping** section.</span></span> 

2. <span data-ttu-id="09fc4-116">**[追跡対象ジオメトリからメッシュ データを生成する]** をオンにします。これにより、空間マッピング データの非同期取得を開始し、**MRMesh** を介して Unreal に表示するように HoloLens プラグインに指示されます。</span><span class="sxs-lookup"><span data-stu-id="09fc4-116">Check **Generate Mesh Data from Tracked Geometry**, which tells the HoloLens plugin to start asynchronously getting spatial mapping data and surface it to Unreal through the **MRMesh**.</span></span> 
3. <span data-ttu-id="09fc4-117">**MRMesh** ですべての三角形の白いワイヤーフレーム アウトラインを表示するには、 **[ワイヤーフレームでメッシュデータをレンダリングする]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="09fc4-117">Check **Render Mesh Data in Wireframe** to show a white wireframe outline of every triangle in the **MRMesh**.</span></span> 

![空間アンカー ストア準備完了](images/unreal-spatialmapping-arsettings.PNG)


## <a name="spatial-mapping-at-runtime"></a><span data-ttu-id="09fc4-119">実行時の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="09fc4-119">Spatial Mapping at runtime</span></span>
<span data-ttu-id="09fc4-120">次のパラメーターを変更して、空間マッピングのランタイム動作を更新できます。</span><span class="sxs-lookup"><span data-stu-id="09fc4-120">You can modify the following parameters to update the spatial mapping runtime behavior:</span></span>

- <span data-ttu-id="09fc4-121">**[編集] > [プロジェクトの設定]** を開き、 **[プラットフォーム]** セクションまで下にスクロールして、 **[HoloLens] > [空間マッピング]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="09fc4-121">Open **Edit > Project Settings**, scroll down to the **Platforms** section and select **HoloLens > Spatial Mapping**:</span></span> 

![空間アンカーのプロジェクト設定](images/unreal-spatialmapping-projectsettings.PNG)

- <span data-ttu-id="09fc4-123">**[Max Triangles Per Cubic Meter]\(立方メートルあたりの最大三角形数\)** で、空間マッピング メッシュの三角形の密度が更新されます。</span><span class="sxs-lookup"><span data-stu-id="09fc4-123">**Max Triangles Per Cubic Meter** updates the density of the triangles in the spatial mapping mesh.</span></span>  
- <span data-ttu-id="09fc4-124">**[Spatial Meshing Volume Size]\(空間メッシュのボリューム サイズ\)** は、空間マッピング データをレンダリングおよび更新するための、プレーヤー周りのキューブのサイズを示します。</span><span class="sxs-lookup"><span data-stu-id="09fc4-124">**Spatial Meshing Volume Size** is the size of the cube around the player to render and update spatial mapping data.</span></span>  
    + <span data-ttu-id="09fc4-125">予想されるアプリケーションの実行時環境が大きくなると思われる場合は、この値を現実世界のスペースに合わせて大きくしなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="09fc4-125">If the expected application runtime environment is expected to be large, this value may need to be large to match the real-world space.</span></span>  <span data-ttu-id="09fc4-126">一方、アプリケーションでユーザーの周囲の表面にホログラムを配置するだけであれば、このフィールドを小さくすることができます。</span><span class="sxs-lookup"><span data-stu-id="09fc4-126">On the other hand, this value can be smaller if the application only needs to place holograms on surfaces immediately around the user.</span></span> <span data-ttu-id="09fc4-127">ユーザーが移動するにつれて、空間マッピングのボリュームも移動します。</span><span class="sxs-lookup"><span data-stu-id="09fc4-127">As the user walks around the world, the spatial mapping volume will move with them.</span></span> 

## <a name="working-with-mrmesh"></a><span data-ttu-id="09fc4-128">MRMesh の操作</span><span class="sxs-lookup"><span data-stu-id="09fc4-128">Working with MRMesh</span></span>

<span data-ttu-id="09fc4-129">最初に、空間マッピングを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="09fc4-129">First, you need to start Spatial Mapping:</span></span>

![空間マッピング キャプチャの種類が強調表示されている ToggleARCapture 関数のブループリント](images/unreal-spatial-mapping-img-02.png)

<span data-ttu-id="09fc4-131">空間の空間マッピングのキャプチャが済んだら、空間マッピングをオフにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="09fc4-131">Once spatial mapping has been captured for the space, we recommend toggling spatial mapping off.</span></span>  <span data-ttu-id="09fc4-132">空間マッピングは、一定の時間が経過した後、または各方向のレイキャストから MRMesh に対する衝突が返されるようになったら、完了できます。</span><span class="sxs-lookup"><span data-stu-id="09fc4-132">The spatial mapping may be completed either after a certain amount of time, or when raycasts in each direction return collisions against the MRMesh.</span></span>

<span data-ttu-id="09fc4-133">実行時に **MRMesh** にアクセスするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="09fc4-133">To get access to the **MRMesh** at runtime:</span></span>
1. <span data-ttu-id="09fc4-134">ブループリント アクターに **ARTrackableNotify** コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="09fc4-134">Add an **ARTrackableNotify** Component to a Blueprint actor.</span></span> 

![空間アンカーの AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="09fc4-136">**ARTrackableNotify** コンポーネントを選択し、 **[詳細]** パネルの **[イベント]** セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="09fc4-136">Select the **ARTrackableNotify** component and expand the **Events** section in the **Details** panel.</span></span> 
    - <span data-ttu-id="09fc4-137">監視するイベントの [ **+** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="09fc4-137">Click the **+** button on the events you want to monitor.</span></span> 

![空間アンカーのイベント](images/unreal-spatialmapping-events.PNG)

<span data-ttu-id="09fc4-139">この場合は、 **[追跡ジオメトリの追加]** イベントが監視され、空間マッピング データに一致する有効なワールド メッシュが検索されます。</span><span class="sxs-lookup"><span data-stu-id="09fc4-139">In this case, the **On Add Tracked Geometry** event is being monitored, which looks for valid world meshes matching to spatial mapping data.</span></span> <span data-ttu-id="09fc4-140">イベントの完全な一覧については、[UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) コンポーネント API を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09fc4-140">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span> 

<span data-ttu-id="09fc4-141">メッシュのマテリアルは、ブループリント イベント グラフまたは C++ で変更できます。</span><span class="sxs-lookup"><span data-stu-id="09fc4-141">You can change the mesh’s material in the Blueprint Event Graph or in C++.</span></span> <span data-ttu-id="09fc4-142">次のスクリーンショットは、ブループリントのルートを示しています。</span><span class="sxs-lookup"><span data-stu-id="09fc4-142">The screenshot below shows the Blueprint route:</span></span> 

![空間アンカーの例](images/unreal-spatialmapping-example.PNG)

## <a name="spatial-mapping-in-c"></a><span data-ttu-id="09fc4-144">C++ での空間マッピング</span><span class="sxs-lookup"><span data-stu-id="09fc4-144">Spatial Mapping in C++</span></span>

<span data-ttu-id="09fc4-145">ゲームの build.cs ファイルで、**AugmentedReality** と **MRMesh** を PublicDependencyModuleNames リストに追加します。</span><span class="sxs-lookup"><span data-stu-id="09fc4-145">In your game's build.cs file, add **AugmentedReality** and **MRMesh** to the PublicDependencyModuleNames list:</span></span>

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",    
        "EyeTracker",
        "AugmentedReality",
        "MRMesh"
});
```

<span data-ttu-id="09fc4-146">MRMesh にアクセスするには、**OnTrackableAdded** デリゲートをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="09fc4-146">To access the MRMesh, subscribe to the **OnTrackableAdded** delegates:</span></span>

```cpp
#include "ARBlueprintLibrary.h"
#include "MRMeshComponent.h"

void AARTrackableMonitor::BeginPlay()
{
    Super::BeginPlay();

    // Subscribe to Tracked Geometry delegates
    UARBlueprintLibrary::AddOnTrackableAddedDelegate_Handle(
        FOnTrackableAddedDelegate::CreateUObject(this, &AARTrackableMonitor::OnTrackableAdded)
    );
}

void AARTrackableMonitor::OnTrackableAdded(UARTrackedGeometry* Added)
{
    // When tracked geometry is received, check that it's from spatial mapping
    if(Added->GetObjectClassification() == EARObjectClassification::World)
    {
        UMRMeshComponent* MRMesh = Added->GetUnderlyingMesh();
    }
}
```

> [!NOTE]
> <span data-ttu-id="09fc4-147">更新および削除イベントにも、それぞれ **AddOnTrackableUpdatedDelegate_Handle** および **AddOnTrackableRemovedDelegate_Handle** という同様のデリゲートがあります。</span><span class="sxs-lookup"><span data-stu-id="09fc4-147">There are similar delegates for updated and removed events, **AddOnTrackableUpdatedDelegate_Handle** and **AddOnTrackableRemovedDelegate_Handle** respectively.</span></span>
>
> <span data-ttu-id="09fc4-148">イベントの完全な一覧については、[UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API を参照してください。</span><span class="sxs-lookup"><span data-stu-id="09fc4-148">You can find the full list of events in the [UARTrackedGeometry](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackedGeometry/index.html) API.</span></span>

## <a name="see-also"></a><span data-ttu-id="09fc4-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="09fc4-149">See also</span></span>
* [<span data-ttu-id="09fc4-150">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="09fc4-150">Spatial mapping</span></span>](../../design/spatial-mapping.md)
