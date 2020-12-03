---
title: Unreal での Azure Spatial Anchors
description: Unreal エンジンでの Azure 空間アンカーの作成に関する概要です。
author: hferrone
ms.author: v-hferrone
ms.date: 07/01/2020
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, Azure, Azure 開発, Spatial Anchors, Mixed Reality, 開発, 機能, 新しいプロジェクト, エミュレーター, ドキュメント, ガイド, ホログラム, ゲーム開発, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: b464292b606f6c375fe84a50867cac770cd8f001
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354550"
---
# <a name="azure-spatial-anchors-in-unreal"></a><span data-ttu-id="2a082-104">Unreal での Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="2a082-104">Azure Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="2a082-105">概要</span><span class="sxs-lookup"><span data-stu-id="2a082-105">Overview</span></span>

<span data-ttu-id="2a082-106">Azure Spatial Anchors は、現実世界のアンカー ポイントを拡張現実デバイスを使って検出、共有、永続化できるようにする Microsoft Mixed Reality サービスです。</span><span class="sxs-lookup"><span data-stu-id="2a082-106">Azure Spatial Anchors is a Microsoft Mixed Reality service, allowing augmented reality devices to discover, share, and persist anchor points in the physical world.</span></span> <span data-ttu-id="2a082-107">このドキュメントでは、Azure Spatial Anchors サービスを Unreal プロジェクトに統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a082-107">Documentation below provides instructions for integrating the Azure Spatial Anchors service into an Unreal project.</span></span> <span data-ttu-id="2a082-108">さらに情報が必要な場合は、[Azure Spatial Anchors サービス](https://azure.microsoft.com/services/spatial-anchors/)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a082-108">If you're looking for more information, check out the [Azure Spatial Anchors service](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

> [!NOTE]
> <span data-ttu-id="2a082-109">Unreal Engine 4.26 には、iOS または Android を対象にする場合に ARKit と ARCore をサポートするためのプラグインが用意されています。</span><span class="sxs-lookup"><span data-stu-id="2a082-109">Unreal Engine 4.26 now has plugins for ARKit and ARCore support if you're targeting iOS or Android.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2a082-110">ローカル アンカーはデバイスに格納されますが、Azure 空間アンカーはクラウドに格納されます。</span><span class="sxs-lookup"><span data-stu-id="2a082-110">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="2a082-111">アンカーをデバイスにローカルに格納することをご希望の場合は、[ローカル空間アンカー](unreal-spatial-anchors.md)のドキュメントにその手順が説明されています。</span><span class="sxs-lookup"><span data-stu-id="2a082-111">If you're looking to store your anchors locally on a device, we have a [Local Spatial Anchors](unreal-spatial-anchors.md) document that can walk you through the process.</span></span> <span data-ttu-id="2a082-112">また、ローカル アンカーと Azure のアンカーは、競合することなく同じプロジェクトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="2a082-112">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2a082-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="2a082-113">Prerequisites</span></span>

<span data-ttu-id="2a082-114">このガイドを完了するには、次のことが必要です。</span><span class="sxs-lookup"><span data-stu-id="2a082-114">To complete this guide, make sure you have:</span></span>

