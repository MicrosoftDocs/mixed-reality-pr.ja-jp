---
title: アプリ モデル
description: Windows Mixed Reality では、最新の Windows アプリのモデルと環境であるユニバーサル Windows プラットフォームによって提供されるアプリモデルを使用します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: UWP、アプリモデル、ライフサイクル、中断、再開、タイル、ビュー、コントラクト、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 332556a5118f0c69a83654d345119995e4262cb5
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703108"
---
# <a name="app-model"></a>アプリ モデル

Windows Mixed Reality は、 [ユニバーサル Windows プラットフォーム](https://docs.microsoft.com/windows/uwp/get-started/) (UWP) によって提供されるアプリモデルを使用します。これは、最新の windows アプリ用のモデルと環境です。 UWP アプリモデルは、アプリのインストール、更新、バージョン管理、および完全な削除の方法を定義します。 アプリケーションのライフサイクル (アプリの実行、スリープ、終了のしくみ、および状態を保持する方法) を制御します。 また、オペレーティングシステム、ファイル、およびその他のアプリとの統合と相互作用についても説明します。

![朝食領域の Windows Mixed Reality ホームに配置された2D アプリ](images/20160112-055908-hololens-500px.jpg)<br>
*Windows Mixed Reality ホームに2D ビューが配置されているアプリ*

## <a name="app-lifecycle"></a>アプリのライフサイクル

混合現実アプリのライフサイクルには、配置、起動、終了、削除などの標準的なアプリの概念が含まれます。

### <a name="placement-is-launch"></a>配置を開始します

すべてのアプリは、 [Windows Mixed reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)にアプリタイル ( [windows セカンダリタイル](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile)のみ) を配置することによって、mixed reality で開始されます。 これらのアプリタイルは、配置時にアプリの実行を開始します。 これらのアプリタイルは、配置されている場所に保持され、いつでもアプリに戻るときのランチャーのように動作します。

![配置では、セカンダリタイルを世界中に配置します](images/slide1-600px.png)<br>
*配置では、セカンダリタイルを世界中に配置します*

配置が完了するとすぐに (アプリの起動の [ためにアプリ](app-model.md#protocols) によって配置が開始された場合を除き)、アプリの起動が開始されます。 Windows Mixed Reality では、限られた数のアプリを一度に実行できます。 アプリを配置して起動するとすぐに、他のアクティブなアプリが中断され、アプリが配置されている場所でアプリの最後の状態のスクリーンショットが残ります。 再開とその他のアプリライフサイクルイベントの処理の詳細については、「 [Windows 10 UWP アプリのライフサイクル](https://docs.microsoft.com/windows/uwp/launch-resume/app-lifecycle) 」を参照してください。

![タイルを配置すると、アプリの実行中 ](images/slide2-500px.png) ![ 、中断、または実行されていない状態の図が開始されます。](images/ic576232-500px.png)<br>
*Left: タイルを配置すると、アプリの実行が開始されます。Right: アプリの実行中、中断中、または実行されていない状態の図。*

### <a name="remove-is-closeterminate-process"></a>終了プロセスと終了プロセスを削除する

配置されたアプリのタイルを世界から削除すると、基になるプロセスが終了します。 これは、アプリが終了したことを確認したり、問題のあるアプリを再起動したりするのに役立ちます。

### <a name="app-suspensiontermination"></a>アプリの中断/終了

[Windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)では、ユーザーはアプリに対して複数のエントリポイントを作成できます。 これを行うには、[スタート] メニューからアプリを起動し、アプリのタイルを世界中に配置します。 各アプリタイルは、異なるエントリポイントとして動作し、システムに個別のタイルインスタンスがあります。 [Secondarytile のクエリ。 FindAllAsync](https://docs.microsoft.com/uwp/api/Windows.UI.StartScreen.SecondaryTile#Windows_UI_StartScreen_SecondaryTile_FindAllAsync)は、各アプリインスタンスの **secondarytile** になります。

UWP アプリが中断すると、現在の状態がスクリーンショットとして取得されます。

![中断されたアプリでスクリーンショットが表示される](images/slide9-800px.png)<br>
*中断されたアプリでスクリーンショットが表示される*

他の Windows 10 シェルとの重要な違いの1つは、アプリインスタンスのアクティベーションが [CoreApplication](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_Resuming) イベントと [corewindow](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Activated) によってどのように通知されるかということです。

|  シナリオ |  再開中  |  アクティブ | 
|----------|----------|----------|
|  [スタート] メニューからアプリの新しいインスタンスを起動する  |   |  新しい [タイル id](https://docs.microsoft.com/uwp/api/windows.ui.startscreen.secondarytile#Windows_UI_StartScreen_SecondaryTile_TileId)で **アクティブ化** されました | 
|  [スタート] メニューからアプリの2番目のインスタンスを起動する  |   |  新しい **タイル id** で **アクティブ化** されました | 
|  現在アクティブでないアプリのインスタンスを選択します  |   |  インスタンスに関連付けられた **タイル id** で **アクティブ化** されます | 
|  別のアプリを選択し、以前にアクティブなインスタンスを選択します。  |  **再開** の発生  |  | 
|  別のアプリを選択し、以前に非アクティブだったインスタンスを選択します。  |  **再開** の発生  |  その後、インスタンスに関連付けられた **タイル id** で **アクティブ化** されます。 | 

### <a name="extended-execution"></a>拡張実行

場合によっては、アプリがバックグラウンドで作業を継続したり、オーディオを再生したりする必要があります。 HoloLens では、[バックグラウンドタスク](https://docs.microsoft.com/windows/uwp/launch-resume/declare-background-tasks-in-the-application-manifest)を使用できます。

![アプリはバックグラウンドで実行できます](images/slide10-800px.png)<br>
*アプリはバックグラウンドで実行できます*

## <a name="app-views"></a>アプリ ビュー

アプリがアクティブになると、表示するビューの種類を選択できます。 アプリの **CoreApplication** には、常にプライマリ [アプリビュー](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationView) と、作成するアプリビューがいくつかあります。 デスクトップでは、アプリビューをウィンドウと見なすことができます。 Mixed reality アプリテンプレートでは、プライマリアプリビューが [イマーシブ](app-views.md)である Unity プロジェクトが作成されます。 

アプリ内購入などの Windows 10 機能を使用するには、XAML などのテクノロジを使用して、追加の2D アプリビューを作成できます。 アプリが他の Windows 10 デバイスの UWP アプリとして起動された場合、プライマリビューは2D になりますが、エクスペリエンスの volumetrically を表示するためのアプリビューを追加することによって、混合現実に "明るい" ことができます。 たとえば、XAML でフォトビューアーアプリをビルドし、スライドショーボタンが世界中および画面上のアプリから写真を撮影したイマーシブアプリビューに切り替わったとします。

![実行中のアプリは、2D ビューまたはイマーシブビューを持つことができます。](images/slide3-800px.png)<br>
*実行中のアプリは、2D ビューまたはイマーシブビューを持つことができます。*

### <a name="creating-an-immersive-view"></a>イマーシブビューの作成

Mixed reality アプリとは、 [HolographicSpace](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace) の種類で実現されるイマーシブビューを作成するアプリです。

純粋にイマーシブなアプリでは、デスクトップから起動した場合でも、常に起動時にイマーシブビューを作成する必要があります。 イマーシブビューは、いつ作成されたかに関係なく、ヘッドセットに常に表示されます。 イマーシブビューをアクティブ化すると、Mixed Reality ポータルが表示され、ユーザーはヘッドセットに配置することができます。

デスクトップモニターの2D ビューから開始するアプリでは、ヘッドセット内のコンテンツを表示するための2次的なイマーシブビューを作成できます。 この例として、モニター上の 2D Edge ウィンドウで、ヘッドセットに360度のビデオが表示されています。

![イマーシブビューで実行されているアプリが1つだけ表示される](images/slide4-800px.png)<br>
*イマーシブビューで実行されているアプリが1つだけ表示される*

### <a name="2d-view-in-the-windows-mixed-reality-home"></a>Windows Mixed Reality ホームの2D ビュー

イマーシブビュー以外のものは、世界中の2D ビューとしてレンダリングされます。

アプリでは、デスクトップモニターとヘッドセットの両方に2D ビューがある場合があります。 新しい2D ビューは、モニターまたはヘッドセットで作成したビューと同じシェルに配置されることに注意してください。 現在、アプリまたはユーザーが混合現実ホームとモニターの間で2D ビューを移動することはできません。

![2D ビューで実行されているアプリが混合世界の領域を他のアプリと共有する](images/slide5-800px.png)<br>
*2D ビューで実行されているアプリが他のアプリとスペースを共有する*

### <a name="placement-of-additional-app-tiles"></a>追加のアプリタイルの配置

[セカンダリタイル api](https://docs.microsoft.com/windows/uwp/design/shell/tiles-and-notifications/secondary-tiles)を使用すると、世界中に2d ビューのアプリをいくつでも配置できます。 これらの "ピン留め" タイルは、ユーザーが配置する必要があるスプラッシュスクリーンとして表示され、後でアプリを起動するために使用できます。 Windows Mixed Reality では、現在、2D タイルコンテンツをライブタイルとして表示することはサポートされていません。

![セカンダリタイルを使用してアプリを複数配置できます。](images/slide6-800px.png)<br>
*セカンダリタイルを使用してアプリを複数配置できます。*

### <a name="switching-views"></a>ビューの切り替え

#### <a name="switching-from-the-2d-xaml-view-to-the-immersive-view"></a>2D XAML ビューからイマーシブビューへの切り替え

アプリで XAML が使用されている場合、XAML [Iframeworkviewsource](https://docs.microsoft.com/uwp/api/windows.applicationmodel.core.iframeworkviewsource) はアプリの最初のビューを制御します。 アプリは、 **Corewindow** をアクティブ化する前に、イマーシブビューに切り替える必要があります。これにより、アプリがイマーシブエクスペリエンスに直接起動します。

[CoreApplication](https://docs.microsoft.com/uwp/api/Windows.ApplicationModel.Core.CoreApplication#Windows_ApplicationModel_Core_CoreApplication_CreateNewView_Windows_ApplicationModel_Core_IFrameworkViewSource_)を使用して、アクティブな[ビューにし](https://docs.microsoft.com/uwp/api/Windows.UI.ViewManagement.ApplicationViewSwitcher#Windows_UI_ViewManagement_ApplicationViewSwitcher_SwitchAsync_System_Int32_)ます。

> [!NOTE]
>* XAML ビューからイマーシブビューへの切り替え時に [Applicationviewswitchingoptions](https://docs.microsoft.com/uwp/api/windows.ui.viewmanagement.applicationviewswitchingoptions) フラグを **switchasync** に指定しないでください。そうしないと、アプリを起動したスレートが世界から削除されます。
>* **Switchasync** は、切り替え先のビューに関連付けられている [ディスパッチャー](https://docs.microsoft.com/uwp/api/windows.ui.core.corewindow#Windows_UI_Core_CoreWindow_Dispatcher) を使用して呼び出す必要があります。
>* 仮想キーボードを起動する必要がある場合、または別のアプリをアクティブ化する必要がある場合は、XAML ビュー **に戻る必要** があります。

![アプリがイマーシブビューに移動したときに、アプリが2D ビューとイマーシブビューを切り替えることができ ](images/slide7-600px.png) ![ 、混合世界とその他のアプリが非表示になる](images/slide8-600px.png)<br>
*Left: アプリは、2D ビューとイマーシブビューを切り替えることができます。Right: アプリがイマーシブビューに移動すると、Windows Mixed Reality ホームとその他のアプリが非表示になります。*

#### <a name="switching-from-the-immersive-view-back-to-a-keyboard-xaml-view"></a>イマーシブビューからキーボードの XAML ビューへの切り替え

ビュー間を切り替える一般的な理由の1つは、混合の現実のアプリにキーボードを表示することです。 シェルでは、アプリに2D ビューが表示されている場合にのみ、システムキーボードを表示できます。 アプリがテキスト入力を取得する必要がある場合、テキスト入力フィールドを含むカスタム XAML ビューを提供し、それに切り替えて、入力の完了後に切り替えます。

前のセクションと同様に、 **Applicationviewswitch. SwitchAsync** を使用して、イマーシブビューから XAML ビューに戻すことができます。

## <a name="app-size"></a>アプリのサイズ

2D アプリビューは、常に固定の仮想スレートに表示されます。 これにより、すべての2D ビューでまったく同じ量のコンテンツが表示されるようになります。 アプリの2D ビューのサイズの詳細を次に示します。
* サイズ変更中は、アプリの縦横比が維持されます。
* アプリの [解像度とスケールファクター](../develop/porting-apps/building-2d-apps.md#2d-app-view-resolution-and-scale-factor) は、サイズ変更によって変更されることはありません。
* アプリでは、世界中の実際のサイズに対してクエリを実行することはできません。

![固定ウィンドウサイズで2D アプリが表示される](images/12493521-10104043956964683-6118765685995662420-o-500px.jpg)<br>
*2D ビューのアプリが固定ウィンドウサイズで表示される*

## <a name="app-tiles"></a>アプリのタイル

[スタート] メニューでは、標準の小さいタイルと、pin の [中] タイルと [ **すべてのアプリ** ] の一覧が混在しています。 

![Windows Mixed Reality の [スタート] メニュー](images/start-500px.png)<br>
*Windows Mixed Reality の [スタート] メニュー*

## <a name="app-to-app-interactions"></a>アプリ間の対話

アプリを構築すると、Windows 10 で利用可能なアプリ間通信の機能豊富なメカニズムにアクセスできます。 新しいプロトコル Api とファイル登録の多くは、アプリの起動と通信を可能にするために HoloLens で完全に動作します。 

デスクトップヘッドセットの場合、特定のファイル拡張子またはプロトコルに関連付けられているアプリは、デスクトップモニターまたはデスクトップスレートにのみ表示できる Win32 アプリである可能性があることに注意してください。

### <a name="protocols"></a>プロトコル

HoloLens は、Windows.System を介してアプリを起動するアプリをサポート [ しています。ランチャー Api](https://docs.microsoft.com/uwp/api/Windows.System.Launcher)。

別のアプリケーションを起動する場合は、次の点を考慮する必要があります。

* [LaunchUriAsync](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriAsync_Windows_Foundation_Uri_)などの非モーダル起動を実行する場合は、ユーザーがアプリを操作する前に配置する必要があります。

* [Launchuriforの async](https://docs.microsoft.com/uwp/api/Windows.System.Launcher#Windows_System_Launcher_LaunchUriForResultsAsync_Windows_Foundation_Uri_Windows_System_LauncherOptions_Windows_Foundation_Collections_ValueSet_)などを使用してモーダル起動を実行すると、モーダルアプリがウィンドウの上部に配置されます。

* Windows Mixed Reality では、排他ビューの上にアプリケーションを重ね合わせることはできません。 起動したアプリを表示するために、Windows はユーザーを世界に戻し、アプリケーションを表示します。

### <a name="file-pickers"></a>ファイルピッカー

HoloLens では、 [Fileopenpicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileOpenPicker) と [FileSavePicker](https://docs.microsoft.com/uwp/api/Windows.Storage.Pickers.FileSavePicker) コントラクトの両方がサポートされています。 ただし、ファイルピッカーコントラクトを満たすアプリは事前にインストールされていません。 これらのアプリ (たとえば、) は Microsoft Store からインストールできます。

複数のファイルピッカーアプリがインストールされている場合は、どのアプリを起動するかを選択するための不明瞭な UI は表示されません。代わりに、最初にインストールされたファイルピッカーが選択されます。 ファイルを保存するときに、タイムスタンプを含むファイル名が生成されます。 ユーザーはこれを変更できません。

既定では、次の拡張機能がローカルでサポートされています。

|  アプリ  |  拡張機能 | 
|----------|----------|
|  Photos  |  bmp、gif、jpg、png、avi、mov、mp4、wmv | 
|  Microsoft Edge  |  htm、html、pdf、svg、xml | 

### <a name="app-contracts-and-windows-mixed-reality-extensions"></a>アプリコントラクトと Windows Mixed Reality 拡張機能

アプリコントラクトと拡張ポイントを使用すると、ファイル拡張子の処理やバックグラウンドタスクの使用など、より詳細なオペレーティングシステム機能を利用できるようにアプリを登録できます。 これは、HoloLens でサポートされている、サポートされていないコントラクトと拡張ポイントの一覧です。

|  コントラクトまたは拡張機能  |  サポート対象かどうか | 
|----------|----------|
| [アカウント画像プロバイダー (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#account_picture_provider) | サポートされていない | 
| [アラーム](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#alarm) | サポートされていない | 
| [App service](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#app_service) | サポートされていますが完全に機能していません | 
| [予定のプロバイダー](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#appointmnets_provider) | サポートされていない | 
| [自動再生 (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#autoplay) | サポートされていない | 
| [バックグラウンドタスク (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#background_tasts) | 部分的にサポートされている (すべてのトリガーが動作するわけではない) | 
| [タスクの更新 (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#update_task) | サポート | 
| [キャッシュされたファイルアップデーターコントラクト](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#cached_file_updater) | サポート | 
| [カメラの設定 (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#camera_settings) | サポートされていない | 
| [ダイヤルプロトコル](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#dial_protocol) | サポートされていない | 
| [ファイルのアクティブ化 (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_activation) | サポート | 
| [ファイルオープンピッカーコントラクト](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_open_picker_contract) | サポート | 
| [ファイル保存ピッカーコントラクト](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#file_save_picker_contract) | サポート | 
| [ロック画面の呼び出し](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#lock_screen_call) | サポートされていない | 
| [メディア再生](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#media_playback) | サポートされていない | 
| [コントラクトに再生](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#playto_contract) | サポートされていない | 
| [プレインストールした構成タスク](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#preinstalled_config_task) | サポートされていない | 
| [印刷3D ワークフロー](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_3d_workflow) | サポート | 
| [印刷タスクの設定 (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#print_task_settings) | サポートされていない | 
| [URI のアクティブ化 (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#protocol_activation) | サポート | 
| [制限付き起動](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#restricted_launch) | サポートされていない | 
| [検索コントラクト](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#search_contract) | サポートされていない | 
| [設定のコントラクト](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#settings_contract) | サポートされていない | 
| [共有コントラクト](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#share_contract) | サポートされていない | 
| [SSL/証明書 (拡張機能)](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#ssl_certificates) | サポート | 
| [Web アカウントプロバイダー](https://msdn.microsoft.com/library/windows/desktop/hh464906.aspx#web_account_provider) | サポート | 

## <a name="app-file-storage"></a>アプリファイルストレージ

すべてのストレージは、 [Windows のストレージの名前空間](https://docs.microsoft.com/uwp/api/Windows.Storage)を使用します。 詳細については、次のドキュメントを参照してください。 HoloLens では、アプリストレージの同期/ローミングはサポートされていません。

* [ファイル、フォルダー、およびライブラリ](https://docs.microsoft.com/windows/uwp/files/index)
* [設定と他のアプリ データを保存して取得する](https://docs.microsoft.com/windows/uwp/design/app-settings/store-and-retrieve-app-data)

### <a name="known-folders"></a>既知のフォルダー

UWP アプリの詳細については、「 [Knownfolders](https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders) 」を参照してください。

<table>
<tr>
<th> プロパティ</th><th> HoloLens でサポートされています</th><th> イマーシブヘッドセットでサポートされています</th><th> [説明]</th>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_AppCaptures">AppCaptures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>アプリのキャプチャフォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_CameraRoll">CameraRoll</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>カメラロールフォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_DocumentsLibrary">ドキュメントライブラリ</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>ドキュメントライブラリを取得します。 ドキュメントライブラリは、一般に使用するためのものではありません。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MusicLibrary">MusicLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>音楽ライブラリを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Objects3D">Objects3D</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>Objects 3D フォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_PicturesLibrary">PicturesLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>ピクチャライブラリを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_Playlists">プレイリスト</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>再生リストフォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_SavedPictures">SavedPictures</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>保存されているピクチャフォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_VideosLibrary">VideosLibrary</a></td><td style="text-align: center;">✔️</td><td style="text-align: center;">✔️</td><td>ビデオライブラリを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_HomeGroup">ホームグループ</a></td><td></td><td style="text-align: center;">✔️</td><td>ホームグループフォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_MediaServerDevices">MediaServerDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>メディアサーバー (デジタル生活ネットワークアライアンス (DLNA) デバイス) のフォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RecordedCalls">RecordedCalls</a></td><td></td><td style="text-align: center;">✔️</td><td>記録された呼び出しフォルダーを取得します。</td>
</tr><tr>
<td><a href="https://docs.microsoft.com/uwp/api/Windows.Storage.KnownFolders#Windows_Storage_KnownFolders_RemovableDevices">RemovableDevices</a></td><td></td><td style="text-align: center;">✔️</td><td>リムーバブルデバイスのフォルダーを取得します。</td>
</tr>
</table>

## <a name="app-package"></a>アプリ パッケージ

Windows 10 では、オペレーティングシステムを対象にするのではなく、 [アプリを1つ以上のデバイスファミリに対象](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide#device-families)とします。 デバイス ファミリに基づいて、デバイス ファミリのデバイス全体で想定できる API、システム特性、動作を特定します。 また、 [Microsoft Store](../distribute/submitting-an-app-to-the-microsoft-store.md#specifying-target-device-families)からアプリをインストールできるデバイスのセットも決定されます。

* デスクトップヘッドセットと HoloLens の両方を対象にするには、アプリを **Windows ユニバーサル** デバイスファミリに対象とします。
* デスクトップヘッドセットだけを対象にするには、アプリを **Windows デスクトップ** デバイスファミリに対象とします。
* HoloLens だけを対象にするには、アプリを **Holographic** デバイスファミリに対象とします。

## <a name="see-also"></a>関連項目

* [アプリ ビュー](app-views.md)
* [複合現実の 2D UWP アプリを更新する](../develop/porting-apps/building-2d-apps.md)
* [3D アプリ起動ツールの設計ガイダンス](../distribute/3d-app-launcher-design-guidance.md)
* [3D アプリ起動ツールの実装](../distribute/implementing-3d-app-launchers.md)
