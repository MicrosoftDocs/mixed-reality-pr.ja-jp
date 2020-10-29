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
# <a name="5-adding-a-button--resetting-piece-locations"></a>5.ボタンの追加およびピースの位置のリセット


## <a name="overview"></a>概要

前のチュートリアルでは、ポーン コンポーネントにハンド インタラクション アクターを追加し、チェス盤にマニピュレーター コンポーネントを追加して、両方を対話型にしました。 このセクションでは、チェス アプリの機能を構築することによって、Mixed Reality ツールキット UX ツール プラグインを引き続き操作します。 これには、新しい関数の作成と、ブループリントでアクターへの参照を取得する方法についての説明が含まれます。 このセクションの完了までに、デバイスまたはエミュレーターに Mixed Reality アプリをパッケージ化してデプロイする準備が整います。

## <a name="objectives"></a>目標

* 対話型ボタンの追加
* ピースの位置をリセットする関数を作成する
* 押されたときに関数をトリガーするボタンをフックする

## <a name="creating-a-reset-function"></a>Reset 関数の作成
最初のタスクは、チェスのピースをシーンの元の位置にリセットする関数のブループリントを作成することです。 

1.  **WhiteKing** を開き、 **[My Blueprint]** の **[関数]** セクションの横にある **+** アイコンをクリックして、 **[Reset Location]** という名前を付けます。 

2.  **SetActorRelativeTransform** ノードを作成するには、ブループリント グリッドの **Reset Location** から実行をドラッグしてリリースします。 
    * この関数では、アクターの親に対して相対的に変換 (位置、回転、スケール) を設定します。 この関数を使用すると、ボードが元の位置から移動した場合でもボード上のキングの位置がリセットされます。 
    
3. イベント グラフ内で右クリックし、 **[変換の作成]** を選択し、 **[場所]** を **X =-26** 、 **Y = 4** 、 **Z = 0** に変更します。
    * **SetActorRelativeTransform** の **[新しい相対変換]** ピンに **[戻り値]** を接続します。 

![Reset Location (位置のリセット) 関数](images/unreal-uxt/5-function.PNG)

メイン ウィンドウに戻る前に、プロジェクトを **コンパイル** して **保存** します。 


## <a name="adding-a-button"></a>ボタンを追加する
関数が正しくセットアップされたので、次のタスクでは、タッチしたときにオフにするボタンを作成します。 


1.  **[新しく追加] > [ブループリント クラス]** をクリックし、 **[すべてのクラス]** セクションを展開して、「 **BP_ButtonHoloLens2** 」を検索します。 
    * これに **ResetButton** という名前を付け、ダブルクリックしてブループリントを開きます。

> [!NOTE]
> **BP_ButtonHoloLens2** は、UX Tools プラグインの一部である 3D ボタンのブループリント アクターです。

![HoloLens 2 スタイル ボタンから新しいブループリントをサブクラス化する](images/unreal-uxt/5-subclass.PNG)

2. **[コンポーネント]** パネルで **[ResetButton(self)]** が選択されていることを確認します。 **[詳細]** パネルで、 **[ボタン]** セクションに移動します。 **[ボタン ラベル]** の既定を [リセット] に変更します。 **[Button Icon Brush]\(ボタン アイコンのブラシ\)** セクションを展開し、 **[Open Icon Brush Editor]\(Icon Brush Editor を開く\)** ボタンをクリックします。 

![ボタンのラベルとアイコンを設定する](images/unreal-uxt/5-buttonconfig.PNG)

これにより、ボタンの新しいアイコンを選択するために UX Tools プラグインによって提供されたユーティリティ、Icon Brush Editor が開きます。 

![ボタンのアイコンを選択する](images/unreal-uxt/5-iconbrusheditor.PNG)

