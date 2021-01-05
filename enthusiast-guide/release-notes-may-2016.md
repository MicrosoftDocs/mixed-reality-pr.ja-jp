---
title: リリース ノート - 2016 年 5 月
description: Windows Holographic 5 月2016更新プログラムの HoloLens リリースノート。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, リリースノート, os, 機能, ビルド, プラットフォーム
ms.openlocfilehash: a1e5ab1ead2816baf2f03c1037299090e1246f17
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725953"
---
# <a name="release-notes---may-2016"></a>リリース ノート - 2016 年 5 月

HoloLens チームは、Windows Insider Program を通じて最新の機能更新プログラムとメジャー修正プログラムを提供することを約束しています。 ご意見をお寄せいただき、ありがとうございます。 フィードバックハブ、[開発者フォーラム](https://forums.hololens.com)、 [ @HoloLens および Twitter](https://twitter.com/hololens)を通じてフィードバックを引き続き[お](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback)寄せください。

**リリースバージョン:** Windows Holographic 5 月2016更新プログラム (**10.0.14342.1016**)

>[!VIDEO https://www.youtube.com/embed/XM5OHHrOGqQ]

現在のリリースに更新するには、 *設定* アプリを開き、[ *update & Security*] にアクセスして、[ *更新プログラムの確認* ] ボタンを選択します。

## <a name="new-features"></a>新機能

* **2d ビューで最大3個のアプリを同時に実行** できるようになりました。これにより、HoloLens でのマルチタスクの無限のユースケースが可能になります。 このフライトの新機能を確認しながら、クエストの一覧が表示された新しいフィードバックハブを用意してください。

  ![HoloLens では、3つのアプリを同時に実行できます。](images/img-3625-400px.jpg)<br>
  2D ビューで最大3個のアプリを同時に実行する

* 新しい **音声コマンド** を追加しました。
   * ホログラムを見て、"顔にする" という指示によって回転してみてください
   * "大きい" または "より小さい" を言い、サイズを変更します。
   * 「Cortana、 *アプリ名* をここに移動する」と言って、アプリを移動します。
* **HoloLens での開発が容易に** なりました。 [Windows デバイスポータル](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)を使用して、ファイルを参照、アップロード、およびダウンロードできるようになりました。 ドキュメントフォルダー、ピクチャフォルダー、および Visual Studio を使用してサイドロードまたは配置したすべてのアプリのローカルストレージにアクセスできます。
* エミュレーターでは、実際の HoloLens の場合と同じように、 **Microsoft アカウントでのログインがサポート** されるようになりました。これは、追加の [ツール] メニューから有効にすることができます。 ">>" です。
* **2D アプリはビデオの全画面を見ているときにアプリバーとカーソルを非表示にして、** 邪魔にならないようになりました。 HoloLens でビデオを視聴するエクスペリエンスがさらに楽しいものになります。
* また、世界中の **アプリバーなしで写真をピン留め** することもできます。

  ![アプリバーは、写真のような2D アプリでは非表示にすることができます。](images/img-3626-400px.jpg)<br>
  画像のような2D ビューを使用するアプリでは、アプリバーを非表示にすることができます。

* **ファイルピッカー** は、HoloLens での場合と同じように動作します。
* デスクトップと電話に統合されたユーザーエクスペリエンスをマップするように **Edge ブラウザー** を更新しました。 ブラウザーの複数のインスタンスを有効にし、カスタム HoloLens の新しいタブページ、タブのピーク、新しいウィンドウで開くことができるようになりました。さらに、power & のパフォーマンスが向上しています。
* 現在、 **Groove Music** アプリは HoloLens にあります。 ストアにアクセスしてダウンロードし、バックグラウンドで再生してみてください。
* アプリがどのように世界中に配置されるかを簡単にカスタマイズできます。 中央の垂直方向のワイヤーフレーム内の円をクリックしてドラッグするだけで、調整モードで **ホログラムを回転** してみてください。 最大の相互作用を実現するために、ホログラムの **境界ボックスが厳密に適合** していることがわかります。 すべてのフラットアプリのサイズを垂直方向に変更することもできます (写真とホログラムアプリを除く)。

  ![ホログラムは、世界中に配置した後に回転できます。](images/img-3627-400px.jpg)<br>
  自分の世界に配置した後に、ホログラムを回転させる

* このフライトでは、いくつかの **入力が改善** されました。 通常の Bluetooth マウスを HoloLens に接続できます。 Clicker は、clicker を使用したホログラムの移動 & サイズ変更を可能にするために微調整されています。 キーボードの動作もこれまでよりも優れています。
* 音量を同時に下げることによって、 **mixed reality の画像** を表示できるようになりました。 また、複数の現実にキャプチャされた写真 & ビデオを Facebook、Twitter、YouTube に共有することもできます。
* **Mixed reality ビデオ** の最大記録長が5分に増加しました。
* **写真アプリ** は、再生前にビデオ全体をダウンロードするのではなく、OneDrive からビデオをストリームするようになりました。
* ここ **では、ホログラムを** どのようにして残すかを改良しました。 また、Wi-Fi に再接続して、HoloLens がどこにいるかを検出できない場合に再試行するオプションも表示されます。
* キーボードでは、 **電子メールアドレスを入力するためのレイアウトが改善** されました。このキーを使用すると、1回のクリックで最も一般的な電子メールドメインを入力できます。
* 迅速な **アプリの登録** と、OOBE 中 **のタイムゾーンの自動検出** により、最初の最高のユーザーエクスペリエンスが提供されます。
* **ストレージの意味** では、設定アプリのシステムとアプリによって残りのディスク領域と使用されているディスク領域を表示できます。
* フィードバックアプリとハブの両方を1つのアプリ **フィードバックハブ** に集約しました。これは、気に入った機能に関する **フィードバックを提供** するための移行ツールであり、改善が必要な機能と、不要な機能を提供します。 Insider プログラムに参加すると、 **最新の insider news の入手**、評価の **ビルド** 、フィードバックハブからの **フィードバックのクエスト** に進むことができます。
* また [、更新された HoloLens エミュレーター](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools) ビルドも公開しました。
* ビデオの自動 **安定化** によって、mixed reality ビデオがより良くなりました。

## <a name="major-fixes"></a>主な修正

領域が低速であるか間違って検出された場合に、ホログラムスペースの問題を修正しました。 シャットダウン中にシェルの起動を引き続き試みる可能性があるシャットダウンの問題を修正しました。

問題を修正した
* これにより、XAML アプリケーションを再開する機能がブロックされます。
* クラッシュによって黒い画面といくつかのギザギザが発生します。
* 一部のアプリを使用すると、スクロールが間違った方向になることがあります。
* 電源 Led は、デバイスがまだオンになっているときにオフ状態であることを示している可能性があります。
* WiFi は、スタンバイから再開した後に無効になることがあります。
* Xbox id プロバイダーは、ゲーマータグのセットアップを提供し、ループ内でスタックします。
* OneDrive ファイルピッカーでダウンロードされたファイルを選択すると、シェルがクラッシュすることがあります。
* リンクを押したままにすると、新しいタブが開き、ショートカットメニューが表示されることがあります。
* windows デバイスポータルで50から80への IPD 調整が許可される場合

写真に関する問題を修正しています。
* "EXIF orientation" プロパティが無視されたため、画像が回転して表示されることがあります。
* ピン留めされた写真の起動時にクラッシュする可能性があります。
* 最後に一時停止した場所から続行するのではなく、一時停止後にビデオが再開されます。
* 共有ビデオが再生中に共有されていた場合、その動画の再生が回避される可能性があります。
* Mixed Reality キャプチャの記録は、オーディオのみのフィードが 0.5-1 秒で開始されます。
* OneDrive の初期同期中に [同期] ボタンが表示されなくなります。

設定に関する問題を修正しています。
* 環境が変更されたときに更新が必要でした。
* 一部のダイアログで [次へ] をクリックするのと同じように、キーボードの "Enter" は動作しません。
* clicker がペアリングに失敗したことを知るのは困難でした。
* WiFi の切断と接続によって応答しなくなる可能性があります。

Cortana の問題を修正しています。
* リッスンしている UI が表示されなくなる可能性があります。
* アプリを終了するための要求に対して "はい/いいえ" と回答した場合、排他モードアプリから "Cortana が何を言いましたか" という質問をすると、そのことが止まってしまいます。
* cortana にスリープ状態に移行してから再開すると、Cortana がリッスンする UI が正常に再開しません。
* "接続先のネットワークの種類" を照会します。 「接続していますか」という 最初のネットワークプロファイルが接続なしで復帰したときに失敗する可能性があります。
* アプリを終了すると、"聞き取り中" の UI froze はすぐに音声認識を開始します。
* Cortana アプリからサインアウトしても、再起動するまでサインインできません。
* 混合の現実のキャプチャ UI がアクティブであったときには起動しません。

Visual Studio での問題を修正しています。
* バックグラウンドタスクのデバッグが機能しませんでした。
* グラフィックスデバッガーのフレーム分析が機能しませんでした。
* プロジェクトの TargetPlatformVersion が10240に設定されていない限り、Visual Studio のドロップダウンリストに HoloLens エミュレーターが表示されませんでした。

## <a name="changes-from-previous-release"></a>以前のリリースからの変更
* Cortana コマンドは **cortana について、再起動** します。デバイスが動作しません。 ユーザーは、 **cortana、再起動** 、または **cortana について、デバイスを再起動** することができます。
* キオスクモードが製品から削除されました。

## <a name="prior-release-notes"></a>以前のリリースノート
* [リリース ノート - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>関連項目
* [HoloLens の既知の問題](https://docs.microsoft.com/windows/mixed-reality/hololens-known-issues)
* [ツールのインストール](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools)
* [Shell](https://docs.microsoft.com/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)
* [複合現実の 2D UWP アプリを更新する](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/building-2d-apps)
* [ハードウェア アクセサリ](https://docs.microsoft.com/windows/mixed-reality/discover/hardware-accessories)
* [複合現実キャプチャ](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-capture)
* [音声入力](https://docs.microsoft.com/windows/mixed-reality/design/voice-input)
* [Windows ストアへのアプリの送信](https://docs.microsoft.com/windows/mixed-reality/distribute/submitting-an-app-to-the-microsoft-store)
* [HoloLens エミュレーターを使用する](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-hololens-emulator)
