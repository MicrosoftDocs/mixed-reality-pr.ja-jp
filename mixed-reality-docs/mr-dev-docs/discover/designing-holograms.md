---
title: ホログラムのデザイン
description: Microsoft が新しく設計したホログラムアプリケーションを使用して、Mixed Reality について説明します。
author: hferrone
ms.author: daescu
ms.date: 11/24/2020
ms.topic: article
keywords: MRTK, Mixed Reality Toolkit, ホログラム, ホログラムの設計, 学習, サンプルアプリ, mixed reality ヘッドセット, 仮想現実のヘッドセット, 仮想現実とは
ms.openlocfilehash: bf904b319ed5b452f254b659315d9b531832a4d5
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002587"
---
# <a name="the-making-of-designing-holograms"></a>ホログラムの設計

> [!NOTE]
> 小さい読み込みウィンドウで、このページのすべてのクール Gif と埋め込みビデオを考慮するようにしてください。

混合現実向けに設計する方法については、特に、どのようにしてメディアがどのようになるかを理解することが難しい場合があります。 Microsoft では、HoloLens 2 用にダウンロードできる無料のアプリを作成しました。これは、じを使用して、mixed reality UX の設計の基礎を理解するのに役立ちます。 独自の魅力的ですばらしい HoloLens アプリを作成するのに役立つように、複数の現実の行動、ヒント、および推奨事項にダイブするために、ホログラムアプリを設計するための独自のアプローチを採用しています。 Microsoft Store からアプリを無料でダウンロードし、Microsoft の Mixed Reality 設計チームから学ぶことができるようになりました。

> [!div class="nextstepaction"]
> [デザインホログラムアプリをダウンロードする](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)

<br>

![デザインホログラムのデモ室にあるヘッド追跡シーンのアニメーション GIF](images/designing-holograms/demo-room.gif)

*ホログラムのデモ室 (人形家とも呼ばれます) の設計*

## <a name="designing-for-mixed-reality"></a>Mixed reality の設計

多くのユーザーと同じように、私はモバイルアプリの設計に使用しました。 2D デザイン環境では、すべてが現在世界中である空間コンピューティングについて詳しく解説してきましたが、大きなシフトでした。 Mixed reality では、アプリが2D 画面に限定されなくなりました。実際には、実世界に配置され、実際のオブジェクトとやり取りしています。

私にとっては、従来の2D デザインプロセスに3D エクスペリエンスを接続することは、mixed reality 開発の最も困難な側面です。 「お客様との会話」では、"どのような機能が含まれているか、およびそれらをどのように稼働させるかを知ることができます。 コードです。ドキュメントやチュートリアルに従うことはできますが、ユーザーエクスペリエンスは、 多くの機能、さまざまな入力オプション、さまざまなシナリオ、および物理的な環境では、非常に大きな問題になります。

![サンフランシスコの ](images/designing-holograms/workshop.jpeg)
 *hololens 2* 設計ワークショップによるサンフランシスコでの Hololens 2 設計ワークショップの画像

## <a name="an-opportunity-to-teach"></a>教える機会

最初は明らかではありませんでしたが、mixed reality を1つのメディアとして使用して説明するための優れた機会が提供されました。

ホログラムの設計は、mixed reality の設計概念と推奨事項について説明するビジュアルエクスペリエンスです。 自分と仮想教師が混合現実の設計概念をデモンストレーションしているだけです。 私たちは、お客様のスペースにしっかりと経験を持っています。

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Designing-Holograms-app-trailer/player]

*ホログラムトレーラービデオの設計*

## <a name="exploring-the-doll-house"></a>人形の家を調べる

人形ハウスは、アプリ全体で使用する仮想環境で、80 x 60 x 40 cm の小さな部屋で、ほとんどの部屋が共通している基本的な要素 (壁、ランプ、家具、テーブル、テレビなど) が含まれています。 人形ハウスはアプリエクスペリエンスの主要な主役であるため、どの環境でもうまく機能することを確認する必要があります。 これは、あらゆる種類の混合現実概念を視覚化するための小さなデモ室と考えてください。

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Dollhouse-adjustment-behavior-in-the-Designing-Holograms-app/player]
*Dollhouse 調整動作のビデオ*

### <a name="11-vs-110-prototypes"></a>1:1 対1:10 プロトタイプ

最初の前提として、1:1 のデモはすばらしい教師であると思います。 このユーザーには、教師が実際の有効期間に見ているものがすべて表示されます。 しかし、すぐに問題が発生することに気付きます。

- ほとんどの開発者は、オフィスで、またはデモ室より小さい部屋でアプリを実行します。
- 表示は加法です。つまり、仮想環境全体がユーザーの部屋に重なって表示されます。 2つのテーブルで混乱を招く可能性があります。おそらく、2つの couches と、アラインされていない壁面です。
- また、ビューのフィールドによって制約されているすべての仮想環境のうち、最悪のものがあります。

