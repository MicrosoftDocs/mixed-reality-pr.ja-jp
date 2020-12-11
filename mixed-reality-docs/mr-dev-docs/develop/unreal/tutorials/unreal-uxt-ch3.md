---
title: 3. Mixed Reality のプロジェクト設定
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用してチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 3
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, はじめに, mrtk, uxt, UX ツール, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 26bb874578e56b21d319741b8b1c1ff6decebe4b
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609703"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="40e4e-104">3.Mixed Reality のプロジェクト設定</span><span class="sxs-lookup"><span data-stu-id="40e4e-104">3. Setting up your project for mixed reality</span></span>

<span data-ttu-id="40e4e-105">前のチュートリアルでは、チェス アプリ プロジェクトの設定に時間を費やしました。</span><span class="sxs-lookup"><span data-stu-id="40e4e-105">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="40e4e-106">このセクションでは、Mixed Reality 開発用にアプリを設定する手順について説明します。これは、AR セッションを追加することを意味します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-106">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="40e4e-107">このタスクには ARSessionConfig データ資産を使用します。これには、空間マッピングやオクルージョンなどの便利な AR 設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="40e4e-107">You'll be using an ARSessionConfig data asset for this task, which has useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="40e4e-108">[ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) 資産と [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) クラスの詳細については、Unreal のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="40e4e-108">You can find more details about the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class in Unreal's documentation.</span></span>

## <a name="objectives"></a><span data-ttu-id="40e4e-109">目標</span><span class="sxs-lookup"><span data-stu-id="40e4e-109">Objectives</span></span>

* <span data-ttu-id="40e4e-110">Unreal Engine の AR 設定の操作</span><span class="sxs-lookup"><span data-stu-id="40e4e-110">Working with Unreal Engine's AR settings</span></span>
* <span data-ttu-id="40e4e-111">ARSessionConfig データ資産の使用</span><span class="sxs-lookup"><span data-stu-id="40e4e-111">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="40e4e-112">ポーンとゲーム モードの設定</span><span class="sxs-lookup"><span data-stu-id="40e4e-112">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="40e4e-113">セッション資産の追加</span><span class="sxs-lookup"><span data-stu-id="40e4e-113">Adding the session asset</span></span>

