---
title: XAML とホログラフィック DirectX アプリの使用
description: DirectX アプリでの 2D XAML ビューとイマーシブビューの切り替えの影響と、XAML ビューとイマーシブビューの両方を効率的に使用する方法について説明します。
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: windows mixed reality, UWP, アプリビュー管理, xaml, キーボード, チュートリアル, DirectX
ms.openlocfilehash: 4908ffbded879709c848a4d767c35a150aa3dfba
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683377"
---
# <a name="using-xaml-with-holographic-directx-apps"></a><span data-ttu-id="f221a-104">XAML とホログラフィック DirectX アプリの使用</span><span class="sxs-lookup"><span data-stu-id="f221a-104">Using XAML with holographic DirectX apps</span></span>

> [!NOTE]
> <span data-ttu-id="f221a-105">この記事は、従来の WinRT ネイティブ Api に関連しています。</span><span class="sxs-lookup"><span data-stu-id="f221a-105">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="f221a-106">新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](../native/openxr-getting-started.md)** を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f221a-106">For new native app projects, we recommend using the **[OpenXR API](../native/openxr-getting-started.md)** .</span></span>

<span data-ttu-id="f221a-107">このトピックでは、DirectX アプリでの [2D XAML ビューとイマーシブビュー](../../design/app-views.md) の切り替えの影響と、xaml ビューとイマーシブビューの両方を効率的に使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f221a-107">This topic explains the impact of switching between [2D XAML views and immersive views](../../design/app-views.md) in your DirectX app, and how to make efficient use of both a XAML view and immersive view.</span></span>

## <a name="xaml-view-switching-overview"></a><span data-ttu-id="f221a-108">XAML ビューの切り替えの概要</span><span class="sxs-lookup"><span data-stu-id="f221a-108">XAML view switching overview</span></span>

<span data-ttu-id="f221a-109">HoloLens では、一般に 2D XAML ビューを表示できるイマーシブアプリでは、最初に XAML ビューを初期化し、そこからすぐにイマーシブビューに切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="f221a-109">On HoloLens, a generally immersive app that may later display a 2D XAML view must initialize that XAML view first and immediately switch to an immersive view from there.</span></span> <span data-ttu-id="f221a-110">これは、アプリが何かを実行する前に XAML が読み込まれることを意味します。</span><span class="sxs-lookup"><span data-stu-id="f221a-110">This means XAML will load before your app can do anything.</span></span> <span data-ttu-id="f221a-111">結果として、起動時間がわずかに増加し、XAML はバックグラウンドでアプリケーションプロセスのメモリ領域を占有し続けます。起動時の遅延とメモリの使用量は、ネイティブビューに切り替える前に、アプリが XAML で何を実行しているかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="f221a-111">As a result, there will be a small increase in your startup time, and XAML will continue to occupy memory space in your app process while it resides in the background; the amount of startup delay and memory usage depends on what your app does with XAML before switching to the native view.</span></span> <span data-ttu-id="f221a-112">XAML の最初のコードで何も実行しない場合は、まず、[イマーシブビューを開始] を除き、影響を軽微にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f221a-112">If you do nothing in your XAML start up code at first except start your immersive view, the impact should be minor.</span></span> <span data-ttu-id="f221a-113">また、holographic のレンダリングは、イマーシブビューに直接行われるため、そのレンダリングには XAML 関連の制限はありません。</span><span class="sxs-lookup"><span data-stu-id="f221a-113">Also, because your holographic rendering is done directly to the immersive view, you will avoid any XAML-related restrictions on that rendering.</span></span>

<span data-ttu-id="f221a-114">CPU と GPU の両方のメモリ使用量がカウントされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f221a-114">Note that the memory usage counts for both CPU and GPU.</span></span> <span data-ttu-id="f221a-115">Direct3D 11 は仮想グラフィックスメモリをスワップできますが、一部またはすべての XAML GPU リソースをスワップできない可能性があり、パフォーマンスが著しく低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f221a-115">Direct3D 11 is able to swap virtual graphics memory, but it might not be able to swap out some or all of the XAML GPU resources, and there might be a noticeable performance hit.</span></span> <span data-ttu-id="f221a-116">どちらの方法でも、不要な XAML 機能を読み込まないと、アプリのためのスペースが増え、エクスペリエンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="f221a-116">Either way, not loading any XAML features you don't need will leave more room for your app and provide a better experience.</span></span>

