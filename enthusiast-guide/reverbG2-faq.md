---
title: HP リバーブ G2 Faq
description: Windows Mixed Reality のイマーシブヘッドセットで HP リバーブ G2 ヘッドセットを使用する方法についてよく寄せられる質問をご覧ください。
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート、パフォーマンス
appliesto:
- Windows 10
ms.openlocfilehash: 00338e1354dc04acc76fa2525c721a5e2bd4afe2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009472"
---
# <a name="hp-reverb-g2-frequently-asked-questions"></a>HP リバーブ G2 に関してよく寄せられる質問

## <a name="is-there-a-specific-order-i-should-follow-to-connect-my-headset-cables-to-a-pc"></a>ヘッドセットケーブルを PC に接続するために従うべき特定の順序はありますか。

HP は次のことを推奨します。

- PC または電源に接続する前に、まず6メートルのケーブルをヘッドセットに接続します。
- 最初のインストール後に、6メートルのケーブルをヘッドセットに接続したままにします。
- ヘッドセットが使用されていない場合は、電源アダプターを6メートルのケーブルから切断します。

## <a name="what-should-i-do-to-get-a-crisper-image"></a>鮮明なイメージを取得するにはどうすればよいですか。

表示が少しぼやけて見える場合は、いくつかの操作を試してみることができます。

- ヘッドセットが、レンズの中央にある目と同じ位置にあることを確認します。
- IPD (interpupillary distance) の調整を試みます。 リバーブ G2 はハードウェア IPD を使用します。 これを変更するには、ヘッドセットの IPD 調整を探します。
- グラスや連絡先が必要な場合は、デバイスを使用するときに摩耗する必要があります。
- レンズがクリーンであることを確認します (マイクロ fiber 布のみ–液体なし)。
- 高度なヘッドセットの設計により、Lcd がウォームアップするまでの間、デバイスを起動するときに、最初の数分間に軽微な画像が表示されることがあります。

## <a name="i-am-getting-a-7-14-something-went-wrong-error-when-i-plug-in-my-headset"></a>ヘッドセットに接続したときに 7-14 "問題が発生しました" というエラーが発生する

7-14 の問題が発生した場合は、必要な USB2 コンポーネントの一部が見つからなかったことを意味します。  HP リバーブ G2 の長いケーブルによって、USB 信号の許容範囲の一部が増えています。  これは、コンピューターの1つのポートが別のポートよりも信頼性の高い方法で動作する可能性があることを意味します。

7-14 "問題が発生しました" というエラーが表示される場合は、次の手順を試してください。

- ヘッドセットと USB コントローラー用に最新のドライバーがインストールされていることを確認します。
- Microsoft USB ドライバーを使用していることを確認してください。 "拡張可能なホストコントローラー" デバイスの名前に "Microsoft" が含まれている必要があります。
- お使いのコンピューターの別の USB-3.0 ポートにケーブルを接続してみてください。 (USB タイプ-C とタイプ-A ポートを試す)
- アダプターに含まれている USB C を使用して、別のポートを試します。
- USB ハブを使用してコンピューターにヘッドセットを接続してみてください。

