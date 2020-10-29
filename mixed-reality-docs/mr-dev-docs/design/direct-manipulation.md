---
title: 手で直接操作
description: ユーザーがホログラムに手で直接触れる入力モデルである、直接操作について説明します。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/02/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 視線入力, 視線入力ターゲット設定, 対話, 設計, 手に近い, HoloLens
ms.openlocfilehash: 18e2a6128a5fa07fe2ddcd3c0eab192ccdedb4b4
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91700690"
---
# <a name="direct-manipulation-with-hands"></a>手で直接操作

![ボタン](images/UX_Hero_Manipulation.jpg)

直接操作は、ホログラムに手で直接触れる入力モデルです。 この概念の背景にある考え方は、オブジェクトを現実の世界と同じように動かすことです。 ボタンを押してオンにしたり、オブジェクトをつかんで手に取ったりできます。2D コンテンツは仮想タッチスクリーンのように動作します。 このため、直接操作はユーザーにとって学びやすく、楽しくもあります。 直接操作は、"近接" 入力モデルと考えられており、手の届く範囲にあるコンテンツの操作に最適です。

直接操作はアフォーダンスをベースとしているので、操作が簡単です。 ユーザーは象徴的なジェスチャを学ぶ必要はありません。 すべての対話は、触ったりつかんだりできる視覚的要素を中心に構築されています。

## <a name="device-support"></a>デバイス サポート

<table>
<colgroup>
    <col width="33%" />
    <col width="22%" />
    <col width="22%" />
    <col width="22%" />
</colgroup>
<tr>
     <td><strong>入力モデル</strong></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (第 1 世代)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="https://docs.microsoft.com/windows/mixed-reality/immersive-headset-hardware-details"><strong>イマーシブ ヘッドセット</strong></a></td>
</tr>
<tr>
     <td>手で直接操作</td>
     <td>❌ サポート対象外</td>
     <td>✔️ 推奨</td>
     <td>➕ サポート対象。  UI の場合、代わりに<a href="point-and-commit.md">手を使ったポイントとコミット</a>を推奨。</td>
    
</tr>
</table>


直接操作は HoloLens 2 の主要な入力モデルであり、新しい多関節ハンド トラッキング システムを使用します。 この入力モデルは、イマーシブ ヘッドセットでもモーション コントローラー経由で利用できますが、オブジェクト操作以外の対話の主要な手段としてはお勧めできません。 HoloLens (第 1 世代) では直接操作を利用できません。

<br>

---

## <a name="collidable-fingertip"></a>接触可能な指先

HoloLens 2 では、ユーザーの手が、左右の手の骨格モデルとして認識および解釈されます。 ホログラムに直接手で触れるという概念を実現するためには、それぞれの手の骨格モデルの 5 本の指先に 5 つのコライダーを取り付けることが理想的と考えられました。 しかし、触覚的フィードバックがないため、10 本の接触可能な指先とホログラムとの間で、期待に反する予測不可能な衝突が発生してしまいました。 

このため、両方の人差し指だけにコライダーを付けることをお勧めします。 それでも、接触可能な人差し指の指先は、下の画像に示すように、他の指を含むさまざまなタッチ ジェスチャのアクティブ タッチ ポイントとして機能します。たとえば、指 1 本で押す、指 1 本でタップ、指 2 本で押す、指 5 本で押すなどです。

:::row:::
    :::column:::
       ![接触可能な指先](images/Collidable-Fingertip.jpg)<br>
       **接触可能な指先**<br>
    :::column-end:::
    :::column:::
       ![指 1 本で押す](images/Collidable-Fingertip-1-finger-press.jpg)<br>
        **指 1 本で押す**<br>
    :::column-end:::
    :::column:::
       ![指 1 本でタップ](images/Collidable-Fingertip-1-finger-tap.jpg)<br>
       **指 1 本でタップ**<br>
    :::column-end:::
    :::column:::
       ![指 5 本で押す](images/Collidable-Fingertip-5-finger-press.jpg)<br>
       **指 5 本で押す**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="sphere-collider"></a>スフィア コライダー

ランダムな汎用シェイプを使用する代わりに、スフィア コライダーを使用することをお勧めします。 そのようにすれば、スフィアを視覚的にレンダリングして、近接ターゲット設定のためのより優れた手掛かりにできます。 タッチ精度を上げるには、スフィアの直径を人差し指の太さに合わせる必要があります。 hand API を呼び出すことで、指の太さの変数を簡単に取得できます。

### <a name="fingertip-cursor"></a>指先カーソル

人差し指の指先に接触可能なスフィアをレンダリングすることに加え、高度な指先カーソルも作成されました。これにより、近接ターゲット設定のエクスペリエンスが向上します。 これは、人差し指に付随するドーナツ型のカーソルです。 これは距離に応じて対象に反応して向きやサイズが変化します。詳しくは、以下のとおりです。

