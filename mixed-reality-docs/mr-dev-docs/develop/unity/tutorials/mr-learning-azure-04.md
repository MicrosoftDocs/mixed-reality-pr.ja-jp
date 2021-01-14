---
title: Azure Spatial Anchors の統合
description: このコースでは、HoloLens 2 アプリケーション内で Azure Spatial Anchors を実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, Hololens 2, Azure Spatial Anchors, Azure クラウド サービス, Azure Custom Vision, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 50e5bccf09e03ebda8057dbb3ca9d83fc01694bd
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008172"
---
# <a name="4-integrating-azure-spatial-anchors"></a><span data-ttu-id="4a9d1-104">4.Azure Spatial Anchors の統合</span><span class="sxs-lookup"><span data-stu-id="4a9d1-104">4. Integrating Azure Spatial Anchors</span></span>

<span data-ttu-id="4a9d1-105">このチュートリアルでは、**Azure Spatial Anchors** を使用する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-105">In this tutorial, you will learn how to use **Azure Spatial Anchors**.</span></span> <span data-ttu-id="4a9d1-106">**追跡対象のオブジェクト** の場所を Azure Spatial Anchor として格納します。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-106">You will store the location of a **Tracked Object** as an Azure Spatial Anchor.</span></span> <span data-ttu-id="4a9d1-107">アンカーに対してクエリを実行すると、場所を指す矢印が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-107">Once you query for the anchor, an arrow will appear to guide you toward the location.</span></span>

## <a name="objectives"></a><span data-ttu-id="4a9d1-108">目標</span><span class="sxs-lookup"><span data-stu-id="4a9d1-108">Objectives</span></span>

* <span data-ttu-id="4a9d1-109">Azure Spatial Anchors の基本を学習する。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-109">Learn the basics of Azure Spatial Anchors.</span></span>
* <span data-ttu-id="4a9d1-110">このプロジェクトで Azure Spatial Anchors を使用するシーンをセットアップする方法を学習する。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-110">Learn how to set up the scene to use Azure Spatial Anchors in this project.</span></span>
* <span data-ttu-id="4a9d1-111">場所の格納とクエリを統合する方法を学習する。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-111">Learn how to integrate storing and querying locations.</span></span>

## <a name="understanding-azure-spatial-anchors"></a><span data-ttu-id="4a9d1-112">Azure Spatial Anchors について</span><span class="sxs-lookup"><span data-stu-id="4a9d1-112">Understanding Azure Spatial Anchors</span></span>

 <span data-ttu-id="4a9d1-113">**Azure Spatial Anchors** は Azure Cloud Services ファミリーに含まれており、アンカーの場所を保存するために使用します。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-113">**Azure Spatial Anchors** is part of the Azure Cloud Services family and is used to save anchor locations.</span></span> <span data-ttu-id="4a9d1-114">保存されたアンカーの場所は、*アンカー ID* に基づいてクラウドから取得できます。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-114">The saved anchor locations can be retrieved based on the *anchor ID* from the cloud.</span></span> <span data-ttu-id="4a9d1-115">このアンカーの場所は、HoloLens、iOS、Android デバイスなどのマルチプラットフォーム デバイスで共有およびアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-115">This anchor location can be shared and accessed by multi-platform devices like HoloLens, iOS, and Android devices.</span></span>

<span data-ttu-id="4a9d1-116">[Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview) の詳細をご確認ください。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-116">Learn more about [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview).</span></span>

## <a name="preparing-azure-spatial-anchors"></a><span data-ttu-id="4a9d1-117">Azure Spatial Anchors の準備</span><span class="sxs-lookup"><span data-stu-id="4a9d1-117">Preparing Azure Spatial Anchors</span></span>

<span data-ttu-id="4a9d1-118">開始する前に、Azure portal で空間アンカー リソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-118">Before you can start, you have to create a spatial anchor resource in your Azure portal.</span></span>
<span data-ttu-id="4a9d1-119">[空間アンカー リソース](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)を作成する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-119">Learn how to make a [spatial anchor resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="4a9d1-120">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="4a9d1-120">Preparing the scene</span></span>

<span data-ttu-id="4a9d1-121">このセクションでは、シーンを構成して、必要な変更を行う方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-121">In this section, you will learn how to configure the scene and make the necessary changes.</span></span>

<span data-ttu-id="4a9d1-122">[プロジェクト] ウィンドウで、 **[アセット] > [MRTK.Tutorials.AzureCloudServices] > [Prefabs]\(プレハブ\) > [マネージャー]** に移動します</span><span class="sxs-lookup"><span data-stu-id="4a9d1-122">In the Project window, navigate to the **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span></span>

