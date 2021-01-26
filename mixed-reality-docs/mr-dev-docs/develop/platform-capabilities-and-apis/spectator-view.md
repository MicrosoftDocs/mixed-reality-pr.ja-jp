---
title: Spectator View
description: 外付けデバイスからホログラムを視覚化して、外付けディスプレイで Mixed Reality エクスペリエンスを表示または記録します。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, カメラ, ARKit, HoloLens, 複合現実, MixedRealityToolkit, デモ, 記録
ms.openlocfilehash: aa85b54283b260447c36072b74031554e1aa1939
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583112"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="0ee8f-104">HoloLens および HoloLens 2 向けの Spectator View</span><span class="sxs-lookup"><span data-stu-id="0ee8f-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

<span data-ttu-id="0ee8f-106">HoloLens を装着していると、自分が見ている素晴らしい世界を、装着していない人は体験できないことを忘れがちです。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-106">When you're wearing a HoloLens, it's easy to forget a person without one can't experience the same wonders you're seeing.</span></span> <span data-ttu-id="0ee8f-107">Spectator View を使用すれば、HoloLens ユーザーが見ているものを他のユーザーが 2D 画面で見ることができます。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-107">Spectator View lets others see what a HoloLens user sees on a 2D screen.</span></span> <span data-ttu-id="0ee8f-108">これは、モバイル デバイスを使用してホログラムを HD に記録し、ビデオ カメラを使用してホログラムの高品質な記録を取得するための高速で手頃な方法でもあります。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-108">It's also a fast and affordable approach to recording holograms in HD with mobile devices and getting great quality recordings of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="0ee8f-109">重要なリソース</span><span class="sxs-lookup"><span data-stu-id="0ee8f-109">Key Resources</span></span>

