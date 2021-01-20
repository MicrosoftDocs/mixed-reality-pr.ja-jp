---
title: カーソル
description: ターゲットベクターのカーソルまたはインジケーターは、ユーザーに対して継続的なフィードバックを提供し、HoloLens がその意図を理解しているかどうかを把握します。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: HoloLens (第1世代)、HoloLens 2、Mixed Reality、カーソル、ターゲット設定、宝石、ジェスチャ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、光線、入力
ms.openlocfilehash: 0525bb9b30dfe71fba7b8ebf2afd2c87a8c97a27
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582408"
---
# <a name="cursors"></a><span data-ttu-id="2a026-104">カーソル</span><span class="sxs-lookup"><span data-stu-id="2a026-104">Cursors</span></span>

![カーソル](images/UX_Hero_Cursor.jpg)

<span data-ttu-id="2a026-106">カーソルは、特定の時点でユーザーが現在フォーカスを認識しているヘッドセットの場所に基づいて、継続的なフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="2a026-106">A cursor provides continuous feedback based on where the headset believes a users current focus is at a given time.</span></span> <span data-ttu-id="2a026-107">カーソルのフィードバックには、仮想環境内のどの領域、ホログラム、またはポイントが入力に応答するかが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2a026-107">Cursor feedback includes what area, hologram, or point in the virtual environment responds to input.</span></span> <span data-ttu-id="2a026-108">カーソルは、デバイスがユーザーの注意を認識している場所をデジタルで表現したものですが、ユーザーの意図を決定することと同じではありません。</span><span class="sxs-lookup"><span data-stu-id="2a026-108">Even though the cursor is a digital representation of where the device understands the user's attention to be, that's not the same as determining the user's intentions.</span></span> <span data-ttu-id="2a026-109">カーソルのフィードバックにより、ユーザーはどのシステムの応答を期待するかを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="2a026-109">The cursor feedback also lets users know what system responses to expect.</span></span> <span data-ttu-id="2a026-110">フィードバックを使用すると、デバイスに対する意思決定を行うことができ、ユーザーの自信が高まります。</span><span class="sxs-lookup"><span data-stu-id="2a026-110">You can use the feedback to communicate their intention to the device, which increases user confidence.</span></span>

<span data-ttu-id="2a026-111">カーソルには、 **指、射線**、および **頭を見つめ** た3種類があります。</span><span class="sxs-lookup"><span data-stu-id="2a026-111">There are 3 kinds of cursors: **finger, ray**, and **head-gaze**.</span></span> <span data-ttu-id="2a026-112">これらのポイントカーソルは、HoloLens、HoloLens 2、およびイマーシブヘッドセットのさまざまな入力感覚様相で動作します。</span><span class="sxs-lookup"><span data-stu-id="2a026-112">These pointing cursors work with different input modalities on HoloLens, HoloLens 2, and immersive headsets.</span></span> <span data-ttu-id="2a026-113">次に、各種類のヘッドセットと相互作用モデルに使用するカーソルの種類に関するガイダンスを示します。</span><span class="sxs-lookup"><span data-stu-id="2a026-113">Below is guidance on which type of cursor to use for each type of headset and interaction model.</span></span> <span data-ttu-id="2a026-114">Mixed Reality Toolkit (MRTK) では、右のポイントエクスペリエンスを構築するのに役立つドラッグアンドドロップカーソルモジュールを作成しました。</span><span class="sxs-lookup"><span data-stu-id="2a026-114">In the Mixed Reality Toolkit (MRTK), we've created drag-and-drop cursors modules to help you build the right pointing experience.</span></span>

