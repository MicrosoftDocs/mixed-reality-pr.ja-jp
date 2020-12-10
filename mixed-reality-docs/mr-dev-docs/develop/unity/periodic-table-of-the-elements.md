---
title: 要素の定期的なテーブル
description: 要素の定期テーブルは、Microsoft の混合現実設計ラボのオープンソースのサンプルアプリです。 オブジェクト コレクションを使用して、さまざまな表面の種類を持つ 3D 空間内のオブジェクトの配列をレイアウトする方法を説明します。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、サンプルアプリ、コントロール、MRTK、Mixed Reality Toolkit、Unity、サンプルアプリ、アプリの例、オープンソース、Microsoft Store、HoloLens、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット
ms.openlocfilehash: a4099c889fee886e63d3a8b773398a250621f26e
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010183"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="33855-105">要素の定期的なテーブル</span><span class="sxs-lookup"><span data-stu-id="33855-105">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="33855-106">この記事では、 [Mixed Reality 設計ラボ](https://github.com/Microsoft/MRDesignLabs_Unity)で作成した探索的サンプルについて説明します。これは、学習の概要と、mixed reality アプリの開発に関する提案を共有する場所です。</span><span class="sxs-lookup"><span data-stu-id="33855-106">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="33855-107">設計関連の記事とコードは、新しい検出を行うと進化します。</span><span class="sxs-lookup"><span data-stu-id="33855-107">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="33855-108">[要素の定期テーブル](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) は、Microsoft の混合現実設計ラボのオープンソースのサンプルアプリです。</span><span class="sxs-lookup"><span data-stu-id="33855-108">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is an open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="33855-109">**[オブジェクトコレクション](../../design/object-collection.md)** を使用して、さまざまな種類のサーフェスを含むオブジェクトの配列を3d 空間に配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="33855-109">Learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)**.</span></span> <span data-ttu-id="33855-110">また、HoloLens から標準入力に応答する対話型オブジェクトを作成する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="33855-110">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="33855-111">このプロジェクトのコンポーネントを使用して、独自の mixed reality アプリエクスペリエンスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="33855-111">You can use this project's components to create your own mixed reality app experience.</span></span>

