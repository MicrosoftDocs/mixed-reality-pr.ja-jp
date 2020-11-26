---
title: 目の視線入力とドウェル
description: 目の視線入力とドウェル入力モデルの概要
author: sostel
ms.author: sostel
ms.date: 10/29/2019
ms.topic: article
ms.localizationpriority: high
keywords: 視線追跡, Mixed Reality, 入力, 目の視線入力, 目のターゲット設定, HoloLens 2, 視線に基づく選択, ドウェル, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, HoloLens, MRTK, Mixed Reality Toolkit, 設計
ms.openlocfilehash: 2d17b93b09b204e6ebb94a51bcc709ee043b5018
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702308"
---
# <a name="eye-gaze-and-dwell"></a><span data-ttu-id="81a28-104">目の視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="81a28-104">Eye-gaze and dwell</span></span>

<span data-ttu-id="81a28-105">_"目の視線入力とドウェル"_ 操作モデルは、[目の視線入力とコミット](gaze-and-commit.md)操作モデルの特殊なケースです。</span><span class="sxs-lookup"><span data-stu-id="81a28-105">The _"eye-gaze and dwell"_ interaction model is a special case of the [eye-gaze and commit](gaze-and-commit.md) interaction model:</span></span>
1. <span data-ttu-id="81a28-106">ターゲットを見つめるだけ</span><span class="sxs-lookup"><span data-stu-id="81a28-106">Simply look at a target and</span></span> 
2. <span data-ttu-id="81a28-107">そのターゲットを選択するという意図を示すために、次のように明示的なセカンダリ入力を実行します。_選択するターゲットをただ見つめ続ける_。</span><span class="sxs-lookup"><span data-stu-id="81a28-107">To confirm your intention to select the target, perform a secondary explicit input: _Simply keep looking at the target you would like to select_.</span></span>

## <a name="advantages-of-the-eye-gaze-and-dwell-interaction-model"></a><span data-ttu-id="81a28-108">"目の視線入力とドウェル" 操作モデルの利点</span><span class="sxs-lookup"><span data-stu-id="81a28-108">Advantages of the "eye-gaze and dwell" interaction model</span></span> 
<span data-ttu-id="81a28-109">タスクやツールの保持などで既に手がふさがっている場合、ホログラムの操作に手を使えないことがあります。</span><span class="sxs-lookup"><span data-stu-id="81a28-109">When your hands are already occupied with a task or holding tools, using them for interacting with holograms may not be an option.</span></span>
<span data-ttu-id="81a28-110">ホログラム選択のためのハンズフリーな代替操作として、"目の視線入力とドウェル" があります。これは、言い換えるなら、 _"見てから、見つめ続ける"_ ことです。</span><span class="sxs-lookup"><span data-stu-id="81a28-110">A hands-free interaction alternative for selecting holograms is "eye-gaze and dwell" or in other words: _"look and stare"_.</span></span> <span data-ttu-id="81a28-111">このアプローチの利点は、頭や体を十分に動かすことのできない非常に制約のあるユーザーであっても、ホログラムを操作できることです (非常に狭い作業環境など)。</span><span class="sxs-lookup"><span data-stu-id="81a28-111">The advantage of this approach is that even severely constrained users who may not be able to fully turn their heads or bodies can interact with holograms (e.g., in a highly confined work environment).</span></span>
<span data-ttu-id="81a28-112">ユーザーが選択したいターゲットを見つめ続けるだけで、プロセスを示す別のドウェル フィードバックが表示されます。</span><span class="sxs-lookup"><span data-stu-id="81a28-112">The user simply keeps looking at the target they would like to select and different dwell feedback is displayed to indicate the process.</span></span>


## <a name="challenges-of-the-eye-gaze-and-dwell-interaction-model"></a><span data-ttu-id="81a28-113">"目の視線入力とドウェル" 操作モデルの課題</span><span class="sxs-lookup"><span data-stu-id="81a28-113">Challenges of the "eye-gaze and dwell" interaction model</span></span>
<span data-ttu-id="81a28-114">一般的には、ドウェル ベースのアクティブ化は、音声入力もハンド入力も利用できない場合の最後のフォールバックとしてのみ使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="81a28-114">In general, we  recommend to only use dwell-based activations as a last fall-back if neither voice input nor hand input is available.</span></span> <span data-ttu-id="81a28-115">これは、ドウェル時間の選択がかなり難しい場合があるためです。</span><span class="sxs-lookup"><span data-stu-id="81a28-115">The reason is that the choice of dwell time can be pretty tricky.</span></span> <span data-ttu-id="81a28-116">初級ユーザーはドウェル時間が長くても問題ないのに対し、上級ユーザーはエクスペリエンスをすばやく効率的にナビゲートすることを好みます。</span><span class="sxs-lookup"><span data-stu-id="81a28-116">Novice users are ok with longer dwell times, while expert users want to quickly and efficiently navigate through their experiences.</span></span> <span data-ttu-id="81a28-117">その結果、ユーザーの特定のニーズに合わせてドウェル時間を調整することが困難になります。</span><span class="sxs-lookup"><span data-stu-id="81a28-117">This leads to the challenge of how to adjust the dwell time to the specific needs of a user.</span></span>
<span data-ttu-id="81a28-118">ドウェル時間が短すぎる場合:ユーザーは、ホログラムが常に自分の視線に反応する事に抵抗を感じるかもしれません。</span><span class="sxs-lookup"><span data-stu-id="81a28-118">If the dwell time is too short: The user may feel overwhelmed by having holograms react to their eye-gaze all the time.</span></span> <span data-ttu-id="81a28-119">ドウェル時間が長すぎる場合:ユーザーが長時間ターゲットを見つめ続けなければならないため、エクスペリエンスが遅すぎてスムーズさが足りないと感じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="81a28-119">If the dwell time is too long: The experience may feel too slow and interruptive as the user has to keep looking at targets for a long time.</span></span>

