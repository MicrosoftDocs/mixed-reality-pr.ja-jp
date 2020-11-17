---
title: マルチユーザー機能のチュートリアル - 2. Photon Unity Networking の設定
description: このコースを完了すると、HoloLens 2 アプリケーション内で Photon Unity Network を実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: aeda463610f1fb1205eade556a2c2b9bc07a4fde
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353480"
---
# <a name="2-setting-up-photon-unity-networking"></a><span data-ttu-id="b4c50-105">2.Photon Unity Networking の設定</span><span class="sxs-lookup"><span data-stu-id="b4c50-105">2. Setting up Photon Unity Networking</span></span>

## <a name="overview"></a><span data-ttu-id="b4c50-106">概要</span><span class="sxs-lookup"><span data-stu-id="b4c50-106">Overview</span></span>

<span data-ttu-id="b4c50-107">このチュートリアルでは、Photon Unity Networking (PUN) を使用して共有エクスペリエンスの作成準備をします。</span><span class="sxs-lookup"><span data-stu-id="b4c50-107">In this tutorial, you will prepare for creating a shared experience using Photon Unity Networking (PUN).</span></span> <span data-ttu-id="b4c50-108">PUN アプリの作成方法、PUN アセットを Unity プロジェクトにインポートする方法、Unity プロジェクトを PUN アプリに接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b4c50-108">You will learn how to create a PUN app, import PUN assets into your Unity project, and connect your Unity project to the PUN app.</span></span>

## <a name="objectives"></a><span data-ttu-id="b4c50-109">目標</span><span class="sxs-lookup"><span data-stu-id="b4c50-109">Objectives</span></span>

* <span data-ttu-id="b4c50-110">PUN アプリを作成する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="b4c50-110">Learn how to create a PUN app</span></span>
* <span data-ttu-id="b4c50-111">PUN アセットを探してインポートする方法を学習する</span><span class="sxs-lookup"><span data-stu-id="b4c50-111">Learn how to find and import the PUN assets</span></span>
* <span data-ttu-id="b4c50-112">Unity プロジェクトを PUN アプリに接続する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="b4c50-112">Learn how to connect your Unity project to the PUN app</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="b4c50-113">Unity プロジェクトの作成と準備</span><span class="sxs-lookup"><span data-stu-id="b4c50-113">Creating and preparing the Unity project</span></span>

