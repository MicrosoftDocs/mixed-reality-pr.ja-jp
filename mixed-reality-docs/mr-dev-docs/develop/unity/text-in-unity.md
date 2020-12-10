---
title: Unity のテキスト
description: Unity でテキストを表示するには、UI テキストと3D テキストメッシュという2種類のテキストコンポーネントを使用できます。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality、デザイン、コントロール、フォント、タイポグラフィ、ui、ux、Mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: da2932234793a6db160d3bc2bd6dba02318c83bd
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010493"
---
# <a name="text-in-unity"></a><span data-ttu-id="7c798-104">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="7c798-104">Text in Unity</span></span>

<span data-ttu-id="7c798-105">Text は、holographic アプリで最も重要なコンポーネントの1つです。</span><span class="sxs-lookup"><span data-stu-id="7c798-105">Text is one of the most important components in holographic apps.</span></span> <span data-ttu-id="7c798-106">Unity でテキストを表示するには、UI テキスト、3D テキストメッシュ、およびテキストメッシュ Pro の3種類のテキストコンポーネントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7c798-106">To display text in Unity, there are three types of text components you can use—UI Text, 3D Text Mesh, and Text Mesh Pro.</span></span> <span data-ttu-id="7c798-107">既定では、UI テキストと3D テキストメッシュはぼやけて表示され、大きすぎます。</span><span class="sxs-lookup"><span data-stu-id="7c798-107">By default, UI Text and 3D Text Mesh appear blurry and are too large.</span></span> <span data-ttu-id="7c798-108">いくつかの変数を変更すると、HoloLens で管理しやすいサイズの、より鮮明で高品質なテキストが生成されます。</span><span class="sxs-lookup"><span data-stu-id="7c798-108">Changing a few variables results in sharper, higher-quality text with a manageable size in HoloLens.</span></span> <span data-ttu-id="7c798-109">UI テキストと3D テキストメッシュコンポーネントの使用時に適切なディメンションを取得するためにスケールファクターを適用すると、レンダリング品質を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="7c798-109">You can achieve better rendering quality by applying a scaling factor to get proper dimensions when using the UI Text and 3D Text Mesh components.</span></span>

<span data-ttu-id="7c798-110">![シャープで美しいテキストを取得する方法](images/hug-text-02-640px.png)</span><span class="sxs-lookup"><span data-stu-id="7c798-110">![How to get sharp and beautiful text](images/hug-text-02-640px.png)</span></span><br>
<span data-ttu-id="7c798-111">*Unity の既定のテキストがぼやけています*</span><span class="sxs-lookup"><span data-stu-id="7c798-111">*Blurry default text in Unity*</span></span>

## <a name="working-with-unitys-3d-text-text-mesh-and-ui-text"></a><span data-ttu-id="7c798-112">Unity の3D テキスト (テキストメッシュ) と UI テキストの操作</span><span class="sxs-lookup"><span data-stu-id="7c798-112">Working with Unity's 3D Text (Text Mesh) and UI Text</span></span>

<span data-ttu-id="7c798-113">Unity では、シーンに追加されるすべての新しい要素は、1つの Unity 単位のサイズ、または100% の変換スケールを想定しています。</span><span class="sxs-lookup"><span data-stu-id="7c798-113">Unity assumes all new elements added to a scene are one Unity Unit in size, or 100% transform scale.</span></span> <span data-ttu-id="7c798-114">1つの Unity ユニットが HoloLens で約1メートルに変換されます。</span><span class="sxs-lookup"><span data-stu-id="7c798-114">One Unity unit translates to about 1 meter on HoloLens.</span></span> <span data-ttu-id="7c798-115">フォントの場合、3D TextMesh の境界ボックスは、既定では約1メートルの高さになります。</span><span class="sxs-lookup"><span data-stu-id="7c798-115">For fonts, the bounding box for a 3D TextMesh comes in by default at about 1 meter in height.</span></span>

