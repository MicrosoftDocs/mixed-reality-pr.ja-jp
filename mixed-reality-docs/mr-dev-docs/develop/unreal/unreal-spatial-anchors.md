---
title: Unreal でのローカル空間アンカー
description: Unreal で空間アンカーを使用するためのガイド
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, 空間アンカー
ms.openlocfilehash: d223c451cbbf0fb4e2cc1392394d2fe771ec8069
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91702179"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="000c7-104">Unreal でのローカル空間アンカー</span><span class="sxs-lookup"><span data-stu-id="000c7-104">Local Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="000c7-105">概要</span><span class="sxs-lookup"><span data-stu-id="000c7-105">Overview</span></span>

<span data-ttu-id="000c7-106">空間アンカーは、アプリケーション セッション間で現実世界の空間にホログラムを保存するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="000c7-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="000c7-107">これらは、Unreal では **ARPin** として示され、今後のセッションで読み込まれるように HoloLens のアンカー ストアに保存されます。</span><span class="sxs-lookup"><span data-stu-id="000c7-107">These get surfaced through Unreal as **ARPin** s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> <span data-ttu-id="000c7-108">ローカル アンカーは、インターネット接続がない場合のフォールバックとして理想的です。</span><span class="sxs-lookup"><span data-stu-id="000c7-108">Local anchors are ideal as a fallback when there is no internet connectivity.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="000c7-109">ローカル アンカーはデバイスに格納されますが、Azure 空間アンカーはクラウドに格納されます。</span><span class="sxs-lookup"><span data-stu-id="000c7-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="000c7-110">アンカーを格納するために Azure クラウド サービスを使用することをご検討の場合は、[Azure Spatial Anchors](unreal-azure-spatial-anchors.md) を統合する方法について説明したドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="000c7-110">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="000c7-111">また、ローカル アンカーと Azure のアンカーは、競合することなく同じプロジェクトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="000c7-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="000c7-112">アンカー ストアの確認</span><span class="sxs-lookup"><span data-stu-id="000c7-112">Checking the anchor store</span></span>

<span data-ttu-id="000c7-113">アンカーを保存または読み込む前に、アンカー ストアの準備ができているかどうか確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="000c7-113">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="000c7-114">アンカー ストアの準備が整う前に、いずれかの HoloLens アンカー関数を呼び出すと、失敗します。</span><span class="sxs-lookup"><span data-stu-id="000c7-114">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

![空間アンカー ストア準備完了](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a><span data-ttu-id="000c7-116">アンカーの保存</span><span class="sxs-lookup"><span data-stu-id="000c7-116">Saving anchors</span></span>

<span data-ttu-id="000c7-117">アプリケーションにコンポーネントがあり、それをワールドに固定する必要がある場合は、次のシーケンスを使用してアンカー ストアに保存できます。</span><span class="sxs-lookup"><span data-stu-id="000c7-117">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

![空間アンカーの保存](images/unreal-spatialanchors-save.PNG)

<span data-ttu-id="000c7-119">次のように分類されます。</span><span class="sxs-lookup"><span data-stu-id="000c7-119">Breaking this down:</span></span>
1. <span data-ttu-id="000c7-120">既知の場所でアクターを生成します。</span><span class="sxs-lookup"><span data-stu-id="000c7-120">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="000c7-121">その場所とアクターのクラスに基づく名前を使用して、 **ARPin** を作成します。</span><span class="sxs-lookup"><span data-stu-id="000c7-121">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="000c7-122">アクターを **ARPin** に追加し、そのピンを HoloLens アンカー ストアに保存します。</span><span class="sxs-lookup"><span data-stu-id="000c7-122">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="000c7-123">選択するアンカー名は一意である必要があります。この例では現在のタイムスタンプを使用します。</span><span class="sxs-lookup"><span data-stu-id="000c7-123">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="000c7-124">アンカーがアンカー ストアに正常に保存された場合、HoloLens デバイス ポータルの **[システム] > [Map manager]\(マップ マネージャー\) > [Anchor Files Saved On Device]\(デバイスに保存されたアンカー ファイル\)** でそのアンカーを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="000c7-124">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device** .</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="000c7-125">アンカーの読み込み</span><span class="sxs-lookup"><span data-stu-id="000c7-125">Loading anchors</span></span>

<span data-ttu-id="000c7-126">アプリケーションが起動すると、次のブループリントを使用して、コンポーネントをアンカー位置に復元できます。</span><span class="sxs-lookup"><span data-stu-id="000c7-126">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

![空間アンカーの読み込み](images/unreal-spatialanchors-load.PNG)

<span data-ttu-id="000c7-128">次のように分類されます。</span><span class="sxs-lookup"><span data-stu-id="000c7-128">Breaking this down:</span></span>
1. <span data-ttu-id="000c7-129">アンカー ストア内のすべてのアンカーを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="000c7-129">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="000c7-130">ID でアクターを生成します。</span><span class="sxs-lookup"><span data-stu-id="000c7-130">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="000c7-131">そのアクターをアンカー ストアから **ARPin** にピン留めします。</span><span class="sxs-lookup"><span data-stu-id="000c7-131">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="000c7-132">アンカーは、保存された位置に基づいてワールドにホログラムを再配置する必要があるため、ID に対してアクターを生成することが重要です。</span><span class="sxs-lookup"><span data-stu-id="000c7-132">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="000c7-133">ここで追加した変換によってアンカーにオフセットが追加されます。</span><span class="sxs-lookup"><span data-stu-id="000c7-133">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="000c7-134">アンカーの保存された名前によって異なるアクターを生成できるように、アンカー ID も照会されます。</span><span class="sxs-lookup"><span data-stu-id="000c7-134">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="000c7-135">アンカーの削除</span><span class="sxs-lookup"><span data-stu-id="000c7-135">Removing anchors</span></span> 

<span data-ttu-id="000c7-136">アンカーが終了したら、 **Remove ARPin from WMRAnchor Store** および **Remove All ARPins from WMRAnchor Store** コンポーネントを使用して個々のアンカーまたはアンカー ストア全体を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="000c7-136">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

![空間アンカーの削除](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> <span data-ttu-id="000c7-138">Spatial Anchors はまだベータ版であるため、最新の情報と機能を確認してください。</span><span class="sxs-lookup"><span data-stu-id="000c7-138">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="000c7-139">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="000c7-139">Next Development Checkpoint</span></span>

<span data-ttu-id="000c7-140">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="000c7-140">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="000c7-141">ここから、次の構成要素に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="000c7-141">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="000c7-142">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="000c7-142">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="000c7-143">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="000c7-143">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="000c7-144">HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="000c7-144">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="000c7-145">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="000c7-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="000c7-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="000c7-146">See also</span></span>
* [<span data-ttu-id="000c7-147">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="000c7-147">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="000c7-148">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="000c7-148">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="000c7-149">座標系</span><span class="sxs-lookup"><span data-stu-id="000c7-149">Coordinate systems</span></span>](../../design/coordinate-systems.md)