## <a name="design-recommendations"></a><span data-ttu-id="81a28-120">設計の推奨事項</span><span class="sxs-lookup"><span data-stu-id="81a28-120">Design recommendations</span></span>
<span data-ttu-id="81a28-121">ドウェル フィードバックには、ツー ステート アプローチを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="81a28-121">We recommend using a two-state approach for dwell feedback:</span></span>
1. <span data-ttu-id="81a28-122">*開始遅延*:ユーザーがターゲットを見つめ始めても、すぐには何も生じません。これは、すぐ何かが生じると、ユーザー エクスペリエンスが不快で当惑させるものになる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="81a28-122">*Onset delay*: When the user starts looking at a target, nothing should immediately happen as this may result in an unpleasant and overwhelming user experience.</span></span> <span data-ttu-id="81a28-123">代わりに、タイマーを起動させて、ユーザーが意図的にそのターゲットを注視しているのか、単にひと目見ただけなのかを検出します。</span><span class="sxs-lookup"><span data-stu-id="81a28-123">Instead start a timer to detect whether the user is intentionally staring at the target or merely glancing over it.</span></span>
<span data-ttu-id="81a28-124">150 から 250 ミリ秒の開始時間を、特定の近接度で (ユーザーが大きなターゲットを注視しているか見回しているか) 指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="81a28-124">We recommend an onset time of 150-250 ms in a given proximity (meaning the user is fixating vs. looking around on a large target).</span></span>  
2. <span data-ttu-id="81a28-125">*ドウェル フィードバックの開始:* ユーザーが意図的にそのターゲットを注視していることが確認されると、ドウェル フィードバックが表示され、ドウェルのアクティブ化が開始されようとしていることがユーザーに通知されます。</span><span class="sxs-lookup"><span data-stu-id="81a28-125">*Start dwell feedback:* After ensuring that the user is intentionally looking at the target, start showing dwell feedback to inform the user that the dwell activation is being initiated.</span></span> 
3. <span data-ttu-id="81a28-126">*継続的なフィードバック:* ユーザーがターゲットを見つめ続けている間、継続進行状況インジケーターが表示されるので、ユーザーはそのターゲットを見つめ続ける必要があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="81a28-126">*Continuous Feedback:* While the user keeps looking at the target, show a continuous progress indicator so that the user knows that they have to keep looking at the target.</span></span> <span data-ttu-id="81a28-127">特に目の視線入力の場合は、大きめの円や球がまず表示され、その円や球が収縮して小さくなるようにすることにより、_ユーザーの視覚的注意を引く_ ことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="81a28-127">In particular for eye-gaze input, we recommend _pulling in the user's visual attention_ by starting out with a bigger circle or sphere that contracts into a smaller version.</span></span> <span data-ttu-id="81a28-128">最終状態 (小さい円) のインジケーターを表示することで、ドウェルが完了するタイミングをユーザーに知らせることができます。</span><span class="sxs-lookup"><span data-stu-id="81a28-128">Showing an indicator for the final state (small circle) helps to communicate to the user when the dwell will be finished.</span></span> <span data-ttu-id="81a28-129">サンプル図を次に示します。</span><span class="sxs-lookup"><span data-stu-id="81a28-129">An example illustration is shown below.</span></span> 
4. <span data-ttu-id="81a28-130">*完了:* ユーザーがターゲットを注視し続けると (さらに 650 から 850 ミリ秒)、ドウェルのアクティブ化が完了し、見つめていたターゲットが選択されます。</span><span class="sxs-lookup"><span data-stu-id="81a28-130">*Finish:* If the user kept fixating the target (for another 650-850 ms), complete the dwell activation and select the looked-at target.</span></span>

![ドウェルの状態](images/eyes_dwellstate_recommendation.png)<br>

## <a name="see-also"></a><span data-ttu-id="81a28-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="81a28-132">See also</span></span>
* [<span data-ttu-id="81a28-133">視線追跡</span><span class="sxs-lookup"><span data-stu-id="81a28-133">Eye tracking</span></span>](eye-tracking.md)
* [<span data-ttu-id="81a28-134">目の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="81a28-134">Eye-gaze and commit</span></span>](gaze-and-commit-eyes.md)
* [<span data-ttu-id="81a28-135">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="81a28-135">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="81a28-136">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="81a28-136">Gaze and dwell</span></span>](gaze-and-dwell.md)
* [<span data-ttu-id="81a28-137">音声入力</span><span class="sxs-lookup"><span data-stu-id="81a28-137">Voice input</span></span>](../out-of-scope/voice-design.md)
