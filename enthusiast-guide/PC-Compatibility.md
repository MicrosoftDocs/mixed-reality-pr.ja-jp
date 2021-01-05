---
title: Windows Mixed Reality PC チェックアプリ
description: Windows mixed reality ヘッドセットを購入する前に、Windows Mixed Reality PC チェックアプリを検索して使用し、PC の互換性をテストする方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、互換性、互換性、PC、システム要件
appliesto:
- Windows 10
ms.openlocfilehash: 6dc187b14950f1446fd5e60c3e6db10fd2c3ce25
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725433"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Windows Mixed Reality PC チェックアプリ

**[Windows Mixed REALITY Pc チェック](https://www.microsoft.com/store/p/windows-mixed-reality-pc-check/9nzvl19n7cnc)** アプリは、Pc が Windows mixed reality を実行する準備ができているかどうかを確認するための最適な方法です。 Windows Mixed Reality PC チェックアプリは、Windows 10 バージョン1607以降がインストールされている Pc でのみ機能します。 Windows のバージョンを確認するには、検索バーに「winver」と入力し、コマンドを実行します。 1607より前のバージョンの Windows では、アプリはストアに引き続き表示されますが、をインストールしようとするとエラーが発生します。

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

アプリを実行すると、次のいずれかのメッセージが表示されます。

* **これで問題ありません。** PC には、Windows Mixed Reality を実行するために必要なものがあります。
* **近くにあります。** この PC は Windows Mixed Reality を実行できますが、一部の機能が制限される場合があります。
* **Mixed reality を実行できません。** この PC は、Windows Mixed Reality を実行するために必要な最小要件を満たしていません。

次に、必要なハードウェア、ドライバー、およびオペレーティングシステムに対して PC の分析を行います。
![Windows Mixed Reality PC チェックのスクリーンショット](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>アイコン</th><th>意味</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">必要な項目が PC から渡されます。</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">指定された要件に応じて、PC に問題がある可能性があります。 何らかの問題が発生した場合は、トラブルシューティングまたは PC のアップグレードが必要になることがあります。</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">指定された項目の要件を PC が満たしていません。</td>
</tr>
</table>

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>Windows Mixed Reality PC チェックの結果に関するヘルプを表示する

Windows Mixed Reality をセットアップするか、コンピューターで Windows Mixed Reality PC 確認アプリを実行すると、互換性レポートが表示されます。 ここでは、表示される内容について詳しく説明します。

### <a name="youre-good-to-go"></a>![お待ちください](images/glyph-succeeded.png)

すばらしいニュース: PC で Windows Mixed Reality を実行できます。 コンピューターのハードウェアと構成の間には引き続き変化があることに注意してください。 すべての PC で mixed reality エクスペリエンスが同じであるとは限りません。

>[!NOTE]
>"このハードウェア構成は Windows Mixed Reality で動作する可能性がありますが、まだテストされていません" というメッセージが表示された場合は、Windows Mixed Reality を長時間セッションに対して実行すると、パフォーマンスの問題が発生する可能性があります。

### <a name="youre-nearly-there"></a>![近くにいます](images/glyph-warning.png)

お使いの PC では、Windows Mixed Reality を実行できますが、最適なエクスペリエンスが得られない場合があります。 グラフィックスは遅れる可能性があり、一部のアプリとゲームは正常に動作しない可能性があります。

表示される可能性があるメッセージとその対処方法を次に示します。

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>この PC には、シングルチャネル RAM を備えた統合グラフィックスカードが搭載されています。

統合グラフィックスカードは、デュアルチャネル RAM を搭載した Pc で、最適な Windows Mixed Reality エクスペリエンスを提供します。 パフォーマンスの問題が発生する場合は、次のようにします。

* 互換性の [ある独立したグラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)をインストールします。
* 追加の RAM スティックを取り付けて、デュアルチャネル RAM を作成します。
* 互換性のある [PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)に切り替えます。

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>この PC には、互換性のない PCIe リンクを備えたハイブリッドグラフィックス構成があります

PCIe は、 *周辺コンポーネントの相互接続 Express* を表します。 これは、グラフィックスカードとの通信に PC が使用する接続です。 構成が機能する場合もありますが、問題が発生した場合は、互換性のある [PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)に切り替える必要があります。

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>この PC のグラフィックドライバーは、Windows Mixed Reality では正しく機能しない可能性があります

問題が発生した場合は、Windows Update を使用して新しいグラフィックスドライバーをダウンロードしてみてください ([**> 設定の開始] > & セキュリティ > 更新プログラムを確認** してください)。または、PC の製造元またはグラフィックスカードの製造元の web サイトにアクセスしてください。

それでもうまくいかない場合は、互換性のある [グラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) を追加するか、互換性のある [PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)に切り替える必要があります。

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>この PC のプロセッサは、Windows Mixed Reality では正しく機能しない可能性があります

この PC のプロセッサは、十分なコアがないため、Windows Mixed Reality ではうまく機能しない可能性があります。 Windows Mixed Reality が正常に動作しない場合は、互換性のある [もの](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) に更新するか、互換性のある [PC](https://www.microsoft.com/windows/windows-mixed-reality-devices)に切り替えます。

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>この PC は、互換性のある USB 構成を持っていない可能性があります

Windows Mixed Reality の実行で問題が発生する場合は、次のようにします。

* 使用可能な場合は、別の USB ポートにヘッドセットを接続します。
* それでもうまくいかない場合は、PC の現在の USB ドライバーをアンインストールしてから、Microsoft ドライバーを再インストールします。

1. [ **スタート**] を選択し、検索ボックスに **「デバイスマネージャー」** と入力します。
1. 結果から [ **デバイスマネージャー** ] を選択します。
1. ユニバーサルシリアルバスコントローラーのカテゴリを展開し、一覧表示されているデバイスを確認して、互換性のないドライバーをアンインストールします。 
 * デバイス名の末尾に "Microsoft" がない "拡張可能なホストコントローラー" 項目が一覧に含まれている場合、ドライバーは Windows Mixed Reality と互換性がありません。 アンインストールする必要があります。 ドライバーをアンインストールするには、一覧でデバイスを右クリックし、[ **デバイスのアンインストール**] を選択します。 [ **このデバイスのドライバーソフトウェアを削除** する] チェックボックスをオンにし、[ **アンインストール**] を選択します。
 * 名前に "Etron" を含む "拡張可能なホストコントローラー" 項目が一覧に含まれている場合、その USB コントローラーは Windows Mixed Reality と互換性がありません。 PC で別の USB ポートを使用するか、別の USB 3.0 ホストコントローラーを購入する必要があります。
1. PC を再起動します。 
1. デバイスマネージャーに戻り、拡張可能なホストコントローラーの項目をもう一度見つけます。 デバイス名の末尾に "Microsoft" が表示されている場合は、これで問題ありません。 インストールされていない場合は、アンインストールの手順を繰り返して、Microsoft 以外の他のバージョンのドライバーを削除します。
* それでもうまくいかない場合は、PCIe USB カードを PC に追加します。

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>この PC には、コントローラー用の Bluetooth 4.0 が搭載されていません。

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>この PC には、自己給電型の USB ポートがありません。

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>この PC は動作しますが、高パフォーマンスの Intel®プロセッサで最高のエクスペリエンスを得られます。

### <a name="cant-run-mixed-reality"></a>![Mixed reality を実行できません](images/glyph-error.png)

 [Windows Mixed Reality PC チェックの結果に関するヘルプを表示する](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
