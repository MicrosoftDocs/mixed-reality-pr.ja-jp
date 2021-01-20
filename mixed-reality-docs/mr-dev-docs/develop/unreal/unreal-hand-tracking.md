---
title: Unreal での手の追跡
description: Unreal mixed reality アプリで、入力、ポーズ、ハンドメッシュ、ライブリンクアニメーションをハンドトラッキングする方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、手動追跡、Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、Mixed Reality、開発、機能、ドキュメント、ガイド、ホログラム、ゲーム開発、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: 1888258321af978ca52623008193e6dae94833a8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581118"
---
# <a name="hand-tracking-in-unreal"></a><span data-ttu-id="9983d-104">Unreal での手の追跡</span><span class="sxs-lookup"><span data-stu-id="9983d-104">Hand tracking in Unreal</span></span>

<span data-ttu-id="9983d-105">ハンドトラッキングシステムは、ユーザーのてのひらとフィンガーを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="9983d-105">The hand tracking system uses a person’s palms and fingers as input.</span></span> <span data-ttu-id="9983d-106">各指の位置と回転に関するデータ、palm 全体、およびハンドジェスチャを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9983d-106">Data on position and rotation of every finger, the entire palm, and hand gestures is available.</span></span> <span data-ttu-id="9983d-107">Unreal 4.26 以降、ハンドトラッキングは Unreal HeadMountedDisplay プラグインに基づいており、すべての XR プラットフォームとデバイスで共通の API を使用します。</span><span class="sxs-lookup"><span data-stu-id="9983d-107">Starting in Unreal 4.26, hand tracking is based on the Unreal HeadMountedDisplay plugin and uses a common API across all XR platforms and devices.</span></span> <span data-ttu-id="9983d-108">Windows Mixed Reality と OpenXR システムの機能は同じです。</span><span class="sxs-lookup"><span data-stu-id="9983d-108">Functionality is the same for both Windows Mixed Reality and OpenXR systems.</span></span>

## <a name="hand-pose"></a><span data-ttu-id="9983d-109">手の形</span><span class="sxs-lookup"><span data-stu-id="9983d-109">Hand pose</span></span>

<span data-ttu-id="9983d-110">手の形では、ユーザーの手と指を入力として追跡し、使用することができます。これは、ブループリントと C++ の両方でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9983d-110">Hand pose lets you track and use the hands and fingers of your users as input, which can be accessed in both Blueprints and C++.</span></span> <span data-ttu-id="9983d-111">Unreal API は、Unreal エンジンとの間で同期されたティックを使用して、データを座標系として送信します。</span><span class="sxs-lookup"><span data-stu-id="9983d-111">The Unreal API sends the data as a coordinate system, with ticks synchronized with the Unreal Engine.</span></span>

![手スケルトン](../native/images/hand-skeleton.png)

[!INCLUDE[](includes/tabs-tracking-hand-pose.md)]

## <a name="hand-live-link-animation"></a><span data-ttu-id="9983d-113">ハンドライブリンクアニメーション</span><span class="sxs-lookup"><span data-stu-id="9983d-113">Hand Live Link Animation</span></span>

<span data-ttu-id="9983d-114">[Live Link プラグイン](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)を使用して、手の形でアニメーションに公開されます。</span><span class="sxs-lookup"><span data-stu-id="9983d-114">Hand poses are exposed to Animation using the [Live Link plugin](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html).</span></span>

<span data-ttu-id="9983d-115">Windows Mixed Reality とライブリンクプラグインが有効になっている場合:</span><span class="sxs-lookup"><span data-stu-id="9983d-115">If the Windows Mixed Reality and Live Link plugins are enabled:</span></span>
1. <span data-ttu-id="9983d-116">[ **ウィンドウ > ライブリンク** ] を選択して、ライブリンクエディターウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="9983d-116">Select **Window > Live Link** to open the Live Link editor window.</span></span>
2. <span data-ttu-id="9983d-117">**ソース** を選択し、 **Windows Mixed Reality の追跡ソース** を有効にする</span><span class="sxs-lookup"><span data-stu-id="9983d-117">Select **Source** and enable **Windows Mixed Reality Hand Tracking Source**</span></span>

![ライブリンクのソース](images/unreal/live-link-source.png)

<span data-ttu-id="9983d-119">ソースを有効にし、アニメーション資産を開いた後、[**プレビューシーン**] タブの [**アニメーション**] セクションを展開すると、追加のオプションが表示されません。</span><span class="sxs-lookup"><span data-stu-id="9983d-119">After you enable the source and open an animation asset, expand the **Animation** section in the **Preview Scene** tab too see additional options.</span></span>

