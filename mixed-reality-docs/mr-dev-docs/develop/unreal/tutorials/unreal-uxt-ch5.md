---
title: 5. ボタンの追加およびピースの位置のリセット
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 5
author: hferrone
ms.author: v-hferrone
ms.date: 08/14/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: f7b57cf8a023874aa14118ff5cd50076bbf344e0
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91702349"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="4ad69-104">5.ボタンの追加およびピースの位置のリセット</span><span class="sxs-lookup"><span data-stu-id="4ad69-104">5. Adding a button & resetting piece locations</span></span>


## <a name="overview"></a><span data-ttu-id="4ad69-105">概要</span><span class="sxs-lookup"><span data-stu-id="4ad69-105">Overview</span></span>

<span data-ttu-id="4ad69-106">前のチュートリアルでは、ポーン コンポーネントにハンド インタラクション アクターを追加し、チェス盤にマニピュレーター コンポーネントを追加して、両方を対話型にしました。</span><span class="sxs-lookup"><span data-stu-id="4ad69-106">In the previous tutorial, you added Hand Interaction Actors to the Pawn and Manipulator components to the chess board to make them both interactive.</span></span> <span data-ttu-id="4ad69-107">このセクションでは、チェス アプリの機能を構築することによって、Mixed Reality ツールキット UX ツール プラグインを引き続き操作します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-107">In this section, you'll continue working with the Mixed Reality Toolkit UX Tools plugin by building out the features of your chess app.</span></span> <span data-ttu-id="4ad69-108">これには、新しい関数の作成と、ブループリントでアクターへの参照を取得する方法についての説明が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4ad69-108">This includes creating a new function and learning how to get references to Actors in a Blueprint.</span></span> <span data-ttu-id="4ad69-109">このセクションの完了までに、デバイスまたはエミュレーターに Mixed Reality アプリをパッケージ化してデプロイする準備が整います。</span><span class="sxs-lookup"><span data-stu-id="4ad69-109">By the end of this section, you'll be ready to package and deploy the mixed reality app on a device or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="4ad69-110">目標</span><span class="sxs-lookup"><span data-stu-id="4ad69-110">Objectives</span></span>

* <span data-ttu-id="4ad69-111">対話型ボタンの追加</span><span class="sxs-lookup"><span data-stu-id="4ad69-111">Adding an interactive button</span></span>
* <span data-ttu-id="4ad69-112">ピースの位置をリセットする関数を作成する</span><span class="sxs-lookup"><span data-stu-id="4ad69-112">Creating a function to reset a pieces' location</span></span>
* <span data-ttu-id="4ad69-113">押されたときに関数をトリガーするボタンをフックする</span><span class="sxs-lookup"><span data-stu-id="4ad69-113">Hooking the button up to trigger the function when pressed</span></span>

## <a name="creating-a-reset-function"></a><span data-ttu-id="4ad69-114">Reset 関数の作成</span><span class="sxs-lookup"><span data-stu-id="4ad69-114">Creating a reset function</span></span>
<span data-ttu-id="4ad69-115">最初のタスクは、チェスのピースをシーンの元の位置にリセットする関数のブループリントを作成することです。</span><span class="sxs-lookup"><span data-stu-id="4ad69-115">Your first task is to create a function blueprint that resets a chess piece to its original position in the scene.</span></span> 

1.  <span data-ttu-id="4ad69-116">**WhiteKing** を開き、 **[My Blueprint]** の **[関数]** セクションの横にある **+** アイコンをクリックして、 **[Reset Location]** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="4ad69-116">Open **WhiteKing** , click the **+** icon next to the **Functions** section in the **My Blueprint** and name it **Reset Location** .</span></span> 

