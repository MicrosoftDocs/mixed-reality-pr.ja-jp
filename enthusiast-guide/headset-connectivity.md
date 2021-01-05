---
title: ヘッドセット接続に関してよく寄せられる質問
description: ヘッドセット接続 Windows Mixed Reality ヘッドセット接続のトラブルシューティングは、標準のコンシューマーサポートドキュメントを超えています。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Mixed Reality, 仮想現実, VR, MR, トラブルシューティング, エラー, ヘルプ, サポート, ヘッドセット
appliesto:
- Windows 10
ms.openlocfilehash: f42994561d032245f4f0345ad494eb38015f3682
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725593"
---
# <a name="headset-connectivity-faqs"></a>ヘッドセット接続に関してよく寄せられる質問

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>コンピューターに HDMI または表示ポートがない

アダプターを使用する必要がある場合があります。 サポートされているアダプターの一覧については、 [こちら](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) を参照してください。

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>Windows Mixed Reality ヘッドセットで USB または HDMI または DisplayPort 拡張ケーブルを使用できます。

Windows Mixed Reality ヘッドセットは、USB、HDMI、または DisplayPort 拡張ケーブルの使用を正式にサポートしていません。 これらのケーブルを使用している場合は、PC の USB コントローラーと Mixed Reality ヘッドセットの間の信号の整合性とバスパワーの変動によって、Mixed Reality エクスペリエンスが影響を受ける可能性があります。 次の場合は、拡張ケーブルを使用せずにヘッドセットを使用してみてください。
* ヘッドセットの表示が短時間でブルースクリーンで表示され、黒と Mixed Reality ポータルの再起動、または使用中に完全に列挙解除されます。
* ヘッドセットオーディオが切り取られるか、glitchy になります。
* ヘッドセットが黒と正しいディスプレイの間でちらつく

## <a name="i-am-getting-a-check-your-display-cable-error"></a>"ディスプレイケーブルを確認してください" というエラーが発生する

* アダプターを使用してヘッドセットを PC に接続している場合は、それらが Windows Mixed Reality をサポートしており、4K 対応であることを確認してください。 アダプターにヘッドセットを接続する前に、アダプターを PC に接続してみてください。
* 別の HDMI または DisplayPort ポートを使用してください。
* ヘッドセットを DisplayPort 1.2 以降、または HDMI 1.4 以降に接続します。 ポートが PC の高度なグラフィックスカードと対応していることを確認します。
* PC に統合グラフィックスと離散グラフィックスの両方がある場合は、アクティブなグラフィックスカードで HDMI または DisplayPort ポートを使用していることを確認してください。 これは、PC ディスプレイを非 HDMI ポートに接続する必要があることを意味します。
* PC に統合グラフィックスと離散グラフィックスの両方があり、統合されたグラフィックスが古いために Windows Mixed Reality がサポートされていない場合は、統合 GPU を無効にしてみてください。
* Pc モニターを PC の HDMI または DisplayPort ポートに接続します。 グラフィックスドライバーが最新であることを確認します。 AMD、Nvidia、または Intel から直接ドライバーをダウンロードしてインストールします。 Windows Update に公開されているものよりも新しい可能性があります。
* HDMI ポートに外付けモニターが接続されている場合は、代わりに DisplayPort に接続し、ヘッドセットの HDMI ポートを使用してください。
* ヘッドセットの HDMI ケーブルを、"HDMI in" ポートではなく、PC の "HDMI out" ポートに接続していることを確認します。
* Windows がディスプレイケーブル接続を検出できない可能性があります。 デバイスマネージャーを開き、ヘッドセットが [モニター] の下に表示されているかどうかを確認します。 それ以外の場合は、[操作] [ **ハードウェアの変更のスキャン > スキャン**] を選択します。 

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>"ヘッドセットに配置する" というメッセージが表示されるが、ヘッドセットがオンになっている

ヘッドセットを使用すると、Windows Mixed Reality でスペースを再読み込みするのに数秒かかることがあります。 このメッセージが表示されない場合は、レンズ間のヘッドセットの内側の近接センサーから保護ステッカーが削除されていることを確認します。 問題が解決しない場合は、ヘッドセットの製造元に問い合わせてください。

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>"ヘッドセットを接続する" というメッセージが表示されますが、ヘッドセットに接続しています

- ヘッドセットの USB および HDMI ケーブルまたは DisplayPort ケーブルが PC の正しいポートに接続されていることを確認します。 正しいポートを特定するには、次の手順を実行します。

    - USB 3.0 ポートには、"SuperSpeed" というマークの付いた特別なロゴが付いています。 ポートの内部部分は通常は青色ですが、古い USB 2.0 ポートは、内部では通常黒色または白です。
    - コンピューターに2つの HDMI または DisplayPort ポートがある場合は、コンピューターのマザーボードではなく、グラフィックスカードに接続しているものを使用します。 これは必ずしも明らかであるとは限りませんが、個別のポートは多くの場合、コンピューターの拡張スロットに配置されます。 1つのポートを試しても機能しない場合は、もう一方を試してみてください。

- ヘッドセットから USB/HDMI ケーブルまたは DisplayPort ケーブルを取り外して、安全に接続されていることを確認します。 USB ケーブルを接続するときは、USB ケーブルの挿入時に一時停止しないようにしてください。
- ヘッドセットの部分的な列挙が表示されている場合は、外部からの USB 3.0 ハブを試してください。たとえば、一連の USB デバイスが列挙されていても、デバイスマネージャーの "Mixed Reality ヘッドホン" の下には何もありません。
- ヘッドセットの製造元の web サイトにアクセスし、ヘッドセットのドライバーとファームウェアを更新します。
- ヘッドセットを別の PC に接続し、デバイスマネージャーを開きます。 PC が Windows Mixed Reality と完全に互換性がない場合でも、ヘッドセットが列挙されているかどうかを確認できます。 ヘッドセットが複数の Pc で列挙されない場合、ハードウェアの問題が発生する可能性があります。

