---
layout: LandingPage
title: Azure 複合現実クラウド サービスの概要
description: Unity または Unreal のアプリケーションに統合できるすべての Azure Mixed Reality クラウド サービスについて説明します。
author: hferrone
ms.author: v-haferr
ms.date: 12/9/2020
ms.topic: overview
ms.localizationpriority: high
keywords: Mixed Reality, 開発する, 開発, HoloLens, クラウド サービス, Azure, リモート レンダリング, 空間アンカー, Cognitive Services, 認知, Unity, 機械学習, 音声翻訳, コンピューター ビジョン, Microsoft Graph
ms.openlocfilehash: abd1515b587842dbccb1747b606059e190559480
ms.sourcegitcommit: 07d6a5c19c9f6ffd0316bce5629ab0e185e1d542
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2021
ms.locfileid: "99973072"
---
# <a name="azure-mixed-reality-cloud-services-overview"></a>Azure 複合現実クラウド サービスの概要

![ Azure Spatial Anchors の画像](../design/images/AzureSpatialAnchors.jpg)

Azure の複合現実サービスを利用して、あらゆる人間が慣れ親しんだ世界、つまり私たちを取り巻く 3 次元の物理世界を解き放ちましょう。 ユーザーの職場や環境のコンテキスト内でデジタル情報を収集、表示することで、開発、学習、共同作業の効率性の向上を支援できます。 モバイル デバイスやヘッドセットなどの非接続式デバイスでの 3D が実現します。 Azure を使用することで、機密性の高い情報を確実に保護できます。

## <a name="mixed-reality-services"></a>複合現実サービス

**Azure Remote Rendering** や **Azure Spatial Anchors** などの Mixed Reality クラウド サービスを使用すると、開発者はさまざまなプラットフォームで魅力的なイマーシブ エクスペリエンスを構築することができます。 これらのサービスを使用すると、3D トレーニング、設備の予測メンテナンス、デザイン レビュー用のアプリケーションを作成する際、プロジェクトに空間認識を統合でき、このすべてをユーザーの環境のコンテキストで行うことができます。

### <a name="azure-remote-rendering"></a>Azure Remote Rendering

[Azure Remote Rendering](https://docs.microsoft.com/azure/remote-rendering/) (ARR) は、非常に複雑な 3D モデルをリアル タイムでレンダリングし、デバイスにストリーム配信するためのサービスです。 ARR は現在パブリック プレビューの段階であり、HoloLens 2 または Windows デスクトップ PC を対象とした Unity またはネイティブ C++ のプロジェクトに追加できます。

<br>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Intro-to-Azure-Mixed-Reality-Services-Azure-Remote-Rendering/player]

ARR は、レンダリング計算能力が低い非接続式デバイスで実行されるあらゆる Mixed Reality アプリケーションに不可欠なコンポーネントです。 次のエンジンのモデルを比較対照の例として取り上げます。忠実度の高い左側のモデルには 1,800 万を超える三角形がありますが、忠実度の低い右側のモデルには約 20 万しかありません。 トラックのエンジンなどの資産の設計レビューや工業プラント管理、術前の手術計画など、あらゆる細部にこだわらなければならないシナリオでは、3D 視覚化によって、その細部を忠実に再現できます。 これは、デザイナー、エンジニア、医師、学生が複雑な情報をより深く理解し、適切な判断を行うために役立ちます。 しかし、このような簡略化を行うと、ビジネス上および設計上の主要な決定に必要とされる、重要な詳細情報が失われる可能性があります。

![Unity ショーケース アプリでの Azure Remote Rendering の例](images/arr-engine.png)

ARR では、レンダリング ワークロードをクラウド内のハイエンド GPU に移動することで、この問題を解決します。 これにより、クラウドでホストされるグラフィックス エンジンによって画像が引き継がれ、ビデオ ストリームとしてエンコードされ、そのモデルがターゲット デバイスに直接ストリーム配信されます。 

* 1 つのハイエンド GPU では処理しきれない複雑なモデルの場合は、ARR がワークロードを複数の GPU に分散し、その結果を 1 つの画像としてマージするので、ユーザーからはプロセスが完全に透過的になります。 

これに加えて、ARR では、アプリで使用できるユーザー インターフェイスの種類が制限されていません。 ローカルでレンダリングされたコンテンツは、次の画像に示されているように、フレームの端で自動的にリモート画像と組み合わされます。

![Unity ショーケース アプリでの Azure Remote Rendering の例](images/showcase-app.png)

