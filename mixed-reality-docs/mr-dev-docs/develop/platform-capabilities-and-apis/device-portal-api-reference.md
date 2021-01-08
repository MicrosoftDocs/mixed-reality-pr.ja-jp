---
title: Device Portal API リファレンス
description: HoloLens 開発用の Windows Device Portal API の最新情報を入手できます。
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens、Windows デバイスポータル、API、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実のヘッドセット
ms.openlocfilehash: 13845a5a5668ee8c86178196326425f46be9b321
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006652"
---
# <a name="device-portal-api-reference"></a>Device Portal API リファレンス

[Windows デバイスポータル](using-the-windows-device-portal.md)のすべての機能は REST API の上に構築されており、データにアクセスしたり、デバイスをプログラムで制御したりするために使用できます。

## <a name="app-deloyment"></a>アプリの撮る

**/api/app/packagemanager/package (削除)**

アプリをアンインストールします

パラメーター
* パッケージ: アンインストールするパッケージのファイル名。

**/api/app/packagemanager/package (POST)**

アプリをインストールします

パラメーター
* パッケージ: インストールするパッケージのファイル名。

ペイロード
* マルチパート準拠の http 本文

**/api/app/packagemanager/packages (GET)**

システムにインストールされているアプリの一覧を詳細と共に取得します。

データを返します
* インストールされているパッケージの一覧と詳細

**/api/app/packagemanager/state (GET)**

進行中のアプリのインストールの状態を取得します

## <a name="dump-collection"></a>ダンプの収集

**/api/debug/dump/usermode/crashcontrol (削除)**

サイドロードアプリのクラッシュダンプの収集を無効にします。

パラメーター
* packageFullname: パッケージ名

**/api/debug/dump/usermode/crashcontrol (GET)**

サイドロード apps のクラッシュダンプの収集の設定を取得します。

パラメーター
* packageFullname: パッケージ名

**/api/debug/dump/usermode/crashcontrol (POST)**

サイドロードアプリのダンプ制御設定を有効にして設定します

パラメーター
* packageFullname: パッケージ名

**/api/debug/dump/usermode/crashdump (削除)**

サイドロードアプリのクラッシュダンプを削除します。

パラメーター
* packageFullname: パッケージ名
* fileName: ダンプファイル名

**/api/debug/dump/usermode/crashdump (GET)**

サイドロードアプリのクラッシュダンプを取得します。

パラメーター
* packageFullname: パッケージ名
* fileName: ダンプファイル名

データを返します
* ダンプファイル。 WinDbg または Visual Studio を使用して検査する

**/api/debug/dump/usermode/dumps (GET)**

サイドロードアプリのすべてのクラッシュダンプの一覧を返します。

データを返します
* サイドロードされたアプリごとのクラッシュダンプの一覧

## <a name="etw"></a>ETW

**/api/etw/providers (GET)**

登録されたプロバイダーを列挙します

データを返します
* プロバイダー、フレンドリ名、GUID の一覧

**/api/etw/session/realtime (GET/WebSocket)**

リアルタイム ETW セッションを作成します。websocket 経由で管理されます。

データを返します
* 有効なプロバイダーからの ETW イベント

## <a name="holographic-os"></a>ホログラフィック OS

**/api/holographic/os/etw/customproviders (GET)**

システムに登録されていない HoloLens 固有の ETW プロバイダーの一覧を返します。

**/api/holographic/os/services (GET)**

実行中のすべてのサービスの状態を返します。

**/api/holographic/os/settings/ipd (GET)**

格納されている IPD (Interpupillary distance) をミリメートル単位で取得します。

**/api/holographic/os/settings/ipd (POST)**

IPD を設定します。

パラメーター
* ipd: mm で設定する新しい IPD 値

**/api/holographic/os/webmanagement/settings/https (GET)**

Device Portal の HTTPS 要件を取得する

**/api/holographic/os/webmanagement/settings/https (POST)**

デバイスポータルの HTTPS 要件を設定します。

