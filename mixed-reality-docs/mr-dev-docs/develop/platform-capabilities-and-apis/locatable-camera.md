---
title: 場所を特定できるカメラ
description: HoloLens のフロント接続カメラに関する一般的な情報、そのしくみ、および開発者が使用できるプロファイルと解決方法について説明します。
author: cdedmonds
ms.author: wguyman
ms.date: 06/12/2019
ms.topic: article
keywords: カメラ、hololens、カラーカメラ、フロント接続、hololens 2、cv、コンピュータービジョン、基準、マーカー、qr コード、qr、写真、ビデオ
ms.openlocfilehash: bc478aa658b26eb3a4efb16c62d0874b12992e78
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583628"
---
# <a name="locatable-camera"></a><span data-ttu-id="5bf70-104">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="5bf70-104">Locatable camera</span></span>

<span data-ttu-id="5bf70-105">HoloLens には、デバイスの前面に取り付けられている世界中のカメラが搭載されています。これにより、アプリはユーザーに表示される内容を確認できます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-105">HoloLens includes a world-facing camera mounted on the front of the device, which enables apps to see what the user sees.</span></span> <span data-ttu-id="5bf70-106">スマートフォン、ノートブック、またはデスクトップのカラーカメラの場合と同じように、開発者はカメラのアクセスと制御を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-106">Developers have access to and control of the camera, just as they would for color cameras on smartphones, portables, or desktops.</span></span> <span data-ttu-id="5bf70-107">モバイルおよびデスクトップで動作する同じユニバーサル windows [media capture](/uwp/api/Windows.Media.Capture.MediaCapture) および windows Media foundation Api が HoloLens で動作します。</span><span class="sxs-lookup"><span data-stu-id="5bf70-107">The same universal windows [media capture](/uwp/api/Windows.Media.Capture.MediaCapture) and windows media foundation APIs that work on mobile and desktop work on HoloLens.</span></span> <span data-ttu-id="5bf70-108">Unity は、HoloLens でカメラの使用機能を抽象化するために、 [これらの Windows api をラップ](../unity/locatable-camera-in-unity.md) しています。</span><span class="sxs-lookup"><span data-stu-id="5bf70-108">Unity [has wrapped these windows APIs](../unity/locatable-camera-in-unity.md) to abstract camera usage features on HoloLens.</span></span> <span data-ttu-id="5bf70-109">機能のタスクには、通常の写真やビデオを (ホログラムの有無にかかわらず) 撮影したり、カメラの位置をシーン上で検索したりする作業が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-109">Feature tasks include taking regular photos and videos (with or without holograms) and locating the camera's position in and perspective on the scene.</span></span>

## <a name="device-camera-information"></a><span data-ttu-id="5bf70-110">デバイスカメラ情報</span><span class="sxs-lookup"><span data-stu-id="5bf70-110">Device camera information</span></span>

### <a name="hololens-first-generation"></a><span data-ttu-id="5bf70-111">HoloLens (最初世代)</span><span class="sxs-lookup"><span data-stu-id="5bf70-111">HoloLens (first-generation)</span></span>

* <span data-ttu-id="5bf70-112">自動白バランス、自動露出、および完全なイメージ処理パイプラインを使用して、フォーカスされたフォト/ビデオ (PV) カメラを修正します。</span><span class="sxs-lookup"><span data-stu-id="5bf70-112">Fixed focus photo/video (PV) camera with auto white balance, auto exposure, and full image-processing pipeline.</span></span>
* <span data-ttu-id="5bf70-113">世界中のホワイトプライバシー LED は、カメラがアクティブになるたびに点灯します</span><span class="sxs-lookup"><span data-stu-id="5bf70-113">White Privacy LED facing the world will illuminate whenever the camera is active</span></span>
* <span data-ttu-id="5bf70-114">カメラは、30、24、20、15、および 5 fps で、次のモード (すべてのモードが16:9 の縦横比) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="5bf70-114">The camera supports the following modes (all modes are 16:9 aspect ratio) at 30, 24, 20, 15, and 5 fps:</span></span>

  |  <span data-ttu-id="5bf70-115">ビデオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-115">Video</span></span>  |  <span data-ttu-id="5bf70-116">プレビュー</span><span class="sxs-lookup"><span data-stu-id="5bf70-116">Preview</span></span>  |  <span data-ttu-id="5bf70-117">それでもなお</span><span class="sxs-lookup"><span data-stu-id="5bf70-117">Still</span></span>  |  <span data-ttu-id="5bf70-118">ビューの水平方向のフィールド (H 視界)</span><span class="sxs-lookup"><span data-stu-id="5bf70-118">Horizontal Field of View (H-FOV)</span></span> |  <span data-ttu-id="5bf70-119">推奨される使用方法</span><span class="sxs-lookup"><span data-stu-id="5bf70-119">Suggested usage</span></span> | 
  |----------|----------|----------|----------|----------|
  |  <span data-ttu-id="5bf70-120">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="5bf70-120">1280x720</span></span> |  <span data-ttu-id="5bf70-121">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="5bf70-121">1280x720</span></span> |  <span data-ttu-id="5bf70-122">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="5bf70-122">1280x720</span></span> |  <span data-ttu-id="5bf70-123">45度</span><span class="sxs-lookup"><span data-stu-id="5bf70-123">45 deg</span></span>  |  <span data-ttu-id="5bf70-124">(ビデオ安定化を使用した既定のモード)</span><span class="sxs-lookup"><span data-stu-id="5bf70-124">(default mode with video stabilization)</span></span> | 
  |  <span data-ttu-id="5bf70-125">N/A</span><span class="sxs-lookup"><span data-stu-id="5bf70-125">N/A</span></span> |  <span data-ttu-id="5bf70-126">N/A</span><span class="sxs-lookup"><span data-stu-id="5bf70-126">N/A</span></span> |  <span data-ttu-id="5bf70-127">2048x1152</span><span class="sxs-lookup"><span data-stu-id="5bf70-127">2048x1152</span></span> |  <span data-ttu-id="5bf70-128">67度</span><span class="sxs-lookup"><span data-stu-id="5bf70-128">67 deg</span></span> |  <span data-ttu-id="5bf70-129">高解像度の静止画像</span><span class="sxs-lookup"><span data-stu-id="5bf70-129">Highest resolution still image</span></span> | 
  |  <span data-ttu-id="5bf70-130">1408x792</span><span class="sxs-lookup"><span data-stu-id="5bf70-130">1408x792</span></span> |  <span data-ttu-id="5bf70-131">1408x792</span><span class="sxs-lookup"><span data-stu-id="5bf70-131">1408x792</span></span> |  <span data-ttu-id="5bf70-132">1408x792</span><span class="sxs-lookup"><span data-stu-id="5bf70-132">1408x792</span></span> |  <span data-ttu-id="5bf70-133">48度</span><span class="sxs-lookup"><span data-stu-id="5bf70-133">48 deg</span></span> |  <span data-ttu-id="5bf70-134">ビデオ安定化前のオーバースキャン (埋め込み) 解像度</span><span class="sxs-lookup"><span data-stu-id="5bf70-134">Overscan (padding) resolution before video stabilization</span></span> | 
  |  <span data-ttu-id="5bf70-135">1344x756</span><span class="sxs-lookup"><span data-stu-id="5bf70-135">1344x756</span></span> |  <span data-ttu-id="5bf70-136">1344x756</span><span class="sxs-lookup"><span data-stu-id="5bf70-136">1344x756</span></span> |  <span data-ttu-id="5bf70-137">1344x756</span><span class="sxs-lookup"><span data-stu-id="5bf70-137">1344x756</span></span> |  <span data-ttu-id="5bf70-138">67度</span><span class="sxs-lookup"><span data-stu-id="5bf70-138">67 deg</span></span> |  <span data-ttu-id="5bf70-139">オーバースキャンによる大規模な視界のビデオモード</span><span class="sxs-lookup"><span data-stu-id="5bf70-139">Large FOV video mode with overscan</span></span> | 
  |  <span data-ttu-id="5bf70-140">896x504</span><span class="sxs-lookup"><span data-stu-id="5bf70-140">896x504</span></span> |  <span data-ttu-id="5bf70-141">896x504</span><span class="sxs-lookup"><span data-stu-id="5bf70-141">896x504</span></span> |  <span data-ttu-id="5bf70-142">896x504</span><span class="sxs-lookup"><span data-stu-id="5bf70-142">896x504</span></span> |  <span data-ttu-id="5bf70-143">48度</span><span class="sxs-lookup"><span data-stu-id="5bf70-143">48 deg</span></span> |  <span data-ttu-id="5bf70-144">イメージ処理タスクの低電力/低解像度モード</span><span class="sxs-lookup"><span data-stu-id="5bf70-144">Low power / Low-resolution mode for image-processing tasks</span></span> | 

