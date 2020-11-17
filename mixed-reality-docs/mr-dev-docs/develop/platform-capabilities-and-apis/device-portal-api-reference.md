---
title: Device Portal API リファレンス
description: HoloLens の Windows デバイスポータルの API リファレンス
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens、Windows デバイスポータル、API、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実のヘッドセット
ms.openlocfilehash: 1085f6c948ab7fe0ff8cb3801ebb0b883570acbc
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677971"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="a854d-104">Device Portal API リファレンス</span><span class="sxs-lookup"><span data-stu-id="a854d-104">Device portal API reference</span></span>

<span data-ttu-id="a854d-105">[Windows デバイスポータル](using-the-windows-device-portal.md)のすべての機能は REST API の上に構築されており、データにアクセスしたり、デバイスをプログラムで制御したりするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="a854d-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="a854d-106">アプリの撮る</span><span class="sxs-lookup"><span data-stu-id="a854d-106">App deloyment</span></span>

<span data-ttu-id="a854d-107">**/api/app/packagemanager/package (削除)**</span><span class="sxs-lookup"><span data-stu-id="a854d-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="a854d-108">アプリをアンインストールします</span><span class="sxs-lookup"><span data-stu-id="a854d-108">Uninstalls an app</span></span>

<span data-ttu-id="a854d-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-109">Parameters</span></span>
* <span data-ttu-id="a854d-110">パッケージ: アンインストールするパッケージのファイル名。</span><span class="sxs-lookup"><span data-stu-id="a854d-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="a854d-111">**/api/app/packagemanager/package (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="a854d-112">アプリをインストールします</span><span class="sxs-lookup"><span data-stu-id="a854d-112">Installs an App</span></span>

<span data-ttu-id="a854d-113">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-113">Parameters</span></span>
* <span data-ttu-id="a854d-114">パッケージ: インストールするパッケージのファイル名。</span><span class="sxs-lookup"><span data-stu-id="a854d-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="a854d-115">ペイロード</span><span class="sxs-lookup"><span data-stu-id="a854d-115">Payload</span></span>
* <span data-ttu-id="a854d-116">マルチパート準拠の http 本文</span><span class="sxs-lookup"><span data-stu-id="a854d-116">multi-part conforming http body</span></span>

