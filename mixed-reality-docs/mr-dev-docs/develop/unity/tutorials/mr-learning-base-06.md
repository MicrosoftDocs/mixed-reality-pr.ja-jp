---
title: 入門チュートリアル - 6. ユーザー インターフェイスの作成
description: このコースでは、Mixed Reality Toolkit (MRTK) を使用してユーザー インターフェイスを作成する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 2d3a826ba3bf8fdf1299038a7964278f0d57dbb7
ms.sourcegitcommit: 63c228af55379810ab2ee4f09f20eded1bb76229
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/04/2020
ms.locfileid: "93353540"
---
# <a name="6-creating-user-interfaces"></a><span data-ttu-id="74578-105">6.ユーザー インターフェイスの作成</span><span class="sxs-lookup"><span data-stu-id="74578-105">6. Creating user interfaces</span></span>

## <a name="overview"></a><span data-ttu-id="74578-106">概要</span><span class="sxs-lookup"><span data-stu-id="74578-106">Overview</span></span>

<span data-ttu-id="74578-107">このチュートリアルでは、MRTK のボタンとメニュー プレハブを Unity の TextMeshPro コンポーネントと共に使用して、シンプルなユーザー インターフェイスを作成する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="74578-107">In this tutorial, you will learn how to create a simple user interface using MRTK's button and menu prefabs alongside Unity's TextMeshPro component.</span></span> <span data-ttu-id="74578-108">また、ボタンでイベントがトリガーされるように構成する方法と、ユーザーに追加情報を提供する動的なヒント UI 要素を追加する方法についても学習します。</span><span class="sxs-lookup"><span data-stu-id="74578-108">You will also learn how to configure the buttons to trigger events and add dynamic tooltip UI elements to provide the user with additional information.</span></span>

## <a name="objectives"></a><span data-ttu-id="74578-109">目標</span><span class="sxs-lookup"><span data-stu-id="74578-109">Objectives</span></span>

* <span data-ttu-id="74578-110">コレクション内のボタンを整理する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="74578-110">Learn how to organize buttons in a collection</span></span>
* <span data-ttu-id="74578-111">MRTK のメニュー プレハブを使用する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="74578-111">Learn how to use MRTK's menu prefabs</span></span>
* <span data-ttu-id="74578-112">UI メニューとボタンを使用してホログラムを操作する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="74578-112">Learn how to interact with holograms using UI menus and buttons</span></span>
* <span data-ttu-id="74578-113">テキスト要素を追加する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="74578-113">Learn how to add text elements</span></span>
* <span data-ttu-id="74578-114">オブジェクト上にヒントを動的に生成する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="74578-114">Learn how to spawn tooltips on objects dynamically</span></span>

## <a name="creating-a-static-panel-of-buttons"></a><span data-ttu-id="74578-115">ボタンの静的パネルの作成</span><span class="sxs-lookup"><span data-stu-id="74578-115">Creating a static panel of buttons</span></span>

<span data-ttu-id="74578-116">[階層] ウィンドウで、**RoverExplorer** オブジェクトを右クリックし、 **[Create Empty]\(空アイテムの作成\)** を選択して、RoverExplorer の子として空のオブジェクトを追加し、そのオブジェクトに **Buttons** と名前を付けて、**Transform** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="74578-116">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **Buttons**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="74578-117">**位置**:X = -0.6、Y = 0.036、Z = -0.5</span><span class="sxs-lookup"><span data-stu-id="74578-117">**Position**: X = -0.6, Y = 0.036, Z = -0.5</span></span>
* <span data-ttu-id="74578-118">**回転**:X = 90、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="74578-118">**Rotation**: X = 90, Y = 0, Z = 0</span></span>
* <span data-ttu-id="74578-119">**スケール**:X = 1、Y = 1、Z = 1</span><span class="sxs-lookup"><span data-stu-id="74578-119">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![新しく作成された Buttons オブジェクトが選択され配置されている Unity](images/mr-learning-base/base-06-section1-step1-1.png)

