---
title: 設計とプロトタイプ作成を始める
description: 何かを作成する準備ができたら、設計とプロトタイプ作成を開始するために必要な基本的な概念について学習しましょう。
author: grbury
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 検出, 配布, インデックス, ランディング ページ, 設計, 開発, チュートリアル, サンプル アプリ, 基本事項, ケース スタディ, リソース, HoloLens の使い方, オープン ソース プロジェクト, 主要な概念, 操作, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f4a4ea50c45263f18079da76dd8dfd5f31e2af44
ms.sourcegitcommit: 44d0f2873c75003caf9d8d244ceaeb3faa89df63
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/12/2021
ms.locfileid: "98110450"
---
# <a name="start-designing-and-prototyping"></a><span data-ttu-id="3b4a5-104">設計とプロトタイプ作成を始める</span><span class="sxs-lookup"><span data-stu-id="3b4a5-104">Start designing and prototyping</span></span>

![Mixed Reality の設計の概要](images/design-hero-image.png)

<span data-ttu-id="3b4a5-106">Mixed Reality アプリケーションはまったく新しいものであるため、その設計は困難な作業です。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-106">Mixed Reality applications are unlike anything else in the world today, and designing them is hard work.</span></span> <span data-ttu-id="3b4a5-107">作成する現実および仮想世界の新たな組み合わせについてだけでなく、それによって提供される新しいユーザー エクスペリエンスについても考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-107">Not only do you have to account for the new combinations of real and virtual worlds you're creating, but also the new user experiences they afford.</span></span> <span data-ttu-id="3b4a5-108">Mixed Reality の領域は広いため、設計範囲に沿って選択した重要なポイントを一連のチェックポイントとして次に示すことにしました。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-108">Since Mixed Reality is a big place, we've selected important points along its design spectrum and laid them out below as a series of checkpoints.</span></span> <span data-ttu-id="3b4a5-109">これらは順番に取り組むことを想定していますが、既に十分な知識がある場合は、ご自由に後続の好きなセクションにスキップしてかまいません。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-109">These are meant to be sequential, but if you've already dipped your feet in feel free to jump to any of the following sections.</span></span> 

<span data-ttu-id="3b4a5-110">初めに、設計の概要に関するビデオをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-110">Take a look at our design overview video to get started:</span></span>

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4LhlW]

## <a name="design-checkpoints"></a><span data-ttu-id="3b4a5-111">設計のチェックポイント</span><span class="sxs-lookup"><span data-stu-id="3b4a5-111">Design checkpoints</span></span>

<span data-ttu-id="3b4a5-112">次のチェックポイントを使用して、アプリケーションのアイデアや概念を Mixed Reality の世界に移植することができます。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-112">Use the following checkpoints to bring your application ideas and concepts into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="3b4a5-113">1.はじめに</span><span class="sxs-lookup"><span data-stu-id="3b4a5-113">1. Getting started</span></span>

<span data-ttu-id="3b4a5-114">あらゆる作業と同様に、Mixed Reality アプリケーションの設計も基礎から始めます。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-114">Like all journeys, your adventure into designing Mixed Reality applications starts with the basics.</span></span> <span data-ttu-id="3b4a5-115">イマーシブ デザインに取りかかる前に、「[Mixed Reality とは](../discover/mixed-reality.md)」と「[ホログラムとは](../discover/hologram.md)」の記事を理解しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-115">We recommend familiarizing yourself with the [What is Mixed Reality](../discover/mixed-reality.md) and [What is a hologram?](../discover/hologram.md) articles to get your mind primed for immersive design.</span></span> <span data-ttu-id="3b4a5-116">読み終えれば、Mixed Reality の設計作業を開始する準備が整っているでしょう。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-116">Once you've completed your read-through, you'll be ready to start your Mixed Reality design journey!</span></span>

![Designing Holograms アプリの紹介 GIF](images/HandTracking2.gif)

