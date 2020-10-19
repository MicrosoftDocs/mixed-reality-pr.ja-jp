---
title: Windows Mixed Reality での WebVR の使用
description: WebVR について説明します。また、Windows Mixed Reality ヘッドセットで Microsoft Edge と共に使用する方法についても説明します。
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、WebVR、Edge、Microsoft Edge、web 閲覧
ms.openlocfilehash: e57ad060a1a539e90631d1b9f1808d1e8466e669
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174347"
---
# <a name="using-webvr-with-windows-mixed-reality"></a><span data-ttu-id="0f4ca-104">Windows Mixed Reality での WebVR の使用</span><span class="sxs-lookup"><span data-stu-id="0f4ca-104">Using WebVR with Windows Mixed Reality</span></span>

>[!IMPORTANT] 
><span data-ttu-id="0f4ca-105">ほとんどの最新の web ブラウザーでは、WebXR を優先して非推奨の WebVR サポートを使用しています。これは、VR ヘッドセット用のイマーシブ web エクスペリエンスを作成するための新しい標準です。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-105">Most modern web browsers have deprecated support of WebVR in favor of WebXR, the new standard for creating immersive web experiences for VR headsets.</span></span> <span data-ttu-id="0f4ca-106">[新しい Microsoft Edge](using-microsoft-edge.md) for WebXR サポートをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-106">Please install [the new Microsoft Edge](using-microsoft-edge.md) for WebXR support.</span></span>

## <a name="what-is-webvr"></a><span data-ttu-id="0f4ca-107">WebVR とは</span><span class="sxs-lookup"><span data-stu-id="0f4ca-107">What is WebVR?</span></span>

