---
title: Unity の永続化
description: 永続化を使用すると、ユーザーは必要な場所に個々のホログラムやワークスペースをピン留めし、アプリの多くの使用を想定している場所で後から検索することができます。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、永続化、Unity
ms.openlocfilehash: bb1a9b0544f9325a60c86c7424b7b451b6b4335b
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91690079"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="f5c68-104">Unity の永続化</span><span class="sxs-lookup"><span data-stu-id="f5c68-104">Persistence in Unity</span></span>

<span data-ttu-id="f5c68-105">**名前空間:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="f5c68-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="f5c68-106">**クラス:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="f5c68-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="f5c68-107">WorldAnchorStore は、ホログラムがアプリケーションのインスタンス間で特定の実際の位置に置かれる holographic エクスペリエンスを作成するための鍵です。</span><span class="sxs-lookup"><span data-stu-id="f5c68-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="f5c68-108">これにより、ユーザーは必要に応じて個々のホログラムまたはワークスペースをピン留めし、アプリの多くの使用を想定している場所で後から検索することができます。</span><span class="sxs-lookup"><span data-stu-id="f5c68-108">This lets your users pin individual holograms or a workspace wherever they want it, and then find it later where they expect over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="f5c68-109">セッション間でホログラムを永続化する方法</span><span class="sxs-lookup"><span data-stu-id="f5c68-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="f5c68-110">WorldAnchorStore を使用すると、WorldAnchor の場所をセッション間で永続化することができます。</span><span class="sxs-lookup"><span data-stu-id="f5c68-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="f5c68-111">セッション間でホログラムを永続化するには、特定のワールドアンカーを使用するユーザーオブジェクトを個別に追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5c68-111">To actually persist holograms across sessions, you will need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="f5c68-112">多くの場合、ワールドアンカーを使用して作成オブジェクトのルートを作成し、ローカル位置のオフセットを使用して子のホログラムを固定することが理にかなっています。</span><span class="sxs-lookup"><span data-stu-id="f5c68-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="f5c68-113">以前のセッションからホログラムを読み込むには:</span><span class="sxs-lookup"><span data-stu-id="f5c68-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="f5c68-114">WorldAnchorStore を取得する</span><span class="sxs-lookup"><span data-stu-id="f5c68-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="f5c68-115">ワールドアンカーに関連するアプリデータを読み込んで、ワールドアンカーの id を提供します</span><span class="sxs-lookup"><span data-stu-id="f5c68-115">Load app data relating to the world anchor which gives you the id of the world anchor</span></span>
3. <span data-ttu-id="f5c68-116">Id からワールドアンカーを読み込みます</span><span class="sxs-lookup"><span data-stu-id="f5c68-116">Load a world anchor from its id</span></span>

<span data-ttu-id="f5c68-117">将来のセッションのホログラムを保存するには:</span><span class="sxs-lookup"><span data-stu-id="f5c68-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="f5c68-118">WorldAnchorStore を取得する</span><span class="sxs-lookup"><span data-stu-id="f5c68-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="f5c68-119">Id を指定してワールドアンカーを保存する</span><span class="sxs-lookup"><span data-stu-id="f5c68-119">Save a world anchor specifying an id</span></span>
3. <span data-ttu-id="f5c68-120">Id と共に世界のアンカーに関連するアプリデータを保存する</span><span class="sxs-lookup"><span data-stu-id="f5c68-120">Save app data relating to the world anchor along with an id</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="f5c68-121">WorldAnchorStore を取得する</span><span class="sxs-lookup"><span data-stu-id="f5c68-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="f5c68-122">WorldAnchorStore への参照を保持して、操作を実行する準備ができていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f5c68-122">We will want to keep a reference to the WorldAnchorStore around so we know we are ready to go when we want to perform an operation.</span></span> <span data-ttu-id="f5c68-123">これは非同期呼び出しであるため、起動直後にを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5c68-123">Since this is an async call, potentially as soon as start up, we want to call</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="f5c68-124">この場合、StoreLoaded は、WorldAnchorStore が読み込みを完了したときのハンドラーです。</span><span class="sxs-lookup"><span data-stu-id="f5c68-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="f5c68-125">ここでは、特定のワールドアンカーを保存して読み込むために使用する WorldAnchorStore への参照を取得しました。</span><span class="sxs-lookup"><span data-stu-id="f5c68-125">We now have a reference to the WorldAnchorStore which we will use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="f5c68-126">WorldAnchor の保存</span><span class="sxs-lookup"><span data-stu-id="f5c68-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="f5c68-127">保存するには、保存する内容に名前を付け、保存する前に WorldAnchor に渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5c68-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="f5c68-128">注: 2 つのアンカーを同じ文字列に保存しようとすると失敗します (ストア。保存すると false が返されます)。</span><span class="sxs-lookup"><span data-stu-id="f5c68-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="f5c68-129">新しい保存を保存する前に、前の保存を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5c68-129">You need to Delete the previous save before saving the new one:</span></span>

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a><span data-ttu-id="f5c68-130">WorldAnchor を読み込んでいます</span><span class="sxs-lookup"><span data-stu-id="f5c68-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="f5c68-131">読み込み:</span><span class="sxs-lookup"><span data-stu-id="f5c68-131">And to load:</span></span>

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

