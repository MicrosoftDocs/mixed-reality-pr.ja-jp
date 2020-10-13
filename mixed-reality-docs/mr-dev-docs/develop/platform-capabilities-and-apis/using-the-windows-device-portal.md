---
title: Windows デバイス ポータルを使用する
description: HoloLens 用の Windows デバイス ポータルでは、Wi-Fi または USB 経由でリモートからデバイスを構成および管理できます。 デバイス ポータルは、お使いの PC に Web ブラウザーから接続することができる HoloLens 上の Web サーバーです。 デバイス ポータルには、HoloLens を管理し、アプリをデバッグおよび最適化するのに役立つ多くのツールが用意されています。
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: Windows デバイス ポータル, HoloLens
ms.localizationpriority: high
ms.openlocfilehash: 398b9ee312c8d49e3468980e5e2c1be556c17162
ms.sourcegitcommit: 252b52f7541a6e15aa33322286855af8a3924fc1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862991"
---
# <a name="using-the-windows-device-portal"></a>Windows デバイス ポータルを使用する

<table>
<tr>
<th>機能</th><th style="width:150px"><a href="../../hololens-hardware-details.md">HoloLens (第 1 世代)</a></th><th style="width:150px">HoloLens 2</th><th style="width:150px">
</tr><tr>
<td> Windows デバイス ポータル</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"></td>
</tr>
</table>

HoloLens 用の Windows デバイス ポータルでは、Wi-Fi または USB 経由でリモートからデバイスを構成および管理できます。 デバイス ポータルは、お使いの PC に Web ブラウザーから接続することができる HoloLens 上の Web サーバーです。 デバイス ポータルには、HoloLens を管理し、アプリをデバッグおよび最適化するのに役立つ多くのツールが用意されています。

このドキュメントは、特に HoloLens 用 Windows デバイス ポータルに関するものです。 デスクトップ用 Windows デバイス ポータル (Windows Mixed Reality 用を含みます) を使用するには、「[Windows Device Portal の概要](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal)」を参照してください

## <a name="setting-up-hololens-to-use-windows-device-portal"></a>Windows デバイス ポータルを使用するように HoloLens をセットアップする

