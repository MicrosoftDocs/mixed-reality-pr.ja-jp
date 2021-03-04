---
title: 対話可能なオブジェクト
description: さまざまな現実のアプリケーションでイベントをトリガーしたり、視覚的な手掛かりを提供したり、オブジェクトと対話したりする方法について説明します。
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: 混合現実、コントロール、対話、キュー、ui、ux、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、audio
ms.openlocfilehash: b93092b597d0267c1169cf823b1a5c1fa03c3c3f
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759878"
---
# <a name="interactable-object"></a><span data-ttu-id="3de6b-104">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="3de6b-104">Interactable object</span></span>

![Interactible オブジェクト](images/UX_Hero_Interactable.jpg)

<span data-ttu-id="3de6b-106">ボタンは、2D 抽象ワールドでイベントをトリガーするために使用される比喩です。</span><span class="sxs-lookup"><span data-stu-id="3de6b-106">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="3de6b-107">3次元混合の現実世界では、この抽象化の世界に限定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="3de6b-107">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="3de6b-108">イベントをトリガーする **対話型オブジェクト** を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3de6b-108">Anything can be an **interactable object** that triggers an event.</span></span> <span data-ttu-id="3de6b-109">対話型オブジェクトは、テーブル上のコーヒーカップから、アウト・エアのバルーンに至るまで、あらゆるものを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="3de6b-109">An interactable object can be anything from a coffee cup on a table to a balloon in midair.</span></span> <span data-ttu-id="3de6b-110">ダイアログ UI などの特定の状況では、従来のボタンを引き続き使用します。</span><span class="sxs-lookup"><span data-stu-id="3de6b-110">We still do make use of traditional buttons in certain situation such as in dialog UI.</span></span> <span data-ttu-id="3de6b-111">ボタンのビジュアル表現は、コンテキストによって異なります。</span><span class="sxs-lookup"><span data-stu-id="3de6b-111">The visual representation of the button depends on the context.</span></span>

<br>

---

## <a name="important-properties-of-the-interactable-object"></a><span data-ttu-id="3de6b-112">対話型オブジェクトの重要なプロパティ</span><span class="sxs-lookup"><span data-stu-id="3de6b-112">Important properties of the interactable object</span></span>

### <a name="visual-cues"></a><span data-ttu-id="3de6b-113">視覚的な合図</span><span class="sxs-lookup"><span data-stu-id="3de6b-113">Visual cues</span></span>

<span data-ttu-id="3de6b-114">視覚的な手掛かりとは、ライトからの sensory 合図、目が見てきたこと、視覚認識中にビジュアルシステムによって処理されることです。</span><span class="sxs-lookup"><span data-stu-id="3de6b-114">Visual cues are sensory cues from light, received by the eye, and processed by the visual system during visual perception.</span></span> <span data-ttu-id="3de6b-115">ビジュアルシステムは多くの人、特に人間にとって最も重要であるため、視覚的な手掛かりは、世界の知覚に関する情報源です。</span><span class="sxs-lookup"><span data-stu-id="3de6b-115">Since the visual system is dominant in many species, especially humans, visual cues are a large source of information in how the world is perceived.</span></span>

<span data-ttu-id="3de6b-116">Holographic オブジェクトは、mixed reality の実際の環境とブレンドされるため、対話できるオブジェクトを理解するのが困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="3de6b-116">Since the holographic objects are blended with the real-world environment in mixed reality, it could be difficult to understand which objects you can interact with.</span></span> <span data-ttu-id="3de6b-117">対話型オブジェクトについては、各入力状態の視覚的な手掛かりを区別することが重要です。</span><span class="sxs-lookup"><span data-stu-id="3de6b-117">For any interactable objects in your experience, it's important to provide differentiated visual cues for each input state.</span></span> <span data-ttu-id="3de6b-118">これにより、ユーザーは、エクスペリエンスのどの部分が対話型されているかを理解し、一貫性のある対話方式を使用してユーザーの信頼を得られるようになります。</span><span class="sxs-lookup"><span data-stu-id="3de6b-118">This helps the user understand which part of your experience is interactable and makes the user confident by using a consistent interaction method.</span></span>

