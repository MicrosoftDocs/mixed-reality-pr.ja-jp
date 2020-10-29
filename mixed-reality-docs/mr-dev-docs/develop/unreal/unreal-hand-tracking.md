---
title: Unreal での手の追跡
description: Unreal でハンドトラッキングを使用する方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、手動追跡、Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、Mixed Reality、開発、機能、ドキュメント、ガイド、ホログラム、ゲーム開発
ms.openlocfilehash: 5bc120f802c2160282befd1ce6cb8025be21cbaa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683082"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="8e6db-104">Unreal での手の追跡</span><span class="sxs-lookup"><span data-stu-id="8e6db-104">Hand tracking in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="8e6db-105">概要</span><span class="sxs-lookup"><span data-stu-id="8e6db-105">Overview</span></span>

<span data-ttu-id="8e6db-106">ハンドトラッキングシステムは、ユーザーのてのひらとフィンガーを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-106">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="8e6db-107">コード内で使用するすべての指、パーム全体、およびハンドジェスチャの位置と回転を取得できます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-107">You can get the position and rotation of every finger, the entire palm, and even hand gestures to use in your code.</span></span> 

## <a name="hand-pose"></a><span data-ttu-id="8e6db-108">手の形</span><span class="sxs-lookup"><span data-stu-id="8e6db-108">Hand Pose</span></span>

<span data-ttu-id="8e6db-109">手の形で、アクティブなユーザーの手と指を追跡し、それを入力として使用できます。これは、ブループリントと C++ を通じてアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-109">Hand pose lets you track the hands and fingers of the active user and use it as input, which you can access through Blueprints and C++.</span></span> <span data-ttu-id="8e6db-110">詳細な技術情報については、Unreal の「 [Windows.](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) ..」 API を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e6db-110">You can find more technical details in Unreal's [Windows.Perception.People.HandPose](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) API.</span></span> <span data-ttu-id="8e6db-111">Unreal API は、Unreal エンジンとの間で同期されたティックを使用して、データを座標系として送信します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

### <a name="understanding-the-bone-hierarchy"></a><span data-ttu-id="8e6db-112">ボーン階層について</span><span class="sxs-lookup"><span data-stu-id="8e6db-112">Understanding the bone hierarchy</span></span>

<span data-ttu-id="8e6db-113">この `EWMRHandKeypoint` 列挙型は、手のボーン階層を記述します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-113">The `EWMRHandKeypoint` enum describes the Hand’s bone hierarchy.</span></span> <span data-ttu-id="8e6db-114">ブループリントに記載されている各ハンドキーポイントを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-114">You can find each hand keypoint listed in your Blueprints:</span></span>

![ハンドキーポイント BP](images/hand-keypoint-bp.png)

<span data-ttu-id="8e6db-116">完全な C++ 列挙型を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-116">The full C++ enum is listed below:</span></span>
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

<span data-ttu-id="8e6db-117">各列挙型のケースの数値は、 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) テーブルで確認できます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-117">You can find the numerical values for each enum case in the [Windows.Perception.People.HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) table.</span></span> <span data-ttu-id="8e6db-118">次の図は、一致する列挙型のケースを持つ完全なレイアウトを示しています。</span><span class="sxs-lookup"><span data-stu-id="8e6db-118">The entire hand pose layout with matching enum cases is shown in the image below:</span></span>

