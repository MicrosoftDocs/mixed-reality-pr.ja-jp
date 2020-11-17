---
title: PC Holographic Remoting のチュートリアル - 2. Holographic Remoting PC アプリケーションを作成する
description: このコースを完了すると、PC アプリケーションを作成して Mixed Reality エクスペリエンスを PC から HoloLens 2 にリモート処理する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 30ef793511285fe2fe52810912f6c5c06c8550dc
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353460"
---
# <a name="2-creating-a-holographic-remoting-pc-application"></a><span data-ttu-id="162b8-105">2.Holographic Remoting PC アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="162b8-105">2. Creating a Holographic Remoting PC application</span></span>

<span data-ttu-id="162b8-106">このチュートリアルでは、Holographic Remoting 用の PC アプリを作成して、いつでも HoloLens 2 に接続できるようにし、Mixed Reality で 3D コンテンツを視覚化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="162b8-106">In this tutorial, you will learn how to create a PC app for Holographic Remoting and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span>

## <a name="objectives"></a><span data-ttu-id="162b8-107">目標</span><span class="sxs-lookup"><span data-stu-id="162b8-107">Objectives</span></span>

* <span data-ttu-id="162b8-108">Holographic Remoting 用に Unity を構成する</span><span class="sxs-lookup"><span data-stu-id="162b8-108">Configure Unity for Holographic Remoting</span></span>
* <span data-ttu-id="162b8-109">Visual Studio でアプリケーションをビルドして展開する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="162b8-109">Learn how to build and deploy the application with Visual Studio</span></span>
* <span data-ttu-id="162b8-110">Holographic Remoting アプリケーションを開発し、HoloLens に接続する</span><span class="sxs-lookup"><span data-stu-id="162b8-110">Developing Holographic Remoting application and connecting to HoloLens</span></span>

## <a name="configuring-your-scene-for-holographic-remoting"></a><span data-ttu-id="162b8-111">Holographic Remoting 用のシーンの構成</span><span class="sxs-lookup"><span data-stu-id="162b8-111">Configuring your scene for Holographic Remoting</span></span>

<span data-ttu-id="162b8-112">このセクションでは、Wi-Fi 接続を使用して、PC から HoloLens 2 デバイスに Mixed Reality エクスペリエンスをリアルタイムにストリーミングできるようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="162b8-112">In this section, you will configure your project to stream your Mixed Reality experience to your HoloLens 2 device from your PC in real-time over a Wi-Fi connection.</span></span>

<span data-ttu-id="162b8-113">[プロジェクト] ウィンドウで、 **[アセット]**  >  **[MRTK.Tutorials.PCHolograhicRemoting]**  >  **[Prefabs]\(プレハブ\)** フォルダーの順に移動します。次に、**HolographicRemoting** プレハブをクリックしてシーンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="162b8-113">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.PCHolograhicRemoting** > **Prefabs** folder, and click and drag **HolographicRemoting** prefab into your scene.</span></span>

![新しく追加された HolographicRemoting プレハブがまだ選択されている Unity](images/mrlearning-pc-holographic-remoting/Tutorial2-Section1-Step1-1.png)

## <a name="build-your-application-to-pc"></a><span data-ttu-id="162b8-115">アプリケーションを PC にビルドする</span><span class="sxs-lookup"><span data-stu-id="162b8-115">Build your application to PC</span></span>

<span data-ttu-id="162b8-116">これで、Holographic Remoting アプリを PC でビルドする準備ができました。</span><span class="sxs-lookup"><span data-stu-id="162b8-116">Your Holographic Remoting app is now ready to build on your PC.</span></span> <span data-ttu-id="162b8-117">次の手順に従って変更を行い、PC にこのアプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="162b8-117">Follow the below steps and make these changes to build this application on to your PC.</span></span>

### <a name="1-set-the-player-settings"></a><span data-ttu-id="162b8-118">1.プレーヤー設定を設定する</span><span class="sxs-lookup"><span data-stu-id="162b8-118">1. Set the player settings</span></span>

