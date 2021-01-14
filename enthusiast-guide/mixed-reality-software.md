---
title: ソフトウェアの概要とリリース履歴
description: Windows Mixed Reality、イマーシブヘッドセット、およびそのリリース履歴の主要なソフトウェアコンポーネントの概要を説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、ソフトウェアコンポーネント、リリース履歴、リリースノート、バージョン履歴
appliesto:
- Windows 10
ms.openlocfilehash: 763814e7ab81feeb22c4cbe4f5daf02d62db38fa
ms.sourcegitcommit: 4b6815605e2ea3830052baed38df21af354d2f9b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2021
ms.locfileid: "98166757"
---
# <a name="mixed-reality-software-overview-and-release-history"></a>Mixed Reality ソフトウェアの概要とリリース履歴

## <a name="introduction-to-mixed-reality-software"></a>Mixed Reality ソフトウェアの概要

Windows Mixed Reality は、次の主要なソフトウェアコンポーネントで構成されています。

1. Windows Mixed Reality の主要なエクスペリエンスを提供する **Mixed Reality ポータル**
    * Windows 10 バージョン1709および1803では、Mixed Reality ポータルは Windows Update によって更新された Windows 10 オペレーティングシステムの重要なコンポーネントです。
    * Windows 10 バージョン1809以降では、Mixed Reality ポータルは Microsoft Store アプリを使用して更新されます。
2. Mixed **reality のオンデマンドパッケージ** ("d") は、Mixed reality ポータルの初回実行時に自動的にダウンロードされ、インストールされます。 パッケージの詳細については、こちらを参照して[ください](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality)。
3. **Mixed reality ヘッドセットと motion controller ドライバー**(HoloLens センサードライバーとも呼ばれます) は、Windows mixed reality ヘッドセットが Windows mixed reality と連携できるようにするための主要なドライバーパッケージです。 これは、Mixed Reality ヘッドセットが初めて接続されたときに Windows Update によって自動的にダウンロードおよびインストールされ Windows Update
4. * * 混合現実運動コントローラーモデルのドライバーには、混合現実のモーションコントローラーの3D モデルが含まれており、サードパーティの Mixed Reality エクスペリエンスに必要です。 これは、Mixed Reality モーションコントローラーが PC とペアリングされて初めて Windows Update によって自動的にダウンロードおよびインストールされ Windows Update
5. **Windows 10 バージョン 1709 (秋の作成者の更新プログラム) 以降には、** Windows Mixed Reality を有効にする主要な OS コンポーネントとテクノロジが含まれています。

SteamVR で Windows Mixed Reality を使用するには、次のソフトウェアが必要です。

