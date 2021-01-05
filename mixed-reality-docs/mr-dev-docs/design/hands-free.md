---
title: ハンズフリー
description: ユーザーが手とコントローラーのインターフェイスで直面する可能性がある問題と、さまざまな方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality、ハンズフリー、宝石、宝石のターゲット、相互作用、設計、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、音声入力、使いやすさ
ms.openlocfilehash: 2864e58fdd8a29ae8f981b42f50735eb13a50869
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847677"
---
# <a name="hands-free"></a><span data-ttu-id="e4a3c-104">ハンズフリー</span><span class="sxs-lookup"><span data-stu-id="e4a3c-104">Hands-free</span></span>

## <a name="scenarios"></a><span data-ttu-id="e4a3c-105">シナリオ</span><span class="sxs-lookup"><span data-stu-id="e4a3c-105">Scenarios</span></span>

<span data-ttu-id="e4a3c-106">「 [相互作用モデルの概要](interaction-fundamentals.md)」で説明されているように、ユーザーとその目的を特定したら、作業を遂行するために使用される可能性がある環境または状況の課題を自分で確認します。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you've identified your users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="e4a3c-107">たとえば、多くのユーザーは、実際の目標を達成するためにユーザーを使用する必要があります。また、ユーザーには、ハンズオンベースのインターフェイスとの対話が困難になります。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-107">For example, many users need to use their hands to accomplish their real-world goals, and they'll have difficulty interacting with a hands-and-controllers based interface.</span></span>

<span data-ttu-id="e4a3c-108">いくつかの具体的なシナリオとしては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-108">Some specific scenarios include:</span></span> 
* <span data-ttu-id="e4a3c-109">ユーザーの手がふさがっているときにタスクを誘導する</span><span class="sxs-lookup"><span data-stu-id="e4a3c-109">Being guided through a task, while the user's hands are busy</span></span>
* <span data-ttu-id="e4a3c-110">ユーザーの手がふさがっているときに資料を参照する</span><span class="sxs-lookup"><span data-stu-id="e4a3c-110">Referencing materials while the user's hands are busy</span></span>
* <span data-ttu-id="e4a3c-111">手の疲労</span><span class="sxs-lookup"><span data-stu-id="e4a3c-111">Hand fatigue</span></span>
* <span data-ttu-id="e4a3c-112">追跡できない手袋</span><span class="sxs-lookup"><span data-stu-id="e4a3c-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="e4a3c-113">手で何かを運んでいる</span><span class="sxs-lookup"><span data-stu-id="e4a3c-113">Carrying something in their hands</span></span>
* <span data-ttu-id="e4a3c-114">大きな手のジェスチャを使用する場合のソーシャル awkwardness</span><span class="sxs-lookup"><span data-stu-id="e4a3c-114">Social awkwardness when using large hand gestures</span></span>
* <span data-ttu-id="e4a3c-115">狭いスペース</span><span class="sxs-lookup"><span data-stu-id="e4a3c-115">Tight spaces</span></span>

## <a name="hands-free-modalities"></a><span data-ttu-id="e4a3c-116">ハンズフリーの感覚様相</span><span class="sxs-lookup"><span data-stu-id="e4a3c-116">Hands-free modalities</span></span>

### <a name="voice-input"></a>[<span data-ttu-id="e4a3c-117">音声入力</span><span class="sxs-lookup"><span data-stu-id="e4a3c-117">Voice input</span></span>](voice-input.md)

<span data-ttu-id="e4a3c-118">音声を使用してコマンドを実行し、インターフェイスを制御することで、自由に操作したり、必要に応じて複数の手順をスキップするショートカットを使用したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-118">Using your voice to command and control an interface offers a convenient way to operate hands-free and to use shortcuts to skip multiple steps if you want.</span></span> <span data-ttu-id="e4a3c-119">音声入力を使用すると、ユーザーはボタンの名前を自由に読み上げることができます。これをアクティブに _すると、_ タスクを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-119">With voice input, the user can read any button's name out loud to activate it _("see it, say it")_ and converse with a digital agent who can accomplish tasks for you.</span></span>

