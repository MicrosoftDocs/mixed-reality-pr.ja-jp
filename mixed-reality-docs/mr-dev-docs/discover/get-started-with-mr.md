---
title: Mixed Reality の概要
description: Mixed Reality を初めて使用するユーザーにその概要と機能について説明します。
author: grbury
ms.author: grbury
ms.date: 07/29/2020
ms.topic: overview
ms.localizationpriority: high
keywords: Mixed Reality, 検出, 配布, インデックス, ランディング ページ, 設計, 開発, チュートリアル, サンプル アプリ, 基本事項, ケース スタディ, リソース, HoloLens の使い方, オープン ソース プロジェクト
ms.openlocfilehash: 7c8fc83fd2b5542909fd2ea6ab4dca288175c56c
ms.sourcegitcommit: cc27d31f0cebaf9fc4221a3300a9e3d73230b367
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2020
ms.locfileid: "94631520"
---
# <a name="get-started-with-mixed-reality"></a><span data-ttu-id="72831-104">Mixed Reality の概要</span><span class="sxs-lookup"><span data-stu-id="72831-104">Get started with Mixed Reality</span></span>

![仮想ハチドリと人の手](images/01_MixedReality.png)

<span data-ttu-id="72831-106">Mixed Reality エコシステムは、物理とデジタルの相互作用の新しい世界であり、人の想像力以外にそれを制限するものはありません。</span><span class="sxs-lookup"><span data-stu-id="72831-106">The Mixed Reality ecosystem is an emerging landscape of physical and digital interactions, limited only by your imagination.</span></span> <span data-ttu-id="72831-107">経験豊富な開発者でも、新しく転向した場合でも、以下のリンクで示されているリソースで Mixed Reality の旅を始めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="72831-107">Whether you're an experienced developer or a new convert, we recommend beginning your Mixed Reality journey with the resources we've laid out in the links below.</span></span> <span data-ttu-id="72831-108">新しく知らなければならないことがたくさんあるので、さっそく始めましょう。</span><span class="sxs-lookup"><span data-stu-id="72831-108">There's a lot of new ground to cover, so let's get started!</span></span> 

## <a name="choose-your-track"></a><span data-ttu-id="72831-109">トラックを選択する</span><span class="sxs-lookup"><span data-stu-id="72831-109">Choose your track</span></span>

