---
title: Unreal でのローカル空間アンカー
description: Unreal で空間アンカーを使用するためのガイド
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, 空間アンカー, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: b517b1d89ddf7a35864db45a17336f4493816526
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609633"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="4ed20-104">Unreal でのローカル空間アンカー</span><span class="sxs-lookup"><span data-stu-id="4ed20-104">Local Spatial Anchors in Unreal</span></span>

<span data-ttu-id="4ed20-105">空間アンカーにより、アプリケーション セッション間で現実世界の空間のホログラムが **ARPin** として保存されます。</span><span class="sxs-lookup"><span data-stu-id="4ed20-105">Spatial anchors save holograms in real-world space between application sessions as **ARPin** s.</span></span> <span data-ttu-id="4ed20-106">HoloLens のアンカー ストアに保存された ARPin は、後のセッションで読み込むことができ、インターネット接続がない場合の理想的なフォールバック オプションになります。</span><span class="sxs-lookup"><span data-stu-id="4ed20-106">Once saved in the HoloLens' anchor store, ARPin's can be loaded in future sessions and are an ideal fallback option when there's no internet connectivity.</span></span>

> [!NOTE]
> <span data-ttu-id="4ed20-107">UE 4.25 のアンカー関数は 4.26 では廃止されているので、新しいものに置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ed20-107">Anchor functions from UE 4.25 are obsolete in 4.26 and should be replaced with newer ones.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="4ed20-108">ローカル アンカーはデバイスに格納されますが、Azure 空間アンカーはクラウドに格納されます。</span><span class="sxs-lookup"><span data-stu-id="4ed20-108">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="4ed20-109">アンカーを格納するために Azure クラウド サービスを使用することをご検討の場合は、[Azure Spatial Anchors](unreal-azure-spatial-anchors.md) を統合する方法について説明したドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ed20-109">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="4ed20-110">また、ローカル アンカーと Azure のアンカーは、競合することなく同じプロジェクトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="4ed20-110">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="4ed20-111">アンカー ストアの確認</span><span class="sxs-lookup"><span data-stu-id="4ed20-111">Checking the anchor store</span></span>

<span data-ttu-id="4ed20-112">アンカーを保存または読み込む前に、アンカー ストアの準備ができているかどうか確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ed20-112">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="4ed20-113">アンカー ストアの準備が整う前に、いずれかの HoloLens アンカー関数を呼び出すと、失敗します。</span><span class="sxs-lookup"><span data-stu-id="4ed20-113">Calling any of the HoloLens anchor functions before the anchor store is ready won't succeed.</span></span>  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a><span data-ttu-id="4ed20-114">アンカーの保存</span><span class="sxs-lookup"><span data-stu-id="4ed20-114">Saving anchors</span></span>

<span data-ttu-id="4ed20-115">アプリケーションにコンポーネントがあり、それをワールドに固定する必要がある場合は、次のシーケンスを使用してアンカー ストアに保存できます。</span><span class="sxs-lookup"><span data-stu-id="4ed20-115">Once the application has a component you need to pin to the world, it can be saved to the anchor store with the following sequence:</span></span> 

[!INCLUDE[](includes/tabs-sa-2.md)]

