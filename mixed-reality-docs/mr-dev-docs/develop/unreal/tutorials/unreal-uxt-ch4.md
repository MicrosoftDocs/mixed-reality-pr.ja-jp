---
title: 4. シーンを対話型にする
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 4
author: hferrone
ms.author: v-hferrone
ms.date: 08/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, はじめに, mrtk, uxt, UX ツール, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: dc17b878255a3d6a8e0efc3a4c5bd7aa7d57373d
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679851"
---
# <a name="4-making-your-scene-interactive"></a><span data-ttu-id="6176f-104">4.シーンを対話型にする</span><span class="sxs-lookup"><span data-stu-id="6176f-104">4. Making your scene interactive</span></span>

## <a name="overview"></a><span data-ttu-id="6176f-105">概要</span><span class="sxs-lookup"><span data-stu-id="6176f-105">Overview</span></span>

<span data-ttu-id="6176f-106">前のチュートリアルでは、ARSession、ポーン、およびゲーム モードを追加して、チェス アプリの Mixed Reality セットアップを完了しました。</span><span class="sxs-lookup"><span data-stu-id="6176f-106">In the previous tutorial you added an ARSession, Pawn, and Game Mode to complete the mixed reality setup for the chess app.</span></span> <span data-ttu-id="6176f-107">このセクションでは、オープン ソースの [Mixed Reality Toolkit UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) プラグインの使用方法について説明します。このプラグインには、シーンを対話型にするためのツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="6176f-107">This section focuses on using the open source [Mixed Reality Toolkit UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) plugin, which provides tools to make the scene interactive.</span></span> <span data-ttu-id="6176f-108">このセクションが完了するまでに、ユーザー入力でチェスの駒を移動できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6176f-108">By the end of this section you'll be able to move the chess pieces with user input.</span></span> 

## <a name="objectives"></a><span data-ttu-id="6176f-109">目標</span><span class="sxs-lookup"><span data-stu-id="6176f-109">Objectives</span></span>

* <span data-ttu-id="6176f-110">Mixed Reality Toolkit UX Tools プラグインをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="6176f-110">Downloading the Mixed Reality Toolkit UX Tools plugin</span></span> 
* <span data-ttu-id="6176f-111">ハンド インタラクション アクターを指先に追加する</span><span class="sxs-lookup"><span data-stu-id="6176f-111">Adding Hand Interaction Actors to your fingertips</span></span>
* <span data-ttu-id="6176f-112">シーン内のオブジェクトにマニピュレーターを作成して追加する</span><span class="sxs-lookup"><span data-stu-id="6176f-112">Creating and adding Manipulators to objects in the scene</span></span>
* <span data-ttu-id="6176f-113">入力シミュレーションを使用してプロジェクトを検証する</span><span class="sxs-lookup"><span data-stu-id="6176f-113">Using input simulation to validate the project</span></span>

## <a name="downloading-the-mrtk-ux-tools-plugin"></a><span data-ttu-id="6176f-114">MRTK UX Tools プラグインのダウンロード</span><span class="sxs-lookup"><span data-stu-id="6176f-114">Downloading the MRTK UX Tools plugin</span></span>
<span data-ttu-id="6176f-115">ユーザー入力の操作を開始する前に、プラグインをプロジェクトに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6176f-115">Before you start working with user input, you'll need to add the plugin to the project.</span></span>

1.  <span data-ttu-id="6176f-116">GitHub 上にある Mixed Reality UX Tools の [リリース ページ](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases)で、UX Tools for Unreal v0.9.0 のリリースに移動し、**UXTools.0.9.0.zip** をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="6176f-116">On the Mixed Reality UX Tools [releases page](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases) on GitHub, navigate to the UX Tools for Unreal v0.9.0 release and download **UXTools.0.9.0.zip**.</span></span> <span data-ttu-id="6176f-117">ファイルを解凍します。</span><span class="sxs-lookup"><span data-stu-id="6176f-117">Unzip the file.</span></span>

2.  <span data-ttu-id="6176f-118">プロジェクトのルート フォルダーに、**Plugins** という名前の新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6176f-118">Create a new folder called **Plugins** in the root folder of the project.</span></span> <span data-ttu-id="6176f-119">解凍された UXTools プラグインをこのフォルダーにコピーし、Unreal エディターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="6176f-119">Copy the unzipped UXTools plugin into this folder and restart the Unreal editor.</span></span> 

![プロジェクト プラグイン フォルダーを作成する](images/unreal-uxt/4-plugins.PNG)

