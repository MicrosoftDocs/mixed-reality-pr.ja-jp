---
title: 部屋のスキャンの可視化
description: 空間マッピングを必要とするアプリケーションでは、デバイスを使用して、時間とセッションをまたいでデータを収集します。
author: mattzmsft
ms.author: alexpf
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, アプリパターン, 設計, HoloLens, ルームスキャン, 空間マッピング, メッシュ, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット, HoloLens
ms.openlocfilehash: 0bef09d7f023127f1f5eedf28065758b4a438f3e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583600"
---
# <a name="room-scan-visualization"></a><span data-ttu-id="d75b3-104">部屋のスキャンの可視化</span><span class="sxs-lookup"><span data-stu-id="d75b3-104">Room scan visualization</span></span>

<span data-ttu-id="d75b3-105">空間マッピングを必要とするアプリケーションは、時間の経過と共にデータを収集するためにデバイスに依存します。</span><span class="sxs-lookup"><span data-stu-id="d75b3-105">Applications that require spatial mapping rely on the device to collect data over time and across sessions.</span></span> <span data-ttu-id="d75b3-106">マッピングデータの完全性と品質は、ユーザーが実行した探索の量、探索から経過した時間、家具やドアなどのオブジェクトが領域をスキャンした後に移動されたかどうかなど、さまざまな要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="d75b3-106">The completeness and quality of the mapping data depends on many factors, including the amount of exploration the user has done, how much time has passed since the exploration, and whether objects such as furniture and doors have moved since the device scanned the area.</span></span>

<span data-ttu-id="d75b3-107">便利な空間マッピングデータを確保するために、アプリケーション開発者にはいくつかのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="d75b3-107">To ensure useful spatial mapping data, applications developers have several options:</span></span>
* <span data-ttu-id="d75b3-108">既に収集されている可能性があるものに依存します。</span><span class="sxs-lookup"><span data-stu-id="d75b3-108">Rely on what may have already been collected.</span></span> <span data-ttu-id="d75b3-109">このデータは、最初は不完全である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d75b3-109">This data may be incomplete initially.</span></span>
* <span data-ttu-id="d75b3-110">ブルームジェスチャを使用して Windows Mixed Reality ホームにアクセスし、エクスペリエンスに使用する領域を調べるようにユーザーに依頼します。</span><span class="sxs-lookup"><span data-stu-id="d75b3-110">Ask the user to use the bloom gesture to get to the Windows Mixed Reality home and then explore the area they wish to use for the experience.</span></span> <span data-ttu-id="d75b3-111">これらのユーザーは、すべての必要な領域がデバイスに認識されていることを、エアタップを使用して確認できます。</span><span class="sxs-lookup"><span data-stu-id="d75b3-111">They can use air-tap to confirm that all the necessary area is known to the device.</span></span>
* <span data-ttu-id="d75b3-112">独自のアプリケーションでカスタム探索エクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="d75b3-112">Build a custom exploration experience in their own application.</span></span>

<span data-ttu-id="d75b3-113">このような場合は、探索中に収集された実際のデータがシステムによって格納され、アプリケーションはこれを行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d75b3-113">In all these cases, the actual data gathered during the exploration is stored by the system and the application doesn't need to do this.</span></span>

## <a name="device-support"></a><span data-ttu-id="d75b3-114">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="d75b3-114">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="d75b3-115"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="d75b3-115"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="d75b3-116"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="d75b3-116"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="d75b3-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="d75b3-117"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="d75b3-118">部屋のスキャンの可視化</span><span class="sxs-lookup"><span data-stu-id="d75b3-118">Room scan visualization</span></span></td>
        <td><span data-ttu-id="d75b3-119">✔️</span><span class="sxs-lookup"><span data-stu-id="d75b3-119">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>



## <a name="building-a-custom-scanning-experience"></a><span data-ttu-id="d75b3-120">カスタムスキャンエクスペリエンスの構築</span><span class="sxs-lookup"><span data-stu-id="d75b3-120">Building a custom scanning experience</span></span>

