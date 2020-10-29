---
title: MR 基本 101E-エミュレーターを使用した完全なプロジェクト
description: Unity、Visual Studio、および HoloLens Emulator を使用したこのコーディングのチュートリアルに従って、holographic アプリケーションの基本を学習してください。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: mixed reality、Windows Mixed Reality、HoloLens、ホログラム、academy、チュートリアル、エミュレーター
ms.openlocfilehash: 9aa3da5367343f43eae167f8ffedc30b78076260
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686490"
---
# <a name="mr-basics-101e-complete-project-with-emulator"></a><span data-ttu-id="0943b-104">MR の基本 101E:エミュレーターを使用した完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="0943b-104">MR Basics 101E: Complete project with emulator</span></span>

>[!NOTE]
><span data-ttu-id="0943b-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="0943b-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0943b-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="0943b-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0943b-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。</span><span class="sxs-lookup"><span data-stu-id="0943b-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0943b-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="0943b-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0943b-109">HoloLens 2 向けには、[新しいチュートリアル シリーズ](mrlearning-base.md)が投稿されています。</span><span class="sxs-lookup"><span data-stu-id="0943b-109">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

 >[!VIDEO https://www.youtube.com/embed/Xzm8_s05mm8]

<span data-ttu-id="0943b-110">このチュートリアルでは、Unity でビルドされた完全なプロジェクトについて説明します。これは、 [宝石](../../../design/gaze-and-commit.md)、 [ジェスチャ](../../../design/gaze-and-commit.md#composite-gestures)、 [音声入力](../../../design/voice-input.md)、 [空間サウンド](../../../design/spatial-sound.md) 、 [空間マッピング](../../../design/spatial-mapping.md)など、HoloLens のコア Windows Mixed Reality 機能を示しています。</span><span class="sxs-lookup"><span data-stu-id="0943b-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](../../../design/gaze-and-commit.md), [gestures](../../../design/gaze-and-commit.md#composite-gestures), [voice input](../../../design/voice-input.md), [spatial sound](../../../design/spatial-sound.md) and [spatial mapping](../../../design/spatial-mapping.md).</span></span> <span data-ttu-id="0943b-111">このチュートリアルの完了には約1時間かかります。</span><span class="sxs-lookup"><span data-stu-id="0943b-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="0943b-112">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="0943b-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0943b-113">コース</span><span class="sxs-lookup"><span data-stu-id="0943b-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0943b-114"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0943b-114"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0943b-115"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="0943b-115"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="0943b-116">MR の基本 101E:エミュレーターを使用した完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="0943b-116">MR Basics 101E: Complete project with emulator</span></span></td><td style="text-align: center;"> <span data-ttu-id="0943b-117">✔️</span><span class="sxs-lookup"><span data-stu-id="0943b-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="0943b-118">開始する前に</span><span class="sxs-lookup"><span data-stu-id="0943b-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0943b-119">前提条件</span><span class="sxs-lookup"><span data-stu-id="0943b-119">Prerequisites</span></span>

* <span data-ttu-id="0943b-120">適切な [ツールがインストール](../../install-the-tools.md)された WINDOWS 10 PC。</span><span class="sxs-lookup"><span data-stu-id="0943b-120">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md).</span></span>

### <a name="project-files"></a><span data-ttu-id="0943b-121">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="0943b-121">Project files</span></span>

* <span data-ttu-id="0943b-122">プロジェクトに必要な [ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="0943b-122">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span><span data-ttu-id="0943b-123">Unity 2017.2 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="0943b-123"> Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="0943b-124">引き続き Unity 5.6 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="0943b-124">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="0943b-125">引き続き Unity 5.5 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="0943b-125">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="0943b-126">引き続き Unity 5.4 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="0943b-126">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="0943b-127">ファイルをデスクトップまたはその他の簡単な場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="0943b-127">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="0943b-128">フォルダー名は **Origami** のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="0943b-128">Keep the folder name as **Origami** .</span></span>

>[!NOTE]
><span data-ttu-id="0943b-129">ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)ます。</span><span class="sxs-lookup"><span data-stu-id="0943b-129">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="0943b-130">Chapter 1-"Holo" ワールド</span><span class="sxs-lookup"><span data-stu-id="0943b-130">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/qotpUpIQxVU]

<span data-ttu-id="0943b-131">この章では、最初の Unity プロジェクトをセットアップし、ビルドとデプロイのプロセスをステップ実行します。</span><span class="sxs-lookup"><span data-stu-id="0943b-131">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="0943b-132">目標</span><span class="sxs-lookup"><span data-stu-id="0943b-132">Objectives</span></span>

* <span data-ttu-id="0943b-133">Holographic 開発用に Unity を設定します。</span><span class="sxs-lookup"><span data-stu-id="0943b-133">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="0943b-134">ホログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="0943b-134">Make a hologram.</span></span>
* <span data-ttu-id="0943b-135">作成したホログラムを確認します。</span><span class="sxs-lookup"><span data-stu-id="0943b-135">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="0943b-136">Instructions</span><span class="sxs-lookup"><span data-stu-id="0943b-136">Instructions</span></span>

