---
title: 色、ライト、素材
description: 混合現実のコンテンツをデザインするには、すべてのビジュアル資産の色、照明、素材を慎重に検討する必要があります。
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、カラー、ライト、マテリアル、Mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 5d99941f068e808ba14d97084ef840a66aded2a9
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848060"
---
# <a name="color-light-and-materials"></a><span data-ttu-id="1f7bc-104">色、ライト、素材</span><span class="sxs-lookup"><span data-stu-id="1f7bc-104">Color, light, and materials</span></span>

![色、ライト、マテリアル](images/RemoteRendering.jpg)

<span data-ttu-id="1f7bc-106">混合現実のコンテンツを設計するには、すべての仮想資産の色、照明、マテリアルを慎重に検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-106">Designing content for mixed reality requires careful consideration of color, lighting, and materials for all your virtual assets.</span></span> <span data-ttu-id="1f7bc-107">見た目を向上させるには、光と素材を使用してイマーシブ環境の雰囲気を設定することができます。また、機能的な目的で、わかりやすい色を使用して、近いアクションをユーザーに通知することもできます。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-107">Aesthetic purposes can include using light and material to set the tone of an immersive environment, while functional purposes can include using striking colors to alert users of an impending action.</span></span> <span data-ttu-id="1f7bc-108">これらの各決定は、エクスペリエンスのターゲットデバイスの機会と制約に照らし合わせて検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-108">Each of these decisions must be weighed against the opportunities and constraints of your experience’s target device.</span></span>

