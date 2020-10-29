---
title: Windows Mixed Reality セットアップに関する FAQ
description: Windows Mixed Reality を使用するときの一般的なセットアップの質問に対する回答を得ます。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、フィードバック、フィードバックハブ、バグ
appliesto:
- Windows 10
ms.openlocfilehash: 2e7276e7d734770e29ce41db9a19ef40555fea30
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685567"
---
# <a name="windows-mixed-reality-setup-faq"></a>Windows Mixed Reality セットアップに関する FAQ

Windows Mixed Reality のイマーシブヘッドセットを設定するときに発生する可能性のある問題のトラブルシューティングに役立つ情報を次に示します。

## <a name="i-get-a-message-that-says-we-couldnt-download-the-window-mixed-reality-software-or-setup-is-stuck-on-the-hang-tight-while-we-do-some-downloading-page"></a>「Windows Mixed Reality ソフトウェアをダウンロードできませんでした」というメッセージが表示されるか、またはセットアップが [ダウンロード中にハングしています] ページで停止します。

以下を試してみてください。
* [設定] にアクセスして **& セキュリティ > Windows Update を更新 >** 、Windows Update が有効になっていることを確認します。 次に、インストールを待機している更新プログラムをダウンロードしてインストールします。
* PC がインターネットに接続されており、少なくとも 2 GB の空き記憶領域があることを確認します。
* PC を再起動して、もう一度やり直してください。 場合によっては、複数回繰り返すか、Windows Update のトラブルシューティングツールを実行して保留中の更新プログラムを消去する必要があります。 

