---
title: 頭の視線入力とドウェル
description: 頭の視線入力とドウェル入力モデルの概要
author: hferrone
ms.author: v-hferrone
ms.date: 05/13/2019
ms.topic: article
keywords: Mixed Reality、視線入力、ドウェル、操作、デザイン
ms.openlocfilehash: 825623b00107eec400b4df926c8980c92b065902
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687010"
---
# <a name="head-gaze-and-dwell"></a><span data-ttu-id="3a6f5-104">頭の視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="3a6f5-104">Head-gaze and dwell</span></span>

<span data-ttu-id="3a6f5-105">工具や部品で手がふさがっていると、ジェスチャは面倒であったりできなかったりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span> <span data-ttu-id="3a6f5-106">ジェスチャなど音声コマンドは、たとえばかなり騒々しい状況では、信頼性が低い場合があります。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-106">Voice commands, like gestures, can be unreliable in certain contexts, for example under excessively loud conditions.</span></span> <span data-ttu-id="3a6f5-107">さらに、音声でコンピューターを制御するのは万国共通ではありませんが、間違いなく勢いを増しています。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-107">Additionally, using voice to control computers isn't universally common, but it certainly is gaining steam!</span></span> <span data-ttu-id="3a6f5-108">頭の視線入力とドウェルは、HoloLens でヘッドアップとハンズフリーを機能させるための最も使い慣れたマスターしやすいメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-108">Head-gaze and dwell offers the most familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span> <span data-ttu-id="3a6f5-109">さらに、頭の視線入力のドウェルは操作環境の雑音障害や無音の制約に左右されず、100% 信頼できます。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-109">Additionally, head-gaze and dwell is 100% reliable independent of noise interference nor silence constraints in the operating environment.</span></span>

## <a name="scenarios"></a><span data-ttu-id="3a6f5-110">シナリオ</span><span class="sxs-lookup"><span data-stu-id="3a6f5-110">Scenarios</span></span>

<span data-ttu-id="3a6f5-111">頭を見つめて熟考は、人が他の仕事をしていて、声が 100% reliable ていない場合や、環境やソーシャルの制約のために利用できない場合に威力を持っています。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-111">Head-gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span> <span data-ttu-id="3a6f5-112">良い例は、車のエンジンの修理中に参考情報をオーバーレイするために HoloLens を付けている人です。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span> <span data-ttu-id="3a6f5-113">その人がエンジンルームに身を乗り出すとき、その手は工具でふさがっているか体を支えています。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span> <span data-ttu-id="3a6f5-114">ガレージのスペースは絶えず工具を打ちつける音やブーンという音がして騒々しいため、音声コマンドを使うのは困難です。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span> <span data-ttu-id="3a6f5-115">熟考を使用すると、HoloLens を使用するユーザーは、ワークフローを中断することなく、参照資料を自信を持ってナビゲートできます。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-115">Head-gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span> 

## <a name="device-support"></a><span data-ttu-id="3a6f5-116">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="3a6f5-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="3a6f5-117"><strong>入力モデル</strong></span><span class="sxs-lookup"><span data-stu-id="3a6f5-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="3a6f5-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="3a6f5-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="3a6f5-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="3a6f5-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="3a6f5-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="3a6f5-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="3a6f5-121">頭の視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="3a6f5-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="3a6f5-122">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="3a6f5-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="3a6f5-123">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="3a6f5-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="3a6f5-124">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="3a6f5-124">✔️ Recommended</span></span></td>
    </tr>
</table>


## <a name="design-principles"></a><span data-ttu-id="3a6f5-125">設計原則</span><span class="sxs-lookup"><span data-stu-id="3a6f5-125">Design principles</span></span>

<span data-ttu-id="3a6f5-126">**[武器としての視線入力] を回避する**</span><span class="sxs-lookup"><span data-stu-id="3a6f5-126">**Avoid "Gaze as a weapon"**</span></span>

