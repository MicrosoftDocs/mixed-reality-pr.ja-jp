---
title: Azure Storage の統合
description: このコースを完了すると、Azure Table Storage と Azure Blob Storage を HoloLens 2 アプリケーション内に実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, HoloLens, HoloLens 2, Azure Storage, Azure クラウド サービス, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: fc049fc54674b4f7387ae937f142b9b4afe44e66
ms.sourcegitcommit: daa45a19a3a353334380cda78fee7fa149f0e48b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2021
ms.locfileid: "98981711"
---
# <a name="2-integrating-azure-storage"></a><span data-ttu-id="86e78-104">2.Azure Storage の統合</span><span class="sxs-lookup"><span data-stu-id="86e78-104">2. Integrating Azure storage</span></span>

<span data-ttu-id="86e78-105">このチュートリアルでは、エンティティ データを Azure Table Storage に、そしてサムネイル画像を Azure Blob Storage に保存する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="86e78-105">In this tutorial, you will learn how to save entity data to Azure Table storage and thumbnail images to Azure Blob storage.</span></span> <span data-ttu-id="86e78-106">この機能を使用すると、ID、名前、サムネイル画像などのデータを含む "*追跡オブジェクト*" を、セッションおよびデバイスを介してクラウドとの間で保存および取得することができます。</span><span class="sxs-lookup"><span data-stu-id="86e78-106">This feature will allow us to store and retrieve *Tracked Objects* with data like ID, Name, Thumbnail Image, etc. across sessions and devices to the cloud.</span></span>

## <a name="objectives"></a><span data-ttu-id="86e78-107">目標</span><span class="sxs-lookup"><span data-stu-id="86e78-107">Objectives</span></span>

* <span data-ttu-id="86e78-108">Azure Storage の基本について学習する</span><span class="sxs-lookup"><span data-stu-id="86e78-108">Learn the basics about Azure storage</span></span>
* <span data-ttu-id="86e78-109">Table Storage に対してデータの格納、変更、および取得を行う方法を学習する</span><span class="sxs-lookup"><span data-stu-id="86e78-109">Learn how to store, modify and retrieve data from Table storage</span></span>
* <span data-ttu-id="86e78-110">Blob Storage に対して画像の格納および削除を行う方法を学習する</span><span class="sxs-lookup"><span data-stu-id="86e78-110">Learn how to store and delete images from Blob storage</span></span>

## <a name="understanding-azure-storage"></a><span data-ttu-id="86e78-111">Azure Storage について</span><span class="sxs-lookup"><span data-stu-id="86e78-111">Understanding Azure storage</span></span>

<span data-ttu-id="86e78-112">**Azure Storage** は、クラウドでの Microsoft のストレージ ソリューションであり、多くのシナリオと要件に対応できます。</span><span class="sxs-lookup"><span data-stu-id="86e78-112">**Azure storage** is a Microsoft storage solution on the cloud that can cover many scenarios and requirements.</span></span> <span data-ttu-id="86e78-113">非常に大規模なスケーリングが可能で、開発者が簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="86e78-113">It can scale massively and is easily approachable by developers.</span></span> <span data-ttu-id="86e78-114">すべてのサービスを、**Azure ストレージ アカウント** の包括的なサービスとして利用することができます。</span><span class="sxs-lookup"><span data-stu-id="86e78-114">All services can be consumed under the umbrella of an **Azure storage Account**.</span></span> <span data-ttu-id="86e78-115">このユース ケースでは、*Table Storage* と *Blob Storage* を使用します。</span><span class="sxs-lookup"><span data-stu-id="86e78-115">For our use case we will use *Table storage* and *Blob storage*.</span></span>

<span data-ttu-id="86e78-116">詳細については、[Azure ストレージ サービス](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-overview)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="86e78-116">Learn more about [Azure storage services](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-overview).</span></span>

### <a name="azure-table-storage"></a><span data-ttu-id="86e78-117">Azure Table Storage</span><span class="sxs-lookup"><span data-stu-id="86e78-117">Azure Table storage</span></span>

<span data-ttu-id="86e78-118">このサービスを使用すると、NoSQL 形式でデータを格納することができます。このプロジェクトでは、それを使用して、名前、説明、空間アンカー ID など、"*追跡オブジェクト*" に関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="86e78-118">This services allows us to store data in a NoSQL fashion, in this project we will use it to store information about the *Tracked Object* such as: name, description, spatial anchor id, and more.</span></span>