* 人差し指をホログラムに近づけると、カーソルは常にホログラムの表面と平行になり、近づくにつれて徐々にサイズが小さくなります。
* 指が表面に触れるとカーソルは直ちにドットにまで縮小し、タッチ イベントが発生します。

次に示されているように、ユーザーは、対話型のフィードバックによって、ハイパーリンクのトリガーやボタンの押下など、高い精度で近接ターゲット設定のタスクを実行できます。 

:::row:::
    :::column:::
       ![指先カーソル (遠い)](images/Fingertip-cursor-far.jpg)<br>
       **指先カーソル (遠い)**<br>
    :::column-end:::
    :::column:::
       ![指先カーソル (近い)](images/Fingertip-cursor-near.jpg)<br>
        **指先カーソル (近い)**<br>
    :::column-end:::
    :::column:::
       ![指先カーソル (接触)](images/Fingertip-cursor-contact.jpg)<br>
       **指先カーソル (接触)**<br>
    :::column-end:::
:::row-end:::

<br>



## <a name="bounding-box-with-proximity-shader"></a>近接シェーダーを備えた境界ボックス

触覚的フィードバックがないことを補うため、ホログラム自体にも視覚および音声の両方のフィードバックを提供する機能が必要です。 そこで、近接シェーダーを備えた境界ボックスという概念が考案されました。 境界ボックスは、3D オブジェクトを囲む最小の立体領域です。 境界ボックスには、近接シェーダーと呼ばれる対話的なレンダリング メカニズムがあります。 近接シェーダーは次のように動作します。

:::row:::
    :::column:::
       ![視覚的なフィードバックのホバー (遠い)](images/bounding-box-with-proximity-shader-hover-far.jpg)<br>
       **ホバー (遠い)**<br>
       人差し指が一定範囲内にある場合、指先スポットライトが境界ボックスの表面に投影されます。
    :::column-end:::
    :::column:::
       ![視覚的なフィードバックのホバー (近い)](images/bounding-box-with-proximity-shader-hover-near.jpg)<br>
        **ホバー (近い)**<br>
        指先が表面に近づくと、距離に応じてスポットライトが縮小します。
    :::column-end:::
    :::column:::
       ![接触開始](images/bounding-box-with-proximity-shader-begin-contact.jpg)<br>
       **接触開始**<br>
       指先が表面に触れると直ちに、境界ボックス全体の色が変わったり、視覚的効果が生じたりして、タッチ状態が反映されます。
    :::column-end:::
    :::column:::
       ![接触終了](images/bounding-box-with-proximity-shader-end-contact.jpg)<br>
       **接触終了**<br>
       また、効果音が鳴るようにしてタッチの視覚的フィードバックを増強できます。
    :::column-end:::
:::row-end:::

<br>

---

## <a name="pressable-button"></a>押しボタン

ユーザーは接触可能な指先で、押しボタンなど基本的なホログラフィック UI コンポーネントを操作できます。 押しボタンは、直接指で押せるように調整されたホログラフィック ボタンです。 押しボタンの場合もそれを押したときの感覚がないので、触覚フィードバックに関連した問題を処理するためのメカニズムがいくつか備えられています。

* 1 つ目のメカニズムは、近接シェーダーを備えた境界ボックスです。これについては、前のセクションで詳しく説明しました。 これにより、ユーザーがボタンに近づいて接触するとき、接近の感覚が向上します。
* 2 つ目のメカニズムは、押し下げの感覚です。 押し下げの感覚により、指先がボタンに接触した後、押し下げるという感覚が生まれます。 このメカニズムは、指先と一緒に、深さ軸に沿って、重みを伴ってボタンが動くようにします。 指定された深さに達したとき (トリガー時) か、その深さを超えた後で離したとき (リリース時) にボタンをトリガーすることができます。
* ボタンがトリガーされたときに効果音が鳴るようにしてフィードバックを増強する必要があります。

:::row:::
    :::column:::
       ![押しボタン (遠い)](images/pressable-button-far.jpg)<br>
       **指は遠く離れている**<br>
    :::column-end:::
    :::column:::
       ![押しボタン (近い)](images/pressable-button-approach.jpg)<br>
        **指が近づく**<br>
    :::column-end:::
    :::column:::
       ![押しボタン (接触開始)](images/pressable-button-contact.jpg)<br>
       **接触開始**<br>
    :::column-end:::
    :::column:::
       ![押しボタン (押下)](images/pressable-button-press.jpg)<br>
       **押し下げる**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>2D スレートとの対話

