---
title: Button
description: ボタンは、特定の操作を直ちに実行する手段をユーザーに提供します。 これは、mixed reality の最も基本的なコンポーネントの1つです。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合現実、コントロール、相互作用、ui、ux、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、ボタン
ms.openlocfilehash: c5e52bef8604ba4874b7f4b055107ec0db6b3683
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702858"
---
# <a name="button"></a><span data-ttu-id="215b4-105">Button</span><span class="sxs-lookup"><span data-stu-id="215b4-105">Button</span></span>

![Button](images/UX_Hero_Button.jpg)

<span data-ttu-id="215b4-107">ボタンは、特定の操作を直ちに実行する手段をユーザーに提供します。</span><span class="sxs-lookup"><span data-stu-id="215b4-107">A button gives the user a way to trigger an immediate action.</span></span> <span data-ttu-id="215b4-108">これは、mixed reality の最も基本的なコンポーネントの1つです。</span><span class="sxs-lookup"><span data-stu-id="215b4-108">It is one of the most foundational components in mixed reality.</span></span> <span data-ttu-id="215b4-109">HoloLens 2 では、ボタンには多くの視覚的な手掛かりと affordances があり、ユーザーの対話操作の信頼性が向上します。</span><span class="sxs-lookup"><span data-stu-id="215b4-109">In HoloLens 2, a button has many visual cues and affordances to increase the user's interaction confidence.</span></span> 


:::row:::
    :::column:::
       <span data-ttu-id="215b4-110">![移動](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="215b4-110">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="215b4-111">**近接光**</span><span class="sxs-lookup"><span data-stu-id="215b4-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="215b4-112">![回転](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="215b4-112">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="215b4-113">**フォーカスの強調表示**</span><span class="sxs-lookup"><span data-stu-id="215b4-113">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="215b4-114">![移動](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="215b4-114">![Move](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="215b4-115">**ケージの圧縮**</span><span class="sxs-lookup"><span data-stu-id="215b4-115">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="215b4-116">![回転](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="215b4-116">![Rotate](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="215b4-117">**トリガーのパルス**</span><span class="sxs-lookup"><span data-stu-id="215b4-117">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>


---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="215b4-118">Unity の MRTK (Mixed Reality Toolkit) のボタン</span><span class="sxs-lookup"><span data-stu-id="215b4-118">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="215b4-119">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、さまざまな種類のボタン prefabs が用意されています。</span><span class="sxs-lookup"><span data-stu-id="215b4-119">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs.</span></span> <span data-ttu-id="215b4-120">HoloLens 2 と HoloLens (第1世代) のシェルスタイルのボタンと、カスタマイズされた例を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="215b4-120">You can find shell-style buttons for HoloLens 2 and HoloLens (1st gen) as well as customized examples.</span></span> <span data-ttu-id="215b4-121">HoloLens 2 ボタン prefab には、ユーザーの信頼を向上させるための詳細な affordances が多数含まれています。</span><span class="sxs-lookup"><span data-stu-id="215b4-121">HoloLens 2 button prefab contains a lot of detailed affordances that help improve the user's confidence.</span></span> <span data-ttu-id="215b4-122">これには、近接度ベースの強調表示、フロントケージの圧縮、トリガーのパルス効果が含まれます。</span><span class="sxs-lookup"><span data-stu-id="215b4-122">It includes proximity-based highlight, compressing front cage, and a pulse effect on trigger.</span></span>

* [<span data-ttu-id="215b4-123">MRTK-ボタン</span><span class="sxs-lookup"><span data-stu-id="215b4-123">MRTK - Button</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)



<br>

---


## <a name="see-also"></a><span data-ttu-id="215b4-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="215b4-124">See also</span></span>

* [<span data-ttu-id="215b4-125">カーソル</span><span class="sxs-lookup"><span data-stu-id="215b4-125">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="215b4-126">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="215b4-126">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="215b4-127">ボタン</span><span class="sxs-lookup"><span data-stu-id="215b4-127">Button</span></span>](button.md)
* [<span data-ttu-id="215b4-128">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="215b4-128">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="215b4-129">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="215b4-129">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="215b4-130">操作</span><span class="sxs-lookup"><span data-stu-id="215b4-130">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="215b4-131">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="215b4-131">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="215b4-132">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="215b4-132">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="215b4-133">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="215b4-133">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="215b4-134">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="215b4-134">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="215b4-135">キーボード</span><span class="sxs-lookup"><span data-stu-id="215b4-135">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="215b4-136">ヒント</span><span class="sxs-lookup"><span data-stu-id="215b4-136">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="215b4-137">スレート</span><span class="sxs-lookup"><span data-stu-id="215b4-137">Slate</span></span>](slate.md)
* [<span data-ttu-id="215b4-138">スライダー</span><span class="sxs-lookup"><span data-stu-id="215b4-138">Slider</span></span>](slider.md)
* [<span data-ttu-id="215b4-139">シェーダー</span><span class="sxs-lookup"><span data-stu-id="215b4-139">Shader</span></span>](shader.md)
* [<span data-ttu-id="215b4-140">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="215b4-140">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="215b4-141">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="215b4-141">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="215b4-142">表面吸着</span><span class="sxs-lookup"><span data-stu-id="215b4-142">Surface magnetism</span></span>](surface-magnetism.md)
