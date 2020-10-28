---
title: 入門チュートリアル -2. プロジェクトの初期化と最初のアプリケーションの配置
description: このコースでは、Mixed Reality Toolkit (MRTK) を使用して複合現実のアプリケーションを作成する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: e62469fd2758590320d59b6c4fa1d469a60e0b8d
ms.sourcegitcommit: d8f39c0b95d9e61d645d64f27baabc7a1c300dc1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92293259"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="78802-105">2. プロジェクトの初期化と最初のアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="78802-105">2. Initializing your project and deploying your first application</span></span>

## <a name="overview"></a><span data-ttu-id="78802-106">概要</span><span class="sxs-lookup"><span data-stu-id="78802-106">Overview</span></span>

<span data-ttu-id="78802-107">このチュートリアルでは、新しい Unity プロジェクトを作成し、それを <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality ツールキット (MRTK)</a> 開発用に構成し、MRTK をインポートする方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="78802-107">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="78802-108">また、Visual Studio で基本的な Unity サンプル シーンを構成およびビルドし、ご利用の HoloLens 2 またはエミュレーターに配置する方法についても学習します。</span><span class="sxs-lookup"><span data-stu-id="78802-108">You'll also walk through configuring, building, and deploying the basic Unity sample scene from Visual Studio to your HoloLens 2 or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="78802-109">目標</span><span class="sxs-lookup"><span data-stu-id="78802-109">Objectives</span></span>

* <span data-ttu-id="78802-110">HoloLens 開発用に Unity を構成する方法について学習する</span><span class="sxs-lookup"><span data-stu-id="78802-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="78802-111">アプリをビルドして HoloLens に配置する方法について学習する</span><span class="sxs-lookup"><span data-stu-id="78802-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="78802-112">空間マッピングのメッシュ、ハンド メッシュ、およびフレームレート カウンターを体験する</span><span class="sxs-lookup"><span data-stu-id="78802-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="78802-113">Unity プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="78802-113">Creating the Unity project</span></span>

