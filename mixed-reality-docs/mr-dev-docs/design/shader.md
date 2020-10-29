---
title: シェーダー
description: MRTK 標準シェーダーには、ホログラムで使用できるさまざまな種類の視覚効果が用意されています。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: Mixed Reality、コントロール、対話、ui、ux
ms.openlocfilehash: 86e56de93736c90f3b28467a0ecd6e18a1ba0146
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683986"
---
# <a name="shader"></a><span data-ttu-id="29cf5-104">シェーダー</span><span class="sxs-lookup"><span data-stu-id="29cf5-104">Shader</span></span>

![シェーダー](images/UX_Hero_StandardShader.jpg)

<span data-ttu-id="29cf5-106">Holographic オブジェクトは実際の環境の物理的なオブジェクトと混在するため、ユーザーに視覚的な手掛かりを与えることが重要です。</span><span class="sxs-lookup"><span data-stu-id="29cf5-106">Since holographic objects are mixed with physical ones in the real environment, it's important to provide visual cues to the user.</span></span> <span data-ttu-id="29cf5-107">MRTK 標準シェーダーには、ホログラムで使用できるさまざまな種類の視覚効果が用意されています。</span><span class="sxs-lookup"><span data-stu-id="29cf5-107">The MRTK Standard shader provides various types of visual effects that can be used with holograms.</span></span> <span data-ttu-id="29cf5-108">MRTK 標準シェーディングシステムでは、Unity の標準シェーダーに似た視覚エフェクトを実現し、 [Fluent 設計システムの原則](https://www.microsoft.com/design/fluent/#/)を実装し、mixed reality デバイスでパフォーマンスを維持できる、単一の柔軟なシェーダーを利用しています。</span><span class="sxs-lookup"><span data-stu-id="29cf5-108">The MRTK Standard shading system utilizes a single, flexible shader that can achieve visuals similar to Unity's Standard Shader, implements [Fluent Design System principles](https://www.microsoft.com/design/fluent/#/), and remains performant on mixed reality devices.</span></span>
<br>

## <a name="examples-of-visual-effects-using-mrtk-standard-shader"></a><span data-ttu-id="29cf5-109">MRTK Standard shader を使用した視覚効果の例</span><span class="sxs-lookup"><span data-stu-id="29cf5-109">Examples of visual effects using MRTK Standard shader</span></span> 
:::row:::
    :::column:::
       <span data-ttu-id="29cf5-110">![移動](images/UX_Button_Affordance_ProximityLight.jpg)</span><span class="sxs-lookup"><span data-stu-id="29cf5-110">![Move](images/UX_Button_Affordance_ProximityLight.jpg)</span></span><br>
       <span data-ttu-id="29cf5-111">**近接光**</span><span class="sxs-lookup"><span data-stu-id="29cf5-111">**Proximity light**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="29cf5-112">![回転](images/UX_Button_Affordance_FocusHighlight.jpg)</span><span class="sxs-lookup"><span data-stu-id="29cf5-112">![Rotate](images/UX_Button_Affordance_FocusHighlight.jpg)</span></span><br>
        <span data-ttu-id="29cf5-113">**罫線 (細)**</span><span class="sxs-lookup"><span data-stu-id="29cf5-113">**Border light**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="mrtk-standard-shader-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="29cf5-114">MRTK の MRTK Standard shader (Mixed Reality Toolkit) (Unity 用)</span><span class="sxs-lookup"><span data-stu-id="29cf5-114">MRTK Standard shader in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="29cf5-115">MRTK-標準シェーダー</span><span class="sxs-lookup"><span data-stu-id="29cf5-115">MRTK - Standard shader</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="29cf5-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="29cf5-116">See also</span></span>

* [<span data-ttu-id="29cf5-117">カーソル</span><span class="sxs-lookup"><span data-stu-id="29cf5-117">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="29cf5-118">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="29cf5-118">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="29cf5-119">ボタン</span><span class="sxs-lookup"><span data-stu-id="29cf5-119">Button</span></span>](button.md)
* [<span data-ttu-id="29cf5-120">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="29cf5-120">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="29cf5-121">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="29cf5-121">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="29cf5-122">操作</span><span class="sxs-lookup"><span data-stu-id="29cf5-122">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="29cf5-123">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="29cf5-123">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="29cf5-124">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="29cf5-124">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="29cf5-125">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="29cf5-125">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="29cf5-126">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="29cf5-126">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="29cf5-127">キーボード</span><span class="sxs-lookup"><span data-stu-id="29cf5-127">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="29cf5-128">ヒント</span><span class="sxs-lookup"><span data-stu-id="29cf5-128">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="29cf5-129">スレート</span><span class="sxs-lookup"><span data-stu-id="29cf5-129">Slate</span></span>](slate.md)
* [<span data-ttu-id="29cf5-130">スライダー</span><span class="sxs-lookup"><span data-stu-id="29cf5-130">Slider</span></span>](slider.md)
* [<span data-ttu-id="29cf5-131">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="29cf5-131">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="29cf5-132">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="29cf5-132">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="29cf5-133">表面吸着</span><span class="sxs-lookup"><span data-stu-id="29cf5-133">Surface magnetism</span></span>](surface-magnetism.md)
