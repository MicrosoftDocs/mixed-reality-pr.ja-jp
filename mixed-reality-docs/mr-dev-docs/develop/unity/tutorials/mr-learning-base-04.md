---
title: 入門チュートリアル - 4. シーンへのオブジェクトの配置
description: このコースでは、Mixed Reality Toolkit (MRTK) を使用して複合現実のアプリケーションを作成する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 4254b15f4c15e491f81f99438389a6e3bf772868
ms.sourcegitcommit: d8f39c0b95d9e61d645d64f27baabc7a1c300dc1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92293226"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="73477-105">4.シーンへのオブジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="73477-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="73477-106">概要</span><span class="sxs-lookup"><span data-stu-id="73477-106">Overview</span></span>

<span data-ttu-id="73477-107">このチュートリアルでは、チュートリアルのアセットをインポートし、シーンに指定されたオブジェクトを配置します。</span><span class="sxs-lookup"><span data-stu-id="73477-107">In this tutorial, you will import the tutorial assets and position the provided objects in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="73477-108">目標</span><span class="sxs-lookup"><span data-stu-id="73477-108">Objectives</span></span>

* <span data-ttu-id="73477-109">シーンにオブジェクトを配置する方法について学ぶ</span><span class="sxs-lookup"><span data-stu-id="73477-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="73477-110">MRTK の Grid Object Collection 機能の使用方法について学ぶ</span><span class="sxs-lookup"><span data-stu-id="73477-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="73477-111">チュートリアルのアセットのインポート</span><span class="sxs-lookup"><span data-stu-id="73477-111">Importing the tutorial assets</span></span>

<span data-ttu-id="73477-112">次の Unity カスタム パッケージをダウンロードしてインポートします。</span><span class="sxs-lookup"><span data-stu-id="73477-112">Download and import the following Unity custom package:</span></span>

