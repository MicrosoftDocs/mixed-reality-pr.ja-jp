---
title: Windows Mixed Reality における PC の互換性に関するヘルプを表示する
description: Windows Mixed Reality を使用する場合の PC 互換性の問題に関するヘルプリソース。
author: hferrone
ms.author: v-hferrone
ms.date: 01/07/2021
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、フィードバック、フィードバックハブ、バグ
appliesto:
- Windows 10
ms.openlocfilehash: a3d8c21a6f9f94cbecca81915145603588e468ff
ms.sourcegitcommit: e944f24d2deb4433865cc8f6fd9305d6d9676f48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97971901"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Windows Mixed Reality における PC の互換性に関するヘルプを表示する

Windows Mixed Reality を設定している場合、または [Mixed Reality ポータル](install-windows-mixed-reality.md)を使用している場合は、PC がタスクに依存しているかどうかに関するレポートが表示されます。 以下のセクションでは、特定の詳細について詳しく説明しています。

先に進む前に、以下の最も一般的な修正を試してください。 

> [!div class="checklist"]
> * コンピューターが[PC ハードウェアの最小互換性要件](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)を満たしていることを確認します。
> * [グラフィックスカードとプロセッサ](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)に互換性があることを確認する
> * 推奨される [アダプター](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) の一覧を確認する
> * [> の設定の開始] を選択してグラフィックドライバーを更新し、 **& セキュリティ > 更新プログラムを確認 >** 更新します。 

