---
title: 3D アプリ起動ツールの設計ガイダンス
description: 3D アプリランチャーは、アプリを起動するために選択できる、ユーザーの mixed reality ハウスの "物理" オブジェクトです。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 設計, 3D アプリランチャー, イマーシブヘッドセット, ライブキューブ
ms.openlocfilehash: 884d05b8b8ef7e15f5c65a411cf500b0d4dc598c
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686554"
---
# <a name="3d-app-launcher-design-guidance"></a><span data-ttu-id="8139a-104">3D アプリ起動ツールの設計ガイダンス</span><span class="sxs-lookup"><span data-stu-id="8139a-104">3D app launcher design guidance</span></span>

<span data-ttu-id="8139a-105">Windows Mixed Reality イマーシブ (VR) ヘッドセットを使用する場合は、山と水で囲まれた崖に家として視覚化された Windows Mixed Reality ホームを入力します (ただし、 [他の環境を選択して独自に作成](../design/add-custom-home-environments.md)することもできます)。</span><span class="sxs-lookup"><span data-stu-id="8139a-105">When you put on a Windows Mixed Reality immersive (VR) headset, you enter the Windows Mixed Reality home, visualized as a house on a cliff surrounded by mountains and water (though you can [choose other environments and even create your own](../design/add-custom-home-environments.md)).</span></span> <span data-ttu-id="8139a-106">このホームの領域内では、ユーザーは、必要に応じて、必要な3D オブジェクトとアプリを自由に配置して整理することができます。</span><span class="sxs-lookup"><span data-stu-id="8139a-106">Within the space of this home, a user is free to arrange and organize the 3D objects and apps that they care about any way they want.</span></span> <span data-ttu-id="8139a-107">**3d アプリランチャー** は、アプリを起動するために選択できる、ユーザーの mixed reality ハウスの "物理" オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="8139a-107">A **3D app launcher** is a “physical” object in the user’s mixed reality house that they can select to launch an app.</span></span>

