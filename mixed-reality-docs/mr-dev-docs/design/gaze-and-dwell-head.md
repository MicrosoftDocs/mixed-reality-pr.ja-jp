---
title: 頭の視線入力とドウェル
description: 一般的なシナリオや設計の原則など、熟考入力モデルの概要について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality、宝石、熟考、対話、設計、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、ux、ガイドライン、リストビュー
ms.openlocfilehash: 2bfd984a466c1ccd3913e889ca57663800f46380
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007082"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="85577-104">頭の視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="85577-104">Head-gaze and dwell</span></span>

<span data-ttu-id="85577-105">工具や部品で手がふさがっていると、ジェスチャは面倒であったりできなかったりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="85577-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="85577-106">ジェスチャなど音声コマンドは、たとえばかなり騒々しい状況では、信頼性が低い場合があります。</span><span class="sxs-lookup"><span data-stu-id="85577-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="85577-107">さらに、音声でコンピューターを制御するのは万国共通ではありませんが、間違いなく勢いを増しています。</span><span class="sxs-lookup"><span data-stu-id="85577-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="85577-108">頭の視線入力とドウェルは、HoloLens でヘッドアップとハンズフリーを機能させるための最も使い慣れたマスターしやすいメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="85577-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="85577-109">さらに、頭の視線入力のドウェルは操作環境の雑音障害や無音の制約に左右されず、100% 信頼できます。</span><span class="sxs-lookup"><span data-stu-id="85577-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="85577-110">シナリオ</span><span class="sxs-lookup"><span data-stu-id="85577-110">Scenarios</span></span>

<span data-ttu-id="85577-111">頭を見つめて熟考は、人の手が他のタスクと共に忙しく使用されるシナリオに適しています。</span><span class="sxs-lookup"><span data-stu-id="85577-111">Head-gaze and dwell is great in scenarios where a person's hands are busy with other tasks.</span></span> <span data-ttu-id="85577-112">また、この機能は、音声が 100% reliable ていない場合や、環境やソーシャルの制約のために利用できない場合にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="85577-112">The feature is also useful when voice isn't 100% reliable or available because of environmental or social constraints.</span></span> <span data-ttu-id="85577-113">良い例は、車のエンジンの修理中に参考情報をオーバーレイするために HoloLens を付けている人です。</span><span class="sxs-lookup"><span data-stu-id="85577-113">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="85577-114">その人がエンジンルームに身を乗り出すとき、その手は工具でふさがっているか体を支えています。</span><span class="sxs-lookup"><span data-stu-id="85577-114">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="85577-115">ガレージのスペースは絶えず工具を打ちつける音やブーンという音がして騒々しいため、音声コマンドを使うのは困難です。</span><span class="sxs-lookup"><span data-stu-id="85577-115">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="85577-116">熟考を使用すると、HoloLens を使用するユーザーは、ワークフローを中断することなく、参照資料を自信を持ってナビゲートできます。</span><span class="sxs-lookup"><span data-stu-id="85577-116">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="85577-117">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="85577-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="85577-118"><strong>入力モデル</strong></span><span class="sxs-lookup"><span data-stu-id="85577-118"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="85577-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="85577-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="85577-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="85577-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="85577-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="85577-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="85577-122">頭の視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="85577-122">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="85577-123">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="85577-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="85577-124">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="85577-124">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="85577-125">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="85577-125">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="85577-126">設計原則</span><span class="sxs-lookup"><span data-stu-id="85577-126">Design principles</span></span>

<span data-ttu-id="85577-127">**[武器としての視線入力] を回避する**</span><span class="sxs-lookup"><span data-stu-id="85577-127">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="85577-128">頭の視線入力とドウェルでは視覚的なフィードバックが直感的である必要がありますが、フィードバックが多すぎると不安を誘発する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="85577-128">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="85577-129">フィードバックは、ユーザーが対象としている内容を把握するのに役立ちますが、目的に対しては自動ではありません。</span><span class="sxs-lookup"><span data-stu-id="85577-129">The feedback should help a user know what they're targeting, but not autoselect it against their intent.</span></span> <span data-ttu-id="85577-130">テキスト、アイコン、およびラベルを読み取っている場合は、選択する前に情報を吸収する時間をユーザーに提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85577-130">When reading text, icons, and labels, you need to provide users time to absorb the information before selecting.</span></span>
    
