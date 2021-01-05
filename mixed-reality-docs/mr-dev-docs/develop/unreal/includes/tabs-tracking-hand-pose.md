---
ms.openlocfilehash: c5a13798ca6a73f1a6410abe310c2166b67f4626
ms.sourcegitcommit: 13ef9f89ee61fbfe547ecf5fdfdb97560a0de833
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2020
ms.locfileid: "97717423"
---
# <a name="426"></a>[<span data-ttu-id="182ed-101">4.26</span><span class="sxs-lookup"><span data-stu-id="182ed-101">4.26</span></span>](#tab/426)

<span data-ttu-id="182ed-102">階層は列挙型によって記述され `EHandKeypoint` ます。</span><span class="sxs-lookup"><span data-stu-id="182ed-102">The hierarchy is described by `EHandKeypoint` enum:</span></span>

![手の keypoint bluprint オプションの画像](../images/hand-keypoint-bp.png)

<span data-ttu-id="182ed-104">**Get Motion Controller データ** 関数を使用して、ユーザーの手からすべてのデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="182ed-104">You can get all this data from a user’s hands using the **Get Motion Controller Data** function.</span></span> <span data-ttu-id="182ed-105">この関数は、 **XRMotionControllerData** 構造体を返します。</span><span class="sxs-lookup"><span data-stu-id="182ed-105">That function returns an **XRMotionControllerData** structure.</span></span> <span data-ttu-id="182ed-106">次に示すのは、XRMotionControllerData 構造体を解析してコロケーションの場所を取得し、各ジョイントの位置にデバッグ座標系を描画するサンプルブループリントスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="182ed-106">Below is a sample Blueprint script that parses the XRMotionControllerData structure to get hand joint locations and draws a debug coordinate system at each joint’s location.</span></span>

![チャネル関数による行トレースに接続された、"データの取得" 関数のブループリント](../images/unreal-hand-tracking-img-03.png)

<span data-ttu-id="182ed-108">構造が有効であり、それが手であるかどうかを確認することが重要です。</span><span class="sxs-lookup"><span data-stu-id="182ed-108">It's important to check if the structure is valid and that it's a hand.</span></span> <span data-ttu-id="182ed-109">そうしないと、位置、回転、および半径配列へのアクセスに未定義の動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="182ed-109">Otherwise, you may get undefined behavior in access to positions, rotations, and radii arrays.</span></span>

# <a name="425"></a>[<span data-ttu-id="182ed-110">4.25</span><span class="sxs-lookup"><span data-stu-id="182ed-110">4.25</span></span>](#tab/425)

<span data-ttu-id="182ed-111">この `EWMRHandKeypoint` 列挙型は、手のボーン階層を記述します。</span><span class="sxs-lookup"><span data-stu-id="182ed-111">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="182ed-112">ブループリントに記載されている各ハンドキーポイントを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="182ed-112">You can find each hand keypoint listed in your Blueprints:</span></span>

![ハンドキーポイント BP](../images/hand-keypoint-bp.png)

<span data-ttu-id="182ed-114">完全な C++ 列挙型を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="182ed-114">The full C++ enum is listed below:</span></span>
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

<span data-ttu-id="182ed-115">各列挙型のケースの数値は、 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) テーブルで確認できます。</span><span class="sxs-lookup"><span data-stu-id="182ed-115">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span>

### <a name="supporting-hand-tracking"></a><span data-ttu-id="182ed-116">ハンドトラッキングのサポート</span><span class="sxs-lookup"><span data-stu-id="182ed-116">Supporting Hand Tracking</span></span>

<span data-ttu-id="182ed-117">手動追跡機能を追加することによって、ブループリントで **手動追跡を** 使用することができます **> Windows Mixed Reality**:</span><span class="sxs-lookup"><span data-stu-id="182ed-117">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality**:</span></span>

![ハンドトラッキング BP](../images/unreal/hand-tracking-bp.png)

<span data-ttu-id="182ed-119">`true`デバイスでハンドトラッキングがサポートされている場合、およびハンドトラッキングが使用できない場合、この関数はを返し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="182ed-119">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking isn't available.</span></span>

![ハンドトラッキング BP のサポート](../images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="182ed-121">C++:</span><span class="sxs-lookup"><span data-stu-id="182ed-121">C++:</span></span>

<span data-ttu-id="182ed-122">`WindowsMixedRealityHandTrackingFunctionLibrary.h` を含めます。</span><span class="sxs-lookup"><span data-stu-id="182ed-122">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="182ed-123">ハンドトラッキングの取得</span><span class="sxs-lookup"><span data-stu-id="182ed-123">Getting Hand Tracking</span></span>

<span data-ttu-id="182ed-124">**GetHandJointTransform** を使用して、空間データを手動で返すことができます。</span><span class="sxs-lookup"><span data-stu-id="182ed-124">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="182ed-125">データはすべてのフレームを更新しますが、フレーム内にいる場合は、返された値がキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="182ed-125">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="182ed-126">パフォーマンス上の理由から、この関数では大きなロジックを使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="182ed-126">It's not recommended to have heavy logic in this function for performance reasons.</span></span>

![ハンドジョイント変換の取得](../images/unreal/get-hand-joint-transform.png)

<span data-ttu-id="182ed-128">C++:</span><span class="sxs-lookup"><span data-stu-id="182ed-128">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="182ed-129">GetHandJointTransform の関数パラメーターの詳細を次に示します。</span><span class="sxs-lookup"><span data-stu-id="182ed-129">Here's a breakdown of GetHandJointTransform's function parameters:</span></span>

* <span data-ttu-id="182ed-130">**手動** –ユーザーを左または右に配置できます。</span><span class="sxs-lookup"><span data-stu-id="182ed-130">**Hand** – can be the users left or right hand.</span></span>
* <span data-ttu-id="182ed-131">**Keypoint** –ハンドのボーンです。</span><span class="sxs-lookup"><span data-stu-id="182ed-131">**Keypoint** – the bone of the hand.</span></span>
* <span data-ttu-id="182ed-132">**Transform** –ボーンの基本の座標と向きを調整します。</span><span class="sxs-lookup"><span data-stu-id="182ed-132">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="182ed-133">次のボーンのベースを要求して、ボーンの終点の変換データを取得できます。</span><span class="sxs-lookup"><span data-stu-id="182ed-133">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="182ed-134">特別なヒントのボーンは、distal の終わりを示します。</span><span class="sxs-lookup"><span data-stu-id="182ed-134">A special Tip bone gives end of distal.</span></span>
* <span data-ttu-id="182ed-135">\* \* 半径: ボーンのベースの半径。</span><span class="sxs-lookup"><span data-stu-id="182ed-135">\*\*Radius—radius of the base of the bone.</span></span>
* <span data-ttu-id="182ed-136">\* \* 戻り値—ボーンがこのフレームを追跡している場合は true、ボーンが追跡されていない場合は false。</span><span class="sxs-lookup"><span data-stu-id="182ed-136">\*\*Return Value—true if the bone is tracked this frame, false if the bone isn't tracked.</span></span>