<span data-ttu-id="72831-110">Mixed Reality で調べたい分野が既にわかっている場合は、次のいずれかのトラックにすぐにジャンプできます。</span><span class="sxs-lookup"><span data-stu-id="72831-110">If you already know which area of Mixed Reality you'd like to explore, feel free to jump right in to any of the tracks below.</span></span> <span data-ttu-id="72831-111">ただし、後で基本概念のコンテンツを参照できるように、このページをブックマークに残しておいてください。</span><span class="sxs-lookup"><span data-stu-id="72831-111">However, keep this page in your bookmarks so you can reference the basic conceptual content at a later time.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="72831-112">[![Mixed Reality を初めて使う](images/Tile-New.jpg)](#understand-the-basics)</span><span class="sxs-lookup"><span data-stu-id="72831-112">[![I'm new to mixed reality](images/Tile-New.jpg)](#understand-the-basics)</span></span><br>
        <span data-ttu-id="72831-113">**[Mixed Reality を初めて使う](#understand-the-basics)**</span><span class="sxs-lookup"><span data-stu-id="72831-113">**[I'm new to mixed reality](#understand-the-basics)**</span></span><br>
        <span data-ttu-id="72831-114">基本を理解する</span><span class="sxs-lookup"><span data-stu-id="72831-114">Understand the basics</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72831-115">[![デザイナーである](images/Tile-Create.jpg)](../design/design.md)</span><span class="sxs-lookup"><span data-stu-id="72831-115">[![I'm a designer](images/Tile-Create.jpg)](../design/design.md)</span></span><br>
        <span data-ttu-id="72831-116">**[デザイナーである](../design/design.md)**</span><span class="sxs-lookup"><span data-stu-id="72831-116">**[I'm a designer](../design/design.md)**</span></span><br>
        <span data-ttu-id="72831-117">設計とプロトタイプ作成を始める</span><span class="sxs-lookup"><span data-stu-id="72831-117">Start designing and prototyping</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="72831-118">[![開発者である](images/Tile-Develop.jpg)](../develop/development.md)</span><span class="sxs-lookup"><span data-stu-id="72831-118">[![I'm a developer](images/Tile-Develop.jpg)](../develop/development.md)</span></span><br>
        <span data-ttu-id="72831-119">**[開発者である](../develop/development.md)**</span><span class="sxs-lookup"><span data-stu-id="72831-119">**[I'm a developer](../develop/development.md)**</span></span><br>
        <span data-ttu-id="72831-120">ツールとアーキテクチャについて学習する</span><span class="sxs-lookup"><span data-stu-id="72831-120">Learn the tools and architecture</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="understand-the-basics"></a><span data-ttu-id="72831-121">基本を理解する</span><span class="sxs-lookup"><span data-stu-id="72831-121">Understand the basics</span></span>

<span data-ttu-id="72831-122">Mixed Reality を初めて使用する場合は、最下層から初めて、中核概念、エクスペリエンス、機能へと上に向かって理解していくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="72831-122">If you're new to mixed reality, it's important that you start from the bottom and work your way up through its core concepts, experiences, and capabilities.</span></span> <span data-ttu-id="72831-123">Mixed Reality で独自のアイデアを設計および開発するための確かな基盤を設けるのに役立つよう、一連の順序がある程度作成されています。</span><span class="sxs-lookup"><span data-stu-id="72831-123">We've created a sequential journey of sorts to help you set a firm foundation for designing and developing your own ideas in Mixed Reality.</span></span>

### <a name="what-is-mixed-reality"></a><span data-ttu-id="72831-124">Mixed Reality とは</span><span class="sxs-lookup"><span data-stu-id="72831-124">What is mixed reality?</span></span>

![Mixed Reality でできること](images/HLS19_remoteAssistHologram_001.jpg)

<span data-ttu-id="72831-126">アプリケーションの設計または開発を始める前に、Mixed Reality がどのような意味で使用されているのかを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="72831-126">Before you dive into application design or development, you need to understand what we mean by Mixed Reality.</span></span> <span data-ttu-id="72831-127">このセクションは、環境入力の範囲、知覚上の変化、設計上の課題、付属するデバイスなど、Mixed Reality の範囲を理解できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="72831-127">This section is designed to get you acquainted with the Mixed Reality spectrum, including the range of environmental input, perceptual changes, design challenges, and devices that come with it.</span></span> 

|  <span data-ttu-id="72831-128">概念</span><span class="sxs-lookup"><span data-stu-id="72831-128">Concept</span></span>  |  <span data-ttu-id="72831-129">結果</span><span class="sxs-lookup"><span data-stu-id="72831-129">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="72831-130">さまざまな Mixed Reality がある</span><span class="sxs-lookup"><span data-stu-id="72831-130">Mixed reality is a spectrum</span></span>](../discover/mixed-reality.md) | <span data-ttu-id="72831-131">Mixed Reality は物理とデジタルを融合するものであり、人間、コンピューター、環境の次世代の相互作用を実現します</span><span class="sxs-lookup"><span data-stu-id="72831-131">Mixed reality blends the physical with the digital, the next evolution in human, computer, and environment interactions</span></span> |
| [<span data-ttu-id="72831-132">ホログラムとは</span><span class="sxs-lookup"><span data-stu-id="72831-132">What is a hologram?</span></span>](../discover/hologram.md) | <span data-ttu-id="72831-133">HoloLens を使用すると、ホログラムつまり自分の周囲に表示される光と音で構成されたオブジェクトを、実際のオブジェクトであるかのように作成できます。</span><span class="sxs-lookup"><span data-stu-id="72831-133">HoloLens lets you create holograms, which are objects made of light and sound that appear in the world around you, just as if they were real objects.</span></span> <span data-ttu-id="72831-134">ホログラムは、視線入力、ジェスチャ、音声コマンドに応答し、周囲の現実世界のサーフェスと対話できます</span><span class="sxs-lookup"><span data-stu-id="72831-134">Holograms respond to your gaze, gestures and voice commands, and can interact with real-world surfaces around you</span></span> |
| [<span data-ttu-id="72831-135">デザイン プロセスを展開する</span><span class="sxs-lookup"><span data-stu-id="72831-135">Expand your design process</span></span>](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | <span data-ttu-id="72831-136">イマーシブ エクスペリエンスを作成するときに空間的思考、ボディストーミング、行動により設計上の考え方を拡張します</span><span class="sxs-lookup"><span data-stu-id="72831-136">Expand your design mindset with spatial thinking, bodystorming, and acting when creating your immersive experiences</span></span>  |

<br>

---

## <a name="see-how-industry-partners-are-using-mixed-reality"></a><span data-ttu-id="72831-137">業界のパートナーが Mixed Reality をどのように使用しているかを確認する</span><span class="sxs-lookup"><span data-stu-id="72831-137">See how industry partners are using mixed reality</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="72831-138">[![Bentley](images/Bentley-Synchro1.jpg)](https://binged.it/31AR3kP)</span><span class="sxs-lookup"><span data-stu-id="72831-138">[![Bentley](images/Bentley-Synchro1.jpg)](https://binged.it/31AR3kP)</span></span>
    :::column-end:::
    :::column span="2":::
        ### <a name="view-complex-construction-projects-with-bentleys-digital-construction-software"></a>[<span data-ttu-id="72831-139">Bentley のデジタル建設ソフトウェアで複雑な建設プロジェクトを表示する</span><span class="sxs-lookup"><span data-stu-id="72831-139">View complex construction projects with Bentley's digital construction software</span></span>](https://binged.it/31AR3kP)
        <span data-ttu-id="72831-140">Synchro は、複雑な建設プロジェクトを Mixed Reality で表示できるようにする Bentley のデジタル建設ソフトウェアです。</span><span class="sxs-lookup"><span data-stu-id="72831-140">Synchro is digital construction software that enables viewing complex construction projects in mixed reality.</span></span> <span data-ttu-id="72831-141">これらの 4D デジタル建設プラットフォームは、従来のガント チャート CPM スケジュールと、統合されたリアルタイムの 4D 視覚化機能を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="72831-141">Their 4D digital construction platform combines traditional Gantt chart CPM scheduling with integrated 4D visualization capabilities in real time.</span></span>
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       <span data-ttu-id="72831-142">[![PTC の Vuforia Studio](images/PTC-Vuforia-Studio1.jpg)](https://binged.it/31ARrjh)</span><span class="sxs-lookup"><span data-stu-id="72831-142">[![PTC's Vuforia Studio](images/PTC-Vuforia-Studio1.jpg)](https://binged.it/31ARrjh)</span></span>
    :::column-end:::
    :::column span="2":::
        ### <a name="ptcs-vuforia-studio-authoring-solution-promotes-workforce-productivity-and-safety"></a>[<span data-ttu-id="72831-143">PTC の Vuforia Studio 作成ソリューションで従業員の生産性と安全性を促進する</span><span class="sxs-lookup"><span data-stu-id="72831-143">PTC's Vuforia Studio authoring solution promotes workforce productivity and safety</span></span>](https://binged.it/31ARrjh)
        <span data-ttu-id="72831-144">Vuforia Studio の効率的な Mixed Reality 作成ソリューションは、従業員が最も頻繁に必要とする情報を提供することによって、従業員の生産性と安全性を促進します。これは、日常業務環境の実際のコンテキストで使用されます。</span><span class="sxs-lookup"><span data-stu-id="72831-144">Vuforia Studio's efficient mixed reality authoring solution promotes workforce productivity and safety by delivering information when and where workers need it most: in the real-world context of their daily work environment.</span></span>
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       <span data-ttu-id="72831-145">[![Philips-Azurion](images/Philips-Azurion1.jpg)](https://binged.it/31B1RiR)</span><span class="sxs-lookup"><span data-stu-id="72831-145">[![Philips-Azurion](images/Philips-Azurion1.jpg)](https://binged.it/31B1RiR)</span></span>
    :::column-end:::
    :::column span="2":::
        ### <a name="philips-is-piloting-hololens-in-the-domain-of-image-guided-minimally-invasive-procedures"></a>[<span data-ttu-id="72831-146">Philips は画像誘導低侵襲的処置の分野で HoloLens をいち早く導入しています</span><span class="sxs-lookup"><span data-stu-id="72831-146">Philips is piloting HoloLens in the domain of image-guided minimally invasive procedures</span></span>](https://binged.it/31B1RiR)
        <span data-ttu-id="72831-147">Philips は画像誘導低侵襲的処置の分野で HoloLens をいち早く導入しています。医師はライブ X 線、超音波、その他の情報源を利用して、患者の体内を "見る" ことにより、処置に役立てています。</span><span class="sxs-lookup"><span data-stu-id="72831-147">Philips is piloting HoloLens in the domain of image-guided minimally invasive procedures, during which physicians rely on live X-ray, ultrasound and other sources of information to "see" inside the patient and guide their actions.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="explore-hololens-and-mixed-reality-services"></a><span data-ttu-id="72831-148">HoloLens と Mixed Reality サービスを調べる</span><span class="sxs-lookup"><span data-stu-id="72831-148">Explore HoloLens and Mixed Reality services</span></span>

![HoloLens の分解図](images/HoloLens2_ExplodedView_8k.png)

<span data-ttu-id="72831-150">さまざまな Mixed Reality ハードウェアとサービスがどのように動作するかを知りたい場合は、以下のリンクを確認してください。</span><span class="sxs-lookup"><span data-stu-id="72831-150">If you're curious to see how the different Mixed Reality hardware and services work, check out the links below.</span></span> <span data-ttu-id="72831-151">これらのリンクからは Microsoft のドキュメントのさまざまな部分に移動しますが、設計と開発の旅を続けられるよう、ここにブックマークを設定して戻ってくることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="72831-151">These links will navigate you to different parts of the Microsoft documentation, but we recommend bookmarking and returning here to continue on your design and development journey.</span></span>

|  <span data-ttu-id="72831-152">概念</span><span class="sxs-lookup"><span data-stu-id="72831-152">Concept</span></span>  |  <span data-ttu-id="72831-153">結果</span><span class="sxs-lookup"><span data-stu-id="72831-153">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="72831-154">HoloLens ハードウェア</span><span class="sxs-lookup"><span data-stu-id="72831-154">HoloLens hardware</span></span>](https://www.microsoft.com//hololens/hardware) | <span data-ttu-id="72831-155">HoloLens 2 は、数分で価値を提供できる業界最先端のソリューションにより、最も快適でイマーシブな複合現実エクスペリエンスを提供します。これらはすべて、Microsoft のクラウドおよび AI サービスの信頼性、セキュリティ、および拡張性によって強化されています</span><span class="sxs-lookup"><span data-stu-id="72831-155">HoloLens 2 offers the most comfortable and immersive mixed reality experience available, with industry-leading solutions that deliver value in minutes—all enhanced by the reliability, security, and scalability of cloud and AI services from Microsoft</span></span> |
| [<span data-ttu-id="72831-156">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="72831-156">Dynamics 365</span></span>](https://dynamics.microsoft.com/mixed-reality/overview/) | <span data-ttu-id="72831-157">[リモート アシスト](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/ra-overview)、[レイアウト](https://docs.microsoft.com/dynamics365/mixed-reality/layout/)、[ガイド](https://docs.microsoft.com/dynamics365/mixed-reality/guides/)など、従業員を支援し、Dynamics 365 での操作を最適化できる、さまざまな製品を調べます。</span><span class="sxs-lookup"><span data-stu-id="72831-157">Explore a range of products that can empower employees and optimize operations with Dynamics 365, including [Remote Assist](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/ra-overview), [Layout](https://docs.microsoft.com/dynamics365/mixed-reality/layout/) and [Guides](https://docs.microsoft.com/dynamics365/mixed-reality/guides/).</span></span> <span data-ttu-id="72831-158">実際の仕事、実際のデバイス、実際のユーザーの実体験から、実践的な分析情報が得られます</span><span class="sxs-lookup"><span data-stu-id="72831-158">Meaningful insight comes from getting hands-on with real work, real devices, and real users</span></span> |
| [<span data-ttu-id="72831-159">Azure Cloud Services</span><span class="sxs-lookup"><span data-stu-id="72831-159">Azure Cloud Services</span></span>](../develop/mixed-reality-cloud-services.md) | <span data-ttu-id="72831-160">空間認識、空間アンカー、複雑な 3D モデル レンダリングを追加することにより、さまざまなプラットフォームで魅力的なイマーシブ エクスペリエンスを構築します</span><span class="sxs-lookup"><span data-stu-id="72831-160">Build compelling immersive experiences on a variety of platforms by adding spatial awareness, spatial anchors, and complex 3D model rendering</span></span> |

## <a name="what-would-you-like-to-do-next"></a><span data-ttu-id="72831-161">次に行うこと</span><span class="sxs-lookup"><span data-stu-id="72831-161">What would you like to do next?</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="72831-162">[![作成者になる](images/icon-design.png)](../design/design.md)</span><span class="sxs-lookup"><span data-stu-id="72831-162">[![Become a creator](images/icon-design.png)](../design/design.md)</span></span><br>
        <span data-ttu-id="72831-163">**[作成者になる](../design/design.md)**</span><span class="sxs-lookup"><span data-stu-id="72831-163">**[Become a creator](../design/design.md)**</span></span><br>
        <span data-ttu-id="72831-164">設計とプロトタイプ作成を開始するために必要な基本的な概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="72831-164">Learn the basic concepts you need to begin designing and prototyping.</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="72831-165">[![開発を始める](images/icon-developer.png)](../develop/development.md)</span><span class="sxs-lookup"><span data-stu-id="72831-165">[![Start developing](images/icon-developer.png)](../develop/development.md)</span></span><br>
        <span data-ttu-id="72831-166">**[開発を始める](../develop/development.md)**</span><span class="sxs-lookup"><span data-stu-id="72831-166">**[Start developing](../develop/development.md)**</span></span><br>
        <span data-ttu-id="72831-167">スキル レベル、ワーク スタイル、プラットフォームへの関心に基づいて、開発パスを選択します。</span><span class="sxs-lookup"><span data-stu-id="72831-167">Choose a development path based on your skill level, work style or platform interest.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="72831-168">[![イベントに参加する](images/icon-calendar.jpg)](../whats-new/sf-academy-events.md)</span><span class="sxs-lookup"><span data-stu-id="72831-168">[![Come to an event](images/icon-calendar.jpg)](../whats-new/sf-academy-events.md)</span></span><br>
        <span data-ttu-id="72831-169">**[イベントに参加する](../whats-new/sf-academy-events.md)**</span><span class="sxs-lookup"><span data-stu-id="72831-169">**[Come to an event](../whats-new/sf-academy-events.md)**</span></span><br>
        <span data-ttu-id="72831-170">最初の HoloLens 2 アプリケーションを作成するには、ハードウェアを参照し、ハンズオン チュートリアルを入手してください。</span><span class="sxs-lookup"><span data-stu-id="72831-170">See the hardware and get a hands-on tutorial to make your first HoloLens 2 application.</span></span>
    :::column-end:::
:::row-end:::


<br>

<br>

>[!IMPORTANT]
><span data-ttu-id="72831-171">このサイトで提供されるすべての複合現実の開発に関する資料は参照のみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="72831-171">All mixed reality development materials are provided on this site for your reference only.</span></span> <span data-ttu-id="72831-172">アプリケーションとその使用法およびエンド ユーザーに与える影響は、アプリケーション開発者としてお客様に責任があるものとし、これには、アプリがエンド ユーザーに対して不快感、傷害、またはその他の害をもたらしたりするものではないことや適切な警告文および免責文を含むことが含まれます。</span><span class="sxs-lookup"><span data-stu-id="72831-172">Your application, its usage, and its effect on end users is your sole responsibility as the application developer, including ensuring that your app does not cause discomfort, injury, or any other harm to the end user, and including appropriate warnings and disclaimers.</span></span> <span data-ttu-id="72831-173">お客様は、自分のアプリケーションが安全であり、「[Microsoft とのアプリ開発者契約](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement)」のすべての責務を満たしていることを保証するために、アプリケーションの開発と発行において常に適切な手順を踏む必要があります。</span><span class="sxs-lookup"><span data-stu-id="72831-173">You need to at all times take the appropriate steps in the development and publishing of your application to ensure that your application is safe, and that you meet all obligations in your [App Developer Agreement with Microsoft](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement).</span></span>