![Elements アプリの期間テーブル](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a><span data-ttu-id="33855-113">デモ ビデオ</span><span class="sxs-lookup"><span data-stu-id="33855-113">Demo video</span></span> 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

<span data-ttu-id="33855-114">Mixed Reality キャプチャを使用して HoloLens 2 で記録</span><span class="sxs-lookup"><span data-stu-id="33855-114">Recorded with HoloLens 2 using Mixed Reality Capture</span></span>

## <a name="about-the-app"></a><span data-ttu-id="33855-115">アプリについて</span><span class="sxs-lookup"><span data-stu-id="33855-115">About the app</span></span>

<span data-ttu-id="33855-116">要素の周期テーブルは、3D 空間の化学要素と各プロパティを視覚化します。</span><span class="sxs-lookup"><span data-stu-id="33855-116">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="33855-117">これには、宝石やエアタップなどの HoloLens の基本的なやり取りが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="33855-117">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="33855-118">ユーザーは、アニメーション化された3D モデルを使用して要素について学習できます。</span><span class="sxs-lookup"><span data-stu-id="33855-118">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="33855-119">要素の電子シェルとその中核を視覚的に理解できます。これは、protons と neutrons で構成されています。</span><span class="sxs-lookup"><span data-stu-id="33855-119">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="33855-120">バックグラウンド</span><span class="sxs-lookup"><span data-stu-id="33855-120">Background</span></span>

<span data-ttu-id="33855-121">初めて HoloLens を使用した経験があれば、mixed reality で定期的なテーブルアプリを試してみたいと思いました。</span><span class="sxs-lookup"><span data-stu-id="33855-121">After I first experienced HoloLens, I knew I wanted to experiment with a periodic table app in mixed reality.</span></span> <span data-ttu-id="33855-122">各要素には、テキストと共に表示されるデータポイントが多数あるため、3D 空間でのタイポグラフィの合成を調べるのには大きな問題があると考えました。</span><span class="sxs-lookup"><span data-stu-id="33855-122">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="33855-123">このプロジェクトの興味深い部分は、要素の電子的なモデルを視覚化する機会をユーザーに提供することです。</span><span class="sxs-lookup"><span data-stu-id="33855-123">Giving users the chance to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="33855-124">デザイン</span><span class="sxs-lookup"><span data-stu-id="33855-124">Design</span></span>

<span data-ttu-id="33855-125">周期テーブルの既定のビューについては、各要素の電子モデルを含む3次元のボックスを想定しています。</span><span class="sxs-lookup"><span data-stu-id="33855-125">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="33855-126">各ボックスの表面は半透明になるため、ユーザーは要素のボリュームを大まかに把握することができます。</span><span class="sxs-lookup"><span data-stu-id="33855-126">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="33855-127">ユーザーは、宝石とエアタップを使用して、各要素の詳細ビューを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="33855-127">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="33855-128">テーブルビューと詳細ビューの間の切り替えを円滑かつ自然に行うために、実際に開いているボックスの物理的な相互作用と同様にしました。</span><span class="sxs-lookup"><span data-stu-id="33855-128">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="33855-129">![スケッチのデザイン](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="33855-129">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="33855-130">*スケッチのデザイン*</span><span class="sxs-lookup"><span data-stu-id="33855-130">*Design sketches*</span></span>

<span data-ttu-id="33855-131">詳細ビューでは、美しくに表示されるテキストを使用して、各要素の情報を3D 空間に視覚化する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="33855-131">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="33855-132">アニメーション化された3D 電子モデルは中心領域に表示され、さまざまな角度から表示できます。</span><span class="sxs-lookup"><span data-stu-id="33855-132">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![相互作用](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="33855-134">![宣言](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="33855-134">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="33855-135">*相互作用プロトタイプ*</span><span class="sxs-lookup"><span data-stu-id="33855-135">*Interaction prototypes*</span></span>

<span data-ttu-id="33855-136">ユーザーは、テーブルの下部にあるボタンをエアタップすることで、画面の種類を変更できます。平面、円柱、球、および散布を切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="33855-136">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere, and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="33855-137">このアプリで使用される一般的なコントロールとパターン</span><span class="sxs-lookup"><span data-stu-id="33855-137">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="33855-138">対話型オブジェクト (ボタン)</span><span class="sxs-lookup"><span data-stu-id="33855-138">Interactable object (button)</span></span>

<span data-ttu-id="33855-139">[対話型オブジェクト](../../design/interactable-object.md) は、基本的な HoloLens 入力に応答できるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="33855-139">[Interactable object](../../design/interactable-object.md) is an object, which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="33855-140">これは、任意のオブジェクトに簡単に適用できる prefab/スクリプトとして提供されています。</span><span class="sxs-lookup"><span data-stu-id="33855-140">It's provided as a prefab/script, which you can easily apply to any object.</span></span> <span data-ttu-id="33855-141">たとえば、シーンの対話型にコーヒーカップを作成し、宝石、エアタップ、ナビゲーション、操作ジェスチャなどの入力に応答することができます。</span><span class="sxs-lookup"><span data-stu-id="33855-141">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation, and manipulation gestures.</span></span> [<span data-ttu-id="33855-142">詳細情報</span><span class="sxs-lookup"><span data-stu-id="33855-142">Learn more</span></span>](../../design/interactable-object.md)

![nteractable オブジェクト](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="33855-144">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="33855-144">Object collection</span></span>

<span data-ttu-id="33855-145">[オブジェクトコレクション](../../design/object-collection.md) はオブジェクトであり、さまざまな図形で複数のオブジェクトをレイアウトするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="33855-145">[Object collection](../../design/object-collection.md) is an object, which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="33855-146">平面、円柱、球、散布図がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="33855-146">It supports plane, cylinder, sphere, and scatter.</span></span> <span data-ttu-id="33855-147">Radius、行の数、間隔などの追加のプロパティを構成できます。</span><span class="sxs-lookup"><span data-stu-id="33855-147">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="33855-148">詳細情報</span><span class="sxs-lookup"><span data-stu-id="33855-148">Learn more</span></span>](../../design/object-collection.md)

![オブジェクト コレクション](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a><span data-ttu-id="33855-150">技術的な詳細</span><span class="sxs-lookup"><span data-stu-id="33855-150">Technical details</span></span>

<span data-ttu-id="33855-151">[Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)では、Elements アプリの周期テーブルのスクリプトと prefabs を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="33855-151">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="porting-story-for-hololens-2"></a><span data-ttu-id="33855-152">HoloLens 2 用の移植のストーリー</span><span class="sxs-lookup"><span data-stu-id="33855-152">Porting story for HoloLens 2</span></span>

<span data-ttu-id="33855-153">HoloLens 2 の instinctual 対話により、Elements アプリの周期テーブルがどのように更新されたかについてのストーリーをお読みください。</span><span class="sxs-lookup"><span data-stu-id="33855-153">Read the story on how Periodic Table of the Elements app was updated with HoloLens 2's instinctual interactions.</span></span>

[<span data-ttu-id="33855-154">元素周期表 2.0</span><span class="sxs-lookup"><span data-stu-id="33855-154">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a><span data-ttu-id="33855-155">筆者について</span><span class="sxs-lookup"><span data-stu-id="33855-155">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="33855-156"><b>Dong Yoon Park</b></span><span class="sxs-lookup"><span data-stu-id="33855-156"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="33855-157">UX デザイナー @Microsoft</span><span class="sxs-lookup"><span data-stu-id="33855-157">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="33855-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="33855-158">See also</span></span>

* <span data-ttu-id="33855-159">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Microsoft Store の HoloLens 2 からダウンロード)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span><span class="sxs-lookup"><span data-stu-id="33855-159">[MRTK Examples Hub](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ExampleHub.html) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)</span></span>
* <span data-ttu-id="33855-160">[Surfaces](sampleapp-surfaces.md) - [(Microsoft Store の HoloLens 2 からダウンロード)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span><span class="sxs-lookup"><span data-stu-id="33855-160">[Surfaces](sampleapp-surfaces.md) - [(Download from Microsoft Store in HoloLens 2)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)</span></span>
* [<span data-ttu-id="33855-161">元素周期表 2.0</span><span class="sxs-lookup"><span data-stu-id="33855-161">Periodic Table of the Elements 2.0</span></span>](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [<span data-ttu-id="33855-162">Galaxy Explorer 2.0</span><span class="sxs-lookup"><span data-stu-id="33855-162">Galaxy Explorer 2.0</span></span>](galaxy-explorer-update.md)