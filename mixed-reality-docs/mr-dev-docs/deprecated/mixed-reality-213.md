---
title: MR 入力 213
description: Unity、Visual Studio、およびイマーシブヘッドセットを使用したこのコーディングチュートリアルに従って、モーションコントローラーの詳細を学習してください。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、イマーシブ、motion controller、academy、チュートリアル
ms.openlocfilehash: c83fd4970e40919e146b0a4e8b4f0f516e9d0906
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685378"
---
# <a name="mr-input-213-motion-controllers"></a><span data-ttu-id="7b338-104">MR 入力 213:モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="7b338-104">MR Input 213: Motion controllers</span></span>

>[!NOTE]
><span data-ttu-id="7b338-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="7b338-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="7b338-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="7b338-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="7b338-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。</span><span class="sxs-lookup"><span data-stu-id="7b338-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="7b338-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="7b338-109">HoloLens 2 向けには、[新しいチュートリアル シリーズ](../mr-learning-base-01.md)が投稿されています。</span><span class="sxs-lookup"><span data-stu-id="7b338-109">[A new series of tutorials](../mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="7b338-110">混合現実世界のモーションコントローラーは、別のレベルの対話機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="7b338-110">Motion controllers in the mixed reality world add another level of interactivity.</span></span> <span data-ttu-id="7b338-111">[モーションコントローラー](../design/motion-controllers.md)を使用すると、リアルタイムでの物理的な相互作用と同様に、オブジェクトをより自然な方法で直接やり取りし、アプリのエクスペリエンスの immersion と満足させるを増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="7b338-111">With [motion controllers](../design/motion-controllers.md), we can directly interact with objects in a more natural way, similar to our physical interactions in real life, increasing immersion and delight in your app experience.</span></span>

<span data-ttu-id="7b338-112">MR 入力213では、単純な空間描画エクスペリエンスを作成することによって、モーションコントローラーの入力イベントを調査します。</span><span class="sxs-lookup"><span data-stu-id="7b338-112">In MR Input 213, we will explore the motion controller's input events by creating a simple spatial painting experience.</span></span> <span data-ttu-id="7b338-113">このアプリでは、ユーザーはさまざまな種類のブラシや色を使用して3次元空間で塗りつぶすことができます。</span><span class="sxs-lookup"><span data-stu-id="7b338-113">With this app, users can paint in three-dimensional space with various types of brushes and colors.</span></span>

## <a name="topics-covered-in-this-tutorial"></a><span data-ttu-id="7b338-114">このチュートリアルで説明するトピック</span><span class="sxs-lookup"><span data-stu-id="7b338-114">Topics covered in this tutorial</span></span>

|![MixedReality213 Topic1](images/mr213-topic1.png)|![MixedReality213 Topic2](images/mr213-topic2.png)|![MixedReality213 Topic3](images/mr213-topic3.png)|
| :--- | :--- | :--- |
|<span data-ttu-id="7b338-118">**コントローラーの視覚化**</span><span class="sxs-lookup"><span data-stu-id="7b338-118">**Controller visualization**</span></span>|<span data-ttu-id="7b338-119">**コントローラーの入力イベント**</span><span class="sxs-lookup"><span data-stu-id="7b338-119">**Controller input events**</span></span>|<span data-ttu-id="7b338-120">**カスタムコントローラーと UI**</span><span class="sxs-lookup"><span data-stu-id="7b338-120">**Custom controller and UI**</span></span>|
|<span data-ttu-id="7b338-121">Unity のゲームモードとランタイムでモーションコントローラーモデルをレンダリングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-121">Learn how to render motion controller models in Unity's game mode and runtime.</span></span>|<span data-ttu-id="7b338-122">さまざまな種類のボタンイベントとそのアプリケーションを理解します。</span><span class="sxs-lookup"><span data-stu-id="7b338-122">Understand different types of button events and their applications.</span></span>|<span data-ttu-id="7b338-123">コントローラー上に UI 要素を重ね合わせる方法、または UI 要素を完全にカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-123">Learn how to overlay UI elements on top of the controller or fully customize it.</span></span>|

## <a name="device-support"></a><span data-ttu-id="7b338-124">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="7b338-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="7b338-125">コース</span><span class="sxs-lookup"><span data-stu-id="7b338-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="7b338-126"><a href="../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="7b338-126"><a href="../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="7b338-127"><a href="../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="7b338-127"><a href="../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="7b338-128">MR 入力 213:モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="7b338-128">MR Input 213: Motion controllers</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="7b338-129">✔️</span><span class="sxs-lookup"><span data-stu-id="7b338-129">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="7b338-130">開始する前に</span><span class="sxs-lookup"><span data-stu-id="7b338-130">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="7b338-131">前提条件</span><span class="sxs-lookup"><span data-stu-id="7b338-131">Prerequisites</span></span>

<span data-ttu-id="7b338-132">[このページ](../develop/install-the-tools.md)の「イマーシブヘッドセットのインストールチェックリスト」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b338-132">See the installation checklist for immersive headsets on [this page](../develop/install-the-tools.md).</span></span>

