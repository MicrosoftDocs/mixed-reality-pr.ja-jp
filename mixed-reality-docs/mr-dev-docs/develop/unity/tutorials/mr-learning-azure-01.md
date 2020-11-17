---
title: Azure Cloud チュートリアル - 1. HoloLens 2 用の Azure Cloud Services
description: このコースを完了すると、HoloLens 2 アプリケーション内でさまざまな Azure サービスを実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Azure, Mixed Reality, Unity, チュートリアル, Hololens, Hololens 2, Azure Blob Storage, Azure Table Storage, Azure Spatial Anchors, Azure Bot Framework
ms.localizationpriority: high
ms.openlocfilehash: 878fd92a946b70ba3b0a867722f86ab801a79032
ms.sourcegitcommit: 8fd127aff85b77778bd7a75c5ec5215d27ecf21a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2020
ms.locfileid: "93416978"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a><span data-ttu-id="d530d-105">1.HoloLens 2 用の Azure Cloud Services</span><span class="sxs-lookup"><span data-stu-id="d530d-105">1. Azure Cloud Services for HoloLens 2</span></span>

## <a name="overview"></a><span data-ttu-id="d530d-106">概要</span><span class="sxs-lookup"><span data-stu-id="d530d-106">Overview</span></span>

<span data-ttu-id="d530d-107">このチュートリアル シリーズへようこそ。ここでは、**Azure クラウド** サービスを **HoloLens 2** アプリケーションに導入することに重点を置いています。</span><span class="sxs-lookup"><span data-stu-id="d530d-107">Welcome to this series of tutorials focused on bringing **Azure Cloud** services into a **HoloLens 2** application.</span></span> <span data-ttu-id="d530d-108">この 5 部構成のチュートリアル シリーズでは、複数の **Azure クラウド** サービスを **HoloLens 2** 用の **Unity** プロジェクトに統合する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="d530d-108">In this five-part tutorial series, you will learn how to integrate several **Azure Cloud** services into a **Unity** project for **HoloLens 2**.</span></span> <span data-ttu-id="d530d-109">連続する各章では、新しい **Azure クラウド** サービスを追加して、アプリケーションの機能とユーザー エクスペリエンスを拡張しながら、各 **Azure クラウド** サービスの基礎について学びます。</span><span class="sxs-lookup"><span data-stu-id="d530d-109">With each consecutive chapter, you will add new **Azure Cloud** services to expand the application features and user experience, while teaching you the fundamentals of each **Azure Cloud** service.</span></span>

> [!NOTE]
> <span data-ttu-id="d530d-110">このチュートリアル シリーズでは **HoloLens 2** に重点を置いていますが、Unity のクロスプラットフォームの性質により、学習内容のほとんどがデスクトップおよび Smartphone アプリケーションにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="d530d-110">This tutorial series will focus on the **HoloLens 2** but due the cross-platform nature of Unity, most of your learnings will also apply for Desktop and Smartphone applications.</span></span>

<span data-ttu-id="d530d-111">この最初のチュートリアルでは、シリーズの目標、使用する各 Azure Cloud サービス、および最初の Unity プロジェクトの設定について紹介します。</span><span class="sxs-lookup"><span data-stu-id="d530d-111">In this first tutorial, you'll be introduced to the goals of the series and each Azure Cloud service you'll be using, as well as setting up the initial Unity project.</span></span>

<span data-ttu-id="d530d-112">2 番目のチュートリアルである「[Azure Storage の統合](mr-learning-azure-02.md)」では、Azure Storage をデモ アプリケーションの永続化ソリューションとして統合することから始めます。</span><span class="sxs-lookup"><span data-stu-id="d530d-112">In the second tutorial, [Integrating Azure Storage](mr-learning-azure-02.md), you'll start off by integrating Azure Storage as the persistence solution for the demo application.</span></span> <span data-ttu-id="d530d-113">また、Blob Storage と Table Storage の違いについて学習し、必要なプロジェクト リソースを準備して、シーンを設定します。</span><span class="sxs-lookup"><span data-stu-id="d530d-113">You'll also learn the differences between Blob Storage and Table Storage, prepare the needed project resources, setup the scene.</span></span> <span data-ttu-id="d530d-114">最後に、データの読み取り、更新、および削除操作を確認する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d530d-114">Finally, you'll learn how to verify the read, update, and delete data operations.</span></span>