> [!NOTE]
> HP では、リバーブ G2 デバイスを搭載したマザーボードに組み込まれている USB コントローラーのみを使用することをお勧めします。
> デバイスに接続できない場合は、 [HP サポート](https://support.hp.com/us-en)にお問い合わせください

## <a name="i-am-getting-a-13-14-something-went-wrong-error-when-my-pc-resumes-from-hibernate-s4"></a>PC が休止状態 (S4) から再開したときに、13-14 "問題が発生しました" というエラーが発生する

再開プロセス中に、ビデオカードが接続を確立できないことがあります。そのため、PC から USB タイプ C を取り外してから再び接続すると、接続の確立に役立ちます。

## <a name="my-hp-motion-controller-joystick-will-sometimes-stick-to-one-side"></a>HP Motion Controller ジョイスティックが1辺になることがある

この問題は、ジョイスティックをクリックするまで完全に押し下げ、自由に移動することによって修正されます。

## <a name="others-state-i-am-loud-or-that-my-audio-is-clipping-while-i-am-using-the-microphone-with-some-applications"></a>一部のアプリケーションでマイクを使用しているときに、他の人が音量を大きくしたり、オーディオがクリッピングしたりしています。

HP リバーブ G2 マイクが Windows PC によって最初に認識されると、入力ボリュームレベルは自動的に100% に設定されます。 リバーブ G2's は高品質のマイクであるため、入力の感度は、Windows 10 の既定の設定よりもはるかに高くなります。 リバーブ G2 マイクの入力レベルを50% から設定し、そこからスケールアップすることをお勧めします。 最適な設定は、特に "自動ゲイン" マイクの設定がないアプリケーションを使用する場合に、ユーザーに固有です。 "自動利得" が適用されるアプリケーションの例としては、Skype、Zoom、Teams、Cisco WebEx などがありますが、すべての VR ソーシャルアプリケーションやブロードキャストアプリケーションがこの機能を備えているわけではありません。

## <a name="the-mixed-reality-portal-says-cant-run-mixed-reality-on-this-headset-but-this-worked-fine-with-my-previous-wmr-headset"></a>Mixed Reality ポータルでは、"このヘッドセットでは mixed reality を実行できません" と表示されますが、これは以前の WMR ヘッドセットで問題なく動作しています。

これは、HP リバーブ G2 が最適なエクスペリエンスを実現するためにより強力な PC を必要とするために発生する可能性があります。 詳細については、「PC の最小[要件](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)」を参照してください。

## <a name="it-looks-like-my-left-display-is-stretched-and-the-right-display-is-off-centered-and-half-black"></a>左側の表示が拡大しているように見えますが、右の表示は中央から半分になります。

これは、ヘッドセットがネイティブの解像度で実行されていない場合に発生する可能性があります。 HP リバーブ G2 HMD の高解像度ディスプレイの性質により、すべてのシステムでネイティブの解像度がレンダリングされるわけではありません。 この後の Windows Update では、ヘッドセットがネイティブの解像度ではないときにレンダリングの問題に対処する修正が行われています。

システムがネイティブの解決方法でレンダリングできない理由はいくつかあります。

- システム上の DisplayPort が1.3 と互換性がない場合や、4つのレーンがすべてサポートされていない場合があります。
- アダプターを使用している場合は、HBR3 との互換性がサポートされていないか、4つのレーンがすべてサポートされていない可能性があります。
- システムにハイブリッド GPU が搭載されている場合は、DisplayPort で使用可能な帯域幅を制限している可能性があります。

## <a name="why-are-my-hp-motion-controller-models-not-showing-up-correctly-in-a-game"></a>HP Motion Controller モデルがゲームで正しく表示されないのはなぜですか。

ほとんどのゲームはコントローラーを表示せず、ドライバーによってインストールされたモデルを使用しませんが、一部のゲームでは独自のバージョンのコントローラーモデルを使用して、それらをカスタマイズしたり、使用可能な入力のコンテキストヘルプを表示したりします。 通常、これによってゲームの機能がブロックされることはありませんが、混乱や視覚的な成果物につながる可能性があります。 これは、ゲーム自体の更新プログラムでのみ修正できます。

## <a name="my-steamvr-games-dont-appear-to-work-correctly-with-my-hp-motion-controllers"></a>私の SteamVR ゲームが HP Motion controller で正常に動作していないように見える

開発者が HP Motion Controller の互換性のためにゲームを更新する作業を行っている間に、多くの人気のあるゲームのためのカスタムコントローラーバインドを蒸気に提供しています。 "SteamVR 用の Windows Mixed Reality" がバージョン1.2.444 に完全に更新されているので、これらのバインドはゲームの実行中に自動的に選択されます。 ただし、この時点でゲームがアクションを登録していないと思われる場合は、SteamVR 設定メニューを使用して、カスタムバインドプロファイルを手動で検索できます。
目的

- 右のモーションコントローラーのメニューボタンを押して、SteamVR メニューを開きます。
- SteamVR メニューの右下隅にある [設定] アイコンを選択します。
- [コントローラー] タブを選択します。
- [コントローラーバインドの管理] オプションを選択します。

ここでは、アクティブコントローラーのバインドを "Custom" に変更することができます。これにより、コミュニティ共有ゲームバインドを試すオプションが開きます。
このゲームでカスタムゲームのバインドがまだ共有されていない場合 (または、試してみたものが完全に満たされていない場合) は、独自のカスタムゲームバインドを作成して、少数のゲームセッション後に共有することで、コミュニティの他の部分にも役立ちます。