<span data-ttu-id="f5c68-132">また、ストアを使用することもできます。Delete () を削除して、以前に保存して保存したアンカーを削除します。以前に保存したデータをすべて削除するには、() をクリアします。</span><span class="sxs-lookup"><span data-stu-id="f5c68-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="f5c68-133">既存のアンカーの列挙</span><span class="sxs-lookup"><span data-stu-id="f5c68-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="f5c68-134">以前に保存されたアンカーを検出するには、GetAllIds を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f5c68-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="f5c68-135">複数のデバイスのホログラムの永続化</span><span class="sxs-lookup"><span data-stu-id="f5c68-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="f5c68-136"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、ローカル WorldAnchor から持続性のあるクラウドアンカーを作成できます。これにより、アプリは複数の HoloLens、iOS、および Android デバイスが同時に存在しない場合でも、そのデバイスを検索できます。</span><span class="sxs-lookup"><span data-stu-id="f5c68-136">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices are not present together at the same time.</span></span>  <span data-ttu-id="f5c68-137">クラウドアンカーは永続的であるため、複数のデバイスが一定期間にわたって、同じ物理的な場所にあるそのアンカーを基準としてレンダリングされたコンテンツを表示できます。</span><span class="sxs-lookup"><span data-stu-id="f5c68-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="f5c68-138">Unity で共有エクスペリエンスの構築を開始するには、5分間の <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間アンカー unity クイックスタート</a>をお試しください。</span><span class="sxs-lookup"><span data-stu-id="f5c68-138">To get started building shared experiences in Unity, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="f5c68-139">Azure 空間アンカーを使用して実行した後は、 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity でアンカーを作成して見つける</a>ことができます。</span><span class="sxs-lookup"><span data-stu-id="f5c68-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="f5c68-140">次回の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="f5c68-140">Next Development Checkpoint</span></span>

<span data-ttu-id="f5c68-141">ここまでに説明した Unity 開発チェックポイントの旅に従っている場合は、Mixed Reality コアの構成要素を調査しています。</span><span class="sxs-lookup"><span data-stu-id="f5c68-141">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="f5c68-142">ここから、次のビルディングブロックに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="f5c68-142">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f5c68-143">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="f5c68-143">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="f5c68-144">または、Mixed Reality プラットフォームの機能と Api に移動します。</span><span class="sxs-lookup"><span data-stu-id="f5c68-144">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f5c68-145">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="f5c68-145">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="f5c68-146">いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks) に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="f5c68-146">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5c68-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5c68-147">See Also</span></span>
* [<span data-ttu-id="f5c68-148">空間アンカーの永続性</span><span class="sxs-lookup"><span data-stu-id="f5c68-148">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="f5c68-149"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="f5c68-149"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="f5c68-150"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空間アンカー SDK for Unity</a></span><span class="sxs-lookup"><span data-stu-id="f5c68-150"><a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>
