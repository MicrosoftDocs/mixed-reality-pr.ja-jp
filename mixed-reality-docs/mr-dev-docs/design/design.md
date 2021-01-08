---
title: 設計とプロトタイプ作成を始める
description: 何かを作成する準備ができたら、設計とプロトタイプ作成を開始するために必要な基本的な概念について学習しましょう。
author: grbury
ms.author: grbury
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 検出, 配布, インデックス, ランディング ページ, 設計, 開発, チュートリアル, サンプル アプリ, 基本事項, ケース スタディ, リソース, HoloLens の使い方, オープン ソース プロジェクト, 主要な概念, 操作, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 5c0eefe6f4811feba6d1d52164652acbc44945c3
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847606"
---
# <a name="start-designing-and-prototyping"></a>設計とプロトタイプ作成を始める

![Mixed Reality の設計の概要](images/design-hero-image.png)

Mixed Reality アプリケーションはまったく新しいものであるため、その設計は困難な作業です。 作成する現実および仮想世界の新たな組み合わせについてだけでなく、それによって提供される新しいユーザー エクスペリエンスについても考慮する必要があります。 Mixed Reality の領域は広いため、設計範囲に沿って選択した重要なポイントを一連のチェックポイントとして次に示すことにしました。 これらは順番に取り組むことを想定していますが、既に十分な知識がある場合は、ご自由に後続の好きなセクションにスキップしてかまいません。

## <a name="design-checkpoints"></a>設計のチェックポイント

次のチェックポイントを使用して、アプリケーションのアイデアや概念を Mixed Reality の世界に移植することができます。

### <a name="1-getting-started"></a>1.はじめに

あらゆる作業と同様に、Mixed Reality アプリケーションの設計も基礎から始めます。 イマーシブ デザインに取りかかる前に、「[Mixed Reality とは](../discover/mixed-reality.md)」と「[ホログラムとは](../discover/hologram.md)」の記事を理解しておくことをお勧めします。 読み終えれば、Mixed Reality の設計作業を開始する準備が整っているでしょう。

![Designing Holograms アプリの紹介 GIF](images/HandTracking2.gif)

|  Checkpoint  |  結果  |
| --- | --- |
| [デザイン プロセスを展開する](../discover/case-study-expanding-the-design-process-for-mixed-reality.md) | Microsoft 内外の設計者から収集された Mixed Reality のデザイン プロセスを直接確認する |
| [Mixed Reality アプリの種類](types-of-mixed-reality-apps.md) | Mixed Reality の範囲のうち、どの領域のアプリ エクスペリエンスを実現するかを決定する |
| [Designing Holograms アプリ](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) | 優れた HoloLens アプリを作成するための動作、ヒント、推奨事項 (Microsoft Store の HoloLens 2 からダウンロード可能) を体験して、Mixed Reality UX Design の基礎を理解する |
| [MRTK Examples Hub](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4) | 複合現実の一般的な空間操作と UX 構成要素を体験する (HoloLens 2 の Microsoft Store からダウンロード可能) |

### <a name="2-core-concepts"></a>2. 主要な概念

開発対象が VR でも AR でも、柔軟なイマーシブ エクスペリエンスの設計には、いくつかの主要な概念が適用されます。 ユーザーの視点を理解し、オブジェクトを配置し、すべてのユーザーの快適性と安全性を確保することが、お客様の作業のこの段階における最優先事項です。 このセクションが完了する頃には、操作の設計まで全体を通して役に立つ強固な基盤が手に入ります。

![主要な概念の例の画像](images/fragments-750px.jpg)

|  概念  |  結果  |
| --- | --- |
| [ホログラフィック フレーム](holographic-frame.md) | ヘッドセットの装着時、現実世界に重ねて表示されたコンテンツがユーザーにどのように見えるかを理解する |
| [座標系](coordinate-systems.md) | 物理的な部屋であれ、自分が作成した仮想領域であれ、空間内の意味のある位置にホログラムを配置する方法を学習する |
| [空間マッピング](spatial-mapping.md) | オブジェクトをユーザーの世界に固定し、現実世界の物理サーフェスを利用する |
| [快適性に関する考慮事項](comfort.md) | 自然世界を模倣した方法でイマーシブ コンテンツの作成と提示を行うことで、ユーザーの快適性と安全性を確保する |

### <a name="3-interaction-design"></a>3.操作の設計

仮想エクスペリエンスがどれほど美しく臨場感にあふれていても、操作ができなければ役に立ちません。 このセクションでは、基本的な操作モデル、手とモーション コントローラー、音声入力、ユーザーからの視線追跡データの収集について説明します。 このセクションが完了する頃には、設計作業における最後の大きなトピックであるユーザー エクスペリエンスに取り組む準備が整います。

![操作の設計の要素](images/UX_Hero_Manipulation.jpg)

|  概念  |  結果  |
| --- | --- |
| [相互作用モデル](interaction-fundamentals.md) | 手、視線、音声による入力を使用した直感的な操作をユーザーに提供する |
| [手とモーション コントローラー](hands-and-tools.md) | ユーザーの手で近くのホログラムを操作する方法と、遠くから正確に操作する方法について学習する |
| [音声入力](voice-input.md) | 音声コマンドをイマーシブ アプリの入力として使用して、周囲のホログラムと環境をコントロールする  |
| [視線追跡](eye-tracking.md) | ユーザーが見ているものに関する情報を使用して、ホログラフィック エクスペリエンスに新しいレベルのコンテキストを追加し、人間による理解を深める |

