---
title: 要素の定期的なテーブル
description: 要素の周期的な表は、Microsoft の混合現実設計ラボのオープンソースのサンプルアプリです。ここでは、オブジェクトコレクションを使用してさまざまな種類の3D 空間にオブジェクトの配列を配置する方法を学習できます。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、サンプルアプリ、コントロール
ms.openlocfilehash: 2f7120aaf92a6e3d7b6ace301aae7392b67fa00b
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91690167"
---
# <a name="periodic-table-of-the-elements"></a><span data-ttu-id="c9e7c-104">要素の定期的なテーブル</span><span class="sxs-lookup"><span data-stu-id="c9e7c-104">Periodic Table of the Elements</span></span>

>[!NOTE]
><span data-ttu-id="c9e7c-105">この記事では、 [Mixed Reality 設計ラボ](https://github.com/Microsoft/MRDesignLabs_Unity)で作成した探索的サンプルについて説明します。これは、学習の概要と、mixed reality アプリの開発に関する提案を共有する場所です。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-105">This article discusses an exploratory sample we’ve created in the [Mixed Reality Design Labs](https://github.com/Microsoft/MRDesignLabs_Unity), a place where we share our learnings about and suggestions for mixed reality app development.</span></span> <span data-ttu-id="c9e7c-106">設計関連の記事とコードは、新しい検出を行うと進化します。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-106">Our design-related articles and code will evolve as we make new discoveries.</span></span>

<span data-ttu-id="c9e7c-107">[要素の定期テーブル](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) は、Microsoft の混合現実設計ラボのオープンソースのサンプルアプリです。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-107">[Periodic Table of the Elements](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) is a open-source sample app from Microsoft's Mixed Reality Design Labs.</span></span> <span data-ttu-id="c9e7c-108">このプロジェクトでは、 **[オブジェクトコレクション](../../design/object-collection.md)** を使用して、さまざまな種類の種類の3d 空間にオブジェクトの配列をレイアウトする方法を学習できます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-108">With this project, you can learn how to lay out an array of objects in 3D space with various surface types using an **[Object collection](../../design/object-collection.md)** .</span></span> <span data-ttu-id="c9e7c-109">また、HoloLens から標準入力に応答する対話型オブジェクトを作成する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-109">Also learn how to create interactable objects that respond to standard inputs from HoloLens.</span></span> <span data-ttu-id="c9e7c-110">このプロジェクトのコンポーネントを使用して、独自の mixed reality アプリエクスペリエンスを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-110">You can use this project's components to create your own mixed reality app experience.</span></span>

![Elements アプリの期間テーブル](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a><span data-ttu-id="c9e7c-112">アプリについて</span><span class="sxs-lookup"><span data-stu-id="c9e7c-112">About the app</span></span>

<span data-ttu-id="c9e7c-113">要素の周期テーブルは、3D 空間の化学要素と各プロパティを視覚化します。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-113">Periodic Table of the Elements visualizes the chemical elements and each of their properties in a 3D space.</span></span> <span data-ttu-id="c9e7c-114">これには、宝石やエアタップなどの HoloLens の基本的なやり取りが組み込まれています。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-114">It incorporates the basic interactions of HoloLens such as gaze and air tap.</span></span> <span data-ttu-id="c9e7c-115">ユーザーは、アニメーション化された3D モデルを使用して要素について学習できます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-115">Users can learn about the elements with animated 3D models.</span></span> <span data-ttu-id="c9e7c-116">要素の電子シェルとその中核を視覚的に理解できます。これは、protons と neutrons で構成されています。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-116">They can visually understand an element's electron shell and its nucleus - which is composed of protons and neutrons.</span></span>

## <a name="background"></a><span data-ttu-id="c9e7c-117">バックグラウンド</span><span class="sxs-lookup"><span data-stu-id="c9e7c-117">Background</span></span>

<span data-ttu-id="c9e7c-118">初めて HoloLens を使用した後、定期的なテーブルアプリは、mixed reality で試してみたいと思っていました。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-118">After I first experienced HoloLens, a periodic table app was an idea I knew that I wanted to experiment with in mixed reality.</span></span> <span data-ttu-id="c9e7c-119">各要素には、テキストと共に表示されるデータポイントが多数あるため、3D 空間でのタイポグラフィの合成を調べるのには大きな問題があると考えました。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-119">Since each element has many data points that are displayed with text, I thought it would be great subject matter for exploring typographic composition in a 3D space.</span></span> <span data-ttu-id="c9e7c-120">このプロジェクトでは、要素の電子モデルを視覚化できることがもう1つの興味深い部分でした。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-120">Being able to visualize the element's electron model was another interesting part of this project.</span></span>

## <a name="design"></a><span data-ttu-id="c9e7c-121">デザイン</span><span class="sxs-lookup"><span data-stu-id="c9e7c-121">Design</span></span>

<span data-ttu-id="c9e7c-122">周期テーブルの既定のビューについては、各要素の電子モデルを含む3次元のボックスを想定しています。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-122">For the default view of the periodic table, I imagined three-dimensional boxes that would contain the electron model of each element.</span></span> <span data-ttu-id="c9e7c-123">各ボックスの表面は半透明になるため、ユーザーは要素のボリュームを大まかに把握することができます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-123">The surface of each box would be translucent so that the user could get a rough idea of the element's volume.</span></span> <span data-ttu-id="c9e7c-124">ユーザーは、宝石とエアタップを使用して、各要素の詳細ビューを開くことができます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-124">With gaze and air tap, the user could open up a detailed view of each element.</span></span> <span data-ttu-id="c9e7c-125">テーブルビューと詳細ビューの間の切り替えを円滑かつ自然に行うために、実際に開いているボックスの物理的な相互作用と同様にしました。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-125">To make the transition between table view and detail view smooth and natural, I made it similar to the physical interaction of a box opening in real life.</span></span>

<span data-ttu-id="c9e7c-126">![スケッチのデザイン](images/640px-sketch20170406.jpg)</span><span class="sxs-lookup"><span data-stu-id="c9e7c-126">![Design sketch](images/640px-sketch20170406.jpg)</span></span><br>
<span data-ttu-id="c9e7c-127">*スケッチのデザイン*</span><span class="sxs-lookup"><span data-stu-id="c9e7c-127">*Design sketches*</span></span>

<span data-ttu-id="c9e7c-128">詳細ビューでは、美しくに表示されるテキストを使用して、各要素の情報を3D 空間に視覚化する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-128">In detail view, I wanted to visualize the information of each element with beautifully rendered text in 3D space.</span></span> <span data-ttu-id="c9e7c-129">アニメーション化された3D 電子モデルは中心領域に表示され、さまざまな角度から表示できます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-129">The animated 3D electron model is displayed in the center area and can be viewed from different angles.</span></span>

![相互作用](images/640px-periodictable-interaction.jpg)

<span data-ttu-id="c9e7c-131">![宣言](images/640px-periodictable-prototypes.jpg)</span><span class="sxs-lookup"><span data-stu-id="c9e7c-131">![Prototypes](images/640px-periodictable-prototypes.jpg)</span></span><br>
<span data-ttu-id="c9e7c-132">*相互作用プロトタイプ*</span><span class="sxs-lookup"><span data-stu-id="c9e7c-132">*Interaction prototypes*</span></span>

<span data-ttu-id="c9e7c-133">ユーザーは、テーブルの下部にあるボタンをエアタップすることで、画面の種類を変更できます。平面、円柱、球体、および散布を切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-133">The user can change the surface type by air tapping the buttons on the bottom of the table - they can switch between plane, cylinder, sphere and scatter.</span></span>

## <a name="common-controls-and-patterns-used-in-this-app"></a><span data-ttu-id="c9e7c-134">このアプリで使用される一般的なコントロールとパターン</span><span class="sxs-lookup"><span data-stu-id="c9e7c-134">Common controls and patterns used in this app</span></span>

### <a name="interactable-object-button"></a><span data-ttu-id="c9e7c-135">対話型オブジェクト (ボタン)</span><span class="sxs-lookup"><span data-stu-id="c9e7c-135">Interactable object (button)</span></span>

<span data-ttu-id="c9e7c-136">[対話型オブジェクト](../../design/interactable-object.md) は、基本的な HoloLens 入力に応答できるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-136">[Interactable object](../../design/interactable-object.md) is an object which can respond to basic HoloLens inputs.</span></span> <span data-ttu-id="c9e7c-137">これは、任意のオブジェクトに簡単に適用できる事前 fab/スクリプトとして提供されています。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-137">It is provided as a prefab/script which you can easily apply to any object.</span></span> <span data-ttu-id="c9e7c-138">たとえば、シーンの対話型にコーヒーカップを作成し、宝石、エアタップ、ナビゲーション、操作ジェスチャなどの入力に応答することができます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-138">For example, you can make a coffee cup in your scene interactable and respond to inputs such as gaze, air tap, navigation and manipulation gestures.</span></span> [<span data-ttu-id="c9e7c-139">詳細情報</span><span class="sxs-lookup"><span data-stu-id="c9e7c-139">Learn more</span></span>](../../design/interactable-object.md)

![nteractable オブジェクト](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a><span data-ttu-id="c9e7c-141">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="c9e7c-141">Object collection</span></span>

<span data-ttu-id="c9e7c-142">[オブジェクトコレクション](../../design/object-collection.md) は、さまざまな図形で複数のオブジェクトをレイアウトするのに役立つオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-142">[Object collection](../../design/object-collection.md) is an object which helps you lay out multiple objects in various shapes.</span></span> <span data-ttu-id="c9e7c-143">平面、円柱、球、および散布図がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-143">It supports plane, cylinder, sphere and scatter.</span></span> <span data-ttu-id="c9e7c-144">Radius、行の数、間隔などの追加のプロパティを構成できます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-144">You can configure additional properties such as radius, number of rows and the spacing.</span></span> [<span data-ttu-id="c9e7c-145">詳細情報</span><span class="sxs-lookup"><span data-stu-id="c9e7c-145">Learn more</span></span>](../../design/object-collection.md)

![オブジェクト コレクション](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a><span data-ttu-id="c9e7c-147">[Fitbox]</span><span class="sxs-lookup"><span data-stu-id="c9e7c-147">Fitbox</span></span>

<span data-ttu-id="c9e7c-148">既定では、ホログラムは、アプリケーションが起動された時点でユーザーが使用している場所に配置されます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-148">By default, holograms will be placed in the location where the user is gazing at the moment the application is launched.</span></span> <span data-ttu-id="c9e7c-149">これは、たとえば、ホログラムが壁の内側またはテーブルの中央に配置されているなど、望ましくない結果につながることがあります。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-149">This sometimes leads to unwanted result such as holograms being placed behind a wall or in the middle of a table.</span></span> <span data-ttu-id="c9e7c-150">[Fitbox] を使用すると、ユーザーは、宝石を使用して、ホログラムが配置される場所を決定できます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-150">A fitbox allows a user to use gaze to determine the location where the hologram will be placed.</span></span> <span data-ttu-id="c9e7c-151">これは、独自のイメージまたは3D オブジェクトを使用して簡単にカスタマイズできる単純な PNG イメージテクスチャを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-151">It is made with a simple PNG image texture which can be easily customized with your own images or 3D objects.</span></span>

![[Fitbox]](../../design/images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a><span data-ttu-id="c9e7c-153">技術的な詳細</span><span class="sxs-lookup"><span data-stu-id="c9e7c-153">Technical details</span></span>

<span data-ttu-id="c9e7c-154">[Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)では、Elements アプリの周期テーブルのスクリプトと prefabs を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-154">You can find scripts and prefabs for the Periodic Table of the Elements app on the [Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable).</span></span>

## <a name="application-examples"></a><span data-ttu-id="c9e7c-155">アプリケーションの例</span><span class="sxs-lookup"><span data-stu-id="c9e7c-155">Application examples</span></span>

<span data-ttu-id="c9e7c-156">ここでは、このプロジェクトのコンポーネントを利用して作成できるものについて、いくつかのアイデアを示します。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-156">Here are some ideas for what you could create by leveraging the components in this project.</span></span>

### <a name="stock-data-visualization-app"></a><span data-ttu-id="c9e7c-157">株価データ可視化アプリ</span><span class="sxs-lookup"><span data-stu-id="c9e7c-157">Stock data visualization app</span></span>

<span data-ttu-id="c9e7c-158">Elements サンプルの定期テーブルと同じコントロールと相互作用モデルを使用して、株式市場データを視覚化するアプリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-158">Using the same controls and interaction model as the Periodic Table of the Elements sample, you could build an app which visualizes stock market data.</span></span> <span data-ttu-id="c9e7c-159">この例では、オブジェクトコレクションコントロールを使用して、球体図形にストックデータを配置します。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-159">This example uses the Object collection control to lay out stock data in a spherical shape.</span></span> <span data-ttu-id="c9e7c-160">各在庫に関する追加情報が興味深い方法で表示されるような詳細ビューを想像することができます。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-160">You can imagine a detail view where additional information about each stock could be displayed in an interesting way.</span></span>

![アプリケーションの例: Finance (1/3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![アプリケーションの例: Finance (2/3)](images/640px-periodictable-applicationexamples-finance2.jpg)

<span data-ttu-id="c9e7c-163">![アプリケーションの例: Finance (3/3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span><span class="sxs-lookup"><span data-stu-id="c9e7c-163">![Application example: Finance (3 of 3)](images/640px-periodictable-applicationexamples-finance3.jpg)</span></span><br>
<span data-ttu-id="c9e7c-164">*Elements サンプルアプリの定期テーブルで使用されるオブジェクトコレクションを finance アプリで使用する方法の例*</span><span class="sxs-lookup"><span data-stu-id="c9e7c-164">*An example of how the Object collection used in the Periodic Table of the Elements sample app could be used in a finance app*</span></span>

### <a name="sports-app"></a><span data-ttu-id="c9e7c-165">スポーツアプリ</span><span class="sxs-lookup"><span data-stu-id="c9e7c-165">Sports app</span></span>

<span data-ttu-id="c9e7c-166">ここでは、オブジェクトコレクションや、Elements サンプルアプリの定期テーブルのその他のコンポーネントを使用して、スポーツデータを視覚化する例を示します。</span><span class="sxs-lookup"><span data-stu-id="c9e7c-166">This is an example of visualizing sports data using Object collection and other components from the Periodic Table of the Elements sample app.</span></span>

![アプリケーションの例: スポーツ (1/3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![アプリケーションの例: スポーツ (2/3)](images/640px-periodictable-applicationexamples-sports1.jpg)

<span data-ttu-id="c9e7c-169">![アプリケーションの例: スポーツ (3/3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span><span class="sxs-lookup"><span data-stu-id="c9e7c-169">![Application example: Sports (3 of 3)](images/640px-periodictable-applicationexamples-sports3.jpg)</span></span><br>
<span data-ttu-id="c9e7c-170">*要素の定期テーブルで使用されるオブジェクトコレクションをスポーツアプリで使用する方法の例*</span><span class="sxs-lookup"><span data-stu-id="c9e7c-170">*An example of how the Object collection used in the Periodic Table of the Elements sample appcould be used in a sports app*</span></span>

## <a name="about-the-author"></a><span data-ttu-id="c9e7c-171">著者について</span><span class="sxs-lookup"><span data-stu-id="c9e7c-171">About the author</span></span>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><span data-ttu-id="c9e7c-172"><b>駐車中</b></span><span class="sxs-lookup"><span data-stu-id="c9e7c-172"><b>Dong Yoon Park</b></span></span><br><span data-ttu-id="c9e7c-173">UX デザイナー @Microsoft</span><span class="sxs-lookup"><span data-stu-id="c9e7c-173">UX Designer @Microsoft</span></span></td>
</tr>
</table>

## <a name="see-also"></a><span data-ttu-id="c9e7c-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9e7c-174">See also</span></span>

* [<span data-ttu-id="c9e7c-175">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="c9e7c-175">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="c9e7c-176">オブジェクト コレクション</span><span class="sxs-lookup"><span data-stu-id="c9e7c-176">Object collection</span></span>](../../design/object-collection.md)
