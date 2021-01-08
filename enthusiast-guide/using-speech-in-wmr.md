---
title: Windows Mixed Reality での音声の使用
description: 音声入力を使用して、Windows Mixed Reality アプリのコマンド、3D オブジェクト、およびディクテーションを制御する方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、フィードバック、フィードバックハブ、バグ
appliesto:
- Windows 10
ms.openlocfilehash: 9c1863a3fb0c7d8681f82aa6e0d93400bef578c9
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007672"
---
# <a name="using-speech-in-windows-mixed-reality"></a><span data-ttu-id="dfa87-104">Windows Mixed Reality での音声の使用</span><span class="sxs-lookup"><span data-stu-id="dfa87-104">Using Speech in Windows Mixed Reality</span></span>

<span data-ttu-id="dfa87-105">音声を使用して、Windows Mixed Reality をより迅速に利用できます。</span><span class="sxs-lookup"><span data-stu-id="dfa87-105">You can use your voice to get around Windows Mixed Reality faster.</span></span> <span data-ttu-id="dfa87-106">すばやく写真を撮影したり、アプリを開いたり、コントローラーを使用せずに、電話による移植を行ったりすることができます。</span><span class="sxs-lookup"><span data-stu-id="dfa87-106">Taking a quick photo, opening an app, even teleporting without a controller are all a word away.</span></span> <span data-ttu-id="dfa87-107">簡単に入力できるようにするには、mixed reality キーボードでディクテーションモードを試してみてください。</span><span class="sxs-lookup"><span data-stu-id="dfa87-107">For an easy way to type, try dictation mode on the mixed reality keyboard.</span></span> 

