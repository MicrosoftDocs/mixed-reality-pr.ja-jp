---
title: WebVR に関する Faq
description: 標準的なコンシューマーサポートドキュメントを超えている web アプリケーションについては、Mixed Reality のトラブルシューティングを使用して最新情報を入手してください。
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート、WebVR
ms.openlocfilehash: dc7a0b28e19f4f1fc029489aae2ea375e43b8d3b
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008662"
---
# <a name="webvr-faqs"></a><span data-ttu-id="e7f74-104">WebVR に関する Faq</span><span class="sxs-lookup"><span data-stu-id="e7f74-104">WebVR FAQs</span></span>

## <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a><span data-ttu-id="e7f74-105">Edge から VR コンテンツを表示するときにコントローラーが表示できないのはなぜですか</span><span class="sxs-lookup"><span data-stu-id="e7f74-105">Why can’t I see my controllers when viewing VR content from Edge</span></span>

<span data-ttu-id="e7f74-106">すべての WebVR コンテンツは、モーションコントローラーをサポートするために作成されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e7f74-106">Not all WebVR content is authored to support motion controllers.</span></span> <span data-ttu-id="e7f74-107">WebVR を使用すると、コンテンツ開発者は、ゲームコントローラーやモーションコントローラーなど、さまざまな種類の入力をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="e7f74-107">WebVR allows content developers to support different types of input, such as game controllers or motion controllers.</span></span> <span data-ttu-id="e7f74-108">サイトにコントローラーが表示されない場合は、モーションコントローラーがサポートされていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e7f74-108">If you don't see your controllers on a site, it probably doesn’t have motion controller support.</span></span>

## <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a><span data-ttu-id="e7f74-109">イマーシブ WebVR ビューでマウスを使用できないのはなぜですか。</span><span class="sxs-lookup"><span data-stu-id="e7f74-109">Why can't I use the mouse in an immersive WebVR view</span></span>

<span data-ttu-id="e7f74-110">マウスの使用は、WebVR 仕様のオプション機能です。</span><span class="sxs-lookup"><span data-stu-id="e7f74-110">Using a mouse is an optional feature of the WebVR specification.</span></span> <span data-ttu-id="e7f74-111">すべてのブラウザーがこの機能をサポートするわけではありません。また、マウス入力をサポートするためにすべての WebVR コンテンツが作成されるわけではありません</span><span class="sxs-lookup"><span data-stu-id="e7f74-111">Not all browsers support this feature, and not all WebVR content is authored to support mouse input.</span></span> <span data-ttu-id="e7f74-112">WebVR を使用すると、コンテンツ開発者は、マウス、キーボード、ゲームコントローラー、またはモーションコントローラーなど、さまざまな種類の入力をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="e7f74-112">WebVR allows content developers to support different types of input, such as mouse, keyboard, game controllers, or motion controllers.</span></span> <span data-ttu-id="e7f74-113">マウス入力の動作は、ブラウザーごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="e7f74-113">Mouse input behavior varies per browser.</span></span> <span data-ttu-id="e7f74-114">Microsoft Edge では、web サイトの作成者は、マウス入力が動作するためにヘッドセットに表示するときに "pointerlock ロック" を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e7f74-114">Within Microsoft Edge, website authors must ensure they take 'pointerlock' when presenting to the headset for mouse input to work.</span></span>

## <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardian-etc-from-edge-in-vr"></a><span data-ttu-id="e7f74-115">VR のエッジから、Youtube/Facebook/Vimeo/ガーディアンから360度のビデオを表示できないのはなぜですか。</span><span class="sxs-lookup"><span data-stu-id="e7f74-115">Why can’t I view 360-degree videos from Youtube/Facebook/Vimeo/The Guardian, etc. from Edge in VR</span></span>

<span data-ttu-id="e7f74-116">Web サイトがブラウザーから直接 VR エクスペリエンスを起動できるようにする WebVR 仕様があります。</span><span class="sxs-lookup"><span data-stu-id="e7f74-116">There's a WebVR specification that lets websites launch VR experiences directly from the browser.</span></span> <span data-ttu-id="e7f74-117">これらの web サイトの作成者は、現時点でこの仕様を実装していません。</span><span class="sxs-lookup"><span data-stu-id="e7f74-117">The authors of these websites haven't implemented this specification at this time.</span></span> <span data-ttu-id="e7f74-118">一部のプラットフォームでは、これらのベンダからの VR コンテンツの表示を可能にするアプリをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="e7f74-118">There may be downloadable apps on some platforms that enable viewing of VR content from these vendors.</span></span>