### <a name="gaze-and-dwell"></a>[<span data-ttu-id="e4a3c-120">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="e4a3c-120">Gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="e4a3c-121">実際には、音声を使用するのは理想的ではなく、可能な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-121">In some hands-free situations, using your voice isn't ideal or even possible.</span></span> <span data-ttu-id="e4a3c-122">出荷時の環境、プライバシー、またはソーシャル規範はすべて制約となります。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-122">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="e4a3c-123">ユーザーは、視線 + 熟考モデルを使用することにより、追加の入力なしでアプリを移動できます。また、ユーザーは、ターゲットで (ヘッドや目を使用して) 移動を維持して、アクティブ化するために lingers するだけです。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-123">The gaze + dwell model allows the user to navigate an app without any extra input aside from their eye or head gaze: The user simply keeps gazing (with their head or eyes) at the target and lingers there for a moment to activate it.</span></span> <span data-ttu-id="e4a3c-124">見つめ + 熟考の個々の設計上の考慮事項の詳細については、「 [視線 + 熟考](gaze-and-dwell-eyes.md) 」と「 [熟考](gaze-and-dwell-head.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-124">To learn more about the individual design considerations for gaze + dwell, check out [eye-gaze + dwell](gaze-and-dwell-eyes.md) and [head-gaze + dwell](gaze-and-dwell-head.md).</span></span>

## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="e4a3c-125">ハンドフリーに移行する</span><span class="sxs-lookup"><span data-stu-id="e4a3c-125">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="e4a3c-126">これらのシナリオでは、コマンドの実行とナビゲーションのために、ホログラムを使用してハンドを解放する必要があります。これは、アプリケーションをエンドツーエンドで操作するための絶対的な要件であり、ユーザーがいつでも切り替えることができるようにするための追加の便宜です。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-126">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="e4a3c-127">アプリケーションで常にハンドフリーで使用する必要がある場合は、熟考、カスタム音声コマンド、または単一の音声コマンドを使用するかどうかにかかわらず、"select" を使用して、UI に適切な設備を作成してください。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-127">If the application requires that it will always be used hands-free, whether by using dwell, custom voice commands, or the single voice command, "select", then make sure to make the appropriate accommodations in your UI.</span></span> 

<span data-ttu-id="e4a3c-128">対象ユーザーが自由にハンドオフに切り替える必要がある場合は、次の原則を考慮することが重要です。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-128">If your target user needs to switch from hands to hands-free at their discretion, then it's important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="e4a3c-129">ユーザーが既に切り替え先のモードになっているとします。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-129">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="e4a3c-130">たとえば、ユーザーが工場出荷時にビデオ参照を監視していて、ユーザーが自分の HoloLens でビデオ参照を見ていて、レンチを使用して作業を開始した場合、ほとんどの場合、ボタンを押すためにレンチを押す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-130">For instance, if the user is on the factory floor, watching a video reference on her HoloLens, and decides to pick up a wrench to start working, she most likely would start working in hands-free without having to put down the wrench to press a button.</span></span> <span data-ttu-id="e4a3c-131">音声コマンドを使用して音声セッションを呼び出したり、熟考を開始するために既に表示されている UI を熟考したり、"select" という単語を言いたりできます。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-131">She can invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="e4a3c-132">ユーザーは次のことができます。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-132">The user can:</span></span> 
* <span data-ttu-id="e4a3c-133">ハンズフリーのまま、ハンドフリーに切り替える</span><span class="sxs-lookup"><span data-stu-id="e4a3c-133">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="e4a3c-134">手で手に切り替える</span><span class="sxs-lookup"><span data-stu-id="e4a3c-134">Switch to hands with your hands</span></span>
* <span data-ttu-id="e4a3c-135">コントローラーを使用してコントローラーに切り替える</span><span class="sxs-lookup"><span data-stu-id="e4a3c-135">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="e4a3c-136">モードを切り替えるための冗長な方法を作成する</span><span class="sxs-lookup"><span data-stu-id="e4a3c-136">Create redundant ways to switch modes</span></span>

<span data-ttu-id="e4a3c-137">最初の原則はアクセスに関するものですが、2番目の原則は可用性です。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-137">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="e4a3c-138">モードを切り替える方法は1つだけではありません。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-138">There shouldn't just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="e4a3c-139">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-139">Some examples would be:</span></span> 
* <span data-ttu-id="e4a3c-140">音声操作を開始するボタン</span><span class="sxs-lookup"><span data-stu-id="e4a3c-140">A button to begin voice interactions</span></span>
* <span data-ttu-id="e4a3c-141">ヘッド宝石と熟考を使用してに移行するための音声コマンド</span><span class="sxs-lookup"><span data-stu-id="e4a3c-141">A voice command to transition to, using head-gaze and dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="e4a3c-142">ドラマのダッシュを追加する</span><span class="sxs-lookup"><span data-stu-id="e4a3c-142">Add a dash of drama</span></span>

