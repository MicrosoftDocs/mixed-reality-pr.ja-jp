---
title: MR 空間 230 - 空間マッピング
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、空間マッピングの概念の詳細を確認してください。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、academy、チュートリアル、空間マッピング、surface 再構築、メッシュ、HoloLens、Mixed Reality Academy、unity、mixed reality ヘッドセット、windows Mixed reality ヘッドセット、virtual Reality ヘッドセット、Windows 10
ms.openlocfilehash: 6b218de239da04190fbf08ff8668fa16009df949
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582933"
---
# <a name="mr-spatial-230-spatial-mapping"></a><span data-ttu-id="e734f-104">MR 空間 230:空間マッピング</span><span class="sxs-lookup"><span data-stu-id="e734f-104">MR Spatial 230: Spatial mapping</span></span>

>[!NOTE]
><span data-ttu-id="e734f-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="e734f-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="e734f-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="e734f-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="e734f-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。</span><span class="sxs-lookup"><span data-stu-id="e734f-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="e734f-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="e734f-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="e734f-109">HoloLens 2 向けには、[新しいチュートリアル シリーズ](./mr-learning-base-01.md)が投稿されています。</span><span class="sxs-lookup"><span data-stu-id="e734f-109">[A new series of tutorials](./mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="e734f-110">[空間マッピング](../../../design/spatial-mapping.md) は、環境に関するホログラムを教えることによって、現実世界と仮想世界を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="e734f-110">[Spatial mapping](../../../design/spatial-mapping.md) combines the real world and virtual world together by teaching holograms about the environment.</span></span> <span data-ttu-id="e734f-111">MR 空間 230 (Project Planetarium) では、次の方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="e734f-111">In MR Spatial 230 (Project Planetarium) we'll learn how to:</span></span>

* <span data-ttu-id="e734f-112">環境をスキャンし、HoloLens から開発用コンピューターにデータを転送します。</span><span class="sxs-lookup"><span data-stu-id="e734f-112">Scan the environment and transfer data from the HoloLens to your development machine.</span></span>
* <span data-ttu-id="e734f-113">シェーダーを調査し、それらを使用してスペースを視覚化する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="e734f-113">Explore shaders and learn how to use them for visualizing your space.</span></span>
* <span data-ttu-id="e734f-114">メッシュ処理を使用して、ルームメッシュを単純な平面に分割します。</span><span class="sxs-lookup"><span data-stu-id="e734f-114">Break down the room mesh into simple planes using mesh processing.</span></span>
* <span data-ttu-id="e734f-115">[MR の基本 101](../../../develop/unity/tutorials/holograms-101.md)で学習した配置手法を超えて、その環境にホログラムを配置できる場所についてのフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="e734f-115">Go beyond the placement techniques we learned in [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), and provide feedback about where a hologram can be placed in the environment.</span></span>
* <span data-ttu-id="e734f-116">遮蔽効果を調べると、ホログラムが実際のオブジェクトの背後にある場合でも、x 光線による視覚エフェクトを見ることができます。</span><span class="sxs-lookup"><span data-stu-id="e734f-116">Explore occlusion effects, so when your hologram is behind a real-world object, you can still see it with x-ray vision!</span></span>

>[!VIDEO https://www.youtube.com/embed/NSNYRkUX6Mw]

## <a name="device-support"></a><span data-ttu-id="e734f-117">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="e734f-117">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="e734f-118">コース</span><span class="sxs-lookup"><span data-stu-id="e734f-118">Course</span></span></th><th style="width:150px"> <span data-ttu-id="e734f-119"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="e734f-119"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="e734f-120"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="e734f-120"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="e734f-121">MR 空間 230:空間マッピング</span><span class="sxs-lookup"><span data-stu-id="e734f-121">MR Spatial 230: Spatial mapping</span></span></td><td style="text-align: center;"> <span data-ttu-id="e734f-122">✔️</span><span class="sxs-lookup"><span data-stu-id="e734f-122">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="e734f-123">開始する前に</span><span class="sxs-lookup"><span data-stu-id="e734f-123">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="e734f-124">前提条件</span><span class="sxs-lookup"><span data-stu-id="e734f-124">Prerequisites</span></span>

* <span data-ttu-id="e734f-125">適切な [ツールがインストール](../../../develop/install-the-tools.md)された WINDOWS 10 PC。</span><span class="sxs-lookup"><span data-stu-id="e734f-125">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="e734f-126">基本的な C# プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="e734f-126">Some basic C# programming ability.</span></span>
* <span data-ttu-id="e734f-127">[MR の基本 101](../../../develop/unity/tutorials/holograms-101.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="e734f-127">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="e734f-128">[開発用に構成され](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)た HoloLens デバイス。</span><span class="sxs-lookup"><span data-stu-id="e734f-128">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="e734f-129">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="e734f-129">Project files</span></span>

* <span data-ttu-id="e734f-130">プロジェクトに必要な [ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="e734f-130">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-230-SpatialMapping.zip) required by the project.</span></span> <span data-ttu-id="e734f-131">Unity 2017.2 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="e734f-131">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="e734f-132">引き続き Unity 5.6 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="e734f-132">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-230.zip).</span></span>
  * <span data-ttu-id="e734f-133">引き続き Unity 5.5 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="e734f-133">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-230.zip).</span></span>
  * <span data-ttu-id="e734f-134">引き続き Unity 5.4 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="e734f-134">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-230.zip).</span></span>
* <span data-ttu-id="e734f-135">ファイルをデスクトップまたはその他の簡単な場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="e734f-135">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="e734f-136">ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping)ます。</span><span class="sxs-lookup"><span data-stu-id="e734f-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-230-SpatialMapping).</span></span>

### <a name="notes"></a><span data-ttu-id="e734f-137">Notes</span><span class="sxs-lookup"><span data-stu-id="e734f-137">Notes</span></span>

* <span data-ttu-id="e734f-138">コード内のブレークポイントにヒットするには、Visual Studio の [マイコードのみの有効化] を無効 (*オフ*> >) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e734f-138">"Enable Just My Code" in Visual Studio needs to be disabled (*unchecked*) under Tools > Options > Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="e734f-139">Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="e734f-139">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/y2Y4LhK6TEM]

