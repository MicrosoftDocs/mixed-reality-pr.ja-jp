---
title: Unity での共有エクスペリエンス
description: Unity アプリケーションの複数のユーザー間で同じホログラムを共有します。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共有、アンカー、WorldAnchor、MR 共有250、WorldAnchorTransferBatch、SpatialPerception、Azure、Azure 空間アンカー、ASA、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実ヘッドセット
ms.openlocfilehash: 46588f84c39a48e22147d0fc246ceb8d5ee7c47d
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010092"
---
# <a name="shared-experiences-in-unity"></a>Unity での共有エクスペリエンス

共有エクスペリエンスを使用すると、複数のユーザーが独自の HoloLens、iOS、または Android デバイスを使用して、同じホログラムをまとめて表示し、操作できます。 ホログラムは、空間アンカーを共有することにより、空間内の固定ポイントに配置されます。

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>は、持続性のあるクラウドベースの空間アンカーを作成します。これにより、アプリは複数の HoloLens、IOS、Android デバイスで検索できます。  複数のデバイスで共通の空間アンカーを共有することにより、各ユーザーは、同じ物理的な場所でそのアンカーを基準としてレンダリングされたコンテンツを表示できます。 

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、HoloLens、iOS、および Android デバイス間での非同期ホログラム永続化を行うこともできます。  持続性のあるクラウド空間アンカーを共有することにより、複数のデバイスが同時に存在しない場合でも、同じ永続化されたホログラムを時間の経過とともに観察できます。

Unity で共有エクスペリエンスの構築を開始するには、5分間の <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間アンカー unity クイックスタート</a>をお試しください。

Azure 空間アンカーを設定したら、 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity でアンカーを作成および検索</a>できます。

## <a name="local-anchor-transfers"></a>ローカルアンカー転送

Azure 空間アンカーを使用できない場合、 [ローカルアンカー転送](../../out-of-scope/local-anchor-transfers-in-unity.md) を使用すると、1つの hololens デバイスでアンカーをエクスポートして、2つ目の hololens がインポートできるようにすることができます。  このアプローチは、iOS および Android デバイスではサポートされておらず、Azure 空間アンカーよりも堅牢なアンカーのリコールを提供します。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

これまでに説明した Unity 開発の取り組みに従っている場合は、Mixed Reality プラットフォームの機能と Api を試してみることになります。 ここから、次のセクションに進むことができます。

> [!div class="nextstepaction"]
> [場所を特定できるカメラ](locatable-camera-in-unity.md)

または、デバイスまたはエミュレーターへのアプリの配置操作に直接移動します。

> [!div class="nextstepaction"]
> [HoloLens または Windows Mixed Reality イマーシブヘッドセットへのデプロイ](../platform-capabilities-and-apis/using-visual-studio.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#3-platform-capabilities-and-apis)に戻ることができます。

## <a name="see-also"></a>関連項目
* [複合現実での共有エクスペリエンス](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空間アンカー SDK for Unity</a>
