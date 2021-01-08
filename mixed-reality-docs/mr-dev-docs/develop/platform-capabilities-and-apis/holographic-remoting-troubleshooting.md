---
title: Holographic リモート処理のトラブルシューティングと制限事項
description: HoloLens 2 デバイスでの Holographic リモート処理機能に関するトラブルシューティングリソースと手順を紹介します。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, ホログラム, holographic リモート処理, リモートレンダリング, ネットワークレンダリング, HoloLens, リモートホログラム, トラブルシューティング, ヘルプ, Mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: ee1dce72af02374e930de4a1bdff94285c7a84ae
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006452"
---
# <a name="holographic-remoting-troubleshooting"></a><span data-ttu-id="7d546-104">Holographic リモート処理のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="7d546-104">Holographic Remoting troubleshooting</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7d546-105">このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="7d546-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

## <a name="spectre-mitigated-libraries-not-found"></a><span data-ttu-id="7d546-106">Spectre の緩和されたライブラリが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="7d546-106">Spectre mitigated libraries not found.</span></span>

<span data-ttu-id="7d546-107">Holographic リモート処理サンプルアプリでは、リリース構成で Spectre 軽減策 (/Qspectre) が有効になっています。</span><span class="sxs-lookup"><span data-stu-id="7d546-107">Holographic Remoting sample apps have Spectre mitigation (/Qspectre) enabled in Release configuration.</span></span>

