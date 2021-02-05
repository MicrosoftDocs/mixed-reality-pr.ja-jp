---
title: 空間オーディオのチュートリアル-1. プロジェクトへの空間オーディオの追加
description: Microsoft Spatializer プラグインを Unity プロジェクトに追加して、HoloLens 2 HRTF ハードウェアオフロードにアクセスします。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、head 関連の転送機能、リバーブ、Microsoft Spatializer
ms.openlocfilehash: 7ed1355e3c522fcd94a96dd761a8a9ebb01c4c4c
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590044"
---
# <a name="1-adding-spatial-audio-to-your-unity-project"></a><span data-ttu-id="82b9b-105">1. Unity プロジェクトに空間オーディオを追加する</span><span class="sxs-lookup"><span data-stu-id="82b9b-105">1. Adding Spatial audio to your Unity project</span></span>

## <a name="overview"></a><span data-ttu-id="82b9b-106">概要</span><span class="sxs-lookup"><span data-stu-id="82b9b-106">Overview</span></span>

<span data-ttu-id="82b9b-107">HoloLens2 上の Unity の空間オーディオチュートリアルへようこそ。</span><span class="sxs-lookup"><span data-stu-id="82b9b-107">Welcome to the spatial audio tutorial for Unity on HoloLens2.</span></span> <span data-ttu-id="82b9b-108">このチュートリアルシリーズでは、HoloLens 2 でヘッド関連の転送関数 (HRTF) オフロードを使用する方法と、HRTF オフロードを使用するときにリバーブを有効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="82b9b-108">Through this tutorial series, you will learn how to use head-related transfer function (HRTF) offload on HoloLens 2 and How to enable reverb when using HRTF offload.</span></span>