パラメーター
* 必須: はい、いいえ、または既定値

## <a name="holographic-perception"></a>Holographic の認識

**/api/holographic/perception/client (GET/WebSocket)**

Websocket のアップグレードを受け入れ、30 fps で更新を送信する認識クライアントを実行します。

パラメーター
* clientmode: "active" は、受動的に確立できないときにビジュアル追跡モードを強制します。

## <a name="holographic-thermal"></a>Holographic Thermal

**/api/holographic/thermal/stage (GET)**

デバイスの温度ステージを取得する (通常は0、1ウォーム、2重大)

## <a name="map-manager"></a>Map Manager

**/api/holographic/mapmanager/mapFiles (GET)**

使用可能なマップファイル (mapx) の一覧を取得します。

**/api/holographic/mapmanager/anchorFiles (GET)**

使用できるアンカーファイル (.. x) の一覧を取得します。

**/api/holographic/mapmanager/srdbFiles (GET)**

使用可能な空間再構築データベースファイル (srdb) の一覧を取得します。

**/api/holographic/mapmanager/getanchors (GET)**

現在のユーザーに対して保持されているアンカーの一覧を取得します。 

### <a name="downloaduploaddelete-files"></a>ファイルのダウンロード/アップロード/削除
**/api/holographic/mapmanager/download (GET)**

マップ、アンカー、または空間再構築データベースファイルをダウンロードします。 ファイルは、既にアップロードまたはエクスポートされている必要があります。

パラメーター
* FileName: ダウンロードするファイルの名前。

例: 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

**/api/holographic/mapmanager/upload (POST)**

マップ、アンカー、または空間再構築データベースファイルをアップロードします。 ファイルがアップロードされると、後でシステムによって使用されるようにインポートできます。

パラメーター
* file: アップロードするファイルの名前。

例:
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

**/api/holographic/mapmanager/delete (POST)**

マップ、アンカー、または空間再構築データベースファイルを削除します。 ファイルは、既にアップロードまたはエクスポートされている必要があります。

パラメーター
* FileName: 削除するファイルの名前。

例: 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a>エクスポート

**/api/holographic/mapmanager/export (POST)**

システムによって現在使用されているマップをエクスポートします。 エクスポートが完了すると、ダウンロードできます。 

例: 
```
$.post("/api/holographic/mapmanager/export")
```

**/api/holographic/mapmanager/exportanchors (POST)**

システムによって現在使用されているマップをエクスポートします。 エクスポートが完了すると、ダウンロードできます。 例: 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

**/api/holographic/mapmanager/exportmapandanchors (POST)**

システムによって現在使用されているマップおよびアンカーをエクスポートします。 をエクスポートすると、ダウンロードできます。 例: 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**

システムによって現在使用されているマップおよび空間再構築データベースをエクスポートします。 エクスポートされると、ダウンロードできます。 

例: 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a>[インポート]

**/api/holographic/mapmanager/import (POST)**

現在使用されているマップをシステムに示します。 は、エクスポートまたはアップロードされたファイルに対して呼び出すことができます。

パラメーター
* FileName: 使用するマップの名前。 

例: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

**/api/holographic/mapmanager/importanchors (POST)**

現在使用されているアンカーをシステムに示します。 は、エクスポートまたはアップロードされたファイルに対して呼び出すことができます。

パラメーター
* FileName: 使用するアンカーの名前。 

例: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

**/api/holographic/mapmanager/importspatialmappingdb (POST)**

現在使用されている空間再構築データベースをシステムに指示します。 は、エクスポートまたはアップロードされたファイルに対して呼び出すことができます。

パラメーター
* FileName: 使用する空間マッピング db の名前。 

例: 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a>その他

**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**

マップ、アンカー、および空間再構築データベースをシステムにリセットします。

例: 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

**/api/holographic/mapmanager/status (GET)**

最後にインポートされたマップ、アンカー、および空間再構築データベースファイルを含む、システムの状態を取得します。 


## <a name="mixed-reality-capture"></a>Mixed Reality キャプチャ