## <a name="device-support"></a><span data-ttu-id="2a026-115">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="2a026-115">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2a026-116"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="2a026-116"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="2a026-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="2a026-117"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="2a026-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="2a026-118"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="2a026-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2a026-119"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2a026-120">指カーソル</span><span class="sxs-lookup"><span data-stu-id="2a026-120">Finger cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="2a026-121">✔️</span><span class="sxs-lookup"><span data-stu-id="2a026-121">✔️</span></span></td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="2a026-122">射線カーソル</span><span class="sxs-lookup"><span data-stu-id="2a026-122">Ray cursor</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="2a026-123">✔️</span><span class="sxs-lookup"><span data-stu-id="2a026-123">✔️</span></span></td>
        <td><span data-ttu-id="2a026-124">✔️</span><span class="sxs-lookup"><span data-stu-id="2a026-124">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2a026-125">頭を見つめたカーソル</span><span class="sxs-lookup"><span data-stu-id="2a026-125">Head-gaze cursor</span></span></td>
        <td><span data-ttu-id="2a026-126">✔️</span><span class="sxs-lookup"><span data-stu-id="2a026-126">✔️</span></span></td>
        <td><span data-ttu-id="2a026-127">✔️</span><span class="sxs-lookup"><span data-stu-id="2a026-127">✔️</span></span></td>
        <td><span data-ttu-id="2a026-128">✔️</span><span class="sxs-lookup"><span data-stu-id="2a026-128">✔️</span></span></td>
    </tr>
</table>

## <a name="finger-cursor"></a><span data-ttu-id="2a026-129">指カーソル</span><span class="sxs-lookup"><span data-stu-id="2a026-129">Finger cursor</span></span>

<span data-ttu-id="2a026-130">この指カーソルは HoloLens 2 でのみ使用できます。 "対話モード[での直接操作](direct-manipulation.md)" を強化します。</span><span class="sxs-lookup"><span data-stu-id="2a026-130">The finger cursor is only available on the HoloLens 2 to enhance the "[direct manipulation with hands](direct-manipulation.md)" interaction mode.</span></span> <span data-ttu-id="2a026-131">指が指している箇所をより深く理解するために、両方のインデックス指のヒントにリングをアタッチしました。</span><span class="sxs-lookup"><span data-stu-id="2a026-131">We've attached rings to the tips of both index fingers to better understand where the finger is pointing.</span></span> <span data-ttu-id="2a026-132">リングサイズは、UI 画面への指の近接部分に基づいています。これは、指が UI に触れると小さいドットに縮小されます。</span><span class="sxs-lookup"><span data-stu-id="2a026-132">The ring size is based on the proximity of the finger to the UI surface, which shrinks to a small dot when the finger touches the UI.</span></span> <span data-ttu-id="2a026-133">指を近づけると、リングが小さくなります。</span><span class="sxs-lookup"><span data-stu-id="2a026-133">The closer the finger, the smaller the ring.</span></span> <br>

<span data-ttu-id="2a026-134">![指カーソル](images/finger-cursor.png)</span><span class="sxs-lookup"><span data-stu-id="2a026-134">![finger cursor](images/finger-cursor.png)</span></span><br>
<span data-ttu-id="2a026-135">"**指カーソル 1" の視覚的なフィードバックの状態**: リングがドットに縮小されます。</span><span class="sxs-lookup"><span data-stu-id="2a026-135">**Visual feedback states of finger cursor** 1: The ring shrinks to a dot.</span></span> <span data-ttu-id="2a026-136">2: リングは画面と一致します。</span><span class="sxs-lookup"><span data-stu-id="2a026-136">2: The ring aligns with surface.</span></span> <span data-ttu-id="2a026-137">3: リングは、指ベクターに対して垂直になります。</span><span class="sxs-lookup"><span data-stu-id="2a026-137">3: The ring is perpendicular to finger vector.</span></span> <span data-ttu-id="2a026-138">4: リングがありません。</span><span class="sxs-lookup"><span data-stu-id="2a026-138">4: No ring.</span></span>

## <a name="ray-cursor"></a><span data-ttu-id="2a026-139">射線カーソル</span><span class="sxs-lookup"><span data-stu-id="2a026-139">Ray cursor</span></span>

