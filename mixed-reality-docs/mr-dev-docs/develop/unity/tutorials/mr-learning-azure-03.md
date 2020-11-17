---
title: Azure Cloud チュートリアル - 3. Azure Custom Vision の統合
description: このコースでは、HoloLens 2 アプリケーション内で Azure Custom Vision を実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: mixed reality, unity, チュートリアル, hololens, hololens 2, azure custom vision, azure cognitive services
ms.localizationpriority: high
ms.openlocfilehash: 9a6cccf9c1a7d2547ed5ddacfc4841d2f4d1609b
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353270"
---
# <a name="3-integrating-azure-custom-vision"></a><span data-ttu-id="fdab6-105">3.Azure Custom Vision の統合</span><span class="sxs-lookup"><span data-stu-id="fdab6-105">3. Integrating Azure Custom Vision</span></span>

<span data-ttu-id="fdab6-106">このチュートリアルでは、**Azure Custom Vision** の使用方法について説明します。一連の写真をアップロードし、それを "*追跡対象オブジェクト*" に関連付け、**Custom Vision** サービスにアップロードし、トレーニング プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="fdab6-106">In this tutorial, you will learn how to use **Azure Custom Vision**.You will upload a set of photos to associate it with a *Tracked Object*, upload them to the **Custom Vision** service and start the training process.</span></span> <span data-ttu-id="fdab6-107">次に、このサービスを使用し、Web カメラ フィードから写真をキャプチャすることで "*追跡対象オブジェクト*" を検出します。</span><span class="sxs-lookup"><span data-stu-id="fdab6-107">Then you will use the service to detect the *Tracked Object* by capturing photos from the webcam feed.</span></span>

## <a name="objectives"></a><span data-ttu-id="fdab6-108">目標</span><span class="sxs-lookup"><span data-stu-id="fdab6-108">Objectives</span></span>

* <span data-ttu-id="fdab6-109">Azure Custom Vision の基本を学習する</span><span class="sxs-lookup"><span data-stu-id="fdab6-109">Learn the basics about Azure Custom Vision</span></span>
* <span data-ttu-id="fdab6-110">このプロジェクトで Custom Vision を使用するようにシーンを設定する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="fdab6-110">Learn how to setup the scene to use Custom Vision in this project</span></span>
* <span data-ttu-id="fdab6-111">画像のアップロード、トレーニング、検出を統合する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="fdab6-111">Learn how to integrate upload, train and detect images</span></span>

## <a name="understanding-azure-custom-vision"></a><span data-ttu-id="fdab6-112">Azure Custom Vision の概要</span><span class="sxs-lookup"><span data-stu-id="fdab6-112">Understanding Azure Custom Vision</span></span>

<span data-ttu-id="fdab6-113">**Azure Custom Vision** は、**Cognitive Services** ファミリの一部であり、画像分類子のトレーニングに使用されます。</span><span class="sxs-lookup"><span data-stu-id="fdab6-113">**Azure Custom Vision** is part of the **Cognitive Services** family and is used to train image classifiers.</span></span> <span data-ttu-id="fdab6-114">画像分類子とは、トレーニング済みモデルを使用して一致するタグを適用する AI サービスです。</span><span class="sxs-lookup"><span data-stu-id="fdab6-114">The image classifier is an AI service that uses the trained model to apply matching tags.</span></span> <span data-ttu-id="fdab6-115">この分類機能は、アプリケーションで "*追跡対象オブジェクト*" を検出するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="fdab6-115">This classification feature will be used by our application to detect *Tracked Objects*.</span></span>

