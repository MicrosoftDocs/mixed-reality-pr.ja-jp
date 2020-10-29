---
title: MR 基本 100-Unity の概要
description: 最初の基本的な mixed reality "hello world" アプリケーションを作成する方法について説明します。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: mixed reality、Windows Mixed Reality、HoloLens、イマーシブ、vr、mr、はじめに、ホログラム、academy、チュートリアル
ms.openlocfilehash: b2992f59970aaba44505d64de06e4ea57f400e1b
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686511"
---
# <a name="mr-basics-100-getting-started-with-unity"></a><span data-ttu-id="e79bf-104">MR の基本 100:Unity の概要</span><span class="sxs-lookup"><span data-stu-id="e79bf-104">MR Basics 100: Getting started with Unity</span></span>

>[!IMPORTANT]
><span data-ttu-id="e79bf-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="e79bf-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="e79bf-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="e79bf-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="e79bf-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。</span><span class="sxs-lookup"><span data-stu-id="e79bf-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="e79bf-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="e79bf-109">HoloLens 2 向けには、[新しいチュートリアル シリーズ](mrlearning-base.md)が投稿されています。</span><span class="sxs-lookup"><span data-stu-id="e79bf-109">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="e79bf-110">このチュートリアルでは、Unity でビルドされた基本的な mixed reality アプリを作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-110">This tutorial will walk you through creating a basic mixed reality app built with Unity.</span></span>

## <a name="device-support"></a><span data-ttu-id="e79bf-111">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="e79bf-111">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e79bf-112">コース</span><span class="sxs-lookup"><span data-stu-id="e79bf-112">Course</span></span></th><th style="width:150px"> <span data-ttu-id="e79bf-113"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="e79bf-113"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="e79bf-114"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="e79bf-114"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="e79bf-115">MR の基本 100:Unity の概要</span><span class="sxs-lookup"><span data-stu-id="e79bf-115">MR Basics 100: Getting started with Unity</span></span></td><td style="text-align: center;"> <span data-ttu-id="e79bf-116">✔️</span><span class="sxs-lookup"><span data-stu-id="e79bf-116">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="e79bf-117">✔️</span><span class="sxs-lookup"><span data-stu-id="e79bf-117">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="e79bf-118">前提条件</span><span class="sxs-lookup"><span data-stu-id="e79bf-118">Prerequisites</span></span>

* <span data-ttu-id="e79bf-119">適切な [ツールがインストール](../../install-the-tools.md)された WINDOWS 10 PC。</span><span class="sxs-lookup"><span data-stu-id="e79bf-119">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md).</span></span>

## <a name="chapter-1---create-a-new-project"></a><span data-ttu-id="e79bf-120">章 1-新しいプロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="e79bf-120">Chapter 1 - Create a New Project</span></span>