6. **Steamvr** は、仮想化されたアプリやゲームを蒸気上で使用できるようにするバルブ Corporation によって開発および管理されています。 詳細は[こちら](https://go.microsoft.com/fwlink/?linkid=862788)をご覧ください。
7. Windows Mixed Reality で SteamVR をブリッジする **steamvr コンポーネント用の Windows Mixed reality** 。 このコンポーネントの詳細については[、「Windows Mixed Reality For SteamVR」ページを参照し](http://store.steampowered.com/app/719950/Windows_Mixed_Reality_for_SteamVR/)てください。

Windows Mixed Reality ヘッドセットの管理:

8. 各ヘッドセット製造元によって開発および管理されている **デバイスコンパニオンアプリ** は、Windows Mixed Reality ヘッドセットを簡単に紹介します。 Bluetooth 機能が組み込まれているヘッドセットでは、デバイスコンパニオンアプリを使用して、モーションコントローラーを工場出荷時の Bluetooth ペアリングに復元できます。 一部のヘッドセット (Samsung Odyssey、Samsung Odyssey + など) も、デバイスコンパニオンアプリを使用してヘッドセットの製造元からヘッドセットファームウェアの更新プログラムを配信します。 このアプリは、ヘッドセットが初めて接続されたときに自動的にダウンロードされ、Windows の [スタート] メニューで見つけることができます。

## <a name="windows-10-release-notes---may-2020"></a>Windows 10 リリースノート-2020 年5月

**Windows 10 5 月2020更新プログラム (v2004)** には、mixed reality ホームで Win32 アプリケーションを起動する機能など、Windows mixed REALITY (VR) ヘッドセットの新機能が含まれています。 HoloLens (第1世代) は長期的なサービス (LTS) であり、サービス更新プログラムは毎月リリースされます。

Windows Mixed Reality イマーシブ (VR) ヘッドセットの最新の PC リリースにアップグレードし、[設定] を開いて **& セキュリティを更新 >** 、[ **更新プログラムの確認**] を選択します。 Windows 10 PC では、windows [media 作成ツール](https://www.microsoft.com/software-download/windows10)を使用して、 **Windows 10 5 月2020更新プログラム** を手動でインストールすることもできます。

**デスクトップの最新リリース**: Windows 10 v2004 (10.0.19041.264)

### <a name="updates-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality イマーシブヘッドセットの更新

#### <a name="introducing-the-new-microsoft-edge"></a>新しい Microsoft Edge の紹介

[以前に発表](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge)したように、Windows Mixed Reality の新しい Microsoft Edge ブラウザーを使用したサポートの向上に向けた更新が行われています。 新しい Microsoft Edge は、Chromium のオープンソースプロジェクトを採用して、顧客向けのより優れた web 互換性を作成し、すべての web 開発者に web の断片化を減らします。 また、WebXR をサポートしています。これは、web Vr の代わりに、VR ヘッドセットのイマーシブ web エクスペリエンスを作成するための新しい標準です。

#### <a name="improved-settings-for-wmr"></a>WMR の設定の改善

フィードバックにより、ヘッドセットの表示ページに設定を追加し、明確にしました。

* **ホームの視覚品質** -これらの設定を変更すると、mixed reality ホーム環境 (崖家と Skyloft) のみに影響します。

* **Mixed reality ホームの詳細レベルと効果の品質を調整** します。これにより、一部の表示がホームでの使用に影響します。 特に、この設定を [低] から [高] に変更すると、さまざまな素材 (木材、具象など) のビジュアル品質が拡張されます。

* **アプリウィンドウ解像度の変更** -既定では、自宅で起動されるほとんどの2d ウィンドウは、720-p 解像度で起動されます。 水平方向 & 手動でサイズを変更することもできますが、すべて1080p を使用するように選択することもできます。 以前は、このオプションは、[画質] の [非常に高い (ベータ)] オプションとして使用できました。 ここでは、別の設定として適切に分割しました。

* **エクスペリエンスオプション** -これらのオプションを使用すると、混合の現実エクスペリエンスが調整され、ハードウェアの負荷が軽減され、90 fps の制限のないシステムの負荷が軽減されます。 これらの追加設定を明示的に有効または無効にすることができます。または、[Windows によって決定され、ヒューリスティックでこれらのオンとオフを切り替えるタイミングを決定する] を選択します。

* **解決方法** -HP リバーブのような高解像度のヘッドセットがある場合は、ネイティブの解像度で実行するか、パフォーマンス上の理由で解像度を下げることができます。 Samsung Odyssey や Odyssey + のような以前のヘッドセットでは、1つの解像度しかサポートされていないため、これらのヘッドセットでこの設定を変更することはできません。

* [**フレームレート**]-ヘッドセットの表示のフレームレートを手動で設定できるようになりました。または、Windows でヒューリスティックを使用して、60 hz または 90 Hz が適切かどうかを判断することができます。

* **調整** -前と同様に、ヘッドセットでサポートされている場合は、IPD (interpupillary distance) を調整できます。

* **入力の切り替え** -入力フォーカスの切り替え (Win + Y) 動作を自動 (プレゼンスセンサーフィードバックに基づいて) または手動に切り替えます。

#### <a name="new-cortana-app"></a>新しい Cortana アプリ

この Windows の更新プログラムには、最新バージョンの Cortana アプリが含まれています。このアプリは現在英語版であり、"画像を撮影する" や "ビデオを撮る" などの特定の mixed reality 固有のコマンドをサポートしなくなりました。 新しい Cortana を使用してアプリを起動することができます。また、"次の会議に出席していますか?" のような、生産性に重点を置いた新しいコマンドもサポートしています。 または、"遅れている電子メールを送信 <name> してください。"
    
#### <a name="additional-updates-in-available-in-19041546-released-october-2020"></a>19041.546 で利用可能な追加の更新プログラム (2020 年10月にリリース)

このデスクトップの月間サービス更新プログラムには、Windows Mixed Reality デバイスに関する次の変更が含まれています。 
* Windows Mixed Reality のヘッドマウントされた表示 (HMD) で、ゆがみと aberrations を減らします。 
* 今後の HP Windows Mixed Reality モーションコントローラーのサポートが追加されます。 
* Windows Mixed Reality の 90 Hz リフレッシュレート設定の動作を変更して、90 Hz を達成できない場合に、自動的に 60 Hz に切り替えないようにします。 

#### <a name="help-us-improve"></a>改善にご協力ください!

互換性の向上については、継続的に検討しています。  Windows Mixed Reality で、お気に入りのクラシック Win32 アプリケーションが正しく動作しないことが判明した場合は、フィードバック [ハブ](https://support.microsoft.com//help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub)を通じてフィードバックを送信してください。

### <a name="prior-release-notes"></a>以前のリリースノート

* [リリースノート-2019 年5月](release-notes-may-2019.md)
* [リリース ノート - 2018 年 10 月](release-notes-october-2018.md)
* [リリースノート-2018 年4月](release-notes-april-2018.md)
* [リリース ノート - 2017 年 10 月](release-notes-october-2017.md)
* [リリース ノート - 2016 年 8 月](release-notes-august-2016.md)
* [リリース ノート - 2016 年 5 月](release-notes-may-2016.md)
* [リリース ノート - 2016 年 3 月](release-notes-march-2016.md)

## <a name="mixed-reality-headset-and-motion-controller-driver-release-history"></a>Mixed Reality ヘッドセットと motion controller ドライバーのリリース履歴 ###

このドライバーは Windows Update 経由で自動的にダウンロードおよびインストールされますが、ダウンロードリンクはインラインで提供されます。

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10 バージョン 2004 (2020 更新プログラム) ####

   | Version          | リリース日          | メジャーの変更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2037](https://www.microsoft.com/en-us/download/details.aspx?id=102527)  | 2020年12月10日  | Windows 10、バージョン1903、およびそれ以降と互換性があります。<br/><ul><li>一部のコントローラーが機能していないトリガーを持つ問題に対処するための、HP コントローラーの新しいコントローラーファームウェア。</li>|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102156)  | 2020年10月8日  | Windows 10、バージョン1903、およびそれ以降と互換性があります。<br/><ul><li>HP リバーブ G2、HP Omnicept、および新しい HP コントローラーの公式サポート。</li><li>HP リバーブと Samsung Odyssey + ヘッドセットの軽微な表示修正。 ( [Os ビルド 19041.546](https://support.microsoft.com/en-us/help/4577063/windows-10-update-kb4577063) 以降または [os ビルド18362.1110 と 18363.1110](https://support.microsoft.com/en-us/help/4577062/windows-10-update-kb4577062) 以降が必要です)。</li><li>スリープからのコンピューターの電源状態の移行の機能強化により、SWW 1-4 エラーが減少しました。</li><li>Windows Mixed Reality ヘッドセットプラットフォームの軽微な修正と信頼性の向上。|
   | [10.0.19041.1009](https://www.microsoft.com/en-us/download/details.aspx?id=101260)  | 2020 年 5 月 7 日      | Windows 10、バージョン1903、およびそれ以降と互換性があります。<br/><ul><li>Windows Mixed Reality ヘッドセットプラットフォームの軽微な修正と信頼性の向上。</li></ul>  |

#### <a name="windows-10-version-1903-may-2019-update"></a>Windows 10 バージョン 1903 (2019 更新プログラム) ####

   | Version          | リリース日          | メジャーの変更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.18362.1162](https://www.microsoft.com/en-us/download/details.aspx?id=100421)  | 2019 年 10 月 14 日      | Windows 10、バージョン1809、およびそれ以降と互換性があります。<br/><ul><li>Windows Mixed Reality ヘッドセットプラットフォームの軽微な修正。</li></ul>  | 
   | [10.0.18362.1062](https://www.microsoft.com/en-us/download/details.aspx?id=58492)  | 2019 年 6 月 24 日      | Windows 10、バージョン1809、およびそれ以降と互換性があります。<br/><ul><li>Windows Mixed Reality ヘッドセットのプラットフォームと信頼性の向上。スリープ状態のコンピューターと電源状態の移行に関する機能強化です。</li></ul>  | 
   | [10.0.18362.1024](https://www.microsoft.com/en-us/download/details.aspx?id=58225)  | 2019 年 5 月 1 日      | Windows 10、バージョン1809、およびそれ以降と互換性があります。<br/><ul><li>Windows Mixed Reality ヘッドセットの 2017 Acer、Asus、Dell、富士通、HP、Lenovo、および Medion ファームウェア更新プログラムが含まれています。 このファームウェアの更新により、特定のグラフィックスアダプターまたはグラフィックスドライバーとのヘッドセット表示の互換性と信頼性が向上します。</li><li>Windows Mixed Reality ヘッドセットのプラットフォームと信頼性の向上</li></ul>  | 

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10、バージョン 1803 (2018 更新プログラム)、バージョン 1809 (10 2018 月の更新プログラム) ####

   | Version          | リリース日          | メジャーの変更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17763.1069](https://www.microsoft.com/en-us/download/details.aspx?id=57702)  | 2019年1月2日      | Windows 10、バージョン1803、およびそれ以降と互換性があります。<br/><ul><li>ヘッドセットのジッターと途切れの修正の追跡</li><li>懐中電灯モードの信頼性の修正</li></ul>  | 
   | [10.0.17760.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57358)  | 2018年10月1日      | Windows 10 バージョン1809用のドライバーの最初のパブリックリリース。<br/>Windows 10、バージョン1803、およびそれ以降と互換性があります。<br/><ul><li>Windows 10 バージョン1809で、懐中電灯モードなどの新しい Windows Mixed Reality 機能を有効にします。</li><li>ヘッドセットの追跡と信頼性の向上</li><li>モーションコントローラーの追跡とパフォーマンスの向上</li><li>USB のパフォーマンスと改善</li></ul>  | 
   | [10.0.17134.1004](https://www.microsoft.com/en-us/download/details.aspx?id=56845)  | 2018 年 4 月 27 日      | Windows 10 バージョン1803用ドライバーの最初のパブリックリリース<br/> <ul><li>ヘッドセットの追跡と信頼性の向上</li><li>モーションコントローラーの追跡とパフォーマンスの向上</li></ul>  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10 バージョン 1709 (作成者の更新プログラム) ####

   | Version          | リリース日          | メジャーの変更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16299.1070](https://www.microsoft.com/en-us/download/details.aspx?id=56571)  | 2018年2月6日    | <ul><li>3Glasses Blubur S2 Mixed Reality ヘッドセットの公式サポート</li></ul> |
   | [10.0.16299.1062](https://www.microsoft.com/en-us/download/details.aspx?id=56332)  | 2017 年 12 月 19 日   | <ul><li>一部の Pc でエラーコード2181038087-7 が *発生* することにつながる、HID の問題を解決します。</li><li>さまざまな安定性と信頼性の修正</li></ul> |
   | [10.0.16299.1058](https://www.microsoft.com/en-us/download/details.aspx?id=56277)  | 2017 年 12 月 5 日    | <ul><li>ヘッドセットの追跡の向上</li><li>モーションコントローラータッチパッドの応答性の向上</li><li>ドライバーのインストールが失敗する可能性がある問題を解決します</li><li>さまざまな安定性と信頼性の修正</li></ul> |
   | [10.0.16299.1042](https://www.microsoft.com/en-us/download/details.aspx?id=56265)  | 2017年11月21日   | <ul><li>使用中にヘッドセットの led が黒になることがある問題を解決します</li><li>モーションコントローラーが消失する場合がある問題を解決します。</li><li>Dell バイザーヘッドセットのプレゼンスセンサーのパフォーマンスの向上</li><li>さまざまな安定性と信頼性の修正</li></ul> |
   | 10.0.16299.1036  | 2017年11月7日    | <ul><li>モーションコントローラーの整備士の改善:<ul><li>位置の精度が概算になると、ベロシティが適切に報告されるようになりました。これで、頭の背後にいることができます。</li><li>スローするコード例は、 [ここで](https://github.com/keluecke/MixedRealityToolkit-Unity/tree/master/External/Unitypackages/)は "ThrowingStarter" unity パッケージにあります。 開始するには、スローシーンを開きます</li></ul></li><li>モーションコントローラーのバッテリレポート機能の向上</li><li>さまざまな安定性と信頼性の修正</li></ul> |
   | 10.0.16299.1012  | 2017 年 10 月 17 日    | ドライバーの最初のパブリックリリース                              |

### <a name="mixed-reality-motion-controller-model-driver-release-history"></a>Mixed Reality モーションコントローラーモデルドライバーのリリース履歴 ###

このドライバーは Windows Update 経由で自動的にダウンロードおよびインストールされますが、ダウンロードリンクはインラインで提供されます。

#### <a name="windows-10-version-2004-may-2020-update"></a>Windows 10 バージョン 2004 (2020 更新プログラム)

| Version          | リリース日          | メジャーの変更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.19041.2034](https://www.microsoft.com/en-us/download/details.aspx?id=102155)  | 2020年9月16日      | 新しい HP Motion Controller 用ドライバーの最初のパブリックリリース。 Windows 10、バージョン1903、およびそれ以降と互換性があります。 このドライバーは、新しい HP Motion Controller とのみ互換性があります。  |

#### <a name="windows-10-version-1803-april-2018-update-and-version-1809-october-2018-update"></a>Windows 10、バージョン 1803 (2018 更新プログラム)、バージョン 1809 (10 2018 月の更新プログラム) ####

   | Version          | リリース日          | メジャーの変更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.17737.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57359)  | 2018年10月1日      | Windows 10 バージョン1809用のドライバーの最初のパブリックリリース。 Windows 10、バージョン1803、およびそれ以降と互換性があります。  |
   | [10.0.17079.1000](https://www.microsoft.com/en-us/download/details.aspx?id=57002)  | 2018 年 4 月 17 日      | Windows 10 バージョン1803用のドライバーの最初のパブリックリリース。  |

#### <a name="windows-10-version-1709-fall-creators-update"></a>Windows 10 バージョン 1709 (作成者の更新プログラム) ####

   | Version          | リリース日          | メジャーの変更                                                 |
   |------------------|-----------------------|---------------------------------------------------------------|
   | [10.0.16291.1000, 10.0.16299.1012](https://www.microsoft.com/download/details.aspx?id=56414)  | 2017 年 10 月 17 日    | ドライバーの最初のパブリックリリース                          |

### <a name="mixed-reality-portal-release-history"></a>Mixed Reality ポータルリリース履歴 ###

Windows 10 バージョン1809以降では、 [Mixed Reality ポータル](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) は Microsoft Store アプリを使用して更新されます。

#### <a name="windows-10-version-1809-and-newer"></a>Windows 10 バージョン1809以降 ####

   | Version            | リリース日          | メジャーの変更                                                 |
   |--------------------|-----------------------|---------------------------------------------------------------|
   | 2000.20111.1381.0  | 2020年12月10日        | <ul><li>Mixed Reality ポータルのランディングページを更新します。</li><li>ファームウェアの更新中にヘッドセット接続エラーを軽減します。 </li></ul>  |    | 2000.20071.1133.0  | 2020 年 8 月 5 日        | <ul><li>プレビューウィンドウを一時停止する [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) のサポート。</li></ul>  | 
   | 2000.20071.1133.0  | 2020 年 8 月 5 日        | <ul><li>プレビューウィンドウを一時停止する [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) のサポート。</li></ul>  | 
   | 2000.20041.1212.0  | 2020 年 5 月 11 日          | <ul><li>エラー15-5 エラーが発生したタイミングの問題に対処します。</li><li>インターネットに接続していない Windows Mixed Reality を実行するためのサポートが強化されました。</li><li>**セットアップコントローラー** による、モーションコントローラーのペアリングのサポートが向上しました。</li></ul>  | 
   | 2000.20031.1202.0  | 2020 年 4 月 14 日        | <ul><li>Windows Mixed Reality に関する情報、ヒント、プランのサインアップがサポートされています。</li></ul>  | 
   | 2000.20011.1312.0  | 2020 年 2 月 11 日     | <ul><li>2019年5月の更新プログラムが適用されたデバイスで [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) を使用するアプリケーションのサポートが向上しました。</li><li>ユーザー補助とキーボードフォーカスの問題に対処する</li></ul>  | 
   | 2000.19101.1211.0  | 2019 年 11 月 11 日     | <ul><li>部屋の境界のビジュアルを切り替えることができない問題に対処します。</li><li>部屋の境界のセットアップ中にヘッドセットをセンタリングできない問題に対処します。</li></ul>  | 
   | 2000.19081.1301.0  | 2019 年 9 月 23 日    | <ul><li>ハードウェアの問題のあるヘッドセットに誤ったエラーメッセージが表示される問題に対処します。 以前のバージョンで1-4 エラーコードを受け取ったユーザーは、デバイスの状態により具体的なエラーコードを受け取ることができるようになりました。</li></ul>  |
   | 2000.19071.1302.0  | 2019 年 8 月 13 日     | <ul><li>2019年5月の更新プログラムが適用されたデバイスで [OpenXR](https://docs.microsoft.com/windows/mixed-reality/openxr) を使用するアプリケーションのサポート。</li></ul>  | 
   | 2000.19061.1011.0  | 2019 年 7 月 16 日         | <ul><li>アプリの動作をカスタマイズするための JSON 構成オプションをサポートします。 詳細については https://docs.microsoft.com/windows/mixed-reality/location-based-experiences#setup 、を参照してください。</li></ul>  | 

### <a name="steamvr-release-history"></a>SteamVR リリース履歴 ###

SteamVR のバルブのリリースノートについては、次を参照してください。 [https://steamcommunity.com/app/250820](https://steamcommunity.com/app/250820)

### <a name="windows-mixed-reality-for-steamvr-release-history"></a>SteamVR リリース履歴用の Windows Mixed Reality ###

Windows Mixed Reality for SteamVR コンポーネントのリリースノートについては、次を参照してください。 [http://steamcommunity.com/games/719950/announcements/](http://steamcommunity.com/games/719950/announcements/)