<span data-ttu-id="74578-121">[プロジェクト] ウィンドウで、 **[アセット]**  >  **[MRTK.Tutorials.GettingStarted]**  >  **[Prefabs]\(プレハブ\)** フォルダーの順に移動し、**PressableRoundButton** プレハブをクリックして **Buttons** オブジェクトにドラッグします。次に、PressableRoundButton を右クリックし、 **[複製]** を選択してコピーを作成します。この操作を、PressableRoundButton オブジェクトが全部で 3 個できるまで繰り返します。</span><span class="sxs-lookup"><span data-stu-id="74578-121">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **PressableRoundButton** prefab on to the **Buttons** object, then right-click on the PressableRoundButton and select **Duplicate** to create a copy, repeat until you have a total of three PressableRoundButton objects:</span></span>

![PressableRoundButton プレハブが新しく追加された Unity](images/mr-learning-base/base-06-section1-step1-2.png)

<span data-ttu-id="74578-123">[階層] ウィンドウで、**Buttons** オブジェクトを選択します。次に、[インスペクター] ウィンドウで **[コンポーネントの追加]** ボタンを使用し、**GridObjectCollection** コンポーネントを追加して、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="74578-123">In the Hierarchy window, select the **Buttons** object, then in the Inspector window, use the **Add Component** button to add the **GridObjectCollection** component and configure it as follows:</span></span>

* <span data-ttu-id="74578-124">**並べ替えの種類**:子の順序</span><span class="sxs-lookup"><span data-stu-id="74578-124">**Sort Type**: Child Order</span></span>
* <span data-ttu-id="74578-125">**レイアウト**:横方向</span><span class="sxs-lookup"><span data-stu-id="74578-125">**Layout**: Horizontal</span></span>
* <span data-ttu-id="74578-126">**セルの幅**:0.2</span><span class="sxs-lookup"><span data-stu-id="74578-126">**Cell Width**: 0.2</span></span>
* <span data-ttu-id="74578-127">**アンカー**:中央左</span><span class="sxs-lookup"><span data-stu-id="74578-127">**Anchor**: Middle Left</span></span>

<span data-ttu-id="74578-128">次に、 **[コレクションの更新]** ボタンをクリックして、Buttons オブジェクトの子オブジェクトの位置を更新します。</span><span class="sxs-lookup"><span data-stu-id="74578-128">Then click the **Update Collection** button to update the position of the Buttons object's child objects:</span></span>

![GridObjectCollection コンポーネントが追加、構成、適用された Unity の Buttons オブジェクト](images/mr-learning-base/base-06-section1-step1-3.png)

<span data-ttu-id="74578-130">[階層] ウィンドウで、それらのボタンに **Hints**、**Explode**、**Reset** という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="74578-130">In the Hierarchy window, name the buttons **Hints**, **Explode**, and **Reset**.</span></span>

<span data-ttu-id="74578-131">各ボタンについて、**SeeItSayItLabel** > **TextMeshPro** 子オブジェクトの順に選択し、[インスペクター] ウィンドウで、それぞれの **TextMeshPro - Text** コンポーネントのテキストをそのボタンの名前と一致するように変更します。</span><span class="sxs-lookup"><span data-stu-id="74578-131">For each button, select the **SeeItSayItLabel** > **TextMeshPro** child object, then in the Inspector window, change the respective **TextMeshPro - Text** component text to match the button names:</span></span>

![ボタンのテキスト ラベルが構成された Unity](images/mr-learning-base/base-06-section1-step1-4.png)

<span data-ttu-id="74578-133">完了したら、Buttons オブジェクトの子オブジェクトを折りたたみます。</span><span class="sxs-lookup"><span data-stu-id="74578-133">Once done, collapse the Buttons object's child objects.</span></span>