<span data-ttu-id="d530d-115">3 番目のチュートリアルである、「[Azure Custom Vision の統合](mr-learning-azure-03.md)」に進んで、Azure Custom Vision を使用して、HoloLens 2 アプリケーションで画像をトレーニングおよび検出します。</span><span class="sxs-lookup"><span data-stu-id="d530d-115">Continuing with the third tutorial, [Integrating Azure Custom Vision](mr-learning-azure-03.md), you will use Azure Custom Vision to train and detect images in the HoloLens 2 application.</span></span> <span data-ttu-id="d530d-116">この章では、まず、独自の Azure Custom Vision リソースを設定し、シーン コンポーネントを準備し、アプリケーション内部から独自の画像をトレーニングおよび検出してアクションを開始します。</span><span class="sxs-lookup"><span data-stu-id="d530d-116">The chapter starts off with setting up your own Azure Custom Vision resource, preparing the scene components and getting into action by training and detecting your own images from inside the application.</span></span>

<span data-ttu-id="d530d-117">次に、4 番目のチュートリアルである、「[Azure Spatial Anchors の統合](mr-learning-azure-04.md)」に進んで、Azure Spatial Anchors サービスを調べて場所の保存と検索を行い、主要概念について学習し、必要なリソースを準備し、シーンを設定してアプリケーションでの新機能の使用を開始します。</span><span class="sxs-lookup"><span data-stu-id="d530d-117">Next you advance in the fourth tutorial, [Integrating Azure Spatial Anchors](mr-learning-azure-04.md), with exploring Azure Spatial Anchors service to save and find locations, learn the core concepts, prepare necessary resources, setup the scene and start using the new feature in the application.</span></span>

<span data-ttu-id="d530d-118">[Azure Bot Service と LUIS との統合](mr-learning-azure-05.md)に関する、5 番目のチュートリアルでは、アプリケーションに自然言語という新しいユーザー操作の方法を与えることで完了します。</span><span class="sxs-lookup"><span data-stu-id="d530d-118">With the fifth tutorial, [Integrating Azure Bot Service with LUIS](mr-learning-azure-05.md), you finalize by giving the application a new method of user interaction: natural language!</span></span> <span data-ttu-id="d530d-119">この機能は、Azure Bot Framework を Language Understanding (LUIS) と共に使用することで実現されます。</span><span class="sxs-lookup"><span data-stu-id="d530d-119">This feature will be realized by using the Azure Bot Framework together with Language Understanding (LUIS).</span></span> <span data-ttu-id="d530d-120">この最後の章では、Azure Bot Service の基本について説明し、プロセスを高速化するために、Bot Framework Composer をゼロ コード ソリューションとして使用します。</span><span class="sxs-lookup"><span data-stu-id="d530d-120">This final chapter teaches you the basics of Azure Bot Service and to speed up the process you will be using the Bot Framework Composer as a zero code solution.</span></span> <span data-ttu-id="d530d-121">ボットが作成されたら、それをシーンに統合し、HoloLens 2 アプリケーションの最終ステージで実行します。</span><span class="sxs-lookup"><span data-stu-id="d530d-121">Once the bot is created, you will integrate it into the scene and give it a run with the final stage of the HoloLens 2 application.</span></span>

## <a name="application-goals"></a><span data-ttu-id="d530d-122">アプリケーションの目標</span><span class="sxs-lookup"><span data-stu-id="d530d-122">Application goals</span></span>

