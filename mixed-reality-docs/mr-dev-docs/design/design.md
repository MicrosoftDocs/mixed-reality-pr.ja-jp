---
title: 設計とプロトタイプ作成を始める
description: 何かを作成する準備ができたら、設計とプロトタイプ作成を開始するために必要な基本的な概念について学習しましょう。
author: grbury
ms.author: grbury
ms.date: 08/24/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 検出, 配布, インデックス, ランディング ページ, 設計, 開発, チュートリアル, サンプル アプリ, 基本事項, ケース スタディ, リソース, HoloLens の使い方, オープン ソース プロジェクト, 主要な概念, 操作
ms.openlocfilehash: 947d9378cd65ceda11cf5dbb1d103a8f9bcc6e63
ms.sourcegitcommit: 8aa3b0034f9f2ff0973d49061c669a82c2c8d7e6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/14/2020
ms.locfileid: "92058586"
---
# <a name="start-designing-and-prototyping"></a><span data-ttu-id="ca382-104">設計とプロトタイプ作成を始める</span><span class="sxs-lookup"><span data-stu-id="ca382-104">Start designing and prototyping</span></span>

![Mixed Reality の設計の概要](images/design-hero-image.png)

<span data-ttu-id="ca382-106">Mixed Reality アプリケーションはまったく新しいものであるため、その設計は困難な作業です。</span><span class="sxs-lookup"><span data-stu-id="ca382-106">Mixed Reality applications are unlike anything else in the world today, and designing them is hard work.</span></span> <span data-ttu-id="ca382-107">作成する仮想世界と現実世界をどのように組み合わせていくかについてだけでなく、それによってどのような種類のユーザー エクスペリエンスを新しく実現するかについても考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca382-107">Not only do you have to account for the new combinations of real and virtual worlds you're creating, but also the new kinds of user experiences they bring to the table.</span></span> <span data-ttu-id="ca382-108">Mixed Reality の領域は広いため、設計範囲に沿って選択した重要なポイントを一連のチェックポイントとして次に示すことにしました。</span><span class="sxs-lookup"><span data-stu-id="ca382-108">Since Mixed Reality is a big place, we've selected important points along its design spectrum and laid them out below as a series of checkpoints.</span></span> <span data-ttu-id="ca382-109">これらは順番に取り組むことを想定していますが、既に十分な知識がある場合は、ご自由に後続の好きなセクションにスキップしてかまいません。</span><span class="sxs-lookup"><span data-stu-id="ca382-109">These are meant to be sequential, but if you've already dipped your feet in feel free to jump to any of the following sections.</span></span>

## <a name="design-checkpoints"></a><span data-ttu-id="ca382-110">設計のチェックポイント</span><span class="sxs-lookup"><span data-stu-id="ca382-110">Design checkpoints</span></span>

<span data-ttu-id="ca382-111">次のチェックポイントを使用して、アプリケーションのアイデアや概念を Mixed Reality の世界に移植することができます。</span><span class="sxs-lookup"><span data-stu-id="ca382-111">Use the following checkpoints to bring your application ideas and concepts into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="ca382-112">1.はじめに</span><span class="sxs-lookup"><span data-stu-id="ca382-112">1. Getting started</span></span>

<span data-ttu-id="ca382-113">あらゆる作業と同様に、Mixed Reality アプリケーションの設計も基礎から始めます。</span><span class="sxs-lookup"><span data-stu-id="ca382-113">Like all journeys, your adventure into designing Mixed Reality applications starts with the basics.</span></span> <span data-ttu-id="ca382-114">イマーシブ デザインに取りかかる前に、「[Mixed Reality とは](../discover/mixed-reality.md)」と「[ホログラムとは](../discover/hologram.md)」の記事を理解しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ca382-114">We recommend familiarizing yourself with the [What is Mixed Reality](../discover/mixed-reality.md) and [What is a hologram?](../discover/hologram.md) articles to get your mind primed for immersive design.</span></span> <span data-ttu-id="ca382-115">読み終えれば、Mixed Reality の設計作業を開始する準備が整っているでしょう。</span><span class="sxs-lookup"><span data-stu-id="ca382-115">Once you've completed your read-through, you'll be ready to start your Mixed Reality design journey!</span></span>