<span data-ttu-id="3a6f5-127">頭の視線入力とドウェルでは視覚的なフィードバックが直感的である必要がありますが、フィードバックが多すぎると不安を誘発する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-127">Head-gaze and dwell requires visual feedback to be intuitive, but too much feedback can induce anxiety.</span></span> <span data-ttu-id="3a6f5-128">フィードバックは、ユーザーが何をターゲットにしているのかを知るのに役立ちますが、意図に反してそれを自動的に選択するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-128">The feedback should help a user know what they're targeting, but not auto-select it against their intent.</span></span> <span data-ttu-id="3a6f5-129">テキスト、アイコン、およびラベルを読み取るには、選択する前に情報を取り入れる余裕を人に提供するための、追加の考慮事項が必要です。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-129">Reading text, icons, and labels requires extra consideration to provide a person room to absorb the information before selecting.</span></span>
    
<span data-ttu-id="3a6f5-130">**ゴルディロックス速度を追及する**</span><span class="sxs-lookup"><span data-stu-id="3a6f5-130">**Seek Goldilocks speed**</span></span>
    
<span data-ttu-id="3a6f5-131">ドウェル操作はナビゲーションの影響に基づいて異なるタイマーを持つことができます。より頻繁に使用される機能は一般的に塗りつぶし時間がより速いという利点がありますが、結果として生じる機能が増えると、塗りつぶし時間がより長くなることが利点になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-131">Dwell interactions can have different timers based on impact of navigation - more frequently used functions will generally benefit from faster fill times, while more consequential functions may benefit from longer fill times.</span></span> <span data-ttu-id="3a6f5-132">塗りつぶし効果を使用してこれらのタイマーを表示する場合、塗りつぶしの色のアニメーション曲線は、塗りつぶし時間をより速く感じるという良い影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-132">When using a fill-effect to show these timers, animation curves of the fill color can positively influence a feeling of faster fill times.</span></span> <span data-ttu-id="3a6f5-133">高速/中速/低速の塗りつぶしの速度のオーバーライドからユーザーが決定できるようにすることを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-133">Consideration should be taken to enable user decision from fast/medium/slow fill speed overrides.</span></span>
    
<span data-ttu-id="3a6f5-134">**ヨーヨー効果を使ってはいけないことにする**</span><span class="sxs-lookup"><span data-stu-id="3a6f5-134">**Say no-no to yo-yo effect**</span></span>

<span data-ttu-id="3a6f5-135">ヨーヨー効果は不快な頭の動きのパターンであり、コンテンツと頭の視線入力、およびドウェルのコントロールの配置によって、人が継続的に繰り返し上下を見なければならないときに発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-135">The yo-yo effect is an uncomfortable pattern of head movement that can emerge when the placement of content and head-gaze and dwell controls forces people to constantly look up and down repeatedly.</span></span> <span data-ttu-id="3a6f5-136">たとえば、下部にある [ヘッドを見つめて熟考] ボタンを使用してリストナビゲーションを実行すると、熟考に移動し、結果を検索して、熟考を検索します。この結果として得られるパターンは不快になります。これを回避するには、移動を必要とする中央の場所にナビゲーションコントロールを配置します。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-136">For example, a list nav with the head-gaze and dwell button at the bottom induces a loop of - look down to dwell, look up at results, look down to dwell, etc. This resulting pattern is uncomfortable and should be avoided by placing navigation controls in a centralized location that requires less back-and-forth.</span></span> <span data-ttu-id="3a6f5-137">快適性のためには、ドウェル ボタンをその効果に応じて配置することが重要になります。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-137">Placement of dwell buttons relative to their effects becomes important for comfort.</span></span>

<br>

---


## <a name="ux-guidelines-and-best-practices"></a><span data-ttu-id="3a6f5-138">UX ガイドラインとベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="3a6f5-138">UX Guidelines and best practices</span></span>

### <a name="target-sizes"></a><span data-ttu-id="3a6f5-139">ターゲット サイズ</span><span class="sxs-lookup"><span data-stu-id="3a6f5-139">Target sizes</span></span>
  <span data-ttu-id="3a6f5-140">簡単にアクセスできるようにするには、ヘッドを見つめて熟考のターゲットが十分に大きく、指定された時間にわたってターゲットに1つのヘッド安定を保持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-140">To be easily accessible, head-gaze and dwell targets need to be large enough to comfortably look at, and hold one's head stable on the target for the prescribed time.</span></span> <span data-ttu-id="3a6f5-141">最も快適なエクスペリエンスを実現するには、最小目標サイズを2度にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-141">We recommend a minimum target size of 2 degrees to achieve the most comfortable experience.</span></span> 

