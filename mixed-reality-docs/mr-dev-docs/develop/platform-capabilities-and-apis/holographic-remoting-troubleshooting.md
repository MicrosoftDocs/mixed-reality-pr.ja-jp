---
title: Holographic リモート処理のトラブルシューティングと制限事項
description: HoloLens 2 での Holographic Remoting のトラブルシューティングの手順
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 03/11/2020
ms.topic: article
keywords: Windows Mixed Reality, ホログラム, holographic リモート処理, リモートレンダリング, ネットワークレンダリング, HoloLens, リモートホログラム, トラブルシューティング, ヘルプ
ms.openlocfilehash: 593b242326b83d4596d22a7e1a39ef18c26bc67a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683650"
---
# <a name="holographic-remoting-troubleshooting"></a>Holographic リモート処理のトラブルシューティング

> [!IMPORTANT]
> このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。

## <a name="spectre-mitigated-libraries-not-found"></a>Spectre の緩和されたライブラリが見つかりません。

Holographic リモート処理サンプルアプリでは、リリース構成で Spectre 軽減策 (/Qspectre) が有効になっています。

"Vccorlib .lib" を開くことができないという致命的なリンカーエラーが発生した場合は、Visual Studio ワークロードに Spectre 軽減可能なライブラリが含まれていることを確認してください。 詳細については、「https://aka.ms/Ofhn4c」を参照してください。

## <a name="speech"></a>音声

Holographic Remoting Player は診断オーバーレイをサポートしています。これは、「」と言って無効にすることで有効にすることができ ```Enable Diagnostics``` ```Disable Diagnostics``` ます。 これらの音声コマンドで問題が発生した場合は、URL としてを使用して web ブラウザーで Holographic リモート処理プレーヤーを起動することもできます ```ms-holographic-remoting:?stats``` 。

## <a name="h265-video-codec-not-available"></a>H265 video コーデックは使用できません

