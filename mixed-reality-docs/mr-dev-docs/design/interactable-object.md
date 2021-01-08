---
title: 対話可能なオブジェクト
description: さまざまな現実のアプリケーションでイベントをトリガーしたり、視覚的な手掛かりを提供したり、オブジェクトと対話したりする方法について説明します。
author: cre8ivepark
ms.author: v-hferrone
ms.date: 06/06/2019
ms.topic: article
keywords: 混合現実、コントロール、対話、キュー、ui、ux、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、audio
ms.openlocfilehash: d0dc8ce6425d597d04b47a6c8b08f72534488594
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007202"
---
# <a name="interactable-object"></a>対話可能なオブジェクト

![Interactible オブジェクト](images/UX_Hero_Interactable.jpg)

ボタンは、2D 抽象ワールドでイベントをトリガーするために使用される比喩です。 3次元混合の現実世界では、この抽象化の世界に限定する必要はありません。 イベントをトリガーする **対話型オブジェクト** を指定できます。 対話型オブジェクトは、テーブル上のコーヒーカップから、アウト・エアのバルーンに至るまで、あらゆるものを持つことができます。 ダイアログ UI などの特定の状況では、従来のボタンを引き続き使用します。 ボタンのビジュアル表現は、コンテキストによって異なります。

<br>

---

## <a name="important-properties-of-the-interactable-object"></a>対話型オブジェクトの重要なプロパティ

### <a name="visual-cues"></a>視覚的な合図

視覚的な手掛かりとは、ライトからの sensory 合図、目が見てきたこと、視覚認識中にビジュアルシステムによって処理されることです。 ビジュアルシステムは多くの人、特に人間にとって最も重要であるため、視覚的な手掛かりは、世界の知覚に関する情報源です。

Holographic オブジェクトは、mixed reality の実際の環境とブレンドされるため、対話できるオブジェクトを理解するのが困難な場合があります。 対話型オブジェクトについては、各入力状態の視覚的な手掛かりを区別することが重要です。 これにより、ユーザーは、エクスペリエンスのどの部分が対話型されているかを理解し、一貫性のある対話方式を使用してユーザーの信頼を得られるようになります。

<br>

---

### <a name="far-interactions"></a>遠くのやり取り

ユーザーが宝石、ハンドレイ、およびモーションコントローラーの射線と対話できるオブジェクトについては、次の3つの入力状態に対して異なる視覚的な合図を使用することをお勧めします。

:::row:::
    :::column:::
       ![interactibleobject-既定値](images/interactibleobject-states-default.jpg)<br>
       **既定 (監視) の状態**<br>
        オブジェクトの既定のアイドル状態。
    カーソルがオブジェクト上にありません。 ハンドが検出されません。
    :::column-end:::
    :::column:::
       ![interactibleobject-対象](images/interactibleobject-states-targeted.jpg)<br>
        **ターゲット (ホバー) 状態**<br>
        オブジェクトが、見つめカーソル、指近接、またはモーションコントローラーのポインターの対象になっている場合。
    カーソルがオブジェクト上にあります。 ハンドが検出され、準備が完了しました。
    :::column-end:::
    :::column:::
       ![interactibleobject-押された状態](images/interactibleobject-states-pressed.jpg)<br>
       **押された状態**<br>
        オブジェクトがエアタップジェスチャで押されたときに、指を押すか、モーションコントローラーの [選択] ボタンをクリックします。
    カーソルがオブジェクト上にあります。 ハンドが検出されました。
    :::column-end:::
:::row-end:::

<br>

---

強調表示や拡大/縮小などの手法を使用して、ユーザーの入力状態を視覚的に示すことができます。 Mixed reality では、[スタート] メニューとアプリバーボタンを使用してさまざまな入力状態を視覚化する例を見つけることができます。 

**Holographic ボタン** では、これらの状態は次のようになります。

:::row:::
    :::column:::
       ![interactibleobject-既定値](images/MRTK_InteractableState-default.jpg)<br>
       **既定 (監視) の状態**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-対象](images/MRTK_InteractableState-targeted.jpg)<br>
        **ターゲット (ホバー) 状態**<br>
    :::column-end:::
    :::column:::
       ![interactibleobject-押された状態](images/MRTK_InteractableState-pressed.jpg)<br>
       **押された状態**<br>
    :::column-end:::
