---
title: Windows Mixed Reality を設定する
description: Windows Mixed Reality のモーションコントローラー、音声、オーディオを設定し、安全な再生スペース用の部屋の境界を定義する方法。
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、はじめに、セットアップ、モーションコントローラー、コントローラー、音声、オーディオ、取り付け済み、継続的、境界、グラフィックスドライバー、Microsoft Edge、chromium
ms.openlocfilehash: 693c55a7375dd2cb1b4a6f880fca31ba8d50c7f9
ms.sourcegitcommit: b90697776b7027ed7eb8dd49a72d52740a16d12d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96843130"
---
# <a name="set-up-windows-mixed-reality"></a>Windows Mixed Reality を設定する

## <a name="get-ready"></a>準備

Windows Mixed Reality を実行するには、次のものが必要です。

* 互換性のある混合現実イマーシブヘッドセット。 [詳細情報](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)
* ヘッドセット用の正しいポートを備えた[Windows Mixed Reality 対応 PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* モーション [コントローラー](controllers-in-wmr.md)、Xbox コントローラー、またはマウスとキーボード
* マイクを使用したヘッドホン (ヘッドセットに組み込まれていない場合)
* 大きな空き領域

## <a name="get-set"></a>セットの取得

領域 (オーバーヘッド領域を含む) を準備します。 使用する領域に、障害、危険、または脆弱な項目がないことを確認します。 階段の上部、または低天井ファンの下には設定しないでください。 領域からすべてのブレーク可能または障害を除去し、すべてのヘッドセットユーザーが安全性ガイドラインを読んで理解していることを確認します。

スペースの準備ができたら、ヘッドセットにプラグインしますが、まだ入れないでください。まず、PC でセットアップを行う必要があります。 PC チェックを実行し、ソフトウェアをダウンロードし、コントローラーに接続して、障害を回避するための [境界](boundary-questions.md) を作成します。

その後、お使いのヘッドセットに入って、混合世界に入ることができます。 Cortana は、ツアーの提供を待っています。 お楽しみください!

## <a name="go"></a>始めましょう。

スペースの準備ができたら、ヘッドセットにプラグインしますが、まだ入れないでください。まず、PC でセットアップを行う必要があります。 PC チェックを実行し、ソフトウェアをダウンロードし、コントローラーに接続して、障害を回避するための [境界](boundary-questions.md) を作成します。

その後、お使いのヘッドセットに入って、混合世界に入ることができます。 Cortana は、ツアーの提供を待っています。 お楽しみください!

## <a name="get-familiar-with-your-motion-controllers"></a>モーションコントローラーについて理解を深める

ヘッドセットにラジオが内蔵されている場合は、ヘッドセットに付属するコントローラーが工場でペアリングされます。 新しいコントローラーとヘッドセットを初めてオンにすると、既にペアリングされています。

組み込みのラジオがないヘッドセットがある場合は、それらを PC にペアリングすることで、モーションコントローラーを設定する必要があります。 2018の後に製造されるほとんどのヘッドセットには、ラジオが組み込まれています。

Xbox ゲームパッド、キーボード、およびマウスを使用することのみを計画している場合は、コントローラーをペアリングする必要はありません。  コントローラーの使用を計画している場合は、それらをペアにすることをお勧めします。

**注**: Windows Mixed Reality モーションコントローラーでは、Bluetooth 4.0 が必要です。 PC に Bluetooth が組み込まれていない場合は、Bluetooth 4.0 をサポートする USB Bluetooth アダプターを接続して、動きコントローラーを有効にする必要があります。 ヘッドセットで内蔵のラジオを使用するための Bluetooth アダプターは必要ありません。

![モーションコントローラーについて理解を深める](images/get_to_know_controllers.png)

モーションコントローラーをペアリングする必要がある場合は、「 [Windows Mixed Reality のコントローラー」](controllers-in-wmr.md) を参照してください。

## <a name="set-up-your-room-boundary"></a>部屋の境界を設定する

ルームスケールまたはデスクスケールエクスペリエンスを選択します。

**オプション 1: すべてのエクスペリエンス (room スケールとも呼ばれます) に対して** セットアップを実行すると、ルームを段階的に確認できます。これは、最もイマーシブな mixed reality エクスペリエンスです。 混合現実には、少なくとも5フィート x 7 フィート (1.5 メートル x 2 メートル) の領域を明確にすることをお勧めします。

**オプション 2: 装着されている (机のスケールとも呼ばれる) エクスペリエンスのために** 、デスクで動作するように設定します。 スペースが大きい場合は、このオプションを使用することをお勧めします。 また、境界のないヘッドセットを使用することにもなります。 物理的な障害を回避するための境界がないため、1つの場所に保持する必要があります。 また、一部のアプリとゲームは境界で使用するように設計されているため、意図したとおりに動作しないことがあります。

![セットアップの選択](images/1050px-chooseasetup.png)

### <a name="if-you-choose-set-me-up-for-all-experiences"></a>[すべてのエクスペリエンスに設定する] を選択した場合

間もなく、お客様の部屋が仮想環境になります。 混合現実を実行するために、部屋の一部の領域を解放してクリアします。 混合現実の場合は、少なくとも5フィート x 7 フィートまたは1.5 メートル x 2 メートル以上の容量が必要です。

![スペースが明確になっていることを確認する](images/1050px-createaboundary.png)

スペースが明確になっていることを確認します。

![ヘッドセットを中央に配置する](images/1050px-createaboundary-2.png)

ヘッドセットを中央に配置します。

![境界をトレースする](images/1050px-createaboundary-3.png)

境界をトレースします。

![PC をポイントしたままにする](images/1050px-createaboundary-4.png)

ヘッドセットを PC に対してポイントしたままにします。

![お客様の境界](images/1050px-createaboundary-5.png)

次に、境界を示します。

### <a name="if-you-choose-set-me-up-for-seated-and-standing"></a>[固定された状態に設定する] を選択した場合

このオプションを選択した場合、追加の手順は必要ありません。

## <a name="what-is-the-maximum-size-of-the-boundary"></a>境界の最大サイズは何ですか。

Windows Mixed Reality でサポートされる最大境界サイズは、中央から 18x18ft (5.7 x 5.7 m) または 13 ft (4 m) の半径です。  境界サイズはアンカーポイントによって異なり、境界の安定性を危険にさらされる前に移動できるアンカーポイントからの距離によって決まります。  Windows Mixed Reality は、プラットフォームのステージの抽象化に基づいて構築されています。ステージは、移動する領域です。 このステージは1つのアンカーに依存しており、ほとんどすべてのアプリは1つの座標系を持つだけなので、Naopak と Oculus の動作も想定しています。  これは、内部では、アンカーポイントから離れた場所に移動するときに、ヘッドセットの追跡が安定した状態を維持するために必要です。  境界は、物理的な障害を回避することを目的としています。そのため、中心からさらに多くの問題が発生します。  境界の最大サイズを決定するために、2つの要素がありました。Windows Mixed Reality ヘッドセットが、境界とヘッドセットケーブルの長さに最適な部屋のスケールエクスペリエンスを提供できる最大距離。ほとんどの Windows Mixed Reality ヘッドセットは 10 ft (3 m) です。

## <a name="set-up-speech"></a>音声の設定

Cortana コマンドを mixed reality で有効にすることができます。これにより、音声コマンドを使用してアプリをテレポートして開くことができます。 これらのアクションの詳細については、「 [Mixed Reality の学習](learn-mixed-reality.md) 」の章を参照してください。

![音声によって Mixed reality の方が優れています。](images/1050px-betterwithspeech.png)

## <a name="set-up-your-audio-headset"></a>オーディオヘッドセットを設定する

AKG ヘッドホンとデュアルマイクアレイが統合された Samsung HMD Odyssey を購入していない場合は、マイクとヘッドホンの両方を備えたオーディオヘッドセットを入手し、ヘッドセットの 3.5-mm オーディオジャックに接続する必要があります。 ヘッドセットの 3.5-mm オーディオジャックは、ヘッドセットバイザーの下側、またはヘッドセットバイザーに接続されている短いオーディオケーブルの最後にあるヘッドセットモデルによって異なります。

## <a name="adjusting-your-headsets-display-settings"></a>ヘッドセットの表示設定を調整する

Windows Mixed Reality では、PC のハードウェア構成に基づいて、品質とパフォーマンスのバランスを取るディスプレイの設定が自動的に選択されます。 これらの設定を調整するには、[設定] [ **Mixed Reality > ヘッドセットの表示] >** にアクセスします。

### <a name="visuals"></a>ビジュアル

この設定は、Mixed reality ホームの視覚的な品質を制御します。 既定値は "Automatic" です。

### <a name="resolution"></a>解決方法

ヘッドセットのネイティブ解像度を次に示します。

高解像度のヘッドセットを PC に接続した場合 (たとえば、4320x2160 が表示されているヘッドセット)、Mixed reality の表示解像度を調整する設定が表示されます。

* この設定では、Windows Mixed Reality コンポジションスタックをネイティブにレンダリングするオプション (たとえば、4320x2160) を使用するか、コンポジションスタックを低解像度でレンダリングするか (たとえば、2upscale 0x1440 ではレンダリングし、upscale を4320x2160 にする) を指定できます。
* 既定の設定では、(たとえば、 **4320 x 2160 (最高品質)** オプションを) ネイティブにレンダリングして、ヘッドセットの画質を最大限に高めることができます。
* PC がヘッドセットのグラフィックスハードウェアの最小要件を満たしていない場合、解像度が高くなります。または、グラフィックスパフォーマンスの問題が見られる場合は、[ **自動アップスケール (最適なパフォーマンス)** ] オプションを選択してみてください。

この設定は、Windows 10 バージョン1903以降で使用できます。

### <a name="calibration"></a>調整

この設定は、ソフトウェアの IPD をサポートするヘッドセットの IPD 調整を調整するためのものです。

### <a name="experience-options"></a>エクスペリエンスオプション

この詳細設定は、既定のヘッドセット表示のリフレッシュレートエクスペリエンスよりも優先されます。

* **自動 (既定値)**: PC のハードウェア構成に基づいて、60 hz または 90 hz エクスペリエンスを自動的に選択します。
* **60 Hz**
* **90 Hz**

>[!Note]
>HP リバーブ G2 ヘッドセットを最初に設定すると、エクスペリエンスが最高になるように90Hz に変更されます。  必要に応じて、これを自動に変更できます。

### <a name="input-switching"></a>入力の切り替え

この設定は、ヘッドセットのプレゼンスセンサーに応じて、Windows Mixed Reality の動作を制御します。

* **ヘッドセットプレゼンスセンサーを使用して自動的に切り替える** (既定): ヘッドセットを装着している場合は、windows によって自動的に入力 (キーボード、マウスなど) が Windows Mixed Reality に自動的に送信されます。 Win + Y を使用すると、いつでもオーバーライドできます。
* **Windows ロゴキーを使用して手動で切り替える + Y**: ヘッドセットが装着されていることを検出するためにヘッドセットプレゼンスセンサーを使用しません。 Win + Y を使用して、PC デスクトップと Windows Mixed Reality の間で入力を切り替える必要があります。

この設定は、Windows 10 バージョン1903以降で使用できます。

## <a name="installing-microsoft-edge"></a>Microsoft Edge のインストール 

Windows Mixed Reality ホームで新しい Chromium ベースの Microsoft Edge を使用するには、windows Mixed Reality ホームの Win32 アプリケーション (新しい Microsoft Edge など) のネイティブサポートのために Windows 10 バージョン1903以降にアップグレードします。 Windows Update を確認 [するか、Windows 10 の最新バージョンを手動でインストールして](https://www.microsoft.com/software-download/windows10)ください。

>[!IMPORTANT]
>新しい Microsoft Edge は、VR ヘッドセット用のイマーシブ web エクスペリエンスを作成するための新しい標準である WebXR のサポートで起動します。 新しい Microsoft Edge をインストールすると、Microsoft Edge で WebVR エクスペリエンスを再生できなくなります。

### <a name="issues-with-the-new-microsoft-edge-in-windows-mixed-reality"></a>Windows Mixed Reality の新しい Microsoft Edge に関する問題

**Windows 10 バージョン 1903 (またはそれ以降) の2020-01 累積更新プログラムによって解決された既知の問題**

- 新しい Microsoft Edge を含む任意の Win32 アプリを起動すると、ヘッドセットの表示が短時間フリーズします。
- Microsoft Edge タイルは、Windows Mixed Reality の [スタート] メニューから消えます ("クラシックアプリ" フォルダーで見つけることができます)。
- 以前の Microsoft Edge からの Windows は、mixed reality ホームの周囲に配置されていますが、使用することはできません。 これらのウィンドウをアクティブ化しようとすると、デスクトップアプリで Edge が起動します。
- Mixed reality ホームでハイパーリンクを選択すると、mixed reality ホームではなく、デスクトップで web ブラウザーが起動します。
- Webvr ショーケースアプリは、WebVR がサポートされなくなっても、mixed reality ホームに存在します。
- キーボード起動とビジュアルの全般的な機能強化。

**その他の既知の問題**

- Windows Mixed reality で開かれている web サイトは、Mixed reality ポータルが閉じたときに失われます。ただし、Microsoft Edge ウィンドウは、mixed reality ホームに配置された場所に残ります。
- Microsoft Edge ウィンドウからのオーディオは spatialized ません。
- 360 Viewer 拡張機能のバージョン 2.3.8: Windows Mixed Reality で YouTube から360ビデオを開くと、ヘッドセットでビデオがゆがんでしまう可能性があります。 Edge を再起動して、この問題を解決するには、360 Viewer 拡張機能を非表示にする必要があります。 アドレスバーに「」と入力し、[拡張機能] の横にある [展開] ボタンを選択すると、拡張機能のバージョンを確認でき `edge://system/` ます。
- Windows Mixed Reality セッション中に、[設定] の [ **> システム > 表示** に汎用物理モニターとして表示されます。

## <a name="launching-mixed-reality-after-the-first-time"></a>最初に mixed reality を起動する

2回目に mixed reality を入力することは、PC に接続している間にヘッドセットを戻すのと同じように簡単です。 また、[スタート] メニューから開いて、Mixed Reality ポータルアプリケーションを手動で起動することもできます。 入力とオーディオは、オンヘッドヘッドに自動的にルーティングされます。または、キーボードの **Windows + Y** キーを押して手動でトリガーすることもできます。

## <a name="see-also"></a>関連項目

* [コミュニティへの質問](https://answers.microsoft.com)
* [サポートについては、お問い合わせください](https://support.microsoft.com/contactus/)
* [インストールのトラブルシューティング](installation_errors.md)
* [セットアップのトラブルシューティング](wmr-setup-faq.md)
* [Mixed Reality について学習する](learn-mixed-reality.md)
* [モーション コントローラー](controllers-in-wmr.md)
* [インサイドアウト追跡のしくみ](tracking-system.md)
