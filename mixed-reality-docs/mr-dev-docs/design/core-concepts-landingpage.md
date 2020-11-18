---
title: Mixed reality コアの概念
description: エクスペリエンスを設計する前に、いくつかの主要な概念を理解しておくことをお勧めします。 以下の各トピックは、ユーザーに対して作成している mixed reality エクスペリエンスの品質に根本的に影響を与え、その品質に寄与する基礎となる要因です。
author: grbury
ms.author: grbury
ms.date: 10/02/2019
ms.topic: overview
keywords: Windows Mixed Reality、設計、アプリパターン、コントロール、スタイル、HoloLens、相互作用、UX 要素、ビヘイビアー、ビルディングブロック、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、快適、アプリモデル、座標、holographic frame
ms.openlocfilehash: 57d2632265c00fbb7232aaae79328f506f00f9d2
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702688"
---
# <a name="core-concepts-overview"></a><span data-ttu-id="1e18a-105">主要な概念の概要</span><span class="sxs-lookup"><span data-stu-id="1e18a-105">Core concepts overview</span></span>

![手で直接操作](images/05_CoreConcepts.png)


<span data-ttu-id="1e18a-107">エクスペリエンスを設計する前に、いくつかの主要な概念を理解しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1e18a-107">Before diving into the design your experience, it's helpful to understand a few core concepts.</span></span> <span data-ttu-id="1e18a-108">以下の各トピックは、ユーザーに対して作成している mixed reality エクスペリエンスの品質に根本的に影響を与え、その品質に寄与する基礎となる要因です。</span><span class="sxs-lookup"><span data-stu-id="1e18a-108">Each topic below is an underlying factor that fundamentally affects and contributes to the quality of the mixed reality experience you are creating for your user.</span></span> 

:::row:::
    :::column:::
        <span data-ttu-id="1e18a-109">[ ![ アプリモデル](images/teleportation-640px.png)](app-model.md) **[アプリモデル](app-model.md)**</span><span class="sxs-lookup"><span data-stu-id="1e18a-109">[![App model](images/teleportation-640px.png)](app-model.md) **[App model](app-model.md)**</span></span>
    :::column-end:::
    :::column:::
       <span data-ttu-id="1e18a-110">[ ![ 快適](images/comfort-chart.PNG)](comfort.md)に **[Comfort](comfort.md)**</span><span class="sxs-lookup"><span data-stu-id="1e18a-110">[![Comfort](images/comfort-chart.PNG)](comfort.md) **[Comfort](comfort.md)**</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1e18a-111">[ ![ 座標](images/coordinate-systems.PNG)](coordinate-systems.md)系の **[座標](coordinate-systems.md)系**</span><span class="sxs-lookup"><span data-stu-id="1e18a-111">[![Coordinate systems](images/coordinate-systems.PNG)](coordinate-systems.md) **[Coordinate systems](coordinate-systems.md)**</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="1e18a-112">[ ![ Holographic frame](images/destinationmars-750px.png)](holographic-frame.md) **[Holographic frame](holographic-frame.md)**</span><span class="sxs-lookup"><span data-stu-id="1e18a-112">[![Holographic frame](images/destinationmars-750px.png)](holographic-frame.md) **[Holographic frame](holographic-frame.md)**</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1e18a-113">[ ![ ルームスキャンの視覚化](images/sr-mixedworld-140429-8pm-00068-1000px.png)](room-scan-visualization.md) **[ルームスキャンの視覚化](room-scan-visualization.md)**</span><span class="sxs-lookup"><span data-stu-id="1e18a-113">[![Room scan visualization](images/sr-mixedworld-140429-8pm-00068-1000px.png)](room-scan-visualization.md) **[Room scan visualization](room-scan-visualization.md)**</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1e18a-114">シーン [について ![](images/scene-understanding.png)](scene-understanding.md)理解する **[Scene understanding](scene-understanding.md)**</span><span class="sxs-lookup"><span data-stu-id="1e18a-114">[![Scene understanding](images/scene-understanding.png)](scene-understanding.md) **[Scene understanding](scene-understanding.md)**</span></span>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        <span data-ttu-id="1e18a-115">[ ![ 空間アンカー](images/azurespatialanchors.jpg)](spatial-anchors.md) **[空間アンカー](spatial-anchors.md)**</span><span class="sxs-lookup"><span data-stu-id="1e18a-115">[![Spatial anchors](images/azurespatialanchors.jpg)](spatial-anchors.md) **[Spatial anchors](spatial-anchors.md)**</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1e18a-116">[ ![ 空間マッピング](images/surfacereconstruction.jpg)](spatial-mapping.md)の **[空間マッピング](spatial-mapping.md)**</span><span class="sxs-lookup"><span data-stu-id="1e18a-116">[![Spatial mapping](images/surfacereconstruction.jpg)](spatial-mapping.md) **[Spatial mapping](spatial-mapping.md)**</span></span>
    :::column-end:::
    :::column:::
        <span data-ttu-id="1e18a-117">Mixed reality アプリの [ ![ 種類混合 reality](images/enhancedenvironmentapps-640px.jpg)](types-of-mixed-reality-apps.md) **[アプリの](types-of-mixed-reality-apps.md)種類**</span><span class="sxs-lookup"><span data-stu-id="1e18a-117">[![Types of mixed reality apps](images/enhancedenvironmentapps-640px.jpg)](types-of-mixed-reality-apps.md) **[Types of mixed reality apps](types-of-mixed-reality-apps.md)**</span></span>
    :::column-end:::
:::row-end:::


<br>

<br>