<span data-ttu-id="2a026-140">射線のカーソルは、遠くにある光線の端に接続して、手に届かないオブジェクトを操作できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2a026-140">Ray cursors attach to the end of far pointing rays to allow manipulation of objects that are out of hands-reach.</span></span> <span data-ttu-id="2a026-141">イマーシブヘッドセットでは、光線がモーションコントローラーから撮影され、ドットカーソルで終了します。</span><span class="sxs-lookup"><span data-stu-id="2a026-141">In immersive headsets, the rays shoot out from motion controllers and end in dot cursors.</span></span> <span data-ttu-id="2a026-142">HoloLens 2 では、これらの運動コントローラーの光線と、直接操作で使用される指カーソルと一貫性のあるリング形のカーソルでてのひらから出てくる直線状のデザインを適用します。</span><span class="sxs-lookup"><span data-stu-id="2a026-142">In HoloLens 2, we apply the mental model of these motion controller rays and designed hand rays that originate from the palms and end in ring-shaped cursors that are consistent with finger cursors used in direct manipulation.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="2a026-143">![レイカーソルコントローラー](images/ray-cursor-controller.png)</span><span class="sxs-lookup"><span data-stu-id="2a026-143">![Ray cursor controller](images/ray-cursor-controller.png)</span></span><br>
        <span data-ttu-id="2a026-144">**モーションコントローラーの射線カーソル**</span><span class="sxs-lookup"><span data-stu-id="2a026-144">**Ray cursors of motion controllers**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2a026-145">![レイカーソルハンド](images/ray-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="2a026-145">![Ray cursor hand](images/ray-cursor-hand.png)</span></span><br>
        <span data-ttu-id="2a026-146">**ハンドカーソル**</span><span class="sxs-lookup"><span data-stu-id="2a026-146">**Ray cursors of hands**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="head-gaze-cursor"></a><span data-ttu-id="2a026-147">頭を見つめたカーソル</span><span class="sxs-lookup"><span data-stu-id="2a026-147">Head-gaze cursor</span></span>

<span data-ttu-id="2a026-148">ヘッドを見つめたカーソルは、先端の位置と回転を使用する、非表示のヘッドを見つめたベクターの終点に接続するドットです。</span><span class="sxs-lookup"><span data-stu-id="2a026-148">The head-gaze cursor is a dot that attaches to the end of an invisible head-gaze vector that uses the position and rotation of the head to point.</span></span> <span data-ttu-id="2a026-149">アクションを実行するために、このポインティングカーソルは、エアタップ、音声コマンド、熟考、ボタンの押下などのさまざまなコミット入力とペアになっています。</span><span class="sxs-lookup"><span data-stu-id="2a026-149">To execute actions, this pointing cursor is paired with various commit inputs such as air tap, voice commands, dwell, and button press.</span></span> <span data-ttu-id="2a026-150">HoloLens 2 では、ヘッドを使用することをお勧めします。これは、エアタップではないすべてのコミット入力とペアになります。</span><span class="sxs-lookup"><span data-stu-id="2a026-150">In HoloLens 2, head-gaze is best paired with any commit input that isn't air tap, as there will be interaction conflict between air tap and far hand rays.</span></span> <br>
:::row:::
    :::column:::
        <span data-ttu-id="2a026-151">![頭を見つめたカーソルハンド](images/head-gaze-cursor-hand.png)</span><span class="sxs-lookup"><span data-stu-id="2a026-151">![Head gaze cursor hand](images/head-gaze-cursor-hand.png)</span></span><br>
        <span data-ttu-id="2a026-152">**ハンドジェスチャを使用した頭を見つめたカーソル**</span><span class="sxs-lookup"><span data-stu-id="2a026-152">**Head-gaze cursor with hand gesture**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="2a026-153">![頭を見つめたカーソルの声](images/head-gaze-cursor-voice.png)</span><span class="sxs-lookup"><span data-stu-id="2a026-153">![Head gaze cursor voice](images/head-gaze-cursor-voice.png)</span></span><br>
        <span data-ttu-id="2a026-154">**音声コマンドを使用した頭を見つめたカーソル**</span><span class="sxs-lookup"><span data-stu-id="2a026-154">**Head-gaze cursor with voice command**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="cursor-customization-recommendations"></a><span data-ttu-id="2a026-155">カーソルのカスタマイズに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="2a026-155">Cursor customization recommendations</span></span>

