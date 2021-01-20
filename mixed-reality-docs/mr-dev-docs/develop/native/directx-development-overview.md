---
title: ネイティブ開発の概要
description: Windows Mixed Reality Api を直接使用して DirectX ベースの mixed reality エンジンを構築する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, holographic レンダリング, ネイティブ, ネイティブアプリ, WinRT, WinRT アプリ, プラットフォーム Api, カスタムエンジン, ミドルウェア, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: b137fad12740542deb4995485201a9bd0d1d7662
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581040"
---
# <a name="native-development-overview"></a><span data-ttu-id="813fc-104">ネイティブ開発の概要</span><span class="sxs-lookup"><span data-stu-id="813fc-104">Native development overview</span></span>

![ネイティブバナーロゴ](../images/native_logo_banner.png)

<span data-ttu-id="813fc-106">[Unity](../unity/unity-development-overview.md)や[unreal](../unreal/unreal-development-overview.md)のような3d エンジンは、自分が開いている唯一の Mixed Reality 開発パスではありません。</span><span class="sxs-lookup"><span data-stu-id="813fc-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="813fc-107">Windows Mixed Reality Api と DirectX 11 または DirectX 12 を使用して、Mixed Reality アプリを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="813fc-107">You can also create Mixed Reality apps using the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="813fc-108">プラットフォームソースにアクセスすることによって、基本的に独自のミドルウェアまたはフレームワークを構築しています。</span><span class="sxs-lookup"><span data-stu-id="813fc-108">By going to the platform source, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="813fc-109">管理する既存の WinRT プロジェクトがある場合は、主な [winrt ドキュメント](creating-a-holographic-directx-project.md)に進んでください。</span><span class="sxs-lookup"><span data-stu-id="813fc-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="813fc-110">開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="813fc-110">Development checkpoints</span></span>

<span data-ttu-id="813fc-111">次のチェックポイントを使用して、Unity のゲームやアプリケーションを Mixed Reality の世界に移植することができます。</span><span class="sxs-lookup"><span data-stu-id="813fc-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="813fc-112">1.はじめに</span><span class="sxs-lookup"><span data-stu-id="813fc-112">1. Getting started</span></span>

