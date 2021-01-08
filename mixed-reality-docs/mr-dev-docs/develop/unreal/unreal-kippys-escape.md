---
title: Kippy のエスケープの作成
description: Unreal Engine での HoloLens 2 用の Kippy の Escape mixed reality アプリケーションの作成については、こちらを参照してください。
author: sw5813
ms.author: suwu
ms.date: 9/4/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、mixed reality、デバイスへの展開、PC、ドキュメント、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
appliesto:
- HoloLens 2
ms.openlocfilehash: df199b6a3215158e15fb1252dd75c58aea5bc2ab
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010042"
---
# <a name="the-making-of-kippys-escape"></a><span data-ttu-id="ac444-104">Kippy のエスケープの作成</span><span class="sxs-lookup"><span data-stu-id="ac444-104">The Making of Kippy's Escape</span></span>

<span data-ttu-id="ac444-105">Kippy ロボットが起動され、島上に残されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="ac444-105">Kippy the robot wakes up to find itself stranded on an island.</span></span> <span data-ttu-id="ac444-106">問題解決の hat を使用して、ロケット船への道を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="ac444-106">It’s up to you to put on your problem-solving hat to help it find a path back to its rocket ship!</span></span> <span data-ttu-id="ac444-107">HoloLens 2 でストラップを利用し、Microsoft Store から [アプリをダウンロード](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) するか、GitHub から [リポジトリ](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) を複製して、Kippy ホームセーフを獲得しましょう。</span><span class="sxs-lookup"><span data-stu-id="ac444-107">Strap on your HoloLens 2 and [download the app](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) from the Microsoft Store or clone the [repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) from GitHub and get Kippy home safe!</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="ac444-108">GitHub リポジトリから Kippy のエスケープを構築している場合は、 **Unreal Engine 4.25** 以降を使用していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ac444-108">Make sure you're using **Unreal Engine 4.25 or later** if you're building Kippy's Escape from the GitHub repository.</span></span>