### <a name="4-user-experience-elements"></a>4.ユーザー エクスペリエンス要素

基本的な操作を習得したので、ここからはユーザー エクスペリエンス要素のより詳細なポイントに注目して、それらを Mixed Reality 特有の環境に適合させていくことができます。 エクスペリエンスをユーザーにとって直感的に操作できるものにしながら、一般的な動作、資産の設計、オブジェクトのスケーリング、タイポグラフィについて説明します。 このセクションで Mixed Reality の正式な設計作業は終了します。さらに理解を深めたい場合は、「[次の操作](#whats-next)」セクションにある、その他のリソースをご利用ください。

![UX 要素](images/UX_Hero_BoundingBox.jpg)

|  概念  |  結果  |
| --- | --- |
| [一般的なコントロールと動作](app-patterns-landingpage.md) | 頻繁に使用される空間操作と UI 構成要素について学習する |
| [色、ライト、素材](color-light-and-materials.md) | 色、照明、素材を考慮して、Mixed Reality 用の高品質な資産を設計する |
| [オブジェクトのスケーリング](scale.md) | オブジェクトの場所、大きさ、材料をユーザーが理解しやすいように、現実世界の視覚的な手がかりを可能な限り組み込む |
| [文字体裁](typography.md) | はっきりと見える読みやすいテキストを 3 次元空間で使用して、ユーザーが必要とする重要な情報を提供する |

## <a name="whats-next"></a>次の操作

設計者の仕事に終わりはありません。新しいパラダイムでのイマーシブ エクスペリエンスの作成について学んでいる場合はなおさらです。 次のセクションでは、ここまでで説明しなかった中級以上の設計資料と、Mixed Reality の開発環境についてご紹介します。 これらのトピックとリソースに決まった順序はないので、お好きなものをご覧ください。

### <a name="choose-a-prototyping-option"></a>プロトタイプ作成のオプションを選択する  

:::row:::   
    :::column:::    
       [![Unity について学習する](images/logo-unity.png)](https://learn.unity.com/)<br>
        **[Unity について学習する](https://learn.unity.com/)**<br>
        Unity で対話型エクスペリエンスを作成する方法について学習します。 最初から最後まで、実践によって学習できます。
    :::column-end:::    
    :::column:::    
        [![Mixed Reality ツールキット (MRTK)](images/74-12.png)](https://github.com/Microsoft/MixedRealityToolkit-Unity)<br>
        **[Mixed Reality ツールキット (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity)**<br>  
        空間操作と UI 構成ブロックを使用すると、Unity での Mixed Reality の設計と開発をすぐに始めることができます。   
    :::column-end:::
    :::column:::    
        [![Mixed Reality Design Labs](images/74-13.png)](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)<br>
        **[Mixed Reality Design Labs](https://github.com/Microsoft/MRDL_Unity_PeriodicTable)**<br>  
        MRTK の構成要素を使用して美しい Mixed Reality エクスペリエンスを作成する方法を示すサンプル アプリを入手できます。
    :::column-end:::        
    :::column:::    
        [![Microsoft Maquette](images/74-14.png)](https://www.maquette.ms/)<br>
        **[Microsoft Maquette](https://www.maquette.ms/)**<br>  
        VR 向けの設計。 Microsoft Maquette を使用すると、空間のプロトタイプ作成をすばやく、簡単、かつイマーシブに実行できます。 
    :::column-end:::    
:::row-end:::

<br>

---

### <a name="other-resources"></a>その他のリソース

:::row:::
    :::column:::
       [![基本を理解する](images/74-15.png)](../discover/get-started-with-mr.md#understand-the-basics)<br>
        **[基本を理解する](../discover/get-started-with-mr.md#understand-the-basics)**<br>
        Mixed Reality が何によって定義され、どのように使用されているかについて理解を深めます。
    :::column-end:::
    :::column:::
        [![イベントに参加する](images/74-16.png)](../whats-new/sf-academy-events.md)<br>
         **[イベントに参加する](../whats-new/sf-academy-events.md)**<br>
        最初の HoloLens 2 アプリケーションを作成するには、ハードウェアを参照し、ハンズオン チュートリアルを入手してください。
    :::column-end:::
    :::column:::
        [![ツールのインストール](images/74-17.png)](../develop/install-the-tools.md)<br>
         **[ツールのインストール](../develop/install-the-tools.md)**<br>
        インストール チェックリストを使用して、HoloLens や Mixed Reality 用のアプリを構築するのに必要なツールを取得します。
    :::column-end:::
    :::column:::
        [![開発を始める](images/74-18.png)](../develop/development.md)<br>
        **[開発を始める](../develop/development.md)**<br>
        スキル レベル、ワーク スタイル、プラットフォームへの関心に基づいて、開発パスを選択します。
    :::column-end:::
:::row-end:::

<br>

<br>