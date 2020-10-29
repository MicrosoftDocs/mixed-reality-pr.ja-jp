---
title: ケーススタディ-Lowe のキッチンからの教訓
description: HoloLens チームは、Lowe の HoloLens プロジェクトから派生したベストプラクティスの一部を共有したいと考えています。
author: brandonbray
ms.author: kevincol
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、Lowe、HoloLens、キッチン、ケーススタディ
ms.openlocfilehash: a6bd7a09f77fb71dc23dc640525ff250abac8f12
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687439"
---
# <a name="case-study---lessons-from-the-lowes-kitchen"></a><span data-ttu-id="d81a3-104">ケーススタディ-Lowe のキッチンからの教訓</span><span class="sxs-lookup"><span data-stu-id="d81a3-104">Case study - Lessons from the Lowe's kitchen</span></span>

<span data-ttu-id="d81a3-105">HoloLens チームは、Lowe の HoloLens プロジェクトから派生したベストプラクティスの一部を共有したいと考えています。</span><span class="sxs-lookup"><span data-stu-id="d81a3-105">The HoloLens team wants to share some of the best practices that were derived from the Lowe's HoloLens project.</span></span> <span data-ttu-id="d81a3-106">以下は、Satya の 2016 Ignite 基調講演で示されている Lowe の HoloLens のビデオです。</span><span class="sxs-lookup"><span data-stu-id="d81a3-106">Below is a video of the Lowe's HoloLens projected demonstrated at Satya's 2016 Ignite keynote.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/gC_4JxF0e_k]

## <a name="lowes-hololens-best-practices"></a><span data-ttu-id="d81a3-107">Lowe の HoloLens のベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="d81a3-107">Lowe's HoloLens Best Practices</span></span>

<span data-ttu-id="d81a3-108">2つのビデオでは、2016年4月から2つの Lowe の店舗に含まれていた Lowe の HoloLens パイロットから得られたベストプラクティスについて説明しています。</span><span class="sxs-lookup"><span data-stu-id="d81a3-108">The two videos cover best practices that were derived from the Lowe's HoloLens Pilot that has been in two Lowe's stores since April 2016.</span></span> <span data-ttu-id="d81a3-109">主なトピックは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d81a3-109">The key topics are:</span></span>
* <span data-ttu-id="d81a3-110">モバイルデバイスのパフォーマンスを最大にする</span><span class="sxs-lookup"><span data-stu-id="d81a3-110">Maximize performance for a mobile device</span></span>
* <span data-ttu-id="d81a3-111">Full holographic フレームを使用して UX メソッドを作成する (2 回目の話)</span><span class="sxs-lookup"><span data-stu-id="d81a3-111">Create UX methods with a full holographic frame (2nd talk)</span></span>
* <span data-ttu-id="d81a3-112">有効桁数の配置 (2 番目のトーク)</span><span class="sxs-lookup"><span data-stu-id="d81a3-112">Precision alignment (2nd talk)</span></span>
* <span data-ttu-id="d81a3-113">Shared holographic エクスペリエンス (2 番目の会話)</span><span class="sxs-lookup"><span data-stu-id="d81a3-113">Shared holographic experiences (2nd talk)</span></span>
* <span data-ttu-id="d81a3-114">顧客との対話 (2 回目の話)</span><span class="sxs-lookup"><span data-stu-id="d81a3-114">Interacting with customers (2nd talk)</span></span>

## <a name="video-1"></a><span data-ttu-id="d81a3-115">ビデオ1</span><span class="sxs-lookup"><span data-stu-id="d81a3-115">Video 1</span></span>

<span data-ttu-id="d81a3-116">**モバイルデバイスのパフォーマンスを最大に** するHoloLens は、デバイスですべての処理が行われるならではデバイスです。</span><span class="sxs-lookup"><span data-stu-id="d81a3-116">**Maximize performance for a mobile device** HoloLens is an untethered device with all the processing taking place in the device.</span></span> <span data-ttu-id="d81a3-117">これにはモバイルプラットフォームが必要であり、モバイルアプリケーションの作成と同様の考え方が必要です。</span><span class="sxs-lookup"><span data-stu-id="d81a3-117">This requires a mobile platform and requires a mindset similar to creating mobile applications.</span></span> <span data-ttu-id="d81a3-118">Microsoft では、ユーザーに delicious エクスペリエンスを提供するために、HoloLens アプリケーションで60FPS を維持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d81a3-118">Microsoft recommends that your HoloLens application maintain 60FPS to provide a delicious experience for your users.</span></span> <span data-ttu-id="d81a3-119">FPS が低いと、ホログラムが不安定になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d81a3-119">Having low FPS can result in unstable holograms.</span></span>

