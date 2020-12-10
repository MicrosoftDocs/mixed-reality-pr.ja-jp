---
ms.openlocfilehash: 9fdcbdfe115fa859081c28b768f9c213ac241d13
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002726"
---
# <a name="425"></a>[4.25](#tab/425)

この `EWMRHandKeypoint` 列挙型は、手のボーン階層を記述します。 ブループリントに記載されている各ハンドキーポイントを見つけることができます。

![ハンドキーポイント BP](../images/hand-keypoint-bp.png)

完全な C++ 列挙型を以下に示します。
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

各列挙型のケースの数値は、 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) テーブルで確認できます。

### <a name="supporting-hand-tracking"></a>ハンドトラッキングのサポート

手動追跡機能を追加することによって、ブループリントで **手動追跡を** 使用することができます **> Windows Mixed Reality**:

![ハンドトラッキング BP](../images/unreal/hand-tracking-bp.png)

`true`デバイスでハンドトラッキングがサポートされている場合、およびハンドトラッキングが使用できない場合、この関数はを返し `false` ます。

![ハンドトラッキング BP のサポート](../images/unreal/supports-hand-tracking-bp.png)

C++:

`WindowsMixedRealityHandTrackingFunctionLibrary.h` を含めます。

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>ハンドトラッキングの取得

**GetHandJointTransform** を使用して、空間データを手動で返すことができます。 データはすべてのフレームを更新しますが、フレーム内にいる場合は、返された値がキャッシュされます。 パフォーマンス上の理由から、この関数では大きなロジックを使用しないことをお勧めします。

![ハンドジョイント変換の取得](../images/unreal/get-hand-joint-transform.png)

C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

GetHandJointTransform の関数パラメーターの詳細を次に示します。

* **手動** –ユーザーを左または右に配置できます。
* **Keypoint** –ハンドのボーンです。
* **Transform** –ボーンの基本の座標と向きを調整します。 次のボーンのベースを要求して、ボーンの終点の変換データを取得できます。 特別なヒントのボーンは、distal の終わりを示します。
* * * 半径: ボーンのベースの半径。
* * * 戻り値—ボーンがこのフレームを追跡している場合は true、ボーンが追跡されていない場合は false。


# <a name="426"></a>[4.26](#tab/426)

階層は列挙型によって記述され `EHandKeypoint` ます。

![手の keypoint bluprint オプションの画像](../images/hand-keypoint-bp.png)

**Get Motion Controller データ** 関数を使用して、ユーザーの手からすべてのデータを取得できます。 この関数は、 **XRMotionControllerData** 構造体を返します。 次に示すのは、XRMotionControllerData 構造体を解析してコロケーションの場所を取得し、各ジョイントの位置にデバッグ座標系を描画するサンプルブループリントスクリプトです。

![チャネル関数による行トレースに接続された、"データの取得" 関数のブループリント](../images/unreal-hand-tracking-img-03.png)

構造が有効であり、それが手であるかどうかを確認することが重要です。 そうしないと、位置、回転、および半径配列へのアクセスに未定義の動作が発生する可能性があります。
