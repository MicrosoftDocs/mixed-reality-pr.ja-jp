---
title: ハンド メニュー
description: メニューを使用すると、ユーザーは頻繁に使用される関数のための直接の UI をすぐに表示できます。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: ハンド、メニュー、ボタン、クイックアクセス、レイアウト、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 77df5974f54323310a696ed6630fbdde0b0faeb0
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847798"
---
# <a name="hand-menu"></a><span data-ttu-id="60e14-104">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="60e14-104">Hand menu</span></span>

![Ulnar side location](images/UX_Hero_HandMenu.jpg)

<span data-ttu-id="60e14-106">このメニューは、HoloLens 2 の最も一意な UX パターンの1つです。</span><span class="sxs-lookup"><span data-stu-id="60e14-106">The hand menu is one of the most unique UX patterns in HoloLens 2.</span></span> <span data-ttu-id="60e14-107">これにより、ハンドアタッチされた UI をすばやく表示できます。</span><span class="sxs-lookup"><span data-stu-id="60e14-107">It allows you to quickly bring up hand-attached UI.</span></span> <span data-ttu-id="60e14-108">いつでもアクセスできるため、簡単に表示および非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="60e14-108">Since it's accessible anytime and can be shown and hidden easily, it's great for quick actions.</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

<span data-ttu-id="60e14-109">以下の一覧で、メニューを使用するための推奨されるベストプラクティスを紹介します。</span><span class="sxs-lookup"><span data-stu-id="60e14-109">You'll find our recommended best practices for working with hand menus in the list below.</span></span> <span data-ttu-id="60e14-110">また、 [Mrtk](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)の手の形を示すシーンの例も見つかります。</span><span class="sxs-lookup"><span data-stu-id="60e14-110">You can also find an example scene demonstrating the hand menu in [MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html).</span></span>

<br>

---

## <a name="best-practices"></a><span data-ttu-id="60e14-111">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="60e14-111">Best practices</span></span>

<span data-ttu-id="60e14-112">**ボタンの数を小さくする**</span><span class="sxs-lookup"><span data-stu-id="60e14-112">**Keep the number of buttons small**</span></span> 

<span data-ttu-id="60e14-113">ハンドロックされたメニューと目の間には距離が近づいており、ユーザーがいつでも比較的小さな視覚面に焦点を当てる傾向があるため (attentional コーンは約10度)、ボタンの数を小さくすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="60e14-113">Because of the close distance between a hand-locked menu and the eyes, and the tendency for users to focus on a relatively small visual area at any time (the attentional cone of vision is roughly 10 degrees), we recommend keeping the number of buttons small.</span></span> <span data-ttu-id="60e14-114">この探索に基づいて、3つのボタンがある1つの列は、ユーザーが視界の中央に移動した場合でも、ビューのフィールド (視界) 内のすべてのコンテンツを保持することで効果的に機能します。</span><span class="sxs-lookup"><span data-stu-id="60e14-114">Based on our exploration, one column with three buttons works well by keeping all the content within the field of view (FOV) even when a user moves their hands to the center of the FOV.</span></span> 

<span data-ttu-id="60e14-115">**クイックアクションにハンドメニューを使用する**</span><span class="sxs-lookup"><span data-stu-id="60e14-115">**Use hand menu for quick action**</span></span> 

<span data-ttu-id="60e14-116">Arm を持ち上げて位置を維持すると、arm の疲労が簡単に生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="60e14-116">Raising an arm and maintaining the position could easily cause arm fatigue.</span></span> <span data-ttu-id="60e14-117">短い対話を必要とするメニューには、ハンドロックされたメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="60e14-117">Use a hand-locked method for the menu requiring a short interaction.</span></span> <span data-ttu-id="60e14-118">メニューが複雑で、対話時間の延長が必要な場合は、代わりにワールドロックまたは本体ロックを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="60e14-118">If your menu is complex and requires extended interaction times, consider using world-locked or body-locked instead.</span></span> 

<span data-ttu-id="60e14-119">**ボタン/パネルの角度**</span><span class="sxs-lookup"><span data-stu-id="60e14-119">**Button / Panel angle**</span></span>

