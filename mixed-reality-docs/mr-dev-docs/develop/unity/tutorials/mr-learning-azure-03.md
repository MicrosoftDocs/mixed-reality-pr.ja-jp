---
title: Azure Custom Vision の統合
description: このコースを完了すると、HoloLens 2 Mixed Reality アプリケーション内で Azure Custom Vision を実装する方法がわかります。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, HoloLens, HoloLens 2, Azure Custom Vision, Azure Cognitive Services, Azure クラウド サービス, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: aa3ad219ab2cd45b14d06881757ec776d3e098f3
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581931"
---
# <a name="3-integrating-azure-custom-vision"></a>3.Azure Custom Vision の統合

このチュートリアルでは、**Azure Custom Vision** の使用方法について説明します。一連の写真をアップロードし、それを "*追跡対象オブジェクト*" に関連付け、**Custom Vision** サービスにアップロードし、トレーニング プロセスを開始します。 次に、このサービスを使用し、Web カメラ フィードから写真をキャプチャすることで "*追跡対象オブジェクト*" を検出します。

## <a name="objectives"></a>目標

* Azure Custom Vision の基本を学習する
* このプロジェクトで Custom Vision を使用するようにシーンを設定する方法を学習する
* 画像のアップロード、トレーニング、検出を統合する方法を学習する

## <a name="understanding-azure-custom-vision"></a>Azure Custom Vision の概要

**Azure Custom Vision** は、**Cognitive Services** ファミリの一部であり、画像分類子のトレーニングに使用されます。 画像分類子とは、トレーニング済みモデルを使用して一致するタグを適用する AI サービスです。 この分類機能は、アプリケーションで "*追跡対象オブジェクト*" を検出するために使用されます。

詳細については、[Azure Custom Vision](/azure/cognitive-services/custom-vision-service/home) に関するページを参照してください。

## <a name="preparing-azure-custom-vision"></a>Azure Custom Vision の準備

開始する前に、Custom Vision プロジェクトを作成する必要があります。最短の方法は、Web ポータルを使用することです。

この [クイックスタート チュートリアル](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images)に従って、セクション「*画像をアップロードし、タグ付けする*」までアカウントとプロジェクトの設定を進めます。

> [!WARNING]
> モデルをトレーニングするには、少なくとも 2 つのタグと、タグごとに 5 つの画像が必要です。 このアプリケーションを使用するには、少なくとも 5 つの画像を含むタグを 1 つ作成し、後でトレーニング プロセスが失敗しないようにする必要があります。

## <a name="preparing-the-scene"></a>シーンの準備

