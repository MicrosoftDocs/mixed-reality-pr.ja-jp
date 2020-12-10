---
title: Unity の永続化
description: 永続化を使用すると、ユーザーが好きな場所に個々のホログラムをピン留めし、アプリの多くの用途で後から検索することができます。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens、永続化、Unity、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実のヘッドセット
ms.openlocfilehash: d74f9c0a118c1886037c564073742ebedc7d0146
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010443"
---
# <a name="persistence-in-unity"></a>Unity の永続化

**名前空間:** *UNITYENGINE. XR*<br>
**クラス:** *WorldAnchorStore*

WorldAnchorStore は、ホログラムがアプリケーションのインスタンス間で特定の実際の位置に置かれる holographic エクスペリエンスを作成するための鍵です。 ユーザーは、必要に応じて個々のホログラムをピン留めし、アプリの多くの用途において、後で同じ場所でそれらを見つけることができます。

## <a name="how-to-persist-holograms-across-sessions"></a>セッション間でホログラムを永続化する方法

WorldAnchorStore を使用すると、WorldAnchor の場所をセッション間で永続化することができます。 セッション間でホログラムを永続化するには、特定のワールドアンカーを使用するユーザーオブジェクトを個別に追跡する必要があります。 多くの場合、ワールドアンカーを使用して作成オブジェクトのルートを作成し、ローカル位置のオフセットを使用して子のホログラムを固定することが理にかなっています。

以前のセッションからホログラムを読み込むには:
1. WorldAnchorStore を取得する
2. ワールドアンカーに関連するアプリデータを読み込みます。これにより、ワールドアンカーの ID が提供されます。
3. ID からワールドアンカーを読み込みます

将来のセッションのホログラムを保存するには:
1. WorldAnchorStore を取得する
2. ID を指定してワールドアンカーを保存する
3. ID と共に世界のアンカーに関連するアプリデータを保存する

### <a name="getting-the-worldanchorstore"></a>WorldAnchorStore を取得する

操作を実行する準備ができたことを知らせるために、WorldAnchorStore への参照を保持する必要があります。 これは非同期呼び出しであるため、起動直後にを呼び出す必要があります。

```
WorldAnchorStore.GetAsync(StoreLoaded);
```

この場合、StoreLoaded は、WorldAnchorStore が読み込みを完了したときのハンドラーです。

```
private void StoreLoaded(WorldAnchorStore store)
{
       this.store = store;
}
```

ここでは、特定のワールドアンカーを保存して読み込むために使用する WorldAnchorStore への参照を取得しました。

### <a name="saving-a-worldanchor"></a>WorldAnchor の保存

保存するには、保存する内容に名前を付け、保存する前に WorldAnchor に渡す必要があります。 注: 2 つのアンカーを同じ文字列に保存しようとすると失敗します (ストア。保存すると false が返されます)。 前の保存を削除してから、新しい保存を保存します。

```
private void SaveGame()
{
       // Save data about holograms positioned by this world anchor
       if (!this.savedRoot) // Only Save the root once
       {
              this.savedRoot = this.store.Save("rootGameObject", anchor);
              Assert(this.savedRoot);
       }
}
```

### <a name="loading-a-worldanchor"></a>WorldAnchor を読み込んでいます

読み込み:

```
private void LoadGame()
{
       // Save data about holograms positioned by this world anchor
       this.savedRoot = this.store.Load("rootGameObject", rootGameObject);
       if (!this.savedRoot)
       {
              // We didn't actually have the game root saved! We have to re-place our objects or start over
       }
}
```

また、ストアを使用することもできます。Delete () を削除して、以前に保存して保存したアンカーを削除します。以前に保存したデータをすべて削除するには、() をクリアします。

### <a name="enumerating-existing-anchors"></a>既存のアンカーの列挙

以前に保存されたアンカーを検出するには、GetAllIds を呼び出します。

```
string[] ids = this.store.GetAllIds();
for (int index = 0; index < ids.Length; index++)
{
        Debug.Log(ids[index]);
}
```

## <a name="persisting-holograms-for-multiple-devices"></a>複数のデバイスのホログラムの永続化

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、ローカル WorldAnchor から持続性のあるクラウドアンカーを作成することができます。これにより、複数の HoloLens、iOS、および Android デバイスが同時に存在しない場合でも、アプリはそれらを検索できます。  クラウドアンカーは永続的であるため、複数のデバイスが一定期間にわたって、同じ物理的な場所にあるそのアンカーを基準としてレンダリングされたコンテンツを表示できます。

Unity で共有エクスペリエンスの構築を開始するには、5分間の <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間アンカー unity クイックスタート</a>をお試しください。

Azure 空間アンカーを使用して実行した後は、 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity でアンカーを作成して見つける</a>ことができます。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

ここまでに説明した Unity 開発チェックポイントの旅に従っている場合は、Mixed Reality コアの構成要素を調査しています。 ここから、次のビルディングブロックに進むことができます。

> [!div class="nextstepaction"]
> [空間マッピング](spatial-mapping-in-unity.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [共有エクスペリエンス](shared-experiences-in-unity.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目
* [空間アンカーの永続性](../../design/coordinate-systems.md#spatial-anchor-persistence)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空間アンカー SDK for Unity</a>
