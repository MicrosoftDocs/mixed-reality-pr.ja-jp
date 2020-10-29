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
# <a name="mixed-reality-spatial-data-packager-documentation"></a><span data-ttu-id="23fde-105">Mixed Reality 空間データパッケージャーのドキュメント</span><span class="sxs-lookup"><span data-stu-id="23fde-105">Mixed Reality Spatial Data Packager Documentation</span></span>

>[!NOTE]
> <span data-ttu-id="23fde-106">非推奨</span><span class="sxs-lookup"><span data-stu-id="23fde-106">DEPRECATED</span></span> 
> 
> <span data-ttu-id="23fde-107">8/1/2020 の時点で、このツールは非推奨とされ、どのプラットフォームでも機能しなくなりました。</span><span class="sxs-lookup"><span data-stu-id="23fde-107">As of 8/1/2020 this tool is now deprecated and no longer functions on any platform.</span></span> <span data-ttu-id="23fde-108">代わりに、デバイスポータルで [マップマネージャー](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) ツールを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="23fde-108">We recommend using the [Map Manager](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) tool in the Device Portal instead.</span></span> 
> 
> <span data-ttu-id="23fde-109">このツールとその操作は、そのとおりに提供されます。</span><span class="sxs-lookup"><span data-stu-id="23fde-109">This tool and its operation are offered as-is.</span></span> <span data-ttu-id="23fde-110">予告なしに変更されることがあり、今後の Windows または Windows Mixed Reality のリリースと互換性がない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="23fde-110">It is subject to change without any notice and may not be compatible with future Windows or Windows Mixed Reality HMD releases.</span></span> 


