---
title: マルチユーザー機能のチュートリアル - 5. Azure Spatial Anchors の共有エクスペリエンスへの統合
description: このコースを完了すると、Azure Spatial Anchors を使用して共有マルチユーザー HoloLens 2 アプリケーション内でオブジェクトを固定する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 65672bad9a967e11e7feb7efc45759608e9c9e76
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353430"
---
# <a name="5-integrating-azure-spatial-anchors-into-a-shared-experience"></a><span data-ttu-id="a8065-105">5.Azure Spatial Anchors の共有エクスペリエンスへの統合</span><span class="sxs-lookup"><span data-stu-id="a8065-105">5. Integrating Azure Spatial Anchors into a shared experience</span></span>

<span data-ttu-id="a8065-106">このチュートリアルでは、Azure Spatial Anchors (ASA) を共有エクスペリエンスに統合する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="a8065-106">In this tutorial, you will learn how to integrate Azure Spatial Anchors (ASA) into the shared experience.</span></span> <span data-ttu-id="a8065-107">ASA により複数のデバイスが現実の世界への共通の参照を持てるようになり、ユーザーは互いの姿をその現実の物理的な位置に見たり、共有エクスペリエンスを同じ場所で見たりすることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="a8065-107">ASA allows multiple devices to have a common reference to the physical world so that the users see each other in their actual physical location and see the shared experience in the same place.</span></span>

## <a name="objectives"></a><span data-ttu-id="a8065-108">目標</span><span class="sxs-lookup"><span data-stu-id="a8065-108">Objectives</span></span>

* <span data-ttu-id="a8065-109">ASA を共有エクスペリエンスに統合し、複数デバイスで位置合わせする</span><span class="sxs-lookup"><span data-stu-id="a8065-109">Integrate ASA into a shared experience for multi-device alignment</span></span>
* <span data-ttu-id="a8065-110">ASA がローカル共有エクスペリエンスのコンテキストでどのように機能するかについての基本を学ぶ</span><span class="sxs-lookup"><span data-stu-id="a8065-110">Learn the fundamentals of how ASA works in the context of a local shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="a8065-111">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="a8065-111">Preparing the scene</span></span>

<span data-ttu-id="a8065-112">[Hierarchy]\(ヒエラルキー\) ウィンドウで **SharedPlayground** オブジェクトを展開し、**TableAnchor** オブジェクトを展開してその子オブジェクトを公開します。</span><span class="sxs-lookup"><span data-stu-id="a8065-112">In the Hierarchy window, expand the **SharedPlayground** object, then expand the **TableAnchor** object to expose its child objects:</span></span>

![SharedPlayground と TableAnchor オブジェクトが展開された Unity](images/mr-learning-sharing/sharing-05-section1-step1-1.png)

<span data-ttu-id="a8065-114">[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Prefabs]\(プレハブ\)** フォルダーの順に移動して、**Buttons** プレハブを **TableAnchor** 子オブジェクト上にドラッグし、TableAnchor オブジェクトの子としてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="a8065-114">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **Buttons** prefab onto the **TableAnchor** child object to add it to your scene as a child of the TableAnchor object:</span></span>

![新しく追加された Buttons プレハブが選択されている Unity](images/mr-learning-sharing/sharing-05-section1-step1-2.png)

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="a8065-116">シーンを操作するためのボタンの構成</span><span class="sxs-lookup"><span data-stu-id="a8065-116">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="a8065-117">このセクションでは一連のボタン イベントを構成して、Azure Spatial Anchors を使用して共有エクスペリエンスでの空間的な位置合わせを実現する方法の基本を示します。</span><span class="sxs-lookup"><span data-stu-id="a8065-117">In this section, you will configure a series of button events demonstrating the fundamentals of how Azure Spatial Anchors can be used to achieve spatial alignment in a shared experience.</span></span>

