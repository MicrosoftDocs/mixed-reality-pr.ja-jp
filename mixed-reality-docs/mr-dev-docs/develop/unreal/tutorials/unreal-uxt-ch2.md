---
title: 2. プロジェクトと最初のアプリケーションの初期化
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用してチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 2
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, はじめに, mrtk, uxt, UX ツール, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 9e02ea6cb2710b4661e97dc8b0d5f4f48ab09fa7
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583904"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="c6c93-104">2.プロジェクトと最初のアプリケーションの初期化</span><span class="sxs-lookup"><span data-stu-id="c6c93-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="c6c93-105">最初のチュートリアルでは、新しい Unreal プロジェクトから始めて、HoloLens プラグインを有効にし、レベルを作成して照明し、チェスの駒を追加します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-105">In the first tutorial, you'll start out with a new Unreal project and enable the HoloLens plugin, create and light a level, and add chess pieces.</span></span> <span data-ttu-id="c6c93-106">3D のすべてのオブジェクトとマテリアルには、事前に作成された資産を使用するため、自分でモデリングする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c6c93-106">You'll be using our pre-made assets for all 3D objects and materials, so don't worry about modeling anything yourself.</span></span> <span data-ttu-id="c6c93-107">このチュートリアルを完了するまでに、Mixed Reality に対応できる空のキャンバスが完成します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-107">By the end of this tutorial, you'll have a blank canvas that's ready for mixed reality.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6c93-108">「[はじめに](/windows/mixed-reality/unreal-uxt-ch1)」ページにあるすべての前提条件を確認してください。</span><span class="sxs-lookup"><span data-stu-id="c6c93-108">Make sure you have all the prerequisites from the [Getting Started](/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="c6c93-109">目標</span><span class="sxs-lookup"><span data-stu-id="c6c93-109">Objectives</span></span>

* <span data-ttu-id="c6c93-110">HoloLens 開発用の Unreal プロジェクトの構成</span><span class="sxs-lookup"><span data-stu-id="c6c93-110">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="c6c93-111">資産のインポートとシーンのセットアップ</span><span class="sxs-lookup"><span data-stu-id="c6c93-111">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="c6c93-112">ブループリントを使用したアクターとスクリプトレベルのイベントの作成</span><span class="sxs-lookup"><span data-stu-id="c6c93-112">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="c6c93-113">新しい Unreal プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="c6c93-113">Creating a new Unreal project</span></span>

<span data-ttu-id="c6c93-114">最初に必要なのは、作業するプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="c6c93-114">The first thing you need is a project to work with.</span></span> <span data-ttu-id="c6c93-115">Unreal で初めて開発する場合は、Epic Launcher から[サポート ファイルをダウンロードする](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6c93-115">If you're a first-time Unreal developer, you'll need to [download supporting files](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="c6c93-116">Unreal Engine を起動します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-116">Launch Unreal Engine</span></span>

2. <span data-ttu-id="c6c93-117">**[New Project Categories]\(新規プロジェクトのカテゴリ\)** で、 **[ゲーム]** を選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-117">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![ゲーム プロジェクト テンプレートの選択](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="c6c93-119">**[Blank]\(空のプロジェクト\)** テンプレートを選択して **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-119">Select the **Blank** Template and click **Next**.</span></span> 

![[Blank]\(空のプロジェクト\) テンプレートを選択する](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="c6c93-121">**[C++]** 、 **[Scalable 3D or 2D]\(スケーラブル 3D または 2D\)、[Mobile/Tablet]\(モバイル/タブレット\)** 、 **[No Starter Content]\(スターター コンテンツを有効にしない\)** を **[Project Settings]\(プロジェクト設定\)** として設定し、保存場所を選択して、 **[Create Project]\(プロジェクトの作成)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-121">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**, then choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="c6c93-122">UX Tools プラグインをビルドするには、ブループリント プロジェクトではなく、C++ プロジェクトを選択する必要があります。UX Tools プラグインは、この後のセクション 4 でセットアップします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-122">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![最初のプロジェクト設定](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="c6c93-124">Unreal エディターでプロジェクトが自動的に開きます。つまり、次のセクションに進む準備はできています。</span><span class="sxs-lookup"><span data-stu-id="c6c93-124">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="c6c93-125">必要なプラグインの有効化</span><span class="sxs-lookup"><span data-stu-id="c6c93-125">Enabling required plugins</span></span>

<span data-ttu-id="c6c93-126">オブジェクトをシーンに追加する前に、2 つのプラグインを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6c93-126">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="c6c93-127">**[編集] > [プラグイン]** を開き、組み込みオプション リストから **[拡張現実]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-127">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="c6c93-128">**HoloLens** まで下にスクロールし、 **[有効]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-128">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![HoloLens プラグインの有効化](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="c6c93-130">組み込みオプション リストから **[仮想現実]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-130">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="c6c93-131">**[Microsoft Windows Mixed Reality]** まで下にスクロールし、 **[有効]** をオンにして、エディターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-131">Scroll down to **Microsoft Windows Mixed Reality**, check **Enabled**, and restart your editor.</span></span> 

![Windows Mixed Reality プラグインを有効にする](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="c6c93-133">HoloLens 2 の開発には、両方のプラグインが必要です。</span><span class="sxs-lookup"><span data-stu-id="c6c93-133">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="c6c93-134">プラグインが有効になったので、空のレベルを使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c6c93-134">With the plugins enabled, your empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="c6c93-135">レベルの作成</span><span class="sxs-lookup"><span data-stu-id="c6c93-135">Creating a level</span></span>
<span data-ttu-id="c6c93-136">次のタスクは、参照とスケール用の開始点とキューブを使用してプレーヤーのセットアップを作成することです。</span><span class="sxs-lookup"><span data-stu-id="c6c93-136">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="c6c93-137">**[ファイル] > [新しいレベル]** を選択し、 **[空のレベル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-137">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="c6c93-138">この時点では、ビューポートの既定のシーンは空です。</span><span class="sxs-lookup"><span data-stu-id="c6c93-138">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="c6c93-139">**[モード]** タブから **[基本]** を選択し、 **[PlayerStart]** をシーンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-139">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="c6c93-140">**[詳細]** タブで、 **[場所]** を **X = 0**、**Y = 0**、**Z = 0** に設定して、アプリの起動時にユーザーをシーンの中心に設定します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-140">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab to set the user at the center of the scene when the app starts up.</span></span>

![PlayerStart を表示したビューポート](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="c6c93-142">**[キューブ]** を **[基本]** タブからシーンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-142">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="c6c93-143">**[位置]** を **X = 50**、**Y = 0**、および **Z = 0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-143">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="c6c93-144">これにより、キューブは開始時にプレーヤーから 50 cm 離れた位置に配置されます。</span><span class="sxs-lookup"><span data-stu-id="c6c93-144">to position the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="c6c93-145">キューブを縮小するには、 **[スケール]** を **X = 0.2**、**Y = 0.2**、および **Z = 0.2** に変更します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-145">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="c6c93-146">シーンにライトを追加しない限り、キューブを表示することはできません。これは、シーンをテストする前の最後のタスクです。</span><span class="sxs-lookup"><span data-stu-id="c6c93-146">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="c6c93-147">**[モード]** パネルの **[Lights]\(ライト\)** タブに切り替えて、**Directional Light** をシーンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-147">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="c6c93-148">ライトが見えるように、**PlayerStart** の上にライトを配置します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-148">Position the light above **PlayerStart** so you can see it.</span></span>

![ライトが追加されたビューポート](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="c6c93-150">**[ファイル] > [現在を保存]** に移動し、レベルに **Main** という名前を付けて、 **[保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-150">Go to **File > Save Current**, name your level **Main**, and select **Save**.</span></span> 

<span data-ttu-id="c6c93-151">シーンを設定したら、ツールバーの **[再生]** を押して、キューブの動作を確認します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-151">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="c6c93-152">作業内容を鑑賞したら、**Esc** を押してアプリケーションを停止します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-152">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![ビューポート内のキューブ](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="c6c93-154">シーンがセットアップされたので、チェス盤と駒を追加して、アプリケーション環境を完成させます。</span><span class="sxs-lookup"><span data-stu-id="c6c93-154">Now that the scene is set up, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="c6c93-155">資産のインポート</span><span class="sxs-lookup"><span data-stu-id="c6c93-155">Importing assets</span></span>
<span data-ttu-id="c6c93-156">現在、シーンは空であるように見えますが、既製の資産をプロジェクトにインポートして修正します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-156">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="c6c93-157">[7-zip](https://www.7-zip.org/) を使用して、[GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) 資産フォルダーをダウンロードして解凍します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-157">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder using [7-zip](https://www.7-zip.org/).</span></span>

2. <span data-ttu-id="c6c93-158">**[Content Browser]\(コンテンツ ブラウザー\)** から **[新規追加] > [新しいフォルダー]** を選択し、**ChessAssets** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="c6c93-158">Select **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="c6c93-159">3D 資産をインポートする新しいフォルダーをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-159">Double-click the new folder where you'll import the 3D assets.</span></span>

![ソース パネルの表示と非表示](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="c6c93-161">**[Content Browser]\(コンテンツ ブラウザー\)** から **[インポート]** を選択し、解凍した資産フォルダー内のすべての項目を選択して、 **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-161">Select **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="c6c93-162">資産には、チェス盤の 3D オブジェクト メッシュと FBX 形式の駒、およびマテリアルに使用する TGA 形式のテクスチャ マップが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c6c93-162">Assets include the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="c6c93-163">[FBX インポート オプション] ウィンドウが表示されたら、 **[マテリアル]** セクションを展開し、 **[マテリアルのインポート方法]** を **[マテリアルを作成しない]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-163">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="c6c93-164">**[Import All]\(すべてインポート\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-164">Select **Import All**.</span></span>

![FBX インポート オプション](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="c6c93-166">これで、資産に対して行う必要な操作は終わりました。</span><span class="sxs-lookup"><span data-stu-id="c6c93-166">That's all you need to do for the assets.</span></span> <span data-ttu-id="c6c93-167">次の一連のタスクでは、ブループリントを使用してアプリケーションの構成要素を作成します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-167">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="c6c93-168">ブループリントの追加</span><span class="sxs-lookup"><span data-stu-id="c6c93-168">Adding blueprints</span></span>

1. <span data-ttu-id="c6c93-169">**[Content Browser]\(コンテンツ ブラウザー\)** で **[新規追加] > [新しいフォルダー]** の順に選択し、「**ブループリント**」という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="c6c93-169">Select **Add New > New Folder** in the **Content Browser** and name it **Blueprints**.</span></span> 

> [!NOTE]
> <span data-ttu-id="c6c93-170">[ブループリント](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html)を初めて使用する場合、これらのブループリントは、新しい種類のアクターとスクリプト レベルのイベントを作成するためのノードベースのインターフェースを提供する特別な資産になります。</span><span class="sxs-lookup"><span data-stu-id="c6c93-170">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="c6c93-171">**[ブループリント]** フォルダーをダブルクリックし、右クリックして **[ブループリント クラス]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-171">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="c6c93-172">**[Actor]\(アクター\)** を選択して、ブループリントに **Board** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="c6c93-172">Select **Actor** and name the blueprint **Board**.</span></span> 

![ブループリントの親クラスを選択する](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="c6c93-174">次のスクリーンショットに示すように、新しい **[ボード]** ブループリントが **[ブループリント]** フォルダーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6c93-174">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![新しい Board ブループリント](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="c6c93-176">作成したオブジェクトにマテリアルを追加するためのすべての設定が完了しました。</span><span class="sxs-lookup"><span data-stu-id="c6c93-176">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="c6c93-177">マテリアルの操作</span><span class="sxs-lookup"><span data-stu-id="c6c93-177">Working with materials</span></span>
<span data-ttu-id="c6c93-178">作成したオブジェクトは既定で灰色になりますが、これはあまり見栄えのよいものではありません。</span><span class="sxs-lookup"><span data-stu-id="c6c93-178">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="c6c93-179">このチュートリアルの最後のタスク セットは、オブジェクトにマテリアルとメッシュを追加することです。</span><span class="sxs-lookup"><span data-stu-id="c6c93-179">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="c6c93-180">**[ボード]** をダブルクリックして、ブループリント エディターを開きます。</span><span class="sxs-lookup"><span data-stu-id="c6c93-180">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="c6c93-181">**[コンポーネント]** パネルから **[コンポーネントの追加] > [シーン]** をクリックし、**Root** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="c6c93-181">Select **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="c6c93-182">以下のスクリーンショットでは、**Root** が **DefaultSceneRoot** の子として表示されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c6c93-182">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![ブループリントでのルートの置換](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="c6c93-184">**ルート** をクリックアンドドラッグして **DefaultSceneRoot** に置換し、ビューポート内の球体を削除します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-184">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![ルートを置き換える](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="c6c93-186">**[コンポーネント]** パネルから **[コンポーネントの追加] > [Static Mesh]\(静的メッシュ\)** を選択し、**SM_Board** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="c6c93-186">Select **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="c6c93-187">これは、**ルート** の下に子オブジェクトとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="c6c93-187">It will appear as a child object under **Root**.</span></span>

![スタティック メッシュの追加](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="c6c93-189">**SM_Board** を選択し、 **[詳細]** パネルの **[Static Mesh]\(静的メッシュ\)** セクションまで下にスクロールして、ドロップダウンから **ChessBoard** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-189">Select **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![ビューポート内のボード メッシュ](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="c6c93-191">引き続き **[詳細]** パネルで、 **[Materials]\(マテリアル\)** セクションを展開し、ドロップダウンから **[Create New Asset]\(新しい資産の作成\) > [Material]\(マテリアル\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-191">Still in the **Details** panel, expand the **Materials** section and select **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="c6c93-192">この資産に **M_ChessBoard** という名前を付けて、**ChessAssets** フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-192">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![新しいマテリアルを作成する](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="c6c93-194">マテリアル エディターを開くには、**M_ChessBoard** マテリアルのイメージをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-194">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![マテリアル エディターを開く](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="c6c93-196">マテリアル エディターで右クリックして、 **[Texture Sample]\(テクスチャ サンプル\)** を検索します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-196">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="c6c93-197">**[詳細]** パネルの **[Material Expression Texture Base]\(マテリアル式テクスチャ ベース\)** セクションを展開し、 **[テクスチャ]** を **ChessBoard_Albedo** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-197">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="c6c93-198">**[RGB]** 出力ピンを **M_ChessBoard** の [Base Color]\(基本色\) ピンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-198">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![基本色を設定する](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="c6c93-200">前のステップをさらに 4 回繰り返して、次の設定でさらに 4 つの **[テクスチャ サンプル]** ノードを作成します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-200">Repeat the previous step 4 more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="c6c93-201">**[テクスチャ]** を **ChessBoard_AO** に設定し、**RGB** を **[アンビエント オクルージョン]** ピンにリンクします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-201">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="c6c93-202">**[テクスチャ]** を **ChessBoard_Metal** に設定し、**RGB** を **[メタリック]** ピンにリンクします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-202">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="c6c93-203">**[テクスチャ]** を **ChessBoard_Normal** に設定し、**RGB** を **[ノーマル]** ピンにリンクします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-203">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="c6c93-204">**[テクスチャ]** を **ChessBoard_Rough** に設定し、**RGB** を **[ラフネス]** ピンにリンクします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-204">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="c6c93-205">**[Save]** (保存) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-205">Click **Save**.</span></span> 

![残りのテクスチャを接続する](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="c6c93-207">続行する前に、マテリアルの設定が上のスクリーンショットのようになっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c6c93-207">Make sure your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="c6c93-208">シーンへのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="c6c93-208">Populating the scene</span></span>
<span data-ttu-id="c6c93-209">**[ボード]** ブループリントに戻ると、作成したばかりのマテリアルが適用されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="c6c93-209">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="c6c93-210">あとは、シーンをセットアップするだけです。</span><span class="sxs-lookup"><span data-stu-id="c6c93-210">All that's left is setting up the scene!</span></span> <span data-ttu-id="c6c93-211">最初に、以下のプロパティを変更して、ボードが適切なサイズであり、シーンに配置されたときに角度が適切であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-211">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="c6c93-212">**[スケール]** を **(0.05、0.05、0.05)** に設定し、 **[Z 回転]** を **90** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-212">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="c6c93-213">上部のツールバーの **[コンパイル]** をクリックし、 **[保存]** をクリックして、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="c6c93-213">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![マテリアルが適用されたチェス盤](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="c6c93-215">**[キューブ] > [編集] > [削除]** を右クリックして、 **[ボード]** を **[コンテンツ ブラウザー]** からビューポートにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-215">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="c6c93-216">**[位置]** を **X = 80**、**Y = 0**、および **Z = -20** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-216">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="c6c93-217">**[Play]\(プレイ\)** ボタンを選択して、新しいチェス盤をレベルに表示します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-217">Select the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="c6c93-218">**Esc** キーを押してエディターに戻ります。</span><span class="sxs-lookup"><span data-stu-id="c6c93-218">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="c6c93-219">次に、ボードで行ったのと同じ手順に従って、チェスの駒を作成します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-219">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="c6c93-220">**[ブループリント]** フォルダーに移動し、右クリックして **[Blueprint Class]\(ブループリント クラス\)** を選択し、 **[Actor]\(アクター\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-220">Go to the **Blueprints** folder, right-click, and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="c6c93-221">このアクターに **WhiteKing** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="c6c93-221">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="c6c93-222">**WhiteKing** をダブルクリックしてブループリント エディターで開き、 **[コンポーネントの追加] > [シーン]** を選択して、**Root** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="c6c93-222">Double-click **WhiteKing** to open it in the Blueprint Editor, select **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="c6c93-223">**Root** を **DefaultSceneRoot** にドラッグアンドドロップして置換します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-223">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="c6c93-224">**[コンポーネントの追加]> [スタティック メッシュ]** をクリックし、**SM_King** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="c6c93-224">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="c6c93-225">[詳細] パネルで、 **[Static Mesh]\(スタティック メッシュ\)** を **Chess_King** に設定し、 **[Material]\(マテリアル\)** を、**M_ChessWhite** という名前の新しいマテリアルに設定します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-225">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="c6c93-226">マテリアル エディターで、**M_ChessWhite** を開き、次の **[テクスチャ サンプル]** ノードを次のものに接続します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-226">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
   * <span data-ttu-id="c6c93-227">**[テクスチャ]** を **ChessWhite_Albedo** に設定し、 **[RGB]** を **[Base Color]\(基本色\)** ピンにリンクします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-227">Set **Texture** to **ChessWhite_Albedo** and link the **RGB** to the **Base Color** pin.</span></span>
    * <span data-ttu-id="c6c93-228">**[テクスチャ]** を **ChessWhite_AO** に設定し、**RGB** を **[アンビエント オクルージョン]** ピンにリンクします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-228">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="c6c93-229">**[テクスチャ]** を **ChessWhite_Metal** に設定し、**RGB** を **[メタリック]** ピンにリンクします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-229">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="c6c93-230">**[テクスチャ]** を **ChessWhite_Normal** に設定し、**RGB** を **[ノーマル]** ピンにリンクします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-230">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="c6c93-231">**[テクスチャ]** を **ChessWhite_Rough** に設定し、**RGB** を **[ラフネス]** ピンにリンクします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-231">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="c6c93-232">**[Save]** (保存) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-232">Click **Save**.</span></span> 

<span data-ttu-id="c6c93-233">続行する前に、**M_ChessKing** マテリアルは次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="c6c93-233">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![チェスのキングのマテリアルを作成する](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="c6c93-235">もう少しで完了です。あとは新しいチェスの駒をシーンに追加するだけです。</span><span class="sxs-lookup"><span data-stu-id="c6c93-235">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="c6c93-236">**WhiteKing** ブループリントを開いて、 **[Scale]\(スケール\)** を **(0.05, 0.05, 0.05)** に、 **[Z 回転]** を **90** に変更します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-236">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="c6c93-237">ブループリントをコンパイルして保存した後、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="c6c93-237">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="c6c93-238">**WhiteKing** をビューポートにドラッグし、 **[ワールド アウトライナー]** パネルに切り替え、**WhiteKing** を **[ボード]** にドラッグして、子オブジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="c6c93-238">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![[World Outliner]\(ワールド アウトライナー\)](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="c6c93-240">**[詳細]** パネルの **[Transform]\(トランスフォーム\)** で、**WhiteKing** の **[Location]\(位置\)** を **X = -26**、**Y = 4**、**Z = 0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-240">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="c6c93-241">これでおしまいです!</span><span class="sxs-lookup"><span data-stu-id="c6c93-241">That's a wrap!</span></span> <span data-ttu-id="c6c93-242">**[Play]\(再生\)** を選択して、データ設定されているレベルの動作を確認し、終了する準備ができたら **Esc** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c6c93-242">Select **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="c6c93-243">簡単なプロジェクトを作成するだけのために多くの基本について学習しましたが、シリーズの次の部分である Mixed Reality の設定に進む準備ができました。</span><span class="sxs-lookup"><span data-stu-id="c6c93-243">You covered a lot of ground just creating a simple project, but now you're ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="c6c93-244">次のセクション: 3.Mixed Reality 用のプロジェクト設定</span><span class="sxs-lookup"><span data-stu-id="c6c93-244">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)