<span data-ttu-id="e4a3c-143">モードの切り替えは大きな問題です。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-143">A mode switch is a big deal.</span></span> <span data-ttu-id="e4a3c-144">このような移行によって、ユーザーが何が起こったかをユーザーに知らせることができます。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-144">It's important that when these transitions happen that they be an explicit, even a dramatic switch, to let the user know what happened.</span></span> 

## <a name="usability-checklist"></a><span data-ttu-id="e4a3c-145">使いやすさのチェックリスト</span><span class="sxs-lookup"><span data-stu-id="e4a3c-145">Usability checklist</span></span>

<span data-ttu-id="e4a3c-146">**エンドツーエンドであらゆることをユーザーが自由に実行できますか。**</span><span class="sxs-lookup"><span data-stu-id="e4a3c-146">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="e4a3c-147">すべての対話型に自由にアクセスできます</span><span class="sxs-lookup"><span data-stu-id="e4a3c-147">Every interactable should be accessible hands-free</span></span>
* <span data-ttu-id="e4a3c-148">サイズ変更、配置、スワイプ、タップなどのすべてのカスタムジェスチャに代わるものがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-148">Ensure that there's a replacement for all custom gestures, such as resizing, placing, swipes, taps, and so on.</span></span>
* <span data-ttu-id="e4a3c-149">ユーザーが UI のプレゼンス、配置、および詳細度を確実に制御できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-149">Ensure that the user has confident control of UI presence, placement, and verbosity always</span></span>
    * <span data-ttu-id="e4a3c-150">UI の取得方法</span><span class="sxs-lookup"><span data-stu-id="e4a3c-150">Getting UI out of the way</span></span>
    * <span data-ttu-id="e4a3c-151">ビューの外にある UI のアドレス指定 (視界)</span><span class="sxs-lookup"><span data-stu-id="e4a3c-151">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="e4a3c-152">表示する量 (</span><span class="sxs-lookup"><span data-stu-id="e4a3c-152">How much I see, where, when</span></span>

<span data-ttu-id="e4a3c-153">**相互作用のしくみは、適切な affordances を使用して学習し、補強するのでしょうか。**</span><span class="sxs-lookup"><span data-stu-id="e4a3c-153">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="e4a3c-154">ユーザーが理解している...</span><span class="sxs-lookup"><span data-stu-id="e4a3c-154">Does the user understand ...</span></span>
* <span data-ttu-id="e4a3c-155">...どのモードであるか。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-155">... What mode they are in?</span></span>
* <span data-ttu-id="e4a3c-156">...このモードでできること</span><span class="sxs-lookup"><span data-stu-id="e4a3c-156">... What they can do in this mode?</span></span>
* <span data-ttu-id="e4a3c-157">...現在の状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-157">... What is the current state?</span></span>
* <span data-ttu-id="e4a3c-158">...どのように移行できますか。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-158">... How they can transition out?</span></span>
    
<span data-ttu-id="e4a3c-159">**UI はハンドフリーに最適化されていますか。**</span><span class="sxs-lookup"><span data-stu-id="e4a3c-159">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="e4a3c-160">例: 熟考 affordances は、一般的な2D パターンに組み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-160">Example: Dwell affordances aren't built in to typical 2D patterns</span></span>
* <span data-ttu-id="e4a3c-161">例: オブジェクトの強調表示を使用すると、音声を対象にすることが適切です。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-161">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="e4a3c-162">例: 音声通話は、有効にする必要があるキャプションに適しています。</span><span class="sxs-lookup"><span data-stu-id="e4a3c-162">Example: Voice interactions are better with captions that need to be turned on</span></span>

## <a name="see-also"></a><span data-ttu-id="e4a3c-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4a3c-163">See also</span></span>

* [<span data-ttu-id="e4a3c-164">HoloLens 2 上の視線追跡</span><span class="sxs-lookup"><span data-stu-id="e4a3c-164">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="e4a3c-165">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="e4a3c-165">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="e4a3c-166">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="e4a3c-166">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="e4a3c-167">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="e4a3c-167">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="e4a3c-168">手 - ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="e4a3c-168">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="e4a3c-169">手 - ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="e4a3c-169">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="e4a3c-170">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="e4a3c-170">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="e4a3c-171">音声入力</span><span class="sxs-lookup"><span data-stu-id="e4a3c-171">Voice input</span></span>](voice-input.md)
