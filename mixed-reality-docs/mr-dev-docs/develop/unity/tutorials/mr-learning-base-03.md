---
title: 入門チュートリアル - 3. MRTK プロファイルの構成
description: このコースでは、Mixed Reality Toolkit (MRTK) を使用して複合現実のアプリケーションを作成する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 028da6e0dd920e90cb353c22d22ab985de56bb81
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91700002"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="6bdfc-105">3.MRTK プロファイルの構成</span><span class="sxs-lookup"><span data-stu-id="6bdfc-105">3. Configuring the MRTK profiles</span></span>

## <a name="overview"></a><span data-ttu-id="6bdfc-106">概要</span><span class="sxs-lookup"><span data-stu-id="6bdfc-106">Overview</span></span>

<span data-ttu-id="6bdfc-107">このチュートリアルでは、MRTK プロファイルをカスタマイズして構成する方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-107">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="6bdfc-108">この特定の例では、空間メッシュ オブザーバーの設定を変更して、空間認識メッシュを非表示にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-108">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="6bdfc-109">ただし、次の同じ原則に従って、MRTK プロファイルのすべての設定または値をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-109">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

## <a name="objectives"></a><span data-ttu-id="6bdfc-110">目標</span><span class="sxs-lookup"><span data-stu-id="6bdfc-110">Objectives</span></span>

