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
# <a name="periodic-table-of-the-elements"></a>要素の定期的なテーブル

>[!NOTE]
>この記事では、 [Mixed Reality 設計ラボ](https://github.com/Microsoft/MRDesignLabs_Unity)で作成した探索的サンプルについて説明します。これは、学習の概要と、mixed reality アプリの開発に関する提案を共有する場所です。 設計関連の記事とコードは、新しい検出を行うと進化します。

[要素の定期テーブル](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) は、Microsoft の混合現実設計ラボのオープンソースのサンプルアプリです。 このプロジェクトでは、 **[オブジェクトコレクション](../../design/object-collection.md)** を使用して、さまざまな種類の種類の3d 空間にオブジェクトの配列をレイアウトする方法を学習できます。 また、HoloLens から標準入力に応答する対話型オブジェクトを作成する方法についても説明します。 このプロジェクトのコンポーネントを使用して、独自の mixed reality アプリエクスペリエンスを作成することができます。

![Elements アプリの期間テーブル](images/640px-periodictable-hero.jpg)

## <a name="about-the-app"></a>アプリについて

要素の周期テーブルは、3D 空間の化学要素と各プロパティを視覚化します。 これには、宝石やエアタップなどの HoloLens の基本的なやり取りが組み込まれています。 ユーザーは、アニメーション化された3D モデルを使用して要素について学習できます。 要素の電子シェルとその中核を視覚的に理解できます。これは、protons と neutrons で構成されています。

## <a name="background"></a>バックグラウンド

初めて HoloLens を使用した後、定期的なテーブルアプリは、mixed reality で試してみたいと思っていました。 各要素には、テキストと共に表示されるデータポイントが多数あるため、3D 空間でのタイポグラフィの合成を調べるのには大きな問題があると考えました。 このプロジェクトでは、要素の電子モデルを視覚化できることがもう1つの興味深い部分でした。

## <a name="design"></a>デザイン

周期テーブルの既定のビューについては、各要素の電子モデルを含む3次元のボックスを想定しています。 各ボックスの表面は半透明になるため、ユーザーは要素のボリュームを大まかに把握することができます。 ユーザーは、宝石とエアタップを使用して、各要素の詳細ビューを開くことができます。 テーブルビューと詳細ビューの間の切り替えを円滑かつ自然に行うために、実際に開いているボックスの物理的な相互作用と同様にしました。

![スケッチのデザイン](images/640px-sketch20170406.jpg)<br>
*スケッチのデザイン*

詳細ビューでは、美しくに表示されるテキストを使用して、各要素の情報を3D 空間に視覚化する必要がありました。 アニメーション化された3D 電子モデルは中心領域に表示され、さまざまな角度から表示できます。

![相互作用](images/640px-periodictable-interaction.jpg)

![宣言](images/640px-periodictable-prototypes.jpg)<br>
*相互作用プロトタイプ*

ユーザーは、テーブルの下部にあるボタンをエアタップすることで、画面の種類を変更できます。平面、円柱、球体、および散布を切り替えることができます。

## <a name="common-controls-and-patterns-used-in-this-app"></a>このアプリで使用される一般的なコントロールとパターン

### <a name="interactable-object-button"></a>対話型オブジェクト (ボタン)

[対話型オブジェクト](../../design/interactable-object.md) は、基本的な HoloLens 入力に応答できるオブジェクトです。 これは、任意のオブジェクトに簡単に適用できる事前 fab/スクリプトとして提供されています。 たとえば、シーンの対話型にコーヒーカップを作成し、宝石、エアタップ、ナビゲーション、操作ジェスチャなどの入力に応答することができます。 [詳細情報](../../design/interactable-object.md)

![nteractable オブジェクト](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>オブジェクト コレクション

[オブジェクトコレクション](../../design/object-collection.md) は、さまざまな図形で複数のオブジェクトをレイアウトするのに役立つオブジェクトです。 平面、円柱、球、および散布図がサポートされています。 Radius、行の数、間隔などの追加のプロパティを構成できます。 [詳細情報](../../design/object-collection.md)

![オブジェクト コレクション](images/640px-periodictable-collections.jpg)

### <a name="fitbox"></a>[Fitbox]

既定では、ホログラムは、アプリケーションが起動された時点でユーザーが使用している場所に配置されます。 これは、たとえば、ホログラムが壁の内側またはテーブルの中央に配置されているなど、望ましくない結果につながることがあります。 [Fitbox] を使用すると、ユーザーは、宝石を使用して、ホログラムが配置される場所を決定できます。 これは、独自のイメージまたは3D オブジェクトを使用して簡単にカスタマイズできる単純な PNG イメージテクスチャを使用して作成されます。

![[Fitbox]](../../design/images/450px-periodictable-fitbox.jpg)

## <a name="technical-details"></a>技術的な詳細

[Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)では、Elements アプリの周期テーブルのスクリプトと prefabs を見つけることができます。

## <a name="application-examples"></a>アプリケーションの例

ここでは、このプロジェクトのコンポーネントを利用して作成できるものについて、いくつかのアイデアを示します。

### <a name="stock-data-visualization-app"></a>株価データ可視化アプリ

Elements サンプルの定期テーブルと同じコントロールと相互作用モデルを使用して、株式市場データを視覚化するアプリを作成できます。 この例では、オブジェクトコレクションコントロールを使用して、球体図形にストックデータを配置します。 各在庫に関する追加情報が興味深い方法で表示されるような詳細ビューを想像することができます。

![アプリケーションの例: Finance (1/3)](images/640px-periodictable-applicationexamples-finance1.jpg)

![アプリケーションの例: Finance (2/3)](images/640px-periodictable-applicationexamples-finance2.jpg)

![アプリケーションの例: Finance (3/3)](images/640px-periodictable-applicationexamples-finance3.jpg)<br>
*Elements サンプルアプリの定期テーブルで使用されるオブジェクトコレクションを finance アプリで使用する方法の例*

### <a name="sports-app"></a>スポーツアプリ

ここでは、オブジェクトコレクションや、Elements サンプルアプリの定期テーブルのその他のコンポーネントを使用して、スポーツデータを視覚化する例を示します。

![アプリケーションの例: スポーツ (1/3)](images/640px-periodictable-applicationexamples-sports0.jpg)

![アプリケーションの例: スポーツ (2/3)](images/640px-periodictable-applicationexamples-sports1.jpg)

![アプリケーションの例: スポーツ (3/3)](images/640px-periodictable-applicationexamples-sports3.jpg)<br>
*要素の定期テーブルで使用されるオブジェクトコレクションをスポーツアプリで使用する方法の例*

## <a name="about-the-author"></a>著者について

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>駐車中</b><br>UX デザイナー @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>関連項目

* [対話可能なオブジェクト](../../design/interactable-object.md)
* [オブジェクト コレクション](../../design/object-collection.md)
