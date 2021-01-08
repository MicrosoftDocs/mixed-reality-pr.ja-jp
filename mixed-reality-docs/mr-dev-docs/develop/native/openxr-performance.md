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
# <a name="openxr-performance"></a>OpenXR パフォーマンス

HoloLens 2 では、を使用してコンポジションデータを送信する方法がいくつかあります `xrEndFrame` 。これにより、後処理が発生し、パフォーマンスが低下する可能性があります。

パフォーマンスが低下しないようにするには、次の特性を持つを[1 つ `XrCompositionProjectionLayer` 送信](openxr-best-practices.md#use-a-single-projection-layer)します。

* [テクスチャ配列のスワップチェーンを使用する](openxr-best-practices.md#render-with-texture-array-and-vprt)
* [プライマリ色のスワップチェーン形式を使用する](openxr-best-practices.md#select-a-swapchain-format)
* [推奨ビューディメンションを使用する](openxr-best-practices.md#render-with-recommended-rendering-parameters-and-frame-timing)
* フラグを設定しない `XR_COMPOSITION_LAYER_UNPREMULTIPLIED_ALPHA_BIT`
* を 0.0 f に、を `XrCompositionLayerDepthInfoKHR` `minDepth` `maxDepth` 1.0 f に設定します

パフォーマンス向上のために、次の点を考慮してください。

* [16ビット深度形式の使用](openxr-best-practices.md#choose-a-reasonable-depth-range)
* [インスタンス化描画呼び出しの作成](openxr-best-practices.md#render-with-texture-array-and-vprt)