![ライブリンクアニメーション](images/unreal/live-link-animation.png)

<span data-ttu-id="9983d-121">ハンドアニメーション階層は、の場合と同じ `EWMRHandKeypoint` です。</span><span class="sxs-lookup"><span data-stu-id="9983d-121">The hand animation hierarchy is the same as in `EWMRHandKeypoint`.</span></span> <span data-ttu-id="9983d-122">アニメーションは、 **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** を使用して再ターゲットできます。</span><span class="sxs-lookup"><span data-stu-id="9983d-122">Animation can be retargeted using **WindowsMixedRealityHandTrackingLiveLinkRemapAsset**:</span></span>

![ライブリンクアニメーション2](images/unreal/live-link-animation2.png)

<span data-ttu-id="9983d-124">また、エディターでサブクラス化することもできます。</span><span class="sxs-lookup"><span data-stu-id="9983d-124">It can also be subclassed in the editor:</span></span>

![ライブリンクの再マップ](images/unreal/live-link-remap.png)

## <a name="hand-mesh"></a><span data-ttu-id="9983d-126">手動メッシュ</span><span class="sxs-lookup"><span data-stu-id="9983d-126">Hand Mesh</span></span>

### <a name="hand-mesh-as-a-tracked-geometry"></a><span data-ttu-id="9983d-127">追跡ジオメトリとしてのハンドメッシュ</span><span class="sxs-lookup"><span data-stu-id="9983d-127">Hand Mesh as a Tracked Geometry</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9983d-128">OpenXR の追跡されたジオメトリとして手メッシュを取得するには、[**有効な追跡ジオメトリ** での **ハンドメッシュを使用** する。</span><span class="sxs-lookup"><span data-stu-id="9983d-128">Getting hand meshes as a tracked geometry in OpenXR requires you to call **Set Use Hand Mesh** with **Enabled Tracking Geometry**.</span></span>

<span data-ttu-id="9983d-129">このモードを有効にするには **、次のように\*\*\*\*設定** する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9983d-129">To enable that mode you should call **Set Use Hand Mesh** with **Enabled Tracking Geometry**:</span></span>

![イベント開始再生のブループリントを設定して、有効な追跡ジオメトリモードでハンドメッシュ関数を使用する](images/unreal-hand-tracking-img-08.png)

> [!NOTE]
> <span data-ttu-id="9983d-131">両方のモードを同時に有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="9983d-131">It’s not possible for both modes to be enabled at the same time.</span></span> <span data-ttu-id="9983d-132">1つを有効にした場合、もう一方は自動的に無効になります。</span><span class="sxs-lookup"><span data-stu-id="9983d-132">If you enable one, the other is automatically disabled.</span></span>

### <a name="accessing-hand-mesh-data"></a><span data-ttu-id="9983d-133">手メッシュデータへのアクセス</span><span class="sxs-lookup"><span data-stu-id="9983d-133">Accessing Hand Mesh Data</span></span>

![手動メッシュ](images/unreal/hand-mesh.png)

<span data-ttu-id="9983d-135">手作業のメッシュデータにアクセスするには、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="9983d-135">Before you can access hand mesh data, you'll need to:</span></span>
- <span data-ttu-id="9983d-136">**Arsessionconfig** 資産を選択し、 **AR の設定-> 世界のマッピング** 設定を展開して、[追跡された **ジオメトリからメッシュデータを生成** する] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="9983d-136">Select your **ARSessionConfig** asset, expand the **AR Settings -> World Mapping** settings, and check **Generate Mesh Data from Tracked Geometry**.</span></span>

<span data-ttu-id="9983d-137">既定のメッシュパラメーターを次に示します。</span><span class="sxs-lookup"><span data-stu-id="9983d-137">Below are the default mesh parameters:</span></span>

1.  <span data-ttu-id="9983d-138">遮蔽にメッシュデータを使用する</span><span class="sxs-lookup"><span data-stu-id="9983d-138">Use Mesh Data for Occlusion</span></span>
2.  <span data-ttu-id="9983d-139">メッシュデータの競合を生成する</span><span class="sxs-lookup"><span data-stu-id="9983d-139">Generate Collision for Mesh Data</span></span>
3.  <span data-ttu-id="9983d-140">メッシュデータの Nav メッシュを生成します</span><span class="sxs-lookup"><span data-stu-id="9983d-140">Generate Nav Mesh for Mesh Data</span></span>
4.  <span data-ttu-id="9983d-141">ワイヤーフレームでメッシュデータをレンダリングする–生成されたメッシュを示すデバッグパラメーター</span><span class="sxs-lookup"><span data-stu-id="9983d-141">Render Mesh Data in Wireframe – debug parameter that shows generated mesh</span></span>