<span data-ttu-id="82b9b-109">[Microsoft Spatializer GitHub リポジトリ](https://github.com/microsoft/spatialaudio-unity)には、このチュートリアルシーケンスの完成した Unity プロジェクトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="82b9b-109">The [Microsoft Spatializer GitHub repository](https://github.com/microsoft/spatialaudio-unity) has a completed Unity project of this tutorial sequence.</span></span>

<span data-ttu-id="82b9b-110">HRTF ベースの spatialization テクノロジを使用してサウンドを spatialize することの意味と、役に立つ可能性がある場合の推奨事項については、「 [空間サウンドの設計](/windows/mixed-reality/spatial-sound-design)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82b9b-110">For an understanding of what it means to spatialize sounds using HRTF-based spatialization technologies and recommendations for when it can be helpful, see [spatial sound design](/windows/mixed-reality/spatial-sound-design).</span></span>

## <a name="what-is-hrtf-offload"></a><span data-ttu-id="82b9b-111">HRTF offload とは</span><span class="sxs-lookup"><span data-stu-id="82b9b-111">What is HRTF offload?</span></span>

<span data-ttu-id="82b9b-112">HRTF ベースのアルゴリズムを使用してオーディオを処理するには、大量の特殊な計算が必要です。</span><span class="sxs-lookup"><span data-stu-id="82b9b-112">Processing audio using HRTF-based algorithms requires a large amount of specialized computation.</span></span> <span data-ttu-id="82b9b-113">HoloLens 2 には、アプリケーションプロセッサに負荷がかからないようにするために使用できる専用のハードウェアが含まれているため、HRTF ベースのアルゴリズムの処理を "オフロード" します。</span><span class="sxs-lookup"><span data-stu-id="82b9b-113">HoloLens 2 includes dedicated hardware that can be utilized to avoid burdening the application processor, thus "offloading" the processing of HRTF-based algorithms.</span></span>  <span data-ttu-id="82b9b-114">Microsoft spatializer プラグインを使用すると、アプリケーションで専用の HRTF ハードウェアを利用して、空間オーディオ以外の操作でアプリケーションプロセッサをより多く使用できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="82b9b-114">The Microsoft spatializer plugin provides an easy way for your application to take advantage of the dedicated HRTF hardware so your application can use more of the application processor for operations other than spatial audio.</span></span>

## <a name="objectives"></a><span data-ttu-id="82b9b-115">目標</span><span class="sxs-lookup"><span data-stu-id="82b9b-115">Objectives</span></span>

* <span data-ttu-id="82b9b-116">Microsoft spatializer プラグインのインポートと有効化</span><span class="sxs-lookup"><span data-stu-id="82b9b-116">Importing and Enabling Microsoft spatializer plugin</span></span>
* <span data-ttu-id="82b9b-117">開発者ワークステーションでの空間オーディオの有効化</span><span class="sxs-lookup"><span data-stu-id="82b9b-117">Enabling Spatial audio on your developer workstation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="82b9b-118">前提条件</span><span class="sxs-lookup"><span data-stu-id="82b9b-118">Prerequisites</span></span>

* <span data-ttu-id="82b9b-119">正しい[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="82b9b-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="82b9b-120">C# プログラミングの基本知識</span><span class="sxs-lookup"><span data-stu-id="82b9b-120">Basic c# programming knowledge</span></span>
* <span data-ttu-id="82b9b-121">[開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="82b9b-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="82b9b-122">Unity 2019 LTS がマウントされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="82b9b-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS mounted, and the Universal Windows Platform Build Support module added</span></span>

<span data-ttu-id="82b9b-123">作業を続行する前に、[概要](mr-learning-base-01.md)チュートリアルシリーズを完了するか、Unity と MRTK の基本的な経験があることを **強くお勧め** します。</span><span class="sxs-lookup"><span data-stu-id="82b9b-123">We **strongly recommend** completing the [Getting started](mr-learning-base-01.md) tutorials series or having some basic prior experience with Unity and MRTK before continuing.</span></span>

> [!IMPORTANT]
>
> * <span data-ttu-id="82b9b-124">このチュートリアル シリーズで推奨されている Unity バージョンは、Unity 2019 LTS です。</span><span class="sxs-lookup"><span data-stu-id="82b9b-124">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="82b9b-125">これは、上でリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="82b9b-125">It supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="82b9b-126">Unity プロジェクトの作成と準備</span><span class="sxs-lookup"><span data-stu-id="82b9b-126">Creating and preparing the Unity project</span></span>

<span data-ttu-id="82b9b-127">このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備をします。</span><span class="sxs-lookup"><span data-stu-id="82b9b-127">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="82b9b-128">このためには、まず「[プロジェクトと最初のアプリケーションの初期化](mr-learning-base-02.md)」に従ってください (「[デバイスへのアプリケーションのビルド](mr-learning-base-02.md#building-your-application-to-your-hololens-2)」の手順は除く)。これには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="82b9b-128">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="82b9b-129">[Unity プロジェクトを作成](mr-learning-base-02.md#creating-the-unity-project)し、"*MRTK チュートリアル*" などの適切な名前を付ける</span><span class="sxs-lookup"><span data-stu-id="82b9b-129">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>

1. [<span data-ttu-id="82b9b-130">ビルド プラットフォームを切り替える</span><span class="sxs-lookup"><span data-stu-id="82b9b-130">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. [<span data-ttu-id="82b9b-131">TextMeshPro の重要なリソースをインポートする</span><span class="sxs-lookup"><span data-stu-id="82b9b-131">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)

1. [<span data-ttu-id="82b9b-132">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="82b9b-132">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)

1. [<span data-ttu-id="82b9b-133">Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="82b9b-133">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)

1. <span data-ttu-id="82b9b-134">[シーンを作成および設定](mr-learning-base-02.md#creating-and-configuring-the-scene)し、シーンに適切な名前を付けます (たとえば、 *SpatialAudio* )。</span><span class="sxs-lookup"><span data-stu-id="82b9b-134">[Creating and setting the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *SpatialAudio*</span></span>

<span data-ttu-id="82b9b-135">次に、「 [空間認識表示オプションの変更」](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) の手順に従って、シーンの MRTK 構成プロファイルが **DefaultHoloLens2ConfigurationProfile** になっていることを確認し、空間認識メッシュの表示オプションを **オクルージョン** に変更します。</span><span class="sxs-lookup"><span data-stu-id="82b9b-135">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to ensure the MRTK configuration profile for your scene is **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="adding-microsoft-spatializer-to-the-project"></a><span data-ttu-id="82b9b-136">プロジェクトへの Microsoft Spatializer の追加</span><span class="sxs-lookup"><span data-stu-id="82b9b-136">Adding Microsoft Spatializer to the Project</span></span>

<span data-ttu-id="82b9b-137">Microsoft Spatializer <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">SpatialAudio. Spatializer</a>をダウンロードしてインポートします。</span><span class="sxs-lookup"><span data-stu-id="82b9b-137">Download and import the Microsoft Spatializer  <a href="https://github.com/microsoft/spatialaudio-unity/releases/download/v1.0.18/Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage" target="_blank">Microsoft.SpatialAudio.Spatializer.Unity.1.0.18.unitypackage </a></span></span>

>[!TIP]
> <span data-ttu-id="82b9b-138">Unity カスタムパッケージをインポートする方法の詳細については、 [チュートリアル資産のインポート](mr-learning-base-04.md#importing-the-tutorial-assets) に関する手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82b9b-138">For a reminder on how to import a Unity custom package, you can refer to the [Importing the tutorial assets](mr-learning-base-04.md#importing-the-tutorial-assets) instructions.</span></span>

## <a name="enable-the-microsoft-spatializer-plugin"></a><span data-ttu-id="82b9b-139">Microsoft Spatializer プラグインを有効にする</span><span class="sxs-lookup"><span data-stu-id="82b9b-139">Enable the Microsoft Spatializer plugin</span></span>

<span data-ttu-id="82b9b-140">**Microsoft Spatializer** をインポートしたら、有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="82b9b-140">After importing the **Microsoft Spatializer** you need to enable it.</span></span> <span data-ttu-id="82b9b-141">[ **編集-> プロジェクトの設定-> オーディオ**] を開き、 **Spatializer プラグイン** を "Microsoft Spatializer" に変更します。</span><span class="sxs-lookup"><span data-stu-id="82b9b-141">Open **Edit -> Project Settings -> Audio**, and change **Spatializer Plugin** to "Microsoft Spatializer".</span></span>

![Spatializer プラグインを表示するプロジェクト設定](images/spatial-audio/spatial-audio-01-section3-step1-1.png)

## <a name="enable-spatial-audio-on-your-workstation"></a><span data-ttu-id="82b9b-143">ワークステーションで空間オーディオを有効にする</span><span class="sxs-lookup"><span data-stu-id="82b9b-143">Enable spatial audio on your workstation</span></span>

<span data-ttu-id="82b9b-144">Windows のデスクトップバージョンでは、空間オーディオは既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="82b9b-144">On desktop versions of Windows, spatial audio is disabled by default.</span></span> <span data-ttu-id="82b9b-145">これを有効にするには、タスクバーのボリュームアイコンを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="82b9b-145">Enable it by right-clicking on the volume icon in the task bar.</span></span> <span data-ttu-id="82b9b-146">HoloLens 2 で耳になる内容を最大限に活用するには、[ **空間サウンド > Windows Sonic For ヘッドホン**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="82b9b-146">To get the best representation of what you'll hear on HoloLens 2, choose **Spatial sound -> Windows Sonic for Headphones**.</span></span>

![デスクトップ空間オーディオの設定](images/spatial-audio/spatial-audio-01-section4-step1-1.png)

> [!NOTE]
> <span data-ttu-id="82b9b-148">この設定は、Unity エディターでプロジェクトをテストする場合にのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="82b9b-148">This setting is only required if you plan to test your project in the Unity editor.</span></span>

## <a name="congratulations"></a><span data-ttu-id="82b9b-149">結論</span><span class="sxs-lookup"><span data-stu-id="82b9b-149">Congratulations</span></span>

<span data-ttu-id="82b9b-150">このチュートリアルでは、Microsoft Spatializer プラグインをインポートして有効にする方法と、ワークステーションで空間オーディオを有効にする方法について説明しました。</span><span class="sxs-lookup"><span data-stu-id="82b9b-150">In this tutorial you have learnt how to Import and enable the Microsoft Spatializer plugin and also to enable the spatial audio on your workstation.</span></span>
<span data-ttu-id="82b9b-151">次のチュートリアルでは、unity プロジェクトに空間オーディオを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="82b9b-151">In the next tutorial you will learn how to add spatial audio in the unity project.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="82b9b-152">次のチュートリアル: 2. Spatializing ボタンの相互作用サウンド</span><span class="sxs-lookup"><span data-stu-id="82b9b-152">Next Tutorial: 2. Spatializing button interaction sounds</span></span>](unity-spatial-audio-ch2.md)