## <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a><span data-ttu-id="e7f74-119">Firefox または Chrome から VR を入力できないのはなぜですか。</span><span class="sxs-lookup"><span data-stu-id="e7f74-119">Why can’t I enter VR from Firefox or Chrome</span></span>

<span data-ttu-id="e7f74-120">WebVR は、現時点では Edge の Windows Mixed Reality デバイスでのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e7f74-120">WebVR is only supported by Windows Mixed Reality devices in Edge at this time.</span></span>

## <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a><span data-ttu-id="e7f74-121">Web サイトから VR を入力したときに、ヘッドセットに空の画面が表示されるのはなぜですか。</span><span class="sxs-lookup"><span data-stu-id="e7f74-121">When I enter VR from a website, why do I see a blank screen in my headset</span></span>

<span data-ttu-id="e7f74-122">Web サイトで、マルチ GPU マシン (ハイブリッド GPU ラップトップを含む) のサポートが実装されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e7f74-122">The website may not have implemented support for multi GPU machines (including hybrid GPU laptops).</span></span> <span data-ttu-id="e7f74-123">試行する操作:</span><span class="sxs-lookup"><span data-stu-id="e7f74-123">Try to:</span></span>

* <span data-ttu-id="e7f74-124">ページを再度読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e7f74-124">Reload the page.</span></span>
* <span data-ttu-id="e7f74-125">デスクトップコンピューターで、Microsoft Edge を表示しているモニターと同じグラフィックスアダプターにヘッドセットを接続します。</span><span class="sxs-lookup"><span data-stu-id="e7f74-125">On desktop machines, plug the headset into the same graphics adapter as the monitor that is displaying Microsoft Edge.</span></span> <span data-ttu-id="e7f74-126">両方を高電力グラフィックスカードに接続し、統合されたグラフィックスアダプターには挿入しません。</span><span class="sxs-lookup"><span data-stu-id="e7f74-126">Plug both into the higher powered graphics card, not into the integrated graphics adapter.</span></span>

## <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a><span data-ttu-id="e7f74-127">Edge からビデオを見ているときに VR を終了すると、サウンドは再生を続行しますが、エッジウィンドウはグレー表示されます。</span><span class="sxs-lookup"><span data-stu-id="e7f74-127">When I exit VR when watching a video from Edge, the sound continues playing but the Edge window is grayed out</span></span>

<span data-ttu-id="e7f74-128">これは、Mixed Reality 崖ハウスのエッジから WebVR を実行するときの既知の問題です。</span><span class="sxs-lookup"><span data-stu-id="e7f74-128">This is a known issue when running WebVR from Edge in the Mixed Reality Cliff House.</span></span> <span data-ttu-id="e7f74-129">これを解決するには、windows のボタンの代わりに、キーボードの esc キーを押して WebVR エクスペリエンスを終了するか、グレー表示のエッジウィンドウを選択してビデオを停止します。</span><span class="sxs-lookup"><span data-stu-id="e7f74-129">To resolve it, press escape on the keyboard instead of the windows button to exit the WebVR experience, or activate the greyed out Edge window by selecting it and then stop the video.</span></span>

## <a name="can-i-use-webvr-on-the-hololens"></a><span data-ttu-id="e7f74-130">HoloLens で WebVR を使用できます</span><span class="sxs-lookup"><span data-stu-id="e7f74-130">Can I use WebVR on the HoloLens</span></span>

<span data-ttu-id="e7f74-131">この時点で、Microsoft は HoloLens での WebVR について何も発表していません。</span><span class="sxs-lookup"><span data-stu-id="e7f74-131">Microsoft hasn't announced anything about WebVR on the HoloLens at this point.</span></span>

## <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a><span data-ttu-id="e7f74-132">Edge から WebVR コンテンツを表示するときに、ビューが floor レベルで表示される理由</span><span class="sxs-lookup"><span data-stu-id="e7f74-132">Why is my view at floor level when viewing WebVR content from Edge</span></span>

<span data-ttu-id="e7f74-133">Web サイトは、Windows Mixed Reality ヘッドセットを正しくサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e7f74-133">The website doesn't properly support Windows Mixed Reality headsets.</span></span> <span data-ttu-id="e7f74-134">これを解決するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="e7f74-134">To work around this:</span></span>

