---
title: プロジェクトの初期化と最初のアプリケーションの配置
description: このコースでは、Mixed Reality Toolkit (MRTK) 用に Unity プロジェクトを構成する方法と、それを HoloLens 2 に配置する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: ff479df81316ab5ceeabf045ad1bbae007190ed4
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2021
ms.locfileid: "99238148"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="2b2db-104">2. プロジェクトの初期化と最初のアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="2b2db-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="2b2db-105">このチュートリアルでは、新しい Unity プロジェクトを作成し、それを <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality ツールキット (MRTK)</a> 開発用に構成し、MRTK をインポートする方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="2b2db-106">また、Visual Studio で基本的な Unity シーンを構成およびビルドし、HoloLens 2 に配置する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="2b2db-107">HoloLens 2 に配置すると、HoloLens によって認識されたサーフェスに対応する空間マッピングのメッシュが表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="2b2db-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="2b2db-108">さらに、手の追跡用の手と指のインジケーターと、アプリのパフォーマンスを監視するためのフレームレート カウンターも表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="2b2db-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="2b2db-109">目標</span><span class="sxs-lookup"><span data-stu-id="2b2db-109">Objectives</span></span>

* <span data-ttu-id="2b2db-110">HoloLens 開発用に Unity を構成する方法について学習する</span><span class="sxs-lookup"><span data-stu-id="2b2db-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="2b2db-111">アプリをビルドして HoloLens に配置する方法について学習する</span><span class="sxs-lookup"><span data-stu-id="2b2db-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="2b2db-112">HoloLens 2 デバイスで空間マッピング メッシュ、ハンド メッシュ、フレームレート カウンターを体験する</span><span class="sxs-lookup"><span data-stu-id="2b2db-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="2b2db-113">Unity プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="2b2db-113">Creating the Unity project</span></span>