<span data-ttu-id="0f4ca-108">[Webvr](https://webvr.info) は、ブラウザーで VR を体験できるようにするオープンな仕様です。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-108">[WebVR](https://webvr.info) is an open specification that makes it possible to experience VR in your browser.</span></span> <span data-ttu-id="0f4ca-109">Web サイトが WebVR サポートを実装し、3D コンテンツを提供する場合、ユーザーの同意と共に、ヘッドホンにイマーシブコンテンツを表示できます。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-109">If a website implements WebVR support and provides 3D content, it can display immersive content in the headset, with user consent.</span></span>

## <a name="what-is-the-difference-between-webvr-and-browsing-the-web-in-vr"></a><span data-ttu-id="0f4ca-110">Webhook での WebVR と web の閲覧の違いは何ですか。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-110">What is the difference between WebVR and browsing the web in VR?</span></span>

<span data-ttu-id="0f4ca-111">WebVR は、web サイトの作成者が VR 機能をページに追加できるようにするテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-111">WebVR is a technology that allows a website author to add VR functionality to a page.</span></span> <span data-ttu-id="0f4ca-112">WebVR API は、ヘッドセット全体に3D コンテンツ (360 度のビデオ、3D モデル、3d ゲームなど) を表示するためにページによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-112">The WebVR API is used by a page to display 3D content (such as 360 degree video, or a 3D model, or a 3D game) to the entirety of your headset.</span></span> <span data-ttu-id="0f4ca-113">**例:**[Cnn.com/vr](http://cnn.com/vr)での360ビデオの表示。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-113">**Example:** Viewing a 360 Video on [cnn.com/vr](http://cnn.com/vr).</span></span> <span data-ttu-id="0f4ca-114">ページが WebVR をサポートしている場合は、ボタンまたはその他の UI 要素が追加され、これをクリックして VR を入力することができます。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-114">If a page supports WebVR, it will add a button or other UI element that you can click to enter VR.</span></span>

<span data-ttu-id="0f4ca-115">VR で web を閲覧することは、プラグインを装着している間に、microsoft Edge ブラウザーを使用することを意味します。これは、Cliffhouse 内の2D アプリスレートです。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-115">Browsing the web in VR means using the Edge browser while you are wearing your headset, as a 2D app slate within the Cliffhouse.</span></span>

## <a name="do-all-websites-support-webvr"></a><span data-ttu-id="0f4ca-116">すべての web サイトが WebVR をサポートしていますか?</span><span class="sxs-lookup"><span data-stu-id="0f4ca-116">Do all websites support WebVR?</span></span>

<span data-ttu-id="0f4ca-117">いいえ。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-117">No.</span></span> <span data-ttu-id="0f4ca-118">Web サイトの作成者は、WebVR を使用することをオプトインする必要があります。さらに、特定のブラウザー、ヘッドセット、およびコントローラー用に最適化されたサイトを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-118">Website authors must opt-in to use WebVR and furthermore they may create sites that are optimized for specific browsers, headsets, and controllers.</span></span> <span data-ttu-id="0f4ca-119">たとえば、一部の WebVR コンテンツは mobile VR デバイスに対してのみ最適化されています。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-119">For example, some WebVR content is optimized for mobile VR devices only.</span></span> <span data-ttu-id="0f4ca-120">また、web サイトでは、WebVR コンテンツを明示的に作成して提供する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-120">Also, keep in mind that web sites need to explicitly create and provide WebVR content.</span></span> <span data-ttu-id="0f4ca-121">WebVR と互換性のあるいくつかのコンテンツがあるサイトの数が毎日増加しています。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-121">The number of sites that have some WebVR compatible content is growing every day.</span></span>

## <a name="can-i-use-my-viveoculus-etc-to-view-webvr-content-in-microsoft-edge"></a><span data-ttu-id="0f4ca-122">Naopak/Oculus などを使用して Microsoft Edge の WebVR コンテンツを表示することはできますか。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-122">Can I use my Vive/Oculus etc to view WebVR content in Microsoft Edge?</span></span>

<span data-ttu-id="0f4ca-123">いいえ。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-123">No.</span></span> <span data-ttu-id="0f4ca-124">Windows Mixed Reality ヘッドセットを使用して、エッジで WebVR を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-124">You must use a Windows Mixed Reality headset to use WebVR in Edge.</span></span> <span data-ttu-id="0f4ca-125">ただし、別のブラウザーで WebVR コンテンツにアクセスできる場合があります。互換性のあるデバイスとブラウザーの完全な一覧については、「 [Webvr. 岩](http://webvr.rocks/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-125">However, you may be able to access WebVR content in another browser; see the complete list of compatible devices and browsers at: [WebVR.rocks](http://webvr.rocks/).</span></span>

## <a name="where-can-i-find-the-webvr-developer-documentation"></a><span data-ttu-id="0f4ca-126">WebVR 開発者向けドキュメントはどこで入手できますか。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-126">Where can I find the WebVR developer documentation?</span></span>

<span data-ttu-id="0f4ca-127">開発者向けドキュメントについては、「 [Webvr Developer documentation](https://docs.microsoft.com/microsoft-edge/webvr/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-127">The developer documentation is located here: [WebVR Developer Documentation](https://docs.microsoft.com/microsoft-edge/webvr/).</span></span>

## <a name="ive-found-a-website-with-webvr-that-doesnt-work-in-windows-mixed-reality-what-do-i-do"></a><span data-ttu-id="0f4ca-128">Windows Mixed Reality では動作しない WebVR を使用した web サイトが見つかりました。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-128">I've found a website with WebVR that doesn't work in Windows Mixed Reality.</span></span> <span data-ttu-id="0f4ca-129">どうしたらよいですか。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-129">What do I do?</span></span>

<span data-ttu-id="0f4ca-130">破損したサイトは、 [問題の追跡ツール](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)で Microsoft Edge ブラウザーチームに直接、または [#EdgeBug ハッシュタグ](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/)を使用して twitter 経由で報告できます。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-130">You can report broken sites directly to the Microsoft Edge browser team in the [issue tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/), or via twitter using [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).</span></span>

<span data-ttu-id="0f4ca-131">カテゴリの下にある Windows フィードバックハブアプリを使用して、バグをログに記録することもできます。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-131">You can also log bugs using the Windows Feedback Hub app under category:</span></span>

<span data-ttu-id="0f4ca-132">Microsoft Edge > Web サイトの問題</span><span class="sxs-lookup"><span data-stu-id="0f4ca-132">Microsoft Edge -> Website Issues</span></span>

## <a name="what-is-a-good-page-to-test-if-webvr-is-working"></a><span data-ttu-id="0f4ca-133">WebVR が機能しているかどうかをテストするための適切なページは何ですか?</span><span class="sxs-lookup"><span data-stu-id="0f4ca-133">What is a good page to test if WebVR is working?</span></span>

<span data-ttu-id="0f4ca-134">[Webvr.info のサンプル](http://webvr.info/samples/XX-vr-controllers.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-134">See [webvr.info samples](http://webvr.info/samples/XX-vr-controllers.html).</span></span>

## <a name="how-do-i-set-up-webvr"></a><span data-ttu-id="0f4ca-135">WebVR をセットアップ操作方法には</span><span class="sxs-lookup"><span data-stu-id="0f4ca-135">How do I set up WebVR?</span></span>

<span data-ttu-id="0f4ca-136">Windows Mixed Reality ヘッドセット (ハードウェアまたはシミュレーションを使用) で WebVR コンテンツを体験するには、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-136">To experience WebVR content on a Windows Mixed Reality headset (using hardware or simulation) you must:</span></span>
1. <span data-ttu-id="0f4ca-137">ヘッドセットが接続されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-137">Ensure your headset is connected.</span></span>
2. <span data-ttu-id="0f4ca-138">デスクトップまたは Mixed Reality のいずれかで Microsoft Edge を起動します。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-138">Launch Microsoft Edge, either on the desktop or within Mixed Reality.</span></span>
3. <span data-ttu-id="0f4ca-139">WebVR enabled ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-139">Navigate to a WebVR enabled page.</span></span>
4. <span data-ttu-id="0f4ca-140">ページ内の Enter VR ボタンをクリックします (このボタンの位置と表示は、web サイトごとに異なる場合があります)。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-140">Click the Enter VR button within the page (the location and visual representation of this button may vary per website).</span></span> <span data-ttu-id="0f4ca-141">次のようになります。 </span><span class="sxs-lookup"><span data-stu-id="0f4ca-141">It may look similar to:</span></span>\
   ![VR メガネイメージ](images/75px-enter-vr.png)
5. <span data-ttu-id="0f4ca-143">特定のドメインに対して最初に VR を入力しようとすると、ブラウザーはイマーシブビューの使用に同意するように要求し、[はい] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-143">The first time you try to enter VR on a specific domain, the browser will ask for consent to use immersive view, click yes:</span></span> ![特定のドメインに対して最初に VR を入力しようとしたときに表示される同意 UI](images/1053px-Webvr-consent-ui.png)
6. <span data-ttu-id="0f4ca-145">ヘッドセットで WebVR コンテンツの表示が開始されます。</span><span class="sxs-lookup"><span data-stu-id="0f4ca-145">Your headset should begin displaying the WebVR content.</span></span>


## <a name="see-also"></a><span data-ttu-id="0f4ca-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f4ca-146">See also</span></span>

* [<span data-ttu-id="0f4ca-147">WebVR > のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="0f4ca-147">Troubleshooting > WebVR</span></span>](webvr-questions.md)
* [<span data-ttu-id="0f4ca-148">初めての WebVR エクスペリエンスを利用する方法</span><span class="sxs-lookup"><span data-stu-id="0f4ca-148">How to get into your first WebVR experience</span></span>](using-games-and-apps-in-windows-mixed-reality.md#how-to-get-into-your-first-webvr-experience)
* [<span data-ttu-id="0f4ca-149">Windows Mixed Reality でのゲームとアプリの使用</span><span class="sxs-lookup"><span data-stu-id="0f4ca-149">Using games and apps in Windows Mixed Reality</span></span>](using-games-and-apps-in-windows-mixed-reality.md)
* [<span data-ttu-id="0f4ca-150">Mixed Reality ホーム</span><span class="sxs-lookup"><span data-stu-id="0f4ca-150">Your Mixed Reality Home</span></span>](your-mixed-reality-home.md)
* [<span data-ttu-id="0f4ca-151">追跡システム</span><span class="sxs-lookup"><span data-stu-id="0f4ca-151">Tracking System</span></span>](tracking-system.md)
* [<span data-ttu-id="0f4ca-152">モーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="0f4ca-152">Motion Controllers</span></span>](controllers-in-wmr.md)
* [<span data-ttu-id="0f4ca-153">SteamVR</span><span class="sxs-lookup"><span data-stu-id="0f4ca-153">SteamVR</span></span>](using-steamvr-with-windows-mixed-reality.md)
* [<span data-ttu-id="0f4ca-154">フィードバックの提出</span><span class="sxs-lookup"><span data-stu-id="0f4ca-154">Filing feedback</span></span>](filing-feedback.md)
