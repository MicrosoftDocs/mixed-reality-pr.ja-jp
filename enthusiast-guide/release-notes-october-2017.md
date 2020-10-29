---
title: リリース ノート - 2017 年 10 月
description: Windows 10 秋の作成者の更新プログラム (2017 年10月) の windows Mixed Reality リリースノート。
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: リリースノート、バージョン、windows 10、ビルド、rs3、os
ms.openlocfilehash: 58980c2efc3e3a213f2b84993adea8455b5a8919
ms.sourcegitcommit: 838bebf6bacac4047feff493c0847d4e6371976f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2020
ms.locfileid: "91784036"
---
# <a name="release-notes---october-2017"></a>リリース ノート - 2017 年 10 月

Windows Mixed Reality をご利用いただき、ありがとうございます。 Windows 10 の作成者の **[更新プログラム](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** のリリースでは、新しい [windows mixed reality イマーシブヘッドセット](https://docs.microsoft.com/windows/mixed-reality/discover/immersive-headset-hardware-details) と [モーションコントローラー](https://docs.microsoft.com/windows/mixed-reality/design/motion-controllers)のサポートが導入されています。これにより、 [windows mixed reality 対応 PC](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)に接続しているときに、新しいワールドを探索し、VR ゲームをプレイし、イマーシブエンターテインメントを体験することができます。

Windows Mixed Reality ヘッドセットとモーションコントローラーのリリースは、大規模なチーム工数の概念であり、 [Microsoft HoloLens](https://docs.microsoft.com/windows/mixed-reality/hololens-hardware-details)を含む[windows mixed reality プラットフォーム](https://docs.microsoft.com/windows/mixed-reality/discover/mixed-reality)の主要な手順です。 HoloLens は Windows 10 のリリースの更新プログラムを受信していませんが、HoloLens での作業が停止していないことを確認してください。Windows Mixed Reality 全体にわたって最近の作業から適用できる学習と洞察が多数用意されています。 実際、Windows Mixed Reality のイマーシブヘッドセットとモーションコントローラーは、同じ Api、ツール、および概念が両方に適用されるため、HoloLens の開発にも優れたエントリポイントとなります。

各デバイスの最新リリースに更新するには、 **設定** アプリを開き、[ **update & Security** ] にアクセスして、[ **更新プログラムの確認** ] ボタンを選択します。 Windows 10 PC では、windows [media 作成ツール](https://www.microsoft.com/software-download/windows10)を使用して、windows 10 の秋の作成者の更新プログラムを手動でインストールすることもできます。

 **デスクトップの最新リリース:** Windows 10 Desktop 10 月 2017 ( **10.0.16299.15** 、Windows 10 フォール作成者更新)<br>
 **HoloLens の最新リリース:** [Windows 10 Holographic 8 月 2016](release-notes-august-2016.md) ( **10.0.14393.0** 、windows 10 記念日更新)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Windows Mixed Reality の概要

Windows 10 の秋の作成者の更新プログラムでは、windows Mixed Reality ヘッドセットとモーションコントローラーのサポートに加えて、世界初の空間オペレーティングシステムにも対応しています。 主な特徴を次に示します。
* **[さまざまなヘッドセット](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)** -Windows Mixed Reality は、パートナーがさまざまなヘッドセットを提供できるようにします。これは、$399 米ドルで開始され、モーションコントローラーにバンドルされています。
* **[モーションコントローラー](https://docs.microsoft.com/windows/mixed-reality/design/motion-controllers)** -Windows Mixed Reality モーションコントローラーは、Bluetooth を使用して PC とワイヤレスでペアリングされます。また、6度の自由度の追跡、豊富な入力方法、および imus 機能を利用できます。
* **[簡単なセットアップと移植性](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)** -10 分以内にセットアップして開始します。 イマーシブヘッドセットでは、クロスアウトトラッキングを使用して、6つの自由度で、移動とモーションコントローラーを追跡します。 外部カメラまたは lighthouse マーカーは不要です。
* より **[広範な pc のサポート](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)** -Windows Mixed Reality を使用すると、より多くの人が以前よりも多くの人にデスクトップ VR を提供できるようになり、$499 米ドルからの統合グラフィックスカードと pc の選択がサポートされるようになります。
* **[Windows Mixed Reality ホーム](https://docs.microsoft.com/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)** -世界初の空間オペレーティングシステムは、2d アプリを使用したマルチタスク、VR ゲームとアプリの起動、および装飾型のホログラムの配置を行うための使い慣れたホーム環境を提供します。
* **[Microsoft Store 内のすばらしい VR ゲームとアプリ](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)** -Hulu VR や360ビデオなどのイマーシブエンターテインメントから SUPERHOT VR やアリゾナ陽などのエピックゲームまで、Microsoft Store は Windows Mixed Reality のさまざまなコンテンツを提供しています。
* **[Steamvr 早期アクセス](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)** -windows 10 の秋の作成者の更新プログラムにより、Windows mixed reality ヘッドセットとコントローラーで SteamVR タイトルを再生できるようになり、Windows mixed reality ユーザーが使用できる VR タイトルの最大のカタログが作成されます。

## <a name="known-issues"></a>既知の問題

Windows Mixed Reality エクスペリエンスの向上に努めていましたが、まだいくつかの既知の問題を追跡しています。 他のユーザーが見つかった場合は、フィードバックをお [送り](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback)ください。

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality ホームのデスクトップアプリ
* Snipping tool はデスクトップアプリでは機能しません。
* デスクトップアプリでは、再起動時に設定が保持されません。
* デスクトップで Mixed Reality ポータルプレビューを使用している場合、Windows Mixed Reality ホームでデスクトップアプリを開くと、無限のミラー効果に気付くことがあります。 
* デスクトップアプリを実行すると、非 Ultra Windows Mixed Reality Pc でパフォーマンスの問題が発生する可能性があります。推奨されません。  
* デスクトップ上の非表示のウィンドウにフォーカスがあるため、デスクトップアプリが自動起動することがあります。 
* デスクトップユーザーアカウント制御プロンプトでは、プロンプトが完了するまでヘッドセットが黒く表示されます。

### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality セットアップ
* ヘッドセットが接続された状態で Windows をセットアップすると、PC モニターが空白になることがあります。 ヘッドセットを抜いて、Windows セットアップを完了するために PC モニターに出力できるようにします。
* 境界を作成すると、トレースが失敗する場合があります。 その場合は、システムによって時間の経過に伴う領域の詳細が表示されるので、もう一度やり直してください。
* Windows Mixed Reality のセットアップ中に Cortana をオンまたはオフにした場合、この変更はデスクトップの Cortana 設定に適用されます。
* ヘッドホンが接続されていない場合は、Windows Mixed Reality ホームに初めてアクセスすると、追加のヒントが表示されないことがあります。
* Bluetooth ヘッドホンでは、モーションコントローラーとの干渉が発生する可能性があります。 Windows Mixed Reality セッション中に、Bluetooth コントローラーのペアリングまたは電源切断をお勧めします。

### <a name="games-and-apps-from-windows-store"></a>Windows ストアからのゲームとアプリ
* Forza Motorsports 6 など、グラフィカルに集中しているゲームの中には、Windows Mixed Reality で再生する場合に、あまり利用できない Pc でパフォーマンスの問題が発生する可能性があります。

### <a name="audio"></a>オーディオ
* 前述のように、Bluetooth オーディオ周辺機器は、Windows Mixed Reality の音声と空間サウンドエクスペリエンスでは適切に機能しません。 また、モーションコントローラーのエクスペリエンスに悪影響を及ぼすこともあります。 Windows Mixed Reality では、Bluetooth オーディオヘッドセットを使用しないことをお勧めします。
* デバイスが装着されていない場合、オーディオ再生用にヘッドセットに接続されている (またはその一部である) オーディオデバイスを使用することはできません。 オーディオヘッドセットが1つしかない場合は、オーディオヘッドセットをヘッドセットではなくホスト PC に接続することをお勧めします。 その場合は、[ **Settings**  >  **Mixed Reality**  >  **オーディオと音声** の設定] の [ヘッドセットオーディオに切り替える] をオフにする必要があります。
* SteamVR を通じて起動されたアプリケーションの多くを含む一部のアプリケーションは、混合の現実のポータルを開始または停止したときにオーディオデバイスが変更されたときにオーディオを紛失したりハングしたりすることがあります。 この問題を解決するには、Mixed Reality ポータルアプリを開いた後でアプリを再起動してください。
* Windows Mixed Reality ヘッドセットを使用する前に、ホスト PC で Cortana が有効になっている場合は、Windows Mixed Reality ホームの周囲に配置するアプリに適用される空間サウンドシミュレーションが失われる可能性があります。 回避策は、コンピューターに接続されているすべてのオーディオデバイスで、ヘッドセット接続されたオーディオデバイスでも、"ヘッドホン用の Windows Sonic" を有効にすることです。
   1. デスクトップタスクバーのスピーカーアイコンを左クリックし、[オーディオデバイス] の一覧から選択します。
   2. デスクトップタスクバーのスピーカーアイコンを右クリックし、[スピーカーのセットアップ] メニューの [ヘッドホン用 Windows] を選択します。
   3. すべてのオーディオデバイス (エンドポイント) に対して、この手順を繰り返します。
>[!NOTE]
> - ヘッドセットに接続されているヘッドホン/スピーカーは、装着していないと表示されません。そのためには、Windows Mixed Reality ホームのデスクトップアプリウィンドウでこの設定を行い、ヘッドセットに接続されている (またはヘッドセットに統合されている) オーディオデバイスにこの設定を適用する必要があります。
> - 別の方法とし **Settings**  >  ては、Windows Mixed Reality を起動する前に、デスクトップの **cortana** の設定で "cortana が cortana に応答できるようにする" をオフにすることもできます。

* 別のマルチメディア USB デバイス (web cam など) が Windows Mixed Reality ヘッドセットを使用して同じ USB ハブ (外部または PC 内) を共有している場合、まれに、ヘッドセットのオーディオジャック/ヘッドホンの音が少なくなったり、音声がまったくない場合があります。 ヘッドセットでこの問題を解決するには、他のデバイスと同じハブを共有しない USB ポートを使用するか、他の USB マルチメディアデバイスを切断/無効にします。
* まれに、ホスト PC の USB ハブが Windows Mixed Reality ヘッドセットに十分な電力を供給できず、ヘッドセットに接続されているヘッドホンからノイズが急増する場合があります。

### <a name="speech"></a>Speech
* Cortana は、コマンドに対する聞き取り/思考と音声応答のために、自分のオーディオキューを再生できない場合があります。
* 中国および日本市場の cortana では、使用中に Cortana サークルの下にテキストが正しく表示されません。
* Cortana は、Mixed Reality ポータルセッションで初めて呼び出されたときに、遅くなることがあります。 **Cortana と** cortana との  >  **Cortana**  >  **対話** が有効になっていることを確認することで、この問題を回避できます。
* Windows Mixed Reality ウルトラ Pc でない Pc では、Cortana の実行速度が低下する可能性があります。
* システムキーボードが Windows Mixed Reality の UI 言語とは異なる言語に設定されている場合、Windows Mixed Reality でキーボードからディクテーションを使用すると、Wi-fi 接続がないためにディクテーションが動作しないというエラーダイアログが表示されます。 この問題を解決するには、システムのキーボード言語が Windows Mixed Reality UI 言語と一致していることを確認するだけです。
* Windows Mixed Reality で音声が有効になっている市場として、スペインは正しく認識されていません。

### <a name="holograms"></a>ホログラム
* Windows Mixed Reality ホームに多数のホログラムが配置されている場合は、表示されているように見えなくなることがあります。 これを回避するには、Windows Mixed Reality ホームのその領域にあるホログラムの一部を削除します。

### <a name="motion-controllers"></a>モーション コントローラー
* 場合によっては、Edge の web ページをクリックすると、コンテンツがクリックではなくズームされます。
* エッジ内のリンクをクリックすると、選択内容が機能しなくなる場合があります。

## <a name="prior-release-notes"></a>以前のリリースノート
* [リリース ノート - 2016 年 8 月](release-notes-august-2016.md)
* [リリース ノート - 2016 年 5 月](release-notes-may-2016.md)
* [リリース ノート - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>関連項目
* [イマーシブヘッドセットのサポート (外部リンク)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens の既知の問題](https://docs.microsoft.com/windows/mixed-reality/hololens-known-issues)
* [ツールのインストール](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools)
* [フィードバックの送信](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback)