|  <span data-ttu-id="3b4a5-118">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="3b4a5-118">Checkpoint</span></span>  |  <span data-ttu-id="3b4a5-119">結果</span><span class="sxs-lookup"><span data-stu-id="3b4a5-119">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="3b4a5-120">デザイン プロセスを展開する</span><span class="sxs-lookup"><span data-stu-id="3b4a5-120">Expand your design process</span></span>](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | <span data-ttu-id="3b4a5-121">Microsoft 内外の設計者から収集された Mixed Reality のデザイン プロセスを直接確認する</span><span class="sxs-lookup"><span data-stu-id="3b4a5-121">Get a first-hand look at design process for Mixed Reality, gathered from designers inside and outside of Microsoft</span></span> |
| [<span data-ttu-id="3b4a5-122">Mixed Reality アプリの種類</span><span class="sxs-lookup"><span data-stu-id="3b4a5-122">Types of Mixed Reality apps</span></span>](types-of-mixed-reality-apps.md) | <span data-ttu-id="3b4a5-123">Mixed Reality の範囲のうち、どの領域のアプリ エクスペリエンスを実現するかを決定する</span><span class="sxs-lookup"><span data-stu-id="3b4a5-123">Decide where your app experience will live on the Mixed Reality spectrum</span></span> |
| [<span data-ttu-id="3b4a5-124">Designing Holograms アプリ</span><span class="sxs-lookup"><span data-stu-id="3b4a5-124">Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | <span data-ttu-id="3b4a5-125">優れた HoloLens アプリを作成するための動作、ヒント、推奨事項 (Microsoft Store の HoloLens 2 からダウンロード可能) を体験して、Mixed Reality UX Design の基礎を理解する</span><span class="sxs-lookup"><span data-stu-id="3b4a5-125">Learn the fundamentals of Mixed Reality UX Design by experiencing with behaviors, tips, and recommendations for creating amazing HoloLens apps (available for download from Microsoft Store in HoloLens 2)</span></span> |
| [<span data-ttu-id="3b4a5-126">MRTK Examples Hub</span><span class="sxs-lookup"><span data-stu-id="3b4a5-126">MRTK Examples Hub</span></span>](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4) | <span data-ttu-id="3b4a5-127">複合現実の一般的な空間操作と UX 構成要素を体験する (HoloLens 2 の Microsoft Store からダウンロード可能)</span><span class="sxs-lookup"><span data-stu-id="3b4a5-127">Experience common spatial interactions and UX building blocks for Mixed Reality (available for download from Microsoft Store in HoloLens 2)</span></span> |

### <a name="2-core-concepts"></a><span data-ttu-id="3b4a5-128">2. 主要な概念</span><span class="sxs-lookup"><span data-stu-id="3b4a5-128">2. Core concepts</span></span>

<span data-ttu-id="3b4a5-129">開発対象が VR でも AR でも、柔軟なイマーシブ エクスペリエンスの設計には、いくつかの主要な概念が適用されます。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-129">Whether you're developing for VR or AR, there are several core concepts that apply to designing fluid immersive experiences.</span></span> <span data-ttu-id="3b4a5-130">ユーザーの視点を理解し、オブジェクトを配置し、すべてのユーザーの快適性と安全性を確保することが、お客様の作業のこの段階における最優先事項です。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-130">Understanding the users point of view, positioning objects, and ensuring everyone is comfortable and safe are your top priorities at this stage of your journey.</span></span> <span data-ttu-id="3b4a5-131">このセクションが完了する頃には、操作の設計まで全体を通して役に立つ強固な基盤が手に入ります。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-131">By the end of this section you'll have a solid foundation to carry through into interaction design.</span></span>

![主要な概念の例の画像](images/fragments-750px.jpg)

|  <span data-ttu-id="3b4a5-133">概念</span><span class="sxs-lookup"><span data-stu-id="3b4a5-133">Concept</span></span>  |  <span data-ttu-id="3b4a5-134">結果</span><span class="sxs-lookup"><span data-stu-id="3b4a5-134">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="3b4a5-135">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="3b4a5-135">Holographic frame</span></span>](holographic-frame.md) | <span data-ttu-id="3b4a5-136">ヘッドセットの装着時、現実世界に重ねて表示されたコンテンツがユーザーにどのように見えるかを理解する</span><span class="sxs-lookup"><span data-stu-id="3b4a5-136">Understand how users see your content overlaid onto the real world when wearing their headsets</span></span> |
| [<span data-ttu-id="3b4a5-137">座標系</span><span class="sxs-lookup"><span data-stu-id="3b4a5-137">Coordinate systems</span></span>](coordinate-systems.md) | <span data-ttu-id="3b4a5-138">物理的な部屋であれ、自分が作成した仮想領域であれ、空間内の意味のある位置にホログラムを配置する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="3b4a5-138">Learn how to position holograms in meaningful places in the world, whether it's their physical room or a virtual realm you've created</span></span> |
| [<span data-ttu-id="3b4a5-139">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="3b4a5-139">Spatial mapping</span></span>](spatial-mapping.md) | <span data-ttu-id="3b4a5-140">オブジェクトをユーザーの世界に固定し、現実世界の物理サーフェスを利用する</span><span class="sxs-lookup"><span data-stu-id="3b4a5-140">Anchor objects in the user's world and take advantage of real world's physical surfaces</span></span> |
| [<span data-ttu-id="3b4a5-141">快適性に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="3b4a5-141">Comfort considerations</span></span>](comfort.md) | <span data-ttu-id="3b4a5-142">自然世界を模倣した方法でイマーシブ コンテンツの作成と提示を行うことで、ユーザーの快適性と安全性を確保する</span><span class="sxs-lookup"><span data-stu-id="3b4a5-142">Ensure user comfort and safety by creating and presenting immersive content in a way that mimics the natural world</span></span> |

### <a name="3-interaction-design"></a><span data-ttu-id="3b4a5-143">3.操作の設計</span><span class="sxs-lookup"><span data-stu-id="3b4a5-143">3. Interaction design</span></span>

<span data-ttu-id="3b4a5-144">仮想エクスペリエンスがどれほど美しく臨場感にあふれていても、操作ができなければ役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-144">No matter how beautiful and immersive a virtual experience is, it's useless without interaction.</span></span> <span data-ttu-id="3b4a5-145">このセクションでは、基本的な操作モデル、手とモーション コントローラー、音声入力、ユーザーからの視線追跡データの収集について説明します。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-145">This section will walk you through basic interaction models, hand and motion controllers, voice input, and gathering eye tracking data from your users.</span></span> <span data-ttu-id="3b4a5-146">このセクションが完了する頃には、設計作業における最後の大きなトピックであるユーザー エクスペリエンスに取り組む準備が整います。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-146">By the end of this section you'll be ready to tackle the last big topic on your design journey: user experience.</span></span>

![操作の設計の要素](images/UX_Hero_Manipulation.jpg)

|  <span data-ttu-id="3b4a5-148">概念</span><span class="sxs-lookup"><span data-stu-id="3b4a5-148">Concept</span></span>  |  <span data-ttu-id="3b4a5-149">結果</span><span class="sxs-lookup"><span data-stu-id="3b4a5-149">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="3b4a5-150">相互作用モデル</span><span class="sxs-lookup"><span data-stu-id="3b4a5-150">Interaction models</span></span>](interaction-fundamentals.md) | <span data-ttu-id="3b4a5-151">手、視線、音声による入力を使用した直感的な操作をユーザーに提供する</span><span class="sxs-lookup"><span data-stu-id="3b4a5-151">Provide your users with instinctual interactions through hand, eye, and voice input</span></span> |
| [<span data-ttu-id="3b4a5-152">手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="3b4a5-152">Hands and motion controllers</span></span>](hands-and-tools.md) | <span data-ttu-id="3b4a5-153">ユーザーの手で近くのホログラムを操作する方法と、遠くから正確に操作する方法について学習する</span><span class="sxs-lookup"><span data-stu-id="3b4a5-153">Learn how to interact with holograms at close range with a user' hands or at long range with precise interactions</span></span> |
| [<span data-ttu-id="3b4a5-154">音声入力</span><span class="sxs-lookup"><span data-stu-id="3b4a5-154">Voice input</span></span>](voice-input.md) | <span data-ttu-id="3b4a5-155">音声コマンドをイマーシブ アプリの入力として使用して、周囲のホログラムと環境をコントロールする</span><span class="sxs-lookup"><span data-stu-id="3b4a5-155">Use voice commands as input in your immersive apps to control surrounding holograms and environments</span></span>  |
| [<span data-ttu-id="3b4a5-156">視線追跡</span><span class="sxs-lookup"><span data-stu-id="3b4a5-156">Eye Tracking</span></span>](eye-tracking.md) | <span data-ttu-id="3b4a5-157">ユーザーが見ているものに関する情報を使用して、ホログラフィック エクスペリエンスに新しいレベルのコンテキストを追加し、人間による理解を深める</span><span class="sxs-lookup"><span data-stu-id="3b4a5-157">Add a new level of context and human understanding in a holographic experience by using information about what your users are looking at</span></span> |