<span data-ttu-id="d75b3-121">アプリケーションでは、エクスペリエンスの開始時に空間マッピングデータを分析して、ユーザーが完全性と品質を向上させるために追加の手順を実行する必要があるかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="d75b3-121">Applications may analyze the spatial mapping data at the start of the experience to judge whether they want the user to do extra steps to improve its completeness and quality.</span></span> <span data-ttu-id="d75b3-122">分析によって品質を向上させる必要がある場合は、開発者が視覚エフェクトを使用して、次のことを示す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d75b3-122">If analysis indicates quality should be improved, developers should provide a visualization to overlay on the world to indicate:</span></span>
* <span data-ttu-id="d75b3-123">ユーザーの近くにあるユーザーの合計ボリュームのうち、エクスペリエンスの一部として必要な量</span><span class="sxs-lookup"><span data-stu-id="d75b3-123">How much of the total volume in the users vicinity needs to be part of the experience</span></span>
* <span data-ttu-id="d75b3-124">データを改善するためにユーザーが行う必要がある場所</span><span class="sxs-lookup"><span data-stu-id="d75b3-124">Where the user should go to improve data</span></span>

<span data-ttu-id="d75b3-125">"良い" スキャンが行われていることをユーザーが認識していません。</span><span class="sxs-lookup"><span data-stu-id="d75b3-125">Users don't know what makes a "good" scan.</span></span> <span data-ttu-id="d75b3-126">スキャンを評価するよう求められた場合は、それらを表示または指定する必要があります。これは、実際の壁面からの距離など、スキャンを評価するように求められます。</span><span class="sxs-lookup"><span data-stu-id="d75b3-126">They need to be shown or told what to look for if they’re asked to evaluate a scan – flatness, distance from actual walls, and so on.</span></span> <span data-ttu-id="d75b3-127">開発者は、スキャンまたは探索フェーズでの空間マッピングデータの更新を含むフィードバックループを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d75b3-127">The developer should implement a feedback loop that includes refreshing the spatial mapping data during the scanning or exploration phase.</span></span>

<span data-ttu-id="d75b3-128">多くの場合、必要なスキャン品質を得るために必要な操作をユーザーに伝えることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d75b3-128">In many cases, it's best to tell the user what they need to do to get the necessary scan quality.</span></span> <span data-ttu-id="d75b3-129">たとえば、天井を見たり、家具を見たりします。</span><span class="sxs-lookup"><span data-stu-id="d75b3-129">For example, look at the ceiling, look behind furniture, and so on.</span></span>

## <a name="cached-versus-continuous-spatial-mapping"></a><span data-ttu-id="d75b3-130">キャッシュと連続空間マッピング</span><span class="sxs-lookup"><span data-stu-id="d75b3-130">Cached versus continuous spatial mapping</span></span>

<span data-ttu-id="d75b3-131">空間マッピングデータは、アプリケーションが使用できる最も負荷の高いデータソースです。</span><span class="sxs-lookup"><span data-stu-id="d75b3-131">The spatial mapping data is the most heavy weight data source applications can consume.</span></span> <span data-ttu-id="d75b3-132">フレームの破棄や途切れなどのパフォーマンスの問題を回避するには、このデータの消費を慎重に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d75b3-132">To avoid performance issues such as dropped frames or stuttering, consumption of this data should be done carefully.</span></span>

<span data-ttu-id="d75b3-133">エクスペリエンス中のアクティブなスキャンは、利点と悪影響を及ぼす可能性があるので、エクスペリエンスに基づいてどの方法を使用するかを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d75b3-133">Active scanning during an experience can be both beneficial and detrimental, so you'll need to decide which method to use based on the experience.</span></span>

### <a name="cached-spatial-mapping"></a><span data-ttu-id="d75b3-134">キャッシュされた空間マッピング</span><span class="sxs-lookup"><span data-stu-id="d75b3-134">Cached spatial mapping</span></span>

<span data-ttu-id="d75b3-135">キャッシュされた空間マッピングデータがある場合、アプリケーションは通常、空間マッピングデータのスナップショットを取得し、エクスペリエンス中にこのスナップショットを使用します。</span><span class="sxs-lookup"><span data-stu-id="d75b3-135">If there's cached spatial mapping data, the application typically takes a snapshot of the spatial mapping data and uses this snapshot during the experience.</span></span>

<span data-ttu-id="d75b3-136">**特典**</span><span class="sxs-lookup"><span data-stu-id="d75b3-136">**Benefits**</span></span>
* <span data-ttu-id="d75b3-137">エクスペリエンスの実行中にシステムのオーバーヘッドを削減し、電力、温度、および cpu のパフォーマンスを大幅に向上させます。</span><span class="sxs-lookup"><span data-stu-id="d75b3-137">Reduced overhead on the system while the experience is running leading to dramatic power, thermal, and cpu performance gains.</span></span>
* <span data-ttu-id="d75b3-138">空間データ内の変更によって中断されないため、メインエクスペリエンスをより簡単に実装できます。</span><span class="sxs-lookup"><span data-stu-id="d75b3-138">A simpler implementation of the main experience since it is not interrupted by changes in the spatial data.</span></span>
* <span data-ttu-id="d75b3-139">物理、グラフィックス、およびその他の目的で空間データの後処理を行う1回限りのコスト。</span><span class="sxs-lookup"><span data-stu-id="d75b3-139">A single one time cost on any post processing of the spatial data for physics, graphics, and other purposes.</span></span>

