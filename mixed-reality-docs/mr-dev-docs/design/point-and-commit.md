---
title: 手を使ったポイントとコミット
description: Mixed Reality アプリケーションでジェスチャをサポートするためのポイントとコミット入力モデルの基本について説明します。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 対話, 設計, HoloLens, 手, 遠隔, ポイントとコミット, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, HoloLens, 手の光線, オブジェクト操作, MRTK, Mixed Reality Toolkit, DoF
ms.openlocfilehash: 3351a38cad99089a60555ffe450447fc5c356fdc
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583205"
---
# <a name="point-and-commit-with-hands"></a><span data-ttu-id="dd635-104">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="dd635-104">Point and commit with hands</span></span>

![カーソル](images/UX_Hero_HandRay.jpg)

<span data-ttu-id="dd635-106">手を使ったポイントとコミットは、ユーザーが手の届かない所にある 2D や 3D のコンテンツをターゲットに設定したり、選択したり、操作したりできる入力モデルです。</span><span class="sxs-lookup"><span data-stu-id="dd635-106">Point and commit with hands is an input model that lets users target, select, and manipulate out of reach 2D and 3D content.</span></span> <span data-ttu-id="dd635-107">この "遠隔" 対話技術は、人間が現実の世界と自然に対話するものではないため、Mixed Reality に固有です。</span><span class="sxs-lookup"><span data-stu-id="dd635-107">This "far" interaction technique is unique to mixed reality because humans don't naturally interact with the real world that way.</span></span> <span data-ttu-id="dd635-108">たとえば、スーパー ヒーロー映画 *X-Men* のキャラクター [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) は、遠くにある物体を自分の手で操作することができます。</span><span class="sxs-lookup"><span data-stu-id="dd635-108">For example, in the super hero movie, *X-Men*, the character [Magneto](https://en.wikipedia.org/wiki/Magneto_(comics)) can manipulate far objects in the distance with his hands.</span></span> <span data-ttu-id="dd635-109">こうしたことは現実世界では行えません。</span><span class="sxs-lookup"><span data-stu-id="dd635-109">This isn't something humans can do in reality.</span></span> <span data-ttu-id="dd635-110">HoloLens (AR) と Mixed Reality (MR) の両方で、この魔法の力をユーザーに付与して現実世界の物理的制約を打ち破ります。</span><span class="sxs-lookup"><span data-stu-id="dd635-110">In both HoloLens (AR) and Mixed Reality (MR), we equip users with this magical power to break the physical constraint of the real world.</span></span> <span data-ttu-id="dd635-111">ホログラフィック エクスペリエンスを楽しむだけでなく、ユーザーの対話をより効果的かつ効率的にします。</span><span class="sxs-lookup"><span data-stu-id="dd635-111">Not only is it a fun holographic experience, but it also makes user interactions more effective and efficient.</span></span>

## <a name="device-support"></a><span data-ttu-id="dd635-112">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="dd635-112">Device support</span></span>

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><span data-ttu-id="dd635-113"><strong>入力モデル</strong></span><span class="sxs-lookup"><span data-stu-id="dd635-113"><strong>Input model</strong></span></span></td>
     <td><span data-ttu-id="dd635-114"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="dd635-114"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
     <td><span data-ttu-id="dd635-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="dd635-115"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
     <td><span data-ttu-id="dd635-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="dd635-116"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
</tr>
<tr>
     <td><span data-ttu-id="dd635-117">手を使ったポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="dd635-117">Point and commit with hands</span></span></td>
     <td><span data-ttu-id="dd635-118">❌ サポート対象外</span><span class="sxs-lookup"><span data-stu-id="dd635-118">❌ Not supported</span></span></td>
     <td><span data-ttu-id="dd635-119">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="dd635-119">✔️ Recommended</span></span></td>
     <td><span data-ttu-id="dd635-120">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="dd635-120">✔️ Recommended</span></span></td>
</tr>
</table>