* [<span data-ttu-id="0ee8f-110">**Spectator View (GitHub)**</span><span class="sxs-lookup"><span data-stu-id="0ee8f-110">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="0ee8f-111">**Spectator View のドキュメント**</span><span class="sxs-lookup"><span data-stu-id="0ee8f-111">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="0ee8f-112">**Spectator View のサンプル**</span><span class="sxs-lookup"><span data-stu-id="0ee8f-112">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="0ee8f-113">使用事例</span><span class="sxs-lookup"><span data-stu-id="0ee8f-113">Use Cases</span></span>

* <span data-ttu-id="0ee8f-114">iPhone または Android デバイスを使用して、複合現実エクスペリエンスを記録できます。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-114">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="0ee8f-115">フル HD で記録し、ホログラムと影にアンチエイリアシングを適用して、コスト効率に優れた方法でホログラムの動画を迅速にキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-115">Record in full HD and apply anti-aliasing to holograms and shadow for a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="0ee8f-116">複合現実エクスペリエンスを、iPhone または iPad から直接 Apple TV にライブ ストリーミングします。遅延は発生しません。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-116">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="0ee8f-117">ゲストとエクスペリエンスを共有します。非 HoloLens ユーザーが各自の電話やタブレットから直接ホログラムを体験できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-117">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="0ee8f-118">現在の機能</span><span class="sxs-lookup"><span data-stu-id="0ee8f-118">Current Features</span></span>

* <span data-ttu-id="0ee8f-119">ホログラムの空間同期。これにより、すべてのユーザーが同じ場所でホログラムを確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-119">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="0ee8f-120">iOS (ARKit 対応デバイス) と Android (ARCore 対応デバイス) のサポート。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-120">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="0ee8f-121">複数の iOS ゲスト。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-121">Multiple iOS guests.</span></span>
<span data-ttu-id="0ee8f-122">動画 + ホログラム + 周囲の音 + ホログラムの音の記録。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-122">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="0ee8f-123">シートを共有して、動画を保存したり、電子メールで送信したり、他のサポート アプリと共有したりできるようにします。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-123">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="0ee8f-124">![マーカー](images/SpecViewPhoneDemo.jpg)
![マーカー](images/hololensspectatorview-500px.jpg) ![マーカー](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="0ee8f-124">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="0ee8f-125">次の表に、Spectator View のさまざまな機能を示します。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-125">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="0ee8f-126">ご自分の録画のニーズに最適なオプションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-126">Choose the option that best fits your video recording needs:</span></span>

|      <span data-ttu-id="0ee8f-127">機能</span><span class="sxs-lookup"><span data-stu-id="0ee8f-127">Functionality</span></span>                                | <span data-ttu-id="0ee8f-128">モバイル</span><span class="sxs-lookup"><span data-stu-id="0ee8f-128">Mobile</span></span>                  |                    <span data-ttu-id="0ee8f-129">ビデオ カメラ</span><span class="sxs-lookup"><span data-stu-id="0ee8f-129">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="0ee8f-130">HD 品質</span><span class="sxs-lookup"><span data-stu-id="0ee8f-130">HD quality</span></span>                           |         <span data-ttu-id="0ee8f-131">フル HD</span><span class="sxs-lookup"><span data-stu-id="0ee8f-131">Full HD</span></span>         |        <span data-ttu-id="0ee8f-132">プロ品質の撮影 (ビデオ カメラによって決定される)</span><span class="sxs-lookup"><span data-stu-id="0ee8f-132">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="0ee8f-133">カメラの容易な移動</span><span class="sxs-lookup"><span data-stu-id="0ee8f-133">Easy camera movement</span></span>                 |            <span data-ttu-id="0ee8f-134">✔</span><span class="sxs-lookup"><span data-stu-id="0ee8f-134">✔</span></span>            |                      <span data-ttu-id="0ee8f-135">✔</span><span class="sxs-lookup"><span data-stu-id="0ee8f-135">✔</span></span>                      |
| <span data-ttu-id="0ee8f-136">第三者の視点</span><span class="sxs-lookup"><span data-stu-id="0ee8f-136">Third-person view</span></span>                    |            <span data-ttu-id="0ee8f-137">✔</span><span class="sxs-lookup"><span data-stu-id="0ee8f-137">✔</span></span>            |                      <span data-ttu-id="0ee8f-138">✔</span><span class="sxs-lookup"><span data-stu-id="0ee8f-138">✔</span></span>                      |
| <span data-ttu-id="0ee8f-139">画面にストリーム可能</span><span class="sxs-lookup"><span data-stu-id="0ee8f-139">Can be streamed to screens</span></span>           |            <span data-ttu-id="0ee8f-140">✔</span><span class="sxs-lookup"><span data-stu-id="0ee8f-140">✔</span></span>            |                      <span data-ttu-id="0ee8f-141">✔</span><span class="sxs-lookup"><span data-stu-id="0ee8f-141">✔</span></span>                      |
| <span data-ttu-id="0ee8f-142">移植性があります。</span><span class="sxs-lookup"><span data-stu-id="0ee8f-142">Portable</span></span>                             |            <span data-ttu-id="0ee8f-143">✔</span><span class="sxs-lookup"><span data-stu-id="0ee8f-143">✔</span></span>            |                                             |
| <span data-ttu-id="0ee8f-144">ワイヤレス</span><span class="sxs-lookup"><span data-stu-id="0ee8f-144">Wireless</span></span>                             |            <span data-ttu-id="0ee8f-145">✔</span><span class="sxs-lookup"><span data-stu-id="0ee8f-145">✔</span></span>            |                                             |
| <span data-ttu-id="0ee8f-146">必要な追加のハードウェア</span><span class="sxs-lookup"><span data-stu-id="0ee8f-146">Additional required hardware</span></span>         |     <span data-ttu-id="0ee8f-147">Android フォン、iPhone</span><span class="sxs-lookup"><span data-stu-id="0ee8f-147">Android phone, iPhone</span></span>    | <span data-ttu-id="0ee8f-148">HoloLens + リグ + 三脚 + ビデオ カメラ + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="0ee8f-148">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="0ee8f-149">ハードウェア投資</span><span class="sxs-lookup"><span data-stu-id="0ee8f-149">Hardware investment</span></span>                  |           <span data-ttu-id="0ee8f-150">低</span><span class="sxs-lookup"><span data-stu-id="0ee8f-150">Low</span></span>            |                     <span data-ttu-id="0ee8f-151">高</span><span class="sxs-lookup"><span data-stu-id="0ee8f-151">High</span></span>                    |
| <span data-ttu-id="0ee8f-152">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="0ee8f-152">Cross-platform</span></span>                       |           <span data-ttu-id="0ee8f-153">Android、iOS</span><span class="sxs-lookup"><span data-stu-id="0ee8f-153">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="0ee8f-154">同期されるコンテンツ</span><span class="sxs-lookup"><span data-stu-id="0ee8f-154">Synchronized content</span></span>                 |            <span data-ttu-id="0ee8f-155">✔</span><span class="sxs-lookup"><span data-stu-id="0ee8f-155">✔</span></span>            |                      <span data-ttu-id="0ee8f-156">✔</span><span class="sxs-lookup"><span data-stu-id="0ee8f-156">✔</span></span>                      |
| <span data-ttu-id="0ee8f-157">ランタイムのセットアップ期間</span><span class="sxs-lookup"><span data-stu-id="0ee8f-157">Runtime setup duration</span></span>               |         <span data-ttu-id="0ee8f-158">即時</span><span class="sxs-lookup"><span data-stu-id="0ee8f-158">Instant</span></span>          |                     <span data-ttu-id="0ee8f-159">遅い</span><span class="sxs-lookup"><span data-stu-id="0ee8f-159">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="0ee8f-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ee8f-160">See also</span></span>

* [<span data-ttu-id="0ee8f-161">複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="0ee8f-161">Mixed reality capture</span></span>](/hololens/holographic-photos-and-videos) 
* [<span data-ttu-id="0ee8f-162">開発者向け複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="0ee8f-162">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="0ee8f-163">複合現実での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="0ee8f-163">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)