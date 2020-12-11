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
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3.Mixed Reality のプロジェクト設定

前のチュートリアルでは、チェス アプリ プロジェクトの設定に時間を費やしました。 このセクションでは、Mixed Reality 開発用にアプリを設定する手順について説明します。これは、AR セッションを追加することを意味します。 このタスクには ARSessionConfig データ資産を使用します。これには、空間マッピングやオクルージョンなどの便利な AR 設定が含まれています。 [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) 資産と [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) クラスの詳細については、Unreal のドキュメントを参照してください。

## <a name="objectives"></a>目標

* Unreal Engine の AR 設定の操作
* ARSessionConfig データ資産の使用
* ポーンとゲーム モードの設定

## <a name="adding-the-session-asset"></a>セッション資産の追加

Unreal の AR セッションは、それ自体では発生しません。 セッションを使用するには、ARSessionConfig データ資産を処理する必要があります。それが次のタスクです。

1. **[コンテンツ ブラウザー]** で、 **[新規追加] > [その他] > [Data Asset]\(データ資産\)** をクリックします。 ルートの **[コンテンツ]** フォルダー レベルであることを確認してください。
    * **ARSessionConfig** を選択し、 **[選択]** をクリックして、アセットに **ARSessionConfig** という名前を付けます。

![データ資産を作成する](images/unreal-uxt/3-createasset.PNG)

3. **ARSessionConfig** をダブルクリックして開き、既定の設定をすべてそのままにして、 **[保存]** をクリックします。 メイン ウィンドウに戻ります。

![AR セッション構成](images/unreal-uxt/3-arsessionconfig.PNG)

それが完了したら、次のステップとして、レベルが読み込まれたら AR セッションが開始し、レベルが終了したら停止するようにします。 さいわい、Unreal には、**レベル ブループリント** と呼ばれる特別なブループリントがあり、レベル全体のグローバル イベント グラフとして機能します。 **レベル ブループリント** で ARSessionConfig アセットを接続すると、ゲームの再生が開始されたときに AR セッションが正常に起動します。

1. エディタのツールバーから、 **[ブループリント] > [レベル ブループリントを開く]** をクリックします。

![オープン レベルのブループリント](images/unreal-uxt/3-level-blueprint.PNG)

5. 実行ノード (左向き矢印アイコン) を **[Event BeginPlay]\(イベント BeginPlay\)** からドラッグして離し、 **[Start AR Session]\(AR セッションの開始\)** ノードを検索して Eenter キーを押します。  
    * **[セッション構成]** の下にある **[アセットの選択]** ドロップダウンをクリックし、**ARSessionConfig** アセットを選択します。

![AR セッションを開始する](images/unreal-uxt/3-start-ar-session.PNG)

6. EventGraph 内の任意の場所を右クリックし、新しい **Event EndPlay** ノードを作成します。 実行ピンをドラッグして離してから、 **[Stop AR Session]\(AR セッションの停止\)** ノードを検索して Enter キーを押します。 レベルが終了しても AR セッションがまだ実行されている場合、ヘッドセットへのストリーミング中にアプリを再起動すると、特定の機能が動作しなくなることがあります。
    * **[コンパイル]** 、 **[保存]** をクリックして、メイン ウィンドウに戻ります。

![AR セッションの停止](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a>ポーンを作成する

この時点では、プロジェクトにはまだプレーヤー オブジェクトが必要です。 Unreal では、**ポーン** はゲーム内のユーザーを表しますが、この場合は HoloLens 2 になります。

1. **[コンテンツ]** フォルダーで、 **[新規追加] > [ブループリント クラス]** をクリックし、下部にある **[すべてのクラス]** セクションを展開します。
    * **DefaultPawn** を検索し、 **[選択]** をクリックして、**MRPawn** という名前を付けてから、そのアセットをダブルクリックして開きます。

![DefaultPawn から継承して新しいポーンを作成する](images/unreal-uxt/3-defaultpawn.PNG)

2. **[コンポーネント]** パネルから **[コンポーネントの追加] > [カメラ]** の順にクリックし、**Camera** という名前を付けます。 **Camera** コンポーネントがルート (**CollisionComponent**) の直接の子であることを確認します。 これで、プレーヤー カメラは HoloLens 2 デバイスと移動できるようになります。

> [!NOTE]
> 既定では、ポーンにはメッシュと衝突コンポーネントがあります。 ほとんどの Unreal プロジェクトでは、ポーンは他のコンポーネントと競合する可能性のあるソリッド オブジェクトです。 ポーンとユーザーは Mixed Reality で同じであるため、衝突せずにホログラムを通過できるようにする必要があります。

3. **[コンポーネント]** パネルから **CollisionComponent** を選択し、 **[詳細]** パネルの **[衝突]** セクションまでスクロールします。
    * **[衝突プリセット]** ドロップダウンをクリックして、値を **NoCollision** に変更します。
    * **MeshComponent** に対しても同じ操作を行います。

![ポーンの衝突プリセットを調整する](images/unreal-uxt/3-nocollision.PNG)

4. ブループリントを **コンパイル** して、**保存** します。

ここで作業を完了したら、メイン ウィンドウに戻ります。

## <a name="create-a-game-mode"></a>ゲーム モードを作成する

Mixed Reality セットアップの最後のステップはゲーム モードです。 ゲーム モードでは、使用する既定のポーンなど、ゲームやエクスペリエンスのさまざまな設定を決定します。

1.  **[Content]\(コンテンツ\)** フォルダーで **[Add New]\(新規追加\) > [Blueprint Class]\(ブループリント クラス\)** をクリックし、親クラスとして **[Game Mode Base]\(ゲーム モード ベース\)** を選択します。 **MRGameMode** という名前を指定し、ダブルクリックして開きます。

![コンテンツ ブラウザー内の MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  **[詳細]** パネルの **[クラス]** セクションに移動し、 **[既定のポーン クラス]** を **MRPawn** に変更します。
    * **[コンパイル]** 、 **[保存]** をクリックして、メイン ウィンドウに戻ります。

![既定のポーン クラスを設定する](images/unreal-uxt/3-setpawn.PNG)

3.  **[編集] > [プロジェクトの設定]** を選択し、左側のリストで **[マップとモード]** をクリックします。
    * **[既定モード]** を展開し、 **[既定のゲーム モード]** を **MRGameMode** に変更します。
    * **[既定のマップ]** を展開し、**EditorStartupMap** と **GameDefaultMap** の両方を **[メイン]** に変更します。 エディターを閉じて再度開くか、ゲームをプレイすると、メイン マップが既定で選択されるようになります。

![プロジェクト設定 - マップ & モード](images/unreal-uxt/3-mapsandmodes.PNG)

プロジェクトで Mixed Reality を完全にセットアップしたら、次のチュートリアルに進み、シーンにユーザー入力を追加できるようになります。

[次のセクション: 4.シーンを対話型にする](unreal-uxt-ch4.md)
