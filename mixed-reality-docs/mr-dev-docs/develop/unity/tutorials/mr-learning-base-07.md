---
title: 3D オブジェクトの操作
description: このコースでは、Mixed Reality ツールキット (MRTK) を使用して、Mixed Reality アプリで 3D オブジェクトと対話して操作する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, オブジェクトの相互作用, 境界ボックス
ms.localizationpriority: high
ms.openlocfilehash: c9acb72b2ad961737f5ce3f21c048fc80024b49d
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007932"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="f37ba-104">7.3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="f37ba-104">7. Interacting with 3D objects</span></span>

<span data-ttu-id="f37ba-105">このチュートリアルでは、3D オブジェクトの近距離および遠距離操作を有効にし、許可される操作の種類を制限する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-105">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="f37ba-106">また、オブジェクトの操作をより簡単に制御できるように、3D オブジェクトの周囲に境界ボックスを追加する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-106">You will also learn how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="f37ba-107">目標</span><span class="sxs-lookup"><span data-stu-id="f37ba-107">Objectives</span></span>

* <span data-ttu-id="f37ba-108">3D オブジェクトを操作できるように構成する方法について学習する</span><span class="sxs-lookup"><span data-stu-id="f37ba-108">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="f37ba-109">3D オブジェクトに境界ボックスを追加する方法について学習する</span><span class="sxs-lookup"><span data-stu-id="f37ba-109">Learn how to add bounding boxes to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="f37ba-110">3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="f37ba-110">Manipulating 3D objects</span></span>

