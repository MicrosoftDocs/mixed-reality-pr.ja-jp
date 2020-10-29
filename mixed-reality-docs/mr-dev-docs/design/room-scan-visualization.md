---
title: 部屋のスキャンの可視化
description: 空間マッピングデータを必要とするアプリケーションでは、ユーザーがデバイスをアクティブにして環境を探索するときに、このデータが時間の経過と共に自動的に収集されるように、デバイスに依存します。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、アプリパターン、設計、HoloLens、ルームスキャン、空間マッピング、メッシュ
ms.openlocfilehash: 25de181bbb2dedaba9e4917f51cc80bac77cc5f1
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684031"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="26538-104">部屋のスキャンの可視化</span><span class="sxs-lookup"><span data-stu-id="26538-104">Room scan visualization</span></span>

<span data-ttu-id="26538-105">空間マッピングデータを必要とするアプリケーションでは、ユーザーがデバイスをアクティブにして環境を探索するときに、このデータが時間の経過と共に自動的に収集されるように、デバイスに依存します。</span><span class="sxs-lookup"><span data-stu-id="26538-105">Applications that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="26538-106">このデータの完全性と品質は、ユーザーが実行した探索の量、探索から経過した時間、家具やドアなどのオブジェクトが領域をスキャンした後に移動されたかどうかなど、さまざまな要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="26538-106">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="26538-107">便利な空間マッピングデータを確保するために、アプリケーション開発者にはいくつかのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="26538-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="26538-108">既に収集されている可能性があるものに依存します。</span><span class="sxs-lookup"><span data-stu-id="26538-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="26538-109">このデータは、最初は不完全である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="26538-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="26538-110">ブルームジェスチャを使用して Windows Mixed Reality ホームにアクセスし、エクスペリエンスに使用する領域を調べるようにユーザーに依頼します。</span><span class="sxs-lookup"><span data-stu-id="26538-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="26538-111">これらのユーザーは、すべての必要な領域がデバイスに認識されていることを、エアタップを使用して確認できます。</span><span class="sxs-lookup"><span data-stu-id="26538-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="26538-112">独自のアプリケーションでカスタム探索エクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="26538-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="26538-113">これらのすべてのケースでは、探索中に収集された実際のデータがシステムによって格納されるため、アプリケーションでこれを行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="26538-113">Note that in all these cases the actual data gathered during the exploration is stored by the system and the application does not need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="26538-114">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="26538-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="26538-115"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="26538-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="26538-116"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="26538-116"><a href="../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="26538-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="26538-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="26538-118">部屋のスキャンの可視化</span><span class="sxs-lookup"><span data-stu-id="26538-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="26538-119">✔️</span><span class="sxs-lookup"><span data-stu-id="26538-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="26538-120">カスタムスキャンエクスペリエンスの構築</span><span class="sxs-lookup"><span data-stu-id="26538-120">Building a custom scanning experience</span></span>

<span data-ttu-id="26538-121">アプリケーションでは、エクスペリエンスの開始時に空間マッピングデータを分析して、その完全性と品質を向上させるために追加の手順を実行する必要があるかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="26538-121">Applications may decide to analyze the spatial mapping data at the start of the experience to judge whether they want the user to perform additional steps to improve its completeness and quality.</span></span> <span data-ttu-id="26538-122">分析によって品質を向上させる必要がある場合は、開発者が視覚エフェクトを使用して、次のことを示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="26538-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="26538-123">ユーザーの近くにあるユーザーの合計ボリュームのうち、エクスペリエンスの一部として必要な量</span><span class="sxs-lookup"><span data-stu-id="26538-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="26538-124">データを改善するためにユーザーが行う必要がある場所</span><span class="sxs-lookup"><span data-stu-id="26538-124">Where the user should go to improve data</span></span>

<span data-ttu-id="26538-125">"良い" スキャンが行われていることをユーザーが認識していません。</span><span class="sxs-lookup"><span data-stu-id="26538-125">Users do not know what makes a "good" scan.</span></span> <span data-ttu-id="26538-126">スキャンを評価するよう求められた場合は、それらを表示または指定する必要があります。開発者は、スキャンまたは探索フェーズでの空間マッピングデータの更新を含むフィードバックループを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26538-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, etc. The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="26538-127">多くの場合、必要なスキャン品質を得るために、ユーザーに対して実行する必要があること (たとえば、天井、家具を見てみてください) を伝えることが最適な場合があります。</span><span class="sxs-lookup"><span data-stu-id="26538-127">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="26538-128">キャッシュと連続空間マッピング</span><span class="sxs-lookup"><span data-stu-id="26538-128">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="26538-129">空間マッピングデータは、アプリケーションが使用できる最も負荷の高いデータソースです。</span><span class="sxs-lookup"><span data-stu-id="26538-129">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="26538-130">フレームの破棄や途切れなどのパフォーマンスの問題を回避するには、このデータの消費を慎重に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="26538-130">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="26538-131">エクスペリエンス中のアクティブなスキャンは、利点と弊害の両方になる可能性があり、開発者はエクスペリエンスに基づいてどの方法を使用するかを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="26538-131">Active scanning during an experience can be both beneficial or detrimental and the developer will need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="26538-132">キャッシュされた空間マッピング</span><span class="sxs-lookup"><span data-stu-id="26538-132">Cached spatial mapping</span></span>