<span data-ttu-id="d81a3-120">HoloLens で開発するときに注目すべき重要な点のいくつかは、カスタムシェーダー ( [Hololens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)で無料で利用可能) を使用した、資産の最適化/確認です。</span><span class="sxs-lookup"><span data-stu-id="d81a3-120">Some of the most important things to look at when developing on HoloLens is asset optimization/decimation, using custom shaders (available for free in the [HoloLens Toolkit](https://github.com/Microsoft/HoloToolkit-Unity)).</span></span> <span data-ttu-id="d81a3-121">もう1つの重要な考慮事項は、プロジェクトの最初からフレームレートを測定することです。</span><span class="sxs-lookup"><span data-stu-id="d81a3-121">Another important consideration is to measure the frame rate from the very beginning of your project.</span></span> <span data-ttu-id="d81a3-122">プロジェクトによっては、アセットを表示する順序が大きな共同作成者である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="d81a3-122">Depending on the project, the order of displaying your assets can also be a big contributor</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/o0QIPwgiP9A]

## <a name="video-2"></a><span data-ttu-id="d81a3-123">ビデオ2</span><span class="sxs-lookup"><span data-stu-id="d81a3-123">Video 2</span></span>

<span data-ttu-id="d81a3-124">**完全な holographic フレームを使用して UX メソッドを作成** する物理的な世界でのホログラムの配置について理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="d81a3-124">**Create UX methods with a full holographic frame** It's important to understand the placement of holograms in a physical world.</span></span> <span data-ttu-id="d81a3-125">Lowe を使用すると、さまざまな UX メソッドについて説明します。これにより、ユーザーは、ホログラムの大規模な環境を見ながら、最新の状態にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d81a3-125">With Lowe's we talk about different UX methods that help users experience holograms up close while still seeing the larger environment of holograms.</span></span>

<span data-ttu-id="d81a3-126">**有効桁数の配置** Lowe のシナリオでは、ホログラムを物理的なキッチンに正確に配置することが最も重要でした。</span><span class="sxs-lookup"><span data-stu-id="d81a3-126">**Precision alignment** For the Lowe's scenario, it was paramount to the experience to have precision alignment of the holograms to the physical kitchen.</span></span> <span data-ttu-id="d81a3-127">これらの手法については、ユーザーの物理的な環境が変更されたことを仕向けるするエクスペリエンスを保証するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d81a3-127">We discuss techniques helps ensure an experience that convinces users that their physical environment has changed.</span></span>

<span data-ttu-id="d81a3-128">**共有 holographic エクスペリエンス** 結合は、Lowe のエクスペリエンスを使用する主な方法です。</span><span class="sxs-lookup"><span data-stu-id="d81a3-128">**Shared holographic experiences** Couples are the primary way that the Lowe's experience is consumed.</span></span> <span data-ttu-id="d81a3-129">1人のユーザーがカウンターを変更すると、他のユーザーが変更を確認できます。</span><span class="sxs-lookup"><span data-stu-id="d81a3-129">One person can change the countertop and the other person will see the changes.</span></span> <span data-ttu-id="d81a3-130">この "共有エクスペリエンス" を呼び出しました。</span><span class="sxs-lookup"><span data-stu-id="d81a3-130">We called this "shared experiences".</span></span>

<span data-ttu-id="d81a3-131">**顧客との対話** Lowe のデザイナーは HoloLens を使用していませんが、顧客に表示される内容を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d81a3-131">**Interacting with customers** Lowe's designers are not using a HoloLens, but they need to see what the customers are seeing.</span></span> <span data-ttu-id="d81a3-132">UWP アプリケーションで顧客が見ている内容をキャプチャする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d81a3-132">We show how to capture what the customer is seeing on a UWP application.</span></span>
<br>
>[!VIDEO https://www.youtube.com/embed/LceMdyKZ4PI]
