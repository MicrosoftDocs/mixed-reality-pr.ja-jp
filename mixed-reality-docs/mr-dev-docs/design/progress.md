---
title: 進行状況を表示する
description: プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、コントロール、ui、ux、進行状況インジケーター、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 93cdd7054c05af9f8621e091fa3d4b59d9e65ee3
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703388"
---
# <a name="progress-indicator"></a><span data-ttu-id="99ef8-104">進捗状況インジケーター</span><span class="sxs-lookup"><span data-stu-id="99ef8-104">Progress indicator</span></span>

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="99ef8-105">プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。</span><span class="sxs-lookup"><span data-stu-id="99ef8-105">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="99ef8-106">使用されているインジケーターに応じて、進行状況インジケーターが表示されているときはユーザーはアプリを操作できないことを知らせたり、待ち時間の長さを示したりできます。</span><span class="sxs-lookup"><span data-stu-id="99ef8-106">It can mean that the user cannot interact with the app when the progress indicator is visible, and can also indicate how long the wait time might be, depending on the indicator used.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="99ef8-107">プログレス コントロールの種類</span><span class="sxs-lookup"><span data-stu-id="99ef8-107">Types of progress</span></span>

<span data-ttu-id="99ef8-108">何が起こっているかについてユーザー情報を提供することが重要です。</span><span class="sxs-lookup"><span data-stu-id="99ef8-108">It is important to provide the user information about what is happening.</span></span> <span data-ttu-id="99ef8-109">混合環境では、アプリから視覚的なフィードバックが得られない場合、ユーザーは物理環境またはオブジェクトによって簡単に気にすることができます。</span><span class="sxs-lookup"><span data-stu-id="99ef8-109">In mixed reality users can be easily distracted by physical environment or objects if your app does not gives good visual feedback.</span></span> <span data-ttu-id="99ef8-110">データが読み込まれたりシーンが更新されたりするなど、数秒かかる状況では、視覚的なインジケーターを表示することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="99ef8-110">For situations that take a few seconds, such when data is loading or a scene is updating, it is good idea to show a visual indicator.</span></span> <span data-ttu-id="99ef8-111">操作が進行しているユーザーを表示するには、 **進行状況バー** または **進行状況のリング** の2つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="99ef8-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="99ef8-112">進行状況バー</span><span class="sxs-lookup"><span data-stu-id="99ef8-112">Progress bar</span></span><br>
        <span data-ttu-id="99ef8-113">進行状況バーには、タスクの完了率が表示されます。</span><span class="sxs-lookup"><span data-stu-id="99ef8-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="99ef8-114">このメソッドは、期間が既知 (有限) の操作中に使用する必要がありますが、進行中のユーザーとアプリとの対話をブロックすることはできません。</span><span class="sxs-lookup"><span data-stu-id="99ef8-114">It should be used during an operation whose duration is known (determinate), but it's progress should not block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="99ef8-115">*イメージ: HoloLens での進行状況バーの例*</span><span class="sxs-lookup"><span data-stu-id="99ef8-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="99ef8-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="99ef8-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="99ef8-117">![HoloLens での進行状況バーの例](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="99ef8-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="99ef8-118">進行状況リング</span><span class="sxs-lookup"><span data-stu-id="99ef8-118">Progress ring</span></span><br>
        <span data-ttu-id="99ef8-119">進行状況のリングは不確定な状態であるため、操作が完了するまで他のユーザー操作がブロックされたときに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99ef8-119">A Progress ring only has an indeterminate state, and should be used when any further user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="99ef8-120">*イメージ: HoloLens での進行状況リングの例*</span><span class="sxs-lookup"><span data-stu-id="99ef8-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="99ef8-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="99ef8-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="99ef8-122">![HoloLens での進行状況リングの例](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="99ef8-122">![Progress ring example in HoloLens](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="99ef8-123">カスタムオブジェクトの進行状況</span><span class="sxs-lookup"><span data-stu-id="99ef8-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="99ef8-124">独自のカスタム 2D/3D オブジェクトを使用して進行状況の制御をカスタマイズすることで、アプリの個性とブランド id に追加できます。</span><span class="sxs-lookup"><span data-stu-id="99ef8-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="99ef8-125">*イメージ: HoloLens でのカスタムメッシュの例の進行状況*</span><span class="sxs-lookup"><span data-stu-id="99ef8-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="99ef8-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="99ef8-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="99ef8-127">![HoloLens でのカスタムメッシュの例の進行状況](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="99ef8-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="99ef8-128">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="99ef8-128">Best practices</span></span>
* <span data-ttu-id="99ef8-129">ユーザーが簡単にヘッドを空の領域に移動してコンテキストを失うことがあるため、 [billboarding またはタグ](billboarding-and-tag-along.md) を進行状況の表示に密に結合します。</span><span class="sxs-lookup"><span data-stu-id="99ef8-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="99ef8-130">ユーザーが何も表示できない場合、アプリがクラッシュしたように見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="99ef8-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="99ef8-131">Billboarding とタグは、進行状況の prefab に組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="99ef8-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="99ef8-132">ユーザーに対して何が起こっているかに関するステータス情報を常に提供するのが適切です。</span><span class="sxs-lookup"><span data-stu-id="99ef8-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="99ef8-133">Progress prefab には、状態を提供するための Windows 標準のリングの種類の進行状況など、さまざまな視覚スタイルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="99ef8-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="99ef8-134">また、進行状況のスタイルをアプリのブランドに合わせる必要がある場合は、アニメーションでカスタムメッシュを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="99ef8-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="99ef8-135">Unity 用 MRTK (Mixed Reality Toolkit) の進行状況インジケーター</span><span class="sxs-lookup"><span data-stu-id="99ef8-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="99ef8-136">MRTK-進行状況インジケーター prefabs</span><span class="sxs-lookup"><span data-stu-id="99ef8-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="99ef8-137">MRTK-シーン移行サービス</span><span class="sxs-lookup"><span data-stu-id="99ef8-137">MRTK - Scene transition service</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="99ef8-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="99ef8-138">See also</span></span>

* [<span data-ttu-id="99ef8-139">カーソル</span><span class="sxs-lookup"><span data-stu-id="99ef8-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="99ef8-140">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="99ef8-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="99ef8-141">ボタン</span><span class="sxs-lookup"><span data-stu-id="99ef8-141">Button</span></span>](button.md)
* [<span data-ttu-id="99ef8-142">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="99ef8-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="99ef8-143">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="99ef8-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="99ef8-144">操作</span><span class="sxs-lookup"><span data-stu-id="99ef8-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="99ef8-145">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="99ef8-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="99ef8-146">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="99ef8-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="99ef8-147">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="99ef8-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="99ef8-148">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="99ef8-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="99ef8-149">キーボード</span><span class="sxs-lookup"><span data-stu-id="99ef8-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="99ef8-150">ヒント</span><span class="sxs-lookup"><span data-stu-id="99ef8-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="99ef8-151">スレート</span><span class="sxs-lookup"><span data-stu-id="99ef8-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="99ef8-152">スライダー</span><span class="sxs-lookup"><span data-stu-id="99ef8-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="99ef8-153">シェーダー</span><span class="sxs-lookup"><span data-stu-id="99ef8-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="99ef8-154">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="99ef8-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="99ef8-155">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="99ef8-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="99ef8-156">表面吸着</span><span class="sxs-lookup"><span data-stu-id="99ef8-156">Surface magnetism</span></span>](surface-magnetism.md)
