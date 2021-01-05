---
title: 手とモーション コントローラー
description: ハンズオンとモーションコントローラーの相互作用モデルについて説明します。これにより、仮想と物理の間の境界が削除されます。
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 混合現実、ハンズオン、モーションコントローラー、相互作用、設計、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: 1dffdd5f3471993dfdb5e504e4c5b87ec0bfef7d
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847323"
---
# <a name="hands-and-motion-controllers"></a>手とモーション コントローラー

## <a name="scenarios"></a>シナリオ

[相互作用の概要](interaction-fundamentals.md)を読み終えたら、ハンドアンドモーションコントローラーの相互作用モデルを選択します。 これは、ユーザーが holographic 世界と対話するために2人のユーザーを使用する必要があるアプリケーションを開発していることを意味します。 アプリケーションは、仮想と物理の間の境界を削除するという目標を達成します。

次のようなシナリオが考えられます。
* コンテンツを表示および制御する UI アフォーダンスを使用してインフォメーション ワーカーに 2D 仮想画面を提供する
* ファクトリアセンブリラインのためのファーストラインワーカーのチュートリアルとガイドの提供
* 医療プロフェッショナルを支援および教育するためのプロフェッショナルなツールを開発する  
* 3D 仮想オブジェクトを使用して実世界を装飾する、または第 2 の世界を創造する 
* 現実世界を背景として使用して、場所ベースのサービスとゲームを作成する

<br>

---

## <a name="hands-and-motion-controllers-modalities"></a>ハンドアンドモーションコントローラー感覚様相

:::row:::
    :::column:::
       [![手による直接操作](images/hands-and-controllers-direct-manipulation.jpg)](direct-manipulation.md)<br>
       ### <a name="direct-manipulation-with-handsbr"></a>[手で直接操作](direct-manipulation.md)<br>
       ユーザーがホログラムにタッチしたり操作したりするために使用できるハンドパワーを適用しています。 日常の生活エクスペリエンスを使用し、適切な視覚的 affordances を提供することで、ユーザーは、実際のオブジェクトを操作するのと同じ方法を使用して仮想マシンと対話できます。
    :::column-end:::
    :::column:::
       [![手によるポイントとコミット](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handsbr"></a>[手を使ったポイントとコミット](point-and-commit.md)<br>
        このモダリティによって、ユーザーは距離内でホログラムを操作できるようになります。 これにより、ユーザーは周囲を最大限に活用できるようになります。 ユーザーは、ホログラムを任意の場所に配置し、どこからでもアクセスすることができます。 2D および3D ホログラムの制御と操作を行うためのメンタルモデルとジェスチャは、直接操作のものと非常に同期されています。
    :::column-end:::
    :::column:::
       [![モーション コントローラー](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersbr"></a>[モーション コントローラー](motion-controllers.md)<br>
       モーションコントローラーは、ユーザーの物理的な機能を拡張して、ある程度の距離にわたって正確な対話を行い、一方または両方を使用します。 これらのハードウェアアクセサリは、一般的に使用される多くの対話へのショートカットを提供し、さまざまなアクションに対して footed、tactile フィードバックを提供します。 現在、モーションコントローラーは、Windows Mixed Reality (WMR) シナリオでのみ使用できます。 
    :::column-end:::
:::row-end:::

<br>

---

## <a name="see-also"></a>関連項目
* [頭の視線入力とコミット](gaze-and-commit.md)
* [ヘッド視線入力とドウェル](gaze-and-dwell.md)
* [手で直接操作](direct-manipulation.md)
* [手を使ったポイントとコミット](point-and-commit.md)
* [ハンズフリー](hands-free.md)