<span data-ttu-id="8139a-108">![例: Floaty 鳥3D アプリランチャー](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8139a-108">![Example: Floaty Bird 3D app launcher](images/20171016-151526-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="8139a-109">*Floaty 鳥3D アプリランチャーの例 (架空のアプリ)*</span><span class="sxs-lookup"><span data-stu-id="8139a-109">*Floaty Bird 3D app launcher example (fictional app)*</span></span>

## <a name="3d-app-launcher-creation-process"></a><span data-ttu-id="8139a-110">3D アプリランチャー作成プロセス</span><span class="sxs-lookup"><span data-stu-id="8139a-110">3D app launcher creation process</span></span>

<span data-ttu-id="8139a-111">3D アプリランチャーを作成するには、次の3つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="8139a-111">There are 3 steps to creating a 3D app launcher:</span></span>

1. <span data-ttu-id="8139a-112">設計と concepting (この記事)</span><span class="sxs-lookup"><span data-stu-id="8139a-112">Designing and concepting (this article)</span></span>
2. [<span data-ttu-id="8139a-113">モデリングとエクスポート</span><span class="sxs-lookup"><span data-stu-id="8139a-113">Modeling and exporting</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. <span data-ttu-id="8139a-114">アプリケーションに統合します。</span><span class="sxs-lookup"><span data-stu-id="8139a-114">Integrating it into your application:</span></span>
    * [<span data-ttu-id="8139a-115">UWP アプリ</span><span class="sxs-lookup"><span data-stu-id="8139a-115">UWP apps</span></span>](implementing-3d-app-launchers.md)
    * [<span data-ttu-id="8139a-116">Win32 アプリ</span><span class="sxs-lookup"><span data-stu-id="8139a-116">Win32 apps</span></span>](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a><span data-ttu-id="8139a-117">設計概念</span><span class="sxs-lookup"><span data-stu-id="8139a-117">Design concepts</span></span>

### <a name="fantastic-yet-familiar"></a><span data-ttu-id="8139a-118">非常になじみのあるすばらしい</span><span class="sxs-lookup"><span data-stu-id="8139a-118">Fantastic yet familiar</span></span>

<span data-ttu-id="8139a-119">アプリランチャーが存在する Windows Mixed Reality 環境は、パート fantastical/sci です。</span><span class="sxs-lookup"><span data-stu-id="8139a-119">The Windows Mixed Reality environment your app launcher lives in is part familiar, part fantastical/sci-fi.</span></span> <span data-ttu-id="8139a-120">最適なランチャーは、この世界の規則に従います。</span><span class="sxs-lookup"><span data-stu-id="8139a-120">The best launchers follow the rules of this world.</span></span> <span data-ttu-id="8139a-121">アプリから使い慣れた代表的なオブジェクトを取得しながら、実際の現実のルールの一部を曲げられる方法を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="8139a-121">Think of how you can take a familiar, representative object from your app, but bend some of the rules of actual reality.</span></span> <span data-ttu-id="8139a-122">マジックが生成されます。</span><span class="sxs-lookup"><span data-stu-id="8139a-122">Magic will result.</span></span>

### <a name="intuitive"></a><span data-ttu-id="8139a-123">にくい</span><span class="sxs-lookup"><span data-stu-id="8139a-123">Intuitive</span></span>

<span data-ttu-id="8139a-124">アプリランチャーを確認するときは、アプリを起動する目的を明確にする必要があり、混乱を招くことはありません。</span><span class="sxs-lookup"><span data-stu-id="8139a-124">When you look at your app launcher, its purpose - to launch your app - should be obvious and shouldn’t cause any confusion.</span></span> <span data-ttu-id="8139a-125">たとえば、décor が崖家の1つの部分と混同されないように、ランチャーが明らかであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8139a-125">For example, be sure your launcher is an obvious-enough representative of your app that it won’t be confused for a piece of decor in the Cliff House.</span></span> <span data-ttu-id="8139a-126">アプリランチャーは、ユーザーにタッチまたは選択を招待する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8139a-126">Your app launcher should invite people to touch/select it.</span></span>

<span data-ttu-id="8139a-127">![例: 新しいメモ3D アプリランチャー](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8139a-127">![Example: Fresh Note 3D app launcher](images/20171016-152145-mixedreality1-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="8139a-128">*新鮮ノート3D アプリランチャーの例 (架空のアプリ)*</span><span class="sxs-lookup"><span data-stu-id="8139a-128">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="home-scale"></a><span data-ttu-id="8139a-129">ホームスケール</span><span class="sxs-lookup"><span data-stu-id="8139a-129">Home scale</span></span>

<span data-ttu-id="8139a-130">3D アプリランチャーは崖家に存在し、その既定のサイズは、空間内の他の "物理" オブジェクトと同じ意味になります。</span><span class="sxs-lookup"><span data-stu-id="8139a-130">3D app launchers live in the Cliff House and their default size should make sense with the other “physical” objects in the space.</span></span> <span data-ttu-id="8139a-131">家の植物や家具など、ランチャーを設置している場合は、自宅でも、サイズにも気が付いています。</span><span class="sxs-lookup"><span data-stu-id="8139a-131">If you place your launcher beside, say, a house plant or some furniture, it should feel at home, size-wise.</span></span> <span data-ttu-id="8139a-132">開始点としては、どのように表示されるかを確認することをお勧めします。ただし、ユーザーが必要に応じてスケールアップまたはスケールダウンできることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8139a-132">A good starting point is to see how it looks at 30 cubic centimeters, but remember that users can scale it up or down if they like.</span></span>

### <a name="own-able"></a><span data-ttu-id="8139a-133">独自の機能</span><span class="sxs-lookup"><span data-stu-id="8139a-133">Own-able</span></span>

<span data-ttu-id="8139a-134">アプリランチャーは、ユーザーが自分のスペースにあるように感じられるオブジェクトのように感じます。</span><span class="sxs-lookup"><span data-stu-id="8139a-134">The app launcher should feel like an object a person would be excited to have in their space.</span></span> <span data-ttu-id="8139a-135">これらの機能は実質的にこのような処理を行っているので、ランチャーは、ユーザーが近くにいると思っていたようなものと考える必要があります。</span><span class="sxs-lookup"><span data-stu-id="8139a-135">They’ll be virtually surrounding themselves with these things, so the launcher should feel like something the user thought was desirable enough to seek out and keep nearby.</span></span>

<span data-ttu-id="8139a-136">![例: Astro ワープ3D アプリランチャー](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8139a-136">![Example: Astro Warp 3D app launcher](images/20171016-132936-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="8139a-137">*Astro ワープ3D アプリランチャーの例 (架空のアプリ)*</span><span class="sxs-lookup"><span data-stu-id="8139a-137">*Astro Warp 3D app launcher example (fictional app)*</span></span>

### <a name="recognizable"></a><span data-ttu-id="8139a-138">認識可能な</span><span class="sxs-lookup"><span data-stu-id="8139a-138">Recognizable</span></span>

<span data-ttu-id="8139a-139">3D アプリランチャーは、"アプリのブランド" を表示している人にすぐに表す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8139a-139">Your 3D app launcher should instantly express “your app’s brand” to people who see it.</span></span> <span data-ttu-id="8139a-140">アプリに星型の文字や特に識別可能なオブジェクトがある場合は、設計の大きな部分としてそれを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8139a-140">If you have a star character or an especially identifiable object in your app, we recommend using that as a big part of your design.</span></span> <span data-ttu-id="8139a-141">現実の世界では、オブジェクトはロゴだけでなくユーザーからも関心を引くことができます。</span><span class="sxs-lookup"><span data-stu-id="8139a-141">In a mixed reality world, an object will draw more interest from users than just a logo alone.</span></span> <span data-ttu-id="8139a-142">認識可能なオブジェクトは、ブランドを迅速かつ明確に伝えることができます。</span><span class="sxs-lookup"><span data-stu-id="8139a-142">Recognizable objects communicate brand quickly and clearly.</span></span>

### <a name="volumetric"></a><span data-ttu-id="8139a-143">容量</span><span class="sxs-lookup"><span data-stu-id="8139a-143">Volumetric</span></span>

<span data-ttu-id="8139a-144">お客様のアプリは、ロゴを平面に配置して1日に呼び出すだけではありません。</span><span class="sxs-lookup"><span data-stu-id="8139a-144">Your app deserves more than just putting your logo on a flat plane and calling it a day.</span></span> <span data-ttu-id="8139a-145">ランチャーは、ユーザーの領域において、魅力的で3D な物理オブジェクトのように感じます。</span><span class="sxs-lookup"><span data-stu-id="8139a-145">Your launcher should feel like an exciting, 3D, physical object in the user’s space.</span></span> <span data-ttu-id="8139a-146">アプリの Macy の感謝祭のパレードにバルーンを設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8139a-146">A good approach is to imagine your app was going to have a balloon in the Macy’s Thanksgiving Day Parade.</span></span> <span data-ttu-id="8139a-147">だれかが言っている人は、どこにいるかということです。</span><span class="sxs-lookup"><span data-stu-id="8139a-147">Ask yourself, what would really wow people as it came down the street?</span></span> <span data-ttu-id="8139a-148">すべての表示角度からはどのようになりますか。</span><span class="sxs-lookup"><span data-stu-id="8139a-148">What would look great from all viewing angles?</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="8139a-149">![ロゴのみの ](images/20171016-140436-mixedreality-640px.jpg) *ロゴのみ*</span><span class="sxs-lookup"><span data-stu-id="8139a-149">![Logo only](images/20171016-140436-mixedreality-640px.jpg) *Logo only*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8139a-150">![文字でよりわかりやすい ](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character* 文字を使用する</span><span class="sxs-lookup"><span data-stu-id="8139a-150">![More recognizable with a character](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character*</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="8139a-151">![純粋なアプローチでは、驚くべきことではありませんがフラットなフラットな ](images/20171016-155101-mixedreality-640px.jpg) *アプローチです* 。</span><span class="sxs-lookup"><span data-stu-id="8139a-151">![Flat approach, not surprisingly, feels flat](images/20171016-155101-mixedreality-640px.jpg) *Flat approach, not surprisingly, feels flat*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8139a-152">![アプリ ](images/20171016-161407-mixedreality-640px.jpg) *の容量アプローチ* をより適切に紹介する容量アプローチ</span><span class="sxs-lookup"><span data-stu-id="8139a-152">![Volumetric approach better showcases your app](images/20171016-161407-mixedreality-640px.jpg) *Volumetric approach better showcases your app*</span></span>
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a><span data-ttu-id="8139a-153">優れた3D モデルのヒント</span><span class="sxs-lookup"><span data-stu-id="8139a-153">Tips for good 3D models</span></span>

* <span data-ttu-id="8139a-154">アプリランチャーのディメンションを計画するときは、約30cm のキューブに対して撮影します。</span><span class="sxs-lookup"><span data-stu-id="8139a-154">When planning dimensions for your app launcher, shoot for roughly a 30cm cube.</span></span> <span data-ttu-id="8139a-155">そのため、1:1:1 のサイズ比率です。</span><span class="sxs-lookup"><span data-stu-id="8139a-155">So, a 1:1:1 size ratio.</span></span>
* <span data-ttu-id="8139a-156">モデルは1万ポリゴン以下である必要があります。</span><span class="sxs-lookup"><span data-stu-id="8139a-156">Models must be under 10,000 polygons.</span></span> [<span data-ttu-id="8139a-157">トライアングルの数と詳細レベルの詳細については、LODs を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8139a-157">Learn more about triangle counts and levels of details (LODs)</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* <span data-ttu-id="8139a-158">イマーシブヘッドセットでテストします。</span><span class="sxs-lookup"><span data-stu-id="8139a-158">Test on an immersive headset.</span></span>
* <span data-ttu-id="8139a-159">可能な限りモデルのジオメトリに詳細をビルドします。詳細については、テクスチャに依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="8139a-159">Build details into your model’s geometry where possible – don’t rely on textures for detail.</span></span>
* <span data-ttu-id="8139a-160">"水のきつい" 閉じたジオメトリを構築します。</span><span class="sxs-lookup"><span data-stu-id="8139a-160">Build “water tight” closed geometry.</span></span> <span data-ttu-id="8139a-161">でモデル化されていない穴はありません。</span><span class="sxs-lookup"><span data-stu-id="8139a-161">No holes that are not modeled in.</span></span>
* <span data-ttu-id="8139a-162">オブジェクトで自然な素材を使用します。</span><span class="sxs-lookup"><span data-stu-id="8139a-162">Use natural materials in your object.</span></span> <span data-ttu-id="8139a-163">現実の世界に構築することを想像してください。</span><span class="sxs-lookup"><span data-stu-id="8139a-163">Imagine crafting it in the real world.</span></span>
* <span data-ttu-id="8139a-164">モデルの距離とサイズが異なることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8139a-164">Make sure your model reads well at different distances and sizes.</span></span>
* <span data-ttu-id="8139a-165">モデルの準備ができたら、「資産の [エクスポートに関するガイドライン](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8139a-165">When your model is ready to go, read the [exporting assets guidelines](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview).</span></span>

<span data-ttu-id="8139a-166">![テクスチャの微妙な詳細情報を含むモデル](images/20171013-143334-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8139a-166">![Model with subtle details in the texture](images/20171013-143334-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="8139a-167">*テクスチャの微妙な詳細情報を含むモデル*</span><span class="sxs-lookup"><span data-stu-id="8139a-167">*Model with subtle details in the texture*</span></span>

### <a name="what-to-avoid"></a><span data-ttu-id="8139a-168">避けるべきこと</span><span class="sxs-lookup"><span data-stu-id="8139a-168">What to avoid</span></span>

* <span data-ttu-id="8139a-169">ハイコントラストの詳細や、小さな、ビジーのパターン、テクスチャは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="8139a-169">Don't use high-contrast details or small, busy patterns and textures.</span></span>
* <span data-ttu-id="8139a-170">シンジオメトリは使用しないでください。距離が適切ではなく、別名が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="8139a-170">Don't use thin geometry – it doesn’t work well at a distance and will alias badly.</span></span>
* <span data-ttu-id="8139a-171">モデルの一部が1:1:1 のサイズ比を超えて拡張されないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="8139a-171">Don't let parts of your model extend too much beyond the 1:1:1 size ratio.</span></span> <span data-ttu-id="8139a-172">スケーリングの問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="8139a-172">It will create scaling problems.</span></span>

<span data-ttu-id="8139a-173">![ハイコントラストの小さなビジーパターンを避ける](images/20171013-143603-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8139a-173">![Avoid high-contrast, small busy patterns](images/20171013-143603-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="8139a-174">*ハイコントラスト、小さい、ビジーパターンを避ける*</span><span class="sxs-lookup"><span data-stu-id="8139a-174">*Avoid high-contrast, small, busy patterns*</span></span>

## <a name="how-to-handle-type"></a><span data-ttu-id="8139a-175">型を処理する方法</span><span class="sxs-lookup"><span data-stu-id="8139a-175">How to handle type</span></span>

* <span data-ttu-id="8139a-176">種類は、アプリランチャーの約 1/3 (またはそれ以上) で構成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8139a-176">We recommend your type comprises about 1/3 of your app launcher (or more).</span></span> <span data-ttu-id="8139a-177">Type は、ランチャーが実際にランチャーであることをユーザーに知らせる主要な作業であり、非常に大きな場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="8139a-177">Type is the main thing that gives people an idea that your launcher is, in fact, a launcher so it’s nice if it’s pretty substantial.</span></span>
* <span data-ttu-id="8139a-178">型を大きくするのは避けてください。アプリランチャーのコアディメンション (より多く以下) の範囲内に保持してください。</span><span class="sxs-lookup"><span data-stu-id="8139a-178">Avoid making type super wide – try to keep it within the confines of the app launchers core dimensions (more or less).</span></span>
* <span data-ttu-id="8139a-179">フラット型は機能しますが、特定の角度や特定の環境で表示するのが難しい場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8139a-179">Flat type can work, but be aware that it can be hard to view from certain angles and in certain environments.</span></span> <span data-ttu-id="8139a-180">これを実現するには、それをソリッドオブジェクトまたは背景に配置することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="8139a-180">You might consider putting it a solid object or backdrop behind it to help with this.</span></span>
* <span data-ttu-id="8139a-181">ディメンションを型に追加すると、3D では見栄えが良くなります。</span><span class="sxs-lookup"><span data-stu-id="8139a-181">Adding dimension to your type feels nice in 3D.</span></span> <span data-ttu-id="8139a-182">種類の面の網掛けは、読みやすさを向上させるのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="8139a-182">Shading the sides of the type a different, darker color can help with readability.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="8139a-183">![背景のないフラット型は特定の角度から見るのが難しい場合があります。また、特定の環境では、 ](images/flattype-640px.png) *背景を持たないフラットな型を特定の角度や特定の環境で表示するのが難しい* 場合があります。</span><span class="sxs-lookup"><span data-stu-id="8139a-183">![Flat type without a backdrop can be hard to view from certain angles and in certain environments](images/flattype-640px.png) *Flat type without a backdrop can be hard to view from certain angles and in certain environments*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8139a-184">![組み込みの背景を持つ型は、組み込みの背景を使用して適切な型を使用できます。 ](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span><span class="sxs-lookup"><span data-stu-id="8139a-184">![Type with a built-in backdrop can work well](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="8139a-185">![押し出しの種類を網掛けすると、 ](images/20171016-160221-mixedreality-640px.jpg) *押し出しの種類* が正しく機能します。</span><span class="sxs-lookup"><span data-stu-id="8139a-185">![Extruded type can work well if you shade the sides](images/20171016-160221-mixedreality-640px.jpg) *Extruded type can work well if you shade the sides*</span></span>
    :::column-end:::
:::row-end:::

<span data-ttu-id="8139a-186">**機能する色を入力する**</span><span class="sxs-lookup"><span data-stu-id="8139a-186">**Type colors that work**</span></span>

* <span data-ttu-id="8139a-187">白</span><span class="sxs-lookup"><span data-stu-id="8139a-187">White</span></span>
* <span data-ttu-id="8139a-188">Black</span><span class="sxs-lookup"><span data-stu-id="8139a-188">Black</span></span>
* <span data-ttu-id="8139a-189">明るい半彩度の色</span><span class="sxs-lookup"><span data-stu-id="8139a-189">Bright semi-saturated color</span></span>

<span data-ttu-id="8139a-190">![機能する色を入力します。](images/20171016-112111-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8139a-190">![Type colors that work.](images/20171016-112111-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="8139a-191">*機能する色を入力する*</span><span class="sxs-lookup"><span data-stu-id="8139a-191">*Type colors that work*</span></span>

### <a name="colors-to-avoid"></a><span data-ttu-id="8139a-192">避ける色</span><span class="sxs-lookup"><span data-stu-id="8139a-192">Colors to avoid</span></span>

<span data-ttu-id="8139a-193">問題の原因となる色の種類は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8139a-193">Type colors that cause trouble include:</span></span>

* <span data-ttu-id="8139a-194">ミッドトーン</span><span class="sxs-lookup"><span data-stu-id="8139a-194">Mid-tones</span></span>
* <span data-ttu-id="8139a-195">グレー</span><span class="sxs-lookup"><span data-stu-id="8139a-195">Gray</span></span>
* <span data-ttu-id="8139a-196">彩度が高い色または desaturated の色</span><span class="sxs-lookup"><span data-stu-id="8139a-196">Over-saturated colors or desaturated colors</span></span>

<span data-ttu-id="8139a-197">![問題の原因となる色を入力します。](images/20171016-112246-mixedreality-640px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8139a-197">![Type colors that cause trouble.](images/20171016-112246-mixedreality-640px.jpg)</span></span><br>
<span data-ttu-id="8139a-198">*問題の原因となる色を入力する*</span><span class="sxs-lookup"><span data-stu-id="8139a-198">*Type colors that cause trouble*</span></span>

## <a name="lighting"></a><span data-ttu-id="8139a-199">照明</span><span class="sxs-lookup"><span data-stu-id="8139a-199">Lighting</span></span>

<span data-ttu-id="8139a-200">アプリランチャーのライティングは、崖ハウス環境から取得されます。</span><span class="sxs-lookup"><span data-stu-id="8139a-200">The lighting for your app launcher comes from the Cliff House environment.</span></span> <span data-ttu-id="8139a-201">ライトとシャドウの両方で適切に見えるように、家全体の複数の場所でランチャーをテストしてください。</span><span class="sxs-lookup"><span data-stu-id="8139a-201">Be sure to test your launcher in several places throughout the house so it looks good in both light and shadows.</span></span> <span data-ttu-id="8139a-202">このドキュメントに記載されている他の設計ガイダンスに従っている場合は、崖家のほとんどの照明に対してランチャーが非常に優れた形になっているはずです。</span><span class="sxs-lookup"><span data-stu-id="8139a-202">The good news is, if you’ve followed the other design guidance in this document, your launcher should be in pretty good shape for most lighting in the Cliff House.</span></span>

<span data-ttu-id="8139a-203">環境内のさまざまなライトをランチャーがどのように検索するのかをテストするのに適しているのは、テラス (芝生を使用した具体的な領域) の外側と背面のどこにあるかを問わず、Studio、メディアルームです。</span><span class="sxs-lookup"><span data-stu-id="8139a-203">Good places to test how your launcher looks in the various lights in the environment are the Studio, the Media Room, anywhere outside and on the Back Patio (the concrete area with the lawn).</span></span> <span data-ttu-id="8139a-204">もう1つの優れたテストは、それを半分のライトと半分に配置し、外観を確認することです。</span><span class="sxs-lookup"><span data-stu-id="8139a-204">Another good test is to put it in half light and half shadow and see what it looks like.</span></span>

<span data-ttu-id="8139a-205">![起動ツールがライトとシャドウの両方で適切であることを確認します。](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="8139a-205">![Make sure your launcher looks good in both light and shadows.](images/20171013-145523-mixedreality-1200px-1000px.jpg)</span></span><br>
<span data-ttu-id="8139a-206">*起動ツールがライトとシャドウの両方で適切であることを確認します。*</span><span class="sxs-lookup"><span data-stu-id="8139a-206">*Make sure your launcher looks good in both light and shadows*</span></span>

## <a name="texturing"></a><span data-ttu-id="8139a-207">テクスチャ</span><span class="sxs-lookup"><span data-stu-id="8139a-207">Texturing</span></span>

### <a name="authoring-your-textures"></a><span data-ttu-id="8139a-208">テクスチャの作成</span><span class="sxs-lookup"><span data-stu-id="8139a-208">Authoring your textures</span></span>

<span data-ttu-id="8139a-209">3D アプリランチャーの終了形式は、glb ファイルになります。これは、(物理的にベースになった) .PBR パイプラインを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="8139a-209">The end format of your 3D app launcher will be a .glb file, which is made using the PBR (Physically Based Rendering) pipeline.</span></span> <span data-ttu-id="8139a-210">これは厄介なプロセスである可能性があります。すでにない場合は、技術的アーティストを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8139a-210">This can be a tricky process - now is a good time to employ a technical artist if you haven't already.</span></span> <span data-ttu-id="8139a-211">勇気 DIY がある場合は、まず、情報を [調査して、.pbr の用語について学習](https://wiki.polycount.com/wiki/PBR) して、内部で何が起きているかを確認すると、よくある間違いを避けることができます。</span><span class="sxs-lookup"><span data-stu-id="8139a-211">If you’re a brave DIY-er, taking the time to [research and learn PBR terminology](https://wiki.polycount.com/wiki/PBR) and what’s happening under the hood before you begin will help you avoid common mistakes.</span></span> 

<span data-ttu-id="8139a-212">![例: 新しいメモアプリ](images/pbr-freshnote1-640px-500px.png)</span><span class="sxs-lookup"><span data-stu-id="8139a-212">![Example: Fresh Note app](images/pbr-freshnote1-640px-500px.png)</span></span><br>
<span data-ttu-id="8139a-213">*新鮮ノート3D アプリランチャーの例 (架空のアプリ)*</span><span class="sxs-lookup"><span data-stu-id="8139a-213">*Fresh Note 3D app launcher example (fictional app)*</span></span>

### <a name="recommended-authoring-tool"></a><span data-ttu-id="8139a-214">推奨 authoring tool</span><span class="sxs-lookup"><span data-stu-id="8139a-214">Recommended authoring tool</span></span>

<span data-ttu-id="8139a-215">最終的なファイルを作成するには、Allegorithmic による [物質塗装](https://www.allegorithmic.com/products/substance-painter) を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8139a-215">We recommend using [Substance Painter](https://www.allegorithmic.com/products/substance-painter) by Allegorithmic to author your final file.</span></span> <span data-ttu-id="8139a-216">物質コピーの作成に慣れていない場合は、次の [チュートリアル](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8139a-216">If you’re not familiar with authoring PBR shaders in Substance Painter, here’s a [tutorial](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials).</span></span>

<span data-ttu-id="8139a-217">(また、 [3D コート](https://3dcoat.com/home/)、 [Quixel Suite 2](https://quixel.se/suite2/)、または [marmoset toolbag](https://www.marmoset.co/toolbag/) は、これらのいずれかを使い慣れている場合にも機能します)。</span><span class="sxs-lookup"><span data-stu-id="8139a-217">(Alternately [3D-Coat](https://3dcoat.com/home/), [Quixel Suite 2](https://quixel.se/suite2/), or [Marmoset Toolbag](https://www.marmoset.co/toolbag/) would also work if you’re more familiar with one of these.)</span></span>

### <a name="best-practices"></a><span data-ttu-id="8139a-218">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="8139a-218">Best practices</span></span>

* <span data-ttu-id="8139a-219">アプリランチャーオブジェクトが .PBR 用に作成されている場合、そのオブジェクトを崖家環境に変換するのは非常に簡単です。</span><span class="sxs-lookup"><span data-stu-id="8139a-219">If your app launcher object was authored for PBR, it should be pretty straightforward to convert it for the Cliff House environment.</span></span>
* <span data-ttu-id="8139a-220">シェーダーは金属/粗さのフローを想定しています。 Unreal の .PBR シェーダーは、近いファクシミリです。</span><span class="sxs-lookup"><span data-stu-id="8139a-220">Our shader is expecting a Metal/Roughness work flow – The Unreal PBR shader is a close facsimile.</span></span>
* <span data-ttu-id="8139a-221">テクスチャをエクスポートするときは、推奨される [テクスチャのサイズ](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="8139a-221">When exporting your textures keep the [recommended texture sizes](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) in mind.</span></span>
* <span data-ttu-id="8139a-222">次のように、リアルタイムライティング用にオブジェクトを構築してください。</span><span class="sxs-lookup"><span data-stu-id="8139a-222">Make sure to build your objects for real-time lighting — this means:</span></span>
  * <span data-ttu-id="8139a-223">影を描画しない (影を描画する)</span><span class="sxs-lookup"><span data-stu-id="8139a-223">Avoid baked shadows – or painted shadows</span></span>
  * <span data-ttu-id="8139a-224">テクスチャに含まれる光源を避けます</span><span class="sxs-lookup"><span data-stu-id="8139a-224">Avoid baked lighting in the textures</span></span>
  * <span data-ttu-id="8139a-225">いずれかの .PBR マテリアル作成パッケージを使用して、シェーダー用に生成された適切なマップを取得します。</span><span class="sxs-lookup"><span data-stu-id="8139a-225">Use one of the PBR material authoring packages to get the right maps generated for our shader</span></span>

## <a name="see-also"></a><span data-ttu-id="8139a-226">関連項目</span><span class="sxs-lookup"><span data-stu-id="8139a-226">See also</span></span>

* [<span data-ttu-id="8139a-227">Mixed reality ホームで使用する3D モデルを作成する</span><span class="sxs-lookup"><span data-stu-id="8139a-227">Create 3D models for use in the mixed reality home</span></span>](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [<span data-ttu-id="8139a-228">3D アプリ起動ツールの実装 (UWP アプリ)</span><span class="sxs-lookup"><span data-stu-id="8139a-228">Implement 3D app launchers (UWP apps)</span></span>](implementing-3d-app-launchers.md)
* [<span data-ttu-id="8139a-229">3D アプリ起動ツールの実装 (Win32 アプリ)</span><span class="sxs-lookup"><span data-stu-id="8139a-229">Implement 3D app launchers (Win32 apps)</span></span>](implementing-3d-app-launchers-win32.md)
