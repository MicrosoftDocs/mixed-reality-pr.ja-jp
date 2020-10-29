---
title: Unity 用入力移植ガイド
description: Unity で Windows Mixed Reality の入力を処理する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: 入力、unity、移植
ms.openlocfilehash: 4ad4b66b8238b3d00142fd14161113c6b912641c
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683287"
---
# <a name="input-porting-guide-for-unity"></a><span data-ttu-id="6014e-104">Unity 用入力移植ガイド</span><span class="sxs-lookup"><span data-stu-id="6014e-104">Input porting guide for Unity</span></span>

<span data-ttu-id="6014e-105">2つの方法のいずれかを使用して、入力ロジックを Windows Mixed Reality に移植できます。 Unity の一般的な入力です。複数のプラットフォームにまたがっている GetButton/GetAxis Api、または Windows 固有の XR です。付い.モーションコントローラーと HoloLens ハンド専用の豊富なデータを提供する入力 Api。</span><span class="sxs-lookup"><span data-stu-id="6014e-105">You can port your input logic to Windows Mixed Reality using one of two approaches, Unity's general Input.GetButton/GetAxis APIs that span across multiple platforms, or the Windows-specific XR.WSA.Input APIs that offer richer data specifically for motion controllers and HoloLens hands.</span></span>

## <a name="general-inputgetbuttongetaxis-apis"></a><span data-ttu-id="6014e-106">一般的な入力。 GetButton/GetAxis Api</span><span class="sxs-lookup"><span data-stu-id="6014e-106">General Input.GetButton/GetAxis APIs</span></span>

