---
title: Windows Mixed Reality ホームのナビゲーション
description: HoloLens と Windows Mixed Reality ヘッドセットは、環境内でアプリと3D モデルを起動、配置、操作するパラダイムを共有しています (物理的またはデジタルのどちらの場合でも)。 両方の種類のデバイスで Windows Mixed Reality ホームを移動する方法について説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: シェル, os, プラットフォーム, 崖家, 家, ホーム, 環境, スタート, スタートメニュー, ホームメニュー, pin, アプリ, 起動アプリ, 配置アプリ, テレポート, 移動, 移動, mixed reality ヘッドセット, 仮想現実のヘッドセット, 仮想現実とは
ms.openlocfilehash: 590e52de7caacc515e703da19e9efdc0a2b9c535
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703448"
---
# <a name="navigating-the-windows-mixed-reality-home"></a>Windows Mixed Reality ホームのナビゲーション

Windows PC エクスペリエンスがデスクトップで起動するのと同じように、Windows Mixed Reality はホームから開始します。 Windows Mixed Reality ホームは、innate の機能を活用して3D の場所を理解し、移動します。 HoloLens では、自宅は物理的なスペースです。 イマーシブヘッドセットを使用すると、自宅は仮想の場所になります。

また、ホームでは、[スタート] メニューを使用してアプリとコンテンツを開いたり、配置したりすることもできます。 複数のアプリを同時に使用することで、大規模な現実のコンテンツとマルチタスクをホームにすることができます。 デバイスを再起動した場合でも、自宅に配置したものはそのままです。

## <a name="start-menu"></a>スタート メニュー

![Microsoft HoloLens の [スタート] メニュー](images/start-500px.png)

[スタート] メニューは次のもので構成されます。
* システム情報 (ネットワークの状態、バッテリの割合、現在の時刻、およびボリューム)
* Cortana (最初の段階で、HoloLens ではスタートタイル、最初は HoloLens)
* ピン留めされたアプリ
* [すべてのアプリ] ボタン (プラス記号)
* [Mixed reality キャプチャ](../mixed-reality-capture.md)の写真ボタンとビデオボタン

プラスボタンまたはマイナスボタンを選択して、ピン留めされたアプリとすべてのアプリビューを切り替えます。 HoloLens で [スタート] メニューを開くには、ブルームジェスチャを使用します。 イマーシブヘッドセットで、コントローラーの [Windows] ボタンを押します。

## <a name="launching-apps"></a>アプリの起動

アプリを起動するには、[スタート] で選択します。 [スタート] メニューが表示されなくなり、アプリは2D ウィンドウまたは [3d モデル](../distribute/implementing-3d-app-launchers.md)のいずれかとして配置モードで開きます。

アプリを実行するには、ホームに配置する必要があります。
1. 目的の場所にアプリを配置するには、 [宝石](../design/gaze-and-commit.md) またはコントローラーを使用します。 配置した領域に合わせて、自動的に (サイズと位置で) 調整されます。
2. エアタップ (HoloLens) または [選択] ボタン (イマーシブヘッドセット) を使用してアプリを配置します。 [スタート] メニューをキャンセルして元に戻すには、ブルームジェスチャまたは Windows ボタンを使用します。