<span data-ttu-id="2a026-156">カーソルフィードバックの動作と外観をカスタマイズする場合は、次のような設計上の推奨事項があります。</span><span class="sxs-lookup"><span data-stu-id="2a026-156">If you would like to customize the cursor feedback behaviors and appearances, here are some design recommendations:</span></span>

### <a name="cursor-scale"></a><span data-ttu-id="2a026-157">カーソルのスケール</span><span class="sxs-lookup"><span data-stu-id="2a026-157">Cursor scale</span></span>

* <span data-ttu-id="2a026-158">カーソルは、使用可能なターゲットを超えないようにする必要があります。これにより、ユーザーは簡単に操作してコンテンツを表示できます。</span><span class="sxs-lookup"><span data-stu-id="2a026-158">The cursor should be no larger than the available targets, allowing users to easily interact with and view the content.</span></span>
* <span data-ttu-id="2a026-159">作成したエクスペリエンスに応じて、ユーザーが見ているようにカーソルを拡大縮小することも重要な考慮事項です。</span><span class="sxs-lookup"><span data-stu-id="2a026-159">Depending on the experience you create, scaling the cursor as the user looks around is also an important consideration.</span></span> <span data-ttu-id="2a026-160">たとえば、ユーザーがさらに経験を見ていくと、カーソルが失われてしまうように小さくなることはありません。</span><span class="sxs-lookup"><span data-stu-id="2a026-160">For example, as the user looks further away in your experience, the cursor shouldn't become too small such that it's lost.</span></span>
* <span data-ttu-id="2a026-161">カーソルをスケーリングするときは、サイズを変更して自然な感覚を与えることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="2a026-161">When scaling the cursor, consider applying a soft animation to it as it scales to give it an organic feeling.</span></span>
* <span data-ttu-id="2a026-162">Obstructing コンテンツは避けてください。</span><span class="sxs-lookup"><span data-stu-id="2a026-162">Avoid obstructing content.</span></span> <span data-ttu-id="2a026-163">ホログラムを使用すると、エクスペリエンスが覚えやすくなり、カーソルを離れることはできません。</span><span class="sxs-lookup"><span data-stu-id="2a026-163">Holograms are what make the experience memorable and the cursor shouldn't be taking away from them.</span></span>

### <a name="directionless-cursor-shape"></a><span data-ttu-id="2a026-164">Directionless カーソルのシェイプ</span><span class="sxs-lookup"><span data-stu-id="2a026-164">Directionless cursor shape</span></span>

* <span data-ttu-id="2a026-165">1つの右カーソル図形はありませんが、トーラスのような directionless 図形を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2a026-165">Although there's no one right cursor shape, we recommend that you use a directionless shape like a torus.</span></span> <span data-ttu-id="2a026-166">ある方向を指すカーソル (たとえば、従来の矢印カーソル) は、ユーザーが常にそのように見えるように混乱する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2a026-166">A cursor that points in some direction (For example, a traditional arrow cursor) might confuse the user to always look that way.</span></span>
* <span data-ttu-id="2a026-167">この例外は、カーソルを使用して対話命令をユーザーに伝える場合です。</span><span class="sxs-lookup"><span data-stu-id="2a026-167">An exception to this is when using the cursor to communicate interaction instruction to the user.</span></span> <span data-ttu-id="2a026-168">たとえば、混合の現実 OS でホログラムをスケーリングする場合、カーソルには一時的に矢印が表示されます。矢印を使用すると、ハンドを移動してホログラムをスケーリングする方法をユーザーに指示することができます。</span><span class="sxs-lookup"><span data-stu-id="2a026-168">For example, when scaling holograms in the Mixed Reality OS, the cursor temporarily includes arrows that instructs the user on how to move their hand to scale the hologram.</span></span>

### <a name="look-and-feel"></a><span data-ttu-id="2a026-169">ルックアンドフィール</span><span class="sxs-lookup"><span data-stu-id="2a026-169">Look and feel</span></span>

