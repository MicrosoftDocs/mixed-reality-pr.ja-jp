---
title: 手とモーション コントローラー
description: ハンズオンとモーションコントローラーの相互作用モデルについて説明します。これにより、仮想と物理の間の境界が削除されます。
author: shengkait
ms.author: shentan
ms.date: 04/26/2019
ms.topic: article
keywords: 混合現実、ハンド、モーションコントローラー、相互作用、設計
ms.openlocfilehash: 8b2ed6127708204d0c4a537c56b2225ff26e0d0f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686890"
---
# <a name="hands-and-motion-controllers"></a>手とモーション コントローラー
## <a name="scenarios"></a>シナリオ
[相互作用の概要](interaction-fundamentals.md)を読み取った後にこの相互作用モデルを採用することを選択した場合は、ユーザーが holographic 世界と対話するために2人のユーザーを使用する必要があるアプリケーションを開発していることを意味します。 アプリケーションは、仮想と物理の間の境界を削除するという目標を達成します。

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
       これは、ユーザーがホログラムを直接操作したり操作したりできるようにするための、手の力を活用したモダリティです。 日常的な経験を活用し、適切な視覚的 affordances を提供することにより、ユーザーは、実際のオブジェクトを操作するのと同じ方法を使用して仮想マシンとやり取りすることができます。
    :::column-end:::
    :::column:::
       [![手によるポイントとコミット](images/hands-and-controllers-point-and-commit.jpg)](point-and-commit.md)<br>
        ### <a name="point-and-commit-with-handsbr"></a>[手を使ったポイントとコミット](point-and-commit.md)<br>
        このモダリティによって、ユーザーは距離内でホログラムを操作できるようになります。 これにより、ユーザーは周囲を最大限に活用できるようになります。 ユーザーは、ホログラムを任意の場所に配置し、どこからでもアクセスすることができます。 2D および3D ホログラムの制御と操作を行うためのメンタルモデルとジェスチャは、直接操作のものと非常に同期されています。
    :::column-end:::
    :::column:::
       [![モーション コントローラー](images/hands-and-controllers-motion-controllers.jpg)](motion-controllers.md)<br>
       ### <a name="motion-controllersbr"></a>[モーション コントローラー](motion-controllers.md)<br>
       モーションコントローラーは、ユーザーの物理的な機能を拡張するツールであり、1つまたは両方のハンズを使用しながら、広範囲の距離にわたる正確な対話を実現します。 これらのハードウェアアクセサリは、一般的に使用される多くの対話にショートカットを提供し、さまざまなアクションに対して tactile のフィードバックを提供します。 現在、モーションコントローラーは、Windows Mixed Reality (WMR) シナリオでのみ使用できます。 
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
