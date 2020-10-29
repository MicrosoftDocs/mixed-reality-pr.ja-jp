---
title: ハンド メニュー
description: メニューを使用すると、ユーザーは頻繁に使用される関数のための直接の UI をすぐに表示できます。 これらは、メニューのベストプラクティスと推奨事項です。
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: ハンド、メニュー、ボタン、クイックアクセス、レイアウト
ms.openlocfilehash: f7bf8ab2fb54e6a939bd538a0a0ba756c5efb916
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686927"
---
# <a name="hand-menu"></a>ハンド メニュー

![Ulnar side location](images/UX_Hero_HandMenu.jpg)

このメニューは、HoloLens 2 の最も一意な UX パターンの1つです。 これにより、ハンドアタッチされた UI をすばやく表示できます。 いつでもアクセスできるため、簡単に表示および非表示にすることができます。

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

以下の一覧で、メニューを使用するための推奨されるベストプラクティスを紹介します。 また、 [Mrtk](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)の手の形を示すシーンの例も見つかります。

<br>


---

## <a name="best-practices"></a>ベスト プラクティス
**ボタンの数を小さくする** 

ハンドロックされたメニューと目の間には距離が近づいているのに対して、比較的小さな視覚面に焦点を当てるという傾向があるため (attentional コーンは約10度)、ボタンの数を小さくしておくことをお勧めします。 この探索に基づいて、3つのボタンがある1つの列は、ユーザーが視界の中央に移動した場合でも、ビューのフィールド (視界) 内のすべてのコンテンツを保持することで効果的に機能します。 

**クイックアクションに手のメニューを使用する** 

Arm を持ち上げて位置を維持すると、arm の疲労が簡単に生じる可能性があります。 短い対話を必要とするメニューには、ハンドロックされたメソッドを使用します。 メニューが複雑で、対話時間の延長が必要な場合は、代わりにワールドロックまたは本体ロックを使用することを検討してください。 

**ボタン/パネルの角度**

メニューは、両端が反対のショルダーと真ん中になるようにする必要があります。これにより、自然な移動は反対の手でメニューと対話し、ボタンをタッチするときに不快または不快な針を回避できます。 

**1ききまたはハンズフリー操作のサポートを検討する**

両方のユーザーが常に使用できるとは限りません。 一方または両方のハンズオンが使用できない場合は、さまざまなコンテキストを検討し、そのような状況に合わせて設計アカウントを確認します。 片手メニューをサポートするには、手動でロックしたときに、メニューの配置を手動でロックしてみてください。 ハンドフリーのシナリオでは、音声コマンドを使用して手の形のメニューを呼び出すことを検討してください。

**手首 (システムホームボタン) の近くにボタンが追加されないようにする**

手の形のボタンが [ホーム] ボタンの近くに置かれている場合は、メニューを操作しているときに誤ってトリガーされることがあります。

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>大規模で複雑な UI コントロールを持つ手のメニュー
<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
手動でアタッチしたメニューでは、ボタンまたは UI コントロールの数を制限することをお勧めします。 これは、多数の UI 要素との拡張操作によって arm の疲労が発生する可能性があるためです。 エクスペリエンスに大きなメニューが必要な場合は、ユーザーがメニューをロックするための簡単な方法を提供します。 1つの方法として、ユーザーを手に入れたり、逆にしたりするときに、メニューを使うことをお勧めします。 もう1つの方法は、ユーザーが直接メニューを取得できるようにすることです。 ユーザーがメニューを離すと、メニューがロックされます。 こうすることで、ユーザーはさまざまな UI 要素との対話を長時間にわたって容易に行うことができます。 

メニューが世界中にロックされている場合は、メニューを移動する方法を用意して、不要になったときにメニューを閉じるようにしてください。 メニューの横または上部にハンドルを入力して、メニューを移動できるようにします。 [閉じる] ボタンを追加して、メニューを閉じることができるようにします。 ユーザーがユーザーを手にしたときに、メニューを手動で再アタッチできるようにします。 また、誤ったアクティベーションを防ぐために、ユーザーが手動で gazes するように要求することもお勧めします (下記参照)。

**ユーザビリティの問題を示す大きなメニュー**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**手の形でロックされたメニュー**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**手動によるグラブ & [ワールドにプル]-メニューをロックする**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]


## <a name="how-to-prevent-false-activation"></a>偽のアクティベーションを防止する方法

ポップアップをイベントとしてのみ使用して、メニューをトリガーすると、不要になったときに誤って表示されることがあります (偽陽性)。これは、ユーザーが (通信とオブジェクトの操作のために) 意図的に移動し、意図せずに移動するためです。 偽のライセンス認証を減らすには、手のひらイベント以外に追加の手順を追加して、手のひら (完全に開いた指など) を呼び出すか、ユーザーが意図的に整理します。

**フラットなパームが必要**

フラットなオープンハンドを要求することで、ユーザーが環境内で通信中にオブジェクトやジェスチャを操作するときに、偽のアクティブ化を防ぐことができます。 