### <a name="hololens-2"></a><span data-ttu-id="5bf70-145">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5bf70-145">HoloLens 2</span></span>

* <span data-ttu-id="5bf70-146">自動ホワイトバランス、自動露出、完全な画像処理パイプラインを使用して、写真/ビデオ (PV) カメラを自動フォーカスします。</span><span class="sxs-lookup"><span data-stu-id="5bf70-146">Auto-focus photo/video (PV) camera with auto white balance, auto exposure, and full image-processing pipeline.</span></span>
* <span data-ttu-id="5bf70-147">世界中のホワイトプライバシー LED は、カメラがアクティブになるたびに点灯します。</span><span class="sxs-lookup"><span data-stu-id="5bf70-147">White Privacy LED facing the world will illuminate whenever the camera is active.</span></span>
* <span data-ttu-id="5bf70-148">HoloLens 2 では、さまざまなカメラプロファイルがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5bf70-148">HoloLens 2 supports different camera profiles.</span></span> <span data-ttu-id="5bf70-149">[カメラの機能を検出して選択](//windows/uwp/audio-video-camera/camera-profiles)する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5bf70-149">Learn how to [discover and select camera capabilities](//windows/uwp/audio-video-camera/camera-profiles).</span></span>
* <span data-ttu-id="5bf70-150">カメラでは、次のプロファイルと解像度がサポートされています (すべてのビデオモードは16:9 縦横比です)。</span><span class="sxs-lookup"><span data-stu-id="5bf70-150">The camera supports the following profiles and resolutions (all video modes are 16:9 aspect ratio):</span></span>
  
  | <span data-ttu-id="5bf70-151">プロファイル</span><span class="sxs-lookup"><span data-stu-id="5bf70-151">Profile</span></span>                                         | <span data-ttu-id="5bf70-152">ビデオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-152">Video</span></span>     | <span data-ttu-id="5bf70-153">プレビュー</span><span class="sxs-lookup"><span data-stu-id="5bf70-153">Preview</span></span>   | <span data-ttu-id="5bf70-154">それでもなお</span><span class="sxs-lookup"><span data-stu-id="5bf70-154">Still</span></span>     | <span data-ttu-id="5bf70-155">フレーム レート</span><span class="sxs-lookup"><span data-stu-id="5bf70-155">Frame rates</span></span> | <span data-ttu-id="5bf70-156">ビューの水平方向のフィールド (H 視界)</span><span class="sxs-lookup"><span data-stu-id="5bf70-156">Horizontal Field of View (H-FOV)</span></span> | <span data-ttu-id="5bf70-157">推奨される使用方法</span><span class="sxs-lookup"><span data-stu-id="5bf70-157">Suggested usage</span></span>                             |
  |-------------------------------------------------|-----------|-----------|-----------|-------------|----------------------------------|---------------------------------------------|
  | <span data-ttu-id="5bf70-158">Legacy、0 BalancedVideoAndPhoto、100</span><span class="sxs-lookup"><span data-stu-id="5bf70-158">Legacy,0  BalancedVideoAndPhoto,100</span></span>             | <span data-ttu-id="5bf70-159">2272x1278</span><span class="sxs-lookup"><span data-stu-id="5bf70-159">2272x1278</span></span> | <span data-ttu-id="5bf70-160">2272x1278</span><span class="sxs-lookup"><span data-stu-id="5bf70-160">2272x1278</span></span> |           | <span data-ttu-id="5bf70-161">15.30</span><span class="sxs-lookup"><span data-stu-id="5bf70-161">15.30</span></span>       | <span data-ttu-id="5bf70-162">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-162">64.69</span></span>                            | <span data-ttu-id="5bf70-163">高画質のビデオ記録</span><span class="sxs-lookup"><span data-stu-id="5bf70-163">High-quality video recording</span></span>                |
  | <span data-ttu-id="5bf70-164">Legacy、0 BalancedVideoAndPhoto、100</span><span class="sxs-lookup"><span data-stu-id="5bf70-164">Legacy,0  BalancedVideoAndPhoto,100</span></span>             | <span data-ttu-id="5bf70-165">896x504</span><span class="sxs-lookup"><span data-stu-id="5bf70-165">896x504</span></span>   | <span data-ttu-id="5bf70-166">896x504</span><span class="sxs-lookup"><span data-stu-id="5bf70-166">896x504</span></span>   |           | <span data-ttu-id="5bf70-167">15.30</span><span class="sxs-lookup"><span data-stu-id="5bf70-167">15.30</span></span>       | <span data-ttu-id="5bf70-168">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-168">64.69</span></span>                            | <span data-ttu-id="5bf70-169">高品質な写真キャプチャのためのプレビューストリーム</span><span class="sxs-lookup"><span data-stu-id="5bf70-169">Preview stream for high-quality photo capture</span></span> |
  | <span data-ttu-id="5bf70-170">Legacy、0 BalancedVideoAndPhoto、100</span><span class="sxs-lookup"><span data-stu-id="5bf70-170">Legacy,0  BalancedVideoAndPhoto,100</span></span>             |           |           | <span data-ttu-id="5bf70-171">3904x2196</span><span class="sxs-lookup"><span data-stu-id="5bf70-171">3904x2196</span></span> |             | <span data-ttu-id="5bf70-172">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-172">64.69</span></span>                            | <span data-ttu-id="5bf70-173">高品質な写真キャプチャ</span><span class="sxs-lookup"><span data-stu-id="5bf70-173">High-quality photo capture</span></span>                  |
  | <span data-ttu-id="5bf70-174">BalancedVideoAndPhoto、120</span><span class="sxs-lookup"><span data-stu-id="5bf70-174">BalancedVideoAndPhoto, 120</span></span>                       | <span data-ttu-id="5bf70-175">1952x1100</span><span class="sxs-lookup"><span data-stu-id="5bf70-175">1952x1100</span></span> | <span data-ttu-id="5bf70-176">1952x1100</span><span class="sxs-lookup"><span data-stu-id="5bf70-176">1952x1100</span></span> | <span data-ttu-id="5bf70-177">1952x1100</span><span class="sxs-lookup"><span data-stu-id="5bf70-177">1952x1100</span></span> | <span data-ttu-id="5bf70-178">15.30</span><span class="sxs-lookup"><span data-stu-id="5bf70-178">15.30</span></span>       | <span data-ttu-id="5bf70-179">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-179">64.69</span></span>                            | <span data-ttu-id="5bf70-180">長期間のシナリオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-180">Long duration scenarios</span></span>                     |
  | <span data-ttu-id="5bf70-181">BalancedVideoAndPhoto、120</span><span class="sxs-lookup"><span data-stu-id="5bf70-181">BalancedVideoAndPhoto, 120</span></span>                       | <span data-ttu-id="5bf70-182">1504x84 6</span><span class="sxs-lookup"><span data-stu-id="5bf70-182">1504x846</span></span>  | <span data-ttu-id="5bf70-183">1504x84 6</span><span class="sxs-lookup"><span data-stu-id="5bf70-183">1504x846</span></span>  |           | <span data-ttu-id="5bf70-184">15.30</span><span class="sxs-lookup"><span data-stu-id="5bf70-184">15.30</span></span>       | <span data-ttu-id="5bf70-185">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-185">64.69</span></span>                            | <span data-ttu-id="5bf70-186">長期間のシナリオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-186">Long duration scenarios</span></span>                     |
  | <span data-ttu-id="5bf70-187">ビデオ会議、100</span><span class="sxs-lookup"><span data-stu-id="5bf70-187">VideoConferencing,100</span></span>                           | <span data-ttu-id="5bf70-188">1952x1100</span><span class="sxs-lookup"><span data-stu-id="5bf70-188">1952x1100</span></span> | <span data-ttu-id="5bf70-189">1952x1100</span><span class="sxs-lookup"><span data-stu-id="5bf70-189">1952x1100</span></span> | <span data-ttu-id="5bf70-190">1952x1100</span><span class="sxs-lookup"><span data-stu-id="5bf70-190">1952x1100</span></span> | <span data-ttu-id="5bf70-191">15、30、60</span><span class="sxs-lookup"><span data-stu-id="5bf70-191">15,30,60</span></span>    | <span data-ttu-id="5bf70-192">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-192">64.69</span></span>                            | <span data-ttu-id="5bf70-193">ビデオ会議、長期間のシナリオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-193">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="5bf70-194">ビデオ会議、100</span><span class="sxs-lookup"><span data-stu-id="5bf70-194">Videoconferencing,100</span></span>                           | <span data-ttu-id="5bf70-195">1504x84 6</span><span class="sxs-lookup"><span data-stu-id="5bf70-195">1504x846</span></span>  | <span data-ttu-id="5bf70-196">1504x84 6</span><span class="sxs-lookup"><span data-stu-id="5bf70-196">1504x846</span></span>  |           | <span data-ttu-id="5bf70-197">5、15、30、60</span><span class="sxs-lookup"><span data-stu-id="5bf70-197">5,15,30,60</span></span>  | <span data-ttu-id="5bf70-198">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-198">64.69</span></span>                            | <span data-ttu-id="5bf70-199">ビデオ会議、長期間のシナリオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-199">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="5bf70-200">ビデオ会議、100 BalancedVideoAndPhoto、120</span><span class="sxs-lookup"><span data-stu-id="5bf70-200">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="5bf70-201">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="5bf70-201">1920x1080</span></span> | <span data-ttu-id="5bf70-202">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="5bf70-202">1920x1080</span></span> | <span data-ttu-id="5bf70-203">1920 x 1080</span><span class="sxs-lookup"><span data-stu-id="5bf70-203">1920x1080</span></span> | <span data-ttu-id="5bf70-204">15、30</span><span class="sxs-lookup"><span data-stu-id="5bf70-204">15,30</span></span>       | <span data-ttu-id="5bf70-205">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-205">64.69</span></span>                            | <span data-ttu-id="5bf70-206">ビデオ会議、長期間のシナリオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-206">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="5bf70-207">ビデオ会議、100 BalancedVideoAndPhoto、120</span><span class="sxs-lookup"><span data-stu-id="5bf70-207">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="5bf70-208">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="5bf70-208">1280x720</span></span>  | <span data-ttu-id="5bf70-209">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="5bf70-209">1280x720</span></span>  | <span data-ttu-id="5bf70-210">1280 x 720</span><span class="sxs-lookup"><span data-stu-id="5bf70-210">1280x720</span></span>  | <span data-ttu-id="5bf70-211">15、30</span><span class="sxs-lookup"><span data-stu-id="5bf70-211">15,30</span></span>       | <span data-ttu-id="5bf70-212">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-212">64.69</span></span>                            | <span data-ttu-id="5bf70-213">ビデオ会議、長期間のシナリオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-213">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="5bf70-214">ビデオ会議、100 BalancedVideoAndPhoto、120</span><span class="sxs-lookup"><span data-stu-id="5bf70-214">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="5bf70-215">1128x636</span><span class="sxs-lookup"><span data-stu-id="5bf70-215">1128x636</span></span>  |           |           | <span data-ttu-id="5bf70-216">15、30</span><span class="sxs-lookup"><span data-stu-id="5bf70-216">15,30</span></span>       | <span data-ttu-id="5bf70-217">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-217">64.69</span></span>                            | <span data-ttu-id="5bf70-218">ビデオ会議、長期間のシナリオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-218">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="5bf70-219">ビデオ会議、100 BalancedVideoAndPhoto、120</span><span class="sxs-lookup"><span data-stu-id="5bf70-219">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="5bf70-220">960 x 540</span><span class="sxs-lookup"><span data-stu-id="5bf70-220">960x540</span></span>   |           |           | <span data-ttu-id="5bf70-221">15、30</span><span class="sxs-lookup"><span data-stu-id="5bf70-221">15,30</span></span>       | <span data-ttu-id="5bf70-222">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-222">64.69</span></span>                            | <span data-ttu-id="5bf70-223">ビデオ会議、長期間のシナリオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-223">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="5bf70-224">ビデオ会議、100 BalancedVideoAndPhoto、120</span><span class="sxs-lookup"><span data-stu-id="5bf70-224">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="5bf70-225">760x428</span><span class="sxs-lookup"><span data-stu-id="5bf70-225">760x428</span></span>   |           |           | <span data-ttu-id="5bf70-226">15、30</span><span class="sxs-lookup"><span data-stu-id="5bf70-226">15,30</span></span>       | <span data-ttu-id="5bf70-227">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-227">64.69</span></span>                            | <span data-ttu-id="5bf70-228">ビデオ会議、長期間のシナリオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-228">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="5bf70-229">ビデオ会議、100 BalancedVideoAndPhoto、120</span><span class="sxs-lookup"><span data-stu-id="5bf70-229">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="5bf70-230">640 x 360</span><span class="sxs-lookup"><span data-stu-id="5bf70-230">640x360</span></span>   |           |           | <span data-ttu-id="5bf70-231">15、30</span><span class="sxs-lookup"><span data-stu-id="5bf70-231">15,30</span></span>       | <span data-ttu-id="5bf70-232">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-232">64.69</span></span>                            | <span data-ttu-id="5bf70-233">ビデオ会議、長期間のシナリオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-233">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="5bf70-234">ビデオ会議、100 BalancedVideoAndPhoto、120</span><span class="sxs-lookup"><span data-stu-id="5bf70-234">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="5bf70-235">500x282</span><span class="sxs-lookup"><span data-stu-id="5bf70-235">500x282</span></span>   |           |           | <span data-ttu-id="5bf70-236">15、30</span><span class="sxs-lookup"><span data-stu-id="5bf70-236">15,30</span></span>       | <span data-ttu-id="5bf70-237">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-237">64.69</span></span>                            | <span data-ttu-id="5bf70-238">ビデオ会議、長期間のシナリオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-238">Video conferencing, long duration scenarios</span></span> |
  | <span data-ttu-id="5bf70-239">ビデオ会議、100 BalancedVideoAndPhoto、120</span><span class="sxs-lookup"><span data-stu-id="5bf70-239">Videoconferencing,100 BalancedVideoAndPhoto,120</span></span> | <span data-ttu-id="5bf70-240">424x240</span><span class="sxs-lookup"><span data-stu-id="5bf70-240">424x240</span></span>   |           |           | <span data-ttu-id="5bf70-241">15、30</span><span class="sxs-lookup"><span data-stu-id="5bf70-241">15,30</span></span>       | <span data-ttu-id="5bf70-242">64.69</span><span class="sxs-lookup"><span data-stu-id="5bf70-242">64.69</span></span>                            | <span data-ttu-id="5bf70-243">ビデオ会議、長期間のシナリオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-243">Video conferencing, long duration scenarios</span></span> |

> [!NOTE]
> <span data-ttu-id="5bf70-244">[混合 reality キャプチャ](/hololens/holographic-photos-and-videos)を利用して、アプリのビデオや写真を撮ることができます。これには、ホログラムやビデオの安定化が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-244">Customers can leverage [mixed reality capture](/hololens/holographic-photos-and-videos) to take videos or photos of your app, which include holograms and video stabilization.</span></span>
>
><span data-ttu-id="5bf70-245">開発者にとっては、顧客がコンテンツをキャプチャしたときに可能な限り、アプリを作成する際に考慮する必要がある考慮事項があります。</span><span class="sxs-lookup"><span data-stu-id="5bf70-245">As a developer, there are considerations you should take into account when creating your app if you want it to look as good as possible when a customer captures content.</span></span> <span data-ttu-id="5bf70-246">また、アプリ内で直接、mixed reality キャプチャを有効 (およびカスタマイズ) することもできます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-246">You can also enable (and customize) mixed reality capture from directly within your app.</span></span> <span data-ttu-id="5bf70-247">詳細につい [ては、「開発者向けの混合現実のキャプチャ」を](mixed-reality-capture-for-developers.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bf70-247">Learn more at [mixed reality capture for developers](mixed-reality-capture-for-developers.md).</span></span>

## <a name="locating-the-device-camera-in-the-world"></a><span data-ttu-id="5bf70-248">デバイスカメラを世界中に配置する</span><span class="sxs-lookup"><span data-stu-id="5bf70-248">Locating the Device Camera in the World</span></span>

<span data-ttu-id="5bf70-249">HoloLens が写真やビデオを撮影する場合、キャプチャされたフレームには、世界中のカメラの位置とカメラのレンズモデルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-249">When HoloLens takes photos and videos, the captured frames include the location of the camera in the world and the lens model of the camera.</span></span> <span data-ttu-id="5bf70-250">これにより、アプリケーションは、イメージのシナリオを強化するために、実際の環境におけるカメラの位置を理解することができます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-250">This allows applications to reason about the position of the camera in the real world for augmented imaging scenarios.</span></span> <span data-ttu-id="5bf70-251">開発者は、お気に入りのイメージ処理またはカスタムコンピュータービジョンライブラリを使用して、独自のシナリオを独創ロールできます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-251">Developers can creatively roll their own scenarios using their favorite image processing or custom computer vision libraries.</span></span>

<span data-ttu-id="5bf70-252">HoloLens ドキュメントの他の場所にある "カメラ" は、"仮想ゲームカメラ" (アプリがレンダリングするための、視錐) を指している場合があります。</span><span class="sxs-lookup"><span data-stu-id="5bf70-252">"Camera" elsewhere in HoloLens documentation may refer to the "virtual game camera" (the frustum the app renders to).</span></span> <span data-ttu-id="5bf70-253">特に明記しない限り、このページの "カメラ" は実際の RGB カラーカメラを表します。</span><span class="sxs-lookup"><span data-stu-id="5bf70-253">Unless denoted otherwise, "camera" on this page refers to the real-world RGB color camera.</span></span>

### <a name="using-unity"></a><span data-ttu-id="5bf70-254">Unity の使用</span><span class="sxs-lookup"><span data-stu-id="5bf70-254">Using Unity</span></span>

<span data-ttu-id="5bf70-255">' CameraIntrinsics ' と ' CameraCoordinateSystem ' からアプリケーション/ワールド座標系に移行するには、 [Unity の検索カメラ](../unity/locatable-camera-in-unity.md) の記事に記載されている手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="5bf70-255">To go from the 'CameraIntrinsics' and 'CameraCoordinateSystem' to your application/world coordinate system, follow the instructions in the [Locatable camera in Unity](../unity/locatable-camera-in-unity.md) article.</span></span>  <span data-ttu-id="5bf70-256">CameraToWorldMatrix は PhotoCaptureFrame クラスによって自動的に提供されるため、以下で説明する CameraCoordinateSystem の変換について心配する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5bf70-256">CameraToWorldMatrix is automatically provided by PhotoCaptureFrame class, and so you don't need to worry about the CameraCoordinateSystem transforms discussed below.</span></span>

### <a name="using-mediaframereference"></a><span data-ttu-id="5bf70-257">MediaFrameReference の使用</span><span class="sxs-lookup"><span data-stu-id="5bf70-257">Using MediaFrameReference</span></span>

<span data-ttu-id="5bf70-258">これらの手順は、 [MediaFrameReference](//uwp/api/windows.media.capture.frames.mediaframereference) クラスを使用してカメラからイメージフレームを読み取る場合に適用されます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-258">These instructions apply if you'r using the [MediaFrameReference](//uwp/api/windows.media.capture.frames.mediaframereference) class to read image frames from the camera.</span></span>

<span data-ttu-id="5bf70-259">各イメージフレーム (写真またはビデオ) には、キャプチャ時にカメラでルート化された[SpatialCoordinateSystem](//uwp/api/windows.perception.spatial.spatialcoordinatesystem)が含まれています。これには、 [MediaFrameReference](//uwp/api/Windows.Media.Capture.Frames.MediaFrameReference)の[CoordinateSystem](//uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem)プロパティを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-259">Each image frame (whether photo or video) includes a [SpatialCoordinateSystem](//uwp/api/windows.perception.spatial.spatialcoordinatesystem) rooted at the camera at the time of capture, which can be accessed using the [CoordinateSystem](//uwp/api/windows.media.capture.frames.mediaframereference.coordinatesystem#Windows_Media_Capture_Frames_MediaFrameReference_CoordinateSystem) property of your [MediaFrameReference](//uwp/api/Windows.Media.Capture.Frames.MediaFrameReference).</span></span> <span data-ttu-id="5bf70-260">各フレームには、カメラレンズモデルの説明が含まれています。このモデルは、 [CameraIntrinsics](//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) プロパティにあります。</span><span class="sxs-lookup"><span data-stu-id="5bf70-260">Each frame contains a description of the camera lens model, which can be found in the [CameraIntrinsics](//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) property.</span></span> <span data-ttu-id="5bf70-261">これらの変換は、ピクセルを生成した photons によって取得されたパスを表す3D 空間の光をピクセルごとに定義します。</span><span class="sxs-lookup"><span data-stu-id="5bf70-261">Together, these transforms define for each pixel a ray in 3D space representing the path taken by the photons that produced the pixel.</span></span> <span data-ttu-id="5bf70-262">これらの光線は、フレームの座標系から他の座標系 (例: [静止フレーム](../../design/coordinate-systems.md#stationary-frame-of-reference)から) への変換を取得することによって、アプリ内の他のコンテンツに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-262">These rays can be related to other content in the app by obtaining the transform from the frame's coordinate system to some other coordinate system (e.g. from a [stationary frame of reference](../../design/coordinate-systems.md#stationary-frame-of-reference)).</span></span> 

<span data-ttu-id="5bf70-263">各イメージフレームには次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="5bf70-263">Each image frame provides the following:</span></span>
* <span data-ttu-id="5bf70-264">ピクセルデータ (RGB/NV12/JPEG/など)</span><span class="sxs-lookup"><span data-stu-id="5bf70-264">Pixel Data (in RGB/NV12/JPEG/etc. format)</span></span>
* <span data-ttu-id="5bf70-265">キャプチャの場所からの[SpatialCoordinateSystem](//uwp/api/windows.perception.spatial.spatialcoordinatesystem)</span><span class="sxs-lookup"><span data-stu-id="5bf70-265">A [SpatialCoordinateSystem](//uwp/api/windows.perception.spatial.spatialcoordinatesystem) from the location of capture</span></span>
* <span data-ttu-id="5bf70-266">カメラのレンズモードを含む [CameraIntrinsics](//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) クラス</span><span class="sxs-lookup"><span data-stu-id="5bf70-266">A [CameraIntrinsics](//uwp/api/windows.media.capture.frames.videomediaframe.cameraintrinsics#Windows_Media_Capture_Frames_VideoMediaFrame_CameraIntrinsics) class containing the lens mode of the camera</span></span>

<span data-ttu-id="5bf70-267">[HolographicFaceTracking サンプル](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)は、カメラの座標系と独自のアプリケーション座標系との間の変換をクエリするための非常に簡単な方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5bf70-267">The [HolographicFaceTracking sample](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking) shows the fairly straightforward way to query for the transform between the camera's coordinate system and your own application coordinate systems.</span></span>

### <a name="using-media-foundation"></a><span data-ttu-id="5bf70-268">メディアファンデーションの使用</span><span class="sxs-lookup"><span data-stu-id="5bf70-268">Using Media Foundation</span></span>

<span data-ttu-id="5bf70-269">カメラからイメージフレームを読み取るためにメディアファンデーション直接使用している場合は、次のサンプルコードに示すように、各フレームの [MFSampleExtension_CameraExtrinsics 属性](/windows/win32/medfound/mfsampleextension-cameraextrinsics) と [MFSampleExtension_PinholeCameraIntrinsics 属性](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) を使用して、アプリケーションの他の座標系を基準としたカメラフレームを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-269">If you are using Media Foundation directly to read image frames from the camera, you can use each frame's [MFSampleExtension_CameraExtrinsics attribute](/windows/win32/medfound/mfsampleextension-cameraextrinsics) and [MFSampleExtension_PinholeCameraIntrinsics attribute](/windows/win32/medfound/mfsampleextension-pinholecameraintrinsics) to locate camera frames relative to your application's other coordinate systems, as shown in this sample code:</span></span>

```cpp
#include <winrt/windows.perception.spatial.preview.h>
#include <mfapi.h>
#include <mfidl.h>
 
using namespace winrt::Windows::Foundation;
using namespace winrt::Windows::Foundation::Numerics;
using namespace winrt::Windows::Perception;
using namespace winrt::Windows::Perception::Spatial;
using namespace winrt::Windows::Perception::Spatial::Preview;
 
class CameraFrameLocator
{
public:
    struct CameraFrameLocation
    {
        SpatialCoordinateSystem CoordinateSystem;
        float4x4 CameraViewToCoordinateSytemTransform;
        MFPinholeCameraIntrinsics Intrinsics;
    };
 
    std::optional<CameraFrameLocation> TryLocateCameraFrame(IMFSample* pSample)
    {
        MFCameraExtrinsics cameraExtrinsics;
        MFPinholeCameraIntrinsics cameraIntrinsics;
        UINT32 sizeCameraExtrinsics = 0;
        UINT32 sizeCameraIntrinsics = 0;
        UINT64 sampleTimeHns = 0;
 
        // query sample for calibration and validate
        if (FAILED(pSample->GetUINT64(MFSampleExtension_DeviceTimestamp, &sampleTimeHns)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_CameraExtrinsics, (UINT8*)& cameraExtrinsics, sizeof(cameraExtrinsics), &sizeCameraExtrinsics)) ||
            FAILED(pSample->GetBlob(MFSampleExtension_PinholeCameraIntrinsics, (UINT8*)& cameraIntrinsics, sizeof(cameraIntrinsics), &sizeCameraIntrinsics)) ||
            (sizeCameraExtrinsics != sizeof(cameraExtrinsics)) ||
            (sizeCameraIntrinsics != sizeof(cameraIntrinsics)) ||
            (cameraExtrinsics.TransformCount == 0))
        {
            return std::nullopt;
        }
 
        // compute extrinsic transform
        const auto& calibratedTransform = cameraExtrinsics.CalibratedTransforms[0];
        const GUID& dynamicNodeId = calibratedTransform.CalibrationId;
        const float4x4 cameraToDynamicNode =
            make_float4x4_from_quaternion(quaternion{ calibratedTransform.Orientation.x, calibratedTransform.Orientation.y, calibratedTransform.Orientation.z, calibratedTransform.Orientation.w }) *
            make_float4x4_translation(calibratedTransform.Position.x, calibratedTransform.Position.y, calibratedTransform.Position.z);
 
        // update locator cache for dynamic node
        if (dynamicNodeId != m_currentDynamicNodeId || !m_locator)
        {
            m_locator = SpatialGraphInteropPreview::CreateLocatorForNode(dynamicNodeId);
            if (!m_locator)
            {
                return std::nullopt;
            }
 
            m_frameOfReference = m_locator.CreateAttachedFrameOfReferenceAtCurrentHeading();
            m_currentDynamicNodeId = dynamicNodeId;
        }
 
        // locate dynamic node
        auto timestamp = PerceptionTimestampHelper::FromSystemRelativeTargetTime(TimeSpan{ sampleTimeHns });
        auto coordinateSystem = m_frameOfReference.GetStationaryCoordinateSystemAtTimestamp(timestamp);
        auto location = m_locator.TryLocateAtTimestamp(timestamp, coordinateSystem);
        if (!location)
        {
            return std::nullopt;
        }
 
        const float4x4 dynamicNodeToCoordinateSystem = make_float4x4_from_quaternion(location.Orientation()) * make_float4x4_translation(location.Position());
 
        return CameraFrameLocation{ coordinateSystem, cameraToDynamicNode * dynamicNodeToCoordinateSystem, cameraIntrinsics };
    }

private:
    GUID m_currentDynamicNodeId{ GUID_NULL };
    SpatialLocator m_locator{ nullptr };
    SpatialLocatorAttachedFrameOfReference m_frameOfReference{ nullptr };
};
```

### <a name="distortion-error"></a><span data-ttu-id="5bf70-270">ディストーションエラー</span><span class="sxs-lookup"><span data-stu-id="5bf70-270">Distortion Error</span></span>

<span data-ttu-id="5bf70-271">HoloLens では、ビデオおよび静止画像ストリームは、アプリケーションでフレームを使用できるようになる前に、システムのイメージ処理パイプラインで undistorted されます (プレビューストリームには、元のゆがんだフレームが含まれます)。</span><span class="sxs-lookup"><span data-stu-id="5bf70-271">On HoloLens, the video and still image streams are undistorted in the system's image-processing pipeline before the frames are made available to the application (the preview stream contains the original distorted frames).</span></span> <span data-ttu-id="5bf70-272">使用できるのは CameraIntrinsics だけなので、アプリケーションではイメージフレームが完全な pinhole カメラを表すものと想定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5bf70-272">Because only the CameraIntrinsics are made available, applications must assume image frames represent a perfect pinhole camera.</span></span>

<span data-ttu-id="5bf70-273">HoloLens (第1世代) では、イメージプロセッサのディストーション関数は、フレームメタデータで CameraIntrinsics を使用しているときに最大10ピクセルのエラーを引き続き発生させる場合があります。</span><span class="sxs-lookup"><span data-stu-id="5bf70-273">On HoloLens (first-generation), the undistortion function in the image processor may still leave an error of up to 10 pixels when using the CameraIntrinsics in the frame metadata.</span></span> <span data-ttu-id="5bf70-274">多くのユースケースでは、このエラーは発生しませんが、たとえば、ホログラムを実際のポスター/マーカーに配置している場合は、<10 px オフセット (2 m の位置にあるホログラムの場合は約 11 mm) が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5bf70-274">In many use cases, this error won't matter, but if you're aligning holograms to real world posters/markers, for example, and you notice a <10-px offset (roughly 11 mm for holograms positioned 2 meters away), this distortion error could be the cause.</span></span> 

## <a name="locatable-camera-usage-scenarios"></a><span data-ttu-id="5bf70-275">お持ちのカメラの使用シナリオ</span><span class="sxs-lookup"><span data-stu-id="5bf70-275">Locatable Camera Usage Scenarios</span></span>

### <a name="show-a-photo-or-video-in-the-world-where-it-was-captured"></a><span data-ttu-id="5bf70-276">キャプチャされた場所で写真またはビデオを表示する</span><span class="sxs-lookup"><span data-stu-id="5bf70-276">Show a photo or video in the world where it was captured</span></span>

<span data-ttu-id="5bf70-277">デバイスカメラのフレームには、イメージがどこで撮影されたかを正確に示すために使用できる "カメラからワールドへの変換" 変換が付属しています。</span><span class="sxs-lookup"><span data-stu-id="5bf70-277">The Device Camera frames come with a "Camera To World" transform, that can be used to show exactly where the device was when the image was taken.</span></span> <span data-ttu-id="5bf70-278">たとえば、小さな holographic アイコンをこの場所 (CameraToWorld (Vector3)) に配置して、カメラが直面している方向に小さな矢印を描画する (CameraToWorld Yvector (Vector3)) ことができます ()。</span><span class="sxs-lookup"><span data-stu-id="5bf70-278">For example, you could position a small holographic icon at this location (CameraToWorld.MultiplyPoint(Vector3.zero)) and even draw a little arrow in the direction that the camera was facing (CameraToWorld.MultiplyVector(Vector3.forward)).</span></span>

### <a name="tag--pattern--poster--object-tracking"></a><span data-ttu-id="5bf70-279">タグ/パターン/ポスター/オブジェクトの追跡</span><span class="sxs-lookup"><span data-stu-id="5bf70-279">Tag / Pattern / Poster / Object Tracking</span></span>

<span data-ttu-id="5bf70-280">多くの mixed reality アプリケーションでは、認識可能なイメージまたはビジュアルパターンを使用して、空間内の追跡可能なポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="5bf70-280">Many mixed reality applications use a recognizable image or visual pattern to create a trackable point in space.</span></span> <span data-ttu-id="5bf70-281">その後、そのポイントを基準としてオブジェクトをレンダリングしたり、既知の場所を作成したりするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-281">This is then used to render objects relative to that point or create a known location.</span></span> <span data-ttu-id="5bf70-282">HoloLens の使用例としては、fiducials でタグ付けされた現実世界のオブジェクト (QR コードを使用したテレビモニターなど) の検索、fiducials に対するホログラムの配置、および Wi-fi を介して HoloLens と通信するように設定されているタブレットなどの非 HoloLens デバイスとの視覚的な組み合わせがあります。</span><span class="sxs-lookup"><span data-stu-id="5bf70-282">Some uses for HoloLens include finding a real world object tagged with fiducials (e.g. a TV monitor with a QR code), placing holograms over fiducials, and visually pairing with non-HoloLens devices like tablets that have been set up to communicate with HoloLens via Wi-Fi.</span></span>

<span data-ttu-id="5bf70-283">ビジュアルパターンを認識し、アプリケーションのワールド空間にオブジェクトを配置するには、いくつかの作業が必要です。</span><span class="sxs-lookup"><span data-stu-id="5bf70-283">You'll need a few things to recognize a visual pattern and place an object in the applications world space:</span></span>
1. <span data-ttu-id="5bf70-284">画像パターン認識ツールキット (QR コード、AR タグ、顔ファインダー、サークルトラッカー、OCR など)。</span><span class="sxs-lookup"><span data-stu-id="5bf70-284">An image pattern recognition toolkit, such as QR code, AR tags, face finder, circle trackers, OCR etc.</span></span>
2. <span data-ttu-id="5bf70-285">実行時にイメージフレームを収集して認識レイヤーに渡す</span><span class="sxs-lookup"><span data-stu-id="5bf70-285">Collect image frames at runtime, and pass them to the recognition layer</span></span>
3. <span data-ttu-id="5bf70-286">画像の位置を、世界中や世界中の写真に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-286">Unproject their image locations back into world positions, or likely world rays.</span></span> 
4. <span data-ttu-id="5bf70-287">これらの世界の場所に仮想モデルを配置する</span><span class="sxs-lookup"><span data-stu-id="5bf70-287">Position your virtual models over these world locations</span></span>

<span data-ttu-id="5bf70-288">いくつかの重要な画像処理リンクを次に示します。</span><span class="sxs-lookup"><span data-stu-id="5bf70-288">Some important image-processing links:</span></span>
* [<span data-ttu-id="5bf70-289">OpenCV</span><span class="sxs-lookup"><span data-stu-id="5bf70-289">OpenCV</span></span>](https://opencv.org/)
* [<span data-ttu-id="5bf70-290">QR タグ</span><span class="sxs-lookup"><span data-stu-id="5bf70-290">QR Tags</span></span>](https://en.wikipedia.org/wiki/QR_code)
* [<span data-ttu-id="5bf70-291">FaceSDK</span><span class="sxs-lookup"><span data-stu-id="5bf70-291">FaceSDK</span></span>](https://research.microsoft.com/projects/facesdk/)
* [<span data-ttu-id="5bf70-292">Microsoft Translator</span><span class="sxs-lookup"><span data-stu-id="5bf70-292">Microsoft Translator</span></span>](https://www.microsoft.com/translator/business)

<span data-ttu-id="5bf70-293">対話型アプリケーションのフレームレートを維持することは、特に長時間実行されるイメージ認識アルゴリズムを扱う場合に重要です。</span><span class="sxs-lookup"><span data-stu-id="5bf70-293">Keeping an interactive application frame-rate is critical, especially when dealing with long-running image recognition algorithms.</span></span> <span data-ttu-id="5bf70-294">このため、一般的には次のパターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="5bf70-294">For this reason, we commonly use the following pattern:</span></span>
1. <span data-ttu-id="5bf70-295">メインスレッド: カメラオブジェクトを管理します</span><span class="sxs-lookup"><span data-stu-id="5bf70-295">Main Thread: manages the camera object</span></span>
2. <span data-ttu-id="5bf70-296">メインスレッド: 新しいフレームの要求 (非同期)</span><span class="sxs-lookup"><span data-stu-id="5bf70-296">Main Thread: requests new frames (async)</span></span>
3. <span data-ttu-id="5bf70-297">メインスレッド: 新しいフレームを追跡スレッドに渡します</span><span class="sxs-lookup"><span data-stu-id="5bf70-297">Main Thread: pass new frames to tracking thread</span></span>
4. <span data-ttu-id="5bf70-298">追跡スレッド: キーポイントを収集するためのイメージの処理</span><span class="sxs-lookup"><span data-stu-id="5bf70-298">Tracking Thread: processes image to collect key points</span></span>
5. <span data-ttu-id="5bf70-299">メインスレッド: 検出されるキーポイントに一致するように仮想モデルを移動します</span><span class="sxs-lookup"><span data-stu-id="5bf70-299">Main Thread: moves virtual model to match found key points</span></span>
6. <span data-ttu-id="5bf70-300">メインスレッド: 手順2の繰り返し</span><span class="sxs-lookup"><span data-stu-id="5bf70-300">Main Thread: repeat from step 2</span></span>

<span data-ttu-id="5bf70-301">一部のイメージマーカーシステムは、1ピクセルの位置のみを提供します (他のユーザーが完全変換を提供します。このセクションは必要ありません)。これは、可能な場所の射線に相当します。</span><span class="sxs-lookup"><span data-stu-id="5bf70-301">Some image marker systems only provide a single pixel location (others provide the full transform in which case this section won't be needed), which equates to a ray of possible locations.</span></span> <span data-ttu-id="5bf70-302">1つの3d 位置に移動するには、複数の光線を活用し、最終的な結果をおおよその交点で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-302">To get to a single 3d location, we can then leverage multiple rays and find the final result by their approximate intersection.</span></span> <span data-ttu-id="5bf70-303">そのために必要な作業を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5bf70-303">To do this, you'll need to:</span></span>
1. <span data-ttu-id="5bf70-304">複数のカメライメージの収集を開始するループを取得する</span><span class="sxs-lookup"><span data-stu-id="5bf70-304">Get a loop going collecting multiple camera images</span></span>
2. <span data-ttu-id="5bf70-305">関連する特徴ポイントとそのワールド光線を検索する</span><span class="sxs-lookup"><span data-stu-id="5bf70-305">Find the associated feature points, and their world rays</span></span>
3. <span data-ttu-id="5bf70-306">特徴のディクショナリ (それぞれが複数のワールド線を持つ) がある場合は、次のコードを使用して、これらの光線の交差部分を解決できます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-306">When you have a dictionary of features, each with multiple world rays, you can use the following code to solve for the intersection of those rays:</span></span>

```
public static Vector3 ClosestPointBetweenRays(
   Vector3 point1, Vector3 normalizedDirection1,
   Vector3 point2, Vector3 normalizedDirection2) {
   float directionProjection = Vector3.Dot(normalizedDirection1, normalizedDirection2);
   if (directionProjection == 1) {
     return point1; // parallel lines
   }
   float projection1 = Vector3.Dot(point2 - point1, normalizedDirection1);
   float projection2 = Vector3.Dot(point2 - point1, normalizedDirection2);
   float distanceAlongLine1 = (projection1 - directionProjection * projection2) / (1 - directionProjection * directionProjection);
   float distanceAlongLine2 = (projection2 - directionProjection * projection1) / (directionProjection * directionProjection - 1);
   Vector3 pointOnLine1 = point1 + distanceAlongLine1 * normalizedDirection1;
   Vector3 pointOnLine2 = point2 + distanceAlongLine2 * normalizedDirection2;
   return Vector3.Lerp(pointOnLine2, pointOnLine1, 0.5f);
 }
```

<span data-ttu-id="5bf70-307">複数の追跡タグの場所を指定すると、ユーザーの現在のシナリオに合わせて、モデル化されたシーンを配置できます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-307">Given two or more tracked tag locations, you can position a modeled scene to fit the user's current scenario.</span></span> <span data-ttu-id="5bf70-308">重力を想定できない場合は、3つのタグ位置が必要になります。</span><span class="sxs-lookup"><span data-stu-id="5bf70-308">If you can't assume gravity, then you'll need three tag locations.</span></span> <span data-ttu-id="5bf70-309">多くの場合、白の球体がリアルタイムの追跡タグの位置を表し、青の球体がモデル化されたタグの場所を表す配色を使用します。</span><span class="sxs-lookup"><span data-stu-id="5bf70-309">In many cases, we use a color scheme where white spheres represent real-time tracked tag locations, and blue spheres represent modeled tag locations.</span></span> <span data-ttu-id="5bf70-310">これにより、ユーザーは配置品質を視覚的に測定できます。</span><span class="sxs-lookup"><span data-stu-id="5bf70-310">This allows the user to visually gauge the alignment quality.</span></span> <span data-ttu-id="5bf70-311">ここでは、すべてのアプリケーションで次のセットアップを想定しています。</span><span class="sxs-lookup"><span data-stu-id="5bf70-311">We assume the following setup in all our applications:</span></span>
* <span data-ttu-id="5bf70-312">2つ以上のモデル化タグの場所</span><span class="sxs-lookup"><span data-stu-id="5bf70-312">Two or more modeled tag locations</span></span>
* <span data-ttu-id="5bf70-313">シーン内の1つの ' 調整空間 ' は、タグの親です。</span><span class="sxs-lookup"><span data-stu-id="5bf70-313">One 'calibration space', which in the scene is the parent of the tags</span></span>
* <span data-ttu-id="5bf70-314">カメラの機能識別子</span><span class="sxs-lookup"><span data-stu-id="5bf70-314">Camera feature identifier</span></span>
* <span data-ttu-id="5bf70-315">動作は、モデル化されたタグをリアルタイムタグに合わせて調整領域を移動します (他の接続はその相対的な位置であるため、モデル化されたマーカー自体ではなく、親スペースを移動するのは注意してください)。</span><span class="sxs-lookup"><span data-stu-id="5bf70-315">Behavior, which moves the calibration space to align the modeled tags with the real-time tags (we're careful to move the parent space, not the modeled markers themselves, because other connect is positions relative to them).</span></span>

```
// In the two tags case:
 Vector3 idealDelta = (realTags[1].EstimatedWorldPos - realTags[0].EstimatedWorldPos);
 Vector3 curDelta = (modelledTags[1].transform.position - modelledTags[0].transform.position);
 if (IsAssumeGravity) {
   idealDelta.y = 0;
   curDelta.y = 0;
 }
 Quaternion deltaRot = Quaternion.FromToRotation(curDelta, idealDelta);
 trans.rotation = Quaternion.LookRotation(deltaRot * trans.forward, trans.up);
 trans.position += realTags[0].EstimatedWorldPos - modelledTags[0].transform.position;
```

### <a name="track-or-identify-tagged-stationary-or-moving-real-world-objectsfaces-using-leds-or-other-recognizer-libraries"></a><span data-ttu-id="5bf70-316">Led または他のレコグナイザーライブラリを使用して、タグ付き静止を追跡または特定したり、実際のオブジェクト/顔を移動したりします。</span><span class="sxs-lookup"><span data-stu-id="5bf70-316">Track or Identify Tagged Stationary or Moving real-world objects/faces using LEDs or other recognizer libraries</span></span>

<span data-ttu-id="5bf70-317">例 :</span><span class="sxs-lookup"><span data-stu-id="5bf70-317">Examples:</span></span>
* <span data-ttu-id="5bf70-318">Led のある工業ロボット (または低速な移動オブジェクトの QR コード)</span><span class="sxs-lookup"><span data-stu-id="5bf70-318">Industrial robots with LEDs (or QR codes for slower moving objects)</span></span>
* <span data-ttu-id="5bf70-319">ルーム内のオブジェクトを識別して認識する</span><span class="sxs-lookup"><span data-stu-id="5bf70-319">Identify and recognize objects in the room</span></span>
* <span data-ttu-id="5bf70-320">部屋の中の人間を識別して認識します。たとえば、顔に holographic の連絡先カードを配置します。</span><span class="sxs-lookup"><span data-stu-id="5bf70-320">Identify and recognize people in the room, for example placing holographic contact cards over faces</span></span>

## <a name="see-also"></a><span data-ttu-id="5bf70-321">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bf70-321">See also</span></span>
* [<span data-ttu-id="5bf70-322">お持ちのカメラのサンプル</span><span class="sxs-lookup"><span data-stu-id="5bf70-322">Locatable camera sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)
* [<span data-ttu-id="5bf70-323">Unity での場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="5bf70-323">Locatable camera in Unity</span></span>](../unity/locatable-camera-in-unity.md)
* [<span data-ttu-id="5bf70-324">複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="5bf70-324">Mixed reality capture</span></span>](/hololens/holographic-photos-and-videos)
* [<span data-ttu-id="5bf70-325">開発者向け複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="5bf70-325">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="5bf70-326">メディアキャプチャの概要</span><span class="sxs-lookup"><span data-stu-id="5bf70-326">Media capture introduction</span></span>](/windows/uwp/audio-video-camera/)
* [<span data-ttu-id="5bf70-327">Holographic face tracking サンプル</span><span class="sxs-lookup"><span data-stu-id="5bf70-327">Holographic face tracking sample</span></span>](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicFaceTracking)