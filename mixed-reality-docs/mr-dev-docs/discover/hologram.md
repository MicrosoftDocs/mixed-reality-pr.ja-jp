---
title: ホログラムとは
description: HoloLens を使用すると、3次元のホログラム、光とサウンドで構成されるオブジェクトを、世界中に表示して対話することができます。
author: hferrone
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、ホログラム、設計、対話、Mixed reality ヘッドセット、windows mixed reality ヘッドセット、強化された現実
ms.openlocfilehash: b390910fcece8e6263d19f52c80b784efb2561f6
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757560"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="e967b-104">ホログラムとは</span><span class="sxs-lookup"><span data-stu-id="e967b-104">What is a hologram?</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


<span data-ttu-id="e967b-105">HoloLens では **ホログラム** を作成できます。これは、実際のオブジェクトのように世界中に表示される光とサウンドで構成されるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="e967b-105">HoloLens lets you create **holograms**, which are objects made of light and sound that appear in the world around you like real objects.</span></span> <span data-ttu-id="e967b-106">ホログラムは、 [宝石](../design/gaze-and-commit.md)、 [ジェスチャ](../design/gaze-and-commit.md#composite-gestures)、 [音声コマンド](../design/voice-input.md)に応答します。</span><span class="sxs-lookup"><span data-stu-id="e967b-106">Holograms respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures), and [voice commands](../design/voice-input.md).</span></span> <span data-ttu-id="e967b-107">これらのユーザーは、 [現実世界の表面](../design/spatial-mapping.md) と対話することもできます。</span><span class="sxs-lookup"><span data-stu-id="e967b-107">They can even interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="e967b-108">ホログラムを使用すると、世界の一部であるデジタル オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e967b-108">With holograms, you can create digital objects that are part of your world.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="e967b-109">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="e967b-109">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e967b-110"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="e967b-110"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="e967b-111"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="e967b-111"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="e967b-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="e967b-112"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="e967b-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="e967b-113"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e967b-114">ホログラム</span><span class="sxs-lookup"><span data-stu-id="e967b-114">Holograms</span></span></td>
        <td><span data-ttu-id="e967b-115">✔️</span><span class="sxs-lookup"><span data-stu-id="e967b-115">✔️</span></span></td>
        <td><span data-ttu-id="e967b-116">✔️</span><span class="sxs-lookup"><span data-stu-id="e967b-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="e967b-117">ホログラムは、ライトとサウンドで構成されます。</span><span class="sxs-lookup"><span data-stu-id="e967b-117">A hologram is made of light and sound</span></span>

<span data-ttu-id="e967b-118">HoloLens が [レンダリング](../develop/platform-capabilities-and-apis/rendering.md) するホログラムは、ユーザーの目の前に holographic フレームに直接表示されます。</span><span class="sxs-lookup"><span data-stu-id="e967b-118">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="e967b-119">ホログラムは、画面の光と周囲の光を両方とも見ることができるように、世界に光を追加します。</span><span class="sxs-lookup"><span data-stu-id="e967b-119">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="e967b-120">HoloLens は目から光を削除しません。そのため、ホログラムは黒の色でレンダリングできません。</span><span class="sxs-lookup"><span data-stu-id="e967b-120">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="e967b-121">代わりに、黒のコンテンツは透明として表示されます。</span><span class="sxs-lookup"><span data-stu-id="e967b-121">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="e967b-122">ホログラムは、さまざまな外観と動作を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="e967b-122">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="e967b-123">現実的で安定したものもあれば、漫画と ethereal もあります。</span><span class="sxs-lookup"><span data-stu-id="e967b-123">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="e967b-124">ホログラムを使用して、周囲の特徴を強調表示したり、アプリのユーザーインターフェイスの要素として使用したりできます。</span><span class="sxs-lookup"><span data-stu-id="e967b-124">You can use holograms to highlight features in your surroundings or use them as elements in your app's user interface.</span></span>

![ホログラムをハンド操作する](images/hologram-hands-940px.jpg)

<span data-ttu-id="e967b-126">ホログラムは [サウンド](../design/spatial-sound.md)を作成することもできます。これは、周囲の特定の場所から発生するように見えます。</span><span class="sxs-lookup"><span data-stu-id="e967b-126">Holograms can also make [sounds](../design/spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="e967b-127">HoloLens では、耳の上に直接配置されている2つのスピーカーをカバーせずに聞こえます。</span><span class="sxs-lookup"><span data-stu-id="e967b-127">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="e967b-128">ディスプレイと同様に、スピーカーは追加され、環境のサウンドをブロックすることなく新しいサウンドを導入します。</span><span class="sxs-lookup"><span data-stu-id="e967b-128">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="e967b-129">ホログラムは、世界またはタグに配置できます。</span><span class="sxs-lookup"><span data-stu-id="e967b-129">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="e967b-130">ホログラムの特定の場所を持っている場合は、その位置に正確に [配置](../design/coordinate-systems.md) することができます。</span><span class="sxs-lookup"><span data-stu-id="e967b-130">When you have a particular location for a hologram, you can [place](../design/coordinate-systems.md) it precisely at that point in the world.</span></span> <span data-ttu-id="e967b-131">説明のとおり、ホログラムは、お近くの世界に基づいて安定したものとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="e967b-131">As you walk around, the hologram appears stable based on the world around you.</span></span> <span data-ttu-id="e967b-132">[空間アンカー](../design/coordinate-systems.md#spatial-anchors)を使用してオブジェクトをピン留めすると、後で元に戻ったときに、システムによってそのまま残されている場所を記憶できます。</span><span class="sxs-lookup"><span data-stu-id="e967b-132">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin the object, the system can even remember where you left it when you come back later.</span></span>

![小売スペースで Microsoft Dynamics 365 レイアウトを使用する2人の男性](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="e967b-134">一部のホログラムは、ユーザーに代わって、ユーザーに代わってユーザーに基づいて配置されます。</span><span class="sxs-lookup"><span data-stu-id="e967b-134">Some holograms follow the user instead, positioning themselves based on the user no matter where they walk.</span></span> <span data-ttu-id="e967b-135">また、別の部屋に手を付けた後で、一度にホログラムを入れて壁に配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="e967b-135">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="e967b-136">**ベスト プラクティス**</span><span class="sxs-lookup"><span data-stu-id="e967b-136">**Best practices**</span></span>
* <span data-ttu-id="e967b-137">一部のシナリオでは、ホログラムを簡単に検出したり、エクスペリエンス全体に表示したりする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="e967b-137">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="e967b-138">この種の配置には、次の2つの高レベルのアプローチがあります。</span><span class="sxs-lookup"><span data-stu-id="e967b-138">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="e967b-139">**"Display-locked"** と **"body-locked"** を呼び出しましょう。</span><span class="sxs-lookup"><span data-stu-id="e967b-139">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="e967b-140">画面のロックされたコンテンツは、デバイスのディスプレイに "locked" 位置れます。</span><span class="sxs-lookup"><span data-stu-id="e967b-140">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="e967b-141">この種のコンテンツは、いくつかの理由から、多くのユーザーが不満を感じて、"シェイクを clingyness" ことを望んでいるという不自然なことがあります。</span><span class="sxs-lookup"><span data-stu-id="e967b-141">This type of content is tricky for several reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="e967b-142">一般に、多くのデザイナーでは、表示ロックの内容を避けることが適切であることがわかりました。</span><span class="sxs-lookup"><span data-stu-id="e967b-142">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="e967b-143">本文ロックのアプローチは、はるかに forgivable です。</span><span class="sxs-lookup"><span data-stu-id="e967b-143">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="e967b-144">ボディロックは、ユーザーの本文にホログラムを置いた場合、または3d 空間で宝石を見つめた場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="e967b-144">Body-locking is when you tether a hologram to the user's body or gaze vector in 3d space.</span></span> <span data-ttu-id="e967b-145">多くのエクスペリエンスでは、ホログラムが "後" にあるユーザーを見つめているボディロック動作が採用されています。これにより、ユーザーは、ホログラムを紛失することなく、本文を回転させたり、スペースを移動したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="e967b-145">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="e967b-146">遅延を組み込むことにより、ホログラムの動きがより自然になります。</span><span class="sxs-lookup"><span data-stu-id="e967b-146">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="e967b-147">たとえば、Windows Holographic OS のコア UI の中には、ユーザーが頭を変えたときに、柔軟に似た緩やかな遅延でユーザーの宝石に続くボディロックのバリエーションが使用されているものがあります。</span><span class="sxs-lookup"><span data-stu-id="e967b-147">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="e967b-148">見やすい距離にホログラムを配置します。通常は、ヘッドから約1-2 メートル離れています。</span><span class="sxs-lookup"><span data-stu-id="e967b-148">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="e967b-149">Holographic フレーム内に常に存在する必要がある要素の誤差量を指定するか、ユーザーが視点を変更したときに、コンテンツを表示の片側にアニメーション化することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e967b-149">Provide a drift amount for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="e967b-150">**最適なゾーンにホログラムを配置する (1.25 m ~ 5 m)**</span><span class="sxs-lookup"><span data-stu-id="e967b-150">**Place holograms in the optimal zone - between 1.25 m and 5 m**</span></span>

<span data-ttu-id="e967b-151">2つのメーターが最適です。1メートルから得られるほど、エクスペリエンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="e967b-151">Two meters is the most optimal, and the experience will degrade the closer you get from 1 meter.</span></span> <span data-ttu-id="e967b-152">1メートル未満の距離では、一般的に深く移動するホログラムは、固定されたホログラムよりも問題になる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="e967b-152">At distances nearer than 1 meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="e967b-153">コンテンツを適切にクリッピングまたはフェードアウトすることを検討してください。そうすれば、ユーザーが予期しないエクスペリエンスになることはありません。</span><span class="sxs-lookup"><span data-stu-id="e967b-153">Consider gracefully clipping or fading out your content when it gets too close so you don't jar the user into an unexpected experience.</span></span>

![ユーザーからのホログラムを配置するための最適な距離。](images/distanceguiderendering-950px.png)

<br>

---

## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="e967b-155">ホログラムがあなたと世界と対話する</span><span class="sxs-lookup"><span data-stu-id="e967b-155">A hologram interacts with you and your world</span></span>

<span data-ttu-id="e967b-156">ホログラムは光とサウンドだけではありません。また、世界中のアクティブな部分でもあります。</span><span class="sxs-lookup"><span data-stu-id="e967b-156">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="e967b-157">手でホログラムとジェスチャを見つめ、ホログラムを使用して、お客様によるフォローを開始することができます。</span><span class="sxs-lookup"><span data-stu-id="e967b-157">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="e967b-158">ホログラムに音声コマンドを指定すると、応答できます。</span><span class="sxs-lookup"><span data-stu-id="e967b-158">Give a voice command to a hologram, and it can reply.</span></span>

![Microsoft HoloLens 2 を使用して、風力 farm 開発プロジェクトで共同作業を行う政府ユーティリティ worker のグループ](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="e967b-160">ホログラムを使用すると、他の場所では不可能な個人の対話が可能になります。</span><span class="sxs-lookup"><span data-stu-id="e967b-160">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="e967b-161">HoloLens は、世界中の場所を認識しているので、holographic 文字を使用すると、部屋の周りを移動するときに、目に見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="e967b-161">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="e967b-162">ホログラムは、周囲と対話することもできます。</span><span class="sxs-lookup"><span data-stu-id="e967b-162">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="e967b-163">たとえば、テーブルの上に holographic バウンスボールを配置できます。</span><span class="sxs-lookup"><span data-stu-id="e967b-163">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="e967b-164">次に、 [エアタップ](../design/gaze-and-commit.md#composite-gestures)を使用してボールのバウンスを観察し、テーブルにヒットしたときに音を鳴らします。</span><span class="sxs-lookup"><span data-stu-id="e967b-164">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce, and make sound when it hits the table.</span></span>

<span data-ttu-id="e967b-165">ホログラムは、実世界のオブジェクトによって occluded することもできます。</span><span class="sxs-lookup"><span data-stu-id="e967b-165">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="e967b-166">たとえば、holographic 文字を使用すると、扉と壁の背後に移動することができます。</span><span class="sxs-lookup"><span data-stu-id="e967b-166">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="e967b-167">**ホログラムと実際の世界を統合するためのヒント**</span><span class="sxs-lookup"><span data-stu-id="e967b-167">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="e967b-168">Gravitational の規則に合わせて、ホログラムをさらに多くの believable に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="e967b-168">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="e967b-169">例: holographic dog を地面に配置して、スペースではなくテーブルの花瓶を & します。</span><span class="sxs-lookup"><span data-stu-id="e967b-169">for example: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="e967b-170">多くのデザイナーでは、ホログラムが置かれている表面に "負の影" を作成することによって、より多くの believable ホログラムを統合できることがわかりました。</span><span class="sxs-lookup"><span data-stu-id="e967b-170">Many designers have found that they can integrate more believable holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="e967b-171">これを行うには、ホログラムの周りにソフトグローを作成し、グローから "影" を引います。</span><span class="sxs-lookup"><span data-stu-id="e967b-171">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="e967b-172">ソフトグローは、実際の世界の光と統合されています。これは、環境内のホログラムに影を使用します。</span><span class="sxs-lookup"><span data-stu-id="e967b-172">The soft glow integrates with the light from the real world, which uses the shadow to ground the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a><span data-ttu-id="e967b-173">ホログラムはどのようなものですか。</span><span class="sxs-lookup"><span data-stu-id="e967b-173">A hologram is whatever</span></span> <br><span data-ttu-id="e967b-174">夢を</span><span class="sxs-lookup"><span data-stu-id="e967b-174">you can dream up</span></span><br>
        <span data-ttu-id="e967b-175">Holographic の開発者として、お客様の創造性を、2D 画面や世界中に分割する力を持っています。</span><span class="sxs-lookup"><span data-stu-id="e967b-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="e967b-176">何をビルド *し* ますか?</span><span class="sxs-lookup"><span data-stu-id="e967b-176">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="e967b-177">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="e967b-177">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="e967b-178">![リビングルームの Holographic 虚数ワールド](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="e967b-178">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="e967b-179">次の探索チェックポイント</span><span class="sxs-lookup"><span data-stu-id="e967b-179">Next Discovery Checkpoint</span></span>

<span data-ttu-id="e967b-180">私たちが用意した[探索ツアー](get-started-with-mr.md)を進んでいる場合、あなたの現在地は Mixed Reality の基本の探索の中盤の段階です。</span><span class="sxs-lookup"><span data-stu-id="e967b-180">If you're following the [discovery journey](get-started-with-mr.md) we've laid out, you're in the midst of exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="e967b-181">ここからは、次の基本トピックに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="e967b-181">From here, you can continue to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="e967b-182">デザイン プロセスを展開する</span><span class="sxs-lookup"><span data-stu-id="e967b-182">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)

