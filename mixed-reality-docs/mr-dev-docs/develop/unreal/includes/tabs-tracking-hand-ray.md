---
ms.openlocfilehash: 23bba22801f61f6b4814991c8b3bde68d2c5f6b7
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002743"
---
# <a name="425"></a>[<span data-ttu-id="5d1c9-101">4.25</span><span class="sxs-lookup"><span data-stu-id="5d1c9-101">4.25</span></span>](#tab/425)

<span data-ttu-id="5d1c9-102">ブループリントを使用するには、 **Windows Mixed Reality HMD** で任意のアクションを検索します。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-102">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD**:</span></span>

![ハンド光線 BP](../images/unreal/hand-rays-bp.png)

<span data-ttu-id="5d1c9-104">C++ でこれらのファイルにアクセスするには、 `WindowsMixedRealityFunctionLibrary.h` 呼び出し元のコードファイルの先頭にを含めます。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-104">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="5d1c9-105">列挙型</span><span class="sxs-lookup"><span data-stu-id="5d1c9-105">Enum</span></span>

<span data-ttu-id="5d1c9-106">また、[ **Ehmdinputコントローラー**] の下にある入力ケースにアクセスできます。このボタンは、ブループリントで使用できます。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-106">You also have access to input cases under **EHMDInputControllerButtons**, which can be used in Blueprints:</span></span>

![入力コントローラーボタン](../images/unreal/input-controller-buttons.png)

<span data-ttu-id="5d1c9-108">C++ でのアクセスには、 `EHMDInputControllerButtons` 列挙型クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-108">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="5d1c9-109">次に、該当する2つの列挙型ケースの内訳を示します。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-109">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="5d1c9-110">**Select** -ユーザーがトリガーした選択イベント。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-110">**Select** - User triggered Select event.</span></span>
    * <span data-ttu-id="5d1c9-111">HoloLens 2 で、エアタップ、宝石、およびコミットによってトリガーされます。または、 [音声入力](../unreal-voice-input.md) を有効にした "選択" を言います。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-111">Triggered in HoloLens 2 by air-tap, gaze, and commit, or by saying “Select” with [voice input](../unreal-voice-input.md) enabled.</span></span>
* <span data-ttu-id="5d1c9-112">ユーザーによってトリガーされるイベントを **把握** します。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-112">**Grasp** - User triggered Grasp event.</span></span>
    * <span data-ttu-id="5d1c9-113">ホログラムでユーザーの指を閉じることによって、HoloLens 2 でトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-113">Triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span>

<span data-ttu-id="5d1c9-114">次に示す列挙体を使用して、C++ でのハンドメッシュの追跡状態にアクセスでき `EHMDTrackingStatus` ます。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-114">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="5d1c9-115">次に、該当する2つの列挙型ケースの内訳を示します。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-115">Below is a breakdown of the two applicable enum cases:</span></span>

* <span data-ttu-id="5d1c9-116">**Nottracked** –-ハンドは表示されません</span><span class="sxs-lookup"><span data-stu-id="5d1c9-116">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="5d1c9-117">**追跡** –ハンドは完全に追跡されます。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-117">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="5d1c9-118">構造体</span><span class="sxs-lookup"><span data-stu-id="5d1c9-118">Struct</span></span>

<span data-ttu-id="5d1c9-119">PointerPoseInfo 構造体は、次のような手作業のデータに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-119">The PointerPoseInfo struct can give you information on the following hand data:</span></span>

* <span data-ttu-id="5d1c9-120">**Origin** –ハンドオリジン</span><span class="sxs-lookup"><span data-stu-id="5d1c9-120">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="5d1c9-121">**方向** –ハンドの方向</span><span class="sxs-lookup"><span data-stu-id="5d1c9-121">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="5d1c9-122">**アップ** (手動)</span><span class="sxs-lookup"><span data-stu-id="5d1c9-122">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="5d1c9-123">**方向** -方向の四元数</span><span class="sxs-lookup"><span data-stu-id="5d1c9-123">**Orientation** – orientation quaternion</span></span>
* <span data-ttu-id="5d1c9-124">**ステータスの追跡** -現在の追跡状態</span><span class="sxs-lookup"><span data-stu-id="5d1c9-124">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="5d1c9-125">次のように、ブループリントを使用して PointerPoseInfo 構造体にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-125">You can access the PointerPoseInfo struct through Blueprints, as shown below:</span></span>