:::row-end:::

<br>

---

### <a name="near-interactions-direct"></a>Near 相互作用 (ダイレクト) 

HoloLens 2 では、オブジェクトとの対話を可能にする、手による追跡入力をサポートしています。 Haptic のフィードバックや完全な深さの認識がなければ、オブジェクトから手の外に出てきたことや、それに触れるかどうかを判断するのは困難な場合があります。 オブジェクトの状態を伝えるのに十分な視覚的な手掛かりを提供することが重要です。特に、そのオブジェクトに基づいて実際の状態を伝えます。

視覚的フィードバックを使用して、次の状態を伝えます。
* **既定 (監視)**: オブジェクトの既定のアイドル状態。
* **ホバー**: 手がホログラムの近くにある場合は、ビジュアルを変更して、その手がホログラムをターゲットとしていることを伝えます。 
* **距離とポイントの相互作用**: 手がホログラムに近づいたときに、投影された相互作用ポイントと、オブジェクトから指がどこまでの距離であるかを通知するデザインフィードバック
* **連絡先の開始**: ビジュアル (明るい色) を変更して、タッチが発生したことを通知します
* **Grasped**: オブジェクトが Grasped の場合にビジュアル (明るい、色) を変更します。
* **連絡先の終了**: タッチが終了したときのビジュアル (明るい、色) を変更します

<br>

---

:::row:::
    :::column:::
        ![ホバー (遠く)](images/640px-interactibleobject-states-near-hover.jpg)<br>
        **ホバー (遠く)**<br>
        手書きの距離に基づいて強調表示します。
    :::column-end:::
    :::column:::
        ![ホバー (Near)](images/640px-interactibleobject-states-near-hovernear.jpg)<br>
        **ホバー (Near)**<br>
        ハンドの距離に応じてサイズの変化を強調表示します。
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![タッチ/押す](images/640px-interactibleobject-states-near-press.jpg)<br>
        **タッチ/押す**<br>
        ビジュアルとオーディオフィードバック。
    :::column-end:::
    :::column:::
        ![つかん](images/640px-interactibleobject-states-near-grasp.jpg)<br>
        **つかん**<br>
        ビジュアルとオーディオフィードバック。
    :::column-end:::
:::row-end:::

<br>

<br>

---

[HoloLens 2 のボタン](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)は、さまざまな入力相互作用状態を視覚化する方法の例です。

