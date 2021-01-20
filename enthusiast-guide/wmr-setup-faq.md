---
title: Windows Mixed Reality の設定に関する FAQ
description: Windows Mixed Reality アプリケーションとデバイスを操作するときの一般的なセットアップに関する質問への回答を得ます。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、フィードバック、フィードバックハブ、バグ
appliesto:
- Windows 10
ms.openlocfilehash: 87eb22e600ca2426bdd3fec1fd428c11d9c45313
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581810"
---
# <a name="windows-mixed-reality-setup-faq"></a>Windows Mixed Reality の設定に関する FAQ

Windows Mixed Reality のイマーシブヘッドセットを設定するときに発生する可能性のある問題のトラブルシューティングに役立つ情報を次に示します。

## <a name="i-get-a-message-that-says-we-couldnt-download-the-window-mixed-reality-software-or-setup-is-stuck-on-the-hang-tight-while-we-do-some-downloading-page"></a>「Windows Mixed Reality ソフトウェアをダウンロードできませんでした」というメッセージが表示されるか、またはセットアップが [ダウンロード中にハングしています] ページで停止します。

次の手順を試してみてください。

* [設定] にアクセスして **& セキュリティ > Windows Update を更新 >** 、Windows Update が有効になっていることを確認します。 次に、インストールを待機している更新プログラムをダウンロードしてインストールします。
* PC がインターネットに接続されており、少なくとも 2 GB の空き記憶領域があることを確認します。
* PC を再起動して、もう一度やり直してください。 場合によっては、複数回繰り返すか、Windows Update のトラブルシューティングツールを実行して保留中の更新プログラムを消去する必要があります。