**/api/holographic/mrc/file (GET)**

混合の現実ファイルをデバイスからダウンロードします。 ストリーミングには op = stream クエリパラメーターを使用します。

パラメーター
* filename: 取得するビデオファイルの名前、hex64 encoded
* op: ストリーム

**/api/holographic/mrc/file (削除)**

デバイスから mixed reality の記録を削除します。

パラメーター
* filename: 削除するファイルの名前、hex64 encoded

**/api/holographic/mrc/files (GET)**

デバイスに格納されている mixed reality ファイルの一覧を返します。

**/api/holographic/mrc/photo (POST)**

Mixed reality の写真を取得し、デバイスにファイルを作成します。

パラメーター
* holo: キャプチャホログラム: true または false (既定値は false)
* pv: キャプチャの PV カメラ: true または false (既定値は false)
* RenderFromCamera: (HoloLens 2 のみ) 写真/ビデオカメラから見たレンダリング: true または false (既定値は true)

**/api/holographic/mrc/settings (GET)**

既定の mixed reality キャプチャ設定を取得します。

**/api/holographic/mrc/settings (POST)**

既定の mixed reality キャプチャ設定を設定します。  これらの設定の一部は、システムの MRC の写真とビデオキャプチャに適用されます。

**/api/holographic/mrc/status (GET)**

Windows デバイスポータル内の mixed reality キャプチャの状態を取得します。

**_応答_* _

応答には、Windows デバイスポータルがビデオを記録しているかどうかを示す JSON プロパティが含まれています。

``` javascript
{"IsRecording" : boolean}
```

_ */api/holographic/mrc/thumbnail (GET)**

指定したファイルのサムネイルイメージを取得します。

パラメーター
* filename: サムネイルが要求されているファイルの名前 (hex64 encoded)

**/api/holographic/mrc/video/control/start (POST)**

Mixed reality の記録を開始します

パラメーター
* holo: キャプチャホログラム: true または false (既定値は false)
* pv: キャプチャの PV カメラ: true または false (既定値は false)
* mic: キャプチャマイク: true または false (既定値は false)
* ループバック: キャプチャアプリオーディオ: true または false (既定値は false)
* RenderFromCamera: (HoloLens 2 のみ) 写真/ビデオカメラから見たレンダリング: true または false (既定値は true)
* vstab: (HoloLens 2 のみ) ビデオ安定化を有効にします。 true または false (既定値は true)
* vstabbuffer: (HoloLens 2 のみ) ビデオ安定化バッファー待機時間: 0 ~ 30 フレーム (既定値は15フレーム)

**/api/holographic/mrc/video/control/stop (POST)**

現在の mixed reality 記録を停止します

## <a name="mixed-reality-streaming"></a>Mixed Reality ストリーミング

> [!CAUTION]
> ループバックが分離されているため、デバイス上のアプリ内から Mixed Reality ストリーミングに接続することはできません。

HoloLens は、フラグメント化された mp4 のチャンクダウンロードを使用して、混合現実のライブプレビューをサポートします。

混合現実のストリームは、キャプチャ対象を制御するために、同じパラメーターのセットを共有します。
* holo: キャプチャホログラム: true または false
* pv: キャプチャの PV カメラ: true または false
* mic: マイクのキャプチャ: true または false
* ループバック: アプリオーディオのキャプチャ: true または false

これらのいずれも指定されていない場合、ホログラム、photo/video カメラ、アプリオーディオがキャプチャされます。<br>
指定されている場合: 未指定のパラメーターは既定で false に設定されます。

省略可能なパラメーター (HoloLens 2 のみ)
* RenderFromCamera: 写真/ビデオカメラから見たレンダリング: true または false (既定値は true)
* vstab: ビデオ安定化を有効にします。 true または false (既定値は false)
* vstabbuffer: ビデオ安定化バッファー待機時間: 0 ~ 30 フレーム (既定では15フレーム)

**/api/holographic/stream/live.mp4 (GET)**

