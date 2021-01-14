---
title: Mixed Reality の概要
description: 開発トラックを選択し、Mixed Reality の理論、開発、一般的なユース ケースの基本について学習します。
author: grbury
ms.author: grbury
ms.date: 12/9/2020
ms.topic: overview
ms.localizationpriority: high
keywords: Mixed Reality, 検出, 配布, インデックス, ランディング ページ, 設計, 開発, チュートリアル, サンプル アプリ, 基本事項, ケース スタディ, リソース, HoloLens の使い方, オープン ソース プロジェクト, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 03db5f79a531d77bfd1cd6513c5bed9ad1202189
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009722"
---
# <a name="get-started-with-mixed-reality"></a><span data-ttu-id="5955d-104">Mixed Reality の概要</span><span class="sxs-lookup"><span data-stu-id="5955d-104">Get started with Mixed Reality</span></span>

![仮想ハチドリと人の手](images/01_MixedReality.png)

<span data-ttu-id="5955d-106">Mixed Reality エコシステムは、物理とデジタルの相互作用の新しい世界であり、人の想像力以外にそれを制限するものはありません。</span><span class="sxs-lookup"><span data-stu-id="5955d-106">The Mixed Reality ecosystem is an emerging landscape of physical and digital interactions, limited only by your imagination.</span></span> <span data-ttu-id="5955d-107">経験豊富な開発者でも、新しく転向した場合でも、以下に詳述するリソースで Mixed Reality の体験を始めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5955d-107">Whether you're an experienced developer or a new convert, we recommend beginning your Mixed Reality journey with the resources we've laid out below.</span></span> <span data-ttu-id="5955d-108">新しく知らなければならないことがたくさんあるので、さっそく始めましょう。</span><span class="sxs-lookup"><span data-stu-id="5955d-108">There's a lot of new ground to cover, so let's get started!</span></span> 

## <a name="choose-your-track"></a><span data-ttu-id="5955d-109">トラックを選択する</span><span class="sxs-lookup"><span data-stu-id="5955d-109">Choose your track</span></span>

