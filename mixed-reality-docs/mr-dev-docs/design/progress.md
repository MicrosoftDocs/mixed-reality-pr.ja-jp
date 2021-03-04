---
title: 進行状況を表示する
description: 実行時間の長い操作が混合の現実のアプリで実行されていることをユーザーにフィードバックするために、進行状況の制御がどのように役立つかについて説明します。
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality、デザイン、コントロール、ui、ux、進行状況インジケーター、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: f323559c9a50a6f01636f0aba0bddc93b547125b
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101759848"
---
# <a name="progress-indicator"></a>進捗状況インジケーター

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

プログレスコントロールは、実行時間の長い操作が進行中であるというフィードバックを提供します。 進行状況インジケーターが表示されると、ユーザーは待機時間を確認でき、アプリと対話できなくなります。

<br>

---

## <a name="types-of-progress"></a>プログレス コントロールの種類

何が起こっているかについてユーザー情報を提供することが重要です。 混合環境では、ユーザーは、アプリに視覚的なフィードバックがない場合に、物理的な環境やオブジェクトによって簡単に気を付けることができます。 データの読み込み中やシーンの更新など、数秒かかる状況では、視覚的なインジケーターを表示することをお勧めします。 操作が進行しているユーザーを表示するには、 **進行状況バー** または **進行状況のリング** の2つのオプションがあります。

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>進行状況バー<br>
        進行状況バーには、タスクの完了率が表示されます。 このメソッドは、期間が既知 (有限) の操作中に使用する必要がありますが、その進行状況では、ユーザーとアプリとの対話をブロックすることはできません。<br>
        <br>
        *イメージ: HoloLens での進行状況バーの例*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens での進行状況バーの例](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>進行状況リング<br>
        進行状況のリングは不確定状態であるため、操作が完了するまでユーザーの操作がブロックされるときに使用する必要があります。<br>
        <br>
        *イメージ: HoloLens での進行状況リングの例*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens デバイスでの進行状況リングの例](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>カスタムオブジェクトの進行状況<br>
        独自のカスタム 2D/3D オブジェクトを使用して進行状況の制御をカスタマイズすることで、アプリの個性とブランド id に追加できます。<br>
        <br>
        *イメージ: HoloLens でのカスタムメッシュの例の進行状況*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![HoloLens でのカスタムメッシュの例の進行状況](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>ベスト プラクティス

* ユーザーが簡単にヘッドを空の領域に移動してコンテキストを失うことがあるため、 [billboarding またはタグ](billboarding-and-tag-along.md) を進行状況の表示に密に結合します。 ユーザーが何も表示できない場合、アプリがクラッシュしたように見えることがあります。 Billboarding とタグは、進行状況の prefab に組み込まれています。
* ユーザーに対して何が起こっているかに関するステータス情報を常に提供するのが適切です。 Progress prefab には、状態を提供するための Windows 標準のリングの種類の進行状況など、さまざまな視覚スタイルが用意されています。 また、進行状況のスタイルをアプリのブランドに合わせる必要がある場合は、アニメーションでカスタムメッシュを使用することもできます。

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>Unity 用 MRTK (Mixed Reality Toolkit) の進行状況インジケーター

* [MRTK-進行状況インジケーター prefabs](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK-シーン移行サービス](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/features/extensions/scene-transition-service.md)


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
