---
title: ネイティブ開発の概要
description: Windows Mixed Reality Api を直接使用して、DirectX ベースの mixed reality エンジンをビルドします。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, holographic レンダリング, ネイティブ, ネイティブアプリ, WinRT, WinRT アプリ, プラットフォーム Api, カスタムエンジン, ミドルウェア, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 0d5e364fdb4faac73f28649f5c009823a74ac595
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679651"
---
# <a name="native-development-overview"></a><span data-ttu-id="276bf-104">ネイティブ開発の概要</span><span class="sxs-lookup"><span data-stu-id="276bf-104">Native development overview</span></span>

![ネイティブバナーロゴ](../images/native_logo_banner.png)

<span data-ttu-id="276bf-106">[Unity](../unity/unity-development-overview.md)や[unreal](../unreal/unreal-development-overview.md)のような3d エンジンは、自分が開いている唯一の Mixed Reality 開発パスではありません。</span><span class="sxs-lookup"><span data-stu-id="276bf-106">3D engines like [Unity](../unity/unity-development-overview.md) or [Unreal](../unreal/unreal-development-overview.md) aren't the only Mixed Reality development paths open to you.</span></span> <span data-ttu-id="276bf-107">DirectX 11 または DirectX 12 で Windows Mixed Reality Api に直接コーディングすることで、Mixed Reality アプリを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="276bf-107">You can also create Mixed Reality apps by directly coding to the Windows Mixed Reality APIs with DirectX 11 or DirectX 12.</span></span> <span data-ttu-id="276bf-108">プラットフォームを直接利用することで、本質的に独自のミドルウェアまたはフレームワークを構築しています。</span><span class="sxs-lookup"><span data-stu-id="276bf-108">By leveraging the platform directly, you're essentially building your own middleware or framework.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="276bf-109">管理する既存の WinRT プロジェクトがある場合は、主な [winrt ドキュメント](creating-a-holographic-directx-project.md)に進んでください。</span><span class="sxs-lookup"><span data-stu-id="276bf-109">If you have an existing WinRT project that you'd like to maintain, head over to our main [WinRT documentation](creating-a-holographic-directx-project.md).</span></span> 

## <a name="development-checkpoints"></a><span data-ttu-id="276bf-110">開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="276bf-110">Development checkpoints</span></span>

<span data-ttu-id="276bf-111">次のチェックポイントを使用して、Unity のゲームやアプリケーションを Mixed Reality の世界に移植することができます。</span><span class="sxs-lookup"><span data-stu-id="276bf-111">Use the following checkpoints to bring your Unity games and applications into the world of mixed reality.</span></span>

### <a name="1-getting-started"></a><span data-ttu-id="276bf-112">1.はじめに</span><span class="sxs-lookup"><span data-stu-id="276bf-112">1. Getting started</span></span>