![Designing Holograms アプリの紹介 GIF](images/HandTracking2.gif)

|  <span data-ttu-id="ca382-117">Checkpoint</span><span class="sxs-lookup"><span data-stu-id="ca382-117">Checkpoint</span></span>  |  <span data-ttu-id="ca382-118">結果</span><span class="sxs-lookup"><span data-stu-id="ca382-118">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="ca382-119">デザイン プロセスを展開する</span><span class="sxs-lookup"><span data-stu-id="ca382-119">Expand your design process</span></span>](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | <span data-ttu-id="ca382-120">Microsoft 内外の Mixed Reality 開発者から収集した手法、知見、設計理論を直に確認する</span><span class="sxs-lookup"><span data-stu-id="ca382-120">Get a first-hand look at methods, insights, and design theory gathered from Mixed Reality developers inside and outside of Microsoft</span></span> |
| [<span data-ttu-id="ca382-121">Mixed Reality アプリの種類</span><span class="sxs-lookup"><span data-stu-id="ca382-121">Types of Mixed Reality apps</span></span>](types-of-mixed-reality-apps.md) | <span data-ttu-id="ca382-122">Mixed Reality の範囲のうち、どの領域のアプリ エクスペリエンスを実現するかを決定する</span><span class="sxs-lookup"><span data-stu-id="ca382-122">Decide where your app experience will live on the Mixed Reality spectrum</span></span> |
| [<span data-ttu-id="ca382-123">Designing Holograms アプリ</span><span class="sxs-lookup"><span data-stu-id="ca382-123">Designing Holograms app</span></span>](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | <span data-ttu-id="ca382-124">Mixed Reality の動作、優れた HoloLens アプリを作成するためのヒントや推奨事項について、Mixed Reality UX Design を実際に使用して、その基礎を理解する</span><span class="sxs-lookup"><span data-stu-id="ca382-124">Learn the fundamentals of Mixed Reality UX Design by experiencing it yourself by diving into into Mixed Reality behaviors, tips and recommendations for creating amazing HoloLens apps</span></span> |

### <a name="2-core-concepts"></a><span data-ttu-id="ca382-125">2. 主要な概念</span><span class="sxs-lookup"><span data-stu-id="ca382-125">2. Core concepts</span></span>

<span data-ttu-id="ca382-126">開発対象が VR でも AR でも、柔軟なイマーシブ エクスペリエンスの設計には、いくつかの主要な概念が適用されます。</span><span class="sxs-lookup"><span data-stu-id="ca382-126">Whether you're developing for VR or AR, there are a several core concepts that apply to designing fluid immersive experiences.</span></span> <span data-ttu-id="ca382-127">ユーザーの視点を理解し、オブジェクトを配置し、すべてのユーザーの快適性と安全性を確保することが、お客様の作業のこの段階における最優先事項です。</span><span class="sxs-lookup"><span data-stu-id="ca382-127">Understanding the users point of view, positioning objects, and ensuring everyone is comfortable and safe are your top priorities at this stage of your journey.</span></span> <span data-ttu-id="ca382-128">このセクションが完了する頃には、操作の設計まで全体を通して役に立つ強固な基盤が手に入ります。</span><span class="sxs-lookup"><span data-stu-id="ca382-128">By the end of this section you'll have a solid foundation to carry through into interaction design.</span></span>

![主要な概念の例の画像](images/fragments-750px.jpg)

|  <span data-ttu-id="ca382-130">概念</span><span class="sxs-lookup"><span data-stu-id="ca382-130">Concept</span></span>  |  <span data-ttu-id="ca382-131">結果</span><span class="sxs-lookup"><span data-stu-id="ca382-131">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="ca382-132">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="ca382-132">Holographic frame</span></span>](holographic-frame.md) | <span data-ttu-id="ca382-133">ヘッドセットの装着時、現実世界に重ねて表示されたコンテンツがユーザーにどのように見えるかを理解する</span><span class="sxs-lookup"><span data-stu-id="ca382-133">Understand how users see your content overlaid onto the real world when wearing their headsets</span></span> |
| [<span data-ttu-id="ca382-134">座標系</span><span class="sxs-lookup"><span data-stu-id="ca382-134">Coordinate systems</span></span>](coordinate-systems.md) | <span data-ttu-id="ca382-135">物理的な部屋であれ、自分が作成した仮想領域であれ、ユーザーにとって意味のある空間内の位置にホログラムを配置する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="ca382-135">Learn how to position holograms at places in the world that are meaningful to the user, whether it's their physical room or a virtual realm you've created</span></span> |
| [<span data-ttu-id="ca382-136">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="ca382-136">Spatial mapping</span></span>](spatial-mapping.md) | <span data-ttu-id="ca382-137">オブジェクトをユーザーの世界に固定し、現実世界の奥行きの手がかりを利用する</span><span class="sxs-lookup"><span data-stu-id="ca382-137">Anchor objects in the user's world and take advantage of real world depth cues</span></span> |
| [<span data-ttu-id="ca382-138">快適性に関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="ca382-138">Comfort considerations</span></span>](comfort.md) | <span data-ttu-id="ca382-139">自然世界を模倣した方法でイマーシブ コンテンツの作成と提示を行うことで、ユーザーの快適性と安全性を確保する</span><span class="sxs-lookup"><span data-stu-id="ca382-139">Ensure user comfort and safety by creating and presenting immersive content in a way that mimics the natural world</span></span> |

### <a name="3-interaction-design"></a><span data-ttu-id="ca382-140">3.操作の設計</span><span class="sxs-lookup"><span data-stu-id="ca382-140">3. Interaction design</span></span>

<span data-ttu-id="ca382-141">仮想エクスペリエンスがどれほど美しく臨場感にあふれていても、操作ができなければ役に立ちません。</span><span class="sxs-lookup"><span data-stu-id="ca382-141">No matter how beautiful and immersive a virtual experience is, it's useless without interaction.</span></span> <span data-ttu-id="ca382-142">このセクションでは、基本的な操作モデル、手とモーション コントローラー、音声入力の使用、ユーザーからの視線追跡データの収集について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca382-142">This section will walk you through basic interaction models, hand and motion controllers, using voice input, and gathering eye tracking data from your users.</span></span> <span data-ttu-id="ca382-143">このセクションが完了する頃には、設計作業における最後の大きなトピックであるユーザー エクスペリエンスに取り組む準備が整います。</span><span class="sxs-lookup"><span data-stu-id="ca382-143">By the end of this section you'll be ready to tackle the last big topic on your design journey: user experience.</span></span>

![操作の設計の要素](images/UX_Hero_Manipulation.jpg)

|  <span data-ttu-id="ca382-145">概念</span><span class="sxs-lookup"><span data-stu-id="ca382-145">Concept</span></span>  |  <span data-ttu-id="ca382-146">結果</span><span class="sxs-lookup"><span data-stu-id="ca382-146">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="ca382-147">相互作用モデル</span><span class="sxs-lookup"><span data-stu-id="ca382-147">Interaction models</span></span>](interaction-fundamentals.md) | <span data-ttu-id="ca382-148">手、視線、音声による入力を使用した直感的な操作をユーザーに提供する</span><span class="sxs-lookup"><span data-stu-id="ca382-148">Provide your users with instinctual interactions through hand, eye, and voice input</span></span> |
| [<span data-ttu-id="ca382-149">手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="ca382-149">Hands and motion controllers</span></span>](hands-and-tools.md) | <span data-ttu-id="ca382-150">ユーザーの手で近くのホログラムに触れて操作を行う方法と、遠くから正確に操作を行う方法について学習する</span><span class="sxs-lookup"><span data-stu-id="ca382-150">Learn how holograms can be touched and manipulated at close range with a users' hands or at long range with precise interactions</span></span> |
| [<span data-ttu-id="ca382-151">音声入力</span><span class="sxs-lookup"><span data-stu-id="ca382-151">Voice input</span></span>](voice-input.md) | <span data-ttu-id="ca382-152">音声コマンドをイマーシブ アプリの入力として使用して、周囲のホログラムと環境をコントロールする</span><span class="sxs-lookup"><span data-stu-id="ca382-152">Use voice commands as input in your immersive apps to control surrounding holograms and environments</span></span>  |
| [<span data-ttu-id="ca382-153">視線追跡</span><span class="sxs-lookup"><span data-stu-id="ca382-153">Eye Tracking</span></span>](eye-tracking.md) | <span data-ttu-id="ca382-154">ユーザーが見ているものに関する情報を使用して、ホログラフィック エクスペリエンスに新しいレベルのコンテキストを追加し、人間による理解を深める</span><span class="sxs-lookup"><span data-stu-id="ca382-154">Add a new level of context and human understanding in a holographic experience by using information about what your users are looking at</span></span> |

