---
title: Windows Mixed Reality を使用した場所ベースのエンターテインメント
description: 場所に基づくエンターテインメント (ハードウェア、backpack Pc、追跡、構成、サポート) のための Windows Mixed Reality について説明します。
author: jessemcculloch
ms.author: ishitak
ms.date: 08/03/2020
ms.topic: article
keywords: mixed reality、vr、lbe、場所、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、ハードウェア、HoloLens、マルチプレーヤー、クラウドサービス、azure
ms.openlocfilehash: 49e96b99d3f74bd24a4a0e71f212018108148ad2
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236913"
---
# <a name="location-based-entertainment-with-windows-mixed-reality"></a><span data-ttu-id="e34df-104">Windows Mixed Reality を使用した場所ベースのエンターテインメント</span><span class="sxs-lookup"><span data-stu-id="e34df-104">Location Based Entertainment with Windows Mixed Reality</span></span>

<span data-ttu-id="e34df-105">過去数年では、場所ベースのエンターテインメントカテゴリに非常に多くの成長とイノベーションが見られました。</span><span class="sxs-lookup"><span data-stu-id="e34df-105">In the last couple of years, we've seen an incredible amount of growth and innovation in the Location Based Entertainment category.</span></span> <span data-ttu-id="e34df-106">テーマの公園やシアターなどの従来の会場は、既存のサービスやインストールに対する優れたエクスペリエンスとして、イマーシブ、マルチプレーヤーエクスペリエンスを提供するようになりました。</span><span class="sxs-lookup"><span data-stu-id="e34df-106">Traditional venues like theme parks and theaters have started offering immersive, multi-player experiences as complimentary experiences to existing rides and installations.</span></span> <span data-ttu-id="e34df-107">新しいオペレーターと会場は、一意のマルチ sensorial、マルチプレーヤーエクスペリエンスを、大量に魅力的な価格でもたらします。</span><span class="sxs-lookup"><span data-stu-id="e34df-107">New operators and venues are bringing unique multi-sensorial, multi-player experiences at an attractive price to the masses.</span></span> <span data-ttu-id="e34df-108">これらのすべてのエクスペリエンスでは、mixed reality でできることについて、エンベロープをプッシュしています。</span><span class="sxs-lookup"><span data-stu-id="e34df-108">All of these experiences are pushing the envelope for what’s possible with mixed reality.</span></span>

<span data-ttu-id="e34df-109">このドキュメントは、[場所ベースのエンターテインメント] カテゴリで Windows Mixed Reality の使用を開始するためのガイドです。</span><span class="sxs-lookup"><span data-stu-id="e34df-109">This document is a guide to get started with Windows Mixed Reality in the Location Based Entertainment category.</span></span> <span data-ttu-id="e34df-110">以下のガイダンスは、トレーニング、製品設計、およびその他のユースケースなど、エンターテインメント以外の場所ベースのエクスペリエンスにも適用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="e34df-110">The guidance below may additionally be applicable to location-based experiences beyond entertainment such as training, product design, and other use cases.</span></span>

## <a name="engineering-faq"></a><span data-ttu-id="e34df-111">エンジニアリングに関する FAQ</span><span class="sxs-lookup"><span data-stu-id="e34df-111">Engineering FAQ</span></span>

### <a name="hardware"></a><span data-ttu-id="e34df-112">ハードウェア</span><span class="sxs-lookup"><span data-stu-id="e34df-112">Hardware</span></span>

<span data-ttu-id="e34df-113">**Q: Microsoft とそのパートナーがセットアップで使用できるハードウェアはどのようなものですか。**</span><span class="sxs-lookup"><span data-stu-id="e34df-113">**Q: What hardware is available from Microsoft and its partners that I can use in my setup?**</span></span>

<span data-ttu-id="e34df-114">A: Microsoft とその OEM パートナーは、ニーズに応じて選択する、説得力のあるデバイスのポートフォリオを提供します。</span><span class="sxs-lookup"><span data-stu-id="e34df-114">A: Microsoft and its OEM partners offer a compelling portfolio of devices to choose from depending on your needs.</span></span>  

<span data-ttu-id="e34df-115">お客様に提供しているエクスペリエンスで仮想現実のヘッドセットが必要な場合は、HP、Samsung、Acer の市場でのヘッドセットが非常に適しています。</span><span class="sxs-lookup"><span data-stu-id="e34df-115">If the experiences you’re providing to your customers requires a virtual reality headset, in-market headsets from HP, Samsung, and Acer are a great fit.</span></span> <span data-ttu-id="e34df-116">各ヘッドセットには独自の区別された属性があります。</span><span class="sxs-lookup"><span data-stu-id="e34df-116">Each headset has their own differentiated attributes.</span></span> <span data-ttu-id="e34df-117">詳細については、以下を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e34df-117">More details on each below.</span></span>