<span data-ttu-id="7d546-108">*Vccorlib を開けない* 場合は、Visual Studio のワークロードに [Spectre 軽減](https://aka.ms/Ofhn4c)可能なライブラリが含まれていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7d546-108">If you get the *vccorlib.lib cannot be opened* fatal error, make sure that your Visual Studio Workload includes the [Spectre mitigated libraries](https://aka.ms/Ofhn4c)</span></span>

## <a name="speech"></a><span data-ttu-id="7d546-109">音声</span><span class="sxs-lookup"><span data-stu-id="7d546-109">Speech</span></span>

<span data-ttu-id="7d546-110">Holographic リモート処理プレーヤーは診断オーバーレイをサポートしています。これは、「」と言って、無効にすることで有効にすることができ ```Enable Diagnostics``` ```Disable Diagnostics``` ます。</span><span class="sxs-lookup"><span data-stu-id="7d546-110">The Holographic Remoting Player supports a diagnostics overlay, which can be enabled by saying ```Enable Diagnostics``` and disabled by saying ```Disable Diagnostics```.</span></span> <span data-ttu-id="7d546-111">これらの音声コマンドで問題が発生した場合は、URL としてを使用して web ブラウザーで Holographic リモート処理プレーヤーを起動することもでき ```ms-holographic-remoting:?stats``` ます。</span><span class="sxs-lookup"><span data-stu-id="7d546-111">If you have trouble with these voice commands, you can also launch the Holographic Remoting player via a web browser using ```ms-holographic-remoting:?stats``` as a URL.</span></span>

## <a name="h265-video-codec-not-available"></a><span data-ttu-id="7d546-112">H265 video コーデックは使用できません</span><span class="sxs-lookup"><span data-stu-id="7d546-112">H265 video codec not available</span></span>

<span data-ttu-id="7d546-113">リモートアプリで H265 video コーデックを使用する場合は、 [HEVC ビデオ拡張機能](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) をインストールします。</span><span class="sxs-lookup"><span data-stu-id="7d546-113">Install the [HEVC Video Extensions](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) when using H265 video codec in your remote app.</span></span> <span data-ttu-id="7d546-114">コーデックがインストールされていても使用できない問題が発生した場合は、「 [トラブルシューティング](https://docs.microsoft.com/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) ガイド」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d546-114">If you run into issues where the codec is installed but can't be used, check out [troubleshooting](https://docs.microsoft.com/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) guide.</span></span>

## <a name="limitations"></a><span data-ttu-id="7d546-115">制限事項</span><span class="sxs-lookup"><span data-stu-id="7d546-115">Limitations</span></span>

<span data-ttu-id="7d546-116">Holographic Remoting を HoloLens 2 に使用する場合、次の Api は現在サポートされて **いません** 。特に明記されて ```ERROR_NOT_SUPPORTED``` いない限り、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7d546-116">The following APIs are currently **not** supported when using Holographic Remoting for HoloLens 2 and will raise an ```ERROR_NOT_SUPPORTED``` error unless otherwise stated:</span></span>

[<span data-ttu-id="7d546-117">Windows.Graphics.Holographic</span><span class="sxs-lookup"><span data-stu-id="7d546-117">Windows.Graphics.Holographic</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [<span data-ttu-id="7d546-118">HolographicCamera.ViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="7d546-118">HolographicCamera.ViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - <span data-ttu-id="7d546-119">サポートされているバージョン[2.0.18](holographic-remoting-version-history.md#v2.0.18)以降</span><span class="sxs-lookup"><span data-stu-id="7d546-119">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="7d546-120">以前のバージョンでは、常にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7d546-120">On previous versions always raise an error.</span></span>
* [<span data-ttu-id="7d546-121">HolographicCamera.IsHardwareContentProtectionEnabled</span><span class="sxs-lookup"><span data-stu-id="7d546-121">HolographicCamera.IsHardwareContentProtectionEnabled</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [<span data-ttu-id="7d546-122">HolographicViewConfiguration.RequestRenderTargetSize</span><span class="sxs-lookup"><span data-stu-id="7d546-122">HolographicViewConfiguration.RequestRenderTargetSize</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - <span data-ttu-id="7d546-123">バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7d546-123">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="7d546-124">以前のバージョンでは失敗しませんが、レンダーターゲットのサイズは変更されません。</span><span class="sxs-lookup"><span data-stu-id="7d546-124">On previous versions don't fail, but the render target size won't be changed.</span></span>
* [<span data-ttu-id="7d546-125">HolographicCameraPose.OverrideProjectionTransform</span><span class="sxs-lookup"><span data-stu-id="7d546-125">HolographicCameraPose.OverrideProjectionTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [<span data-ttu-id="7d546-126">HolographicCameraPose ビューポート</span><span class="sxs-lookup"><span data-stu-id="7d546-126">HolographicCameraPose.OverrideViewport</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [<span data-ttu-id="7d546-127">HolographicCameraPose</span><span class="sxs-lookup"><span data-stu-id="7d546-127">HolographicCameraPose.OverrideViewTransform</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - <span data-ttu-id="7d546-128">バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7d546-128">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="7d546-129">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span><span class="sxs-lookup"><span data-stu-id="7d546-129">HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - <span data-ttu-id="7d546-130">姓.</span><span class="sxs-lookup"><span data-stu-id="7d546-130">Doe.</span></span>
  - <span data-ttu-id="7d546-131">サポートされているバージョン[2.1.0](holographic-remoting-version-history.md#v2.1.0)以降</span><span class="sxs-lookup"><span data-stu-id="7d546-131">Supported starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0)</span></span>
* [<span data-ttu-id="7d546-132">HolographicDisplay.TryGetViewConfiguration</span><span class="sxs-lookup"><span data-stu-id="7d546-132">HolographicDisplay.TryGetViewConfiguration</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - <span data-ttu-id="7d546-133">HolographicViewConfigurationKind にクエリを実行すると、常にが返されます ```nullptr``` 。</span><span class="sxs-lookup"><span data-stu-id="7d546-133">Querying HolographicViewConfigurationKind.PhotoVideoCamera will always return a ```nullptr```.</span></span>
  - <span data-ttu-id="7d546-134">サポートされているバージョン[2.0.18](holographic-remoting-version-history.md#v2.0.18)以降</span><span class="sxs-lookup"><span data-stu-id="7d546-134">Supported starting with version [2.0.18](holographic-remoting-version-history.md#v2.0.18)</span></span>
  - <span data-ttu-id="7d546-135">以前のバージョンでは、常にエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="7d546-135">On previous versions always raise an error.</span></span>
* [<span data-ttu-id="7d546-136">HolographicSpace プレゼンテーションモニター</span><span class="sxs-lookup"><span data-stu-id="7d546-136">HolographicSpace.CreateFramePresentationMonitor</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [<span data-ttu-id="7d546-137">HolographicDisplay</span><span class="sxs-lookup"><span data-stu-id="7d546-137">HolographicDisplay.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - <span data-ttu-id="7d546-138">は、接続が確立される前に呼び出された場合にエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="7d546-138">Will report an error if called before a connection was established.</span></span>


[<span data-ttu-id="7d546-139">Windows.Perception.Spatial</span><span class="sxs-lookup"><span data-stu-id="7d546-139">Windows.Perception.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [<span data-ttu-id="7d546-140">SpatialLocation AbsoluteAngularAcceleration</span><span class="sxs-lookup"><span data-stu-id="7d546-140">SpatialLocation.AbsoluteAngularAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [<span data-ttu-id="7d546-141">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span><span class="sxs-lookup"><span data-stu-id="7d546-141">SpatialLocation.AbsoluteAngularAccelerationAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [<span data-ttu-id="7d546-142">SpatialLocation AbsoluteAngularVelocity</span><span class="sxs-lookup"><span data-stu-id="7d546-142">SpatialLocation.AbsoluteAngularVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [<span data-ttu-id="7d546-143">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span><span class="sxs-lookup"><span data-stu-id="7d546-143">SpatialLocation.AbsoluteAngularVelocityAxisAngle</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [<span data-ttu-id="7d546-144">SpatialLocation AbsoluteLinearAcceleration</span><span class="sxs-lookup"><span data-stu-id="7d546-144">SpatialLocation.AbsoluteLinearAcceleration</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [<span data-ttu-id="7d546-145">SpatialLocation AbsoluteLinearVelocity</span><span class="sxs-lookup"><span data-stu-id="7d546-145">SpatialLocation.AbsoluteLinearVelocity</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [<span data-ttu-id="7d546-146">SpatialStageFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="7d546-146">SpatialStageFrameOfReference.Current</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - <span data-ttu-id="7d546-147">バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7d546-147">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
  - <span data-ttu-id="7d546-148">以前のバージョンでは、常にを返し ```nullptr``` ます。</span><span class="sxs-lookup"><span data-stu-id="7d546-148">On previous versions always return ```nullptr```.</span></span>
* [<span data-ttu-id="7d546-149">SpatialStageFrameOfReference.RequestNewStageAsync</span><span class="sxs-lookup"><span data-stu-id="7d546-149">SpatialStageFrameOfReference.RequestNewStageAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - <span data-ttu-id="7d546-150">バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7d546-150">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>
* [<span data-ttu-id="7d546-151">SpatialAnchor. RemovedByUser</span><span class="sxs-lookup"><span data-stu-id="7d546-151">SpatialAnchor.RemovedByUser</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [<span data-ttu-id="7d546-152">SpatialAnchorExporter.GetDefault</span><span class="sxs-lookup"><span data-stu-id="7d546-152">SpatialAnchorExporter.GetDefault</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - <span data-ttu-id="7d546-153">バージョン [2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7d546-153">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="7d546-154">以前のバージョンでは、常にを返し ```nullptr``` ます。</span><span class="sxs-lookup"><span data-stu-id="7d546-154">On previous versions always return ```nullptr```.</span></span> 
* [<span data-ttu-id="7d546-155">SpatialAnchorExporter.RequestAccessAsync</span><span class="sxs-lookup"><span data-stu-id="7d546-155">SpatialAnchorExporter.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - <span data-ttu-id="7d546-156">バージョン [2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7d546-156">Supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 
  - <span data-ttu-id="7d546-157">以前のバージョンでは、非同期操作は常にで完了していました ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。</span><span class="sxs-lookup"><span data-stu-id="7d546-157">On previous versions the async operation always completed with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="7d546-158">SpatialAnchorTransferManager</span><span class="sxs-lookup"><span data-stu-id="7d546-158">SpatialAnchorTransferManager.RequestAccessAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - <span data-ttu-id="7d546-159">非同期操作は常にで完了 ```SpatialPerceptionAccessStatus.DeniedBySystem``` します。</span><span class="sxs-lookup"><span data-stu-id="7d546-159">Async operation always completes with ```SpatialPerceptionAccessStatus.DeniedBySystem```.</span></span>
* [<span data-ttu-id="7d546-160">SpatialAnchorTransferManager.TryExportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="7d546-160">SpatialAnchorTransferManager.TryExportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - <span data-ttu-id="7d546-161">非同期操作は常にで完了 ```false``` します。</span><span class="sxs-lookup"><span data-stu-id="7d546-161">Async operation always completes with ```false```.</span></span>
* [<span data-ttu-id="7d546-162">SpatialAnchorTransferManager.TryImportAnchorsAsync</span><span class="sxs-lookup"><span data-stu-id="7d546-162">SpatialAnchorTransferManager.TryImportAnchorsAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - <span data-ttu-id="7d546-163">非同期操作は常にで完了 ```nullptr``` します。</span><span class="sxs-lookup"><span data-stu-id="7d546-163">Async operation always completes with ```nullptr```.</span></span>

[<span data-ttu-id="7d546-164">Windows.UI.Input.Spatial</span><span class="sxs-lookup"><span data-stu-id="7d546-164">Windows.UI.Input.Spatial</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [<span data-ttu-id="7d546-165">SpatialInteractionSource.TryCreateHandMeshObserver</span><span class="sxs-lookup"><span data-stu-id="7d546-165">SpatialInteractionSource.TryCreateHandMeshObserver</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [<span data-ttu-id="7d546-166">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span><span class="sxs-lookup"><span data-stu-id="7d546-166">SpatialInteractionSource.TryCreateHandMeshObserverAsync</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [<span data-ttu-id="7d546-167">SpatialInteractionSource</span><span class="sxs-lookup"><span data-stu-id="7d546-167">SpatialInteractionSource.Controller</span></span>](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - <span data-ttu-id="7d546-168">バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="7d546-168">Supported starting with version [2.2.0](holographic-remoting-version-history.md#v2.2.0)</span></span>

[<span data-ttu-id="7d546-169">Windows.Perception.Spatial.Preview</span><span class="sxs-lookup"><span data-stu-id="7d546-169">Windows.Perception.Spatial.Preview</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [<span data-ttu-id="7d546-170">SpatialGraphInteropPreview.CreateLocatorForNode</span><span class="sxs-lookup"><span data-stu-id="7d546-170">SpatialGraphInteropPreview.CreateLocatorForNode</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [<span data-ttu-id="7d546-171">SpatialGraphInteropPreview.TryCreateFrameOfReference</span><span class="sxs-lookup"><span data-stu-id="7d546-171">SpatialGraphInteropPreview.TryCreateFrameOfReference</span></span>](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a><span data-ttu-id="7d546-172">参照</span><span class="sxs-lookup"><span data-stu-id="7d546-172">See Also</span></span>
* [<span data-ttu-id="7d546-173">Holographic リモート処理のバージョン履歴</span><span class="sxs-lookup"><span data-stu-id="7d546-173">Holographic Remoting Version History</span></span>](holographic-remoting-version-history.md)
* [<span data-ttu-id="7d546-174">Windows Mixed Reality Api を使用した Holographic リモート処理リモートアプリの作成</span><span class="sxs-lookup"><span data-stu-id="7d546-174">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="7d546-175">OpenXR Api を使用した Holographic リモート処理リモートアプリの作成</span><span class="sxs-lookup"><span data-stu-id="7d546-175">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="7d546-176">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="7d546-176">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="7d546-177">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="7d546-177">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="7d546-178">Microsoft プライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="7d546-178">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
