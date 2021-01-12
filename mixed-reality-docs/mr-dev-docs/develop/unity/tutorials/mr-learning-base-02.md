---
title: プロジェクトの初期化と最初のアプリケーションの配置
description: このコースでは、Mixed Reality Toolkit (MRTK) 用に Unity プロジェクトを構成する方法と、それを HoloLens 2 に配置する方法について説明します。
author: jessemcculloch
ms.author: v-vtieto
ms.date: 12/30/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 2ce119e1dd18eacf02088d00e99fb70d06bf956e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008222"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="1f457-104">2. プロジェクトの初期化と最初のアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="1f457-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="1f457-105">このチュートリアルでは、新しい Unity プロジェクトを作成し、それを <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality ツールキット (MRTK)</a> 開発用に構成し、MRTK をインポートする方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="1f457-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="1f457-106">また、Visual Studio で基本的な Unity シーンを構成およびビルドし、HoloLens 2 に配置する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="1f457-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="1f457-107">HoloLens 2 に配置すると、HoloLens によって認識されたサーフェスに対応する空間マッピングのメッシュが表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="1f457-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="1f457-108">さらに、手の追跡用の手と指のインジケーターと、アプリのパフォーマンスを監視するためのフレームレート カウンターも表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="1f457-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="1f457-109">目標</span><span class="sxs-lookup"><span data-stu-id="1f457-109">Objectives</span></span>

* <span data-ttu-id="1f457-110">HoloLens 開発用に Unity を構成する方法について学習する。</span><span class="sxs-lookup"><span data-stu-id="1f457-110">Learn how to configure Unity for HoloLens development.</span></span>
* <span data-ttu-id="1f457-111">アプリをビルドして HoloLens に配置する方法について学習する。</span><span class="sxs-lookup"><span data-stu-id="1f457-111">Learn how to build and deploy your app to HoloLens.</span></span>
* <span data-ttu-id="1f457-112">HoloLens 2 デバイスで空間マッピング メッシュ、ハンド メッシュ、フレームレート カウンターを体験する。</span><span class="sxs-lookup"><span data-stu-id="1f457-112">Experience the spatial mapping mesh, hand meshes, and  framerate counter on your HoloLens 2 device.</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="1f457-113">Unity プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="1f457-113">Creating the Unity project</span></span>

1. <span data-ttu-id="1f457-114">**Unity Hub** を起動し、 **[Projects]\(プロジェクト\)** タブを選択してから、 **[New]\(新規\)** ボタンの横にある **下矢印** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f457-114">Launch **Unity Hub**, select the **Projects** tab, and then click the **down arrow** next to the **New** button:</span></span>

![[New]\(新規\) ボタンの下矢印が強調表示されている Unity Hub](images/mr-learning-base/base-02-section1-step1-1.png)

