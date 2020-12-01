---
title: Holographic リモート処理のトラブルシューティングと制限事項
description: HoloLens 2 での Holographic Remoting のトラブルシューティングの手順
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, ホログラム, holographic リモート処理, リモートレンダリング, ネットワークレンダリング, HoloLens, リモートホログラム, トラブルシューティング, ヘルプ, Mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: ca0e4b3a43eae5be09f2c0bfbee9056cd847787c
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443602"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="5ab26-104">Holographic リモート処理のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="5ab26-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5ab26-105">このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="5ab26-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="5ab26-106">Spectre の緩和されたライブラリが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="5ab26-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="5ab26-107">Holographic リモート処理サンプルアプリでは、リリース構成で Spectre 軽減策 (/Qspectre) が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="5ab26-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="5ab26-108">"Vccorlib .lib" を開くことができないという致命的なリンカーエラーが発生した場合は、Visual Studio ワークロードに Spectre 軽減可能なライブラリが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5ab26-108">If you get a fatal linker error which states that 'vccorlib.lib' cannot be opened, make sure that your Visual Studio Workload includes the Spectre mitigated libraries.</span></span> <span data-ttu-id="5ab26-109">詳細については、「 https://aka.ms/Ofhn4c 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ab26-109">See https://aka.ms/Ofhn4c for more information.</span></span>

## <a name="speech"></a><span data-ttu-id="5ab26-110">音声</span><span class="sxs-lookup"><span data-stu-id="5ab26-110">Speech</span></span>

<span data-ttu-id="5ab26-111">Holographic Remoting Player は診断オーバーレイをサポートしています。これは、「」と言って無効にすることで有効にすることができ ```Enable Diagnostics``` ```Disable Diagnostics``` ます。</span><span class="sxs-lookup"><span data-stu-id="5ab26-111">The Holographic Remoting Player supports a diagnostics overlay which can be enabled by saying ```Enable Diagnostics``` and disabled by saying ```Disable Diagnostics```.</span></span> <span data-ttu-id="5ab26-112">これらの音声コマンドで問題が発生した場合は、URL としてを使用して web ブラウザーで Holographic リモート処理プレーヤーを起動することもできます ```ms-holographic-remoting:?stats``` 。</span><span class="sxs-lookup"><span data-stu-id="5ab26-112">If you have trouble with these voice commands you can also launch the Holographic Remoting player via a web browser using ```ms-holographic-remoting:?stats``` as an URL.</span></span>

## <a name="h265-video-codec-not-available"></a><span data-ttu-id="5ab26-113">H265 video コーデックは使用できません</span><span class="sxs-lookup"><span data-stu-id="5ab26-113">H265 video codec not available</span></span>