<br>

---

### <a name="far-interactions"></a><span data-ttu-id="3de6b-119">遠くのやり取り</span><span class="sxs-lookup"><span data-stu-id="3de6b-119">Far interactions</span></span>

<span data-ttu-id="3de6b-120">ユーザーが宝石、ハンドレイ、およびモーションコントローラーの射線と対話できるオブジェクトについては、次の3つの入力状態に対して異なる視覚的な合図を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3de6b-120">For any objects that user can interact with gaze, hand ray, and motion controller's ray, we recommend having different visual cue for these three input states:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="3de6b-121">![既定の状態の対話型オブジェクト](images/interactibleobject-states-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-121">![Interactable object with default state](images/interactibleobject-states-default.jpg)</span></span><br>
       <span data-ttu-id="3de6b-122">**既定 (監視) の状態**</span><span class="sxs-lookup"><span data-stu-id="3de6b-122">**Default (Observation) state**</span></span><br>
        <span data-ttu-id="3de6b-123">オブジェクトの既定のアイドル状態。</span><span class="sxs-lookup"><span data-stu-id="3de6b-123">Default idle state of the object.</span></span>
    <span data-ttu-id="3de6b-124">カーソルがオブジェクト上にありません。</span><span class="sxs-lookup"><span data-stu-id="3de6b-124">The cursor isn't on the object.</span></span> <span data-ttu-id="3de6b-125">ハンドが検出されません。</span><span class="sxs-lookup"><span data-stu-id="3de6b-125">Hand isn't detected.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3de6b-126">![ターゲットとホバー状態の対話型オブジェクト](images/interactibleobject-states-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-126">![Interactable object with target and hover state](images/interactibleobject-states-targeted.jpg)</span></span><br>
        <span data-ttu-id="3de6b-127">**ターゲット (ホバー) 状態**</span><span class="sxs-lookup"><span data-stu-id="3de6b-127">**Targeted (Hover) state**</span></span><br>
        <span data-ttu-id="3de6b-128">オブジェクトが、見つめカーソル、指近接、またはモーションコントローラーのポインターの対象になっている場合。</span><span class="sxs-lookup"><span data-stu-id="3de6b-128">When the object is targeted with gaze cursor, finger proximity or motion controller's pointer.</span></span>
    <span data-ttu-id="3de6b-129">カーソルがオブジェクト上にあります。</span><span class="sxs-lookup"><span data-stu-id="3de6b-129">The cursor is on the object.</span></span> <span data-ttu-id="3de6b-130">ハンドが検出され、準備が完了しました。</span><span class="sxs-lookup"><span data-stu-id="3de6b-130">Hand is detected, ready.</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3de6b-131">![押された状態の対話型オブジェクト](images/interactibleobject-states-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-131">![Interactable object with pressed state](images/interactibleobject-states-pressed.jpg)</span></span><br>
       <span data-ttu-id="3de6b-132">**押された状態**</span><span class="sxs-lookup"><span data-stu-id="3de6b-132">**Pressed state**</span></span><br>
        <span data-ttu-id="3de6b-133">オブジェクトがエアタップジェスチャで押されたときに、指を押すか、モーションコントローラーの [選択] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3de6b-133">When the object is pressed with an air tap gesture, finger press or motion controller's select button.</span></span>
    <span data-ttu-id="3de6b-134">カーソルがオブジェクト上にあります。</span><span class="sxs-lookup"><span data-stu-id="3de6b-134">The cursor is on the object.</span></span> <span data-ttu-id="3de6b-135">ハンドが検出されました。</span><span class="sxs-lookup"><span data-stu-id="3de6b-135">Hand is detected, air tapped.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

<span data-ttu-id="3de6b-136">強調表示や拡大/縮小などの手法を使用して、ユーザーの入力状態を視覚的に示すことができます。</span><span class="sxs-lookup"><span data-stu-id="3de6b-136">You can use techniques such as highlighting or scaling to provide visual cues for the user’s input state.</span></span> <span data-ttu-id="3de6b-137">Mixed reality では、[スタート] メニューとアプリバーボタンを使用してさまざまな入力状態を視覚化する例を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="3de6b-137">In mixed reality, you can find examples of visualizing different input states on the Start menu and with app bar buttons.</span></span> 

