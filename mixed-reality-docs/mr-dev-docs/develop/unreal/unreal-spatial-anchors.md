---
title: Unreal でのローカル空間アンカー
description: Unreal で空間アンカーを使用するためのガイド
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, 空間アンカー, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 3ce83160f745fc48f082776caa3cfa87d23a1844
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678831"
---
# <a name="local-spatial-anchors-in-unreal"></a>Unreal でのローカル空間アンカー

## <a name="overview"></a>概要

空間アンカーは、アプリケーション セッション間で現実世界の空間にホログラムを保存するために使用されます。 これらは、Unreal では **ARPin** として示され、今後のセッションで読み込まれるように HoloLens のアンカー ストアに保存されます。 ローカル アンカーは、インターネット接続がない場合のフォールバックとして理想的です。

> [!IMPORTANT]
> ローカル アンカーはデバイスに格納されますが、Azure 空間アンカーはクラウドに格納されます。 アンカーを格納するために Azure クラウド サービスを使用することをご検討の場合は、[Azure Spatial Anchors](unreal-azure-spatial-anchors.md) を統合する方法について説明したドキュメントを参照してください。 また、ローカル アンカーと Azure のアンカーは、競合することなく同じプロジェクトで使用できます。

## <a name="checking-the-anchor-store"></a>アンカー ストアの確認

アンカーを保存または読み込む前に、アンカー ストアの準備ができているかどうか確認する必要があります。  アンカー ストアの準備が整う前に、いずれかの HoloLens アンカー関数を呼び出すと、失敗します。  

![空間アンカー ストア準備完了](images/unreal-spatialanchors-store-ready.PNG)

## <a name="saving-anchors"></a>アンカーの保存

アプリケーションにコンポーネントがあり、それをワールドに固定する必要がある場合は、次のシーケンスを使用してアンカー ストアに保存できます。 

![空間アンカーの保存](images/unreal-spatialanchors-save.PNG)

次のように分類されます。
1. 既知の場所でアクターを生成します。
2. その場所とアクターのクラスに基づく名前を使用して、**ARPin** を作成します。 
3. アクターを **ARPin** に追加し、そのピンを HoloLens アンカー ストアに保存します。  
    * 選択するアンカー名は一意である必要があります。この例では現在のタイムスタンプを使用します。 

4. アンカーがアンカー ストアに正常に保存された場合、HoloLens デバイス ポータルの **[システム] > [Map manager]\(マップ マネージャー\) > [Anchor Files Saved On Device]\(デバイスに保存されたアンカー ファイル\)** でそのアンカーを調べることができます。 

## <a name="loading-anchors"></a>アンカーの読み込み

アプリケーションが起動すると、次のブループリントを使用して、コンポーネントをアンカー位置に復元できます。

![空間アンカーの読み込み](images/unreal-spatialanchors-load.PNG)

次のように分類されます。
1. アンカー ストア内のすべてのアンカーを反復処理します。 
2. ID でアクターを生成します。
3. そのアクターをアンカー ストアから **ARPin** にピン留めします。  

    * アンカーは、保存された位置に基づいてワールドにホログラムを再配置する必要があるため、ID に対してアクターを生成することが重要です。 ここで追加した変換によってアンカーにオフセットが追加されます。 

アンカーの保存された名前によって異なるアクターを生成できるように、アンカー ID も照会されます。 

## <a name="removing-anchors"></a>アンカーの削除 

アンカーが終了したら、**Remove ARPin from WMRAnchor Store** および **Remove All ARPins from WMRAnchor Store** コンポーネントを使用して個々のアンカーまたはアンカー ストア全体を削除することができます。

![空間アンカーの削除](images/unreal-spatialanchors-remove.PNG)

> [!NOTE]
> Spatial Anchors はまだベータ版であるため、最新の情報と機能を確認してください。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。 ここから、次の構成要素に進むことができます。 

> [!div class="nextstepaction"]
> [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [HoloLens カメラ](unreal-hololens-camera.md)

いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目
* [Azure Spatial Anchors](unreal-azure-spatial-anchors.md)
* [空間アンカー](../../design/spatial-anchors.md)
* [座標系](../../design/coordinate-systems.md)