<span data-ttu-id="2b2db-114">**Unity Hub** を起動し、 **[Projects]\(プロジェクト\)** タブを選択し、 **[New]\(新規\)** ボタンの横にある **下矢印** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b2db-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![[New]\(新規\) ボタンが強調表示されている Unity Hub](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="2b2db-116">「[前提条件](mr-learning-base-01.md#prerequisites)」に指定されている Unity の **バージョン** を、ドロップダウンで選択します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity Hub と新しいバージョン セレクター ドロップダウン](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="2b2db-118">Unity Hub で特定の Unity バージョンが利用できない場合は、Unity の<a href="https://unity3d.com/get-unity/download/archive" target="_blank">アーカイブのダウンロード</a>に関するページから、そのインストールを開始できます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="2b2db-119">[Create a new project]\(新規プロジェクトの作成\) ウィンドウで、以下のようにします。</span><span class="sxs-lookup"><span data-stu-id="2b2db-119">In the Create a new project window:</span></span>

* <span data-ttu-id="2b2db-120">**[Templates]\(テンプレート\)** が **3D** に設定されていることを確認します</span><span class="sxs-lookup"><span data-stu-id="2b2db-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="2b2db-121">"_MRTK チュートリアル_" など、適切な **[Project Name]\(プロジェクト名\)** を入力します</span><span class="sxs-lookup"><span data-stu-id="2b2db-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="2b2db-122">プロジェクトを格納するための適切な **[Location]\(場所\)** を選択します。たとえば、_D:\MixedRealityLearning_ など</span><span class="sxs-lookup"><span data-stu-id="2b2db-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="2b2db-123">**[Create]\(作成\)** ボタンをクリックして、新しい Unity プロジェクトを作成して起動します</span><span class="sxs-lookup"><span data-stu-id="2b2db-123">Click the **Create** button to create and launch your new Unity project</span></span>

![[Create a new project]\(新規プロジェクトの作成\) ウィンドウが設定された Unity Hub](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="2b2db-125">Windows で作業している場合は、255 文字の MAX_PATH 制限があります。</span><span class="sxs-lookup"><span data-stu-id="2b2db-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="2b2db-126">そのため、Unity プロジェクトはドライブのルートの近くに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b2db-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="2b2db-127">Unity によってプロジェクトが作成されるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-127">Wait for Unity to create the project:</span></span>

![新しいプロジェクトの作成が進行中の Unity](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="2b2db-129">ビルド プラットフォームを切り替える</span><span class="sxs-lookup"><span data-stu-id="2b2db-129">Switching the build platform</span></span>

<span data-ttu-id="2b2db-130">Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** を選択し、[Build Settings]\(ビルド設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity の [Build Settings...]\(ビルド設定...\) メニュー パス](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="2b2db-132">[Build Settings]\(ビルド設定\) ウィンドウで、 **[Universal Windows Platform]\(ユニバーサル Windows プラットフォーム\)** を選択して、 **[Switch Platform]\(プラットフォームの切り替え\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b2db-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![UWP が選択されてプラットフォームがスタンドアロンから切り替えられている Unity の [Build Settings]\(ビルド設定\) ウィンドウ](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="2b2db-134">Unity がプラットフォームの切り替えを完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-134">Wait for Unity to finish switching the platform:</span></span>

![プラットフォームの切り替えが進行中の Unity](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="2b2db-136">Unity でプラットフォームの切り替えが完了したら、赤色の **x** アイコンをクリックして、[Build Settings]\(ビルド設定\) ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![閉じるアイコンが強調表示されている Unity のビルド ウィンドウ](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="2b2db-138">TextMeshPro の重要なリソースをインポートする</span><span class="sxs-lookup"><span data-stu-id="2b2db-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="2b2db-139">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[TextMeshPro]**  >  **[Import TMP Essential Resources]\(TMP の重要なリソースをインポート\)** の順に選択して、[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Unity の [Import TMP Essential Resources]\(TMP の重要なリソースをインポート\) メニュー パス](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="2b2db-141">[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="2b2db-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity の TMP の重要なリソース インポート ウィンドウ](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="2b2db-143">TextMeshPro の重要なリソースは、MRTK の UI 要素で必要です。</span><span class="sxs-lookup"><span data-stu-id="2b2db-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="2b2db-144">ご自分のプロジェクトで MRTK の UI 要素を使用する予定がない場合は、この手順を省略できます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="2b2db-145">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="2b2db-145">Importing the Mixed Reality Toolkit</span></span>

### <a name="using-the-mixed-reality-feature-tool"></a><span data-ttu-id="2b2db-146">Mixed Reality Feature Tool の使用</span><span class="sxs-lookup"><span data-stu-id="2b2db-146">Using the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="2b2db-147">新しい Mixed Reality Feature Tool アプリケーションを使用して MRTK をインストールするには、[インストールと使用方法の手順](../welcome-to-mr-feature-tool.md)に関するページに従い、Mixed Reality Toolkit カテゴリの **Mixed Reality Toolkit Foundation** パッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-147">To install MRTK with our new Mixed Reality Feature Tool application, follow our [installation and usage instructions](../welcome-to-mr-feature-tool.md) and select the **Mixed Reality Toolkit Foundation** package in the Mixed Reality Toolkit category.</span></span>

### <a name="using-unity-packages"></a><span data-ttu-id="2b2db-148">Unity パッケージの使用</span><span class="sxs-lookup"><span data-stu-id="2b2db-148">Using Unity Packages</span></span>

<span data-ttu-id="2b2db-149">カスタム パッケージを使用して MRTK をインストールするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="2b2db-149">To install MRTK with a custom package:</span></span>

* [<span data-ttu-id="2b2db-150">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="2b2db-150">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.5.1/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage)

<span data-ttu-id="2b2db-151">Unity メニューで、 **[Assets]\(アセット\)**  >  **[Import Package]\(パッケージのインポート\)**  >  **[Custom Package...]\(カスタム パッケージ...\)** を選択して [Import package...]\(パッケージのインポート...\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-151">In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Unity のインポートの [Custom Package...]\(カスタム パッケージ...\) メニュー パス](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="2b2db-153">[Import package...]\(パッケージのインポート...\) ウィンドウで、ダウンロードした **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage** を選択し、 **[Open]\(開く\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2b2db-153">In the Import package... window, select the **Microsoft.MixedReality.Toolkit.Unity.Foundation.2.5.1.unitypackage** you downloaded and click the **Open** button:</span></span>

![Unity のカスタム パッケージのインポートの [Open]\(開く\) プロンプト ウィンドウ](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="2b2db-155">[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="2b2db-155">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity MRTK Foundation インポート ウィンドウ](images/mr-learning-base/base-02-section4-step1-3.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="2b2db-157">Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="2b2db-157">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="2b2db-158">1. MRTK プロジェクト コンフィギュレーター設定を適用する</span><span class="sxs-lookup"><span data-stu-id="2b2db-158">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="2b2db-159">Unity によって前のセクションからのパッケージのインポートが完了すると、[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-159">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="2b2db-160">表示されない場合は、 **[Mixed Reality Toolkit]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** に移動して手動で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-160">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Unity の [Configure Unity Project]\(Unity プロジェクトの構成\) メニュー パス](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="2b2db-162">[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウで、 **[Modify Configurations]\(構成の変更\)** セクションを展開し、他のすべてのオプションを確実にオンにしてから、 **[Apply]\(適用\)** ボタンをクリックして設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-162">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが表示された Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="2b2db-164">MRTK の既定の設定の適用はオプションですが、一部の推奨される Unity 設定を構成するのに役立つので強く推奨されます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-164">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="2b2db-165">[Set Single Pass Instanced rendering path]\(単一パスのインスタンス化レンダリング パスを設定する\): 同じ描画呼び出しで両方の目のレンダリング パイプラインを実行することにより、グラフィックスのパフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-165">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="2b2db-166">このトピックの詳細については、MRTK の「[パフォーマンス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)」ドキュメントの「[単一パス インスタンス化レンダリング](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b2db-166">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="2b2db-167">[Set default Spatial Awareness layer]\(既定の空間認識レイヤーを設定する\): 空間認識という名前の Unity レイヤーを作成し、空間認識メッシュにこのレイヤーを使用するように MRTK を構成します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-167">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="2b2db-168">Unity レイヤーの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">ワークスペースのカスタマイズ</a>に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b2db-168">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="2b2db-169">2.追加のプロジェクト設定を構成する</span><span class="sxs-lookup"><span data-stu-id="2b2db-169">2. Configure additional project settings</span></span>

<span data-ttu-id="2b2db-170">Unity メニューで、 **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクト設定...\)** を選択し、[Project Settings]\(プロジェクト設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-170">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

![Unity の [Project Settings...]\(プロジェクト設定...\) メニュー パス](images/mr-learning-base/base-02-section5-step2-1.png)

<span data-ttu-id="2b2db-172">[Project Settings]\(プロジェクトの設定\) ウィンドウで、 **[XR Plug-in Management]\(XR プラグイン管理\)**  >  **[Install XR Plug-in Management]\(XR プラグイン管理のインストール\)** を選択して、XR プラグイン管理をインストールします。</span><span class="sxs-lookup"><span data-stu-id="2b2db-172">In the Project Settings window, select **XR Plug-in Management** > **Install XR Plug-in Management**, to install XR Plug-in Management:</span></span>

![[XR Plug-in Management]\(XR プラグイン管理\) が選択されたプロジェクトの設定](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="2b2db-174">Unity による XR プラグイン管理のインストールが完了した後。</span><span class="sxs-lookup"><span data-stu-id="2b2db-174">After Unity has finished installing the XR Plug-in Management.</span></span> <span data-ttu-id="2b2db-175">ユニバーサル Windows プラットフォームの設定になっていることを確認し、[Initialize XR on Startup]\(起動時に XR を初期化する\) をオンにします。</span><span class="sxs-lookup"><span data-stu-id="2b2db-175">Ensure that you are in Universal Windows Platform settings and Check the Initialize XR on Startup.</span></span>

![Unity 構成 XR プラグインの管理](images/mr-learning-base/base-02-section5-step2-3.png)

<span data-ttu-id="2b2db-177">[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレイヤー\)**  >  **[XR Settings]\(XR 設定\)** の順に選択し、[ **+** ] アイコンをクリックします。Windows Mixed reality を選択して Windows Mixed Reality SDK を追加します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-177">In the Project Settings window, select **Player** > **XR Settings**, click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![Windows Mixed Reality SDK の追加が選択された Unity の XR 設定](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="2b2db-179">Unity によって Windows Mixed Reality SDK のインポートが完了すると、[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが再び表示されます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-179">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="2b2db-180">そうならない場合は、Unity メニューを使用してそれを開きます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-180">If it doesn't, use the Unity menu to open it.</span></span>

<span data-ttu-id="2b2db-181">[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウで、 **[Audio Spatializer]** ドロップダウンを使用して **[MS HRTF Spatializer]** を選択してから、 **[Apply]\(適用\)** ボタンをクリックしてこの設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-181">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![[Audio Spatializer] プロパティが強調表示されている [MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウ](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="2b2db-183">Audio Spatializer プロパティの設定はオプションですが、プロジェクトでのオーディオ エクスペリエンスが向上する場合があります。</span><span class="sxs-lookup"><span data-stu-id="2b2db-183">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="2b2db-184">MS HRTF Spatializer に設定した場合、Unity の AudioSource.spatialize プロパティが有効になっていると、この Spatializer プラグインが使用されます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-184">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="2b2db-185">このトピックの詳細については、<a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">立体オーディオのチュートリアル</a>に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b2db-185">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="2b2db-186">[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレーヤー\)**  >  **[XR Settings]\(XR 設定\)** を選択してから、 **[Depth Format]\(深度形式\)** ドロップダウンを使用して **[16-bit depth]\(16 ビット深度\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-186">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity で 16 ビット深度を有効にする](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="2b2db-188">深度形式を 16 ビットに減らすことはオプションですが、プロジェクトでのグラフィックス パフォーマンスの向上につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2b2db-188">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="2b2db-189">このトピックの詳細については、MRTK の「<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">パフォーマンス</a>」ドキュメントの「<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">深度バッファー共有 (HoloLens)</a>」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b2db-189">To learn more about this topic, you can refer to the   <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="2b2db-190">[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレイヤー\)**  >  **[Publishing Settings]\(公開の設定\)** の順に選択してから、 **[Package name]\(パッケージ名\)** フィールドに適切な名前 (たとえば _MRTKTutorials-GettingStarted_) を入力します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-190">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![パッケージ名が構成されている Unity の公開設定](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="2b2db-192">'パッケージ名' は、アプリの一意の識別子です。</span><span class="sxs-lookup"><span data-stu-id="2b2db-192">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="2b2db-193">以前にインストールしたアプリが上書きされないように、アプリを配置する前にこの識別子を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b2db-193">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="2b2db-194">'製品名' は、HoloLens の [スタート] メニューに表示される名前です。</span><span class="sxs-lookup"><span data-stu-id="2b2db-194">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="2b2db-195">開発中にアプリを見つけやすくするには、名前の前にアンダースコアを追加し、上部にくるように並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-195">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="2b2db-196">シーンを作成して構成する</span><span class="sxs-lookup"><span data-stu-id="2b2db-196">Creating and configuring the scene</span></span>

<span data-ttu-id="2b2db-197">Unity メニューで、 **[File]\(ファイル\)**  >  **[New Scene]\(新しいシーン\)** の順に選択して新しいシーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-197">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Unity の [New Scene]\(新しいシーン\) メニュー パス](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="2b2db-199">Unity メニューで、 **[Mixed Reality Toolkit]**  >  **[Add to Scene and Configure...]\(シーンに追加して構成する...\)** の順に選択して、MRTK を現在のシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-199">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity の [Add to Scene and Configure...]\(シーンに追加して構成する...\) メニュー パス](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="2b2db-201">[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択したままとし、[Inspector]\(インスペクター\) ウィンドウで、**MixedRealityToolkit** 構成プロファイルが **DefaultMixedRealityToolkitConfigurationProfile** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-201">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![DefaultMixedRealityTookitConfigurationProfile が選択された Unity MixedRealityToolkit コンポーネント](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="2b2db-203">Unity メニューで、 **[File]\(ファイル\)**  >  **[Save As...]\(名前を付けて保存...\)** を選択して [Save Scene]\(シーンの保存\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-203">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity の [Save As...]\(名前を付けて保存...\) メニュー パス](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="2b2db-205">[Save Scene]\(シーンの保存\) ウィンドウで、プロジェクトの **[Scenes]\(シーン\)** フォルダーに移動し、シーンに適切な名前を付け (たとえば、_GettingStarted_)、 **[Save]\(保存\)** ボタンをクリックしてシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-205">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![Unity のシーン保存の [Save]\(保存\) プロンプト ウィンドウ](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="2b2db-207">HoloLens 2 デバイス用にアプリケーションをビルドする</span><span class="sxs-lookup"><span data-stu-id="2b2db-207">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="2b2db-208">1.Unity プロジェクトのビルド</span><span class="sxs-lookup"><span data-stu-id="2b2db-208">1. Build the Unity project</span></span>

<span data-ttu-id="2b2db-209">Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** を選択し、[Build Settings]\(ビルド設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-209">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="2b2db-210">[Build Settings]\(ビルド設定\) ウィンドウで、 **[Add Open Scenes]\(開いているシーンを追加する\)** ボタンをクリックして、 **[Scenes In Build]\(ビルド内のシーン\)** リストの現在のシーンを追加します。次に **[Build]\(ビルド\)** ボタンをクリックして、[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-210">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![UWP が選択されている [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="2b2db-212">[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウで、ビルドを格納する適切な場所 (たとえば _D:\MixedRealityLearning\Builds_) を選択し、新しいフォルダーを作成して適切な名前 (たとえば _GettingStarted_) を付け、 **[Select Folder]\(フォルダーの選択\)** ボタンをクリックしてビルド処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-212">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![[フォルダーの選択] プロンプト ウィンドウが表示されている [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="2b2db-214">Unity がビルド処理を完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-214">Wait for Unity to finish the build process:</span></span>

![ビルド処理が進行中の Unity](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="2b2db-216">2.アプリのビルドと配置</span><span class="sxs-lookup"><span data-stu-id="2b2db-216">2. Build and deploy the application</span></span>

<span data-ttu-id="2b2db-217">ビルド処理が完了すると、お客様がビルドを格納した場所を開くように Unity から Windows ファイル エクスプローラーに指示が出されます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-217">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="2b2db-218">フォルダー内を移動し、ソリューション ファイルをダブルクリックして Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-218">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![新しく作成された Visual Studio ソリューションが選択された Windows エクスプローラー](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="2b2db-220">Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、「 **[ツールのインストール](../../install-the-tools.md)** 」ドキュメントで示されている、前提条件となるすべてのコンポーネントが用意できていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2b2db-220">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="2b2db-221">**[マスター]** または **[リリース]** 構成を選択し、 **[ARM64]** アーキテクチャを選択し、ターゲットとして **[デバイス]** を選択して、HoloLens 用に Visual Studio を構成します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-221">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![HoloLens 2 に配置するように構成された Visual Studio](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="2b2db-223">HoloLens (第 1 世代) に配置する場合は、**x86** アーキテクチャを選択します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-223">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="2b2db-224">HoloLens の場合、通常は ARM アーキテクチャ用にビルドします。</span><span class="sxs-lookup"><span data-stu-id="2b2db-224">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="2b2db-225">ただし、Unity 2019.3 には、Visual Studio で ARM をビルド アーキテクチャとして選択した場合にエラーを引き起こす<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>既知の問題</strong></a>が存在します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-225">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="2b2db-226">推奨される回避策は、ARM64 用にビルドすることです。</span><span class="sxs-lookup"><span data-stu-id="2b2db-226">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="2b2db-227">それがオプションでない場合は **[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\) > [Player]\(プレイヤー\) > [Other Settings]\(他の設定\)** の順に選択して、 **[Graphics Jobs]\(グラフィック ジョブ\)** を無効にします。</span><span class="sxs-lookup"><span data-stu-id="2b2db-227">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="2b2db-228">ターゲット オプションとして [デバイス] が表示されない場合は、Visual Studio ソリューションのスタートアップ プロジェクトを IL2CPP プロジェクトから UWP プロジェクトに変更することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="2b2db-228">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="2b2db-229">それを行うには、ソリューション エクスプローラーで、[YourProjectName (Universal Windows)]\(YourProjectName (ユニバーサル Windows)\) を右クリックし、 **[スタートアップ プロジェクトに設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-229">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="2b2db-230">ご利用のコンピューターに HoloLens を接続し、 **[デバッグ]**  >  **[デバッグなしで開始]** の順に選択して、ご利用のデバイス用にビルドして配置します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-230">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio の [デバッグなしで開始] メニュー パス](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="2b2db-232">デバイスに対してビルドする前に、デバイスが開発者モードになっており、かつ、開発コンピューターとペアリングされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b2db-232">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="2b2db-233">この両方のステップを完了するには、[こちらの手順](../../platform-capabilities-and-apis/using-visual-studio.md)に従います。</span><span class="sxs-lookup"><span data-stu-id="2b2db-233">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="2b2db-234">また、[HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) に配置することも、サイドローディング用の[アプリ パッケージ](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-234">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="2b2db-235">[デバッグなしで開始] を使用すると、Visual Studio デバッガーがアタッチされていない状態でも、ご利用のデバイス上でアプリが自動的に起動します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-235">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="2b2db-236">アプリを自動的に起動せずに、ご利用のデバイスに配置するには、 **[ビルド] > [ソリューションの配置]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-236">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="2b2db-237">アプリでは、診断プロファイラーが表示される場合があります。このオン、オフを切り替えるには、音声コマンド **Toggle Diagnostics** を使用します。</span><span class="sxs-lookup"><span data-stu-id="2b2db-237">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="2b2db-238">アプリへの変更がパフォーマンスに影響を与える可能性がある場合は、開発中の多くは、プロファイラーを表示したままにしておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2b2db-238">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="2b2db-239">たとえば、HoloLens アプリは [60 FPS で継続的に実行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b2db-239">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="2b2db-240">結論</span><span class="sxs-lookup"><span data-stu-id="2b2db-240">Congratulations</span></span>

<span data-ttu-id="2b2db-241">これで、最初の HoloLens アプリが展開されました。</span><span class="sxs-lookup"><span data-stu-id="2b2db-241">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="2b2db-242">手順に従うと、HoloLens によって認識されたサーフェイスに対応する空間マッピングのメッシュが表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="2b2db-242">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="2b2db-243">さらに、手の追跡用の手と指のインジケーターと、アプリのパフォーマンスを監視するためのフレームレート カウンターも表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="2b2db-243">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="2b2db-244">これらの機能は、MRTK に含まれている基本的なもののほんの一部です。</span><span class="sxs-lookup"><span data-stu-id="2b2db-244">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="2b2db-245">次のチュートリアルでは、コンテンツをシーンに追加して、HoloLens と MRTK の機能を調べます。</span><span class="sxs-lookup"><span data-stu-id="2b2db-245">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2b2db-246">次のチュートリアル:3. MRTK プロファイルの構成</span><span class="sxs-lookup"><span data-stu-id="2b2db-246">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)