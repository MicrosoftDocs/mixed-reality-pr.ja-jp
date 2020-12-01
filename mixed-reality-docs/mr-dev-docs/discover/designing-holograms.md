---
title: ホログラムのデザイン
description: Microsoft が新しく設計したホログラムアプリケーションを使用して、Mixed Reality について説明します。
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, ホログラム, ホログラムの設計, 学習, サンプルアプリ, mixed reality ヘッドセット, 仮想現実のヘッドセット, 仮想現実とは
ms.openlocfilehash: 243b6f28da7b074b3ff6d48794d525ac08281fa7
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/30/2020
ms.locfileid: "96355435"
---
# <a name="the-making-of-designing-holograms"></a><span data-ttu-id="a56cc-104">ホログラムの設計</span><span class="sxs-lookup"><span data-stu-id="a56cc-104">The making of Designing Holograms</span></span>

> [!NOTE]
> <span data-ttu-id="a56cc-105">小さい読み込みウィンドウで、このページのすべてのクール Gif と埋め込みビデオを考慮するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="a56cc-105">Please allow for a small loading window to account for all the cool GIFs and embedded videos on this page.</span></span>

<span data-ttu-id="a56cc-106">混合現実向けに設計する方法については、特に、どのようにしてメディアがどのようになるかを理解することが難しい場合があります。</span><span class="sxs-lookup"><span data-stu-id="a56cc-106">Learning how to design for mixed reality can be hard, especially with how visual the medium is, which doesn't always translate well to 2D design processes.</span></span> <span data-ttu-id="a56cc-107">Microsoft では、HoloLens 2 用にダウンロードできる無料のアプリを作成しました。これは、じを使用して、mixed reality UX の設計の基礎を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a56cc-107">Here at Microsoft, we've created a free app you can download for the HoloLens 2, which helps you learn the fundamentals of mixed reality UX Design by experiencing it firsthand.</span></span> <span data-ttu-id="a56cc-108">独自の魅力的ですばらしい HoloLens アプリを作成するのに役立つように、複数の現実の行動、ヒント、および推奨事項にダイブするために、ホログラムアプリを設計するための独自のアプローチを採用しています。</span><span class="sxs-lookup"><span data-stu-id="a56cc-108">The unique approach of the Designing Holograms app dives into mixed reality behaviors, tips, and recommendations to help you create engaging and amazing HoloLens apps of your own.</span></span> <span data-ttu-id="a56cc-109">Microsoft Store からアプリを無料でダウンロードし、Microsoft の Mixed Reality 設計チームから学ぶことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a56cc-109">Download the app for free from the Microsoft Store and learn from Microsoft’s Mixed Reality Design Team!</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a56cc-110">デザインホログラムアプリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="a56cc-110">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![デザインホログラムのデモ室にあるヘッド追跡シーンのアニメーション GIF](images/designing-holograms/demo-room.gif)

<span data-ttu-id="a56cc-112">*ホログラムのデモ室 (人形家とも呼ばれます) の設計*</span><span class="sxs-lookup"><span data-stu-id="a56cc-112">*Designing Hologram’s demo room (also known as the doll house)*</span></span>

## <a name="designing-for-mixed-reality"></a><span data-ttu-id="a56cc-113">Mixed reality の設計</span><span class="sxs-lookup"><span data-stu-id="a56cc-113">Designing for mixed reality</span></span>

<span data-ttu-id="a56cc-114">多くのユーザーと同じように、私はモバイルアプリの設計に使用しました。</span><span class="sxs-lookup"><span data-stu-id="a56cc-114">Like many of you, I used to design mobile apps.</span></span> <span data-ttu-id="a56cc-115">2D デザイン環境では、すべてが現在世界中である空間コンピューティングについて詳しく解説してきましたが、大きなシフトでした。</span><span class="sxs-lookup"><span data-stu-id="a56cc-115">Coming from a 2D design world, jumping into full on spatial computing, where everything is now in the world, was a significant shift.</span></span> <span data-ttu-id="a56cc-116">Mixed reality では、アプリが2D 画面に限定されなくなりました。実際には、実世界に配置され、実際のオブジェクトとやり取りしています。</span><span class="sxs-lookup"><span data-stu-id="a56cc-116">In mixed reality, apps aren't confined to a 2D screen anymore; in fact, they're almost free, placed in the real world and interacting with real objects.</span></span>

