---
title: 複数のユーザーの接続
description: このコースを完了すると、HoloLens 2 Mixed Reality アプリケーション内で複数のユーザーを接続する方法がわかります。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, マルチユーザー機能, Photon, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー
ms.localizationpriority: high
ms.openlocfilehash: 6cc77b32e9479bafeb53dcb99cba4f2f29865fd7
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007212"
---
# <a name="3-connecting-multiple-users"></a><span data-ttu-id="60e62-104">3.複数のユーザーの接続</span><span class="sxs-lookup"><span data-stu-id="60e62-104">3. Connecting multiple users</span></span>

<span data-ttu-id="60e62-105">このチュートリアルでは、ライブ共有エクスペリエンスの一部として複数のユーザーを接続する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="60e62-105">In this tutorial, you will learn how to connect multiple users as part of a live shared experience.</span></span> <span data-ttu-id="60e62-106">チュートリアルを終えるときには、複数のデバイスでアプリを実行して、各ユーザーが他のユーザーのアバターの動きをリアルタイムで確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="60e62-106">By the end of the tutorial, you will be able to run the app on multiple devices and have each user see the avatar of other users move in real-time.</span></span>

## <a name="objectives"></a><span data-ttu-id="60e62-107">目標</span><span class="sxs-lookup"><span data-stu-id="60e62-107">Objectives</span></span>

* <span data-ttu-id="60e62-108">共有エクスペリエンスで複数のユーザーを接続する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="60e62-108">Learn how to connect multiple users in a shared experience</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="60e62-109">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="60e62-109">Preparing the scene</span></span>

<span data-ttu-id="60e62-110">このセクションでは、チュートリアルのプレハブをいくつか追加してシーンを準備します。</span><span class="sxs-lookup"><span data-stu-id="60e62-110">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="60e62-111">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動し、次のプレハブを [Hierarchy]\(階層\) ウィンドウにドラッグしてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="60e62-111">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="60e62-112">**NetworkLobby** プレハブ</span><span class="sxs-lookup"><span data-stu-id="60e62-112">**NetworkLobby** prefab</span></span>
* <span data-ttu-id="60e62-113">**SharedPlayground** プレハブ</span><span class="sxs-lookup"><span data-stu-id="60e62-113">**SharedPlayground** prefab</span></span>

![新しく追加された NetworkLobby と SharedPlayground プレハブが選択されている Unity](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

<span data-ttu-id="60e62-115">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.AzureSpatialAnchors]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動し、次のプレハブを [Hierarchy]\(階層\) ウィンドウにドラッグしてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="60e62-115">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefab into the Hierarchy window to add it to your scene:</span></span>

* <span data-ttu-id="60e62-116">**DebugWindow** プレハブ</span><span class="sxs-lookup"><span data-stu-id="60e62-116">**DebugWindow** prefab</span></span>

