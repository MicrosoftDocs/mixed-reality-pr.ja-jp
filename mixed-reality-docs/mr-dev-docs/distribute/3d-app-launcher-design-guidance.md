---
title: 3D アプリ起動ツールの設計ガイダンス
description: 3D アプリランチャーは、アプリを起動するために選択できる、ユーザーの mixed reality ハウスの "物理" オブジェクトです。
author: thmignon
ms.author: thmignon
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, 設計, 3D アプリランチャー, イマーシブヘッドセット, ライブキューブ
ms.openlocfilehash: 884d05b8b8ef7e15f5c65a411cf500b0d4dc598c
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686554"
---
# <a name="3d-app-launcher-design-guidance"></a>3D アプリ起動ツールの設計ガイダンス

Windows Mixed Reality イマーシブ (VR) ヘッドセットを使用する場合は、山と水で囲まれた崖に家として視覚化された Windows Mixed Reality ホームを入力します (ただし、 [他の環境を選択して独自に作成](../design/add-custom-home-environments.md)することもできます)。 このホームの領域内では、ユーザーは、必要に応じて、必要な3D オブジェクトとアプリを自由に配置して整理することができます。 **3d アプリランチャー** は、アプリを起動するために選択できる、ユーザーの mixed reality ハウスの "物理" オブジェクトです。

![例: Floaty 鳥3D アプリランチャー](images/20171016-151526-mixedreality1-1200px-1000px.jpg)<br>
*Floaty 鳥3D アプリランチャーの例 (架空のアプリ)*

## <a name="3d-app-launcher-creation-process"></a>3D アプリランチャー作成プロセス

3D アプリランチャーを作成するには、次の3つの手順を実行します。