<span data-ttu-id="dfa87-108">音声に問題がありますか。</span><span class="sxs-lookup"><span data-stu-id="dfa87-108">Having trouble with Speech?</span></span> [<span data-ttu-id="dfa87-109">ヘルプの表示</span><span class="sxs-lookup"><span data-stu-id="dfa87-109">Get help</span></span>](using-wmr-faq.md#speech-commands-arent-working)

<!-- NEED VIDEO: https://support.microsoft.com/en-us/help/4041322/windows-10-speech-in-windows-mixed-reality -->

> [!NOTE]
> * <span data-ttu-id="dfa87-110">音声が有効になっている場合、Windows Mixed Reality は常にリッスンします。</span><span class="sxs-lookup"><span data-stu-id="dfa87-110">When Speech is turned on, Windows Mixed Reality is always listening.</span></span> <span data-ttu-id="dfa87-111">インターネットに接続している場合は、Microsoft speech services がさらに多くのコマンドを認識できるように、すべてのユーザーをクラウドに送信します。</span><span class="sxs-lookup"><span data-stu-id="dfa87-111">When you’re connected to the Internet, we send everything you say to the cloud so Microsoft speech services can recognize even more of your commands.</span></span>
> * <span data-ttu-id="dfa87-112">音声コマンドは、すべての言語でサポートされているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="dfa87-112">Speech commands are not supported in all languages.</span></span> <span data-ttu-id="dfa87-113">詳細情報</span><span class="sxs-lookup"><span data-stu-id="dfa87-113">Learn more</span></span>
> * <span data-ttu-id="dfa87-114">Bluetooth ヘッドセットとスピーカーは、Windows Mixed Reality ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="dfa87-114">Bluetooth headsets and speakers are not supported in Windows Mixed Reality.</span></span>

## <a name="see-it-say-it"></a><span data-ttu-id="dfa87-115">見て発音する</span><span class="sxs-lookup"><span data-stu-id="dfa87-115">See it, say it</span></span>

<span data-ttu-id="dfa87-116">Windows Mixed Reality ホームでは、単語が表示される場合は、多くの場合、音声コマンドとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="dfa87-116">In the Windows Mixed Reality home, if you see a word, you can often use it as a speech command.</span></span> <span data-ttu-id="dfa87-117">たとえば、ボタンの名前を指定するだけで、それを選択できます。</span><span class="sxs-lookup"><span data-stu-id="dfa87-117">For instance, just say the name of a button to select it.</span></span> <span data-ttu-id="dfa87-118">名前が表示されない場合は、ボタンでモーションコントローラーをポイントして、何を言うかを確認します。</span><span class="sxs-lookup"><span data-stu-id="dfa87-118">If you don’t see a name, point your motion controller at the button to find out what to say.</span></span> <span data-ttu-id="dfa87-119">Xbox ゲームパッドの場合は、ボタンをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="dfa87-119">For Xbox gamepads, rest your gaze on the button.</span></span>

## <a name="general-speech-commands"></a><span data-ttu-id="dfa87-120">一般的な音声コマンド</span><span class="sxs-lookup"><span data-stu-id="dfa87-120">General speech commands</span></span>

<span data-ttu-id="dfa87-121">Windows Mixed Reality 全体で次の音声コマンドを使用すると、より迅速に作業を始めることができます。</span><span class="sxs-lookup"><span data-stu-id="dfa87-121">Use the following speech commands throughout Windows Mixed Reality to get around faster.</span></span> <span data-ttu-id="dfa87-122">一部のコマンドでは、"select" という指示によって表示される、宝石のカーソルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="dfa87-122">Some commands use the gaze cursor, which you’ll bring up by saying “select.”</span></span>

| <span data-ttu-id="dfa87-123">目的</span><span class="sxs-lookup"><span data-stu-id="dfa87-123">To do this</span></span> | <span data-ttu-id="dfa87-124">言う言葉</span><span class="sxs-lookup"><span data-stu-id="dfa87-124">Say this</span></span> |
| --- | --- |
| <span data-ttu-id="dfa87-125">選択</span><span class="sxs-lookup"><span data-stu-id="dfa87-125">Select</span></span> | <span data-ttu-id="dfa87-126">「選択」と言うと、宝石カーソルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dfa87-126">Say “select” to bring up the gaze cursor.</span></span> <span data-ttu-id="dfa87-127">次に、選択する項目にカーソルを置き、もう一度 [選択] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="dfa87-127">Then, turn your head to position the cursor on the thing you want to select, and say “select” again.</span></span> |
| <span data-ttu-id="dfa87-128">[スタート] メニューを開く</span><span class="sxs-lookup"><span data-stu-id="dfa87-128">Open the Start menu</span></span> | <span data-ttu-id="dfa87-129">スタート画面に戻る</span><span class="sxs-lookup"><span data-stu-id="dfa87-129">Go to Start</span></span> |
| <span data-ttu-id="dfa87-130">イマーシブアプリを終了する</span><span class="sxs-lookup"><span data-stu-id="dfa87-130">Leave an immersive app</span></span> | <span data-ttu-id="dfa87-131">[スタート画面に移動] をクリックして [クイックアクション] メニューを表示し、「Mixed reality ホーム」と言います。</span><span class="sxs-lookup"><span data-stu-id="dfa87-131">Say "Go to Start" to bring up the quick actions menu, then say "Mixed reality home."</span></span> |
| <span data-ttu-id="dfa87-132">懐中電灯をオン/オフにする</span><span class="sxs-lookup"><span data-stu-id="dfa87-132">Turn Flashlight on/off</span></span> | <span data-ttu-id="dfa87-133">[スタート画面に移動] をクリックして [クイックアクション] メニューを表示し、「Mixed reality ホーム」と言います。</span><span class="sxs-lookup"><span data-stu-id="dfa87-133">Say "Go to Start" to bring up the quick actions menu, then say "Mixed reality home."</span></span> |
| <span data-ttu-id="dfa87-134">遠距離</span><span class="sxs-lookup"><span data-stu-id="dfa87-134">Teleport</span></span> | <span data-ttu-id="dfa87-135">頭を移動する場所に変え、「テレポート」と言います。</span><span class="sxs-lookup"><span data-stu-id="dfa87-135">Turn your head toward the place you want to go, and then say “teleport.”</span></span> <span data-ttu-id="dfa87-136">(より正確なターゲットを設定するには、まず "select" を使用して、宝石のカーソルを表示し、「テレポート」と言います)。</span><span class="sxs-lookup"><span data-stu-id="dfa87-136">(For more precise targeting, first say “select” to bring up the gaze cursor, then say “teleport.”)</span></span> |
| <span data-ttu-id="dfa87-137">左または右に移動する</span><span class="sxs-lookup"><span data-stu-id="dfa87-137">Turn to the left or right</span></span> | <span data-ttu-id="dfa87-138">左または右に移動</span><span class="sxs-lookup"><span data-stu-id="dfa87-138">Turn left / turn right</span></span> |
| <span data-ttu-id="dfa87-139">180°にする</span><span class="sxs-lookup"><span data-stu-id="dfa87-139">Turn 180 degrees</span></span> | <span data-ttu-id="dfa87-140">振り向いてください</span><span class="sxs-lookup"><span data-stu-id="dfa87-140">Turn around</span></span> |
| <span data-ttu-id="dfa87-141">前に進む</span><span class="sxs-lookup"><span data-stu-id="dfa87-141">Move forward</span></span> | <span data-ttu-id="dfa87-142">前方または前方へ移動</span><span class="sxs-lookup"><span data-stu-id="dfa87-142">Move forward / walk forward</span></span> |
| <span data-ttu-id="dfa87-143">バックアップ</span><span class="sxs-lookup"><span data-stu-id="dfa87-143">Back up</span></span> | <span data-ttu-id="dfa87-144">戻る/ウォークバック</span><span class="sxs-lookup"><span data-stu-id="dfa87-144">Move back / walk back</span></span> |
| <span data-ttu-id="dfa87-145">左へ移動</span><span class="sxs-lookup"><span data-stu-id="dfa87-145">Move to the left</span></span> | <span data-ttu-id="dfa87-146">左または左に移動</span><span class="sxs-lookup"><span data-stu-id="dfa87-146">Move left / walk left</span></span> |
| <span data-ttu-id="dfa87-147">右へ移動</span><span class="sxs-lookup"><span data-stu-id="dfa87-147">Move to the right</span></span> | <span data-ttu-id="dfa87-148">右または右に移動</span><span class="sxs-lookup"><span data-stu-id="dfa87-148">Move right / walk right</span></span> |

## <a name="3d-object-commands"></a><span data-ttu-id="dfa87-149">3D オブジェクトコマンド</span><span class="sxs-lookup"><span data-stu-id="dfa87-149">3D object commands</span></span>

<span data-ttu-id="dfa87-150">次のコマンドを使用するには、3D オブジェクト、ホログラム、またはアプリウィンドウを見つめます。</span><span class="sxs-lookup"><span data-stu-id="dfa87-150">Gaze at a 3D object, hologram, or app window to use these commands:</span></span>

| <span data-ttu-id="dfa87-151">目的</span><span class="sxs-lookup"><span data-stu-id="dfa87-151">To do this</span></span> | <span data-ttu-id="dfa87-152">言う言葉</span><span class="sxs-lookup"><span data-stu-id="dfa87-152">Say this</span></span> |
| --- | --- |
| <span data-ttu-id="dfa87-153">拡大する</span><span class="sxs-lookup"><span data-stu-id="dfa87-153">Make it bigger</span></span> | <span data-ttu-id="dfa87-154">大き</span><span class="sxs-lookup"><span data-stu-id="dfa87-154">Bigger</span></span> |
| <span data-ttu-id="dfa87-155">小さくする</span><span class="sxs-lookup"><span data-stu-id="dfa87-155">Make it smaller</span></span> | <span data-ttu-id="dfa87-156">小</span><span class="sxs-lookup"><span data-stu-id="dfa87-156">Smaller</span></span> |
| <span data-ttu-id="dfa87-157">顔に変える</span><span class="sxs-lookup"><span data-stu-id="dfa87-157">Turn it to face you</span></span> | <span data-ttu-id="dfa87-158">顔</span><span class="sxs-lookup"><span data-stu-id="dfa87-158">Face me</span></span> |
| <span data-ttu-id="dfa87-159">移動する準備ができました。お待ちください</span><span class="sxs-lookup"><span data-stu-id="dfa87-159">Get it ready to move - it will follow your gaze</span></span> | <span data-ttu-id="dfa87-160">移動</span><span class="sxs-lookup"><span data-stu-id="dfa87-160">Move this</span></span> |
| <span data-ttu-id="dfa87-161">移動が完了したら配置する</span><span class="sxs-lookup"><span data-stu-id="dfa87-161">Place it when you're done moving it</span></span> | <span data-ttu-id="dfa87-162">場所</span><span class="sxs-lookup"><span data-stu-id="dfa87-162">Place</span></span> |

## <a name="app-bar-commands"></a><span data-ttu-id="dfa87-163">アプリバーのコマンド</span><span class="sxs-lookup"><span data-stu-id="dfa87-163">App bar commands</span></span>

<span data-ttu-id="dfa87-164">アプリウィンドウまたは3D オブジェクトを見つめて、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="dfa87-164">Gaze at an app window or a 3D object to use these commands:</span></span>

| <span data-ttu-id="dfa87-165">目的</span><span class="sxs-lookup"><span data-stu-id="dfa87-165">To do this</span></span> | <span data-ttu-id="dfa87-166">言う言葉</span><span class="sxs-lookup"><span data-stu-id="dfa87-166">Say this</span></span> |
| --- | --- |
| <span data-ttu-id="dfa87-167">アプリまたは3D オブジェクトを閉じる</span><span class="sxs-lookup"><span data-stu-id="dfa87-167">Close an app or 3D object</span></span> | <span data-ttu-id="dfa87-168">閉じる</span><span class="sxs-lookup"><span data-stu-id="dfa87-168">Close</span></span> |
| <span data-ttu-id="dfa87-169">何かを調整する (サイズ変更または移動)</span><span class="sxs-lookup"><span data-stu-id="dfa87-169">Adjust something (resize or move)</span></span> | <span data-ttu-id="dfa87-170">Adjust</span><span class="sxs-lookup"><span data-stu-id="dfa87-170">Adjust</span></span> |
| <span data-ttu-id="dfa87-171">調整を停止する</span><span class="sxs-lookup"><span data-stu-id="dfa87-171">Stop adjusting</span></span> | <span data-ttu-id="dfa87-172">完了</span><span class="sxs-lookup"><span data-stu-id="dfa87-172">Done</span></span> |
| <span data-ttu-id="dfa87-173">3D オブジェクトのアプリバーを非表示にする</span><span class="sxs-lookup"><span data-stu-id="dfa87-173">Hide the app bar on a 3D object</span></span> | <span data-ttu-id="dfa87-174">メニューの非表示</span><span class="sxs-lookup"><span data-stu-id="dfa87-174">Hide menu</span></span> |
| <span data-ttu-id="dfa87-175">3D オブジェクトでのアプリバーの表示</span><span class="sxs-lookup"><span data-stu-id="dfa87-175">Show the app bar on a 3D object</span></span> | <span data-ttu-id="dfa87-176">メニューの表示</span><span class="sxs-lookup"><span data-stu-id="dfa87-176">Show Menu</span></span> |
| <span data-ttu-id="dfa87-177">[戻る] ボタンがあるアプリの前の画面またはページに戻る</span><span class="sxs-lookup"><span data-stu-id="dfa87-177">Go back to the previous screen or page in an app that has a Go back button</span></span>  | <span data-ttu-id="dfa87-178">戻る</span><span class="sxs-lookup"><span data-stu-id="dfa87-178">Go back</span></span> |
| <span data-ttu-id="dfa87-179">お探しのアプリで、Xbox コントローラーを mixed reality コントローラーとしてではなく、ゲームパッドとして使用します。</span><span class="sxs-lookup"><span data-stu-id="dfa87-179">Use your Xbox controller as a gamepad, rather than as a mixed reality controller, in the app you’re looking at</span></span> | <span data-ttu-id="dfa87-180">ゲームパッドとして使用</span><span class="sxs-lookup"><span data-stu-id="dfa87-180">Use as gamepad</span></span> |
| <span data-ttu-id="dfa87-181">Xbox コントローラーを mixed reality コントローラーとして使用する (ゲームパッドとして使用されている場合)</span><span class="sxs-lookup"><span data-stu-id="dfa87-181">Use your Xbox controller as a mixed reality controller (when you’ve been using it as a gamepad)</span></span> | <span data-ttu-id="dfa87-182">見つめで使用する</span><span class="sxs-lookup"><span data-stu-id="dfa87-182">Use with gaze</span></span> |

## <a name="start-menu-commands"></a><span data-ttu-id="dfa87-183">[スタート] メニューのコマンド</span><span class="sxs-lookup"><span data-stu-id="dfa87-183">Start menu commands</span></span>

<span data-ttu-id="dfa87-184">次のコマンドを使用するには、[スタート] メニューを見つめます。</span><span class="sxs-lookup"><span data-stu-id="dfa87-184">Gaze at the Start menu to use these commands:</span></span>

| <span data-ttu-id="dfa87-185">目的</span><span class="sxs-lookup"><span data-stu-id="dfa87-185">To do this</span></span> | <span data-ttu-id="dfa87-186">言う言葉</span><span class="sxs-lookup"><span data-stu-id="dfa87-186">Say this</span></span> |
| --- | --- |
| <span data-ttu-id="dfa87-187">すべてのアプリの一覧にアクセスする</span><span class="sxs-lookup"><span data-stu-id="dfa87-187">Go to the All Apps list</span></span> | <span data-ttu-id="dfa87-188">すべてのアプリ</span><span class="sxs-lookup"><span data-stu-id="dfa87-188">All apps</span></span> |
| <span data-ttu-id="dfa87-189">スタートまたはすべてのアプリで上または下へ移動</span><span class="sxs-lookup"><span data-stu-id="dfa87-189">Move up or down on Start or All apps</span></span> | <span data-ttu-id="dfa87-190">ページ アップ/ダウン</span><span class="sxs-lookup"><span data-stu-id="dfa87-190">Page up/down</span></span> |
| <span data-ttu-id="dfa87-191">[スタート] メニューに戻る (すべてのアプリから)</span><span class="sxs-lookup"><span data-stu-id="dfa87-191">Go back to Start menu from All apps</span></span> | <span data-ttu-id="dfa87-192">戻る</span><span class="sxs-lookup"><span data-stu-id="dfa87-192">Go back</span></span> |
| <span data-ttu-id="dfa87-193">写真を撮って</span><span class="sxs-lookup"><span data-stu-id="dfa87-193">Take a photo</span></span> | <span data-ttu-id="dfa87-194">カメラ</span><span class="sxs-lookup"><span data-stu-id="dfa87-194">Camera</span></span> |
| <span data-ttu-id="dfa87-195">ビデオを見る</span><span class="sxs-lookup"><span data-stu-id="dfa87-195">Take a video</span></span> | <span data-ttu-id="dfa87-196">ビデオ</span><span class="sxs-lookup"><span data-stu-id="dfa87-196">Video</span></span> |
| <span data-ttu-id="dfa87-197">デスクトップの混合 Reality ポータルでヘッドセットビューを表示する</span><span class="sxs-lookup"><span data-stu-id="dfa87-197">Show the headset view in Mixed Reality Portal on your desktop</span></span> | <span data-ttu-id="dfa87-198">プレビュー</span><span class="sxs-lookup"><span data-stu-id="dfa87-198">Preview</span></span> |
| <span data-ttu-id="dfa87-199">開始時にボリュームコントロールを開く</span><span class="sxs-lookup"><span data-stu-id="dfa87-199">Open the volume control on Start</span></span> | <span data-ttu-id="dfa87-200">音量を変更する</span><span class="sxs-lookup"><span data-stu-id="dfa87-200">Change volume</span></span> |
| <span data-ttu-id="dfa87-201">Mute</span><span class="sxs-lookup"><span data-stu-id="dfa87-201">Mute</span></span> | <span data-ttu-id="dfa87-202">Mute</span><span class="sxs-lookup"><span data-stu-id="dfa87-202">Mute</span></span> |
| <span data-ttu-id="dfa87-203">Unmute</span><span class="sxs-lookup"><span data-stu-id="dfa87-203">Unmute</span></span> | <span data-ttu-id="dfa87-204">Unmute</span><span class="sxs-lookup"><span data-stu-id="dfa87-204">Unmute</span></span> |
| <span data-ttu-id="dfa87-205">[スタート] メニューを閉じる</span><span class="sxs-lookup"><span data-stu-id="dfa87-205">Close the Start menu</span></span> | <span data-ttu-id="dfa87-206">終了またはキャンセル</span><span class="sxs-lookup"><span data-stu-id="dfa87-206">Close or cancel</span></span> |

## <a name="hey-cortana-commands"></a><span data-ttu-id="dfa87-207">Cortana コマンドのこんにちは</span><span class="sxs-lookup"><span data-stu-id="dfa87-207">Hey Cortana commands</span></span>

<span data-ttu-id="dfa87-208">「Cortana」と言って、次のいずれかのコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="dfa87-208">Say "Hey Cortana,” then use one of the following commands:</span></span>

| <span data-ttu-id="dfa87-209">目的</span><span class="sxs-lookup"><span data-stu-id="dfa87-209">To do this</span></span> | <span data-ttu-id="dfa87-210">言う言葉</span><span class="sxs-lookup"><span data-stu-id="dfa87-210">Say this</span></span> |
| --- | --- |
| <span data-ttu-id="dfa87-211">Cortana に対して何ができるかを確認する</span><span class="sxs-lookup"><span data-stu-id="dfa87-211">Find out what you can say to Cortana</span></span> | <span data-ttu-id="dfa87-212">何を言えばよいですか。</span><span class="sxs-lookup"><span data-stu-id="dfa87-212">What can I say?</span></span> |
| <span data-ttu-id="dfa87-213">音量を上げる/下げる</span><span class="sxs-lookup"><span data-stu-id="dfa87-213">Increase/decrease volume</span></span> | <span data-ttu-id="dfa87-214">音量を上げる</span><span class="sxs-lookup"><span data-stu-id="dfa87-214">Turn the volume up/down</span></span> |
| <span data-ttu-id="dfa87-215">ミュート/ミュート解除</span><span class="sxs-lookup"><span data-stu-id="dfa87-215">Mute/unmute</span></span> | <span data-ttu-id="dfa87-216">ミュート/ミュート解除</span><span class="sxs-lookup"><span data-stu-id="dfa87-216">Mute/unmute</span></span> |
| <span data-ttu-id="dfa87-217">アプリを起動する</span><span class="sxs-lookup"><span data-stu-id="dfa87-217">Start an app</span></span> | <span data-ttu-id="dfa87-218">起動 [アプリ名]</span><span class="sxs-lookup"><span data-stu-id="dfa87-218">Launch [app name]</span></span> |
| <span data-ttu-id="dfa87-219">Microsoft Edge で web サイトを開く</span><span class="sxs-lookup"><span data-stu-id="dfa87-219">Open a website in Microsoft Edge</span></span> | <span data-ttu-id="dfa87-220">[Web サイト名] (たとえば、"open bing.com") を開きます。</span><span class="sxs-lookup"><span data-stu-id="dfa87-220">Open [website name] (for example, “open bing.com”)</span></span> |
| <span data-ttu-id="dfa87-221">写真を撮って</span><span class="sxs-lookup"><span data-stu-id="dfa87-221">Take a photo</span></span> | <span data-ttu-id="dfa87-222">画像の撮影</span><span class="sxs-lookup"><span data-stu-id="dfa87-222">Take picture</span></span> |
| <span data-ttu-id="dfa87-223">ビデオの録画を開始する</span><span class="sxs-lookup"><span data-stu-id="dfa87-223">Start recording a video</span></span> | <span data-ttu-id="dfa87-224">録画を開始して</span><span class="sxs-lookup"><span data-stu-id="dfa87-224">Start recording</span></span> |
| <span data-ttu-id="dfa87-225">ビデオの録画を停止する</span><span class="sxs-lookup"><span data-stu-id="dfa87-225">Stop recording a video</span></span> | <span data-ttu-id="dfa87-226">記録の停止</span><span class="sxs-lookup"><span data-stu-id="dfa87-226">Stop recording</span></span> |
| <span data-ttu-id="dfa87-227">時間を表示する</span><span class="sxs-lookup"><span data-stu-id="dfa87-227">Show the time</span></span> | <span data-ttu-id="dfa87-228">何時ですか。</span><span class="sxs-lookup"><span data-stu-id="dfa87-228">What time is it?</span></span> |
| <span data-ttu-id="dfa87-229">[スタート] メニューを開く</span><span class="sxs-lookup"><span data-stu-id="dfa87-229">Open the Start menu</span></span> | <span data-ttu-id="dfa87-230">[スタート] メニューを開く</span><span class="sxs-lookup"><span data-stu-id="dfa87-230">Open Start menu</span></span> |
| <span data-ttu-id="dfa87-231">タイマーを設定する</span><span class="sxs-lookup"><span data-stu-id="dfa87-231">Set a timer</span></span> | <span data-ttu-id="dfa87-232">タイマーを設定する</span><span class="sxs-lookup"><span data-stu-id="dfa87-232">Set a timer</span></span> |
| <span data-ttu-id="dfa87-233">リマインダーを設定する</span><span class="sxs-lookup"><span data-stu-id="dfa87-233">Set a reminder</span></span> | <span data-ttu-id="dfa87-234">リマインダーを設定する</span><span class="sxs-lookup"><span data-stu-id="dfa87-234">Set a reminder</span></span> |

> [!NOTE]
> * <span data-ttu-id="dfa87-235">Cortana は、すべての地域と言語で使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="dfa87-235">Cortana is not available in all regions and languages.</span></span> <span data-ttu-id="dfa87-236">[詳細情報](https://support.microsoft.com/help/4026948)</span><span class="sxs-lookup"><span data-stu-id="dfa87-236">[Learn more](https://support.microsoft.com/help/4026948).</span></span>
> * <span data-ttu-id="dfa87-237">Cortana が "Cortana" に応答していない場合は、[ **設定 > プライバシー > 音声** 認識] を選択し、オンライン音声認識を有効にします。</span><span class="sxs-lookup"><span data-stu-id="dfa87-237">If Cortana isn't responding to "Hey Cortana," select **Settings > Privacy > Speech** and make Online speech recognition is turned on.</span></span>
> * <span data-ttu-id="dfa87-238">Cortana をオフにすると、"Cortana" 音声コマンドは使用できなくなりますが、他のコマンド ("select" や "テレポート" など) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="dfa87-238">If you turn Cortana off, "Hey Cortana" voice commands won't be available, but you'll still be able to use other commands (like "select" and "teleport")</span></span>

## <a name="keyboard-dictation"></a><span data-ttu-id="dfa87-239">キーボードディクテーション</span><span class="sxs-lookup"><span data-stu-id="dfa87-239">Keyboard dictation</span></span>

<span data-ttu-id="dfa87-240">キーボードを使用して簡単に入力できるようにするには、いつでもディクテーションモードに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="dfa87-240">Switch to dictation mode anytime the keyboard is active for an easy way to type.</span></span> <span data-ttu-id="dfa87-241">キーボードの [マイク] を選択するか、[開始] をクリックして開始します。</span><span class="sxs-lookup"><span data-stu-id="dfa87-241">Select microphone  on the keyboard—or just say “start dictating”—to get started.</span></span>

> [!NOTE]
> <span data-ttu-id="dfa87-242">Mixed reality キーボードは英語でのみ使用できますが、サポートされているすべての [Windows Mixed reality 言語](other-questions.md#what-languages-are-supported-in-windows-mixed-reality)でディクテーションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="dfa87-242">The mixed reality keyboard is only available in English, but you can use dictation in any of the supported [Windows Mixed Reality languages](other-questions.md#what-languages-are-supported-in-windows-mixed-reality).</span></span>

### <a name="keyboard-dictation-commands"></a><span data-ttu-id="dfa87-243">キーボードディクテーションコマンド</span><span class="sxs-lookup"><span data-stu-id="dfa87-243">Keyboard dictation commands</span></span>

| <span data-ttu-id="dfa87-244">目的</span><span class="sxs-lookup"><span data-stu-id="dfa87-244">To do this</span></span> | <span data-ttu-id="dfa87-245">言う言葉</span><span class="sxs-lookup"><span data-stu-id="dfa87-245">Say this</span></span> |
| --- | --- |
| <span data-ttu-id="dfa87-246">キーボードを閉じる</span><span class="sxs-lookup"><span data-stu-id="dfa87-246">Close the keyboard</span></span> | <span data-ttu-id="dfa87-247">閉じる</span><span class="sxs-lookup"><span data-stu-id="dfa87-247">Close</span></span> |
| <span data-ttu-id="dfa87-248">ディクテーションを開始する</span><span class="sxs-lookup"><span data-stu-id="dfa87-248">Start dictation</span></span> | <span data-ttu-id="dfa87-249">音声の開始</span><span class="sxs-lookup"><span data-stu-id="dfa87-249">Start dictating</span></span> |
| <span data-ttu-id="dfa87-250">ディクテーションの停止</span><span class="sxs-lookup"><span data-stu-id="dfa87-250">Stop dictation</span></span> | <span data-ttu-id="dfa87-251">音声を止める</span><span class="sxs-lookup"><span data-stu-id="dfa87-251">Stop dictating</span></span> |
| <span data-ttu-id="dfa87-252">確認した内容を削除する</span><span class="sxs-lookup"><span data-stu-id="dfa87-252">Delete what you've dictated</span></span> | <span data-ttu-id="dfa87-253">それを削除</span><span class="sxs-lookup"><span data-stu-id="dfa87-253">Delete that</span></span> |
| <span data-ttu-id="dfa87-254">[ディクテーション] ボックス内のすべてを選択します。</span><span class="sxs-lookup"><span data-stu-id="dfa87-254">Select everything in the dictation box</span></span> | <span data-ttu-id="dfa87-255">すべて選択する</span><span class="sxs-lookup"><span data-stu-id="dfa87-255">Select all</span></span> |

### <a name="punctuation"></a><span data-ttu-id="dfa87-256">句読点</span><span class="sxs-lookup"><span data-stu-id="dfa87-256">Punctuation</span></span>

<span data-ttu-id="dfa87-257">使用する句読点の名前を言う必要があります。</span><span class="sxs-lookup"><span data-stu-id="dfa87-257">You’ll need to say the names of the punctuation you want to use.</span></span> <span data-ttu-id="dfa87-258">たとえば、"**質問マーク** について **コンマ** を入力してください" と表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="dfa87-258">For instance, you might say "Hey **comma** what are you up to **question mark**."</span></span>

<span data-ttu-id="dfa87-259">使用できる句読点のキーワードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="dfa87-259">Here are the punctuation keywords you can use:</span></span>

* <span data-ttu-id="dfa87-260">ピリオド、コンマ、疑問符、感嘆符、感嘆符</span><span class="sxs-lookup"><span data-stu-id="dfa87-260">Period, comma, question mark, exclamation point/exclamation mark</span></span>
* <span data-ttu-id="dfa87-261">新しい行/新しい段落</span><span class="sxs-lookup"><span data-stu-id="dfa87-261">New line/new paragraph</span></span>
* <span data-ttu-id="dfa87-262">セミコロン、コロン</span><span class="sxs-lookup"><span data-stu-id="dfa87-262">Semicolon, colon</span></span>
* <span data-ttu-id="dfa87-263">引用符を開き、引用符を閉じます</span><span class="sxs-lookup"><span data-stu-id="dfa87-263">Open quote(s), close quote(s)</span></span>
* <span data-ttu-id="dfa87-264">ハッシュタグ、スマイル、スマイル、しかめっ、ウィンク</span><span class="sxs-lookup"><span data-stu-id="dfa87-264">Hashtag, smiley/smiley face, frowny, winky</span></span>
* <span data-ttu-id="dfa87-265">ドル、パーセント</span><span class="sxs-lookup"><span data-stu-id="dfa87-265">Dollar, percent</span></span>

<span data-ttu-id="dfa87-266">場合によっては、電子メールアドレスなどをスペルチェックすると便利です。</span><span class="sxs-lookup"><span data-stu-id="dfa87-266">Sometimes it's helpful to spell out things like email addresses.</span></span> <span data-ttu-id="dfa87-267">たとえば、 example@outlook.com "e X A M P L E at outlook dot-com" と言います。</span><span class="sxs-lookup"><span data-stu-id="dfa87-267">For instance, to dictate example@outlook.com, you'd say "E X A M P L E at outlook dot-com."</span></span>

<span data-ttu-id="dfa87-268">ディクテーションを停止するには、[ **完了**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="dfa87-268">To stop dictating, select **Done**.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfa87-269">関連項目</span><span class="sxs-lookup"><span data-stu-id="dfa87-269">See also</span></span>

* [<span data-ttu-id="dfa87-270">コミュニティへの質問</span><span class="sxs-lookup"><span data-stu-id="dfa87-270">Ask the community</span></span>](https://answers.microsoft.com)
* [<span data-ttu-id="dfa87-271">サポートについては、お問い合わせください</span><span class="sxs-lookup"><span data-stu-id="dfa87-271">Contact us for support</span></span>](https://support.microsoft.com/contactus/)