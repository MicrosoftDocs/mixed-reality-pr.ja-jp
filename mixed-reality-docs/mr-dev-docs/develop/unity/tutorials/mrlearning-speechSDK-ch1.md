---
title: 音声認識と文字起こしの統合と使用
description: このコースを完了すると、Mixed Reality アプリケーションで Azure の音声認識と文字起こしを追加して使用する方法がわかります。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー, 音声認識, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: f0c26c861cb3400c552d17d45f77cfe3a5cc284c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010122"
---
# <a name="1-integrating-and-using-speech-recognition-and-transcription"></a><span data-ttu-id="6b6a1-104">1.音声認識と文字起こしの統合と使用</span><span class="sxs-lookup"><span data-stu-id="6b6a1-104">1. Integrating and using speech recognition and transcription</span></span>

<span data-ttu-id="6b6a1-105">このチュートリアル シリーズでは、HoloLens 2 での Azure Speech Services の使用を探索する Mixed Reality アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-105">In this tutorial series, you will create a Mixed Reality application that explores the use of Azure Speech Services with the HoloLens 2.</span></span> <span data-ttu-id="6b6a1-106">このチュートリアル シリーズを完了すると、デバイスのマイクを使用して、リアルタイムで音声を文字に起こしたり、音声を他の言語に翻訳したり、意図認識機能を利用して、人工知能を使って音声コマンドを理解したりできるようになります。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-106">When you complete this tutorial series, you will be able to use your device's microphone to transcribe speech to text in real time, translate your speech into other languages, and leverage the Intent recognition feature to understand voice commands using artificial intelligence.</span></span>

## <a name="objectives"></a><span data-ttu-id="6b6a1-107">目標</span><span class="sxs-lookup"><span data-stu-id="6b6a1-107">Objectives</span></span>

* <span data-ttu-id="6b6a1-108">Azure Speech Services と HoloLens 2 アプリケーションを統合する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="6b6a1-108">Learn how to integrate Azure Speech Services with a HoloLens 2 application</span></span>
* <span data-ttu-id="6b6a1-109">音声認識を使用して文字に起こす方法を学習する</span><span class="sxs-lookup"><span data-stu-id="6b6a1-109">Learn how to use speech recognition to transcribe text</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6b6a1-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="6b6a1-110">Prerequisites</span></span>

>[!TIP]
><span data-ttu-id="6b6a1-111">[入門チュートリアル](mr-learning-base-01.md) シリーズをまだ完了していない場合は、まずこれらのチュートリアルを完了することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-111">If you have not completed the [Getting started tutorials](mr-learning-base-01.md) series yet, it's recommended that you complete those tutorials first.</span></span>