連絡先にアクセスする場合は、 [コミュニティ](https://answers.microsoft.com)に問い合わせるか、サポートに [問い合わせる](https://support.microsoft.com/contactus/)か、 [トラブルシューティング](troubleshooting-windows-mixed-reality.md) 情報を参照してください。

## <a name="youre-good-to-go"></a>お待ちください

良いニュースが表示 **された** 場合は、PC で Windows Mixed Reality を実行できます。 コンピューターのハードウェアと構成の間には変化があるため、すべての PC で Mixed Reality エクスペリエンスが同じであるとは限りません。

## <a name="supports-some-features"></a>一部の機能をサポート

"機能の一部を **サポート** " というメッセージが表示されている場合は、一部の Windows Mixed Reality エクスペリエンスを PC で実行できますが、最適なエクスペリエンスが得られない可能性があります。 欠点としては、遅れているグラフィックス、パフォーマンスヒット、および実行できないアプリケーションやゲームがあります。 次のようなメッセージが表示されます。

* [この PC には、シングルチャネル RAM を備えた統合グラフィックスカードが搭載されています。](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [この PC には、互換性のない PCIe リンクを備えたハイブリッドグラフィックス構成があります](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [この PC のグラフィックドライバーは、Windows Mixed Reality では正しく機能しない可能性があります](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [この PC のプロセッサは、Windows Mixed Reality では正しく機能しない可能性があります](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [この PC は、互換性のある USB 構成を持っていない可能性があります](#this-pc-might-not-have-a-compatible-usb-configuration)
* [この PC には、コントローラー用の Bluetooth 4.0 がありません](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [ヘッドセットによっては、モーションコントローラーを使用するために Bluetooth アダプターが必要になる場合があります。](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [この PC には、自己供給型の USB ポートがありません](#this-pc-doesnt-have-a-self-powered-usb-port)
* [この PC のグラフィックスカードは Windows Mixed Reality では動作しません](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [この PC のグラフィックドライバーは、Windows Mixed Reality では動作しません。](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [この PC のプロセッサは、Windows Mixed Reality では動作しません。](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [この PC には、Windows Mixed Reality を実行するのに十分な空きディスク領域がありません](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [この PC は、Windows Mixed Reality をサポートしていない Windows のエディションを実行しています](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [この PC では最新バージョンの Windows 10 が実行されていません](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [この PC には USB 3.0 ポートがありません](#this-pc-has-no-usb-30-port)
* [リモートデスクトップでこのアプリを実行することはできません](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>この PC には、シングルチャネル RAM を備えた統合グラフィックスカードが搭載されています。

統合グラフィックスカードは、デュアルチャネル RAM を搭載した Pc で、最適な Windows Mixed Reality エクスペリエンスを提供します。 パフォーマンスの問題が発生する場合は、次のようにします。

> [!div class="checklist"]
> * 互換性の[ある独立したグラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)をインストールする
> * 追加の RAM スティックを取り付けてデュアルチャネル RAM を作成する
> * 互換性のある[PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)に切り替える

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>この PC には、互換性のない PCIe リンクを備えたハイブリッドグラフィックス構成があります

PCIe は、PC がグラフィックスカードとの通信に使用する接続である *周辺コンポーネントの相互接続 Express* を表します。 構成が機能する場合もありますが、問題が発生した場合は、 [互換性](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)のある PC に切り替える必要があります。

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>この PC のグラフィックドライバーは、Windows Mixed Reality では正しく機能しない可能性があります

Windows Update を使用して新しいグラフィックスドライバーをダウンロードしてみてください。

> [!div class="checklist"]
> * [ **> の設定の開始] を選択して & セキュリティ > 更新プログラムを確認** するか、PC またはグラフィックスカードの製造元の web サイトに移動 > ます。
> * [更新プログラムをチェックする](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

それでもうまくいかない場合は、次のことを行う必要があります。

> [!div class="checklist"]
> * 互換性の[あるグラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)を追加する 
> * 互換性のある[PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)に切り替える

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>この PC のプロセッサは、Windows Mixed Reality では正しく機能しない可能性があります

十分なコアがないため、Windows Mixed Reality では PC のプロセッサがうまく機能しない可能性があります。 Windows Mixed Reality が正常に実行されない場合は、次のようになります。

> [!div class="checklist"]
> * プロセッサを互換性のある[もの](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)に置き換えます。 
> * 互換性のある[PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)に切り替える

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>この PC は、互換性のある USB 構成を持っていない可能性があります

Windows Mixed Reality の実行に関する問題:

> [!div class="checklist"]
> * 一般的な互換性の問題の解決策については、 [推奨されるアダプターのドキュメント](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) を参照してください。
> * [外部電源 USB ハブ](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)の使用を検討する

問題が引き続き発生する場合:

> [!div class="checklist"]
> * 使用可能な場合は、別の USB ポートにヘッドセットを接続します。
> * それでもうまくいかない場合は、PC の現在の USB ドライバーをアンインストールしてから、Microsoft ドライバーを再インストールします。

1. [ **スタート**] を選択し、 **検索** ボックスに「デバイスマネージャー」と入力します。
2. 結果から [ **デバイスマネージャー** ] を選択します。
3. ユニバーサルシリアルバスコントローラーのカテゴリを展開し、一覧表示されているデバイスを確認して、互換性のないドライバーをアンインストールします。
    * 一覧に、デバイス名の末尾に "Microsoft" がない "拡張可能なホストコントローラー" 項目が含まれている場合、そのドライバーは Windows Mixed Reality と互換性がありません。 アンインストールする必要があります。 ドライバーをアンインストールするには、一覧でデバイスを右クリックし、[ **デバイスのアンインストール**] を選択します。 [ **このデバイスのドライバーソフトウェアを削除** する] チェックボックスをオンにし、[ **アンインストール**] を選択します。
    * 名前に "Etron" を含む "拡張可能なホストコントローラー" 項目が一覧に含まれている場合、その USB コントローラーは Windows Mixed Reality と互換性がありません。 PC で別の USB ポートを使用するか、別の USB 3.0 ホストコントローラーを購入する必要があります。
4. PC を再起動します。
5. デバイスマネージャーに戻り、拡張可能なホストコントローラーの項目をもう一度見つけます。 デバイス名の末尾に "Microsoft" が表示されている場合は、これで問題ありません。 インストールされていない場合は、アンインストールの手順を繰り返して、Microsoft 以外のその他のバージョンのドライバーを削除します。

> [!div class="checklist"]
> * それでもうまくいかない場合は、PCIe USB カードを PC に追加します。

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>この PC には、コントローラー用の Bluetooth 4.0 がありません

2018およびそれ以降の Windows Mixed Reality ヘッドセットには既に Bluetooth が組み込まれていますが、古いヘッドセットを使用している場合は、Mixed reality モーションコントローラーに bluetooth 4.0 が必要です。 [Windows Mixed Reality を Xbox コントローラー](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset)、[マウス、キーボード](https://docs.microsoft.com/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse)、または[USB Bluetooth アダプター](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)と共に使用して、モーションコントローラーを PC に接続することもできます。 [推奨されるアダプターの表示](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>ヘッドセットによっては、モーションコントローラーを使用するために Bluetooth アダプターが必要になる場合があります。

一部のヘッドセットは Bluetooth を内蔵しているため、コントローラーはヘッドセットに直接ペアリングできます。 また、モーションコントローラーを使用するには、PC (または別のドングル) に Bluetooth ラジオが必要です。 詳細については、 [推奨されるアダプター](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters) に関するページを参照してください。

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>この PC には、自己供給型の USB ポートがありません

Windows Mixed Reality ヘッドセットに接続するには、自己供給型の USB 3.0 ポートが必要です。 電源が [入っている USB 3.0 ハブ](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) を PC に接続し、それを使用してヘッドセットを接続します。

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>この PC のグラフィックスカードは Windows Mixed Reality では動作しません

この PC のグラフィックスカードは、Windows Mixed Reality と互換性がありません。 次のことを行う必要があります。

> [!div class="checklist"]
> * 互換性の[あるグラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)を追加する 
> * 互換性のある[PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)に切り替える

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>この PC のグラフィックドライバーは、Windows Mixed Reality では動作しません。

この PC のグラフィックドライバーは、Windows Mixed Reality では動作しません。 Windows Update を使用して新しいグラフィックスドライバーをダウンロードしてみてください。

> [!div class="checklist"]
> * [ **> の設定の開始] を選択して & セキュリティ > 更新プログラムを確認** するか、PC またはグラフィックスカードの製造元の web サイトに移動 > ます。
> * [更新プログラムをチェックする](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

それでもうまくいかない場合は、次のことを行う必要があります。

> [!div class="checklist"]
> * 互換性の[あるグラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)を追加する 
> * 互換性のある[PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)に切り替える

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>この PC のプロセッサは、Windows Mixed Reality では動作しません。

この PC のプロセッサは、AVX/Popcnt 命令をサポートしていません。 Windows Mixed Reality を実行するには、次のことを行う必要があります。

> [!div class="checklist"]
> * [互換性のあるグラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)で置き換える 
> * 互換性のある[PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)に切り替える

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>この PC には、Windows Mixed Reality を実行するのに十分な空きディスク領域がありません

Windows Mixed Reality では、セットアップと最高のパフォーマンスを実現するために 10 GB の空きディスク領域が必要です。 ドライブの空き領域を増やしてから、最初からもう一度セットアップを実行してください。

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>この PC は、Windows Mixed Reality をサポートしていない Windows のエディションを実行しています

Windows Mixed Reality は、 [windows 10 Home](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab) と [windows 10 Pro](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab)で動作します。 Windows Mixed Reality を使用するには、これらのエディションのいずれかをインストールする必要があります。

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>この PC では最新バージョンの Windows 10 が実行されていません

Windows Mixed Reality では、Windows 10 の秋の作成者の更新プログラムが必要です。 [PC を更新](https://support.microsoft.com/help/4028685) して、もう一度やり直してください。

### <a name="this-pc-has-no-usb-30-port"></a>この PC には USB 3.0 ポートがありません

Windows Mixed Reality ヘッドセットを接続するには、USB 3.0 ポートが必要です。 デスクトップ PC を使用している場合は、PCIe USB カードを追加します。 ラップトップの場合は、互換性のある [PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)に切り替える必要があります。

### <a name="you-cant-run-this-app-via-remote-desktop"></a>リモートデスクトップでこのアプリを実行することはできません

Windows Mixed Reality を使用するには、モニターが接続されている PC が必要です。 バーチャルマシンを使用している場合、またはモニターがない場合は、仮想ディスプレイアダプタを使用してみてください。 これは、PC の DisplayPort に接続し、コンピューターのディスプレイをエミュレートするデバイスです。

## <a name="getting-the-best-performance"></a>最高のパフォーマンスを得る

一部のハードウェア構成では、Windows Mixed Reality でパフォーマンスの問題が発生する可能性があります。 読み込み速度の低下、ビジュアルの途切れ、または画質の低下などの問題については、次の一般的な修正を試してください。

* PC デスクトップで実行されている開いているアプリを終了します
* USB-C または DisplayPort を HDMI アダプターとして使用している場合は、別のアダプターを試してみてください。 推奨されるアダプターの表示
* PC のグラフィックスカードに追加のモニターが接続されている場合は、切断します。
* いくつかの異なる mixed reality アプリを Windows ストアからダウンロードしてみてください。コンピューターのセットアップによって、機能が向上する場合があります。
* [パフォーマンスに関する質問のドキュメント](performance-questions.md)を確認する

パフォーマンスの問題が解決しない場合は、次の [Windows Mixed Reality](set-up-windows-mixed-reality.md) 設定を更新して、最適なユーザーエクスペリエンスを実現します。

* エクスペリエンス
* 解決方法
* フレームレート
* 調整

> [!NOTE]
> "このハードウェア構成は Windows Mixed Reality で動作する可能性がありますが、まだテストされていません" というメッセージが表示された場合は、Windows Mixed Reality を長時間セッションに対して実行すると、パフォーマンスの問題が発生する可能性があります。

## <a name="working-with-steamvr"></a>SteamVR の使用

SteamVR からゲームを楽しむことは、すべての VR が提供するすべての機能を体験するための優れた方法です。 ただし、イマーシブデバイスから [最適なパフォーマンスを得](performance-questions.md) られるようにする必要があります。 [ストリーム](https://store.steampowered.com/about)をインストールした後:

* [Windows Mixed Reality で SteamVR を使用する](using-steamvr-with-windows-mixed-reality.md)手順に従います。
* [Steamvr パフォーマンステスト](https://store.steampowered.com/app/323910/SteamVR_Performance_Test)アプリをインストールする

## <a name="next-vr-checkpoint"></a>次の VR チェックポイント

これまでに説明した VR の旅に従うと、デバイスを購入する準備ができています。 ここでは、チェックポイントを購入する前に、次の手順に進むことができます。

> [!div class="nextstepaction"]
> [購入に関する Faq](before-you-buy-faqs.md)

または、[作業の開始] セクションに直接移動します。

> [!div class="nextstepaction"]
> [Windows Mixed Reality のセットアップ](set-up-windows-mixed-reality.md)

いつでも、いつでも [VR](vr-journey.md) に戻ることができます。