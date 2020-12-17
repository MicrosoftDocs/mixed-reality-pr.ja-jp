---
title: Windows Mixed Reality 用に SteamVR アプリを更新する
description: Windows Mixed Reality ヘッドセットとの互換性を最大化するために SteamVR アプリケーションを更新するためのベストプラクティス。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: SteamVR、互換性、移植、HoloLens ファースト世代、mixed reality ヘッドセット、windows mixed reality ヘッドセット、移行、Windows 10、蒸気、motion controller、haptics
ms.openlocfilehash: 94b6aad63156d752858c6566174ff01e6127d75d
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612906"
---
# <a name="updating-steamvr-apps-for-windows-mixed-reality"></a><span data-ttu-id="c6b08-104">Windows Mixed Reality 用に SteamVR アプリを更新する</span><span class="sxs-lookup"><span data-stu-id="c6b08-104">Updating SteamVR apps for Windows Mixed Reality</span></span>

<span data-ttu-id="c6b08-105">Windows Mixed Reality ヘッドセットで実行するために、開発者は SteamVR エクスペリエンスをテストして最適化することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c6b08-105">We encourage developers to test and optimize their SteamVR experiences to run on Windows Mixed Reality headsets.</span></span> <span data-ttu-id="c6b08-106">このドキュメントでは、Windows Mixed Reality でのエクスペリエンスを向上させるために実行できる一般的な機能強化について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6b08-106">This documentation covers common improvements you can make to get your experiences running great on Windows Mixed Reality.</span></span>

## <a name="initial-setup-instructions"></a><span data-ttu-id="c6b08-107">初期セットアップの手順</span><span class="sxs-lookup"><span data-stu-id="c6b08-107">Initial setup instructions</span></span>