<span data-ttu-id="60e14-120">メニューは、両端が反対のショルダーと真ん中になるようにする必要があります。これにより、自然な移動は反対の手でメニューと対話し、ボタンをタッチするときに不快または不快な針を回避できます。</span><span class="sxs-lookup"><span data-stu-id="60e14-120">Menus should billboard towards the opposite shoulder and middle of the head: This allows a natural hand move to interact with the menu with the opposite hand and avoids any awkward or uncomfortable hand positions when touching buttons.</span></span> 

<span data-ttu-id="60e14-121">**1ききまたはハンズフリー操作のサポートを検討する**</span><span class="sxs-lookup"><span data-stu-id="60e14-121">**Consider supporting one-handed or hands-free operation**</span></span>

<span data-ttu-id="60e14-122">両方のユーザーが常に使用できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="60e14-122">Don't assume both of the user's hands are always available.</span></span> <span data-ttu-id="60e14-123">一方または両方のハンズが使用できない場合は、さまざまなコンテキストを検討し、そのような状況に合わせて設計アカウントを確認します。</span><span class="sxs-lookup"><span data-stu-id="60e14-123">Consider a wide range of contexts when one or both hands aren't available, and make sure your design accounts for those situations.</span></span> <span data-ttu-id="60e14-124">片手メニューをサポートするには、手動でロックしたときに、メニューの配置を手動でロックしてみてください。</span><span class="sxs-lookup"><span data-stu-id="60e14-124">To support a one-handed hand menu, you can try transitioning the menu placement from hand-locked to world-locked when the hand flips (goes palm down).</span></span> <span data-ttu-id="60e14-125">ハンドフリーのシナリオでは、音声コマンドを使用して手の形のメニューを呼び出すことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="60e14-125">For hands-free scenarios, consider using a voice command to invoke the hand menu.</span></span>

<span data-ttu-id="60e14-126">**手首 (システムホームボタン) の近くにボタンが追加されないようにする**</span><span class="sxs-lookup"><span data-stu-id="60e14-126">**Avoid adding buttons near the wrist (system home button)**</span></span>

<span data-ttu-id="60e14-127">手の形のボタンが [ホーム] ボタンの近くに置かれている場合は、メニューを操作しているときに誤ってトリガーされることがあります。</span><span class="sxs-lookup"><span data-stu-id="60e14-127">If the hand menu buttons are placed too close to the home button, it may accidentally trigger while interacting with the hand menu.</span></span>

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a><span data-ttu-id="60e14-128">大規模で複雑な UI コントロールを持つ手のメニュー</span><span class="sxs-lookup"><span data-stu-id="60e14-128">Hand menu with large and complex UI controls</span></span>

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
<span data-ttu-id="60e14-129">手動でアタッチしたメニューでは、ボタンまたは UI コントロールの数を制限することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="60e14-129">It's recommended to limit the number of buttons or UI controls on hand-attached menus.</span></span> <span data-ttu-id="60e14-130">これは、多数の UI 要素との拡張操作によって arm の疲労が発生する可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="60e14-130">This is because extended interaction with a large number of UI elements can cause arm fatigue.</span></span> <span data-ttu-id="60e14-131">エクスペリエンスに大きなメニューが必要な場合は、ユーザーがメニューをロックするための簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="60e14-131">If your experience requires a large menu, provide an easy way for the user to world lock the menu.</span></span> <span data-ttu-id="60e14-132">1つの方法として、ユーザーを手に入れたり、逆にしたりするときに、メニューを使うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="60e14-132">One technique we recommend is to world-lock then menu when the hand drops or flips away from the user.</span></span> <span data-ttu-id="60e14-133">もう1つの方法は、ユーザーが直接メニューを取得できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="60e14-133">A second technique is to allow the user to directly grab the menu with the other hand.</span></span> <span data-ttu-id="60e14-134">ユーザーがメニューを離すと、メニューがロックされます。</span><span class="sxs-lookup"><span data-stu-id="60e14-134">When the user releases the menu, the menu should world lock.</span></span> <span data-ttu-id="60e14-135">こうすることで、ユーザーはさまざまな UI 要素との対話を長時間にわたって容易に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="60e14-135">This way, a user can interact with various UI elements comfortably and confidently over an extended period of time.</span></span> 

