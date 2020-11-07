---
title: ホログラムとは
description: HoloLens を使用すると、3次元のホログラム、光とサウンドで構成されるオブジェクトを、世界中に表示して対話することができます。
author: hferrone
ms.author: v-hferrone
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、HoloLens、ホログラム、設計、相互作用
ms.openlocfilehash: 5e0ef2768b6e79136f8144492d6825107a6ed88e
ms.sourcegitcommit: 9a489e8a3bf90b20f1b61606eea42c859c833424
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2020
ms.locfileid: "94340700"
---
# <a name="what-is-a-hologram"></a>ホログラムとは

<iframe width="940" height="530" src="https://www.youtube.com/embed/MVXH5V8MVQo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


HoloLens を使用する **と、実際** のオブジェクトの場合と同様に、世界中に表示される電球、光、サウンドで構成されるオブジェクトを作成できます。 ホログラムは、 [宝石](../design/gaze-and-commit.md)、 [ジェスチャ](../design/gaze-and-commit.md#composite-gestures) 、 [音声コマンド](../design/voice-input.md)に応答し、 [現実世界の表面](../design/spatial-mapping.md) と対話できます。 ホログラムを使用すると、世界の一部であるデジタル オブジェクトを作成できます。

<br>


## <a name="device-support"></a>デバイス サポート

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>機能</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>ホログラム</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

<br>

---

## <a name="a-hologram-is-made-of-light-and-sound"></a>ホログラムは、ライトとサウンドで構成されます。

HoloLens が [レンダリング](../develop/platform-capabilities-and-apis/rendering.md) するホログラムは、ユーザーの目の前に holographic フレームに直接表示されます。 ホログラムは、画面の光と周囲の光を両方とも見ることができるように、世界に光を追加します。 HoloLens は目から光を削除しません。そのため、ホログラムは黒の色でレンダリングできません。 代わりに、黒のコンテンツは透明として表示されます。

ホログラムは、さまざまな外観と動作を持つことができます。 現実的で安定したものもあれば、漫画と ethereal もあります。 ホログラムは、環境内の特徴を強調表示し、アプリのユーザーインターフェイスの要素にすることができます。

![ホログラムをハンド操作する](images/hologram-hands-940px.jpg)

ホログラムは [サウンド](../design/spatial-sound.md)を作成することもできます。これは、周囲の特定の場所から発生するように見えます。 HoloLens では、耳の上に直接配置されている2つのスピーカーをカバーせずに聞こえます。 ディスプレイと同様に、スピーカーは追加され、環境のサウンドをブロックすることなく新しいサウンドを導入します。

<br>

---

## <a name="a-hologram-can-be-placed-in-the-world-or-tag-along-with-you"></a>ホログラムは、世界またはタグに配置できます。

ホログラムが必要な場所がある場合は、それを世界中に正確に [配置](../design/coordinate-systems.md) することができます。 このホログラムを操作すると、ユーザーに対して相対的に安定したものとして表示されます。 [空間アンカー](../design/coordinate-systems.md#spatial-anchors)を使用してオブジェクトを世界にしっかりピン留めしている場合は、後で戻るときに、システムによってどこから離れているかを記憶できます。

![小売スペースで Microsoft Dynamics 365 レイアウトを使用する2人の男性](images/HLS19_retailLayoutHologram_001-940px.jpg)

一部のホログラムはユーザーに代わります。 これらのタグは、どこにいるかに関係なく、ユーザーに対して相対的に位置付けられます。 また、別の部屋に手を付けた後で、一度にホログラムを入れて壁に配置することもできます。

**ベスト プラクティス**
* 一部のシナリオでは、ホログラムを簡単に検出したり、エクスペリエンス全体に表示したりする必要がある場合があります。 この種の配置には、次の2つの高レベルのアプローチがあります。 **"Display-locked"** と **"body-locked"** を呼び出しましょう。
   * 画面のロックされたコンテンツは、デバイスのディスプレイに "locked" 位置れます。 これは、多くのユーザーが不満を感じ、"シェイクを clingyness" ことを望んでいるような不自然な "" を含むさまざまな理由により、非常に厄介です。 一般に、多くのデザイナーでは、表示ロックの内容を避けることが適切であることがわかりました。
   * 本文ロックのアプローチは、はるかに forgivable です。 ボディロックは、ホログラムがユーザーの本文またはテザリングさに配置されているにもかかわらず、ユーザーの周りに3d 空間に配置されている場合に行います。 多くのエクスペリエンスでは、ホログラムが "後" にあるユーザーを見つめているボディロック動作が採用されています。これにより、ユーザーは、ホログラムを紛失することなく、本文を回転させたり、スペースを移動したりすることができます。 遅延を組み込むことにより、ホログラムの動きがより自然になります。 たとえば、Windows Holographic OS のコア UI の中には、ユーザーが頭を変えたときに、柔軟に似た緩やかな遅延でユーザーの宝石に続くボディロックのバリエーションが使用されているものがあります。
* 見やすい距離にホログラムを配置します。通常は、ヘッドから約1-2 メートル離れています。
* Holographic フレーム内に常に存在する必要がある要素の誤差の量を指定するか、ユーザーが視点を変更したときに、コンテンツを表示の片側にアニメーション化することを検討します。

**最適なゾーンにホログラムを配置する (1.25 m から5分の間)**

2つのメーターが最適です。1つのメーターから見た方が近づくほど、エクスペリエンスが低下します。 1つのメーターよりも近い距離で、多くの場合に頻繁に移動するホログラムは、固定されたホログラムよりも問題になる可能性が高くなります。 ユーザーを予期しないエクスペリエンスにすることができないように、コンテンツが近すぎる場合は、適切にクリッピングまたはフェードアウトすることを検討してください。

![ユーザーからのホログラムを配置するための最適な距離。](images/distanceguiderendering-950px.png)

<br>

---


## <a name="a-hologram-interacts-with-you-and-your-world"></a>ホログラムがあなたと世界と対話する

ホログラムは光とサウンドだけではありません。また、世界中のアクティブな部分でもあります。 手でホログラムとジェスチャを見つめ、ホログラムを使用して、お客様によるフォローを開始することができます。 ホログラムに音声コマンドを指定すると、応答できます。

![Microsoft HoloLens 2 を使用して、風力 farm 開発プロジェクトで共同作業を行う政府ユーティリティ worker のグループ](images/HLS19_governmentUtilitiesHologram_001-940px.jpg)

ホログラムを使用すると、他の場所では不可能な個人の対話が可能になります。 HoloLens は、世界中の場所を認識しているので、holographic 文字を使用すると、部屋の周りを移動するときに、目に見えることがあります。

ホログラムは、周囲と対話することもできます。 たとえば、テーブルの上に holographic バウンスボールを配置できます。 次に、 [エアタップ](../design/gaze-and-commit.md#composite-gestures)でボールを見て、テーブルにヒットしたときに音を鳴らします。

ホログラムは、実世界のオブジェクトによって occluded することもできます。 たとえば、holographic 文字を使用すると、扉と壁の背後に移動することができます。

**ホログラムと実際の世界を統合するためのヒント**
* Gravitational の規則に合わせて、ホログラムをさらに多くの believable に関連付けることができます。 例: holographic dog は、スペースではなくテーブルの花瓶に & ています。
* 多くのデザイナーでは、ホログラムが置かれている表面に "負の影" を作成することによって、ホログラムをさらに believably に統合できることがわかりました。 これを行うには、ホログラムの周りにソフトグローを作成し、グローから "影" を引います。 ソフトグローは、現実世界の光と統合され、環境内のホログラムを grounds します。

<br>

---

:::row:::
    :::column:::
        ## <a name="a-hologram-is-whatever-bryou-can-dream-upbr"></a>ホログラムはどのようなものですか。 <br>夢を<br>
        Holographic の開発者として、お客様の創造性を、2D 画面や世界中に分割する力を持っています。<br><br>
        何をビルド *し* ますか?
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![リビングルームの Holographic 虚数ワールド](images/designoverview.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="next-discovery-checkpoint"></a>次回の検出チェックポイント

ここまでに説明した [探索](get-started-with-mr.md) の方法に従っている場合は、Mixed Reality の基本を確認しています。 ここから、次の基本トピックに進むことができます。 

> [!div class="nextstepaction"]
> [仕事のための新しいビジョン](https://dynamics.microsoft.com//mixed-reality/overview/)

または、にジャンプします。

> [!div class="nextstepaction"]
> [よりパーソナルなコンピューティングの追求](../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md)

## <a name="see-also"></a>関連項目
* [デザイン プロセスを展開する](case-study-expanding-the-design-process-for-mixed-reality.md)
* [立体音響](../design/spatial-sound.md)
* [色、ライト、マテリアル](../color,-light-and-materials.md)