### <a name="4-user-experience-elements"></a><span data-ttu-id="3b4a5-158">4.ユーザー エクスペリエンス要素</span><span class="sxs-lookup"><span data-stu-id="3b4a5-158">4. User experience elements</span></span>

<span data-ttu-id="3b4a5-159">基本的な操作を習得したので、ここからはユーザー エクスペリエンス要素のより詳細なポイントに注目して、それらを Mixed Reality 特有の環境に適合させていくことができます。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-159">Now that you've mastered basic interactions, you can focus on the finer points of user experience elements and how to adapt them for Mixed Reality's unique environments.</span></span> <span data-ttu-id="3b4a5-160">エクスペリエンスをユーザーにとって直感的に操作できるものにしながら、一般的な動作、資産の設計、オブジェクトのスケーリング、タイポグラフィについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-160">You'll cover common behaviors, asset design, object scaling, and typography, while making the experience intuitive for your users.</span></span> <span data-ttu-id="3b4a5-161">このセクションで Mixed Reality の正式な設計作業は終了します。さらに理解を深めたい場合は、「[次の操作](#whats-next)」セクションにある、その他のリソースをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-161">This section marks the end of the official Mixed Reality design journey, but there are more resources in the [What's next?](#whats-next) section to keep you going.</span></span>

![UX 要素](images/UX_Hero_BoundingBox.jpg)

|  <span data-ttu-id="3b4a5-163">概念</span><span class="sxs-lookup"><span data-stu-id="3b4a5-163">Concept</span></span>  |  <span data-ttu-id="3b4a5-164">結果</span><span class="sxs-lookup"><span data-stu-id="3b4a5-164">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="3b4a5-165">一般的なコントロールと動作</span><span class="sxs-lookup"><span data-stu-id="3b4a5-165">Common controls and behaviors</span></span>](app-patterns-landingpage.md) | <span data-ttu-id="3b4a5-166">頻繁に使用される空間操作と UI 構成要素について学習する</span><span class="sxs-lookup"><span data-stu-id="3b4a5-166">Learn about frequently used spatial interactions and UI building blocks</span></span> |
| [<span data-ttu-id="3b4a5-167">色、ライト、素材</span><span class="sxs-lookup"><span data-stu-id="3b4a5-167">Color, light, and materials</span></span>](color-light-and-materials.md) | <span data-ttu-id="3b4a5-168">色、照明、素材を考慮して、Mixed Reality 用の高品質な資産を設計する</span><span class="sxs-lookup"><span data-stu-id="3b4a5-168">Design quality assets for Mixed Reality that take color, lighting, and materials into account</span></span> |
| [<span data-ttu-id="3b4a5-169">オブジェクトのスケーリング</span><span class="sxs-lookup"><span data-stu-id="3b4a5-169">Object scale</span></span>](scale.md) | <span data-ttu-id="3b4a5-170">オブジェクトの場所、大きさ、材料をユーザーが理解しやすいように、現実世界の視覚的な手がかりを可能な限り組み込む</span><span class="sxs-lookup"><span data-stu-id="3b4a5-170">Incorporate as many real-world visual cues as possible to us help your users understand where objects are, how big they are, and what they’re made of</span></span> |
| [<span data-ttu-id="3b4a5-171">文字体裁</span><span class="sxs-lookup"><span data-stu-id="3b4a5-171">Typography</span></span>](typography.md) | <span data-ttu-id="3b4a5-172">はっきりと見える読みやすいテキストを 3 次元空間で使用して、ユーザーが必要とする重要な情報を提供する</span><span class="sxs-lookup"><span data-stu-id="3b4a5-172">Use clear, readable text in three-dimensional space to give your users the important information they need</span></span> |

