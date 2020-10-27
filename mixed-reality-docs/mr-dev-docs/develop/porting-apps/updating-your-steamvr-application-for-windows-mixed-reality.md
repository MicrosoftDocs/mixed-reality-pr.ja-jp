---
title: SteamVR アプリケーションを更新しています
description: Windows Mixed Reality ヘッドセットとの互換性を最大化するために SteamVR アプリケーションを更新するためのベストプラクティス。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR、互換性
ms.openlocfilehash: 4a1439bed8743396cba13fa4d65debc62487ab46
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638509"
---
# <a name="updating-your-steamvr-application"></a><span data-ttu-id="c6be5-104">SteamVR アプリケーションを更新しています</span><span class="sxs-lookup"><span data-stu-id="c6be5-104">Updating your SteamVR application</span></span>
<span data-ttu-id="c6be5-105">Windows Mixed Reality ヘッドセットで実行するために、開発者は SteamVR エクスペリエンスをテストして最適化することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c6be5-105">We encourage developers to test and optimize their SteamVR experiences to run on Windows Mixed Reality headsets.</span></span> <span data-ttu-id="c6be5-106">このドキュメントでは、開発者が Windows Mixed Reality でエクスペリエンスを確実に実行できるようにするための一般的な機能強化について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6be5-106">This documentation covers common improvements developers can make to ensure that their experience runs great on Windows Mixed Reality.</span></span>

## <a name="initial-setup-instructions"></a><span data-ttu-id="c6be5-107">初期セットアップの手順</span><span class="sxs-lookup"><span data-stu-id="c6be5-107">Initial setup instructions</span></span>