* <span data-ttu-id="6bdfc-111">MRTK プロファイルをカスタマイズして構成する方法について学習する</span><span class="sxs-lookup"><span data-stu-id="6bdfc-111">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="6bdfc-112">空間認識メッシュを非表示にする</span><span class="sxs-lookup"><span data-stu-id="6bdfc-112">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="6bdfc-113">空間認識表示オプションを変更する</span><span class="sxs-lookup"><span data-stu-id="6bdfc-113">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="6bdfc-114">空間認識メッシュを非表示にするための主な手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-114">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="6bdfc-115">既定の構成プロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="6bdfc-115">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="6bdfc-116">空間認識システムを有効にする</span><span class="sxs-lookup"><span data-stu-id="6bdfc-116">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="6bdfc-117">既定の空間認識システムのプロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="6bdfc-117">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="6bdfc-118">既定の空間認識メッシュ オブザーバーのプロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="6bdfc-118">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="6bdfc-119">空間認識メッシュの可視性を変更する</span><span class="sxs-lookup"><span data-stu-id="6bdfc-119">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="6bdfc-120">既定では、MRTK プロファイルは編集できません。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-120">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="6bdfc-121">これらは、編集する前に複製する必要がある既定プロファイルのテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-121">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="6bdfc-122">入れ子になったプロファイル レイヤーがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-122">There are several nested layers of profiles.</span></span> <span data-ttu-id="6bdfc-123">そのため、1 つ以上の設定を構成するときは、複数のプロファイルを複製して編集するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-123">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="6bdfc-124">1.既定の構成プロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="6bdfc-124">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="6bdfc-125">構成プロファイルは最上位のプロファイルです。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-125">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="6bdfc-126">そのため、他のプロファイルを編集できるようにするには、まず構成プロファイルを複製する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-126">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="6bdfc-127">[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで、 **MixedRealityToolkit** の構成プロファイルを **DefaultHoloLens2ConfigurationProfile** に変更します。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-127">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile** :</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="6bdfc-129">**MixedRealityToolkit** オブジェクトを選択した状態で、[Inspector]\(インスペクター\) ウィンドウで **[Copy & Customize]\(コピーしてカスタマイズ\)** ボタンをクリックして、[Clone Profile]\(プロファイルの複製\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-129">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="6bdfc-131">[Clone Profile]\(プロファイルのクローン\) ウィンドウで、適切な **[Profile Name]\(プロファイル名\)** (例: _GettingStarted_HoloLens2ConfigurationProfile_ ) を入力し、 **[Clone]\(クローン\)** ボタンをクリックし、 **DefaultHololens2ConfigurationProfile** の編集可能なコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-131">In the Clone Profile window, enter a suitable **Profile Name** , for example, _GettingStarted_HoloLens2ConfigurationProfile_ , then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile** :</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="6bdfc-133">新しく作成された構成プロファイルが、シーンの構成プロファイルとして割り当てられました。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-133">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="6bdfc-135">Unity メニューで、 **[File]\(ファイル\)**  >  **[Save]\(保存\)** の順に選択してシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-135">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="6bdfc-136">チュートリアルの実行中は、必ず作業を保存するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-136">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="6bdfc-137">2.空間認識システムを有効にする</span><span class="sxs-lookup"><span data-stu-id="6bdfc-137">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="6bdfc-138">[Hierarchy]\(階層\) ウィンドウで **MixedRealityToolkit** オブジェクトを選択し、[Inspector]\(インスペクター\) ウィンドウで **[Spatial Awareness]\(空間認識\)** タブを選択し、次に **[Enable Spatial Awareness System]\(空間認識システムを有効にする\)** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-138">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step2-1.png)

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="6bdfc-140">3.既定の空間認識システムのプロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="6bdfc-140">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="6bdfc-141">**[Spatial Awareness]\(空間認識\)** タブで、 **[Clone]\(複製\)** ボタンをクリックして [Clone Profile]\(プロファイルの複製\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-141">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="6bdfc-143">[Clone Profile]\(プロファイルのクローン\) ウィンドウで、適切な **[Profile Name]\(プロファイル名\)** (例: _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_ ) を入力し、 **[Clone]\(クローン\)** ボタンをクリックし、 **DefaultMixedRealitySpatialAwarenessSystemProfile** の編集可能なコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-143">In the Clone Profile window, enter a suitable **Profile Name** , for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_ , then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile** :</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="6bdfc-145">これで、新しく作成された空間認識システム プロファイルが、構成プロファイルに自動的に割り当てられるようになりました。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-145">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="6bdfc-147">4.既定の空間認識メッシュ オブザーバーのプロファイルを複製する</span><span class="sxs-lookup"><span data-stu-id="6bdfc-147">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="6bdfc-148">**[Spatial Awareness]\(空間認識\)** タブを引き続き選択した状態で、 **[Windows Mixed Reality Spatial Mesh Observer]\(Windows Mixed Reality 空間メッシュ オブザーバー\)** セクションを展開し、 **[Clone]\(複製\)** ボタンをクリックして、[Clone Profile]\(プロファイルの複製\) ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-148">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="6bdfc-150">[Clone Profile]\(プロファイルのクローン\) ウィンドウで、適切な **[Profile Name]\(プロファイル名\)** (例: _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ ) を入力し、 **[Clone]\(クローン\)** ボタンをクリックし、 **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** の編集可能なコピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-150">In the Clone Profile window, enter a suitable **Profile Name** , for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ , then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile** :</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="6bdfc-152">これで、新しく作成された空間認識メッシュ オブザーバーが、空間認識システム プロファイルに自動的に割り当てられるようになりました。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-152">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="6bdfc-154">5.空間認識メッシュの可視性を変更する</span><span class="sxs-lookup"><span data-stu-id="6bdfc-154">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="6bdfc-155">**[Spatial Mesh Observer Settings]\(空間メッシュ オブザーバーの設定\)** で、 **[Display Option]\(表示オプション\)** を **[Occlusion]\(オクルージョン\)** に変更して、空間マッピング メッシュを、機能している状態のまま非表示にします。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-155">In the **Spatial Mesh Observer Settings** , change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![mr-learning-base](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="6bdfc-157">空間マッピング メッシュは非表示になっていますが、引き続き存在して、機能しています。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-157">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="6bdfc-158">たとえば、物理的な壁の後ろのホログラムなど、空間マッピング メッシュの背後にあるホログラムは表示されません。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-158">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="6bdfc-159">ここまで、MRTK プロファイル内の設定を変更する方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-159">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="6bdfc-160">ご覧のように、MRTK の設定をカスタマイズするには、最初に既定のプロファイルのコピーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-160">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="6bdfc-161">既定のプロファイルは編集できないため、既定の設定に戻す場合の参照として常に保持します。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-161">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="6bdfc-162">MRTK プロファイルとそのアーキテクチャの詳細については、[MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)にある [MRTK プロファイルの構成ガイド](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-162">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="6bdfc-163">結論</span><span class="sxs-lookup"><span data-stu-id="6bdfc-163">Congratulations</span></span>

<span data-ttu-id="6bdfc-164">このチュートリアルでは、MRTK プロファイルの設定をクローン、カスタマイズ、および構成する方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="6bdfc-164">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6bdfc-165">次のチュートリアル:4.シーンへのオブジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="6bdfc-165">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