* [<span data-ttu-id="73477-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="73477-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

<span data-ttu-id="73477-114">チュートリアルのアセットをインポートすると、プロジェクト ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="73477-114">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="73477-116">Unity カスタム パッケージをインポートする方法については、[MRTK のインポート](mr-learning-base-02.md#importing-the-mixed-reality-toolkit)に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73477-116">For a reminder on how to import a Unity custom package, you can refer to the [Importing the MRTK](mr-learning-base-02.md#importing-the-mixed-reality-toolkit) instructions.</span></span>

## <a name="creating-the-parent-object"></a><span data-ttu-id="73477-117">親オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="73477-117">Creating the parent object</span></span>

<span data-ttu-id="73477-118">[Hierarchy]\(階層\) ウィンドウで空の領域を右クリックし、 **[Create Empty]\(空アイテムの作成\)** を選択してシーンに空のオブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="73477-118">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="73477-120">上の図のようにシーンとゲーム ウィンドウを並べて表示するには、ゲーム ウィンドウをシーン ウィンドウの右側にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="73477-120">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="73477-121">ワークスペースのカスタマイズの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">ワークスペースのカスタマイズ</a>に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="73477-121">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="73477-122">新規作成したオブジェクトを右クリックし、 **[Rename]\(名前の変更\)** を選択して、名前を **[RoverExplorer]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="73477-122">Right-click on the newly created object, select **Rename** , and change the name to **RoverExplorer** :</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-2.png)

<span data-ttu-id="73477-124">[RoverExplorer] オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで、次のように **[Transform]\(変換\)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="73477-124">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="73477-125">**位置** :X = 0、Y = -0.6、Z = 2</span><span class="sxs-lookup"><span data-stu-id="73477-125">**Position** : X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="73477-126">**回転** :X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="73477-126">**Rotation** : X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="73477-127">**スケール** :X = 1、Y = 1、Z = 1</span><span class="sxs-lookup"><span data-stu-id="73477-127">**Scale** : X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="73477-129">カメラはユーザーのヘッドを示し、X = 0、Y = 0、Z = 0 の基点に配置されています。</span><span class="sxs-lookup"><span data-stu-id="73477-129">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="73477-130">一般に、Unity の 1 単位は現実世界の約 1 m に相当します。</span><span class="sxs-lookup"><span data-stu-id="73477-130">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="73477-131">ただし、これには、あるオブジェクトがスケーリングされたオブジェクトの子である場合などの例外があります。</span><span class="sxs-lookup"><span data-stu-id="73477-131">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="73477-132">上のシナリオで RoverExplorer は、ユーザーのヘッドの 2 m 前、0.6 m 下に配置されています。</span><span class="sxs-lookup"><span data-stu-id="73477-132">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="73477-133">チュートリアル プレハブの追加</span><span class="sxs-lookup"><span data-stu-id="73477-133">Adding the tutorial prefabs</span></span>

<span data-ttu-id="73477-134">[Project]\(プロジェクト\) ウィンドウで **[Assets]\(アセット\)**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="73477-134">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="73477-136"><a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">プレハブ</a>は、Unity アセットとして格納されている事前構成済みの GameObject であり、プロジェクト全体で再利用できます。</span><span class="sxs-lookup"><span data-stu-id="73477-136">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="73477-137">[Project]\(プロジェクト\) ウィンドウで **[テーブル]** プレハブを **[RoverExplorer]** オブジェクトにクリックしてドラッグし、[RoverExplorer] オブジェクトの子にします。次いで [Inspector]\(インスペクター\) ウィンドウで、次のように **[Transform]\(変換\)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="73477-137">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="73477-138">**位置** :X = 0、Y = -0.005、Z = 0</span><span class="sxs-lookup"><span data-stu-id="73477-138">**Position** : X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="73477-139">**回転** :X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="73477-139">**Rotation** : X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="73477-140">**スケール** :X = 1.2、Y = 0.01、Z = 1.2</span><span class="sxs-lookup"><span data-stu-id="73477-140">**Scale** : X = 1.2, Y = 0.01, Z = 1.2</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="73477-142">次の図のようにシーンを表示するには、[Scene]\(シーン\) ウィンドウの右上隅にある <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">[Scene Gizmo]</a>\(シーン ギズモ\) を使用して、前の Z 軸に沿うように表示角度を調整します。[MixedRealityPlayspace] オブジェクトをダブルクリックし、カメラにフォーカスを当て、必要に応じて拡大します。</span><span class="sxs-lookup"><span data-stu-id="73477-142">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="73477-143">[Project]\(プロジェクト\) ウィンドウで **[RoverAssembly]** プレハブを **[RoverExplorer]** オブジェクトにクリックしてドラッグし、[RoverExplorer] オブジェクトの子にします。次いで [Inspector]\(インスペクター\) ウィンドウで、次のように **[Transform]\(変換\)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="73477-143">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="73477-144">**位置** :X = -0.1、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="73477-144">**Position** : X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="73477-145">**回転** :X = 0、Y = -135、Z = 0</span><span class="sxs-lookup"><span data-stu-id="73477-145">**Rotation** : X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="73477-146">**スケール** :X = 1、Y = 1、Z = 1</span><span class="sxs-lookup"><span data-stu-id="73477-146">**Scale** : X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="73477-148">コレクション内のオブジェクトの整理</span><span class="sxs-lookup"><span data-stu-id="73477-148">Organizing objects in a collection</span></span>

<span data-ttu-id="73477-149">[Hierarchy]\(階層\) ウィンドウで、 **[RoverExplorer]** オブジェクトを右クリックし、RoverExplorer の子として空のオブジェクトを追加するために **[Create Empty]\(空アイテムの作成\)** を選択します。そのオブジェクトには、 **[RoverParts]** と名前を付け、次のように **[Transform]\(変換\)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="73477-149">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts** , and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="73477-150">**位置** :X = 0、Y = 0.06、Z = 0</span><span class="sxs-lookup"><span data-stu-id="73477-150">**Position** : X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="73477-151">**回転** :X = 0、Y = 90、Z = 0</span><span class="sxs-lookup"><span data-stu-id="73477-151">**Rotation** : X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="73477-152">**スケール** :X = 1、Y = 1、Z = 1</span><span class="sxs-lookup"><span data-stu-id="73477-152">**Scale** : X = 1, Y = 1, Z = 1</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-1.png)

<span data-ttu-id="73477-154">[Hierarchy]\(階層\) ウィンドウで、[RoverExplorer]、[RoverAssembly]、[RoverModel]、 **[Parts]\(パーツ\)** の子オブジェクトをすべて選択し、それらを右クリックして、 **[Duplicate]\(重複\)** を選択し、各パーツのコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="73477-154">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="73477-156">隣接するオブジェクトを複数選択するには、SHIFT キーを押しながら、マウスを使用して最初と最後のオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="73477-156">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="73477-157">新しく複製した [Parts]\(パーツ\) 子オブジェクトを選択した状態で、それらをクリックして **[RoverParts]** オブジェクトにドラッグし、それらを RoverParts オブジェクトの子オブジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="73477-157">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-3.png)