<span data-ttu-id="ac444-109">Kippy のエスケープは、Unreal Engine 4 と[Mixed REALITY UX Tools For Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal)を使用して構築されたオープンソースの[HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware)サンプルアプリです。</span><span class="sxs-lookup"><span data-stu-id="ac444-109">Kippy’s Escape is an open-source [HoloLens 2](https://docs.microsoft.com/hololens/hololens2-hardware) sample app built with Unreal Engine 4 and [Mixed Reality UX Tools for Unreal](https://github.com/microsoft/MixedReality-UXTools-Unreal).</span></span> <span data-ttu-id="ac444-110">この記事では、最初の原則とビジュアルデザインから、エクスペリエンスを実装して最適化するプロセスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ac444-110">In this post, we’ll walk you through our process from first principles and visual design to implementing and optimizing the experience.</span></span> <span data-ttu-id="ac444-111">MRTK UX ツールを使用した Mixed Reality アプリケーションの開発の詳細については、 [Unreal development の概要](unreal-development-overview.md)に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac444-111">You can find more information on developing Mixed Reality applications with MRTK UX Tools in the [Unreal development overview](unreal-development-overview.md).</span></span>

## <a name="first-principles"></a><span data-ttu-id="ac444-112">最初の原則</span><span class="sxs-lookup"><span data-stu-id="ac444-112">First principles</span></span> 

<span data-ttu-id="ac444-113">Kippy のエスケープを作成するための設定では、 [Unreal Engine の HoloLens 2 のサポート](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html)、hololens 2 の機能、Mixed Reality Toolkit を強調するエクスペリエンスを作成することを目標としました。</span><span class="sxs-lookup"><span data-stu-id="ac444-113">In setting out to create Kippy’s Escape, our goal was to create an experience that would highlight [Unreal Engine’s HoloLens 2 support](https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html), the HoloLens 2’s capabilities, and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="ac444-114">私たちは、Unreal と HoloLens 2 で作成できることを想像するために開発者を支援したいと考えていました。</span><span class="sxs-lookup"><span data-stu-id="ac444-114">We wanted to inspire developers to imagine what they could create with Unreal and HoloLens 2.</span></span>  

<span data-ttu-id="ac444-115">経験に関する3つの基本原則を紹介しました。これは楽しい作業で、対話型であり、エントリの障壁が低いことが必要でした。</span><span class="sxs-lookup"><span data-stu-id="ac444-115">We came up with three guiding principles for the experience: that it needed to be fun, interactive, and have a low barrier to entry.</span></span> <span data-ttu-id="ac444-116">この経験は、初めての混合の現実ユーザーであっても、チュートリアルを実行する必要がないという直感的な経験が必要でした。</span><span class="sxs-lookup"><span data-stu-id="ac444-116">We wanted the experience to be intuitive enough that even a first-time mixed reality user won’t need a tutorial to go through it.</span></span>  

## <a name="designing-the-game"></a><span data-ttu-id="ac444-117">ゲームの設計</span><span class="sxs-lookup"><span data-stu-id="ac444-117">Designing the game</span></span> 

<span data-ttu-id="ac444-118">HoloLens 2 は、今日のゲームでは、他の場所ではない設計機能にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="ac444-118">The HoloLens 2 has access to design features found nowhere else in gaming today.</span></span> <span data-ttu-id="ac444-119">オブジェクトは、ハンドを使用して直接プッシュしたり操作したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="ac444-119">Objects can be directly pushed or manipulated using your hands or targeted with eye tracking.</span></span> <span data-ttu-id="ac444-120">これらの主な機能は、Kippy のエスケープで構築した楽しい瞬間の背後にあります。</span><span class="sxs-lookup"><span data-stu-id="ac444-120">These key features are behind some of the fun moments we built out in Kippy’s Escape.</span></span>  

<span data-ttu-id="ac444-121">ゲーム設計のガイダンスとして、独自の HoloLens 2 機能を使用して、いくつかの小規模な環境シナリオを対象にしています。</span><span class="sxs-lookup"><span data-stu-id="ac444-121">Using the unique HoloLens 2 features as guidance for our game design, we scoped out a few small environment scenarios.</span></span> <span data-ttu-id="ac444-122">アイランドは、プレーヤーの高さが異なるために調整でき、おもしろいブリッジのアイデアを提供できるため、意味がありました。</span><span class="sxs-lookup"><span data-stu-id="ac444-122">Islands made sense because they can be adjusted for different player heights, and provided some entertaining bridge ideas.</span></span> <span data-ttu-id="ac444-123">いにしえの文明のテーマには、sci テクノロジを満たしています。これは、他のユーザーが、各島によって提供される奇妙なエネルギーを利用して、廃墟による機械を構築したという考え方です。</span><span class="sxs-lookup"><span data-stu-id="ac444-123">We landed on the theme of ancient civilization meets sci-fi tech, with the idea that someone had built machinery over ruins harnessing a strange energy provided by each island.</span></span> <span data-ttu-id="ac444-124">アイランドはそれぞれ独自のルックアンドフィールを与えられており、視覚効果の作成に役立つ情報を提供しています。</span><span class="sxs-lookup"><span data-stu-id="ac444-124">The islands were each given their own look and feel, a detail that helped create visual interest.</span></span> <span data-ttu-id="ac444-125">モデリングとテクスチャの間で適切なバランスを取ると、描画呼び出しのパフォーマンスが低下します。そのため、この点を念頭に置いた外観が設計されています。</span><span class="sxs-lookup"><span data-stu-id="ac444-125">A good balance between modeling and texturing would keep draw calls low for rendering performance, so a stylized look was designed with that in mind.</span></span> 

<span data-ttu-id="ac444-126">![初期のゲーム設計 ](images/kippys-escape/kippys-escape-img-01.png)
 *では、エクスペリエンスがどのようなものになるかを事前に確認し* ています。</span><span class="sxs-lookup"><span data-stu-id="ac444-126">![Early game design sketches](images/kippys-escape/kippys-escape-img-01.png)
*Some early sketches for what the experience might look like*</span></span>

<span data-ttu-id="ac444-127">![2番目の島の2番目の島 ](images/kippys-escape/kippys-escape-img-02.png)
 *レンダリング* のレンダリング</span><span class="sxs-lookup"><span data-stu-id="ac444-127">![Renderings of the second island](images/kippys-escape/kippys-escape-img-02.png)
*Renderings of the second island*</span></span>

<span data-ttu-id="ac444-128">短時間の運用スケジュール内に保持するために、浮動小文字が厳密なアニメーションサイクルを使用せずに意図と感情をキャプチャできることに同意しました。</span><span class="sxs-lookup"><span data-stu-id="ac444-128">To keep within our short production schedule, we agreed that a floating character could capture intent and emotion without rigorous animation cycles.</span></span> <span data-ttu-id="ac444-129">Kippy が生まれました。</span><span class="sxs-lookup"><span data-stu-id="ac444-129">And so Kippy was born!</span></span> <span data-ttu-id="ac444-130">その目とミニマルなボーカルを通じていくつかの異なる式を見て、プレイヤーのエクスペリエンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="ac444-130">It emotes a few different expressions through its eyes and through minimalistic vocal sound effects to help guide the player throughout the experience.</span></span> 

![さまざまな式を目で見て Kippy](images/kippys-escape/kippys-escape-img-03.gif)

<span data-ttu-id="ac444-132">*さまざまな式を目で見て Kippy*</span><span class="sxs-lookup"><span data-stu-id="ac444-132">*Kippy showing different expressions via its eyes*</span></span>

![ユーザーによるパズルの解決に時間がかかりすぎる場合、Kippy はユーザーにヒントを提供します。](images/kippys-escape/kippys-escape-img-04.gif)

<span data-ttu-id="ac444-134">*ユーザーによるパズルの解決に時間がかかりすぎる場合、Kippy はユーザーにヒントを提供します。*</span><span class="sxs-lookup"><span data-stu-id="ac444-134">*If the user takes too long to solve a puzzle, Kippy will give the user a hint*</span></span>

<span data-ttu-id="ac444-135">文字と環境の設計以外にも、ゲームが楽しくなるように一丸努力をしました。</span><span class="sxs-lookup"><span data-stu-id="ac444-135">Beyond the character and environment design, we made a concerted effort to make the game feel fun.</span></span> <span data-ttu-id="ac444-136">目の追跡では、ゲームの重要な部分を強調表示した素材とサウンドの属性をオフにすることができました。</span><span class="sxs-lookup"><span data-stu-id="ac444-136">Eye tracking allowed us to fire off material and sound attributes, which highlighted key pieces of the game.</span></span> <span data-ttu-id="ac444-137">空間オーディオを使用すると、プレーヤーの周囲のレベルを自宅で見ることができます。</span><span class="sxs-lookup"><span data-stu-id="ac444-137">Spatial audio helped make the levels feel at home in the player’s surroundings.</span></span> <span data-ttu-id="ac444-138">オブジェクトの取得、ボタンのプッシュ、およびスライダーの操作を行うことで、革新的なプレーヤーのエンゲージメントを実現できます。</span><span class="sxs-lookup"><span data-stu-id="ac444-138">Being able to grab objects, push buttons, and manipulate sliders drives innovative player engagements.</span></span> <span data-ttu-id="ac444-139">これらの接続ポイントが自然に認識されるようにすることが重要でした。</span><span class="sxs-lookup"><span data-stu-id="ac444-139">It was important to make sure these connection points felt natural.</span></span> 

![ブリッジケーブルの端は、ユーザーが自分の手に近づいたときにグローします。](images/kippys-escape/kippys-escape-img-05.gif)

<span data-ttu-id="ac444-141">*ブリッジケーブルの端は、ユーザーが自分の手に近づいたときにグローします。*</span><span class="sxs-lookup"><span data-stu-id="ac444-141">*The end of the bridge cable glows when the user’s hand approaches it*</span></span>

## <a name="building-the-game-mechanics"></a><span data-ttu-id="ac444-142">ゲーム機構の構築</span><span class="sxs-lookup"><span data-stu-id="ac444-142">Building the game mechanics</span></span> 

<span data-ttu-id="ac444-143">Kippy のエスケープは、ゲームをインタラクティブにするために、混合現実 UX ツールコンポーネントに大きく依存しています。つまり、手作業でアクター、境界コントロール、マニピュレーター、スライダー、およびボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="ac444-143">Kippy’s Escape relies heavily on Mixed Reality UX Tools components to make the game interactive - namely hand interaction actors, bounds controls, manipulators, sliders, and buttons.</span></span>   

<span data-ttu-id="ac444-144">[ハンドインタラクションアクター](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html)は、ホログラムの直接および遠くの操作の両方を可能にします。</span><span class="sxs-lookup"><span data-stu-id="ac444-144">The [hand interaction actor](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html) enables both direct and far manipulation of holograms.</span></span> <span data-ttu-id="ac444-145">Kippy のエスケープの開始時に、ユーザーにゲームの場所を設定する機会が与えられます。</span><span class="sxs-lookup"><span data-stu-id="ac444-145">At the start of Kippy’s Escape, the user is given the opportunity to set the location of the game.</span></span> <span data-ttu-id="ac444-146">ユーザーの palm から手のひらを使用すると、以下の gif に示すように、はるかに離れた大きなホログラムを簡単に操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ac444-146">Hand beams extending from the user’s palm make it easy to manipulate large holograms that are far away, as seen in the gif below.</span></span>  

![ハンド相互作用アクター gif](images/kippys-escape/kippys-escape-img-06.gif)

<span data-ttu-id="ac444-148">プレースホルダーシーン自体は、UX ツールの [境界制御](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/BoundsControl.html) コンポーネントを使用してドラッグアンドローテーションすることができます。</span><span class="sxs-lookup"><span data-stu-id="ac444-148">The placeholder scene itself can be dragged and rotated using UX Tools’ [bounds control](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/BoundsControl.html) component.</span></span>  

<span data-ttu-id="ac444-149">2番目の島では、ユーザーは gem を選択し、対応するスロットに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac444-149">On the second island, the user must pick up gems and place them in their matching slots.</span></span> <span data-ttu-id="ac444-150">Gem には、ユーザーが選択して下に配置できるようにする [マニピュレーター](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html) が関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="ac444-150">The gems have [manipulators](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html) attached to them that allow the user to pick them up and place them down.</span></span> 

![マニピュレーターの例 gif](images/kippys-escape/kippys-escape-img-07.gif)

<span data-ttu-id="ac444-152">[Pressable ボタン](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html)は、3つ目の島で使用するために爆弾を立ち上げる鍵です。</span><span class="sxs-lookup"><span data-stu-id="ac444-152">A [pressable button](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html) is the key to bringing up bombs for use on the third island.</span></span>  

![Pressable button の例 gif](images/kippys-escape/kippys-escape-img-08.gif)

<span data-ttu-id="ac444-154">4つ目の島に [スライダー](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PinchSlider.html) コンポーネントが表示され、最終的なブリッジが発生します。</span><span class="sxs-lookup"><span data-stu-id="ac444-154">A [slider](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PinchSlider.html) component appears on the fourth island, triggering the final bridge to be raised.</span></span>  

![スライダーコンポーネントの例 gif](images/kippys-escape/kippys-escape-img-09.gif) 

## <a name="optimizing-for-hololens-2"></a><span data-ttu-id="ac444-156">HoloLens 2 の最適化</span><span class="sxs-lookup"><span data-stu-id="ac444-156">Optimizing for HoloLens 2</span></span> 

<span data-ttu-id="ac444-157">モバイルデバイスで実行するように構築された経験があれば、パフォーマンスを監視することが重要です。</span><span class="sxs-lookup"><span data-stu-id="ac444-157">With any experience built to run on a mobile device, keeping an eye on performance is critical.</span></span> <span data-ttu-id="ac444-158">Unreal 4.25 には、モバイルマルチビューをサポートするための主要な更新プログラムが含まれています。これにより、レンダリングのオーバーヘッドが大幅に減少し、フレームレートが増幅されます。</span><span class="sxs-lookup"><span data-stu-id="ac444-158">Unreal 4.25 includes a major update to support for mobile multi-view, which significantly reduces rendering overhead and boosts frame-rate.</span></span> <span data-ttu-id="ac444-159">最適化の際に、非 Real の HoloLens 2 開発に対して推奨される他の [パフォーマンス設定](performance-recommendations-for-unreal.md) を確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ac444-159">We recommend checking out our other [recommended performance settings](performance-recommendations-for-unreal.md) for HoloLens 2 development with Unreal when you're optimizing.</span></span>  

<span data-ttu-id="ac444-160">物理オブジェクトのパフォーマンスは依然として高くなります。そのため、いくつかの巧妙な回避策が使用されていました。</span><span class="sxs-lookup"><span data-stu-id="ac444-160">Physics objects still remain costly for performance, so a couple clever workarounds were used.</span></span> <span data-ttu-id="ac444-161">たとえば、3番目の "ブリッジ" では、階段を妨げているいくつかのごみが必要です。</span><span class="sxs-lookup"><span data-stu-id="ac444-161">For instance, the third “bridge” requires blowing up some debris blocking the stairway.</span></span> <span data-ttu-id="ac444-162">デトネーションは、物理的なオブジェクトとして石に影響を与えるのではなく、スワップをトリガーし、固定のパーティクル効果のために静的石を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="ac444-162">Instead of having a force impact the stones as physics objects, the bomb detonation triggers a swap, switching the static stones for an exploding particle effect.</span></span> 

![HoloLens 2 gif 用に最適化された例](images/kippys-escape/kippys-escape-img-10.gif) 

<span data-ttu-id="ac444-164">また、次のようにして、400 ~ 260 の描画呼び出しを削減します。</span><span class="sxs-lookup"><span data-stu-id="ac444-164">We also cut down our draw calls from over 400 to  ~260 by:</span></span> 
* <span data-ttu-id="ac444-165">メッシュの複雑さの軽減</span><span class="sxs-lookup"><span data-stu-id="ac444-165">Reducing mesh complexity</span></span>
* <span data-ttu-id="ac444-166">メッシュの結合</span><span class="sxs-lookup"><span data-stu-id="ac444-166">Combining meshes</span></span>
* <span data-ttu-id="ac444-167">初期の動的な光源要素の一部を削除しています</span><span class="sxs-lookup"><span data-stu-id="ac444-167">Removing some of our initial dynamic lighting elements</span></span>

<span data-ttu-id="ac444-168">他にも可能なことがありますが、パフォーマンスと視覚品質のバランスが良好であると考えました。</span><span class="sxs-lookup"><span data-stu-id="ac444-168">While there’s likely more we could have done, we felt that was a good balance between performance and visual quality.</span></span>  

## <a name="try-it-out"></a><span data-ttu-id="ac444-169">試してみましょう。</span><span class="sxs-lookup"><span data-stu-id="ac444-169">Try it out!</span></span> 

<span data-ttu-id="ac444-170">HoloLens 2 を起動し、Microsoft Store からアプリを [ダウンロード](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) するか、GitHub から [リポジトリ](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) を複製して自分でアプリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="ac444-170">Boot up your HoloLens 2 and [download](https://www.microsoft.com/p/kippys-escape/9nbd7gl86vkd) the app from the Microsoft Store, or clone the [repository](https://github.com/microsoft/MixedReality-Unreal-KippysEscape) from GitHub and build the app yourself!</span></span>  

## <a name="about-the-team"></a><span data-ttu-id="ac444-171">チームについて</span><span class="sxs-lookup"><span data-stu-id="ac444-171">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Jack Caron" width="60" height="60" src="images/kippys-escape/jack-caron.jpg"></td>
<td style="border-style: none"><span data-ttu-id="ac444-172"><b>ジャックキャロン</b></span><span class="sxs-lookup"><span data-stu-id="ac444-172"><b>Jack Caron</b></span></span><br><span data-ttu-id="ac444-173"><i>リードゲームデザイナー</i></span><span class="sxs-lookup"><span data-stu-id="ac444-173"><i>Lead Game Designer</i></span></span><br><span data-ttu-id="ac444-174">Jack は、現在、HoloLens 2 プロジェクトや Altをはじめとする Microsoft の Mixed Reality エクスペリエンスで機能しており、以前は HoloLens プラットフォームチームのデザイナーでした。</span><span class="sxs-lookup"><span data-stu-id="ac444-174">Jack currently works on Mixed Reality experiences for Microsoft, including HoloLens 2 projects and AltspaceVR, and was previously a designer on the HoloLens platform team.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Summer Wu" width="60" height="60" src="images/kippys-escape/summer-wu.jpg"></td>
<td style="border-style: none"><span data-ttu-id="ac444-175"><b>夏 Wu</b></span><span class="sxs-lookup"><span data-stu-id="ac444-175"><b>Summer Wu</b></span></span><br><span data-ttu-id="ac444-176"><i>Producer</i></span><span class="sxs-lookup"><span data-stu-id="ac444-176"><i>Producer</i></span></span><br><span data-ttu-id="ac444-177">夏は、mixed reality 開発者プラットフォームに勤務しており、チームのエンジン関連の作業には参加していません。</span><span class="sxs-lookup"><span data-stu-id="ac444-177">Summer works on the mixed reality developer platform and heads the team’s Unreal Engine related efforts.</span></span></td>
</tr>
</table>

<span data-ttu-id="ac444-178">Kippy の脱出を実現するために、 [フレームストア](https://www.framestore.com/) で友人に感謝しています。</span><span class="sxs-lookup"><span data-stu-id="ac444-178">Special thanks to our friends at [Framestore](https://www.framestore.com/) for helping us bring Kippy’s Escape to life.</span></span> <span data-ttu-id="ac444-179">キャラクターの開発、資産の設計、ゲームプログラミングから、このプロジェクトのコラボレーションは非常に重要でした。</span><span class="sxs-lookup"><span data-stu-id="ac444-179">From character development, to asset design, to game programming, their collaboration on this project was pivotal.</span></span>  