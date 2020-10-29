---
title: リリースノート-2018 年4月
description: Windows 10 April 2018 更新プログラム (RS4 とも呼ばれます) の HoloLens および Windows Mixed Reality リリースノート。
author: mattzmsft
ms.author: mazeller
ms.date: 05/21/2018
ms.topic: article
keywords: リリースノート、バージョン、windows 10、ビルド、rs4、os
ms.openlocfilehash: 9f9d82bc667f18cae2a606aa47b10b8a5f4b6f56
ms.sourcegitcommit: 838bebf6bacac4047feff493c0847d4e6371976f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2020
ms.locfileid: "91784064"
---
# <a name="release-notes---april-2018"></a>リリースノート-2018 年4月

**[Windows 10 の2018年4月更新プログラム](https://blogs.windows.com/windowsexperience/2018/04/30/whats-new-in-the-windows-10-april-2018-update)** (RS4 とも呼ばれます) には、pc に接続された HoloLens と Windows Mixed Reality の両方に対する新機能が含まれています。 

いずれかのデバイスの種類の最新リリースに更新するには、 **設定** アプリを開き、[ **update & Security** ] にアクセスして、[ **更新プログラムの確認** ] ボタンを選択します。 Windows 10 PC では、windows [media 作成ツール](https://www.microsoft.com/software-download/windows10)を使用して、Windows 10 April 2018 更新プログラムを手動でインストールすることもできます。

**デスクトップの最新リリース:** Windows 10 April 2018 更新プログラム ( **10.0.17134.1** )<br>
**HoloLens の最新リリース:** Windows 10 April 2018 更新プログラム ( **10.0.17134.80** )<br>
<br>

>[!VIDEO https://www.youtube.com/embed/O-84oWjSbr0]

*Alex Kipman からのメッセージと、Windows 10 April 2018 Update の新しい mixed reality 機能の概要*

## <a name="new-features-for-windows-mixed-reality-immersive-headsets"></a>Windows Mixed Reality イマーシブヘッドセットの新機能

Windows 10 の2018年4月の更新プログラムには、デスクトップ PC で Windows Mixed Reality イマーシブ (VR) ヘッドセットを使用するための多くの機能強化が含まれています。次に例を示します。 

* **Mixed reality ホームの新しい環境** : [スタート] メニューの [ **場所** ] を選択して、崖家と new Skyloft 環境のどちらかを選択できるようになりました。 また、作成したカスタム環境を使用できるようにするための [試験的な機能](https://docs.microsoft.com/windows/mixed-reality/design/add-custom-home-environments) も追加されました。
* **Mixed reality キャプチャにすばやくアクセス** できるようになりました。モーションコントローラーを使用して、mixed reality の写真を撮ることができます。 Windows ボタンを押したまま、トリガーをタップします。 これは、環境とアプリ間で機能しますが、DRM で保護されたコンテンツをキャプチャしません。
* **コンテンツの起動とサイズ変更のための新しいオプション** -アプリを [スタート] メニューから起動すると、その前に自動的に配置されるようになりました。 また、ウィンドウの端と隅をドラッグして、2D アプリのサイズを変更することもできます。
* **"テレポート" 音声コマンドを使用してコンテンツに簡単にジャンプ** できるようになりました。コンテンツに移動し、"テレポート" と指示することで、Windows Mixed Reality ホームのコンテンツの前にすばやくテレポートできます。
* **複合現実ホーム用のアニメーション化された [3d アプリランチャー](https://docs.microsoft.com/windows/mixed-reality/distribute/creating-3d-models-for-use-in-the-windows-mixed-reality-home#animation-guidelines)および [装飾3d オブジェクト](https://docs.microsoft.com/windows/mixed-reality/distribute/enable-placement-of-3d-models-in-the-home)** : 3d アプリランチャーにアニメーションを追加できるようになりました。ユーザーは、web ページまたは2d アプリから Windows mixed Reality ホームに装飾的な3d モデルを配置できます。
* **[Steamvr の Windows Mixed reality の機能強化](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/updating-your-steamvr-application-for-windows-mixed-reality)** -steamvr 用の Windows mixed reality は、新しいアップグレードによって "早期アクセス" から出てきました。たとえば、モーションコントローラーを使用する場合の haptic フィードバック、パフォーマンスと信頼性の向上、SteamVR のモーションコントローラーの外観の向上などがあります。
* **その他の機能強化** -自動パフォーマンス設定が、より最適化されたエクスペリエンスを提供するように更新されました (この設定は [手動で上書き](#visual-quality) できます)。 セットアップで、USB 3.0 コントローラーおよびグラフィックスカードとの一般的な互換性の問題に関する詳細情報が提供されるようになりました。

## <a name="new-features-for-hololens"></a>HoloLens の新機能

すべての HoloLens のお客様について、Windows 10 April 2018 更新プログラムが到着しました。 この更新プログラムには、 [2016 年8月](release-notes-august-2016.md)の HoloLens ソフトウェアの最終メジャーリリース以降に導入された改善点があります。

### <a name="for-everyone"></a>すべてのユーザー向け

<table>
  <tr>
    <th>機能</th><th>詳細</th><th>Instructions</th>
  </tr>
  <tr>
    <td>起動時の2D および3D コンテンツの自動配置</td><td>2D アプリランチャーまたは 2D UWP アプリが、起動時にユーザーによる配置を要求する代わりに、最適なサイズと距離で世界中に自動的に配置されます。 <a href="https://docs.microsoft.com/windows/mixed-reality/design/app-views">イマーシブアプリ</a>で<a href="https://docs.microsoft.com/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">3d アプリランチャー</a>ではなく2d アプリランチャーが使用されている場合、イマーシブアプリは RS1 の場合と同じように2d アプリランチャーから自動的に起動します。<br><br>[スタート] メニューの3D アプリランチャーも、世界中に自動的に配置されます。 アプリを自動的に起動する代わりに、ユーザーはランチャーをクリックして、イマーシブアプリを起動することができます。 ホログラムアプリから開かれた3D コンテンツと Edge から、世界中の自動配置されます。</td><td>[スタート] メニューからアプリを開くと、そのアプリを世界中に配置するように求められなくなります。<br><br>2D アプリ/<a href="https://docs.microsoft.com/windows/mixed-reality/distribute/3d-app-launcher-design-guidance">3d アプリランチャー</a> の配置が最適でない場合は、以下に説明する新しい流動的なアプリ操作を使用して簡単に移動できます。 2D アプリランチャー/3D コンテンツを再配置することもできます。これを行うには、「移動」と入力してから、宝石を使用してコンテンツを再配置します。</td>
  </tr>
  <tr>
    <td>流動的アプリの操作</td><td>"調整" モードを入力しなくても、2D および3D コンテンツの移動、サイズ変更、および回転を行うことができます。</td><td>2D UWP アプリまたは2D アプリランチャーを移動するには、単にアプリバーを見つめ、tap + hold + ドラッグジェスチャを使用します。 3D コンテンツを移動するには、オブジェクト上の任意の場所に移動し、tap + hold + drag を使用します。<br><br>2D コンテンツのサイズを変更するには、そのコーナーを見つめます。 見つめカーソルはサイズ変更カーソルに変わります。その後、[+ 押し + ドラッグ] をタップしてサイズを変更できます。 また、端を見てドラッグすることで、2D コンテンツを縦または横に並べて表示することもできます。<br><br>3D コンテンツのサイズを変更するには、両手でジェスチャフレームを持ち上げ、準備完了の位置に指を置きます。 カーソルが2つの両手で状態になることがわかります。 タップして、両方の手でジェスチャを押します。 また、離れた場所に移動すると、オブジェクトのサイズが変更されます。 前後を移動すると、オブジェクトが回転します。 この方法で、2D コンテンツのサイズを変更したり、回転させたりすることもできます。</td>
  </tr>
  <tr>
    <td>リフローによる2D アプリの水平方向のサイズ変更</td><td>2D UWP アプリの縦横比を広げることで、アプリのコンテンツをさらに表示します。 たとえば、プレビューウィンドウを表示するのに十分な幅のメールアプリを作成します。</td><td>2D UWP アプリの左端または右端を見つめてサイズ変更カーソルを表示し、tap + hold + ドラッグジェスチャを使用してサイズを変更します。</td>
  </tr>
  <tr>
    <td>拡張された音声コマンドのサポート</td><td>音声を使用するだけで、より多くのことができます。</td><td>次の音声コマンドを試してください。<ul><li>[スタート画面に移動]-[スタート] メニューを表示するか、 <a href="https://docs.microsoft.com/windows/mixed-reality/design/app-views">イマーシブアプリ</a>を終了します。</li><li>[移動]: オブジェクトを移動できます。</li></ul></td>
  </tr>
  <tr>
    <td>ホログラムと Photos アプリが更新されました</td><td>新しいホログラムでホログラムアプリを更新しました。 写真アプリを更新しました。</td><td>ホログラムと Photos アプリの外観が更新されていることがわかります。 ホログラムアプリには、テキストを簡単に作成できるように、新しいホログラムとラベルメーカーがいくつか含まれています。</td>
  </tr>
  <tr>
    <td>強化された mixed reality キャプチャ</td><td>ハードウェアショートカットは、MRC ビデオを開始および終了します。</td><td>ボリュームを3秒間押したままにして、MRC ビデオの録画を開始します。 もう一度タップするか、ブルームジェスチャを使用して終了します。</td>
  </tr>
  <tr>
    <td>統合スペース</td><td>ホログラムの領域管理を1つのスペースに簡略化します。</td><td>HoloLens はスペースを自動的に検索し、スペースを管理または選択する必要がなくなりました。 ホログラムに関する問題が発生した場合は、[ <b>設定] > [システム > ホログラム] >、近くのホログラムを削除</b>します。 必要に応じて、[ <b>すべてのホログラムを削除</b>する] を選択することもできます。</td>
  </tr>
  <tr>
    <td>強化されたオーディオ immersion</td><td>デバイスで検出された実際の壁によって音が隠されるため、アプリケーションからのよりリアルなサウンドを体感できるようになりました。</td><td>改善された空間サウンドを活用するために何もする必要はありません。</td>
  </tr>
  <tr>
    <td>エクスプローラー</td><td>HoloLens 内からファイルを移動および削除します。</td><td><b>ファイルエクスプローラー</b>アプリを使用して、HoloLens 内からファイルを移動したり、削除したりできます。<br><br><b>ヒント:</b> ファイルが何も表示されない場合は、"最近" のフィルターがアクティブになっている可能性があります (時計のアイコンは左のウィンドウで強調表示されています)。 修正するには、左側のウィンドウ (時計のアイコンの下) で <b>このデバイス</b> ドキュメントアイコンを選択するか、メニューを開いて [ <b>このデバイス</b>] を選択します。
</td>
  </tr>
  <tr>
    <td>MTP (メディア転送プロトコル) のサポート</td><td>デスクトップ PC が HoloLens のライブラリ (写真、ビデオ、ドキュメント) にアクセスして、転送ツールを簡単に使用できるようにします。</td><td>他のモバイルデバイスと同様に、HoloLens を PC に接続して、 <b>ファイルエクスプローラー</b> から hololens ライブラリ (写真、ビデオ、ドキュメント) にアクセスして転送を容易にすることができます。<br><br><b>ヒント:</b><ul><li>ファイルが表示されない場合は、HoloLens にサインインしてデータにアクセスできることを確認してください。</li><li>PC の <b>エクスプローラー</b> から、[ <b>デバイスのプロパティ</b> ] を選択して、Windows Holographic OS のバージョン番号 (ファームウェアのバージョン) とデバイスのシリアル番号を確認できます。</li></ul><b>既知の問題:</b> PC で <b>ファイルエクスプローラー</b> を使用して HoloLens の名前を変更することはできません。</td>
  </tr>
  <tr>
    <td>セットアップ時の専用ポータルネットワークサポート</td><td>お客様は、宿泊ポータルを使用するホテル、カンファレンスセンター、小売店、または企業のゲストネットワークに HoloLens をセットアップできるようになりました。</td><td>セットアップ中にネットワークを選択し、必要に応じて [自動的に接続する] チェックボックスをオンにして、要求されたネットワーク情報を入力します。</td>
  </tr>
  <tr>
    <td>OneDrive アプリを使用した写真とビデオの同期</td><td>HoloLens からの写真やビデオは、フォトアプリを通じて直接ではなく、Microsoft Store の OneDrive アプリを介して同期されるようになりました。</td><td>これを設定するには、ストアから OneDrive アプリをダウンロードして起動します。 最初の実行時に、OneDrive に自動的に写真をアップロードするように求めるメッセージが表示されます。または、[アプリの設定] でオプションを確認することもできます。</td>
  </tr>
</table>

### <a name="for-developers"></a>開発者向け

<table>
  <tr>
    <th>機能</th><th>詳細</th><th>Instructions</th>
  </tr>
  <tr>
    <td>空間マッピングの機能強化</td><td>品質、簡素化、およびパフォーマンスの向上。</td><td>空間マッピングメッシュはクリーナーとして表示されます。同じレベルの詳細を表すために必要な三角形が減少します。 シーンでは、三角形の密度が変化することがあります。</td>
  </tr>
  <tr>
    <td>深度バッファーに基づくフォーカスポイントの自動選択</td><td>Windows に深度バッファーを送信すると、HoloLens は、ホログラムの安定性を最適化するためにフォーカスポイントを自動的に選択できます。</td><td>Unity では、[ <b>Edit > Project Settings] > Player > ユニバーサル Windows プラットフォーム tab > XR settings</b>]、[ <b>WINDOWS Mixed Reality SDK</b> ] の順に展開し、[ <b>深度バッファーの共有を有効にする</b> ] がオンになっていることを確認します。 新しいプロジェクトの場合、このチェックボックスは自動的にオンになります。<br><br>DirectX アプリの場合は、各フレームの<b>HolographicRenderingParameters</b>に<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer">CommitDirect3D11DepthBuffer</a>メソッドを呼び出して、深度バッファーを Windows に提供するようにします。
</td>
  </tr>
  <tr>
    <td>Holographic reprojection モード</td><td>HoloLens で位置指定の再プロジェクションを無効にして、360度のビデオなど、本体でロックされているコンテンツのホログラムの安定性を向上させることができるようになりました。</td><td>Unity では、 <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html">HolographicSettings を ReprojectionMode</a> に設定して、ビュー内のすべてのコンテンツが固定本文でロックされている場合に <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html">OrientationOnly</a> に設定します。<br><br>DirectX アプリの場合は、HolographicCameraRenderingParameters を<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicreprojectionmode">HolographicReprojectionMode</a>に設定します。これは、ビューのすべてのコンテンツが固定本文でロックされている場合に<a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.reprojectionmode">ReprojectionMode</a>になります。</td>
  </tr>
  <tr>
    <td>アプリの調整 Api</td><td>Windows Api では、デバイスのディスプレイが透過的 (HoloLens) であるか不透明な (イマーシブヘッドセット)、holographic シェルに UWP アプリの2D ビューが表示されているかなど、アプリが実行されている場所の詳細がわかります。</td><td>Unity は、このビルドよりも前に動作するように HolographicSettings を手動で公開していま <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html">し</a> た。<br><br>DirectX アプリでは、HolographicDisplay () のような既存の Api にアクセスできるようになりました <a href="https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.isopaque">。</a> HoloLens でも IsOpaque で <a href="https://docs.microsoft.com/uwp/api/windows.applicationmodel.preview.holographic.holographicapplicationpreview.iscurrentviewpresentedonholographicdisplay">HolographicApplicationPreview、IsCurrentViewPresentedOnHolographicDisplay</a> 。
</td>
  </tr>
  <tr>
      <td>リサーチモード</td><td>を使用すると、開発者は、次のようなコンピュータービジョンとロボット機構のフィールドで新しいアイデアをテストするために、学術および産業アプリケーションを構築するときに、主要な HoloLens センサーにアクセスできます。<ul><li>4つの環境トラッキングカメラ</li><li>カメラデータの2つのバージョンの深さマッピング</li><li>赤外線反射反射ストリームの2つのバージョン</li></ul></td><td><a href="https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/research-mode">リサーチモードのドキュメント</a><br><a href="https://github.com/Microsoft/HoloLensForCV">リサーチモードのサンプルアプリ</a></td>
  </tr>
</table>

### <a name="for-commercial-customers"></a>商用のお客様向け

<table>
  <tr>
    <th>機能</th><th>詳細</th><th>Instructions</th>
  </tr>
  <tr>
    <td>1つのデバイスで複数の Azure Active Directory ユーザーアカウントを使用する</td><td>HoloLens を複数の Azure AD ユーザーと共有し、それぞれにユーザー設定とデバイス上のユーザーデータを設定します。</td><td><a href="https://docs.microsoft.com/hololens/hololens-multiple-users">IT Pro センター: HoloLens を複数の担当者と共有する</a></td>
  </tr>
  <tr>
    <td>サインイン時に Wi-fi ネットワークを変更する</td><td>サインインする前に Wi-fi ネットワークを変更して、別のユーザーが Azure AD ユーザーアカウントを使用して初めてサインインできるようにします。これにより、ユーザーはさまざまな場所やジョブサイトでデバイスを共有できるようになります。</td><td>サインイン画面で、[パスワード] フィールドの下にあるネットワークアイコンを使用して、ネットワークに接続できます。 これは、デバイスに初めてサインインするときに役立ちます。</td>
  </tr>
  <tr>
    <td>統合された登録</td><td>HoloLens ユーザーは、個人の Microsoft アカウントを使用してデバイスをセットアップし、職場アカウント (Azure AD) を追加して、デバイスを MDM サーバーに参加させることが簡単になりました。</td><td>Azure AD アカウントを使用してサインインするだけで、登録が自動的に行われます。</td>
  </tr>
  <tr>
    <td>MDM 登録を使用しないメール同期</td><td>MDM 登録を必要としない Exchange Active Sync (EAS) メール同期のサポート。</td><td>MDM に登録しなくても電子メールを同期できるようになりました。 Microsoft アカウントを使用してデバイスをセットアップし、メールアプリをダウンロードしてインストールし、仕事用の電子メールアカウントを直接追加することができます。</td>
  </tr>
</table>

### <a name="for-it-pros"></a>IT 技術者の場合

<table>
  <tr>
    <th>機能</th><th>詳細</th><th>Instructions</th>
  </tr>
  <tr>
    <td>新しい "Windows Holographic for Business" OS 名</td><td>HoloLens で商用スイート機能が有効になっている場合、エディションのアップグレードライセンスアプリケーションの混乱を減らすためにエディション名をクリアします。</td><td>デバイス上の Windows Holographic のエディションは、[ <b>設定 > システム > につい</b>て] で確認できます。 "Windows Holographic for Business" は、エディションの更新プログラムが適用されて市販のスイート機能を有効にした場合に表示されます。 <a href="https://docs.microsoft.com/hololens/hololens-upgrade-enterprise">Windows Holographic For Business の機能のロックを解除</a>する方法について説明します。</td>
  </tr>
  <tr>
  <td>Windows 構成デザイナー (WCD)</td><td>プロビジョニングパッケージを作成および編集して、更新された WCD アプリを使用して HoloLens を構成します。 エディションの更新、構成可能な OOBE、地域/タイムゾーン、一括 Azure AD トークン、ネットワーク、および developer CSP 用の単純な HoloLens ウィザード。 割り当てられたアクセスおよびアカウント管理 Csp を含む、HoloLens がサポートするオプションにフィルターが適用された詳細エディター。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro センター: プロビジョニングパッケージを使用して HoloLens を構成する</a></td>
  </tr>
  <tr>
    <td>構成可能なセットアップ (OOBE)</td><td>セットアップ中に、調整、ジェスチャ/宝石トレーニング、および Wi-fi 構成画面を非表示にします。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning#create-a-provisioning-package-for-hololens-using-the-hololens-wizard">IT Pro センター: プロビジョニングパッケージを使用して HoloLens を構成する</a></td>
  </tr>
  <tr>
    <td>一括 Azure AD トークンのサポート</td><td>ユーザー設定のフローを迅速にするために、デバイスを Azure AD directory テナントに事前登録します。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro センター: プロビジョニングパッケージを使用して HoloLens を構成する</a></td>
  </tr>
  <tr>
  <td>DeveloperSetup CSP</td><td>開発者モードで HoloLens を設定するためのプロファイルを展開します。 開発とデモの両方のデバイスに役立ちます。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro センター: プロビジョニングパッケージを使用して HoloLens を構成する</a></td>
  </tr>
  <tr>
  <td>AccountManagement CSP</td><td>一時的な使用のために、シングルサインオンまたは非アクティブまたはストレージのしきい値の後に HoloLens デバイスを共有し、ユーザーデータを削除します。 Azure AD アカウントをサポートします。</td><td><a href="https://docs.microsoft.com/hololens/hololens-provisioning">IT Pro センター: プロビジョニングパッケージを使用して HoloLens を構成する</a></td>
  </tr>
  <tr>
  <td>割り当てられたアクセス</td><td>最初のワーカーまたはデモのために割り当てられた Windows アクセス。 1つまたは複数のアプリによるロックダウン。 開発者によるロック解除は必要ありません。</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk">IT Pro センター: キオスクモードでの HoloLens のセットアップ</a></td>
  </tr>
  <tr>
  <td>キオスクデバイスのゲストアクセス</td><td>デモ用のパスワードのない guest アカウントを使用した Windows 割り当てアクセス。 1つまたは複数のアプリによるロックダウン。 開発者によるロック解除は必要ありません。</td><td><a href="https://docs.microsoft.com/hololens/hololens-kiosk#guest">IT Pro センター: キオスクモードでの HoloLens のセットアップ</a></td>
  </tr>
  <tr>
    <td>セットアップ (OOBE) 診断</td><td>HoloLens から診断ログを取得して Azure AD サインインエラーのトラブルシューティングを行えるようにします (サインインに失敗したユーザーはフィードバックハブを利用できます)。</td><td>セットアップまたはサインインに失敗した場合は、[新しい <b>収集情報</b> ] オプションを選択して、トラブルシューティングの診断ログを取得します。</td>
  </tr>
  <tr>
    <td>ローカルアカウントの無期限パスワードの有効期限</td><td>ローカルアカウントのパスワードの有効期限が切れたときに、デバイスのリセットが中断しないようにします。</td><td>ローカルアカウントをプロビジョニングするときに、アカウントのパスワードの有効期限が切れているため、[ <b>設定</b>] の42日おきにパスワードを変更する必要はなくなりました。</td>
  </tr>
  <tr>
    <td>MDM 同期の状態と詳細</td><td>HoloLens 内から MDM の同期状態と詳細を把握するための標準の Windows 機能。</td><td>デバイスの MDM 同期ステータスを確認するには、[ <b>設定 > アカウント > [職場または学校 > 情報にアクセス</b>する] を使用します。 [ <b> デバイスの同期の状態] セクションでは、 <b> 同期の開始、MDM によって管理されている領域の確認、高度な診断レポートの作成とエクスポートを行うことができます。</td>
  </tr>
</table>

## <a name="known-issues"></a>既知の問題

Windows Mixed Reality エクスペリエンスの向上に努めていましたが、まだいくつかの既知の問題を追跡しています。 他のユーザーが見つかった場合は、フィードバックをお [送り](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback)ください。

### <a name="hololens"></a>HoloLens

#### <a name="after-update"></a>更新後

HoloLens で RS1 から RS4 に更新すると、次の問題が発生する場合があります。
* **Pin のリセット** -[スタート] メニューにピン留めされた 3 x 3 のアプリは、更新後に既定値にリセットされます。 
* **アプリと配置** されたホログラムのリセット-世界中に配置されたアプリは更新後に削除され、スペース全体に再配置する必要があります。 
* **フィードバックハブはすぐに起動しないことがあり** ます。更新の直後に、フィードバックハブなどの一部の受信トレイアプリを自分で更新して起動するまで数分かかります。 
* **企業の wi-fi 証明書は再同期する必要があり** ます。会社の証明書をデバイスに再同期してから、証明書を使用して企業ネットワークに再接続できるようにするために、HoloLens を別のネットワークに接続する必要がある問題を調査しています。 
* **HEVC ビデオ再生が機能しない** -265 のビデオを再生しようとすると、エラーメッセージが表示されます。 回避策として、 [Windows デバイスポータルにアクセス](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)し、左側のナビゲーションバーで [ **アプリ** ] を選択して、HEVC アプリケーションを **削除** します。 次に、Microsoft Store から最新の [HEVC ビデオ拡張機能](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) をインストールします。 問題を調査しています。 

#### <a name="for-developers-updating-hololens-apps-for-devices-running-windows-10-april-2018-update"></a>開発者向け: Windows 10 April 2018 更新プログラムを実行しているデバイスの HoloLens アプリを更新する

[新しい機能](#new-features-for-hololens)の一覧と共に、Windows 10 April 2018 UPDATE (RS4) for HoloLens では、以前のバージョンではないコードの動作が適用されます。
* **機密リソース (カメラ、マイクなど) を使用するためのアクセス許可要求** -RS4 では、カメラやマイクなどの機密リソースにアクセスするためのアプリのアクセス許可要求が適用されます。 HoloLens の RS1 はこれらのプロンプトを強制しませんでした。したがって、アプリがこれらのリソースに直ちにアクセスすることを前提としている場合は、ユーザーが要求されたリソースにアクセス許可を付与したとしても、RS4 でクラッシュする可能性があります。 詳細については、関連する [UWP アプリ機能の宣言](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) に関する記事を参照してください。
* HoloLens で RS4 の **外部のアプリを呼び出す** と、Windows.System が適切に使用され [*ます。ランチャー* クラス](https://docs.microsoft.com/uwp/api/Windows.System.Launcher)を使用して、自分で別のアプリを起動します。 たとえば、Windows.System を呼び出しているアプリに関する問題が見つかりました *。* ASTA (UI) 以外のスレッドから起動します。 これは HoloLens の RS1 で成功しますが、RS4 では、UI スレッドでの呼び出しを実行する必要があります。

### <a name="windows-mixed-reality-on-desktop"></a>デスクトップ上の Windows Mixed Reality

#### <a name="visual-quality"></a>ビジュアルの品質

* Windows 10 の2018年4月に、グラフィックスが以前よりもぼやけたものであるか、またはビューのフィールドのヘッドセットが小さくなることがわかった場合は、低画質のグラフィックスカード (Nvidia 1050 など) で十分なフレームレートを維持するために、自動パフォーマンス設定が変更されている可能性があります。 このオプションを手動でオーバーライドすることができます (選択した場合)。 [設定] に移動すると **> > ヘッドセットに > エクスペリエンスのオプション > 変更** され、[自動] が "90 Hz" に変更されます。 また、(同じ設定ページで) **ビジュアル品質** を "高" に変更することもできます。

#### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality セットアップ

* ヘッドセットが接続された状態で Windows をセットアップすると、PC モニターが空白になることがあります。 ヘッドセットを抜いて、Windows セットアップを完了するために PC モニターに出力できるようにします。
* ヘッドホンが接続されていない場合は、Windows Mixed Reality ホームに初めてアクセスすると、追加のヒントが表示されないことがあります。
* その他の Bluetooth デバイスは、モーションコントローラーに干渉する可能性があります。 モーションコントローラーに接続/ペアリング/追跡の問題がある場合は、Bluetooth ラジオ (外付けドングルの場合) が、別の Bluetooth ドングルのすぐ横ではなく、どこにも接続されていないことを確認してください。 また、Windows Mixed Reality セッション中に他の Bluetooth 周辺機器の電源をオンにして、それが役立つかどうかを確認してください。

#### <a name="games-and-apps-from-the-microsoft-store"></a>Microsoft Store からのゲームとアプリ

* Forza Motorsport 7 など、グラフィカルに集中しているゲームの中には、Windows Mixed Reality で再生する場合に、あまり利用できない Pc でパフォーマンスの問題が発生する可能性があります。

#### <a name="audio"></a>オーディオ

* Windows Mixed Reality ヘッドセットを使用する前に、ホスト PC で Cortana が有効になっている場合、Windows Mixed Reality ホームの周囲に配置するアプリに適用される、空間サウンドシミュレーションが失われる可能性があります。 
   * 回避策は、コンピューターに接続されているすべてのオーディオデバイスで、ヘッドセット接続されたオーディオデバイスでも、"ヘッドホン用の Windows Sonic" を有効にすることです。
      1. デスクトップタスクバーのスピーカーアイコンを左クリックし、[オーディオデバイス] の一覧から選択します。
      2. デスクトップタスクバーのスピーカーアイコンを右クリックし、[スピーカーのセットアップ] メニューの [ヘッドホン用 Windows] を選択します。
      3. すべてのオーディオデバイス (エンドポイント) に対して、この手順を繰り返します。
   * もう1つのオプションは **Settings**  >  、Windows Mixed Reality を起動する前に、デスクトップの **cortana** の設定で cortana に対して cortana への応答を許可することです。
* 別のマルチメディア USB デバイス (web cam など) が Windows Mixed Reality ヘッドセットを使用して同じ USB ハブ (外部または PC 内) を共有している場合、まれに、ヘッドセットのオーディオジャック/ヘッドホンの音が少なくなったり、音声がまったくない場合があります。 ヘッドセットでこの問題を解決するには、他のデバイスと同じハブを共有しない USB ポートを使用するか、他の USB マルチメディアデバイスを切断/無効にします。
* まれに、ホスト PC の USB ハブが Windows Mixed Reality ヘッドセットに十分な電力を供給できず、ヘッドセットに接続されているヘッドホンからノイズが急増する場合があります。

#### <a name="holograms"></a>ホログラム

* Windows Mixed Reality ホームに多数のホログラムが配置されている場合は、表示されているように見えなくなることがあります。 これを回避するには、Windows Mixed Reality ホームのその領域にあるホログラムの一部を削除します。

#### <a name="motion-controllers"></a>モーション コントローラー

* 入力がヘッドセットにルーティングされていない場合、モーションコントローラーは、部屋の境界の横に保持されていると、簡単に消えます。 Win + Y キーを押して、デスクトップモニター全体に青いバナーがあることを確認すると、このように解決されます。 
* 場合によっては、Microsoft Edge で web ページをクリックすると、コンテンツがクリックではなくズームされます。

#### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality ホームのデスクトップアプリ

* Snipping tool はデスクトップアプリでは機能しません。
* デスクトップアプリでは、再起動時に設定が保持されません。
* デスクトップで Mixed Reality ポータルプレビューを使用している場合、Windows Mixed Reality ホームでデスクトップアプリを開くと、無限のミラー効果に気付くことがあります。 
* デスクトップアプリを実行すると、非 Ultra Windows Mixed Reality Pc でパフォーマンスの問題が発生する可能性があります。推奨されません。  
* デスクトップ上の非表示のウィンドウにフォーカスがあるため、デスクトップアプリが自動起動することがあります。 
* デスクトップユーザーアカウント制御プロンプトでは、プロンプトが完了するまでヘッドセットが黒く表示されます。

#### <a name="windows-mixed-reality-for-steamvr"></a>SteamVR の Windows Mixed Reality

* SteamVR を起動する前に、Windows 10 April 2018 更新プログラムに必要なソフトウェア更新プログラムが完了していることを確認するために、の更新後に Mixed Reality ポータルを起動することが必要になる場合があります。 
* Windows 10 April 2018 更新プログラムとの互換性を維持するために、SteamVR の Windows Mixed Reality の最新バージョンを使用する必要があります。 SteamVR の Windows Mixed Reality で自動更新が有効になっていることを確認します。これは、ストリームのライブラリの "ソフトウェア" セクションにあります。  

#### <a name="other-issues"></a>その他の問題

>[!IMPORTANT]
>Insider (バージョン 17134.5) にプッシュされた Windows 10 April 2018 更新プログラムの初期バージョンでは、Windows Mixed Reality を実行するために必要なソフトウェアが不足していました。 Windows Mixed Reality を使用する場合は、このバージョンを避けることをお勧めします。 

この更新プログラムの最初のリリース (10.0.17134.1) で Surface Book 2 を使用すると、パフォーマンスが低下していることを確認しました。これは、今後の更新プログラムの修正プログラムで修正される予定です。 手動で更新する前、または更新が正常にロールアウトされるのを待機する前に、このが修正されるまで待機することをお勧めします。

## <a name="provide-feedback-and-report-issues"></a>フィードバックの提供と問題の報告

[お客様の HoloLens または Windows 10 PC でフィードバックハブアプリ](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback)を使用して、フィードバックを提供し、問題を報告してください。 フィードバックハブを使用すると、エンジニアが迅速に問題をデバッグして解決できるように、必要な診断情報がすべて含まれるようになります。

>[!NOTE]
>フィードバックハブがドキュメントフォルダーにアクセスするかどうかを確認するメッセージが表示されることを確認します (メッセージが表示されたら [ **はい]** を選択します)。

## <a name="prior-release-notes"></a>以前のリリースノート

* [リリース ノート - 2017 年 10 月](release-notes-october-2017.md)
* [リリース ノート - 2016 年 8 月](release-notes-august-2016.md)
* [リリース ノート - 2016 年 5 月](release-notes-may-2016.md)
* [リリース ノート - 2016 年 3 月](release-notes-march-2016.md)

## <a name="see-also"></a>関連項目
* [イマーシブヘッドセットのサポート (外部リンク)](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality)
* [HoloLens サポート (外部リンク)](https://support.microsoft.com/products/hololens)
* [ツールのインストール](https://docs.microsoft.com/windows/mixed-reality/develop/install-the-tools)
* [フィードバックの送信](https://docs.microsoft.com/windows/mixed-reality/give-us-feedback)

