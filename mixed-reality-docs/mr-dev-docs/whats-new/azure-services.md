---
title: Azure mixed reality サービス
description: Azure mixed reality サービスを使用すると、HoloLens、iOS、および Android デバイス間でアクセスできる、3D、マルチユーザー、空間的に対応したアプリケーションを作成できます。
author: grbury
ms.author: grbury
ms.date: 08/21/2019
ms.topic: overview
keywords: 混合現実、開発、開発、HoloLens、Azure サービス、空間アンカー、音声、ビジョン、リモートレンダリング
ms.openlocfilehash: 4da1a6ffdc5c51927d12add8fb266aa2e0597bc7
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91690930"
---
# <a name="azure-mixed-reality-services"></a><span data-ttu-id="34794-104">Azure mixed reality サービス</span><span class="sxs-lookup"><span data-stu-id="34794-104">Azure mixed reality services</span></span>
<span data-ttu-id="34794-105">Azure mixed reality サービスを使用して、人間全員が、3次元の物理的な世界である専門家であることを、ロック解除します。</span><span class="sxs-lookup"><span data-stu-id="34794-105">Unlock what every human is an expert at—the three-dimensional, physical world around us—with Azure mixed reality services.</span></span> <span data-ttu-id="34794-106">仕事や世界のコンテキスト内でデジタル情報をキャプチャして表示することで、ユーザーがより効果的に作成、学習、共同作業を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="34794-106">Help people create, learn, and collaborate more effectively by capturing and surfacing digital information within the context of their work and world.</span></span> <span data-ttu-id="34794-107">3D をモバイルデバイス、ヘッドセット、およびその他のならではデバイスに移動します。</span><span class="sxs-lookup"><span data-stu-id="34794-107">Bring 3D to mobile devices, headsets, and other untethered devices.</span></span> <span data-ttu-id="34794-108">Azure を使用すると、最も機密性の高い情報を確実に保護することができます。</span><span class="sxs-lookup"><span data-stu-id="34794-108">Using Azure, help ensure that your most sensitive information is protected.</span></span>

## <a name="multi-user-spatially-aware-applications-using-spatial-anchors"></a><span data-ttu-id="34794-109">空間アンカーを使用した、マルチユーザー、空間的に対応するアプリケーション</span><span class="sxs-lookup"><span data-stu-id="34794-109">Multi-user, spatially aware applications using Spatial Anchors</span></span>

![ <span data-ttu-id="34794-110">Azure 空間アンカーの画像</span><span class="sxs-lookup"><span data-stu-id="34794-110">Azure Spatial Anchors image</span></span>](../design/images/AzureSpatialAnchors.jpg)

<span data-ttu-id="34794-111">空間アンカーを使用して、多対多ユーザー対応の混合現実アプリケーションを構築します。</span><span class="sxs-lookup"><span data-stu-id="34794-111">Build multi-user, spatially aware mixed reality applications using Spatial Anchors.</span></span> <span data-ttu-id="34794-112">HoloLens、iOS、および Android デバイス間でアクセスできる、関心のある正確なポイントをマップ、指定、およびリコールする、mixed reality アプリを作成します。</span><span class="sxs-lookup"><span data-stu-id="34794-112">Create mixed reality apps that map, designate, and recall precise points of interest that are accessible across HoloLens, iOS, and Android devices.</span></span> <span data-ttu-id="34794-113">ユーザーがより効率的に共同作業できるように、スペース間の検索を可能にします。</span><span class="sxs-lookup"><span data-stu-id="34794-113">Enable wayfinding across spaces to help your users collaborate more efficiently.</span></span>

