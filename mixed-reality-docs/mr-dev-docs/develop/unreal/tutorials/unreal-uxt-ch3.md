---
title: 3. Mixed Reality のプロジェクト設定
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 3
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント
ms.openlocfilehash: 5af888fe57afce21e9ff0ccfe8144533e7368acf
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91701566"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a>3.Mixed Reality のプロジェクト設定

## <a name="overview"></a>概要

前のチュートリアルでは、チェス アプリ プロジェクトの設定に時間を費やしました。 このセクションでは、Mixed Reality 開発用にアプリを設定する手順について説明します。これは、AR セッションを追加することを意味します。 このタスクには ARSessionConfig データ資産を使用します。この資産には、空間マッピングやオクルージョンなどの便利な AR 設定が多数含まれています。 さらに詳しく知りたい場合は、Unreal Engine のドキュメントに、[ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) 資産と [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) クラスの詳細が記載されています。

## <a name="objectives"></a>目標
* Unreal Engine の AR 設定の操作 
* ARSessionConfig データ資産の使用
* ポーンとゲーム モードの設定

## <a name="adding-the-session-asset"></a>セッション資産の追加
Unreal の AR セッションは、それ自体では発生しません。 セッションを使用するには、次の作業として使用する ARSessionConfig データ資産が必要です。

1. **[コンテンツ ブラウザー]** で、 **[新規追加] > [その他] > [Data Asset]\(データ資産\)** をクリックします。 ルートの **[コンテンツ]** フォルダー レベルであることを確認してください。 
    * **ARSessionConfig** を選択し、 **[選択]** をクリックして、アセットに **ARSessionConfig** という名前を付けます。

![データ資産を作成する](images/unreal-uxt/3-createasset.PNG)

3. **ARSessionConfig** をダブルクリックして開き、既定の設定をすべてそのままにして、 **[保存]** をクリックします。 メイン ウィンドウに戻ります。 

![AR セッション構成](images/unreal-uxt/3-arsessionconfig.PNG)

これが完了したら、次のステップとして、レベルが読み込まれたときに AR セッションが開始され、レベルが終了したときに AR セッションが停止するようにします。 さいわい、Unreal には、 **レベル ブループリント** と呼ばれる特別な種類のブループリントがあり、レベル全体のグローバル イベント グラフとして機能します。 **レベル ブループリント** で ARSessionConfig アセットを接続すると、ゲームの再生が開始されたときに AR セッションが正常に起動します。

1. エディタのツールバーから、 **[ブループリント] > [レベル ブループリントを開く]** をクリックします。 

![オープン レベルのブループリント](images/unreal-uxt/3-level-blueprint.PNG)

5. 実行ノード (左向き矢印アイコン) を **Event BeginPlay** からドラッグ アンド リリースします。 **[Start AR Session]\(AR セッションの開始\)** ノードを検索し、Enter キーを押します。  
    * **[セッション構成]** の下にある **[アセットの選択]** ドロップダウンをクリックし、 **ARSessionConfig** アセットを選択します。 

![AR セッションを開始する](images/unreal-uxt/3-start-ar-session.PNG)

6. EventGraph 内の任意の場所を右クリックし、新しい **Event EndPlay** ノードを作成します。 実行ピンをドラッグ アンド リリースします。 **[Stop AR Session]\(AR セッションの停止\)** ノードを検索し、Enter キーを押します。 レベルが終了しても AR セッションが停止していない場合、ヘッドセットへのストリーミング中にアプリを再起動すると、特定の機能が動作しなくなることがあります。 
    * **[コンパイル]** 、 **[保存]** をクリックして、メイン ウィンドウに戻ります。

![AR セッションの停止](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a>ポーンを作成する
この時点では、プロジェクトにはまだプレーヤー オブジェクトが必要です。 Unreal では、 **ポーン** はゲーム内のユーザーを表しますが、この場合は HoloLens 2 になります。

1. **[コンテンツ]** フォルダーで、 **[新規追加] > [ブループリント クラス]** をクリックし、下部にある **[すべてのクラス]** セクションを展開します。 
    * **DefaultPawn** を検索し、 **[選択]** をクリックして、 **MRPawn** という名前を付けてから、そのアセットをダブルクリックして開きます。 

![DefaultPawn から継承して新しいポーンを作成する](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> 既定では、ポーンにはメッシュと衝突コンポーネントがあります。 ほとんどの Unreal プロジェクトでは、ポーンは他のコンポーネントと競合する可能性のあるソリッド オブジェクトです。 ポーンとユーザーは Mixed Reality で同じであるため、衝突せずにホログラムを通過できるようにする必要があります。 

2. **[コンポーネント]** パネルから **CollisionComponent** を選択し、 **[詳細]** パネルの **[衝突]** セクションまでスクロールします。 
    * **[衝突プリセット]** ドロップダウンをクリックして、値を **NoCollision** に変更します。 
    * **MeshComponent** に対しても同じ操作を行います。

![ポーンの衝突プリセットを調整する](images/unreal-uxt/3-nocollision.PNG)

3. **[コンポーネント]** パネルから **[コンポーネントの追加] > [カメラ]** の順にクリックし、 **Camera** という名前を付けます。 これで、プレーヤー カメラは HoloLens 2 デバイスと移動できるようになります。

4. ブループリントを **コンパイル** して、 **保存** します。

ここで作業を完了したら、メイン ウィンドウに戻ります。

## <a name="create-a-game-mode"></a>ゲーム モードを作成する
Mixed Reality セットアップの最後のステップはゲーム モードです。 ゲーム モードでは、使用する既定のポーンなど、ゲームやエクスペリエンスのさまざまな設定を決定します。

1.  **[コンテンツ]** フォルダーで、 **[新規追加] > [ブループリント クラス]** をクリックし、下部にある **[すべてのクラス]** セクションを展開します。 
    * **Game Mode Base** を検索し、 **MRGameMode** という名前を指定し、ダブルクリックして開きます。 

![コンテンツ ブラウザー内の MRGameMode](images/unreal-uxt/3-gamemode.PNG)

2.  **[詳細]** パネルの **[クラス]** セクションに移動し、 **[既定のポーン クラス]** を **MRPawn** に変更します。 
    * **[コンパイル]** 、 **[保存]** をクリックして、メイン ウィンドウに戻ります。 

![既定のポーン クラスを設定する](images/unreal-uxt/3-setpawn.PNG)

3.  **[編集] > [プロジェクトの設定]** を選択し、左側のリストで **[マップとモード]** をクリックします。 
    * **[既定モード]** を展開し、 **[既定のゲーム モード]** を **MRGameMode** に変更します。 
    * **[既定のマップ]** を展開し、 **EditorStartupMap** と **GameDefaultMap** の両方を **[メイン]** に変更します。 このようにして、エディターを閉じて再度開くか、ゲームをプレイしたときに、メイン マップが既定で選択されます。

![プロジェクト設定 - マップ & モード](images/unreal-uxt/3-mapsandmodes.PNG)

プロジェクトで Mixed Reality を完全にセットアップしたら、次のチュートリアルに進み、シーンにユーザー入力を追加できるようになります。 

[次のセクション: 4.シーンを対話型にする](unreal-uxt-ch4.md)