<span data-ttu-id="3de6b-138">**Holographic ボタン** では、これらの状態は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3de6b-138">Here's what these states look like on a **holographic button**:</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="3de6b-139">![既定の状態の Holographic ボタン](images/MRTK_InteractableState-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-139">![Holographic button in default state](images/MRTK_InteractableState-default.jpg)</span></span><br>
       <span data-ttu-id="3de6b-140">**既定 (監視) の状態**</span><span class="sxs-lookup"><span data-stu-id="3de6b-140">**Default (Observation) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3de6b-141">![ターゲットとホバー状態の Holographic ボタン](images/MRTK_InteractableState-targeted.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-141">![Holographic button in target and hover state](images/MRTK_InteractableState-targeted.jpg)</span></span><br>
        <span data-ttu-id="3de6b-142">**ターゲット (ホバー) 状態**</span><span class="sxs-lookup"><span data-stu-id="3de6b-142">**Targeted (Hover) state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="3de6b-143">![押された状態の Holographic ボタン](images/MRTK_InteractableState-pressed.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-143">![Holographic button in pressed state](images/MRTK_InteractableState-pressed.jpg)</span></span><br>
       <span data-ttu-id="3de6b-144">**押された状態**</span><span class="sxs-lookup"><span data-stu-id="3de6b-144">**Pressed state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a><span data-ttu-id="3de6b-145">Near 相互作用 (ダイレクト)</span><span class="sxs-lookup"><span data-stu-id="3de6b-145">Near interactions (direct)</span></span> 

<span data-ttu-id="3de6b-146">HoloLens 2 では、オブジェクトとの対話を可能にする、手による追跡入力をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3de6b-146">HoloLens 2 supports articulated hand tracking input, which allows you to interact with objects.</span></span> <span data-ttu-id="3de6b-147">Haptic のフィードバックや完全な深さの認識がなければ、オブジェクトから手の外に出てきたことや、それに触れるかどうかを判断するのは困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="3de6b-147">Without haptic feedback and perfect depth perception, it can be hard to tell how far away your hand is from an object or whether you're touching it.</span></span> <span data-ttu-id="3de6b-148">オブジェクトの状態を伝えるのに十分な視覚的な手掛かりを提供することが重要です。特に、そのオブジェクトに基づいて実際の状態を伝えます。</span><span class="sxs-lookup"><span data-stu-id="3de6b-148">It's important to provide enough visual cues to communicate the state of the object, in particular the state of your hands based on that object.</span></span>

<span data-ttu-id="3de6b-149">視覚的フィードバックを使用して、次の状態を伝えます。</span><span class="sxs-lookup"><span data-stu-id="3de6b-149">Use visual feedback to communicate the following states:</span></span>
* <span data-ttu-id="3de6b-150">**既定 (監視)**: オブジェクトの既定のアイドル状態。</span><span class="sxs-lookup"><span data-stu-id="3de6b-150">**Default (Observation)**: Default idle state of the object.</span></span>
* <span data-ttu-id="3de6b-151">**ホバー**: 手がホログラムの近くにある場合は、ビジュアルを変更して、その手がホログラムをターゲットとしていることを伝えます。</span><span class="sxs-lookup"><span data-stu-id="3de6b-151">**Hover**: When a hand is near a hologram, change visuals to communicate that hand is targeting hologram.</span></span> 
* <span data-ttu-id="3de6b-152">**距離とポイントの相互作用**: 手がホログラムに近づいたときに、投影された相互作用ポイントと、オブジェクトから指がどこまでの距離であるかを通知するデザインフィードバック</span><span class="sxs-lookup"><span data-stu-id="3de6b-152">**Distance and point of interaction**: As the hand approaches a hologram, design feedback to communicate the projected point of interaction, and how far from the object the finger is</span></span>
* <span data-ttu-id="3de6b-153">**連絡先の開始**: ビジュアル (明るい色) を変更して、タッチが発生したことを通知します</span><span class="sxs-lookup"><span data-stu-id="3de6b-153">**Contact begins**: Change visuals (light, color) to communicate that a touch has occurred</span></span>
* <span data-ttu-id="3de6b-154">**Grasped**: オブジェクトが Grasped の場合にビジュアル (明るい、色) を変更します。</span><span class="sxs-lookup"><span data-stu-id="3de6b-154">**Grasped**: Change visuals (light, color) when the object is grasped</span></span>
* <span data-ttu-id="3de6b-155">**連絡先の終了**: タッチが終了したときのビジュアル (明るい、色) を変更します</span><span class="sxs-lookup"><span data-stu-id="3de6b-155">**Contact ends**: Change visuals (light, color) when touch has ended</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="3de6b-156">![ホバー (遠く)](images/640px-interactibleobject-states-near-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-156">![Hover (Far)](images/640px-interactibleobject-states-near-hover.jpg)</span></span><br>
        <span data-ttu-id="3de6b-157">**ホバー (遠く)**</span><span class="sxs-lookup"><span data-stu-id="3de6b-157">**Hover (Far)**</span></span><br>
        <span data-ttu-id="3de6b-158">手書きの距離に基づいて強調表示します。</span><span class="sxs-lookup"><span data-stu-id="3de6b-158">Highlighting based on the proximity of the hand.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3de6b-159">![ホバー (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-159">![Hover (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)</span></span><br>
        <span data-ttu-id="3de6b-160">**ホバー (Near)**</span><span class="sxs-lookup"><span data-stu-id="3de6b-160">**Hover (Near)**</span></span><br>
        <span data-ttu-id="3de6b-161">ハンドの距離に応じてサイズの変化を強調表示します。</span><span class="sxs-lookup"><span data-stu-id="3de6b-161">Highlight size changes based on the distance to the hand.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="3de6b-162">![タッチ/押す](images/640px-interactibleobject-states-near-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-162">![Touch / press](images/640px-interactibleobject-states-near-press.jpg)</span></span><br>
        <span data-ttu-id="3de6b-163">**タッチ/押す**</span><span class="sxs-lookup"><span data-stu-id="3de6b-163">**Touch / press**</span></span><br>
        <span data-ttu-id="3de6b-164">ビジュアルとオーディオフィードバック。</span><span class="sxs-lookup"><span data-stu-id="3de6b-164">Visual plus audio feedback.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3de6b-165">![つかん](images/640px-interactibleobject-states-near-grasp.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-165">![Grasp](images/640px-interactibleobject-states-near-grasp.jpg)</span></span><br>
        <span data-ttu-id="3de6b-166">**つかん**</span><span class="sxs-lookup"><span data-stu-id="3de6b-166">**Grasp**</span></span><br>
        <span data-ttu-id="3de6b-167">ビジュアルとオーディオフィードバック。</span><span class="sxs-lookup"><span data-stu-id="3de6b-167">Visual plus audio feedback.</span></span>
    :::column-end:::
:::row-end:::

<br>

<br>

---

<span data-ttu-id="3de6b-168">[HoloLens 2 のボタン](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)は、さまざまな入力相互作用状態を視覚化する方法の例です。</span><span class="sxs-lookup"><span data-stu-id="3de6b-168">A [button on HoloLens 2](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html) is an example of how the different input interaction states are visualized:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3de6b-169">![既定値](images/640px-interactibleobject-pressablebutton-default.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-169">![Default](images/640px-interactibleobject-pressablebutton-default.jpg)</span></span><br>
        <span data-ttu-id="3de6b-170">**[Default]**</span><span class="sxs-lookup"><span data-stu-id="3de6b-170">**Default**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3de6b-171">![ホバー](images/640px-interactibleobject-pressablebutton-hover.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-171">![Hover](images/640px-interactibleobject-pressablebutton-hover.jpg)</span></span><br>
        <span data-ttu-id="3de6b-172">**ホバー**</span><span class="sxs-lookup"><span data-stu-id="3de6b-172">**Hover**</span></span><br>
        <span data-ttu-id="3de6b-173">距離に基づく光源効果を表示します。</span><span class="sxs-lookup"><span data-stu-id="3de6b-173">Reveal a proximity-based lighting effect.</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="3de6b-174">![タッチ](images/640px-interactibleobject-pressablebutton-touch.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-174">![Touch](images/640px-interactibleobject-pressablebutton-touch.jpg)</span></span><br>
        <span data-ttu-id="3de6b-175">**タッチ**</span><span class="sxs-lookup"><span data-stu-id="3de6b-175">**Touch**</span></span><br>
        <span data-ttu-id="3de6b-176">Ripple 効果を表示します。</span><span class="sxs-lookup"><span data-stu-id="3de6b-176">Show ripple effect.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="3de6b-177">![ショートカット キー](images/640px-interactibleobject-pressablebutton-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-177">![Press](images/640px-interactibleobject-pressablebutton-press.jpg)</span></span><br>
        <span data-ttu-id="3de6b-178">**ショートカット キー**</span><span class="sxs-lookup"><span data-stu-id="3de6b-178">**Press**</span></span><br>
        <span data-ttu-id="3de6b-179">前面プレートを移動します。</span><span class="sxs-lookup"><span data-stu-id="3de6b-179">Move the front plate.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a><span data-ttu-id="3de6b-180">HoloLens 2 の "リング" ビジュアルキュー</span><span class="sxs-lookup"><span data-stu-id="3de6b-180">The "ring" visual cue on HoloLens 2</span></span><br>
        <span data-ttu-id="3de6b-181">HoloLens 2 では、追加の視覚的な手掛かりがあります。これは、ユーザーが深さを認識するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3de6b-181">On HoloLens 2, there's an extra visual cue, which can help the user's perception of depth.</span></span> <span data-ttu-id="3de6b-182">指先がオブジェクトに近づいたときに、指先の近くにあるリングが表示され、スケールダウンされます。</span><span class="sxs-lookup"><span data-stu-id="3de6b-182">A ring near their fingertip shows up and scales down as the fingertip gets closer to the object.</span></span> <span data-ttu-id="3de6b-183">このリングは、押された状態に達したときに、最終的にドットに収束します。</span><span class="sxs-lookup"><span data-stu-id="3de6b-183">The ring eventually converges into a dot when the pressed state is reached.</span></span> <span data-ttu-id="3de6b-184">このビジュアル affordance は、オブジェクトからの距離をユーザーが理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3de6b-184">This visual affordance helps the user understand how far they are from the object.</span></span><br>
        <br>
        <span data-ttu-id="3de6b-185">*ビデオループ: 境界ボックスとの近接度に基づくビジュアルフィードバックの例*</span><span class="sxs-lookup"><span data-stu-id="3de6b-185">*Video loop: Example of visual feedback based on proximity to a bounding box*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="3de6b-186">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="3de6b-186">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="3de6b-187">![手書きの視覚的フィードバック](images/HoloLens2_Proximity.gif)</span><span class="sxs-lookup"><span data-stu-id="3de6b-187">![Visual feedback on hand proximity](images/HoloLens2_Proximity.gif)</span></span><br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a><span data-ttu-id="3de6b-188">オーディオキュー</span><span class="sxs-lookup"><span data-stu-id="3de6b-188">Audio cues</span></span>

<span data-ttu-id="3de6b-189">直接の対話では、適切なオーディオフィードバックによってユーザーエクスペリエンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="3de6b-189">For direct hand interactions, proper audio feedback can dramatically improve the user experience.</span></span> <span data-ttu-id="3de6b-190">オーディオフィードバックを使用して、次の手掛かりを伝えます。</span><span class="sxs-lookup"><span data-stu-id="3de6b-190">Use audio feedback to communicate the following cues:</span></span>
* <span data-ttu-id="3de6b-191">**連絡先の開始**: タッチの開始時にサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="3de6b-191">**Contact begins**: Play sound when touch begins</span></span>
* <span data-ttu-id="3de6b-192">**連絡先の終了**: タッチエンドでサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="3de6b-192">**Contact ends**: Play sound on touch end</span></span>
* <span data-ttu-id="3de6b-193">**グラブの開始**: グラブの開始時にサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="3de6b-193">**Grab begins**: Play sound when grab starts</span></span>
* <span data-ttu-id="3de6b-194">**グラブ端**: グラブ終了時にサウンドを再生する</span><span class="sxs-lookup"><span data-stu-id="3de6b-194">**Grab ends**: Play sound when grab ends</span></span>

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a><span data-ttu-id="3de6b-195">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="3de6b-195">Voice commanding</span></span><br>
        <span data-ttu-id="3de6b-196">対話型オブジェクトについては、代替の対話オプションをサポートすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="3de6b-196">For any interactable objects, it's important to support alternative interaction options.</span></span> <span data-ttu-id="3de6b-197">既定では、対話型されているすべてのオブジェクトに対して、 [音声コマンド](../out-of-scope/voice-design.md) をサポートすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3de6b-197">By default, we recommend that [voice commanding](../out-of-scope/voice-design.md) be supported for any objects that are interactable.</span></span> <span data-ttu-id="3de6b-198">見つけやすさを向上させるために、ホバー状態のときにツールヒントを提供することもできます。</span><span class="sxs-lookup"><span data-stu-id="3de6b-198">To improve discoverability, you can also provide a tooltip during the hover state.</span></span><br>
        <br>
        <span data-ttu-id="3de6b-199">*イメージ: 音声コマンドのツールヒント*</span><span class="sxs-lookup"><span data-stu-id="3de6b-199">*Image: Tooltip for the voice command*</span></span>
    :::column-end:::
        :::column:::
       ![音声によるコマンド](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a><span data-ttu-id="3de6b-201">サイズ設定に関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="3de6b-201">Sizing recommendations</span></span> 

<span data-ttu-id="3de6b-202">すべての対話型オブジェクトを簡単に操作できるようにするには、ユーザーからの距離に基づいて、対話型が最小サイズを満たしていることを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3de6b-202">To ensure all interactable objects can easily be touched, we recommend making sure the interactable meets a minimum size based on the distance it's placed from the user.</span></span> <span data-ttu-id="3de6b-203">視覚的な角度は、多くの場合、視覚円弧の度数で測定されます。視覚的な角度は、ユーザーの視点とオブジェクトの間の距離に基づいており、一定のままになります。一方、ターゲットの物理的なサイズは、ユーザーからの距離が変化すると変化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3de6b-203">The visual angle is often measured in degrees of visual arc. Visual angle is based on the distance between the user's eyes and the object and stays constant, while the physical size of the target may change as the distance from the user changes.</span></span> <span data-ttu-id="3de6b-204">ユーザーからの距離に基づいてオブジェクトの必要な物理サイズを判断するには、 [この](https://elvers.us/perception/visualAngle/)ような視覚的な角度計算ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="3de6b-204">To determine the necessary physical size of an object based on the distance from the user, try using a visual angle calculator such as [this one](https://elvers.us/perception/visualAngle/).</span></span>

<span data-ttu-id="3de6b-205">対話型コンテンツの最小サイズに関する推奨事項を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="3de6b-205">Below are the recommendations for minimum sizes of interactable content.</span></span>


### <a name="target-size-for-direct-hand-interaction"></a><span data-ttu-id="3de6b-206">ダイレクトハンド操作のターゲットサイズ</span><span class="sxs-lookup"><span data-stu-id="3de6b-206">Target size for direct hand interaction</span></span>

| <span data-ttu-id="3de6b-207">距離</span><span class="sxs-lookup"><span data-stu-id="3de6b-207">Distance</span></span> | <span data-ttu-id="3de6b-208">表示角度</span><span class="sxs-lookup"><span data-stu-id="3de6b-208">Viewing angle</span></span> | <span data-ttu-id="3de6b-209">サイズ</span><span class="sxs-lookup"><span data-stu-id="3de6b-209">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="3de6b-210">45 cm</span><span class="sxs-lookup"><span data-stu-id="3de6b-210">45 cm</span></span>  | <span data-ttu-id="3de6b-211">2°未満</span><span class="sxs-lookup"><span data-stu-id="3de6b-211">no smaller than 2°</span></span> | <span data-ttu-id="3de6b-212">1.6 x 1.6 cm</span><span class="sxs-lookup"><span data-stu-id="3de6b-212">1.6 x 1.6 cm</span></span> |

<span data-ttu-id="3de6b-213">![ダイレクトハンド操作のターゲットサイズ](images/TargetSizingNear.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-213">![Target size for direct hand interaction](images/TargetSizingNear.jpg)</span></span><br>
<span data-ttu-id="3de6b-214">*ダイレクトハンド操作のターゲットサイズ*</span><span class="sxs-lookup"><span data-stu-id="3de6b-214">*Target size for direct hand interaction*</span></span>

<br>

### <a name="target-size-for-buttons"></a><span data-ttu-id="3de6b-215">ボタンのターゲットサイズ</span><span class="sxs-lookup"><span data-stu-id="3de6b-215">Target size for buttons</span></span>

<span data-ttu-id="3de6b-216">直接対話するためのボタンを作成する場合は、3.2 x 3.2 cm の最小サイズを大きくすることをお勧めします。これにより、アイコンと一部のテキストを格納するための十分な領域が確保されます。</span><span class="sxs-lookup"><span data-stu-id="3de6b-216">When creating buttons for direct interaction, we recommend a larger minimum size of 3.2 x 3.2 cm to ensure that there's enough space to contain an icon and potentially some text.</span></span>

| <span data-ttu-id="3de6b-217">距離</span><span class="sxs-lookup"><span data-stu-id="3de6b-217">Distance</span></span> | <span data-ttu-id="3de6b-218">最小サイズ</span><span class="sxs-lookup"><span data-stu-id="3de6b-218">Minimum size</span></span> |
|---------|---------|
| <span data-ttu-id="3de6b-219">45 cm</span><span class="sxs-lookup"><span data-stu-id="3de6b-219">45 cm</span></span>  | <span data-ttu-id="3de6b-220">3.2 x 3.2 cm</span><span class="sxs-lookup"><span data-stu-id="3de6b-220">3.2 x 3.2 cm</span></span> |

<span data-ttu-id="3de6b-221">![ボタンのターゲットサイズ](images/TargetSizingButtons.png)</span><span class="sxs-lookup"><span data-stu-id="3de6b-221">![Target size for the buttons](images/TargetSizingButtons.png)</span></span><br>
<span data-ttu-id="3de6b-222">*ボタンのターゲットサイズ*</span><span class="sxs-lookup"><span data-stu-id="3de6b-222">*Target size for the buttons*</span></span>

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a><span data-ttu-id="3de6b-223">ハンドレイまたは宝石の相互作用の目標サイズ</span><span class="sxs-lookup"><span data-stu-id="3de6b-223">Target size for hand ray or gaze interaction</span></span>
| <span data-ttu-id="3de6b-224">距離</span><span class="sxs-lookup"><span data-stu-id="3de6b-224">Distance</span></span> | <span data-ttu-id="3de6b-225">表示角度</span><span class="sxs-lookup"><span data-stu-id="3de6b-225">Viewing angle</span></span> | <span data-ttu-id="3de6b-226">サイズ</span><span class="sxs-lookup"><span data-stu-id="3de6b-226">Size</span></span> |
|---------|---------|---------|
| <span data-ttu-id="3de6b-227">2 m</span><span class="sxs-lookup"><span data-stu-id="3de6b-227">2 m</span></span>  | <span data-ttu-id="3de6b-228">1°未満</span><span class="sxs-lookup"><span data-stu-id="3de6b-228">no smaller than 1°</span></span> | <span data-ttu-id="3de6b-229">3.5 x 3.5 cm</span><span class="sxs-lookup"><span data-stu-id="3de6b-229">3.5 x 3.5 cm</span></span> |

<span data-ttu-id="3de6b-230">![ハンドレイまたは宝石の相互作用の目標サイズ](images/TargetSizingFar.jpg)</span><span class="sxs-lookup"><span data-stu-id="3de6b-230">![Target size for hand ray or gaze interaction](images/TargetSizingFar.jpg)</span></span><br>
<span data-ttu-id="3de6b-231">*ハンドレイまたは宝石の相互作用の目標サイズ*</span><span class="sxs-lookup"><span data-stu-id="3de6b-231">*Target size for hand ray or gaze interaction*</span></span>


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="3de6b-232">Unity 用の MRTK (Mixed Reality Toolkit) の対話型オブジェクト</span><span class="sxs-lookup"><span data-stu-id="3de6b-232">Interactable object in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="3de6b-233">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** では、スクリプト [**対話型**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts)を使用して、オブジェクトがさまざまな種類の入力相互作用状態に応答するようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="3de6b-233">In **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can use the script [**Interactable**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts) to make objects respond to various types of input interaction states.</span></span> <span data-ttu-id="3de6b-234">色、サイズ、素材、シェーダーなどのオブジェクトプロパティを制御することで、視覚的な状態を定義できるさまざまなテーマをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3de6b-234">It supports various types of themes that allow you define visual states by controlling object properties such as color, size, material, and shader.</span></span>

* [<span data-ttu-id="3de6b-235">対話型</span><span class="sxs-lookup"><span data-stu-id="3de6b-235">Interactable</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/interactable.md)
* [<span data-ttu-id="3de6b-236">Button</span><span class="sxs-lookup"><span data-stu-id="3de6b-236">Button</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md)
* [<span data-ttu-id="3de6b-237">ハンド操作の例シーン</span><span class="sxs-lookup"><span data-stu-id="3de6b-237">Hand interaction examples scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

<span data-ttu-id="3de6b-238">MixedRealityToolkit の標準シェーダーには、ビジュアルおよびオーディオキューを作成するのに役立つ **近接光** などのさまざまなオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="3de6b-238">MixedRealityToolkit's Standard shader provides various options such as **proximity light** that helps you create visual and audio cues.</span></span>
* [<span data-ttu-id="3de6b-239">MRTK 標準シェーダー</span><span class="sxs-lookup"><span data-stu-id="3de6b-239">MRTK Standard Shader</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/rendering/mrtk-standard-shader.md)


<br>

---


## <a name="see-also"></a><span data-ttu-id="3de6b-240">関連項目</span><span class="sxs-lookup"><span data-stu-id="3de6b-240">See also</span></span>

* [<span data-ttu-id="3de6b-241">カーソル</span><span class="sxs-lookup"><span data-stu-id="3de6b-241">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="3de6b-242">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="3de6b-242">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="3de6b-243">ボタン</span><span class="sxs-lookup"><span data-stu-id="3de6b-243">Button</span></span>](button.md)
* [<span data-ttu-id="3de6b-244">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="3de6b-244">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="3de6b-245">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="3de6b-245">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="3de6b-246">操作</span><span class="sxs-lookup"><span data-stu-id="3de6b-246">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="3de6b-247">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="3de6b-247">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="3de6b-248">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="3de6b-248">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="3de6b-249">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="3de6b-249">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="3de6b-250">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="3de6b-250">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="3de6b-251">キーボード</span><span class="sxs-lookup"><span data-stu-id="3de6b-251">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="3de6b-252">ヒント</span><span class="sxs-lookup"><span data-stu-id="3de6b-252">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="3de6b-253">スレート</span><span class="sxs-lookup"><span data-stu-id="3de6b-253">Slate</span></span>](slate.md)
* [<span data-ttu-id="3de6b-254">スライダー</span><span class="sxs-lookup"><span data-stu-id="3de6b-254">Slider</span></span>](slider.md)
* [<span data-ttu-id="3de6b-255">シェーダー</span><span class="sxs-lookup"><span data-stu-id="3de6b-255">Shader</span></span>](shader.md)
* [<span data-ttu-id="3de6b-256">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="3de6b-256">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="3de6b-257">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="3de6b-257">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="3de6b-258">表面吸着</span><span class="sxs-lookup"><span data-stu-id="3de6b-258">Surface magnetism</span></span>](surface-magnetism.md)