<span data-ttu-id="a8065-118">[Hierarchy]\(ヒエラルキー\) ウィンドウで **Button** オブジェクトを展開し、**StartAzureSession** という名前の最初の子ボタン オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="a8065-118">In the Hierarchy window, expand the **Button** object and select the first child button object named **StartAzureSession**:</span></span>

![StartAzureSession ボタン オブジェクトが選択されている Unity](images/mr-learning-sharing/sharing-05-section2-step1-1.png)

<span data-ttu-id="a8065-120">[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探し、**OnClick ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="a8065-120">In the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="a8065-121">**[None (Object)]\(なし (オブジェクト))\** フィールドに、\*\*TableAnchor*\* オブジェクトを割り当てる</span><span class="sxs-lookup"><span data-stu-id="a8065-121">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="a8065-122">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  > **StartAzureSession ()** 関数の順に選択する</span><span class="sxs-lookup"><span data-stu-id="a8065-122">From the **No Function** dropdown, select the **AnchorModuleScript** > **StartAzureSession ()** function</span></span>

![StartAzureSession ボタンの OnClick イベントが構成された Unity](images/mr-learning-sharing/sharing-05-section2-step1-2.png)

<span data-ttu-id="a8065-124">[Hierarchy]\(ヒエラルキー\) ウィンドウで **CreateAzureAnchor** という名前の 2 番目の子ボタン オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探して **OnClick ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="a8065-124">In the Hierarchy window, select the second child button object named **CreateAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="a8065-125">**[None (Object)]\(なし (オブジェクト))\** フィールドに、\*\*TableAnchor*\* オブジェクトを割り当てる</span><span class="sxs-lookup"><span data-stu-id="a8065-125">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="a8065-126">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  > **CreateAzureAnchor()** 関数の順に選択する</span><span class="sxs-lookup"><span data-stu-id="a8065-126">From the **No Function** dropdown, select the **AnchorModuleScript** > **CreateAzureAnchor ()** function</span></span>
* <span data-ttu-id="a8065-127">表示される新しい **"None (Game Object)"(なし (ゲーム オブジェクト))** フィールドに、**TableAnchor** オブジェクトを割り当てる</span><span class="sxs-lookup"><span data-stu-id="a8065-127">To the new **None (Game Object)** field that appears, assign the **TableAnchor** object</span></span>

![CreateAzureAnchor ボタンの OnClick イベントが構成された Unity](images/mr-learning-sharing/sharing-05-section2-step1-3.png)

<span data-ttu-id="a8065-129">[Hierarchy]\(ヒエラルキー\) ウィンドウで **ShareAzureAnchor** という名前の 3 番目の子ボタン オブジェクトを選択して、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探して **OnClick ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="a8065-129">In the Hierarchy window, select the third child button object named **ShareAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="a8065-130">**[None (Object)]\(なし (オブジェクト))\** フィールドに、\*\*TableAnchor*\* オブジェクトを割り当てる</span><span class="sxs-lookup"><span data-stu-id="a8065-130">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="a8065-131">**[No Function]** (関数なし) ドロップダウンから、 **[SharingModuleScript]**  > **ShareAzureAnchor()** 関数の順に選択する</span><span class="sxs-lookup"><span data-stu-id="a8065-131">From the **No Function** dropdown, select the **SharingModuleScript** > **ShareAzureAnchor ()** function</span></span>

![ShareAzureAnchor ボタンの OnClick イベントが構成された Unity](images/mr-learning-sharing/sharing-05-section2-step1-4.png)

<span data-ttu-id="a8065-133">[Hierarchy]\(階層\) ウィンドウで **GetAzureAnchor** という名前の 4 番目の子ボタン オブジェクトを選択して、[Inspector]\(インスペクター\) ウィンドウで **Interactable (Script)** コンポーネントを探して **OnClick ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="a8065-133">In the Hierarchy window, select the fourth child button object named **GetAzureAnchor**, then in the Inspector window, locate the **Interactable (Script)** component and configure the **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="a8065-134">**[None (Object)]\(なし (オブジェクト))\** フィールドに、\*\*TableAnchor*\* オブジェクトを割り当てる</span><span class="sxs-lookup"><span data-stu-id="a8065-134">To the **None (Object)** field, assign the **TableAnchor** object</span></span>
* <span data-ttu-id="a8065-135">**[No Function]** (関数なし) ドロップダウンから、 **[SharingModuleScript]**  > **GetAzureAnchor()** 関数の順に選択する</span><span class="sxs-lookup"><span data-stu-id="a8065-135">From the **No Function** dropdown, select the **SharingModuleScript** > **GetAzureAnchor ()** function</span></span>

![GetAzureAnchor ボタンの OnClick イベントが構成された Unity](images/mr-learning-sharing/sharing-05-section2-step1-5.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="a8065-137">シーンを Azure リソースに接続する</span><span class="sxs-lookup"><span data-stu-id="a8065-137">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="a8065-138">[Hierarchy]\(ヒエラルキー\) ウィンドウで **SharedPlayground** オブジェクトを展開し、**TableAnchor** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="a8065-138">In the Hierarchy window, expand the **SharedPlayground** object and select the **TableAnchor** object.</span></span>

<span data-ttu-id="a8065-139">[Inspector]\(インスペクター\) ウィンドウで **Spatial Anchor Manager (Script)** コンポーネントを探し、このチュートリアル シリーズの「[前提条件](mr-learning-sharing-01.md#prerequisites)」の部分で作成した Azure Spatial Anchors アカウントからの資格情報を使用して、 **[Credentials]\(資格情報\)** セクションを構成します。</span><span class="sxs-lookup"><span data-stu-id="a8065-139">In the Inspector window, locate the **Spatial Anchor Manager (Script)** component and configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-sharing-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="a8065-140">**"Spatial Anchors Account ID"(Spatial Anchors アカウント ID)** フィールドに、Azure Spatial Anchors アカウントからの **アカウント ID** を貼り付ける</span><span class="sxs-lookup"><span data-stu-id="a8065-140">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="a8065-141">**"Spatial Anchors Account Key"(Spatial Anchors アカウント キー)** フィールドに、Azure Spatial Anchors アカウントからのプライマリまたはセカンダリ **アクセス キー** を貼り付ける</span><span class="sxs-lookup"><span data-stu-id="a8065-141">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![Spatial Anchor Manager が構成された Unity](images/mr-learning-sharing/sharing-05-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="a8065-143">シーン内で空間アンカー アカウント ID およびキーを設定するのでなく、プロジェクト全体に対してそれを設定することもできます。ASA を使用して複数のシーンを用意する場合は、これが有利です。</span><span class="sxs-lookup"><span data-stu-id="a8065-143">Instead of setting the Spatial Anchors Account ID and Key in the scene, you can set it for your entire project, this can be advantageous if you have multiple scenes using ASA.</span></span> <span data-ttu-id="a8065-144">それを行うには、[Project]\(プロジェクト\) ウィンドウで、[Assets]\(アセット\) > [AzureSpatialAnchors.SDK] > [Resources]\(リソース\) > **[SpatialAnchorConfig]** アセットの順に移動し、次に [Inspector]\(インスペクター\) ウィンドウで値を設定します。</span><span class="sxs-lookup"><span data-stu-id="a8065-144">To do this, in the Project window, navigate to the Assets > AzureSpatialAnchors.SDK > Resources > **SpatialAnchorConfig** asset, then set the values in the Inspector window.</span></span>

<span data-ttu-id="a8065-145">[Hierarchy]\(階層\) ウィンドウで、 **[TableAnchor]** オブジェクトを選択してから、[Inspector]\(インスペクター\) ウィンドウで **Anchor Module (Script)** コンポーネントを探し、それを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="a8065-145">In the Hierarchy window, select the **TableAnchor** object, then in the Inspector window, locate the **Anchor Module (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="a8065-146">**[Public Sharing Pin]\(パブリック共有ピン\)** フィールドで、いくつかの数字を変更します。これにより、ピンが自分のプロジェクトに固有のものとなります。</span><span class="sxs-lookup"><span data-stu-id="a8065-146">In the **Public Sharing Pin** field, change a few digits, so the pin becomes unique to your project</span></span>

![Anchor Module Script が構成された Unity](images/mr-learning-sharing/sharing-05-section3-step1-2.png)

<span data-ttu-id="a8065-148">**TableAnchor** オブジェクトを選択したまま、[Inspector]\(インスペクター\) ウィンドウですべてのスクリプト コンポーネントが **有効** になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a8065-148">With the **TableAnchor** object still selected, in the Inspector window, make sure all the script components are **enabled**:</span></span>

* <span data-ttu-id="a8065-149">**Spatial Anchor Manager (Script)** コンポーネントの隣にあるチェックボックスをオンにして有効にする</span><span class="sxs-lookup"><span data-stu-id="a8065-149">Check the checkbox next to the **Spatial Anchor Manager (Script)** components to enable it</span></span>
* <span data-ttu-id="a8065-150">**Anchor Module Script (Script)** コンポーネントの隣にあるチェックボックスをオンにして有効にする</span><span class="sxs-lookup"><span data-stu-id="a8065-150">Check the checkbox next to the **Anchor Module Script (Script)** components to enable it</span></span>
* <span data-ttu-id="a8065-151">**Sharing Module Script (Script)** コンポーネントの隣にあるチェックボックスをオンにして有効にする</span><span class="sxs-lookup"><span data-stu-id="a8065-151">Check the checkbox next to the **Sharing Module Script (Script)** components to enable it</span></span>

![TableAnchor スクリプト コンポーネントが有効にされた Unity](images/mr-learning-sharing/sharing-05-section3-step1-3.png)

## <a name="trying-the-experience-with-spatial-alignment"></a><span data-ttu-id="a8065-153">空間的な位置合わせのエクスペリエンスを試す</span><span class="sxs-lookup"><span data-stu-id="a8065-153">Trying the experience with spatial alignment</span></span>

> [!NOTE]
> <span data-ttu-id="a8065-154">Azure Spatial Anchors を Unity で実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="a8065-154">Azure Spatial Anchors can not run in Unity.</span></span> <span data-ttu-id="a8065-155">そのため、Azure Spatial Anchors の機能をテストするには、最低 2 台のデバイスにプロジェクトを配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8065-155">Consequently, to test the Azure Spatial Anchors functionality, you need to deploy the project to a minimum of two devices.</span></span>

<span data-ttu-id="a8065-156">Unity プロジェクトをビルドして 2 台のデバイスに配置すると、Azure Anchor ID を共有してデバイス間で空間的な位置合わせを実現できます。</span><span class="sxs-lookup"><span data-stu-id="a8065-156">If you now build and deploy the Unity project to two devices, you can achieve spatial alignment between the devices by sharing the Azure Anchor ID.</span></span> <span data-ttu-id="a8065-157">これをテストするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a8065-157">To test it out, you can follow these steps:</span></span>

1. <span data-ttu-id="a8065-158">デバイス 1 の場合: **アプリを開始する** (Rover エクスプローラーのインスタンスが作成され、テーブルに配置されます)</span><span class="sxs-lookup"><span data-stu-id="a8065-158">On device 1: **Start the app** (the Rover Explorer is instantiated and placed on the table)</span></span>
2. <span data-ttu-id="a8065-159">デバイス 2 の場合: **アプリを開始する** (両方のユーザーが Rover エクスプローラーのあるテーブルを見ることができますが、テーブルは同じ場所には表示されず、ユーザー アバターはユーザーが実際にいるところに表示されません)</span><span class="sxs-lookup"><span data-stu-id="a8065-159">On device 2: **Start the app** (both users see the table with the Rover Explorer, but the table does not appear in the same place, and the user avatars do not appear where the users are)</span></span>
3. <span data-ttu-id="a8065-160">デバイス 1 の場合: **[Start Azure Session]\(Azure セッションの開始\)** ボタンを押す</span><span class="sxs-lookup"><span data-stu-id="a8065-160">On device 1: Press the **Start Azure Session** button</span></span>
4. <span data-ttu-id="a8065-161">デバイス 1 の場合: **[Create Azure Anchor]\(Azure Anchor の作成\)** ボタンを押す (TableAnchor オブジェクトの場所にアンカーが作成され、アンカーの情報が Azure リソースに保存されます)。</span><span class="sxs-lookup"><span data-stu-id="a8065-161">On device 1: Press the **Create Azure Anchor** button (creates anchor at the location of the TableAnchor object and stores the anchor information in the Azure resource).</span></span>
5. <span data-ttu-id="a8065-162">デバイス 1 の場合: **[Share Azure Anchor]\(Azure Anchor の共有\)** ボタンを押す (他のユーザーとアンカー ID がリアルタイムで共有されます)</span><span class="sxs-lookup"><span data-stu-id="a8065-162">On device 1: Press the **Share Azure Anchor** button (shares the anchor ID with other users in real-time)</span></span>
6. <span data-ttu-id="a8065-163">デバイス 2 の場合: **[Start Azure Session]\(Azure セッションの開始\)** ボタンを押す</span><span class="sxs-lookup"><span data-stu-id="a8065-163">On device 2: Press the **Start Azure Session** button</span></span>
7. <span data-ttu-id="a8065-164">デバイス 2 の場合: **[Get Azure Anchor]\(Azure Anchor の取得\)** ボタンを押す (Azure リソースに接続して共有アンカー ID のアンカー情報が取得され、TableAnchor オブジェクトはデバイス 1 でアンカーを作成した場所に移動します)</span><span class="sxs-lookup"><span data-stu-id="a8065-164">On device 2: Press the **Get Azure Anchor** button (connects to the Azure resource to retrieve the anchor information for the shared anchor ID, then moves the TableAnchor object to the location where the anchor was created with the device 1)</span></span>

> [!TIP]
> <span data-ttu-id="a8065-165">2 台の HoloLens デバイスへのアクセス権がない場合は、[モバイル デバイス用の Azure Spatial Anchors のビルド](mr-learning-asa-05.md)に関するページに従って、ご利用のモバイル デバイスにプロジェクトを配置することができます。</span><span class="sxs-lookup"><span data-stu-id="a8065-165">If you don't have access to two HoloLens devices, you may follow the [Building Azure Spatial Anchors for mobile devices](mr-learning-asa-05.md) to deploy the project to your mobile device.</span></span>

## <a name="congratulations"></a><span data-ttu-id="a8065-166">結論</span><span class="sxs-lookup"><span data-stu-id="a8065-166">Congratulations</span></span>

<span data-ttu-id="a8065-167">このチュートリアルでは、Azure の強力な Spatial Anchors を統合して、複数のデバイスを共有エクスペリエンスの中に配置する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="a8065-167">In this tutorial, you learned how to integrate Azure's powerful Spatial Anchors to align devices in a shared experience.</span></span>

<span data-ttu-id="a8065-168">これでこのチュートリアル シリーズは終了となります。Photon アカウントを設定し、PUN アプリを作成し、PUN を Unity プロジェクトに統合し、ユーザー アバターと共有オブジェクトを構成し、最後に Azure Spatial Anchors を使用して複数の参加者を配置する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="a8065-168">This also concludes this tutorial series where you learned how to set up a Photon account, create a PUN app, integrate PUN into the Unity project, configure user avatars and shared objects, and finally align multiple participants using Azure Spatial Anchors.</span></span>
