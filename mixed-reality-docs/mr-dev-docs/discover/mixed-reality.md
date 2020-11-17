---
title: Mixed Reality とは
description: この記事では、Mixed Reality を定義し、Mixed Reality の範囲における AR および VR デバイスの位置付けを示します。
author: brandonbray
ms.author: branbray
ms.date: 08/26/2020
ms.topic: article
keywords: Mixed Reality, ホログラフィック, AR, VR, MR, XR, 拡張現実, 仮想現実, 説明
ms.localizationpriority: high
ms.openlocfilehash: a55b05f8edfeedfff3313844428b9af4cf7a2fc0
ms.sourcegitcommit: 9a489e8a3bf90b20f1b61606eea42c859c833424
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2020
ms.locfileid: "94340710"
---
# <a name="what-is-mixed-reality"></a>Mixed Reality とは

![HoloLens 2 での手を使ったポイントとコミット](images/02_MixedRealitySlashMixedReality.png)

Mixed Reality は、物理とデジタルの世界を融合し、人間、コンピューター、環境間の相互作用のリンクを解除します。 この新しい現実は、コンピューター ビジョン、グラフィカル処理能力、ディスプレイ テクノロジ、および入力システムの進歩が基盤となっています。 ただし、"*Mixed Reality*" という用語は、ポール・ミルグラムと岸野文郎による 1994 年の論文『[複合現実のビジュアル表示の分類](https://search.ieice.org/bin/summary.php?id=e77-d_12_1321)』で初めて紹介されました。 この論文では、"*仮想現実連続体*" の概念と、表示に適用される分類法のカテゴリについて考察しています。 それ以降、Mixed Reality の応用は表示の範囲を超え、以下が含まれるようになっています。
* 環境入力
* 立体音響
* 現実と仮想の両方の空間における場所と位置

![Mixed Reality の範囲の画像](images/mixedrealityspectrum-worlds.png)<br>
*図: Mixed Reality は物理的な世界とデジタル世界を融合したものです。*

<br>

---

## <a name="environmental-input-and-perception"></a>環境の入力と認識

過去数十年にわたって、人間とコンピューターの入力の関係についての研究が続いており、"*ヒューマン コンピューター インタラクション*" または HCI と呼ばれる分野につながっています。 人間入力は、キーボード、マウス、タッチ、インク、音声、さらには Kinect の骨格追跡など、さまざまな方法で行われます。

センサーと処理の進歩は、環境からのコンピューター入力の新しい領域を生み出しています。 コンピューターと環境の間の相互作用とは、実質的に、環境を理解または "*認識*" することです。そのため、環境情報を公開する Windows の API は、[認識 API シリーズ](https://docs.microsoft.com/uwp/api/Windows.Perception)と呼ばれています。 環境入力では、世界での人の位置 ([頭の追跡](../design/coordinate-systems.md))、表面と境界 ([空間マッピング](../design/spatial-mapping.md)や[シーンの理解](../design/scene-understanding.md))、環境光、環境音、オブジェクト認識、場所などがキャプチャされます。

<br>

![コンピューター、人間、環境間の相互作用を示すベン図](images/mixed-reality-venn-diagram-300px.png)<br> 
*図: コンピューター、人間、環境間の相互作用。*

<br>

**コンピューター処理、人間入力、環境入力** の 3 つすべてを組み合わせにより、真の Mixed Reality エクスペリエンスを作成するための準備が整います。 物理的な世界内の移動は、デジタル世界での動きに変換できます。 物理的な世界の境界は、デジタル環境でのゲーム プレイなどのアプリケーション エクスペリエンスに影響を与える可能性があります。 環境入力がないと、エクスペリエンスで物理とデジタルの現実を融合することはできません。<br>

<br>

---


## <a name="the-mixed-reality-spectrum"></a>Mixed Reality の範囲

Mixed Reality では物理とデジタルの両方の世界が融合されるため、これらの 2 つの現実によって、仮想現実連続体と呼ばれる範囲の両端が定義されます。 この現実の配列を "*Mixed Reality の範囲*" と呼んでいます。 左側には、人間が存在する物理的な現実があります。 右側には、対応するデジタル的な現実があります。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/_xpI0JosYUk" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<br>

### <a name="augmented-vs-virtual-reality"></a>拡張現実と仮想現実

現在市場にあるほとんどの携帯電話には、環境を理解する機能はほとんどありません。 これらによって提供されるエクスペリエンスでは、物理とデジタルの現実を融合することはできません。 物理的な世界のビデオ ストリームにグラフィックを重ね合わせるエクスペリエンスは、"*拡張現実*" です。 人の視野を遮ってデジタル エクスペリエンスを提供するエクスペリエンスは、"*仮想現実*" です。 拡張現実と仮想現実の間で可能になるエクスペリエンスにより、"*Mixed Reality*" が形成されます。
* 物理的な世界から始まって、ホログラムなどのデジタル オブジェクトが、そこに存在しているかのように配置されます。
* 物理的な世界から始まって、別の人のデジタル表現 (アバター) を使用して、ノートを離れるときに立っていた場所が示されます。 つまり、異なる時点での非同期コラボレーションを表すエクスペリエンスです。
* デジタル世界から始まって、壁や家具など、物理的な世界の物理的な境界が、ユーザーが物理的なオブジェクトを回避できるように、エクスペリエンス内にデジタルで表示されます。


<br>

![Mixed Reality の範囲](images/mixedrealityspectrum.png)<br>
*図: Mixed Reality の範囲*

<br>

現在利用可能なほとんどの拡張現実および仮想現実の製品は、この範囲のごく一部を表しており、より大きな Mixed Reality の範囲のサブセットと見なされています。 Windows 10 は、範囲全体を念頭に置いて構築されており、人間、場所、物のデジタル表現を現実の世界と融合できます。


## <a name="devices-and-experiences"></a>デバイスとエクスペリエンス

Windows Mixed Reality のエクスペリエンスを提供するデバイスには、主に次の 2 種類があります。
1. **ホログラフィック デバイス** の特徴は、そこに存在しているかのように、デジタル コンテンツを現実の世界に配置できることです。
2. **イマーシブ デバイス** の特徴は、物理的な世界を隠し、デジタル エクスペリエンスで置き換えることによって、"存在感" を作成できることです。

<table>
<tr>
<th width="30%"> 特徴</th><th width="35%"> ホログラフィック デバイス</th><th width="35%"> イマーシブ デバイス</th>
</tr><tr>
<td><strong>デバイスの例</strong></td><td> Microsoft HoloLens<br><br> <img alt="Microsoft HoloLens 2 image" width="300" height="169" src="images/HoloLens2.jpg" /></td><td> Samsung HMD Odyssey+<br><br> <img alt="Samsung HMD Odyssey+ image" width="300" height="169" src="images/Samsung-HMD-Odyssey.jpg" /></td>
</tr><tr>
<td><strong>ディスプレイ</strong></td><td> シースルー ディスプレイ。 ユーザーはヘッドセットを装着している間も物理環境を見ることができます。</td><td> 非透過ディスプレイ。 ユーザーはヘッドセットを装着している間は物理環境を見ることができません。</td>
</tr><tr>
<td><strong>移動</strong></td><td> 回転と平行移動の両方で、6 自由度の完全な移動。</td><td> 回転と平行移動の両方で、6 自由度の完全な移動。</td>
</tr>
</table> 


> [!NOTE]
> デバイスが (USB ケーブルまたは Wi-Fi 経由で) 別の PC に接続されているか、自己完結型 (非接続) であるかは、デバイスがホログラフィックかイマーシブかを表しているわけではありません。 モビリティ向上機能によってエクスペリエンスは向上し、ホログラフィック デバイスとイマーシブ デバイスはどちらも接続式または非接続式にできます。

技術的な進歩によって、Mixed Reality エクスペリエンスは可能になりました。 現在、すべての範囲でエクスペリエンスを実行できるデバイスはありません。 Windows 10 では、デバイスの製造元と開発者の両方に共通の Mixed Reality プラットフォームを提供しています。 今日のデバイスでは Mixed Reality の範囲内の特定の範囲をサポートでき、新しいデバイスにより、その範囲は広がっています。 将来、ホログラフィック デバイスはよりイマーシブになり、イマーシブ デバイスはよりホログラフィックになります。

<br>

![Mixed Reality の範囲におけるデバイスの種類](images/Final_WhatIsMixedReality07.png)<br>
*図: Mixed Reality の範囲におけるデバイスの位置付け*

アプリケーションやゲームの開発者が作成しようとしているエクスペリエンスの種類を考えることをお勧めします。 エクスペリエンスは、通常、範囲の特定の点または部分を対象としています。 開発者は、対象とするデバイスの機能を考慮する必要があります。 たとえば、物理的な世界に依存するエクスペリエンスは、HoloLens で実行するのが最善です。
* **左に向かう (物理的な現実に近づく)。** ユーザーは、物理的な環境内に存在していて、その環境を離れたと信じさせられることはありません。
* **中央 (完全な Mixed Reality)。** これらのエクスペリエンスでは、現実世界とデジタル世界が融合されています。 映画『[ジュマンジ](https://en.wikipedia.org/wiki/Jumanji)』を見た人なら、物語が展開する家の物理的な構造と、ジャングルの環境がどのようにブレンドされていたかわかります。
* **右に向かう (デジタル的な現実に近づく)。** ユーザーは、デジタル環境を体験し、自分の周りの物理的な環境で起こっていることは認識しません。

## <a name="next-discovery-checkpoint"></a>次の探索チェックポイント

私たちが用意した[探索ツアー](get-started-with-mr.md)を進んでいる場合、あなたの現在地は Mixed Reality の基本の探索の中盤の段階です。 ここから、次の基本トピックに進むことができます。 

> [!div class="nextstepaction"]
> [ホログラムとは](hologram.md)

## <a name="see-also"></a>関連項目

* [ホログラムとは](hologram.md)
* [Mixed Reality の基本を理解する](get-started-with-mr.md#understand-the-basics)
* [作成とプロトタイプ作成を始める](../design/design.md)
* [ツールとアーキテクチャについて学習する](../develop/development.md)