* <span data-ttu-id="2a026-170">ドーナツまたはトーラスのカーソルは、多くのアプリケーションで機能します。</span><span class="sxs-lookup"><span data-stu-id="2a026-170">A donut or torus shaped cursor works for many applications.</span></span>
* <span data-ttu-id="2a026-171">作成中のエクスペリエンスを最もよく表す色と形状を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a026-171">Pick a color and shape that best represents the experience you're creating.</span></span>
* <span data-ttu-id="2a026-172">カーソルは、特に [色の分離](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)が非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2a026-172">Cursors are especially prone to [color separation](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation).</span></span>
* <span data-ttu-id="2a026-173">均衡がとれた小さいカーソルは、視覚的な階層を占めことなく、有益な情報を保持します。</span><span class="sxs-lookup"><span data-stu-id="2a026-173">A small cursor with balanced opacity keeps it informative without dominating the visual hierarchy.</span></span>
* <span data-ttu-id="2a026-174">Cognizant を使用すると、コンテンツが妨げされたり、作業が邪魔されたりする可能性があるため、カーソルの背後に影を付けたりハイライトしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="2a026-174">Be cognizant of using shadows or highlights behind your cursor as they might obstruct content and distract from the task at hand.</span></span>
* <span data-ttu-id="2a026-175">カーソルは、アプリ内のサーフェイスに合わせて hug する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a026-175">Cursors should align to and hug the surfaces in your app.</span></span> <span data-ttu-id="2a026-176">ユーザーは、システムが探している場所を確認できますが、システムがその環境を認識していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="2a026-176">Users will have a feeling that the system can see where they're looking, but also that the system is aware of their surroundings.</span></span> <span data-ttu-id="2a026-177">たとえば、Mixed Reality OS のカーソルはユーザーの世界の表面に配置され、ユーザーがホログラムを直接見ていない場合でも、世界を認識しています。</span><span class="sxs-lookup"><span data-stu-id="2a026-177">For example, the cursor in the Mixed Reality OS aligns to the surfaces of the user's world, creating a feeling of awareness of the world even when the user isn't looking directly at a hologram.</span></span>
* <span data-ttu-id="2a026-178">ユーザーの近くでカーソルを対話型要素にロックすると、ユーザーが選択アクションを使用するときにその要素と対話する自信を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="2a026-178">Magnetically locking the cursor to an interactive element when it's close to the user can help improve confidence that user will interact with that element when they use a selection action.</span></span>

### <a name="visual-cues"></a><span data-ttu-id="2a026-179">視覚的な合図</span><span class="sxs-lookup"><span data-stu-id="2a026-179">Visual cues</span></span>

* <span data-ttu-id="2a026-180">1つのホログラムに焦点を絞った経験がある場合、そのホログラムから離れると、カーソルはそのホログラムと change 図形だけを hug して、変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a026-180">If your experience is focused on a single hologram, your cursor should align and hug only that hologram and change shape when you look away from that hologram.</span></span> <span data-ttu-id="2a026-181">これは、ホログラムが実用的であり、それと対話できることをユーザーに伝えることができます。</span><span class="sxs-lookup"><span data-stu-id="2a026-181">This can convey to the user that the hologram is actionable and they can interact with it.</span></span>
* <span data-ttu-id="2a026-182">アプリケーションで空間マッピングが使用されている場合は、カーソルが表示されるすべての画面を配置し、hug することができます。</span><span class="sxs-lookup"><span data-stu-id="2a026-182">If your application uses spatial mapping, then your cursor could align and hug every surface it sees.</span></span> <span data-ttu-id="2a026-183">これにより、HoloLens を使用するユーザーに対してフィードバックが提供され、アプリケーションはその領域を見ることができます。</span><span class="sxs-lookup"><span data-stu-id="2a026-183">This gives feedback to the users that HoloLens and your application can see their space.</span></span> <span data-ttu-id="2a026-184">これにより、ホログラムは実際のものであり、現実と仮想の間のギャップを埋めることができます。</span><span class="sxs-lookup"><span data-stu-id="2a026-184">This reinforces the fact that holograms are real and in our world and helps bridge the gap between real and virtual.</span></span>
* <span data-ttu-id="2a026-185">ビューにホログラムや surface が存在しない場合のカーソルの動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a026-185">Have an idea of what the cursor should do when there are no holograms or surfaces in view.</span></span> <span data-ttu-id="2a026-186">ユーザーの前にあらかじめ定義されている距離で配置することは、1つの選択肢です。</span><span class="sxs-lookup"><span data-stu-id="2a026-186">Placing it at a predetermined distance in front of the user is one option.</span></span>

