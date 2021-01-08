---
title: Spectator View
description: 外付けデバイスからホログラムを視覚化して、外付けディスプレイで Mixed Reality エクスペリエンスを表示または記録します。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, カメラ, ARKit, HoloLens, 複合現実, MixedRealityToolkit, デモ, 記録
ms.openlocfilehash: c344edea9b499bdff15d1d93e400b8be626a63b6
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530104"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a><span data-ttu-id="f8c99-104">HoloLens および HoloLens 2 向けの Spectator View</span><span class="sxs-lookup"><span data-stu-id="f8c99-104">Spectator View for HoloLens and HoloLens 2</span></span>

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a><span data-ttu-id="f8c99-106">概要</span><span class="sxs-lookup"><span data-stu-id="f8c99-106">Overview</span></span>

<span data-ttu-id="f8c99-107">HoloLens を装着していると、自分が見ている素晴らしい世界を、装着していない人は体験できないことを忘れがちです。</span><span class="sxs-lookup"><span data-stu-id="f8c99-107">When you're wearing a HoloLens, it's easy to forget a person without one can't experience the same wonders you're seeing.</span></span> <span data-ttu-id="f8c99-108">Spectator View を使用すれば、HoloLens ユーザーが見ているものを他のユーザーが 2D 画面で見ることができます。</span><span class="sxs-lookup"><span data-stu-id="f8c99-108">Spectator View lets others see what a HoloLens user sees on a 2D screen.</span></span> <span data-ttu-id="f8c99-109">これは、モバイル デバイスを使用してホログラムを HD に記録し、ビデオ カメラを使用してホログラムの高品質な記録を取得するための高速で手頃な方法でもあります。</span><span class="sxs-lookup"><span data-stu-id="f8c99-109">It's also a fast and affordable approach to recording holograms in HD with mobile devices and getting great quality recordings of holograms with video cameras.</span></span>

## <a name="key-resources"></a><span data-ttu-id="f8c99-110">重要なリソース</span><span class="sxs-lookup"><span data-stu-id="f8c99-110">Key Resources</span></span>