<span data-ttu-id="a854d-117">**/api/app/packagemanager/packages (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="a854d-118">システムにインストールされているアプリの一覧を詳細と共に取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="a854d-119">データを返します</span><span class="sxs-lookup"><span data-stu-id="a854d-119">Return data</span></span>
* <span data-ttu-id="a854d-120">インストールされているパッケージの一覧と詳細</span><span class="sxs-lookup"><span data-stu-id="a854d-120">List of installed packages with details</span></span>

<span data-ttu-id="a854d-121">**/api/app/packagemanager/state (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="a854d-122">進行中のアプリのインストールの状態を取得します</span><span class="sxs-lookup"><span data-stu-id="a854d-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="a854d-123">ダンプの収集</span><span class="sxs-lookup"><span data-stu-id="a854d-123">Dump collection</span></span>

<span data-ttu-id="a854d-124">**/api/debug/dump/usermode/crashcontrol (削除)**</span><span class="sxs-lookup"><span data-stu-id="a854d-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="a854d-125">サイドロードアプリのクラッシュダンプの収集を無効にします。</span><span class="sxs-lookup"><span data-stu-id="a854d-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="a854d-126">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-126">Parameters</span></span>
* <span data-ttu-id="a854d-127">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="a854d-127">packageFullname : package name</span></span>

<span data-ttu-id="a854d-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="a854d-129">サイドロード apps のクラッシュダンプの収集の設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="a854d-130">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-130">Parameters</span></span>
* <span data-ttu-id="a854d-131">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="a854d-131">packageFullname : package name</span></span>

<span data-ttu-id="a854d-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="a854d-133">サイドロードアプリのダンプ制御設定を有効にして設定します</span><span class="sxs-lookup"><span data-stu-id="a854d-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="a854d-134">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-134">Parameters</span></span>
* <span data-ttu-id="a854d-135">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="a854d-135">packageFullname : package name</span></span>

<span data-ttu-id="a854d-136">**/api/debug/dump/usermode/crashdump (削除)**</span><span class="sxs-lookup"><span data-stu-id="a854d-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="a854d-137">サイドロードアプリのクラッシュダンプを削除します。</span><span class="sxs-lookup"><span data-stu-id="a854d-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="a854d-138">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-138">Parameters</span></span>
* <span data-ttu-id="a854d-139">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="a854d-139">packageFullname : package name</span></span>
* <span data-ttu-id="a854d-140">fileName: ダンプファイル名</span><span class="sxs-lookup"><span data-stu-id="a854d-140">fileName : dump file name</span></span>

<span data-ttu-id="a854d-141">**/api/debug/dump/usermode/crashdump (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="a854d-142">サイドロードアプリのクラッシュダンプを取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="a854d-143">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-143">Parameters</span></span>
* <span data-ttu-id="a854d-144">packageFullname: パッケージ名</span><span class="sxs-lookup"><span data-stu-id="a854d-144">packageFullname : package name</span></span>
* <span data-ttu-id="a854d-145">fileName: ダンプファイル名</span><span class="sxs-lookup"><span data-stu-id="a854d-145">fileName : dump file name</span></span>

<span data-ttu-id="a854d-146">データを返します</span><span class="sxs-lookup"><span data-stu-id="a854d-146">Return data</span></span>
* <span data-ttu-id="a854d-147">ダンプファイル。</span><span class="sxs-lookup"><span data-stu-id="a854d-147">Dump file.</span></span> <span data-ttu-id="a854d-148">WinDbg または Visual Studio を使用して検査する</span><span class="sxs-lookup"><span data-stu-id="a854d-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="a854d-149">**/api/debug/dump/usermode/dumps (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="a854d-150">サイドロードアプリのすべてのクラッシュダンプの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="a854d-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="a854d-151">データを返します</span><span class="sxs-lookup"><span data-stu-id="a854d-151">Return data</span></span>
* <span data-ttu-id="a854d-152">サイドロードされたアプリごとのクラッシュダンプの一覧</span><span class="sxs-lookup"><span data-stu-id="a854d-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="a854d-153">ETW</span><span class="sxs-lookup"><span data-stu-id="a854d-153">ETW</span></span>

<span data-ttu-id="a854d-154">**/api/etw/providers (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="a854d-155">登録されたプロバイダーを列挙します</span><span class="sxs-lookup"><span data-stu-id="a854d-155">Enumerates registered providers</span></span>

<span data-ttu-id="a854d-156">データを返します</span><span class="sxs-lookup"><span data-stu-id="a854d-156">Return data</span></span>
* <span data-ttu-id="a854d-157">プロバイダー、フレンドリ名、GUID の一覧</span><span class="sxs-lookup"><span data-stu-id="a854d-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="a854d-158">**/api/etw/session/realtime (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="a854d-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="a854d-159">リアルタイム ETW セッションを作成します。websocket 経由で管理されます。</span><span class="sxs-lookup"><span data-stu-id="a854d-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="a854d-160">データを返します</span><span class="sxs-lookup"><span data-stu-id="a854d-160">Return data</span></span>
* <span data-ttu-id="a854d-161">有効なプロバイダーからの ETW イベント</span><span class="sxs-lookup"><span data-stu-id="a854d-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="a854d-162">ホログラフィック OS</span><span class="sxs-lookup"><span data-stu-id="a854d-162">Holographic OS</span></span>

<span data-ttu-id="a854d-163">**/api/holographic/os/etw/customproviders (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="a854d-164">システムに登録されていない HoloLens 固有の ETW プロバイダーの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="a854d-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="a854d-165">**/api/holographic/os/services (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="a854d-166">実行中のすべてのサービスの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="a854d-166">Returns the states of all services running.</span></span>

<span data-ttu-id="a854d-167">**/api/holographic/os/settings/ipd (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="a854d-168">格納されている IPD (Interpupillary distance) をミリメートル単位で取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="a854d-169">**/api/holographic/os/settings/ipd (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="a854d-170">IPD を設定します。</span><span class="sxs-lookup"><span data-stu-id="a854d-170">Sets the IPD</span></span>

<span data-ttu-id="a854d-171">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-171">Parameters</span></span>
* <span data-ttu-id="a854d-172">ipd: mm で設定する新しい IPD 値</span><span class="sxs-lookup"><span data-stu-id="a854d-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="a854d-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="a854d-174">Device Portal の HTTPS 要件を取得する</span><span class="sxs-lookup"><span data-stu-id="a854d-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="a854d-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="a854d-176">デバイスポータルの HTTPS 要件を設定します。</span><span class="sxs-lookup"><span data-stu-id="a854d-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="a854d-177">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-177">Parameters</span></span>
* <span data-ttu-id="a854d-178">必須: はい、いいえ、または既定値</span><span class="sxs-lookup"><span data-stu-id="a854d-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="a854d-179">Holographic の認識</span><span class="sxs-lookup"><span data-stu-id="a854d-179">Holographic Perception</span></span>

<span data-ttu-id="a854d-180">**/api/holographic/perception/client (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="a854d-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="a854d-181">Websocket のアップグレードを受け入れ、30 fps で更新を送信する認識クライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="a854d-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="a854d-182">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-182">Parameters</span></span>
* <span data-ttu-id="a854d-183">clientmode: "active" は、受動的に確立できないときにビジュアル追跡モードを強制します。</span><span class="sxs-lookup"><span data-stu-id="a854d-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="a854d-184">Holographic Thermal</span><span class="sxs-lookup"><span data-stu-id="a854d-184">Holographic Thermal</span></span>

<span data-ttu-id="a854d-185">**/api/holographic/thermal/stage (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="a854d-186">デバイスの温度ステージを取得する (通常は0、1ウォーム、2重大)</span><span class="sxs-lookup"><span data-stu-id="a854d-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="a854d-187">Map Manager</span><span class="sxs-lookup"><span data-stu-id="a854d-187">Map Manager</span></span>

<span data-ttu-id="a854d-188">**/api/holographic/mapmanager/mapFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="a854d-189">使用可能なマップファイル (mapx) の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="a854d-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="a854d-191">使用できるアンカーファイル (.. x) の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="a854d-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="a854d-193">使用可能な空間再構築データベースファイル (srdb) の一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="a854d-194">**/api/holographic/mapmanager/getanchors (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="a854d-195">現在のユーザーに対して保持されているアンカーの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="a854d-196">ファイルのダウンロード/アップロード/削除</span><span class="sxs-lookup"><span data-stu-id="a854d-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="a854d-197">**/api/holographic/mapmanager/download (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="a854d-198">マップ、アンカー、または空間再構築データベースファイルをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="a854d-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="a854d-199">ファイルは、既にアップロードまたはエクスポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a854d-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="a854d-200">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-200">Parameters</span></span>
* <span data-ttu-id="a854d-201">FileName: ダウンロードするファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="a854d-202">例:</span><span class="sxs-lookup"><span data-stu-id="a854d-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="a854d-203">**/api/holographic/mapmanager/upload (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="a854d-204">マップ、アンカー、または空間再構築データベースファイルをアップロードします。</span><span class="sxs-lookup"><span data-stu-id="a854d-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="a854d-205">ファイルがアップロードされると、後でシステムによって使用されるようにインポートできます。</span><span class="sxs-lookup"><span data-stu-id="a854d-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="a854d-206">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-206">Parameters</span></span>
* <span data-ttu-id="a854d-207">file: アップロードするファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="a854d-208">例:</span><span class="sxs-lookup"><span data-stu-id="a854d-208">Example:</span></span>
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

<span data-ttu-id="a854d-209">**/api/holographic/mapmanager/delete (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="a854d-210">マップ、アンカー、または空間再構築データベースファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="a854d-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="a854d-211">ファイルは、既にアップロードまたはエクスポートされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a854d-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="a854d-212">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-212">Parameters</span></span>
* <span data-ttu-id="a854d-213">FileName: 削除するファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="a854d-214">例:</span><span class="sxs-lookup"><span data-stu-id="a854d-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="a854d-215">エクスポート</span><span class="sxs-lookup"><span data-stu-id="a854d-215">Export</span></span>

<span data-ttu-id="a854d-216">**/api/holographic/mapmanager/export (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="a854d-217">システムによって現在使用されているマップをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="a854d-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="a854d-218">エクスポートが完了すると、ダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="a854d-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="a854d-219">例:</span><span class="sxs-lookup"><span data-stu-id="a854d-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="a854d-220">**/api/holographic/mapmanager/exportanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="a854d-221">システムによって現在使用されているマップをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="a854d-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="a854d-222">エクスポートが完了すると、ダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="a854d-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="a854d-223">例:</span><span class="sxs-lookup"><span data-stu-id="a854d-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="a854d-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="a854d-225">システムによって現在使用されているマップおよびアンカーをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="a854d-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="a854d-226">をエクスポートすると、ダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="a854d-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="a854d-227">例:</span><span class="sxs-lookup"><span data-stu-id="a854d-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="a854d-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="a854d-229">システムによって現在使用されているマップおよび空間再構築データベースをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="a854d-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="a854d-230">エクスポートされると、ダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="a854d-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="a854d-231">例:</span><span class="sxs-lookup"><span data-stu-id="a854d-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="a854d-232">[インポート]</span><span class="sxs-lookup"><span data-stu-id="a854d-232">Import</span></span>

<span data-ttu-id="a854d-233">**/api/holographic/mapmanager/import (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="a854d-234">現在使用されているマップをシステムに示します。</span><span class="sxs-lookup"><span data-stu-id="a854d-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="a854d-235">は、エクスポートまたはアップロードされたファイルに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a854d-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="a854d-236">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-236">Parameters</span></span>
* <span data-ttu-id="a854d-237">FileName: 使用するマップの名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="a854d-238">例:</span><span class="sxs-lookup"><span data-stu-id="a854d-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="a854d-239">**/api/holographic/mapmanager/importanchors (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="a854d-240">現在使用されているアンカーをシステムに示します。</span><span class="sxs-lookup"><span data-stu-id="a854d-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="a854d-241">は、エクスポートまたはアップロードされたファイルに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a854d-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="a854d-242">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-242">Parameters</span></span>
* <span data-ttu-id="a854d-243">FileName: 使用するアンカーの名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="a854d-244">例:</span><span class="sxs-lookup"><span data-stu-id="a854d-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="a854d-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="a854d-246">現在使用されている空間再構築データベースをシステムに指示します。</span><span class="sxs-lookup"><span data-stu-id="a854d-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="a854d-247">は、エクスポートまたはアップロードされたファイルに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a854d-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="a854d-248">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-248">Parameters</span></span>
* <span data-ttu-id="a854d-249">FileName: 使用する空間マッピング db の名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="a854d-250">例:</span><span class="sxs-lookup"><span data-stu-id="a854d-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="a854d-251">その他</span><span class="sxs-lookup"><span data-stu-id="a854d-251">Other</span></span>

<span data-ttu-id="a854d-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="a854d-253">マップ、アンカー、および空間再構築データベースをシステムにリセットします。</span><span class="sxs-lookup"><span data-stu-id="a854d-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="a854d-254">例:</span><span class="sxs-lookup"><span data-stu-id="a854d-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="a854d-255">**/api/holographic/mapmanager/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="a854d-256">最後にインポートされたマップ、アンカー、および空間再構築データベースファイルを含む、システムの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="a854d-257">Mixed Reality キャプチャ</span><span class="sxs-lookup"><span data-stu-id="a854d-257">Mixed Reality Capture</span></span>

<span data-ttu-id="a854d-258">**/api/holographic/mrc/file (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="a854d-259">混合の現実ファイルをデバイスからダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="a854d-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="a854d-260">ストリーミングには op = stream クエリパラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="a854d-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="a854d-261">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-261">Parameters</span></span>
* <span data-ttu-id="a854d-262">filename: 取得するビデオファイルの名前、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="a854d-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="a854d-263">op: ストリーム</span><span class="sxs-lookup"><span data-stu-id="a854d-263">op : stream</span></span>

<span data-ttu-id="a854d-264">**/api/holographic/mrc/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="a854d-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="a854d-265">デバイスから mixed reality の記録を削除します。</span><span class="sxs-lookup"><span data-stu-id="a854d-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="a854d-266">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-266">Parameters</span></span>
* <span data-ttu-id="a854d-267">filename: 削除するファイルの名前、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="a854d-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="a854d-268">**/api/holographic/mrc/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="a854d-269">デバイスに格納されている mixed reality ファイルの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="a854d-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="a854d-270">**/api/holographic/mrc/photo (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="a854d-271">Mixed reality の写真を取得し、デバイスにファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="a854d-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="a854d-272">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-272">Parameters</span></span>
* <span data-ttu-id="a854d-273">holo: キャプチャホログラム: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="a854d-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="a854d-274">pv: キャプチャの PV カメラ: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="a854d-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="a854d-275">RenderFromCamera: (HoloLens 2 のみ) 写真/ビデオカメラから見たレンダリング: true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="a854d-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="a854d-276">**/api/holographic/mrc/settings (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="a854d-277">既定の mixed reality キャプチャ設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="a854d-278">**/api/holographic/mrc/settings (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="a854d-279">既定の mixed reality キャプチャ設定を設定します。</span><span class="sxs-lookup"><span data-stu-id="a854d-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="a854d-280">これらの設定の一部は、システムの MRC の写真とビデオキャプチャに適用されます。</span><span class="sxs-lookup"><span data-stu-id="a854d-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="a854d-281">**/api/holographic/mrc/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="a854d-282">Windows デバイスポータル内の mixed reality キャプチャの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="a854d-283">\**_応答_* _</span><span class="sxs-lookup"><span data-stu-id="a854d-283">\**_Response_* _</span></span>

<span data-ttu-id="a854d-284">応答には、Windows デバイスポータルがビデオを記録しているかどうかを示す JSON プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a854d-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="a854d-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span><span class="sxs-lookup"><span data-stu-id="a854d-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span></span>

<span data-ttu-id="a854d-286">指定したファイルのサムネイルイメージを取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="a854d-287">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-287">Parameters</span></span>
* <span data-ttu-id="a854d-288">filename: サムネイルが要求されているファイルの名前 (hex64 encoded)</span><span class="sxs-lookup"><span data-stu-id="a854d-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="a854d-289">**/api/holographic/mrc/video/control/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="a854d-290">Mixed reality の記録を開始します</span><span class="sxs-lookup"><span data-stu-id="a854d-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="a854d-291">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-291">Parameters</span></span>
* <span data-ttu-id="a854d-292">holo: キャプチャホログラム: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="a854d-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="a854d-293">pv: キャプチャの PV カメラ: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="a854d-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="a854d-294">mic: キャプチャマイク: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="a854d-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="a854d-295">ループバック: キャプチャアプリオーディオ: true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="a854d-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="a854d-296">RenderFromCamera: (HoloLens 2 のみ) 写真/ビデオカメラから見たレンダリング: true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="a854d-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="a854d-297">vstab: (HoloLens 2 のみ) ビデオ安定化を有効にします。 true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="a854d-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="a854d-298">vstabbuffer: (HoloLens 2 のみ) ビデオ安定化バッファー待機時間: 0 ~ 30 フレーム (既定値は15フレーム)</span><span class="sxs-lookup"><span data-stu-id="a854d-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="a854d-299">**/api/holographic/mrc/video/control/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="a854d-300">現在の mixed reality 記録を停止します</span><span class="sxs-lookup"><span data-stu-id="a854d-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="a854d-301">Mixed Reality ストリーミング</span><span class="sxs-lookup"><span data-stu-id="a854d-301">Mixed Reality Streaming</span></span>

<span data-ttu-id="a854d-302">HoloLens は、フラグメント化された mp4 のチャンクダウンロードを使用して、混合現実のライブプレビューをサポートします。</span><span class="sxs-lookup"><span data-stu-id="a854d-302">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="a854d-303">混合現実のストリームは、キャプチャ対象を制御するために、同じパラメーターのセットを共有します。</span><span class="sxs-lookup"><span data-stu-id="a854d-303">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="a854d-304">holo: キャプチャホログラム: true または false</span><span class="sxs-lookup"><span data-stu-id="a854d-304">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="a854d-305">pv: キャプチャの PV カメラ: true または false</span><span class="sxs-lookup"><span data-stu-id="a854d-305">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="a854d-306">mic: マイクのキャプチャ: true または false</span><span class="sxs-lookup"><span data-stu-id="a854d-306">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="a854d-307">ループバック: アプリオーディオのキャプチャ: true または false</span><span class="sxs-lookup"><span data-stu-id="a854d-307">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="a854d-308">これらのいずれも指定されていない場合、ホログラム、photo/video カメラ、アプリオーディオがキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="a854d-308">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="a854d-309">指定されている場合: 未指定のパラメーターは既定で false に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a854d-309">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="a854d-310">省略可能なパラメーター (HoloLens 2 のみ)</span><span class="sxs-lookup"><span data-stu-id="a854d-310">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="a854d-311">RenderFromCamera: 写真/ビデオカメラから見たレンダリング: true または false (既定値は true)</span><span class="sxs-lookup"><span data-stu-id="a854d-311">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="a854d-312">vstab: ビデオ安定化を有効にします。 true または false (既定値は false)</span><span class="sxs-lookup"><span data-stu-id="a854d-312">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="a854d-313">vstabbuffer: ビデオ安定化バッファー待機時間: 0 ~ 30 フレーム (既定では15フレーム)</span><span class="sxs-lookup"><span data-stu-id="a854d-313">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="a854d-314">**/api/holographic/stream/live.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-314">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="a854d-315">1280x720p 30 fps 5 Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="a854d-315">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="a854d-316">**/api/holographic/stream/live_high.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-316">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="a854d-317">1280x720p 30 fps 5 Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="a854d-317">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="a854d-318">**/api/holographic/stream/live_med.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-318">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="a854d-319">854x480p 30 fps 2.5 Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="a854d-319">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="a854d-320">**/api/holographic/stream/live_low.mp4 (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-320">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="a854d-321">428x240p 15fps 0.6 Mbit ストリーム。</span><span class="sxs-lookup"><span data-stu-id="a854d-321">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="a854d-322">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="a854d-322">Networking</span></span>

<span data-ttu-id="a854d-323">**/api/networking/ipconfig (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-323">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="a854d-324">現在の ip 構成を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-324">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="a854d-325">OS 情報</span><span class="sxs-lookup"><span data-stu-id="a854d-325">OS Information</span></span>

<span data-ttu-id="a854d-326">**/api/info (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-326">**/api/os/info (GET)**</span></span>

<span data-ttu-id="a854d-327">オペレーティングシステム情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-327">Gets operating system information</span></span>

<span data-ttu-id="a854d-328">**/api/machinename (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-328">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="a854d-329">コンピューター名を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-329">Gets the machine name</span></span>

<span data-ttu-id="a854d-330">**/api/machinename (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-330">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="a854d-331">コンピューター名を設定します</span><span class="sxs-lookup"><span data-stu-id="a854d-331">Sets the machine name</span></span>

<span data-ttu-id="a854d-332">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-332">Parameters</span></span>
* <span data-ttu-id="a854d-333">[名前]: 新しいコンピューター名、hex64 encoded、をに設定します。</span><span class="sxs-lookup"><span data-stu-id="a854d-333">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="a854d-334">認識シミュレーションの制御</span><span class="sxs-lookup"><span data-stu-id="a854d-334">Perception Simulation Control</span></span>

<span data-ttu-id="a854d-335">**/api/holographic/simulation/control/mode (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-335">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="a854d-336">シミュレーションモードを取得する</span><span class="sxs-lookup"><span data-stu-id="a854d-336">Get the simulation mode</span></span>

<span data-ttu-id="a854d-337">**/api/holographic/simulation/control/mode (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-337">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="a854d-338">シミュレーションモードの設定</span><span class="sxs-lookup"><span data-stu-id="a854d-338">Set the simulation mode</span></span>

<span data-ttu-id="a854d-339">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-339">Parameters</span></span>
* <span data-ttu-id="a854d-340">モード: シミュレーションモード: 既定、シミュレーション、リモート、レガシ</span><span class="sxs-lookup"><span data-stu-id="a854d-340">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="a854d-341">**/api/holographic/simulation/control/stream (削除)**</span><span class="sxs-lookup"><span data-stu-id="a854d-341">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="a854d-342">コントロールストリームを削除します。</span><span class="sxs-lookup"><span data-stu-id="a854d-342">Delete a control stream.</span></span>

<span data-ttu-id="a854d-343">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="a854d-343">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="a854d-344">コントロールストリームの web ソケット接続を開きます。</span><span class="sxs-lookup"><span data-stu-id="a854d-344">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="a854d-345">**/api/holographic/simulation/control/stream (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-345">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="a854d-346">コントロールストリームを作成するか (優先順位が必要)、作成されたストリームにデータを post します (streamId が必要)。</span><span class="sxs-lookup"><span data-stu-id="a854d-346">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="a854d-347">ポストされたデータは ' application/オクテット-stream ' 型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a854d-347">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="a854d-348">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="a854d-348">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="a854d-349">"シミュレーション" モードで、システムに表示されるコンテンツを含むシミュレーションビデオストリームを要求します。</span><span class="sxs-lookup"><span data-stu-id="a854d-349">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="a854d-350">単純なフォーマット記述子ヘッダーが最初に送信され、その後に h.264 でエンコードされたテクスチャが続きます。それぞれのヘッダーには、目のインデックスとテクスチャサイズが示されます。</span><span class="sxs-lookup"><span data-stu-id="a854d-350">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="a854d-351">認識シミュレーションの再生</span><span class="sxs-lookup"><span data-stu-id="a854d-351">Perception Simulation Playback</span></span>

<span data-ttu-id="a854d-352">**/api/holographic/simulation/playback/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="a854d-352">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="a854d-353">記録を削除します。</span><span class="sxs-lookup"><span data-stu-id="a854d-353">Delete a recording.</span></span>

<span data-ttu-id="a854d-354">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-354">Parameters</span></span>
* <span data-ttu-id="a854d-355">記録: 削除する記録の名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-355">recording : Name of recording to delete.</span></span>

<span data-ttu-id="a854d-356">**/api/holographic/simulation/playback/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-356">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="a854d-357">記録をアップロードします。</span><span class="sxs-lookup"><span data-stu-id="a854d-357">Upload a recording.</span></span>

<span data-ttu-id="a854d-358">**/api/holographic/simulation/playback/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-358">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="a854d-359">すべての記録を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-359">Get all recordings.</span></span>

<span data-ttu-id="a854d-360">**/api/holographic/simulation/playback/session (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-360">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="a854d-361">記録の現在の再生状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-361">Get the current playback state of a recording.</span></span>

<span data-ttu-id="a854d-362">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-362">Parameters</span></span>
* <span data-ttu-id="a854d-363">記録: 記録の名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-363">recording : Name of recording.</span></span>

<span data-ttu-id="a854d-364">**/api/holographic/simulation/playback/session/file (削除)**</span><span class="sxs-lookup"><span data-stu-id="a854d-364">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="a854d-365">記録をアンロードします。</span><span class="sxs-lookup"><span data-stu-id="a854d-365">Unload a recording.</span></span>

<span data-ttu-id="a854d-366">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-366">Parameters</span></span>
* <span data-ttu-id="a854d-367">記録: アンロードする記録の名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-367">recording : Name of recording to unload.</span></span>

<span data-ttu-id="a854d-368">**/api/holographic/simulation/playback/session/file (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-368">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="a854d-369">記録を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a854d-369">Load a recording.</span></span>

<span data-ttu-id="a854d-370">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-370">Parameters</span></span>
* <span data-ttu-id="a854d-371">記録: 読み込む記録の名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-371">recording : Name of recording to load.</span></span>

<span data-ttu-id="a854d-372">**/api/holographic/simulation/playback/session/files (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-372">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="a854d-373">読み込まれたすべての録音を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-373">Get all loaded recordings.</span></span>

<span data-ttu-id="a854d-374">**/api/holographic/simulation/playback/session/pause (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-374">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="a854d-375">記録を一時停止します。</span><span class="sxs-lookup"><span data-stu-id="a854d-375">Pause a recording.</span></span>

<span data-ttu-id="a854d-376">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-376">Parameters</span></span>
* <span data-ttu-id="a854d-377">記録: 記録の名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-377">recording : Name of recording.</span></span>

<span data-ttu-id="a854d-378">**/api/holographic/simulation/playback/session/play (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-378">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="a854d-379">録音を再生します。</span><span class="sxs-lookup"><span data-stu-id="a854d-379">Play a recording.</span></span>

<span data-ttu-id="a854d-380">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-380">Parameters</span></span>
* <span data-ttu-id="a854d-381">記録: 記録の名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-381">recording : Name of recording.</span></span>

<span data-ttu-id="a854d-382">**/api/holographic/simulation/playback/session/stop (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-382">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="a854d-383">記録を停止します。</span><span class="sxs-lookup"><span data-stu-id="a854d-383">Stop a recording.</span></span>

<span data-ttu-id="a854d-384">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-384">Parameters</span></span>
* <span data-ttu-id="a854d-385">記録: 記録の名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-385">recording : Name of recording.</span></span>

<span data-ttu-id="a854d-386">**/api/holographic/simulation/playback/session/types (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-386">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="a854d-387">読み込まれた記録のデータの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-387">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="a854d-388">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-388">Parameters</span></span>
* <span data-ttu-id="a854d-389">記録: 記録の名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-389">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="a854d-390">認識のシミュレーション記録</span><span class="sxs-lookup"><span data-stu-id="a854d-390">Perception Simulation Recording</span></span>

<span data-ttu-id="a854d-391">**/api/holographic/simulation/recording/start (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-391">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="a854d-392">記録を開始します。</span><span class="sxs-lookup"><span data-stu-id="a854d-392">Start a recording.</span></span> <span data-ttu-id="a854d-393">一度にアクティブにできる記録は1つだけです。</span><span class="sxs-lookup"><span data-stu-id="a854d-393">Only a single recording can be active at once.</span></span> <span data-ttu-id="a854d-394">ヘッド、ハンド、spatialMapping、または環境のいずれかを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a854d-394">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="a854d-395">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-395">Parameters</span></span>
* <span data-ttu-id="a854d-396">head: 1 に設定すると、ヘッドデータが記録されます。</span><span class="sxs-lookup"><span data-stu-id="a854d-396">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="a854d-397">手: 1 に設定すると、手のデータが記録されます。</span><span class="sxs-lookup"><span data-stu-id="a854d-397">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="a854d-398">spatialMapping: 空間マッピングを記録するには、1に設定します。</span><span class="sxs-lookup"><span data-stu-id="a854d-398">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="a854d-399">環境: 1 に設定すると、環境データが記録されます。</span><span class="sxs-lookup"><span data-stu-id="a854d-399">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="a854d-400">名前: 記録の名前。</span><span class="sxs-lookup"><span data-stu-id="a854d-400">name : Name of the recording.</span></span>
* <span data-ttu-id="a854d-401">singleSpatialMappingFrame: 1 に設定すると、空間マッピングフレームが1つだけ記録されます。</span><span class="sxs-lookup"><span data-stu-id="a854d-401">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="a854d-402">**/api/holographic/simulation/recording/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-402">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="a854d-403">記録の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-403">Get recording state.</span></span>

<span data-ttu-id="a854d-404">**/api/holographic/simulation/recording/stop (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-404">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="a854d-405">現在の記録を停止します。</span><span class="sxs-lookup"><span data-stu-id="a854d-405">Stop the current recording.</span></span> <span data-ttu-id="a854d-406">記録はファイルとして返されます。</span><span class="sxs-lookup"><span data-stu-id="a854d-406">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="a854d-407">パフォーマンス データ</span><span class="sxs-lookup"><span data-stu-id="a854d-407">Performance data</span></span>

<span data-ttu-id="a854d-408">**/api/resourcemanager/processes (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-408">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="a854d-409">詳細を含む実行中のプロセスの一覧を返します</span><span class="sxs-lookup"><span data-stu-id="a854d-409">Returns the list of running processes with details</span></span>

<span data-ttu-id="a854d-410">データを返します</span><span class="sxs-lookup"><span data-stu-id="a854d-410">Return data</span></span>
* <span data-ttu-id="a854d-411">各プロセスのプロセスと詳細の一覧を含む JSON</span><span class="sxs-lookup"><span data-stu-id="a854d-411">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="a854d-412">**/api/resourcemanager/systemperf (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-412">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="a854d-413">システムパフォーマンス統計情報 (i/o 読み取り/書き込み、メモリ統計など) を返します。</span><span class="sxs-lookup"><span data-stu-id="a854d-413">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="a854d-414">データを返します</span><span class="sxs-lookup"><span data-stu-id="a854d-414">Return data</span></span>
* <span data-ttu-id="a854d-415">システム情報を含む JSON: CPU、GPU、メモリ、ネットワーク、IO</span><span class="sxs-lookup"><span data-stu-id="a854d-415">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="a854d-416">Power</span><span class="sxs-lookup"><span data-stu-id="a854d-416">Power</span></span>

<span data-ttu-id="a854d-417">**/api/バッテリ (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-417">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="a854d-418">現在のバッテリの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-418">Gets the current battery state</span></span>

<span data-ttu-id="a854d-419">**//(GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-419">**/api/power/state (GET)**</span></span>

<span data-ttu-id="a854d-420">システムが低電力状態であるかどうかを確認します</span><span class="sxs-lookup"><span data-stu-id="a854d-420">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="a854d-421">リモート コントロール</span><span class="sxs-lookup"><span data-stu-id="a854d-421">Remote Control</span></span>

<span data-ttu-id="a854d-422">**/api/control/restart (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-422">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="a854d-423">ターゲットデバイスを再起動します</span><span class="sxs-lookup"><span data-stu-id="a854d-423">Restarts the target device</span></span>

<span data-ttu-id="a854d-424">**/api/control/shutdown (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-424">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="a854d-425">ターゲットデバイスをシャットダウンします</span><span class="sxs-lookup"><span data-stu-id="a854d-425">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="a854d-426">タスク マネージャー</span><span class="sxs-lookup"><span data-stu-id="a854d-426">Task Manager</span></span>

<span data-ttu-id="a854d-427">**/api/taskmanager/app (削除)**</span><span class="sxs-lookup"><span data-stu-id="a854d-427">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="a854d-428">モダンアプリを停止します</span><span class="sxs-lookup"><span data-stu-id="a854d-428">Stops a modern app</span></span>

<span data-ttu-id="a854d-429">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-429">Parameters</span></span>
* <span data-ttu-id="a854d-430">パッケージ: アプリパッケージの完全名、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="a854d-430">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="a854d-431">forcestop: すべてのプロセスを強制的に停止します (= yes)</span><span class="sxs-lookup"><span data-stu-id="a854d-431">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="a854d-432">**/api/taskmanager/app (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-432">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="a854d-433">モダンアプリを開始します</span><span class="sxs-lookup"><span data-stu-id="a854d-433">Starts a modern app</span></span>

<span data-ttu-id="a854d-434">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-434">Parameters</span></span>
* <span data-ttu-id="a854d-435">appid: アプリの開始、hex64 エンコード</span><span class="sxs-lookup"><span data-stu-id="a854d-435">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="a854d-436">パッケージ: アプリパッケージの完全名、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="a854d-436">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="a854d-437">WiFi の管理</span><span class="sxs-lookup"><span data-stu-id="a854d-437">WiFi Management</span></span>

<span data-ttu-id="a854d-438">**/api/wifi/interfaces (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-438">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="a854d-439">ワイヤレスネットワークインターフェイスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="a854d-439">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="a854d-440">データを返します</span><span class="sxs-lookup"><span data-stu-id="a854d-440">Return data</span></span>
* <span data-ttu-id="a854d-441">詳細 (GUID、説明など) があるワイヤレスインターフェイスの一覧</span><span class="sxs-lookup"><span data-stu-id="a854d-441">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="a854d-442">**/api/wifi/network (削除)**</span><span class="sxs-lookup"><span data-stu-id="a854d-442">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="a854d-443">指定したインターフェイスのネットワークに関連付けられているプロファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="a854d-443">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="a854d-444">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-444">Parameters</span></span>
* <span data-ttu-id="a854d-445">インターフェイス: ネットワークインターフェイス guid</span><span class="sxs-lookup"><span data-stu-id="a854d-445">interface : network interface guid</span></span>
* <span data-ttu-id="a854d-446">プロファイル: プロファイル名</span><span class="sxs-lookup"><span data-stu-id="a854d-446">profile : profile name</span></span>

<span data-ttu-id="a854d-447">**/api/wifi/networks (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-447">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="a854d-448">指定されたネットワークインターフェイスのワイヤレスネットワークを列挙します</span><span class="sxs-lookup"><span data-stu-id="a854d-448">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="a854d-449">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-449">Parameters</span></span>
* <span data-ttu-id="a854d-450">インターフェイス: ネットワークインターフェイス guid</span><span class="sxs-lookup"><span data-stu-id="a854d-450">interface : network interface guid</span></span>

<span data-ttu-id="a854d-451">データを返します</span><span class="sxs-lookup"><span data-stu-id="a854d-451">Return data</span></span>
* <span data-ttu-id="a854d-452">ネットワークインターフェイスで検出されたワイヤレスネットワークの一覧と詳細</span><span class="sxs-lookup"><span data-stu-id="a854d-452">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="a854d-453">**/api/wifi/network (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-453">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="a854d-454">指定されたインターフェイスでネットワークに接続または切断します。</span><span class="sxs-lookup"><span data-stu-id="a854d-454">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="a854d-455">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-455">Parameters</span></span>
* <span data-ttu-id="a854d-456">インターフェイス: ネットワークインターフェイス guid</span><span class="sxs-lookup"><span data-stu-id="a854d-456">interface : network interface guid</span></span>
* <span data-ttu-id="a854d-457">ssid: 接続先の ssid、hex64 encoded、</span><span class="sxs-lookup"><span data-stu-id="a854d-457">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="a854d-458">op: 接続または切断</span><span class="sxs-lookup"><span data-stu-id="a854d-458">op : connect or disconnect</span></span>
* <span data-ttu-id="a854d-459">createprofile: はいまたはいいえ</span><span class="sxs-lookup"><span data-stu-id="a854d-459">createprofile : yes or no</span></span>
* <span data-ttu-id="a854d-460">キー: shared key、hex64 encoded</span><span class="sxs-lookup"><span data-stu-id="a854d-460">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="a854d-461">Windows パフォーマンス レコーダー</span><span class="sxs-lookup"><span data-stu-id="a854d-461">Windows Performance Recorder</span></span>

<span data-ttu-id="a854d-462">**/api/wpr/customtrace (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-462">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="a854d-463">WPR プロファイルをアップロードし、アップロードされたプロファイルを使用してトレースを開始します。</span><span class="sxs-lookup"><span data-stu-id="a854d-463">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="a854d-464">ペイロード</span><span class="sxs-lookup"><span data-stu-id="a854d-464">Payload</span></span>
* <span data-ttu-id="a854d-465">マルチパート準拠の http 本文</span><span class="sxs-lookup"><span data-stu-id="a854d-465">multi-part conforming http body</span></span>

<span data-ttu-id="a854d-466">データを返します</span><span class="sxs-lookup"><span data-stu-id="a854d-466">Return data</span></span>
* <span data-ttu-id="a854d-467">WPR セッションの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="a854d-467">Returns the WPR session status.</span></span>

<span data-ttu-id="a854d-468">**/api/wpr/status (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-468">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="a854d-469">WPR セッションの状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="a854d-469">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="a854d-470">データを返します</span><span class="sxs-lookup"><span data-stu-id="a854d-470">Return data</span></span>
* <span data-ttu-id="a854d-471">WPR セッションの状態。</span><span class="sxs-lookup"><span data-stu-id="a854d-471">WPR session status.</span></span>

<span data-ttu-id="a854d-472">**/api/wpr/trace (GET)**</span><span class="sxs-lookup"><span data-stu-id="a854d-472">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="a854d-473">WPR (パフォーマンス) トレースセッションを停止します</span><span class="sxs-lookup"><span data-stu-id="a854d-473">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="a854d-474">データを返します</span><span class="sxs-lookup"><span data-stu-id="a854d-474">Return data</span></span>
* <span data-ttu-id="a854d-475">トレース ETL ファイルを返します。</span><span class="sxs-lookup"><span data-stu-id="a854d-475">Returns the trace ETL file</span></span>

<span data-ttu-id="a854d-476">**/api/wpr/trace (POST)**</span><span class="sxs-lookup"><span data-stu-id="a854d-476">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="a854d-477">WPR (パフォーマンス) トレースセッションを開始します</span><span class="sxs-lookup"><span data-stu-id="a854d-477">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="a854d-478">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a854d-478">Parameters</span></span>
* <span data-ttu-id="a854d-479">プロファイル: プロファイル名。</span><span class="sxs-lookup"><span data-stu-id="a854d-479">profile : Profile name.</span></span> <span data-ttu-id="a854d-480">使用可能なプロファイルは、の perfprofiles/profiles.jsに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a854d-480">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="a854d-481">データを返します</span><span class="sxs-lookup"><span data-stu-id="a854d-481">Return data</span></span>
* <span data-ttu-id="a854d-482">開始時に、WPR セッションの状態を返します。</span><span class="sxs-lookup"><span data-stu-id="a854d-482">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="a854d-483">関連項目</span><span class="sxs-lookup"><span data-stu-id="a854d-483">See also</span></span>
* [<span data-ttu-id="a854d-484">Windows Device Portal を使用する</span><span class="sxs-lookup"><span data-stu-id="a854d-484">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="a854d-485">デバイスポータルコア API リファレンス (UWP)</span><span class="sxs-lookup"><span data-stu-id="a854d-485">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
