---
title: 初めての HoloLens Unreal アプリケーションの作成
description: HoloLens Mixed Reality 開発用のシーン オブジェクトと入力対話式操作を含む Unreal プロジェクトを正しく構成する方法について説明します。
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, Unreal エディター, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, ドキュメント, ガイド, 機能, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 移植, アップグレード
ms.openlocfilehash: 467987f69b50c0ec635c99899d6bcecab5a62af0
ms.sourcegitcommit: 1304f8f0a838290c1ae3db34670b67c75ea9bdaa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/02/2021
ms.locfileid: "99421431"
---
# <a name="creating-your-first-hololens-unreal-application"></a>初めての HoloLens Unreal アプリケーションの作成

このガイドでは、Unreal Engine の HoloLens 上で初めての Mixed Reality アプリを実行する手順について説明します。 "Hello World" のように、画面にキューブを表示する簡単なアプリを作成します。 さらに便利にするために、最初のジェスチャも作成してキューブを回転させ、アプリケーションを終了します。 

## <a name="objectives"></a>目標

* HoloLens プロジェクトを開始する
* 正しいプラグインを有効にする
* ARSessionConfig データ資産を使用する
* ジェスチャ入力を設定する
* 基本レベルを構築する
* ピンチ ジェスチャを実装する

## <a name="creating-a-new-project"></a>新しいプロジェクトの作成

最初に必要なのは、作業するプロジェクトです。 Unreal で初めて開発する場合は、Epic Launcher から[サポート ファイルをダウンロードする](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)必要があります。

1. Unreal Engine を起動します。
2. **[New Project Categories]\(新しいプロジェクトのカテゴリ\)** で、 **[Games]\(ゲーム\)** を選択して **[Next]\(次へ\)** をクリックします。

![[Games]\(ゲーム\) が強調表示されている最近のプロジェクトのウィンドウ](images/unreal-quickstart-img-01.png)

3. **[Blank]\(空\)** テンプレートを選択して **[Next]\(次へ\)** をクリックします。

![空のテンプレートが強調表示されている Unreal プロジェクト ブラウザー ウィンドウ](images/unreal-quickstart-img-02.png)

4. **[Project Settings]\(プロジェクト設定\)** で、 **[C++]、[Scalable 3D or 2D]\(スケーラブル 3D または 2D\)、[Mobile/Tablet]\(モバイル/タブレット\)** 、 **[No Starter Content]\(スターター コンテンツを有効にしない\)** を設定し、保存場所を選択して、 **[Create Project]\(プロジェクトの作成)** をクリックします

> [!NOTE] 
> 後で OpenXR プラグインを使用できるようにするため、ブループリント プロジェクトではなく C++ を使用しています。 この QuickStart では、Unreal Engine に付属する既定の OpenXR プラグインを使用します。 ただし、公式の Microsoft OpenXR プラグインをダウンロードして使用することをお勧めします。 それには、プロジェクトが C++ プロジェクトである必要があります。

![プロジェクト、パフォーマンス、ターゲット プラットフォーム、スターター コンテンツの選択が強調表示されているプロジェクト設定ウィンドウ](images/unreal-quickstart-img-03.png)

新しいプロジェクトが Unreal エディターで自動的に開かれます。つまり、次のセクションに進む準備はできています。

## <a name="enabling-required-plugins"></a>必要なプラグインの有効化

オブジェクトをシーンに追加する前に、2 つのプラグインを有効にする必要があります。

1. **[編集] > [プラグイン]** を開き、組み込みオプション リストから **[拡張現実]** を選択します。
* **HoloLens** まで下にスクロールし、 **[Enabled]\(有効\)** をオンにします

![拡張現実セクションが開き HoloLens が強調表示されているプラグイン ウィンドウ](images/unreal-quickstart-img-04.png)

2. 右上の検索ボックスに「**OpenXR**」と入力し、**OpenXR** および **OpenXRMsftHandInteraction** プラグインを有効にします。

