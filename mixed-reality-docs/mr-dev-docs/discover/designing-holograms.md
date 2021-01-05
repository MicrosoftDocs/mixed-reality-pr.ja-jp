---
title: ホログラムのデザイン
description: Microsoft が新しく設計したホログラムアプリケーションを使用して、Mixed Reality について説明します。
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, ホログラム, ホログラムの設計, 学習, サンプルアプリ, mixed reality ヘッドセット, 仮想現実のヘッドセット, 仮想現実とは
ms.openlocfilehash: 2480b5e0b4dca502c746dad6f070226ffa8cd1f9
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757760"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="501d1-104">ホログラムの設計</span><span class="sxs-lookup"><span data-stu-id="501d1-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="501d1-105">小さい読み込みウィンドウで、このページのすべてのクール Gif と埋め込みビデオを考慮するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="501d1-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="501d1-106">混合現実向けに設計する方法を習得することは難しい場合があります。これは、メディアが2D デザインプロセスに適切に変換されないためです。</span><span class="sxs-lookup"><span data-stu-id="501d1-106">Learning how to design for mixed reality can be hard because the medium doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="501d1-107">Microsoft では、mixed reality UX Design じの基礎を理解するのに役立つ、HoloLens 2 用の無料のアプリを作成しました。</span><span class="sxs-lookup"><span data-stu-id="501d1-107">Here at Microsoft, we've created a free app for the HoloLens 2 to help you learn the fundamentals of mixed reality UX Design firsthand.</span></span> <span data-ttu-id="501d1-108">独自の魅力的ですばらしい HoloLens アプリを作成するのに役立つように、複数の現実の行動、ヒント、および推奨事項にダイブするために、ホログラムアプリを設計するための独自のアプローチを採用しています。</span><span class="sxs-lookup"><span data-stu-id="501d1-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="501d1-109">Microsoft Store からアプリを無料でダウンロードし、Microsoft の Mixed Reality 設計チームから学ぶことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="501d1-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="501d1-110">デザインホログラムアプリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="501d1-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![デザインホログラムのデモ室にあるヘッド追跡シーンのアニメーション GIF](images/designing-holograms/demo-room.gif)

<span data-ttu-id="501d1-112">*ホログラムのデモ室 (人形家とも呼ばれます) の設計*</span><span class="sxs-lookup"><span data-stu-id="501d1-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="501d1-113">Mixed reality の設計</span><span class="sxs-lookup"><span data-stu-id="501d1-113">Designing for mixed reality</span></span>

<span data-ttu-id="501d1-114">多くのユーザーと同じように、私はモバイルアプリの設計に使用しました。</span><span class="sxs-lookup"><span data-stu-id="501d1-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="501d1-115">2D デザイン環境では、すべてが現在世界中である空間コンピューティングについて詳しく解説してきましたが、大きなシフトでした。</span><span class="sxs-lookup"><span data-stu-id="501d1-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="501d1-116">Mixed reality では、アプリが2D 画面に限定されなくなりました。実際には、実世界に配置され、実際のオブジェクトとやり取りしています。</span><span class="sxs-lookup"><span data-stu-id="501d1-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="501d1-117">私にとっては、従来の2D デザインプロセスに3D エクスペリエンスを接続することは、mixed reality 開発の最も困難な側面です。</span><span class="sxs-lookup"><span data-stu-id="501d1-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="501d1-118">「お客様との会話」では、"どのような機能が含まれているか、およびそれらをどのように稼働させるかを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="501d1-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="501d1-119">コードです。ドキュメントやチュートリアルに従うことはできますが、ユーザーエクスペリエンスは、</span><span class="sxs-lookup"><span data-stu-id="501d1-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="501d1-120">多くの機能、さまざまな入力オプション、さまざまなシナリオ、および物理的な環境が非常に多くあります。</span><span class="sxs-lookup"><span data-stu-id="501d1-120">So many features, different input options, different scenarios, and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="501d1-121">![サンフランシスコの ](images/designing-holograms/workshop.jpeg)
 *hololens 2* 設計ワークショップによるサンフランシスコでの Hololens 2 設計ワークショップの画像</span><span class="sxs-lookup"><span data-stu-id="501d1-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="501d1-122">教える機会</span><span class="sxs-lookup"><span data-stu-id="501d1-122">An opportunity to teach</span></span>