### <a name="possible-actions"></a><span data-ttu-id="2a026-187">実行可能なアクション</span><span class="sxs-lookup"><span data-stu-id="2a026-187">Possible actions</span></span>

* <span data-ttu-id="2a026-188">カーソルはさまざまなアイコンで表すことができ、これによって、ホログラムが行うことのできるアクション (スケーリングや回転など) を伝えることができます。</span><span class="sxs-lookup"><span data-stu-id="2a026-188">The cursor can be represented by different icons to convey possible actions a hologram can do, such as scaling or rotation.</span></span>
* <span data-ttu-id="2a026-189">カーソルがユーザーに対して何かを意味する場合にのみ、追加情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="2a026-189">Only add extra information on the cursor if it means something to the user.</span></span> <span data-ttu-id="2a026-190">そうしないと、ユーザーは状態の変化を気付かないか、カーソルによって混乱を受ける可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2a026-190">Otherwise, users might either not notice the state changes or get confused by the cursor.</span></span>

### <a name="input-state"></a><span data-ttu-id="2a026-191">入力状態</span><span class="sxs-lookup"><span data-stu-id="2a026-191">Input state</span></span>

* <span data-ttu-id="2a026-192">カーソルを使用して、ユーザーの入力状態または目的を表示できます。</span><span class="sxs-lookup"><span data-stu-id="2a026-192">We could use the cursor to display the user's input state or intent.</span></span> <span data-ttu-id="2a026-193">たとえば、システムに手の状態が表示され、アプリケーションがアクションを実行する準備ができていることを知らせるアイコンを表示できます。</span><span class="sxs-lookup"><span data-stu-id="2a026-193">For example, we could display an icon telling the user the system sees their hand state and that the application knows they're ready to take action.</span></span>
* <span data-ttu-id="2a026-194">また、カーソルを使用して、システムによって一時的な色の変更によって音声コマンドが知られていることをユーザーに示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="2a026-194">We could also use the cursor to show users that voice commands have been heard by the system via a momentary color change</span></span>

* <span data-ttu-id="2a026-195">次のカーソルの状態は、さまざまな方法で実装できます。</span><span class="sxs-lookup"><span data-stu-id="2a026-195">The following cursor states can be implemented in different ways.</span></span> <span data-ttu-id="2a026-196">ステートマシンのようにカーソルをモデル化することによって、これらの異なる状態を実装する場合があります。</span><span class="sxs-lookup"><span data-stu-id="2a026-196">You might implement these different states by modeling the cursor like a state machine.</span></span> <span data-ttu-id="2a026-197">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2a026-197">For example:</span></span>
    * <span data-ttu-id="2a026-198">アイドル状態は、既定のカーソルを表示する場所です。</span><span class="sxs-lookup"><span data-stu-id="2a026-198">Idle state is where you show the default cursor.</span></span>
    * <span data-ttu-id="2a026-199">準備完了の状態は、ユーザーの手が準備完了の位置にあることを検出したときに表示されます。</span><span class="sxs-lookup"><span data-stu-id="2a026-199">Ready state is when you've detected the user's hand in the ready position.</span></span>
    * <span data-ttu-id="2a026-200">対話状態は、ユーザーが特定の操作を行っているときに行われます。</span><span class="sxs-lookup"><span data-stu-id="2a026-200">Interaction state is when the user is doing a particular interaction.</span></span>
    * <span data-ttu-id="2a026-201">考えられるアクションの状態またはホバー状態は、ホログラムで実行できるアクションを伝達するときに使用されます。</span><span class="sxs-lookup"><span data-stu-id="2a026-201">Possible Actions state or hover state is when you convey possible actions that can be performed on a hologram.</span></span>

