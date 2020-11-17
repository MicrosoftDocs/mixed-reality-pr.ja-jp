---
title: MR の基本 101 - デバイスを使用した完全なプロジェクト
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、Windows Mixed Reality の基本を学習してください。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: mixed reality、Windows Mixed Reality、HoloLens、ホログラム、academy、チュートリアル、HoloLens、Mixed Reality Academy、unity、mixed reality ヘッドセット、windows Mixed reality ヘッドセット、virtual reality ヘッドセット、Windows 10
ms.openlocfilehash: f2725db17a2991b956c777ee7106b7f094582f77
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677201"
---
# <a name="mr-basics-101-complete-project-with-device"></a><span data-ttu-id="0c35f-104">MR の基本 101:デバイスを使用した完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="0c35f-104">MR Basics 101: Complete project with device</span></span>

<br>

>[!NOTE]
><span data-ttu-id="0c35f-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="0c35f-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0c35f-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="0c35f-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0c35f-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。</span><span class="sxs-lookup"><span data-stu-id="0c35f-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0c35f-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0c35f-109">HoloLens 2 向けには、[新しいチュートリアル シリーズ](mrlearning-base.md)が投稿されています。</span><span class="sxs-lookup"><span data-stu-id="0c35f-109">[A new series of tutorials](mrlearning-base.md) has been posted for HoloLens 2.</span></span>

<br>

>[!VIDEO https://www.youtube.com/embed/XKIIEC5BMWg]

<span data-ttu-id="0c35f-110">このチュートリアルでは、Unity でビルドされた完全なプロジェクトについて説明します。これは、 [宝石](../../../design/gaze-and-commit.md)、 [ジェスチャ](../../../design/gaze-and-commit.md#composite-gestures)、 [音声入力](../../../design/voice-input.md)、 [空間サウンド](../../../design/spatial-sound.md) 、 [空間マッピング](../../../design/spatial-mapping.md)など、HoloLens のコア Windows Mixed Reality 機能を示しています。</span><span class="sxs-lookup"><span data-stu-id="0c35f-110">This tutorial will walk you through a complete project, built in Unity, that demonstrates core Windows Mixed Reality features on HoloLens including [gaze](../../../design/gaze-and-commit.md), [gestures](../../../design/gaze-and-commit.md#composite-gestures), [voice input](../../../design/voice-input.md), [spatial sound](../../../design/spatial-sound.md) and [spatial mapping](../../../design/spatial-mapping.md).</span></span>

<span data-ttu-id="0c35f-111">このチュートリアルの完了には約1時間かかります。</span><span class="sxs-lookup"><span data-stu-id="0c35f-111">The tutorial will take approximately 1 hour to complete.</span></span>

## <a name="device-support"></a><span data-ttu-id="0c35f-112">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="0c35f-112">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0c35f-113">コース</span><span class="sxs-lookup"><span data-stu-id="0c35f-113">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0c35f-114"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0c35f-114"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0c35f-115"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="0c35f-115"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="0c35f-116">MR の基本 101:デバイスを使用した完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="0c35f-116">MR Basics 101: Complete project with device</span></span></td><td style="text-align: center;"> <span data-ttu-id="0c35f-117">✔️</span><span class="sxs-lookup"><span data-stu-id="0c35f-117">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="0c35f-118">開始する前に</span><span class="sxs-lookup"><span data-stu-id="0c35f-118">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="0c35f-119">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="0c35f-119">Prerequisites</span></span>

* <span data-ttu-id="0c35f-120">適切な [ツールがインストール](../../install-the-tools.md)された WINDOWS 10 PC。</span><span class="sxs-lookup"><span data-stu-id="0c35f-120">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md).</span></span>
* <span data-ttu-id="0c35f-121">[開発用に構成され](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)た HoloLens デバイス。</span><span class="sxs-lookup"><span data-stu-id="0c35f-121">A HoloLens device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="0c35f-122">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="0c35f-122">Project files</span></span>

* <span data-ttu-id="0c35f-123">プロジェクトに必要な [ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-123">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-101.zip) required by the project.</span></span> <span data-ttu-id="0c35f-124">Unity 2017.2 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="0c35f-124">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="0c35f-125">引き続き Unity 5.6 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="0c35f-125">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-101.zip).</span></span>
  * <span data-ttu-id="0c35f-126">引き続き Unity 5.5 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="0c35f-126">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-101.zip).</span></span>
  * <span data-ttu-id="0c35f-127">引き続き Unity 5.4 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="0c35f-127">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-101.zip).</span></span>
* <span data-ttu-id="0c35f-128">ファイルをデスクトップまたはその他の簡単な場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-128">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="0c35f-129">フォルダー名は **Origami** のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-129">Keep the folder name as **Origami**.</span></span>

>[!NOTE]
><span data-ttu-id="0c35f-130">ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101)ます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-130">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-101).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="0c35f-131">Chapter 1-"Holo" ワールド</span><span class="sxs-lookup"><span data-stu-id="0c35f-131">Chapter 1 - "Holo" world</span></span>

