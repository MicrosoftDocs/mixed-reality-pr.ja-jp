---
title: ケーススタディ-3 HoloStudio UI と相互作用設計学習
description: HoloStudio UI と操作設計の学習
author: rwinj
ms.author: marcghal
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens、HoloStudio、Windows Mixed Reality
ms.openlocfilehash: 55fc9cea93582612abb5e0f8955deb5629da3093
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687586"
---
# <a name="case-study---3-holostudio-ui-and-interaction-design-learnings"></a><span data-ttu-id="f7d30-104">ケーススタディ-3 HoloStudio UI と相互作用設計学習</span><span class="sxs-lookup"><span data-stu-id="f7d30-104">Case study - 3 HoloStudio UI and interaction design learnings</span></span>

<span data-ttu-id="f7d30-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) は、HoloLens 用の最初の Microsoft アプリの1つでした。</span><span class="sxs-lookup"><span data-stu-id="f7d30-105">[HoloStudio](https://www.youtube.com/watch?v=BRIJG0x_We8) was one of the first Microsoft apps for HoloLens.</span></span> <span data-ttu-id="f7d30-106">このため、3D UI と対話デザインのための新しいベストプラクティスを作成する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="f7d30-106">Because of this, we had to create new best practices for 3D UI and interaction design.</span></span> <span data-ttu-id="f7d30-107">これは、多数のユーザーテスト、プロトタイプ、および試用とエラーによって行われました。</span><span class="sxs-lookup"><span data-stu-id="f7d30-107">We did this through a lot of user testing, prototyping, and trial and error.</span></span>

<span data-ttu-id="f7d30-108">私たちは、この種の調査を行うためのリソースがすべてのユーザーに提供されているわけではありません。 Holographic Designer、Marcus Ghaly、HoloStudio の開発中に学習した3つのことを、HoloLens アプリの UI と相互作用設計について共有しています。</span><span class="sxs-lookup"><span data-stu-id="f7d30-108">We know that not everyone has the resources at their disposal to do this type of research, so we had our Sr. Holographic Designer, Marcus Ghaly, share three things we learned during the development of HoloStudio about UI and interaction design for HoloLens apps.</span></span>

## <a name="watch-the-video"></a><span data-ttu-id="f7d30-109">ビデオを見る</span><span class="sxs-lookup"><span data-stu-id="f7d30-109">Watch the video</span></span>