<span data-ttu-id="2a026-202">また、これらの状態をスキン対応の方法で実装して、さまざまな状態を検出したときにさまざまなアートアセットを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="2a026-202">You could also implement these states in a skin-able manner to display different art assets when you detect different states.</span></span>

<br>

---

## <a name="going-cursor-free"></a><span data-ttu-id="2a026-203">"カーソルを利用しない"</span><span class="sxs-lookup"><span data-stu-id="2a026-203">Going "cursor-free"</span></span>

<span data-ttu-id="2a026-204">Immersion の意味がエクスペリエンスの重要な要素であり、(宝石とジェスチャを使用して) 相互作用をポイントする場合、十分な精度を必要としない場合は、カーソルを使用せずにデザインすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2a026-204">Designing without a cursor is recommended when the sense of immersion is a key component of an experience and when pointing interactions (through gaze and gesture) don't require great precision.</span></span> <span data-ttu-id="2a026-205">システムはカーソルの通常の要件を満たしている必要があります。システムがポイントを理解していることについての継続的なフィードバックをユーザーに提供し、システムへの意思疎通を支援します。</span><span class="sxs-lookup"><span data-stu-id="2a026-205">The system still needs to meet the normal requirements of a cursor: providing users with continuous feedback on the system's understanding of their pointing, and helping them to communicate their intentions to the system.</span></span> <span data-ttu-id="2a026-206">これは、他の顕著な状態の変更によって実現可能です。</span><span class="sxs-lookup"><span data-stu-id="2a026-206">This may be achievable through other noticeable state changes.</span></span>

<br>

---

## <a name="cursor-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="2a026-207">Unity の MRTK (Mixed Reality Toolkit) のカーソル</span><span class="sxs-lookup"><span data-stu-id="2a026-207">Cursor in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="2a026-208">既定では、 [Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity) には、シェルのシステムカーソルと同じビジュアル状態を持つカーソル事前 Fab ([defaultcursor. prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) が用意されています。</span><span class="sxs-lookup"><span data-stu-id="2a026-208">By default, [MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides a cursor prefab([DefaultCursor.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Cursors)) which has the same visual state as the shell's system cursor.</span></span> <span data-ttu-id="2a026-209">これは、[ポインター] にある MRTK の入力プロファイルに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="2a026-209">It's assigned in MRTK's Input profile, under Pointers.</span></span> <span data-ttu-id="2a026-210">このカーソルを置き換えたり、カスタマイズしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="2a026-210">You can replace/customize this cursor for your experience.</span></span> <span data-ttu-id="2a026-211">アイトラッキング入力のエクスペリエンスを実現するために、MRTK には EyeGazeCursor も用意されています。これにより、視覚効果を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="2a026-211">For the experience with eye-tracking input, MRTK also provides EyeGazeCursor, which has subtle visual to minimize the distraction.</span></span>

* [<span data-ttu-id="2a026-212">MRTK - ポインター プロファイル</span><span class="sxs-lookup"><span data-stu-id="2a026-212">MRTK - Pointer profile</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [<span data-ttu-id="2a026-213">MRTK - 入力システム</span><span class="sxs-lookup"><span data-stu-id="2a026-213">MRTK - Input system</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [<span data-ttu-id="2a026-214">MRTK - ポインター</span><span class="sxs-lookup"><span data-stu-id="2a026-214">MRTK - Pointers</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)

---

## <a name="see-also"></a><span data-ttu-id="2a026-215">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a026-215">See also</span></span>

* [<span data-ttu-id="2a026-216">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="2a026-216">Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="2a026-217">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="2a026-217">Head-gaze and commit</span></span>](gaze-and-commit.md)