<span data-ttu-id="d530d-123">このチュートリアル シリーズでは、画像からオブジェクトを検出し、その空間位置を見つけることができる **HoloLens 2** アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="d530d-123">In this tutorial series, you will build a **HoloLens 2** application that can detect objects from images and find its spatial location.</span></span> <span data-ttu-id="d530d-124">ドメインの言語を設定するために、**追跡対象オブジェクト** からこのようなエンティティを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d530d-124">To set a domain language, you call such entities from now **Tracked Object**.</span></span>
<span data-ttu-id="d530d-125">ユーザーは **追跡対象オブジェクト** を作成し、コンピューター ビジョンまたは空間位置、あるいはその両方を使用して画像のセットを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="d530d-125">The user can create a **Tracked Object** to either or both associate a set of images via computer vision and/or a spatial location.</span></span> <span data-ttu-id="d530d-126">すべてのデータをクラウドに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d530d-126">All data must be persisted into the cloud.</span></span> <span data-ttu-id="d530d-127">さらに、アプリケーションの一部の側面は、ボットを通じてサポートされる自然言語によって制御されることもあります。</span><span class="sxs-lookup"><span data-stu-id="d530d-127">Furthermore some aspects of the application will be optionally controlled by natural language assisted through a bot.</span></span>

### <a name="features"></a><span data-ttu-id="d530d-128">機能</span><span class="sxs-lookup"><span data-stu-id="d530d-128">Features</span></span>

* <span data-ttu-id="d530d-129">データと画像の基本的な管理</span><span class="sxs-lookup"><span data-stu-id="d530d-129">Basic managing of data and images</span></span>
* <span data-ttu-id="d530d-130">画像のトレーニングと検出</span><span class="sxs-lookup"><span data-stu-id="d530d-130">Image training and detection</span></span>
* <span data-ttu-id="d530d-131">空間位置の格納とそのガイダンス</span><span class="sxs-lookup"><span data-stu-id="d530d-131">Storing a spatial location and guidance to it</span></span>
* <span data-ttu-id="d530d-132">自然言語を介して一部の機能を使用するためのボット サポート</span><span class="sxs-lookup"><span data-stu-id="d530d-132">Bot assistant to use some features via natural language</span></span>

## <a name="azure-cloud-services"></a><span data-ttu-id="d530d-133">Azure クラウド サービス</span><span class="sxs-lookup"><span data-stu-id="d530d-133">Azure Cloud services</span></span>

<span data-ttu-id="d530d-134">以下の **Azure Cloud** サービスを使用して、上の機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="d530d-134">You'll use the following **Azure Cloud** services to implement the above features:</span></span>

### <a name="azure-storage"></a><span data-ttu-id="d530d-135">Azure Storage に関するページ</span><span class="sxs-lookup"><span data-stu-id="d530d-135">Azure Storage</span></span>

