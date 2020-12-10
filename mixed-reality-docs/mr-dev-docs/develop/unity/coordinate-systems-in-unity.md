---
title: Unity の座標系
description: Unity で、固定された、継続的に拡大している大規模な環境で、世界規模で混在する現実のエクスペリエンスを構築する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: 座標系、空間座標系、方向専用、固定スケール、継続スケール、部屋規模、ワールドスケール、360度、取り付けられている、継続的、部屋、ワールド、スケール、位置、向き、Unity、アンカー、空間アンカー、ワールドアンカー、ワールドロック、ワールドロック、ボディロック、ボディロック、追跡の損失、分離機能、境界、recenter、混合現実ヘッドセット、windows mixed reality ヘッドセット、仮想現実のヘッドセット
ms.openlocfilehash: 900c393bf9ab09f1ac49e3108488d081f8025c19
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010283"
---
# <a name="coordinate-systems-in-unity"></a>Unity の座標系

Windows Mixed Reality は、大規模な [エクスペリエンス](../../design/coordinate-systems.md)スケールのアプリをサポートしています。また、向きのみのアプリや、部屋規模のアプリによって配置されたアプリを拡張できます。 HoloLens では、さらに一歩進めて、世界規模のアプリを構築できます。これにより、ユーザーは5メートルを超えて、ビルのフロア全体を調べることができます。

Unity で mixed reality エクスペリエンスを構築するための最初の手順は、アプリが対象とする [エクスペリエンススケール](../../design/coordinate-systems.md) を決定することです。

## <a name="building-an-orientation-only-or-seated-scale-experience"></a>向きのみまたは取り付けられたスケールエクスペリエンスの構築

**名前空間:** *unityengine. XR*<br>
**型:** *XRDevice*

