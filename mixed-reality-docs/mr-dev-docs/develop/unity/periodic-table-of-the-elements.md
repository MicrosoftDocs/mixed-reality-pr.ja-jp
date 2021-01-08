---
title: 要素の定期的なテーブル
description: オブジェクトコレクションと、Elements サンプルアプリの定期テーブルを使用して、さまざまな種類のサーフェスを含む3D 空間内のオブジェクトの配列をレイアウトする方法について説明します。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、サンプルアプリ、コントロール、MRTK、Mixed Reality Toolkit、Unity、サンプルアプリ、アプリの例、オープンソース、Microsoft Store、HoloLens、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット
ms.openlocfilehash: fd525b0d41efa15ff55097456fb6b06dd3d60c25
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009362"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="aa1c7-104">要素の定期的なテーブル</span><span class="sxs-lookup"><span data-stu-id="aa1c7-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="aa1c7-105">この記事では、 [Mixed Reality 設計ラボ](https://github.com/Microsoft/MRDesignLabs_Unity)で作成した探索的サンプルについて説明します。これは、学習の概要と、mixed reality アプリの開発に関する提案を共有する場所です。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="aa1c7-106">設計関連の記事とコードは、新しい検出を行うと進化します。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="aa1c7-107">[要素の定期テーブル](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) は、Microsoft の混合現実設計ラボのオープンソースのサンプルアプリです。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="aa1c7-108">**[オブジェクトコレクション](../../design/object-collection.md)** を使用して、さまざまな種類のサーフェスを含むオブジェクトの配列を3d 空間に配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-108">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="aa1c7-109">また、HoloLens から標準入力に応答する対話型オブジェクトを作成する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="aa1c7-110">このプロジェクトのコンポーネントを使用して、独自の mixed reality アプリエクスペリエンスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Elements アプリの期間テーブル](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="aa1c7-112">デモ ビデオ</span><span class="sxs-lookup"><span data-stu-id="aa1c7-112">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="aa1c7-113">Mixed Reality キャプチャを使用して HoloLens 2 で記録</span><span class="sxs-lookup"><span data-stu-id="aa1c7-113">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="aa1c7-114">アプリについて</span><span class="sxs-lookup"><span data-stu-id="aa1c7-114">About the app</span></span>

<span data-ttu-id="aa1c7-115">要素の周期テーブルは、3D 空間の化学要素と各プロパティを視覚化します。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-115">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="aa1c7-116">これには、宝石やエアタップなどの HoloLens の基本的なやり取りが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-116">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="aa1c7-117">ユーザーは、アニメーション化された3D モデルを使用して要素について学習できます。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-117">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="aa1c7-118">要素の電子シェルとその中核を視覚的に理解できます。これは、protons と neutrons で構成されています。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-118">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="aa1c7-119">背景</span><span class="sxs-lookup"><span data-stu-id="aa1c7-119">Background</span></span>

<span data-ttu-id="aa1c7-120">初めて HoloLens を使用した経験があれば、mixed reality で定期的なテーブルアプリを試してみたいと思いました。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-120">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="aa1c7-121">各要素には、テキストと共に表示されるデータポイントが多数あるため、3D 空間でのタイポグラフィの合成を調べるのには大きな問題があると考えました。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-121">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="aa1c7-122">このプロジェクトの興味深い部分は、要素の電子的なモデルを視覚化する機会をユーザーに提供することです。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-122">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="aa1c7-123">設計</span><span class="sxs-lookup"><span data-stu-id="aa1c7-123">Design</span></span>

<span data-ttu-id="aa1c7-124">周期テーブルの既定のビューについては、各要素の電子モデルを含む3次元のボックスを想定しています。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-124">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="aa1c7-125">各ボックスの表面は半透明になるため、ユーザーは要素のボリュームを大まかに把握することができます。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-125">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="aa1c7-126">ユーザーは、宝石とエアタップを使用して、各要素の詳細ビューを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-126">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="aa1c7-127">テーブルビューと詳細ビューの間の切り替えを円滑かつ自然に行うために、実際に開いているボックスの物理的な相互作用と同様にしました。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-127">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="aa1c7-128">![スケッチのデザイン](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="aa1c7-128">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="aa1c7-129">*スケッチのデザイン*</span><span class="sxs-lookup"><span data-stu-id="aa1c7-129">*Design sketches*</span></span>

<span data-ttu-id="aa1c7-130">詳細ビューでは、美しくに表示されるテキストを使用して、各要素の情報を3D 空間に視覚化する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-130">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="aa1c7-131">アニメーション化された3D 電子モデルは中心領域に表示され、さまざまな角度から表示できます。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-131">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![相互作用](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="aa1c7-133">![宣言](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="aa1c7-133">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="aa1c7-134">*相互作用プロトタイプ*</span><span class="sxs-lookup"><span data-stu-id="aa1c7-134">*Interaction prototypes*</span></span>

<span data-ttu-id="aa1c7-135">ユーザーは、テーブルの下部にあるボタンをエアタップすることで、画面の種類を変更できます。平面、円柱、球、および散布を切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-135">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="aa1c7-136">このアプリで使用される一般的なコントロールとパターン</span><span class="sxs-lookup"><span data-stu-id="aa1c7-136">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="aa1c7-137">対話型オブジェクト (ボタン)</span><span class="sxs-lookup"><span data-stu-id="aa1c7-137">Interactable object (button)</span></span>

<span data-ttu-id="aa1c7-138">[対話型オブジェクト](../../design/interactable-object.md) は、基本的な HoloLens 入力に応答できるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-138">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="aa1c7-139">これは、任意のオブジェクトに簡単に適用できる prefab/スクリプトとして提供されています。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-139">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="aa1c7-140">たとえば、シーンの対話型にコーヒーカップを作成し、宝石、エアタップ、ナビゲーション、操作ジェスチャなどの入力に応答することができます。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-140">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="aa1c7-141">詳細情報</span><span class="sxs-lookup"><span data-stu-id="aa1c7-141">Learn more</span></span>](../../design/interactable-object.md)

![nteractable オブジェクト](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="aa1c7-143">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="aa1c7-143">Object collection</span></span>

<span data-ttu-id="aa1c7-144">[オブジェクトコレクション](../../design/object-collection.md) はオブジェクトであり、さまざまな図形で複数のオブジェクトをレイアウトするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-144">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="aa1c7-145">平面、円柱、球、散布図がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-145">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="aa1c7-146">Radius、行の数、間隔などの追加のプロパティを構成できます。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-146">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="aa1c7-147">詳細情報</span><span class="sxs-lookup"><span data-stu-id="aa1c7-147">Learn more</span></span>](../../design/object-collection.md)

![オブジェクト コレクション](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="aa1c7-149">技術的な詳細</span><span class="sxs-lookup"><span data-stu-id="aa1c7-149">Technical details</span></span>

<span data-ttu-id="aa1c7-150">[Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)では、Elements アプリの周期テーブルのスクリプトと prefabs を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-150">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="aa1c7-151">HoloLens 2 用の移植のストーリー</span><span class="sxs-lookup"><span data-stu-id="aa1c7-151">Porting story for HoloLens 2</span></span>

<span data-ttu-id="aa1c7-152">HoloLens 2 の instinctual 対話により、Elements アプリの周期テーブルがどのように更新されたかについてのストーリーをお読みください。</span><span class="sxs-lookup"><span data-stu-id="aa1c7-152">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="aa1c7-153">元素周期表 2.0</span><span class="sxs-lookup"><span data-stu-id="aa1c7-153">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="aa1c7-154">筆者について</span><span class="sxs-lookup"><span data-stu-id="aa1c7-154">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="aa1c7-155"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="aa1c7-155"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="aa1c7-156">UX デザイナー @Microsoft</span><span class="sxs-lookup"><span data-stu-id="aa1c7-156">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="aa1c7-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa1c7-157">See also</span></span>

* <span data-ttu-id="aa1c7-158">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Microsoft Store の HoloLens 2 からダウンロード)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="aa1c7-158">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="aa1c7-159">[Surfaces](sampleapp-surfaces.md) - [(Microsoft Store の HoloLens 2 からダウンロード)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="aa1c7-159">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="aa1c7-160">元素周期表 2.0</span><span class="sxs-lookup"><span data-stu-id="aa1c7-160">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="aa1c7-161">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="aa1c7-161">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)