[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  > **MRTK.Tutorials.AzureCloudServices** >  **[Prefabs]\(プレハブ\)**  > **Manager** フォルダーの順に移動します。

![ObjectDetectionManager プレハブへのパスを示す[Project]\(プロジェクト\) ウィンドウが表示された Unity](images/mr-learning-azure/tutorial3-section4-step1-1.png)

そこから、プレハブ **ObjectDetectionManager** をシーンの [Hierarchy]\(階層\) にドラッグします。

![ObjectDetectionManager スクリプト コンポーネント構成フィールドがインスペクターに表示された Unity](images/mr-learning-azure/tutorial3-section4-step1-2.png)

[Hierarchy]\(階層\) ウィンドウで、**ObjectDetectionManager** オブジェクトを見つけて選択します。
**ObjectDetectionManager** プレハブには **ObjectDetectionManager (script)** コンポーネントが含まれており、[Inspector]\(インスペクター\) ウィンドウからわかるように、いくつかの設定に依存しています。

## <a name="retrieving-azure-api-resource-credentials"></a>Azure api リソースの資格情報の取得

**ObjectDetectionManager (script)** の設定に必要な資格情報は、Azure portal と Custom Vision ポータルから取得できます。

### <a name="azure-portal"></a>Azure portal

このチュートリアルの「*シーンの準備*」セクションで作成した種類 **Cognitive Services** の Custom Vision リソースを探して見つけます。 *[Keys and Endpoint]\(キーとエンドポイント\)* をクリックして必要な資格情報を取得します。

### <a name="custom-vision-dashboard"></a>Custom Vision ダッシュボード

[Custom Vision](https://www.customvision.ai/projects) ダッシュボードで、このチュートリアル用に作成したプロジェクトを開き、ページの右上隅にある歯車アイコンをクリックして設定ページを開きます。 この右側の *[Resources]\(リソース\)* セクションで、必要な資格情報を確認できます。

**ObjectDetectionManager (script)** を正しく設定したら、シーンの [Hierarchy]\(階層\) で **SceneController** オブジェクトを見つけて選択します。

![SceneController スクリプト コンポーネント構成フィールドがインスペクターに表示された Unity](images/mr-learning-azure/tutorial3-section4-step1-3.png)

**SceneController** コンポーネントの *[Object Detection Manager]* フィールドが空であることがわかります。[Hierarchy]\(階層\) の **ObjectDetectionManager** をそのフィールドにドラッグし、シーンを保存します。

![SceneController スクリプト コンポーネントが構成された Unity](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a>画像の取得とアップロード

シーンを実行して **[Set Object]\(オブジェクトの設定\)** をクリックし、[前のレッスン](mr-learning-azure-02.md)で作成した **追跡対象オブジェクト** のいずれかの名前を入力します。 **[Object Card]\(オブジェクト カード\)** の下部にある **[Computer Vision]** ボタンをクリックします。

新しいウィンドウが開きます。ここでは、6 枚の写真を撮影し、画像認識のためにモデルをトレーニングする必要があります。 **[カメラ]** ボタンをクリックし、追跡するオブジェクトを見たときに AirTap を実行します。これを 6 回実行します。

> [!TIP]
> モデルのトレーニングを改善するには、角度と照明条件を変えて各画像を撮影してみてください。

十分な画像が得られたら、 **[トレーニング]** ボタンをクリックし、クラウドでモデルのトレーニング プロセスを開始します。 トレーニングをアクティブにすると、すべての画像がアップロードされ、トレーニングが開始されます。これには 1 分以上かかる場合があります。 メニュー内のメッセージは現在の進行状況を示します。完了と表示されたら、アプリケーションを停止できます

> [!TIP]
> 撮影された画像は、**ObjectDetectionManager (script)** によって Custom Vision サービスに直接アップロードされます。 また、Custom Vision API で画像の URL を受け取る方法もあります。演習として、**ObjectDetectionManager (script)** を変更し、代わりに画像を BLOB ストレージにアップロードすることができます。

## <a name="detect-objects"></a>オブジェクトを検出する

これで、トレーニング済みモデルをテストに配置し、アプリケーションを実行し、*メイン メニュー* から **[Search Object]\(オブジェクトの検索\)** をクリックして、問題の **追跡対象オブジェクト** の名前を入力することができます。 **[Object Card]\(オブジェクト カード\)** が表示されたら **[Custom Vision]** ボタンをクリックします。 ここから、**ObjectDetectionManager** によって、バックグラウンドでカメラから画像キャプチャの取得が開始され、進行状況がメニューに表示されます。 モデルのトレーニングに使用したオブジェクトにカメラを向け、少し待つと、オブジェクトが検出されることがわかります。

## <a name="congratulations"></a>結論

このチュートリアルでは、Azure Custom Vision を使用して画像をトレーニングし、分類サービスを使用して、関連する **追跡対象オブジェクト** と一致する画像を検出する方法を学習しました。

次のチュートリアルでは、Azure Spatial Anchors を使用して "*追跡対象オブジェクト*" を物理的な世界の場所にリンクする方法と、ユーザーを追跡対象オブジェクトのリンクされた場所に導くための矢印を表示する方法について学習します。

> [!div class="nextstepaction"]
> [次のチュートリアル: 4.Azure Spatial Anchors の統合](mr-learning-azure-04.md)