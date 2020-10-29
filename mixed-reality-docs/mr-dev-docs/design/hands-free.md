---
title: ハンズフリー
description: ユーザーが手とコントローラーのインターフェイスで直面する可能性がある問題と、さまざまな方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Mixed Reality、ハンズフリー、宝石、宝石をターゲット、相互作用、設計
ms.openlocfilehash: 47e2bd8fef52a36601d58f321def9c066db259e5
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686882"
---
# <a name="hands-free"></a><span data-ttu-id="4ae1c-104">ハンズフリー</span><span class="sxs-lookup"><span data-stu-id="4ae1c-104">Hands-free</span></span>

## <a name="scenarios"></a><span data-ttu-id="4ae1c-105">シナリオ</span><span class="sxs-lookup"><span data-stu-id="4ae1c-105">Scenarios</span></span>

<span data-ttu-id="4ae1c-106">「 [相互作用モデルの概要](interaction-fundamentals.md)」で説明されているように、ユーザーとその目的を特定したら、作業を遂行するために機能する際に直面する可能性がある環境や状況の課題を自分で確認します。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-106">As outlined in the [interaction model overview](interaction-fundamentals.md), once you have identified your users and their goals, ask yourself what environmental or situational challenges they might face as they work to accomplish their tasks.</span></span> <span data-ttu-id="4ae1c-107">たとえば、多くのユーザーは、実際の目標を達成するためにユーザーを使用する必要があります。また、ユーザーには、ハンズオンベースのインターフェイスとの対話が困難になります。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-107">For example, many users need to use their hands to accomplish their real-world goals, and they will have difficulty interacting with a hands-and-controllers based interface.</span></span> 

<span data-ttu-id="4ae1c-108">いくつかの具体的なシナリオとしては、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-108">Some specific scenarios include:</span></span> 
* <span data-ttu-id="4ae1c-109">ユーザーの手がふさがっているときにタスクを誘導する</span><span class="sxs-lookup"><span data-stu-id="4ae1c-109">Being guided through a task, while the user's hands are busy</span></span>
* <span data-ttu-id="4ae1c-110">ユーザーの手がふさがっているときに資料を参照する</span><span class="sxs-lookup"><span data-stu-id="4ae1c-110">Referencing materials while the user's hands are busy</span></span>
* <span data-ttu-id="4ae1c-111">手の疲労</span><span class="sxs-lookup"><span data-stu-id="4ae1c-111">Hand fatigue</span></span>
* <span data-ttu-id="4ae1c-112">追跡できない手袋</span><span class="sxs-lookup"><span data-stu-id="4ae1c-112">Gloves that can't be tracked</span></span>
* <span data-ttu-id="4ae1c-113">手で何かを運んでいる</span><span class="sxs-lookup"><span data-stu-id="4ae1c-113">Carrying something in their hands</span></span>
* <span data-ttu-id="4ae1c-114">大きな手のジェスチャを実行するためのソーシャル awkwardness</span><span class="sxs-lookup"><span data-stu-id="4ae1c-114">Social awkwardness to perform large hand gestures</span></span>
* <span data-ttu-id="4ae1c-115">狭いスペース</span><span class="sxs-lookup"><span data-stu-id="4ae1c-115">Tight spaces</span></span>


## <a name="hands-free-modalities"></a><span data-ttu-id="4ae1c-116">ハンズフリーの感覚様相</span><span class="sxs-lookup"><span data-stu-id="4ae1c-116">Hands-free modalities</span></span>

### <a name="voice-input"></a>[<span data-ttu-id="4ae1c-117">音声入力</span><span class="sxs-lookup"><span data-stu-id="4ae1c-117">Voice input</span></span>](voice-input.md)

