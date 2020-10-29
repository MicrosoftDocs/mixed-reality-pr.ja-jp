---
title: マルチユーザー機能のチュートリアル - 4. 複数のユーザーとオブジェクトの移動を共有する
description: このコースでは、HoloLens 2 アプリケーション内でマルチユーザー共有エクスペリエンスを実装する方法について学習します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: b080522e25d933aeb979c3d9a851beaaac4da57f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91701686"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a><span data-ttu-id="99cf5-105">4.複数のユーザーとオブジェクトの移動を共有する</span><span class="sxs-lookup"><span data-stu-id="99cf5-105">4. Sharing object movements with multiple users</span></span>

<span data-ttu-id="99cf5-106">このチュートリアルでは、共有エクスペリエンスのすべての参加者が共同作業したり、相互の操作を表示したりできるように、オブジェクトの移動を共有する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="99cf5-106">In this tutorial, you will learn how to share the movements of objects so that all participants of a shared experience can collaborate and view each other's interactions.</span></span>

## <a name="objectives"></a><span data-ttu-id="99cf5-107">目標</span><span class="sxs-lookup"><span data-stu-id="99cf5-107">Objectives</span></span>

* <span data-ttu-id="99cf5-108">オブジェクトの移動を共有するようにプロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="99cf5-108">Configure your project to share the movements of objects</span></span>
* <span data-ttu-id="99cf5-109">基本的なマルチユーザー コラボレーション アプリを構築する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="99cf5-109">Learn how to build a basic multi-user collaborative app</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="99cf5-110">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="99cf5-110">Preparing the scene</span></span>

<span data-ttu-id="99cf5-111">このセクションでは、チュートリアルのプレハブを追加してシーンを準備します。</span><span class="sxs-lookup"><span data-stu-id="99cf5-111">In this section, you will prepare the scene by adding the tutorial prefab.</span></span>

<span data-ttu-id="99cf5-112">プロジェクト ウィンドウで **アセット** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs\(プレハブ\)** フォルダーの順に移動して、 **TableAnchor** プレハブを 階層 ウィンドウの **SharedPlayground** オブジェクト上にドラッグし、SharedPlayground オブジェクトの子としてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="99cf5-112">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Prefabs** folder and drag the **TableAnchor** prefab onto the **SharedPlayground** object in the Hierarchy window to add it to your scene as a child of the SharedPlayground object:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a><span data-ttu-id="99cf5-114">PUN を構成してオブジェクトのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="99cf5-114">Configuring PUN to instantiate the objects</span></span>

<span data-ttu-id="99cf5-115">このセクションでは、「[入門チュートリアル](mr-learning-base-01.md)」で作成した Rover Explorer エクスペリエンスを使用するようにプロジェクトを構成し、そのプロジェクトがインスタンス化される場所を定義します。</span><span class="sxs-lookup"><span data-stu-id="99cf5-115">In this section, you will configure the project to use the Rover Explorer experience created during the [Getting started tutorials](mr-learning-base-01.md) and define where it will be instantiated.</span></span>

<span data-ttu-id="99cf5-116">[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.MultiUserCapabilities]**  >  **[Resources]\(リソース\)** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="99cf5-116">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.MultiUserCapabilities** > **Resources** folder.</span></span>

<span data-ttu-id="99cf5-117">[Hierarchy]\(ヒエラルキー\) ウィンドウで **NetworkLobby** オブジェクトを展開して **NetworkRoom** 子オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **Photon Room (Script)** コンポーネントを探し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="99cf5-117">In the Hierarchy window, expand the **NetworkLobby** object and select the **NetworkRoom** child object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="99cf5-118">**Rover Explorer の [Prefab]\(プレハブ\)** フィールドに、[リソース] フォルダーから **RoverExplorer_Complete_Variant** プレハブを割り当てます</span><span class="sxs-lookup"><span data-stu-id="99cf5-118">To the **Rover Explorer Prefab** field, assign the **RoverExplorer_Complete_Variant** prefab from the Resources folder</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

<span data-ttu-id="99cf5-120">**NetworkRoom** 子オブジェクトを選択したまま [Hierarchy]\(ヒエラルキー\) ウィンドウで **TableAnchor** オブジェクトを展開し、[Inspector]\(インスペクター\) ウィンドウで **Photon Room (Script)** コンポーネントを探して次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="99cf5-120">With the **NetworkRoom** child object still selected, in the Hierarchy window, expand the **TableAnchor** object, then in the Inspector window, locate the **Photon Room (Script)** component and configure it as follows:</span></span>

* <span data-ttu-id="99cf5-121">**Rover Explorer の [場所]** フィールドに、[階層] ウィンドウから TableAnchor > **Table** 子オブジェクトを割り当てます</span><span class="sxs-lookup"><span data-stu-id="99cf5-121">To the **Rover Explorer Location** field, assign the TableAnchor > **Table** child object from the Hierarchy window</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a><span data-ttu-id="99cf5-123">共有オブジェクト移動のエクスペリエンスを試す</span><span class="sxs-lookup"><span data-stu-id="99cf5-123">Trying the experience with shared object movement</span></span>

<span data-ttu-id="99cf5-124">Unity プロジェクトをビルドして HoloLens にデプロイしてから Unity に戻り、HoloLens でアプリが実行されている間に [再生] ボタンを押してゲーム モードに入ると、HoloLens でオブジェクトを動かした時に Unity でオブジェクトが移動するのを確認できます。</span><span class="sxs-lookup"><span data-stu-id="99cf5-124">If you now build and deploy the Unity project to your HoloLens, and then, back in Unity, press the Play button to enter Game mode while the app is running on your HoloLens, you will see the object move in Unity when you move the object in HoloLens:</span></span>

![mr-learning-sharing](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a><span data-ttu-id="99cf5-126">結論</span><span class="sxs-lookup"><span data-stu-id="99cf5-126">Congratulations</span></span>

<span data-ttu-id="99cf5-127">他のユーザーがオブジェクトを移動したときにそのオブジェクトの移動をユーザーが確認できるように、プロジェクトでオブジェクトの移動が同期するように構成できました。</span><span class="sxs-lookup"><span data-stu-id="99cf5-127">You have successfully configured your project to synchronize object movements so users can see the objects move when other users move them.</span></span> <span data-ttu-id="99cf5-128">次のチュートリアルでは、現実の世界に合わせてエクスペリエンスを調整するための機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="99cf5-128">In the next tutorial, you will implement functionality to align the experience in the physical world.</span></span> <span data-ttu-id="99cf5-129">これにより、ユーザーどうしが実際の物理的な位置関係にいるように表示したり、オブジェクトがどのユーザーからも同じ物理的な位置と角度で表示されるようにしたりできます。</span><span class="sxs-lookup"><span data-stu-id="99cf5-129">This will ensure the users see each other in their actual physical location, and so the objects appear in the same physical position and rotation for all users.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="99cf5-130">次のチュートリアル:5.Azure Spatial Anchors の共有エクスペリエンスへの統合</span><span class="sxs-lookup"><span data-stu-id="99cf5-130">Next Tutorial: 5. Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)