1280x720p 30 fps 5 Mbit ストリーム。

**/api/holographic/stream/live_high.mp4 (GET)**

1280x720p 30 fps 5 Mbit ストリーム。

**/api/holographic/stream/live_med.mp4 (GET)**

854x480p 30 fps 2.5 Mbit ストリーム。

**/api/holographic/stream/live_low.mp4 (GET)**

428x240p 15fps 0.6 Mbit ストリーム。

## <a name="networking"></a>ネットワーク

**/api/networking/ipconfig (GET)**

現在の ip 構成を取得します。

## <a name="os-information"></a>OS 情報

**/api/info (GET)**

オペレーティングシステム情報を取得します。

**/api/machinename (GET)**

コンピューター名を取得します。

**/api/machinename (POST)**

コンピューター名を設定します

パラメーター
* [名前]: 新しいコンピューター名、hex64 encoded、をに設定します。

## <a name="perception-simulation-control"></a>認識シミュレーションの制御

**/api/holographic/simulation/control/mode (GET)**

シミュレーションモードを取得する

**/api/holographic/simulation/control/mode (POST)**

シミュレーションモードの設定

パラメーター
* モード: シミュレーションモード: 既定、シミュレーション、リモート、レガシ

**/api/holographic/simulation/control/stream (削除)**

コントロールストリームを削除します。

**/api/holographic/simulation/control/stream (GET/WebSocket)**

コントロールストリームの web ソケット接続を開きます。

**/api/holographic/simulation/control/stream (POST)**

コントロールストリームを作成するか (優先順位が必要)、作成されたストリームにデータを post します (streamId が必要)。 ポストされたデータは ' application/オクテット-stream ' 型である必要があります。

**/api/holographic/simulation/display/stream (GET/WebSocket)**

"シミュレーション" モードで、システムに表示されるコンテンツを含むシミュレーションビデオストリームを要求します。  単純なフォーマット記述子ヘッダーが最初に送信され、その後に h.264 でエンコードされたテクスチャが続きます。それぞれのヘッダーには、目のインデックスとテクスチャサイズが示されます。

## <a name="perception-simulation-playback"></a>認識シミュレーションの再生

**/api/holographic/simulation/playback/file (削除)**

記録を削除します。

パラメーター
* 記録: 削除する記録の名前。

**/api/holographic/simulation/playback/file (POST)**

記録をアップロードします。

**/api/holographic/simulation/playback/files (GET)**

すべての記録を取得します。

**/api/holographic/simulation/playback/session (GET)**

記録の現在の再生状態を取得します。

パラメーター
* 記録: 記録の名前。

**/api/holographic/simulation/playback/session/file (削除)**

記録をアンロードします。

パラメーター
* 記録: アンロードする記録の名前。

**/api/holographic/simulation/playback/session/file (POST)**

記録を読み込みます。

パラメーター
* 記録: 読み込む記録の名前。

**/api/holographic/simulation/playback/session/files (GET)**

読み込まれたすべての録音を取得します。

**/api/holographic/simulation/playback/session/pause (POST)**

記録を一時停止します。

パラメーター
* 記録: 記録の名前。

**/api/holographic/simulation/playback/session/play (POST)**

録音を再生します。

パラメーター
* 記録: 記録の名前。

**/api/holographic/simulation/playback/session/stop (POST)**

記録を停止します。

パラメーター
* 記録: 記録の名前。

**/api/holographic/simulation/playback/session/types (GET)**

読み込まれた記録のデータの種類を取得します。

パラメーター
* 記録: 記録の名前。

## <a name="perception-simulation-recording"></a>認識のシミュレーション記録

**/api/holographic/simulation/recording/start (POST)**

記録を開始します。 一度にアクティブにできる記録は1つだけです。 ヘッド、ハンド、spatialMapping、または環境のいずれかを設定する必要があります。