### <a name="visual-feedback"></a><span data-ttu-id="3a6f5-142">視覚的なフィードバック</span><span class="sxs-lookup"><span data-stu-id="3a6f5-142">Visual feedback</span></span>

<span data-ttu-id="3a6f5-143">放射状の塗りつぶしを使用してドウェル タイマーを表す場合は、ボタンの中心から開始します。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-143">When using a radial fill to represent the dwell timer, start from the center of button.</span></span> <span data-ttu-id="3a6f5-144">一貫した反応の方が、さまざまなボタンのさまざまな方向よりも混乱が少なくて済みます。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-144">A consistent response is less confusing than all different directions on different buttons.</span></span> 

  * <span data-ttu-id="3a6f5-145">このルールは方向の操作 (上/下/左/右へのナビゲーションなど) では破られることがあります。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-145">This rule can be broken though for directional interactions (e.g., nav up/down/left/right, etc.).</span></span> <span data-ttu-id="3a6f5-146">たとえば、Microsoft Dynamics 365 Guides では、NEXT/BACK を左右の塗りつぶしにするという例外を認めています。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-146">For example, Microsoft Dynamics 365 Guides makes an exception on NEXT/BACK being left right fills.</span></span>
  * <span data-ttu-id="3a6f5-147">ボタンをオフに切り替えるといったシナリオでは、外部からの放射状の塗りつぶしを逆にすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-147">Consider inverting radial fill from outside, for scenarios like toggling a button off.</span></span> <span data-ttu-id="3a6f5-148">ボタンを押すことの反対の感覚は、維持すべき良好な視覚パターンです。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-148">The inverse feeling of pushing a button is a nice visual pattern to maintain.</span></span> 

### <a name="progressive-disclosure"></a><span data-ttu-id="3a6f5-149">段階的表示</span><span class="sxs-lookup"><span data-stu-id="3a6f5-149">Progressive disclosure</span></span>

<span data-ttu-id="3a6f5-150">段階的表示は、操作の各段階で関連性のあるものだけを可能な限り詳細に表示することを意味します。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-150">Progressive disclosure means only showing as much detail as is relevant at each stage of an interaction.</span></span> <span data-ttu-id="3a6f5-151">つまり、ドウェルの場合は、ドウェルのターゲットが強調表示されます (たとえば、リスト コントロールで)。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-151">For dwell, that means the dwell target is revealed on highlight (e.g., in a list control).</span></span>

 ### <a name="oversized-targets"></a><span data-ttu-id="3a6f5-152">サイズ超過のターゲット</span><span class="sxs-lookup"><span data-stu-id="3a6f5-152">Oversized targets</span></span>
<span data-ttu-id="3a6f5-153">ドウェル領域は、Microsoft Dynamics 365 Guides の [戻る] ボタンのように、使いやすくするためにアクティブでないアイコンより大きくすることができます。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-153">Dwell region can be larger than inactive icon to make it easier to use, like the Back button in Microsoft Dynamics 365 Guides.</span></span>

### <a name="prevent-flickering-with-delayed-feedback"></a><span data-ttu-id="3a6f5-154">フィードバックの遅延によるちらつきを防止する</span><span class="sxs-lookup"><span data-stu-id="3a6f5-154">Prevent flickering with delayed feedback</span></span>
<span data-ttu-id="3a6f5-155">視覚的なフィードバックを開始する前に若干の遅延を使用すると、だれかがドウェルのターゲットを横切ったときのちらつきを回避できます。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-155">Use a short delay before starting visual feedback to avoid flickering when someone passes over a dwell target.</span></span>
* <span data-ttu-id="3a6f5-156">頻繁に対話するボタンについては、遅延を短くして、アプリケーションがリアクティブに見えるようにします。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-156">For buttons interacted with frequently, keep the delay very short so the application feels reactive.</span></span>
* <span data-ttu-id="3a6f5-157">頻繁に使用されないボタンの場合は、インターフェイスの twitchy を避けるために、遅延時間が長くなることがあります。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-157">For buttons that are interacted with infrequently, a longer delay can be appropriate to avoid the interface feeling twitchy.</span></span>


<br>

---

## <a name="ui-patterns"></a><span data-ttu-id="3a6f5-158">UI のパターン</span><span class="sxs-lookup"><span data-stu-id="3a6f5-158">UI patterns</span></span>