<span data-ttu-id="78802-114">**Unity Hub** を起動し、 **[Projects]\(プロジェクト\)** タブを選択し、 **[New]\(新規\)** ボタンの横にある **下矢印** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="78802-114">Launch **Unity Hub** , select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="78802-116">「 [前提条件](mr-learning-base-01.md#prerequisites)」に指定されている Unity の **バージョン** を、ドロップダウンで選択します。</span><span class="sxs-lookup"><span data-stu-id="78802-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="78802-118">Unity Hub で特定の Unity バージョンが利用できない場合は、Unity の<a href="https://unity3d.com/get-unity/download/archive" target="_blank">アーカイブのダウンロード</a>に関するページから、そのインストールを開始できます。</span><span class="sxs-lookup"><span data-stu-id="78802-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="78802-119">[Create a new project]\(新規プロジェクトの作成\) ウィンドウで、以下のようにします。</span><span class="sxs-lookup"><span data-stu-id="78802-119">In the Create a new project window:</span></span>

* <span data-ttu-id="78802-120">**[Templates]\(テンプレート\)** が **3D** に設定されていることを確認します</span><span class="sxs-lookup"><span data-stu-id="78802-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="78802-121">" _MRTK チュートリアル_ " など、適切な **[Project Name]\(プロジェクト名\)** を入力します</span><span class="sxs-lookup"><span data-stu-id="78802-121">Enter a suitable **Project Name** , for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="78802-122">プロジェクトを格納するための適切な **[Location]\(場所\)** を選択します。たとえば、 _D:\MixedRealityLearning_ など</span><span class="sxs-lookup"><span data-stu-id="78802-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="78802-123">**[Create]\(作成\)** ボタンをクリックして、新しい Unity プロジェクトを作成して起動します</span><span class="sxs-lookup"><span data-stu-id="78802-123">Click the **Create** button to create and launch your new Unity project</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="78802-125">Windows で作業している場合は、255 文字の MAX_PATH 制限があります。</span><span class="sxs-lookup"><span data-stu-id="78802-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="78802-126">そのため、Unity プロジェクトはドライブのルートの近くに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78802-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="78802-127">Unity によってプロジェクトが作成されるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="78802-127">Wait for Unity to create the project:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="78802-129">ビルド プラットフォームを切り替える</span><span class="sxs-lookup"><span data-stu-id="78802-129">Switching the build platform</span></span>

<span data-ttu-id="78802-130">Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** を選択し、[Build Settings]\(ビルド設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="78802-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="78802-132">[Build Settings]\(ビルド設定\) ウィンドウで、 **[Universal Windows Platform]\(ユニバーサル Windows プラットフォーム\)** を選択して、 **[Switch Platform]\(プラットフォームの切り替え\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="78802-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="78802-134">Unity がプラットフォームの切り替えを完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="78802-134">Wait for Unity to finish switching the platform:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="78802-136">Unity でプラットフォームの切り替えが完了したら、赤色の **x** アイコンをクリックして、[Build Settings]\(ビルド設定\) ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="78802-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="78802-138">TextMeshPro の重要なリソースをインポートする</span><span class="sxs-lookup"><span data-stu-id="78802-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="78802-139">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[TextMeshPro]**  >  **[Import TMP Essential Resources]\(TMP の重要なリソースをインポート\)** の順に選択して、[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="78802-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="78802-141">[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="78802-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="78802-143">TextMeshPro の重要なリソースは、MRTK の UI 要素で必要です。</span><span class="sxs-lookup"><span data-stu-id="78802-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="78802-144">ご自分のプロジェクトで MRTK の UI 要素を使用する予定がない場合は、この手順を省略できます。</span><span class="sxs-lookup"><span data-stu-id="78802-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="78802-145">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="78802-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="78802-146">Unity カスタム パッケージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="78802-146">Download the Unity custom package:</span></span>

* [<span data-ttu-id="78802-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="78802-147">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

<span data-ttu-id="78802-148">Unity メニューで、 **[Assets]\(アセット\)**  >  **[Import Package]\(パッケージのインポート\)**  >  **[Custom Package...]\(カスタム パッケージ...\)** を選択して [Import package...]\(パッケージのインポート...\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="78802-148">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="78802-150">[Import package...]\(パッケージのインポート...\) ウィンドウで、ダウンロードした **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** を選択し、 **[Open]\(開く\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="78802-150">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage** you downloaded and click the **Open** button:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="78802-152">[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="78802-152">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="78802-154">Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="78802-154">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="78802-155">1. MRTK プロジェクト コンフィギュレーター設定を適用する</span><span class="sxs-lookup"><span data-stu-id="78802-155">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="78802-156">Unity によって前のセクションからのパッケージのインポートが完了すると、[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="78802-156">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="78802-157">表示されない場合は、 **[Mixed Reality Toolkit]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** に移動して手動で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="78802-157">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** :</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="78802-159">[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウで、 **[Modify Configurations]\(構成の変更\)** セクションを展開し、他のすべてのオプションを確実にオンにしてから、 **[Apply]\(適用\)** ボタンをクリックして設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="78802-159">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step1-2.png)

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="78802-161">2.追加のプロジェクト設定を構成する</span><span class="sxs-lookup"><span data-stu-id="78802-161">2. Configure additional project settings</span></span>

<span data-ttu-id="78802-162">Unity メニューで、 **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクト設定...\)** を選択し、[Project Settings]\(プロジェクト設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="78802-162">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="78802-164">[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレイヤー\)**  >  **[XR Settings]\(XR 設定\)** の順に選択し、[ **+** ] アイコンをクリックします。Windows Mixed reality を選択して Windows Mixed Reality SDK を追加します。</span><span class="sxs-lookup"><span data-stu-id="78802-164">In the Project Settings window, select **Player** > **XR Settings** , click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="78802-166">Unity によって Windows Mixed Reality SDK のインポートが完了すると、[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが再び表示されます。</span><span class="sxs-lookup"><span data-stu-id="78802-166">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="78802-167">そうならない場合は、Unity メニューを使用してそれを開きます。</span><span class="sxs-lookup"><span data-stu-id="78802-167">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="78802-168">[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウで、 **[Audio Spatializer]** ドロップダウンを使用して **[MS HRTF Spatializer]** を選択してから、 **[Apply]\(適用\)** ボタンをクリックしてこの設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="78802-168">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer** , then click the **Apply** button to apply the setting:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-3.png)

<span data-ttu-id="78802-170">[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレーヤー\)**  >  **[XR Settings]\(XR 設定\)** を選択してから、 **[Depth Format]\(深度形式\)** ドロップダウンを使用して **[16-bit depth]\(16 ビット深度\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="78802-170">In the Project Settings window, select **Player** > **XR Settings** , then use the **Depth Format** dropdown to select **16-bit depth** :</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="78802-172">[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレイヤー\)**  >  **[Publishing Settings]\(公開の設定\)** の順に選択してから、 **[Package name]\(パッケージ名\)** フィールドに適切な名前 (たとえば _MRTKTutorials-GettingStarted_ ) を入力します。</span><span class="sxs-lookup"><span data-stu-id="78802-172">In the Project Settings window, select **Player** > **Publishing Settings** , then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_ :</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section5-step2-5.png)

> [!NOTE]
> <span data-ttu-id="78802-174">'パッケージ名' は、アプリの一意の識別子です。</span><span class="sxs-lookup"><span data-stu-id="78802-174">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="78802-175">以前にインストールしたアプリが上書きされないように、アプリを配置する前にこの識別子を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78802-175">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="78802-176">'製品名' は、HoloLens の [スタート] メニューに表示される名前です。</span><span class="sxs-lookup"><span data-stu-id="78802-176">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="78802-177">開発中にアプリを見つけやすくするには、名前の前にアンダースコアを追加し、上部にくるように並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="78802-177">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="78802-178">シーンを作成して構成する</span><span class="sxs-lookup"><span data-stu-id="78802-178">Creating and configuring the scene</span></span>

<span data-ttu-id="78802-179">Unity メニューで、 **[File]\(ファイル\)**  >  **[New Scene]\(新しいシーン\)** の順に選択して新しいシーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="78802-179">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="78802-181">Unity メニューで、 **[Mixed Reality Toolkit]**  >  **[Add to Scene and Configure...]\(シーンに追加して構成する...\)** の順に選択して、MRTK を現在のシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="78802-181">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="78802-183">[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択したままとし、[Inspector]\(インスペクター\) ウィンドウで、 **MixedRealityToolkit** 構成プロファイルが **DefaultMixedRealityToolkitConfigurationProfile** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="78802-183">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile** :</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="78802-185">通常、HoloLens 向けの開発時には DefaultHoloLens2ConfigurationProfile を使用します。</span><span class="sxs-lookup"><span data-stu-id="78802-185">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="78802-186">ただし、このチュートリアルでは、DefaultMixedRealityToolkitConfigurationProfile を使用します。そして、次のチュートリアル「[MRTK プロファイルの構成](mr-learning-base-03.md)」で、DefaultHoloLens2ConfigurationProfile に変更します。</span><span class="sxs-lookup"><span data-stu-id="78802-186">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile, then in the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

<span data-ttu-id="78802-187">Unity メニューで、 **[File]\(ファイル\)**  >  **[Save As...]\(名前を付けて保存...\)** を選択して [Save Scene]\(シーンの保存\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="78802-187">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="78802-189">[Save Scene]\(シーンの保存\) ウィンドウで、プロジェクトの **[Scenes]\(シーン\)** フォルダーに移動し、シーンに適切な名前を付け (たとえば、 _GettingStarted_ )、 **[Save]\(保存\)** ボタンをクリックしてシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="78802-189">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_ , and click the **Save** button to save the scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="78802-191">HoloLens 2 デバイス用にアプリケーションをビルドする</span><span class="sxs-lookup"><span data-stu-id="78802-191">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="78802-192">1.Unity プロジェクトのビルド</span><span class="sxs-lookup"><span data-stu-id="78802-192">1. Build the Unity project</span></span>

<span data-ttu-id="78802-193">Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** を選択し、[Build Settings]\(ビルド設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="78802-193">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="78802-194">[Build Settings]\(ビルド設定\) ウィンドウで、 **[Add Open Scenes]\(開いているシーンを追加する\)** ボタンをクリックして、 **[Scenes In Build]\(ビルド内のシーン\)** リストの現在のシーンを追加します。次に **[Build]\(ビルド\)** ボタンをクリックして、[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="78802-194">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="78802-196">[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウで、ビルドを格納する適切な場所 (たとえば _D:\MixedRealityLearning\Builds_ ) を選択し、新しいフォルダーを作成して適切な名前 (たとえば _GettingStarted_ ) を付け、 **[Select Folder]\(フォルダーの選択\)** ボタンをクリックしてビルド処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="78802-196">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_ , create a new folder and give it a suitable name, for example, _GettingStarted_ , and then click the **Select Folder** button to start the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="78802-198">Unity がビルド処理を完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="78802-198">Wait for Unity to finish the build process:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="78802-200">2.アプリのビルドと配置</span><span class="sxs-lookup"><span data-stu-id="78802-200">2. Build and deploy the application</span></span>

<span data-ttu-id="78802-201">ビルド処理が完了すると、お客様がビルドを格納した場所を開くように Unity から Windows ファイル エクスプローラーに指示が出されます。</span><span class="sxs-lookup"><span data-stu-id="78802-201">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="78802-202">フォルダー内を移動し、ソリューション ファイルをダブルクリックして Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="78802-202">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="78802-204">Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、「 **[ツールのインストール](../../install-the-tools.md)** 」ドキュメントで示されている、前提条件となるすべてのコンポーネントが用意できていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="78802-204">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="78802-205">**[マスター]** または **[リリース]** 構成を選択し、 **[ARM64]** アーキテクチャを選択し、ターゲットとして **[デバイス]** を選択して、HoloLens 用に Visual Studio を構成します。</span><span class="sxs-lookup"><span data-stu-id="78802-205">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="78802-207">HoloLens (第 1 世代) に配置する場合は、 **x86** アーキテクチャを選択します。</span><span class="sxs-lookup"><span data-stu-id="78802-207">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="78802-208">HoloLens の場合、通常は ARM アーキテクチャ用にビルドします。</span><span class="sxs-lookup"><span data-stu-id="78802-208">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="78802-209">ただし、Unity 2019.3 には、Visual Studio で ARM をビルド アーキテクチャとして選択した場合にエラーを引き起こす<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>既知の問題</strong></a>が存在します。</span><span class="sxs-lookup"><span data-stu-id="78802-209">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="78802-210">推奨される回避策は、ARM64 用にビルドすることです。</span><span class="sxs-lookup"><span data-stu-id="78802-210">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="78802-211">それがオプションでない場合は **[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\) > [Player]\(プレイヤー\) > [Other Settings]\(他の設定\)** の順に選択して、 **[Graphics Jobs]\(グラフィック ジョブ\)** を無効にします。</span><span class="sxs-lookup"><span data-stu-id="78802-211">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs** .</span></span>

> [!NOTE]
> <span data-ttu-id="78802-212">ターゲット オプションとして [デバイス] が表示されない場合は、Visual Studio ソリューションのスタートアップ プロジェクトを IL2CPP プロジェクトから UWP プロジェクトに変更することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="78802-212">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="78802-213">それを行うには、ソリューション エクスプローラーで、[YourProjectName (Universal Windows)]\(YourProjectName (ユニバーサル Windows)\) を右クリックし、 **[スタートアップ プロジェクトに設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="78802-213">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project** .</span></span>

<span data-ttu-id="78802-214">ご利用のコンピューターに HoloLens を接続し、 **[デバッグ]**  >  **[デバッグなしで開始]** の順に選択して、ご利用のデバイス用にビルドして配置します。</span><span class="sxs-lookup"><span data-stu-id="78802-214">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![mr-learning-base](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="78802-216">デバイスに対してビルドする前に、デバイスが開発者モードになっており、かつ、開発コンピューターとペアリングされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="78802-216">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="78802-217">この両方のステップを完了するには、[こちらの手順](../../platform-capabilities-and-apis/using-visual-studio.md)に従います。</span><span class="sxs-lookup"><span data-stu-id="78802-217">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="78802-218">また、[HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) に配置することも、サイドローディング用の[アプリ パッケージ](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="78802-218">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="78802-219">[デバッグなしで開始] を使用すると、Visual Studio デバッガーがアタッチされていない状態でも、ご利用のデバイス上でアプリが自動的に起動します。</span><span class="sxs-lookup"><span data-stu-id="78802-219">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="78802-220">アプリを自動的に起動せずに、ご利用のデバイスに配置するには、 **[ビルド] > [ソリューションの配置]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="78802-220">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="78802-221">アプリでは、診断プロファイラーが表示される場合があります。このオン、オフを切り替えるには、音声コマンド **Toggle Diagnostics** を使用します。</span><span class="sxs-lookup"><span data-stu-id="78802-221">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics** .</span></span> <span data-ttu-id="78802-222">アプリへの変更がパフォーマンスに影響を与える可能性がある場合は、開発中の多くは、プロファイラーを表示したままにしておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="78802-222">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="78802-223">たとえば、HoloLens アプリは [60 FPS で継続的に実行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="78802-223">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="78802-224">結論</span><span class="sxs-lookup"><span data-stu-id="78802-224">Congratulations</span></span>

<span data-ttu-id="78802-225">これで、最初の HoloLens アプリが展開されました。</span><span class="sxs-lookup"><span data-stu-id="78802-225">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="78802-226">手順に従うと、HoloLens によって認識されたサーフェイスに対応する空間マッピングのメッシュが表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="78802-226">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="78802-227">さらに、手の追跡用の手と指のインジケーターと、アプリのパフォーマンスを監視するためのフレームレート カウンターも表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="78802-227">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="78802-228">これらの機能は、MRTK に含まれている基本的なもののほんの一部です。</span><span class="sxs-lookup"><span data-stu-id="78802-228">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="78802-229">次のチュートリアルでは、コンテンツをシーンに追加して、HoloLens と MRTK の機能を調べます。</span><span class="sxs-lookup"><span data-stu-id="78802-229">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="78802-230">次のチュートリアル:3. MRTK プロファイルの構成</span><span class="sxs-lookup"><span data-stu-id="78802-230">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