<span data-ttu-id="a56cc-117">私にとっては、従来の2D デザインプロセスに3D エクスペリエンスを接続することは、mixed reality 開発の最も困難な側面です。</span><span class="sxs-lookup"><span data-stu-id="a56cc-117">To me, connecting 3D experiences to conventional 2D design processes is the most challenging aspect of mixed reality development.</span></span> <span data-ttu-id="a56cc-118">「お客様との会話」では、"どのような機能が含まれているか、およびそれらをどのように稼働させるかを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="a56cc-118">In conversations with customers, I would hear things like “I know what features to include and how to get them up and running.</span></span> <span data-ttu-id="a56cc-119">コードです。ドキュメントやチュートリアルに従うことはできますが、ユーザーエクスペリエンスは、</span><span class="sxs-lookup"><span data-stu-id="a56cc-119">It’s code, I can follow the docs and tutorials, but the user experience?</span></span> <span data-ttu-id="a56cc-120">多くの機能、さまざまな入力オプション、さまざまなシナリオ、および物理的な環境では、非常に大きな問題になります。</span><span class="sxs-lookup"><span data-stu-id="a56cc-120">So many features, different input options, different scenarios and physical environments, it’s overwhelming".</span></span>

<span data-ttu-id="a56cc-121">![サンフランシスコの ](images/designing-holograms/workshop.jpeg)
 *hololens 2* 設計ワークショップによるサンフランシスコでの Hololens 2 設計ワークショップの画像</span><span class="sxs-lookup"><span data-stu-id="a56cc-121">![Image from the HoloLens 2 Design Workshop in San Francisco](images/designing-holograms/workshop.jpeg)
*Image from the HoloLens 2 Design Workshop in San Francisco*</span></span>

## <a name="an-opportunity-to-teach"></a><span data-ttu-id="a56cc-122">教える機会</span><span class="sxs-lookup"><span data-stu-id="a56cc-122">An opportunity to teach</span></span>

<span data-ttu-id="a56cc-123">最初は明らかではありませんでしたが、mixed reality を1つのメディアとして使用して説明するための優れた機会が提供されました。</span><span class="sxs-lookup"><span data-stu-id="a56cc-123">It wasn’t obvious at first, but an excellent opportunity was presented to use mixed reality as a Medium to teach it.</span></span>

<span data-ttu-id="a56cc-124">ホログラムの設計は、mixed reality の設計概念と推奨事項について説明するビジュアルエクスペリエンスです。</span><span class="sxs-lookup"><span data-stu-id="a56cc-124">Designing Holograms is a visual experience that explains mixed reality design concepts and recommendations.</span></span> <span data-ttu-id="a56cc-125">自分と仮想教師が混合現実の設計概念をデモンストレーションしているだけです。</span><span class="sxs-lookup"><span data-stu-id="a56cc-125">It’s just you and a virtual teacher demonstrating mixed reality design concepts.</span></span> <span data-ttu-id="a56cc-126">私たちは、お客様のスペースにしっかりと経験を持っています。</span><span class="sxs-lookup"><span data-stu-id="a56cc-126">Everything is from a third person perspective with the experience firmly in your own space.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

<span data-ttu-id="a56cc-127">*ホログラムトレーラービデオの設計*</span><span class="sxs-lookup"><span data-stu-id="a56cc-127">*Designing Holograms trailer video*</span></span>

## <a name="exploring-the-doll-house"></a><span data-ttu-id="a56cc-128">人形の家を調べる</span><span class="sxs-lookup"><span data-stu-id="a56cc-128">Exploring the doll house</span></span>

<span data-ttu-id="a56cc-129">人形ハウスは、アプリ全体で使用する仮想環境で、80 x 60 x 40 cm の小さな部屋で、ほとんどの部屋が共通している基本的な要素 (壁、ランプ、家具、テーブル、テレビなど) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a56cc-129">The doll house is the virtual environment we use throughout the app, an 80 x 60 x 40-cm miniature room that contains the basic elements that most rooms have in common, like walls, lamps, furniture, a table, and a TV.</span></span> <span data-ttu-id="a56cc-130">人形ハウスはアプリエクスペリエンスの主要な主役であるため、どの環境でもうまく機能することを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a56cc-130">The doll house is the main protagonist of the app experience, so we needed to make sure that it would work great in any environment.</span></span> <span data-ttu-id="a56cc-131">これは、あらゆる種類の混合現実概念を視覚化するための小さなデモ室と考えてください。</span><span class="sxs-lookup"><span data-stu-id="a56cc-131">Think of it as a small demo room for visualizing all sorts of mixed reality concepts.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
<span data-ttu-id="a56cc-132">*Dollhouse 調整動作のビデオ*</span><span class="sxs-lookup"><span data-stu-id="a56cc-132">*Video of the Dollhouse adjustment behavior*</span></span>

