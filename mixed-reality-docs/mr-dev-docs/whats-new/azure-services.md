---
title: Azure Mixed Reality サービス
description: Azure mixed reality サービスを使用して、HoloLens、iOS、および Android デバイス間でアクセスできる、3D、マルチユーザー、および空間的に対応するアプリケーションを作成します。
author: grbury
ms.author: grbury
ms.date: 08/21/2019
ms.topic: overview
keywords: 混合現実、開発、開発、HoloLens、Azure サービス、空間アンカー、音声、ビジョン、リモートレンダリング
ms.openlocfilehash: c25584bd77495ab4e45713d2ad25b1b7b4e526e9
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757570"
---
# <a name="azure-mixed-reality-services"></a>Azure Mixed Reality サービス
Azure の複合現実サービスを利用して、あらゆる人間が慣れ親しんだ世界、つまり私たちを取り巻く 3 次元の物理世界を解き放ちましょう。 デジタル情報のキャプチャと表示により、より効果的に作成、学習、共同作業を行うことができます。 モバイル デバイスやヘッドセットなどの非接続式デバイスでの 3D が実現します。 Azure を使用することで、機密性の高い情報を確実に保護できます。

## <a name="multi-user-spatially-aware-applications-using-spatial-anchors"></a>空間アンカーを使用した、マルチユーザー、空間的に対応するアプリケーション

![ Azure Spatial Anchors の画像](../design/images/AzureSpatialAnchors.jpg)

空間アンカーを使用して、多対多ユーザー対応の混合現実アプリケーションを構築します。 HoloLens、iOS、および Android デバイス間でアクセスできる正確なポイントをマップ、指定、およびリコールする、mixed reality アプリを作成します。 ユーザーがより効率的に共同作業できるように、スペース間の検索を可能にします。

[Azure 空間アンカーを試す](https://docs.microsoft.com/azure/spatial-anchors)


## <a name="interactive-high-quality-3d-models-using-remote-rendering"></a>リモートレンダリングを使用した対話型の高品質な3D モデル

![ リモート レンダリングの画像](../design/images/RemoteRendering.jpg)

シナリオには、すべての詳細情報が含まれています。たとえば、工業プラント管理、トラックエンジンのような資産の設計レビュー、事前オペレーティングの手術計画などがあります。 デザイナー、エンジニア、医師、および学生が複雑な情報を理解し、適切な呼び出しを行うのに役立ちます。

現在、モバイルデバイスや mixed reality ヘッドセットで高品質の3D モデルを実行している場合は、ターゲットハードウェアで実行するのに十分な3D モデルを簡素化する必要があります。 この簡略化により、主要なビジネスおよび設計上の決定に必要な重要な詳細が失われる可能性があります。

Azure リモートレンダリングプレビューを使用すると、対話型の高品質な3D モデルにより、すべての詳細情報を保持した状態でデバイスをならではすることができ、品質の侵害もありません。

[Azure リモートレンダリングの詳細情報](https://azure.microsoft.com/services/remote-rendering)

## <a name="cognitive-services"></a>Cognitive Services

:::row:::
    :::column:::
       [![空の灰色の背景を持つ音声バブルアイコン](images/speech.jpg)](https://docs.microsoft.com/azure/cognitive-services/speech-service/)
    :::column-end:::
    :::column span="2":::
        ### <a name="speech"></a>[Speech](https://docs.microsoft.com/azure/cognitive-services/speech-service/)
        音声を使用して、音声処理機能を任意のアプリやサービスに統合する方法をご紹介します。 読み上げられた言語をテキストに変換したり、標準の (またはカスタマイズ可能な) 音声フォントを使用してテキストから自然に聞こえる音声を生成したりできます。 お好みのサービスを無料で試用していただけます。次の機能により、音声対応のアプリとサービスをすばやく構築できます。
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       [![空の灰色の背景を持つ視覚視点グラフィック](images/vision.jpg)](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)
    :::column-end:::
    :::column span="2":::
        ### <a name="vision"></a>[Vision](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)
        画像、ビデオ、デジタル インク コンテンツを認識および識別し、キャプションの挿入、インデックスの作成、モデレーションを行います。視覚サービスを使用して、アプリやサービスで画像、ビデオ、デジタル インク内のコンテンツを正確に識別および分析する方法について説明します。
    :::column-end:::
:::row-end:::


## <a name="see-also"></a>関連項目

* HoloLens 2 向けの Azure Spatial Anchors チュートリアル - [Azure Spatial Anchors での作業の開始 (1/3 章)](../mrlearning-asa-ch1.md)
* HoloLens 2 向けの Azure Speech Services チュートリアル - [音声認識と文字起こしの統合と使用 (1/4 章)](../develop/unity/tutorials/mrlearning-speechSDK-ch1.md)
