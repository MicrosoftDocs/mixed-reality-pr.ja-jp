---
title: Azure Cloud のチュートリアル - 4. Azure Spatial Anchors の統合
description: このコースでは、HoloLens 2 アプリケーション内で Azure Spatial Anchors を実装する方法を学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, HoloLens, HoloLens 2, Azure Spatial Anchors
ms.localizationpriority: high
ms.openlocfilehash: 2c10d7458fc956cb8974319cd5355260179f10b4
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91700090"
---
# <a name="4-integrating-azure-spatial-anchors"></a><span data-ttu-id="39426-105">4.Azure Spatial Anchors の統合</span><span class="sxs-lookup"><span data-stu-id="39426-105">4. Integrating Azure Spatial Anchors</span></span>

<span data-ttu-id="39426-106">このチュートリアルでは、 **Azure Spatial Anchors** を使用する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="39426-106">In this tutorial, you will learn how to use **Azure Spatial Anchors** .</span></span> <span data-ttu-id="39426-107">**追跡対象のオブジェクト** の場所を Azure Spatial Anchor として格納します。</span><span class="sxs-lookup"><span data-stu-id="39426-107">You will store the location of a **Tracked Object** as an Azure Spatial Anchor.</span></span> <span data-ttu-id="39426-108">アンカーに対してクエリを実行すると、場所を指す矢印が表示されます。</span><span class="sxs-lookup"><span data-stu-id="39426-108">Once you query for the anchor, an arrow will appear to guide you toward the location.</span></span>

## <a name="objectives"></a><span data-ttu-id="39426-109">目標</span><span class="sxs-lookup"><span data-stu-id="39426-109">Objectives</span></span>

* <span data-ttu-id="39426-110">Azure Spatial Anchors の基本を学習する。</span><span class="sxs-lookup"><span data-stu-id="39426-110">Learn the basics of Azure Spatial Anchors.</span></span>
* <span data-ttu-id="39426-111">このプロジェクトで Azure Spatial Anchors を使用するシーンをセットアップする方法を学習する。</span><span class="sxs-lookup"><span data-stu-id="39426-111">Learn how to set up the scene to use Azure Spatial Anchors in this project.</span></span>
* <span data-ttu-id="39426-112">場所の格納とクエリを統合する方法を学習する。</span><span class="sxs-lookup"><span data-stu-id="39426-112">Learn how to integrate storing and querying locations.</span></span>

## <a name="understanding-azure-spatial-anchors"></a><span data-ttu-id="39426-113">Azure Spatial Anchors について</span><span class="sxs-lookup"><span data-stu-id="39426-113">Understanding Azure Spatial Anchors</span></span>

 <span data-ttu-id="39426-114">**Azure Spatial Anchors** は Azure Cloud Services ファミリーに含まれており、アンカーの場所を保存するために使用します。</span><span class="sxs-lookup"><span data-stu-id="39426-114">**Azure Spatial Anchors** is part of the Azure Cloud Services family and is used to save anchor locations.</span></span> <span data-ttu-id="39426-115">保存されたアンカーの場所は、 *アンカー ID* に基づいてクラウドから取得できます。</span><span class="sxs-lookup"><span data-stu-id="39426-115">The saved anchor locations can be retrieved based on the *anchor ID* from the cloud.</span></span> <span data-ttu-id="39426-116">このアンカーの場所は、HoloLens、iOS、Android デバイスなどのマルチプラットフォーム デバイスで共有およびアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="39426-116">This anchor location can be shared and accessed by multi-platform devices like HoloLens, iOS, and Android devices.</span></span>

<span data-ttu-id="39426-117">[Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview) の詳細をご確認ください。</span><span class="sxs-lookup"><span data-stu-id="39426-117">Learn more about [Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/overview).</span></span>

## <a name="preparing-azure-spatial-anchors"></a><span data-ttu-id="39426-118">Azure Spatial Anchors の準備</span><span class="sxs-lookup"><span data-stu-id="39426-118">Preparing Azure Spatial Anchors</span></span>

<span data-ttu-id="39426-119">開始する前に、Azure portal で空間アンカー リソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39426-119">Before you can start, you have to create a spatial anchor resource in your Azure portal.</span></span>
<span data-ttu-id="39426-120">[空間アンカー リソース](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)を作成する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="39426-120">Learn how to make a [spatial anchor resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="39426-121">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="39426-121">Preparing the scene</span></span>

<span data-ttu-id="39426-122">このセクションでは、シーンを構成して、必要な変更を行う方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="39426-122">In this section, you will learn how to configure the scene and make the necessary changes.</span></span>

<span data-ttu-id="39426-123">[プロジェクト] ウィンドウで、 **[アセット] > [MRTK.Tutorials.AzureCloudServices] > [Prefabs]\(プレハブ\) > [マネージャー]** に移動します</span><span class="sxs-lookup"><span data-stu-id="39426-123">In the Project window, navigate to the **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step1-1.png)