<span data-ttu-id="60e14-136">メニューが世界中にロックされている場合は、メニューを移動する方法を用意して、不要になったときにメニューを閉じるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="60e14-136">When the menu is world-locked, make sure to provide a way to move the menu, and close the menu when it's no longer needed.</span></span> <span data-ttu-id="60e14-137">メニューの横または上部にハンドルを入力して、メニューを移動できるようにします。</span><span class="sxs-lookup"><span data-stu-id="60e14-137">Make the menu movable by providing handles on the sides or top of menu.</span></span> <span data-ttu-id="60e14-138">[閉じる] ボタンを追加して、メニューを閉じることができるようにします。</span><span class="sxs-lookup"><span data-stu-id="60e14-138">Add a close button to allow the menu to close.</span></span> <span data-ttu-id="60e14-139">ユーザーがユーザーを手にしたときに、メニューを手動で再アタッチできるようにします。</span><span class="sxs-lookup"><span data-stu-id="60e14-139">Allow for the menu to reattach to the hand when the user hand faces the user.</span></span> <span data-ttu-id="60e14-140">また、誤ったアクティベーションを防ぐために、ユーザーの手を見つめておくことをお勧めします (下記参照)。</span><span class="sxs-lookup"><span data-stu-id="60e14-140">We also recommend requiring that the users gaze at their hand to prevent false activations (see below).</span></span>

<span data-ttu-id="60e14-141">**ユーザビリティの問題を示す大きなメニュー**</span><span class="sxs-lookup"><span data-stu-id="60e14-141">**Large menu that shows a usability issue**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

<span data-ttu-id="60e14-142">**手の形でロックされたメニュー**</span><span class="sxs-lookup"><span data-stu-id="60e14-142">**World-locked menu on hand drop**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

<span data-ttu-id="60e14-143">**手動によるグラブ & [ワールドにプル]-メニューをロックする**</span><span class="sxs-lookup"><span data-stu-id="60e14-143">**Manual grab & pull to world-lock the menu**</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a><span data-ttu-id="60e14-144">偽のアクティベーションを防止する方法</span><span class="sxs-lookup"><span data-stu-id="60e14-144">How to prevent false activation</span></span>

<span data-ttu-id="60e14-145">ポップアップをイベントとしてのみ使用して、メニューをトリガーすると、不要になったときに誤って表示されることがあります (偽陽性)。これは、ユーザーが (通信とオブジェクトの操作のために) 意図的に移動し、意図せずに移動するためです。</span><span class="sxs-lookup"><span data-stu-id="60e14-145">If you use just palm-up as an event to trigger the hand menu, it may accidentally appear when you don't need it (false-positive), because people move their hands both intentionally (for communication and object manipulation) and unintentionally.</span></span> <span data-ttu-id="60e14-146">偽のライセンス認証を減らすには、手のひらイベント以外に追加の手順を追加して、手のひら (完全に開いた指など) を呼び出すか、ユーザーが意図的に整理します。</span><span class="sxs-lookup"><span data-stu-id="60e14-146">To reduce false activations, add an extra step besides the palm-up event to invoke the hand menu (such as fully opened fingers, or the user intentionally gazing at their hand).</span></span>

<span data-ttu-id="60e14-147">**フラットなパームが必要**</span><span class="sxs-lookup"><span data-stu-id="60e14-147">**Require Flat Palm**</span></span>

<span data-ttu-id="60e14-148">フラットなオープンハンドを要求することで、ユーザーが環境内で通信中にオブジェクトやジェスチャを操作するときに、偽のアクティブ化を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="60e14-148">By requiring a flat open hand, you can prevent false activation that might occur as the user manipulates objects or gestures while communicating within an environment.</span></span> 

<span data-ttu-id="60e14-149">**宝石が必要**</span><span class="sxs-lookup"><span data-stu-id="60e14-149">**Require Gaze**</span></span>

<span data-ttu-id="60e14-150">ユーザーが自分の手を見つめ (目を見つめているか、頭を見つめている) ことを要求することによって、誤ったライセンス認証を防ぐことができます。これは、ユーザーが補助的なアクティブ化の手順として手動で注意を向ける必要があるためです</span><span class="sxs-lookup"><span data-stu-id="60e14-150">By requiring the user to gaze at their hand (either with eye gaze or head gaze), it prevents false activations because of the user having to direct their attention to the hand as a secondary activation step (with a tunable distance threshold used to allow for user comfort).</span></span>  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a><span data-ttu-id="60e14-151">手動によるメニューの配置のベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="60e14-151">Hand menu placement best practices</span></span>