パラメーター
* head: 1 に設定すると、ヘッドデータが記録されます。
* 手: 1 に設定すると、手のデータが記録されます。
* spatialMapping: 空間マッピングを記録するには、1に設定します。
* 環境: 1 に設定すると、環境データが記録されます。
* 名前: 記録の名前。
* singleSpatialMappingFrame: 1 に設定すると、空間マッピングフレームが1つだけ記録されます。

**/api/holographic/simulation/recording/status (GET)**

記録の状態を取得します。

**/api/holographic/simulation/recording/stop (GET)**

現在の記録を停止します。 記録はファイルとして返されます。

## <a name="performance-data"></a>パフォーマンス データ

**/api/resourcemanager/processes (GET)**

詳細を含む実行中のプロセスの一覧を返します

データを返します
* 各プロセスのプロセスと詳細の一覧を含む JSON

**/api/resourcemanager/systemperf (GET)**

システムパフォーマンス統計情報 (i/o 読み取り/書き込み、メモリ統計など) を返します。

データを返します
* システム情報を含む JSON: CPU、GPU、メモリ、ネットワーク、IO

## <a name="power"></a>Power

**/api/バッテリ (GET)**

現在のバッテリの状態を取得します。

**//(GET)**

システムが低電力状態であるかどうかを確認します

## <a name="remote-control"></a>リモート コントロール

**/api/control/restart (POST)**

ターゲットデバイスを再起動します

**/api/control/shutdown (POST)**

ターゲットデバイスをシャットダウンします

## <a name="task-manager"></a>タスク マネージャー

**/api/taskmanager/app (削除)**

モダンアプリを停止します

パラメーター
* パッケージ: アプリパッケージの完全名、hex64 encoded
* forcestop: すべてのプロセスを強制的に停止します (= yes)

**/api/taskmanager/app (POST)**

モダンアプリを開始します

パラメーター
* appid: アプリの開始、hex64 エンコード
* パッケージ: アプリパッケージの完全名、hex64 encoded

## <a name="wifi-management"></a>WiFi の管理

**/api/wifi/interfaces (GET)**

ワイヤレスネットワークインターフェイスを列挙します。

データを返します
* 詳細 (GUID、説明など) があるワイヤレスインターフェイスの一覧

**/api/wifi/network (削除)**

指定したインターフェイスのネットワークに関連付けられているプロファイルを削除します。

パラメーター
* インターフェイス: ネットワークインターフェイス guid
* プロファイル: プロファイル名

**/api/wifi/networks (GET)**

指定されたネットワークインターフェイスのワイヤレスネットワークを列挙します

パラメーター
* インターフェイス: ネットワークインターフェイス guid

データを返します
* ネットワークインターフェイスで検出されたワイヤレスネットワークの一覧と詳細

**/api/wifi/network (POST)**

指定されたインターフェイスでネットワークに接続または切断します。

パラメーター
* インターフェイス: ネットワークインターフェイス guid
* ssid: 接続先の ssid、hex64 encoded、
* op: 接続または切断
* createprofile: はいまたはいいえ
* キー: shared key、hex64 encoded

## <a name="windows-performance-recorder"></a>Windows パフォーマンス レコーダー

**/api/wpr/customtrace (POST)**

WPR プロファイルをアップロードし、アップロードされたプロファイルを使用してトレースを開始します。

ペイロード
* マルチパート準拠の http 本文

データを返します
* WPR セッションの状態を返します。

**/api/wpr/status (GET)**

WPR セッションの状態を取得します。

データを返します
* WPR セッションの状態。

**/api/wpr/trace (GET)**

WPR (パフォーマンス) トレースセッションを停止します

データを返します
* トレース ETL ファイルを返します。

**/api/wpr/trace (POST)**

WPR (パフォーマンス) トレースセッションを開始します

パラメーター
* プロファイル: プロファイル名。 使用可能なプロファイルは、の perfprofiles/profiles.jsに格納されます。

データを返します
* 開始時に、WPR セッションの状態を返します。

## <a name="see-also"></a>関連項目
* [Windows Device Portal を使用する](using-the-windows-device-portal.md)
* [デバイスポータルコア API リファレンス (UWP)](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
