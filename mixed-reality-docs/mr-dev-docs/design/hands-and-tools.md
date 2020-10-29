---
title: 手とモーション コントローラー
description: ハンズオンとモーションコントローラーの相互作用モデルについて説明します。これにより、仮想と物理の間の境界が削除されます。
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 混合現実、ハンド、モーションコントローラー、相互作用、設計
ms.openlocfilehash: 8b2ed6127708204d0c4a537c56b2225ff26e0d0f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686890"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="5762d-104">手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="5762d-104">Hands and motion controllers</span></span>
## <a name="scenarios"></a><span data-ttu-id="5762d-105">シナリオ</span><span class="sxs-lookup"><span data-stu-id="5762d-105">Scenarios</span></span>
<span data-ttu-id="5762d-106">[相互作用の概要](interaction-fundamentals.md)を読み取った後にこの相互作用モデルを採用することを選択した場合は、ユーザーが holographic 世界と対話するために2人のユーザーを使用する必要があるアプリケーションを開発していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="5762d-106">If you choose to adopt this interaction model after reading the [interaction overview](interaction-fundamentals.md), it means that you are developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="5762d-107">アプリケーションは、仮想と物理の間の境界を削除するという目標を達成します。</span><span class="sxs-lookup"><span data-stu-id="5762d-107">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="5762d-108">次のようなシナリオが考えられます。</span><span class="sxs-lookup"><span data-stu-id="5762d-108">Some specific scenarios might be:</span></span>
* <span data-ttu-id="5762d-109">コンテンツを表示および制御する UI アフォーダンスを使用してインフォメーション ワーカーに 2D 仮想画面を提供する</span><span class="sxs-lookup"><span data-stu-id="5762d-109">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="5762d-110">ファクトリアセンブリラインのためのファーストラインワーカーのチュートリアルとガイドの提供</span><span class="sxs-lookup"><span data-stu-id="5762d-110">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="5762d-111">医療プロフェッショナルを支援および教育するためのプロフェッショナルなツールを開発する</span><span class="sxs-lookup"><span data-stu-id="5762d-111">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="5762d-112">3D 仮想オブジェクトを使用して実世界を装飾する、または第 2 の世界を創造する</span><span class="sxs-lookup"><span data-stu-id="5762d-112">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="5762d-113">現実世界を背景として使用して、場所ベースのサービスとゲームを作成する</span><span class="sxs-lookup"><span data-stu-id="5762d-113">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="5762d-114">ハンドアンドモーションコントローラー感覚様相</span><span class="sxs-lookup"><span data-stu-id="5762d-114">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="5762d-115">[![手による直接操作](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="5762d-115">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="5762d-116">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="5762d-116">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="5762d-117">これは、ユーザーがホログラムを直接操作したり操作したりできるようにするための、手の力を活用したモダリティです。</span><span class="sxs-lookup"><span data-stu-id="5762d-117">This is a modality leveraging the power of hands, with which users are capable of touching and manipulating the holograms directly.</span></span> <span data-ttu-id="5762d-118">日常的な経験を活用し、適切な視覚的 affordances を提供することにより、ユーザーは、実際のオブジェクトを操作するのと同じ方法を使用して仮想マシンとやり取りすることができます。</span><span class="sxs-lookup"><span data-stu-id="5762d-118">By leveraging daily life experiences and providing proper visual affordances, users are able to use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5762d-119">[![手によるポイントとコミット](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="5762d-119">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="5762d-120">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="5762d-120">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="5762d-121">このモダリティによって、ユーザーは距離内でホログラムを操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="5762d-121">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="5762d-122">これにより、ユーザーは周囲を最大限に活用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="5762d-122">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="5762d-123">ユーザーは、ホログラムを任意の場所に配置し、どこからでもアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="5762d-123">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="5762d-124">2D および3D ホログラムの制御と操作を行うためのメンタルモデルとジェスチャは、直接操作のものと非常に同期されています。</span><span class="sxs-lookup"><span data-stu-id="5762d-124">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5762d-125">[![モーション コントローラー](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="5762d-125">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="5762d-126">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="5762d-126">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="5762d-127">モーションコントローラーは、ユーザーの物理的な機能を拡張するツールであり、1つまたは両方のハンズを使用しながら、広範囲の距離にわたる正確な対話を実現します。</span><span class="sxs-lookup"><span data-stu-id="5762d-127">Motion controllers are tools that extend the user's physical capabilities by providing precise interactions across a large range of distances while using one or both hands.</span></span> <span data-ttu-id="5762d-128">これらのハードウェアアクセサリは、一般的に使用される多くの対話にショートカットを提供し、さまざまなアクションに対して tactile のフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="5762d-128">These hardware accessories provide shortcuts to many commonly-used interactions and provide surefooted, tactile feedback for a variety of actions.</span></span> <span data-ttu-id="5762d-129">現在、モーションコントローラーは、Windows Mixed Reality (WMR) シナリオでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="5762d-129">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="5762d-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="5762d-130">See also</span></span>
* [<span data-ttu-id="5762d-131">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="5762d-131">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="5762d-132">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="5762d-132">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="5762d-133">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="5762d-133">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="5762d-134">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="5762d-134">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="5762d-135">ハンズフリー</span><span class="sxs-lookup"><span data-stu-id="5762d-135">Hands-free</span></span>](hands-free.md)