<span data-ttu-id="4ed20-116">次のように分類されます。</span><span class="sxs-lookup"><span data-stu-id="4ed20-116">Breaking this down:</span></span>
1. <span data-ttu-id="4ed20-117">既知の場所でアクターを生成します。</span><span class="sxs-lookup"><span data-stu-id="4ed20-117">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="4ed20-118">その場所とアクターのクラスに基づく名前を使用して、**ARPin** を作成します。</span><span class="sxs-lookup"><span data-stu-id="4ed20-118">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="4ed20-119">アクターを **ARPin** に追加し、そのピンを HoloLens アンカー ストアに保存します。</span><span class="sxs-lookup"><span data-stu-id="4ed20-119">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="4ed20-120">選択するアンカー名は一意である必要があります。この例では現在のタイムスタンプを使用します。</span><span class="sxs-lookup"><span data-stu-id="4ed20-120">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="4ed20-121">アンカーがアンカー ストアに正常に保存された場合、HoloLens デバイス ポータルの **[System]\(システム\) > [Map manager]\(マップ マネージャー\) > [Anchor Files Saved On Device]\(デバイスに保存されたアンカー ファイル\)** でそのアンカーを見ることができます。</span><span class="sxs-lookup"><span data-stu-id="4ed20-121">If the anchor is successfully saved to the anchor store, you can see it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="4ed20-122">アンカーの読み込み</span><span class="sxs-lookup"><span data-stu-id="4ed20-122">Loading anchors</span></span>

<span data-ttu-id="4ed20-123">アプリケーションが起動すると、次のブループリントを使用して、コンポーネントをアンカー位置に復元できます。</span><span class="sxs-lookup"><span data-stu-id="4ed20-123">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

[!INCLUDE[](includes/tabs-sa-3.md)]

<span data-ttu-id="4ed20-124">次のように分類されます。</span><span class="sxs-lookup"><span data-stu-id="4ed20-124">Breaking this down:</span></span>
1. <span data-ttu-id="4ed20-125">アンカー ストア内のすべてのアンカーを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="4ed20-125">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="4ed20-126">ID でアクターを生成します。</span><span class="sxs-lookup"><span data-stu-id="4ed20-126">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="4ed20-127">そのアクターをアンカー ストアから **ARPin** にピン留めします。</span><span class="sxs-lookup"><span data-stu-id="4ed20-127">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="4ed20-128">アンカーは、保存された位置に基づいてワールドにホログラムを再配置する必要があるため、ID に対してアクターを生成することが重要です。</span><span class="sxs-lookup"><span data-stu-id="4ed20-128">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="4ed20-129">ここで追加した変換によってアンカーにオフセットが追加されます。</span><span class="sxs-lookup"><span data-stu-id="4ed20-129">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="4ed20-130">アンカーの保存された名前によって異なるアクターを生成できるように、アンカー ID も照会されます。</span><span class="sxs-lookup"><span data-stu-id="4ed20-130">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="4ed20-131">アンカーの削除</span><span class="sxs-lookup"><span data-stu-id="4ed20-131">Removing anchors</span></span> 

<span data-ttu-id="4ed20-132">アンカーの使用が終了したら、 **[Remove ARPin from WMRAnchor Store]\(WMRAnchor ストアから ARPin を削除する\)** および **[Remove All ARPins from WMRAnchor Store]\(WMRAnchor ストアからすべての ARPin を削除する\)** コンポーネントを使用して、個々のアンカーまたはアンカー ストア全体を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="4ed20-132">When you're done with an anchor, you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> <span data-ttu-id="4ed20-133">Spatial Anchors はまだベータ版であるため、最新の情報と機能を確認してください。</span><span class="sxs-lookup"><span data-stu-id="4ed20-133">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="4ed20-134">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="4ed20-134">Next Development Checkpoint</span></span>

<span data-ttu-id="4ed20-135">用意されている Unreal 開発体験に従っている場合、MRTK コア構成要素を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="4ed20-135">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="4ed20-136">ここから、次の構成要素を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="4ed20-136">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="4ed20-137">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="4ed20-137">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="4ed20-138">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="4ed20-138">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4ed20-139">HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="4ed20-139">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="4ed20-140">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="4ed20-140">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ed20-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ed20-141">See also</span></span>
* [<span data-ttu-id="4ed20-142">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="4ed20-142">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="4ed20-143">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="4ed20-143">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="4ed20-144">座標系</span><span class="sxs-lookup"><span data-stu-id="4ed20-144">Coordinate systems</span></span>](../../design/coordinate-systems.md)
