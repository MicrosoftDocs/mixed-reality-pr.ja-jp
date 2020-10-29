---
title: Holographic display のコンテンツのデザイン
description: Holographic 表示の設計ガイドラインとベストプラクティス
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI デザイン, holographic 表示, コンテンツデザイン, ダークテーマ, ライトテーマ
ms.openlocfilehash: 627ffdd0a413ad3140c29e9b1c7bb69c9dc249cf
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686111"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="e1400-104">Holographic display のコンテンツのデザイン</span><span class="sxs-lookup"><span data-stu-id="e1400-104">Designing content for holographic display</span></span>

![Ulnar side location](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="e1400-106">Holographic が表示されるようにコンテンツを設計する際には、最適なエクスペリエンスを実現するために考慮する必要がある要素がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="e1400-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="e1400-107">ここでは、いくつかの推奨事項の一覧を示し、 [色、光、およびマテリアル](color-light-and-materials.md) のページで holographic 表示の特性について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="e1400-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="e1400-108">大きな表面で明るい色の課題</span><span class="sxs-lookup"><span data-stu-id="e1400-108">Challenges with bright color on a large surface</span></span> 
<span data-ttu-id="e1400-109">さまざまな種類の HoloLens エクスペリエンスに対するユーザー調査とテストに基づいて、ディスプレイの大きな領域で明るい色を使用すると、いくつかの問題が発生する可能性があることがわかりました。</span><span class="sxs-lookup"><span data-stu-id="e1400-109">Based on our user research and testing on various types of HoloLens experiences, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="e1400-110">**目の疲労**</span><span class="sxs-lookup"><span data-stu-id="e1400-110">**Eye fatigue**</span></span> 

<span data-ttu-id="e1400-111">Holographic display は加法であるため、明るい色はより多くの光を使用してホログラムを表示します。</span><span class="sxs-lookup"><span data-stu-id="e1400-111">Since holographic display is additive, bright color uses more light to display holograms.</span></span> <span data-ttu-id="e1400-112">ディスプレイの大きな領域に明るい色を使用すると、ユーザーにとって目の疲労が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="e1400-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="e1400-113">**手動でのオクルージョン**</span><span class="sxs-lookup"><span data-stu-id="e1400-113">**Hand occlusion**</span></span> 

<span data-ttu-id="e1400-114">明るい色を使用すると、オブジェクトを直接操作するときにユーザーが手を見ることが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="e1400-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="e1400-115">ユーザーは人間を見ることができないため、針とターゲットサーフェスの間の深さや距離を認識することは困難になります。</span><span class="sxs-lookup"><span data-stu-id="e1400-115">Since the user cannot see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="e1400-116">指カーソルを使用するとこの問題を補うことができますが、それでも明るい白い面では困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e1400-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="e1400-117">![色とハンドオクルーが ](images/color_handocclusion.jpg)
 *明るい色のコンテンツバックプレートで手を見づらい*</span><span class="sxs-lookup"><span data-stu-id="e1400-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="e1400-118">**色の統一性**</span><span class="sxs-lookup"><span data-stu-id="e1400-118">**Color uniformity**</span></span>

<span data-ttu-id="e1400-119">Holographic 表示の特性により、画面上の大きな明るい領域が blotchy になることがあります。</span><span class="sxs-lookup"><span data-stu-id="e1400-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="e1400-120">ダーク配色を使用すると、この問題を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="e1400-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines"></a><span data-ttu-id="e1400-121">設計ガイドライン</span><span class="sxs-lookup"><span data-stu-id="e1400-121">Design guidelines</span></span>

<span data-ttu-id="e1400-122">**UI の背景に濃い色を使用する**</span><span class="sxs-lookup"><span data-stu-id="e1400-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="e1400-123">ダーク配色を使用することにより、目の疲労を最小化し、直接的なやり取りに対する信頼度を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="e1400-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="e1400-124">![ダーク UI ](images/color_dark_examples.jpg)
 *の例コンテンツの背景に使用される濃い色の例*</span><span class="sxs-lookup"><span data-stu-id="e1400-124">![Dark UI examples](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="e1400-125">**Semibold または太字のフォントの太さを使用する**</span><span class="sxs-lookup"><span data-stu-id="e1400-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="e1400-126">HoloLens を使用すると、美しい高解像度のテキストを表示できます。</span><span class="sxs-lookup"><span data-stu-id="e1400-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="e1400-127">ただし、縦方向のストロークが小さいフォントサイズでジッターになる可能性があるため、光や半光などの細いフォントの重みを使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e1400-127">However, it is recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="e1400-128">![濃い UI ](images/color_font_examples.jpg)
 *の例太字または半太字のフォントの太さ (上部パネル) では、読みやすくなります。*</span><span class="sxs-lookup"><span data-stu-id="e1400-128">![Dark UI examples](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="e1400-129">**MRTK の HolographicBackplate マテリアルを使用する**</span><span class="sxs-lookup"><span data-stu-id="e1400-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="e1400-130">HolographicBackplate マテリアルは、HoloLens シェルのいくつかの UI パネルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e1400-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="e1400-131">その機能の1つは、ユーザーがパネルに対して位置をシフトするときに表示される iridescence 効果です。</span><span class="sxs-lookup"><span data-stu-id="e1400-131">One of its features is an iridescence effect that is visible to users as they shift their position in relation to the panel.</span></span> <span data-ttu-id="e1400-132">バックプレートの色は、事前に定義された範囲にわたって微妙に変化し、コンテンツの読みやすさを妨げることなく、魅力的で動的な視覚効果を作成します。</span><span class="sxs-lookup"><span data-stu-id="e1400-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="e1400-133">この微妙な色の変化は、軽微な色の不規則性を補正するためにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e1400-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="e1400-134">透明または半透明の UI backplate に関する課題</span><span class="sxs-lookup"><span data-stu-id="e1400-134">Challenges with transparent or translucent UI backplate</span></span> 
<span data-ttu-id="e1400-135">![透過的 ](images/color_transparent_examples.jpg)
 *な ui の例透過 ui バックプレートの例*</span><span class="sxs-lookup"><span data-stu-id="e1400-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="e1400-136">**視覚的な複雑さとアクセシビリティ**</span><span class="sxs-lookup"><span data-stu-id="e1400-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="e1400-137">Holographic オブジェクトは物理環境とブレンドされるため、透明または半透明のウィンドウでコンテンツまたは UI が読みやすくなり、パフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e1400-137">Since holographic objects are blended with the physical environment, the legibility of the content or UI on the transparent or translucent window could be degraded.</span></span> <span data-ttu-id="e1400-138">さらに、transparent holographic オブジェクトが相互に重なっていると、ユーザーが混乱を招くことがあるため、ユーザーが対話するのが困難になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e1400-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="e1400-139">**パフォーマンス**</span><span class="sxs-lookup"><span data-stu-id="e1400-139">**Performance**</span></span>

<span data-ttu-id="e1400-140">透明または半透明のオブジェクトが正しくレンダリングされるようにするには、背景に存在するオブジェクトとの間で並べ替えおよびブレンドを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1400-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects which exist in the background.</span></span> <span data-ttu-id="e1400-141">透過的なオブジェクトを並べ替えると CPU コストが非常に大きくなります。これにより、GPU では、z カリング (つまり、</span><span class="sxs-lookup"><span data-stu-id="e1400-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it does not allow the GPU to perform hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="e1400-142">詳細テスト)。</span><span class="sxs-lookup"><span data-stu-id="e1400-142">depth testing).</span></span> <span data-ttu-id="e1400-143">非表示サーフェイスの削除を許可しない場合は、レンダリングされた最後のピクセルに対して計算する必要がある操作の数が増加するため、フィルレートの制約に対する負荷が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="e1400-143">Not allowing hidden surface removal increases the number of operations that need to be computed for the final rendered pixel, and thus puts more pressure on fill rate constraints.</span></span>

<span data-ttu-id="e1400-144">**深さ LSR テクノロジを使用したホログラムの安定性の問題**</span><span class="sxs-lookup"><span data-stu-id="e1400-144">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="e1400-145">Holographic の再プロジェクションやホログラムの安定性を向上させるために、アプリケーションは描画されたすべてのフレームに対して深度バッファーをシステムに送信できます。</span><span class="sxs-lookup"><span data-stu-id="e1400-145">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="e1400-146">Reprojection の深度バッファーを使用する場合は、対応する深度値をレンダリングするすべてのカラーピクセルが深度バッファーに書き込まれる必要があります (さらに、深度値を持つすべてのピクセルに色の値が必要です)。</span><span class="sxs-lookup"><span data-stu-id="e1400-146">When using the depth buffer for reprojection one rule is that for every color pixel rendered a corresponding depth value must be written to the depth buffer (and any pixel with a depth value should also have color value).</span></span> <span data-ttu-id="e1400-147">上記のガイダンスに従っていない場合、有効な深度情報のないレンダリングされたイメージの領域は、成果物を生成する方法で再投影される可能性があります (多くの場合、波形に似たゆがみとして表示されます)。</span><span class="sxs-lookup"><span data-stu-id="e1400-147">If the above guidance is not followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts (often visible as a wave-like distortion).</span></span>


## <a name="design-guidelines"></a><span data-ttu-id="e1400-148">設計ガイドライン</span><span class="sxs-lookup"><span data-stu-id="e1400-148">Design guidelines</span></span>
<span data-ttu-id="e1400-149">**不透明な UI の背景を使用する**</span><span class="sxs-lookup"><span data-stu-id="e1400-149">**Use opaque UI background**</span></span>

<span data-ttu-id="e1400-150">既定では、透明または半透明のオブジェクトは、適切にブレンドできるように深度を書き込みません。</span><span class="sxs-lookup"><span data-stu-id="e1400-150">By default, transparent or translucent objects do not write depth to allow for proper blending.</span></span> <span data-ttu-id="e1400-151">この問題を軽減するには、不透明なオブジェクトを使用して、透明なオブジェクトが不透明なオブジェクト (不透明なバックプレートの前面にある半透明のボタンなど) の近くに表示されるようにする、半透明なオブジェクトを強制的に書き込み (すべてのシナリオでは適用しない)、またはフレームの最後に深度値のみを提供するプロキシ</span><span class="sxs-lookup"><span data-stu-id="e1400-151">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="e1400-152">MRTK-Unity 内のソリューション: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="e1400-152">Solutions within MRTK-Unity: https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/hologram-stabilization.html#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="e1400-153">純色と不透明なバックプレートを使用することにより、読みやすさと相互作用の信頼を確保できます。</span><span class="sxs-lookup"><span data-stu-id="e1400-153">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="e1400-154">**影響を受けるピクセル数を最小限に抑える**</span><span class="sxs-lookup"><span data-stu-id="e1400-154">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="e1400-155">プロジェクトで透過的なオブジェクトを使用する必要がある場合は、影響を受けるピクセル数を最小限に抑えてください。</span><span class="sxs-lookup"><span data-stu-id="e1400-155">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="e1400-156">たとえば、オブジェクトが特定の条件下でのみ表示される場合 (加法グロー効果のように)、オブジェクトが完全に非表示になっている場合はそのオブジェクトを無効にします (加法の色を黒に設定するのではなく)。</span><span class="sxs-lookup"><span data-stu-id="e1400-156">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it is fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="e1400-157">アルファマスクを持つクワッドを使用して作成された単純な2D 図形の場合は、代わりに不透明なシェーダーを使用して図形のメッシュ表現を作成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e1400-157">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="e1400-158">Unity 用の濃い UI の例 (Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="e1400-158">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="e1400-159">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、濃色配色に基づく多数の UI 構成ブロックの例が用意されています。</span><span class="sxs-lookup"><span data-stu-id="e1400-159">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="e1400-160">Near メニュー</span><span class="sxs-lookup"><span data-stu-id="e1400-160">Near Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_NearMenu.html)
* [<span data-ttu-id="e1400-161">ダイアログ</span><span class="sxs-lookup"><span data-stu-id="e1400-161">Dialog</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Assets/MRTK/SDK/Experimental/Dialog/README_Dialog.html)
* [<span data-ttu-id="e1400-162">ハンドメニュー</span><span class="sxs-lookup"><span data-stu-id="e1400-162">Hand Menu</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)


<br>

---


## <a name="see-also"></a><span data-ttu-id="e1400-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1400-163">See also</span></span>
* [<span data-ttu-id="e1400-164">色、ライト、マテリアル</span><span class="sxs-lookup"><span data-stu-id="e1400-164">Color, light and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="e1400-165">カーソル</span><span class="sxs-lookup"><span data-stu-id="e1400-165">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="e1400-166">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="e1400-166">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="e1400-167">ボタン</span><span class="sxs-lookup"><span data-stu-id="e1400-167">Button</span></span>](button.md)
* [<span data-ttu-id="e1400-168">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="e1400-168">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e1400-169">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="e1400-169">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="e1400-170">操作</span><span class="sxs-lookup"><span data-stu-id="e1400-170">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e1400-171">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="e1400-171">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="e1400-172">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="e1400-172">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="e1400-173">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="e1400-173">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="e1400-174">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="e1400-174">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="e1400-175">キーボード</span><span class="sxs-lookup"><span data-stu-id="e1400-175">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="e1400-176">ヒント</span><span class="sxs-lookup"><span data-stu-id="e1400-176">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="e1400-177">スレート</span><span class="sxs-lookup"><span data-stu-id="e1400-177">Slate</span></span>](slate.md)
* [<span data-ttu-id="e1400-178">スライダー</span><span class="sxs-lookup"><span data-stu-id="e1400-178">Slider</span></span>](slider.md)
* [<span data-ttu-id="e1400-179">シェーダー</span><span class="sxs-lookup"><span data-stu-id="e1400-179">Shader</span></span>](shader.md)
* [<span data-ttu-id="e1400-180">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="e1400-180">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="e1400-181">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="e1400-181">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="e1400-182">表面吸着</span><span class="sxs-lookup"><span data-stu-id="e1400-182">Surface magnetism</span></span>](surface-magnetism.md)