> [!NOTE]
> Surface ユーザーの場合: 以前のバージョンの Surface Dock と Surface Book の USB ハブファームウェア更新ソフトウェアは、Mixed Reality ヘッドセットと互換性がありません。 Surface PC で "ヘッドセットを接続する" というメッセージが表示された場合は、デバイスマネージャーに "コード 10: デバイスを起動できません" というエラーを報告しているデバイスがないかどうかを確認します。 その場合は、 [競合しているドライバーを削除](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book)します。 この操作は一度だけ行う必要があります。

注 Windows 10-N ユーザーの場合: PC で Windows 10 N が実行されている場合は、Mixed Reality ヘッドセットに接続した後、デバイスマネージャーに "コード 28: インストールクラスが存在しないか、無効です" というエラーが表示されます。 Windows 10 の N エディションは、Windows Mixed Reality ではサポートされていません。 詳細については、こちらの [手順](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) に従ってください。

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>"USB ケーブルを確認してください" または "USB 速度が不足しています" というメッセージが表示する

* PC でサポートされている USB 3.0 ポートを使用していることを確認します。

    * ヘッドセットの USB ケーブルがすべて接続されていることを確認します。
    * [Windows Mixed Reality ポータル](install-windows-mixed-reality.md#launch-mixed-reality-portal)を実行して、PC の USB 3.0 コントローラーがサポートされていることを確認します。
    * ヘッドセットを PC の他の USB 3.0 ポートに接続します。 Pc によっては、複数の USB 3.0 コントローラーが搭載されている場合があります。
    * PC に接続されているすべての USB デバイスを一時的に切断し、ヘッドセットのみを接続します。
    * カスタム作成の Pc では、ポートが USB 3.0 ポートとしてマークされていても、USB 2.0 コントローラーに接続されている可能性があります。 ヘッドセットを接続した状態で、デバイスマネージャーを開き、ヘッドセットから列挙されたデバイスのいずれかを見つけてクリックし、[ **接続別の > デバイスの表示**] に移動します。
* 別の PC でヘッドセットを試してみてください。 他の PC が Windows Mixed Reality と完全に互換性がない場合は、デバイスマネージャーをチェックインして、"USB 速度が不足しています" というメッセージが表示されるかどうかを確認します。 複数の Pc で正しく列挙されない場合は、ヘッドセットに欠陥がある可能性があります。
* ヘッドセットとコンピューター間の extender またはハブをすべて削除します。

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>ヘッドセットに接続した後に Mixed Reality ポータルが起動しない

基になる問題のため、ヘッドセットが正しく検出されていない可能性があります。 Mixed Reality ポータルを手動で起動し、表示されるエラーメッセージを探します。

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>PC がスリープモードまたは休止モードになったとき、または自分のヘッドセットが取り付けられている PC を再起動したときに、ヘッドセットが動作を停止した

1. デバイスマネージャーを開き、ヘッドセットが [Mixed Reality デバイス] の下に一覧表示されていることを確認します。
2. [Mixed Reality デバイス] でヘッドセットを選択し、デバイスの状態が "このデバイスは正常に動作しています" と表示されていることを確認します。
3. デバイスが動作を停止したことを示す "コード 43" エラーが表示された場合、または [Mixed Reality デバイス] の下にヘッドセットが表示されない場合は、ヘッドセットの USB ケーブルを取り外し、replug します。 マイクロソフトは、ソフトウェアとドライバーの相互運用性に関する潜在的な問題を調査しています。このエラーが発生する可能性があります。 この問題は少数の Pc に影響を及ぼし、Mixed Reality ヘッドセットドライバーの今後の更新で解決される予定です。

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>PC をスリープ状態にするか、休止モードにすると、自分のヘッドセットによって、PC でバグチェック (青い画面) が生成されます。

10.0.19041.2034 ドライバー以降であることを確認します。

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>ヘッドセットに接続したときにヘッドセットドライバーが自動的にインストールされませんでした

新しい Pc、または新しくインストールされた Windows 10 のコピーを搭載した Pc では、ヘッドセットドライバーが他の Windows 更新プログラムの背後でキューに置かれ、すぐにはインストールされない場合があります。

1. [ **スタート > デバイスマネージャー** にアクセスし、ヘッドセットの [Mixed Reality デバイス] を確認します。 デバイスの状態は、"デバイスが正常に動作している" ことを示します。
2. デバイスを右クリックし、[ドライバーの更新] を選択します。

それでもうまくいかない場合は、ドライバーをアンインストールしてみてください。

1. [ **スタート > デバイスマネージャー** にアクセスし、ヘッドセットの [Mixed Reality デバイス] を確認します。 デバイスの状態は、"デバイスが正常に動作している" ことを示します。
2. デバイスを右クリックし、[デバイスのアンインストール] を選択します。
3. 表示される新しいポップアップで、[このデバイスのドライバーソフトウェアを削除する] チェックボックスをオンにし、[アンインストール] を選択します。
4. この処理が完了したら、PC からヘッドセットを取り外し、に戻します。 新しいドライバーをダウンロードしてインストールする Windows Update ます。

注: windows の N エディションを使用している場合は、windows Mixed Reality を使用するには、windows 10 の通常のエディションに切り替える必要があります。