リモートアプリで H265 video コーデックを使用する場合は、 [HEVC ビデオ拡張機能](https://www.microsoft.com/p/hevc-video-extensions/9nmzlz57r3t7) をインストールする必要があります。 コーデックがインストールされていても使用できない問題が発生した場合は、「 [トラブルシューティング](https://docs.microsoft.com/azure/remote-rendering/resources/troubleshoot#h265-codec-not-available) ガイド」を参照してください。

## <a name="limitations"></a>制限事項

Holographic Remoting を HoloLens 2 に使用する場合、次の Api は現在サポートされて **いません** 。特に明記されて ```ERROR_NOT_SUPPORTED``` いない限り、エラーが発生します。

[Windows.Graphics.Holographic](https://docs.microsoft.com/uwp/api/windows.graphics.holographic)

* [HolographicCamera.ViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration)
  - サポートされているバージョン[2.0.18](holographic-remoting-version-history.md#v2.0.18)以降
  - 以前のバージョンでは、常にエラーが発生します。
* [HolographicCamera.IsHardwareContentProtectionEnabled](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled#Windows_Graphics_Holographic_HolographicCamera_IsHardwareContentProtectionEnabled)
* [HolographicViewConfiguration.RequestRenderTargetSize](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicviewconfiguration.requestrendertargetsize#Windows_Graphics_Holographic_HolographicViewConfiguration_RequestRenderTargetSize_Windows_Foundation_Size_)
  - バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。
  - 以前のバージョンでは、は失敗しませんが、レンダーターゲットのサイズは変更されません。
* [HolographicCameraPose.OverrideProjectionTransform](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideprojectiontransform)
* [HolographicCameraPose ビューポート](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewport)
* [HolographicCameraPose](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerapose.overrideviewtransform)
  - バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。
* [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)
  - は失敗しませんが、深度バッファーはリモート処理されません。
  - サポートされているバージョン[2.1.0](holographic-remoting-version-history.md#v2.1.0)以降
* [HolographicDisplay.TryGetViewConfiguration](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.trygetviewconfiguration)
  - HolographicViewConfigurationKind にクエリを実行すると、常にが返されます ```nullptr``` 。
  - サポートされているバージョン[2.0.18](holographic-remoting-version-history.md#v2.0.18)以降
  - 以前のバージョンでは、常にエラーが発生します。
* [HolographicSpace プレゼンテーションモニター](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicspace.createframepresentationmonitor)
* [HolographicDisplay](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay.getdefault#Windows_Graphics_Holographic_HolographicDisplay_GetDefault)
  - は、接続が確立される前に呼び出された場合にエラーを報告します。


[Windows.Perception.Spatial](https://docs.microsoft.com/uwp/api/windows.perception.spatial)

* [SpatialLocation AbsoluteAngularAcceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularacceleration)
* [SpatialLocation.AbsoluteAngularAccelerationAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularaccelerationaxisangle)
* [SpatialLocation AbsoluteAngularVelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocity)
* [SpatialLocation.AbsoluteAngularVelocityAxisAngle](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absoluteangularvelocityaxisangle)
* [SpatialLocation AbsoluteLinearAcceleration](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearacceleration)
* [SpatialLocation AbsoluteLinearVelocity](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatiallocation.absolutelinearvelocity)
* [SpatialStageFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.current)
  - バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。
  - 以前のバージョンでは、は常にを返し ```nullptr``` ます。
* [SpatialStageFrameOfReference.RequestNewStageAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialstageframeofreference.requestnewstageasync)
  - バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。
* [SpatialAnchor. RemovedByUser](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchor.removedbyuser)
* [SpatialAnchorExporter.GetDefault](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.getdefault
)
  - バージョン [2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。 
  - 以前のバージョンでは、は常にを返し ```nullptr``` ます。 
* [SpatialAnchorExporter.RequestAccessAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchorexporter.requestaccessasync
)
  - バージョン [2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。 
  - 以前のバージョンでは、非同期操作は常にで完了していました ```SpatialPerceptionAccessStatus.DeniedBySystem``` 。
* [SpatialAnchorTransferManager](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_RequestAccessAsync)
  - 非同期操作は常にで完了 ```SpatialPerceptionAccessStatus.DeniedBySystem``` します。
* [SpatialAnchorTransferManager.TryExportAnchorsAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryexportanchorsasync#Windows_Perception_Spatial_SpatialAnchorTransferManager_TryExportAnchorsAsync_Windows_Foundation_Collections_IIterable_Windows_Foundation_Collections_IKeyValuePair_System_String_Windows_Perception_Spatial_SpatialAnchor___Windows_Storage_Streams_IOutputStream_)
  - 非同期操作は常にで完了 ```false``` します。
* [SpatialAnchorTransferManager.TryImportAnchorsAsync](https://docs.microsoft.com/uwp/api/windows.perception.spatial.spatialanchortransfermanager.tryimportanchorsasync
)
  - 非同期操作は常にで完了 ```nullptr``` します。

[Windows.UI.Input.Spatial](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial)

* [SpatialInteractionSource.TryCreateHandMeshObserver](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserver#Windows_UI_Input_Spatial_SpatialInteractionSource_TryCreateHandMeshObserver)
* [SpatialInteractionSource.TryCreateHandMeshObserverAsync](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)
* [SpatialInteractionSource](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsource.controller#Windows_UI_Input_Spatial_SpatialInteractionSource_Controller)
  - バージョン[2.2.0](holographic-remoting-version-history.md#v2.2.0)以降でサポートされます。

[Windows.Perception.Spatial.Preview](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview)

* [SpatialGraphInteropPreview.CreateLocatorForNode](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.createlocatorfornode)
* [SpatialGraphInteropPreview.TryCreateFrameOfReference](https://docs.microsoft.com/uwp/api/windows.perception.spatial.preview.spatialgraphinteroppreview.trycreateframeofreference)

## <a name="see-also"></a>関連項目
* [Holographic リモート処理のバージョン履歴](holographic-remoting-version-history.md)
* [Holographic Remoting リモート アプリの作成](holographic-remoting-create-host.md)
* [カスタム Holographic リモート処理プレーヤーアプリの作成](holographic-remoting-create-player.md)
* [Holographic Remoting ソフトウェア ライセンス条項](https://docs.microsoft.com/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