ボタンの構成のために調整できる設定は、他にも多くあります。 UXT Pressable Button コンポーネントの詳細については、[ドキュメント](https://microsoft.github.io/MixedReality-UXTools-Unreal/version/public/0.9.x/Docs/PressableButton.html)をご覧ください。

3. **[コンポーネント]** パネルの **[UxtPressableButton (継承)]** をクリックし、 **[詳細]** パネルを下にスクロールして **[イベント]** セクションを表示します。 
    * **[On Button Pressed]\(ボタンが押されたとき\)** の横にある緑色の **+** のボタンをクリックして、ボタンが押されたときに呼び出されるイベントをイベント グラフに追加します。 
    
ここから、レベルの **WhiteKing** アクターへの参照が必要な  **WhiteKing** の **Reset Location** 関数を呼び出す必要があります。 

4.  **[My Blueprint]\(マイ ブループリント\)** パネルの **[変数]** セクションに移動し、 **[+]** ボタンをクリックして、変数に **WhiteKing** という名前を付けます。 
    * **[Details]\(詳細\)** パネルで、 **[Variable Type]\(変数の種類\)** の横にあるドロップダウンを選択し、 **WhiteKing** を検索して、 **[Object Reference]\(オブジェクト参照\)** を選択します。 
    * **[Instance Editable]\(インスタンス編集可能\)** の横のボックスをオンにします。 これにより、変数をメイン レベルから設定できるようになります。 

![変数を作成する](images/unreal-uxt/5-var.PNG)

5.  WhiteKing 変数を **[My Blueprint]\(マイ ブループリント\) > [Variables]\(変数\)** から Reset Button イベント グラフにドラッグし、 **[WhiteKing の取得]** を選択します。 

## <a name="firing-the-function"></a>関数の起動
あとは、ボタンが押されたときに Reset 関数を正式に起動するだけです。

1.  WhiteKing の出力ピンをドラッグしてリリースし、新しいノードを配置します。 **Reset Location** 関数を選択します。 最後に、 **[On Button Pressed]\(ボタンが押されたとき\)** から出力実行ピンを **[Reset Location]** の入力実行ピンにドラッグします。 ResetButton ブループリントの **[Compile]\(コンパイル\)** と **[Save]\(保存\)** の後、メイン ウィンドウに戻ります。 

![On Button Pressed (ボタンが押されたとき) から Reset Location 関数を呼び出す](images/unreal-uxt/5-callresetloc.PNG)

2.  **ResetButton** をビューポートにドラッグし、その位置を **X = 50** 、 **Y = -25** 、 **Z = 10** に設定します。 回転を **Z = 180** に設定します。 **[Default]\(既定\)** で、 **WhiteKing** 変数の値を **WhiteKing** に設定します。

![変数の値を設定する](images/unreal-uxt/5-buttonlevel.PNG)

アプリを実行し、チェスのピースを新しい場所に移動し、先ほどの HoloLens 2 スタイル ボタンを押すと、リセット ロジックが動作するのを確認できます。

これで、対話可能なチェスの駒とボードを備えた Mixed Reality アプリと、ピースの位置をリセットする、完全に機能するボタンが完成しました。 ここまでで完成したアプリは [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/tree/master/ChessApp) リポジトリにあります。 このチュートリアルをさらに進めて、ボタンを押したときにボード全体がリセットされるように、チェスの残りのピースを設定してみてください。

![ビューポートの終わりのシーン](images/unreal-uxt/5-endscene.PNG)

このチュートリアルの最後のセクションに進む準備ができました。そこでは、アプリを正しくパッケージ化してデバイスまたはエミュレーターにデプロイする方法について説明します。

> [!IMPORTANT]
> アプリケーションをデバイスまたはエミュレーターにデプロイする前のこの時点で、推奨される **[Unreal パフォーマンス設定](../performance-recommendations-for-unreal.md)** を使用してプロジェクトを更新する必要があります。

[次のセクション: 6.デバイスまたはエミュレーターのパッケージ化およびデプロイ](unreal-uxt-ch6.md)