![ポインターのポーズ情報 BP](../images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="5d1c9-127">C++ の場合:</span><span class="sxs-lookup"><span data-stu-id="5d1c9-127">Or with C++:</span></span>

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a><span data-ttu-id="5d1c9-128">機能</span><span class="sxs-lookup"><span data-stu-id="5d1c9-128">Functions</span></span>

<span data-ttu-id="5d1c9-129">次に示すすべての関数は、継続的な監視を可能にするすべてのフレームに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-129">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span>

1. <span data-ttu-id="5d1c9-130">**ポインターの取得の詳細** 情報は、現在のフレームにおけるハンドレイの方向に関する完全な情報を返します。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-130">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span>

<span data-ttu-id="5d1c9-131">建築</span><span class="sxs-lookup"><span data-stu-id="5d1c9-131">Blueprint:</span></span>

![ポインターの表示情報の取得](../images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="5d1c9-133">C++:</span><span class="sxs-lookup"><span data-stu-id="5d1c9-133">C++:</span></span>
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="5d1c9-134">**Grasped** は、現在のフレームに Grasped がある場合に true を返します。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-134">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="5d1c9-135">建築</span><span class="sxs-lookup"><span data-stu-id="5d1c9-135">Blueprint:</span></span>

![Grasped BP](../images/unreal/is-grasped-bp.png)

<span data-ttu-id="5d1c9-137">C++:</span><span class="sxs-lookup"><span data-stu-id="5d1c9-137">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. <span data-ttu-id="5d1c9-138">**Select 押さ** れた場合、ユーザーが現在のフレームで select をトリガーした場合は true を返します。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-138">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="5d1c9-139">建築</span><span class="sxs-lookup"><span data-stu-id="5d1c9-139">Blueprint:</span></span>

![選択された BP (BP)](../images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="5d1c9-141">C++:</span><span class="sxs-lookup"><span data-stu-id="5d1c9-141">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="5d1c9-142">現在のフレームでイベントまたはボタンがトリガーされた場合、**ボタンがクリックされる** と true が返されます。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-142">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="5d1c9-143">建築</span><span class="sxs-lookup"><span data-stu-id="5d1c9-143">Blueprint:</span></span>

![ボタンが BP をクリックしました](../images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="5d1c9-145">C++:</span><span class="sxs-lookup"><span data-stu-id="5d1c9-145">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="5d1c9-146">**コントローラー追跡状態の取得** は、現在のフレームの追跡状態を返します。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-146">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="5d1c9-147">建築</span><span class="sxs-lookup"><span data-stu-id="5d1c9-147">Blueprint:</span></span>

![コントローラー追跡ステータス BP の取得](../images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="5d1c9-149">C++:</span><span class="sxs-lookup"><span data-stu-id="5d1c9-149">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
# <a name="426"></a>[<span data-ttu-id="5d1c9-150">4.26</span><span class="sxs-lookup"><span data-stu-id="5d1c9-150">4.26</span></span>](#tab/426)

<span data-ttu-id="5d1c9-151">手の形のデータを取得するには、前のセクションの「Get Motion Controller Data 関数」を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-151">To get the data for the hand rays, you should use the Get Motion Controller Data function from the previous section.</span></span> <span data-ttu-id="5d1c9-152">返される構造体には、ハンドレイを作成するために使用できる2つのパラメーター ( **目標位置** と **目標の回転**) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-152">The returned structure contains two parameters you can use to create a hand ray – **Aim Position** and **Aim Rotation**.</span></span> <span data-ttu-id="5d1c9-153">これらのパラメーターは、エルボウによって送られる射線を形成します。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-153">These parameters form a ray directed by your elbow.</span></span> <span data-ttu-id="5d1c9-154">これらを取得して、指されているホログラムを見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-154">You should take them and find a hologram being pointed by.</span></span>

<span data-ttu-id="5d1c9-155">次に示すのは、ハンドレイがウィジェットをヒットし、カスタムヒット結果を設定するかどうかを判断する例です。</span><span class="sxs-lookup"><span data-stu-id="5d1c9-155">Below is an example of determining whether a hand ray hits a Widget and setting a custom hit result:</span></span>

![Get motion controller データ関数のブループリント](../images/unreal-hand-tracking-img-04.png) 