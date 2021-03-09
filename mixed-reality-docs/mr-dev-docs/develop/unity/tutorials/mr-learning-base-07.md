---
title: 3D オブジェクトの操作
description: このコースでは、Mixed Reality ツールキット (MRTK) を使用して、Mixed Reality アプリで 3D オブジェクトと対話して操作する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality ツールキット, UWP, オブジェクトの操作, 境界コントロール
ms.localizationpriority: high
ms.openlocfilehash: 1ab7b3a334639be564717d77d3bbc478a25e8326
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102237243"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="d7365-104">7.3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="d7365-104">7. Interacting with 3D objects</span></span>

<span data-ttu-id="d7365-105">このチュートリアルでは、3D オブジェクトの近距離および遠距離操作を有効にし、許可される操作の種類を制限する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="d7365-105">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="d7365-106">また、オブジェクトの操作をより簡単に制御できるように、3D オブジェクトの周囲に境界コントロールを追加する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="d7365-106">You will also learn how to add bounds control around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="d7365-107">目標</span><span class="sxs-lookup"><span data-stu-id="d7365-107">Objectives</span></span>

* <span data-ttu-id="d7365-108">3D オブジェクトを操作できるように構成する方法について学習する</span><span class="sxs-lookup"><span data-stu-id="d7365-108">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="d7365-109">3D オブジェクトに境界コントロールを追加する方法について学習する</span><span class="sxs-lookup"><span data-stu-id="d7365-109">Learn how to add bounds control to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="d7365-110">3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="d7365-110">Manipulating 3D objects</span></span>

