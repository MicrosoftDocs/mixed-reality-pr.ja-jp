---
ms.openlocfilehash: 50b56f6f081f682c3f3655e81aa492d84d254314
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002703"
---
# <a name="425"></a>[4.25](#tab/425)

のブループリント関数は、呼び出し元のコードファイルにを追加することで、 **Windows Mixed Reality 空間入力** と C++ 関数の下に `WindowsMixedRealitySpatialInputFunctionLibrary.h` あります。

![キャプチャジェスチャ](../images/unreal/capture-gestures.png)

### <a name="enum"></a>列挙型
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
建築

![ジェスチャの種類](../images/unreal/gesture-type.png)

C++:
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>機能
ジェスチャのキャプチャを有効または無効にするには、関数を使用 `CaptureGestures` します。 有効なジェスチャによって入力イベントが発生した場合、この関数はジェスチャキャプチャが成功した場合はを返し、エラーが発生した場合はを返し `true` `false` ます。

建築

![キャプチャジェスチャ BP](../images/unreal/capture-gestures-bp.png)

C++:
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

次に示すのは、[ブループリント] と [C++: キーイベント] で確認できる主要なイベントです。 ![](../images/unreal/key-events.png)

![主要イベント2](../images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

# <a name="426"></a>[4.26](#tab/426)

### <a name="windows-mixed-reality"></a>Windows Mixed Reality

![ジェスチャの構成機能に接続されたイベント開始再生のブループリント](../images/unreal-hand-tracking-img-09.png)

次に、次のイベントをサブスクライブするコードを追加する必要があります。

![Windows 空間入力のホールド、タップ、および左操作のジェスチャのブループリントの ](../images/unreal/key-events.png)
 ![ スクリーンショット詳細パネルの [空間入力] タップジェスチャオプションのスクリーンショット](../images/unreal/key-events2.png)

### <a name="openxr"></a>OpenXR

OpenXR では、ジェスチャイベントは入力パイプラインを通じて追跡されます。 デバイスは、手動での対話を使用することにより、タップしてジェスチャを自動的に認識することができますが、他のジェスチャは認識しません。 これらの名前は、OpenXRMsftHandInteraction Select とグリップのマッピングとして指定されます。 サブスクリプションを有効にする必要はありません。次のように、プロジェクト設定/エンジン/入力でイベントを宣言する必要があります。

![OpenXR アクションマッピングのスクリーンショット](../images/unreal-hand-tracking-img-12.png)