* <span data-ttu-id="7b338-133">このチュートリアルには[Unity 2017.2.1 p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)が必要です</span><span class="sxs-lookup"><span data-stu-id="7b338-133">This tutorial requires [Unity 2017.2.1p2](https://beta.unity3d.com/download/1dc514532f08/UnityDownloadAssistant-2017.2.1p2.exe)</span></span>

### <a name="project-files"></a><span data-ttu-id="7b338-134">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="7b338-134">Project files</span></span>

* <span data-ttu-id="7b338-135">プロジェクトに必要な[ファイルをダウンロード](https://github.com/Microsoft/MixedReality213/archive/master.zip)し、ファイルをデスクトップに抽出します。</span><span class="sxs-lookup"><span data-stu-id="7b338-135">[Download the files](https://github.com/Microsoft/MixedReality213/archive/master.zip) required by the project and extract the files to the Desktop.</span></span>

>[!NOTE]
><span data-ttu-id="7b338-136">ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/MixedReality213)ます。</span><span class="sxs-lookup"><span data-stu-id="7b338-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/MixedReality213).</span></span>

## <a name="unity-setup"></a><span data-ttu-id="7b338-137">Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="7b338-137">Unity setup</span></span>

>[!VIDEO https://www.youtube.com/embed/cBAOALaHys4]

### <a name="objectives"></a><span data-ttu-id="7b338-138">目標</span><span class="sxs-lookup"><span data-stu-id="7b338-138">Objectives</span></span>

* <span data-ttu-id="7b338-139">Windows Mixed Reality 開発用に Unity を最適化する</span><span class="sxs-lookup"><span data-stu-id="7b338-139">Optimize Unity for Windows Mixed Reality development</span></span>
* <span data-ttu-id="7b338-140">Mixed Reality カメラの設定</span><span class="sxs-lookup"><span data-stu-id="7b338-140">Setup Mixed Reality Camera</span></span>
* <span data-ttu-id="7b338-141">環境の設定</span><span class="sxs-lookup"><span data-stu-id="7b338-141">Setup environment</span></span>

### <a name="instructions"></a><span data-ttu-id="7b338-142">Instructions</span><span class="sxs-lookup"><span data-stu-id="7b338-142">Instructions</span></span>

* <span data-ttu-id="7b338-143">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="7b338-143">Start Unity.</span></span>
* <span data-ttu-id="7b338-144">**[Open (開く)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b338-144">Select **Open** .</span></span>
* <span data-ttu-id="7b338-145">デスクトップに移動し、以前に unarchived した **MixedReality213** フォルダーを探します。</span><span class="sxs-lookup"><span data-stu-id="7b338-145">Navigate to your Desktop and find the **MixedReality213-master** folder you previously unarchived.</span></span>
* <span data-ttu-id="7b338-146">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-146">Click **Select Folder** .</span></span>
* <span data-ttu-id="7b338-147">Unity がプロジェクトファイルの読み込みを完了すると、Unity エディターを表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7b338-147">Once Unity finishes loading project files, you will be able to see Unity editor.</span></span>
* <span data-ttu-id="7b338-148">Unity で、[ **ファイル > ビルド設定** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b338-148">In Unity, select **File > Build Settings** .</span></span>

    ![MR213_BuildSettings](images/mr213-buildsettings-450px.png)

* <span data-ttu-id="7b338-150">[ **プラットフォーム** ] ボックスの一覧の [ **ユニバーサル Windows プラットフォーム** ] を選択し、[ **プラットフォームの切り替え** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-150">Select **Universal Windows Platform** in the **Platform** list and click the **Switch Platform** button.</span></span>
* <span data-ttu-id="7b338-151">ターゲットデバイスを **任意のデバイス** に設定する</span><span class="sxs-lookup"><span data-stu-id="7b338-151">Set Target Device to **Any device**</span></span>
* <span data-ttu-id="7b338-152">ビルドの種類を **D3D** に設定</span><span class="sxs-lookup"><span data-stu-id="7b338-152">Set Build Type to **D3D**</span></span>
* <span data-ttu-id="7b338-153">SDK を **最新のインストール済み** に設定する</span><span class="sxs-lookup"><span data-stu-id="7b338-153">Set SDK to **Latest Installed**</span></span>
* <span data-ttu-id="7b338-154">**Unity C# プロジェクト** を確認する</span><span class="sxs-lookup"><span data-stu-id="7b338-154">Check **Unity C# Projects**</span></span>
    * <span data-ttu-id="7b338-155">これにより、Unity プロジェクトを再構築しなくても、Visual Studio プロジェクトでスクリプトファイルを変更できます。</span><span class="sxs-lookup"><span data-stu-id="7b338-155">This allows you modify script files in the Visual Studio project without rebuilding Unity project.</span></span>
* <span data-ttu-id="7b338-156">[ **プレーヤーの設定** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-156">Click **Player Settings** .</span></span>
* <span data-ttu-id="7b338-157">[ **インスペクター** ] パネルで、下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="7b338-157">In the **Inspector** panel, scroll down to the bottom</span></span>
* <span data-ttu-id="7b338-158">XR の設定で、[ **Virtual Reality がサポートされる** ] をオンにします。</span><span class="sxs-lookup"><span data-stu-id="7b338-158">In XR Settings, check **Virtual Reality Supported**</span></span>
* <span data-ttu-id="7b338-159">[Virtual Reality Sdk] で、[ **Windows Mixed reality** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b338-159">Under Virtual Reality SDKs, select **Windows Mixed Reality**</span></span>

    ![MR213_XRSettings](images/mr213-xrsettings-500px.png)

* <span data-ttu-id="7b338-161">**ビルドの設定** ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="7b338-161">Close **Build Settings** window.</span></span>

### <a name="project-structure"></a><span data-ttu-id="7b338-162">プロジェクト構造</span><span class="sxs-lookup"><span data-stu-id="7b338-162">Project structure</span></span>

<span data-ttu-id="7b338-163">このチュートリアルでは **[、Mixed Reality Toolkit-Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** を使用します。</span><span class="sxs-lookup"><span data-stu-id="7b338-163">This tutorial uses **[Mixed Reality Toolkit - Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)** .</span></span> <span data-ttu-id="7b338-164">リリースは [このページ](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="7b338-164">You can find the releases on [this page](https://github.com/Microsoft/MixedRealityToolkit-Unity/releases).</span></span>

![ProjectStructure](images/mr213-projectstructure-650px.png)

<span data-ttu-id="7b338-166">**参照のための完了したシーン**</span><span class="sxs-lookup"><span data-stu-id="7b338-166">**Completed scenes for your reference**</span></span>

* <span data-ttu-id="7b338-167">[ **シーン** ] フォルダーの下に2つの Unity シーンが完成していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="7b338-167">You will find two completed Unity scenes under **Scenes** folder.</span></span>
    * <span data-ttu-id="7b338-168">**MixedReality213** : 1 つのブラシを使用した完成したシーン</span><span class="sxs-lookup"><span data-stu-id="7b338-168">**MixedReality213** : Completed scene with single brush</span></span>
    * <span data-ttu-id="7b338-169">**MixedReality213Advanced** : 複数のブラシを使用した高度なデザインのための完成したシーン</span><span class="sxs-lookup"><span data-stu-id="7b338-169">**MixedReality213Advanced** : Completed scene for advanced design with multiple brushes</span></span>

<span data-ttu-id="7b338-170">**チュートリアルの新しいシーンの設定**</span><span class="sxs-lookup"><span data-stu-id="7b338-170">**New Scene setup for the tutorial**</span></span>

* <span data-ttu-id="7b338-171">Unity で、[ **ファイル > 新しいシーン** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-171">In Unity, click **File > New Scene**</span></span>
* <span data-ttu-id="7b338-172">**メインカメラ** と **指向性ライト** の削除</span><span class="sxs-lookup"><span data-stu-id="7b338-172">Delete **Main Camera** and **Directional Light**</span></span>
* <span data-ttu-id="7b338-173">[ **プロジェクト] パネル** で、次の prefabs を検索し、[ **階層** ] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7b338-173">From the **Project panel** , search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="7b338-174">Assets/HoloToolkit/Input/Prefabs/ **MixedRealityCamera**</span><span class="sxs-lookup"><span data-stu-id="7b338-174">Assets/HoloToolkit/Input/Prefabs/ **MixedRealityCamera**</span></span>
    * <span data-ttu-id="7b338-175">Assets/AppPrefabs/ **Environment**</span><span class="sxs-lookup"><span data-stu-id="7b338-175">Assets/AppPrefabs/ **Environment**</span></span>

    ![カメラと環境](images/mr213-cameraenvironment-300px.jpg)

* <span data-ttu-id="7b338-177">Mixed Reality Toolkit には、次の2つのカメラ prefabs があります。</span><span class="sxs-lookup"><span data-stu-id="7b338-177">There are two camera prefabs in Mixed Reality Toolkit:</span></span>
    * <span data-ttu-id="7b338-178">**MixedRealityCamera** : カメラのみ</span><span class="sxs-lookup"><span data-stu-id="7b338-178">**MixedRealityCamera.prefab** : Camera only</span></span>
    * <span data-ttu-id="7b338-179">**MixedRealityCameraParent** : カメラ + テレの境界線</span><span class="sxs-lookup"><span data-stu-id="7b338-179">**MixedRealityCameraParent.prefab** : Camera + Teleportation + Boundary</span></span>
    * <span data-ttu-id="7b338-180">このチュートリアルでは、 **MixedRealityCamera** 機能を使用せずに、この機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="7b338-180">In this tutorial, we will use **MixedRealityCamera** without teleportation feature.</span></span> <span data-ttu-id="7b338-181">このため、基本的なフロアを含む単純な **環境** prefab を追加し、ユーザーが接地できるようにしました。</span><span class="sxs-lookup"><span data-stu-id="7b338-181">Because of this, we added simple **Environment** prefab which contains a basic floor to make the user feel grounded.</span></span>
    * <span data-ttu-id="7b338-182">**MixedRealityCameraParent** を使用した電話の詳細については、 [上級設計と locomotion](#advanced-design---teleportation-and-locomotion)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b338-182">To learn more about the teleportation with **MixedRealityCameraParent** , see [Advanced design - Teleportation and locomotion](#advanced-design---teleportation-and-locomotion)</span></span>

<span data-ttu-id="7b338-183">**スカイボックスのセットアップ**</span><span class="sxs-lookup"><span data-stu-id="7b338-183">**Skybox setup**</span></span>

* <span data-ttu-id="7b338-184">[ **ウィンドウ > 照明 > 設定** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-184">Click **Window > Lighting > Settings**</span></span>
* <span data-ttu-id="7b338-185">[ **スカイボックス素材] フィールド** の右側にある円をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-185">Click the circle on the right side of the **Skybox Material field**</span></span>
* <span data-ttu-id="7b338-186">「Gray」と入力し、[ **SkyboxGray** (Assets/AppPrefabs/Support/マテリアル/SkyboxGray)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b338-186">Type in ‘gray’ and select **SkyboxGray** (Assets/AppPrefabs/Support/Materials/SkyboxGray.mat)</span></span>

    ![スカイボックスの設定](images/mr123-skyboxsetting-400px.jpg)

* <span data-ttu-id="7b338-188">**スカイ** ボックスをチェックして、割り当てられている灰色のグラデーションスカイボックスを確認できるようにします</span><span class="sxs-lookup"><span data-stu-id="7b338-188">Check **Skybox** option to be able to see assigned gray gradient skybox</span></span>

    ![スカイボックスの切り替えオプション](images/mr213-skyboxcheck-400px.jpg)

* <span data-ttu-id="7b338-190">MixedRealityCamera、Environment、および gray スカイボックスのシーンは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="7b338-190">The scene with MixedRealityCamera, Environment and gray skybox will look like this.</span></span>

    ![MixedReality213 環境](images/mr213-environment-600px.jpg)

* <span data-ttu-id="7b338-192">[ **ファイル > をクリックしてシーンを保存** ]</span><span class="sxs-lookup"><span data-stu-id="7b338-192">Click **File > Save Scene as**</span></span>
* <span data-ttu-id="7b338-193">シーンを任意の名前でシーンフォルダーに **保存** する</span><span class="sxs-lookup"><span data-stu-id="7b338-193">**Save** your scene under Scenes folder with any name</span></span>

## <a name="chapter-1---controller-visualization"></a><span data-ttu-id="7b338-194">第1章-コントローラーの視覚化</span><span class="sxs-lookup"><span data-stu-id="7b338-194">Chapter 1 - Controller visualization</span></span>

>[!VIDEO https://www.youtube.com/embed/Kw0bf5NqyRg]

### <a name="objectives"></a><span data-ttu-id="7b338-195">目標</span><span class="sxs-lookup"><span data-stu-id="7b338-195">Objectives</span></span>

* <span data-ttu-id="7b338-196">Unity のゲームモードと実行時にモーションコントローラーモデルをレンダリングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-196">Learn how to render motion controller models in Unity's game mode and at runtime.</span></span>

<span data-ttu-id="7b338-197">Windows Mixed Reality は、コントローラーを視覚化するためのアニメーションコントローラーモデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="7b338-197">Windows Mixed Reality provides an animated controller model for controller visualization.</span></span> <span data-ttu-id="7b338-198">アプリでコントローラーを視覚化するには、いくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="7b338-198">There are several approaches you can take for controller visualization in your app:</span></span>

* <span data-ttu-id="7b338-199">既定-変更せずに既定のコントローラーを使用する</span><span class="sxs-lookup"><span data-stu-id="7b338-199">Default - Using default controller without modification</span></span>
* <span data-ttu-id="7b338-200">ハイブリッド-既定のコントローラーを使用しますが、一部の要素または UI コンポーネントのオーバーレイをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="7b338-200">Hybrid - Using default controller, but customizing some of its elements or overlaying UI components</span></span>
* <span data-ttu-id="7b338-201">置換-コントローラー用にカスタマイズした独自の3D モデルを使用する</span><span class="sxs-lookup"><span data-stu-id="7b338-201">Replacement - Using your own customized 3D model for the controller</span></span>

<span data-ttu-id="7b338-202">この章では、これらのコントローラーのカスタマイズの例について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-202">In this chapter, we will learn about the examples of these controller customizations.</span></span>

### <a name="instructions"></a><span data-ttu-id="7b338-203">Instructions</span><span class="sxs-lookup"><span data-stu-id="7b338-203">Instructions</span></span>

* <span data-ttu-id="7b338-204">[ **プロジェクト** ] パネルで、検索ボックスに「 **motioncontrollers** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="7b338-204">In the **Project** panel, type **MotionControllers** in the search box .</span></span> <span data-ttu-id="7b338-205">また、Assets/HoloToolkit/Input/Prefabs/で見つけることもできます。</span><span class="sxs-lookup"><span data-stu-id="7b338-205">You can also find it under Assets/HoloToolkit/Input/Prefabs/.</span></span>
* <span data-ttu-id="7b338-206">**Motioncontrollers** prefab を [ **階層** ] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7b338-206">Drag the **MotionControllers** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7b338-207">[ **階層** ] パネルで、 **motioncontrollers** prefab をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-207">Click on the **MotionControllers** prefab in the **Hierarchy** panel.</span></span>

<span data-ttu-id="7b338-208">**MotionControllers prefab**</span><span class="sxs-lookup"><span data-stu-id="7b338-208">**MotionControllers prefab**</span></span>

<span data-ttu-id="7b338-209">**Motioncontrollers** prefab には、代替コントローラーモデルのスロットを提供する **Motioncontrollers ビジュアライザー** スクリプトが用意されています。</span><span class="sxs-lookup"><span data-stu-id="7b338-209">**MotionControllers** prefab has a **MotionControllerVisualizer** script which provides the slots for alternate controller models.</span></span> <span data-ttu-id="7b338-210">独自のカスタム3D モデル (手動または剣) を割り当て、[常に代替の左/右モデルを使用する] チェックボックスをオンにすると、既定のモデルの代わりにそれらが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-210">If you assign your own custom 3D models such as a hand or a sword and check 'Always Use Alternate Left/Right Model', you will see them instead of the default model.</span></span> <span data-ttu-id="7b338-211">このスロットを4章で使用して、コントローラーモデルをブラシで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="7b338-211">We will use this slot in Chapter 4 to replace the controller model with a brush.</span></span>

![MR213_ControllerVisualizer](images/mr213-controllervisualizer-600px.png)

<span data-ttu-id="7b338-213">**手順**</span><span class="sxs-lookup"><span data-stu-id="7b338-213">**Instructions**</span></span>

* <span data-ttu-id="7b338-214">[ **インスペクター** ] パネルで、[ **Motionコントローラービジュアライザー** スクリプト] をダブルクリックして、Visual Studio のコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="7b338-214">In the **Inspector** panel, double click **MotionControllerVisualizer** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="7b338-215">**Motionコントローラービジュアライザースクリプト**</span><span class="sxs-lookup"><span data-stu-id="7b338-215">**MotionControllerVisualizer script**</span></span>

<span data-ttu-id="7b338-216">**Motioncontroller ビジュアライザー** と **Motioncontroller info** クラスは、既定のコントローラーモデルにアクセス & 変更する手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="7b338-216">The **MotionControllerVisualizer** and **MotionControllerInfo** classes provide the means to access & modify the default controller models.</span></span> <span data-ttu-id="7b338-217">**Motioncontroller ビジュアライザー** は、Unity の **interactionsourcedetected** イベントをサブスクライブし、検出されたときにコントローラーモデルを自動的にインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="7b338-217">**MotionControllerVisualizer** subscribes to Unity's **InteractionSourceDetected** event and automatically instantiates controller models when they are found.</span></span>

```cs
protected override void Awake()
{
    ...
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    ...
}
```

<span data-ttu-id="7b338-218">コントローラーモデルは、 [glTF 仕様](https://github.com/KhronosGroup/glTF)に従って配信されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-218">The controller models are delivered according to [the glTF specification](https://github.com/KhronosGroup/glTF).</span></span> <span data-ttu-id="7b338-219">この形式は、一般的な形式を提供するために作成されており、3D アセットの送信とアンパックの背後にあるプロセスが改善されています。</span><span class="sxs-lookup"><span data-stu-id="7b338-219">This format has been created to provide a common format, while improving the process behind transmitting and unpacking 3D assets.</span></span> <span data-ttu-id="7b338-220">この場合、ユーザーの操作を可能な限りシームレスにするため、実行時にコントローラーモデルを取得して読み込む必要があります。また、ユーザーが使用しているモーションコントローラーのバージョンが保証されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="7b338-220">In this case, we need to retrieve and load the controller models at runtime, as we want to make the user's experience as seamless as possible, and it's not guaranteed which version of the motion controllers the user might be using.</span></span> <span data-ttu-id="7b338-221">このコースでは、Mixed Reality Toolkit を使用して、Khronos グループの [Unitygltf プロジェクト](https://github.com/KhronosGroup/UnityGLTF)のバージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b338-221">This course, via the Mixed Reality Toolkit, uses a version of the Khronos Group's [UnityGLTF project](https://github.com/KhronosGroup/UnityGLTF).</span></span>

<span data-ttu-id="7b338-222">コントローラーが配信されると、スクリプトは **Motioncontroller info** を使用して特定のコントローラー要素の変換を見つけることができるため、適切に配置できます。</span><span class="sxs-lookup"><span data-stu-id="7b338-222">Once the controller has been delivered, scripts can use **MotionControllerInfo** to find the transforms for specific controller elements so they can correctly position themselves.</span></span>

<span data-ttu-id="7b338-223">この後の章では、これらのスクリプトを使用して、UI 要素をコントローラーにアタッチする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-223">In a later chapter, we will learn how to use these scripts to attach UI elements to the controllers.</span></span>

<span data-ttu-id="7b338-224">*スクリプトによっては、#if のあるコードブロックを見つけることができます **。UNITY_EDITOR** または **UNITY_WSA** 。これらのコードブロックは、Windows に配置するときに UWP ランタイムでのみ実行されます。これは、Unity エディターと UWP アプリのランタイムで使用される Api のセットが異なるためです。*</span><span class="sxs-lookup"><span data-stu-id="7b338-224">*In some scripts, you will find code blocks with **#if !UNITY_EDITOR** or **UNITY_WSA** . These code blocks run only on the UWP runtime when you deploy to Windows. This is because the set of APIs used by the Unity editor and the UWP app runtime are different.*</span></span>

* <span data-ttu-id="7b338-225">シーンを **保存** し、[ **再生** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-225">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="7b338-226">ヘッドセットには、モーションコントローラーを含むシーンを表示できます。</span><span class="sxs-lookup"><span data-stu-id="7b338-226">You will be able to see the scene with motion controllers in your headset.</span></span> <span data-ttu-id="7b338-227">ボタンのクリック、サムスティックの移動、およびタッチパッドのタッチの強調表示に関する詳細なアニメーションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="7b338-227">You can see detailed animations for button clicks, thumbstick movement, and touchpad touch highlighting.</span></span>

![視覚エフェクトの既定値 MR213_Controller](images/mr213-controllervisualizationdefault-500px.jpg)

## <a name="chapter-2---attaching-ui-elements-to-the-controller"></a><span data-ttu-id="7b338-229">第2章-UI 要素のコントローラーへのアタッチ</span><span class="sxs-lookup"><span data-stu-id="7b338-229">Chapter 2 - Attaching UI elements to the controller</span></span>

>[!VIDEO https://www.youtube.com/embed/e-mLlwmTzJo]

### <a name="objectives"></a><span data-ttu-id="7b338-230">目標</span><span class="sxs-lookup"><span data-stu-id="7b338-230">Objectives</span></span>

* <span data-ttu-id="7b338-231">モーションコントローラーの要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-231">Learn about the elements of the motion controllers</span></span>
* <span data-ttu-id="7b338-232">コントローラーの特定の部分にオブジェクトをアタッチする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-232">Learn how to attach objects to specific parts of the controllers</span></span>

<span data-ttu-id="7b338-233">この章では、ユーザーがいつでも簡単にアクセスして操作できるコントローラーにユーザーインターフェイス要素を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-233">In this chapter, you will learn how to add user interface elements to the controller which the user can easily access and manipulate at anytime.</span></span> <span data-ttu-id="7b338-234">また、タッチパッド入力を使用して簡単なカラーピッカー UI を追加する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-234">You will also learn how to add a simple color picker UI using the touchpad input.</span></span>

### <a name="instructions"></a><span data-ttu-id="7b338-235">Instructions</span><span class="sxs-lookup"><span data-stu-id="7b338-235">Instructions</span></span>

* <span data-ttu-id="7b338-236">[ **プロジェクト** ] パネルで、 **Motionコントローラー情報** スクリプトを検索します。</span><span class="sxs-lookup"><span data-stu-id="7b338-236">In the **Project** panel, search **MotionControllerInfo** script.</span></span>
* <span data-ttu-id="7b338-237">検索結果から [ **Motionコントローラー情報** スクリプト] をダブルクリックして、Visual Studio のコードを確認します。</span><span class="sxs-lookup"><span data-stu-id="7b338-237">From the search result, double click **MotionControllerInfo** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="7b338-238">**Motionコントローラー情報スクリプト**</span><span class="sxs-lookup"><span data-stu-id="7b338-238">**MotionControllerInfo script**</span></span>

<span data-ttu-id="7b338-239">最初の手順は、UI をアタッチするコントローラーの要素を選択することです。</span><span class="sxs-lookup"><span data-stu-id="7b338-239">The first step is to choose which element of the controller you want the UI to attach to.</span></span> <span data-ttu-id="7b338-240">これらの要素は、 **MotionControllerInfo.cs** の **コントローラー** で定義されています。</span><span class="sxs-lookup"><span data-stu-id="7b338-240">These elements are defined in **ControllerElementEnum** in **MotionControllerInfo.cs** .</span></span>

![MR213 Motionコントローラー要素](images/mr213-motioncontrollerelements-1000px.jpg)

* <span data-ttu-id="7b338-242">**ホーム**</span><span class="sxs-lookup"><span data-stu-id="7b338-242">**Home**</span></span>
* <span data-ttu-id="7b338-243">**Menu**</span><span class="sxs-lookup"><span data-stu-id="7b338-243">**Menu**</span></span>
* <span data-ttu-id="7b338-244">**つかん**</span><span class="sxs-lookup"><span data-stu-id="7b338-244">**Grasp**</span></span>
* <span data-ttu-id="7b338-245">**スティック**</span><span class="sxs-lookup"><span data-stu-id="7b338-245">**Thumbstick**</span></span>
* <span data-ttu-id="7b338-246">**Select**</span><span class="sxs-lookup"><span data-stu-id="7b338-246">**Select**</span></span>
* <span data-ttu-id="7b338-247">**タッチパッド**</span><span class="sxs-lookup"><span data-stu-id="7b338-247">**Touchpad**</span></span>
* <span data-ttu-id="7b338-248">**ポインティング** 型: この要素は、方向をポイントするコントローラーの先端を表します。</span><span class="sxs-lookup"><span data-stu-id="7b338-248">**Pointing pose** – this element represents the tip of the controller pointing forward direction.</span></span>

<span data-ttu-id="7b338-249">**手順**</span><span class="sxs-lookup"><span data-stu-id="7b338-249">**Instructions**</span></span>

* <span data-ttu-id="7b338-250">[ **プロジェクト** ] パネルで、[ **attachtocontroller** スクリプト] を検索します。</span><span class="sxs-lookup"><span data-stu-id="7b338-250">In the **Project** panel, search **AttachToController** script.</span></span>
* <span data-ttu-id="7b338-251">検索結果から、[ **Attachtocontroller** script] をダブルクリックして Visual Studio のコードを確認します。</span><span class="sxs-lookup"><span data-stu-id="7b338-251">From the search result, double click **AttachToController** script to see the code in Visual Studio.</span></span>

<span data-ttu-id="7b338-252">**AttachToController スクリプト**</span><span class="sxs-lookup"><span data-stu-id="7b338-252">**AttachToController script**</span></span>

<span data-ttu-id="7b338-253">**Attachtocontroller** スクリプトを使用すると、任意のオブジェクトを、指定したコントローラーのききと要素に簡単にアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="7b338-253">The **AttachToController** script provides a simple way to attach any objects to a specified controller handedness and element.</span></span>

<span data-ttu-id="7b338-254">**Attachelementtocontroller ()** で、</span><span class="sxs-lookup"><span data-stu-id="7b338-254">In **AttachElementToController()** ,</span></span>

* <span data-ttu-id="7b338-255">**Motionコントローラー** を使用してきき手をチェックする</span><span class="sxs-lookup"><span data-stu-id="7b338-255">Check handedness using **MotionControllerInfo.Handedness**</span></span>
* <span data-ttu-id="7b338-256">**MotionTryGetElement ()** を使用して、コントローラーの特定の要素を取得します。</span><span class="sxs-lookup"><span data-stu-id="7b338-256">Get specific element of the controller using **MotionControllerInfo.TryGetElement()**</span></span>
* <span data-ttu-id="7b338-257">コントローラーモデルから要素の変換を取得した後、その下にあるオブジェクトを親として設定し、オブジェクトのローカル位置 & 回転を0に設定します。</span><span class="sxs-lookup"><span data-stu-id="7b338-257">After retrieving the element's transform from the controller model, parent the object under it and set object's local position & rotation to zero.</span></span>

```cs
public MotionControllerInfo.ControllerElementEnum Element { get { return element; } }

private void AttachElementToController(MotionControllerInfo newController)
{
     if (!IsAttached && newController.Handedness == handedness)
     {
          if (!newController.TryGetElement(element, out elementTransform))
          {
               Debug.LogError("Unable to find element of type " + element + " under controller " + newController.ControllerParent.name + "; not attaching.");
               return;
          }

          controller = newController;

          SetChildrenActive(true);

          // Parent ourselves under the element and set our offsets
          transform.parent = elementTransform;
          transform.localPosition = positionOffset;
          transform.localEulerAngles = rotationOffset;
          if (setScaleOnAttach)
          {
               transform.localScale = scale;
          }

          // Announce that we're attached
          OnAttachToController();
          IsAttached = true;
     }
}
```

<span data-ttu-id="7b338-258">**Attachtocontroller** スクリプトを使用する最も簡単な方法は、ColorPickerWheel の場合と同様に、このスクリプトを継承することです **。**</span><span class="sxs-lookup"><span data-stu-id="7b338-258">The simplest way to use **AttachToController** script is to inherit from it, as we've done in the case of **ColorPickerWheel.**</span></span> <span data-ttu-id="7b338-259">**Onattachtocontroller** 関数と **OnDetachFromController** 関数をオーバーライドするだけで、コントローラーが検出または切断されたときにセットアップ/ブレークダウンを実行できます。</span><span class="sxs-lookup"><span data-stu-id="7b338-259">Simply override the **OnAttachToController** and **OnDetachFromController** functions to perform your setup / breakdown when the controller is detected / disconnected.</span></span>

<span data-ttu-id="7b338-260">**手順**</span><span class="sxs-lookup"><span data-stu-id="7b338-260">**Instructions**</span></span>

* <span data-ttu-id="7b338-261">[ **プロジェクト** ] パネルで、検索ボックスに「 **ColorPickerWheel** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="7b338-261">In the **Project** panel, type in the search box **ColorPickerWheel** .</span></span> <span data-ttu-id="7b338-262">[Assets/AppPrefabs/] の下にも表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-262">You can also find it under Assets/AppPrefabs/.</span></span>
* <span data-ttu-id="7b338-263">**ColorPickerWheel** prefab を [ **階層** ] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7b338-263">Drag **ColorPickerWheel** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7b338-264">[ **階層** ] パネルの [ **ColorPickerWheel** prefab] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-264">Click the **ColorPickerWheel** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7b338-265">[ **インスペクター** ] パネルで [ **ColorPickerWheel** Script] をダブルクリックして、Visual Studio でコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="7b338-265">In the **Inspector** panel, double click **ColorPickerWheel** Script to see the code in Visual Studio.</span></span>

![ColorPickerWheel prefab](images/mr213-colorpickerwheel-1000px.jpg)

<span data-ttu-id="7b338-267">**ColorPickerWheel スクリプト**</span><span class="sxs-lookup"><span data-stu-id="7b338-267">**ColorPickerWheel script**</span></span>

<span data-ttu-id="7b338-268">**ColorPickerWheel** は **attachtocontroller** を継承するため **Handedness** 、Inspector と **要素** が **インスペクター** パネルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-268">Since **ColorPickerWheel** inherits **AttachToController** , it shows **Handedness** and **Element** in the **Inspector** panel.</span></span> <span data-ttu-id="7b338-269">左側のコントローラーのタッチパッド要素に UI をアタッチします。</span><span class="sxs-lookup"><span data-stu-id="7b338-269">We'll be attaching the UI to the Touchpad element on the left controller.</span></span>

![ColorPickerWheel スクリプト](images/mr213-attachtocontroller-300px.jpg)

<span data-ttu-id="7b338-271">**ColorPickerWheel** は、 **Onattachtocontroller** と **OnDetachFromController** をオーバーライドして入力イベントをサブスクライブします。これは、タッチパッド入力による色の選択の次の章で使用されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-271">**ColorPickerWheel** overrides the **OnAttachToController** and **OnDetachFromController** to subscribe to the input event which will be used in next chapter for color selection with touchpad input.</span></span>

```cs
public class ColorPickerWheel : AttachToController, IPointerTarget
{
    protected override void OnAttachToController()
    {
        // Subscribe to input now that we're parented under the controller
        InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
    }

    protected override void OnDetachFromController()
    {
        Visible = false;

        // Unsubscribe from input now that we've detached from the controller
        InteractionManager.InteractionSourceUpdated -= InteractionSourceUpdated;
    }
    ...
}
```

* <span data-ttu-id="7b338-272">シーンを **保存** し、[ **再生** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-272">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="7b338-273">**オブジェクトをコントローラーにアタッチするための別の方法**</span><span class="sxs-lookup"><span data-stu-id="7b338-273">**Alternative method for attaching objects to the controllers**</span></span>

<span data-ttu-id="7b338-274">スクリプトは **attachtocontroller** から継承し、 **onattachtocontroller** をオーバーライドすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7b338-274">We recommend that your scripts inherit from **AttachToController** and override **OnAttachToController** .</span></span> <span data-ttu-id="7b338-275">ただし、これは常に可能であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="7b338-275">However, this may not always be possible.</span></span> <span data-ttu-id="7b338-276">別の方法として、スタンドアロンコンポーネントとして使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="7b338-276">An alternative is using it as a standalone component.</span></span> <span data-ttu-id="7b338-277">これは、スクリプトをリファクタリングせずに既存の prefab をコントローラーにアタッチする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="7b338-277">This can be useful when you want to attach an existing prefab to a controller without refactoring your scripts.</span></span> <span data-ttu-id="7b338-278">セットアップを実行する前に、クラスで IsAttached が true に設定されるのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="7b338-278">Simply have your class wait for IsAttached to be set to true before performing any setup.</span></span> <span data-ttu-id="7b338-279">これを行う最も簡単な方法は、' Start ' にコルーチンを使用することです。</span><span class="sxs-lookup"><span data-stu-id="7b338-279">The simplest way to do this is by using a coroutine for 'Start.'</span></span>

```cs
private IEnumerator Start() {
    AttachToController attach = gameObject.GetComponent<AttachToController>();

    while (!attach.IsAttached) {
        yield return null;
    }

    // Perform setup here
}
```

## <a name="chapter-3---working-with-touchpad-input"></a><span data-ttu-id="7b338-280">第3章: タッチパッド入力の操作</span><span class="sxs-lookup"><span data-stu-id="7b338-280">Chapter 3 - Working with touchpad input</span></span>

>[!VIDEO https://www.youtube.com/embed/SUyw0kxZPFw]

### <a name="objectives"></a><span data-ttu-id="7b338-281">目標</span><span class="sxs-lookup"><span data-stu-id="7b338-281">Objectives</span></span>

* <span data-ttu-id="7b338-282">タッチパッド入力データイベントを取得する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="7b338-282">Learn how to get touchpad input data events</span></span>
* <span data-ttu-id="7b338-283">タッチパッドの軸の位置情報をアプリのエクスペリエンスに使用する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="7b338-283">Learn how to use touchpad axis position information for your app experience</span></span>

### <a name="instructions"></a><span data-ttu-id="7b338-284">Instructions</span><span class="sxs-lookup"><span data-stu-id="7b338-284">Instructions</span></span>

* <span data-ttu-id="7b338-285">[ **階層** ] パネルで、[ **ColorPickerWheel** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-285">In the **Hierarchy** panel, click **ColorPickerWheel**</span></span>
* <span data-ttu-id="7b338-286">[ **インスペクター** ] パネルの [ **アニメーター** ] の下で、[ **ColorPickerWheelController** ] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-286">In the **Inspector** panel, under **Animator** , double click **ColorPickerWheelController**</span></span>
* <span data-ttu-id="7b338-287">[ **アニメーター** ] タブが開いていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="7b338-287">You will be able to see **Animator** tab opened</span></span>

<span data-ttu-id="7b338-288">**Unity のアニメーションコントローラーを使用した UI の表示/非表示**</span><span class="sxs-lookup"><span data-stu-id="7b338-288">**Showing/hiding UI with Unity's Animation controller**</span></span>

<span data-ttu-id="7b338-289">アニメーションを使用して **ColorPickerWheel** UI の表示と非表示を切り替えるには、 [Unity のアニメーションシステム](https://docs.unity3d.com/Manual/AnimationOverview.html)を使用します。</span><span class="sxs-lookup"><span data-stu-id="7b338-289">To show and hide the **ColorPickerWheel** UI with animation, we are using [Unity's animation system](https://docs.unity3d.com/Manual/AnimationOverview.html).</span></span> <span data-ttu-id="7b338-290">**ColorPickerWheel** の **Visible** プロパティを true または false に設定すると、アニメーショントリガーの **表示** と **非表示が切り替え** られます。</span><span class="sxs-lookup"><span data-stu-id="7b338-290">Setting the **ColorPickerWheel** 's **Visible** property to true or false triggers **Show** and **Hide** animation triggers.</span></span> <span data-ttu-id="7b338-291">**表示** と **非表示** のパラメーターは、 **ColorPickerWheelController** animation コントローラーで定義されています。</span><span class="sxs-lookup"><span data-stu-id="7b338-291">**Show** and **Hide** parameters are defined in the **ColorPickerWheelController** animation controller.</span></span>

![Unity アニメーションコントローラー](images/mr123-animationcontroller-550px.jpg)

<span data-ttu-id="7b338-293">**手順**</span><span class="sxs-lookup"><span data-stu-id="7b338-293">**Instructions**</span></span>

* <span data-ttu-id="7b338-294">[ **階層** ] パネルで [ **ColorPickerWheel** prefab] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b338-294">In the **Hierarchy** panel, select **ColorPickerWheel** prefab</span></span>
* <span data-ttu-id="7b338-295">[ **インスペクター** ] パネルで [ **ColorPickerWheel** script] をダブルクリックして、Visual Studio でコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="7b338-295">In the **Inspector** panel, double click **ColorPickerWheel** script to see the code in the Visual Studio</span></span>

<span data-ttu-id="7b338-296">**ColorPickerWheel スクリプト**</span><span class="sxs-lookup"><span data-stu-id="7b338-296">**ColorPickerWheel script**</span></span>

<span data-ttu-id="7b338-297">**ColorPickerWheel** は、タッチパッドイベントをリッスンするために、Unity の **Interactionsourceupdated** イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="7b338-297">**ColorPickerWheel** subscribes to Unity's **InteractionSourceUpdated** event to listen for touchpad events.</span></span>

<span data-ttu-id="7b338-298">**Interactionsourceupdated ()** では、スクリプトはまず次のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="7b338-298">In **InteractionSourceUpdated()** , the script first checks to ensure that it:</span></span>

* <span data-ttu-id="7b338-299">は、実際にはタッチパッドイベント (obj. state. **touchpadTouched** )</span><span class="sxs-lookup"><span data-stu-id="7b338-299">is actually a touchpad event (obj.state. **touchpadTouched** )</span></span>
* <span data-ttu-id="7b338-300">左のコントローラー (obj. state. source. **きき手** )</span><span class="sxs-lookup"><span data-stu-id="7b338-300">originates from the left controller (obj.state.source. **handedness** )</span></span>

<span data-ttu-id="7b338-301">両方が true の場合、タッチパッドの位置 (obj. **touchpadPosition** ) は **selectorPosition** に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="7b338-301">If both are true, the touchpad position (obj.state. **touchpadPosition** ) is assigned to **selectorPosition** .</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness && obj.state.touchpadTouched)
    {
        Visible = true;
        selectorPosition = obj.state.touchpadPosition;
    }
}
```

<span data-ttu-id="7b338-302">**Update ()** では、 **visible** プロパティに基づいて、カラーピッカーのアニメーターコンポーネントでアニメーショントリガーの表示と非表示をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="7b338-302">In **Update()** , based on **visible** property, it triggers Show and Hide animation triggers in the color picker's animator component</span></span>

```cs
if (visible != visibleLastFrame)
{
    if (visible)
    {
        animator.SetTrigger("Show");
    }
    else
    {
        animator.SetTrigger("Hide");
    }
}
```

<span data-ttu-id="7b338-303">**Update ()** では、 **selectorPosition** を使用して、カラーホイールのメッシュ collider に射線をキャストします。これにより、UV 位置が返されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-303">In **Update()** , **selectorPosition** is used to cast a ray at the color wheel's mesh collider, which returns a UV position.</span></span> <span data-ttu-id="7b338-304">この位置を使用して、カラーホイールのテクスチャのピクセル座標と色の値を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="7b338-304">This position can then be used to find the pixel coordinate and color value of the color wheel's texture.</span></span> <span data-ttu-id="7b338-305">この値は、 **Selectedcolor** プロパティを使用して他のスクリプトからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7b338-305">This value is accessible to other scripts via the **SelectedColor** property.</span></span>

![カラーピッカーのホイール Raycasting](images/mr213-colorpickerwheel-raycast-700px.png)

```cs
...
    // Clamp selector position to a radius of 1
    Vector3 localPosition = new Vector3(selectorPosition.x * inputScale, 0.15f, selectorPosition.y * inputScale);
    if (localPosition.magnitude > 1)
    {
        localPosition = localPosition.normalized;
    }
    selectorTransform.localPosition = localPosition;

    // Raycast the wheel mesh and get its UV coordinates
    Vector3 raycastStart = selectorTransform.position + selectorTransform.up * 0.15f;
    RaycastHit hit;
    Debug.DrawLine(raycastStart, raycastStart - (selectorTransform.up * 0.25f));

    if (Physics.Raycast(raycastStart, -selectorTransform.up, out hit, 0.25f, 1 << colorWheelObject.layer, QueryTriggerInteraction.Ignore))
    {
        // Get pixel from the color wheel texture using UV coordinates
        Vector2 uv = hit.textureCoord;
        int pixelX = Mathf.FloorToInt(colorWheelTexture.width * uv.x);
        int pixelY = Mathf.FloorToInt(colorWheelTexture.height * uv.y);
        selectedColor = colorWheelTexture.GetPixel(pixelX, pixelY);
        selectedColor.a = 1f;
    }
    // Set the selector's color and blend it with white to make it visible on top of the wheel
    selectorRenderer.material.color = Color.Lerp (selectedColor, Color.white, 0.5f);
}
```

## <a name="chapter-4---overriding-controller-model"></a><span data-ttu-id="7b338-307">Chapter 4-コントローラーモデルのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="7b338-307">Chapter 4 - Overriding controller model</span></span>

>[!VIDEO https://www.youtube.com/embed/8gBFqA_DZ_U]

### <a name="objectives"></a><span data-ttu-id="7b338-308">目標</span><span class="sxs-lookup"><span data-stu-id="7b338-308">Objectives</span></span>

* <span data-ttu-id="7b338-309">カスタム3D モデルを使用してコントローラーモデルを上書きする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-309">Learn how to override the controller model with a custom 3D model.</span></span>

![MR213_BrushToolOverride](images/mr213-brushtooloverride-500px.jpg)

### <a name="instructions"></a><span data-ttu-id="7b338-311">Instructions</span><span class="sxs-lookup"><span data-stu-id="7b338-311">Instructions</span></span>

* <span data-ttu-id="7b338-312">[ **階層** ] パネルの [ **motioncontrollers** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-312">Click **MotionControllers** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7b338-313">[ **代替右コントローラー** ] フィールドの右側にある円をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-313">Click the circle on the right side of the **Alternate Right Controller** field.</span></span>
* <span data-ttu-id="7b338-314">**「BrushController** 」と入力し、結果から prefab を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b338-314">Type in **'BrushController** ' and select the prefab from the result.</span></span> <span data-ttu-id="7b338-315">これは Assets/AppPrefabs/ **BrushController** にあります。</span><span class="sxs-lookup"><span data-stu-id="7b338-315">You can find it under Assets/AppPrefabs/ **BrushController** .</span></span>
* <span data-ttu-id="7b338-316">**常に代替右モデルを使用することを確認する**</span><span class="sxs-lookup"><span data-stu-id="7b338-316">Check **Always Use Alternate Right Model**</span></span>

![MR213_BrushToolOverrideSlot](images/mr213-motioncontrollersoverride-700px.jpg)

<span data-ttu-id="7b338-318">**BrushController** prefab は、 **階層** パネルに含まれている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7b338-318">The **BrushController** prefab does not have to be included in the **Hierarchy** panel.</span></span> <span data-ttu-id="7b338-319">ただし、子コンポーネントを確認するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="7b338-319">However, to check out its child components:</span></span>

* <span data-ttu-id="7b338-320">[ **プロジェクト** ] パネルで、「 **BrushController** 」と入力し、[ **BrushController** prefab] を [ **階層** ] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7b338-320">In the **Project** panel, type in **BrushController** and drag **BrushController** prefab into the **Hierarchy** panel.</span></span>

![MR213_BrushTool_Prefab2](images/mr213-brushtool-prefab-1000px.jpg)

<span data-ttu-id="7b338-322">**Tip** コンポーネントは **BrushController** にあります。</span><span class="sxs-lookup"><span data-stu-id="7b338-322">You will find the **Tip** component in **BrushController** .</span></span> <span data-ttu-id="7b338-323">この変換を使用して、描画線を開始または停止します。</span><span class="sxs-lookup"><span data-stu-id="7b338-323">We will use its transform to start/stop drawing lines.</span></span>

* <span data-ttu-id="7b338-324">[ **階層** ] パネルから **BrushController** を削除します。</span><span class="sxs-lookup"><span data-stu-id="7b338-324">Delete the **BrushController** from the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7b338-325">シーンを **保存** し、[ **再生** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-325">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="7b338-326">ブラシモデルは、右側のモーションコントローラーに置き換えられていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="7b338-326">You will be able to see the brush model replaced the right-hand motion controller.</span></span>

## <a name="chapter-5---painting-with-select-input"></a><span data-ttu-id="7b338-327">Chapter 5-Select 入力による塗りつぶし</span><span class="sxs-lookup"><span data-stu-id="7b338-327">Chapter 5 - Painting with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/QTrYaMHIs7w]

### <a name="objectives"></a><span data-ttu-id="7b338-328">目標</span><span class="sxs-lookup"><span data-stu-id="7b338-328">Objectives</span></span>

* <span data-ttu-id="7b338-329">Select button イベントを使用して、線描画を開始および停止する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-329">Learn how to use the Select button event to start and stop a line drawing</span></span>

### <a name="instructions"></a><span data-ttu-id="7b338-330">Instructions</span><span class="sxs-lookup"><span data-stu-id="7b338-330">Instructions</span></span>

* <span data-ttu-id="7b338-331">[ **プロジェクト** ] パネルで **BrushController** prefab を検索します。</span><span class="sxs-lookup"><span data-stu-id="7b338-331">Search **BrushController** prefab in the **Project** panel.</span></span>
* <span data-ttu-id="7b338-332">[ **インスペクター** ] パネルで [ **BrushController** Script] をダブルクリックして、Visual Studio でコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="7b338-332">In the **Inspector** panel, double click **BrushController** Script to see the code in Visual Studio</span></span>

<span data-ttu-id="7b338-333">**BrushController スクリプト**</span><span class="sxs-lookup"><span data-stu-id="7b338-333">**BrushController script**</span></span>

<span data-ttu-id="7b338-334">**BrushController** は、InteractionManager の **Interactionsource押さ** れたイベントと **InteractionSourceReleased** イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="7b338-334">**BrushController** subscribes to the InteractionManager's **InteractionSourcePressed** and **InteractionSourceReleased** events.</span></span> <span data-ttu-id="7b338-335">**Interactionsourcepressed** れたイベントがトリガーされると、ブラシの **Draw** プロパティが true に設定されます。 **InteractionSourceReleased** イベントがトリガーされると、ブラシの **Draw** プロパティが false に設定されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-335">When **InteractionSourcePressed** event is triggered, the brush's **Draw** property is set to true; when **InteractionSourceReleased** event is triggered, the brush's **Draw** property is set to false.</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = true;
    }
}

private void InteractionSourceReleased(InteractionSourceReleasedEventArgs obj)
{
    if (obj.state.source.handedness == InteractionSourceHandedness.Right && obj.pressType == InteractionSourcePressType.Select)
    {
        Draw = false;
    }
}
```

<span data-ttu-id="7b338-336">**描画** が true に設定されている場合、ブラシはインスタンス化された Unity **LineRenderer** 内のポイントを生成します。</span><span class="sxs-lookup"><span data-stu-id="7b338-336">While **Draw** is set to true, the brush will generate points in an instantiated Unity **LineRenderer** .</span></span> <span data-ttu-id="7b338-337">この prefab への参照は、ブラシの **ストローク prefab** フィールドに保持されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-337">A reference to this prefab is kept in the brush's **Stroke Prefab** field.</span></span>

```cs
private IEnumerator DrawOverTime()
{
    // Get the position of the tip
    Vector3 lastPointPosition = tip.position;

    ...

    // Create a new brush stroke
    GameObject newStroke = Instantiate(strokePrefab);
    LineRenderer line = newStroke.GetComponent<LineRenderer>();
    newStroke.transform.position = startPosition;
    line.SetPosition(0, tip.position);
    float initialWidth = line.widthMultiplier;

    // Generate points in an instantiated Unity LineRenderer
    while (draw)
    {
        // Move the last point to the draw point position
        line.SetPosition(line.positionCount - 1, tip.position);
        line.material.color = colorPicker.SelectedColor;
        brushRenderer.material.color = colorPicker.SelectedColor;
        lastPointAddedTime = Time.unscaledTime;
        // Adjust the width between 1x and 2x width based on strength of trigger pull
        line.widthMultiplier = Mathf.Lerp(initialWidth, initialWidth * 2, width);

        if (Vector3.Distance(lastPointPosition, tip.position) > minPositionDelta || Time.unscaledTime > lastPointAddedTime + maxTimeDelta)
        {
            // Spawn a new point
            lastPointAddedTime = Time.unscaledTime;
            lastPointPosition = tip.position;
            line.positionCount += 1;
            line.SetPosition(line.positionCount - 1, lastPointPosition);
        }
        yield return null;
    }
}
```

<span data-ttu-id="7b338-338">カラーピッカーのホイール UI で現在選択されている色を使用するには、 **BrushController** が **ColorPickerWheel** オブジェクトへの参照を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b338-338">To use the currently selected color from the color picker wheel UI, **BrushController** needs to have a reference to the **ColorPickerWheel** object.</span></span> <span data-ttu-id="7b338-339">**BrushController** prefab は実行時に交換用コントローラーとしてインスタンス化されるため、シーン内のオブジェクトへの参照は実行時に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b338-339">Because the **BrushController** prefab is instantiated at runtime as a replacement controller, any references to objects in the scene will have to be set at runtime.</span></span> <span data-ttu-id="7b338-340">この例では、 **FindObjectOfType** を使用して **ColorPickerWheel** を検索します。</span><span class="sxs-lookup"><span data-stu-id="7b338-340">In this case we use **GameObject.FindObjectOfType** to locate the **ColorPickerWheel** :</span></span>

```cs
private void OnEnable()
{
    // Locate the ColorPickerWheel
    colorPicker = FindObjectOfType<ColorPickerWheel>();

    // Assign currently selected color to the brush’s material color
    brushRenderer.material.color = colorPicker.SelectedColor;
    ...
}
```

* <span data-ttu-id="7b338-341">シーンを **保存** し、[ **再生** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-341">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="7b338-342">右側のコントローラーの [選択] ボタンを使用して、線を描画し、塗りつぶすことができます。</span><span class="sxs-lookup"><span data-stu-id="7b338-342">You will be able to draw the lines and paint using the select button on the right-hand controller.</span></span>

## <a name="chapter-6---object-spawning-with-select-input"></a><span data-ttu-id="7b338-343">Chapter 6-Select 入力を使用したオブジェクトの生成</span><span class="sxs-lookup"><span data-stu-id="7b338-343">Chapter 6 - Object spawning with Select input</span></span>

>[!VIDEO https://www.youtube.com/embed/z4IxyzFHP0U]

### <a name="objectives"></a><span data-ttu-id="7b338-344">目標</span><span class="sxs-lookup"><span data-stu-id="7b338-344">Objectives</span></span>

* <span data-ttu-id="7b338-345">選択ボタンと表示ボタンの入力イベントを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-345">Learn how to use Select and Grasp button input events</span></span>
* <span data-ttu-id="7b338-346">オブジェクトをインスタンス化する方法について説明します</span><span class="sxs-lookup"><span data-stu-id="7b338-346">Learn how to instantiate objects</span></span>

### <a name="instructions"></a><span data-ttu-id="7b338-347">Instructions</span><span class="sxs-lookup"><span data-stu-id="7b338-347">Instructions</span></span>

* <span data-ttu-id="7b338-348">[ **プロジェクト** ] パネルの [検索] ボックスに「 **ObjectSpawner** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="7b338-348">In the **Project** panel, type **ObjectSpawner** in the search box.</span></span> <span data-ttu-id="7b338-349">また、Assets/AppPrefabs の下にあります。</span><span class="sxs-lookup"><span data-stu-id="7b338-349">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="7b338-350">**ObjectSpawner** prefab を [ **階層** ] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7b338-350">Drag the **ObjectSpawner** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7b338-351">[ **階層** ] パネルの [ **ObjectSpawner** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-351">Click **ObjectSpawner** in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7b338-352">**ObjectSpawner** には、 **Color Source** という名前のフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="7b338-352">**ObjectSpawner** has a field named **Color Source** .</span></span>
* <span data-ttu-id="7b338-353">[ **階層** ] パネルで、 **ColorPickerWheel** 参照をこのフィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7b338-353">From the **Hierarchy** panel, drag the **ColorPickerWheel** reference into this field.</span></span>

    ![オブジェクト Spawner Inspector](images/mr213-objectspawnercolorpickerwheel-650px.jpg)

* <span data-ttu-id="7b338-355">[ **階層** ] パネルの [ **ObjectSpawner** prefab] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-355">Click the **ObjectSpawner** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7b338-356">[ **インスペクター** ] パネルで [ **ObjectSpawner** Script] をダブルクリックして、Visual Studio でコードを表示します。</span><span class="sxs-lookup"><span data-stu-id="7b338-356">In the **Inspector** panel, double click **ObjectSpawner** Script to see the code in Visual Studio.</span></span>

<span data-ttu-id="7b338-357">**ObjectSpawner スクリプト**</span><span class="sxs-lookup"><span data-stu-id="7b338-357">**ObjectSpawner script**</span></span>

<span data-ttu-id="7b338-358">**ObjectSpawner** は、空間にプリミティブメッシュ (cube、球、シリンダ) のコピーをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="7b338-358">The **ObjectSpawner** instantiates copies of a primitive mesh (cube, sphere, cylinder) into the space.</span></span> <span data-ttu-id="7b338-359">**Interactionsourcepressed** れたことが検出されると、きき者と、そのイベントが **interactionsourcepresstype** または **interactionsourcepresstype** であるかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-359">When a **InteractionSourcePressed** is detected it checks the handedness and if it's an **InteractionSourcePressType.Grasp** or **InteractionSourcePressType.Select** event.</span></span>

<span data-ttu-id="7b338-360">イベントを **把握** するために、現在のメッシュの種類 (球、cube、円柱) のインデックスをインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="7b338-360">For a **Grasp** event, it increments the index of current mesh type (sphere, cube, cylinder)</span></span>

```cs
private void InteractionSourcePressed(InteractionSourcePressedEventArgs obj)
{
    // Check handedness, see if it is left controller
    if (obj.state.source.handedness == handedness)
    {
        switch (obj.pressType)
        {
            // If it is Select button event, spawn object
            case InteractionSourcePressType.Select:
                if (state == StateEnum.Idle)
                {
                    // We've pressed the grasp - enter spawning state
                    state = StateEnum.Spawning;
                    SpawnObject();
                }
                break;

            // If it is Grasp button event
            case InteractionSourcePressType.Grasp:

                // Increment the index of current mesh type (sphere, cube, cylinder)
                meshIndex++;
                if (meshIndex >= NumAvailableMeshes)
                {
                    meshIndex = 0;
                }
                break;

            default:
                break;
        }
    }
}
```

<span data-ttu-id="7b338-361">**Select** イベントの場合、 **SpawnObject ()** では、新しいオブジェクトがインスタンス化され、親ではありません。</span><span class="sxs-lookup"><span data-stu-id="7b338-361">For a **Select** event, in **SpawnObject()** , a new object is instantiated, un-parented and released into the world.</span></span>

```cs
private void SpawnObject()
{
    // Instantiate the spawned object
    GameObject newObject = Instantiate(displayObject.gameObject, spawnParent);
    // Detach the newly spawned object
    newObject.transform.parent = null;
    // Reset the scale transform to 1
    scaleParent.localScale = Vector3.one;
    // Set its material color so its material gets instantiated
    newObject.GetComponent<Renderer>().material.color = colorSource.SelectedColor;
}
```

<span data-ttu-id="7b338-362">**ObjectSpawner** は、 **ColorPickerWheel** を使用して、表示オブジェクトの素材の色を設定します。</span><span class="sxs-lookup"><span data-stu-id="7b338-362">The **ObjectSpawner** uses the **ColorPickerWheel** to set the color of the display object's material.</span></span> <span data-ttu-id="7b338-363">生成されたオブジェクトには、その色が保持されるように、このマテリアルのインスタンスが与えられます。</span><span class="sxs-lookup"><span data-stu-id="7b338-363">Spawned objects are given an instance of this material so they will retain their color.</span></span>

* <span data-ttu-id="7b338-364">シーンを **保存** し、[ **再生** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-364">**Save** the scene and click the **play** button.</span></span>

<span data-ttu-id="7b338-365">ボタンを使用してオブジェクトを変更し、[選択] ボタンを使用してオブジェクトを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="7b338-365">You will be able to change the objects with the Grasp button and spawn objects with the Select button.</span></span>

## <a name="build-and-deploy-app-to-mixed-reality-portal"></a><span data-ttu-id="7b338-366">アプリをビルドし、Mixed Reality ポータルにデプロイする</span><span class="sxs-lookup"><span data-stu-id="7b338-366">Build and deploy app to Mixed Reality Portal</span></span>

* <span data-ttu-id="7b338-367">Unity で、[ **ファイル > ビルド設定** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b338-367">In Unity, select **File > Build Settings** .</span></span>
* <span data-ttu-id="7b338-368">[ **開い** ているシーンの追加] をクリックして、 **ビルドのシーン** に現在のシーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="7b338-368">Click **Add Open Scenes** to add current scene to the **Scenes In Build** .</span></span>
* <span data-ttu-id="7b338-369">[ **ビルド** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-369">Click **Build** .</span></span>
* <span data-ttu-id="7b338-370">"App" という名前の **新しいフォルダー** を作成します。</span><span class="sxs-lookup"><span data-stu-id="7b338-370">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="7b338-371">**アプリ** フォルダーをシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-371">Single click the **App** folder.</span></span>
* <span data-ttu-id="7b338-372">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-372">Click **Select Folder** .</span></span>
* <span data-ttu-id="7b338-373">Unity が完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-373">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="7b338-374">**アプリ** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="7b338-374">Open the **App** folder.</span></span>
* <span data-ttu-id="7b338-375">**YourSceneName** Visual Studio ソリューションファイルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-375">Double click **YourSceneName.sln** Visual Studio Solution file.</span></span>
* <span data-ttu-id="7b338-376">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に、ARM から **X64** に変更します。</span><span class="sxs-lookup"><span data-stu-id="7b338-376">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X64** .</span></span>
* <span data-ttu-id="7b338-377">[デバイス] ボタンの横にあるドロップダウン矢印をクリックし、[ **ローカルコンピューター** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7b338-377">Click on the drop-down arrow next to the Device button, and select **Local Machine** .</span></span>
* <span data-ttu-id="7b338-378">メニューで [デバッグ] **、[デバッグなしで開始** ] の順にクリックする >、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7b338-378">Click **Debug -> Start Without debugging** in the menu or press **Ctrl + F5** .</span></span>

<span data-ttu-id="7b338-379">これで、アプリがビルドされ、Mixed Reality ポータルにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="7b338-379">Now the app is built and installed in Mixed Reality Portal.</span></span> <span data-ttu-id="7b338-380">これは、Mixed Reality ポータルの [スタート] メニューを使用して再度起動することができます。</span><span class="sxs-lookup"><span data-stu-id="7b338-380">You can launch it again through Start menu in Mixed Reality Portal.</span></span>

## <a name="advanced-design---brush-tools-with-radial-layout"></a><span data-ttu-id="7b338-381">高度なデザイン-放射状レイアウトを使用したブラシツール</span><span class="sxs-lookup"><span data-stu-id="7b338-381">Advanced design - Brush tools with radial layout</span></span>

![MixedReality213 Main](images/mr213-main-600px.jpg)

<span data-ttu-id="7b338-383">この章では、既定のモーションコントローラーモデルをカスタムブラシツールコレクションに置き換える方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-383">In this chapter, you will learn how to replace the default motion controller model with a custom brush tool collection.</span></span> <span data-ttu-id="7b338-384">参考までに **、[シーン** ] フォルダーの下の完成したシーン **MixedReality213Advanced** を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="7b338-384">For your reference, you can find the completed scene **MixedReality213Advanced** under **Scenes** folder.</span></span>

### <a name="instructions"></a><span data-ttu-id="7b338-385">Instructions</span><span class="sxs-lookup"><span data-stu-id="7b338-385">Instructions</span></span>

* <span data-ttu-id="7b338-386">[ **プロジェクト** ] パネルの [検索] ボックスに「 **BrushSelector** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="7b338-386">In the **Project** panel, type **BrushSelector** in the search box .</span></span> <span data-ttu-id="7b338-387">また、Assets/AppPrefabs の下にあります。</span><span class="sxs-lookup"><span data-stu-id="7b338-387">You can also find it under Assets/AppPrefabs/</span></span>
* <span data-ttu-id="7b338-388">**BrushSelector** prefab を [ **階層** ] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7b338-388">Drag the **BrushSelector** prefab into the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7b338-389">組織の場合は、 **ブラシ** と呼ばれる空のオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="7b338-389">For organization, create an empty GameObject called **Brushes**</span></span>
* <span data-ttu-id="7b338-390">[ **プロジェクト** ] パネルから [ **ブラシ** ] に次の prefabs をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7b338-390">Drag following prefabs from the **Project** panel into **Brushes**</span></span>
    * <span data-ttu-id="7b338-391">Assets/AppPrefabs/ **BrushFat**</span><span class="sxs-lookup"><span data-stu-id="7b338-391">Assets/AppPrefabs/ **BrushFat**</span></span>
    * <span data-ttu-id="7b338-392">Assets/AppPrefabs/ **BrushThin**</span><span class="sxs-lookup"><span data-stu-id="7b338-392">Assets/AppPrefabs/ **BrushThin**</span></span>
    * <span data-ttu-id="7b338-393">Assets/AppPrefabs/ **消しゴム**</span><span class="sxs-lookup"><span data-stu-id="7b338-393">Assets/AppPrefabs/ **Eraser**</span></span>
    * <span data-ttu-id="7b338-394">Assets/AppPrefabs/ **MarkerFat**</span><span class="sxs-lookup"><span data-stu-id="7b338-394">Assets/AppPrefabs/ **MarkerFat**</span></span>
    * <span data-ttu-id="7b338-395">Assets/AppPrefabs/ **MarkerThin**</span><span class="sxs-lookup"><span data-stu-id="7b338-395">Assets/AppPrefabs/ **MarkerThin**</span></span>
    * <span data-ttu-id="7b338-396">Assets/AppPrefabs/ **鉛筆**</span><span class="sxs-lookup"><span data-stu-id="7b338-396">Assets/AppPrefabs/ **Pencil**</span></span>

    ![ブラシ](images/mixedreality213-brushes-250px.png)

* <span data-ttu-id="7b338-398">[ **階層** ] パネルの [ **motioncontrollers** prefab] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-398">Click **MotionControllers** prefab in the **Hierarchy** panel.</span></span>
* <span data-ttu-id="7b338-399">[ **インスペクター** ] パネルの [ **モーションコントローラービジュアライザー** で **常に代替モデルを使用する** ] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="7b338-399">In the **Inspector** panel, uncheck **Always Use Alternate Right Model** on the **Motion Controller Visualizer**</span></span>
* <span data-ttu-id="7b338-400">[ **階層** ] パネルで、[ **BrushSelector** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-400">In the **Hierarchy** panel, click **BrushSelector**</span></span>
* <span data-ttu-id="7b338-401">**BrushSelector** に **colorpicker** という名前のフィールドがある</span><span class="sxs-lookup"><span data-stu-id="7b338-401">**BrushSelector** has a field named **ColorPicker**</span></span>
* <span data-ttu-id="7b338-402">[ **階層** ] パネルで、[ **ColorPickerWheel** ] を [ **インスペクター** ] パネルの [ **colorpicker** ] フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7b338-402">From the **Hierarchy** panel, drag the **ColorPickerWheel** into **ColorPicker** field in the **Inspector** panel.</span></span>

    ![ColorPickerWheel をブラシセレクターに割り当てる](images/mr213-brushselector-500px.jpg)

* <span data-ttu-id="7b338-404">[ **階層** ] パネルの [ **BrushSelector** Prefab] で、 **メニュー** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="7b338-404">In the **Hierarchy** panel, under **BrushSelector** prefab, select the **Menu** object.</span></span>
* <span data-ttu-id="7b338-405">[ **インスペクター** ] パネルの **lineobjectcollection** コンポーネントで、[ **オブジェクト** 配列] ドロップダウンを開きます。</span><span class="sxs-lookup"><span data-stu-id="7b338-405">In the **Inspector** panel, under the **LineObjectCollection** component, open the **Objects** array dropdown.</span></span> <span data-ttu-id="7b338-406">6個の空のスロットが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-406">You will see 6 empty slots.</span></span>
* <span data-ttu-id="7b338-407">[ **階層** ] パネルで、[ **ブラシ** の prefabs] の下にある各親を、任意の順序でこれらのスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7b338-407">From the **Hierarchy** panel, drag each of the prefabs parented under the **Brushes** GameObject into these slots in any order.</span></span> <span data-ttu-id="7b338-408">(プロジェクトフォルダー内の prefabs ではなく、シーンから prefabs をドラッグしていることを確認してください)。</span><span class="sxs-lookup"><span data-stu-id="7b338-408">(Make sure you're dragging the prefabs from the scene, not the prefabs in the project folder.)</span></span>

![ブラシセレクター](images/mr213-brushselectorbrushes-700px.jpg)

<span data-ttu-id="7b338-410">**BrushSelector prefab**</span><span class="sxs-lookup"><span data-stu-id="7b338-410">**BrushSelector prefab**</span></span>

<span data-ttu-id="7b338-411">**BrushSelector** は **attachtocontroller** を継承するため、[ **Inspector** ] パネルに **きき** と **要素** のオプションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-411">Since the **BrushSelector** inherits **AttachToController** , it shows **Handedness** and **Element** options in the **Inspector** panel.</span></span> <span data-ttu-id="7b338-412">**右** を選択し、[ポーズ] を **ポイント** して、右のコントローラーに [ブラシ] ツールを接続します。</span><span class="sxs-lookup"><span data-stu-id="7b338-412">We selected **Right** and **Pointing Pose** to attach brush tools to the right hand controller with forward direction.</span></span>

<span data-ttu-id="7b338-413">**BrushSelector** は、次の2つのユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b338-413">The **BrushSelector** makes use of two utilities:</span></span>

* <span data-ttu-id="7b338-414">**楕円** : 楕円形に沿って空間内のポイントを生成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-414">**Ellipse** : used to generate points in space along an ellipse shape.</span></span>
* <span data-ttu-id="7b338-415">**Lineobjectcollection** : 任意の行クラスによって生成された点を使用してオブジェクトを分散します (例: 楕円)。</span><span class="sxs-lookup"><span data-stu-id="7b338-415">**LineObjectCollection** : distributes objects using the points generated by any Line class (eg, Ellipse).</span></span> <span data-ttu-id="7b338-416">ここでは、楕円の形状に沿ってブラシを配置するために使用します。</span><span class="sxs-lookup"><span data-stu-id="7b338-416">This is what we'll be using to place our brushes along the Ellipse shape.</span></span>

<span data-ttu-id="7b338-417">これらのユーティリティを組み合わせて使用すると、放射状メニューを作成できます。</span><span class="sxs-lookup"><span data-stu-id="7b338-417">When combined, these utilities can be used to create a radial menu.</span></span>

<span data-ttu-id="7b338-418">**LineObjectCollection スクリプト**</span><span class="sxs-lookup"><span data-stu-id="7b338-418">**LineObjectCollection script**</span></span>

<span data-ttu-id="7b338-419">**Lineobjectcollection** には、その行に沿って分布するオブジェクトのサイズ、位置、および回転を制御します。</span><span class="sxs-lookup"><span data-stu-id="7b338-419">**LineObjectCollection** has controls for the size, position and rotation of objects distributed along its line.</span></span> <span data-ttu-id="7b338-420">これは、ブラシセレクターのような放射状メニューを作成する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="7b338-420">This is useful for creating radial menus like the brush selector.</span></span> <span data-ttu-id="7b338-421">中心が選択された位置に近づいたときに、何もスケールアップしないブラシの外観を作成するために、 **objectscale** 曲線は中央にピークし、端に tapers ます。</span><span class="sxs-lookup"><span data-stu-id="7b338-421">To create the appearance of brushes that scale up from nothing as they approach the center selected position, the **ObjectScale** curve peaks in the center and tapers off at the edges.</span></span>

<span data-ttu-id="7b338-422">**BrushSelector スクリプト**</span><span class="sxs-lookup"><span data-stu-id="7b338-422">**BrushSelector script**</span></span>

<span data-ttu-id="7b338-423">**BrushSelector** の場合、手続き型アニメーションを使用することを選択しました。</span><span class="sxs-lookup"><span data-stu-id="7b338-423">In the case of the **BrushSelector** , we've chosen to use procedural animation.</span></span> <span data-ttu-id="7b338-424">最初に、ブラシモデルは **Lineobjectcollection** スクリプトによって楕円で配分されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-424">First, brush models are distributed in an ellipse by the **LineObjectCollection** script.</span></span> <span data-ttu-id="7b338-425">次に、各ブラシは、選択内容に基づいて変化する **DisplayMode** 値に基づいて、ユーザー側での位置を維持する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="7b338-425">Then, each brush is responsible for maintaining its position in the user's hand based on its **DisplayMode** value, which changes based on the selection.</span></span> <span data-ttu-id="7b338-426">ユーザーがブラシを選択したときにブラシの位置の切り替えが中断される可能性が高いため、手続き型の方法を選択しました。</span><span class="sxs-lookup"><span data-stu-id="7b338-426">We chose a procedural approach because of the high probability of brush position transitions being interrupted as the user selects brushes.</span></span> <span data-ttu-id="7b338-427">Mecanim アニメーションは中断を適切に処理できますが、単純な Lerp 操作よりも複雑になる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="7b338-427">Mecanim animations can handle interruptions gracefully, but it tends to be more complicated than a simple Lerp operation.</span></span>

<span data-ttu-id="7b338-428">**BrushSelector** は、両方の組み合わせを使用します。</span><span class="sxs-lookup"><span data-stu-id="7b338-428">**BrushSelector** uses a combination of both.</span></span> <span data-ttu-id="7b338-429">タッチパッドの入力が検出されると、ブラシのオプションが表示され、放射状メニューに沿ってスケールアップされます。</span><span class="sxs-lookup"><span data-stu-id="7b338-429">When touchpad input is detected, brush options become visible and scale up along the radial menu.</span></span> <span data-ttu-id="7b338-430">タイムアウト期間が経過すると (ユーザーが選択を行ったことを示す)、ブラシのオプションが再度スケールダウンされ、選択したブラシだけが残ります。</span><span class="sxs-lookup"><span data-stu-id="7b338-430">After a timeout period (which indicates that the user has made a selection) the brush options scale down again, leaving only the selected brush.</span></span>

<span data-ttu-id="7b338-431">**タッチパッド入力の視覚化**</span><span class="sxs-lookup"><span data-stu-id="7b338-431">**Visualizing touchpad input**</span></span>

<span data-ttu-id="7b338-432">コントローラーモデルが完全に置き換えられている場合でも、元のモデル入力に入力を表示すると便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="7b338-432">Even in cases where the controller model has been completely replaced, it can be helpful to show input on the original model inputs.</span></span> <span data-ttu-id="7b338-433">これは、実際にユーザーの操作をグラウンドにするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7b338-433">This helps to ground the user's actions in reality.</span></span> <span data-ttu-id="7b338-434">**BrushSelector** の場合、入力を受け取ったときにタッチパッドを短時間で表示するように選択しました。</span><span class="sxs-lookup"><span data-stu-id="7b338-434">For the **BrushSelector** we've chosen to make the touchpad briefly visible when the input is received.</span></span> <span data-ttu-id="7b338-435">これを行うには、コントローラーからタッチパッド要素を取得し、そのマテリアルをカスタムマテリアルに置き換えて、タッチパッド入力を最後に受信したときに基づいてそのマテリアルの色にグラデーションを適用します。</span><span class="sxs-lookup"><span data-stu-id="7b338-435">This was done by retrieving the Touchpad element from the controller, replacing its material with a custom material, then applying a gradient to that material's color based on the last time touchpad input was received.</span></span>

```cs
protected override void OnAttachToController()
{
    // Turn off the default controller's renderers
    controller.SetRenderersVisible(false);

    // Get the touchpad and assign our custom material to it
    Transform touchpad;
    if (controller.TryGetElement(MotionControllerInfo.ControllerElementEnum.Touchpad, out touchpad))
    {
        touchpadRenderer = touchpad.GetComponentInChildren<MeshRenderer>();
        originalTouchpadMaterial = touchpadRenderer.material;
        touchpadRenderer.material = touchpadMaterial;
        touchpadRenderer.enabled = true;
    }

    // Subscribe to input now that we're parented under the controller
    InteractionManager.InteractionSourceUpdated += InteractionSourceUpdated;
}

private void Update()
{
    ...
    // Update our touchpad material
    Color glowColor = touchpadColor.Evaluate((Time.unscaledTime - touchpadTouchTime) / touchpadGlowLossTime);
    touchpadMaterial.SetColor("_EmissionColor", glowColor);
    touchpadMaterial.SetColor("_Color", glowColor);
    ...
}
```

<span data-ttu-id="7b338-436">**タッチパッド入力によるブラシツールの選択**</span><span class="sxs-lookup"><span data-stu-id="7b338-436">**Brush tool selection with touchpad input**</span></span>

<span data-ttu-id="7b338-437">ブラシセレクターがタッチパッドの押された入力を検出すると、入力の位置を調べて、左または右にあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="7b338-437">When the brush selector detects touchpad's pressed input, it checks the position of the input to determine if it was to the left or right.</span></span>

<span data-ttu-id="7b338-438">**SelectPressedAmount を使用したストロークの太さ**</span><span class="sxs-lookup"><span data-stu-id="7b338-438">**Stroke thickness with selectPressedAmount**</span></span>

<span data-ttu-id="7b338-439">**Interactionsourcepresstype ()** 内の **Select** イベントの代わりに、 **selectPressedAmount** を使用して、押された量のアナログ値を取得できます。</span><span class="sxs-lookup"><span data-stu-id="7b338-439">Instead of the **InteractionSourcePressType.Select** event in the **InteractionSourcePressed()** , you can get the analog value of the pressed amount through **selectPressedAmount** .</span></span> <span data-ttu-id="7b338-440">この値は、 **Interactionsourceupdated ()** で取得できます。</span><span class="sxs-lookup"><span data-stu-id="7b338-440">This value can be retrieved in **InteractionSourceUpdated()** .</span></span>

```cs
private void InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
{
    if (obj.state.source.handedness == handedness)
    {
        if (obj.state.touchpadPressed)
        {
            // Check which side we clicked
            if (obj.state.touchpadPosition.x < 0)
            {
                currentAction = SwipeEnum.Left;
            }
            else
            {
                currentAction = SwipeEnum.Right;
            }

            // Ping the touchpad material so it gets bright
            touchpadTouchTime = Time.unscaledTime;
        }

        if (activeBrush != null)
        {
            // If the pressed amount is greater than our threshold, draw
            if (obj.state.selectPressedAmount >= selectPressedDrawThreshold)
            {
                activeBrush.Draw = true;
                activeBrush.Width = ProcessSelectPressedAmount(obj.state.selectPressedAmount);
            }
            else
            {
                // Otherwise, stop drawing
                activeBrush.Draw = false;
                selectPressedSmooth = 0f;
            }
        }
    }
}
```

<span data-ttu-id="7b338-441">**消しゴムスクリプト**</span><span class="sxs-lookup"><span data-stu-id="7b338-441">**Eraser script**</span></span>

<span data-ttu-id="7b338-442">**消しゴム** は、基本 **ブラシ** の **drawovertime ()** 関数をオーバーライドする特殊な種類のブラシです。</span><span class="sxs-lookup"><span data-stu-id="7b338-442">**Eraser** is a special type of brush that overrides the base **Brush** 's **DrawOverTime()** function.</span></span> <span data-ttu-id="7b338-443">描画が true の場合、消しゴムは、そのチップが既存のブラシストロークと交差しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="7b338-443">While Draw is true, the eraser checks to see if its tip intersects with any existing brush strokes.</span></span> <span data-ttu-id="7b338-444">存在する場合は、圧縮されて削除されるようにキューに追加されます。</span><span class="sxs-lookup"><span data-stu-id="7b338-444">If it does, they are added to a queue to be shrunk down and deleted.</span></span>

## <a name="advanced-design---teleportation-and-locomotion"></a><span data-ttu-id="7b338-445">高度な設計-電話と locomotion</span><span class="sxs-lookup"><span data-stu-id="7b338-445">Advanced design - Teleportation and locomotion</span></span>

<span data-ttu-id="7b338-446">ユーザーがサムスティックを使用して、ユーザーによるシーンの移動を許可する場合は、 **MixedRealityCamera** ではなく **MixedRealityCameraParent** を使用します。</span><span class="sxs-lookup"><span data-stu-id="7b338-446">If you want to allow the user to move around the scene with teleportation using thumbstick, use **MixedRealityCameraParent** instead of **MixedRealityCamera** .</span></span> <span data-ttu-id="7b338-447">**Inputmanager** と **defaultcursor** も追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b338-447">You also need to add **InputManager** and **DefaultCursor** .</span></span> <span data-ttu-id="7b338-448">**MixedRealityCameraParent** には既に **Motioncontrollers** と **境界** が子コンポーネントとして含まれているため、既存の **motioncontrollers** と **環境** prefab を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7b338-448">Since **MixedRealityCameraParent** already includes **MotionControllers** and **Boundary** as child components, you should remove existing **MotionControllers** and **Environment** prefab.</span></span>

### <a name="instructions"></a><span data-ttu-id="7b338-449">Instructions</span><span class="sxs-lookup"><span data-stu-id="7b338-449">Instructions</span></span>

* <span data-ttu-id="7b338-450">[ **階層** ] パネルで、 **MixedRealityCamera** 、 **Environment** 、 **motioncontrollers** を削除します。</span><span class="sxs-lookup"><span data-stu-id="7b338-450">In the **Hierarchy** panel, delete **MixedRealityCamera** , **Environment** and **MotionControllers**</span></span>
* <span data-ttu-id="7b338-451">[ **プロジェクト] パネル** で、次の prefabs を検索し、[ **階層** ] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7b338-451">From the **Project panel** , search and drag the following prefabs into the **Hierarchy** panel:</span></span>
    * <span data-ttu-id="7b338-452">Assets/AppPrefabs/Input/Prefabs/ **MixedRealityCameraParent**</span><span class="sxs-lookup"><span data-stu-id="7b338-452">Assets/AppPrefabs/Input/Prefabs/ **MixedRealityCameraParent**</span></span>
    * <span data-ttu-id="7b338-453">Assets/AppPrefabs/Input/Prefabs/ **Inputmanager**</span><span class="sxs-lookup"><span data-stu-id="7b338-453">Assets/AppPrefabs/Input/Prefabs/ **InputManager**</span></span>
    * <span data-ttu-id="7b338-454">Assets/AppPrefabs/Input/Prefabs/Cursor/ **Defaultcursor**</span><span class="sxs-lookup"><span data-stu-id="7b338-454">Assets/AppPrefabs/Input/Prefabs/Cursor/ **DefaultCursor**</span></span>

    ![Mixed Reality カメラの親](images/mr213-cameraparent-300px.png)

* <span data-ttu-id="7b338-456">[ **階層** ] パネルで、[ **入力マネージャー** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-456">In the **Hierarchy** panel, click **Input Manager**</span></span>
* <span data-ttu-id="7b338-457">[ **インスペクター** ] パネルで、 **単純な単一ポインターセレクター** セクションまで下にスクロールします。</span><span class="sxs-lookup"><span data-stu-id="7b338-457">In the **Inspector** panel, scroll down to the **Simple Single Pointer Selector** section</span></span>
* <span data-ttu-id="7b338-458">[ **階層** ] パネルで、[ **Defaultcursor** ] を **カーソル** フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7b338-458">From the **Hierarchy** panel, drag **DefaultCursor** into **Cursor** field</span></span>

    ![DefaultCursor の割り当て](images/mr213-defaultcursor-500px.png)

* <span data-ttu-id="7b338-460">シーンを **保存** し、[ **再生** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-460">**Save** the scene and click the **play** button.</span></span> <span data-ttu-id="7b338-461">サムスティックを使用して、左/右に回転したり、テレポートしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="7b338-461">You will be able to use the thumbstick to rotate left/right or teleport.</span></span>

## <a name="the-end"></a><span data-ttu-id="7b338-462">最後です</span><span class="sxs-lookup"><span data-stu-id="7b338-462">The end</span></span>

<span data-ttu-id="7b338-463">これがこのチュートリアルの終わりです。</span><span class="sxs-lookup"><span data-stu-id="7b338-463">And that's the end of this tutorial!</span></span> <span data-ttu-id="7b338-464">学習した内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7b338-464">You learned:</span></span>

* <span data-ttu-id="7b338-465">Unity のゲームモードとランタイムでモーションコントローラーモデルを操作する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-465">How to work with motion controller models in Unity's game mode and runtime.</span></span>
* <span data-ttu-id="7b338-466">さまざまな種類のボタンイベントとそのアプリケーションを使用する方法。</span><span class="sxs-lookup"><span data-stu-id="7b338-466">How to use different types of button events and their applications.</span></span>
* <span data-ttu-id="7b338-467">コントローラー上に UI 要素を重ね合わせる方法、または UI 要素を完全にカスタマイズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b338-467">How to overlay UI elements on top of the controller or fully customize it.</span></span>

<span data-ttu-id="7b338-468">これで、モーションコントローラーで独自のイマーシブエクスペリエンスを作成する準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="7b338-468">You are now ready to start creating your own immersive experience with motion controllers!</span></span>

## <a name="completed-scenes"></a><span data-ttu-id="7b338-469">完成したシーン</span><span class="sxs-lookup"><span data-stu-id="7b338-469">Completed scenes</span></span>

* <span data-ttu-id="7b338-470">Unity の [ **プロジェクト** ] パネルで、[ **シーン** ] フォルダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7b338-470">In Unity's **Project** panel click on the **Scenes** folder.</span></span>
* <span data-ttu-id="7b338-471">Unity シーン **MixedReality213** と **MixedReality213Advanced** が2つ見つかります。</span><span class="sxs-lookup"><span data-stu-id="7b338-471">You will find two Unity scenes **MixedReality213** and **MixedReality213Advanced** .</span></span>
    * <span data-ttu-id="7b338-472">**MixedReality213** : 1 つのブラシを使用した完成したシーン</span><span class="sxs-lookup"><span data-stu-id="7b338-472">**MixedReality213** : Completed scene with single brush</span></span>
    * <span data-ttu-id="7b338-473">**MixedReality213Advanced** : 複数のブラシを持つ完成したシーンを選択ボタンの押す回数の例</span><span class="sxs-lookup"><span data-stu-id="7b338-473">**MixedReality213Advanced** : Completed scene with multiple brush with select button's press amount example</span></span>

## <a name="see-also"></a><span data-ttu-id="7b338-474">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b338-474">See also</span></span>

* [<span data-ttu-id="7b338-475">MR 入力213プロジェクトファイル</span><span class="sxs-lookup"><span data-stu-id="7b338-475">MR Input 213 project files</span></span>](https://github.com/Microsoft/MixedReality213)
* [<span data-ttu-id="7b338-476">Mixed Reality Toolkit-モーションコントローラーテストシーン</span><span class="sxs-lookup"><span data-stu-id="7b338-476">Mixed Reality Toolkit - Motion Controller Test scene</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/Input/Scenes)
* [<span data-ttu-id="7b338-477">Mixed Reality Toolkit-グラブ機構</span><span class="sxs-lookup"><span data-stu-id="7b338-477">Mixed Reality Toolkit - Grab Mechanics</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/MotionControllers-GrabMechanics)
* [<span data-ttu-id="7b338-478">モーションコントローラーの開発ガイドライン</span><span class="sxs-lookup"><span data-stu-id="7b338-478">Motion controller development guidelines</span></span>](../design/motion-controllers.md)
