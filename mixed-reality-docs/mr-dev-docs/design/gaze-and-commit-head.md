---
title: 頭の視線入力とコミット
description: ターゲットのサイズ設定、配置、安定化など、ヘッドとコミットの入力モデルの使用を開始します。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality、宝石、宝石を絞ったターゲット、相互作用、設計、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、ターゲット、フォーカス、スムージング
ms.openlocfilehash: a69b855e2246327affeeb0f771f565b94ea65cb2
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582280"
---
# <a name="head-gaze-and-commit"></a><span data-ttu-id="4ba74-104">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="4ba74-104">Head-gaze and commit</span></span>

<span data-ttu-id="4ba74-105">_頭を見つめてコミット_ することは、ユーザーの頭の方向を持つオブジェクトを対象とする、 [宝石とコミット](gaze-and-commit.md) の入力モデルの特殊なケースです。</span><span class="sxs-lookup"><span data-stu-id="4ba74-105">_Head-gaze and commit_ is a special case of the [gaze and commit](gaze-and-commit.md) input model that involves targeting an object with a users head direction.</span></span> <span data-ttu-id="4ba74-106">ハンドジェスチャのエアタップや "選択" 音声コマンドなど、2番目の入力でターゲットを操作できます。</span><span class="sxs-lookup"><span data-stu-id="4ba74-106">You can act on the target with a secondary input, such as the hand gesture air tap or "Select" voice command.</span></span> 

## <a name="device-support"></a><span data-ttu-id="4ba74-107">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="4ba74-107">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="4ba74-108"><strong>入力モデル</strong></span><span class="sxs-lookup"><span data-stu-id="4ba74-108"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="4ba74-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="4ba74-109"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="4ba74-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="4ba74-110"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="4ba74-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="4ba74-111"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="4ba74-112">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="4ba74-112">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="4ba74-113">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="4ba74-113">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="4ba74-114">✔️ 推奨 (3 番目の選択肢 -<a href="interaction-fundamentals.md">他のオプションを参照</a>)</span><span class="sxs-lookup"><span data-stu-id="4ba74-114">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="4ba74-115">➕ 代替オプション</span><span class="sxs-lookup"><span data-stu-id="4ba74-115">➕ Alternate option</span></span></td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a><span data-ttu-id="4ba74-116">ターゲットのサイズ設定とフィードバック</span><span class="sxs-lookup"><span data-stu-id="4ba74-116">Target sizing and feedback</span></span>

<span data-ttu-id="4ba74-117">ヘッドの見つめベクターは、適切にターゲットを設定するために繰り返し表示されていますが、多くの場合、より大きなターゲットを取得する場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="4ba74-117">The head gaze vector has been shown repeatedly to be usable for fine targeting, but often works best for gross targeting--acquiring larger targets.</span></span> <span data-ttu-id="4ba74-118">最小目標サイズが1°から1.5 °になると、ほとんどのシナリオでユーザーの操作が成功します。ただし、3度のターゲットでは、多くの場合、より高速に実行できます。</span><span class="sxs-lookup"><span data-stu-id="4ba74-118">Minimum target sizes of 1 degree to 1.5 degrees allow successful user actions in most scenarios, though targets of 3 degrees often allow for greater speed.</span></span> <span data-ttu-id="4ba74-119">ユーザーが対象としているサイズは、3d 要素の場合でも実質的には2d 領域です。つまり、どちらの投影が発生しているかは、不要領域である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ba74-119">The size that the user targets is effectively a 2D area even for 3D elements--whichever projection is facing them should be the targetable area.</span></span> <span data-ttu-id="4ba74-120">要素が "アクティブ" である (ユーザーがターゲットとしている) ことを示すいくつかの重要な手掛かりが役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="4ba74-120">Providing some salient cue that an element is "active" (that the user is targeting it) is helpful.</span></span> <span data-ttu-id="4ba74-121">これには、表示されている "ホバー" 効果、オーディオのハイライトやクリック、要素を含むカーソルの配置のクリアなどの処置が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4ba74-121">This can include treatments like visible "hover" effects, audio highlights or clicks, or clear alignment of a cursor with an element.</span></span>