## <a name="whats-next"></a><span data-ttu-id="3b4a5-173">次の操作</span><span class="sxs-lookup"><span data-stu-id="3b4a5-173">What's next?</span></span>

<span data-ttu-id="3b4a5-174">設計者の仕事に終わりはありません。新しいパラダイムでのイマーシブ エクスペリエンスの作成について学んでいる場合はなおさらです。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-174">A designer's job is never done, especially when learning to create immersive experiences in a new paradigm.</span></span> <span data-ttu-id="3b4a5-175">次のセクションでは、ここまでで説明しなかった中級以上の設計資料と、Mixed Reality の開発環境についてご紹介します。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-175">The following sections will take you beyond the beginner level design material you've already completed and into the world of Mixed Reality development.</span></span> <span data-ttu-id="3b4a5-176">これらのトピックとリソースに決まった順序はないので、お好きなものをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-176">These topics and resources aren't in any sequential order, so feel free to explore!</span></span>

### <a name="choose-a-prototyping-option"></a><span data-ttu-id="3b4a5-177">プロトタイプ作成のオプションを選択する</span><span class="sxs-lookup"><span data-stu-id="3b4a5-177">Choose a prototyping option</span></span>  

:::row:::   
    :::column:::    
       <span data-ttu-id="3b4a5-178">[![Unity について学習する](images/logo-unity.png)](https://learn.unity.com/)</span><span class="sxs-lookup"><span data-stu-id="3b4a5-178">[![Learn Unity](images/logo-unity.png)](https://learn.unity.com/)</span></span><br>
        <span data-ttu-id="3b4a5-179">**[Unity について学習する](https://learn.unity.com/)**</span><span class="sxs-lookup"><span data-stu-id="3b4a5-179">**[Learn Unity](https://learn.unity.com/)**</span></span><br>
        <span data-ttu-id="3b4a5-180">Unity で対話型エクスペリエンスを作成する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-180">Learn how to create interactive experiences with Unity.</span></span> <span data-ttu-id="3b4a5-181">最初から最後まで、実践によって学習できます。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-181">Learn by doing, from start to finish.</span></span>
    :::column-end:::    
    :::column:::    
        <span data-ttu-id="3b4a5-182">[![Mixed Reality ツールキット (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span><span class="sxs-lookup"><span data-stu-id="3b4a5-182">[![Mixed Reality Toolkit (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span></span><br>
        <span data-ttu-id="3b4a5-183">**[Mixed Reality ツールキット (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**</span><span class="sxs-lookup"><span data-stu-id="3b4a5-183">**[Mixed Reality Toolkit (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**</span></span><br>  
        <span data-ttu-id="3b4a5-184">空間操作と UI 構成ブロックを使用すると、Unity での Mixed Reality の設計と開発をすぐに始めることができます。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-184">With spatial interaction and UI building blocks, jump-start your mixed reality design and development with Unity.</span></span>   
    :::column-end:::
    :::column:::    
        <span data-ttu-id="3b4a5-185">[![Mixed Reality Design Labs](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)</span><span class="sxs-lookup"><span data-stu-id="3b4a5-185">[![Mixed Reality Design Labs](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)</span></span><br>
        <span data-ttu-id="3b4a5-186">**[Mixed Reality Design Labs](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**</span><span class="sxs-lookup"><span data-stu-id="3b4a5-186">**[Mixed Reality Design Labs](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**</span></span><br>  
        <span data-ttu-id="3b4a5-187">MRTK の構成要素を使用して美しい Mixed Reality エクスペリエンスを作成する方法を示すサンプル アプリを入手できます。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-187">Get sample apps that show you how to use MRTK's building blocks to create beautiful mixed reality experiences.</span></span>
    :::column-end:::        
    :::column:::    
        <span data-ttu-id="3b4a5-188">[![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)</span><span class="sxs-lookup"><span data-stu-id="3b4a5-188">[![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)</span></span><br>
        <span data-ttu-id="3b4a5-189">**[Microsoft Maquette](https://www.maquette.ms/)**</span><span class="sxs-lookup"><span data-stu-id="3b4a5-189">**[Microsoft Maquette](https://www.maquette.ms/)**</span></span><br>  
        <span data-ttu-id="3b4a5-190">VR 向けの設計。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-190">Design for VR.</span></span> <span data-ttu-id="3b4a5-191">Microsoft Maquette を使用すると、空間のプロトタイプ作成をすばやく、簡単、かつイマーシブに実行できます。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-191">Microsoft Maquette makes spatial prototyping easy, quick, and immersive.</span></span> 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="other-resources"></a><span data-ttu-id="3b4a5-192">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="3b4a5-192">Other resources</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="3b4a5-193">[![基本を理解する](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)</span><span class="sxs-lookup"><span data-stu-id="3b4a5-193">[![Understand the basics](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)</span></span><br>
        <span data-ttu-id="3b4a5-194">**[基本を理解する](../discover/get-started-with-mr.md#understand-the-basics)**</span><span class="sxs-lookup"><span data-stu-id="3b4a5-194">**[Understand the basics](../discover/get-started-with-mr.md#understand-the-basics)**</span></span><br>
        <span data-ttu-id="3b4a5-195">Mixed Reality が何によって定義され、どのように使用されているかについて理解を深めます。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-195">Get a better understanding of what defines mixed reality and how it’s being used.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3b4a5-196">[![イベントに参加する](images/74-16.png)](../whats-new/sf-academy-events.md)</span><span class="sxs-lookup"><span data-stu-id="3b4a5-196">[![Come to an event](images/74-16.png)](../whats-new/sf-academy-events.md)</span></span><br>
         <span data-ttu-id="3b4a5-197">**[イベントに参加する](../whats-new/sf-academy-events.md)**</span><span class="sxs-lookup"><span data-stu-id="3b4a5-197">**[Come to an event](../whats-new/sf-academy-events.md)**</span></span><br>
        <span data-ttu-id="3b4a5-198">最初の HoloLens 2 アプリケーションを作成するには、ハードウェアを参照し、ハンズオン チュートリアルを入手してください。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-198">See the hardware and get a hands-on tutorial to make your first HoloLens 2 application.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3b4a5-199">[![ツールのインストール](images/74-17.png)](../develop/install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="3b4a5-199">[![Install the tools](images/74-17.png)](../develop/install-the-tools.md)</span></span><br>
         <span data-ttu-id="3b4a5-200">**[ツールのインストール](../develop/install-the-tools.md)**</span><span class="sxs-lookup"><span data-stu-id="3b4a5-200">**[Install the tools](../develop/install-the-tools.md)**</span></span><br>
        <span data-ttu-id="3b4a5-201">インストール チェックリストを使用して、HoloLens や Mixed Reality 用のアプリを構築するのに必要なツールを取得します。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-201">Use the installation checklist to get the tools you need to build apps for HoloLens and mixed reality.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3b4a5-202">[![開発を始める](images/74-18.png)](../develop/development.md)</span><span class="sxs-lookup"><span data-stu-id="3b4a5-202">[![Start developing](images/74-18.png)](../develop/development.md)</span></span><br>
        <span data-ttu-id="3b4a5-203">**[開発を始める](../develop/development.md)**</span><span class="sxs-lookup"><span data-stu-id="3b4a5-203">**[Start developing](../develop/development.md)**</span></span><br>
        <span data-ttu-id="3b4a5-204">スキル レベル、ワーク スタイル、プラットフォームへの関心に基づいて、開発パスを選択します。</span><span class="sxs-lookup"><span data-stu-id="3b4a5-204">Choose a development path based on your skill level, work style, or platform interest.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>