<span data-ttu-id="26538-133">キャッシュされた空間マッピングの場合、アプリケーションは通常、空間マッピングデータのスナップショットを取得し、エクスペリエンスの間、このスナップショットを使用します。</span><span class="sxs-lookup"><span data-stu-id="26538-133">In the case of cached spatial mapping, the application typically takes a snapshot of the spatial mapping data and uses this snapshot for the duration of the experience.</span></span>

<span data-ttu-id="26538-134">**メリット**</span><span class="sxs-lookup"><span data-stu-id="26538-134">**Benefits**</span></span>
* <span data-ttu-id="26538-135">エクスペリエンスの実行中にシステムのオーバーヘッドを削減し、電力、温度、および cpu のパフォーマンスを大幅に向上させます。</span><span class="sxs-lookup"><span data-stu-id="26538-135">Reduced overhead on the system while the experience is running leading to dramatic power, thermal and cpu performance gains.</span></span>
* <span data-ttu-id="26538-136">空間データ内の変更によって中断されないため、メインエクスペリエンスをより簡単に実装できます。</span><span class="sxs-lookup"><span data-stu-id="26538-136">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="26538-137">物理、グラフィックス、およびその他の目的で空間データの後処理を行う1回限りのコスト。</span><span class="sxs-lookup"><span data-stu-id="26538-137">A single one time cost on any post processing of the spatial data for physics, graphics and other purposes.</span></span>

<span data-ttu-id="26538-138">**デメリット**</span><span class="sxs-lookup"><span data-stu-id="26538-138">**Drawbacks**</span></span>
* <span data-ttu-id="26538-139">実際のオブジェクトまたはオブジェクトの移動は、キャッシュされたデータに反映されません。</span><span class="sxs-lookup"><span data-stu-id="26538-139">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="26538-140">例:</span><span class="sxs-lookup"><span data-stu-id="26538-140">E.g.</span></span> <span data-ttu-id="26538-141">アプリケーションでは、実際に閉じられたときにドアが開いていると考えられる場合があります。</span><span class="sxs-lookup"><span data-stu-id="26538-141">the application might consider a door open when it is actually closed now.</span></span>
* <span data-ttu-id="26538-142">キャッシュされたバージョンのデータを維持するために、アプリケーションメモリが増える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="26538-142">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="26538-143">この方法の良いケースは、制御された環境またはテーブルトップのゲームです。</span><span class="sxs-lookup"><span data-stu-id="26538-143">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="26538-144">連続空間マッピング</span><span class="sxs-lookup"><span data-stu-id="26538-144">Continuous spatial mapping</span></span>

<span data-ttu-id="26538-145">特定のアプリケーションは、スキャンを続行して空間マッピングデータを更新することがあります。</span><span class="sxs-lookup"><span data-stu-id="26538-145">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="26538-146">**メリット**</span><span class="sxs-lookup"><span data-stu-id="26538-146">**Benefits**</span></span>
* <span data-ttu-id="26538-147">アプリケーションでは、個別にスキャンや探索を行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="26538-147">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="26538-148">実際のオブジェクトの動きはゲームによって反映されますが、少し時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="26538-148">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="26538-149">**デメリット**</span><span class="sxs-lookup"><span data-stu-id="26538-149">**Drawbacks**</span></span>
* <span data-ttu-id="26538-150">メインエクスペリエンスの実装がより複雑になります。</span><span class="sxs-lookup"><span data-stu-id="26538-150">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="26538-151">変化に応じてグラフィックまたは物理の追加処理のオーバーヘッドが発生する可能性があるため、これらのシステムによって段階的に取り込まれたを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="26538-151">Potential overhead of the additional processing for graphic or physics as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="26538-152">電力、温度、および CPU の影響力が高くなります。</span><span class="sxs-lookup"><span data-stu-id="26538-152">Higher power, thermal and CPU impact.</span></span>

<span data-ttu-id="26538-153">このメソッドの優れたケースは、ホログラムがオブジェクトの移動と対話することが予想される場合です。たとえば、holographic 自動車では、床の上のドライブが、開いているか閉じているかに応じて、ドアに正しく入る必要があります。</span><span class="sxs-lookup"><span data-stu-id="26538-153">A good case for this method is one where holograms are expected to interact with moving objects, e.g. a holographic car that drives on the floor may want to correctly bump into a door depending on whether it is open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="26538-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="26538-154">See also</span></span>
* [<span data-ttu-id="26538-155">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="26538-155">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="26538-156">座標系</span><span class="sxs-lookup"><span data-stu-id="26538-156">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="26538-157">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="26538-157">Spatial sound design</span></span>](spatial-sound-design.md)
