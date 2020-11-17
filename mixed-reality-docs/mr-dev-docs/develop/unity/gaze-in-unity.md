---
title: Unity の視線入力
description: アプリが混合現実で作成するホログラムをユーザーが対象にする主な方法は、宝石です。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 視線、ヘッド・宝石、unity、ホログラム、mixed reality、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、unity、Mixed Reality ツールキット
ms.openlocfilehash: 0c62de9cb1b7ea892831ea2cedbeb23be5ea7b37
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677511"
---
# <a name="head-gaze-in-unity"></a>Unity でのヘッドを見つめます

アプリが[混合現実](../../discover/mixed-reality.md)で作成する[ホログラム](../../discover/hologram.md)をユーザーが対象にする主な方法は、[宝石](../../design/gaze-and-commit.md)です。


## <a name="implementing-head-gaze"></a>ヘッド見つめを実装する

概念的には、ヘッド・ [宝石](../../design/gaze-and-commit.md) は、ヘッドセットがあるユーザーのヘッドから、接続している前方方向に、射線がどのように衝突しているかを判断することによって実装されます。
Unity では、ユーザーの head 位置と方向は、Unity のメイン [カメラ](camera-in-unity.md)(具体的には [unityengine](https://docs.unity3d.com/ScriptReference/Camera-main.html)) を介して公開されます。[transform](https://docs.unity3d.com/ScriptReference/Transform-forward.html) と [Unityengine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html)を変換します。[transform. position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

[RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html)を呼び出すと、衝突が発生した3d ポイントや、その他の競合しがを使用している他のオブジェクトを含む、衝突に関する情報を含む[RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html)構造が生成されます。

### <a name="example-implement-head-gaze"></a>例: ヘッドを見つめて実装する

```cs
void Update()
{
       RaycastHit hitInfo;
       if (Physics.Raycast(
               Camera.main.transform.position,
               Camera.main.transform.forward,
               out hitInfo,
               20.0f,
               Physics.DefaultRaycastLayers))
       {
           // If the Raycast has succeeded and hit a hologram
           // hitInfo's point represents the position being gazed at
           // hitInfo's collider GameObject represents the hologram being gazed at
       }
}
```

### <a name="best-practices"></a>ベスト プラクティス

上記の例では、update ループで1つの raycast を実行してユーザーのヘッドポイントの対象を見つける方法を示していますが、この操作は、gazed されているオブジェクトに関係する可能性があるすべてのオブジェクトではなく、頭を見つめて管理する1つのオブジェクトで行うことをお勧めします。 これにより、各フレームに1つのヘッドを raycast するだけで、アプリの処理を保存できます。

## <a name="visualizing-head-gaze"></a>ヘッドを視覚化する

マウスポインターを使用してコンテンツをターゲットにして操作するデスクトップと同様に、ユーザーの顔を示す [カーソル](../../design/cursors.md) を実装する必要があります。 これにより、ユーザーが操作しようとしている内容に自信を持っています。

## <a name="head-gaze-in-the-mixed-reality-toolkit-v2"></a>Mixed Reality Toolkit v2 でのヘッドを見つめます
MRTK v2 の [入力マネージャー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) から、ヘッドを使用してアクセスできます。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

私たちが用意した Unity 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。 ここから、次の構成要素に進むことができます。

> [!div class="nextstepaction"]
> [ジェスチャとモーション コントローラー](gestures-and-motion-controllers-in-unity.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [共有エクスペリエンス](shared-experiences-in-unity.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目
* [カメラ](camera-in-unity.md)
* [カーソル](../../design/cursors.md)
* [頭の視線入力とコミット](../../design/gaze-and-commit.md)