- <span data-ttu-id="2a082-115">インストール済みの [Unreal バージョン 4.25](https://www.unrealengine.com/get-now) 以降</span><span class="sxs-lookup"><span data-stu-id="2a082-115">Installed [Unreal version 4.25](https://www.unrealengine.com/get-now) or later</span></span>
- <span data-ttu-id="2a082-116">Unreal にセットアップされた [HoloLens 2 プロジェクト](tutorials/unreal-uxt-ch1.md)</span><span class="sxs-lookup"><span data-stu-id="2a082-116">A [HoloLens 2 project](tutorials/unreal-uxt-ch1.md) setup in Unreal</span></span> 
- <span data-ttu-id="2a082-117">「[Azure Spatial Anchors の概要](https://docs.microsoft.com/azure/spatial-anchors/overview)」の確認</span><span class="sxs-lookup"><span data-stu-id="2a082-117">Read through the [Azure Spatial Anchors overview](https://docs.microsoft.com/azure/spatial-anchors/overview)</span></span>
- <span data-ttu-id="2a082-118">C++ と Unreal に関する基本的な知識</span><span class="sxs-lookup"><span data-stu-id="2a082-118">Basic knowledge on C++ and Unreal</span></span>

## <a name="getting-azure-spatial-anchors-account-info"></a><span data-ttu-id="2a082-119">Azure Spatial Anchors アカウント情報を取得する</span><span class="sxs-lookup"><span data-stu-id="2a082-119">Getting Azure Spatial Anchors account info</span></span>

<span data-ttu-id="2a082-120">プロジェクトで Azure Spatial Anchors を使用する前に、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a082-120">Before using Azure Spatial Anchors in your project, you need to:</span></span>
* <span data-ttu-id="2a082-121">[Spatial Anchors リソースを作成](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)し、次に示すアカウント フィールドをコピーします。</span><span class="sxs-lookup"><span data-stu-id="2a082-121">[Create a spatial anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) and copy the account fields listed below.</span></span> <span data-ttu-id="2a082-122">これらの値は、アプリケーションのアカウントでユーザーを認証するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="2a082-122">These values are used to authenticate users with your application's account:</span></span>
    * <span data-ttu-id="2a082-123">**アカウント ID**</span><span class="sxs-lookup"><span data-stu-id="2a082-123">**Account ID**</span></span>
    * <span data-ttu-id="2a082-124">**アカウント キー**</span><span class="sxs-lookup"><span data-stu-id="2a082-124">**Account Key**</span></span>

<span data-ttu-id="2a082-125">詳細については、[Azure Spatial Anchors の認証](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp)に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a082-125">Check out the [Azure Spatial Anchors authentication](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) docs for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="2a082-126">Unreal 4.25 での Azure Spatial Anchors では、Azure AD 認証トークンがサポートされていませんが、この機能のサポートは今後のリリースで導入される予定です。</span><span class="sxs-lookup"><span data-stu-id="2a082-126">Azure Spatial Anchors in Unreal 4.25 does not support Azure AD authentication tokens, but support for this functionality will be coming in a later release.</span></span>

## <a name="adding-azure-spatial-anchors-plugins"></a><span data-ttu-id="2a082-127">Azure Spatial Anchors プラグインを追加する</span><span class="sxs-lookup"><span data-stu-id="2a082-127">Adding Azure Spatial Anchors plugins</span></span>

<span data-ttu-id="2a082-128">Azure Spatial Anchors プラグインを、次のようにして、Unreal エディターで有効にします。</span><span class="sxs-lookup"><span data-stu-id="2a082-128">Enable the Azure Spatial Anchors plugins in the Unreal editor by:</span></span>
1. <span data-ttu-id="2a082-129">**[編集] > [プラグイン]** の順にクリックし、**AzureSpatialAnchors** と **AzureSpatialAnchorsForWMR** を検索します。</span><span class="sxs-lookup"><span data-stu-id="2a082-129">Clicking **Edit > Plugins** and searching for **AzureSpatialAnchors** and **AzureSpatialAnchorsForWMR**.</span></span>
2. <span data-ttu-id="2a082-130">両方のプラグインの **[有効]** チェックボックスをオンにして、アプリケーションの Azure Spatial Anchors ブループリント ライブラリへのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="2a082-130">Select the **Enabled** checkbox in both plugins to allow access to the Azure Spatial Anchors blueprint libraries in your application.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-01.png)

<span data-ttu-id="2a082-132">完了したら、プラグインの変更を有効にするために、Unreal エディターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="2a082-132">Once that's done, restart the Unreal Editor for the plugin changes to take effect.</span></span> <span data-ttu-id="2a082-133">これで、プロジェクトで Azure Spatial Anchors を使用する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="2a082-133">The project is now ready to use Azure Spatial Anchors.</span></span>

## <a name="starting-a-spatial-anchors-session"></a><span data-ttu-id="2a082-134">Spatial Anchors セッションを開始する</span><span class="sxs-lookup"><span data-stu-id="2a082-134">Starting a Spatial Anchors session</span></span>
<span data-ttu-id="2a082-135">Azure Spatial Anchors セッションを使用すると、クライアント アプリケーションが Azure Spatial Anchors サービスと通信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2a082-135">An Azure Spatial Anchors session allows client applications to communicate with the Azure Spatial Anchors service.</span></span> <span data-ttu-id="2a082-136">Azure 空間アンカーの作成、永続化、共有には、Azure Spatial Anchors セッションを作成して開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a082-136">You'll need to create and start an Azure Spatial Anchors session to create, persist, and share Azure Spatial Anchors:</span></span>

1. <span data-ttu-id="2a082-137">アプリケーションで使用しているポーンのブループリントを開きます。</span><span class="sxs-lookup"><span data-stu-id="2a082-137">Open the blueprint for the Pawn you're using in the application.</span></span>
2. <span data-ttu-id="2a082-138">**[アカウント ID]** と **[アカウント キー]** 用に 2 つの文字列変数を追加し、Azure Spatial Anchors アカウントから対応する値を割り当てて、セッションを認証します。</span><span class="sxs-lookup"><span data-stu-id="2a082-138">Add two string variables for the **Account ID** and **Account Key**, then assign the corresponding values from your Azure Spatial Anchors account to authenticate the session.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-02.png)

