---
title: ホログラフィック ディスプレイのコンテンツを設計する
description: HoloLens デバイスでの holographic 表示の設計ガイドラインとベストプラクティスについて説明します。
author: yoonpark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: UI デザイン, holographic 表示, コンテンツデザイン, ダークテーマ, ライトテーマ, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット, HoloLens, MRTK, Mixed Reality Toolkit, 設計, ピクセル
ms.openlocfilehash: 6bf65b9e40e42f1609b1108b366ac65637fcf106
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759277"
---
# <a name="designing-content-for-holographic-display"></a><span data-ttu-id="e1ecf-104">ホログラフィック ディスプレイのコンテンツを設計する</span><span class="sxs-lookup"><span data-stu-id="e1ecf-104">Designing content for holographic display</span></span>

![Ulnar side location](images/UX_Hero_DarkTheme.jpg)

<span data-ttu-id="e1ecf-106">Holographic が表示されるようにコンテンツを設計する際には、最適なエクスペリエンスを実現するために考慮する必要がある要素がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-106">When designing content for holographic displays, there are several elements that you need to consider for achieving the best experience.</span></span> <span data-ttu-id="e1ecf-107">ここでは、いくつかの推奨事項の一覧を示し、 [色、光、およびマテリアル](color-light-and-materials.md) のページで holographic 表示の特性について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-107">We've listed some of our recommendations below and you can learn more about the characteristics of holographic displays at [Color, light and materials](color-light-and-materials.md) page.</span></span>

<br>

## <a name="challenges-with-bright-color-on-a-large-surface"></a><span data-ttu-id="e1ecf-108">大きな表面で明るい色の課題</span><span class="sxs-lookup"><span data-stu-id="e1ecf-108">Challenges with bright color on a large surface</span></span> 

<span data-ttu-id="e1ecf-109">HoloLens エクスペリエンスの研究とテストに基づいて、ディスプレイの大きな領域で明るい色を使用すると、いくつかの問題が発生する可能性があることがわかりました。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-109">Based on our HoloLens experience research and testing, we found that using bright colors in a large area of the display can cause several issues:</span></span> 

<span data-ttu-id="e1ecf-110">**目の疲労**</span><span class="sxs-lookup"><span data-stu-id="e1ecf-110">**Eye fatigue**</span></span> 

<span data-ttu-id="e1ecf-111">Holographic display は加法であるため、明るい色を持つホログラムはより多くの光を使用します。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-111">Since holographic display is additive, holograms with bright colors use more light.</span></span> <span data-ttu-id="e1ecf-112">ディスプレイの大きな領域に明るい色を使用すると、ユーザーにとって目の疲労が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-112">Bright, solid color in a large area of the display can easily cause eye fatigue for the user.</span></span> 

<span data-ttu-id="e1ecf-113">**手動でのオクルージョン**</span><span class="sxs-lookup"><span data-stu-id="e1ecf-113">**Hand occlusion**</span></span> 

<span data-ttu-id="e1ecf-114">明るい色を使用すると、オブジェクトを直接操作するときにユーザーが手を見ることが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-114">Bright color makes it difficult for the user to see their hands when directly interacting with objects.</span></span> <span data-ttu-id="e1ecf-115">ユーザーは人間を見ることができないため、針とターゲットサーフェスの間の深さ/距離を認識することは困難になります。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-115">Since the user can't see their hands, it becomes difficult to perceive the depth/distance between the hand/finger to the target surface.</span></span> <span data-ttu-id="e1ecf-116">指カーソルを使用するとこの問題を補うことができますが、それでも明るい白い面では困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-116">The Finger Cursor helps compensate for this issue, but it can still be challenging on a bright white surface.</span></span> 

<span data-ttu-id="e1ecf-117">![色とハンドオクルーが ](images/color_handocclusion.jpg)
 *明るい色のコンテンツバックプレートで手を見づらい*</span><span class="sxs-lookup"><span data-stu-id="e1ecf-117">![Color and hand occlusion](images/color_handocclusion.jpg)
*Difficult to see the hand on the bright colored content backplate*</span></span>

<span data-ttu-id="e1ecf-118">**色の統一性**</span><span class="sxs-lookup"><span data-stu-id="e1ecf-118">**Color uniformity**</span></span>

<span data-ttu-id="e1ecf-119">Holographic 表示の特性により、画面上の大きな明るい領域が blotchy になることがあります。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-119">Because of the characteristics of holographic displays, a large bright area on the display can become blotchy.</span></span> <span data-ttu-id="e1ecf-120">ダーク配色を使用すると、この問題を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-120">By using dark color schemes, you can minimize this issue.</span></span> 

## <a name="design-guidelines-for-color-choices"></a><span data-ttu-id="e1ecf-121">色の選択のデザインガイドライン</span><span class="sxs-lookup"><span data-stu-id="e1ecf-121">Design guidelines for color choices</span></span>

