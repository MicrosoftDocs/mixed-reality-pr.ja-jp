---
title: 境界ボックスとアプリ バー
description: アプリバーは、ホログラムの境界の下端に表示される一連のボタンを含むオブジェクトレベルのメニューです。
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality、アプリバー、境界ボックス、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: aba2e318439fec2bbb9e986c2ff7cac7a8a5fb3a
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759438"
---
# <a name="bounding-box-and-app-bar"></a>境界ボックスとアプリ バー
![境界は、混合現実のオブジェクト操作の標準インターフェイスです。](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>境界ボックスとは何ですか。

境界は、混合現実のオブジェクト操作の標準インターフェイスです。 この機能により、オブジェクトが現在調整可能であることを視覚的に示すことができます。 HoloLens 2 では、境界ボックスはダイレクト操作と連動し、ユーザーの finger's 近接に応答します。 これは、ユーザーがオブジェクトからの距離を認識するのに役立つ視覚的フィードバックを示しています。

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>オブジェクトのスケーリング<br>
        境界ボックスのコーナーは、オブジェクトを拡張できることをユーザーに通知します。 ハンドルは、スケールを調整するために広く理解されているパターンに従います。 このビジュアルキューは、調整モードの外部では表示されない場合でも、オブジェクトの合計領域をユーザーに表示します。 この機能がないと、別のオブジェクトまたはサーフェイスにスナップされたオブジェクトは、そこには存在しない領域があるように動作しているように見えることがあります。<br>
        <br>
        *ビデオループ: 境界ボックスを使用したオブジェクトのスケーリング*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![境界ボックスを使用したオブジェクトのスケーリングの HoloLens ポイント](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>オブジェクトの回転<br>
        境界ボックスの端の垂直四角形 affordances は回転インジケーターです。 これにより、ユーザーは、配置されたホログラムをより細かく調整できます。 調整と拡大縮小だけでなく、回転も可能になりました。<br>
        <br>
        *ビデオループ: 境界ボックスを使用したオブジェクトの回転*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![境界ボックスを使用してオブジェクトを回転するための HoloLens のポイント](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>HoloLens 2 での視覚的フィードバック (手動による)<br>
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

**Unity アプリの開発については、 [Mixed Reality Toolkit の「境界ボックス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)」を参照してください。**

<br>

---

## <a name="what-is-the-app-bar"></a>アプリバーとは何ですか。

アプリバーはオブジェクトレベルのメニューであり、ホログラムの境界の下端に表示される一連のボタンが含まれています。 このパターンは、ユーザーがホログラムを削除および調整できるようにするためによく使用されます。 アプリバーは、主にユーザーの環境で配置されたオブジェクトを管理する方法として設計されました。 境界ボックスと組み合わせて使用すると、ユーザーはどこでも、どのようにオブジェクトが混合現実に向いているかを完全に制御できます。

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>アプリバーはユーザーに従います<br>
        このパターンは、世界でロックされているオブジェクトで使用されるため、ユーザーがオブジェクトの周りを移動すると、アプリバーは常にユーザーに最も近いオブジェクトの側に表示されます。 技術的には billboarding ではありませんが、この機能は実質的に同じ結果を実現します。 環境内の別の場所から使用できるようにするために、ユーザーの位置を occlude またはブロックすることを防止します。 <br>
        <br>
        *ビデオループ: ホログラムの周りをたどると、アプリバーが次のようになります。*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![ホログラムの周りを歩いています。 アプリバーは次のようになります。](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 用の MRTK (Mixed Reality Toolkit) の境界ボックス
**[Mrtk](https://github.com/Microsoft/MixedRealityToolkit-Unity)** には、境界ボックスとアプリバーのスクリプトと prefabs が用意されています。 境界ボックスを追加するには、BoundingBox.cs スクリプトを任意のオブジェクトに割り当てます。

* [MRTK-境界ボックス](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/ux-building-blocks/bounding-box.md)


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
