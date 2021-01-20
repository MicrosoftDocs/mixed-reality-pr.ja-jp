---
title: Unity の永続化
description: 永続化を使用すると、ユーザーが好きな場所に個々のホログラムをピン留めし、アプリの多くの用途で後から検索することができます。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、永続化、Unity、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実のヘッドセット
ms.openlocfilehash: 7d12764dac2259388fe57d3924165783eab3dac5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583489"
---
# <a name="persistence-in-unity"></a><span data-ttu-id="2e6ce-104">Unity の永続化</span><span class="sxs-lookup"><span data-stu-id="2e6ce-104">Persistence in Unity</span></span>

<span data-ttu-id="2e6ce-105">**名前空間:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="2e6ce-105">**Namespace:** *UnityEngine.XR.WSA.Persistence*</span></span><br>
<span data-ttu-id="2e6ce-106">**クラス:** *WorldAnchorStore*</span><span class="sxs-lookup"><span data-stu-id="2e6ce-106">**Class:** *WorldAnchorStore*</span></span>

<span data-ttu-id="2e6ce-107">WorldAnchorStore は、ホログラムがアプリケーションのインスタンス間で特定の実際の位置に置かれる holographic エクスペリエンスを作成するための鍵です。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-107">The WorldAnchorStore is the key to creating holographic experiences where holograms stay in specific real world positions across instances of the application.</span></span> <span data-ttu-id="2e6ce-108">ユーザーは、必要に応じて個々のホログラムをピン留めし、アプリの多くの用途において、後で同じ場所でそれらを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-108">Users can then pin individual holograms wherever they want, and find them later in the same spot over many uses of your app.</span></span>

## <a name="how-to-persist-holograms-across-sessions"></a><span data-ttu-id="2e6ce-109">セッション間でホログラムを永続化する方法</span><span class="sxs-lookup"><span data-stu-id="2e6ce-109">How to persist holograms across sessions</span></span>

<span data-ttu-id="2e6ce-110">WorldAnchorStore を使用すると、WorldAnchor の場所をセッション間で永続化することができます。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-110">The WorldAnchorStore will allow you to persist the location of WorldAnchor's across sessions.</span></span> <span data-ttu-id="2e6ce-111">セッション間でホログラムを永続化するには、特定のワールドアンカーを使用するユーザーオブジェクトを個別に追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-111">To actually persist holograms across sessions, you'll need to separately keep track of your GameObjects that use a particular world anchor.</span></span> <span data-ttu-id="2e6ce-112">多くの場合、ワールドアンカーを使用して作成オブジェクトのルートを作成し、ローカル位置のオフセットを使用して子のホログラムを固定することが理にかなっています。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-112">It often makes sense to create a GameObject root with a world anchor and have children holograms anchored by it with a local position offset.</span></span>

<span data-ttu-id="2e6ce-113">以前のセッションからホログラムを読み込むには:</span><span class="sxs-lookup"><span data-stu-id="2e6ce-113">To load holograms from previous sessions:</span></span>
1. <span data-ttu-id="2e6ce-114">WorldAnchorStore を取得する</span><span class="sxs-lookup"><span data-stu-id="2e6ce-114">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="2e6ce-115">ワールドアンカーに関連するアプリデータを読み込みます。これにより、ワールドアンカーの ID が提供されます。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-115">Load app data relating to the world anchor, which gives you the ID of the world anchor</span></span>
3. <span data-ttu-id="2e6ce-116">ID からワールドアンカーを読み込みます</span><span class="sxs-lookup"><span data-stu-id="2e6ce-116">Load a world anchor from its ID</span></span>

<span data-ttu-id="2e6ce-117">将来のセッションのホログラムを保存するには:</span><span class="sxs-lookup"><span data-stu-id="2e6ce-117">To save holograms for future sessions:</span></span>
1. <span data-ttu-id="2e6ce-118">WorldAnchorStore を取得する</span><span class="sxs-lookup"><span data-stu-id="2e6ce-118">Get the WorldAnchorStore</span></span>
2. <span data-ttu-id="2e6ce-119">ID を指定してワールドアンカーを保存する</span><span class="sxs-lookup"><span data-stu-id="2e6ce-119">Save a world anchor specifying an ID</span></span>
3. <span data-ttu-id="2e6ce-120">ID と共に世界のアンカーに関連するアプリデータを保存する</span><span class="sxs-lookup"><span data-stu-id="2e6ce-120">Save app data relating to the world anchor along with an ID</span></span>

### <a name="getting-the-worldanchorstore"></a><span data-ttu-id="2e6ce-121">WorldAnchorStore を取得する</span><span class="sxs-lookup"><span data-stu-id="2e6ce-121">Getting the WorldAnchorStore</span></span>

<span data-ttu-id="2e6ce-122">操作を実行する準備ができたことを知らせるために、WorldAnchorStore への参照を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-122">You'll want to keep a reference to the WorldAnchorStore so you know when it's ready to perform an operation.</span></span> <span data-ttu-id="2e6ce-123">これは非同期呼び出しであるため、起動直後にを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-123">Since this is an async call, potentially as soon as start up, you want to call:</span></span>

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