[<span data-ttu-id="34794-114">Azure 空間アンカーを試す</span><span class="sxs-lookup"><span data-stu-id="34794-114">Try Azure Spatial Anchors</span></span>](https://docs.microsoft.com/azure/spatial-anchors)


## <a name="interactive-high-quality-3d-models-using-remote-rendering"></a><span data-ttu-id="34794-115">リモートレンダリングを使用した対話型の高品質な3D モデル</span><span class="sxs-lookup"><span data-stu-id="34794-115">Interactive, high-quality 3D models using Remote Rendering</span></span>

![ <span data-ttu-id="34794-116">リモートレンダリングイメージ</span><span class="sxs-lookup"><span data-stu-id="34794-116">Remote rendering image</span></span>](../design/images/RemoteRendering.jpg)

<span data-ttu-id="34794-117">すべての詳細情報が重要なシナリオでは、工業プラント管理、トラックエンジンなどの資産の設計レビュー、事前オペレーティングの手術計画などがあります。</span><span class="sxs-lookup"><span data-stu-id="34794-117">In scenarios where every detail matters—industrial plant management, design review for assets like truck engines, pre-operative surgery planning, and more—3D visualization brings that detail to life.</span></span> <span data-ttu-id="34794-118">デザイナー、エンジニア、医師、および学生が複雑な情報をより深く理解し、適切な呼び出しを行うのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="34794-118">It's what helps designers, engineers, doctors, and students better understand complex information and make the right call.</span></span>

<span data-ttu-id="34794-119">現在、モバイルデバイスと mixed reality ヘッドセットで高品質の3D モデルを実行するには、多くの場合、3D モデルを "確認して"、ターゲットハードウェアで実行するのに十分な単純化を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="34794-119">Today, to run high-quality 3D models on mobile devices and mixed reality headsets, you often need to "decimate" 3D models and simplify them enough to run on target hardware.</span></span> <span data-ttu-id="34794-120">しかし、この簡略化により、主要なビジネスおよび設計上の決定に必要な重要な詳細が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="34794-120">But this simplification can result in a loss of important detail that's needed in key business and design decisions.</span></span>

<span data-ttu-id="34794-121">Azure リモートレンダリングプレビューを使用して、すべての詳細情報を保持し、品質を損なうことなく、対話型の高品質の3D モデルをならではします。</span><span class="sxs-lookup"><span data-stu-id="34794-121">Bring interactive, high-quality 3D models to untethered devices with every detail intact and no compromise on quality using Azure Remote Rendering Preview.</span></span>

[<span data-ttu-id="34794-122">Azure リモートレンダリングの詳細情報</span><span class="sxs-lookup"><span data-stu-id="34794-122">Learn more about Azure Remote Rendering</span></span>](https://azure.microsoft.com/services/remote-rendering)


## <a name="cognitive-services"></a><span data-ttu-id="34794-123">Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="34794-123">Cognitive Services</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="34794-124">[![スピーチ](images/speech.jpg)](https://docs.microsoft.com/azure/cognitive-services/speech-service/)</span><span class="sxs-lookup"><span data-stu-id="34794-124">[![Speech](images/speech.jpg)](https://docs.microsoft.com/azure/cognitive-services/speech-service/)</span></span>
    :::column-end:::
    :::column span="2":::
        ### <a name="speech"></a>[<span data-ttu-id="34794-125">Speech</span><span class="sxs-lookup"><span data-stu-id="34794-125">Speech</span></span>](https://docs.microsoft.com/azure/cognitive-services/speech-service/)
        <span data-ttu-id="34794-126">音声認識を使用して、音声処理機能を任意のアプリやサービスに統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="34794-126">Discover how Speech enables the integration of speech processing capabilities into any app or service.</span></span> <span data-ttu-id="34794-127">読み上げられた言語をテキストに変換したり、標準的な (またはカスタマイズ可能な) 音声フォントを使用して、テキストから自然に発音した音声を生成します。</span><span class="sxs-lookup"><span data-stu-id="34794-127">Convert spoken language into text or produce natural sounding speech from text using standard (or customizable) voice fonts.</span></span> <span data-ttu-id="34794-128">任意のサービスを無料で試すことができ、次の機能を使用して音声対応のアプリとサービスをすばやく作成できます。</span><span class="sxs-lookup"><span data-stu-id="34794-128">Try any service free—and quickly build speech-enabled apps and services with the following capabilities.</span></span>
    :::column-end:::
:::row-end:::

---

:::row:::
    :::column:::
       <span data-ttu-id="34794-129">[![視覚](images/vision.jpg)](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)</span><span class="sxs-lookup"><span data-stu-id="34794-129">[![Vision](images/vision.jpg)](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)</span></span>
    :::column-end:::
    :::column span="2":::
        ### <a name="vision"></a>[<span data-ttu-id="34794-130">Vision</span><span class="sxs-lookup"><span data-stu-id="34794-130">Vision</span></span>](https://docs.microsoft.com/azure/cognitive-services/computer-vision/)
        <span data-ttu-id="34794-131">画像、ビデオ、およびデジタルインクコンテンツを認識し、識別し、キャプションし、インデックスを作成し、モデレートします。アプリやサービスが画像、ビデオ、およびデジタルインク内のコンテンツを正確に特定して分析する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="34794-131">Recognize, identify, caption, index, and moderate your pictures, videos, and digital ink content.Learn how Vision makes it possible for apps and services to accurately identify and analyze content within images, videos, and digital ink.</span></span>
    :::column-end:::
:::row-end:::


## <a name="see-also"></a><span data-ttu-id="34794-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="34794-132">See also</span></span>

* <span data-ttu-id="34794-133">HoloLens 2-1 の azure 空間アンカーチュートリアル[Azure 空間アンカーの](../mrlearning-asa-ch1.md)概要</span><span class="sxs-lookup"><span data-stu-id="34794-133">Azure Spatial Anchor tutorials for HoloLens 2 - [1 of 3 Getting started with Azure Spatial Anchors](../mrlearning-asa-ch1.md)</span></span>
* <span data-ttu-id="34794-134">HoloLens 2- [1、音声認識と議事録の統合と使用](../develop/unity/tutorials/mrlearning-speechSDK-ch1.md)に関する Azure Speech Services チュートリアル</span><span class="sxs-lookup"><span data-stu-id="34794-134">Azure Speech Services tutorials for HoloLens 2 - [1 of 4 Integrating and using speech recognition and transcription](../develop/unity/tutorials/mrlearning-speechSDK-ch1.md)</span></span>