* <span data-ttu-id="e734f-140">**Unity** を起動します。</span><span class="sxs-lookup"><span data-stu-id="e734f-140">Start **Unity**.</span></span>
* <span data-ttu-id="e734f-141">[ **新規** ] を選択して、新しいプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="e734f-141">Select **New** to create a new project.</span></span>
* <span data-ttu-id="e734f-142">プロジェクトに **Planetarium** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e734f-142">Name the project **Planetarium**.</span></span>
* <span data-ttu-id="e734f-143">**3d** の設定が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e734f-143">Verify that the **3D** setting is selected.</span></span>
* <span data-ttu-id="e734f-144">[ **プロジェクトの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-144">Click **Create Project**.</span></span>
* <span data-ttu-id="e734f-145">Unity が起動したら、[ **Edit > Project Settings > Player**] を開きます。</span><span class="sxs-lookup"><span data-stu-id="e734f-145">Once Unity launches, go to **Edit > Project Settings > Player**.</span></span>
* <span data-ttu-id="e734f-146">[ **インスペクター** ] パネルで、緑色の **Windows ストア** アイコンを見つけて選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-146">In the **Inspector** panel, find and select the green **Windows Store** icon.</span></span>
* <span data-ttu-id="e734f-147">[ **その他の設定**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="e734f-147">Expand **Other Settings**.</span></span>
* <span data-ttu-id="e734f-148">[ **レンダリング** ] セクションで、[ **Virtual Reality サポート** ] オプションをオンにします。</span><span class="sxs-lookup"><span data-stu-id="e734f-148">In the **Rendering** section, check the **Virtual Reality Supported** option.</span></span>
* <span data-ttu-id="e734f-149">**Virtual Reality sdk** の一覧に [ **Windows Holographic** ] が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e734f-149">Verify that **Windows Holographic** appears in the list of **Virtual Reality SDKs**.</span></span> <span data-ttu-id="e734f-150">表示されていない場合は、 **+** 一覧の下部にあるボタンを選択し、[ **Windows Holographic**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-150">If not, select the **+** button at the bottom of the list and choose **Windows Holographic**.</span></span>
* <span data-ttu-id="e734f-151">[ **発行の設定**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="e734f-151">Expand **Publishing Settings**.</span></span>
* <span data-ttu-id="e734f-152">[ **機能** ] セクションで、次の設定を確認します。</span><span class="sxs-lookup"><span data-stu-id="e734f-152">In the **Capabilities** section, check the following settings:</span></span>
    * <span data-ttu-id="e734f-153">InternetClientServer</span><span class="sxs-lookup"><span data-stu-id="e734f-153">InternetClientServer</span></span>
    * <span data-ttu-id="e734f-154">PrivateNetworkClientServer</span><span class="sxs-lookup"><span data-stu-id="e734f-154">PrivateNetworkClientServer</span></span>
    * <span data-ttu-id="e734f-155">Microphone</span><span class="sxs-lookup"><span data-stu-id="e734f-155">Microphone</span></span>
    * <span data-ttu-id="e734f-156">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="e734f-156">SpatialPerception</span></span>
* <span data-ttu-id="e734f-157">**プロジェクト設定の編集 > > 品質** に進む</span><span class="sxs-lookup"><span data-stu-id="e734f-157">Go to **Edit > Project Settings > Quality**</span></span>
* <span data-ttu-id="e734f-158">[ **インスペクター** ] パネルの [Windows ストア] アイコンで、[既定] 行の下にある黒のドロップダウン矢印を選択し、既定の設定を [ **非常に低い**] に変更します。</span><span class="sxs-lookup"><span data-stu-id="e734f-158">In the **Inspector** panel, under the Windows Store icon, select the black drop-down arrow under the 'Default' row and change the default setting to **Very Low**.</span></span>
* <span data-ttu-id="e734f-159">[アセット] [ **> カスタムパッケージ**] の [パッケージのインポート >] にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="e734f-159">Go to **Assets > Import Package > Custom Package**.</span></span>
* <span data-ttu-id="e734f-160">**..\Holographicacademy-holograms-230-SpatialMapping\Starting** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="e734f-160">Navigate to the **...\HolographicAcademy-Holograms-230-SpatialMapping\Starting** folder.</span></span>
* <span data-ttu-id="e734f-161">**Planetarium unitypackage** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-161">Click on **Planetarium.unitypackage**.</span></span>
* <span data-ttu-id="e734f-162">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-162">Click **Open**.</span></span>
* <span data-ttu-id="e734f-163">[ **Unity パッケージのインポート** ] ウィンドウが表示されたら、[ **インポート** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-163">An **Import Unity Package** window should appear, click on the **Import** button.</span></span>
* <span data-ttu-id="e734f-164">Unity によって、このプロジェクトを完了するために必要なすべての資産がインポートされるのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="e734f-164">Wait for Unity to import all of the assets that we will need to complete this project.</span></span>
* <span data-ttu-id="e734f-165">[ **階層** ] パネルで、 **メインカメラ** を削除します。</span><span class="sxs-lookup"><span data-stu-id="e734f-165">In the **Hierarchy** panel, delete the **Main Camera**.</span></span>
* <span data-ttu-id="e734f-166">[ **プロジェクト** ] パネルの [ **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** ] フォルダーで、 **メインカメラ** オブジェクトを見つけます。</span><span class="sxs-lookup"><span data-stu-id="e734f-166">In the **Project** panel, **HoloToolkit-SpatialMapping-230\Utilities\Prefabs** folder, find the **Main Camera** object.</span></span>
* <span data-ttu-id="e734f-167">**メインカメラ** prefab を [**階層**] パネルにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="e734f-167">Drag and drop the **Main Camera** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="e734f-168">[ **階層** ] パネルで、 **指向性ライト** オブジェクトを削除します。</span><span class="sxs-lookup"><span data-stu-id="e734f-168">In the **Hierarchy** panel, delete the **Directional Light** object.</span></span>
* <span data-ttu-id="e734f-169">[ **プロジェクト** ] パネルの [ **ホログラム** ] フォルダーで、 **Cursor** オブジェクトを探します。</span><span class="sxs-lookup"><span data-stu-id="e734f-169">In the **Project** panel, **Holograms** folder, locate the **Cursor** object.</span></span>
* <span data-ttu-id="e734f-170">**カーソル** をドラッグして **階層** に & ドロップします。</span><span class="sxs-lookup"><span data-stu-id="e734f-170">Drag & drop the **Cursor** prefab into the **Hierarchy**.</span></span>
* <span data-ttu-id="e734f-171">[ **階層** ] パネルで、 **カーソル** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-171">In the **Hierarchy** panel, select the **Cursor** object.</span></span>
* <span data-ttu-id="e734f-172">[ **インスペクター** ] パネルで、[ **レイヤー** ] ドロップダウンをクリックし、[ **レイヤーの編集...**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-172">In the **Inspector** panel, click the **Layer** drop-down and select **Edit Layers...**.</span></span>
* <span data-ttu-id="e734f-173">**ユーザーレイヤー 31** を "**SpatialMapping**" として指定します。</span><span class="sxs-lookup"><span data-stu-id="e734f-173">Name **User Layer 31** as "**SpatialMapping**".</span></span>
* <span data-ttu-id="e734f-174">新しいシーンを保存する: **ファイル > [シーン名を付けて保存...**</span><span class="sxs-lookup"><span data-stu-id="e734f-174">Save the new scene: **File > Save Scene As...**</span></span>
* <span data-ttu-id="e734f-175">[ **新しいフォルダー** ] をクリックし、フォルダーに「 **シーン**」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="e734f-175">Click **New Folder** and name the folder **Scenes**.</span></span>
* <span data-ttu-id="e734f-176">ファイルに "**Planetarium**" という名前を付けて、[ **シーン** ] フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="e734f-176">Name the file "**Planetarium**" and save it in the **Scenes** folder.</span></span>

## <a name="chapter-1---scanning"></a><span data-ttu-id="e734f-177">第1章-スキャン</span><span class="sxs-lookup"><span data-stu-id="e734f-177">Chapter 1 - Scanning</span></span>

>[!VIDEO https://www.youtube.com/embed/888oW51z_cE]

<span data-ttu-id="e734f-178">**目標**</span><span class="sxs-lookup"><span data-stu-id="e734f-178">**Objectives**</span></span>

* <span data-ttu-id="e734f-179">SurfaceObserver とその設定がエクスペリエンスとパフォーマンスに与える影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="e734f-179">Learn about the SurfaceObserver and how its settings impact experience and performance.</span></span>
* <span data-ttu-id="e734f-180">部屋のメッシュを収集するためのルームスキャンエクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e734f-180">Create a room scanning experience to collect the meshes of your room.</span></span>

<span data-ttu-id="e734f-181">**手順**</span><span class="sxs-lookup"><span data-stu-id="e734f-181">**Instructions**</span></span>

* <span data-ttu-id="e734f-182">[ **プロジェクト** ] パネルの **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** フォルダーで、 **SpatialMapping** prefab を見つけます。</span><span class="sxs-lookup"><span data-stu-id="e734f-182">In the **Project** panel **HoloToolkit-SpatialMapping-230\SpatialMapping\Prefabs** folder, find the **SpatialMapping** prefab.</span></span>
* <span data-ttu-id="e734f-183">**SpatialMapping** prefab を [**階層**] パネルにドラッグ & ドロップします。</span><span class="sxs-lookup"><span data-stu-id="e734f-183">Drag & drop the **SpatialMapping** prefab into the **Hierarchy** panel.</span></span>

<span data-ttu-id="e734f-184">**ビルドと配置 (パート 1)**</span><span class="sxs-lookup"><span data-stu-id="e734f-184">**Build and Deploy (part 1)**</span></span>

* <span data-ttu-id="e734f-185">Unity で、[ **ファイル > ビルド設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-185">In Unity, select **File > Build Settings**.</span></span>
* <span data-ttu-id="e734f-186">[ **開い** ているシーンの追加] をクリックして、 **Planetarium** シーンをビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="e734f-186">Click **Add Open Scenes** to add the **Planetarium** scene to the build.</span></span>
* <span data-ttu-id="e734f-187">[**プラットフォーム**] ボックスの一覧の [**ユニバーサル Windows プラットフォーム**] を選択し、[**プラットフォームの切り替え**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-187">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="e734f-188">**SDK** を **Universal 10** に設定し、 **UWP ビルドの種類** を **D3D** に設定します。</span><span class="sxs-lookup"><span data-stu-id="e734f-188">Set **SDK** to **Universal 10** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="e734f-189">**Unity C# プロジェクト** を確認します。</span><span class="sxs-lookup"><span data-stu-id="e734f-189">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="e734f-190">[**ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-190">Click **Build**.</span></span>
* <span data-ttu-id="e734f-191">"App" という名前の **新しいフォルダー** を作成します。</span><span class="sxs-lookup"><span data-stu-id="e734f-191">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="e734f-192">**アプリ** フォルダーをシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-192">Single click the **App** folder.</span></span>
* <span data-ttu-id="e734f-193">**[フォルダーの選択**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-193">Press the **Select Folder** button.</span></span>
* <span data-ttu-id="e734f-194">Unity のビルドが完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e734f-194">When Unity is done building, a File Explorer window will appear.</span></span>
* <span data-ttu-id="e734f-195">**アプリ** フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="e734f-195">Double-click on the **App** folder to open it.</span></span>
* <span data-ttu-id="e734f-196">**Planetarium** をダブルクリックして、Visual Studio でプロジェクトを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="e734f-196">Double-click on **Planetarium.sln** to load the project in Visual Studio.</span></span>
* <span data-ttu-id="e734f-197">Visual Studio で、上部のツールバーを使用して、構成を [ **リリース**] に変更します。</span><span class="sxs-lookup"><span data-stu-id="e734f-197">In Visual Studio, use the top toolbar to change the Configuration to **Release**.</span></span>
* <span data-ttu-id="e734f-198">プラットフォームを **x86** に変更します。</span><span class="sxs-lookup"><span data-stu-id="e734f-198">Change the Platform to **x86**.</span></span>
* <span data-ttu-id="e734f-199">[ローカルコンピューター] の右側にあるドロップダウン矢印をクリックし、[ **リモートコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-199">Click on the drop-down arrow to the right of 'Local Machine', and select **Remote Machine**.</span></span>
* <span data-ttu-id="e734f-200">[アドレス] フィールドに [デバイスの IP アドレス](/hololens/hololens-network#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) を入力し、[認証モード] を [ **ユニバーサル (暗号化** されていないプロトコル)] に変更します。</span><span class="sxs-lookup"><span data-stu-id="e734f-200">Enter [your device's IP address](/hololens/hololens-network#identifying-the-ip-address-of-your-hololens-on-the-wi-fi-network) in the Address field and change Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span>
* <span data-ttu-id="e734f-201">[ **デバッグ]、[デバッグなしで開始] の順にクリック >** 、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e734f-201">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="e734f-202">ビルドと配置の状態については、Visual Studio の [ **出力** ] パネルをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e734f-202">Watch the **Output** panel in Visual Studio for build and deploy status.</span></span>
* <span data-ttu-id="e734f-203">アプリがデプロイされたら、ルームを案内します。</span><span class="sxs-lookup"><span data-stu-id="e734f-203">Once your app has deployed, walk around the room.</span></span> <span data-ttu-id="e734f-204">周囲のサーフェスが黒と白のワイヤーフレームメッシュで覆われていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="e734f-204">You will see the surrounding surfaces covered by black and white wireframe meshes.</span></span>
* <span data-ttu-id="e734f-205">周囲をスキャンします。</span><span class="sxs-lookup"><span data-stu-id="e734f-205">Scan your surroundings.</span></span> <span data-ttu-id="e734f-206">壁、雲、床を見てください。</span><span class="sxs-lookup"><span data-stu-id="e734f-206">Be sure to look at walls, ceilings, and floors.</span></span>

<span data-ttu-id="e734f-207">**ビルドと配置 (パート 2)**</span><span class="sxs-lookup"><span data-stu-id="e734f-207">**Build and Deploy (part 2)**</span></span>

<span data-ttu-id="e734f-208">次に、空間マッピングがパフォーマンスに与える影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="e734f-208">Now let's explore how Spatial Mapping can affect performance.</span></span>

* <span data-ttu-id="e734f-209">Unity で、[ **ウィンドウ > プロファイラー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-209">In Unity, select **Window > Profiler**.</span></span>
* <span data-ttu-id="e734f-210">[ **プロファイラーの追加 > GPU**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-210">Click **Add Profiler > GPU**.</span></span>
* <span data-ttu-id="e734f-211">[**アクティブなプロファイラー <Enter IP> の >**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-211">Click **Active Profiler > <Enter IP>**.</span></span>
* <span data-ttu-id="e734f-212">HoloLens の **IP アドレス** を入力します。</span><span class="sxs-lookup"><span data-stu-id="e734f-212">Enter the **IP address** of your HoloLens.</span></span>
* <span data-ttu-id="e734f-213">**[Connect]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-213">Click **Connect**.</span></span>
* <span data-ttu-id="e734f-214">GPU がフレームをレンダリングするためにかかる時間 (ミリ秒単位) を観察します。</span><span class="sxs-lookup"><span data-stu-id="e734f-214">Observe the number of milliseconds it takes for the GPU to render a frame.</span></span>
* <span data-ttu-id="e734f-215">デバイスでアプリケーションの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="e734f-215">Stop the application from running on the device.</span></span>
* <span data-ttu-id="e734f-216">Visual Studio に戻り、 **SpatialMappingObserver.cs** を開きます。</span><span class="sxs-lookup"><span data-stu-id="e734f-216">Return to Visual Studio and open **SpatialMappingObserver.cs**.</span></span> <span data-ttu-id="e734f-217">これは、Assembly-CSharp (ユニバーサル Windows) プロジェクトの HoloToolkit\SpatialMapping フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="e734f-217">You will find it in the HoloToolkit\SpatialMapping folder of the Assembly-CSharp (Universal Windows) project.</span></span>
* <span data-ttu-id="e734f-218">起動 **()** 関数を見つけ、次のコード行を追加します: **TrianglesPerCubicMeter = 1200;**</span><span class="sxs-lookup"><span data-stu-id="e734f-218">Find the **Awake()** function, and add the following line of code: **TrianglesPerCubicMeter = 1200;**</span></span>
* <span data-ttu-id="e734f-219">プロジェクトをデバイスに再配置してから、 **プロファイラーを再接続** します。</span><span class="sxs-lookup"><span data-stu-id="e734f-219">Re-deploy the project to your device, and then **reconnect the profiler**.</span></span> <span data-ttu-id="e734f-220">フレームをレンダリングするミリ秒数の変化を確認します。</span><span class="sxs-lookup"><span data-stu-id="e734f-220">Observe the change in the number of milliseconds to render a frame.</span></span>
* <span data-ttu-id="e734f-221">デバイスでアプリケーションの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="e734f-221">Stop the application from running on the device.</span></span>

<span data-ttu-id="e734f-222">**Unity での保存と読み込み**</span><span class="sxs-lookup"><span data-stu-id="e734f-222">**Save and load in Unity**</span></span>

<span data-ttu-id="e734f-223">最後に、部屋のメッシュを保存し、Unity に読み込んでみましょう。</span><span class="sxs-lookup"><span data-stu-id="e734f-223">Finally, let's save our room mesh and load it into Unity.</span></span>

* <span data-ttu-id="e734f-224">Visual Studio に戻り、前のセクションで **TrianglesPerCubicMeter** **()** 関数に追加した行を削除します。</span><span class="sxs-lookup"><span data-stu-id="e734f-224">Return to Visual Studio and remove the **TrianglesPerCubicMeter** line that you added in the **Awake()** function during the previous section.</span></span>
* <span data-ttu-id="e734f-225">プロジェクトをデバイスに再デプロイします。</span><span class="sxs-lookup"><span data-stu-id="e734f-225">Redeploy the project to your device.</span></span> <span data-ttu-id="e734f-226">ここでは、3つ **500** の3つのトライアングルメーターで実行されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e734f-226">We should now be running with **500** triangles per cubic meter.</span></span>
* <span data-ttu-id="e734f-227">ブラウザーを開き、HoloLens IPAddress に「」と入力して、 **Windows デバイスポータル** に移動します。</span><span class="sxs-lookup"><span data-stu-id="e734f-227">Open a browser and enter in your HoloLens IPAddress to navigate to the **Windows Device Portal**.</span></span>
* <span data-ttu-id="e734f-228">左側のパネルで [ **3D 表示** ] オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-228">Select the **3D View** option in the left panel.</span></span>
* <span data-ttu-id="e734f-229">[ **Surface 再構築** ] で、[ **更新** ] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-229">Under **Surface reconstruction** select the **Update** button.</span></span>
* <span data-ttu-id="e734f-230">HoloLens でスキャンした領域が表示ウィンドウに表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e734f-230">Watch as the areas that you have scanned on your HoloLens appear in the display window.</span></span>
* <span data-ttu-id="e734f-231">部屋のスキャンを保存するには、[ **保存** ] ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="e734f-231">To save your room scan, press the **Save** button.</span></span>
* <span data-ttu-id="e734f-232">**ダウンロード** フォルダーを開いて、保存されているルームモデル **srmesh. .obj** を見つけます。</span><span class="sxs-lookup"><span data-stu-id="e734f-232">Open your **Downloads** folder to find the saved room model **SRMesh.obj**.</span></span>
* <span data-ttu-id="e734f-233">Unity プロジェクトの **Assets** フォルダーに **srmesh. .obj** をコピーします。</span><span class="sxs-lookup"><span data-stu-id="e734f-233">Copy **SRMesh.obj** to the **Assets** folder of your Unity project.</span></span>
* <span data-ttu-id="e734f-234">Unity で、[**階層**] パネルの [ **SpatialMapping** ] オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-234">In Unity, select the **SpatialMapping** object in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="e734f-235">**オブジェクトサーフェイスのオブザーバー (スクリプト)** コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="e734f-235">Locate the **Object Surface Observer (Script)** component.</span></span>
* <span data-ttu-id="e734f-236">[ **ルームモデル** ] プロパティの右側にある円をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-236">Click the circle to the right of the **Room Model** property.</span></span>
* <span data-ttu-id="e734f-237">**Srmesh** オブジェクトを探して選択し、ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e734f-237">Find and select the **SRMesh** object and then close the window.</span></span>
* <span data-ttu-id="e734f-238">[**インスペクター** ] パネルの [**ルームモデル**] プロパティが [ **srmesh**] に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e734f-238">Verify that the **Room Model** property in the **Inspector** panel is now set to **SRMesh**.</span></span>
* <span data-ttu-id="e734f-239">[ **再生** ] ボタンを押して Unity のプレビューモードに入ります。</span><span class="sxs-lookup"><span data-stu-id="e734f-239">Press the **Play** button to enter Unity's preview mode.</span></span>
* <span data-ttu-id="e734f-240">SpatialMapping コンポーネントは、保存された部屋モデルからメッシュを読み込み、Unity で使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e734f-240">The SpatialMapping component will load the meshes from the saved room model so you can use them in Unity.</span></span>
* <span data-ttu-id="e734f-241">[ **シーン** ] ビューに切り替えて、ワイヤーフレームシェーダーで表示されているすべての部屋モデルを表示します。</span><span class="sxs-lookup"><span data-stu-id="e734f-241">Switch to **Scene** view to see all of your room model displayed with the wireframe shader.</span></span>
* <span data-ttu-id="e734f-242">プレビューモードを終了するには、もう一度 [ **再生** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-242">Press the **Play** button again to exit preview mode.</span></span>

<span data-ttu-id="e734f-243">**注:** Unity で次にプレビューモードに入ると、既定で保存されているルームメッシュが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="e734f-243">**NOTE:** The next time that you enter preview mode in Unity, it will load the saved room mesh by default.</span></span>

## <a name="chapter-2---visualization"></a><span data-ttu-id="e734f-244">第2章-視覚化</span><span class="sxs-lookup"><span data-stu-id="e734f-244">Chapter 2 - Visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/RnkvXl-aXD4]

<span data-ttu-id="e734f-245">**目標**</span><span class="sxs-lookup"><span data-stu-id="e734f-245">**Objectives**</span></span>

* <span data-ttu-id="e734f-246">シェーダーの基本について説明します。</span><span class="sxs-lookup"><span data-stu-id="e734f-246">Learn the basics of shaders.</span></span>
* <span data-ttu-id="e734f-247">周囲を視覚化します。</span><span class="sxs-lookup"><span data-stu-id="e734f-247">Visualize your surroundings.</span></span>

<span data-ttu-id="e734f-248">**手順**</span><span class="sxs-lookup"><span data-stu-id="e734f-248">**Instructions**</span></span>

* <span data-ttu-id="e734f-249">Unity の [ **階層** ] パネルで、 **SpatialMapping** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-249">In Unity's **Hierarchy** panel, select the **SpatialMapping** object.</span></span>
* <span data-ttu-id="e734f-250">[ **インスペクター** ] パネルで、[ **空間マッピングマネージャー (スクリプト)** ] コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="e734f-250">In the **Inspector** panel, find the **Spatial Mapping Manager (Script)** component.</span></span>
* <span data-ttu-id="e734f-251">[ **Surface Material** ] プロパティの右側にある円をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-251">Click the circle to the right of the **Surface Material** property.</span></span>
* <span data-ttu-id="e734f-252">**BlueLinesOnWalls** 素材を検索して選択し、ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e734f-252">Find and select the **BlueLinesOnWalls** material and close the window.</span></span>
* <span data-ttu-id="e734f-253">[ **プロジェクト** パネル **シェーダー** ] フォルダーで、 **BlueLinesOnWalls** をダブルクリックして、Visual Studio でシェーダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="e734f-253">In the **Project** panel **Shaders** folder, double-click on **BlueLinesOnWalls** to open the shader in Visual Studio.</span></span>
* <span data-ttu-id="e734f-254">これは単純なピクセル (頂点からフラグメント) シェーダーで、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="e734f-254">This is a simple pixel (vertex to fragment) shader, which accomplishes the following tasks:</span></span>
    1. <span data-ttu-id="e734f-255">頂点の位置をワールド空間に変換します。</span><span class="sxs-lookup"><span data-stu-id="e734f-255">Converts a vertex's location to world space.</span></span>
    2. <span data-ttu-id="e734f-256">ピクセルが垂直かどうかを判断するために、頂点の法線をチェックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-256">Checks the vertex's normal to determine if a pixel is vertical.</span></span>
    3. <span data-ttu-id="e734f-257">表示するピクセルの色を設定します。</span><span class="sxs-lookup"><span data-stu-id="e734f-257">Sets the color of the pixel for rendering.</span></span>

<span data-ttu-id="e734f-258">**ビルドと配置**</span><span class="sxs-lookup"><span data-stu-id="e734f-258">**Build and Deploy**</span></span>

* <span data-ttu-id="e734f-259">Unity に戻り、[ **Play** ] を押してプレビューモードに入ります。</span><span class="sxs-lookup"><span data-stu-id="e734f-259">Return to Unity and press **Play** to enter preview mode.</span></span>
* <span data-ttu-id="e734f-260">青色の線は、保存されているスキャンデータから自動的に読み込まれる、部屋メッシュのすべての垂直サーフェイスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e734f-260">Blue lines will be rendered on all vertical surfaces of the room mesh (which automatically loaded from our saved scanning data).</span></span>
* <span data-ttu-id="e734f-261">[ **シーン** ] タブに切り替えて、部屋の表示を調整し、Unity でのルームメッシュ全体の表示方法を確認します。</span><span class="sxs-lookup"><span data-stu-id="e734f-261">Switch to the **Scene** tab to adjust your view of the room and see how the entire room mesh appears in Unity.</span></span>
* <span data-ttu-id="e734f-262">[ **プロジェクト** ] パネルで、[ **素材** ] フォルダーを見つけて、 **BlueLinesOnWalls** の素材を選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-262">In the **Project** panel, find the **Materials** folder and select the **BlueLinesOnWalls** material.</span></span>
* <span data-ttu-id="e734f-263">一部のプロパティを変更し、Unity エディターで変更がどのように表示されるかを確認します。</span><span class="sxs-lookup"><span data-stu-id="e734f-263">Modify some properties and see how the changes appear in the Unity editor.</span></span>
    * <span data-ttu-id="e734f-264">[ **インスペクター** ] パネルで、 **LineScale** の値を調整して、線が太くまたは細くなるようにします。</span><span class="sxs-lookup"><span data-stu-id="e734f-264">In the **Inspector** panel, adjust the **LineScale** value to make the lines appear thicker or thinner.</span></span>
    * <span data-ttu-id="e734f-265">[ **インスペクター** ] パネルで、[行 **perメーター** ] の値を調整して、各壁面に表示される線の数を変更します。</span><span class="sxs-lookup"><span data-stu-id="e734f-265">In the **Inspector** panel, adjust the **LinesPerMeter** value to change how many lines appear on each wall.</span></span>
* <span data-ttu-id="e734f-266">[ **再生** ] をもう一度クリックして、プレビューモードを終了します。</span><span class="sxs-lookup"><span data-stu-id="e734f-266">Click **Play** again to exit preview mode.</span></span>
* <span data-ttu-id="e734f-267">HoloLens にビルドして展開し、シェーダーのレンダリングが実際のサーフェイスにどのように表示されるかを観察します。</span><span class="sxs-lookup"><span data-stu-id="e734f-267">Build and deploy to the HoloLens and observe how the shader rendering appears on real surfaces.</span></span>

<span data-ttu-id="e734f-268">Unity は、素材をプレビューするための優れたジョブを行いますが、常にデバイスでのレンダリングをチェックアウトすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e734f-268">Unity does a great job of previewing materials, but it's always a good idea to check-out rendering in the device.</span></span>

## <a name="chapter-3---processing"></a><span data-ttu-id="e734f-269">第3章: 処理</span><span class="sxs-lookup"><span data-stu-id="e734f-269">Chapter 3 - Processing</span></span>

>[!VIDEO https://www.youtube.com/embed/kaUKiNiDxwY]

<span data-ttu-id="e734f-270">**目標**</span><span class="sxs-lookup"><span data-stu-id="e734f-270">**Objectives**</span></span>

* <span data-ttu-id="e734f-271">アプリケーションで使用するために空間マッピングデータを処理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e734f-271">Learn techniques to process spatial mapping data for use in your application.</span></span>
* <span data-ttu-id="e734f-272">空間マッピングデータを分析してプレーンを検索し、三角形を削除します。</span><span class="sxs-lookup"><span data-stu-id="e734f-272">Analyze spatial mapping data to find planes and remove triangles.</span></span>
* <span data-ttu-id="e734f-273">ホログラムの配置に平面を使用します。</span><span class="sxs-lookup"><span data-stu-id="e734f-273">Use planes for hologram placement.</span></span>

<span data-ttu-id="e734f-274">**手順**</span><span class="sxs-lookup"><span data-stu-id="e734f-274">**Instructions**</span></span>

* <span data-ttu-id="e734f-275">Unity の [ **プロジェクト** ] パネルの [ **ホログラム** ] フォルダーで、 **SpatialProcessing** オブジェクトを見つけます。</span><span class="sxs-lookup"><span data-stu-id="e734f-275">In Unity's **Project** panel, **Holograms** folder, find the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="e734f-276">**SpatialProcessing** オブジェクトを [**階層**] パネルにドラッグ & ドロップします。</span><span class="sxs-lookup"><span data-stu-id="e734f-276">Drag & drop the **SpatialProcessing** object into the **Hierarchy** panel.</span></span>

<span data-ttu-id="e734f-277">SpatialProcessing prefab には、空間マッピングデータを処理するためのコンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e734f-277">The SpatialProcessing prefab includes components for processing the spatial mapping data.</span></span> <span data-ttu-id="e734f-278">**SurfaceMeshesToPlanes.cs** は、空間マッピングのデータに基づいてプレーンを検索して生成します。</span><span class="sxs-lookup"><span data-stu-id="e734f-278">**SurfaceMeshesToPlanes.cs** will find and generate planes based on the spatial mapping data.</span></span> <span data-ttu-id="e734f-279">このアプリケーションでは、壁、床、および雲を表す平面を使用します。</span><span class="sxs-lookup"><span data-stu-id="e734f-279">We will use planes in our application to represent walls, floors and ceilings.</span></span> <span data-ttu-id="e734f-280">この事前 fab には、空間マッピングメッシュから頂点を削除できる **RemoveSurfaceVertices.cs** も含まれています。</span><span class="sxs-lookup"><span data-stu-id="e734f-280">This prefab also includes **RemoveSurfaceVertices.cs** which can remove vertices from the spatial mapping mesh.</span></span> <span data-ttu-id="e734f-281">これを使用すると、メッシュに穴を作成したり、不要になった余分な三角形を削除したりできます (プレーンを代わりに使用できるため)。</span><span class="sxs-lookup"><span data-stu-id="e734f-281">This can be used to create holes in the mesh, or to remove excess triangles that are no longer needed (because planes can be used instead).</span></span>

* <span data-ttu-id="e734f-282">Unity の [ **プロジェクト** ] パネルの [ **ホログラム** ] フォルダーで **、[場所] オブジェクトを** 見つけます。</span><span class="sxs-lookup"><span data-stu-id="e734f-282">In Unity's **Project** panel, **Holograms** folder, find the **SpaceCollection** object.</span></span>
* <span data-ttu-id="e734f-283">[移動] オブジェクトを [**階層**] パネルにドラッグアンド **ドロップします**。</span><span class="sxs-lookup"><span data-stu-id="e734f-283">Drag and drop the **SpaceCollection** object into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="e734f-284">[ **階層** ] パネルで、 **SpatialProcessing** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-284">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="e734f-285">[ **インスペクター** ] パネルで、[ **Play Space Manager (スクリプト)** ] コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="e734f-285">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="e734f-286">**PlaySpaceManager.cs** をダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="e734f-286">Double-click on **PlaySpaceManager.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="e734f-287">PlaySpaceManager.cs には、アプリケーション固有のコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e734f-287">PlaySpaceManager.cs contains application-specific code.</span></span> <span data-ttu-id="e734f-288">このスクリプトに機能を追加して、次の動作を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e734f-288">We will add functionality to this script to enable the following behavior:</span></span>

1. <span data-ttu-id="e734f-289">スキャンの制限時間 (10 秒) を超えた後に、空間マッピングデータの収集を停止します。</span><span class="sxs-lookup"><span data-stu-id="e734f-289">Stop collecting spatial mapping data after we exceed the scanning time limit (10 seconds).</span></span>
2. <span data-ttu-id="e734f-290">空間マッピングデータを処理します。</span><span class="sxs-lookup"><span data-stu-id="e734f-290">Process the spatial mapping data:</span></span>
    1. <span data-ttu-id="e734f-291">SurfaceMeshesToPlanes を使用して、ワールドの表現を平面 (壁面、床、雲など) として簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="e734f-291">Use SurfaceMeshesToPlanes to create a simpler representation of the world as planes (walls, floors, ceilings, etc).</span></span>
    2. <span data-ttu-id="e734f-292">平面の境界内にある表面の三角形を削除するには、RemoveSurfaceVertices を使用します。</span><span class="sxs-lookup"><span data-stu-id="e734f-292">Use RemoveSurfaceVertices to remove surface triangles that fall within plane boundaries.</span></span>
3. <span data-ttu-id="e734f-293">世界中にホログラムのコレクションを生成し、ユーザーの近くにある壁と床面に配置します。</span><span class="sxs-lookup"><span data-stu-id="e734f-293">Generate a collection of holograms in the world and place them on wall and floor planes near the user.</span></span>

<span data-ttu-id="e734f-294">PlaySpaceManager.cs でマークされたコーディング演習を完了するか、次のスクリプトを完成したソリューションに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e734f-294">Complete the coding exercises marked in PlaySpaceManager.cs, or replace the script with the finished solution from below:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;

/// <summary>
/// The SurfaceManager class allows applications to scan the environment for a specified amount of time 
/// and then process the Spatial Mapping Mesh (find planes, remove vertices) after that time has expired.
/// </summary>
public class PlaySpaceManager : Singleton<PlaySpaceManager>
{
    [Tooltip("When checked, the SurfaceObserver will stop running after a specified amount of time.")]
    public bool limitScanningByTime = true;

    [Tooltip("How much time (in seconds) that the SurfaceObserver will run after being started; used when 'Limit Scanning By Time' is checked.")]
    public float scanTime = 30.0f;

    [Tooltip("Material to use when rendering Spatial Mapping meshes while the observer is running.")]
    public Material defaultMaterial;

    [Tooltip("Optional Material to use when rendering Spatial Mapping meshes after the observer has been stopped.")]
    public Material secondaryMaterial;

    [Tooltip("Minimum number of floor planes required in order to exit scanning/processing mode.")]
    public uint minimumFloors = 1;

    [Tooltip("Minimum number of wall planes required in order to exit scanning/processing mode.")]
    public uint minimumWalls = 1;

    /// <summary>
    /// Indicates if processing of the surface meshes is complete.
    /// </summary>
    private bool meshesProcessed = false;

    /// <summary>
    /// GameObject initialization.
    /// </summary>
    private void Start()
    {
        // Update surfaceObserver and storedMeshes to use the same material during scanning.
        SpatialMappingManager.Instance.SetSurfaceMaterial(defaultMaterial);

        // Register for the MakePlanesComplete event.
        SurfaceMeshesToPlanes.Instance.MakePlanesComplete += SurfaceMeshesToPlanes_MakePlanesComplete;
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        // Check to see if the spatial mapping data has been processed
        // and if we are limiting how much time the user can spend scanning.
        if (!meshesProcessed && limitScanningByTime)
        {
            // If we have not processed the spatial mapping data
            // and scanning time is limited...

            // Check to see if enough scanning time has passed
            // since starting the observer.
            if (limitScanningByTime && ((Time.time - SpatialMappingManager.Instance.StartTime) < scanTime))
            {
                // If we have a limited scanning time, then we should wait until
                // enough time has passed before processing the mesh.
            }
            else
            {
                // The user should be done scanning their environment,
                // so start processing the spatial mapping data...

                /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

                // 3.a: Check if IsObserverRunning() is true on the
                // SpatialMappingManager.Instance.
                if(SpatialMappingManager.Instance.IsObserverRunning())
                {
                    // 3.a: If running, Stop the observer by calling
                    // StopObserver() on the SpatialMappingManager.Instance.
                    SpatialMappingManager.Instance.StopObserver();
                }

                // 3.a: Call CreatePlanes() to generate planes.
                CreatePlanes();

                // 3.a: Set meshesProcessed to true.
                meshesProcessed = true;
            }
        }
    }

    /// <summary>
    /// Handler for the SurfaceMeshesToPlanes MakePlanesComplete event.
    /// </summary>
    /// <param name="source">Source of the event.</param>
    /// <param name="args">Args for the event.</param>
    private void SurfaceMeshesToPlanes_MakePlanesComplete(object source, System.EventArgs args)
    {
        /* TODO: 3.a DEVELOPER CODING EXERCISE 3.a */

        // Collection of floor and table planes that we can use to set horizontal items on.
        List<GameObject> horizontal = new List<GameObject>();

        // Collection of wall planes that we can use to set vertical items on.
        List<GameObject> vertical = new List<GameObject>();

        // 3.a: Get all floor and table planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'horizontal' list.
        horizontal = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Table | PlaneTypes.Floor);

        // 3.a: Get all wall planes by calling
        // SurfaceMeshesToPlanes.Instance.GetActivePlanes().
        // Assign the result to the 'vertical' list.
        vertical = SurfaceMeshesToPlanes.Instance.GetActivePlanes(PlaneTypes.Wall);

        // Check to see if we have enough horizontal planes (minimumFloors)
        // and vertical planes (minimumWalls), to set holograms on in the world.
        if (horizontal.Count >= minimumFloors && vertical.Count >= minimumWalls)
        {
            // We have enough floors and walls to place our holograms on...

            // 3.a: Let's reduce our triangle count by removing triangles
            // from SpatialMapping meshes that intersect with our active planes.
            // Call RemoveVertices().
            // Pass in all activePlanes found by SurfaceMeshesToPlanes.Instance.
            RemoveVertices(SurfaceMeshesToPlanes.Instance.ActivePlanes);

            // 3.a: We can indicate to the user that scanning is over by
            // changing the material applied to the Spatial Mapping meshes.
            // Call SpatialMappingManager.Instance.SetSurfaceMaterial().
            // Pass in the secondaryMaterial.
            SpatialMappingManager.Instance.SetSurfaceMaterial(secondaryMaterial);

            // 3.a: We are all done processing the mesh, so we can now
            // initialize a collection of Placeable holograms in the world
            // and use horizontal/vertical planes to set their starting positions.
            // Call SpaceCollectionManager.Instance.GenerateItemsInWorld().
            // Pass in the lists of horizontal and vertical planes that we found earlier.
            SpaceCollectionManager.Instance.GenerateItemsInWorld(horizontal, vertical);
        }
        else
        {
            // We do not have enough floors/walls to place our holograms on...

            // 3.a: Re-enter scanning mode so the user can find more surfaces by
            // calling StartObserver() on the SpatialMappingManager.Instance.
            SpatialMappingManager.Instance.StartObserver();

            // 3.a: Re-process spatial data after scanning completes by
            // re-setting meshesProcessed to false.
            meshesProcessed = false;
        }
    }

    /// <summary>
    /// Creates planes from the spatial mapping surfaces.
    /// </summary>
    private void CreatePlanes()
    {
        // Generate planes based on the spatial map.
        SurfaceMeshesToPlanes surfaceToPlanes = SurfaceMeshesToPlanes.Instance;
        if (surfaceToPlanes != null && surfaceToPlanes.enabled)
        {
            surfaceToPlanes.MakePlanes();
        }
    }

    /// <summary>
    /// Removes triangles from the spatial mapping surfaces.
    /// </summary>
    /// <param name="boundingObjects"></param>
    private void RemoveVertices(IEnumerable<GameObject> boundingObjects)
    {
        RemoveSurfaceVertices removeVerts = RemoveSurfaceVertices.Instance;
        if (removeVerts != null && removeVerts.enabled)
        {
            removeVerts.RemoveSurfaceVerticesWithinBounds(boundingObjects);
        }
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        if (SurfaceMeshesToPlanes.Instance != null)
        {
            SurfaceMeshesToPlanes.Instance.MakePlanesComplete -= SurfaceMeshesToPlanes_MakePlanesComplete;
        }
    }
}
```

<span data-ttu-id="e734f-295">**ビルドと配置**</span><span class="sxs-lookup"><span data-stu-id="e734f-295">**Build and Deploy**</span></span>

* <span data-ttu-id="e734f-296">HoloLens に展開する前に、Unity の [ **再生** ] ボタンを押して、再生モードにします。</span><span class="sxs-lookup"><span data-stu-id="e734f-296">Before deploying to the HoloLens, press the **Play** button in Unity to enter play mode.</span></span>
* <span data-ttu-id="e734f-297">ファイルからルームメッシュが読み込まれたら、空間マッピングメッシュで処理が開始されるまで10秒間待機します。</span><span class="sxs-lookup"><span data-stu-id="e734f-297">After the room mesh is loaded from file, wait for 10 seconds before processing starts on the spatial mapping mesh.</span></span>
* <span data-ttu-id="e734f-298">処理が完了すると、平面は床、壁面、天井などを表すように見えます。</span><span class="sxs-lookup"><span data-stu-id="e734f-298">When processing is complete, planes will appear to represent the floor, walls, ceiling, etc.</span></span>
* <span data-ttu-id="e734f-299">すべての面が見つかったら、カメラの近くにあるフロアのテーブルに太陽のシステムが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e734f-299">After all of the planes have been found, you should see a solar system appear on a table of floor near the camera.</span></span>
* <span data-ttu-id="e734f-300">2つのポスターは、カメラの近くの壁にも表示されます。</span><span class="sxs-lookup"><span data-stu-id="e734f-300">Two posters should appear on walls near the camera too.</span></span> <span data-ttu-id="e734f-301">**ゲーム** モードで表示できない場合は、[**シーン**] タブに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="e734f-301">Switch to the **Scene** tab if you cannot see them in **Game** mode.</span></span>
* <span data-ttu-id="e734f-302">再生モードを終了するには、もう一度 [ **再生** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-302">Press the **Play** button again to exit play mode.</span></span>
* <span data-ttu-id="e734f-303">通常どおり HoloLens にビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="e734f-303">Build and deploy to the HoloLens, as usual.</span></span>
* <span data-ttu-id="e734f-304">空間マッピングデータのスキャンと処理が完了するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="e734f-304">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="e734f-305">プレーンが表示されたら、太陽のシステムとポスターを検索してみてください。</span><span class="sxs-lookup"><span data-stu-id="e734f-305">Once you see planes, try to find the solar system and posters in your world.</span></span>

## <a name="chapter-4---placement"></a><span data-ttu-id="e734f-306">章 4-配置</span><span class="sxs-lookup"><span data-stu-id="e734f-306">Chapter 4 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/Srhtpid1uZc]

<span data-ttu-id="e734f-307">**目標**</span><span class="sxs-lookup"><span data-stu-id="e734f-307">**Objectives**</span></span>

* <span data-ttu-id="e734f-308">ホログラムがサーフェイスに適合するかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="e734f-308">Determine if a hologram will fit on a surface.</span></span>
* <span data-ttu-id="e734f-309">ホログラムがサーフェイスに適合しない場合にユーザーにフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="e734f-309">Provide feedback to the user when a hologram can/cannot fit on a surface.</span></span>

<span data-ttu-id="e734f-310">**手順**</span><span class="sxs-lookup"><span data-stu-id="e734f-310">**Instructions**</span></span>

* <span data-ttu-id="e734f-311">Unity の [ **階層** ] パネルで、 **SpatialProcessing** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-311">In Unity's **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="e734f-312">[ **インスペクター** ] パネルで、[ **平面 (スクリプト)] コンポーネントの表面メッシュを** 見つけます。</span><span class="sxs-lookup"><span data-stu-id="e734f-312">In the **Inspector** panel, find the **Surface Meshes To Planes (Script)** component.</span></span>
* <span data-ttu-id="e734f-313">[ **描画平面** ] プロパティを [ **なし** ] に変更して選択範囲をクリアします。</span><span class="sxs-lookup"><span data-stu-id="e734f-313">Change the **Draw Planes** property to **Nothing** to clear the selection.</span></span>
* <span data-ttu-id="e734f-314">" **描画平面** " プロパティを " **壁**" に変更して、壁面平面だけがレンダリングされるようにします。</span><span class="sxs-lookup"><span data-stu-id="e734f-314">Change the **Draw Planes** property to **Wall**, so that only wall planes will be rendered.</span></span>
* <span data-ttu-id="e734f-315">[ **プロジェクト** ] パネルの **Scripts** フォルダーで、 **Placeable.cs** をダブルクリックして Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="e734f-315">In the **Project** panel, **Scripts** folder, double-click on **Placeable.cs** to open it in Visual Studio.</span></span>

<span data-ttu-id="e734f-316">配置可能 **なスクリプトは、平面** 検索が完了した後に作成されたポスターとプロジェクションボックスに既にアタッチされています。</span><span class="sxs-lookup"><span data-stu-id="e734f-316">The **Placeable** script is already attached to the posters and projection box that are created after plane finding completes.</span></span> <span data-ttu-id="e734f-317">いくつかのコードをコメント解除するだけで、次のことが実現されます。</span><span class="sxs-lookup"><span data-stu-id="e734f-317">All we need to do is uncomment some code, and this script will achieve the following:</span></span>

1. <span data-ttu-id="e734f-318">Raycasting が境界キューブの中心と4つのコーナーから表面にホログラムを収めるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="e734f-318">Determine if a hologram will fit on a surface by raycasting from the center and four corners of the bounding cube.</span></span>
2. <span data-ttu-id="e734f-319">表面の法線を調べて、ホログラムをフラッシュするのに十分な滑らかさがあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="e734f-319">Check the surface normal to determine if it is smooth enough for the hologram to sit flush on.</span></span>
3. <span data-ttu-id="e734f-320">ホログラムの周りに境界キューブをレンダリングして、配置中の実際のサイズを示します。</span><span class="sxs-lookup"><span data-stu-id="e734f-320">Render a bounding cube around the hologram to show its actual size while being placed.</span></span>
4. <span data-ttu-id="e734f-321">ホログラムの下または後ろに影をキャストして、床と壁のどこに配置されるかを示します。</span><span class="sxs-lookup"><span data-stu-id="e734f-321">Cast a shadow under/behind the hologram to show where it will be placed on the floor/wall.</span></span>
5. <span data-ttu-id="e734f-322">ホログラムを表面に配置できない場合、または緑の場合は、影を赤で表示します。</span><span class="sxs-lookup"><span data-stu-id="e734f-322">Render the shadow as red, if the hologram cannot be placed on the surface, or green, if it can.</span></span>
6. <span data-ttu-id="e734f-323">関係がある表面の種類 (垂直方向または水平方向) に合わせてホログラムを再配置します。</span><span class="sxs-lookup"><span data-stu-id="e734f-323">Re-orient the hologram to align with the surface type (vertical or horizontal) that it has affinity to.</span></span>
7. <span data-ttu-id="e734f-324">選択したサーフェイスにホログラムをスムーズに配置して、ジャンプやスナップ動作を回避します。</span><span class="sxs-lookup"><span data-stu-id="e734f-324">Smoothly place the hologram on the selected surface to avoid jumping or snapping behavior.</span></span>

<span data-ttu-id="e734f-325">以下のコーディング演習ですべてのコードのコメントを解除するか、 **Placeable.cs** でこの完成したソリューションを使用します。</span><span class="sxs-lookup"><span data-stu-id="e734f-325">Uncomment all code in the coding exercise below, or use this completed solution in **Placeable.cs**:</span></span>

```cs
using System.Collections.Generic;
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Enumeration containing the surfaces on which a GameObject
/// can be placed.  For simplicity of this sample, only one
/// surface type is allowed to be selected.
/// </summary>
public enum PlacementSurfaces
{
    // Horizontal surface with an upward pointing normal.
    Horizontal = 1,

    // Vertical surface with a normal facing the user.
    Vertical = 2,
}

/// <summary>
/// The Placeable class implements the logic used to determine if a GameObject
/// can be placed on a target surface. Constraints for placement include:
/// * No part of the GameObject's box collider impacts with another object in the scene
/// * The object lays flat (within specified tolerances) against the surface
/// * The object would not fall off of the surface if gravity were enabled.
/// This class also provides the following visualizations.
/// * A transparent cube representing the object's box collider.
/// * Shadow on the target surface indicating whether or not placement is valid.
/// </summary>
public class Placeable : MonoBehaviour
{
    [Tooltip("The base material used to render the bounds asset when placement is allowed.")]
    public Material PlaceableBoundsMaterial = null;

    [Tooltip("The base material used to render the bounds asset when placement is not allowed.")]
    public Material NotPlaceableBoundsMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it allowed.")]
    public Material PlaceableShadowMaterial = null;

    [Tooltip("The material used to render the placement shadow when placement it not allowed.")]
    public Material NotPlaceableShadowMaterial = null;

    [Tooltip("The type of surface on which the object can be placed.")]
    public PlacementSurfaces PlacementSurface = PlacementSurfaces.Horizontal;

    [Tooltip("The child object(s) to hide during placement.")]
    public List<GameObject> ChildrenToHide = new List<GameObject>();

    /// <summary>
    /// Indicates if the object is in the process of being placed.
    /// </summary>
    public bool IsPlacing { get; private set; }

    // The most recent distance to the surface.  This is used to 
    // locate the object when the user's gaze does not intersect
    // with the Spatial Mapping mesh.
    private float lastDistance = 2.0f;

    // The distance away from the target surface that the object should hover prior while being placed.
    private float hoverDistance = 0.15f;

    // Threshold (the closer to 0, the stricter the standard) used to determine if a surface is flat.
    private float distanceThreshold = 0.02f;

    // Threshold (the closer to 1, the stricter the standard) used to determine if a surface is vertical.
    private float upNormalThreshold = 0.9f;

    // Maximum distance, from the object, that placement is allowed.
    // This is used when raycasting to see if the object is near a placeable surface.
    private float maximumPlacementDistance = 5.0f;

    // Speed (1.0 being fastest) at which the object settles to the surface upon placement.
    private float placementVelocity = 0.06f;

    // Indicates whether or not this script manages the object's box collider.
    private bool managingBoxCollider = false;

    // The box collider used to determine of the object will fit in the desired location.
    // It is also used to size the bounding cube.
    private BoxCollider boxCollider = null;

    // Visible asset used to show the dimensions of the object. This asset is sized
    // using the box collider's bounds.
    private GameObject boundsAsset = null;

    // Visible asset used to show the where the object is attempting to be placed.
    // This asset is sized using the box collider's bounds.
    private GameObject shadowAsset = null;

    // The location at which the object will be placed.
    private Vector3 targetPosition;

    /// <summary>
    /// Called when the GameObject is created.
    /// </summary>
    private void Awake()
    {
        targetPosition = gameObject.transform.position;

        // Get the object's collider.
        boxCollider = gameObject.GetComponent<BoxCollider>();
        if (boxCollider == null)
        {
            // The object does not have a collider, create one and remember that
            // we are managing it.
            managingBoxCollider = true;
            boxCollider = gameObject.AddComponent<BoxCollider>();
            boxCollider.enabled = false;
        }

        // Create the object that will be used to indicate the bounds of the GameObject.
        boundsAsset = GameObject.CreatePrimitive(PrimitiveType.Cube);
        boundsAsset.transform.parent = gameObject.transform;
        boundsAsset.SetActive(false);

        // Create a object that will be used as a shadow.
        shadowAsset = GameObject.CreatePrimitive(PrimitiveType.Quad);
        shadowAsset.transform.parent = gameObject.transform;
        shadowAsset.SetActive(false);
    }

    /// <summary>
    /// Called when our object is selected.  Generally called by
    /// a gesture management component.
    /// </summary>
    public void OnSelect()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (!IsPlacing)
        {
            OnPlacementStart();
        }
        else
        {
            OnPlacementStop();
        }
    }

    /// <summary>
    /// Called once per frame.
    /// </summary>
    private void Update()
    {
        /* TODO: 4.a CODE ALONG 4.a */

        if (IsPlacing)
        {
            // Move the object.
            Move();

            // Set the visual elements.
            Vector3 targetPosition;
            Vector3 surfaceNormal;
            bool canBePlaced = ValidatePlacement(out targetPosition, out surfaceNormal);
            DisplayBounds(canBePlaced);
            DisplayShadow(targetPosition, surfaceNormal, canBePlaced);
        }
        else
        {
            // Disable the visual elements.
            boundsAsset.SetActive(false);
            shadowAsset.SetActive(false);

            // Gracefully place the object on the target surface.
            float dist = (gameObject.transform.position - targetPosition).magnitude;
            if (dist > 0)
            {
                gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, targetPosition, placementVelocity / dist);
            }
            else
            {
                // Unhide the child object(s) to make placement easier.
                for (int i = 0; i < ChildrenToHide.Count; i++)
                {
                    ChildrenToHide[i].SetActive(true);
                }
            }
        }
    }

    /// <summary>
    /// Verify whether or not the object can be placed.
    /// </summary>
    /// <param name="position">
    /// The target position on the surface.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the object is to be placed.
    /// </param>
    /// <returns>
    /// True if the target position is valid for placing the object, otherwise false.
    /// </returns>
    private bool ValidatePlacement(out Vector3 position, out Vector3 surfaceNormal)
    {
        Vector3 raycastDirection = gameObject.transform.forward;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            // Raycast from the bottom face of the box collider.
            raycastDirection = -(Vector3.up);
        }

        // Initialize out parameters.
        position = Vector3.zero;
        surfaceNormal = Vector3.zero;

        Vector3[] facePoints = GetColliderFacePoints();

        // The origin points we receive are in local space and we 
        // need to raycast in world space.
        for (int i = 0; i < facePoints.Length; i++)
        {
            facePoints[i] = gameObject.transform.TransformVector(facePoints[i]) + gameObject.transform.position;
        }

        // Cast a ray from the center of the box collider face to the surface.
        RaycastHit centerHit;
        if (!Physics.Raycast(facePoints[0],
                        raycastDirection,
                        out centerHit,
                        maximumPlacementDistance,
                        SpatialMappingManager.Instance.LayerMask))
        {
            // If the ray failed to hit the surface, we are done.
            return false;
        }

        // We have found a surface.  Set position and surfaceNormal.
        position = centerHit.point;
        surfaceNormal = centerHit.normal;

        // Cast a ray from the corners of the box collider face to the surface.
        for (int i = 1; i < facePoints.Length; i++)
        {
            RaycastHit hitInfo;
            if (Physics.Raycast(facePoints[i],
                                raycastDirection,
                                out hitInfo,
                                maximumPlacementDistance,
                                SpatialMappingManager.Instance.LayerMask))
            {
                // To be a valid placement location, each of the corners must have a similar
                // enough distance to the surface as the center point
                if (!IsEquivalentDistance(centerHit.distance, hitInfo.distance))
                {
                    return false;
                }
            }
            else
            {
                // The raycast failed to intersect with the target layer.
                return false;
            }
        }

        return true;
    }

    /// <summary>
    /// Determine the coordinates, in local space, of the box collider face that 
    /// will be placed against the target surface.
    /// </summary>
    /// <returns>
    /// Vector3 array with the center point of the face at index 0.
    /// </returns>
    private Vector3[] GetColliderFacePoints()
    {
        // Get the collider extents.  
        // The size values are twice the extents.
        Vector3 extents = boxCollider.size / 2;

        // Calculate the min and max values for each coordinate.
        float minX = boxCollider.center.x - extents.x;
        float maxX = boxCollider.center.x + extents.x;
        float minY = boxCollider.center.y - extents.y;
        float maxY = boxCollider.center.y + extents.y;
        float minZ = boxCollider.center.z - extents.z;
        float maxZ = boxCollider.center.z + extents.z;

        Vector3 center;
        Vector3 corner0;
        Vector3 corner1;
        Vector3 corner2;
        Vector3 corner3;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            // Placing on horizontal surfaces.
            center = new Vector3(boxCollider.center.x, minY, boxCollider.center.z);
            corner0 = new Vector3(minX, minY, minZ);
            corner1 = new Vector3(minX, minY, maxZ);
            corner2 = new Vector3(maxX, minY, minZ);
            corner3 = new Vector3(maxX, minY, maxZ);
        }
        else
        {
            // Placing on vertical surfaces.
            center = new Vector3(boxCollider.center.x, boxCollider.center.y, maxZ);
            corner0 = new Vector3(minX, minY, maxZ);
            corner1 = new Vector3(minX, maxY, maxZ);
            corner2 = new Vector3(maxX, minY, maxZ);
            corner3 = new Vector3(maxX, maxY, maxZ);
        }

        return new Vector3[] { center, corner0, corner1, corner2, corner3 };
    }

    /// <summary>
    /// Put the object into placement mode.
    /// </summary>
    public void OnPlacementStart()
    {
        // If we are managing the collider, enable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = true;
        }

        // Hide the child object(s) to make placement easier.
        for (int i = 0; i < ChildrenToHide.Count; i++)
        {
            ChildrenToHide[i].SetActive(false);
        }

        // Tell the gesture manager that it is to assume
        // all input is to be given to this object.
        GestureManager.Instance.OverrideFocusedObject = gameObject;

        // Enter placement mode.
        IsPlacing = true;
    }

    /// <summary>
    /// Take the object out of placement mode.
    /// </summary>
    /// <remarks>
    /// This method will leave the object in placement mode if called while
    /// the object is in an invalid location.  To determine whether or not
    /// the object has been placed, check the value of the IsPlacing property.
    /// </remarks>
    public void OnPlacementStop()
    {
        // ValidatePlacement requires a normal as an out parameter.
        Vector3 position;
        Vector3 surfaceNormal;

        // Check to see if we can exit placement mode.
        if (!ValidatePlacement(out position, out surfaceNormal))
        {
            return;
        }

        // The object is allowed to be placed.
        // We are placing at a small buffer away from the surface.
        targetPosition = position + (0.01f * surfaceNormal);

        OrientObject(true, surfaceNormal);

        // If we are managing the collider, disable it. 
        if (managingBoxCollider)
        {
            boxCollider.enabled = false;
        }

        // Tell the gesture manager that it is to resume
        // its normal behavior.
        GestureManager.Instance.OverrideFocusedObject = null;

        // Exit placement mode.
        IsPlacing = false;
    }

    /// <summary>
    /// Positions the object along the surface toward which the user is gazing.
    /// </summary>
    /// <remarks>
    /// If the user's gaze does not intersect with a surface, the object
    /// will remain at the most recently calculated distance.
    /// </remarks>
    private void Move()
    {
        Vector3 moveTo = gameObject.transform.position;
        Vector3 surfaceNormal = Vector3.zero;
        RaycastHit hitInfo;

        bool hit = Physics.Raycast(Camera.main.transform.position,
                                Camera.main.transform.forward,
                                out hitInfo,
                                20f,
                                SpatialMappingManager.Instance.LayerMask);

        if (hit)
        {
            float offsetDistance = hoverDistance;

            // Place the object a small distance away from the surface while keeping 
            // the object from going behind the user.
            if (hitInfo.distance <= hoverDistance)
            {
                offsetDistance = 0f;
            }

            moveTo = hitInfo.point + (offsetDistance * hitInfo.normal);

            lastDistance = hitInfo.distance;
            surfaceNormal = hitInfo.normal;
        }
        else
        {
            // The raycast failed to hit a surface.  In this case, keep the object at the distance of the last
            // intersected surface.
            moveTo = Camera.main.transform.position + (Camera.main.transform.forward * lastDistance);
        }

        // Follow the user's gaze.
        float dist = Mathf.Abs((gameObject.transform.position - moveTo).magnitude);
        gameObject.transform.position = Vector3.Lerp(gameObject.transform.position, moveTo, placementVelocity / dist);

        // Orient the object.
        // We are using the return value from Physics.Raycast to instruct
        // the OrientObject function to align to the vertical surface if appropriate.
        OrientObject(hit, surfaceNormal);
    }

    /// <summary>
    /// Orients the object so that it faces the user.
    /// </summary>
    /// <param name="alignToVerticalSurface">
    /// If true and the object is to be placed on a vertical surface, 
    /// orient parallel to the target surface.  If false, orient the object 
    /// to face the user.
    /// </param>
    /// <param name="surfaceNormal">
    /// The target surface's normal vector.
    /// </param>
    /// <remarks>
    /// The alignToVerticalSurface parameter is ignored if the object
    /// is to be placed on a horizontalSurface
    /// </remarks>
    private void OrientObject(bool alignToVerticalSurface, Vector3 surfaceNormal)
    {
        Quaternion rotation = Camera.main.transform.localRotation;

        // If the user's gaze does not intersect with the Spatial Mapping mesh,
        // orient the object towards the user.
        if (alignToVerticalSurface && (PlacementSurface == PlacementSurfaces.Vertical))
        {
            // We are placing on a vertical surface.
            // If the normal of the Spatial Mapping mesh indicates that the
            // surface is vertical, orient parallel to the surface.
            if (Mathf.Abs(surfaceNormal.y) <= (1 - upNormalThreshold))
            {
                rotation = Quaternion.LookRotation(-surfaceNormal, Vector3.up);
            }
        }
        else
        {
            rotation.x = 0f;
            rotation.z = 0f;
        }

        gameObject.transform.rotation = rotation;
    }

    /// <summary>
    /// Displays the bounds asset.
    /// </summary>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayBounds(bool canBePlaced)
    {
        // Ensure the bounds asset is sized and positioned correctly.
        boundsAsset.transform.localPosition = boxCollider.center;
        boundsAsset.transform.localScale = boxCollider.size;
        boundsAsset.transform.rotation = gameObject.transform.rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = PlaceableBoundsMaterial;
        }
        else
        {
            boundsAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableBoundsMaterial;
        }

        // Show the bounds asset.
        boundsAsset.SetActive(true);
    }

    /// <summary>
    /// Displays the placement shadow asset.
    /// </summary>
    /// <param name="position">
    /// The position at which to place the shadow asset.
    /// </param>
    /// <param name="surfaceNormal">
    /// The normal of the surface on which the asset will be placed
    /// </param>
    /// <param name="canBePlaced">
    /// Specifies if the object is in a valid placement location.
    /// </param>
    private void DisplayShadow(Vector3 position,
                            Vector3 surfaceNormal,
                            bool canBePlaced)
    {
        // Rotate and scale the shadow so that it is displayed on the correct surface and matches the object.
        float rotationX = 0.0f;

        if (PlacementSurface == PlacementSurfaces.Horizontal)
        {
            rotationX = 90.0f;
            shadowAsset.transform.localScale = new Vector3(boxCollider.size.x, boxCollider.size.z, 1);
        }
        else
        {
            shadowAsset.transform.localScale = boxCollider.size;
        }

        Quaternion rotation = Quaternion.Euler(rotationX, gameObject.transform.rotation.eulerAngles.y, 0);
        shadowAsset.transform.rotation = rotation;

        // Apply the appropriate material.
        if (canBePlaced)
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = PlaceableShadowMaterial;
        }
        else
        {
            shadowAsset.GetComponent<Renderer>().sharedMaterial = NotPlaceableShadowMaterial;
        }

        // Show the shadow asset as appropriate.
        if (position != Vector3.zero)
        {
            // Position the shadow a small distance from the target surface, along the normal.
            shadowAsset.transform.position = position + (0.01f * surfaceNormal);
            shadowAsset.SetActive(true);
        }
        else
        {
            shadowAsset.SetActive(false);
        }
    }

    /// <summary>
    /// Determines if two distance values should be considered equivalent. 
    /// </summary>
    /// <param name="d1">
    /// Distance to compare.
    /// </param>
    /// <param name="d2">
    /// Distance to compare.
    /// </param>
    /// <returns>
    /// True if the distances are within the desired tolerance, otherwise false.
    /// </returns>
    private bool IsEquivalentDistance(float d1, float d2)
    {
        float dist = Mathf.Abs(d1 - d2);
        return (dist <= distanceThreshold);
    }

    /// <summary>
    /// Called when the GameObject is unloaded.
    /// </summary>
    private void OnDestroy()
    {
        // Unload objects we have created.
        Destroy(boundsAsset);
        boundsAsset = null;
        Destroy(shadowAsset);
        shadowAsset = null;
    }
}
```

<span data-ttu-id="e734f-326">**ビルドと配置**</span><span class="sxs-lookup"><span data-stu-id="e734f-326">**Build and Deploy**</span></span>

* <span data-ttu-id="e734f-327">前と同様に、プロジェクトをビルドし、HoloLens にデプロイします。</span><span class="sxs-lookup"><span data-stu-id="e734f-327">As before, build the project and deploy to the HoloLens.</span></span>
* <span data-ttu-id="e734f-328">空間マッピングデータのスキャンと処理が完了するまで待機します。</span><span class="sxs-lookup"><span data-stu-id="e734f-328">Wait for scanning and processing of the spatial mapping data to complete.</span></span>
* <span data-ttu-id="e734f-329">太陽のシステムが表示されたら、下の投影ボックスを見つめ、選択ジェスチャを実行して移動します。</span><span class="sxs-lookup"><span data-stu-id="e734f-329">When you see the solar system, gaze at the projection box below and perform a select gesture to move it around.</span></span> <span data-ttu-id="e734f-330">[プロジェクション] ボックスを選択すると、[プロジェクション] ボックスの周囲に境界キューブが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e734f-330">While the projection box is selected, a bounding cube will be visible around the projection box.</span></span>
* <span data-ttu-id="e734f-331">部屋の別の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="e734f-331">Move you head to gaze at a different location in the room.</span></span> <span data-ttu-id="e734f-332">プロジェクションボックスは、お使いの宝石に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="e734f-332">The projection box should follow your gaze.</span></span> <span data-ttu-id="e734f-333">投影ボックスの下の影が赤に変わったら、その表面にホログラムを配置することはできません。</span><span class="sxs-lookup"><span data-stu-id="e734f-333">When the shadow below the projection box turns red, you cannot place the hologram on that surface.</span></span> <span data-ttu-id="e734f-334">投影ボックスの下の影が緑色に変わったら、別の選択ジェスチャを実行してホログラムを配置できます。</span><span class="sxs-lookup"><span data-stu-id="e734f-334">When the shadow below the projection box turns green, you can place the hologram by performing another select gesture.</span></span>
* <span data-ttu-id="e734f-335">壁の holographic ポスターの1つを探して選択し、新しい場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="e734f-335">Find and select one of the holographic posters on a wall to move it to a new location.</span></span> <span data-ttu-id="e734f-336">フロアまたはシーリングにポスターを配置することはできません。また、移動するたびに各壁面に合わせて正しい向きに保たれることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e734f-336">Notice that you cannot place the poster on the floor or ceiling, and that it stays correctly oriented to each wall as you move around.</span></span>

## <a name="chapter-5---occlusion"></a><span data-ttu-id="e734f-337">第5章-オクルージョン</span><span class="sxs-lookup"><span data-stu-id="e734f-337">Chapter 5 - Occlusion</span></span>

>[!VIDEO https://www.youtube.com/embed/6Xrzh_w-7SE]

<span data-ttu-id="e734f-338">**目標**</span><span class="sxs-lookup"><span data-stu-id="e734f-338">**Objectives**</span></span>

* <span data-ttu-id="e734f-339">ホログラムが空間マッピングメッシュによって occluded されているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="e734f-339">Determine if a hologram is occluded by the spatial mapping mesh.</span></span>
* <span data-ttu-id="e734f-340">さまざまな遮蔽手法を適用して、楽しい効果を実現します。</span><span class="sxs-lookup"><span data-stu-id="e734f-340">Apply different occlusion techniques to achieve a fun effect.</span></span>

<span data-ttu-id="e734f-341">**手順**</span><span class="sxs-lookup"><span data-stu-id="e734f-341">**Instructions**</span></span>

<span data-ttu-id="e734f-342">まず、空間マッピングメッシュで、occluding を使用せずに他のホログラムを occlude できるようにします。</span><span class="sxs-lookup"><span data-stu-id="e734f-342">First, we are going to allow the spatial mapping mesh to occlude other holograms without occluding the real world:</span></span>

* <span data-ttu-id="e734f-343">[ **階層** ] パネルで、 **SpatialProcessing** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="e734f-343">In the **Hierarchy** panel, select the **SpatialProcessing** object.</span></span>
* <span data-ttu-id="e734f-344">[ **インスペクター** ] パネルで、[ **Play Space Manager (スクリプト)** ] コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="e734f-344">In the **Inspector** panel, find the **Play Space Manager (Script)** component.</span></span>
* <span data-ttu-id="e734f-345">[ **セカンダリマテリアル** ] プロパティの右側にある円をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-345">Click the circle to the right of the **Secondary Material** property.</span></span>
* <span data-ttu-id="e734f-346">**オクルージョン** を検索して選択し、ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="e734f-346">Find and select the **Occlusion** material and close the window.</span></span>

<span data-ttu-id="e734f-347">次に、地球に特別な動作を追加します。これにより、(太陽などの) 別のホログラムによって occluded されたとき、または空間マッピングメッシュによって、青の強調表示になります。</span><span class="sxs-lookup"><span data-stu-id="e734f-347">Next, we are going to add a special behavior to Earth, so that it has a blue highlight whenever it becomes occluded by another hologram (like the sun), or by the spatial mapping mesh:</span></span>

* <span data-ttu-id="e734f-348">[ **プロジェクト** ] パネルの [ **ホログラム** ] フォルダーで **、[] オブジェクトを** 展開します。</span><span class="sxs-lookup"><span data-stu-id="e734f-348">In the **Project** panel, in the **Holograms** folder, expand the **SolarSystem** object.</span></span>
* <span data-ttu-id="e734f-349">[ **地球**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e734f-349">Click on **Earth**.</span></span>
* <span data-ttu-id="e734f-350">[ **インスペクター** ] パネルで、地球の素材 (下部コンポーネント) を見つけます。</span><span class="sxs-lookup"><span data-stu-id="e734f-350">In the **Inspector** panel, find the Earth's material (bottom component).</span></span>
* <span data-ttu-id="e734f-351">シェーダーの **ドロップダウン** で、シェーダーを **カスタム > OcclusionRim** に変更します。</span><span class="sxs-lookup"><span data-stu-id="e734f-351">In the **Shader drop-down**, change the shader to **Custom > OcclusionRim**.</span></span> <span data-ttu-id="e734f-352">これは、別のオブジェクトによって occluded されたときに、地球を中心とした青い強調表示になります。</span><span class="sxs-lookup"><span data-stu-id="e734f-352">This will render a blue highlight around Earth whenever it is occluded by another object.</span></span>

<span data-ttu-id="e734f-353">最後に、太陽のシステムで惑星に対して x 線の視覚効果を有効にします。</span><span class="sxs-lookup"><span data-stu-id="e734f-353">Finally, we are going to enable an x-ray vision effect for planets in our solar system.</span></span> <span data-ttu-id="e734f-354">次のことを実現するために、 **PlanetOcclusion.cs** (スクリプト \ システムフォルダーにあります) を編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e734f-354">We will need to edit **PlanetOcclusion.cs** (found in the Scripts\SolarSystem folder) in order to achieve the following:</span></span>

1. <span data-ttu-id="e734f-355">地球が SpatialMapping レイヤーによって occluded されているかどうかを判断します (部屋メッシュと平面)。</span><span class="sxs-lookup"><span data-stu-id="e734f-355">Determine if a planet is occluded by the SpatialMapping layer (room meshes and planes).</span></span>
2. <span data-ttu-id="e734f-356">SpatialMapping レイヤーによって occluded されるたびに、地球のワイヤーフレーム表現を表示します。</span><span class="sxs-lookup"><span data-stu-id="e734f-356">Show the wireframe representation of a planet whenever it is occluded by the SpatialMapping layer.</span></span>
3. <span data-ttu-id="e734f-357">地球のワイヤーフレーム表現が SpatialMapping レイヤーによってブロックされていない場合は非表示にします。</span><span class="sxs-lookup"><span data-stu-id="e734f-357">Hide the wireframe representation of a planet when it is not blocked by the SpatialMapping layer.</span></span>

<span data-ttu-id="e734f-358">PlanetOcclusion.cs のコーディングの演習に従うか、次の解決策を使用します。</span><span class="sxs-lookup"><span data-stu-id="e734f-358">Follow the coding exercise in PlanetOcclusion.cs, or use the following solution:</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Determines when the occluded version of the planet should be visible.
/// This script allows us to do selective occlusion, so the occlusionObject
/// will only be rendered when a Spatial Mapping surface is occluding the planet,
/// not when another hologram is responsible for the occlusion.
/// </summary>
public class PlanetOcclusion : MonoBehaviour
{
    [Tooltip("Object to display when the planet is occluded.")]
    public GameObject occlusionObject;

    /// <summary>
    /// Points to raycast to when checking for occlusion.
    /// </summary>
    private Vector3[] checkPoints;

    // Use this for initialization
    void Start()
    {
        occlusionObject.SetActive(false);

        // Set the check points to use when testing for occlusion.
        MeshFilter filter = gameObject.GetComponent<MeshFilter>();
        Vector3 extents = filter.mesh.bounds.extents;
        Vector3 center = filter.mesh.bounds.center;
        Vector3 top = new Vector3(center.x, center.y + extents.y, center.z);
        Vector3 left = new Vector3(center.x - extents.x, center.y, center.z);
        Vector3 right = new Vector3(center.x + extents.x, center.y, center.z);
        Vector3 bottom = new Vector3(center.x, center.y - extents.y, center.z);

        checkPoints = new Vector3[] { center, top, left, right, bottom };
    }

    // Update is called once per frame
    void Update()
    {
        /* TODO: 5.a DEVELOPER CODING EXERCISE 5.a */

        // Check to see if any of the planet's boundary points are occluded.
        for (int i = 0; i < checkPoints.Length; i++)
        {
            // 5.a: Convert the current checkPoint to world coordinates.
            // Call gameObject.transform.TransformPoint(checkPoints[i]).
            // Assign the result to a new Vector3 variable called 'checkPt'.
            Vector3 checkPt = gameObject.transform.TransformPoint(checkPoints[i]);

            // 5.a: Call Vector3.Distance() to calculate the distance
            // between the Main Camera's position and 'checkPt'.
            // Assign the result to a new float variable called 'distance'.
            float distance = Vector3.Distance(Camera.main.transform.position, checkPt);

            // 5.a: Take 'checkPt' and subtract the Main Camera's position from it.
            // Assign the result to a new Vector3 variable called 'direction'.
            Vector3 direction = checkPt - Camera.main.transform.position;

            // Used to indicate if the call to Physics.Raycast() was successful.
            bool raycastHit = false;

            // 5.a: Check if the planet is occluded by a spatial mapping surface.
            // Call Physics.Raycast() with the following arguments:
            // - Pass in the Main Camera's position as the origin.
            // - Pass in 'direction' for the direction.
            // - Pass in 'distance' for the maxDistance.
            // - Pass in SpatialMappingManager.Instance.LayerMask as layerMask.
            // Assign the result to 'raycastHit'.
            raycastHit = Physics.Raycast(Camera.main.transform.position, direction, distance, SpatialMappingManager.Instance.LayerMask);

            if (raycastHit)
            {
                // 5.a: Our raycast hit a surface, so the planet is occluded.
                // Set the occlusionObject to active.
                occlusionObject.SetActive(true);

                // At least one point is occluded, so break from the loop.
                break;
            }
            else
            {
                // 5.a: The Raycast did not hit, so the planet is not occluded.
                // Deactivate the occlusionObject.
                occlusionObject.SetActive(false);
            }
        }
    }
}
```

<span data-ttu-id="e734f-359">**ビルドと配置**</span><span class="sxs-lookup"><span data-stu-id="e734f-359">**Build and Deploy**</span></span>

* <span data-ttu-id="e734f-360">通常どおり、アプリケーションを HoloLens に構築してデプロイします。</span><span class="sxs-lookup"><span data-stu-id="e734f-360">Build and deploy the application to HoloLens, as usual.</span></span>
* <span data-ttu-id="e734f-361">空間マッピングデータのスキャンと処理が完了するまで待ちます (壁に青い線が表示されます)。</span><span class="sxs-lookup"><span data-stu-id="e734f-361">Wait for scanning and processing of the spatial mapping data to be complete (you should see blue lines appear on walls).</span></span>
* <span data-ttu-id="e734f-362">[太陽システムの投影] ボックスを探して選択し、壁の横またはカウンターの背後にあるボックスを設定します。</span><span class="sxs-lookup"><span data-stu-id="e734f-362">Find and select the solar system's projection box and then set the box next to a wall or behind a counter.</span></span>
* <span data-ttu-id="e734f-363">[ポスター] ボックスまたは [投影] ボックスで、ピアに対する表面の背後を非表示にすることで、基本的なオクルージョンを表示できます。</span><span class="sxs-lookup"><span data-stu-id="e734f-363">You can view basic occlusion by hiding behind surfaces to peer at the poster or projection box.</span></span>
* <span data-ttu-id="e734f-364">地球を探すには、別のホログラムや表面にいるときは常に青いハイライト効果があるはずです。</span><span class="sxs-lookup"><span data-stu-id="e734f-364">Look for the Earth, there should be a blue highlight effect whenever it goes behind another hologram or surface.</span></span>
* <span data-ttu-id="e734f-365">惑星が部屋の壁またはその他の表面の内側に移動するのを監視します。</span><span class="sxs-lookup"><span data-stu-id="e734f-365">Watch as the planets move behind the wall or other surfaces in the room.</span></span> <span data-ttu-id="e734f-366">X 線によるビジョンが可能になり、ワイヤーフレームスケルトンを見ることができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e734f-366">You now have x-ray vision and can see their wireframe skeletons!</span></span>

## <a name="the-end"></a><span data-ttu-id="e734f-367">最後です</span><span class="sxs-lookup"><span data-stu-id="e734f-367">The End</span></span>

<span data-ttu-id="e734f-368">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="e734f-368">Congratulations!</span></span> <span data-ttu-id="e734f-369">これで、 **MR 空間 230: 空間マッピング** が完了しました。</span><span class="sxs-lookup"><span data-stu-id="e734f-369">You have now completed **MR Spatial 230: Spatial mapping**.</span></span>

* <span data-ttu-id="e734f-370">環境をスキャンして、Unity に空間マッピングデータを読み込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e734f-370">You know how to scan your environment and load spatial mapping data to Unity.</span></span>
* <span data-ttu-id="e734f-371">シェーダーの基本と、マテリアルを使用して世界を再視覚化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e734f-371">You understand the basics of shaders and how materials can be used to re-visualize the world.</span></span>
* <span data-ttu-id="e734f-372">平面を検索し、メッシュから三角形を削除するための新しい処理手法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="e734f-372">You learned of new processing techniques for finding planes and removing triangles from a mesh.</span></span>
* <span data-ttu-id="e734f-373">意味のあるサーフェイスにホログラムを移動して配置することができました。</span><span class="sxs-lookup"><span data-stu-id="e734f-373">You were able to move and place holograms on surfaces that made sense.</span></span>
* <span data-ttu-id="e734f-374">さまざまな遮蔽手法を経験し、開花の力を活用しました。</span><span class="sxs-lookup"><span data-stu-id="e734f-374">You experienced different occlusion techniques and harnessed the power of x-ray vision!</span></span>