1. 設計と concepting (この記事)
2. [モデリングとエクスポート](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
3. アプリケーションに統合します。
    * [UWP アプリ](implementing-3d-app-launchers.md)
    * [Win32 アプリ](implementing-3d-app-launchers-win32.md)

## <a name="design-concepts"></a>設計概念

### <a name="fantastic-yet-familiar"></a>非常になじみのあるすばらしい

アプリランチャーが存在する Windows Mixed Reality 環境は、パート fantastical/sci です。 最適なランチャーは、この世界の規則に従います。 アプリから使い慣れた代表的なオブジェクトを取得しながら、実際の現実のルールの一部を曲げられる方法を考えてみましょう。 マジックが生成されます。

### <a name="intuitive"></a>にくい

アプリランチャーを確認するときは、アプリを起動する目的を明確にする必要があり、混乱を招くことはありません。 たとえば、décor が崖家の1つの部分と混同されないように、ランチャーが明らかであることを確認してください。 アプリランチャーは、ユーザーにタッチまたは選択を招待する必要があります。

![例: 新しいメモ3D アプリランチャー](images/20171016-152145-mixedreality1-1200px-1000px.jpg)<br>
*新鮮ノート3D アプリランチャーの例 (架空のアプリ)*

### <a name="home-scale"></a>ホームスケール

3D アプリランチャーは崖家に存在し、その既定のサイズは、空間内の他の "物理" オブジェクトと同じ意味になります。 家の植物や家具など、ランチャーを設置している場合は、自宅でも、サイズにも気が付いています。 開始点としては、どのように表示されるかを確認することをお勧めします。ただし、ユーザーが必要に応じてスケールアップまたはスケールダウンできることに注意してください。

### <a name="own-able"></a>独自の機能

アプリランチャーは、ユーザーが自分のスペースにあるように感じられるオブジェクトのように感じます。 これらの機能は実質的にこのような処理を行っているので、ランチャーは、ユーザーが近くにいると思っていたようなものと考える必要があります。

![例: Astro ワープ3D アプリランチャー](images/20171016-132936-mixedreality-1200px-1000px.jpg)<br>
*Astro ワープ3D アプリランチャーの例 (架空のアプリ)*

### <a name="recognizable"></a>認識可能な

3D アプリランチャーは、"アプリのブランド" を表示している人にすぐに表す必要があります。 アプリに星型の文字や特に識別可能なオブジェクトがある場合は、設計の大きな部分としてそれを使用することをお勧めします。 現実の世界では、オブジェクトはロゴだけでなくユーザーからも関心を引くことができます。 認識可能なオブジェクトは、ブランドを迅速かつ明確に伝えることができます。

### <a name="volumetric"></a>容量

お客様のアプリは、ロゴを平面に配置して1日に呼び出すだけではありません。 ランチャーは、ユーザーの領域において、魅力的で3D な物理オブジェクトのように感じます。 アプリの Macy の感謝祭のパレードにバルーンを設定することをお勧めします。 だれかが言っている人は、どこにいるかということです。 すべての表示角度からはどのようになりますか。

:::row:::
    :::column:::
        ![ロゴのみの ](images/20171016-140436-mixedreality-640px.jpg) *ロゴのみ*
    :::column-end:::
    :::column:::
        ![文字でよりわかりやすい ](images/20171016-140557-mixedreality-640px.jpg) *More recognizable with a character* 文字を使用する
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![純粋なアプローチでは、驚くべきことではありませんがフラットなフラットな ](images/20171016-155101-mixedreality-640px.jpg) *アプローチです* 。
    :::column-end:::
    :::column:::
        ![アプリ ](images/20171016-161407-mixedreality-640px.jpg) *の容量アプローチ* をより適切に紹介する容量アプローチ
    :::column-end:::
:::row-end:::

## <a name="tips-for-good-3d-models"></a>優れた3D モデルのヒント

* アプリランチャーのディメンションを計画するときは、約30cm のキューブに対して撮影します。 そのため、1:1:1 のサイズ比率です。
* モデルは1万ポリゴン以下である必要があります。 [トライアングルの数と詳細レベルの詳細については、LODs を参照してください。](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#triangle-counts-and-levels-of-detail-lods)
* イマーシブヘッドセットでテストします。
* 可能な限りモデルのジオメトリに詳細をビルドします。詳細については、テクスチャに依存しないでください。
* "水のきつい" 閉じたジオメトリを構築します。 でモデル化されていない穴はありません。
* オブジェクトで自然な素材を使用します。 現実の世界に構築することを想像してください。
* モデルの距離とサイズが異なることを確認します。
* モデルの準備ができたら、「資産の [エクスポートに関するガイドライン](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#asset-requirements-overview)」を参照してください。

![テクスチャの微妙な詳細情報を含むモデル](images/20171013-143334-mixedreality-640px.jpg)<br>
*テクスチャの微妙な詳細情報を含むモデル*

### <a name="what-to-avoid"></a>避けるべきこと

* ハイコントラストの詳細や、小さな、ビジーのパターン、テクスチャは使用しないでください。
* シンジオメトリは使用しないでください。距離が適切ではなく、別名が正しくありません。
* モデルの一部が1:1:1 のサイズ比を超えて拡張されないようにしてください。 スケーリングの問題が発生します。

![ハイコントラストの小さなビジーパターンを避ける](images/20171013-143603-mixedreality-640px.jpg)<br>
*ハイコントラスト、小さい、ビジーパターンを避ける*

## <a name="how-to-handle-type"></a>型を処理する方法

* 種類は、アプリランチャーの約 1/3 (またはそれ以上) で構成することをお勧めします。 Type は、ランチャーが実際にランチャーであることをユーザーに知らせる主要な作業であり、非常に大きな場合に便利です。
* 型を大きくするのは避けてください。アプリランチャーのコアディメンション (より多く以下) の範囲内に保持してください。
* フラット型は機能しますが、特定の角度や特定の環境で表示するのが難しい場合があることに注意してください。 これを実現するには、それをソリッドオブジェクトまたは背景に配置することを検討してください。
* ディメンションを型に追加すると、3D では見栄えが良くなります。 種類の面の網掛けは、読みやすさを向上させるのに役立ちます。

:::row:::
    :::column:::
        ![背景のないフラット型は特定の角度から見るのが難しい場合があります。また、特定の環境では、 ](images/flattype-640px.png) *背景を持たないフラットな型を特定の角度や特定の環境で表示するのが難しい* 場合があります。
    :::column-end:::
    :::column:::
        ![組み込みの背景を持つ型は、組み込みの背景を使用して適切な型を使用できます。 ](images/flattypeandbkg-640px.png) *Type with a built-in backdrop can work well*
    :::column-end:::
    :::column:::
        ![押し出しの種類を網掛けすると、 ](images/20171016-160221-mixedreality-640px.jpg) *押し出しの種類* が正しく機能します。
    :::column-end:::
:::row-end:::

**機能する色を入力する**

* 白
* Black
* 明るい半彩度の色

![機能する色を入力します。](images/20171016-112111-mixedreality-640px.jpg)<br>
*機能する色を入力する*

### <a name="colors-to-avoid"></a>避ける色

問題の原因となる色の種類は次のとおりです。

* ミッドトーン
* グレー
* 彩度が高い色または desaturated の色

![問題の原因となる色を入力します。](images/20171016-112246-mixedreality-640px.jpg)<br>
*問題の原因となる色を入力する*

## <a name="lighting"></a>照明

アプリランチャーのライティングは、崖ハウス環境から取得されます。 ライトとシャドウの両方で適切に見えるように、家全体の複数の場所でランチャーをテストしてください。 このドキュメントに記載されている他の設計ガイダンスに従っている場合は、崖家のほとんどの照明に対してランチャーが非常に優れた形になっているはずです。

環境内のさまざまなライトをランチャーがどのように検索するのかをテストするのに適しているのは、テラス (芝生を使用した具体的な領域) の外側と背面のどこにあるかを問わず、Studio、メディアルームです。 もう1つの優れたテストは、それを半分のライトと半分に配置し、外観を確認することです。

![起動ツールがライトとシャドウの両方で適切であることを確認します。](images/20171013-145523-mixedreality-1200px-1000px.jpg)<br>
*起動ツールがライトとシャドウの両方で適切であることを確認します。*

## <a name="texturing"></a>テクスチャ

### <a name="authoring-your-textures"></a>テクスチャの作成

3D アプリランチャーの終了形式は、glb ファイルになります。これは、(物理的にベースになった) .PBR パイプラインを使用して作成されます。 これは厄介なプロセスである可能性があります。すでにない場合は、技術的アーティストを使用することをお勧めします。 勇気 DIY がある場合は、まず、情報を [調査して、.pbr の用語について学習](https://wiki.polycount.com/wiki/PBR) して、内部で何が起きているかを確認すると、よくある間違いを避けることができます。 

![例: 新しいメモアプリ](images/pbr-freshnote1-640px-500px.png)<br>
*新鮮ノート3D アプリランチャーの例 (架空のアプリ)*

### <a name="recommended-authoring-tool"></a>推奨 authoring tool

最終的なファイルを作成するには、Allegorithmic による [物質塗装](https://www.allegorithmic.com/products/substance-painter) を使用することをお勧めします。 物質コピーの作成に慣れていない場合は、次の [チュートリアル](https://docs.allegorithmic.com/documentation/display/SPDOC/Tutorials)を参照してください。

(また、 [3D コート](https://3dcoat.com/home/)、 [Quixel Suite 2](https://quixel.se/suite2/)、または [marmoset toolbag](https://www.marmoset.co/toolbag/) は、これらのいずれかを使い慣れている場合にも機能します)。

### <a name="best-practices"></a>ベスト プラクティス

* アプリランチャーオブジェクトが .PBR 用に作成されている場合、そのオブジェクトを崖家環境に変換するのは非常に簡単です。
* シェーダーは金属/粗さのフローを想定しています。 Unreal の .PBR シェーダーは、近いファクシミリです。
* テクスチャをエクスポートするときは、推奨される [テクスチャのサイズ](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md#material-guidelines) を考慮してください。
* 次のように、リアルタイムライティング用にオブジェクトを構築してください。
  * 影を描画しない (影を描画する)
  * テクスチャに含まれる光源を避けます
  * いずれかの .PBR マテリアル作成パッケージを使用して、シェーダー用に生成された適切なマップを取得します。

## <a name="see-also"></a>関連項目

* [Mixed reality ホームで使用する3D モデルを作成する](creating-3d-models-for-use-in-the-windows-mixed-reality-home.md)
* [3D アプリ起動ツールの実装 (UWP アプリ)](implementing-3d-app-launchers.md)
* [3D アプリ起動ツールの実装 (Win32 アプリ)](implementing-3d-app-launchers-win32.md)