2.  <span data-ttu-id="4ad69-117">**SetActorRelativeTransform** ノードを作成するには、ブループリント グリッドの **Reset Location** から実行をドラッグしてリリースします。</span><span class="sxs-lookup"><span data-stu-id="4ad69-117">Drag and release the execution from **Reset Location** on the Blueprint grid to create a **SetActorRelativeTransform** node.</span></span> 
    * <span data-ttu-id="4ad69-118">この関数では、アクターの親に対して相対的に変換 (位置、回転、スケール) を設定します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-118">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="4ad69-119">この関数を使用すると、ボードが元の位置から移動した場合でもボード上のキングの位置がリセットされます。</span><span class="sxs-lookup"><span data-stu-id="4ad69-119">You’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span> 
    
3. <span data-ttu-id="4ad69-120">イベント グラフ内で右クリックし、 **[変換の作成]** を選択し、 **[場所]** を **X =-26** 、 **Y = 4** 、 **Z = 0** に変更します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-120">Right-click inside the Event Graph, select **Make Transform** , and change its **Location** to **X = -26** , **Y = 4** , **Z = 0** .</span></span>
    * <span data-ttu-id="4ad69-121">**SetActorRelativeTransform** の **[新しい相対変換]** ピンに **[戻り値]** を接続します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-121">Connect its **Return Value** to the **New Relative Transform** pin in **SetActorRelativeTransform** .</span></span> 

![Reset Location (位置のリセット) 関数](images/unreal-uxt/5-function.PNG)

<span data-ttu-id="4ad69-123">メイン ウィンドウに戻る前に、プロジェクトを **コンパイル** して **保存** します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-123">**Compile** and **Save** the project before returning to the Main window.</span></span> 


## <a name="adding-a-button"></a><span data-ttu-id="4ad69-124">ボタンを追加する</span><span class="sxs-lookup"><span data-stu-id="4ad69-124">Adding a button</span></span>
<span data-ttu-id="4ad69-125">関数が正しくセットアップされたので、次のタスクでは、タッチしたときにオフにするボタンを作成します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-125">Now that the function is setup correctly, your next task is to create a button that fires it off when touched.</span></span> 


1.  <span data-ttu-id="4ad69-126">**[新しく追加] > [ブループリント クラス]** をクリックし、 **[すべてのクラス]** セクションを展開して、「 **BP_ButtonHoloLens2** 」を検索します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-126">Click **Add New > Blueprint Class** , expand the **All Classes** section, and search for **BP_ButtonHoloLens2** .</span></span> 
    * <span data-ttu-id="4ad69-127">これに **ResetButton** という名前を付け、ダブルクリックしてブループリントを開きます。</span><span class="sxs-lookup"><span data-stu-id="4ad69-127">Name it **ResetButton** and double click to open the Blueprint</span></span>

> [!NOTE]
> <span data-ttu-id="4ad69-128">**BP_ButtonHoloLens2** は、UX Tools プラグインの一部である 3D ボタンのブループリント アクターです。</span><span class="sxs-lookup"><span data-stu-id="4ad69-128">**BP_ButtonHoloLens2** is a 3D button Blueprint Actor that's part of the UX Tools plugin.</span></span>

![HoloLens 2 スタイル ボタンから新しいブループリントをサブクラス化する](images/unreal-uxt/5-subclass.PNG)

2. <span data-ttu-id="4ad69-130">**[コンポーネント]** パネルで **[ResetButton(self)]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-130">Ensure **ResetButton(self)** is selected in the **Components** panel.</span></span> <span data-ttu-id="4ad69-131">**[詳細]** パネルで、 **[ボタン]** セクションに移動します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-131">In the **Details** panel, navigate to the **Button** section.</span></span> <span data-ttu-id="4ad69-132">**[ボタン ラベル]** の既定を [リセット] に変更します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-132">Change the default **Button Label** to "Reset".</span></span> <span data-ttu-id="4ad69-133">**[Button Icon Brush]\(ボタン アイコンのブラシ\)** セクションを展開し、 **[Open Icon Brush Editor]\(Icon Brush Editor を開く\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="4ad69-133">Expand the **Button Icon Brush** section and press the **Open Icon Brush Editor** button.</span></span> 

![ボタンのラベルとアイコンを設定する](images/unreal-uxt/5-buttonconfig.PNG)