1. HoloLens の電源を入れ、デバイスを装着します。
2. HoloLens 2 の[スタート ジェスチャ](https://docs.microsoft.com/hololens/hololens2-basic-usage#start-gesture) または HoloLens (第 1 世代) の[ブルーム](https://docs.microsoft.com/hololens/hololens1-basic-usage#open-the-start-menu-with-bloom)を実行して、メイン メニューを起動します。 
3. HoloLens (第 1 世代) では **[設定]** タイルを見つめて[エアタップ](https://docs.microsoft.com/hololens/hololens1-basic-usage#select-holograms-with-gaze-and-air-tap) ジェスチャを実行し、HoloLens 2 では[タッチするかハンド レイを使用](https://docs.microsoft.com/hololens/hololens2-basic-usage)してそれを選択します。 
4. **[Update]** (更新) メニュー項目を選択します。
5. **[For developers]** (開発者向け) メニュー項目を選択します。
6. **[Developer Mode]** (開発者モード) を有効にします。

> [!IMPORTANT]
> 管理者ではなく、マルチユーザーである場合は、開発者モードに入る機能が淡色表示されることがあります。自分が **[デバイスの管理者](https://docs.microsoft.com/hololens/security-adminless-os)** であることを確認してください。

7. [下へスクロール](../../design/gaze-and-commit.md#composite-gestures)し、**デバイス ポータル**を有効にします。
8. USB または Wi-Fi 経由でこの HoloLens にアプリを展開できるように Windows デバイス ポータルを設定している場合は、 **[ペアリング]** をクリックして、[ペアリング PIN を生成](using-visual-studio.md)します。 最初のデプロイ中に Visual Studio に PIN を入力するまで、設定アプリは PIN ポップアップのままにしておきます。

![Windows Holographic の設定アプリで開発者モードを有効にする](images/using-windows-portal-img-01.jpg)

## <a name="connecting-over-wi-fi"></a>Wi-Fi 経由で接続する

1. [HoloLens を Wi-Fi に接続します](../../connecting-to-wi-fi-on-hololens.md)。
2. 次のどちらかの方法でデバイスの IP アドレスを検索します。
   * **[設定] > [ネットワークとインターネット] > [Wi-Fi] > [詳細オプション]** の順に移動する。
   * **[設定] > [ネットワークとインターネット]** の順に移動し、 **[ハードウェアのプロパティ]** を選択する。

![HoloLens 2 の設定](images/using-windows-portal-img-02.jpg)

3. PC の Web ブラウザーで、 https://<HoloLens の IP アドレス> に移動します
   * ブラウザーに次のメッセージが表示されます。"この Web サイトのセキュリティ証明書には問題があります"。 これは、Device Portal に発行された証明書がテスト証明書であるためです。 ここでは、この証明書エラーを無視して続行できます。

## <a name="connecting-over-usb"></a>USB 経由で接続する

1. [ツールをインストール](../install-the-tools.md)して、USB 接続ができるように、PC に Visual Studio と Windows 10 開発者ツールを確実にインストールします。

> [!IMPORTANT]
> USB 接続に関する問題が発生した場合は、USB デバイス接続のオプション コンポーネントが **[Visual Studio ツール パッケージ](../install-the-tools.md#installation-checklist)** の一部としてインストールされていることを再確認します。

2. Hololens 用のマイクロ USB ケーブル (第 1 世代) または HoloLens 2 用の USB-C を使用して、HoloLens を PC に接続します。
3. PC の Web ブラウザーから、[https://127.0.0.1:10080](https://127.0.0.1:10080) にアクセスします。

### <a name="moving-files-over-usb"></a>USB 経由でファイルを移動する

追加の設定を行わずに、PC から HoloLens にファイルを移動することができます。
1. USB コードを使用して PC を HoloLens に接続します
2. ファイルをデスクトップ上の **PC\\[Your_HoloLens_Device_Name]\Internal Storage** にドラッグします
3. HoloLens で **[スタート]** メニューを開き、 **[すべてのアプリ] > [エクスプローラー]** の順に選択します

> [!NOTE]
> 場合によっては、[Recently used]\(最近の使用\) から移動してファイルを探すために、パネルの左側にある **[このデバイス]** を選択する必要があります。 

## <a name="connecting-to-an-emulator"></a>エミュレーターに接続する

Device Portal はエミュレーターで使うこともできます。 デバイス ポータルに接続するには、[ツール バー](using-the-hololens-emulator.md)を使用します。 次のアイコンをクリックします。![デバイス ポータルを開くアイコン](images/emulator-deviceportal.png) **デバイス ポータルを開く**: エミュレーターで HoloLens OS の Windows デバイス ポータルを開きます。

## <a name="creating-a-username-and-password"></a>ユーザー名とパスワードを作成する

![Windows デバイス ポータルへのアクセスを設定する](images/windows-device-portal-credentials-reset-page-1000px.png)<br>
*Windows デバイス ポータルへのアクセスを設定する*

HoloLens で初めて Device Portal に接続するときは、ユーザー名とパスワードを作成する必要があります。
1. PC 上の Web ブラウザーで、HoloLens の IP アドレスを入力します。 [Set up access] (アクセスのセットアップ) ページが開きます。
2. **[Request pin]\(PIN の要求\)** をクリックまたはタップし、生成された PIN を HoloLens のディスプレイで確認します。
3. **[PIN displayed on your device]\(デバイスに表示された PIN\)** テキスト ボックスに PIN を入力します。
4. Device Portal への接続に使うユーザー名を入力します。 Microsoft アカウント (MSA) 名やドメイン アカウント名を指定する必要はありません。
5. パスワードを入力し、確認用にもう一度入力します。 パスワードは 7 文字以上にする必要があります。 MSA やドメインのパスワードと同じにする必要はありません。
6. **[ペアリング]** をクリックして、HoloLens の Windows デバイス ポータルに接続します。

このユーザー名またはパスワードは、デバイスのセキュリティ ページでこの手順を繰り返すことでいつでも変更できます。デバイスのセキュリティ ページを表示するには、 https://<HoloLens の IP アドレス>/devicepair.htm にアクセスします。

## <a name="security-certificate"></a>セキュリティ証明書

ブラウザーで "証明書エラー" が表示される場合は、デバイスとの信頼関係を作成することで修正できます。

ぞれぞれの HoloLens では、SSL 接続用に一意の自己署名証明書が生成されます。 既定では、この証明書が PC の Web ブラウザーによって信頼されていないため、"証明書エラー" が発生することがあります。 この証明書を HoloLens から (USB または信頼している Wi-Fi ネットワーク経由で) ダウンロードし、PC で信頼すると、デバイスに安全に接続できます。
1. **安全なネットワーク (USB または信頼している Wi-Fi ネットワーク) に接続していることを確認します。**
2. デバイス ポータルの [セキュリティ] ページから、このデバイスの証明書をダウンロードします。
   * https://<HoloLens の IP アドレス>/devicepair.htm に移動します
   * [システム] > [基本設定] ノードを開きます。 
   * [デバイス セキュリティ] まで下にスクロールし、[Download this device's certificate]\(このデバイスの証明書をダウンロードする\) ボタンをクリックします。
3. 証明書を PC の "信頼されたルート証明機関" にインストールします。
   * Windows のメニューから、次のように入力します: Manage Computer Certificates and start the applet (コンピューターの証明書を管理し、アプレットを開始する)
   * **[信頼されたルート証明機関]** フォルダーを展開します。
   * **[証明書]** フォルダーをクリックします。
   * [操作] メニューから次を選択します: [すべてのタスク] > [インポート...]
   * Device Portal からダウンロードした証明書ファイルを使って、証明書のインポート ウィザードを完了します。
4. ブラウザーを再起動します。

>[!NOTE]
> この証明書はデバイスに対してのみ信頼されるため、デバイスがフラッシュされた場合、ユーザーはプロセスを再度実行する必要があります。


## <a name="device-portal-pages"></a>Device Portal のページ

### <a name="home"></a>ホーム

![Microsoft HoloLens の Windows デバイス ポータル ホーム ページ](images/using-windows-portal-img-04.png)<br>
*Microsoft HoloLens の Windows デバイス ポータル ホーム ページ*

Device Portal セッションは Home (ホーム) ページから始まります。 他のページにアクセスするには、ホーム ページの左側にあるナビゲーション バーを使います。

ページの最上部にあるツール バーでは、よく使われる状態や機能にアクセスできます。
* **オンライン**:デバイスが Wi-Fi に接続しているかどうかを示します。
* **[Shutdown]\(シャットダウン\)** : デバイスをオフにします。
* **[Restart]\(再起動\)** : デバイスの電源を入れ直します。
* **[Security]\(セキュリティ\)** : [デバイス セキュリティ] ページを開きます。
* **[Cool]\(クール\)** : デバイスの温度を示します。
* **[A/C]** : デバイスが電源に接続され、充電されているかどうかを示します。
* **[Help]\(ヘルプ\)** : REST インターフェイスのドキュメント ページを開きます。

ホーム ページには次の情報が表示されます。
* **[Device Status]\(デバイスの状態\):** デバイスの正常性を監視し、重大なエラーを報告します。
* **[Windows information]\(Windows の情報\):** HoloLens の名前と、現在インストールされている Windows のバージョンを表示します。
* **[Preferences]** (設定) セクションには次の設定が含まれます。
   * **[IPD]** : 瞳孔間距離 (IPD) を設定します。これは、ユーザーがまっすぐ前を向いたときの瞳孔の中心間の距離をミリメートル単位で示すものです。 設定はすぐに反映されます。 既定値は、デバイスのセットアップ時に自動的に計算された値です。
   * **[Device name]\(デバイス名\)** : HoloLens に名前を割り当てます。 この値を変更した場合、変更を有効にするにはデバイスを再起動する必要があります。 **[Save]\(保存\)** をクリックすると、デバイスを今すぐ再起動するか、後で再起動するかをたずねるダイアログが表示されます。
   * **[Sleep settings]\(スリープの設定\)** : デバイスが電源に接続されているときとバッテリで動作しているときの、スリープ状態に移行するまでの待ち時間の長さを設定します。

### <a name="3d-view"></a>3D View (3D ビュー)

![Microsoft HoloLens の Windows デバイス ポータルの [3D View]\(3D ビュー\) ページ](images/using-windows-portal-img-05.png)<br>
*Microsoft HoloLens の Windows デバイス ポータルの [3D View]\(3D ビュー\) ページ*

[3D View] (3D ビュー) ページを使うと、HoloLens がどのように周囲を解釈するかを確認できます。 ビュー内を移動するには、マウスを次のように使います。
* 回転: 左クリック + マウス
* パン: 右クリック + マウス
* ズーム: マウス スクロール
* **[Tracking options]\(追跡オプション\)**
   * **[Force visual tracking]\(視覚追跡を強制\)** をオンにすると、連続的な視覚追跡が有効になります。 
   * **[Pause]\(一時停止\)** : 視覚追跡を停止します。
* **[View options]\(表示オプション\)** : 3D ビューのオプションを設定します。
  * **[Tracking]\(追跡\)** : 視覚追跡がアクティブかどうかを示します。
  * **[Show floor]\(フロアを表示\)** : チェック模様のフロア平面を表示します。
  * **[Show frustum]\(視錐台を表示\)** : 視錐台を表示します。
  * **[Show stabilization plane]\(手ブレ補正平面を表示\)** : HoloLens でモーションの手ブレ補正用に使われる平面を表示します。
  * **[Show mesh]\(メッシュを表示\)** : 周囲を表す空間マッピング メッシュを表示します。
  * **[Show spatial anchors]\(空間アンカーを表示\)** : アクティブなアプリの空間アンカーを表示します。 アンカーを取得して更新するには、[Update]\(更新\) ボタンをクリックする必要があります。
  * **[Show details]\(詳細を表示)** : 手の位置、頭部の回転の四元数、デバイスの原点のベクトルを、動きに合わせてリアルタイムで表示します。
  * **[Full screen]\(全画面表示\)** ボタン: 3D ビューを全画面表示モードで表示します。 Esc キーを押すと全画面表示を終了します。
* **[Surface reconstruction]\(サーフェスの認識\)** : **[Update]\(更新\)** をクリックまたはタップすると、デバイスから最新の空間マッピング メッシュを表示します。 全体の処理が完了するまでには、しばらくかかる可能性があります (最大で数秒)。 3D ビューではメッシュは自動的に更新されないため、デバイスから最新のメッシュを取得するには、手動で **[Update]\(更新\)** をクリックする必要があります。 **[Save]\(保存\)** をクリックすると、現在の空間マッピング メッシュを obj ファイルとして PC に保存します。
* **[Spatial anchors]\(空間アンカー\)** : アクティブなアプリの空間アンカーを表示または更新するには、[Update]\(更新\) をクリックします。

### <a name="map-manager"></a>Map Manager

Map Manager を使用すると、複数のデバイス間でマップを共有できます。これによって、場所に基づいたエンターテインメントの顧客に共有エクスペリエンスを設定できます。 このツールでは、システム マップおよびアンカーのインポートとエクスポートもできます。  

Map Manager にアクセスするには、デバイス ポータルにログインし、 **[Mixed Reality] -> [Map Manager]** の順に選択します。 

![Windows デバイス ポータルの [Map Manager] ページ](images/using-windows-portal-img-06.png)
*Microsoft HoloLens 上の Windows デバイス ポータルの [Map Manager] ページ*

#### <a name="exporting-and-importing-maps"></a>マップをエクスポートおよびインポートする

マップをエクスポートするには、 **[Export System Map & Anchors]\(システム マップとアンカーのエクスポート\)** をクリックします。 この処理には時間がかかることがあります。マップがエクスポートされている間、30 から 60 秒間待機します。 完了すると、ブラウザーにファイルがダウンロードされます。  

マップとアンカーをインポートするには、 **[Upload a map file]\(マップ ファイルのアップロード\)** と **[Upload an anchor file]\(アンカー ファイルのアップロード\)** をそれぞれクリックし、エクスポート済みのマップ ファイルまたはアンカー ファイルを選択します。 アップロードされたマップ ファイルまたはアンカー ファイルは、自分の HoloLens デバイスからのものである場合も、他の HoloLens デバイスからのものである場合もあります。 

> [!NOTE]
> HoloLens では、空間マッピング データベースをインポートおよびエクスポートすることもできます。 ただし、これは非 HoloLens デバイスでは機能しません。  


### <a name="mixed-reality-capture"></a>Mixed Reality キャプチャ

![Microsoft HoloLens の Windows デバイス ポータルの [Mixed Reality Capture]\(Mixed Reality キャプチャ\) ページ](images/using-windows-portal-img-07.png)<br>
*Microsoft HoloLens の Windows デバイス ポータルの [Mixed Reality Capture]\(Mixed Reality キャプチャ\) ページ*

Mixed Reality キャプチャ ページを使うと、HoloLens からメディア ストリームを保存できます。
* **キャプチャの設定**:次の設定をオンにすることにより、キャプチャされるメディア ストリームを制御します。
  * **[Holograms]\(ホログラム\)** : ビデオ ストリームのホログラフィック コンテンツをキャプチャします。 ホログラムは、ステレオではなくモノラルでレンダリングされます。
  * **[PV camera]\(PV カメラ\)** : 写真やビデオ カメラからビデオ ストリームをキャプチャします。
  * **[Mic Audio]\(マイク オーディオ\)** : マイク配列からオーディオをキャプチャします。
  * **[App Audio]\(アプリ オーディオ\)** : 現在実行中のアプリからオーディオをキャプチャします。
  * **[Render from Camera]\(カメラからのレンダリング\)** : [実行中のアプリでサポートされている](mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)場合、写真やビデオ カメラのパースペクティブにキャプチャを配置します (HoloLens 2 のみ)。
  * **[Live preview quality]\(ライブ プレビューの品質\)** : ライブ プレビューの画面解像度、フレーム レート、ストリーミング レートを選択します。
* **オーディオ設定** (HoloLens 2 のみ):
  * **オーディオ メディア カテゴリ**:マイクの処理時に使用するカテゴリを選択します。 **[既定]** には一部の環境が含まれており、 **[通信]** はバックグラウンド ノイズ キャンセルを適用します。
  * **アプリ オーディオ ゲイン**:アプリ オーディオのボリュームに適用されるゲイン。
  * **マイク オーディオ ゲイン**:マイク オーディオのボリュームに適用されるゲイン。
* **写真とビデオの設定** (HoloLens 2、バージョン 2004 以降):
  * **キャプチャ プロファイル**:写真やビデオを撮影するときに使用するプロファイルを選択します。 プロファイルによって、使用可能な解像度とフレームレートが決まります。
  * **写真の解像度**:写真の撮影に使用される解像度。
  * **ビデオ解像度とフレームレート**:ビデオの再生に使用される解像度とフレームレート。
  * **ビデオ手ブレ補正バッファー**:ビデオを撮影するときに使用するバッファー サイズ。 値が大きいほど、速い動きをより適切に補正できます。
* **[Live preview]\(ライブ プレビュー\)** ボタンをクリックまたはタップすると、キャプチャ ストリームを表示します。 **[Stop live preview]\(ライブ プレビューの停止\)** は、キャプチャ ストリームを停止します。
* **[Record]\(記録\)** をクリックまたはタップすると、指定された設定を使って Mixed Reality ストリームのレコーディングを開始します。 **[Stop recording]\(記録の終了\)** は、レコーディングを終了して保存します。
* **[Take photo]\(写真の撮影\)** をクリックまたはタップすると、キャプチャ ストリームから静止画像を取得します。
* **[既定の設定を復元する]** をクリックまたはタップして、オーディオ、写真、ビデオの設定をデフォルト設定に復元します。
* **[Videos and photos]\(ビデオと写真\)** : デバイスで取得されたビデオと写真のキャプチャの一覧を表示します。

このページのすべての設定は、Windows デバイス ポータルを使用して取得したキャプチャに適用されますが、一部はシステム MRC (スタート メニュー、ハードウェア ボタン、グローバル ボイス コマンド、Miracast) およびカスタム MRC レコーダーにも適用されます。

|  設定  |  システム MRC に適用されます  |  カスタム MRC レコーダーに適用されます |
|----------|----------|----------|
|  ホログラム  |  いいえ  |  いいえ |
|  PV カメラ  |  いいえ  |  いいえ |
|  マイク オーディオ  |  いいえ  |  いいえ |
|  アプリ オーディオ  |  いいえ  |  いいえ |
|  カメラからのレンダリング  |  はい    |  はい (オーバーライド可能) |
|  ライブ プレビューの品質  |  いいえ  |  いいえ |
|  オーディオ メディア カテゴリ  |  はい  |  いいえ |
|  アプリ オーディオ ゲイン  |  はい  |  はい (オーバーライド可能) |
|  マイク オーディオ ゲイン  |  はい  |  はい (オーバーライド可能) |
|  キャプチャ プロファイル  |  はい  |  いいえ |
|  写真の解像度  |  はい  |  いいえ |
|  ビデオ解像度とフレームレート  |  はい  |  いいえ |
|  ビデオ手ブレ補正バッファー  |  はい  |  はい (オーバーライド可能) |

> [!NOTE]
> [同時に MRC には制限事項](mixed-reality-capture-for-developers.md#simultaneous-mrc-limitations)があります。
> * Windows デバイス ポータルがビデオを記録しているときに、アプリが写真やビデオ カメラにアクセスしようとすると、ビデオの記録が停止します。
>   * HoloLens 2 では、アプリが SharedReadOnly モードで写真やビデオ カメラにアクセスした場合、ビデオの記録は停止されません。
> * アプリで写真やビデオ カメラがアクティブに使用されている場合、Windows デバイス ポータルで写真を撮影したり、ビデオを録画したりすることができます。
> * ライブ ストリーミング:
>   * HoloLens (第 1 世代) では、Windows デバイス ポータルからのライブ ストリーミング中に、アプリで写真やビデオ カメラにアクセスすることはできません。
>   * アプリで写真やビデオ カメラがアクティブに使用されている場合、HoloLens (第 1 世代) のライブ ストリームは失敗します。
>   * HoloLens 2 では、アプリが ExclusiveControl モードで写真やビデオ カメラにアクセスしようとすると、ライブ ストリーミングが自動的に停止されます。
>   * HoloLens 2 では、アプリで PV カメラがアクティブに使用されている間に、ライブ ストリームを開始できます。

### <a name="performance-tracing"></a>パフォーマンス トレース

![Microsoft HoloLens の Windows デバイス ポータルの [Performance Tracing]\(パフォーマンス トレース\) ページ](images/using-windows-portal-img-08.png)<br>
*Microsoft HoloLens の Windows デバイス ポータルの [Performance Tracing]\(パフォーマンス トレース\) ページ*

[Windows Performance Recorder](https://msdn.microsoft.com/library/windows/hardware/hh448205.aspx) (WPR) のトレースを HoloLens からキャプチャします。
* **[Available profiles]\(利用可能なプロファイル\)** : ドロップダウン リストから WPR プロファイルを選択し、 **[Start]\(開始\)** をクリックまたはタップすると、トレースを開始できます。
* **[Custom profiles]\(カスタム プロファイル\)** : **[Browse]\(参照\)** をクリックまたはタップして、PC から WPR プロファイルを選択します。 **[Upload and start]** (アップロードして開始) をクリックまたはタップすると、トレースが開始します。

トレースを停止するには、停止リンクをクリックします。 トレース ファイルのダウンロードが完了するまで、このページを閉じないでください。

キャプチャした ETL ファイルは、[Windows Performance Analyzer](https://msdn.microsoft.com/library/windows/hardware/hh448170.aspx) で開いて分析に使用できます。

### <a name="processes"></a>プロセス

![Microsoft HoloLens の Windows デバイス ポータルの [Processes]\(プロセス\) ページ](images/using-windows-portal-img-09.png)<br>
*Microsoft HoloLens の Windows デバイス ポータルの [Processes]\(プロセス\) ページ*

現在実行中のプロセスに関する詳細を表示します。 これには、アプリとシステムの両方のプロセスが含まれます。

### <a name="system-performance"></a>System Performance (システム パフォーマンス)

![Microsoft HoloLens の Windows デバイス ポータルの [System Performance]\(システム パフォーマンス\) ページ](images/using-windows-portal-img-10.png)<br>
*Microsoft HoloLens の Windows デバイス ポータルの [System Performance]\(システム パフォーマンス\) ページ*

電力消費、フレーム レート、CPU 負荷など、システムの診断情報のグラフをリアルタイムで表示します。

利用可能なメトリックを次に示します。
* **[SoC power]\(SoC 電力\)** : System on a Chip の瞬間的な電力使用量 (1 秒あたりの平均)
* **[System power]\(システム電力\)** : システムの瞬間的な電力使用量 (1 秒あたりの平均)
* **[Frame rate]\(フレーム レート\)** : 1 秒あたりのフレーム数、1 秒あたりに失敗した VBlank 数、連続で失敗した VBlank 数
* **[GPU]** : GPU エンジンの使用率、使用可能量の合計に対するパーセント
* **CPU**: 使用可能量の合計に対するパーセント
* **[I/O]** : 読み取りと書き込み
* **ネットワーク**:受信と送信
* **[Memory]\(メモリ\)** : 合計メモリ、使用中のメモリ、コミット メモリ、ページ メモリ、および非ページ メモリ

### <a name="apps"></a>アプリ

![Microsoft HoloLens の Windows デバイス ポータルの [Apps]\(アプリ\) ページ](images/using-windows-portal-img-11.png)<br>
*Microsoft HoloLens の Windows デバイス ポータルの [Apps]\(アプリ\) ページ*

HoloLens にインストールされているアプリを管理します。
* **[Installed apps]\(インストール済みのアプリ\)** : アプリを削除および起動します。
* **[Running apps]\(実行中のアプリ\)** : 現在実行されているアプリを一覧表示します。
* **[Install app]\(アプリのインストール\)** : コンピューターまたはネットワーク上のフォルダーからインストールするアプリ パッケージを選択します。
* **[Dependency]\(依存関係\)** : インストールするアプリの依存関係を追加します。
* **[Deploy]\(展開\)** : 選択したアプリと依存関係を HoloLens に展開します。

### <a name="app-crash-dumps"></a>App Crash Dumps (アプリのクラッシュ ダンプ)

![Microsoft HoloLens の Windows デバイス ポータルの [App Crash Dumps]\(アプリのクラッシュ ダンプ\) ページ](images/using-windows-portal-img-12.png)<br>
*Microsoft HoloLens の Windows デバイス ポータルの [App Crash Dumps]\(アプリのクラッシュ ダンプ\) ページ*

このページでは、サイドローディングしたアプリのクラッシュ ダンプを収集できます。 クラッシュ ダンプを収集する各アプリについて、 **[Crash Dumps Enabled]\(クラッシュ ダンプ有効\)** チェック ボックスをオンにします。 後でこのページに戻ると、クラッシュ ダンプが収集されています。 ダンプ ファイルは、[デバッグ用に Visual Studio で開く](https://msdn.microsoft.com/library/d5zhxt22.aspx)ことができます。

### <a name="file-explorer"></a>エクスプローラー

![Microsoft HoloLens の Windows デバイス ポータルの [File Explorer]\(ファイル エクスプローラー\) ページ](images/using-windows-portal-img-13.png)<br>
*Microsoft HoloLens の Windows デバイス ポータルの [File Explorer]\(ファイル エクスプローラー\) ページ*

ファイルを参照、アップロード、ダウンロードするには、ファイル エクスプローラーを使用します。 ドキュメント フォルダー、ピクチャ フォルダー、および Visual Studio やデバイス ポータルから展開されたアプリ用のローカル ストレージ フォルダー内のファイルを操作できます。

### <a name="kiosk-mode"></a>キオスク モード

>[!NOTE]
>キオスク モードは、[Microsoft HoloLens Commercial Suite](../../commercial-features.md) でのみ使用できます。

![Microsoft HoloLens 上の Windows デバイス ポータルのキオスク モード ページ](images/using-windows-portal-img-14.png)

Windows デバイス ポータルを使用してキオスク モードを有効にするための最新の手順については、Windows IT Pro Center の「[キオスク モードでの HoloLens のセットアップ](https://docs.microsoft.com/hololens/hololens-kiosk#set-up-kiosk-mode-using-the-windows-device-portal-windows-10-version-1607-and-version-1803)」記事を参照してください。

### <a name="logging"></a>ログ記録

![Microsoft HoloLens の Windows デバイス ポータルの [Logging]\(ログ記録\) ページ](images/using-windows-portal-img-15.png)<br>
*Microsoft HoloLens の Windows デバイス ポータルの [Logging]\(ログ記録\) ページ*

HoloLens 上の Windows イベント トレーシング (ETW) をリアルタイムで管理します。

**[Hide Providers]\(プロバイダを非表示にする\)** チェックボックスをオンにすると、 **[Events]\(イベント\)** の一覧のみが表示されます。
* **[Registered providers]\(登録済みプロバイダー\)** : ETW プロバイダーとトレース レベルを選択します。 トレース レベルは次のいずれかの値になります。
   1. 異常終了または終了
   2. 重大なエラー
   3. 警告
   4. エラーではない警告

トレースを開始するには、 **[Enable]** (有効にする) をクリックまたはタップします。 **[Enabled Providers]** (有効なプロバイダー) ドロップダウン リストにプロバイダーが追加されます。
* **[Custom providers]\(カスタム プロバイダー\)** : カスタム ETW プロバイダーとトレース レベルを選択します。 GUID を使用してプロバイダーを識別します。 GUID にはかっこを含めないでください。
* **[Enabled providers]\(有効なプロバイダー\)** : 有効なプロバイダーを一覧表示します。 ドロップダウンからプロバイダーを選択し、 **[Disable]** (無効にする) をクリックまたはタップしてトレースを停止します。 すべてのトレースを中断するには、 **[Stop All]** (すべて停止) をクリックまたはタップします。
* **[Providers history]\(プロバイダー履歴\)** : 現在のセッション中に有効になった ETW プロバイダーを表示します。 無効になっているプロバイダーをアクティブ化するには、 **[Enable]** (有効にする) をクリックまたはタップします。 履歴をクリアするには、 **[Clear]** (クリア) をクリックまたはタップします。
* **[Events]\(イベント\)** : 選択したプロバイダーの ETW イベントを表形式で一覧表示します。 この表は、リアルタイムで更新されます。 すべての ETW イベントを表から削除するには、表の下にある **[Clear]** (クリア) ボタンをクリックします。 これによってプロバイダーが無効になることはありません。 **[Save to file]** (ファイルに保存) をクリックすると、現在収集されている ETW イベントをローカルの CSV ファイルにエクスポートできます。
* **[Filters]\(フィルター\)** : 収集された ETW イベントを、ID、キーワード、レベル、プロバイダー名、タスク名、またはテキストでフィルター処理できます。 複数の条件を組み合わせることができます。
   1. 同じプロパティに適用する条件では、これらの条件のいずれかを満たすことができるイベントが表示されます。
   2. 異なるプロパティに適用する条件では、イベントはすべての条件を満たしている必要があります

たとえば、 *(Task Name contains 'Foo' or 'Bar') AND (Text contains 'error' or 'warning')* のような条件を指定できます

### <a name="simulation"></a>シミュレーション

![Microsoft HoloLens の Windows デバイス ポータルの [Simulation]\(シミュレーション\) ページ](images/using-windows-portal-img-16.png)<br>
*Microsoft HoloLens の Windows デバイス ポータルの [Simulation]\(シミュレーション\) ページ*

テスト用に入力データを記録して再生できます。
* **[Capture room]\(ルームのキャプチャ\)** : シミュレートされたルーム ファイルをダウンロードするために使います。このファイルには、ユーザーの周囲の空間マッピング メッシュが含まれます。 ルームに名前を付けて **[Capture]\(キャプチャ\)** をクリックすると、データが .xef ファイルとして PC に保存されます。 このルーム ファイルは、HoloLens エミュレーターに読み込むことができます。
* **[Recording]\(記録\)** : レコーディングを開始します。記録するストリームをオンにし、レコーディングに名前を付けて、 **[Record]\(記録\)** をクリックまたはタップします。 HoloLens でアクションを実行した後、 **[Stop]\(停止\)** をクリックすると、データが .xef ファイルとして PC に保存されます。 このファイルは、HoloLens エミュレーターまたはデバイスで読み込むことができます。
* **[Playback]\(再生\)** : **[Upload recording]\(記録のアップロード\)** をクリックまたはタップし、PC から xef ファイルを選択して、そのデータを HoloLens に送信します。
* **[Control mode]\(制御モード\)** : HoloLens のモードを選択します。ドロップダウンから **[Default]\(既定\)** または **[Simulation]\(シミュレーション\)** を選択し、 **[Set]\(設定\)** ボタンをクリックまたはタップします。 [Simulation] (シミュレーション) を選ぶと、HoloLens の実際のセンサーは無効になり、アップロードされたシミュレーション データが代わりに使われます。 [Simulation] (シミュレーション) に切り替えると、[Default] (既定) に戻すまで、HoloLens は実際のユーザーに応答しなくなります。

### <a name="networking"></a>ネットワーク

![Microsoft HoloLens の Windows デバイス ポータルの [Networking]\(ネットワーク\) ページ](images/using-windows-portal-img-17.png)<br>
*Microsoft HoloLens の Windows デバイス ポータルの [Networking]\(ネットワーク\) ページ*

HoloLens での Wi-Fi 接続を管理します。
* **[WiFi adapters]\(Wi-Fi アダプター\)** : ドロップダウン コントロールを使用して、Wi-Fi アダプターとプロファイルを選択します。 選択したアダプターを使用するには、 **[Connect]\(接続\)** をクリックまたはタップします。
* **[Available networks]\(使用可能なネットワーク\)** : HoloLens が接続できる Wi-Fi ネットワークの一覧が表示されます。 一覧を更新するには、 **[Refresh]\(最新の情報に更新\)** をクリックします。
* **[IP configuration]\(IP 構成\)** : ネットワーク接続の IP アドレスとその他の詳細が表示されます。

### <a name="virtual-input"></a>Virtual Input (仮想入力)

![Microsoft HoloLens の Windows デバイス ポータルの [Virtual Input]\(仮想入力\) ページ](images/using-windows-portal-img-18.png)<br>
*Microsoft HoloLens の Windows デバイス ポータルの [Virtual Input]\(仮想入力\) ページ*

リモート コンピューターから HoloLens にキーボード入力を送信します。

**[Virtual keyboard]\(仮想キーボード\)** の下にある領域をクリックまたはタップすると、HoloLens にキー入力を送信できるようになります。 **[Input text]\(テキストの入力\)** テキスト ボックスに入力し、 **[Send]\(送信\)** をクリックまたはタップすると、アクティブなアプリにキー入力が送信されます。

## <a name="device-portal-rest-apis"></a>Device Portal REST API

デバイス ポータルの機能はすべて、[REST API](device-portal-api-reference.md) の上に構築されています。REST API は、必要に応じて、プログラムからデータにアクセスしてデバイスを制御するために使用できます。
