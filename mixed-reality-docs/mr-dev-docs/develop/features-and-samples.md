---
title: サンプルとおすすめアプリ
description: HoloLens 向けに利用可能なすべての Microsoft サンプルと Mixed Reality 機能アプリについての最新情報を説明します。
author: hferrone
ms.author: jemccull
ms.date: 12/3/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, 学習, サンプル, MRTK, Research モード, HoloLens 2, QR コード, WebRTC, Mixed Reality キャプチャ, Holographic Remoting, UX Tools
ms.localizationpriority: high
ms.openlocfilehash: 78cfc726bdffdb461a83bd1e9805d8f0e64b0f01
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583195"
---
# <a name="samples-and-feature-apps"></a>サンプルとおすすめアプリ

![HoloLens を装着し、手の動きでホログラムを操作しているユーザーの画像](unreal/images/unreal-developer.jpg)

すべての開発作業は、他の開発者が構築に成功したものを振り返って見ることから始まります。Mixed Reality の場合も同じです。 現在、すべてのチュートリアルとサンプル アプリは Unity か Unreal で構築されています。 他のエンジンおよびプラットフォーム向けのコンテンツを開発する場合は、目次にある関連する見出しの下で確認できます。

## <a name="sample-apps"></a>サンプル アプリ

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a>機能のサンプル

以下に示す機能のサンプルは、ドキュメントに記載されている特定の実装に対応しており、さまざまな開発プラットフォームとハードウェア デバイスがカバーされています。

### <a name="research-mode"></a>Research モード

Research モードは、デバイス上の主要センサーへのアクセスを提供するために、第 1 世代の HoloLens で導入されました。特に、配置を意図されていない研究アプリケーションを対象としています。 次のサンプル アプリケーションは、Research モードのストリームにアクセスして記録し、[組み込みのものと外部のもの](/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)を使用する例です。

<br>

| 参照記事 | サンプル アプリケーション |
| --- | --- |
| [Research モード](platform-capabilities-and-apis/research-mode.md) | [HoloLens (第 1 世代)](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [Research モード](platform-capabilities-and-apis/research-mode.md) | [HoloLens 2](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a>QR コード

HoloLens 2 を使用すると、ヘッドセット周辺の環境内の QR コードを検出し、各コードの実際の場所で座標系を確立することができます。

<br>

| 参照記事 | サンプル |
| --- | --- |
| [QR コード](platform-capabilities-and-apis/qr-code-tracking.md) | [Unity での QR コードの追跡](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a>WebRTC

MixedReality-WebRTC プロジェクトは、Mixed Reality アプリ開発者がピアツーピア オーディオ、ビデオ、データ リアルタイム通信をアプリケーションに統合するのに役立つコンポーネントのコレクションです。 WebRTC コンポーネントは、ほとんどの最新 Web ブラウザーでサポートされているリアルタイム通信 (RTC) 用の WebRTC プロトコルに基づいています。

<br>

| 参照記事 | サンプル |
| --- | --- |
| [WebRTC](https://microsoft.github.io/MixedReality-WebRTC) | [WebRTC サンプル アプリ](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a>ホログラフィック Mixed Reality キャプチャ

Mixed Reality キャプチャ (MRC) を使用すると、現実とデジタルの世界を写真または動画として合成し、自分が見ているものを他のユーザーとリアルタイムで共有する、一人称視点のエクスペリエンスがキャプチャされます。

<br>

| 参照記事 | サンプル |
| --- | --- |
| [Mixed Reality キャプチャ](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [Mixed Reality キャプチャのサンプル](/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a>Holographic Remoting

Holographic Remoting Player は、Holographic Remoting をサポートする PC アプリやゲームに接続するコンパニオン アプリです。 Holographic Remoting は、Wi-Fi 接続を使用して PC から Microsoft HoloLens にホログラフィック コンテンツをリアルタイムにストリーミングする機能を備え、HoloLens (第 1 世代) と HoloLens 2 でサポートされています。

<br>

| 参照記事 | サンプル |
| --- | --- |
| [Holographic Remoting](platform-capabilities-and-apis/holographic-remoting-player.md) | [Holographic Remoting のサンプル](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |