---
title: ヘッドセットの Faq を表示する
description: Windows Mixed Reality の表示ヘッドセットのトラブルシューティングでは、標準のコンシューマーサポートドキュメントを超える問題が表示されます。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート
appliesto:
- Windows 10
ms.openlocfilehash: 6bcd6db30bf3a8a6e69d45c10be523d45ee4f82a
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725413"
---
# <a name="headset-display-faqs"></a>ヘッドセットの Faq を表示する

## <a name="my-headset-displays-are-black"></a>ヘッドセットの表示が黒くなっている

* PC のパフォーマンスと安定性を確認します。
    * タスクマネージャーを使用して、PC の CPU、GPU、またはディスクドライブをアウトしているプロセスがあるかどうかを確認します。
    * **Windows ログ > イベントビューアー** の "アプリケーション" と "システム" ログを確認して、アプリがクラッシュして WINDOWS エラー報告 (WER) レポートを生成しているかどうかを確認します。
    * Windows Update を確認して、Windows のバージョンが最新であることを確認します。 [更新プログラムの確認] を複数回選択することが必要になる場合があります。
* アプリとゲームの安定性を確認します。
    * PC が、正常に実行されていないアプリまたはゲームの最小システム要件を満たしていることを確認します。
    * GPU ドライバーのバージョンが最新であることを確認し、新しいドライバーのパフォーマンスと互換性に関する新しい問題と回帰を確認してください。
    * SteamVR アプリとゲームを使用している場合は、steamvr と SteamVR コンポーネント用の Windows Mixed Reality が最新の状態であることを確認してください。
* HDMI アダプターの互換性を確認します。
    * HDMI ケーブルがすべての方法で接続されていることを確認します。
    * HDMI アダプター (たとえば、ミニ DisplayPort から HDMI アダプター) を使用している場合は、Windows Mixed Reality と互換性があることを確認してください。 アダプターは HDMI 2.0 をサポートする必要があり、1080p のみをサポートする古いアダプターが多数存在します。 [Windows Mixed Reality の推奨されるアダプターを](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)参照してください。
    * プラグの順序は重要です。 アダプタにヘッドセットを接続する前に、PC に HDMI アダプタを接続します (特に USB-C から HDMI アダプタを使用している場合)。
    * 拡張機能ケーブルを使用している場合は、削除してみてください。
* グラフィックスカードとドライバーの互換性を確認します。
    * Pc モニターで PC の HDMI ポートを試してみてください。 Pc によっては、複数の HDMI ポートが使用されている場合があり、それらのすべてがアクティブになっているわけではありません。
    * PC に統合グラフィックスプロセッシングユニット (iGPU) と離散グラフィックスプロセッシングユニット (dGPU) が搭載されている場合は、dGPU の HDMI ポートに接続していることを確認します。
    * GPU ドライバーのバージョンをもう一度確認します。 最新のものであることを確認してください。ただし、新しいドライバーのパフォーマンスや互換性に関する新しい問題や回帰にも注目してください。
    * ラップトップで Mixed Reality を使用していて、グラフィックスカードの製造元の web サイトから新しいグラフィックドライバーをインストールしている場合は、PC 製造元の web サイトまたは Windows Update で提供されている最新のグラフィックスカードドライバーにダウングレードしてみてください。
    * PC に複数の pc モニターが接続されている場合は、1台の PC モニター以外は一時的に切断してみてください。
    * PC モニターのカスタムリフレッシュレートを設定している場合は、60 Hz などの標準のリフレッシュレートに一時的に戻してみてください。
    * 最近、Windows を再インストールせずにグラフィックスカードを変更した場合は、ヘッドセットモニターに正しいドライバーがインストールされていることを確認してください。 ヘッドセットを接続した状態で、"Mixed Reality ヘッドセット" がデバイスマネージャーの [モニター] ノードの下に一覧表示されていることを確認します。
    * PC に Nvidia グラフィックスカードがある場合は、Nvidia の3D ビジョンソフトウェアが無効になっていることを確認します。
    * 一部のグラフィックスカード (特に古いカード) では、hdmi ポートが HDMI 2.0 をサポートしていないか、Windows Mixed Reality と完全に互換性がない可能性があります。 グラフィックスカードの DisplayPort を [DisplayPort 1.2 から HDMI 2.0 アダプター](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)に使用してみてください。
    * Hp 製品番号が 1RJ99EA # アブダビの HP Omen Pc には、Windows Mixed Reality と互換性のない HDMI ポートがあります ("HP Support Assistant" を開き、この番号はアプリの下部に表示されます)。
    * PC に AMD R9 シリーズグラフィックスカードが搭載されており、Samsung Mixed Reality ヘッドセットを使用している場合は、ヘッドホンのファームウェアを1.0.8 以降のバージョンに更新して、ヘッドセットでグラフィックスカードの HDMI ポートを使用します。
    * Surface Book 2 を使用している場合は、 [SURFACE USB-C を HDMI アダプターに](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)使用していることを確認してください。
