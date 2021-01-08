---
title: 開始ジェスチャ
description: 開始ジェスチャを使用して、HoloLens および Windows Mixed Reality のイマーシブヘッドセットの [スタート] メニューを呼び出す方法について説明します。
author: shengkait
ms.author: cmeekhof
ms.date: 10/22/2019
ms.topic: article
keywords: Mixed reality、ジェスチャ、相互作用、設計、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、ブルーム
ms.openlocfilehash: 9e29d483375db103cebc30be9117e40899a9f81f
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009432"
---
# <a name="start-gesture"></a><span data-ttu-id="fde8c-104">開始ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="fde8c-104">Start gesture</span></span>

<span data-ttu-id="fde8c-105">Start ジェスチャは、[スタート] メニューを呼び出すために使用するハンドジェスチャです。</span><span class="sxs-lookup"><span data-stu-id="fde8c-105">The Start gesture is a hand gesture used to invoke the Start Menu.</span></span> <span data-ttu-id="fde8c-106">これは、キーボードで Windows キーを押すか、Xbox コントローラーの Xbox ボタンを押すか、またはイマーシブヘッドセットモーションコントローラーの Windows ボタンを押すことに相当します。</span><span class="sxs-lookup"><span data-stu-id="fde8c-106">It's the equivalent of pressing the Windows key on keyboards, the Xbox button on Xbox controllers, or the Windows button on immersive headset motion controllers.</span></span> <span data-ttu-id="fde8c-107">相互作用を設計する際の競合を防ぐため、各 Mixed Reality デバイスでの予約済みシステムジェスチャに特に注意してください。</span><span class="sxs-lookup"><span data-stu-id="fde8c-107">Pay special attention to reserved system gestures on each Mixed Reality device to prevent conflicts when you're designing interactions.</span></span>

## <a name="device-support"></a><span data-ttu-id="fde8c-108">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="fde8c-108">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fde8c-109"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="fde8c-109"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="fde8c-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="fde8c-110"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="fde8c-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="fde8c-111"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="fde8c-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="fde8c-112"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="fde8c-113">Bloom (ブルーム)</span><span class="sxs-lookup"><span data-stu-id="fde8c-113">Bloom</span></span></td>
        <td><span data-ttu-id="fde8c-114">✔️</span><span class="sxs-lookup"><span data-stu-id="fde8c-114">✔️</span></span></td>
        <td>❌</td>
        <td>❌</td>
    </tr>
     <tr>
        <td><span data-ttu-id="fde8c-115">手首ボタン</span><span class="sxs-lookup"><span data-stu-id="fde8c-115">Wrist button</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="fde8c-116">✔️</span><span class="sxs-lookup"><span data-stu-id="fde8c-116">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="fde8c-117">視線とパームアップのピンチ</span><span class="sxs-lookup"><span data-stu-id="fde8c-117">Eye gaze and palm up pinch</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="fde8c-118">✔️</span><span class="sxs-lookup"><span data-stu-id="fde8c-118">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="bloom"></a><span data-ttu-id="fde8c-119">Bloom (ブルーム)</span><span class="sxs-lookup"><span data-stu-id="fde8c-119">Bloom</span></span>

<span data-ttu-id="fde8c-120">HoloLens の [スタート] メニューを表示するように "ブルーム" を設計しました。これは、花開花を模したシンボリックジェスチャです。</span><span class="sxs-lookup"><span data-stu-id="fde8c-120">We designed “Bloom” to bring up the start menu in HoloLens (1st gen), which is a symbolic gesture mimicking a flower blossom.</span></span> <span data-ttu-id="fde8c-121">これは、footed の相互作用、使いやすさ、および迅速な再呼び出しにとっては独特です。</span><span class="sxs-lookup"><span data-stu-id="fde8c-121">It's distinctive for sure-footed interaction, easy of use, and quick to recall.</span></span> <span data-ttu-id="fde8c-122">ジェスチャを使用するには、手を手に入れてすぐに手に入れ、指を押しながら手を開けます。</span><span class="sxs-lookup"><span data-stu-id="fde8c-122">To use the gesture, hold out your hand with your palm up and fingertips together, then open your hand by spreading your fingers.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="fde8c-123">![ブルーム close](images/bloom-close.png)</span><span class="sxs-lookup"><span data-stu-id="fde8c-123">![Bloom close](images/bloom-close.png)</span></span><br>
        <span data-ttu-id="fde8c-124">**手順 1: すぐに使用することができます。**</span><span class="sxs-lookup"><span data-stu-id="fde8c-124">**Step 1: Palm up with fingertips together**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="fde8c-125">![ブルームを開く](images/bloom-open.png)</span><span class="sxs-lookup"><span data-stu-id="fde8c-125">![Bloom open](images/bloom-open.png)</span></span><br>
        <span data-ttu-id="fde8c-126">**手順 2: すぐに使えるパームアップ**</span><span class="sxs-lookup"><span data-stu-id="fde8c-126">**Step 2: Palm up with fingertips spread**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="start-gesture"></a><span data-ttu-id="fde8c-127">開始ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="fde8c-127">Start gesture</span></span>