<span data-ttu-id="9983d-142">これらのパラメーター値は、空間マッピングメッシュと手動メッシュの既定値として使用されます。</span><span class="sxs-lookup"><span data-stu-id="9983d-142">These parameter values are used as the spatial mapping mesh and hand mesh defaults.</span></span> <span data-ttu-id="9983d-143">これらは、任意のメッシュのブループリントまたはコードでいつでも変更できます。</span><span class="sxs-lookup"><span data-stu-id="9983d-143">You can change them at any time in Blueprints or code for any mesh.</span></span>

### <a name="c-api-reference"></a><span data-ttu-id="9983d-144">C++ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="9983d-144">C++ API Reference</span></span>
<span data-ttu-id="9983d-145">`EEARObjectClassification`を使用すると、すべての追跡可能なオブジェクトで手動メッシュ値を検索できます。</span><span class="sxs-lookup"><span data-stu-id="9983d-145">Use `EEARObjectClassification` to find hand mesh values in all trackable objects.</span></span>
```cpp
enum class EARObjectClassification : uint8
{
    // Other types
    HandMesh,
};
```

<span data-ttu-id="9983d-146">システムによって追跡可能なオブジェクト (手メッシュを含む) が検出されると、次のデリゲートが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9983d-146">The following delegates are called when the system detects any trackable object, including a hand mesh.</span></span>

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

<span data-ttu-id="9983d-147">デリゲートハンドラーが以下の関数シグネチャに従うことを確認します。</span><span class="sxs-lookup"><span data-stu-id="9983d-147">Make sure your delegate handlers follow the function signature below:</span></span>

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

