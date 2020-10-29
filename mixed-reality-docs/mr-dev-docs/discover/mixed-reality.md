---
title: Mixed Reality とは
description: この記事では、Mixed Reality を定義し、Mixed Reality の範囲における AR および VR デバイスの位置付けを示します。
author: brandonbray
ms.author: branbray
ms.date: 08/26/2020
ms.topic: article
keywords: Mixed Reality, ホログラフィック, AR, VR, MR, XR, 拡張現実, 仮想現実, 説明
ms.localizationpriority: high
ms.openlocfilehash: 44ef30925f8429628ebeb2c5f367d379a8ab102f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91700851"
---
# <a name="what-is-mixed-reality"></a><span data-ttu-id="5e41d-104">Mixed Reality とは</span><span class="sxs-lookup"><span data-stu-id="5e41d-104">What is Mixed Reality?</span></span>

![HoloLens 2 での手を使ったポイントとコミット](images/02_MixedRealitySlashMixedReality.png)

<span data-ttu-id="5e41d-106">Mixed Reality は、物理とデジタルの世界を融合し、人間、コンピューター、環境間の相互作用のリンクを解除します。</span><span class="sxs-lookup"><span data-stu-id="5e41d-106">Mixed Reality is a blend of physical and digital worlds, unlocking the links between human, computer, and environment interaction.</span></span> <span data-ttu-id="5e41d-107">この新しい現実は、コンピューター ビジョン、グラフィカル処理能力、ディスプレイ テクノロジ、および入力システムの進歩が基盤となっています。</span><span class="sxs-lookup"><span data-stu-id="5e41d-107">This new reality is based on advancements in computer vision, graphical processing power, display technology, and input systems.</span></span> <span data-ttu-id="5e41d-108">ただし、" *Mixed Reality* " という用語は、ポール・ミルグラムと岸野文郎による 1994 年の論文『[複合現実のビジュアル表示の分類](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)』で初めて紹介されました。</span><span class="sxs-lookup"><span data-stu-id="5e41d-108">However, the term *Mixed Reality* was introduced in a 1994 paper by Paul Milgram and Fumio Kishino, "[A Taxonomy of Mixed Reality Visual Displays](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)."</span></span> <span data-ttu-id="5e41d-109">この論文では、" *仮想現実連続体* " の概念と、表示に適用される分類法のカテゴリについて考察しています。</span><span class="sxs-lookup"><span data-stu-id="5e41d-109">Their paper explored the concept of the *virtuality continuum* and the categorization of taxonomy applied to displays.</span></span> <span data-ttu-id="5e41d-110">それ以降、Mixed Reality の応用は表示の範囲を超え、以下が含まれるようになっています。</span><span class="sxs-lookup"><span data-stu-id="5e41d-110">Since then, the application of Mixed Reality has gone beyond displays to include:</span></span>
* <span data-ttu-id="5e41d-111">環境入力</span><span class="sxs-lookup"><span data-stu-id="5e41d-111">Environmental input</span></span>
* <span data-ttu-id="5e41d-112">立体音響</span><span class="sxs-lookup"><span data-stu-id="5e41d-112">Spatial sound</span></span>
* <span data-ttu-id="5e41d-113">現実と仮想の両方の空間における場所と位置</span><span class="sxs-lookup"><span data-stu-id="5e41d-113">Locations and positioning in both real and virtual spaces</span></span>

<span data-ttu-id="5e41d-114">![Mixed Reality の範囲の画像](images/mixedrealityspectrum-worlds.png)</span><span class="sxs-lookup"><span data-stu-id="5e41d-114">![The Mixed Reality spectrum image](images/mixedrealityspectrum-worlds.png)</span></span><br>
<span data-ttu-id="5e41d-115">*図: Mixed Reality は物理的な世界とデジタル世界を融合したものです。*</span><span class="sxs-lookup"><span data-stu-id="5e41d-115">*Image: Mixed Reality is the result of blending the physical world with the digital world.*</span></span>

<br>

---

## <a name="environmental-input-and-perception"></a><span data-ttu-id="5e41d-116">環境の入力と認識</span><span class="sxs-lookup"><span data-stu-id="5e41d-116">Environmental input and perception</span></span>