<span data-ttu-id="e1ecf-122">**UI の背景に濃い色を使用する**</span><span class="sxs-lookup"><span data-stu-id="e1ecf-122">**Use dark color for the UI background**</span></span>

<span data-ttu-id="e1ecf-123">ダーク配色を使用することにより、目の疲労を最小化し、直接的なやり取りに対する信頼度を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-123">By using the dark color scheme, you can minimize eye fatigue and improve the confidence on direct hand interactions.</span></span> 

<span data-ttu-id="e1ecf-124">![コンテンツの背景に使用される濃い色 ](images/color_dark_examples.jpg)
 *の例* コンテンツの背景に使用される暗い色の例</span><span class="sxs-lookup"><span data-stu-id="e1ecf-124">![Examples of dark color used for the content background](images/color_dark_examples.jpg)
*Examples of dark color used for the content background*</span></span>

<span data-ttu-id="e1ecf-125">**Semibold または太字のフォントの太さを使用する**</span><span class="sxs-lookup"><span data-stu-id="e1ecf-125">**Use semibold or bold font weight**</span></span>

<span data-ttu-id="e1ecf-126">HoloLens を使用すると、美しい高解像度のテキストを表示できます。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-126">HoloLens allows your experience to show beautiful high-resolution text.</span></span> <span data-ttu-id="e1ecf-127">ただし、縦方向のストロークが小さいフォントサイズでジッターになる可能性があるため、光や半光などの細いフォントの重みを使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-127">However, it's recommended that you avoid thin font weights such as light or semi-light because the vertical strokes can jitter in small font size.</span></span> 

<span data-ttu-id="e1ecf-128">![太字または半太字のフォントの太さ (上のパネル) では、読みやすくするために ](images/color_font_examples.jpg)
 *太字または半太字のフォントの太さ (上のパネル) が向上します。*</span><span class="sxs-lookup"><span data-stu-id="e1ecf-128">![Bold or semi-bold font weight (upper panel) improves the legibility](images/color_font_examples.jpg)
*Bold or semi-bold font weight (upper panel) improves the legibility*</span></span>

<span data-ttu-id="e1ecf-129">**MRTK の HolographicBackplate マテリアルを使用する**</span><span class="sxs-lookup"><span data-stu-id="e1ecf-129">**Use MRTK’s HolographicBackplate material**</span></span>

<span data-ttu-id="e1ecf-130">HolographicBackplate マテリアルは、HoloLens シェルのいくつかの UI パネルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-130">The HolographicBackplate material is applied to several UI panels in the HoloLens shell.</span></span> <span data-ttu-id="e1ecf-131">その機能の1つは、パネルに基づいてユーザーが移動するときにユーザーに表示される iridescence 効果です。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-131">One of its features is an iridescence effect that is visible to users as they shift their position based on the panel.</span></span> <span data-ttu-id="e1ecf-132">バックプレートの色は、事前に定義された範囲にわたって微妙に変化し、コンテンツの読みやすさを妨げることなく、魅力的で動的な視覚効果を作成します。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-132">The backplate color shifts subtly across a predefined spectrum, creating an engaging and dynamic visual effect without interfering with content readability.</span></span> <span data-ttu-id="e1ecf-133">この微妙な色の変化は、軽微な色の不規則性を補正するためにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-133">This subtle shift in color also serves to compensate for any minor color irregularities.</span></span> 


## <a name="challenges-with-transparent-or-translucent-ui-backplate"></a><span data-ttu-id="e1ecf-134">透明または半透明の UI backplate に関する課題</span><span class="sxs-lookup"><span data-stu-id="e1ecf-134">Challenges with transparent or translucent UI backplate</span></span> 

<span data-ttu-id="e1ecf-135">![透過的 ](images/color_transparent_examples.jpg)
 *な ui の例透過 ui バックプレートの例*</span><span class="sxs-lookup"><span data-stu-id="e1ecf-135">![Transparent UI examples](images/color_transparent_examples.jpg)
*Examples of transparent UI backplate*</span></span>

<span data-ttu-id="e1ecf-136">**視覚的な複雑さとアクセシビリティ**</span><span class="sxs-lookup"><span data-stu-id="e1ecf-136">**Visual complexity and accessibility**</span></span>

<span data-ttu-id="e1ecf-137">Holographic オブジェクトは物理的な環境と blend があるため、透明または半透明のウィンドウでコンテンツや UI が読みやすくなり、パフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-137">Since holographic objects blend with the physical environment, content or UI legibility on transparent or translucent windows could be degraded.</span></span> <span data-ttu-id="e1ecf-138">さらに、transparent holographic オブジェクトが相互に重なっていると、ユーザーが混乱を招くことがあるため、ユーザーが対話するのが困難になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-138">Additionally, when transparent holographic objects are overlaid on top of each other, it could make it difficult for the user to interact because of the confusing depth.</span></span>