**向きのみ** または取り付けられた **スケールエクスペリエンス** を構築するには、Unity を固定の追跡領域の種類に設定する必要があります。 静止した追跡領域は、Unity のワールド座標系を設定して、 [参照の静止フレーム](../../design/coordinate-systems.md#spatial-coordinate-systems)を追跡します。 静止の追跡モードでは、アプリの起動時に、カメラの既定の場所 (前方が Z) の直前にあるエディターに配置されたコンテンツがユーザーの前に表示されます。

```cs
XRDevice.SetTrackingSpaceType(TrackingSpaceType.Stationary);
```

**名前空間:** *unityengine. XR*<br>
**種類:** *inputtracking*

360度のビデオビューアーのような純粋な **向きのみのエクスペリエンス** (位置指定更新によって錯覚が無駄になる) については、XR を設定でき [ます。InputTracking。 disablePositionalTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking-disablePositionalTracking.html) を true にします。

```cs
InputTracking.disablePositionalTracking = true;
```

挿入された元の recenter を後で使用できるように、固定された **スケールエクスペリエンス** の場合は、XR を呼び出すことができ [ます。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html) メソッド:

```cs
InputTracking.Recenter();
```

## <a name="building-a-standing-scale-or-room-scale-experience"></a>大規模または部屋規模のエクスペリエンスを構築する

**名前空間:** *unityengine. XR*<br>
**型:** *XRDevice*

**大規模** または **部屋規模のエクスペリエンス** を実現するには、フロアを基準としたコンテンツを配置する必要があります。 ユーザーが定義したフロアレベルのオリジンとオプションの部屋の境界を表す **[空間ステージ](../../design/coordinate-systems.md#spatial-coordinate-systems)** を使用して、ユーザーのフロアについては、最初の実行時に設定します。

Unity が世界の座標系をフロアレベルで運用していることを確認するには、Unity が RoomScale の追跡領域の種類を使用していることを設定し、テストします。

```cs
if (XRDevice.SetTrackingSpaceType(TrackingSpaceType.RoomScale))
{
    // RoomScale mode was set successfully.  App can now assume that y=0 in Unity world coordinate represents the floor.
}
else
{
    // RoomScale mode was not set successfully.  App cannot make assumptions about where the floor plane is.
}
```
* Settrackingspace 型によって true が返された場合、Unity は、そのワールド座標系を正常に切り替えて、 [参照のステージフレーム](../../design/coordinate-systems.md#spatial-coordinate-systems)を追跡します。
* Settrackingspace 型から false が返された場合、Unity は参照のステージフレームに切り替えることができませんでした。ユーザーが環境にフロアを設定していない可能性があります。 False の戻り値は一般的ではありませんが、ステージが別の部屋に設定されていて、ユーザーが新しいステージを設定せずに現在の部屋にデバイスを移動した場合に発生する可能性があります。

アプリで RoomScale の追跡領域の種類が正常に設定されると、y = 0 平面に配置されたコンテンツがフロア上に表示されます。 0、0、0の原点は、部屋のセットアップ中にユーザーがそこしたフロア上の特定の場所になります。この位置は、セットアップ中に接続されていた前方方向を表します。

**名前空間:** *UNITYENGINE XR*<br>
**型:** *境界*

スクリプトコードでは、TrackedArea の境界の種類を指定して、UnityEngine 型の TryGetGeometry メソッドを呼び出し、境界ポリゴンを取得できます。 ユーザーが境界を定義している場合 (頂点の一覧を取得した場合)、ユーザーに **ルームスケールエクスペリエンス** を提供し、ユーザーが作成したシーンを周囲にたどることができます。

> [!NOTE]
> ユーザーがこの境界に近づいたときに、境界が自動的に表示されます。 アプリでは、境界自体をレンダリングするためにこの多角形を使用する必要はありません。 ただし、この境界多角形を使用してシーンオブジェクトをレイアウトすることで、ユーザーがテレを使用して物理的にオブジェクトに接続できるようにすることができます。

```cs
var vertices = new List<Vector3>();
if (UnityEngine.Experimental.XR.Boundary.TryGetGeometry(vertices, Boundary.Type.TrackedArea))
{
    // Lay out your app's content within the boundary polygon, to ensure that users can reach it without teleporting.
}
```

## <a name="building-a-world-scale-experience"></a>世界規模でのエクスペリエンスの構築

**名前空間:** *UNITYENGINE. XR*<br>
**型:** *WorldAnchor*

ユーザーが 5 m を超えることができるようにする HoloLens の真の **ワールドスケールエクスペリエンス** では、ルームスケールエクスペリエンスに使用されるもの以外の新しい手法が必要になります。 使用する主な手法の1つは、 [空間アンカー](../../design/coordinate-systems.md#spatial-anchors) を作成して、ユーザーがどの程度ローミングしたかに関係なく、物理的な場所にあるホログラムのクラスターを正確にロックし、 [後のセッションで再びそれらのホログラムを見つける](../../design/coordinate-systems.md#spatial-anchor-persistence)ことです。

Unity では、 **WorldAnchor** Unity コンポーネントをユーザーオブジェクトに追加することによって、空間アンカーを作成します。

### <a name="adding-a-world-anchor"></a>ワールドアンカーの追加

ワールドアンカーを追加するには、 <WorldAnchor> 実際の世界で固定する変換を使用して、game オブジェクトで AddComponent () を呼び出します。

```cs
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

これで完了です。 このゲームオブジェクトは、物理的な世界の現在の場所に固定されるようになりました。物理的な配置を確保するために、Unity のワールド座標が少し時間をかけて若干調整されていることがわかります。 この固定された場所を今後のアプリセッションで再び見つけるには、 [永続](persistence-in-unity.md) 化を使用します。

### <a name="removing-a-world-anchor"></a>ワールドアンカーの削除

他のユーザーが物理的な場所をロックし、このフレームを移動したくない場合は、ワールドアンカーコンポーネントで Destroy を呼び出すことができます。

```cs
Destroy(gameObject.GetComponent<WorldAnchor>());
```

このフレームを移動する場合は、代わりに DestroyImmediate を呼び出す必要があります。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
```

### <a name="moving-a-world-anchored-gameobject"></a>ワールド固定のオブジェクトの移動

ワールドアンカーがある間は、このオブジェクトを移動できません。 このフレームを移動する必要がある場合は、次のことを行う必要があります。
1. ワールドアンカーコンポーネントを直ちに破棄する
2. オブジェクトを移動する
3. 新しいワールドアンカーコンポーネントを、このオブジェクトに追加します。

```cs
DestroyImmediate(gameObject.GetComponent<WorldAnchor>());
gameObject.transform.position = new Vector3(0, 0, 2);
WorldAnchor anchor = gameObject.AddComponent<WorldAnchor>();
```

### <a name="handling-locatability-changes"></a>Locatability の変更の処理

WorldAnchor は、ある時点で物理的な世界では特定できないことがあります。 このような場合は、Unity はアンカー付きオブジェクトの変換を更新しません。 これは、アプリの実行中にも変更される可能性があります。 Locatability の変更を処理できないと、オブジェクトが世界の正しい物理的な場所に表示されません。

Locatability の変更について通知するには、次のようにします。
1. OnTrackingChanged イベントのサブスクライブ
2. イベントを処理します

**Ontrackingchanged** イベントは、基になる空間アンカーが、状態が "可能" から "見つからない" の間で変化するたびに呼び出されます。

```cs
anchor.OnTrackingChanged += Anchor_OnTrackingChanged;
```

次に、イベントを処理します。

```cs
private void Anchor_OnTrackingChanged(WorldAnchor self, bool located)
{
    // This simply activates/deactivates this object and all children when tracking changes
    self.gameObject.SetActiveRecursively(located);
}
```

アンカーはすぐに配置されることがあります。 この場合、AddComponent () がを返すと、アンカーのこの isLocated プロパティは true に設定され <WorldAnchor> ます。 その結果、OnTrackingChanged イベントはトリガーされません。 クリーンパターンでは、アンカーをアタッチした後、最初の IsLocated 状態を使用して OnTrackingChanged ハンドラーを呼び出すことができます。

```cs
Anchor_OnTrackingChanged(anchor, anchor.isLocated);
```

## <a name="sharing-anchors-across-devices"></a>デバイス間でのアンカーの共有

<a href="https://docs.microsoft.com/azure/spatial-anchors/overview" target="_blank">Azure 空間アンカー</a>を使用して、ローカル WorldAnchor から持続性のあるクラウドアンカーを作成します。これにより、アプリは複数の HoloLens、IOS、Android デバイスで検索できます。  複数のデバイスで共通の空間アンカーを共有することにより、各ユーザーは、同じ物理的な場所でそのアンカーを基準としてレンダリングされたコンテンツを表示できます。  これにより、リアルタイム共有エクスペリエンスを実現できます。

Unity で共有エクスペリエンスの構築を開始するには、5分間の <a href="https://docs.microsoft.com/azure/spatial-anchors/unity-overview" target="_blank">Azure 空間アンカー unity クイックスタート</a>をお試しください。

Azure 空間アンカーを使用して実行した後は、 <a href="https://docs.microsoft.com/azure/spatial-anchors/concepts/create-locate-anchors-unity" target="_blank">Unity でアンカーを作成して見つける</a>ことができます。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

ここまでに説明した Unity 開発チェックポイントの旅に従っている場合は、Mixed Reality コアの構成要素を調査しています。 ここから、次のビルディングブロックに進むことができます。

> [!div class="nextstepaction"]
> [視線入力](gaze-in-unity.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [共有エクスペリエンス](shared-experiences-in-unity.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目
* [エクスペリエンススケール](../../design/coordinate-systems.md#mixed-reality-experience-scales)
* [空間ステージ](../../design/coordinate-systems.md#stage-frame-of-reference)
* [Unity での損失の追跡](tracking-loss-in-unity.md)
* [空間アンカー](../../design/spatial-anchors.md)
* [Unity の永続化](persistence-in-unity.md)
* [Unity での共有エクスペリエンス](shared-experiences-in-unity.md)
* <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>
* <a href="https://docs.microsoft.com/dotnet/api/Microsoft.Azure.SpatialAnchors" target="_blank">Azure 空間アンカー SDK for Unity</a>
