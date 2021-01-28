---
title: Azure Spatial Anchors をお使いになる前に
description: このコースを完了すると、Azure Spatial Anchors を使用して Mixed Reality アプリケーション内でオブジェクトを固定する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー
ms.localizationpriority: high
ms.openlocfilehash: 60d4ae99629f0caf7e5cc7e73b05ed35ee3f4ac4
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699219"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a><span data-ttu-id="fb3a9-104">2.Azure Spatial Anchors をお使いになる前に</span><span class="sxs-lookup"><span data-stu-id="fb3a9-104">2. Getting started with Azure Spatial Anchors</span></span>

<span data-ttu-id="fb3a9-105">このチュートリアルでは、Azure Spatial Anchors セッションの開始と停止、および単一のデバイス上での Azure Spatial Anchors の作成、アップロード、ダウンロードに必要なさまざまな手順を学習します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-105">In this tutorial, you will explore the various steps required to start and stop an Azure Spatial Anchors session and to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

## <a name="objectives"></a><span data-ttu-id="fb3a9-106">目標</span><span class="sxs-lookup"><span data-stu-id="fb3a9-106">Objectives</span></span>

* <span data-ttu-id="fb3a9-107">HoloLens 2 用の Azure Spatial Anchors を使用した開発の基礎について学習する</span><span class="sxs-lookup"><span data-stu-id="fb3a9-107">Learn the fundamentals of developing with Azure Spatial Anchors for HoloLens 2</span></span>
* <span data-ttu-id="fb3a9-108">Spatial Anchors を作成し、それらを Azure からフェッチする方法を学習する</span><span class="sxs-lookup"><span data-stu-id="fb3a9-108">Learn how to create spatial anchors and fetch them from Azure</span></span>

## <a name="creating-and-preparing-the-unity-project"></a><span data-ttu-id="fb3a9-109">Unity プロジェクトの作成と準備</span><span class="sxs-lookup"><span data-stu-id="fb3a9-109">Creating and preparing the Unity project</span></span>

<span data-ttu-id="fb3a9-110">このセクションでは、新しい Unity プロジェクトを作成し、MRTK 開発用に準備します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-110">In this section, you will create a new Unity project and get it ready for MRTK development.</span></span>