3.  <span data-ttu-id="6176f-121">UX Tools プラグインには、**ボタン**、**入力シミュレーション**、および **ポインター** を含むコンポーネント用のサブフォルダーのある Content フォルダーと、その他のコード用の C++ Classes フォルダーがあります。</span><span class="sxs-lookup"><span data-stu-id="6176f-121">The UXTools plugin has a Content folder with subfolders for components including **Buttons**, **Input Simulation**, and **Pointers**, as well as a C++ Classes folder with additional code.</span></span>  

> [!NOTE]
> <span data-ttu-id="6176f-122">**コンテンツ ブラウザー** に **[UXTools コンテンツ]** セクションが表示されない場合は、 **[表示オプション] > [プラグイン コンテンツを表示する]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6176f-122">If you don’t see the **UXTools Content** section in the **Content Browser**, click **View Options > Show Plugin Content**.</span></span> 

![プラグイン コンテンツを表示する](images/unreal-uxt/4-showplugincontent.PNG)

<span data-ttu-id="6176f-124">プラグインがインストールされたら、プラグインから提供されるツールを使用する準備が整います。まずはハンド インタラクション アクターから使い始めます。</span><span class="sxs-lookup"><span data-stu-id="6176f-124">With the plugin installed, you're ready to start using the tools it has to offer, starting with hand interaction actors.</span></span>

## <a name="spawning-hand-interaction-actors"></a><span data-ttu-id="6176f-125">ハンド インタラクション アクターを生成する</span><span class="sxs-lookup"><span data-stu-id="6176f-125">Spawning Hand Interaction Actors</span></span>
<span data-ttu-id="6176f-126">UX 要素とのハンド インタラクションは、ハンド インタラクション アクターを使用して実行されます。これにより、近接および遠隔のインタラクションのポインターとビジュアルが作成および起動されます。</span><span class="sxs-lookup"><span data-stu-id="6176f-126">Hand interaction with UX elements is performed with Hand Interaction Actors, which create and drive the pointers and visuals for near and far interactions.</span></span>
- <span data-ttu-id="6176f-127">*近接インタラクション* は、人差し指と親指で要素をつまむか、指先でそれらをつつくことによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="6176f-127">*Near interactions* are performed by pinching elements between index finger and thumb or by poking them with a fingertip.</span></span> 
- <span data-ttu-id="6176f-128">*遠隔インタラクション* は、仮想ハンドの光線を要素にあてて、人差し指と親指を一緒に押すことで実行されます。</span><span class="sxs-lookup"><span data-stu-id="6176f-128">*Far interactions* are performed by pointing a ray from the virtual hand at an element and pressing index and thumb together.</span></span>

<span data-ttu-id="6176f-129">この例では、**MRPawn** にハンド インタラクション アクターを追加すると、次の処理が行われます。</span><span class="sxs-lookup"><span data-stu-id="6176f-129">In our case, adding a Hand Interaction Actor to **MRPawn** will:</span></span>
- <span data-ttu-id="6176f-130">ポーンの人差し指の先端にカーソルを追加します。</span><span class="sxs-lookup"><span data-stu-id="6176f-130">Add a cursor to the tips of the Pawn’s index fingers.</span></span>
- <span data-ttu-id="6176f-131">ポーンを介して操作できる多関節ハンド入力イベントを提供します。</span><span class="sxs-lookup"><span data-stu-id="6176f-131">Provide articulated hand input events that can be manipulated through the Pawn.</span></span>
- <span data-ttu-id="6176f-132">仮想ハンドの手のひらから伸びる手の光線を通して、遠くの相互作用入力イベントを許可します。</span><span class="sxs-lookup"><span data-stu-id="6176f-132">Allow far interaction input events through hand rays extending from the palms of the virtual hands.</span></span>