### <a name="11-vs-110-prototypes"></a><span data-ttu-id="a56cc-133">1:1 対1:10 プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="a56cc-133">1:1 vs 1:10 prototypes</span></span>

<span data-ttu-id="a56cc-134">最初の前提として、1:1 のデモはすばらしい教師であると思います。</span><span class="sxs-lookup"><span data-stu-id="a56cc-134">Our initial assumption was that 1:1 demonstrations would be amazing, almost like looking at a real life teacher.</span></span> <span data-ttu-id="a56cc-135">このユーザーには、教師が実際の有効期間に見ているものがすべて表示されます。</span><span class="sxs-lookup"><span data-stu-id="a56cc-135">The user would see everything that the teacher sees at a real life scale.</span></span> <span data-ttu-id="a56cc-136">しかし、すぐに問題が発生することに気付きます。</span><span class="sxs-lookup"><span data-stu-id="a56cc-136">However, we immediately realized that there would be a few problems:</span></span>

- <span data-ttu-id="a56cc-137">ほとんどの開発者は、オフィスで、またはデモ室より小さい部屋でアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="a56cc-137">Most developers will run their apps in offices, or rooms smaller than the demo room, so it wouldn’t fit.</span></span>
- <span data-ttu-id="a56cc-138">表示は加法です。つまり、仮想環境全体がユーザーの部屋に重なって表示されます。</span><span class="sxs-lookup"><span data-stu-id="a56cc-138">Displays are additive, meaning the entire virtual environment will be overlaid over a user’s room.</span></span> <span data-ttu-id="a56cc-139">2つのテーブルで混乱を招く可能性があります。おそらく、2つの couches と、アラインされていない壁面です。</span><span class="sxs-lookup"><span data-stu-id="a56cc-139">That can get confusing with two tables, maybe double couches and walls that don’t align.</span></span>
- <span data-ttu-id="a56cc-140">また、ビューのフィールドによって制約されているすべての仮想環境のうち、最悪のものがあります。</span><span class="sxs-lookup"><span data-stu-id="a56cc-140">And worst of all a virtual environment heavily constrained by a field of view.</span></span>

<span data-ttu-id="a56cc-141">ミニ1:10 スケールを試したときに、結果は現実的な部屋を見てきました。このビューでは、あらゆる角度からすべてを同時に確認できます。</span><span class="sxs-lookup"><span data-stu-id="a56cc-141">When we tried out a mini 1:10 scale, the result was a fantastic birds-eye view of a realistic room where you could see everything that was going on from any angle and all at the same time.</span></span> <span data-ttu-id="a56cc-142">最も驚くべきことは、ほとんどのテスト担当者が、小規模なバージョンを確認するために多くのものを見つけた後、1:1 スケールに切り替えられないことです。</span><span class="sxs-lookup"><span data-stu-id="a56cc-142">What was most surprising is that most testers found it so much more immersive to see a small version, then they never toggled back to the 1:1 scale.</span></span> <span data-ttu-id="a56cc-143">そのため、1:1 バージョンを実際に廃棄し、UI やアプリのその他の側面を調整するために必要な余分な作業を回避することにしました。</span><span class="sxs-lookup"><span data-stu-id="a56cc-143">So we decided to actually scrap the 1:1 version and avoid the extra work required to adapt UI and other aspects of the app.</span></span>

<span data-ttu-id="a56cc-144">![1:1 スケールのフィールドと ](images/designing-holograms/1-1-scale.png)
 *1:1 scale の* ビューのフィールド</span><span class="sxs-lookup"><span data-stu-id="a56cc-144">![Field of view with 1:1 scale](images/designing-holograms/1-1-scale.png)
*Field of view with 1:1 scale*</span></span>

<span data-ttu-id="a56cc-145">![1:10 スケールのフィールドと ](images/designing-holograms/1-10-scale.png)
 *1:10 scale の* ビューのフィールド</span><span class="sxs-lookup"><span data-stu-id="a56cc-145">![Field of view with 1:10 scale](images/designing-holograms/1-10-scale.png)