<span data-ttu-id="501d1-123">最初は明らかではありませんでしたが、mixed reality を1つのメディアとして使用して説明するための優れた機会が提供されました。</span><span class="sxs-lookup"><span data-stu-id="501d1-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="501d1-124">ホログラムの設計は、mixed reality の設計概念と推奨事項について説明するビジュアルエクスペリエンスです。</span><span class="sxs-lookup"><span data-stu-id="501d1-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="501d1-125">自分と仮想教師が混合現実の設計概念をデモンストレーションしているだけです。</span><span class="sxs-lookup"><span data-stu-id="501d1-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="501d1-126">私たちは、お客様のスペースにしっかりと経験を持っています。</span><span class="sxs-lookup"><span data-stu-id="501d1-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="501d1-127">*ホログラムトレーラービデオの設計*</span><span class="sxs-lookup"><span data-stu-id="501d1-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="501d1-128">人形の家を調べる</span><span class="sxs-lookup"><span data-stu-id="501d1-128">Exploring the doll house</span></span>

<span data-ttu-id="501d1-129">人形ハウスは、アプリ全体で使用する仮想環境です。</span><span class="sxs-lookup"><span data-stu-id="501d1-129">The doll house is the virtual environment we use throughout the app.</span></span> <span data-ttu-id="501d1-130">この環境は、壁面、ランプ、家具、テーブル、テレビなど、ほとんどの部屋が共通している基本的な要素を含む 80 x 60 x 40 cm のミニルームです。</span><span class="sxs-lookup"><span data-stu-id="501d1-130">The environment is an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="501d1-131">人形ハウスはアプリエクスペリエンスの主要な主役であるため、どの環境でもうまく機能することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="501d1-131">The doll house is the main protagonist of the app experience, so we needed to make sure it would work great in any environment.</span></span> <span data-ttu-id="501d1-132">これは、あらゆる種類の混合現実概念を視覚化するための小さなデモ室と考えてください。</span><span class="sxs-lookup"><span data-stu-id="501d1-132">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="501d1-133">*Dollhouse 調整動作のビデオ*</span><span class="sxs-lookup"><span data-stu-id="501d1-133">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="501d1-134">1:1 対1:10 プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="501d1-134">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="501d1-135">最初の前提として、1:1 のデモはすばらしい教師であると思います。</span><span class="sxs-lookup"><span data-stu-id="501d1-135">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="501d1-136">このユーザーには、教師が実際の有効期間に見ているものがすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="501d1-136">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="501d1-137">しかし、すぐに問題が発生することに気付きます。</span><span class="sxs-lookup"><span data-stu-id="501d1-137">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="501d1-138">ほとんどの開発者は、オフィスで、またはデモ室より小さい部屋でアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="501d1-138">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="501d1-139">表示は加法です。つまり、仮想環境全体がユーザーの部屋に重なって表示されます。</span><span class="sxs-lookup"><span data-stu-id="501d1-139">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="501d1-140">2つのテーブルが混同される可能性があります。2つの couches と、アラインされていない壁面が考えられます。</span><span class="sxs-lookup"><span data-stu-id="501d1-140">That can get confusing with two tables, maybe double couches, and walls that don’t align.</span></span>
- <span data-ttu-id="501d1-141">また、ビューのフィールドによって制約されているすべての仮想環境のうち、最悪のものがあります。</span><span class="sxs-lookup"><span data-stu-id="501d1-141">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="501d1-142">ミニ1:10 スケールを試してみたところ、結果は現実的な部屋のすばらしい鳥のビューでした。</span><span class="sxs-lookup"><span data-stu-id="501d1-142">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room.</span></span> <span data-ttu-id="501d1-143">すべての角度から発生したすべてのものが同時に表示されます。</span><span class="sxs-lookup"><span data-stu-id="501d1-143">You could see everything that was going on from any angle all at the same time.</span></span> <span data-ttu-id="501d1-144">最も驚くべきことは、ほとんどのテスト担当者が、小規模なバージョンを確認するために多くのものを見つけた後、1:1 スケールに切り替えられないことです。</span><span class="sxs-lookup"><span data-stu-id="501d1-144">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="501d1-145">そのため、1:1 バージョンを実際に廃棄し、UI やアプリのその他の側面を調整するために必要な余分な作業を回避することにしました。</span><span class="sxs-lookup"><span data-stu-id="501d1-145">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="501d1-146">![1:1 スケールのフィールドと ](images/designing-holograms/1-1-scale.png)
 *1:1 scale の* ビューのフィールド</span><span class="sxs-lookup"><span data-stu-id="501d1-146">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="501d1-147">![1:10 スケールのフィールドと ](images/designing-holograms/1-10-scale.png)
 *1:10 scale の* ビューのフィールド</span><span class="sxs-lookup"><span data-stu-id="501d1-147">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="501d1-148">Mixed Reality キャプチャの使用</span><span class="sxs-lookup"><span data-stu-id="501d1-148">Using Mixed Reality Capture</span></span>

