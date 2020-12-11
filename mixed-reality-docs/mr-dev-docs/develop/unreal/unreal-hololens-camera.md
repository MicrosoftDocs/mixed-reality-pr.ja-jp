---
title: Unreal での HoloLens 写真/ビデオ カメラ
description: HoloLens 写真/ビデオを Unreal で使用するためのガイド
author: hferrone
ms.author: jacksonf
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, カメラ, PV カメラ, MRC, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: c0c6e06e66e03934912906dbff5a93f9271a68b6
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609609"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="5cc17-104">Unreal での HoloLens 写真/ビデオ カメラ</span><span class="sxs-lookup"><span data-stu-id="5cc17-104">HoloLens Photo/Video Camera in Unreal</span></span>

<span data-ttu-id="5cc17-105">HoloLens のバイザーには写真と動画 (PV) 用のカメラが付いており、Mixed Reality キャプチャ (MRC) のためと、カメラ フレームのピクセル座標から Unreal 空間内のオブジェクトを見つけるための両方に、使用することができます。</span><span class="sxs-lookup"><span data-stu-id="5cc17-105">The HoloLens has a Photo/Video (PV) Camera on the visor that can be used for both Mixed Reality Capture (MRC) and locating objects in Unreal world space from pixel coordinates in the camera frame.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5cc17-106">Holographic Remoting では PV カメラはサポートされていませんが、お使いの PC に搭載のウェブ カメラを使用して、HoloLens PV カメラの機能をシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="5cc17-106">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

[!INCLUDE[](includes/tabs-pv-camera.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="5cc17-107">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="5cc17-107">Next Development Checkpoint</span></span>

<span data-ttu-id="5cc17-108">用意されている Unreal 開発体験に従っている場合、Mixed Reality プラットフォームの機能と API を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="5cc17-108">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="5cc17-109">ここから、次のトピックを続けることができます。</span><span class="sxs-lookup"><span data-stu-id="5cc17-109">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5cc17-110">QR コード</span><span class="sxs-lookup"><span data-stu-id="5cc17-110">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="5cc17-111">または、デバイスまたはエミュレーターへのアプリの配置操作に直接移動します。</span><span class="sxs-lookup"><span data-stu-id="5cc17-111">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5cc17-112">デバイスへの配置</span><span class="sxs-lookup"><span data-stu-id="5cc17-112">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="5cc17-113">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#3-platform-capabilities-and-apis)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="5cc17-113">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="5cc17-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5cc17-114">See also</span></span>
* [<span data-ttu-id="5cc17-115">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="5cc17-115">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="5cc17-116">開発者向け複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="5cc17-116">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
