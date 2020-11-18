---
title: 視線入力とドウェル
description: (視線/ヘッド) の宝石と熟考入力モデルの一般的な概要
author: sostel
ms.author: sostel
ms.date: 10/31/2019
ms.topic: article
keywords: Mixed Reality、宝石、熟考、相互作用、設計、視線追跡、ヘッド追跡、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: d47401b65f7d62e1fe59655c42efe72ac68acfc6
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702198"
---
# <a name="gaze-and-dwell"></a><span data-ttu-id="dac9a-104">視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="dac9a-104">Gaze and dwell</span></span>

<span data-ttu-id="dac9a-105">工具や部品で手がふさがっていると、ジェスチャは面倒であったりできなかったりすることがあります。</span><span class="sxs-lookup"><span data-stu-id="dac9a-105">When hands are occupied with tools and parts, gestures can be tedious or impossible.</span></span>
<span data-ttu-id="dac9a-106">また、音声コマンドは特定のコンテキストでは信頼できない場合もあります。たとえば、非常に大きな条件が発生した場合などです。</span><span class="sxs-lookup"><span data-stu-id="dac9a-106">Voice commands may also be unreliable in certain contexts, for example under excessively loud conditions.</span></span>
<span data-ttu-id="dac9a-107">宝石と熟考は、HoloLens でのヘッドアップとハンズフリーの作業を行うための使い慣れた、簡単なマスタメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="dac9a-107">Gaze and dwell offers a familiar and easy-to-master mechanism for working heads-up and hands-free on HoloLens.</span></span>
<span data-ttu-id="dac9a-108">また、宝石と熟考は、運用環境でのノイズ干渉や無音の制約に依存しない優れたフォールバックです。</span><span class="sxs-lookup"><span data-stu-id="dac9a-108">Additionally, gaze and dwell is a great fallback which is independent of noise interference or silence constraints in the operating environment.</span></span>
<span data-ttu-id="dac9a-109">_熟考_ と [熟考](gaze-and-dwell-head.md)の2つのバリエーションと、[視線と熟考](gaze-and-dwell-eyes.md)を区別しています。</span><span class="sxs-lookup"><span data-stu-id="dac9a-109">We distinguish two variants of _gaze and dwell_: [Head-gaze and dwell](gaze-and-dwell-head.md) and [Eye-gaze and dwell](gaze-and-dwell-eyes.md).</span></span>

## <a name="scenarios"></a><span data-ttu-id="dac9a-110">シナリオ</span><span class="sxs-lookup"><span data-stu-id="dac9a-110">Scenarios</span></span>

<span data-ttu-id="dac9a-111">熟考は、人間の手が他のタスクと共に忙しい場合や、環境や社会的な制約のためにボイスが 100% reliable or available ではない場合に威力を持っています。</span><span class="sxs-lookup"><span data-stu-id="dac9a-111">Gaze and dwell excels in scenarios where a person's hands are busy with other tasks, and voice isn't 100% reliable or available due to environmental or social constraints.</span></span>
<span data-ttu-id="dac9a-112">良い例は、車のエンジンの修理中に参考情報をオーバーレイするために HoloLens を付けている人です。</span><span class="sxs-lookup"><span data-stu-id="dac9a-112">A good example is a person wearing a HoloLens to overlay reference information while repairing a car engine.</span></span>
<span data-ttu-id="dac9a-113">その人がエンジンルームに身を乗り出すとき、その手は工具でふさがっているか体を支えています。</span><span class="sxs-lookup"><span data-stu-id="dac9a-113">Their hands are busy with tools or supporting their body as they lean into the engine compartment.</span></span>
<span data-ttu-id="dac9a-114">ガレージのスペースは絶えず工具を打ちつける音やブーンという音がして騒々しいため、音声コマンドを使うのは困難です。</span><span class="sxs-lookup"><span data-stu-id="dac9a-114">The garage space is loud, with the constant banging and buzzing of tools, making voice commands difficult.</span></span>
<span data-ttu-id="dac9a-115">熟考を使用すると、HoloLens を使用するユーザーは、ワークフローを中断することなく、参照資料を自信を持ってナビゲートできます。</span><span class="sxs-lookup"><span data-stu-id="dac9a-115">Gaze and dwell allows the person using the HoloLens to confidently navigate their reference material without interrupting their workflow.</span></span>

## <a name="device-support"></a><span data-ttu-id="dac9a-116">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="dac9a-116">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="dac9a-117"><strong>入力モデル</strong></span><span class="sxs-lookup"><span data-stu-id="dac9a-117"><strong>Input model</strong></span></span></td>
        <td><span data-ttu-id="dac9a-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="dac9a-118"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="dac9a-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="dac9a-119"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="dac9a-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="dac9a-120"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="dac9a-121">頭の視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="dac9a-121">Head-gaze and dwell</span></span></td>
        <td><span data-ttu-id="dac9a-122">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="dac9a-122">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="dac9a-123">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="dac9a-123">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="dac9a-124">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="dac9a-124">✔️ Recommended</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="dac9a-125">目の視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="dac9a-125">Eye-gaze and dwell</span></span></td>
        <td><span data-ttu-id="dac9a-126">❌ 使用できません</span><span class="sxs-lookup"><span data-stu-id="dac9a-126">❌ Not available</span></span></td>
        <td><span data-ttu-id="dac9a-127">✔️ 推奨</span><span class="sxs-lookup"><span data-stu-id="dac9a-127">✔️ Recommended</span></span></td>
        <td><span data-ttu-id="dac9a-128">❌ 使用できません</span><span class="sxs-lookup"><span data-stu-id="dac9a-128">❌ Not available</span></span></td>
    </tr>
</table>


<br>

---

 ## <a name="see-also"></a><span data-ttu-id="dac9a-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="dac9a-129">See also</span></span>
* [<span data-ttu-id="dac9a-130">視線ベースの操作</span><span class="sxs-lookup"><span data-stu-id="dac9a-130">Eye-based interaction</span></span>](eye-gaze-interaction.md)
* [<span data-ttu-id="dac9a-131">HoloLens 2 上の視線追跡</span><span class="sxs-lookup"><span data-stu-id="dac9a-131">Eye tracking on HoloLens 2</span></span>](eye-tracking.md)
* [<span data-ttu-id="dac9a-132">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="dac9a-132">Gaze and commit</span></span>](gaze-and-commit.md)
* [<span data-ttu-id="dac9a-133">手 - 直接操作</span><span class="sxs-lookup"><span data-stu-id="dac9a-133">Hands - Direct manipulation</span></span>](direct-manipulation.md)
* [<span data-ttu-id="dac9a-134">手 - ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="dac9a-134">Hands - Gestures</span></span>](gaze-and-commit.md#composite-gestures)
* [<span data-ttu-id="dac9a-135">手 - ポイントとコミット</span><span class="sxs-lookup"><span data-stu-id="dac9a-135">Hands - Point and commit</span></span>](point-and-commit.md)
* [<span data-ttu-id="dac9a-136">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="dac9a-136">Instinctual interactions</span></span>](interaction-fundamentals.md)
* [<span data-ttu-id="dac9a-137">音声入力</span><span class="sxs-lookup"><span data-stu-id="dac9a-137">Voice input</span></span>](voice-input.md)
