---
title: プロジェクトの初期化と最初のアプリケーションの配置
description: このコースでは、Mixed Reality Toolkit (MRTK) 用に Unity プロジェクトを構成する方法と、それを HoloLens 2 に配置する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, TextMeshPro,
ms.localizationpriority: high
ms.openlocfilehash: 82551257339d41940075ee06a6e6937624b83900
ms.sourcegitcommit: 08503cada8a29a34bcbd9fd955cb23adfe9b60a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/06/2021
ms.locfileid: "99627853"
---
# <a name="2-initializing-your-project-and-deploying-your-first-application"></a><span data-ttu-id="53bc2-104">2. プロジェクトの初期化と最初のアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="53bc2-104">2. Initializing your project and deploying your first application</span></span>

<span data-ttu-id="53bc2-105">このチュートリアルでは、新しい Unity プロジェクトを作成し、それを <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality ツールキット (MRTK)</a> 開発用に構成し、MRTK をインポートする方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-105">In this tutorial, you'll learn how to create a new Unity project, configure it for <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank">Mixed Reality Toolkit (MRTK)</a> development, and import MRTK.</span></span> <span data-ttu-id="53bc2-106">また、Visual Studio で基本的な Unity シーンを構成およびビルドし、HoloLens 2 に配置する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-106">You'll also walk through configuring, building, and deploying a basic Unity scene from Visual Studio to your HoloLens 2.</span></span> <span data-ttu-id="53bc2-107">HoloLens 2 に配置すると、HoloLens によって認識されたサーフェスに対応する空間マッピングのメッシュが表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="53bc2-107">Once you have deployed it to your HoloLens 2, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="53bc2-108">さらに、手の追跡用の手と指のインジケーターと、アプリのパフォーマンスを監視するためのフレームレート カウンターも表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="53bc2-108">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span>

## <a name="objectives"></a><span data-ttu-id="53bc2-109">目標</span><span class="sxs-lookup"><span data-stu-id="53bc2-109">Objectives</span></span>

* <span data-ttu-id="53bc2-110">HoloLens 開発用に Unity を構成する方法について学習する</span><span class="sxs-lookup"><span data-stu-id="53bc2-110">Learn how to configure Unity for HoloLens development</span></span>
* <span data-ttu-id="53bc2-111">アプリをビルドして HoloLens に配置する方法について学習する</span><span class="sxs-lookup"><span data-stu-id="53bc2-111">Learn how to build and deploy your app to HoloLens</span></span>
* <span data-ttu-id="53bc2-112">HoloLens 2 デバイスで空間マッピング メッシュ、ハンド メッシュ、フレームレート カウンターを体験する</span><span class="sxs-lookup"><span data-stu-id="53bc2-112">Experience the spatial mapping mesh, hand meshes, and the framerate counter on HoloLens 2 device</span></span>

## <a name="creating-the-unity-project"></a><span data-ttu-id="53bc2-113">Unity プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="53bc2-113">Creating the Unity project</span></span>

<span data-ttu-id="53bc2-114">**Unity Hub** を起動し、 **[Projects]\(プロジェクト\)** タブを選択し、 **[New]\(新規\)** ボタンの横にある **下矢印** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="53bc2-114">Launch **Unity Hub**, select the **Projects** tab, and click the **down arrow** next to the **New** button:</span></span>

![[New]\(新規\) ボタンが強調表示されている Unity Hub](images/mr-learning-base/base-02-section1-step1-1.png)

