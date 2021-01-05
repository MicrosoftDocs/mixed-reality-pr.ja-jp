---
title: 手とモーション コントローラー
description: ハンズオンとモーションコントローラーの相互作用モデルについて説明します。これにより、仮想と物理の間の境界が削除されます。
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 混合現実、ハンズオン、モーションコントローラー、相互作用、設計、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 1dffdd5f3471993dfdb5e504e4c5b87ec0bfef7d
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847323"
---
# <a name="hands-and-motion-controllers"></a><span data-ttu-id="78789-104">手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="78789-104">Hands and motion controllers</span></span>

## <a name="scenarios"></a><span data-ttu-id="78789-105">シナリオ</span><span class="sxs-lookup"><span data-stu-id="78789-105">Scenarios</span></span>

<span data-ttu-id="78789-106">[相互作用の概要](interaction-fundamentals.md)を読み終えたら、ハンドアンドモーションコントローラーの相互作用モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="78789-106">After reading the [interaction overview](interaction-fundamentals.md), you choose the hand and motion controller interaction model.</span></span> <span data-ttu-id="78789-107">これは、ユーザーが holographic 世界と対話するために2人のユーザーを使用する必要があるアプリケーションを開発していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="78789-107">This means you're developing an application requiring users to use two hands to interact with the holographic world.</span></span> <span data-ttu-id="78789-108">アプリケーションは、仮想と物理の間の境界を削除するという目標を達成します。</span><span class="sxs-lookup"><span data-stu-id="78789-108">Your application is going to achieve the goal of removing the boundary between virtual and physical.</span></span>

<span data-ttu-id="78789-109">次のようなシナリオが考えられます。</span><span class="sxs-lookup"><span data-stu-id="78789-109">Some specific scenarios might be:</span></span>
* <span data-ttu-id="78789-110">コンテンツを表示および制御する UI アフォーダンスを使用してインフォメーション ワーカーに 2D 仮想画面を提供する</span><span class="sxs-lookup"><span data-stu-id="78789-110">Providing information workers 2D virtual screens with UI affordances to display and control content</span></span>
* <span data-ttu-id="78789-111">ファクトリアセンブリラインのためのファーストラインワーカーのチュートリアルとガイドの提供</span><span class="sxs-lookup"><span data-stu-id="78789-111">Providing first line workers tutorials and guides for factory assembly lines</span></span>
* <span data-ttu-id="78789-112">医療プロフェッショナルを支援および教育するためのプロフェッショナルなツールを開発する</span><span class="sxs-lookup"><span data-stu-id="78789-112">Developing professional tools for assisting and educating medical professionals</span></span>  
* <span data-ttu-id="78789-113">3D 仮想オブジェクトを使用して実世界を装飾する、または第 2 の世界を創造する</span><span class="sxs-lookup"><span data-stu-id="78789-113">Using 3D virtual objects to decorate the real world or to create a second world</span></span> 
* <span data-ttu-id="78789-114">現実世界を背景として使用して、場所ベースのサービスとゲームを作成する</span><span class="sxs-lookup"><span data-stu-id="78789-114">Creating location-based services and games using the real world as a background</span></span>

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a><span data-ttu-id="78789-115">ハンドアンドモーションコントローラー感覚様相</span><span class="sxs-lookup"><span data-stu-id="78789-115">Hands and motion controllers modalities</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="78789-116">[![手による直接操作](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span><span class="sxs-lookup"><span data-stu-id="78789-116">[![Direct manipulation with hands](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)</span></span><br>
       ### <a name="direct-manipulation-with-handsbr"></a>[<span data-ttu-id="78789-117">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="78789-117">Direct manipulation with hands</span></span>](direct-manipulation.md)<br>
       <span data-ttu-id="78789-118">ユーザーがホログラムにタッチしたり操作したりするために使用できるハンドパワーを適用しています。</span><span class="sxs-lookup"><span data-stu-id="78789-118">Modality applying the power of hands that users can use to touch and manipulate holograms.</span></span> <span data-ttu-id="78789-119">日常の生活エクスペリエンスを使用し、適切な視覚的 affordances を提供することで、ユーザーは、実際のオブジェクトを操作するのと同じ方法を使用して仮想マシンと対話できます。</span><span class="sxs-lookup"><span data-stu-id="78789-119">By using daily life experiences and providing proper visual affordances, users can use the same way of manipulating real world objects to interact with virtual ones.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78789-120">[![手によるポイントとコミット](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="78789-120">[![Point and commit with hands](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)</span></span><br>
        ### <a name="point-and-commit-with-handsbr"></a>[<span data-ttu-id="78789-121">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="78789-121">Point and commit with hands</span></span>](point-and-commit.md)<br>
        <span data-ttu-id="78789-122">このモダリティによって、ユーザーは距離内でホログラムを操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="78789-122">This modality empowers users to interact with holograms in a distance.</span></span> <span data-ttu-id="78789-123">これにより、ユーザーは周囲を最大限に活用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="78789-123">It enables users to make the best use of surroundings.</span></span> <span data-ttu-id="78789-124">ユーザーは、ホログラムを任意の場所に配置し、どこからでもアクセスすることができます。</span><span class="sxs-lookup"><span data-stu-id="78789-124">Users can place holograms anywhere and still access them from any distance.</span></span> <span data-ttu-id="78789-125">2D および3D ホログラムの制御と操作を行うためのメンタルモデルとジェスチャは、直接操作のものと非常に同期されています。</span><span class="sxs-lookup"><span data-stu-id="78789-125">The mental models and gestures for controlling and manipulating 2D and 3D holograms are highly in sync with those of direct manipulation.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="78789-126">[![モーション コントローラー](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="78789-126">[![Motion controllers](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)</span></span><br>
       ### <a name="motion-controllersbr"></a>[<span data-ttu-id="78789-127">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="78789-127">Motion controllers</span></span>](motion-controllers.md)<br>
       <span data-ttu-id="78789-128">モーションコントローラーは、ユーザーの物理的な機能を拡張して、ある程度の距離にわたって正確な対話を行い、一方または両方を使用します。</span><span class="sxs-lookup"><span data-stu-id="78789-128">Motion controllers extend the user's physical capabilities with precise interactions across a range of distances while using one or both hands.</span></span> <span data-ttu-id="78789-129">これらのハードウェアアクセサリは、一般的に使用される多くの対話へのショートカットを提供し、さまざまなアクションに対して footed、tactile フィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="78789-129">These hardware accessories provide shortcuts to many commonly used interactions and provide sure-footed, tactile feedback for various actions.</span></span> <span data-ttu-id="78789-130">現在、モーションコントローラーは、Windows Mixed Reality (WMR) シナリオでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="78789-130">Currently, motion controllers are only available for Windows Mixed Reality (WMR) scenarios.</span></span> 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="78789-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="78789-131">See also</span></span>
* [<span data-ttu-id="78789-132">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="78789-132">Head-gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="78789-133">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="78789-133">Head-gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="78789-134">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="78789-134">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="78789-135">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="78789-135">Point and commit with hands</span></span>](point-and-commit.md)
* [<span data-ttu-id="78789-136">ハンズフリー</span><span class="sxs-lookup"><span data-stu-id="78789-136">Hands-free</span></span>](hands-free.md)