<span data-ttu-id="7c798-116">![Unity でのフォントの操作](images/640px-hug-text-03.png)</span><span class="sxs-lookup"><span data-stu-id="7c798-116">![Working with Fonts in Unity](images/640px-hug-text-03.png)</span></span><br>
<span data-ttu-id="7c798-117">*既定の Unity 3D テキスト (テキストメッシュ) が1つの Unity 単位 (1 メートル) を占める*</span><span class="sxs-lookup"><span data-stu-id="7c798-117">*Default Unity 3D Text (Text Mesh) occupies one Unity Unit, which is 1 meter*</span></span>

<br>

<span data-ttu-id="7c798-118">ほとんどのビジュアルデザイナーはポイントを使用して、実際の世界でのフォントサイズを定義します。</span><span class="sxs-lookup"><span data-stu-id="7c798-118">Most visual designers use points to define font sizes in the real world.</span></span> <span data-ttu-id="7c798-119">1メートルには約 2835 (2, 834.645666399962) のポイントがあります。</span><span class="sxs-lookup"><span data-stu-id="7c798-119">There are about 2835 (2,834.645666399962) points in 1 meter.</span></span> <span data-ttu-id="7c798-120">ポイントシステムの1メーターへの変換と Unity の既定のテキストメッシュのフォントサイズ13に基づき、13を2835で割った単純な数値は 0.0046 (正確には 0.004586111116) になります。これにより、最初に適切な標準スケールが得られます (0.005 に丸めたい場合もあります)。</span><span class="sxs-lookup"><span data-stu-id="7c798-120">Based on the point system conversion to 1 meter and Unity's default Text Mesh font size of 13, the simple math of 13 divided by 2835 equals 0.0046 (0.004586111116 to be exact) which provides a good standard scale to start with (some may wish to round to 0.005).</span></span> <span data-ttu-id="7c798-121">テキストオブジェクトまたはコンテナーをこれらの値に拡張すると、デザインプログラムでフォントサイズを1:1 変換できるだけでなく、エクスペリエンス全体の一貫性を維持するための標準も提供されます。</span><span class="sxs-lookup"><span data-stu-id="7c798-121">Scaling the text object or container to these values will not only allow for the 1:1 conversion of font sizes in a design program, but also provides a standard so you can maintain consistency throughout your experience.</span></span>

<span data-ttu-id="7c798-122">![Unity 3D テキストと UI テキストの値のスケーリング](images/Text_In_Unity_Measurements1.png)</span><span class="sxs-lookup"><span data-stu-id="7c798-122">![Scaling values for the Unity 3D Text and UI Text](images/Text_In_Unity_Measurements1.png)</span></span><br>
<span data-ttu-id="7c798-123">*Unity 3D テキストと UI テキストの値のスケーリング*</span><span class="sxs-lookup"><span data-stu-id="7c798-123">*Scaling values for the Unity 3D Text and UI Text*</span></span>

<br>

