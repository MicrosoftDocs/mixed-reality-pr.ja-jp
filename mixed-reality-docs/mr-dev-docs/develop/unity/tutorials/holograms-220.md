---
title: MR 空間 220 - 立体音響
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、空間サウンドの概念の詳細を確認してください。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、academy、チュートリアル、空間サウンド、HoloLens、Mixed Reality Academy、unity、mixed reality ヘッドセット、windows Mixed reality ヘッドセット、virtual Reality ヘッドセット、Windows 10
ms.openlocfilehash: 043443c0c197e3b606c4845966e0cf60102d0b85
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678371"
---
# <a name="mr-spatial-220-spatial-sound"></a><span data-ttu-id="9b364-104">MR 空間 220:立体音響</span><span class="sxs-lookup"><span data-stu-id="9b364-104">MR Spatial 220: Spatial sound</span></span>

>[!NOTE]
><span data-ttu-id="9b364-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="9b364-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="9b364-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="9b364-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="9b364-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。</span><span class="sxs-lookup"><span data-stu-id="9b364-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="9b364-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="9b364-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="9b364-109">HoloLens 2 向けには、[新しいチュートリアル シリーズ](../../../mr-learning-base-01.md)が投稿されています。</span><span class="sxs-lookup"><span data-stu-id="9b364-109">[A new series of tutorials](../../../mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="9b364-110">[空間サウンド](../../../design/spatial-sound.md) はホログラムに breathes し、世界中に存在します。</span><span class="sxs-lookup"><span data-stu-id="9b364-110">[Spatial sound](../../../design/spatial-sound.md) breathes life into holograms and gives them presence in our world.</span></span> <span data-ttu-id="9b364-111">ホログラムは、ライトとサウンドの両方で構成されています。ホログラムが見えなくなった場合は、空間サウンドを使用して見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="9b364-111">Holograms are composed of both light and sound, and if you happen to lose sight of your holograms, spatial sound can help you find them.</span></span> <span data-ttu-id="9b364-112">空間サウンドは、無線で聞くことができる一般的なサウンドとは異なり、3D 空間に配置されています。</span><span class="sxs-lookup"><span data-stu-id="9b364-112">Spatial sound is not like the typical sound that you would hear on the radio, it is sound that is positioned in 3D space.</span></span> <span data-ttu-id="9b364-113">空間サウンドを使用すると、ユーザーの背後、または自分の頭にいるかのように、ホログラムを鳴らすことができます。</span><span class="sxs-lookup"><span data-stu-id="9b364-113">With spatial sound, you can make holograms sound like they're behind you, next to you, or even on your head!</span></span> <span data-ttu-id="9b364-114">このコースでは、次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="9b364-114">In this course, you will:</span></span>

* <span data-ttu-id="9b364-115">Microsoft の空間サウンドを使用するように開発環境を構成します。</span><span class="sxs-lookup"><span data-stu-id="9b364-115">Configure your development environment to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="9b364-116">相互作用を強化するには、空間サウンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b364-116">Use Spatial Sound to enhance interactions.</span></span>
* <span data-ttu-id="9b364-117">空間の [マッピング](../../../design/spatial-mapping.md)と共に空間サウンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="9b364-117">Use Spatial Sound in conjunction with [Spatial Mapping](../../../design/spatial-mapping.md).</span></span>
* <span data-ttu-id="9b364-118">サウンドのデザインとベストプラクティスの混在を理解します。</span><span class="sxs-lookup"><span data-stu-id="9b364-118">Understand sound design and mixing best practices.</span></span>
* <span data-ttu-id="9b364-119">音を使用して特殊効果を向上させ、ユーザーを混合現実の世界に持ち込むことができます。</span><span class="sxs-lookup"><span data-stu-id="9b364-119">Use sound to enhance special effects and bring the user into the Mixed Reality world.</span></span>

## <a name="device-support"></a><span data-ttu-id="9b364-120">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="9b364-120">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="9b364-121">コース</span><span class="sxs-lookup"><span data-stu-id="9b364-121">Course</span></span></th><th style="width:150px"> <span data-ttu-id="9b364-122"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="9b364-122"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="9b364-123"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="9b364-123"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="9b364-124">MR 空間 220:立体音響</span><span class="sxs-lookup"><span data-stu-id="9b364-124">MR Spatial 220: Spatial sound</span></span></td><td style="text-align: center;"> <span data-ttu-id="9b364-125">✔️</span><span class="sxs-lookup"><span data-stu-id="9b364-125">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="9b364-126">✔️</span><span class="sxs-lookup"><span data-stu-id="9b364-126">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="9b364-127">開始する前に</span><span class="sxs-lookup"><span data-stu-id="9b364-127">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="9b364-128">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="9b364-128">Prerequisites</span></span>

* <span data-ttu-id="9b364-129">適切な [ツールがインストール](../../../develop/install-the-tools.md)された WINDOWS 10 PC。</span><span class="sxs-lookup"><span data-stu-id="9b364-129">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="9b364-130">基本的な C# プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="9b364-130">Some basic C# programming ability.</span></span>
* <span data-ttu-id="9b364-131">[MR の基本 101](../../../develop/unity/tutorials/holograms-101.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-131">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="9b364-132">[開発用に構成され](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)た HoloLens デバイス。</span><span class="sxs-lookup"><span data-stu-id="9b364-132">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="9b364-133">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="9b364-133">Project files</span></span>

* <span data-ttu-id="9b364-134">プロジェクトに必要な [ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9b364-134">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-220-SpatialSound.zip) required by the project.</span></span> <span data-ttu-id="9b364-135">Unity 2017.2 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="9b364-135">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="9b364-136">引き続き Unity 5.6 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="9b364-136">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-220.zip).</span></span> <span data-ttu-id="9b364-137">このリリースは最新ではなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-137">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="9b364-138">引き続き Unity 5.5 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="9b364-138">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-220.zip).</span></span> <span data-ttu-id="9b364-139">このリリースは最新ではなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-139">This release may no longer be up-to-date.</span></span>
  * <span data-ttu-id="9b364-140">引き続き Unity 5.4 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="9b364-140">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-220.zip).</span></span> <span data-ttu-id="9b364-141">このリリースは最新ではなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-141">This release may no longer be up-to-date.</span></span>
* <span data-ttu-id="9b364-142">ファイルをデスクトップまたはその他の簡単な場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="9b364-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="9b364-143">ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound)ます。</span><span class="sxs-lookup"><span data-stu-id="9b364-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-220-SpatialSound).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="9b364-144">エラッタとメモ</span><span class="sxs-lookup"><span data-stu-id="9b364-144">Errata and Notes</span></span>

* <span data-ttu-id="9b364-145">コード内のブレークポイントにヒットするには、Visual Studio の [ツール]->オプション->デバッグ] の下にある [マイコードのみを有効にする] を無効 (*オフ*) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-145">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="9b364-146">章 1-Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="9b364-146">Chapter 1 - Unity Setup</span></span>

### <a name="objectives"></a><span data-ttu-id="9b364-147">目標</span><span class="sxs-lookup"><span data-stu-id="9b364-147">Objectives</span></span>

* <span data-ttu-id="9b364-148">Microsoft の空間サウンドを使用するように Unity のサウンド構成を変更します。</span><span class="sxs-lookup"><span data-stu-id="9b364-148">Change Unity's sound configuration to use Microsoft Spatial Sound.</span></span>
* <span data-ttu-id="9b364-149">Unity のオブジェクトに3D サウンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="9b364-149">Add 3D sound to an object in Unity.</span></span>

### <a name="instructions"></a><span data-ttu-id="9b364-150">手順</span><span class="sxs-lookup"><span data-stu-id="9b364-150">Instructions</span></span>