<span data-ttu-id="5ab26-114">リモートアプリで H265 video コーデックを使用する場合は、 [HEVC ビデオ拡張機能](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5ab26-114">You need to install the [HEVC Video Extensions](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) when using H265 video codec in your remote app.</span></span> <span data-ttu-id="5ab26-115">コーデックがインストールされていても使用できない問題が発生した場合は、「 [トラブルシューティング](https://docs.microsoft.com/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) ガイド」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ab26-115">If you run into issues where the codec is installed but can't be used, check out [troubleshooting](https://docs.microsoft.com/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) guide.</span></span>

## <a name="limitations"></a><span data-ttu-id="5ab26-116">制限事項</span><span class="sxs-lookup"><span data-stu-id="5ab26-116">Limitations</span></span>

<span data-ttu-id="5ab26-117">Holographic Remoting を HoloLens 2 に使用する場合、次の Api は現在サポートされて **いません** 。特に明記されて ```ERROR_NOT_SUPPORTED``` いない限り、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="5ab26-117">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raises an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="5ab26-118">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="5ab26-118">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="5ab26-119">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="5ab26-119">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="5ab26-120">サポートされているバージョン[2.0.18](holographic-remoting-version-history.md#v2.0.18)以降</span><span class="sxs-lookup"><span data-stu-id="5ab26-120">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="5ab26-121">以前のバージョンでは、常にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="5ab26-121">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="5ab26-122">HolographicCamera.IsHardwareContentProtectionEnabled</span><span class="sxs-lookup"><span data-stu-id="5ab26-122">HolographicCamera.IsHardwareContentProtectionEnabled</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [<span data-ttu-id="5ab26-123">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="5ab26-123">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="5ab26-124">バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="5ab26-124">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="5ab26-125">以前のバージョンでは、は失敗しませんが、レンダーターゲットのサイズは変更されません。</span><span class="sxs-lookup"><span data-stu-id="5ab26-125">On previous versions does not fail, but the render target size will not be changed.</span></span>
* [<span data-ttu-id="5ab26-126">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="5ab26-126">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="5ab26-127">HolographicCameraPose ビューポート</span><span class="sxs-lookup"><span data-stu-id="5ab26-127">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="5ab26-128">HolographicCameraPose</span><span class="sxs-lookup"><span data-stu-id="5ab26-128">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - <span data-ttu-id="5ab26-129">バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="5ab26-129">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="5ab26-130">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="5ab26-130">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="5ab26-131">は失敗しませんが、深度バッファーはリモート処理されません。</span><span class="sxs-lookup"><span data-stu-id="5ab26-131">Does not fail but depth buffer will not be remoted.</span></span>
  - <span data-ttu-id="5ab26-132">サポートされているバージョン[2.1.0](holographic-remoting-version-history.md#v2.1.0)以降</span><span class="sxs-lookup"><span data-stu-id="5ab26-132">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="5ab26-133">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="5ab26-133">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="5ab26-134">HolographicViewConfigurationKind にクエリを実行すると、常にが返されます ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="5ab26-134">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="5ab26-135">サポートされているバージョン[2.0.18](holographic-remoting-version-history.md#v2.0.18)以降</span><span class="sxs-lookup"><span data-stu-id="5ab26-135">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="5ab26-136">以前のバージョンでは、常にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="5ab26-136">On previous versions always raises an error.</span></span>
* [<span data-ttu-id="5ab26-137">HolographicSpace プレゼンテーションモニター</span><span class="sxs-lookup"><span data-stu-id="5ab26-137">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="5ab26-138">HolographicDisplay</span><span class="sxs-lookup"><span data-stu-id="5ab26-138">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="5ab26-139">は、接続が確立される前に呼び出された場合にエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="5ab26-139">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="5ab26-140">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="5ab26-140">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="5ab26-141">SpatialLocation AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="5ab26-141">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="5ab26-142">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="5ab26-142">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="5ab26-143">SpatialLocation AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="5ab26-143">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="5ab26-144">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="5ab26-144">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="5ab26-145">SpatialLocation AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="5ab26-145">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="5ab26-146">SpatialLocation AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="5ab26-146">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="5ab26-147">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="5ab26-147">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="5ab26-148">バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="5ab26-148">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="5ab26-149">以前のバージョンでは、は常にを返し ```nullptr``` ます。</span><span class="sxs-lookup"><span data-stu-id="5ab26-149">On previous versions always returns ```nullptr```.</span></span>
* [<span data-ttu-id="5ab26-150">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="5ab26-150">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - <span data-ttu-id="5ab26-151">バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="5ab26-151">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="5ab26-152">SpatialAnchor. RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="5ab26-152">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="5ab26-153">SpatialAnchorExporter.GetDefault</span><span class="sxs-lookup"><span data-stu-id="5ab26-153">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="5ab26-154">バージョン [2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5ab26-154">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="5ab26-155">以前のバージョンでは、は常にを返し ```nullptr``` ます。</span><span class="sxs-lookup"><span data-stu-id="5ab26-155">On previous versions always returns ```nullptr```.</span></span> 
* [<span data-ttu-id="5ab26-156">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="5ab26-156">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="5ab26-157">バージョン [2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5ab26-157">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="5ab26-158">以前のバージョンでは、非同期操作は常にで完了していました ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。</span><span class="sxs-lookup"><span data-stu-id="5ab26-158">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="5ab26-159">SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="5ab26-159">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="5ab26-160">非同期操作は常にで完了 ```SpatialPerceptionAccessStatus.DeniedBySystem``` します。</span><span class="sxs-lookup"><span data-stu-id="5ab26-160">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="5ab26-161">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="5ab26-161">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="5ab26-162">非同期操作は常にで完了 ```false``` します。</span><span class="sxs-lookup"><span data-stu-id="5ab26-162">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="5ab26-163">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="5ab26-163">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="5ab26-164">非同期操作は常にで完了 ```nullptr``` します。</span><span class="sxs-lookup"><span data-stu-id="5ab26-164">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="5ab26-165">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="5ab26-165">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="5ab26-166">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="5ab26-166">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="5ab26-167">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="5ab26-167">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [<span data-ttu-id="5ab26-168">SpatialInteractionSource</span><span class="sxs-lookup"><span data-stu-id="5ab26-168">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - <span data-ttu-id="5ab26-169">バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="5ab26-169">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>

[<span data-ttu-id="5ab26-170">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="5ab26-170">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="5ab26-171">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="5ab26-171">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="5ab26-172">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="5ab26-172">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="5ab26-173">参照</span><span class="sxs-lookup"><span data-stu-id="5ab26-173">See Also</span></span>
* [<span data-ttu-id="5ab26-174">Holographic リモート処理のバージョン履歴</span><span class="sxs-lookup"><span data-stu-id="5ab26-174">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="5ab26-175">Windows Mixed Realiy Api を使用した Holographic リモート処理リモートアプリの作成</span><span class="sxs-lookup"><span data-stu-id="5ab26-175">Writing a Holographic Remoting remote app using Windows Mixed Realiy APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="5ab26-176">OpenXR Api を使用した Holographic リモート処理リモートアプリの作成</span><span class="sxs-lookup"><span data-stu-id="5ab26-176">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="5ab26-177">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="5ab26-177">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="5ab26-178">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="5ab26-178">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="5ab26-179">Microsoft プライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="5ab26-179">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