<span data-ttu-id="2a082-140">次の手順で、Azure Spatial Anchors セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="2a082-140">Start an Azure Spatial Anchors session by:</span></span>
1. <span data-ttu-id="2a082-141">**AR セッション** が HoloLens アプリケーションで実行されていることを確認します。これは、AR セッションが実行されていないと、Azure Spatial Anchors セッションを開始できないからです。</span><span class="sxs-lookup"><span data-stu-id="2a082-141">Checking that an **AR Session** is running in the HoloLens application, as the Azure Spatial Anchors session can't start until an AR Session is running.</span></span> <span data-ttu-id="2a082-142">セットアップされているものがない場合は、[AR セッション資産を作成](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)します。</span><span class="sxs-lookup"><span data-stu-id="2a082-142">If you don't have one setup, [create an AR Session asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>
2. <span data-ttu-id="2a082-143">**Start Azure Spatial Anchors Session** カスタム イベントを追加し、次のスクリーンショットに示すように構成します。</span><span class="sxs-lookup"><span data-stu-id="2a082-143">Adding the **Start Azure Spatial Anchors Session** custom event and configure it as shown in the screenshot below.</span></span>
    * <span data-ttu-id="2a082-144">セッションを作成しても、既定ではセッションは開始されません。このため、開発者は Azure Spatial Anchors サービスでの認証用にそのセッションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="2a082-144">Creating a session doesn't start the session by default, which allows the developer to configure the session for authentication with the Azure Spatial Anchors service.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. <span data-ttu-id="2a082-146">Azure Spatial Anchors セッションを構成して、 **[アカウント ID]** と **[アカウント キー]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="2a082-146">Configure the Azure Spatial Anchors session to provide the **Account ID** and **Account Key**.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. <span data-ttu-id="2a082-148">Azure Spatial Anchors セッションを開始し、アプリケーションで Azure 空間アンカーを作成して配置できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2a082-148">Start the Azure Spatial Anchors session, allowing the application to create and locate Azure Spatial Anchors.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-05.png)

<span data-ttu-id="2a082-150">サービスを使用しなくなった場合は、イベント グラフ ブループリントの Azure Spatial Anchors リソースをクリーンアップすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2a082-150">It's good practice to clean up Azure Spatial Anchors resources in your Event Graph blueprint when you're no longer using the service:</span></span>

1. <span data-ttu-id="2a082-151">その Azure Spatial Anchors セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="2a082-151">Stop the Azure Spatial Anchors session.</span></span> <span data-ttu-id="2a082-152">そのセッションは実行されなくなりますが、関連付けられているリソースは Azure Spatial Anchors プラグインにまだ存在しています。</span><span class="sxs-lookup"><span data-stu-id="2a082-152">The session will no longer be running, but its associated resources will still exist in the Azure Spatial Anchors plugin.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. <span data-ttu-id="2a082-154">Azure Spatial Anchors セッションを破棄して、その Azure Spatial Anchors プラグインでまだ認識されている Azure Spatial Anchors セッション リソースをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="2a082-154">Destroy the Azure Spatial Anchors session to clean up any Azure Spatial Anchors session resources still known to the Azure Spatial Anchors plugin.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-07.png)

<span data-ttu-id="2a082-156">イベント グラフ ブループリントは、次のスクリーンショットのようになります。</span><span class="sxs-lookup"><span data-stu-id="2a082-156">Your Event Graph blueprint should look like the screenshot below:</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-08.png)


## <a name="creating-an-anchor"></a><span data-ttu-id="2a082-158">アンカーを作成する</span><span class="sxs-lookup"><span data-stu-id="2a082-158">Creating an anchor</span></span>
<span data-ttu-id="2a082-159">Azure 空間アンカーは、拡張現実アプリケーション空間における現実世界のポーズを表します。これにより、拡張現実コンテンツが現実世界の場所に固定されます。</span><span class="sxs-lookup"><span data-stu-id="2a082-159">An Azure Spatial Anchor represents a physical world pose in the augmented reality application space, which locks augmented reality content to locations in the physical world.</span></span> <span data-ttu-id="2a082-160">Azure 空間アンカーは、異なるユーザー間で共有することもできます。</span><span class="sxs-lookup"><span data-stu-id="2a082-160">Azure Spatial Anchors can also be shared among different users.</span></span> <span data-ttu-id="2a082-161">この共有により、異なるデバイス上に描画される拡張現実コンテンツを、現実世界の同一の場所に配置することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="2a082-161">This sharing allows augmented reality content drawn on different devices to be positioned in the same location in the physical world.</span></span> 

<span data-ttu-id="2a082-162">新しい Azure 空間アンカーを作成するには:</span><span class="sxs-lookup"><span data-stu-id="2a082-162">To create a new Azure Spatial Anchor:</span></span>
1. <span data-ttu-id="2a082-163">Azure Spatial Anchors セッションが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2a082-163">Check that an Azure Spatial Anchors session is running.</span></span> <span data-ttu-id="2a082-164">Azure Spatial Anchors セッションが 1 つも実行されていない場合、アプリケーションは Azure 空間アンカーの作成や永続化を行えません。</span><span class="sxs-lookup"><span data-stu-id="2a082-164">The application can't create or persist an Azure Spatial Anchor when no Azure Spatial Anchors session is running.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. <span data-ttu-id="2a082-166">Unreal **[Scene コンポーネント](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** を作成または取得します。これは、場所が永続化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a082-166">Create or obtain an Unreal **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** that should have its location persisted.</span></span> 
    * <span data-ttu-id="2a082-167">次の図では、**Scene Component Needing Anchor** コンポーネントが変数として使用されています。</span><span class="sxs-lookup"><span data-stu-id="2a082-167">In the below image, the **Scene Component Needing Anchor** component is used as a variable.</span></span> <span data-ttu-id="2a082-168">Unreal Scene コンポーネントは、[AR ピン](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html)と Azure 空間アンカーのためのアプリケーション ワールド変換を確立するために必要です。</span><span class="sxs-lookup"><span data-stu-id="2a082-168">An Unreal Scene Component is needed to establish an application world transform for an [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) and Azure Spatial Anchor.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-10.png)