<span data-ttu-id="39426-125">**[マネージャー]** フォルダーで、プレハブ **[Anchor Manager]** をシーン階層にドラッグ アンド ドロップします。</span><span class="sxs-lookup"><span data-stu-id="39426-125">From the **Manager** folder, drag and drop the prefab **Anchor Manager** into the scene Hierarchy.</span></span>

<span data-ttu-id="39426-126">階層内の **[Anchor Manager]** GameObject を選択すると、[インスペクター] セクションに **[Spatial Anchor Manager]** (Script) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="39426-126">Select **Anchor Manager** GameObject in the Hierarchy, and in the Inspector section, you will find **Spatial Anchor Manager** (Script).</span></span> <span data-ttu-id="39426-127">アカウント ID とキー フィールドを検索し、前の段階で前提条件に作成した資格情報を追加します。</span><span class="sxs-lookup"><span data-stu-id="39426-127">Find account ID and key field and add the credentials which you had created in the prerequisite in the earlier stage.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step2-1.png)

<span data-ttu-id="39426-129">ここで、シーン階層で **[Scene Controller]\(シーン コントローラー\)** オブジェクトを見つけて選択します。</span><span class="sxs-lookup"><span data-stu-id="39426-129">Now find the **Scene Controller** object in your scene Hierarchy and select it.</span></span> <span data-ttu-id="39426-130">**[Scene Controller]\(シーン コントローラー\)** インスペクターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="39426-130">You will see the **Scene Controller** Inspector.</span></span>

![mr-learning-azure](images/mr-learning-azure/tutorial4-section1-step3-1.png)

