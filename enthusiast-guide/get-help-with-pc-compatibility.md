---
title: Windows Mixed Reality における PC の互換性に関するヘルプを表示する
description: Windows Mixed Reality を使用する場合の PC 互換性の問題に関するヘルプリソース。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、フィードバック、フィードバックハブ、バグ
appliesto:
- Windows 10
ms.openlocfilehash: 75d8ade12d5534a1eb86f36bcdd590539a6811b5
ms.sourcegitcommit: 24d96bf3bb9a3143445e018195edae99d91684c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92683178"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Windows Mixed Reality における PC の互換性に関するヘルプを表示する

Windows Mixed Reality をセットアップするか、 [Windows Mixed REALITY Pc チェック](https://www.microsoft.com/p/windows-mixed-reality-pc-check/9nzvl19n7cnc?rtc=1#activetab=pivot:overviewtab) アプリをコンピューターで実行すると、pc で実行準備が整っているかどうかをレポートするレポートが作成されます。 ここでは、表示される内容について詳しく説明します。

Mixed Reality を確実に実行できるようにするには、 [PC ハードウェアの最小互換性要件](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)を確認してください。

## <a name="youre-good-to-go"></a>お待ちください

すばらしいニュース: PC で Windows Mixed Reality を実行できます。 しかし、コンピューターのハードウェアと構成の間には変化があることに注意してください。そのため、すべての PC で Mixed Reality エクスペリエンスが同じであるとは限りません。

## <a name="supports-some-features"></a>一部の機能をサポート

お使いの PC では、一部の Windows Mixed Reality エクスペリエンスを実行できますが、最適なエクスペリエンスが得られない場合があります。 グラフィックスが遅れる可能性があり、一部のアプリとゲームがうまく動作しない可能性があります。 

表示される可能性があるメッセージとその対処方法を次に示します。

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>この PC には、シングルチャネル RAM を備えた統合グラフィックスカードが搭載されています。

統合グラフィックスカードは、デュアルチャネル RAM を搭載した Pc で、最適な Windows Mixed Reality エクスペリエンスを提供します。 パフォーマンスの問題が発生した場合は、次のいずれかを試してください。

* 互換性の [ある独立したグラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)をインストールします。
* 追加の RAM スティックを取り付けて、デュアルチャネル RAM を作成します。
* 互換性のある [PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)に切り替えます。

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>この PC には、互換性のない PCIe リンクを備えたハイブリッドグラフィックス構成があります

PCIe は、 *周辺コンポーネントの相互接続 Express* を表します。 これは、グラフィックスカードとの通信に PC が使用する接続です。 構成が機能する場合もありますが、問題が発生した場合は、互換性のある [PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)に切り替える必要があります。

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>この PC のグラフィックドライバーは、Windows Mixed Reality では正しく機能しない可能性があります

問題が発生した場合は、Windows Update を使用して新しいグラフィックスドライバーをダウンロードしてみてください ([ **> 設定の開始] > & セキュリティ > 更新プログラムを確認** してください)。または、PC の製造元またはグラフィックスカードの製造元の web サイトにアクセスしてください。

> [!div class="nextstepaction"]
> [更新プログラムをチェックする](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

それでもうまくいかない場合は、互換性のある [グラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) を追加するか、互換性のある [PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)に切り替える必要があります。

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>この PC のプロセッサは、Windows Mixed Reality では正しく機能しない可能性があります

この PC のプロセッサは、十分なコアがないため、Windows Mixed Reality ではうまく機能しない可能性があります。 Windows Mixed Reality が正常に動作しない場合は、プロセッサを互換性のある [もの](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) に置き換えるか、互換性のある [PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)に切り替えます。

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>この PC は、互換性のある USB 構成を持っていない可能性があります

Windows Mixed Reality の実行で問題が発生した場合は、次の操作を試してください。

* 使用可能な場合は、別の USB ポートにヘッドセットを接続します。
* それでもうまくいかない場合は、PC の現在の USB ドライバーをアンインストールしてから、Microsoft ドライバーを再インストールします。

1. [ **スタート** ] を選択し、 **検索** ボックスに「デバイスマネージャー」と入力します。
2. 結果から [ **デバイスマネージャー** ] を選択します。
3. ユニバーサルシリアルバスコントローラーのカテゴリを展開し、一覧表示されているデバイスを確認して、互換性のないドライバーをアンインストールします。
    * 一覧に、デバイス名の末尾に "Microsoft" がない "拡張可能なホストコントローラー" 項目が含まれている場合、そのドライバーは Windows Mixed Reality と互換性がありません。 アンインストールする必要があります。 ドライバーをアンインストールするには、一覧でデバイスを右クリックし、[ **デバイスのアンインストール** ] を選択します。 [ **このデバイスのドライバーソフトウェアを削除** する] チェックボックスをオンにし、[ **アンインストール** ] を選択します。
    * 名前に "Etron" を含む "拡張可能なホストコントローラー" 項目が一覧に含まれている場合、その USB コントローラーは Windows Mixed Reality と互換性がありません。 PC で別の USB ポートを使用するか、別の USB 3.0 ホストコントローラーを購入する必要があります。
4. PC を再起動します。
5. デバイスマネージャーに戻り、拡張可能なホストコントローラーの項目をもう一度見つけます。 デバイス名の末尾に "Microsoft" が表示されている場合は、これで問題ありません。 インストールされていない場合は、アンインストールの手順を繰り返して、Microsoft 以外の他のバージョンのドライバーを削除します。

* それでもうまくいかない場合は、PCIe USB カードを PC に追加します。

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>この PC には、コントローラー用の Bluetooth 4.0 がありません

一部のヘッドセットでは、mixed reality モーションコントローラーには Bluetooth 4.0 が必要です。 Windows Mixed Reality は、Xbox コントローラーでもマウスやキーボードでも使用できます。また、USB Bluetooth アダプターを使用して、PC にモーションコントローラーを接続することもできます。 [推奨されるアダプターの表示](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>ヘッドセットによっては、モーションコントローラーを使用するために Bluetooth アダプターが必要になる場合があります。

一部のヘッドセットには Bluetooth が組み込まれているため、コントローラーはヘッドセットに直接ペアリングできます。 また、モーションコントローラーを使用するには、PC (または別のドングル) に Bluetooth ラジオが必要です。 [推奨されるアダプターの表示](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>この PC には、自己供給型の USB ポートがありません

Windows Mixed Reality ヘッドセットに接続するには、自己供給型の USB 3.0 ポートが必要です。 電源が入っている USB 3.0 ハブを PC に接続し、それを使用してヘッドセットを接続します。

### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>この PC は動作しますが、高性能の Intel®プロセッサを使用することをお勧めします。

この PC は動作しますが、高性能の Intel プロセッサが最適なエクスペリエンスを提供します。 Intel® Core™または7世代の intel® Core™ i5 プロセッサを8世代にすることをお勧めします。

## <a name="cant-run-windows-mixed-reality"></a>Windows Mixed Reality を実行できません

表示される可能性があるメッセージとその対処方法を次に示します。

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>この PC のグラフィックスカードは Windows Mixed Reality では動作しません

この PC のグラフィックスカードは、Windows Mixed Reality と互換性がありません。 互換性のある [グラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) または互換性のある [PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)へのスイッチを追加する必要があります。

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>この PC のグラフィックドライバーは、Windows Mixed Reality では動作しません。

この PC のグラフィックドライバーは、Windows Mixed Reality では動作しません。 Windows Update を使用して新しいグラフィックスドライバーをダウンロードしてみてください ([ **> 設定の開始] > & セキュリティ > 更新プログラムを確認** してください)。または、PC の製造元またはグラフィックスカードの製造元の web サイトにアクセスしてください。 

> [!div class="nextstepaction"]
> [更新プログラムをチェックする](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

それでもうまくいかない場合は、互換性のある [グラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) を追加するか、互換性のある [PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)に切り替える必要があります。

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>この PC のプロセッサは、Windows Mixed Reality では動作しません。

この PC のプロセッサは、AVX/Popcnt 命令をサポートしていません。 Windows Mixed Reality を実行するには、互換性のある [グラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) で置き換えるか、互換性のある [PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)に切り替える必要があります。

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>この PC には、Windows Mixed Reality を実行するのに十分な空きディスク領域がありません

Windows Mixed Reality では、セットアップと最高のパフォーマンスを実現するために 10 GB の空きディスク領域が必要です。 ドライブの空き領域を増やしてから、セットアップを再試行してください。

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>この PC は、Windows Mixed Reality をサポートしていない Windows のエディションを実行しています

Windows Mixed Reality は、Windows 10 Home と Windows 10 Pro で動作します。 Windows Mixed Reality を使用するには、これらのエディションのいずれかをインストールする必要があります。

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>この PC では最新バージョンの Windows 10 が実行されていません

Windows Mixed Reality では、Windows 10 の秋の作成者の更新プログラムが必要です。 [PC を更新](https://support.microsoft.com/help/4028685) して、もう一度やり直してください。

### <a name="this-pc-has-no-usb-30-port"></a>この PC には USB 3.0 ポートがありません

Windows Mixed Reality ヘッドセットを接続するには、USB 3.0 ポートが必要です。 デスクトップ PC を使用している場合は、PCIe USB カードを追加します。 ラップトップを使用している場合は、互換性のある [PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)に切り替える必要があります。

### <a name="you-cant-run-this-app-via-remote-desktop"></a>リモートデスクトップでこのアプリを実行することはできません

Windows Mixed Reality を使用するには、モニターが接続されている PC にします。 バーチャルマシンを使用している場合、またはモニターがない場合は、仮想ディスプレイアダプタを使用してみてください。 これは、PC の DisplayPort に接続し、コンピューターのディスプレイをエミュレートするデバイスです。 

## <a name="getting-the-best-performance"></a>最高のパフォーマンスを得る

一部のハードウェア構成では、Windows Mixed Reality でパフォーマンスの問題が発生する可能性があります。 読み込み速度の低下、ビジュアルの途切れ、または画質の低下などの問題については、次の一般的な修正を試してください。

* PC デスクトップで実行されている開いているアプリを終了します。
* USB-C または DisplayPort を HDMI アダプターとして使用している場合は、別のアダプターを試してみてください。 推奨されるアダプターの表示
* PC のグラフィックスカードに追加のモニターが接続されている場合は、切断します。
* Windows ストアからいくつかの異なる mixed reality アプリをダウンロードしてみてください。コンピューターのセットアップでは、いくつかの機能が強化される可能性があります。

> [!NOTE]
> "このハードウェア構成は Windows Mixed Reality で動作する可能性がありますが、まだテストされていません" というメッセージが表示された場合は、Windows Mixed Reality を長時間セッションに対して実行すると、パフォーマンスの問題が発生する可能性があります。

## <a name="see-also"></a>関連項目

* [コミュニティへの質問](https://answers.microsoft.com)
* [サポートについては、お問い合わせください](https://support.microsoft.com/contactus/)
* [トラブルシューティング](troubleshooting-windows-mixed-reality.md)