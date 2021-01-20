---
title: 視線入力とコミット
description: 2種類の宝石 (ヘッド宝石と視線)、およびさまざまな種類のコミットを含む、宝石とコミットの入力モデルについて説明します。
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality、宝石、ビジョン化、相互作用、設計、視線追跡、ヘッド追跡、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: bfbf58ad065f91b27208d36ba63672ee5c28dfdd
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582330"
---
# <a name="gaze-and-commit"></a><span data-ttu-id="2130a-104">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="2130a-104">Gaze and commit</span></span>

<span data-ttu-id="2130a-105">_宝石とコミットメント_ は、マウス: _ポイント & クリック_ を使用してコンピューターと対話する方法に密接に関連する基本的な入力モデルです。</span><span class="sxs-lookup"><span data-stu-id="2130a-105">_Gaze and commit_ is a fundamental input model that is closely related to the way we're interacting with our computers using the mouse: _Point & click_.</span></span> <span data-ttu-id="2130a-106">このページでは、2種類の宝石入力 (ヘッドと視線) とさまざまな種類のコミットアクションを紹介します。</span><span class="sxs-lookup"><span data-stu-id="2130a-106">On this page, we introduce two types of gaze input (head- and eye-gaze) and different types of commit actions.</span></span> <span data-ttu-id="2130a-107">_宝石とコミットメント_ は、間接的な操作による遠くの入力モデルと見なされます。</span><span class="sxs-lookup"><span data-stu-id="2130a-107">_Gaze and commit_ is considered a far input model with indirect manipulation.</span></span> <span data-ttu-id="2130a-108">これは、holographic コンテンツとのやり取りに最適です。</span><span class="sxs-lookup"><span data-stu-id="2130a-108">It's best used for interacting with holographic content that is out of reach.</span></span>

<span data-ttu-id="2130a-109">Mixed reality ヘッドセットでは、ユーザーのヘッドの位置と向きを使用して、そのヘッド方向ベクターを決定できます。</span><span class="sxs-lookup"><span data-stu-id="2130a-109">Mixed reality headsets can use the position and orientation of the user's head to determine their head direction vector.</span></span> <span data-ttu-id="2130a-110">ユーザーの目の間で直接のレーザーを指します。</span><span class="sxs-lookup"><span data-stu-id="2130a-110">Think of gaze as a laser pointing straight ahead from directly between the user's eyes.</span></span> <span data-ttu-id="2130a-111">これはユーザーが目を向けている場所の非常に粗い近似値です。</span><span class="sxs-lookup"><span data-stu-id="2130a-111">This is a fairly coarse approximation of where the user is looking.</span></span> <span data-ttu-id="2130a-112">アプリケーションでは、この射線と仮想または実世界のオブジェクトを交差させ、その位置にカーソルを描画して、ターゲットの内容をユーザーに知らせることができます。</span><span class="sxs-lookup"><span data-stu-id="2130a-112">Your application can intersect this ray with virtual or real-world objects, and draw a cursor at that location to let the user know what they're targeting.</span></span>

<span data-ttu-id="2130a-113">また、HoloLens 2 など、一部の mixed reality ヘッドセットには、目を見つめたベクトルを作り出す視線追跡システムが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2130a-113">In addition to head gaze, some mixed reality headsets, such as HoloLens 2, include eye tracking systems that produce an eye-gaze vector.</span></span> <span data-ttu-id="2130a-114">これにより、ユーザーが目を向けている場所のきめ細かい測定値が得られます。</span><span class="sxs-lookup"><span data-stu-id="2130a-114">This provides a fine-grained measurement of where the user is looking.</span></span> <span data-ttu-id="2130a-115">どちらの場合も、宝石はユーザーの意図に対する重要な信号を表します。</span><span class="sxs-lookup"><span data-stu-id="2130a-115">In both cases, the gaze represents an important signal for the user's intent.</span></span> <span data-ttu-id="2130a-116">システムがユーザーの意図したアクションを解釈および予測できるので、ユーザーの満足度とパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="2130a-116">The better the system can interpret and predict the user's intended actions, the more user satisfaction and performance improves.</span></span>