<span data-ttu-id="2a082-170">Unreal Scene コンポーネント用の Azure 空間アンカーを構築して保存するには:</span><span class="sxs-lookup"><span data-stu-id="2a082-170">To construct and save an Azure Spatial Anchor for an Unreal Scene Component:</span></span>
1. <span data-ttu-id="2a082-171">Unreal Scene コンポーネントの [Pin コンポーネント](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html)を呼び出し、Scene コンポーネントの **World Transform** を AR ピンで使用するワールド トランスフォームとして指定します。</span><span class="sxs-lookup"><span data-stu-id="2a082-171">Call the [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) for the Unreal Scene Component and specify the Scene Component's **World Transform** as the World Transform used for the AR Pin.</span></span>
    * <span data-ttu-id="2a082-172">Unreal は、AR ピンを使用してアプリケーション空間内の AR ポイントを追跡します。これは、Azure 空間アンカーを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="2a082-172">Unreal tracks AR points in the application space using AR Pins, which are used to create an Azure Spatial Anchor.</span></span> <span data-ttu-id="2a082-173">Unreal では、AR ピンは HoloLens の SpatialAnchor に似ています。</span><span class="sxs-lookup"><span data-stu-id="2a082-173">In Unreal, an AR Pin is analogous to a SpatialAnchor on HoloLens.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. <span data-ttu-id="2a082-175">新しく作成した AR ピンを使用して、**Create Cloud Anchor** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2a082-175">Call **Create Cloud Anchor** using the newly created AR Pin.</span></span>
    * <span data-ttu-id="2a082-176">Create Cloud Anchor では、Azure Spatial Anchors サービス内ではなく、ローカルに Azure 空間アンカーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2a082-176">Create Cloud Anchor creates an Azure Spatial Anchor locally but not in the Azure Spatial Anchor service.</span></span> <span data-ttu-id="2a082-177">Azure 空間アンカーの有効期限などのパラメーターは、サービスを使用して Azure 空間アンカーを作成する前に設定できます。</span><span class="sxs-lookup"><span data-stu-id="2a082-177">Parameters for the Azure Spatial Anchor, such as an expiration date, can be set before creating the Azure Spatial Anchor with the service.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. <span data-ttu-id="2a082-179">Azure 空間アンカーの有効期限を設定します。</span><span class="sxs-lookup"><span data-stu-id="2a082-179">Set the Azure Spatial Anchor expiration.</span></span> <span data-ttu-id="2a082-180">開発者は、この関数の Lifetime パラメーターを使用して、アンカーがサービスによって維持される期間を秒単位で指定できます。</span><span class="sxs-lookup"><span data-stu-id="2a082-180">This function's Lifetime parameter allows the developer to specify in seconds how long the anchor should be maintained by the service.</span></span>
    * <span data-ttu-id="2a082-181">たとえば、有効期限を 1 週間とする場合、60 秒 x 60 分 x 24 時間 x 7 日で、604,800 秒と指定します。</span><span class="sxs-lookup"><span data-stu-id="2a082-181">For example, a week long expiration would take a value of 60 seconds x 60 minutes x 24 hours x seven days = 604,800 seconds.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-13.png)

<span data-ttu-id="2a082-183">アンカーのパラメーターを設定したら、アンカーの保存準備ができたことを宣言します。</span><span class="sxs-lookup"><span data-stu-id="2a082-183">After setting anchor parameters, declare the anchor as ready to save.</span></span> <span data-ttu-id="2a082-184">次の例では、新しく作成した Azure 空間アンカーが、保存が必要な一連の Azure 空間アンカーに追加されています。</span><span class="sxs-lookup"><span data-stu-id="2a082-184">In the example below, the newly created Azure Spatial Anchor is added to a set of Azure Spatial Anchors needing saving.</span></span> <span data-ttu-id="2a082-185">このセットは、ポーン ブループリントの変数として宣言されています。</span><span class="sxs-lookup"><span data-stu-id="2a082-185">This set is declared as a variable for the Pawn blueprint.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a><span data-ttu-id="2a082-187">アンカーを保存する</span><span class="sxs-lookup"><span data-stu-id="2a082-187">Saving an Anchor</span></span>

