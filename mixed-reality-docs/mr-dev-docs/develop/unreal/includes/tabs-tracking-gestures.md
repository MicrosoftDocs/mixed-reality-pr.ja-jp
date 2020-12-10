---
ms.openlocfilehash: 50b56f6f081f682c3f3655e81aa492d84d254314
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002703"
---
# <a name="425"></a>[<span data-ttu-id="35e42-101">4.25</span><span class="sxs-lookup"><span data-stu-id="35e42-101">4.25</span></span>](#tab/425)

<span data-ttu-id="35e42-102">のブループリント関数は、呼び出し元のコードファイルにを追加することで、 **Windows Mixed Reality 空間入力** と C++ 関数の下に `WindowsMixedRealitySpatialInputFunctionLibrary.h` あります。</span><span class="sxs-lookup"><span data-stu-id="35e42-102">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input**, and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![キャプチャジェスチャ](../images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="35e42-104">列挙型</span><span class="sxs-lookup"><span data-stu-id="35e42-104">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="35e42-105">建築</span><span class="sxs-lookup"><span data-stu-id="35e42-105">Blueprint:</span></span>

![ジェスチャの種類](../images/unreal/gesture-type.png)

<span data-ttu-id="35e42-107">C++:</span><span class="sxs-lookup"><span data-stu-id="35e42-107">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="35e42-108">機能</span><span class="sxs-lookup"><span data-stu-id="35e42-108">Function</span></span>
<span data-ttu-id="35e42-109">ジェスチャのキャプチャを有効または無効にするには、関数を使用 `CaptureGestures` します。</span><span class="sxs-lookup"><span data-stu-id="35e42-109">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="35e42-110">有効なジェスチャによって入力イベントが発生した場合、この関数はジェスチャキャプチャが成功した場合はを返し、エラーが発生した場合はを返し `true` `false` ます。</span><span class="sxs-lookup"><span data-stu-id="35e42-110">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="35e42-111">建築</span><span class="sxs-lookup"><span data-stu-id="35e42-111">Blueprint:</span></span>

![キャプチャジェスチャ BP](../images/unreal/capture-gestures-bp.png)

<span data-ttu-id="35e42-113">C++:</span><span class="sxs-lookup"><span data-stu-id="35e42-113">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false,
    bool Hold = false,
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None,
    bool NavigationAxisX = true,
    bool NavigationAxisY = true,
    bool NavigationAxisZ = true);
```

<span data-ttu-id="35e42-114">次に示すのは、[ブループリント] と [C++: キーイベント] で確認できる主要なイベントです。 ![](../images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="35e42-114">The following are key events, which you can find in Blueprints and C++: ![Key Events](../images/unreal/key-events.png)</span></span>

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

# <a name="426"></a>[<span data-ttu-id="35e42-116">4.26</span><span class="sxs-lookup"><span data-stu-id="35e42-116">4.26</span></span>](#tab/426)

### <a name="windows-mixed-reality"></a><span data-ttu-id="35e42-117">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="35e42-117">Windows Mixed Reality</span></span>

![ジェスチャの構成機能に接続されたイベント開始再生のブループリント](../images/unreal-hand-tracking-img-09.png)

<span data-ttu-id="35e42-119">次に、次のイベントをサブスクライブするコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35e42-119">Then you should add code to subscribe to the following events:</span></span>

<span data-ttu-id="35e42-120">![Windows 空間入力のホールド、タップ、および左操作のジェスチャのブループリントの ](../images/unreal/key-events.png)
 ![ スクリーンショット詳細パネルの [空間入力] タップジェスチャオプションのスクリーンショット](../images/unreal/key-events2.png)</span><span class="sxs-lookup"><span data-stu-id="35e42-120">![Blueprint of Windows spatial input hold, tap, and left manipulation gestures](../images/unreal/key-events.png)
![Screenshot of Windows spatial input tap gesture options in the details panel](../images/unreal/key-events2.png)</span></span>

### <a name="openxr"></a><span data-ttu-id="35e42-121">OpenXR</span><span class="sxs-lookup"><span data-stu-id="35e42-121">OpenXR</span></span>

<span data-ttu-id="35e42-122">OpenXR では、ジェスチャイベントは入力パイプラインを通じて追跡されます。</span><span class="sxs-lookup"><span data-stu-id="35e42-122">In OpenXR, gesture events are tracked through the input pipeline.</span></span> <span data-ttu-id="35e42-123">デバイスは、手動での対話を使用することにより、タップしてジェスチャを自動的に認識することができますが、他のジェスチャは認識しません。</span><span class="sxs-lookup"><span data-stu-id="35e42-123">Using hand interaction, the device can automatically recognize Tap and Hold gestures, but not the others.</span></span> <span data-ttu-id="35e42-124">これらの名前は、OpenXRMsftHandInteraction Select とグリップのマッピングとして指定されます。</span><span class="sxs-lookup"><span data-stu-id="35e42-124">They are named as OpenXRMsftHandInteraction Select and Grip mappings.</span></span> <span data-ttu-id="35e42-125">サブスクリプションを有効にする必要はありません。次のように、プロジェクト設定/エンジン/入力でイベントを宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35e42-125">You don’t need to enable subscription, you should declare the events in Project Settings/Engine/Input, just like this:</span></span>

![OpenXR アクションマッピングのスクリーンショット](../images/unreal-hand-tracking-img-12.png)