<span data-ttu-id="e1ecf-139">**パフォーマンス**</span><span class="sxs-lookup"><span data-stu-id="e1ecf-139">**Performance**</span></span>

<span data-ttu-id="e1ecf-140">透明または半透明のオブジェクトが正しくレンダリングされるようにするには、背景に存在するオブジェクトとの間で並べ替えおよびブレンドを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-140">For transparent or translucent objects to render correctly they must be sorted and blended with any objects, which exist in the background.</span></span> <span data-ttu-id="e1ecf-141">透過的なオブジェクトを並べ替えると CPU コストが非常に大きくなります。これは、GPU が z カリングを使用した非表示サーフェスの削除を許可しないため (つまり、</span><span class="sxs-lookup"><span data-stu-id="e1ecf-141">Sorting of transparent objects has a modest CPU cost, blending has considerable GPU cost because it doesn't allow the GPU to do hidden surface removal via z-culling (i.e</span></span> <span data-ttu-id="e1ecf-142">詳細テスト)。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-142">depth testing).</span></span> <span data-ttu-id="e1ecf-143">非表示サーフェイスの削除を許可しない場合は、レンダリングされた最後のピクセルに必要な操作の数が増加します。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-143">Not allowing hidden surface removal increases the number of operations needed for the final rendered pixel.</span></span> <span data-ttu-id="e1ecf-144">これにより、より多くの圧力フィルレート制約が課されます。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-144">This puts on more pressure fill rate constraints.</span></span>

<span data-ttu-id="e1ecf-145">**深さ LSR テクノロジを使用したホログラムの安定性の問題**</span><span class="sxs-lookup"><span data-stu-id="e1ecf-145">**Hologram stability issue with Depth LSR technology**</span></span>

<span data-ttu-id="e1ecf-146">Holographic の再プロジェクションやホログラムの安定性を向上させるために、アプリケーションは描画されたすべてのフレームに対して深度バッファーをシステムに送信できます。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-146">To improve holographic reprojection, or hologram stability, an application can submit a depth buffer to the system for every rendered frame.</span></span> <span data-ttu-id="e1ecf-147">Reprojection の深度バッファーを使用する場合は、表示されるすべての色に対応する深度に対して深度バッファーを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-147">When using the depth buffer for reprojection, you need to write a depth buffer for every color rendered pixel a corresponding depth.</span></span> <span data-ttu-id="e1ecf-148">深度値を持つすべてのピクセルにも色の値が必要です。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-148">Any pixel with a depth value should also have color value.</span></span> <span data-ttu-id="e1ecf-149">上記のガイダンスに従っていない場合、有効な深度情報のないレンダリングされたイメージの領域が、成果物を生成する方法で再投影される可能性があります。これは、多くの場合、波のような歪みとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-149">If the above guidance isn't followed, areas of the rendered image that lack valid depth information may be reprojected in a way that produces artifacts, which are often visible as a wave-like distortion.</span></span>


## <a name="design-guidelines-for-transparent-elements"></a><span data-ttu-id="e1ecf-150">透過的な要素のデザインガイドライン</span><span class="sxs-lookup"><span data-stu-id="e1ecf-150">Design guidelines for transparent elements</span></span>

<span data-ttu-id="e1ecf-151">**不透明な UI の背景を使用する**</span><span class="sxs-lookup"><span data-stu-id="e1ecf-151">**Use opaque UI background**</span></span>

<span data-ttu-id="e1ecf-152">既定では、透明または半透明のオブジェクトは、適切なブレンドを可能にするための深度を書き込みません。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-152">By default, transparent or translucent objects don't write depth to allow for proper blending.</span></span> <span data-ttu-id="e1ecf-153">この問題を軽減するには、不透明なオブジェクトを使用して、透明なオブジェクトが不透明なオブジェクト (不透明な backplate の前面にある半透明のボタンなど) の近くに表示されるようにする、半透明なオブジェクトを強制的に書き込み (すべてのシナリオでは適用しない)、またはフレームの最後に深さの値のみを提供する</span><span class="sxs-lookup"><span data-stu-id="e1ecf-153">Ways to mitigate this issue include, using opaque objects, ensuring translucent objects appear close to opaque objects (such as a translucent button in front of an opaque backplate), forcing translucent objects to write depth (not applicable in all scenarios), or rendering proxy objects, which only contribute depth values at the end of the frame.</span></span>

<span data-ttu-id="e1ecf-154">MRTK-Unity 内のソリューション: https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/hologram-stabilization.md#depth-buffer-sharing-in-unity</span><span class="sxs-lookup"><span data-stu-id="e1ecf-154">Solutions within MRTK-Unity: https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/performance/hologram-stabilization.md#depth-buffer-sharing-in-unity</span></span>  