<span data-ttu-id="6014e-107">Unity では、現在、一般的な入力である GetButton/GetAxis Api を使用して [、OCULUS sdk](https://docs.unity3d.com/Manual/OculusControllers.html) と [openvr sdk](https://docs.unity3d.com/Manual/OpenVRControllers.html)の入力を公開しています。</span><span class="sxs-lookup"><span data-stu-id="6014e-107">Unity currently uses its general Input.GetButton/Input.GetAxis APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html) and [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html).</span></span> <span data-ttu-id="6014e-108">アプリが既にこれらの Api を入力に使用している場合は、これが Windows Mixed Reality でのモーションコントローラーをサポートするための最も簡単なパスです。入力マネージャーでボタンと軸を再マップするだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="6014e-108">If your apps are already using these APIs for input, this is the easiest path for supporting motion controllers in Windows Mixed Reality: you should just need to remap buttons and axes in the Input Manager.</span></span>

<span data-ttu-id="6014e-109">詳細については、「 [unity のボタン/軸マッピングテーブル](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 」と「 [共通 unity api の概要](../unity/gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6014e-109">For more information, see the [Unity button/axis mapping table](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) and the [overview of the common Unity APIs](../unity/gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis).</span></span>

## <a name="windows-specific-xrwsainput-apis"></a><span data-ttu-id="6014e-110">Windows 固有の XR。付い.入力 Api</span><span class="sxs-lookup"><span data-stu-id="6014e-110">Windows-specific XR.WSA.Input APIs</span></span>

<span data-ttu-id="6014e-111">アプリが各プラットフォームのカスタム入力ロジックを既に作成している場合は、 **XR** 名前空間の下で Windows 固有の空間入力 api を使用することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="6014e-111">If your app already builds custom input logic for each platform, you can choose to use the Windows-specific spatial input APIs under the **UnityEngine.XR.WSA.Input** namespace.</span></span> <span data-ttu-id="6014e-112">これにより、位置の精度やソースの種類などの追加情報にアクセスして、HoloLens で両手とコントローラーを区別できるようになります。</span><span class="sxs-lookup"><span data-stu-id="6014e-112">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart on HoloLens.</span></span>

<span data-ttu-id="6014e-113">詳細については、「 [UnityEngine. XR api の概要](../unity/gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6014e-113">For more information, see the [overview of the UnityEngine.XR.WSA.Input APIs](../unity/gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput).</span></span>

## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="6014e-114">グリップポーズとポインティングポーズ</span><span class="sxs-lookup"><span data-stu-id="6014e-114">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="6014e-115">Windows Mixed Reality では、さまざまなフォームファクターでモーションコントローラーがサポートされています。各コントローラーの設計は、ユーザーの手の位置と、アプリがコントローラーを表示するときに使用する自然な "進む" 方向との間の関係において異なります。</span><span class="sxs-lookup"><span data-stu-id="6014e-115">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="6014e-116">これらのコントローラーをより適切に表現するために、相互作用ソースごとに調査できる2種類の方法があります。</span><span class="sxs-lookup"><span data-stu-id="6014e-116">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source:</span></span>

* <span data-ttu-id="6014e-117">**グリップ** は、HoloLens によって検出されたハンドの位置を表します。または、運動コントローラーを持つパームです。</span><span class="sxs-lookup"><span data-stu-id="6014e-117">The **grip pose** , representing the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>
    * <span data-ttu-id="6014e-118">イマーシブヘッドセットでは、この方法を使用して、 **ユーザーの手** や、剣や銃などの **ユーザーの手に保持** されているオブジェクトをレンダリングすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6014e-118">On immersive headsets, this pose is best used to render **the user's hand** or **an object held in the user's hand** , such as a sword or gun.</span></span>
    * <span data-ttu-id="6014e-119">**グリップの位置** : コントローラーを自然に保持するときのパーム重心。グリップ内の位置を中央に配置するように左右に調整されます。</span><span class="sxs-lookup"><span data-stu-id="6014e-119">The **grip position** : The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span>
    * <span data-ttu-id="6014e-120">**グリップの向きの右軸** : 手を完全に開いて平らな5本の指を作成した場合 (左側のパームから前方、右側のパームから後方)、</span><span class="sxs-lookup"><span data-stu-id="6014e-120">The **grip orientation's Right axis** : When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
    * <span data-ttu-id="6014e-121">**グリップの向きの前方軸** : ハンドを部分的に閉じた場合 (コントローラーを保持している場合と同様)、非表示の指で形成されたチューブを通過する光線。</span><span class="sxs-lookup"><span data-stu-id="6014e-121">The **grip orientation's Forward axis** : When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
    * <span data-ttu-id="6014e-122">**グリップの向きの上位軸** : 右および順方向の定義によって暗黙的に示される上位軸。</span><span class="sxs-lookup"><span data-stu-id="6014e-122">The **grip orientation's Up axis** : The Up axis implied by the Right and Forward definitions.</span></span>
    * <span data-ttu-id="6014e-123">このグリップには、Unity のクロスベンダ入力 API (XR) を使用してアクセスでき **[ます。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation** ) または Windows 固有の API ( **TryGetPosition/rotation** ) を使用して、グリップを要求します。</span><span class="sxs-lookup"><span data-stu-id="6014e-123">You can access the grip pose through either Unity's cross-vendor input API ( **[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation** ) or through the Windows-specific API ( **sourceState.sourcePose.TryGetPosition/Rotation** , requesting the Grip pose).</span></span>
* <span data-ttu-id="6014e-124">**ポインター** は、前方を指し示すコントローラーの先端を表します。</span><span class="sxs-lookup"><span data-stu-id="6014e-124">The **pointer pose** , representing the tip of the controller pointing forward.</span></span>
    * <span data-ttu-id="6014e-125">この方法は、コントローラーモデル自体をレンダリングするときに **UI をポイント** するときに raycast するために使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6014e-125">This pose is best used to raycast when **pointing at UI** when you are rendering the controller model itself.</span></span>
    * <span data-ttu-id="6014e-126">現時点では、ポインターのポーズは、Windows 固有の API ( **Sourcestate/Rotation** ) を介してのみ使用でき、ポインターのポーズを要求します。</span><span class="sxs-lookup"><span data-stu-id="6014e-126">Currently, the pointer pose is available only through the Windows-specific API ( **sourceState.sourcePose.TryGetPosition/Rotation** , requesting the Pointer pose).</span></span>

<span data-ttu-id="6014e-127">これらの発生座標はすべて Unity のワールド座標で表現されます。</span><span class="sxs-lookup"><span data-stu-id="6014e-127">These pose coordinates are all expressed in Unity world coordinates.</span></span>

## <a name="see-also"></a><span data-ttu-id="6014e-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="6014e-128">See also</span></span>
* <span data-ttu-id="6014e-129">[モーションコントローラー]()../../design/motion-controllers.md)</span><span class="sxs-lookup"><span data-stu-id="6014e-129">[Motion controllers]()../../design/motion-controllers.md)</span></span>
* [<span data-ttu-id="6014e-130">Unity でのジェスチャとモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="6014e-130">Gestures and motion controllers in Unity</span></span>](../unity/gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="6014e-131">UnityEngine. XR</span><span class="sxs-lookup"><span data-stu-id="6014e-131">UnityEngine.XR.WSA.Input</span></span>](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [<span data-ttu-id="6014e-132">UnityEngine. XR 追跡</span><span class="sxs-lookup"><span data-stu-id="6014e-132">UnityEngine.XR.InputTracking</span></span>](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [<span data-ttu-id="6014e-133">移植ガイド</span><span class="sxs-lookup"><span data-stu-id="6014e-133">Porting guides</span></span>](porting-guides.md)
