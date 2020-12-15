---
title: XAML とホログラフィック DirectX アプリの使用
description: DirectX アプリでの 2D XAML ビューとイマーシブビューの切り替えの影響と、XAML ビューとイマーシブビューの両方を効率的に使用する方法について説明します。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: windows mixed reality, UWP, アプリビュー管理, xaml, キーボード, チュートリアル, DirectX
ms.openlocfilehash: b062efadca9ccfe2e2caeb054f662becc0807b50
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530275"
---
# <a name="using-xaml-with-holographic-directx-apps"></a><span data-ttu-id="b7a3c-104">XAML とホログラフィック DirectX アプリの使用</span><span class="sxs-lookup"><span data-stu-id="b7a3c-104">Using XAML with holographic DirectX apps</span></span>

> [!NOTE]
> <span data-ttu-id="b7a3c-105">この記事は、従来の WinRT ネイティブ Api に関連しています。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="b7a3c-106">新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](../native/openxr-getting-started.md)** を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)**.</span></span>

<span data-ttu-id="b7a3c-107">このトピックでは、DirectX アプリでの [2D XAML ビューとイマーシブビュー](../../design/app-views.md) の切り替えの影響と、xaml ビューとイマーシブビューの両方を効率的に使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-107">This topic explains the impact of switching between [2D XAML views and immersive views](../../design/app-views.md) in your DirectX app, and how to make efficient use of both a XAML view and immersive view.</span></span>

## <a name="xaml-view-switching-overview"></a><span data-ttu-id="b7a3c-108">XAML ビューの切り替えの概要</span><span class="sxs-lookup"><span data-stu-id="b7a3c-108">XAML view switching overview</span></span>

<span data-ttu-id="b7a3c-109">HoloLens では、後から 2D XAML ビューを表示できるイマーシブアプリでは、最初に XAML ビューを初期化し、そこからすぐにイマーシブビューに切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-109">On HoloLens, an immersive app that may later display a 2D XAML view needs to initialize that XAML view first and immediately switch to an immersive view from there.</span></span> <span data-ttu-id="b7a3c-110">アプリが何かを実行する前に XAML が読み込まれるため、起動時間がわずかに増加します。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-110">XAML will load before your app can do anything, which adds a small increase to your startup time.</span></span> <span data-ttu-id="b7a3c-111">XAML は、バックグラウンドのままで、アプリのプロセスのメモリ領域を占有し続けます。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-111">XAML will continue to occupy memory space in your app process while it stays in the background.</span></span> <span data-ttu-id="b7a3c-112">起動時の遅延とメモリの使用量は、ネイティブビューに切り替える前に、アプリが XAML で何を実行しているかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-112">The amount of startup delay and memory usage depends on what your app does with XAML before switching to the native view.</span></span> <span data-ttu-id="b7a3c-113">最初に XAML スタートアップコードで何もしない場合は、イマーシブビューを開始する以外に、影響は軽微である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-113">If you do nothing in your XAML startup code at first except start your immersive view, the impact should be minor.</span></span> <span data-ttu-id="b7a3c-114">また、holographic レンダリングはイマーシブビューに直接行われるため、そのレンダリングには XAML 関連の制限はありません。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-114">Also, because your holographic rendering is done directly to the immersive view, you'll avoid any XAML-related restrictions on that rendering.</span></span>

<span data-ttu-id="b7a3c-115">CPU と GPU の両方のメモリ使用量がカウントされます。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-115">The memory usage counts for both CPU and GPU.</span></span> <span data-ttu-id="b7a3c-116">Direct3D 11 では仮想グラフィックスメモリを交換できますが、一部またはすべての XAML GPU リソースをスワップすることはできず、パフォーマンスが著しく低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-116">Direct3D 11 can swap virtual graphics memory, but it might not be able to swap out some or all of the XAML GPU resources, and there might be a noticeable performance hit.</span></span> <span data-ttu-id="b7a3c-117">どちらの方法でも、不要な XAML 機能を読み込まないと、アプリのためのスペースが増え、エクスペリエンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-117">Either way, not loading any XAML features you don't need will leave more room for your app and provide a better experience.</span></span>

## <a name="xaml-view-switching-workflow"></a><span data-ttu-id="b7a3c-118">XAML ビューの切り替えワークフロー</span><span class="sxs-lookup"><span data-stu-id="b7a3c-118">XAML view switching workflow</span></span>

<span data-ttu-id="b7a3c-119">XAML からイマーシブモードに直接移動するアプリのワークフローは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-119">The workflow for an app that goes directly from XAML to immersive mode is like so:</span></span>
* <span data-ttu-id="b7a3c-120">アプリが 2D XAML ビューで開始されます。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-120">The app starts up in the 2D XAML view.</span></span>
* <span data-ttu-id="b7a3c-121">アプリの XAML スタートアップシーケンスは、現在のシステムが holographic のレンダリングをサポートしているかどうかを検出します。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-121">The app’s XAML startup sequence detects if the current system supports holographic rendering:</span></span>
* <span data-ttu-id="b7a3c-122">その場合は、アプリによってイマーシブビューが作成され、すぐに前面に移動します。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-122">If so, the app creates the immersive view and brings it to the foreground right away.</span></span> <span data-ttu-id="b7a3c-123">Xaml の読み込みは、XAML ビューでのレンダリングクラスや資産の読み込みなど、Windows Mixed Reality デバイスでは不要なものに対してスキップされます。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-123">XAML loading is skipped for anything not necessary on Windows Mixed Reality devices, including any rendering classes and asset loading in the XAML view.</span></span> <span data-ttu-id="b7a3c-124">アプリでキーボード入力に XAML が使用されている場合でも、その入力ページは作成されます。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-124">If the app is using XAML for keyboard input, that input page should still be created.</span></span>
* <span data-ttu-id="b7a3c-125">それ以外の場合、XAML ビューは通常どおりビジネスで続行できます。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-125">If not, the XAML view can continue with business as usual.</span></span>

## <a name="tip-for-rendering-graphics-across-both-views"></a><span data-ttu-id="b7a3c-126">両方のビューでグラフィックスをレンダリングするためのヒント</span><span class="sxs-lookup"><span data-stu-id="b7a3c-126">Tip for rendering graphics across both views</span></span>

<span data-ttu-id="b7a3c-127">Windows Mixed Reality の XAML ビューに対して、DirectX で一定量のレンダリングを実装する必要がある場合、最良の方法は、両方のビューを使用できるレンダラーを1つ作成することです。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-127">If your app needs to implement some amount of rendering in DirectX for the XAML view in Windows Mixed Reality, your best bet is to create one renderer that can work with both views.</span></span> <span data-ttu-id="b7a3c-128">レンダラーは、両方のビューからアクセスできる1つのインスタンスである必要があり、2D と holographic のレンダリングを切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-128">The renderer should be one instance that can be accessed from both views, and it should switch between 2D and holographic rendering.</span></span> <span data-ttu-id="b7a3c-129">これにより、GPU 資産は1回だけ読み込みます。これにより、読み込み時間、メモリの影響、およびビューの切り替え時にスワップされたリソースの量が減少します。</span><span class="sxs-lookup"><span data-stu-id="b7a3c-129">This way GPU assets only load once, which reduces load times, memory impact, and the amount of swapped resources when switching views.</span></span>