<span data-ttu-id="4ae1c-118">音声を使用してコマンドを実行し、インターフェイスを制御すると、必要に応じて複数の手順を柔軟にスキップするための便利な方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-118">Using your voice to command and control an interface offers a convenient way to operate hands-free and to use shortcuts to flexibly skip multiple steps if desired.</span></span> <span data-ttu-id="4ae1c-119">音声入力を使用すると、ユーザーはボタンの名前を自由に読み取り、アクティブ化することができます _("参照してください" と言います)_ 。また、タスクを実行できるデジタルエージェントと会話します。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-119">With voice input, the user can simply read any button's name out loud to activate it _("see it, say it")_ and converse with a digital agent who can accomplish tasks for you.</span></span>


### <a name="gaze-and-dwell"></a>[<span data-ttu-id="4ae1c-120">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="4ae1c-120">Gaze and dwell</span></span>](gaze-and-dwell.md)

<span data-ttu-id="4ae1c-121">実際には、音声を使用するのは理想的ではなく、可能な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-121">In some hands-free situations, using your voice is not ideal or even possible.</span></span> <span data-ttu-id="4ae1c-122">出荷時の環境、プライバシー、またはソーシャル規範はすべて制約となります。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-122">Loud factory environments, privacy, or social norms can all be constraints.</span></span> <span data-ttu-id="4ae1c-123">ユーザーは、視線 + 熟考モデルを使用することにより、他の入力を必要とせずにアプリを移動することができます。ユーザーは、ターゲットで (ヘッドや目を使用して) 移動を維持して、アクティブ化するために lingers するだけです。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-123">The gaze + dwell model allows the user to navigate an app without any additional input aside from their eye or head gaze: The user simply keeps gazing (with their head or eyes) at the target and lingers there for a moment to activate it.</span></span> <span data-ttu-id="4ae1c-124">見つめ + 熟考の個々の設計上の考慮事項の詳細については、「 [視線 + 熟考](gaze-and-dwell-eyes.md) 」と「 [熟考](gaze-and-dwell-head.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-124">To learn more about the individual design considerations for gaze + dwell, check out [eye-gaze + dwell](gaze-and-dwell-eyes.md) and [head-gaze + dwell](gaze-and-dwell-head.md).</span></span>


## <a name="transitioning-in-and-out-of-hands-free"></a><span data-ttu-id="4ae1c-125">ハンドフリーに移行する</span><span class="sxs-lookup"><span data-stu-id="4ae1c-125">Transitioning in and out of hands-free</span></span>

<span data-ttu-id="4ae1c-126">これらのシナリオでは、コマンドの実行とナビゲーションのために、ホログラムを使用してハンドを解放する必要があります。これは、アプリケーションをエンドツーエンドで操作するための絶対的な要件であり、ユーザーがいつでも切り替えることができるようにするための追加の便宜です。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-126">For these scenarios, freeing your hands from interacting with holograms for commanding and navigation can range from being an absolute requirement to operating the application, end-to-end, to an added convenience that the user can transition in and out of at any time.</span></span> 

<span data-ttu-id="4ae1c-127">アプリケーションの要件が常にハンズフリーで、熟考、カスタム音声コマンド、または単一の音声コマンドを使用しているかどうかにかかわらず、"select" を使用する場合は、必ず適切なものを UI に作成してください。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-127">If the requirement of the application is that it will always be used hands-free, whether by using dwell, custom voice commands, or the single voice command, "select", then make sure to make the appropriate accommodations in your UI.</span></span> 