**宝石が必要**

ユーザーが自分の手を見つめ (目を見つめているか、頭を見つめている) ことを要求することで、誤ったライセンス認証を防ぐことができます。これは、ユーザーが補助的なアクティブ化の手順として手動で注意を向ける必要があるためです  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>手動によるメニューの配置のベストプラクティス

人間の構造では、ulnar は ulnar のボーンの近くで実行されます。 Ulna は、l 肘から最小の指まで伸縮する長い骨の中にあります。

次に、探索に基づく2つの推奨される配置を示します。


:::row:::
    :::column:::
        ![Ulnar side location](images/UlnarSideHandMenu.gif)<br>
        **Palm 内部の Ulnar**<br>
        この位置は、両手が互いに重ならないため、信頼性が高くなります。 これは、正確な手動検出と追跡に不可欠です。
    :::column-end:::
    :::column:::
        ![Ulnar side location](images/UlnarAboveHandMenu.gif)<br>
        **B. Ulnar (手動)**<br>
        この場所はユーザーにとって使いやすいものです。ユーザーは arm を起動して、手のメニューと対話する必要がないからです。 メニュー **13cm** をパームの上に配置し、ボタンを ulnar palm の内側に配置することをお勧めします。 [最適なボタンサイズの詳細を確認する](interactable-object.md)<br>
        <br>
        技術的な理由により、この場所は1つの必須の実装にすることをお勧めします。開発者は、ユーザーの反対側がこのメニューを操作するために終了した後で、メニューを固定する必要があります。 これにより、jitteriness が重複しないようにすることができ、ボタンをより高速にターゲット設定できるようになります。<br>
        <br>
        HoloLens 2 カメラは、互いに独立しているときに正確に識別します。 両手が重なると、メニューがアンカー位置から離れてしまう可能性があります。<br>
    :::column-end:::
:::row-end:::



<br>

---

## <a name="menu-positions-that-are-not-recommended"></a>推奨されないメニュー位置
さまざまなメニューのレイアウトや場所を使用したユーザーの調査を行っていますが、次のメニューの場所は推奨されて **いません** 。以下の各研究の欠点を確認してください。


:::row:::
    :::column:::
        ![Arm より上](images/AboveArm.gif)<br>
        **Arm の上**<br>
        1-適切な追跡を維持することが困難<br>
        2-不自然な位置が原因でユーザーの疲労が発生する
    :::column-end:::
    :::column:::
        ![上の指](images/AboveFingers.gif)<br>
        **上の指**<br>
        長い時間が経過したことによる1つの疲労<br>
        インデックスと中段指に関する2つの問題の追跡
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![中央の上にあるパーム](images/handCenter.gif)<br>
        **上-中央のパーム**<br>
        両手が重なっているために問題を追跡する<br>
        メニューと対話するためにハンドを長時間保持することによる2ハンドの疲労
    :::column-end:::
    :::column:::
        ![Top 指先 ](images/TopFingerTip.gif) **top 指先**<br>
        1ハンドトラッキングの問題<br>
        通常の姿勢を超えたままの2ハンドの疲労<br>
        3-指間のスペースが限られているために偶発的に他の指でボタンを押す問題
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Arm の背面](images/BackOfTheArm.gif)<br>
        **Arm の背面**<br>
        1-事故によってホームボタンをトリガーできる<br>
        2-自然または快適な位置
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity の MRTK (Mixed Reality Toolkit) の手の形のメニュー
**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、ハンドメニューのスクリプトとサンプルシーンが用意されています。 HandConstraintPalmUp ソルバースクリプトを使用すると、さまざまな構成可能なオプションを使用して、任意のオブジェクトをハンドにアタッチできます。 MRTK の手の形のメニューの例には、誤ったアクティベーションを防止するためのフラットなパームや宝石の要件などの便利なオプションが含まれています。

* [ハンドメニュードキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_HandMenu.html)
* [ハンドメニューのシーンの例](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

MRTK サンプルハブアプリを使用して、HoloLens 2 でメニューの例を試すことができます。 
* [MRTK サンプルハブの手メニューシーン](https://www.microsoft.com/en-us/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---


## <a name="see-also"></a>関連項目

* [カーソル](cursors.md)
* [ハンド レイ](point-and-commit.md)
* [ボタン](button.md)
* [対話可能なオブジェクト](interactable-object.md)
* [境界ボックスとアプリ バー](app-bar-and-bounding-box.md)
* [操作](direct-manipulation.md)
* [ハンド メニュー](hand-menu.md)
* [メニューの近く](near-menu.md)
* [オブジェクト コレクション](object-collection.md)
* [音声コマンド](voice-input.md)
* [キーボード](keyboard.md)
* [ヒント](tooltip.md)
* [スレート](slate.md)
* [スライダー](slider.md)
* [シェーダー](shader.md)
* [Billboard と Tag-along](billboarding-and-tag-along.md)
* [進行状況を表示する](progress.md)
* [表面吸着](surface-magnetism.md)
