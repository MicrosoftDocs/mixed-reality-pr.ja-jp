---
title: DirectX での共有された空間アンカー
description: DirectX アプリケーションでローカル空間アンカーと Azure 空間アンカーを共有することで、2つの HoloLens デバイスを同期する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: HoloLens, 同期, 空間アンカー, 転送, マルチプレイヤー, ビュー, シナリオ, チュートリアル, サンプルコード, Azure, Azure 空間アンカー, ASA
ms.openlocfilehash: cf823809d1f6b9bf4bc44a6aa1e8f0e16fd76a16
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583105"
---
# <a name="shared-experiences-in-directx"></a>DirectX での共有エクスペリエンス

> [!NOTE]
> この記事は、従来の WinRT ネイティブ Api に関連しています。  新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](../native/openxr-getting-started.md)** を使用することをお勧めします。

共有エクスペリエンスとは、1つの HoloLens、iOS、または Android デバイスを持つ複数のユーザーが、同じホログラムをまとめて表示し、対話することです。 ホログラムは空間アンカー共有を使用して、空間の固定ポイントに配置されます。

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、持続性のあるクラウドベースの空間アンカーを作成できます。これにより、アプリは複数の HoloLens、IOS、Android デバイスで検索できます。  複数のデバイスで共通の空間アンカーを共有することにより、各ユーザーは、同じ物理的な場所でそのアンカーを基準としてレンダリングされたコンテンツを表示できます。  これにより、リアルタイム共有エクスペリエンスを実現できます。

<a href="/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、HoloLens、iOS、および Android デバイス間での非同期ホログラム永続化を行うこともできます。  持続性のあるクラウド空間アンカーを共有することにより、複数のデバイスが同時に存在しない場合でも、同じ永続化されたホログラムを時間の経過とともに観察できます。

HoloLens アプリでの共有エクスペリエンスの構築を開始するには、5分間の <a href="/azure/spatial-anchors/quickstarts/get-started-hololens" target="_blank">Azure 空間アンカー HoloLens クイックスタート</a>をお試しください。

Azure 空間アンカーを使用して実行すると、 <a href="/azure/spatial-anchors/concepts/create-locate-anchors-cpp-winrt" target="_blank">HoloLens でアンカーを作成して検索</a>できます。  チュートリアルは <a href="/azure/spatial-anchors/create-locate-anchors-overview" target="_blank">Android と iOS</a> でも使用できます。これにより、すべてのデバイスで同じアンカーを共有できるようになります。

## <a name="local-anchor-transfers"></a>ローカルアンカー転送

Azure 空間アンカーを使用できない場合、 [ローカルアンカー転送](../../out-of-scope/local-anchor-transfers-in-directx.md) を使用すると、1つの hololens デバイスで2つ目の hololens デバイスによってインポートされるアンカーをエクスポートできます。  このアプローチでは、Azure 空間アンカーよりも堅牢なアンカーの再呼び出しが可能であり、iOS デバイスと Android デバイスはこの方法ではサポートされていません。

## <a name="see-also"></a>関連項目

* [複合現実での共有エクスペリエンス](shared-experiences-in-mixed-reality.md)
* <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="/cpp/api/spatial-anchors/winrt/" target="_blank">HoloLens 用 Azure 空間アンカー SDK</a>