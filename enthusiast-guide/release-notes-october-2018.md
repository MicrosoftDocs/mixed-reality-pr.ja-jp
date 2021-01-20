---
title: リリース ノート - 2018 年 10 月
description: Windows 10 10 月の 2018/RS5 Update については、HoloLens と Windows Mixed Reality のリリースノートを最新の状態に維持してください。
author: mattzmsft
ms.author: mazeller
ms.date: 10/02/2018
ms.topic: article
keywords: リリースノート、バージョン、windows 10、ビルド、rs5、os
ms.openlocfilehash: f62bc5b1e172958a6aebf366852cfd921f7817a3
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581484"
---
# <a name="release-notes---october-2018"></a>リリース ノート - 2018 年 10 月

**[Windows 10 10 月2018更新プログラム](https://blogs.windows.com/windowsexperience/2018/10/02/find-out-whats-new-in-windows-and-office-in-october/)**(RS5 とも呼ばれます) には、pc に接続された HoloLens および Windows Mixed Reality イマーシブヘッドセットの新機能が含まれています。 

HoloLens または PC (Windows Mixed Reality イマーシブ (VR) ヘッドセット) の最新リリースに更新するには、 **設定** アプリを開き、[ **update & Security**] にアクセスして、[ **更新プログラムの確認** ] ボタンを選択します。 Windows 10 PC では、windows [media 作成ツール](https://www.microsoft.com/software-download/windows10)を使用して、Windows 10 10 月2018更新プログラムを手動でインストールすることもできます。

**デスクトップの最新リリース:** Windows 10 10 月2018更新プログラム (**10.0.17763.107**)<br>
**HoloLens の最新リリース:** Windows 10 10 月2018更新プログラム (**10.0.17763.134**)<br>

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality イマーシブヘッドセットの新機能

Windows 10 10 月2018更新プログラムには、デスクトップ PC で Windows Mixed Reality イマーシブ (VR) ヘッドセットを使用するための多くの機能強化が含まれています。

### <a name="for-everyone"></a>すべてのユーザー向け

* **Mixed Reality 懐中電灯** -ポータルを実際の世界に開き、キーボードを見つけたり、近くのユーザーを見たり、ヘッドセットを削除せずに周囲を見たりすることがあります。 [スタート] メニューから [Windows + グラブ] を押すか、"懐中電灯をオン/オフにする" という指示によって、Mixed Reality 懐中電灯をオンにすることができます。 暗色の懐中電灯を使用するなど、表示する内容の方向にコントローラーをポイントします。

    ![Mixed Reality 懐中電灯](images/mr-flashlight.png)

* **新しいアプリと、mixed reality ホームでコンテンツを起動する方法**
    * [SteamVR で Windows Mixed Reality](./using-steamvr-with-windows-mixed-reality.md)を使用している場合、steamvr タイトルが [スタート] メニューに表示され、それぞれのアプリランチャーが Mixed reality ホームに配置されるようになりました。
    
        ![SteamVR アプリランチャー](images/steamvr-launchers.png)
        
    * Curated の360度のビデオを定期的に検出するための新しい *360 ビデオ* アプリ。
    * Curated の WebVR エクスペリエンスを定期的に検出するための新しい *Webvr ショーケース* アプリ。
    * Windows Mixed Reality を初めて使用する場合、お客様は崖ハウスに入っており、Microsoft Store の使い慣れたイマーシブアプリとゲームのいくつかについて、3D アプリランチャーが事前に設定されています。
    * Microsoft Edge ウィンドウに [ *共有* ] ボタンが追加されました。
* **クイックアクションメニュー** -イマーシブ mixed reality アプリ内から、[Windows] ボタンをクリックして新しい [クイックアクション] メニューにアクセスし、 *steamvr メニュー*、 *写真/ビデオキャプチャ*、 *懐中電灯*、および *ホーム* に簡単にアクセスできます。
* **Backpack pc のサポート** -Windows Mixed Reality イマーシブ (VR) ヘッドセットは、セットアップの完了後にディスプレイエミュレーターを必要とせずに、backpack pc で実行されます。
* **新しいオーディオ機能** -Windows Mixed Reality エクスペリエンスのオーディオを、ヘッドセットのオーディオジャック (またはヘッドホン) *と* 、PC に接続されているオーディオデバイス (外部スピーカーなど) の両方にミラー化できるようになりました。 また、ヘッドセットのディスプレイにボリュームレベルの視覚的インジケーターも追加しました。
* **その他の機能強化**
    * Microsoft Store によって、Mixed Reality ポータルの更新が配信されるようになりました。これにより、主要な Windows リリース間での更新が迅速になります。 これはデスクトップアプリにのみ適用され、Windows Mixed Reality ヘッドセットエクスペリエンスは引き続き OS で更新されることに注意してください。 
    * ヘッドセットがスリープ状態になると、Windows Mixed Reality アプリは終了せずに中断されます (Mixed Reality ポータルが閉じられるまで)。
    
### <a name="for-developers"></a>開発者向け

* **[Qr コードの追跡](/windows/mixed-reality/develop/platform-capabilities-and-apis/qr-code-tracking)** -mixed reality アプリで qr コード追跡を有効にします。これにより、Windows mixed reality イマーシブ (VR) ヘッドセットで qr コードをスキャンして、関心のあるアプリに報告することができます。
* **アプリのハードウェア DRM サポート** -ディスプレイハードウェアでサポートされている場合は、ハードウェアで保護された backbuffer テクスチャを要求できるようになりました。これにより、アプリケーションは PlayReady などのソースからハードウェアで保護されたコンテンツを使用できるようになります。
* **[Mixed reality キャプチャ ui をイマーシブアプリに統合](/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app)** する-開発者は、組み込みの Windows [カメラキャプチャ ui](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) を使用して、いくつかのコード行だけを使用して、混合 reality キャプチャをアプリに統合できます。

## <a name="new-features-for-hololens"></a>HoloLens の新機能

Windows 10 10 月2018更新プログラムは、すべての HoloLens のお客様に公開されており、次のようないくつかの改善点があります。

### <a name="for-everyone"></a>すべてのユーザー向け

* **クイックアクションメニュー** -イマーシブ mixed reality アプリ内では、[Windows] ボタンをクリックして新しい [クイックアクション] メニューにアクセスできます。簡単にアクセスして、 *ビデオの録音*、 *画像の撮影*、現実の *ホーム*、 *変更音量*、および *接続* を簡単に行うことができます。
* **[開始] または [クイックアクション] メニューからビデオキャプチャを開始** または停止する-[スタート] メニューまたは [クイックアクション] メニューからビデオキャプチャを開始すると、同じ場所から録画を停止できるようになります。 (忘れずに、音声コマンドでこれを行うことができます)。
* [**プロジェクトから miracast 対応デバイスへ**]-miracast が有効になっているディスプレイまたはアダプターを使用している場合は、近隣の Surface デバイスまたはテレビ/モニターに HoloLens コンテンツを投影します。
* **新しい通知** -PC の場合と同じように、HoloLens で通知を表示し、対応します。  
* **イマーシブ mixed reality アプリの便利なオーバーレイ** -イマーシブ mixed reality アプリを使用するときに、キーボード、ダイアログ、ファイルピッカーなどのオーバーレイが表示されるようになりました。
* **ボリュームの変更の視覚的なインジケーター** -HoloLens で [音量のアップ] ボタンまたは [下へ] ボタンを使用すると、ヘッドセットのボリュームレベルを視覚的に示すインジケーターが表示されます。
* **デバイスブートの新しいビジュアル** -システムの読み込み中に視覚的なフィードバックを提供するために、ブートプロセス中に読み込みインジケーターが追加されました。
* **近くの共有** -Windows の近くの共有エクスペリエンスでは、近くの windows デバイスとキャプチャを共有できます。  
* **Microsoft edge から共有** する-microsoft edge には、[ *共有* ] ボタンが含まれるようになりました。 

### <a name="for-developers"></a>開発者向け

* **[Mixed reality キャプチャ ui をイマーシブアプリに統合](/windows/mixed-reality/develop/platform-capabilities-and-apis/mixed-reality-capture-for-developers#integrating-mrc-functionality-from-within-your-app)** する-開発者は、組み込みの Windows [カメラキャプチャ ui](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui) を使用して、いくつかのコード行だけを使用して、混合 reality キャプチャをアプリに統合できます。

### <a name="for-commercial-customers"></a>商用のお客様向け

* **セットアップ後のプロビジョニングを有効** にする-設定を使用していつでもランタイムプロビジョニングパッケージを適用できるようになりました。
* **Azure AD グループで割り当てられたアクセス** -Azure AD グループを使用して、1つまたは複数のアプリのキオスク構成を設定するために、Windows の割り当てられたアクセスを構成できます。
* **サインイン画面からのプロファイルスイッチでの pin のサインイン** -サインイン画面で [その他のユーザー] に対して [サインイン] を使用できるようになりました。 
* **Mdm を使用してデバイスのハードウェア情報を読み取る** -IT 管理者は、mdm コンソールで、デバイスのシリアル番号を使用して HoloLens を表示および追跡できます。
* **Mdm による hololens デバイス名の設定 (名前の変更)** -IT 管理者は mdm コンソールで hololens デバイスの表示と名前の変更を行うことができます。

### <a name="for-international-customers"></a>海外のお客様向け

ローカライズされたピンインキーボード、ディクテーション、音声合成 (TTS)、音声コマンドなど、簡体字中国語または日本語用のローカライズされたユーザーインターフェイスで HoloLens を使用できるようになりました。

## <a name="known-issues"></a>既知の問題

Windows Mixed Reality エクスペリエンスの向上に努めていましたが、まだいくつかの既知の問題を追跡しています。 他のユーザーが見つかった場合は、フィードバックをお [送り](/windows/mixed-reality/give-us-feedback)ください。

### <a name="hololens"></a>HoloLens
 
#### <a name="after-update"></a>更新後
HoloLens で Windows 10 10 月2018更新プログラムを使用すると、次の問題が発生する場合があります。
* **通知から起動すると、アプリはサインインループになる可能性が** あります。サインインが必要な一部のアプリは、通知から起動すると、無限のサインインループで終了することができます。 たとえば、Microsoft ポータルサイトアプリを Microsoft Store からインストールし、インストールの完了通知から起動した後に発生する可能性があります。
* **アプリのサインインページは空白のページで完了することがあります** 。サインインプロンプトがアプリケーションを表示したときに、入力が完了すると、サインインページが閉じず、代わりに空白 (黒) のページが表示される場合があります。 空のページを閉じるか、またはその下にあるアプリケーションを見つけるために移動できます。 例として、これは設定アプリからの MDM 登録中にサインインしたときに発生する可能性があります。 

## <a name="provide-feedback-and-report-issues"></a>フィードバックの提供と問題の報告

[お客様の HoloLens または Windows 10 PC でフィードバックハブアプリ](/windows/mixed-reality/give-us-feedback)を使用して、フィードバックを提供し、問題を報告してください。 フィードバックハブを使用すると、エンジニアが迅速に問題をデバッグして解決できるように、必要な診断情報がすべて含まれるようになります。

>[!NOTE]
>フィードバックハブがドキュメントフォルダーにアクセスするかどうかを確認するメッセージが表示されることを確認します (メッセージが表示されたら [ **はい]** を選択します)。

## <a name="prior-release-notes"></a>以前のリリースノート

* [リリースノート-2018 年4月](release-notes-april-2018.md)
* [リリース ノート - 2017 年 10 月](release-notes-october-2017.md)
* [リリース ノート - 2016 年 8 月](release-notes-august-2016.md)
* [リリース ノート - 2016 年 5 月](release-notes-may-2016.md)
* [リリース ノート - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>関連項目
* [イマーシブヘッドセットのサポート (外部リンク)](./troubleshooting-windows-mixed-reality.md)
* [HoloLens サポート (外部リンク)](https://support.microsoft.com/products/hololens)
* [ツールのインストール](/windows/mixed-reality/develop/install-the-tools)
* [フィードバックの送信](/windows/mixed-reality/give-us-feedback)