<span data-ttu-id="9983d-148">メッシュデータには、を使用してアクセスでき  `UARTrackedGeometry::GetUnderlyingMesh` ます。</span><span class="sxs-lookup"><span data-stu-id="9983d-148">You can access mesh data through the  `UARTrackedGeometry::GetUnderlyingMesh`:</span></span>

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```

### <a name="blueprint-api-reference"></a><span data-ttu-id="9983d-149">ブループリント API リファレンス</span><span class="sxs-lookup"><span data-stu-id="9983d-149">Blueprint API Reference</span></span>

<span data-ttu-id="9983d-150">ブループリントを使用するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="9983d-150">To work with Hand Meshes in Blueprints:</span></span>
1. <span data-ttu-id="9983d-151">**ARTrackableNotify** コンポーネントをブループリントアクターに追加する</span><span class="sxs-lookup"><span data-stu-id="9983d-151">Add an **ARTrackableNotify** Component to a Blueprint actor</span></span>

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)

2. <span data-ttu-id="9983d-153">[ **詳細** ] パネルにアクセスし、[ **イベント** ] セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="9983d-153">Go to the **Details** panel and expand the **Events** section.</span></span>

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)

3. <span data-ttu-id="9983d-155">イベントグラフ内の次のノードを使用して、追跡したジオメトリの追加/更新/削除を上書きします。</span><span class="sxs-lookup"><span data-stu-id="9983d-155">Overwrite On Add/Update/Remove Tracked Geometry with the following nodes in your Event Graph:</span></span>

![ARTrackable 通知で](images/unreal/on-artrackable-notify.png)

### <a name="hand-mesh-visualization-in-openxr"></a><span data-ttu-id="9983d-157">OpenXR での手メッシュの視覚化</span><span class="sxs-lookup"><span data-stu-id="9983d-157">Hand Mesh visualization in OpenXR</span></span>

<span data-ttu-id="9983d-158">手動メッシュを視覚化するには、エピックの XRVisualization プラグインを [Microsoft OpenXR プラグイン](https://github.com/microsoft/Microsoft-OpenXR-Unreal)と共に使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9983d-158">The recommended way to visualize hand mesh is to use Epic’s XRVisualization plugin together with the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span> 

<span data-ttu-id="9983d-159">次に、ブループリントエディターで、次のように、**有効な XRVisualization** をパラメーターとして使用して、 [Microsoft OpenXR Plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal)の **Set use ハンドメッシュ** 関数を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9983d-159">Then in the blueprint editor, you should use **Set Use Hand Mesh** function from the [Microsoft OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal) with **Enabled XRVisualization** as a parameter:</span></span>

![イベント開始再生のブループリントを設定して、有効な xrvisualization モードでハンドメッシュ関数を使用する](images/unreal-hand-tracking-img-05.png)

<span data-ttu-id="9983d-161">レンダリングプロセスを管理するには、XRVisualization から **レンダーモーションコントローラー** を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9983d-161">To manage the rendering process, you should use **Render Motion Controller** from XRVisualization:</span></span>

![レンダーモーションコントローラー関数に接続された、motion controller データ関数のブループリント](images/unreal-hand-tracking-img-06.png)

<span data-ttu-id="9983d-163">結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9983d-163">The result:</span></span>

![人間の手で店舗たデジタルハンドの画像](images/unreal-hand-tracking-img-07.png) 

<span data-ttu-id="9983d-165">カスタムシェーダーを使用したハンドメッシュの描画など、さらに複雑なものが必要な場合は、メッシュを追跡対象のジオメトリとして取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9983d-165">If you need anything more complicated, such as drawing a hand mesh with a custom shader, you need to get the meshes as a tracked geometry.</span></span> 

## <a name="hand-rays"></a><span data-ttu-id="9983d-166">手の光線</span><span class="sxs-lookup"><span data-stu-id="9983d-166">Hand rays</span></span>

<span data-ttu-id="9983d-167">オブジェクトを取得したり、ボタンを押したりするなど、密接な相互作用を手にすることができます。</span><span class="sxs-lookup"><span data-stu-id="9983d-167">Getting hand pose works for close interactions like grabbing objects or pressing buttons.</span></span> <span data-ttu-id="9983d-168">ただし、場合によっては、ユーザーから離れた場所にあるホログラムを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9983d-168">However, sometimes you need to work with holograms that are far away from your users.</span></span> <span data-ttu-id="9983d-169">これは、C++ とブループリントの両方でポインティングデバイスとして使用できる手書き線で実現できます。</span><span class="sxs-lookup"><span data-stu-id="9983d-169">This can be accomplished with hand rays, which can be used as pointing devices in both C++ and Blueprints.</span></span> <span data-ttu-id="9983d-170">離れた場所から遠くに伸びる光線を描画することができます。また、Unreal 射線 tracing の助けを得て、それ以外の場合には外れているホログラムを選択します。</span><span class="sxs-lookup"><span data-stu-id="9983d-170">You can draw a ray from your hand to a far point and, with some help from Unreal ray tracing, select a hologram that would otherwise be out of reach.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="9983d-171">すべての関数の結果はすべてのフレームに変更されるため、すべてが呼び出し可能になります。</span><span class="sxs-lookup"><span data-stu-id="9983d-171">Since all function results change every frame, they're all made callable.</span></span> <span data-ttu-id="9983d-172">純粋関数と純粋でない関数、または呼び出し可能関数の詳細については、「 [関数](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)のブループリントユーザー guid」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9983d-172">For more information about pure and impure or callable functions, see the Blueprint user guid on [functions](https://docs.unrealengine.com/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure).</span></span>

[!INCLUDE[](includes/tabs-tracking-hand-ray.md)]

## <a name="gestures"></a><span data-ttu-id="9983d-173">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="9983d-173">Gestures</span></span>

<span data-ttu-id="9983d-174">HoloLens 2 は、空間ジェスチャを追跡します。これは、これらのジェスチャを入力としてキャプチャできることを意味します。</span><span class="sxs-lookup"><span data-stu-id="9983d-174">The HoloLens 2 tracks spatial gestures, which means you can capture those gestures as input.</span></span> <span data-ttu-id="9983d-175">ジェスチャの追跡は、サブスクリプションモデルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="9983d-175">Gesture tracking is based on a subscription model.</span></span> <span data-ttu-id="9983d-176">追跡するジェスチャをデバイスに通知するには、"ジェスチャの構成" 機能を使用する必要があります。 ジェスチャの詳細については、「 [HoloLens 2 の基本的な使用方法](/hololens/hololens2-basic-usage) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9983d-176">You should use the “Configure Gestures” function to tell the device which gestures you want to track.  You can find more details about gestures are the [HoloLens 2 Basic Usage](/hololens/hololens2-basic-usage) document.</span></span>

[!INCLUDE[](includes/tabs-tracking-gestures.md)]

## <a name="next-development-checkpoint"></a><span data-ttu-id="9983d-177">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="9983d-177">Next Development Checkpoint</span></span>

<span data-ttu-id="9983d-178">用意されている Unreal 開発体験に従っている場合、MRTK コア構成要素を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="9983d-178">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="9983d-179">ここから、次の構成要素を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="9983d-179">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9983d-180">ローカル空間アンカー</span><span class="sxs-lookup"><span data-stu-id="9983d-180">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)

<span data-ttu-id="9983d-181">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="9983d-181">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9983d-182">HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="9983d-182">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="9983d-183">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="9983d-183">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>