![新しく追加された DebugWindow プレハブが選択されている Unity](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="creating-the-user-prefab"></a><span data-ttu-id="60e62-118">ユーザー プレハブを作成する</span><span class="sxs-lookup"><span data-stu-id="60e62-118">Creating the user prefab</span></span>

<span data-ttu-id="60e62-119">このセクションでは、共有エクスペリエンスでユーザーを表すために使用されるプレハブを作成します。</span><span class="sxs-lookup"><span data-stu-id="60e62-119">In this section, you will create a prefab that will be used to represent the users in the shared experience.</span></span>

### <a name="1-create-and-configure-the-user"></a><span data-ttu-id="60e62-120">1.ユーザーの作成と構成</span><span class="sxs-lookup"><span data-stu-id="60e62-120">1. Create and configure the user</span></span>

<span data-ttu-id="60e62-121">[Hierarchy]\(ヒエラルキー\) ウィンドウで空の領域を右クリックし、 **[Create Empty]\(空のユーザーを作成\)** を選択してシーンに空のオブジェクトを追加し、オブジェクトに「**PhotonUser**」という名前を付けて、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="60e62-121">In the Hierarchy window, right-click on an empty area and select **Create Empty** to add an empty object to your scene, name the object **PhotonUser**, and configure it as follows:</span></span>

* <span data-ttu-id="60e62-122">[Transform]\(変換\) の **[Position]\(位置\)** が、X = 0、Y = 0、Z = 0 に設定されていることを確認する</span><span class="sxs-lookup"><span data-stu-id="60e62-122">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0:</span></span>

![新しく作成された PhotonUser オブジェクトが選択されている Unity](images/mr-learning-sharing/sharing-03-section2-step1-1.png)

<span data-ttu-id="60e62-124">[Hierarchy]\(階層\) ウィンドウで、**PhotonUser** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウの **[Add Component]\(コンポーネントの追加\)** ボタンを使用して **Photon User (Script)** コンポーネントを PhotonUser オブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="60e62-124">In the Hierarchy window, select the **PhotonUser** object, then in the Inspector window, use the **Add Component** button to add the **Photon User (Script)** component to the PhotonUser object:</span></span>

![Photon User コンポーネントが追加された Unity](images/mr-learning-sharing/sharing-03-section2-step1-2.png)

<span data-ttu-id="60e62-126">[Inspector]\(インスペクター\) ウィンドウで、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して PhotonUser オブジェクトに **Generic Net Sync (Script)** コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="60e62-126">In the Inspector window, use the **Add Component** button to add the **Generic Net Sync (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="60e62-127">**[Is User]\(ユーザーである\)** チェックボックスをオンにする</span><span class="sxs-lookup"><span data-stu-id="60e62-127">Check the **Is User** checkbox</span></span>

![Generic Net Sync コンポーネントが追加され構成された Unity](images/mr-learning-sharing/sharing-03-section2-step1-3.png)

<span data-ttu-id="60e62-129">[Inspector]\(インスペクター\) ウィンドウで、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して PhotonUser オブジェクトに **Photon View (Script)** コンポーネントを追加し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="60e62-129">In the Inspector window, use the **Add Component** button to add the **Photon View (Script)** component to the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="60e62-130">**[Observed Components]\(観察されるコンポーネント\)** フィールドに、**Generic Net Sync (Script)** コンポーネントを割り当てる</span><span class="sxs-lookup"><span data-stu-id="60e62-130">To the **Observed Components** field, assign the **Generic Net Sync (Script)** component</span></span>

![Photon View コンポーネントが追加され構成された Unity](images/mr-learning-sharing/sharing-03-section2-step1-4.png)

### <a name="2-create-the-avatar"></a><span data-ttu-id="60e62-132">2.アバターを作成する</span><span class="sxs-lookup"><span data-stu-id="60e62-132">2. Create the avatar</span></span>

<span data-ttu-id="60e62-133">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  > **MRTK** > **SDK** > **StandardAssets** >  **[Materials]\(素材\)** に移動し、MRTK の素材を見つけます。</span><span class="sxs-lookup"><span data-stu-id="60e62-133">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Materials** folder to locate the MRTK materials.</span></span>

<span data-ttu-id="60e62-134">次に、[Hierarchy]\(階層\) ウィンドウで、**PhotonUser** オブジェクトを右クリックして **[3D Object]\(3D オブジェクト\)**  >  **[Sphere]\(球体\)** を選択し、PhotonUser オブジェクトの子として球体オブジェクトを作成して次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="60e62-134">Then, in the Hierarchy window, right-click on the **PhotonUser** object and select **3D Object** > **Sphere** to create a sphere object as a child of the PhotonUser object and configure it as follows:</span></span>

* <span data-ttu-id="60e62-135">[Transform]\(変換\) の **[Position]\(位置\)** が、X = 0、Y = 0、Z = 0 に設定されていることを確認する</span><span class="sxs-lookup"><span data-stu-id="60e62-135">Ensure the Transform **Position** is set to X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="60e62-136">[Transform]\(変換\) の **[Scale]\(スケール\)** を適切なサイズに変更する。例: X = 0.15、Y = 0.15、Z = 0.15</span><span class="sxs-lookup"><span data-stu-id="60e62-136">Change the Transform **Scale** to a suitable size, for example, X = 0.15, Y = 0.15, Z = 0.15</span></span>
* <span data-ttu-id="60e62-137">[MeshRenderer] > [Materials]\(素材\) > **[Element 0]\(要素 0\)** フィールドに、**MRTK_Standard_White** 素材を割り当てる</span><span class="sxs-lookup"><span data-stu-id="60e62-137">To the MeshRenderer > Materials > **Element 0** field, assign the **MRTK_Standard_White** material</span></span>

![新しく作成され構成されたアバター球体が表示された Unity](images/mr-learning-sharing/sharing-03-section2-step2-1.png)

### <a name="3-create-the-prefab"></a><span data-ttu-id="60e62-139">3.プレハブを作成する</span><span class="sxs-lookup"><span data-stu-id="60e62-139">3. Create the prefab</span></span>

<span data-ttu-id="60e62-140">[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Resources]\(リソース\)** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="60e62-140">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder:</span></span>

![[Resources]\(リソース\) フォルダーが選択されているプロジェクト ウィンドウが表示された Unity](images/mr-learning-sharing/sharing-03-section2-step3-1.png)

<span data-ttu-id="60e62-142">[Resources]\(リソース\) フォルダーを選択したまま、[Hierarchy]\(ヒエラルキー\) ウィンドウから **PhotonUser** オブジェクトを **[Resources]\(リソース\)** フォルダーに **クリックしてドラッグ** し、PhotonUser オブジェクトをプレハブにします。</span><span class="sxs-lookup"><span data-stu-id="60e62-142">With the Resources folder still selected, **click-and-drag** the **PhotonUser** object from the Hierarchy window into the **Resources** folder to make the PhotonUser object a prefab:</span></span>

![新しく作成された PhotonUser プレハブが選択されている Unity](images/mr-learning-sharing/sharing-03-section2-step3-2.png)

<span data-ttu-id="60e62-144">[Hierarchy]\(ヒエラルキー\) ウィンドウで **PhotonUser** オブジェクトを右クリックし、 **[Delete]\(削除\)** を選択してシーンから削除します。</span><span class="sxs-lookup"><span data-stu-id="60e62-144">In the Hierarchy window, right-click on the **PhotonUser** object and select **Delete** to remove it from the scene:</span></span>

![新しく作成された PhotonUser プレハブ オブジェクトがシーンから削除されている Unity](images/mr-learning-sharing/sharing-03-section2-step3-3.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a><span data-ttu-id="60e62-146">PUN を構成してユーザー プレハブのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="60e62-146">Configuring PUN to instantiate the user prefab</span></span>

<span data-ttu-id="60e62-147">このセクションでは、前のセクションで作成した PhotonUser プレハブを使用するようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="60e62-147">In this section, you will configure the project to use the PhotonUser prefab you created in the previous section.</span></span>

<span data-ttu-id="60e62-148">[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Resources]\(リソース\)** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="60e62-148">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="60e62-149">[Hierarchy]\(ヒエラルキー\) ウィンドウで **NetworkLobby** オブジェクトを展開して **NetworkRoom** 子オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **Photon Room (Script)** コンポーネントを探し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="60e62-149">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="60e62-150">**"Photon User Prefab"(Photon ユーザー プレハブ)** フィールドに、[Resources]\(リソース\) フォルダーから **PhotonUser** プレハブを割り当てる</span><span class="sxs-lookup"><span data-stu-id="60e62-150">To the **Photon User Prefab** field, assign the **PhotonUser** prefab from the Resources folder</span></span>

![Photon Room コンポーネントが部分的に構成された Unity](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a><span data-ttu-id="60e62-152">複数のユーザーのエクスペリエンスを試す</span><span class="sxs-lookup"><span data-stu-id="60e62-152">Trying the experience with multiple users</span></span>

<span data-ttu-id="60e62-153">Unity プロジェクトをビルドして HoloLens に配置してから Unity に戻り、HoloLens でアプリが実行されている間にゲーム モードに入ると、頭 (HoloLens) を動かした時に HoloLens のユーザー アバターが動くのを確認できます。</span><span class="sxs-lookup"><span data-stu-id="60e62-153">If you now build and deploy the Unity project to your HoloLens, then, back in Unity, enter Game mode while the app is running on your HoloLens, you will see the HoloLens user avatar move when you move your head (HoloLens) around:</span></span>

![ネットワーク接続されたユーザーが表示された Unity を表示するアニメーション](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> <span data-ttu-id="60e62-155">HoloLens 2 に Unity プロジェクトをビルドして配置する方法を再確認するには、[HoloLens 2 にアプリをビルドする](mr-learning-base-02.md#building-and-deploying-to-your-hololens-2)手順に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60e62-155">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-and-deploying-to-your-hololens-2) instructions.</span></span>

> [!CAUTION]
> <span data-ttu-id="60e62-156">アプリから Photon に接続する必要があるため、お使いのコンピューターまたはデバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="60e62-156">The app needs to connect to Photon, so make sure your computer/device is connected to the internet.</span></span>

## <a name="congratulations"></a><span data-ttu-id="60e62-157">結論</span><span class="sxs-lookup"><span data-stu-id="60e62-157">Congratulations</span></span>

<span data-ttu-id="60e62-158">複数のユーザーが同じエクスペリエンスに接続して、互いの動きを確認できるようにプロジェクトを構成できました。</span><span class="sxs-lookup"><span data-stu-id="60e62-158">You have successfully configured your project to allow multiple users to connect to the same experience and see each other's movements.</span></span> <span data-ttu-id="60e62-159">次のチュートリアルでは、オブジェクトの動きが複数のデバイスで共有されるようにする機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="60e62-159">In the next tutorial, you will implement functionality so that the movements of objects are also shared across multiple devices.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="60e62-160">次のチュートリアル:4.オブジェクトの動きの複数のユーザーとの共有</span><span class="sxs-lookup"><span data-stu-id="60e62-160">Next Tutorial: 4. Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