<span data-ttu-id="e34df-118">HP リバーブ: [詳細](https://hp.com/go/Reverbpro)</span><span class="sxs-lookup"><span data-stu-id="e34df-118">HP Reverb: [Details](https://hp.com/go/Reverbpro)</span></span>

<span data-ttu-id="e34df-119">Samsung Odyssey +: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span><span class="sxs-lookup"><span data-stu-id="e34df-119">Samsung Odyssey+: [Details](https://www.samsung.com/us/computing/hmd/windows-mixed-reality/hmd-odyssey-windows-mixed-reality-headset-xe800zba-hc1us/)</span></span>

<span data-ttu-id="e34df-120">Acer: [詳細](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span><span class="sxs-lookup"><span data-stu-id="e34df-120">Acer: [Details](https://www.acer.com/ac/en/US/content/model/VD.R05AP.002)</span></span>

<span data-ttu-id="e34df-121">お客様の場所で、「」を参照して、ヘッドセットを使用した、mixed または拡張された現実エクスペリエンスを専門とする場合は、Microsoft HoloLens 2 をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e34df-121">If your location specializes in mixed or augmented reality experiences with see-through headsets, check out the Microsoft HoloLens 2.</span></span>  

<span data-ttu-id="e34df-122">HoloLens 2: [注文前の関心](https://www.microsoft.com//hololens/buy)</span><span class="sxs-lookup"><span data-stu-id="e34df-122">HoloLens 2: [Pre-order interest](https://www.microsoft.com//hololens/buy)</span></span>

<span data-ttu-id="e34df-123">高度なコンピュータービジョン、音声、および本文の追跡を使用する経験をお持ちの場合は、Azure Kinect DK が最適です。</span><span class="sxs-lookup"><span data-stu-id="e34df-123">If you’re experimenting with experiences that use advanced computer vision, speech, and body tracking, the Azure Kinect DK is a good fit.</span></span>  

<span data-ttu-id="e34df-124">Azure Kinect: [詳細](https://azure.microsoft.com//services/kinect-dk/)</span><span class="sxs-lookup"><span data-stu-id="e34df-124">Azure Kinect: [Details](https://azure.microsoft.com//services/kinect-dk/)</span></span>

<span data-ttu-id="e34df-125">**Q: PC-テザリングさ VR エクスペリエンスを実行するために使用できる backpack Pc のポートフォリオは何ですか。**</span><span class="sxs-lookup"><span data-stu-id="e34df-125">**Q: What is the portfolio of backpack PCs I can use to run my PC-tethered VR experiences?**</span></span>

<span data-ttu-id="e34df-126">PC-テザリングさ VR エクスペリエンスの場合、Oem は、ニーズに応じて正確に構築された backpack Pc を非常に優れた選択肢として提供しています。</span><span class="sxs-lookup"><span data-stu-id="e34df-126">For PC-tethered VR experiences, our OEMs offer an incredible selection of backpack PCs built exactly for that need.</span></span>

<span data-ttu-id="e34df-127">HP は HP VR backpack G2 を起動しました。これは、無料ローミングエクスペリエンスのために最適化された、現在のところ、RTX 2080 GPU では30% 向上しています。</span><span class="sxs-lookup"><span data-stu-id="e34df-127">HP just launched their HP VR backpack G2, the world’s most powerful wearable PC – optimized for free-roam experiences, now with 30% more power with an RTX 2080 GPU inside.</span></span> [<span data-ttu-id="e34df-128">詳細</span><span class="sxs-lookup"><span data-stu-id="e34df-128">Details</span></span>](https://www8.hp.com/us/en/vr/vr-backpack.html)

### <a name="setup"></a><span data-ttu-id="e34df-129">セットアップ</span><span class="sxs-lookup"><span data-stu-id="e34df-129">Setup</span></span>

<span data-ttu-id="e34df-130">**Q: セットアップを簡単に構成し、LBE 用に Mixed Reality ポータルをカスタマイズするにはどうすればよいですか。**</span><span class="sxs-lookup"><span data-stu-id="e34df-130">**Q: How can I more easily configure setup and customize the Mixed Reality Portal for LBE?**</span></span>

>[!NOTE]
><span data-ttu-id="e34df-131">この機能には、バージョン2000.19061.1011.0 以上が必要です。</span><span class="sxs-lookup"><span data-stu-id="e34df-131">This feature requires version 2000.19061.1011.0 or greater.</span></span>  

<span data-ttu-id="e34df-132">アプリをキオスクまたはカスタマイズされたエクスペリエンスにデプロイするためにアプリで通常利用できるものよりも、混合の現実ポータルのカスタマイズが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="e34df-132">You may find that you need more customization of Mixed Reality Portal than is normally available through the app for deploying apps to kiosks or customized experiences.</span></span> <span data-ttu-id="e34df-133">最新の7月の Mixed Reality ポータルの更新では、構成ファイルを使用して設定できるいくつかの詳細設定がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e34df-133">The latest July update of Mixed Reality Portal supports several advanced settings, which you can set via a configuration file:</span></span>  

<span data-ttu-id="e34df-134">[失敗したシステムチェックを許可する] –セットアップを完了する前に、セットアッププロセスによって、PC が Windows Mixed Reality との互換性を確認します。</span><span class="sxs-lookup"><span data-stu-id="e34df-134">Allow failed system checks – normally the setup process checks the PC for compatibility with Windows Mixed Reality before completing setup.</span></span> <span data-ttu-id="e34df-135">互換性チェックを省略すると、互換性の問題がある場合に Windows Mixed Reality を実行しようとすると問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e34df-135">Bypassing compatibility checks may cause issues when trying to run Windows Mixed Reality if there are compatibility issues.</span></span>  

<span data-ttu-id="e34df-136">デバイスコンパニオンアプリのスキップ– DCA は製造元によって提供されるヘッドセット固有のセットアップ手順を提供し、ヘッドセットのファームウェアを更新できます。</span><span class="sxs-lookup"><span data-stu-id="e34df-136">Skip Device Companion App – the DCA provides headset-specific setup steps provided by the manufacturer and allows for updating the headset’s firmware.</span></span>  

<span data-ttu-id="e34df-137">ルームのセットアップをスキップする–部屋の境界を作成するように求めるメッセージが表示されるのではなく、装着済み/継続モードのヘッドセットに直接進むことができます。</span><span class="sxs-lookup"><span data-stu-id="e34df-137">Skip room setup – instead of being prompted to create a room boundary, you can continue directly into the headset in Seated/Standing mode.</span></span>  

<span data-ttu-id="e34df-138">ストアからのアプリのインストールをスキップする-標準セットアップでは、3D ビューアーと Edge 360 ビューアーアドオンを含む、いくつかのストアアプリがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e34df-138">Skip installing apps from the Store - normal setup installs several Store apps including 3D Viewer and the Edge 360 Viewer add-on.</span></span> <span data-ttu-id="e34df-139">これにより、これらのアプリのインストールはスキップされますが、デバイスの機能が不足している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e34df-139">This will skip the install of these apps, but you may be missing device functionality.</span></span>  

<span data-ttu-id="e34df-140">全画面表示でプレビューを表示する: 混合 Reality ポータルでは、ヘッドセットが使用されている間、デスクトップ PC に全画面表示でヘッドセットのプレビューが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="e34df-140">Show preview in full screen – Mixed Reality Portal will default to showing the headset preview in full-screen on the desktop PC while the headset is in use.</span></span>  

<span data-ttu-id="e34df-141">サイドパネルの [新規] を非表示にする– Mixed Reality ポータルの起動時にパネルの新しいが展開されないようにします。</span><span class="sxs-lookup"><span data-stu-id="e34df-141">Hide New for you side panel – prevents the New for you panel from being expanded on launch of Mixed Reality Portal.</span></span>  

#### <a name="how-to-configure"></a><span data-ttu-id="e34df-142">構成方法:</span><span class="sxs-lookup"><span data-stu-id="e34df-142">How to configure:</span></span>  

<span data-ttu-id="e34df-143">これらの構成のいずれかを設定するには、次 _のディレクトリにUserConfig.js_ という名前のファイルを作成する必要があります: _$env: Localappdata\packages\ Microsoft.MixedReality.Portal_8wekyb3d8bbwe \ localstate \\_</span><span class="sxs-lookup"><span data-stu-id="e34df-143">To set any of these configurations, you need to create a file called _UserConfig.json_ under this directory: _$env:LOCALAPPDATA\Packages\Microsoft.MixedReality.Portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="e34df-144">ほとんどのユーザーにとって、次のようになります: _C:\Users \<username> \Appdata\local\packages\ Microsoft.mixedreality.portal_8wekyb3d8bbwe \ localstate \\_</span><span class="sxs-lookup"><span data-stu-id="e34df-144">For most users, this will look like: _C:\Users\<username>\AppData\Local\Packages\microsoft.mixedreality.portal_8wekyb3d8bbwe\LocalState\\_</span></span>

<span data-ttu-id="e34df-145">JSON ファイルの内容は、有効にする上記の設定のいずれかに対して "true" が設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e34df-145">The JSON file should have the below contents with “true” set for any of the above settings you want enabled:</span></span>  

```
{

  "shouldAllowFailedSystemChecks": true,

  "shouldSkipDcaApp": true,

  "shouldSkipRoomSetup": true,

  "shouldSkipStoreAppInstall": true,

  "shouldShowPreviewFullScreen": true,

  "shouldHideEngagementPane": true

}
```
 
<span data-ttu-id="e34df-146">**Q: playspace の構成についてのガイダンスはありますか。**</span><span class="sxs-lookup"><span data-stu-id="e34df-146">**Q: Is there any guidance on configuring the playspace?**</span></span>

<span data-ttu-id="e34df-147">A: playspace の構成は、コンシューマーのセットアップエクスペリエンスの場合と同じように行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e34df-147">A: Configuring a playspace should be done as you would with a consumer setup experience.</span></span> <span data-ttu-id="e34df-148">ルームのセットアッププロセスでは、部屋の境界を定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="e34df-148">The Room Setup process will also let you define your room boundaries.</span></span> <span data-ttu-id="e34df-149">ルーム境界の構成の詳細については、 [こちら](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e34df-149">More details on configuring room boundaries can be read [here](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="e34df-150">上のドキュメントで説明したように、最大の適正な1座標の再生領域は5mx5m を中心にしています。</span><span class="sxs-lookup"><span data-stu-id="e34df-150">As discussed in the above document the maximum reasonable single coordinate playspace is around 5mx5m.</span></span> <span data-ttu-id="e34df-151">より大きな領域を作成する場合は、Windows Holographic API スタックで空間アンカー機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e34df-151">If you want to have a larger area, you can make use of the Spatial Anchors capability in the Windows Holographic API stack.</span></span> <span data-ttu-id="e34df-152">この API を使用するには、生成中のエクスペリエンスにカスタムエンジニアリングが必要です。</span><span class="sxs-lookup"><span data-stu-id="e34df-152">Using this API will require custom engineering in the experiences you're producing.</span></span>  

<span data-ttu-id="e34df-153">さまざまな領域サイズに合わせてコンテンツを最適化する方法の詳細については、 [こちら](/windows/mixed-reality/coordinate-systems)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e34df-153">More details on how to optimize your content for different space sizes can be read [here](/windows/mixed-reality/coordinate-systems).</span></span>
 

<span data-ttu-id="e34df-154">**Q: 空間が大きすぎて、境界を使用して継続的なエクスペリエンスを設定しようとしたときにエラーが発生しています。大規模な無料ローミングエクスペリエンスを設定するにはどうすればよいですか。**</span><span class="sxs-lookup"><span data-stu-id="e34df-154">**Q: My space is too large and I’m running into errors when I try to set up a Standing experience with boundaries. What should I do to set up my large free-roam experience work?**</span></span>

<span data-ttu-id="e34df-155">A: ~ 18x18ft よりも大きな領域を設定する場合、システムによって提供される境界を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="e34df-155">A: To set up a larger space than ~18x18ft, you can't use the boundary experience provided by the system.</span></span>  <span data-ttu-id="e34df-156">境界システムは、1つの固定座標 "アンカー" に依存しています。これは、中央のステージアンカーから離れすぎていると不安定になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e34df-156">The boundary systems rely on a single fixed coordinate “anchor”, which can become unstable when a user is too far from the center stage anchor.</span></span> 

<span data-ttu-id="e34df-157">"固定" モードを設定できます。このモードでは、境界が表示されたり、ステージの境界や再生空間が構成されたりしません。</span><span class="sxs-lookup"><span data-stu-id="e34df-157">You can set up “seated” mode, which won't display the boundary or configure a stage bounds or playspace.</span></span>  <span data-ttu-id="e34df-158">物理的な境界領域を参照するには、アプリ内に複数の空間アンカーを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e34df-158">You’ll need to configure multiple spatial anchors within the app to reference physical boundary areas.</span></span> 

<span data-ttu-id="e34df-159">アプリケーション開発者は、ユーザーが物理的な環境と競合しないように、必要なセーフガードを表示する責任があります。</span><span class="sxs-lookup"><span data-stu-id="e34df-159">The application developer is responsible to display necessary safeguards so that users don’t collide with physical surroundings.</span></span>  <span data-ttu-id="e34df-160">これらは、エクスペリエンス内のデジタル壁面や、カスタマイズされたゲームの境界ビジュアルです。</span><span class="sxs-lookup"><span data-stu-id="e34df-160">These could be digital walls within the experience or a customized game boundary visual.</span></span> 

<span data-ttu-id="e34df-161">WMR を使用したルーム境界の設定に関するガイダンスについては、 [こちら](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e34df-161">Guidance on setting up the room boundary with WMR can be found [here](/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary).</span></span>

<span data-ttu-id="e34df-162">**Q: playspace の起点はどこですか。**</span><span class="sxs-lookup"><span data-stu-id="e34df-162">**Q: Where is the origin of the playspace?**</span></span>

<span data-ttu-id="e34df-163">A: playspace の原点は、セットアップ中にセンターボタンが押されたときに、ルームのセットアップエクスペリエンスによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="e34df-163">A: The origin of the playspace is determined by the Room Setup experience, more specifically the HMD position when the Center button is pressed during setup.</span></span> 

### <a name="multi-player-setup"></a><span data-ttu-id="e34df-164">マルチプレーヤーセットアップ</span><span class="sxs-lookup"><span data-stu-id="e34df-164">MULTI-PLAYER SETUP</span></span>

<span data-ttu-id="e34df-165">**Q: 自分の会場で、マルチプレーヤーエクスペリエンスをデプロイしています。Windows Mixed Reality ではサポートされていますか。**</span><span class="sxs-lookup"><span data-stu-id="e34df-165">**Q: I’m deploying a multi-player experience in at my venue. Is that supported on Windows Mixed Reality?**</span></span>

<span data-ttu-id="e34df-166">A: Insider プログラムを使用して Windows 20H1 以降のビルドを選択すると、マップ共有用の新しいインターフェイスにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="e34df-166">A: If you opt into the Windows 20H1 or later build via our Insider program, you can access a new interface for map sharing.</span></span> <span data-ttu-id="e34df-167">この新しい機能は、Windows デバイスポータルの [マップマネージャー](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) インターフェイスを使用して入手できます。</span><span class="sxs-lookup"><span data-stu-id="e34df-167">This new functionality is available via the [Map Manager](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) interface of the Windows Device portal.</span></span> <span data-ttu-id="e34df-168">このツールを使用するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e34df-168">To use this tool, follow the steps below:</span></span>
* <span data-ttu-id="e34df-169">2019年9月以降のバージョンである20H1 以降を選択していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e34df-169">Make sure you're opted into 20H1 or later - after September 2019, this means using our Insider program</span></span>
* <span data-ttu-id="e34df-170">次の[手順](/windows/uwp/debug-test-perf/device-portal-desktop)に従って、Windows デバイスポータル (WDP) を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e34df-170">Enable the Windows Device Portal (WDP) using these [instructions](/windows/uwp/debug-test-perf/device-portal-desktop)</span></span>
* <span data-ttu-id="e34df-171">既存のマップをダウンロードするか、新しいマップをインポートする Windows Mixed Reality HMD をプラグインします。</span><span class="sxs-lookup"><span data-stu-id="e34df-171">Plug in a Windows Mixed Reality HMD that you wish to either download an existing map from or import a new map</span></span>
* <span data-ttu-id="e34df-172">[設定] 画面で指定した URL を使用して、選択したブラウザーの WDP に移動します。</span><span class="sxs-lookup"><span data-stu-id="e34df-172">Navigate to the WDP in your browser of choice using the URL provided in the settings screen.</span></span>
    * <span data-ttu-id="e34df-173">その後、"Mixed Reality" セクションに移動し、[マップマネージャー] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e34df-173">Once there Navigate to the "Mixed Reality" section and select "Map Manager".</span></span>
    * <span data-ttu-id="e34df-174">[ダウンロード] ボタンを使用して、コンピューターから既存のマップをエクスポートできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e34df-174">You can now use the "Download" button to export an existing map from the machine.</span></span>
    * <span data-ttu-id="e34df-175">[マップファイルのアップロード] ボタンを使用すると、以前のエクスポートからマップをインポートできます (おそらく、別のコンピューターにあります)。</span><span class="sxs-lookup"><span data-stu-id="e34df-175">You can use the "Upload a map file" button to import a map from a previous export (perhaps on a different machine).</span></span>
    * <span data-ttu-id="e34df-176">"Import" を使用して、システムがこのコンピューター上のこの HMD に対してこのマップを使用できるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="e34df-176">You can use "Import" to enable the system to use that map for this HMD on this machine.</span></span>

> [!NOTE] 
> <span data-ttu-id="e34df-177">以前は、空間データパッケージャーツールを使用することができましたが、そのツールは当初はサポートされていないものとしてリリースされており、公式に非推奨とされ、20H1 では機能しなくなりました。</span><span class="sxs-lookup"><span data-stu-id="e34df-177">Previously, it was possible to use the Spatial Data Packager Tool, however, that tool was originally released as unsupported and is now officially deprecated and no longer functional on 20H1.</span></span> <span data-ttu-id="e34df-178">代わりに、前に説明したように、受信トレイ [マップマネージャー](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) ツールを使用してください。</span><span class="sxs-lookup"><span data-stu-id="e34df-178">Instead, please use the inbox [Map Manager](../develop/platform-capabilities-and-apis/using-the-windows-device-portal.md#map-manager) tool as described above.</span></span> 

### <a name="tracking"></a><span data-ttu-id="e34df-179">追跡</span><span class="sxs-lookup"><span data-stu-id="e34df-179">TRACKING</span></span>

<span data-ttu-id="e34df-180">Q: Windows Mixed Reality ヘッドセットの追跡テクノロジはどのように動作しますか。</span><span class="sxs-lookup"><span data-stu-id="e34df-180">Q: How does the tracking technology in the Windows Mixed Reality headsets work?</span></span>  

<span data-ttu-id="e34df-181">Mixed Reality は、HoloLens と同じ追跡テクノロジを共有します。</span><span class="sxs-lookup"><span data-stu-id="e34df-181">Mixed Reality shares the same tracking technology as the HoloLens.</span></span> <span data-ttu-id="e34df-182">内部アウト追跡システムの詳細については、 [こちら](/windows/mixed-reality/enthusiast-guide/tracking-system)のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e34df-182">To learn more about the inside-out tracking system, check out the documentation [here](/windows/mixed-reality/enthusiast-guide/tracking-system).</span></span>

<span data-ttu-id="e34df-183">上位レベルの空間マッピングシステムの動作の詳細については、 [こちらで](../design/spatial-mapping.md)説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e34df-183">For a description of how the higher-level spatial mapping system works you can read our description [here](../design/spatial-mapping.md).</span></span>

<span data-ttu-id="e34df-184">**Q: reliable tracking ボリュームを取得するためのベストプラクティスはありますか。**</span><span class="sxs-lookup"><span data-stu-id="e34df-184">**Q: Are there any best practices for getting a reliable tracking volume?**</span></span>

<span data-ttu-id="e34df-185">成功を追跡するために環境を最適に構成するには、この [投稿](/hololens/hololens-environment-considerations)のベストプラクティスを読むことができます。</span><span class="sxs-lookup"><span data-stu-id="e34df-185">To best configure the environment for tracking success, you can read best practices in this [post](/hololens/hololens-environment-considerations).</span></span>

<span data-ttu-id="e34df-186">**Q: ウェアハウスでの追跡には特定の差異がありますか? スケールスペースや最適化を検討してください。**</span><span class="sxs-lookup"><span data-stu-id="e34df-186">**Q: Are there any specific nuances with tracking in warehouse-scale spaces or optimizations to consider?**</span></span>

<span data-ttu-id="e34df-187">A: 次のプラクティスは、より信頼性の高い追跡ボリュームを取得するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e34df-187">A: The following practices can help with getting a more reliable tracking volume:</span></span>  

<span data-ttu-id="e34df-188">複数の位置で重なり合うさまざまな機能を部屋に用意することにより、追跡システムが安定したロックを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="e34df-188">Providing different features in the room that overlap at multiple positions will help the tracking system get a solid lock.</span></span> <span data-ttu-id="e34df-189">単色の輪郭スタイルの線を使用するのではなく、ランダムな描画の splatters と陰影を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="e34df-189">Think of random paint splatters and hatching rather than using solid contour style lines.</span></span> 

<span data-ttu-id="e34df-190">可能な場合は、領域内の照明の動的範囲を最小化します。</span><span class="sxs-lookup"><span data-stu-id="e34df-190">Minimize the dynamic range of lighting in your area where possible.</span></span> <span data-ttu-id="e34df-191">混合現実 HMDs の追跡カメラは HDR ではなく、AGC (自動利得) と AEC (自動露出) によってさまざまな照明を扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="e34df-191">The tracking cameras on our Mixed Reality HMDs aren't HDR and have AGC (auto gain) and AEC (auto exposure) going to deal with different lighting.</span></span> <span data-ttu-id="e34df-192">表面光、パターン、およびコントラストの分布によっては、AGC または AEC によって、すべての白または黒の部屋にいることがわかっている場合があります。これにより、反対の "色" の機能が薄く表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e34df-192">Depending on the distribution of surface light, patterns and contrast, either AGC or AEC may conclude you’re in a much all white or black room, which can wash out your features that may be in the opposite “color”.</span></span> <span data-ttu-id="e34df-193">明るい日光を持つ外部ウィンドウの前に内部の画像を撮影しようとしているときに、露出を調整して詳細を見ることができるようにする場合、内部のすべてのものは underexposed と黒色です。</span><span class="sxs-lookup"><span data-stu-id="e34df-193">If you're trying to take an interior picture in front of an exterior window with bright daylight behind and you adjust exposure so you can see detail outside, then everything on the interior is underexposed and black.</span></span> <span data-ttu-id="e34df-194">または、内に設定されている場合、以外のすべてが overexposed、すべて白になります。</span><span class="sxs-lookup"><span data-stu-id="e34df-194">Or if set for inside, then everything outside is now overexposed and all white.</span></span>  

<span data-ttu-id="e34df-195">トラックカメラが発生されることがあり、追跡カメラの AEC/AGC が混乱する可能性がある場合に、表示される部屋 (オーバーヘッド) にスポットライト。</span><span class="sxs-lookup"><span data-stu-id="e34df-195">Spotlights in a room (even overhead) that are in view if tracking cameras can sometimes be culprits, which confuse the AEC/AGC of the tracking cameras.</span></span> <span data-ttu-id="e34df-196">フラット/拡散照明が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e34df-196">Flat/diffused lighting helps.</span></span>  

### <a name="mixed-reality-cloud-services-and-azure"></a><span data-ttu-id="e34df-197">MIXED REALITY クラウドサービスと AZURE</span><span class="sxs-lookup"><span data-stu-id="e34df-197">MIXED REALITY CLOUD SERVICES AND AZURE</span></span> 

<span data-ttu-id="e34df-198">**Q: どのようにしてビジネススケールを Microsoft Azure できますか。**</span><span class="sxs-lookup"><span data-stu-id="e34df-198">**Q: How can Microsoft Azure help my business scale?**</span></span>

<span data-ttu-id="e34df-199">A: Azure ベースのオンサイトおよびリモート管理を使用すると、ビジネスをデータ主導にすることができ、運用コストが削減され、既存の場所と新しい場所でのデプロイをスケーリングできます。</span><span class="sxs-lookup"><span data-stu-id="e34df-199">A: Azure based onsite and remote management can help your business be data-driven, reduce operational costs and scale deployment across existing and new locations.</span></span> <span data-ttu-id="e34df-200">Azure Storage、Azure Functions、App Service、Azure ネットワーク、IOT Hub などの azure クラウドサービスは、次のユースケースに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="e34df-200">Azure cloud services such as Azure Storage, Azure Functions, App Service, Azure Networking, and IOT Hub can help with the following use cases:</span></span>  

<span data-ttu-id="e34df-201">リモートデバイス展開 & 管理</span><span class="sxs-lookup"><span data-stu-id="e34df-201">Remote Device Deployment & Management</span></span> 

<span data-ttu-id="e34df-202">オンサイト分析の Real-Time</span><span class="sxs-lookup"><span data-stu-id="e34df-202">Real-Time Onsite Analytics</span></span> 

<span data-ttu-id="e34df-203">インテリジェントな適応性に優れたゲームプレイ</span><span class="sxs-lookup"><span data-stu-id="e34df-203">Intelligent Adaptable LBE Gameplay</span></span> 

<span data-ttu-id="e34df-204">LBE コンテンツのストリーミングとデプロイ</span><span class="sxs-lookup"><span data-stu-id="e34df-204">LBE Content Streaming and Deployment</span></span> 

<span data-ttu-id="e34df-205">LBE プレーヤーの基本設定ヒートマップ</span><span class="sxs-lookup"><span data-stu-id="e34df-205">LBE Player Preference Heatmap</span></span> 

<span data-ttu-id="e34df-206">LBE 予約と予約システム</span><span class="sxs-lookup"><span data-stu-id="e34df-206">LBE Reservation and Booking System</span></span> 

<span data-ttu-id="e34df-207">**Q: 空間 MMOG を開発して、大規模なフットプリントをデプロイしています。コンテンツとオブジェクトの永続化を管理するのに役立つすべてのサービス**</span><span class="sxs-lookup"><span data-stu-id="e34df-207">**Q: I’m developing a spatial MMOG to deploy over a massive footprint. Any services that help me manage my content and object persistence?**</span></span>

<span data-ttu-id="e34df-208">A: Azure 空間アンカーは、HoloLens、iOS、および Android デバイスで、複数のユーザーに対応し、空間的に対応した mixed reality エクスペリエンスを可能にする新しい Mixed Reality サービスです。</span><span class="sxs-lookup"><span data-stu-id="e34df-208">A: Azure Spatial Anchors is a new Mixed Reality service that enables multi-user, spatially aware mixed reality experiences across HoloLens, iOS, and Android devices.</span></span> <span data-ttu-id="e34df-209">Azure 空間アンカーの詳細については、 [こちら](https://azure.microsoft.com//services/spatial-anchors/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e34df-209">You can learn more about Azure Spatial Anchors [here](https://azure.microsoft.com//services/spatial-anchors/).</span></span>

<span data-ttu-id="e34df-210">**Q..この会場では、マルチプレーヤーエクスペリエンスを専門としており、開発時間をコンテンツやフロントエンド開発に専念させたいと考えています。バックエンド開発をブートストラップまたはオフロードするのに役立つサービスはありますか。**</span><span class="sxs-lookup"><span data-stu-id="e34df-210">**Q. Our venue specializes in multi-player experiences and I’d like to focus our development time on content and front-end development. Are there offerings that can help me bootstrap or offload backend development?**</span></span>

<span data-ttu-id="e34df-211">A: Azure PlayFab は、ライブゲーム用の完全なバックエンドプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="e34df-211">A: Azure PlayFab is a complete backend platform for live games.</span></span> <span data-ttu-id="e34df-212">詳細については、 [こちら](https://playfab.com/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e34df-212">You can learn more about it [here](https://playfab.com/).</span></span>

### <a name="misc"></a><span data-ttu-id="e34df-213">その他</span><span class="sxs-lookup"><span data-stu-id="e34df-213">Misc</span></span>

<span data-ttu-id="e34df-214">**Q: SteamVR を使用して自分のエクスペリエンスをデプロイします。Windows Mixed Reality は SteamVR と連携しますか。**</span><span class="sxs-lookup"><span data-stu-id="e34df-214">**Q: I use SteamVR to deploy my experiences. Does Windows Mixed Reality work with SteamVR?**</span></span>

<span data-ttu-id="e34df-215">A: SteamVR の Windows Mixed Reality では、ユーザーは Windows Mixed Reality のイマーシブヘッドセットで SteamVR エクスペリエンスを実行できます。</span><span class="sxs-lookup"><span data-stu-id="e34df-215">A: Windows Mixed Reality for SteamVR allows users to run SteamVR experiences on Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="e34df-216">SteamVR と WMR の詳細について [は、こちら](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e34df-216">Learn more about SteamVR with WMR [here](/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality).</span></span>

### <a name="support-and-community"></a><span data-ttu-id="e34df-217">サポートとコミュニティ</span><span class="sxs-lookup"><span data-stu-id="e34df-217">Support and community</span></span>  

<span data-ttu-id="e34df-218">チームで分野の専門家と連携し、トラブルシューティングサポートを受け、より広範な mixed reality 開発コミュニティに貢献するうえで役立つリソースがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="e34df-218">We have a few helpful resources to help you engage with subject matter experts on our team, get troubleshooting support, and contribute to the broader mixed reality dev community.</span></span>  

<span data-ttu-id="e34df-219">公開されているすべての機能で問題が発生した場合は、フィードバックハブを使用してバグを報告してください。ガイダンスについては、この [ページ](/windows/mixed-reality/enthusiast-guide/filing-feedback)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e34df-219">If you run into issues with any publicly released features, file a bug using Feedback Hub.For guidance, refer to this [page](/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span>

<span data-ttu-id="e34df-220">WMR のその他のトラブルシューティングのヘルプについては、カスタマーサポート [チームにお](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782) 問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="e34df-220">For other troubleshooting help with WMR, file a [support request](https://support.microsoft.com//supportforbusiness/productselection?sapId=96bfb202-bc79-741b-bf7a-774d8b767782) with our customer support team.</span></span>

<span data-ttu-id="e34df-221">HoloDevelopers の余裕期間チャネルに参加して、mixed reality 開発者と分野の専門家と連携します。 [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span><span class="sxs-lookup"><span data-stu-id="e34df-221">Join our HoloDevelopers Slack channel to engage with the mixed reality developers and subject matter experts: [aka.ms/holodevelopers](https://aka.ms/holodevelopers)</span></span>

<span data-ttu-id="e34df-222">Twitter: ニュース、イベント、および更新については、Mixed Reality 開発者関係チームに従ってください。 @MxdRealityDev</span><span class="sxs-lookup"><span data-stu-id="e34df-222">Twitter: Follow our Mixed Reality Developer Relations team for news, events, and updates @MxdRealityDev</span></span> 

<span data-ttu-id="e34df-223">サンフランシスコにいる場合、Microsoft リアクターでは常に何かが行われています。</span><span class="sxs-lookup"><span data-stu-id="e34df-223">If you happen to be in or around San Francisco, there’s always something going on at the Microsoft Reactor.</span></span> <span data-ttu-id="e34df-224">イベントのカレンダーを [ここ](https://developer.microsoft.com//reactor/Location/San%20Francisco)に表示できます。</span><span class="sxs-lookup"><span data-stu-id="e34df-224">You can see our calendar of events [here](https://developer.microsoft.com//reactor/Location/San%20Francisco).</span></span>
