---
title: タイポグラフィ
description: テキストは、アプリのエクスペリエンスに情報を提供するための重要な要素です。
author: cre8ivepark
ms.author: dongpark
ms.date: 06/03/2019
ms.topic: article
keywords: Windows Mixed Reality、デザイン、スタイル、フォント、タイポグラフィ、ui、ux
ms.openlocfilehash: 59c7796998ac01fcbb5c9dc418da6454c8c74d12
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685962"
---
# <a name="typography"></a>文字体裁

![HoloLens でのタイポグラフィの例](images/typography-cover.png)<br>


テキストは、アプリのエクスペリエンスに情報を提供するための重要な要素です。 2D 画面の文字体裁と同じように、明確で読みやすくすることを目指します。 Mixed Reality の 3 次元の側面により、テキストと全体的なユーザー エクスペリエンスをいっそう優れたものにする機会があります。

3D で型について話をするときは、押し出し、容量の3D テキストを考えてみる傾向があります。 一部ののロゴデザインやその他の限られたアプリケーションを除き、押し出しテキストはテキストの読みやすさを低下させる傾向があります。 3D のエクスペリエンスを設計する場合でも、読みやすく、読みやすくなるため、型に2D を使用します。

HoloLens では、加法色システムに基づいた光を使用したホログラムで型が構築されます。 他のホログラムと同じように、type を実際の環境に配置して、世界中でロックし、任意の角度から観察することができます。 型と環境の間の [視差](https://en.wikipedia.org/wiki/Parallax) 効果によっても、エクスペリエンスの深さが向上します。

## <a name="typography-in-mixed-reality"></a>Mixed reality でのタイポグラフィ

混合現実の表記規則は、他の場所とは異なります。 物理的な世界と仮想環境の両方のテキストは、読みやすく、読みやすいものである必要があります。 テキストは、壁上にあるか、物理オブジェクトに重ねて表示されます。 デジタルユーザーインターフェイスと共に使用することもできます。 文脈に関係なく、読み取りと認識に対して同じタイポグラフィルールを適用します。

### <a name="create-clear-hierarchy"></a>明確階層の作成

さまざまな種類のサイズと重みを使用して、コントラストと階層を作成します。 アプリのエクスペリエンス全体で型の傾斜を定義し、それに従うことで、一貫性のある情報階層で優れたユーザーエクスペリエンスを実現できます。

![型の傾斜の例](images/typography-ramp-1000px.jpg)<br>
*アプリケーションエクスペリエンス全体で、型の傾斜を定義し、それに従う*

### <a name="limit-your-fonts"></a>フォントを制限する

1つのコンテキストで2つ以上の異なるフォントファミリを使用することは避けてください。 これにより、お客様のエクスペリエンスのハーモニーと一貫性が損なわれ、情報を使用することが難しくなります。 HoloLens では、情報は物理環境の上に重なっているため、使用するフォントスタイルが多すぎるとエクスペリエンスが低下します。 Segoe UI は、すべての Microsoft デジタルデザインのフォントです。 Windows Mixed Reality シェルでは一貫して使用されます。 Segoe UI フォントファイルは、 [Windows design toolkit のページ](https://docs.microsoft.com/windows/uwp/design-downloads/)からダウンロードできます。

[Segoe UI タイプフェイスに関する詳細情報](https://docs.microsoft.com/windows/uwp/design/style/typography)

### <a name="avoid-thin-font-weights"></a>細いフォントの太さを避ける

細い垂直線はバイブレーションになり、読みにくくなるため、42 pt 未満の型サイズに対しては薄いまたは semilight のフォントの重みを使用しないようにします。 ストロークの太さが十分にある最新のフォントがうまく機能します。 たとえば、Helvetica, と Arial は、標準または太字の重みを使用して HoloLens で非常に読みやすくなっています。

### <a name="color"></a>Color

HoloLens では、ホログラムは加法の光源システムを使用して構築されるため、白のテキストは非常に読みやすくなります。 ホワイトテキストの例については、[スタート] メニューとアプリバーを参照してください。 HoloLens でバックプレートを使用しなくても白のテキストは適切に機能しますが、複雑な物理的背景によって型が読みづらくなる可能性があります。 ユーザーのフォーカスを改善し、物理的な背景からの邪魔を最小限に抑えるには、濃い色または色付きの背景色で白いテキストを使用することをお勧めします。

<br>


![ダークカラーまたは色付きの背景プレートでは、白いテキストを使用することをお勧めします。 ](images/typography-whiteonblack2-1000px.jpg)
*ダークカラーまたは色付きの背景プレートの白いテキストの例。*
<br>

ダークテキストを使用するには、明るい背景プレートを使用して読み取り可能にする必要があります。 加法色のシステムでは、黒は透明として表示されます。 これは、色付きの背景プレートを使用せずに黒のテキストを表示できないことを意味します。

:::row:::
    :::column:::
        ![黒のテキストの例](images/typography-whiteonblack.png)<br>
        *黒と黒の白いテキストの例*<br>
    :::column-end:::
    :::column:::
        ![黒のテキストの例](images/640px-typography-blackonwhite.jpg)<br>
        *システムアプリの黒いテキストの例-ストアと設定*<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="recommended-font-size"></a>推奨されるフォントサイズ

ご想像のとおり、PC またはタブレットデバイスで使用する種類のサイズ (通常は 12 ~ 32pt) は2メートルの距離で非常に小さくなります。 これは、各フォントの特性によって異なりますが、一般的には、ユーザー研究の研究に基づいて、推奨される最小の表示角度と、読みやすくするためのフォントの高さは、0.35 °-0.4 °/12.21-13.97mm にあります。 [Unity ページのテキスト](../develop/unity/text-in-unity.md)で導入されたスケールファクターを使用して、約 35 ~ 40pt です。 

0.45 m (45cm) でのほぼ相互作用の場合、フォントの表示角度と高さの最小値は0.4 °-0.5 °/3.14 – 3.9 mm です。 これは、 [Unity のテキスト](../develop/unity/text-in-unity.md)で導入されたスケールファクターを使用した12ポイントです。

![近距離および遠くの相互作用範囲 ](images/typography-distance-1000px.jpg)
 *のコンテンツとほぼの相互作用範囲*

### <a name="the-minimum-legible-font-size"></a>最小のフォントサイズの最小値
| 距離 | 表示角度 | テキストの高さ | フォントサイズ * * |
|---------|---------|---------|---------|
| 45cm (直接操作距離) | 0.4 °-0.5 ° | 3.14 ~ 3.9 mm | 8.9 – 11.13 pt |
| 2分 | 0.35 °-0.4 ° | 12.21 – 13.97 mm | 34.63-39.58 pt |


### <a name="the-comfortably-legible-font-size"></a>判読しやすいフォントサイズ
| 距離 | 表示角度 | テキストの高さ | フォントサイズ * * |
|---------|---------|---------|---------|
| 45cm (直接操作距離) | 0.65 °-0.8 ° | 5.1-6.3 mm | 14.47-17.8 pt |
| 2分 | 0.6 °-0.75 ° | 20.9-26.2 mm | 59.4-74.2 pt |


Segoe UI (Windows の既定のフォント) は、ほとんどの場合に適しています。 ただし、薄い垂直方向のストロークはバイブレーションので、読みやすさが低下するので、小さいサイズの明るいフォントや半明るいフォントファミリは使用しないようにしてください。 ストロークの太さが十分にある最新のフォントがうまく機能します。 たとえば、Helvetica, と Arial は、通常または太字の重みを使用して HoloLens で非常に読みやすくなります。

**Unity でのテキストサイズの計算の詳細については、「 [unity のテキスト](../develop/unity/text-in-unity.md)」を参照してください。**

![角度 ](images/Text_In_Unity_ViewingAngle.jpg)
 *表示距離、角度、およびテキストの高さ* を表示する

<br>

---

## <a name="resources"></a>リソース

:::row:::
    :::column:::
    ### <a name="segoe-fontsbr"></a>[Segoe フォント](https://download.microsoft.com/download/1/B/C/1BCF071A-78EE-4968-ACBE-15461C274B61/Segoe%20fonts%20v1705.zip)<br>
    (Zip ファイル)<br>
    ### <a name="hololens-fontbr"></a>[HoloLens フォント](https://download.microsoft.com/download/3/8/D/38D659E2-4B9C-413A-B2E7-1956181DC427/Hololens%20font.zip)<br>
    (Zip ファイル)<br>
    <br>
    *Image: HoloLens フォントは、Windows Mixed Reality で使用される記号のグリフを提供します。*
    :::column-end:::
        :::column:::
        ![HoloLens フォントは、Windows Mixed Reality で使用される記号のグリフを提供します。](images/hololensmdl2symbols.jpg)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="see-also"></a>関連項目
* [Unity のテキスト](../develop/unity/text-in-unity.md)
* [色、ライト、マテリアル](../color,-light-and-materials.md)