<span data-ttu-id="1f7bc-109">次に示すのは、イマーシブと holographic ヘッドセットの両方でのアセットのレンダリングに固有のガイドラインです。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-109">Below are guidelines specific to rendering assets on both immersive and holographic headsets.</span></span> <span data-ttu-id="1f7bc-110">これらの多くは、他の技術領域に密接に関連しており、関連する項目の一覧に [ついて](color-light-and-materials.md#see-also) は、この記事の最後にある「関連項目」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-110">Many of these are closely tied to other technical areas and a list of related subjects can be found in the [See also](color-light-and-materials.md#see-also) section at the end of this article.</span></span>

## <a name="rendering-on-immersive-vs-holographic-devices"></a><span data-ttu-id="1f7bc-111">イマーシブおよび holographic デバイスでのレンダリング</span><span class="sxs-lookup"><span data-stu-id="1f7bc-111">Rendering on immersive vs. holographic devices</span></span>

<span data-ttu-id="1f7bc-112">イマーシブヘッドセットでレンダリングされるコンテンツは、holographic ヘッドセットでレンダリングされるコンテンツと比較すると、視覚的に異なります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-112">Content rendered in immersive headsets will appear visually different when compared to content rendered in holographic headsets.</span></span> <span data-ttu-id="1f7bc-113">イマーシブヘッドセットでは、通常、2D 画面の場合と同じようにコンテンツがレンダリングされますが、HoloLens のような holographic ヘッドセットは、カラーシーケンシャルで、「」を参照して、ホログラムをレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-113">While immersive headsets generally render content much as you would expect on a 2D screen, holographic headsets like HoloLens use color-sequential, see-through RGB displays to renders holograms.</span></span>

<span data-ttu-id="1f7bc-114">Holographic ヘッドセットで holographic エクスペリエンスをテストするには、常に時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-114">Always take time to test your holographic experiences in a holographic headset.</span></span> <span data-ttu-id="1f7bc-115">コンテンツの外観は、holographic デバイス専用に構築されている場合でも、セカンダリモニター、スナップショット、および spectator ビューで見られるものとは異なります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-115">The appearance of content, even if it's built specifically for holographic devices, will differ as seen on secondary monitors, snapshots, and in spectator view.</span></span> <span data-ttu-id="1f7bc-116">デバイスのエクスペリエンスについて説明し、ホログラムの照明をテストして、コンテンツがどのようにレンダリングされるかについて、すべての辺 (および上および下) から観察することを忘れないでください。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-116">Remember to walk around experiences with a device, testing the lighting of holograms and observing from all sides (as well as from above and below) how your content renders.</span></span> <span data-ttu-id="1f7bc-117">デバイスのさまざまな明るさの設定でテストしてください。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-117">Be sure to test with a range of brightness settings on the device.</span></span> <span data-ttu-id="1f7bc-118">すべてのユーザーが想定されている既定値と、さまざまな照明条件のセットを共有することはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-118">It's unlikely all users will share an assumed default, and a diverse set of lighting conditions.</span></span>

## <a name="fundamentals-of-rendering-on-holographic-devices"></a><span data-ttu-id="1f7bc-119">Holographic デバイスでのレンダリングの基礎</span><span class="sxs-lookup"><span data-stu-id="1f7bc-119">Fundamentals of rendering on holographic devices</span></span>

* <span data-ttu-id="1f7bc-120">Holographic のデバイスには追加の **ディスプレイがあり** ます。実際の世界から光に光を追加することによって、ホログラムが作成されます。白は明るいと表示され、黒は透明に見えます。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-120">**Holographic devices have additive displays** – Holograms are created by adding light to the light from the real world – white will appear brightly, while black will appear transparent.</span></span>

* <span data-ttu-id="1f7bc-121">**色の影響はユーザーの環境によって異なり** ます。ユーザーの部屋にはさまざまな照明条件があります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-121">**Colors impact varies with the user’s environment** – There are many diverse lighting conditions in a user’s room.</span></span> <span data-ttu-id="1f7bc-122">わかりやすくするために、適切なコントラストレベルでコンテンツを作成します。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-122">Create content with appropriate levels of contrast to help with clarity.</span></span>

* <span data-ttu-id="1f7bc-123">**動的な照明を避ける** – holographic エクスペリエンスで一様に点灯するホログラムは最も効率的です。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-123">**Avoid dynamic lighting** – Holograms that are uniformly lit in holographic experiences are the most efficient.</span></span> <span data-ttu-id="1f7bc-124">高度な機能を使用すると、モバイルデバイスの機能を超える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-124">Using advanced, dynamic lighting will likely exceed the capabilities of mobile devices.</span></span> <span data-ttu-id="1f7bc-125">動的ライティングが必要な場合は、 [Mixed Reality Toolkit の標準シェーダー](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-125">When dynamic lighting is required, it's recommended to use the [Mixed Reality Toolkit Standard shader](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md).</span></span> 

## <a name="designing-with-color"></a><span data-ttu-id="1f7bc-126">色を使用したデザイン</span><span class="sxs-lookup"><span data-stu-id="1f7bc-126">Designing with color</span></span>

<span data-ttu-id="1f7bc-127">加法表示の性質により、holographic の表示では特定の色が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-127">Because of the nature of additive displays, certain colors can appear different on holographic displays.</span></span> <span data-ttu-id="1f7bc-128">照明環境ではいくつかの色が表示されますが、他の色は少ないインパクトとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-128">Some colors will pop in lighting environments while others will appear as less impactful.</span></span> <span data-ttu-id="1f7bc-129">クール色は背景に recede 傾向があり、ウォームカラーは前景に移動します。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-129">Cool colors tend to recede into the background while warm colors jump to the foreground.</span></span> <span data-ttu-id="1f7bc-130">エクスペリエンスの色を調べる際には、次の要因を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-130">Consider these factors as you explore color in your experiences:</span></span>

* <span data-ttu-id="1f7bc-131">**明るい色** を表示する-白は明るく、控えめに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-131">**Rendering light colors** - White appears bright and should be used sparingly.</span></span> <span data-ttu-id="1f7bc-132">ほとんどの場合、R 235 G 235 B 235 に関する白い値を検討してください。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-132">For most cases, consider a white value around R 235 G 235 B 235.</span></span> <span data-ttu-id="1f7bc-133">大きな明るい領域では、ユーザー不快感が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-133">Large bright areas may cause user discomfort.</span></span> <span data-ttu-id="1f7bc-134">UI ウィンドウの背景プレートでは、暗い色を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-134">For the UI window's backplate, it's recommended to use dark colors.</span></span>

* <span data-ttu-id="1f7bc-135">**ダークカラーのレンダリング** -加法表示の性質により、暗い色は透明に見えます。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-135">**Rendering dark colors** - Because of the nature of additive displays, dark colors appear transparent.</span></span> <span data-ttu-id="1f7bc-136">純色の黒のオブジェクトは、実際の世界とは異なるものとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-136">A solid black object will appear no different from the real world.</span></span> <span data-ttu-id="1f7bc-137">下記の「アルファチャネル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-137">See Alpha channel below.</span></span> <span data-ttu-id="1f7bc-138">"Black" のように見えるようにするには、16、16、16などの非常に濃い灰色の RGB 値を試してみてください。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-138">To give the appearance of “black”, try a very dark grey RGB value such as 16,16,16.</span></span>

* <span data-ttu-id="1f7bc-139">**色の統一性** -通常、ホログラムは、背景の色の統一性を維持するために十分な明るい色で表示されます。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-139">**Color uniformity** - Typically holograms are rendered brightly enough so that they maintain color uniformity, whatever the background.</span></span> <span data-ttu-id="1f7bc-140">大きな領域が blotchy になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-140">Large areas may become blotchy.</span></span> <span data-ttu-id="1f7bc-141">明るい、純色の大きな領域は避けてください。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-141">Avoid large regions of bright, solid color.</span></span>

* <span data-ttu-id="1f7bc-142">色 **域**-HoloLens は、概念的には Adobe RGB に似ています。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-142">**Gamut** - HoloLens benefits from a "wide gamut" of color, conceptually similar to Adobe RGB.</span></span> <span data-ttu-id="1f7bc-143">その結果、色によっては、デバイス内のさまざまな品質と表現が表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-143">As a result, some colors can show different qualities and representation in the device.</span></span>

* <span data-ttu-id="1f7bc-144">**ガンマ** -レンダリングされるイメージの明るさとコントラストは、イマーシブデバイスと holographic デバイスで異なります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-144">**Gamma** - The brightness and contrast of the rendered image will vary between immersive and holographic devices.</span></span> <span data-ttu-id="1f7bc-145">多くの場合、これらのデバイスの違いは、色や影の暗い領域を作成したり、明るくしたりするように見えます。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-145">These device differences often appear to make dark areas of color and shadows, more or less bright.</span></span>

* <span data-ttu-id="1f7bc-146">**色の分離** -"色を分割した" または "カラー fringing" とも呼ばれ、ユーザーが目のオブジェクトを追跡するときに、最も一般的に色の分離が発生します。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-146">**Color separation** - Also called "color breakup" or "color fringing", color separation most commonly occurs with moving holograms (including cursor) when a user tracks objects with their eyes.</span></span>

## <a name="technical-considerations"></a><span data-ttu-id="1f7bc-147">技術的な考慮事項</span><span class="sxs-lookup"><span data-stu-id="1f7bc-147">Technical considerations</span></span>

* <span data-ttu-id="1f7bc-148">**別名** -ホログラム、ギザギザ、"階段のよく検討" のように、ホログラムのジオメトリのエッジが実際の世界を満たしていることを認識します。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-148">**Aliasing** - Be considerate of aliasing, jagged or “stair steps” where the edge of a hologram’s geometry meets the real world.</span></span> <span data-ttu-id="1f7bc-149">詳細が高いテクスチャを使用すると、この効果を aggravate ことができます。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-149">Using textures with high detail can aggravate this effect.</span></span> <span data-ttu-id="1f7bc-150">テクスチャをマップし、フィルター処理を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-150">Textures should be mapped and filtering enabled.</span></span> <span data-ttu-id="1f7bc-151">ホログラムの端をフェードさせるか、オブジェクトの周囲に黒いエッジ境界線を作成するテクスチャを追加することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-151">Consider fading the edges of holograms or adding a texture that creates a black edge border around objects.</span></span> <span data-ttu-id="1f7bc-152">可能であれば、thin geometry は避けてください。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-152">Avoid thin geometry where possible.</span></span>

* <span data-ttu-id="1f7bc-153">**アルファチャネル** -ホログラムをレンダリングしていないすべてのパーツに対して完全に透明にするには、アルファチャネルをクリアする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-153">**Alpha channel** - You must clear your alpha channel to fully transparent for any parts where you aren't rendering a hologram.</span></span> <span data-ttu-id="1f7bc-154">アルファを未定義のままにすると、デバイスまたは Spectator ビューで画像やビデオを撮影するときに、視覚的な成果物が得られます。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-154">Leaving the alpha undefined leads to visual artifacts when taking images/videos from the device or with Spectator View.</span></span>

* <span data-ttu-id="1f7bc-155">**テクスチャの補正** : ライトは holographic ディスプレイで追加されるため、強い色の広い領域を避けることをお勧めします。これは、多くの場合、意図した視覚効果を生み出すことがないためです。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-155">**Texture softening** - Since light is additive in holographic displays, it's best to avoid large regions of bright, solid color as they often don't produce the intended visual effect.</span></span>

## <a name="design-guidelines-for-holographic-display"></a><span data-ttu-id="1f7bc-156">Holographic 表示の設計ガイドライン</span><span class="sxs-lookup"><span data-stu-id="1f7bc-156">Design guidelines for holographic display</span></span>

![色とハンドオクルージョン](images/color_handocclusion.jpg)

<span data-ttu-id="1f7bc-158">Holographic 表示用にコンテンツをデザインする場合、最適なエクスペリエンスを実現するために必要ないくつかの要素があります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-158">When designing content for holographic displays, there are several elements that you need to consider achieving the best experience.</span></span> <span data-ttu-id="1f7bc-159">ガイドラインと推奨事項については、「 [holographic のコンテンツのデザイン](designing-content-for-holographic-display.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-159">Visit [Designing content for holographic display](designing-content-for-holographic-display.md) for the guidelines and recommendations.</span></span>

## <a name="storytelling-with-light-and-color"></a><span data-ttu-id="1f7bc-160">薄いと color を使用したストーリーテリング</span><span class="sxs-lookup"><span data-stu-id="1f7bc-160">Storytelling with light and color</span></span>

<span data-ttu-id="1f7bc-161">色と色を使用すると、ユーザーの環境でのホログラムの表示がより自然になり、ユーザーのためのガイダンスやヘルプが提供されます。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-161">Light and color can help make your holograms appear more naturally in a user's environment and offer guidance and help for the user.</span></span> <span data-ttu-id="1f7bc-162">Holographic エクスペリエンスについては、照明と色を調べる際に、次の要因を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-162">For holographic experiences, consider these factors as you explore lighting and color:</span></span>

:::row:::
    :::column:::
* <span data-ttu-id="1f7bc-163">**Vignetting** -マテリアルを暗くするための ' vignette ' 効果は、ビューのフィールドの中央にユーザーの注意を集中するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-163">**Vignetting** - A 'vignette' effect to darken materials can help focus the user's attention on the center of the field of view.</span></span> <span data-ttu-id="1f7bc-164">この効果により、ユーザーの見つめベクターから、ある程度の半径でホログラムのマテリアルが暗くなります。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-164">This effect darkens the hologram's material at some radius from the user's gaze vector.</span></span> <span data-ttu-id="1f7bc-165">これは、ユーザーが傾斜や glancing の角度からホログラムを表示する場合にも有効です。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-165">This is also effective when the user views holograms from an oblique or glancing angle.</span></span>

* <span data-ttu-id="1f7bc-166">**強調** 描画: 色、明るさ、および光源を比較して、オブジェクトまたは相互作用のポイントに注目します。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-166">**Emphasis** - Draw attention to objects or points of interaction by contrasting colors, brightness, and lighting.</span></span> <span data-ttu-id="1f7bc-167">ストーリーテリングの照明メソッドの詳細については、「 [ピクセル Cinematography-コンピューターグラフィックスの照明アプローチ](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-167">For a more detailed look at lighting methods in storytelling, see [Pixel Cinematography - A Lighting Approach for Computer Graphics](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf).</span></span><br>
        <br>
        <span data-ttu-id="1f7bc-168">*Image: 色を使用してストーリーテリング要素の強調を表示します。ここでは、 [フラグメント](https://www.microsoft.com/p/fragments/9nblggh5ggm8)からのシーンに示します。*</span><span class="sxs-lookup"><span data-stu-id="1f7bc-168">*Image: Use of color to show emphasis for storytelling elements, shown here in a scene from [Fragments](https://www.microsoft.com/p/fragments/9nblggh5ggm8).*</span></span>
    :::column-end:::
        :::column:::
        ![色を使用して、ストーリーテリング要素の強調を表示します。ここでは、フラグメントからのシーンに示します。](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a><span data-ttu-id="1f7bc-170">素材</span><span class="sxs-lookup"><span data-stu-id="1f7bc-170">Materials</span></span>

:::row:::
    :::column:::
<span data-ttu-id="1f7bc-171">マテリアルは、現実的なホログラムを作成するための重要な要素です。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-171">Materials are crucial elements for making realistic holograms.</span></span> <span data-ttu-id="1f7bc-172">適切な視覚的特性を提供することにより、物理環境に合わせて優れた holographic オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-172">By providing proper visual characteristics, you can make compelling holographic objects that can blend well with the physical environment.</span></span> <span data-ttu-id="1f7bc-173">さまざまな種類のユーザー入力のやり取りについて視覚的なフィードバックを提供するために、素材も重要です。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-173">Materials are also important for providing visual feedback for the various types of user input interactions.</span></span>  

<span data-ttu-id="1f7bc-174">[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity) には、視覚的なフィードバックに使用できるさまざまな視覚効果オプションを備えた Mrtk Standard シェーダーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-174">[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides an MRTK Standard Shader with various visual effect options that can be used for visual feedback.</span></span> <span data-ttu-id="1f7bc-175">たとえば、"近接光" プロパティを使用して、ユーザーの指がオブジェクトの表面に近づいたときに光源効果を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="1f7bc-175">For example, you can use 'Proximity Light' property to provide a lighting effect when the user's finger is approaching the object's surface.</span></span> <span data-ttu-id="1f7bc-176">[Mrtk Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)の詳細情報</span><span class="sxs-lookup"><span data-stu-id="1f7bc-176">Learn more about [MRTK Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)</span></span>
    :::column-end:::
        :::column:::
    <span data-ttu-id="1f7bc-177">*ビデオループ: 境界ボックス* 
     ![ との近接度に基づくビジュアルフィードバックの例手書きの視覚的フィードバック](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="1f7bc-177">*Video loop: Example of visual feedback based on proximity to a bounding box*
![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span>

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a><span data-ttu-id="1f7bc-178">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f7bc-178">See also</span></span>
* [<span data-ttu-id="1f7bc-179">ホログラフィック ディスプレイのコンテンツを設計する</span><span class="sxs-lookup"><span data-stu-id="1f7bc-179">Designing content for holographic display</span></span>](designing-content-for-holographic-display.md)
* [<span data-ttu-id="1f7bc-180">色の分離</span><span class="sxs-lookup"><span data-stu-id="1f7bc-180">Color Separation</span></span>](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [<span data-ttu-id="1f7bc-181">ホログラム</span><span class="sxs-lookup"><span data-stu-id="1f7bc-181">Holograms</span></span>](../discover/hologram.md)
* [<span data-ttu-id="1f7bc-182">Microsoft デザイン言語-色</span><span class="sxs-lookup"><span data-stu-id="1f7bc-182">Microsoft Design Language - color</span></span>](https://www.microsoft.com/design/color)
* [<span data-ttu-id="1f7bc-183">ユニバーサル Windows プラットフォーム-色</span><span class="sxs-lookup"><span data-stu-id="1f7bc-183">Universal Windows Platform - color</span></span>](https://docs.microsoft.com/windows/uwp/style/color)