<span data-ttu-id="74578-134">[階層] ウィンドウで、**Hints** ボタン オブジェクトを選択します。次に、[インスペクター] ウィンドウで、次のように Interactable **OnClick ()** イベントを構成します。</span><span class="sxs-lookup"><span data-stu-id="74578-134">In the Hierarchy window, select the **Hints** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="74578-135">**RoverAssembly** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="74578-135">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="74578-136">**[No Function]\(関数なし\)** ドロップダウンから、**PlacementHintsController** > **TogglePlacementHints ()** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="74578-136">From the **No Function** dropdown, select **PlacementHintsController** > **TogglePlacementHints ()** to set this function as the action to be executed when the event is triggered</span></span>

![Hints ボタン オブジェクトの OnClick イベントが構成された Unity](images/mr-learning-base/base-06-section1-step1-5.png)

<span data-ttu-id="74578-138">[階層] ウィンドウで、**Explode** ボタン オブジェクトを選択します。次に、[インスペクター] ウィンドウで、次のように Interactable **OnClick ()** イベントを構成します。</span><span class="sxs-lookup"><span data-stu-id="74578-138">In the Hierarchy window, select the **Explode** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="74578-139">**RoverAssembly** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="74578-139">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="74578-140">**[No Function]\(関数なし\)** ドロップダウンから、**ExplodedViewController** > **ToggleExplodedView ()** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="74578-140">From the **No Function** dropdown, select **ExplodedViewController** > **ToggleExplodedView ()** to set this function as the action to be executed when the event is triggered</span></span>

![Explode ボタン オブジェクトの OnClick イベントが構成された Unity](images/mr-learning-base/base-06-section1-step1-6.png)

<span data-ttu-id="74578-142">[再生] ボタンを押してゲーム モードに入り、スペース バー ボタンを押したままにして手をアクティブにし、マウスを使用して **Hints** ボタンを押して、配置ヒント オブジェクトの可視性を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="74578-142">Press the Play button to enter Game mode, then press-and-hold the space bar button to activate the hand and use the mouse to press the **Hints** button to toggle the visibility of the placement hint objects:</span></span>

![[ヒント] ボタンが押されている Unity 再生モードの分割ビュー](images/mr-learning-base/base-06-section1-step1-7.png)

<span data-ttu-id="74578-144">また、**Explode** ボタンを押して、分解ビューのオンとオフを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="74578-144">and the **Explode** button to toggle the exploded view on and off:</span></span>

