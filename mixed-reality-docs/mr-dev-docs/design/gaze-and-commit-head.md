---
title: 頭の視線入力とコミット
description: ヘッドとコミットの入力モデルの概要。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality、宝石、宝石を絞ったターゲット、相互作用、設計、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、ターゲット、フォーカス、スムージング
ms.openlocfilehash: cc12c349704a63c5b95c9eede91d0486f56787a2
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847884"
---
# <a name="head-gaze-and-commit"></a>頭の視線入力とコミット

_頭を見つめてコミット_ することは、ユーザーの頭の方向を持つオブジェクトを対象とする、 [宝石とコミット](gaze-and-commit.md) の入力モデルの特殊なケースです。 ハンドジェスチャのエアタップや "選択" 音声コマンドなど、2番目の入力でターゲットを操作できます。 

## <a name="device-support"></a>デバイス サポート

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>入力モデル</strong></td>
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>頭の視線入力とコミット</td>
        <td>✔️ 推奨</td>
        <td>✔️ 推奨 (3 番目の選択肢 -<a href="interaction-fundamentals.md">他のオプションを参照</a>)</td>
        <td>➕ 代替オプション</td>
    </tr>
</table>

---

## <a name="target-sizing-and-feedback"></a>ターゲットのサイズ設定とフィードバック

ヘッドの見つめベクターは、適切にターゲットを設定するために繰り返し表示されていますが、多くの場合、より大きなターゲットを取得する場合に最適です。 最小目標サイズが1°から1.5 °になると、ほとんどのシナリオでユーザーの操作が成功します。ただし、3度のターゲットでは、多くの場合、より高速に実行できます。 ユーザーが対象としているサイズは、3d 要素の場合でも実質的には2d 領域です。つまり、どちらの投影が発生しているかは、不要領域である必要があります。 要素が "アクティブ" である (ユーザーがターゲットとしている) ことを示すいくつかの重要な手掛かりが役に立ちます。 これには、表示されている "ホバー" 効果、オーディオのハイライトやクリック、要素を含むカーソルの配置のクリアなどの処置が含まれます。

![2 m の距離での最適なターゲット サイズ](images/gazetargeting-size-1000px.jpg)<br>
*2メートル距離での最適な目標サイズ*

<br>

![視線入力のターゲットとなるオブジェクトの強調表示の例](images/gazetargeting-highlighting-940px.jpg)<br>
*視線入力のターゲットとなるオブジェクトの強調表示の例*

## <a name="target-placement"></a>ターゲットの配置

多くの場合、ユーザーは、表示されているフィールドの数が多すぎる、または低い UI 要素を見つけることができません。 注目すべき点のほとんどは、主に注目している分野です。 ほとんどのターゲットは目の高さあたりの適正な帯域に配置すると効果的です。 ユーザーがいつでも比較的小さい視覚領域に焦点を当てる傾向がある場合 (attentional コーンは約10度)、UI 要素を関連する程度にグループ化することで、ユーザーが1つの領域に移動したときに項目から項目へのアテンションチェーン動作を使用できます。 UI を設計する際は、HoloLens とイマーシブ ヘッドセットでは視野内に潜在的な大きなバリエーションがあることに注意してください。

![Galaxy Explorer で視線入力のターゲット設定を容易にするためにグループ化された UI 要素の例](images/gazetargeting-grouping-1000px.jpg)<br>
*Galaxy Explorer で視線入力のターゲット設定を容易にするためにグループ化された UI 要素の例*

## <a name="improving-targeting-behaviors"></a>ターゲット設定動作の向上

ユーザーの意図を特定したり、近似したりすることができる場合は、適切に対象としているかのように、ユーザーの介入試行を受け入れることをお勧めします。 Mixed reality エクスペリエンスに組み込むことができる成功したメソッドのいくつかを次に示します。

### <a name="head-gaze-stabilization-gravity-wells"></a>頭の視線入力の安定化 ("重力井戸")

これは、ほとんどまたはすべての時間に有効にする必要があります。 この手法では、自然なヘッドとネックのジッターを排除します。これは、ユーザーが動作を検索したり話したりするため、動きが動いてくる可能性があります。

### <a name="closest-link-algorithms"></a>最も近いリンク アルゴリズム

これらのアルゴリズムは、スパースな対話型コンテンツを持つ領域で最適に機能します。 ユーザーが何を操作しようとしているかを判断できる確率が高い場合は、ある程度のインテントを想定して、対象となる機能を補完することができます。

### <a name="backdating-and-postdating-actions"></a>バックと後処理のアクション

このメカニズムは、速度が必要なタスクに役立ちます。 ユーザーが一連のターゲットとアクティブ化の処理を高速に進めるときは、何らかの目的を想定すると便利です。 また、タップの前または少し前に、ユーザーがフォーカスしていたターゲットに対して、不足しているステップの実行を許可することもできます (初期テストでは、50ミリ秒前後に有効です)。

### <a name="smoothing"></a>スムージング

このメカニズムは、自然な移動特性によってわずかなジッターと wobbles を減らすことで、パスの移動に役立ちます。 パスモーションをスムーズにスムージングする場合は、時間の経過と共に、移動のサイズと距離を滑らかにします。

### <a name="magnetism"></a>磁性

このメカニズムは、最も近いリンクアルゴリズムのより一般的なバージョンであると考えることができます。これは、ターゲットに向かってカーソルを描画するか、またはユーザーの意図に応じて対話型レイアウトに関する知識を使用して、ユーザーがターゲットに近づくことになる可能性があるためです。 これは、小規模なターゲットでは強力です。

### <a name="focus-stickiness"></a>焦点の持続性

対象となる近くの対話型要素を決定するときに、フォーカスの持続性によって、現在フォーカスがある要素にバイアスが与えられます。 これにより、自然なノイズを持つ2つの要素間の中間点で浮動フォーカスの切り替え動作を減らすことができます。

## <a name="see-also"></a>関連項目

* [視線ベースの操作](eye-gaze-interaction.md)
* [視線入力とドウェル](gaze-and-dwell.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - ジェスチャ](gaze-and-commit.md#composite-gestures)
* [手 - ポイントとコミット](point-and-commit.md)
* [本能的な操作](interaction-fundamentals.md)
* [音声入力](voice-input.md)