<span data-ttu-id="fdab6-116">詳細については、[Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fdab6-116">Learn more about [Azure Custom Vision](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/home).</span></span>

## <a name="preparing-azure-custom-vision"></a><span data-ttu-id="fdab6-117">Azure Custom Vision の準備</span><span class="sxs-lookup"><span data-stu-id="fdab6-117">Preparing Azure Custom Vision</span></span>

<span data-ttu-id="fdab6-118">開始する前に、Custom Vision プロジェクトを作成する必要があります。最短の方法は、Web ポータルを使用することです。</span><span class="sxs-lookup"><span data-stu-id="fdab6-118">Before you can start, you have to create a custom vision project, the fastest way is by using the web portal.</span></span>

<span data-ttu-id="fdab6-119">この [クイックスタート チュートリアル](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images)に従って、セクション「*画像をアップロードし、タグ付けする*」までアカウントとプロジェクトの設定を進めます。</span><span class="sxs-lookup"><span data-stu-id="fdab6-119">Follow this [quickstart tutorial](https://docs.microsoft.com/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) to setup your account and project until section *Upload and tag images*.</span></span>

> [!WARNING]
> <span data-ttu-id="fdab6-120">モデルをトレーニングするには、少なくとも 2 つのタグと、タグごとに 5 つの画像が必要です。</span><span class="sxs-lookup"><span data-stu-id="fdab6-120">To train a model you need to have at least 2 tags and 5 images per tag.</span></span> <span data-ttu-id="fdab6-121">このアプリケーションを使用するには、少なくとも 5 つの画像を含むタグを 1 つ作成し、後でトレーニング プロセスが失敗しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fdab6-121">To use this application you should at least create one tag with 5 images, so that the training process later won't fail.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="fdab6-122">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="fdab6-122">Preparing the scene</span></span>

<span data-ttu-id="fdab6-123">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  > **MRTK.Tutorials.AzureCloudServices** >  **[Prefabs]\(プレハブ\)**  > **Manager** フォルダーの順に移動します。</span><span class="sxs-lookup"><span data-stu-id="fdab6-123">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![ObjectDetectionManager プレハブへのパスを示す[Project]\(プロジェクト\) ウィンドウが表示された Unity](images/mr-learning-azure/tutorial3-section4-step1-1.png)

<span data-ttu-id="fdab6-125">そこから、プレハブ **ObjectDetectionManager** をシーンの [Hierarchy]\(階層\) にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="fdab6-125">From there drag the prefab **ObjectDetectionManager** into the scene Hierarchy.</span></span>

![ObjectDetectionManager スクリプト コンポーネント構成フィールドがインスペクターに表示された Unity](images/mr-learning-azure/tutorial3-section4-step1-2.png)

<span data-ttu-id="fdab6-127">[Hierarchy]\(階層\) ウィンドウで、**ObjectDetectionManager** オブジェクトを見つけて選択します。</span><span class="sxs-lookup"><span data-stu-id="fdab6-127">In the Hierarchy window locate the **ObjectDetectionManager** object and select it.</span></span>
<span data-ttu-id="fdab6-128">**ObjectDetectionManager** プレハブには **ObjectDetectionManager (script)** コンポーネントが含まれており、[Inspector]\(インスペクター\) ウィンドウからわかるように、いくつかの設定に依存しています。</span><span class="sxs-lookup"><span data-stu-id="fdab6-128">The **ObjectDetectionManager** prefab contains the **ObjectDetectionManager (script)** component and as you can see from the Inspector window it depends on several settings.</span></span>

## <a name="retrieving-azure-api-resource-credentials"></a><span data-ttu-id="fdab6-129">Azure api リソースの資格情報の取得</span><span class="sxs-lookup"><span data-stu-id="fdab6-129">Retrieving Azure api resource credentials</span></span>

<span data-ttu-id="fdab6-130">**ObjectDetectionManager (script)** の設定に必要な資格情報は、Azure portal と Custom Vision ポータルから取得できます。</span><span class="sxs-lookup"><span data-stu-id="fdab6-130">The necessary credentials for the **ObjectDetectionManager (script)** settings can be retrieve from the Azure Portal and the custom vision portal.</span></span>

### <a name="azure-portal"></a><span data-ttu-id="fdab6-131">Azure portal</span><span class="sxs-lookup"><span data-stu-id="fdab6-131">Azure Portal</span></span>

<span data-ttu-id="fdab6-132">このチュートリアルの「*シーンの準備*」セクションで作成した種類 **Cognitive Services** の Custom Vision リソースを探して見つけます。</span><span class="sxs-lookup"><span data-stu-id="fdab6-132">Find and locate the custom vision resource of type **Cognitive Services** you have created in the *Preparing the scene* section of this tutorial.</span></span> <span data-ttu-id="fdab6-133">*[Keys and Endpoint]\(キーとエンドポイント\)* をクリックして必要な資格情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="fdab6-133">There click on *Keys and Endpoint* to retrieve the necessary credentials.</span></span>

### <a name="custom-vision-dashboard"></a><span data-ttu-id="fdab6-134">Custom Vision ダッシュボード</span><span class="sxs-lookup"><span data-stu-id="fdab6-134">Custom Vision Dashboard</span></span>

<span data-ttu-id="fdab6-135">[Custom Vision](https://www.customvision.ai/projects) ダッシュボードで、このチュートリアル用に作成したプロジェクトを開き、ページの右上隅にある歯車アイコンをクリックして設定ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="fdab6-135">In the [custom vision](https://www.customvision.ai/projects) dashboard, open the project you have created for this tutorial and click on the top right corner of the page on the gear icon to open the settings page.</span></span> <span data-ttu-id="fdab6-136">この右側の *[Resources]\(リソース\)* セクションで、必要な資格情報を確認できます。</span><span class="sxs-lookup"><span data-stu-id="fdab6-136">Here on the right hand *Resources* section you will find the necessary credentials.</span></span>

<span data-ttu-id="fdab6-137">**ObjectDetectionManager (script)** を正しく設定したら、シーンの [Hierarchy]\(階層\) で **SceneController** オブジェクトを見つけて選択します。</span><span class="sxs-lookup"><span data-stu-id="fdab6-137">Now with the **ObjectDetectionManager (script)** setup correctly, find the **SceneController** object in your scene Hierarchy and select it.</span></span>

![SceneController スクリプト コンポーネント構成フィールドがインスペクターに表示された Unity](images/mr-learning-azure/tutorial3-section4-step1-3.png)

<span data-ttu-id="fdab6-139">**SceneController** コンポーネントの *[Object Detection Manager]* フィールドが空であることがわかります。[Hierarchy]\(階層\) の **ObjectDetectionManager** をそのフィールドにドラッグし、シーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="fdab6-139">You see *Object Detection Manager* field in the **SceneController** component is empty, drag the **ObjectDetectionManager** from the Hierarchy into that field and save the scene.</span></span>

![SceneController スクリプト コンポーネントが構成された Unity](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a><span data-ttu-id="fdab6-141">画像の取得とアップロード</span><span class="sxs-lookup"><span data-stu-id="fdab6-141">Take and upload images</span></span>

<span data-ttu-id="fdab6-142">シーンを実行して **[Set Object]\(オブジェクトの設定\)** をクリックし、[前のレッスン](mr-learning-azure-02.md)で作成した **追跡対象オブジェクト** のいずれかの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="fdab6-142">Run the scene and click on **Set Object**, type in the name for one of the **Tracked Objects** you have created in the [previous lesson](mr-learning-azure-02.md).</span></span> <span data-ttu-id="fdab6-143">**[Object Card]\(オブジェクト カード\)** の下部にある **[Computer Vision]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fdab6-143">Now click on **Computer Vision** button you can find at the bottom of the **Object Card**.</span></span>

<span data-ttu-id="fdab6-144">新しいウィンドウが開きます。ここでは、6 枚の写真を撮影し、画像認識のためにモデルをトレーニングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fdab6-144">A new window will open where you have to take six photos to train the model for image recognition.</span></span> <span data-ttu-id="fdab6-145">**[カメラ]** ボタンをクリックし、追跡するオブジェクトを見たときに AirTap を実行します。これを 6 回実行します。</span><span class="sxs-lookup"><span data-stu-id="fdab6-145">Click on the **Camera** button and perform an AirTap when you look on the object you like to track, do this six times.</span></span>

> [!TIP]
> <span data-ttu-id="fdab6-146">モデルのトレーニングを改善するには、角度と照明条件を変えて各画像を撮影してみてください。</span><span class="sxs-lookup"><span data-stu-id="fdab6-146">To improve the model training try to take each image from different angles and lighting conditions.</span></span>

<span data-ttu-id="fdab6-147">十分な画像が得られたら、 **[トレーニング]** ボタンをクリックし、クラウドでモデルのトレーニング プロセスを開始します。</span><span class="sxs-lookup"><span data-stu-id="fdab6-147">Once you have enough images click on the **Train** button to start the model training process in the cloud.</span></span> <span data-ttu-id="fdab6-148">トレーニングをアクティブにすると、すべての画像がアップロードされ、トレーニングが開始されます。これには 1 分以上かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fdab6-148">Activating the training will upload all images and then start the training, this can take up to a minute or more.</span></span> <span data-ttu-id="fdab6-149">メニュー内のメッセージは現在の進行状況を示します。完了と表示されたら、アプリケーションを停止できます</span><span class="sxs-lookup"><span data-stu-id="fdab6-149">A message inside the menu indicates the current progress and once it indicates the completion you can stop the application</span></span>

> [!TIP]
> <span data-ttu-id="fdab6-150">撮影された画像は、**ObjectDetectionManager (script)** によって Custom Vision サービスに直接アップロードされます。</span><span class="sxs-lookup"><span data-stu-id="fdab6-150">The **ObjectDetectionManager (script)** directly uploads taken images into the Custom Vision service.</span></span> <span data-ttu-id="fdab6-151">また、Custom Vision API で画像の URL を受け取る方法もあります。演習として、**ObjectDetectionManager (script)** を変更し、代わりに画像を BLOB ストレージにアップロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="fdab6-151">As an alternative the custom vision API accepts URLs to the images, as an exercise you can modify the **ObjectDetectionManager (script)** to upload the images to a Blob storage instead.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="fdab6-152">オブジェクトを検出する</span><span class="sxs-lookup"><span data-stu-id="fdab6-152">Detect objects</span></span>

<span data-ttu-id="fdab6-153">これで、トレーニング済みモデルをテストに配置し、アプリケーションを実行し、*メイン メニュー* から **[Search Object]\(オブジェクトの検索\)** をクリックして、問題の **追跡対象オブジェクト** の名前を入力することができます。</span><span class="sxs-lookup"><span data-stu-id="fdab6-153">You can now put the trained model to the test, run the application and from the *main menu* click on **Search Object** and type the name of the **Tracked Object** in question.</span></span> <span data-ttu-id="fdab6-154">**[Object Card]\(オブジェクト カード\)** が表示されたら **[Custom Vision]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fdab6-154">The **Object Card** will appear and click on the **Custom Vision** button.</span></span> <span data-ttu-id="fdab6-155">ここから、**ObjectDetectionManager** によって、バックグラウンドでカメラから画像キャプチャの取得が開始され、進行状況がメニューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="fdab6-155">From here the **ObjectDetectionManager** will start taking image captures in the background from the camera and the progress will be indicated on the menu.</span></span> <span data-ttu-id="fdab6-156">モデルのトレーニングに使用したオブジェクトにカメラを向け、少し待つと、オブジェクトが検出されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="fdab6-156">Point the camera to the object you used to train the model and you will see that after a short while it will detect the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="fdab6-157">結論</span><span class="sxs-lookup"><span data-stu-id="fdab6-157">Congratulations</span></span>

<span data-ttu-id="fdab6-158">このチュートリアルでは、Azure Custom Vision を使用して画像をトレーニングし、分類サービスを使用して、関連する **追跡対象オブジェクト** と一致する画像を検出する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="fdab6-158">In this tutorial you learned how Azure Custom Vision can be used to train images and use the classification service to detect images that match the associated **Tracked Object**.</span></span>

<span data-ttu-id="fdab6-159">次のチュートリアルでは、Azure Spatial Anchors を使用して "*追跡対象オブジェクト*" を物理的な世界の場所にリンクする方法と、ユーザーを追跡対象オブジェクトのリンクされた場所に導くための矢印を表示する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="fdab6-159">In the next tutorial you will learn how to use Azure Spatial Anchors to link a *Tracked Object* with a location in the physical world and how to display an arrow that will guide the user back to the Tracked Object's linked location.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fdab6-160">次のチュートリアル: 4.Azure Spatial Anchors の統合</span><span class="sxs-lookup"><span data-stu-id="fdab6-160">Next tutorial: 4. Integrating Azure Spatial Anchors</span></span>](mr-learning-azure-04.md)