> [!NOTE]
> * エンタープライズ管理ネットワークを使用している場合は、管理者に確認してください。 Windows Mixed Reality を有効にすることが必要になる場合があります。 IT プロフェッショナル向けの手順をお探しですか? **[この記事](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality)** をご覧ください。
> * Wi-fi ネットワーク接続が従量制課金に設定されている場合は、従量制課金に変更します。 **[詳細情報](https://support.microsoft.com/help/4028458)**

## <a name="i-get-a-message-that-says-something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"問題が発生しました。 Windows Mixed Reality を開始できませんでした" というメッセージが表示されます。

以下を試してみてください。
1. コンピューターからヘッドセットを取り外します (両方のケーブル)。
2. コンピューターを再起動する
3. [ **設定] を > & セキュリティ Windows Update > を更新** し、Windows Update が有効になっていることを確認します。 次に、インストールを待機している更新プログラムをダウンロードしてインストールします。
4. ヘッドセットをコンピューターに再接続してから、セットアップを再試行してください。

上記の手順が機能しない場合は、Windows Mixed Reality をアンインストールしてから再インストールしてみてください。 [設定] [ **Mixed reality > アンインストール] >** クリックして、[ **アンインストール** ] を選択します。 次に、コンピューターを再起動します。 もう一度セットアッププロセスを開始するには、ヘッドセットを PC に接続するだけです。

## <a name="i-get-a-message-that-says-my-pc-cant-run-windows-mixed-reality"></a>"PC で Windows Mixed Reality を実行できません" というメッセージが表示されます。

このメッセージが表示された場合は、Windows Mixed Reality を実行するために必要な [最小要件](https://support.microsoft.com/help/4039260) を PC が満たしていません。 これは、コンピューターのハードウェアセットアップが Windows Mixed Reality と互換性がないか、 [最新バージョンの windows に更新](https://support.microsoft.com/help/12373)する必要があることが原因である可能性があります。

グラフィックスカードに関する注意事項:

* Windows Mixed Reality セットアップでグラフィックスカードが要件を満たしていないと思われる場合は、ヘッドセットが正しいカードに接続されていることを確認します。
* ドライバーの最新の更新については、グラフィックスカードの製造元に問い合わせてください。 Windows Mixed Reality には、少なくとも WDDM 2.2 をサポートするグラフィックスカードドライバーが必要です。

## <a name="i-get-a-message-that-says-youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>「今のところ、この PC は Windows Mixed Reality を実行するために必要な最小要件を満たしていません」というメッセージが表示されます。

このメッセージが表示された場合、Windows Mixed Reality の最良のエクスペリエンスを実現するために必要な最小要件を PC が満たしていません。 お使いの PC では、イマーシブヘッドセットを実行できますが、特定のアプリを実行できないか、またはパフォーマンスに問題がある可能性があります。

## <a name="my-xbox-controller-isnt-working"></a>Xbox コントローラーが動作していません。

以下を試してみてください。

* コントローラーの電源が入っていること、完全に充電されていること、および PC に接続されていることを確認します。
* コントローラーのバッテリを交換します。
* Bluetooth コントローラーを使用している場合は、PC 上の [設定] [ **デバイス > bluetooth & 他のデバイスの >** ] にアクセスし、ペアリングされていることを確認します (ページに表示されていることを確認してください)。

[Xbox コントローラーの詳細情報](https://support.xbox.com/xbox-on-windows/accessories/connect-xbox-one-controller-to-pc)

## <a name="my-motion-controllers-arent-working"></a>モーションコントローラーが動作していません。
 
以下を試してみてください。

* コントローラーの電源が入っていて、完全に充電されていることを確認します。
* コントローラーのバッテリを交換します。
* コントローラーをオンにしたまま、再び手前に表示したままにします。 4秒間、Windows ボタンを押したままにして、コントローラーの電源をオフにします。2秒間、もう一度押して電源をオンにします。 
* [設定] にアクセスして、PC の [ **Bluetooth & 他のデバイス > デバイスを >** し、ペアリングされていることを確認します (ページに一覧表示されているはずです)。

[モーションコントローラーの詳細情報](controllers-in-wmr.md)

## <a name="i-get-a-message-that-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>ヘッドセットに接続しているにもかかわらず、「ヘッドセットを接続する」というメッセージが表示されます。

以下を試してみてください。

* ヘッドセットがコンピューターの正しいポートに接続されていることを確認します。 PC の独立したグラフィックスカードと USB 3.0 ポートに接続されている必要があります。 正しいポートを特定するには、次の手順を実行します。
    * USB 3.0 ポートには、"SuperSpeed" というマークの付いた特別なロゴが付いています。 ポートの内部部分は通常は青色で、古い USB 2.0 ポートは、内部では通常は黒または白です。
    * コンピューターに2つの HDMI ポートがある場合は、コンピューターのマザーボードではなく、グラフィックスカードに接続しているものを使用します。 これは必ずしも明らかであるとは限りませんが、個別のポートは多くの場合、コンピューターの拡張スロットに配置されます。 1つのポートを試しても機能しない場合は、もう一方を試してみてください。
* ヘッドセットの製造元の web サイトにアクセスし、ヘッドセットのドライバーとファームウェアを更新します。

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>境界を作成しようとすると、エラーメッセージが表示されます。

境界を作成するためのガイドラインを次に示します。

* 壁やその他の障害物に近すぎないようにしてください。
* ヘッドセットをウェストの高さに保持し、境界のトレース中にコンピューターに向いていることを確認します。
* センサーがブロックされていないことと、十分な光があることを確認してください。
* トレースしている領域は、3平方メートルを超える必要があります。
* 空間が大きすぎたり複雑すぎたりしないようにする必要があります。この場合、ひねるとターンが多くなくても、単純な幾何学的な形になります。
* トレース中に、独自のパスを使用しないようにしてください。
* 角が動かない場合は、最初からやり直してください。

**[固定されたもののみ] を選択した場合、どのようなエクスペリエンスが得られますか。**

"固定された状態のみ" とは、境界のないヘッドセットを使用することを意味します。 物理的な障害を回避するための境界がないため、1つの場所に保持する必要があります。 また、一部のアプリとゲームは、境界と共に使用するように設計されている場合があるため、意図したとおりに動作しないことがあります。

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>ヘッドセットでより明確なビューを取得するにはどうすればよいですか。

ヘッドセットの調整を試してみてください。 表面上での位置を調整するには、上下または左右に移動します。ストラップを調整して、snug を感じるようにします。

ヘッドセットでサポートされている場合は、その調整設定を調整することもできます。 ヘッドセットに調整のためのノブがある場合は、それを使用します。 表示されていない場合は、[設定] にアクセスして **> Mixed reality > 画質** を調整し、調整を調整します。 特定のデバイスの調整の詳細については、ヘッドセットの製造元に確認してください。

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Windows Mixed Reality ではどの言語がサポートされていますか。

Windows Mixed Reality は、次の言語で使用できます。 PC が別の言語に設定されている場合でも、Windows Mixed Reality を使用できますが、インターフェイスは英語 (米国) で表示され、音声コマンドやディクテーションは使用できません。

* 簡体字中国語 (中国)
* 英語 (オーストラリア)
* 英語 (カナダ)
* 英語 (英国)
* 英語 (米国)
* フランス語 (カナダ)
* フランス語 (フランス)
* ドイツ語 (ドイツ)
* イタリア語 (イタリア)
* 日本語 (日本)
* スペイン語 (メキシコ)
* スペイン語 (スペイン)

また、上記のサポートされている Windows Mixed Reality 言語のいずれかでディクテーションを使用することもできます。スクリーンキーボードで [ **マイク**  ] を選択するだけです。

Windows Mixed Reality は、次の言語でも使用できます。音声コマンドやディクテーション機能は必要ありません。

* 繁体字中国語 (台湾および香港)
* オランダ語 (オランダ)
* 韓国語 (韓国)
* ロシア語 (ロシア)

## <a name="when-i-plug-in-my-headset-nothing-happensmixed-reality-portal-doesnt-open"></a>ヘッドセットを接続しても何も起こりません。 Mixed Reality ポータルが開かれていません。

Windows Mixed Reality のセットアップを実行するアプリである mixed Reality ポータルは、互換性のあるヘッドセットを接続するときに自動的に開くように設計されています。 開いていない場合は、[ **スタート** ] にアクセスし、 **検索** ボックスに「 **Mixed Reality Portal** 」と入力して、そこからアプリを開きます。 Mixed Reality ポータルが見つからない場合は、 [最新バージョンの Windows に更新](https://support.microsoft.com/help/12373) する必要があるか、ヘッドセットが PC に正しく接続されていないことを意味します。

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer"></a>ヘッドセットのサウンドが聞こえないか、またはコンピューターでサウンドが再生されています。

イマーシブヘッドセットに内蔵ヘッドホンが含まれていない場合は、ヘッドホンをヘッドホンのオーディオジャックに接続する必要があります。 (多くの場合、ジャックはヘッドセットのバイザーまたはレンズのすぐ内側にあります。問題が検出されない場合は、ヘッドセットの製造元に確認してください。) 

オーディオヘッドセットの中には、音量を調整するための物理的なボタンがあるものもあります。 オーディオが動作していない場合は、ボリュームが有効になっているかミュートされているかを確認します。

Windows Mixed Reality は、カードを装着してヘッドホンを接続したときに、イマーシブヘッドセットを使用してサウンドを再生するように設計されています。 ヘッドセットをオフにするか、またはバイザーを裏返すと、オーディオは既定の Windows 再生デバイスに切り替わります。 [設定] でこの設定を変更して、[ **オーディオと音声] > [Mixed reality] >** ます。

> [!NOTE]
> * Windows Mixed Reality 空間オーディオは、イマーシブヘッドセットに内蔵または直接接続されているヘッドホンで最適に動作します。 Pc スピーカーまたは PC に接続されているヘッドホンが、空間オーディオで適切に動作しないことがあります。
> * Windows Mixed Reality は、Bluetooth オーディオヘッドセットをサポートしていません。

## <a name="speech-commands-arent-working"></a>音声コマンドが動作していません。

音声コマンドを使用するには、PC の音声と言語の設定が、Windows Mixed Reality でサポートされているいずれかの [言語](#what-languages-are-supported-in-windows-mixed-reality) に設定されている必要があります。 これを確認するには、[設定] [ **> 時間 & 言語 > 地域 & 言語** と設定] にアクセスし、[ **> & 言語 > 音声** ] をオンにします。

ヘッドセットにマイクが内蔵されていない場合は、ヘッドホンをヘッドホンに接続するか、PC に接続する必要があります。 磨耗するときに、ヘッドホンに自動的に mic 入力スイッチを付けるには、[設定] [ **Mixed reality > オーディオと音声** ] に移動し、ヘッド **セットを磨耗** したときにヘッドセットを > に切り替えます。

オーディオヘッドセットには、マイクのミュートとミュート解除を行うための物理的なボタンがあります。 音声コマンドが動作していない場合は、mic がミュートされているかどうかを確認します。

## <a name="my-head-mount-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>シャットダウンして高速なスタートアップを実行した後は、ヘッドマウントの表示が機能しません。

これを試してみます。

* ヘッドマウントディスプレイからディスプレイケーブルと USB ケーブルを抜いてから、再び接続します。

## <a name="my-wi-fi-slows-down-when-i-use-windows-mixed-reality"></a>Windows Mixed Reality を使用すると Wi-fi の速度が低下する

2.4 GHz の Wi-fi 接続を使用している場合は、動作コントローラーによって Wi-fi の速度が低下する可能性があります。 次のいずれかの操作を試してください。

* 5 GHz の Wi-fi 接続 (使用可能な場合) に切り替えます。 詳細情報
* 別の Bluetooth アダプターを使用して、動きコントローラーを PC に接続します。 [推奨されるアダプターの表示](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

> [!NOTE]
> 新しいヘッドセットは、組み込みの Bluetooth チップを通じてコントローラーに直接ペアになっており、この問題が発生することはありません。 

## <a name="see-also"></a>関連項目
* [コミュニティへの質問](https://answers.microsoft.com)
* [サポートについては、お問い合わせください](https://support.microsoft.com/contactus/)
* [トラブルシューティング](troubleshooting-windows-mixed-reality.md)