ミニ1:10 スケールを試したときに、結果は現実的な部屋を見てきました。このビューでは、あらゆる角度からすべてを同時に確認できます。 最も驚くべきことは、ほとんどのテスト担当者が、小規模なバージョンを確認するために多くのものを見つけた後、1:1 スケールに切り替えられないことです。 そのため、1:1 バージョンを実際に廃棄し、UI やアプリのその他の側面を調整するために必要な余分な作業を回避することにしました。

![1:1 スケールのフィールドと ](images/designing-holograms/1-1-scale.png)
 *1:1 scale の* ビューのフィールド

![1:10 スケールのフィールドと ](images/designing-holograms/1-10-scale.png)
 *1:10 scale の* ビューのフィールド

## <a name="using-mixed-reality-capture"></a>Mixed Reality キャプチャの使用

このアプリの最も重要な特徴の1つは、mixed reality のキャプチャを使用して、mixed reality の設計概念を学習し、デモンストレーションすることです。

Microsoft は、サンフランシスコに Mixed Reality Capture studio を持っています。 また、このテクノロジは他のスタジオにもライセンス供与されています。これには、ワシントン D.C. にあるアバターディメンション、ロサンゼルスのメタステージ、ロンドンのディメンションスタジオ、ソウルでの、および Volucap (ベルリン) が含まれます。 詳細については、 [こちら](https://www.microsoft.com/mixed-reality/capture-studios)を参照してください。

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Raw-capture-footage-for-the-Designing-Holograms-app/player]
*サンフランシスコの混合 Reality Capture Studio にある106カメラの1つからの Daniel Escudero の生の映像。*

キャプチャプロセスでは、keyframed メッシュ、法線、およびテクスチャが生成されます。これは、さらに実稼働後に OBJ/PNG ファイルとして提供されるか、または h.264 圧縮 MP4 ファイルとして再生できる状態になります。 これらのファイルは、Unity、Unreal、native、WebXR にインポートして、Windows、iOS、Mac、Android、マジック Leap、Playstation VR で実行できます。

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Mixed-Reality-Capture-footage-for-the-Designing-Holograms-app/player]
*オーディオと埋め込みメッシュを含むビデオを含む mp4 を分析するために用意されているキャプチャプレーヤー。*

## <a name="manipulating-captures-and-virtual-objects"></a>キャプチャと仮想オブジェクトの操作

Mixed Reality では、ユーザーまたは動物の仮想表現が生成されますが、他の仮想オブジェクトと対話するためにこれらの文字が必要になる場合があります。 次の2つの例は、この効果を実現するためにシーンを操作するさまざまな方法を示しています。

### <a name="head-gaze-adjustment"></a>ヘッドを見つめた調整

ヘッド見つめ調整を使用すると、キャプチャしたユーザーのヘッドを実行時に移動できます。つまり、ユーザーに対してキャプチャを行うことができます。 ここでは、ビューと目的のフィールドを表示するために使用しています。 次に示すのは、移動するためのターゲットとして機能する移動中のオブジェクトです。 ターゲットを左右に移動すると、キャプチャの先頭は次のようになります。

このトリックを使用して、人形ハウスのさまざまな部分に配置されているホログラムに対してアイドルキャプチャが常に直面していることを確認しています。 

![Unity のターゲットのオブジェクトに従って、実行時にキャプチャのヘッドを移動しています](images/designing-holograms/head-adjustment.gif)

*Unity のターゲットのオブジェクトに従って、実行時にキャプチャのヘッドを移動します。*

### <a name="syncing-animated-objects"></a>同期 (アニメーションオブジェクトを)

2つ目は、キャプチャの移動と同期するためにオブジェクトをアニメーション化していました。 アプリのさまざまな部分で、5フレームごとに特定のキャプチャのシーケンシャル Obj をインポートしました。 次に、Obj はシーンでアニメーション化され、キャプチャの対応するフレームと一致することが確認されます。 これは、アニメーション化と表示操作の面倒なプロセスですが、結果は優れています。これにより、キャプチャされていないオブジェクトと相互作用する Mixed Reality キャプチャが表示されるようになります。

![混合 Reality キャプチャと UI パネル間で同期されたアニメーション](images/designing-holograms/synced-objects.gif)

*混合 Reality キャプチャと UI パネル間で同期されたアニメーション*

### <a name="ui-creative-process"></a>UI クリエイティブプロセス

UI デザインの作成を開始したときに、情報の転送だけでなく、ホログラムによって提供される可能性のあるマジックと可能性を示すことも必要でした。 単純に、静的な2D ウィンドウとテキストボックスを表示するのは3D の世界には適しておらず、多くの可能性はありません。そのため、最初から、holographic の3D 空間を最大限に活用することにしました。