## <a name="download"></a><span data-ttu-id="23fde-111">ダウンロード</span><span class="sxs-lookup"><span data-stu-id="23fde-111">Download</span></span>
 <span data-ttu-id="23fde-112">[MixedRealitySpatialDataPackager をこちら](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)からダウンロード</span><span class="sxs-lookup"><span data-stu-id="23fde-112">Download [MixedRealitySpatialDataPackager here](https://download.microsoft.com/download/A/1/2/A12B8A90-B3F7-4ED9-A4BB-D59DDCDAA125/MixedRealitySpatialDataPackager.zip)</span></span>

## <a name="device-support"></a><span data-ttu-id="23fde-113">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="23fde-113">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="23fde-114"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="23fde-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="23fde-115"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="23fde-115"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="23fde-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="23fde-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="23fde-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="23fde-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="23fde-118">Mixed Reality 空間データパッケージャー</span><span class="sxs-lookup"><span data-stu-id="23fde-118">Mixed Reality Spatial Data Packager</span></span></td>
        <td>❌</td>
        <td>❌</td>
        <td><span data-ttu-id="23fde-119">✔️</span><span class="sxs-lookup"><span data-stu-id="23fde-119">✔️</span></span></td>
    </tr>
</table>

## <a name="quickstart"></a><span data-ttu-id="23fde-120">クイックスタート</span><span class="sxs-lookup"><span data-stu-id="23fde-120">Quickstart</span></span>

<span data-ttu-id="23fde-121">Mixed Reality 空間データパッケージャーツールは、エクスポートとインポートの2つの手順を通じて、ターゲットアプリの空間データをある PC から別の PC にコピーします。</span><span class="sxs-lookup"><span data-stu-id="23fde-121">The Mixed Reality Spatial Data Packager tool copies the spatial data of a target app from one PC to another through a two step export and import process.</span></span> <span data-ttu-id="23fde-122">このツールは、管理者特権で実行する必要があり、インポート時に既存の空間データを削除します。</span><span class="sxs-lookup"><span data-stu-id="23fde-122">The tool must be run with administrator privileges and deletes the existing spatial data on import.</span></span> <span data-ttu-id="23fde-123">Export は、既存の空間データをそのまま残します。</span><span class="sxs-lookup"><span data-stu-id="23fde-123">Export leaves the existing spatial data intact.</span></span>

<span data-ttu-id="23fde-124">重要な要件と制限事項:</span><span class="sxs-lookup"><span data-stu-id="23fde-124">Key requirements and limitations:</span></span>

1. <span data-ttu-id="23fde-125">ツールは、管理者特権で実行する必要があります</span><span class="sxs-lookup"><span data-stu-id="23fde-125">Tool must be run with administrator privileges</span></span> 
2. <span data-ttu-id="23fde-126">ツールを実行した後に Mixed Reality ポータルが不安定な場合は、PC の再起動が必要になることがあります</span><span class="sxs-lookup"><span data-stu-id="23fde-126">You may have to restart PC if Mixed Reality Portal is unstable after running the tool</span></span>
3. <span data-ttu-id="23fde-127">空間データのバージョンの不一致または非互換性の検出時にツールが実行されない</span><span class="sxs-lookup"><span data-stu-id="23fde-127">Tool will not run when encountering spatial data version mismatches or incompatibilities</span></span>
4. <span data-ttu-id="23fde-128">インポート時に既存の空間データが消去されます</span><span class="sxs-lookup"><span data-stu-id="23fde-128">Tool will erase existing spatial data on import</span></span>
5. <span data-ttu-id="23fde-129">インポート処理が失敗した場合、以前のデータをエクスポートしてバックアップしていない限り、以前のデータを復元することはできません。</span><span class="sxs-lookup"><span data-stu-id="23fde-129">If import process fails previous data cannot be restored unless it has been backed up by exporting previously</span></span>
6. <span data-ttu-id="23fde-130">空間マップデータの "読み取り専用" モードでのインポート機能の品質</span><span class="sxs-lookup"><span data-stu-id="23fde-130">Quality of import functionality contingent on “Read-Only” mode for spatial map data</span></span>
***

## <a name="mapping-best-practices"></a><span data-ttu-id="23fde-131">マッピングのベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="23fde-131">Mapping Best Practices</span></span>

1. <span data-ttu-id="23fde-132">コントロールパネルから既存のマップをクリアする (設定 > Mixed Reality-> Environment-環境データをクリア >)</span><span class="sxs-lookup"><span data-stu-id="23fde-132">Clear existing maps from the Control Panel (Settings -> Mixed Reality -> Environment -> Clear environment data)</span></span>
2. <span data-ttu-id="23fde-133">適切な追跡に十分な照明を確保し、ロックされたマップモードを実行している場合は、同じ照明を維持します</span><span class="sxs-lookup"><span data-stu-id="23fde-133">Ensure sufficient lighting for good tracking and if running locked map mode try to maintain the same lighting</span></span>
3. <span data-ttu-id="23fde-134">可能な場合は、暗い領域、影付き領域の横に高い照明の領域を避けて、光源の範囲を小さくします。</span><span class="sxs-lookup"><span data-stu-id="23fde-134">When possible keep the lighting dynamic range low by avoiding areas of high illumination next to dark, shadowed areas</span></span>
4. <span data-ttu-id="23fde-135">空白の領域を最小化する (たとえば、異なるポスターの範囲をホワイトウォールに配置する)</span><span class="sxs-lookup"><span data-stu-id="23fde-135">Minimize blank, textureless surfaces e.g. place a range of different posters on white walls</span></span>
5. <span data-ttu-id="23fde-136">オブジェクトの移動など、シーンに動的オブジェクトを使用せずに領域をマップする</span><span class="sxs-lookup"><span data-stu-id="23fde-136">Map the space without dynamic objects in the scene such as moving people</span></span>
6. <span data-ttu-id="23fde-137">インポート時にマップをロックする (Insider Preview 経由で利用可能)</span><span class="sxs-lookup"><span data-stu-id="23fde-137">Lock the map on import (available via Insider Preview)</span></span>
7. <span data-ttu-id="23fde-138">品質の追跡が低下したとき、または環境に変化があった場合に、マップのロックを解除して環境を再スキャンする (照明またはオブジェクトのレイアウトの変更)</span><span class="sxs-lookup"><span data-stu-id="23fde-138">Unlock the map and rescan the environment when tracking quality degrades and/or there are changes in the environment (lighting or changes in object layout)</span></span>
***

## <a name="running-mixed-reality-spatial-data-packager-with-companion-script"></a><span data-ttu-id="23fde-139">コンパニオンスクリプトを使用した Mixed Reality 空間データパッケージャーの実行</span><span class="sxs-lookup"><span data-stu-id="23fde-139">Running Mixed Reality Spatial Data Packager with Companion Script</span></span>

<span data-ttu-id="23fde-140">ツールのマップを実行する MRSpatialPackagerHelperScript.ps1 が用意されています。</span><span class="sxs-lookup"><span data-stu-id="23fde-140">We have provided MRSpatialPackagerHelperScript.ps1 that runs the map packager the tools.</span></span> 


<span data-ttu-id="23fde-141">スクリプトのパラメーターは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="23fde-141">The script parameters are defined below:</span></span>

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

### <a name="powershell-script-example-usage-and-output"></a><span data-ttu-id="23fde-142">Powershell スクリプトの使用例と出力</span><span class="sxs-lookup"><span data-stu-id="23fde-142">Powershell Script Example Usage and Output</span></span>

<span data-ttu-id="23fde-143">.\MRSpatialPackagerHelperScript.ps1-AppName holoshell-UserName D:\temp\-MapxPath-LockMap 0</span><span class="sxs-lookup"><span data-stu-id="23fde-143">.\MRSpatialPackagerHelperScript.ps1 -AppName holoshell -UserName Administrator -Mode export -MapxPath D:\temp\ -LockMap 0</span></span>
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

### <a name="how-to-export-using-mixedrealityspatialdatapackagerexe"></a><span data-ttu-id="23fde-144">MixedRealitySpatialDataPackager.exe を使用してエクスポートする方法</span><span class="sxs-lookup"><span data-stu-id="23fde-144">How to Export using MixedRealitySpatialDataPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe export <folderpath to mapx files> <source package family name>    
```

<span data-ttu-id="23fde-145">デバイスからマップをエクスポートすると、het. mapx と sa. mapx という2つの mapx ファイルが生成されます。</span><span class="sxs-lookup"><span data-stu-id="23fde-145">Exporting maps off device generates two mapx files, het.mapx and sa.mapx.</span></span> <span data-ttu-id="23fde-146">エクスポートプロセスでは、指定されたアプリとユーザーが作成した境界 (存在する場合) を除き、すべての空間アンカーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="23fde-146">During the export process all spatial anchors are removed except for the specified app and the user-created boundary (if it exists).</span></span> <span data-ttu-id="23fde-147">ソースパッケージファミリ名は、インストールされている既存のアプリと一致する必要があります。一致しないと、exe は失敗します。</span><span class="sxs-lookup"><span data-stu-id="23fde-147">The source package family name must match an existing installed app or the exe will fail.</span></span>

### <a name="how-to-import-using-mixedrealityspatialdatapackagerexe"></a><span data-ttu-id="23fde-148">MixedRealitySpatialDataPackager.exe を使用してインポートする方法</span><span class="sxs-lookup"><span data-stu-id="23fde-148">How to Import using MixedRealitySpatialDataPackager.exe</span></span>
```
MixedRealitySpatialDataPackager.exe import <folderpath to mapx files> <target package family name> <user SID>
```
<span data-ttu-id="23fde-149">インポートによって既存の空間データが削除され、指定したディレクトリのデータで置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="23fde-149">Import deletes the existing spatial data and replaces it with the data from the specified directory.</span></span> <span data-ttu-id="23fde-150">アプリ名の入力では、空間アンカーをインポートする対象アプリのパッケージ名を指定し、ターゲットユーザー SID で、インポートされた空間アンカーへのアクセス権を持つユーザーを指定します。</span><span class="sxs-lookup"><span data-stu-id="23fde-150">The app name input specifies the package name of the target app that like the spatial anchors should be imported for and the target user SID specifies the user that should have access to the imported spatial anchors.</span></span> <span data-ttu-id="23fde-151">ターゲットパッケージファミリ名とユーザー Sid が PC 上の既存の値と一致している必要があります。指定しないと、exe は失敗します。</span><span class="sxs-lookup"><span data-stu-id="23fde-151">The target package family name and user SIDs must match existing values on the PC or the exe will fail.</span></span>


***
## <a name="error-messages"></a><span data-ttu-id="23fde-152">エラー メッセージ</span><span class="sxs-lookup"><span data-stu-id="23fde-152">Error Messages</span></span>
<span data-ttu-id="23fde-153">さらに、次のエラーメッセージにも HRESULT が付随します。</span><span class="sxs-lookup"><span data-stu-id="23fde-153">In addition the error messages below failures will also be accompanied with an HRESULT</span></span>

### <a name="if-there-was-an-error-invalid-arguments"></a><span data-ttu-id="23fde-154">エラーが発生した場合は、無効な引数</span><span class="sxs-lookup"><span data-stu-id="23fde-154">If there was an error invalid arguments</span></span>
```
Invalid command line parameters
```

### <a name="if-the-executable-was-not-run-in-administrator-mode"></a><span data-ttu-id="23fde-155">実行可能ファイルが管理者モードで実行されなかった場合</span><span class="sxs-lookup"><span data-stu-id="23fde-155">If the executable was not run in administrator mode</span></span>
```
1. Unable to determine elevation privileges 
2. Please run with administrator privileges 
```

### <a name="if-there-was-an-error-enabling-or-disabling-the-driver"></a><span data-ttu-id="23fde-156">ドライバーの有効化または無効化でエラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="23fde-156">If there was an error enabling or disabling the driver</span></span>
```
1. Could not find the specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
2. Could not find the device instance ID for specified driver with class GUID {d612553d-06b1-49ca-8938-e39ef80eb16f}
3. Could not find the specified driver with device instance ID <INSTANCE ID>
4. Failed to enable/disable driver
```

### <a name="if-there-was-an-error-validating-the-spatial-database-version"></a><span data-ttu-id="23fde-157">空間データベースバージョンの検証中にエラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="23fde-157">If there was an error validating the spatial database version</span></span>
```
1. Could not read database version
2. This tool is not compatible with the current driver version of Windows Mixed Reality and/or the spatial data provided to replace the existing spatial data is an invalid version.
3. No spatial data is present on the current device please connect your Mixed Reality device to initialize spatial data. If the problem persists please restart your PC.
```

### <a name="if-there-was-an-error-validating-the-package-family-name-provided-for-target-importexport-app"></a><span data-ttu-id="23fde-158">ターゲットのインポート/エクスポートアプリに指定されたパッケージファミリ名の検証中にエラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="23fde-158">If there was an error validating the package family name provided for target import/export app</span></span>
```
The package family name does not correspond to an installed app
```

### <a name="if-there-was-an-error-validating-the-user-sid"></a><span data-ttu-id="23fde-159">ユーザー SID の検証中にエラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="23fde-159">If there was an error validating the user SID</span></span>
```
Failed to find local user for passed in user SID
```

### <a name="if-there-was-an-error-related-to-the-destination-or-source-spatial-data-files"></a><span data-ttu-id="23fde-160">コピー先またはコピー元の空間データファイルに関連するエラーが発生した場合</span><span class="sxs-lookup"><span data-stu-id="23fde-160">If there was an error related to the destination or source spatial data files</span></span>
```
1. Folder path to space store files doesn't exist 
2. het.mapx or sa.mapx file doesn't exist in <PATH> for import
3. Unable to create directory at <PATH> for export
```

### <a name="if-there-was-an-error-related-to-starting-and-stopping-spectrumsharedrealitysvc"></a><span data-ttu-id="23fde-161">スペクトラムの開始と停止に関連するエラーが発生した場合は、</span><span class="sxs-lookup"><span data-stu-id="23fde-161">If there was an error related to starting and stopping Spectrum/SharedRealitySvc</span></span>
```
1. Unable to open service manager <SERVICE>
2. Timed out trying to start/stop <SERVICE>
```