![AnchorManager プレハブが選択されている Unity](images/mr-learning-azure/tutorial4-section1-step1-1.png)

<span data-ttu-id="4a9d1-124">**[マネージャー]** フォルダーで、プレハブ **[Anchor Manager]** をシーン階層にドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-124">From the **Manager** folder, drag and drop the prefab **Anchor Manager** into the scene Hierarchy.</span></span>

<span data-ttu-id="4a9d1-125">階層内の **[Anchor Manager]** GameObject を選択すると、[インスペクター] セクションに **[Spatial Anchor Manager]** (Script) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-125">Select **Anchor Manager** GameObject in the Hierarchy, and in the Inspector section, you will find **Spatial Anchor Manager** (Script).</span></span> <span data-ttu-id="4a9d1-126">アカウント ID とキー フィールドを検索し、前の段階で前提条件に作成した資格情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-126">Find account ID and key field and add the credentials which you had created in the prerequisite in the earlier stage.</span></span>

![新しく追加された AnchorManager プレハブがまだ選択されている Unity](images/mr-learning-azure/tutorial4-section1-step2-1.png)

<span data-ttu-id="4a9d1-128">ここで、シーン階層で **[Scene Controller]\(シーン コントローラー\)** オブジェクトを見つけて選択します。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-128">Now find the **Scene Controller** object in your scene Hierarchy and select it.</span></span> <span data-ttu-id="4a9d1-129">**[Scene Controller]\(シーン コントローラー\)** インスペクターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-129">You will see the **Scene Controller** Inspector.</span></span>

![SceneController スクリプト コンポーネントが構成された Unity](images/mr-learning-azure/tutorial4-section1-step3-1.png)

