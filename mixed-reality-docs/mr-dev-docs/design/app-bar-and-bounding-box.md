---
title: 境界ボックスとアプリ バー
description: アプリバーは、ホログラムの境界の下端に表示される一連のボタンを含むオブジェクトレベルのメニューです。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality、アプリバー、境界ボックス、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: aba2e318439fec2bbb9e986c2ff7cac7a8a5fb3a
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759438"
---
# <a name="bounding-box-and-app-bar"></a><span data-ttu-id="88d0e-104">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="88d0e-104">Bounding box and App bar</span></span>
<span data-ttu-id="88d0e-105">![境界は、混合現実のオブジェクト操作の標準インターフェイスです。](images/UX_Hero_BoundingBox.jpg)</span><span class="sxs-lookup"><span data-stu-id="88d0e-105">![Bounding is the standard interface for object manipulation in Mixed Reality.](images/UX_Hero_BoundingBox.jpg)</span></span><br>
<br>

## <a name="what-is-the-bounding-box"></a><span data-ttu-id="88d0e-106">境界ボックスとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="88d0e-106">What is the Bounding box?</span></span>

<span data-ttu-id="88d0e-107">境界は、混合現実のオブジェクト操作の標準インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="88d0e-107">Bounding is the standard interface for object manipulation in Mixed Reality.</span></span> <span data-ttu-id="88d0e-108">この機能により、オブジェクトが現在調整可能であることを視覚的に示すことができます。</span><span class="sxs-lookup"><span data-stu-id="88d0e-108">This feature provides the user with a visual cue that the object is currently adjustable.</span></span> <span data-ttu-id="88d0e-109">HoloLens 2 では、境界ボックスはダイレクト操作と連動し、ユーザーの finger's 近接に応答します。</span><span class="sxs-lookup"><span data-stu-id="88d0e-109">On HoloLens 2, the bounding box works with direct hand manipulation and responds to the user's finger's proximity.</span></span> <span data-ttu-id="88d0e-110">これは、ユーザーがオブジェクトからの距離を認識するのに役立つ視覚的フィードバックを示しています。</span><span class="sxs-lookup"><span data-stu-id="88d0e-110">It shows visual feedback to help the user perceive the distance from the object.</span></span>

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a><span data-ttu-id="88d0e-111">オブジェクトのスケーリング</span><span class="sxs-lookup"><span data-stu-id="88d0e-111">Scaling an object</span></span><br>
        <span data-ttu-id="88d0e-112">境界ボックスのコーナーは、オブジェクトを拡張できることをユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="88d0e-112">The corners of the bounding box tell the user that the object can scale.</span></span> <span data-ttu-id="88d0e-113">ハンドルは、スケールを調整するために広く理解されているパターンに従います。</span><span class="sxs-lookup"><span data-stu-id="88d0e-113">The handles follow a widely understood pattern for adjusting scale.</span></span> <span data-ttu-id="88d0e-114">このビジュアルキューは、調整モードの外部では表示されない場合でも、オブジェクトの合計領域をユーザーに表示します。</span><span class="sxs-lookup"><span data-stu-id="88d0e-114">This visual cue shows users the total area of the object – even if it’s not visible outside of an adjustment mode.</span></span> <span data-ttu-id="88d0e-115">この機能がないと、別のオブジェクトまたはサーフェイスにスナップされたオブジェクトは、そこには存在しない領域があるように動作しているように見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="88d0e-115">Without this feature, an object snapped to another object or surface may appear to behave like there was space around it that shouldn’t be there.</span></span><br>
        <br>
        <span data-ttu-id="88d0e-116">*ビデオループ: 境界ボックスを使用したオブジェクトのスケーリング*</span><span class="sxs-lookup"><span data-stu-id="88d0e-116">*Video loop: Scaling an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="88d0e-117">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="88d0e-117">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="88d0e-118">![境界ボックスを使用したオブジェクトのスケーリングの HoloLens ポイント](images/HoloLens2_BoundingBox.gif)</span><span class="sxs-lookup"><span data-stu-id="88d0e-118">![HoloLens point-of-view of scaling an object via bounding box](images/HoloLens2_BoundingBox.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a><span data-ttu-id="88d0e-119">オブジェクトの回転</span><span class="sxs-lookup"><span data-stu-id="88d0e-119">Rotating an object</span></span><br>
        <span data-ttu-id="88d0e-120">境界ボックスの端の垂直四角形 affordances は回転インジケーターです。</span><span class="sxs-lookup"><span data-stu-id="88d0e-120">The vertical rectangular affordances on the edges of the bounding box are rotation indicators.</span></span> <span data-ttu-id="88d0e-121">これにより、ユーザーは、配置されたホログラムをより細かく調整できます。</span><span class="sxs-lookup"><span data-stu-id="88d0e-121">This gives the user more fine adjustment over their placed holograms.</span></span> <span data-ttu-id="88d0e-122">調整と拡大縮小だけでなく、回転も可能になりました。</span><span class="sxs-lookup"><span data-stu-id="88d0e-122">Not only can they adjust and scale, but now rotate as well.</span></span><br>
        <br>
        <span data-ttu-id="88d0e-123">*ビデオループ: 境界ボックスを使用したオブジェクトの回転*</span><span class="sxs-lookup"><span data-stu-id="88d0e-123">*Video loop: Rotating an object via bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="88d0e-124">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="88d0e-124">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="88d0e-125">![境界ボックスを使用してオブジェクトを回転するための HoloLens のポイント](images/HoloLens2_BoundingBox_Rotate.gif)</span><span class="sxs-lookup"><span data-stu-id="88d0e-125">![HoloLens point-of-view of rotating an object via bounding box](images/HoloLens2_BoundingBox_Rotate.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a><span data-ttu-id="88d0e-126">HoloLens 2 での視覚的フィードバック (手動による)</span><span class="sxs-lookup"><span data-stu-id="88d0e-126">Visual feedback on hand proximity on HoloLens 2</span></span><br>
        <span data-ttu-id="88d0e-127">HoloLens 2 では、追加の視覚的な手掛かりがあります。これは、ユーザーが深さを認識するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="88d0e-127">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="88d0e-128">指先がオブジェクトに近づいたときに、指先の近くにあるリングが表示され、スケールダウンされます。</span><span class="sxs-lookup"><span data-stu-id="88d0e-128">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="88d0e-129">このリングは、押された状態に達したときに、最終的にドットに収束します。</span><span class="sxs-lookup"><span data-stu-id="88d0e-129">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="88d0e-130">このビジュアル affordance は、オブジェクトからの距離をユーザーが理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="88d0e-130">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="88d0e-131">*ビデオループ: 境界ボックスとの近接度に基づくビジュアルフィードバックの例*</span><span class="sxs-lookup"><span data-stu-id="88d0e-131">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="88d0e-132">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="88d0e-132">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="88d0e-133">![手書きの視覚的フィードバック](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="88d0e-133">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="88d0e-134">**Unity アプリの開発については、 [Mixed Reality Toolkit の「境界ボックス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)」を参照してください。**</span><span class="sxs-lookup"><span data-stu-id="88d0e-134">**For Unity app development, see [Bounding box in the Mixed Reality Toolkit-Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**</span></span>

<br>

---

## <a name="what-is-the-app-bar"></a><span data-ttu-id="88d0e-135">アプリバーとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="88d0e-135">What is the App bar?</span></span>

<span data-ttu-id="88d0e-136">アプリバーはオブジェクトレベルのメニューであり、ホログラムの境界の下端に表示される一連のボタンが含まれています。</span><span class="sxs-lookup"><span data-stu-id="88d0e-136">The App bar is an object-level menu, which contains a series of buttons displayed on the bottom edge of a hologram's bounds.</span></span> <span data-ttu-id="88d0e-137">このパターンは、ユーザーがホログラムを削除および調整できるようにするためによく使用されます。</span><span class="sxs-lookup"><span data-stu-id="88d0e-137">This pattern is commonly used to let users remove and adjust holograms.</span></span> <span data-ttu-id="88d0e-138">アプリバーは、主にユーザーの環境で配置されたオブジェクトを管理する方法として設計されました。</span><span class="sxs-lookup"><span data-stu-id="88d0e-138">The App bar was designed primarily as a way to manage placed objects in a user's environment.</span></span> <span data-ttu-id="88d0e-139">境界ボックスと組み合わせて使用すると、ユーザーはどこでも、どのようにオブジェクトが混合現実に向いているかを完全に制御できます。</span><span class="sxs-lookup"><span data-stu-id="88d0e-139">Coupled with the bounding box, a user has full control over where and how objects are oriented in mixed reality.</span></span>

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a><span data-ttu-id="88d0e-140">アプリバーはユーザーに従います</span><span class="sxs-lookup"><span data-stu-id="88d0e-140">The App bar follows the user</span></span><br>
        <span data-ttu-id="88d0e-141">このパターンは、世界でロックされているオブジェクトで使用されるため、ユーザーがオブジェクトの周りを移動すると、アプリバーは常にユーザーに最も近いオブジェクトの側に表示されます。</span><span class="sxs-lookup"><span data-stu-id="88d0e-141">Since this pattern is used with objects that are world locked, as a user moves around the object the App bar will always display on the objects' side closest to the user.</span></span> <span data-ttu-id="88d0e-142">技術的には billboarding ではありませんが、この機能は実質的に同じ結果を実現します。</span><span class="sxs-lookup"><span data-stu-id="88d0e-142">While not technically billboarding, this feature effectively achieves the same result.</span></span> <span data-ttu-id="88d0e-143">環境内の別の場所から使用できるようにするために、ユーザーの位置を occlude またはブロックすることを防止します。</span><span class="sxs-lookup"><span data-stu-id="88d0e-143">Preventing a user's position to occlude or block functionality that would otherwise be available from a different location in their environment.</span></span> <br>
        <br>
        <span data-ttu-id="88d0e-144">*ビデオループ: ホログラムの周りをたどると、アプリバーが次のようになります。*</span><span class="sxs-lookup"><span data-stu-id="88d0e-144">*Video loop: Walking around a hologram, the App bar follows*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="88d0e-145">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="88d0e-145">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="88d0e-146">![ホログラムの周りを歩いています。</span><span class="sxs-lookup"><span data-stu-id="88d0e-146">![Walking around a hologram.</span></span> <span data-ttu-id="88d0e-147">アプリバーは次のようになります。](images/HoloLens2_AppBarFollowing.gif)</span><span class="sxs-lookup"><span data-stu-id="88d0e-147">The App bar follows.](images/HoloLens2_AppBarFollowing.gif)</span></span><br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="88d0e-148">Unity 用の MRTK (Mixed Reality Toolkit) の境界ボックス</span><span class="sxs-lookup"><span data-stu-id="88d0e-148">Bounding box in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="88d0e-149">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、境界ボックスとアプリバーのスクリプトと prefabs が用意されています。</span><span class="sxs-lookup"><span data-stu-id="88d0e-149">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and prefabs for the Bounding box and App bar.</span></span> <span data-ttu-id="88d0e-150">境界ボックスを追加するには、BoundingBox.cs スクリプトを任意のオブジェクトに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="88d0e-150">You can add a Bounding box by assigning the BoundingBox.cs script onto any object.</span></span>

* [<span data-ttu-id="88d0e-151">MRTK-境界ボックス</span><span class="sxs-lookup"><span data-stu-id="88d0e-151">MRTK - Bounding Box</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/bounding-box.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="88d0e-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="88d0e-152">See also</span></span>

* [<span data-ttu-id="88d0e-153">カーソル</span><span class="sxs-lookup"><span data-stu-id="88d0e-153">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="88d0e-154">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="88d0e-154">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="88d0e-155">ボタン</span><span class="sxs-lookup"><span data-stu-id="88d0e-155">Button</span></span>](button.md)
* [<span data-ttu-id="88d0e-156">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="88d0e-156">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="88d0e-157">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="88d0e-157">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="88d0e-158">操作</span><span class="sxs-lookup"><span data-stu-id="88d0e-158">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="88d0e-159">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="88d0e-159">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="88d0e-160">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="88d0e-160">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="88d0e-161">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="88d0e-161">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="88d0e-162">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="88d0e-162">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="88d0e-163">キーボード</span><span class="sxs-lookup"><span data-stu-id="88d0e-163">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="88d0e-164">ヒント</span><span class="sxs-lookup"><span data-stu-id="88d0e-164">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="88d0e-165">スレート</span><span class="sxs-lookup"><span data-stu-id="88d0e-165">Slate</span></span>](slate.md)
* [<span data-ttu-id="88d0e-166">スライダー</span><span class="sxs-lookup"><span data-stu-id="88d0e-166">Slider</span></span>](slider.md)
* [<span data-ttu-id="88d0e-167">シェーダー</span><span class="sxs-lookup"><span data-stu-id="88d0e-167">Shader</span></span>](shader.md)
* [<span data-ttu-id="88d0e-168">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="88d0e-168">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="88d0e-169">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="88d0e-169">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="88d0e-170">表面吸着</span><span class="sxs-lookup"><span data-stu-id="88d0e-170">Surface magnetism</span></span>](surface-magnetism.md)
