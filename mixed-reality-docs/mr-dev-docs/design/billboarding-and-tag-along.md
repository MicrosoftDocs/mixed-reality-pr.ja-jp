---
title: Billboard と Tag-along
description: Billboarding でオブジェクトを使用する方法について説明します。これらのオブジェクトは常に、混合現実アプリケーションでユーザーを顔にするために使用されます。
author: radicalad
ms.author: adlinv
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、billboarding、タグ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: f0a5c4fc66e287c04fe8fa42c0c671e895a26169
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759408"
---
# <a name="billboarding-and-tag-along"></a><span data-ttu-id="818ea-104">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="818ea-104">Billboarding and tag-along</span></span>

<br>

<img src="images/MRTK_TagAlong.gif" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<br>

## <a name="what-is-billboarding"></a><span data-ttu-id="818ea-105">Billboarding とは</span><span class="sxs-lookup"><span data-stu-id="818ea-105">What is billboarding?</span></span>

<span data-ttu-id="818ea-106">Billboarding は、混合現実のオブジェクトに適用できる動作の概念です。</span><span class="sxs-lookup"><span data-stu-id="818ea-106">Billboarding is a behavioral concept that can be applied to objects in mixed reality.</span></span> <span data-ttu-id="818ea-107">Billboarding を使用するオブジェクトは、常にユーザーに顔を合わせて向きます。</span><span class="sxs-lookup"><span data-stu-id="818ea-107">Objects with billboarding always orient themselves to face the user.</span></span> <span data-ttu-id="818ea-108">テキストおよびメニューシステムは一般的なユースケースであり、ユーザーが移動したときに、ユーザーの環境に配置された静的オブジェクト (ワールドロック) が隠されたり、読み取り不可能になったりします。</span><span class="sxs-lookup"><span data-stu-id="818ea-108">Text and menu systems are common use cases, where static objects placed in the user's environment (world-locked) would be otherwise obscured or unreadable when users move around.</span></span>

<span data-ttu-id="818ea-109">Billboarding が有効になっているオブジェクトは、ユーザーの環境で自由に回転できます。</span><span class="sxs-lookup"><span data-stu-id="818ea-109">Objects with billboarding enabled can rotate freely in the user's environment.</span></span> <span data-ttu-id="818ea-110">また、設計上の考慮事項に応じて、1つの軸に制限することもできます。</span><span class="sxs-lookup"><span data-stu-id="818ea-110">They can also be constrained to a single axis depending on design considerations.</span></span> <span data-ttu-id="818ea-111">Billboarded オブジェクトは、他のオブジェクトに近い場合、または HoloLens でスキャンされたサーフェイスを閉じすぎた場合に、自身をクリップまたは occlude することができます。</span><span class="sxs-lookup"><span data-stu-id="818ea-111">Keep in mind, billboarded objects can clip or occlude themselves when placed too close to other objects, or in HoloLens, too close scanned surfaces.</span></span> <span data-ttu-id="818ea-112">これを回避するには、billboarding に対して有効にした軸で回転したときにオブジェクトが生成する総フットプリントを考えてください。</span><span class="sxs-lookup"><span data-stu-id="818ea-112">To avoid this, think about the total footprint an object may produce when rotated on the axis enabled for billboarding.</span></span>

<br>

---
## <a name="what-is-a-tag-along"></a><span data-ttu-id="818ea-113">タグとは何ですか。</span><span class="sxs-lookup"><span data-stu-id="818ea-113">What is a tag-along?</span></span>

<span data-ttu-id="818ea-114">タグに加えて、ホログラムに追加できる動作の概念です。</span><span class="sxs-lookup"><span data-stu-id="818ea-114">Tag-along is a behavioral concept that can be added to holograms.</span></span> <span data-ttu-id="818ea-115">タグに沿ったオブジェクトは、ユーザーが快適に対話できる範囲内を維持しようとします。</span><span class="sxs-lookup"><span data-stu-id="818ea-115">A tag-along object attempts to stay in a range that allows the user to interact comfortably.</span></span>