2. <span data-ttu-id="1f457-116">ドロップダウン メニューで、「[前提条件](mr-learning-base-01.md#prerequisites)」に指定されている Unity のバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-116">In the dropdown menu, select the Unity version specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity のバージョンを選択する](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="1f457-118">Unity Hub で特定の Unity バージョンが利用できない場合は、Unity の<a href="https://unity3d.com/get-unity/download/archive" target="_blank">アーカイブのダウンロード</a>に関するページから、そのインストールを開始できます。</span><span class="sxs-lookup"><span data-stu-id="1f457-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

3. <span data-ttu-id="1f457-119">**[Create a new project]\(新規プロジェクトの作成\)** ウィンドウで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1f457-119">In the **Create a new project** window, do the following:</span></span>

    * <span data-ttu-id="1f457-120">**[Templates]\(テンプレート\)** が **[3D]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1f457-120">Ensure **Templates** is set to **3D**.</span></span>
    * <span data-ttu-id="1f457-121">**[Project Name]\(プロジェクト名\)** ボックスに、プロジェクトの適切な名前 (「MRTK Tutorials」など) を入力します。</span><span class="sxs-lookup"><span data-stu-id="1f457-121">In the **Project Name** box, enter a suitable name for your project (for example, "MRTK Tutorials").</span></span>
    * <span data-ttu-id="1f457-122">**[Location]\(保存先\)** の横にある 3 つのドット ボタンをクリックして、プロジェクトを保存するフォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1f457-122">Click the three-dot button next to **Location**, and then navigate to the folder where you want to save your project.</span></span>

> [!CAUTION]
> <span data-ttu-id="1f457-123">Windows で作業している場合は、255 文字の MAX_PATH 制限があります。</span><span class="sxs-lookup"><span data-stu-id="1f457-123">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="1f457-124">そのため、Unity プロジェクトはドライブのルートの近くに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f457-124">Because of this, you should save the Unity project close to the root of the drive.</span></span>

    * <span data-ttu-id="1f457-125">**[作成]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f457-125">Click the **Create** button.</span></span> <span data-ttu-id="1f457-126">すると、新しい Unity プロジェクトが作成されて起動します。</span><span class="sxs-lookup"><span data-stu-id="1f457-126">This creates and launches your new Unity project.</span></span>

![[Create a new project]\(新規プロジェクトの作成\) ウィンドウが設定された Unity Hub](images/mr-learning-base/base-02-section1-step1-3.png)

<span data-ttu-id="1f457-128">ステータス バーに進行状況が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1f457-128">The status bar keeps you updated on your progress.</span></span>

![プロジェクトの作成状態を表示する Unity の進行状況バー](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="1f457-130">ビルド プラットフォームを切り替える</span><span class="sxs-lookup"><span data-stu-id="1f457-130">Switching the build platform</span></span>

1. <span data-ttu-id="1f457-131">メニュー バーで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-131">On the menu bar, select **File** > **Build Settings...**</span></span>

![Unity の [Build Settings...]\(ビルド設定...\) メニュー パス](images/mr-learning-base/base-02-section2-step1-1.png)

2. <span data-ttu-id="1f457-133">**[Build Settings]\(ビルド設定\)** ウィンドウで、 **[Universal Windows Platform]\(ユニバーサル Windows プラットフォーム\)** を選択して、 **[Switch Platform]\(プラットフォームの切り替え\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f457-133">In the **Build Settings** window, select **Universal Windows Platform** and then click the **Switch Platform** button:</span></span>

![UWP が選択されてプラットフォームがスタンドアロンから切り替えられている Unity の [Build Settings]\(ビルド設定\) ウィンドウ](images/mr-learning-base/base-02-section2-step1-2.png)

3. <span data-ttu-id="1f457-135">Unity でプラットフォームの切り替えが完了するのを待ってから、 **[Build Settings]\(ビルド設定\)** ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1f457-135">Wait for Unity to finish switching the platform, and then close the **Build Settings** window.</span></span>

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="1f457-136">TextMeshPro の重要なリソースをインポートする</span><span class="sxs-lookup"><span data-stu-id="1f457-136">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="1f457-137">TextMeshPro の重要なリソースは、MRTK の UI 要素で必要です。</span><span class="sxs-lookup"><span data-stu-id="1f457-137">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="1f457-138">プロジェクトで MRTK の UI 要素を使用する予定がない場合は、この手順を省略できます。</span><span class="sxs-lookup"><span data-stu-id="1f457-138">If you are not planning to use MRTK's UI elements in your project, you can skip this step.</span></span>

1. <span data-ttu-id="1f457-139">メニュー バーで、 **[Window]\(ウィンドウ\)**  >  **[TextMeshPro]**  >  **[Import TMP Essential Resources]\(TMP の重要なリソースをインポート\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-139">On the menu bar, select **Window** > **TextMeshPro** > **Import TMP Essential Resources**.</span></span>

![Unity の [Import TMP Essential Resources]\(TMP の重要なリソースをインポート\) メニュー パス](images/mr-learning-base/base-02-section3-step1-1.png)

2. <span data-ttu-id="1f457-141">**[Import Unity Package]\(Unity パッケージのインポート\)** ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認したら、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="1f457-141">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets:</span></span>

![Unity の TMP の重要なリソース インポート ウィンドウ](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="1f457-143">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="1f457-143">Importing the Mixed Reality Toolkit</span></span>

1. <span data-ttu-id="1f457-144">Unity カスタム パッケージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="1f457-144">Download the Unity custom package:</span></span>

    [<span data-ttu-id="1f457-145">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="1f457-145">Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/releases/download/v2.4.0/Microsoft.MixedReality.Toolkit.Unity.Foundation.2.4.0.unitypackage)

2. <span data-ttu-id="1f457-146">メニュー バーで、 **[Assets]\(アセット\)**  >  **[Import Package]\(パッケージのインポート\)**  >  **[Custom Package...]\(カスタム パッケージ...\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-146">On the menu bar, select **Assets** > **Import Package** > **Custom Package...**.</span></span>
3. <span data-ttu-id="1f457-147">**[Import Package...]\(パッケージのインポート...\)** ダイアログで、ダウンロードしたパッケージの保存先に移動し、そのパッケージを選択して、 **[Open]\(開く\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f457-147">In the **Import package...** dialog, navigate to the location of the package you just downloaded, then select it, and then click the **Open** button.</span></span>
4. <span data-ttu-id="1f457-148">**[Import Unity Package]\(Unity パッケージのインポート\)** ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認したら、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="1f457-148">In the **Import Unity Package** window, click the **All** button to ensure that all the assets are selected, and then click the **Import** button to import the assets.</span></span>

## <a name="selecting-mrtk-and-project-settings"></a><span data-ttu-id="1f457-149">MRTK とプロジェクトの設定を選択する</span><span class="sxs-lookup"><span data-stu-id="1f457-149">Selecting MRTK and project settings</span></span>

<span data-ttu-id="1f457-150">Unity によって前のセクションからのパッケージのインポートが完了すると、 **[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\)** ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1f457-150">After Unity has finished importing the package from the previous section, the **MRTK Project Configurator** window should appear.</span></span> <span data-ttu-id="1f457-151">表示されない場合は、 **[Mixed Reality Toolkit]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** に移動して手動で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="1f457-151">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Unity の [Configure Unity Project]\(Unity プロジェクトの構成\) メニュー パス](images/mr-learning-base/base-02-section5-step1-1.png)

1. <span data-ttu-id="1f457-153">**[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\)** ウィンドウで、必要に応じて **[Modify Configurations]\(構成の変更\)** セクションを展開し、すべてのオプションが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1f457-153">In the **MRTK Project Configurator** window, expand the **Modify Configurations** section, if necessary, and then ensure that all options are selected.</span></span>

![[Modify Configurations]\(構成の変更\) が表示されている Unity の [MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウ](images/mr-learning-base/base-02-section5-step1-2.png)

2. <span data-ttu-id="1f457-155">設定を適用するには、 **[Apply]\(適用\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f457-155">To apply the settings, click the **Apply** button.</span></span>

![MRTK の [Apply]\(適用\) ボタン](images/mr-learning-base/apply.png)

> [!NOTE]
> <span data-ttu-id="1f457-157">新しいシステムはこのチュートリアル シリーズに対して[推奨される Unity および MRTK のバージョン](mr-learning-base-01.md#prerequisites)と完全には互換性がないため、新しい XR プラグイン システムではなく、Unity の組み込みのレガシ XR を使用しています。</span><span class="sxs-lookup"><span data-stu-id="1f457-157">You are using Unity's built-in legacy XR instead of the new XR Plugin System because the new system is not fully compatible with the [recommended Unity and MRTK versions](mr-learning-base-01.md#prerequisites) for this tutorial series.</span></span> <span data-ttu-id="1f457-158">組み込みの XR は非推奨であることを示す警告が表示されても、無視してかまいません。</span><span class="sxs-lookup"><span data-stu-id="1f457-158">If you see any warnings about built-in XR being deprecated, you can ignore them.</span></span>

> [!TIP]
> <span data-ttu-id="1f457-159">MRTK の既定の設定の適用はオプションですが、一部の推奨される Unity 設定を構成するのに役立つので強く推奨されます。</span><span class="sxs-lookup"><span data-stu-id="1f457-159">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>
>
> * <span data-ttu-id="1f457-160">[Enable legacy XR]\(レガシ XR を有効にする\): プロジェクトの VR を有効にします。</span><span class="sxs-lookup"><span data-stu-id="1f457-160">Enable legacy XR: Enables VR for the project.</span></span>
> * <span data-ttu-id="1f457-161">[Set Single Pass Instanced rendering path]\(単一パスのインスタンス化レンダリング パスを設定する\): 同じ描画呼び出しで両方の目のレンダリング パイプラインを実行することにより、グラフィックスのパフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="1f457-161">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="1f457-162">このトピックの詳細については、MRTK の「[パフォーマンス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)」ドキュメントの「[単一パス インスタンス化レンダリング](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f457-162">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="1f457-163">[Set default Spatial Awareness layer]\(既定の空間認識レイヤーを設定する\): 空間認識という名前の Unity レイヤーを作成し、空間認識メッシュにこのレイヤーを使用するように MRTK を構成します。</span><span class="sxs-lookup"><span data-stu-id="1f457-163">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="1f457-164">Unity レイヤーの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">ワークスペースのカスタマイズ</a>に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f457-164">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

3. <span data-ttu-id="1f457-165">メニュー バーで、 **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクト設定...\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-165">On the menu bar, select **Edit** > **Project Settings...** .</span></span>

4. <span data-ttu-id="1f457-166">**[Project Settings...]\(プロジェクト設定...\)** ウィンドウで、 **[Player]\(プレイヤー\)** を選択し、 **[XR Settings]\(XR 設定\)** ドロップダウンをクリックして、 **[Virtual Reality Supported]\(仮想現実のサポート\)** の横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1f457-166">In the **Project Settings** window, select **Player**, then click the **XR Settings** dropdown, and then select the box next to **Virtual Reality Supported**:</span></span>

![[Virtual Reality Supported]\(仮想現実のサポート\) が表示されている Unity の XR 設定](images/mr-learning-base/base-02-section5-step2-2.png)

<span data-ttu-id="1f457-168">これにより、Windows Mixed Reality SDK がインポートされます。</span><span class="sxs-lookup"><span data-stu-id="1f457-168">This imports the Windows Mixed Reality SDK:</span></span>

![[Virtual Reality SDKs]\(仮想現実 SDK\) が表示されている Unity の XR 設定](images/mr-learning-base/mixed-reality-sdk.png)

<span data-ttu-id="1f457-170">Unity によって Windows Mixed Reality SDK のインポートが完了すると、 **[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\)** ウィンドウが再び表示されます。</span><span class="sxs-lookup"><span data-stu-id="1f457-170">After Unity has finished importing the Windows Mixed Reality SDK, the **MRTK Project Configurator** window should appear again.</span></span> <span data-ttu-id="1f457-171">表示されない場合は、 **[Mixed Reality Toolkit]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** の順に選択して、ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="1f457-171">If it doesn't, select **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project** to open it.</span></span>

5. <span data-ttu-id="1f457-172">**[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\)** ウィンドウで、 **[Audio spatializer]\(オーディオ スペーシャライザー\)** ドロップダウンをクリックし、 **[MS HRTF Spatializer]\(MS HRTF スペーシャライザー\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-172">In the **MRTK Project Configurator** window, click the **Audio spatializer** dropdown, and then select **MS HRTF Spatializer**.</span></span>

![[Audio spatializer]\(オーディオ スペーシャライザー\) オプションが表示されたプロジェクト設定](images/mr-learning-base/base-02-section5-step2-3.png)

6. <span data-ttu-id="1f457-174">**[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f457-174">Click the **Apply** button.</span></span> <span data-ttu-id="1f457-175">これにより、 **[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\)** ウィンドウが閉じます。</span><span class="sxs-lookup"><span data-stu-id="1f457-175">This closes the **MRTK Project Configurator** window.</span></span>

    > [!TIP]
    > <span data-ttu-id="1f457-176">Audio Spatializer プロパティの設定はオプションですが、プロジェクトでのオーディオ エクスペリエンスが向上する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1f457-176">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="1f457-177">MS HRTF Spatializer に設定した場合、Unity の AudioSource.spatialize プロパティが有効になっていると、この Spatializer プラグインが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1f457-177">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="1f457-178">このトピックの詳細については、立体オーディオのチュートリアルに関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f457-178">To learn more about this topic, you can refer to the Spatial audio tutorials.</span></span>

7. <span data-ttu-id="1f457-179">**[Project Settings]\(プロジェクト設定\)** ウィンドウで、 **[Depth Format]\(深度形式\)** ドロップダウンをクリックして、 **[16-bit depth]\(16 ビット深度\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-179">In the **Project Settings** window, click the **Depth Format** dropdown, and then select **16-bit depth**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-4.png" alt-text="[16-bit depth]\(16 ビット深度\) が選択された Unity の XR 設定":::

    > [!TIP]
    > <span data-ttu-id="1f457-181">深度形式を 16 ビットに減らすことはオプションですが、プロジェクトでのグラフィックス パフォーマンスの向上につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1f457-181">Reducing the Depth Format to 16-bit is optional but may help improve graphics performance in your project.</span></span> <span data-ttu-id="1f457-182">このトピックの詳細については、MRTK の「[パフォーマンス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)」ドキュメントの「[深度バッファー共有 (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f457-182">To learn more about this topic, you can refer to the [Depth buffer sharing (HoloLens)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>

8. <span data-ttu-id="1f457-183">**[Publishing Settings]\(公開設定\)** ドロップダウンをクリックし、 **[Package name]\(パッケージ名\)** ボックスに適切な名前 (「MRTK-Tutorials-Getting-Started」など) を入力します。</span><span class="sxs-lookup"><span data-stu-id="1f457-183">Click the **Publishing Settings** drop-down, and then in the **Package name** box, enter a suitable name (for example, "MRTK-Tutorials-Getting-Started").</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section5-step2-5.png" alt-text="パッケージ名が構成されている Unity の公開設定":::

    <span data-ttu-id="1f457-185">**パッケージ名と製品名**</span><span class="sxs-lookup"><span data-stu-id="1f457-185">**Package Name and Product Name**</span></span>

    - <span data-ttu-id="1f457-186">'パッケージ名' は、アプリの一意の識別子です。</span><span class="sxs-lookup"><span data-stu-id="1f457-186">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="1f457-187">以前にインストールしたアプリが上書きされないようにするため、アプリを配置する前にこの識別子を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f457-187">You should create this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>
    - <span data-ttu-id="1f457-188">'製品名' は、HoloLens の [スタート] メニューに表示される名前です。</span><span class="sxs-lookup"><span data-stu-id="1f457-188">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="1f457-189">名前の前にアンダースコアを追加すると、並べ替えの先頭に表示されるので、開発中にアプリを見つけやすくなります。</span><span class="sxs-lookup"><span data-stu-id="1f457-189">To make the app easier to locate during development, you can add an underscore in front of the name to sort it to the top.</span></span>

    :::image type="content" source="images/mr-learning-base/product-name.png" alt-text="製品名が構成されている Unity のプロジェクト設定":::

9. <span data-ttu-id="1f457-191">**[Project Settings]\(プロジェクト設定\)** ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1f457-191">Close the **Project Settings** window.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="1f457-192">シーンを作成して構成する</span><span class="sxs-lookup"><span data-stu-id="1f457-192">Creating and configuring the scene</span></span>

1. <span data-ttu-id="1f457-193">メニュー バーで、 **[File]\(ファイル\)**  >  **[New Scene]\(新しいシーン\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-193">On the menu bar, select **File** > **New Scene**.</span></span>
2. <span data-ttu-id="1f457-194">シーンに MRTK を追加するには、Unity メニューで、 **[Mixed Reality Toolkit]**  >  **[Add to Scene and Configure...]\(シーンに追加して構成する...\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-194">To add the MRTK to the scene, on the menu bar, select **Mixed Reality Toolkit** > **Add to Scene and Configure...**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-2.png" alt-text="Unity の [Add to Scene and Configure...]\(シーンに追加して構成する...\) メニュー パス":::

3. <span data-ttu-id="1f457-196">**[Hierarchy]\(階層\)** ウィンドウで、 **[MixedRealityToolkit]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1f457-196">In the **Hierarchy** window, ensure that **MixedRealityToolkit** is selected.</span></span>

    :::image type="content" source="images/mr-learning-base/select-mixed-reality-toolkit.png" alt-text="[MixedRealityTookit] が選択されていることを確認する":::

4. <span data-ttu-id="1f457-198">**[Inspector]\(インスペクター\)** ウィンドウの **[MixedRealityToolkit]** セクションで、構成プロファイルが **[DefaultMixedRealityToolkitConfigurationProfile]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1f457-198">In the **Inspector** window's **MixedRealityToolkit** section, verify that the configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-3.png" alt-text="[DefaultMixedRealityTookitConfigurationProfile] が選択された Unity の MixedRealityToolkit コンポーネント":::

    > [!IMPORTANT]
    > <span data-ttu-id="1f457-200">通常、HoloLens 向けの開発時には DefaultHoloLens2ConfigurationProfile を使用します。</span><span class="sxs-lookup"><span data-stu-id="1f457-200">Typically, you will use the DefaultHoloLens2ConfigurationProfile when developing for HoloLens.</span></span> <span data-ttu-id="1f457-201">ただし、このチュートリアルでは DefaultMixedRealityToolkitConfigurationProfile を使用します。</span><span class="sxs-lookup"><span data-stu-id="1f457-201">However, for this tutorial, you will use the DefaultMixedRealityToolkitConfigurationProfile.</span></span> <span data-ttu-id="1f457-202">次のチュートリアル (「[MRTK プロファイルの構成](mr-learning-base-03.md)」) では、DefaultHoloLens2ConfigurationProfile に変更します。</span><span class="sxs-lookup"><span data-stu-id="1f457-202">In the next tutorial, [Configuring the MRTK profiles](mr-learning-base-03.md), you will change to the DefaultHoloLens2ConfigurationProfile.</span></span>

5. <span data-ttu-id="1f457-203">メニュー バーで、 **[File]\(ファイル\)**  >  **[Save As...]\(名前を付けて保存...\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-203">On the menu bar, select **File** > **Save As...**</span></span>
6. <span data-ttu-id="1f457-204">**[Save Scene]\(シーンの保存\)** ダイアログで、プロジェクトの **[Scenes]\(シーン\)** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1f457-204">In the **Save Scene** dialog, navigate to your project's **Scenes** folder.</span></span> <span data-ttu-id="1f457-205">**[File name]\(ファイル名\)** ボックスで、シーンに適切な名前 (「\_GettingStarted\_」など) を指定し、 **[Save]\(保存\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f457-205">In the **File name** box, give your scene a suitable name (for example, "\_GettingStarted\_"), and then click the **Save** button.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section6-step1-5.png" alt-text="Unity のシーン保存の [Save]\(保存\) プロンプト ウィンドウ":::

## <a name="building-and-deploying-to-your-hololens-2"></a><span data-ttu-id="1f457-207">HoloLens 2 へのビルドと配置</span><span class="sxs-lookup"><span data-stu-id="1f457-207">Building and deploying to your HoloLens 2</span></span>

> <span data-ttu-id="1f457-208">デバイスにビルドする前に、次のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="1f457-208">Before building to your device, confirm the following:</span></span>
- <span data-ttu-id="1f457-209">デバイスが開発者モードである。</span><span class="sxs-lookup"><span data-stu-id="1f457-209">Your device is in Developer Mode.</span></span>
- <span data-ttu-id="1f457-210">デバイスが開発用コンピューターとペアリングされている。</span><span class="sxs-lookup"><span data-stu-id="1f457-210">Your device is paired with your development computer.</span></span> <span data-ttu-id="1f457-211">ペアリングされていない場合、ビルド プロセス中に、次のダイアログ ボックスが Visual Studio に表示されます。</span><span class="sxs-lookup"><span data-stu-id="1f457-211">If it's not, you will see the following dialog box in Visual Studio during the build process:</span></span>

![ペアリング デバイスの PIN の入力](images/mr-learning-base/pin-request.png)

 <span data-ttu-id="1f457-213">これらの手順の詳細については、「[Visual Studio を使用した配置とデバッグ](../../platform-capabilities-and-apis/using-visual-studio.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f457-213">To learn more about both of these steps, see [Using Visual Studio to deploy and debug](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

1. <span data-ttu-id="1f457-214">メニュー バーで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-214">On the menu bar, select **File** > **Build Settings...**.</span></span>
2. <span data-ttu-id="1f457-215">**[Build Settings]\(ビルドの設定\)** ウィンドウで、 **[Add Open Scenes]\(オープン シーンの追加\)** ボタンをクリックして、現在のシーンを **[Scenes in Build]\(ビルド内のシーン\)** リストに追加します。</span><span class="sxs-lookup"><span data-stu-id="1f457-215">In the **Build Settings** window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list.</span></span>

![現在のシーンを [Scenes in Build]\(ビルド内のシーン\) リストに追加](images/mr-learning-base/base-02-section7-step1-1.png)

3. <span data-ttu-id="1f457-217">**[ビルド]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1f457-217">Click the **Build** button.</span></span>

    :::image type="content" source="images/mr-learning-base/build-button.png" alt-text="[ビルド] ボタンをクリックします。":::

4. <span data-ttu-id="1f457-219">**[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\)** ダイアログで、ビルドを格納するのに適した保存先を選択します (たとえば、"MRTK Tutorials" フォルダーに "Builds" フォルダーを作成することもできます)。</span><span class="sxs-lookup"><span data-stu-id="1f457-219">In the **Build Universal Windows Platform** dialog, choose a suitable location to store your build (for example, you may want to create a "Builds" folder in your "MRTK Tutorials" folder).</span></span> <span data-ttu-id="1f457-220">新しいフォルダーを作成して、適切な名前 ("GettingStarted" など) を指定し、そのフォルダーを選択します。次に **[Select Folder]\(フォルダーの選択\)** ボタンをクリックして、ビルド プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="1f457-220">Create a new folder and give it a suitable name (for example, "GettingStarted"), then select the folder, and then click the **Select Folder** button to start the build process.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-2.png" alt-text="ビルド フォルダーが表示されている Unity の [Build]\(ビルド\) ウィンドウ":::

    <span data-ttu-id="1f457-222">ステータス バーが表示され、ビルドの進行状況が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1f457-222">A status bar appears and keeps you updated on your build progress.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section7-step1-3.png" alt-text="進行中の Unity のビルド プロセス":::

    > [!TIP]
    > <span data-ttu-id="1f457-224">また、[HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) に配置することも、サイドローディング用の[アプリ パッケージ](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1f457-224">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

5. <span data-ttu-id="1f457-225">ビルド プロセスが完了したら、エクスプローラーで、ビルドを格納した保存先に移動し、ソリューション ファイルをダブルクリックして Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="1f457-225">When the build process has completed, in File Explorer, navigate to the location where you stored the build, and then double-click the solution file to open it in Visual Studio:</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-1.png" alt-text="新しく作成された Visual Studio のソリューション ファイルが選択されたエクスプローラー":::

    > [!NOTE]
    > <span data-ttu-id="1f457-227">Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、「 **[ツールのインストール](../../install-the-tools.md)** 」ドキュメントで示されている、前提条件となるすべてのコンポーネントが用意できていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1f457-227">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

6. <span data-ttu-id="1f457-228">**[マスター]** または **[リリース]** 構成を選択し、 **[ARM64]** アーキテクチャを選択し、ターゲットとして **[デバイス]** を選択して、HoloLens 用に Visual Studio を構成します。</span><span class="sxs-lookup"><span data-stu-id="1f457-228">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as the target.</span></span>

    > [!TIP]
    > <span data-ttu-id="1f457-229">HoloLens (第 1 世代) に配置する場合は、**x86** アーキテクチャを選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-229">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-2.png" alt-text="HoloLens 2 に配置するように構成された Visual Studio":::

    > [!NOTE]
    > <span data-ttu-id="1f457-231">HoloLens の場合、通常は ARM アーキテクチャ用にビルドします。</span><span class="sxs-lookup"><span data-stu-id="1f457-231">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="1f457-232">ただし、Unity 2019.3 には、Visual Studio で ARM をビルド アーキテクチャとして選択した場合にエラーを引き起こす<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>既知の問題</strong></a>が存在します。</span><span class="sxs-lookup"><span data-stu-id="1f457-232">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="1f457-233">推奨される回避策は、ARM64 用にビルドすることです。</span><span class="sxs-lookup"><span data-stu-id="1f457-233">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="1f457-234">それがオプションでない場合は **[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\) > [Player]\(プレイヤー\) > [Other Settings]\(他の設定\)** の順に選択して、 **[Graphics Jobs]\(グラフィック ジョブ\)** を無効にします。</span><span class="sxs-lookup"><span data-stu-id="1f457-234">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1f457-235">ターゲット オプションとして [デバイス] が表示されない場合は、Visual Studio ソリューションのスタートアップ プロジェクトを IL2CPP プロジェクトから UWP プロジェクトに変更することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="1f457-235">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="1f457-236">これを行うには、ソリューション エクスプローラーで [YourProjectName (Universal Windows)]\(YourProjectName (ユニバーサル Windows)\) を右クリックして、 **[スタートアップ プロジェクトに設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-236">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows), and then select **Set as StartUp Project**.</span></span>

7. <span data-ttu-id="1f457-237">HoloLens をコンピューターに接続し、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="1f457-237">Connect your HoloLens to your computer, and then do one of the following:</span></span>
- <span data-ttu-id="1f457-238">アプリをビルドし、HoloLens に配置して、Visual Studio デバッガーがアタッチされていない状態で自動的に起動するには、メニュー バーで、 **[デバッグ]**  >  **[デバッグなしで開始]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-238">To build the app, deploy it to your HoloLens, and start it automatically without the Visual Studio debugger attached, on the menu bar, select **Debug** > **Start Without Debugging**.</span></span>

    :::image type="content" source="images/mr-learning-base/base-02-section8-step1-3.png" alt-text="Visual Studio の [デバッグなしで開始] メニュー パス":::

- <span data-ttu-id="1f457-240">アプリを HoloLens にビルドして配置はするものの、自動的に起動しないようにするには、メニュー バーで **[ビルド] > [ソリューションの配置]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1f457-240">To build and deploy the app to your HoloLens but not have it start automatically, on the menu bar, select **Build > Deploy Solution**.</span></span>

    > [!NOTE]
    ><span data-ttu-id="1f457-241">アプリでは、診断プロファイラーが表示される場合があります。このオン、オフを切り替えるには、音声コマンド **Toggle Diagnostics** を使用します。</span><span class="sxs-lookup"><span data-stu-id="1f457-241">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="1f457-242">アプリへの変更がパフォーマンスに影響を与える可能性がある場合は、開発中の多くは、プロファイラーを表示したままにしておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1f457-242">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="1f457-243">たとえば、HoloLens アプリは [60 FPS で継続的に実行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1f457-243">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="1f457-244">結論</span><span class="sxs-lookup"><span data-stu-id="1f457-244">Congratulations</span></span>

<span data-ttu-id="1f457-245">これで、最初の HoloLens アプリが展開されました。</span><span class="sxs-lookup"><span data-stu-id="1f457-245">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="1f457-246">手順に従うと、HoloLens によって認識されたサーフェイスに対応する空間マッピングのメッシュが表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="1f457-246">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="1f457-247">さらに、手の追跡用の手と指のインジケーターと、アプリのパフォーマンスを監視するためのフレームレート カウンターも表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="1f457-247">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="1f457-248">これらの機能は、MRTK に含まれている基本的なもののほんの一部です。</span><span class="sxs-lookup"><span data-stu-id="1f457-248">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="1f457-249">次のチュートリアルでは、コンテンツをシーンに追加して、HoloLens と MRTK の機能を調べます。</span><span class="sxs-lookup"><span data-stu-id="1f457-249">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1f457-250">次のチュートリアル:3. MRTK プロファイルの構成</span><span class="sxs-lookup"><span data-stu-id="1f457-250">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
