---
title: Unity での共有エクスペリエンス
description: Unity アプリケーションの複数のユーザー間で同じホログラムを共有します。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 共有、アンカー、WorldAnchor、MR 共有250、WorldAnchorTransferBatch、SpatialPerception、Azure、Azure 空間アンカー、ASA
ms.openlocfilehash: 324aecdc89b4996625ce93514616c32d2d064ffa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684807"
---
# <a name="shared-experiences-in-unity"></a>Unity での共有エクスペリエンス

共有エクスペリエンスとは、各ユーザーが独自の HoloLens、iOS、または Android デバイスを持つ複数のユーザーをまとめて表示し、空間内の固定ポイントに配置されている同じホログラムと対話することです。 これは、空間アンカーの共有によって実現されます。

## <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、持続性のあるクラウドベースの空間アンカーを作成できます。これにより、アプリは複数の HoloLens、IOS、Android デバイスで検索できます。  複数のデバイスで共通の空間アンカーを共有することにより、各ユーザーは、同じ物理的な場所でそのアンカーを基準としてレンダリングされたコンテンツを表示できます。  これにより、リアルタイム共有エクスペリエンスを実現できます。

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して HoloLens、iOS および Android デバイスの間で非同期ホログラム永続化を行うこともできます。  永続的なクラウド空間アンカーを共有すると、永続化した同じホログラムを長時間にわたって複数のデバイスに表示できます。これらのデバイスが同じ時間と場所に居合わせていなくても問題ありません。

Unity で共有エクスペリエンスの構築を開始するには、5分間の <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間アンカー unity クイックスタート</a>をお試しください。

Azure 空間アンカーを使用して実行した後は、 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity でアンカーを作成して見つける</a>ことができます。

## <a name="local-anchor-transfers"></a>ローカルアンカー転送

Azure 空間アンカーを使用できない場合、 [ローカルアンカー転送](../../out-of-scope/local-anchor-transfers-in-unity.md) では、1つの hololens デバイスが2つ目の hololens デバイスによってインポートされるアンカーをエクスポートできるようにします。  このアプローチでは、Azure 空間アンカーよりも堅牢なアンカーの再呼び出しが可能であり、iOS デバイスと Android デバイスはこの方法ではサポートされていないことに注意してください。

## <a name="next-development-checkpoint"></a>次回の開発チェックポイント

ここまでに説明した Unity 開発チェックポイントの旅に従っている場合は、Mixed Reality プラットフォームの機能と Api の調査が途中で終了しています。 ここから、次のトピックに進むことができます。

> [!div class="nextstepaction"]
> [場所を特定できるカメラ](locatable-camera-in-unity.md)

または、デバイスまたはエミュレーターへのアプリのデプロイに直接移動します。

> [!div class="nextstepaction"]
> [HoloLens または Windows Mixed Reality イマーシブヘッドセットへのデプロイ](../platform-capabilities-and-apis/using-visual-studio.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#3-platform-capabilities-and-apis) に戻ることができます。

## <a name="see-also"></a>関連項目
* [複合現実での共有エクスペリエンス](../platform-capabilities-and-apis/shared-experiences-in-mixed-reality.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空間アンカー SDK for Unity</a>
