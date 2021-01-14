---
title: Unreal での Azure Spatial Anchors
description: Unreal Mixed Reality アプリケーションで既存の Azure Spatial Anchors を作成、管理、配置する方法について説明します。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, Azure, Azure 開発, Spatial Anchors, Mixed Reality, 開発, 機能, 新しいプロジェクト, エミュレーター, ドキュメント, ガイド, ホログラム, ゲーム開発, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 95e8ad708dd44a05fb306b2ea49f167fd400c5d8
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009772"
---
# <a name="azure-spatial-anchors-in-unreal"></a><span data-ttu-id="f12fe-104">Unreal での Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="f12fe-104">Azure Spatial Anchors in Unreal</span></span>

<span data-ttu-id="f12fe-105">Azure Spatial Anchors は、現実世界のアンカー ポイントを拡張現実デバイスを使って検出、共有、永続化できるようにする Microsoft Mixed Reality サービスです。</span><span class="sxs-lookup"><span data-stu-id="f12fe-105">Azure Spatial Anchors is a Microsoft Mixed Reality service, allowing augmented reality devices to discover, share, and persist anchor points in the physical world.</span></span> <span data-ttu-id="f12fe-106">このドキュメントでは、Azure Spatial Anchors サービスを Unreal プロジェクトに統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-106">Documentation below provides instructions for integrating the Azure Spatial Anchors service into an Unreal project.</span></span> <span data-ttu-id="f12fe-107">さらに情報が必要な場合は、[Azure Spatial Anchors サービス](https://azure.microsoft.com/services/spatial-anchors/)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f12fe-107">If you're looking for more information, check out the [Azure Spatial Anchors service](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

> [!NOTE]
> <span data-ttu-id="f12fe-108">Unreal Engine 4.26 には、iOS または Android を対象にする場合に ARKit と ARCore をサポートするためのプラグインが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f12fe-108">Unreal Engine 4.26 now has plugins for ARKit and ARCore support if you're targeting iOS or Android.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f12fe-109">ローカル アンカーはデバイスに格納されますが、Azure 空間アンカーはクラウドに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-109">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="f12fe-110">アンカーをデバイスにローカルに格納することをご希望の場合は、[ローカル空間アンカー](unreal-spatial-anchors.md)のドキュメントにその手順が説明されています。</span><span class="sxs-lookup"><span data-stu-id="f12fe-110">If you're looking to store your anchors locally on a device, we have a [Local Spatial Anchors](unreal-spatial-anchors.md) document that can walk you through the process.</span></span> <span data-ttu-id="f12fe-111">また、ローカル アンカーと Azure のアンカーは、競合することなく同じプロジェクトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-111">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f12fe-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="f12fe-112">Prerequisites</span></span>

<span data-ttu-id="f12fe-113">このガイドを完了するには、次のことが必要です。</span><span class="sxs-lookup"><span data-stu-id="f12fe-113">To complete this guide, make sure you have:</span></span>