<span data-ttu-id="6176f-133">これらの概念を理解するために、操作を続行する前に、ハンド インタラクションに関する[ドキュメント](https://github.com/microsoft/MixedReality-UXTools-Unreal/blob/public/0.9.x/Docs/HandInteraction.md)を参照することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6176f-133">In order to drive these concepts home, you're encouraged to read through the [documentation](https://github.com/microsoft/MixedReality-UXTools-Unreal/blob/public/0.9.x/Docs/HandInteraction.md) on hand interactions before continuing.</span></span> 

<span data-ttu-id="6176f-134">準備ができたら、**MRPawn** ブループリントを開き、 **[Event Graph]\(イベント グラフ\)** に移動します。</span><span class="sxs-lookup"><span data-stu-id="6176f-134">Once you're ready, open the **MRPawn** Blueprint and go to the **Event Graph**.</span></span> 

1. <span data-ttu-id="6176f-135">**Event BeginPlay** から実行ピンをドラッグ アンド リリースして、新しいノードを配置します。</span><span class="sxs-lookup"><span data-stu-id="6176f-135">Drag and release the execution pin from **Event BeginPlay** to place a new node.</span></span> 
    * <span data-ttu-id="6176f-136">**[Spawn Actor from Class]** を選択し、 **[クラス]** ピンの横にあるドロップダウンをクリックし、**Uxt ハンド インタラクション アクター** を検索します。</span><span class="sxs-lookup"><span data-stu-id="6176f-136">Select **Spawn Actor from Class**, click the dropdown next to the **Class** pin and search for **Uxt Hand Interaction Actor**.</span></span>  

2. <span data-ttu-id="6176f-137">2 番目の **Uxt ハンド インタラクション アクター** を生成します。今回は、**手** を **右** に設定します。</span><span class="sxs-lookup"><span data-stu-id="6176f-137">Spawn a second **Uxt Hand Interaction Actor**, this time setting the **Hand** to **Right**.</span></span> <span data-ttu-id="6176f-138">イベントが開始されると、Uxt ハンド インタラクション アクターがそれぞれの手で生成されます。</span><span class="sxs-lookup"><span data-stu-id="6176f-138">When the event begins, a Uxt Hand Interaction Actor will be spawned on each hand.</span></span> 

<span data-ttu-id="6176f-139">**イベント グラフ** は、次のスクリーンショットと一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="6176f-139">Your **Event Graph** should match the following screenshot:</span></span>

![Uxt ハンド インタラクション アクターを生成する](images/unreal-uxt/4-spawnactor.PNG)

<span data-ttu-id="6176f-141">Uxt ハンド インタラクション アクターには、オーナーと最初の変換場所が必要です。</span><span class="sxs-lookup"><span data-stu-id="6176f-141">Both Uxt Hand Interaction Actors need owners and initial transform locations.</span></span> <span data-ttu-id="6176f-142">ハンド インタラクション アクターが表示されるとすぐに仮想ハンドにジャンプするため、最初の変換は重要ではありません (この動作は UX Tools プラグインに含まれています)。</span><span class="sxs-lookup"><span data-stu-id="6176f-142">The initial transform  doesn’t matter since the Hand Interaction Actors will jump to the virtual hands as soon as they're visible (this behavior is included in the UX Tools plugin).</span></span> <span data-ttu-id="6176f-143">ただし、`SpawnActor` 機能では、コンパイラ エラーを回避するために変換入力が必要であるため、既定値を使用します。</span><span class="sxs-lookup"><span data-stu-id="6176f-143">However, the `SpawnActor` function requires a Transform input to avoid a compiler error, so you'll use the default values.</span></span> 

1. <span data-ttu-id="6176f-144">**Spawn Transform** ピンの 1 つからピンをドラッグ アンド リリースして、新しいノードを配置します。</span><span class="sxs-lookup"><span data-stu-id="6176f-144">Drag and release the pin off one of the **Spawn Transform** pins to place a new node.</span></span> 
    * <span data-ttu-id="6176f-145">**Make Transform** ノードを検索し、**戻り値** をもう一方の **Spawn Transform** にドラッグして、両方の **SpawnActor** ノードが接続されるようにします。</span><span class="sxs-lookup"><span data-stu-id="6176f-145">Search for the **Make Transform** node, then drag the **Return Value** to the other hand’s **Spawn Transform** so that both **SpawnActor** nodes are connected.</span></span> 

2.  <span data-ttu-id="6176f-146">両方の **SpawnActor** ノードの下部にある **下矢印** をクリックして、 **[所有者]** ピンを表示します。</span><span class="sxs-lookup"><span data-stu-id="6176f-146">Click the **down arrow** at the bottom of both **SpawnActor** nodes to reveal the **Owner** pin.</span></span>    
    * <span data-ttu-id="6176f-147">**[所有者]** ピンの 1 つからピンをドラッグ アンド リリースして、新しいノードを配置します。</span><span class="sxs-lookup"><span data-stu-id="6176f-147">Drag the pin off one of the **Owner** pins and release to place a new node.</span></span> 
    * <span data-ttu-id="6176f-148">**self** を検索して **Get a reference to self** 変数を選択し、**Self**  オブジェクト参照ノードと他のハンド インタラクション アクターの **[所有者]** ピンの間にリンクを作成します。</span><span class="sxs-lookup"><span data-stu-id="6176f-148">Search for **self** and select the **Get a reference to self** variable, then create a link between the **Self** object reference node and the other Hand Interaction Actor’s **Owner** pin.</span></span> 
3. <span data-ttu-id="6176f-149">最後に重要な点として、両方のハンド インタラクション アクターの **[Show Near Cursor on Grab Targets]\(つかむ対象の近くにあるカーソルを表示する\)** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6176f-149">Last but not least, check the **Show Near Cursor on Grab Targets** box for both Hand Interaction Actors.</span></span> <span data-ttu-id="6176f-150">これで、人差し指が近づいたときに、つかむ対象に重ねてカーソルが表示されるようになり、ターゲットに対する指の位置を相対的に確認しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="6176f-150">This will cause a cursor to appear on the grab target as your index finger approaches it, which will make it easier to see where your finger is relative to the target.</span></span>
    * <span data-ttu-id="6176f-151">**コンパイル** と **保存** を行って、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="6176f-151">**Compile**, **save**, and return to the Main window.</span></span> 

<span data-ttu-id="6176f-152">接続が次のスクリーンショットと一致していることを確認しますが、ブループリントを読みやすくするためにノードをドラッグしてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="6176f-152">Make sure the connections match the following screenshot, but feel free to drag around nodes to make your Blueprint more readable</span></span>

![Uxt ハンド インタラクション アクターのセットアップを完了する](images/unreal-uxt/4-fingerptrs.PNG) 

<span data-ttu-id="6176f-154">MRTK UX Tools プラグインに用意されているハンド インタラクション アクターの詳細については、[ドキュメント](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6176f-154">You can find more information about the Hand Interaction Actor provided in the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/HandInteraction.html).</span></span>

<span data-ttu-id="6176f-155">これで、プロジェクトの仮想ハンドはオブジェクトを選択できるようになりましたが、オブジェクトを操作することはできません。</span><span class="sxs-lookup"><span data-stu-id="6176f-155">Now the virtual hands in the project have a way of selecting objects, but they still can't manipulate them.</span></span> <span data-ttu-id="6176f-156">アプリをテストする前の最後のタスクは、シーン内のアクターにマニピュレーター コンポーネントを追加することです。</span><span class="sxs-lookup"><span data-stu-id="6176f-156">Your last task before testing the app is to add Manipulator components to the actors in the scene.</span></span>

## <a name="attaching-manipulators"></a><span data-ttu-id="6176f-157">マニピュレーターの添付</span><span class="sxs-lookup"><span data-stu-id="6176f-157">Attaching Manipulators</span></span>

<span data-ttu-id="6176f-158">マニピュレーターは、多関節ハンドによる入力に応答するコンポーネントであり、つかんだり、回転させたり、および変換したりできます。</span><span class="sxs-lookup"><span data-stu-id="6176f-158">A Manipulator is a component that responds to articulated hand input and can be grabbed, rotated, and translated.</span></span> <span data-ttu-id="6176f-159">マニピュレーターの変換をアクターの変換に適用すると、アクターの直接操作が可能になります。</span><span class="sxs-lookup"><span data-stu-id="6176f-159">Applying the Manipulator’s transform to an Actors transform allows direct Actor manipulation.</span></span> 

1. <span data-ttu-id="6176f-160">**[ボード]** ブループリントを開き、 **[コンポーネントの追加]** をクリックして、 **[コンポーネント]** パネルで **Uxt 汎用マニピュレーター** を検索します。</span><span class="sxs-lookup"><span data-stu-id="6176f-160">Open the **Board** blueprint, click **Add Component** and search for **Uxt Generic Manipulator** in the **Components** panel.</span></span>

![汎用マニピュレーターを追加する](images/unreal-uxt/4-addmanip.PNG)

2. <span data-ttu-id="6176f-162">**[詳細]** パネルの **[汎用マニピュレーター]** セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="6176f-162">Expand the **Generic Manipulator** section in the **Details** panel.</span></span> <span data-ttu-id="6176f-163">ここから片手または両手操作、回転モード、スムージングを設定できます。</span><span class="sxs-lookup"><span data-stu-id="6176f-163">You can set one-handed or two-handed manipulation, rotation mode, and smoothing from here.</span></span> <span data-ttu-id="6176f-164">好きなモードを自由に選択して、ボードを **コンパイル** し、**保存** します。</span><span class="sxs-lookup"><span data-stu-id="6176f-164">Feel free to select whichever modes you wish, then **Compile** and **Save** Board.</span></span> 

![モードを設定する](images/unreal-uxt/4-setrotmode.PNG)

3. <span data-ttu-id="6176f-166">**WhiteKing** アクターについて上記の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="6176f-166">Repeat the steps above for the **WhiteKing** Actor.</span></span>

<span data-ttu-id="6176f-167">MRTK UX Tools プラグインに用意されているマニピュレーター コンポーネントの詳細については、[ドキュメント](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6176f-167">You can find more information about the Manipulator Components provided in the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/Manipulator.html).</span></span>

## <a name="testing-the-scene"></a><span data-ttu-id="6176f-168">シーンのテスト</span><span class="sxs-lookup"><span data-stu-id="6176f-168">Testing the scene</span></span>
<span data-ttu-id="6176f-169">良い知らせです。</span><span class="sxs-lookup"><span data-stu-id="6176f-169">Good news everyone!</span></span> <span data-ttu-id="6176f-170">これで、新しい仮想ハンドとユーザー入力でアプリをテストする準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="6176f-170">You're ready to test out the app with its new virtual hands and user input.</span></span> <span data-ttu-id="6176f-171">メイン ウィンドウで **[再生]** を押すと、MRTK UX Tools プラグインから 2 つのメッシュ ハンドが提供され、それぞれの手の平からハンド レイが伸びているのを確認できます。</span><span class="sxs-lookup"><span data-stu-id="6176f-171">Press **Play** in the Main Window and you'll see two mesh hands provided by the MRTK UX Tools plugin with hand rays extending from each hand’s palm.</span></span> <span data-ttu-id="6176f-172">次のように、手とその相互作用を制御できます。</span><span class="sxs-lookup"><span data-stu-id="6176f-172">You can control the hands and their interactions as follows:</span></span>
- <span data-ttu-id="6176f-173">**左 Alt** キーを押しながら **左手** を制御し、**左 Shift** キーを押して **右手** を制御します。</span><span class="sxs-lookup"><span data-stu-id="6176f-173">Hold down the **left Alt** key to control the **left hand** and the **left Shift** key to control the **right hand**.</span></span> 
- <span data-ttu-id="6176f-174">マウスを動かして手を動かし、**マウス ホイール** を使用してスクロールして、手を **前方** または **後方** に移動します。</span><span class="sxs-lookup"><span data-stu-id="6176f-174">Move your mouse to move the hand and scroll with your **mouse wheel** to move the hand **forwards** or **backwards**.</span></span> 
- <span data-ttu-id="6176f-175">左マウスをクリックして **ピンチ**、マウスの中央ボタンをクリックして **指さし** を行います。</span><span class="sxs-lookup"><span data-stu-id="6176f-175">Click the left mouse button to **pinch**, click the middle mouse button to **poke**.</span></span> 

> [!NOTE]
> <span data-ttu-id="6176f-176">PC に複数のヘッドセットが接続されている場合、入力シミュレーションが機能しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6176f-176">Input simulation may not work if you have multiple headsets plugged into your PC.</span></span> <span data-ttu-id="6176f-177">問題が発生している場合は、他のヘッドセットを取り外してみてください。</span><span class="sxs-lookup"><span data-stu-id="6176f-177">If you're having issues, try unplugging your other headsets.</span></span> 

![ビューポート内のシミュレートされた手](images/unreal-uxt/4-handsim.PNG)

<span data-ttu-id="6176f-179">シミュレートされた手を使用して、チェスの白キングを手に取り、移動して、置いて、ボードを操作してみましょう。</span><span class="sxs-lookup"><span data-stu-id="6176f-179">Try using the simulated hands to pick up, move, and set down the white chess king and manipulate the board!</span></span> <span data-ttu-id="6176f-180">近接インタラクションと遠隔インタラクションの両方を試してみてください。手がボードとキングを直接つかめる位置まで近づくと、ハンド レイが消え、人差し指の先が指カーソルに置き換わります。</span><span class="sxs-lookup"><span data-stu-id="6176f-180">Experiment with both near and far interaction - notice that when your hands get close enough to grab the board and king directly, the hand ray disappears and is replaced with a finger cursor at the tip of the index finger.</span></span> 

<span data-ttu-id="6176f-181">MRTK UX Tools プラグインに用意されているシミュレートされた手の機能の詳細については、[ドキュメント](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/InputSimulation.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6176f-181">You can find more information about the simulated hands feature provided by the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/InputSimulation.html).</span></span>

<span data-ttu-id="6176f-182">これで、仮想ユーザーがオブジェクトと対話できるようになったので、次のチュートリアルに進み、ユーザー インターフェイスとイベントを追加する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="6176f-182">Now that your virtual hands can interact with objects, you're ready to move on to the next tutorial and add user interfaces and events.</span></span>

[<span data-ttu-id="6176f-183">次のセクション: 5.ボタンの追加およびピースの位置のリセット</span><span class="sxs-lookup"><span data-stu-id="6176f-183">Next Section: 5. Adding a button & resetting piece locations</span></span>](unreal-uxt-ch5.md)