1. <span data-ttu-id="e7f74-135">ヘッドセットをスペースの床に配置します。</span><span class="sxs-lookup"><span data-stu-id="e7f74-135">Place the headset on the floor of your space.</span></span>
2. <span data-ttu-id="e7f74-136">(Mixed reality ではなく) デスクトップで Microsoft Edge を使用して WebVR ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="e7f74-136">Navigate to the WebVR page using Microsoft Edge on your desktop (not within mixed reality).</span></span>
3. <span data-ttu-id="e7f74-137">[Enter VR] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e7f74-137">Select "Enter VR".</span></span>
4. <span data-ttu-id="e7f74-138">エクスペリエンスがイマーシブモードに完全に入るまで 5 ~ 10 秒待機します。</span><span class="sxs-lookup"><span data-stu-id="e7f74-138">Wait five to 10 seconds for the experience to fully enter immersive mode.</span></span>
5. <span data-ttu-id="e7f74-139">ヘッドセットに配置します。</span><span class="sxs-lookup"><span data-stu-id="e7f74-139">Put on the headset.</span></span>

## <a name="the-display-is-low-resolution-in-some-webvr-experiences"></a><span data-ttu-id="e7f74-140">一部の WebVR エクスペリエンスでは、表示が低解像度になります。</span><span class="sxs-lookup"><span data-stu-id="e7f74-140">The display is low resolution in some WebVR experiences</span></span>

<span data-ttu-id="e7f74-141">これらの web サイトは、高解像度のヘッドセットを正しくサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e7f74-141">Those websites don't properly support high-resolution headsets.</span></span> <span data-ttu-id="e7f74-142">これを解決するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="e7f74-142">To work around this:</span></span>

* <span data-ttu-id="e7f74-143">(Mixed reality 崖家ではなく) デスクトップから WebVR を起動する場合は、[Enter VR] を選択する前にウィンドウが最大化されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e7f74-143">If launching WebVR from the desktop (rather than the mixed reality Cliff House), ensure the window is maximized before selecting "Enter VR".</span></span>
* <span data-ttu-id="e7f74-144">VR を入力した後、Microsoft Edge ウィンドウのサイズを変更しないようにします。</span><span class="sxs-lookup"><span data-stu-id="e7f74-144">Avoid resizing the Microsoft Edge window after you have entered VR.</span></span>

## <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a><span data-ttu-id="e7f74-145">ブラウザータブを変更すると WebVR イマーシブビューが終了するのはなぜですか</span><span class="sxs-lookup"><span data-stu-id="e7f74-145">Why does the WebVR immersive view exit when I change browser tabs</span></span>

<span data-ttu-id="e7f74-146">これは通常の動作です。</span><span class="sxs-lookup"><span data-stu-id="e7f74-146">This is expected behavior.</span></span> <span data-ttu-id="e7f74-147">セキュリティ上の理由から、接続されているヘッドセットにアクセスできるのは、[アクティブブラウザー] タブだけです。</span><span class="sxs-lookup"><span data-stu-id="e7f74-147">For security reasons, only the active browser tab can access connected headsets.</span></span>

## <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a><span data-ttu-id="e7f74-148">特定の WebVR エクスペリエンスでオーディオを再生できないのはなぜですか。</span><span class="sxs-lookup"><span data-stu-id="e7f74-148">Why can't I hear audio on a particular WebVR experience</span></span>

<span data-ttu-id="e7f74-149">Web サイトは、Microsoft Edge で現在サポートされていない OGG オーディオファイル形式を使用している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e7f74-149">The website may be using the OGG audio file format, which Microsoft Edge doesn't currently support.</span></span>

<span data-ttu-id="e7f74-150">破損したサイトは、 [問題の追跡ツール](https://developer.microsoft.com/microsoft-edge/platform/issues/)で Microsoft Edge ブラウザーチームに直接、または [#EdgeBug ハッシュタグ](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)を使用して twitter 経由で報告できます。</span><span class="sxs-lookup"><span data-stu-id="e7f74-150">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

## <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a><span data-ttu-id="e7f74-151">Haptic フィードバックが WebVR とモーションコントローラーで動作しないのはなぜですか。</span><span class="sxs-lookup"><span data-stu-id="e7f74-151">Why does haptic feedback not work in WebVR with motion controllers</span></span>

<span data-ttu-id="e7f74-152">Microsoft Edge では、現在、WebVR ゲームパッド API 拡張機能の haptics はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e7f74-152">Microsoft Edge doesn't currently support haptics on the WebVR gamepad API extensions.</span></span>