<span data-ttu-id="40e4e-114">Unreal の AR セッションは、それ自体では発生しません。</span><span class="sxs-lookup"><span data-stu-id="40e4e-114">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="40e4e-115">セッションを使用するには、ARSessionConfig データ資産を処理する必要があります。それが次のタスクです。</span><span class="sxs-lookup"><span data-stu-id="40e4e-115">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="40e4e-116">**[コンテンツ ブラウザー]** で、 **[新規追加] > [その他] > [Data Asset]\(データ資産\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="40e4e-116">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="40e4e-117">ルートの **[コンテンツ]** フォルダー レベルであることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="40e4e-117">Make sure you're at the root **Content** folder level.</span></span>
    * <span data-ttu-id="40e4e-118">**ARSessionConfig** を選択し、 **[選択]** をクリックして、アセットに **ARSessionConfig** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="40e4e-118">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![データ資産を作成する](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="40e4e-120">**ARSessionConfig** をダブルクリックして開き、既定の設定をすべてそのままにして、 **[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="40e4e-120">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="40e4e-121">メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="40e4e-121">Return to the Main window.</span></span>

![AR セッション構成](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="40e4e-123">それが完了したら、次のステップとして、レベルが読み込まれたら AR セッションが開始し、レベルが終了したら停止するようにします。</span><span class="sxs-lookup"><span data-stu-id="40e4e-123">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="40e4e-124">さいわい、Unreal には、**レベル ブループリント** と呼ばれる特別なブループリントがあり、レベル全体のグローバル イベント グラフとして機能します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-124">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="40e4e-125">**レベル ブループリント** で ARSessionConfig アセットを接続すると、ゲームの再生が開始されたときに AR セッションが正常に起動します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-125">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="40e4e-126">エディタのツールバーから、 **[ブループリント] > [レベル ブループリントを開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="40e4e-126">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span>

![オープン レベルのブループリント](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="40e4e-128">実行ノード (左向き矢印アイコン) を **[Event BeginPlay]\(イベント BeginPlay\)** からドラッグして離し、 **[Start AR Session]\(AR セッションの開始\)** ノードを検索して Eenter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-128">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release, then search for the **Start AR Session** node and hit enter.</span></span>  
    * <span data-ttu-id="40e4e-129">**[セッション構成]** の下にある **[アセットの選択]** ドロップダウンをクリックし、**ARSessionConfig** アセットを選択します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-129">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span>

![AR セッションを開始する](images/unreal-uxt/3-start-ar-session.PNG)

6. <span data-ttu-id="40e4e-131">EventGraph 内の任意の場所を右クリックし、新しい **Event EndPlay** ノードを作成します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-131">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> <span data-ttu-id="40e4e-132">実行ピンをドラッグして離してから、 **[Stop AR Session]\(AR セッションの停止\)** ノードを検索して Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-132">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter.</span></span> <span data-ttu-id="40e4e-133">レベルが終了しても AR セッションがまだ実行されている場合、ヘッドセットへのストリーミング中にアプリを再起動すると、特定の機能が動作しなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="40e4e-133">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>
    * <span data-ttu-id="40e4e-134">**[コンパイル]** 、 **[保存]** をクリックして、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="40e4e-134">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![AR セッションの停止](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="40e4e-136">ポーンを作成する</span><span class="sxs-lookup"><span data-stu-id="40e4e-136">Create a Pawn</span></span>

<span data-ttu-id="40e4e-137">この時点では、プロジェクトにはまだプレーヤー オブジェクトが必要です。</span><span class="sxs-lookup"><span data-stu-id="40e4e-137">At this point, the project still needs a player object.</span></span> <span data-ttu-id="40e4e-138">Unreal では、**ポーン** はゲーム内のユーザーを表しますが、この場合は HoloLens 2 になります。</span><span class="sxs-lookup"><span data-stu-id="40e4e-138">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="40e4e-139">**[コンテンツ]** フォルダーで、 **[新規追加] > [ブループリント クラス]** をクリックし、下部にある **[すべてのクラス]** セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-139">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span>
    * <span data-ttu-id="40e4e-140">**DefaultPawn** を検索し、 **[選択]** をクリックして、**MRPawn** という名前を付けてから、そのアセットをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="40e4e-140">Search for **DefaultPawn**, click **Select**, name it **MRPawn**, and double-click the asset to open.</span></span>

![DefaultPawn から継承して新しいポーンを作成する](images/unreal-uxt/3-defaultpawn.PNG)

2. <span data-ttu-id="40e4e-142">**[コンポーネント]** パネルから **[コンポーネントの追加] > [カメラ]** の順にクリックし、**Camera** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="40e4e-142">Click **Add Component > Camera** from the **Components** panel and name it **Camera**.</span></span> <span data-ttu-id="40e4e-143">**Camera** コンポーネントがルート (**CollisionComponent**) の直接の子であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-143">Make sure that the **Camera** component is a direct child of the root (**CollisionComponent**).</span></span> <span data-ttu-id="40e4e-144">これで、プレーヤー カメラは HoloLens 2 デバイスと移動できるようになります。</span><span class="sxs-lookup"><span data-stu-id="40e4e-144">This allows the player camera to move with the HoloLens 2 device.</span></span>

> [!NOTE]
> <span data-ttu-id="40e4e-145">既定では、ポーンにはメッシュと衝突コンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="40e4e-145">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="40e4e-146">ほとんどの Unreal プロジェクトでは、ポーンは他のコンポーネントと競合する可能性のあるソリッド オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="40e4e-146">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="40e4e-147">ポーンとユーザーは Mixed Reality で同じであるため、衝突せずにホログラムを通過できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="40e4e-147">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span>

3. <span data-ttu-id="40e4e-148">**[コンポーネント]** パネルから **CollisionComponent** を選択し、 **[詳細]** パネルの **[衝突]** セクションまでスクロールします。</span><span class="sxs-lookup"><span data-stu-id="40e4e-148">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span>
    * <span data-ttu-id="40e4e-149">**[衝突プリセット]** ドロップダウンをクリックして、値を **NoCollision** に変更します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-149">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span>
    * <span data-ttu-id="40e4e-150">**MeshComponent** に対しても同じ操作を行います。</span><span class="sxs-lookup"><span data-stu-id="40e4e-150">Do the same for the **MeshComponent**</span></span>

![ポーンの衝突プリセットを調整する](images/unreal-uxt/3-nocollision.PNG)

4. <span data-ttu-id="40e4e-152">ブループリントを **コンパイル** して、**保存** します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-152">**Compile** and **Save** the Blueprint.</span></span>

<span data-ttu-id="40e4e-153">ここで作業を完了したら、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="40e4e-153">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="40e4e-154">ゲーム モードを作成する</span><span class="sxs-lookup"><span data-stu-id="40e4e-154">Create a Game Mode</span></span>

<span data-ttu-id="40e4e-155">Mixed Reality セットアップの最後のステップはゲーム モードです。</span><span class="sxs-lookup"><span data-stu-id="40e4e-155">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="40e4e-156">ゲーム モードでは、使用する既定のポーンなど、ゲームやエクスペリエンスのさまざまな設定を決定します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-156">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="40e4e-157">**[Content]\(コンテンツ\)** フォルダーで **[Add New]\(新規追加\) > [Blueprint Class]\(ブループリント クラス\)** をクリックし、親クラスとして **[Game Mode Base]\(ゲーム モード ベース\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-157">Click **Add New > Blueprint Class** in the **Content** folder and select **Game Mode Base** as the parent class.</span></span> <span data-ttu-id="40e4e-158">**MRGameMode** という名前を指定し、ダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="40e4e-158">Name it **MRGameMode** and double-click to open.</span></span>

![コンテンツ ブラウザー内の MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="40e4e-160">**[詳細]** パネルの **[クラス]** セクションに移動し、 **[既定のポーン クラス]** を **MRPawn** に変更します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-160">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span>
    * <span data-ttu-id="40e4e-161">**[コンパイル]** 、 **[保存]** をクリックして、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="40e4e-161">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![既定のポーン クラスを設定する](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="40e4e-163">**[編集] > [プロジェクトの設定]** を選択し、左側のリストで **[マップとモード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="40e4e-163">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span>
    * <span data-ttu-id="40e4e-164">**[既定モード]** を展開し、 **[既定のゲーム モード]** を **MRGameMode** に変更します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-164">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span>
    * <span data-ttu-id="40e4e-165">**[既定のマップ]** を展開し、**EditorStartupMap** と **GameDefaultMap** の両方を **[メイン]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="40e4e-165">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="40e4e-166">エディターを閉じて再度開くか、ゲームをプレイすると、メイン マップが既定で選択されるようになります。</span><span class="sxs-lookup"><span data-stu-id="40e4e-166">When you close and reopen the editor or play the game, the Main map will now be selected by default.</span></span>

![プロジェクト設定 - マップ & モード](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="40e4e-168">プロジェクトで Mixed Reality を完全にセットアップしたら、次のチュートリアルに進み、シーンにユーザー入力を追加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="40e4e-168">With the project fully set up for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span>

[<span data-ttu-id="40e4e-169">次のセクション: 4.シーンを対話型にする</span><span class="sxs-lookup"><span data-stu-id="40e4e-169">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)