<span data-ttu-id="dd635-121">_"手を使ったポイントとコミット"_ は、新しい多関節ハンド トラッキング システムを使用した新機能の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="dd635-121">_"Point and commit with hands"_ is one of the new features that use the new articulated hand-tracking system.</span></span> <span data-ttu-id="dd635-122">この入力モデルは、モーション コントローラーを使用したイマーシブ ヘッドセットの主要な入力モデルでもあります。</span><span class="sxs-lookup"><span data-stu-id="dd635-122">This input model is also the primary input model on immersive headsets by using motion controllers.</span></span>

<br>

---

## <a name="hand-rays"></a><span data-ttu-id="dd635-123">手の光線</span><span class="sxs-lookup"><span data-stu-id="dd635-123">Hand rays</span></span>

<span data-ttu-id="dd635-124">HoloLens 2 では、ユーザーの手のひらの中心から放出される手の光線を考案しました。</span><span class="sxs-lookup"><span data-stu-id="dd635-124">On HoloLens 2, we created a hand ray that shoots out from the center of the user's palm.</span></span> <span data-ttu-id="dd635-125">この光線は、手の延長と見なされます。</span><span class="sxs-lookup"><span data-stu-id="dd635-125">This ray is treated as an extension of the hand.</span></span> <span data-ttu-id="dd635-126">光線がターゲット オブジェクトと交わる場所を示すために、光線の終端にドーナツ型のカーソルが取り付けられています。</span><span class="sxs-lookup"><span data-stu-id="dd635-126">A donut-shaped cursor is attached to the end of the ray to indicate the location where the ray intersects with a target object.</span></span> <span data-ttu-id="dd635-127">カーソルが届いているオブジェクトは、手から出されるジェスチャ コマンドを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="dd635-127">The object that the cursor lands on can then receive gestural commands from the hand.</span></span>

