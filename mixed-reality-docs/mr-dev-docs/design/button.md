---
title: Button
description: ボタンを使用して即時アクションをトリガーする方法について説明します。ボタンは、mixed reality の基本コンポーネントの1つです。
author: cre8ivepark
ms.author: dongpark
ms.date: 11/01/2019
ms.topic: article
keywords: 混合現実、コントロール、相互作用、ui、ux、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit、ボタン
ms.openlocfilehash: 9e4d0637d8c10c3cd23bd2ee1369fd57137af795
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759428"
---
# <a name="button"></a>Button

![Button](images/UX_Hero_Button.jpg)

ボタンを使用すると、ユーザーは、mixed reality エクスペリエンスで即時アクションをトリガーできます。 HoloLens 2 では、ボタンに視覚的な手掛かりと affordances があり、ユーザーとの相互作用の信頼を高めることができます。 

:::row:::
    :::column:::
       ![近接光効果が表示されているボタン](images/UX_Button_Affordance_ProximityLight.jpg)<br>
       **近接光**<br>
    :::column-end:::
    :::column:::
       ![フォーカスハイライト効果が表示された状態で選択されたボタン](images/UX_Button_Affordance_FocusHighlight.jpg)<br>
        **フォーカスの強調表示**<br>
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
       ![圧縮ケージ効果が表示された状態で押されたボタン](images/UX_Button_Affordance_Compression.jpg)<br>
       **ケージの圧縮**<br>
    :::column-end:::
    :::column:::
       ![トリガーのパルス効果が表示された状態で押されたボタン](images/UX_Button_Affordance_Pulse.jpg)<br>
        **トリガーのパルス**<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="button-in-mrtkmixed-reality-toolkit-for-unity"></a>Unity の MRTK (Mixed Reality Toolkit) のボタン
**[Mrtk For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、hololens 2 および hololens (第1世代) 用のシェルスタイルのボタンを含む、さまざまな種類のボタン prefabs が用意されています。 HoloLens 2 ボタンの prefab には、ユーザーの信頼度の向上に役立ついくつかの詳細な affordances が含まれています。

* 近接度に基づく強調表示
* フロントケージの圧縮
* トリガーに対するパルス効果。

* 詳細な手順とカスタマイズされた例については、 [Mrtk のボタン](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/button.md) をご覧ください。

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