<span data-ttu-id="d7365-111">このセクションでは、「[シーン内のオブジェクトの配置](mr-learning-base-04.md)」チュートリアルで、テーブルで構成したすべての探査車 (Rover) のパーツを操作する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="d7365-111">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="d7365-112">これを実現するための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d7365-112">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="d7365-113">すべてのパーツ オブジェクトに Object Manipulator (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="d7365-113">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="d7365-114">すべてのパーツ オブジェクトに NearInteractionGrabbable コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="d7365-114">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="d7365-115">Object Manipulator (Script) コンポーネントを構成する</span><span class="sxs-lookup"><span data-stu-id="d7365-115">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="d7365-116">**オブジェクトを操作** できるようにするには、オブジェクトに次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="d7365-116">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="d7365-117">**Collider** コンポーネント、たとえばボックス コライダー</span><span class="sxs-lookup"><span data-stu-id="d7365-117">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="d7365-118">**Object Manipulator (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d7365-118">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="d7365-119">オブジェクトを **操作** し、**追跡対象の手でオブジェクトをつかむ** ことができるようにするには、オブジェクトに次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="d7365-119">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="d7365-120">**Collider** コンポーネント、たとえばボックス コライダー</span><span class="sxs-lookup"><span data-stu-id="d7365-120">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="d7365-121">**Object Manipulator (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d7365-121">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="d7365-122">**NearInteractionGrabbable** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d7365-122">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="d7365-123">さらに、探査車のパーツを Rover に配置して完全な探査車アセンブリにすることができるように、Rover Explorer を構成します。</span><span class="sxs-lookup"><span data-stu-id="d7365-123">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="d7365-124">[階層] ウィンドウで、RoverExplorer > **RoverParts** オブジェクトの順に展開し、そのすべての子の探査車のパーツ オブジェクトと **RoverAssembly** オブジェクトを選択します。その後、[インスペクター] ウィンドウで、 **[コンポーネントの追加]** ボタンを使用して、選択されたすべてのオブジェクトに次のコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7365-124">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="d7365-125">**Object Manipulator (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d7365-125">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="d7365-126">**NearInteractionGrabbable** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d7365-126">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="d7365-127">**Part Assembly Controller (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d7365-127">**Part Assembly Controller (Script)** component</span></span>

![RoverAssembly とすべての探査車パーツ オブジェクトが選択され、コンポーネントが追加されている Unity](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="d7365-129">互いに隣接していない複数のオブジェクトを選択するには、CTRL キーを押しながらマウスを使用して、任意のオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="d7365-129">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="d7365-130">Object Manipulator (Script) を追加すると、この場合、Object Manipulator (Script) は Constraint Manager (Script) に依存しているため、それが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="d7365-130">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="d7365-131">このチュートリアルでは、コライダーが既に探査車のパーツに追加されています。</span><span class="sxs-lookup"><span data-stu-id="d7365-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="d7365-132">コライダーの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">コライダー</a>に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7365-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="d7365-133">Part Assembly Controller (Script) は MRTK の一部ではありませんが、チュートリアル アセットには含まれていました。</span><span class="sxs-lookup"><span data-stu-id="d7365-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="d7365-134">すべての探査車のパーツ オブジェクトと RoverAssembly オブジェクトを引き続き選択した状態で、[インスペクター] ウィンドウで、次のように **Object Manipulator (Script)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="d7365-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="d7365-135">**[両手を使った操作の種類]** ドロップダウンで、[スケール] をオフにし、 **[移動]** と **[回転]** のみが有効になるようにします</span><span class="sxs-lookup"><span data-stu-id="d7365-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![[Two Handed Manipulation Type]\(両手を使った操作の種類\) が構成された Unity](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="d7365-137">この時点で、すべての探査車のパーツ オブジェクトと RoverAssembly オブジェクトのオブジェクト操作が有効になりました。</span><span class="sxs-lookup"><span data-stu-id="d7365-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="d7365-138">[プロジェクト] ウィンドウで、 **[パッケージ]**  >  **[Mixed Reality Toolkit Standard Assetss]**  >  **[Audio]** フォルダーに移動して、オーディオ クリップを見つけます。</span><span class="sxs-lookup"><span data-stu-id="d7365-138">In the Project window, navigate to **Packages** > **Mixed Reality Toolkit Standard Assets** > **Audio** folder to locate the audio clips:</span></span>

![[Audio] フォルダーが選択されているプロジェクト ウィンドウが表示された Unity](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="d7365-140">[階層] ウィンドウで、すべての **探査車のパーツ オブジェクト** をもう一度選択します。その後、[インスペクター] ウィンドウで、 **[コンポーネントの追加]** ボタンを使用し、**Audio Sources** コンポーネントを追加して、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="d7365-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="d7365-141">**MRTK_Scale_Start** オーディオ クリップを **AudioClip** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="d7365-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="d7365-142">**[Play On Awake]\(起動時に再生\)** チェックボックスをオフにします</span><span class="sxs-lookup"><span data-stu-id="d7365-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="d7365-143">**[Spatial Blend]\(空間ブレンド\)** を 1 に変更します</span><span class="sxs-lookup"><span data-stu-id="d7365-143">Change **Spatial Blend** to 1</span></span>

![すべての探査車パーツ オブジェクトが選択され、Audio Source コンポーネントが追加され構成されている Unity](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="d7365-145">[階層] ウィンドウで、RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** オブジェクトの順に展開し、すべての配置ヒント オブジェクトを表示します。その後、最初の探査車のパーツである、RoverParts > **Camera_Part** の順に選択し、**Part Assembly Controller (Script)** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="d7365-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="d7365-146">**Camera_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="d7365-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![Camera_Part PartAssemblyController コンポーネントが構成された Unity](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="d7365-148">残りの探査車のパーツ オブジェクトと RoverAssembly オブジェクトのそれぞれに対して、この手順を **繰り返し**、次のように **Part Assembly Controller (Script)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="d7365-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="d7365-149">**Generator_Part** については、**Generator_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="d7365-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="d7365-150">**Lights_Part** については、**Lights_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="d7365-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="d7365-151">**UHFAntenna_Part** については、**UHFAntenna_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="d7365-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="d7365-152">**Spectrometer_Part** については、**Spectrometer_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="d7365-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="d7365-153">**RoverAssembly** については、オブジェクト自体 (つまり、同じ **RoverAssembly** オブジェクト) を **[Location To Place]\(配置する場所\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="d7365-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="d7365-154">[階層] ウィンドウで、[RoverExplorer] > [ボタン] > **[リセット]** ボタン オブジェクトの順に選択します。その後、[インスペクター] ウィンドウで、次のように Interactable **OnClick ()** イベントを構成します。</span><span class="sxs-lookup"><span data-stu-id="d7365-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="d7365-155">**RoverAssembly** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="d7365-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d7365-156">**[No Function]\(関数なし\)** ドロップダウンから、**PartAssemblyController** > **ResetPlacement ()** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="d7365-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![[リセット] ボタン オブジェクトの OnClick イベントが構成された Unity](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="d7365-158">ゲーム モードになったら、近距離または遠距離操作を使用して、探査車のパーツを Rover に配置できます。</span><span class="sxs-lookup"><span data-stu-id="d7365-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="d7365-159">パーツは、対応する配置ヒントに近づくと、自動的に所定の位置にはめ込まれ、Rover の一部になります。</span><span class="sxs-lookup"><span data-stu-id="d7365-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="d7365-160">配置をリセットする場合は、[リセット] ボタンを押すことができます。</span><span class="sxs-lookup"><span data-stu-id="d7365-160">To reset the placements, you can press the Reset button:</span></span>

![[リセット] ボタンが押されている再生モードの分割ビューが表示された Unity](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="d7365-162">Object Manipulator コンポーネントとその関連プロパティの詳細については、[MRTK ドキュメント ポータル](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/)の「[オブジェクト マニピュレーター](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)」のガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7365-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).</span></span>

## <a name="adding-bounds-control"></a><span data-ttu-id="d7365-163">境界コントロールの追加</span><span class="sxs-lookup"><span data-stu-id="d7365-163">Adding Bounds Control</span></span>

<span data-ttu-id="d7365-164">境界コントロールを使用すると、拡大縮小および回転に使用できるハンドルが提供され、近距離と遠距離操作の両方のオブジェクト操作が片手で直感的にしやすくなります。</span><span class="sxs-lookup"><span data-stu-id="d7365-164">Bounds Control makes it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="d7365-165">この例では、BoundsControl を RoverExplorer オブジェクトに追加して、エクスペリエンス全体を簡単に移動、回転、および拡大縮小できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d7365-165">In this example, you will add a BoundsControl to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="d7365-166">また、境界コントロールのオンとオフを切り替えられるように、メニューを構成します。</span><span class="sxs-lookup"><span data-stu-id="d7365-166">Additionally, you will configure the Menu so you can turn the Bounds Control on and off.</span></span>

<span data-ttu-id="d7365-167">[階層] ウィンドウで、 **[RoverExplorer]** オブジェクトを選択します。その後、[インスペクター] ウィンドウで、 **[コンポーネントの追加]** ボタンを使用して、以下のコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="d7365-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="d7365-168">**BoundsControl** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d7365-168">**BoundsControl** component</span></span>
* <span data-ttu-id="d7365-169">**Object Manipulator (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d7365-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="d7365-170">その後、すべてのコンポーネントの横にあるチェックボックスを **オフ** にして、既定で **無効** になるようにします。</span><span class="sxs-lookup"><span data-stu-id="d7365-170">Then **uncheck** the checkbox next to all the components to make them **disabled** by default:</span></span>

![RoverExplorer オブジェクトが選択され、コンポーネントが追加され無効にされている Unity](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="d7365-172">境界コントロールの視覚エフェクトは実行時に作成されるため、ゲーム モードに入る前には表示されません。</span><span class="sxs-lookup"><span data-stu-id="d7365-172">The Bounds Control visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
><span data-ttu-id="d7365-173">Object Manipulator (Script) により、Constraint Manager (Script) が自動的に追加されます</span><span class="sxs-lookup"><span data-stu-id="d7365-173">The Object Manipulator (Script) automatically adds Constraint Manager (Script)</span></span>

<span data-ttu-id="d7365-174">[階層] ウィンドウで、[メニュー] > **[ButtonCollection]** オブジェクトの順に展開して 4 つのボタンを表示し、3 番目のボタンの名前を **BoundsControl_Enable** に変更します。その後、[インスペクター] ウィンドウで、**Button Config Helper (Script)** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="d7365-174">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundsControl_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="d7365-175">**[Main Label Text]\(メイン ラベル テキスト\)** を **[有効]** に変更します</span><span class="sxs-lookup"><span data-stu-id="d7365-175">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="d7365-176">**RoverExplorer** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="d7365-176">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d7365-177">**[No Function]\(関数なし\)** ドロップダウンから、 **[BoundsControl]**  >  **[bool Enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="d7365-177">From the **No Function** dropdown, select **BoundsControl** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="d7365-178">引数チェックボックスが **オン** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="d7365-178">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="d7365-179">小さい **[+]** アイコンをクリックして、別のイベントを追加します</span><span class="sxs-lookup"><span data-stu-id="d7365-179">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="d7365-180">**RoverExplorer** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="d7365-180">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d7365-181">**[No Function]\(関数なし\)** ドロップダウンから、 **[ObjectManipulator]**  >  **[bool Enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="d7365-181">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="d7365-182">引数チェックボックスが **オン** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="d7365-182">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="d7365-183">**[Icon]\(アイコン\)** は、"境界コントロールがあるキューブ" アイコンのままにしておきます</span><span class="sxs-lookup"><span data-stu-id="d7365-183">Leave the **Icon** as the 'cube with bounds control' icon</span></span>

![BoundsControl_Enable ボタン オブジェクトが選択され、Button Config Helper コンポーネントが構成された Unity](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="d7365-185">4 番目と最後のボタンの名前を **BoundsControl_Disable** に変更します。その後、[インスペクター] ウィンドウで、次のように **Button Config Helper (Script)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="d7365-185">Rename the forth and last button to **BoundsControl_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="d7365-186">**[Main Label Text]\(メイン ラベル テキスト\)** を **[無効]** に変更します</span><span class="sxs-lookup"><span data-stu-id="d7365-186">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="d7365-187">**RoverExplorer** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="d7365-187">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d7365-188">**[No Function]\(関数なし\)** ドロップダウンから、 **[BoundsControl]**  >  **[bool Enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="d7365-188">From the **No Function** dropdown, select **BoundsControl** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="d7365-189">引数チェックボックスが **オフ** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="d7365-189">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="d7365-190">小さい **[+]** アイコンをクリックして、別のイベントを追加します</span><span class="sxs-lookup"><span data-stu-id="d7365-190">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="d7365-191">**RoverExplorer** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="d7365-191">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="d7365-192">**[No Function]\(関数なし\)** ドロップダウンから、 **[ObjectManipulator]**  >  **[bool Enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="d7365-192">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="d7365-193">引数チェックボックスが **オフ** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="d7365-193">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="d7365-194">**[Icon]\(アイコン\)** を、"境界コントロールがあるキューブ" アイコンに変更します</span><span class="sxs-lookup"><span data-stu-id="d7365-194">Change the **Icon** to the 'cube with bounds control" icon</span></span>

![BoundsControl_Disable ボタン オブジェクトが選択され、Button Config Helper コンポーネントが構成された Unity](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="d7365-196">ゲーム モードに入り、[Enable]\(有効\) ボタンをクリックして境界コントロールを有効にしたら、近距離または遠距離操作を使用して、境界コントロールの移動、回転、および拡大縮小を行い、[Disable]\(無効\) ボタンを使用して、境界コントロールをもう一度無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="d7365-196">If you now enter Game mode and enable the Bounds Control by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounds Control, and use the Disable button to disable the Bounds Control again:</span></span>

![境界コントロールが操作されている Unity Play モードの分割ビュー](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="d7365-198">Bounds Control コンポーネントとその関連プロパティの詳細については、[MRTK ドキュメント ポータル](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/)の[境界コントロール](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html)に関するガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7365-198">To learn more about the Bounds Control component and its associated properties, you can visit the [Bounds Control](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-docs/).</span></span>

## <a name="congratulations"></a><span data-ttu-id="d7365-199">結論</span><span class="sxs-lookup"><span data-stu-id="d7365-199">Congratulations</span></span>

<span data-ttu-id="d7365-200">このチュートリアルでは、3D オブジェクトの近距離および遠距離操作を有効にする方法と、許可される操作の種類を制限する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="d7365-200">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="d7365-201">また、3D オブジェクトの周囲に境界コントロールを追加して、オブジェクトの操作をより簡単に制御できるようにする方法についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="d7365-201">You also learned how to add Bounds Control around 3D objects to make it easier to control the object manipulation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d7365-202">次のチュートリアル:8.視線追跡の使用</span><span class="sxs-lookup"><span data-stu-id="d7365-202">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