<span data-ttu-id="d75b3-140">**デメリット**</span><span class="sxs-lookup"><span data-stu-id="d75b3-140">**Drawbacks**</span></span>
* <span data-ttu-id="d75b3-141">実際のオブジェクトまたはオブジェクトの移動は、キャッシュされたデータに反映されません。</span><span class="sxs-lookup"><span data-stu-id="d75b3-141">The movement of real world objects or people is not reflected by the cached data.</span></span> <span data-ttu-id="d75b3-142">たとえば、アプリケーションでは、現在閉じられているドアを開いているとします。</span><span class="sxs-lookup"><span data-stu-id="d75b3-142">for example, the application might consider a door open when it's closed now.</span></span>
* <span data-ttu-id="d75b3-143">キャッシュされたバージョンのデータを維持するために、アプリケーションメモリが増える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d75b3-143">Potentially more application memory to maintain the cached version of the data.</span></span>

<span data-ttu-id="d75b3-144">この方法の良いケースは、制御された環境またはテーブルトップのゲームです。</span><span class="sxs-lookup"><span data-stu-id="d75b3-144">A good case for this method is a controlled environment or a table top game.</span></span>

### <a name="continuous-spatial-mapping"></a><span data-ttu-id="d75b3-145">連続空間マッピング</span><span class="sxs-lookup"><span data-stu-id="d75b3-145">Continuous spatial mapping</span></span>

<span data-ttu-id="d75b3-146">特定のアプリケーションは、スキャンを続行して空間マッピングデータを更新することがあります。</span><span class="sxs-lookup"><span data-stu-id="d75b3-146">Certain applications may rely on continues scanning to refresh spatial mapping data.</span></span>

<span data-ttu-id="d75b3-147">**特典**</span><span class="sxs-lookup"><span data-stu-id="d75b3-147">**Benefits**</span></span>
* <span data-ttu-id="d75b3-148">アプリケーションでは、個別にスキャンや探索を行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d75b3-148">You don't need to build in a separate scanning or exploration experience upfront in your application.</span></span>
* <span data-ttu-id="d75b3-149">実際のオブジェクトの動きはゲームによって反映されますが、少し時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="d75b3-149">The movement of real world objects can be reflected by the game, although with some delay.</span></span>

<span data-ttu-id="d75b3-150">**デメリット**</span><span class="sxs-lookup"><span data-stu-id="d75b3-150">**Drawbacks**</span></span>
* <span data-ttu-id="d75b3-151">メインエクスペリエンスの実装がより複雑になります。</span><span class="sxs-lookup"><span data-stu-id="d75b3-151">Higher complexity in the implementation of the main experience.</span></span>
* <span data-ttu-id="d75b3-152">これらのシステムで変更を段階的に取り込まれたする必要があるため、グラフィックと物理処理のオーバーヘッドが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d75b3-152">Potential overhead from the extra graphic and physics processing, as changes need to be incrementally ingested by these systems.</span></span>
* <span data-ttu-id="d75b3-153">高い電力、温度、CPU の影響。</span><span class="sxs-lookup"><span data-stu-id="d75b3-153">Higher power, thermal, and CPU impact.</span></span>

<span data-ttu-id="d75b3-154">このメソッドの優れたケースは、ホログラムがオブジェクトの移動と対話することが予想される場合です。たとえば、holographic 車は、開いているか閉じられているかに応じて、床の上にあるドライブがドアに入るようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="d75b3-154">A good case for this method is one where holograms are expected to interact with moving objects, for example, a holographic car that drives on the floor may want to bump into a door depending on whether it's open or closed.</span></span>

## <a name="see-also"></a><span data-ttu-id="d75b3-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="d75b3-155">See also</span></span>

* [<span data-ttu-id="d75b3-156">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="d75b3-156">Spatial mapping</span></span>](spatial-mapping.md)
* [<span data-ttu-id="d75b3-157">座標系</span><span class="sxs-lookup"><span data-stu-id="d75b3-157">Coordinate systems</span></span>](coordinate-systems.md)
* [<span data-ttu-id="d75b3-158">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="d75b3-158">Spatial sound design</span></span>](spatial-sound-design.md)