## <a name="xaml-view-switching-workflow"></a><span data-ttu-id="f221a-117">XAML ビューの切り替えワークフロー</span><span class="sxs-lookup"><span data-stu-id="f221a-117">XAML view switching workflow</span></span>

<span data-ttu-id="f221a-118">XAML からイマーシブモードに直接移動するアプリのワークフローは、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f221a-118">The workflow for an app that goes directly from XAML to immersive mode is like so:</span></span>
* <span data-ttu-id="f221a-119">アプリが 2D XAML ビューで開始されます。</span><span class="sxs-lookup"><span data-stu-id="f221a-119">The app starts up in the 2D XAML view.</span></span>
* <span data-ttu-id="f221a-120">アプリの XAML スタートアップシーケンスは、現在のシステムが holographic のレンダリングをサポートしているかどうかを検出します。</span><span class="sxs-lookup"><span data-stu-id="f221a-120">The app’s XAML startup sequence detects if the current system supports holographic rendering:</span></span>
* <span data-ttu-id="f221a-121">その場合は、アプリによってイマーシブビューが作成され、すぐに前面に移動します。</span><span class="sxs-lookup"><span data-stu-id="f221a-121">If so, the app creates the immersive view and brings it to the foreground right away.</span></span> <span data-ttu-id="f221a-122">Xaml の読み込みは、XAML ビューでのレンダリングクラスや資産の読み込みなど、Windows Mixed Reality デバイスでは不要なものに対してスキップされます。</span><span class="sxs-lookup"><span data-stu-id="f221a-122">XAML loading is skipped for anything not necessary on Windows Mixed Reality devices, including any rendering classes and asset loading in the XAML view.</span></span> <span data-ttu-id="f221a-123">アプリでキーボード入力に XAML が使用されている場合でも、その入力ページは作成されます。</span><span class="sxs-lookup"><span data-stu-id="f221a-123">If the app is using XAML for keyboard input, that input page should still be created.</span></span>
* <span data-ttu-id="f221a-124">それ以外の場合、XAML ビューは通常どおりビジネスで続行できます。</span><span class="sxs-lookup"><span data-stu-id="f221a-124">If not, the XAML view can proceed with business as usual.</span></span>

## <a name="tip-for-rendering-graphics-across-both-views"></a><span data-ttu-id="f221a-125">両方のビューでグラフィックスをレンダリングするためのヒント</span><span class="sxs-lookup"><span data-stu-id="f221a-125">Tip for rendering graphics across both views</span></span>

<span data-ttu-id="f221a-126">Windows Mixed Reality の XAML ビューに対して、DirectX で一定量のレンダリングを実装する必要がある場合、最良の方法は、両方のビューを使用できるレンダラーを1つ作成することです。</span><span class="sxs-lookup"><span data-stu-id="f221a-126">If your app needs to implement some amount of rendering in DirectX for the XAML view in Windows Mixed Reality, your best bet is to create one renderer that can work with both views.</span></span> <span data-ttu-id="f221a-127">レンダラーは、両方のビューからアクセスできる1つのインスタンスである必要があり、2D と holographic のレンダリングを切り替えることができる必要があります。</span><span class="sxs-lookup"><span data-stu-id="f221a-127">The renderer should be one instance that can be accessed from both views, and it should be able to switch between 2D and holographic rendering.</span></span> <span data-ttu-id="f221a-128">これにより、GPU 資産は一度だけ読み込まれます。これにより、読み込み時間、メモリの影響、およびビューを切り替えるときにスワップされるリソースの量が減少します。</span><span class="sxs-lookup"><span data-stu-id="f221a-128">That way GPU assets are only loaded once - this reduces load times, memory impact, and the amount of resources to be swapped when switching views.</span></span>