<span data-ttu-id="53bc2-116">「[前提条件](mr-learning-base-01.md#prerequisites)」に指定されている Unity の **バージョン** を、ドロップダウンで選択します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-116">In the dropdown, select the Unity **version** specified in the [Prerequisites](mr-learning-base-01.md#prerequisites):</span></span>

![Unity Hub と新しいバージョン セレクター ドロップダウン](images/mr-learning-base/base-02-section1-step1-2.png)

> [!TIP]
> <span data-ttu-id="53bc2-118">Unity Hub で特定の Unity バージョンが利用できない場合は、Unity の<a href="https://unity3d.com/get-unity/download/archive" target="_blank">アーカイブのダウンロード</a>に関するページから、そのインストールを開始できます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-118">If the particular Unity version is not available in Unity Hub, you can initiate the installation from Unity's <a href="https://unity3d.com/get-unity/download/archive" target="_blank">Download Archive</a>.</span></span>

<span data-ttu-id="53bc2-119">[Create a new project]\(新規プロジェクトの作成\) ウィンドウで、以下のようにします。</span><span class="sxs-lookup"><span data-stu-id="53bc2-119">In the Create a new project window:</span></span>

* <span data-ttu-id="53bc2-120">**[Templates]\(テンプレート\)** が **3D** に設定されていることを確認します</span><span class="sxs-lookup"><span data-stu-id="53bc2-120">Ensure **Templates** is set to **3D**</span></span>
* <span data-ttu-id="53bc2-121">"_MRTK チュートリアル_" など、適切な **[Project Name]\(プロジェクト名\)** を入力します</span><span class="sxs-lookup"><span data-stu-id="53bc2-121">Enter a suitable **Project Name**, for example, _MRTK Tutorials_</span></span>
* <span data-ttu-id="53bc2-122">プロジェクトを格納するための適切な **[Location]\(場所\)** を選択します。たとえば、_D:\MixedRealityLearning_ など</span><span class="sxs-lookup"><span data-stu-id="53bc2-122">Choose a suitable **Location** to store your project, for example, _D:\MixedRealityLearning_</span></span>
* <span data-ttu-id="53bc2-123">**[Create]\(作成\)** ボタンをクリックして、新しい Unity プロジェクトを作成して起動します</span><span class="sxs-lookup"><span data-stu-id="53bc2-123">Click the **Create** button to create and launch your new Unity project</span></span>

![[Create a new project]\(新規プロジェクトの作成\) ウィンドウが設定された Unity Hub](images/mr-learning-base/base-02-section1-step1-3.png)

> [!CAUTION]
> <span data-ttu-id="53bc2-125">Windows で作業している場合は、255 文字の MAX_PATH 制限があります。</span><span class="sxs-lookup"><span data-stu-id="53bc2-125">When working on Windows, there is a MAX_PATH limit of 255 characters.</span></span> <span data-ttu-id="53bc2-126">そのため、Unity プロジェクトはドライブのルートの近くに保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53bc2-126">Consequently, you should save the Unity project close to the root of the drive.</span></span>

<span data-ttu-id="53bc2-127">Unity によってプロジェクトが作成されるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-127">Wait for Unity to create the project:</span></span>

![新しいプロジェクトの作成が進行中の Unity](images/mr-learning-base/base-02-section1-step1-4.png)

## <a name="switching-the-build-platform"></a><span data-ttu-id="53bc2-129">ビルド プラットフォームを切り替える</span><span class="sxs-lookup"><span data-stu-id="53bc2-129">Switching the build platform</span></span>

<span data-ttu-id="53bc2-130">Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** を選択し、[Build Settings]\(ビルド設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-130">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window:</span></span>

![Unity の [Build Settings...]\(ビルド設定...\) メニュー パス](images/mr-learning-base/base-02-section2-step1-1.png)

<span data-ttu-id="53bc2-132">[Build Settings]\(ビルド設定\) ウィンドウで、 **[Universal Windows Platform]\(ユニバーサル Windows プラットフォーム\)** を選択して、 **[Switch Platform]\(プラットフォームの切り替え\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="53bc2-132">In the Build Settings window, select **Universal Windows Platform** and click the **Switch Platform** button:</span></span>

![UWP が選択されてプラットフォームがスタンドアロンから切り替えられている Unity の [Build Settings]\(ビルド設定\) ウィンドウ](images/mr-learning-base/base-02-section2-step1-2.png)

<span data-ttu-id="53bc2-134">Unity がプラットフォームの切り替えを完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-134">Wait for Unity to finish switching the platform:</span></span>

![プラットフォームの切り替えが進行中の Unity](images/mr-learning-base/base-02-section2-step1-3.png)

<span data-ttu-id="53bc2-136">Unity でプラットフォームの切り替えが完了したら、赤色の **x** アイコンをクリックして、[Build Settings]\(ビルド設定\) ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-136">When Unity has finished switching the platform, click the red **x** icon to close the Build Settings window:</span></span>

![閉じるアイコンが強調表示されている Unity のビルド ウィンドウ](images/mr-learning-base/base-02-section2-step1-4.png)

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="53bc2-138">TextMeshPro の重要なリソースをインポートする</span><span class="sxs-lookup"><span data-stu-id="53bc2-138">Importing the TextMeshPro Essential Resources</span></span>

<span data-ttu-id="53bc2-139">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[TextMeshPro]**  >  **[Import TMP Essential Resources]\(TMP の重要なリソースをインポート\)** の順に選択して、[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-139">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Unity の [Import TMP Essential Resources]\(TMP の重要なリソースをインポート\) メニュー パス](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="53bc2-141">[Import Unity Package]\(Unity パッケージのインポート\) ウィンドウで、 **[All]\(すべて\)** ボタンをクリックしてすべてのアセットが選択されていることを確認し、 **[Import]\(インポート\)** ボタンをクリックしてアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="53bc2-141">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Unity の TMP の重要なリソース インポート ウィンドウ](images/mr-learning-base/base-02-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="53bc2-143">TextMeshPro の重要なリソースは、MRTK の UI 要素で必要です。</span><span class="sxs-lookup"><span data-stu-id="53bc2-143">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="53bc2-144">ご自分のプロジェクトで MRTK の UI 要素を使用する予定がない場合は、この手順を省略できます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-144">You can skip this step if you are not planning to use MRTK's UI elements in your project.</span></span>

## <a name="importing-the-mixed-reality-toolkit"></a><span data-ttu-id="53bc2-145">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="53bc2-145">Importing the Mixed Reality Toolkit</span></span>

<span data-ttu-id="53bc2-146">Mixed Reality Toolkit を Unity プロジェクトにインポートするには、[Mixed Reality Feature Tool](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) を使用する必要があります。これにより、開発者は Mixed Reality 機能パッケージの検出、更新、Unity プロジェクトへの追加ができます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-146">To Import Mixed Reality Toolkit into the Unity Project you will have to use [Mixed Reality Feature Tool](https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool) which allows  developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="53bc2-147">名前またはカテゴリでパッケージを検索し、それらの依存関係を確認し、インポートする前にプロジェクト マニフェスト ファイルに提案された変更を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-147">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span>

<span data-ttu-id="53bc2-148">[Microsoft ダウンロード センター](https://aka.ms/MRFeatureTool)から最新バージョンの Mixed Reality Feature Tool をダウンロードし、ダウンロードが完了したら、ファイルを解凍してデスクトップに保存します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-148">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool), When the download is complete, unzip the file and save it to your desktop.</span></span>

> [!NOTE]
> <span data-ttu-id="53bc2-149">Mixed Reality Feature Tool を実行する前に、[.NET 5.0 ランタイム](https://dotnet.microsoft.com/download/dotnet/5.0)をインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="53bc2-149">Before you can run the Mixed Reality Feature Tool please instal [.NET 5.0 runtime](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>

> [!NOTE]
> <span data-ttu-id="53bc2-150">現在、Mixed Reality Feature Tool は Windows 上でのみ動作します。 MacOS の場合は、この[手順](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages)に従って、Mixed Reality Toolkit をダウンロードして Unity プロジェクトにインポートしてください。</span><span class="sxs-lookup"><span data-stu-id="53bc2-150">The Mixed Reality Feature Tool currently only runs on Windows, For MacOS please follow this [procedure](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html#1-get-the-latest-mrtk-unity-packages) to download and import the Mixed Reality Toolkit into the unity project.</span></span>

<span data-ttu-id="53bc2-151">ダウンロードしたフォルダーから実行可能ファイル **MixedRealityFeatureTool** を開き、Mixed Reality Feature Tool を起動します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-151">Open the executable file **MixedRealityFeatureTool** from the downloaded folder to launch the Mixed Reality Feature Tool.</span></span>  

![MixedRealityFeatureTool を開く](images/mr-learning-base/base-02-section4-step1-1.png)

<span data-ttu-id="53bc2-153">**MixedRealityFeatureTool** が開いたら、[スタート] をクリックして、Mixed Reality Feature Tool の使用を開始します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-153">Once **MixedRealityFeatureTool** is opened click on start to get started with Mixed Reality Feature Tool.</span></span>

![MixedRealityFeatureTool](images/mr-learning-base/base-02-section4-step1-2.png)

<span data-ttu-id="53bc2-155">機能は、見つけやすいようにカテゴリ別にグループ化されているので、 **[Mixed Reality Toolkit]** ドロップダウンをクリックし、Mixed Reality Toolkit に関連するパッケージを見つけます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-155">Features are grouped by category to make things easier to find, click on **Mixed Reality Toolkit** dropdown to find packages relating to the Mixed Reality Toolkit.</span></span>

![MixedRealityFeatureTool ウィンドウ](images/mr-learning-base/base-02-section4-step1-3.png)

<span data-ttu-id="53bc2-157">**Mixed Reality Toolkit Foundation** にチェックマークを付け、その横のドロップダウンをクリックし、必要な MRTK バージョンを選択します。このチュートリアル シリーズでは、**2.5.3** を選択してください。</span><span class="sxs-lookup"><span data-stu-id="53bc2-157">check the **Mixed Reality Toolkit Foundation**, and click on the dropdown next to it to select the required MRTK version, for this tutorial series please select **2.5.3**.</span></span> <span data-ttu-id="53bc2-158">次に、 **[Get features]\(機能の取得\)** ボタンをクリックして、選択したパッケージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="53bc2-158">then click on **Get features** button to download the selected packages.</span></span>

![Mixed Reality Foundation の選択](images/mr-learning-base/base-02-section4-step1-4.png)

<span data-ttu-id="53bc2-160">選択したパッケージ **Mixed Reality Toolkit Foundation 2.5.3** が表示され、その依存パッケージ **Mixed Reality Toolkit Standard Asset 2.5.3** が **[Import Features]\(機能のインポート\)** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-160">Selected package **Mixed Reality Toolkit Foundation 2.5.3** is presented, along with its dependence package **Mixed Reality Toolkit Standard Assets 2.5.3** in the **Import Features** window.</span></span>

<span data-ttu-id="53bc2-161">また、対象の Unity プロジェクトの場所を設定して、 **[Project path]\(プロジェクト パス\)** を指定し、[Project path]\(プロジェクト パス\) の横にある **3 つのドット** をクリックして、エクスプローラーでプロジェクト フォルダー (たとえば _D:\MixedRealityLearning\MRTK Tutorials_) を参照する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="53bc2-161">You also need to set the location of the target unity project to provide the **Project path**, click on the **Three dots** next to the Project path and browse to your project folder in the explorer for example _D:\MixedRealityLearning\MRTK Tutorials_.</span></span>

> [!NOTE]
> <span data-ttu-id="53bc2-162">Unity プロジェクト フォルダーを参照するときに表示されるダイアログには、ファイル名として '_' が含まれています。</span><span class="sxs-lookup"><span data-stu-id="53bc2-162">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="53bc2-163">フォルダーを選択できるようにするには、ファイル名に値が必要です。</span><span class="sxs-lookup"><span data-stu-id="53bc2-163">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="53bc2-164">次に **[Validate]\(検証\)** ボタンをクリックして、選択したパッケージを検証すると、 **[No validation issues were detected]\(検証の問題は検出されませんでした\)** というメッセージを含むポップアップが表示されます。 **[OK]** をクリックしてポップアップを閉じ、 **[Import]\(インポート\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="53bc2-164">Next click on the **Validate** button to validate the selected package, you will get a popup with message **No validation issues were detected** click on **OK** to close the popup and click on **Import** button.</span></span>

![Mixed Reality Foundation の検証](images/mr-learning-base/base-02-section4-step1-5.png)

<span data-ttu-id="53bc2-166">**Mixed Reality Toolkit** をプロジェクトに追加するには、**Approve\(承認\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="53bc2-166">Click on **Approve** Button to add the **Mixed Reality Toolkit** into the project.</span></span>

![Mixed Reality Foundation の承認](images/mr-learning-base/base-02-section4-step1-6.png)

## <a name="configuring-the-unity-project"></a><span data-ttu-id="53bc2-168">Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="53bc2-168">Configuring the Unity project</span></span>

### <a name="1-apply-the-mrtk-project-configurator-settings"></a><span data-ttu-id="53bc2-169">1. MRTK プロジェクト コンフィギュレーター設定を適用する</span><span class="sxs-lookup"><span data-stu-id="53bc2-169">1. Apply the MRTK Project Configurator settings</span></span>

<span data-ttu-id="53bc2-170">Unity によって前のセクションからのパッケージのインポートが完了すると、[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-170">After Unity has finished importing the package from the previous section, the MRTK Project Configurator window should appear.</span></span> <span data-ttu-id="53bc2-171">表示されない場合は、 **[Mixed Reality Toolkit]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** に移動して手動で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-171">If it doesn't, you can manually open it by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**:</span></span>

![Unity の [Configure Unity Project]\(Unity プロジェクトの構成\) メニュー パス](images/mr-learning-base/base-02-section5-step1-1.png)

<span data-ttu-id="53bc2-173">[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウで、 **[Modify Configurations]\(構成の変更\)** セクションを展開し、他のすべてのオプションを確実にオンにしてから、 **[Apply]\(適用\)** ボタンをクリックして設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-173">In the MRTK Project Configurator window, expand the **Modify Configurations** section, ensure all options are checked, and click the **Apply** button to apply the settings:</span></span>

![[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが表示された Unity](images/mr-learning-base/base-02-section5-step1-2.png)

> [!TIP]
> <span data-ttu-id="53bc2-175">MRTK の既定の設定の適用はオプションですが、一部の推奨される Unity 設定を構成するのに役立つので強く推奨されます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-175">Applying the MRTK Default Settings is optional but strongly recommended as it will help configure some recommended Unity settings:</span></span>

> * <span data-ttu-id="53bc2-176">[Set Single Pass Instanced rendering path]\(単一パスのインスタンス化レンダリング パスを設定する\): 同じ描画呼び出しで両方の目のレンダリング パイプラインを実行することにより、グラフィックスのパフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-176">Set Single Pass Instanced rendering path: Improves graphics performance by executing the render pipeline for both eyes in the same draw call.</span></span> <span data-ttu-id="53bc2-177">このトピックの詳細については、MRTK の「[パフォーマンス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html)」ドキュメントの「[単一パス インスタンス化レンダリング](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="53bc2-177">To learn more about this topic, you can refer to the [Single-Pass Instanced rendering](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#single-pass-instanced-rendering) section of MRTK's [Performance](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) documentation.</span></span>
> * <span data-ttu-id="53bc2-178">[Set default Spatial Awareness layer]\(既定の空間認識レイヤーを設定する\): 空間認識という名前の Unity レイヤーを作成し、空間認識メッシュにこのレイヤーを使用するように MRTK を構成します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-178">Set default Spatial Awareness layer: Creates a Unity Layer named Spatial Awareness and configures MRTK to use this layer for the spatial awareness mesh.</span></span> <span data-ttu-id="53bc2-179">Unity レイヤーの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">ワークスペースのカスタマイズ</a>に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="53bc2-179">To learn more about Unity Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

### <a name="2-configure-additional-project-settings"></a><span data-ttu-id="53bc2-180">2.追加のプロジェクト設定を構成する</span><span class="sxs-lookup"><span data-stu-id="53bc2-180">2. Configure additional project settings</span></span>

<span data-ttu-id="53bc2-181">Unity メニューで、 **[Edit]\(編集\)**  >  **[Project Settings...]\(プロジェクト設定...\)** を選択し、[Project Settings]\(プロジェクト設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-181">In the Unity menu, select **Edit** > **Project Settings...** to open the Project Settings window:</span></span>

<span data-ttu-id="53bc2-182">[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレイヤー\)**  >  **[XR Settings]\(XR 設定\)** の順に選択し、 **[Virtual Reality Supported]\(仮想現実のサポート\)** チェック ボックスをオンにします。次に、 **+** アイコンをクリックし、[Windows Mixed Reality] を選択して Windows Mixed Reality SDK を追加します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-182">In the Project Settings window, select **Player** > **XR Settings** and check the **Virual Reality Supported** checkbox then click the **+** icon, and select Windows Mixed Reality to add the Windows Mixed Reality SDK:</span></span>

![Windows Mixed Reality SDK の追加が選択された Unity の XR 設定](images/mr-learning-base/base-02-section5-step2-4.png)

<span data-ttu-id="53bc2-184">Unity によって Windows Mixed Reality SDK のインポートが完了すると、[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが再び表示されます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-184">After Unity has finished importing the Windows Mixed Reality SDK, the MRTK Project Configurator window should appear again.</span></span> <span data-ttu-id="53bc2-185">表示されない場合は、 **[Mixed Reality Toolkit]**  >  **[Utilities]\(ユーティリティ\)**  >  **[Configure Unity Project]\(Unity プロジェクトの構成\)** に移動して、Unity メニューから手動で開くことができます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-185">If it doesn't, you can manually open it from the Unity menu by going to **Mixed Reality Toolkit** > **Utilities** > **Configure Unity Project**</span></span>

<span data-ttu-id="53bc2-186">[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウで、 **[Audio Spatializer]** ドロップダウンを使用して **[MS HRTF Spatializer]** を選択してから、 **[Apply]\(適用\)** ボタンをクリックしてこの設定を適用します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-186">In the MRTK Project Configurator window, use the **Audio spatializer** dropdown to select the **MS HRTF Spatializer**, then click the **Apply** button to apply the setting:</span></span>

![Windows Mixed Reality SDK の追加が選択された Unity の XR 設定](images/mr-learning-base/base-02-section5-step2-5.png)

> [!TIP]
><span data-ttu-id="53bc2-188">Audio Spatializer プロパティの設定はオプションですが、プロジェクトでのオーディオ エクスペリエンスが向上する場合があります。</span><span class="sxs-lookup"><span data-stu-id="53bc2-188">Setting the Audio spatializer property is optional but may improve the audio experience in your project.</span></span> <span data-ttu-id="53bc2-189">MS HRTF Spatializer に設定した場合、Unity の AudioSource.spatialize プロパティが有効になっていると、この Spatializer プラグインが使用されます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-189">If you set it to MS HRTF Spatializer, this spatializer plugin will be used when Unity's AudioSource.spatialize property is enabled.</span></span> <span data-ttu-id="53bc2-190">このトピックの詳細については、<a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank">立体オーディオのチュートリアル</a>に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="53bc2-190">To learn more about this topic, you can refer to the  <a href="https://docs.microsoft.com/en-us/windows/mixed-reality/develop/unity/tutorials/unity-spatial-audio-ch1" target="_blank"> Spatial audio tutorials</a>.</span></span>

<span data-ttu-id="53bc2-191">[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレーヤー\)**  >  **[XR Settings]\(XR 設定\)** を選択してから、 **[Depth Format]\(深度形式\)** ドロップダウンを使用して **[16-bit depth]\(16 ビット深度\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-191">In the Project Settings window, select **Player** > **XR Settings**, then use the **Depth Format** dropdown to select **16-bit depth**:</span></span>

![Unity で 16 ビット深度を有効にする](images/mr-learning-base/base-02-section5-step2-6.png)

> [!TIP]
> <span data-ttu-id="53bc2-193">深度形式を 16 ビットに減らすことはオプションですが、プロジェクトでのグラフィックス パフォーマンスの向上につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="53bc2-193">Reducing the Depth Format to 16-bit is optional but my help improve graphics performance in your project.</span></span> <span data-ttu-id="53bc2-194">このトピックの詳細については、MRTK の「<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank">パフォーマンス</a>」ドキュメントの「<a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">深度バッファー共有 (HoloLens)</a>」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="53bc2-194">To learn more about this topic, you can refer to the   <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html#depth-buffer-sharing-hololens" target="_blank">  Depth buffer sharing (HoloLens) </a> section of MRTK's  <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html" target="_blank"> Performance </a> documentation.</span></span>

<span data-ttu-id="53bc2-195">[Project Settings]\(プロジェクト設定\) ウィンドウで、 **[Player]\(プレイヤー\)**  >  **[Publishing Settings]\(公開の設定\)** の順に選択してから、 **[Package name]\(パッケージ名\)** フィールドに適切な名前 (たとえば _MRTKTutorials-GettingStarted_) を入力します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-195">In the Project Settings window, select **Player** > **Publishing Settings**, then in the **Package name** field, enter a suitable name, for example, _MRTKTutorials-GettingStarted_:</span></span>

![パッケージ名が構成されている Unity の公開設定](images/mr-learning-base/base-02-section5-step2-7.png)

> [!NOTE]
> <span data-ttu-id="53bc2-197">'パッケージ名' は、アプリの一意の識別子です。</span><span class="sxs-lookup"><span data-stu-id="53bc2-197">The 'Package name' is the unique identifier for the app.</span></span> <span data-ttu-id="53bc2-198">以前にインストールしたアプリが上書きされないように、アプリを配置する前にこの識別子を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53bc2-198">You should change this identifier before deploying the app to avoid overwriting previously installed apps.</span></span>

> [!TIP]
> <span data-ttu-id="53bc2-199">'製品名' は、HoloLens の [スタート] メニューに表示される名前です。</span><span class="sxs-lookup"><span data-stu-id="53bc2-199">The 'Product Name' is the name displayed in the HoloLens Start menu.</span></span> <span data-ttu-id="53bc2-200">開発中にアプリを見つけやすくするには、名前の前にアンダースコアを追加し、上部にくるように並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-200">To make the app easier to locate during development, add an underscore in front of the name to sort it to the top.</span></span>

## <a name="creating-and-configuring-the-scene"></a><span data-ttu-id="53bc2-201">シーンを作成して構成する</span><span class="sxs-lookup"><span data-stu-id="53bc2-201">Creating and configuring the scene</span></span>

<span data-ttu-id="53bc2-202">Unity メニューで、 **[File]\(ファイル\)**  >  **[New Scene]\(新しいシーン\)** の順に選択して新しいシーンを作成します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-202">In the Unity menu, select **File** > **New Scene** to create a new scene:</span></span>

![Unity の [New Scene]\(新しいシーン\) メニュー パス](images/mr-learning-base/base-02-section6-step1-1.png)

<span data-ttu-id="53bc2-204">Unity メニューで、 **[Mixed Reality Toolkit]**  >  **[Add to Scene and Configure...]\(シーンに追加して構成する...\)** の順に選択して、MRTK を現在のシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-204">In the Unity menu, select **Mixed Reality Toolkit** > **Add to Scene and Configure...** to add the MRTK to your current scene:</span></span>

![Unity の [Add to Scene and Configure...]\(シーンに追加して構成する...\) メニュー パス](images/mr-learning-base/base-02-section6-step1-2.png)

<span data-ttu-id="53bc2-206">[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択したままとし、[Inspector]\(インスペクター\) ウィンドウで、**MixedRealityToolkit** 構成プロファイルが **DefaultMixedRealityToolkitConfigurationProfile** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-206">With the **MixedRealityToolkit** object still selected in the Hierarchy window, in the Inspector window, verify that the **MixedRealityToolkit** configuration profile is set to **DefaultMixedRealityToolkitConfigurationProfile**:</span></span>

![DefaultMixedRealityTookitConfigurationProfile が選択された Unity MixedRealityToolkit コンポーネント](images/mr-learning-base/base-02-section6-step1-3.png)

<span data-ttu-id="53bc2-208">Unity メニューで、 **[File]\(ファイル\)**  >  **[Save As...]\(名前を付けて保存...\)** を選択して [Save Scene]\(シーンの保存\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-208">In the Unity menu, select **File** > **Save As...** to open the Save Scene window:</span></span>

![Unity の [Save As...]\(名前を付けて保存...\) メニュー パス](images/mr-learning-base/base-02-section6-step1-4.png)

<span data-ttu-id="53bc2-210">[Save Scene]\(シーンの保存\) ウィンドウで、プロジェクトの **[Scenes]\(シーン\)** フォルダーに移動し、シーンに適切な名前を付け (たとえば、_GettingStarted_)、 **[Save]\(保存\)** ボタンをクリックしてシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-210">In the Save Scene window, navigate to your project's **Scenes** folder, give your scene a suitable name, for example, _GettingStarted_, and click the **Save** button to save the scene:</span></span>

![Unity のシーン保存の [Save]\(保存\) プロンプト ウィンドウ](images/mr-learning-base/base-02-section6-step1-5.png)

## <a name="building-your-application-to-your-hololens-2"></a><span data-ttu-id="53bc2-212">HoloLens 2 デバイス用にアプリケーションをビルドする</span><span class="sxs-lookup"><span data-stu-id="53bc2-212">Building your application to your HoloLens 2</span></span>

### <a name="1-build-the-unity-project"></a><span data-ttu-id="53bc2-213">1.Unity プロジェクトのビルド</span><span class="sxs-lookup"><span data-stu-id="53bc2-213">1. Build the Unity project</span></span>

<span data-ttu-id="53bc2-214">Unity メニューで、 **[File]\(ファイル\)**  >  **[Build Settings...]\(ビルド設定...\)** を選択し、[Build Settings]\(ビルド設定\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-214">In the Unity menu, select **File** > **Build Settings...** to open the Build Settings window.</span></span>

<span data-ttu-id="53bc2-215">[Build Settings]\(ビルド設定\) ウィンドウで、 **[Add Open Scenes]\(開いているシーンを追加する\)** ボタンをクリックして、 **[Scenes In Build]\(ビルド内のシーン\)** リストの現在のシーンを追加します。次に **[Build]\(ビルド\)** ボタンをクリックして、[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-215">In the Build Settings window, click the **Add Open Scenes** button to add your current scene to the **Scenes In Build** list, then click the **Build** button to open the Build Universal Windows Platform window:</span></span>

![UWP が選択されている [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="53bc2-217">[Build Universal Windows Platform]\(ユニバーサル Windows プラットフォームのビルド\) ウィンドウで、ビルドを格納する適切な場所 (たとえば _D:\MixedRealityLearning\Builds_) を選択し、新しいフォルダーを作成して適切な名前 (たとえば _GettingStarted_) を付け、 **[Select Folder]\(フォルダーの選択\)** ボタンをクリックしてビルド処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-217">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, _D:\MixedRealityLearning\Builds_, create a new folder and give it a suitable name, for example, _GettingStarted_, and then click the **Select Folder** button to start the build process:</span></span>

![[フォルダーの選択] プロンプト ウィンドウが表示されている [Build Settings]\(ビルド設定\) ウィンドウが表示された Unity](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="53bc2-219">Unity がビルド処理を完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-219">Wait for Unity to finish the build process:</span></span>

![ビルド処理が進行中の Unity](images/mr-learning-base/base-02-section7-step1-3.png)

### <a name="2-build-and-deploy-the-application"></a><span data-ttu-id="53bc2-221">2.アプリのビルドと配置</span><span class="sxs-lookup"><span data-stu-id="53bc2-221">2. Build and deploy the application</span></span>

<span data-ttu-id="53bc2-222">ビルド処理が完了すると、お客様がビルドを格納した場所を開くように Unity から Windows ファイル エクスプローラーに指示が出されます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-222">When the build process has completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="53bc2-223">フォルダー内を移動し、ソリューション ファイルをダブルクリックして Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-223">Navigate inside the folder, and double-click the solution file to open it in Visual Studio:</span></span>

![新しく作成された Visual Studio ソリューションが選択された Windows エクスプローラー](images/mr-learning-base/base-02-section8-step1-1.png)

> [!NOTE]
> <span data-ttu-id="53bc2-225">Visual Studio から新しいコンポーネントをインストールするよう求められたら、少し時間を取って、「 **[ツールのインストール](../../install-the-tools.md)** 」ドキュメントで示されている、前提条件となるすべてのコンポーネントが用意できていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="53bc2-225">If Visual Studio asks you to install new components, take a moment to check that you have all the prerequisite components in the **[Install the Tools](../../install-the-tools.md)** documentation.</span></span>

<span data-ttu-id="53bc2-226">**[マスター]** または **[リリース]** 構成を選択し、 **[ARM64]** アーキテクチャを選択し、ターゲットとして **[デバイス]** を選択して、HoloLens 用に Visual Studio を構成します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-226">Configure Visual Studio for HoloLens by selecting the **Master** or **Release** configuration, the **ARM64** architecture, and **Device** as target:</span></span>

![HoloLens 2 に配置するように構成された Visual Studio](images/mr-learning-base/base-02-section8-step1-2.png)

> [!TIP]
> <span data-ttu-id="53bc2-228">HoloLens (第 1 世代) に配置する場合は、**x86** アーキテクチャを選択します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-228">If you're deploying to HoloLens (1st generation), select the **x86** architecture.</span></span>

> [!NOTE]
> <span data-ttu-id="53bc2-229">HoloLens の場合、通常は ARM アーキテクチャ用にビルドします。</span><span class="sxs-lookup"><span data-stu-id="53bc2-229">For HoloLens, you will typically build for the ARM architecture.</span></span> <span data-ttu-id="53bc2-230">ただし、Unity 2019.3 には、Visual Studio で ARM をビルド アーキテクチャとして選択した場合にエラーを引き起こす<a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>既知の問題</strong></a>が存在します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-230">However, there is a  <a href="https://github.com/microsoft/MixedRealityToolkit-Unity" target="_blank"><strong>known issue</strong></a> in Unity 2019.3 that causes errors when selecting ARM as the build architecture in Visual Studio.</span></span> <span data-ttu-id="53bc2-231">推奨される回避策は、ARM64 用にビルドすることです。</span><span class="sxs-lookup"><span data-stu-id="53bc2-231">The recommended workaround is to build for ARM64.</span></span> <span data-ttu-id="53bc2-232">それがオプションでない場合は **[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\) > [Player]\(プレイヤー\) > [Other Settings]\(他の設定\)** の順に選択して、 **[Graphics Jobs]\(グラフィック ジョブ\)** を無効にします。</span><span class="sxs-lookup"><span data-stu-id="53bc2-232">If that is not an option, go to **Edit > Project Settings > Player > Other Settings** and disable **Graphics Jobs**.</span></span>

> [!NOTE]
> <span data-ttu-id="53bc2-233">ターゲット オプションとして [デバイス] が表示されない場合は、Visual Studio ソリューションのスタートアップ プロジェクトを IL2CPP プロジェクトから UWP プロジェクトに変更することが必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="53bc2-233">If you don't see Device as a target option, you may need to change the startup project for the Visual Studio solution from the IL2CPP project to the UWP project.</span></span> <span data-ttu-id="53bc2-234">それを行うには、ソリューション エクスプローラーで、[YourProjectName (Universal Windows)]\(YourProjectName (ユニバーサル Windows)\) を右クリックし、 **[スタートアップ プロジェクトに設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-234">To do this, in the Solution Explorer, right-click on YourProjectName (Universal Windows) and select **Set as StartUp Project**.</span></span>

<span data-ttu-id="53bc2-235">ご利用のコンピューターに HoloLens を接続し、 **[デバッグ]**  >  **[デバッグなしで開始]** の順に選択して、ご利用のデバイス用にビルドして配置します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-235">Connect your HoloLens to your computer, then select **Debug** > **Start Without Debugging** to build and deploy to your device:</span></span>

![Visual Studio の [デバッグなしで開始] メニュー パス](images/mr-learning-base/base-02-section8-step1-3.png)

> [!IMPORTANT]
> <span data-ttu-id="53bc2-237">デバイスに対してビルドする前に、デバイスが開発者モードになっており、かつ、開発コンピューターとペアリングされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="53bc2-237">Before building to your device, the device must be in Developer Mode and paired with your development computer.</span></span> <span data-ttu-id="53bc2-238">この両方のステップを完了するには、[こちらの手順](../../platform-capabilities-and-apis/using-visual-studio.md)に従います。</span><span class="sxs-lookup"><span data-stu-id="53bc2-238">Both of these steps can be completed by following [these instructions](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

> [!TIP]
> <span data-ttu-id="53bc2-239">また、[HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) に配置することも、サイドローディング用の[アプリ パッケージ](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps)を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-239">You can also deploy to the [HoloLens Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md) or create an [App Package](https://docs.microsoft.com/windows/uwp/packaging/packaging-uwp-apps) for sideloading.</span></span>

<span data-ttu-id="53bc2-240">[デバッグなしで開始] を使用すると、Visual Studio デバッガーがアタッチされていない状態でも、ご利用のデバイス上でアプリが自動的に起動します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-240">Using Start Without Debugging automatically starts the app on your device without the Visual Studio debugger attached.</span></span>

<span data-ttu-id="53bc2-241">アプリを自動的に起動せずに、ご利用のデバイスに配置するには、 **[ビルド] > [ソリューションの配置]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-241">Select **Build > Deploy Solution** to deploy to your device without having the app start automatically.</span></span>

> [!NOTE]
><span data-ttu-id="53bc2-242">アプリでは、診断プロファイラーが表示される場合があります。このオン、オフを切り替えるには、音声コマンド **Toggle Diagnostics** を使用します。</span><span class="sxs-lookup"><span data-stu-id="53bc2-242">You may notice the Diagnostics profiler in the app, which you can toggle on or off by using the speech command **Toggle Diagnostics**.</span></span> <span data-ttu-id="53bc2-243">アプリへの変更がパフォーマンスに影響を与える可能性がある場合は、開発中の多くは、プロファイラーを表示したままにしておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="53bc2-243">It's recommended that you keep the profiler visible most of the time during development to understand when changes to the app may impact performance.</span></span> <span data-ttu-id="53bc2-244">たとえば、HoloLens アプリは [60 FPS で継続的に実行](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="53bc2-244">For example, HoloLens apps should [continuously run at 60 FPS](../../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span>

## <a name="congratulations"></a><span data-ttu-id="53bc2-245">結論</span><span class="sxs-lookup"><span data-stu-id="53bc2-245">Congratulations</span></span>

<span data-ttu-id="53bc2-246">これで、最初の HoloLens アプリが展開されました。</span><span class="sxs-lookup"><span data-stu-id="53bc2-246">You've now deployed your first HoloLens app.</span></span> <span data-ttu-id="53bc2-247">手順に従うと、HoloLens によって認識されたサーフェイスに対応する空間マッピングのメッシュが表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="53bc2-247">As you walk around, you should see a spatial mapping mesh covering the surfaces that are perceived by the HoloLens.</span></span> <span data-ttu-id="53bc2-248">さらに、手の追跡用の手と指のインジケーターと、アプリのパフォーマンスを監視するためのフレームレート カウンターも表示されるはずです。</span><span class="sxs-lookup"><span data-stu-id="53bc2-248">Additionally, you should see indicators on your hands and fingers for hand tracking and a frame rate counter for keeping an eye on app performance.</span></span> <span data-ttu-id="53bc2-249">これらの機能は、MRTK に含まれている基本的なもののほんの一部です。</span><span class="sxs-lookup"><span data-stu-id="53bc2-249">These features are just a few foundational pieces included with MRTK.</span></span> <span data-ttu-id="53bc2-250">次のチュートリアルでは、コンテンツをシーンに追加して、HoloLens と MRTK の機能を調べます。</span><span class="sxs-lookup"><span data-stu-id="53bc2-250">In the upcoming tutorials, you'll add content to your scene to explore the capabilities of HoloLens and the MRTK.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="53bc2-251">次のチュートリアル:3. MRTK プロファイルの構成</span><span class="sxs-lookup"><span data-stu-id="53bc2-251">Next Tutorial: 3. Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
