---
title: モーションコントローラーに関する Faq
description: コントローラー Windows Mixed Reality のトラブルシューティングは、標準のコンシューマーサポートドキュメントを超えています。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート、モーションコントローラー
appliesto:
- Windows 10
ms.openlocfilehash: 7d3cdae2e098504a755369e3c829c1d4a6142b9d
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132026"
---
# <a name="motion-controller-faqs"></a>モーションコントローラーに関する Faq

## <a name="what-do-the-vibrations-and-lights-mean"></a>Vibrations とライトの意味

LED 悪化リングと haptics は、モーションコントローラーの状態を示します。

| State    | 状態に関連付けられている動作 | 状態を取得または非表示にする方法 |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **電源投入**               | Led をオンにすると、コントローラーの vibrates が1回だけ表示されます。 | コントローラーの Windows ボタンを2秒間押したままにして、コントローラーの電源を入れます。  |
| **電源オフ**              |  Led をオフにして、コントローラーの vibrates を2回オフにします。 | コントローラーの Windows ボタンを4秒間押したままにして、コントローラーの電源をオフにします。   |
| **休止中**               |  Led は、スリープ状態のときに3秒ごとにオフにして点滅します。 | 30秒間 motionless されると、コントローラーはスリープ状態に自動的に入ります。 デバイスがホスト PC とペアリングされていない場合を除き、コントローラーは動作を検出するとスリープ状態を解除します。 その場合は、ボタンを押してスリープ解除します。 |
| **組み合わせる**                |  ペアリングモード中に Led の速度が低下し、ペアリングモードを終了すると、点灯します。 ペアリングが成功した場合、またはペアリングが失敗した場合は3回 vibrates、コントローラーは1回だけ実行されます。 | バッテリケース内のペアリングボタンを3秒間押したままにします。     |
| **コントローラーの接続/PC からの切断** |  コントローラーは、PC への接続または切断時に1回 vibrates ます。 | これは、コントローラーをオンにした後にコントローラーが正常に PC に接続したとき、またはコントローラーが使用中に PC から切断された場合に発生します。|
| **バッテリ低下のレベル**      | バッテリが少ない場合、Haptics は無効になります (LED が示されません)。 ヘッドセット内のコントローラーハンドルのバッテリインジケーターアイコンは、バッテリが少なくなったときに、1/4 がいっぱいになっていることを示します。 | バッテリを交換します。 | 
| **バッテリ切れのレベル** |  コントローラーは、電源をオンにすると3回 vibrates、自動的にオフになります。 バッテリインジケーターアイコンが赤に変わります。 | バッテリを交換します。 問題が引き続き発生する場合は、[デバイスを工場出荷時の設定に戻し](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)ます。|

## <a name="my-motion-controllers-arent-working-properly"></a>モーションコントローラーが正常に動作していません

[モーションコントローラー](controllers-in-wmr.md)が動作していない場合、接続されていない場合、またはヘッドセットを装着しているときにコントローラーのイメージが表示されない場合は、次の操作を試してください。

