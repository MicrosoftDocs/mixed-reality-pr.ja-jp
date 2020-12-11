---
title: サンプルとおすすめアプリ
description: HoloLens で使用可能な機能のサンプルを参照してください。
author: hferrone
ms.author: jemccull
ms.date: 12/3/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, 学習, サンプル, MRTK, Research モード, HoloLens 2, QR コード, WebRTC, Mixed Reality キャプチャ, Holographic Remoting, UX Tools
ms.localizationpriority: high
ms.openlocfilehash: 2624949dd21b4c8e14ed45f152d41900b5f91faf
ms.sourcegitcommit: 924f8c1ceb93c378f800cf88d82944cf80f092bc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96615553"
---
# <a name="samples-and-feature-apps"></a><span data-ttu-id="5a715-104">サンプルとおすすめアプリ</span><span class="sxs-lookup"><span data-stu-id="5a715-104">Samples and feature apps</span></span>

![HoloLens を装着し、手の動きでホログラムを操作しているユーザーの画像](unreal/images/unreal-developer.jpg)

<span data-ttu-id="5a715-106">すべての開発作業は、他の開発者が構築に成功したものを振り返って見ることから始まります。Mixed Reality の場合も同じです。</span><span class="sxs-lookup"><span data-stu-id="5a715-106">Every development journey starts with a look back at what other developers have successfully built - mixed reality is no different.</span></span> <span data-ttu-id="5a715-107">現在、すべてのチュートリアルとサンプル アプリは Unity か Unreal で構築されています。</span><span class="sxs-lookup"><span data-stu-id="5a715-107">Currently, all of our tutorials and sample apps are built in Unity or Unreal.</span></span> <span data-ttu-id="5a715-108">他のエンジンおよびプラットフォーム向けのコンテンツを開発する場合は、目次にある関連する見出しの下で確認できます。</span><span class="sxs-lookup"><span data-stu-id="5a715-108">As we develop content for other engines and platforms, you'll find them under the relevant heading in the Table of Contents.</span></span>

## <a name="sample-apps"></a><span data-ttu-id="5a715-109">サンプル アプリ</span><span class="sxs-lookup"><span data-stu-id="5a715-109">Sample apps</span></span>

[!INCLUDE[](includes/tabs-samples.md)]

## <a name="feature-samples"></a><span data-ttu-id="5a715-110">機能のサンプル</span><span class="sxs-lookup"><span data-stu-id="5a715-110">Feature samples</span></span>

<span data-ttu-id="5a715-111">以下に示す機能のサンプルは、ドキュメントに記載されている特定の実装に対応しており、さまざまな開発プラットフォームとハードウェア デバイスがカバーされています。</span><span class="sxs-lookup"><span data-stu-id="5a715-111">The feature samples listed below correspond to specific implementations that are covered in our documentation and covers a range of development platforms and hardware devices.</span></span>

### <a name="research-mode"></a><span data-ttu-id="5a715-112">Research モード</span><span class="sxs-lookup"><span data-stu-id="5a715-112">Research Mode</span></span>

<span data-ttu-id="5a715-113">Research モードは、デバイス上の主要センサーへのアクセスを提供するために、第 1 世代の HoloLens で導入されました。特に、配置を意図されていない研究アプリケーションを対象としています。</span><span class="sxs-lookup"><span data-stu-id="5a715-113">Research Mode was introduced in the 1st Generation HoloLens to give access to key sensors on the device, specifically for research applications that are not intended for deployment.</span></span> <span data-ttu-id="5a715-114">次のサンプル アプリケーションは、Research モードのストリームにアクセスして記録し、[組み込みのものと外部のもの](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)を使用する例です。</span><span class="sxs-lookup"><span data-stu-id="5a715-114">The sample applications below are examples for accessing and recording Research Mode streams and using the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world).</span></span>

<br>

