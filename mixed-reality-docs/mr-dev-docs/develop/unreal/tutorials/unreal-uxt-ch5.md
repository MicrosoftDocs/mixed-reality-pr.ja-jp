---
title: 5. ボタンの追加およびピースの位置のリセット
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用してチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 5
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, はじめに, mrtk, uxt, UX ツール, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 8e16865e89c06c37f2932f1828bf8ca5551e6fce
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609693"
---
# <a name="5-adding-a-button--resetting-piece-locations"></a><span data-ttu-id="7ecc3-104">5.ボタンの追加およびピースの位置のリセット</span><span class="sxs-lookup"><span data-stu-id="7ecc3-104">5. Adding a button & resetting piece locations</span></span>

<span data-ttu-id="7ecc3-105">前のチュートリアルでは、ポーン コンポーネントにハンド インタラクション アクターを追加し、チェス盤にマニピュレーター コンポーネントを追加して、両方を対話型にしました。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-105">In the previous tutorial, you added Hand Interaction Actors to the Pawn and Manipulator components to the chess board to make them both interactive.</span></span> <span data-ttu-id="7ecc3-106">このセクションでは、引き続き Mixed Reality ツールキットの UX Tools プラグインを使用して、ブループリントの新しい関数とアクター参照を使用してチェス アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-106">In this section, you'll continue to use the Mixed Reality Toolkit UX Tools plugin to build out your chess app with new functions and Actor references in Blueprints.</span></span> <span data-ttu-id="7ecc3-107">このセクションの完了までに、デバイスまたはエミュレーターに Mixed Reality アプリをパッケージ化してデプロイする準備が整います。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-107">By the end of this section, you'll be ready to package and deploy the mixed reality app on a device or emulator.</span></span>

## <a name="objectives"></a><span data-ttu-id="7ecc3-108">目標</span><span class="sxs-lookup"><span data-stu-id="7ecc3-108">Objectives</span></span>

* <span data-ttu-id="7ecc3-109">対話型ボタンの追加</span><span class="sxs-lookup"><span data-stu-id="7ecc3-109">Adding an interactive button</span></span>
* <span data-ttu-id="7ecc3-110">ピースの位置をリセットする関数を作成する</span><span class="sxs-lookup"><span data-stu-id="7ecc3-110">Creating a function to reset a pieces' location</span></span>
* <span data-ttu-id="7ecc3-111">押されたときに関数をトリガーするボタンをフックする</span><span class="sxs-lookup"><span data-stu-id="7ecc3-111">Hooking the button up to trigger the function when pressed</span></span>

## <a name="creating-a-reset-function"></a><span data-ttu-id="7ecc3-112">Reset 関数の作成</span><span class="sxs-lookup"><span data-stu-id="7ecc3-112">Creating a reset function</span></span>

<span data-ttu-id="7ecc3-113">最初のタスクは、チェスのピースをシーンの元の位置にリセットする関数のブループリントを作成することです。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-113">Your first task is to create a function blueprint that resets a chess piece to its original position in the scene.</span></span>

1.  <span data-ttu-id="7ecc3-114">**WhiteKing** を開き、 **[My Blueprint]\(マイ ブループリント\)** の **[Functions]\(関数\)** セクションの横にある **[+]** アイコンをクリックして、「**Reset Location**」という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-114">Open **WhiteKing**, select the **+** icon next to the **Functions** section in the **My Blueprint** and name it **Reset Location**.</span></span>

2.  <span data-ttu-id="7ecc3-115">**SetActorRelativeTransform** ノードを作成するには、ブループリント グリッドの **Reset Location** から実行をドラッグしてリリースします。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-115">Drag and release the execution from **Reset Location** on the Blueprint grid to create a **SetActorRelativeTransform** node.</span></span>
    * <span data-ttu-id="7ecc3-116">この関数では、アクターの親に対して相対的に変換 (位置、回転、スケール) を設定します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-116">This function sets the transform (location, rotation, and scale) of an actor relative to its parent.</span></span> <span data-ttu-id="7ecc3-117">この関数を使用すると、ボードが元の位置から移動した場合でもボード上のキングの位置がリセットされます。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-117">You’ll use this function to reset the king’s position on the board, even if the board has been moved from its original position.</span></span>

3. <span data-ttu-id="7ecc3-118">イベント グラフ内で右クリックし、 **[変換の作成]** を選択し、 **[場所]** を **X =-26**、**Y = 4**、**Z = 0** に変更します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-118">Right-click inside the Event Graph, select **Make Transform**, and change its **Location** to **X = -26**, **Y = 4**, **Z = 0**.</span></span>
    * <span data-ttu-id="7ecc3-119">**SetActorRelativeTransform** の **[新しい相対変換]** ピンに **[戻り値]** を接続します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-119">Connect its **Return Value** to the **New Relative Transform** pin in **SetActorRelativeTransform**.</span></span>

![Reset Location (位置のリセット) 関数](images/unreal-uxt/5-function.PNG)

<span data-ttu-id="7ecc3-121">メイン ウィンドウに戻る前に、プロジェクトを **コンパイル** して **保存** します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-121">**Compile** and **Save** the project before returning to the Main window.</span></span>


## <a name="adding-a-button"></a><span data-ttu-id="7ecc3-122">ボタンを追加する</span><span class="sxs-lookup"><span data-stu-id="7ecc3-122">Adding a button</span></span>

<span data-ttu-id="7ecc3-123">関数が正しくセットアップされたので、次のタスクでは、タッチしたときにオフにするボタンを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-123">Now that the function is set up correctly, your next task is to create a button that fires it off when touched.</span></span>

1.  <span data-ttu-id="7ecc3-124">**[Add New]\(新規追加\) > [Blueprint Class]\(ブループリント クラス\)** をクリックし、 **[All Classes]\(すべてのクラス\)** セクションを展開して、**UxtPressableButtonActor** を見つけます。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-124">Click **Add New > Blueprint Class**, expand the **All Classes** section, and search for **UxtPressableButtonActor**.</span></span>
    * <span data-ttu-id="7ecc3-125">これに **ResetButton** という名前を付け、ダブルクリックしてブループリントを開きます。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-125">Name it **ResetButton** and double click to open the Blueprint</span></span>

![HoloLens 2 スタイル ボタンから新しいブループリントをサブクラス化する](images/unreal-uxt/5-subclass.PNG)

2. <span data-ttu-id="7ecc3-127">**[コンポーネント]** パネルで **[ResetButton(self)]** が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-127">Ensure **ResetButton(self)** is selected in the **Components** panel.</span></span> <span data-ttu-id="7ecc3-128">**[詳細]** パネルで、 **[ボタン]** セクションに移動します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-128">In the **Details** panel, navigate to the **Button** section.</span></span> <span data-ttu-id="7ecc3-129">既定の **[Button Label]\(ボタン ラベル\)** を「リセット」に変更し、 **[Button Icon Brush]\(ボタン アイコンのブラシ\)** セクションを展開し、 **[Open Icon Brush Editor]\(Icon Brush Editor を開く\)** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-129">Change the default **Button Label** to "Reset", expand the **Button Icon Brush** section, and press the **Open Icon Brush Editor** button.</span></span>

![ボタンのラベルとアイコンを設定する](images/unreal-uxt/5-buttonconfig.PNG)

<span data-ttu-id="7ecc3-131">アイコン ブラシ エディターが開き、ボタンの新しいアイコンを選択できます。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-131">The Icon Brush Editor will open, which you can use to select a new icon for your button.</span></span>

![ボタンのアイコンを選択する](images/unreal-uxt/5-iconbrusheditor.PNG)

<span data-ttu-id="7ecc3-133">ボタンの構成のために調整できる設定は、他にも多くあります。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-133">There are plenty of other settings you can adjust to configure your button.</span></span> <span data-ttu-id="7ecc3-134">UXT Pressable Button コンポーネントの詳細については、[ドキュメント](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-134">To learn more about the UXT Pressable Button component, check out the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/PressableButton.html).</span></span>

3. <span data-ttu-id="7ecc3-135">**[コンポーネント]** パネルで **[ButtonComponent (Inherited)]\(ButtonComponent (継承)\)** をクリックし、 **[詳細]** パネルを下にスクロールして **[イベント]** セクションを表示します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-135">Click **ButtonComponent (Inherited)** in the **Components** panel and scroll down the **Details** panel to the **Events** section.</span></span>
    * <span data-ttu-id="7ecc3-136">**[On Button Pressed]\(ボタンが押されたとき\)** の横にある緑色の **+** のボタンをクリックして、ボタンが押されたときに呼び出されるイベントをイベント グラフに追加します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-136">Click the green **+** button next to **On Button Pressed** to add an event to the Event Graph, which will be called when the button is pressed.</span></span>

<span data-ttu-id="7ecc3-137">ここから、レベルの **WhiteKing** アクターへの参照が必要な  **WhiteKing** の **Reset Location** 関数を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-137">From here, you’ll want to call **WhiteKing**’s **Reset Location** function, which needs a reference to the **WhiteKing** Actor in the Level.</span></span>