<span data-ttu-id="813fc-113">Windows Mixed Reality は [、次の2種類のアプリを](../../design/app-views.md)サポートしています。</span><span class="sxs-lookup"><span data-stu-id="813fc-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="813fc-114">[HOLOGRAPHICSPACE api](getting-a-holographicspace.md)または [OpenXR api](openxr.md)を使用して、ヘッドセットの表示を埋める [イマーシブビュー](../../design/app-views.md)をレンダリングする UWP または Win32 **Mixed Reality アプリケーション**</span><span class="sxs-lookup"><span data-stu-id="813fc-114">UWP or Win32 **Mixed Reality applications** that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) that fills the headset display</span></span>
* <span data-ttu-id="813fc-115">DirectX、XAML、または別のフレームワークを使用して、Windows Mixed Reality ホームのスレートに [2d ビュー](../../design/app-views.md#2d-views)をレンダリングする **2d アプリ**(UWP)</span><span class="sxs-lookup"><span data-stu-id="813fc-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="813fc-116">[2d ビューとイマーシブビュー](../../design/app-views.md)の DirectX 開発の違いは、主に holographic のレンダリングと空間入力に関係しています。</span><span class="sxs-lookup"><span data-stu-id="813fc-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="813fc-117">UWP アプリケーションの [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) または Win32 アプリケーションの HWND が必要であり、ほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="813fc-117">Your UWP application's [IFrameworkView](/uwp/api/Windows.ApplicationModel.Core.IFrameworkView) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="813fc-118">アプリで使用できる WinRT Api にも同じことが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="813fc-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="813fc-119">ただし、holographic 機能を利用するには、これらの Api の異なるサブセットを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="813fc-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="813fc-120">たとえば、holographic アプリケーションのシステムでは、発生しているスワップチェーンとフレームを管理して、予測可能なフレームループを有効にします。</span><span class="sxs-lookup"><span data-stu-id="813fc-120">For example, the system for holographic applications manages the swapchain and frame present to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="813fc-121">2. コア構成要素</span><span class="sxs-lookup"><span data-stu-id="813fc-121">2. Core building blocks</span></span>

<span data-ttu-id="813fc-122">Windows Mixed Reality アプリケーションは、次の Api を使用して、HoloLens とその他のイマーシブヘッドセットの [Mixed Reality](../../discover/mixed-reality.md) エクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="813fc-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="813fc-123">機能</span><span class="sxs-lookup"><span data-stu-id="813fc-123">Feature</span></span>  |  <span data-ttu-id="813fc-124">説明</span><span class="sxs-lookup"><span data-stu-id="813fc-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="813fc-125">視線入力</span><span class="sxs-lookup"><span data-stu-id="813fc-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="813fc-126">ホログラムを見ることによってユーザーがホログラムを対象とすることができるようにします</span><span class="sxs-lookup"><span data-stu-id="813fc-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="813fc-127">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="813fc-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="813fc-128">アプリに空間アクションを追加する</span><span class="sxs-lookup"><span data-stu-id="813fc-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="813fc-129">ホログラフィック レンダリング</span><span class="sxs-lookup"><span data-stu-id="813fc-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="813fc-130">ユーザーに対して世界中の正確な場所にホログラムを描画します</span><span class="sxs-lookup"><span data-stu-id="813fc-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="813fc-131">モーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="813fc-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="813fc-132">ユーザーが Mixed Reality 環境でアクションを実行できるようにする</span><span class="sxs-lookup"><span data-stu-id="813fc-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="813fc-133">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="813fc-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="813fc-134">仮想メッシュ オーバーレイを使用して物理領域をマップし、環境の境界をマークします</span><span class="sxs-lookup"><span data-stu-id="813fc-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="813fc-135">音声</span><span class="sxs-lookup"><span data-stu-id="813fc-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="813fc-136">ユーザーが話したキーワード、フレーズ、ディクテーションをキャプチャします</span><span class="sxs-lookup"><span data-stu-id="813fc-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="813fc-137">OpenXR の [ロードマップ](openxr.md#roadmap) のドキュメントで、近日中および開発中のコア機能を確認できます。</span><span class="sxs-lookup"><span data-stu-id="813fc-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="813fc-138">3. 配置とテスト</span><span class="sxs-lookup"><span data-stu-id="813fc-138">3. Deploying and testing</span></span>

<span data-ttu-id="813fc-139">HoloLens 2 または Windows Mixed Reality イマーシブヘッドセットで OpenXR を使用してデスクトップで開発できます。</span><span class="sxs-lookup"><span data-stu-id="813fc-139">You can develop on a desktop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset.</span></span>  <span data-ttu-id="813fc-140">ヘッドセットへのアクセス権がない場合は、代わりに [HoloLens 2 エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md) または [Windows Mixed Reality シミュレーター](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="813fc-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="813fc-141">次の操作</span><span class="sxs-lookup"><span data-stu-id="813fc-141">What's next?</span></span>

<span data-ttu-id="813fc-142">開発者の仕事に終わりはありません。新しいツールや SDK について学ぶ場合は特にこれが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="813fc-142">A developer's job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="813fc-143">次のセクションでは、既に完了している初心者レベルの資料以外の領域について説明します。</span><span class="sxs-lookup"><span data-stu-id="813fc-143">The following sections can take you into areas beyond the beginner level material you've already completed.</span></span> <span data-ttu-id="813fc-144">これらのトピックとリソースは順番には記載されていないため、先に進んで調査してください。</span><span class="sxs-lookup"><span data-stu-id="813fc-144">These topics and resources aren't in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="813fc-145">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="813fc-145">Additional resources</span></span>

<span data-ttu-id="813fc-146">OpenXR ゲームのレベルアップを検討している場合は、以下のリンクを確認してください。</span><span class="sxs-lookup"><span data-stu-id="813fc-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="813fc-147">OpenXR ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="813fc-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="813fc-148">OpenXR パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="813fc-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="813fc-149">OpenXR トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="813fc-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="813fc-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="813fc-150">See also</span></span>
* [<span data-ttu-id="813fc-151">アプリ モデル</span><span class="sxs-lookup"><span data-stu-id="813fc-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="813fc-152">アプリ ビュー</span><span class="sxs-lookup"><span data-stu-id="813fc-152">App views</span></span>](../../design/app-views.md)