<span data-ttu-id="5e41d-117">過去数十年にわたって、人間とコンピューターの入力の関係についての研究が続いており、" *ヒューマン コンピューター インタラクション* " または HCI と呼ばれる分野につながっています。</span><span class="sxs-lookup"><span data-stu-id="5e41d-117">Over the past several decades, exploration into the relationship between human and computer input has continued, leading to the discipline known as *human computer interaction* or HCI.</span></span> <span data-ttu-id="5e41d-118">人間入力は、キーボード、マウス、タッチ、インク、音声、さらには Kinect の骨格追跡など、さまざまな方法で行われます。</span><span class="sxs-lookup"><span data-stu-id="5e41d-118">Human input happens through different means, including keyboards, mice, touch, ink, voice, and even Kinect skeletal tracking.</span></span>

<span data-ttu-id="5e41d-119">センサーと処理の進歩は、環境からのコンピューター入力の新しい領域を生み出しています。</span><span class="sxs-lookup"><span data-stu-id="5e41d-119">Advancements in sensors and processing are giving rise to a new area of computer input from environments.</span></span> <span data-ttu-id="5e41d-120">コンピューターと環境の間の相互作用とは、実質的に、環境を理解または " *認識* " することです。そのため、環境情報を公開する Windows の API は、[認識 API シリーズ](https://docs.microsoft.com/uwp/api/Windows.Perception)と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="5e41d-120">The interaction between computers and environments is effectively environmental understanding or *perception* , which is why the API names in Windows that reveal environmental information are called the [perception APIs](https://docs.microsoft.com/uwp/api/Windows.Perception).</span></span> <span data-ttu-id="5e41d-121">環境入力では、世界での人の位置 ([頭の追跡](../design/coordinate-systems.md))、表面と境界 ([空間マッピング](../design/spatial-mapping.md)や[シーンの理解](../design/scene-understanding.md))、環境光、環境音、オブジェクト認識、場所などがキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="5e41d-121">Environmental input captures things like a person's position in the world ([head tracking](../design/coordinate-systems.md)), surfaces and boundaries ([spatial mapping](../design/spatial-mapping.md) and [scene understanding](../design/scene-understanding.md)), ambient lighting, environmental sound, object recognition, and location.</span></span>

<br>

<span data-ttu-id="5e41d-122">![コンピューター、人間、環境間の相互作用を示すベン図](images/mixed-reality-venn-diagram-300px.png)</span><span class="sxs-lookup"><span data-stu-id="5e41d-122">![Venn diagram showing interactions between computers, humans and environments](images/mixed-reality-venn-diagram-300px.png)</span></span><br><span data-ttu-id="5e41d-123"> \
*図: コンピューター、人間、環境間の相互作用。*</span><span class="sxs-lookup"><span data-stu-id="5e41d-123"> \
*Image: The interactions between computers, humans, and environments.*</span></span>

<br>

<span data-ttu-id="5e41d-124">**コンピューター処理、人間入力、環境入力** の 3 つすべてを組み合わせにより、真の Mixed Reality エクスペリエンスを作成するための準備が整います。</span><span class="sxs-lookup"><span data-stu-id="5e41d-124">The combination of all three - **computer processing, human input, and environmental input** - sets the stage for creating true Mixed Reality experiences.</span></span> <span data-ttu-id="5e41d-125">物理的な世界内の移動は、デジタル世界での動きに変換できます。</span><span class="sxs-lookup"><span data-stu-id="5e41d-125">Movement through the physical world can translate to movement in the digital world.</span></span> <span data-ttu-id="5e41d-126">物理的な世界の境界は、デジタル環境でのゲーム プレイなどのアプリケーション エクスペリエンスに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5e41d-126">Boundaries in the physical world can influence application experiences, such as game play, in the digital world.</span></span> <span data-ttu-id="5e41d-127">環境入力がないと、エクスペリエンスで物理とデジタルの現実を融合することはできません。</span><span class="sxs-lookup"><span data-stu-id="5e41d-127">Without environmental input, experiences can't blend between physical and digital realities.</span></span><br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a><span data-ttu-id="5e41d-128">Mixed Reality の範囲</span><span class="sxs-lookup"><span data-stu-id="5e41d-128">The Mixed Reality spectrum</span></span>

<span data-ttu-id="5e41d-129">Mixed Reality では物理とデジタルの両方の世界が融合されるため、これらの 2 つの現実によって、仮想現実連続体と呼ばれる範囲の両端が定義されます。</span><span class="sxs-lookup"><span data-stu-id="5e41d-129">Since Mixed Reality blends both physical and digital worlds, these two realities define the polar ends of a spectrum known as the virtuality continuum.</span></span> <span data-ttu-id="5e41d-130">この現実の配列を " *Mixed Reality の範囲* " と呼んでいます。</span><span class="sxs-lookup"><span data-stu-id="5e41d-130">We refer to the array of realities as the *Mixed Reality spectrum* .</span></span> <span data-ttu-id="5e41d-131">左側には、人間が存在する物理的な現実があります。</span><span class="sxs-lookup"><span data-stu-id="5e41d-131">On the left-hand side, we have the physical reality that we as humans exist in.</span></span> <span data-ttu-id="5e41d-132">右側には、対応するデジタル的な現実があります。</span><span class="sxs-lookup"><span data-stu-id="5e41d-132">On the right-hand side, we have the corresponding digital reality.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a><span data-ttu-id="5e41d-133">拡張現実と仮想現実</span><span class="sxs-lookup"><span data-stu-id="5e41d-133">Augmented vs. virtual reality</span></span>

<span data-ttu-id="5e41d-134">現在市場にあるほとんどの携帯電話には、環境を理解する機能はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="5e41d-134">Most mobile phones on the market today have little to no environmental understanding capabilities.</span></span> <span data-ttu-id="5e41d-135">これらによって提供されるエクスペリエンスでは、物理とデジタルの現実を融合することはできません。</span><span class="sxs-lookup"><span data-stu-id="5e41d-135">The experiences they offer can't mix physical and digital realities.</span></span> <span data-ttu-id="5e41d-136">物理的な世界のビデオ ストリームにグラフィックを重ね合わせるエクスペリエンスは、" *拡張現実* " です。</span><span class="sxs-lookup"><span data-stu-id="5e41d-136">The experiences that overlay graphics on video streams of the physical world are *augmented reality* .</span></span> <span data-ttu-id="5e41d-137">人の視野を遮ってデジタル エクスペリエンスを提供するエクスペリエンスは、" *仮想現実* " です。</span><span class="sxs-lookup"><span data-stu-id="5e41d-137">The experiences that occlude your view to present a digital experience are *virtual reality* .</span></span> <span data-ttu-id="5e41d-138">拡張現実と仮想現実の間で可能になるエクスペリエンスにより、" *Mixed Reality* " が形成されます。</span><span class="sxs-lookup"><span data-stu-id="5e41d-138">The experiences enabled between augmented and virtual reality form *Mixed Reality* :</span></span>
* <span data-ttu-id="5e41d-139">物理的な世界から始まって、ホログラムなどのデジタル オブジェクトが、そこに存在しているかのように配置されます。</span><span class="sxs-lookup"><span data-stu-id="5e41d-139">Starting with the physical world, placing a digital object, such as a hologram, as if it was there.</span></span>
* <span data-ttu-id="5e41d-140">物理的な世界から始まって、別の人のデジタル表現 (アバター) を使用して、ノートを離れるときに立っていた場所が示されます。</span><span class="sxs-lookup"><span data-stu-id="5e41d-140">Starting with the physical world, a digital representation of another person--an avatar--shows the location where they were standing when leaving notes.</span></span> <span data-ttu-id="5e41d-141">つまり、異なる時点での非同期コラボレーションを表すエクスペリエンスです。</span><span class="sxs-lookup"><span data-stu-id="5e41d-141">In other words, experiences that represent asynchronous collaboration at different points in time.</span></span>
* <span data-ttu-id="5e41d-142">デジタル世界から始まって、壁や家具など、物理的な世界の物理的な境界が、ユーザーが物理的なオブジェクトを回避できるように、エクスペリエンス内にデジタルで表示されます。</span><span class="sxs-lookup"><span data-stu-id="5e41d-142">Starting with a digital world, physical boundaries from the physical world, such as walls and furniture, appear digitally within the experience to help users avoid physical objects.</span></span>


<br>

<span data-ttu-id="5e41d-143">![Mixed Reality の範囲](images/mixedrealityspectrum.png)</span><span class="sxs-lookup"><span data-stu-id="5e41d-143">![The Mixed Reality spectrum](images/mixedrealityspectrum.png)</span></span><br>
<span data-ttu-id="5e41d-144">*図: Mixed Reality の範囲*</span><span class="sxs-lookup"><span data-stu-id="5e41d-144">*Image: The Mixed Reality spectrum*</span></span>

<br>

<span data-ttu-id="5e41d-145">現在利用可能なほとんどの拡張現実および仮想現実の製品は、この範囲のごく一部を表しており、より大きな Mixed Reality の範囲のサブセットと見なされています。</span><span class="sxs-lookup"><span data-stu-id="5e41d-145">Most augmented reality and virtual reality offerings available today represent a small part of this spectrum and are considered subsets of the larger Mixed Reality spectrum.</span></span> <span data-ttu-id="5e41d-146">Windows 10 は、範囲全体を念頭に置いて構築されており、人間、場所、物のデジタル表現を現実の世界と融合できます。</span><span class="sxs-lookup"><span data-stu-id="5e41d-146">Windows 10 is built with the entire spectrum in mind, and allows blending digital representations of people, places, and things with the real world.</span></span>


## <a name="devices-and-experiences"></a><span data-ttu-id="5e41d-147">デバイスとエクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="5e41d-147">Devices and experiences</span></span>

<span data-ttu-id="5e41d-148">Windows Mixed Reality のエクスペリエンスを提供するデバイスには、主に次の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="5e41d-148">There are two main types of devices that deliver Windows Mixed Reality experiences:</span></span>
1. <span data-ttu-id="5e41d-149">**ホログラフィック デバイス** の特徴は、そこに存在しているかのように、デジタル コンテンツを現実の世界に配置できることです。</span><span class="sxs-lookup"><span data-stu-id="5e41d-149">**Holographic devices** are characterized by the device's ability to place digital content in the real world as if it were there.</span></span>
2. <span data-ttu-id="5e41d-150">**イマーシブ デバイス** の特徴は、物理的な世界を隠し、デジタル エクスペリエンスで置き換えることによって、"存在感" を作成できることです。</span><span class="sxs-lookup"><span data-stu-id="5e41d-150">**Immersive devices** are characterized by the device's ability to create a sense of "presence"--hiding the physical world, and replacing it with a digital experience.</span></span>

<table>
<tr>
<th width="30%"> <span data-ttu-id="5e41d-151">特徴</span><span class="sxs-lookup"><span data-stu-id="5e41d-151">Characteristic</span></span></th><th width="35%"> <span data-ttu-id="5e41d-152">ホログラフィック デバイス</span><span class="sxs-lookup"><span data-stu-id="5e41d-152">Holographic devices</span></span></th><th width="35%"> <span data-ttu-id="5e41d-153">イマーシブ デバイス</span><span class="sxs-lookup"><span data-stu-id="5e41d-153">Immersive devices</span></span></th>
</tr><tr>
<td><span data-ttu-id="5e41d-154"><strong>デバイスの例</strong></span><span class="sxs-lookup"><span data-stu-id="5e41d-154"><strong>Example device</strong></span></span></td><td> <span data-ttu-id="5e41d-155">Microsoft HoloLens</span><span class="sxs-lookup"><span data-stu-id="5e41d-155">Microsoft HoloLens</span></span><br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> <span data-ttu-id="5e41d-156">Samsung HMD Odyssey+</span><span class="sxs-lookup"><span data-stu-id="5e41d-156">Samsung HMD Odyssey+</span></span><br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><span data-ttu-id="5e41d-157"><strong>ディスプレイ</strong></span><span class="sxs-lookup"><span data-stu-id="5e41d-157"><strong>Display</strong></span></span></td><td> <span data-ttu-id="5e41d-158">シースルー ディスプレイ。</span><span class="sxs-lookup"><span data-stu-id="5e41d-158">See-through display.</span></span> <span data-ttu-id="5e41d-159">ユーザーはヘッドセットを装着している間も物理環境を見ることができます。</span><span class="sxs-lookup"><span data-stu-id="5e41d-159">Allows user to see the physical environment while wearing the headset.</span></span></td><td> <span data-ttu-id="5e41d-160">非透過ディスプレイ。</span><span class="sxs-lookup"><span data-stu-id="5e41d-160">Opaque display.</span></span> <span data-ttu-id="5e41d-161">ユーザーはヘッドセットを装着している間は物理環境を見ることができません。</span><span class="sxs-lookup"><span data-stu-id="5e41d-161">Blocks out the physical environment while wearing the headset.</span></span></td>
</tr><tr>
<td><span data-ttu-id="5e41d-162"><strong>移動</strong></span><span class="sxs-lookup"><span data-stu-id="5e41d-162"><strong>Movement</strong></span></span></td><td> <span data-ttu-id="5e41d-163">回転と平行移動の両方で、6 自由度の完全な移動。</span><span class="sxs-lookup"><span data-stu-id="5e41d-163">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td><td> <span data-ttu-id="5e41d-164">回転と平行移動の両方で、6 自由度の完全な移動。</span><span class="sxs-lookup"><span data-stu-id="5e41d-164">Full six-degrees-of-freedom movement, both rotation and translation.</span></span></td>
</tr>
</table> 


> <span data-ttu-id="5e41d-165">[注] デバイスが (USB ケーブルまたは Wi-Fi 経由で) 別の PC に接続されているか、自己完結型 (非接続) であるかは、デバイスがホログラフィックかイマーシブかを表しているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="5e41d-165">[NOTE] Whether a device is connected to or tethered to a separate PC (via USB cable or Wi-Fi) or self-contained (untethered) doesn't reflect whether a device is holographic or immersive.</span></span> <span data-ttu-id="5e41d-166">モビリティ向上機能によってエクスペリエンスは向上し、ホログラフィック デバイスとイマーシブ デバイスはどちらも接続式または非接続式にできます。</span><span class="sxs-lookup"><span data-stu-id="5e41d-166">Features that improve mobility lead to better experiences, and both holographic and immersive devices could be tethered or untethered.</span></span>

<span data-ttu-id="5e41d-167">技術的な進歩によって、Mixed Reality エクスペリエンスは可能になりました。</span><span class="sxs-lookup"><span data-stu-id="5e41d-167">Technological advancement is what has enabled Mixed Reality experiences.</span></span> <span data-ttu-id="5e41d-168">現在、すべての範囲でエクスペリエンスを実行できるデバイスはありません。</span><span class="sxs-lookup"><span data-stu-id="5e41d-168">There are no devices today that can run experiences across the entire spectrum.</span></span> <span data-ttu-id="5e41d-169">Windows 10 では、デバイスの製造元と開発者の両方に共通の Mixed Reality プラットフォームを提供しています。</span><span class="sxs-lookup"><span data-stu-id="5e41d-169">Windows 10 provides a common Mixed Reality platform for both device manufacturers and developers.</span></span> <span data-ttu-id="5e41d-170">今日のデバイスでは Mixed Reality の範囲内の特定の範囲をサポートでき、新しいデバイスにより、その範囲は広がっています。</span><span class="sxs-lookup"><span data-stu-id="5e41d-170">Devices today can support a specific range within the Mixed Reality spectrum, with new devices expanding that range.</span></span> <span data-ttu-id="5e41d-171">将来、ホログラフィック デバイスはよりイマーシブになり、イマーシブ デバイスはよりホログラフィックになります。</span><span class="sxs-lookup"><span data-stu-id="5e41d-171">In the future, holographic devices will become more immersive, and immersive devices will become more holographic.</span></span>

<br>

<span data-ttu-id="5e41d-172">![Mixed Reality の範囲におけるデバイスの種類](images/Final_WhatIsMixedReality07.png)</span><span class="sxs-lookup"><span data-stu-id="5e41d-172">![Device types in the Mixed Reality spectrum](images/Final_WhatIsMixedReality07.png)</span></span><br>
<span data-ttu-id="5e41d-173">*図: Mixed Reality の範囲におけるデバイスの位置付け*</span><span class="sxs-lookup"><span data-stu-id="5e41d-173">*Image: Where devices exist on the Mixed Reality spectrum*</span></span>

<span data-ttu-id="5e41d-174">アプリケーションやゲームの開発者が作成しようとしているエクスペリエンスの種類を考えることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5e41d-174">It's best to think what type of experience an application or game developer wants to create.</span></span> <span data-ttu-id="5e41d-175">エクスペリエンスは、通常、範囲の特定の点または部分を対象としています。</span><span class="sxs-lookup"><span data-stu-id="5e41d-175">The experiences will typically target a specific point or part on the spectrum.</span></span> <span data-ttu-id="5e41d-176">開発者は、対象とするデバイスの機能を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e41d-176">Developers should consider the capabilities of devices they want to target.</span></span> <span data-ttu-id="5e41d-177">たとえば、物理的な世界に依存するエクスペリエンスは、HoloLens で実行するのが最善です。</span><span class="sxs-lookup"><span data-stu-id="5e41d-177">Experiences that rely on the physical world will run best on HoloLens.</span></span>
* <span data-ttu-id="5e41d-178">**左に向かう (物理的な現実に近づく)。**</span><span class="sxs-lookup"><span data-stu-id="5e41d-178">**Towards the left (near physical reality).**</span></span> <span data-ttu-id="5e41d-179">ユーザーは、物理的な環境内に存在していて、その環境を離れたと信じさせられることはありません。</span><span class="sxs-lookup"><span data-stu-id="5e41d-179">Users remain present in their physical environment and are never made to believe they have left that environment.</span></span>
* <span data-ttu-id="5e41d-180">**中央 (完全な Mixed Reality)。**</span><span class="sxs-lookup"><span data-stu-id="5e41d-180">**In the middle (fully Mixed Reality).**</span></span> <span data-ttu-id="5e41d-181">これらのエクスペリエンスでは、現実世界とデジタル世界が融合されています。</span><span class="sxs-lookup"><span data-stu-id="5e41d-181">These experiences blend the real world and the digital world.</span></span> <span data-ttu-id="5e41d-182">映画『[ジュマンジ](https://en.wikipedia.org/wiki/Jumanji)』を見た人なら、物語が展開する家の物理的な構造と、ジャングルの環境がどのようにブレンドされていたかわかります。</span><span class="sxs-lookup"><span data-stu-id="5e41d-182">Viewers who have seen the movie [Jumanji](https://en.wikipedia.org/wiki/Jumanji) can reconcile how the physical structure of the house where the story took place was blended with a jungle environment.</span></span>
* <span data-ttu-id="5e41d-183">**右に向かう (デジタル的な現実に近づく)。**</span><span class="sxs-lookup"><span data-stu-id="5e41d-183">**Towards the right (near digital reality).**</span></span> <span data-ttu-id="5e41d-184">ユーザーは、デジタル環境を体験し、自分の周りの物理的な環境で起こっていることは認識しません。</span><span class="sxs-lookup"><span data-stu-id="5e41d-184">Users experience a digital environment, and are unaware of what occurs in the physical environment around them.</span></span>


## <a name="see-also"></a><span data-ttu-id="5e41d-185">関連項目</span><span class="sxs-lookup"><span data-stu-id="5e41d-185">See also</span></span>

* [<span data-ttu-id="5e41d-186">ホログラムとは</span><span class="sxs-lookup"><span data-stu-id="5e41d-186">What is a hologram?</span></span>](hologram.md)
* [<span data-ttu-id="5e41d-187">Mixed Reality の基本を理解する</span><span class="sxs-lookup"><span data-stu-id="5e41d-187">Understand the basics of Mixed Reality</span></span>](get-started-with-mr.md#understand-the-basics)
* [<span data-ttu-id="5e41d-188">作成とプロトタイプ作成を始める</span><span class="sxs-lookup"><span data-stu-id="5e41d-188">Start creating and prototyping</span></span>](../design/design.md)
* [<span data-ttu-id="5e41d-189">ツールとアーキテクチャについて学習する</span><span class="sxs-lookup"><span data-stu-id="5e41d-189">Learn the tools and architecture</span></span>](../develop/development.md)