4.  <span data-ttu-id="7ecc3-138">**[My Blueprint]\(マイ ブループリント\)** パネルの **[変数]** セクションに移動し、 **[+]** ボタンをクリックして、変数に **WhiteKing** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-138">In the **My Blueprint** panel, navigate to the **Variables** section, click the **+** button, and name the variable **WhiteKing**.</span></span>
    * <span data-ttu-id="7ecc3-139">**[Details]\(詳細\)** パネルで、 **[Variable Type]\(変数の種類\)** の横にあるドロップダウンを選択し、**WhiteKing** を検索して、 **[Object Reference]\(オブジェクト参照\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-139">In the **Details** panel, select the dropdown next to **Variable Type**, search for **WhiteKing**, and select the **Object Reference**.</span></span>
    * <span data-ttu-id="7ecc3-140">**[Instance Editable]\(インスタンスの編集可能\)** の横にあるチェック ボックスをオンにすると、変数をメイン レベルから設定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-140">Check the box next to **Instance Editable**, which allows the variable to be set from the Main Level.</span></span>

![変数を作成する](images/unreal-uxt/5-var.PNG)

5.  <span data-ttu-id="7ecc3-142">WhiteKing 変数を **[My Blueprint]\(マイ ブループリント\) > [Variables]\(変数\)** から Reset Button イベント グラフにドラッグし、 **[WhiteKing の取得]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-142">Drag the WhiteKing variable from **My Blueprint > Variables** onto the Reset Button Event Graph and choose **Get WhiteKing**.</span></span>

## <a name="firing-the-function"></a><span data-ttu-id="7ecc3-143">関数の起動</span><span class="sxs-lookup"><span data-stu-id="7ecc3-143">Firing the function</span></span>

<span data-ttu-id="7ecc3-144">あとは、ボタンが押されたときに Reset 関数を正式に起動するだけです。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-144">All that's left is to officially fire off the reset function when the button is pressed.</span></span>

1.  <span data-ttu-id="7ecc3-145">WhiteKing の出力ピンをドラッグしてリリースし、新しいノードを配置します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-145">Drag the WhiteKing output pin and release to place a new node.</span></span> <span data-ttu-id="7ecc3-146">**Reset Location** 関数を選択します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-146">Select the **Reset Location** function.</span></span> <span data-ttu-id="7ecc3-147">最後に、 **[On Button Pressed]\(ボタンが押されたとき\)** から出力実行ピンを **[Reset Location]** の入力実行ピンにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-147">Finally, drag the outgoing execution pin from **On Button Pressed** to the incoming execution pin on **Reset Location**.</span></span> <span data-ttu-id="7ecc3-148">ResetButton ブループリントの **[Compile]\(コンパイル\)** と **[Save]\(保存\)** の後、メイン ウィンドウに戻ります。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-148">**Compile** and **Save** the ResetButton Blueprint, then return to the Main window.</span></span>

![On Button Pressed (ボタンが押されたとき) から Reset Location 関数を呼び出す](images/unreal-uxt/5-callresetloc.PNG)

2.  <span data-ttu-id="7ecc3-150">**ResetButton** をビューポートにドラッグし、その位置を **X = 50**、 **Y = -25**、**Z = 10** に設定します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-150">Drag **ResetButton** into the viewport and set its location to **X = 50**, **Y = -25**, and **Z = 10**.</span></span> <span data-ttu-id="7ecc3-151">回転を **Z = 180** に設定します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-151">Set its rotation to **Z = 180**.</span></span> <span data-ttu-id="7ecc3-152">**[Default]\(既定\)** で、**WhiteKing** 変数の値を **WhiteKing** に設定します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-152">Under **Default**, set the value of the **WhiteKing** variable to **WhiteKing**.</span></span>

![変数の値を設定する](images/unreal-uxt/5-buttonlevel.PNG)

<span data-ttu-id="7ecc3-154">アプリを実行し、チェスのピースを新しい場所に移動し、先ほどの HoloLens 2 スタイル ボタンを押すと、リセット ロジックが動作するのを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-154">Run the app, move the chess piece to a new location, and press your HoloLens 2-style button to see the reset logic in action!</span></span>

<span data-ttu-id="7ecc3-155">これで、対話可能なチェスの駒とボードを備えた Mixed Reality アプリと、駒の位置をリセットする、完全に機能するボタンが完成しました。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-155">You now have a mixed reality app with an interactable chess piece and board, and a fully functioning button that resets the piece’s location.</span></span> <span data-ttu-id="7ecc3-156">ここまでで完成したアプリは [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) リポジトリにあります。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-156">You can find the completed app up to this point in its [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) repo.</span></span> <span data-ttu-id="7ecc3-157">このチュートリアルをさらに進めて、リセット ボタンを押したらボード全体がリセットされるように、チェスの残りの駒を設定してみてください。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-157">Feel free to go beyond this tutorial and set up the rest of the chess pieces so that the entire board is reset when you press the reset button.</span></span>

![ビューポートの終わりのシーン](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="7ecc3-159">このチュートリアルの最後のセクションに進む準備ができました。そこでは、アプリをパッケージ化してデバイスまたはエミュレーターにデプロイする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-159">You're ready to move on to the final section of this tutorial where you'll learn how to package and deploy the app to a device or emulator.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7ecc3-160">アプリケーションをデバイスまたはエミュレーターにデプロイする前のこの時点で、推奨される **[Unreal パフォーマンス設定](../performance-recommendations-for-unreal.md)** を使用してプロジェクトを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ecc3-160">At this point, you should update your project with the recommended **[Unreal performance settings](../performance-recommendations-for-unreal.md)** before deploying your application to a device or emulator.</span></span>

[<span data-ttu-id="7ecc3-161">次のセクション: 6.デバイスまたはエミュレーターのパッケージ化およびデプロイ</span><span class="sxs-lookup"><span data-stu-id="7ecc3-161">Next Section: 6. Packaging & deploying to device or emulator</span></span>](unreal-uxt-ch6.md)