<span data-ttu-id="2a082-188">パラメーターを指定して Azure 空間アンカーを構成したら、**Save Cloud Anchor** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2a082-188">After configuring the Azure Spatial Anchor with your parameters, call **Save Cloud Anchor**.</span></span> <span data-ttu-id="2a082-189">Save Cloud Anchor では、Azure Spatial Anchors サービスにそのアンカーが宣言されます。</span><span class="sxs-lookup"><span data-stu-id="2a082-189">Save Cloud Anchor declares the anchor to the Azure Spatial Anchors service.</span></span> <span data-ttu-id="2a082-190">Save Cloud Anchor への呼び出しが成功すると、Azure 空間アンカーは、その Azure Spatial Anchors サービスの他のユーザーにも使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2a082-190">When the call to Save Cloud Anchor succeeds, the Azure Spatial Anchor is available to other users of the Azure Spatial Anchor service.</span></span>  

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> <span data-ttu-id="2a082-192">Save Cloud Anchor は非同期関数で、**EventTick** などのゲーム スレッド イベントでのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="2a082-192">Save Cloud Anchor is an asynchronous function and can only be called on a game thread event such as **EventTick**.</span></span> <span data-ttu-id="2a082-193">Save Cloud Anchor は、カスタムのブループリント関数では、使用可能なブループリント関数として表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="2a082-193">Save Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="2a082-194">ただし、ポーン イベント グラフ ブループリント エディターでは使用できます。</span><span class="sxs-lookup"><span data-stu-id="2a082-194">However, it should be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="2a082-195">次の例では、Azure 空間アンカーは入力イベント コールバック中にセットに保存されます。</span><span class="sxs-lookup"><span data-stu-id="2a082-195">In the example below, the Azure Spatial Anchor is stored in a set during an input event callback.</span></span> <span data-ttu-id="2a082-196">その後、アンカーは EventTick に保存されます。</span><span class="sxs-lookup"><span data-stu-id="2a082-196">The anchor is then saved on the EventTick.</span></span> <span data-ttu-id="2a082-197">Azure Spatial Anchors セッションで作成した空間データの量によっては、Azure 空間アンカーの保存を複数回試行することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="2a082-197">Saving an Azure Spatial Anchor may take multiple attempts depending on the amount of spatial data that your Azure Spatial Anchors session has created.</span></span> <span data-ttu-id="2a082-198">そのため、保存の呼び出しが成功したかどうかを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2a082-198">That's why it's a good idea to check whether the save call succeeded.</span></span>

<span data-ttu-id="2a082-199">アンカーが保存されていない場合は、これから保存する必要のあるアンカーのセットにそのアンカーをもう一度追加します。</span><span class="sxs-lookup"><span data-stu-id="2a082-199">If the anchor doesn't save, re-add it to the set of anchors still needing to be saved.</span></span> <span data-ttu-id="2a082-200">将来的には、アンカーが Azure Spatial Anchors サービスに正常に保存されるまで、EventTick によってアンカーの保存が試みられるようになる予定です。</span><span class="sxs-lookup"><span data-stu-id="2a082-200">Future EventTicks will try to save the anchor until it's successfully stored in the Azure Spatial Anchor service.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-16.png)

<span data-ttu-id="2a082-202">アンカーが保存されると、その AR ピンの変換を、アプリケーションにコンテンツを配置するための参照変換として使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2a082-202">Once the anchor saves, you can use the AR Pins' transform as a reference transform for placing content in the application.</span></span> <span data-ttu-id="2a082-203">他のユーザーは、このアンカーを検出し、現実世界のさまざまなデバイス向けに AR コンテンツを配置できます。</span><span class="sxs-lookup"><span data-stu-id="2a082-203">Other users can detect this anchor and align AR content for different devices in the physical world.</span></span>

## <a name="deleting-an-anchor"></a><span data-ttu-id="2a082-204">アンカーを削除する</span><span class="sxs-lookup"><span data-stu-id="2a082-204">Deleting an Anchor</span></span>

<span data-ttu-id="2a082-205">**Delete Cloud Anchor** を呼び出して、Azure Spatial Anchors サービスからアンカーを削除できます。</span><span class="sxs-lookup"><span data-stu-id="2a082-205">You can delete anchors from the Azure Spatial Anchor service by calling **Delete Cloud Anchor**.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> <span data-ttu-id="2a082-207">Delete Cloud Anchor は潜在関数で、EventTick などのゲーム スレッド イベントでのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="2a082-207">Delete Cloud Anchor is a latent function and can only be called on a game thread event, such as EventTick.</span></span> <span data-ttu-id="2a082-208">Delete Cloud Anchor は、カスタムのブループリント関数では、使用可能なブループリント関数として表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="2a082-208">Delete Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="2a082-209">ただし、ポーン イベント グラフ ブループリント エディターでは使用できます。</span><span class="sxs-lookup"><span data-stu-id="2a082-209">It should however be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="2a082-210">次の例では、カスタム入力イベントで、アンカーに削除のフラグが設定されています。</span><span class="sxs-lookup"><span data-stu-id="2a082-210">In the example below, the anchor is flagged for deletion on a custom input event.</span></span> <span data-ttu-id="2a082-211">その後、EventTick で削除が試行されます。</span><span class="sxs-lookup"><span data-stu-id="2a082-211">The deletion is then attempted on the EventTick.</span></span> <span data-ttu-id="2a082-212">アンカーの削除が失敗した場合は、その Azure 空間アンカーを削除のフラグが設定されているアンカーのセットに追加し、EventTick で後でもう一度試行します。</span><span class="sxs-lookup"><span data-stu-id="2a082-212">If the anchor deletion fails, add the Azure Spatial Anchor to the set of anchors flagged for deletion and tries again on later EventTicks.</span></span>