* <span data-ttu-id="0943b-137">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="0943b-137">Start Unity.</span></span>
* <span data-ttu-id="0943b-138">**[Open (開く)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-138">Select **Open** .</span></span>
* <span data-ttu-id="0943b-139">前にアーカイブしていない **Origami** フォルダーとして場所を入力します。</span><span class="sxs-lookup"><span data-stu-id="0943b-139">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="0943b-140">[ **Origami** ] を選択し、[ **フォルダーの選択** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0943b-140">Select **Origami** and click **Select Folder** .</span></span>
* <span data-ttu-id="0943b-141">新しいシーンを保存します。 [ **ファイル**  /  **名を付けてシーンを保存** する。</span><span class="sxs-lookup"><span data-stu-id="0943b-141">Save the new scene: **File** / **Save Scene As** .</span></span>
* <span data-ttu-id="0943b-142">シーンに **Origami** という名前を **付け** 、[保存] ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="0943b-142">Name the scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-camera"></a><span data-ttu-id="0943b-143">メインカメラの設定</span><span class="sxs-lookup"><span data-stu-id="0943b-143">Setup the main camera</span></span>

* <span data-ttu-id="0943b-144">**[Hierarchy]\(階層\) パネル** で、 **[Main Camera]\(メイン カメラ\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-144">In the **Hierarchy Panel** , select **Main Camera** .</span></span>
* <span data-ttu-id="0943b-145">**インスペクター** で、変換位置を **0、0、0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="0943b-145">In the **Inspector** set its transform position to **0,0,0** .</span></span>
* <span data-ttu-id="0943b-146">" **Clear Flags** " プロパティを見つけ、ドロップ **ダウンから [** **単色** ] に変更します。</span><span class="sxs-lookup"><span data-stu-id="0943b-146">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color** .</span></span>
* <span data-ttu-id="0943b-147">**[Background]\(背景\)** フィールドをクリックして、カラー ピッカーを開きます。</span><span class="sxs-lookup"><span data-stu-id="0943b-147">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="0943b-148">**R、G、B、A** を **0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="0943b-148">Set **R, G, B, and A** to **0** .</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="0943b-149">シーンを設定する</span><span class="sxs-lookup"><span data-stu-id="0943b-149">Setup the scene</span></span>

* <span data-ttu-id="0943b-150">[ **階層] パネル** で、[ **作成** ] をクリックし、[ **空の作成** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0943b-150">In the **Hierarchy Panel** , click on **Create** and **Create Empty** .</span></span>
* <span data-ttu-id="0943b-151">新しい [作成] **オブジェクト** を右クリックし、[名前の変更] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-151">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="0943b-152">**OrigamiCollection** オブジェクトの名前を「」に変更します。</span><span class="sxs-lookup"><span data-stu-id="0943b-152">Rename the GameObject to **OrigamiCollection** .</span></span>
* <span data-ttu-id="0943b-153">[ **プロジェクト] パネル** の [ **ホログラム** ] フォルダーから次のようにします。</span><span class="sxs-lookup"><span data-stu-id="0943b-153">From the **Holograms** folder in the **Project Panel** :</span></span>
  * <span data-ttu-id="0943b-154">**ステージ** を階層にドラッグして、 **OrigamiCollection** の子にします。</span><span class="sxs-lookup"><span data-stu-id="0943b-154">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection** .</span></span>
  * <span data-ttu-id="0943b-155">**Sphere1** を階層内にドラッグして、 **OrigamiCollection** の子にします。</span><span class="sxs-lookup"><span data-stu-id="0943b-155">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection** .</span></span>
  * <span data-ttu-id="0943b-156">**Sphere2** を階層内にドラッグして、 **OrigamiCollection** の子にします。</span><span class="sxs-lookup"><span data-stu-id="0943b-156">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection** .</span></span>
* <span data-ttu-id="0943b-157">[ **階層] パネル** で **指向性ライト** オブジェクトを右クリックし、[ **削除** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-157">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete** .</span></span>
* <span data-ttu-id="0943b-158">[ **ホログラム** ] フォルダーから、[ **階層] パネル** のルートに **ライト** をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0943b-158">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel** .</span></span>
* <span data-ttu-id="0943b-159">**階層** で、 **OrigamiCollection** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-159">In the **Hierarchy** , select the **OrigamiCollection** .</span></span>
* <span data-ttu-id="0943b-160">**インスペクター** で、変換位置を **0、-0.5、2.0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="0943b-160">In the **Inspector** , set the transform position to **0, -0.5, 2.0** .</span></span>
* <span data-ttu-id="0943b-161">Unity の [ **再生** ] ボタンをクリックして、ホログラムをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="0943b-161">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="0943b-162">プレビューウィンドウに Origami オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0943b-162">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="0943b-163">プレビューモードを停止するには、もう一度 **Play** を押します。</span><span class="sxs-lookup"><span data-stu-id="0943b-163">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="0943b-164">Unity から Visual Studio にプロジェクトをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="0943b-164">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="0943b-165">Unity で、[ **ファイル > ビルド設定** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-165">In Unity select **File > Build Settings** .</span></span>
* <span data-ttu-id="0943b-166">[ **プラットフォーム** ] ボックスの一覧で [ **Windows ストア** ] を選択し、[ **プラットフォームの切り替え** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0943b-166">Select **Windows Store** in the **Platform** list and click **Switch Platform** .</span></span>
* <span data-ttu-id="0943b-167">**SDK** を **Universal 10** に設定し、 **ビルドの種類** を **D3D** に設定します。</span><span class="sxs-lookup"><span data-stu-id="0943b-167">Set **SDK** to **Universal 10** and **Build Type** to **D3D** .</span></span>
* <span data-ttu-id="0943b-168">**Unity C# プロジェクト** を確認します。</span><span class="sxs-lookup"><span data-stu-id="0943b-168">Check **Unity C# Projects** .</span></span>
* <span data-ttu-id="0943b-169">シーンを追加するには、[開いている **シーンの追加** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0943b-169">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="0943b-170">[ **プレーヤーの設定** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0943b-170">Click **Player Settings...** .</span></span>
* <span data-ttu-id="0943b-171">[インスペクター] パネルで、[ **Windows ストア] ロゴ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-171">In the Inspector Panel select the **Windows Store logo** .</span></span> <span data-ttu-id="0943b-172">次に、[ **発行の設定** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-172">Then select **Publishing Settings** .</span></span>
* <span data-ttu-id="0943b-173">[ **機能** ] セクションで、 **マイク** と **SpatialPerception** 機能を選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-173">In the **Capabilities** section, select the **Microphone** and **SpatialPerception** capabilities.</span></span>
* <span data-ttu-id="0943b-174">[ビルドの設定] ウィンドウに戻り、[ **ビルド** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0943b-174">Back in the Build Settings window, click **Build** .</span></span>
* <span data-ttu-id="0943b-175">"App" という名前の **新しいフォルダー** を作成します。</span><span class="sxs-lookup"><span data-stu-id="0943b-175">Create a **New Folder** named "App".</span></span>
* <span data-ttu-id="0943b-176">**アプリフォルダー** をシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="0943b-176">Single click the **App Folder** .</span></span>
* <span data-ttu-id="0943b-177">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0943b-177">Press **Select Folder** .</span></span>
* <span data-ttu-id="0943b-178">Unity が完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0943b-178">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="0943b-179">**アプリ** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="0943b-179">Open the **App** folder.</span></span>
* <span data-ttu-id="0943b-180">**Origami Visual Studio ソリューション** を開きます。</span><span class="sxs-lookup"><span data-stu-id="0943b-180">Open the **Origami Visual Studio Solution** .</span></span>
* <span data-ttu-id="0943b-181">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に変更し、ARM から **X86** に変更します。</span><span class="sxs-lookup"><span data-stu-id="0943b-181">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86** .</span></span>
  * <span data-ttu-id="0943b-182">デバイスのボタンの横にある矢印をクリックし、[ **HoloLens Emulator** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-182">Click on the arrow next to the Device button, and select **HoloLens Emulator** .</span></span>
  * <span data-ttu-id="0943b-183">[ **デバッグ]、[デバッグなしで開始] の順にクリック >** 、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0943b-183">Click **Debug -> Start Without debugging** or press **Ctrl + F5** .</span></span>
  * <span data-ttu-id="0943b-184">しばらくすると、エミュレーターは Origami プロジェクトから開始されます。</span><span class="sxs-lookup"><span data-stu-id="0943b-184">After some time the emulator will start with the Origami project.</span></span> <span data-ttu-id="0943b-185">[エミュレーター](../../platform-capabilities-and-apis/using-the-hololens-emulator.md)を初めて起動するときは、エミュレーターが起動するまでに15分程度かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="0943b-185">When first launching the [emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md), it can take as long as 15 minutes for the emulator to start up.</span></span> <span data-ttu-id="0943b-186">開始したら、閉じないでください。</span><span class="sxs-lookup"><span data-stu-id="0943b-186">Once it starts, do not close it.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="0943b-187">第2章-宝石</span><span class="sxs-lookup"><span data-stu-id="0943b-187">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/BPWTbAC210k]

<span data-ttu-id="0943b-188">この章では、最初に3つの方法を使用して、ホログラムと対話する方法を紹介[します。](../../../design/gaze-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="0943b-188">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](../../../design/gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="0943b-189">目標</span><span class="sxs-lookup"><span data-stu-id="0943b-189">Objectives</span></span>

* <span data-ttu-id="0943b-190">世界でロックされているカーソルを使用して、宝石を視覚化します。</span><span class="sxs-lookup"><span data-stu-id="0943b-190">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="0943b-191">Instructions</span><span class="sxs-lookup"><span data-stu-id="0943b-191">Instructions</span></span>

* <span data-ttu-id="0943b-192">Unity プロジェクトに戻り、[ビルドの設定] ウィンドウがまだ開いている場合は閉じます。</span><span class="sxs-lookup"><span data-stu-id="0943b-192">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="0943b-193">[ **プロジェクト] パネル** で [ **ホログラム** ] フォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-193">Select the **Holograms** folder in the **Project panel** .</span></span>
* <span data-ttu-id="0943b-194">**カーソル** オブジェクトをルートレベルの [ **階層] パネル** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0943b-194">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="0943b-195">**カーソル** オブジェクトをダブルクリックすると、詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0943b-195">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="0943b-196">[プロジェクト] パネルの [ **Scripts** ] フォルダーを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="0943b-196">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="0943b-197">[ **作成** ] サブメニューをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0943b-197">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="0943b-198">**C# スクリプト** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-198">Select **C# Script** .</span></span>
* <span data-ttu-id="0943b-199">スクリプトに **WorldCursor** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0943b-199">Name the script **WorldCursor** .</span></span> <span data-ttu-id="0943b-200">注: 名前は大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="0943b-200">Note: The name is case-sensitive.</span></span> <span data-ttu-id="0943b-201">.Cs 拡張子を追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0943b-201">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="0943b-202">[ **階層] パネル** で **カーソル** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-202">Select the **Cursor** object in the **Hierarchy panel** .</span></span>
* <span data-ttu-id="0943b-203">**WorldCursor** スクリプトを [ **インスペクター] パネル** にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="0943b-203">Drag and drop the **WorldCursor** script into the **Inspector panel** .</span></span>
* <span data-ttu-id="0943b-204">**WorldCursor** スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="0943b-204">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="0943b-205">このコードをコピーして **WorldCursor.cs** に貼り付け、 **すべて保存** します。</span><span class="sxs-lookup"><span data-stu-id="0943b-205">Copy and paste this code into **WorldCursor.cs** and **Save All** .</span></span>

```cs
using UnityEngine;

public class WorldCursor : MonoBehaviour
{
    private MeshRenderer meshRenderer;

    // Use this for initialization
    void Start()
    {
        // Grab the mesh renderer that's on the same object as this script.
        meshRenderer = this.gameObject.GetComponentInChildren<MeshRenderer>();
    }

    // Update is called once per frame
    void Update()
    {
        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;

        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram...
            // Display the cursor mesh.
            meshRenderer.enabled = true;

            // Move thecursor to the point where the raycast hit.
            this.transform.position = hitInfo.point;

            // Rotate the cursor to hug the surface of the hologram.
            this.transform.rotation = Quaternion.FromToRotation(Vector3.up, hitInfo.normal);
        }
        else
        {
            // If the raycast did not hit a hologram, hide the cursor mesh.
            meshRenderer.enabled = false;
        }
    }
}
```

* <span data-ttu-id="0943b-206">**ファイル > ビルド設定** からアプリをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="0943b-206">Rebuild the app from **File > Build Settings** .</span></span>
* <span data-ttu-id="0943b-207">以前にエミュレーターに配置するために使用した Visual Studio ソリューションに戻ります。</span><span class="sxs-lookup"><span data-stu-id="0943b-207">Return to the Visual Studio solution previously used to deploy to the emulator.</span></span>
* <span data-ttu-id="0943b-208">メッセージが表示されたら、[すべて再読み込み] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-208">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="0943b-209">[ **デバッグ]、[デバッグなしで開始] の順にクリック >** 、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0943b-209">Click **Debug -> Start Without debugging** or press **Ctrl + F5** .</span></span>
* <span data-ttu-id="0943b-210">Xbox コントローラーを使用してシーンを周囲に表示します。</span><span class="sxs-lookup"><span data-stu-id="0943b-210">Use the Xbox controller to look around the scene.</span></span> <span data-ttu-id="0943b-211">カーソルがオブジェクトの形状とどのように連動するかに注目してください。</span><span class="sxs-lookup"><span data-stu-id="0943b-211">Notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="0943b-212">第3章-ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="0943b-212">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/6d-0RHeKHq4]

<span data-ttu-id="0943b-213">この章では、 [ジェスチャ](../../../design/gaze-and-commit.md#composite-gestures)のサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="0943b-213">In this chapter, we'll add support for [gestures](../../../design/gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="0943b-214">ユーザーがペーパー球を選択すると、Unity の物理エンジンを使用して重力をオンにすることで、球がフォールされるようになります。</span><span class="sxs-lookup"><span data-stu-id="0943b-214">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="0943b-215">目標</span><span class="sxs-lookup"><span data-stu-id="0943b-215">Objectives</span></span>

* <span data-ttu-id="0943b-216">選択ジェスチャでホログラムを制御します。</span><span class="sxs-lookup"><span data-stu-id="0943b-216">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="0943b-217">Instructions</span><span class="sxs-lookup"><span data-stu-id="0943b-217">Instructions</span></span>

<span data-ttu-id="0943b-218">まず、Select ジェスチャを検出できるスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0943b-218">We'll start by creating a script than can detect the Select gesture.</span></span>

* <span data-ttu-id="0943b-219">**Scripts** フォルダーで、 **GazeGestureManager** という名前のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0943b-219">In the **Scripts** folder, create a script named **GazeGestureManager** .</span></span>
* <span data-ttu-id="0943b-220">**GazeGestureManager** スクリプトを階層内の **OrigamiCollection** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0943b-220">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="0943b-221">Visual Studio で **GazeGestureManager** スクリプトを開き、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0943b-221">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

```cs
using UnityEngine;
using UnityEngine.XR.WSA.Input;

public class GazeGestureManager : MonoBehaviour
{
    public static GazeGestureManager Instance { get; private set; }

    // Represents the hologram that is currently being gazed at.
    public GameObject FocusedObject { get; private set; }

    GestureRecognizer recognizer;

    // Use this for initialization
    void Start()
    {
        Instance = this;

        // Set up a GestureRecognizer to detect Select gestures.
        recognizer = new GestureRecognizer();
        recognizer.Tapped += (args) =>
        {
            // Send an OnSelect message to the focused object and its ancestors.
            if (FocusedObject != null)
            {
                FocusedObject.SendMessageUpwards("OnSelect", SendMessageOptions.DontRequireReceiver);
            }
        };
        recognizer.StartCapturingGestures();
    }

    // Update is called once per frame
    void Update()
    {
        // Figure out which hologram is focused this frame.
        GameObject oldFocusObject = FocusedObject;

        // Do a raycast into the world based on the user's
        // head position and orientation.
        var headPosition = Camera.main.transform.position;
        var gazeDirection = Camera.main.transform.forward;

        RaycastHit hitInfo;
        if (Physics.Raycast(headPosition, gazeDirection, out hitInfo))
        {
            // If the raycast hit a hologram, use that as the focused object.
            FocusedObject = hitInfo.collider.gameObject;
        }
        else
        {
            // If the raycast did not hit a hologram, clear the focused object.
            FocusedObject = null;
        }

        // If the focused object changed this frame,
        // start detecting fresh gestures again.
        if (FocusedObject != oldFocusObject)
        {
            recognizer.CancelGestures();
            recognizer.StartCapturingGestures();
        }
    }
}
```

* <span data-ttu-id="0943b-222">Scripts フォルダーに、今度は **SphereCommands** という名前の別のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0943b-222">Create another script in the Scripts folder, this time named **SphereCommands** .</span></span>
* <span data-ttu-id="0943b-223">[階層] ビューで [ **OrigamiCollection** ] オブジェクトを展開します。</span><span class="sxs-lookup"><span data-stu-id="0943b-223">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="0943b-224">**SphereCommands** スクリプトを、[階層] パネルの [ **Sphere1** ] オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0943b-224">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0943b-225">**SphereCommands** スクリプトを、[階層] パネルの [ **Sphere2** ] オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0943b-225">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0943b-226">編集するために Visual Studio でスクリプトを開き、既定のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0943b-226">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }
}
```

* <span data-ttu-id="0943b-227">アプリのエクスポート、ビルド、および HoloLens エミュレーターへのデプロイを行います。</span><span class="sxs-lookup"><span data-stu-id="0943b-227">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0943b-228">シーンを見て、球体の1つを中心にします。</span><span class="sxs-lookup"><span data-stu-id="0943b-228">Look around the scene, and center on one of the spheres.</span></span>
* <span data-ttu-id="0943b-229">Xbox コントローラーの **A** ボタンを押すか、space キーを押して選択ジェスチャをシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="0943b-229">Press the **A** button on the Xbox controller or press the Spacebar to simulate the Select gesture.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="0943b-230">第4章-音声</span><span class="sxs-lookup"><span data-stu-id="0943b-230">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/LxbOhnd2_GM]

<span data-ttu-id="0943b-231">この章では、次の2つの [音声コマンド](../../../design/voice-input.md)のサポートを追加します。 "リセット world" は、ドロップされた球体を元の場所に返し、"ドロップ球" を使用して球をフォールします。</span><span class="sxs-lookup"><span data-stu-id="0943b-231">In this chapter, we'll add support for two [voice commands](../../../design/voice-input.md): "Reset world" to returns the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="0943b-232">目標</span><span class="sxs-lookup"><span data-stu-id="0943b-232">Objectives</span></span>

* <span data-ttu-id="0943b-233">常にバックグラウンドで待機する音声コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="0943b-233">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="0943b-234">音声コマンドに反応するホログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="0943b-234">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="0943b-235">Instructions</span><span class="sxs-lookup"><span data-stu-id="0943b-235">Instructions</span></span>

* <span data-ttu-id="0943b-236">**Scripts** フォルダーで、 **SpeechManager** という名前のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0943b-236">In the **Scripts** folder, create a script named **SpeechManager** .</span></span>
* <span data-ttu-id="0943b-237">**SpeechManager** スクリプトを階層内の **OrigamiCollection** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0943b-237">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="0943b-238">Visual Studio で **SpeechManager** スクリプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="0943b-238">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="0943b-239">このコードをコピーして **SpeechManager.cs** に貼り付け、 **すべてを保存** します。</span><span class="sxs-lookup"><span data-stu-id="0943b-239">Copy and paste this code into **SpeechManager.cs** and **Save All** :</span></span>

```cs
using System.Collections.Generic;
using System.Linq;
using UnityEngine;
using UnityEngine.Windows.Speech;

public class SpeechManager : MonoBehaviour
{
    KeywordRecognizer keywordRecognizer = null;
    Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();

    // Use this for initialization
    void Start()
    {
        keywords.Add("Reset world", () =>
        {
            // Call the OnReset method on every descendant object.
            this.BroadcastMessage("OnReset");
        });

        keywords.Add("Drop Sphere", () =>
        {
            var focusObject = GazeGestureManager.Instance.FocusedObject;
            if (focusObject != null)
            {
                // Call the OnDrop method on just the focused object.
                focusObject.SendMessage("OnDrop", SendMessageOptions.DontRequireReceiver);
            }
        });

        // Tell the KeywordRecognizer about our keywords.
        keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());

        // Register a callback for the KeywordRecognizer and start recognizing!
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        System.Action keywordAction;
        if (keywords.TryGetValue(args.text, out keywordAction))
        {
            keywordAction.Invoke();
        }
    }
}
```

* <span data-ttu-id="0943b-240">Visual Studio で **SphereCommands** スクリプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="0943b-240">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="0943b-241">次のようにスクリプトを更新します。</span><span class="sxs-lookup"><span data-stu-id="0943b-241">Update the script to read as follows:</span></span>

```cs
using UnityEngine;

public class SphereCommands : MonoBehaviour
{
    Vector3 originalPosition;

    // Use this for initialization
    void Start()
    {
        // Grab the original local position of the sphere when the app starts.
        originalPosition = this.transform.localPosition;
    }

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // If the sphere has no Rigidbody component, add one to enable physics.
        if (!this.GetComponent<Rigidbody>())
        {
            var rigidbody = this.gameObject.AddComponent<Rigidbody>();
            rigidbody.collisionDetectionMode = CollisionDetectionMode.Continuous;
        }
    }

    // Called by SpeechManager when the user says the "Reset world" command
    void OnReset()
    {
        // If the sphere has a Rigidbody component, remove it to disable physics.
        var rigidbody = this.GetComponent<Rigidbody>();
        if (rigidbody != null)
        {
            rigidbody.isKinematic = true;
            Destroy(rigidbody);
        }

        // Put the sphere back into its original local position.
        this.transform.localPosition = originalPosition;
    }

    // Called by SpeechManager when the user says the "Drop sphere" command
    void OnDrop()
    {
        // Just do the same logic as a Select gesture.
        OnSelect();
    }
}
```

* <span data-ttu-id="0943b-242">アプリのエクスポート、ビルド、および HoloLens エミュレーターへのデプロイを行います。</span><span class="sxs-lookup"><span data-stu-id="0943b-242">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0943b-243">エミュレーターは PC のマイクをサポートし、音声に応答します。つまり、カーソルが球体の1つになるようにビューを調整し、"ドロップ球" と言います。</span><span class="sxs-lookup"><span data-stu-id="0943b-243">The emulator will support your PC's microphone and respond to your voice: adjust the view so the cursor is on one of the spheres, and say "Drop Sphere".</span></span>
* <span data-ttu-id="0943b-244">" **世界のリセット** " と言うと、最初の位置に戻ります。</span><span class="sxs-lookup"><span data-stu-id="0943b-244">Say " **Reset World** " to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="0943b-245">第5章-空間サウンド</span><span class="sxs-lookup"><span data-stu-id="0943b-245">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Xc3C4VA10w4]

<span data-ttu-id="0943b-246">この章では、アプリに音楽を追加し、特定のアクションに対してサウンド効果をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="0943b-246">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="0943b-247">[空間サウンド](../../../design/spatial-sound.md)を使用して、3d 空間内の特定の位置にサウンドを与えます。</span><span class="sxs-lookup"><span data-stu-id="0943b-247">We'll be using [spatial sound](../../../design/spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="0943b-248">目標</span><span class="sxs-lookup"><span data-stu-id="0943b-248">Objectives</span></span>

* <span data-ttu-id="0943b-249">世界中のホログラムを聞くことができます。</span><span class="sxs-lookup"><span data-stu-id="0943b-249">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="0943b-250">Instructions</span><span class="sxs-lookup"><span data-stu-id="0943b-250">Instructions</span></span>

* <span data-ttu-id="0943b-251">Unity で、上部のメニューから [ **> プロジェクトの設定を編集** します] [オーディオ] > 選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-251">In the Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="0943b-252">**Spatializer プラグイン** 設定を探し、[ **MS HRTF Spatializer** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-252">Find the **Spatializer Plugin** setting and select **MS HRTF Spatializer** .</span></span>
* <span data-ttu-id="0943b-253">[ **ホログラム** ] フォルダーから、[ **アンビエント** ] オブジェクトを [階層] パネルの **OrigamiCollection** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0943b-253">From the **Holograms** folder, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="0943b-254">[ **OrigamiCollection** ] を選択し、 **オーディオソース** コンポーネントを検索します。</span><span class="sxs-lookup"><span data-stu-id="0943b-254">Select **OrigamiCollection** and find the **Audio Source** component.</span></span> <span data-ttu-id="0943b-255">次のプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="0943b-255">Change these properties:</span></span>
  * <span data-ttu-id="0943b-256">**Spatialize** プロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="0943b-256">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="0943b-257">スリープ状態 **になって** いることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0943b-257">Check the **Play On Awake** .</span></span>
  * <span data-ttu-id="0943b-258">スライダーを右にドラッグして、 **空間 Blend** を **3d** に変更します。</span><span class="sxs-lookup"><span data-stu-id="0943b-258">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span>
  * <span data-ttu-id="0943b-259">**Loop** プロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="0943b-259">Check the **Loop** property.</span></span>
  * <span data-ttu-id="0943b-260">[ **3D サウンド設定** ] を展開し、 **ドップラーレベル** に「 **0.1** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0943b-260">Expand **3D Sound Settings** , and enter **0.1** for **Doppler Level** .</span></span>
  * <span data-ttu-id="0943b-261">**ボリュームのロール** アウトを **対数ロールオフ** に設定します。</span><span class="sxs-lookup"><span data-stu-id="0943b-261">Set **Volume Rolloff** to **Logarithmic Rolloff** .</span></span>
  * <span data-ttu-id="0943b-262">**最大距離** を **20** に設定します。</span><span class="sxs-lookup"><span data-stu-id="0943b-262">Set **Max Distance** to **20** .</span></span>
* <span data-ttu-id="0943b-263">**Scripts** フォルダーで、 **SphereSounds** という名前のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0943b-263">In the **Scripts** folder, create a script named **SphereSounds** .</span></span>
* <span data-ttu-id="0943b-264">**SphereSounds** を階層内の **Sphere1** オブジェクトと **Sphere2** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0943b-264">Drag **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="0943b-265">Visual Studio で **SphereSounds** を開き、次のコードを更新して **すべてを保存** します。</span><span class="sxs-lookup"><span data-stu-id="0943b-265">Open **SphereSounds** in Visual Studio, update the following code and **Save All** .</span></span>

```cs
using UnityEngine;

public class SphereSounds : MonoBehaviour
{
    AudioSource impactAudioSource = null;
    AudioSource rollingAudioSource = null;

    bool rolling = false;

    void Start()
    {
        // Add an AudioSource component and set up some defaults
        impactAudioSource = gameObject.AddComponent<AudioSource>();
        impactAudioSource.playOnAwake = false;
        impactAudioSource.spatialize = true;
        impactAudioSource.spatialBlend = 1.0f;
        impactAudioSource.dopplerLevel = 0.0f;
        impactAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        impactAudioSource.maxDistance = 20f;

        rollingAudioSource = gameObject.AddComponent<AudioSource>();
        rollingAudioSource.playOnAwake = false;
        rollingAudioSource.spatialize = true;
        rollingAudioSource.spatialBlend = 1.0f;
        rollingAudioSource.dopplerLevel = 0.0f;
        rollingAudioSource.rolloffMode = AudioRolloffMode.Logarithmic;
        rollingAudioSource.maxDistance = 20f;
        rollingAudioSource.loop = true;

        // Load the Sphere sounds from the Resources folder
        impactAudioSource.clip = Resources.Load<AudioClip>("Impact");
        rollingAudioSource.clip = Resources.Load<AudioClip>("Rolling");
    }

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Play an impact sound if the sphere impacts strongly enough.
        if (collision.relativeVelocity.magnitude >= 0.1f)
        {
            impactAudioSource.Play();
        }
    }

    // Occurs each frame that this object continues to collide with another object
    void OnCollisionStay(Collision collision)
    {
        Rigidbody rigid = gameObject.GetComponent<Rigidbody>();

        // Play a rolling sound if the sphere is rolling fast enough.
        if (!rolling && rigid.velocity.magnitude >= 0.01f)
        {
            rolling = true;
            rollingAudioSource.Play();
        }
        // Stop the rolling sound if rolling slows down.
        else if (rolling && rigid.velocity.magnitude < 0.01f)
        {
            rolling = false;
            rollingAudioSource.Stop();
        }
    }

    // Occurs when this object stops colliding with another object
    void OnCollisionExit(Collision collision)
    {
        // Stop the rolling sound if the object falls off and stops colliding.
        if (rolling)
        {
            rolling = false;
            impactAudioSource.Stop();
            rollingAudioSource.Stop();
        }
    }
}
```

* <span data-ttu-id="0943b-266">スクリプトを保存し、Unity に戻ります。</span><span class="sxs-lookup"><span data-stu-id="0943b-266">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="0943b-267">アプリのエクスポート、ビルド、および HoloLens エミュレーターへのデプロイを行います。</span><span class="sxs-lookup"><span data-stu-id="0943b-267">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0943b-268">すべての効果を取得するための磨耗のヘッドホンと、より近くに移動し、サウンドが変化することを確認します。</span><span class="sxs-lookup"><span data-stu-id="0943b-268">Wear headphones to get the full effect, and move closer and further from the Stage to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="0943b-269">Chapter 6-空間マッピング</span><span class="sxs-lookup"><span data-stu-id="0943b-269">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/S-517Y63Cnk]

<span data-ttu-id="0943b-270">ここでは、 [空間マッピング](../../../design/spatial-mapping.md) を使用して、ゲームボードを現実世界の実際のオブジェクトに配置します。</span><span class="sxs-lookup"><span data-stu-id="0943b-270">Now we are going to use [spatial mapping](../../../design/spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="0943b-271">目標</span><span class="sxs-lookup"><span data-stu-id="0943b-271">Objectives</span></span>

* <span data-ttu-id="0943b-272">実際の世界を仮想環境に移します。</span><span class="sxs-lookup"><span data-stu-id="0943b-272">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="0943b-273">自分にとって最も重要な場所にホログラムを配置します。</span><span class="sxs-lookup"><span data-stu-id="0943b-273">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="0943b-274">Instructions</span><span class="sxs-lookup"><span data-stu-id="0943b-274">Instructions</span></span>

* <span data-ttu-id="0943b-275">[プロジェクト] パネルの [ **ホログラム** ] フォルダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0943b-275">Click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="0943b-276">**空間マッピング** 資産を **階層** のルートにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0943b-276">Drag the **Spatial Mapping** asset into the root of the **Hierarchy** .</span></span>
* <span data-ttu-id="0943b-277">階層内の **空間マッピング** オブジェクトをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0943b-277">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="0943b-278">[ **インスペクター] パネル** で、次のプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="0943b-278">In the **Inspector panel** , change the following properties:</span></span>
  * <span data-ttu-id="0943b-279">[ **ビジュアルメッシュの描画** ] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="0943b-279">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="0943b-280">[ **素材の描画** ] を見つけ、右側にある円をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0943b-280">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="0943b-281">上部にある検索フィールドに「 **ワイヤーフレーム** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0943b-281">Type " **wireframe** " into the search field at the top.</span></span> <span data-ttu-id="0943b-282">結果をクリックし、ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0943b-282">Click on the result and then close the window.</span></span>
* <span data-ttu-id="0943b-283">アプリのエクスポート、ビルド、および HoloLens エミュレーターへのデプロイを行います。</span><span class="sxs-lookup"><span data-stu-id="0943b-283">Export, build and deploy the app to the HoloLens emulator.</span></span>
* <span data-ttu-id="0943b-284">アプリを実行すると、前にスキャンした実際の生活室のメッシュがワイヤーフレームでレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="0943b-284">When the app runs, a mesh of a previously scanned real-world living room will be rendered in wireframe.</span></span>
* <span data-ttu-id="0943b-285">ローリング球がステージとフロアにどのように分かれているかを見てください。</span><span class="sxs-lookup"><span data-stu-id="0943b-285">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="0943b-286">ここでは、OrigamiCollection を新しい場所に移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0943b-286">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="0943b-287">**Scripts** フォルダーで、 **TapToPlaceParent** という名前のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0943b-287">In the **Scripts** folder, create a script named **TapToPlaceParent** .</span></span>
* <span data-ttu-id="0943b-288">**階層** で、 **OrigamiCollection** を展開し、[ **ステージ** ] オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="0943b-288">In the **Hierarchy** , expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="0943b-289">**TapToPlaceParent** スクリプトを Stage オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0943b-289">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="0943b-290">Visual Studio で **TapToPlaceParent** スクリプトを開き、次のように更新します。</span><span class="sxs-lookup"><span data-stu-id="0943b-290">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class TapToPlaceParent : MonoBehaviour
{
    bool placing = false;

    // Called by GazeGestureManager when the user performs a Select gesture
    void OnSelect()
    {
        // On each Select gesture, toggle whether the user is in placing mode.
        placing = !placing;

        // If the user is in placing mode, display the spatial mapping mesh.
        if (placing)
        {
            SpatialMapping.Instance.DrawVisualMeshes = true;
        }
        // If the user is not in placing mode, hide the spatial mapping mesh.
        else
        {
            SpatialMapping.Instance.DrawVisualMeshes = false;
        }
    }

    // Update is called once per frame
    void Update()
    {
        // If the user is in placing mode,
        // update the placement to match the user's gaze.

        if (placing)
        {
            // Do a raycast into the world that will only hit the Spatial Mapping mesh.
            var headPosition = Camera.main.transform.position;
            var gazeDirection = Camera.main.transform.forward;

            RaycastHit hitInfo;
            if (Physics.Raycast(headPosition, gazeDirection, out hitInfo,
                30.0f, SpatialMapping.PhysicsRaycastMask))
            {
                // Move this object's parent object to
                // where the raycast hit the Spatial Mapping mesh.
                this.transform.parent.position = hitInfo.point;

                // Rotate this object's parent object to face the user.
                Quaternion toQuat = Camera.main.transform.localRotation;
                toQuat.x = 0;
                toQuat.z = 0;
                this.transform.parent.rotation = toQuat;
            }
        }
    }
}
```

* <span data-ttu-id="0943b-291">アプリをエクスポート、ビルド、デプロイします。</span><span class="sxs-lookup"><span data-stu-id="0943b-291">Export, build and deploy the app.</span></span>
* <span data-ttu-id="0943b-292">これで、特定の場所にゲームを配置できるようになりました。これを行うには、選択ジェスチャ ( **a** または space キー) を使用してから新しい場所に移動し、もう一度 select ジェスチャを使用します。</span><span class="sxs-lookup"><span data-stu-id="0943b-292">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture ( **A** or Spacebar) and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="the-end"></a><span data-ttu-id="0943b-293">最後です</span><span class="sxs-lookup"><span data-stu-id="0943b-293">The end</span></span>

<span data-ttu-id="0943b-294">これがこのチュートリアルの終わりです。</span><span class="sxs-lookup"><span data-stu-id="0943b-294">And that's the end of this tutorial!</span></span>

<span data-ttu-id="0943b-295">学習した内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0943b-295">You learned:</span></span>

* <span data-ttu-id="0943b-296">Unity で holographic アプリを作成する方法。</span><span class="sxs-lookup"><span data-stu-id="0943b-296">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="0943b-297">見つめ、ジェスチャ、音声、サウンド、および空間マッピングを使用する方法。</span><span class="sxs-lookup"><span data-stu-id="0943b-297">How to make use of gaze, gesture, voice, sounds, and spatial mapping.</span></span>
* <span data-ttu-id="0943b-298">Visual Studio を使用してアプリをビルドしてデプロイする方法。</span><span class="sxs-lookup"><span data-stu-id="0943b-298">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="0943b-299">これで、独自の holographic アプリの作成を開始する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="0943b-299">You are now ready to start creating your own holographic apps!</span></span>

## <a name="see-also"></a><span data-ttu-id="0943b-300">関連項目</span><span class="sxs-lookup"><span data-stu-id="0943b-300">See also</span></span>

* [<span data-ttu-id="0943b-301">MR の基本 101:デバイスを使用した完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="0943b-301">MR Basics 101: Complete project with device</span></span>](holograms-101.md)
* [<span data-ttu-id="0943b-302">視線入力</span><span class="sxs-lookup"><span data-stu-id="0943b-302">Gaze</span></span>](../../../design/gaze-and-commit.md)
* [<span data-ttu-id="0943b-303">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="0943b-303">Head-gaze and commit</span></span>](../../../design/gaze-and-commit.md)
* [<span data-ttu-id="0943b-304">音声入力</span><span class="sxs-lookup"><span data-stu-id="0943b-304">Voice input</span></span>](../../../design/voice-input.md)
* [<span data-ttu-id="0943b-305">立体音響</span><span class="sxs-lookup"><span data-stu-id="0943b-305">Spatial sound</span></span>](../../../design/spatial-sound.md)
* [<span data-ttu-id="0943b-306">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="0943b-306">Spatial mapping</span></span>](../../../design/spatial-mapping.md)