*Field of view with 1:10 scale*</span></span>

## <a name="using-mixed-reality-capture"></a><span data-ttu-id="a56cc-146">Mixed Reality キャプチャの使用</span><span class="sxs-lookup"><span data-stu-id="a56cc-146">Using Mixed Reality Capture</span></span>

<span data-ttu-id="a56cc-147">このアプリの最も重要な特徴の1つは、mixed reality のキャプチャを使用して、mixed reality の設計概念を学習し、デモンストレーションすることです。</span><span class="sxs-lookup"><span data-stu-id="a56cc-147">One of the most characteristic features of this app is the use of Mixed Reality Capture to teach and demonstrate mixed reality design concepts.</span></span>

<span data-ttu-id="a56cc-148">Microsoft は、サンフランシスコに Mixed Reality Capture studio を持っています。</span><span class="sxs-lookup"><span data-stu-id="a56cc-148">Microsoft has a Mixed Reality Capture studio in San Francisco.</span></span> <span data-ttu-id="a56cc-149">また、このテクノロジは他のスタジオにもライセンス供与されています。これには、ワシントン D.C. にあるアバターディメンション、ロサンゼルスのメタステージ、ロンドンのディメンションスタジオ、ソウルでの、および Volucap (ベルリン) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a56cc-149">Microsoft also licenses this technology to other studios, which include Avatar Dimension in Washington D.C., Metastage in Los Angeles, Dimension Studios in London, SK Telecom in Seoul, and Volucap in Berlin.</span></span> <span data-ttu-id="a56cc-150">詳細については、 [こちら](https://www.microsoft.com/mixed-reality/capture-studios)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a56cc-150">You can find more information on our [Mixed Reality Capture Studios here](https://www.microsoft.com/mixed-reality/capture-studios).</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="a56cc-151">*サンフランシスコの混合 Reality Capture Studio にある106カメラの1つからの Daniel Escudero の生の映像。*</span><span class="sxs-lookup"><span data-stu-id="a56cc-151">*Raw footage of Daniel Escudero from one of the 106 cameras in the Mixed Reality Capture Studio in San Francisco.*</span></span>

<span data-ttu-id="a56cc-152">キャプチャプロセスでは、keyframed メッシュ、法線、およびテクスチャが生成されます。これは、さらに実稼働後に OBJ/PNG ファイルとして提供されるか、または h.264 圧縮 MP4 ファイルとして再生できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="a56cc-152">The capture process generates a keyframed mesh, normals, and texture, which can be delivered as OBJ/PNG files for further post-production, or ready for playback as an H.264 compressed MP4 file.</span></span> <span data-ttu-id="a56cc-153">これらのファイルは、Unity、Unreal、native、WebXR にインポートして、Windows、iOS、Mac、Android、マジック Leap、Playstation VR で実行できます。</span><span class="sxs-lookup"><span data-stu-id="a56cc-153">These files can be imported into Unity, Unreal, native, and WebXR and run on Windows, iOS, Mac, Android, Magic Leap, and Playstation VR.</span></span>

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
<span data-ttu-id="a56cc-154">*オーディオと埋め込みメッシュを含むビデオを含む mp4 を分析するために用意されているキャプチャプレーヤー。*</span><span class="sxs-lookup"><span data-stu-id="a56cc-154">*The Capture Player provided to analyze mp4s that contain video with audio and embedded meshes.*</span></span>

## <a name="manipulating-captures-and-virtual-objects"></a><span data-ttu-id="a56cc-155">キャプチャと仮想オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="a56cc-155">Manipulating captures and virtual objects</span></span>

<span data-ttu-id="a56cc-156">Mixed Reality では、ユーザーまたは動物の仮想表現が生成されますが、他の仮想オブジェクトと対話するためにこれらの文字が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a56cc-156">Mixed Reality Captures produce virtual representations of people or animals, but at times you may need those characters to interact with other virtual objects.</span></span> <span data-ttu-id="a56cc-157">次の2つの例は、この効果を実現するためにシーンを操作するさまざまな方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a56cc-157">The following two examples show different ways we manipulated the scenes to achieve this effect.</span></span>

### <a name="head-gaze-adjustment"></a><span data-ttu-id="a56cc-158">ヘッドを見つめた調整</span><span class="sxs-lookup"><span data-stu-id="a56cc-158">Head Gaze Adjustment</span></span>

<span data-ttu-id="a56cc-159">ヘッド見つめ調整を使用すると、キャプチャしたユーザーのヘッドを実行時に移動できます。つまり、ユーザーに対してキャプチャを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a56cc-159">Headgaze adjustment lets you to move a captured person’s head at runtime, meaning you could have a capture face towards a user.</span></span> <span data-ttu-id="a56cc-160">ここでは、ビューと目的のフィールドを表示するために使用しています。</span><span class="sxs-lookup"><span data-stu-id="a56cc-160">In our case, we used it to show the field of view and field of interest.</span></span> <span data-ttu-id="a56cc-161">次に示すのは、移動するためのターゲットとして機能する移動中のオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="a56cc-161">What you see below is a moving gameobject acting as a target for the head gaze to look at.</span></span> <span data-ttu-id="a56cc-162">ターゲットを左右に移動すると、キャプチャの先頭は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a56cc-162">As we move the target from side to side, the head of the capture follows.</span></span>

<span data-ttu-id="a56cc-163">このトリックを使用して、人形ハウスのさまざまな部分に配置されているホログラムに対してアイドルキャプチャが常に直面していることを確認しています。</span><span class="sxs-lookup"><span data-stu-id="a56cc-163">We used this trick to make sure that the idle capture would always face towards holograms placed in different parts of the doll house.</span></span> 

![Unity のターゲットのオブジェクトに従って、実行時にキャプチャのヘッドを移動しています](images/designing-holograms/head-adjustment.gif)

<span data-ttu-id="a56cc-165">*Unity のターゲットのオブジェクトに従って、実行時にキャプチャのヘッドを移動します。*</span><span class="sxs-lookup"><span data-stu-id="a56cc-165">*The Capture’s head being moved at runtime following a target gameobject in Unity.*</span></span>

### <a name="syncing-animated-objects"></a><span data-ttu-id="a56cc-166">同期 (アニメーションオブジェクトを)</span><span class="sxs-lookup"><span data-stu-id="a56cc-166">Syncing Animated Objects</span></span>

<span data-ttu-id="a56cc-167">2つ目は、キャプチャの移動と同期するためにオブジェクトをアニメーション化していました。</span><span class="sxs-lookup"><span data-stu-id="a56cc-167">The second one, was animating objects to sync with a capture’s movement.</span></span> <span data-ttu-id="a56cc-168">アプリのさまざまな部分で、5フレームごとに特定のキャプチャのシーケンシャル Obj をインポートしました。</span><span class="sxs-lookup"><span data-stu-id="a56cc-168">In different parts of the app, we imported sequential OBJs of a specific capture every five frames.</span></span> <span data-ttu-id="a56cc-169">次に、Obj はシーンでアニメーション化され、キャプチャの対応するフレームと一致することが確認されます。</span><span class="sxs-lookup"><span data-stu-id="a56cc-169">The OBJs were then animated in the scene to make sure they would match the corresponding frame of the capture.</span></span> <span data-ttu-id="a56cc-170">これは、アニメーション化と表示操作の面倒なプロセスですが、結果は優れています。これにより、キャプチャされていないオブジェクトと相互作用する Mixed Reality キャプチャが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="a56cc-170">It’s a tedious process of animating and keyframing, but the result is great, you can now see a Mixed Reality Capture interacting with non-captured objects.</span></span>

![混合 Reality キャプチャと UI パネル間で同期されたアニメーション](images/designing-holograms/synced-objects.gif)

<span data-ttu-id="a56cc-172">*混合 Reality キャプチャと UI パネル間で同期されたアニメーション*</span><span class="sxs-lookup"><span data-stu-id="a56cc-172">*Synced animation between a Mixed Reality Capture and UI panel*</span></span>

### <a name="ui-creative-process"></a><span data-ttu-id="a56cc-173">UI クリエイティブプロセス</span><span class="sxs-lookup"><span data-stu-id="a56cc-173">UI creative process</span></span>

<span data-ttu-id="a56cc-174">UI デザインの作成を開始したときに、情報の転送だけでなく、ホログラムによって提供される可能性のあるマジックと可能性を示すことも必要でした。</span><span class="sxs-lookup"><span data-stu-id="a56cc-174">When we started ideating the UI design, besides from transporting information we also wanted to show some of the magic and the possibilities that holograms have to offer.</span></span> <span data-ttu-id="a56cc-175">単純に、静的な2D ウィンドウとテキストボックスを表示するのは3D の世界には適しておらず、多くの可能性はありません。そのため、最初から、holographic の3D 空間を最大限に活用することにしました。</span><span class="sxs-lookup"><span data-stu-id="a56cc-175">Simply showing static 2D windows and text boxes doesn’t feel right in the 3D world and doesn’t show many of the possibilities at hand, so right from the beginning we decided to move away from that and make full use of holographic 3D space.</span></span>

<span data-ttu-id="a56cc-176">最初に、テキスト情報だけでなく、パネルとアイコンにもいくつかの太さを追加しました。</span><span class="sxs-lookup"><span data-stu-id="a56cc-176">At first, we started with adding some thickness to the panels and icons in addition to text information.</span></span> <span data-ttu-id="a56cc-177">それでも、ユーザーとしては、テキストボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a56cc-177">Still, as a user, what I see is a text box.</span></span> <span data-ttu-id="a56cc-178">画像を含むテキストボックスが表示されません。</span><span class="sxs-lookup"><span data-stu-id="a56cc-178">Text boxes with images, but we are not there.</span></span> <span data-ttu-id="a56cc-179">Mixed Reality Toolkit (MRTK) シェーダーを使用することによってさらに問題が発生しました。</span><span class="sxs-lookup"><span data-stu-id="a56cc-179">We went further by making use of the Mixed Reality Toolkit (MRTK) shaders.</span></span> <span data-ttu-id="a56cc-180">MRTK シェーダーは強力なツールになりました。そのステンシル機能を使用しています。そのため、パネルに負の深度を追加すると、ポータルの効果として認識されることがあります。</span><span class="sxs-lookup"><span data-stu-id="a56cc-180">The MRTK shaders became a powerful tool, and we made use of its stencil features, some may know it as the portal effect, to add negative depth to the panels.</span></span> <span data-ttu-id="a56cc-181">つまり、テキストボックスの前に要素を追加するのではなく、透明なパネルの背後にアイコンが表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a56cc-181">That means instead of adding elements in front of a text box, the icons now appear behind a transparent panel.</span></span> <span data-ttu-id="a56cc-182">現在、ユーザーとして表示されているのは、実際にはレプリケートできないことです。これは、holographic マジックが発生し始めたところです。</span><span class="sxs-lookup"><span data-stu-id="a56cc-182">What I see now as a user is something that I just can’t replicate anymore in the real world, and this is where holographic magic started to happen.</span></span> <span data-ttu-id="a56cc-183">また、実際にはお読みたくないユーザーとして、既に物理的な世界にいます。</span><span class="sxs-lookup"><span data-stu-id="a56cc-183">Also as a user I don’t really like to read, I do that a lot already in the physical world.</span></span>

<span data-ttu-id="a56cc-184">明らかにアイコンは、単純なテキストよりもはるかに優れています。そのため、さらに強力なガイダンスを提供するために、一連のアニメーションオブジェクトとアバターの作成を開始し、それぞれのシナリオで何が行われているか、およびその使用方法についての小さなストーリーを示しています。</span><span class="sxs-lookup"><span data-stu-id="a56cc-184">Obviously icons work a lot better than simple text does, so in order to provide an even more powerful guidance, I then started creating a set of animated objects and avatars, each of them telling a tiny story about what is being done in the respective scenario and how it’s being used.</span></span>

![対話型の holographic メニューシステムのアニメーション GIF](images/designing-holograms/creative-process.gif)

## <a name="try-it-out-moments"></a><span data-ttu-id="a56cc-186">"試してみる"</span><span class="sxs-lookup"><span data-stu-id="a56cc-186">"Try it out" moments</span></span>

<span data-ttu-id="a56cc-187">ホログラムを設計すると、mixed reality の概念が説明されますが、ルームでも試してみることができます。</span><span class="sxs-lookup"><span data-stu-id="a56cc-187">Designing Holograms teaches mixed reality concepts, but it also allows you to try them in your room.</span></span> <span data-ttu-id="a56cc-188">これらの説明の後に、人形の家を一時停止して、対話的な時間を取ります。</span><span class="sxs-lookup"><span data-stu-id="a56cc-188">After some of those explanations, we pause and take you out of the doll house and into an interactive moment.</span></span> <span data-ttu-id="a56cc-189">これらの対話型の瞬間の例をいくつか次に示します。</span><span class="sxs-lookup"><span data-stu-id="a56cc-189">Here are some examples of those interactive moments:</span></span>

![ハンドが検出されたときと、ビューのフィールドに入るタイミングを示す、ハンドトラッキングフレームのアニメーション GIF](images/designing-holograms/try-out-1.gif)

<span data-ttu-id="a56cc-191">*ハンドが検出されたときと、そのフィールドに表示されるタイミングを示すハンドトラッキングフレーム。*</span><span class="sxs-lookup"><span data-stu-id="a56cc-191">*The hand tracking frame showing when hands are detected and when they enter the field of view.*</span></span>

![遠隔操作による競合の crystals と対話するアニメーション GIF](images/designing-holograms/try-out-2.gif)

<span data-ttu-id="a56cc-193">*遠隔操作による衝突の crystals との対話*</span><span class="sxs-lookup"><span data-stu-id="a56cc-193">*Interacting with colliding crystals through far interaction*</span></span>

![相互作用 affordances を調べるためのアニメーション GIF](images/designing-holograms/try-out-3.gif)

<span data-ttu-id="a56cc-195">*Near 対話 affordances の探索*</span><span class="sxs-lookup"><span data-stu-id="a56cc-195">*Exploring near interaction affordances*</span></span>

## <a name="about-the-team"></a><span data-ttu-id="a56cc-196">チームについて</span><span class="sxs-lookup"><span data-stu-id="a56cc-196">About the team</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="a56cc-197"><b>Daniel Escudero</b></span><span class="sxs-lookup"><span data-stu-id="a56cc-197"><b>Daniel Escudero</b></span></span><br><span data-ttu-id="a56cc-198"><i>リーダーのテクニカルデザイナー</i></span><span class="sxs-lookup"><span data-stu-id="a56cc-198"><i>Lead Technical Designer</i></span></span><br><span data-ttu-id="a56cc-199">Dan は、ホログラムを設計するためのクリエイティブなディレクターであり、現在、サンフランシスコにおけるマイクロソフトの Mixed Reality Academy の設計リードとして機能しています。これは、以前はロンドンの Microsoft の Mixed Reality スタジオの1つであるデザイナーでした。</span><span class="sxs-lookup"><span data-stu-id="a56cc-199">Dan is the Creative Director on Designing Holograms and currently works as Design Lead for the Microsoft’s Mixed Reality Academy in San Francisco, and was previously a Designer in one of Microsoft’s Mixed Reality Studios in London.</span></span></td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><span data-ttu-id="a56cc-200"><b>Martin Wettig</b></span><span class="sxs-lookup"><span data-stu-id="a56cc-200"><b>Martin Wettig</b></span></span><br><span data-ttu-id="a56cc-201"><i>シニア3D アーティスト</i></span><span class="sxs-lookup"><span data-stu-id="a56cc-201"><i>Senior 3D Artist</i></span></span><br><span data-ttu-id="a56cc-202">Martin は、ホログラムの設計に関する3D アートと UI 設計をリードしています。これは、ベルリンの Microsoft の混合現実スタジオの1つであるシニア3D アーティストでした。</span><span class="sxs-lookup"><span data-stu-id="a56cc-202">Martin leads 3D Art and UI Design on Designing Holograms and was previously a Senior 3D Artist in one of Microsoft’s Mixed Reality Studios in Berlin.</span></span></td>
</tr>
</table>

<span data-ttu-id="a56cc-203">このプロジェクトの1つの手順でチームメートが重要なチームを持つことができるようになったので、多くの知識を共有し、 [オブジェクト理論](https://objecttheory.com/) のすばらしい人たちにとっては、複雑な現実の設計チームに感謝します。</span><span class="sxs-lookup"><span data-stu-id="a56cc-203">A huge thank you to the Mixed Reality Design Team for sharing so much knowledge and of course to the amazing folks at [Object Theory](https://objecttheory.com/) that became essential teammates in every single step of this project.</span></span> <span data-ttu-id="a56cc-204">情熱と特別な設計のために、すばらしい人材に感謝します。</span><span class="sxs-lookup"><span data-stu-id="a56cc-204">Thank you all for you amazing talent, for your passion and exceptional eye for design.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a56cc-205">デザインホログラムアプリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="a56cc-205">Download the Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)