| <span data-ttu-id="5a715-115">参照記事</span><span class="sxs-lookup"><span data-stu-id="5a715-115">Reference article</span></span> | <span data-ttu-id="5a715-116">サンプル アプリケーション</span><span class="sxs-lookup"><span data-stu-id="5a715-116">Sample application</span></span> |
| --- | --- |
| [<span data-ttu-id="5a715-117">Research モード</span><span class="sxs-lookup"><span data-stu-id="5a715-117">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="5a715-118">HoloLens (第 1 世代)</span><span class="sxs-lookup"><span data-stu-id="5a715-118">HoloLens (1st gen)</span></span>](https://github.com/microsoft/HoloLensForCV/tree/master/Samples) |
| [<span data-ttu-id="5a715-119">Research モード</span><span class="sxs-lookup"><span data-stu-id="5a715-119">Research Mode</span></span>](platform-capabilities-and-apis/research-mode.md) | [<span data-ttu-id="5a715-120">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="5a715-120">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV/tree/main/Samples) |

### <a name="qr-codes"></a><span data-ttu-id="5a715-121">QR コード</span><span class="sxs-lookup"><span data-stu-id="5a715-121">QR codes</span></span>

<span data-ttu-id="5a715-122">HoloLens 2 を使用すると、ヘッドセット周辺の環境内の QR コードを検出し、各コードの実際の場所で座標系を確立することができます。</span><span class="sxs-lookup"><span data-stu-id="5a715-122">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span>

<br>

| <span data-ttu-id="5a715-123">参照記事</span><span class="sxs-lookup"><span data-stu-id="5a715-123">Reference article</span></span> | <span data-ttu-id="5a715-124">サンプル</span><span class="sxs-lookup"><span data-stu-id="5a715-124">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="5a715-125">QR コード</span><span class="sxs-lookup"><span data-stu-id="5a715-125">QR codes</span></span>](platform-capabilities-and-apis/qr-code-tracking.md) | [<span data-ttu-id="5a715-126">Unity での QR コードの追跡</span><span class="sxs-lookup"><span data-stu-id="5a715-126">QR code tracking in Unity</span></span>](https://github.com/chgatla-microsoft/QRTracking/tree/master/SampleQRCodes) |

### <a name="webrtc"></a><span data-ttu-id="5a715-127">WebRTC</span><span class="sxs-lookup"><span data-stu-id="5a715-127">WebRTC</span></span>

<span data-ttu-id="5a715-128">MixedReality-WebRTC プロジェクトは、Mixed Reality アプリ開発者がピアツーピア オーディオ、ビデオ、データ リアルタイム通信をアプリケーションに統合するのに役立つコンポーネントのコレクションです。 WebRTC コンポーネントは、ほとんどの最新 Web ブラウザーでサポートされているリアルタイム通信 (RTC) 用の WebRTC プロトコルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="5a715-128">The MixedReality-WebRTC project is a collection of components to help mixed reality app developers to integrate peer-to-peer audio, video, and data real-time communication into their applications WebRTC components are based on the WebRTC protocol for Real-Time Communication (RTC), which is supported by most modern web browsers.</span></span>

<br>

| <span data-ttu-id="5a715-129">参照記事</span><span class="sxs-lookup"><span data-stu-id="5a715-129">Reference article</span></span> | <span data-ttu-id="5a715-130">サンプル</span><span class="sxs-lookup"><span data-stu-id="5a715-130">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="5a715-131">WebRTC</span><span class="sxs-lookup"><span data-stu-id="5a715-131">WebRTC</span></span>](https://microsoft.github.io/MixedReality-WebRTC) | [<span data-ttu-id="5a715-132">WebRTC サンプル アプリ</span><span class="sxs-lookup"><span data-stu-id="5a715-132">WebRTC sample apps</span></span>](https://github.com/microsoft/MixedReality-WebRTC/tree/master/examples) |

### <a name="holographic-mixed-reality-capture"></a><span data-ttu-id="5a715-133">ホログラフィック Mixed Reality キャプチャ</span><span class="sxs-lookup"><span data-stu-id="5a715-133">Holographic Mixed Reality Capture</span></span>

<span data-ttu-id="5a715-134">Mixed Reality キャプチャ (MRC) を使用すると、現実とデジタルの世界を写真または動画として合成し、自分が見ているものを他のユーザーとリアルタイムで共有する、一人称視点のエクスペリエンスがキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="5a715-134">Mixed reality capture (MRC) captures the first-person experience of mixing real and digital worlds as a photo or video, sharing what you see with others in real-time.</span></span>

<br>

| <span data-ttu-id="5a715-135">参照記事</span><span class="sxs-lookup"><span data-stu-id="5a715-135">Reference article</span></span> | <span data-ttu-id="5a715-136">サンプル</span><span class="sxs-lookup"><span data-stu-id="5a715-136">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="5a715-137">Mixed Reality キャプチャ</span><span class="sxs-lookup"><span data-stu-id="5a715-137">Mixed Reality Capture</span></span>](platform-capabilities-and-apis/mixed-reality-capture-for-developers.md) | [<span data-ttu-id="5a715-138">Mixed Reality キャプチャのサンプル</span><span class="sxs-lookup"><span data-stu-id="5a715-138">Mixed Reality Capture samples</span></span>](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/holographicmixedrealitycapture/) |

### <a name="holographic-remoting"></a><span data-ttu-id="5a715-139">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="5a715-139">Holographic Remoting</span></span>

<span data-ttu-id="5a715-140">Holographic Remoting Player は、Holographic Remoting をサポートする PC アプリやゲームに接続するコンパニオン アプリです。</span><span class="sxs-lookup"><span data-stu-id="5a715-140">The Holographic Remoting Player is a companion app that connects to PC apps and games that support Holographic Remoting.</span></span> <span data-ttu-id="5a715-141">Holographic Remoting は、Wi-Fi 接続を使用して PC から Microsoft HoloLens にホログラフィック コンテンツをリアルタイムにストリーミングする機能を備え、HoloLens (第 1 世代) と HoloLens 2 でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5a715-141">Holographic Remoting streams holographic content from a PC to your Microsoft HoloLens in real-time, using a Wi-Fi connection, and is supported on HoloLens (1st gen) and HoloLens 2.</span></span>

<br>

| <span data-ttu-id="5a715-142">参照記事</span><span class="sxs-lookup"><span data-stu-id="5a715-142">Reference article</span></span> | <span data-ttu-id="5a715-143">サンプル</span><span class="sxs-lookup"><span data-stu-id="5a715-143">Sample</span></span> |
| --- | --- |
| [<span data-ttu-id="5a715-144">Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="5a715-144">Holographic Remoting</span></span>](platform-capabilities-and-apis/holographic-remoting-player.md) | [<span data-ttu-id="5a715-145">Holographic Remoting のサンプル</span><span class="sxs-lookup"><span data-stu-id="5a715-145">Holographic Remoting samples</span></span>](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples) |