<span data-ttu-id="4ba74-122">![2 m の距離での最適なターゲット サイズ](images/gazetargeting-size-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4ba74-122">![Optimal target size at 2 meter distance](images/gazetargeting-size-1000px.jpg)</span></span><br>
<span data-ttu-id="4ba74-123">*2メートル距離での最適な目標サイズ*</span><span class="sxs-lookup"><span data-stu-id="4ba74-123">*Optimal target size at 2-meter distance*</span></span>

<br>

<span data-ttu-id="4ba74-124">![視線入力のターゲットとなるオブジェクトの強調表示の例](images/gazetargeting-highlighting-940px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4ba74-124">![An example of highlighting a gaze targeted object](images/gazetargeting-highlighting-940px.jpg)</span></span><br>
<span data-ttu-id="4ba74-125">*視線入力のターゲットとなるオブジェクトの強調表示の例*</span><span class="sxs-lookup"><span data-stu-id="4ba74-125">*An example of highlighting a gaze targeted object*</span></span>

## <a name="target-placement"></a><span data-ttu-id="4ba74-126">ターゲットの配置</span><span class="sxs-lookup"><span data-stu-id="4ba74-126">Target placement</span></span>

<span data-ttu-id="4ba74-127">多くの場合、ユーザーは、表示されているフィールドの数が多すぎる、または低い UI 要素を見つけることができません。</span><span class="sxs-lookup"><span data-stu-id="4ba74-127">Users often fail to find UI elements located either too high or low in their field of view.</span></span> <span data-ttu-id="4ba74-128">注目すべき点のほとんどは、主に注目している分野です。</span><span class="sxs-lookup"><span data-stu-id="4ba74-128">Most of their attention ends up on areas around their main focus, which is approximately at eye level.</span></span> <span data-ttu-id="4ba74-129">ほとんどのターゲットは目の高さあたりの適正な帯域に配置すると効果的です。</span><span class="sxs-lookup"><span data-stu-id="4ba74-129">Placing most targets in some reasonable band around eye level can help.</span></span> <span data-ttu-id="4ba74-130">ユーザーがいつでも比較的小さい視覚領域に焦点を当てる傾向がある場合 (attentional コーンは約10度)、UI 要素を関連する程度にグループ化することで、ユーザーが1つの領域に移動したときに項目から項目へのアテンションチェーン動作を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4ba74-130">Given the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), grouping UI elements together to the degree they're related conceptually can use attention-chaining behaviors from item to item as a user moves their gaze through an area.</span></span> <span data-ttu-id="4ba74-131">UI を設計する際は、HoloLens とイマーシブ ヘッドセットでは視野内に潜在的な大きなバリエーションがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4ba74-131">When designing UI, keep in mind the potential large variation in field of view between HoloLens and immersive headsets.</span></span>

<span data-ttu-id="4ba74-132">![Galaxy Explorer で視線入力のターゲット設定を容易にするためにグループ化された UI 要素の例](images/gazetargeting-grouping-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="4ba74-132">![An example of grouped UI elements for easier gaze targeting in Galaxy Explorer](images/gazetargeting-grouping-1000px.jpg)</span></span><br>
<span data-ttu-id="4ba74-133">*Galaxy Explorer で視線入力のターゲット設定を容易にするためにグループ化された UI 要素の例*</span><span class="sxs-lookup"><span data-stu-id="4ba74-133">*An example of grouped UI elements for easier gaze targeting in Galaxy Explorer*</span></span>

## <a name="improving-targeting-behaviors"></a><span data-ttu-id="4ba74-134">ターゲット設定動作の向上</span><span class="sxs-lookup"><span data-stu-id="4ba74-134">Improving targeting behaviors</span></span>

<span data-ttu-id="4ba74-135">ユーザーの意図を特定したり、近似したりすることができる場合は、適切に対象としているかのように、ユーザーの介入試行を受け入れることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4ba74-135">If user intent to target something can be determined or closely approximated, it can be helpful to accept near miss interaction attempts as though they were targeted correctly.</span></span> <span data-ttu-id="4ba74-136">Mixed reality エクスペリエンスに組み込むことができる成功したメソッドのいくつかを次に示します。</span><span class="sxs-lookup"><span data-stu-id="4ba74-136">Here's a handful of successful methods that can be incorporated in mixed reality experiences:</span></span>

### <a name="head-gaze-stabilization-gravity-wells"></a><span data-ttu-id="4ba74-137">頭の視線入力の安定化 ("重力井戸")</span><span class="sxs-lookup"><span data-stu-id="4ba74-137">Head-gaze stabilization ("gravity wells")</span></span>

<span data-ttu-id="4ba74-138">これは、ほとんどまたはすべての時間に有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ba74-138">This should be turned on most or all of the time.</span></span> <span data-ttu-id="4ba74-139">この手法では、自然なヘッドとネックのジッターを排除します。これは、ユーザーが動作を検索したり話したりするため、動きが動いてくる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4ba74-139">This technique removes the natural head and neck jitters that users might have as well movement because of looking and speaking behaviors.</span></span>

### <a name="closest-link-algorithms"></a><span data-ttu-id="4ba74-140">最も近いリンク アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4ba74-140">Closest link algorithms</span></span>

<span data-ttu-id="4ba74-141">これらのアルゴリズムは、スパースな対話型コンテンツを持つ領域で最適に機能します。</span><span class="sxs-lookup"><span data-stu-id="4ba74-141">These algorithms work best in areas with sparse interactive content.</span></span> <span data-ttu-id="4ba74-142">ユーザーが何を操作しようとしているかを判断できる確率が高い場合は、ある程度のインテントを想定して、対象となる機能を補完することができます。</span><span class="sxs-lookup"><span data-stu-id="4ba74-142">If there's a high probability that you can determine what a user was attempting to interact with, you can supplement their targeting abilities by assuming some level of intent.</span></span>

### <a name="backdating-and-postdating-actions"></a><span data-ttu-id="4ba74-143">バックと後処理のアクション</span><span class="sxs-lookup"><span data-stu-id="4ba74-143">Backdating and postdating actions</span></span>

<span data-ttu-id="4ba74-144">このメカニズムは、速度が必要なタスクに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4ba74-144">This mechanism is useful in tasks requiring speed.</span></span> <span data-ttu-id="4ba74-145">ユーザーが一連のターゲットとアクティブ化の処理を高速に進めるときは、何らかの目的を想定すると便利です。</span><span class="sxs-lookup"><span data-stu-id="4ba74-145">When a user is moving through a series of targeting and activation maneuvers at speed, it's useful to assume some intent.</span></span> <span data-ttu-id="4ba74-146">また、タップの前または少し前に、ユーザーがフォーカスしていたターゲットに対して、不足しているステップの実行を許可することもできます (初期テストでは、50ミリ秒前後に有効です)。</span><span class="sxs-lookup"><span data-stu-id="4ba74-146">It's also useful to allow missed steps to act on targets that the user had in focus slightly before or slightly after the tap (50 ms before/after was effective in early testing).</span></span>

### <a name="smoothing"></a><span data-ttu-id="4ba74-147">スムージング</span><span class="sxs-lookup"><span data-stu-id="4ba74-147">Smoothing</span></span>

<span data-ttu-id="4ba74-148">このメカニズムは、自然な移動特性によってわずかなジッターと wobbles を減らすことで、パスの移動に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4ba74-148">This mechanism is useful for pathing movements, reducing the slight jitter and wobbles because of natural head movement characteristics.</span></span> <span data-ttu-id="4ba74-149">パスモーションをスムーズにスムージングする場合は、時間の経過と共に、移動のサイズと距離を滑らかにします。</span><span class="sxs-lookup"><span data-stu-id="4ba74-149">When smoothing over pathing motions, smooth by the size and distance of movements rather than over time.</span></span>

### <a name="magnetism"></a><span data-ttu-id="4ba74-150">磁性</span><span class="sxs-lookup"><span data-stu-id="4ba74-150">Magnetism</span></span>

<span data-ttu-id="4ba74-151">このメカニズムは、最も近いリンクアルゴリズムのより一般的なバージョンであると考えることができます。これは、ターゲットに向かってカーソルを描画するか、またはユーザーの意図に応じて対話型レイアウトに関する知識を使用して、ユーザーがターゲットに近づくことになる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="4ba74-151">This mechanism can be thought of as a more general version of closest link algorithms--drawing a cursor toward a target or simply increasing hitboxes, whether visibly or not, as users approach likely targets by using some knowledge of the interactive layout to better approach user intent.</span></span> <span data-ttu-id="4ba74-152">これは、小規模なターゲットでは強力です。</span><span class="sxs-lookup"><span data-stu-id="4ba74-152">This can be powerful for small targets.</span></span>

### <a name="focus-stickiness"></a><span data-ttu-id="4ba74-153">焦点の持続性</span><span class="sxs-lookup"><span data-stu-id="4ba74-153">Focus stickiness</span></span>

<span data-ttu-id="4ba74-154">対象となる近くの対話型要素を決定するときに、フォーカスの持続性によって、現在フォーカスがある要素にバイアスが与えられます。</span><span class="sxs-lookup"><span data-stu-id="4ba74-154">When determining which nearby interactive elements to give,  focus to, focus stickiness provides a bias to the element that is currently focused.</span></span> <span data-ttu-id="4ba74-155">これにより、自然なノイズを持つ2つの要素間の中間点で浮動フォーカスの切り替え動作を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="4ba74-155">This helps reduce erratic focus switching behaviors when floating at a midpoint between two elements with natural noise.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ba74-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ba74-156">See also</span></span>

* [<span data-ttu-id="4ba74-157">視線ベースの操作</span><span class="sxs-lookup"><span data-stu-id="4ba74-157">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="4ba74-158">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="4ba74-158">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="4ba74-159">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="4ba74-159">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4ba74-160">手 - ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="4ba74-160">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="4ba74-161">手 - ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="4ba74-161">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="4ba74-162">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="4ba74-162">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="4ba74-163">音声入力</span><span class="sxs-lookup"><span data-stu-id="4ba74-163">Voice input</span></span>](voice-input.md)