<span data-ttu-id="4ae1c-128">対象ユーザーが自由に自由に切り替えられるようにする必要がある場合は、次の原則を考慮することが重要です。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-128">If your target user needs to be able to switch from hands to hands-free at their discretion, then it is important to take the following principles into account.</span></span>

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a><span data-ttu-id="4ae1c-129">ユーザーが既に切り替え先のモードになっているとします。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-129">Assume the user is already in the mode that they want to switch to</span></span>
<span data-ttu-id="4ae1c-130">たとえば、ユーザーが工場出荷時にビデオ参照を監視していて、ユーザーが自分の HoloLens でビデオ参照を見ていて、レンチを使用して作業を開始した場合、ほとんどの場合、ボタンを押すためにレンチを押す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-130">For instance, if the user is on the factory floor, watching a video reference on her HoloLens, and decides to pick up a wrench to start working, she most likely would start working in hands-free without having to put down the wrench to press a button.</span></span> <span data-ttu-id="4ae1c-131">彼女は、音声コマンドを使用して音声セッションを呼び出し、熟考を開始するために既に表示されている UI で熟考、"select" という単語を言い出すことができるはずです。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-131">She should be able to invoke a voice session with a voice command, dwell on an already-visible UI to begin dwell, or say the word "select".</span></span>

<span data-ttu-id="4ae1c-132">ユーザーは次のことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-132">The user should have the ability to:</span></span> 
* <span data-ttu-id="4ae1c-133">ハンズフリーのまま、ハンドフリーに切り替える</span><span class="sxs-lookup"><span data-stu-id="4ae1c-133">Switch to hands-free while hands-free</span></span>
* <span data-ttu-id="4ae1c-134">手で手に切り替える</span><span class="sxs-lookup"><span data-stu-id="4ae1c-134">Switch to hands with your hands</span></span>
* <span data-ttu-id="4ae1c-135">コントローラーを使用してコントローラーに切り替える</span><span class="sxs-lookup"><span data-stu-id="4ae1c-135">Switch to the controller using a controller</span></span> 

### <a name="create-redundant-ways-to-switch-modes"></a><span data-ttu-id="4ae1c-136">モードを切り替えるための冗長な方法を作成する</span><span class="sxs-lookup"><span data-stu-id="4ae1c-136">Create redundant ways to switch modes</span></span>
<span data-ttu-id="4ae1c-137">最初の原則はアクセスに関するものですが、2番目の原則は可用性です。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-137">While the first principle is about access, the second one is about availability.</span></span> <span data-ttu-id="4ae1c-138">モードを切り替える方法は1つだけではありません。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-138">There should not just be a single way to transition in and out of a mode.</span></span> 

<span data-ttu-id="4ae1c-139">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-139">Some examples would be:</span></span> 
* <span data-ttu-id="4ae1c-140">音声操作を開始するボタン</span><span class="sxs-lookup"><span data-stu-id="4ae1c-140">A button to begin voice interactions</span></span>
* <span data-ttu-id="4ae1c-141">ヘッド宝石と熟考を使用してに移行するための音声コマンド</span><span class="sxs-lookup"><span data-stu-id="4ae1c-141">A voice command to transition to, using head-gaze and dwell</span></span>

### <a name="add-a-dash-of-drama"></a><span data-ttu-id="4ae1c-142">ドラマのダッシュを追加する</span><span class="sxs-lookup"><span data-stu-id="4ae1c-142">Add a dash of drama</span></span>
<span data-ttu-id="4ae1c-143">モードの切り替えは非常に重要です。このような切り替えが行われたときに、ユーザーが何が起こったかをユーザーに知らせるために、これらの遷移が明示的であっても、劇的なスイッチであることが重要です。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-143">A mode switch is a big deal--it is important that when these transitions happen that they be an explicit, even a dramatic switch, to let the user know what happened.</span></span> 


## <a name="usability-checklist"></a><span data-ttu-id="4ae1c-144">使いやすさのチェックリスト</span><span class="sxs-lookup"><span data-stu-id="4ae1c-144">Usability checklist</span></span>