<span data-ttu-id="501d1-149">このアプリの最も重要な特徴の1つは、mixed reality のキャプチャを使用して、mixed reality の設計概念を学習し、デモンストレーションすることです。</span><span class="sxs-lookup"><span data-stu-id="501d1-149">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="501d1-150">Microsoft は、サンフランシスコに Mixed Reality Capture studio を持っています。</span><span class="sxs-lookup"><span data-stu-id="501d1-150">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="501d1-151">また、このテクノロジは他のスタジオにもライセンス供与されています。これには、ワシントン D.C. にあるアバターディメンション、ロサンゼルスのメタステージ、ロンドンのディメンションスタジオ、ソウルでの、および Volucap (ベルリン) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="501d1-151">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="501d1-152">詳細については、 [こちら](https://www.microsoft.com/mixed-reality/capture-studios)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="501d1-152">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="501d1-153">*サンフランシスコの混合 Reality Capture Studio にある106カメラの1つからの Daniel Escudero の生の映像。*</span><span class="sxs-lookup"><span data-stu-id="501d1-153">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="501d1-154">キャプチャプロセスでは、keyframed メッシュ、法線、およびテクスチャが生成されます。これは、さらに実稼働後に OBJ/PNG ファイルとして提供されるか、または h.264 圧縮 MP4 ファイルとして再生できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="501d1-154">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="501d1-155">これらのファイルは、Unity、Unreal、ネイティブ、および WebXR の各プロジェクトにインポートできます。</span><span class="sxs-lookup"><span data-stu-id="501d1-155">These files can be imported into Unity, Unreal, Native, and WebXR projects.</span></span> <span data-ttu-id="501d1-156">ファイルは、Windows、iOS、Mac、Android、マジック Leap、Playstation VR で実行できます。</span><span class="sxs-lookup"><span data-stu-id="501d1-156">Files can run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="501d1-157">*オーディオと埋め込みメッシュを含むビデオを含む mp4 を分析するために用意されているキャプチャプレーヤー。*</span><span class="sxs-lookup"><span data-stu-id="501d1-157">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="501d1-158">キャプチャと仮想オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="501d1-158">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="501d1-159">Mixed Reality では、ユーザーまたは動物の仮想表現が生成されますが、他の仮想オブジェクトと対話するためにこれらの文字が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="501d1-159">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="501d1-160">次の2つの例は、この効果を実現するためにシーンを操作するさまざまな方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="501d1-160">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="501d1-161">ヘッドを見つめた調整</span><span class="sxs-lookup"><span data-stu-id="501d1-161">Head Gaze Adjustment</span></span>

<span data-ttu-id="501d1-162">ヘッド見つめ調整を使用すると、キャプチャしたユーザーのヘッドを実行時に移動できます。つまり、ユーザーに対してキャプチャを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="501d1-162">Headgaze adjustment lets you move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="501d1-163">ここでは、ビューと目的のフィールドを表示するために使用しています。</span><span class="sxs-lookup"><span data-stu-id="501d1-163">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="501d1-164">次に示すのは、移動するためのターゲットとして機能する移動中のオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="501d1-164">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="501d1-165">ターゲットを左右に移動すると、キャプチャの先頭は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="501d1-165">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="501d1-166">このトリックを使用して、人形ハウスのさまざまな部分に配置されているホログラムに対してアイドルキャプチャが常に直面していることを確認しています。</span><span class="sxs-lookup"><span data-stu-id="501d1-166">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![Unity のターゲットのオブジェクトに従って、実行時にキャプチャのヘッドを移動しています](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="501d1-168">*Unity のターゲットのオブジェクトに従って、実行時にキャプチャのヘッドを移動します。*</span><span class="sxs-lookup"><span data-stu-id="501d1-168">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="501d1-169">同期 (アニメーションオブジェクトを)</span><span class="sxs-lookup"><span data-stu-id="501d1-169">Syncing Animated Objects</span></span>

<span data-ttu-id="501d1-170">2つ目は、キャプチャの移動と同期するためにオブジェクトをアニメーション化していました。</span><span class="sxs-lookup"><span data-stu-id="501d1-170">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="501d1-171">アプリのさまざまな部分で、5フレームごとに特定のキャプチャのシーケンシャル Obj をインポートしました。</span><span class="sxs-lookup"><span data-stu-id="501d1-171">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="501d1-172">次に、Obj はシーンでアニメーション化され、キャプチャの対応するフレームと一致することが確認されます。</span><span class="sxs-lookup"><span data-stu-id="501d1-172">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="501d1-173">これは、アニメーション化と部分処理を行う面倒なプロセスですが、結果は非常に優れています。</span><span class="sxs-lookup"><span data-stu-id="501d1-173">It’s a tedious process of animating and keyframing, but the result is great.</span></span> <span data-ttu-id="501d1-174">これで、非キャプチャオブジェクトと対話する Mixed Reality キャプチャが表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="501d1-174">You can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![混合 Reality キャプチャと UI パネル間で同期されたアニメーション](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="501d1-176">*混合 Reality キャプチャと UI パネル間で同期されたアニメーション*</span><span class="sxs-lookup"><span data-stu-id="501d1-176">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="501d1-177">UI クリエイティブプロセス</span><span class="sxs-lookup"><span data-stu-id="501d1-177">UI creative process</span></span>

<span data-ttu-id="501d1-178">UI デザインを開始したときに、ホログラムが提供するマジックと可能性のいくつかを紹介する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="501d1-178">When we started the UI design, we wanted to show some of the magic and possibility that holograms have to offer.</span></span> <span data-ttu-id="501d1-179">静的な2D ウィンドウとテキストボックスを単に表示するのは、3D の世界には適していません。</span><span class="sxs-lookup"><span data-stu-id="501d1-179">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world.</span></span> <span data-ttu-id="501d1-180">そのような場合には、ほとんどの場合は表示されません。そのため、最初から、holographic 3D 空間を最大限に活用することにしました。</span><span class="sxs-lookup"><span data-stu-id="501d1-180">Many of the possibilities at hand just don't show up, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="501d1-181">まず、パネル、アイコン、テキスト情報に対していくつかの太さを追加しました。</span><span class="sxs-lookup"><span data-stu-id="501d1-181">At first, we started with adding some thickness to the panels, icons, and text information.</span></span> <span data-ttu-id="501d1-182">それでも、ユーザーとしては、テキストボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="501d1-182">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="501d1-183">画像を含むテキストボックスが表示されません。</span><span class="sxs-lookup"><span data-stu-id="501d1-183">Text boxes with images, but we aren't there.</span></span> <span data-ttu-id="501d1-184">Mixed Reality Toolkit (MRTK) シェーダーを使用することによってさらに問題が発生しました。</span><span class="sxs-lookup"><span data-stu-id="501d1-184">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="501d1-185">MRTK シェーダーは強力なツールになり、そのステンシル機能を使用してパネルに負の深度を追加しました。</span><span class="sxs-lookup"><span data-stu-id="501d1-185">The MRTK shaders became a powerful tool, and we made use of its stencil features to add negative depth to the panels.</span></span> <span data-ttu-id="501d1-186">つまり、テキストボックスの前に要素を追加するのではなく、透明なパネルの背後にアイコンが表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="501d1-186">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="501d1-187">現在、ユーザーとして表示されているのは、実際にはレプリケートできないことです。これは、holographic マジックが発生し始めたところです。</span><span class="sxs-lookup"><span data-stu-id="501d1-187">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="501d1-188">また、実際にはお読みたくないユーザーとしても、既に物理的な世界にいます。</span><span class="sxs-lookup"><span data-stu-id="501d1-188">Also as a user I don’t really like to read, I do a lot already in the physical world.</span></span>

<span data-ttu-id="501d1-189">明らかにアイコンは、単純なテキストよりもはるかに優れています。さらに強力なガイダンスを提供するために、一連のアニメーションオブジェクトとアバターの作成を開始し、それぞれのシナリオで何が行われているか、およびその使用方法について小さなストーリーを示しています。</span><span class="sxs-lookup"><span data-stu-id="501d1-189">Obviously icons work a lot better than simple text does, to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![対話型の holographic メニューシステムのアニメーション GIF](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a><span data-ttu-id="501d1-191">主要な概念</span><span class="sxs-lookup"><span data-stu-id="501d1-191">Core concepts</span></span>

<span data-ttu-id="501d1-192">**ホログラフィック フレーム**</span><span class="sxs-lookup"><span data-stu-id="501d1-192">**Holographic frame**</span></span>

![Holographic フレームが強調表示されている dollhouse を囲むユーザーのアニメーション GIF](images/designing-holograms/FOVandFOI.gif)

<span data-ttu-id="501d1-194">**座標系**</span><span class="sxs-lookup"><span data-stu-id="501d1-194">**Coordinate systems**</span></span>

![座標系が強調表示されている dollhouse を囲むユーザーのアニメーション GIF](images/designing-holograms/CoordinateSystems.gif)

<span data-ttu-id="501d1-196">**視線追跡**</span><span class="sxs-lookup"><span data-stu-id="501d1-196">**Eye tracking**</span></span>

![外観が強調表示されている固定のホログラムを見ているユーザーのアニメーション GIF](images/designing-holograms/EyeTracking.gif)

<span data-ttu-id="501d1-198">**ルームスキャンの視覚化と空間マッピング**</span><span class="sxs-lookup"><span data-stu-id="501d1-198">**Room scan visualization and spatial mapping**</span></span>

![マップされている dollhouse 内のすべてのサーフェイスのアニメーション GIF](images/designing-holograms/SpatialMapping.gif)

<span data-ttu-id="501d1-200">**シーンの理解**</span><span class="sxs-lookup"><span data-stu-id="501d1-200">**Scene understanding**</span></span>

![認識されている dollhouse 内のオブジェクトのアニメーション GIF](images/designing-holograms/SceneUnderstanding.gif)

<span data-ttu-id="501d1-202">**手書き線を使用したポイントアンドコミット**</span><span class="sxs-lookup"><span data-stu-id="501d1-202">**Point and commit with hand rays**</span></span>

![ハンドレイが強調表示されているユーザーのアニメーション GIF](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="501d1-204">"試してみる"</span><span class="sxs-lookup"><span data-stu-id="501d1-204">"Try it out" moments</span></span>

<span data-ttu-id="501d1-205">ホログラムを設計すると、mixed reality の概念が説明されますが、ルームでも試してみることができます。</span><span class="sxs-lookup"><span data-stu-id="501d1-205">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="501d1-206">これらの説明の後に、人形の家を一時停止して、対話的な時間を取ります。</span><span class="sxs-lookup"><span data-stu-id="501d1-206">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="501d1-207">これらの対話型の瞬間の例をいくつか次に示します。</span><span class="sxs-lookup"><span data-stu-id="501d1-207">Here are some examples of those interactive moments:</span></span>

![ハンドが検出されたときと、ビューのフィールドに入るタイミングを示す、ハンドトラッキングフレームのアニメーション GIF](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="501d1-209">*ハンドが検出されたときと、そのフィールドに表示されるタイミングを示すハンドトラッキングフレーム。*</span><span class="sxs-lookup"><span data-stu-id="501d1-209">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![遠隔操作による競合の crystals と対話するアニメーション GIF](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="501d1-211">*遠隔操作による衝突の crystals との対話*</span><span class="sxs-lookup"><span data-stu-id="501d1-211">*Interacting with colliding crystals through far interaction*</span></span>

![相互作用 affordances を調べるためのアニメーション GIF](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="501d1-213">*Near 対話 affordances の探索*</span><span class="sxs-lookup"><span data-stu-id="501d1-213">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="501d1-214">チームについて</span><span class="sxs-lookup"><span data-stu-id="501d1-214">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="501d1-215"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="501d1-215"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="501d1-216"><i>リーダーのテクニカルデザイナー</i></span><span class="sxs-lookup"><span data-stu-id="501d1-216"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="501d1-217">Dan は、ホログラムを設計するためのクリエイティブなディレクターであり、現在、サンフランシスコにおけるマイクロソフトの Mixed Reality Academy の設計リードとして機能しています。これは、以前はロンドンの Microsoft の Mixed Reality スタジオの1つであるデザイナーでした。</span><span class="sxs-lookup"><span data-stu-id="501d1-217">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="501d1-218"><b>Martin Wettig</b></span><span class="sxs-lookup"><span data-stu-id="501d1-218"><b>Martin Wettig</b></span></span><br><span data-ttu-id="501d1-219"><i>シニア3D アーティスト</i></span><span class="sxs-lookup"><span data-stu-id="501d1-219"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="501d1-220">Martin は、ホログラムの設計に関する3D アートと UI 設計をリードしています。これまでは、ベルリンの Microsoft の混合現実スタジオにあるシニア3D アーティストでした。</span><span class="sxs-lookup"><span data-stu-id="501d1-220">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist at one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="501d1-221">多くの知識を共有するために、Mixed Reality 設計チームに感謝しています。また、プロジェクトのすべての手順を通じてチームが不可欠であることを理解するために、 [オブジェクト理論](https://objecttheory.com/) のすばらしい人々に感謝しています。</span><span class="sxs-lookup"><span data-stu-id="501d1-221">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge, and to the amazing folks at [Object Theory](https://objecttheory.com/) for being essential teammates through every step of the project.</span></span> <span data-ttu-id="501d1-222">情熱と特別な設計のために、すばらしい人材に感謝します。</span><span class="sxs-lookup"><span data-stu-id="501d1-222">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="501d1-223">デザインホログラムアプリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="501d1-223">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)