:::row:::
    :::column:::
        ![既定値](images/640px-interactibleobject-pressablebutton-default.jpg)<br>
        **[Default]**<br>
    :::column-end:::
    :::column:::
        ![ホバー](images/640px-interactibleobject-pressablebutton-hover.jpg)<br>
        **ホバー**<br>
        距離に基づく光源効果を表示します。
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        ![タッチ](images/640px-interactibleobject-pressablebutton-touch.jpg)<br>
        **タッチ**<br>
        Ripple 効果を表示します。
    :::column-end:::
    :::column:::
        ![ショートカット キー](images/640px-interactibleobject-pressablebutton-press.jpg)<br>
        **ショートカット キー**<br>
        前面プレートを移動します。
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="the-ring-visual-cue-on-hololens-2br"></a>HoloLens 2 の "リング" ビジュアルキュー<br>
        HoloLens 2 では、追加の視覚的な手掛かりがあります。これは、ユーザーが深さを認識するのに役立ちます。 指先がオブジェクトに近づいたときに、指先の近くにあるリングが表示され、スケールダウンされます。 このリングは、押された状態に達したときに、最終的にドットに収束します。 このビジュアル affordance は、オブジェクトからの距離をユーザーが理解するのに役立ちます。<br>
        <br>
        *ビデオループ: 境界ボックスとの近接度に基づくビジュアルフィードバックの例*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![手書きの視覚的フィードバック](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::


<br>

---


### <a name="audio-cues"></a>オーディオキュー

直接の対話では、適切なオーディオフィードバックによってユーザーエクスペリエンスが大幅に向上します。 オーディオフィードバックを使用して、次の手掛かりを伝えます。
* **連絡先の開始**: タッチの開始時にサウンドを再生する
* **連絡先の終了**: タッチエンドでサウンドを再生する
* **グラブの開始**: グラブの開始時にサウンドを再生する
* **グラブ端**: グラブ終了時にサウンドを再生する

<br>

---

:::row:::
    :::column:::
        ### <a name="voice-commandingbr"></a>音声コマンド<br>
        対話型オブジェクトについては、代替の対話オプションをサポートすることが重要です。 既定では、対話型されているすべてのオブジェクトに対して、 [音声コマンド](../out-of-scope/voice-design.md) をサポートすることをお勧めします。 見つけやすさを向上させるために、ホバー状態のときにツールヒントを提供することもできます。<br>
        <br>
        *イメージ: 音声コマンドのツールヒント*
    :::column-end:::
        :::column:::
       ![音声によるコマンド](images/640px-interactibleobject-voicecommand.png)<br>
    :::column-end:::
:::row-end:::


<br>

---


## <a name="sizing-recommendations"></a>サイズ設定に関する推奨事項 

すべての対話型オブジェクトを簡単に操作できるようにするには、ユーザーからの距離に基づいて、対話型が最小サイズを満たしていることを確認することをお勧めします。 視覚的な角度は、多くの場合、視覚円弧の度数で測定されます。視覚的な角度は、ユーザーの視点とオブジェクトの間の距離に基づいており、一定のままになります。一方、ターゲットの物理的なサイズは、ユーザーからの距離が変化すると変化する可能性があります。 ユーザーからの距離に基づいてオブジェクトの必要な物理サイズを判断するには、 [この](https://elvers.us/perception/visualAngle/)ような視覚的な角度計算ツールを使用します。

対話型コンテンツの最小サイズに関する推奨事項を以下に示します。


### <a name="target-size-for-direct-hand-interaction"></a>ダイレクトハンド操作のターゲットサイズ

| 距離 | 表示角度 | サイズ |
|---------|---------|---------|
| 45 cm  | 2°未満 | 1.6 x 1.6 cm |

![ダイレクトハンド操作のターゲットサイズ](images/TargetSizingNear.jpg)<br>
*ダイレクトハンド操作のターゲットサイズ*

<br>

### <a name="target-size-for-buttons"></a>ボタンのターゲットサイズ

直接対話するためのボタンを作成する場合は、3.2 x 3.2 cm の最小サイズを大きくすることをお勧めします。これにより、アイコンと一部のテキストを格納するための十分な領域が確保されます。

| 距離 | 最小サイズ |
|---------|---------|
| 45 cm  | 3.2 x 3.2 cm |

![ボタンのターゲットサイズ](images/TargetSizingButtons.png)<br>
*ボタンのターゲットサイズ*

<br>

### <a name="target-size-for-hand-ray-or-gaze-interaction"></a>ハンドレイまたは宝石の相互作用の目標サイズ
| 距離 | 表示角度 | サイズ |
|---------|---------|---------|
| 2 m  | 1°未満 | 3.5 x 3.5 cm |

![ハンドレイまたは宝石の相互作用の目標サイズ](images/TargetSizingFar.jpg)<br>
*ハンドレイまたは宝石の相互作用の目標サイズ*


<br>

---


## <a name="interactable-object-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 用の MRTK (Mixed Reality Toolkit) の対話型オブジェクト

**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** では、スクリプト [**対話型**](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.SDK/Features/UX/Interactable/Scripts)を使用して、オブジェクトがさまざまな種類の入力相互作用状態に応答するようにすることができます。 色、サイズ、素材、シェーダーなどのオブジェクトプロパティを制御することで、視覚的な状態を定義できるさまざまなテーマをサポートしています。

* [対話型](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)
* [Button](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)
* [ハンド操作の例シーン](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_release/Documentation/README_HandInteractionExamples.md)

MixedRealityToolkit の標準シェーダーには、ビジュアルおよびオーディオキューを作成するのに役立つ **近接光** などのさまざまなオプションが用意されています。
* [MRTK 標準シェーダー](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/mrtk_development/Documentation/README_MRTKStandardShader.md)


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
