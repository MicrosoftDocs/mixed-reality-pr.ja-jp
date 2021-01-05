---
title: タイポグラフィ
description: テキストは、アプリのエクスペリエンスに情報を提供するための重要な要素です。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality、デザイン、スタイル、フォント、タイポグラフィ、ui、ux、テキスト、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット、HoloLens
ms.openlocfilehash: 09e0e6029011fdd7fda793f6b6645cb3744baa3b
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848140"
---
# <a name="typography"></a><span data-ttu-id="39a10-104">文字体裁</span><span class="sxs-lookup"><span data-stu-id="39a10-104">Typography</span></span>

![HoloLens でのタイポグラフィの例](images/typography-cover.png)<br>


<span data-ttu-id="39a10-106">テキストは、アプリのエクスペリエンスに情報を提供するための重要な要素です。</span><span class="sxs-lookup"><span data-stu-id="39a10-106">Text is an important element for delivering information in your app experience.</span></span> <span data-ttu-id="39a10-107">2D 画面の文字体裁と同じように、明確で読みやすくすることを目指します。</span><span class="sxs-lookup"><span data-stu-id="39a10-107">Just like typography on 2D screens, the goal is to be clear and readable.</span></span> <span data-ttu-id="39a10-108">混合現実の3次元の側面により、テキストと全体的なユーザーエクスペリエンスをさらに大きくすることができます。</span><span class="sxs-lookup"><span data-stu-id="39a10-108">With the three-dimensional aspect of mixed reality, there's an opportunity to affect the text and the overall user experience in an even greater way.</span></span>

<span data-ttu-id="39a10-109">3D で型について話をするときは、押し出し、容量の3D テキストを考えてみる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="39a10-109">When we talk about type in 3D, we tend to think extruded, volumetric 3D text.</span></span> <span data-ttu-id="39a10-110">一部ののロゴデザインやその他の限られたアプリケーションを除き、押し出しテキストはテキストの読みやすさを低下させる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="39a10-110">Except for some logotype designs and a few other limited applications, extruded text tends to degrade the readability of the text.</span></span> <span data-ttu-id="39a10-111">3D のエクスペリエンスを設計している場合でも、読みやすく、読みやすくなるため、型に2D を使用します。</span><span class="sxs-lookup"><span data-stu-id="39a10-111">Even though we're designing experiences for 3D, we use 2D for the type because it's more legible and easier to read.</span></span>