2D [スレート](slate.md)は、Web ブラウザーなどの 2D アプリ コンテンツをホストするホログラフィック コンテナーです。 直接操作による 2D スレートとの対話の設計概念は、物理的なタッチ画面との対話という概念的モデルを利用するというものです。

### <a name="to-interact-with-the-slate-contact"></a>スレートとの接触は、次のように操作します。

:::row:::
    :::column:::
       ![タッチ](images/2d-slate-interaction-touch.jpg)<br>
       **タッチ**<br>
       人差し指を使ってハイパーリンクまたはボタンを押します。
    :::column-end:::
    :::column:::
       ![スクロール](images/2d-slate-interaction-scroll2.jpg)<br>
        **スクロール**<br>
        人差し指を使ってスレート コンテンツを上下にスクロールします。
    :::column-end:::
    :::column:::
       ![ズーム](images/2d-slate-interaction-zoom2.jpg)<br>
       **ズーム**<br>
       ユーザーは 2 本の人差し指を使用して、指の相対的な動きに応じてスレートのコンテンツを拡大縮小します。
    :::column-end:::
:::row-end:::


### <a name="for-manipulating-the-2d-slate-itself"></a>2D スレート本体の操作方法

:::row:::
    :::column:::
       ![移動](images/manipulate-2d-slate-move.jpg)<br>
       **移動**<br>
       隅や端に手を動かして、一番近くにある操作アフォーダンスを表示します。 2D スレートの上部にあるホロバーをつかむことで、スレート全体を動かすことができます。
    :::column-end:::
    :::column:::
       ![スケール](images/manipulate-2d-slate-scale.jpg)<br>
        **スケール**<br>
        操作アフォーダンスをつかみ、隅のアフォーダンスで均等に拡大縮小します。
    :::column-end:::
    :::column:::
       ![リフロー](images/manipulate-2d-slate-reflow.jpg)<br>
       **リフロー**<br>
       操作アフォーダンスをつかみ、端のアフォーダンスでリフローを実行します。
    :::column-end:::
:::row-end:::

<br>

---


## <a name="3d-object-manipulation"></a>3D オブジェクトの操作

HoloLens 2 では、各 3D オブジェクトに境界ボックスを適用することで、ユーザーが 3D ホログラフィック オブジェクトを手で指示し、操作できます。 境界ボックスは、その近接シェーダーによって奥行きを感知しやすくします。 境界ボックスには、3D オブジェクト操作のための 2 つの設計アプローチがあります。

### <a name="affordance-based-manipulation"></a>アフォーダンスをベースとする操作

アフォーダンスをベースとする操作により、境界ボックスとその周囲の操作アフォーダンスを通じて 3D オブジェクトを操作できます。 

:::row:::
    :::column:::
       ![移動](images/3d-object-manipulation-move.jpg)<br>
       **移動**<br>
       ユーザーの手が 3D オブジェクトに近づくと直ちに、境界ボックスおよび最も近いアフォーダンスが表示されます。 ユーザーは、境界ボックスをつかんでオブジェクト全体を移動できます。
    :::column-end:::
    :::column:::
       ![回転](images/3d-object-manipulation-rotate.jpg)<br>
        **回転**<br>
        ユーザーは、端のアフォーダンスをつかんで回転できます。
    :::column-end:::
    :::column:::
       ![スケール](images/3d-object-manipulation-scale.jpg)<br>
       **スケール**<br>
       ユーザーは、隅のアフォーダンスをつかんで均等に拡大縮小できます。
    :::column-end:::
:::row-end:::

<br>


### <a name="non-affordance-based-manipulation"></a>アフォーダンスをベースとしない操作

アフォーダンスをベースとしない操作では、アフォーダンスは境界ボックスにアタッチされません。 ユーザーが行えるのは、境界ボックスを表示した後、直接対話することだけです。 境界ボックスを片手でつかむと、オブジェクトの移動と回転は手の動きと向きに関連付けられます。 ユーザーがオブジェクトを両手でつかむと、両手の相対的な動きに応じてそのオブジェクトを移動、拡大縮小、回転できます。

特定の操作では正確さが求められます。 **アフォーダンスをベースとする操作** を使用することをお勧めします。細かい調整を行うことができるためです。 融通が利く操作の場合は、 **アフォーダンスをベースとしない操作** を使用することをお勧めします。即興性のある、遊び心を加えたエクスペリエンスが許されるためです。

<br>

---


## <a name="instinctual-gestures"></a>本能的なジェスチャ

HoloLens (第 1 世代) では、ブルームやエアタップなど、いくつかの定義済みジェスチャをユーザーが学ぶ必要がありました。 HoloLens 2 では、ユーザーが象徴的なジェスチャを覚える必要はありません。 ユーザーがホログラムやコンテンツと対話するときに必要とされるユーザー ジェスチャは、どれも本能的なものです。 本能的なジェスチャを実現するには、ユーザーがジェスチャを実行するよう、UI アフォーダンスのデザインを通して支援するという方法を使用します。