<span data-ttu-id="b4c50-114">このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備します。</span><span class="sxs-lookup"><span data-stu-id="b4c50-114">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="b4c50-115">このためには、まず「[プロジェクトの初期化と最初のアプリケーションの配置](mr-learning-base-02.md)」に従ってください ([デバイスにアプリケーションをビルドする](mr-learning-base-02.md#building-your-application-to-your-hololens-2)手順は除きます)。これには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="b4c50-115">For this, first follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="b4c50-116">[Unity プロジェクトを作成](mr-learning-base-02.md#creating-the-unity-project)し、"*MRTK チュートリアル*" などの適切な名前を付ける</span><span class="sxs-lookup"><span data-stu-id="b4c50-116">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
1. [<span data-ttu-id="b4c50-117">ビルド プラットフォームを切り替える</span><span class="sxs-lookup"><span data-stu-id="b4c50-117">Switching the build platform</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. [<span data-ttu-id="b4c50-118">TextMeshPro の重要なリソースをインポートする</span><span class="sxs-lookup"><span data-stu-id="b4c50-118">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
1. [<span data-ttu-id="b4c50-119">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="b4c50-119">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
1. [<span data-ttu-id="b4c50-120">Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="b4c50-120">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
1. <span data-ttu-id="b4c50-121">[シーンを作成して構成](mr-learning-base-02.md#creating-and-configuring-the-scene)し、シーンに *MultiUserCapabilities* などの適切な名前を付ける</span><span class="sxs-lookup"><span data-stu-id="b4c50-121">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *MultiUserCapabilities*</span></span>

<span data-ttu-id="b4c50-122">次に、「[空間認識表示オプションの変更](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)」の指示に従い、次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="b4c50-122">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="b4c50-123">**MRTK 構成プロファイル** を **DefaultHoloLens2ConfigurationProfile** に変更します</span><span class="sxs-lookup"><span data-stu-id="b4c50-123">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="b4c50-124">**空間認識メッシュ表示オプション** を **[Occlusion]\(オクルージョン\)** に変更します</span><span class="sxs-lookup"><span data-stu-id="b4c50-124">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="enabling-additional-capabilities"></a><span data-ttu-id="b4c50-125">その他の機能を有効にする</span><span class="sxs-lookup"><span data-stu-id="b4c50-125">Enabling additional capabilities</span></span>

<span data-ttu-id="b4c50-126">Unity メニューで **[Edit]\(編集\)**  >  **[Project Settings]\(プロジェクトの設定\)** を選択して、[Player Settings]\(プレーヤーの設定\) ウィンドウを開きます。次に、 **[Player]\(プレーヤー\)**  >   **[Publishing Settings]\(発行の設定\)** セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="b4c50-126">In the Unity menu, select **Edit** > **Project Settings...** to open the Player Settings window, then locate the **Player** >  **Publishing Settings** section:</span></span>

![[Player]\(プレーヤー\) 設定が表示された Unity](images/mr-learning-sharing/sharing-02-section2-step1-1.png)

<span data-ttu-id="b4c50-128">**[Publishing Settings]\(公開の設定\)** で、 **[Capabilities]\(機能\)** セクションまで下にスクロールして、上の「[Unity プロジェクトを構成する](mr-learning-base-02.md#configuring-the-unity-project)」手順で有効にした **InternetClient**、**Microphone**、**SpatialPerception**、**GazeInput** の機能が有効になっていることを再確認します。</span><span class="sxs-lookup"><span data-stu-id="b4c50-128">In the  **Publishing Settings**, scroll down to the **Capabilities** section and double-check that the **InternetClient**, **Microphone**, **SpatialPerception**, and **GazeInput** capabilities, which you enabled during the [Configuring the Unity project](mr-learning-base-02.md#configuring-the-unity-project) step above, are enabled.</span></span>

<span data-ttu-id="b4c50-129">その後、次の追加機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b4c50-129">Then enable the following additional capabilities:</span></span>

* <span data-ttu-id="b4c50-130">**InternetClientServer** 機能</span><span class="sxs-lookup"><span data-stu-id="b4c50-130">**InternetClientServer** capability</span></span>
* <span data-ttu-id="b4c50-131">**PrivateNetworkClientServer** 機能</span><span class="sxs-lookup"><span data-stu-id="b4c50-131">**PrivateNetworkClientServer** capability</span></span>

![[Capabilities]\(機能\) 設定が表示された Unity](images/mr-learning-sharing/sharing-02-section2-step1-2.png)

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="b4c50-133">組み込みの Unity パッケージのインストール</span><span class="sxs-lookup"><span data-stu-id="b4c50-133">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="b4c50-134">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Package Manager]\(パッケージ マネージャー\)** の順に選択して、[Package Manager]\(パッケージ マネージャー\) ウィンドウを開きます。次に、 **[AR Foundation]** を選択し、 **[Install]\(インストール\)** ボタンをクリックしてパッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="b4c50-134">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![AR Foundation が選択されている [Package Manager]\(パッケージ マネージャー\) が表示された Unity](images/mr-learning-sharing/sharing-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="b4c50-136">次のセクションでインポートする Azure Spatial Anchors SDK で必要になるため、AR Foundation パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="b4c50-136">You are installing the AR Foundation package because it is required by the Azure Spatial Anchors SDK you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="b4c50-137">チュートリアルのアセットのインポート</span><span class="sxs-lookup"><span data-stu-id="b4c50-137">Importing the tutorial assets</span></span>

<span data-ttu-id="b4c50-138">次の Unity カスタム パッケージを、**記載されている順で** ダウンロードして **インポート** します。</span><span class="sxs-lookup"><span data-stu-id="b4c50-138">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>

* <span data-ttu-id="b4c50-139">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (バージョン 2.2.1)</span><span class="sxs-lookup"><span data-stu-id="b4c50-139">[AzureSpatialAnchors.unitypackage](https://github.com/Azure/azure-spatial-anchors-samples/releases/download/v2.2.1/AzureSpatialAnchors.unitypackage) (version 2.2.1)</span></span>
* [<span data-ttu-id="b4c50-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b4c50-140">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="b4c50-141">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b4c50-141">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)
* [<span data-ttu-id="b4c50-142">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="b4c50-142">MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/multi-user-capabilities-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.MultiUserCapabilities.2.4.0.unitypackage)

<span data-ttu-id="b4c50-143">チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b4c50-143">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![チュートリアルのアセットがインポートされた後の Unity の [Hierarchy]\(階層\)、[Scene]\(シーン\)、[Project]\(プロジェクト\) ウィンドウ](images/mr-learning-sharing/sharing-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="b4c50-145">Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4c50-145">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="b4c50-146">MultiUserCapabilities チュートリアル アセット パッケージをインポートすると、型または名前空間が存在しないことを示すいくつかの [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) エラーが [Console]\(コンソール\) ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4c50-146">After importing the MultiUserCapabilities tutorial assets package, you will see several [CS0246](https://docs.microsoft.com/dotnet/csharp/language-reference/compiler-messages/cs0246) errors in the Console window stating that the type or namespace is missing.</span></span> <span data-ttu-id="b4c50-147">これは想定されているものであり、次のセクションで PUN アセットをインポートする際に解決されます。</span><span class="sxs-lookup"><span data-stu-id="b4c50-147">This is expected and will be resolved in the next section when you import the PUN assets.</span></span>

## <a name="importing-the-pun-assets"></a><span data-ttu-id="b4c50-148">PUN アセットをインポートする</span><span class="sxs-lookup"><span data-stu-id="b4c50-148">Importing the PUN assets</span></span>

<span data-ttu-id="b4c50-149">Unity メニューで、 **[Window]\(ウィンドウ\)** 、 **[Asset Store]\(アセット ストア\)** の順に選択して [Asset Store]\(アセット ストア\) ウィンドウを開き、Exit Games から **[PUN 2 - FREE]** を検索して選択し、 **[Download]\(ダウンロード\)** ボタンをクリックしてアセット パッケージを自分の Unity アカウントにダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b4c50-149">In the Unity menu, select **Window** > **Asset Store** to open the Asset Store window, search for and select **PUN 2 - FREE** from Exit Games, click the **Download** button to download the asset package to your Unity account.</span></span>

<span data-ttu-id="b4c50-150">ダウンロードが完了したら、 **[Import]\(インポート\)** ボタンをクリックして [Import Unity Package]\(Unity パッケージのインポート\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="b4c50-150">When the download is complete, click the **Import** button to open the Import Unity Package window:</span></span>

![[PUN 2 - Free] が表示された [Asset Store]\(アセット ストア\) が表示された Unity](images/mr-learning-sharing/sharing-02-section5-step1-1.png)

<span data-ttu-id="b4c50-152">[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="b4c50-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![PUN 2 のインポート ウィンドウが表示された Unity](images/mr-learning-sharing/sharing-02-section5-step1-2.png)

<span data-ttu-id="b4c50-154">Unity でインポート プロセスが完了したら、[Pun Wizard]\(Pun ウィザード\) ウィンドウが表示されて [PUN Setup]\(PUN 設定\) メニューが読み込まれます。今はこのウィンドウを無視するか、閉じて構いません。</span><span class="sxs-lookup"><span data-stu-id="b4c50-154">Once Unity has completed the import process, the Pun Wizard window will appear with the PUN Setup menu loaded, you can ignore or close this window for now:</span></span>

![[PUN Setup]\(PUN 設定\) ウィンドウが表示された Unity](images/mr-learning-sharing/sharing-02-section5-step1-3.png)

## <a name="creating-the-pun-application"></a><span data-ttu-id="b4c50-156">PUN アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="b4c50-156">Creating the PUN application</span></span>

<span data-ttu-id="b4c50-157">このセクションでは、Photon アカウントを作成し (まだ作成していない場合)、新しい PUN アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b4c50-157">In this section, you will create a Photon account, if you don't already have one, and create a new PUN app.</span></span>

<span data-ttu-id="b4c50-158">使用したいアカウントが既にある場合は Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">ダッシュボード</a> に移動してサインインします。なければ、 **[こちらから作成してください]** リンクをクリックして手順に従い、新しいアカウントを登録します。</span><span class="sxs-lookup"><span data-stu-id="b4c50-158">Navigate to the Photon <a href="https://dashboard.photonengine.com/account/signin" target="_blank">dashboard</a> and sign in if you already have an account you want to use, otherwise, click the **Create One** link and follow the instructions to register a new account:</span></span>

![Photon ログイン ページ](images/mr-learning-sharing/sharing-02-section6-step1-1.png)

<span data-ttu-id="b4c50-160">サインインしたら、 **[Create a New App]\(新しいアプリの作成\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b4c50-160">Once signed in, click the **Create a New App** button:</span></span>

![Photon ダッシュボードの開始ページ](images/mr-learning-sharing/sharing-02-section6-step1-2.png)

<span data-ttu-id="b4c50-162">[Create a New Application]\(新しいアプリケーションの作成\) ページで、次の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="b4c50-162">On the Create a New Application page, enter the following values:</span></span>

* <span data-ttu-id="b4c50-163">[Photon Type]\(Photon の種別\) には、[PUN] を選択します</span><span class="sxs-lookup"><span data-stu-id="b4c50-163">For Photon Type, select PUN</span></span>
* <span data-ttu-id="b4c50-164">[Name]\(名前\) には、適切な名前 (_MRTK チュートリアル_ など) を入力します</span><span class="sxs-lookup"><span data-stu-id="b4c50-164">For Name, enter a suitable name, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="b4c50-165">[Description]\(説明\) には、必要に応じて適切な説明を入力します</span><span class="sxs-lookup"><span data-stu-id="b4c50-165">For Description, optionally enter a suitable description</span></span>
* <span data-ttu-id="b4c50-166">"URL" フィールドは空のままにします</span><span class="sxs-lookup"><span data-stu-id="b4c50-166">For Url, leave the field empty</span></span>

<span data-ttu-id="b4c50-167">**[Create]\(作成する\)** をクリックして新しいアプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="b4c50-167">Then click the **Create** button to create the new app:</span></span>

![Photon のアプリケーションの作成ページ](images/mr-learning-sharing/sharing-02-section6-step1-3.png)

<span data-ttu-id="b4c50-169">Photon で作成プロセスが完了すると、新しい PUN アプリがダッシュボードに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4c50-169">Once Photon has finished the creation process, the new PUN app will appear on your dashboard:</span></span>

![Photon のアプリケーション ページ](images/mr-learning-sharing/sharing-02-section6-step1-4.png)

## <a name="connecting-the-unity-project-to-the-pun-application"></a><span data-ttu-id="b4c50-171">Unity プロジェクトを PUN アプリケーションに接続する</span><span class="sxs-lookup"><span data-stu-id="b4c50-171">Connecting the Unity project to the PUN application</span></span>

<span data-ttu-id="b4c50-172">このセクションでは、Unity プロジェクトを前のセクションで作成した PUN アプリに接続します。</span><span class="sxs-lookup"><span data-stu-id="b4c50-172">In this section, you will connect your Unity project to the PUN app you created in the previous section.</span></span>

<span data-ttu-id="b4c50-173">Photon ダッシュボードで、 **"App ID"(アプリ ID)** フィールドをクリックしてアプリ ID を表示し、クリップボードにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b4c50-173">On the Photon dashboard, click the **App ID** field to reveal the app ID, then copy it to your clipboard:</span></span>

![アプリ ID が選択されている Photon アプリケーション ページ](images/mr-learning-sharing/sharing-02-section7-step1-1.png)

<span data-ttu-id="b4c50-175">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Photon Unity Networking]**  >  **[PUN Wizard]\(PUN ウィザード\)** を選択して [Pun Wizard]\(Pun ウィザード\) ウィンドウを開き、 **[Setup Project]\(プロジェクトの設定\)** ボタンをクリックして [PUN Setup]\(PUN 設定\) メニューを開いて次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="b4c50-175">In the Unity menu, select **Window** > **Photon Unity Networking** > **PUN Wizard** to open the Pun Wizard window, click the **Setup Project** button to open the PUN Setup menu, and configure it as follows:</span></span>

* <span data-ttu-id="b4c50-176">**"AppId or Email"(アプリ ID またはメール)** フィールドで、前のステップでコピーした PUN アプリ ID を貼り付けます</span><span class="sxs-lookup"><span data-stu-id="b4c50-176">In the **AppId or Email** field, paste the PUN app ID you copied in the previous step</span></span>

<span data-ttu-id="b4c50-177">**[Setup Project]\(プロジェクトの設定\)** ボタンをクリックしてアプリ ID を適用します。</span><span class="sxs-lookup"><span data-stu-id="b4c50-177">Then click the **Setup Project** button to apply the app ID:</span></span>

![アプリ ID が入力された [PUN Setup]\(PUN 設定\) が表示された Unity](images/mr-learning-sharing/sharing-02-section7-step1-2.png)

<span data-ttu-id="b4c50-179">Unity で PUN 設定プロセスが完了すると、[PUN Setup]\(PUN 設定\) メニューに **[Done!]\(完了\)** というメッセージが表示され、</span><span class="sxs-lookup"><span data-stu-id="b4c50-179">Once Unity has finished the PUN setup process, the PUN Setup menu will display the message **Done!**</span></span> <span data-ttu-id="b4c50-180">[Project]\(プロジェクト\) ウィンドウで **PhotonServerSettings** アセットが自動的に選択され、そのプロパティが [Inspector]\(インスペクター\) ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b4c50-180">and automatically select the **PhotonServerSettings** asset in the Project window, so its properties are displayed in the Inspector window:</span></span>

![[Setup Project]\(プロジェクトの設定\) が適用された [PUN Setup]\(PUN 設定\) が表示された Unity](images/mr-learning-sharing/sharing-02-section7-step1-3.png)

## <a name="congratulations"></a><span data-ttu-id="b4c50-182">結論</span><span class="sxs-lookup"><span data-stu-id="b4c50-182">Congratulations</span></span>

<span data-ttu-id="b4c50-183">PUN アプリを作成して、これを Unity プロジェクトに接続できました。</span><span class="sxs-lookup"><span data-stu-id="b4c50-183">You have successfully created a PUN app and connected it to your Unity project.</span></span> <span data-ttu-id="b4c50-184">次の手順では、他のユーザーとの接続を許可して複数のユーザーが互いを見られるようにします。</span><span class="sxs-lookup"><span data-stu-id="b4c50-184">Your next step is to allow connections with other users so that multiple users can see each other.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b4c50-185">次のチュートリアル:3.複数ユーザーの接続</span><span class="sxs-lookup"><span data-stu-id="b4c50-185">Next Tutorial: 3. Connecting multiple users</span></span>](mr-learning-sharing-03.md)
