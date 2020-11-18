---
title: 頭の視線入力とコミット
description: 頭の視線入力とコミットの入力モデルの概要
author: caseymeekhof
ms.author: cmeekhof
ms.date: 03/31/2019
ms.topic: article
keywords: Mixed Reality、宝石、宝石を絞ったターゲット、相互作用、設計、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、ターゲット、フォーカス、スムージング
ms.openlocfilehash: d913ac81e20962d38178223a050fdccfb51d8632
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94702388"
---
# <a name="head-gaze-and-commit"></a>頭の視線入力とコミット
_頭を見つめてコミット_ することは、 [宝石とコミット](gaze-and-commit.md) の入力モデルの特殊なケースです。頭の方向 (ヘッド方向) を使用してオブジェクトをターゲットにし、その後、エアタップや音声コマンドの "Select" など、2番目の入力で動作します。 

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
ヘッドの見つめベクターは、適切にターゲット設定できるように繰り返し表示されていますが、多くの場合、ターゲットの全体に最適です。 最小目標サイズが 1 ~ 1.5 °の場合、ほとんどのシナリオでユーザーの操作が成功します。ただし、3度のターゲットでは、多くの場合、速度が向上します。 ユーザーがターゲットに設定するサイズは、3D 要素であっても実質的に 2D 領域であり、それが面しているどの投影もターゲット設定可能な領域になるはずです。 要素が "アクティブ" である (ユーザーがターゲットとしている) ことを示すいくつかの重要な手掛かりが、非常に便利です。 これには、表示されている "ホバー" 効果、オーディオのハイライトやクリック、要素を含むカーソルの配置のクリアなどの処置が含まれます。

![2 m の距離での最適なターゲット サイズ](images/gazetargeting-size-1000px.jpg)<br>
*2 m の距離での最適なターゲット サイズ*

<br>

![視線入力のターゲットとなるオブジェクトの強調表示の例](images/gazetargeting-highlighting-940px.jpg)<br>
*視線入力のターゲットとなるオブジェクトの強調表示の例*

## <a name="target-placement"></a>ターゲットの配置
多くの場合、ユーザーは、ビューのフィールドに非常に高い、または低い位置にある UI 要素を見つけることができず、主なフォーカスの周りにある領域に注目することに重点が置かれています。 ほとんどのターゲットは目の高さあたりの適正な帯域に配置すると効果的です。 ユーザーは常に比較的小さい視覚野に焦点を合わせる傾向があることを考慮すると (注意の視円錐は約 10 度)、UI 要素を概念的に関連性のある度数にグループ化すれば、ユーザーが視線入力で領域内を移動する場合に、項目から項目への注意の連鎖動作を活用できます。 UI を設計する際は、HoloLens とイマーシブ ヘッドセットでは視野内に潜在的な大きなバリエーションがあることに注意してください。

![Galaxy Explorer で視線入力のターゲット設定を容易にするためにグループ化された UI 要素の例](images/gazetargeting-grouping-1000px.jpg)<br>
*Galaxy Explorer で視線入力のターゲット設定を容易にするためにグループ化された UI 要素の例*

## <a name="improving-targeting-behaviors"></a>ターゲット設定動作の向上
ユーザーの意図を特定できる (または近似値を近似する) ことができた場合は、適切に対象としているかのように、操作の試行回数をよく受け入れることが非常に便利です。 Mixed reality エクスペリエンスに組み込むことができる成功したメソッドのいくつかを次に示します。

### <a name="head-gaze-stabilization-gravity-wells"></a>頭の視線入力の安定化 ("重力井戸")
これは、ほとんどまたはすべての時間に有効にする必要があります。 この手法では、自然なヘッドとネックのジッターを排除します。これは、ユーザーが動作を検索したり話したりすることによって動きが多い場合があります。

### <a name="closest-link-algorithms"></a>最も近いリンク アルゴリズム
これらは対話型コンテンツが少ない領域で最大の効果を発揮します。 ユーザーが何を操作しようとしているかを判断できる確率が高い場合は、ある程度のインテントを想定して、対象となる機能を補完することができます。

### <a name="backdating-and-postdating-actions"></a>バックと後処理のアクション
このメカニズムは、速度が必要なタスクに役立ちます。 ユーザーが一連のターゲットとアクティブ化の処理を高速に進めるときは、何らかのインテントを想定して、ユーザーが tap の前または少しの間にフォーカスを移動したターゲット (初期テストでは50ミリ秒前/後) に対して、不要な手順の実行を許可すると便利です。

### <a name="smoothing"></a>スムージング
このメカニズムは、自然なヘッド移動特性によってわずかなジッターと wobble を減らすことで、パスの移動に役立ちます。 パスモーションをスムーズにスムージングする場合は、時間の経過と共に、移動のサイズと距離を滑らかにします。

### <a name="magnetism"></a>磁性
このメカニズムは、最も近いリンクアルゴリズムのより一般的なバージョンであると考えることができます。これは、ターゲットに向かってカーソルを描画するか、またはユーザーの意図に応じて対話型レイアウトに関する知識を使用して、ユーザーがターゲットに近づくことになる可能性があるためです。 これは、小さいターゲットの場合は特に効果を発揮する可能性があります。

### <a name="focus-stickiness"></a>焦点の持続性
フォーカスのある近接要素にフォーカスを移すときに、フォーカスの持続性により、現在フォーカスがある要素にバイアスが適用されます。 これにより、自然なノイズを持つ2つの要素間の中間点で浮動フォーカスの切り替え動作を減らすことができます。


## <a name="see-also"></a>関連項目
* [視線ベースの操作](eye-gaze-interaction.md)
* [視線入力とドウェル](gaze-and-dwell.md)
* [手 - 直接操作](direct-manipulation.md)
* [手 - ジェスチャ](gaze-and-commit.md#composite-gestures)
* [手 - ポイントとコミット](point-and-commit.md)
* [本能的な操作](interaction-fundamentals.md)
* [音声入力](voice-input.md)



