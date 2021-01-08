---
title: 手を使ったポイントとコミット
description: ポイントとコミットの入力モデルの概要
author: caseymeekhof
ms.author: cmeekhof
ms.date: 04/05/2019
ms.topic: article
ms.localizationpriority: high
keywords: Mixed Reality, 対話, 設計, HoloLens, 手, 遠隔, ポイントとコミット, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, HoloLens, 手の光線, オブジェクト操作, MRTK, Mixed Reality Toolkit, DoF
ms.openlocfilehash: 13b692dada134f856ac6eed446cca45702030f67
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848294"
---
# <a name="point-and-commit-with-hands"></a>手を使ったポイントとコミット

![カーソル](images/UX_Hero_HandRay.jpg)

手を使ったポイントとコミットは、ユーザーが手の届かない所にある 2D や 3D のコンテンツをターゲットに設定したり、選択したり、操作したりできる入力モデルです。 この "遠隔" 対話技術は、人間が現実の世界と自然に対話するものではないため、Mixed Reality に固有です。 たとえば、スーパー ヒーロー映画 *X-Men* のキャラクター [Magneto ](https://en.wikipedia.org/wiki/Magneto_(comics)) は、遠くにある物体を自分の手で操作することができます。 こうしたことは現実世界では行えません。 HoloLens (AR) と Mixed Reality (MR) の両方で、この魔法の力をユーザーに付与して現実世界の物理的制約を打ち破ります。 ホログラフィック エクスペリエンスを楽しむだけでなく、ユーザーの対話をより効果的かつ効率的にします。

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
     <td><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
     <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
     <td><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
</tr>
<tr>
     <td>手を使ったポイントとコミット</td>
     <td>❌ サポート対象外</td>
     <td>✔️ 推奨</td>
     <td>✔️ 推奨</td>
</tr>
</table>


_"手を使ったポイントとコミット"_ は、新しい多関節ハンド トラッキング システムを使用した新機能の 1 つです。 この入力モデルは、モーション コントローラーを使用したイマーシブ ヘッドセットの主要な入力モデルでもあります。

<br>

---

## <a name="hand-rays"></a>手の光線

HoloLens 2 では、ユーザーの手のひらの中心から放出される手の光線を考案しました。 この光線は、手の延長と見なされます。 光線がターゲット オブジェクトと交わる場所を示すために、光線の終端にドーナツ型のカーソルが取り付けられています。 カーソルが届いているオブジェクトは、手から出されるジェスチャ コマンドを受け取ることができます。

この基本的なジェスチャ コマンドは、親指と人差し指を使ってエアタップ アクションを実行することでトリガーされます。 手の光線を使用してポイントし、エアタップを使用してコミットすることで、ユーザーはボタンまたはハイパーリンクを有効にすることができます。 ユーザーは、より複合的なジェスチャを使うことで、Web コンテンツをナビゲートしたり、遠くから 3D オブジェクトを操作したりすることができます。 以下に説明および図示されているように、手の光線の視覚的なデザインも、これらのポイントとコミット状態に合わせて変化します。 

:::row:::
    :::column:::
        ![ハンド レイ ポイント](images/hand-rays-pointing.jpg)<br>
        **ポイント状態**<br>
        *ポイント* 状態の光線は破線で表され、カーソルはドーナツ型になります。
    :::column-end:::
    :::column:::
        ![ハンド レイ コミット](images/hand-rays-commit.jpg)<br>
        **コミット状態**<br>
        *コミット* 状態になると光線は実線に変わり、カーソルは小さくなってドットになります。
    :::column-end:::
:::row-end:::

<br>

---

## <a name="transition-between-near-and-far"></a>近くと遠くの切り替え

「人差し指で指す」ことで光線を方向付けるなどの特定のジェスチャを使用する代わりに、ユーザーの手のひらの中心から光線が出るように設計しました。 これにより、5 本の指を解放して、より操作的なジェスチャ (ピンチやグラブなど) を行うために取っておくことができます。 この設計では、メンタル モデルを 1 つだけ作りました。近くでも遠くでも、まったく同じ一連の手のジェスチャで操作できます。 同じグラブ ジェスチャで、距離が異なるオブジェクトを操作できます。 光線の呼び出しは、次のように近さに基づいて自動で行われます。

:::row:::
    :::column:::
        ![近くの操作](images/transition-near-manipulation.jpg)<br>
        **近くの操作**<br>
        腕の長さ (約 50 cm) の範囲内にオブジェクトが入ると光線は自動的に消え、近接の対話が勧められます。
    :::column-end:::
    :::column:::
        ![遠くの操作](images/transition-far-manipulation.jpg)<br>
        **遠くの操作**<br>
        オブジェクトとの距離が 50 cm を超えると、光線が点灯します。 切り替えはスムーズかつシームレスに行われます。
    :::column-end:::
:::row-end:::

<br>

---

## <a name="2d-slate-interaction"></a>2D スレートとの対話

2D スレートは、Web ブラウザーなどの 2D アプリ コンテンツをホストするホログラフィック コンテナーです。 2D スレートとの遠隔対話の設計概念は、手の光線を使ってターゲット設定し、エアタップで選択するというものです。 手の光線でターゲット設定した後、ユーザーはエアタップしてハイパーリンクまたはボタンをトリガーできます。 片手で「エアタップ アンド ドラッグ」して、スレートのコンテンツを上下にスクロールすることができます。 両手を使ってエアタップ アンド ドラッグするという相対的な動きにより、スレートのコンテンツを拡大縮小することができます。

手の光線を隅や端にターゲット設定すると、最も近くにある操作アフォーダンスが表示されます。 ユーザーは操作アフォーダンスを「グラブ アンド ドラッグ」することで、隅のアフォーダンスによって均等に拡大縮小したり、端のアフォーダンスによってスレートをリフローしたりできます。 2D スレートの上部にあるホロバーをグラブ アンド ドラッグすることで、ユーザーはスレート全体を移動できます。

:::row:::
    :::column:::
       ![2D スレートの操作 (クリック)](images/2d-slate-interaction-click.jpg)<br>
       **クリック**<br>
    :::column-end:::
    :::column:::
       ![2D スレートの操作 (スクロール)](images/2d-slate-interaction-scroll.jpg)<br>
        **スクロール**<br>
    :::column-end:::
    :::column:::
       ![2D スレートの操作 (ズーム)](images/2d-slate-interaction-zoom.jpg)<br>
       **ズーム**<br>
    :::column-end:::
:::row-end:::

<br>

**2D スレートの操作方法**<br>

* ユーザーは、手の光線を隅または端にポイントして、最も近くにある操作アフォーダンスを表示します。 
* アフォーダンスに操作ジェスチャを適用すれば、ユーザーは隅のアフォーダンスによって均等に拡大縮小したり、端のアフォーダンスによってスレートをリフローしたりできます。 
* 2D スレートの上部にあるホロバーに操作ジェスチャを適用することで、ユーザーはスレート全体を移動できます。<br>

<br>

---

## <a name="3d-object-manipulation"></a>3D オブジェクトの操作

直接操作では、ユーザーは、アフォーダンスをベースとする操作とアフォーダンスをベースとしない操作の 2 つの方法で 3D オブジェクトを操作できます。 ポイントとコミットのモデルでは、ユーザーはハンド レイを使ってまったく同じ作業を行えます。 追加の学習は必要ありません。<br>

### <a name="affordance-based-manipulation"></a>アフォーダンスをベースとする操作

ユーザーは手の光線を使用して、境界ボックスと操作アフォーダンスをポイントし、表示します。 ユーザーは操作ジェスチャを境界ボックスに適用してオブジェクト全体を移動したり、端のアフォーダンスに適用して回転させたり、隅のアフォーダンスに適用して均等に拡大縮小したりすることができます。 <br>

:::row:::
    :::column:::
       ![3D オブジェクト操作 (遠方移動)](images/3d-object-manipulation-far-move.jpg)<br>
       **移動**<br>
    :::column-end:::
    :::column:::
       ![3D オブジェクト操作 (遠方回転)](images/3d-object-manipulation-far-rotate.jpg)<br>
        **回転**<br>
    :::column-end:::
    :::column:::
       ![3D オブジェクト操作 (遠方スケール)](images/3d-object-manipulation-far-scale.jpg)<br>
       **スケール**<br>
    :::column-end:::
:::row-end:::

### <a name="non-affordance-based-manipulation"></a>アフォーダンスをベースとしない操作

ユーザーは手の光線を使ってポイントし、境界ボックスを表示した後、直接操作ジェスチャを適用します。 片手を使用する場合、オブジェクトの移動と回転は手の動きと向きに関連付けられます。 ユーザーが両手を使用すると、両手の相対的な動きに応じてそれを移動、拡大縮小、回転できます。<br>

<br>

---

## <a name="instinctual-gestures"></a>本能的なジェスチャ

ポイントとコミットについての本能的なジェスチャの概念は、[手による直接操作](direct-manipulation.md)の概念と似ています。 ユーザーが 3D オブジェクトに対して実行するジェスチャは、UI アフォーダンスの設計によって導かれます。 たとえば、小さな制御点の場合にはユーザーは親指と人差し指でピンチするよう誘導されるのに対し、大きなオブジェクトをつかむためには 5 本の指すべてを使うかもしれません。

:::row:::
    :::column:::
       ![本能的なジェスチャ (遠くの小さなオブジェクト)](images/instinctual-gestures-far-smallobject.jpg)<br>
       **小さなオブジェクト**<br>
    :::column-end:::
    :::column:::
       ![本能的なジェスチャ (遠くの中程度のオブジェクト)](images/instinctual-gestures-far-mediumobject.jpg)<br>
        **中程度のオブジェクト**<br>
    :::column-end:::
    :::column:::
       ![本能的なジェスチャ (遠くの大きなオブジェクト)](images/instinctual-gestures-far-largeobject.jpg)<br>
       **大きなオブジェクト**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="symmetric-design-between-hands-and-6-dof-controller"></a>手と 6 DoF コントローラーの間の対称設計 

遠くにあるものと対話する場合のポイントとコミットの概念は、Mixed Reality ポータル (MRP) 向けに考案され、定義されました。 このシナリオでは、ユーザーはイマーシブ ヘッドセットを装着し、モーション コントローラーを介して 3D オブジェクトとやり取りします。 モーション コントローラーは、遠くにあるオブジェクトをポイントして操作するために光線を放ちます。 コントローラーにはボタンがあって、さまざまな操作をさらにコミットします。 光線の対話モデルを適用して、それを両手で利用することにしました。 この対称設計により、MRP に精通しているユーザーは HoloLens 2 を使用するとき、遠くにあるものをポイントして操作するための別の対話モデルを学ぶ必要がなくなります (逆も同様です)。    

:::row:::
    :::column:::
        ![コントローラーでの光線の対称設計](images/symmetric-design-for-rays-controllers.jpg)<br>
        **コントローラーの光線**<br>
    :::column-end:::
    :::column:::
        ![手での光線の対称設計](images/symmetric-design-for-rays-hands.jpg)<br>
        **ハンド レイ**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-ray-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 向け MRTK (Mixed Reality ツールキット) のハンド レイ

既定で、MRTK には、シェルのシステム ハンド レイと同じ表示状態のハンド レイ プレハブ ([DefaultControllerPointer.prefab](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Prefabs/Pointers)) が備わっています。 これは、[ポインター] にある MRTK の入力プロファイルに割り当てられています。 イマーシブ ヘッドセットでは、モーション コントローラーにも同じ光線が使用されています。

* [MRTK - ポインター プロファイル](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html#pointer-configuration)
* [MRTK - 入力システム](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)
* [MRTK - ポインター](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Pointers.html)

---

## <a name="see-also"></a>関連項目
* [手で直接操作](direct-manipulation.md)
* [視線入力とコミット](gaze-and-commit.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - ジェスチャ](gaze-and-commit.md#composite-gestures)
* [本能的な操作](interaction-fundamentals.md)