<span data-ttu-id="c6be5-108">Windows Mixed Reality でゲームやアプリのテストを開始するには、まず、[ファーストステップガイド](https://aka.ms/WindowsMixedRealitySteamVR)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="c6be5-108">To start testing out your game or app on Windows Mixed Reality make sure to first follow our [getting started guide.](https://aka.ms/WindowsMixedRealitySteamVR)</span></span>

## <a name="controller-models"></a><span data-ttu-id="c6be5-109">コントローラーモデル</span><span class="sxs-lookup"><span data-stu-id="c6be5-109">Controller Models</span></span>
1. <span data-ttu-id="c6be5-110">アプリがコントローラーモデルをレンダリングする場合:</span><span class="sxs-lookup"><span data-stu-id="c6be5-110">If your app renders controller models:</span></span>
    * <span data-ttu-id="c6be5-111">[Windows Mixed Reality モーションコントローラーモデル](../../design/motion-controllers.md#rendering-the-motion-controller-model)を使用する</span><span class="sxs-lookup"><span data-stu-id="c6be5-111">Use the [Windows Mixed Reality motion controller models](../../design/motion-controllers.md#rendering-the-motion-controller-model)</span></span>
    * <span data-ttu-id="c6be5-112">IVRRenderModel:: GetComponentState を使用して、コンポーネントパーツへのローカル変換を取得します (例:</span><span class="sxs-lookup"><span data-stu-id="c6be5-112">Use IVRRenderModel::GetComponentState to get local transforms to component parts (eg.</span></span> <span data-ttu-id="c6be5-113">ポインターのポーズ)</span><span class="sxs-lookup"><span data-stu-id="c6be5-113">Pointer pose)</span></span>
2. <span data-ttu-id="c6be5-114">ききの概念を持つエクスペリエンスでは、コントローラーを区別するために入力 Api からヒントを取得する必要があります [(Unity の例)。](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span><span class="sxs-lookup"><span data-stu-id="c6be5-114">Experiences that have a notion of handedness should get hints from the input APIs to differentiate controllers [(Unity example)](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span></span>

## <a name="controls"></a><span data-ttu-id="c6be5-115">コントロール</span><span class="sxs-lookup"><span data-stu-id="c6be5-115">Controls</span></span>

<span data-ttu-id="c6be5-116">コントロールレイアウトをデザインまたは調整する場合は、次の予約済みコマンドのセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c6be5-116">When designing or adjusting your control layout keep in mind the following set of reserved commands:</span></span>
1. <span data-ttu-id="c6be5-117">**左と右のアナログサムスティック** をクリックすると、 **蒸気ダッシュボード** 用に予約されます。</span><span class="sxs-lookup"><span data-stu-id="c6be5-117">Clicking down the **left and right analog thumbstick** is reserved for the **Steam Dashboard** .</span></span>

> [!NOTE]
> <span data-ttu-id="c6be5-118">HP リバーブ G2 コントローラーを使用している場合は、右のメニューボタンをクリックすると、 **蒸気ダッシュボード** 用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="c6be5-118">If you're using an HP Reverb G2 controller, clicking the right menu button is reserved for the **Steam Dashboard** .</span></span>

2. <span data-ttu-id="c6be5-119">**Windows のボタンをクリック** すると、常にユーザーが Windows Mixed Reality ホームに戻ります。</span><span class="sxs-lookup"><span data-stu-id="c6be5-119">The **Windows button** will always return users to the Windows Mixed Reality home.</span></span>

<span data-ttu-id="c6be5-120">可能であれば、既定では、 [Windows Mixed Reality ホーム](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) に準拠するように設定されています。</span><span class="sxs-lookup"><span data-stu-id="c6be5-120">If possible, default to thumb stick based teleportation to match the [Windows Mixed Reality home](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation behavior</span></span>

## <a name="tooltips-and-ui"></a><span data-ttu-id="c6be5-121">ツールヒントと UI</span><span class="sxs-lookup"><span data-stu-id="c6be5-121">Tooltips and UI</span></span>

<span data-ttu-id="c6be5-122">多くの VR ゲームでは、モーションコントローラーのツールヒントとオーバーレイを利用して、ユーザーがゲームやアプリにとって最も重要なコマンドを学習できます。</span><span class="sxs-lookup"><span data-stu-id="c6be5-122">Many VR games take advantage of motion controller tooltips and overlays to teach users the most important commands for their game or app.</span></span> <span data-ttu-id="c6be5-123">Windows Mixed reality 用にアプリケーションをチューニングする場合は、ツールヒントが Windows コントローラーモデルにマップされていることを確認するために、エクスペリエンスのこの部分を確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c6be5-123">When tuning your application for Windows Mixed reality we recommend reviewing this part of your experience to make sure the tooltips map to the Windows controller models.</span></span>

<span data-ttu-id="c6be5-124">また、コントローラーのイメージを表示するポイントがある場合は、Windows Mixed Reality モーションコントローラーを使用して、更新されたイメージを提供するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="c6be5-124">Additionally if there are any points in your experience where you display images of the controllers make sure to provide updated images using the Windows Mixed Reality motion controllers.</span></span>

## <a name="haptics"></a><span data-ttu-id="c6be5-125">Haptics</span><span class="sxs-lookup"><span data-stu-id="c6be5-125">Haptics</span></span>

<span data-ttu-id="c6be5-126">[Windows 10 April 2018 Update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)以降では、Haptics が Windows Mixed Reality での SteamVR エクスペリエンスでサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c6be5-126">Beginning with the [Windows 10 April 2018 Update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018), haptics are now supported for SteamVR experiences on Windows Mixed Reality.</span></span> <span data-ttu-id="c6be5-127">SteamVR アプリまたはゲームに既に haptics のサポートが含まれている場合は、 [Windows Mixed Reality モーションコントローラー](../../design/motion-controllers.md)を使用して (追加の作業を行わずに) 動作するようになります。</span><span class="sxs-lookup"><span data-stu-id="c6be5-127">If your SteamVR app or game already includes support for haptics, it should now work (with no additional work) with [Windows Mixed Reality motion controllers](../../design/motion-controllers.md).</span></span>

<span data-ttu-id="c6be5-128">Windows Mixed Reality モーションコントローラーは、他の SteamVR モーションコントローラーにある線形アクチュエータではなく、標準の haptics モータを使用します。これにより、予期しないユーザーエクスペリエンスが多少異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c6be5-128">Windows Mixed Reality motion controllers use a standard haptics motor, as opposed to the linear actuators found in some other SteamVR motion controllers, which can lead to a slightly different-than-expected user experience.</span></span> <span data-ttu-id="c6be5-129">そのため、Windows Mixed Reality motion controller を使用して haptics の設計をテストおよびチューニングすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c6be5-129">So, we recommend testing and tuning your haptics design with Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="c6be5-130">たとえば、Windows Mixed Reality モーションコントローラーでは、短い haptic パルス (5-10 ミリ秒) があまり目立たない場合があります。</span><span class="sxs-lookup"><span data-stu-id="c6be5-130">For example, sometimes short haptic pulses (5-10 ms) are less noticeable on Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="c6be5-131">より顕著なパルスを生成するには、もう一度電源をオフにするように指示する前に、より長い "クリック" (40 ~ 70 ミリ秒) を送信してください。</span><span class="sxs-lookup"><span data-stu-id="c6be5-131">To produce a more noticeable pulse, experiment with sending a longer “click” (40-70ms) to give the motor more time to spin up before being told to power off again.</span></span>

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a><span data-ttu-id="c6be5-132">Windows Mixed Reality の [スタート] メニューから SteamVR アプリを起動する</span><span class="sxs-lookup"><span data-stu-id="c6be5-132">Launching SteamVR apps from Windows Mixed Reality Start menu</span></span>

<span data-ttu-id="c6be5-133">ストリームによって配布される VR エクスペリエンスについては、windows [Mixed reality For Steamvr Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) と最新の [windows Insider](https://insider.windows.com) RS5 フライトを更新しました。これにより、Steamvr タイトルが [すべてのアプリ] リストの windows Mixed reality の [スタート] メニューに自動的に表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c6be5-133">For VR experiences distributed through Steam, we've [updated the Windows Mixed Reality for SteamVR Beta](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest [Windows Insider](https://insider.windows.com) RS5 flights so that SteamVR titles now show up in the Windows Mixed Reality Start menu in the "All apps" list automatically.</span></span> <span data-ttu-id="c6be5-134">これらのソフトウェアバージョンがインストールされているので、お客様は、ヘッドセットを削除せずに、Windows Mixed Reality ホーム内から直接 SteamVR タイトルを起動できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c6be5-134">With these software versions installed, your customers can now launch SteamVR titles directly from within the Windows Mixed Reality home without removing their headsets.</span></span>

## <a name="windows-mixed-reality-logo"></a><span data-ttu-id="c6be5-135">Windows Mixed Reality ロゴ</span><span class="sxs-lookup"><span data-stu-id="c6be5-135">Windows Mixed Reality logo</span></span>

<span data-ttu-id="c6be5-136">タイトルの Windows Mixed Reality サポートを表示するには、アプリのランディングページの [ストアの編集] ページに移動し、[基本情報] タブをクリックして、[仮想現実] を下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="c6be5-136">To display Windows Mixed Reality support for your title, go to the "Edit Store Page" link on your App Landing Page, click the "Basic Info" tab, and scroll down to "Virtual Reality."</span></span> <span data-ttu-id="c6be5-137">[Windows Mixed Reality を非表示にする] をオフにして、ストアに発行します。</span><span class="sxs-lookup"><span data-stu-id="c6be5-137">Uncheck the "Hide Windows Mixed Reality" and then publish to the store.</span></span>

## <a name="bugs-and-feedback"></a><span data-ttu-id="c6be5-138">バグとフィードバック</span><span class="sxs-lookup"><span data-stu-id="c6be5-138">Bugs and feedback</span></span>

<span data-ttu-id="c6be5-139">Windows Mixed Reality SteamVR エクスペリエンスを向上させるために、お客様のフィードバックは非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="c6be5-139">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="c6be5-140">すべてのフィードバックとバグを [Windows フィードバックハブ](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)から送信してください。</span><span class="sxs-lookup"><span data-stu-id="c6be5-140">Please submit all feedback and bugs through the [Windows Feedback Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span> <span data-ttu-id="c6be5-141">ここでは [、SteamVR フィードバックを可能な限り活用するためのヒント](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)を紹介します。</span><span class="sxs-lookup"><span data-stu-id="c6be5-141">Here are some [tips on how to make your SteamVR feedback as helpful as possible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).</span></span>

<span data-ttu-id="c6be5-142">共有する質問やコメントがある場合は、 [ストリームフォーラム](https://steamcommunity.com/app/719950/discussions/)からもご連絡いただけます。</span><span class="sxs-lookup"><span data-stu-id="c6be5-142">If you have questions or comments to share, you can also reach us on our [Steam forum](https://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="faqs-and-troubleshooting"></a><span data-ttu-id="c6be5-143">FAQ とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c6be5-143">FAQs and troubleshooting</span></span>

<span data-ttu-id="c6be5-144">一般的な問題が発生したときに、エクスペリエンスをセットアップまたは再生するには、 [最新のトラブルシューティング手順を確認](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)してください。</span><span class="sxs-lookup"><span data-stu-id="c6be5-144">If you're running into general issues setting up or playing your experience, [check out the latest troubleshooting steps](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6be5-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6be5-145">See also</span></span>
* [<span data-ttu-id="c6be5-146">ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="c6be5-146">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="c6be5-147">ヘッドセットとモーションコントローラーのドライバー履歴</span><span class="sxs-lookup"><span data-stu-id="c6be5-147">Headset and motion controller driver history</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [<span data-ttu-id="c6be5-148">Windows Mixed Reality の PC ハードウェアの最小互換性ガイドライン</span><span class="sxs-lookup"><span data-stu-id="c6be5-148">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