![[分解] ボタンが押されている Unity 再生モードの分割ビュー](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a><span data-ttu-id="74578-146">ユーザーに追従する動的メニューの作成</span><span class="sxs-lookup"><span data-stu-id="74578-146">Creating a dynamic menu that follows the user</span></span>

<span data-ttu-id="74578-147">[プロジェクト] ウィンドウで、 **[資産]**  >  **[MRTK]**  >  **[SDK]**  >  **[Features]\(機能\)**  >  **[UX]**  >  **[Prefabs]\(プレハブ\)**  >  **[Menus]\(メニュー\)** フォルダーの順に移動し、 **[NearMenu4x1]** プレハブをクリックして [階層] ウィンドウにドラッグします。その [Transform]\(変換\) の **[Position]\(位置\)** を X = 0、Y = -0.4、Z = 0 に設定し、以下のように構成します。</span><span class="sxs-lookup"><span data-stu-id="74578-147">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **Menus** folder, click-and-drag the **NearMenu4x1** prefab into the Hierarchy window, set its Transform **Position** to X = 0, Y = -0.4, Z = 0 and configure it as follows:</span></span>

* <span data-ttu-id="74578-148">**SolverHandler** コンポーネントの **[Tracked Target Type]\(追跡対象の種類\)** が **[ヘッド]** に設定されていることを確認します</span><span class="sxs-lookup"><span data-stu-id="74578-148">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="74578-149">**RadialView** Solver コンポーネントの横にあるチェックボックスをオンにして、既定で有効になるようにします</span><span class="sxs-lookup"><span data-stu-id="74578-149">Check the checkbox next to the **RadialView** Solver component so it is enabled by default</span></span>

![新しく追加されたメニューの近くのプレハブが選択されている Unity](images/mr-learning-base/base-06-section2-step1-1.png)

<span data-ttu-id="74578-151">[階層] ウィンドウで、オブジェクトの名前を **Menu** に変更し、**ButtonCollection** 子オブジェクトを展開して、次の 4 つのボタンを表示します。</span><span class="sxs-lookup"><span data-stu-id="74578-151">In the Hierarchy window, rename the object to **Menu**, then expand its **ButtonCollection** child object to reveal the four buttons:</span></span>

![Menu オブジェクトが選択されて ButtonCollection オブジェクトが展開されている Unity](images/mr-learning-base/base-06-section2-step1-2.png)

<span data-ttu-id="74578-153">最初のボタンの名前を **Indicator** に変更します。その後、[インスペクター] ウィンドウで、次のように **Button Config Helper (Script)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="74578-153">Rename the first button to **Indicator**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="74578-154">ボタンの名前と一致するように **[Main Label Text]\(メイン ラベル テキスト\)** を変更します</span><span class="sxs-lookup"><span data-stu-id="74578-154">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="74578-155">**Indicator** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="74578-155">Assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="74578-156">**[No Function]\(関数なし\)** ドロップダウンから、**GameObject** > **SetActive (bool)** の順に選択し、イベントがトリガーされたときに実行するアクションとして、この関数を設定します</span><span class="sxs-lookup"><span data-stu-id="74578-156">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="74578-157">引数チェックボックスが **オン** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="74578-157">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="74578-158">**アイコン** を [検索] アイコンに変更します</span><span class="sxs-lookup"><span data-stu-id="74578-158">Change the **Icon** to the 'search' icon</span></span>

![Indicator ボタン オブジェクトのボタン構成ヘルパーが構成されている Unity](images/mr-learning-base/base-06-section2-step1-3.png)

<span data-ttu-id="74578-160">[階層] ウィンドウで **Indicator** オブジェクトを選択します。次に、[インスペクター] ウィンドウで以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="74578-160">In the Hierarchy window, select the **Indicator** object, then in the Inspector window:</span></span>

* <span data-ttu-id="74578-161">その名前の横にあるチェックボックスをオフにして、既定で非アクティブにします</span><span class="sxs-lookup"><span data-stu-id="74578-161">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="74578-162">**[コンポーネントの追加]** ボタンを使用して **Directional Indicator Controller (Script)** コンポーネントを追加します</span><span class="sxs-lookup"><span data-stu-id="74578-162">Use the **Add Component** button to add the **Directional Indicator Controller (Script)** component</span></span>

![Indicator オブジェクトが選択されて無効化され、DirectionalIndicatorController コンポーネントが追加された Unity](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="74578-164">これで、アプリの起動時にインジケーターは既定で無効になり、[Indicator]\(インジケーター\) ボタンを押すと有効にできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="74578-164">Now, when the app starts, the Indicator is disabled by default and can be enabled by pressing the Indicator button.</span></span>

<span data-ttu-id="74578-165">2 番目のボタンの名前を **TapToPlace** に変更します。その後、[インスペクター] ウィンドウで、次のように **Button Config Helper (Script)** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="74578-165">Rename the second button to **TapToPlace**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="74578-166">ボタンの名前と一致するように **[Main Label Text]\(メイン ラベル テキスト\)** を変更します</span><span class="sxs-lookup"><span data-stu-id="74578-166">Change the **Main Label Text** to match the name of the button</span></span>
* <span data-ttu-id="74578-167">RoverExplorer > **RoverAssembly** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="74578-167">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="74578-168">**[No Function]\(関数なし\)** ドロップダウンから、**TapToPlace** > **bool Enabled** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="74578-168">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="74578-169">引数チェックボックスが **オン** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="74578-169">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="74578-170">**アイコン** を [hand with ray]\(手の光線を表示\) アイコンに変更します</span><span class="sxs-lookup"><span data-stu-id="74578-170">Change the **Icon** to the 'hand with ray' icon</span></span>

![TapToPlace ボタン オブジェクトのボタン構成ヘルパーが構成されている Unity](images/mr-learning-base/base-06-section2-step1-5.png)

<span data-ttu-id="74578-172">[階層] ウィンドウで **RoverAssembly** オブジェクトを選択してから、[インスペクター] ウィンドウで **Tap To Place (Script)** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="74578-172">In the Hierarchy window, select the **RoverAssembly** object, then in the Inspector window, configure the **Tap To Place (Script)** component as follows:</span></span>

* <span data-ttu-id="74578-173">その名前の横にあるチェックボックスをオフにして、既定で非アクティブにします</span><span class="sxs-lookup"><span data-stu-id="74578-173">Uncheck the checkbox next to its name to make it inactive by default</span></span>
* <span data-ttu-id="74578-174">**On Placing Stopped ()** イベント セクションで、 **+** アイコンをクリックし、新しいイベントを追加します。</span><span class="sxs-lookup"><span data-stu-id="74578-174">In the **On Placing Stopped ()** event section, click the **+** icon to add a new event:</span></span>
* <span data-ttu-id="74578-175">RoverExplorer > **RoverAssembly** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="74578-175">Assign the RoverExplorer > **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="74578-176">**[No Function]\(関数なし\)** ドロップダウンから、**TapToPlace** > **bool Enabled** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="74578-176">From the **No Function** dropdown, select **TapToPlace** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="74578-177">引数チェックボックスが **オフ** になっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="74578-177">Verify that the argument checkbox is **unchecked**</span></span>

![TapToPlace コンポーネントが再構成された Unity](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> <span data-ttu-id="74578-179">これで、アプリの起動時に Tap to Place 機能は既定で無効になり、[Tap to Place] ボタンを押すと有効にできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="74578-179">Now, when the app starts, the Tap to Place functionality is disabled by default and can be enabled by pressing the Tap to Place button.</span></span> <span data-ttu-id="74578-180">また、Tap to Place が完了すると、自動的に機能は無効になります。</span><span class="sxs-lookup"><span data-stu-id="74578-180">Additionally, when the tap to place is completed, it will disable itself.</span></span>

## <a name="adding-text-to-the-scene"></a><span data-ttu-id="74578-181">シーンへのテキストの追加</span><span class="sxs-lookup"><span data-stu-id="74578-181">Adding text to the scene</span></span>

<span data-ttu-id="74578-182">[階層] ウィンドウで、**Table** オブジェクトを右クリックし、 **[3D オブジェクト]**  >  **[Text - TextMeshPro]\(テキスト - TextMeshPro\)** の順に選択して、テキスト オブジェクトを Table オブジェクトの子として追加します。次に、[インスペクター] ウィンドウで、次のように **Rect Transform** コンポーネントを構成します。</span><span class="sxs-lookup"><span data-stu-id="74578-182">In the Hierarchy window, right-click on the **Table** object and select **3D Object** > **Text - TextMeshPro** to add a text object as a child of the Table object, then in the Inspector window, configure the **Rect Transform** component as follows:</span></span>

* <span data-ttu-id="74578-183">**[Pos Y]\(位置 Y\)** を 1 に変更します</span><span class="sxs-lookup"><span data-stu-id="74578-183">Change **Pos Y** to 1</span></span>
* <span data-ttu-id="74578-184">**[幅]** を 1 に変更します</span><span class="sxs-lookup"><span data-stu-id="74578-184">Change **Width** to 1</span></span>
* <span data-ttu-id="74578-185">**[高さ]** を 1 に変更します</span><span class="sxs-lookup"><span data-stu-id="74578-185">Change **Height** to 1</span></span>
* <span data-ttu-id="74578-186">**[回転 X]** を 90 に変更します</span><span class="sxs-lookup"><span data-stu-id="74578-186">Change **Rotation X** to 90</span></span>

![新しく作成された TextMeshPro オブジェクトが選択されている Unity](images/mr-learning-base/base-06-section3-step1-1.png)

<span data-ttu-id="74578-188">次に、**TextMeshPro - Text** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="74578-188">Then configure the **TextMeshPro - Text** component as follows::</span></span>

* <span data-ttu-id="74578-189">**[テキスト]** を Rover Explorer に変更します</span><span class="sxs-lookup"><span data-stu-id="74578-189">Change **Text** to Rover Explorer</span></span>
* <span data-ttu-id="74578-190">**[フォント スタイル]** を [太字] に変更します</span><span class="sxs-lookup"><span data-stu-id="74578-190">Change **Font Style** to Bold</span></span>
* <span data-ttu-id="74578-191">**[フォント サイズ]** を 1 に変更します</span><span class="sxs-lookup"><span data-stu-id="74578-191">Change **Font Size** to 1</span></span>
* <span data-ttu-id="74578-192">[追加設定] > **[余白]** を 0.03 に変更します</span><span class="sxs-lookup"><span data-stu-id="74578-192">Change Extra Settings > **Margins** to 0.03</span></span>

![TextMeshPro コンポーネントが構成された Unity](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a><span data-ttu-id="74578-194">ヒントの追加</span><span class="sxs-lookup"><span data-stu-id="74578-194">Adding tooltips</span></span>

<span data-ttu-id="74578-195">[プロジェクト] ウィンドウで、 **[アセット]**  >  **[MRTK]**  >  **[SDK]**  >  **[機能]**  >  **[UX]**  >  **[Prefabs]\(プレハブ\)**  >  **[ヒント]** フォルダーの順に移動して、ヒント プレハブを見つけます。</span><span class="sxs-lookup"><span data-stu-id="74578-195">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![ToolTips フォルダーが選択されている Unity プロジェクト ウィンドウ](images/mr-learning-base/base-06-section4-step1-1.png)

<span data-ttu-id="74578-197">[階層] ウィンドウで、RoverExplorer > **RoverParts** オブジェクトの順に展開し、そのすべての子のローバー パーツ オブジェクトを選択します。次に、[インスペクター] ウィンドウで **[コンポーネントの追加]** ボタンを使用し、**ToolTipSpawner** コンポーネントを追加して、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="74578-197">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects, then in the Inspector window, use the **Add Component** button to add the **ToolTipSpawner** component and configure it as follows:</span></span>

* <span data-ttu-id="74578-198">ヒントを表示するにはユーザーがそのパーツに視線を向けることが必要であるようにするため、 **[Focus Enabled]\(フォーカスが有効\)** チェックボックスがオンになっていることを確認します</span><span class="sxs-lookup"><span data-stu-id="74578-198">Ensure the **Focus Enabled** checkbox is checked to require the user to look at the part for the tooltip to appear</span></span>
* <span data-ttu-id="74578-199">**Simple Line ToolTip** プレハブを、[プロジェクト] ウィンドウから **[Tool Tip Prefab]\(ツール ヒント プレハブ\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="74578-199">Assign the **Simple Line ToolTip** prefab from the Project window to the **Tool Tip Prefab** field</span></span>
* <span data-ttu-id="74578-200">[ToolTip Override Settings]\(ヒントのオーバーライド設定\) > **[設定モード]** を **[オーバーライド]** に変更します</span><span class="sxs-lookup"><span data-stu-id="74578-200">Change the ToolTip Override Settings > **Settings Mode** to **Override**</span></span>
* <span data-ttu-id="74578-201">[ToolTip Override Settings]\(ヒントのオーバーライド設定\) > **[Manual Pivot Local Position Y]\(手動のピボットのローカル位置 Y\)** を **1.5** に変更します</span><span class="sxs-lookup"><span data-stu-id="74578-201">Change the ToolTip Override Settings > **Manual Pivot Local Position Y** to **1.5**</span></span>

![すべての探査車パーツ オブジェクトが選択され、ToolTipSpawner コンポーネントが追加されて構成された Unity](images/mr-learning-base/base-06-section4-step1-2.png)

<span data-ttu-id="74578-203">[階層] ウィンドウで、最初のローバー パーツを RoverParts > **Camera_Part** の順で選択し、**ToolTipSpawner** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="74578-203">In the Hierarchy window, select the first rover part, RoverParts > **Camera_Part**, and configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="74578-204">パーツの名前を反映するように、 **[Tool Tip Text]\(ツール ヒントのテキスト\)** を **Camera** に変更します</span><span class="sxs-lookup"><span data-stu-id="74578-204">Change **Tool Tip Text** to reflect the name of the part, i.e., **Camera**</span></span>

![カメラの ToolTipText が構成された Unity](images/mr-learning-base/base-06-section4-step1-3.png)

<span data-ttu-id="74578-206">それぞれのローバー パーツ オブジェクトに対してこの手順を **繰り返し** て、**ToolTipSpawner** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="74578-206">**Repeat** this step for each of the rover part objects to configure the **ToolTipSpawner** component as follows:</span></span>

* <span data-ttu-id="74578-207">**Generator_Part** では、 **[Tool Tip Text]\(ツール ヒントのテキスト\)** を **Generator** に変更する</span><span class="sxs-lookup"><span data-stu-id="74578-207">For the **Generator_Part**, change the **Tool Tip Text** to **Generator**</span></span>
* <span data-ttu-id="74578-208">**Lights_Part** では、 **[Tool Tip Text]\(ツール ヒントのテキスト\)** を **Lights** に変更する</span><span class="sxs-lookup"><span data-stu-id="74578-208">For the **Lights_Part**, change the **Tool Tip Text** to **Lights**</span></span>
* <span data-ttu-id="74578-209">**UHFAntenna_Part** では、 **[Tool Tip Text]\(ツール ヒントのテキスト\)** を **UHF Antenna field** に変更する</span><span class="sxs-lookup"><span data-stu-id="74578-209">For the **UHFAntenna_Part**, change the **Tool Tip Text** to **UHF Antenna** field</span></span>
* <span data-ttu-id="74578-210">**Spectrometer_Part** では、 **[Tool Tip Text]\(ツール ヒントのテキスト\)** を **Spectrometer** に変更する</span><span class="sxs-lookup"><span data-stu-id="74578-210">For the **Spectrometer_Part**, change the **Tool Tip Text** to **Spectrometer**</span></span>

<span data-ttu-id="74578-211">[再生] ボタンを押してゲーム モードに入り、マウスの右ボタンを押したまま、視線入力がパーツの 1 つに当たるまでマウスを移動します。すると、そのパーツのヒントが次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="74578-211">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the parts and the tooltip for that part will be displayed:</span></span>

![視線によってツールヒントがトリガーされた Unity の再生モード分割ビュー](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="74578-213">結論</span><span class="sxs-lookup"><span data-stu-id="74578-213">Congratulations</span></span>

<span data-ttu-id="74578-214">このチュートリアルでは、MRTK で用意されているボタンとメニュー プレハブを Unity の TextMeshPro コンポーネントと共に使用して、シンプルなユーザー インターフェイスを作成する方法について学習しました。また、ボタンが押されたときにイベントがトリガーされるようにボタンを構成する方法についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="74578-214">In this tutorial, you learned how to create a simple user interface using MRTK's provided button and menu prefabs alongside Unity's TextMeshPro component and how to configure the buttons to trigger events when they are pressed.</span></span> <span data-ttu-id="74578-215">さらに、動的なヒント UI 要素を追加して、ユーザーに追加情報を提供する方法についても学習しました。</span><span class="sxs-lookup"><span data-stu-id="74578-215">You also learned how to add dynamic tooltip UI elements to provide the user with additional information.</span></span>

[<span data-ttu-id="74578-216">次のチュートリアル:7.3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="74578-216">Next Tutorial: 7. Interacting with 3D objects</span></span>](mr-learning-base-07.md)