![手スケルトン](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a><span data-ttu-id="8e6db-120">ハンドトラッキングのサポート</span><span class="sxs-lookup"><span data-stu-id="8e6db-120">Supporting Hand Tracking</span></span>

<span data-ttu-id="8e6db-121">手動追跡機能を追加することによって、ブループリントで **手動追跡を** 使用することができます **> Windows Mixed Reality** :</span><span class="sxs-lookup"><span data-stu-id="8e6db-121">You can use hand tracking in Blueprints by adding **Supports Hand Tracking** from **Hand Tracking > Windows Mixed Reality** :</span></span>

![ハンドトラッキング BP](images/unreal/hand-tracking-bp.png)

<span data-ttu-id="8e6db-123">この関数は `true` 、デバイスでハンドトラッキングがサポートされている場合、および `false` ハンドトラッキングが使用できない場合にを返します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-123">This function returns `true` if hand tracking is supported on the device and `false` if hand tracking is not available.</span></span>

![ハンドトラッキング BP のサポート](images/unreal/supports-hand-tracking-bp.png)

<span data-ttu-id="8e6db-125">C++:</span><span class="sxs-lookup"><span data-stu-id="8e6db-125">C++:</span></span> 

<span data-ttu-id="8e6db-126">`WindowsMixedRealityHandTrackingFunctionLibrary.h` を含めます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-126">Include `WindowsMixedRealityHandTrackingFunctionLibrary.h`.</span></span>

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a><span data-ttu-id="8e6db-127">ハンドトラッキングの取得</span><span class="sxs-lookup"><span data-stu-id="8e6db-127">Getting Hand Tracking</span></span>
<span data-ttu-id="8e6db-128">**GetHandJointTransform** を使用して、空間データを手動で返すことができます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-128">You can use **GetHandJointTransform** to return spatial data from the hand.</span></span> <span data-ttu-id="8e6db-129">データはすべてのフレームを更新しますが、フレーム内にいる場合は、返された値がキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-129">The data updates every frame, but if you're inside a frame the returned values are cached.</span></span> <span data-ttu-id="8e6db-130">パフォーマンス上の理由から、この関数では大きなロジックを使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="8e6db-130">It's not recommended to have heavy logic in this function for performance reasons.</span></span> 

![ハンドジョイント変換の取得](images/unreal/get-hand-joint-transform.png)
 
<span data-ttu-id="8e6db-132">C++:</span><span class="sxs-lookup"><span data-stu-id="8e6db-132">C++:</span></span>
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

<span data-ttu-id="8e6db-133">関数パラメーターの内訳:</span><span class="sxs-lookup"><span data-stu-id="8e6db-133">Function parameter breakdown:</span></span>

* <span data-ttu-id="8e6db-134">**手** : ユーザーの左側または右側</span><span class="sxs-lookup"><span data-stu-id="8e6db-134">**Hand** – an be the left or right hand of the user</span></span>
* <span data-ttu-id="8e6db-135">**Keypoint** –ハンドのボーンです。</span><span class="sxs-lookup"><span data-stu-id="8e6db-135">**Keypoint** – the bone of the hand.</span></span> 
* <span data-ttu-id="8e6db-136">**Transform** –ボーンの基本の座標と向きを調整します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-136">**Transform** – coordinates and orientation of bone’s base.</span></span> <span data-ttu-id="8e6db-137">次のボーンのベースを要求して、ボーンの終点の変換データを取得できます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-137">You can request the base of the next bone to get the transform data for the end of a bone.</span></span> <span data-ttu-id="8e6db-138">特別なヒントのボーンは、distal の終わりを示します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-138">A special Tip bone gives end of distal.</span></span> 
* <span data-ttu-id="8e6db-139">**Radius** : ボーンのベースの半径。</span><span class="sxs-lookup"><span data-stu-id="8e6db-139">**Radius** — radius of the base of the bone.</span></span>
* <span data-ttu-id="8e6db-140">**戻り値** -ボーンがこのフレームを追跡している場合は true、ボーンが追跡されていない場合は false。</span><span class="sxs-lookup"><span data-stu-id="8e6db-140">**Return Value** — true if the bone is tracked this frame, false if the bone is not tracked.</span></span>

## <a name="hand-live-link-animation"></a><span data-ttu-id="8e6db-141">ハンドライブリンクアニメーション</span><span class="sxs-lookup"><span data-stu-id="8e6db-141">Hand Live Link Animation</span></span>
<span data-ttu-id="8e6db-142">[Live Link プラグイン](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)を使用して、手の形でアニメーションに公開されます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-142">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="8e6db-143">Windows Mixed Reality とライブリンクプラグインが有効になっている場合:</span><span class="sxs-lookup"><span data-stu-id="8e6db-143">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span> 
1. <span data-ttu-id="8e6db-144">[ **ウィンドウ > ライブリンク** ] を選択して、ライブリンクエディターウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-144">Select **Window > Live Link** to open the Live Link editor window.</span></span> 
2. <span data-ttu-id="8e6db-145">[ **ソース** ] をクリックし、[ **Windows Mixed Reality ハンドトラッキングソース** を有効にする]</span><span class="sxs-lookup"><span data-stu-id="8e6db-145">Click **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![ライブリンクのソース](images/unreal/live-link-source.png)
 
<span data-ttu-id="8e6db-147">ソースを有効にし、アニメーションのアセットを開くと、[ **プレビューシーン** ] タブの [ **アニメーション** ] セクションが表示されなくなります (詳細については、「ライブリンクのドキュメント」を参照してください。プラグインがベータ版であるため、プロセスは後で変更される可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="8e6db-147">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options (the details are in Unreal’s Live Link documentation - as the plugin is in beta, the process may change later).</span></span>

![ライブリンクアニメーション](images/unreal/live-link-animation.png)
 
<span data-ttu-id="8e6db-149">ハンドアニメーション階層は、の場合と同じ `EWMRHandKeypoint` です。</span><span class="sxs-lookup"><span data-stu-id="8e6db-149">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="8e6db-150">アニメーションは、 **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** を使用して再ターゲットできます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-150">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** :</span></span>

![ライブリンクアニメーション2](images/unreal/live-link-animation2.png)
 
<span data-ttu-id="8e6db-152">また、エディターでサブクラス化することもできます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-152">It can also be subclassed in the editor:</span></span>

![ライブリンクの再マップ](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a><span data-ttu-id="8e6db-154">手メッシュデータへのアクセス</span><span class="sxs-lookup"><span data-stu-id="8e6db-154">Accessing Hand Mesh Data</span></span>

![手動メッシュ](images/unreal/hand-mesh.png)

<span data-ttu-id="8e6db-156">手作業のメッシュデータにアクセスするには、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="8e6db-156">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="8e6db-157">**Arsessionconfig** 資産を選択し、 **AR の設定-> 世界のマッピング** 設定を展開して、[追跡された **ジオメトリからメッシュデータを生成** する] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="8e6db-157">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry** .</span></span> 

<span data-ttu-id="8e6db-158">既定のメッシュパラメーターを次に示します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-158">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="8e6db-159">遮蔽にメッシュデータを使用する</span><span class="sxs-lookup"><span data-stu-id="8e6db-159">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="8e6db-160">メッシュデータの競合を生成する</span><span class="sxs-lookup"><span data-stu-id="8e6db-160">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="8e6db-161">メッシュデータの Nav メッシュを生成します</span><span class="sxs-lookup"><span data-stu-id="8e6db-161">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="8e6db-162">ワイヤーフレームでメッシュデータをレンダリングする–生成されたメッシュを示すデバッグパラメーター</span><span class="sxs-lookup"><span data-stu-id="8e6db-162">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="8e6db-163">これらのパラメーター値は、空間マッピングメッシュと手動メッシュの既定値として使用されます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-163">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="8e6db-164">これらは、任意のメッシュのブループリントまたはコードでいつでも変更できます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-164">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="8e6db-165">C++ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="8e6db-165">C++ API Reference</span></span> 
<span data-ttu-id="8e6db-166">`EEARObjectClassification`を使用すると、すべての追跡可能なオブジェクトで手動メッシュ値を検索できます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-166">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

<span data-ttu-id="8e6db-167">システムによって追跡可能なオブジェクト (手メッシュを含む) が検出されると、次のデリゲートが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-167">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span> 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

<span data-ttu-id="8e6db-168">デリゲートハンドラーが以下の関数シグネチャに従うことを確認します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-168">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="8e6db-169">メッシュデータには、を使用してアクセスでき  `UARTrackedGeometry::GetUnderlyingMesh` ます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-169">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a><span data-ttu-id="8e6db-170">ブループリント API リファレンス</span><span class="sxs-lookup"><span data-stu-id="8e6db-170">Blueprint API Reference</span></span>

<span data-ttu-id="8e6db-171">ブループリントを使用するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="8e6db-171">In order to work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="8e6db-172">**ARTrackableNotify** コンポーネントをブループリントアクターに追加する</span><span class="sxs-lookup"><span data-stu-id="8e6db-172">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)
 
2. <span data-ttu-id="8e6db-174">[ **詳細** ] パネルにアクセスし、[ **イベント** ] セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-174">Go to the **Details** panel and expand the **Events** section.</span></span> 

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)
 
3. <span data-ttu-id="8e6db-176">イベントグラフ内の次のノードを使用して、追跡したジオメトリの追加/更新/削除を上書きします。</span><span class="sxs-lookup"><span data-stu-id="8e6db-176">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![ARTrackable 通知で](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a><span data-ttu-id="8e6db-178">手の線</span><span class="sxs-lookup"><span data-stu-id="8e6db-178">Hand Rays</span></span>

<span data-ttu-id="8e6db-179">[SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API を公開する C++ とブループリントの両方で、ポインティングデバイスとしてハンドレイを使用できます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-179">You can use a hand ray as a pointing device in both C++ and Blueprints, which exposes the [Windows.UI.Input.Spatial.SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API.</span></span>

<span data-ttu-id="8e6db-180">すべての関数の結果がすべてのフレームに変更されるため、すべての関数が呼び出し可能になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="8e6db-180">It’s important to mention that since the results of all the functions change every frame, they're all made callable.</span></span> <span data-ttu-id="8e6db-181">純粋関数と純粋でない関数、または呼び出し可能関数の詳細については、「[関数](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)のブループリントユーザー guid」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e6db-181">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)</span></span>

<span data-ttu-id="8e6db-182">ブループリントを使用するには、 **Windows Mixed Reality HMD** で任意のアクションを検索します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-182">To use Hand Rays in Blueprints, search for any of the actions under **Windows Mixed Reality HMD** :</span></span>

![ハンド光線 BP](images/unreal/hand-rays-bp.png)
 
<span data-ttu-id="8e6db-184">C++ でこれらのファイルにアクセスするには、 `WindowsMixedRealityFunctionLibrary.h` 呼び出し元のコードファイルの先頭にを含めます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-184">To access them in C++, include `WindowsMixedRealityFunctionLibrary.h` to the top of your calling code file.</span></span>

### <a name="enum"></a><span data-ttu-id="8e6db-185">列挙型</span><span class="sxs-lookup"><span data-stu-id="8e6db-185">Enum</span></span>
<span data-ttu-id="8e6db-186">また、[ **Ehmdinputコントローラー** ] の下にある入力ケースにアクセスできます。このボタンは、ブループリントで使用できます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-186">You also have access to input cases under **EHMDInputControllerButtons** , which can be used in Blueprints:</span></span>

![入力コントローラーボタン](images/unreal/input-controller-buttons.png)

<span data-ttu-id="8e6db-188">C++ でのアクセスには、 `EHMDInputControllerButtons` 列挙型クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-188">For access in C++, use the `EHMDInputControllerButtons` enum class:</span></span>
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

<span data-ttu-id="8e6db-189">次に、該当する2つの列挙型ケースの内訳を示します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-189">Below is a breakdown of the two applicable enum cases:</span></span>
* <span data-ttu-id="8e6db-190">**Select** -ユーザーがトリガーした選択イベント。</span><span class="sxs-lookup"><span data-stu-id="8e6db-190">**Select** - User triggered Select event.</span></span> 
    * <span data-ttu-id="8e6db-191">このイベントは、外気タップ、宝石、およびコミットによって HoloLens 2 でトリガーされます。または、 [音声入力](unreal-voice-input.md) を有効にした "選択" を言います。</span><span class="sxs-lookup"><span data-stu-id="8e6db-191">The event can be triggered in HoloLens 2 by air-tap, gaze and commit, or by saying “Select” with [voice input](unreal-voice-input.md) enabled.</span></span> 
* <span data-ttu-id="8e6db-192">ユーザーによってトリガーされるイベントを **把握** します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-192">**Grasp** - User triggered Grasp event.</span></span> 
    * <span data-ttu-id="8e6db-193">このイベントは、ホログラムでユーザーの指を閉じることで、HoloLens 2 でトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-193">This event can be triggered in HoloLens 2 by closing the user’s fingers on a hologram.</span></span> 

<span data-ttu-id="8e6db-194">次に示す列挙体を使用して、C++ でのハンドメッシュの追跡状態にアクセスでき `EHMDTrackingStatus` ます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-194">You can access the tracking status of your hand mesh in C++ through the `EHMDTrackingStatus` enum shown below:</span></span>

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

<span data-ttu-id="8e6db-195">次に、該当する2つの列挙型ケースの内訳を示します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-195">Below is a breakdown of the two applicable enum cases:</span></span>
* <span data-ttu-id="8e6db-196">**Nottracked** –-ハンドは表示されません</span><span class="sxs-lookup"><span data-stu-id="8e6db-196">**NotTracked** –- the hand isn’t visible</span></span>
* <span data-ttu-id="8e6db-197">**追跡** –ハンドは完全に追跡されます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-197">**Tracked** –- the hand is fully tracked</span></span>

### <a name="struct"></a><span data-ttu-id="8e6db-198">構造体</span><span class="sxs-lookup"><span data-stu-id="8e6db-198">Struct</span></span>
<span data-ttu-id="8e6db-199">PointerPoseInfo 構造体は、次のような手作業のデータに関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-199">The PointerPoseInfo struct can give you information on the following hand data:</span></span>
* <span data-ttu-id="8e6db-200">**Origin** –ハンドオリジン</span><span class="sxs-lookup"><span data-stu-id="8e6db-200">**Origin** – origin of the hand</span></span>
* <span data-ttu-id="8e6db-201">**方向** –ハンドの方向</span><span class="sxs-lookup"><span data-stu-id="8e6db-201">**Direction** – direction of the hand</span></span>
* <span data-ttu-id="8e6db-202">**アップ** (手動)</span><span class="sxs-lookup"><span data-stu-id="8e6db-202">**Up** – up vector of the hand</span></span>
* <span data-ttu-id="8e6db-203">**方向** -方向の四元数</span><span class="sxs-lookup"><span data-stu-id="8e6db-203">**Orientation** – orientation quaternion</span></span> 
* <span data-ttu-id="8e6db-204">**ステータスの追跡** -現在の追跡状態</span><span class="sxs-lookup"><span data-stu-id="8e6db-204">**Tracking Status** – current tracking status</span></span>

<span data-ttu-id="8e6db-205">これには、次に示すように、ブループリントを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-205">You can access this through Blueprints, as shown below:</span></span>

![ポインターのポーズ情報 BP](images/unreal/pointer-pose-info-bp.png)

<span data-ttu-id="8e6db-207">C++ の場合:</span><span class="sxs-lookup"><span data-stu-id="8e6db-207">Or with C++:</span></span>

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

### <a name="functions"></a><span data-ttu-id="8e6db-208">関数</span><span class="sxs-lookup"><span data-stu-id="8e6db-208">Functions</span></span>

<span data-ttu-id="8e6db-209">次に示すすべての関数は、継続的な監視を可能にするすべてのフレームに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-209">All of the functions listed below can be called on every frame, which allows continuous monitoring.</span></span> 

1. <span data-ttu-id="8e6db-210">**ポインターの取得の詳細** 情報は、現在のフレームにおけるハンドレイの方向に関する完全な情報を返します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-210">**Get Pointer Pose Info** returns complete information about the hand ray direction in the current frame.</span></span> 

<span data-ttu-id="8e6db-211">建築</span><span class="sxs-lookup"><span data-stu-id="8e6db-211">Blueprint:</span></span>

![ポインターの表示情報の取得](images/unreal/get-pointer-pose-info.png)

<span data-ttu-id="8e6db-213">C++:</span><span class="sxs-lookup"><span data-stu-id="8e6db-213">C++:</span></span> 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. <span data-ttu-id="8e6db-214">**Grasped** は、現在のフレームに Grasped がある場合に true を返します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-214">**Is Grasped** returns true if the hand is grasped in the current frame.</span></span>

<span data-ttu-id="8e6db-215">建築</span><span class="sxs-lookup"><span data-stu-id="8e6db-215">Blueprint:</span></span>

![Grasped BP](images/unreal/is-grasped-bp.png)

<span data-ttu-id="8e6db-217">C++:</span><span class="sxs-lookup"><span data-stu-id="8e6db-217">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. <span data-ttu-id="8e6db-218">**Select 押さ** れた場合、ユーザーが現在のフレームで select をトリガーした場合は true を返します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-218">**Is Select Pressed** returns true if the user triggered Select in the current frame.</span></span>

<span data-ttu-id="8e6db-219">建築</span><span class="sxs-lookup"><span data-stu-id="8e6db-219">Blueprint:</span></span>

![選択された BP (BP)](images/unreal/is-select-pressed-bp.png)

<span data-ttu-id="8e6db-221">C++:</span><span class="sxs-lookup"><span data-stu-id="8e6db-221">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. <span data-ttu-id="8e6db-222">現在のフレームでイベントまたはボタンがトリガーされた場合、 **ボタンがクリックされる** と true が返されます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-222">**Is Button Clicked** returns true if the event or button is triggered in the current frame.</span></span>

<span data-ttu-id="8e6db-223">建築</span><span class="sxs-lookup"><span data-stu-id="8e6db-223">Blueprint:</span></span>

![ボタンが BP をクリックしました](images/unreal/is-button-clicked-bp.png)

<span data-ttu-id="8e6db-225">C++:</span><span class="sxs-lookup"><span data-stu-id="8e6db-225">C++:</span></span>
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. <span data-ttu-id="8e6db-226">**コントローラー追跡状態の取得** は、現在のフレームの追跡状態を返します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-226">**Get Controller Tracking Status** returns the tracking status in the current frame.</span></span>

<span data-ttu-id="8e6db-227">建築</span><span class="sxs-lookup"><span data-stu-id="8e6db-227">Blueprint:</span></span>

![コントローラー追跡ステータス BP の取得](images/unreal/get-controller-tracking-status-bp.png)

<span data-ttu-id="8e6db-229">C++:</span><span class="sxs-lookup"><span data-stu-id="8e6db-229">C++:</span></span>
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a><span data-ttu-id="8e6db-230">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="8e6db-230">Gestures</span></span>

<span data-ttu-id="8e6db-231">Hololens 2 では、空間ジェスチャを追跡できます。これは、これらのジェスチャを入力としてキャプチャできることを意味します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-231">The Hololens 2 can track spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="8e6db-232">ジェスチャの詳細については、「 [HoloLens 2 の基本的な使用方法](https://docs.microsoft.com/hololens/hololens2-basic-usage) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8e6db-232">You can find more details about gestures are the [HoloLens 2 Basic Usage](https://docs.microsoft.com/hololens/hololens2-basic-usage) document.</span></span>

<span data-ttu-id="8e6db-233">のブループリント関数は、呼び出し元のコードファイルにを追加することで、 **Windows Mixed Reality 空間入力** と C++ 関数の下に `WindowsMixedRealitySpatialInputFunctionLibrary.h` あります。</span><span class="sxs-lookup"><span data-stu-id="8e6db-233">You can find the Blueprint function in under **Windows Mixed Reality Spatial Input** , and the C++ function by adding `WindowsMixedRealitySpatialInputFunctionLibrary.h` in your calling code file.</span></span>

![キャプチャジェスチャ](images/unreal/capture-gestures.png)

### <a name="enum"></a><span data-ttu-id="8e6db-235">列挙型</span><span class="sxs-lookup"><span data-stu-id="8e6db-235">Enum</span></span>
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
<span data-ttu-id="8e6db-236">建築</span><span class="sxs-lookup"><span data-stu-id="8e6db-236">Blueprint:</span></span> 

![ジェスチャの種類](images/unreal/gesture-type.png)

<span data-ttu-id="8e6db-238">C++:</span><span class="sxs-lookup"><span data-stu-id="8e6db-238">C++:</span></span>
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a><span data-ttu-id="8e6db-239">機能</span><span class="sxs-lookup"><span data-stu-id="8e6db-239">Function</span></span>
<span data-ttu-id="8e6db-240">ジェスチャのキャプチャを有効または無効にするには、関数を使用 `CaptureGestures` します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-240">You can enable and disable gesture capture with the `CaptureGestures` function.</span></span> <span data-ttu-id="8e6db-241">有効なジェスチャによって入力イベントが発生した場合、この関数はジェスチャキャプチャが成功した場合はを返し、エラーが発生した場合はを返し `true` `false` ます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-241">When an enabled gesture fires input events, the function returns `true` if gesture capture succeeded, and `false` if there's an error.</span></span>

<span data-ttu-id="8e6db-242">建築</span><span class="sxs-lookup"><span data-stu-id="8e6db-242">Blueprint:</span></span>

![キャプチャジェスチャ BP](images/unreal/capture-gestures-bp.png)

<span data-ttu-id="8e6db-244">C++:</span><span class="sxs-lookup"><span data-stu-id="8e6db-244">C++:</span></span>
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

<span data-ttu-id="8e6db-245">次に示すのは、[ブループリント] と [C++: キーイベント] で確認できる主要なイベントです。 ![](images/unreal/key-events.png)</span><span class="sxs-lookup"><span data-stu-id="8e6db-245">The following are key events, which you can find in Blueprints and C++: ![Key Events](images/unreal/key-events.png)</span></span>

![主要イベント2](images/unreal/key-events2.png)
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

## <a name="next-development-checkpoint"></a><span data-ttu-id="8e6db-247">次回の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="8e6db-247">Next Development Checkpoint</span></span>

<span data-ttu-id="8e6db-248">デプロイされていない実際のチェックポイントの旅に従っている場合、MRTK コアのビルディングブロックを調べています。</span><span class="sxs-lookup"><span data-stu-id="8e6db-248">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="8e6db-249">ここから、次のビルディングブロックに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-249">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="8e6db-250">ローカル空間アンカー</span><span class="sxs-lookup"><span data-stu-id="8e6db-250">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="8e6db-251">または、Mixed Reality プラットフォームの機能と Api に移動します。</span><span class="sxs-lookup"><span data-stu-id="8e6db-251">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8e6db-252">HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="8e6db-252">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="8e6db-253">いつでも、 [Unreal の開発チェックポイント](unreal-development-overview.md#2-core-building-blocks) に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="8e6db-253">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>