>[!VIDEO https://www.youtube.com/embed/PmtZGjYFroY]

<span data-ttu-id="0c35f-132">この章では、最初の Unity プロジェクトをセットアップし、ビルドとデプロイのプロセスをステップ実行します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-132">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="0c35f-133">目標</span><span class="sxs-lookup"><span data-stu-id="0c35f-133">Objectives</span></span>

* <span data-ttu-id="0c35f-134">Holographic 開発用に Unity を設定します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-134">Set up Unity for holographic development.</span></span>
* <span data-ttu-id="0c35f-135">ホログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-135">Make a hologram.</span></span>
* <span data-ttu-id="0c35f-136">作成したホログラムを確認します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-136">See a hologram that you made.</span></span>

### <a name="instructions"></a><span data-ttu-id="0c35f-137">手順</span><span class="sxs-lookup"><span data-stu-id="0c35f-137">Instructions</span></span>

* <span data-ttu-id="0c35f-138">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-138">Start Unity.</span></span>
* <span data-ttu-id="0c35f-139">**[Open (開く)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-139">Select **Open**.</span></span>
* <span data-ttu-id="0c35f-140">前にアーカイブしていない **Origami** フォルダーとして場所を入力します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-140">Enter location as the **Origami** folder you previously un-archived.</span></span>
* <span data-ttu-id="0c35f-141">[ **Origami** ] を選択し、[ **フォルダーの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-141">Select **Origami** and click **Select Folder**.</span></span>
* <span data-ttu-id="0c35f-142">**Origami** プロジェクトにはシーンが含まれていないので、[**ファイル**] [  /  **シーンとして保存**] を使用して、空の既定のシーンを新しいファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-142">Since the **Origami** project does not contain a scene, save the empty default scene to a new file using: **File** / **Save Scene As**.</span></span>
* <span data-ttu-id="0c35f-143">新しいシーンに **Origami** という名前を **付け** 、[保存] ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-143">Name the new scene **Origami** and press the **Save** button.</span></span>

#### <a name="setup-the-main-virtual-camera"></a><span data-ttu-id="0c35f-144">メインの仮想カメラをセットアップする</span><span class="sxs-lookup"><span data-stu-id="0c35f-144">Setup the main virtual camera</span></span>

* <span data-ttu-id="0c35f-145">**[Hierarchy]\(階層\) パネル** で、 **[Main Camera]\(メイン カメラ\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-145">In the **Hierarchy Panel**, select **Main Camera**.</span></span>
* <span data-ttu-id="0c35f-146">**インスペクター** で、変換位置を **0、0、0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-146">In the **Inspector** set its transform position to **0,0,0**.</span></span>
* <span data-ttu-id="0c35f-147">" **Clear Flags** " プロパティを見つけ、ドロップ **ダウンから [** **単色**] に変更します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-147">Find the **Clear Flags** property, and change the dropdown from **Skybox** to **Solid color**.</span></span>
* <span data-ttu-id="0c35f-148">**[Background]\(背景\)** フィールドをクリックして、カラー ピッカーを開きます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-148">Click on the **Background** field to open a color picker.</span></span>
* <span data-ttu-id="0c35f-149">**R、G、B、A** を **0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-149">Set **R, G, B, and A** to **0**.</span></span>

#### <a name="setup-the-scene"></a><span data-ttu-id="0c35f-150">シーンを設定する</span><span class="sxs-lookup"><span data-stu-id="0c35f-150">Setup the scene</span></span>

* <span data-ttu-id="0c35f-151">[ **階層] パネル** で、[ **作成** ] をクリックし、[ **空の作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-151">In the **Hierarchy Panel**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="0c35f-152">新しい [作成] **オブジェクト** を右クリックし、[名前の変更] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-152">Right-click the new **GameObject** and select Rename.</span></span> <span data-ttu-id="0c35f-153">**OrigamiCollection** オブジェクトの名前を「」に変更します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-153">Rename the GameObject to **OrigamiCollection**.</span></span>
* <span data-ttu-id="0c35f-154">[プロジェクト] パネルの [ **ホログラム** ] フォルダーから ([アセット] を展開して [ホログラム] を選択するか、[プロジェクト] パネルで [ホログラム] フォルダーをダブルクリックします)。</span><span class="sxs-lookup"><span data-stu-id="0c35f-154">From the **Holograms** folder in the Project Panel (expand Assets and select Holograms or double click the Holograms folder in the Project Panel):</span></span>
  * <span data-ttu-id="0c35f-155">**ステージ** を階層にドラッグして、 **OrigamiCollection** の子にします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-155">Drag **Stage** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="0c35f-156">**Sphere1** を階層内にドラッグして、 **OrigamiCollection** の子にします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-156">Drag **Sphere1** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
  * <span data-ttu-id="0c35f-157">**Sphere2** を階層内にドラッグして、 **OrigamiCollection** の子にします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-157">Drag **Sphere2** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="0c35f-158">[**階層] パネル** で **指向性ライト** オブジェクトを右クリックし、[**削除**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-158">Right-click the **Directional Light** object in the **Hierarchy Panel** and select **Delete**.</span></span>
* <span data-ttu-id="0c35f-159">[**ホログラム**] フォルダーから、[**階層] パネル** のルートに **ライト** をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-159">From the **Holograms** folder, drag **Lights** into the root of the **Hierarchy Panel**.</span></span>
* <span data-ttu-id="0c35f-160">**階層** で、 **OrigamiCollection** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-160">In the **Hierarchy**, select the **OrigamiCollection**.</span></span>
* <span data-ttu-id="0c35f-161">**インスペクター** で、変換位置を **0、-0.5、2.0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-161">In the **Inspector**, set the transform position to **0, -0.5, 2.0**.</span></span>
* <span data-ttu-id="0c35f-162">Unity の [ **再生** ] ボタンをクリックして、ホログラムをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-162">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="0c35f-163">プレビューウィンドウに Origami オブジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-163">You should see the Origami objects in the preview window.</span></span>
* <span data-ttu-id="0c35f-164">プレビューモードを停止するには、もう一度 **Play** を押します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-164">Press **Play** a second time to stop preview mode.</span></span>

#### <a name="export-the-project-from-unity-to-visual-studio"></a><span data-ttu-id="0c35f-165">Unity から Visual Studio にプロジェクトをエクスポートする</span><span class="sxs-lookup"><span data-stu-id="0c35f-165">Export the project from Unity to Visual Studio</span></span>

* <span data-ttu-id="0c35f-166">Unity で、[ **ファイル > ビルド設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-166">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="0c35f-167">[**プラットフォーム**] ボックスの一覧の [**ユニバーサル Windows プラットフォーム**] を選択し、[**プラットフォームの切り替え**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-167">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="0c35f-168">**SDK** を **Universal 10** に設定し、**ビルドの種類** を **D3D** に設定します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-168">Set **SDK** to **Universal 10** and **Build Type** to **D3D**.</span></span>
* <span data-ttu-id="0c35f-169">**Unity C# プロジェクト** を確認します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-169">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="0c35f-170">シーンを追加するには、[開いている **シーンの追加** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-170">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="0c35f-171">[**ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-171">Click **Build**.</span></span>
* <span data-ttu-id="0c35f-172">表示された [エクスプローラー] ウィンドウで、"App" という名前の **新しいフォルダー** を作成します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-172">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="0c35f-173">**アプリフォルダー** をシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-173">Single click the **App Folder**.</span></span>
* <span data-ttu-id="0c35f-174">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-174">Press **Select Folder**.</span></span>
* <span data-ttu-id="0c35f-175">Unity が完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-175">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="0c35f-176">**アプリ** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-176">Open the **App** folder.</span></span>
* <span data-ttu-id="0c35f-177">**Origami** を開きます (ダブルクリックします)。</span><span class="sxs-lookup"><span data-stu-id="0c35f-177">Open (double click) **Origami.sln**.</span></span>
* <span data-ttu-id="0c35f-178">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に変更し、ARM から **X86** に変更します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-178">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="0c35f-179">[デバイス] ボタンの横にある矢印をクリックし、[ **リモートコンピューター** ] を選択して wi-fi 経由で展開します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-179">Click on the arrow next to the Device button, and select **Remote Machine** to deploy over Wi-Fi.</span></span>
  * <span data-ttu-id="0c35f-180">**アドレス** を HoloLens の名前または IP アドレスに設定します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-180">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="0c35f-181">デバイスの IP アドレスがわからない場合は、[設定] の [**ネットワーク & Internet > 詳細オプション >** 確認するか、cortana **に "Cortana さん、どのような IP アドレスがあるか" を** 確認してください。</span><span class="sxs-lookup"><span data-stu-id="0c35f-181">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
  * <span data-ttu-id="0c35f-182">HoloLens が USB 経由で接続されている場合は、代わりに [ **デバイス** ] を選択して usb 経由で展開することができます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-182">If the HoloLens is attached over USB, you may instead select **Device** to deploy over USB.</span></span>
  * <span data-ttu-id="0c35f-183">[ **認証モード** ( **ユニバーサル**) に設定したままにします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-183">Leave the **Authentication Mode** set to **Universal**.</span></span>
  * <span data-ttu-id="0c35f-184">[**選択] を** クリック</span><span class="sxs-lookup"><span data-stu-id="0c35f-184">Click **Select**</span></span>

* <span data-ttu-id="0c35f-185">[デバッグ] をクリックして [ **デバッグなしで開始** ] を >、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-185">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="0c35f-186">初めてデバイスをデプロイする場合は、 [Visual Studio とペアリング](../../platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c35f-186">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>

* <span data-ttu-id="0c35f-187">これで、Origami プロジェクトが作成され、HoloLens にデプロイされた後、が実行されます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-187">The Origami project will now build, deploy to your HoloLens, and then run.</span></span>
* <span data-ttu-id="0c35f-188">HoloLens に移動し、新しいホログラムを見てみてください。</span><span class="sxs-lookup"><span data-stu-id="0c35f-188">Put on your HoloLens and look around to see your new holograms.</span></span>

## <a name="chapter-2---gaze"></a><span data-ttu-id="0c35f-189">第2章-宝石</span><span class="sxs-lookup"><span data-stu-id="0c35f-189">Chapter 2 - Gaze</span></span>

>[!VIDEO https://www.youtube.com/embed/MSO2BoFSQbM]

<span data-ttu-id="0c35f-190">この章では、最初に3つの方法を使用して、ホログラムと対話する方法を紹介[します。](../../../design/gaze-and-commit.md)</span><span class="sxs-lookup"><span data-stu-id="0c35f-190">In this chapter, we are going to introduce the first of three ways of interacting with your holograms -- [gaze](../../../design/gaze-and-commit.md).</span></span>

### <a name="objectives"></a><span data-ttu-id="0c35f-191">目標</span><span class="sxs-lookup"><span data-stu-id="0c35f-191">Objectives</span></span>

* <span data-ttu-id="0c35f-192">世界でロックされているカーソルを使用して、宝石を視覚化します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-192">Visualize your gaze using a world-locked cursor.</span></span>

### <a name="instructions"></a><span data-ttu-id="0c35f-193">手順</span><span class="sxs-lookup"><span data-stu-id="0c35f-193">Instructions</span></span>

* <span data-ttu-id="0c35f-194">Unity プロジェクトに戻り、[ビルドの設定] ウィンドウがまだ開いている場合は閉じます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-194">Go back to your Unity project, and close the Build Settings window if it's still open.</span></span>
* <span data-ttu-id="0c35f-195">[**プロジェクト] パネル** で [**ホログラム**] フォルダーを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-195">Select the **Holograms** folder in the **Project panel**.</span></span>
* <span data-ttu-id="0c35f-196">**カーソル** オブジェクトをルートレベルの [**階層] パネル** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-196">Drag the **Cursor** object into the **Hierarchy panel** at the root level.</span></span>
* <span data-ttu-id="0c35f-197">**カーソル** オブジェクトをダブルクリックすると、詳細が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-197">Double-click on the **Cursor** object to take a closer look at it.</span></span>
* <span data-ttu-id="0c35f-198">[プロジェクト] パネルの [ **Scripts** ] フォルダーを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-198">Right-click on the **Scripts** folder in the Project panel.</span></span>
* <span data-ttu-id="0c35f-199">[ **作成** ] サブメニューをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-199">Click the **Create** sub-menu.</span></span>
* <span data-ttu-id="0c35f-200">**C# スクリプト** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-200">Select **C# Script**.</span></span>
* <span data-ttu-id="0c35f-201">スクリプトに **WorldCursor** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-201">Name the script **WorldCursor**.</span></span> <span data-ttu-id="0c35f-202">注: 名前は大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-202">Note: The name is case-sensitive.</span></span> <span data-ttu-id="0c35f-203">.Cs 拡張子を追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0c35f-203">You do not need to add the .cs extension.</span></span>
* <span data-ttu-id="0c35f-204">[**階層] パネル** で **カーソル** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-204">Select the **Cursor** object in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="0c35f-205">**WorldCursor** スクリプトを [**インスペクター] パネル** にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-205">Drag and drop the **WorldCursor** script into the **Inspector panel**.</span></span>
* <span data-ttu-id="0c35f-206">**WorldCursor** スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-206">Double-click the **WorldCursor** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="0c35f-207">このコードをコピーして **WorldCursor.cs** に貼り付け、 **すべて保存** します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-207">Copy and paste this code into **WorldCursor.cs** and **Save All**.</span></span>

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

            // Move the cursor to the point where the raycast hit.
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

* <span data-ttu-id="0c35f-208">**ファイル > ビルド設定** からアプリをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-208">Rebuild the app from **File > Build Settings**.</span></span>
* <span data-ttu-id="0c35f-209">以前に HoloLens にデプロイするために使用した Visual Studio ソリューションに戻ります。</span><span class="sxs-lookup"><span data-stu-id="0c35f-209">Return to the Visual Studio solution previously used to deploy to your HoloLens.</span></span>
* <span data-ttu-id="0c35f-210">メッセージが表示されたら、[すべて再読み込み] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-210">Select 'Reload All' when prompted.</span></span>
* <span data-ttu-id="0c35f-211">[ **デバッグ]、[デバッグなしで開始] の順にクリック >** 、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-211">Click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="0c35f-212">次に、シーンを見て、カーソルがオブジェクトの形状とどのように対話するかを確認します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-212">Now look around the scene and notice how the cursor interacts with the shape of objects.</span></span>

## <a name="chapter-3---gestures"></a><span data-ttu-id="0c35f-213">第3章-ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="0c35f-213">Chapter 3 - Gestures</span></span>

>[!VIDEO https://www.youtube.com/embed/kW3ThJ2MbvQ]

<span data-ttu-id="0c35f-214">この章では、 [ジェスチャ](../../../design/gaze-and-commit.md#composite-gestures)のサポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-214">In this chapter, we'll add support for [gestures](../../../design/gaze-and-commit.md#composite-gestures).</span></span> <span data-ttu-id="0c35f-215">ユーザーがペーパー球を選択すると、Unity の物理エンジンを使用して重力をオンにすることで、球がフォールされるようになります。</span><span class="sxs-lookup"><span data-stu-id="0c35f-215">When the user selects a paper sphere, we'll make the sphere fall by turning on gravity using Unity's physics engine.</span></span>

### <a name="objectives"></a><span data-ttu-id="0c35f-216">目標</span><span class="sxs-lookup"><span data-stu-id="0c35f-216">Objectives</span></span>

* <span data-ttu-id="0c35f-217">選択ジェスチャでホログラムを制御します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-217">Control your holograms with the Select gesture.</span></span>

### <a name="instructions"></a><span data-ttu-id="0c35f-218">手順</span><span class="sxs-lookup"><span data-stu-id="0c35f-218">Instructions</span></span>

<span data-ttu-id="0c35f-219">まず、スクリプトを作成してから、選択したジェスチャを検出できるようにします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-219">We'll start by creating a script then can detect the Select gesture.</span></span>

* <span data-ttu-id="0c35f-220">**Scripts** フォルダーで、 **GazeGestureManager** という名前のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-220">In the **Scripts** folder, create a script named **GazeGestureManager**.</span></span>
* <span data-ttu-id="0c35f-221">**GazeGestureManager** スクリプトを階層内の **OrigamiCollection** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-221">Drag the **GazeGestureManager** script onto the **OrigamiCollection** object in the Hierarchy.</span></span>
* <span data-ttu-id="0c35f-222">Visual Studio で **GazeGestureManager** スクリプトを開き、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-222">Open the **GazeGestureManager** script in Visual Studio and add the following code:</span></span>

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
    void Awake()
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

* <span data-ttu-id="0c35f-223">Scripts フォルダーに、今度は **SphereCommands** という名前の別のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-223">Create another script in the Scripts folder, this time named **SphereCommands**.</span></span>
* <span data-ttu-id="0c35f-224">[階層] ビューで [ **OrigamiCollection** ] オブジェクトを展開します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-224">Expand the **OrigamiCollection** object in the Hierarchy view.</span></span>
* <span data-ttu-id="0c35f-225">**SphereCommands** スクリプトを、[階層] パネルの [ **Sphere1** ] オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-225">Drag the **SphereCommands** script onto the **Sphere1** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0c35f-226">**SphereCommands** スクリプトを、[階層] パネルの [ **Sphere2** ] オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-226">Drag the **SphereCommands** script onto the **Sphere2** object in the Hierarchy panel.</span></span>
* <span data-ttu-id="0c35f-227">編集するために Visual Studio でスクリプトを開き、既定のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-227">Open the script in Visual Studio for editing, and replace the default code with this:</span></span>

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

* <span data-ttu-id="0c35f-228">アプリのエクスポート、ビルド、および HoloLens へのデプロイを行います。</span><span class="sxs-lookup"><span data-stu-id="0c35f-228">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0c35f-229">いずれかの球体を確認します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-229">Look at one of the spheres.</span></span>
* <span data-ttu-id="0c35f-230">選択ジェスチャを実行し、球が下の画面にあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-230">Perform the select gesture and watch the sphere drop onto the surface below.</span></span>

## <a name="chapter-4---voice"></a><span data-ttu-id="0c35f-231">第4章-音声</span><span class="sxs-lookup"><span data-stu-id="0c35f-231">Chapter 4 - Voice</span></span>

>[!VIDEO https://www.youtube.com/embed/1-Aq0VVtHM8]

<span data-ttu-id="0c35f-232">この章では、2つの [音声コマンド](../../../design/voice-input.md)のサポートを追加します。 "リセットワールド" は、ドロップされた球体を元の場所に返し、"球を落下させる" と球を作成します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-232">In this chapter, we'll add support for two [voice commands](../../../design/voice-input.md): "Reset world" to return the dropped spheres to their original location, and "Drop sphere" to make the sphere fall.</span></span>

### <a name="objectives"></a><span data-ttu-id="0c35f-233">目標</span><span class="sxs-lookup"><span data-stu-id="0c35f-233">Objectives</span></span>

* <span data-ttu-id="0c35f-234">常にバックグラウンドで待機する音声コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-234">Add voice commands that always listen in the background.</span></span>
* <span data-ttu-id="0c35f-235">音声コマンドに反応するホログラムを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-235">Create a hologram that reacts to a voice command.</span></span>

### <a name="instructions"></a><span data-ttu-id="0c35f-236">手順</span><span class="sxs-lookup"><span data-stu-id="0c35f-236">Instructions</span></span>

* <span data-ttu-id="0c35f-237">**Scripts** フォルダーで、 **SpeechManager** という名前のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-237">In the **Scripts** folder, create a script named **SpeechManager**.</span></span>
* <span data-ttu-id="0c35f-238">**SpeechManager** スクリプトを階層内の **OrigamiCollection** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-238">Drag the **SpeechManager** script onto the **OrigamiCollection** object in the Hierarchy</span></span>
* <span data-ttu-id="0c35f-239">Visual Studio で **SpeechManager** スクリプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-239">Open the **SpeechManager** script in Visual Studio.</span></span>
* <span data-ttu-id="0c35f-240">このコードをコピーして **SpeechManager.cs** に貼り付け、 **すべてを保存** します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-240">Copy and paste this code into **SpeechManager.cs** and **Save All**:</span></span>

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

* <span data-ttu-id="0c35f-241">Visual Studio で **SphereCommands** スクリプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-241">Open the **SphereCommands** script in Visual Studio.</span></span>
* <span data-ttu-id="0c35f-242">次のようにスクリプトを更新します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-242">Update the script to read as follows:</span></span>

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

* <span data-ttu-id="0c35f-243">アプリのエクスポート、ビルド、および HoloLens へのデプロイを行います。</span><span class="sxs-lookup"><span data-stu-id="0c35f-243">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0c35f-244">球体の1つを見て、"**ドロップ球**" と言います。</span><span class="sxs-lookup"><span data-stu-id="0c35f-244">Look at one of the spheres, and say "**Drop Sphere**".</span></span>
* <span data-ttu-id="0c35f-245">"**世界のリセット**" と言うと、最初の位置に戻ります。</span><span class="sxs-lookup"><span data-stu-id="0c35f-245">Say "**Reset World**" to bring them back to their initial positions.</span></span>

## <a name="chapter-5---spatial-sound"></a><span data-ttu-id="0c35f-246">第5章-空間サウンド</span><span class="sxs-lookup"><span data-stu-id="0c35f-246">Chapter 5 - Spatial sound</span></span>

>[!VIDEO https://www.youtube.com/embed/Aj4de5Ncbfo]

<span data-ttu-id="0c35f-247">この章では、アプリに音楽を追加し、特定のアクションに対してサウンド効果をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-247">In this chapter, we'll add music to the app, and then trigger sound effects on certain actions.</span></span> <span data-ttu-id="0c35f-248">[空間サウンド](../../../design/spatial-sound.md)を使用して、3d 空間内の特定の位置にサウンドを与えます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-248">We'll be using [spatial sound](../../../design/spatial-sound.md) to give sounds a specific location in 3D space.</span></span>

### <a name="objectives"></a><span data-ttu-id="0c35f-249">目標</span><span class="sxs-lookup"><span data-stu-id="0c35f-249">Objectives</span></span>

* <span data-ttu-id="0c35f-250">世界中のホログラムを聞くことができます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-250">Hear holograms in your world.</span></span>

### <a name="instructions"></a><span data-ttu-id="0c35f-251">手順</span><span class="sxs-lookup"><span data-stu-id="0c35f-251">Instructions</span></span>

* <span data-ttu-id="0c35f-252">Unity で、上部のメニューから [ **> プロジェクトの設定**] [オーディオの > の編集] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-252">In Unity select from the top menu **Edit > Project Settings > Audio**</span></span>
* <span data-ttu-id="0c35f-253">右側の [インスペクター] パネルで、 **Spatializer プラグイン** の設定を見つけて、[ **MS HRTF Spatializer**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-253">In the Inspector Panel on the right side, find the **Spatializer Plugin** setting and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="0c35f-254">[プロジェクト] パネルの [ **ホログラム** ] フォルダーから、[ **アンビエント** ] オブジェクトを [階層] パネルの **OrigamiCollection** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-254">From the **Holograms** folder in the Project panel, drag the **Ambience** object onto the **OrigamiCollection** object in the Hierarchy Panel.</span></span>
* <span data-ttu-id="0c35f-255">[ **OrigamiCollection** ] を選択し、[インスペクター] パネルで [ **オーディオソース** ] コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-255">Select **OrigamiCollection** and find the **Audio Source** component in the Inspector panel.</span></span> <span data-ttu-id="0c35f-256">次のプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-256">Change these properties:</span></span>
  * <span data-ttu-id="0c35f-257">**Spatialize** プロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-257">Check the **Spatialize** property.</span></span>
  * <span data-ttu-id="0c35f-258">スリープ状態 **になって** いることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-258">Check the **Play On Awake**.</span></span>
  * <span data-ttu-id="0c35f-259">スライダーを右にドラッグして、 **空間 Blend** を **3d** に変更します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-259">Change **Spatial Blend** to **3D** by dragging the slider all the way to the right.</span></span> <span data-ttu-id="0c35f-260">スライダーを移動すると、値は0から1に変更されます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-260">The value should change from 0 to 1 when you move the slider.</span></span>
  * <span data-ttu-id="0c35f-261">**Loop** プロパティを確認します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-261">Check the **Loop** property.</span></span>
  * <span data-ttu-id="0c35f-262">[ **3D サウンド設定**] を展開し、**ドップラーレベル** に「 **0.1** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-262">Expand **3D Sound Settings**, and enter **0.1** for **Doppler Level**.</span></span>
  * <span data-ttu-id="0c35f-263">**ボリュームのロール** アウトを **対数ロールオフ** に設定します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-263">Set **Volume Rolloff** to **Logarithmic Rolloff**.</span></span>
  * <span data-ttu-id="0c35f-264">**最大距離** を **20** に設定します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-264">Set **Max Distance** to **20**.</span></span>
* <span data-ttu-id="0c35f-265">**Scripts** フォルダーで、 **SphereSounds** という名前のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-265">In the **Scripts** folder, create a script named **SphereSounds**.</span></span>
* <span data-ttu-id="0c35f-266">**SphereSounds** を、階層内の **Sphere1** オブジェクトと **Sphere2** オブジェクトにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-266">Drag and drop **SphereSounds** to the **Sphere1** and **Sphere2** objects in the Hierarchy.</span></span>
* <span data-ttu-id="0c35f-267">Visual Studio で **SphereSounds** を開き、次のコードを更新して **すべてを保存** します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-267">Open **SphereSounds** in Visual Studio, update the following code and **Save All**.</span></span>

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

* <span data-ttu-id="0c35f-268">スクリプトを保存し、Unity に戻ります。</span><span class="sxs-lookup"><span data-stu-id="0c35f-268">Save the script, and return to Unity.</span></span>
* <span data-ttu-id="0c35f-269">アプリのエクスポート、ビルド、および HoloLens へのデプロイを行います。</span><span class="sxs-lookup"><span data-stu-id="0c35f-269">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0c35f-270">ステージからさらに近い場所に移動し、サウンドが変化するのを左右に並べて表示します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-270">Move closer and further from the Stage and turn side-to-side to hear the sounds change.</span></span>

## <a name="chapter-6---spatial-mapping"></a><span data-ttu-id="0c35f-271">Chapter 6-空間マッピング</span><span class="sxs-lookup"><span data-stu-id="0c35f-271">Chapter 6 - Spatial mapping</span></span>

>[!VIDEO https://www.youtube.com/embed/Pkt1_wNLLXY]

<span data-ttu-id="0c35f-272">ここでは、 [空間マッピング](../../../design/spatial-mapping.md) を使用して、ゲームボードを現実世界の実際のオブジェクトに配置します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-272">Now we are going to use [spatial mapping](../../../design/spatial-mapping.md) to place the game board on a real object in the real world.</span></span>

### <a name="objectives"></a><span data-ttu-id="0c35f-273">目標</span><span class="sxs-lookup"><span data-stu-id="0c35f-273">Objectives</span></span>

* <span data-ttu-id="0c35f-274">実際の世界を仮想環境に移します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-274">Bring your real world into the virtual world.</span></span>
* <span data-ttu-id="0c35f-275">自分にとって最も重要な場所にホログラムを配置します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-275">Place your holograms where they matter most to you.</span></span>

### <a name="instructions"></a><span data-ttu-id="0c35f-276">手順</span><span class="sxs-lookup"><span data-stu-id="0c35f-276">Instructions</span></span>

* <span data-ttu-id="0c35f-277">Unity で、[プロジェクト] パネルの [ **ホログラム** ] フォルダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-277">In Unity, click on the **Holograms** folder in the Project panel.</span></span>
* <span data-ttu-id="0c35f-278">**空間マッピング** 資産を **階層** のルートにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-278">Drag the **Spatial Mapping** asset into the root of the **Hierarchy**.</span></span>
* <span data-ttu-id="0c35f-279">階層内の **空間マッピング** オブジェクトをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-279">Click on the **Spatial Mapping** object in the Hierarchy.</span></span>
* <span data-ttu-id="0c35f-280">[ **インスペクター] パネル** で、次のプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-280">In the **Inspector panel**, change the following properties:</span></span>
  * <span data-ttu-id="0c35f-281">[ **ビジュアルメッシュの描画** ] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-281">Check the **Draw Visual Meshes** box.</span></span>
  * <span data-ttu-id="0c35f-282">[ **素材の描画** ] を見つけ、右側にある円をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-282">Locate **Draw Material** and click the circle on the right.</span></span> <span data-ttu-id="0c35f-283">上部にある検索フィールドに「**ワイヤーフレーム**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-283">Type "**wireframe**" into the search field at the top.</span></span> <span data-ttu-id="0c35f-284">結果をクリックし、ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-284">Click on the result and then close the window.</span></span> <span data-ttu-id="0c35f-285">これを行うと、描画マテリアルの値はワイヤーフレームに設定されます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-285">When you do this, the value for Draw Material should get set to Wireframe.</span></span>
* <span data-ttu-id="0c35f-286">アプリのエクスポート、ビルド、および HoloLens へのデプロイを行います。</span><span class="sxs-lookup"><span data-stu-id="0c35f-286">Export, build and deploy the app to your HoloLens.</span></span>
* <span data-ttu-id="0c35f-287">アプリを実行すると、ワイヤーフレームメッシュが実際の世界にオーバーレイされます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-287">When the app runs, a wireframe mesh will overlay your real world.</span></span>
* <span data-ttu-id="0c35f-288">ローリング球がステージとフロアにどのように分かれているかを見てください。</span><span class="sxs-lookup"><span data-stu-id="0c35f-288">Watch how a rolling sphere will fall off the stage, and onto the floor!</span></span>

<span data-ttu-id="0c35f-289">ここでは、OrigamiCollection を新しい場所に移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-289">Now we'll show you how to move the OrigamiCollection to a new location:</span></span>

* <span data-ttu-id="0c35f-290">**Scripts** フォルダーで、 **TapToPlaceParent** という名前のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-290">In the **Scripts** folder, create a script named **TapToPlaceParent**.</span></span>
* <span data-ttu-id="0c35f-291">**階層** で、 **OrigamiCollection** を展開し、[**ステージ**] オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-291">In the **Hierarchy**, expand the **OrigamiCollection** and select the **Stage** object.</span></span>
* <span data-ttu-id="0c35f-292">**TapToPlaceParent** スクリプトを Stage オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-292">Drag the **TapToPlaceParent** script onto the Stage object.</span></span>
* <span data-ttu-id="0c35f-293">Visual Studio で **TapToPlaceParent** スクリプトを開き、次のように更新します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-293">Open the **TapToPlaceParent** script in Visual Studio, and update it to be the following:</span></span>

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

* <span data-ttu-id="0c35f-294">アプリをエクスポート、ビルド、デプロイします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-294">Export, build and deploy the app.</span></span>
* <span data-ttu-id="0c35f-295">これで、[選択] ジェスチャを使用して新しい場所に移動し、もう一度 Select ジェスチャを使用して、ゲームを特定の場所に配置できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="0c35f-295">Now you should now be able to place the game in a specific location by gazing at it, using the Select gesture and then moving to a new location, and using the Select gesture again.</span></span>

## <a name="chapter-7---holographic-fun"></a><span data-ttu-id="0c35f-296">第7章-Holographic 楽しい</span><span class="sxs-lookup"><span data-stu-id="0c35f-296">Chapter 7 - Holographic fun</span></span>

### <a name="objectives"></a><span data-ttu-id="0c35f-297">目標</span><span class="sxs-lookup"><span data-stu-id="0c35f-297">Objectives</span></span>

* <span data-ttu-id="0c35f-298">Holographic 黄泉の入口を公開します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-298">Reveal the entrance to a holographic underworld.</span></span>

### <a name="instructions"></a><span data-ttu-id="0c35f-299">手順</span><span class="sxs-lookup"><span data-stu-id="0c35f-299">Instructions</span></span>

<span data-ttu-id="0c35f-300">次に、holographic 黄泉を発見する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-300">Now we'll show you how to uncover the holographic underworld:</span></span>

* <span data-ttu-id="0c35f-301">[プロジェクト] パネルの [ **ホログラム** ] フォルダーから次のようにします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-301">From the **Holograms** folder in the Project Panel:</span></span>
  * <span data-ttu-id="0c35f-302">**OrigamiCollection** の子になるように、階層に **黄泉** をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-302">Drag **Underworld** into the Hierarchy to be a child of **OrigamiCollection**.</span></span>
* <span data-ttu-id="0c35f-303">**Scripts** フォルダーで、**ヒットターゲット** という名前のスクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-303">In the **Scripts** folder, create a script named **HitTarget**.</span></span>
* <span data-ttu-id="0c35f-304">**階層** で、 **OrigamiCollection** を展開します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-304">In the **Hierarchy**, expand the **OrigamiCollection**.</span></span>
* <span data-ttu-id="0c35f-305">**ステージ** オブジェクトを展開し、**ターゲット** オブジェクト (青いファン) を選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-305">Expand the **Stage** object and select the **Target** object (blue fan).</span></span>
* <span data-ttu-id="0c35f-306">**ヒットターゲット** スクリプトを **ターゲット** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-306">Drag the **HitTarget** script onto the **Target** object.</span></span>
* <span data-ttu-id="0c35f-307">Visual Studio で **ヒットするターゲット** スクリプトを開き、次のように更新します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-307">Open the **HitTarget** script in Visual Studio, and update it to be the following:</span></span>

```cs
using UnityEngine;

public class HitTarget : MonoBehaviour
{
    // These public fields become settable properties in the Unity editor.
    public GameObject underworld;
    public GameObject objectToHide;

    // Occurs when this object starts colliding with another object
    void OnCollisionEnter(Collision collision)
    {
        // Hide the stage and show the underworld.
        objectToHide.SetActive(false);
        underworld.SetActive(true);

        // Disable Spatial Mapping to let the spheres enter the underworld.
        SpatialMapping.Instance.MappingEnabled = false;
    }
}
```

* <span data-ttu-id="0c35f-308">Unity で、 **ターゲット** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-308">In Unity, select the **Target** object.</span></span>
* <span data-ttu-id="0c35f-309">**ヒットターゲット** コンポーネントには、2つのパブリックプロパティが表示されるようになりました。シーン内のオブジェクトを参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c35f-309">Two public properties are now visible on the **Hit Target** component and need to reference objects in our scene:</span></span>
  * <span data-ttu-id="0c35f-310">[**階層**] パネルから、**ヒットターゲット** コンポーネントの "**黄泉**" プロパティに [**黄泉**] をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-310">Drag **Underworld** from the **Hierarchy** panel to the **Underworld** property on the **Hit Target** component.</span></span>
  * <span data-ttu-id="0c35f-311">[**階層**] パネルから [**ステージ**] をオブジェクトにドラッグして、**ヒットターゲット** コンポーネントのプロパティを **非表示に** します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-311">Drag **Stage** from the **Hierarchy** panel to the **Object to Hide** property on the **Hit Target** component.</span></span>
* <span data-ttu-id="0c35f-312">アプリをエクスポート、ビルド、デプロイします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-312">Export, build and deploy the app.</span></span>
* <span data-ttu-id="0c35f-313">Origami コレクションを床に配置し、Select ジェスチャを使用して球をドロップします。</span><span class="sxs-lookup"><span data-stu-id="0c35f-313">Place the Origami Collection on the floor, and then use the Select gesture to make a sphere drop.</span></span>
* <span data-ttu-id="0c35f-314">球がターゲット (青いファン) にヒットすると、爆発が発生します。</span><span class="sxs-lookup"><span data-stu-id="0c35f-314">When the sphere hits the target (blue fan), an explosion will occur.</span></span> <span data-ttu-id="0c35f-315">コレクションが非表示になり、黄泉の抜け穴が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0c35f-315">The collection will be hidden and a hole to the underworld will appear.</span></span>

## <a name="the-end"></a><span data-ttu-id="0c35f-316">最後です</span><span class="sxs-lookup"><span data-stu-id="0c35f-316">The end</span></span>

<span data-ttu-id="0c35f-317">これがこのチュートリアルの終わりです。</span><span class="sxs-lookup"><span data-stu-id="0c35f-317">And that's the end of this tutorial!</span></span>

<span data-ttu-id="0c35f-318">学習した内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0c35f-318">You learned:</span></span>

* <span data-ttu-id="0c35f-319">Unity で holographic アプリを作成する方法。</span><span class="sxs-lookup"><span data-stu-id="0c35f-319">How to create a holographic app in Unity.</span></span>
* <span data-ttu-id="0c35f-320">見つめ、ジェスチャ、音声、サウンド、および空間マッピングを使用する方法。</span><span class="sxs-lookup"><span data-stu-id="0c35f-320">How to make use of gaze, gesture, voice, sound, and spatial mapping.</span></span>
* <span data-ttu-id="0c35f-321">Visual Studio を使用してアプリをビルドしてデプロイする方法。</span><span class="sxs-lookup"><span data-stu-id="0c35f-321">How to build and deploy an app using Visual Studio.</span></span>

<span data-ttu-id="0c35f-322">これで、独自の holographic エクスペリエンスの作成を開始する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="0c35f-322">You are now ready to start creating your own holographic experience!</span></span>

## <a name="see-also"></a><span data-ttu-id="0c35f-323">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c35f-323">See also</span></span>

* [<span data-ttu-id="0c35f-324">MR の基本 101E:エミュレーターを使用した完全なプロジェクト</span><span class="sxs-lookup"><span data-stu-id="0c35f-324">MR Basics 101E: Complete project with emulator</span></span>](holograms-101e.md)
* [<span data-ttu-id="0c35f-325">視線入力</span><span class="sxs-lookup"><span data-stu-id="0c35f-325">Gaze</span></span>](../../../design/gaze-and-commit.md)
* [<span data-ttu-id="0c35f-326">頭の視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="0c35f-326">Head-gaze and commit</span></span>](../../../design/gaze-and-commit.md)
* [<span data-ttu-id="0c35f-327">音声入力</span><span class="sxs-lookup"><span data-stu-id="0c35f-327">Voice input</span></span>](../../../design/voice-input.md)
* [<span data-ttu-id="0c35f-328">立体音響</span><span class="sxs-lookup"><span data-stu-id="0c35f-328">Spatial sound</span></span>](../../../design/spatial-sound.md)
* [<span data-ttu-id="0c35f-329">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="0c35f-329">Spatial mapping</span></span>](../../../design/spatial-mapping.md)