<span data-ttu-id="2a082-213">イベント グラフ ブループリントは、次のスクリーンショットのようになります。</span><span class="sxs-lookup"><span data-stu-id="2a082-213">Your Event Graph blueprint should now look like the screenshot below:</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a><span data-ttu-id="2a082-215">既存のアンカーを検索する</span><span class="sxs-lookup"><span data-stu-id="2a082-215">Locating pre-existing anchors</span></span>

<span data-ttu-id="2a082-216">Azure 空間アンカーを作成するだけでなく、仲間が Azure Spatial Anchors サービスを使って作成したアンカーを検出することもできます。</span><span class="sxs-lookup"><span data-stu-id="2a082-216">In addition to creating Azure Spatial Anchors, you can detect anchors created by peers with the Azure Spatial Anchors service:</span></span>

1. <span data-ttu-id="2a082-217">検出したいアンカーの Azure 空間アンカー識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="2a082-217">Obtain an Azure Spatial Anchor identifier for the anchor that you would like to detect.</span></span>
    * <span data-ttu-id="2a082-218">アンカー識別子は、前の Azure Spatial Anchors セッションで同じデバイスによって作成されたアンカー用に取得できます。</span><span class="sxs-lookup"><span data-stu-id="2a082-218">An anchor identifier can be obtained for an anchor created by the same device in a previous Azure Spatial Anchors session.</span></span> <span data-ttu-id="2a082-219">また、その Azure Spatial Anchors サービスと対話するピア デバイスで作成して共有することもできます。</span><span class="sxs-lookup"><span data-stu-id="2a082-219">It can also be created and shared by peer devices interacting with the Azure Spatial Anchors service.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. <span data-ttu-id="2a082-221">**AzureSpatialAnchorsEvent** コンポーネントをポーン ブループリントに追加します。</span><span class="sxs-lookup"><span data-stu-id="2a082-221">Add an **AzureSpatialAnchorsEvent** component to your Pawn blueprint.</span></span>
    * <span data-ttu-id="2a082-222">このコンポーネントを使用すると、Azure 空間アンカーが検索されるときに呼び出されるイベントなど、さまざまな Azure Spatial Anchors イベントをサブスクライブできます。</span><span class="sxs-lookup"><span data-stu-id="2a082-222">This component allows you to subscribe to various Azure Spatial Anchors events, such as events called when Azure Spatial Anchors are located.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. <span data-ttu-id="2a082-224">**AzureSpatialAnchorsEvent** コンポーネントの **ASAAnchor Located Delegate** をサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="2a082-224">Subscribe to the **ASAAnchor Located Delegate** for the **AzureSpatialAnchorsEvent** component.</span></span>
    * <span data-ttu-id="2a082-225">このデリゲートを使用すると、Azure Spatial Anchors アカウントに関連付けられている新しいアンカーが検索されたときに、アプリケーションで認識できます。</span><span class="sxs-lookup"><span data-stu-id="2a082-225">The delegate lets the application know when new anchors associated with the Azure Spatial Anchors account have been located.</span></span>
    * <span data-ttu-id="2a082-226">このイベント コールバックでは、仲間が Azure Spatial Anchors セッションを使用して作成した Azure 空間アンカーには、既定で AR ピンが作成されません。</span><span class="sxs-lookup"><span data-stu-id="2a082-226">With the event callback, Azure Spatial Anchors created by peers using the Azure Spatial Anchors session won't have AR Pins created by default.</span></span> <span data-ttu-id="2a082-227">検出された Azure 空間アンカーの AR ピンを作成するため、開発者は **Create ARPin Around Azure Cloud Spatial Anchor** を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="2a082-227">To create an AR Pin for the detected Azure Spatial Anchor, developers can call **Create ARPin Around Azure Cloud Spatial Anchor**.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-20.png)