>[!VIDEO https://www.youtube.com/embed/sX6yKHmN1qM]

## <a name="problem-1-people-didnt-want-to-move-around-their-creations"></a><span data-ttu-id="f7d30-110">問題 #1: ユーザーの作成を避けたい</span><span class="sxs-lookup"><span data-stu-id="f7d30-110">Problem #1: People didn't want to move around their creations</span></span>

<span data-ttu-id="f7d30-111">最初は、現実の世界で見たように、HoloStudio でワークベンチを四角形として設計しました。</span><span class="sxs-lookup"><span data-stu-id="f7d30-111">We originally designed the workbench in HoloStudio as a rectangle, much like you'd find in the real world.</span></span> <span data-ttu-id="f7d30-112">問題は、ユーザーが席に座っているときや、コンピューターの前に座っているときでも、ワークベンチを動かさずに3D の作成を調べることができなかったことを示す、経験のある期間があることです。</span><span class="sxs-lookup"><span data-stu-id="f7d30-112">The problem is that people have a lifetime of experience that tells them to stay still when they're sitting at a desk or working in front of a computer, so they weren't moving around the workbench and exploring their 3D creation from all sides.</span></span>

![HoloStudio dissuaded のワークベンチの四角形のデザインは、すべての側からの作成を左右に移動できません。](images/rectangular-workbench-500px.jpg)

<span data-ttu-id="f7d30-114">私たちは、ワークベンチを丸めるための洞察を得ました。これにより、"正面" や明確な場所がなくなります。</span><span class="sxs-lookup"><span data-stu-id="f7d30-114">We had the insight to make the workbench round, so that there was no "front" or clear place that you were supposed to stand.</span></span> <span data-ttu-id="f7d30-115">これをテストしたところ、突然のユーザーが自分で開発を行ってきました。</span><span class="sxs-lookup"><span data-stu-id="f7d30-115">When we tested this, suddenly people started moving around and exploring their creations on their own.</span></span>

![円形ワークベンチの設計では、ユーザーの作成をすべての方法で行うことをお勧めします。](images/circular-workbench-500px.jpg)

<span data-ttu-id="f7d30-117">**学習内容**</span><span class="sxs-lookup"><span data-stu-id="f7d30-117">**What we learned**</span></span>

<span data-ttu-id="f7d30-118">常に、ユーザーにとって快適なことを考えてください。</span><span class="sxs-lookup"><span data-stu-id="f7d30-118">Always be thinking about what's comfortable for the user.</span></span> <span data-ttu-id="f7d30-119">これらの物理領域を利用することは、HoloLens の優れた機能であり、他のデバイスでは実行できないものです。</span><span class="sxs-lookup"><span data-stu-id="f7d30-119">Taking advantage of their physical space is a cool feature of HoloLens and something you can't do with other devices.</span></span>

## <a name="problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame"></a><span data-ttu-id="f7d30-120">問題 #2: モーダルダイアログが holographic フレームの外になることがあります。</span><span class="sxs-lookup"><span data-stu-id="f7d30-120">Problem #2: Modal dialogs are sometimes out of the holographic frame</span></span>

<span data-ttu-id="f7d30-121">場合によっては、ユーザーがアプリで注意する必要があるものとは異なる方向を探すことがあります。</span><span class="sxs-lookup"><span data-stu-id="f7d30-121">Sometimes, your user may be looking in a different direction from something that needs their attention in your app.</span></span> <span data-ttu-id="f7d30-122">PC では、ダイアログをポップアップするだけで済みますが、3D 環境で他のユーザーの顔でこの操作を行うと、ダイアログが表示されているように感じられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f7d30-122">On a PC, you can just pop up a dialog, but if you do this in someone's face in a 3D environment, it can feel like the dialog is getting in their way.</span></span> <span data-ttu-id="f7d30-123">メッセージを読み取るために必要ですが、性質はそのメッセージを取得しようとしています。</span><span class="sxs-lookup"><span data-stu-id="f7d30-123">You need them to read the message, but their instinct is to try to get away from it.</span></span> <span data-ttu-id="f7d30-124">この反応はゲームをプレイしている場合には非常に便利ですが、作業用に設計されたツールでは理想的とは言えません。</span><span class="sxs-lookup"><span data-stu-id="f7d30-124">This reaction is great if you're playing a game, but in a tool designed for work, it's less than ideal.</span></span>

<span data-ttu-id="f7d30-125">いくつかの点を試した後、最終的には、ダイアログの "思考バブル" システムを使用して、ユーザーがアプリケーションで注意が必要な箇所に従うことができる tendrils を追加しました。</span><span class="sxs-lookup"><span data-stu-id="f7d30-125">After trying a few different things, we finally settled on using a "thought bubble" system for our dialogs and added tendrils that users can follow to where their attention is needed in our application.</span></span> <span data-ttu-id="f7d30-126">また、tendrils のパルスも作成しました。これは、ユーザーがどこに移動するかを把握できるように、方向性の意味を暗示しています。</span><span class="sxs-lookup"><span data-stu-id="f7d30-126">We also made the tendrils pulse, which implied a sense of directionality so that users knew where to go.</span></span>

!["思考バブル" システムには、方向を意味する発する tendrils が含まれていました。これは、アプリでの注意が必要な場所をユーザーに導きます。](images/thought-bubble-500px.jpg)

<span data-ttu-id="f7d30-128">**学習内容**</span><span class="sxs-lookup"><span data-stu-id="f7d30-128">**What we learned**</span></span>

<span data-ttu-id="f7d30-129">3D では、ユーザーに注意を払う必要があることを警告するのは非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="f7d30-129">It's much harder in 3D to alert users to things they need to pay attention to.</span></span> <span data-ttu-id="f7d30-130">[空間サウンド](../design/spatial-sound.md)、光線、または思考バブルなどのアテンションダイレクタを使用すると、ユーザーが必要な場所に移動する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f7d30-130">Using attention directors such as [spatial sound](../design/spatial-sound.md), light rays, or thought bubbles, can lead users to where they need to be.</span></span>

## <a name="problem-3-sometimes-ui-can-get-blocked-by-other-holograms"></a><span data-ttu-id="f7d30-131">問題 #3: 他のホログラムによって UI がブロックされることがある</span><span class="sxs-lookup"><span data-stu-id="f7d30-131">Problem #3: Sometimes UI can get blocked by other holograms</span></span>

<span data-ttu-id="f7d30-132">ユーザーがホログラムとそれに関連付けられた UI コントロールを操作しようとしていても、別のホログラムが前面にあるためにビューがブロックされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f7d30-132">There are times when a user wants to interact with a hologram and its associated UI controls, but they are blocked from view because another hologram is in front of them.</span></span> <span data-ttu-id="f7d30-133">HoloStudio の開発中に、試用版とエラーを使用して、このソリューションを提供しました。</span><span class="sxs-lookup"><span data-stu-id="f7d30-133">While we were developing HoloStudio, we used trial and error to come to a solution for this.</span></span>

![ホログラムに関連付けられている UI コントロールは、それとユーザーが装着した HoloLens の間に別のホログラムがある場合、ブロックされる可能性があります。](images/ui-blocked-500px.jpg)

<span data-ttu-id="f7d30-135">UI コントロールはユーザーの近くに移動しようとしました。ブロックされることはありませんでしたが、ユーザーは、遠くにいるホログラムを同時に見ている間に、ユーザーが自分の近くにいたコントロールを見ても慣れていないことがわかりました。</span><span class="sxs-lookup"><span data-stu-id="f7d30-135">We tried moving the UI control closer to the user so it couldn't get blocked, but found that it wasn't comfortable for the user to look at a control that was near to you while simultaneously looking at a hologram that was far away.</span></span> <span data-ttu-id="f7d30-136">ただし、最も近いホログラムの前にあるコントロールをユーザーに移動した場合は、影響を受けているホログラムから切り離されているように感じられます。</span><span class="sxs-lookup"><span data-stu-id="f7d30-136">If, however, we moved the control in front of the closest hologram to the user, they felt like it was detached from the hologram it should be affecting.</span></span>

<span data-ttu-id="f7d30-137">最後に、UI コントロールのゴーストを終了し、ユーザーから関連付けられているホログラムと同じ距離に配置します。そのため、両方とも接続されています。</span><span class="sxs-lookup"><span data-stu-id="f7d30-137">We finally ended up ghosting the UI control, and put it at the same distance from the user as the hologram it's associated with, so they both feel connected.</span></span> <span data-ttu-id="f7d30-138">これにより、ユーザーは、隠されている場合でもコントロールを操作できます。</span><span class="sxs-lookup"><span data-stu-id="f7d30-138">This allows the user to interact with the control even though it's been obscured.</span></span>

![解決策: UI コントロールを非実体にします。このコントロールは、コントロールとの対話を許可し、それが影響を与えていたホログラムに接続するようにしました。](images/ghosting-ui-500px.jpg)

<span data-ttu-id="f7d30-140">**学習内容**</span><span class="sxs-lookup"><span data-stu-id="f7d30-140">**What we learned**</span></span>

<span data-ttu-id="f7d30-141">ユーザーは、ブロックされている場合でも UI コントロールに簡単にアクセスできる必要があります。そのため、ユーザーが自分のホログラムが実際のどこにあるかに関係なく、ユーザーがタスクを完了できるようにする方法を確認してください。</span><span class="sxs-lookup"><span data-stu-id="f7d30-141">Users need to be able to easily access UI controls even if they've been blocked, so figure out methods to ensure that users can complete their tasks no matter where their holograms are in the real world.</span></span>

## <a name="about-the-author"></a><span data-ttu-id="f7d30-142">著者について</span><span class="sxs-lookup"><span data-stu-id="f7d30-142">About the author</span></span>

<table style="border-collapse:collapse">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Marcus Ghaly" width="60" height="60" src="images/marcus-ghaly-200px.jpg"></td>
<td style="border-style: none"><span data-ttu-id="f7d30-143"><b>Marcus Ghaly</b></span><span class="sxs-lookup"><span data-stu-id="f7d30-143"><b>Marcus Ghaly</b></span></span><br><span data-ttu-id="f7d30-144">Holographic デザイナー @Microsoft</span><span class="sxs-lookup"><span data-stu-id="f7d30-144">Sr. Holographic Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="f7d30-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7d30-145">See also</span></span>
* [<span data-ttu-id="f7d30-146">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="f7d30-146">Instinctual interactions</span></span>](../design/interaction-fundamentals.md)