<span data-ttu-id="39a10-112">HoloLens では、加法色システムに基づいた光を使用したホログラムで型が構築されます。</span><span class="sxs-lookup"><span data-stu-id="39a10-112">In HoloLens, type is constructed with holograms using light based on the additive color system.</span></span> <span data-ttu-id="39a10-113">他のホログラムと同じように、type を実際の環境に配置して、世界中でロックし、任意の角度から観察することができます。</span><span class="sxs-lookup"><span data-stu-id="39a10-113">Just like other holograms, type can be placed in the actual environment where it can be world locked and observed from any angle.</span></span> <span data-ttu-id="39a10-114">型と環境の間の [視差](https://en.wikipedia.org/wiki/Parallax) 効果によっても、エクスペリエンスの深さが向上します。</span><span class="sxs-lookup"><span data-stu-id="39a10-114">The [parallax](https://en.wikipedia.org/wiki/Parallax) effect between the type and the environment also adds depth to the experience.</span></span>

## <a name="typography-in-mixed-reality"></a><span data-ttu-id="39a10-115">Mixed reality でのタイポグラフィ</span><span class="sxs-lookup"><span data-stu-id="39a10-115">Typography in mixed reality</span></span>

<span data-ttu-id="39a10-116">混合現実の表記規則は、他の場所とは異なります。</span><span class="sxs-lookup"><span data-stu-id="39a10-116">Typographic rules in mixed reality are no different from anywhere else.</span></span> <span data-ttu-id="39a10-117">物理的な世界と仮想環境の両方のテキストは、読みやすく、読みやすいものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="39a10-117">Text in both the physical world and the virtual world needs to be legible and readable.</span></span> <span data-ttu-id="39a10-118">テキストは、壁上にあるか、物理オブジェクトに重ねて表示されます。</span><span class="sxs-lookup"><span data-stu-id="39a10-118">Text could be on a wall or superimposed on a physical object.</span></span> <span data-ttu-id="39a10-119">デジタルユーザーインターフェイスと共に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="39a10-119">It could be floating along with a digital user interface.</span></span> <span data-ttu-id="39a10-120">どのような状況でも、読み取りと認識に同じタイポグラフィ規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="39a10-120">Whatever the context, we apply the same typographic rules for reading and recognition.</span></span>

### <a name="create-clear-hierarchy"></a><span data-ttu-id="39a10-121">明確階層の作成</span><span class="sxs-lookup"><span data-stu-id="39a10-121">Create clear hierarchy</span></span>

<span data-ttu-id="39a10-122">さまざまな種類のサイズと重みを使用して、コントラストと階層を作成します。</span><span class="sxs-lookup"><span data-stu-id="39a10-122">Build contrast and hierarchy by using different type sizes and weights.</span></span> <span data-ttu-id="39a10-123">アプリのエクスペリエンス全体で型の傾斜を定義し、それに従うことで、一貫性のある情報階層で優れたユーザーエクスペリエンスを実現できます。</span><span class="sxs-lookup"><span data-stu-id="39a10-123">Defining a type ramp and following it throughout the app experience will provide a great user experience with consistent information hierarchy.</span></span>

<span data-ttu-id="39a10-124">![型の傾斜の例](images/typography-ramp-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="39a10-124">![Type ramp examples](images/typography-ramp-1000px.jpg)</span></span><br>
<span data-ttu-id="39a10-125">*アプリケーションエクスペリエンス全体で、型の傾斜を定義し、それに従う*</span><span class="sxs-lookup"><span data-stu-id="39a10-125">*Define your type ramp and follow it throughout the app experience*</span></span>

### <a name="limit-your-fonts"></a><span data-ttu-id="39a10-126">フォントを制限する</span><span class="sxs-lookup"><span data-stu-id="39a10-126">Limit your fonts</span></span>

<span data-ttu-id="39a10-127">1つのコンテキストで2つ以上の異なるフォントファミリを使用することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="39a10-127">Avoid using more than two different font families in a single context.</span></span> <span data-ttu-id="39a10-128">フォントが多すぎると、使いやすさと一貫性が損なわれ、情報を使用することが難しくなります。</span><span class="sxs-lookup"><span data-stu-id="39a10-128">Too many fonts will break the harmony and consistency of your experience and make it harder to consume information.</span></span> <span data-ttu-id="39a10-129">HoloLens では、情報は物理環境の上に重なっているため、使用するフォントスタイルが多すぎるとエクスペリエンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="39a10-129">In HoloLens, since the information is overlaid on top of the physical environment, using too many font styles will degrade the experience.</span></span> <span data-ttu-id="39a10-130">Segoe UI は、すべての Microsoft デジタルデザインのフォントです。</span><span class="sxs-lookup"><span data-stu-id="39a10-130">Segoe UI is the font for all Microsoft digital designs.</span></span> <span data-ttu-id="39a10-131">これは、Windows Mixed Reality シェルで一貫して使用されます。</span><span class="sxs-lookup"><span data-stu-id="39a10-131">It's used consistently in the Windows Mixed Reality shell.</span></span> <span data-ttu-id="39a10-132">Segoe UI フォントファイルは、 [Windows design toolkit のページ](https://docs.microsoft.com/windows/uwp/design-downloads/)からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="39a10-132">You can download the Segoe UI font file from the [Windows design toolkit page](https://docs.microsoft.com/windows/uwp/design-downloads/).</span></span>

[<span data-ttu-id="39a10-133">Segoe UI タイプフェイスに関する詳細情報</span><span class="sxs-lookup"><span data-stu-id="39a10-133">More information about the Segoe UI typeface</span></span>](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a><span data-ttu-id="39a10-134">細いフォントの太さを避ける</span><span class="sxs-lookup"><span data-stu-id="39a10-134">Avoid thin font weights</span></span>

<span data-ttu-id="39a10-135">42 pt 未満の型サイズに対しては薄いまたは semilight のフォントの重みを使用しないでください。薄い縦線のストロークはバイブレーションで、読みにくくなります。</span><span class="sxs-lookup"><span data-stu-id="39a10-135">Avoid using light or semilight font weights for type sizes under 42 pt because thin vertical strokes will vibrate and degrade legibility.</span></span> <span data-ttu-id="39a10-136">ストロークの太さが十分にある最新のフォントがうまく機能します。</span><span class="sxs-lookup"><span data-stu-id="39a10-136">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="39a10-137">たとえば、Helvetica, と Arial は、標準または太字の重みを使用して HoloLens で判読できます。</span><span class="sxs-lookup"><span data-stu-id="39a10-137">For example, Helvetica and Arial are legible in HoloLens using regular or bold weights.</span></span>

### <a name="color"></a><span data-ttu-id="39a10-138">Color</span><span class="sxs-lookup"><span data-stu-id="39a10-138">Color</span></span>

<span data-ttu-id="39a10-139">HoloLens では、ホログラムは加法の光源システムを使用して構築されるため、白のテキストは非常に読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="39a10-139">In HoloLens, since the holograms are constructed with an additive light system, white text is highly legible.</span></span> <span data-ttu-id="39a10-140">ホワイトテキストの例については、[スタート] メニューとアプリバーを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39a10-140">You can find examples of white text on the Start menu and the App bar.</span></span> <span data-ttu-id="39a10-141">HoloLens でバックプレートを使用しなくても白のテキストは適切に機能しますが、複雑な物理的背景によって型が読みづらくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="39a10-141">Even though white text works well without a back plate on HoloLens, a complex physical background could make the type difficult to read.</span></span> <span data-ttu-id="39a10-142">ユーザーのフォーカスを改善し、物理的な背景からの邪魔を最小限に抑えるために、暗い色または色の裏面に白いテキストを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="39a10-142">We recommend using white text on a dark or colored back plate to improve the user's focus and minimize the distraction from a physical background.</span></span>

<br>


<span data-ttu-id="39a10-143">![ダークカラーまたは色付きの背景プレートでは、白いテキストを使用することをお勧めします。 ](images/typography-whiteonblack2-1000px.jpg)
*ダークカラーまたは色付きの背景プレートの白いテキストの例。*</span><span class="sxs-lookup"><span data-stu-id="39a10-143">![We recommend using white text on a dark or colored back plate.](images/typography-whiteonblack2-1000px.jpg)
*Examples of white text on a dark or colored back plate.*</span></span>
<br>

<span data-ttu-id="39a10-144">ダークテキストを使用するには、明るい背景プレートを使用して読み取り可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="39a10-144">To use dark text, you should use a bright back plate to make it readable.</span></span> <span data-ttu-id="39a10-145">加法色のシステムでは、黒は透明として表示されます。</span><span class="sxs-lookup"><span data-stu-id="39a10-145">In additive color systems, black is displayed as transparent.</span></span> <span data-ttu-id="39a10-146">これは、色付きの背景プレートのない黒いテキストが表示されないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="39a10-146">This means you won't see the black text without a colored back plate.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="39a10-147">![黒と黒の白いテキストの例](images/typography-whiteonblack.png)</span><span class="sxs-lookup"><span data-stu-id="39a10-147">![Examples of white on black and black on white text](images/typography-whiteonblack.png)</span></span><br>
        <span data-ttu-id="39a10-148">*黒と黒の白いテキストの例*</span><span class="sxs-lookup"><span data-stu-id="39a10-148">*Examples of white on black and black on white text*</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="39a10-149">![システムアプリの黒いテキストの例-ストアと設定](images/640px-typography-blackonwhite.jpg)</span><span class="sxs-lookup"><span data-stu-id="39a10-149">![Examples of black text in the system apps - Store and Settings](images/640px-typography-blackonwhite.jpg)</span></span><br>
        <span data-ttu-id="39a10-150">*システムアプリの黒いテキストの例-ストアと設定*</span><span class="sxs-lookup"><span data-stu-id="39a10-150">*Examples of black text in the system apps - Store and Settings*</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a><span data-ttu-id="39a10-151">推奨されるフォントサイズ</span><span class="sxs-lookup"><span data-stu-id="39a10-151">Recommended font size</span></span>

<span data-ttu-id="39a10-152">ご想像のとおり、PC またはタブレットデバイスで使用する種類のサイズ (通常は 12 ~ 32pt) は、2メートルの距離で小さくなります。</span><span class="sxs-lookup"><span data-stu-id="39a10-152">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look small at a distance of 2 meters.</span></span> <span data-ttu-id="39a10-153">これは、各フォントの特性によって異なりますが、一般的には、ユーザー研究の研究に基づいて、推奨される最小の表示角度と読みやすさのためのフォントの高さは0.35 °-0.4 °/12.21-13.97 mm によって決まります。</span><span class="sxs-lookup"><span data-stu-id="39a10-153">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97 mm based on our user research studies.</span></span> <span data-ttu-id="39a10-154">[Unity ページのテキスト](../develop/unity/text-in-unity.md)で導入されたスケールファクターを使用した約 35-40 pt です。</span><span class="sxs-lookup"><span data-stu-id="39a10-154">It's about 35-40 pt with the scaling factor introduced in [Text in Unity](../develop/unity/text-in-unity.md) page.</span></span> 

<span data-ttu-id="39a10-155">0.45 m (45 cm) でのほぼの相互作用の場合、フォントの表示角度と高さの最小値は0.4 °-0.5 °/3.14 – 3.9 mm です。</span><span class="sxs-lookup"><span data-stu-id="39a10-155">For the near interaction at 0.45 m(45 cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="39a10-156">これは、 [Unity のテキスト](../develop/unity/text-in-unity.md)で導入されたスケールファクターを使用した約 9-12 pt です。</span><span class="sxs-lookup"><span data-stu-id="39a10-156">It's about 9-12 pt with the scaling factor introduced in [Text in Unity](../develop/unity/text-in-unity.md).</span></span>

<span data-ttu-id="39a10-157">![近距離および遠くの相互作用範囲 ](images/typography-distance-1000px.jpg)
 *のコンテンツとほぼの相互作用範囲*</span><span class="sxs-lookup"><span data-stu-id="39a10-157">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="39a10-158">最小のフォントサイズの最小値</span><span class="sxs-lookup"><span data-stu-id="39a10-158">The minimum legible font size</span></span>

| <span data-ttu-id="39a10-159">距離</span><span class="sxs-lookup"><span data-stu-id="39a10-159">Distance</span></span> | <span data-ttu-id="39a10-160">表示角度</span><span class="sxs-lookup"><span data-stu-id="39a10-160">Viewing angle</span></span> | <span data-ttu-id="39a10-161">テキストの高さ</span><span class="sxs-lookup"><span data-stu-id="39a10-161">Text height</span></span> | <span data-ttu-id="39a10-162">フォントサイズ \* \*</span><span class="sxs-lookup"><span data-stu-id="39a10-162">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="39a10-163">45 cm (直接操作距離)</span><span class="sxs-lookup"><span data-stu-id="39a10-163">45 cm (direct manipulation distance)</span></span> | <span data-ttu-id="39a10-164">0.4 °-0.5 °</span><span class="sxs-lookup"><span data-stu-id="39a10-164">0.4°-0.5°</span></span> | <span data-ttu-id="39a10-165">3.14 ~ 3.9 mm</span><span class="sxs-lookup"><span data-stu-id="39a10-165">3.14–3.9mm</span></span> | <span data-ttu-id="39a10-166">8.9 – 11.13 pt</span><span class="sxs-lookup"><span data-stu-id="39a10-166">8.9–11.13pt</span></span> |
| <span data-ttu-id="39a10-167">2 m</span><span class="sxs-lookup"><span data-stu-id="39a10-167">2 m</span></span> | <span data-ttu-id="39a10-168">0.35 °-0.4 °</span><span class="sxs-lookup"><span data-stu-id="39a10-168">0.35°-0.4°</span></span> | <span data-ttu-id="39a10-169">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="39a10-169">12.21–13.97mm</span></span> | <span data-ttu-id="39a10-170">34.63-39.58 pt</span><span class="sxs-lookup"><span data-stu-id="39a10-170">34.63-39.58 pt</span></span> |

### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="39a10-171">判読しやすいフォントサイズ</span><span class="sxs-lookup"><span data-stu-id="39a10-171">The comfortably legible font size</span></span>

| <span data-ttu-id="39a10-172">距離</span><span class="sxs-lookup"><span data-stu-id="39a10-172">Distance</span></span> | <span data-ttu-id="39a10-173">表示角度</span><span class="sxs-lookup"><span data-stu-id="39a10-173">Viewing angle</span></span> | <span data-ttu-id="39a10-174">テキストの高さ</span><span class="sxs-lookup"><span data-stu-id="39a10-174">Text height</span></span> | <span data-ttu-id="39a10-175">フォントサイズ \* \*</span><span class="sxs-lookup"><span data-stu-id="39a10-175">Font size\*\*</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="39a10-176">45 cm (直接操作距離)</span><span class="sxs-lookup"><span data-stu-id="39a10-176">45 cm (direct manipulation distance)</span></span> | <span data-ttu-id="39a10-177">0.65 °-0.8 °</span><span class="sxs-lookup"><span data-stu-id="39a10-177">0.65°-0.8°</span></span> | <span data-ttu-id="39a10-178">5.1-6.3 mm</span><span class="sxs-lookup"><span data-stu-id="39a10-178">5.1-6.3 mm</span></span> | <span data-ttu-id="39a10-179">14.47-17.8 pt</span><span class="sxs-lookup"><span data-stu-id="39a10-179">14.47-17.8 pt</span></span> |
| <span data-ttu-id="39a10-180">2 m</span><span class="sxs-lookup"><span data-stu-id="39a10-180">2 m</span></span> | <span data-ttu-id="39a10-181">0.6 °-0.75 °</span><span class="sxs-lookup"><span data-stu-id="39a10-181">0.6°-0.75°</span></span> | <span data-ttu-id="39a10-182">20.9-26.2 mm</span><span class="sxs-lookup"><span data-stu-id="39a10-182">20.9-26.2 mm</span></span> | <span data-ttu-id="39a10-183">59.4-74.2 pt</span><span class="sxs-lookup"><span data-stu-id="39a10-183">59.4-74.2 pt</span></span> |


<span data-ttu-id="39a10-184">Segoe UI (Windows の既定のフォント) は、ほとんどの場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="39a10-184">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="39a10-185">薄い垂直方向のストロークはバイブレーションので、読みやすさが低下するため、小さいサイズのライトフォントまたはセミライトフォントファミリは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="39a10-185">Avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="39a10-186">ストロークの太さが十分にある最新のフォントがうまく機能します。</span><span class="sxs-lookup"><span data-stu-id="39a10-186">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="39a10-187">たとえば、Helvetica, と Arial は、標準または太字の重みを使用して HoloLens で読みやすくなっています。</span><span class="sxs-lookup"><span data-stu-id="39a10-187">For example, Helvetica and Arial look gorgeous and are legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="39a10-188">**Unity でのテキストサイズの計算の詳細については、「 [unity のテキスト](../develop/unity/text-in-unity.md)」を参照してください。**</span><span class="sxs-lookup"><span data-stu-id="39a10-188">**For more detailed information about text size calculation in Unity, refer to [Text in Unity](../develop/unity/text-in-unity.md)**</span></span>

<span data-ttu-id="39a10-189">![角度 ](images/Text_In_Unity_ViewingAngle.jpg)
 *表示距離、角度、およびテキストの高さ* を表示する</span><span class="sxs-lookup"><span data-stu-id="39a10-189">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

<br>

---

## <a name="resources"></a><span data-ttu-id="39a10-190">リソース</span><span class="sxs-lookup"><span data-stu-id="39a10-190">Resources</span></span>

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[<span data-ttu-id="39a10-191">Segoe フォント</span><span class="sxs-lookup"><span data-stu-id="39a10-191">Segoe fonts</span></span>](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    <span data-ttu-id="39a10-192">(Zip ファイル)</span><span class="sxs-lookup"><span data-stu-id="39a10-192">(Zip file)</span></span><br>
    ### <a name="hololens-fontbr"></a>[<span data-ttu-id="39a10-193">HoloLens フォント</span><span class="sxs-lookup"><span data-stu-id="39a10-193">HoloLens font</span></span>](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    <span data-ttu-id="39a10-194">(Zip ファイル)</span><span class="sxs-lookup"><span data-stu-id="39a10-194">(Zip file)</span></span><br>
    <br>
    <span data-ttu-id="39a10-195">*Image: HoloLens フォントは、Windows Mixed Reality で使用される記号のグリフを提供します。*</span><span class="sxs-lookup"><span data-stu-id="39a10-195">*Image: The HoloLens font gives you the symbol glyphs used in Windows Mixed Reality.*</span></span>
    :::column-end:::
        :::column:::
        ![HoloLens フォントは、Windows Mixed Reality で使用される記号のグリフを提供します。](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---

## <a name="see-also"></a><span data-ttu-id="39a10-197">関連項目</span><span class="sxs-lookup"><span data-stu-id="39a10-197">See also</span></span>

* [<span data-ttu-id="39a10-198">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="39a10-198">Text in Unity</span></span>](../develop/unity/text-in-unity.md)
* [<span data-ttu-id="39a10-199">色、ライト、素材</span><span class="sxs-lookup"><span data-stu-id="39a10-199">Color, light, and materials</span></span>](../color,-light-and-materials.md)