* Mixed Reality ヘッドセットハードウェアの問題を確認します。
    * ヘッドセットのハードウェアの問題を確認または除外するには、Mixed Reality ヘッドセットを別の PC に接続します。
    * 症状が似ているため、最初に PC の互換性とセットアップの問題を確認します。
* USB ケーブルが USB 3.0 または高速ポートに接続されていることを確認します。 USB 3.0 ポートの横には SS (超高速) があり、多くの場合、青で色分けされています。

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>使用したヘッドセットの表示が黒に変わることがある

* PC で USB 一時停止機能または省電力機能を無効にしてみてください。 たとえば、[ **設定 > システム > 電源 & スリープ > [USB セレクティブサスペンド](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-selective-suspend)**] では、[コンピューターがこのデバイスの電源をオフにして電源を入れることを許可する] デバイスマネージャー設定と、PC のファームウェアで usb 省電力設定を使用できるようにします。
* PC に接続されている他の USB デバイスと周辺機器を一時的に切断します。
* GPU ドライバーのバージョンが最新であることを確認し、新しいドライバーのパフォーマンスと互換性に関する新しい問題と回帰を確認します。

## <a name="one-of-the-displays-on-my-headset-is-black"></a>ヘッドセットの表示の1つが黒です

* HDMI アダプターを使用している場合は、HDMI 2.0 がサポートされていることを確認します。
* 使用している可能性がある USB および HDMI 拡張ケーブルをすべて削除します。
* グラフィックスドライバーが最新であることを確認します。
* 別の PC で Mixed Reality ヘッドセットを試してみてください。

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-reinitializes"></a>ヘッドセットが青色に変わり、Mixed Reality ポータルが再初期化される

これは通常、PC で USB コントローラーの信頼性の問題がときどき発生することを示します。

* 別の USB ポートを試してください。 PC に複数の USB 3.0 コントローラーがある場合があります。
* 拡張ケーブル (該当する場合) をすべて削除します。
* PC から他のすべての USB デバイスを取り外します。
* 外部から供給される USB 3.0 ハブを PC に接続し、ヘッドセットをハブに接続します。
* デスクトップ PC を使用している場合は、USB 3.0 PCIe カードを購入して、PC に別の USB コントローラーを追加することを検討してください。

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>ヘッドセットによって PC がハングしたり、起動中に黒い画面が表示される

Pc によっては、ヘッドセットの電源を入れたままにしておくか、PC を再起動すると起動プロセスが妨げられることがあります。 PC では、ヘッドセットが "プライマリモニター" として表示され、PC の起動が正常に開始されていないこと、正常に起動していないこと、または "ハング" が発生したか、ビープ音エラーコードが生成されたこと 動作は、PC の製造元とモデル、またはグラフィックスカードの製造元とモデルによって異なります。 この問題を解決するには:

* ヘッドセットをグラフィックスカードの別のポートに接続します (他のポートを使用するには、アダプターを使用する必要がある場合があります)。
* PC の BIOS/UEFI ファームウェアが最新の状態であることを確認します (ただし、快適な場合は、PC の BIOS/UEFI ファームウェアのみを更新してください)。

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Surface PC を使用すると、PC またはヘッドセットにちらつき、フラッシュ、または黒が表示される

* HDMI 2.0 をサポートする HDMI アダプターを使用していることを確認します。 古い HDMI アダプターの多くは1080p 解像度のみをサポートしています。これは、Mixed Reality ヘッドセットには不十分です。
* グラフィックスドライバーが最新であることを確認します。 Windows Update と PC 製造元の web サイトで、更新されたグラフィックスドライバーを確認します。
* 一部の Surface デバイスは、Windows Mixed Reality と互換性がありません。 詳細については [、Surface の互換性と要件](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)に関するページを参照してください。

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>シャットダウンして高速スタートアップを実行した後、自分のヘッドセットの表示が機能しない

