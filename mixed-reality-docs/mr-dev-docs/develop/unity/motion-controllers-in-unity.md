---
title: Unity のモーションコントローラー
description: XR および共通のボタンと軸の Api を使用して、モーショントゥイーンでのモーションコントローラー入力を使用して、その操作を実行する方法について説明します。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: モーションコントローラー, unity, 入力, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実のヘッドセット, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 6dee5f03ab5fe84ac11a4eb10ef0483fea6e0083
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759063"
---
# <a name="motion-controllers-in-unity"></a><span data-ttu-id="77621-104">Unity のモーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="77621-104">Motion controllers in Unity</span></span>

<span data-ttu-id="77621-105">[Unity](gaze-in-unity.md)での操作を実行するには、2つの主要な方法があります。 HoloLens では[ハンドジェスチャ](../../design/gaze-and-commit.md#composite-gestures)と、HoloLens では[アニメーションコントローラー](../../design/motion-controllers.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="77621-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="77621-106">Unity の同じ Api を使用して、空間入力の両方のソースのデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="77621-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="77621-107">Unity には、Windows Mixed Reality の空間入力データにアクセスする主な方法が2つあります。</span><span class="sxs-lookup"><span data-stu-id="77621-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="77621-108">Common *input. GetButton/GetAxis* api は複数の Unity XR sdk に対して機能しますが、Windows Mixed Reality に固有の *Interactionmanager/GestureRecognizer* api は、空間入力データの完全なセットを公開します。</span><span class="sxs-lookup"><span data-stu-id="77621-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="unity-xr-input-apis"></a><span data-ttu-id="77621-109">Unity XR 入力 Api</span><span class="sxs-lookup"><span data-stu-id="77621-109">Unity XR input APIs</span></span>

<span data-ttu-id="77621-110">新しいプロジェクトの場合は、最初から新しい XR 入力 Api を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="77621-110">For new projects, we recommend using the new XR input APIs from the beginning.</span></span> 

<span data-ttu-id="77621-111">[XR api](https://docs.unity3d.com/Manual/xr_input.html)の詳細については、こちらを参照してください。</span><span class="sxs-lookup"><span data-stu-id="77621-111">You can find more information about the [XR APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="77621-112">Unity ボタン/軸マッピングテーブル</span><span class="sxs-lookup"><span data-stu-id="77621-112">Unity button/axis mapping table</span></span>

<span data-ttu-id="77621-113">Unity の Windows Mixed Reality モーションコントローラーの入力マネージャーでは、次に示すボタンと軸の Id を *入力します。 GetButton/GetAxis* api を使用します。</span><span class="sxs-lookup"><span data-stu-id="77621-113">Unity's Input Manager for Windows Mixed Reality motion controllers supports the button and axis IDs listed below through the *Input.GetButton/GetAxis* APIs.</span></span> <span data-ttu-id="77621-114">「Windows MR 固有」列では、 *Interactionsourcestate* 型から使用できるプロパティを参照しています。</span><span class="sxs-lookup"><span data-stu-id="77621-114">The "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="77621-115">これらの各 Api の詳細については、以下のセクションで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="77621-115">Each of these APIs is described in detail in the sections below.</span></span>

<span data-ttu-id="77621-116">Windows Mixed Reality のボタン/軸 ID マッピングは、通常、Oculus のボタン/軸 Id と一致します。</span><span class="sxs-lookup"><span data-stu-id="77621-116">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="77621-117">Windows Mixed Reality のボタン/軸 ID マッピングは、次の2つの方法で OpenVR のマッピングと異なります。</span><span class="sxs-lookup"><span data-stu-id="77621-117">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="77621-118">このマッピングでは、サムスティックとは異なるタッチパッド Id を使用して、thumbsticks とタッチパッド向けの両方を持つコントローラーをサポートします。</span><span class="sxs-lookup"><span data-stu-id="77621-118">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="77621-119">このマッピングにより、メニューボタンの A および X ボタン Id のオーバーロードが回避され、物理 ABXY ボタンで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="77621-119">The mapping avoids overloading the A and X button IDs for the Menu buttons to leave them available for the physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="77621-120">入力</span><span class="sxs-lookup"><span data-stu-id="77621-120">Input</span></span> </th><th colspan="2"><span data-ttu-id="77621-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">一般的な Unity API</a></span><span class="sxs-lookup"><span data-stu-id="77621-121"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="77621-122">(Input. GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="77621-122">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="77621-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR 固有の入力 API</a></span><span class="sxs-lookup"><span data-stu-id="77621-123"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="77621-124">XR.付い.代入</span><span class="sxs-lookup"><span data-stu-id="77621-124">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="77621-125">左側</span><span class="sxs-lookup"><span data-stu-id="77621-125">Left hand</span></span> </th><th> <span data-ttu-id="77621-126">Right</span><span class="sxs-lookup"><span data-stu-id="77621-126">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="77621-127">押されたトリガーを選択</span><span class="sxs-lookup"><span data-stu-id="77621-127">Select trigger pressed</span></span> </td><td> <span data-ttu-id="77621-128">軸 9 = 1.0</span><span class="sxs-lookup"><span data-stu-id="77621-128">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="77621-129">軸 10 = 1.0</span><span class="sxs-lookup"><span data-stu-id="77621-129">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="77621-130">selectPressed れた</span><span class="sxs-lookup"><span data-stu-id="77621-130">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-131">トリガーのアナログ値の選択</span><span class="sxs-lookup"><span data-stu-id="77621-131">Select trigger analog value</span></span> </td><td> <span data-ttu-id="77621-132">軸9</span><span class="sxs-lookup"><span data-stu-id="77621-132">Axis 9</span></span> </td><td> <span data-ttu-id="77621-133">軸10</span><span class="sxs-lookup"><span data-stu-id="77621-133">Axis 10</span></span> </td><td> <span data-ttu-id="77621-134">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="77621-134">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-135">一部押されたトリガーを選択</span><span class="sxs-lookup"><span data-stu-id="77621-135">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="77621-136">ボタン 14 <i>(ゲームパッド互換)</i> </span><span class="sxs-lookup"><span data-stu-id="77621-136">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="77621-137">ボタン 15 <i>(ゲームパッド互換)</i> </span><span class="sxs-lookup"><span data-stu-id="77621-137">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="77621-138">selectPressedAmount &gt; 0.0</span><span class="sxs-lookup"><span data-stu-id="77621-138">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-139">押されたメニューボタン</span><span class="sxs-lookup"><span data-stu-id="77621-139">Menu button pressed</span></span> </td><td> <span data-ttu-id="77621-140">ボタン 6 \*</span><span class="sxs-lookup"><span data-stu-id="77621-140">Button 6\*</span></span> </td><td> <span data-ttu-id="77621-141">ボタン 7 \*</span><span class="sxs-lookup"><span data-stu-id="77621-141">Button 7\*</span></span> </td><td> <span data-ttu-id="77621-142">menuPressed</span><span class="sxs-lookup"><span data-stu-id="77621-142">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-143">押されたグリップボタン</span><span class="sxs-lookup"><span data-stu-id="77621-143">Grip button pressed</span></span> </td><td> <span data-ttu-id="77621-144">軸 11 = 1.0 (アナログ値なし)</span><span class="sxs-lookup"><span data-stu-id="77621-144">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="77621-145">ボタン 4 <i>(ゲームパッド互換)</i> </span><span class="sxs-lookup"><span data-stu-id="77621-145">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="77621-146">軸 12 = 1.0 (アナログ値なし)</span><span class="sxs-lookup"><span data-stu-id="77621-146">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="77621-147">ボタン 5 <i>(ゲームパッド互換)</i> </span><span class="sxs-lookup"><span data-stu-id="77621-147">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="77621-148">grasped</span><span class="sxs-lookup"><span data-stu-id="77621-148">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-149">スティック X <i>(左:-1.0、右: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="77621-149">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="77621-150">軸1</span><span class="sxs-lookup"><span data-stu-id="77621-150">Axis 1</span></span> </td><td> <span data-ttu-id="77621-151">軸4</span><span class="sxs-lookup"><span data-stu-id="77621-151">Axis 4</span></span> </td><td> <span data-ttu-id="77621-152">thumbstickPosition</span><span class="sxs-lookup"><span data-stu-id="77621-152">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-153">サムスティック Y <i>(上:-1.0、下: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="77621-153">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="77621-154">軸2</span><span class="sxs-lookup"><span data-stu-id="77621-154">Axis 2</span></span> </td><td> <span data-ttu-id="77621-155">軸5</span><span class="sxs-lookup"><span data-stu-id="77621-155">Axis 5</span></span> </td><td> <span data-ttu-id="77621-156">thumbstickPosition</span><span class="sxs-lookup"><span data-stu-id="77621-156">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-157">押したサムスティック</span><span class="sxs-lookup"><span data-stu-id="77621-157">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="77621-158">ボタン8</span><span class="sxs-lookup"><span data-stu-id="77621-158">Button 8</span></span> </td><td> <span data-ttu-id="77621-159">ボタン9</span><span class="sxs-lookup"><span data-stu-id="77621-159">Button 9</span></span> </td><td> <span data-ttu-id="77621-160">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="77621-160">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-161">タッチパッド X <i>(左:-1.0、右: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="77621-161">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="77621-162">軸 17 \*</span><span class="sxs-lookup"><span data-stu-id="77621-162">Axis 17\*</span></span> </td><td> <span data-ttu-id="77621-163">軸 19 \*</span><span class="sxs-lookup"><span data-stu-id="77621-163">Axis 19\*</span></span> </td><td> <span data-ttu-id="77621-164">touchpadPosition</span><span class="sxs-lookup"><span data-stu-id="77621-164">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-165">タッチパッド Y <i>(上:-1.0、下: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="77621-165">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="77621-166">軸 18 \*</span><span class="sxs-lookup"><span data-stu-id="77621-166">Axis 18\*</span></span> </td><td> <span data-ttu-id="77621-167">軸 20 \*</span><span class="sxs-lookup"><span data-stu-id="77621-167">Axis 20\*</span></span> </td><td> <span data-ttu-id="77621-168">touchpadPosition</span><span class="sxs-lookup"><span data-stu-id="77621-168">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-169">タッチパッドにタッチ</span><span class="sxs-lookup"><span data-stu-id="77621-169">Touchpad touched</span></span> </td><td> <span data-ttu-id="77621-170">ボタン 18 \*</span><span class="sxs-lookup"><span data-stu-id="77621-170">Button 18\*</span></span> </td><td> <span data-ttu-id="77621-171">ボタン 19 \*</span><span class="sxs-lookup"><span data-stu-id="77621-171">Button 19\*</span></span> </td><td> <span data-ttu-id="77621-172">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="77621-172">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-173">タッチパッドが押されました</span><span class="sxs-lookup"><span data-stu-id="77621-173">Touchpad pressed</span></span> </td><td> <span data-ttu-id="77621-174">ボタン 16 \*</span><span class="sxs-lookup"><span data-stu-id="77621-174">Button 16\*</span></span> </td><td> <span data-ttu-id="77621-175">ボタン 17 \*</span><span class="sxs-lookup"><span data-stu-id="77621-175">Button 17\*</span></span> </td><td> <span data-ttu-id="77621-176">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="77621-176">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-177">6自由度グリップまたはポインターのポーズ</span><span class="sxs-lookup"><span data-stu-id="77621-177">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="77621-178"><i>グリップ</i> の発生のみ: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR。InputTracking。 GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="77621-178"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="77621-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking。 GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="77621-179"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="77621-180"><i>グリップ</i>または<i>ポインター</i>を引数として渡す: sourcestate</span><span class="sxs-lookup"><span data-stu-id="77621-180">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="77621-181">sourceState。 TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="77621-181">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="77621-182">状態の追跡</span><span class="sxs-lookup"><span data-stu-id="77621-182">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="77621-183"><i>位置の精度とソース損失リスクは MR 固有の API を介してのみ利用可能</i> </span><span class="sxs-lookup"><span data-stu-id="77621-183"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="77621-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState. Sourcestate の精度</a></span><span class="sxs-lookup"><span data-stu-id="77621-184"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="77621-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="77621-185"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="77621-186">これらのボタン/軸 Id は、ゲームパッド、Oculus Touch、OpenVR で使用されるマッピングの競合により、Unity が OpenVR に使用する Id とは異なります。</span><span class="sxs-lookup"><span data-stu-id="77621-186">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="77621-187">グリップポーズとポインティングポーズ</span><span class="sxs-lookup"><span data-stu-id="77621-187">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="77621-188">Windows Mixed Reality では、さまざまなフォームファクターでモーションコントローラーをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="77621-188">Windows Mixed Reality supports motion controllers in a variety of form factors.</span></span> <span data-ttu-id="77621-189">各コントローラーの設計は、ユーザーの手の位置と、アプリがコントローラーをレンダリングするときに使用する自然な "転送" の方向との間の関係において異なります。</span><span class="sxs-lookup"><span data-stu-id="77621-189">Each controller's design differs in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="77621-190">これらのコントローラーをより適切に表現するために、それぞれの相互作用ソース、 **グリップ** の原因、および **ポインター** の種類に対して調査できる2種類の方法があります。</span><span class="sxs-lookup"><span data-stu-id="77621-190">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="77621-191">グリップとポインターの両方の座標は、グローバル Unity ワールド座標のすべての Unity Api によって表されます。</span><span class="sxs-lookup"><span data-stu-id="77621-191">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="77621-192">グリップの原因</span><span class="sxs-lookup"><span data-stu-id="77621-192">Grip pose</span></span>

<span data-ttu-id="77621-193">**グリップ** は、HoloLens によって検出されたか、または運動コントローラーを保持しているユーザーの palm の場所を表します。</span><span class="sxs-lookup"><span data-stu-id="77621-193">The **grip pose** represents the location of the users palm, either detected by a HoloLens or holding a motion controller.</span></span>

<span data-ttu-id="77621-194">イマーシブヘッドセットでは、ユーザー **の手** や **ユーザー側に保持** されているオブジェクトをレンダリングするために、グリップが最適です。</span><span class="sxs-lookup"><span data-stu-id="77621-194">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**.</span></span> <span data-ttu-id="77621-195">グリップは、モーションコントローラーを視覚化するときにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="77621-195">The grip pose is also used when visualizing a motion controller.</span></span> <span data-ttu-id="77621-196">モーションコントローラー用に Windows によって提供される **描画モデル** では、回転の原点と中心としてグリップが使用されます。</span><span class="sxs-lookup"><span data-stu-id="77621-196">The **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="77621-197">グリップは、次のように明確に定義されます。</span><span class="sxs-lookup"><span data-stu-id="77621-197">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="77621-198">**グリップの位置**: コントローラーを自然に保持するときのパーム重心。グリップ内の位置を中央に配置するように左右に調整されます。</span><span class="sxs-lookup"><span data-stu-id="77621-198">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="77621-199">Windows Mixed Reality モーションコントローラーでは、通常、この位置はボタンをつかみに揃えて配置されます。</span><span class="sxs-lookup"><span data-stu-id="77621-199">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="77621-200">**グリップの向きの右軸**: 手を完全に開いて平らな5本の指を作成した場合 (左側のパームから前方、右側のパームから後方)、</span><span class="sxs-lookup"><span data-stu-id="77621-200">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="77621-201">**グリップの向きの前方軸**: ハンドを部分的に閉じた場合 (コントローラーを保持している場合と同様)、非表示の指で形成されたチューブを通過する光線。</span><span class="sxs-lookup"><span data-stu-id="77621-201">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="77621-202">**グリップの向きの上位軸**: 右および順方向の定義によって暗黙的に示される上位軸。</span><span class="sxs-lookup"><span data-stu-id="77621-202">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="77621-203">このグリップには、Unity のクロスベンダ入力 API (XR) を使用してアクセスでき *[ます。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation*) または WINDOWS MR 固有の API (*TryGetPosition/rotation*) を使用して、 **グリップ** ノードのポーズデータを要求します。</span><span class="sxs-lookup"><span data-stu-id="77621-203">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="77621-204">ポインターのポーズ</span><span class="sxs-lookup"><span data-stu-id="77621-204">Pointer pose</span></span>

<span data-ttu-id="77621-205">**ポインター** は、前方にあるコントローラーの先端を表します。</span><span class="sxs-lookup"><span data-stu-id="77621-205">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="77621-206">システム指定のポインターの raycast は、 **コントローラーモデル自体をレンダリング** するときに最もよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="77621-206">The system-provided pointer pose is best used to raycast when you're **rendering the controller model itself**.</span></span> <span data-ttu-id="77621-207">仮想銃など、コントローラーの代わりに他の仮想オブジェクトをレンダリングする場合は、アプリ定義の銃モデルの胴体に沿って移動する射線など、その仮想オブジェクトに最も適した光線をポイントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="77621-207">If you're rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that's most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="77621-208">ユーザーは物理コントローラーではなく仮想オブジェクトを見ることができるため、仮想オブジェクトをポイントすると、アプリを使用している方がより自然な場合があります。</span><span class="sxs-lookup"><span data-stu-id="77621-208">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="77621-209">現時点では、ポインターの破壊は、Unity では、Windows MR 固有の API *TryGetPosition/ローテーション* を通じてのみ使用できます。引数として *Interactionsourcenode* を渡します。</span><span class="sxs-lookup"><span data-stu-id="77621-209">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="77621-210">コントローラー追跡状態</span><span class="sxs-lookup"><span data-stu-id="77621-210">Controller tracking state</span></span>

<span data-ttu-id="77621-211">ヘッドセットと同様に、Windows Mixed Reality モーションコントローラーでは、外部の追跡センサーを設定する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="77621-211">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="77621-212">代わりに、コントローラーはヘッドセット自体のセンサーによって追跡されます。</span><span class="sxs-lookup"><span data-stu-id="77621-212">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="77621-213">ユーザーがコントローラーをヘッドセットのビューのフィールドから移動した場合、ほとんどの場合、Windows はコントローラーの位置を推測し続けます。</span><span class="sxs-lookup"><span data-stu-id="77621-213">If the user moves the controllers out of the headset's field of view, Windows continues to infer controller positions in most cases.</span></span> <span data-ttu-id="77621-214">コントローラーのビジュアル追跡が十分に失われた場合、コントローラーの位置はおおよその精度の位置にドロップします。</span><span class="sxs-lookup"><span data-stu-id="77621-214">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="77621-215">この時点で、システムはコントローラーをユーザーにボディロックし、ユーザーが移動したときの位置を追跡しながら、内部方向センサーを使用してコントローラーの真向きを公開します。</span><span class="sxs-lookup"><span data-stu-id="77621-215">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="77621-216">UI 要素をポイントしてアクティブ化するためにコントローラーを使用する多くのアプリは、ユーザーに気付かなくても、おおよその精度で正常に動作できます。</span><span class="sxs-lookup"><span data-stu-id="77621-216">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="77621-217">これを実現する最善の方法は、自分で試してみることです。</span><span class="sxs-lookup"><span data-stu-id="77621-217">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="77621-218">次のビデオでは、さまざまな追跡状態におけるモーションコントローラーで動作するイマーシブコンテンツの例を紹介しています。</span><span class="sxs-lookup"><span data-stu-id="77621-218">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="77621-219">状態の明示的な追跡に関する推論</span><span class="sxs-lookup"><span data-stu-id="77621-219">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="77621-220">追跡の状態に基づいて位置を異なる方法で処理する必要があるアプリは、さらに詳細になり、コントローラーの状態 ( *SourceLossRisk* や *positionaccuracy* など) のプロパティを検査することができます。</span><span class="sxs-lookup"><span data-stu-id="77621-220">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="77621-221">状態の追跡</span><span class="sxs-lookup"><span data-stu-id="77621-221">Tracking state</span></span> </th><th> <span data-ttu-id="77621-222">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="77621-222">SourceLossRisk</span></span> </th><th> <span data-ttu-id="77621-223">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="77621-223">PositionAccuracy</span></span> </th><th> <span data-ttu-id="77621-224">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="77621-224">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="77621-225"><b>高精度</b> </span><span class="sxs-lookup"><span data-stu-id="77621-225"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="77621-226">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="77621-226">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="77621-227">高</span><span class="sxs-lookup"><span data-stu-id="77621-227">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="77621-228">true</span><span class="sxs-lookup"><span data-stu-id="77621-228">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-229"><b>高精度 (消失のリスク)</b> </span><span class="sxs-lookup"><span data-stu-id="77621-229"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="77621-230">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="77621-230">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="77621-231">高</span><span class="sxs-lookup"><span data-stu-id="77621-231">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="77621-232">true</span><span class="sxs-lookup"><span data-stu-id="77621-232">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-233"><b>おおよその精度</b> </span><span class="sxs-lookup"><span data-stu-id="77621-233"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="77621-234">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="77621-234">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="77621-235">Approximate</span><span class="sxs-lookup"><span data-stu-id="77621-235">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="77621-236">true</span><span class="sxs-lookup"><span data-stu-id="77621-236">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="77621-237"><b>位置なし</b> </span><span class="sxs-lookup"><span data-stu-id="77621-237"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="77621-238">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="77621-238">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="77621-239">Approximate</span><span class="sxs-lookup"><span data-stu-id="77621-239">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="77621-240">false</span><span class="sxs-lookup"><span data-stu-id="77621-240">false</span></span></td>
</tr>
</table>

<span data-ttu-id="77621-241">これらのモーションコントローラーの追跡状態は、次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="77621-241">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="77621-242">**高精度:** モーションコントローラーは、ヘッドセットのビューに含まれていますが、通常、ビジュアルの追跡に基づいて高精度の位置を提供します。</span><span class="sxs-lookup"><span data-stu-id="77621-242">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="77621-243">一時的にビューのフィールドから離れるか、ヘッドセットセンサー (ユーザーなど) から瞬間的に見えなくなる移動コントローラーは、コントローラー自体の慣性追跡に基づいて、短時間で高精度のポーズを返します。</span><span class="sxs-lookup"><span data-stu-id="77621-243">A moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="77621-244">**高精度 (損失のリスク):** ユーザーが、ヘッドセットのビューの端を越えてモーションコントローラーを動かすと、ヘッドセットはすぐにコントローラーの位置を視覚的に追跡できなくなります。</span><span class="sxs-lookup"><span data-stu-id="77621-244">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="77621-245">アプリでは、 **SourceLossRisk** が1.0 に到達して、コントローラーがこの視界の境界に達したことを認識します。</span><span class="sxs-lookup"><span data-stu-id="77621-245">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="77621-246">その時点で、アプリは、高い品質を備えた安定したストリームを必要とするコントローラージェスチャを一時停止することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="77621-246">At that point, the app may choose to pause controller gestures that require a steady stream of high quality poses.</span></span>
* <span data-ttu-id="77621-247">**おおよその精度:** コントローラーのビジュアル追跡が十分に失われた場合、コントローラーの位置はおおよその精度の位置にドロップします。</span><span class="sxs-lookup"><span data-stu-id="77621-247">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="77621-248">この時点で、システムはコントローラーをユーザーにボディロックし、ユーザーが移動したときの位置を追跡しながら、内部方向センサーを使用してコントローラーの真向きを公開します。</span><span class="sxs-lookup"><span data-stu-id="77621-248">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="77621-249">UI 要素をポイントしてアクティブ化するためにコントローラーを使用する多くのアプリは、ユーザーに気付かずに正確な精度で、通常どおりに動作できます。</span><span class="sxs-lookup"><span data-stu-id="77621-249">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="77621-250">入力要件が重いアプリでは、 **positionaccuracy** プロパティを調べることによって、精度が **高い** ことを **意味します**。たとえば、この期間中にユーザーに対して、オフスクリーンのターゲットに対してより多くのヒットボックスを与えることができます。</span><span class="sxs-lookup"><span data-stu-id="77621-250">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="77621-251">**位置なし:** コントローラーは長時間の精度で実行できますが、本体でロックされた位置であっても、その時点では意味がないことをシステムが認識している場合があります。</span><span class="sxs-lookup"><span data-stu-id="77621-251">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position isn't meaningful at the moment.</span></span> <span data-ttu-id="77621-252">たとえば、電源がオンにされたコントローラーが視覚的に観察されていない場合や、ユーザーがコントローラーを停止した後に他のユーザーが選択した場合などです。</span><span class="sxs-lookup"><span data-stu-id="77621-252">For example, a controller that was turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="77621-253">これらのタイミングでは、システムはアプリに位置を提供せず、 *TryGetPosition* は false を返します。</span><span class="sxs-lookup"><span data-stu-id="77621-253">At those times, the system won't provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="77621-254">共通 Unity Api (Input. GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="77621-254">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="77621-255">**名前空間:** *unityengine*、 *unityengine XR*</span><span class="sxs-lookup"><span data-stu-id="77621-255">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="77621-256">**型**: *Input*、 *XR。InputTracking*</span><span class="sxs-lookup"><span data-stu-id="77621-256">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="77621-257">Unity では、現在、一般的な *入力. GetButton/GetAxis* api を使用して、 [Oculus Sdk](https://docs.unity3d.com/Manual/OculusControllers.html)、 [Openvr SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) 、および Windows Mixed Reality の入力を公開しています。これには、ハンドアンドモーションコントローラーも含まれます。</span><span class="sxs-lookup"><span data-stu-id="77621-257">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="77621-258">アプリがこれらの Api を入力に使用する場合、Windows Mixed Reality を含む複数の XR Sdk 間で、モーションコントローラーを簡単にサポートできます。</span><span class="sxs-lookup"><span data-stu-id="77621-258">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="77621-259">論理ボタンの押された状態の取得</span><span class="sxs-lookup"><span data-stu-id="77621-259">Getting a logical button's pressed state</span></span>

<span data-ttu-id="77621-260">一般的な Unity 入力 Api を使用するには、まず、 [Unity 入力マネージャー](https://docs.unity3d.com/Manual/ConventionalGameInput.html)で論理名にボタンと軸を配線し、ボタンまたは軸 id を各名前にバインドします。</span><span class="sxs-lookup"><span data-stu-id="77621-260">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="77621-261">その後、その論理ボタンと軸名を参照するコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="77621-261">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="77621-262">たとえば、左モーションコントローラーの [トリガー] ボタンを [送信] アクションにマップするには、[ **編集 > プロジェクトの設定** ] に移動し、Unity 内の [入力] > て、[軸] の [送信] セクションのプロパティを展開します。</span><span class="sxs-lookup"><span data-stu-id="77621-262">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="77621-263">次のように、 **正のボタン** または **Alt 陽性のボタン** プロパティを [ジョイスティックの読み取り **] ボタン 14** に変更します。</span><span class="sxs-lookup"><span data-stu-id="77621-263">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="77621-264">![Unity の InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="77621-264">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="77621-265">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="77621-265">*Unity InputManager*</span></span>

<span data-ttu-id="77621-266">スクリプトは、 *Input. GetButton* を使用して送信アクションを確認できます。</span><span class="sxs-lookup"><span data-stu-id="77621-266">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="77621-267">論理ボタンを追加するには、[**軸**] の [**サイズ**] プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="77621-267">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="77621-268">物理的なボタンの押された状態を直接取得する</span><span class="sxs-lookup"><span data-stu-id="77621-268">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="77621-269">*GetKey* を使用して、完全修飾名でボタンに手動でアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="77621-269">You can also access buttons manually by their fully qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="77621-270">手や運動コントローラーのポーズ</span><span class="sxs-lookup"><span data-stu-id="77621-270">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="77621-271">XR を使用して、コントローラーの位置と回転にアクセスでき *ます。InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="77621-271">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> <span data-ttu-id="77621-272">上のコードは、コントローラーのグリップの発生 (ユーザーがコントローラーを保持している場所) を表します。これは、ユーザーの手に剣や銃をレンダリングする場合や、コントローラー自体のモデルをレンダリングする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="77621-272">The above code represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>
> 
> <span data-ttu-id="77621-273">このグリップとポインターの (コントローラーの先端が指している) 間のリレーションシップは、コントローラーによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="77621-273">The relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="77621-274">現時点では、コントローラーのポインターにアクセスするには、次のセクションで説明する MR 固有の入力 API を使用するしかありません。</span><span class="sxs-lookup"><span data-stu-id="77621-274">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="77621-275">Windows 固有の Api (XR。付い.代入</span><span class="sxs-lookup"><span data-stu-id="77621-275">Windows-specific APIs (XR.WSA.Input)</span></span>

> [!CAUTION]
> <span data-ttu-id="77621-276">プロジェクトが XR のいずれかを使用している場合。WSA Api は、今後の Unity リリースで XR SDK を優先するように段階的に廃止されています。</span><span class="sxs-lookup"><span data-stu-id="77621-276">If your project is using any of the XR.WSA APIs, these are being phased out in favor of the XR SDK in future Unity releases.</span></span> <span data-ttu-id="77621-277">新しいプロジェクトの場合は、最初から XR SDK を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="77621-277">For new projects, we recommend using the XR SDK from the beginning.</span></span> <span data-ttu-id="77621-278">[XR 入力システムと api](https://docs.unity3d.com/Manual/xr_input.html)の詳細については、こちらを参照してください。</span><span class="sxs-lookup"><span data-stu-id="77621-278">You can find more information about the [XR Input system and APIs here](https://docs.unity3d.com/Manual/xr_input.html).</span></span>

<span data-ttu-id="77621-279">**名前空間:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="77621-279">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="77621-280">**型**: *interactionmanager*、 *interactionsourcestate*、 *interactionmanager*、 *interactionsourceproperties*、 *interactionsourcekind*、 *interactionmanager*</span><span class="sxs-lookup"><span data-stu-id="77621-280">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="77621-281">Windows Mixed Reality の入力 (HoloLens) とモーションコントローラーの詳細情報を取得するには、 *XR* 名前空間で windows 固有の空間入力 api を使用することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="77621-281">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="77621-282">これにより、位置の精度やソースの種類などの追加情報にアクセスして、ハンドとコントローラーを区別できます。</span><span class="sxs-lookup"><span data-stu-id="77621-282">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="77621-283">ハンドコントローラーとモーションコントローラーの状態のポーリング</span><span class="sxs-lookup"><span data-stu-id="77621-283">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="77621-284">このフレームの状態は、 *GetCurrentReading* メソッドを使用して、相互作用ソース (手動またはモーションコントローラー) ごとにポーリングできます。</span><span class="sxs-lookup"><span data-stu-id="77621-284">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="77621-285">返される各 *Interactionsourcestate* は、現在の時点の相互作用ソースを表します。</span><span class="sxs-lookup"><span data-stu-id="77621-285">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="77621-286">*Interactionsourcestate* は、次のような情報を公開します。</span><span class="sxs-lookup"><span data-stu-id="77621-286">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="77621-287">どのような [種類の押下](../../design/motion-controllers.md) が発生していますか (選択/メニュー/つかみ/タッチパッド/サムスティック)</span><span class="sxs-lookup"><span data-stu-id="77621-287">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="77621-288">タッチパッドやサムスティックの XY 座標とタッチされた状態など、モーションコントローラー固有のその他のデータ</span><span class="sxs-lookup"><span data-stu-id="77621-288">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="77621-289">ソースがハンドコントローラーであるか、モーションコントローラーであるかを知るための InteractionSourceKind</span><span class="sxs-lookup"><span data-stu-id="77621-289">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="77621-290">前方予測レンダリングのポーリング</span><span class="sxs-lookup"><span data-stu-id="77621-290">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="77621-291">ハンドおよびコントローラーからの相互作用ソースデータをポーリングする場合、取得されるのは、このフレームの photons がユーザーの目に到達する瞬間を予測することです。</span><span class="sxs-lookup"><span data-stu-id="77621-291">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="77621-292">前方予測は、コントローラーまたは保持されたオブジェクトを各フレームに **レンダリング** する場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="77621-292">Forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="77621-293">コントローラーで特定のプレスまたはリリースを対象としている場合は、次に説明する履歴イベント Api を使用すると、そのことが最も正確になります。</span><span class="sxs-lookup"><span data-stu-id="77621-293">If you're targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="77621-294">この現在のフレームの前方予測ヘッドを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="77621-294">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="77621-295">ソースの場合と同様に、これはカーソルを **レンダリング** するときに便利です。ただし、次に説明する履歴イベント api を使用すると、特定のプレスまたはリリースをターゲットにすると最も正確になります。</span><span class="sxs-lookup"><span data-stu-id="77621-295">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="77621-296">相互作用ソースイベントの処理</span><span class="sxs-lookup"><span data-stu-id="77621-296">Handling interaction source events</span></span>

<span data-ttu-id="77621-297">正確な履歴データで発生した入力イベントを処理するために、ポーリングではなく相互作用ソースイベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="77621-297">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="77621-298">相互作用ソースイベントを処理するには:</span><span class="sxs-lookup"><span data-stu-id="77621-298">To handle interaction source events:</span></span>
* <span data-ttu-id="77621-299">*Interactionmanager* 入力イベントに登録します。</span><span class="sxs-lookup"><span data-stu-id="77621-299">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="77621-300">関心がある相互作用イベントの種類ごとに、サブスクライブする必要があります。</span><span class="sxs-lookup"><span data-stu-id="77621-300">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="77621-301">イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="77621-301">Handle the event.</span></span> <span data-ttu-id="77621-302">相互作用イベントをサブスクライブすると、必要に応じてコールバックが取得されます。</span><span class="sxs-lookup"><span data-stu-id="77621-302">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="77621-303">*Sourcepressed* れた例では、ソースが検出されてから解放されるか、または失われる前に、が発生します。</span><span class="sxs-lookup"><span data-stu-id="77621-303">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="77621-304">イベントの処理を停止する方法</span><span class="sxs-lookup"><span data-stu-id="77621-304">How to stop handling an event</span></span>

<span data-ttu-id="77621-305">イベントに関心がなくなった場合、またはイベントをサブスクライブしているオブジェクトを破棄する場合は、イベントの処理を停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77621-305">You need to stop handling an event when you're no longer interested in the event or you're destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="77621-306">イベントの処理を停止するには、イベントのサブスクリプションを解除します。</span><span class="sxs-lookup"><span data-stu-id="77621-306">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="77621-307">相互作用ソースイベントの一覧</span><span class="sxs-lookup"><span data-stu-id="77621-307">List of interaction source events</span></span>

<span data-ttu-id="77621-308">使用可能な相互作用ソースイベントは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="77621-308">The available interaction source events are:</span></span>
* <span data-ttu-id="77621-309">*Interactionsourcedetected 検出されました* (ソースがアクティブになります)</span><span class="sxs-lookup"><span data-stu-id="77621-309">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="77621-310">*Interactionsourcelost* (非アクティブになります)</span><span class="sxs-lookup"><span data-stu-id="77621-310">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="77621-311">*Interactionsourcepressed* れた (tap、button press、または "Select" 発音)</span><span class="sxs-lookup"><span data-stu-id="77621-311">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="77621-312">*InteractionSourceReleased* (tap の終了、ボタンの解放、または "Select" 発音の最後)</span><span class="sxs-lookup"><span data-stu-id="77621-312">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="77621-313">*Interactionsourceupdated* (移動またはその他の状態の変更)</span><span class="sxs-lookup"><span data-stu-id="77621-313">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="77621-314">プレスまたはリリースと最も正確に一致する履歴ターゲットのイベント</span><span class="sxs-lookup"><span data-stu-id="77621-314">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="77621-315">前に説明したポーリング Api を使用すると、アプリが事前に予測されるようになります。</span><span class="sxs-lookup"><span data-stu-id="77621-315">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="77621-316">これらの予測される効果はコントローラーまたは仮想ハンドヘルドオブジェクトのレンダリングに最適ですが、次の2つの主な理由から、将来のターゲット設定には最適ではありません。</span><span class="sxs-lookup"><span data-stu-id="77621-316">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses aren't optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="77621-317">ユーザーがコントローラー上のボタンを押すと、Bluetooth 経由のワイヤレス待ち時間は約20ミリ秒になることがあります。</span><span class="sxs-lookup"><span data-stu-id="77621-317">When the user presses a button on a controller, there can be about 20 ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="77621-318">次に、前方予測攻撃を使用している場合、現在のフレームの photons がユーザーの目に近づいた時間をターゲットにするために、10-20 ミリ秒の前方予測が適用されます。</span><span class="sxs-lookup"><span data-stu-id="77621-318">Then, if you're using a forward-predicted pose, there would be another 10-20 ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="77621-319">これは、ポーリングによって、ユーザーの頭と針が、プレスまたはリリースが発生したときに実際には30-40 ミリ秒後に発生するようにすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="77621-319">This means that polling gives you a source pose or head pose that is 30-40 ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="77621-320">HoloLens の入力では、ワイヤレス転送の遅延は発生しませんが、押しを検出するために同様の処理遅延が発生します。</span><span class="sxs-lookup"><span data-stu-id="77621-320">For HoloLens hand input, while there's no wireless transmission delay, there's a similar processing delay to detect the press.</span></span>

<span data-ttu-id="77621-321">ユーザーが手やコントローラーを押したときの本来の目的に基づいて正確にターゲットを指定するには、その *Interactionsourcepressed* れたイベントまたは *InteractionSourceReleased* 入力イベントからの履歴ソースの発生元またはヘッドポーズを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="77621-321">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="77621-322">ユーザーのヘッドまたはコントローラーの履歴リーダーデータを使用して、プレスまたはリリースを対象にすることができます。</span><span class="sxs-lookup"><span data-stu-id="77621-322">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="77621-323">ジェスチャまたはコントローラーの押下が発生した時点で、[ユーザーがどの](../../design/gaze-and-commit.md)ようにしているかを **判断するため** に使用できます。</span><span class="sxs-lookup"><span data-stu-id="77621-323">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* <span data-ttu-id="77621-324">モーションコントローラーの押下が発生した時点のソースは、ユーザーがコントローラーを指していた **対象を判別するため** に使用できます。</span><span class="sxs-lookup"><span data-stu-id="77621-324">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="77621-325">これは、押下を経験したコントローラーの状態になります。</span><span class="sxs-lookup"><span data-stu-id="77621-325">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="77621-326">コントローラー自体をレンダリングする場合は、グリップの原因ではなくポインターのポーズを要求できます。これにより、レンダリングされたコントローラーの自然なヒントをユーザーが考慮する対象から、ターゲットの射線をシュートすることができます。</span><span class="sxs-lookup"><span data-stu-id="77621-326">If you're rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a><span data-ttu-id="77621-327">イベントハンドラーの例</span><span class="sxs-lookup"><span data-stu-id="77621-327">Event handlers example</span></span>

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="motion-controllers-in-mrtk"></a><span data-ttu-id="77621-328">MRTK のモーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="77621-328">Motion Controllers in MRTK</span></span>

<span data-ttu-id="77621-329">入力マネージャーから [ジェスチャとモーションコントローラー](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/controllers.md) にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="77621-329">You can access [gesture and motion controller](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/controllers.md) from the input Manager.</span></span>

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="77621-330">チュートリアルに従う</span><span class="sxs-lookup"><span data-stu-id="77621-330">Follow along with tutorials</span></span>

<span data-ttu-id="77621-331">詳細なカスタマイズ例が記載されたステップバイステップのチュートリアルは、Mixed Reality Academy でご利用いただけます。</span><span class="sxs-lookup"><span data-stu-id="77621-331">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="77621-332">MR 入力 211:ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="77621-332">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="77621-333">MR 入力 213:モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="77621-333">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="77621-334">[![MR 入力 213-モーションコントローラー](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="77621-334">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="77621-335">*MR 入力 213-モーションコントローラー*</span><span class="sxs-lookup"><span data-stu-id="77621-335">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="77621-336">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="77621-336">Next Development Checkpoint</span></span>

<span data-ttu-id="77621-337">Unity の開発に関する体験に従っている場合は、MRTK コアのビルディングブロックを調べています。</span><span class="sxs-lookup"><span data-stu-id="77621-337">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="77621-338">ここから、次の構成要素を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="77621-338">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="77621-339">手と視線の追跡</span><span class="sxs-lookup"><span data-stu-id="77621-339">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="77621-340">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="77621-340">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="77621-341">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="77621-341">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="77621-342">いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="77621-342">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="77621-343">関連項目</span><span class="sxs-lookup"><span data-stu-id="77621-343">See also</span></span>

* [<span data-ttu-id="77621-344">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="77621-344">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="77621-345">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="77621-345">Motion controllers</span></span>](../../design/motion-controllers.md)