<span data-ttu-id="7c798-124">![最適化された値を持つ Unity 3D テキストメッシュ](images/hug-text-05-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7c798-124">![Unity 3D Text Mesh with optimized values](images/hug-text-05-1000px.png)</span></span><br>
<span data-ttu-id="7c798-125">*最適化された値を持つ Unity 3D テキストメッシュ*</span><span class="sxs-lookup"><span data-stu-id="7c798-125">*Unity 3D Text Mesh with optimized values*</span></span>

<br>

<span data-ttu-id="7c798-126">UI またはキャンバスベースのテキスト要素をシーンに追加すると、サイズの不均衡が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="7c798-126">When adding a UI or canvas-based text element to a scene, the size disparity is greater still.</span></span> <span data-ttu-id="7c798-127">2つのサイズの違いは約1000% です。これにより、UI ベースのテキストコンポーネントのスケールファクターが 0.00046 (正確には 0.0004586111116) または0.0005 値のになります。</span><span class="sxs-lookup"><span data-stu-id="7c798-127">The differences in the two sizes are about 1000%, which would bring the scale factor for UI-based text components to 0.00046 (0.0004586111116 to be exact) or 0.0005 for the rounded value.</span></span>

<span data-ttu-id="7c798-128">![最適化された値を含む Unity UI テキスト](images/hug-text-04-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7c798-128">![Unity UI Text with optimized values](images/hug-text-04-1000px.png)</span></span><br>
<span data-ttu-id="7c798-129">*最適化された値を含む Unity UI テキスト*</span><span class="sxs-lookup"><span data-stu-id="7c798-129">*Unity UI Text with optimized values*</span></span>

<br>

>[!NOTE]
><span data-ttu-id="7c798-130">フォントの既定値は、そのフォントのテクスチャサイズ、またはフォントが Unity にインポートされた方法によって影響を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7c798-130">The default value of any font may be affected by the texture size of that font or how the font was imported into Unity.</span></span> <span data-ttu-id="7c798-131">これらのテストは、Unity の既定の Arial フォントおよびその他のインポートされたフォントに基づいて実行されました。</span><span class="sxs-lookup"><span data-stu-id="7c798-131">These tests were performed based on the default Arial font in Unity, as well as one other imported font.</span></span>

## <a name="working-with-text-mesh-pro"></a><span data-ttu-id="7c798-132">Text メッシュ Pro の操作</span><span class="sxs-lookup"><span data-stu-id="7c798-132">Working with Text Mesh Pro</span></span>

<span data-ttu-id="7c798-133">Unity のテキストメッシュ Pro を使用すると、テキストの表示品質を保護できます。</span><span class="sxs-lookup"><span data-stu-id="7c798-133">With Unity's Text Mesh Pro, you can secure the text rendering quality.</span></span> <span data-ttu-id="7c798-134">[署名済み距離フィールド (.sdf)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf)手法を使用した距離に関係なく、鮮明なテキストのアウトラインがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7c798-134">It supports crisp text outlines regardless of the distance using the [Signed Distance Field (SDF)](https://steamcdn-a.akamaihd.net/apps/valve/2007/SIGGRAPH2007_AlphaTestedMagnification.pdf) technique.</span></span> <span data-ttu-id="7c798-135">上記で3D テキストメッシュと UI テキストに使用したのと同じ計算方法を使用して、通常のタイポグラフィポイントで使用する適切なスケーリング値を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="7c798-135">Using the same calculation method that we used above for the 3D Text Mesh and UI Text, we can find the proper scaling values to use with conventional typographic points.</span></span> <span data-ttu-id="7c798-136">サイズが36の既定の3D テキストメッシュ Pro フォントは、2.5 Unity ユニット (2.5 m) の境界サイズを持つため、スケール値0.005 を使用してポイントサイズを取得できます。</span><span class="sxs-lookup"><span data-stu-id="7c798-136">Since the default 3D Text Mesh Pro font with the size of 36 has a bounding size of 2.5 Unity units (2.5 m), we can use a scaling value of 0.005 to get the point size.</span></span> <span data-ttu-id="7c798-137">UI メニューの下にあるテキストメッシュ Pro の既定の境界サイズは 25 Unity ユニット (25 m) です。</span><span class="sxs-lookup"><span data-stu-id="7c798-137">The Text Mesh Pro under the UI menu has a default bounding size of 25 Unity units (25 m).</span></span> <span data-ttu-id="7c798-138">これにより、0.0005 のスケーリング値が得られます。</span><span class="sxs-lookup"><span data-stu-id="7c798-138">This gives us 0.0005 for the scaling value.</span></span>

<span data-ttu-id="7c798-139">![Unity 3D テキストおよび UI の値のスケーリング](images/Text_In_Unity_Measurements2.png)</span><span class="sxs-lookup"><span data-stu-id="7c798-139">![Scaling values for the Unity 3D Text and UI](images/Text_In_Unity_Measurements2.png)</span></span><br>
<span data-ttu-id="7c798-140">*Unity 3D テキストおよび UI の値のスケーリング*</span><span class="sxs-lookup"><span data-stu-id="7c798-140">*Scaling values for the Unity 3D Text and UI*</span></span>

## <a name="recommended-text-size"></a><span data-ttu-id="7c798-141">推奨されるテキストのサイズ</span><span class="sxs-lookup"><span data-stu-id="7c798-141">Recommended text size</span></span>
<span data-ttu-id="7c798-142">ご想像のとおり、PC またはタブレットデバイスで使用する種類のサイズ (通常は 12 ~ 32pt) は、2メートルの距離で小さくなります。</span><span class="sxs-lookup"><span data-stu-id="7c798-142">As you can expect, type sizes that we use on a PC or a tablet device (typically between 12–32pt) look small at a distance of 2 meters.</span></span> <span data-ttu-id="7c798-143">これは、各フォントの特性によって異なりますが、一般的には、ユーザー研究の研究に基づいて、推奨される最小の表示角度と読みやすさのためのフォントの高さは0.35 °-0.4 °/12.21-13.97 mm によって決まります。</span><span class="sxs-lookup"><span data-stu-id="7c798-143">It depends on the characteristics of each font, but in general the recommended minimum viewing angle and the font height for legibility are around 0.35°-0.4°/12.21-13.97 mm based on our user research studies.</span></span> <span data-ttu-id="7c798-144">これは、上で導入されたスケールファクターを使用した約 35-40 pt です。</span><span class="sxs-lookup"><span data-stu-id="7c798-144">It's about 35-40 pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="7c798-145">0.45 m (45 cm) でのほぼの相互作用の場合、フォントの表示角度と高さの最小値は0.4 °-0.5 °/3.14 – 3.9 mm です。</span><span class="sxs-lookup"><span data-stu-id="7c798-145">For the near interaction at 0.45 m (45 cm), the minimum legible font's viewing angle and the height are 0.4°-0.5° / 3.14–3.9mm.</span></span> <span data-ttu-id="7c798-146">これは、上で導入されたスケールファクターを使用した約 9-12 pt です。</span><span class="sxs-lookup"><span data-stu-id="7c798-146">It's about 9-12 pt with the scaling factor introduced above.</span></span>

<span data-ttu-id="7c798-147">![近距離および遠くの相互作用範囲 ](images/typography-distance-1000px.jpg)
 *のコンテンツとほぼの相互作用範囲*</span><span class="sxs-lookup"><span data-stu-id="7c798-147">![Near and far interaction range](images/typography-distance-1000px.jpg)
*Content at near and far interaction range*</span></span>

### <a name="the-minimum-legible-font-size"></a><span data-ttu-id="7c798-148">最小のフォントサイズの最小値</span><span class="sxs-lookup"><span data-stu-id="7c798-148">The minimum legible font size</span></span>
| <span data-ttu-id="7c798-149">距離</span><span class="sxs-lookup"><span data-stu-id="7c798-149">Distance</span></span> | <span data-ttu-id="7c798-150">表示角度</span><span class="sxs-lookup"><span data-stu-id="7c798-150">Viewing angle</span></span> | <span data-ttu-id="7c798-151">テキストの高さ</span><span class="sxs-lookup"><span data-stu-id="7c798-151">Text height</span></span> | <span data-ttu-id="7c798-152">フォント サイズ</span><span class="sxs-lookup"><span data-stu-id="7c798-152">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="7c798-153">45 cm (直接操作距離)</span><span class="sxs-lookup"><span data-stu-id="7c798-153">45 cm (direct manipulation distance)</span></span> | <span data-ttu-id="7c798-154">0.4 °-0.5 °</span><span class="sxs-lookup"><span data-stu-id="7c798-154">0.4°-0.5°</span></span> | <span data-ttu-id="7c798-155">3.14 ~ 3.9 mm</span><span class="sxs-lookup"><span data-stu-id="7c798-155">3.14–3.9mm</span></span> | <span data-ttu-id="7c798-156">8.9 – 11.13 pt</span><span class="sxs-lookup"><span data-stu-id="7c798-156">8.9–11.13pt</span></span> |
| <span data-ttu-id="7c798-157">2 m</span><span class="sxs-lookup"><span data-stu-id="7c798-157">2 m</span></span> | <span data-ttu-id="7c798-158">0.35 °-0.4 °</span><span class="sxs-lookup"><span data-stu-id="7c798-158">0.35°-0.4°</span></span> | <span data-ttu-id="7c798-159">12.21 – 13.97 mm</span><span class="sxs-lookup"><span data-stu-id="7c798-159">12.21–13.97mm</span></span> | <span data-ttu-id="7c798-160">34.63-39.58 pt</span><span class="sxs-lookup"><span data-stu-id="7c798-160">34.63-39.58 pt</span></span> |


### <a name="the-comfortably-legible-font-size"></a><span data-ttu-id="7c798-161">判読しやすいフォントサイズ</span><span class="sxs-lookup"><span data-stu-id="7c798-161">The comfortably legible font size</span></span>
| <span data-ttu-id="7c798-162">距離</span><span class="sxs-lookup"><span data-stu-id="7c798-162">Distance</span></span> | <span data-ttu-id="7c798-163">表示角度</span><span class="sxs-lookup"><span data-stu-id="7c798-163">Viewing angle</span></span> | <span data-ttu-id="7c798-164">テキストの高さ</span><span class="sxs-lookup"><span data-stu-id="7c798-164">Text height</span></span> | <span data-ttu-id="7c798-165">フォント サイズ</span><span class="sxs-lookup"><span data-stu-id="7c798-165">Font size</span></span> |
|---------|---------|---------|---------|
| <span data-ttu-id="7c798-166">45 cm (直接操作距離)</span><span class="sxs-lookup"><span data-stu-id="7c798-166">45 cm (direct manipulation distance)</span></span> | <span data-ttu-id="7c798-167">0.65 °-0.8 °</span><span class="sxs-lookup"><span data-stu-id="7c798-167">0.65°-0.8°</span></span> | <span data-ttu-id="7c798-168">5.1-6.3 mm</span><span class="sxs-lookup"><span data-stu-id="7c798-168">5.1-6.3 mm</span></span> | <span data-ttu-id="7c798-169">14.47-17.8 pt</span><span class="sxs-lookup"><span data-stu-id="7c798-169">14.47-17.8 pt</span></span> |
| <span data-ttu-id="7c798-170">2 m</span><span class="sxs-lookup"><span data-stu-id="7c798-170">2 m</span></span> | <span data-ttu-id="7c798-171">0.6 °-0.75 °</span><span class="sxs-lookup"><span data-stu-id="7c798-171">0.6°-0.75°</span></span> | <span data-ttu-id="7c798-172">20.9-26.2 mm</span><span class="sxs-lookup"><span data-stu-id="7c798-172">20.9-26.2 mm</span></span> | <span data-ttu-id="7c798-173">59.4-74.2 pt</span><span class="sxs-lookup"><span data-stu-id="7c798-173">59.4-74.2 pt</span></span> |

<span data-ttu-id="7c798-174">Segoe UI (Windows の既定のフォント) は、ほとんどの場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="7c798-174">Segoe UI (the default font for Windows) works well in most cases.</span></span> <span data-ttu-id="7c798-175">ただし、薄い垂直方向のストロークはバイブレーションので、読みやすさが低下するので、小さいサイズの明るいフォントや半明るいフォントファミリは使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="7c798-175">However, avoid using light or semi light font families in small size since thin vertical strokes will vibrate and it will degrade the legibility.</span></span> <span data-ttu-id="7c798-176">ストロークの太さが十分にある最新のフォントがうまく機能します。</span><span class="sxs-lookup"><span data-stu-id="7c798-176">Modern fonts with enough stroke thickness work well.</span></span> <span data-ttu-id="7c798-177">たとえば、Helvetica, と Arial は、標準または太字の重みを使用して HoloLens で読みやすくなっています。</span><span class="sxs-lookup"><span data-stu-id="7c798-177">For example, Helvetica and Arial look gorgeous and are legible in HoloLens with regular or bold weights.</span></span>

<span data-ttu-id="7c798-178">![角度 ](images/Text_In_Unity_ViewingAngle.jpg)
 *表示距離、角度、およびテキストの高さ* を表示する</span><span class="sxs-lookup"><span data-stu-id="7c798-178">![Viewing Angle](images/Text_In_Unity_ViewingAngle.jpg)
*Viewing distance, angle, and text height*</span></span>

## <a name="text-with-mixed-reality-toolkit-v2"></a><span data-ttu-id="7c798-179">Mixed Reality Toolkit v2 を使用したテキスト</span><span class="sxs-lookup"><span data-stu-id="7c798-179">Text with Mixed Reality Toolkit v2</span></span>

### <a name="sharp-text-rendering-quality-with-proper-dimension"></a><span data-ttu-id="7c798-180">適切なディメンションを使用した鋭いテキストレンダリング品質</span><span class="sxs-lookup"><span data-stu-id="7c798-180">Sharp text rendering quality with proper dimension</span></span>

<span data-ttu-id="7c798-181">これらのスケールファクターに基づき、 [UI テキストと3D テキストメッシュを使用してテキスト prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)を作成しました。</span><span class="sxs-lookup"><span data-stu-id="7c798-181">Based on these scaling factors, we have created [text prefabs with UI Text and 3D Text Mesh](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text).</span></span> <span data-ttu-id="7c798-182">開発者は、これらの prefabs を使用して、鋭いテキストと一貫したフォントサイズを取得できます。</span><span class="sxs-lookup"><span data-stu-id="7c798-182">Developers can use these prefabs to get sharp text and consistent font size.</span></span>

<span data-ttu-id="7c798-183">![適切なディメンションを使用した鋭いテキストレンダリング品質](images/hug-text-06-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7c798-183">![Sharp text rendering quality with proper dimension](images/hug-text-06-1000px.png)</span></span><br>
<span data-ttu-id="7c798-184">*適切なディメンションを使用した鋭いテキストレンダリング品質*</span><span class="sxs-lookup"><span data-stu-id="7c798-184">*Sharp text rendering quality with proper dimension*</span></span>

### <a name="shader-with-occlusion-support"></a><span data-ttu-id="7c798-185">オクルージョンサポート付きのシェーダー</span><span class="sxs-lookup"><span data-stu-id="7c798-185">Shader with occlusion support</span></span>

<span data-ttu-id="7c798-186">Unity の既定のフォントマテリアルでは、オクルージョンはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7c798-186">Unity's default font material doesn't support occlusion.</span></span> <span data-ttu-id="7c798-187">このため、既定では、オブジェクトの背後にテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7c798-187">Because of this, you'll see the text behind the objects by default.</span></span> <span data-ttu-id="7c798-188">[遮蔽をサポートする](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader)単純なシェーダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7c798-188">We've included a simple [shader that supports the occlusion](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/StandardAssets/Shaders/Text3DShader.shader).</span></span> <span data-ttu-id="7c798-189">次の画像は、既定のフォントマテリアル (左側) が付いたテキストと、適切な遮蔽 (right) のテキストを示しています。</span><span class="sxs-lookup"><span data-stu-id="7c798-189">The image below shows the text with default font material (left) and the text with proper occlusion (right).</span></span>

<span data-ttu-id="7c798-190">![オクルージョンサポート付きのシェーダー](images/hug-text-07-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7c798-190">![Shader with occlusion support](images/hug-text-07-1000px.png)</span></span><br>
<span data-ttu-id="7c798-191">*オクルージョンサポート付きのシェーダー*</span><span class="sxs-lookup"><span data-stu-id="7c798-191">*Shader with occlusion support*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="7c798-192">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="7c798-192">Next Development Checkpoint</span></span>

<span data-ttu-id="7c798-193">Unity の開発に関する体験に従っている場合は、MRTK コアのビルディングブロックを調べています。</span><span class="sxs-lookup"><span data-stu-id="7c798-193">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="7c798-194">ここから、次のビルディングブロックに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="7c798-194">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c798-195">音声入力</span><span class="sxs-lookup"><span data-stu-id="7c798-195">Voice input</span></span>](voice-input-in-unity.md)

<span data-ttu-id="7c798-196">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="7c798-196">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c798-197">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="7c798-197">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="7c798-198">いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="7c798-198">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="see-also"></a><span data-ttu-id="7c798-199">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c798-199">See also</span></span>
* [<span data-ttu-id="7c798-200">MRTK のテキスト Prefab</span><span class="sxs-lookup"><span data-stu-id="7c798-200">Text Prefab in the MRTK</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/SDK/StandardAssets/Prefabs/Text)
* [<span data-ttu-id="7c798-201">文字体裁</span><span class="sxs-lookup"><span data-stu-id="7c798-201">Typography</span></span>](../../design/typography.md)