<span data-ttu-id="2e6ce-124">この場合、StoreLoaded は、WorldAnchorStore が読み込みを完了したときのハンドラーです。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-124">StoreLoaded in this case is our handler for when the WorldAnchorStore has completed loading:</span></span>

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

<span data-ttu-id="2e6ce-125">ここでは、特定のワールドアンカーを保存して読み込むために使用する WorldAnchorStore への参照を取得しました。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-125">We now have a reference to the WorldAnchorStore, which we'll use to save and load specific World Anchors.</span></span>

### <a name="saving-a-worldanchor"></a><span data-ttu-id="2e6ce-126">WorldAnchor の保存</span><span class="sxs-lookup"><span data-stu-id="2e6ce-126">Saving a WorldAnchor</span></span>

<span data-ttu-id="2e6ce-127">保存するには、保存する内容に名前を付け、保存する前に WorldAnchor に渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-127">To save, we simply need to name what we are saving and pass it in the WorldAnchor we got before when we want to save.</span></span> <span data-ttu-id="2e6ce-128">注: 2 つのアンカーを同じ文字列に保存しようとすると失敗します (ストア。保存すると false が返されます)。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-128">Note: trying to save two anchors to the same string will fail (store.Save will return false).</span></span> <span data-ttu-id="2e6ce-129">前の保存を削除してから、新しい保存を保存します。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-129">Delete the previous save before saving the new one:</span></span>

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

### <a name="loading-a-worldanchor"></a><span data-ttu-id="2e6ce-130">WorldAnchor を読み込んでいます</span><span class="sxs-lookup"><span data-stu-id="2e6ce-130">Loading a WorldAnchor</span></span>

<span data-ttu-id="2e6ce-131">読み込み:</span><span class="sxs-lookup"><span data-stu-id="2e6ce-131">And to load:</span></span>

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

<span data-ttu-id="2e6ce-132">また、ストアを使用することもできます。Delete () を削除して、以前に保存して保存したアンカーを削除します。以前に保存したデータをすべて削除するには、() をクリアします。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-132">We additionally can use store.Delete() to remove an anchor we previously saved and store.Clear() to remove all previously saved data.</span></span>

### <a name="enumerating-existing-anchors"></a><span data-ttu-id="2e6ce-133">既存のアンカーの列挙</span><span class="sxs-lookup"><span data-stu-id="2e6ce-133">Enumerating Existing Anchors</span></span>

<span data-ttu-id="2e6ce-134">以前に保存されたアンカーを検出するには、GetAllIds を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-134">To discover previously stored anchors, call GetAllIds.</span></span>

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a><span data-ttu-id="2e6ce-135">複数のデバイスのホログラムの永続化</span><span class="sxs-lookup"><span data-stu-id="2e6ce-135">Persisting holograms for multiple devices</span></span>

<span data-ttu-id="2e6ce-136"><a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、ローカル WorldAnchor から持続性のあるクラウドアンカーを作成することができます。これにより、複数の HoloLens、iOS、および Android デバイスが同時に存在しない場合でも、アプリはそれらを検索できます。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-136">You can use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create a durable cloud anchor from a local WorldAnchor, which your app can then locate across multiple HoloLens, iOS and Android devices, even if those devices aren't present together at the same time.</span></span>  <span data-ttu-id="2e6ce-137">クラウドアンカーは永続的であるため、複数のデバイスが一定期間にわたって、同じ物理的な場所にあるそのアンカーを基準としてレンダリングされたコンテンツを表示できます。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-137">Because cloud anchors are persistent, multiple devices over time can each see content rendered relative to that anchor in the same physical location.</span></span>

<span data-ttu-id="2e6ce-138">Unity で共有エクスペリエンスの構築を開始するには、5分間の <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間アンカー unity クイックスタート</a>をお試しください。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-138">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="2e6ce-139">Azure 空間アンカーを使用して実行した後は、 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity でアンカーを作成して見つける</a>ことができます。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-139">Once you're up and running with Azure Spatial Anchors, you can then <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="2e6ce-140">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="2e6ce-140">Next Development Checkpoint</span></span>

<span data-ttu-id="2e6ce-141">ここまでに説明した Unity 開発チェックポイントの旅に従っている場合は、Mixed Reality コアの構成要素を調査しています。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-141">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality core building blocks.</span></span> <span data-ttu-id="2e6ce-142">ここから、次の構成要素を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-142">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e6ce-143">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="2e6ce-143">Spatial mapping</span></span>](spatial-mapping-in-unity.md)

<span data-ttu-id="2e6ce-144">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-144">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e6ce-145">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="2e6ce-145">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="2e6ce-146">いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="2e6ce-146">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="2e6ce-147">参照</span><span class="sxs-lookup"><span data-stu-id="2e6ce-147">See Also</span></span>
* [<span data-ttu-id="2e6ce-148">空間アンカーの永続性</span><span class="sxs-lookup"><span data-stu-id="2e6ce-148">Spatial anchor persistence</span></span>](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <span data-ttu-id="2e6ce-149"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="2e6ce-149"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="2e6ce-150"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空間アンカー SDK for Unity</a></span><span class="sxs-lookup"><span data-stu-id="2e6ce-150"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>