<span data-ttu-id="c6b08-108">Windows Mixed Reality でゲームやアプリのテストを開始するには、まず、[ファーストステップガイド](https://aka.ms/WindowsMixedRealitySteamVR)に従ってください。</span><span class="sxs-lookup"><span data-stu-id="c6b08-108">To start testing out your game or app on Windows Mixed Reality make sure to first follow our [getting started guide.](https://aka.ms/WindowsMixedRealitySteamVR)</span></span>

## <a name="controller-models"></a><span data-ttu-id="c6b08-109">コントローラーモデル</span><span class="sxs-lookup"><span data-stu-id="c6b08-109">Controller Models</span></span>

1. <span data-ttu-id="c6b08-110">アプリがコントローラーモデルをレンダリングする場合:</span><span class="sxs-lookup"><span data-stu-id="c6b08-110">If your app renders controller models:</span></span>
    * <span data-ttu-id="c6b08-111">[Windows Mixed Reality モーションコントローラーモデル](../../design/motion-controllers.md#rendering-the-motion-controller-model)を使用する</span><span class="sxs-lookup"><span data-stu-id="c6b08-111">Use the [Windows Mixed Reality motion controller models](../../design/motion-controllers.md#rendering-the-motion-controller-model)</span></span>
    * <span data-ttu-id="c6b08-112">IVRRenderModel:: GetComponentState を使用して、コンポーネントパーツへのローカル変換を取得します (ポインターの例など)。</span><span class="sxs-lookup"><span data-stu-id="c6b08-112">Use IVRRenderModel::GetComponentState to get local transforms to component parts (for example, Pointer pose)</span></span>
2. <span data-ttu-id="c6b08-113">ききの概念を持つエクスペリエンスでは、コントローラーを区別するために入力 Api からヒントを取得する必要があります [(Unity の例)。](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span><span class="sxs-lookup"><span data-stu-id="c6b08-113">Experiences that have a notion of handedness should get hints from the input APIs to differentiate controllers [(Unity example)](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table)</span></span>

## <a name="controls"></a><span data-ttu-id="c6b08-114">コントロール</span><span class="sxs-lookup"><span data-stu-id="c6b08-114">Controls</span></span>

<span data-ttu-id="c6b08-115">コントロールのレイアウトをデザインまたは調整する場合は、次の予約済みコマンドのセットに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c6b08-115">When designing or adjusting your control layout, keep in mind the following set of reserved commands:</span></span>
1. <span data-ttu-id="c6b08-116">**左と右のアナログサムスティック** をクリックすると、**蒸気ダッシュボード** 用に予約されます。</span><span class="sxs-lookup"><span data-stu-id="c6b08-116">Clicking down the **left and right analog thumbstick** is reserved for the **Steam Dashboard**.</span></span>

> [!NOTE]
> <span data-ttu-id="c6b08-117">HP リバーブ G2 コントローラーを使用している場合は、右のメニューボタンをクリックすると、 **蒸気ダッシュボード** 用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="c6b08-117">If you're using an HP Reverb G2 controller, clicking the right menu button is reserved for the **Steam Dashboard**.</span></span>

2. <span data-ttu-id="c6b08-118">**Windows のボタンをクリック** すると、常にユーザーが Windows Mixed Reality ホームに戻ります。</span><span class="sxs-lookup"><span data-stu-id="c6b08-118">The **Windows button** will always return users to the Windows Mixed Reality home.</span></span>

<span data-ttu-id="c6b08-119">可能であれば、既定ではサムスティックベースの [電話](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c6b08-119">If possible, default to thumbstick-based teleportation to match the [Windows Mixed Reality home](../../discover/navigating-the-windows-mixed-reality-home.md#getting-around-your-home) teleportation behavior</span></span>

## <a name="tooltips-and-ui"></a><span data-ttu-id="c6b08-120">ツールヒントと UI</span><span class="sxs-lookup"><span data-stu-id="c6b08-120">Tooltips and UI</span></span>

<span data-ttu-id="c6b08-121">多くの VR ゲームでは、モーションコントローラーのツールヒントとオーバーレイを利用して、ユーザーにアプリまたはゲームの最も重要なコマンドを学習させることができます。</span><span class="sxs-lookup"><span data-stu-id="c6b08-121">Many VR games take advantage of motion controller tooltips and overlays to teach users their app or games most important commands.</span></span> <span data-ttu-id="c6b08-122">Windows Mixed reality 用にアプリケーションをチューニングする場合、ツールヒントが Windows コントローラーモデルにマップされるように、エクスペリエンスのこの部分を確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c6b08-122">When tuning your application for Windows Mixed reality, we recommend reviewing this part of your experience to make sure the tooltips map to the Windows controller models.</span></span>

<span data-ttu-id="c6b08-123">また、コントローラーのイメージを表示するポイントがある場合は、Windows Mixed Reality モーションコントローラーを使用して、更新されたイメージを提供するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="c6b08-123">Additionally if there are any points in your experience where you display images of the controllers make sure to provide updated images using the Windows Mixed Reality motion controllers.</span></span>

## <a name="haptics"></a><span data-ttu-id="c6b08-124">Haptics</span><span class="sxs-lookup"><span data-stu-id="c6b08-124">Haptics</span></span>

<span data-ttu-id="c6b08-125">[Windows 10 April 2018 Update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018)以降では、Haptics が Windows Mixed Reality での SteamVR エクスペリエンスでサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c6b08-125">Beginning with the [Windows 10 April 2018 Update](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-april-2018), haptics are now supported for SteamVR experiences on Windows Mixed Reality.</span></span> <span data-ttu-id="c6b08-126">SteamVR アプリまたはゲームに既に haptics のサポートが含まれている場合は、 [Windows Mixed Reality モーションコントローラー](../../design/motion-controllers.md)を使用して (追加の作業を行わずに) 動作するようになります。</span><span class="sxs-lookup"><span data-stu-id="c6b08-126">If your SteamVR app or game already includes support for haptics, it should now work (with no additional work) with [Windows Mixed Reality motion controllers](../../design/motion-controllers.md).</span></span>

<span data-ttu-id="c6b08-127">Windows Mixed Reality モーションコントローラーでは、他の SteamVR モーションコントローラーの線形アクチュエータではなく、標準の haptics モータが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c6b08-127">Windows Mixed Reality motion controllers use a standard haptics motor, as opposed to the linear actuators found in some other SteamVR motion controllers.</span></span> <span data-ttu-id="c6b08-128">これにより、想定外のユーザーエクスペリエンスが多少異なります。</span><span class="sxs-lookup"><span data-stu-id="c6b08-128">This can lead to a slightly different-than-expected user experience.</span></span> <span data-ttu-id="c6b08-129">そのため、Windows Mixed Reality motion controller を使用して haptics の設計をテストおよびチューニングすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c6b08-129">So, we recommend testing and tuning your haptics design with Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="c6b08-130">たとえば、Windows Mixed Reality モーションコントローラーでは、短い haptic パルス (5-10 ミリ秒) があまり目立たない場合があります。</span><span class="sxs-lookup"><span data-stu-id="c6b08-130">For example, sometimes short haptic pulses (5-10 ms) are less noticeable on Windows Mixed Reality motion controllers.</span></span> <span data-ttu-id="c6b08-131">より顕著なパルスを生成するには、もう一度電源をオフにするように指示する前に、より長い "クリック" (40-70 ミリ秒) を送信してみてください。</span><span class="sxs-lookup"><span data-stu-id="c6b08-131">To produce a more noticeable pulse, experiment with sending a longer “click” (40-70 ms) to give the motor more time to spin up before being told to power off again.</span></span>

## <a name="launching-steamvr-apps-from-windows-mixed-reality-start-menu"></a><span data-ttu-id="c6b08-132">Windows Mixed Reality の [スタート] メニューから SteamVR アプリを起動する</span><span class="sxs-lookup"><span data-stu-id="c6b08-132">Launching SteamVR apps from Windows Mixed Reality Start menu</span></span>

<span data-ttu-id="c6b08-133">ストリームによって配布される VR エクスペリエンスについては、最新の[windows リリース](https://insider.windows.com)と共に[steamvr の windows Mixed Reality を更新](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800)しました。</span><span class="sxs-lookup"><span data-stu-id="c6b08-133">For VR experiences distributed through Steam, we've [updated Windows Mixed Reality for SteamVR](https://steamcommunity.com/games/719950/announcements/detail/1687045485866139800) along with the latest [Windows releases](https://insider.windows.com).</span></span> <span data-ttu-id="c6b08-134">SteamVR のタイトルが、[すべてのアプリ] の一覧の Windows Mixed Reality の [スタート] メニューに自動的に表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="c6b08-134">SteamVR titles now show up in the Windows Mixed Reality Start menu in the "All apps" list automatically.</span></span>

## <a name="windows-mixed-reality-logo"></a><span data-ttu-id="c6b08-135">Windows Mixed Reality ロゴ</span><span class="sxs-lookup"><span data-stu-id="c6b08-135">Windows Mixed Reality logo</span></span>

<span data-ttu-id="c6b08-136">タイトルの Windows Mixed Reality サポートを表示するには、アプリのランディングページの [ストアの編集] ページに移動し、[基本情報] タブを選択して、[仮想現実] を下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="c6b08-136">To display Windows Mixed Reality support for your title, go to the "Edit Store Page" link on your App Landing Page, select the "Basic Info" tab, and scroll down to "Virtual Reality."</span></span> <span data-ttu-id="c6b08-137">[Windows Mixed Reality を非表示にする] をオフにして、ストアに発行します。</span><span class="sxs-lookup"><span data-stu-id="c6b08-137">Uncheck the "Hide Windows Mixed Reality" and then publish to the store.</span></span>

## <a name="bugs-and-feedback"></a><span data-ttu-id="c6b08-138">バグとフィードバック</span><span class="sxs-lookup"><span data-stu-id="c6b08-138">Bugs and feedback</span></span>

<span data-ttu-id="c6b08-139">Windows Mixed Reality SteamVR エクスペリエンスを向上させるために、お客様のフィードバックは非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="c6b08-139">Your feedback is invaluable when it comes to improving the Windows Mixed Reality SteamVR experience.</span></span> <span data-ttu-id="c6b08-140">[Windows フィードバックハブ](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback)を通じてすべてのフィードバックとバグを送信します。</span><span class="sxs-lookup"><span data-stu-id="c6b08-140">Submit all feedback and bugs through the [Windows Feedback Hub](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/filing-feedback).</span></span> <span data-ttu-id="c6b08-141">ここでは [、SteamVR フィードバックを可能な限り活用するためのヒント](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr)を紹介します。</span><span class="sxs-lookup"><span data-stu-id="c6b08-141">Here are some [tips on how to make your SteamVR feedback as helpful as possible](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality#sharing-feedback-on-steamvr).</span></span>

<span data-ttu-id="c6b08-142">共有する質問やコメントがある場合は、 [ストリームフォーラム](https://steamcommunity.com/app/719950/discussions/)からもご連絡いただけます。</span><span class="sxs-lookup"><span data-stu-id="c6b08-142">If you have questions or comments to share, you can also reach us on our [Steam forum](https://steamcommunity.com/app/719950/discussions/).</span></span>

## <a name="faqs-and-troubleshooting"></a><span data-ttu-id="c6b08-143">FAQ とトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c6b08-143">FAQs and troubleshooting</span></span>

<span data-ttu-id="c6b08-144">一般的な問題が発生したときに、エクスペリエンスをセットアップまたは再生するには、 [最新のトラブルシューティング手順を確認](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr)してください。</span><span class="sxs-lookup"><span data-stu-id="c6b08-144">If you're running into general issues setting up or playing your experience, [check out the latest troubleshooting steps](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/troubleshooting-windows-mixed-reality#steamvr).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6b08-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6b08-145">See also</span></span>

* [<span data-ttu-id="c6b08-146">ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="c6b08-146">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="c6b08-147">ヘッドセットとモーションコントローラーのドライバー履歴</span><span class="sxs-lookup"><span data-stu-id="c6b08-147">Headset and motion controller driver history</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software)
* [<span data-ttu-id="c6b08-148">Windows Mixed Reality の PC ハードウェアの最小互換性ガイドライン</span><span class="sxs-lookup"><span data-stu-id="c6b08-148">Windows Mixed Reality minimum PC hardware compatibility guidelines</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines)