<span data-ttu-id="85577-131">**ゴルディロックス速度を追及する**</span><span class="sxs-lookup"><span data-stu-id="85577-131">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="85577-132">ドウェル操作はナビゲーションの影響に基づいて異なるタイマーを持つことができます。より頻繁に使用される機能は一般的に塗りつぶし時間がより速いという利点がありますが、結果として生じる機能が増えると、塗りつぶし時間がより長くなることが利点になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="85577-132">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="85577-133">塗りつぶし効果を使用してこれらのタイマーを表示する場合、塗りつぶしの色のアニメーション曲線は、塗りつぶし時間をより速く感じるという良い影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="85577-133">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="85577-134">高速/中速/低速の塗りつぶしの速度のオーバーライドからユーザーが決定できるようにすることを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85577-134">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="85577-135">**ヨーヨー効果を使ってはいけないことにする**</span><span class="sxs-lookup"><span data-stu-id="85577-135">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="85577-136">Yo-yo 効果は、コンテンツの配置と、熟考コントロールによってメンバーが繰り返し検索される場合に発生する不快な移動パターンです。</span><span class="sxs-lookup"><span data-stu-id="85577-136">The yo-yo effect is an uncomfortable head movement pattern that happens when the content placement and head-gaze/dwell controls forces people to look up and down repeatedly.</span></span> <span data-ttu-id="85577-137">たとえば、下部にある [ヘッドを見つめて熟考] ボタンを使用してリストナビゲーションを実行すると、熟考に移動し、結果を検索して、熟考を検索します。</span><span class="sxs-lookup"><span data-stu-id="85577-137">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, and so on.</span></span> <span data-ttu-id="85577-138">結果として得られるパターンは不快になるため、ナビゲーションコントロールは、少なくとも、必要のない中央の場所に配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="85577-138">The resulting pattern is uncomfortable, so we recommend placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="85577-139">効果に基づいて熟考ボタンを配置することは、快適にするために重要になります。</span><span class="sxs-lookup"><span data-stu-id="85577-139">Placement of dwell buttons based on their effects becomes important for comfort.</span></span>
<span data-ttu-id="85577-140">s</span><span class="sxs-lookup"><span data-stu-id="85577-140">s</span></span>
<br>

---

## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="85577-141">UX ガイドラインとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="85577-141">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="85577-142">ターゲット サイズ</span><span class="sxs-lookup"><span data-stu-id="85577-142">Target sizes</span></span>

<span data-ttu-id="85577-143">簡単にアクセスできるようにするには、ヘッドを見つめて熟考のターゲットを十分に大きくし、所定の時間にわたってターゲットに1つのヘッド安定を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85577-143">To be easily accessible, head-gaze and dwell targets need to be large enough to look at comfortably, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="85577-144">最も快適なエクスペリエンスを実現するには、最小目標サイズを2度にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="85577-144">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="85577-145">視覚的なフィードバック</span><span class="sxs-lookup"><span data-stu-id="85577-145">Visual feedback</span></span>

<span data-ttu-id="85577-146">放射状の塗りつぶしを使用してドウェル タイマーを表す場合は、ボタンの中心から開始します。</span><span class="sxs-lookup"><span data-stu-id="85577-146">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="85577-147">一貫した反応の方が、さまざまなボタンのさまざまな方向よりも混乱が少なくて済みます。</span><span class="sxs-lookup"><span data-stu-id="85577-147">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="85577-148">このルールは、方向の相互作用 (たとえば、nav up/down/left/right など) に対しては分割できます。</span><span class="sxs-lookup"><span data-stu-id="85577-148">This rule can be broken though for directional interactions (for example, nav up/down/left/right, and so on).</span></span> <span data-ttu-id="85577-149">たとえば、Microsoft Dynamics 365 Guides では、NEXT/BACK を左右の塗りつぶしにするという例外を認めています。</span><span class="sxs-lookup"><span data-stu-id="85577-149">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="85577-150">ボタンの切り替えなどのシナリオについては、外側から放射状の塗りつぶしを反転することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="85577-150">Consider inverting radial fill from outside, for scenarios like toggling off a button.</span></span> <span data-ttu-id="85577-151">ボタンを押すことの反対の感覚は、維持すべき良好な視覚パターンです。</span><span class="sxs-lookup"><span data-stu-id="85577-151">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="85577-152">段階的表示</span><span class="sxs-lookup"><span data-stu-id="85577-152">Progressive disclosure</span></span>