![OpenXR が有効になっているプラグイン ウィンドウ](images/unreal-quickstart-img-05.jpg)

![OpenXRMsftHandInteraction が有効になっているプラグイン ウィンドウ](images/unreal-quickstart-img-06.jpg)

3. エディターを再起動します

> [!NOTE]
> このチュートリアルでは OpenXR を使用しますが、上でインストールした 2 つのプラグインには、現在、HoloLens 開発用の完全な機能セットはありません。 後で使用する "ピンチ" ジェスチャには HandInteraction プラグインで十分ですが、基本機能以外を使用するには、[OpenXR プラグインをダウンロードする](https://github.com/microsoft/Microsoft-OpenXR-Unreal)必要があります。

プラグインを有効にすると、それにコンテンツを設定できます。

## <a name="creating-a-level"></a>レベルの作成

次のタスクは、参照とスケール用の開始点とキューブを使用してプレーヤーのセットアップを作成することです。

1. **[ファイル] > [新しいレベル]** を選択し、 **[空のレベル]** を選択します。 この時点では、ビューポートの既定のシーンは空です
2. **[Modes]\(モード\)** タブから **[Basic]\(基本\)** を選択し、**PlayerStart** をシーンにドラッグします
* **[Details]\(詳細\)** タブで、 **[Location]\(位置\)** を **X = 0、Y = 0**、**Z = 0** に設定して、アプリの起動時にユーザーをシーンの中心に設定します

![位置とプレーヤーのスタートが追加された Unreal エディター シーン](images/unreal-quickstart-img-07.png)

3. **[Basic]\(基本\)** タブから **Cube** をシーンにドラッグします
* キューブの **[Location]\(位置\)** を **X = 50、Y = 0**、**Z = 0** に設定して、開始時にプレーヤーから 50 cm 離れた位置にキューブを配置します
* キューブの **[Scale]\(スケール\)** を **X = 0.2、Y = 0.2**、**Z = 0.2** に変更します 

シーンにライトを追加しない限り、キューブを表示することはできません。これは、シーンをテストする前の最後のタスクです。

4. **[Modes]\(モード\)** パネルで **[Lights]\(ライト\)** タブに切り替えて、**Directional Light** をシーンにドラッグします
* ライトが見えるように、**PlayerStart** の上にそれを配置します

![キューブと指向性ライトが追加された Unreal エディターのシーン](images/unreal-quickstart-img-08.png)

5. **[File]\(ファイル\) > [Save Current]\(現在を保存\)** に移動し、レベルに **Main** という名前を付けて、 **[Save]\(保存\)** を選択します

シーンを設定したら、ツールバーの **[再生]** を押して、キューブの動作を確認します。 作業内容を鑑賞したら、Esc を押してアプリケーションを停止します。

![画面の中央にキューブがあるプレイ モードのシーン](images/unreal-quickstart-img-09.png)

シーンをセットアップしたので、AR でいくつかの基本的な対話式操作を実行できるようにします。 最初に、AR セッションを作成する必要があり、ブループリントを追加してハンド インタラクションを可能にできます。

## <a name="adding-a-session-asset"></a>セッション アセットの追加

Unreal の AR セッションは、それ自体では発生しません。 セッションを使用するには、ARSessionConfig データ資産を処理する必要があります。それが次のタスクです。

1. **[Content Browser]\(コンテンツ ブラウザー\)** で、 **[Add New]\(新規追加\) > [Miscellaneous]\(その他\) > [Data Asset]\(データ アセット\)** を選択し、ルート コンテンツ フォルダー レベルであることを確認します
2. **ARSessionConfig** を選択し、 **[Select]\(選択\)** をクリックして、アセットに **ARSessionConfig** という名前を付けます。

![AR セッション構成アセットが強調表示されている [Pick data asset class]\(データ資産クラス選択\) ウィンドウ](images/unreal-quickstart-img-10.png)

2. **ARSessionConfig** をダブルクリックして開き、既定の設定をすべてそのままにして **[Save]\(保存\)** を選択し、メイン ウィンドウに戻ります。

![AR セッション構成アセットの詳細ウィンドウ](images/unreal-quickstart-img-11.png)

それが完了したら、次のステップとして、レベルが読み込まれたら AR セッションが開始し、レベルが終了したら停止するようにします。 さいわい、Unreal には、**レベル ブループリント** と呼ばれる特別なブループリントがあり、レベル全体のグローバル イベント グラフとして機能します。 レベル ブループリントで ARSessionConfig アセットを接続すると、ゲームの再生が開始されたときに AR セッションが正常に起動します。

3. エディターのツール バーから、 **[Blueprints]\(ブループリント\) > [Open Level Blueprint]\(Level ブループリントを開く\)** をクリックします。

![[Open Level Blueprint]\(Level ブループリントを開く\) オプションが強調表示されているブループリント メニュー](images/unreal-quickstart-img-12.png)

4. 実行ノード (左向き矢印アイコン) を **Event BeginPlay** からドラッグして離します
* **[Start AR Session]\(AR セッションの開始\)** ノードを検索し、Enter キーを押します
* **[Session Config]\(セッション構成\)** の下にある **[Select Asset]\(アセットの選択\)** ドロップダウンをクリックし、**ARSessionConfig** アセットを選択します

![プレイ開始イベントが AR セッション開始関数に接続されたブループリント グラフ](images/unreal-quickstart-img-13.png)

5. EventGraph 内の任意の場所を右クリックし、新しい **Event EndPlay** ノードを作成します。 
* 実行ピンをドラッグして離してから、 **[Stop AR Session]\(AR セッションの停止\)** ノードを検索して Enter キーを押します 
* **[Compile]\(コンパイル\)** 、 **[Save]\(保存\)** の順にクリックして、メイン ウィンドウに戻ります

> [!IMPORTANT]
> レベルが終了しても AR セッションがまだ実行されている場合、ヘッドセットへのストリーミング中にアプリを再起動すると、特定の機能が動作しなくなることがあります。

![AR セッション停止関数に接続された EventEndPlay ノード](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a>入力の設定

1. **[Edit]\(編集\) > [Project Settings]\(プロジェクトの設定\)** を編集し、 **[Engine]\(エンジン\) > [Input]\(入力\)** に移動します
2. **[Action Mappings]\(アクション マッピング\)** の横にある **[+]** アイコンを選択して、**RightPinch** アクションと **LeftPinch** アクションを作成します。

![右と左のピンチ アクション マッピングが強調表示されているバインド入力設定](images/unreal-quickstart-img-15.jpg)

3. **RightPinch** および **LeftPinch** アクションをそれぞれの **OpenXR Msft ハンド インタラクション** アクションにマップします。

![OpenXR Msft ハンド インタラクション オプションが強調表示されたアクション マッピング](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a>ジェスチャの設定

入力を設定したので、わくわくする部分に進むことができます。ジェスチャの追加です。 右ピンチでキューブを回転させ、左ピンチでアプリケーションを終了しましょう。

1. **[Level Blueprint]\(Level ブループリント\)** を開き、**InputAction RightPinch** と **InputAction LeftPinch** を追加します
* ターゲットを **Cube** に設定し、 **[Delta Rotation]\(デルタ回転\)** を **X = 0、Y = 0**、**Z = 20** に設定して、右ピンチ イベントを **AddActorLocalRotation** に接続します。 これで、ピンチするたびにキューブが 20 度回転するようになります
* 左ピンチ イベントを **Quit Game** に接続します

![右と左のピンチ イベントに対する入力アクションが設定された Level ブループリント](images/unreal-quickstart-img-17.jpg)

2. キューブの **[Transform]\(変換\)** の設定で、 **[Mobility]\(モビリティ\)** を **[Movable]\(移動可能\)** に設定して、動的に移動できるようにします。

![モビリティ プロパティが強調表示されている変換設定](images/unreal-quickstart-img-18.jpg)

これで、アプリケーションをデプロイしてテストする準備ができました。