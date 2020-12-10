---
title: Unity の視線入力
description: アプリが混合現実で作成するホログラムをユーザーが対象にする主な方法は、宝石です。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 視線、ヘッド・宝石、unity、ホログラム、mixed reality、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、unity、Mixed Reality ツールキット
ms.openlocfilehash: ca33fef5a5a761df83ed7991b366cf711a5db224
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010363"
---
# <a name="head-gaze-in-unity"></a>Unity でのヘッドを見つめます

アプリが[混合現実](../../discover/mixed-reality.md)で作成する[ホログラム](../../discover/hologram.md)をユーザーが対象とする主な方法は、[宝石](../../design/gaze-and-commit.md)です。

## <a name="implementing-head-gaze"></a>ヘッド見つめを実装する

概念的には、ユーザーのヘッドセットからの光を投射してヒットを確認することによって、 [頭を見つめ](../../design/gaze-and-commit.md) ます。 Unity では、ユーザーのヘッド位置と方向は、 [カメラ](camera-in-unity.md)を通じて公開されます (具体的には [unityengine](https://docs.unity3d.com/ScriptReference/Camera-main.html)。[transform](https://docs.unity3d.com/ScriptReference/Transform-forward.html) と [Unityengine. Camera. main](https://docs.unity3d.com/ScriptReference/Camera-main.html)を変換します。[transform. position](https://docs.unity3d.com/ScriptReference/Transform-position.html).

[RayCast](https://docs.unity3d.com/ScriptReference/Physics.Raycast.html)を呼び出すと、 [RaycastHit](https://docs.unity3d.com/ScriptReference/RaycastHit.html)には、3d 衝突ポイントや、ヘッド宝石光がヒットした他のユーザーオブジェクトなど、衝突に関する情報が含まれます。

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

上記の例では、update ループから1つの raycast を使用して、ユーザーのヘッドポイントの対象を検索しますが、1つのオブジェクトを使用してすべてのヘッドを見つめたプロセスを管理することをお勧めします。 ヘッドを見つめたロジックを組み合わせると、アプリの貴重な処理能力が節約され、raycasting はフレームごとに1つに制限されます。

## <a name="visualizing-head-gaze"></a>ヘッドを視覚化する

コンピューター上のマウスポインターと同じように、ユーザーの顔を示す [カーソル](../../design/cursors.md) を実装する必要があります。 ユーザーが対象としているコンテンツを把握することで、ユーザーが操作しようとしている内容の信頼性が向上します。

## <a name="head-gaze-in-the-mixed-reality-toolkit"></a>Mixed Reality ツールキットの頭を見つめます 
MRTK の [入力マネージャー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html) から、ヘッドを使用してアクセスできます。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

Unity の開発に関する体験に従っている場合は、MRTK コアのビルディングブロックを調べています。 ここから、次のビルディングブロックに進むことができます。

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
