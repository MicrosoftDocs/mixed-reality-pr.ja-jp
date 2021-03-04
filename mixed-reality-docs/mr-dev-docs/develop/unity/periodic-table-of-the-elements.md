---
title: 要素の定期的なテーブル
description: オブジェクトコレクションと、Elements サンプルアプリの定期テーブルを使用して、さまざまな種類のサーフェスを含む3D 空間内のオブジェクトの配列をレイアウトする方法について説明します。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、設計、サンプルアプリ、コントロール、MRTK、Mixed Reality Toolkit、Unity、サンプルアプリ、アプリの例、オープンソース、Microsoft Store、HoloLens、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット
ms.openlocfilehash: 19307b310d104f418e4f7739b0576c63407d83fd
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759738"
---
# <a name="periodic-table-of-the-elements"></a>要素の定期的なテーブル

>[!NOTE]
>この記事では、 [Mixed Reality 設計ラボ](https://github.com/Microsoft/MRDesignLabs_Unity)で作成した探索的サンプルについて説明します。これは、学習の概要と、mixed reality アプリの開発に関する提案を共有する場所です。 設計関連の記事とコードは、新しい検出を行うと進化します。

[要素の定期テーブル](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable) は、Microsoft の混合現実設計ラボのオープンソースのサンプルアプリです。 **[オブジェクトコレクション](../../design/object-collection.md)** を使用して、さまざまな種類のサーフェスを含むオブジェクトの配列を3d 空間に配置する方法について説明します。 また、HoloLens から標準入力に応答する対話型オブジェクトを作成する方法についても説明します。 このプロジェクトのコンポーネントを使用して、独自の mixed reality アプリエクスペリエンスを作成することができます。

![Elements アプリの期間テーブル](images/640px-periodictable-hero.jpg)

## <a name="demo-video"></a>デモ ビデオ 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4IkCF]

Mixed Reality キャプチャを使用して HoloLens 2 で記録

## <a name="about-the-app"></a>アプリについて

要素の周期テーブルは、3D 空間の化学要素と各プロパティを視覚化します。 これには、宝石やエアタップなどの HoloLens の基本的なやり取りが組み込まれています。 ユーザーは、アニメーション化された3D モデルを使用して要素について学習できます。 要素の電子シェルとその中核を視覚的に理解できます。これは、protons と neutrons で構成されています。

## <a name="background"></a>バックグラウンド

初めて HoloLens を使用した経験があれば、mixed reality で定期的なテーブルアプリを試してみたいと思いました。 各要素には、テキストと共に表示されるデータポイントが多数あるため、3D 空間でのタイポグラフィの合成を調べるのには大きな問題があると考えました。 このプロジェクトの興味深い部分は、要素の電子的なモデルを視覚化する機会をユーザーに提供することです。

## <a name="design"></a>デザイン

周期テーブルの既定のビューについては、各要素の電子モデルを含む3次元のボックスを想定しています。 各ボックスの表面は半透明になるため、ユーザーは要素のボリュームを大まかに把握することができます。 ユーザーは、宝石とエアタップを使用して、各要素の詳細ビューを開くことができます。 テーブルビューと詳細ビューの間の切り替えを円滑かつ自然に行うために、実際に開いているボックスの物理的な相互作用と同様にしました。

![スケッチのデザイン](images/640px-sketch20170406.jpg)<br>
*スケッチのデザイン*

詳細ビューでは、美しくに表示されるテキストを使用して、各要素の情報を3D 空間に視覚化する必要がありました。 アニメーション化された3D 電子モデルは中心領域に表示され、さまざまな角度から表示できます。

![相互作用](images/640px-periodictable-interaction.jpg)

![宣言](images/640px-periodictable-prototypes.jpg)<br>
*相互作用プロトタイプ*

ユーザーは、テーブルの下部にあるボタンをエアタップすることで、画面の種類を変更できます。平面、円柱、球、および散布を切り替えることができます。

## <a name="common-controls-and-patterns-used-in-this-app"></a>このアプリで使用される一般的なコントロールとパターン

### <a name="interactable-object-button"></a>対話型オブジェクト (ボタン)

[対話型オブジェクト](../../design/interactable-object.md) は、基本的な HoloLens 入力に応答できるオブジェクトです。 これは、任意のオブジェクトに簡単に適用できる prefab/スクリプトとして提供されています。 たとえば、シーンの対話型にコーヒーカップを作成し、宝石、エアタップ、ナビゲーション、操作ジェスチャなどの入力に応答することができます。 [詳細情報](../../design/interactable-object.md)

![nteractable オブジェクト](images/640px-periodictable-interactableobject.jpg)

### <a name="object-collection"></a>オブジェクト コレクション

[オブジェクトコレクション](../../design/object-collection.md) はオブジェクトであり、さまざまな図形で複数のオブジェクトをレイアウトするのに役立ちます。 平面、円柱、球、散布図がサポートされています。 Radius、行の数、間隔などの追加のプロパティを構成できます。 [詳細情報](../../design/object-collection.md)

![オブジェクト コレクション](images/640px-periodictable-collections.jpg)

## <a name="technical-details"></a>技術的な詳細

[Mixed Reality Design Labs GitHub](https://github.com/Microsoft/MRDesignLabs_Unity_PeriodicTable)では、Elements アプリの周期テーブルのスクリプトと prefabs を見つけることができます。

## <a name="porting-story-for-hololens-2"></a>HoloLens 2 用の移植のストーリー

HoloLens 2 の instinctual 対話により、Elements アプリの周期テーブルがどのように更新されたかについてのストーリーをお読みください。

[元素周期表 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)




## <a name="about-the-author"></a>筆者について

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>UX デザイナー @Microsoft</td>
</tr>
</table>

## <a name="see-also"></a>関連項目

* [MRTK Examples Hub](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/example-scenes/example-hub.md) - [(Microsoft Store の HoloLens 2 からダウンロード)](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4)
* [Surfaces](sampleapp-surfaces.md) - [(Microsoft Store の HoloLens 2 からダウンロード)](https://www.microsoft.com/en-us/p/surfaces/9nvkpv3sk3x0)
* [元素周期表 2.0](https://medium.com/@dongyoonpark/bringing-the-periodic-table-of-the-elements-app-to-hololens-2-with-mrtk-v2-a6e3d8362158)
* [Galaxy Explorer 2.0](galaxy-explorer-update.md)