> [!NOTE]
> * エンタープライズ管理ネットワークを使用している場合は、管理者に確認してください。 Windows Mixed Reality を有効にすることが必要になる場合があります。 IT プロフェッショナル向けの手順をお探しですか? **[この記事](/windows/application-management/manage-windows-mixed-reality)** をご覧ください。
> * Wi-Fi ネットワーク接続が従量制課金に設定されている場合は、従量制課金に変更します。 **[詳細情報](https://support.microsoft.com/help/4028458)**

## <a name="i-get-a-message-that-says-something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"問題が発生しました。 Windows Mixed Reality を開始できませんでした" というメッセージが表示されます。

次の手順を試してみてください。

1. コンピューターからヘッドセットを取り外します (両方のケーブル)。
2. コンピューターを再起動する
3. [ **設定] を > & セキュリティ Windows Update > を更新** し、Windows Update が有効になっていることを確認します。 次に、インストールを待機している更新プログラムをダウンロードしてインストールします。
4. ヘッドセットをコンピューターに再接続してから、セットアップを再試行してください。

上記の手順が機能しない場合は、Windows Mixed Reality をアンインストールしてから再インストールしてみてください。 [設定] [ **Mixed reality > アンインストール] >** クリックして、[ **アンインストール**] を選択します。 次に、コンピューターを再起動します。 もう一度セットアッププロセスを開始するには、ヘッドセットを PC に接続するだけです。

## <a name="the-mixed-reality-portal-doesnt-open-when-i-plug-in-my-headset"></a>ヘッドセットを接続したときに Mixed Reality ポータルが開かない

Windows Mixed Reality のセットアップを実行するアプリである mixed Reality ポータルは、互換性のあるヘッドセットを接続するときに自動的に開くように設計されています。 開いていない場合は、[スタート] にアクセスし、検索ボックスに「Mixed Reality ポータル」と入力して、アプリを開きます。 Mixed Reality ポータルが見つからない場合は [、最新バージョンの Windows に更新](https://support.microsoft.com/en-us/help/12373/windows-update-faq) することが必要になる場合があります。

## <a name="i-get-a-message-that-says-my-pc-cant-run-windows-mixed-reality"></a>"PC で Windows Mixed Reality を実行できません" というメッセージが表示されます。

このメッセージが表示された場合は、Windows Mixed Reality を実行するために必要な [最小要件](https://support.microsoft.com/help/4039260) を PC が満たしていません。 コンピューターのハードウェアのセットアップが Windows Mixed Reality と互換性がない可能性があります。または、 [最新バージョンの windows に更新](https://support.microsoft.com/help/12373)する必要がある場合があります。

グラフィックスカードに関する注意事項:

* Windows Mixed Reality セットアップでグラフィックスカードが要件を満たしていないと思われる場合は、ヘッドセットが正しいカードに接続されていることを確認します。
* ドライバーの最新の更新については、グラフィックスカードの製造元に問い合わせてください。 Windows Mixed Reality には、少なくとも WDDM 2.2 をサポートするグラフィックスカードドライバーが必要です。

## <a name="i-get-a-message-that-says-youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>「今のところ、この PC は Windows Mixed Reality を実行するために必要な最小要件を満たしていません」というメッセージが表示されます。

このメッセージが表示された場合、Windows Mixed Reality の最良のエクスペリエンスを実現するために必要な最小要件を PC が満たしていません。 お使いの PC では、イマーシブヘッドセットを実行できますが、特定のアプリを実行できない場合や、パフォーマンスに問題がある場合があります。

## <a name="my-xbox-controller-isnt-working"></a>Xbox コントローラーが動作していない

次の手順を試してみてください。

* コントローラーの電源が入っていること、完全に充電されていること、および PC に接続されていることを確認します。
* コントローラーのバッテリを交換します。
* Bluetooth コントローラーを使用している場合は、PC 上の [設定] [ **デバイス > bluetooth & 他のデバイスの >** ] にアクセスし、ペアリングされていることを確認します (ページに表示されていることを確認してください)。

[Xbox コントローラーの詳細情報](https://support.xbox.com/xbox-on-windows/accessories/connect-xbox-one-controller-to-pc)

## <a name="my-motion-controllers-arent-working"></a>モーションコントローラーが動作していません

次の手順を試してみてください。

* コントローラーの電源が入っていて、完全に充電されていることを確認します。
* コントローラーのバッテリを交換します。
* コントローラーをオンにしたまま、再び手前に表示したままにします。 4秒間、Windows ボタンを押したままにして、コントローラーの電源をオフにします。2秒間、もう一度押して電源をオンにします。
* [設定] にアクセスして、PC の [ **Bluetooth & 他のデバイス > デバイスを >** し、ペアリングされていることを確認します (ページに一覧表示されているはずです)。

[モーションコントローラーの詳細情報](controllers-in-wmr.md)

## <a name="i-get-a-message-that-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>ヘッドセットに接続しているにもかかわらず、「ヘッドセットを接続する」というメッセージが表示されます。

次の手順を試してみてください。

- ヘッドセットがコンピューターの正しいポートに接続されていることを確認します。 PC の独立したグラフィックスカードと USB 3.0 ポートに接続されている必要があります。 正しいポートを特定するには、次の手順を実行します。
    - USB 3.0 ポートには、"SuperSpeed" というマークの付いた特別なロゴが付いています。 ポートの内部部分は通常は青色ですが、古い USB 2.0 ポートは、内部では通常黒色または白です。
    - コンピューターに2つの HDMI ポートがある場合は、コンピューターのマザーボードではなく、グラフィックスカードに接続しているものを使用します。 これは必ずしも明らかであるとは限りませんが、個別のポートは多くの場合、コンピューターの拡張スロットに配置されます。 1つのポートを試しても機能しない場合は、もう一方を試してみてください。
- ヘッドセットの製造元の web サイトにアクセスし、ヘッドセットのドライバーとファームウェアを更新します。

## <a name="during-mixed-reality-start-up-im-stuck-at-turn-your-head-side-to-side-and-then-at-the-floor"></a>Mixed Reality の起動時には、「ヘッドを並べて、次にフロアを切る」で行き詰まっています。

この手順では、ヘッドセットでスペースを認識し、既存のバーチャルフロアと境界を復元できます。 ヘッドセットに入れると、このスキャンプロセスに最大で10秒かかることがあります。 完了すると、Windows Mixed Reality ホームになるか、境界をもう一度設定するように求められます。

スキャンプロセスにかかる時間が10秒を超えた場合は、ヘッドセットの近接センサーに問題がある可能性があります。

1. 近接センサーからステッカーが削除されていることを確認します。 近接センサーは、ヘッドセット内に配置されています。
2. 近接センサーがヘッドセットへの入力を切り替えていることを確認します。指を使用して、入力がヘッドセットに切り替わることを確認するために、距離センサーを数回入力します。 PC の上部に **Windows キー + Y** バナーが表示されます。 キーボードで「 **Windows キー + Y** 」と入力すると、入力をいつでも手動でヘッドセットに切り替えることができます。

## <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height"></a>Windows Mixed Reality ホームのフロアが正しい高さになっていないように見える

[ **開始 > フロア調整**] を選択します。これは、世界中にアプリを配置した後に起動し、ヘッドセットの装着中に変更を行います。 このアプリでは、タッチパッド (モーションコントローラー) または方向パッド (ゲームパッド) を使用して、床の高さを調整するように指示されます。 フロアが正しい場合は、[Windows] ボタンを使用してホームに戻ります。

## <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop"></a>自分のデスクトップのヘッドセットに表示される内容のプレビューを表示できません

Windows Mixed Reality ポータルには、画面下部に [ **再生** ] ボタンがあります。このボタンを使用すると、画面のヘッドセットに表示されていることをデスクトップ画面にプレビューできます。 パフォーマンス上の理由から、この機能は Windows Mixed Reality (90 Hz) で実行されている Pc でのみ使用できます。

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>ヘッドセットでより明確なビューを取得する方法はありますか

ヘッドセットの調整を試してみてください。 表面上での位置を調整するには、上下または左右に移動します。ストラップを調整して、snug を感じるようにします。

ヘッドセットでサポートされている場合は、その調整設定を調整することもできます。 ヘッドセットに調整のためのノブがある場合は、それを使用します。 表示されていない場合は、[設定] にアクセスして **> Mixed reality > 画質** を調整し、調整を調整します。 特定のデバイスの調整の詳細については、ヘッドセットの製造元に確認してください。

## <a name="when-i-plug-in-my-headset-nothing-happensmixed-reality-portal-doesnt-open"></a>ヘッドセットを接続しても何も起こりません。 Mixed Reality ポータルが開いていません。

Windows Mixed Reality のセットアップを実行するアプリである mixed Reality ポータルは、互換性のあるヘッドセットを接続するときに自動的に開くように設計されています。 開いていない場合は、[**スタート**] にアクセスし、**検索** ボックスに「 **Mixed Reality Portal** 」と入力して、そこからアプリを開きます。 Mixed Reality ポータルが見つからない場合は、 [最新バージョンの Windows に更新](https://support.microsoft.com/help/12373) する必要があるか、ヘッドセットが PC に正しく接続されていないことを意味します。

## <a name="my-head-mount-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>シャットダウンして高速スタートアップを実行すると、ヘッドマウントの表示が機能しない

これを試してみます。

* ヘッドマウントディスプレイからディスプレイケーブルと USB ケーブルを抜いてから、再び接続します。

## <a name="my-wi-fi-slows-down-when-i-use-windows-mixed-reality"></a>Windows Mixed Reality を使用すると Wi-Fi 速度が低下する

2.4 GHz の Wi-Fi 接続を使用している場合、動作コントローラーは Wi-fi の速度を低下する可能性があります。 次のいずれかの手順を実行します。

* 5 GHz の Wi-Fi 接続 (使用可能な場合) に切り替えます。 詳細情報
* 別の Bluetooth アダプターを使用して、動きコントローラーを PC に接続します。 [推奨されるアダプターの表示](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

> [!NOTE]
> 新しいヘッドセットは、組み込みの Bluetooth チップを通じてコントローラーに直接ペアになっており、この問題が発生することはありません。

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>"問題が発生しました" というエラーメッセージが表示されるか、または Mixed Reality ポータルで問題が発生しています

特定のエラーコードに関する詳細情報を取得するには、 [こちら](error-codes.md)を参照してください。 次のようにすることもできます。

Windows Mixed Reality を再起動します。

1. PC からヘッドセットケーブルの両方を切断します。
2. PC を再起動します。
3. ヘッドセットを再接続します。

PC でヘッドセットが認識されていることを確認します。

1. [スタート] を選択します。
2. 検索ボックスに「デバイスマネージャー」と入力し、一覧から選択します。
3. [Mixed reality devices] を展開し、ヘッドセットが表示されているかどうかを確認します。

表示されていない場合:

1. 使用可能な場合は、ヘッドセットを PC の別のポートに接続します。
2. Windows Update から、最新のソフトウェア更新プログラムを確認します。
3. Windows Mixed Reality をアンインストールして再インストールします。
    1. PC からヘッドセットケーブルの両方を切断します。
    2. [設定] を選択して **> Mixed reality > アンインストール**] を選択します。
    3. モーションコントローラーが PC とペアリングされている場合は、[ **設定] > [Bluetooth & 他のデバイス >** デバイス] を選択してペアリングします。 各コントローラーを選択し、[デバイスの削除] をクリックします。 コントローラーがヘッドセットとペアリングされている場合は、この手順を省略できます。
    4. ヘッドセットを PC に接続し直して、Windows Mixed Reality を再インストールします。

## <a name="see-also"></a>関連項目

* [コミュニティへの質問](https://answers.microsoft.com)
* [サポートについては、お問い合わせください](https://support.microsoft.com/contactus/)
* [トラブルシューティング](troubleshooting-windows-mixed-reality.md)