<span data-ttu-id="2130a-117">次に示すのは、mixed reality 開発者が頭または目を見つめている場合の利点を示すいくつかの例です。</span><span class="sxs-lookup"><span data-stu-id="2130a-117">Below are a few examples for how you as a mixed reality developer can benefit from head- or eye-gaze:</span></span>
* <span data-ttu-id="2130a-118">アプリでは、シーン内のホログラムを使用して、ユーザーの注意がどこであるかを判断することができます (詳細については、「視線」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="2130a-118">Your app can intersect gaze with the holograms in your scene to determine where the user's attention is (more precise with eye-gaze).</span></span>
* <span data-ttu-id="2130a-119">アプリでは、ユーザーの宝石に基づいてチャネルのジェスチャとコントローラーを押すことができます。これにより、ユーザーは、そのホログラムをシームレスに選択、アクティブ化、グラブ、スクロール、またはその他の方法で操作できます。</span><span class="sxs-lookup"><span data-stu-id="2130a-119">Your app can channel gestures and controller presses based on the user's gaze, which lets the user seamlessly select, activate, grab, scroll, or otherwise interact with their holograms.</span></span>
* <span data-ttu-id="2130a-120">アプリを使用すると、空間マッピングメッシュを使用して、宝石を実際の表面に配置できます。</span><span class="sxs-lookup"><span data-stu-id="2130a-120">Your app can let the user place holograms on real-world surfaces by intersecting their gaze ray with the spatial mapping mesh.</span></span>
* <span data-ttu-id="2130a-121">アプリは、ユーザーが重要なオブジェクトの方向を確認していないことを知ることができます。これにより、アプリは、そのオブジェクトに対してビジュアルおよびオーディオの手掛かりを与えることができます。</span><span class="sxs-lookup"><span data-stu-id="2130a-121">Your app can know when the user isn't looking in the direction of an important object, which can lead your app to give visual and audio cues to turn towards that object.</span></span>

<br>

## <a name="device-support"></a><span data-ttu-id="2130a-122">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="2130a-122">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2130a-123"><strong>入力モデル</strong></span><span class="sxs-lookup"><span data-stu-id="2130a-123"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="2130a-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="2130a-124"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="2130a-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="2130a-125"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="2130a-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2130a-126"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2130a-127">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="2130a-127">Head-gaze and commit</span></span></td>
        <td><span data-ttu-id="2130a-128">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="2130a-128">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="2130a-129">✔️ 推奨 (3 番目の選択肢 -<a href="interaction-fundamentals.md">他のオプションを参照</a>)</span><span class="sxs-lookup"><span data-stu-id="2130a-129">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="2130a-130">➕ 代替オプション</span><span class="sxs-lookup"><span data-stu-id="2130a-130">➕ Alternate option</span></span></td>
    </tr>
         <tr>
        <td><span data-ttu-id="2130a-131">目の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="2130a-131">Eye-gaze and commit</span></span></td>
        <td><span data-ttu-id="2130a-132">❌ 使用できません</span><span class="sxs-lookup"><span data-stu-id="2130a-132">❌ Not available</span></span></td>
        <td><span data-ttu-id="2130a-133">✔️ 推奨 (3 番目の選択肢 -<a href="interaction-fundamentals.md">他のオプションを参照</a>)</span><span class="sxs-lookup"><span data-stu-id="2130a-133">✔️ Recommended (third choice - <a href="interaction-fundamentals.md">See the other options</a>)</span></span></td>
        <td><span data-ttu-id="2130a-134">❌ 使用できません</span><span class="sxs-lookup"><span data-stu-id="2130a-134">❌ Not available</span></span></td>
    </tr>
</table>


## <a name="gaze"></a><span data-ttu-id="2130a-135">視線入力</span><span class="sxs-lookup"><span data-stu-id="2130a-135">Gaze</span></span>

### <a name="eye--or-head-gaze"></a><span data-ttu-id="2130a-136">目を通して、またはヘッドを見つめますか。</span><span class="sxs-lookup"><span data-stu-id="2130a-136">Eye- or head-gaze?</span></span>
<span data-ttu-id="2130a-137">"視線とコミット" または "ヘッドを見つめ、コミット" 入力モデルを使用する必要があるかどうかについて、いくつかの考慮事項があります。</span><span class="sxs-lookup"><span data-stu-id="2130a-137">There are several considerations when faced with the question whether you should use the "eye-gaze and commit" or "head-gaze and commit" input model.</span></span> <span data-ttu-id="2130a-138">イマーシブヘッドセットまたは HoloLens (第1世代) 用に開発している場合、選択は簡単です。ヘッドを見つめ、コミットします。</span><span class="sxs-lookup"><span data-stu-id="2130a-138">If you're developing for an immersive headset or for HoloLens (1st gen), then the choice is simple: Head-gaze and commit.</span></span> <span data-ttu-id="2130a-139">HoloLens 2 用に開発している場合、選択肢は少し難しくなります。</span><span class="sxs-lookup"><span data-stu-id="2130a-139">If you're developing for HoloLens 2, the choice becomes a little harder.</span></span> <span data-ttu-id="2130a-140">それぞれに付随する利点と課題を理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="2130a-140">It's important to understand the advantages and challenges that come with each of them.</span></span>
<span data-ttu-id="2130a-141">ここでは、ヘッドと視点を見つめたターゲットを比較するために、次の表に示す幅広い pro とをまとめています。</span><span class="sxs-lookup"><span data-stu-id="2130a-141">We compiled some broad pro's and con's in the table below to contrast head- vs. eye-gaze targeting.</span></span> <span data-ttu-id="2130a-142">これは完全なものではありません。ここでは、混合現実における視点を見つめたターゲットについてさらに学習することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2130a-142">This is far from complete and we suggest learning more about eye-gaze targeting in mixed reality here:</span></span>
* <span data-ttu-id="2130a-143">[Hololens 2 の視線追跡](eye-tracking.md): 開発者向けのガイダンスを含む、hololens 2 での新しいアイ tracking 機能の概要。</span><span class="sxs-lookup"><span data-stu-id="2130a-143">[Eye tracking on HoloLens 2](eye-tracking.md): General introduction of our new eye tracking capability on HoloLens 2 including some developer guidance.</span></span> 
* <span data-ttu-id="2130a-144">視線に[よる対話](eye-gaze-interaction.md): 入力として視線追跡を使用することを計画するときの設計上の考慮事項と推奨事項。</span><span class="sxs-lookup"><span data-stu-id="2130a-144">[Eye-gaze interaction](eye-gaze-interaction.md): Design considerations and recommendations when planning to use eye tracking as an input.</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
   <tr>
        <td><span data-ttu-id="2130a-145"><strong>目を見つめたターゲット</strong></span><span class="sxs-lookup"><span data-stu-id="2130a-145"><strong>Eye-gaze targeting</strong></span></span></td>
        <td><span data-ttu-id="2130a-146"><strong>頭の視線入力のターゲット設定</strong></span><span class="sxs-lookup"><span data-stu-id="2130a-146"><strong>Head-gaze targeting</strong></span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2130a-147">より!</span><span class="sxs-lookup"><span data-stu-id="2130a-147">Fast!</span></span></td>
        <td><span data-ttu-id="2130a-148">かかる</span><span class="sxs-lookup"><span data-stu-id="2130a-148">Slower</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2130a-149">少ない労力 (ほとんどの場合、本文の移動は必要ありません)</span><span class="sxs-lookup"><span data-stu-id="2130a-149">Low effort (barely any body movements necessary)</span></span></td>
        <td><span data-ttu-id="2130a-150">Fatiguing 可能な不快感にすることができます (たとえば、ネック歪み)</span><span class="sxs-lookup"><span data-stu-id="2130a-150">Can be fatiguing - Possible discomfort (for example, neck strain)</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2130a-151">カーソルは必要ありませんが、微妙なフィードバックが推奨されます</span><span class="sxs-lookup"><span data-stu-id="2130a-151">Doesn't require a cursor, but subtle feedback is recommended</span></span></td>
        <td><span data-ttu-id="2130a-152">カーソルを表示する必要があります</span><span class="sxs-lookup"><span data-stu-id="2130a-152">Requires to show a cursor</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2130a-153">Smooth 視線 (たとえば、描画には適していません)</span><span class="sxs-lookup"><span data-stu-id="2130a-153">No smooth eye movements – for example, not good for drawing</span></span></td>
        <td><span data-ttu-id="2130a-154">より詳細な制御と明示</span><span class="sxs-lookup"><span data-stu-id="2130a-154">More controlled and explicit</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2130a-155">小さいターゲットでは難しい (小さいボタンや web リンクなど)</span><span class="sxs-lookup"><span data-stu-id="2130a-155">Difficult for small targets (for example, tiny buttons or weblinks)</span></span></td>
        <td><span data-ttu-id="2130a-156">信頼性!</span><span class="sxs-lookup"><span data-stu-id="2130a-156">Reliable!</span></span> <span data-ttu-id="2130a-157">優れたフォールバック</span><span class="sxs-lookup"><span data-stu-id="2130a-157">Great fallback!</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="2130a-158">...</span><span class="sxs-lookup"><span data-stu-id="2130a-158">...</span></span></td>
        <td><span data-ttu-id="2130a-159">...</span><span class="sxs-lookup"><span data-stu-id="2130a-159">...</span></span></td>
    </tr>
</table>

<span data-ttu-id="2130a-160">宝石とコミットの入力モデルに対して、頭を見つめているか、または目を見つめているかにかかわらず、それぞれに異なる設計制約が用意されています。</span><span class="sxs-lookup"><span data-stu-id="2130a-160">Whether you use head-gaze or eye-gaze for your gaze-and-commit input model, each comes with different sets of design constraints.</span></span> <span data-ttu-id="2130a-161">これらについては、「 [視線とコミット](gaze-and-commit-eyes.md) 」と「 [ヘッドとコミット](gaze-and-commit-head.md) 」の記事で個別に説明されています。</span><span class="sxs-lookup"><span data-stu-id="2130a-161">These are covered separately in the [eye-gaze and commit](gaze-and-commit-eyes.md) and [head-gaze and commit](gaze-and-commit-head.md) articles.</span></span>

<br>

---

### <a name="cursor"></a><span data-ttu-id="2130a-162">カーソル</span><span class="sxs-lookup"><span data-stu-id="2130a-162">Cursor</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="2130a-163">ヘッドを見つめする場合、ほとんどのアプリは [カーソル](cursors.md) またはその他の聴覚/視覚表示を使用して、ユーザーが操作しようとしている内容に自信を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2130a-163">For head gaze, most apps should use a [cursor](cursors.md) or other auditory/visual indication to give the user confidence in what they're about to interact with.</span></span> <span data-ttu-id="2130a-164">通常、このカーソルを世界中に配置して、頭の中線が1つ目のオブジェクトと交差するようにします。これは、ホログラムや実際の表面です。</span><span class="sxs-lookup"><span data-stu-id="2130a-164">You typically position this cursor in the world where their head gaze ray first intersects an object, which may be a hologram or a real-world surface.</span></span><br>
        <br>
        <span data-ttu-id="2130a-165">目を見つめて、通常はカーソルを表示し *ない* ことをお勧めします。これは、ユーザーにとって煩雑で面倒になるためです。</span><span class="sxs-lookup"><span data-stu-id="2130a-165">For eye gaze, we generally recommend *not* to show a cursor, as this can quickly become distracting and annoying for the user.</span></span> <span data-ttu-id="2130a-166">代わりに、視覚的なターゲットを微妙に強調表示するか、目に見えるカーソルを使用して、ユーザーが操作しようとしている内容について自信を持っています。</span><span class="sxs-lookup"><span data-stu-id="2130a-166">Instead subtly highlight visual targets or use a faint eye cursor to provide confidence about what the user is about to interact with.</span></span> <span data-ttu-id="2130a-167">詳細については、HoloLens 2 での [目に基づく入力の設計ガイダンスを](eye-tracking.md) 参照してください。</span><span class="sxs-lookup"><span data-stu-id="2130a-167">For more information, please check out our [design guidance for eye-based input](eye-tracking.md) on HoloLens 2.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="2130a-168">![宝石を示すビジュアルカーソルの例](images/cursor.jpg)</span><span class="sxs-lookup"><span data-stu-id="2130a-168">![An example visual cursor to show gaze](images/cursor.jpg)</span></span><br>
       <span data-ttu-id="2130a-169">*Image: 宝石を示すビジュアルカーソルの例*</span><span class="sxs-lookup"><span data-stu-id="2130a-169">*Image: An example visual cursor to show gaze*</span></span>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="commit"></a><span data-ttu-id="2130a-170">Commit</span><span class="sxs-lookup"><span data-stu-id="2130a-170">Commit</span></span>
<span data-ttu-id="2130a-171">ターゲットを _見つめ_ たさまざまな方法について説明した後、「_宝石とコミットメント_」の _コミット_ 部分についてもう少し詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="2130a-171">After talking about different ways to _gaze_ at a target, let's talk a bit more about the _commit_ part in _gaze and commit_.</span></span>
<span data-ttu-id="2130a-172">オブジェクトまたは UI 要素をターゲットにした後、ユーザーは2次入力を使用して操作またはクリックできます。</span><span class="sxs-lookup"><span data-stu-id="2130a-172">After targeting an object or UI element, the user can interact or click on it using a secondary input.</span></span> <span data-ttu-id="2130a-173">これは、入力モデルのコミット ステップと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2130a-173">This is known as the commit step of the input model.</span></span> 

<span data-ttu-id="2130a-174">以下のコミット方法がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2130a-174">The following commit methods are supported:</span></span>
- <span data-ttu-id="2130a-175">エアタップハンドジェスチャ (つまり、自分の正面に手を付けて、インデックスの指とつまみをまとめる)</span><span class="sxs-lookup"><span data-stu-id="2130a-175">Air tap hand gesture (that is, raise your hand in front of you and bring together your index finger and thumb)</span></span>
- <span data-ttu-id="2130a-176">_"選択"_ または対象となる音声コマンドの1つを言います。</span><span class="sxs-lookup"><span data-stu-id="2130a-176">Say _"select"_ or one of the targeted voice commands</span></span>
- <span data-ttu-id="2130a-177">[HoloLens Clicker](/hololens/hololens1-clicker)で1つのボタンを押す</span><span class="sxs-lookup"><span data-stu-id="2130a-177">Press a single button on a [HoloLens Clicker](/hololens/hololens1-clicker)</span></span>
- <span data-ttu-id="2130a-178">Xbox ゲームパッドで [A] ボタンを押す</span><span class="sxs-lookup"><span data-stu-id="2130a-178">Press the 'A' button on an Xbox gamepad</span></span>
- <span data-ttu-id="2130a-179">Xbox adaptive コントローラーで [A] ボタンを押す</span><span class="sxs-lookup"><span data-stu-id="2130a-179">Press the 'A' button on an Xbox adaptive controller</span></span>

### <a name="gaze-and-air-tap-gesture"></a><span data-ttu-id="2130a-180">宝石とエアタップのジェスチャ</span><span class="sxs-lookup"><span data-stu-id="2130a-180">Gaze and air tap gesture</span></span>
<span data-ttu-id="2130a-181">エアタップは、手をまっすぐにしてタップするジェスチャです。</span><span class="sxs-lookup"><span data-stu-id="2130a-181">Air tap is a tapping gesture with the hand held upright.</span></span> <span data-ttu-id="2130a-182">エアタップを使用するには、インデックスの指を準備完了の位置まで上げて、親指でピンチし、インデックスを作成して、リリースまでさかのぼってください。</span><span class="sxs-lookup"><span data-stu-id="2130a-182">To use an air tap, raise your index finger to the ready position, then pinch with your thumb, and raise your index finger back up to release.</span></span> <span data-ttu-id="2130a-183">HoloLens (第1世代) では、無線タップが最も一般的な2番目の入力です。</span><span class="sxs-lookup"><span data-stu-id="2130a-183">On HoloLens (1st gen), air tap is the most common secondary input.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="2130a-184">![準備完了の位置にある指](images/readyandpress-ready.jpg)</span><span class="sxs-lookup"><span data-stu-id="2130a-184">![Finger in the ready position](images/readyandpress-ready.jpg)</span></span><br>
       <span data-ttu-id="2130a-185">**準備完了の位置にある指**</span><span class="sxs-lookup"><span data-stu-id="2130a-185">**Finger in the ready position**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="2130a-186">![指を押しながらタップまたはクリックします。](images/readyandpress-press.jpg)</span><span class="sxs-lookup"><span data-stu-id="2130a-186">![Press finger down to tap or click](images/readyandpress-press.jpg)</span></span><br>
        <span data-ttu-id="2130a-187">**指を押しながらタップまたはクリックします。**</span><span class="sxs-lookup"><span data-stu-id="2130a-187">**Press finger down to tap or click**</span></span><br>
    :::column-end:::
:::row-end:::


<span data-ttu-id="2130a-188">無線タップは、HoloLens 2 でも使用できます。</span><span class="sxs-lookup"><span data-stu-id="2130a-188">Air tap is also available on HoloLens 2.</span></span> <span data-ttu-id="2130a-189">これは、元のバージョンからは緩和されています。</span><span class="sxs-lookup"><span data-stu-id="2130a-189">It has been relaxed from the original version.</span></span> <span data-ttu-id="2130a-190">ほとんどすべての種類の pinches は、手が垂直で維持されている限り、サポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="2130a-190">Nearly all types of pinches are now supported as long as the hand is upright and holding still.</span></span> <span data-ttu-id="2130a-191">これにより、ユーザーがジェスチャを簡単に習得して使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2130a-191">This makes it much easier for users to learn and use the gesture.</span></span> <span data-ttu-id="2130a-192">この新しいエアタップでは、古いものが同じ API を使用して置き換えられるため、HoloLens 2 の再コンパイル後に既存のアプリケーションの新しい動作が自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="2130a-192">This new air tap replaces the old one through the same API, so existing applications will have the new behavior automatically after recompiling for HoloLens 2.</span></span>

<br>

---

### <a name="gaze-and-select-voice-command"></a><span data-ttu-id="2130a-193">宝石と "選択" 音声コマンド</span><span class="sxs-lookup"><span data-stu-id="2130a-193">Gaze and "Select" voice command</span></span>
<span data-ttu-id="2130a-194">音声コマンド処理は、mixed reality の主要な相互作用メソッドの1つです。</span><span class="sxs-lookup"><span data-stu-id="2130a-194">Voice commanding is one of the primary interaction methods in mixed reality.</span></span> <span data-ttu-id="2130a-195">システムを制御するための強力なハンズフリーのメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="2130a-195">It provides a powerful hands-free mechanism to control the system.</span></span> <span data-ttu-id="2130a-196">ボイス作用モデルには、次のような種類があります。</span><span class="sxs-lookup"><span data-stu-id="2130a-196">There are different types of voice interaction models:</span></span>

- <span data-ttu-id="2130a-197">クリックを使用する汎用の "Select" コマンドは、2番目の入力としてコミットまたはコミットします。</span><span class="sxs-lookup"><span data-stu-id="2130a-197">The generic "Select" command that uses a click actuation or commit as a secondary input.</span></span>
- <span data-ttu-id="2130a-198">オブジェクトコマンド (たとえば、"Close" や "拡大する" など) は、アクションを実行し、セカンダリ入力としてコミットします。</span><span class="sxs-lookup"><span data-stu-id="2130a-198">Object commands (for example, "Close" or "Make it bigger") perform and commit to an action as a secondary input.</span></span>
- <span data-ttu-id="2130a-199">グローバルコマンド (たとえば、[スタート画面に移動]) では、ターゲットは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="2130a-199">Global commands (for example, "Go to start") don't require a target.</span></span>
- <span data-ttu-id="2130a-200">対話ユーザーインターフェイスまたは Cortana のようなエンティティには、AI 自然言語機能があります。</span><span class="sxs-lookup"><span data-stu-id="2130a-200">Conversation user interfaces or entities like Cortana have an AI natural language capability.</span></span>
- <span data-ttu-id="2130a-201">カスタム音声コマンド</span><span class="sxs-lookup"><span data-stu-id="2130a-201">Custom voice commands</span></span>

<span data-ttu-id="2130a-202">詳細と、使用可能な音声コマンドの詳細な一覧と使用方法については、「 [音声](../out-of-scope/voice-design.md) コマンドの操作に関するガイダンス」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2130a-202">To find out more about details and a comprehensive list of available voice commands and how to use them, check out our [voice commanding](../out-of-scope/voice-design.md) guidance.</span></span>

<br>

---


### <a name="gaze-and-hololens-clicker"></a><span data-ttu-id="2130a-203">宝石と HoloLens Clicker</span><span class="sxs-lookup"><span data-stu-id="2130a-203">Gaze and HoloLens Clicker</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="2130a-204">HoloLens Clicker は、HoloLens 専用に構築された最初の周辺機器です。</span><span class="sxs-lookup"><span data-stu-id="2130a-204">The HoloLens Clicker is the first peripheral device built specifically for HoloLens.</span></span> <span data-ttu-id="2130a-205">これは HoloLens (第1世代) Development Edition に含まれています。</span><span class="sxs-lookup"><span data-stu-id="2130a-205">It's included with HoloLens (1st gen) Development Edition.</span></span> <span data-ttu-id="2130a-206">HoloLens Clicker を使用すると、ユーザーは最小限の手でクリックし、2番目の入力としてコミットできます。</span><span class="sxs-lookup"><span data-stu-id="2130a-206">The HoloLens Clicker lets a user click with minimal hand motion, and commit as a secondary input.</span></span> <span data-ttu-id="2130a-207">HoloLens Clicker は、Bluetooth 低エネルギー (BTLE) を使用して HoloLens (第1世代) または HoloLens 2 に接続します。</span><span class="sxs-lookup"><span data-stu-id="2130a-207">The HoloLens Clicker connects to HoloLens (1st gen) or HoloLens 2 using Bluetooth Low Energy (BTLE).</span></span><br>
        <br>
        [<span data-ttu-id="2130a-208">デバイスをペアリングするための詳細情報と手順</span><span class="sxs-lookup"><span data-stu-id="2130a-208">More information and instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="2130a-209">*イメージ: HoloLens Clicker*</span><span class="sxs-lookup"><span data-stu-id="2130a-209">*Image: HoloLens Clicker*</span></span>
    :::column-end:::
        :::column:::
       ![HoloLens クリッカー](images/hololens-clicker-500px.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="gaze-and-xbox-wireless-controller"></a><span data-ttu-id="2130a-211">宝石と Xbox ワイヤレスコントローラー</span><span class="sxs-lookup"><span data-stu-id="2130a-211">Gaze and Xbox Wireless Controller</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="2130a-212">Xbox ワイヤレスコントローラーは、"A" ボタンを使用して、2番目の入力としてクリックを実行します。</span><span class="sxs-lookup"><span data-stu-id="2130a-212">The Xbox Wireless Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="2130a-213">デバイスは、システムの移動と制御に役立つ既定のアクションセットにマップされます。</span><span class="sxs-lookup"><span data-stu-id="2130a-213">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="2130a-214">コントローラーをカスタマイズする場合は、Xbox アクセサリアプリケーションを使用して、Xbox ワイヤレスコントローラーを構成します。</span><span class="sxs-lookup"><span data-stu-id="2130a-214">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Wireless Controller.</span></span><br>
        <br>
        [<span data-ttu-id="2130a-215">Xbox コントローラーを PC とペアリングする方法</span><span class="sxs-lookup"><span data-stu-id="2130a-215">How to pair an Xbox controller with your PC</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)<br>
        <br>
        <span data-ttu-id="2130a-216">*イメージ: Xbox ワイヤレスコントローラー*</span><span class="sxs-lookup"><span data-stu-id="2130a-216">*Image: Xbox Wireless Controller*</span></span>
    :::column-end:::
        :::column:::
       ![Xbox ワイヤレス コントローラー](images/xboxcontroller.jpg)<br>
    :::column-end:::
:::row-end:::



<br>

---


### <a name="gaze-and-xbox-adaptive-controller"></a><span data-ttu-id="2130a-218">宝石と Xbox Adaptive Controller</span><span class="sxs-lookup"><span data-stu-id="2130a-218">Gaze and Xbox Adaptive Controller</span></span>
<span data-ttu-id="2130a-219">多くの場合、モビリティが制限されたゲーマーのニーズを満たすように設計されています。 Xbox Adaptive Controller はデバイス用の統合されたハブであり、混合の現実によりアクセスしやすくなります。</span><span class="sxs-lookup"><span data-stu-id="2130a-219">Designed primarily to meet the needs of gamers with limited mobility, the Xbox Adaptive Controller is a unified hub for devices that helps make mixed reality more accessible.</span></span>

<span data-ttu-id="2130a-220">Xbox Adaptive Controller は、"A" ボタンを使用して、2番目の入力としてクリックを実行します。</span><span class="sxs-lookup"><span data-stu-id="2130a-220">The Xbox Adaptive Controller performs a click actuation as a secondary input by using the 'A' button.</span></span> <span data-ttu-id="2130a-221">デバイスは、システムの移動と制御に役立つ既定のアクションセットにマップされます。</span><span class="sxs-lookup"><span data-stu-id="2130a-221">The device is mapped to a default set of actions that help navigate and control the system.</span></span> <span data-ttu-id="2130a-222">コントローラーをカスタマイズする場合は、Xbox アクセサリアプリケーションを使用して Xbox Adaptive コントローラーを構成します。</span><span class="sxs-lookup"><span data-stu-id="2130a-222">If you want to customize the controller, use the Xbox Accessories application to configure your Xbox Adaptive Controller.</span></span>

<span data-ttu-id="2130a-223">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span><span class="sxs-lookup"><span data-stu-id="2130a-223">![Xbox Adaptive Controller](images/xbox-adaptive-controller-devices.jpg)</span></span><br>
<span data-ttu-id="2130a-224">*Xbox Adaptive Controller*</span><span class="sxs-lookup"><span data-stu-id="2130a-224">*Xbox Adaptive Controller*</span></span>

<span data-ttu-id="2130a-225">スイッチ、ボタン、マウント、ジョイスティックなどの外部デバイスを接続して、独自のカスタムコントローラーエクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2130a-225">Connect external devices such as switches, buttons, mounts, and joysticks to create a custom controller experience that is uniquely yours.</span></span> <span data-ttu-id="2130a-226">ボタン、サムスティック、およびトリガーの入力は、3.5-mm ジャックと USB ポートを介して接続されている補助デバイスで制御されます。</span><span class="sxs-lookup"><span data-stu-id="2130a-226">Button, thumbstick, and trigger inputs are controlled with assistive devices connected through 3.5-mm jacks and USB ports.</span></span>

<span data-ttu-id="2130a-227">![Xbox Adaptive Controller のポート](images/xbox-adaptive-controller-ports.jpg)</span><span class="sxs-lookup"><span data-stu-id="2130a-227">![Xbox Adaptive Controller ports](images/xbox-adaptive-controller-ports.jpg)</span></span><br>
<span data-ttu-id="2130a-228">*Xbox Adaptive Controller のポート*</span><span class="sxs-lookup"><span data-stu-id="2130a-228">*Xbox Adaptive Controller ports*</span></span>

[<span data-ttu-id="2130a-229">デバイスをペアリングする手順</span><span class="sxs-lookup"><span data-stu-id="2130a-229">Instructions to pair the device</span></span>](../discover/hardware-accessories.md#pairing-bluetooth-accessories)

<span data-ttu-id="2130a-230"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>Xbox のサイトで参照できる詳細情報</a></span><span class="sxs-lookup"><span data-stu-id="2130a-230"><a href=https://www.xbox.com/xbox-one/accessories/controllers/xbox-adaptive-controller>More info available on the Xbox site</a></span></span>

<br>

---

## <a name="composite-gestures"></a><span data-ttu-id="2130a-231">複合ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="2130a-231">Composite gestures</span></span>

### <a name="air-tap"></a><span data-ttu-id="2130a-232">エアタップ</span><span class="sxs-lookup"><span data-stu-id="2130a-232">Air tap</span></span>
<span data-ttu-id="2130a-233">エアタップジェスチャ (およびその他のジェスチャ) は、特定の tap にのみ反応します。</span><span class="sxs-lookup"><span data-stu-id="2130a-233">The air tap gesture (and the other gestures below) reacts only to a specific tap.</span></span> <span data-ttu-id="2130a-234">メニューやつかみなど、他のタップを検出するには、前の「2つの主要なコンポーネントのジェスチャ」セクションで説明されている下位レベルの相互作用をアプリケーションで直接使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2130a-234">To detect other taps, such as Menu or Grasp, your application must directly use the lower-level interactions described in the two key component gestures section above.</span></span>

### <a name="tap-and-hold"></a><span data-ttu-id="2130a-235">タップ アンド ホールド</span><span class="sxs-lookup"><span data-stu-id="2130a-235">Tap and hold</span></span>
<span data-ttu-id="2130a-236">ホールドは、単にエアタップの下向きの指の位置を保持することです。</span><span class="sxs-lookup"><span data-stu-id="2130a-236">Hold is simply maintaining the downward finger position of the air tap.</span></span> <span data-ttu-id="2130a-237">エアタップとホールディングを組み合わせることで、さまざまな複雑な "クリックアンドドラッグ" の相互作用 (オブジェクトをアクティブ化する代わりに、オブジェクトを選択したり、コンテキストメニューを表示するなどの二次的な相互作用を行うなど) を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2130a-237">The combination of air tap and hold allows for various more complex "click and drag" interactions when combined with arm movement such as picking up an object instead of activating it or mousedown secondary interactions such as showing a context menu.</span></span>
<span data-ttu-id="2130a-238">ただし、このジェスチャを設計するときは注意が必要です。拡張ジェスチャでは、ユーザーが自分の手をリラックスする傾向があるためです。</span><span class="sxs-lookup"><span data-stu-id="2130a-238">Caution should be used when designing for this gesture however, as users can be prone to relaxing their hand postures during any extended gesture.</span></span>

### <a name="manipulation"></a><span data-ttu-id="2130a-239">操作</span><span class="sxs-lookup"><span data-stu-id="2130a-239">Manipulation</span></span>
<span data-ttu-id="2130a-240">操作ジェスチャを使用すると、ホログラムがユーザーの手の動きに1:1 を反応させる場合に、ホログラムの移動、サイズ変更、または回転を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="2130a-240">Manipulation gestures can be used to move, resize, or rotate a hologram when you want the hologram to react 1:1 to the user's hand movements.</span></span> <span data-ttu-id="2130a-241">このような 1 対 1 の動きの 1 つの用途は、ユーザーが世界中で絵を描いたりペイントしたりできるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="2130a-241">One use for such 1:1 movements is to let the user draw or paint in the world.</span></span>
<span data-ttu-id="2130a-242">操作のジェスチャの最初のターゲット設定は、視線入力またはポインティングによって行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="2130a-242">The initial targeting for a manipulation gesture should be done by gaze or pointing.</span></span> <span data-ttu-id="2130a-243">タップとホールドが開始されると、オブジェクトの操作は手作業で処理されます。これにより、操作中にユーザーを移動させることができます。</span><span class="sxs-lookup"><span data-stu-id="2130a-243">Once the tap and hold starts, any object manipulation is handled by hand movements, which frees the user to look around while they manipulate.</span></span>

### <a name="navigation"></a><span data-ttu-id="2130a-244">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="2130a-244">Navigation</span></span>
<span data-ttu-id="2130a-245">ナビゲーションのジェスチャは仮想ジョイスティックのように動作し、リング メニューなどの UI ウィジェット内で移動するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="2130a-245">Navigation gestures operate like a virtual joystick, and can be used to navigate UI widgets, such as radial menus.</span></span> <span data-ttu-id="2130a-246">タップ アンド ホールドでジェスチャを始めてから、最初に押したところを中心に、正規化された 3D 立方体の中で手を動かします。</span><span class="sxs-lookup"><span data-stu-id="2130a-246">You tap and hold to start the gesture and then move your hand within a normalized 3D cube, centered around the initial press.</span></span> <span data-ttu-id="2130a-247">X、Y、または Z 軸に沿って、値を-1 から1に移動できます。0は開始点となります。</span><span class="sxs-lookup"><span data-stu-id="2130a-247">You can move your hand along the X, Y, or Z axis from a value of -1 to 1, with 0 being the starting point.</span></span>
<span data-ttu-id="2130a-248">ナビゲーションを使用すると、マウスの中央ボタンをクリックしてからマウスを上下に移動して 2 次元の UI をスクロールするのと同様に、速度ベースの連続したスクロールやズームのジェスチャを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2130a-248">Navigation can be used to build velocity-based continuous scrolling or zooming gestures, similar to scrolling a 2D UI by clicking the middle mouse button and then moving the mouse up and down.</span></span>

<span data-ttu-id="2130a-249">Rails を使用したナビゲーションとは、特定の軸で特定のしきい値に達するまで移動を認識する機能を指します。</span><span class="sxs-lookup"><span data-stu-id="2130a-249">Navigation with rails refers to the ability of recognizing movements in certain axis until a certain threshold is reached on that axis.</span></span> <span data-ttu-id="2130a-250">これは、開発者によってアプリケーションで複数の軸での移動が有効になっている場合にのみ役立ちます。たとえば、アプリケーションが X 軸と Y 軸にわたるナビゲーションジェスチャを認識するように構成されていても、X 軸に rails が指定されている場合などです。</span><span class="sxs-lookup"><span data-stu-id="2130a-250">This is only useful when movement in more than one axis is enabled in an application by the developer, such as if an application is configured to recognize navigation gestures across X, Y axis but also specified X axis with rails.</span></span> <span data-ttu-id="2130a-251">この場合、システムは x 軸上の架空のレール (ガイド) 内にある限り、X 軸を越えた手の移動を認識します。これは、Y 軸でも手動で移動した場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="2130a-251">In this case, the system will recognize hand movements across X axis as long as they remain within an imaginary rails (guide) on the X axis, if hand movement also occurs on the Y axis.</span></span>

<span data-ttu-id="2130a-252">2D のアプリ内では、ユーザーは、アプリ内でスクロール、ズーム、またはドラッグするために、垂直方向のナビゲーション ジェスチャを使用できます。</span><span class="sxs-lookup"><span data-stu-id="2130a-252">Within 2D apps, users can use vertical navigation gestures to scroll, zoom, or drag inside the app.</span></span> <span data-ttu-id="2130a-253">これは、同じ種類のタッチ ジェスチャをシミュレートするために、アプリに仮想の指でのタッチを挿入します。</span><span class="sxs-lookup"><span data-stu-id="2130a-253">This injects virtual finger touches to the app to simulate touch gestures of the same type.</span></span> <span data-ttu-id="2130a-254">ユーザーは、アプリケーションの上部にあるバーのツールを切り替えることによって実行するアクションを選択できます。これを行うには、ボタンを選択するか、[スクロール/ドラッグ/ズーム> ツールを <] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2130a-254">Users can select which of these actions take place by toggling between the tools on the bar above the application, either by selecting the button or saying '<Scroll/Drag/Zoom> Tool'.</span></span>

[<span data-ttu-id="2130a-255">複合ジェスチャに関する詳細情報</span><span class="sxs-lookup"><span data-stu-id="2130a-255">More info on composite gestures</span></span>](gaze-and-commit.md#composite-gestures)

## <a name="gesture-recognizers"></a><span data-ttu-id="2130a-256">ジェスチャ認識エンジン</span><span class="sxs-lookup"><span data-stu-id="2130a-256">Gesture recognizers</span></span>

<span data-ttu-id="2130a-257">ジェスチャ認識を使用する利点の1つは、現在ターゲットとなっているホログラムが受け入れるジェスチャに対してのみジェスチャ認識エンジンを構成できることです。</span><span class="sxs-lookup"><span data-stu-id="2130a-257">One benefit of using gesture recognition is that you can configure a gesture recognizer only for the gestures the currently targeted hologram can accept.</span></span> <span data-ttu-id="2130a-258">プラットフォームは、サポートされている特定のジェスチャを区別するために、必要に応じてあいまいさを解消します。</span><span class="sxs-lookup"><span data-stu-id="2130a-258">The platform only does disambiguation as necessary to distinguish those particular supported gestures.</span></span> <span data-ttu-id="2130a-259">このようにして、エアタップをサポートしているホログラムは、プレスとリリースの間に任意の時間を受け入れることができます。一方、タップとホールドの両方をサポートするホログラムは、ホールド時間のしきい値を超えたときにタップを保留に昇格させることができます。</span><span class="sxs-lookup"><span data-stu-id="2130a-259">In this way, a hologram that just supports air tap can accept any length of time between press and release, while a hologram that supports both tap and hold can promote the tap to a hold after the hold time threshold.</span></span>

## <a name="hand-recognition"></a><span data-ttu-id="2130a-260">手の認識</span><span class="sxs-lookup"><span data-stu-id="2130a-260">Hand recognition</span></span>
<span data-ttu-id="2130a-261">HoloLens は、デバイスで確認できる片手または両手の位置を追跡することで、手のジェスチャを認識します。</span><span class="sxs-lookup"><span data-stu-id="2130a-261">HoloLens recognizes hand gestures by tracking the position of either or both hands that are visible to the device.</span></span> <span data-ttu-id="2130a-262">HoloLens は、手が準備完了状態 (手の甲を自分に向けて人差し指を立てる) または押された状態 (手の甲を自分に向けて人差し指を曲げる) のいずれかの状態のときに、手を認識します。</span><span class="sxs-lookup"><span data-stu-id="2130a-262">HoloLens sees hands when they are in either the ready state (back of the hand facing you with index finger up) or the pressed state (back of the hand facing you with the index finger down).</span></span> <span data-ttu-id="2130a-263">他の人に手を付けると、HoloLens はそれらを無視します。</span><span class="sxs-lookup"><span data-stu-id="2130a-263">When hands are in other poses, HoloLens ignores them.</span></span>
<span data-ttu-id="2130a-264">HoloLens が検出した各ハンドでは、向きと押されていない状態でその位置にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2130a-264">For each hand that HoloLens detects, you can access its position without orientation and its pressed state.</span></span> <span data-ttu-id="2130a-265">手がジェスチャ フレームの端に近づくと、方向ベクトルも表示されます。これをユーザーに示すことで、ユーザーは、どのように手を動かせば、HoloLens が認識できる位置に戻せるかを知ることができます。</span><span class="sxs-lookup"><span data-stu-id="2130a-265">As the hand nears the edge of the gesture frame, you're also provided with a direction vector, which you can show to the user so they know how to move their hand to get it back where HoloLens can see it.</span></span>

## <a name="gesture-frame"></a><span data-ttu-id="2130a-266">ジェスチャ フレーム</span><span class="sxs-lookup"><span data-stu-id="2130a-266">Gesture frame</span></span>
<span data-ttu-id="2130a-267">HoloLens でのジェスチャでは、ジェスチャが検出されたカメラが適切に見える範囲で、ウェストとショルダーの間にジェスチャを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2130a-267">For gestures on HoloLens, the hand must be within a gesture frame, in a range that the gesture-sensing cameras can see appropriately,  from nose to waist and between the shoulders.</span></span> <span data-ttu-id="2130a-268">ユーザーは、正常に動作していて快適にするために、この認識の領域でトレーニングを受ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="2130a-268">Users need to be trained on this area of recognition both for success of action and for their own comfort.</span></span> <span data-ttu-id="2130a-269">多くのユーザーは、最初に、ジェスチャフレームが HoloLens を通じて表示されている必要があります。また、そのアームは、対話するために快適に保持しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="2130a-269">Many users will initially assume that the gesture frame must be within their view through HoloLens, and hold up their arms uncomfortably to interact.</span></span> <span data-ttu-id="2130a-270">HoloLens Clicker を使用する場合、ジェスチャフレーム内にハンドを配置する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2130a-270">When using the HoloLens Clicker, it's not necessary for hands to be within the gesture frame.</span></span>

<span data-ttu-id="2130a-271">特に、連続したジェスチャでは、ユーザーが holographic オブジェクトを移動するときにジェスチャを使用していて、意図した結果が失われるというリスクがあります。</span><span class="sxs-lookup"><span data-stu-id="2130a-271">For continuous gestures in particular, there's some risk of users moving their hands outside of the gesture frame while in mid-gesture when moving a holographic object, for example, and losing their intended outcome.</span></span>

<span data-ttu-id="2130a-272">考慮すべきことが 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="2130a-272">There are three things that you should consider:</span></span>

- <span data-ttu-id="2130a-273">ジェスチャフレームの存在とおおよその境界に関するユーザー教育。</span><span class="sxs-lookup"><span data-stu-id="2130a-273">User education on the gesture frame's existence and approximate boundaries.</span></span> <span data-ttu-id="2130a-274">これは、HoloLens セットアップ中に学習されます。</span><span class="sxs-lookup"><span data-stu-id="2130a-274">This is taught during HoloLens setup.</span></span>

- <span data-ttu-id="2130a-275">アプリケーション内のジェスチャが近づいているか、ジェスチャフレームの境界が失われた場合に、望ましくない結果につながることをユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2130a-275">Notifying users when their gestures are nearing or breaking the gesture frame boundaries within an application to the degree that a lost gesture leads to undesired outcomes.</span></span> <span data-ttu-id="2130a-276">調査には、このような通知システムの主要な品質が示されています。</span><span class="sxs-lookup"><span data-stu-id="2130a-276">Research has shown the key qualities of such a notification system.</span></span> <span data-ttu-id="2130a-277">HoloLens シェルは、この種類の通知の良い例を提供しています。つまり、中央カーソルで、境界の交差が行われている方向を示しています。</span><span class="sxs-lookup"><span data-stu-id="2130a-277">The HoloLens shell provides a good example of this type of notification--visual, on the central cursor, indicating the direction in which boundary crossing is taking place.</span></span>

- <span data-ttu-id="2130a-278">ジェスチャ フレームの境界を越えることによる影響は、最小限に抑える必要があります。</span><span class="sxs-lookup"><span data-stu-id="2130a-278">Consequences of breaking the gesture frame boundaries should be minimized.</span></span> <span data-ttu-id="2130a-279">一般に、これは、ジェスチャの結果を、逆順ではなく境界で停止する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="2130a-279">In general, this means that the outcome of a gesture should be stopped at the boundary, and not reversed.</span></span> <span data-ttu-id="2130a-280">たとえば、ユーザーがある程度の holographic オブジェクトを部屋に移動する場合、ジェスチャフレームが侵害されたときに移動が停止し、開始位置には返されません。</span><span class="sxs-lookup"><span data-stu-id="2130a-280">For example, if a user is moving some holographic object across a room, the movement should stop when the gesture frame is breached, and not returned to the starting point.</span></span> <span data-ttu-id="2130a-281">ユーザーにはいくつかのフラストレーションが生じる可能性がありますが、境界をよりよく理解しておくことが必要であり、すべての目的のアクションを毎回再起動する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2130a-281">The user might experience some frustration, but might more quickly understand the boundaries, and not have to restart their full intended actions each time.</span></span>



## <a name="see-also"></a><span data-ttu-id="2130a-282">関連項目</span><span class="sxs-lookup"><span data-stu-id="2130a-282">See also</span></span>
* [<span data-ttu-id="2130a-283">視線ベースの操作</span><span class="sxs-lookup"><span data-stu-id="2130a-283">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="2130a-284">HoloLens 2 上の視線追跡</span><span class="sxs-lookup"><span data-stu-id="2130a-284">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="2130a-285">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="2130a-285">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="2130a-286">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="2130a-286">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="2130a-287">手 - ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="2130a-287">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="2130a-288">手 - ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="2130a-288">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="2130a-289">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="2130a-289">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="2130a-290">音声入力</span><span class="sxs-lookup"><span data-stu-id="2130a-290">Voice input</span></span>](voice-input.md)