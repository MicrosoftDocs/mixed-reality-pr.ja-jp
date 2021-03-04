---
title: 音声入力
description: 音声入力は、HoloLens および Windows Mixed Reality イマーシブヘッドセットの中核となる入力です。 音声は、コマンド、ディクテーション、Cortana などに使用できます。
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv, 音声, cortana, 音声, 入力, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット, HoloLens, MRTK, Mixed Reality ツールキット, 宝石
ms.openlocfilehash: cc1ecd7d236748c3c4de77678e6f67c69a2c1af1
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759143"
---
# <a name="voice-input"></a><span data-ttu-id="46afd-105">音声入力</span><span class="sxs-lookup"><span data-stu-id="46afd-105">Voice input</span></span>

![音声入力](images/UX_Hero_VoiceCommand.jpg)

<span data-ttu-id="46afd-107">音声は、HoloLens の主な入力形式の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="46afd-107">Voice is one of the key forms of input on HoloLens.</span></span> <span data-ttu-id="46afd-108">[ハンドジェスチャ](gaze-and-commit.md#composite-gestures)を使用しなくても、ホログラムに直接コマンドを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-108">It allows you to directly command a hologram without having to use [hand gestures](gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="46afd-109">音声入力は、意図を伝える自然な方法として使用できます。</span><span class="sxs-lookup"><span data-stu-id="46afd-109">Voice input can be a natural way to communicate your intent.</span></span> <span data-ttu-id="46afd-110">複雑なインターフェイスを走査するのは、ユーザーが1つのコマンドで入れ子になったメニューを使用できるため、音声は特に便利です。</span><span class="sxs-lookup"><span data-stu-id="46afd-110">Voice is especially good at traversing complex interfaces, because it lets users cut through nested menus with one command.</span></span>

<span data-ttu-id="46afd-111">音声入力は、すべての _ユニバーサル Windows アプリ_ で音声をサポートするのと [同じエンジン](/windows/uwp/design/input/speech-recognition)によって機能します。</span><span class="sxs-lookup"><span data-stu-id="46afd-111">Voice input is powered by the [same engine](/windows/uwp/design/input/speech-recognition) that supports speech in all _Universal Windows Apps_.</span></span> <span data-ttu-id="46afd-112">HoloLens では、音声認識は、デバイス設定で構成されている Windows の表示言語で常に機能します。</span><span class="sxs-lookup"><span data-stu-id="46afd-112">On HoloLens, speech recognition will always function in the Windows display language configured in your device Settings.</span></span> 

<br>

## <a name="voice-and-gaze"></a><span data-ttu-id="46afd-113">音声と宝石</span><span class="sxs-lookup"><span data-stu-id="46afd-113">Voice and gaze</span></span>

<span data-ttu-id="46afd-114">音声コマンドを使用している場合は、"選択" するカーソルがあるかどうか、または目的のアプリケーションにコマンドをチャネル化するかどうかにかかわらず、一般的なターゲット設定の機能があります。</span><span class="sxs-lookup"><span data-stu-id="46afd-114">When you're using voice commands, head or eye gaze is the typical targeting mechanism, whether with a cursor to "select" or to channel your command to an application you're looking at.</span></span> <span data-ttu-id="46afd-115">また、どのカーソルを見つめているかを示すために必要な場合もあります _("参照してください" と言います)_。</span><span class="sxs-lookup"><span data-stu-id="46afd-115">It may not even be required to show any gaze cursor _("see it, say it")_.</span></span> <span data-ttu-id="46afd-116">一部の音声コマンドでは、"スタート画面に移動" や "Cortana のこんにちは" など、ターゲットがまったく必要ありません。</span><span class="sxs-lookup"><span data-stu-id="46afd-116">Some voice commands don't require a target at all, such as "go to start" or "Hey Cortana."</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a><span data-ttu-id="46afd-117">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="46afd-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="46afd-118"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="46afd-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="46afd-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="46afd-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="46afd-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="46afd-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="46afd-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="46afd-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="46afd-122">音声入力</span><span class="sxs-lookup"><span data-stu-id="46afd-122">Voice input</span></span></td>
        <td><span data-ttu-id="46afd-123">✔️</span><span class="sxs-lookup"><span data-stu-id="46afd-123">✔️</span></span></td>
        <td><span data-ttu-id="46afd-124">✔️</span><span class="sxs-lookup"><span data-stu-id="46afd-124">✔️</span></span></td>
        <td><span data-ttu-id="46afd-125">✔️ (マイクを使用)</span><span class="sxs-lookup"><span data-stu-id="46afd-125">✔️ (with microphone)</span></span></td>
    </tr>
</table>

## <a name="the-select-command"></a><span data-ttu-id="46afd-126">"Select" コマンド</span><span class="sxs-lookup"><span data-stu-id="46afd-126">The "select" command</span></span>

<span data-ttu-id="46afd-127">**HoloLens (第 1 世代)**</span><span class="sxs-lookup"><span data-stu-id="46afd-127">**HoloLens (1st gen)**</span></span>

<span data-ttu-id="46afd-128">特に音声サポートをアプリに追加しなくても、ユーザーはシステム音声コマンド "select" を指定するだけで、ホログラムをアクティブにすることができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-128">Even without specifically adding voice support to your app, your users can activate holograms simply by saying the system voice command "select".</span></span> <span data-ttu-id="46afd-129">これは、HoloLens での [エアタップ](gaze-and-commit.md#composite-gestures) と同じように動作します。また、 [hololens clicker](/hololens/hololens1-clicker)の [選択] ボタンを押すか、 [Windows Mixed Reality モーションコントローラー](motion-controllers.md)でトリガーを押します。</span><span class="sxs-lookup"><span data-stu-id="46afd-129">This behaves the same as an [air tap](gaze-and-commit.md#composite-gestures) on HoloLens, pressing the select button on the [HoloLens clicker](/hololens/hololens1-clicker), or pressing the trigger on a [Windows Mixed Reality motion controller](motion-controllers.md).</span></span> <span data-ttu-id="46afd-130">サウンドが聞こえ、[選択] というヒントが確認として表示されます。</span><span class="sxs-lookup"><span data-stu-id="46afd-130">You'll hear a sound and see a tooltip with "select" appear as confirmation.</span></span> <span data-ttu-id="46afd-131">"Select" は、低電力のキーワード検出アルゴリズムによって有効にされます。これは、バッテリ寿命の影響を最小限に抑えていつでも使用できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="46afd-131">"Select" is enabled by a low-power keyword detection algorithm, which means you can say it anytime with minimal battery life impact.</span></span> <span data-ttu-id="46afd-132">自分の手で "選択" することもできます。</span><span class="sxs-lookup"><span data-stu-id="46afd-132">You can even say "select" with your hands at your side.</span></span>

<br>

---

:::row:::
    :::column:::
        <span data-ttu-id="46afd-133">**HoloLens 2**</span><span class="sxs-lookup"><span data-stu-id="46afd-133">**HoloLens 2**</span></span><br><br>
        <span data-ttu-id="46afd-134">HoloLens 2 で "選択" 音声コマンドを使用するには、まず、ポインターとして使用するために、最初に見つめカーソルを立ち上げる必要があります。</span><span class="sxs-lookup"><span data-stu-id="46afd-134">To use the "select" voice command in HoloLens 2, you first need to bring up the gaze cursor to use as a pointer.</span></span> <span data-ttu-id="46afd-135">これを起動するためのコマンドは覚えやすいものです。 "select" と言うだけです。</span><span class="sxs-lookup"><span data-stu-id="46afd-135">The command to bring it up is easy to remember--just say, "select".</span></span><br><br>
        <span data-ttu-id="46afd-136">モードを終了するには、無線タップ、指でのボタンの接近、またはシステムジェスチャの使用によって、もう一度手を使います。</span><span class="sxs-lookup"><span data-stu-id="46afd-136">To exit the mode, use your hands again by air tapping, approaching a button with your fingers, or using the system gesture.</span></span><br>
        <br> 
        <span data-ttu-id="46afd-137">*イメージ: 音声コマンドを選択に使用するには、[選択] を言います。*</span><span class="sxs-lookup"><span data-stu-id="46afd-137">*Image: Say "select" to use the voice command for selection*</span></span>
    :::column-end:::
        :::column:::
       ![ユーザーは、[選択] を選択して、音声コマンドを選択に使用できます。](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a><span data-ttu-id="46afd-139">コルタナさん</span><span class="sxs-lookup"><span data-stu-id="46afd-139">Hey Cortana</span></span>

<span data-ttu-id="46afd-140">Cortana をいつでも表示するには、「Cortana」と言うことができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-140">You can say "Hey Cortana" to bring up Cortana at any time.</span></span> <span data-ttu-id="46afd-141">自分の質問を続けたり、指示を与えたりすることができるようになるまで待つ必要はありません。</span><span class="sxs-lookup"><span data-stu-id="46afd-141">You don't have to wait for her to appear to continue asking her your question or giving her an instruction.</span></span> <span data-ttu-id="46afd-142">たとえば、「Cortana について、どのような天気があるか」と言ってみてください。</span><span class="sxs-lookup"><span data-stu-id="46afd-142">For example, try saying "Hey Cortana, what's the weather?"</span></span> <span data-ttu-id="46afd-143">1つの文として。</span><span class="sxs-lookup"><span data-stu-id="46afd-143">as a single sentence.</span></span> <span data-ttu-id="46afd-144">Cortana とその対処方法の詳細については、こちらをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="46afd-144">For more information about Cortana and what you can do, ask her!</span></span> <span data-ttu-id="46afd-145">「Cortana とはどういうことですか。」と言います。</span><span class="sxs-lookup"><span data-stu-id="46afd-145">Say "Hey Cortana, what can I say?"</span></span> <span data-ttu-id="46afd-146">次に、作業と推奨されるコマンドの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="46afd-146">and she'll pull up a list of working and suggested commands.</span></span> <span data-ttu-id="46afd-147">既に Cortana アプリを使用している場合は、[?] を選択し **ます。**</span><span class="sxs-lookup"><span data-stu-id="46afd-147">If you're already in the Cortana app, select the **?**</span></span> <span data-ttu-id="46afd-148">同じメニューをプルするためのサイドバーのアイコン。</span><span class="sxs-lookup"><span data-stu-id="46afd-148">icon on the sidebar to pull up this same menu.</span></span>

<span data-ttu-id="46afd-149">**HoloLens 固有のコマンド**</span><span class="sxs-lookup"><span data-stu-id="46afd-149">**HoloLens-specific commands**</span></span>
* <span data-ttu-id="46afd-150">音声操作の項目</span><span class="sxs-lookup"><span data-stu-id="46afd-150">"What can I say?"</span></span>
* <span data-ttu-id="46afd-151">[ブルーム](system-gesture.md#bloom)の代わりに [スタート] メニューから [スタート][メニュー](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)に移動する</span><span class="sxs-lookup"><span data-stu-id="46afd-151">"Go to Start" - instead of [bloom](system-gesture.md#bloom) to get to [Start Menu](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)</span></span>
* <span data-ttu-id="46afd-152">"起動 <app> "</span><span class="sxs-lookup"><span data-stu-id="46afd-152">"Launch <app>"</span></span>
* <span data-ttu-id="46afd-153">"ここに移動 <app> "</span><span class="sxs-lookup"><span data-stu-id="46afd-153">"Move <app> here"</span></span>
* <span data-ttu-id="46afd-154">"写真を撮る"</span><span class="sxs-lookup"><span data-stu-id="46afd-154">"Take a picture"</span></span>
* <span data-ttu-id="46afd-155">"記録の開始"</span><span class="sxs-lookup"><span data-stu-id="46afd-155">"Start recording"</span></span>
* <span data-ttu-id="46afd-156">"記録の停止"</span><span class="sxs-lookup"><span data-stu-id="46afd-156">"Stop recording"</span></span>
* <span data-ttu-id="46afd-157">"ハンドレイを表示する"</span><span class="sxs-lookup"><span data-stu-id="46afd-157">"Show hand ray"</span></span>
* <span data-ttu-id="46afd-158">"ハンドレイを隠す"</span><span class="sxs-lookup"><span data-stu-id="46afd-158">"Hide hand ray"</span></span>
* <span data-ttu-id="46afd-159">「明るさを上げる」</span><span class="sxs-lookup"><span data-stu-id="46afd-159">"Increase the brightness"</span></span>
* <span data-ttu-id="46afd-160">「明るさを下げる」</span><span class="sxs-lookup"><span data-stu-id="46afd-160">"Decrease the brightness"</span></span>
* <span data-ttu-id="46afd-161">"ボリュームを増やす"</span><span class="sxs-lookup"><span data-stu-id="46afd-161">"Increase the volume"</span></span>
* <span data-ttu-id="46afd-162">"音量を下げる"</span><span class="sxs-lookup"><span data-stu-id="46afd-162">"Decrease the volume"</span></span>
* <span data-ttu-id="46afd-163">"ミュート" または "ミュート解除"</span><span class="sxs-lookup"><span data-stu-id="46afd-163">"Mute" or "Unmute"</span></span>
* <span data-ttu-id="46afd-164">"デバイスをシャットダウンする"</span><span class="sxs-lookup"><span data-stu-id="46afd-164">"Shut down the device"</span></span>
* <span data-ttu-id="46afd-165">"デバイスを再起動する"</span><span class="sxs-lookup"><span data-stu-id="46afd-165">"Restart the device"</span></span>
* <span data-ttu-id="46afd-166">"スリープ状態に移行"</span><span class="sxs-lookup"><span data-stu-id="46afd-166">"Go to sleep"</span></span>
* <span data-ttu-id="46afd-167">"どのような時間がかかりますか。"</span><span class="sxs-lookup"><span data-stu-id="46afd-167">"What time is it?"</span></span>
* <span data-ttu-id="46afd-168">「どのくらいのバッテリが残っていますか?」</span><span class="sxs-lookup"><span data-stu-id="46afd-168">"How much battery do I have left?"</span></span>

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a><span data-ttu-id="46afd-169">「言ってください。</span><span class="sxs-lookup"><span data-stu-id="46afd-169">"See It, Say It"</span></span><br>
        <span data-ttu-id="46afd-170">HoloLens には、音声入力用の "it it はこれを見る" モデルがあります。ボタンのラベルはユーザーに対して、どのような音声コマンドを伝えることもできます。</span><span class="sxs-lookup"><span data-stu-id="46afd-170">HoloLens has a "see it, say it" model for voice input, where labels on buttons tell users what voice commands they can say as well.</span></span> <span data-ttu-id="46afd-171">たとえば、HoloLens (第1世代) のアプリウィンドウを見ると、ユーザーは "調整" コマンドを使用して世界中のアプリの位置を調整できます。</span><span class="sxs-lookup"><span data-stu-id="46afd-171">For example, when looking at an app window in HoloLens (1st gen), a user can say "Adjust" command to adjust the position of the app in the world.</span></span><br>
        <br>
        <span data-ttu-id="46afd-172">*イメージ: ユーザーは、アプリバーに表示される "調整" コマンドを使用してアプリの位置を調整できます。*</span><span class="sxs-lookup"><span data-stu-id="46afd-172">*Image: A user can say the "Adjust" command, which they see in the App bar to adjust the position of the app*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="46afd-173">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="46afd-173">![space](images/spacer-20x582.png)</span></span><br>
        <span data-ttu-id="46afd-174">![アプリウィンドウまたはホログラムを見ると、ユーザーはアプリバーに表示される "調整" コマンドを使用して、世界中のアプリの位置を調整することができます。](images/microphone-600px.png)</span><span class="sxs-lookup"><span data-stu-id="46afd-174">![When looking at an app window or hologram, a user can say the "Adjust" command which they see in the App bar to adjust the position of the app in the world](images/microphone-600px.png)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="46afd-175">アプリがこの規則に従うと、ユーザーはシステムを制御する方法を簡単に理解できます。</span><span class="sxs-lookup"><span data-stu-id="46afd-175">When apps follow this rule, users can easily understand what to say to control the system.</span></span> <span data-ttu-id="46afd-176">HoloLens のボタン (第1世代) では、"音声熟考" というツールヒントが表示されます。ボタンが音声に対応している場合は、1秒後に表示され、"press" を押すコマンドを表示します。</span><span class="sxs-lookup"><span data-stu-id="46afd-176">While gazing at a button in HoloLens (1st gen), you'll see a "voice dwell" tooltip that comes up after a second if the button is voice-enabled and displays the command to speak to "press" it.</span></span> <span data-ttu-id="46afd-177">HoloLens 2 の音声ツールヒントを表示するには、"選択" または "どのように言ってください" (画像を参照) と言って、音声カーソルを表示します。</span><span class="sxs-lookup"><span data-stu-id="46afd-177">To reveal voice tooltips in HoloLens 2, show the voice cursor by saying "select" or "What can I say" (See image).</span></span> <br>
        <br>
        <span data-ttu-id="46afd-178">*イメージ: ボタンの下にコマンドが表示されます。*</span><span class="sxs-lookup"><span data-stu-id="46afd-178">*Image: "See it, say it" commands appear below the buttons*</span></span>
    :::column-end:::
        :::column:::
       ![ボタンの下にコマンドが表示されるとします。](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a><span data-ttu-id="46afd-180">迅速なホログラム操作のための音声コマンド</span><span class="sxs-lookup"><span data-stu-id="46afd-180">Voice commands for fast hologram manipulation</span></span>

<span data-ttu-id="46afd-181">多くの音声コマンドを使用して、操作タスクを迅速に実行するためにホログラムでの処理を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-181">There are many voice commands you can say while gazing at a hologram to quickly do manipulation tasks.</span></span> <span data-ttu-id="46afd-182">これらの音声コマンドは、世界中に配置したアプリウィンドウと3D オブジェクトに対して機能します。</span><span class="sxs-lookup"><span data-stu-id="46afd-182">These voice commands work on app windows and 3D objects you've placed in the world.</span></span>

<span data-ttu-id="46afd-183">**ホログラム操作コマンド**</span><span class="sxs-lookup"><span data-stu-id="46afd-183">**Hologram manipulation commands**</span></span>
* <span data-ttu-id="46afd-184">顔</span><span class="sxs-lookup"><span data-stu-id="46afd-184">Face me</span></span>
* <span data-ttu-id="46afd-185">大規模 |用</span><span class="sxs-lookup"><span data-stu-id="46afd-185">Bigger | Enhance</span></span>
* <span data-ttu-id="46afd-186">小</span><span class="sxs-lookup"><span data-stu-id="46afd-186">Smaller</span></span>

<span data-ttu-id="46afd-187">HoloLens 2 では、より自然な対話を視線と組み合わせて作成することもできます。これは、参照している内容についてのコンテキスト情報を暗黙的に提供します。</span><span class="sxs-lookup"><span data-stu-id="46afd-187">On HoloLens 2, you can also create more natural interactions in combination with eye-gaze, which implicitly provides contextual information about what you are referring to.</span></span> <span data-ttu-id="46afd-188">たとえば、ホログラムを見て "put _this_" と言い、どこに配置するかを見て、「 _ここ_ で」と言うことができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-188">For example, you could look at a hologram and say "put _this_" and then look over where you want to place it and say "over _here_".</span></span>
<span data-ttu-id="46afd-189">または、複雑なコンピューター上の holographic の部分を見て、「 _これ_ に関する詳細情報を提供する」と言います。</span><span class="sxs-lookup"><span data-stu-id="46afd-189">Or you could look at a holographic part on a complex machine and say: "give me more information about _this_".</span></span>

## <a name="discovering-voice-commands"></a><span data-ttu-id="46afd-190">音声コマンドの検出</span><span class="sxs-lookup"><span data-stu-id="46afd-190">Discovering voice commands</span></span>

<span data-ttu-id="46afd-191">上記の高速操作のコマンドのように、一部のコマンドは非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-191">Some commands, like the commands for fast manipulation above, can be hidden.</span></span> <span data-ttu-id="46afd-192">使用できるコマンドの詳細については、オブジェクトを見つめ、「どうしたら言いますか」と言うことができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-192">To learn about what commands you can use, gaze at an object and say, "what can I say?".</span></span> <span data-ttu-id="46afd-193">使用可能なコマンドの一覧がポップアップ表示されます。</span><span class="sxs-lookup"><span data-stu-id="46afd-193">A list of possible commands pops up.</span></span> <span data-ttu-id="46afd-194">また、頭を見つめたカーソルを使用して、前の各ボタンの音声ツールヒントを見たり、表示したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="46afd-194">You can also use the head gaze cursor to look around and reveal the voice tooltips for each button in front of you.</span></span> 

<span data-ttu-id="46afd-195">完全な一覧が必要な場合は、いつでも [すべてのコマンドを表示] を選択します。</span><span class="sxs-lookup"><span data-stu-id="46afd-195">If you want a complete list, just say, "Show all commands" anytime.</span></span> 

## <a name="dictation"></a><span data-ttu-id="46afd-196">ディクテーション</span><span class="sxs-lookup"><span data-stu-id="46afd-196">Dictation</span></span>

<span data-ttu-id="46afd-197">音声ディクテーションで入力 [するのではなく、アプリケーション](gaze-and-commit.md#composite-gestures)にテキストを入力する方が効率的です。</span><span class="sxs-lookup"><span data-stu-id="46afd-197">Rather than typing with [air taps](gaze-and-commit.md#composite-gestures), voice dictation can be more efficient to enter text into an app.</span></span> <span data-ttu-id="46afd-198">これにより、ユーザーの負担を軽減しながら、入力を大幅に高速化できます。</span><span class="sxs-lookup"><span data-stu-id="46afd-198">This can greatly accelerate input with less effort for the user.</span></span>

<span data-ttu-id="46afd-199">![音声ディクテーションを開始するには、マイクボタンを選択します。](images/micbuttonfordictation.png)</span><span class="sxs-lookup"><span data-stu-id="46afd-199">![Voice dictation starts by selecting the microphone button](images/micbuttonfordictation.png)</span></span><br>
<span data-ttu-id="46afd-200">*音声ディクテーションを開始するには、キーボードのマイクボタンを選択します。*</span><span class="sxs-lookup"><span data-stu-id="46afd-200">*Voice dictation starts by selecting the microphone button on the keyboard*</span></span>

<span data-ttu-id="46afd-201">Holographic キーボードがアクティブなときはいつでも、入力せずにディクテーションモードに切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-201">Anytime the holographic keyboard is active, you can switch to dictation mode instead of typing.</span></span> <span data-ttu-id="46afd-202">開始するには、テキスト入力ボックスの横にあるマイクを選択します。</span><span class="sxs-lookup"><span data-stu-id="46afd-202">Select the microphone on the side of the text input box to get started.</span></span>

## <a name="adding-voice-commands-to-your-app"></a><span data-ttu-id="46afd-203">音声コマンドをアプリに追加する</span><span class="sxs-lookup"><span data-stu-id="46afd-203">Adding voice commands to your app</span></span>

<span data-ttu-id="46afd-204">構築するすべてのエクスペリエンスに対して、音声コマンドを加えることをご検討ください。</span><span class="sxs-lookup"><span data-stu-id="46afd-204">Consider adding voice commands to any experience that you build.</span></span> <span data-ttu-id="46afd-205">音声は、システムとアプリを制御する強力な方法です。</span><span class="sxs-lookup"><span data-stu-id="46afd-205">Voice is a powerful way control the system and apps.</span></span> <span data-ttu-id="46afd-206">ユーザーはさまざまな種類の言語やアクセントを使用するため、音声キーワードを適切に選択することで、ユーザーのコマンドが明確に解釈されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-206">Because users speak with different kinds of dialects and accents, proper choice of speech keywords will make sure your users' commands are interpreted unambiguously.</span></span>

### <a name="best-practices"></a><span data-ttu-id="46afd-207">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="46afd-207">Best practices</span></span>

<span data-ttu-id="46afd-208">スムーズな音声認識に役立ついくつかのプラクティスを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="46afd-208">Below are some practices that will aid in smooth speech recognition.</span></span>
* <span data-ttu-id="46afd-209">**簡潔なコマンドを使用する** - 可能なら 2 音節以上から成るキーワードを選択します。</span><span class="sxs-lookup"><span data-stu-id="46afd-209">**Use concise commands** - When possible, choose keywords of two or more syllables.</span></span> <span data-ttu-id="46afd-210">1 音節の単語は、アクセントが異なる人が読み上げると、別の母音が使用されやすくなります。</span><span class="sxs-lookup"><span data-stu-id="46afd-210">One-syllable words tend to use different vowel sounds when spoken by persons of different accents.</span></span> <span data-ttu-id="46afd-211">例: "ビデオの再生" は、"現在選択されているビデオを再生する" よりも優れています。</span><span class="sxs-lookup"><span data-stu-id="46afd-211">Example: "Play video" is better than "Play the currently selected video"</span></span>
* <span data-ttu-id="46afd-212">**単純な語彙を使用する** -例: "show プラカード" よりも "メモの表示" が適しています。</span><span class="sxs-lookup"><span data-stu-id="46afd-212">**Use simple vocabulary** - Example: "Show note" is better than "Show placard"</span></span>
* <span data-ttu-id="46afd-213">**コマンドが破壊されていないこと** を確認してください。 speech コマンドアクションが破壊的でないことを確認してください。ユーザーが誤ってコマンドをトリガーした場合には、その操作を簡単に元に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-213">**Make sure commands are non-destructive** - Make sure any speech command actions are non-destructive and can easily be undone in case another person speaking near the user accidentally triggers a command.</span></span>
* <span data-ttu-id="46afd-214">**発音が似たコマンドを避ける** -類似している音声コマンドを複数登録しないでください。</span><span class="sxs-lookup"><span data-stu-id="46afd-214">**Avoid similar sounding commands** - Avoid registering multiple speech commands that sound similar.</span></span> <span data-ttu-id="46afd-215">例: "more Show" と "Show store" は、同様の音で表示されます。</span><span class="sxs-lookup"><span data-stu-id="46afd-215">Example: "Show more" and "Show store" can be similar sounding.</span></span>
* <span data-ttu-id="46afd-216">**アプリが使用されていないときにアプリの登録を解除** する-アプリが特定の speech コマンドが有効な状態ではない場合、他のコマンドが混同されないように、アプリの登録を解除することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="46afd-216">**Unregister your app when not it uses** - When your app isn't in a state in which a particular speech command is valid, consider unregistering it so that other commands aren't confused for that one.</span></span>
* <span data-ttu-id="46afd-217">**別のアクセントによるテスト** - 別のアクセントのユーザーによってアプリをテストします。</span><span class="sxs-lookup"><span data-stu-id="46afd-217">**Test with different accents** - Test your app with users of different accents.</span></span>
* <span data-ttu-id="46afd-218">**音声コマンドの一貫性を維持** - 「戻る」で前のページに戻るようになっているなら、ご自分のアプリケーションでもこの動作を維持してください。</span><span class="sxs-lookup"><span data-stu-id="46afd-218">**Maintain voice command consistency** - If "Go back" goes to the previous page, maintain this behavior in your applications.</span></span>
* <span data-ttu-id="46afd-219">**システムコマンドの使用を避ける** -次の音声コマンドはシステム用に予約されているため、アプリケーションでは使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="46afd-219">**Avoid using system commands** - The following voice commands are reserved for the system, so avoid using them in your applications:</span></span>
   * <span data-ttu-id="46afd-220">「コルタナさん」</span><span class="sxs-lookup"><span data-stu-id="46afd-220">"Hey Cortana"</span></span>
   * <span data-ttu-id="46afd-221">「選択」</span><span class="sxs-lookup"><span data-stu-id="46afd-221">"Select"</span></span>
   * <span data-ttu-id="46afd-222">"スタート画面に進む"</span><span class="sxs-lookup"><span data-stu-id="46afd-222">"Go to start"</span></span>

### <a name="advantages-of-voice-input"></a><span data-ttu-id="46afd-223">音声入力の利点</span><span class="sxs-lookup"><span data-stu-id="46afd-223">Advantages of voice input</span></span>

<span data-ttu-id="46afd-224">音声入力は、意図を伝える自然な方法です。</span><span class="sxs-lookup"><span data-stu-id="46afd-224">Voice input is a natural way to communicate our intents.</span></span> <span data-ttu-id="46afd-225">インターフェイスの複数の手順をユーザーが切り取ることができるので、インターフェイス **トラバーサル** では音声が特に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="46afd-225">Voice is especially good at interface **traversals** because it can help users cut through multiple steps of an interface.</span></span> <span data-ttu-id="46afd-226">ユーザーは、アプリの [戻る] ボタンをクリックするのではなく、web ページを見ながら "戻る" ようにすることがあります。</span><span class="sxs-lookup"><span data-stu-id="46afd-226">A user might say "go back" while looking at a webpage, instead of having to go up and hit the back button in the app.</span></span> <span data-ttu-id="46afd-227">この小さな節約には、ユーザーによるエクスペリエンスの認識に対する大きな **影響** があるため、少量のスーパーパワーが得られます。</span><span class="sxs-lookup"><span data-stu-id="46afd-227">This small time saving has a powerful **emotional effect** on user’s perception of the experience and gives them a small amount superpower.</span></span> <span data-ttu-id="46afd-228">音声の使用は、両手がふさがっているときや、**マルチタスク** 中にも便利な入力方法です。</span><span class="sxs-lookup"><span data-stu-id="46afd-228">Using voice is also a convenient input method when we have our arms full or are **multi-tasking**.</span></span> <span data-ttu-id="46afd-229">キーボードでの入力が難しいデバイスでは、 **音声ディクテーション** を使用してテキストを入力する方法が効率的です。</span><span class="sxs-lookup"><span data-stu-id="46afd-229">On devices where typing on a keyboard is difficult, **voice dictation** can be an efficient alternative way to input text.</span></span> <span data-ttu-id="46afd-230">最後に、宝石とジェスチャの **精度の範囲** が限られている場合は、音声を使用してユーザーの意図を明確にすることができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-230">Lastly, in some cases when the **range of accuracy** for gaze and gesture are limited, voice can help to disambiguate the user's intent.</span></span> 

<span data-ttu-id="46afd-231">**音声使用がユーザーにもたらすメリット**</span><span class="sxs-lookup"><span data-stu-id="46afd-231">**How using voice can benefit the user**</span></span>
* <span data-ttu-id="46afd-232">時間の短縮 - 最終目的をより効率的にします。</span><span class="sxs-lookup"><span data-stu-id="46afd-232">Reduces time - it should make the end goal more efficient.</span></span>
* <span data-ttu-id="46afd-233">労力の最小化 - タスクをよりスムーズかつ簡単にします。</span><span class="sxs-lookup"><span data-stu-id="46afd-233">Minimizes effort - it should make tasks more fluid and effortless.</span></span>
* <span data-ttu-id="46afd-234">認知負荷の軽減 - 直感的かつ簡単で、覚えるのが容易です。</span><span class="sxs-lookup"><span data-stu-id="46afd-234">Reduces cognitive load - it's intuitive, easy to learn, and remember.</span></span>
* <span data-ttu-id="46afd-235">ソーシャルは受け入れられません。社会の動作に適しています。</span><span class="sxs-lookup"><span data-stu-id="46afd-235">It's socially acceptable - it should fit in with societal norms of behavior.</span></span>
* <span data-ttu-id="46afd-236">日常的 - 音声はすぐに習慣的な動作となることができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-236">It's routine - voice can readily become a habitual behavior.</span></span>

### <a name="challenges-for-voice-input"></a><span data-ttu-id="46afd-237">音声入力の課題</span><span class="sxs-lookup"><span data-stu-id="46afd-237">Challenges for voice input</span></span>

<span data-ttu-id="46afd-238">音声入力は多くのさまざまなアプリケーションにとって優れていますが、いくつかの課題に直面しています。</span><span class="sxs-lookup"><span data-stu-id="46afd-238">While voice input is great for many different applications, it also faces several challenges.</span></span> <span data-ttu-id="46afd-239">音声入力の利点と課題の両方を理解することで、アプリ開発者は、音声入力を使用する方法とタイミング、およびユーザーのエクスペリエンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-239">Understanding both the advantages and challenges for voice input enables app developers to make smarter choices for how and when to use voice input and to create a great experience for their users.</span></span>

<span data-ttu-id="46afd-240">**連続入力コントロールの音声入力** 細かい制御はその1つです。</span><span class="sxs-lookup"><span data-stu-id="46afd-240">**Voice input for continuous input control** Fine-grained control is one of them.</span></span> <span data-ttu-id="46afd-241">たとえば、ユーザーが音楽アプリでボリュームを変更する場合があります。</span><span class="sxs-lookup"><span data-stu-id="46afd-241">For example, a user might want to change their volume in their music app.</span></span> <span data-ttu-id="46afd-242">"音を大きくする" と言うことができますが、ボリュームを作成するためにシステムがどの程度大きくなっているかが明確ではありません。</span><span class="sxs-lookup"><span data-stu-id="46afd-242">She can say "louder", but it's not clear how much louder the system is supposed to make the volume.</span></span> <span data-ttu-id="46afd-243">ユーザーは、"少し大きくする" ようにすることができますが、"少し" は定量化が困難です。</span><span class="sxs-lookup"><span data-stu-id="46afd-243">The user could say: "Make it a little louder", but "a little" is difficult to quantify.</span></span> <span data-ttu-id="46afd-244">音声を使用したホログラムの移動またはスケーリングも難しくなります。</span><span class="sxs-lookup"><span data-stu-id="46afd-244">Moving or scaling holograms with voice is similarly difficult.</span></span> 

<span data-ttu-id="46afd-245">**音声入力の検出の信頼性** 音声入力システムの品質と品質が向上しても、音声コマンドが誤って聞こえたり、解釈されたりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="46afd-245">**Reliability of voice input detection** While voice input systems become better and better, sometimes they may incorrectly hear and interpret a voice command.</span></span>
<span data-ttu-id="46afd-246">重要なのは、アプリケーションの課題に対処することです。</span><span class="sxs-lookup"><span data-stu-id="46afd-246">The key is to address the challenge in your application.</span></span> <span data-ttu-id="46afd-247">システムがリッスンしているときにユーザーにフィードバックを提供し、システムが認識していることを確認して、ユーザーの音声を理解する潜在的な問題を明確にします。</span><span class="sxs-lookup"><span data-stu-id="46afd-247">Provide feedback to your users when the system is listening and what the system understood clarifies potential issues understanding the users' speech.</span></span>  

<span data-ttu-id="46afd-248">**共有スペースでの音声入力** 他のユーザーと共有するスペースでは、音声をソーシャルことができない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="46afd-248">**Voice input in shared spaces** Voice may not be socially acceptable in spaces that you share with others.</span></span>
<span data-ttu-id="46afd-249">次に例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="46afd-249">Here are a few examples:</span></span>
* <span data-ttu-id="46afd-250">ユーザーは他のユーザーを妨害したくない場合があります (たとえば、quiet ライブラリや共有オフィスなど)。</span><span class="sxs-lookup"><span data-stu-id="46afd-250">The user may not want to disturb others (for example, in a quiet library or shared office)</span></span>
* <span data-ttu-id="46afd-251">ユーザーは、公開されていないように見えにくいかもしれません。</span><span class="sxs-lookup"><span data-stu-id="46afd-251">Users may feel awkward being seen talking to themselves in public,</span></span>
* <span data-ttu-id="46afd-252">他のユーザーがリッスンしているときに、個人または機密のメッセージ (パスワードを含む) がディクテーションされることが不快に感じられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="46afd-252">A user may feel uncomfortable dictating a personal or confidential message (including passwords) while others are listening</span></span>

<span data-ttu-id="46afd-253">**一意または不明な単語の音声入力** ユーザーが、ニックネーム、特定のスラング語、略語など、システムに知られていない単語をディクテーションしている場合にも、音声入力の問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="46afd-253">**Voice input of unique or unknown words** Difficulties for voice input also come when users are dictating words that may be unknown to the system, such as nicknames, certain slang words, or abbreviations.</span></span> 

<span data-ttu-id="46afd-254">**音声コマンドの学習** 最終的な目標はシステムと自然に逆のことですが、多くの場合、アプリは特定の定義済み音声コマンドに依存しています。</span><span class="sxs-lookup"><span data-stu-id="46afd-254">**Learning voice commands** While the ultimate goal is to naturally converse with your system, often apps still rely on specific pre-defined voice commands.</span></span>
<span data-ttu-id="46afd-255">音声コマンドの重要なセットに関連する課題は、ユーザーをオーバーロードすることなくユーザーを教える方法と、ユーザーがそれを保持できるようにする方法です。</span><span class="sxs-lookup"><span data-stu-id="46afd-255">A challenge associated with a significant set of voice commands is how to teach them without overloading the user and how to help the user to keep them.</span></span> 

<br>

---

### <a name="voice-feedback-states"></a><span data-ttu-id="46afd-256">音声のフィードバックの状態</span><span class="sxs-lookup"><span data-stu-id="46afd-256">Voice feedback states</span></span>

<span data-ttu-id="46afd-257">音声が適切に適用されると、**ユーザーは自分が何を言えるのかを理解し、**システムがそれを正しく認識した\*\* という明確なフィードバックを得ます。\*\*</span><span class="sxs-lookup"><span data-stu-id="46afd-257">When Voice is applied properly, the user understands **what they can say and get clear feedback** the system **heard them correctly**.</span></span> <span data-ttu-id="46afd-258">こうした 2 つのシグナルにより、ユーザーは音声をメインの入力として使用することに自信を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-258">These two signals make the user feel confident in using Voice as a primary input.</span></span> <span data-ttu-id="46afd-259">下の図は、音声入力が認識されたときにカーソルに何が発生するか、またそれがユーザーにどのように伝わるかを示す図です。</span><span class="sxs-lookup"><span data-stu-id="46afd-259">Below is a diagram showing what happens to the cursor when voice input is recognized and how it communicates that to the user.</span></span>


:::row:::
    :::column:::
       <span data-ttu-id="46afd-260">![1. 標準のカーソル状態](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="46afd-260">![1. Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="46afd-261">**1. 標準のカーソル状態**</span><span class="sxs-lookup"><span data-stu-id="46afd-261">**1. Regular cursor state**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="46afd-262">![2. 音声フィードバックを通知してから、非表示にします。](images/voicefeedbackstates-voice.jpg)</span><span class="sxs-lookup"><span data-stu-id="46afd-262">![2. Communicates voice feedback and then disappears](images/voicefeedbackstates-voice.jpg)</span></span><br>
        <span data-ttu-id="46afd-263">**2. 音声フィードバックを通知してから、非表示にします。**</span><span class="sxs-lookup"><span data-stu-id="46afd-263">**2. Communicates voice feedback and then disappears**</span></span><br>
    :::column-end:::
    :::column:::
       <span data-ttu-id="46afd-264">![番.</span><span class="sxs-lookup"><span data-stu-id="46afd-264">![\*3.</span></span> <span data-ttu-id="46afd-265">通常のカーソルの状態](images/voicefeedbackstates-regular.jpg)</span><span class="sxs-lookup"><span data-stu-id="46afd-265">Regular cursor state](images/voicefeedbackstates-regular.jpg)</span></span><br>
       <span data-ttu-id="46afd-266">**3. 通常のカーソル状態に戻ります。**</span><span class="sxs-lookup"><span data-stu-id="46afd-266">**3. Returns to regular cursor state**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a><span data-ttu-id="46afd-267">Mixed Reality における「音声」について、ユーザーが知っておくべき重要な事項</span><span class="sxs-lookup"><span data-stu-id="46afd-267">Top things users should know about "speech" in mixed reality</span></span>

* <span data-ttu-id="46afd-268">ボタンをターゲットにしている間に **"Select"** を言います (ボタンを選択するには、このボタンを任意の場所で使用できます)。</span><span class="sxs-lookup"><span data-stu-id="46afd-268">Say **"Select"** while targeting a button (you can use this anywhere to select a button).</span></span>
* <span data-ttu-id="46afd-269">一部のアプリでは、アクションを実行するために **アプリ バー ボタンのラベル名** を言うことができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-269">You can say the **label name of an app bar button** in some apps to take an action.</span></span> <span data-ttu-id="46afd-270">たとえば、アプリを確認しているときに、ユーザーは "Remove" コマンドを使用してアプリを世界中から削除することができます (これにより、自分で選択しなければならない時間が節約されます)。</span><span class="sxs-lookup"><span data-stu-id="46afd-270">For example, while looking at an app, a user can say the command "Remove" to remove the app from the world (this saves time from having to select it with your hand).</span></span>
* <span data-ttu-id="46afd-271">Cortana の聞き取りを開始するには、「Cortana」と言って **ください。**</span><span class="sxs-lookup"><span data-stu-id="46afd-271">You can start Cortana listening by saying **"Hey Cortana."**</span></span> <span data-ttu-id="46afd-272">質問をしたり (「コルタナさん、エッフェル塔の高さは?」など)、アプリを開くように指示したり (「コルタナさん、Netflix を開いて」など)、スタート メニューを表示するように指示したり (「コルタナさん、ホームに戻って」など) することができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-272">You can ask her questions ("Hey Cortana, how tall is the Eiffel tower"), tell her to open an app ("Hey Cortana, open Netflix"), or tell her to bring up the Start Menu ("Hey Cortana, take me home") and more.</span></span>

## <a name="common-questions-and-concerns-users-have-about-voice"></a><span data-ttu-id="46afd-273">音声に関する一般的な質問と問題</span><span class="sxs-lookup"><span data-stu-id="46afd-273">Common questions and concerns users have about voice</span></span>

* <span data-ttu-id="46afd-274">何を言えばよいですか。</span><span class="sxs-lookup"><span data-stu-id="46afd-274">What can I say?</span></span>
* <span data-ttu-id="46afd-275">音声が正しく認識されているかどうかを確認する方法。</span><span class="sxs-lookup"><span data-stu-id="46afd-275">How do I know the system heard me correctly?</span></span>
   * <span data-ttu-id="46afd-276">音声コマンドが継続的に誤認識される。</span><span class="sxs-lookup"><span data-stu-id="46afd-276">The system keeps getting my voice commands wrong.</span></span>
   * <span data-ttu-id="46afd-277">音声コマンドに対する反応がない。</span><span class="sxs-lookup"><span data-stu-id="46afd-277">It doesn’t react when I give it a voice command.</span></span>
* <span data-ttu-id="46afd-278">音声コマンドを言ったが、間違った動作になる。</span><span class="sxs-lookup"><span data-stu-id="46afd-278">It reacts the wrong way when I give it a voice command.</span></span>
* <span data-ttu-id="46afd-279">自分の音声のターゲットを特定のアプリやアプリ コマンドにする方法。</span><span class="sxs-lookup"><span data-stu-id="46afd-279">How do I target my voice to a specific app or app command?</span></span>
* <span data-ttu-id="46afd-280">HoloLens のホログラフィック フレームから外れたものに音声でコマンドを出せるか。</span><span class="sxs-lookup"><span data-stu-id="46afd-280">Can I use voice to command things out the holographic frame on HoloLens?</span></span>

## <a name="communication"></a><span data-ttu-id="46afd-281">通信</span><span class="sxs-lookup"><span data-stu-id="46afd-281">Communication</span></span>

<span data-ttu-id="46afd-282">HoloLens が提供するカスタマイズされたオーディオ入力処理オプションを利用する必要があるアプリケーションでは、アプリが使用できるさまざまな [オーディオストリームのカテゴリ](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) を理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="46afd-282">For applications that want to take advantage of the customized audio input processing options provided by HoloLens, it's important to understand the various [audio stream categories](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) your app can consume.</span></span> <span data-ttu-id="46afd-283">Windows 10 では、さまざまなストリームカテゴリがサポートされています。 HoloLens では、これらのうちの3つを使用して、音声、通信、その他に調整されたマイクオーディオ品質をカスタム処理によって最適化します。これは、アンビエント環境のオーディオキャプチャ (つまり、"ビデオカメラ") シナリオで使用できます。</span><span class="sxs-lookup"><span data-stu-id="46afd-283">Windows 10 supports several different stream categories and HoloLens makes use of three of these to enable custom processing to optimize the microphone audio quality tailored for speech, communication, and other, which can be used for ambient environment audio capture (that is, "camcorder") scenarios.</span></span>
* <span data-ttu-id="46afd-284">AudioCategory_Communications ストリームカテゴリは、通話の品質とナレーションのシナリオに合わせてカスタマイズされ、クライアントにユーザーの声の 16 kHz 24 ビットの mono オーディオストリームを提供します。</span><span class="sxs-lookup"><span data-stu-id="46afd-284">The AudioCategory_Communications stream category is customized for call quality and narration scenarios and provides the client with a 16-kHz 24-bit mono audio stream of the user's voice</span></span>
* <span data-ttu-id="46afd-285">AudioCategory_Speech ストリームカテゴリは、HoloLens (Windows) 音声エンジン用にカスタマイズされており、ユーザーの声の 16 kHz 24 ビットの mono ストリームを提供します。</span><span class="sxs-lookup"><span data-stu-id="46afd-285">The AudioCategory_Speech stream category is customized for the HoloLens (Windows) speech engine and provides it with a 16-kHz 24-bit mono stream of the user's voice.</span></span> <span data-ttu-id="46afd-286">このカテゴリは、サードパーティの音声エンジンで必要に応じて使用できます。</span><span class="sxs-lookup"><span data-stu-id="46afd-286">This category can be used by third-party speech engines if needed.</span></span>
* <span data-ttu-id="46afd-287">AudioCategory_Other ストリームカテゴリは、アンビエント環境のオーディオ記録用にカスタマイズされており、クライアントには 48 kHz 24 ビットのステレオオーディオストリームが用意されています。</span><span class="sxs-lookup"><span data-stu-id="46afd-287">The AudioCategory_Other stream category is customized for ambient environment audio recording and provides the client with a 48-kHz 24-bit stereo audio stream.</span></span>

<span data-ttu-id="46afd-288">このようなオーディオ処理はすべてハードウェアアクセラレータです。これは、HoloLens CPU で同じ処理が行われた場合と比べて、機能の電力消費が多くなることを意味します。</span><span class="sxs-lookup"><span data-stu-id="46afd-288">All this audio processing is hardware accelerated which means the features drain a lot less power than if the same processing was done on the HoloLens CPU.</span></span> <span data-ttu-id="46afd-289">システムのバッテリ寿命を最大化し、組み込みのオフロードオーディオ入力処理を活用するために、CPU で他のオーディオ入力処理を実行しないようにします。</span><span class="sxs-lookup"><span data-stu-id="46afd-289">Avoid running other audio input processing on the CPU to maximize system battery life and take advantage of the built-in, offloaded audio input processing.</span></span>

## <a name="languages"></a><span data-ttu-id="46afd-290">Languages</span><span class="sxs-lookup"><span data-stu-id="46afd-290">Languages</span></span>

<span data-ttu-id="46afd-291">HoloLens 2 では、 [複数の言語がサポート](/hololens/hololens2-language-support)されています。</span><span class="sxs-lookup"><span data-stu-id="46afd-291">HoloLens 2 [supports multiple languages](/hololens/hololens2-language-support).</span></span> <span data-ttu-id="46afd-292">複数のキーボードがインストールされている場合や、アプリが別の言語で音声認識エンジンを作成しようとした場合でも、音声コマンドは常にシステムの表示言語で実行されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="46afd-292">Keep in mind that speech commands will always run in the system's display language even if multiple keyboards are installed or if apps attempt to create a speech recognizer in a different language.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="46afd-293">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="46afd-293">Troubleshooting</span></span>

<span data-ttu-id="46afd-294">"Select" と "Cortana" を使用して問題が発生している場合は、静かな領域に移動するか、ノイズの発生源から離れるか、音を大きくしてみてください。</span><span class="sxs-lookup"><span data-stu-id="46afd-294">If you're having any issues using "select" and "Hey Cortana", try moving to a quieter space, turning away from the source of noise, or by speaking louder.</span></span> <span data-ttu-id="46afd-295">現時点では、HoloLens の音声認識はすべて米国英語のネイティブスピーカーに対して調整および最適化されています。</span><span class="sxs-lookup"><span data-stu-id="46afd-295">At this time, all speech recognition on HoloLens is tuned and optimized specifically to native speakers of United States English.</span></span>

<span data-ttu-id="46afd-296">Windows Mixed Reality Developer Edition release 2017 では、オーディオエンドポイント管理ロジックは、最初の HMD 接続の後、いったんログアウトして PC デスクトップに戻すと、正常に機能します。</span><span class="sxs-lookup"><span data-stu-id="46afd-296">For the Windows Mixed Reality Developer Edition release 2017, the audio endpoint management logic will work fine (forever) after logging out and back in to the PC desktop after the initial HMD connection.</span></span> <span data-ttu-id="46afd-297">ユーザーは、WMR OOBE を通過した後に初めてサインアウト/イベントが発生する前に、HMD を初めて接続する前にシステムがどのように設定されているかによって、オーディオの切り替えなしのさまざまなオーディオ機能の問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="46afd-297">Before that first sign out/in event after going through WMR OOBE, the user could experience various audio functionality issues ranging from no audio to no audio switching depending on how the system was set up before connecting the HMD for the first time.</span></span>

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="46afd-298">Unity 用の MRTK (Mixed Reality Toolkit) での音声入力</span><span class="sxs-lookup"><span data-stu-id="46afd-298">Voice input in MRTK (Mixed Reality Toolkit) for Unity</span></span>
<span data-ttu-id="46afd-299">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** では、任意のオブジェクトに音声コマンドを簡単に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-299">With **[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)**, you can easily assign voice command on any objects.</span></span> <span data-ttu-id="46afd-300">MRTK の **音声入力プロファイル** を使用して、キーワードを定義します。</span><span class="sxs-lookup"><span data-stu-id="46afd-300">Use MRTK's **Speech Input Profile** to define your keywords.</span></span> <span data-ttu-id="46afd-301">**SpeechInputHandler** スクリプトを割り当てることにより、音声入力プロファイルで定義されているキーワードにオブジェクトを応答させることができます。</span><span class="sxs-lookup"><span data-stu-id="46afd-301">By assigning **SpeechInputHandler** script, you can make any object respond to the keywords defined in the Speech Input Profile.</span></span> <span data-ttu-id="46afd-302">また、SpeechInputHandler は、ユーザーの信頼度を向上させるための音声確認ラベルも提供します。</span><span class="sxs-lookup"><span data-stu-id="46afd-302">SpeechInputHandler also provides speech confirmation label to improve the user's confidence.</span></span>

* [<span data-ttu-id="46afd-303">MRTK-Voice コマンド</span><span class="sxs-lookup"><span data-stu-id="46afd-303">MRTK - Voice command</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/input/speech.md)

---

## <a name="see-also"></a><span data-ttu-id="46afd-304">関連項目</span><span class="sxs-lookup"><span data-stu-id="46afd-304">See also</span></span>

* [<span data-ttu-id="46afd-305">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="46afd-305">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="46afd-306">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="46afd-306">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="46afd-307">DirectX の音声入力</span><span class="sxs-lookup"><span data-stu-id="46afd-307">Voice input in DirectX</span></span>](../develop/native/voice-input-in-directx.md)
* [<span data-ttu-id="46afd-308">Unity の音声入力</span><span class="sxs-lookup"><span data-stu-id="46afd-308">Voice input in Unity</span></span>](../develop/unity/voice-input-in-unity.md)