<span data-ttu-id="f37ba-111">このセクションでは、「[シーン内のオブジェクトの配置](mr-learning-base-04.md)」チュートリアルで、テーブルで構成したすべての探査車 (Rover) のパーツを操作する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-111">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="f37ba-112">これを実現するための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f37ba-112">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="f37ba-113">すべてのパーツ オブジェクトに Object Manipulator (Script) コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="f37ba-113">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="f37ba-114">すべてのパーツ オブジェクトに NearInteractionGrabbable コンポーネントを追加する</span><span class="sxs-lookup"><span data-stu-id="f37ba-114">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="f37ba-115">Object Manipulator (Script) コンポーネントを構成する</span><span class="sxs-lookup"><span data-stu-id="f37ba-115">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="f37ba-116">**オブジェクトを操作** できるようにするには、オブジェクトに次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="f37ba-116">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="f37ba-117">**Collider** コンポーネント、たとえばボックス コライダー</span><span class="sxs-lookup"><span data-stu-id="f37ba-117">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="f37ba-118">**Object Manipulator (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f37ba-118">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="f37ba-119">オブジェクトを **操作** し、**追跡対象の手でオブジェクトをつかむ** ことができるようにするには、オブジェクトに次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="f37ba-119">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="f37ba-120">**Collider** コンポーネント、たとえばボックス コライダー</span><span class="sxs-lookup"><span data-stu-id="f37ba-120">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="f37ba-121">**Object Manipulator (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f37ba-121">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="f37ba-122">**NearInteractionGrabbable** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f37ba-122">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="f37ba-123">さらに、探査車のパーツを Rover に配置して完全な探査車アセンブリにすることができるように、Rover Explorer を構成します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-123">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="f37ba-124">[階層] ウィンドウで、RoverExplorer > **RoverParts** オブジェクトの順に展開し、そのすべての子の探査車のパーツ オブジェクトと **RoverAssembly** オブジェクトを選択します。その後、[インスペクター] ウィンドウで、 **[コンポーネントの追加]** ボタンを使用して、選択されたすべてのオブジェクトに次のコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-124">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="f37ba-125">**Object Manipulator (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f37ba-125">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="f37ba-126">**NearInteractionGrabbable** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f37ba-126">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="f37ba-127">**Part Assembly Controller (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f37ba-127">**Part Assembly Controller (Script)** component</span></span>

![RoverAssembly とすべての探査車パーツ オブジェクトが選択され、コンポーネントが追加されている Unity](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="f37ba-129">互いに隣接していない複数のオブジェクトを選択するには、CTRL キーを押しながらマウスを使用して、任意のオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-129">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="f37ba-130">このチュートリアルでは、コライダーが既に探査車のパーツに追加されています。</span><span class="sxs-lookup"><span data-stu-id="f37ba-130">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="f37ba-131">コライダーの詳細については、Unity の<a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">コライダー</a>に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f37ba-131">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="f37ba-132">Part Assembly Controller (Script) は MRTK の一部ではありませんが、チュートリアル アセットには含まれていました。</span><span class="sxs-lookup"><span data-stu-id="f37ba-132">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="f37ba-133">すべての探査車のパーツ オブジェクトと RoverAssembly オブジェクトを引き続き選択した状態で、[インスペクター] ウィンドウで、次のように **Object Manipulator (Script)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-133">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="f37ba-134">**[両手を使った操作の種類]** ドロップダウンで、[スケール] をオフにし、 **[移動]** と **[回転]** のみが有効になるようにします</span><span class="sxs-lookup"><span data-stu-id="f37ba-134">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![[Two Handed Manipulation Type]\(両手を使った操作の種類\) が構成された Unity](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="f37ba-136">この時点で、すべての探査車のパーツ オブジェクトと RoverAssembly オブジェクトのオブジェクト操作が有効になりました。</span><span class="sxs-lookup"><span data-stu-id="f37ba-136">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="f37ba-137">[プロジェクト] ウィンドウで、**Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** フォルダーの順に移動して、オーディオ クリップを見つけます。</span><span class="sxs-lookup"><span data-stu-id="f37ba-137">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **StandardAssets** > **Audio** folder to locate the audio clips:</span></span>

![[Audio] フォルダーが選択されているプロジェクト ウィンドウが表示された Unity](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="f37ba-139">[階層] ウィンドウで、すべての **探査車のパーツ オブジェクト** をもう一度選択します。その後、[インスペクター] ウィンドウで、 **[コンポーネントの追加]** ボタンを使用し、**Audio Sources** コンポーネントを追加して、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-139">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="f37ba-140">**MRTK_Scale_Start** オーディオ クリップを **AudioClip** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="f37ba-140">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="f37ba-141">**[Play On Awake]\(起動時に再生\)** チェックボックスをオフにします</span><span class="sxs-lookup"><span data-stu-id="f37ba-141">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="f37ba-142">**[Spatial Blend]\(空間ブレンド\)** を 1 に変更します</span><span class="sxs-lookup"><span data-stu-id="f37ba-142">Change **Spatial Blend** to 1</span></span>

![すべての探査車パーツ オブジェクトが選択され、Audio Source コンポーネントが追加され構成されている Unity](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="f37ba-144">[階層] ウィンドウで、RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** オブジェクトの順に展開し、すべての配置ヒント オブジェクトを表示します。その後、最初の探査車のパーツである、RoverParts > **Camera_Part** の順に選択し、**Part Assembly Controller (Script)** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-144">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="f37ba-145">**Camera_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="f37ba-145">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![Camera_Part PartAssemblyController コンポーネントが構成された Unity](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="f37ba-147">残りの探査車のパーツ オブジェクトと RoverAssembly オブジェクトのそれぞれに対して、この手順を **繰り返し**、次のように **Part Assembly Controller (Script)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-147">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="f37ba-148">**Generator_Part** については、**Generator_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="f37ba-148">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="f37ba-149">**Lights_Part** については、**Lights_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="f37ba-149">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="f37ba-150">**UHFAntenna_Part** については、**UHFAntenna_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="f37ba-150">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="f37ba-151">**Spectrometer_Part** については、**Spectrometer_PlacementHint** オブジェクトを **[Location To Place]\(配置する場所\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="f37ba-151">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="f37ba-152">**RoverAssembly** については、オブジェクト自体 (つまり、同じ **RoverAssembly** オブジェクト) を **[Location To Place]\(配置する場所\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="f37ba-152">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="f37ba-153">[階層] ウィンドウで、[RoverExplorer] > [ボタン] > **[リセット]** ボタン オブジェクトの順に選択します。その後、[インスペクター] ウィンドウで、次のように Interactable **OnClick ()** イベントを構成します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-153">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="f37ba-154">**RoverAssembly** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="f37ba-154">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f37ba-155">**[No Function]\(関数なし\)** ドロップダウンから、**PartAssemblyController** > **ResetPlacement ()** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="f37ba-155">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![[リセット] ボタン オブジェクトの OnClick イベントが構成された Unity](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="f37ba-157">ゲーム モードになったら、近距離または遠距離操作を使用して、探査車のパーツを Rover に配置できます。</span><span class="sxs-lookup"><span data-stu-id="f37ba-157">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="f37ba-158">パーツは、対応する配置ヒントに近づくと、自動的に所定の位置にはめ込まれ、Rover の一部になります。</span><span class="sxs-lookup"><span data-stu-id="f37ba-158">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="f37ba-159">配置をリセットする場合は、[リセット] ボタンを押すことができます。</span><span class="sxs-lookup"><span data-stu-id="f37ba-159">To reset the placements, you can press the Reset button:</span></span>

![[リセット] ボタンが押されている再生モードの分割ビューが表示された Unity](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="f37ba-161">Object Manipulator コンポーネントとその関連プロパティの詳細については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の「[オブジェクト マニピュレーター](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html)」のガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f37ba-161">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="adding-bounding-boxes"></a><span data-ttu-id="f37ba-162">境界ボックスの追加</span><span class="sxs-lookup"><span data-stu-id="f37ba-162">Adding bounding boxes</span></span>

<span data-ttu-id="f37ba-163">境界ボックスには、拡大縮小および回転に使用できるハンドルが用意されているため、1 つの手で、近距離と遠距離の両方のオブジェクトを操作するのがより簡単かつ直感的になります。</span><span class="sxs-lookup"><span data-stu-id="f37ba-163">Bounding boxes make it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="f37ba-164">この例では、RoverExplorer オブジェクトに境界ボックスを追加して、エクスペリエンス全体を簡単に移動、回転、スケーリングできるようにします。</span><span class="sxs-lookup"><span data-stu-id="f37ba-164">In this example, you will add a bounding box to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="f37ba-165">また、境界ボックスのオンとオフを切り替えられるように、メニューを構成します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-165">Additionally, you will configure the Menu so you can turn the Bounding Box on and off.</span></span>

<span data-ttu-id="f37ba-166">[階層] ウィンドウで、 **[RoverExplorer]** オブジェクトを選択します。その後、[インスペクター] ウィンドウで、 **[コンポーネントの追加]** ボタンを使用して、以下のコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-166">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="f37ba-167">**BoundingBox** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f37ba-167">**BoundingBox** component</span></span>
* <span data-ttu-id="f37ba-168">**Object Manipulator (Script)** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f37ba-168">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="f37ba-169">その後、両方のコンポーネントの横にあるチェックボックスを **オフ** にして、既定で **無効** になるようにします。</span><span class="sxs-lookup"><span data-stu-id="f37ba-169">Then **uncheck** the checkbox next to both components to make them **disabled** by default:</span></span>

![RoverExplorer オブジェクトが選択され、コンポーネントが追加され無効にされている Unity](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="f37ba-171">境界ボックスの視覚エフェクトは実行時に作成されるため、ゲーム モードに入る前は表示されません。</span><span class="sxs-lookup"><span data-stu-id="f37ba-171">The Bounding Box visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
> <span data-ttu-id="f37ba-172">BoundingBox コンポーネントによって、実行時に NearInteractionGrabbable コンポーネントが自動的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="f37ba-172">The BoundingBox component will automatically add the NearInteractionGrabbable component at runtime.</span></span> <span data-ttu-id="f37ba-173">したがって、このコンポーネントを追加して、追跡対象の手で囲まれたオブジェクトをつかむ必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f37ba-173">Therefore, we do not need to add this component to grab the enclosed objects with tracked hands.</span></span>

<span data-ttu-id="f37ba-174">[階層] ウィンドウで、[メニュー] > **[ButtonCollection]** オブジェクトの順に展開して 4 つのボタンを表示し、3 番目のボタンの名前を **BoundingBox_Enable** に変更します。その後、[インスペクター] ウィンドウで、**Button Config Helper (Script)** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-174">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundingBox_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="f37ba-175">**[Main Label Text]\(メイン ラベル テキスト\)** を **[有効]** に変更します</span><span class="sxs-lookup"><span data-stu-id="f37ba-175">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="f37ba-176">**RoverExplorer** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="f37ba-176">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f37ba-177">**[No Function]\(関数なし\)** ドロップダウンから、 **[BoundingBox]**  >  **[bool Enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="f37ba-177">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="f37ba-178">引数チェックボックスが **オン** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="f37ba-178">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="f37ba-179">小さい **[+]** アイコンをクリックして、別のイベントを追加します</span><span class="sxs-lookup"><span data-stu-id="f37ba-179">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="f37ba-180">**RoverExplorer** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="f37ba-180">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f37ba-181">**[No Function]\(関数なし\)** ドロップダウンから、 **[ObjectManipulator]**  >  **[bool Enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="f37ba-181">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="f37ba-182">引数チェックボックスが **オン** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="f37ba-182">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="f37ba-183">**[アイコン]** は、'境界ボックスがあるキューブ' アイコンのままにしておきます</span><span class="sxs-lookup"><span data-stu-id="f37ba-183">Leave the **Icon** as the 'cube with bounding box' icon</span></span>

![BoundingBox_Enable ボタン オブジェクトが選択され、Button Config Helper コンポーネントが構成された Unity](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="f37ba-185">4 番目と最後のボタンの名前を **BoundingBox_Disable** に変更します。その後、[インスペクター] ウィンドウで、次のように **Button Config Helper (Script)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="f37ba-185">Rename the forth and last button to **BoundingBox_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="f37ba-186">**[Main Label Text]\(メイン ラベル テキスト\)** を **[無効]** に変更します</span><span class="sxs-lookup"><span data-stu-id="f37ba-186">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="f37ba-187">**RoverExplorer** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="f37ba-187">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f37ba-188">**[No Function]\(関数なし\)** ドロップダウンから、 **[BoundingBox]**  >  **[bool Enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="f37ba-188">From the **No Function** dropdown, select **BoundingBox** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="f37ba-189">引数チェックボックスが **オフ** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="f37ba-189">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="f37ba-190">小さい **[+]** アイコンをクリックして、別のイベントを追加します</span><span class="sxs-lookup"><span data-stu-id="f37ba-190">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="f37ba-191">**RoverExplorer** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="f37ba-191">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="f37ba-192">**[No Function]\(関数なし\)** ドロップダウンから、 **[ObjectManipulator]**  >  **[bool Enabled]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="f37ba-192">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="f37ba-193">引数チェックボックスが **オフ** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="f37ba-193">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="f37ba-194">**[アイコン]** を、'境界ボックスがあるキューブ' アイコンに変更します</span><span class="sxs-lookup"><span data-stu-id="f37ba-194">Change the **Icon** to the 'cube with bounding box" icon</span></span>

![BoundingBox_Disable オブジェクトが選択され、Button Config Helper コンポーネントが構成された Unity](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="f37ba-196">ゲーム モードに入り、[有効] ボタンをクリックして境界ボックスを有効にしたら、近距離または遠距離操作を使用して、境界ボックスの移動、回転、およびスケーリングを行い、[無効] ボタンを使用して、境界ボックスをもう一度無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="f37ba-196">If you now enter Game mode and enable the Bounding Box by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounding Box, and use the Disable button to disable the Bounding Box again:</span></span>

![境界ボックスが操作されている再生モードの分割ビューが表示された Unity](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="f37ba-198">Bounding Box コンポーネントとその関連プロパティの詳細については、[MRTK ドキュメントポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)の[境界ボックス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)に関するガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f37ba-198">To learn more about the Bounding Box component and its associated properties, you can visit the [Bounding box](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="f37ba-199">結論</span><span class="sxs-lookup"><span data-stu-id="f37ba-199">Congratulations</span></span>

<span data-ttu-id="f37ba-200">このチュートリアルでは、3D オブジェクトの近距離および遠距離操作を有効にする方法と、許可される操作の種類を制限する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="f37ba-200">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="f37ba-201">また、オブジェクトの操作をより簡単に制御できるように、3D オブジェクトの周囲に境界ボックスを追加する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="f37ba-201">You also learned how to add bounding boxes around 3D objects to make it easier to control the object manipulation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f37ba-202">次のチュートリアル:8.視線追跡の使用</span><span class="sxs-lookup"><span data-stu-id="f37ba-202">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