### <a name="high-frequency-buttons"></a><span data-ttu-id="3a6f5-159">使用頻度の高いボタン</span><span class="sxs-lookup"><span data-stu-id="3a6f5-159">High frequency buttons</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3a6f5-160">高頻度のボタンは、アプリケーション全体で一般的に使用されるボタンです。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-160">High frequency buttons are buttons that are used commonly throughout an application.</span></span> <span data-ttu-id="3a6f5-161">これらの良い例は、Microsoft Dynamics 365 Guides の [次へ] ボタンと [前へ] ボタンです。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-161">A good example of these are the next and back buttons in Microsoft Dynamics 365 Guides.</span></span><br>
        <br>
        <span data-ttu-id="3a6f5-162">**Recommendations (推奨事項)**</span><span class="sxs-lookup"><span data-stu-id="3a6f5-162">**Recommendations**</span></span><br>
  * <span data-ttu-id="3a6f5-163">高頻度のボタンは大規模で、ヘッドを見つめた方が簡単にヒットできるようにする必要があります</span><span class="sxs-lookup"><span data-stu-id="3a6f5-163">High frequency buttons should be large, easier to hit with head-gaze</span></span>
  * <span data-ttu-id="3a6f5-164">人間の負担を避けるために、ほぼ近い高さを維持します。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-164">Stay near eye height to avoid ergonomic straining.</span></span><br>
        <br>
<span data-ttu-id="3a6f5-165">*画像: Microsoft Dynamics 365 ガイド [次へ] ボタン*</span><span class="sxs-lookup"><span data-stu-id="3a6f5-165">*Image: Microsoft Dynamics 365 Guides next button*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 ガイド [次へ] ボタン](images/GuideNextButton.png)<br>
    :::column-end:::
:::row-end:::

<br>

---


### <a name="low-frequency-buttons"></a><span data-ttu-id="3a6f5-167">使用頻度の低いボタン</span><span class="sxs-lookup"><span data-stu-id="3a6f5-167">Low frequency buttons</span></span>
<span data-ttu-id="3a6f5-168">使用頻度の低いボタンは、アプリケーション全体を通してあまり定期的には操作しないボタンです。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-168">Low frequency buttons are buttons that are not interacted with as regularly throughout the application.</span></span> <span data-ttu-id="3a6f5-169">良い例は、設定メニューにアクセスするためのボタンや、すべての作業を消去するためのボタンです。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-169">A good example might be a button to access the settings menu, or a button to clear all work.</span></span>

* <span data-ttu-id="3a6f5-170">誤ってアクティブ化することのないよう、これらのボタンは頻繁な頭の視線入力の経路の邪魔にならないようにしてみてください。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-170">Try to keep these buttons out of the way of frequent head-gaze paths to avoid accidental activation.</span></span> 

<br>

---

### <a name="confirmations"></a><span data-ttu-id="3a6f5-171">確認</span><span class="sxs-lookup"><span data-stu-id="3a6f5-171">Confirmations</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3a6f5-172">料金の請求、作業の削除、長いプロセスの開始のように、アクションに大きな影響がある場合に、人が意図してボタンを選択していることを確認するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-172">When an action has significant impact, like charging money, deleting work, or starting a long process, it is useful to confirm that a person meant to select a button.</span></span><br>
        <br>
        <span data-ttu-id="3a6f5-173">**Recommendations (推奨事項)**</span><span class="sxs-lookup"><span data-stu-id="3a6f5-173">**Recommendations**</span></span><br>
  * <span data-ttu-id="3a6f5-174">メイン ボタンに選択内容を強調表示にして表示してください。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-174">Show selection highlight on main button.</span></span>
  * <span data-ttu-id="3a6f5-175">選択内容の強調表示と同時にドウェルのターゲットを表示してください。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-175">Reveal dwell target at same time as selection highlight.</span></span>
  * <span data-ttu-id="3a6f5-176">セカンダリ ボタンでは、頭の視線入力にドウェルのターゲットを表示してください。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-176">For the secondary button, reveal the dwell target on head-gaze.</span></span><br>
        <br>