<span data-ttu-id="2a082-229">仲間が Azure Spatial Anchors サービスを使用して作成した Azure 空間アンカーを検索するには、そのアプリケーションで **Azure Spatial Anchors Watcher** を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2a082-229">In order to locate Azure Spatial Anchors created by peers using the Azure Spatial Anchor service, the application will have to create an **Azure Spatial Anchors Watcher**:</span></span>
1. <span data-ttu-id="2a082-230">Azure Spatial Anchors セッションが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2a082-230">Check that an Azure Spatial Anchors session is running.</span></span>
2. <span data-ttu-id="2a082-231">**AzureSpatialAnchorsLocateCriteria** を作成します。</span><span class="sxs-lookup"><span data-stu-id="2a082-231">Create an **AzureSpatialAnchorsLocateCriteria**.</span></span>
    * <span data-ttu-id="2a082-232">ユーザーからの距離や別のアンカーからの距離など、さまざまな位置パラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2a082-232">You can specify various location parameters like distance from the user or distance from another anchor.</span></span>
3. <span data-ttu-id="2a082-233">**AzureSpatialAnchorsLocateCritieria** で、目的の Azure 空間アンカー識別子を宣言します。</span><span class="sxs-lookup"><span data-stu-id="2a082-233">Declare your desired Azure Spatial Anchor identifier in the **AzureSpatialAnchorsLocateCritieria**.</span></span>
4. <span data-ttu-id="2a082-234">**Create Watcher** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2a082-234">Call **Create Watcher**.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-21.png)

<span data-ttu-id="2a082-236">これで、アプリケーションで、Azure Spatial Anchors サービスに認識されている Azure 空間アンカーの検索が開始されます。この結果、ユーザーは仲間が作成した Azure 空間アンカーを見つけることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="2a082-236">The application now begins looking for Azure Spatial Anchors known to the Azure Spatial Anchors service, meaning that users can locate Azure Spatial Anchors created by their peers.</span></span>

<span data-ttu-id="2a082-237">Azure 空間アンカーを見つけたら、**Stop Watcher** を呼び出して Azure Spatial Anchors Watcher を停止し、監視リソースをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="2a082-237">After locating the Azure Spatial Anchor, call **Stop Watcher** to stop the Azure Spatial Anchors Watcher and clean up watcher resources.</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-22.png)

<span data-ttu-id="2a082-239">最終的なイベント グラフ ブループリントは、次のスクリーンショットのようになります。</span><span class="sxs-lookup"><span data-stu-id="2a082-239">Your final Event Graph blueprint should now look like the screenshot below:</span></span>

![Spatial Anchors プラグイン](images/asa-unreal/unreal-spatial-anchors-img-23.png)

## <a name="next-development-checkpoint"></a><span data-ttu-id="2a082-241">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="2a082-241">Next Development Checkpoint</span></span>

<span data-ttu-id="2a082-242">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="2a082-242">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="2a082-243">ここから、次の構成要素に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="2a082-243">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="2a082-244">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="2a082-244">Spatial mapping</span></span>](unreal-spatial-mapping.md)

<span data-ttu-id="2a082-245">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="2a082-245">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2a082-246">HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="2a082-246">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="2a082-247">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="2a082-247">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="next-steps"></a><span data-ttu-id="2a082-248">次の手順</span><span class="sxs-lookup"><span data-stu-id="2a082-248">Next steps</span></span>
* [<span data-ttu-id="2a082-249">ローカル空間アンカー</span><span class="sxs-lookup"><span data-stu-id="2a082-249">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="2a082-250">Spatial Anchors のドキュメント</span><span class="sxs-lookup"><span data-stu-id="2a082-250">Spatial Anchors documentation</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)
* [<span data-ttu-id="2a082-251">空間アンカーの機能</span><span class="sxs-lookup"><span data-stu-id="2a082-251">Spatial Anchor features</span></span>](https://azure.microsoft.com/services/spatial-anchors/#features)
* [<span data-ttu-id="2a082-252">効果的なアンカー エクスペリエンスのガイドライン</span><span class="sxs-lookup"><span data-stu-id="2a082-252">Effective anchor experience guidelines</span></span>](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)