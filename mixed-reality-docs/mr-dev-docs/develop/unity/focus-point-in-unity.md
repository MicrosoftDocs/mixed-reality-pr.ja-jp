---
title: Unity でのフォーカス ポイント
description: フォーカスポイントを設定して Unity のホログラムの安定性を手動で調整する
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, フォーカスポイント, フォーカスプレーン, 安定化平面, 安定化ポイント, reprojection, LSR, 深度バッファー
ms.openlocfilehash: 4d8c8a232d12a8d6f0a7694fbc0ed8f66395163a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683111"
---
# <a name="focus-point-in-unity"></a>Unity でのフォーカス ポイント

**名前空間:** *UNITYENGINE. XR*<br>
**型** : *HolographicSettings*

[フォーカスポイント](../platform-capabilities-and-apis/hologram-stability.md#reprojection)は、現在表示されているホログラムに対して安定化を最適に実行する方法について、HoloLens にヒントを提供するように設定できます。

Unity でフォーカスポイントを設定する場合は、 *HolographicSettings. SetFocusPointForFrame ()* を使用してすべてのフレームを設定する必要があります。 フレームにフォーカスポイントが設定されていない場合は、既定の安定化平面が使用されます。

> [!NOTE]
> 既定では、新しい Unity プロジェクトの [深度バッファーの共有を有効にする] オプションが設定されています。  このオプションを使用すると、アプリでフォーカスポイントを指定しなくても、イマーシブデスクトップヘッドセットまたは Windows 10 April 2018 更新プログラム (RS4) 以降を実行する HoloLens で実行されている Unity アプリが Windows に深度バッファーを送信し、ホログラムの安定性を自動的に最適化します。
> * イマーシブデスクトップヘッドセットでは、これにより、ピクセルごとの深度ベースの再プロジェクションが有効になります。
> * Windows 10 April 2018 Update 以降を実行している HoloLens では、これにより深度バッファーが分析され、最適な安定化平面が自動的に選択されます。
>
> どちらの方法も、各フレームのフォーカスポイントを選択するために、アプリによる明示的な作業を行わずに、より優れたイメージ品質を提供する必要があります。  フォーカスポイントを手動で指定すると、上記の自動動作がオーバーライドされ、通常はホログラムの安定性が低下します。  一般に、アプリが HoloLens で実行されている場合は、Windows 10 April 2018 更新プログラムにまだ更新されていない場合にのみ、手動のフォーカスポイントを指定することをお勧めします。

### <a name="example"></a>例

*SetFocusPointForFrame* 静的関数で使用できるオーバーロードによって提案されているように、フォーカスポイントを設定するにはさまざまな方法があります。 次に示すのは、各フレームに対して指定されたオブジェクトにフォーカス平面を設定する簡単な例です。

```cs
public GameObject focusedObject;
void Update()
{
    // Normally the normal is best set to be the opposite of the main camera's
    // forward vector.
    // If the content is actually all on a plane (like text), set the normal to
    // the normal of the plane and ensure the user does not pass through the
    // plane.
    var normal = -Camera.main.transform.forward;     
    var position = focusedObject.transform.position;
    UnityEngine.XR.WSA.HolographicSettings.SetFocusPointForFrame(position, normal);
}
```

上の単純なコードでは、フォーカスがあるオブジェクトがユーザーの背後にある場合に、ホログラムの安定性が低下する可能性があることに注意してください。  このため、通常は、フォーカスポイントを手動で指定するのではなく、"深度バッファーの共有を有効にする" を設定する必要があります。

## <a name="next-development-checkpoint"></a>次回の開発チェックポイント

ここまでに説明した Unity 開発チェックポイントの旅に従っている場合は、Mixed Reality プラットフォームの機能と Api の調査が途中で終了しています。 ここから、次のトピックに進むことができます。

> [!div class="nextstepaction"]
> [追跡の損失](tracking-loss-in-unity.md)

または、デバイスまたはエミュレーターへのアプリのデプロイに直接移動します。

> [!div class="nextstepaction"]
> [HoloLens または Windows Mixed Reality イマーシブヘッドセットへのデプロイ](../platform-capabilities-and-apis/using-visual-studio.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#3-platform-capabilities-and-apis) に戻ることができます。

### <a name="see-also"></a>関連項目
* [安定化平面](../platform-capabilities-and-apis/hologram-stability.md#reprojection)