<span data-ttu-id="dd635-128">この基本的なジェスチャ コマンドは、親指と人差し指を使ってエアタップ アクションを実行することでトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="dd635-128">This basic gestural command is triggered by using the thumb and index finger to do the air-tap action.</span></span> <span data-ttu-id="dd635-129">手の光線を使用してポイントし、エアタップを使用してコミットすることで、ユーザーはボタンまたはハイパーリンクを有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="dd635-129">By using the hand ray to point and air tap to commit, users can activate a button or a hyperlink.</span></span> <span data-ttu-id="dd635-130">ユーザーは、より複合的なジェスチャを使うことで、Web コンテンツをナビゲートしたり、遠くから 3D オブジェクトを操作したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="dd635-130">With more composite gestures, users can navigating web content and manipulating 3D objects from a distance.</span></span> <span data-ttu-id="dd635-131">以下に説明および図示されているように、手の光線の視覚的なデザインも、これらのポイントとコミット状態に合わせて変化します。</span><span class="sxs-lookup"><span data-stu-id="dd635-131">The visual design of the hand ray should also react to these point and commit states, as described and shown below:</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="dd635-132">![ハンド レイ ポイント](images/hand-rays-pointing.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-132">![hand rays pointing](images/hand-rays-pointing.jpg)</span></span><br>
        <span data-ttu-id="dd635-133">**ポイント状態**</span><span class="sxs-lookup"><span data-stu-id="dd635-133">**Pointing state**</span></span><br>
        <span data-ttu-id="dd635-134">*ポイント* 状態の光線は破線で表され、カーソルはドーナツ型になります。</span><span class="sxs-lookup"><span data-stu-id="dd635-134">In the *pointing* state, the ray is a dash line and the cursor is a donut shape.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="dd635-135">![ハンド レイ コミット](images/hand-rays-commit.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-135">![hand rays commit](images/hand-rays-commit.jpg)</span></span><br>
        <span data-ttu-id="dd635-136">**コミット状態**</span><span class="sxs-lookup"><span data-stu-id="dd635-136">**Commit state**</span></span><br>
        <span data-ttu-id="dd635-137">*コミット* 状態になると光線は実線に変わり、カーソルは小さくなってドットになります。</span><span class="sxs-lookup"><span data-stu-id="dd635-137">In the *commit* state, the ray turns into a solid line and the cursor shrinks to a dot.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="transition-between-near-and-far"></a><span data-ttu-id="dd635-138">近くと遠くの切り替え</span><span class="sxs-lookup"><span data-stu-id="dd635-138">Transition between near and far</span></span>

<span data-ttu-id="dd635-139">「人差し指で指す」ことで光線を方向付けるなどの特定のジェスチャを使用する代わりに、ユーザーの手のひらの中心から光線が出るように設計しました。</span><span class="sxs-lookup"><span data-stu-id="dd635-139">Instead of using specific gestures like "pointing with index finger" to direct the ray, we designed the ray to comout out from the center of the users' palm.</span></span> <span data-ttu-id="dd635-140">これにより、5 本の指を解放して、より操作的なジェスチャ (ピンチやグラブなど) を行うために取っておくことができます。</span><span class="sxs-lookup"><span data-stu-id="dd635-140">This way, we've released and reserved the Five Fingers for more manipulative gestures like pinch and grab.</span></span> <span data-ttu-id="dd635-141">この設計では、メンタル モデルを 1 つだけ作りました。近くでも遠くでも、まったく同じ一連の手のジェスチャで操作できます。</span><span class="sxs-lookup"><span data-stu-id="dd635-141">With this design, we create only one mental model - the same set of hand gestures are used for both near and far interaction.</span></span> <span data-ttu-id="dd635-142">同じグラブ ジェスチャで、距離が異なるオブジェクトを操作できます。</span><span class="sxs-lookup"><span data-stu-id="dd635-142">You can use the same grab gesture to manipulate objects at different distances.</span></span> <span data-ttu-id="dd635-143">光線の呼び出しは、次のように近さに基づいて自動で行われます。</span><span class="sxs-lookup"><span data-stu-id="dd635-143">The invocation of the rays is automatic and proximity-based as follows:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="dd635-144">![近くの操作](images/transition-near-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-144">![Near manipulation](images/transition-near-manipulation.jpg)</span></span><br>
        <span data-ttu-id="dd635-145">**近くの操作**</span><span class="sxs-lookup"><span data-stu-id="dd635-145">**Near manipulation**</span></span><br>
        <span data-ttu-id="dd635-146">腕の長さ (約 50 cm) の範囲内にオブジェクトが入ると光線は自動的に消え、近接の対話が勧められます。</span><span class="sxs-lookup"><span data-stu-id="dd635-146">When an object is within arm's length (roughly 50 cm), the rays are turned off automatically, encouraging near interaction.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="dd635-147">![遠くの操作](images/transition-far-manipulation.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-147">![Far manipulation](images/transition-far-manipulation.jpg)</span></span><br>
        <span data-ttu-id="dd635-148">**遠くの操作**</span><span class="sxs-lookup"><span data-stu-id="dd635-148">**Far manipulation**</span></span><br>
        <span data-ttu-id="dd635-149">オブジェクトとの距離が 50 cm を超えると、光線が点灯します。</span><span class="sxs-lookup"><span data-stu-id="dd635-149">When the object is farther than 50 cm, the rays are turned on.</span></span> <span data-ttu-id="dd635-150">切り替えはスムーズかつシームレスに行われます。</span><span class="sxs-lookup"><span data-stu-id="dd635-150">The transition should be smooth and seamless.</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a><span data-ttu-id="dd635-151">2D スレートとの対話</span><span class="sxs-lookup"><span data-stu-id="dd635-151">2D slate interaction</span></span>

<span data-ttu-id="dd635-152">2D スレートは、Web ブラウザーなどの 2D アプリ コンテンツをホストするホログラフィック コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="dd635-152">A 2D slate is a holographic container hosting 2D app contents, such as a web browser.</span></span> <span data-ttu-id="dd635-153">2D スレートとの遠隔対話の設計概念は、手の光線を使ってターゲット設定し、エアタップで選択するというものです。</span><span class="sxs-lookup"><span data-stu-id="dd635-153">The design concept for far interacting with a 2D slate is to use hand rays to target and air tap to select.</span></span> <span data-ttu-id="dd635-154">手の光線でターゲット設定した後、ユーザーはエアタップしてハイパーリンクまたはボタンをトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="dd635-154">After targeting with a hand ray, users can air tap to trigger a hyperlink or a button.</span></span> <span data-ttu-id="dd635-155">片手で「エアタップ アンド ドラッグ」して、スレートのコンテンツを上下にスクロールすることができます。</span><span class="sxs-lookup"><span data-stu-id="dd635-155">They can use one hand to "air tap and drag" to scroll slate content up and down.</span></span> <span data-ttu-id="dd635-156">両手を使ってエアタップ アンド ドラッグするという相対的な動きにより、スレートのコンテンツを拡大縮小することができます。</span><span class="sxs-lookup"><span data-stu-id="dd635-156">The relative motion of using two hands to air tap and drag can zoom in and out the slate content.</span></span>

<span data-ttu-id="dd635-157">手の光線を隅や端にターゲット設定すると、最も近くにある操作アフォーダンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dd635-157">Targeting the hand ray at the corners and edges reveals the closest manipulation affordance.</span></span> <span data-ttu-id="dd635-158">ユーザーは操作アフォーダンスを「グラブ アンド ドラッグ」することで、隅のアフォーダンスによって均等に拡大縮小したり、端のアフォーダンスによってスレートをリフローしたりできます。</span><span class="sxs-lookup"><span data-stu-id="dd635-158">By "grab and drag" manipulation affordances, users can do uniform scaling through the corner affordances, and can reflow the slate via the edge affordances.</span></span> <span data-ttu-id="dd635-159">2D スレートの上部にあるホロバーをグラブ アンド ドラッグすることで、ユーザーはスレート全体を移動できます。</span><span class="sxs-lookup"><span data-stu-id="dd635-159">Grabbing and dragging the holobar at the top of the 2D slate lets users move the entire slate.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="dd635-160">![2D スレートの操作 (クリック)](images/2d-slate-interaction-click.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-160">![2d slate interaction click](images/2d-slate-interaction-click.jpg)</span></span><br>
       <span data-ttu-id="dd635-161">**クリック**</span><span class="sxs-lookup"><span data-stu-id="dd635-161">**Click**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="dd635-162">![2D スレートの操作 (スクロール)](images/2d-slate-interaction-scroll.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-162">![2d slate interaction scroll](images/2d-slate-interaction-scroll.jpg)</span></span><br>
        <span data-ttu-id="dd635-163">**スクロール**</span><span class="sxs-lookup"><span data-stu-id="dd635-163">**Scroll**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="dd635-164">![2D スレートの操作 (ズーム)](images/2d-slate-interaction-zoom.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-164">![2d slate interaction zoom](images/2d-slate-interaction-zoom.jpg)</span></span><br>
       <span data-ttu-id="dd635-165">**ズーム**</span><span class="sxs-lookup"><span data-stu-id="dd635-165">**Zoom**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

<span data-ttu-id="dd635-166">**2D スレートの操作方法**</span><span class="sxs-lookup"><span data-stu-id="dd635-166">**For manipulating the 2D slate**</span></span><br>

* <span data-ttu-id="dd635-167">ユーザーは、手の光線を隅または端にポイントして、最も近くにある操作アフォーダンスを表示します。</span><span class="sxs-lookup"><span data-stu-id="dd635-167">Users point the hand ray at the corners or edges to reveal the closest manipulation affordance.</span></span> 
* <span data-ttu-id="dd635-168">アフォーダンスに操作ジェスチャを適用すれば、ユーザーは隅のアフォーダンスによって均等に拡大縮小したり、端のアフォーダンスによってスレートをリフローしたりできます。</span><span class="sxs-lookup"><span data-stu-id="dd635-168">By applying a manipulation gesture on the affordance, users can do uniform scaling through the corner affordance, and can reflow the slate via the edge affordance.</span></span> 
* <span data-ttu-id="dd635-169">2D スレートの上部にあるホロバーに操作ジェスチャを適用することで、ユーザーはスレート全体を移動できます。</span><span class="sxs-lookup"><span data-stu-id="dd635-169">By applying a manipulation gesture on the holobar at the top of the 2D slate, users can move the entire slate.</span></span><br>

<br>

---

## <a name="3d-object-manipulation"></a><span data-ttu-id="dd635-170">3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="dd635-170">3D object manipulation</span></span>

<span data-ttu-id="dd635-171">直接操作では、ユーザーは、アフォーダンスをベースとする操作とアフォーダンスをベースとしない操作の 2 つの方法で 3D オブジェクトを操作できます。</span><span class="sxs-lookup"><span data-stu-id="dd635-171">In direct manipulation, there are two ways for users to manipulate 3D objects: affordance-based manipulation and non-affordance based manipulation.</span></span> <span data-ttu-id="dd635-172">ポイントとコミットのモデルでは、ユーザーはハンド レイを使ってまったく同じ作業を行えます。</span><span class="sxs-lookup"><span data-stu-id="dd635-172">In the point and commit model, users can achieve exactly the same tasks through the hand rays.</span></span> <span data-ttu-id="dd635-173">追加の学習は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="dd635-173">No extra learning is needed.</span></span><br>

### <a name="affordance-based-manipulation"></a><span data-ttu-id="dd635-174">アフォーダンスをベースとする操作</span><span class="sxs-lookup"><span data-stu-id="dd635-174">Affordance-based manipulation</span></span>

<span data-ttu-id="dd635-175">ユーザーは手の光線を使用して、境界ボックスと操作アフォーダンスをポイントし、表示します。</span><span class="sxs-lookup"><span data-stu-id="dd635-175">Users use hand rays to point and reveal the bounding box and manipulation affordances.</span></span> <span data-ttu-id="dd635-176">ユーザーは操作ジェスチャを境界ボックスに適用してオブジェクト全体を移動したり、端のアフォーダンスに適用して回転させたり、隅のアフォーダンスに適用して均等に拡大縮小したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="dd635-176">Users can apply the manipulation gesture on the bounding box to move the whole object, on the edge affordances to rotate, and on the corner affordances to scale uniformly.</span></span> <br>

:::row:::
    :::column:::
       <span data-ttu-id="dd635-177">![3D オブジェクト操作 (遠方移動)](images/3d-object-manipulation-far-move.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-177">![3d object manipulation far move](images/3d-object-manipulation-far-move.jpg)</span></span><br>
       <span data-ttu-id="dd635-178">**移動**</span><span class="sxs-lookup"><span data-stu-id="dd635-178">**Move**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="dd635-179">![3D オブジェクト操作 (遠方回転)](images/3d-object-manipulation-far-rotate.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-179">![3d object manipulation far rotate](images/3d-object-manipulation-far-rotate.jpg)</span></span><br>
        <span data-ttu-id="dd635-180">**回転**</span><span class="sxs-lookup"><span data-stu-id="dd635-180">**Rotate**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="dd635-181">![3D オブジェクト操作 (遠方スケール)](images/3d-object-manipulation-far-scale.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-181">![3d object manipulation far scale](images/3d-object-manipulation-far-scale.jpg)</span></span><br>
       <span data-ttu-id="dd635-182">**スケール**</span><span class="sxs-lookup"><span data-stu-id="dd635-182">**Scale**</span></span><br>
    :::column-end:::
:::row-end:::

### <a name="non-affordance-based-manipulation"></a><span data-ttu-id="dd635-183">アフォーダンスをベースとしない操作</span><span class="sxs-lookup"><span data-stu-id="dd635-183">Non-affordance-based manipulation</span></span>

<span data-ttu-id="dd635-184">ユーザーは手の光線を使ってポイントし、境界ボックスを表示した後、直接操作ジェスチャを適用します。</span><span class="sxs-lookup"><span data-stu-id="dd635-184">Users point with hand rays to reveal the bounding box then directly apply manipulation gestures on it.</span></span> <span data-ttu-id="dd635-185">片手を使用する場合、オブジェクトの移動と回転は手の動きと向きに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="dd635-185">With one hand, the translation and rotation of the object are associated to motion and orientation of the hand.</span></span> <span data-ttu-id="dd635-186">ユーザーが両手を使用すると、両手の相対的な動きに応じてそれを移動、拡大縮小、回転できます。</span><span class="sxs-lookup"><span data-stu-id="dd635-186">With two hands, users can translate, scale, and rotate it according to relative motions of two hands.</span></span><br>

<br>

---

## <a name="instinctual-gestures"></a><span data-ttu-id="dd635-187">本能的なジェスチャ</span><span class="sxs-lookup"><span data-stu-id="dd635-187">Instinctual gestures</span></span>

<span data-ttu-id="dd635-188">ポイントとコミットについての本能的なジェスチャの概念は、[手による直接操作](direct-manipulation.md)の概念と似ています。</span><span class="sxs-lookup"><span data-stu-id="dd635-188">The concept of instinctual gestures for point and commit is similar to that for [direct manipulation with hands](direct-manipulation.md).</span></span> <span data-ttu-id="dd635-189">ユーザーが 3D オブジェクトに対して実行するジェスチャは、UI アフォーダンスの設計によって導かれます。</span><span class="sxs-lookup"><span data-stu-id="dd635-189">The gestures users do on a 3D object are guided by the design of UI affordances.</span></span> <span data-ttu-id="dd635-190">たとえば、小さな制御点の場合にはユーザーは親指と人差し指でピンチするよう誘導されるのに対し、大きなオブジェクトをつかむためには 5 本の指すべてを使うかもしれません。</span><span class="sxs-lookup"><span data-stu-id="dd635-190">For example, a small control point might motivate users to pinch with their thumb and index finger, while a user might want to use all Five Fingers to grab a larger object.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="dd635-191">![本能的なジェスチャ (遠くの小さなオブジェクト)](images/instinctual-gestures-far-smallobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-191">![instinctual gestures far small object](images/instinctual-gestures-far-smallobject.jpg)</span></span><br>
       <span data-ttu-id="dd635-192">**小さなオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="dd635-192">**Small object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="dd635-193">![本能的なジェスチャ (遠くの中程度のオブジェクト)](images/instinctual-gestures-far-mediumobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-193">![instinctual gestures far medium object](images/instinctual-gestures-far-mediumobject.jpg)</span></span><br>
        <span data-ttu-id="dd635-194">**中程度のオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="dd635-194">**Medium object**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="dd635-195">![本能的なジェスチャ (遠くの大きなオブジェクト)](images/instinctual-gestures-far-largeobject.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-195">![instinctual gestures far large object](images/instinctual-gestures-far-largeobject.jpg)</span></span><br>
       <span data-ttu-id="dd635-196">**大きなオブジェクト**</span><span class="sxs-lookup"><span data-stu-id="dd635-196">**Large object**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a><span data-ttu-id="dd635-197">手と 6 DoF コントローラーの間の対称設計</span><span class="sxs-lookup"><span data-stu-id="dd635-197">Symmetric design between hands and 6 DoF controller</span></span> 

<span data-ttu-id="dd635-198">遠くにあるものと対話する場合のポイントとコミットの概念は、Mixed Reality ポータル (MRP) 向けに考案され、定義されました。</span><span class="sxs-lookup"><span data-stu-id="dd635-198">The concept of point and commit for far interaction was created and defined for the Mixed Reality Portal (MRP).</span></span> <span data-ttu-id="dd635-199">このシナリオでは、ユーザーはイマーシブ ヘッドセットを装着し、モーション コントローラーを介して 3D オブジェクトとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="dd635-199">In this scenario, a user wears an immersive headset and interacts with 3D objects via motion controllers.</span></span> <span data-ttu-id="dd635-200">モーション コントローラーは、遠くにあるオブジェクトをポイントして操作するために光線を放ちます。</span><span class="sxs-lookup"><span data-stu-id="dd635-200">The motion controllers shoot out rays for pointing and manipulating far objects.</span></span> <span data-ttu-id="dd635-201">コントローラーにはボタンがあって、さまざまな操作をさらにコミットします。</span><span class="sxs-lookup"><span data-stu-id="dd635-201">There are buttons on the controllers for further committing different actions.</span></span> <span data-ttu-id="dd635-202">光線の対話モデルを適用して、それを両手で利用することにしました。</span><span class="sxs-lookup"><span data-stu-id="dd635-202">We apply the interaction model of rays and attached them to both hands.</span></span> <span data-ttu-id="dd635-203">この対称設計により、MRP に精通しているユーザーは HoloLens 2 を使用するとき、遠くにあるものをポイントして操作するための別の対話モデルを学ぶ必要がなくなります (逆も同様です)。</span><span class="sxs-lookup"><span data-stu-id="dd635-203">With this symmetric design, users who are familiar with MRP won't need to learn another interaction model for far pointing and manipulation when they use HoloLens 2, and the other way around.</span></span>    

:::row:::
    :::column:::
        <span data-ttu-id="dd635-204">![コントローラーでの光線の対称設計](images/symmetric-design-for-rays-controllers.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-204">![symmetric design for rays with controllers](images/symmetric-design-for-rays-controllers.jpg)</span></span><br>
        <span data-ttu-id="dd635-205">**コントローラーの光線**</span><span class="sxs-lookup"><span data-stu-id="dd635-205">**Controller rays**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="dd635-206">![手での光線の対称設計](images/symmetric-design-for-rays-hands.jpg)</span><span class="sxs-lookup"><span data-stu-id="dd635-206">![symmetric design for rays with hands](images/symmetric-design-for-rays-hands.jpg)</span></span><br>
        <span data-ttu-id="dd635-207">**ハンド レイ**</span><span class="sxs-lookup"><span data-stu-id="dd635-207">**Hand rays**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="dd635-208">Unity 向け MRTK (Mixed Reality ツールキット) のハンド レイ</span><span class="sxs-lookup"><span data-stu-id="dd635-208">Hand ray in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="dd635-209">既定で、MRTK には、シェルのシステム ハンド レイと同じ表示状態のハンド レイ プレハブ ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) が備わっています。</span><span class="sxs-lookup"><span data-stu-id="dd635-209">By default, MRTK provides a hand ray prefab ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) which has the same visual state as the shell's system hand ray.</span></span> <span data-ttu-id="dd635-210">これは、[ポインター] にある MRTK の入力プロファイルに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="dd635-210">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="dd635-211">イマーシブ ヘッドセットでは、モーション コントローラーにも同じ光線が使用されています。</span><span class="sxs-lookup"><span data-stu-id="dd635-211">In an immersive headset, the same rays are used for the motion controllers.</span></span>

* [<span data-ttu-id="dd635-212">MRTK - ポインター プロファイル</span><span class="sxs-lookup"><span data-stu-id="dd635-212">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="dd635-213">MRTK - 入力システム</span><span class="sxs-lookup"><span data-stu-id="dd635-213">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="dd635-214">MRTK - ポインター</span><span class="sxs-lookup"><span data-stu-id="dd635-214">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)

---

## <a name="see-also"></a><span data-ttu-id="dd635-215">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd635-215">See also</span></span>
* [<span data-ttu-id="dd635-216">手で直接操作</span><span class="sxs-lookup"><span data-stu-id="dd635-216">Direct manipulation with hands</span></span>](direct-manipulation.md)
* [<span data-ttu-id="dd635-217">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="dd635-217">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="dd635-218">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="dd635-218">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="dd635-219">手 - ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="dd635-219">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="dd635-220">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="dd635-220">Instinctual interactions</span></span>](interaction-fundamentals.md)