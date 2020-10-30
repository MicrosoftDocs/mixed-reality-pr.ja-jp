---
title: HP リバーブ G2 Faq
description: HP リバーブ G2 ヘッドセットの使用に関してよく寄せられる質問
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート、パフォーマンス
appliesto:
- Windows 10
ms.openlocfilehash: 82f9accc8e24574faf7c826aff1908bea7350b08
ms.sourcegitcommit: feceb21018ce1d966188a34bd1faeddfdc1b9544
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93049474"
---
# <a name="hp-reverb-g2-frequently-asked-questions"></a>HP リバーブ G2 に関してよく寄せられる質問

## <a name="is-there-a-specific-order-i-should-follow-to-connect-my-headset-cables-to-a-pc"></a>ヘッドセットケーブルを PC に接続するために従うべき特定の順序はありますか。

HP は次のことを推奨します。

- PC または電源に接続する前に、まず6メートルのケーブルをヘッドセットに接続します。
- 最初のインストール後に、6メートルのケーブルをヘッドセットに接続したままにします。
- ヘッドセットが使用されていない場合は、電源アダプターを6メートルのケーブルから切断します。

## <a name="what-should-i-do-to-get-a-crisper-image"></a>鮮明なイメージを取得するにはどうすればよいですか。

表示が少しぼやけて見える場合は、いくつかの操作を試してみることができます。

- ヘッドセットが適切にヘッドに配置されていることを確認してください。
- IPD (interpupillary distance) の調整を試みます。 リバーブ G2 はハードウェア IPD を使用することに注意してください。 これを変更するには、ヘッドセットの IPD 調整を探します。
- グラスや連絡先が必要な場合でも必要です。
- レンズをクリーニングする必要があるかどうかを確認します (マイクロ fiber 布のみ–液体なし)。
- ヘッドセットの高度な設計により、Lcd がウォームアップできるようになるまで、デバイスを起動したとき、最初の数分間に軽微な画像が表示されることがあります。

## <a name="i-am-getting-a-7-14-something-went-wrong-error-when-i-plug-in-my-headset"></a>ヘッドセットに接続したときに 7-14 "問題が発生しました" というエラーが発生する

7-14 "問題が発生しました" というエラーが表示される場合は、次の手順を試してください。

- 最新のドライバーがインストールされていることを確認します。
- ケーブルを別の USB-3.0 ポートに接続してみてください。
- 別のポートを試すには、USB C を使用してアダプターを追加してください。

ケーブルを別の USB ハブに接続してみてください。  

> [!NOTE]
> HP では、リバーブ G2 デバイスを搭載したマザーボードに組み込まれている USB コントローラーのみを使用することをお勧めします。
> デバイスに接続できない場合は、 [HP サポート](https://support.hp.com/us-en)にお問い合わせください

## <a name="i-am-getting-a-13-14-something-went-wrong-error-when-my-pc-resumes-from-hibernate-s4"></a>PC が休止状態 (S4) から再開したときに、13-14 "問題が発生しました" というエラーが発生する

再開プロセス中に、ビデオカードが接続を確立できないことがあります。そのため、PC から USB タイプ C を取り外してから再び接続すると、接続の確立に役立ちます。

## <a name="the-mixed-reality-portal-says-cant-run-mixed-reality-on-this-headset-but-this-worked-fine-with-my-previous-wmr-headset"></a>Mixed Reality ポータルでは、"このヘッドセットでは mixed reality を実行できません" と表示されますが、これは以前の WMR ヘッドセットで問題なく動作しています。

これは、HP リバーブ G2 が最適なエクスペリエンスを実現するためにより強力な PC を必要とするために発生する可能性があります。 詳細については、「PC の最小[要件](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)」を参照してください。

## <a name="it-looks-like-my-left-display-is-stretched-and-the-right-display-is-off-centered-and-half-black"></a>左側の表示が拡大しているように見えますが、右の表示は中央から半分になります。

これは、ヘッドセットがネイティブの解像度で実行されていない場合に発生する可能性があります。 HP リバーブ G2 HMD の高解像度ディスプレイの性質により、すべてのシステムがネイティブの解像度をレンダリングできるわけではありません。 ヘッドセットがネイティブの解像度になっていない場合にレンダリングの問題に対処する、今後の Windows Update に修正プログラムが導入されています。

システムがネイティブの解決方法でレンダリングできない理由はいくつかあります。

- システム上の DisplayPort が1.3 と互換性がない場合や、4つのレーンがすべてサポートされていない場合があります。
- アダプターを使用している場合は、HBR3 との互換性がサポートされていないか、4つのレーンがすべてサポートされていない可能性があります。
- システムにハイブリッド GPU が搭載されている場合は、DisplayPort で使用可能な帯域幅を制限している可能性があります。

## <a name="why-are-my-hp-motion-controller-models-not-showing-up-correctly-in-a-game"></a>HP Motion Controller モデルがゲームで正しく表示されないのはなぜですか。

多くのゲームは HP Motion Controller ですぐに機能しますが、一部のゲームでは既存のコントローラー機能に依存しているため、いくつかの問題が発生する可能性があります。

- 間違ったモデルが表示されています: これを修正するにはゲームの更新が必要です。 通常、これはゲームのすべての機能をブロックするわけではありませんが、混乱や視覚的な成果物につながる可能性があります。
- タッチパッドへの依存関係、またはコントローラーの入力レイアウトでの一般的な関係。 SteamVR では、この種の問題を回避するために、カスタムバインドを作成できます。
    - SteamVR の Windows Mixed Reality には、一部のゲームのカスタムバインドが含まれています。 これらのバインドは、ゲームの開始時に自動的に使用され、ユーザーの操作は必要ありません。