最初に、テキスト情報だけでなく、パネルとアイコンにもいくつかの太さを追加しました。 それでも、ユーザーとしては、テキストボックスが表示されます。 画像を含むテキストボックスが表示されません。 Mixed Reality Toolkit (MRTK) シェーダーを使用することによってさらに問題が発生しました。 MRTK シェーダーは強力なツールになりました。そのステンシル機能を使用しています。そのため、パネルに負の深度を追加すると、ポータルの効果として認識されることがあります。 つまり、テキストボックスの前に要素を追加するのではなく、透明なパネルの背後にアイコンが表示されるようになりました。 現在、ユーザーとして表示されているのは、実際にはレプリケートできないことです。これは、holographic マジックが発生し始めたところです。 また、実際にはお読みたくないユーザーとして、既に物理的な世界にいます。

明らかにアイコンは、単純なテキストよりもはるかに優れています。そのため、さらに強力なガイダンスを提供するために、一連のアニメーションオブジェクトとアバターの作成を開始し、それぞれのシナリオで何が行われているか、およびその使用方法についての小さなストーリーを示しています。

![対話型の holographic メニューシステムのアニメーション GIF](images/designing-holograms/creative-process.gif)

## <a name="core-concepts"></a>主要な概念

**ホログラフィック フレーム**

![Holographic フレームが強調表示されている dollhouse を囲むユーザーのアニメーション GIF](images/designing-holograms/FOVandFOI.gif)

**座標系**

![座標系が強調表示されている dollhouse を囲むユーザーのアニメーション GIF](images/designing-holograms/CoordinateSystems.gif)

**視線追跡**

![外観が強調表示されている固定のホログラムを見ているユーザーのアニメーション GIF](images/designing-holograms/EyeTracking.gif)

**ルームスキャンの視覚化と空間マッピング**

![マップされている dollhouse 内のすべてのサーフェイスのアニメーション GIF](images/designing-holograms/SpatialMapping.gif)

**シーンの理解**

![認識されている dollhouse 内のオブジェクトのアニメーション GIF](images/designing-holograms/SceneUnderstanding.gif)

**手書き線を使用したポイントアンドコミット**

![ハンドレイが強調表示されているユーザーのアニメーション GIF](images/designing-holograms/HandRays.gif)

## <a name="try-it-out-moments"></a>"試してみる"

ホログラムを設計すると、mixed reality の概念が説明されますが、ルームでも試してみることができます。 これらの説明の後に、人形の家を一時停止して、対話的な時間を取ります。 これらの対話型の瞬間の例をいくつか次に示します。

![ハンドが検出されたときと、ビューのフィールドに入るタイミングを示す、ハンドトラッキングフレームのアニメーション GIF](images/designing-holograms/try-out-1.gif)

*ハンドが検出されたときと、そのフィールドに表示されるタイミングを示すハンドトラッキングフレーム。*

![遠隔操作による競合の crystals と対話するアニメーション GIF](images/designing-holograms/try-out-2.gif)

*遠隔操作による衝突の crystals との対話*

![相互作用 affordances を調べるためのアニメーション GIF](images/designing-holograms/try-out-3.gif)

*Near 対話 affordances の探索*

## <a name="about-the-team"></a>チームについて

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Daniel Escudero" width="60" height="60" src="images/designing-holograms/daniel-escudero.jpeg"></td>
<td style="border-style: none"><b>Daniel Escudero</b><br><i>リーダーのテクニカルデザイナー</i><br>Dan は、ホログラムを設計するためのクリエイティブなディレクターであり、現在、サンフランシスコにおけるマイクロソフトの Mixed Reality Academy の設計リードとして機能しています。これは、以前はロンドンの Microsoft の Mixed Reality スタジオの1つであるデザイナーでした。</td>
</tr>
</table>

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60"><img alt="Picture of Martin Wettig" width="60" height="60" src="images/designing-holograms/martin-wettig.jpeg"></td>
<td style="border-style: none"><b>Martin Wettig</b><br><i>シニア3D アーティスト</i><br>Martin は、ホログラムの設計に関する3D アートと UI 設計をリードしています。これは、ベルリンの Microsoft の混合現実スタジオの1つであるシニア3D アーティストでした。</td>
</tr>
</table>

このプロジェクトの1つの手順でチームメートが重要なチームを持つことができるようになったので、多くの知識を共有し、 [オブジェクト理論](https://objecttheory.com/) のすばらしい人たちにとっては、複雑な現実の設計チームに感謝します。 情熱と特別な設計のために、すばらしい人材に感謝します。

> [!div class="nextstepaction"]
> [デザインホログラムアプリをダウンロードする](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)