* <span data-ttu-id="6b6a1-112">正しい[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="6b6a1-112">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="6b6a1-113">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="6b6a1-113">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="6b6a1-114">基本的な C# プログラミング能力</span><span class="sxs-lookup"><span data-stu-id="6b6a1-114">Some basic C# programming ability</span></span>
* <span data-ttu-id="6b6a1-115">[開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="6b6a1-115">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="6b6a1-116">Unity 2019 LTS がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="6b6a1-116"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b6a1-117">このチュートリアル シリーズで推奨されている Unity バージョンは、Unity 2019 LTS です。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-117">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="6b6a1-118">これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-118">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="6b6a1-119">Unity プロジェクトの作成と準備</span><span class="sxs-lookup"><span data-stu-id="6b6a1-119">Creating and preparing the Unity project</span></span>

<span data-ttu-id="6b6a1-120">このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備します。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-120">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="6b6a1-121">このためには、まず「[プロジェクトと最初のアプリケーションの初期化](mr-learning-base-02.md)」に従ってください (「[デバイスへのアプリケーションのビルド](mr-learning-base-02.md#building-and-deploying-to-your-hololens-2)」の手順は除く)。これには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-121">For this, first follow the [Initializing your project and first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-and-deploying-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="6b6a1-122">[Unity プロジェクトを作成](mr-learning-base-02.md#creating-the-unity-project)し、"*MRTK チュートリアル*" などの適切な名前を付ける</span><span class="sxs-lookup"><span data-stu-id="6b6a1-122">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="6b6a1-123">ビルド プラットフォームを切り替える</span><span class="sxs-lookup"><span data-stu-id="6b6a1-123">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="6b6a1-124">TextMeshPro の重要なリソースをインポートする</span><span class="sxs-lookup"><span data-stu-id="6b6a1-124">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="6b6a1-125">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="6b6a1-125">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="6b6a1-126">Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="6b6a1-126">Configuring the Unity project</span></span>](mr-learning-base-02.md#selecting-mrtk-and-project-settings)
6. <span data-ttu-id="6b6a1-127">[シーンを作成して構成](mr-learning-base-02.md#creating-and-configuring-the-scene)し、シーンに *AzureSpeechServices* などの適切な名前を付ける</span><span class="sxs-lookup"><span data-stu-id="6b6a1-127">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpeechServices*</span></span>

<span data-ttu-id="6b6a1-128">その後、「[空間認識表示オプションの変更](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)」の手順に従って、シーンの MRTK 構成プロファイルを **[DefaultHoloLens2ConfigurationProfile]** に変更し、空間認識メッシュの表示オプションを **[Occlusion]\(オクルージョン\)** に変更します。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-128">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to change the MRTK configuration profile for your scene to the **DefaultHoloLens2ConfigurationProfile** and change the display options for the spatial awareness mesh to **Occlusion**.</span></span>

## <a name="configuring-the-speech-commands-start-behavior"></a><span data-ttu-id="6b6a1-129">音声コマンドの開始動作の構成</span><span class="sxs-lookup"><span data-stu-id="6b6a1-129">Configuring the speech commands start behavior</span></span>

<span data-ttu-id="6b6a1-130">音声認識と文字起こしには Speech SDK を使用するため、Speech SDK の機能の妨げにならないように、MRTK の音声コマンドを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-130">Because you will use the Speech SDK for speech recognition and transcription you need to configure the MRTK Speech Commands so they do not interfere with the Speech SDK functionality.</span></span> <span data-ttu-id="6b6a1-131">これを実現するには、音声コマンドの開始動作を [Auto Start]\(自動開始\) から [Manual Start]\(手動開始\) に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-131">To achieve this you can change the speech commands start behavior from Auto Start to Manual Start.</span></span>

<span data-ttu-id="6b6a1-132">[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **[Input]\(入力\)** タブを選択し、**DefaultHoloLens2InputSystemProfile** と **DefaultMixedRealitySpeechCommandsProfile** を複製し、音声コマンドの **[Start Behavior]\(開始動作\)** を **[Manual Start]\(手動開始\)** に変更します。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-132">With the **MixedRealityToolkit** object selected in the Hierarchy window, in the Inspector window, select the **Input** tab, clone the **DefaultHoloLens2InputSystemProfile** and the **DefaultMixedRealitySpeechCommandsProfile**, and then change the speech commands **Start Behavior** to **Manual Start**:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="6b6a1-134">MRTK プロファイルを複製し、構成する方法については、[Mixed Reality ツールキット プロファイルの構成](mr-learning-base-03.md)に関するページにある手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-134">For a reminder on how to clone and configure MRTK profiles, you can refer to the [Configuring the Mixed Reality Toolkit profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="configuring-the-capabilities"></a><span data-ttu-id="6b6a1-135">機能の構成</span><span class="sxs-lookup"><span data-stu-id="6b6a1-135">Configuring the capabilities</span></span>

<span data-ttu-id="6b6a1-136">Unity メニューで **[Edit]\(編集\)**  >  **[Project Settings]\(プロジェクトの設定\)** を選択して、[Player Settings]\(プレーヤーの設定\) ウィンドウを開きます。次に、 **[Player]\(プレーヤー\)**  >   **[Publishing Settings]\(発行の設定\)** セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-136">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-1.png)

<span data-ttu-id="6b6a1-138">**[Publishing Settings]\(発行の設定\)** で、下にスクロールして **[Capabilities]\(機能\)** セクションまで移動し、チュートリアルの開始時にプロジェクトを作成したときに有効にした **InternetClient**、**Microphone**、および **SpatialPerception** の機能が有効になっていることを再確認します。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-138">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, and **SpatialPerception** capabilities, which you enabled when you created the project at the beginning of the tutorial, are enabled.</span></span> <span data-ttu-id="6b6a1-139">次に、**InternetClientServer** と **PrivateNetworkClientServer** の機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-139">Then, enable the **InternetClientServer** and **PrivateNetworkClientServer** capabilities:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="6b6a1-141">チュートリアルのアセットのインポート</span><span class="sxs-lookup"><span data-stu-id="6b6a1-141">Importing the tutorial assets</span></span>

<span data-ttu-id="6b6a1-142">次の Unity カスタム パッケージを、**一覧に表示されている順序で** ダウンロードして **インポート** します。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-142">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="6b6a1-143">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (最新バージョン)</span><span class="sxs-lookup"><span data-stu-id="6b6a1-143">[Microsoft.CognitiveServices.Speech.N.N.N.unitypackage](https://aka.ms/csspeech/unitypackage) (latest version)</span></span>
* [<span data-ttu-id="6b6a1-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span><span class="sxs-lookup"><span data-stu-id="6b6a1-144">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.3.0.3/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.3.0.3.unitypackage)
* [<span data-ttu-id="6b6a1-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="6b6a1-145">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-speech-services-v2.3.0.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpeechServices.2.3.0.0.unitypackage)

> [!TIP]
> <span data-ttu-id="6b6a1-146">Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-146">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

<span data-ttu-id="6b6a1-147">チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-147">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section4-step1-1.png)

## <a name="preparing-the-scene"></a><span data-ttu-id="6b6a1-149">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="6b6a1-149">Preparing the scene</span></span>

<span data-ttu-id="6b6a1-150">このセクションでは、チュートリアルのプレハブを追加してシーンを準備し、シーンを制御するように Lunarcom Controller (Script) コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-150">In this section, you will prepare the scene by adding the tutorial prefab and configure the Lunarcom Controller (Script) component to control your scene.</span></span>

<span data-ttu-id="6b6a1-151">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.AzureSpeechServices]**  >  **[Prefabs]** フォルダーに移動し、 **[Lunarcom]** プレハブを [Hierarchy]\(階層\) ウィンドウにドラッグしてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-151">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureSpeechServices** > **Prefabs** folder and drag the **Lunarcom** prefab into the Hierarchy window to add it to your scene:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-1.png)

<span data-ttu-id="6b6a1-153">[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Lunarcom Controller (Script)** コンポーネントを Lunarcom オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-153">With the **Lunarcom** object still selected in the Hierarchy window, in the Inspector window, use the **Add Component** button to add the **Lunarcom Controller (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-2.png)

> [!NOTE]
> <span data-ttu-id="6b6a1-155">Lunarcom Controller (Script) コンポーネントは MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-155">The Lunarcom Controller (Script) component is not part of MRTK.</span></span> <span data-ttu-id="6b6a1-156">このチュートリアルのアセットと共に提供されました。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-156">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="6b6a1-157">**[Lunarcom]** オブジェクトを選択した状態で、それを展開して子オブジェクトを表示し、次に **Terminal** オブジェクトを Lunarcom Controller (Script) コンポーネントの **[Terminal]\(ターミナル\)** フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-157">With the **Lunarcom** object still selected, expand it to reveal its child objects, then drag the **Terminal** object into the Lunarcom Controller (Script) component's **Terminal** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-3.png)

<span data-ttu-id="6b6a1-159">**Lunarcom** オブジェクトを選択した状態で、Terminal オブジェクトを展開して子オブジェクトを表示し、**ConnectionLight** オブジェクトを Lunarcom Controller (Script) コンポーネントの **[Connection Light]\(接続ライト\)** フィールドに、**OutputText** オブジェクトを **[Output Text]\(出力テキスト\)** フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-159">With the **Lunarcom** object still selected, expand the Terminal object to reveal its child objects, then drag the **ConnectionLight** object into the Lunarcom Controller (Script) component's **Connection Light** field and the **OutputText** object into the **Output Text** field:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-4.png)

<span data-ttu-id="6b6a1-161">**Lunarcom** オブジェクトを選択した状態で、Buttons オブジェクトを展開して子オブジェクトを表示し、次に [Inspector]\(インスペクター\) ウィンドウで **[Buttons]\(ボタン\)** リストを展開し、その **[Size]\(サイズ\)** を 3 に設定し、**MicButton**、**SatelliteButton**、および **RocketButton** の各オブジェクトを **[Element]\(要素\)** 0、1、2 のフィールドにそれぞれドラッグします。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-161">With the **Lunarcom** object still selected, expand the Buttons object to reveal its child objects, and then in the Inspector window, expand the **Buttons** list, set its **Size** to 3, and drag the **MicButton**, **SatelliteButton**, and **RocketButton** objects into the **Element** 0, 1, and 2 fields respectively:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section5-step1-5.png)

## <a name="connecting-the-unity-project-to-the-azure-resource"></a><span data-ttu-id="6b6a1-163">Unity プロジェクトを Azure リソースに接続</span><span class="sxs-lookup"><span data-stu-id="6b6a1-163">Connecting the Unity project to the Azure resource</span></span>

<span data-ttu-id="6b6a1-164">Azure Speech Services を使用するには、Azure リソースを作成し、Speech Service 用の API キーを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-164">To use Azure Speech Services, you need to create an Azure resource and obtain an API key for the Speech Service.</span></span> <span data-ttu-id="6b6a1-165">「[Speech Service を無料で試す](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started)」の手順に従って、ご利用のサービス リージョン (ロケーションとも呼ばれる) と API キー (Key1 または Key2 とも呼ばれる) をメモします。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-165">Follow the [Try the Speech service for free](https://docs.microsoft.com/azure/cognitive-services/speech-service/get-started) instructions and make a note of your service region (also known as Location) and API key (also known as Key1 or Key2).</span></span>

<span data-ttu-id="6b6a1-166">[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択し、次に [Inspector]\(インスペクター\) ウィンドウで **Lunarcom Controller (Script)** コンポーネントの **[Speech SDK Credentials]\(Speech SDK 資格情報\)** セクションを見つけ、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-166">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, locate the **Lunarcom Controller (Script)** component's **Speech SDK Credentials** section and configure it as follows:</span></span>

* <span data-ttu-id="6b6a1-167">**[Speech Service API Key]\(Speech Service の API キー\)** フィールドに、API キー (Key1 または Key2) を入力します</span><span class="sxs-lookup"><span data-stu-id="6b6a1-167">In the **Speech Service API Key** field, enter your API key (Key1 or Key2)</span></span>
* <span data-ttu-id="6b6a1-168">**[Speech Service Region]\(Speech Service のリージョン\)** フィールドに、小文字を使用し、スペースを削除して、サービス リージョン (ロケーション) を入力します</span><span class="sxs-lookup"><span data-stu-id="6b6a1-168">In the **Speech Service Region** field, enter your service region (Location) using lowercase letters and spaces removed</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section6-step1-1.png)

## <a name="using-speech-recognition-to-transcribe-speech"></a><span data-ttu-id="6b6a1-170">音声認識を使用して音声を文字に起こす</span><span class="sxs-lookup"><span data-stu-id="6b6a1-170">Using speech recognition to transcribe speech</span></span>

<span data-ttu-id="6b6a1-171">[Hierarchy]\(階層\) ウィンドウで **Lunarcom** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、**Lunarcom Speech Recognizer (Script)** コンポーネントを Lunarcom オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-171">In the Hierarchy window, select the **Lunarcom** object, then in the Inspector window, use the **Add Component** button to add the **Lunarcom Speech Recognizer (Script)** component to the Lunarcom object:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-1.png)

> [!NOTE]
> <span data-ttu-id="6b6a1-173">Lunarcom Speech Recognizer (Script) コンポーネントは MRTK の一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-173">The Lunarcom Speech Recognizer (Script) component is not part of MRTK.</span></span> <span data-ttu-id="6b6a1-174">このチュートリアルのアセットと共に提供されました。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-174">It was provided with this tutorial's assets.</span></span>

<span data-ttu-id="6b6a1-175">ゲーム モードに入ったら、まずマイクのボタンを押して音声認識をテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-175">If you now enter Game mode, you can test the speech recognition by first pressing the microphone button:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-2.png)

<span data-ttu-id="6b6a1-177">次に、お使いのコンピューターにマイクがあると仮定して、何か話すと、音声がターミナルのパネル上に文字で表示されます。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-177">Then, assuming your computer has a microphone, when you say something, your speech will be transcribed on the terminal panel:</span></span>

![mrlearning-speech](images/mrlearning-speech/tutorial1-section7-step1-3.png)


> [!CAUTION]
> <span data-ttu-id="6b6a1-179">アプリケーションは Azure に接続する必要があるため、お使いのコンピューター/デバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-179">The application needs to connect to Azure, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6b6a1-180">結論</span><span class="sxs-lookup"><span data-stu-id="6b6a1-180">Congratulations</span></span>

<span data-ttu-id="6b6a1-181">Azure で提供される音声認識を実装しました。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-181">You have implemented speech recognition powered by Azure.</span></span> <span data-ttu-id="6b6a1-182">デバイスでアプリケーションを実行して、機能が正常に動作していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-182">Run the application on your device to ensure the feature is working properly.</span></span>

<span data-ttu-id="6b6a1-183">次のチュートリアルでは、Azure 音声認識を使用してコマンドを実行する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="6b6a1-183">In the next tutorial, you will learn how to execute commands using Azure speech recognition.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6b6a1-184">次のチュートリアル: 2.音声認識を使用したコマンドの実行</span><span class="sxs-lookup"><span data-stu-id="6b6a1-184">Next tutorial: 2. Using speech recognition to execute commands</span></span>](mrlearning-speechSDK-ch2.md)