<span data-ttu-id="818ea-116">![HoloLens のピンパネルは、タグに沿った動作の優れた例です。](images/tagalong-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="818ea-116">![The HoloLens pins panel is a great example of how tag-along behaves](images/tagalong-1000px.jpg)</span></span><br>
<span data-ttu-id="818ea-117">*HoloLens の [スタート] メニューは、タグに沿った動作の優れた例です。*</span><span class="sxs-lookup"><span data-stu-id="818ea-117">*The HoloLens Start menu is a great example of tag-along behavior*</span></span>

<span data-ttu-id="818ea-118">タグに沿ったオブジェクトにはパラメーターがあり、それらの動作を細かく調整できます。</span><span class="sxs-lookup"><span data-stu-id="818ea-118">Tag-along objects have parameters, which can fine-tune the way they behave.</span></span> <span data-ttu-id="818ea-119">ユーザーが環境を移動している間に、コンテンツをユーザーの目の見えない状態にすることができます。</span><span class="sxs-lookup"><span data-stu-id="818ea-119">Content can be in or out of the user’s line of sight while the user moves around their environment.</span></span> <span data-ttu-id="818ea-120">移動すると、コンテンツは、ビューの端に向かってスライドすることによって、ユーザーの周囲内にとどまります。</span><span class="sxs-lookup"><span data-stu-id="818ea-120">As you move, the content attempts to stay within the user’s periphery by sliding towards the edge of the view.</span></span> <span data-ttu-id="818ea-121">コンテンツは、ユーザーの移動速度に応じて一時的に非表示になることがあります。</span><span class="sxs-lookup"><span data-stu-id="818ea-121">The content might be temporarily out of view depending on how quickly the user is moving.</span></span> <span data-ttu-id="818ea-122">ユーザーがタグに沿って gazes すると、より完全に表示されます。</span><span class="sxs-lookup"><span data-stu-id="818ea-122">When the user gazes towards the tag-along object, it comes more fully into view.</span></span> <span data-ttu-id="818ea-123">コンテンツは常に "一目でわかる" と考えられるので、ユーザーがコンテンツの方向を忘れないようにします。</span><span class="sxs-lookup"><span data-stu-id="818ea-123">Think of content always being "a glance away" so users never forget what direction their content is in.</span></span>

<span data-ttu-id="818ea-124">余分なパラメーターを使用すると、タグに沿ってオブジェクトをラバーバンドでユーザーの頭に接続することができます。</span><span class="sxs-lookup"><span data-stu-id="818ea-124">Extra parameters can make the tag-along object feel attached to the user's head by a rubber band.</span></span> <span data-ttu-id="818ea-125">ダンパーの加速または減速により、オブジェクトに対して重みが与えられ、物理的に存在するようになります。</span><span class="sxs-lookup"><span data-stu-id="818ea-125">Dampening acceleration or deceleration gives weight to the object making it feel more physically present.</span></span> <span data-ttu-id="818ea-126">この spring behavior は、ユーザーがタグを操作する方法の正確なメンタルモデルを作成するのに役立つ affordance です。</span><span class="sxs-lookup"><span data-stu-id="818ea-126">This spring behavior is an affordance that helps the user build an accurate mental model of how tag-along works.</span></span> <span data-ttu-id="818ea-127">オーディオを使用すると、ユーザーがタグに沿ってオブジェクトを持っている場合に、他の手掛かりを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="818ea-127">Audio helps provide other cues for when users have objects in tag-along mode.</span></span> <span data-ttu-id="818ea-128">オーディオは移動速度を強調する必要があります。ファーストヘッドターンではより目立つ音効果が得られますが、自然な速度を調べるには、オーディオの効果を最小限にするか、まったく使用しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="818ea-128">Audio should reinforce the speed of movement; a fast head turn should provide a more noticeable sound effect, while walking at a natural speed should have minimal or no audio effects.</span></span>

<span data-ttu-id="818ea-129">実際にヘッドにロックされたコンテンツと同様に、タグに沿ってオブジェクトを使用すると、ユーザーのビューで非常に大きな動きがあるか、またはばねが非常に大きくなると、非常に多くのことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="818ea-129">Just like truly head-locked content, tag-along objects can prove overwhelming or nauseating if they move wildly or spring too much in the user’s view.</span></span> <span data-ttu-id="818ea-130">ユーザーが見たように、停止したことがわかります。</span><span class="sxs-lookup"><span data-stu-id="818ea-130">As a user looks around, then quickly stops, their senses tell them they've stopped.</span></span> <span data-ttu-id="818ea-131">これらのバランスによって、ヘッドがオフになったことが通知され、その構想によって世界が停止していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="818ea-131">Their balance informs them that their head has stopped turning and their vision sees the world stop turning.</span></span> <span data-ttu-id="818ea-132">ただし、ユーザーが停止したときにタグに沿って移動し続けると、その状態が混乱する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="818ea-132">However, if tag-along keeps on moving when the user has stopped, it may confuse their senses.</span></span>

<br>

---

## <a name="billboarding-and-tag-along-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="818ea-133">Billboarding とタグ-Unity の MRTK (Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="818ea-133">Billboarding and Tag-along in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="818ea-134">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、Billboarding とタグに沿った動作のスクリプトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="818ea-134">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts for the Billboarding and tag-along behavior.</span></span> <span data-ttu-id="818ea-135">Billboard.cs スクリプトを任意のオブジェクトに割り当てて、billboarding の動作を追加し、オブジェクトが常に顔になるようにします。</span><span class="sxs-lookup"><span data-stu-id="818ea-135">Assign the Billboard.cs script onto any object to add billboarding behavior and make the object always face you.</span></span> <span data-ttu-id="818ea-136">タグに沿った動作を追加するには、RadialView.cs スクリプトを使用します。</span><span class="sxs-lookup"><span data-stu-id="818ea-136">To add tag-along behavior, use the RadialView.cs script.</span></span> <span data-ttu-id="818ea-137">Lerping time、distance、次数などのさまざまなオプションを調整できます。</span><span class="sxs-lookup"><span data-stu-id="818ea-137">You can adjust various options such as lerping time, distance, and degree.</span></span>

* [<span data-ttu-id="818ea-138">MRTK-放射状ビューのソルバー</span><span class="sxs-lookup"><span data-stu-id="818ea-138">MRTK - Radial View Solver</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/solvers/solver.md#radialview)
* [<span data-ttu-id="818ea-139">MRTK-ビルボードスクリプト</span><span class="sxs-lookup"><span data-stu-id="818ea-139">MRTK - Billboard script</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Scripts/Utilities/Billboard.cs)


<br>

---

## <a name="see-also"></a><span data-ttu-id="818ea-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="818ea-140">See also</span></span>

* [<span data-ttu-id="818ea-141">カーソル</span><span class="sxs-lookup"><span data-stu-id="818ea-141">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="818ea-142">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="818ea-142">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="818ea-143">ボタン</span><span class="sxs-lookup"><span data-stu-id="818ea-143">Button</span></span>](button.md)
* [<span data-ttu-id="818ea-144">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="818ea-144">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="818ea-145">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="818ea-145">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="818ea-146">操作</span><span class="sxs-lookup"><span data-stu-id="818ea-146">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="818ea-147">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="818ea-147">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="818ea-148">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="818ea-148">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="818ea-149">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="818ea-149">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="818ea-150">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="818ea-150">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="818ea-151">キーボード</span><span class="sxs-lookup"><span data-stu-id="818ea-151">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="818ea-152">ヒント</span><span class="sxs-lookup"><span data-stu-id="818ea-152">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="818ea-153">スレート</span><span class="sxs-lookup"><span data-stu-id="818ea-153">Slate</span></span>](slate.md)
* [<span data-ttu-id="818ea-154">スライダー</span><span class="sxs-lookup"><span data-stu-id="818ea-154">Slider</span></span>](slider.md)
* [<span data-ttu-id="818ea-155">シェーダー</span><span class="sxs-lookup"><span data-stu-id="818ea-155">Shader</span></span>](shader.md)
* [<span data-ttu-id="818ea-156">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="818ea-156">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="818ea-157">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="818ea-157">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="818ea-158">表面吸着</span><span class="sxs-lookup"><span data-stu-id="818ea-158">Surface magnetism</span></span>](surface-magnetism.md)
