---
title: HoloLens プロジェクトの作成
description: HoloLens Mixed Reality 開発用のシーン オブジェクトと入力対話式操作を含む Unreal プロジェクトを正しく構成する方法について説明します。
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Unreal エディター, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, ドキュメント, ガイド, 機能, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 移植, アップグレード
ms.openlocfilehash: 3b2b88ac897a8791fec1ca2942d0db34efcee598
ms.sourcegitcommit: be33fcda10d1cb98df90b428a923289933d42c77
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98672739"
---
# <a name="creating-a-hololens-project"></a><span data-ttu-id="882f2-104">HoloLens プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="882f2-104">Creating a HoloLens project</span></span>

<span data-ttu-id="882f2-105">最初に必要なのは、作業するプロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="882f2-105">The first thing you need is a project to work with.</span></span> <span data-ttu-id="882f2-106">Unreal で初めて開発する場合は、Epic Launcher から[サポート ファイルをダウンロードする](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)必要があります。</span><span class="sxs-lookup"><span data-stu-id="882f2-106">If you're a first-time Unreal developer, you'll need to [download supporting files](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="882f2-107">Unreal Engine を起動します。</span><span class="sxs-lookup"><span data-stu-id="882f2-107">Launch Unreal Engine</span></span>
2. <span data-ttu-id="882f2-108">**[New Project Categories]\(新しいプロジェクトのカテゴリ\)** で、 **[Games]\(ゲーム\)** を選択して **[Next]\(次へ\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="882f2-108">In the **New Project Categories**, select **Games** and click **Next**:</span></span>

![[Games]\(ゲーム\) が強調表示されている最近のプロジェクトのウィンドウ](images/unreal-quickstart-img-01.png)

3. <span data-ttu-id="882f2-110">**[Blank]\(空\)** テンプレートを選択して **[Next]\(次へ\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="882f2-110">Select the **Blank** template and click **Next**:</span></span>

![空のテンプレートが強調表示されている Unreal プロジェクト ブラウザー ウィンドウ](images/unreal-quickstart-img-02.png)

4. <span data-ttu-id="882f2-112">**[Project Settings]\(プロジェクト設定\)** で、 **[C++]、[Scalable 3D or 2D]\(スケーラブル 3D または 2D\)、[Mobile/Tablet]\(モバイル/タブレット\)** 、 **[No Starter Content]\(スターター コンテンツを有効にしない\)** を設定し、保存場所を選択して、 **[Create Project]\(プロジェクトの作成)** をクリックします</span><span class="sxs-lookup"><span data-stu-id="882f2-112">In the **Project Settings**, set **C++, Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content**, then choose a save location and click **Create Project**</span></span>

> [!NOTE] <span data-ttu-id="882f2-113">後で OpenXR プラグインを使用できるようにするため、ブループリント プロジェクトではなく C++ を使用しています。</span><span class="sxs-lookup"><span data-stu-id="882f2-113">You're using a C++ rather than a Blueprint project in order to be ready to use the OpenXR plugin later.</span></span> <span data-ttu-id="882f2-114">この QuickStart では、Unreal Engine に付属する既定の OpenXR プラグインを使用します。</span><span class="sxs-lookup"><span data-stu-id="882f2-114">This QuickStart uses the default OpenXR plugin that comes with Unreal Engine.</span></span> <span data-ttu-id="882f2-115">ただし、公式の Microsoft OpenXR プラグインをダウンロードして使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="882f2-115">However, downloading and using the official Microsoft OpenXR plugin is recommended.</span></span> <span data-ttu-id="882f2-116">それには、プロジェクトが C++ プロジェクトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="882f2-116">That requires the project to be a C++ project.</span></span>

![プロジェクト、パフォーマンス、ターゲット プラットフォーム、スターター コンテンツの選択が強調表示されているプロジェクト設定ウィンドウ](images/unreal-quickstart-img-03.png)

<span data-ttu-id="882f2-118">新しいプロジェクトが Unreal エディターで自動的に開かれます。つまり、次のセクションに進む準備はできています。</span><span class="sxs-lookup"><span data-stu-id="882f2-118">Your new project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="882f2-119">必要なプラグインの有効化</span><span class="sxs-lookup"><span data-stu-id="882f2-119">Enabling required plugins</span></span>

<span data-ttu-id="882f2-120">オブジェクトをシーンに追加する前に、2 つのプラグインを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="882f2-120">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="882f2-121">**[編集] > [プラグイン]** を開き、組み込みオプション リストから **[拡張現実]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="882f2-121">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span>
* <span data-ttu-id="882f2-122">**HoloLens** まで下にスクロールし、 **[Enabled]\(有効\)** をオンにします</span><span class="sxs-lookup"><span data-stu-id="882f2-122">Scroll down to **HoloLens** and check **Enabled**</span></span>

![拡張現実セクションが開き HoloLens が強調表示されているプラグイン ウィンドウ](images/unreal-quickstart-img-04.png)

2. <span data-ttu-id="882f2-124">右上の検索ボックスに「**OpenXR**」と入力し、**OpenXR** および **OpenXRMsftHandInteraction** プラグインを有効にします。</span><span class="sxs-lookup"><span data-stu-id="882f2-124">Type **OpenXR** in the search box at the top right and enable the **OpenXR** and **OpenXRMsftHandInteraction** plugins:</span></span>

![OpenXR が有効になっているプラグイン ウィンドウ](images/unreal-quickstart-img-05.jpg)

![OpenXRMsftHandInteraction が有効になっているプラグイン ウィンドウ](images/unreal-quickstart-img-06.jpg)

3. <span data-ttu-id="882f2-127">エディターを再起動します</span><span class="sxs-lookup"><span data-stu-id="882f2-127">Restart your editor</span></span>

> [!NOTE]
> <span data-ttu-id="882f2-128">このチュートリアルでは OpenXR を使用しますが、上でインストールした 2 つのプラグインには、現在、HoloLens 開発用の完全な機能セットはありません。</span><span class="sxs-lookup"><span data-stu-id="882f2-128">This tutorial uses OpenXR, but the two plugins you've installed above don't currently provide the full feature set for HoloLens development.</span></span> <span data-ttu-id="882f2-129">後で使用する "ピンチ" ジェスチャには HandInteraction プラグインで十分ですが、基本機能以外を使用するには、[OpenXR プラグインをダウンロードする](https://github.com/microsoft/Microsoft-OpenXR-Unreal)必要があります。</span><span class="sxs-lookup"><span data-stu-id="882f2-129">The HandInteraction plugin will suffice for the "Pinch" gesture you'll use later, but if you want to go beyond the basics you'll need to [download the OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

<span data-ttu-id="882f2-130">プラグインを有効にすると、それにコンテンツを設定できます。</span><span class="sxs-lookup"><span data-stu-id="882f2-130">With the plugins enabled, you can focus on filling it with content.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="882f2-131">レベルの作成</span><span class="sxs-lookup"><span data-stu-id="882f2-131">Creating a level</span></span>

<span data-ttu-id="882f2-132">次のタスクは、参照とスケール用の開始点とキューブを使用してプレーヤーのセットアップを作成することです。</span><span class="sxs-lookup"><span data-stu-id="882f2-132">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="882f2-133">**[ファイル] > [新しいレベル]** を選択し、 **[空のレベル]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="882f2-133">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="882f2-134">この時点では、ビューポートの既定のシーンは空です</span><span class="sxs-lookup"><span data-stu-id="882f2-134">The default scene in the viewport should now be empty</span></span>
2. <span data-ttu-id="882f2-135">**[Modes]\(モード\)** タブから **[Basic]\(基本\)** を選択し、**PlayerStart** をシーンにドラッグします</span><span class="sxs-lookup"><span data-stu-id="882f2-135">From the **Modes** tab, select **Basic** and drag **PlayerStart** into the scene</span></span>
* <span data-ttu-id="882f2-136">**[Details]\(詳細\)** タブで、 **[Location]\(位置\)** を **X = 0、Y = 0**、**Z = 0** に設定して、アプリの起動時にユーザーをシーンの中心に設定します</span><span class="sxs-lookup"><span data-stu-id="882f2-136">In the **Details** tab, set **Location** to **X = 0, Y = 0,** and **Z = 0** to place the user at the center of the scene when the app starts</span></span>

![位置とプレーヤーのスタートが追加された Unreal エディター シーン](images/unreal-quickstart-img-07.png)

3. <span data-ttu-id="882f2-138">**[Basic]\(基本\)** タブから **Cube** をシーンにドラッグします</span><span class="sxs-lookup"><span data-stu-id="882f2-138">From the **Basic** tab, drag a **Cube** into the scene</span></span>
* <span data-ttu-id="882f2-139">キューブの **[Location]\(位置\)** を **X = 50、Y = 0**、**Z = 0** に設定して、開始時にプレーヤーから 50 cm 離れた位置にキューブを配置します</span><span class="sxs-lookup"><span data-stu-id="882f2-139">Set the cube's **Location** to **X = 50, Y = 0**, and **Z = 0** to position the cube 50 cm away from the player at start</span></span>
* <span data-ttu-id="882f2-140">キューブの **[Scale]\(スケール\)** を **X = 0.2、Y = 0.2**、**Z = 0.2** に変更します</span><span class="sxs-lookup"><span data-stu-id="882f2-140">Change  the cube's **Scale** to **X = 0.2, Y = 0.2**, and **Z = 0.2**</span></span> 

<span data-ttu-id="882f2-141">シーンにライトを追加しない限り、キューブを表示することはできません。これは、シーンをテストする前の最後のタスクです。</span><span class="sxs-lookup"><span data-stu-id="882f2-141">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="882f2-142">**[Modes]\(モード\)** パネルで **[Lights]\(ライト\)** タブに切り替えて、**Directional Light** をシーンにドラッグします</span><span class="sxs-lookup"><span data-stu-id="882f2-142">In the **Modes** panel, switch to the **Lights** tab and drag a **Directional Light** into the scene</span></span>
* <span data-ttu-id="882f2-143">ライトが見えるように、**PlayerStart** の上にそれを配置します</span><span class="sxs-lookup"><span data-stu-id="882f2-143">Position the light above **PlayerStart** so you can see it</span></span>

![キューブと指向性ライトが追加された Unreal エディターのシーン](images/unreal-quickstart-img-08.png)

5. <span data-ttu-id="882f2-145">**[File]\(ファイル\) > [Save Current]\(現在を保存\)** に移動し、レベルに **Main** という名前を付けて、 **[Save]\(保存\)** を選択します</span><span class="sxs-lookup"><span data-stu-id="882f2-145">Go to **File > Save Current**, name your level **Main**, and select **Save**</span></span>

<span data-ttu-id="882f2-146">シーンを設定したら、ツールバーの **[再生]** を押して、キューブの動作を確認します。</span><span class="sxs-lookup"><span data-stu-id="882f2-146">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="882f2-147">作業内容を鑑賞したら、Esc を押してアプリケーションを停止します。</span><span class="sxs-lookup"><span data-stu-id="882f2-147">When you're finished admiring your work, press Esc to stop the application.</span></span>

![画面の中央にキューブがあるプレイ モードのシーン](images/unreal-quickstart-img-09.png)

<span data-ttu-id="882f2-149">シーンをセットアップしたので、AR でいくつかの基本的な対話式操作を実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="882f2-149">Now that the scene is set up, lets get it ready for some basic interactions in AR.</span></span> <span data-ttu-id="882f2-150">最初に、AR セッションを作成する必要があり、ブループリントを追加してハンド インタラクションを可能にできます。</span><span class="sxs-lookup"><span data-stu-id="882f2-150">First, you need to create an AR Session and can add blueprints to enable hand interaction.</span></span>

## <a name="adding-a-session-asset"></a><span data-ttu-id="882f2-151">セッション アセットの追加</span><span class="sxs-lookup"><span data-stu-id="882f2-151">Adding a session asset</span></span>

<span data-ttu-id="882f2-152">Unreal の AR セッションは、それ自体では発生しません。</span><span class="sxs-lookup"><span data-stu-id="882f2-152">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="882f2-153">セッションを使用するには、ARSessionConfig データ資産を処理する必要があります。それが次のタスクです。</span><span class="sxs-lookup"><span data-stu-id="882f2-153">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="882f2-154">**[Content Browser]\(コンテンツ ブラウザー\)** で、 **[Add New]\(新規追加\) > [Miscellaneous]\(その他\) > [Data Asset]\(データ アセット\)** を選択し、ルート コンテンツ フォルダー レベルであることを確認します</span><span class="sxs-lookup"><span data-stu-id="882f2-154">In the **Content Browser**, select **Add New > Miscellaneous > Data Asset** and make sure you're at the root Content folder level</span></span>
2. <span data-ttu-id="882f2-155">**ARSessionConfig** を選択し、 **[Select]\(選択\)** をクリックして、アセットに **ARSessionConfig** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="882f2-155">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**:</span></span>

![AR セッション構成アセットが強調表示されている [Pick data asset class]\(データ資産クラス選択\) ウィンドウ](images/unreal-quickstart-img-10.png)

2. <span data-ttu-id="882f2-157">**ARSessionConfig** をダブルクリックして開き、既定の設定をすべてそのままにして **[Save]\(保存\)** を選択し、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="882f2-157">Double-click **ARSessionConfig** to open it, **Save** with all default settings, and return to the Main window:</span></span>

![AR セッション構成アセットの詳細ウィンドウ](images/unreal-quickstart-img-11.png)

<span data-ttu-id="882f2-159">それが完了したら、次のステップとして、レベルが読み込まれたら AR セッションが開始し、レベルが終了したら停止するようにします。</span><span class="sxs-lookup"><span data-stu-id="882f2-159">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="882f2-160">さいわい、Unreal には、**レベル ブループリント** と呼ばれる特別なブループリントがあり、レベル全体のグローバル イベント グラフとして機能します。</span><span class="sxs-lookup"><span data-stu-id="882f2-160">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="882f2-161">レベル ブループリントで ARSessionConfig アセットを接続すると、ゲームの再生が開始されたときに AR セッションが正常に起動します。</span><span class="sxs-lookup"><span data-stu-id="882f2-161">Connecting the ARSessionConfig asset in the Level Blueprint guarantees the AR session will fire right when the game starts playing.</span></span>

3. <span data-ttu-id="882f2-162">エディターのツール バーから、 **[Blueprints]\(ブループリント\) > [Open Level Blueprint]\(Level ブループリントを開く\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="882f2-162">From the editor toolbar, select **Blueprints > Open Level Blueprint**:</span></span>

![[Open Level Blueprint]\(Level ブループリントを開く\) オプションが強調表示されているブループリント メニュー](images/unreal-quickstart-img-12.png)

4. <span data-ttu-id="882f2-164">実行ノード (左向き矢印アイコン) を **Event BeginPlay** からドラッグして離します</span><span class="sxs-lookup"><span data-stu-id="882f2-164">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release</span></span>
* <span data-ttu-id="882f2-165">**[Start AR Session]\(AR セッションの開始\)** ノードを検索し、Enter キーを押します</span><span class="sxs-lookup"><span data-stu-id="882f2-165">Search for the **Start AR Session node** and hit enter</span></span>
* <span data-ttu-id="882f2-166">**[Session Config]\(セッション構成\)** の下にある **[Select Asset]\(アセットの選択\)** ドロップダウンをクリックし、**ARSessionConfig** アセットを選択します</span><span class="sxs-lookup"><span data-stu-id="882f2-166">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset</span></span>

![プレイ開始イベントが AR セッション開始関数に接続されたブループリント グラフ](images/unreal-quickstart-img-13.png)

5. <span data-ttu-id="882f2-168">EventGraph 内の任意の場所を右クリックし、新しい **Event EndPlay** ノードを作成します。</span><span class="sxs-lookup"><span data-stu-id="882f2-168">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> 
* <span data-ttu-id="882f2-169">実行ピンをドラッグして離してから、 **[Stop AR Session]\(AR セッションの停止\)** ノードを検索して Enter キーを押します</span><span class="sxs-lookup"><span data-stu-id="882f2-169">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter</span></span> 
* <span data-ttu-id="882f2-170">**[Compile]\(コンパイル\)** 、 **[Save]\(保存\)** の順にクリックして、メイン ウィンドウに戻ります</span><span class="sxs-lookup"><span data-stu-id="882f2-170">Hit **Compile**, then **Save** and return to the Main window</span></span>

> [!IMPORTANT]
> <span data-ttu-id="882f2-171">レベルが終了しても AR セッションがまだ実行されている場合、ヘッドセットへのストリーミング中にアプリを再起動すると、特定の機能が動作しなくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="882f2-171">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>

![AR セッション停止関数に接続された EventEndPlay ノード](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a><span data-ttu-id="882f2-173">入力の設定</span><span class="sxs-lookup"><span data-stu-id="882f2-173">Setting up inputs</span></span>

1. <span data-ttu-id="882f2-174">**[Edit]\(編集\) > [Project Settings]\(プロジェクトの設定\)** を編集し、 **[Engine]\(エンジン\) > [Input]\(入力\)** に移動します</span><span class="sxs-lookup"><span data-stu-id="882f2-174">Select **Edit > Project Settings** and go to the **Engine > Input**</span></span>
2. <span data-ttu-id="882f2-175">**[Action Mappings]\(アクション マッピング\)** の横にある **[+]** アイコンを選択して、**RightPinch** アクションと **LeftPinch** アクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="882f2-175">Select the **+** icon next to **Action Mappings** and create **RightPinch** and **LeftPinch** actions:</span></span>

![右と左のピンチ アクション マッピングが強調表示されているバインド入力設定](images/unreal-quickstart-img-15.jpg)

3. <span data-ttu-id="882f2-177">**RightPinch** および **LeftPinch** アクションをそれぞれの **OpenXR Msft ハンド インタラクション** アクションにマップします。</span><span class="sxs-lookup"><span data-stu-id="882f2-177">Map the **RightPinch** and **LeftPinch** actions the to the respective **OpenXR Msft Hand Interaction** actions:</span></span>

![OpenXR Msft ハンド インタラクション オプションが強調表示されたアクション マッピング](images/unreal-quickstart-img-16.jpg)

4. <span data-ttu-id="882f2-179">**[Level Blueprint]\(Level ブループリント\)** を開き、**InputAction RightPinch** と **InputAction LeftPinch** を追加します</span><span class="sxs-lookup"><span data-stu-id="882f2-179">Open the **Level Blueprint** and add an **InputAction RightPinch** and **InputAction LeftPinch**</span></span>
* <span data-ttu-id="882f2-180">ターゲットを **Cube** に設定し、 **[Delta Rotation]\(デルタ回転\)** を **X = 0、Y = 0**、**Z = 20** に設定して、右ピンチ イベントを **AddActorLocalRotation** に接続します。</span><span class="sxs-lookup"><span data-stu-id="882f2-180">Connect the right pinch event to an **AddActorLocalRotation** with your **Cube** as the target and **Delta Rotation** set to **X = 0, Y = 0**, and **Z = 20**.</span></span> <span data-ttu-id="882f2-181">これで、ピンチするたびにキューブが 20 度回転するようになります</span><span class="sxs-lookup"><span data-stu-id="882f2-181">The cube will now rotate by 20 degrees every time you pinch</span></span>
* <span data-ttu-id="882f2-182">左ピンチ イベントを **Quit Game** に接続します</span><span class="sxs-lookup"><span data-stu-id="882f2-182">Connect the left pinch event to **Quit Game**</span></span>

![右と左のピンチ イベントに対する入力アクションが設定された Level ブループリント](images/unreal-quickstart-img-17.jpg)

5. <span data-ttu-id="882f2-184">キューブの **[Transform]\(変換\)** の設定で、 **[Mobility]\(モビリティ\)** を **[Movable]\(移動可能\)** に設定して、動的に移動できるようにします。</span><span class="sxs-lookup"><span data-stu-id="882f2-184">In the cube's **Transform** settings, set **Mobility** to **Movable** so it can move dynamically:</span></span>

![モビリティ プロパティが強調表示されている変換設定](images/unreal-quickstart-img-18.jpg)

<span data-ttu-id="882f2-186">これで、アプリケーションを展開してテストする準備ができました。</span><span class="sxs-lookup"><span data-stu-id="882f2-186">At this point, you're ready to deply and test the application!</span></span>