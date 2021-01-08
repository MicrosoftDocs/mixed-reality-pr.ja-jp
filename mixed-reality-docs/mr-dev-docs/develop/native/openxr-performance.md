---
title: OpenXR パフォーマンス
description: OpenXR mixed reality アプリケーションの GPU パフォーマンスをデバッグする方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア、パフォーマンス、最適化、GPU デバッグ、RenderDoc、PIX
ms.openlocfilehash: 158bd2eef8f38f16a1fb5299d64335aca33a3b7f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006762"
---
# <a name="openxr-performance"></a><span data-ttu-id="2e1ae-104">OpenXR パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="2e1ae-104">OpenXR performance</span></span>

<span data-ttu-id="2e1ae-105">HoloLens 2 では、を使用してコンポジションデータを送信する方法がいくつかあります `xrEndFrame` 。これにより、後処理が発生し、パフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2e1ae-105">On HoloLens 2, there are a number of ways to submit composition data through `xrEndFrame`, which can result in post-processing and noticeable performance penalties.</span></span>

<span data-ttu-id="2e1ae-106">パフォーマンスが低下しないようにするには、次の特性を持つを[1 つ `XrCompositionProjectionLayer` 送信](openxr-best-practices.md#use-a-single-projection-layer)します。</span><span class="sxs-lookup"><span data-stu-id="2e1ae-106">To avoid poor performance, [submit a single `XrCompositionProjectionLayer`](openxr-best-practices.md#use-a-single-projection-layer) with the following characteristics:</span></span>

* [<span data-ttu-id="2e1ae-107">テクスチャ配列のスワップチェーンを使用する</span><span class="sxs-lookup"><span data-stu-id="2e1ae-107">Use a texture array swapchain</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [<span data-ttu-id="2e1ae-108">プライマリ色のスワップチェーン形式を使用する</span><span class="sxs-lookup"><span data-stu-id="2e1ae-108">Use the primary color swapchain format</span></span>](openxr-best-practices.md#select-a-swapchain-format)
* [<span data-ttu-id="2e1ae-109">推奨ビューディメンションを使用する</span><span class="sxs-lookup"><span data-stu-id="2e1ae-109">Use the recommended view dimensions</span></span>](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* <span data-ttu-id="2e1ae-110">フラグを設定しない `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`</span><span class="sxs-lookup"><span data-stu-id="2e1ae-110">Don't set the `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT` flag</span></span>
* <span data-ttu-id="2e1ae-111">を 0.0 f に、を `XrCompositionLayerDepthInfoKHR` `minDepth` `maxDepth` 1.0 f に設定します</span><span class="sxs-lookup"><span data-stu-id="2e1ae-111">Set the `XrCompositionLayerDepthInfoKHR` `minDepth` to 0.0f and `maxDepth` to 1.0f</span></span>

<span data-ttu-id="2e1ae-112">パフォーマンス向上のために、次の点を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="2e1ae-112">For better performance, consider:</span></span>

* [<span data-ttu-id="2e1ae-113">16ビット深度形式の使用</span><span class="sxs-lookup"><span data-stu-id="2e1ae-113">Using the 16-bit depth format</span></span>](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [<span data-ttu-id="2e1ae-114">インスタンス化描画呼び出しの作成</span><span class="sxs-lookup"><span data-stu-id="2e1ae-114">Making instanced draw calls</span></span>](openxr-best-practices.md#render-with-texture-array-and-vprt)