### <a name="azure-spatial-anchors"></a>Azure Spatial Anchors

[Azure Spatial Anchors](https://docs.microsoft.com /azure/spatial-anchors/) は、空間認識 Mixed Reality アプリケーションを構築するための、クロスプラットフォームのサービスです。 Azure Spatial Anchors を使用すると、複数デバイス間でのホログラフィック コンテンツのマッピング、保持、共有を、現実世界のスケールで実現できます。 

Azure Spatial Anchors は、次のような Mixed Reality の一般的なユースケース向けに独自にカスタマイズされたソリューションです。
* **ウェイファインディング**: 2 つ以上の空間アンカーを接続して、ユーザーが操作する必要のあるタスク リストまたは関心のあるポイントを作成できます。
* **マルチユーザー エクスペリエンス**: 同じ仮想空間内のオブジェクトを操作することで、ユーザー間で動作のやり取りを行えます。
* **現実世界での仮想コンテンツの保持**: ユーザーは、他のサポートされているデバイスでも表示可能な仮想オブジェクトを現実世界に配置できます。

![Azure Spatial Anchors の例](images/persistence.gif)

このサービスは多くの環境で開発でき、デバイスとプラットフォームの大規模なグループにデプロイできます。 そのため、利用できるプラットフォームの一覧には次のように多くのものが含まれます。
* Unity for HoloLens
* Unity for iOS
* Unity for Android
* ネイティブ iOS
* ネイティブ Android
* HoloLens 向け C++/WinRT および DirectX
* Xamarin for iOS
* Xamarin for Android

## <a name="cognitive-services"></a>Cognitive Services

:::row:::
    :::column:::
       [![Speech](../whats-new/images/speech.jpg)](/azure/cognitive-services/speech-service/)
    :::column-end:::
    :::column span="2":::
        ### <a name="speech"></a>[Speech](/azure/cognitive-services/speech-service/)
        音声を使用して、音声処理機能を任意のアプリやサービスに統合する方法をご紹介します。 読み上げられた言語をテキストに変換したり、標準の (またはカスタマイズ可能な) 音声フォントを使用してテキストから自然に聞こえる音声を生成したりできます。 お好みのサービスを無料で試用していただけます。次の機能により、音声対応のアプリとサービスをすばやく構築できます。
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       [![視覚](../whats-new/images/vision.jpg)](/azure/cognitive-services/computer-vision/)
    :::column-end:::
    :::column span="2":::
        ### <a name="vision"></a>[Vision](/azure/cognitive-services/computer-vision/)
        画像、ビデオ、デジタル インク コンテンツを認識および識別し、キャプションの挿入、インデックスの作成、モデレーションを行います。視覚サービスを使用して、アプリやサービスで画像、ビデオ、デジタル インク内のコンテンツを正確に識別および分析する方法について説明します。
    :::column-end:::
:::row-end:::


## <a name="standalone-unity-services"></a>スタンドアロンの Unity サービス

以下に一覧表示されているスタンドアロンのサービスは Mixed Reality には該当しませんが、さまざまな開発状況で役に立つ可能性があります。 Unity を使用して開発している場合は、これらの各サービスを新規または既存のプロジェクトに統合することができます。

### <a name="device-support"></a>デバイス サポート
<table>
    <tr>
        <td><strong>Azure クラウド サービス</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 世代)</strong></a></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td><a href="unity/tutorials/mr-azure-301.md">言語翻訳</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302.md">Computer Vision</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-302b.md">Custom Vision</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-303.md">クロスデバイス通知</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-304.md">顔認識</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-305.md">Functions と Storage</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-306.md">ビデオのストリーム配信</a></td>
        <td>❌</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-307.md">Machine Learning</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-308.md"mr-azure-308.md">Functions と Storage</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-309.md">Application Insights</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-310.md">物体検出</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-311.md">Microsoft Graph</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
    <tr>
        <td><a href="unity/tutorials/mr-azure-312.md">ボットの統合</a></td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="see-also"></a>関連項目

* HoloLens 2 向けの Azure Spatial Anchors チュートリアル - [Azure Spatial Anchors での作業の開始 (1/3 章)](./unity/tutorials/mr-learning-asa-02.md)
* HoloLens 2 向けの Azure Speech Services チュートリアル - [音声認識と文字起こしの統合と使用 (1/4 章)](../develop/unity/tutorials/mrlearning-speechSDK-ch1.md)