1. コントローラーの電源が入っていることを確認します。 有効にするには、Windows のボタンを2秒間押したままにします。
2. コントローラーが完全に充電されていることを確認し、バッテリがない場合は交換します。
3. コントローラーをオンにしたまま、再び手前に表示したままにします。 4秒間、Windows ボタンを押したままにして、コントローラーをオフにした後、2秒間押したままにしてオンにします。
4. モーションコントローラーが [正しくペアリング](controllers-in-wmr.md#pair-motion-controllers)されているかどうかを確認します。
5. モーションコントローラーの Led を確認します。照明照明のあるコントローラーがペアリングされ、接続されています。 dimly lit controller は接続されていません。
6. PC で [ **Start > Mixed Reality Portal** ] にアクセスし、[Menu] を選択します。 モーションコントローラーが、ステータスメッセージと共に表示されます。
    * [準備完了]: すべてのコントローラーが設定されています。
    * 失われた追跡– Mixed Reality ポータルがコントローラーを見つけることができません。 ヘッドセットの前に置いて、4秒間、もう一度2秒間、Windows のボタンを押して再起動します。
    * バッテリ低下-コントローラーのバッテリを交換します。
7. 外部 USB Bluetooth アダプターを使用している場合は、USB 2.0 ポートに接続されていることを確認します (多くの場合、常に黒ではありません)。 また、ヘッドセットの USB コネクタを含め、他のワイヤレス送信装置や USB フラッシュドライブから可能な限り遠くに接続する必要があります。 
8. PC に Bluetooth ラジオが1つしかないことを確認するには、[ **デバイスマネージャー > bluetooth** ] にアクセスし、1つのアダプターを探します。 組み込みのラジオでデスクトップ PC 構成を使用している場合は、外部アンテナが接続されているかどうかを確認します。 外部アンテナが接続されていない場合は、問題の追跡が発生する可能性があります。 または、外部 Bluetooth ドングル (USB) を使用して、Bluetooth の内部機能を無効にし、ペアリングと接続を再試行します。
9. Bluetooth 設定ウィンドウがバックグラウンドで開かれている場合は、Bluetooth プロトコルに多くの追加呼び出しが行われます。 この画面は閉じます。
10. コントローラーを mixed reality でオンにして、バッテリアイコンを表示することにより、モーションコントローラーの仮想バッテリレベルを確認します。 報告されるレベルがコントローラーの接続直後の実際のレベルよりも高いため、レベルを読み取る前に約15秒間待ちます。 アイコンが赤の場合は、バッテリを交換します。
11. [設定] で Bluetooth ヘッドホンとスピーカーを削除し、[ **bluetooth & 他のデバイス >** デバイスを > し、デバイスの電源をオフにします。 最適なオーディオエクスペリエンスを実現するために、mixed reality ヘッドセットでヘッドフォンジャックまたは内蔵スピーカーを使用します。
12. コンピューターとペアリングされている可能性のある他の Bluetooth デバイス (ヘッドホンやゲームパッドなど) を削除します。 [ **設定] > [Bluetooth & 他のデバイス] >** [デバイス] の順に選択し、デバイスを選択して、[デバイスの削除] をクリックします。
13. ヘッドセットの USB ケーブルを取り外し、PC に接続し直して Windows Mixed Reality を再起動します。
14. コントローラーライトは、ファームウェアの更新中にフラッシュされます。 更新が完了するのを待ち、コントローラーが Mixed Reality に表示されるようにします。
15. PC が 5GHz Wi-Fi ネットワークに接続されていることを確認します。 ラップトップが 2.4 GHz の Wifi ネットワークに接続されている場合、通常は Bluetooth 接続を共有します。 これは、製品の設計によっては、Wifi または Bluetooth のパフォーマンスに悪影響を及ぼす可能性があります。 ネットワークアダプターの設定で、優先するバンドを5GHz に変更します。 ネットワークで5GHz がサポートされていない場合は、bluetooth ドングルを内部 Bluetooth 機能の代わりに使用できます。
16. Bluetooth 設定が既にペアリングされている場合、新しいデバイスが取り外されるまで、Windows は新しいデバイスを検出しません (特定のドングルを使用して追加されている場合は、そのドングルでのみ削除できます)。
17. PC に Bluetooth が組み込まれていて、接続の問題が発生している場合は、USB Bluetooth アダプターを使用してみてください。 これを行うには、デバイスマネージャーで内蔵 Bluetooth ラジオをオフにしてから、他の Bluetooth デバイスを新しいアダプターとペアリングします。

## <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>コントローラーのジッター、行き詰まった、またはちらつきが混合現実に見えなくなる

* PC が 2.4 GHz の wifi で動作している場合は、5 GHz の wifi に切り替えます。 
* 外部 Bluetooth アダプターを使用している場合は、USB 2.0 ポートに接続されていることを確認します (多くの場合、常時ではありません)。他のワイヤレス送信装置や USB フラッシュドライブから離れています。
* Bluetooth のトラブルシューティングツールを実行して、[ **設定 > 更新] & セキュリティ >、bluetooth > のトラブルシューティング** を行います。

## <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>コントローラーが無限の再起動でスタックしている

これは重大なバッテリインジケーターです。 デバイスに新しい電池を入れます。問題が解決しない場合は、 [コントローラーを工場出荷時の設定に戻し](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)ます。

## <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>Mixed Reality ポータルは動作していますが、コントローラーの追跡が適切ではありません (飛行、シェイクなど)。

1. 照明条件は追跡に影響する可能性があります。 お客様が直接日光にさらされていないこと、および HMD に多数のポイントライトソースが表示されていないことを確認してください (たとえば、クリスマスツリーのような電球の文字列)。
2. これらの現象は、一般に、コントローラーとホスト PC 間の通信に失敗し、Bluetooth リンクの品質が低いことを示している場合に発生します。 [Bluetooth に関する質問](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)を参照してください。

## <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>モーションコントローラー Led は点灯していませんが、ボタンとサムスティックは Mixed Reality ポータルで引き続き動作します

モーションコントローラー調整のキャッシュが壊れている可能性があります。 キャッシュを削除するには、管理者のコマンドプロンプトで次のコマンドを実行します。

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

このフォルダーは、エクスプローラーではアクセスできず、管理者コマンドプロンプトからのみ変更できます。 フォルダーを削除したら、PC を再起動し、調整ファイルを復元するために、モーションコントローラーに再接続します。

## <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>コントローラーが Naopak/Oculus のように見えるか、奇妙な向きになっているか、ボタンが正しくマップされていません

多くの場合、web サイトはフルモーションコントローラーをサポートしていません。

## <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>マイモーションコントローラーが SteamVR アプリとゲームに表示されない

最初に、コントローラーのバッテリが充電されていることを確認します。 バッテリが故障したり起きしたりしても、コントローラーは機能しません。

お客様のコントローラーが、SteamVR アプリやゲームではなく、崖家に表示される場合は、モーションコントローラーモデルドライバーが正しくインストールされていない可能性があります。 モーションコントローラーモデルドライバーが正しくインストールされていることを確認するには、次のようにします。

1. 両方の動きコントローラーをオンにします。 モーションコントローラーが [正しくペアリング](controllers-in-wmr.md#pair-motion-controllers)されているかどうかを確認します。
2. **Bluetooth > デバイスマネージャー** に移動し、"Motion controller" を探します。
3. デバイスを選択し、[ **接続別のデバイスの表示** ] にアクセスして > ます。
4. [ **システム設定] [Bluetooth & 他** のデバイス > 他のデバイス] の順に >、表示されているかどうかを確認 > ます。 "Bluetooth HID デバイス" デバイスは2つあります。各 Bluetooth HID デバイスの下には、モーションコントローラーと同じノードに "Motion Controller" という名前のデバイス (灰色のアイコン) が付いている必要があります。
5. 各 "Motion Controller" デバイスをダブルクリックし、[ドライバー] タブに移動します。一覧表示されているドライバーのバージョンが、 [これらのバージョン](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history)のいずれかに対応していることを確認します。
6. インストールされていない場合は、Windows Update を実行します。これにより、ドライバーが自動的にダウンロードされ、インストールされます。 エンタープライズポリシーを持つ PC を使用している場合、または Windows Update が制限されている場合は、手動で motion controller モデルドライバーをインストールする必要があります。 これを行うには、 [このページ](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history) にアクセスして、使用している Windows 10 のバージョンに対応するドライバーのバージョンを探します。 インストール手順については、ダウンロードページを参照してください。

## <a name="the-controller-firmware-update-takes-significantly-longer-than-two-minutes"></a>コントローラーファームウェアの更新には2分以上かかる

[「Bluetooth の質問」セクション](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)を確認します。 Bluetooth リンクの品質が低いと、通常、これらの問題が発生します。

## <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>新しい電池を挿入しましたが、コントローラーのバーチャルバッテリレベルは完全なレベルを示していません

モーションコントローラーのバッテリレベルは、AA バッテリ用に調整されています。 一部の低電圧 rechargeable バッテリは、完全に充電されていても、完全として報告されない場合があります。

## <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>Samsung motion controller のタッチパッドがセンター外にあるか、または停止しています

これはハードウェアの不具合である場合があります。交換または交換のために、販売店または機器の製造元に戻る必要があります。

## <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>コントローラーを工場出荷時の設定に復元する方法はありますか

工場出荷時の状態に復元する (新しい電池が必要です):

1. コントローラーを取り外し、電源をオフにします。
2. バッテリカバーを開きます。
3. 新しい電池を挿入します。
4. ペアリングボタン (バッテリの下部にあるタブ) を押したままにします。
5. ペアリングボタンを押したまま、5秒間、Windows ボタンを押したままにして、コントローラーの電源を入れます (両方のボタンを押したままにします)。
6. ボタンを離して、コントローラーの電源がオンになるのを待ちます。 これには最大15秒かかり、デバイスの回復が行われているときのインジケーターはありません。 デバイスの電源がすぐにボタンのリリースになった場合、回復ボタンのシーケンスは登録されなかったため、もう一度試す必要があります。
7. コントローラーが PC とペアリングされている場合は、[ **設定] > > [その他のデバイス** ] を選択し、[モーションコントローラー] を選択し、[デバイスの削除] を選択して、bluetooth 設定からコントローラーの関連付けを削除します。
8. [コントローラーを](controllers-in-wmr.md#pair-motion-controllers) ヘッドセットまたは PC とペアリングし直します。
9. ホストとヘッドセットを使用して接続した後、デバイスは利用可能な最新のファームウェアに更新されます。

## <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>Xbox コントローラーをヘッドセットで使用できるように、自分の PC にペアリングすることはできますか。

[次の手順](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues)に従うと、Bluetooth Xbox コントローラーをペアリングしてヘッドセットで使用することができます。

ワイヤード (有線) Xbox コントローラーがある場合は、PC に接続します。

一部のゲームとアプリは、混合現実で使用されるものとは異なる方法で Xbox コントローラーを使用します。 ゲームまたはアプリにコントローラーを使用するには、アプリバーで [ゲームパッドとして使用する] または [ゲームパッドとして使用する] を選択します。 コントローラーを mixed reality に戻すには、もう一度 [ゲームパッドとして使用する] を選択するか、[使用との併用] を選択します。 

## <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Windows Mixed Reality が既に PC にセットアップされている場合は、新しいコントローラーを操作方法します。

コントローラーをヘッドセットにペアリングする場合は、コンパニオンアプリを使用してください ( [Mixed Reality ポータル](install-windows-mixed-reality.md#launch-mixed-reality-portal) は、起動するコンパニオンアプリを見つけたり、選択できるコンパニオンアプリの一覧を提供したりするのに役立ちます)。

## <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>コントローラーを工場出荷時のペアリングに戻す方法はありますか

モーションコントローラーを工場出荷時のペアリングに戻す、または内蔵 Bluetooth ラジオを使用して Windows Mixed Reality ヘッドセットとペアリングするには、ヘッドセットのデバイスコンパニオンアプリを実行します (たとえば、"Acer OJO 500" アプリまたは "Samsung HMD Odyssey + Setup" アプリを、ヘッドセットの初回接続時に自動的にインストールします)。

## <a name="my-motion-controllers-are-not-pairing-to-my-pc"></a>マイモーションコントローラーが PC とペアリングされていない

* コントローラーの電源がオンになっていない場合は、新しい電池を挿入します。 これで問題が解決しない場合は、ペアリングボタンを押しながらデバイスの電源を入れて、デバイスを工場出荷時の設定に戻します。 詳細については、 [デバイスの回復手順](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) を参照してください。
* コントローラーで電源がオンになっていて、外部 Bluetooth アダプターを使用している場合は、アダプターが USB 2.0 ポートに接続されていることを確認してください (多くの場合、常時ではありません)。他のワイヤレストランスミッタや USB フラッシュドライブから離れています。 それでも問題が解決しない場合は、Bluetooth のトラブルシューティングツールを実行して、[設定 > 更新] & セキュリティ > [Bluetooth > のトラブルシューティング] を実行します。
* Qualcomm アダプターを使用していて、PC がクラッシュしたばかりの場合は、PC を再起動します。
* ペアリングされていないモーションコントローラーを一度に1つずつ再起動し、PC を再起動してみてください。
* モーションコントローラーのキャッシュが壊れている可能性があります。 この問題を解決するには、次の [手順](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal)を参照してください。
* これらの手順で問題が解決されない場合は、製造元にお問い合わせください。

## <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>ペアになっているコントローラーが Mixed Reality ポータルに表示されない

* ヘッドセットの前にコントローラーを置き、4秒間、もう一度2秒間、Windows のボタンを押して再起動します。
* コントローラーが connected と表示されている場合は、それらをペアリングし、 [ペアリングプロセス](controllers-in-wmr.md#pair-motion-controllers) を再度実行します。
* コントローラーの Led が循環している場合、一度に1つのライトのクアドラントをオンにしてからオフにすると、ファームウェアの更新が実行されます。 更新が完了するのを待ち、コントローラーが Mixed Reality に表示されるようにします。
* 外部 Bluetooth アダプターが使用されている場合は、アダプターが USB 2.0 ポート (通常は白黒) に接続されていること3.0 を確認します。
* PC がクラッシュしただけで Qualcomm アダプターが使用されている場合は、リセットが機能しない可能性があります。 この問題を解決するには、コンピューターの背面から電源を抜いて (またはノート pc の場合は、電源ボタンを10秒押したままにして) PC を再起動します。
* Bluetooth のトラブルシューティングツールを実行して、[ **設定 > 更新] & セキュリティ >、bluetooth > のトラブルシューティング** を行います。  

## <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>コントローラーをペアリングしようとしていますが、Bluetooth 設定の [新しいデバイスの追加] メニューに表示されません。

既にコントローラーがペアリングされていないことを確認します。 削除した場合は、削除してからもう一度やり直してください。 問題が解決しない場合は、PC を再起動します。 それでも失敗する場合は、 [Bluetooth に関する詳細情報](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)を参照してください。

注: 別の一連のモーションコントローラーが PC とペアリングされている場合は、新しいコントローラーをペアリングする前に、それらのコントローラーをペアリングする必要があります。 一連のモーションコントローラーを現在の PC とペアリングしてから、2台目の PC とペアリングした場合は、再利用する前に、それらをペアリングして現在の PC とペアリングする必要があります。

## <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>Bluetooth テクノロジを使用しているかどうかを確認する方法

モーションコントローラーは、多くのコンシューマーデバイスで使用されているのと同じ Bluetooth テクノロジを使用し、最近の PC に含まれる Bluetooth 機能を使用するように設計されています。 混合 reality 互換性チェックに合格した場合、PC には Bluetooth ラジオが必要です。 検証するには:

* "デバイスマネージャー" を開きます。
* [Bluetooth] セクションを展開し、アダプターを探します。

![デバイスマネージャー例のスクリーンショット。 アダプタは Bluetooth ラジオです。](images/devicemanagerbtadapterpic.png)

PC に Bluetooth が搭載されていない場合は、Plugable USB Bluetooth 4.0 低エネルギーマイクロアダプタを使用します。

## <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>モーションコントローラーの電源がオンになっていると、Wi-Fi がノートブックの速度を低下させる

2.4 GHz アクセスポイントに接続されている場合、ノートブックは Bluetooth で Wi-Fi アンテナを共有する場合があります。 バンド設定を5GHz に切り替えることができる場合は、デバイスマネージャーチェックインします。 5GHz ネットワークが使用できず、パフォーマンスに大きな影響が及ぶ場合は、Bluetooth ドングルの使用を検討してください。

![Wifi 帯域選択の設定は、デバイスマネージャーを使用して見つけることができます。](images/wifi5ghz.png)

## <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers"></a>PC に Bluetooth テクノロジがありますが、コントローラーで問題が発生しています

モーションコントローラーは、他の Bluetooth キーボード、マウス、およびゲームコントローラーでも動作しますが、使用するキーボード、マウス、またはゲームコントローラーのモデルによってエクスペリエンスが異なります。 パフォーマンスを向上させるためにできることを次に示します。

* コンピューターに Bluetooth があるにもかかわらず、動きコントローラーで問題が発生する場合は、Bluetooth ラジオを、USB に接続されている Plugable 外部 Bluetooth アダプターに置き換えることを検討してください。 Bluetooth ラジオアダプターは一度に1つしかアクティブにできません。 既存のラジオに加えて外付けのラジオを差し込む場合は、デバイスマネージャーで既存の Bluetooth ラジオを無効にする必要があります (アダプターを右クリックし、[デバイスを無効にする] を選択します)。また、以前のすべての Bluetooth デバイスとペアリング/ペアリングを解除する必要があります。
* USB Bluetooth アダプターを使用している場合は、USB 2.0 ポートに接続します (2.0 ポートは黒であり、"SS" というラベルが付いていない場合があります) (使用可能な場合)。 ポートは、次の場所から物理的に分離する必要があります。
    - HMD USB コネクタ
    - フラッシュ ドライブ
    - ハードドライブ
    - キーボードやマウスのようなワイヤレス USB レシーバーは理想的で、他のコネクタから可能な限り、USB Bluetooth アダプタをコンピューターの反対側に接続します。
* Bluetooth 設定ウィンドウが開いている場合は閉じます。 バックグラウンドで開いたままにすると、Bluetooth プロトコルに多くの余分な呼び出しが行われることになります。
* ヘッドセットが PC とペアリングされている場合は、Windows Bluetooth ドライバースタックを使用します。サードパーティの Bluetooth ドライバースタックはインストールしないでください。 サードパーティ製のソフトウェアが正しく機能しない可能性があります。
* ホストのラジオスキャンアクティビティを減らすには、[Bluetooth & 他のデバイス] の [Swift ペアを使用して接続するように通知を表示する] 設定を無効にします。
* 内部 Bluetooth カードを使用している場合は、外部 Bluetooth アンテナを使用していることを確認してください。または、問題の追跡が発生する可能性があります。 これがうまくいかない場合は、内部 Bluetooth を無効にした後で、外部 Bluetooth ドングル (USB) を使用します。
* デバイスは、Bluetooth 設定の [マウス、キーボード & ペン] カテゴリの下に表示されます。 [その他のデバイス] の下にある場合は、ペアリングをクリックしてデバイスをペアリングします。
* Bluetooth ヘッドホンとスピーカーを取り外し、ペアリング、電源オフにします。 これらは、Windows Mixed Reality ではサポートされていません。 最適なオーディオエクスペリエンスを実現するために、Mixed Reality ヘッドセットでヘッドフォンジャックまたは内蔵スピーカーを使用します。

## <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>2つ目のコントローラーの再接続に時間がかかる

一部の古い Intel ラジオでは、モーションコントローラーの電源が同時にオンになっている場合にこの問題が発生しています。 コントローラーの電源を同時にオンにしないでください。

## <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>PC のクラッシュ後、マイ Qualcomm Bluetooth ラジオがコントローラーをペアリングできない

10.0.0.448 より前の Qualcomm (QCA) Bluetooth ラジオドライバーは、Windows のクラッシュ後、正常な状態にならない可能性があります。 この問題を回避するには、PC の電源を完全にオフにしてください。

## <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Marvell オプションを使用したコントローラーの追跡が不十分である

**デバイスマネージャー > bluetooth > MARVELL AVASTAR Bluetooth ラジオアダプター > プロパティ > ドライバー** にアクセスし、driver 15.68.9210.47 以降を使用していることを確認してください。
