---
title: ホログラムとは
description: HoloLens を使用すると、3次元のホログラム、光とサウンドで構成されるオブジェクトを、世界中に表示して対話することができます。
author: hferrone
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、ホログラム、設計、相互作用
ms.openlocfilehash: 5e0ef2768b6e79136f8144492d6825107a6ed88e
ms.sourcegitcommit: 9a489e8a3bf90b20f1b61606eea42c859c833424
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2020
ms.locfileid: "94340700"
---
# <a name="what-is-a-hologram"></a><span data-ttu-id="b8bfc-104">ホログラムとは</span><span class="sxs-lookup"><span data-stu-id="b8bfc-104">What is a hologram?</span></span>

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


<span data-ttu-id="b8bfc-105">HoloLens を使用する **と、実際** のオブジェクトの場合と同様に、世界中に表示される電球、光、サウンドで構成されるオブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-105">HoloLens lets you create **holograms** , objects made of light and sound that appear in the world around you, just as if they were real objects.</span></span> <span data-ttu-id="b8bfc-106">ホログラムは、 [宝石](../design/gaze-and-commit.md)、 [ジェスチャ](../design/gaze-and-commit.md#composite-gestures) 、 [音声コマンド](../design/voice-input.md)に応答し、 [現実世界の表面](../design/spatial-mapping.md) と対話できます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-106">Holograms respond to your [gaze](../design/gaze-and-commit.md), [gestures](../design/gaze-and-commit.md#composite-gestures) and [voice commands](../design/voice-input.md), and can interact with [real-world surfaces](../design/spatial-mapping.md) around you.</span></span> <span data-ttu-id="b8bfc-107">ホログラムを使用すると、世界の一部であるデジタル オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-107">With holograms, you can create digital objects that are part of your world.</span></span>

<br>


## <a name="device-support"></a><span data-ttu-id="b8bfc-108">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="b8bfc-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="b8bfc-109"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="b8bfc-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b8bfc-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="b8bfc-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="b8bfc-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="b8bfc-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="b8bfc-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="b8bfc-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b8bfc-113">ホログラム</span><span class="sxs-lookup"><span data-stu-id="b8bfc-113">Holograms</span></span></td>
        <td><span data-ttu-id="b8bfc-114">✔️</span><span class="sxs-lookup"><span data-stu-id="b8bfc-114">✔️</span></span></td>
        <td><span data-ttu-id="b8bfc-115">✔️</span><span class="sxs-lookup"><span data-stu-id="b8bfc-115">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a><span data-ttu-id="b8bfc-116">ホログラムは、ライトとサウンドで構成されます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-116">A hologram is made of light and sound</span></span>

<span data-ttu-id="b8bfc-117">HoloLens が [レンダリング](../develop/platform-capabilities-and-apis/rendering.md) するホログラムは、ユーザーの目の前に holographic フレームに直接表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-117">The holograms that HoloLens [renders](../develop/platform-capabilities-and-apis/rendering.md) appear in the holographic frame directly in front of the user's eyes.</span></span> <span data-ttu-id="b8bfc-118">ホログラムは、画面の光と周囲の光を両方とも見ることができるように、世界に光を追加します。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-118">Holograms add light to your world, which means that you see both the light from the display and the light from your surroundings.</span></span> <span data-ttu-id="b8bfc-119">HoloLens は目から光を削除しません。そのため、ホログラムは黒の色でレンダリングできません。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-119">HoloLens doesn't remove light from your eyes, so holograms can't be rendered with the color black.</span></span> <span data-ttu-id="b8bfc-120">代わりに、黒のコンテンツは透明として表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-120">Instead, black content appears as transparent.</span></span>

<span data-ttu-id="b8bfc-121">ホログラムは、さまざまな外観と動作を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-121">Holograms can have many different appearances and behaviors.</span></span> <span data-ttu-id="b8bfc-122">現実的で安定したものもあれば、漫画と ethereal もあります。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-122">Some are realistic and solid, and others are cartoonish and ethereal.</span></span> <span data-ttu-id="b8bfc-123">ホログラムは、環境内の特徴を強調表示し、アプリのユーザーインターフェイスの要素にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-123">Holograms can highlight features in your surroundings, and they can be elements in your app's user interface.</span></span>

![ホログラムをハンド操作する](images/hologram-hands-940px.jpg)

<span data-ttu-id="b8bfc-125">ホログラムは [サウンド](../design/spatial-sound.md)を作成することもできます。これは、周囲の特定の場所から発生するように見えます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-125">Holograms can also make [sounds](../design/spatial-sound.md), which will appear to come from a specific place in your surroundings.</span></span> <span data-ttu-id="b8bfc-126">HoloLens では、耳の上に直接配置されている2つのスピーカーをカバーせずに聞こえます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-126">On HoloLens, sound comes from two speakers that are located directly above your ears, without covering them.</span></span> <span data-ttu-id="b8bfc-127">ディスプレイと同様に、スピーカーは追加され、環境のサウンドをブロックすることなく新しいサウンドを導入します。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-127">Similar to the displays, the speakers are additive, introducing new sounds without blocking the sounds from your environment.</span></span>

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a><span data-ttu-id="b8bfc-128">ホログラムは、世界またはタグに配置できます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-128">A hologram can be placed in the world or tag along with you</span></span>

<span data-ttu-id="b8bfc-129">ホログラムが必要な場所がある場合は、それを世界中に正確に [配置](../design/coordinate-systems.md) することができます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-129">When you have a particular location where you want a hologram, you can [place](../design/coordinate-systems.md) it precisely there in the world.</span></span> <span data-ttu-id="b8bfc-130">このホログラムを操作すると、ユーザーに対して相対的に安定したものとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-130">As you walk around that hologram, it will appear stable relative to the world around you.</span></span> <span data-ttu-id="b8bfc-131">[空間アンカー](../design/coordinate-systems.md#spatial-anchors)を使用してオブジェクトを世界にしっかりピン留めしている場合は、後で戻るときに、システムによってどこから離れているかを記憶できます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-131">If you use a [spatial anchor](../design/coordinate-systems.md#spatial-anchors) to pin that object firmly to the world, the system can even remember where you left it when you come back later.</span></span>

![小売スペースで Microsoft Dynamics 365 レイアウトを使用する2人の男性](images/HLS19_retailLayoutHologram_001-940px.jpg)

<span data-ttu-id="b8bfc-133">一部のホログラムはユーザーに代わります。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-133">Some holograms follow the user instead.</span></span> <span data-ttu-id="b8bfc-134">これらのタグは、どこにいるかに関係なく、ユーザーに対して相対的に位置付けられます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-134">These tag-along holograms position themselves relative to the user, no matter where they walk.</span></span> <span data-ttu-id="b8bfc-135">また、別の部屋に手を付けた後で、一度にホログラムを入れて壁に配置することもできます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-135">You may even choose to bring a hologram with you for a while and then place it on the wall once you get to another room.</span></span>

<span data-ttu-id="b8bfc-136">**ベスト プラクティス**</span><span class="sxs-lookup"><span data-stu-id="b8bfc-136">**Best practices**</span></span>
* <span data-ttu-id="b8bfc-137">一部のシナリオでは、ホログラムを簡単に検出したり、エクスペリエンス全体に表示したりする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-137">Some scenarios may demand that holograms remain easily discoverable or visible throughout the experience.</span></span> <span data-ttu-id="b8bfc-138">この種の配置には、次の2つの高レベルのアプローチがあります。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-138">There are two high-level approaches to this kind of positioning.</span></span> <span data-ttu-id="b8bfc-139">**"Display-locked"** と **"body-locked"** を呼び出しましょう。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-139">Let's call them **"display-locked"** and **"body-locked"**.</span></span>
   * <span data-ttu-id="b8bfc-140">画面のロックされたコンテンツは、デバイスのディスプレイに "locked" 位置れます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-140">Display-locked content is positionally "locked" to the device display.</span></span> <span data-ttu-id="b8bfc-141">これは、多くのユーザーが不満を感じ、"シェイクを clingyness" ことを望んでいるような不自然な "" を含むさまざまな理由により、非常に厄介です。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-141">This is tricky for a number of reasons, including an unnatural feeling of "clingyness" that makes many users frustrated and wanting to "shake it off."</span></span> <span data-ttu-id="b8bfc-142">一般に、多くのデザイナーでは、表示ロックの内容を避けることが適切であることがわかりました。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-142">In general, many designers have found it better to avoid display-locking content.</span></span>
   * <span data-ttu-id="b8bfc-143">本文ロックのアプローチは、はるかに forgivable です。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-143">The body-locked approach is far more forgivable.</span></span> <span data-ttu-id="b8bfc-144">ボディロックは、ホログラムがユーザーの本文またはテザリングさに配置されているにもかかわらず、ユーザーの周りに3d 空間に配置されている場合に行います。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-144">Body-locking is when a hologram is tethered to the user's body or gaze vector, but is positioned in 3d space around the user.</span></span> <span data-ttu-id="b8bfc-145">多くのエクスペリエンスでは、ホログラムが "後" にあるユーザーを見つめているボディロック動作が採用されています。これにより、ユーザーは、ホログラムを紛失することなく、本文を回転させたり、スペースを移動したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-145">Many experiences have adopted a body-locking behavior where the hologram "follows" the users gaze, which allows the user to rotate their body and move through space without losing the hologram.</span></span> <span data-ttu-id="b8bfc-146">遅延を組み込むことにより、ホログラムの動きがより自然になります。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-146">Incorporating a delay helps the hologram movement feel more natural.</span></span> <span data-ttu-id="b8bfc-147">たとえば、Windows Holographic OS のコア UI の中には、ユーザーが頭を変えたときに、柔軟に似た緩やかな遅延でユーザーの宝石に続くボディロックのバリエーションが使用されているものがあります。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-147">For example, some core UI of the Windows Holographic OS uses a variation on body-locking that follows the user's gaze with a gentle, elastic-like delay while the user turns their head.</span></span>
* <span data-ttu-id="b8bfc-148">見やすい距離にホログラムを配置します。通常は、ヘッドから約1-2 メートル離れています。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-148">Place the hologram at a comfortable viewing distance typically about 1-2 meters away from the head.</span></span>
* <span data-ttu-id="b8bfc-149">Holographic フレーム内に常に存在する必要がある要素の誤差の量を指定するか、ユーザーが視点を変更したときに、コンテンツを表示の片側にアニメーション化することを検討します。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-149">Provide an amount of drift for elements that must be continually in the holographic frame, or consider animating your content to one side of the display when the user changes their point of view.</span></span>

<span data-ttu-id="b8bfc-150">**最適なゾーンにホログラムを配置する (1.25 m から5分の間)**</span><span class="sxs-lookup"><span data-stu-id="b8bfc-150">**Place holograms in the optimal zone - between 1.25m and 5m**</span></span>

<span data-ttu-id="b8bfc-151">2つのメーターが最適です。1つのメーターから見た方が近づくほど、エクスペリエンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-151">Two meters is the most optimal, and the experience will degrade the closer you get from one meter.</span></span> <span data-ttu-id="b8bfc-152">1つのメーターよりも近い距離で、多くの場合に頻繁に移動するホログラムは、固定されたホログラムよりも問題になる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-152">At distances nearer than one meter, holograms that regularly move in depth are more likely to be problematic than stationary holograms.</span></span> <span data-ttu-id="b8bfc-153">ユーザーを予期しないエクスペリエンスにすることができないように、コンテンツが近すぎる場合は、適切にクリッピングまたはフェードアウトすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-153">Consider gracefully clipping or fading out your content when it gets too close so as not to jar the user into an unexpected experience.</span></span>

![ユーザーからのホログラムを配置するための最適な距離。](images/distanceguiderendering-950px.png)

<br>

---


## <a name="a-hologram-interacts-with-you-and-your-world"></a><span data-ttu-id="b8bfc-155">ホログラムがあなたと世界と対話する</span><span class="sxs-lookup"><span data-stu-id="b8bfc-155">A hologram interacts with you and your world</span></span>

<span data-ttu-id="b8bfc-156">ホログラムは光とサウンドだけではありません。また、世界中のアクティブな部分でもあります。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-156">Holograms aren't only about light and sound; they're also an active part of your world.</span></span> <span data-ttu-id="b8bfc-157">手でホログラムとジェスチャを見つめ、ホログラムを使用して、お客様によるフォローを開始することができます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-157">Gaze at a hologram and gesture with your hand, and a hologram can start to follow you.</span></span> <span data-ttu-id="b8bfc-158">ホログラムに音声コマンドを指定すると、応答できます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-158">Give a voice command to a hologram, and it can reply.</span></span>

![Microsoft HoloLens 2 を使用して、風力 farm 開発プロジェクトで共同作業を行う政府ユーティリティ worker のグループ](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

<span data-ttu-id="b8bfc-160">ホログラムを使用すると、他の場所では不可能な個人の対話が可能になります。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-160">Holograms enable personal interactions that aren't possible elsewhere.</span></span> <span data-ttu-id="b8bfc-161">HoloLens は、世界中の場所を認識しているので、holographic 文字を使用すると、部屋の周りを移動するときに、目に見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-161">Because the HoloLens knows where it is in the world, a holographic character can look you directly in the eyes as you walk around the room.</span></span>

<span data-ttu-id="b8bfc-162">ホログラムは、周囲と対話することもできます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-162">A hologram can also interact with your surroundings.</span></span> <span data-ttu-id="b8bfc-163">たとえば、テーブルの上に holographic バウンスボールを配置できます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-163">For example, you can place a holographic bouncing ball above a table.</span></span> <span data-ttu-id="b8bfc-164">次に、 [エアタップ](../design/gaze-and-commit.md#composite-gestures)でボールを見て、テーブルにヒットしたときに音を鳴らします。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-164">Then, with an [air tap](../design/gaze-and-commit.md#composite-gestures), watch the ball bounce and make sound when it hits the table.</span></span>

<span data-ttu-id="b8bfc-165">ホログラムは、実世界のオブジェクトによって occluded することもできます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-165">Holograms can also be occluded by real-world objects.</span></span> <span data-ttu-id="b8bfc-166">たとえば、holographic 文字を使用すると、扉と壁の背後に移動することができます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-166">For example, a holographic character might walk through a door and behind a wall, out of your sight.</span></span>

<span data-ttu-id="b8bfc-167">**ホログラムと実際の世界を統合するためのヒント**</span><span class="sxs-lookup"><span data-stu-id="b8bfc-167">**Tips for integrating holograms and the real world**</span></span>
* <span data-ttu-id="b8bfc-168">Gravitational の規則に合わせて、ホログラムをさらに多くの believable に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-168">Aligning to gravitational rules makes holograms easier to relate to and more believable.</span></span> <span data-ttu-id="b8bfc-169">例: holographic dog は、スペースではなくテーブルの花瓶に & ています。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-169">eg: Place a holographic dog on the ground & a vase on the table rather than have them floating in space.</span></span>
* <span data-ttu-id="b8bfc-170">多くのデザイナーでは、ホログラムが置かれている表面に "負の影" を作成することによって、ホログラムをさらに believably に統合できることがわかりました。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-170">Many designers have found that they can even more believably integrate holograms by creating a "negative shadow" on the surface that the hologram is sitting on.</span></span> <span data-ttu-id="b8bfc-171">これを行うには、ホログラムの周りにソフトグローを作成し、グローから "影" を引います。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-171">They do this by creating a soft glow on the ground around the hologram and then subtracting the "shadow" from the glow.</span></span> <span data-ttu-id="b8bfc-172">ソフトグローは、現実世界の光と統合され、環境内のホログラムを grounds します。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-172">The soft glow integrates with the light from the real world and the shadow grounds the hologram in the environment.</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a><span data-ttu-id="b8bfc-173">ホログラムはどのようなものですか。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-173">A hologram is whatever</span></span> <br><span data-ttu-id="b8bfc-174">夢を</span><span class="sxs-lookup"><span data-stu-id="b8bfc-174">you can dream up</span></span><br>
        <span data-ttu-id="b8bfc-175">Holographic の開発者として、お客様の創造性を、2D 画面や世界中に分割する力を持っています。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-175">As a holographic developer, you have the power to break your creativity out of 2D screens and into the world around you.</span></span><br><br>
        <span data-ttu-id="b8bfc-176">何をビルド *し* ますか?</span><span class="sxs-lookup"><span data-stu-id="b8bfc-176">What will *you* build?</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="b8bfc-177">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="b8bfc-177">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="b8bfc-178">![リビングルームの Holographic 虚数ワールド](images/designoverview.jpg)</span><span class="sxs-lookup"><span data-stu-id="b8bfc-178">![Holographic imaginary world in living room](images/designoverview.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a><span data-ttu-id="b8bfc-179">次回の検出チェックポイント</span><span class="sxs-lookup"><span data-stu-id="b8bfc-179">Next Discovery Checkpoint</span></span>

<span data-ttu-id="b8bfc-180">ここまでに説明した [探索](get-started-with-mr.md) の方法に従っている場合は、Mixed Reality の基本を確認しています。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-180">If you're following the [discovery journey](get-started-with-mr.md) we've laid out, you're in the midst of exploring the basics of Mixed Reality.</span></span> <span data-ttu-id="b8bfc-181">ここから、次の基本トピックに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-181">From here, you can proceed to the next foundational topic:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="b8bfc-182">仕事のための新しいビジョン</span><span class="sxs-lookup"><span data-stu-id="b8bfc-182">A new vision for work</span></span>](https://dynamics.microsoft.com//mixed-reality/overview/)

<span data-ttu-id="b8bfc-183">または、にジャンプします。</span><span class="sxs-lookup"><span data-stu-id="b8bfc-183">Or jump to:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b8bfc-184">よりパーソナルなコンピューティングの追求</span><span class="sxs-lookup"><span data-stu-id="b8bfc-184">The pursuit of more personal computing</span></span>](../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md)

## <a name="see-also"></a><span data-ttu-id="b8bfc-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="b8bfc-185">See also</span></span>
* [<span data-ttu-id="b8bfc-186">デザイン プロセスを展開する</span><span class="sxs-lookup"><span data-stu-id="b8bfc-186">Expand your design process</span></span>](case-study-expanding-the-design-process-for-mixed-reality.md)
* [<span data-ttu-id="b8bfc-187">立体音響</span><span class="sxs-lookup"><span data-stu-id="b8bfc-187">Spatial sound</span></span>](../design/spatial-sound.md)
* [<span data-ttu-id="b8bfc-188">色、ライト、マテリアル</span><span class="sxs-lookup"><span data-stu-id="b8bfc-188">Color, light and materials</span></span>](../color,-light-and-materials.md)