<span data-ttu-id="4ad69-135">これにより、ボタンの新しいアイコンを選択するために UX Tools プラグインによって提供されたユーティリティ、Icon Brush Editor が開きます。</span><span class="sxs-lookup"><span data-stu-id="4ad69-135">This will open up the Icon Brush Editor, which is a utility provided by the UX Tools plugin which you can use to select a new icon for your button.</span></span> 

![ボタンのアイコンを選択する](images/unreal-uxt/5-iconbrusheditor.PNG)

<span data-ttu-id="4ad69-137">ボタンの構成のために調整できる設定は、他にも多くあります。</span><span class="sxs-lookup"><span data-stu-id="4ad69-137">There are plenty of other settings you can adjust to configure your button.</span></span> <span data-ttu-id="4ad69-138">UXT Pressable Button コンポーネントの詳細については、[ドキュメント](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4ad69-138">To learn more about the UXT Pressable Button component, check out the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html).</span></span>

3. <span data-ttu-id="4ad69-139">**[コンポーネント]** パネルの **[UxtPressableButton (継承)]** をクリックし、 **[詳細]** パネルを下にスクロールして **[イベント]** セクションを表示します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-139">Click **UxtPressableButton (Inherited)** in the **Components** panel and scroll down the **Details** panel to the **Events** section.</span></span> 
    * <span data-ttu-id="4ad69-140">**[On Button Pressed]\(ボタンが押されたとき\)** の横にある緑色の **+** のボタンをクリックして、ボタンが押されたときに呼び出されるイベントをイベント グラフに追加します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-140">Click the green **+** button next to **On Button Pressed** to add an event to the Event Graph, which will be called when the button is pressed.</span></span> 
    
<span data-ttu-id="4ad69-141">ここから、レベルの **WhiteKing** アクターへの参照が必要な  **WhiteKing** の **Reset Location** 関数を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ad69-141">From here, you’ll want to call **WhiteKing** ’s **Reset Location** function, which needs a reference to the **WhiteKing** Actor in the Level.</span></span> 

4.  <span data-ttu-id="4ad69-142">**[My Blueprint]\(マイ ブループリント\)** パネルの **[変数]** セクションに移動し、 **[+]** ボタンをクリックして、変数に **WhiteKing** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="4ad69-142">In the **My Blueprint** panel, navigate to the **Variables** section , click the **+** button and name the variable **WhiteKing** .</span></span> 
    * <span data-ttu-id="4ad69-143">**[Details]\(詳細\)** パネルで、 **[Variable Type]\(変数の種類\)** の横にあるドロップダウンを選択し、 **WhiteKing** を検索して、 **[Object Reference]\(オブジェクト参照\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-143">In the **Details** panel, select the dropdown next to **Variable Type** , search for **WhiteKing** , and select the **Object Reference** .</span></span> 
    * <span data-ttu-id="4ad69-144">**[Instance Editable]\(インスタンス編集可能\)** の横のボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4ad69-144">Check the box next to **Instance Editable** .</span></span> <span data-ttu-id="4ad69-145">これにより、変数をメイン レベルから設定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4ad69-145">This will allow the variable to be set from the Main Level.</span></span> 

![変数を作成する](images/unreal-uxt/5-var.PNG)

5.  <span data-ttu-id="4ad69-147">WhiteKing 変数を **[My Blueprint]\(マイ ブループリント\) > [Variables]\(変数\)** から Reset Button イベント グラフにドラッグし、 **[WhiteKing の取得]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-147">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph and choose **Get WhiteKing** .</span></span> 

## <a name="firing-the-function"></a><span data-ttu-id="4ad69-148">関数の起動</span><span class="sxs-lookup"><span data-stu-id="4ad69-148">Firing the function</span></span>
<span data-ttu-id="4ad69-149">あとは、ボタンが押されたときに Reset 関数を正式に起動するだけです。</span><span class="sxs-lookup"><span data-stu-id="4ad69-149">All that's left is to officially fire off the reset function when the button is pressed.</span></span>

1.  <span data-ttu-id="4ad69-150">WhiteKing の出力ピンをドラッグしてリリースし、新しいノードを配置します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-150">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="4ad69-151">**Reset Location** 関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-151">Select the **Reset Location** function.</span></span> <span data-ttu-id="4ad69-152">最後に、 **[On Button Pressed]\(ボタンが押されたとき\)** から出力実行ピンを **[Reset Location]** の入力実行ピンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="4ad69-152">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location** .</span></span> <span data-ttu-id="4ad69-153">ResetButton ブループリントの **[Compile]\(コンパイル\)** と **[Save]\(保存\)** の後、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="4ad69-153">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span> 

![On Button Pressed (ボタンが押されたとき) から Reset Location 関数を呼び出す](images/unreal-uxt/5-callresetloc.PNG)

2.  <span data-ttu-id="4ad69-155">**ResetButton** をビューポートにドラッグし、その位置を **X = 50** 、 **Y = -25** 、 **Z = 10** に設定します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-155">Drag **ResetButton** into the viewport and set its location to **X = 50** , **Y = -25** , and **Z = 10** .</span></span> <span data-ttu-id="4ad69-156">回転を **Z = 180** に設定します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-156">Set its rotation to **Z = 180** .</span></span> <span data-ttu-id="4ad69-157">**[Default]\(既定\)** で、 **WhiteKing** 変数の値を **WhiteKing** に設定します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-157">Under **Default** , set the value of the **WhiteKing** variable to **WhiteKing** .</span></span>

![変数の値を設定する](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="4ad69-159">アプリを実行し、チェスのピースを新しい場所に移動し、先ほどの HoloLens 2 スタイル ボタンを押すと、リセット ロジックが動作するのを確認できます。</span><span class="sxs-lookup"><span data-stu-id="4ad69-159">Run the app, move the chess piece to a new location, and press your HoloLens 2-style button to see the reset logic in action!</span></span>

<span data-ttu-id="4ad69-160">これで、対話可能なチェスの駒とボードを備えた Mixed Reality アプリと、ピースの位置をリセットする、完全に機能するボタンが完成しました。</span><span class="sxs-lookup"><span data-stu-id="4ad69-160">You now have a mixed reality app with a chess piece and board that you can interact with, as well as a fully functioning button that will reset the piece’s location.</span></span> <span data-ttu-id="4ad69-161">ここまでで完成したアプリは [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) リポジトリにあります。</span><span class="sxs-lookup"><span data-stu-id="4ad69-161">You can find the completed app up to this point in its [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) repo.</span></span> <span data-ttu-id="4ad69-162">このチュートリアルをさらに進めて、ボタンを押したときにボード全体がリセットされるように、チェスの残りのピースを設定してみてください。</span><span class="sxs-lookup"><span data-stu-id="4ad69-162">Feel free to go beyond this tutorial and set up the remainder of the chess pieces so that the entire board is reset when the button is pressed.</span></span>

![ビューポートの終わりのシーン](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="4ad69-164">このチュートリアルの最後のセクションに進む準備ができました。そこでは、アプリを正しくパッケージ化してデバイスまたはエミュレーターにデプロイする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4ad69-164">You're ready to move on to the final section of this tutorial where you'll learn how to correctly package and deploy the app to a device or emulator.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4ad69-165">アプリケーションをデバイスまたはエミュレーターにデプロイする前のこの時点で、推奨される **[Unreal パフォーマンス設定](../performance-recommendations-for-unreal.md)** を使用してプロジェクトを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ad69-165">At this point, you should update your project with the recommended **[Unreal performance settings](../performance-recommendations-for-unreal.md)** before deploying your application to a device or emulator.</span></span>

[<span data-ttu-id="4ad69-166">次のセクション: 6.デバイスまたはエミュレーターのパッケージ化およびデプロイ</span><span class="sxs-lookup"><span data-stu-id="4ad69-166">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