デスクトップ、モバイル、または Xbox 用に作成された[2d アプリ](../develop/porting-apps/building-2d-apps.md)は、 [HolographicSpace API](https://msdn.microsoft.com/library/windows/apps/windows.graphics.holographic.holographicspace.aspx)を使用して mixed reality イマーシブアプリとして実行するように変更できます。 イマーシブアプリによって、ユーザーは家庭から、またはイマーシブエクスペリエンスを利用できます。 ユーザーは、ブルームジェスチャ (HoloLens) を使用するか、コントローラー (イマーシブヘッドセット) の Windows ボタンを押すことによって、自宅を返すことができます。

アプリはアプリ間 API または Cortana を使用して起動することもできます。

![Windows Mixed Reality ホームのアプリ](images/mixed-reality-home-500px.png)

## <a name="moving-and-adjusting-apps"></a>アプリの移動と調整

アプリバーの [ **調整** ] を選択すると、mixed reality コンテンツの移動、拡大縮小、および回転を行うコントロールが表示されます。 終了したら、[ **完了**] を選択します。

![調整モード (青いフレーム) の場合、ストアはスレートです。 メモアプリバー (上部) には、[完了] ボタンと [削除] ボタンが表示されるように変更されました。](images/adjust-500px.png)

アプリによっては、アプリバーに他のオプションが追加される場合があります。 たとえば、Microsoft Edge には、 *スクロール*、 *ドラッグ*、および *ズーム* の選択肢があります。 

![HoloLens で実行されている2D アプリのアプリバー](images/holobar-500px.png)

[ **戻る** ] ボタンをクリックすると、アプリで以前に表示されていた画面に戻ります。 アプリに表示されているエクスペリエンスの最初に達したときに停止し、他のアプリには移動しません。

## <a name="getting-around-your-home"></a>ホームに移動する

**HoloLens** では、ホームに移動するために物理的な領域を移動します。

**イマーシブヘッドセット** を使用すると、同じような方法で playspace を利用して、仮想環境内の同様の領域内で移動することもできます。 距離をさらに長くするには、コントローラーでサムスティックを使用して仮想的に "ウォーク" します。または、電話を使用して、距離をすぐに *長くすること* ができます。

![Windows Mixed Reality ホームの受付](images/teleportation-500px.png)

**テレポートするには:**
1. Reticle を立ち上げます。
   * [モーションコントローラー](../design/motion-controllers.md)の使用: サムスティックを前方に押し、その位置に保持します。
   * Xbox コントローラーを使用する: 左スティックを前方に押し、その位置に保持します。
   * マウスを使用して、マウスの右ボタンを押したままにします (そして、スクロールホイールを使用して、テレポート時の方向を回転させます)。
2. テレポートする場所に reticle を配置します。
   * [モーションコントローラー](../design/motion-controllers.md)の使用: reticle を移動するには、(サムスティックを前方に保持している) コントローラーを傾けます。
   * Xbox コントローラーの使用: reticle を移動するには、 [宝石](../design/gaze-and-commit.md) を使用します。
   * マウスを使用する: マウスを動かして reticle を移動します。
3. ボタンを離して、reticle が配置された位置にテレポートします。

**実際に "ウォーク:"**
* [モーションコントローラー](../design/motion-controllers.md)を使用する: サムスティックを押したままにして、サムスティックを "ウォーク" する方向に移動します。
* Xbox コントローラーを使用する: 左スティックを押したままにして、サムスティックを "ウォーク" する方向に移動します。

## <a name="immersive-headset-input-support"></a>イマーシブヘッドセットの入力サポート

[Windows Mixed reality イマーシブヘッドセット](immersive-headset-hardware-details.md) は、Windows mixed reality ホーム内を移動するための複数の入力の種類をサポートしています。 HoloLens は、ナビゲーションのためのアクセサリ入力をサポートしていません。これは、環境が物理的に移動して表示されるためです。 ただし、HoloLens は、アプリと対話するための [入力をサポート](hardware-accessories.md) しています。

### <a name="motion-controllers"></a>モーション コントローラー

最適な Windows Mixed Reality エクスペリエンスは、ヘッドセットのセンサーのみを使用して6度の自由度の追跡をサポートする Windows Mixed Reality の [モーションコントローラー](../design/motion-controllers.md) です。外部カメラやマーカーは必要ありません。

ナビゲーションコマンドは近日公開予定です。

### <a name="gamepad"></a>ゲームパッド
* **左サムスティック:**
  * 左スティックを前方に押して [、reticle を表示します](navigating-the-windows-mixed-reality-home.md#getting-around-your-home) 。
  * 左、右、または後ろにあるサムスティックをタップして、小さい順に左または右に移動します。
  * 左側のサムスティックを押したままにして、画面のサムスティックを任意の方向に移動し [ます。](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)
* **右サムスティック** を左または右にタップして、表示する方向を45°回転させます。
* **A** ボタンを押すと、選択が実行され、[エアタップ](../design/gaze-and-commit.md#composite-gestures)ジェスチャのように動作します。
* [ **ガイド** ] ボタンを押すと、[ [スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu) が表示され、 [ブルーム](../design/system-gesture.md#bloom) ジェスチャのように動作します。
* **左トリガーと右トリガー** を押すと、自宅で対話している2d デスクトップアプリを拡大または縮小できます。

### <a name="keyboard-and-mouse"></a>キーボードとマウス

**注:****Windows キー + Y** を使用して、PC のデスクトップと Windows Mixed Reality ホームを制御するようにマウスを切り替えます。

Windows Mixed Reality ホーム内:
* **左クリック** でマウスボタンを押すと、選択が実行され、[エアタップ](../design/gaze-and-commit.md#composite-gestures)ジェスチャのように動作します。
* **右クリック** マウスボタンを押すと [、reticle が表示されます](navigating-the-windows-mixed-reality-home.md#getting-around-your-home)。
* キーボードの **Windows** キーを押すと、[ [スタート] メニュー](navigating-the-windows-mixed-reality-home.md#start-menu) が表示され、 [ブルーム](../design/system-gesture.md#bloom) ジェスチャのように動作します。
* 2D デスクトップアプリでの [移動時に](../design/gaze-and-commit.md) は、 **左クリック** して選択し、 **右クリック** してコンテキストメニューを表示し、スクロール **ホイール** を使用して (PC のデスクトップと同様に) スクロールできます。

## <a name="cortana"></a>Cortana

[Cortana](../design/voice-input.md#hey-cortana) は、PC や電話の場合と同じように、Windows Mixed Reality の個人用アシスタントです。 HoloLens にはマイクが内蔵されていますが、イマーシブヘッドセットには追加のハードウェアが必要になる場合があります。 Cortana を使用して、アプリを開いたり、デバイスを再起動したり、オンラインで検索することができます。 開発者は、Cortana をエクスペリエンスに [統合](https://dev.windows.com/cortana) することもできます。

また、音声コマンドを使用してホームにアクセスすることもできます。 たとえば、ボタン (デバイスによっては、 [宝石](../design/gaze-and-commit.md) またはコントローラーを使用) をポイントし、[選択] と言います。 その他の音声コマンドには、"外出先"、"大規模"、"小さく"、"閉じる"、"顔" などがあります。

## <a name="store-settings-and-system-apps"></a>ストア、設定、およびシステムアプリ

Windows Mixed Reality には、次のようなさまざまな組み込みアプリがあります。
* アプリとゲームを取得するための **Microsoft Store**
* システムアプリとシステムアプリに関するフィードバックを送信する **フィードバックハブ**
* システム設定を構成するための **設定**(ネットワークとシステムの更新プログラムを [含む](../connecting-to-wi-fi-on-hololens.md))
* Web サイトを参照するための **Microsoft Edge**
* 写真とビデオを表示して共有するための **写真**
* 現在のユーザーに対して HoloLens エクスペリエンスを調整するための **調整**(hololens のみ)
* デバイスの使用方法について学習するには、「**ジェスチャ**(HoloLens)」または「 **Mixed Reality** (イマーシブヘッドセット)」を参照してください。
* 混合の現実コンテンツで世界を装飾する **3D ビューアー**
* イマーシブヘッドセットを設定および管理し、他のユーザーが表示できるようにヘッドセット内のビューのライブプレビューをストリーミングする、 **Mixed Reality ポータル**(デスクトップ)。
* 360ビデオと最新の映画やテレビ番組を表示するための **ムービーとテレビ**
* すべての仮想アシスタントのニーズに対応する **Cortana**
* イマーシブヘッドセット内のデスクトップモニターを表示するための **デスクトップ**(イマーシブヘッドセット)
* **エクスプローラー** デバイスにあるファイルとフォルダーにアクセスする

## <a name="see-also"></a>関連項目
* [アプリ ビュー](../design/app-views.md)
* [モーション コントローラー](../design/motion-controllers.md)
* [ハードウェア アクセサリ](hardware-accessories.md)
* [HoloLens の環境への配慮](../environment-considerations-for-hololens.md)
* [3D アプリ起動ツールの実装](../distribute/implementing-3d-app-launchers.md)
* [Windows Mixed Reality ホームで使用するための3D モデルの作成](../distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