<span data-ttu-id="4ae1c-145">**エンドツーエンドであらゆることをユーザーが自由に実行できますか。**</span><span class="sxs-lookup"><span data-stu-id="4ae1c-145">**Can the user do everything and anything hands-free, end-to-end?**</span></span>
* <span data-ttu-id="4ae1c-146">すべての対話型に自由にアクセスできます</span><span class="sxs-lookup"><span data-stu-id="4ae1c-146">Every interactable should be accessible hands-free</span></span>
* <span data-ttu-id="4ae1c-147">サイズ変更、配置、スワイプ、タップなどのすべてのカスタムジェスチャに代わるものがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-147">Ensure that there is a replacement for all custom gestures, such as resizing, placing, swipes, taps, etc.</span></span>
* <span data-ttu-id="4ae1c-148">UI のプレゼンス、配置、および詳細度を常にユーザーが確実に制御できるようにする</span><span class="sxs-lookup"><span data-stu-id="4ae1c-148">Ensure that the user has confident control of UI presence, placement, and verbosity at all times</span></span>
    * <span data-ttu-id="4ae1c-149">UI の取得方法</span><span class="sxs-lookup"><span data-stu-id="4ae1c-149">Getting UI out of the way</span></span>
    * <span data-ttu-id="4ae1c-150">ビューの外にある UI のアドレス指定 (視界)</span><span class="sxs-lookup"><span data-stu-id="4ae1c-150">Addressing UI that is out of field of view (FOV)</span></span>
    * <span data-ttu-id="4ae1c-151">表示する量 (</span><span class="sxs-lookup"><span data-stu-id="4ae1c-151">How much I see, where, when</span></span>

<span data-ttu-id="4ae1c-152">**相互作用のしくみは、適切な affordances を使用して学習し、補強するのでしょうか。**</span><span class="sxs-lookup"><span data-stu-id="4ae1c-152">**Are the mechanics of the interaction being taught and reinforced with the right affordances?**</span></span>

<span data-ttu-id="4ae1c-153">ユーザーが理解している...</span><span class="sxs-lookup"><span data-stu-id="4ae1c-153">Does the user understand ...</span></span>
* <span data-ttu-id="4ae1c-154">...どのモードであるか。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-154">... What mode they are in?</span></span>
* <span data-ttu-id="4ae1c-155">...このモードでできること</span><span class="sxs-lookup"><span data-stu-id="4ae1c-155">... What they can do in this mode?</span></span>
* <span data-ttu-id="4ae1c-156">...現在の状態を確認できます。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-156">... What is the current state?</span></span>
* <span data-ttu-id="4ae1c-157">...どのように移行できますか。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-157">... How they can transition out?</span></span>
    
<span data-ttu-id="4ae1c-158">**UI はハンドフリーに最適化されていますか。**</span><span class="sxs-lookup"><span data-stu-id="4ae1c-158">**Is the UI optimized for hands-free?**</span></span>   

* <span data-ttu-id="4ae1c-159">例: 熟考 affordances は、一般的な2D パターンに組み込まれていません。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-159">Example: Dwell affordances are not built-in to typical 2D patterns</span></span>
* <span data-ttu-id="4ae1c-160">例: オブジェクトの強調表示を使用すると、音声を対象にすることが適切です。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-160">Example: Voice targeting is better with object highlighting</span></span>
* <span data-ttu-id="4ae1c-161">例: 音声通話は、有効にする必要があるキャプションに適しています。</span><span class="sxs-lookup"><span data-stu-id="4ae1c-161">Example: Voice interactions are better with captions that need to be turned on</span></span>


## <a name="see-also"></a><span data-ttu-id="4ae1c-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ae1c-162">See also</span></span>
* [<span data-ttu-id="4ae1c-163">HoloLens 2 上の視線追跡</span><span class="sxs-lookup"><span data-stu-id="4ae1c-163">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="4ae1c-164">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="4ae1c-164">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="4ae1c-165">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="4ae1c-165">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="4ae1c-166">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="4ae1c-166">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="4ae1c-167">手 - ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="4ae1c-167">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="4ae1c-168">手 - ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="4ae1c-168">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="4ae1c-169">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="4ae1c-169">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="4ae1c-170">音声入力</span><span class="sxs-lookup"><span data-stu-id="4ae1c-170">Voice input</span></span>](voice-input.md)