<span data-ttu-id="3a6f5-177">*画像: Microsoft Dynamics 365 ガイドの確認ダイアログ*</span><span class="sxs-lookup"><span data-stu-id="3a6f5-177">*Image: Microsoft Dynamics 365 Guides confirmation dialog*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 ガイドの確認ダイアログ](images/GuidesConfirmation.png)<br>
    :::column-end:::
:::row-end:::
        
<br>

---

### <a name="toggle-buttons"></a><span data-ttu-id="3a6f5-179">トグル ボタン</span><span class="sxs-lookup"><span data-stu-id="3a6f5-179">Toggle buttons</span></span>
<span data-ttu-id="3a6f5-180">トグル ボタンを適切に機能させるには、何らかの微妙なロジックが必要です。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-180">Toggle buttons require some nuanced logic to work properly.</span></span> <span data-ttu-id="3a6f5-181">人がトグル ボタンをドウェルしてアクティブにするときは、ボタンから離れてから、戻ってドウェル ロジックを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-181">When a person dwells on a toggle button and actives it, they need to exit the button and then return to restart the dwell logic.</span></span> <span data-ttu-id="3a6f5-182">トグル可能なボタンには、明確にアクティブな状態とアクティブでない状態があることが重要です。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-182">It is important that togglable buttons have a clear active versus inactive state.</span></span> 

<br>

---

### <a name="list-views"></a><span data-ttu-id="3a6f5-183">リスト ビュー</span><span class="sxs-lookup"><span data-stu-id="3a6f5-183">List views</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="3a6f5-184">リストビューでは、熟考入力に特定の課題があります。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-184">List views present a particular challenge for head-gaze and dwell input.</span></span> <span data-ttu-id="3a6f5-185">人がコンテンツに目を通すときに、ドウェルのターゲットの近くでは慎重に操作しなければならないなどと感じなくて済むようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-185">People need to be able to scan the content without feeling like that have to tiptoe around the dwell targets.</span></span><br>
        <br>
<span data-ttu-id="3a6f5-186">**Recommendations (推奨事項)**</span><span class="sxs-lookup"><span data-stu-id="3a6f5-186">**Recommendations**</span></span><br>
  * <span data-ttu-id="3a6f5-187">Gazed 時には行全体を強調表示しますが、特定の熟考ターゲットにヘッドを熟考ない場合は、開始しません。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-187">Have the entire row highlight when head-gazed but doesn’t begin dwell unless head-gaze is on the specific dwell target.</span></span>
  * <span data-ttu-id="3a6f5-188">熟考ターゲットは、行が強調表示されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-188">Only show the dwell target when the row is highlighted to cut down on visual noise.</span></span>
  * <span data-ttu-id="3a6f5-189">熟考ターゲットの位置と明確で一貫性があること。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-189">Be clear and consistent with the position of dwell targets.</span></span>
  * <span data-ttu-id="3a6f5-190">反復的な UI を避けるために、すべての熟考ターゲットを一度に表示しないでください。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-190">Don't show all dwell targets at once to avoid repetitive UI.</span></span>
  * <span data-ttu-id="3a6f5-191">できるだけ頻繁に同じパターンを再利用して、UX の知識を確立します。</span><span class="sxs-lookup"><span data-stu-id="3a6f5-191">Re-use the same pattern as often as possible to establish UX familiarity.</span></span><br>
        <br>
<span data-ttu-id="3a6f5-192">*画像: Microsoft Dynamics 365 ガイド一覧*</span><span class="sxs-lookup"><span data-stu-id="3a6f5-192">*Image: Microsoft Dynamics 365 Guides list*</span></span>
    :::column-end:::
        :::column:::
       ![Microsoft Dynamics 365 ガイドの一覧](images/GuidesListView.png)<br>
    :::column-end:::
:::row-end:::

<br>

---
 
 ## <a name="see-also"></a><span data-ttu-id="3a6f5-194">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a6f5-194">See also</span></span>
* [<span data-ttu-id="3a6f5-195">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="3a6f5-195">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="3a6f5-196">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="3a6f5-196">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="3a6f5-197">手 - ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="3a6f5-197">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="3a6f5-198">手 - ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="3a6f5-198">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="3a6f5-199">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="3a6f5-199">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="3a6f5-200">音声入力</span><span class="sxs-lookup"><span data-stu-id="3a6f5-200">Voice input</span></span>](voice-input.md)