<span data-ttu-id="85577-153">段階的表示は、操作の各段階で関連性のあるものだけを可能な限り詳細に表示することを意味します。</span><span class="sxs-lookup"><span data-stu-id="85577-153">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="85577-154">熟考の場合、熟考ターゲットは強調表示されます (リストコントロールなど)。</span><span class="sxs-lookup"><span data-stu-id="85577-154">For dwell, that means the dwell target is revealed on highlight (for example, in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="85577-155">サイズ超過のターゲット</span><span class="sxs-lookup"><span data-stu-id="85577-155">Oversized targets</span></span>

<span data-ttu-id="85577-156">ドウェル領域は、Microsoft Dynamics 365 Guides の [戻る] ボタンのように、使いやすくするためにアクティブでないアイコンより大きくすることができます。</span><span class="sxs-lookup"><span data-stu-id="85577-156">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="85577-157">フィードバックの遅延によるちらつきを防止する</span><span class="sxs-lookup"><span data-stu-id="85577-157">Prevent flickering with delayed feedback</span></span>

<span data-ttu-id="85577-158">視覚的なフィードバックを開始する前に若干の遅延を使用すると、だれかがドウェルのターゲットを横切ったときのちらつきを回避できます。</span><span class="sxs-lookup"><span data-stu-id="85577-158">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="85577-159">頻繁に対話するボタンについては、アプリケーションがリアクティブに見えるように遅延を短くしてください。</span><span class="sxs-lookup"><span data-stu-id="85577-159">For buttons interacted with frequently, keep the delay short so the application feels reactive.</span></span>
* <span data-ttu-id="85577-160">頻繁に使用されないボタンの場合は、インターフェイスの twitchy を避けるために、遅延時間が長くなることがあります。</span><span class="sxs-lookup"><span data-stu-id="85577-160">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>

<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="85577-161">UI のパターン</span><span class="sxs-lookup"><span data-stu-id="85577-161">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="85577-162">使用頻度の高いボタン</span><span class="sxs-lookup"><span data-stu-id="85577-162">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="85577-163">高頻度のボタンは、アプリケーション全体で一般的に使用されるボタンです。</span><span class="sxs-lookup"><span data-stu-id="85577-163">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="85577-164">これらの良い例は、Microsoft Dynamics 365 Guides の [次へ] ボタンと [前へ] ボタンです。</span><span class="sxs-lookup"><span data-stu-id="85577-164">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="85577-165">**Recommendations (推奨事項)**</span><span class="sxs-lookup"><span data-stu-id="85577-165">**Recommendations**</span></span><br>
  * <span data-ttu-id="85577-166">高頻度のボタンは大規模で、ヘッドを見つめた方が簡単にヒットできるようにする必要があります</span><span class="sxs-lookup"><span data-stu-id="85577-166">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="85577-167">人間の負担を避けるために、ほぼ近い高さを維持します。</span><span class="sxs-lookup"><span data-stu-id="85577-167">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="85577-168">*画像: Microsoft Dynamics 365 ガイド [次へ] ボタン*</span><span class="sxs-lookup"><span data-stu-id="85577-168">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 ガイド [次へ] ボタン](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="85577-170">使用頻度の低いボタン</span><span class="sxs-lookup"><span data-stu-id="85577-170">Low frequency buttons</span></span>

<span data-ttu-id="85577-171">低頻度のボタンは、アプリケーション全体で定期的に対話していないボタンです。</span><span class="sxs-lookup"><span data-stu-id="85577-171">Low frequency buttons are buttons that aren't interacted with as regularly throughout the application.</span></span> <span data-ttu-id="85577-172">良い例は、設定メニューにアクセスするためのボタンや、すべての作業を消去するためのボタンです。</span><span class="sxs-lookup"><span data-stu-id="85577-172">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="85577-173">誤ってアクティブ化することのないよう、これらのボタンは頻繁な頭の視線入力の経路の邪魔にならないようにしてみてください。</span><span class="sxs-lookup"><span data-stu-id="85577-173">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="85577-174">確認</span><span class="sxs-lookup"><span data-stu-id="85577-174">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="85577-175">操作に大きな影響がある場合 (料金の請求、作業の削除、長いプロセスの開始など)、ユーザーがボタンを選択することを確認すると便利です。</span><span class="sxs-lookup"><span data-stu-id="85577-175">When an action has significant impact, like charging money, deleting work, or starting a long process, it's useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="85577-176">**Recommendations (推奨事項)**</span><span class="sxs-lookup"><span data-stu-id="85577-176">**Recommendations**</span></span><br>
  * <span data-ttu-id="85577-177">メイン ボタンに選択内容を強調表示にして表示してください。</span><span class="sxs-lookup"><span data-stu-id="85577-177">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="85577-178">選択内容の強調表示と同時にドウェルのターゲットを表示してください。</span><span class="sxs-lookup"><span data-stu-id="85577-178">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="85577-179">セカンダリ ボタンでは、頭の視線入力にドウェルのターゲットを表示してください。</span><span class="sxs-lookup"><span data-stu-id="85577-179">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="85577-180">*画像: Microsoft Dynamics 365 ガイドの確認ダイアログ*</span><span class="sxs-lookup"><span data-stu-id="85577-180">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 ガイドの確認ダイアログ](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="85577-182">トグル ボタン</span><span class="sxs-lookup"><span data-stu-id="85577-182">Toggle buttons</span></span>

<span data-ttu-id="85577-183">トグル ボタンを適切に機能させるには、何らかの微妙なロジックが必要です。</span><span class="sxs-lookup"><span data-stu-id="85577-183">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="85577-184">トグルボタンをクリックしてアクティブにすると、ボタンを終了してから、熟考ロジックを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="85577-184">When a person dwells on a toggle button and activates it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="85577-185">Togglable のボタンの状態が "アクティブ" または "非アクティブ" になっていることが重要です。</span><span class="sxs-lookup"><span data-stu-id="85577-185">It's important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="85577-186">リスト ビュー</span><span class="sxs-lookup"><span data-stu-id="85577-186">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="85577-187">リストビューでは、熟考入力に特定の課題があります。</span><span class="sxs-lookup"><span data-stu-id="85577-187">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="85577-188">熟考のターゲットを気にすることなく、コンテンツをスキャンできます。</span><span class="sxs-lookup"><span data-stu-id="85577-188">People can scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="85577-189">**Recommendations (推奨事項)**</span><span class="sxs-lookup"><span data-stu-id="85577-189">**Recommendations**</span></span><br>
  * <span data-ttu-id="85577-190">Gazed 時には行全体を強調表示しますが、特定の熟考ターゲットにヘッドを熟考ない場合は、開始しません。</span><span class="sxs-lookup"><span data-stu-id="85577-190">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="85577-191">熟考ターゲットは、行が強調表示されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="85577-191">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="85577-192">熟考ターゲットの位置と明確で一貫性があること。</span><span class="sxs-lookup"><span data-stu-id="85577-192">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="85577-193">反復的な UI を避けるために、すべての熟考ターゲットを一度に表示しないでください。</span><span class="sxs-lookup"><span data-stu-id="85577-193">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="85577-194">できるだけ頻繁に同じパターンを再利用して、UX の知識を確立します。</span><span class="sxs-lookup"><span data-stu-id="85577-194">Reuse the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="85577-195">*画像: Microsoft Dynamics 365 ガイド一覧*</span><span class="sxs-lookup"><span data-stu-id="85577-195">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 ガイドの一覧](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="85577-197">関連項目</span><span class="sxs-lookup"><span data-stu-id="85577-197">See also</span></span>

* [<span data-ttu-id="85577-198">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="85577-198">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="85577-199">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="85577-199">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="85577-200">手 - ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="85577-200">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="85577-201">手 - ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="85577-201">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="85577-202">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="85577-202">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="85577-203">音声入力</span><span class="sxs-lookup"><span data-stu-id="85577-203">Voice input</span></span>](voice-input.md)
