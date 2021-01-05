---
title: 進行状況を表示する
description: プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、コントロール、ui、ux、進行状況インジケーター、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 3f24f7095147a0d220df8adc42b67a1b8e4053c9
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848280"
---
# <a name="progress-indicator"></a><span data-ttu-id="318d6-104">進捗状況インジケーター</span><span class="sxs-lookup"><span data-stu-id="318d6-104">Progress indicator</span></span>

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

<span data-ttu-id="318d6-105">プログレスコントロールは、実行時間の長い操作が進行中であるというフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="318d6-105">A progress control provides feedback that a long-running operation is underway.</span></span> <span data-ttu-id="318d6-106">進行状況インジケーターが表示されると、ユーザーは待機時間を確認でき、アプリと対話できなくなります。</span><span class="sxs-lookup"><span data-stu-id="318d6-106">When a progress indicator is visible, users can see the wait time and can't interact with the app.</span></span>

<br>

---

## <a name="types-of-progress"></a><span data-ttu-id="318d6-107">プログレス コントロールの種類</span><span class="sxs-lookup"><span data-stu-id="318d6-107">Types of progress</span></span>

<span data-ttu-id="318d6-108">何が起こっているかについてユーザー情報を提供することが重要です。</span><span class="sxs-lookup"><span data-stu-id="318d6-108">It's important to provide the user information about what is happening.</span></span> <span data-ttu-id="318d6-109">混合環境では、ユーザーは、アプリに視覚的なフィードバックがない場合に、物理的な環境やオブジェクトによって簡単に気を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="318d6-109">In mixed reality, users can be easily distracted by the physical environment or objects if your app doesn't have good visual feedback.</span></span> <span data-ttu-id="318d6-110">データの読み込み中やシーンの更新など、数秒かかる状況では、視覚的なインジケーターを表示することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="318d6-110">For situations that take a few seconds, like when data is loading or a scene is updating, it's a good idea to show a visual indicator.</span></span> <span data-ttu-id="318d6-111">操作が進行しているユーザーを表示するには、 **進行状況バー** または **進行状況のリング** の2つのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="318d6-111">There are two options to show the user that an operation is underway – a **Progress bar** or a **Progress ring**.</span></span>

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a><span data-ttu-id="318d6-112">進行状況バー</span><span class="sxs-lookup"><span data-stu-id="318d6-112">Progress bar</span></span><br>
        <span data-ttu-id="318d6-113">進行状況バーには、タスクの完了率が表示されます。</span><span class="sxs-lookup"><span data-stu-id="318d6-113">A Progress bar shows the percentage completed of a task.</span></span> <span data-ttu-id="318d6-114">このメソッドは、期間が既知 (有限) の操作中に使用する必要がありますが、その進行状況では、ユーザーとアプリとの対話をブロックすることはできません。</span><span class="sxs-lookup"><span data-stu-id="318d6-114">It should be used during an operation whose duration is known (determinate), but its progress shouldn't block the user's interaction with the app.</span></span><br>
        <br>
        <span data-ttu-id="318d6-115">*イメージ: HoloLens での進行状況バーの例*</span><span class="sxs-lookup"><span data-stu-id="318d6-115">*Image: Progress bar example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="318d6-116">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="318d6-116">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="318d6-117">![HoloLens での進行状況バーの例](images/640px-progressbar.jpg)</span><span class="sxs-lookup"><span data-stu-id="318d6-117">![Progress bar example in HoloLens](images/640px-progressbar.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a><span data-ttu-id="318d6-118">進行状況リング</span><span class="sxs-lookup"><span data-stu-id="318d6-118">Progress ring</span></span><br>
        <span data-ttu-id="318d6-119">進行状況のリングは不確定状態であるため、操作が完了するまでユーザーの操作がブロックされるときに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="318d6-119">A Progress ring only has an indeterminate state, and should be used when user interaction is blocked until the operation has completed.</span></span><br>
        <br>
        <span data-ttu-id="318d6-120">*イメージ: HoloLens での進行状況リングの例*</span><span class="sxs-lookup"><span data-stu-id="318d6-120">*Image: Progress ring example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="318d6-121">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="318d6-121">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="318d6-122">![HoloLens デバイスでの進行状況リングの例](images/640px-progressring.jpg)</span><span class="sxs-lookup"><span data-stu-id="318d6-122">![Progress ring example on HoloLens device](images/640px-progressring.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a><span data-ttu-id="318d6-123">カスタムオブジェクトの進行状況</span><span class="sxs-lookup"><span data-stu-id="318d6-123">Progress with a custom object</span></span><br>
        <span data-ttu-id="318d6-124">独自のカスタム 2D/3D オブジェクトを使用して進行状況の制御をカスタマイズすることで、アプリの個性とブランド id に追加できます。</span><span class="sxs-lookup"><span data-stu-id="318d6-124">You can add to your app's personality and brand identity by customizing the Progress control with your own custom 2D/3D objects.</span></span><br>
        <br>
        <span data-ttu-id="318d6-125">*イメージ: HoloLens でのカスタムメッシュの例の進行状況*</span><span class="sxs-lookup"><span data-stu-id="318d6-125">*Image: Progress with custom mesh example in HoloLens*</span></span>
    :::column-end:::
        :::column:::
        <span data-ttu-id="318d6-126">![space](images/spacer-20x582.png)</span><span class="sxs-lookup"><span data-stu-id="318d6-126">![space](images/spacer-20x582.png)</span></span><br>
       <span data-ttu-id="318d6-127">![HoloLens でのカスタムメッシュの例の進行状況](images/640px-progresscustom.jpg)</span><span class="sxs-lookup"><span data-stu-id="318d6-127">![Progress with custom mesh example in HoloLens](images/640px-progresscustom.jpg)</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a><span data-ttu-id="318d6-128">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="318d6-128">Best practices</span></span>
* <span data-ttu-id="318d6-129">ユーザーが簡単にヘッドを空の領域に移動してコンテキストを失うことがあるため、 [billboarding またはタグ](billboarding-and-tag-along.md) を進行状況の表示に密に結合します。</span><span class="sxs-lookup"><span data-stu-id="318d6-129">Tightly couple [billboarding or tag-along](billboarding-and-tag-along.md) to the display of Progress since the user can easily move their head into empty space and lose context.</span></span> <span data-ttu-id="318d6-130">ユーザーが何も表示できない場合、アプリがクラッシュしたように見えることがあります。</span><span class="sxs-lookup"><span data-stu-id="318d6-130">Your app might look like it has crashed if the user is unable to see anything.</span></span> <span data-ttu-id="318d6-131">Billboarding とタグは、進行状況の prefab に組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="318d6-131">Billboarding and tag-along is built into the Progress prefab.</span></span>
* <span data-ttu-id="318d6-132">ユーザーに対して何が起こっているかに関するステータス情報を常に提供するのが適切です。</span><span class="sxs-lookup"><span data-stu-id="318d6-132">It's always good to provide status information about what is happening to the user.</span></span> <span data-ttu-id="318d6-133">Progress prefab には、状態を提供するための Windows 標準のリングの種類の進行状況など、さまざまな視覚スタイルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="318d6-133">The Progress prefab provides various visual styles including the Windows standard ring-type progress for providing status.</span></span> <span data-ttu-id="318d6-134">また、進行状況のスタイルをアプリのブランドに合わせる必要がある場合は、アニメーションでカスタムメッシュを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="318d6-134">You can also use a custom mesh with an animation if you want the style of your progress to align to your app’s brand.</span></span>

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a><span data-ttu-id="318d6-135">Unity 用 MRTK (Mixed Reality Toolkit) の進行状況インジケーター</span><span class="sxs-lookup"><span data-stu-id="318d6-135">Progress indicator in MRTK (Mixed Reality Toolkit) for Unity</span></span>

* [<span data-ttu-id="318d6-136">MRTK-進行状況インジケーター prefabs</span><span class="sxs-lookup"><span data-stu-id="318d6-136">MRTK - Progress indicator prefabs</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [<span data-ttu-id="318d6-137">MRTK-シーン移行サービス</span><span class="sxs-lookup"><span data-stu-id="318d6-137">MRTK - Scene transition service</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Extensions/SceneTransitionService/SceneTransitionServiceOverview.html)


<br>

---

## <a name="see-also"></a><span data-ttu-id="318d6-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="318d6-138">See also</span></span>

* [<span data-ttu-id="318d6-139">カーソル</span><span class="sxs-lookup"><span data-stu-id="318d6-139">Cursors</span></span>](cursors.md)
* [<span data-ttu-id="318d6-140">ハンド レイ</span><span class="sxs-lookup"><span data-stu-id="318d6-140">Hand ray</span></span>](point-and-commit.md)
* [<span data-ttu-id="318d6-141">ボタン</span><span class="sxs-lookup"><span data-stu-id="318d6-141">Button</span></span>](button.md)
* [<span data-ttu-id="318d6-142">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="318d6-142">Interactable object</span></span>](interactable-object.md)
* [<span data-ttu-id="318d6-143">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="318d6-143">Bounding box and App bar</span></span>](app-bar-and-bounding-box.md)
* [<span data-ttu-id="318d6-144">操作</span><span class="sxs-lookup"><span data-stu-id="318d6-144">Manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="318d6-145">ハンド メニュー</span><span class="sxs-lookup"><span data-stu-id="318d6-145">Hand menu</span></span>](hand-menu.md)
* [<span data-ttu-id="318d6-146">メニューの近く</span><span class="sxs-lookup"><span data-stu-id="318d6-146">Near menu</span></span>](near-menu.md)
* [<span data-ttu-id="318d6-147">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="318d6-147">Object collection</span></span>](object-collection.md)
* [<span data-ttu-id="318d6-148">音声コマンド</span><span class="sxs-lookup"><span data-stu-id="318d6-148">Voice command</span></span>](voice-input.md)
* [<span data-ttu-id="318d6-149">キーボード</span><span class="sxs-lookup"><span data-stu-id="318d6-149">Keyboard</span></span>](keyboard.md)
* [<span data-ttu-id="318d6-150">ヒント</span><span class="sxs-lookup"><span data-stu-id="318d6-150">Tooltip</span></span>](tooltip.md)
* [<span data-ttu-id="318d6-151">スレート</span><span class="sxs-lookup"><span data-stu-id="318d6-151">Slate</span></span>](slate.md)
* [<span data-ttu-id="318d6-152">スライダー</span><span class="sxs-lookup"><span data-stu-id="318d6-152">Slider</span></span>](slider.md)
* [<span data-ttu-id="318d6-153">シェーダー</span><span class="sxs-lookup"><span data-stu-id="318d6-153">Shader</span></span>](shader.md)
* [<span data-ttu-id="318d6-154">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="318d6-154">Billboarding and tag-along</span></span>](billboarding-and-tag-along.md)
* [<span data-ttu-id="318d6-155">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="318d6-155">Displaying progress</span></span>](progress.md)
* [<span data-ttu-id="318d6-156">表面吸着</span><span class="sxs-lookup"><span data-stu-id="318d6-156">Surface magnetism</span></span>](surface-magnetism.md)