### <a name="4-user-experience-elements"></a><span data-ttu-id="ca382-155">4.ユーザー エクスペリエンス要素</span><span class="sxs-lookup"><span data-stu-id="ca382-155">4. User experience elements</span></span>

<span data-ttu-id="ca382-156">基本的な操作を習得したので、ここからはユーザー エクスペリエンス要素のより詳細なポイントに注目して、それらを Mixed Reality 特有の環境に適合させていくことができます。</span><span class="sxs-lookup"><span data-stu-id="ca382-156">Now that you've mastered basic interactions, you can focus on the finer points of user experience elements and how to adapt them for Mixed Reality's unique environments.</span></span> <span data-ttu-id="ca382-157">可能な限りアプリをユーザーにとって直感的に操作できるものにすることを念頭に置いて、一般的な動作、資産の設計、オブジェクトのスケーリング、タイポグラフィについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ca382-157">You'll cover common behaviors, asset design, object scaling, and typography, all with an eye on making your apps as intuitive for users as possible.</span></span> <span data-ttu-id="ca382-158">このセクションで Mixed Reality の正式な設計作業は終了します。さらに理解を深めたい場合は、「[次の操作](#whats-next)」セクションにある、その他のリソースをご利用ください。</span><span class="sxs-lookup"><span data-stu-id="ca382-158">This section marks the end of the official Mixed Reality design journey, but there are more resources in the [What's next?](#whats-next) section to keep you going.</span></span>