- <span data-ttu-id="f12fe-114">インストール済みの [Unreal バージョン 4.25](https://www.unrealengine.com/get-now) 以降</span><span class="sxs-lookup"><span data-stu-id="f12fe-114">Installed [Unreal version 4.25](https://www.unrealengine.com/get-now) or later</span></span>
- <span data-ttu-id="f12fe-115">Unreal にセットアップされた [HoloLens 2 プロジェクト](tutorials/unreal-uxt-ch1.md)</span><span class="sxs-lookup"><span data-stu-id="f12fe-115">A [HoloLens 2 project](tutorials/unreal-uxt-ch1.md) setup in Unreal</span></span> 
- <span data-ttu-id="f12fe-116">「[Azure Spatial Anchors の概要](https://docs.microsoft.com/azure/spatial-anchors/overview)」の確認</span><span class="sxs-lookup"><span data-stu-id="f12fe-116">Read through the [Azure Spatial Anchors overview](https://docs.microsoft.com/azure/spatial-anchors/overview)</span></span>
- <span data-ttu-id="f12fe-117">C++ と Unreal に関する基本的な知識</span><span class="sxs-lookup"><span data-stu-id="f12fe-117">Basic knowledge on C++ and Unreal</span></span>

## <a name="getting-azure-spatial-anchors-account-info"></a><span data-ttu-id="f12fe-118">Azure Spatial Anchors アカウント情報を取得する</span><span class="sxs-lookup"><span data-stu-id="f12fe-118">Getting Azure Spatial Anchors account info</span></span>

<span data-ttu-id="f12fe-119">プロジェクトで Azure Spatial Anchors を使用する前に、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-119">Before using Azure Spatial Anchors in your project, you need to:</span></span>
* <span data-ttu-id="f12fe-120">[Spatial Anchors リソースを作成](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource)し、次に示すアカウント フィールドをコピーします。</span><span class="sxs-lookup"><span data-stu-id="f12fe-120">[Create a spatial anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) and copy the account fields listed below.</span></span> <span data-ttu-id="f12fe-121">これらの値は、アプリケーションのアカウントでユーザーを認証するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-121">These values are used to authenticate users with your application's account:</span></span>
    * <span data-ttu-id="f12fe-122">**アカウント ID**</span><span class="sxs-lookup"><span data-stu-id="f12fe-122">**Account ID**</span></span>
    * <span data-ttu-id="f12fe-123">**アカウント キー**</span><span class="sxs-lookup"><span data-stu-id="f12fe-123">**Account Key**</span></span>

<span data-ttu-id="f12fe-124">詳細については、[Azure Spatial Anchors の認証](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp)に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f12fe-124">Check out the [Azure Spatial Anchors authentication](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) docs for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="f12fe-125">Unreal 4.25 での Azure Spatial Anchors では、Azure AD 認証トークンがサポートされていませんが、この機能のサポートは今後のリリースで導入される予定です。</span><span class="sxs-lookup"><span data-stu-id="f12fe-125">Azure Spatial Anchors in Unreal 4.25 does not support Azure AD authentication tokens, but support for this functionality will be coming in a later release.</span></span>

## <a name="adding-azure-spatial-anchors-plugins"></a><span data-ttu-id="f12fe-126">Azure Spatial Anchors プラグインを追加する</span><span class="sxs-lookup"><span data-stu-id="f12fe-126">Adding Azure Spatial Anchors plugins</span></span>

<span data-ttu-id="f12fe-127">Azure Spatial Anchors プラグインを、次のようにして、Unreal エディターで有効にします。</span><span class="sxs-lookup"><span data-stu-id="f12fe-127">Enable the Azure Spatial Anchors plugins in the Unreal editor by:</span></span>
1. <span data-ttu-id="f12fe-128">**[編集] > [プラグイン]** の順にクリックし、**AzureSpatialAnchors** と **AzureSpatialAnchorsForWMR** を検索します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-128">Clicking **Edit > Plugins** and searching for **AzureSpatialAnchors** and **AzureSpatialAnchorsForWMR**.</span></span>
2. <span data-ttu-id="f12fe-129">両方のプラグインの **[有効]** チェックボックスをオンにして、アプリケーションの Azure Spatial Anchors ブループリント ライブラリへのアクセスを許可します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-129">Select the **Enabled** checkbox in both plugins to allow access to the Azure Spatial Anchors blueprint libraries in your application.</span></span>

![Unreal エディターでの Spatial Anchors プラグインのスクリーンショット](images/asa-unreal/unreal-spatial-anchors-img-01.png)

<span data-ttu-id="f12fe-131">完了したら、プラグインの変更を有効にするために、Unreal エディターを再起動します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-131">Once that's done, restart the Unreal Editor for the plugin changes to take effect.</span></span> <span data-ttu-id="f12fe-132">これで、プロジェクトで Azure Spatial Anchors を使用する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="f12fe-132">The project is now ready to use Azure Spatial Anchors.</span></span>

## <a name="starting-a-spatial-anchors-session"></a><span data-ttu-id="f12fe-133">Spatial Anchors セッションを開始する</span><span class="sxs-lookup"><span data-stu-id="f12fe-133">Starting a Spatial Anchors session</span></span>

<span data-ttu-id="f12fe-134">Azure Spatial Anchors セッションを使用すると、クライアント アプリケーションが Azure Spatial Anchors サービスと通信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-134">An Azure Spatial Anchors session allows client applications to communicate with the Azure Spatial Anchors service.</span></span> <span data-ttu-id="f12fe-135">Azure 空間アンカーの作成、永続化、共有には、Azure Spatial Anchors セッションを作成して開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-135">You'll need to create and start an Azure Spatial Anchors session to create, persist, and share Azure Spatial Anchors:</span></span>

1. <span data-ttu-id="f12fe-136">アプリケーションで使用しているポーンのブループリントを開きます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-136">Open the blueprint for the Pawn you're using in the application.</span></span>
2. <span data-ttu-id="f12fe-137">**[アカウント ID]** と **[アカウント キー]** 用に 2 つの文字列変数を追加し、Azure Spatial Anchors アカウントから対応する値を割り当てて、セッションを認証します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-137">Add two string variables for the **Account ID** and **Account Key**, then assign the corresponding values from your Azure Spatial Anchors account to authenticate the session.</span></span>

![Azure Spatial Anchors のアカウント ID、キー、変数の種類が強調表示されている詳細パネルのスクリーンショット](images/asa-unreal/unreal-spatial-anchors-img-02.png)

<span data-ttu-id="f12fe-139">次の手順で、Azure Spatial Anchors セッションを開始します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-139">Start an Azure Spatial Anchors session by:</span></span>
1. <span data-ttu-id="f12fe-140">**AR セッション** が HoloLens アプリケーションで実行されていることを確認します。これは、AR セッションが実行されていないと、Azure Spatial Anchors セッションを開始できないからです。</span><span class="sxs-lookup"><span data-stu-id="f12fe-140">Checking that an **AR Session** is running in the HoloLens application, as the Azure Spatial Anchors session can't start until an AR Session is running.</span></span> <span data-ttu-id="f12fe-141">セットアップされているものがない場合は、[AR セッション資産を作成](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-141">If you don't have one setup, [create an AR Session asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>
2. <span data-ttu-id="f12fe-142">**Start Azure Spatial Anchors Session** カスタム イベントを追加し、次のスクリーンショットに示すように構成します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-142">Adding the **Start Azure Spatial Anchors Session** custom event and configure it as shown in the screenshot below.</span></span>
    * <span data-ttu-id="f12fe-143">セッションを作成しても、既定ではセッションは開始されません。このため、Azure Spatial Anchors サービスでの認証用にセッションを構成できます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-143">Creating a session doesn't start the session by default, which allows you to configure the session for authentication with the Azure Spatial Anchors service.</span></span>

![Azure Spatial Anchors セッション開始中カスタム イベントのブループリント](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. <span data-ttu-id="f12fe-145">Azure Spatial Anchors セッションを構成して、 **[アカウント ID]** と **[アカウント キー]** を指定します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-145">Configure the Azure Spatial Anchors session to provide the **Account ID** and **Account Key**.</span></span>

![アカウント ID とキーが追加されたセッション構成関数のブループリント](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. <span data-ttu-id="f12fe-147">Azure Spatial Anchors セッションを開始し、アプリケーションで Azure 空間アンカーを作成して配置できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f12fe-147">Start the Azure Spatial Anchors session, allowing the application to create and locate Azure Spatial Anchors.</span></span>

![Azure Spatial Anchors セッション開始関数のブループリント](images/asa-unreal/unreal-spatial-anchors-img-05.png)

<span data-ttu-id="f12fe-149">サービスを使用しなくなった場合は、イベント グラフ ブループリントの Azure Spatial Anchors リソースをクリーンアップすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f12fe-149">It's good practice to clean up Azure Spatial Anchors resources in your Event Graph blueprint when you're no longer using the service:</span></span>

1. <span data-ttu-id="f12fe-150">その Azure Spatial Anchors セッションを停止します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-150">Stop the Azure Spatial Anchors session.</span></span> <span data-ttu-id="f12fe-151">そのセッションは実行されなくなりますが、関連付けられているリソースは Azure Spatial Anchors プラグインにまだ存在しています。</span><span class="sxs-lookup"><span data-stu-id="f12fe-151">The session will no longer be running, but its associated resources will still exist in the Azure Spatial Anchors plugin.</span></span>

![Azure Spatial Anchors セッション停止カスタム イベントとセッション停止関数のブループリント](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. <span data-ttu-id="f12fe-153">Azure Spatial Anchors セッションを破棄して、その Azure Spatial Anchors プラグインでまだ認識されている Azure Spatial Anchors セッション リソースをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="f12fe-153">Destroy the Azure Spatial Anchors session to clean up any Azure Spatial Anchors session resources still known to the Azure Spatial Anchors plugin.</span></span>

![セッション破棄関数のブループリント](images/asa-unreal/unreal-spatial-anchors-img-07.png)

<span data-ttu-id="f12fe-155">イベント グラフ ブループリントは、次のスクリーンショットのようになります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-155">Your Event Graph blueprint should look like the screenshot below:</span></span>

![Azure Spatial Anchors セッション セットアップの完全なイベント グラフのブループリント](images/asa-unreal/unreal-spatial-anchors-img-08.png)

## <a name="creating-an-anchor"></a><span data-ttu-id="f12fe-157">アンカーを作成する</span><span class="sxs-lookup"><span data-stu-id="f12fe-157">Creating an anchor</span></span>

<span data-ttu-id="f12fe-158">Azure 空間アンカーは、拡張現実アプリケーション空間における現実世界のポーズを表します。これにより、拡張現実コンテンツが物理的な場所に固定されます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-158">An Azure Spatial Anchor represents a physical world pose in the augmented reality application space, which locks augmented reality content to physical locations.</span></span> <span data-ttu-id="f12fe-159">Azure 空間アンカーは、異なるユーザー間で共有することもできます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-159">Azure Spatial Anchors can also be shared among different users.</span></span> <span data-ttu-id="f12fe-160">この共有により、異なるデバイス上に描画される拡張現実コンテンツを、現実世界の同一の場所に配置することが可能になります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-160">This sharing allows augmented reality content drawn on different devices to be positioned in the same location in the physical world.</span></span> 

<span data-ttu-id="f12fe-161">新しい Azure 空間アンカーを作成するには:</span><span class="sxs-lookup"><span data-stu-id="f12fe-161">To create a new Azure Spatial Anchor:</span></span>
1. <span data-ttu-id="f12fe-162">Azure Spatial Anchors セッションが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-162">Check that an Azure Spatial Anchors session is running.</span></span> <span data-ttu-id="f12fe-163">Azure Spatial Anchors セッションが 1 つも実行されていない場合、アプリケーションは Azure 空間アンカーの作成や永続化を行えません。</span><span class="sxs-lookup"><span data-stu-id="f12fe-163">The application can't create or persist an Azure Spatial Anchor when no Azure Spatial Anchors session is running.</span></span>

![Azure 空間アンカー作成カスタム イベントのブループリント](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. <span data-ttu-id="f12fe-165">Unreal **[Scene コンポーネント](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** を作成または取得します。これは、場所が永続化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-165">Create or obtain an Unreal **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** that should have its location persisted.</span></span> 
    * <span data-ttu-id="f12fe-166">次の図では、**Scene Component Needing Anchor** コンポーネントが変数として使用されています。</span><span class="sxs-lookup"><span data-stu-id="f12fe-166">In the below image, the **Scene Component Needing Anchor** component is used as a variable.</span></span> <span data-ttu-id="f12fe-167">Unreal Scene コンポーネントは、[AR ピン](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html)と Azure 空間アンカーのためのアプリケーション ワールド変換を確立するために必要です。</span><span class="sxs-lookup"><span data-stu-id="f12fe-167">An Unreal Scene Component is needed to establish an application world transform for an [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) and Azure Spatial Anchor.</span></span>

![シーン コンポーネントを含む Azure 空間アンカー作成カスタム イベントのブループリント](images/asa-unreal/unreal-spatial-anchors-img-10.png)

<span data-ttu-id="f12fe-169">Unreal Scene コンポーネント用の Azure 空間アンカーを構築して保存するには:</span><span class="sxs-lookup"><span data-stu-id="f12fe-169">To construct and save an Azure Spatial Anchor for an Unreal Scene Component:</span></span>
1. <span data-ttu-id="f12fe-170">Unreal Scene コンポーネントの [Pin コンポーネント](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html)を呼び出し、Scene コンポーネントの **World Transform** を AR ピンで使用するワールド トランスフォームとして指定します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-170">Call the [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) for the Unreal Scene Component and specify the Scene Component's **World Transform** as the World Transform used for the AR Pin.</span></span>
    * <span data-ttu-id="f12fe-171">Unreal は、AR ピンを使用してアプリケーション空間内の AR ポイントを追跡します。これは、Azure 空間アンカーを作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-171">Unreal tracks AR points in the application space using AR Pins, which are used to create an Azure Spatial Anchor.</span></span> <span data-ttu-id="f12fe-172">Unreal では、AR ピンは HoloLens の SpatialAnchor に似ています。</span><span class="sxs-lookup"><span data-stu-id="f12fe-172">In Unreal, an AR Pin is analogous to a SpatialAnchor on HoloLens.</span></span>

![ピン コンポーネント関数に接続されているシーン コンポーネントのブループリント](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. <span data-ttu-id="f12fe-174">新しく作成した AR ピンを使用して、**Create Cloud Anchor** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-174">Call **Create Cloud Anchor** using the newly created AR Pin.</span></span>
    * <span data-ttu-id="f12fe-175">Create Cloud Anchor では、Azure Spatial Anchors サービス内ではなく、ローカルに Azure 空間アンカーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-175">Create Cloud Anchor creates an Azure Spatial Anchor locally but not in the Azure Spatial Anchor service.</span></span> <span data-ttu-id="f12fe-176">Azure 空間アンカーの有効期限などのパラメーターは、サービスを使用して Azure 空間アンカーを作成する前に設定できます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-176">Parameters for the Azure Spatial Anchor, such as an expiration date, can be set before creating the Azure Spatial Anchor with the service.</span></span>

![ARPin を返すクラウド アンカー作成関数に接続されたピン コンポーネント関数のブループリント](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. <span data-ttu-id="f12fe-178">Azure 空間アンカーの有効期限を設定します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-178">Set the Azure Spatial Anchor expiration.</span></span> <span data-ttu-id="f12fe-179">開発者は、この関数の Lifetime パラメーターを使用して、アンカーがサービスによって維持される期間を秒単位で指定できます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-179">This function's Lifetime parameter allows the developer to specify in seconds how long the anchor should be maintained by the service.</span></span>
    * <span data-ttu-id="f12fe-180">たとえば、有効期限を 1 週間とする場合、60 秒 x 60 分 x 24 時間 x 7 日で、604,800 秒と指定します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-180">For example, a week long expiration would take a value of 60 seconds x 60 minutes x 24 hours x seven days = 604,800 seconds.</span></span>

![有効期間の値が 604,800 秒に設定された有効期間設定関数に接続されたクラウド アンカーのブループリント](images/asa-unreal/unreal-spatial-anchors-img-13.png)

<span data-ttu-id="f12fe-182">アンカーのパラメーターを設定したら、アンカーの保存準備ができたことを宣言します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-182">After setting anchor parameters, declare the anchor as ready to save.</span></span> <span data-ttu-id="f12fe-183">次の例では、新しく作成した Azure 空間アンカーが、保存が必要な一連の Azure 空間アンカーに追加されています。</span><span class="sxs-lookup"><span data-stu-id="f12fe-183">In the example below, the newly created Azure Spatial Anchor is added to a set of Azure Spatial Anchors needing saving.</span></span> <span data-ttu-id="f12fe-184">このセットは、ポーン ブループリントの変数として宣言されています。</span><span class="sxs-lookup"><span data-stu-id="f12fe-184">This set is declared as a variable for the Pawn blueprint.</span></span>

![セット変数に保存できるアンカーのブループリント](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a><span data-ttu-id="f12fe-186">アンカーを保存する</span><span class="sxs-lookup"><span data-stu-id="f12fe-186">Saving an Anchor</span></span>

<span data-ttu-id="f12fe-187">パラメーターを指定して Azure 空間アンカーを構成したら、**Save Cloud Anchor** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-187">After configuring the Azure Spatial Anchor with your parameters, call **Save Cloud Anchor**.</span></span> <span data-ttu-id="f12fe-188">Save Cloud Anchor では、Azure Spatial Anchors サービスにそのアンカーが宣言されます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-188">Save Cloud Anchor declares the anchor to the Azure Spatial Anchors service.</span></span> <span data-ttu-id="f12fe-189">Save Cloud Anchor への呼び出しが成功すると、Azure 空間アンカーは、その Azure Spatial Anchors サービスの他のユーザーにも使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-189">When the call to Save Cloud Anchor succeeds, the Azure Spatial Anchor is available to other users of the Azure Spatial Anchor service.</span></span>  

![クラウドアンカー保存関数が呼び出されているブループリント](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> <span data-ttu-id="f12fe-191">Save Cloud Anchor は非同期関数で、**EventTick** などのゲーム スレッド イベントでのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-191">Save Cloud Anchor is an asynchronous function and can only be called on a game thread event such as **EventTick**.</span></span> <span data-ttu-id="f12fe-192">Save Cloud Anchor は、カスタムのブループリント関数では、使用可能なブループリント関数として表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-192">Save Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="f12fe-193">ただし、ポーン イベント グラフ ブループリント エディターでは使用できます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-193">However, it should be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="f12fe-194">次の例では、Azure 空間アンカーは入力イベント コールバック中にセットに保存されます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-194">In the example below, the Azure Spatial Anchor is stored in a set during an input event callback.</span></span> <span data-ttu-id="f12fe-195">その後、アンカーは EventTick に保存されます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-195">The anchor is then saved on the EventTick.</span></span> <span data-ttu-id="f12fe-196">Azure Spatial Anchors セッションで作成した空間データの量によっては、Azure 空間アンカーの保存を複数回試行することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-196">Saving an Azure Spatial Anchor may take multiple attempts depending on the amount of spatial data that your Azure Spatial Anchors session has created.</span></span> <span data-ttu-id="f12fe-197">そのため、保存の呼び出しが成功したかどうかを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f12fe-197">That's why it's a good idea to check whether the save call succeeded.</span></span>

<span data-ttu-id="f12fe-198">アンカーが保存されていない場合は、これから保存する必要のあるアンカーのセットにそのアンカーをもう一度追加します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-198">If the anchor doesn't save, readd it to the set of anchors still needing to be saved.</span></span> <span data-ttu-id="f12fe-199">将来的には、アンカーが正常に保存されるまで、EventTick によるアンカー保存の試みが続けられるようになります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-199">Future EventTicks will keep trying to save the anchor until it's successfully stored.</span></span>

![保存されていないアンカーがセット変数に再び保存されるブループリント](images/asa-unreal/unreal-spatial-anchors-img-16.png)

<span data-ttu-id="f12fe-201">アンカーが保存されると、その AR ピンの変換が、アプリにコンテンツを配置するための参照変換として機能するようになります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-201">Once the anchor saves, the AR Pins' transform acts as a reference transform for placing content in your app.</span></span> <span data-ttu-id="f12fe-202">他のユーザーは、このアンカーを検出し、現実世界のさまざまなデバイス向けに AR コンテンツを配置できます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-202">Other users can detect this anchor and align AR content for different devices in the physical world.</span></span>

## <a name="deleting-an-anchor"></a><span data-ttu-id="f12fe-203">アンカーを削除する</span><span class="sxs-lookup"><span data-stu-id="f12fe-203">Deleting an Anchor</span></span>

<span data-ttu-id="f12fe-204">**Delete Cloud Anchor** を呼び出して、Azure Spatial Anchors サービスからアンカーを削除できます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-204">You can delete anchors from the Azure Spatial Anchor service by calling **Delete Cloud Anchor**.</span></span>

![クラウド アンカー削除関数が呼び出されているブループリント](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> <span data-ttu-id="f12fe-206">Delete Cloud Anchor は潜在関数で、EventTick などのゲーム スレッド イベントでのみ呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-206">Delete Cloud Anchor is a latent function and can only be called on a game thread event, such as EventTick.</span></span> <span data-ttu-id="f12fe-207">Delete Cloud Anchor は、カスタムのブループリント関数では、使用可能なブループリント関数として表示されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-207">Delete Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="f12fe-208">ただし、ポーン イベント グラフ ブループリント エディターでは使用できます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-208">It should however be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="f12fe-209">次の例では、カスタム入力イベントで、アンカーに削除のフラグが設定されています。</span><span class="sxs-lookup"><span data-stu-id="f12fe-209">In the example below, the anchor is flagged for deletion on a custom input event.</span></span> <span data-ttu-id="f12fe-210">その後、EventTick で削除が試行されます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-210">The deletion is then attempted on the EventTick.</span></span> <span data-ttu-id="f12fe-211">アンカーの削除が失敗した場合は、その Azure 空間アンカーを削除のフラグが設定されているアンカーのセットに追加し、EventTick で後でもう一度試行します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-211">If the anchor deletion fails, add the Azure Spatial Anchor to the set of anchors flagged for deletion and tries again on later EventTicks.</span></span>

<span data-ttu-id="f12fe-212">イベント グラフ ブループリントは、次のスクリーンショットのようになります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-212">Your Event Graph blueprint should now look like the screenshot below:</span></span>

![クラウド アンカー処理の完全なイベント グラフのブループリント](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a><span data-ttu-id="f12fe-214">既存のアンカーを検索する</span><span class="sxs-lookup"><span data-stu-id="f12fe-214">Locating pre-existing anchors</span></span>

<span data-ttu-id="f12fe-215">既存のアンカーは、Azure Spatial Anchors サービスとのピアによって作成できます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-215">Existing anchors can be created by peers with the Azure Spatial Anchors service:</span></span>

1. <span data-ttu-id="f12fe-216">検出したいアンカーの Azure 空間アンカー識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-216">Obtain an Azure Spatial Anchor identifier for the anchor that you would like to detect.</span></span>
    * <span data-ttu-id="f12fe-217">アンカー識別子は、前の Azure Spatial Anchors セッションで同じデバイスによって作成されたアンカー用に取得できます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-217">An anchor identifier can be obtained for an anchor created by the same device in a previous Azure Spatial Anchors session.</span></span> <span data-ttu-id="f12fe-218">また、その Azure Spatial Anchors サービスと対話するピア デバイスで作成して共有することもできます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-218">It can also be created and shared by peer devices interacting with the Azure Spatial Anchors service.</span></span>

![Azure 空間アンカー識別子格納カスタム イベントと Azure クラウド識別子取得関数のブループリント](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. <span data-ttu-id="f12fe-220">**AzureSpatialAnchorsEvent** コンポーネントをポーン ブループリントに追加します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-220">Add an **AzureSpatialAnchorsEvent** component to your Pawn blueprint.</span></span>
    * <span data-ttu-id="f12fe-221">このコンポーネントを使用すると、Azure 空間アンカーが検索されるときに呼び出されるイベントなど、さまざまな Azure Spatial Anchors イベントをサブスクライブできます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-221">This component allows you to subscribe to various Azure Spatial Anchors events, such as events called when Azure Spatial Anchors are located.</span></span>

![BP_Pawn がブループリント エディターで開かれ、コンポーネント パネルと詳細パネルが開いているスクリーンショット](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. <span data-ttu-id="f12fe-223">**AzureSpatialAnchorsEvent** コンポーネントの **ASAAnchor Located Delegate** をサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="f12fe-223">Subscribe to the **ASAAnchor Located Delegate** for the **AzureSpatialAnchorsEvent** component.</span></span>
    * <span data-ttu-id="f12fe-224">このデリゲートを使用すると、Azure Spatial Anchors アカウントに関連付けられている新しいアンカーが検索されたときに、アプリケーションで認識できます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-224">The delegate lets the application know when new anchors associated with the Azure Spatial Anchors account have been located.</span></span>
    * <span data-ttu-id="f12fe-225">このイベント コールバックでは、仲間が Azure Spatial Anchors セッションを使用して作成した Azure 空間アンカーには、既定で AR ピンが作成されません。</span><span class="sxs-lookup"><span data-stu-id="f12fe-225">With the event callback, Azure Spatial Anchors created by peers using the Azure Spatial Anchors session won't have AR Pins created by default.</span></span> <span data-ttu-id="f12fe-226">検出された Azure 空間アンカーの AR ピンを作成するため、開発者は **Create ARPin Around Azure Cloud Spatial Anchor** を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-226">To create an AR Pin for the detected Azure Spatial Anchor, developers can call **Create ARPin Around Azure Cloud Spatial Anchor**.</span></span>

![ASAAnchor Located Delegate に接続されたプレイ開始イベントのブループリント](images/asa-unreal/unreal-spatial-anchors-img-20.png)

<span data-ttu-id="f12fe-228">Azure Spatial Anchors サービスを使用してピアによって作成された Azure 空間アンカーを検索するには、そのアプリケーションで **Azure Spatial Anchors Watcher** を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-228">To locate Azure Spatial Anchors created by peers using the Azure Spatial Anchor service, the application will have to create an **Azure Spatial Anchors Watcher**:</span></span>
1. <span data-ttu-id="f12fe-229">Azure Spatial Anchors セッションが実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-229">Check that an Azure Spatial Anchors session is running.</span></span>
2. <span data-ttu-id="f12fe-230">**AzureSpatialAnchorsLocateCriteria** を作成します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-230">Create an **AzureSpatialAnchorsLocateCriteria**.</span></span>
    * <span data-ttu-id="f12fe-231">ユーザーからの距離や別のアンカーからの距離など、さまざまな位置パラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-231">You can specify various location parameters like distance from the user or distance from another anchor.</span></span>
3. <span data-ttu-id="f12fe-232">**AzureSpatialAnchorsLocateCritieria** で、探している Azure 空間アンカー識別子を宣言します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-232">Declare the Azure Spatial Anchor identifier you're looking for in the **AzureSpatialAnchorsLocateCritieria**.</span></span>
4. <span data-ttu-id="f12fe-233">**Create Watcher** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-233">Call **Create Watcher**.</span></span>

![Azure Spatial Anchors 監視開始カスタム イベントのブループリント](images/asa-unreal/unreal-spatial-anchors-img-21.png)

<span data-ttu-id="f12fe-235">これで、アプリケーションで、Azure Spatial Anchors サービスに認識されている Azure 空間アンカーの検索が開始されます。この結果、ユーザーは仲間が作成した Azure 空間アンカーを見つけることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-235">The application now begins looking for Azure Spatial Anchors known to the Azure Spatial Anchors service, meaning that users can locate Azure Spatial Anchors created by their peers.</span></span>

<span data-ttu-id="f12fe-236">Azure 空間アンカーを見つけたら、**Stop Watcher** を呼び出して Azure Spatial Anchors Watcher を停止し、監視リソースをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="f12fe-236">After locating the Azure Spatial Anchor, call **Stop Watcher** to stop the Azure Spatial Anchors Watcher and clean up watcher resources.</span></span>

![監視停止関数の呼び出しのブループリント](images/asa-unreal/unreal-spatial-anchors-img-22.png)

<span data-ttu-id="f12fe-238">最終的なイベント グラフ ブループリントは、次のスクリーンショットのようになります。</span><span class="sxs-lookup"><span data-stu-id="f12fe-238">Your final Event Graph blueprint should now look like the screenshot below:</span></span>

![アンカー委任イベントの処理の完全なイベント グラフのブループリント](images/asa-unreal/unreal-spatial-anchors-img-23.png)

## <a name="next-development-checkpoint"></a><span data-ttu-id="f12fe-240">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="f12fe-240">Next Development Checkpoint</span></span>

<span data-ttu-id="f12fe-241">用意されている Unreal 開発体験に従っている場合、MRTK コア構成要素を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-241">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="f12fe-242">ここから、次の構成要素を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-242">From here, you can continue to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="f12fe-243">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="f12fe-243">Spatial mapping</span></span>](unreal-spatial-mapping.md)

<span data-ttu-id="f12fe-244">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="f12fe-244">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f12fe-245">HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="f12fe-245">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="f12fe-246">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="f12fe-246">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="next-steps"></a><span data-ttu-id="f12fe-247">次の手順</span><span class="sxs-lookup"><span data-stu-id="f12fe-247">Next steps</span></span>
* [<span data-ttu-id="f12fe-248">ローカル空間アンカー</span><span class="sxs-lookup"><span data-stu-id="f12fe-248">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="f12fe-249">Spatial Anchors のドキュメント</span><span class="sxs-lookup"><span data-stu-id="f12fe-249">Spatial Anchors documentation</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)
* [<span data-ttu-id="f12fe-250">空間アンカーの機能</span><span class="sxs-lookup"><span data-stu-id="f12fe-250">Spatial Anchor features</span></span>](https://azure.microsoft.com/services/spatial-anchors/#features)
* [<span data-ttu-id="f12fe-251">効果的なアンカー エクスペリエンスのガイドライン</span><span class="sxs-lookup"><span data-stu-id="f12fe-251">Effective anchor experience guidelines</span></span>](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)