<span data-ttu-id="e1ecf-155">純色と不透明なバックプレートを使用することにより、読みやすさと相互作用の信頼を確保できます。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-155">By using a solid and opaque backplate, we can secure legibility and interaction confidence.</span></span>

<span data-ttu-id="e1ecf-156">**影響を受けるピクセル数を最小限に抑える**</span><span class="sxs-lookup"><span data-stu-id="e1ecf-156">**Minimize the number of pixels affected**</span></span>

<span data-ttu-id="e1ecf-157">プロジェクトで透過的なオブジェクトを使用する必要がある場合は、影響を受けるピクセル数を最小限に抑えてください。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-157">If your project must use transparent objects, try to minimize the number of pixels affected.</span></span> <span data-ttu-id="e1ecf-158">たとえば、オブジェクトが特定の条件下でのみ表示される場合 (加法グロー効果など) は、オブジェクトが完全に非表示になったときに、そのオブジェクトを無効にします (加法の色を黒に設定するのではなく)。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-158">For example, if an object is only visible under certain conditions (like an additive glow effect), disable the object when it's fully invisible (instead of setting the additive color to black).</span></span> <span data-ttu-id="e1ecf-159">アルファマスクを持つクワッドを使用して作成された単純な2D 図形の場合は、代わりに不透明なシェーダーを使用して図形のメッシュ表現を作成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-159">For simple 2D shapes created using a quad with an alpha mask, consider creating a mesh representation of the shape with an opaque shader instead.</span></span> 

<br/>

---

<br/>

## <a name="dark-ui-examples-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="e1ecf-160">Unity 用の濃い UI の例 (Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="e1ecf-160">Dark UI examples in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="e1ecf-161">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、濃色配色に基づく多数の UI 構成ブロックの例が用意されています。</span><span class="sxs-lookup"><span data-stu-id="e1ecf-161">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides many UI building block examples based on the dark color schemes.</span></span>

* [<span data-ttu-id="e1ecf-162">Near メニュー</span><span class="sxs-lookup"><span data-stu-id="e1ecf-162">Near Menu</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/near-menu.md)
* [<span data-ttu-id="e1ecf-163">ダイアログ</span><span class="sxs-lookup"><span data-stu-id="e1ecf-163">Dialog</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/experimental/dialog.md)
* [<span data-ttu-id="e1ecf-164">ハンドメニュー</span><span class="sxs-lookup"><span data-stu-id="e1ecf-164">Hand Menu</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/hand-menu.md)

<br>

---

## <a name="see-also"></a><span data-ttu-id="e1ecf-165">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1ecf-165">See also</span></span>

* [<span data-ttu-id="e1ecf-166">色、ライト、素材</span><span class="sxs-lookup"><span data-stu-id="e1ecf-166">Color, light, and materials</span></span>](color-light-and-materials.md)
* [<span data-ttu-id="e1ecf-167">カーソル</span><span class="sxs-lookup"><span data-stu-id="e1ecf-167">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="e1ecf-168">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="e1ecf-168">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="e1ecf-169">ボタン</span><span class="sxs-lookup"><span data-stu-id="e1ecf-169">Button</span></span>](button.md)
* [<span data-ttu-id="e1ecf-170">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="e1ecf-170">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="e1ecf-171">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="e1ecf-171">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="e1ecf-172">操作</span><span class="sxs-lookup"><span data-stu-id="e1ecf-172">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e1ecf-173">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="e1ecf-173">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="e1ecf-174">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="e1ecf-174">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="e1ecf-175">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="e1ecf-175">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="e1ecf-176">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="e1ecf-176">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="e1ecf-177">キーボード</span><span class="sxs-lookup"><span data-stu-id="e1ecf-177">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="e1ecf-178">ヒント</span><span class="sxs-lookup"><span data-stu-id="e1ecf-178">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="e1ecf-179">スレート</span><span class="sxs-lookup"><span data-stu-id="e1ecf-179">Slate</span></span>](slate.md)
* [<span data-ttu-id="e1ecf-180">スライダー</span><span class="sxs-lookup"><span data-stu-id="e1ecf-180">Slider</span></span>](slider.md)
* [<span data-ttu-id="e1ecf-181">シェーダー</span><span class="sxs-lookup"><span data-stu-id="e1ecf-181">Shader</span></span>](shader.md)
* [<span data-ttu-id="e1ecf-182">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="e1ecf-182">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="e1ecf-183">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="e1ecf-183">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="e1ecf-184">表面吸着</span><span class="sxs-lookup"><span data-stu-id="e1ecf-184">Surface magnetism</span></span>](surface-magnetism.md)