たとえば、2 本の指でピンチしてオブジェクトまたは制御点をつかむようユーザーに促す場合、オブジェクトまたは制御点は小さいはずです。 5 本の指でつかむようユーザーに促す場合、オブジェクトまたは制御点は比較的大きいはずです。 ボタンも同様です。小さいボタンならユーザーは 1 本の指でしか押せませんが、大きなボタンならユーザーは手のひらで押すよう促されます。


:::row:::
    :::column:::
       ![移動](images/instinctual-gestures-smallobject.jpg)<br>
       **小さなオブジェクト**<br>
    :::column-end:::
    :::column:::
       ![回転](images/instinctual-gestures-mediumobject.jpg)<br>
        **中程度のオブジェクト**<br>
    :::column-end:::
    :::column:::
       ![スケール](images/instinctual-gestures-largeobject.jpg)<br>
       **大きなオブジェクト**<br>
    :::column-end:::
:::row-end:::


<br>

---

<br>

## <a name="symmetric-design-between-hands-and-6-dof-controllers"></a>手と 6 DoF コントローラーの間の対称設計

AR の手と VR のモーション コントローラーとの間には、操作に類似点があることにお気付きかもしれません。 どちらの入力も、それぞれの環境で直接操作をトリガーするために使用できます。 HoloLens 2 で近くのものを手でグラブ アンド ドラッグする操作は、WMR のモーション コントローラーのグラブ ボタンによる実行内容とほとんど同じです。 これにより、ユーザーは、2 つのプラットフォームの間の操作に習熟することができます。この知識は、アプリケーションを一方から他方に移植する場合に役立つことがあります。

<br>

---

## <a name="optimize-with-eye-tracking"></a>視線追跡の使用による最適化

直接操作が思い通りに機能する場合は魅力的に感じられるかもしれません。 しかし、手をどこに動かしても意図に反してホログラムがトリガーされてしまうと、フラストレーションの元になりかねません。 視線追跡は、ユーザーの意図をより的確に識別するのに役立ちます。

* **いつ** :意図に反して操作応答がトリガーされることが少なくなります。 視線追跡により、ユーザーの現在の関心事を理解しやすくなります。
たとえば、ホログラフィック テキスト (説明書) を読んでいるときに、現実世界の仕事道具を取るために手を伸ばしたとします。

そのときうっかり、ユーザーの視野 (FOV) に入っていなかったなどの理由で、それまでは気付いてさえいなかったいくつかの対話型ホログラフィック ボタンを横切って手を動かしてしまいました。

  つまり:ユーザーがしばらくの間ホログラムを見ていないにもかかわらず、それに対するタッチ イベントまたはグリップ イベントが検出された場合、ユーザーは実際にはそのホログラムと対話するつもりはなかった可能性があります。

* **どちら** :アクティブ化の誤検知への対応以外に、つかんだり突いたりするホログラムを識別しやすくなるという別の例もあります。特にいくつかのホログラムが互いに近接して配置されている場合、こちらの視点から正確な交点がはっきりと見えない場合があるためです。

  HoloLens 2 の視線追跡は、目の視線入力を識別する精度に基づく限界はありますが、奥行きの差により、手入力で操作する際の近くの操作に非常に役立ちます。 このことは、たとえば操作ウィジェットをつかむときに手がホログラムの後ろにあるのか前にあるのかを判断するのが難しい場合があることを意味します。

* **どこ** :クイック スロー ジェスチャで、ユーザーの視線に関する情報を使用します。 ホログラムをつかみ、目標とする場所のだいたいの方角に向かって放り投げたとします。  

    これでうまくいくこともあるかもしれませんが、ジェスチャの手の動きが速いと、目標とする場所が極めて不正確になる可能性があります。 しかし、視線追跡でジェスチャの精度を向上できる場合があります。

<br>

---

## <a name="manipulation-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 向け MRTK (Mixed Reality ツールキット) の操作
**[MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** を使用すると、スクリプト **ObjectManipulator** を使って一般的な操作の動作を簡単に実行できます。 ObjectManipulator を使用すると、手で直接またはハンド レイを使って、オブジェクトをつかんで移動させることができます。 また、オブジェクトのスケーリングおよび回転に対する両手の操作もサポートしています。

* [MRTK - 操作](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)


---

## <a name="see-also"></a>関連項目

* [頭の視線入力とコミット](gaze-and-commit.md)
* [手を使ったポイントとコミット](point-and-commit.md)
* [本能的な操作](interaction-fundamentals.md)