<span data-ttu-id="d530d-136">永続化ソリューションには、[Azure Storage](https://azure.microsoft.com/services/storage/) を使用します。</span><span class="sxs-lookup"><span data-stu-id="d530d-136">You will use [Azure Storage](https://azure.microsoft.com/services/storage/) for the persistence solution.</span></span> <span data-ttu-id="d530d-137">これにより、データをテーブルに格納し、画像のような大きなバイナリをアップロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="d530d-137">It allows you to store data on a table and upload large binaries like images.</span></span>

### <a name="azure-custom-vision"></a><span data-ttu-id="d530d-138">Azure Custom Vision</span><span class="sxs-lookup"><span data-stu-id="d530d-138">Azure Custom Vision</span></span>

<span data-ttu-id="d530d-139">[Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) ([Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/) の一部) を使用すると、画像のセットを "*追跡対象オブジェクト*" に関連付けたり、そのセットで機械学習モデルをトレーニングしたり、"*追跡対象オブジェクト*" を検出したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="d530d-139">With [Azure Custom Vision](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (part of the [Azure Cognitive Services](https://azure.microsoft.com/services/cognitive-services/)) you can associate to *Tracked Objects* a set of images, train a machine learning model on the set and detect the *Tracked Object*.</span></span>

### <a name="azure-spatial-anchors"></a><span data-ttu-id="d530d-140">Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="d530d-140">Azure Spatial Anchors</span></span>

<span data-ttu-id="d530d-141">"*追跡対象オブジェクト*" の場所を格納し、それを見つけられるようにガイドするには、[Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/) を使用します。</span><span class="sxs-lookup"><span data-stu-id="d530d-141">To store a *Tracked Object* location and give a guided directions to find it, you use [Azure Spatial Anchors](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

### <a name="azure-bot-service"></a><span data-ttu-id="d530d-142">Azure Bot Service</span><span class="sxs-lookup"><span data-stu-id="d530d-142">Azure Bot Service</span></span>

<span data-ttu-id="d530d-143">アプリケーションは主に従来の UI で起動するため、[Azure Bot Service](https://azure.microsoft.com/services/bot-service/) を使用して、何らかの個性を加え、新しい操作方法として機能するようにします。</span><span class="sxs-lookup"><span data-stu-id="d530d-143">The application is mainly driven by traditional UI, so you use the [Azure Bot Service](https://azure.microsoft.com/services/bot-service/) to add some personality and act as a new interaction method.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d530d-144">前提条件</span><span class="sxs-lookup"><span data-stu-id="d530d-144">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="d530d-145">[入門チュートリアル](mr-learning-base-01.md) シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d530d-145">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="d530d-146">正しい[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="d530d-146">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="d530d-147">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="d530d-147">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="d530d-148">基本的な C# プログラミング能力</span><span class="sxs-lookup"><span data-stu-id="d530d-148">Some basic C# programming ability</span></span>
* <span data-ttu-id="d530d-149">[開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="d530d-149">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="d530d-150">Unity エディターからテストする場合は、接続された Web カメラ</span><span class="sxs-lookup"><span data-stu-id="d530d-150">A connected webcam if you like to test from Unity editor</span></span>
* <span data-ttu-id="d530d-151">Unity 2019 LTS がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="d530d-151"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="d530d-152">このチュートリアル シリーズで推奨されている Unity バージョンは、Unity 2019 LTS です。</span><span class="sxs-lookup"><span data-stu-id="d530d-152">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="d530d-153">これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="d530d-153">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="d530d-154">Unity プロジェクトの作成と準備</span><span class="sxs-lookup"><span data-stu-id="d530d-154">Creating and preparing the Unity project</span></span>

<span data-ttu-id="d530d-155">このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備します。</span><span class="sxs-lookup"><span data-stu-id="d530d-155">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="d530d-156">このためには、まず「[プロジェクトと最初のアプリケーションの初期化](mr-learning-base-02.md)」に従ってください (「[デバイスへのアプリケーションのビルド](mr-learning-base-02.md#building-your-application-to-your-hololens-2)」の手順は除く)。これには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d530d-156">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="d530d-157">[Unity プロジェクトを作成](mr-learning-base-02.md#creating-the-unity-project)し、"*Azure クラウド チュートリアル*" などの適切な名前を付ける</span><span class="sxs-lookup"><span data-stu-id="d530d-157">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *Azure Cloud Tutorials*</span></span>
2. [<span data-ttu-id="d530d-158">ビルド プラットフォームを切り替える</span><span class="sxs-lookup"><span data-stu-id="d530d-158">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
3. [<span data-ttu-id="d530d-159">TextMeshPro の重要なリソースをインポートする</span><span class="sxs-lookup"><span data-stu-id="d530d-159">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="d530d-160">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="d530d-160">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="d530d-161">Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="d530d-161">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="d530d-162">[シーンを作成して構成](mr-learning-base-02.md#creating-and-configuring-the-scene)し、シーンに *AzureCloudServices* などの適切な名前を付ける</span><span class="sxs-lookup"><span data-stu-id="d530d-162">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureCloudServices*</span></span>

<span data-ttu-id="d530d-163">その後、「[空間認識表示オプションの変更](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)」の手順に従って、シーンの MRTK 構成プロファイルを **[DefaultHoloLens2ConfigurationProfile]** に変更し、空間認識メッシュの表示オプションを **[Occlusion]\(オクルージョン\)** に変更します。</span><span class="sxs-lookup"><span data-stu-id="d530d-163">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="d530d-164">組み込みの Unity パッケージのインストール</span><span class="sxs-lookup"><span data-stu-id="d530d-164">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="d530d-165">Unity メニューで、 **[ウィンドウ]**  >  **[パッケージ マネージャー]** の順に選択して、[パッケージ マネージャー] ウィンドウを開きます。その後、 **[AR Foundation]** を選択し、 **[インストール]** ボタンをクリックしてパッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="d530d-165">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![AR Foundation が選択されている Unity Package Manager ウィンドウ](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="d530d-167">Azure Spatial Anchors SDK で必要になるため、AR Foundation パッケージをインストールします。これは、次のセクションでインポートします。</span><span class="sxs-lookup"><span data-stu-id="d530d-167">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="d530d-168">チュートリアルのアセットのインポート</span><span class="sxs-lookup"><span data-stu-id="d530d-168">Importing the tutorial assets</span></span>

<span data-ttu-id="d530d-169">次の Unity カスタム パッケージを、**記載されている順で** ダウンロードして **インポート** します。</span><span class="sxs-lookup"><span data-stu-id="d530d-169">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* [<span data-ttu-id="d530d-170">AzureSpatialAnchors.unitypackage</span><span class="sxs-lookup"><span data-stu-id="d530d-170">AzureSpatialAnchors.unitypackage</span></span>](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage)
* [<span data-ttu-id="d530d-171">AzureStorageForUnity.unitypackage</span><span class="sxs-lookup"><span data-stu-id="d530d-171">AzureStorageForUnity.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureStorageForUnity.unitypackage)
* [<span data-ttu-id="d530d-172">MRTK.Tutorials.AzureCloudServices.unitypackage</span><span class="sxs-lookup"><span data-stu-id="d530d-172">MRTK.Tutorials.AzureCloudServices.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/MRTK.Tutorials.AzureCloudServices.unitypackage)

> [!TIP]
> <span data-ttu-id="d530d-173">Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d530d-173">For a reminder on how to import a Unity custom package, you can refer to the [Import the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="d530d-174">チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d530d-174">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![チュートリアルのアセットがインポートされた後の Unity の [Hierarchy]\(階層\)、[Scene]\(シーン\)、[Project]\(プロジェクト\) ウィンドウ](images/mr-learning-azure/tutorial1-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="d530d-176">"WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)" と "WorldAnchor.GetNativeSpatialAnchorPtr()" が廃止されていることに関する CS0618 警告が表示されても、無視してかまいません。</span><span class="sxs-lookup"><span data-stu-id="d530d-176">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' and 'WorldAnchor.GetNativeSpatialAnchorPtr()' being obsolete, you can ignore these warnings.</span></span>

## <a name="creating-and-preparing-the-scene"></a><span data-ttu-id="d530d-177">シーンの作成と準備</span><span class="sxs-lookup"><span data-stu-id="d530d-177">Creating and preparing the scene</span></span>
<!-- TODO: Consider renaming to 'Preparing the scene' -->

<span data-ttu-id="d530d-178">このセクションでは、チュートリアルのプレハブをいくつか追加してシーンを準備します。</span><span class="sxs-lookup"><span data-stu-id="d530d-178">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="d530d-179">[プロジェクト] ウィンドウで、**Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** フォルダーの順に移動します。</span><span class="sxs-lookup"><span data-stu-id="d530d-179">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span> <span data-ttu-id="d530d-180">CTRL ボタンを押したまま、 **[SceneController]** 、 **[RootMenu]** および **[DataManager]** をクリックして、3 つのプレハブを選択します。</span><span class="sxs-lookup"><span data-stu-id="d530d-180">While holding down the CTRL button, click on **SceneController**, **RootMenu** and **DataManager** to select the three prefabs:</span></span>

![SceneController、RootMenu、DataManager の各プレハブが選択されている Unity](images/mr-learning-azure/tutorial1-section5-step1-1.png)

<span data-ttu-id="d530d-182">**SceneController (プレハブ)** には、**SceneController (スクリプト)** と **UnityDispatcher (スクリプト)** の 2 つのスクリプトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d530d-182">The **SceneController (prefab)** contains two scripts, **SceneController (script)** and **UnityDispatcher (script)**.</span></span> <span data-ttu-id="d530d-183">**SceneController** スクリプト コンポーネントには、いくつかの UX 関数が含まれており、写真キャプチャ機能が促進されますが、**UnityDispatcher** は、Unity メイン スレッドでのアクションの実行を許可するヘルパー クラスです。</span><span class="sxs-lookup"><span data-stu-id="d530d-183">The **SceneController** script component contains several UX functions and facilitates the photo capture functionality while **UnityDispatcher** is a helper class to allow execute actions on the Unity main thread.</span></span>

<span data-ttu-id="d530d-184">**RootMenu (プレハブ)** は、さまざまな小さいスクリプト コンポーネントを介して相互に接続され、アプリケーションの一般的な UX フローを制御する UI ウィンドウをすべて保持する主要な UI プレハブです。</span><span class="sxs-lookup"><span data-stu-id="d530d-184">The **RootMenu (prefab)** is the primary UI prefab that holds all UI windows that are connected to each other through various small script components and control the general UX flow of the application.</span></span>

<span data-ttu-id="d530d-185">**DataManager (プレハブ)** は、Azure Storage との対話を担当します。これについては、次のチュートリアルで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="d530d-185">The **DataManager (prefab)** is responsible for talking to Azure storage and will be explained further in the next tutorial.</span></span>

<span data-ttu-id="d530d-186">ここで、3 つのプレハブを選択したまま、それらを [階層] ウィンドウにドラッグしてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="d530d-186">Now with the three prefabs still selected, drag them into the Hierarchy window to add them to the scene:</span></span>

![新しく追加された SceneController、RootMenu、DataManager の各プレハブがまだ選択されている Unity](images/mr-learning-azure/tutorial1-section5-step1-2.png)

<span data-ttu-id="d530d-188">シーン内のオブジェクトに焦点を合わせるために、**RootMenu** オブジェクトをダブルクリックし、もう一度少しズームアウトすることができます。</span><span class="sxs-lookup"><span data-stu-id="d530d-188">To focus in on the objects in the scene, you can double-click on the **RootMenu** object, and then zoom slightly out again:</span></span>

![RootMenu オブジェクトが選択されている Unity](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> <span data-ttu-id="d530d-190">シーンに大きいアイコンが表示されている場合 (たとえば、大きいフレームの 'T' アイコンが邪魔になる場合)、<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">ギズモをオフに切り替える</a>ことによってこれらを非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d530d-190">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position.</span></span>

## <a name="configuring-the-scene"></a><span data-ttu-id="d530d-191">シーンの構成</span><span class="sxs-lookup"><span data-stu-id="d530d-191">Configuring the scene</span></span>

<span data-ttu-id="d530d-192">このセクションでは、*SceneManager*、*DataManager* および *RootMenu* を一緒に接続し、作業シーンを次の「[Azure Storage の統合](mr-learning-azure-01.md)」チュートリアルのために準備します。</span><span class="sxs-lookup"><span data-stu-id="d530d-192">In this section, you will connect *SceneManager*, *DataManager* and *RootMenu* together to have a working scene to be ready for the following [Integrating Azure storage](mr-learning-azure-01.md) tutorial.</span></span>

### <a name="connect-the-objects"></a><span data-ttu-id="d530d-193">オブジェクトを接続する</span><span class="sxs-lookup"><span data-stu-id="d530d-193">Connect the objects</span></span>

<span data-ttu-id="d530d-194">[階層] ウィンドウで、**DataManager** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="d530d-194">In the Hierarchy window, select the **DataManager** object:</span></span>

![DataManager オブジェクトが選択されている Unity](images/mr-learning-azure/tutorial1-section6-step1-1.png)

<span data-ttu-id="d530d-196">[インスペクター] ウィンドウで、**DataManager (Script)** コンポーネントを見つけます。**On Data Manager Ready ()** イベントには空のスロットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d530d-196">In the Inspector window, locate the **DataManager (Script)** component and you will see an empty slot on the **On Data Manager Ready ()** event.</span></span> <span data-ttu-id="d530d-197">ここで、[階層] ウィンドウから、**SceneController** オブジェクトを **On Data Manager Ready ()** イベントにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="d530d-197">Now from the Hierarchy window drag the **SceneController** object into the **On Data Manager Ready ()** event.</span></span>

![DataManager イベント リスナーが追加された Unity](images/mr-learning-azure/tutorial1-section6-step1-2.png)

<span data-ttu-id="d530d-199">イベントのドロップダウン メニューがアクティブになったことがわかります。このドロップダウン メニューをクリックして、**SceneController** に移動し、サブ メニューで **[Init ()]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="d530d-199">You will notice that the dropdown menu of the event became active, click on the dropdown menu and navigate to **SceneController** and in the sub menu select the **Init ()** option:</span></span>

![DataManager イベント アクションが追加された Unity](images/mr-learning-azure/tutorial1-section6-step1-3.png)

<span data-ttu-id="d530d-201">[階層] ウィンドウで **SceneController** オブジェクトを選択すると、[インスペクター] に **SceneController** (スクリプト) コンポーネントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d530d-201">From the Hierarchy window, select the **SceneController** object, there in the Inspector you will find the **SceneController** (script) component.</span></span>

![SceneController が選択されている Unity](images/mr-learning-azure/tutorial1-section6-step1-4.png)

<span data-ttu-id="d530d-203">設定されていないフィールドがいくつかあることがわかります。これを変更してみましょう。</span><span class="sxs-lookup"><span data-stu-id="d530d-203">You will see that there are several unpopulated fields, let's change that.</span></span> <span data-ttu-id="d530d-204">**DataManager** オブジェクトを [階層] から *[データ マネージャー]* フィールドに移動し、**RootMenu** GameObject を [階層] から *[メイン メニュー]* フィールドに移動します。</span><span class="sxs-lookup"><span data-stu-id="d530d-204">Move the **DataManager** object from the Hierarchy into the *Data Manager* field and move the **RootMenu** GameObject from the Hierarchy into the *Main Menu* field.</span></span>

![SceneController が構成された Unity](images/mr-learning-azure/tutorial1-section6-step1-5.png)

<span data-ttu-id="d530d-206">これで、今後のチュートリアルのためにシーンの準備ができました。</span><span class="sxs-lookup"><span data-stu-id="d530d-206">Now your scene is ready for the upcoming tutorials.</span></span> <span data-ttu-id="d530d-207">これは必ずプロジェクトに保存してください。</span><span class="sxs-lookup"><span data-stu-id="d530d-207">Don't forget to save it into your project.</span></span>

## <a name="prepare-project-build-pipeline"></a><span data-ttu-id="d530d-208">プロジェクト ビルド パイプラインを準備する</span><span class="sxs-lookup"><span data-stu-id="d530d-208">Prepare project build pipeline</span></span>

<span data-ttu-id="d530d-209">プロジェクトにはまだコンテンツが入力されていませんが、いくつかの準備を行い、プロジェクトを **HoloLens 2** 用にビルドできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d530d-209">While the project yet has to be filled with content, you have to perform some preparations, so the project is ready for building for **HoloLens 2**.</span></span>

### <a name="1-add-additional-required-capabilities"></a><span data-ttu-id="d530d-210">1.必要な機能をさらに追加する</span><span class="sxs-lookup"><span data-stu-id="d530d-210">1. Add additional required capabilities</span></span>

<span data-ttu-id="d530d-211">Unity メニューで、 **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクト設定...\)** を選択し、[Project Settings]\(プロジェクト設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="d530d-211">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![[Project Settings]\(プロジェクト設定\) が開かれている Unity](images/mr-learning-azure/tutorial1-section7-step1-1.png)

<span data-ttu-id="d530d-213">[Project Settings]\(プロジェクトの設定\) ウィンドウで、 **[Player]\(プレーヤー\)** **[Publishing Settings]\(公開の設定\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="d530d-213">In the Project Settings window, select **Player** and then **Publishing Settings**:</span></span>

![Unity の [Publishing Settings]\(公開の設定\)](images/mr-learning-azure/tutorial1-section7-step1-2.png)

<span data-ttu-id="d530d-215">**[Publishing Settings]\(公開の設定\)** で、 **[Capabilities]\(機能\)** セクションまで下にスクロールし、チュートリアルの最初にプロジェクトを作成したときに有効にした **InternetClient**、**Microphone** および **SpatialPerception** の機能が有効になっていることを再確認します。</span><span class="sxs-lookup"><span data-stu-id="d530d-215">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone** and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="d530d-216">その後、**InternetClientServer**、**PrivateNetworkClientServer**、および **Webcam** の機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="d530d-216">Then, enable the **InternetClientServer**, **PrivateNetworkClientServer**, and **Webcam** capabilities:</span></span>

![Unity の機能](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="d530d-218">2.HoloLens 2 にアプリをデプロイする</span><span class="sxs-lookup"><span data-stu-id="d530d-218">2. Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="d530d-219">このチュートリアル シリーズで使用するすべての機能が、Unity エディター内で実行できるわけではありません。つまり、アプリケーションを HoloLens 2 デバイスにデプロイする方法についてよく理解しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="d530d-219">Not all features that you will use in this tutorial series can run inside the Unity editor, this means that you need to be familiar with deploying the application to your HoloLens 2 device.</span></span>

> [!TIP]
> <span data-ttu-id="d530d-220">HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、「[入門チュートリアル」のデバイスへのアプリケーションのビルド](mr-learning-base-02.md#building-your-application-to-your-hololens-2)に関するセクションの手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d530d-220">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Getting started tutorials - Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="d530d-221">3.HoloLens 2 でアプリを実行し、アプリ内の指示に従う</span><span class="sxs-lookup"><span data-stu-id="d530d-221">3. Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

> [!CAUTION]
> <span data-ttu-id="d530d-222">すべての Azure Services でインターネットが使用されるため、デバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d530d-222">All Azure Services uses the internet, so make sure your device is connected to the internet.</span></span>

<span data-ttu-id="d530d-223">アプリケーションがデバイスで実行されている場合は、次の要求された機能へのアクセスを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="d530d-223">When the application is running on your device, accept access to the following requested capabilities:</span></span>

* <span data-ttu-id="d530d-224">マイク</span><span class="sxs-lookup"><span data-stu-id="d530d-224">Microphone</span></span>
* <span data-ttu-id="d530d-225">カメラ</span><span class="sxs-lookup"><span data-stu-id="d530d-225">Camera</span></span>

<span data-ttu-id="d530d-226">これらの機能は、"*チャット ボット*" や *Custom Vision* などのサービスを正しく機能させるために必要です。</span><span class="sxs-lookup"><span data-stu-id="d530d-226">These capabilities are required for services like *Chat Bot* and *Custom Vision* to function properly.</span></span>

## <a name="congratulations"></a><span data-ttu-id="d530d-227">結論</span><span class="sxs-lookup"><span data-stu-id="d530d-227">Congratulations</span></span>

<span data-ttu-id="d530d-228">このチュートリアルでは、チュートリアル シリーズの概要を確認し、実装する機能についてと、*HoloLens 2* アプリケーションの実行と **Azure クラウド** サービスがどのように結び付いているかについて学習しました。</span><span class="sxs-lookup"><span data-stu-id="d530d-228">In this tutorial, you were introduced to the tutorial series, learned about the features you will implement and how **Azure Cloud** services tie in to making your *HoloLens 2* application happen.</span></span> <span data-ttu-id="d530d-229">必要なコンポーネントをプロジェクトに追加し、このチュートリアル シリーズのためにシーンを準備しました。</span><span class="sxs-lookup"><span data-stu-id="d530d-229">You added the required components into the project and prepared the scene for this tutorial series.</span></span>

<span data-ttu-id="d530d-230">次のレッスンでは、データと画像を格納するためのクラウド ベースの永続化ソリューションとして、Azure Storage を使用します。</span><span class="sxs-lookup"><span data-stu-id="d530d-230">In the next lesson, you will use Azure storage as a cloud based persistence solution for storing data and images.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d530d-231">次のチュートリアル: 2.Azure Storage の統合</span><span class="sxs-lookup"><span data-stu-id="d530d-231">Next tutorial: 2. Integrating Azure storage</span></span>](mr-learning-azure-02.md)