ヘッドセットから HDMI ケーブルと USB ケーブルを取り外し、再び接続します。

## <a name="my-headset-displays-are-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>ヘッドセットの表示が途切れていますが、Mixed Reality ポータルのプレビューウィンドウが正常に表示されます

* PC のシステムリソース (CPU、メモリ、およびハードドライブ) が使用可能であり、別のアプリまたはプロセスで使用されていないことを確認します。
* グラフィックスドライバーを更新します。

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>"インストールクラスが存在しないか、無効です" というエラーが表示されるデバイスマネージャー

デバイスマネージャーに黄色の感嘆符が付いた "HoloLens センサー" が表示されている場合は、詳細についてデバイスを選択します。 "このデバイスのドライバーはインストールされていません。 (コード 28)--インストールクラスが存在しないか、無効です。通常、これは PC が [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017)を実行していることが原因です。Windows 10 のエディションでは、Windows Mixed Reality がサポートされていないため、Windows 10 の N 以外のバージョンをインストールする必要があります。

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>頭を移動してダブルビジョンを表示すると、自分の WMR 環境がちらつく、または stutters

グラフィックスと Nvidia GPU が統合されたノート pc では、前のフレームが次のフレームの後に表示されるように見える期間が経過するとエラーが発生します。これにより、ダブルビジョンにより、ヨー、ピッチ、またはロールの移動で頭を移動する速度が向上します。 Nvidia グラフィックスドライバー436.48 以降のドライバーで問題が発生しているようです。  このドライバーをインストールすると、Nvidia が更新されたドライバーの問題を解決するまで、問題が解決されます。 Nvidia グラフィックスドライバー436.48 を直接インストールする場合は、 [nvidia](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us)にアクセスしてください。

## <a name="im-uncomfortable-in-my-headset"></a>ヘッドセットで不快を感じています

Windows Mixed Reality の快適さに関する一般情報については、「 [Windows Mixed reality イマーシブヘッドセットの正常性、安全性、および快適](wmr-health-safety-comfort.md)さ」を参照してください。 特定のヘッドセットの詳細については、ヘッドセットの製造元に確認してください。

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>ヘッドセットでより明確なビューを取得する方法はありますか

ヘッドセットの調整を試してみてください。 顔を上下に移動するか、ストラップを調整して snug を感じます。

ヘッドセットに調整を調整するノブがある場合は、調整設定を調整します。 表示されていない場合は、[設定] にアクセスして **> Mixed reality > 画質** を調整し、調整を調整します。 特定のデバイスの調整の詳細については、ヘッドセットの製造元に確認してください。

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>ヘッドセットのビューの周囲に黒い境界線が表示されることがよくあります。 トンネルを探しているように見えることがあります。

これは、アプリケーションが PC 上のフレームレートに到達できず、システムが古いフレームを使用してヘッドセットにビューを表示していることを意味します。 アプリケーションでは、表示している世界の一部だけがレンダリングされるため、フレームレートに常に達していない場合、システムは前のビューから世界を表示しようとし、不足している詳細を黒で塗りつぶします。 頻繁に発生する場合:

1. 不要なプログラムをすべて終了または停止して、メモリと CPU を解放します。
2. アプリケーションの詳細設定を減らします。
3. [設定] にアクセスして、Windows Mixed Reality ホームに表示される詳細情報の量を減らすために **> ヘッドセット > 表示** します。

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>ヘッドセットのビューが jittering で、途切れが見られる

システムは、ヘッドセットにコンテンツを表示できないか、追跡システムで問題が発生している可能性があります。

1. タスクマネージャーを開き、PC に十分なコンピューティングリソースがあることを確認します。 CPU の80%、400 MB の RAM、およびディスク IO が80% 未満である必要があります。
2. ハードウェア用の最新のグラフィックスドライバーがあることを確認します。 「 [グラフィックスドライバー」セクション](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver)を参照してください。
3. 部屋に十分な光があることを確認します。
4. デバイスを取り外し、Windows Mixed Reality を閉じてから、もう一度接続します。
5. PC を再起動します。
6. 問題が解決しない場合は、 [カスタマーサポート](https://support.microsoft.com/)にお問い合わせください。