<span data-ttu-id="5955d-110">Mixed Reality で調べたい分野が既にわかっている場合は、次のいずれかのトラックにすぐにジャンプできます。</span><span class="sxs-lookup"><span data-stu-id="5955d-110">If you already know which area of Mixed Reality you'd like to explore, feel free to jump right in to any of the tracks below.</span></span> <span data-ttu-id="5955d-111">ただし、後で基本概念のコンテンツを参照できるように、このページをブックマークに残しておいてください。</span><span class="sxs-lookup"><span data-stu-id="5955d-111">However, keep this page in your bookmarks so you can reference the basic conceptual content at a later time.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="5955d-112">[![Mixed Reality を初めて使う](images/Tile-New.jpg)](#understand-the-basics)</span><span class="sxs-lookup"><span data-stu-id="5955d-112">[![I'm new to mixed reality](images/Tile-New.jpg)](#understand-the-basics)</span></span><br>
        <span data-ttu-id="5955d-113">**[Mixed Reality を初めて使う](#understand-the-basics)**</span><span class="sxs-lookup"><span data-stu-id="5955d-113">**[I'm new to mixed reality](#understand-the-basics)**</span></span><br>
        <span data-ttu-id="5955d-114">基本を理解する</span><span class="sxs-lookup"><span data-stu-id="5955d-114">Understand the basics</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5955d-115">[![デザイナーである](images/Tile-Create.jpg)](../design/design.md)</span><span class="sxs-lookup"><span data-stu-id="5955d-115">[![I'm a designer](images/Tile-Create.jpg)](../design/design.md)</span></span><br>
        <span data-ttu-id="5955d-116">**[デザイナーである](../design/design.md)**</span><span class="sxs-lookup"><span data-stu-id="5955d-116">**[I'm a designer](../design/design.md)**</span></span><br>
        <span data-ttu-id="5955d-117">設計とプロトタイプ作成を始める</span><span class="sxs-lookup"><span data-stu-id="5955d-117">Start designing and prototyping</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="5955d-118">[![開発者である](images/Tile-Develop.jpg)](../develop/development.md)</span><span class="sxs-lookup"><span data-stu-id="5955d-118">[![I'm a developer](images/Tile-Develop.jpg)](../develop/development.md)</span></span><br>
        <span data-ttu-id="5955d-119">**[開発者である](../develop/development.md)**</span><span class="sxs-lookup"><span data-stu-id="5955d-119">**[I'm a developer](../develop/development.md)**</span></span><br>
        <span data-ttu-id="5955d-120">ツールとアーキテクチャについて学習する</span><span class="sxs-lookup"><span data-stu-id="5955d-120">Learn the tools and architecture</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="understand-the-basics"></a><span data-ttu-id="5955d-121">基本を理解する</span><span class="sxs-lookup"><span data-stu-id="5955d-121">Understand the basics</span></span>

<span data-ttu-id="5955d-122">Mixed Reality を初めて使用する場合は、その基本を理解することから始めて、中核概念、エクスペリエンス、機能の理解と積み重ねていくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="5955d-122">If you're new to mixed reality, it's important you start from the bottom and work your way up through its core concepts, experiences, and capabilities.</span></span> <span data-ttu-id="5955d-123">Mixed Reality で独自のアイデアを設計および開発するための確かな基盤を設けるのに役立つよう、一連の順序がある程度作成されています。</span><span class="sxs-lookup"><span data-stu-id="5955d-123">We've created a sequential journey of sorts to help you set a firm foundation for designing and developing your own ideas in Mixed Reality.</span></span>

### <a name="what-is-mixed-reality"></a><span data-ttu-id="5955d-124">Mixed Reality とは</span><span class="sxs-lookup"><span data-stu-id="5955d-124">What is mixed reality?</span></span>

![Mixed Reality でできること](images/HLS19_remoteAssistHologram_001.jpg)

<span data-ttu-id="5955d-126">アプリケーションの設計または開発を始める前に、Mixed Reality がどのような意味で使用されているのかを理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5955d-126">Before you dive into application design or development, you need to understand what we mean by Mixed Reality.</span></span> <span data-ttu-id="5955d-127">このセクションは、環境入力、知覚上の変化、設計上の課題、デバイスなど、Mixed Reality の範囲を理解できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="5955d-127">This section is designed to get you acquainted with the Mixed Reality spectrum, including environmental input, perceptual changes, design challenges, and devices.</span></span> 

|  <span data-ttu-id="5955d-128">概念</span><span class="sxs-lookup"><span data-stu-id="5955d-128">Concept</span></span>  |  <span data-ttu-id="5955d-129">結果</span><span class="sxs-lookup"><span data-stu-id="5955d-129">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="5955d-130">さまざまな Mixed Reality がある</span><span class="sxs-lookup"><span data-stu-id="5955d-130">Mixed reality is a spectrum</span></span>](../discover/mixed-reality.md) | <span data-ttu-id="5955d-131">Mixed Reality は物理とデジタルを融合するものであり、人間、コンピューター、環境の次世代の相互作用を実現します</span><span class="sxs-lookup"><span data-stu-id="5955d-131">Mixed reality blends the physical with the digital, the next evolution in human, computer, and environment interactions</span></span> |
| [<span data-ttu-id="5955d-132">ホログラムとは</span><span class="sxs-lookup"><span data-stu-id="5955d-132">What is a hologram?</span></span>](../discover/hologram.md) | <span data-ttu-id="5955d-133">HoloLens を使用すると、ホログラムを作成できます。ホログラムは、光と音で構成されたオブジェクトで、ユーザーの周囲に実際のオブジェクトのように表示されます。</span><span class="sxs-lookup"><span data-stu-id="5955d-133">HoloLens lets you create holograms, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="5955d-134">ホログラムは、視線入力、ジェスチャ、音声コマンドに応答し、周囲の現実世界のサーフェスと対話できます</span><span class="sxs-lookup"><span data-stu-id="5955d-134">Holograms respond to your gaze, gestures and voice commands, and can interact with real-world surfaces around you</span></span> |
| [<span data-ttu-id="5955d-135">Mixed Reality の学習の概要</span><span class="sxs-lookup"><span data-stu-id="5955d-135">Mixed Reality learning overview</span></span>](mr-learning-overview.md#general-modules) | <span data-ttu-id="5955d-136">Microsoft Learn を使用して厳選された Mixed Reality モジュールを試す</span><span class="sxs-lookup"><span data-stu-id="5955d-136">Try out our curated Mixed Reality module through Microsoft Learn</span></span> |
| [<span data-ttu-id="5955d-137">デザイン プロセスを展開する</span><span class="sxs-lookup"><span data-stu-id="5955d-137">Expand your design process</span></span>](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | <span data-ttu-id="5955d-138">イマーシブ エクスペリエンスを作成するときに空間的思考、ボディストーミング、行動により設計上の考え方を拡張します</span><span class="sxs-lookup"><span data-stu-id="5955d-138">Expand your design mindset with spatial thinking, bodystorming, and acting when creating your immersive experiences</span></span>  |

<br>

---

## <a name="see-how-industry-partners-are-using-mixed-reality"></a><span data-ttu-id="5955d-139">業界のパートナーが Mixed Reality をどのように使用しているかを確認する</span><span class="sxs-lookup"><span data-stu-id="5955d-139">See how industry partners are using mixed reality</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="5955d-140">[![Mercedes 自動車会社での HoloLens](images/mercedes.png)](https://customers.microsoft.com/story/839709-mercedes-benz-automotive-holoLens-en-usa)</span><span class="sxs-lookup"><span data-stu-id="5955d-140">[![Mercedes automotive HoloLens](images/mercedes.png)](https://customers.microsoft.com/story/839709-mercedes-benz-automotive-holoLens-en-usa)</span></span>
    :::column-end:::
    :::column span="2":::
        ### <a name="mercedes-benz-is-transforming-the-service-workforce-with-hololens-2-and-dynamics-365-remote-assist"></a>[<span data-ttu-id="5955d-141">Mercedes-Benz 社で進む、HoloLens 2 および Dynamics 365 Remote Assist を使用したサービス従業員の変革</span><span class="sxs-lookup"><span data-stu-id="5955d-141">Mercedes-Benz is transforming the service workforce with HoloLens 2 and Dynamics 365 Remote Assist</span></span>](https://customers.microsoft.com/story/839709-mercedes-benz-automotive-holoLens-en-usa)
        <span data-ttu-id="5955d-142">Mercedes-Benz USA 社は、HoloLens 2 と Dynamics 365 Remote Assist を使用して、サービス技術者の効率向上、問題解決の時間短縮、サービス関連の移動に要するコストと環境への影響の削減を実現しています。</span><span class="sxs-lookup"><span data-stu-id="5955d-142">Mercedes-Benz USA is using HoloLens 2 and Dynamics 365 Remote Assist to improve service technician efficiency, reduce time to problem solution, and reduce the cost and environmental impact of service-related travel.</span></span>
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       <span data-ttu-id="5955d-143">[![BHP エネルギー会社での Dynamics 365 HoloLens](images/bhp.png)](https://customers.microsoft.com/story/850776-bhp-energy-dynamics-365-hololens)</span><span class="sxs-lookup"><span data-stu-id="5955d-143">[![BHP energy dynamics 365 HoloLens](images/bhp.png)](https://customers.microsoft.com/story/850776-bhp-energy-dynamics-365-hololens)</span></span>
    :::column-end:::
    :::column span="2":::
        ### <a name="bhp-increases-the-pace-of-innovation-despite-lockdown-with-mixed-reality-and-iot"></a>[<span data-ttu-id="5955d-144">BHP 社は、Mixed Reality と IoT により、ロックダウン中でもイノベーションのペースを向上</span><span class="sxs-lookup"><span data-stu-id="5955d-144">BHP increases the pace of innovation despite lockdown with mixed reality and IoT</span></span>](https://customers.microsoft.com/story/850776-bhp-energy-dynamics-365-hololens)
        <span data-ttu-id="5955d-145">BHP 社は、COVID-19 による影響や数々の制限にもかかわらず、HoloLens 2 と Dynamics 365 Remote Assist を使用することにより、数千マイル離れた現場の従業員にサポートとトレーニングを提供しています。</span><span class="sxs-lookup"><span data-stu-id="5955d-145">Despite COVID-19's impact and restrictions, BHP is delivering support and training to field workers from thousands of miles away with HoloLens 2 and Dynamics 365 Remote Assist.</span></span>
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       <span data-ttu-id="5955d-146">[![MediView 社での HoloLens ストーリー](images/mediview.jpeg)](https://customers.microsoft.com/story/848966-mediview-mcs-story)</span><span class="sxs-lookup"><span data-stu-id="5955d-146">[![MediView HoloLens story](images/mediview.jpeg)](https://customers.microsoft.com/story/848966-mediview-mcs-story)</span></span>
    :::column-end:::
    :::column span="2":::
        ### <a name="healthcare-startup-cuts-time-to-market-by-up-to-70-despite-pandemic"></a>[<span data-ttu-id="5955d-147">医療分野のスタートアップ企業が、パンデミックにもかかわらず市場投入までの時間を最大 70% 削減</span><span class="sxs-lookup"><span data-stu-id="5955d-147">Healthcare startup cuts time to market by up to 70%, despite pandemic</span></span>](https://customers.microsoft.com/story/848966-mediview-mcs-story)
        <span data-ttu-id="5955d-148">医療分野のスタートアップ企業である MediView 社は、3D ホログラムを使用した優れた製品を開発しました。この製品は、3D ホログラムが患者の解剖画像上に直接投影するか、その上にホバリング表示して、外科医が患者の体内の解剖画像を確認できるようにするとともに、手術中の外科医へのガイドも提供します。</span><span class="sxs-lookup"><span data-stu-id="5955d-148">Healthcare startup Mediview has developed a remarkable product that uses 3D holograms projected either directly on top of the patient’s anatomy or hovering above it to help surgeons see the patients internal anatomy and guide them through procedures.</span></span>
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       <span data-ttu-id="5955d-149">[![Bentley](images/Bentley-Synchro1.jpg)](https://binged.it/31AR3kP)</span><span class="sxs-lookup"><span data-stu-id="5955d-149">[![Bentley](images/Bentley-Synchro1.jpg)](https://binged.it/31AR3kP)</span></span>
    :::column-end:::
    :::column span="2":::
        ### <a name="view-complex-construction-projects-with-bentleys-digital-construction-software"></a>[<span data-ttu-id="5955d-150">Bentley のデジタル建設ソフトウェアで複雑な建設プロジェクトを表示する</span><span class="sxs-lookup"><span data-stu-id="5955d-150">View complex construction projects with Bentley's digital construction software</span></span>](https://binged.it/31AR3kP)
        <span data-ttu-id="5955d-151">Synchro は、複雑な建設プロジェクトを Mixed Reality で表示できるようにする Bentley のデジタル建設ソフトウェアです。</span><span class="sxs-lookup"><span data-stu-id="5955d-151">Synchro is digital construction software that enables viewing complex construction projects in mixed reality.</span></span> <span data-ttu-id="5955d-152">これらの 4D デジタル建設プラットフォームは、従来のガント チャート CPM スケジュールと、統合されたリアルタイムの 4D 視覚化機能を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="5955d-152">Their 4D digital construction platform combines traditional Gantt chart CPM scheduling with integrated 4D visualization capabilities in real time.</span></span>
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       <span data-ttu-id="5955d-153">[![PTC の Vuforia Studio](images/PTC-Vuforia-Studio1.jpg)](https://binged.it/31ARrjh)</span><span class="sxs-lookup"><span data-stu-id="5955d-153">[![PTC's Vuforia Studio](images/PTC-Vuforia-Studio1.jpg)](https://binged.it/31ARrjh)</span></span>
    :::column-end:::
    :::column span="2":::
        ### <a name="ptcs-vuforia-studio-authoring-solution-promotes-workforce-productivity-and-safety"></a>[<span data-ttu-id="5955d-154">PTC の Vuforia Studio 作成ソリューションで従業員の生産性と安全性を促進する</span><span class="sxs-lookup"><span data-stu-id="5955d-154">PTC's Vuforia Studio authoring solution promotes workforce productivity and safety</span></span>](https://binged.it/31ARrjh)
        <span data-ttu-id="5955d-155">Vuforia Studio の効率的な Mixed Reality 作成ソリューションは、従業員が最も頻繁に必要とする情報を提供することによって、従業員の生産性と安全性を促進します。これは、日常業務環境の実際のコンテキストで使用されます。</span><span class="sxs-lookup"><span data-stu-id="5955d-155">Vuforia Studio's efficient mixed reality authoring solution promotes workforce productivity and safety by delivering information when and where workers need it most: in the real-world context of their daily work environment.</span></span>
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       <span data-ttu-id="5955d-156">[![Philips-Azurion](images/Philips-Azurion1.jpg)](https://binged.it/31B1RiR)</span><span class="sxs-lookup"><span data-stu-id="5955d-156">[![Philips-Azurion](images/Philips-Azurion1.jpg)](https://binged.it/31B1RiR)</span></span>
    :::column-end:::
    :::column span="2":::
        ### <a name="philips-is-piloting-hololens-in-the-domain-of-image-guided-invasive-procedures"></a>[<span data-ttu-id="5955d-157">Philips 社は、画像誘導型の侵襲的処置の分野で HoloLens をいち早く導入</span><span class="sxs-lookup"><span data-stu-id="5955d-157">Philips is piloting HoloLens in the domain of image-guided invasive procedures</span></span>](https://binged.it/31B1RiR)
        <span data-ttu-id="5955d-158">Philips は画像誘導型の侵襲的処置の分野で HoloLens をいち早く導入しています。医師はライブ X 線、超音波、その他の情報源を利用して、患者の体内を "見る" ことにより、処置に役立てています。</span><span class="sxs-lookup"><span data-stu-id="5955d-158">Philips is piloting HoloLens in the domain of image-guided invasive procedures, during which physicians rely on live X-ray, ultrasound, and other sources of information to "see" inside the patient and guide their actions.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="explore-hololens-and-mixed-reality-services"></a><span data-ttu-id="5955d-159">HoloLens と Mixed Reality サービスを調べる</span><span class="sxs-lookup"><span data-stu-id="5955d-159">Explore HoloLens and Mixed Reality services</span></span>

![HoloLens の分解図](images/HoloLens2_ExplodedView_8k.png)

<span data-ttu-id="5955d-161">さまざまな Mixed Reality ハードウェアとサービスがどのように動作するかを知りたい場合は、以下のリンクを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5955d-161">If you're curious to see how the different Mixed Reality hardware and services work, check out the links below.</span></span> <span data-ttu-id="5955d-162">これらのリンクをクリックすると、Microsoft ドキュメントのさまざまな部分に移動します。</span><span class="sxs-lookup"><span data-stu-id="5955d-162">These links will navigate you to different parts of the Microsoft documentation.</span></span> <span data-ttu-id="5955d-163">設計と開発の体験を続けるために、このページをブックマークして、このページに戻ることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5955d-163">We recommend bookmarking and returning here to continue on your design and development journey.</span></span>

|  <span data-ttu-id="5955d-164">概念</span><span class="sxs-lookup"><span data-stu-id="5955d-164">Concept</span></span>  |  <span data-ttu-id="5955d-165">結果</span><span class="sxs-lookup"><span data-stu-id="5955d-165">Outcome</span></span>  |
| --- | --- |
| [<span data-ttu-id="5955d-166">HoloLens ハードウェア</span><span class="sxs-lookup"><span data-stu-id="5955d-166">HoloLens hardware</span></span>](https://www.microsoft.com//hololens/hardware) | <span data-ttu-id="5955d-167">HoloLens 2 は、数分で価値を提供できる業界最先端のソリューションにより、最も快適でイマーシブな複合現実エクスペリエンスを提供します。これらはすべて、Microsoft のクラウドおよび AI サービスの信頼性、セキュリティ、および拡張性によって強化されています</span><span class="sxs-lookup"><span data-stu-id="5955d-167">HoloLens 2 offers the most comfortable and immersive mixed reality experience available, with industry-leading solutions that deliver value in minutes—all enhanced by the reliability, security, and scalability of cloud and AI services from Microsoft</span></span> |
| [<span data-ttu-id="5955d-168">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="5955d-168">Dynamics 365</span></span>](https://dynamics.microsoft.com/mixed-reality/overview/) | <span data-ttu-id="5955d-169">[Remote Assist](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/ra-overview)、Layout、[Guides](https://docs.microsoft.com/dynamics365/mixed-reality/guides/) など、従業員を支援し、Dynamics 365 での操作を最適化できる、さまざまな製品を紹介します</span><span class="sxs-lookup"><span data-stu-id="5955d-169">Explore a range of products that can empower employees and optimize operations with Dynamics 365, including [Remote Assist](https://docs.microsoft.com/dynamics365/mixed-reality/remote-assist/ra-overview), [Layout, and [Guides](https://docs.microsoft.com/dynamics365/mixed-reality/guides/).</span></span> <span data-ttu-id="5955d-170">実際の仕事、実際のデバイス、実際のユーザーの実体験から、実践的な分析情報が得られます</span><span class="sxs-lookup"><span data-stu-id="5955d-170">Meaningful insight comes from getting hands-on with real work, real devices, and real users</span></span> |
| [<span data-ttu-id="5955d-171">Azure Cloud Services</span><span class="sxs-lookup"><span data-stu-id="5955d-171">Azure Cloud Services</span></span>](../develop/mixed-reality-cloud-services.md) | <span data-ttu-id="5955d-172">空間認識、空間アンカー、複雑な 3D モデル レンダリングを使用して、異なるプラットフォームで魅力的なイマーシブ エクスペリエンスを構築します</span><span class="sxs-lookup"><span data-stu-id="5955d-172">Build compelling immersive experiences on different platforms with spatial awareness, spatial anchors, and complex 3D model rendering</span></span> |

## <a name="what-would-you-like-to-do-next"></a><span data-ttu-id="5955d-173">次に行うこと</span><span class="sxs-lookup"><span data-stu-id="5955d-173">What would you like to do next?</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="5955d-174">[![作成者になる](images/icon-design.png)](../design/design.md)</span><span class="sxs-lookup"><span data-stu-id="5955d-174">[![Become a creator](images/icon-design.png)](../design/design.md)</span></span><br>
        <span data-ttu-id="5955d-175">**[作成者になる](../design/design.md)**</span><span class="sxs-lookup"><span data-stu-id="5955d-175">**[Become a creator](../design/design.md)**</span></span><br>
        <span data-ttu-id="5955d-176">設計とプロトタイプ作成を開始するために必要な基本的な概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="5955d-176">Learn the basic concepts you need to begin designing and prototyping.</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="5955d-177">[![開発を始める](images/icon-developer.png)](../develop/development.md)</span><span class="sxs-lookup"><span data-stu-id="5955d-177">[![Start developing](images/icon-developer.png)](../develop/development.md)</span></span><br>
        <span data-ttu-id="5955d-178">**[開発を始める](../develop/development.md)**</span><span class="sxs-lookup"><span data-stu-id="5955d-178">**[Start developing](../develop/development.md)**</span></span><br>
        <span data-ttu-id="5955d-179">スキル レベル、ワーク スタイル、プラットフォームへの関心に基づいて、開発パスを選択します。</span><span class="sxs-lookup"><span data-stu-id="5955d-179">Choose a development path based on your skill level, work style, or platform interest.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="5955d-180">[![イベントに参加する](images/icon-calendar.jpg)](../whats-new/sf-academy-events.md)</span><span class="sxs-lookup"><span data-stu-id="5955d-180">[![Come to an event](images/icon-calendar.jpg)](../whats-new/sf-academy-events.md)</span></span><br>
        <span data-ttu-id="5955d-181">**[イベントに参加する](../whats-new/sf-academy-events.md)**</span><span class="sxs-lookup"><span data-stu-id="5955d-181">**[Come to an event](../whats-new/sf-academy-events.md)**</span></span><br>
        <span data-ttu-id="5955d-182">最初の HoloLens 2 アプリケーションを作成するには、ハードウェアを参照し、ハンズオン チュートリアルを入手してください。</span><span class="sxs-lookup"><span data-stu-id="5955d-182">See the hardware and get a hands-on tutorial to make your first HoloLens 2 application.</span></span>
    :::column-end:::
:::row-end:::


<br>

<br>

>[!IMPORTANT]
><span data-ttu-id="5955d-183">このサイトで提供されるすべての複合現実の開発に関する資料は参照のみを目的としています。</span><span class="sxs-lookup"><span data-stu-id="5955d-183">All mixed reality development materials are provided on this site for your reference only.</span></span> <span data-ttu-id="5955d-184">アプリケーションとその使用法およびエンド ユーザーに与える影響は、アプリケーション開発者としてお客様に責任があるものとし、これには、アプリがエンド ユーザーに対して不快感、傷害、またはその他の害をもたらしたりするものではないことや適切な警告文および免責文を含むことが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5955d-184">Your application, its usage, and its effect on end users is your sole responsibility as the application developer, including ensuring that your app does not cause discomfort, injury, or any other harm to the end user, and including appropriate warnings and disclaimers.</span></span> <span data-ttu-id="5955d-185">お客様は、自分のアプリケーションが安全であり、「[Microsoft とのアプリ開発者契約](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement)」のすべての責務を満たしていることを保証するために、アプリケーションの開発と発行において常に適切な手順を踏む必要があります。</span><span class="sxs-lookup"><span data-stu-id="5955d-185">You need to at all times take the appropriate steps in the development and publishing of your application to ensure that your application is safe, and that you meet all obligations in your [App Developer Agreement with Microsoft](https://docs.microsoft.com/legal/windows/agreements/app-developer-agreement).</span></span>

