---
title: Surfaces
description: Surface サンプルアプリで、ビジュアル、オーディオ、および tactile sensations を使用して、視覚的、オーディオ、および指向の手追跡を含むを作成する方法について説明します。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality、設計、サンプルアプリ、コントロール、MRTK、Mixed Reality Toolkit、Unity、サンプルアプリ、アプリの例、オープンソース、Microsoft Store、HoloLens、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット
ms.openlocfilehash: bfb93574212dc9e6624d8baac636caf5c8df428a
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009312"
---
# <a name="surfaces"></a><span data-ttu-id="5817d-104">Surfaces</span><span class="sxs-lookup"><span data-stu-id="5817d-104">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="5817d-105">この記事では、 [Mixed Reality 設計ラボ](https://github.com/Microsoft/MRDesignLabs_Unity)で作成した探索的サンプルについて説明します。これは、学習の概要と、mixed reality アプリの開発に関する提案を共有する場所です。</span><span class="sxs-lookup"><span data-stu-id="5817d-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="5817d-106">設計関連の記事とコードは、新しい検出を行うと進化します。</span><span class="sxs-lookup"><span data-stu-id="5817d-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="5817d-107">Surface は、Microsoft の混合現実設計ラボのオープンソースのサンプル[アプリです。](https://github.com/microsoft/MRDL_Unity_Surfaces)</span><span class="sxs-lookup"><span data-stu-id="5817d-107">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="5817d-108">ここでは、ビジュアル、オーディオ、および完全に手を付けて tactile 人気を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="5817d-108">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Surfaces](images/MRDL_Surfaces_1.jpg)

## <a name="demo-video"></a><span data-ttu-id="5817d-110">デモ ビデオ</span><span class="sxs-lookup"><span data-stu-id="5817d-110">Demo video</span></span> 

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IhWQ]

<span data-ttu-id="5817d-111">Mixed Reality キャプチャを使用して HoloLens 2 で記録</span><span class="sxs-lookup"><span data-stu-id="5817d-111">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="5817d-112">アプリについて</span><span class="sxs-lookup"><span data-stu-id="5817d-112">About the app</span></span>

<span data-ttu-id="5817d-113">Surface は、Mixed Reality Toolkit (MRTK) の入力システムと構成要素を使用して、HoloLens 2 のアプリエクスペリエンスを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5817d-113">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="5817d-114">このプロジェクトでは、次の例を確認できます。</span><span class="sxs-lookup"><span data-stu-id="5817d-114">In this project, you can find the examples of:</span></span>
- <span data-ttu-id="5817d-115">MRTK の [入力システム](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)を使用します。具体的には、手動による追跡です。</span><span class="sxs-lookup"><span data-stu-id="5817d-115">Use MRTK's [Input System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="5817d-116">高性能グラフィックスには、MRTK の [標準シェーダー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) を使用します。</span><span class="sxs-lookup"><span data-stu-id="5817d-116">Use MRTK's [Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) for performant graphics.</span></span>

<span data-ttu-id="5817d-117">このプロジェクトのコンポーネントを使用して、独自の mixed reality アプリエクスペリエンスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="5817d-117">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="5817d-118">Mr Dev 日 2020-MR surface アプリからの学習</span><span class="sxs-lookup"><span data-stu-id="5817d-118">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>

[<span data-ttu-id="5817d-119">MR surface アプリからの学習</span><span class="sxs-lookup"><span data-stu-id="5817d-119">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="5817d-120">Lars-erik Simkins は、MRDL surface アプリの背後にあるシニアデザイナーで、アプリのデザインストーリーと技術的なハイライトについて話しています。</span><span class="sxs-lookup"><span data-stu-id="5817d-120">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="5817d-121">GitHub のプロジェクトリポジトリ</span><span class="sxs-lookup"><span data-stu-id="5817d-121">Project repository on GitHub</span></span>

[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="5817d-122">HoloLens 2 の Microsoft Store からアプリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="5817d-122">Download app from Microsoft Store in HoloLens 2</span></span>

https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="5817d-123">(アプリは HoloLens 2 でのみ利用可能)</span><span class="sxs-lookup"><span data-stu-id="5817d-123">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="5817d-124">筆者について</span><span class="sxs-lookup"><span data-stu-id="5817d-124">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="5817d-125"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="5817d-125"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="5817d-126">UX デザイナー @Microsoft</span><span class="sxs-lookup"><span data-stu-id="5817d-126">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="5817d-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="5817d-127">See also</span></span>

* <span data-ttu-id="5817d-128">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Microsoft Store の HoloLens 2 からダウンロード)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="5817d-128">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="5817d-129">[Surfaces](sampleapp-surfaces.md) - [(Microsoft Store の HoloLens 2 からダウンロード)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="5817d-129">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="5817d-130">元素周期表 2.0</span><span class="sxs-lookup"><span data-stu-id="5817d-130">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="5817d-131">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="5817d-131">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)