<span data-ttu-id="86e78-119">デモ アプリケーションのコンテキストでは、2 つのテーブルが必要です。1 つは、プロジェクトに関する情報とトレーニング済みモデルの状態に関する情報 (詳細についてはチュートリアル「[Azure Custom Vision の統合](mr-learning-azure-03.md)」を参照) を格納するテーブルであり、もう 1 つは "*追跡オブジェクト*" に関する情報を格納するものです。</span><span class="sxs-lookup"><span data-stu-id="86e78-119">In context of the demo application, you need two Tables, one to store information about the project with information about the state of trained models more about that in the ([Integrating Azure Custom Vision](mr-learning-azure-03.md)) tutorial and a second table to store information about *Tracked Objects*.</span></span>

<span data-ttu-id="86e78-120">詳細については、[Azure Table Storage](https://docs.microsoft.com/azure/storage/tables/table-storage-overview) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="86e78-120">Learn more about [Azure Table storage](https://docs.microsoft.com/azure/storage/tables/table-storage-overview).</span></span>

### <a name="azure-blob-storage"></a><span data-ttu-id="86e78-121">Azure Blob Storage</span><span class="sxs-lookup"><span data-stu-id="86e78-121">Azure Blob storage</span></span>

<span data-ttu-id="86e78-122">このサービスでは、大規模なバイナリ ファイルを格納することができます。"*追跡オブジェクト*" について撮影した写真をサムネイルとして格納するために、これを使用します。</span><span class="sxs-lookup"><span data-stu-id="86e78-122">This service allows to store large binary files, you will use this to store photos taken for *Tracked Objects* as thumbnail.</span></span>
<span data-ttu-id="86e78-123">デモ アプリケーションでは、画像を格納するために、BLOB コンテナーが 1 つ必要です。</span><span class="sxs-lookup"><span data-stu-id="86e78-123">For of the demo application you need one Blob Container to store the images.</span></span>

<span data-ttu-id="86e78-124">詳細については、[Azure Blob Storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="86e78-124">Learn more about [Azure Blob storage](https://docs.microsoft.com/azure/storage/blobs/storage-blobs-introduction).</span></span>

## <a name="preparing-azure-storage"></a><span data-ttu-id="86e78-125">Azure Storage の準備</span><span class="sxs-lookup"><span data-stu-id="86e78-125">Preparing Azure Storage</span></span>

<span data-ttu-id="86e78-126">Azure ストレージ サービスを利用するには、Azure ストレージ アカウントが必要です。</span><span class="sxs-lookup"><span data-stu-id="86e78-126">To consume the Azure storage services you will need an Azure storage account.</span></span> <span data-ttu-id="86e78-127">ストレージ アカウントを作成するには、[ストレージ アカウントの作成](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="86e78-127">To create a storage account, see [Create a storage account](https://docs.microsoft.com/azure/storage/common/storage-account-create?tabs=azure-portal).</span></span> <span data-ttu-id="86e78-128">ストレージ アカウントの詳細については、[Azure ストレージ アカウントの概要](https://docs.microsoft.com/azure/storage/common/storage-account-overview)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="86e78-128">To learn more about storage accounts, see [Azure storage account overview](https://docs.microsoft.com/azure/storage/common/storage-account-overview).</span></span>

<span data-ttu-id="86e78-129">ストレージ アカウントを作成したら、このレッスンの次のセクションで必要となる接続文字列を **Azure portal** から取得できます。</span><span class="sxs-lookup"><span data-stu-id="86e78-129">Once you have a storage account, you can retrieve the connection string from the **Azure Portal** which will be needed in the next section of this lesson.</span></span>

### <a name="optional-azure-storage-explorer"></a><span data-ttu-id="86e78-130">オプションの Azure Storage Explorer</span><span class="sxs-lookup"><span data-stu-id="86e78-130">Optional Azure Storage Explorer</span></span>

<span data-ttu-id="86e78-131">アプリケーション内の UI からデータに関するすべての変更を表示および確認することができますが、[Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) をインストールすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="86e78-131">While you can see and verify all data changes from the UI inside the application, we recommend to install [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/).</span></span> <span data-ttu-id="86e78-132">このツールを使用すると、Azure Storage 内のデータを視覚的に確認できるため、デバッグを行うときや学習するときに大いに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="86e78-132">This tool allows you to visually see the data in the Azure storage and is of great help when debugging and learning.</span></span>

> [!TIP]
> <span data-ttu-id="86e78-133">Unity エディター内からテストする場合は、次のローカル エミュレーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="86e78-133">For testing from inside the Unity editor you can use a local emulator:</span></span>
>
> * <span data-ttu-id="86e78-134">Windows 10 では、[Azure ストレージ エミュレーター](https://docs.microsoft.com/azure/storage/common/storage-use-emulator)を使用できます。</span><span class="sxs-lookup"><span data-stu-id="86e78-134">on Windows 10 you can use [Azure Storage Emulator](https://docs.microsoft.com/azure/storage/common/storage-use-emulator)</span></span>
> * <span data-ttu-id="86e78-135">MacOS、Linux では、Docker 用の [Azurite Docker Image](https://hub.docker.com/_/microsoft-azure-storage-azurite) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="86e78-135">on MacOS/Linux you can use [Azurite Docker Image](https://hub.docker.com/_/microsoft-azure-storage-azurite) for Docker</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="86e78-136">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="86e78-136">Preparing the scene</span></span>

<span data-ttu-id="86e78-137">[階層] ウィンドウで、**DataManager** オブジェクトを見つけて選択します。</span><span class="sxs-lookup"><span data-stu-id="86e78-137">In the Hierarchy window, locate the **DataManager** object and select it.</span></span>

![DataManager スクリプト コンポーネント構成フィールドがインスペクターに表示された Unity](images/mr-learning-azure/tutorial2-section4-step1-1.png)

<span data-ttu-id="86e78-139">[インスペクター] ウィンドウから、**DataManager (script)** コンポーネントは **Azure Storage** 関連のすべての設定が保持される場所であることがわかります。</span><span class="sxs-lookup"><span data-stu-id="86e78-139">From the Inspector window you will see that the **DataManager (script)** component is where all **Azure storage** related settings are kept.</span></span> <span data-ttu-id="86e78-140">関連する設定はすべて、既に設定されているので、"*接続文字列*" フィールドを、Azure portal から取得できるものに置き換えるだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="86e78-140">All relevant settings are already set, you just need to replace the *Connection String* field with the one you can retrieve from the Azure Portal.</span></span> <span data-ttu-id="86e78-141">ローカルの Azure ストレージ エミュレーター ソリューションを使用している場合は、既に指定されている "*接続文字列*" を保持できます。</span><span class="sxs-lookup"><span data-stu-id="86e78-141">If you are using a local Azure storage emulator solution, then you can keep the already provided *Connection String*.</span></span>

<span data-ttu-id="86e78-142">**DataManager (スクリプト)** は、**Table Storage** および **Blob Storage** とやりとりすることが役割であり、UI コンポーネント上の他のコントローラー スクリプトによって利用されます。</span><span class="sxs-lookup"><span data-stu-id="86e78-142">The **DataManager (script)** is responsible for talking to the **Table storage** and **Blob storage** which is consumed by other controller scripts on the UI components.</span></span>

## <a name="writing-and-reading-data-from-azure-table-storage"></a><span data-ttu-id="86e78-143">Azure Table Storage に対するデータの書き込みと読み取り</span><span class="sxs-lookup"><span data-stu-id="86e78-143">Writing and reading data from Azure Table storage</span></span>

<span data-ttu-id="86e78-144">すべての準備が整ったら、"*追跡オブジェクト*" を作成します。</span><span class="sxs-lookup"><span data-stu-id="86e78-144">With everything prepared it's time to create a *Tracked Object*.</span></span>

<span data-ttu-id="86e78-145">ご利用の HoloLens 上でアプリケーションを開き、 **[オブジェクトの設定]** をクリックします。*EnterObjectName* オブジェクトが階層内でどのようにアクティブになるかがわかります。</span><span class="sxs-lookup"><span data-stu-id="86e78-145">Open the application on your HoloLens, click on the **Set Object** and you will see how the *EnterObjectName* object will become active in the hierarchy.</span></span> <span data-ttu-id="86e78-146">このメニューで、"*検索バー*" をクリックし、"*追跡オブジェクト*" に付ける名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="86e78-146">In this menu click on the *search bar* and type in the name you want to give the *Tracked Object*.</span></span> <span data-ttu-id="86e78-147">名前を指定したら、 **[オブジェクトの設定]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="86e78-147">After providing a name click on the **Set object** button.</span></span> <span data-ttu-id="86e78-148">これにより、Azure Table Storage に "*追跡オブジェクト*" が作成され、 **[オブジェクト カード]** が表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="86e78-148">This will create the *Tracked Object* on the Azure Table storage and you will see now the **Object Card**.</span></span>

<span data-ttu-id="86e78-149">この **[オブジェクト カード]** は、"*追跡オブジェクト*" の UI 表現であり、このチュートリアル シリーズでは重要な役割を何度も果たします。</span><span class="sxs-lookup"><span data-stu-id="86e78-149">This **Object Card** is a UI representation of the *Tracked Object* and will have an important role several times in this tutorial series.</span></span>

<span data-ttu-id="86e78-150">次に、説明 "*テキスト ボックス*" をクリックし、「Car」と入力します。その後、 **[保存]** をクリックして、変更を保存します。</span><span class="sxs-lookup"><span data-stu-id="86e78-150">Now click on the description *text box* and type in "Car", after that click on the **Save** button to save the changes.</span></span> <span data-ttu-id="86e78-151">アプリケーションを停止してから、再実行します。</span><span class="sxs-lookup"><span data-stu-id="86e78-151">Stop the application and rerun it.</span></span>

<span data-ttu-id="86e78-152">今度は、 **[オブジェクトの検索]** をクリックし、以前 "*追跡オブジェクト*" を作成するときに使用した名前を "*検索バー*" に入力します。</span><span class="sxs-lookup"><span data-stu-id="86e78-152">Now this time click on **Search Object** and type in the *search bar* the name you have used before when creating the *Tracked Object*.</span></span> <span data-ttu-id="86e78-153">すべてのデータを含む **[オブジェクト カード]** が **Azure Table Storage** から取得されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="86e78-153">You will see that the **Object Card** with all the data is retrieved from the **Azure Table storage**.</span></span>

<span data-ttu-id="86e78-154">**[オブジェクト カード]** を閉じて、新しい "*追跡オブジェクト*" を作成し、そのデータを編集することも自由にできます。</span><span class="sxs-lookup"><span data-stu-id="86e78-154">Feel free to close the **Object Card** and create new *Tracked Objects* and edit their data.</span></span>

> [!TIP]
> <span data-ttu-id="86e78-155">[Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) をインストール済みである場合、*objects* テーブルを参照すると、"*追跡対象*" オブジェクトが作成されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="86e78-155">If you have installed the [Azure Storage Explorer](https://azure.microsoft.com/features/storage-explorer/) then look into the *objects* table and you will see there the created *Tracked Object*.</span></span>

## <a name="uploading-and-download-image-from-azure-blob-storage"></a><span data-ttu-id="86e78-156">Azure Blob Storage への画像のアップロードおよびダウンロード</span><span class="sxs-lookup"><span data-stu-id="86e78-156">Uploading and Download image from Azure Blob storage</span></span>

<span data-ttu-id="86e78-157">このセクションでは、Azure Blob Storage を使用して、"*追跡オブジェクト*" のサムネイルとして使用される画像をアップロードおよびダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="86e78-157">In this section you will use the Azure Blob storage to upload and download images that will be used as thumbnails for *Tracked Objects*.</span></span>

> [!NOTE]
> <span data-ttu-id="86e78-158">このチュートリアルでは、アプリケーションによって、写真を撮影して、画像を BLOB ストレージにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="86e78-158">In this tutorial the application will take photos to upload images to the Blob storage.</span></span> <span data-ttu-id="86e78-159">それを Unity エディターからローカルに実行している場合は、Web カメラがコンピューターに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="86e78-159">If you are running this locally from the Unity editor, then make sure that you have a webcam connected to your computer.</span></span>

<span data-ttu-id="86e78-160">ご利用の HoloLens 上でアプリケーションを開き、 **[Set Object]\(オブジェクトの設定\)** をクリックし、"*検索バー*" に「Car」という名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="86e78-160">Open the application on your HoloLens, click on **Set Object** and type in the *search bar* the name "Car".</span></span> <span data-ttu-id="86e78-161">これで、 **[オブジェクト カード]** が表示されるので、 **[カメラ]** ボタンをクリックすると、AirTap を実行して写真を撮るように指示されます。</span><span class="sxs-lookup"><span data-stu-id="86e78-161">Now you should see the **Object Card**, click on the **Camera** button and you will be instructed to do an AirTap to take a photo.</span></span> <span data-ttu-id="86e78-162">写真を撮影すると、アクティブなアップロードについて通知するメッセージが表示され、しばらくすると、プレースホルダーが以前にあった場所に、その画像が表示されます。</span><span class="sxs-lookup"><span data-stu-id="86e78-162">After taking a photo you will see a message that informs you about the active upload and after a while the image should appear where the placeholder was before.</span></span>

<span data-ttu-id="86e78-163">次に、アプリケーションを再実行し、"*追跡オブジェクト*" を検索します。前にアップロードした画像がサムネイルとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="86e78-163">Now rerun the application and search for the *Tracked Object* and the previously uploaded image should appear as thumbnail.</span></span>

## <a name="deleting-image-from-azure-blob-storage"></a><span data-ttu-id="86e78-164">Azure Blob Storage から画像を削除する</span><span class="sxs-lookup"><span data-stu-id="86e78-164">Deleting image from Azure Blob storage</span></span>

<span data-ttu-id="86e78-165">前のセクションでは、Azure Blob Storage に新しい画像をアップロードしました。このセクションでは、"*追跡オブジェクト*" のサムネイル画像を削除します。</span><span class="sxs-lookup"><span data-stu-id="86e78-165">In the previous section you uploaded new images to Azure Blob storage, in this section you will delete an image thumbnail for *Tracked Objects*.</span></span>

<span data-ttu-id="86e78-166">ご利用の HoloLens 上でアプリケーションを開き、 **[Set Object]\(オブジェクトの設定\)** をクリックし、"*検索バー*" に「Car」という名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="86e78-166">Open the application on your HoloLens, click on **Set Object** and type in the *search bar* the name "Car".</span></span> <span data-ttu-id="86e78-167">これで、サムネイル画像を伴って **[オブジェクト カード]** が表示されるので、 **[削除]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="86e78-167">Now you should see the **Object Card** with the thumbnail image, click on the **Delete** button.</span></span> <span data-ttu-id="86e78-168">サムネイル画像がプレースホルダー画像に置き換えられていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="86e78-168">You will notice that the thumbnail image is replaced by the placeholder image.</span></span>

<span data-ttu-id="86e78-169">次に、アプリケーションを再実行して、前に削除したサムネイルの "*追跡オブジェクト*" を検索するとプレースホルダー画像のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="86e78-169">Now rerun the application and search for the *Tracked Object* of the previously deleted thumbnail, you should only see the placeholder image.</span></span>

## <a name="congratulations"></a><span data-ttu-id="86e78-170">結論</span><span class="sxs-lookup"><span data-stu-id="86e78-170">Congratulations</span></span>

<span data-ttu-id="86e78-171">このチュートリアルでは、Azure ストレージ サービスを使用して非構造化データ (ここでは、クラウド上の **HoloLens 2** デモ アプリケーション用の "**追跡オブジェクト**" や、サムネイル画像の形式のバイナリなど) を保持する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="86e78-171">In this tutorial you learned how Azure storage services can be used to persist unstructured data, like in our case **Tracked Objects** and binaries in form of thumbnail images for the **HoloLens 2** demo application on the cloud.</span></span>

<span data-ttu-id="86e78-172">次のチュートリアルでは、Azure Custom Vision を使用して、"*追跡オブジェクト*" に関連付けられている画像を検出する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="86e78-172">In the next tutorial you will learn how to use Azure Custom Vision to detect images associated with a *Tracked Object*.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="86e78-173">次のチュートリアル: 3. Azure Custom Vision の統合</span><span class="sxs-lookup"><span data-stu-id="86e78-173">Next tutorial: 3. Integrating Azure Custom Vision</span></span>](mr-learning-azure-03.md)
