---
title: OpenXR パフォーマンス
description: OpenXR アプリケーションの GPU パフォーマンスをデバッグします。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア、パフォーマンス、最適化、GPU デバッグ、RenderDoc、PIX
ms.openlocfilehash: 717dc2d534773bd28f5ad2d5c3720bf4177a1480
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683831"
---
# <a name="openxr-performance"></a>OpenXR パフォーマンス

HoloLens 2 では、さまざまな方法でコンポジションデータを送信 `xrEndFrame` できます。これにより、パフォーマンスが大幅に低下する後処理が行われます。
パフォーマンス penalities を回避するには、次の特性を持つ[単一 `XrCompositionProjectionLayer` のを送信](openxr-best-practices.md#use-a-single-projection-layer)します。
* [テクスチャ配列のスワップチェーンを使用する](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [プライマリ色のスワップチェーン形式を使用する](openxr-best-practices.md#select-a-swapchain-format)
* [推奨ビューディメンションを使用する](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* フラグを設定しない `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`
* を 0.0 f に、を `XrCompositionLayerDepthInfoKHR` `minDepth` `maxDepth` 1.0 f に設定します

その他の考慮事項により、パフォーマンスが向上します。
* [16ビット深度形式を使用する](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [インスタンス化描画呼び出しを作成する](openxr-best-practices.md#render-with-texture-array-and-vprt)
