---
title: その他の質問
description: 標準のコンシューマーサポートドキュメントを超えている、その他の Windows Mixed Reality トラブルシューティングのヒント。
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート、Windows Mixed Reality のアンインストール、サポートされる言語
appliesto:
- Windows 10
ms.openlocfilehash: aa61148a115ae295c1dc64b575a2fae7b0111470
ms.sourcegitcommit: feceb21018ce1d966188a34bd1faeddfdc1b9544
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93044456"
---
# <a name="other-questions"></a>その他の質問

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a>グラフィックスドライバーがサポートされていません (グラフィックスドライバーエラーが発生しています)。

"Dxdiag" を検索して実行します。

1.  結果が "Basic レンダラー" の場合、グラフィックスドライバーはインストールされません。 この問題を解決するには:
    * デバイスマネージャーにアクセスし **て、ハードウェアの変更をスキャン > > アクション** を実行します。
    * Windows Update を使用してドライバーを更新します。
    * これで問題が解決しない場合は、製造元の web サイトにアクセスして、最新のドライバー更新プログラムをインストールしてください。 
    * GPU で更新プログラムが利用できない場合、デバイスで WMR がサポートされていない可能性があります。 必要な場合は、 [サポート](https://support.microsoft.com)にお問い合わせください。
2.  "WDDM 2.1" またはそれより前のバージョンを取得した場合、グラフィックスドライバーはインストールされますが、最新バージョンではない可能性があります。 最新バージョンを取得するには:
    * Windows Update を使用してドライバーを更新します。
    * 更新プログラムによって問題が解決されない場合は、製造元の web サイトにアクセスして、最新のドライバー更新プログラムをインストールしてください。 
    * GPU で更新プログラムが利用できない場合、デバイスで WMR がサポートされていない可能性があります。 必要な場合は、 [サポート](https://support.microsoft.com)にお問い合わせください。
    
Windows Mixed Reality セットアップでグラフィックスカードが要件を満たしていないと思われる場合は、ヘッドセットが正しいカードに接続されていることを確認します。

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a>Samsung Odyssey または Odyssey + ヘッドセットファームウェアの更新がスタックしています。

Samsung は、"Samsung HMD Odyssey セットアップ" と "Samsung HMD Odyssey + セットアップ" デバイスコンパニオンアプリを通じて配信されるヘッドセットファームウェアの更新プログラムを所有および発行します。 Samsung のファームウェア更新に関する問題の詳細については、Samsung カスタマサービスにお問い合わせください。

ファームウェアの更新プロセスがスタックし、5分以上経過していない場合は、次の手順を実行します。
* 他のすべての USB デバイスを一時的に取り外し、ファームウェアの更新を再試行してください。
* Samsung ヘッドセットを PC の別の USB 3.0 ポートに接続します。
* ギガバイトの AORUS App Center など、ファームウェアの更新を妨げる可能性のあるソフトウェアがインストールされている場合は、無効にするか、アンインストールします。
* 別の PC を使用して Samsung ヘッドセットファームウェアの更新を実行します。

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Mixed reality で PC デスクトップにアクセス操作方法には、
Windows のヘッドセットでデスクトップアプリを起動し、[ **すべてのアプリ] > [デスクトップ] >** て、mixed REALITY で PC デスクトップにアクセスします。

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>混合現実に複数のモニターを表示するにはどうすればよいですか。
既定では、デスクトップアプリが自動的に切り替えられ、フォーカスがあるモニターが表示されます。 すべてのモニターを mixed reality で表示するには、次のようにします。 
* アプリの左上隅にある [モニター] アイコンをクリックします。
* [モニターを自動的に切り替える] を無効にします。
* 表示するモニターを選択します。
* デスクトップアプリの別のインスタンスを起動します。
* そのインスタンスに表示するモニターを選択します。
* すべての物理モニターについて、この手順を繰り返します。
混合現実を再起動するたびに、各デスクトップアプリに表示するモニターを再選択する必要があることに注意してください。 

## <a name="my-desktop-app-only-shows-a-black-screen"></a>デスクトップアプリでは、黒い画面のみが表示されます。
PC に Nvidia ハイブリッド GPU が搭載されている場合、この問題は、Nvidia デバイスが、統合された GPU ではなく、個別の GPU で runtimebroker.exe を実行していることが原因である可能性があります。 この問題を解決するには、「[新しいプログラムに対して最適な設定を作成操作方法](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)には」の手順に従います。 C:\windows\system32\runtimebroker.exe を追加し、それを "統合グラフィックス" プロセッサ上で強制的に実行します。 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Windows Mixed Reality を使用すると Wi-Fi 速度が低下します。

2.4 GHz の Wi-Fi 接続を使用している場合は、動作コントローラーによって Wi-fi の速度が低下する可能性があります。 次のいずれかの操作を試してください。
* 5GHz Wi-Fi 接続を使用できる場合は、その接続に切り替えます。 [詳細については、こちらを参照してください](https://support.microsoft.com/en-us/help/4000461)。
* 別の Bluetooth アダプターを使用して、動きコントローラーを PC に接続します。 [推奨されるアダプター](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)を参照してください。

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>「PC に接続して充電する」というメッセージが表示されていました。 なぜでしょうか。

ラップトップを使用している場合、Windows Mixed Reality は、PC が完全に充電され、電源が接続されている場合に最適に動作します。 

## <a name="what-is-the-experience-options-setting"></a>エクスペリエンスオプションの設定は何ですか?

この設定 ( **mixed reality > ヘッドセット > 表示 > エクスペリエンスオプション** ) を使用すると、Windows Mixed reality パフォーマンス設定を変更できます。 これにより、さまざまなコンテンツにわたるハードウェア構成に最適なエクスペリエンスを選択できます。 次のオプションがあります。
* 自動: Windows Mixed Reality は、ハードウェア構成に最適なエクスペリエンスを決定します。 ほとんどの場合、この方法を使用することをお勧めします。
* 60Hz: [リフレッシュレート] を60Hz に設定し、Mixed Reality ポータルでのビデオキャプチャやプレビューなどの特定の機能をオフにします。
* 90Hz: リフレッシュレートを90Hz に設定します。

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Windows Mixed Reality ではどの言語がサポートされていますか。

Windows Mixed Reality は、次の言語で使用できます。
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

PC が別の言語に設定されている場合は、Windows Mixed Reality を使用できます。ただし、インターフェイスは英語 (米国) で表示され、音声コマンドやディクテーションは使用できません。 Windows Mixed Reality のスクリーンキーボードは英語 (米国) のみです。 別の言語でテキストを入力するには、PC に接続されている物理キーボードを使用します。 また、上記のサポートされている Windows Mixed Reality 言語のいずれかでディクテーションを使用することもできます。スクリーンキーボードで [マイク] を選択するだけです。

Windows Mixed Reality は、次の言語でも使用できます。音声コマンドやディクテーション機能は必要ありません。
* 繁体字中国語 (台湾および香港)
* オランダ語 (オランダ)
* 韓国語 (韓国)
* ロシア語 (ロシア)

## <a name="i-have-questions-about-my-headset-hardware"></a>ヘッドセットハードウェアに関する質問があります。

ヘッドセットの詳細については、製造元に確認してください。 箱に製品ガイドがあるか、製造元の web サイトを試すことができます。

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Windows Mixed Reality をアンインストール操作方法には

1. ヘッドセットを PC から切断します。
2. Windows Mixed Reality ポータルを閉じます。
2. [> の設定の開始] を選択し  **> Mixed Reality** ] を選択し、[アンインストール] を選択します。

ヘッドセットの使用をもう一度開始する準備ができたら、プラグインに接続し、Windows Mixed Reality ポータルでセットアップを実行します。

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>「Windows Mixed Reality のアンインストールを完了できませんでした」というメッセージが表示できました。

お使いの環境に関する情報など、一部のファイルは依然としてコンピューターに存在している可能性があります。 Windows Mixed Reality を後で再インストールする場合は、問題が発生する可能性があります。 レジストリを変更し、Windows PowerShell を使用してコマンドを実行することで、残りの Windows Mixed Reality 情報を PC から手動で削除できます。 _レジストリを正しく変更しないと、重大な問題が発生する可能性があります。必ずこれらの手順に従ってください。保護を強化するために、レジストリを変更する前にバックアップし、問題が使うした場合に復元できるようにします。_ 詳細については、「 [Windows でレジストリをバックアップして再構築する方法](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows)」を参照してください。 

Windows mixed reality をアンインストールするには、次のコマンドを使用します。
1. PC を再起動します。
2. **検索** ボックスに「regedit」と入力し、[はい] を選択します。
3. 次のレジストリ値を削除します。
   <ul>
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>し、"" を削除します。</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>、"PreferDesktopSpeaker" と "PreferDesktopMic" を削除します。</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>をクリックし、次に "DisableSpeechInput" を削除します。 注: HHKEY_CURRENT_USER のレジストリ項目は、Windows Mixed Reality を使用している PC 上のすべてのユーザーアカウントに対して削除する必要があります。</li> 
    <li><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>、"DeviceID" と "Mode" を削除します。</li> 
    <li><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>、"OnDeviceLearningCompleted" を削除します。</li> 
   </ul>
4. 次のレジストリキーを削除します。 <ul>
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></li><br/></ul>
5. レジストリエディターを閉じます。
6.**C:\Users\user name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \ localstate** にアクセスし、"RoomBounds.json" を削除します。 Windows Mixed Reality を使用したユーザーごとに、この手順を繰り返します。
7. 管理者コマンドプロンプトを開き、 **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** にアクセスします。 "ヘッド追跡データ" フォルダーの内容を削除します (フォルダー自体は削除しません)。
8. [検索] ボックスに「powershell」と入力し、[Windows PowerShell] を右クリックして、[管理者として実行] を選択します。
9. Windows PowerShell の場合: <ul>
   <li>コマンドプロンプトで、 <b>Dism/Online/Get-Capabilities</b>をコピーして貼り付け、enter キーを押します。</b></li> 
   <li>Holographic で始まる機能 Id をコピーします (存在しない場合は、この項目がインストールされていないことを意味します)。 その場合は、手順10に進みます)。</li> 
   <li>次のコマンドプロンプトをコピーして貼り付け、enter キーを押します。 <b>Dism/Online/Remove-Capability/CapabilityName: 最後の手順でコピーされた機能 id</b></li>
   </ul>
10. PC を再起動します。

