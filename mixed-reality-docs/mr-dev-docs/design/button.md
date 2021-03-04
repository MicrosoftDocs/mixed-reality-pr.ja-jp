---
title: Button
description: ボタンを使用して即時アクションをトリガーする方法について説明します。ボタンは、mixed reality の基本コンポーネントの1つです。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合現実、コントロール、相互作用、ui、ux、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、ボタン
ms.openlocfilehash: 9e4d0637d8c10c3cd23bd2ee1369fd57137af795
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759428"
---
# <a name="button"></a><span data-ttu-id="4d517-104">Button</span><span class="sxs-lookup"><span data-stu-id="4d517-104">Button</span></span>

![Button](images/UX_Hero_Button.jpg)

<span data-ttu-id="4d517-106">ボタンを使用すると、ユーザーは、mixed reality エクスペリエンスで即時アクションをトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="4d517-106">A button lets your users trigger immediate actions in a mixed reality experience.</span></span> <span data-ttu-id="4d517-107">HoloLens 2 では、ボタンに視覚的な手掛かりと affordances があり、ユーザーとの相互作用の信頼を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="4d517-107">In HoloLens 2, buttons have visual cues and affordances that help increase interaction confidence with users.</span></span> 

:::row:::
    :::column:::
       <span data-ttu-id="4d517-108">![近接光効果が表示されているボタン](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="4d517-108">![Button with proximity light effect shown](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="4d517-109">**近接光**</span><span class="sxs-lookup"><span data-stu-id="4d517-109">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="4d517-110">![フォーカスハイライト効果が表示された状態で選択されたボタン](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="4d517-110">![Button selected with focus highlight effect shown](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="4d517-111">**フォーカスの強調表示**</span><span class="sxs-lookup"><span data-stu-id="4d517-111">**Focus highlight**</span></span><br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       <span data-ttu-id="4d517-112">![圧縮ケージ効果が表示された状態で押されたボタン](images/UX_Button_Affordance_Compression.jpg)</span><span class="sxs-lookup"><span data-stu-id="4d517-112">![Button being pressed with compression cage effect shown](images/UX_Button_Affordance_Compression.jpg)</span></span><br>
       <span data-ttu-id="4d517-113">**ケージの圧縮**</span><span class="sxs-lookup"><span data-stu-id="4d517-113">**Compressing cage**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="4d517-114">![トリガーのパルス効果が表示された状態で押されたボタン](images/UX_Button_Affordance_Pulse.jpg)</span><span class="sxs-lookup"><span data-stu-id="4d517-114">![Button being pressed with trigger pulse effect shown](images/UX_Button_Affordance_Pulse.jpg)</span></span><br>
        <span data-ttu-id="4d517-115">**トリガーのパルス**</span><span class="sxs-lookup"><span data-stu-id="4d517-115">**Pulse on trigger**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a><span data-ttu-id="4d517-116">Unity の MRTK (Mixed Reality Toolkit) のボタン</span><span class="sxs-lookup"><span data-stu-id="4d517-116">Button in MRTK(Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="4d517-117">**[Mrtk For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、hololens 2 および hololens (第1世代) 用のシェルスタイルのボタンを含む、さまざまな種類のボタン prefabs が用意されています。</span><span class="sxs-lookup"><span data-stu-id="4d517-117">**[MRTK for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides various types of button prefabs, including shell-style buttons for HoloLens 2 and HoloLens (1st gen).</span></span> <span data-ttu-id="4d517-118">HoloLens 2 ボタンの prefab には、ユーザーの信頼度の向上に役立ついくつかの詳細な affordances が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4d517-118">The HoloLens 2 button prefab contains several detailed affordances that help improve user confidence:</span></span>

* <span data-ttu-id="4d517-119">近接度に基づく強調表示</span><span class="sxs-lookup"><span data-stu-id="4d517-119">Proximity-based highlight</span></span>
* <span data-ttu-id="4d517-120">フロントケージの圧縮</span><span class="sxs-lookup"><span data-stu-id="4d517-120">Compressing front cage</span></span>
* <span data-ttu-id="4d517-121">トリガーに対するパルス効果。</span><span class="sxs-lookup"><span data-stu-id="4d517-121">Pulse effect on trigger.</span></span>

* <span data-ttu-id="4d517-122">詳細な手順とカスタマイズされた例については、 [Mrtk のボタン](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4d517-122">Check out the [MRTK - Button](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md) for more instructions and customized examples.</span></span>

<br>

---

## <a name="see-also"></a><span data-ttu-id="4d517-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="4d517-123">See also</span></span>

* [<span data-ttu-id="4d517-124">カーソル</span><span class="sxs-lookup"><span data-stu-id="4d517-124">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="4d517-125">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="4d517-125">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="4d517-126">ボタン</span><span class="sxs-lookup"><span data-stu-id="4d517-126">Button</span></span>](button.md)
* [<span data-ttu-id="4d517-127">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="4d517-127">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="4d517-128">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="4d517-128">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="4d517-129">操作</span><span class="sxs-lookup"><span data-stu-id="4d517-129">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4d517-130">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="4d517-130">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="4d517-131">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="4d517-131">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="4d517-132">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="4d517-132">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="4d517-133">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="4d517-133">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="4d517-134">キーボード</span><span class="sxs-lookup"><span data-stu-id="4d517-134">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="4d517-135">ヒント</span><span class="sxs-lookup"><span data-stu-id="4d517-135">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="4d517-136">スレート</span><span class="sxs-lookup"><span data-stu-id="4d517-136">Slate</span></span>](slate.md)
* [<span data-ttu-id="4d517-137">スライダー</span><span class="sxs-lookup"><span data-stu-id="4d517-137">Slider</span></span>](slider.md)
* [<span data-ttu-id="4d517-138">シェーダー</span><span class="sxs-lookup"><span data-stu-id="4d517-138">Shader</span></span>](shader.md)
* [<span data-ttu-id="4d517-139">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="4d517-139">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="4d517-140">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="4d517-140">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="4d517-141">表面吸着</span><span class="sxs-lookup"><span data-stu-id="4d517-141">Surface magnetism</span></span>](surface-magnetism.md)