![UX 要素](images/UX_Hero_BoundingBox.jpg)

|  <span data-ttu-id="ca382-160">概念</span><span class="sxs-lookup"><span data-stu-id="ca382-160">Concept</span></span>  |  <span data-ttu-id="ca382-161">結果</span><span class="sxs-lookup"><span data-stu-id="ca382-161">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="ca382-162">一般的なコントロールと動作</span><span class="sxs-lookup"><span data-stu-id="ca382-162">Common controls and behaviors</span></span>](app-patterns-landingpage.md) | <span data-ttu-id="ca382-163">頻繁に使用される空間操作と UI 構成要素について学習する</span><span class="sxs-lookup"><span data-stu-id="ca382-163">Learn about frequently used spatial interactions and UI building blocks</span></span> |
| [<span data-ttu-id="ca382-164">色、ライト、マテリアル</span><span class="sxs-lookup"><span data-stu-id="ca382-164">Color, light and materials</span></span>](color-light-and-materials.md) | <span data-ttu-id="ca382-165">色、照明、素材を考慮して、Mixed Reality 用の高品質な資産を設計する</span><span class="sxs-lookup"><span data-stu-id="ca382-165">Design quality assets for Mixed Reality that take color, lighting, and materials into account</span></span> |
| [<span data-ttu-id="ca382-166">オブジェクトのスケーリング</span><span class="sxs-lookup"><span data-stu-id="ca382-166">Object scale</span></span>](scale.md) | <span data-ttu-id="ca382-167">オブジェクトの場所、大きさ、材料をユーザーが理解しやすいように、現実世界の視覚的な手がかりを可能な限り組み込む</span><span class="sxs-lookup"><span data-stu-id="ca382-167">Incorporate as many real-world visual cues as possible to us help your users understand where objects are, how big they are, and what they’re made of</span></span> |
| [<span data-ttu-id="ca382-168">文字体裁</span><span class="sxs-lookup"><span data-stu-id="ca382-168">Typography</span></span>](typography.md) | <span data-ttu-id="ca382-169">はっきりと見える読みやすいテキストを 3 次元空間で使用して、ユーザーが必要とする重要な情報を提供する</span><span class="sxs-lookup"><span data-stu-id="ca382-169">Use clear, readable text in three-dimensional space to give your users the important information they need</span></span> |

## <a name="whats-next"></a><span data-ttu-id="ca382-170">次の操作</span><span class="sxs-lookup"><span data-stu-id="ca382-170">What's next?</span></span>