<span data-ttu-id="fde8c-128">HoloLens 2 では、ブルームジェスチャを仮想手首ボタンに置き換えました。これはユーザーにとって instinctual です。</span><span class="sxs-lookup"><span data-stu-id="fde8c-128">In HoloLens 2, we replaced the Bloom gesture with a virtual wrist button, which is more instinctual for users.</span></span> <span data-ttu-id="fde8c-129">手首にユーザーを表示することにより、ユーザーは直感的に接続して、もう一方の手で押すことができます。</span><span class="sxs-lookup"><span data-stu-id="fde8c-129">By showing users the button on the wrist, they can intuitively reach out and press it with their other hand.</span></span>

:::row:::
    :::column:::
        <span data-ttu-id="fde8c-130">![手首ボタンの準備完了](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="fde8c-130">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="fde8c-131">**手順 1: パームアップ: 手首ボタンを表示する**</span><span class="sxs-lookup"><span data-stu-id="fde8c-131">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="fde8c-132">![手首ボタンの押下](images/wrist-button-press.png)</span><span class="sxs-lookup"><span data-stu-id="fde8c-132">![Wrist button press](images/wrist-button-press.png)</span></span><br>
        <span data-ttu-id="fde8c-133">**手順 2: 手首ボタンを押す**</span><span class="sxs-lookup"><span data-stu-id="fde8c-133">**Step 2: Press the wrist button**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="one-handed-start-gesture"></a><span data-ttu-id="fde8c-134">ワンきき開始ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="fde8c-134">One-handed Start gesture</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fde8c-135">ワンきき開始ジェスチャを機能させるには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="fde8c-135">For the one-handed Start gesture to work:</span></span>
>
> 1. <span data-ttu-id="fde8c-136">2019年11月の更新プログラム (ビルド 18363.1039) 以降に更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fde8c-136">You must update to the November 2019 update (build 18363.1039) or later.</span></span>
> 1. <span data-ttu-id="fde8c-137">視線追跡が正常に機能するように、デバイスで目を調整する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fde8c-137">Your eyes must be calibrated on the device so that eye tracking functions correctly.</span></span> <span data-ttu-id="fde8c-138">[Start] \ (開始 \) アイコンを見たときに orbiting のドットが表示されない場合は、デバイス上で目が調整されていません。</span><span class="sxs-lookup"><span data-stu-id="fde8c-138">If you do not see orbiting dots around the Start icon when you look at it, your eyes are not calibrated on the device.</span></span>

<span data-ttu-id="fde8c-139">また、開始ジェスチャを使用できるのはワンハンドだけです。</span><span class="sxs-lookup"><span data-stu-id="fde8c-139">You can also use the Start gesture with only one hand.</span></span> <span data-ttu-id="fde8c-140">手のひらを使って、内部の手首にある **スタートアイコン** を見てください。</span><span class="sxs-lookup"><span data-stu-id="fde8c-140">Hold out your hand with your palm facing you and look at the **Start icon** on your inner wrist.</span></span> <span data-ttu-id="fde8c-141">**アイコンを見たまま** にして、親指と人差し指を一緒にピンチします。</span><span class="sxs-lookup"><span data-stu-id="fde8c-141">**While keeping your eye on the icon**, pinch your thumb and index finger together.</span></span><br>
:::row:::
    :::column:::
        <span data-ttu-id="fde8c-142">![手首ボタンの準備完了](images/wrist-button-ready.png)</span><span class="sxs-lookup"><span data-stu-id="fde8c-142">![Wrist button ready](images/wrist-button-ready.png)</span></span><br>
        <span data-ttu-id="fde8c-143">**手順 1: パームアップ: 手首ボタンを表示する**</span><span class="sxs-lookup"><span data-stu-id="fde8c-143">**Step 1: Palm up to show the wrist button**</span></span><br>
    :::column-end:::
    :::column:::
        <span data-ttu-id="fde8c-144">![手首ボタンのピンチ](images/wrist-button-pinch.png)</span><span class="sxs-lookup"><span data-stu-id="fde8c-144">![Wrist button pinch](images/wrist-button-pinch.png)</span></span><br>
        <span data-ttu-id="fde8c-145">**手順 2: ボタンをクリックしてからピンチする**</span><span class="sxs-lookup"><span data-stu-id="fde8c-145">**Step 2: Eye gaze at the button then pinch**</span></span><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a><span data-ttu-id="fde8c-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="fde8c-146">See also</span></span>

* [<span data-ttu-id="fde8c-147">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="fde8c-147">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="fde8c-148">視線</span><span class="sxs-lookup"><span data-stu-id="fde8c-148">Eye-gaze</span></span>](eye-tracking.md)
* [<span data-ttu-id="fde8c-149">音声入力</span><span class="sxs-lookup"><span data-stu-id="fde8c-149">Voice input</span></span>](voice-input.md)
