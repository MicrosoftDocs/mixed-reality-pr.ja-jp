---
title: DirectX での共有された空間アンカー
description: 空間アンカーを共有することで、2つの HoloLens デバイスを同期する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, 同期, 空間アンカー, 転送, マルチプレイヤー, ビュー, シナリオ, チュートリアル, サンプルコード, Azure, Azure 空間アンカー, ASA
ms.openlocfilehash: 4e41975a18c28cb2228b20ebb5d3a445774cca44
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530325"
---
# <a name="shared-experiences-in-directx"></a><span data-ttu-id="8cf56-104">DirectX での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="8cf56-104">Shared experiences in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="8cf56-105">この記事は、従来の WinRT ネイティブ Api に関連しています。</span><span class="sxs-lookup"><span data-stu-id="8cf56-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="8cf56-106">新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](../native/openxr-getting-started.md)** を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8cf56-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)**.</span></span>

<span data-ttu-id="8cf56-107">共有エクスペリエンスとは、1つの HoloLens、iOS、または Android デバイスを持つ複数のユーザーが、同じホログラムをまとめて表示し、対話することです。</span><span class="sxs-lookup"><span data-stu-id="8cf56-107">A shared experience is one where multiple users with their own HoloLens, iOS, or Android device, collectively view and interact with the same hologram.</span></span> <span data-ttu-id="8cf56-108">ホログラムは空間アンカー共有を使用して、空間の固定ポイントに配置されます。</span><span class="sxs-lookup"><span data-stu-id="8cf56-108">The hologram is positioned at a fixed point in space using spatial anchor sharing.</span></span>

## <a name="azure-spatial-anchors"></a><span data-ttu-id="8cf56-109">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="8cf56-109">Azure Spatial Anchors</span></span>

<span data-ttu-id="8cf56-110"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、持続性のあるクラウドベースの空間アンカーを作成できます。これにより、アプリは複数の HoloLens、IOS、Android デバイスで検索できます。</span><span class="sxs-lookup"><span data-stu-id="8cf56-110">You can use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> to create durable cloud-backed spatial anchors, which your app can then locate across multiple HoloLens, iOS and Android devices.</span></span>  <span data-ttu-id="8cf56-111">複数のデバイスで共通の空間アンカーを共有することにより、各ユーザーは、同じ物理的な場所でそのアンカーを基準としてレンダリングされたコンテンツを表示できます。</span><span class="sxs-lookup"><span data-stu-id="8cf56-111">By sharing a common spatial anchor across multiple devices, each user can see content rendered relative to that anchor in the same physical location.</span></span>  <span data-ttu-id="8cf56-112">これにより、リアルタイム共有エクスペリエンスを実現できます。</span><span class="sxs-lookup"><span data-stu-id="8cf56-112">This allows for real-time shared experiences.</span></span>

<span data-ttu-id="8cf56-113"><a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、HoloLens、iOS、および Android デバイス間での非同期ホログラム永続化を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="8cf56-113">You can also use <a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure Spatial Anchors</a> for asynchronous hologram persistence across HoloLens, iOS, and Android devices.</span></span>  <span data-ttu-id="8cf56-114">持続性のあるクラウド空間アンカーを共有することにより、複数のデバイスが同時に存在しない場合でも、同じ永続化されたホログラムを時間の経過とともに観察できます。</span><span class="sxs-lookup"><span data-stu-id="8cf56-114">By sharing a durable cloud spatial anchor, multiple devices can observe the same persisted hologram over time, even if those devices aren't present together at the same time.</span></span>

<span data-ttu-id="8cf56-115">HoloLens アプリでの共有エクスペリエンスの構築を開始するには、5分間の <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空間アンカー HoloLens クイックスタート</a>をお試しください。</span><span class="sxs-lookup"><span data-stu-id="8cf56-115">To get started building shared experiences in your HoloLens app, try out the 5-minute <a href="https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure Spatial Anchors HoloLens quickstart</a>.</span></span>

<span data-ttu-id="8cf56-116">Azure 空間アンカーを使用して実行すると、 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens でアンカーを作成して検索</a>できます。</span><span class="sxs-lookup"><span data-stu-id="8cf56-116">Once you're up and running with Azure Spatial Anchors, you can then <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">create and locate anchors on HoloLens</a>.</span></span>  <span data-ttu-id="8cf56-117">チュートリアルは <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android と iOS</a> でも使用できます。これにより、すべてのデバイスで同じアンカーを共有できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8cf56-117">Walkthroughs are available for <a href="https://docs.microsoft.com/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android and iOS</a> as well, enabling you to share the same anchors on all devices.</span></span>

## <a name="local-anchor-transfers"></a><span data-ttu-id="8cf56-118">ローカルアンカー転送</span><span class="sxs-lookup"><span data-stu-id="8cf56-118">Local anchor transfers</span></span>

<span data-ttu-id="8cf56-119">Azure 空間アンカーを使用できない場合、 [ローカルアンカー転送](../../out-of-scope/local-anchor-transfers-in-directx.md) を使用すると、1つの hololens デバイスで2つ目の hololens デバイスによってインポートされるアンカーをエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="8cf56-119">In situations where you can't use Azure Spatial Anchors, [local anchor transfers](../../out-of-scope/local-anchor-transfers-in-directx.md) enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>  <span data-ttu-id="8cf56-120">このアプローチでは、Azure 空間アンカーよりも堅牢なアンカーの再呼び出しが可能であり、iOS デバイスと Android デバイスはこの方法ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8cf56-120">This approach provides less robust anchor recall than Azure Spatial Anchors, and iOS and Android devices are not supported by this approach.</span></span>

## <a name="see-also"></a><span data-ttu-id="8cf56-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="8cf56-121">See also</span></span>
* [<span data-ttu-id="8cf56-122">複合現実での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="8cf56-122">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
* <span data-ttu-id="8cf56-123"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span><span class="sxs-lookup"><span data-stu-id="8cf56-123"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a></span></span>
* <span data-ttu-id="8cf56-124"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">HoloLens 用 Azure 空間アンカー SDK</a></span><span class="sxs-lookup"><span data-stu-id="8cf56-124"><a href="https://docs.microsoft.com/cpp/api/spatial-anchors/winrt/" target="_blank">Azure Spatial Anchors SDK for HoloLens</a></span></span>