<span data-ttu-id="162b8-119">Unity メニューで、[編集] > [プロジェクトの設定] の順に選択して、[プレーヤーの設定] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="162b8-119">In the Unity menu, select Edit > Project Settings to open the Player Settings window.</span></span>

<span data-ttu-id="162b8-120">**[XR Settings]\(XR 設定\)** セクションで、 **[WSA Holographic Remoting Supported]\(WSA Holographic Remoting のサポート\)** チェックボックスをオンにして、Holographic Remoting を有効にします。</span><span class="sxs-lookup"><span data-stu-id="162b8-120">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![[WSA Holographic Remoting Supported]\(WSA Holographic Remoting のサポート\) が有効にされている [XR Settings]\(XR 設定\) ウィンドウが表示された Unity](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="162b8-122">2.Unity プロジェクトをビルドする</span><span class="sxs-lookup"><span data-stu-id="162b8-122">2. Build the Unity Project</span></span>

<span data-ttu-id="162b8-123">Unity メニューで、[ファイル] > [ビルド設定] の順に選択して、[ビルド設定] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="162b8-123">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="162b8-124">[Build Settings]\(ビルド設定\) ウィンドウで、\**_[Add Open Scenes]\(開いているシーンの追加\)_* ボタンをクリックして、現在のシーンを [シーン] に追加します。</span><span class="sxs-lookup"><span data-stu-id="162b8-124">In the Build Settings window, click the \**_Add Open Scenes_* _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="162b8-125">ビルドの一覧で、_\*_[ビルド] ボタン_\*_ をクリックして、[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="162b8-125">In the Build list, then click the _*_Build button_*_ to open the Build Universal Windows Platform window:</span></span>

![シーンが追加されている [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="162b8-127">[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウで、ビルドを格納するのに適切な場所 (Documents\MixedRealityLearning など) を選択します。</span><span class="sxs-lookup"><span data-stu-id="162b8-127">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="162b8-128">新しいフォルダーを作成し、PCHolographicRemoting などの適切な名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="162b8-128">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="162b8-129">次に、_\*_[フォルダーの選択]_\*_ ボタンをクリックして、ビルド処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="162b8-129">Then click the _*_Select Folder_*_ button to start the build process:</span></span>

![[フォルダーの選択] プロンプト ウィンドウが表示されている [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="162b8-131">Unity でビルド処理が完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="162b8-131">Wait for Unity to finish the build process.</span></span>

![ビルド処理が進行中の Unity](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="162b8-133">3.アプリのビルドと配置</span><span class="sxs-lookup"><span data-stu-id="162b8-133">3. Build and deploy the application</span></span>

<span data-ttu-id="162b8-134">ビルド処理が完了すると、Unity は、ビルドを格納した場所を開くように Windows ファイル エクスプローラーを表示します。</span><span class="sxs-lookup"><span data-stu-id="162b8-134">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="162b8-135">フォルダー内を移動し、.sln ファイルをダブルクリックして Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="162b8-135">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![新しく作成された Visual Studio ソリューションが選択された Windows エクスプローラー](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="162b8-137">Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、ツールのインストールに関するドキュメントで示されている、前提条件となるすべてのコンポーネントがインストールされていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="162b8-137">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="162b8-138">[リリース] 構成、[x64] アーキテクチャ、ターゲットとして [ローカル コンピューター] を選択して、PC 用に Visual Studio を構成します。</span><span class="sxs-lookup"><span data-stu-id="162b8-138">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![ローカル コンピューター用に構成された Visual Studio](images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="162b8-140">_\*_[ローカル コンピューター]_\*_ と表示されているボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="162b8-140">Click the button that says _*_Local Machine_*_.</span></span> <span data-ttu-id="162b8-141">PC 上でアプリケーションのビルドとデプロイが開始されます。</span><span class="sxs-lookup"><span data-stu-id="162b8-141">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="162b8-142">既定では、アプリケーションはお使いの PC にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="162b8-142">The application will be installed in your PC by default.</span></span>

## <a name="testing-holographic-remoting-remote-application"></a><span data-ttu-id="162b8-143">Holographic Remoting リモート アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="162b8-143">Testing Holographic Remoting remote application</span></span>

<span data-ttu-id="162b8-144">PC アプリケーションを HoloLens 2 に接続するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="162b8-144">To connect your PC application to your HoloLens 2, follow the below process:</span></span>

### <a name="1-install-the-remoting-player-application-on-hololens-2-device"></a><span data-ttu-id="162b8-145">1.Remoting Player アプリケーションを HoloLens 2 デバイスにインストールする</span><span class="sxs-lookup"><span data-stu-id="162b8-145">1. Install the Remoting Player application on HoloLens 2 device</span></span>

<span data-ttu-id="162b8-146">_ HoloLens 2 で、Store アプリにアクセスし、"**Remoting Player**" を検索します。</span><span class="sxs-lookup"><span data-stu-id="162b8-146">_ On your HoloLens 2, visit the Store app and search for "**Remoting Player**."</span></span>
* <span data-ttu-id="162b8-147">**Remoting Player** アプリを選択します。</span><span class="sxs-lookup"><span data-stu-id="162b8-147">Select the **Remoting Player** app.</span></span>
* <span data-ttu-id="162b8-148">**[インストール]** をタップし、アプリをダウンロードしてインストールします。</span><span class="sxs-lookup"><span data-stu-id="162b8-148">Tap **Install** to download and install the app.</span></span>

### <a name="2-connect-the-holographic-remoting-pc-app-to-the-remoting-player"></a><span data-ttu-id="162b8-149">2.Holographic Remoting PC アプリを Remoting Player に接続する</span><span class="sxs-lookup"><span data-stu-id="162b8-149">2. Connect the Holographic remoting PC app to the Remoting Player</span></span>

* <span data-ttu-id="162b8-150">HoloLens で **Remoting Player** を起動します。</span><span class="sxs-lookup"><span data-stu-id="162b8-150">Start the **Remoting Player** on your HoloLens.</span></span>
* <span data-ttu-id="162b8-151">HoloLens の **IP アドレス** をメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="162b8-151">Take note of the HoloLens **IP address**.</span></span> <span data-ttu-id="162b8-152">これは、**Remoting Player** が起動した直後に Remoting Player によってホログラムとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="162b8-152">It will be displayed as a hologram by the **Remoting Player** as soon as it launches.</span></span>
* <span data-ttu-id="162b8-153">Holographic Remoting PC アプリケーションを PC で開きます。</span><span class="sxs-lookup"><span data-stu-id="162b8-153">Open the Holographic Remoting PC application on your PC.</span></span>
* <span data-ttu-id="162b8-154">アプリケーションが起動したら、**IP アドレス** を入力し、 **[接続]** ボタンをクリックして接続します。</span><span class="sxs-lookup"><span data-stu-id="162b8-154">Once the application is launched, enter the **IP address** and click on the **Connect**  button to connect.</span></span>

## <a name="congratulations"></a><span data-ttu-id="162b8-155">結論</span><span class="sxs-lookup"><span data-stu-id="162b8-155">Congratulations</span></span>

<span data-ttu-id="162b8-156">このチュートリアルでは、Holographic Remoting リモート アプリを作成していつでも HoloLens 2 に接続できるようにし、Mixed Reality で 3D コンテンツを視覚化する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="162b8-156">In this tutorial, you learned how to create a Holographic Remoting remote app and connect to HoloLens 2 at any point, providing a way to visualize 3D content in mixed reality.</span></span> <span data-ttu-id="162b8-157">HoloLens が Holographic Remoting PC アプリケーションに接続されると、Mixed Reality エクスペリエンスが HoloLens 2 デバイスにストリーミングされているのを確認できます。</span><span class="sxs-lookup"><span data-stu-id="162b8-157">Once the HoloLens connected to the Holographic Remoting PC application, you should see the mixed reality experience streaming into your HoloLens 2 device.</span></span>