<span data-ttu-id="60e14-152">人間の構造では、ulnar は ulnar のボーンの近くで実行されます。</span><span class="sxs-lookup"><span data-stu-id="60e14-152">In human anatomy, the ulnar nerve is a nerve that runs near the ulna bone.</span></span> <span data-ttu-id="60e14-153">Ulna は、l 肘から最小の指まで伸縮する長い骨の中にあります。</span><span class="sxs-lookup"><span data-stu-id="60e14-153">The ulna is a long bone found in the forearm that stretches from the elbow to the smallest finger.</span></span>

<span data-ttu-id="60e14-154">次に、探索に基づく2つの推奨される配置を示します。</span><span class="sxs-lookup"><span data-stu-id="60e14-154">Below are two recommended placements based on our explorations:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="60e14-155">![パーム内の ulnar の針](images/UlnarSideHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="60e14-155">![Ulnar side hand location inside palm](images/UlnarSideHandMenu.gif)</span></span><br>
        <span data-ttu-id="60e14-156">**Palm 内部の Ulnar**</span><span class="sxs-lookup"><span data-stu-id="60e14-156">**A. Ulnar inside palm**</span></span><br>
        <span data-ttu-id="60e14-157">この位置は、互いに重ならないため、信頼性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="60e14-157">This position is reliable because the hands don't overlap each other.</span></span> <span data-ttu-id="60e14-158">これは、正確な手動検出と追跡に不可欠です。</span><span class="sxs-lookup"><span data-stu-id="60e14-158">This is critical for accurate hand detection and tracking.</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="60e14-159">![手動での ulnar の位置](images/UlnarAboveHandMenu.gif)</span><span class="sxs-lookup"><span data-stu-id="60e14-159">![Ulnar side hand location above hand](images/UlnarAboveHandMenu.gif)</span></span><br>
        <span data-ttu-id="60e14-160">**B. Ulnar (手動)**</span><span class="sxs-lookup"><span data-stu-id="60e14-160">**B. Ulnar above hand**</span></span><br>
        <span data-ttu-id="60e14-161">この場所はユーザーにとって使いやすいものです。ユーザーは arm を起動して、手のメニューと対話する必要がないからです。</span><span class="sxs-lookup"><span data-stu-id="60e14-161">This location is comfortable for users because they don't need to raise their arm too much to interact with the hand menu.</span></span> <span data-ttu-id="60e14-162">メニュー **13 cm** をパームの上に配置し、ボタンを ulnar palm 内に配置することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="60e14-162">We recommend placing menus **13 cm** above the palm and align the buttons inside the ulnar palm.</span></span> [<span data-ttu-id="60e14-163">最適なボタンサイズの詳細を確認する</span><span class="sxs-lookup"><span data-stu-id="60e14-163">Read more about the optimal button size</span></span>](interactable-object.md)<br>
        <br>
        <span data-ttu-id="60e14-164">技術的な理由から、この場所には、必要な実装を1つ用意することをお勧めします。開発者は、ユーザーの反対側がこのメニューを操作するために終了した後に、メニューを固定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="60e14-164">For technical reasons, we recommend this location with one required implementation: the developer will need to freeze the menu once the user's opposite hand gets close to interacting with it.</span></span> <span data-ttu-id="60e14-165">これにより、jitteriness が重複しないようにすることができ、ボタンをより高速にターゲット設定できるようになります。</span><span class="sxs-lookup"><span data-stu-id="60e14-165">This will avoid jitteriness from overlapping hands and also allows for a faster targeting of the buttons.</span></span><br>
        <br>
        <span data-ttu-id="60e14-166">HoloLens 2 カメラは、互いに独立しているときに正確に識別します。</span><span class="sxs-lookup"><span data-stu-id="60e14-166">HoloLens 2 cameras identify hands accurately when they're separate from each other.</span></span> <span data-ttu-id="60e14-167">両手が重なると、メニューがアンカー位置から離れてしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="60e14-167">Any overlapping hands can cause hand menus move away from the anchor location.</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a><span data-ttu-id="60e14-168">推奨されていないメニュー位置</span><span class="sxs-lookup"><span data-stu-id="60e14-168">Menu positions that aren't recommended</span></span>

<span data-ttu-id="60e14-169">さまざまなメニューのレイアウトや場所を使用したユーザーの調査を行っていますが、次のメニューの場所は推奨されて **いません**。以下の各研究の欠点を確認してください。</span><span class="sxs-lookup"><span data-stu-id="60e14-169">We have done user research with different menus layouts and locations, the following menu locations are **NOT recommended**, find the cons of each study below:</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="60e14-170">![Arm より上](images/AboveArm.gif)</span><span class="sxs-lookup"><span data-stu-id="60e14-170">![Above arm](images/AboveArm.gif)</span></span><br>
        <span data-ttu-id="60e14-171">**Arm の上**</span><span class="sxs-lookup"><span data-stu-id="60e14-171">**Above the arm**</span></span><br>
        <span data-ttu-id="60e14-172">1-適切な追跡を維持することが困難</span><span class="sxs-lookup"><span data-stu-id="60e14-172">1 - Difficult to maintain good hand tracking</span></span><br>
        <span data-ttu-id="60e14-173">2-不自然な位置が原因でユーザーの疲労が発生する</span><span class="sxs-lookup"><span data-stu-id="60e14-173">2 - Causes user fatigue because of unnatural position</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="60e14-174">![上の指](images/AboveFingers.gif)</span><span class="sxs-lookup"><span data-stu-id="60e14-174">![Above fingers](images/AboveFingers.gif)</span></span><br>
        <span data-ttu-id="60e14-175">**上の指**</span><span class="sxs-lookup"><span data-stu-id="60e14-175">**Above fingers**</span></span><br>
        <span data-ttu-id="60e14-176">長い時間が経過しているため、1ハンドの疲労</span><span class="sxs-lookup"><span data-stu-id="60e14-176">1 - Hand fatigue because of holding out hand for a long time</span></span><br>
        <span data-ttu-id="60e14-177">インデックスと中段指に関する2つの問題の追跡</span><span class="sxs-lookup"><span data-stu-id="60e14-177">2 - Hand tracking issues on index and middle fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="60e14-178">![中央の上にあるパーム](images/handCenter.gif)</span><span class="sxs-lookup"><span data-stu-id="60e14-178">![Above center palm](images/handCenter.gif)</span></span><br>
        <span data-ttu-id="60e14-179">**上-中央のパーム**</span><span class="sxs-lookup"><span data-stu-id="60e14-179">**Above-center palm**</span></span><br>
        <span data-ttu-id="60e14-180">1つは、重複することによる問題の追跡です。</span><span class="sxs-lookup"><span data-stu-id="60e14-180">1 - Hand tracking issues because of overlapping hands</span></span><br>
        <span data-ttu-id="60e14-181">メニューとの対話に時間がかかるため、2ハンドの疲労</span><span class="sxs-lookup"><span data-stu-id="60e14-181">2 - Hand fatigue because of holding hands for long time to interact with menus</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="60e14-182">![Top 指先 ](images/TopFingerTip.gif) **top 指先**</span><span class="sxs-lookup"><span data-stu-id="60e14-182">![Top Fingertip](images/TopFingerTip.gif) **Top fingertip**</span></span><br>
        <span data-ttu-id="60e14-183">1ハンドトラッキングの問題</span><span class="sxs-lookup"><span data-stu-id="60e14-183">1 - Hand tracking issues</span></span><br>
        <span data-ttu-id="60e14-184">通常の姿勢を超えたままの2ハンドの疲労</span><span class="sxs-lookup"><span data-stu-id="60e14-184">2 - Hand fatigue from holding hand above normal posture</span></span><br>
        <span data-ttu-id="60e14-185">3-指の間にスペースが限られているため、偶発的に他の指でボタンを押す問題</span><span class="sxs-lookup"><span data-stu-id="60e14-185">3 - Issues pressing buttons with other fingers by accident because of limited space between fingers</span></span>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        <span data-ttu-id="60e14-186">![Arm の背面](images/BackOfTheArm.gif)</span><span class="sxs-lookup"><span data-stu-id="60e14-186">![Back of the Arm](images/BackOfTheArm.gif)</span></span><br>
        <span data-ttu-id="60e14-187">**Arm の背面**</span><span class="sxs-lookup"><span data-stu-id="60e14-187">**Back of the arm**</span></span><br>
        <span data-ttu-id="60e14-188">1-事故によってホームボタンをトリガーできる</span><span class="sxs-lookup"><span data-stu-id="60e14-188">1 - Can trigger home button by accident</span></span><br>
        <span data-ttu-id="60e14-189">2-自然または快適な位置</span><span class="sxs-lookup"><span data-stu-id="60e14-189">2 - Not a natural or comfortable position</span></span>
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="60e14-190">Unity の MRTK (Mixed Reality Toolkit) の手の形のメニュー</span><span class="sxs-lookup"><span data-stu-id="60e14-190">Hand menu in MRTK (Mixed Reality Toolkit) for Unity</span></span>

<span data-ttu-id="60e14-191">**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、ハンドメニューのスクリプトとサンプルシーンが用意されています。</span><span class="sxs-lookup"><span data-stu-id="60e14-191">**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** provides scripts and example scenes for the hand menu.</span></span> <span data-ttu-id="60e14-192">HandConstraintPalmUp ソルバースクリプトを使用すると、さまざまな構成可能なオプションを使用して、任意のオブジェクトをハンドにアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="60e14-192">The HandConstraintPalmUp solver script allows you to attach any objects to the hands with various configurable options.</span></span> <span data-ttu-id="60e14-193">MRTK の手の形のメニューの例には、誤ったアクティベーションを防止するためのフラットなパームや宝石の要件などの便利なオプションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="60e14-193">MRTK's hand menu examples include useful options such as flat palm and gaze requirement for preventing false activation.</span></span>

* [<span data-ttu-id="60e14-194">ハンドメニュードキュメント</span><span class="sxs-lookup"><span data-stu-id="60e14-194">Hand Menu Documentations</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [<span data-ttu-id="60e14-195">ハンドメニューのシーンの例</span><span class="sxs-lookup"><span data-stu-id="60e14-195">Hand Menu Example Scene</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

<span data-ttu-id="60e14-196">MRTK サンプルハブアプリを使用して、HoloLens 2 でメニューの例を試すことができます。</span><span class="sxs-lookup"><span data-stu-id="60e14-196">You can try hand menu examples in HoloLens 2 with MRTK Examples Hub app.</span></span> 
* [<span data-ttu-id="60e14-197">MRTK サンプルハブの手メニューシーン</span><span class="sxs-lookup"><span data-stu-id="60e14-197">Hand Menu Scene in MRTK Examples Hub</span></span>](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a><span data-ttu-id="60e14-198">関連項目</span><span class="sxs-lookup"><span data-stu-id="60e14-198">See also</span></span>

* [<span data-ttu-id="60e14-199">カーソル</span><span class="sxs-lookup"><span data-stu-id="60e14-199">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="60e14-200">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="60e14-200">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="60e14-201">ボタン</span><span class="sxs-lookup"><span data-stu-id="60e14-201">Button</span></span>](button.md)
* [<span data-ttu-id="60e14-202">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="60e14-202">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="60e14-203">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="60e14-203">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="60e14-204">操作</span><span class="sxs-lookup"><span data-stu-id="60e14-204">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="60e14-205">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="60e14-205">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="60e14-206">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="60e14-206">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="60e14-207">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="60e14-207">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="60e14-208">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="60e14-208">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="60e14-209">キーボード</span><span class="sxs-lookup"><span data-stu-id="60e14-209">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="60e14-210">ヒント</span><span class="sxs-lookup"><span data-stu-id="60e14-210">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="60e14-211">スレート</span><span class="sxs-lookup"><span data-stu-id="60e14-211">Slate</span></span>](slate.md)
* [<span data-ttu-id="60e14-212">スライダー</span><span class="sxs-lookup"><span data-stu-id="60e14-212">Slider</span></span>](slider.md)
* [<span data-ttu-id="60e14-213">シェーダー</span><span class="sxs-lookup"><span data-stu-id="60e14-213">Shader</span></span>](shader.md)
* [<span data-ttu-id="60e14-214">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="60e14-214">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="60e14-215">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="60e14-215">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="60e14-216">表面吸着</span><span class="sxs-lookup"><span data-stu-id="60e14-216">Surface magnetism</span></span>](surface-magnetism.md)
