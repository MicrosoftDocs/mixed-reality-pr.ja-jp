---
title: 頭の視線入力とコミット
description: 頭の視線入力とコミットの入力モデルの概要
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality、宝石、宝石を絞ったターゲット、相互作用、設計、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、ターゲット、フォーカス、スムージング
ms.openlocfilehash: d913ac81e20962d38178223a050fdccfb51d8632
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702388"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="13a86-104">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="13a86-104">Head-gaze and commit</span></span>
<span data-ttu-id="13a86-105">_頭を見つめてコミット_ することは、 [宝石とコミット](gaze-and-commit.md) の入力モデルの特殊なケースです。頭の方向 (ヘッド方向) を使用してオブジェクトをターゲットにし、その後、エアタップや音声コマンドの "Select" など、2番目の入力で動作します。</span><span class="sxs-lookup"><span data-stu-id="13a86-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with the direction of your head pointing forward (head-direction), and then acting on it with a secondary input, such as the hand gesture air tap or the voice command "Select".</span></span> 

## <a name="device-support"></a><span data-ttu-id="13a86-106">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="13a86-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="13a86-107"><strong>入力モデル</strong></span><span class="sxs-lookup"><span data-stu-id="13a86-107"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="13a86-108"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="13a86-108"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="13a86-109"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="13a86-109"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="13a86-110"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="13a86-110"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="13a86-111">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="13a86-111">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="13a86-112">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="13a86-112">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="13a86-113">✔️ 推奨 (3 番目の選択肢 -<a href="interaction-fundamentals.md">他のオプションを参照</a>)</span><span class="sxs-lookup"><span data-stu-id="13a86-113">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="13a86-114">➕ 代替オプション</span><span class="sxs-lookup"><span data-stu-id="13a86-114">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="13a86-115">ターゲットのサイズ設定とフィードバック</span><span class="sxs-lookup"><span data-stu-id="13a86-115">Target sizing and feedback</span></span>
<span data-ttu-id="13a86-116">ヘッドの見つめベクターは、適切にターゲット設定できるように繰り返し表示されていますが、多くの場合、ターゲットの全体に最適です。</span><span class="sxs-lookup"><span data-stu-id="13a86-116">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring somewhat larger targets.</span></span> <span data-ttu-id="13a86-117">最小目標サイズが 1 ~ 1.5 °の場合、ほとんどのシナリオでユーザーの操作が成功します。ただし、3度のターゲットでは、多くの場合、速度が向上します。</span><span class="sxs-lookup"><span data-stu-id="13a86-117">Minimum target sizes of 1 to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="13a86-118">ユーザーがターゲットに設定するサイズは、3D 要素であっても実質的に 2D 領域であり、それが面しているどの投影もターゲット設定可能な領域になるはずです。</span><span class="sxs-lookup"><span data-stu-id="13a86-118">Note that the size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="13a86-119">要素が "アクティブ" である (ユーザーがターゲットとしている) ことを示すいくつかの重要な手掛かりが、非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="13a86-119">Providing some salient cue that an element is "active" (that the user is targeting it) is extremely helpful.</span></span> <span data-ttu-id="13a86-120">これには、表示されている "ホバー" 効果、オーディオのハイライトやクリック、要素を含むカーソルの配置のクリアなどの処置が含まれます。</span><span class="sxs-lookup"><span data-stu-id="13a86-120">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="13a86-121">![2 m の距離での最適なターゲット サイズ](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13a86-121">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="13a86-122">*2 m の距離での最適なターゲット サイズ*</span><span class="sxs-lookup"><span data-stu-id="13a86-122">*Optimal target size at 2 meter distance*</span></span>

<br>

<span data-ttu-id="13a86-123">![視線入力のターゲットとなるオブジェクトの強調表示の例](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13a86-123">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="13a86-124">*視線入力のターゲットとなるオブジェクトの強調表示の例*</span><span class="sxs-lookup"><span data-stu-id="13a86-124">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="13a86-125">ターゲットの配置</span><span class="sxs-lookup"><span data-stu-id="13a86-125">Target placement</span></span>
<span data-ttu-id="13a86-126">多くの場合、ユーザーは、ビューのフィールドに非常に高い、または低い位置にある UI 要素を見つけることができず、主なフォーカスの周りにある領域に注目することに重点が置かれています。</span><span class="sxs-lookup"><span data-stu-id="13a86-126">Users often fail to find UI elements that are positioned very high or very low in their field of view, focusing most of their attention on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="13a86-127">ほとんどのターゲットは目の高さあたりの適正な帯域に配置すると効果的です。</span><span class="sxs-lookup"><span data-stu-id="13a86-127">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="13a86-128">ユーザーは常に比較的小さい視覚野に焦点を合わせる傾向があることを考慮すると (注意の視円錐は約 10 度)、UI 要素を概念的に関連性のある度数にグループ化すれば、ユーザーが視線入力で領域内を移動する場合に、項目から項目への注意の連鎖動作を活用できます。</span><span class="sxs-lookup"><span data-stu-id="13a86-128">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree that they're related conceptually can leverage attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="13a86-129">UI を設計する際は、HoloLens とイマーシブ ヘッドセットでは視野内に潜在的な大きなバリエーションがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="13a86-129">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="13a86-130">![Galaxy Explorer で視線入力のターゲット設定を容易にするためにグループ化された UI 要素の例](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="13a86-130">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="13a86-131">*Galaxy Explorer で視線入力のターゲット設定を容易にするためにグループ化された UI 要素の例*</span><span class="sxs-lookup"><span data-stu-id="13a86-131">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="13a86-132">ターゲット設定動作の向上</span><span class="sxs-lookup"><span data-stu-id="13a86-132">Improving targeting behaviors</span></span>
<span data-ttu-id="13a86-133">ユーザーの意図を特定できる (または近似値を近似する) ことができた場合は、適切に対象としているかのように、操作の試行回数をよく受け入れることが非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="13a86-133">If user intent to target something can be determined (or approximated closely), it can be very helpful to accept near miss attempts at interaction as though they were targeted correctly.</span></span> <span data-ttu-id="13a86-134">Mixed reality エクスペリエンスに組み込むことができる成功したメソッドのいくつかを次に示します。</span><span class="sxs-lookup"><span data-stu-id="13a86-134">Here are a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="13a86-135">頭の視線入力の安定化 ("重力井戸")</span><span class="sxs-lookup"><span data-stu-id="13a86-135">Head-gaze stabilization ("gravity wells")</span></span>
<span data-ttu-id="13a86-136">これは、ほとんどまたはすべての時間に有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="13a86-136">This should be turned on most or all of the time.</span></span> <span data-ttu-id="13a86-137">この手法では、自然なヘッドとネックのジッターを排除します。これは、ユーザーが動作を検索したり話したりすることによって動きが多い場合があります。</span><span class="sxs-lookup"><span data-stu-id="13a86-137">This technique removes the natural head and neck jitters that users might have as well movement due to looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="13a86-138">最も近いリンク アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="13a86-138">Closest link algorithms</span></span>
<span data-ttu-id="13a86-139">これらは対話型コンテンツが少ない領域で最大の効果を発揮します。</span><span class="sxs-lookup"><span data-stu-id="13a86-139">These work best in areas with sparse interactive content.</span></span> <span data-ttu-id="13a86-140">ユーザーが何を操作しようとしているかを判断できる確率が高い場合は、ある程度のインテントを想定して、対象となる機能を補完することができます。</span><span class="sxs-lookup"><span data-stu-id="13a86-140">If there is a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="13a86-141">バックと後処理のアクション</span><span class="sxs-lookup"><span data-stu-id="13a86-141">Backdating and postdating actions</span></span>
<span data-ttu-id="13a86-142">このメカニズムは、速度が必要なタスクに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="13a86-142">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="13a86-143">ユーザーが一連のターゲットとアクティブ化の処理を高速に進めるときは、何らかのインテントを想定して、ユーザーが tap の前または少しの間にフォーカスを移動したターゲット (初期テストでは50ミリ秒前/後) に対して、不要な手順の実行を許可すると便利です。</span><span class="sxs-lookup"><span data-stu-id="13a86-143">When a user is moving through a series of targeting and activation maneuvers at speed, it is useful to assume some intent, and allow missed steps to act upon targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="13a86-144">スムージング</span><span class="sxs-lookup"><span data-stu-id="13a86-144">Smoothing</span></span>
<span data-ttu-id="13a86-145">このメカニズムは、自然なヘッド移動特性によってわずかなジッターと wobble を減らすことで、パスの移動に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="13a86-145">This mechanism is useful for pathing movements, reducing the slight jitter and wobble due to natural head movement characteristics.</span></span> <span data-ttu-id="13a86-146">パスモーションをスムーズにスムージングする場合は、時間の経過と共に、移動のサイズと距離を滑らかにします。</span><span class="sxs-lookup"><span data-stu-id="13a86-146">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="13a86-147">磁性</span><span class="sxs-lookup"><span data-stu-id="13a86-147">Magnetism</span></span>
<span data-ttu-id="13a86-148">このメカニズムは、最も近いリンクアルゴリズムのより一般的なバージョンであると考えることができます。これは、ターゲットに向かってカーソルを描画するか、またはユーザーの意図に応じて対話型レイアウトに関する知識を使用して、ユーザーがターゲットに近づくことになる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="13a86-148">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="13a86-149">これは、小さいターゲットの場合は特に効果を発揮する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13a86-149">This can be particularly powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="13a86-150">焦点の持続性</span><span class="sxs-lookup"><span data-stu-id="13a86-150">Focus stickiness</span></span>
<span data-ttu-id="13a86-151">フォーカスのある近接要素にフォーカスを移すときに、フォーカスの持続性により、現在フォーカスがある要素にバイアスが適用されます。</span><span class="sxs-lookup"><span data-stu-id="13a86-151">When determining which nearby interactive elements to give focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="13a86-152">これにより、自然なノイズを持つ2つの要素間の中間点で浮動フォーカスの切り替え動作を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="13a86-152">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>


## <a name="see-also"></a><span data-ttu-id="13a86-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="13a86-153">See also</span></span>
* [<span data-ttu-id="13a86-154">視線ベースの操作</span><span class="sxs-lookup"><span data-stu-id="13a86-154">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="13a86-155">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="13a86-155">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="13a86-156">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="13a86-156">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="13a86-157">手 - ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="13a86-157">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="13a86-158">手 - ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="13a86-158">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="13a86-159">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="13a86-159">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="13a86-160">音声入力</span><span class="sxs-lookup"><span data-stu-id="13a86-160">Voice input</span></span>](voice-input.md)



