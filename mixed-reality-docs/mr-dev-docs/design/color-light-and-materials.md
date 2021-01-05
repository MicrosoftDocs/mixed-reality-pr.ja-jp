---
title: 色、ライト、素材
description: 混合現実のコンテンツをデザインするには、すべてのビジュアル資産の色、照明、素材を慎重に検討する必要があります。
author: mavitazk
ms.author: pinkb
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、カラー、ライト、マテリアル、Mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 5d99941f068e808ba14d97084ef840a66aded2a9
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848060"
---
# <a name="color-light-and-materials"></a>色、ライト、素材

![色、ライト、マテリアル](images/RemoteRendering.jpg)

混合現実のコンテンツを設計するには、すべての仮想資産の色、照明、マテリアルを慎重に検討する必要があります。 見た目を向上させるには、光と素材を使用してイマーシブ環境の雰囲気を設定することができます。また、機能的な目的で、わかりやすい色を使用して、近いアクションをユーザーに通知することもできます。 これらの各決定は、エクスペリエンスのターゲットデバイスの機会と制約に照らし合わせて検討する必要があります。

次に示すのは、イマーシブと holographic ヘッドセットの両方でのアセットのレンダリングに固有のガイドラインです。 これらの多くは、他の技術領域に密接に関連しており、関連する項目の一覧に [ついて](color-light-and-materials.md#see-also) は、この記事の最後にある「関連項目」セクションを参照してください。

## <a name="rendering-on-immersive-vs-holographic-devices"></a>イマーシブおよび holographic デバイスでのレンダリング

イマーシブヘッドセットでレンダリングされるコンテンツは、holographic ヘッドセットでレンダリングされるコンテンツと比較すると、視覚的に異なります。 イマーシブヘッドセットでは、通常、2D 画面の場合と同じようにコンテンツがレンダリングされますが、HoloLens のような holographic ヘッドセットは、カラーシーケンシャルで、「」を参照して、ホログラムをレンダリングします。

Holographic ヘッドセットで holographic エクスペリエンスをテストするには、常に時間がかかります。 コンテンツの外観は、holographic デバイス専用に構築されている場合でも、セカンダリモニター、スナップショット、および spectator ビューで見られるものとは異なります。 デバイスのエクスペリエンスについて説明し、ホログラムの照明をテストして、コンテンツがどのようにレンダリングされるかについて、すべての辺 (および上および下) から観察することを忘れないでください。 デバイスのさまざまな明るさの設定でテストしてください。 すべてのユーザーが想定されている既定値と、さまざまな照明条件のセットを共有することはほとんどありません。

## <a name="fundamentals-of-rendering-on-holographic-devices"></a>Holographic デバイスでのレンダリングの基礎

* Holographic のデバイスには追加の **ディスプレイがあり** ます。実際の世界から光に光を追加することによって、ホログラムが作成されます。白は明るいと表示され、黒は透明に見えます。

* **色の影響はユーザーの環境によって異なり** ます。ユーザーの部屋にはさまざまな照明条件があります。 わかりやすくするために、適切なコントラストレベルでコンテンツを作成します。

* **動的な照明を避ける** – holographic エクスペリエンスで一様に点灯するホログラムは最も効率的です。 高度な機能を使用すると、モバイルデバイスの機能を超える可能性があります。 動的ライティングが必要な場合は、 [Mixed Reality Toolkit の標準シェーダー](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_MRTKStandardShader.md)を使用することをお勧めします。 

## <a name="designing-with-color"></a>色を使用したデザイン

加法表示の性質により、holographic の表示では特定の色が異なる場合があります。 照明環境ではいくつかの色が表示されますが、他の色は少ないインパクトとして表示されます。 クール色は背景に recede 傾向があり、ウォームカラーは前景に移動します。 エクスペリエンスの色を調べる際には、次の要因を考慮してください。

* **明るい色** を表示する-白は明るく、控えめに使用する必要があります。 ほとんどの場合、R 235 G 235 B 235 に関する白い値を検討してください。 大きな明るい領域では、ユーザー不快感が発生する可能性があります。 UI ウィンドウの背景プレートでは、暗い色を使用することをお勧めします。

* **ダークカラーのレンダリング** -加法表示の性質により、暗い色は透明に見えます。 純色の黒のオブジェクトは、実際の世界とは異なるものとして表示されます。 下記の「アルファチャネル」を参照してください。 "Black" のように見えるようにするには、16、16、16などの非常に濃い灰色の RGB 値を試してみてください。

* **色の統一性** -通常、ホログラムは、背景の色の統一性を維持するために十分な明るい色で表示されます。 大きな領域が blotchy になる可能性があります。 明るい、純色の大きな領域は避けてください。

* 色 **域**-HoloLens は、概念的には Adobe RGB に似ています。 その結果、色によっては、デバイス内のさまざまな品質と表現が表示されることがあります。

* **ガンマ** -レンダリングされるイメージの明るさとコントラストは、イマーシブデバイスと holographic デバイスで異なります。 多くの場合、これらのデバイスの違いは、色や影の暗い領域を作成したり、明るくしたりするように見えます。

* **色の分離** -"色を分割した" または "カラー fringing" とも呼ばれ、ユーザーが目のオブジェクトを追跡するときに、最も一般的に色の分離が発生します。

## <a name="technical-considerations"></a>技術的な考慮事項

* **別名** -ホログラム、ギザギザ、"階段のよく検討" のように、ホログラムのジオメトリのエッジが実際の世界を満たしていることを認識します。 詳細が高いテクスチャを使用すると、この効果を aggravate ことができます。 テクスチャをマップし、フィルター処理を有効にする必要があります。 ホログラムの端をフェードさせるか、オブジェクトの周囲に黒いエッジ境界線を作成するテクスチャを追加することを検討してください。 可能であれば、thin geometry は避けてください。

* **アルファチャネル** -ホログラムをレンダリングしていないすべてのパーツに対して完全に透明にするには、アルファチャネルをクリアする必要があります。 アルファを未定義のままにすると、デバイスまたは Spectator ビューで画像やビデオを撮影するときに、視覚的な成果物が得られます。

* **テクスチャの補正** : ライトは holographic ディスプレイで追加されるため、強い色の広い領域を避けることをお勧めします。これは、多くの場合、意図した視覚効果を生み出すことがないためです。

## <a name="design-guidelines-for-holographic-display"></a>Holographic 表示の設計ガイドライン

![色とハンドオクルージョン](images/color_handocclusion.jpg)

Holographic 表示用にコンテンツをデザインする場合、最適なエクスペリエンスを実現するために必要ないくつかの要素があります。 ガイドラインと推奨事項については、「 [holographic のコンテンツのデザイン](designing-content-for-holographic-display.md) 」を参照してください。

## <a name="storytelling-with-light-and-color"></a>薄いと color を使用したストーリーテリング

色と色を使用すると、ユーザーの環境でのホログラムの表示がより自然になり、ユーザーのためのガイダンスやヘルプが提供されます。 Holographic エクスペリエンスについては、照明と色を調べる際に、次の要因を考慮してください。

:::row:::
    :::column:::
* **Vignetting** -マテリアルを暗くするための ' vignette ' 効果は、ビューのフィールドの中央にユーザーの注意を集中するのに役立ちます。 この効果により、ユーザーの見つめベクターから、ある程度の半径でホログラムのマテリアルが暗くなります。 これは、ユーザーが傾斜や glancing の角度からホログラムを表示する場合にも有効です。

* **強調** 描画: 色、明るさ、および光源を比較して、オブジェクトまたは相互作用のポイントに注目します。 ストーリーテリングの照明メソッドの詳細については、「 [ピクセル Cinematography-コンピューターグラフィックスの照明アプローチ](http://media.siggraph.org/education/cgsource/Archive/ConfereceCourses/S96/course30.pdf)」を参照してください。<br>
        <br>
        *Image: 色を使用してストーリーテリング要素の強調を表示します。ここでは、 [フラグメント](https://www.microsoft.com/p/fragments/9nblggh5ggm8)からのシーンに示します。*
    :::column-end:::
        :::column:::
        ![色を使用して、ストーリーテリング要素の強調を表示します。ここでは、フラグメントからのシーンに示します。](images/640px-fragments.jpg)<br>
    :::column-end:::
:::row-end:::

## <a name="materials"></a>素材

:::row:::
    :::column:::
マテリアルは、現実的なホログラムを作成するための重要な要素です。 適切な視覚的特性を提供することにより、物理環境に合わせて優れた holographic オブジェクトを作成できます。 さまざまな種類のユーザー入力のやり取りについて視覚的なフィードバックを提供するために、素材も重要です。  

[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity) には、視覚的なフィードバックに使用できるさまざまな視覚効果オプションを備えた Mrtk Standard シェーダーが用意されています。 たとえば、"近接光" プロパティを使用して、ユーザーの指がオブジェクトの表面に近づいたときに光源効果を与えることができます。 [Mrtk Standard Shader](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)の詳細情報
    :::column-end:::
        :::column:::
    *ビデオループ: 境界ボックス* 
     ![ との近接度に基づくビジュアルフィードバックの例手書きの視覚的フィードバック](images/HoloLens2_Proximity.gif)

    :::column-end:::
:::row-end:::
<br>

---

## <a name="see-also"></a>関連項目
* [ホログラフィック ディスプレイのコンテンツを設計する](designing-content-for-holographic-display.md)
* [色の分離](../develop/platform-capabilities-and-apis/hologram-stability.md#color-separation)
* [ホログラム](../discover/hologram.md)
* [Microsoft デザイン言語-色](https://www.microsoft.com/design/color)
* [ユニバーサル Windows プラットフォーム-色](https://docs.microsoft.com/windows/uwp/style/color)