<span data-ttu-id="39426-132">**[Scene Controller]\(シーン コントローラー\)** コンポーネントの **[Anchor Manager]** フィールドが空であることを確認し、 **[Anchor Manager]** をシーンの階層からそのフィールドにドラッグ アンド ドロップしてシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="39426-132">You will observe that the **Anchor Manager** field in the **Scene Controller** component is empty, drag and drop the **Anchor Manager** from the Hierarchy in the scene into that field and save the scene.</span></span>

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="39426-133">アプリをビルドして HoloLens 2 にデプロイする</span><span class="sxs-lookup"><span data-stu-id="39426-133">Build and Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="39426-134">Azure Spatial Anchors は Unity では実行できないため、Azure Spatial Anchors の機能をテストするには、プロジェクトをお使いのデバイスにデプロイする必要があります。</span><span class="sxs-lookup"><span data-stu-id="39426-134">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="39426-135">HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、[HoloLens 2 にアプリをビルドする](mr-learning-base-02.md#building-your-application-to-your-hololens-2)手順に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39426-135">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="39426-136">HoloLens 2 でアプリを実行し、アプリ内の指示に従う</span><span class="sxs-lookup"><span data-stu-id="39426-136">Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

### <a name="create-an-anchor-to-store-a-location"></a><span data-ttu-id="39426-137">場所を格納するアンカーを作成する</span><span class="sxs-lookup"><span data-stu-id="39426-137">Create an anchor to store a location</span></span>

<span data-ttu-id="39426-138">このセクションでは、オブジェクトの場所を保存する方法を確認します。</span><span class="sxs-lookup"><span data-stu-id="39426-138">In this section you will see how to save the object location.</span></span>

<span data-ttu-id="39426-139">アプリケーションを実行し、エクスペリエンスのメイン メニューで **[Set Object]\(オブジェクトの設定\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39426-139">Run the application and click on **Set Object** in the main menu of the experience.</span></span>

<span data-ttu-id="39426-140">保存するオブジェクトの **名前** を指定し、 **[Set Object]\(オブジェクトの設定\)** をクリックして続行します。</span><span class="sxs-lookup"><span data-stu-id="39426-140">Give the **name** of the object you want to save and click on **Set Object** to continue.</span></span> <span data-ttu-id="39426-141">オブジェクトに関する詳細情報を追加するには、 **画像** を選択し、オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="39426-141">To add more information about the object, select the **image** , and describe the object.</span></span>

<span data-ttu-id="39426-142">場所を保存するには **[場所の保存]** をクリックします</span><span class="sxs-lookup"><span data-stu-id="39426-142">To save the location, click on **Save Location**</span></span>

<span data-ttu-id="39426-143">表示されている **アンカー ポインター** を移動して、保存する場所に配置することができます。</span><span class="sxs-lookup"><span data-stu-id="39426-143">You will see an **anchor pointer** that you can move and place on the location you want to save.</span></span> <span data-ttu-id="39426-144">その後、確認のポップアップが表示されます。</span><span class="sxs-lookup"><span data-stu-id="39426-144">After that, you will get a confirmation popup.</span></span> <span data-ttu-id="39426-145">場所を確認して保存する場合は、 **[はい]** をクリックします。そうでない場合は、 **[いいえ]** をクリックして場所をもう一度選択することによって、場所を変更できます。</span><span class="sxs-lookup"><span data-stu-id="39426-145">If you want to confirm and save the location, click on **Yes** ; otherwise, you can change the location by clicking on **No** and selecting the location again.</span></span>

<span data-ttu-id="39426-146">**[はい]** をクリックして場所を確認すると、場所とアンカー ID が Azure クラウド ストレージに保存されます。</span><span class="sxs-lookup"><span data-stu-id="39426-146">Once you confirm the location by clicking on **Yes** , the location and the Anchor ID will be saved in the Azure cloud storage.</span></span> <span data-ttu-id="39426-147">保存すると、オブジェクトの名前が指定された **オブジェクト タグ** がアンカーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="39426-147">Once it is saved, you will see the **Object tag**  in the anchor with the object's name.</span></span>

<span data-ttu-id="39426-148">これで、オブジェクトの場所が正常に保存されました。</span><span class="sxs-lookup"><span data-stu-id="39426-148">Now the object location is saved successfully.</span></span>

### <a name="query-for-finding-an-anchor-location"></a><span data-ttu-id="39426-149">アンカーの場所を検索するためのクエリ</span><span class="sxs-lookup"><span data-stu-id="39426-149">Query for finding an anchor location</span></span>

<span data-ttu-id="39426-150">アンカーの場所が正常に保存されたら、メイン メニューで **[オブジェクトの検索]** を選択してアンカーの場所を検索できるようになります。</span><span class="sxs-lookup"><span data-stu-id="39426-150">Once after you successfully saved the anchor location, now you can find the anchor location by selecting **Search Object** in the main menu.</span></span>

<span data-ttu-id="39426-151">**[オブジェクトの検索]** をクリックすると、新しいウィンドウが表示されます。そこで、検索するオブジェクトの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39426-151">After clicking on **Search Object** , a new window will pop up in which you should give the name of the object you want to search.</span></span>

<span data-ttu-id="39426-152">オブジェクトの名前を入力し、 **[オブジェクトの検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39426-152">Enter the name of the object and click on **Search Object** .</span></span> <span data-ttu-id="39426-153">オブジェクトが既に保存されていて、データベースに存在する場合は、以前に保存したオブジェクトのすべての詳細を含むオブジェクト カードが表示されます。</span><span class="sxs-lookup"><span data-stu-id="39426-153">If the object is saved previously and is found in the database, you will get the object card with all the details of the object you would have saved earlier.</span></span>

<span data-ttu-id="39426-154">これで、 **[Show Location]\(場所の表示\)** をクリックしてオブジェクトを検索できるようになります。</span><span class="sxs-lookup"><span data-stu-id="39426-154">Now you can click on **Show Location** to find the object.</span></span> <span data-ttu-id="39426-155">**[Show Location]\(場所の表示\)** をクリックすると、システムによってクラウド ストレージからオブジェクト アドレスに対してクエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="39426-155">Once you click on **Show Location** , the system will query the object address from the cloud storage.</span></span>

<span data-ttu-id="39426-156">場所を正常に取得できたら、 **矢印** に従ってオブジェクトの場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="39426-156">After successfully retrieving the location, an **arrow** will direct you towards the location of the object.</span></span> <span data-ttu-id="39426-157">オブジェクトの場所が見つかるまで、矢印マークに従います。</span><span class="sxs-lookup"><span data-stu-id="39426-157">Follow the arrow mark until you find the location of the object.</span></span>

<span data-ttu-id="39426-158">オブジェクトが見つかったら、オブジェクト名が上部に表示され、矢印マークが消えます。これで、 **オブジェクト タグ** をクリックしてオブジェクトの詳細を確認できます。</span><span class="sxs-lookup"><span data-stu-id="39426-158">Once you find the object, the object name will appear at the top, and the arrow mark will disappear, and now you can click on the **object tag** to see the details of the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="39426-159">結論</span><span class="sxs-lookup"><span data-stu-id="39426-159">Congratulations</span></span>

<span data-ttu-id="39426-160">このチュートリアルでは、Azure Spatial Anchors を使用して、Hololense 2 でオブジェクトの場所を保存および取得する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="39426-160">In this tutorial, you learned how Azure Spatial Anchors could save and retrieve the object location on Hololense 2.</span></span>

<span data-ttu-id="39426-161">最後のチュートリアルでは、 **Azure Bot Service** を使用して、アプリケーションの新しい相互作用方式として自然言語を追加する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="39426-161">In the final tutorial, you will learn how to use the **Azure Bot Service** to add natural language as a new interaction method for our application.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="39426-162">次のチュートリアル: 5.Azure Bot Service と LUIS との統合</span><span class="sxs-lookup"><span data-stu-id="39426-162">Next tutorial: 5. Integrating Azure Bot Service with LUIS</span></span>](mr-learning-azure-05.md)
