---
title: Unreal での HoloLens 写真/ビデオ カメラ
description: Unreal で Mixed Reality キャプチャとオブジェクトの場に HoloLens の写真およびビデオ カメラを使用する方法について説明します。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, カメラ, PV カメラ, MRC, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 15eba0c992d6d3d8895314f1a6128ace18c02483
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010062"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="35a83-104">Unreal での HoloLens 写真/ビデオ カメラ</span><span class="sxs-lookup"><span data-stu-id="35a83-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="35a83-105">HoloLens のバイザーには写真と動画 (PV) 用のカメラが付いており、Mixed Reality キャプチャ (MRC) のためと、カメラ フレームのピクセル座標から Unreal 空間内のオブジェクトを見つけるための両方に、使用することができます。</span><span class="sxs-lookup"><span data-stu-id="35a83-105">The HoloLens has a Photo/Video (PV) Camera on the visor that can be used for both Mixed Reality Capture (MRC) and locating objects in Unreal world space from pixel coordinates in the camera frame.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35a83-106">Holographic Remoting では PV カメラはサポートされていませんが、お使いの PC に搭載のウェブ カメラを使用して、HoloLens PV カメラの機能をシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="35a83-106">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

[!INCLUDE[](includes/tabs-pv-camera.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="35a83-107">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="35a83-107">Next Development Checkpoint</span></span>

<span data-ttu-id="35a83-108">用意されている Unreal 開発体験に従っている場合、Mixed Reality プラットフォームの機能と API を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="35a83-108">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="35a83-109">ここから、次のトピックを続けることができます。</span><span class="sxs-lookup"><span data-stu-id="35a83-109">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="35a83-110">QR コード</span><span class="sxs-lookup"><span data-stu-id="35a83-110">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="35a83-111">または、デバイスまたはエミュレーターへのアプリの配置操作に直接移動します。</span><span class="sxs-lookup"><span data-stu-id="35a83-111">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="35a83-112">デバイスへの配置</span><span class="sxs-lookup"><span data-stu-id="35a83-112">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="35a83-113">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#3-platform-capabilities-and-apis)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="35a83-113">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="35a83-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="35a83-114">See also</span></span>

* [<span data-ttu-id="35a83-115">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="35a83-115">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="35a83-116">開発者向け複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="35a83-116">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