<span data-ttu-id="fb3a9-111">最初に、「[プロジェクトの初期化と最初のアプリケーションの配置](mr-learning-base-02.md)」に従います (「[デバイスへのアプリケーションのビルド](mr-learning-base-02.md#building-your-application-to-your-hololens-2)」の手順は除く)。これには、次の手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-111">First, follow the [Initializing your project and deploying your first application](mr-learning-base-02.md), excluding the [Build your application to your device](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions, which includes the following steps:</span></span>

1. <span data-ttu-id="fb3a9-112">[Unity プロジェクトを作成](mr-learning-base-02.md#creating-the-unity-project)し、"*MRTK チュートリアル*" などの適切な名前を付ける</span><span class="sxs-lookup"><span data-stu-id="fb3a9-112">[Creating the Unity project](mr-learning-base-02.md#creating-the-unity-project) and give it a suitable name, for example, *MRTK Tutorials*</span></span>
2. [<span data-ttu-id="fb3a9-113">ビルド プラットフォームを切り替える</span><span class="sxs-lookup"><span data-stu-id="fb3a9-113">Switching the build platform</span></span>](mr-learning-base-02.md#switching-the-build-platform)
3. [<span data-ttu-id="fb3a9-114">TextMeshPro の重要なリソースをインポートする</span><span class="sxs-lookup"><span data-stu-id="fb3a9-114">Importing the TextMeshPro Essential Resources</span></span>](mr-learning-base-02.md#importing-the-textmeshpro-essential-resources)
4. [<span data-ttu-id="fb3a9-115">Mixed Reality Toolkit をインポートする</span><span class="sxs-lookup"><span data-stu-id="fb3a9-115">Importing the Mixed Reality Toolkit</span></span>](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)
5. [<span data-ttu-id="fb3a9-116">Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="fb3a9-116">Configuring the Unity project</span></span>](mr-learning-base-02.md#configuring-the-unity-project)
6. <span data-ttu-id="fb3a9-117">[シーンを作成して構成](mr-learning-base-02.md#creating-and-configuring-the-scene)し、シーンに *AzureSpatialAnchors* などの適切な名前を付ける</span><span class="sxs-lookup"><span data-stu-id="fb3a9-117">[Creating and configuring the scene](mr-learning-base-02.md#creating-and-configuring-the-scene) and give the scene a suitable name, for example, *AzureSpatialAnchors*</span></span>

<span data-ttu-id="fb3a9-118">次に、「[空間認識表示オプションの変更](mr-learning-base-03.md#changing-the-spatial-awareness-display-option)」の指示に従い、次の作業を行います。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-118">Then follow the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions to:</span></span>

1. <span data-ttu-id="fb3a9-119">**MRTK 構成プロファイル** を **DefaultHoloLens2ConfigurationProfile** に変更します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-119">Change the **MRTK configuration profile** for to the **DefaultHoloLens2ConfigurationProfile**</span></span>
1. <span data-ttu-id="fb3a9-120">**空間認識メッシュ表示オプション** を **[Occlusion]\(オクルージョン\)** に変更します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-120">Change the **spatial awareness mesh display options** to **Occlusion**.</span></span>

## <a name="installing-inbuilt-unity-packages"></a><span data-ttu-id="fb3a9-121">組み込みの Unity パッケージのインストール</span><span class="sxs-lookup"><span data-stu-id="fb3a9-121">Installing inbuilt Unity packages</span></span>

<span data-ttu-id="fb3a9-122">Unity メニューで、 **[Window]\(ウィンドウ\)**  >  **[Package Manager]\(パッケージ マネージャー\)** の順に選択して、[Package Manager]\(パッケージ マネージャー\) ウィンドウを開きます。次に、 **[AR Foundation]** を選択し、 **[Install]\(インストール\)** ボタンをクリックしてパッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-122">In the Unity menu, select **Window** > **Package Manager** to open the Package Manager window, then select **AR Foundation** and click the **Install** button to install the package:</span></span>

![AR Foundation が選択されている [Package Manager]\(パッケージ マネージャー\) が表示された Unity](images/mr-learning-asa/asa-02-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="fb3a9-124">Azure Spatial Anchors SDK で必要になるため、AR Foundation パッケージをインストールします。これは、次のセクションでインポートします。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-124">You are installing the AR Foundation package because the Azure Spatial Anchors SDK requires it, which you will import in the next section.</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="fb3a9-125">チュートリアルのアセットのインポート</span><span class="sxs-lookup"><span data-stu-id="fb3a9-125">Importing the tutorial assets</span></span>

<span data-ttu-id="fb3a9-126">AzurespatialAnchors SDK V2.7.1 を Unity プロジェクトに追加します。パッケージを追加するには、こちらの[チュートリアル](https://docs.microsoft.com/en-us/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)に従ってください</span><span class="sxs-lookup"><span data-stu-id="fb3a9-126">Add AzurespatialAnchors SDK V2.7.1 into your unity project, to add the packages please follow this [tutorial](https://docs.microsoft.com/en-us/azure/spatial-anchors/how-tos/setup-unity-project?tabs=UPMPackage)</span></span>

<span data-ttu-id="fb3a9-127">次の Unity カスタム パッケージを、**記載されている順で** ダウンロードして **インポート** します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-127">Download and **import** the following Unity custom packages **in the order they are listed**:</span></span>


* [<span data-ttu-id="fb3a9-128">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="fb3a9-128">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)
* [<span data-ttu-id="fb3a9-129">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="fb3a9-129">MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-spatial-anchors-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.AzureSpatialAnchors.2.4.0.unitypackage)

<span data-ttu-id="fb3a9-130">チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-130">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![チュートリアルのアセットがインポートされた後の Unity の [Hierarchy]\(階層\)、[Scene]\(シーン\)、[Project]\(プロジェクト\) ウィンドウ](images/mr-learning-asa/asa-02-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="fb3a9-132">"WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)" が廃止されていることに関する CS0618 警告が表示されても、無視してかまいません。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-132">If you see any CS0618 warnings regarding 'WorldAnchor.SetNativeSpatialAnchorPtr(IntPtr)' is obsolete, you can ignore these warnings.</span></span>

> [!TIP]
> <span data-ttu-id="fb3a9-133">Unity カスタム パッケージをインポートする方法については、「[Mixed Reality Toolkit をインポートする](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)」の手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-133">For a reminder on how to import a Unity custom package, you can refer to the [Importing the Mixed Reality Toolkit](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="fb3a9-134">シーンの準備</span><span class="sxs-lookup"><span data-stu-id="fb3a9-134">Preparing the scene</span></span>

<span data-ttu-id="fb3a9-135">このセクションでは、チュートリアルのプレハブをいくつか追加してシーンを準備します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-135">In this section, you will prepare the scene by adding some of the tutorial prefabs.</span></span>

<span data-ttu-id="fb3a9-136">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.AzureSpatialAnchors]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動し、次のプレハブを [Hierarchy]\(階層\) ウィンドウにドラッグしてシーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-136">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureSpatialAnchors** > **Prefabs** folder, then click-and-drag the following prefabs into the Hierarchy window to add them to your scene:</span></span>

* <span data-ttu-id="fb3a9-137">**ButtonParent** プレハブ</span><span class="sxs-lookup"><span data-stu-id="fb3a9-137">**ButtonParent** prefabs</span></span>
* <span data-ttu-id="fb3a9-138">**DebugWindow** プレハブ</span><span class="sxs-lookup"><span data-stu-id="fb3a9-138">**DebugWindow** prefabs</span></span>
* <span data-ttu-id="fb3a9-139">**Instructions** プレハブ</span><span class="sxs-lookup"><span data-stu-id="fb3a9-139">**Instructions** prefabs</span></span>
* <span data-ttu-id="fb3a9-140">**ParentAnchor** プレハブ</span><span class="sxs-lookup"><span data-stu-id="fb3a9-140">**ParentAnchor** prefabs</span></span>

![新しく追加されたプレハブが選択されている Unity](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> <span data-ttu-id="fb3a9-142">シーンに大きいアイコンが表示されている場合 (たとえば、大きいフレームの 'T' アイコンが邪魔になる場合など)、上の画像で示すように、<a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">ギズモをオフに切り替える</a>ことによってこれらを非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-142">If you find the large icons in your scene, for example, the large framed 'T' icons distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span>

## <a name="configuring-the-buttons-to-operate-the-scene"></a><span data-ttu-id="fb3a9-143">シーンを操作するためのボタンの構成</span><span class="sxs-lookup"><span data-stu-id="fb3a9-143">Configuring the buttons to operate the scene</span></span>

<span data-ttu-id="fb3a9-144">このセクションでは、スクリプトをシーンに追加して、アプリでのローカル アンカーと Azure Spatial Anchors の両方の基本的な動作を示す一連のボタン イベントを作成します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-144">In this section, you will add scripts to the scene to create a series of button events that demonstrate the fundamentals of how both local anchors and Azure Spatial Anchors behave in an app.</span></span>

<span data-ttu-id="fb3a9-145">[Hierarchy]\(階層\) ウィンドウで、 **[ButtonParent]** オブジェクトを展開し、**StartAzureSession** という名前の最初の子オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-145">In the Hierarchy window, expand the **ButtonParent** object and select the first child object named **StartAzureSession**, in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="fb3a9-146">**ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="fb3a9-146">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="fb3a9-147">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[StartAzureSession ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-147">From the **No Function** dropdown, select **AnchorModuleScript** > **StartAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![StartAzureSession ボタンの OnClick イベントが構成された Unity](images/mr-learning-asa/asa-02-section5-step1-1.png)

<span data-ttu-id="fb3a9-149">[Hierarchy]\(階層\) ウィンドウで、次の **StopAzureSession** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-149">In the Hierarchy window, select the next button named **StopAzureSession**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="fb3a9-150">**ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="fb3a9-150">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="fb3a9-151">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[StopAzureSession ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-151">From the **No Function** dropdown, select **AnchorModuleScript** > **StopAzureSession ()** to set this function as the action to be executed when the event is triggered</span></span>

![StopAzureSession ボタンの OnClick イベントが構成された Unity](images/mr-learning-asa/asa-02-section5-step1-2.png)

<span data-ttu-id="fb3a9-153">[Hierarchy]\(階層\) ウィンドウで、次の **CreateAzureAnchor** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-153">In the Hierarchy window, select the next button named **CreateAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="fb3a9-154">**ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="fb3a9-154">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="fb3a9-155">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[CreateAzureAnchor ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-155">From the **No Function** dropdown, select **AnchorModuleScript** > **CreateAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="fb3a9-156">**[ParentAnchor]** オブジェクトを空の **[None (Game Object)]\(なし (ゲーム オブジェクト)\)** フィールドに割り当てて、CreateAzureAnchor () 関数の引数にします</span><span class="sxs-lookup"><span data-stu-id="fb3a9-156">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the CreateAzureAnchor () function</span></span>

![CreateAzureAnchor ボタンの OnClick イベントが構成された Unity](images/mr-learning-asa/asa-02-section5-step1-3.png)

<span data-ttu-id="fb3a9-158">[Hierarchy]\(階層\) ウィンドウで、次の **RemoveLocalAnchor** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-158">In the Hierarchy window, select the next button named **RemoveLocalAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="fb3a9-159">**ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="fb3a9-159">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="fb3a9-160">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[RemoveLocalAnchor ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-160">From the **No Function** dropdown, select **AnchorModuleScript** > **RemoveLocalAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="fb3a9-161">**[ParentAnchor]** オブジェクトを空の **[None (Game Object)]\(なし (ゲーム オブジェクト)\)** フィールドに割り当てて、RemoveLocalAnchor () 関数の引数にします</span><span class="sxs-lookup"><span data-stu-id="fb3a9-161">Assign the **ParentAnchor** object to the empty **None (Game Object)** field to make it the argument for the RemoveLocalAnchor () function</span></span>

![RemoveLocalAnchor ボタンの OnClick イベントが構成された Unity](images/mr-learning-asa/asa-02-section5-step1-4.png)

<span data-ttu-id="fb3a9-163">[Hierarchy]\(階層\) ウィンドウで、次の **FindAzureAnchor** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-163">In the Hierarchy window, select the next button named **FindAzureAnchor**,then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="fb3a9-164">**ParentAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="fb3a9-164">Assign the **ParentAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="fb3a9-165">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[FindAzureAnchor ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-165">From the **No Function** dropdown, select **AnchorModuleScript** > **FindAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![FindAzureAnchor ボタンの OnClick イベントが構成された Unity](images/mr-learning-asa/asa-02-section5-step1-5.png)

<span data-ttu-id="fb3a9-167">[Hierarchy]\(階層\) ウィンドウで、次の **DeleteAzureAnchor** という名前のボタンを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Button Config Helper (Script)** コンポーネントの **On Click ()** イベントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-167">In the Hierarchy window, select the next button named **DeleteAzureAnchor**, then in the Inspector window, configure the **Button Config Helper (Script)** component's **On Click ()** event as follows:</span></span>

* <span data-ttu-id="fb3a9-168">**DeleteAzureAnchor** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="fb3a9-168">Assign the **DeleteAzureAnchor** object to the **None (Object)** field</span></span>
* <span data-ttu-id="fb3a9-169">**[No Function]\(関数なし\)** ドロップダウンから、 **[AnchorModuleScript]**  >  **[DeleteAzureAnchor ()]** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-169">From the **No Function** dropdown, select **AnchorModuleScript** > **DeleteAzureAnchor ()** to set this function as the action to be executed when the event is triggered</span></span>

![DeleteAzureAnchor ボタンの OnClick イベントが構成された Unity](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a><span data-ttu-id="fb3a9-171">シーンを Azure リソースに接続する</span><span class="sxs-lookup"><span data-stu-id="fb3a9-171">Connecting the scene to the Azure resource</span></span>

<span data-ttu-id="fb3a9-172">[Hierarchy]\(階層\) ウィンドウで **[ParentAnchor]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Spatial Anchor Manager (Script)** コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-172">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, locate the **Spatial Anchor Manager (Script)** component.</span></span> <span data-ttu-id="fb3a9-173">このチュートリアル シリーズの「[前提条件](mr-learning-asa-01.md#prerequisites)」の一環として作成した Azure Spatial Anchors アカウントの資格情報を使用して、 **[Credentials]\(資格情報\)** セクションを構成します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-173">Configure the **Credentials** section with the credentials from the Azure Spatial Anchors account created as part of the [Prerequisites](mr-learning-asa-01.md#prerequisites) for this tutorial series:</span></span>

* <span data-ttu-id="fb3a9-174">**"Spatial Anchors Account ID"(Spatial Anchors アカウント ID)** フィールドに、Azure Spatial Anchors アカウントからの **アカウント ID** を貼り付ける</span><span class="sxs-lookup"><span data-stu-id="fb3a9-174">In the **Spatial Anchors Account ID** field, paste the **Account ID** from your Azure Spatial Anchors account</span></span>
* <span data-ttu-id="fb3a9-175">**"Spatial Anchors Account Key"(Spatial Anchors アカウント キー)** フィールドに、Azure Spatial Anchors アカウントからのプライマリまたはセカンダリ **アクセス キー** を貼り付ける</span><span class="sxs-lookup"><span data-stu-id="fb3a9-175">In the **Spatial Anchors Account Key** field, paste the primary or secondary **Access Key** from your Azure Spatial Anchors account</span></span>

![Spatial Anchor Manager が構成された Unity](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a><span data-ttu-id="fb3a9-177">Azure Spatial Anchors の基本的な動作を試す</span><span class="sxs-lookup"><span data-stu-id="fb3a9-177">Trying the basic behaviors of Azure Spatial Anchors</span></span>

<span data-ttu-id="fb3a9-178">Azure Spatial Anchors は Unity では実行できないため、Azure Spatial Anchors の機能をテストするには、ご利用のデバイスにプロジェクトをビルドし、アプリをデプロイする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-178">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to build the project and deploy the app to your device.</span></span>

> [!TIP]
> <span data-ttu-id="fb3a9-179">HoloLens 2 に Unity プロジェクトをビルドしてデプロイする方法については、[HoloLens 2 用のアプリケーションの構築](mr-learning-base-02.md#building-your-application-to-your-hololens-2)の手順に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-179">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2]((mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

<span data-ttu-id="fb3a9-180">ご利用のデバイスでアプリケーションが実行されているときに、Azure Spatial Anchor チュートリアルの手順パネルに表示される画面の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-180">When the app runs on your device, follow the on-screen instructions displayed on the Azure Spatial Anchor Tutorial Instructions panel:</span></span>

1. <span data-ttu-id="fb3a9-181">キューブを別の場所に移動します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-181">Move the cube to a different location</span></span>
1. <span data-ttu-id="fb3a9-182">Azure セッションを開始します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-182">Start Azure Session</span></span>
1. <span data-ttu-id="fb3a9-183">Azure Anchor を作成します (キューブの場所に Anchor を作成します)。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-183">Create Azure Anchor (creates an anchor at the location of the cube).</span></span>
1. <span data-ttu-id="fb3a9-184">Azure セッションを停止します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-184">Stop Azure Session</span></span>
1. <span data-ttu-id="fb3a9-185">ローカル アンカーを削除します (これにより、ユーザーはキューブを移動できます)</span><span class="sxs-lookup"><span data-stu-id="fb3a9-185">Remove Local Anchor (allows the user to move the cube)</span></span>
1. <span data-ttu-id="fb3a9-186">キューブを別の場所に移動します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-186">Move the cube somewhere else</span></span>
1. <span data-ttu-id="fb3a9-187">Azure セッションを開始します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-187">Start Azure Session</span></span>
1. <span data-ttu-id="fb3a9-188">Azure Anchor を見つけます (手順 3 の場所にキューブを配置します)</span><span class="sxs-lookup"><span data-stu-id="fb3a9-188">Find Azure Anchor (positions the cube at the location from step 3)</span></span>
1. <span data-ttu-id="fb3a9-189">Azure Anchor を削除します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-189">Delete Azure Anchor</span></span>
1. <span data-ttu-id="fb3a9-190">Azure セッションを停止します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-190">Stop Azure session</span></span>

![Instructions オブジェクトが選択されている Unity](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> <span data-ttu-id="fb3a9-192">Azure Spatial Anchors では、インターネットを使用してアンカー データの保存と読み込みを行うため、ご利用のデバイスがインターネットに接続されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-192">Azure Spatial Anchors uses the internet to save and load the anchor data, so make sure your device is connected to the internet.</span></span>

## <a name="anchoring-an-experience"></a><span data-ttu-id="fb3a9-193">エクスペリエンスの固定</span><span class="sxs-lookup"><span data-stu-id="fb3a9-193">Anchoring an experience</span></span>

<span data-ttu-id="fb3a9-194">前のセクションでは、Azure Spatial Anchors の基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-194">In the previous sections, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="fb3a9-195">キューブを使用して、アンカーがアタッチされた親のゲーム オブジェクトを表現および視覚化しました。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-195">We used a cube to represent and visualize the parent game object with the attached anchor.</span></span> <span data-ttu-id="fb3a9-196">このセクションでは、エクスペリエンス全体を、ParentAnchor オブジェクトの子として配置して固定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-196">In this section, you will learn how to anchor an entire experience by placing it as a child of the ParentAnchor object.</span></span>

<span data-ttu-id="fb3a9-197">[Hierarchy]\(階層\) ウィンドウで、**ParentAnchor** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、**Transform** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-197">In the Hierarchy window, select the **ParentAnchor** object, then in the Inspector window, configure the **Transform** components as follows:</span></span>

* <span data-ttu-id="fb3a9-198">**[Scale X]\(X 拡大縮小\)** を 1.1 に変更します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-198">Change **Scale X** to 1.1</span></span>
* <span data-ttu-id="fb3a9-199">**[Scale Z]\(Z 拡大縮小\)** を 1.1 に変更します</span><span class="sxs-lookup"><span data-stu-id="fb3a9-199">Change **Scale Z** to 1.1</span></span>

![ParentAnchor オブジェクトが選択され、配置され、スケーリングされている Unity](images/mr-learning-asa/asa-02-section8-step1-1.png)

<span data-ttu-id="fb3a9-201">[Project]\(プロジェクト\) ウィンドウで、 **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)**  >  **[Rover]** フォルダーの順に移動し、**RoverExplorer_Complete** プレハブをクリックして [Hierarchy]\(階層\) ウィンドウにドラッグし、シーンに追加します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-201">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** > **Rover** folder, then click-and-drag the **RoverExplorer_Complete** prefab into the Hierarchy window to add it to the scene:</span></span>

![新しく追加された RoverExplorer_Complete プレハブが選択されている Unity](images/mr-learning-asa/asa-02-section8-step1-2.png)

<span data-ttu-id="fb3a9-203">新しく追加した RoverModule_Complete オブジェクトが [Hierarchy]\(階層\) ウィンドウで選択されたままの状態で、それを **ParentAnchor** オブジェクトにドラッグして、ParentAnchor オブジェクトの子にします。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-203">With the newly added RoverModule_Complete object still selected in the Hierarchy window, drag it onto the **ParentAnchor** object to make it a child of the ParentAnchor object:</span></span>

![RoverExplorer_Complete オブジェクトが ParentAnchor の子として設定されている Unity](images/mr-learning-asa/asa-02-section8-step1-3.png)

<span data-ttu-id="fb3a9-205">ここでプロジェクトを再ビルドして、アプリをご利用のデバイスにデプロイすると、サイズ変更したキューブを移動して、Rover エクスプローラー エクスペリエンス全体を再配置できます。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-205">If you now rebuild the project and deploy the app to your device, you can now reposition the entire Rover Explorer experience by moving the resized cube.</span></span>

> [!TIP]
> <span data-ttu-id="fb3a9-206">エクスペリエンスの再配置には、再配置オブジェクト (このチュートリアルで使用するキューブなど) の使用、エクスペリエンスを囲む境界コントロールを切り替えるボタンの使用、位置と回転のギズモの使用など、さまざまなユーザー エクスペリエンス フローがあります。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-206">A variety of user experience flows for repositioning experiences, including the use of a repositioning object (such as the cube used in this tutorial), the use of a button to toggle a bounds control that surrounds the experience, the use of position and rotation gizmos, and more.</span></span>

## <a name="congratulations"></a><span data-ttu-id="fb3a9-207">結論</span><span class="sxs-lookup"><span data-stu-id="fb3a9-207">Congratulations</span></span>

<span data-ttu-id="fb3a9-208">このチュートリアルでは、Azure Spatial Anchors の基礎について学習しました。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-208">In this tutorial, you learned the fundamentals of Azure Spatial Anchors.</span></span> <span data-ttu-id="fb3a9-209">このチュートリアルでは、Azure Spatial Anchors セッションの開始と停止を行うため、および単一のデバイスで Azure Spatial Anchors の作成、アップロード、ダウンロードを行うために</span><span class="sxs-lookup"><span data-stu-id="fb3a9-209">This tutorial provided you with several buttons to let you explore the various steps required to start and stop an Azure Spatial Anchors session.</span></span> <span data-ttu-id="fb3a9-210">必要なさまざまな手順を調べることができるいくつかのボタンについて説明しました。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-210">Also, to create, upload, and download Azure Spatial Anchors on a single device.</span></span>

<span data-ttu-id="fb3a9-211">次のチュートリアルでは、アプリを再起動した後でも取得できるように、Azure アンカー ID を HoloLens 2 に保存する方法と、アンカー ID を複数のデバイス間で転送して空間的な位置合わせを行う方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="fb3a9-211">In the next tutorial, you will learn how to save Azure anchor IDs to your HoloLens 2 for retrieval, even after the app is restarted, and how to transfer anchor IDs between multiple devices to achieve spatial alignment.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fb3a9-212">次のチュートリアル:3.Azure Spatial Anchors の保存、取得、および共有</span><span class="sxs-lookup"><span data-stu-id="fb3a9-212">Next Tutorial: 3. Saving, retrieving and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
