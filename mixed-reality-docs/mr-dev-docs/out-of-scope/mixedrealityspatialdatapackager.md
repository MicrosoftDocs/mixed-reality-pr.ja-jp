---
title: Mixed Reality 空間データパッケージャーのドキュメント
description: Mixed Reality 空間データパッケージャーツールは現在非推奨とされており、どのプラットフォームでも機能しなくなりました。 代わりに、マップマネージャーツールをお勧めします。
author: hferrone
ms.author: v-hferrone
ms.date: 08/03/2020
ms.topic: article
keywords: lbe、MixedRealitySpatialDataPackager.exe、MixedRealitySpatialDataPackager
ms.openlocfilehash: df6757730c8a5448d96811bfe4ce024f6942dc07
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686266"
---
# <a name="mixed-reality-spatial-data-packager-documentation"></a>Mixed Reality 空間データパッケージャーのドキュメント

>[!NOTE]
> 非推奨 
> 
> 8/1/2020 の時点で、このツールは非推奨とされ、どのプラットフォームでも機能しなくなりました。 代わりに、デバイスポータルで [マップマネージャー](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) ツールを使用することをお勧めします。 
> 
> このツールとその操作は、そのとおりに提供されます。 予告なしに変更されることがあり、今後の Windows または Windows Mixed Reality のリリースと互換性がない可能性があります。 


## <a name="download"></a>ダウンロード
 [MixedRealitySpatialDataPackager をこちら](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)からダウンロード

## <a name="device-support"></a>デバイス サポート

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>機能</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>Mixed Reality 空間データパッケージャー</td>
        <td>❌</td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="quickstart"></a>クイックスタート

Mixed Reality 空間データパッケージャーツールは、エクスポートとインポートの2つの手順を通じて、ターゲットアプリの空間データをある PC から別の PC にコピーします。 このツールは、管理者特権で実行する必要があり、インポート時に既存の空間データを削除します。 Export は、既存の空間データをそのまま残します。

重要な要件と制限事項:

1. ツールは、管理者特権で実行する必要があります 
2. ツールを実行した後に Mixed Reality ポータルが不安定な場合は、PC の再起動が必要になることがあります
3. 空間データのバージョンの不一致または非互換性の検出時にツールが実行されない
4. インポート時に既存の空間データが消去されます
5. インポート処理が失敗した場合、以前のデータをエクスポートしてバックアップしていない限り、以前のデータを復元することはできません。
6. 空間マップデータの "読み取り専用" モードでのインポート機能の品質
***

## <a name="mapping-best-practices"></a>マッピングのベストプラクティス

1. コントロールパネルから既存のマップをクリアする (設定 > Mixed Reality-> Environment-環境データをクリア >)
2. 適切な追跡に十分な照明を確保し、ロックされたマップモードを実行している場合は、同じ照明を維持します
3. 可能な場合は、暗い領域、影付き領域の横に高い照明の領域を避けて、光源の範囲を小さくします。
4. 空白の領域を最小化する (たとえば、異なるポスターの範囲をホワイトウォールに配置する)
5. オブジェクトの移動など、シーンに動的オブジェクトを使用せずに領域をマップする
6. インポート時にマップをロックする (Insider Preview 経由で利用可能)
7. 品質の追跡が低下したとき、または環境に変化があった場合に、マップのロックを解除して環境を再スキャンする (照明またはオブジェクトのレイアウトの変更)
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a>コンパニオンスクリプトを使用した Mixed Reality 空間データパッケージャーの実行

ツールのマップを実行する MRSpatialPackagerHelperScript.ps1 が用意されています。 


スクリプトのパラメーターは次のように定義されています。

```
-AppName <String>
    On export: The spatial anchors from the app of interest
    On import: The target app that spatial anchors should be imported for
    Returns a list of apps containing the input string if a unique app is not found

-UserName <String>
    Target username, will return a list of users if a unique match is not found

-Mode <String>
    import or export

-MapxPath <String>
    On export: Directory to export your mapx files
    On import: Directory where import mapx are stored

-LockMap <Int32>
    0 to unlock map
    1 to lock map

-BinPath <String>
    Path to MixedRealitySpatialDataPackager.exe, default value is current directory
```

### <a name="powershell-script-example-usage-and-output"></a>Powershell スクリプトの使用例と出力

.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-UserName D:\temp\-MapxPath-LockMap 0
```
Package Family Name for holoshell: HoloShell_cw5n1h2txyewy
User SID for Administrator: S-1-5-21-1279937937-3984375698-1043392598-499
Lock map value successfully set to 0

Running: C:\bin\MixedRealitySpatialDataPackager.exe export D:\temp\ HoloShell_cw5n1h2txyewy S-1-5-21-1279937937-3984375698-1043392598-499

Attempting to disable Windows MR driver
Driver disabled
Validating spatial data version information...
Device spatial data version OK
External spatial data version OK
Importing spatial anchors for user account phguan
Stopping SPECTRUM
Stopped SPECTRUM
Stopping SHAREDREALITYSVC
Stopped SHAREDREALITYSVC
Space ID is {00000000-4321-0000-0000-000000000000}
SUCCESS: Unpacked Space from D:\temp\map\het.mapx to
C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors\{00000000-4321-0000-0000-000000000000}\
Space ID is {78FA06B5-4416-4815-BB00-B3CB5C983B7D}
SUCCESS: Unpacked Space from D:\temp\map\sa.mapx to
C:\ProgramData\Microsoft\Spectrum\PersistedSpatialAnchors\
Attempting to enable Windows MR driver
Driver enabled
Starting SHAREDREALITYSVC
Started SHAREDREALITYSVC
Starting SPECTRUM
Started SPECTRUM
IMPORT SUCCESS
```

### <a name="how-to-export-using-mixedrealityspatialdatapackagerexe"></a>MixedRealitySpatialDataPackager.exe を使用してエクスポートする方法
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

デバイスからマップをエクスポートすると、het. mapx と sa. mapx という2つの mapx ファイルが生成されます。 エクスポートプロセスでは、指定されたアプリとユーザーが作成した境界 (存在する場合) を除き、すべての空間アンカーが削除されます。 ソースパッケージファミリ名は、インストールされている既存のアプリと一致する必要があります。一致しないと、exe は失敗します。

### <a name="how-to-import-using-mixedrealityspatialdatapackagerexe"></a>MixedRealitySpatialDataPackager.exe を使用してインポートする方法
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
インポートによって既存の空間データが削除され、指定したディレクトリのデータで置き換えられます。 アプリ名の入力では、空間アンカーをインポートする対象アプリのパッケージ名を指定し、ターゲットユーザー SID で、インポートされた空間アンカーへのアクセス権を持つユーザーを指定します。 ターゲットパッケージファミリ名とユーザー Sid が PC 上の既存の値と一致している必要があります。指定しないと、exe は失敗します。


***
## <a name="error-messages"></a>エラー メッセージ
さらに、次のエラーメッセージにも HRESULT が付随します。

### <a name="if-there-was-an-error-invalid-arguments"></a>エラーが発生した場合は、無効な引数
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a>実行可能ファイルが管理者モードで実行されなかった場合
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a>ドライバーの有効化または無効化でエラーが発生した場合
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a>空間データベースバージョンの検証中にエラーが発生した場合
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a>ターゲットのインポート/エクスポートアプリに指定されたパッケージファミリ名の検証中にエラーが発生した場合
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a>ユーザー SID の検証中にエラーが発生した場合
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a>コピー先またはコピー元の空間データファイルに関連するエラーが発生した場合
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a>スペクトラムの開始と停止に関連するエラーが発生した場合は、
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
