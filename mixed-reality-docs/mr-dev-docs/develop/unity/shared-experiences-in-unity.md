---
title: Unity での共有エクスペリエンス
description: Azure 空間アンカーを使用して Unity アプリケーション内の複数のユーザー間で同じホログラムを共有する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共有、アンカー、WorldAnchor、MR 共有250、WorldAnchorTransferBatch、SpatialPerception、Azure、Azure 空間アンカー、ASA、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実ヘッドセット
ms.openlocfilehash: 7762a76e1eaa944f69153b13fb0f380c7dce643e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583368"
---
# <a name="shared-experiences-in-unity"></a><span data-ttu-id="93c97-104">Unity での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="93c97-104">Shared experiences in Unity</span></span>

<span data-ttu-id="93c97-105">共有エクスペリエンスを使用すると、複数のユーザーが独自の HoloLens、iOS、または Android デバイスを使用して、同じホログラムをまとめて表示し、操作できます。</span><span class="sxs-lookup"><span data-stu-id="93c97-105">A shared experience lets multiple users, each with their own HoloLens, iOS or Android device, collectively view and interact with the same hologram.</span></span> <span data-ttu-id="93c97-106">ホログラムは、空間アンカーを共有することにより、空間内の固定ポイントに配置されます。</span><span class="sxs-lookup"><span data-stu-id="93c97-106">Holograms are positioned at a fixed point in space through spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="93c97-107">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="93c97-107">Azure Spatial Anchors</span></span>

<span data-ttu-id="93c97-108"><a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a> は、持続性のあるクラウドベースの空間アンカーを作成します。これにより、アプリは複数の HoloLens、IOS、Android デバイスで検索できます。</span><span class="sxs-lookup"><span data-stu-id="93c97-108"><a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="93c97-109">複数のデバイスで共通の空間アンカーを共有することにより、各ユーザーは、同じ物理的な場所でそのアンカーを基準としてレンダリングされたコンテンツを表示できます。</span><span class="sxs-lookup"><span data-stu-id="93c97-109">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span> 

<span data-ttu-id="93c97-110"><a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、HoloLens、iOS、および Android デバイス間での非同期ホログラム永続化を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="93c97-110">You can also use <a href="/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="93c97-111">持続性のあるクラウド空間アンカーを共有することにより、複数のデバイスが同時に存在しない場合でも、同じ永続化されたホログラムを時間の経過とともに観察できます。</span><span class="sxs-lookup"><span data-stu-id="93c97-111">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="93c97-112">Unity で共有エクスペリエンスの構築を開始するには、5分間の <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間アンカー unity クイックスタート</a>をお試しください。</span><span class="sxs-lookup"><span data-stu-id="93c97-112">To get started building shared experiences in Unity, try out the 5-minute <a href="/azure/spatial-anchors/unity-overview" target="_blank">Azure Spatial Anchors Unity quickstarts</a>.</span></span>

<span data-ttu-id="93c97-113">Azure 空間アンカーを設定したら、 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity でアンカーを作成および検索</a>できます。</span><span class="sxs-lookup"><span data-stu-id="93c97-113">Once Azure Spatial Anchors is set up, you can <a href="/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">create and locate anchors in Unity</a>.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="93c97-114">ローカルアンカー転送</span><span class="sxs-lookup"><span data-stu-id="93c97-114">Local anchor transfers</span></span>

<span data-ttu-id="93c97-115">Azure 空間アンカーを使用できない場合、 [ローカルアンカー転送](../../out-of-scope/local-anchor-transfers-in-unity.md) を使用すると、1つの hololens デバイスでアンカーをエクスポートして、2つ目の hololens がインポートできるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="93c97-115">In situations where you can't use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-unity.md) enable one HoloLens device to export an anchor so that a second HoloLens can import it.</span></span>  <span data-ttu-id="93c97-116">このアプローチは、iOS および Android デバイスではサポートされておらず、Azure 空間アンカーよりも堅牢なアンカーのリコールを提供します。</span><span class="sxs-lookup"><span data-stu-id="93c97-116">This approach is not supported on iOS and Android devices, and provides less robust anchor recall than Azure Spatial Anchors.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="93c97-117">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="93c97-117">Next Development Checkpoint</span></span>

<span data-ttu-id="93c97-118">これまでに説明した Unity 開発の取り組みに従っている場合は、Mixed Reality プラットフォームの機能と Api を試してみることになります。</span><span class="sxs-lookup"><span data-stu-id="93c97-118">If you're following the Unity development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="93c97-119">ここから、次のセクションに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="93c97-119">From here, you can continue to the next section:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="93c97-120">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="93c97-120">Locatable camera</span></span>](locatable-camera-in-unity.md)

<span data-ttu-id="93c97-121">または、デバイスまたはエミュレーターへのアプリの配置操作に直接移動します。</span><span class="sxs-lookup"><span data-stu-id="93c97-121">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="93c97-122">HoloLens または Windows Mixed Reality イマーシブヘッドセットへのデプロイ</span><span class="sxs-lookup"><span data-stu-id="93c97-122">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="93c97-123">いつでも [Unity 開発チェックポイント](unity-development-overview.md#3-advanced-features)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="93c97-123">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="93c97-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="93c97-124">See also</span></span>
* [<span data-ttu-id="93c97-125">複合現実での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="93c97-125">Shared experiences in mixed reality</span></span>](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="93c97-126"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="93c97-126"><a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="93c97-127"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空間アンカー SDK for Unity</a></span><span class="sxs-lookup"><span data-stu-id="93c97-127"><a href="/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure Spatial Anchors SDK for Unity</a></span></span>