<span data-ttu-id="ca382-171">設計者の仕事に終わりはありません。新しいパラダイムでイマーシブ エクスペリエンスを作成する場合はなおさらです。</span><span class="sxs-lookup"><span data-stu-id="ca382-171">A designers job is never done, especially when learning to create immersive experiences in a new paradigm.</span></span> <span data-ttu-id="ca382-172">次のセクションでは、ここまでで説明しなかった中級以上の設計資料と、Mixed Reality の開発環境についてご紹介します。</span><span class="sxs-lookup"><span data-stu-id="ca382-172">The following sections will take you beyond the beginner level design material you've already completed and into the world of Mixed Reality development.</span></span> <span data-ttu-id="ca382-173">これらのトピックとリソースに決まった順序はないので、お好きなものをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ca382-173">These topics and resources aren't in any sequential order, so feel free to explore!</span></span>

### <a name="choose-a-prototyping-option"></a><span data-ttu-id="ca382-174">プロトタイプ作成のオプションを選択する</span><span class="sxs-lookup"><span data-stu-id="ca382-174">Choose a prototyping option</span></span>  

:::row:::   
    :::column:::    
       <span data-ttu-id="ca382-175">[![Unity について学習する](images/logo-unity.png)](https://learn.unity.com/)</span><span class="sxs-lookup"><span data-stu-id="ca382-175">[![Learn Unity](images/logo-unity.png)](https://learn.unity.com/)</span></span><br>
        <span data-ttu-id="ca382-176">**[Unity について学習する](https://learn.unity.com/)**</span><span class="sxs-lookup"><span data-stu-id="ca382-176">**[Learn Unity](https://learn.unity.com/)**</span></span><br>
        <span data-ttu-id="ca382-177">Unity で対話型エクスペリエンスを作成する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="ca382-177">Learn how to create interactive experiences with Unity.</span></span> <span data-ttu-id="ca382-178">最初から最後まで、実践によって学習できます。</span><span class="sxs-lookup"><span data-stu-id="ca382-178">Learn by doing, from start to finish.</span></span>
    :::column-end:::    
    :::column:::    
        <span data-ttu-id="ca382-179">[![Mixed Reality ツールキット (MRTK)](images/Final_mrtk-small_logo.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span><span class="sxs-lookup"><span data-stu-id="ca382-179">[![Mixed Reality Toolkit (MRTK)](images/Final_mrtk-small_logo.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)</span></span><br>
        <span data-ttu-id="ca382-180">**[Mixed Reality ツールキット (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**</span><span class="sxs-lookup"><span data-stu-id="ca382-180">**[Mixed Reality Toolkit (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**</span></span><br>  
        <span data-ttu-id="ca382-181">空間操作と UI 構成ブロックを使用すると、Unity での Mixed Reality の設計と開発をすぐに始めることができます。</span><span class="sxs-lookup"><span data-stu-id="ca382-181">With spatial interaction and UI building blocks, jump-start your mixed reality design and development with Unity.</span></span>   
    :::column-end:::
    :::column:::    
        <span data-ttu-id="ca382-182">[![Mixed Reality Design Labs](images/Final_mrdl_logo.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)</span><span class="sxs-lookup"><span data-stu-id="ca382-182">[![Mixed Reality Design Labs](images/Final_mrdl_logo.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)</span></span><br>
        <span data-ttu-id="ca382-183">**[Mixed Reality Design Labs](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**</span><span class="sxs-lookup"><span data-stu-id="ca382-183">**[Mixed Reality Design Labs](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**</span></span><br>  
        <span data-ttu-id="ca382-184">MRTK の構成要素を使用して美しい Mixed Reality エクスペリエンスを作成する方法を示すサンプル アプリを入手できます。</span><span class="sxs-lookup"><span data-stu-id="ca382-184">Get sample apps that show you how to use MRTK's building blocks to create beautiful mixed reality experiences.</span></span>
    :::column-end:::        
    :::column:::    
        <span data-ttu-id="ca382-185">[![Microsoft Maquette](images/Final_maquette_logo.png)](https://www.maquette.ms/)</span><span class="sxs-lookup"><span data-stu-id="ca382-185">[![Microsoft Maquette](images/Final_maquette_logo.png)](https://www.maquette.ms/)</span></span><br>
        <span data-ttu-id="ca382-186">**[Microsoft Maquette](https://www.maquette.ms/)**</span><span class="sxs-lookup"><span data-stu-id="ca382-186">**[Microsoft Maquette](https://www.maquette.ms/)**</span></span><br>  
        <span data-ttu-id="ca382-187">VR 向けの設計。</span><span class="sxs-lookup"><span data-stu-id="ca382-187">Design for VR.</span></span> <span data-ttu-id="ca382-188">Microsoft Maquette を使用すると、空間のプロトタイプ作成をすばやく、簡単、かつイマーシブに実行できます。</span><span class="sxs-lookup"><span data-stu-id="ca382-188">Microsoft Maquette makes spatial prototyping easy, quick, and immersive.</span></span> 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="additional-resources"></a><span data-ttu-id="ca382-189">その他の技術情報</span><span class="sxs-lookup"><span data-stu-id="ca382-189">Additional resources</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="ca382-190">[![基本を理解する](images/icon-lightbulb.png)](../discover/get-started-with-mr.md#understand-the-basics)</span><span class="sxs-lookup"><span data-stu-id="ca382-190">[![Understand the basics](images/icon-lightbulb.png)](../discover/get-started-with-mr.md#understand-the-basics)</span></span><br>
        <span data-ttu-id="ca382-191">**[基本を理解する](../discover/get-started-with-mr.md#understand-the-basics)**</span><span class="sxs-lookup"><span data-stu-id="ca382-191">**[Understand the basics](../discover/get-started-with-mr.md#understand-the-basics)**</span></span><br>
        <span data-ttu-id="ca382-192">Mixed Reality が何によって定義され、どのように使用されているかについて理解を深めます。</span><span class="sxs-lookup"><span data-stu-id="ca382-192">Get a better understanding of what defines mixed reality and how it’s being used.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ca382-193">[![イベントに参加する](images/icon-calendar.jpg)](../whats-new/sf-academy-events.md)</span><span class="sxs-lookup"><span data-stu-id="ca382-193">[![Come to an event](images/icon-calendar.jpg)](../whats-new/sf-academy-events.md)</span></span><br>
         <span data-ttu-id="ca382-194">**[イベントに参加する](../whats-new/sf-academy-events.md)**</span><span class="sxs-lookup"><span data-stu-id="ca382-194">**[Come to an event](../whats-new/sf-academy-events.md)**</span></span><br>
        <span data-ttu-id="ca382-195">最初の HoloLens 2 アプリケーションを作成するには、ハードウェアを参照し、ハンズオン チュートリアルを入手してください。</span><span class="sxs-lookup"><span data-stu-id="ca382-195">See the hardware and get a hands-on tutorial to make your first HoloLens 2 application.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ca382-196">[![ツールのインストール](images/icon-design.png)](../develop/install-the-tools.md)</span><span class="sxs-lookup"><span data-stu-id="ca382-196">[![Install the tools](images/icon-design.png)](../develop/install-the-tools.md)</span></span><br>
         <span data-ttu-id="ca382-197">**[ツールのインストール](../develop/install-the-tools.md)**</span><span class="sxs-lookup"><span data-stu-id="ca382-197">**[Install the tools](../develop/install-the-tools.md)**</span></span><br>
        <span data-ttu-id="ca382-198">インストール チェックリストを使用して、HoloLens や Mixed Reality 用のアプリを構築するのに必要なツールを取得します。</span><span class="sxs-lookup"><span data-stu-id="ca382-198">Use the installation checklist to get the tools you need to build apps for HoloLens and mixed reality.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="ca382-199">[![開発を始める](images/icon-developer.png)](../develop/development.md)</span><span class="sxs-lookup"><span data-stu-id="ca382-199">[![Start developing](images/icon-developer.png)](../develop/development.md)</span></span><br>
        <span data-ttu-id="ca382-200">**[開発を始める](../develop/development.md)**</span><span class="sxs-lookup"><span data-stu-id="ca382-200">**[Start developing](../develop/development.md)**</span></span><br>
        <span data-ttu-id="ca382-201">スキル レベル、ワーク スタイル、プラットフォームへの関心に基づいて、開発パスを選択します。</span><span class="sxs-lookup"><span data-stu-id="ca382-201">Choose a development path based on your skill level, work style, or platform interest.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>