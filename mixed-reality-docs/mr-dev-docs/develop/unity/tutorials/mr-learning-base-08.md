---
title: 視線追跡の使用
description: このコースでは、Mixed Reality Toolkit (MRTK) を使用して Mixed Reality アプリで視線追跡を使用する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, 視線追跡
ms.localizationpriority: high
ms.openlocfilehash: e4104dfd0d7b27425217c8cb92fa36c807053081
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590374"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="1ef39-104">8.視線追跡の使用</span><span class="sxs-lookup"><span data-stu-id="1ef39-104">8. Using eye-tracking</span></span>

<span data-ttu-id="1ef39-105">このチュートリアルでは、HoloLens 2 の視線追跡を有効にし、視線追跡をオブジェクトに追加して、ユーザーがオブジェクトを見たときにアクションをトリガーする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1ef39-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="1ef39-106">このプロジェクトを HoloLens (第 1 世代) にもデプロイする場合、視線追跡は HoloLens 2 でのみサポートされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1ef39-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="1ef39-107">目標</span><span class="sxs-lookup"><span data-stu-id="1ef39-107">Objectives</span></span>

* <span data-ttu-id="1ef39-108">HoleLens 2 の視線追跡を有効にする方法を学習する</span><span class="sxs-lookup"><span data-stu-id="1ef39-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="1ef39-109">視線追跡を使用してアクションをトリガーする方法を学習する</span><span class="sxs-lookup"><span data-stu-id="1ef39-109">Learn how to use eye-tracking to trigger action</span></span>

## <a name="ensuring-the-eye-gaze-input-capability-is-enabled"></a><span data-ttu-id="1ef39-110">視線入力機能を確実に有効にする</span><span class="sxs-lookup"><span data-stu-id="1ef39-110">Ensuring the Eye Gaze Input capability is enabled</span></span>

<span data-ttu-id="1ef39-111">[Unity] メニューで、[Mixed Reality Toolkit] > [ユーティリティ] > **[Configure Unity Project]\(Unity プロジェクトの構成\)** の順に選択して **[MRTK Project Configurator]** ウィンドウを開き、 **[UWP Capabilities]\(UWP 機能\)** セクションで **[Enable Eye Gaze Input Capability]\(視線入力機能を有効にする\)** がグレーで表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1ef39-111">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Eye Gaze Input Capability** is greyed out:</span></span>