<span data-ttu-id="4a9d1-131">**[Scene Controller]\(シーン コントローラー\)** コンポーネントの **[Anchor Manager]** フィールドが空であることを確認し、 **[Anchor Manager]** をシーンの階層からそのフィールドにドラッグ アンド ドロップしてシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-131">You will observe that the **Anchor Manager** field in the **Scene Controller** component is empty, drag and drop the **Anchor Manager** from the Hierarchy in the scene into that field and save the scene.</span></span>

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="4a9d1-132">アプリをビルドして HoloLens 2 にデプロイする</span><span class="sxs-lookup"><span data-stu-id="4a9d1-132">Build and Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="4a9d1-133">Azure Spatial Anchors は Unity では実行できないため、Azure Spatial Anchors の機能をテストするには、プロジェクトをお使いのデバイスにデプロイする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-133">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="4a9d1-134">HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、[HoloLens 2 用のアプリケーションの構築](mr-learning-base-02.md#building-and-deploying-to-your-hololens-2)の手順に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-134">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2]((mr-learning-base-02.md#building-and-deploying-to-your-hololens-2) instructions.</span></span>

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="4a9d1-135">HoloLens 2 でアプリを実行し、アプリ内の指示に従う</span><span class="sxs-lookup"><span data-stu-id="4a9d1-135">Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

### <a name="create-an-anchor-to-store-a-location"></a><span data-ttu-id="4a9d1-136">場所を格納するアンカーを作成する</span><span class="sxs-lookup"><span data-stu-id="4a9d1-136">Create an anchor to store a location</span></span>

<span data-ttu-id="4a9d1-137">このセクションでは、オブジェクトの場所を保存する方法を確認します。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-137">In this section you will see how to save the object location.</span></span>

<span data-ttu-id="4a9d1-138">アプリケーションを実行し、エクスペリエンスのメイン メニューで **[Set Object]\(オブジェクトの設定\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-138">Run the application and click on **Set Object** in the main menu of the experience.</span></span>

<span data-ttu-id="4a9d1-139">保存するオブジェクトの **名前** を指定し、 **[Set Object]\(オブジェクトの設定\)** をクリックして続行します。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-139">Give the **name** of the object you want to save and click on **Set Object** to continue.</span></span> <span data-ttu-id="4a9d1-140">オブジェクトに関する詳細情報を追加するには、**画像** を選択し、オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-140">To add more information about the object, select the **image**, and describe the object.</span></span>

<span data-ttu-id="4a9d1-141">場所を保存するには **[場所の保存]** をクリックします</span><span class="sxs-lookup"><span data-stu-id="4a9d1-141">To save the location, click on **Save Location**</span></span>

<span data-ttu-id="4a9d1-142">表示されている **アンカー ポインター** を移動して、保存する場所に配置することができます。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-142">You will see an **anchor pointer** that you can move and place on the location you want to save.</span></span> <span data-ttu-id="4a9d1-143">その後、確認のポップアップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-143">After that, you will get a confirmation popup.</span></span> <span data-ttu-id="4a9d1-144">場所を確認して保存する場合は、 **[はい]** をクリックします。そうでない場合は、 **[いいえ]** をクリックして場所をもう一度選択することによって、場所を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-144">If you want to confirm and save the location, click on **Yes**; otherwise, you can change the location by clicking on **No** and selecting the location again.</span></span>

<span data-ttu-id="4a9d1-145">**[はい]** をクリックして場所を確認すると、場所とアンカー ID が Azure クラウド ストレージに保存されます。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-145">Once you confirm the location by clicking on **Yes**, the location and the Anchor ID will be saved in the Azure cloud storage.</span></span> <span data-ttu-id="4a9d1-146">保存すると、オブジェクトの名前が指定された **オブジェクト タグ** がアンカーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-146">Once it is saved, you will see the **Object tag**  in the anchor with the object's name.</span></span>

<span data-ttu-id="4a9d1-147">これで、オブジェクトの場所が正常に保存されました。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-147">Now the object location is saved successfully.</span></span>

### <a name="query-for-finding-an-anchor-location"></a><span data-ttu-id="4a9d1-148">アンカーの場所を検索するためのクエリ</span><span class="sxs-lookup"><span data-stu-id="4a9d1-148">Query for finding an anchor location</span></span>

<span data-ttu-id="4a9d1-149">アンカーの場所が正常に保存されたら、メイン メニューで **[オブジェクトの検索]** を選択してアンカーの場所を検索できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-149">Once after you successfully saved the anchor location, now you can find the anchor location by selecting **Search Object** in the main menu.</span></span>

<span data-ttu-id="4a9d1-150">**[オブジェクトの検索]** をクリックすると、新しいウィンドウが表示されます。そこで、検索するオブジェクトの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-150">After clicking on **Search Object**, a new window will pop up in which you should give the name of the object you want to search.</span></span>

<span data-ttu-id="4a9d1-151">オブジェクトの名前を入力し、 **[オブジェクトの検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-151">Enter the name of the object and click on **Search Object**.</span></span> <span data-ttu-id="4a9d1-152">オブジェクトが既に保存されていて、データベースに存在する場合は、以前に保存したオブジェクトのすべての詳細を含むオブジェクト カードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-152">If the object is saved previously and is found in the database, you will get the object card with all the details of the object you would have saved earlier.</span></span>

<span data-ttu-id="4a9d1-153">これで、 **[Show Location]\(場所の表示\)** をクリックしてオブジェクトを検索できるようになります。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-153">Now you can click on **Show Location** to find the object.</span></span> <span data-ttu-id="4a9d1-154">**[Show Location]\(場所の表示\)** をクリックすると、システムによってクラウド ストレージからオブジェクト アドレスに対してクエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-154">Once you click on **Show Location**, the system will query the object address from the cloud storage.</span></span>

<span data-ttu-id="4a9d1-155">場所を正常に取得できたら、**矢印** に従ってオブジェクトの場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-155">After successfully retrieving the location, an **arrow** will direct you towards the location of the object.</span></span> <span data-ttu-id="4a9d1-156">オブジェクトの場所が見つかるまで、矢印マークに従います。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-156">Follow the arrow mark until you find the location of the object.</span></span>

<span data-ttu-id="4a9d1-157">オブジェクトが見つかったら、オブジェクト名が上部に表示され、矢印マークが消えます。これで、**オブジェクト タグ** をクリックしてオブジェクトの詳細を確認できます。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-157">Once you find the object, the object name will appear at the top, and the arrow mark will disappear, and now you can click on the **object tag** to see the details of the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="4a9d1-158">結論</span><span class="sxs-lookup"><span data-stu-id="4a9d1-158">Congratulations</span></span>

<span data-ttu-id="4a9d1-159">このチュートリアルでは、Azure Spatial Anchors を使用して、Hololense 2 でオブジェクトの場所を保存および取得する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-159">In this tutorial, you learned how Azure Spatial Anchors could save and retrieve the object location on Hololense 2.</span></span>

<span data-ttu-id="4a9d1-160">最後のチュートリアルでは、**Azure Bot Service** を使用して、アプリケーションの新しい相互作用方式として自然言語を追加する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="4a9d1-160">In the final tutorial, you will learn how to use the **Azure Bot Service** to add natural language as a new interaction method for our application.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4a9d1-161">次のチュートリアル: 5.Azure Bot Service と LUIS との統合</span><span class="sxs-lookup"><span data-stu-id="4a9d1-161">Next tutorial: 5. Integrating Azure Bot Service with LUIS</span></span>](mr-learning-azure-05.md)