>[!VIDEO https://www.youtube.com/embed/2L5IFO0hnYA]

<span data-ttu-id="e79bf-121">Unity を使用してアプリをビルドするには、最初にプロジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e79bf-121">To build an app with Unity, you first need to create a project.</span></span> <span data-ttu-id="e79bf-122">このプロジェクトはいくつかのフォルダーに整理されています。最も重要なのは、アセットフォルダーです。</span><span class="sxs-lookup"><span data-stu-id="e79bf-122">This project is organized into a few folders, the most important of which is your Assets folder.</span></span> <span data-ttu-id="e79bf-123">これは、Maya、Max 映画4D または Photoshop などのデジタルコンテンツ作成ツールからインポートしたすべてのアセット、Visual Studio で作成したすべてのコード、または任意のコードエディターを使用して作成したすべてのコンテンツを保持するフォルダーで、さらに、エディターでシーン、アニメーション、その他の Unity アセット型を作成するときに Unity によっ</span><span class="sxs-lookup"><span data-stu-id="e79bf-123">This is the folder that holds all assets you import from digital content creation tools such as Maya, Max Cinema 4D or Photoshop, all code you create with Visual Studio or your favorite code editor, and any number of content files that Unity creates as you compose scenes, animations and other Unity asset types in the editor.</span></span>

<span data-ttu-id="e79bf-124">UWP アプリをビルドして展開するために、Unity はプロジェクトを Visual Studio ソリューションとしてエクスポートできます。このソリューションには、必要なすべての資産とコードファイルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-124">To build and deploy UWP apps, Unity can export the project as a Visual Studio solution that will contain all necessary asset and code files.</span></span>

1. <span data-ttu-id="e79bf-125">Unity を開始する</span><span class="sxs-lookup"><span data-stu-id="e79bf-125">Start Unity</span></span>
2. <span data-ttu-id="e79bf-126">**新規** の選択</span><span class="sxs-lookup"><span data-stu-id="e79bf-126">Select **New**</span></span>
3. <span data-ttu-id="e79bf-127">プロジェクト名を入力してください (例: "MixedRealityIntroduction")</span><span class="sxs-lookup"><span data-stu-id="e79bf-127">Enter a project name (e.g. "MixedRealityIntroduction")</span></span>
4. <span data-ttu-id="e79bf-128">プロジェクトを保存する場所を入力してください</span><span class="sxs-lookup"><span data-stu-id="e79bf-128">Enter a location to save your project</span></span>
5. <span data-ttu-id="e79bf-129">**3d** の切り替えが選択されていることを確認する</span><span class="sxs-lookup"><span data-stu-id="e79bf-129">Ensure the **3D** toggle is selected</span></span>
6. <span data-ttu-id="e79bf-130">[ **プロジェクトの作成** ] の選択</span><span class="sxs-lookup"><span data-stu-id="e79bf-130">Select **Create project**</span></span>

<span data-ttu-id="e79bf-131">おめでとう、すべての設定が完了したら、今すぐに mixed reality カスタマイズを開始できます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-131">Congrats, you are all setup to get started with your mixed reality customizations now.</span></span>

## <a name="chapter-2---setup-the-camera"></a><span data-ttu-id="e79bf-132">Chapter 2-カメラの設定</span><span class="sxs-lookup"><span data-stu-id="e79bf-132">Chapter 2 - Setup the Camera</span></span>

>[!VIDEO https://www.youtube.com/embed/eP1ZwB4wSNA]

<span data-ttu-id="e79bf-133">Unity のメインカメラは、ヘッドの追跡とステレオスコピックのレンダリングを処理します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-133">The Unity Main Camera handles head tracking and stereoscopic rendering.</span></span> <span data-ttu-id="e79bf-134">メインカメラには、mixed reality と共に使用するためのいくつかの変更が加えられています。</span><span class="sxs-lookup"><span data-stu-id="e79bf-134">There are a few changes to make to the Main Camera to use it with mixed reality.</span></span>

1. <span data-ttu-id="e79bf-135">ファイル > 新しいシーンの選択</span><span class="sxs-lookup"><span data-stu-id="e79bf-135">Select File > New Scene</span></span>

<span data-ttu-id="e79bf-136">まず、ユーザーの開始位置を ( **X** : 0, **Y** : 0, **Z** : 0) と考えると、アプリのレイアウトが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="e79bf-136">First, it will be easier to lay out your app if you imagine the starting position of the user as ( **X** : 0, **Y** : 0, **Z** : 0).</span></span> <span data-ttu-id="e79bf-137">メインカメラはユーザーのヘッドの移動を追跡しているため、ユーザーの開始位置を設定することによって、メインカメラの開始位置を設定できます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-137">Since the Main Camera is tracking movement of the user's head, the starting position of the user can be set by setting the starting position of the Main Camera.</span></span>

1. <span data-ttu-id="e79bf-138">[ **階層** ] パネルの [ **メインカメラ** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-138">Select **Main Camera** in the **Hierarchy** panel</span></span>
2. <span data-ttu-id="e79bf-139">[ **インスペクター** ] パネルで **変換** コンポーネントを見つけ、 **位置** を ( **x** : 0, **y** : 1, **z** :-10) から ( **x** : 0, **y** : 0, **z** : 0) に変更します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-139">In the **Inspector** panel, find the **Transform** component and change the **Position** from ( **X** : 0, **Y** : 1, **Z** : -10) to ( **X** : 0, **Y** : 0, **Z** : 0)</span></span>

<span data-ttu-id="e79bf-140">次に、カメラの既定の背景はいくつかの点を考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e79bf-140">Second, the default Camera background needs some thought.</span></span>

<span data-ttu-id="e79bf-141">**HoloLens アプリケーションの** 場合、実際の世界は、スカイボックステクスチャではなく、カメラがレンダリングするすべての要素の背後に表示されます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-141">**For HoloLens applications** , the real world should appear behind everything the camera renders, not a Skybox texture.</span></span>

1. <span data-ttu-id="e79bf-142">**メインカメラ** が [ **階層** ] パネルで選択された状態で、[ **インスペクター** ] パネルの [ **カメラ** ] コンポーネントを見つけて、[ **クリアフラグ** ] ボックスを [ **スカイ** ボックス] から [ **純色** ] に変更します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-142">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Clear Flags** dropdown from **Skybox** to **Solid Color** .</span></span>
2. <span data-ttu-id="e79bf-143">**背景** 色ピッカーを選択し、 **RGBA** 値を (0, 0, 0, 0) に変更します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-143">Select the **Background** color picker and change the **RGBA** values to (0, 0, 0, 0)</span></span>

<span data-ttu-id="e79bf-144">**イマーシブヘッドセットを対象とする mixed reality アプリケーション** では、Unity が提供する既定のスカイボックステクスチャを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-144">**For mixed reality applications targeted to immersive headsets** , we can use the default Skybox texture that Unity provides.</span></span>

1. <span data-ttu-id="e79bf-145">**メインカメラ** を [ **階層** ] パネルで選択した状態で、[ **インスペクター** ] パネルの [ **カメラ** ] コンポーネントを見つけて、[ **フラグのクリア** ] ドロップダウンを [ **スカイ** ボックス] にします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-145">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Clear Flags** dropdown to **Skybox** .</span></span>

<span data-ttu-id="e79bf-146">3番目の方法として、Unity の近くのクリッププレーンを考えて、ユーザーがオブジェクトまたはオブジェクトにアプローチしているときに、ユーザーに近いオブジェクトが表示されないようにします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-146">Third, let us consider the near clip plane in Unity and prevent objects from being rendered too close to the users eyes as a user approaches an object or an object approaches a user.</span></span>

<span data-ttu-id="e79bf-147">**Hololens アプリケーション** では、near クリッププレーンを [hololens 推奨](../camera-in-unity.md#clip-planes) 0.85 メーターに設定できます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-147">**For HoloLens applications** , the near clip plane can be set to the [HoloLens recommended](../camera-in-unity.md#clip-planes) 0.85 meters.</span></span>

1. <span data-ttu-id="e79bf-148">**メインカメラ** を [ **階層** ] パネルで選択した状態で、[ **インスペクター** ] パネルの [ **カメラ** ] コンポーネントを見つけて、[ **近距離クリップ平面** ] フィールドを既定の **0.3** から HoloLens 推奨 **0.85** に変更します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-148">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and change the **Near Clip Plane** field from the default **0.3** to the HoloLens recommended **0.85** .</span></span>

<span data-ttu-id="e79bf-149">**イマーシブヘッドセットを対象とする mixed reality アプリケーション** では、Unity が提供する既定の設定を使用できます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-149">**For mixed reality applications targeted to immersive headsets** , we can use the default setting that Unity provides.</span></span>

1. <span data-ttu-id="e79bf-150">**メインカメラ** を [ **階層** ] パネルで選択した状態で、[ **インスペクター** ] パネルの [ **カメラ** ] コンポーネントを見つけて、[ **近くのクリッププレーン** ] フィールドを既定の **0.3** にします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-150">With the **Main Camera** still selected in the **Hierarchy** panel, find the **Camera** component in the **Inspector** panel and keep the **Near Clip Plane** field to the default **0.3** .</span></span>

<span data-ttu-id="e79bf-151">最後に、ここまでの進行状況を保存しておきます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-151">Finally, let us save our progress so far.</span></span> <span data-ttu-id="e79bf-152">シーンの変更を保存するには、> [名前を付け **てシーンを保存** ] を選択し、シーンに「 **Main** 」という名前を付けて、[ **保存** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-152">To save the scene changes, select **File > Save Scene As** , name the scene **Main** , and select **Save** .</span></span>

## <a name="chapter-3---setup-the-project-settings"></a><span data-ttu-id="e79bf-153">Chapter 3-プロジェクト設定のセットアップ</span><span class="sxs-lookup"><span data-stu-id="e79bf-153">Chapter 3 - Setup the Project Settings</span></span>

>[!VIDEO https://www.youtube.com/embed/ItRoiXccC0g]

<span data-ttu-id="e79bf-154">この章では、開発用に Windows Holographic SDK を対象とするのに役立つ Unity プロジェクト設定をいくつか設定します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-154">In this chapter, we will set some Unity project settings that help us target the Windows Holographic SDK for development.</span></span> <span data-ttu-id="e79bf-155">また、アプリケーションの品質設定をいくつか設定します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-155">We will also set some quality settings for our application.</span></span> <span data-ttu-id="e79bf-156">最後に、ビルドターゲットがユニバーサル Windows プラットフォームに設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-156">Finally, we will ensure our build targets are set to Universal Windows Platform.</span></span>

### <a name="unity-performance-and-quality-settings"></a><span data-ttu-id="e79bf-157">Unity のパフォーマンスと品質の設定</span><span class="sxs-lookup"><span data-stu-id="e79bf-157">Unity performance and quality settings</span></span>

<span data-ttu-id="e79bf-158">**HoloLens の Unity 品質設定**</span><span class="sxs-lookup"><span data-stu-id="e79bf-158">**Unity quality settings for HoloLens**</span></span>

![HoloLens の Unity 品質設定](images/qualitysettings.png)

<span data-ttu-id="e79bf-160">HoloLens で高フレームレートを維持することは非常に重要であるため、品質設定をチューニングしてパフォーマンスを最速にすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-160">Since maintaining high framerate on HoloLens is so important, we want the quality settings tuned for fastest performance.</span></span> <span data-ttu-id="e79bf-161">詳細については、「 [Unity のパフォーマンスに関する推奨事項](../performance-recommendations-for-unity.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e79bf-161">For more detailed performance information, [Performance recommendations for Unity](../performance-recommendations-for-unity.md).</span></span>

1. <span data-ttu-id="e79bf-162">[ **プロジェクト設定の編集 > の > 品質** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-162">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="e79bf-163">**ユニバーサル Windows プラットフォーム** ロゴの下にある **ドロップダウン** を選択し、[ **非常に低い** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-163">Select the **dropdown** under the **Universal Windows Platform** logo and select **Very Low** .</span></span> <span data-ttu-id="e79bf-164">ユニバーサル Windows プラットフォーム列のボックスと **非常に少ない** 行が緑色になっている場合は、設定が正しく適用されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="e79bf-164">You'll know the setting is applied correctly when the box in the Universal Windows Platform column and **Very Low** row is green.</span></span>

<span data-ttu-id="e79bf-165">**Occluded を対象とする mixed reality アプリケーションで** は、品質設定を既定値のままにすることができます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-165">**For mixed reality applications targeted to occluded displays** , you can leave the quality settings to its default values.</span></span>

### <a name="target-windows-10-sdk"></a><span data-ttu-id="e79bf-166">ターゲット Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="e79bf-166">Target Windows 10 SDK</span></span>

<span data-ttu-id="e79bf-167">**ターゲット Windows Holographic SDK**</span><span class="sxs-lookup"><span data-stu-id="e79bf-167">**Target Windows Holographic SDK**</span></span>

![ターゲット Windows Holographic SDK](../images/xrsettings.png)

<span data-ttu-id="e79bf-169">エクスポートしようとしているアプリが2D ビューではなく [イマーシブビュー](../../../design/app-views.md) を作成する必要があることを Unity に知らせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e79bf-169">We need to let Unity know that the app we are trying to export should create an [immersive view](../../../design/app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="e79bf-170">これを行うには、Windows 10 SDK を対象とする Unity で仮想現実のサポートを有効にします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-170">We do this by enabling Virtual Reality support on Unity targeting the Windows 10 SDK.</span></span>

1. <span data-ttu-id="e79bf-171">[ **Edit > Project Settings > Player** ] にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-171">Go to **Edit > Project Settings > Player** .</span></span>
2. <span data-ttu-id="e79bf-172">[プレーヤー設定] の [ **インスペクター] パネル** で、[ **ユニバーサル Windows プラットフォーム** ] アイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-172">In the **Inspector Panel** for Player Settings, select the **Universal Windows Platform** icon.</span></span>
3. <span data-ttu-id="e79bf-173">**[XR Settings]\(XR 設定\)** グループを展開します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-173">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="e79bf-174">**[Rendering]\(レンダリング\)** セクションで、 **[Virtual Reality Supported]\(バーチャル リアリティ サポート\)** チェック ボックスをオンにして、新しい **バーチャル リアリティ SDK** の一覧を追加します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-174">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="e79bf-175">**[Windows Mixed Reality]** が一覧に表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-175">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="e79bf-176">されていない場合は、一覧の下部にある **[+]** ボタンを選択し、 **[Windows Mixed Reality]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-176">If not, select the **+** button at the bottom of the list and choose **Windows Mixed Reality** .</span></span>

>[!NOTE]
><span data-ttu-id="e79bf-177">**ユニバーサル Windows プラットフォーム** アイコンが表示されない場合は、インストール時にユニバーサル Windows プラットフォームビルドサポートが選択されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e79bf-177">If you do not see the **Universal Windows Platform** icon, double check to make sure you selected Universal Windows Platform Build Support during installation.</span></span> <span data-ttu-id="e79bf-178">していない場合は、適切な Windows インストールを使用して、Unity を再インストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e79bf-178">If not, you may need to reinstall Unity with the correct Windows installation.</span></span>

<span data-ttu-id="e79bf-179">適用されたすべてのプロジェクト設定を取得するためのすばらしいジョブ。</span><span class="sxs-lookup"><span data-stu-id="e79bf-179">Awesome job on getting all the project settings applied.</span></span> <span data-ttu-id="e79bf-180">次に、ホログラムを追加してみましょう。</span><span class="sxs-lookup"><span data-stu-id="e79bf-180">Next, let us add a hologram!</span></span>

## <a name="chapter-4---create-a-cube"></a><span data-ttu-id="e79bf-181">Chapter 4-キューブの作成</span><span class="sxs-lookup"><span data-stu-id="e79bf-181">Chapter 4 - Create a cube</span></span>

>[!VIDEO https://www.youtube.com/embed/qKcK1Yuj-HQ]

<span data-ttu-id="e79bf-182">Unity プロジェクトでのキューブの作成は、Unity で他のオブジェクトを作成するのと同じです。</span><span class="sxs-lookup"><span data-stu-id="e79bf-182">Creating a cube in your Unity project is just like creating any other object in Unity.</span></span> <span data-ttu-id="e79bf-183">Unity の座標系は現実世界にマップされているため、ユーザーの前にキューブを配置するのは簡単です。 Unity の1つのメーターは実際の世界では約1メートルです。</span><span class="sxs-lookup"><span data-stu-id="e79bf-183">Placing a cube in front of the user is easy because Unity's coordinate system is mapped to the real world - where one meter in Unity is approximately one meter in the real world.</span></span>

1. <span data-ttu-id="e79bf-184">**階層** パネルの左上隅にある [ **作成** ] ドロップダウンを選択し、[ **3d オブジェクト > キューブ** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-184">In the top left corner of the **Hierarchy** panel, select the **Create** dropdown and choose **3D Object > Cube** .</span></span>
2. <span data-ttu-id="e79bf-185">[ **階層** ] パネルで、新しく作成した **キューブ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-185">Select the newly created **Cube** in the **Hierarchy** panel</span></span>
3. <span data-ttu-id="e79bf-186">**インスペクター** で **変換** コンポーネントを検索し、 **位置** を ( **X** : 0、 **Y** : 0、 **Z** : 2) に変更します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-186">In the **Inspector** find the **Transform** component and change **Position** to ( **X** : 0, **Y** : 0, **Z** : 2).</span></span> <span data-ttu-id="e79bf-187">*これにより、ユーザーの開始位置の前にキューブ2のメーターが配置されます。*</span><span class="sxs-lookup"><span data-stu-id="e79bf-187">*This positions the cube 2 meters in front of the user's starting position.*</span></span>
4. <span data-ttu-id="e79bf-188">**変換** コンポーネントで、 **ローテーション** を ( **x** :45、 **y** :45、 **z** :45) に変更し、 **スケール** を ( **x** : 0.25、 **y** : 0.25、 **z** : 0.25) に変更します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-188">In the **Transform** component, change **Rotation** to ( **X** : 45, **Y** : 45, **Z** : 45) and change **Scale** to ( **X** : 0.25, **Y** : 0.25, **Z** : 0.25).</span></span> <span data-ttu-id="e79bf-189">*これにより、キューブが0.25 メートルにスケールされます。*</span><span class="sxs-lookup"><span data-stu-id="e79bf-189">*This scales the cube to 0.25 meters.*</span></span>
5. <span data-ttu-id="e79bf-190">シーンの変更を保存するには、[ **ファイル > [シーンの保存** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-190">To save the scene changes, select **File > Save Scene** .</span></span>

## <a name="chapter-5---verify-on-device-from-unity-editor"></a><span data-ttu-id="e79bf-191">章 5-Unity エディターからデバイスを確認する</span><span class="sxs-lookup"><span data-stu-id="e79bf-191">Chapter 5 - Verify on device from Unity editor</span></span>

>[!VIDEO https://www.youtube.com/embed/vmCfiIdRb6Q]

<span data-ttu-id="e79bf-192">キューブを作成したので、デバイスのクイックチェックを実行します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-192">Now that we have created our cube, it is time to do a quick check in device.</span></span> <span data-ttu-id="e79bf-193">これは、Unity エディター内から直接行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-193">You can do this directly from within the Unity editor.</span></span>

### <a name="initial-setup"></a><span data-ttu-id="e79bf-194">初期セットアップ</span><span class="sxs-lookup"><span data-stu-id="e79bf-194">Initial setup</span></span>

1. <span data-ttu-id="e79bf-195">開発用 PC の Unity で、[ **ファイル > ビルドの設定** ] ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-195">On your development PC, in Unity, open **File > Build Settings** window.</span></span>
2. <span data-ttu-id="e79bf-196">**プラットフォーム** を **ユニバーサル Windows プラットフォーム** に変更し、[ **プラットフォームの切り替え** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-196">Change **Platform** to **Universal Windows Platform** and click **Switch Platform**</span></span>

### <a name="for-hololens-use-unity-remoting"></a><span data-ttu-id="e79bf-197">HoloLens で Unity リモート処理を使用する</span><span class="sxs-lookup"><span data-stu-id="e79bf-197">For HoloLens use Unity Remoting</span></span>

1. <span data-ttu-id="e79bf-198">HoloLens で、Windows ストアから入手できる [Holographic リモート処理プレーヤー](../../platform-capabilities-and-apis/holographic-remoting-player.md)をインストールして実行します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-198">On your HoloLens, install and run the [Holographic Remoting Player](../../platform-capabilities-and-apis/holographic-remoting-player.md), available from the Windows Store.</span></span> <span data-ttu-id="e79bf-199">デバイスでアプリケーションを起動すると、待機状態になり、デバイスの IP アドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-199">Launch the application on the device, and it will enter a waiting state and show the IP address of the device.</span></span> <span data-ttu-id="e79bf-200">IP を書き留めます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-200">Note down the IP.</span></span>
2. <span data-ttu-id="e79bf-201">**ウィンドウ > XR > Holographic エミュレーション]** を開きます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-201">Open **Window > XR > Holographic Emulation** .</span></span>
3. <span data-ttu-id="e79bf-202">[ **エミュレーションモード** ] を **[なし** ] から [リモート] から [ **デバイス** ] に変更します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-202">Change **Emulation Mode** from **None** to **Remote to Device** .</span></span>
4. <span data-ttu-id="e79bf-203">[ **リモートコンピューター** ] に、前にメモした HOLOLENS の IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-203">In **Remote Machine** , enter the IP address of your HoloLens noted earlier.</span></span>
5. <span data-ttu-id="e79bf-204">**[Connect]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-204">Click **Connect** .</span></span>
6. <span data-ttu-id="e79bf-205">接続の **状態** が緑色に変わっ **ていること** を確認します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-205">Ensure the **Connection Status** changes to green **Connected** .</span></span>
7. <span data-ttu-id="e79bf-206">これで、Unity エディターで [ **再生** ] をクリックできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e79bf-206">Now you can now click **Play** in the Unity editor.</span></span>

<span data-ttu-id="e79bf-207">これで、デバイスとエディターでキューブを表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e79bf-207">You will now be able to see the cube in device and in the editor.</span></span> <span data-ttu-id="e79bf-208">エディターでアプリを実行するのと同じように、一時停止、検査、およびデバッグを行うことができます。これは、アプリケーションをエディターで実行するのと同じです。ただし、これは基本的には、ホストコンピューターとデバイス間のネットワーク間で送受信されるビデオ、オーディオ、デバイスの入力を使用します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-208">You can pause, inspect objects, and debug just like you are running an app in the editor, because that's essentially what's happening, but with video, audio, and device input transmitted back and forth across the network between the host machine and the device.</span></span>

### <a name="for-other-mixed-reality-supported-headsets"></a><span data-ttu-id="e79bf-209">その他の mixed reality がサポートするヘッドセットの場合</span><span class="sxs-lookup"><span data-stu-id="e79bf-209">For other mixed reality supported headsets</span></span>

1. <span data-ttu-id="e79bf-210">USB ケーブルと HDMI またはディスプレイポートケーブルを使用して、ヘッドセットを開発用 PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-210">Connect the headset to your development PC using the USB cable and the HDMI or display port cable.</span></span>
2. <span data-ttu-id="e79bf-211">**Mixed Reality ポータル** を起動し、最初の実行エクスペリエンスを完了していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-211">Launch the **Mixed Reality Portal** and ensure you have completed the first run experience.</span></span>
3. <span data-ttu-id="e79bf-212">Unity から、再生ボタンを押すことができます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-212">From Unity, you can now press the Play button.</span></span>

<span data-ttu-id="e79bf-213">これで、混合現実のヘッドセットとエディターでキューブのレンダリングを確認できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e79bf-213">You will now be able to see the cube rendering in your mixed reality headset and in the editor.</span></span>

## <a name="chapter-6---build-and-deploy-to-device-from-visual-studio"></a><span data-ttu-id="e79bf-214">第6章-Visual Studio からデバイスへのビルドと配置</span><span class="sxs-lookup"><span data-stu-id="e79bf-214">Chapter 6 - Build and deploy to device from Visual Studio</span></span>

>[!VIDEO https://www.youtube.com/embed/USSu8yHUdbk]

<span data-ttu-id="e79bf-215">これで、プロジェクトを Visual Studio にコンパイルし、ターゲットデバイスにデプロイする準備ができました。</span><span class="sxs-lookup"><span data-stu-id="e79bf-215">We are now ready to compile our project to Visual Studio and deploy to our target device.</span></span>

### <a name="export-to-the-visual-studio-solution"></a><span data-ttu-id="e79bf-216">Visual Studio ソリューションへのエクスポート</span><span class="sxs-lookup"><span data-stu-id="e79bf-216">Export to the Visual Studio solution</span></span>

1. <span data-ttu-id="e79bf-217">[ **ビルドの設定] ウィンドウ > ファイル** を開きます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-217">Open **File > Build Settings** window.</span></span>
1. <span data-ttu-id="e79bf-218">シーンを追加するには、[開いている **シーンの追加** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-218">Click **Add Open Scenes** to add the scene.</span></span>
1. <span data-ttu-id="e79bf-219">[ **プラットフォーム** ] を [ **ユニバーサル Windows プラットフォーム** に変更し、[ **プラットフォームの切り替え** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-219">Change **Platform** to **Universal Windows Platform** and click **Switch Platform** .</span></span>
1. <span data-ttu-id="e79bf-220">**ユニバーサル Windows プラットフォーム** 設定で、 **SDK** が **Universal 10** であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-220">In **Universal Windows Platform** settings, ensure **SDK** is **Universal 10** .</span></span>
1. <span data-ttu-id="e79bf-221">ターゲットデバイスの場合は、occluded の **任意のデバイス** に表示するか、または **HoloLens** に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-221">For Target device, leave to **Any Device** for occluded displays or switch to **HoloLens** .</span></span>
1. <span data-ttu-id="e79bf-222">**UWP ビルドの種類** は **D3D** である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e79bf-222">**UWP Build Type** should be **D3D** .</span></span>
1. <span data-ttu-id="e79bf-223">**UWP SDK** は、 **インストールされている最新** の状態のままにすることができます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-223">**UWP SDK** could be left at **Latest installed** .</span></span>
1. <span data-ttu-id="e79bf-224">[ **ビルド** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-224">Click **Build** .</span></span>
1. <span data-ttu-id="e79bf-225">エクスプローラーで、[ **新しいフォルダー** ] をクリックし、フォルダーに **「App」** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-225">In the file explorer, click **New Folder** and name the folder **"App"** .</span></span>
1. <span data-ttu-id="e79bf-226">**アプリ** フォルダーを選択した状態で、[ **フォルダーの選択** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-226">With the **App** folder selected, click the **Select Folder** button.</span></span>
1. <span data-ttu-id="e79bf-227">Unity のビルドが完了すると、Windows エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-227">When Unity is done building, a Windows File Explorer window will appear.</span></span>
1. <span data-ttu-id="e79bf-228">エクスプローラーで **アプリ** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="e79bf-228">Open the **App** folder in file explorer.</span></span>
1. <span data-ttu-id="e79bf-229">生成された Visual Studio ソリューションを開きます (この例では MixedRealityIntroduction)。</span><span class="sxs-lookup"><span data-stu-id="e79bf-229">Open the generated Visual Studio solution (MixedRealityIntroduction.sln in this example)</span></span>

### <a name="compile-the-visual-studio-solution"></a><span data-ttu-id="e79bf-230">Visual Studio ソリューションをコンパイルする</span><span class="sxs-lookup"><span data-stu-id="e79bf-230">Compile the Visual Studio solution</span></span>

<span data-ttu-id="e79bf-231">最後に、エクスポートされた Visual Studio ソリューションをコンパイルしてデプロイし、デバイスで試します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-231">Finally, we will compile the exported Visual Studio solution, deploy it, and try it out on the device.</span></span>

1. <span data-ttu-id="e79bf-232">Visual Studio の上部のツールバーを使用して、ターゲットを **デバッグ** から **リリース** に変更し、 **ARM** から **X86** に変更します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-232">Using the top toolbar in Visual Studio, change the target from **Debug** to **Release** and from **ARM** to **X86** .</span></span>

<span data-ttu-id="e79bf-233">この手順は、デバイスとエミュレーターの間の配置で異なります。</span><span class="sxs-lookup"><span data-stu-id="e79bf-233">The instructions differ for deploying to a device versus the emulator.</span></span> <span data-ttu-id="e79bf-234">セットアップに一致する指示に従います。</span><span class="sxs-lookup"><span data-stu-id="e79bf-234">Follow the instructions that match your setup.</span></span>

### <a name="deploy-to-mixed-reality-device-over-wi-fi"></a><span data-ttu-id="e79bf-235">Wi-fi 経由で mixed reality デバイスに展開する</span><span class="sxs-lookup"><span data-stu-id="e79bf-235">Deploy to mixed reality device over Wi-Fi</span></span>

1. <span data-ttu-id="e79bf-236">[ **ローカルコンピューター** ] ボタンの横にある矢印をクリックし、[配置ターゲット] を [ **リモートコンピューター** ] に変更します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-236">Click on the arrow next to the **Local Machine** button, and change the deployment target to **Remote Machine** .</span></span>
2. <span data-ttu-id="e79bf-237">Mixed reality デバイスの IP アドレスを入力し、HoloLens と **Windows** で他のデバイスの **認証モード** を Universal (暗号化されていないプロトコル) に変更します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-237">Enter the IP address of your mixed reality device and change **Authentication Mode** to Universal (Unencrypted Protocol) for HoloLens and **Windows** for other devices.</span></span>
3. <span data-ttu-id="e79bf-238">[ **デバッグ > デバッグなしで開始** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-238">Click **Debug > Start without debugging** .</span></span>

<span data-ttu-id="e79bf-239">**HoloLens の** 場合、初めてデバイスをデプロイする場合は、 [Visual Studio を使用して](../../platform-capabilities-and-apis/using-visual-studio.md)ペアリングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e79bf-239">**For HoloLens** , If this is the first time deploying to your device, you will need to pair [using Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md).</span></span>

### <a name="deploy-to-mixed-reality-device-over-usb"></a><span data-ttu-id="e79bf-240">USB 経由で mixed reality デバイスに展開する</span><span class="sxs-lookup"><span data-stu-id="e79bf-240">Deploy to mixed reality device over USB</span></span>

<span data-ttu-id="e79bf-241">デバイスが USB ケーブル経由で接続されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-241">Ensure you device is plugged in via the USB cable.</span></span>

1. <span data-ttu-id="e79bf-242">**HoloLens の** 場合は、[ **ローカルコンピューター** ] ボタンの横にある矢印をクリックし、展開ターゲットを [ **デバイス** ] に変更します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-242">**For HoloLens** , click on the arrow next to the **Local Machine** button, and change the deployment target to **Device** .</span></span>
2. <span data-ttu-id="e79bf-243">**PC に接続されている occluded デバイスを対象に** するには、設定をローカルコンピューターに保持します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-243">**For targeting occluded devices attached to your PC** , keep the setting to Local Machine.</span></span> <span data-ttu-id="e79bf-244">**Mixed Reality ポータル** が実行されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-244">Ensure you have the **Mixed Reality Portal** running.</span></span>
3. <span data-ttu-id="e79bf-245">[ **デバッグ > デバッグなしで開始** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-245">Click **Debug > Start without debugging** .</span></span>

### <a name="deploy-to-emulator"></a><span data-ttu-id="e79bf-246">Emulator に配置</span><span class="sxs-lookup"><span data-stu-id="e79bf-246">Deploy to Emulator</span></span>

1. <span data-ttu-id="e79bf-247">**デバイス** ボタンの横にある矢印をクリックし、ドロップダウンから [ **HoloLens Emulator** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-247">Click on the arrow next to the **Device** button, and from drop down select **HoloLens Emulator** .</span></span>
2. <span data-ttu-id="e79bf-248">[ **デバッグ > デバッグなしで開始** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e79bf-248">Click **Debug > Start without debugging** .</span></span>

### <a name="try-out-your-app"></a><span data-ttu-id="e79bf-249">アプリを試してみる</span><span class="sxs-lookup"><span data-stu-id="e79bf-249">Try out your app</span></span>

<span data-ttu-id="e79bf-250">アプリがデプロイされたので、キューブ全体を移動して、その前に世界中の状態が維持されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e79bf-250">Now that your app is deployed, try moving all around the cube and observe that it stays in the world in front of you.</span></span>

## <a name="see-also"></a><span data-ttu-id="e79bf-251">関連項目</span><span class="sxs-lookup"><span data-stu-id="e79bf-251">See also</span></span>

* [<span data-ttu-id="e79bf-252">Unity 開発の概要</span><span class="sxs-lookup"><span data-stu-id="e79bf-252">Unity development overview</span></span>](../unity-development-overview.md)
* [<span data-ttu-id="e79bf-253">Unity と Visual Studio を使用するためのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="e79bf-253">Best practices for working with Unity and Visual Studio</span></span>](../best-practices-for-working-with-unity-and-visual-studio.md)
* [<span data-ttu-id="e79bf-254">MR の基本 101</span><span class="sxs-lookup"><span data-stu-id="e79bf-254">MR Basics 101</span></span>](holograms-101.md)
* [<span data-ttu-id="e79bf-255">MR の基本 101E</span><span class="sxs-lookup"><span data-stu-id="e79bf-255">MR Basics 101E</span></span>](holograms-101e.md)
