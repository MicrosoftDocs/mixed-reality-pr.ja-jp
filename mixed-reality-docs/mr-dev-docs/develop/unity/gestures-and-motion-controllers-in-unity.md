---
title: Unity でのジェスチャとモーション コントローラー
description: ハンドジェスチャとモーションコントローラーを使用して、Unity での操作を実行する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: ジェスチャ、モーションコントローラー、unity、宝石、入力、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: e1a2ae10638bb8dbd35eed7e9a0a1d2a05181f0c
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678651"
---
# <a name="gestures-and-motion-controllers-in-unity"></a><span data-ttu-id="cf95a-104">Unity でのジェスチャとモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="cf95a-104">Gestures and motion controllers in Unity</span></span>

<span data-ttu-id="cf95a-105">[Unity](gaze-in-unity.md)での操作を実行するには、2つの主要な方法があります。 HoloLens では[ハンドジェスチャ](../../design/gaze-and-commit.md#composite-gestures)と、HoloLens では[アニメーションコントローラー](../../design/motion-controllers.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="cf95a-106">Unity の同じ Api を使用して、空間入力の両方のソースのデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="cf95a-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="cf95a-107">Unity には、Windows Mixed Reality の空間入力データにアクセスするための主な方法が2つあります。複数の Unity XR Sdk 間で動作する common *input. GetButton/GetAxis* api と、使用可能な空間入力データの完全なセットを公開する Windows mixed reality に固有の *Interactionmanager/GestureRecognizer* api です。</span><span class="sxs-lookup"><span data-stu-id="cf95a-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality, the common *Input.GetButton/Input.GetAxis* APIs that work across multiple Unity XR SDKs, and an *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality that exposes the full set of spatial input data available.</span></span>

## <a name="unity-buttonaxis-mapping-table"></a><span data-ttu-id="cf95a-108">Unity ボタン/軸マッピングテーブル</span><span class="sxs-lookup"><span data-stu-id="cf95a-108">Unity button/axis mapping table</span></span>

<span data-ttu-id="cf95a-109">次の表に示すボタンと軸の Id は、Unity の Windows Mixed Reality の入力マネージャーでは、 *入力の GetButton/GetAxis* api を通じてサポートされていますが、"Windows MR 固有" の列では、 *Interactionsourcestate* 型から使用できるプロパティを参照しています。</span><span class="sxs-lookup"><span data-stu-id="cf95a-109">The button and axis IDs in the table below are supported in Unity's Input Manager for Windows Mixed Reality motion controllers through the *Input.GetButton/GetAxis* APIs, while the "Windows MR-specific" column refers to properties available off of the *InteractionSourceState* type.</span></span> <span data-ttu-id="cf95a-110">これらの各 Api の詳細については、以下のセクションで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-110">Each of these APIs are described in detail in the sections below.</span></span>

<span data-ttu-id="cf95a-111">Windows Mixed Reality のボタン/軸 ID マッピングは、通常、Oculus のボタン/軸 Id と一致します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-111">The button/axis ID mappings for Windows Mixed Reality generally match the Oculus button/axis IDs.</span></span>

<span data-ttu-id="cf95a-112">Windows Mixed Reality のボタン/軸 ID マッピングは、次の2つの方法で OpenVR のマッピングと異なります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-112">The button/axis ID mappings for Windows Mixed Reality differ from OpenVR's mappings in two ways:</span></span>
1. <span data-ttu-id="cf95a-113">このマッピングでは、サムスティックとは異なるタッチパッド Id を使用して、thumbsticks とタッチパッド向けの両方を持つコントローラーをサポートします。</span><span class="sxs-lookup"><span data-stu-id="cf95a-113">The mapping uses touchpad IDs that are distinct from thumbstick, to support controllers with both thumbsticks and touchpads.</span></span>
2. <span data-ttu-id="cf95a-114">このマッピングにより、メニューボタンの A および X ボタン Id のオーバーロードが回避され、物理 ABXY ボタンで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-114">The mapping avoids overloading the A and X button IDs for the Menu buttons, to leave those available for physical ABXY buttons.</span></span>

<table>
<tr>
<th rowspan="2"><span data-ttu-id="cf95a-115">入力</span><span class="sxs-lookup"><span data-stu-id="cf95a-115">Input</span></span> </th><th colspan="2"><span data-ttu-id="cf95a-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">一般的な Unity API</a></span><span class="sxs-lookup"><span data-stu-id="cf95a-116"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">Common Unity APIs</a></span></span><br /><span data-ttu-id="cf95a-117">(Input. GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="cf95a-117">(Input.GetButton/GetAxis)</span></span> </th><th rowspan="2"><span data-ttu-id="cf95a-118"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR 固有の入力 API</a></span><span class="sxs-lookup"><span data-stu-id="cf95a-118"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR-specific Input API</a></span></span><br /><span data-ttu-id="cf95a-119">XR.付い.代入</span><span class="sxs-lookup"><span data-stu-id="cf95a-119">(XR.WSA.Input)</span></span></th>
</tr><tr>
<th> <span data-ttu-id="cf95a-120">左側</span><span class="sxs-lookup"><span data-stu-id="cf95a-120">Left hand</span></span> </th><th> <span data-ttu-id="cf95a-121">Right</span><span class="sxs-lookup"><span data-stu-id="cf95a-121">Right hand</span></span></th>
</tr><tr>
<td> <span data-ttu-id="cf95a-122">押されたトリガーを選択</span><span class="sxs-lookup"><span data-stu-id="cf95a-122">Select trigger pressed</span></span> </td><td> <span data-ttu-id="cf95a-123">軸 9 = 1.0</span><span class="sxs-lookup"><span data-stu-id="cf95a-123">Axis 9 = 1.0</span></span> </td><td> <span data-ttu-id="cf95a-124">軸 10 = 1.0</span><span class="sxs-lookup"><span data-stu-id="cf95a-124">Axis 10 = 1.0</span></span> </td><td> <span data-ttu-id="cf95a-125">selectPressed れた</span><span class="sxs-lookup"><span data-stu-id="cf95a-125">selectPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-126">トリガーのアナログ値の選択</span><span class="sxs-lookup"><span data-stu-id="cf95a-126">Select trigger analog value</span></span> </td><td> <span data-ttu-id="cf95a-127">軸9</span><span class="sxs-lookup"><span data-stu-id="cf95a-127">Axis 9</span></span> </td><td> <span data-ttu-id="cf95a-128">軸10</span><span class="sxs-lookup"><span data-stu-id="cf95a-128">Axis 10</span></span> </td><td> <span data-ttu-id="cf95a-129">selectPressedAmount</span><span class="sxs-lookup"><span data-stu-id="cf95a-129">selectPressedAmount</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-130">一部押されたトリガーを選択</span><span class="sxs-lookup"><span data-stu-id="cf95a-130">Select trigger partially pressed</span></span> </td><td> <span data-ttu-id="cf95a-131">ボタン 14 <i>(ゲームパッド互換)</i> </span><span class="sxs-lookup"><span data-stu-id="cf95a-131">Button 14 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="cf95a-132">ボタン 15 <i>(ゲームパッド互換)</i> </span><span class="sxs-lookup"><span data-stu-id="cf95a-132">Button 15 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="cf95a-133">selectPressedAmount &gt; 0.0</span><span class="sxs-lookup"><span data-stu-id="cf95a-133">selectPressedAmount &gt; 0.0</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-134">押されたメニューボタン</span><span class="sxs-lookup"><span data-stu-id="cf95a-134">Menu button pressed</span></span> </td><td> <span data-ttu-id="cf95a-135">ボタン 6 \*</span><span class="sxs-lookup"><span data-stu-id="cf95a-135">Button 6\*</span></span> </td><td> <span data-ttu-id="cf95a-136">ボタン 7 \*</span><span class="sxs-lookup"><span data-stu-id="cf95a-136">Button 7\*</span></span> </td><td> <span data-ttu-id="cf95a-137">menuPressed</span><span class="sxs-lookup"><span data-stu-id="cf95a-137">menuPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-138">押されたグリップボタン</span><span class="sxs-lookup"><span data-stu-id="cf95a-138">Grip button pressed</span></span> </td><td> <span data-ttu-id="cf95a-139">軸 11 = 1.0 (アナログ値なし)</span><span class="sxs-lookup"><span data-stu-id="cf95a-139">Axis 11 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="cf95a-140">ボタン 4 <i>(ゲームパッド互換)</i> </span><span class="sxs-lookup"><span data-stu-id="cf95a-140">Button 4 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="cf95a-141">軸 12 = 1.0 (アナログ値なし)</span><span class="sxs-lookup"><span data-stu-id="cf95a-141">Axis 12 = 1.0 (no analog values)</span></span><br /><span data-ttu-id="cf95a-142">ボタン 5 <i>(ゲームパッド互換)</i> </span><span class="sxs-lookup"><span data-stu-id="cf95a-142">Button 5 <i>(gamepad compat)</i> </span></span></td><td> <span data-ttu-id="cf95a-143">grasped</span><span class="sxs-lookup"><span data-stu-id="cf95a-143">grasped</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-144">スティック X <i>(左:-1.0、右: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="cf95a-144">Thumbstick X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="cf95a-145">軸1</span><span class="sxs-lookup"><span data-stu-id="cf95a-145">Axis 1</span></span> </td><td> <span data-ttu-id="cf95a-146">軸4</span><span class="sxs-lookup"><span data-stu-id="cf95a-146">Axis 4</span></span> </td><td> <span data-ttu-id="cf95a-147">thumbstickPosition</span><span class="sxs-lookup"><span data-stu-id="cf95a-147">thumbstickPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-148">サムスティック Y <i>(上:-1.0、下: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="cf95a-148">Thumbstick Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="cf95a-149">軸2</span><span class="sxs-lookup"><span data-stu-id="cf95a-149">Axis 2</span></span> </td><td> <span data-ttu-id="cf95a-150">軸5</span><span class="sxs-lookup"><span data-stu-id="cf95a-150">Axis 5</span></span> </td><td> <span data-ttu-id="cf95a-151">thumbstickPosition</span><span class="sxs-lookup"><span data-stu-id="cf95a-151">thumbstickPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-152">押したサムスティック</span><span class="sxs-lookup"><span data-stu-id="cf95a-152">Thumbstick pressed</span></span> </td><td> <span data-ttu-id="cf95a-153">ボタン8</span><span class="sxs-lookup"><span data-stu-id="cf95a-153">Button 8</span></span> </td><td> <span data-ttu-id="cf95a-154">ボタン9</span><span class="sxs-lookup"><span data-stu-id="cf95a-154">Button 9</span></span> </td><td> <span data-ttu-id="cf95a-155">thumbstickPressed</span><span class="sxs-lookup"><span data-stu-id="cf95a-155">thumbstickPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-156">タッチパッド X <i>(左:-1.0、右: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="cf95a-156">Touchpad X <i>(left: -1.0, right: 1.0)</i> </span></span></td><td> <span data-ttu-id="cf95a-157">軸 17 \*</span><span class="sxs-lookup"><span data-stu-id="cf95a-157">Axis 17\*</span></span> </td><td> <span data-ttu-id="cf95a-158">軸 19 \*</span><span class="sxs-lookup"><span data-stu-id="cf95a-158">Axis 19\*</span></span> </td><td> <span data-ttu-id="cf95a-159">touchpadPosition</span><span class="sxs-lookup"><span data-stu-id="cf95a-159">touchpadPosition.x</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-160">タッチパッド Y <i>(上:-1.0、下: 1.0)</i> </span><span class="sxs-lookup"><span data-stu-id="cf95a-160">Touchpad Y <i>(top: -1.0, bottom: 1.0)</i> </span></span></td><td> <span data-ttu-id="cf95a-161">軸 18 \*</span><span class="sxs-lookup"><span data-stu-id="cf95a-161">Axis 18\*</span></span> </td><td> <span data-ttu-id="cf95a-162">軸 20 \*</span><span class="sxs-lookup"><span data-stu-id="cf95a-162">Axis 20\*</span></span> </td><td> <span data-ttu-id="cf95a-163">touchpadPosition</span><span class="sxs-lookup"><span data-stu-id="cf95a-163">touchpadPosition.y</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-164">タッチパッドにタッチ</span><span class="sxs-lookup"><span data-stu-id="cf95a-164">Touchpad touched</span></span> </td><td> <span data-ttu-id="cf95a-165">ボタン 18 \*</span><span class="sxs-lookup"><span data-stu-id="cf95a-165">Button 18\*</span></span> </td><td> <span data-ttu-id="cf95a-166">ボタン 19 \*</span><span class="sxs-lookup"><span data-stu-id="cf95a-166">Button 19\*</span></span> </td><td> <span data-ttu-id="cf95a-167">touchpadTouched</span><span class="sxs-lookup"><span data-stu-id="cf95a-167">touchpadTouched</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-168">タッチパッドが押されました</span><span class="sxs-lookup"><span data-stu-id="cf95a-168">Touchpad pressed</span></span> </td><td> <span data-ttu-id="cf95a-169">ボタン 16 \*</span><span class="sxs-lookup"><span data-stu-id="cf95a-169">Button 16\*</span></span> </td><td> <span data-ttu-id="cf95a-170">ボタン 17 \*</span><span class="sxs-lookup"><span data-stu-id="cf95a-170">Button 17\*</span></span> </td><td> <span data-ttu-id="cf95a-171">touchpadPressed</span><span class="sxs-lookup"><span data-stu-id="cf95a-171">touchpadPressed</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-172">6自由度グリップまたはポインターのポーズ</span><span class="sxs-lookup"><span data-stu-id="cf95a-172">6DoF grip pose or pointer pose</span></span> </td><td colspan="2"> <span data-ttu-id="cf95a-173"><i>グリップ</i> の発生のみ: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR。InputTracking。 GetLocalPosition</a></span><span class="sxs-lookup"><span data-stu-id="cf95a-173"><i>Grip</i> pose only: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR.InputTracking.GetLocalPosition</a></span></span><br /><span data-ttu-id="cf95a-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking。 GetLocalRotation</a></span><span class="sxs-lookup"><span data-stu-id="cf95a-174"><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking.GetLocalRotation</a></span></span></td><td> <span data-ttu-id="cf95a-175"><i>グリップ</i>または<i>ポインター</i>を引数として渡す: sourcestate</span><span class="sxs-lookup"><span data-stu-id="cf95a-175">Pass <i>Grip</i> or <i>Pointer</i> as an argument: sourceState.sourcePose.TryGetPosition</span></span><br /><span data-ttu-id="cf95a-176">sourceState。 TryGetRotation</span><span class="sxs-lookup"><span data-stu-id="cf95a-176">sourceState.sourcePose.TryGetRotation</span></span><br /></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-177">状態の追跡</span><span class="sxs-lookup"><span data-stu-id="cf95a-177">Tracking state</span></span> </td><td colspan="2"> <span data-ttu-id="cf95a-178"><i>位置の精度とソース損失リスクは MR 固有の API を介してのみ利用可能</i> </span><span class="sxs-lookup"><span data-stu-id="cf95a-178"><i>Position accuracy and source loss risk only available through MR-specific API</i> </span></span></td><td> <span data-ttu-id="cf95a-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState. Sourcestate の精度</a></span><span class="sxs-lookup"><span data-stu-id="cf95a-179"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState.sourcePose.positionAccuracy</a></span></span><br /><span data-ttu-id="cf95a-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. sourceLossRisk</a></span><span class="sxs-lookup"><span data-stu-id="cf95a-180"><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState.properties.sourceLossRisk</a></span></span></td>
</tr>
</table>

>[!NOTE]
><span data-ttu-id="cf95a-181">これらのボタン/軸 Id は、ゲームパッド、Oculus Touch、OpenVR で使用されるマッピングの競合により、Unity が OpenVR に使用する Id とは異なります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-181">These button/axis IDs differ from the IDs that Unity uses for OpenVR due to collisions in the mappings used by gamepads, Oculus Touch and OpenVR.</span></span>

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


## <a name="grip-pose-vs-pointing-pose"></a><span data-ttu-id="cf95a-182">グリップポーズとポインティングポーズ</span><span class="sxs-lookup"><span data-stu-id="cf95a-182">Grip pose vs. pointing pose</span></span>

<span data-ttu-id="cf95a-183">Windows Mixed Reality では、さまざまなフォームファクターでモーションコントローラーがサポートされています。各コントローラーの設計は、ユーザーの手の位置と、アプリがコントローラーを表示するときに使用する自然な "進む" 方向との間の関係において異なります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-183">Windows Mixed Reality supports motion controllers in a variety of form factors, with each controller's design differing in its relationship between the user's hand position and the natural "forward" direction that apps should use for pointing when rendering the controller.</span></span>

<span data-ttu-id="cf95a-184">これらのコントローラーをより適切に表現するために、それぞれの相互作用ソース、 **グリップ** の原因、および **ポインター** の種類に対して調査できる2種類の方法があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-184">To better represent these controllers, there are two kinds of poses you can investigate for each interaction source, the **grip pose** and the **pointer pose**.</span></span> <span data-ttu-id="cf95a-185">グリップとポインターの両方の座標は、グローバル Unity ワールド座標のすべての Unity Api によって表されます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-185">Both the grip pose and pointer pose coordinates are expressed by all Unity APIs in global Unity world coordinates.</span></span>

### <a name="grip-pose"></a><span data-ttu-id="cf95a-186">グリップの原因</span><span class="sxs-lookup"><span data-stu-id="cf95a-186">Grip pose</span></span>

<span data-ttu-id="cf95a-187">**グリップ** は、HoloLens によって検出された、または運動コントローラーを持つパームのいずれかの場所を表します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-187">The **grip pose** represents the location of either the palm of a hand detected by a HoloLens, or the palm holding a motion controller.</span></span>

<span data-ttu-id="cf95a-188">イマーシブヘッドセットでは、グリップは、 **ユーザーの手** や、剣や銃など、 **ユーザーの手に保持** されているオブジェクトをレンダリングするために最適です。</span><span class="sxs-lookup"><span data-stu-id="cf95a-188">On immersive headsets, the grip pose is best used to render **the user's hand** or **an object held in the user's hand**, such as a sword or gun.</span></span> <span data-ttu-id="cf95a-189">また、このグリップは、モーションコントローラーを視覚化するときにも使用されます。これは、モーションコントローラー用に Windows によって提供される **描画モデル** が、グリップを原点と回転の中心として使用するためです。</span><span class="sxs-lookup"><span data-stu-id="cf95a-189">The grip pose is also used when visualizing a motion controller, as the **renderable model** provided by Windows for a motion controller uses the grip pose as its origin and center of rotation.</span></span>

<span data-ttu-id="cf95a-190">グリップは、次のように明確に定義されます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-190">The grip pose is defined specifically as follows:</span></span>
* <span data-ttu-id="cf95a-191">**グリップの位置**: コントローラーを自然に保持するときのパーム重心。グリップ内の位置を中央に配置するように左右に調整されます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-191">The **grip position**: The palm centroid when holding the controller naturally, adjusted left or right to center the position within the grip.</span></span> <span data-ttu-id="cf95a-192">Windows Mixed Reality モーションコントローラーでは、通常、この位置はボタンをつかみに揃えて配置されます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-192">On the Windows Mixed Reality motion controller, this position generally aligns with the Grasp button.</span></span>
* <span data-ttu-id="cf95a-193">**グリップの向きの右軸**: 手を完全に開いて平らな5本の指を作成した場合 (左側のパームから前方、右側のパームから後方)、</span><span class="sxs-lookup"><span data-stu-id="cf95a-193">The **grip orientation's Right axis**: When you completely open your hand to form a flat 5-finger pose, the ray that is normal to your palm (forward from left palm, backward from right palm)</span></span>
* <span data-ttu-id="cf95a-194">**グリップの向きの前方軸**: ハンドを部分的に閉じた場合 (コントローラーを保持している場合と同様)、非表示の指で形成されたチューブを通過する光線。</span><span class="sxs-lookup"><span data-stu-id="cf95a-194">The **grip orientation's Forward axis**: When you close your hand partially (as if holding the controller), the ray that points "forward" through the tube formed by your non-thumb fingers.</span></span>
* <span data-ttu-id="cf95a-195">**グリップの向きの上位軸**: 右および順方向の定義によって暗黙的に示される上位軸。</span><span class="sxs-lookup"><span data-stu-id="cf95a-195">The **grip orientation's Up axis**: The Up axis implied by the Right and Forward definitions.</span></span>

<span data-ttu-id="cf95a-196">このグリップには、Unity のクロスベンダ入力 API (XR) を使用してアクセスでき *[ます。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation*) または WINDOWS MR 固有の API (*TryGetPosition/rotation*) を使用して、 **グリップ** ノードのポーズデータを要求します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-196">You can access the grip pose through either Unity's cross-vendor input API (*[XR.InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html).GetLocalPosition/Rotation*) or through the Windows MR-specific API (*sourceState.sourcePose.TryGetPosition/Rotation*, requesting pose data for the **Grip** node).</span></span>

### <a name="pointer-pose"></a><span data-ttu-id="cf95a-197">ポインターのポーズ</span><span class="sxs-lookup"><span data-stu-id="cf95a-197">Pointer pose</span></span>

<span data-ttu-id="cf95a-198">**ポインター** は、前方にあるコントローラーの先端を表します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-198">The **pointer pose** represents the tip of the controller pointing forward.</span></span>

<span data-ttu-id="cf95a-199">システム指定のポインターの raycast は、 **コントローラーモデル自体をレンダリング** するときに最もよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-199">The system-provided pointer pose is best used to raycast when you are **rendering the controller model itself**.</span></span> <span data-ttu-id="cf95a-200">仮想銃など、コントローラーの代わりに他の仮想オブジェクトをレンダリングする場合は、アプリ定義の銃モデルの胴体に沿って移動する射線など、その仮想オブジェクトに最も適した光線をポイントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-200">If you are rendering some other virtual object in place of the controller, such as a virtual gun, you should point with a ray that is most natural for that virtual object, such as a ray that travels along the barrel of the app-defined gun model.</span></span> <span data-ttu-id="cf95a-201">ユーザーは物理コントローラーではなく仮想オブジェクトを見ることができるため、仮想オブジェクトをポイントすると、アプリを使用している方がより自然な場合があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-201">Because users can see the virtual object and not the physical controller, pointing with the virtual object will likely be more natural for those using your app.</span></span>

<span data-ttu-id="cf95a-202">現時点では、ポインターの破壊は、Unity では、Windows MR 固有の API *TryGetPosition/ローテーション* を通じてのみ使用できます。引数として *Interactionsourcenode* を渡します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-202">Currently, the pointer pose is available in Unity only through the Windows MR-specific API, *sourceState.sourcePose.TryGetPosition/Rotation*, passing in *InteractionSourceNode.Pointer* as the argument.</span></span>

## <a name="controller-tracking-state"></a><span data-ttu-id="cf95a-203">コントローラー追跡状態</span><span class="sxs-lookup"><span data-stu-id="cf95a-203">Controller tracking state</span></span>

<span data-ttu-id="cf95a-204">ヘッドセットと同様に、Windows Mixed Reality モーションコントローラーでは、外部の追跡センサーを設定する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="cf95a-204">Like the headsets, the Windows Mixed Reality motion controller requires no setup of external tracking sensors.</span></span> <span data-ttu-id="cf95a-205">代わりに、コントローラーはヘッドセット自体のセンサーによって追跡されます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-205">Instead, the controllers are tracked by sensors in the headset itself.</span></span>

<span data-ttu-id="cf95a-206">ユーザーがヘッドセットのビューのフィールドからコントローラーを移動した場合、ほとんどの場合、Windows はコントローラーの位置を推測してアプリに提供し続けます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-206">If the user moves the controllers out of the headset's field of view, in most cases Windows will continue to infer controller positions and provide them to the app.</span></span> <span data-ttu-id="cf95a-207">コントローラーのビジュアル追跡が十分に失われた場合、コントローラーの位置はおおよその精度の位置にドロップします。</span><span class="sxs-lookup"><span data-stu-id="cf95a-207">When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span>

<span data-ttu-id="cf95a-208">この時点で、システムはコントローラーをユーザーにボディロックし、ユーザーが移動したときの位置を追跡しながら、内部方向センサーを使用してコントローラーの真向きを公開します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-208">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="cf95a-209">UI 要素をポイントしてアクティブ化するためにコントローラーを使用する多くのアプリは、ユーザーに気付かなくても、おおよその精度で正常に動作できます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-209">Many apps that use controllers to point at and activate UI elements can operate normally while in approximate accuracy without the user noticing.</span></span>

<span data-ttu-id="cf95a-210">これを実現する最善の方法は、自分で試してみることです。</span><span class="sxs-lookup"><span data-stu-id="cf95a-210">The best way to get a feel for this is to try it yourself.</span></span> <span data-ttu-id="cf95a-211">次のビデオでは、さまざまな追跡状態におけるモーションコントローラーで動作するイマーシブコンテンツの例を紹介しています。</span><span class="sxs-lookup"><span data-stu-id="cf95a-211">Check out this video with examples of immersive content that works with motion controllers across various tracking states:</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a><span data-ttu-id="cf95a-212">状態の明示的な追跡に関する推論</span><span class="sxs-lookup"><span data-stu-id="cf95a-212">Reasoning about tracking state explicitly</span></span>

<span data-ttu-id="cf95a-213">追跡の状態に基づいて位置を異なる方法で処理する必要があるアプリは、さらに詳細になり、コントローラーの状態 ( *SourceLossRisk* や *positionaccuracy* など) のプロパティを検査することができます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-213">Apps that wish to treat positions differently based on tracking state may go further and inspect properties on the controller's state, such as *SourceLossRisk* and *PositionAccuracy*:</span></span>

<table>
<tr>
<th> <span data-ttu-id="cf95a-214">状態の追跡</span><span class="sxs-lookup"><span data-stu-id="cf95a-214">Tracking state</span></span> </th><th> <span data-ttu-id="cf95a-215">SourceLossRisk</span><span class="sxs-lookup"><span data-stu-id="cf95a-215">SourceLossRisk</span></span> </th><th> <span data-ttu-id="cf95a-216">PositionAccuracy</span><span class="sxs-lookup"><span data-stu-id="cf95a-216">PositionAccuracy</span></span> </th><th> <span data-ttu-id="cf95a-217">TryGetPosition</span><span class="sxs-lookup"><span data-stu-id="cf95a-217">TryGetPosition</span></span></th>
</tr><tr>
<td> <span data-ttu-id="cf95a-218"><b>高精度</b> </span><span class="sxs-lookup"><span data-stu-id="cf95a-218"><b>High accuracy</b> </span></span></td><td style="background-color: green; color: white"> <span data-ttu-id="cf95a-219">&lt; 1.0</span><span class="sxs-lookup"><span data-stu-id="cf95a-219">&lt; 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="cf95a-220">高</span><span class="sxs-lookup"><span data-stu-id="cf95a-220">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="cf95a-221">true</span><span class="sxs-lookup"><span data-stu-id="cf95a-221">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-222"><b>高精度 (消失のリスク)</b> </span><span class="sxs-lookup"><span data-stu-id="cf95a-222"><b>High accuracy (at risk of losing)</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="cf95a-223">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="cf95a-223">== 1.0</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="cf95a-224">高</span><span class="sxs-lookup"><span data-stu-id="cf95a-224">High</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="cf95a-225">true</span><span class="sxs-lookup"><span data-stu-id="cf95a-225">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-226"><b>おおよその精度</b> </span><span class="sxs-lookup"><span data-stu-id="cf95a-226"><b>Approximate accuracy</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="cf95a-227">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="cf95a-227">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="cf95a-228">Approximate</span><span class="sxs-lookup"><span data-stu-id="cf95a-228">Approximate</span></span> </td><td style="background-color: green; color: white"> <span data-ttu-id="cf95a-229">true</span><span class="sxs-lookup"><span data-stu-id="cf95a-229">true</span></span></td>
</tr><tr>
<td> <span data-ttu-id="cf95a-230"><b>位置なし</b> </span><span class="sxs-lookup"><span data-stu-id="cf95a-230"><b>No position</b> </span></span></td><td style="background-color: orange"> <span data-ttu-id="cf95a-231">= = 1.0</span><span class="sxs-lookup"><span data-stu-id="cf95a-231">== 1.0</span></span> </td><td style="background-color: orange"> <span data-ttu-id="cf95a-232">Approximate</span><span class="sxs-lookup"><span data-stu-id="cf95a-232">Approximate</span></span> </td><td style="background-color: orange"> <span data-ttu-id="cf95a-233">false</span><span class="sxs-lookup"><span data-stu-id="cf95a-233">false</span></span></td>
</tr>
</table>

<span data-ttu-id="cf95a-234">これらのモーションコントローラーの追跡状態は、次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="cf95a-234">These motion controller tracking states are defined as follows:</span></span>
* <span data-ttu-id="cf95a-235">**高精度:** モーションコントローラーは、ヘッドセットのビューに含まれていますが、通常、ビジュアルの追跡に基づいて高精度の位置を提供します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-235">**High accuracy:** While the motion controller is within the headset's field of view, it will generally provide high-accuracy positions, based on visual tracking.</span></span> <span data-ttu-id="cf95a-236">ビューまたはのフィールドから瞬間的に見えない移動コントローラーは、(ユーザーの他の手によって) ヘッドセットセンサーから瞬間的に見えなくなっていることに注意してください。これは、コントローラー自体の慣性追跡に基づいて、短時間で高精度のポーズを返します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-236">Note that a moving controller that momentarily leaves the field of view or is momentarily obscured from the headset sensors (e.g. by the user's other hand) will continue to return high-accuracy poses for a short time, based on inertial tracking of the controller itself.</span></span>
* <span data-ttu-id="cf95a-237">**高精度 (損失のリスク):** ユーザーが、ヘッドセットのビューの端を越えてモーションコントローラーを動かすと、ヘッドセットはすぐにコントローラーの位置を視覚的に追跡できなくなります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-237">**High accuracy (at risk of losing):** When the user moves the motion controller past the edge of the headset's field of view, the headset will soon be unable to visually track the controller's position.</span></span> <span data-ttu-id="cf95a-238">アプリでは、 **SourceLossRisk** が1.0 に到達して、コントローラーがこの視界の境界に達したことを認識します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-238">The app knows when the controller has reached this FOV boundary by seeing the **SourceLossRisk** reach 1.0.</span></span> <span data-ttu-id="cf95a-239">その時点で、アプリは、非常に高品質なポーズの安定したストリームを必要とするコントローラージェスチャを一時停止することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-239">At that point, the app may choose to pause controller gestures that require a steady stream of very high-quality poses.</span></span>
* <span data-ttu-id="cf95a-240">**おおよその精度:** コントローラーのビジュアル追跡が十分に失われた場合、コントローラーの位置はおおよその精度の位置にドロップします。</span><span class="sxs-lookup"><span data-stu-id="cf95a-240">**Approximate accuracy:** When the controller has lost visual tracking for long enough, the controller's positions will drop to approximate-accuracy positions.</span></span> <span data-ttu-id="cf95a-241">この時点で、システムはコントローラーをユーザーにボディロックし、ユーザーが移動したときの位置を追跡しながら、内部方向センサーを使用してコントローラーの真向きを公開します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-241">At this point, the system will body-lock the controller to the user, tracking the user's position as they move around, while still exposing the controller's true orientation using its internal orientation sensors.</span></span> <span data-ttu-id="cf95a-242">UI 要素をポイントしてアクティブ化するためにコントローラーを使用する多くのアプリは、ユーザーに気付かずに正確な精度で、通常どおりに動作できます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-242">Many apps that use controllers to point at and activate UI elements can operate as normal while in approximate accuracy without the user noticing.</span></span> <span data-ttu-id="cf95a-243">入力要件が重いアプリでは、 **positionaccuracy** プロパティを調べることによって、精度が **高い** ことを **意味します**。たとえば、この期間中にユーザーに対して、オフスクリーンのターゲットに対してより多くのヒットボックスを与えることができます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-243">Apps with heavier input requirements may choose to sense this drop from **High** accuracy to **Approximate** accuracy by inspecting the **PositionAccuracy** property, for example to give the user a more generous hitbox on off-screen targets during this time.</span></span>
* <span data-ttu-id="cf95a-244">**位置なし:** コントローラーは長時間の精度で実行できますが、本体でロックされている位置が現時点では意味を持たないことをシステムが認識している場合があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-244">**No position:** While the controller can operate at approximate accuracy for a long time, sometimes the system knows that even a body-locked position is not meaningful at the moment.</span></span> <span data-ttu-id="cf95a-245">たとえば、電源が入っていたコントローラーが視覚的に観察されていない場合や、ユーザーがコントローラーを停止した後に他のユーザーが選択した場合などです。</span><span class="sxs-lookup"><span data-stu-id="cf95a-245">For example, a controller that was just turned on may have never been observed visually, or a user may put down a controller that's then picked up by someone else.</span></span> <span data-ttu-id="cf95a-246">これらのタイミングでは、システムはアプリに位置を提供せず、 *TryGetPosition* は false を返します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-246">At those times, the system will not provide any position to the app, and *TryGetPosition* will return false.</span></span>

## <a name="common-unity-apis-inputgetbuttongetaxis"></a><span data-ttu-id="cf95a-247">共通 Unity Api (Input. GetButton/GetAxis)</span><span class="sxs-lookup"><span data-stu-id="cf95a-247">Common Unity APIs (Input.GetButton/GetAxis)</span></span>

<span data-ttu-id="cf95a-248">**名前空間:** *unityengine*、 *unityengine XR*</span><span class="sxs-lookup"><span data-stu-id="cf95a-248">**Namespace:** *UnityEngine*, *UnityEngine.XR*</span></span><br>
<span data-ttu-id="cf95a-249">**型**: *Input*、 *XR。InputTracking*</span><span class="sxs-lookup"><span data-stu-id="cf95a-249">**Types**: *Input*, *XR.InputTracking*</span></span>

<span data-ttu-id="cf95a-250">Unity では、現在、一般的な *入力. GetButton/GetAxis* api を使用して、 [Oculus Sdk](https://docs.unity3d.com/Manual/OculusControllers.html)、 [Openvr SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) 、および Windows Mixed Reality の入力を公開しています。これには、ハンドアンドモーションコントローラーも含まれます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-250">Unity currently uses its general *Input.GetButton/Input.GetAxis* APIs to expose input for [the Oculus SDK](https://docs.unity3d.com/Manual/OculusControllers.html), [the OpenVR SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) and Windows Mixed Reality, including hands and motion controllers.</span></span> <span data-ttu-id="cf95a-251">アプリがこれらの Api を入力に使用する場合、Windows Mixed Reality を含む複数の XR Sdk 間で、モーションコントローラーを簡単にサポートできます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-251">If your app uses these APIs for input, it can easily support motion controllers across multiple XR SDKs, including Windows Mixed Reality.</span></span>

### <a name="getting-a-logical-buttons-pressed-state"></a><span data-ttu-id="cf95a-252">論理ボタンの押された状態の取得</span><span class="sxs-lookup"><span data-stu-id="cf95a-252">Getting a logical button's pressed state</span></span>

<span data-ttu-id="cf95a-253">一般的な Unity 入力 Api を使用するには、まず、 [Unity 入力マネージャー](https://docs.unity3d.com/Manual/ConventionalGameInput.html)で論理名にボタンと軸を配線し、ボタンまたは軸 id を各名前にバインドします。</span><span class="sxs-lookup"><span data-stu-id="cf95a-253">To use the general Unity input APIs, you'll typically start by wiring up buttons and axes to logical names in the [Unity Input Manager](https://docs.unity3d.com/Manual/ConventionalGameInput.html), binding a button or axis IDs to each name.</span></span> <span data-ttu-id="cf95a-254">その後、その論理ボタンと軸名を参照するコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-254">You can then write code that refers to that logical button/axis name.</span></span>

<span data-ttu-id="cf95a-255">たとえば、左モーションコントローラーの [トリガー] ボタンを [送信] アクションにマップするには、[ **編集 > プロジェクトの設定** ] に移動し、Unity 内の [入力] > て、[軸] の [送信] セクションのプロパティを展開します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-255">For example, to map the left motion controller's trigger button to the Submit action, go to **Edit > Project Settings > Input** within Unity, and expand the properties of the Submit section under Axes.</span></span> <span data-ttu-id="cf95a-256">次のように、 **正のボタン** または **Alt 陽性のボタン** プロパティを [ジョイスティックの読み取り **] ボタン 14** に変更します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-256">Change the **Positive Button** or **Alt Positive Button** property to read **joystick button 14**, like this:</span></span>

<span data-ttu-id="cf95a-257">![Unity の InputManager](images/unity-input-manager.png)</span><span class="sxs-lookup"><span data-stu-id="cf95a-257">![Unity's InputManager](images/unity-input-manager.png)</span></span><br>
<span data-ttu-id="cf95a-258">*Unity InputManager*</span><span class="sxs-lookup"><span data-stu-id="cf95a-258">*Unity InputManager*</span></span>

<span data-ttu-id="cf95a-259">スクリプトは、 *Input. GetButton* を使用して送信アクションを確認できます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-259">Your script can then check for the Submit action using *Input.GetButton*:</span></span>

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
<span data-ttu-id="cf95a-260">論理ボタンを追加するには、[**軸**] の [**サイズ**] プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-260">You can add more logical buttons by changing the **Size** property under **Axes**.</span></span>

### <a name="getting-a-physical-buttons-pressed-state-directly"></a><span data-ttu-id="cf95a-261">物理的なボタンの押された状態を直接取得する</span><span class="sxs-lookup"><span data-stu-id="cf95a-261">Getting a physical button's pressed state directly</span></span>

<span data-ttu-id="cf95a-262">*GetKey* を使用して、完全修飾名でボタンに手動でアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-262">You can also access buttons manually by their fully-qualified name, using *Input.GetKey*:</span></span>

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a><span data-ttu-id="cf95a-263">手や運動コントローラーのポーズ</span><span class="sxs-lookup"><span data-stu-id="cf95a-263">Getting a hand or motion controller's pose</span></span>

<span data-ttu-id="cf95a-264">XR を使用して、コントローラーの位置と回転にアクセスでき *ます。InputTracking*:</span><span class="sxs-lookup"><span data-stu-id="cf95a-264">You can access the position and rotation of the controller, using *XR.InputTracking*:</span></span>

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

<span data-ttu-id="cf95a-265">これはコントローラーのグリップ (ユーザーがコントローラーを保持している場所) を表します。これは、ユーザーの手に剣や銃をレンダリングする場合や、コントローラー自体のモデルをレンダリングする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="cf95a-265">Note that this represents the controller's grip pose (where the user holds the controller), which is useful for rendering a sword or gun in the user's hand, or a model of the controller itself.</span></span>

<span data-ttu-id="cf95a-266">このグリップとポインターの (コントローラーの先端が指している) 間のリレーションシップは、コントローラーによって異なる場合があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cf95a-266">Note that the relationship between this grip pose and the pointer pose (where the tip of the controller is pointing) may differ across controllers.</span></span> <span data-ttu-id="cf95a-267">現時点では、コントローラーのポインターにアクセスするには、次のセクションで説明する MR 固有の入力 API を使用するしかありません。</span><span class="sxs-lookup"><span data-stu-id="cf95a-267">At this moment, accessing the controller's pointer pose is only possible through the MR-specific input API, described in the sections below.</span></span>

## <a name="windows-specific-apis-xrwsainput"></a><span data-ttu-id="cf95a-268">Windows 固有の Api (XR。付い.代入</span><span class="sxs-lookup"><span data-stu-id="cf95a-268">Windows-specific APIs (XR.WSA.Input)</span></span>

<span data-ttu-id="cf95a-269">**名前空間:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="cf95a-269">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="cf95a-270">**型**: *interactionmanager*、 *interactionsourcestate*、 *interactionmanager*、 *interactionsourceproperties*、 *interactionsourcekind*、 *interactionmanager*</span><span class="sxs-lookup"><span data-stu-id="cf95a-270">**Types**: *InteractionManager*, *InteractionSourceState*, *InteractionSource*, *InteractionSourceProperties*, *InteractionSourceKind*, *InteractionSourceLocation*</span></span>

<span data-ttu-id="cf95a-271">Windows Mixed Reality の入力 (HoloLens) とモーションコントローラーの詳細情報を取得するには、 *XR* 名前空間で windows 固有の空間入力 api を使用することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-271">To get at more detailed information about Windows Mixed Reality hand input (for HoloLens) and motion controllers, you can choose to use the Windows-specific spatial input APIs under the *UnityEngine.XR.WSA.Input* namespace.</span></span> <span data-ttu-id="cf95a-272">これにより、位置の精度やソースの種類などの追加情報にアクセスして、ハンドとコントローラーを区別できます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-272">This lets you access additional information, such as position accuracy or the source kind, letting you tell hands and controllers apart.</span></span>

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a><span data-ttu-id="cf95a-273">ハンドコントローラーとモーションコントローラーの状態のポーリング</span><span class="sxs-lookup"><span data-stu-id="cf95a-273">Polling for the state of hands and motion controllers</span></span>

<span data-ttu-id="cf95a-274">このフレームの状態は、 *GetCurrentReading* メソッドを使用して、相互作用ソース (手動またはモーションコントローラー) ごとにポーリングできます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-274">You can poll for this frame's state for each interaction source (hand or motion controller) using the *GetCurrentReading* method.</span></span>

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

<span data-ttu-id="cf95a-275">返される各 *Interactionsourcestate* は、現在の時点の相互作用ソースを表します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-275">Each *InteractionSourceState* you get back represents an interaction source at the current moment in time.</span></span> <span data-ttu-id="cf95a-276">*Interactionsourcestate* は、次のような情報を公開します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-276">The *InteractionSourceState* exposes info such as:</span></span>
* <span data-ttu-id="cf95a-277">どのような [種類の押下](../../design/motion-controllers.md) が発生していますか (選択/メニュー/つかみ/タッチパッド/サムスティック)</span><span class="sxs-lookup"><span data-stu-id="cf95a-277">Which [kinds of presses](../../design/motion-controllers.md) are occurring (Select/Menu/Grasp/Touchpad/Thumbstick)</span></span>

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* <span data-ttu-id="cf95a-278">タッチパッドやサムスティックの XY 座標とタッチされた状態など、モーションコントローラー固有のその他のデータ</span><span class="sxs-lookup"><span data-stu-id="cf95a-278">Other data specific to motion controllers, such the touchpad and/or thumbstick's XY coordinates and touched state</span></span>

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* <span data-ttu-id="cf95a-279">ソースがハンドコントローラーであるか、モーションコントローラーであるかを知るための InteractionSourceKind</span><span class="sxs-lookup"><span data-stu-id="cf95a-279">The InteractionSourceKind to know if the source is a hand or a motion controller</span></span>

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a><span data-ttu-id="cf95a-280">前方予測レンダリングのポーリング</span><span class="sxs-lookup"><span data-stu-id="cf95a-280">Polling for forward-predicted rendering poses</span></span>

* <span data-ttu-id="cf95a-281">ハンドおよびコントローラーからの相互作用ソースデータをポーリングする場合、取得されるのは、このフレームの photons がユーザーの目に到達する瞬間を予測することです。</span><span class="sxs-lookup"><span data-stu-id="cf95a-281">When polling for interaction source data from hands and controllers, the poses you get are forward-predicted poses for the moment in time when this frame's photons will reach the user's eyes.</span></span>  <span data-ttu-id="cf95a-282">これらの前方予測は、コントローラーまたは保持されたオブジェクトを各フレームに **レンダリング** する場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="cf95a-282">These forward-predicted poses are best used for **rendering** the controller or a held object each frame.</span></span>  <span data-ttu-id="cf95a-283">コントローラーで特定のプレスまたはリリースを対象としている場合は、次に説明する履歴イベント Api を使用すると、そのことが最も正確になります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-283">If you are targeting a given press or release with the controller, that will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* <span data-ttu-id="cf95a-284">この現在のフレームの前方予測ヘッドを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-284">You can also get the forward-predicted head pose for this current frame.</span></span>  <span data-ttu-id="cf95a-285">ソースの場合と同様に、これはカーソルを **レンダリング** するときに便利です。ただし、次に説明する履歴イベント api を使用すると、特定のプレスまたはリリースをターゲットにすると最も正確になります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-285">As with the source pose, this is useful for **rendering** a cursor, although targeting a given press or release will be most accurate if you use the historical event APIs described below.</span></span>

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a><span data-ttu-id="cf95a-286">相互作用ソースイベントの処理</span><span class="sxs-lookup"><span data-stu-id="cf95a-286">Handling interaction source events</span></span>

<span data-ttu-id="cf95a-287">正確な履歴データで発生した入力イベントを処理するために、ポーリングではなく相互作用ソースイベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-287">To handle input events as they happen with their accurate historical pose data, you can handle interaction source events instead of polling.</span></span>

<span data-ttu-id="cf95a-288">相互作用ソースイベントを処理するには:</span><span class="sxs-lookup"><span data-stu-id="cf95a-288">To handle interaction source events:</span></span>
* <span data-ttu-id="cf95a-289">*Interactionmanager* 入力イベントに登録します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-289">Register for a *InteractionManager* input event.</span></span> <span data-ttu-id="cf95a-290">関心がある相互作用イベントの種類ごとに、サブスクライブする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-290">For each type of interaction event that you are interested in, you need to subscribe to it.</span></span>

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* <span data-ttu-id="cf95a-291">イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-291">Handle the event.</span></span> <span data-ttu-id="cf95a-292">相互作用イベントをサブスクライブすると、必要に応じてコールバックが取得されます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-292">Once you have subscribed to an interaction event, you will get the callback when appropriate.</span></span> <span data-ttu-id="cf95a-293">*Sourcepressed* れた例では、ソースが検出されてから解放されるか、または失われる前に、が発生します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-293">In the *SourcePressed* example, this will be after the source was detected and before it is released or lost.</span></span>

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

### <a name="how-to-stop-handling-an-event"></a><span data-ttu-id="cf95a-294">イベントの処理を停止する方法</span><span class="sxs-lookup"><span data-stu-id="cf95a-294">How to stop handling an event</span></span>

<span data-ttu-id="cf95a-295">イベントに関心がなくなった場合、またはイベントをサブスクライブしているオブジェクトを破棄する場合は、イベントの処理を停止する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-295">You need to stop handling an event when you are no longer interested in the event or you are destroying the object that has subscribed to the event.</span></span> <span data-ttu-id="cf95a-296">イベントの処理を停止するには、イベントのサブスクリプションを解除します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-296">To stop handling the event, you unsubscribe from the event.</span></span>

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a><span data-ttu-id="cf95a-297">相互作用ソースイベントの一覧</span><span class="sxs-lookup"><span data-stu-id="cf95a-297">List of interaction source events</span></span>

<span data-ttu-id="cf95a-298">使用可能な相互作用ソースイベントは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cf95a-298">The available interaction source events are:</span></span>
* <span data-ttu-id="cf95a-299">*Interactionsourcedetected 検出されました* (ソースがアクティブになります)</span><span class="sxs-lookup"><span data-stu-id="cf95a-299">*InteractionSourceDetected* (source becomes active)</span></span>
* <span data-ttu-id="cf95a-300">*Interactionsourcelost* (非アクティブになります)</span><span class="sxs-lookup"><span data-stu-id="cf95a-300">*InteractionSourceLost* (becomes inactive)</span></span>
* <span data-ttu-id="cf95a-301">*Interactionsourcepressed* れた (tap、button press、または "Select" 発音)</span><span class="sxs-lookup"><span data-stu-id="cf95a-301">*InteractionSourcePressed* (tap, button press, or "Select" uttered)</span></span>
* <span data-ttu-id="cf95a-302">*InteractionSourceReleased* (tap の終了、ボタンの解放、または "Select" 発音の最後)</span><span class="sxs-lookup"><span data-stu-id="cf95a-302">*InteractionSourceReleased* (end of a tap, button released, or end of "Select" uttered)</span></span>
* <span data-ttu-id="cf95a-303">*Interactionsourceupdated* (移動またはその他の状態の変更)</span><span class="sxs-lookup"><span data-stu-id="cf95a-303">*InteractionSourceUpdated* (moves or otherwise changes some state)</span></span>

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a><span data-ttu-id="cf95a-304">プレスまたはリリースと最も正確に一致する履歴ターゲットのイベント</span><span class="sxs-lookup"><span data-stu-id="cf95a-304">Events for historical targeting poses that most accurately match a press or release</span></span>

<span data-ttu-id="cf95a-305">前に説明したポーリング Api を使用すると、アプリが事前に予測されるようになります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-305">The polling APIs described earlier give your app forward-predicted poses.</span></span>  <span data-ttu-id="cf95a-306">これらの予測される値はコントローラーまたは仮想ハンドヘルドオブジェクトのレンダリングに最適ですが、2つの主な理由から、将来のターゲット設定には最適ではありません。</span><span class="sxs-lookup"><span data-stu-id="cf95a-306">While those predicted poses are best for rendering the controller or a virtual handheld object, future poses are not optimal for targeting, for two key reasons:</span></span>
* <span data-ttu-id="cf95a-307">ユーザーがコントローラーでボタンを押すと、システムが押される前に、Bluetooth 経由のワイヤレス待ち時間が20ミリ秒になることがあります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-307">When the user presses a button on a controller, there can be about 20ms of wireless latency over Bluetooth before the system receives the press.</span></span>
* <span data-ttu-id="cf95a-308">次に、前方予測攻撃を使用している場合、現在のフレームの photons がユーザーの目に到着するまでの時間を目標として、前方予測の別の 10 20 ミリ秒が適用されます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-308">Then, if you are using a forward-predicted pose, there would be another 10-20ms of forward prediction applied to target the time when the current frame's photons will reach the user's eyes.</span></span>

<span data-ttu-id="cf95a-309">これは、ポーリングによって、ユーザーの頭と針が、プレスまたはリリースが発生したときに実際に戻ってきた、発信元やヘッドが 30 ~ 40 ミリ秒であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-309">This means that polling gives you a source pose or head pose that is 30-40ms forward from where the user's head and hands actually were back when the press or release happened.</span></span>  <span data-ttu-id="cf95a-310">HoloLens の入力では、ワイヤレス転送の遅延は発生しませんが、押しを検出するために同様の処理遅延が発生します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-310">For HoloLens hand input, while there's no wireless transmission delay, there is a similar processing delay to detect the press.</span></span>

<span data-ttu-id="cf95a-311">ユーザーが手やコントローラーを押したときの本来の目的に基づいて正確にターゲットを指定するには、その *Interactionsourcepressed* れたイベントまたは *InteractionSourceReleased* 入力イベントからの履歴ソースの発生元またはヘッドポーズを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-311">To accurately target based on the user's original intent for a hand or controller press, you should use the historical source pose or head pose from that *InteractionSourcePressed* or *InteractionSourceReleased* input event.</span></span>

<span data-ttu-id="cf95a-312">ユーザーのヘッドまたはコントローラーの履歴リーダーデータを使用して、プレスまたはリリースを対象にすることができます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-312">You can target a press or release with historical pose data from the user's head or their controller:</span></span>
* <span data-ttu-id="cf95a-313">ジェスチャまたはコントローラーの押下が発生した時点で、[ユーザーがどの](../../design/gaze-and-commit.md)ようにしているかを **判断するため** に使用できます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-313">The head pose at the moment in time when a gesture or controller press occurred, which can be used for **targeting** to determine what the user was [gazing](../../design/gaze-and-commit.md) at:</span></span>

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

* <span data-ttu-id="cf95a-314">モーションコントローラーの押下が発生した時点のソースは、ユーザーがコントローラーを指していた **対象を判別するため** に使用できます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-314">The source pose at the moment in time when a motion controller press occurred, which can be used for **targeting** to determine what the user was pointing the controller at.</span></span>  <span data-ttu-id="cf95a-315">これは、押下を経験したコントローラーの状態になります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-315">This will be the state of the controller that experienced the press.</span></span>  <span data-ttu-id="cf95a-316">コントローラー自体をレンダリングする場合は、グリップの原因ではなくポインターのポーズを要求できます。これにより、レンダリングされたコントローラーの自然なヒントをユーザーが考慮しているものからターゲットの射線にシュートすることができます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-316">If you are rendering the controller itself, you can request the pointer pose rather than the grip pose, to shoot the targeting ray from what the user will consider the natural tip of that rendered controller:</span></span>

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

### <a name="event-handlers-example"></a><span data-ttu-id="cf95a-317">イベントハンドラーの例</span><span class="sxs-lookup"><span data-stu-id="cf95a-317">Event handlers example</span></span>

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="cf95a-318">高レベル複合ジェスチャ Api (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="cf95a-318">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="cf95a-319">**名前空間:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="cf95a-319">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="cf95a-320">**型**: *GestureRecognizer*、 *GestureSettings*、 *interactionsourcekind*</span><span class="sxs-lookup"><span data-stu-id="cf95a-320">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="cf95a-321">アプリでは、空間入力ソース、タップ、ホールド、操作、およびナビゲーションジェスチャに対する高レベルの複合ジェスチャを認識することもできます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-321">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation and Navigation gestures.</span></span> <span data-ttu-id="cf95a-322">GestureRecognizer を使用して、[ハンド](../../design/gaze-and-commit.md#composite-gestures)[コントローラーとモーションコントローラー](../../design/motion-controllers.md)の両方でこれらの複合ジェスチャを認識できます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-322">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="cf95a-323">GestureRecognizer の各ジェスチャイベントは、イベントの発生時に、入力とターゲットのヘッドレイを提供します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-323">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="cf95a-324">一部のイベントは、追加のコンテキスト固有の情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-324">Some events provide additional context specific information.</span></span>

<span data-ttu-id="cf95a-325">ジェスチャ認識エンジンを使用してジェスチャをキャプチャするには、いくつかの手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-325">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="cf95a-326">新しいジェスチャ認識エンジンを作成する</span><span class="sxs-lookup"><span data-stu-id="cf95a-326">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="cf95a-327">監視するジェスチャを指定する</span><span class="sxs-lookup"><span data-stu-id="cf95a-327">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="cf95a-328">これらのジェスチャのイベントをサブスクライブする</span><span class="sxs-lookup"><span data-stu-id="cf95a-328">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="cf95a-329">ジェスチャのキャプチャを開始する</span><span class="sxs-lookup"><span data-stu-id="cf95a-329">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="cf95a-330">新しいジェスチャ認識エンジンを作成する</span><span class="sxs-lookup"><span data-stu-id="cf95a-330">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="cf95a-331">*GestureRecognizer* を使用するには、 *GestureRecognizer* を作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-331">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="cf95a-332">監視するジェスチャを指定する</span><span class="sxs-lookup"><span data-stu-id="cf95a-332">Specify which gestures to watch for</span></span>

<span data-ttu-id="cf95a-333">*Set認識 Izableジェスチャー ()* を使用して、興味のあるジェスチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-333">Specify which gestures you are interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="cf95a-334">これらのジェスチャのイベントをサブスクライブする</span><span class="sxs-lookup"><span data-stu-id="cf95a-334">Subscribe to events for those gestures</span></span>

<span data-ttu-id="cf95a-335">関心のあるジェスチャのイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="cf95a-335">Subscribe to events for the gestures you are interested in.</span></span>

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
><span data-ttu-id="cf95a-336">ナビゲーションと操作のジェスチャは、 *GestureRecognizer* のインスタンスで相互に排他的です。</span><span class="sxs-lookup"><span data-stu-id="cf95a-336">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="cf95a-337">ジェスチャのキャプチャを開始する</span><span class="sxs-lookup"><span data-stu-id="cf95a-337">Start capturing gestures</span></span>

<span data-ttu-id="cf95a-338">既定では、 *GestureRecognizer* は、 *Startcapturinggestures ()* が呼び出されるまで、入力を監視しません。</span><span class="sxs-lookup"><span data-stu-id="cf95a-338">By default, a *GestureRecognizer* does not monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="cf95a-339">Stopcapturinggestures () が *処理されたフレーム* の前に入力が実行された場合、 *Stopcapturinggestures ()* が呼び出された後にジェスチャイベントが生成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-339">It is possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="cf95a-340">*GestureRecognizer* は、ジェスチャが実際に発生した前のフレームでオンまたはオフにされたかどうかを記憶します。そのため、このフレームのターゲット設定に基づいてジェスチャの監視を開始および停止することができます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-340">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it is reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="cf95a-341">ジェスチャのキャプチャを停止します</span><span class="sxs-lookup"><span data-stu-id="cf95a-341">Stop capturing gestures</span></span>

<span data-ttu-id="cf95a-342">ジェスチャ認識を停止するには:</span><span class="sxs-lookup"><span data-stu-id="cf95a-342">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="cf95a-343">ジェスチャ認識エンジンの削除</span><span class="sxs-lookup"><span data-stu-id="cf95a-343">Removing a gesture recognizer</span></span>

<span data-ttu-id="cf95a-344">*GestureRecognizer* オブジェクトを破棄する前に、サブスクライブされたイベントのサブスクリプションを解除してください。</span><span class="sxs-lookup"><span data-stu-id="cf95a-344">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="cf95a-345">Unity でのモーションコントローラーモデルのレンダリング</span><span class="sxs-lookup"><span data-stu-id="cf95a-345">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="cf95a-346">![モーションコントローラーモデルとテレ](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="cf95a-346">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="cf95a-347">*モーションコントローラーモデルとテレ*</span><span class="sxs-lookup"><span data-stu-id="cf95a-347">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="cf95a-348">ユーザーが保持している物理コントローラーに一致するモーションコントローラーをアプリでレンダリングし、さまざまなボタンが押されていることを明確にするために、 [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/)で **motioncontroller prefab** を使用できます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-348">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="cf95a-349">この prefab は、システムのインストールされている motion controller ドライバーから、実行時に正しい glTF モデルを動的に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-349">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="cf95a-350">これらのモデルは、エディターで手動でインポートするのではなく、動的に読み込むことが重要です。これにより、ユーザーが現在使用しているコントローラーと将来のコントローラーに対して、アプリケーションで物理的に正確な3D モデルが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-350">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="cf95a-351">[はじめに](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)の手順に従って、Mixed Reality Toolkit をダウンロードし、Unity プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-351">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="cf95a-352">はじめにの手順の一部としてカメラを *MixedRealityCameraParent* prefab に置き換えると、お勧めします。</span><span class="sxs-lookup"><span data-stu-id="cf95a-352">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="cf95a-353">この事前 fab には、モーションコントローラーレンダリングが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cf95a-353">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="cf95a-354">それ以外の場合は、 *Assets/HoloToolkit/Input/Prefabs/MotionControllers* を [プロジェクト] ウィンドウからシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-354">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="cf95a-355">この prefab は、シーン内のユーザーが携帯電話に接続しているときに、カメラを移動するために使用する親オブジェクトの子として追加します。これにより、コントローラーはユーザーと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-355">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="cf95a-356">アプリにテレが含まれていない場合は、シーンのルートに prefab を追加するだけです。</span><span class="sxs-lookup"><span data-stu-id="cf95a-356">If your app does not involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="cf95a-357">オブジェクトのスロー</span><span class="sxs-lookup"><span data-stu-id="cf95a-357">Throwing objects</span></span>

<span data-ttu-id="cf95a-358">仮想現実のオブジェクトをスローすると、問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-358">Throwing objects in virtual reality is a harder problem then it may at first seem.</span></span> <span data-ttu-id="cf95a-359">ほとんどの物理的な相互作用と同様に、ゲームでのスローが予期しない方法で動作する場合は、すぐに明らかになり、immersion が壊れることがあります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-359">As with most physically based interactions, when throwing in game acts in an unexpected way, it is immediately obvious and breaks immersion.</span></span> <span data-ttu-id="cf95a-360">私たちは、物理的に正しいスロー動作を表す方法について、少し時間をかけてきました。また、お客様と共有するプラットフォームの更新によって有効になるガイドラインがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-360">We have spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="cf95a-361">スローを実装する方法の例については、 [こちら](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cf95a-361">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="cf95a-362">このサンプルは、次の4つのガイドラインに従います。</span><span class="sxs-lookup"><span data-stu-id="cf95a-362">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="cf95a-363">**位置ではなく、コントローラーの *ベロシティ* を使用** します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-363">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="cf95a-364">Windows の11月の更新プログラムでは、 [' ' 概算 ' ' 位置追跡状態](../../design/motion-controllers.md#controller-tracking-state)での動作の変更が導入されました。</span><span class="sxs-lookup"><span data-stu-id="cf95a-364">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="cf95a-365">この状態になっている場合、コントローラーに関する速度情報は、高い精度であると考えられている限り、継続的に報告されます。これは、位置が高精度のままである場合もあります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-365">When in this state, velocity information about the controller will continue to be reported for as long as we believe it is high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="cf95a-366">**コントローラーの *角速度* を組み込み** ます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-366">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="cf95a-367">このロジックはすべて、上記の `throwing.cs` リンクされ `GetThrownObjectVelAngVel` たパッケージ内の静的メソッドのファイルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="cf95a-367">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="cf95a-368">角速度が節約であるため、スローされたオブジェクトは、スローの時点と同じ角度速度を維持する必要があります。 `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="cf95a-368">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="cf95a-369">スローされたオブジェクトの質量の中心がグリップの原因ではない可能性があるため、ユーザーの参照フレーム内のコントローラーの速度が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-369">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity then that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="cf95a-370">この方法で発生したオブジェクトのベロシティの部分は、コントローラーの原点を中心としてスローされたオブジェクトの質量の中心となる瞬間流速度です。</span><span class="sxs-lookup"><span data-stu-id="cf95a-370">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="cf95a-371">この接線速度は、コントローラーの原点と、スローされたオブジェクトの質量の中心との距離を表すベクトルを使用して、コントローラーの角速度のクロス積です。</span><span class="sxs-lookup"><span data-stu-id="cf95a-371">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="cf95a-372">したがって、スローされたオブジェクトの合計速度は、コントローラーのベロシティとこの接線速度の合計になります。 `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="cf95a-372">The total velocity of the thrown object is thus the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="cf95a-373">**速度を適用する *時間* に細心の注意を** 払ってください。</span><span class="sxs-lookup"><span data-stu-id="cf95a-373">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="cf95a-374">ボタンが押されると、そのイベントが Bluetooth 経由でオペレーティングシステムに20ミリ秒になるまでに最大の時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-374">When a button is pressed, it can take up to 20ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="cf95a-375">これは、コントローラーの状態の変化をポーリングしたときに、押されていない状態や押されていない状態の変化をポーリングした場合に、そのコントローラーの状態が変更される前に発生します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-375">This means that if you poll for a controller state change from pressed to not pressed or vice versa, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="cf95a-376">さらに、ポーリング API によって提示されるコントローラーは、フレームが表示されるときに発生する可能性があることを反映するためにフォワード予測が行われます。これは、今後20ミリ秒される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-376">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more then 20ms in the future.</span></span> <span data-ttu-id="cf95a-377">これは、保持されたオブジェクトを *レンダリング* する場合に適していますが、ユーザーがスローをリリースした瞬間の軌道を計算するときに、オブジェクトを *ターゲット* にするための時間の問題が複雑になります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-377">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released their throw.</span></span> <span data-ttu-id="cf95a-378">幸いにも、11月の更新プログラムでは、 *Interactionsourcepressed* または *InteractionSourceReleased* のような Unity イベントが送信されたときに、ボタンが実際に押されたとき、または解放されたときの履歴の表示データが状態に含まれています。</span><span class="sxs-lookup"><span data-stu-id="cf95a-378">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was actually pressed or released.</span></span>  <span data-ttu-id="cf95a-379">スロー中に正確なコントローラーレンダリングとコントローラーターゲットを取得するには、必要に応じて、ポーリングとイベントを正しく使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-379">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="cf95a-380">コントローラーが各フレームを **レンダリング** する場合、アプリは、現在のフレームの photon 時間に合わせて、コントローラーの *オブジェクト* を前方予測コントローラーに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-380">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="cf95a-381">このデータは、XR のような Unity ポーリング Api から取得し *[ます。InputTracking。 GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* または *[XR。付い.GetCurrentReading を入力し](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* ます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-381">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="cf95a-382">プレスまたはリリースを対象とする **コントローラー** の場合、アプリは、そのプレスまたはリリースイベントのコントローラーの履歴に基づいて、軌道を raycast して計算する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cf95a-382">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="cf95a-383">このデータは、Interactionmanager と同様に Unity イベント Api から取得し *[ます。 Interactionsource押さ](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* れています。</span><span class="sxs-lookup"><span data-stu-id="cf95a-383">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="cf95a-384">**グリップを使用** します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-384">**Use the grip pose**.</span></span> <span data-ttu-id="cf95a-385">角速度とベロシティは、ポインターではなく、グリップによって報告されます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-385">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="cf95a-386">今後の Windows 更新プログラムでは、のスローが引き続き改善され、詳細についてはここで確認できます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-386">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a><span data-ttu-id="cf95a-387">MRTK v2 のジェスチャとモーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="cf95a-387">Gesture and Motion Controllers in MRTK v2</span></span>

<span data-ttu-id="cf95a-388">入力マネージャーからジェスチャとモーションコントローラーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-388">You can access gesture and motion controller from the input Manager.</span></span>
* [<span data-ttu-id="cf95a-389">MRTK v2 でのジェスチャ</span><span class="sxs-lookup"><span data-stu-id="cf95a-389">Gesture in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [<span data-ttu-id="cf95a-390">MRTK v2 のモーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="cf95a-390">Motion Controller in MRTK v2</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a><span data-ttu-id="cf95a-391">チュートリアルに従う</span><span class="sxs-lookup"><span data-stu-id="cf95a-391">Follow along with tutorials</span></span>

<span data-ttu-id="cf95a-392">詳細なカスタマイズ例が記載されたステップバイステップのチュートリアルは、Mixed Reality Academy でご利用いただけます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-392">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="cf95a-393">MR 入力 211:ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="cf95a-393">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="cf95a-394">MR 入力 213:モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="cf95a-394">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="cf95a-395">[![MR 入力 213-モーションコントローラー](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="cf95a-395">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="cf95a-396">*MR 入力 213-モーションコントローラー*</span><span class="sxs-lookup"><span data-stu-id="cf95a-396">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="cf95a-397">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="cf95a-397">Next Development Checkpoint</span></span>

<span data-ttu-id="cf95a-398">私たちが用意した Unity 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-398">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="cf95a-399">ここから、次の構成要素に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-399">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cf95a-400">手と視線の追跡</span><span class="sxs-lookup"><span data-stu-id="cf95a-400">Hand and eye tracking</span></span>](hand-eye-in-unit.md)

<span data-ttu-id="cf95a-401">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="cf95a-401">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cf95a-402">共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="cf95a-402">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="cf95a-403">いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="cf95a-403">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf95a-404">関連項目</span><span class="sxs-lookup"><span data-stu-id="cf95a-404">See also</span></span>

* [<span data-ttu-id="cf95a-405">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="cf95a-405">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="cf95a-406">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="cf95a-406">Motion controllers</span></span>](../../design/motion-controllers.md)