<span data-ttu-id="276bf-113">Windows Mixed Reality は [、次の2種類のアプリを](../../design/app-views.md)サポートしています。</span><span class="sxs-lookup"><span data-stu-id="276bf-113">Windows Mixed Reality supports [two kinds of apps](../../design/app-views.md):</span></span>
* <span data-ttu-id="276bf-114">[HOLOGRAPHICSPACE api](getting-a-holographicspace.md)または [OpenXR api](openxr.md)を使用して、ヘッドセットの表示を満たすユーザーに [イマーシブビュー](../../design/app-views.md)をレンダリングする **Mixed reality アプリケーション**(UWP または Win32)</span><span class="sxs-lookup"><span data-stu-id="276bf-114">**Mixed-reality applications** (UWP or Win32) that use the [HolographicSpace API](getting-a-holographicspace.md) or [OpenXR API](openxr.md) to render an [immersive view](../../design/app-views.md) to the user that fills the headset display</span></span>
* <span data-ttu-id="276bf-115">DirectX、XAML、または別のフレームワークを使用して、Windows Mixed Reality ホームのスレートに [2d ビュー](../../design/app-views.md#2d-views)をレンダリングする **2d アプリ**(UWP)</span><span class="sxs-lookup"><span data-stu-id="276bf-115">**2D apps** (UWP) that use DirectX, XAML, or another framework to render [2D views](../../design/app-views.md#2d-views) on slates in the Windows Mixed Reality home</span></span>

<span data-ttu-id="276bf-116">[2d ビューとイマーシブビュー](../../design/app-views.md)の DirectX 開発の違いは、主に holographic のレンダリングと空間入力に関係しています。</span><span class="sxs-lookup"><span data-stu-id="276bf-116">The differences between DirectX development for [2D views and immersive views](../../design/app-views.md) primarily concern holographic rendering and spatial input.</span></span> <span data-ttu-id="276bf-117">UWP アプリケーションの [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) または Win32 アプリケーションの HWND が必要であり、ほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="276bf-117">Your UWP application's [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) or your Win32 application's HWND are required and remain largely the same.</span></span> <span data-ttu-id="276bf-118">アプリで使用できる WinRT Api にも同じことが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="276bf-118">The same is true for the WinRT APIs that are available to your app.</span></span> <span data-ttu-id="276bf-119">ただし、holographic 機能を利用するには、これらの Api の異なるサブセットを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="276bf-119">But you must use a different subset of these APIs to take advantage of holographic features.</span></span> <span data-ttu-id="276bf-120">たとえば、存在するスワップチェーンと frame は、holographic アプリケーション用にシステムによって管理されます。これにより、予測可能なフレームループが有効になります。</span><span class="sxs-lookup"><span data-stu-id="276bf-120">For example, the swapchain and frame present is managed by the system for holographic applications in order to enable a pose-predicted frame loop.</span></span>

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a><span data-ttu-id="276bf-121">2. コア構成要素</span><span class="sxs-lookup"><span data-stu-id="276bf-121">2. Core building blocks</span></span>

<span data-ttu-id="276bf-122">Windows Mixed Reality アプリケーションは、次の Api を使用して、HoloLens とその他のイマーシブヘッドセットの [Mixed Reality](../../discover/mixed-reality.md) エクスペリエンスを構築します。</span><span class="sxs-lookup"><span data-stu-id="276bf-122">Windows Mixed Reality applications use the following APIs to build [mixed-reality](../../discover/mixed-reality.md) experiences for HoloLens and other immersive headsets:</span></span>

|  <span data-ttu-id="276bf-123">機能</span><span class="sxs-lookup"><span data-stu-id="276bf-123">Feature</span></span>  |  <span data-ttu-id="276bf-124">説明</span><span class="sxs-lookup"><span data-stu-id="276bf-124">Capability</span></span>  |
| --- | --- |
| [<span data-ttu-id="276bf-125">視線入力</span><span class="sxs-lookup"><span data-stu-id="276bf-125">Gaze</span></span>](../../design/gaze-and-commit.md) | <span data-ttu-id="276bf-126">ホログラムを見ることによってユーザーがホログラムを対象とすることができるようにします</span><span class="sxs-lookup"><span data-stu-id="276bf-126">Let users target holograms with by looking at them</span></span> |
| [<span data-ttu-id="276bf-127">ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="276bf-127">Gesture</span></span>](../../design/gaze-and-commit.md#composite-gestures) | <span data-ttu-id="276bf-128">アプリに空間アクションを追加する</span><span class="sxs-lookup"><span data-stu-id="276bf-128">Add spatial actions to your apps</span></span> |
| [<span data-ttu-id="276bf-129">ホログラフィック レンダリング</span><span class="sxs-lookup"><span data-stu-id="276bf-129">Holographic rendering</span></span>](../platform-capabilities-and-apis/rendering.md) | <span data-ttu-id="276bf-130">ユーザーに対して世界中の正確な場所にホログラムを描画します</span><span class="sxs-lookup"><span data-stu-id="276bf-130">Draw a hologram at a precise location in the world around your users</span></span> |
| [<span data-ttu-id="276bf-131">モーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="276bf-131">Motion controller</span></span>](../../design/motion-controllers.md) | <span data-ttu-id="276bf-132">ユーザーが Mixed Reality 環境でアクションを実行できるようにする</span><span class="sxs-lookup"><span data-stu-id="276bf-132">Let your users take action in your Mixed Reality environments</span></span> |
| [<span data-ttu-id="276bf-133">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="276bf-133">Spatial mapping</span></span>](../../design/spatial-mapping.md) | <span data-ttu-id="276bf-134">仮想メッシュ オーバーレイを使用して物理領域をマップし、環境の境界をマークします</span><span class="sxs-lookup"><span data-stu-id="276bf-134">Map your physical space with a virtual mesh overlay to mark the boundaries of your environment</span></span> |
| [<span data-ttu-id="276bf-135">音声</span><span class="sxs-lookup"><span data-stu-id="276bf-135">Voice</span></span>](../../design/voice-input.md) | <span data-ttu-id="276bf-136">ユーザーが話したキーワード、フレーズ、ディクテーションをキャプチャします</span><span class="sxs-lookup"><span data-stu-id="276bf-136">Capture spoken keywords, phrases, and dictation from your users</span></span> |
 
> [!NOTE]
> <span data-ttu-id="276bf-137">OpenXR の [ロードマップ](openxr.md#roadmap) のドキュメントで、近日中および開発中のコア機能を確認できます。</span><span class="sxs-lookup"><span data-stu-id="276bf-137">You can find upcoming and in-development core features in the OpenXR [roadmap](openxr.md#roadmap) documentation.</span></span>

### <a name="3-deploying-and-testing"></a><span data-ttu-id="276bf-138">3. 配置とテスト</span><span class="sxs-lookup"><span data-stu-id="276bf-138">3. Deploying and testing</span></span>

<span data-ttu-id="276bf-139">HoloLens 2 で OpenXR を使用するか、デスクトップで Windows Mixed Reality イマーシブ ヘッドセットを使用して開発できます。</span><span class="sxs-lookup"><span data-stu-id="276bf-139">You can develop using OpenXR on a HoloLens 2 or Windows Mixed Reality immersive headset on the desktop.</span></span>  <span data-ttu-id="276bf-140">ヘッドセットへのアクセス権がない場合は、代わりに [HoloLens 2 エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md) または [Windows Mixed Reality シミュレーター](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="276bf-140">If you don't have access to a headset, you can use the [HoloLens 2 Emulator](../platform-capabilities-and-apis/using-the-hololens-emulator.md) or the [Windows Mixed Reality Simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) instead.</span></span>

## <a name="whats-next"></a><span data-ttu-id="276bf-141">次の操作</span><span class="sxs-lookup"><span data-stu-id="276bf-141">What's next?</span></span>

<span data-ttu-id="276bf-142">開発者の仕事に終わりはありません。新しいツールや SDK について学ぶ場合は特にこれが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="276bf-142">A developers job is never done, especially when learning a new tool or SDK.</span></span> <span data-ttu-id="276bf-143">以降のセクションでは、既に終えた初級レベルの教材からは一歩進んだ領域について説明します。また、行き詰まった場合に役に立つリソースも紹介します。</span><span class="sxs-lookup"><span data-stu-id="276bf-143">The following sections can take you into areas beyond the beginner level material you've already completed, along with helpful resources if you get stuck.</span></span> <span data-ttu-id="276bf-144">これらのトピックとリソースは順番に並んでいるわけではないため、お好きなところから自由に参照することができます。</span><span class="sxs-lookup"><span data-stu-id="276bf-144">Note that these topics and resources are not in any sequential order, so feel free to jump around and explore!</span></span>

### <a name="additional-resources"></a><span data-ttu-id="276bf-145">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="276bf-145">Additional resources</span></span>

<span data-ttu-id="276bf-146">OpenXR ゲームのレベルアップを検討している場合は、以下のリンクを確認してください。</span><span class="sxs-lookup"><span data-stu-id="276bf-146">If you're looking to level up your OpenXR game, check out the links below:</span></span>

* [<span data-ttu-id="276bf-147">OpenXR ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="276bf-147">OpenXR best practices</span></span>](openxr-best-practices.md)
* [<span data-ttu-id="276bf-148">OpenXR パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="276bf-148">OpenXR performance</span></span>](openxr-performance.md)
* [<span data-ttu-id="276bf-149">OpenXR トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="276bf-149">OpenXR troubleshooting</span></span>](openxr-troubleshooting.md)

## <a name="see-also"></a><span data-ttu-id="276bf-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="276bf-150">See also</span></span>
* [<span data-ttu-id="276bf-151">アプリ モデル</span><span class="sxs-lookup"><span data-stu-id="276bf-151">App model</span></span>](../../design/app-model.md)
* [<span data-ttu-id="276bf-152">アプリ ビュー</span><span class="sxs-lookup"><span data-stu-id="276bf-152">App views</span></span>](../../design/app-views.md)