<span data-ttu-id="73477-159">ご自分のシーンで簡単に操作するには、[階層] ウィンドウでオブジェクトの左側にある **目** のアイコンをクリックして、 **[RoverAssembly]** オブジェクトの **シーンの可視性** をオフに設定します。</span><span class="sxs-lookup"><span data-stu-id="73477-159">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverAssembly** object off.</span></span> <span data-ttu-id="73477-160">これにより、ゲーム内での可視性は変えずに、[Scene]\(シーン\) ウィンドウ内でオブジェクトを非表示にできます。</span><span class="sxs-lookup"><span data-stu-id="73477-160">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> <span data-ttu-id="73477-162">シーンの可視性の制御と、それらを使用したシーン ビューとワークフローの最適化方法の詳細については、Unity の<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">シーンの可視性</a>に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="73477-162">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="73477-163">[Hierarchy]\(階層\) ウィンドウで、RoverParts の子オブジェクトの名前に追加された **(1)** を **_Part** に置き換え、整理します。</span><span class="sxs-lookup"><span data-stu-id="73477-163">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part** :</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-5.png)

<span data-ttu-id="73477-165">[Hierarchy]\(階層\) ウィンドウで **[RoverParts]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **[Add Component]\(コンポーネントの追加\)** ボタンをクリックします。次に、 **[GridObjectCollection]** を検索して選択し、RoverParts オブジェクトに GridObjectCollection コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="73477-165">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-6.png)

<span data-ttu-id="73477-167">**GridObjectCollection** コンポーネントの値を次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="73477-167">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="73477-168">**並べ替えの種類** :アルファベット</span><span class="sxs-lookup"><span data-stu-id="73477-168">**Sort Type** : Alphabetic</span></span>
* <span data-ttu-id="73477-169">**レイアウト** :横方向</span><span class="sxs-lookup"><span data-stu-id="73477-169">**Layout** : Horizontal</span></span>
* <span data-ttu-id="73477-170">**セルの幅** :0.25</span><span class="sxs-lookup"><span data-stu-id="73477-170">**Cell Width** : 0.25</span></span>
* <span data-ttu-id="73477-171">**Distance from parent (親からの距離)** :0.38</span><span class="sxs-lookup"><span data-stu-id="73477-171">**Distance from parent** : 0.38</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-7.png)

<span data-ttu-id="73477-173">次に、 **[Update Collection]\(コレクションの更新\)** ボタンをクリックして、次のように RoverParts の子オブジェクトの位置を更新します。</span><span class="sxs-lookup"><span data-stu-id="73477-173">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![mr-learning-base](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="73477-175">結論</span><span class="sxs-lookup"><span data-stu-id="73477-175">Congratulations</span></span>

<span data-ttu-id="73477-176">このチュートリアルでは、シーン内のオブジェクトをユーザーに対して配置し、MRTK の Grid Object Collection 機能を使用してコレクション内のオブジェクトを整理する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="73477-176">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

[<span data-ttu-id="73477-177">次のチュートリアル:5.ソルバーを使用した動的なコンテンツの作成</span><span class="sxs-lookup"><span data-stu-id="73477-177">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)