![[MRTK Project Configurator]\(MRTK プロジェクト コンフィギュレーター\) ウィンドウが表示された Unity](images/mr-learning-base/base-08-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="1ef39-113">視線入力機能は、このチュートリアル シリーズの冒頭で Unity プロジェクトを構成したときに、[MRTK Project Configurator 設定を適用する](mr-learning-base-02.md#creating-and-configuring-the-scene)手順で有効にする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="1ef39-113">The Gaze Input capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#creating-and-configuring-the-scene) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="1ef39-114">しかし、有効にしていない場合は、ここで必ず有効にしてください。</span><span class="sxs-lookup"><span data-stu-id="1ef39-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="1ef39-115">Gaze Provider で目の動きに基づく視線入力を有効にする</span><span class="sxs-lookup"><span data-stu-id="1ef39-115">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="1ef39-116">[Hierarchy]\(階層\) ウィンドウで **[MixedRealityToolkit]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで [MixedRealityToolkit] > **[入力]** タブの順に選択して、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1ef39-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="1ef39-117">**DefaultHoloLens2InputSystemProfile** をクローンし、適切な名前 (たとえば、_GettingStarted_HoloLens2InputSystemProfile_) を付けます</span><span class="sxs-lookup"><span data-stu-id="1ef39-117">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="1ef39-118">**[ポインター]** セクションを展開します</span><span class="sxs-lookup"><span data-stu-id="1ef39-118">Expand the **Pointers** section</span></span>
* <span data-ttu-id="1ef39-119">**DefaultMixedRealityPointerProfile** をクローンし、適切な名前 (たとえば、_GettingStarted_MixedRealityPointerProfile_) を付けます</span><span class="sxs-lookup"><span data-stu-id="1ef39-119">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="1ef39-120">**[Gaze Settings]\(視線入力の設定\)** セクションを見つけて、 **[Is Eye Tracking Enabled]\(視線追跡を有効にする\)** チェックボックスをオンにします</span><span class="sxs-lookup"><span data-stu-id="1ef39-120">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![新しく作成されたプロファイルが適用され、視線追跡が有効にされた MixedRealityToolkit コンポーネントが表示された Unity](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="1ef39-122">MRTK プロファイルをクローンする方法については、[MRTK プロファイルの構成](mr-learning-base-03.md)に関するページにある手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1ef39-122">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="1ef39-123">Unity エディターの視線追跡シミュレーションを有効にする</span><span class="sxs-lookup"><span data-stu-id="1ef39-123">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="1ef39-124">[Hierarchy]\(階層\) ウィンドウで **[MixedRealityToolkit]** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **[入力]** タブの順に選択して、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1ef39-124">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="1ef39-125">**[Input Data Providers]\(入力データ プロバイダー\)**  >  **[Input Simulation Service]\(入力シミュレーション サービス\)** セクションの順に展開します</span><span class="sxs-lookup"><span data-stu-id="1ef39-125">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="1ef39-126">**DefaultMixedRealityInputSimulationProfile** をクローンし、適切な名前 (たとえば、_GettingStarted_MixedRealityInputSimulationProfile_) を付けます</span><span class="sxs-lookup"><span data-stu-id="1ef39-126">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="1ef39-127">**[Eye Gaze Simulation]\(視線入力シミュレーション\)** を見つけて、 **[Default Eye Gaze Simulation Mode]\(既定の視線入力シミュレーション モード\)** を **[Camera Forward Axis]\(カメラの前方の軸\)** に設定します</span><span class="sxs-lookup"><span data-stu-id="1ef39-127">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![TextMeshPro オブジェクトが選択されている Unity](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="1ef39-129">視線追跡をオブジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="1ef39-129">Adding eye-tracking to objects</span></span>

<span data-ttu-id="1ef39-130">[Hierarchy]\(階層\) ウィンドウで、[RoverExplorer] > **[ボタン]** オブジェクトの順に展開し、3 つの子ボタン オブジェクトのそれぞれについて、[SeeItSayItLabel] > **[TextMeshPro]** オブジェクトの順に選択します。</span><span class="sxs-lookup"><span data-stu-id="1ef39-130">In the Hierarchy window, expand the RoverExplorer > **Buttons** object, then for each of the three child button objects, expand and select the SeeItSayItLabel > **TextMeshPro** object:</span></span>

![TextMeshPro オブジェクトが選択されている Unity](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="1ef39-132">[Inspector]\(インスペクター\) ウィンドウで 3 つの TextMeshPro オブジェクトが選択されたままの状態で、 **[Add Component]\(コンポーネントの追加\)** ボタンを使用して、選択されたすべてのオブジェクトに次のコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="1ef39-132">With the three TextMeshPro objects still selected, in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="1ef39-133">**Box Collider** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1ef39-133">**Box Collider** component</span></span>
* <span data-ttu-id="1ef39-134">**EyeTrackingTarget** コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1ef39-134">**EyeTrackingTarget** component</span></span>

![TextMeshPro オブジェクトが選択され、コンポーネントが追加されている Unity](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="1ef39-136">[Hierarchy]\(階層\) ウィンドウで、 **[ヒント]** > [SeeItSayItLabel] > **TextMeshPro** オブジェクトの順に選択し、**EyeTrackingTarget** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="1ef39-136">In the Hierarchy window, select the **Hints** > SeeItSayItLabel > **TextMeshPro** object, then configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="1ef39-137">**On Look At Start ()** イベント セクション内</span><span class="sxs-lookup"><span data-stu-id="1ef39-137">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="1ef39-138">小さい **[+]** アイコンをクリックして、別のイベントを追加します</span><span class="sxs-lookup"><span data-stu-id="1ef39-138">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="1ef39-139">オブジェクト自体、つまり同じ **TextMeshPro** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="1ef39-139">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="1ef39-140">**[No Function]\(関数なし\)** ドロップダウンから、 **[TextMeshPro]**  >  **[float fontSize]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="1ef39-140">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="1ef39-141">引数を **0.06** に設定して、現在のフォント サイズ 0.04 を 50% 増加します</span><span class="sxs-lookup"><span data-stu-id="1ef39-141">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="1ef39-142">**On Look Away ()** イベント セクション内</span><span class="sxs-lookup"><span data-stu-id="1ef39-142">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="1ef39-143">小さい **[+]** アイコンをクリックして、別のイベントを追加します</span><span class="sxs-lookup"><span data-stu-id="1ef39-143">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="1ef39-144">オブジェクト自体、つまり同じ **TextMeshPro** オブジェクトを **[None (Object)]\(なし (オブジェクト)\)** フィールドに割り当てます</span><span class="sxs-lookup"><span data-stu-id="1ef39-144">Assign the object itself, i.e. the same **TextMeshPro** object, to the **None (Object)** field</span></span>
  * <span data-ttu-id="1ef39-145">**[No Function]\(関数なし\)** ドロップダウンから、 **[TextMeshPro]**  >  **[float fontSize]** の順に選択し、イベントがトリガーされたときにこのプロパティ値を更新するようにします</span><span class="sxs-lookup"><span data-stu-id="1ef39-145">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="1ef39-146">引数を **0.04** に設定し、フォント サイズを 0.04 に戻します</span><span class="sxs-lookup"><span data-stu-id="1ef39-146">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![Hints TextMeshPro オブジェクトが選択され、EyeTrackingTarget コンポーネントが構成された Unity](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="1ef39-148">**[Explode]\(展開\)** > [SeeItSayItLabel] > **[TextMeshPro]** オブジェクトと **[リセット]** > [SeeItSayItLabel] > **[TextMeshPro]** オブジェクトに対して、この手順を **繰り返し** ます。</span><span class="sxs-lookup"><span data-stu-id="1ef39-148">**Repeat** this step for the **Explode** > SeeItSayItLabel > **TextMeshPro** object and the **Reset** > SeeItSayItLabel > **TextMeshPro** object.</span></span>

<span data-ttu-id="1ef39-149">ここで、ゲーム モードに入り、マウスの右ボタンを押したまま、視線がラベルの 1 つをヒットするまでマウスを移動すると、フォント サイズが 50% 増加され、視線が離れると元のサイズに戻ることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="1ef39-149">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the labels, you will see the font size increase by 50% and reset back to its original size when looking away:</span></span>

![視線ヒット視線追跡が [Explode]\(展開\) ボタン ラベルをターゲットにしている再生モードの分割ビューが表示された Unity](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="1ef39-151">結論</span><span class="sxs-lookup"><span data-stu-id="1ef39-151">Congratulations</span></span>

<span data-ttu-id="1ef39-152">このチュートリアルでは、HoloLens 2 の視線追跡を有効にし、視線追跡をオブジェクトに追加して、ユーザーがオブジェクトを見たときにアクションをトリガーする方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="1ef39-152">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1ef39-153">次のチュートリアル:9.音声コマンドの使用</span><span class="sxs-lookup"><span data-stu-id="1ef39-153">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