* <span data-ttu-id="9b364-151">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="9b364-151">Start Unity.</span></span>
* <span data-ttu-id="9b364-152">**[Open (開く)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-152">Select **Open**.</span></span>
* <span data-ttu-id="9b364-153">デスクトップに移動し、以前にアーカイブしていないフォルダーを見つけます。</span><span class="sxs-lookup"><span data-stu-id="9b364-153">Navigate to your Desktop and find the folder you previously un-archived.</span></span>
* <span data-ttu-id="9b364-154">**Starting\Decibel** フォルダーをクリックし、[フォルダーの **選択**] ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="9b364-154">Click on the **Starting\Decibel** folder and then press the **Select Folder** button.</span></span>
* <span data-ttu-id="9b364-155">Unity にプロジェクトが読み込まれるのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="9b364-155">Wait for the project to load in Unity.</span></span>
* <span data-ttu-id="9b364-156">[ **プロジェクト** ] パネルで、[ **Scenes\Decibel.unity**] を開きます。</span><span class="sxs-lookup"><span data-stu-id="9b364-156">In the **Project** panel, open **Scenes\Decibel.unity**.</span></span>
* <span data-ttu-id="9b364-157">[ **階層** ] パネルで、[ **HologramCollection** ] を展開し、[ **P0LY**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-157">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="9b364-158">インスペクターで、[ **Audiosource** ] を展開し、[ **Spatialize** ] チェックボックスが表示されないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="9b364-158">In the Inspector, expand **AudioSource** and notice that there is no **Spatialize** check box.</span></span>

<span data-ttu-id="9b364-159">既定では、Unity は spatializer プラグインを読み込みません。</span><span class="sxs-lookup"><span data-stu-id="9b364-159">By default, Unity does not load a spatializer plugin.</span></span> <span data-ttu-id="9b364-160">次の手順を実行すると、プロジェクトの空間サウンドが有効になります。</span><span class="sxs-lookup"><span data-stu-id="9b364-160">The following steps will enable Spatial Sound in the project.</span></span>

* <span data-ttu-id="9b364-161">Unity のトップメニューで、[ **Edit > Project Settings > Audio**] を開きます。</span><span class="sxs-lookup"><span data-stu-id="9b364-161">In Unity's top menu, go to **Edit > Project Settings > Audio**.</span></span>
* <span data-ttu-id="9b364-162">**Spatializer プラグイン** のドロップダウンを見つけて、[ **MS HRTF Spatializer**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-162">Find the **Spatializer Plugin** dropdown, and select **MS HRTF Spatializer**.</span></span>
* <span data-ttu-id="9b364-163">[ **階層** ] パネルで、[ **HologramCollection > P0LY**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-163">In the **Hierarchy** panel, select **HologramCollection > P0LY**.</span></span>
* <span data-ttu-id="9b364-164">[ **インスペクター** ] パネルで、[ **オーディオソース** ] コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="9b364-164">In the **Inspector** panel, find the **Audio Source** component.</span></span>
* <span data-ttu-id="9b364-165">**Spatialize** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="9b364-165">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="9b364-166">[ **空間 Blend** ] スライダーを **3d** にドラッグするか、編集ボックスに「 **1** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9b364-166">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>

<span data-ttu-id="9b364-167">ここでは、Unity でプロジェクトをビルドし、Visual Studio でソリューションを構成します。</span><span class="sxs-lookup"><span data-stu-id="9b364-167">We will now build the project in Unity and configure the solution in Visual Studio.</span></span>

1. <span data-ttu-id="9b364-168">Unity で、[ **ファイル > ビルド設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-168">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="9b364-169">シーンを追加するには、[開いている **シーンの追加** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b364-169">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="9b364-170">[**プラットフォーム**] ボックスの一覧の [**ユニバーサル Windows プラットフォーム**] を選択し、[**プラットフォームの切り替え**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b364-170">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
4. <span data-ttu-id="9b364-171">HoloLens 向けに特に開発している場合は、 **ターゲットデバイス** を **hololens** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-171">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="9b364-172">それ以外の場合は、 **任意のデバイス** に残しておきます。</span><span class="sxs-lookup"><span data-stu-id="9b364-172">Otherwise, leave it on **Any device**.</span></span>
5. <span data-ttu-id="9b364-173">**ビルドの種類** が [ **D3D** ] に設定され、[ **sdk** ] が [**最新のインストール済み**] に設定されていることを確認します (sdk 16299 以降である必要があります)。</span><span class="sxs-lookup"><span data-stu-id="9b364-173">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="9b364-174">[**ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b364-174">Click **Build**.</span></span>
7. <span data-ttu-id="9b364-175">"App" という名前の **新しいフォルダー** を作成します。</span><span class="sxs-lookup"><span data-stu-id="9b364-175">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="9b364-176">**アプリ** フォルダーをシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b364-176">Single click the **App** folder.</span></span>
9. <span data-ttu-id="9b364-177">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b364-177">Press **Select Folder**.</span></span>

<span data-ttu-id="9b364-178">Unity が完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b364-178">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="9b364-179">**アプリ** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="9b364-179">Open the **App** folder.</span></span>
2. <span data-ttu-id="9b364-180">**デシベル Visual Studio ソリューション** を開きます。</span><span class="sxs-lookup"><span data-stu-id="9b364-180">Open the **Decibel Visual Studio Solution**.</span></span>

<span data-ttu-id="9b364-181">HoloLens に展開する場合:</span><span class="sxs-lookup"><span data-stu-id="9b364-181">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="9b364-182">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に変更し、ARM から **x86** に変更します。</span><span class="sxs-lookup"><span data-stu-id="9b364-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="9b364-183">[ローカルコンピューター] ボタンの横にあるドロップダウン矢印をクリックし、[ **リモートコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-183">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="9b364-184">**HoloLens デバイスの IP アドレス** を入力し、[認証モード] を [**ユニバーサル (暗号化** されていないプロトコル)] に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-184">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="9b364-185">**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b364-185">Click **Select**.</span></span> <span data-ttu-id="9b364-186">デバイスの IP アドレスがわからない場合は、[ **設定] [Network & Internet > 詳細オプション >** 確認してください。</span><span class="sxs-lookup"><span data-stu-id="9b364-186">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="9b364-187">上部のメニューバーで、[デバッグ]、[ **デバッグなしで開始** ] の順にクリック >、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="9b364-187">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="9b364-188">初めてデバイスをデプロイする場合は、 [Visual Studio とペアリング](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-188">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>

<span data-ttu-id="9b364-189">イマーシブヘッドセットに展開する場合:</span><span class="sxs-lookup"><span data-stu-id="9b364-189">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="9b364-190">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に、ARM から **x64** に変更します。</span><span class="sxs-lookup"><span data-stu-id="9b364-190">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="9b364-191">配置ターゲットが **ローカルコンピューター** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9b364-191">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="9b364-192">上部のメニューバーで、[デバッグ]、[ **デバッグなしで開始** ] の順にクリック >、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="9b364-192">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>

## <a name="chapter-2---spatial-sound-and-interaction"></a><span data-ttu-id="9b364-193">第2章: 空間サウンドと相互作用</span><span class="sxs-lookup"><span data-stu-id="9b364-193">Chapter 2 - Spatial Sound and Interaction</span></span>

### <a name="objectives"></a><span data-ttu-id="9b364-194">目標</span><span class="sxs-lookup"><span data-stu-id="9b364-194">Objectives</span></span>

* <span data-ttu-id="9b364-195">サウンドを使用して、ホログラムのリアリティを高めます。</span><span class="sxs-lookup"><span data-stu-id="9b364-195">Enhance hologram realism using sound.</span></span>
* <span data-ttu-id="9b364-196">サウンドを使用して、ユーザーの宝石を誘導します。</span><span class="sxs-lookup"><span data-stu-id="9b364-196">Direct the user's gaze using sound.</span></span>
* <span data-ttu-id="9b364-197">サウンドを使用してジェスチャに関するフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="9b364-197">Provide gesture feedback using sound.</span></span>

### <a name="part-1---enhancing-realism"></a><span data-ttu-id="9b364-198">パート 1-リアリティの向上</span><span class="sxs-lookup"><span data-stu-id="9b364-198">Part 1 - Enhancing Realism</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9b364-199">主要概念</span><span class="sxs-lookup"><span data-stu-id="9b364-199">Key Concepts</span></span>

* <span data-ttu-id="9b364-200">Spatialize ホログラムサウンド。</span><span class="sxs-lookup"><span data-stu-id="9b364-200">Spatialize hologram sounds.</span></span>
* <span data-ttu-id="9b364-201">サウンドソースは、ホログラムの適切な場所に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-201">Sound sources should be placed at an appropriate location on the hologram.</span></span>

<span data-ttu-id="9b364-202">サウンドの適切な場所は、ホログラムに依存します。</span><span class="sxs-lookup"><span data-stu-id="9b364-202">The appropriate location for the sound is going to depend on the hologram.</span></span> <span data-ttu-id="9b364-203">たとえば、ホログラムが人間の場合、サウンドソースは、脚ではなく口の近くに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-203">For example, if the hologram is of a human, the sound source should be located near the mouth and not the feet.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9b364-204">手順</span><span class="sxs-lookup"><span data-stu-id="9b364-204">Instructions</span></span>

<span data-ttu-id="9b364-205">次の手順では、spatialized サウンドをホログラムにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="9b364-205">The following instructions will attach a spatialized sound to a hologram.</span></span>

* <span data-ttu-id="9b364-206">[ **階層** ] パネルで、[ **HologramCollection** ] を展開し、[ **P0LY**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-206">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="9b364-207">[ **インスペクター** ] パネルの [ **audiosource**] で、[ **audiosource** ] の横にある円をクリックし、ポップアップから [ **PolyHover** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-207">In the **Inspector** panel, in the **AudioSource**, click the circle next to **AudioClip** and select **PolyHover** from the pop-up.</span></span>
* <span data-ttu-id="9b364-208">[ **出力** ] の横にある円をクリックし、ポップアップから [ **SoundEffects** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-208">Click the circle next to **Output** and select **SoundEffects** from the pop-up.</span></span>

<span data-ttu-id="9b364-209">プロジェクトのデシベルは、Unity **Audiomixer** コンポーネントを使用して、サウンドグループのサウンドレベルを調整できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9b364-209">Project Decibel uses a Unity **AudioMixer** component to enable adjusting sound levels for groups of sounds.</span></span> <span data-ttu-id="9b364-210">この方法でサウンドをグループ化することで、各サウンドの相対的なボリュームを維持しながら、全体的なボリュームを調整できます。</span><span class="sxs-lookup"><span data-stu-id="9b364-210">By grouping sounds this way, the overall volume can be adjusted while maintaining the relative volume of each sound.</span></span>

* <span data-ttu-id="9b364-211">**Audiosource** で、[ **3d サウンド設定**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b364-211">In the **AudioSource**, expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="9b364-212">**ドップラーレベル** を **0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-212">Set **Doppler Level** to **0**.</span></span>

<span data-ttu-id="9b364-213">ドップラーレベルを0に設定すると、モーション (ホログラムまたはユーザーのいずれか) によるピッチの変更が無効になります。</span><span class="sxs-lookup"><span data-stu-id="9b364-213">Setting Doppler level to zero disables changes in pitch caused by motion (either of the hologram or the user).</span></span> <span data-ttu-id="9b364-214">ドップラーの典型的な例は、高速移動車です。</span><span class="sxs-lookup"><span data-stu-id="9b364-214">A classic example of Doppler is a fast-moving car.</span></span> <span data-ttu-id="9b364-215">車が静止リスナーに近づくにつれて、エンジンのピッチは上がります。</span><span class="sxs-lookup"><span data-stu-id="9b364-215">As the car approaches a stationary listener, the pitch of the engine rises.</span></span> <span data-ttu-id="9b364-216">リスナーがリスナーに渡されると、距離によってピッチが低下します。</span><span class="sxs-lookup"><span data-stu-id="9b364-216">When it passes the listener, the pitch lowers with distance.</span></span>

### <a name="part-2---directing-the-users-gaze"></a><span data-ttu-id="9b364-217">パート 2-ユーザーの宝石を誘導する</span><span class="sxs-lookup"><span data-stu-id="9b364-217">Part 2 - Directing the User's Gaze</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9b364-218">主要概念</span><span class="sxs-lookup"><span data-stu-id="9b364-218">Key Concepts</span></span>

* <span data-ttu-id="9b364-219">サウンドを使用して、重要なホログラムに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9b364-219">Use sound to call attention to important holograms.</span></span>
* <span data-ttu-id="9b364-220">耳は、目が見える場所に直接役立ちます。</span><span class="sxs-lookup"><span data-stu-id="9b364-220">The ears help direct where the eyes should look.</span></span>
* <span data-ttu-id="9b364-221">脳には、期待されることがあります。</span><span class="sxs-lookup"><span data-stu-id="9b364-221">The brain has some learned expectations.</span></span>

<span data-ttu-id="9b364-222">1つの例として、鳥は一般に人間の頭を超えています。</span><span class="sxs-lookup"><span data-stu-id="9b364-222">One example of learned expectations is that birds are generally above the heads of humans.</span></span> <span data-ttu-id="9b364-223">ユーザーが鳥のサウンドを聞くと、最初の反応が検索されます。</span><span class="sxs-lookup"><span data-stu-id="9b364-223">If a user hears a bird sound, their initial reaction is to look up.</span></span> <span data-ttu-id="9b364-224">ユーザーの下に鳥を配置すると、それらのユーザーが正しい方向のサウンドを使用することになりますが、検索が必要になると予想されるホログラムを見つけることができません。</span><span class="sxs-lookup"><span data-stu-id="9b364-224">Placing a bird below the user can lead to them facing the correct direction of the sound, but being unable to find the hologram based on the expectation of needing to look up.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9b364-225">手順</span><span class="sxs-lookup"><span data-stu-id="9b364-225">Instructions</span></span>

<span data-ttu-id="9b364-226">次の手順を実行すると、P0LY を使用して、ホログラムを見つけることができるようになります。</span><span class="sxs-lookup"><span data-stu-id="9b364-226">The following instructions enable P0LY to hide behind you, so that you can use sound to locate the hologram.</span></span>

* <span data-ttu-id="9b364-227">[ **階層** ] パネルで、[ **マネージャー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-227">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="9b364-228">[ **インスペクター** ] パネルで、[ **音声入力ハンドラー**] を見つけます。</span><span class="sxs-lookup"><span data-stu-id="9b364-228">In the **Inspector** panel, find **Speech Input Handler**.</span></span>
* <span data-ttu-id="9b364-229">**音声入力ハンドラー** で、 **[表示** しない] を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b364-229">In **Speech Input Handler**, expand **Go Hide**.</span></span>
* <span data-ttu-id="9b364-230">**関数** を **PolyActions** に変更します。</span><span class="sxs-lookup"><span data-stu-id="9b364-230">Change **No Function** to **PolyActions.GoHide**.</span></span>

![キーワード: [非表示にする]](images/gohide.png)

### <a name="part-3---gesture-feedback"></a><span data-ttu-id="9b364-232">パート 3-ジェスチャに関するフィードバック</span><span class="sxs-lookup"><span data-stu-id="9b364-232">Part 3 - Gesture Feedback</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9b364-233">主要概念</span><span class="sxs-lookup"><span data-stu-id="9b364-233">Key Concepts</span></span>

* <span data-ttu-id="9b364-234">サウンドを使用してユーザーに正のジェスチャ確認を提供する</span><span class="sxs-lookup"><span data-stu-id="9b364-234">Provide the user with positive gesture confirmation using sound</span></span>
* <span data-ttu-id="9b364-235">ユーザーに大きな音がかからないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="9b364-235">Do not overwhelm the user - overly loud sounds get in the way</span></span>
* <span data-ttu-id="9b364-236">微妙なサウンドが最適であり、エクスペリエンスを過度に影にしない</span><span class="sxs-lookup"><span data-stu-id="9b364-236">Subtle sounds work best - do not overshadow the experience</span></span>

#### <a name="instructions"></a><span data-ttu-id="9b364-237">手順</span><span class="sxs-lookup"><span data-stu-id="9b364-237">Instructions</span></span>

* <span data-ttu-id="9b364-238">[ **階層** ] パネルで、[ **HologramCollection**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b364-238">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="9b364-239">[ **EnergyHub** ] を展開し、[ **Base**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-239">Expand **EnergyHub** and select **Base**.</span></span>
* <span data-ttu-id="9b364-240">[ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] をクリックし、[ **ジェスチャサウンドハンドラー** の追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b364-240">In the **Inspector** panel, click **Add Component** and add **Gesture Sound Handler**.</span></span>
* <span data-ttu-id="9b364-241">[ **ジェスチャサウンドハンドラー**] で、[ナビゲーションの **開始] クリップ** と **ナビゲーション更新クリップ** の横にある円をクリックし、両方のポップアップから [ **RotateClick** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-241">In **Gesture Sound Handler**, click the circle next to **Navigation Started Clip** and **Navigation Updated Clip** and select **RotateClick** from the pop-up for both.</span></span>
* <span data-ttu-id="9b364-242">Visual Studio に読み込むには、"GestureSoundHandler" をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b364-242">Double click on "GestureSoundHandler" to load in Visual Studio.</span></span>

<span data-ttu-id="9b364-243">ジェスチャサウンドハンドラーは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="9b364-243">Gesture Sound Handler performs the following tasks:</span></span>

* <span data-ttu-id="9b364-244">**Audiosource** を作成および構成します。</span><span class="sxs-lookup"><span data-stu-id="9b364-244">Create and configure an **AudioSource**.</span></span>
* <span data-ttu-id="9b364-245">適切な **オブジェクト** の場所に **audiosource** を配置します。</span><span class="sxs-lookup"><span data-stu-id="9b364-245">Place the **AudioSource** at the location of the appropriate **GameObject**.</span></span>
* <span data-ttu-id="9b364-246">ジェスチャに関連付けられている **Audioclip** を再生します。</span><span class="sxs-lookup"><span data-stu-id="9b364-246">Plays the **AudioClip** associated with the gesture.</span></span>

#### <a name="build-and-deploy"></a><span data-ttu-id="9b364-247">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="9b364-247">Build and Deploy</span></span>

1. <span data-ttu-id="9b364-248">Unity で、[ **ファイル > ビルド設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-248">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="9b364-249">[**ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b364-249">Click **Build**.</span></span>
3. <span data-ttu-id="9b364-250">**アプリ** フォルダーをシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b364-250">Single click the **App** folder.</span></span>
4. <span data-ttu-id="9b364-251">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b364-251">Press **Select Folder**.</span></span>

<span data-ttu-id="9b364-252">ツールバーに "Release"、"x86"、"x64"、および "Remote Device" と表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9b364-252">Check that the Toolbar says "Release", "x86" or "x64", and "Remote Device".</span></span> <span data-ttu-id="9b364-253">それ以外の場合は、Visual Studio のコーディングインスタンスになります。</span><span class="sxs-lookup"><span data-stu-id="9b364-253">If not, this is the coding instance of Visual Studio.</span></span> <span data-ttu-id="9b364-254">場合によっては、アプリフォルダーからソリューションを再度開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-254">You may need to re-open the solution from the App folder.</span></span>

* <span data-ttu-id="9b364-255">メッセージが表示されたら、プロジェクトファイルを再度読み込みます。</span><span class="sxs-lookup"><span data-stu-id="9b364-255">If prompted, reload the project files.</span></span>
* <span data-ttu-id="9b364-256">前と同様に、Visual Studio からデプロイします。</span><span class="sxs-lookup"><span data-stu-id="9b364-256">As before, deploy from Visual Studio.</span></span>

<span data-ttu-id="9b364-257">アプリケーションが展開された後:</span><span class="sxs-lookup"><span data-stu-id="9b364-257">After the application is deployed:</span></span>

* <span data-ttu-id="9b364-258">P0LY の周りを移動すると、サウンドがどのように変化するかを観察します。</span><span class="sxs-lookup"><span data-stu-id="9b364-258">Observe how the sound changes as you move around P0LY.</span></span>
* <span data-ttu-id="9b364-259">*[非表示* にする] を指定すると、P0LY が自分の位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="9b364-259">Say *"Go Hide"* to make P0LY move to a location behind you.</span></span> <span data-ttu-id="9b364-260">サウンドで検索します。</span><span class="sxs-lookup"><span data-stu-id="9b364-260">Find it by the sound.</span></span>
* <span data-ttu-id="9b364-261">エネルギーハブのベースを見つめます。</span><span class="sxs-lookup"><span data-stu-id="9b364-261">Gaze at the base of the Energy Hub.</span></span> <span data-ttu-id="9b364-262">左または右にドラッグしてホログラムを回転させ、クリック音によってジェスチャが確認されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9b364-262">Tap and drag left or right to rotate the hologram and notice how the clicking sound confirms the gesture.</span></span>

<span data-ttu-id="9b364-263">メモ: ユーザーにタグを付けるテキストパネルがあります。</span><span class="sxs-lookup"><span data-stu-id="9b364-263">Note: There is a text panel that will tag-along with you.</span></span> <span data-ttu-id="9b364-264">これには、このコース全体で使用できる音声コマンドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="9b364-264">This will contain the available voice commands that you can use throughout this course.</span></span>

## <a name="chapter-3---spatial-sound-and-spatial-mapping"></a><span data-ttu-id="9b364-265">第3章: 空間サウンドと空間マッピング</span><span class="sxs-lookup"><span data-stu-id="9b364-265">Chapter 3 - Spatial Sound and Spatial Mapping</span></span>

### <a name="objectives"></a><span data-ttu-id="9b364-266">目標</span><span class="sxs-lookup"><span data-stu-id="9b364-266">Objectives</span></span>

* <span data-ttu-id="9b364-267">サウンドを使用して、ホログラムと実際の世界の間の相互作用を確認します。</span><span class="sxs-lookup"><span data-stu-id="9b364-267">Confirm interaction between holograms and the real world using sound.</span></span>
* <span data-ttu-id="9b364-268">Occlude は、物理的な世界を使ってサウンドを再生します。</span><span class="sxs-lookup"><span data-stu-id="9b364-268">Occlude sound using the physical world.</span></span>

### <a name="part-1---physical-world-interaction"></a><span data-ttu-id="9b364-269">パート 1-物理的な世界の相互作用</span><span class="sxs-lookup"><span data-stu-id="9b364-269">Part 1 - Physical World Interaction</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9b364-270">主要概念</span><span class="sxs-lookup"><span data-stu-id="9b364-270">Key Concepts</span></span>

* <span data-ttu-id="9b364-271">通常、物理オブジェクトは、サーフェイスや別のオブジェクトが検出したときに音を鳴らします。</span><span class="sxs-lookup"><span data-stu-id="9b364-271">Physical objects generally make a sound when encountering a surface or another object.</span></span>
* <span data-ttu-id="9b364-272">サウンドは、エクスペリエンスの中で適切なコンテキストである必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-272">Sounds should be context appropriate within the experience.</span></span>

<span data-ttu-id="9b364-273">たとえば、テーブルのカップを設定すると、金属の一部で boulder を落とした場合よりも静かに聞こえます。</span><span class="sxs-lookup"><span data-stu-id="9b364-273">For example, setting a cup on a table should make a quieter sound than dropping a boulder on a piece of metal.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9b364-274">手順</span><span class="sxs-lookup"><span data-stu-id="9b364-274">Instructions</span></span>

* <span data-ttu-id="9b364-275">[ **階層** ] パネルで、[ **HologramCollection**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b364-275">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="9b364-276">[ **EnergyHub**] を展開し、[ **Base**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-276">Expand **EnergyHub**, select **Base**.</span></span>
* <span data-ttu-id="9b364-277">[ **インスペクター** ] パネルで [ **コンポーネントの追加** ] をクリックし、[再生] を追加し **てサウンドとアクションを** 設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-277">In the **Inspector** panel, click **Add Component** and add **Tap To Place With Sound and Action**.</span></span>
* <span data-ttu-id="9b364-278">**サウンドとアクションを使用して配置する場合**:</span><span class="sxs-lookup"><span data-stu-id="9b364-278">In **Tap To Place With Sound and Action**:</span></span>
  * <span data-ttu-id="9b364-279">**タップ時に親を** 確認します。</span><span class="sxs-lookup"><span data-stu-id="9b364-279">Check **Place Parent On Tap**.</span></span>
  * <span data-ttu-id="9b364-280">配置の **サウンド** を **配置** するように設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-280">Set **Placement Sound** to **Place**.</span></span>
  * <span data-ttu-id="9b364-281">**ピックアップ音** を **集配** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-281">Set **Pickup Sound** to **Pickup**.</span></span>
  * <span data-ttu-id="9b364-282">**Pickup アクション** と **配置アクション** の両方の下で、下の方の [+] を押します。</span><span class="sxs-lookup"><span data-stu-id="9b364-282">Press the + in the bottom right under both **On Pickup Action** and **On Placement Action**.</span></span> <span data-ttu-id="9b364-283">シーンから EnergyHub **(オブジェクト)** フィールドに [] をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="9b364-283">Drag EnergyHub from the scene into the **None (Object)** fields.</span></span>
    * <span data-ttu-id="9b364-284">[**ピックアップアクション**] で、[ **No Function**  ->  **EnergyHubBase**  ->  **resetanimation**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b364-284">Under **On Pickup Action**, click on **No Function** -> **EnergyHubBase** -> **ResetAnimation**.</span></span>
    * <span data-ttu-id="9b364-285">[**配置アクション**] で、[ **No Function**  ->  **EnergyHubBase**  ->  **onselect**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b364-285">Under **On Placement Action**, click on **No Function** -> **EnergyHubBase** -> **OnSelect**.</span></span>

![サウンドとアクションを使用して配置するには、タップしてください](images/holograms220-taptoplace.png)

### <a name="part-2---sound-occlusion"></a><span data-ttu-id="9b364-287">パート 2-サウンドオクルージョン</span><span class="sxs-lookup"><span data-stu-id="9b364-287">Part 2 - Sound Occlusion</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9b364-288">主要概念</span><span class="sxs-lookup"><span data-stu-id="9b364-288">Key Concepts</span></span>

* <span data-ttu-id="9b364-289">ライトのようなサウンドは、occluded にすることができます。</span><span class="sxs-lookup"><span data-stu-id="9b364-289">Sound, like light, can be occluded.</span></span>

<span data-ttu-id="9b364-290">従来の例としては、コンサートホールがあります。</span><span class="sxs-lookup"><span data-stu-id="9b364-290">A classic example is a concert hall.</span></span> <span data-ttu-id="9b364-291">リスナーがホールの外部にあり、ドアが閉じている場合、音楽サウンドは muffled ます。</span><span class="sxs-lookup"><span data-stu-id="9b364-291">When a listener is standing outside of the hall and the door is closed, the music sounds muffled.</span></span> <span data-ttu-id="9b364-292">また、通常はボリュームが減少しています。</span><span class="sxs-lookup"><span data-stu-id="9b364-292">There is also typically a reduction in volume.</span></span> <span data-ttu-id="9b364-293">ドアを開くと、実際のボリュームでサウンドの全範囲が聞こえます。</span><span class="sxs-lookup"><span data-stu-id="9b364-293">When the door is opened, the full spectrum of the sound is heard at the actual volume.</span></span> <span data-ttu-id="9b364-294">高頻度のサウンドは、一般に低周波数よりも多く吸収されます。</span><span class="sxs-lookup"><span data-stu-id="9b364-294">High frequency sounds are generally absorbed more than low frequencies.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9b364-295">手順</span><span class="sxs-lookup"><span data-stu-id="9b364-295">Instructions</span></span>

* <span data-ttu-id="9b364-296">[ **階層** ] パネルで、[ **HologramCollection** ] を展開し、[ **P0LY**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-296">In the **Hierarchy** panel, expand **HologramCollection** and select **P0LY**.</span></span>
* <span data-ttu-id="9b364-297">[ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] をクリックし、 **オーディオエミッタ** を追加します。</span><span class="sxs-lookup"><span data-stu-id="9b364-297">In the **Inspector** panel, click **Add Component** and add **Audio Emitter**.</span></span>

<span data-ttu-id="9b364-298">オーディオエミッタクラスは、次の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="9b364-298">The Audio Emitter class provides the following features:</span></span>

* <span data-ttu-id="9b364-299">**Audiosource** のボリュームに対するすべての変更を復元します。</span><span class="sxs-lookup"><span data-stu-id="9b364-299">Restores any changes to the volume of the **AudioSource**.</span></span>
* <span data-ttu-id="9b364-300">**AudioEmitter** がアタッチされて **いる、ユーザー** の位置から、 **RaycastNonAlloc** を実行します。</span><span class="sxs-lookup"><span data-stu-id="9b364-300">Performs a **Physics.RaycastNonAlloc** from the user's position in the direction of the **GameObject** to which the **AudioEmitter** is attached.</span></span>

<span data-ttu-id="9b364-301">RaycastNonAlloc メソッドは、割り当てと返される結果の数を制限するために、パフォーマンスの最適化として使用されます。</span><span class="sxs-lookup"><span data-stu-id="9b364-301">The RaycastNonAlloc method is used as a performance optimization to limit allocations as well as the number of results returned.</span></span>

* <span data-ttu-id="9b364-302">検出された各 **Iaudioinfluencer** ついて、は **applyeffect** メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9b364-302">For each **IAudioInfluencer** encountered, calls the **ApplyEffect** method.</span></span>
* <span data-ttu-id="9b364-303">以前に発生したすべての **Iaudioinfluencer** ついて、 **removeeffect** メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9b364-303">For each previous **IAudioInfluencer** that is no longer encountered, call the **RemoveEffect** method.</span></span>

<span data-ttu-id="9b364-304">AudioEmitter は、フレームごとではなく、人間の時間単位で更新されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9b364-304">Note that AudioEmitter updates on human time scales, as opposed to on a per frame basis.</span></span> <span data-ttu-id="9b364-305">この処理が行われるのは、一般に、影響をより頻繁に更新する必要があるほど高速ではないためです。</span><span class="sxs-lookup"><span data-stu-id="9b364-305">This is done because humans generally do not move fast enough for the effect to need to be updated more frequently than every quarter or half of a second.</span></span> <span data-ttu-id="9b364-306">ある場所から別の場所に急速にテレポートするホログラムは、錯覚を壊す可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-306">Holograms that teleport rapidly from one location to another can break the illusion.</span></span>

* <span data-ttu-id="9b364-307">[ **階層** ] パネルで、[ **HologramCollection**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b364-307">In the **Hierarchy** panel, expand **HologramCollection**.</span></span>
* <span data-ttu-id="9b364-308">**EnergyHub** を展開し、[ **bloboutside**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-308">Expand **EnergyHub** and select **BlobOutside**.</span></span>
* <span data-ttu-id="9b364-309">[ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] をクリックし、 **Audio Occluder** を追加します。</span><span class="sxs-lookup"><span data-stu-id="9b364-309">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="9b364-310">**Audio Occluder** で、[**カットオフの頻度**] を **1500** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-310">In **Audio Occluder**, set **Cutoff Frequency** to **1500**.</span></span>

<span data-ttu-id="9b364-311">この設定により、AudioSource の周波数が 1500 Hz 以下に制限されます。</span><span class="sxs-lookup"><span data-stu-id="9b364-311">This setting limits the AudioSource frequencies to 1500 Hz and below.</span></span>

* <span data-ttu-id="9b364-312">**ボリュームパススルー** を **0.9** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-312">Set **Volume Pass Through** to **0.9**.</span></span>

<span data-ttu-id="9b364-313">この設定により、AudioSource の音量が現在のレベルの90% に減少します。</span><span class="sxs-lookup"><span data-stu-id="9b364-313">This setting reduces the volume of the AudioSource to 90% of it's current level.</span></span>

<span data-ttu-id="9b364-314">Audio Occluder は、次のように IAudioInfluencer 有力企業を実装します。</span><span class="sxs-lookup"><span data-stu-id="9b364-314">Audio Occluder implements IAudioInfluencer to:</span></span>

* <span data-ttu-id="9b364-315">Audiosource に接続されている **Audiolowpass filter** を使用し **AudioSource** て、遮蔽効果を適用します。このフィルターは、 **AudioEmitter** を購入します。</span><span class="sxs-lookup"><span data-stu-id="9b364-315">Apply an occlusion effect using an **AudioLowPassFilter** which gets attached to the **AudioSource** managed buy the **AudioEmitter**.</span></span>
* <span data-ttu-id="9b364-316">オーディオソースにボリュームの減衰を適用します。</span><span class="sxs-lookup"><span data-stu-id="9b364-316">Applies volume attenuation to the AudioSource.</span></span>
* <span data-ttu-id="9b364-317">ニュートラルカットオフ周波数を設定し、フィルターを無効にすることで、効果を無効にします。</span><span class="sxs-lookup"><span data-stu-id="9b364-317">Disables the effect by setting a neutral cutoff frequency and disabling the filter.</span></span>

<span data-ttu-id="9b364-318">ニュートラルとして使用される頻度は 22 kHz (22000 Hz) です。</span><span class="sxs-lookup"><span data-stu-id="9b364-318">The frequency used as neutral is 22 kHz (22000 Hz).</span></span> <span data-ttu-id="9b364-319">この頻度が選択されたのは、人間の耳によって聞こえる可能性のある最大周波数を超えているためです。これにより、サウンドへのはっきりの影響はありません。</span><span class="sxs-lookup"><span data-stu-id="9b364-319">This frequency was chosen due to it being above the nominal maximum frequency that can be heard by the human ear, this making no discernable impact to the sound.</span></span>

* <span data-ttu-id="9b364-320">[ **階層** ] パネルで、[ **SpatialMapping**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-320">In the **Hierarchy** panel, select **SpatialMapping**.</span></span>
* <span data-ttu-id="9b364-321">[ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] をクリックし、 **Audio Occluder** を追加します。</span><span class="sxs-lookup"><span data-stu-id="9b364-321">In the **Inspector** panel, click **Add Component** and add **Audio Occluder**.</span></span>
* <span data-ttu-id="9b364-322">**Audio Occluder** で、[**カットオフの頻度**] を **750** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-322">In **Audio Occluder**, set **Cutoff Frequency** to **750**.</span></span>

<span data-ttu-id="9b364-323">ユーザーと **AudioEmitter** の間のパスに複数の occluders がある場合、最も低い頻度がフィルターに適用されます。</span><span class="sxs-lookup"><span data-stu-id="9b364-323">When multiple occluders are in the path between the user and the **AudioEmitter**, the lowest frequency is applied to the filter.</span></span>

* <span data-ttu-id="9b364-324">**ボリュームパススルー** を **0.75** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-324">Set **Volume Pass Through** to **0.75**.</span></span>

<span data-ttu-id="9b364-325">ユーザーと **AudioEmitter** の間のパスに複数の occluders がある場合、ボリュームパススルーが加算に適用されます。</span><span class="sxs-lookup"><span data-stu-id="9b364-325">When multiple occluders are in the path between the user and the **AudioEmitter**, the volume pass through is applied additively.</span></span>

* <span data-ttu-id="9b364-326">[ **階層** ] パネルで、[ **マネージャー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-326">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="9b364-327">[ **インスペクター** ] パネルで、[ **音声入力ハンドラ**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b364-327">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="9b364-328">**音声入力ハンドラー** で、 **[充電**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b364-328">In **Speech Input Handler**, expand **Go Charge**.</span></span>
* <span data-ttu-id="9b364-329">**関数** を **PolyActions** に変更します。</span><span class="sxs-lookup"><span data-stu-id="9b364-329">Change **No Function** to **PolyActions.GoCharge**.</span></span>

![キーワード: 利用料金](images/gocharge.png)

* <span data-ttu-id="9b364-331">展開 **し** ます。</span><span class="sxs-lookup"><span data-stu-id="9b364-331">Expand **Come Here**.</span></span>
* <span data-ttu-id="9b364-332">**関数** を PolyActions に変更します。**カムバック** です。</span><span class="sxs-lookup"><span data-stu-id="9b364-332">Change **No Function** to **PolyActions.ComeBack**.</span></span>

![キーワード: ここにあります](images/comehere.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="9b364-334">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="9b364-334">Build and Deploy</span></span>

* <span data-ttu-id="9b364-335">前と同様に、Unity でプロジェクトをビルドし、Visual Studio に配置します。</span><span class="sxs-lookup"><span data-stu-id="9b364-335">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="9b364-336">アプリケーションが展開された後:</span><span class="sxs-lookup"><span data-stu-id="9b364-336">After the application is deployed:</span></span>

* <span data-ttu-id="9b364-337">*「充電」* と入力して、P0LY にエネルギーハブを入力します。</span><span class="sxs-lookup"><span data-stu-id="9b364-337">Say *"Go Charge"* to have P0LY enter the Energy Hub.</span></span>

<span data-ttu-id="9b364-338">サウンドの変更点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="9b364-338">Note the change in the sound.</span></span> <span data-ttu-id="9b364-339">Muffled と少し静かに聞こえます。</span><span class="sxs-lookup"><span data-stu-id="9b364-339">It should sound muffled and a little quieter.</span></span> <span data-ttu-id="9b364-340">自分とエネルギーハブの間に壁やその他のオブジェクトを配置できる場合は、現実の世界によって遮蔽されているため、さらに消音の音が発生します。</span><span class="sxs-lookup"><span data-stu-id="9b364-340">If you are able to position yourself with a wall or other object between you and the Energy Hub, you should notice a further muffling of the sound due to the occlusion by the real world.</span></span>

* <span data-ttu-id="9b364-341">*「ここ* に移動」と言うと、P0LY を使用してエネルギーハブを離れ、その前に配置します。</span><span class="sxs-lookup"><span data-stu-id="9b364-341">Say *"Come Here"* to have P0LY leave the Energy Hub and position itself in front of you.</span></span>

<span data-ttu-id="9b364-342">P0LY がエネルギーハブを終了すると、サウンドオクルージョンが削除されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9b364-342">Note that the sound occlusion is removed once P0LY exits the Energy Hub.</span></span> <span data-ttu-id="9b364-343">引き続き P0LY が聞こえる場合は、現実世界によって occluded されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-343">If you are still hearing occlusion, P0LY may be occluded by the real world.</span></span> <span data-ttu-id="9b364-344">P0LY を明確に理解できるように、移動してみてください。</span><span class="sxs-lookup"><span data-stu-id="9b364-344">Try moving to ensure you have a clear line of sight to P0LY.</span></span>

### <a name="part-3---room-models"></a><span data-ttu-id="9b364-345">パート 3-部屋モデル</span><span class="sxs-lookup"><span data-stu-id="9b364-345">Part 3 - Room Models</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9b364-346">主要概念</span><span class="sxs-lookup"><span data-stu-id="9b364-346">Key Concepts</span></span>

* <span data-ttu-id="9b364-347">領域のサイズは、サウンドのローカライズに寄与する subliminal キューを提供します。</span><span class="sxs-lookup"><span data-stu-id="9b364-347">The size of the space provides subliminal queues that contribute to sound localization.</span></span>
* <span data-ttu-id="9b364-348">Room モデルは、**Audiosource** ごとに設定されます。</span><span class="sxs-lookup"><span data-stu-id="9b364-348">Room models are set per-**AudioSource**.</span></span>
* <span data-ttu-id="9b364-349">[MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)には、部屋モデルを設定するためのコードが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9b364-349">The [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity) provides code for setting the room model.</span></span>
* <span data-ttu-id="9b364-350">Mixed Reality エクスペリエンスの場合は、実際のワールド空間に最も適した部屋モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-350">For Mixed Reality experiences, select the room model that best fits the real world space.</span></span>

<span data-ttu-id="9b364-351">仮想現実のシナリオを作成する場合は、仮想環境に最も適した部屋モデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-351">If you are creating a Virtual Reality scenario, select the room model that best fits the virtual environment.</span></span>

## <a name="chapter-4---sound-design"></a><span data-ttu-id="9b364-352">第4章-サウンドのデザイン</span><span class="sxs-lookup"><span data-stu-id="9b364-352">Chapter 4 - Sound Design</span></span>

### <a name="objectives"></a><span data-ttu-id="9b364-353">目標</span><span class="sxs-lookup"><span data-stu-id="9b364-353">Objectives</span></span>

* <span data-ttu-id="9b364-354">効果的なサウンドデザインの考慮事項を理解します。</span><span class="sxs-lookup"><span data-stu-id="9b364-354">Understand considerations for effective sound design.</span></span>
* <span data-ttu-id="9b364-355">さまざまな手法とガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9b364-355">Learn mixing techniques and guidelines.</span></span>

### <a name="part-1---sound-and-experience-design"></a><span data-ttu-id="9b364-356">パート 1-サウンドとエクスペリエンスの設計</span><span class="sxs-lookup"><span data-stu-id="9b364-356">Part 1 - Sound and Experience Design</span></span>

<span data-ttu-id="9b364-357">このセクションでは、主要なサウンドとエクスペリエンスの設計に関する考慮事項とガイドラインについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9b364-357">This section discusses key sound and experience design considerations and guidelines.</span></span>

#### <a name="normalize-all-sounds"></a><span data-ttu-id="9b364-358">すべてのサウンドを正規化する</span><span class="sxs-lookup"><span data-stu-id="9b364-358">Normalize all sounds</span></span>

<span data-ttu-id="9b364-359">これにより、サウンドごとにボリュームレベルを調整する特殊なケースコードが不要になるため、サウンドファイルを簡単に更新できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9b364-359">This avoids the need for special case code to adjust volume levels per sound, which can be time consuming and limits the ability to easily update sound files.</span></span>

#### <a name="design-for-an-untethered-experience"></a><span data-ttu-id="9b364-360">ならではエクスペリエンスの設計</span><span class="sxs-lookup"><span data-stu-id="9b364-360">Design for an untethered experience</span></span>

<span data-ttu-id="9b364-361">HoloLens は、完全に包含されたならでは holographic コンピューターです。</span><span class="sxs-lookup"><span data-stu-id="9b364-361">HoloLens is a fully contained, untethered holographic computer.</span></span> <span data-ttu-id="9b364-362">ユーザーは移動中にエクスペリエンスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9b364-362">Your users can and will use your experiences while moving.</span></span> <span data-ttu-id="9b364-363">オーディオミックスをテストしてください。</span><span class="sxs-lookup"><span data-stu-id="9b364-363">Be sure to test your audio mix by walking around.</span></span>

#### <a name="emit-sound-from-logical-locations-on-your-holograms"></a><span data-ttu-id="9b364-364">ホログラムの論理位置からサウンドを生成します</span><span class="sxs-lookup"><span data-stu-id="9b364-364">Emit sound from logical locations on your holograms</span></span>

<span data-ttu-id="9b364-365">現実の世界では、犬は尾からほえていません。人間の声は彼の足から来ていません。</span><span class="sxs-lookup"><span data-stu-id="9b364-365">In the real world, a dog does not bark from its tail and a human's voice does not come from his/her feet.</span></span> <span data-ttu-id="9b364-366">ホログラムの予期しない部分からサウンドを生成しないようにします。</span><span class="sxs-lookup"><span data-stu-id="9b364-366">Avoid having your sounds emit from unexpected portions of your holograms.</span></span>

<span data-ttu-id="9b364-367">小さいホログラムの場合は、ジオメトリの中心からサウンドを出力するのが妥当です。</span><span class="sxs-lookup"><span data-stu-id="9b364-367">For small holograms, it is reasonable to have sound emit from the center of the geometry.</span></span>

#### <a name="familiar-sounds-are-most-localizable"></a><span data-ttu-id="9b364-368">使い慣れたサウンドが最もローカライズ可能</span><span class="sxs-lookup"><span data-stu-id="9b364-368">Familiar sounds are most localizable</span></span>

<span data-ttu-id="9b364-369">人間の声と音楽は、非常に簡単にローカライズできます。</span><span class="sxs-lookup"><span data-stu-id="9b364-369">The human voice and music are very easy to localize.</span></span> <span data-ttu-id="9b364-370">だれかがあなたの名前を呼び出すと、声が出た方向と、それまでの距離から、正確に判断できます。</span><span class="sxs-lookup"><span data-stu-id="9b364-370">If someone calls your name, you are able to very accurately determine from what direction the voice came and from how far away.</span></span> <span data-ttu-id="9b364-371">あまり知られていないサウンドをローカライズするのは困難です。</span><span class="sxs-lookup"><span data-stu-id="9b364-371">Short, unfamiliar sounds are harder to localize.</span></span>

#### <a name="be-cognizant-of-user-expectations"></a><span data-ttu-id="9b364-372">ユーザーの期待に cognizant</span><span class="sxs-lookup"><span data-stu-id="9b364-372">Be cognizant of user expectations</span></span>

<span data-ttu-id="9b364-373">人生 experience は、サウンドの場所を特定する機能の一部を果たします。</span><span class="sxs-lookup"><span data-stu-id="9b364-373">Life experience plays a part in our ability to identify the location of a sound.</span></span> <span data-ttu-id="9b364-374">これは、人間の声が特に簡単にローカライズできる理由の1つです。</span><span class="sxs-lookup"><span data-stu-id="9b364-374">This is one reason why the human voice is particularly easy to localize.</span></span> <span data-ttu-id="9b364-375">サウンドを配置する際には、ユーザーが学習した期待を把握しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="9b364-375">It is important to be aware of your user's learned expectations when placing your sounds.</span></span>

<span data-ttu-id="9b364-376">たとえば、他のユーザーが鳥の曲を聞いたときには、通常、鳥が見やすくなる傾向があります (飛行中またはツリー内)。</span><span class="sxs-lookup"><span data-stu-id="9b364-376">For example, when someone hears a bird song they generally look up, as birds tend to be above the line of sight (flying or in a tree).</span></span> <span data-ttu-id="9b364-377">ユーザーは、サウンドの正しい方向を変えることは珍しくありませんが、間違った垂直方向では、ホログラムが見つからないときに混乱や不満を感じます。</span><span class="sxs-lookup"><span data-stu-id="9b364-377">It is not uncommon for a user to turn in the correct direction of a sound, but look in the wrong vertical direction and become confused or frustrated when they are unable to find the hologram.</span></span>

#### <a name="avoid-hidden-emitters"></a><span data-ttu-id="9b364-378">非表示の発信器を回避する</span><span class="sxs-lookup"><span data-stu-id="9b364-378">Avoid hidden emitters</span></span>

<span data-ttu-id="9b364-379">現実には、サウンドを聞くと、通常、サウンドを発しているオブジェクトを特定できます。</span><span class="sxs-lookup"><span data-stu-id="9b364-379">In the real world, if we hear a sound, we can generally identify the object that is emitting the sound.</span></span> <span data-ttu-id="9b364-380">また、エクスペリエンスにも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="9b364-380">This should also hold true in your experiences.</span></span> <span data-ttu-id="9b364-381">ユーザーがサウンドを聞いたときに、音が聞こえ、オブジェクトを表示できないことを混乱ことがあります。</span><span class="sxs-lookup"><span data-stu-id="9b364-381">It can be very disconcerting for users to hear a sound, know from where the sound originates and be unable to see an object.</span></span>

<span data-ttu-id="9b364-382">このガイドラインにはいくつかの例外があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-382">There are some exceptions to this guideline.</span></span> <span data-ttu-id="9b364-383">たとえば、フィールドの crickets などのアンビエントサウンドが表示されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-383">For example, ambient sounds such as crickets in a field need not be visible.</span></span> <span data-ttu-id="9b364-384">生命経験により、これらのサウンドのソースについての知識を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="9b364-384">Life experience gives us familiarity with the source of these sounds without the need to see it.</span></span>

### <a name="part-2---sound-mixing"></a><span data-ttu-id="9b364-385">パート 2-サウンドの混合</span><span class="sxs-lookup"><span data-stu-id="9b364-385">Part 2 - Sound Mixing</span></span>

#### <a name="target-your-mix-for-70-volume-on-the-hololens"></a><span data-ttu-id="9b364-386">HoloLens で70% のボリュームをターゲットにする</span><span class="sxs-lookup"><span data-stu-id="9b364-386">Target your mix for 70% volume on the HoloLens</span></span>

<span data-ttu-id="9b364-387">Mixed Reality エクスペリエンスでは、ホログラムを現実世界で見ることができます。</span><span class="sxs-lookup"><span data-stu-id="9b364-387">Mixed Reality experiences allow holograms to be seen in the real world.</span></span> <span data-ttu-id="9b364-388">また、現実世界のサウンドを聞くこともできます。</span><span class="sxs-lookup"><span data-stu-id="9b364-388">They should also allow real world sounds to be heard.</span></span> <span data-ttu-id="9b364-389">70% のボリュームターゲットを使用すると、ユーザーは自分の体験を楽しむことができます。</span><span class="sxs-lookup"><span data-stu-id="9b364-389">A 70% volume target enables the user to hear the world around them along with the sound of your experience.</span></span>

#### <a name="hololens-at-100-volume-should-drown-out-external-sounds"></a><span data-ttu-id="9b364-390">100% ボリュームの HoloLens は外部サウンドを drown 必要があります</span><span class="sxs-lookup"><span data-stu-id="9b364-390">HoloLens at 100% volume should drown out external sounds</span></span>

<span data-ttu-id="9b364-391">ボリュームレベル100% は、仮想現実のエクスペリエンスに似ています。</span><span class="sxs-lookup"><span data-stu-id="9b364-391">A volume level of 100% is akin to a Virtual Reality experience.</span></span> <span data-ttu-id="9b364-392">視覚的には、ユーザーは別の世界に転送されます。</span><span class="sxs-lookup"><span data-stu-id="9b364-392">Visually, the user is transported to a different world.</span></span> <span data-ttu-id="9b364-393">同じものが true 音声でを保持している必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-393">The same should hold true audibly.</span></span>

#### <a name="use-the-unity-audiomixer-to-adjust-categories-of-sounds"></a><span data-ttu-id="9b364-394">Unity AudioMixer を使用して、サウンドのカテゴリを調整する</span><span class="sxs-lookup"><span data-stu-id="9b364-394">Use the Unity AudioMixer to adjust categories of sounds</span></span>

<span data-ttu-id="9b364-395">ミックスを設計する場合、サウンドカテゴリを作成し、ボリュームを1つの単位として増減できることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="9b364-395">When designing your mix, it is often helpful to create sound categories and have the ability to increase or decrease their volume as a unit.</span></span> <span data-ttu-id="9b364-396">これにより、各サウンドの相対レベルが維持され、全体的なミックスをすばやく簡単に変更できるようになります。</span><span class="sxs-lookup"><span data-stu-id="9b364-396">This retains the relative levels of each sound while enabling quick and easy changes to the overall mix.</span></span> <span data-ttu-id="9b364-397">一般的なカテゴリは次のとおりです。サウンド効果、アンビエント、ボイスオーバー、およびバックグラウンドミュージック。</span><span class="sxs-lookup"><span data-stu-id="9b364-397">Common categories include; sound effects, ambience, voice overs and background music.</span></span>

#### <a name="mix-sounds-based-on-the-users-gaze"></a><span data-ttu-id="9b364-398">ユーザーの宝石に基づいてサウンドをミキシングする</span><span class="sxs-lookup"><span data-stu-id="9b364-398">Mix sounds based on the user's gaze</span></span>

<span data-ttu-id="9b364-399">多くの場合、ユーザーが見ている (またはそうでない) 場所に基づいて、エクスペリエンスのサウンドミックスを変更すると便利な場合があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-399">It can often be useful to change the sound mix in your experience based on where a user is (or is not) looking.</span></span> <span data-ttu-id="9b364-400">この手法の一般的な用途の1つは、Holographic フレームの外側にあるホログラムのボリュームレベルを下げることです。これにより、ユーザーは前の情報に簡単に集中することができます。</span><span class="sxs-lookup"><span data-stu-id="9b364-400">One common use for this technique are to reduce the volume level for holograms that are outside of the Holographic Frame to make it easier for the user to focus on the information in front of them.</span></span> <span data-ttu-id="9b364-401">もう1つの用途は、ユーザーが重要なイベントに注意を向けるために、サウンドの音量を上げることです。</span><span class="sxs-lookup"><span data-stu-id="9b364-401">Another use is to increase the volume of a sound to draw the user's attention to an important event.</span></span>

#### <a name="building-your-mix"></a><span data-ttu-id="9b364-402">ミックスの構築</span><span class="sxs-lookup"><span data-stu-id="9b364-402">Building your mix</span></span>

<span data-ttu-id="9b364-403">ミックスを構築するときは、エクスペリエンスのバックグラウンドオーディオから始め、重要度に基づいてレイヤーを追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9b364-403">When building your mix, it is recommended to start with your experience's background audio and add layers based on importance.</span></span> <span data-ttu-id="9b364-404">多くの場合、これにより、各レイヤーは前のレイヤーよりも大きくなります。</span><span class="sxs-lookup"><span data-stu-id="9b364-404">Often, this results in each layer being louder than the previous.</span></span>

<span data-ttu-id="9b364-405">ミックスを反転したじょうごとして練りし、一番下に最も重要ではない (一般的に quietest の) サウンドを使用して、次の図のようなミックスを構築することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9b364-405">Imagining your mix as an inverted funnel, with the least important (and generally quietest sounds) at the bottom, it is recommended to structure your mix similar to the following diagram.</span></span>

![サウンドミックスの構造](images/soundlevels.png)

<span data-ttu-id="9b364-407">ボイスオーバーは興味深いシナリオです。</span><span class="sxs-lookup"><span data-stu-id="9b364-407">Voice overs are an interesting scenario.</span></span> <span data-ttu-id="9b364-408">作成中のエクスペリエンスに基づいて、ステレオ (ローカライズされていない) サウンドを使用するか、またはボイスオーバーを spatialize することができます。</span><span class="sxs-lookup"><span data-stu-id="9b364-408">Based on the experience you are creating you may wish to have a stereo (not localized) sound or to spatialize your voice overs.</span></span> <span data-ttu-id="9b364-409">Microsoft が発行した2つのエクスペリエンスは、各シナリオの優れた例を示しています。</span><span class="sxs-lookup"><span data-stu-id="9b364-409">Two Microsoft published experiences illustrate excellent examples of each scenario.</span></span>

<span data-ttu-id="9b364-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) は、ステレオ音声を使用します。</span><span class="sxs-lookup"><span data-stu-id="9b364-410">[HoloTour](https://www.microsoft.com/store/p/holotour/9nblggh5pj87) uses a stereo voice over.</span></span> <span data-ttu-id="9b364-411">ナレーターが表示されている場所を記述する場合、サウンドは一貫しており、ユーザーの位置によって異なります。</span><span class="sxs-lookup"><span data-stu-id="9b364-411">When the narrator is describing the location being viewed, the sound is consistent and does not vary based on the user's position.</span></span> <span data-ttu-id="9b364-412">これにより、ナレーターは環境の spatialized 音から離れることなくシーンを記述できます。</span><span class="sxs-lookup"><span data-stu-id="9b364-412">This enables the narrator to describe the scene without taking away from the spatialized sounds of the environment.</span></span>

<span data-ttu-id="9b364-413">[フラグメント](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) は、検出の形式で spatialized ボイスオーバーを利用します。</span><span class="sxs-lookup"><span data-stu-id="9b364-413">[Fragments](https://www.microsoft.com/store/p/fragments/9nblggh5ggm8) utilizes a spatialized voice over in the form of a detective.</span></span> <span data-ttu-id="9b364-414">検出の声は、実際の人間が部屋にいたかのように、ユーザーが重要な手掛かりに注意を向けるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9b364-414">The detective's voice is used to help bring the user's attention to an important clue as if an actual human was in the room.</span></span> <span data-ttu-id="9b364-415">これにより、謎を immersion ことができます。</span><span class="sxs-lookup"><span data-stu-id="9b364-415">This enables an even greater sense of immersion into the experience of solving the mystery.</span></span>

### <a name="part-3--performance"></a><span data-ttu-id="9b364-416">パート 3-パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="9b364-416">Part 3 -Performance</span></span>

#### <a name="cpu-usage"></a><span data-ttu-id="9b364-417">CPU 使用率</span><span class="sxs-lookup"><span data-stu-id="9b364-417">CPU usage</span></span>

<span data-ttu-id="9b364-418">空間サウンドを使用する場合、10-12 発信器は CPU の約12% を消費します。</span><span class="sxs-lookup"><span data-stu-id="9b364-418">When using Spatial Sound, 10 - 12 emitters will consume approximately 12% of the CPU.</span></span>

#### <a name="stream-long-audio-files"></a><span data-ttu-id="9b364-419">長いオーディオファイルをストリーミングする</span><span class="sxs-lookup"><span data-stu-id="9b364-419">Stream long audio files</span></span>

<span data-ttu-id="9b364-420">オーディオデータは、特に一般的なサンプルレート (44.1 と 48 kHz) で大きくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="9b364-420">Audio data can be large, especially at common sample rates (44.1 and 48 kHz).</span></span> <span data-ttu-id="9b364-421">一般的なルールとして、5-10 秒を超えるオーディオファイルは、アプリケーションのメモリ使用量を減らすためにストリーミングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-421">A general rule is that audio files longer than 5 - 10 seconds should be streamed to reduce application memory usage.</span></span>

<span data-ttu-id="9b364-422">Unity では、ファイルのインポート設定でストリーミング用にオーディオファイルをマークできます。</span><span class="sxs-lookup"><span data-stu-id="9b364-422">In Unity, you can mark an audio file for streaming in the file's import settings.</span></span>

![オーディオのインポート設定](images/audioimportsettings.png)

## <a name="chapter-5---special-effects"></a><span data-ttu-id="9b364-424">Chapter 5-特殊効果</span><span class="sxs-lookup"><span data-stu-id="9b364-424">Chapter 5 - Special Effects</span></span>

### <a name="objectives"></a><span data-ttu-id="9b364-425">目標</span><span class="sxs-lookup"><span data-stu-id="9b364-425">Objectives</span></span>

* <span data-ttu-id="9b364-426">"マジックウィンドウ" に奥行を追加します。</span><span class="sxs-lookup"><span data-stu-id="9b364-426">Add depth to "Magic Windows".</span></span>
* <span data-ttu-id="9b364-427">ユーザーを仮想環境に移します。</span><span class="sxs-lookup"><span data-stu-id="9b364-427">Bring the user into the virtual world.</span></span>

### <a name="magic-windows"></a><span data-ttu-id="9b364-428">マジックウィンドウ</span><span class="sxs-lookup"><span data-stu-id="9b364-428">Magic Windows</span></span>

#### <a name="key-concepts"></a><span data-ttu-id="9b364-429">主要概念</span><span class="sxs-lookup"><span data-stu-id="9b364-429">Key Concepts</span></span>

* <span data-ttu-id="9b364-430">非表示の世界にビューを作成することは、視覚的に説得力のあるものです。</span><span class="sxs-lookup"><span data-stu-id="9b364-430">Creating views into a hidden world, is visually compelling.</span></span>
* <span data-ttu-id="9b364-431">ホログラムやユーザーが非表示の世界に近づいたときにオーディオ効果を追加して、リアリティを高めます。</span><span class="sxs-lookup"><span data-stu-id="9b364-431">Enhance realism by adding audio effects when a hologram or the user is near the hidden world.</span></span>

#### <a name="instructions"></a><span data-ttu-id="9b364-432">手順</span><span class="sxs-lookup"><span data-stu-id="9b364-432">Instructions</span></span>

* <span data-ttu-id="9b364-433">[ **階層** ] パネルで、[ **HologramCollection** ] を展開し、[ **黄泉**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-433">In the **Hierarchy** panel, expand **HologramCollection** and select **Underworld**.</span></span>
* <span data-ttu-id="9b364-434">[ **黄泉** ] を展開し、[ **VoiceSource**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-434">Expand **Underworld** and select **VoiceSource**.</span></span>
* <span data-ttu-id="9b364-435">[ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] をクリックし、ユーザーの **音声効果** を追加します。</span><span class="sxs-lookup"><span data-stu-id="9b364-435">In the **Inspector** panel, click **Add Component** and add **User Voice Effect**.</span></span>

<span data-ttu-id="9b364-436">**Audiosource** コンポーネントが **VoiceSource** に追加されます。</span><span class="sxs-lookup"><span data-stu-id="9b364-436">An **AudioSource** component will be added to **VoiceSource**.</span></span>

* <span data-ttu-id="9b364-437">**Audiosource** で、[**出力**] を **UserVoice (ミキサー)** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-437">In **AudioSource**, set **Output** to **UserVoice (Mixer)**.</span></span>
* <span data-ttu-id="9b364-438">**Spatialize** チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="9b364-438">Check the **Spatialize** checkbox.</span></span>
* <span data-ttu-id="9b364-439">[ **空間 Blend** ] スライダーを **3d** にドラッグするか、編集ボックスに「 **1** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="9b364-439">Drag the **Spatial Blend** slider all the way to **3D**, or enter **1** in the edit box.</span></span>
* <span data-ttu-id="9b364-440">**3D サウンド設定** を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b364-440">Expand **3D Sound Settings**.</span></span>
* <span data-ttu-id="9b364-441">**ドップラーレベル** を **0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-441">Set **Doppler Level** to **0**.</span></span>
* <span data-ttu-id="9b364-442">[ **ユーザーの声の効果**] で、[ **親オブジェクト** ] をシーンから **黄泉** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-442">In **User Voice Effect**, set **Parent Object** to the **Underworld** from the scene.</span></span>
* <span data-ttu-id="9b364-443">**Max Distance** を **1** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-443">Set **Max Distance** to **1**.</span></span>

<span data-ttu-id="9b364-444">[ **最大距離** の設定] を使用すると、 **ユーザーの音声効果** は、ユーザーが親オブジェクトに対して、効果を有効にする前にどのように閉じる必要があるかを示します。</span><span class="sxs-lookup"><span data-stu-id="9b364-444">Setting **Max Distance** tells **User Voice Effect** how close the user must be to the parent object before the effect is enabled.</span></span>

* <span data-ttu-id="9b364-445">[ **ユーザーの音声効果**] で、[ **コーラスパラメーター**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b364-445">In **User Voice Effect**, expand **Chorus Parameters**.</span></span>
* <span data-ttu-id="9b364-446">**深さ** を **0.1** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-446">Set **Depth** to **0.1**.</span></span>
* <span data-ttu-id="9b364-447">**タップ1ボリューム** を設定し、 **2 つのボリュームをタップ** して、 **3 つのボリューム** を **0.8** にタップします。</span><span class="sxs-lookup"><span data-stu-id="9b364-447">Set **Tap 1 Volume**, **Tap 2 Volume** and **Tap 3 Volume** to **0.8**.</span></span>
* <span data-ttu-id="9b364-448">**元のサウンドボリューム** を **0.5** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-448">Set **Original Sound Volume** to **0.5**.</span></span>

<span data-ttu-id="9b364-449">前の設定では、ユーザーの声に豊富な部分を追加するために使用される Unity **AudioChorusFilter** のパラメーターを構成しています。</span><span class="sxs-lookup"><span data-stu-id="9b364-449">The previous settings configure the parameters of the Unity **AudioChorusFilter** used to add richness to the user's voice.</span></span>

* <span data-ttu-id="9b364-450">[ **ユーザーの音声効果**] で、[ **エコーパラメーター**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b364-450">In **User Voice Effect**, expand **Echo Parameters**.</span></span>
* <span data-ttu-id="9b364-451">**Delay** を **300** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-451">Set **Delay** to **300**</span></span>
* <span data-ttu-id="9b364-452">**減衰率** を **0.2** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-452">Set **Decay Ratio** to **0.2**.</span></span>
* <span data-ttu-id="9b364-453">**元のサウンドボリューム** を **0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-453">Set **Original Sound Volume** to **0**.</span></span>

<span data-ttu-id="9b364-454">前の設定では、ユーザーの音声をエコーするために使用する Unity **AudioEchoFilter** のパラメーターを構成しています。</span><span class="sxs-lookup"><span data-stu-id="9b364-454">The previous settings configure the parameters of the Unity **AudioEchoFilter** used to cause the user's voice to echo.</span></span>

<span data-ttu-id="9b364-455">ユーザーの声効果スクリプトは、次のことを担当します。</span><span class="sxs-lookup"><span data-stu-id="9b364-455">The User Voice Effect script is responsible for:</span></span>

* <span data-ttu-id="9b364-456">ユーザーと、スクリプトがアタッチされているユーザー **オブジェクト** との距離を測定します。</span><span class="sxs-lookup"><span data-stu-id="9b364-456">Measuring the distance between the user and the **GameObject** to which the script is attached.</span></span>
* <span data-ttu-id="9b364-457">ユーザーが接続 **オブジェクト** を接続しているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="9b364-457">Determining whether or not the user is facing the **GameObject**.</span></span>

<span data-ttu-id="9b364-458">ユーザーは、効果を有効にするために、距離に関係なく、接続オブジェクトに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b364-458">The user must be facing the GameObject, regardless of distance, for the effect to be enabled.</span></span>

* <span data-ttu-id="9b364-459">**AudioChorusFilter** と **AudioEchoFilter** を **audiosource** に適用して構成します。</span><span class="sxs-lookup"><span data-stu-id="9b364-459">Applying and configuring an **AudioChorusFilter** and an **AudioEchoFilter** to the **AudioSource**.</span></span>
* <span data-ttu-id="9b364-460">フィルターを無効にして効果を無効にする。</span><span class="sxs-lookup"><span data-stu-id="9b364-460">Disabling the effect by disabling the filters.</span></span>

<span data-ttu-id="9b364-461">ユーザーの音声効果では、 [MixedRealityToolkit For Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity)の Mic ストリームセレクターコンポーネントを使用して、高品質の音声ストリームを選択し、unity のオーディオシステムにルーティングします。</span><span class="sxs-lookup"><span data-stu-id="9b364-461">User Voice Effect uses the Mic Stream Selector component, from the [MixedRealityToolkit for Unity](https://github.com/Microsoft/MixedRealityToolkit-Unity), to select the high quality voice stream and route it into Unity's audio system.</span></span>

* <span data-ttu-id="9b364-462">[ **階層** ] パネルで、[ **マネージャー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9b364-462">In the **Hierarchy** panel, select **Managers**.</span></span>
* <span data-ttu-id="9b364-463">[ **インスペクター** ] パネルで、[ **音声入力ハンドラ**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b364-463">In the **Inspector** panel, expand **Speech Input Handler**.</span></span>
* <span data-ttu-id="9b364-464">**音声入力ハンドラー** で、[**黄泉を表示する]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b364-464">In **Speech Input Handler**, expand **Show Underworld**.</span></span>
* <span data-ttu-id="9b364-465">**関数** を **UnderworldBase** に変更します。</span><span class="sxs-lookup"><span data-stu-id="9b364-465">Change **No Function** to **UnderworldBase.OnEnable**.</span></span>

![キーワード: 黄泉を表示する](images/showunderworld.png)

* <span data-ttu-id="9b364-467">[ **黄泉の非表示**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="9b364-467">Expand **Hide Underworld**.</span></span>
* <span data-ttu-id="9b364-468">**関数** を **UnderworldBase** に変更します。</span><span class="sxs-lookup"><span data-stu-id="9b364-468">Change **No Function** to **UnderworldBase.OnDisable**.</span></span>

![キーワード: 黄泉の非表示](images/hideunderworld.png)

#### <a name="build-and-deploy"></a><span data-ttu-id="9b364-470">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="9b364-470">Build and Deploy</span></span>

* <span data-ttu-id="9b364-471">前と同様に、Unity でプロジェクトをビルドし、Visual Studio に配置します。</span><span class="sxs-lookup"><span data-stu-id="9b364-471">As before, build the project in Unity and deploy in Visual Studio.</span></span>

<span data-ttu-id="9b364-472">アプリケーションが展開された後:</span><span class="sxs-lookup"><span data-stu-id="9b364-472">After the application is deployed:</span></span>

* <span data-ttu-id="9b364-473">表面 (壁面、床、テーブル) に顔を置いて、"黄泉の顔を *表示する"* と言います。</span><span class="sxs-lookup"><span data-stu-id="9b364-473">Face a surface (wall, floor, table) and say *"Show Underworld"*.</span></span>

<span data-ttu-id="9b364-474">黄泉のものが表示され、他のすべてのホログラムは非表示になります。</span><span class="sxs-lookup"><span data-stu-id="9b364-474">The underworld will be shown and all other holograms will be hidden.</span></span> <span data-ttu-id="9b364-475">黄泉の場所にいない場合は、実際の画面に接続していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9b364-475">If you do not see the underworld, ensure that you are facing a real-world surface.</span></span>

* <span data-ttu-id="9b364-476">黄泉のホログラムの1メートル以内にアプローチし、話し始めます。</span><span class="sxs-lookup"><span data-stu-id="9b364-476">Approach within 1 meter of the underworld hologram and start talking.</span></span>

<span data-ttu-id="9b364-477">音声にオーディオ効果が適用されました。</span><span class="sxs-lookup"><span data-stu-id="9b364-477">There are now audio effects applied to your voice!</span></span>

* <span data-ttu-id="9b364-478">黄泉の場所から離れると、効果がどのように適用されるかがわかります。</span><span class="sxs-lookup"><span data-stu-id="9b364-478">Turn away from the underworld and notice how the effect is no longer applied.</span></span>
* <span data-ttu-id="9b364-479">*"黄泉の非表示" を "* 黄泉の人に隠す" と言います。</span><span class="sxs-lookup"><span data-stu-id="9b364-479">Say *"Hide Underworld"* to hide the underworld.</span></span>

<span data-ttu-id="9b364-480">黄泉の場合は非表示になり、以前に非表示になったホログラムは再び表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b364-480">The underworld will be hidden and the previously hidden holograms will reappear.</span></span>

## <a name="the-end"></a><span data-ttu-id="9b364-481">最後です</span><span class="sxs-lookup"><span data-stu-id="9b364-481">The End</span></span>

<span data-ttu-id="9b364-482">おめでとうございます。</span><span class="sxs-lookup"><span data-stu-id="9b364-482">Congratulations!</span></span> <span data-ttu-id="9b364-483">これで **MR 空間 220: 空間サウンド** が完成しました。</span><span class="sxs-lookup"><span data-stu-id="9b364-483">You have now completed **MR Spatial 220: Spatial sound**.</span></span>

<span data-ttu-id="9b364-484">世界を聞いて、ご意見をお待ちしております。</span><span class="sxs-lookup"><span data-stu-id="9b364-484">Listen to the world and bring your experiences to life with sound!</span></span>