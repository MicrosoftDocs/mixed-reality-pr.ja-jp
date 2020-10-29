---
title: Surfaces
description: Surface は、Microsoft の混合現実設計ラボのオープンソースのサンプルアプリです。 ここでは、ビジュアル、オーディオ、および完全に手を付けて tactile 人気を作成する方法について説明します。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/18/2020
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、mrtk、design、sample app、controls
ms.openlocfilehash: ee410e16a578efa53a38da2fb6b6477e109ac101
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91690522"
---
# <a name="surfaces"></a><span data-ttu-id="e1c6b-105">Surfaces</span><span class="sxs-lookup"><span data-stu-id="e1c6b-105">Surfaces</span></span>

>[!NOTE]
><span data-ttu-id="e1c6b-106">この記事では、 [Mixed Reality 設計ラボ](https://github.com/Microsoft/MRDesignLabs_Unity)で作成した探索的サンプルについて説明します。これは、学習の概要と、mixed reality アプリの開発に関する提案を共有する場所です。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="e1c6b-107">設計関連の記事とコードは、新しい検出を行うと進化します。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="e1c6b-108">Surface は、Microsoft の混合現実設計ラボのオープンソースのサンプル[アプリです。](https://github.com/microsoft/MRDL_Unity_Surfaces)</span><span class="sxs-lookup"><span data-stu-id="e1c6b-108">[Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)  is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="e1c6b-109">ここでは、ビジュアル、オーディオ、および完全に手を付けて tactile 人気を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-109">It explores how we can create a tactile sensation with visual, audio, and fully articulated hand-tracking.</span></span>

![Surfaces](images/MRDL_Surfaces_1.jpg)

## <a name="about-the-app"></a><span data-ttu-id="e1c6b-111">アプリについて</span><span class="sxs-lookup"><span data-stu-id="e1c6b-111">About the app</span></span>
<span data-ttu-id="e1c6b-112">Surface は、Mixed Reality Toolkit (MRTK) の入力システムと構成要素を使用して、HoloLens 2 のアプリエクスペリエンスを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-112">Surfaces demonstrates how to use Mixed Reality Toolkit(MRTK)'s input system and building blocks to create an app experience for HoloLens 2.</span></span> <span data-ttu-id="e1c6b-113">このプロジェクトでは、次の例を確認できます。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-113">In this project, you can find the examples of:</span></span>
- <span data-ttu-id="e1c6b-114">MRTK の [入力システム](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)を使用します。具体的には、手動による追跡です。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-114">Use MRTK's [Input System](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html), specifically hand / joint tracking.</span></span>
- <span data-ttu-id="e1c6b-115">高性能グラフィックスには、MRTK の [標準シェーダー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) を使用します。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-115">Use MRTK's [Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html) for performant graphics.</span></span>

<span data-ttu-id="e1c6b-116">このプロジェクトのコンポーネントを使用して、独自の mixed reality アプリエクスペリエンスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-116">You can use this project's components to create your own mixed reality app experiences.</span></span>

## <a name="mr-dev-days-2020---learnings-from-the-mr-surfaces-app"></a><span data-ttu-id="e1c6b-117">Mr Dev 日 2020-MR surface アプリからの学習</span><span class="sxs-lookup"><span data-stu-id="e1c6b-117">MR Dev Days 2020 - Learnings from the MR Surfaces App</span></span>
[<span data-ttu-id="e1c6b-118">MR surface アプリからの学習</span><span class="sxs-lookup"><span data-stu-id="e1c6b-118">Learnings from the MR Surfaces App</span></span>](https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Learnings-from-the-MR-Surfaces-App)

<span data-ttu-id="e1c6b-119">Lars-erik Simkins は、MRDL surface アプリの背後にあるシニアデザイナーで、アプリのデザインストーリーと技術的なハイライトについて話しています。</span><span class="sxs-lookup"><span data-stu-id="e1c6b-119">Lars Simkins, Senior designer behind the MRDL Surfaces app talks about the app's design story and technical highlights.</span></span>

## <a name="project-repository-on-github"></a><span data-ttu-id="e1c6b-120">GitHub のプロジェクトリポジトリ</span><span class="sxs-lookup"><span data-stu-id="e1c6b-120">Project repository on GitHub</span></span>
[https://github.com/microsoft/MRDL_Unity_Surfaces](https://github.com/microsoft/MRDL_Unity_Surfaces)

## <a name="download-app-from-microsoft-store-in-hololens-2"></a><span data-ttu-id="e1c6b-121">HoloLens 2 の Microsoft Store からアプリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="e1c6b-121">Download app from Microsoft Store in HoloLens 2</span></span>
https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0#activetab=pivot:overviewtab

<span data-ttu-id="e1c6b-122">(アプリは HoloLens 2 でのみ利用可能)</span><span class="sxs-lookup"><span data-stu-id="e1c6b-122">(The app is only available on HoloLens 2)</span></span>

## <a name="about-the-author"></a><span data-ttu-id="e1c6b-123">著者について</span><span class="sxs-lookup"><span data-stu-id="e1c6b-123">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="e1c6b-124"><b>駐車中</b></span><span class="sxs-lookup"><span data-stu-id="e1c6b-124"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="e1c6b-125">UX デザイナー @Microsoft</span><span class="sxs-lookup"><span data-stu-id="e1c6b-125">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="e1c6b-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1c6b-126">See also</span></span>

* [<span data-ttu-id="e1c6b-127">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="e1c6b-127">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="e1c6b-128">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="e1c6b-128">Object collection</span></span>](../../design/object-collection.md)
