---
title: シェーダー
description: Mixed Reality Toolkit の標準シェーダーは、ホログラムで使用できるさまざまな種類の視覚効果を提供します。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合現実、コントロール、相互作用、ui、ux、シェーダー、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実ヘッドセット、reality、MRTK、Mixed Reality Toolkit、視覚効果
ms.openlocfilehash: 08701fb48d633f7de75b74b5e44655c3a01fade8
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848246"
---
# <a name="shader"></a><span data-ttu-id="33e30-104">シェーダー</span><span class="sxs-lookup"><span data-stu-id="33e30-104">Shader</span></span>

![シェーダー](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="33e30-106">Holographic オブジェクトは実際の環境の物理的なオブジェクトと混在するため、ユーザーに視覚的な手掛かりを与えることが重要です。</span><span class="sxs-lookup"><span data-stu-id="33e30-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="33e30-107">Mixed Reality Toolkit Standard shader は、ホログラムで使用するさまざまな種類の視覚効果を提供します。</span><span class="sxs-lookup"><span data-stu-id="33e30-107">The Mixed Reality Toolkit Standard shader provides various types of visual effects for use with holograms.</span></span> <span data-ttu-id="33e30-108">シェーディングシステムは、単一の柔軟なシェーダーを使用して、Unity の標準シェーダーに似た視覚エフェクトを実現します。</span><span class="sxs-lookup"><span data-stu-id="33e30-108">The shading system uses a single, flexible shader to achieve visuals similar to Unity's Standard Shader.</span></span> <span data-ttu-id="33e30-109">シェーダーは、 [Fluent デザインシステムの原則](https://www.microsoft.com/design/fluent/#/) を実装し、混合の現実のデバイスでもパフォーマンスを維持します。</span><span class="sxs-lookup"><span data-stu-id="33e30-109">The shader implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/) and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-mixed-reality-toolkit-standard-shader"></a><span data-ttu-id="33e30-110">MRTK (Mixed Reality Toolkit) 標準シェーダーを使用した視覚効果の例</span><span class="sxs-lookup"><span data-stu-id="33e30-110">Examples of visual effects using MRTK (Mixed Reality Toolkit) Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="33e30-111">![移動](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="33e30-111">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="33e30-112">**近接光**</span><span class="sxs-lookup"><span data-stu-id="33e30-112">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="33e30-113">![回転](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="33e30-113">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="33e30-114">**罫線 (細)**</span><span class="sxs-lookup"><span data-stu-id="33e30-114">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="standard-shader-in-mrtk-for-unity"></a><span data-ttu-id="33e30-115">Unity の MRTK の標準シェーダー</span><span class="sxs-lookup"><span data-stu-id="33e30-115">Standard shader in MRTK for Unity</span></span>

* [<span data-ttu-id="33e30-116">MRTK-標準シェーダー</span><span class="sxs-lookup"><span data-stu-id="33e30-116">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

<br>

---

## <a name="see-also"></a><span data-ttu-id="33e30-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="33e30-117">See also</span></span>

* [<span data-ttu-id="33e30-118">カーソル</span><span class="sxs-lookup"><span data-stu-id="33e30-118">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="33e30-119">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="33e30-119">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="33e30-120">ボタン</span><span class="sxs-lookup"><span data-stu-id="33e30-120">Button</span></span>](button.md)
* [<span data-ttu-id="33e30-121">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="33e30-121">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="33e30-122">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="33e30-122">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="33e30-123">操作</span><span class="sxs-lookup"><span data-stu-id="33e30-123">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="33e30-124">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="33e30-124">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="33e30-125">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="33e30-125">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="33e30-126">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="33e30-126">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="33e30-127">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="33e30-127">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="33e30-128">キーボード</span><span class="sxs-lookup"><span data-stu-id="33e30-128">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="33e30-129">ヒント</span><span class="sxs-lookup"><span data-stu-id="33e30-129">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="33e30-130">スレート</span><span class="sxs-lookup"><span data-stu-id="33e30-130">Slate</span></span>](slate.md)
* [<span data-ttu-id="33e30-131">スライダー</span><span class="sxs-lookup"><span data-stu-id="33e30-131">Slider</span></span>](slider.md)
* [<span data-ttu-id="33e30-132">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="33e30-132">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="33e30-133">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="33e30-133">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="33e30-134">表面吸着</span><span class="sxs-lookup"><span data-stu-id="33e30-134">Surface magnetism</span></span>](surface-magnetism.md)