* [<span data-ttu-id="f8c99-111">**Spectator View (GitHub)**</span><span class="sxs-lookup"><span data-stu-id="f8c99-111">**Spectator View on GitHub**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView)
* [<span data-ttu-id="f8c99-112">**Spectator View のドキュメント**</span><span class="sxs-lookup"><span data-stu-id="f8c99-112">**Spectator View Documentation**</span></span>](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [<span data-ttu-id="f8c99-113">**Spectator View のサンプル**</span><span class="sxs-lookup"><span data-stu-id="f8c99-113">**Spectator View Samples**</span></span>](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a><span data-ttu-id="f8c99-114">使用事例</span><span class="sxs-lookup"><span data-stu-id="f8c99-114">Use Cases</span></span>

* <span data-ttu-id="f8c99-115">iPhone または Android デバイスを使用して、複合現実エクスペリエンスを記録できます。</span><span class="sxs-lookup"><span data-stu-id="f8c99-115">You can record a mixed reality experience using an iPhone or Android device.</span></span> <span data-ttu-id="f8c99-116">フル HD で記録し、ホログラムと影にアンチエイリアシングを適用して、コスト効率に優れた方法でホログラムの動画を迅速にキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="f8c99-116">Record in full HD and apply anti-aliasing to holograms and shadow for a cost-effective and quick way to capture video of holograms.</span></span>
* <span data-ttu-id="f8c99-117">複合現実エクスペリエンスを、iPhone または iPad から直接 Apple TV にライブ ストリーミングします。遅延は発生しません。</span><span class="sxs-lookup"><span data-stu-id="f8c99-117">Stream live mixed reality experiences to an Apple TV directly from your iPhone or iPad, lag-free!</span></span>
* <span data-ttu-id="f8c99-118">ゲストとエクスペリエンスを共有します。非 HoloLens ユーザーが各自の電話やタブレットから直接ホログラムを体験できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f8c99-118">Share the experience with guests: Let non-HoloLens users experience holograms directly from their phones or tablets.</span></span>

## <a name="current-features"></a><span data-ttu-id="f8c99-119">現在の機能</span><span class="sxs-lookup"><span data-stu-id="f8c99-119">Current Features</span></span>

* <span data-ttu-id="f8c99-120">ホログラムの空間同期。これにより、すべてのユーザーが同じ場所でホログラムを確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f8c99-120">Spatial synchronization of Holograms, so everyone sees holograms in the exact same place.</span></span>
* <span data-ttu-id="f8c99-121">iOS (ARKit 対応デバイス) と Android (ARCore 対応デバイス) のサポート。</span><span class="sxs-lookup"><span data-stu-id="f8c99-121">iOS (ARKit-enabled devices) and Android (ARCore-enabled devices) support.</span></span>
<span data-ttu-id="f8c99-122">複数の iOS ゲスト。</span><span class="sxs-lookup"><span data-stu-id="f8c99-122">Multiple iOS guests.</span></span>
<span data-ttu-id="f8c99-123">動画 + ホログラム + 周囲の音 + ホログラムの音の記録。</span><span class="sxs-lookup"><span data-stu-id="f8c99-123">Recording of video + holograms + ambient sound + hologram sound.</span></span>
<span data-ttu-id="f8c99-124">シートを共有して、動画を保存したり、電子メールで送信したり、他のサポート アプリと共有したりできるようにします。</span><span class="sxs-lookup"><span data-stu-id="f8c99-124">Share sheet so you can save video, email it, or share with other supporting apps.</span></span>

<span data-ttu-id="f8c99-125">![マーカー](images/SpecViewPhoneDemo.jpg)
![マーカー](images/hololensspectatorview-500px.jpg) ![マーカー](images/spectatorview-300px.png)</span><span class="sxs-lookup"><span data-stu-id="f8c99-125">![Marker](images/SpecViewPhoneDemo.jpg)
![Marker](images/hololensspectatorview-500px.jpg) ![Marker](images/spectatorview-300px.png)</span></span>

<span data-ttu-id="f8c99-126">次の表に、Spectator View のさまざまな機能を示します。</span><span class="sxs-lookup"><span data-stu-id="f8c99-126">The following table shows different Spectator View functionality and their capabilities.</span></span> <span data-ttu-id="f8c99-127">ご自分の録画のニーズに最適なオプションを選択してください。</span><span class="sxs-lookup"><span data-stu-id="f8c99-127">Choose the option that best fits your video recording needs:</span></span>

|      <span data-ttu-id="f8c99-128">機能</span><span class="sxs-lookup"><span data-stu-id="f8c99-128">Functionality</span></span>                                | <span data-ttu-id="f8c99-129">モバイル</span><span class="sxs-lookup"><span data-stu-id="f8c99-129">Mobile</span></span>                  |                    <span data-ttu-id="f8c99-130">ビデオ カメラ</span><span class="sxs-lookup"><span data-stu-id="f8c99-130">Video Camera</span></span>              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| <span data-ttu-id="f8c99-131">HD 品質</span><span class="sxs-lookup"><span data-stu-id="f8c99-131">HD quality</span></span>                           |         <span data-ttu-id="f8c99-132">フル HD</span><span class="sxs-lookup"><span data-stu-id="f8c99-132">Full HD</span></span>         |        <span data-ttu-id="f8c99-133">プロ品質の撮影 (ビデオ カメラによって決定される)</span><span class="sxs-lookup"><span data-stu-id="f8c99-133">Professional quality filming (as determined by video camera)</span></span>      |
| <span data-ttu-id="f8c99-134">カメラの容易な移動</span><span class="sxs-lookup"><span data-stu-id="f8c99-134">Easy camera movement</span></span>                 |            <span data-ttu-id="f8c99-135">✔</span><span class="sxs-lookup"><span data-stu-id="f8c99-135">✔</span></span>            |                      <span data-ttu-id="f8c99-136">✔</span><span class="sxs-lookup"><span data-stu-id="f8c99-136">✔</span></span>                      |
| <span data-ttu-id="f8c99-137">第三者の視点</span><span class="sxs-lookup"><span data-stu-id="f8c99-137">Third-person view</span></span>                    |            <span data-ttu-id="f8c99-138">✔</span><span class="sxs-lookup"><span data-stu-id="f8c99-138">✔</span></span>            |                      <span data-ttu-id="f8c99-139">✔</span><span class="sxs-lookup"><span data-stu-id="f8c99-139">✔</span></span>                      |
| <span data-ttu-id="f8c99-140">画面にストリーム可能</span><span class="sxs-lookup"><span data-stu-id="f8c99-140">Can be streamed to screens</span></span>           |            <span data-ttu-id="f8c99-141">✔</span><span class="sxs-lookup"><span data-stu-id="f8c99-141">✔</span></span>            |                      <span data-ttu-id="f8c99-142">✔</span><span class="sxs-lookup"><span data-stu-id="f8c99-142">✔</span></span>                      |
| <span data-ttu-id="f8c99-143">移植性があります。</span><span class="sxs-lookup"><span data-stu-id="f8c99-143">Portable</span></span>                             |            <span data-ttu-id="f8c99-144">✔</span><span class="sxs-lookup"><span data-stu-id="f8c99-144">✔</span></span>            |                                             |
| <span data-ttu-id="f8c99-145">ワイヤレス</span><span class="sxs-lookup"><span data-stu-id="f8c99-145">Wireless</span></span>                             |            <span data-ttu-id="f8c99-146">✔</span><span class="sxs-lookup"><span data-stu-id="f8c99-146">✔</span></span>            |                                             |
| <span data-ttu-id="f8c99-147">必要な追加のハードウェア</span><span class="sxs-lookup"><span data-stu-id="f8c99-147">Additional required hardware</span></span>         |     <span data-ttu-id="f8c99-148">Android フォン、iPhone</span><span class="sxs-lookup"><span data-stu-id="f8c99-148">Android phone, iPhone</span></span>    | <span data-ttu-id="f8c99-149">HoloLens + リグ + 三脚 + ビデオ カメラ + PC + Unity</span><span class="sxs-lookup"><span data-stu-id="f8c99-149">HoloLens + Rig + Tripod + Video Camera + PC + Unity</span></span> |
| <span data-ttu-id="f8c99-150">ハードウェア投資</span><span class="sxs-lookup"><span data-stu-id="f8c99-150">Hardware investment</span></span>                  |           <span data-ttu-id="f8c99-151">低</span><span class="sxs-lookup"><span data-stu-id="f8c99-151">Low</span></span>            |                     <span data-ttu-id="f8c99-152">高</span><span class="sxs-lookup"><span data-stu-id="f8c99-152">High</span></span>                    |
| <span data-ttu-id="f8c99-153">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="f8c99-153">Cross-platform</span></span>                       |           <span data-ttu-id="f8c99-154">Android、iOS</span><span class="sxs-lookup"><span data-stu-id="f8c99-154">Android, iOS</span></span>   |                                             |
| <span data-ttu-id="f8c99-155">同期されるコンテンツ</span><span class="sxs-lookup"><span data-stu-id="f8c99-155">Synchronized content</span></span>                 |            <span data-ttu-id="f8c99-156">✔</span><span class="sxs-lookup"><span data-stu-id="f8c99-156">✔</span></span>            |                      <span data-ttu-id="f8c99-157">✔</span><span class="sxs-lookup"><span data-stu-id="f8c99-157">✔</span></span>                      |
| <span data-ttu-id="f8c99-158">ランタイムのセットアップ期間</span><span class="sxs-lookup"><span data-stu-id="f8c99-158">Runtime setup duration</span></span>               |         <span data-ttu-id="f8c99-159">即時</span><span class="sxs-lookup"><span data-stu-id="f8c99-159">Instant</span></span>          |                     <span data-ttu-id="f8c99-160">遅い</span><span class="sxs-lookup"><span data-stu-id="f8c99-160">Slow</span></span>                    |
## <a name="see-also"></a><span data-ttu-id="f8c99-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="f8c99-161">See also</span></span>

* [<span data-ttu-id="f8c99-162">複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="f8c99-162">Mixed reality capture</span></span>](../../mixed-reality-capture.md) 
* [<span data-ttu-id="f8c99-163">開発者向け複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="f8c99-163">Mixed reality capture for developers</span></span>](mixed-reality-capture-for-developers.md)
* [<span data-ttu-id="f8c99-164">複合現実での共有エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="f8c99-164">Shared experiences in mixed reality</span></span>](shared-experiences-in-mixed-reality.md)
