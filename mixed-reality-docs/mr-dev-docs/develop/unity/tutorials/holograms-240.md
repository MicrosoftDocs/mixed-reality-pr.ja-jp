---
title: MR 共有 240-複数の HoloLens デバイス
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、ホログラムの共有の詳細を確認してください。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、共有、ネットワーク、academy、チュートリアル、HoloLens、Mixed Reality Academy、unity、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット、Windows 10
ms.openlocfilehash: f57629e37463c9a05219ebae92bff8870728d688
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678261"
---
# <a name="mr-sharing-240-multiple-hololens-devices"></a><span data-ttu-id="1fa4c-104">MR 共有 240:複数の HoloLens デバイス</span><span class="sxs-lookup"><span data-stu-id="1fa4c-104">MR Sharing 240: Multiple HoloLens devices</span></span>

>[!NOTE]
><span data-ttu-id="1fa4c-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1fa4c-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1fa4c-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1fa4c-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1fa4c-109">HoloLens 2 向けには、[新しいチュートリアル シリーズ](../../../mr-learning-base-01.md)が投稿されています。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-109">[A new series of tutorials](../../../mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="1fa4c-110">ホログラムは、領域内での移動によって、世界中に残されています。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-110">Holograms are given presence in our world by remaining in place as we move about in space.</span></span> <span data-ttu-id="1fa4c-111">HoloLens は、さまざまな [座標](../../../design/coordinate-systems.md) 系を使用して、オブジェクトの位置と向きを追跡することで、ホログラムを保持します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-111">HoloLens keeps holograms in place by using various [coordinate systems](../../../design/coordinate-systems.md) to keep track of the location and orientation of objects.</span></span> <span data-ttu-id="1fa4c-112">これらの座標系をデバイス間で共有すると、共有された holographic 世界に参加するための共有エクスペリエンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-112">When we share these coordinate systems between devices, we can create a shared experience that allows us to take part in a shared holographic world.</span></span>

<span data-ttu-id="1fa4c-113">このチュートリアルでは、次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-113">In this tutorial, we will:</span></span>

* <span data-ttu-id="1fa4c-114">共有エクスペリエンスのためにネットワークをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-114">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="1fa4c-115">HoloLens デバイス間でホログラムを共有します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-115">Share holograms across HoloLens devices.</span></span>
* <span data-ttu-id="1fa4c-116">共有 holographic 世界の他のメンバーを発見します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-116">Discover other people in our shared holographic world.</span></span>
* <span data-ttu-id="1fa4c-117">他のプレーヤーをターゲットにして projectiles を起動できる、共有のインタラクティブなエクスペリエンスを作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-117">Create a shared interactive experience where you can target other players - and launch projectiles at them!</span></span>

## <a name="device-support"></a><span data-ttu-id="1fa4c-118">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="1fa4c-118">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1fa4c-119">コース</span><span class="sxs-lookup"><span data-stu-id="1fa4c-119">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1fa4c-120"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1fa4c-120"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1fa4c-121"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="1fa4c-121"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="1fa4c-122">MR 共有 240:複数の HoloLens デバイス</span><span class="sxs-lookup"><span data-stu-id="1fa4c-122">MR Sharing 240: Multiple HoloLens devices</span></span></td><td style="text-align: center;"> <span data-ttu-id="1fa4c-123">✔️</span><span class="sxs-lookup"><span data-stu-id="1fa4c-123">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="1fa4c-124">開始する前に</span><span class="sxs-lookup"><span data-stu-id="1fa4c-124">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1fa4c-125">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="1fa4c-125">Prerequisites</span></span>

* <span data-ttu-id="1fa4c-126">インターネットアクセスを使用して適切な [ツールがインストール](../../../develop/install-the-tools.md) されている WINDOWS 10 PC。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-126">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md) with Internet access.</span></span>
* <span data-ttu-id="1fa4c-127">[開発用に構成された](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)少なくとも2つの HoloLens デバイス。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-127">At least two HoloLens devices [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="1fa4c-128">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="1fa4c-128">Project files</span></span>

* <span data-ttu-id="1fa4c-129">プロジェクトに必要な [ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-129">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-240-SharedHolograms.zip) required by the project.</span></span> <span data-ttu-id="1fa4c-130">Unity 2017.2 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-130">Requires Unity 2017.2 or later.</span></span>
  * <span data-ttu-id="1fa4c-131">引き続き Unity 5.6 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-131">If you still need Unity 5.6 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.6-240.zip).</span></span>
  * <span data-ttu-id="1fa4c-132">引き続き Unity 5.5 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-132">If you still need Unity 5.5 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.5-240.zip).</span></span>
  * <span data-ttu-id="1fa4c-133">引き続き Unity 5.4 のサポートが必要な場合は、 [このリリース](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip)をご利用ください。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-133">If you still need Unity 5.4 support, please use [this release](https://github.com/Microsoft/HolographicAcademy/archive/v1.5.4-240.zip).</span></span>
* <span data-ttu-id="1fa4c-134">ファイルをデスクトップまたはその他の簡単な場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-134">Un-archive the files to your desktop or other easy to reach location.</span></span> <span data-ttu-id="1fa4c-135">フォルダー名を **Sharedholograms** として保持します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-135">Keep the folder name as **SharedHolograms**.</span></span>

>[!NOTE]
><span data-ttu-id="1fa4c-136">ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms)ます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-136">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-240-SharedHolograms).</span></span>

## <a name="chapter-1---holo-world"></a><span data-ttu-id="1fa4c-137">Chapter 1-Holo World</span><span class="sxs-lookup"><span data-stu-id="1fa4c-137">Chapter 1 - Holo World</span></span>

>[!VIDEO https://www.youtube.com/embed/c7qHYYW8rxQ]

<span data-ttu-id="1fa4c-138">この章では、最初の Unity プロジェクトをセットアップし、ビルドとデプロイのプロセスをステップ実行します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-138">In this chapter, we'll setup our first Unity project and step through the build and deploy process.</span></span>

### <a name="objectives"></a><span data-ttu-id="1fa4c-139">目標</span><span class="sxs-lookup"><span data-stu-id="1fa4c-139">Objectives</span></span>

* <span data-ttu-id="1fa4c-140">Unity をセットアップして、holographic アプリを開発します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-140">Setup Unity to develop holographic apps.</span></span>
* <span data-ttu-id="1fa4c-141">ホログラムをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-141">See your hologram!</span></span>

### <a name="instructions"></a><span data-ttu-id="1fa4c-142">手順</span><span class="sxs-lookup"><span data-stu-id="1fa4c-142">Instructions</span></span>

* <span data-ttu-id="1fa4c-143">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-143">Start Unity.</span></span>
* <span data-ttu-id="1fa4c-144">**[Open (開く)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-144">Select **Open**.</span></span>
* <span data-ttu-id="1fa4c-145">以前に unarchived した **Sharedholograms** フォルダーとして場所を入力します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-145">Enter location as the **SharedHolograms** folder you previously unarchived.</span></span>
* <span data-ttu-id="1fa4c-146">[ **プロジェクト名** ] を選択し、[ **フォルダーの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-146">Select **Project Name** and click **Select Folder**.</span></span>
* <span data-ttu-id="1fa4c-147">**階層** で、**メインカメラ** を右クリックし、[**削除**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-147">In the **Hierarchy**, right-click the **Main Camera** and select **Delete**.</span></span>
* <span data-ttu-id="1fa4c-148">**HoloToolkit-240/Prefabs/カメラ** フォルダーで、**メインカメラ** の事前 fab を見つけます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-148">In the **HoloToolkit-Sharing-240/Prefabs/Camera** folder, find the **Main Camera** prefab.</span></span>
* <span data-ttu-id="1fa4c-149">**メインカメラ** を **階層** にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-149">Drag and drop the **Main Camera** into the **Hierarchy**.</span></span>
* <span data-ttu-id="1fa4c-150">**階層** で、[**作成**] をクリックし、[**空の作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-150">In the **Hierarchy**, click on **Create** and **Create Empty**.</span></span>
* <span data-ttu-id="1fa4c-151">新しい [作成] **オブジェクト** を右クリックし、[ **名前の変更**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-151">Right-click the new **GameObject** and select **Rename**.</span></span>
* <span data-ttu-id="1fa4c-152">**HologramCollection** オブジェクトの名前を「」に変更します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-152">Rename the GameObject to **HologramCollection**.</span></span>
* <span data-ttu-id="1fa4c-153">**階層** 内の **HologramCollection** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-153">Select the **HologramCollection** object in the **Hierarchy**.</span></span>
* <span data-ttu-id="1fa4c-154">**インスペクター** で、**変換位置** を **X: 0、Y:-0.25、Z: 2** のように設定します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-154">In the **Inspector** set the **transform position** to: **X: 0, Y: -0.25, Z: 2**.</span></span>
* <span data-ttu-id="1fa4c-155">[**プロジェクト] パネル** の [**ホログラム**] フォルダーで、 **EnergyHub** 資産を見つけます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-155">In the **Holograms** folder in the **Project panel**, find the **EnergyHub** asset.</span></span>
* <span data-ttu-id="1fa4c-156">[**プロジェクト] パネル** から、 **EnergyHub** オブジェクトを **HologramCollection の子** として **階層** にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-156">Drag and drop the **EnergyHub** object from the **Project panel** to the **Hierarchy** as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="1fa4c-157">[ **ファイル] > 選択してシーンを保存...**</span><span class="sxs-lookup"><span data-stu-id="1fa4c-157">Select **File > Save Scene As...**</span></span>
* <span data-ttu-id="1fa4c-158">シーンに **Sharedholograms** という名前を付け、[ **保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-158">Name the scene **SharedHolograms** and click **Save**.</span></span>
* <span data-ttu-id="1fa4c-159">Unity の [ **再生** ] ボタンをクリックして、ホログラムをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-159">Press the **Play** button in Unity to preview your holograms.</span></span>
* <span data-ttu-id="1fa4c-160">プレビューモードを停止するには、もう一度 **Play** を押します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-160">Press **Play** a second time to stop preview mode.</span></span>

<span data-ttu-id="1fa4c-161">**Unity から Visual Studio にプロジェクトをエクスポートする**</span><span class="sxs-lookup"><span data-stu-id="1fa4c-161">**Export the project from Unity to Visual Studio**</span></span>

* <span data-ttu-id="1fa4c-162">Unity で、[ **ファイル > ビルド設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-162">In Unity select **File > Build Settings**.</span></span>
* <span data-ttu-id="1fa4c-163">シーンを追加するには、[開いている **シーンの追加** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-163">Click **Add Open Scenes** to add the scene.</span></span>
* <span data-ttu-id="1fa4c-164">[**プラットフォーム**] ボックスの一覧の [**ユニバーサル Windows プラットフォーム**] を選択し、[**プラットフォームの切り替え**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-164">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform**.</span></span>
* <span data-ttu-id="1fa4c-165">**SDK** を **Universal 10** に設定します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-165">Set **SDK** to **Universal 10**.</span></span>
* <span data-ttu-id="1fa4c-166">**ターゲットデバイス** を **HoloLens** に設定し、 **UWP ビルドの種類** を **D3D** に設定します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-166">Set **Target device** to **HoloLens** and **UWP Build Type** to **D3D**.</span></span>
* <span data-ttu-id="1fa4c-167">**Unity C# プロジェクト** を確認します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-167">Check **Unity C# Projects**.</span></span>
* <span data-ttu-id="1fa4c-168">[**ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-168">Click **Build**.</span></span>
* <span data-ttu-id="1fa4c-169">表示された [エクスプローラー] ウィンドウで、"App" という名前の **新しいフォルダー** を作成します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-169">In the file explorer window that appears, create a **New Folder** named "App".</span></span>
* <span data-ttu-id="1fa4c-170">**アプリ** フォルダーをシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-170">Single click the **App** folder.</span></span>
* <span data-ttu-id="1fa4c-171">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-171">Press **Select Folder**.</span></span>
* <span data-ttu-id="1fa4c-172">Unity が完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-172">When Unity is done, a File Explorer window will appear.</span></span>
* <span data-ttu-id="1fa4c-173">**アプリ** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-173">Open the **App** folder.</span></span>
* <span data-ttu-id="1fa4c-174">**Sharedholograms** を開いて、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-174">Open **SharedHolograms.sln** to launch Visual Studio.</span></span>
* <span data-ttu-id="1fa4c-175">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に変更し、ARM から **X86** に変更します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-175">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **X86**.</span></span>
* <span data-ttu-id="1fa4c-176">[ローカルコンピューター] の横にあるドロップダウン矢印をクリックし、[ **リモートデバイス**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-176">Click on the drop-down arrow next to Local Machine, and select **Remote Device**.</span></span>
    * <span data-ttu-id="1fa4c-177">**アドレス** を HoloLens の名前または IP アドレスに設定します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-177">Set the **Address** to the name or IP address of your HoloLens.</span></span> <span data-ttu-id="1fa4c-178">デバイスの IP アドレスがわからない場合は、[設定] の [**ネットワーク & Internet > 詳細オプション >** 確認するか、cortana **に "Cortana さん、どのような IP アドレスがあるか" を** 確認してください。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-178">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** or ask Cortana **"Hey Cortana, What's my IP address?"**</span></span>
    * <span data-ttu-id="1fa4c-179">[ **認証モード** ( **ユニバーサル**) に設定したままにします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-179">Leave the **Authentication Mode** set to **Universal**.</span></span>
    * <span data-ttu-id="1fa4c-180">[**選択] を** クリック</span><span class="sxs-lookup"><span data-stu-id="1fa4c-180">Click **Select**</span></span>
* <span data-ttu-id="1fa4c-181">[デバッグ] をクリックして [ **デバッグなしで開始** ] を >、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-181">Click **Debug > Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="1fa4c-182">初めてデバイスをデプロイする場合は、 [Visual Studio とペアリング](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-182">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>
* <span data-ttu-id="1fa4c-183">HoloLens に配置し、EnergyHub ホログラムを見つけます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-183">Put on your HoloLens and find the EnergyHub hologram.</span></span>

## <a name="chapter-2---interaction"></a><span data-ttu-id="1fa4c-184">Chapter 2-相互作用</span><span class="sxs-lookup"><span data-stu-id="1fa4c-184">Chapter 2 - Interaction</span></span>

>[!VIDEO https://www.youtube.com/embed/W60xG15a8gc]

<span data-ttu-id="1fa4c-185">この章では、ホログラムを操作します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-185">In this chapter, we'll interact with our holograms.</span></span> <span data-ttu-id="1fa4c-186">最初に、 [見つめ](../../../design/gaze-and-commit.md)を視覚化するカーソルを追加します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-186">First, we'll add a cursor to visualize our [Gaze](../../../design/gaze-and-commit.md).</span></span> <span data-ttu-id="1fa4c-187">次に、 [ジェスチャ](../../../design/gaze-and-commit.md#composite-gestures) を追加し、手を使用してホログラムをスペースに配置します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-187">Then, we'll add [Gestures](../../../design/gaze-and-commit.md#composite-gestures) and use our hand to place our holograms in space.</span></span>

### <a name="objectives"></a><span data-ttu-id="1fa4c-188">目標</span><span class="sxs-lookup"><span data-stu-id="1fa4c-188">Objectives</span></span>

* <span data-ttu-id="1fa4c-189">行方向の入力を使用してカーソルを制御します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-189">Use gaze input to control a cursor.</span></span>
* <span data-ttu-id="1fa4c-190">ジェスチャ入力を使用して、ホログラムを操作します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-190">Use gesture input to interact with holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="1fa4c-191">手順</span><span class="sxs-lookup"><span data-stu-id="1fa4c-191">Instructions</span></span>

<span data-ttu-id="1fa4c-192">**視線入力**</span><span class="sxs-lookup"><span data-stu-id="1fa4c-192">**Gaze**</span></span>

* <span data-ttu-id="1fa4c-193">[ **階層] パネル** で、 **HologramCollection** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-193">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="1fa4c-194">[ **インスペクター] パネル** で、[ **コンポーネントの追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-194">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="1fa4c-195">メニューの [検索] ボックスに「と **入力してください」** と入力します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-195">In the menu, type in the search box **Gaze Manager**.</span></span> <span data-ttu-id="1fa4c-196">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-196">Select the search result.</span></span>
* <span data-ttu-id="1fa4c-197">**HoloToolkit-Sharing-240\Prefabs\Input** フォルダーで、**カーソル** アセットを見つけます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-197">In the **HoloToolkit-Sharing-240\Prefabs\Input** folder, find the **Cursor** asset.</span></span>
* <span data-ttu-id="1fa4c-198">**カーソル** アセットを **階層** にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-198">Drag and drop the **Cursor** asset onto the **Hierarchy**.</span></span>

<span data-ttu-id="1fa4c-199">**ジェスチャ**</span><span class="sxs-lookup"><span data-stu-id="1fa4c-199">**Gesture**</span></span>

* <span data-ttu-id="1fa4c-200">[ **階層] パネル** で、 **HologramCollection** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-200">In the **Hierarchy panel** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="1fa4c-201">[ **コンポーネントの追加** ] をクリックし、検索フィールドに「 **ジェスチャマネージャー** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-201">Click **Add Component** and type **Gesture Manager** in the search field.</span></span> <span data-ttu-id="1fa4c-202">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-202">Select the search result.</span></span>
* <span data-ttu-id="1fa4c-203">[ **階層] パネル** で、[ **HologramCollection**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-203">In the **Hierarchy panel**, expand **HologramCollection**.</span></span>
* <span data-ttu-id="1fa4c-204">子 **EnergyHub** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-204">Select the child **EnergyHub** object.</span></span>
* <span data-ttu-id="1fa4c-205">[ **インスペクター] パネル** で、[ **コンポーネントの追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-205">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="1fa4c-206">メニューで、検索ボックスの **ホログラムの配置** を入力します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-206">In the menu, type in the search box **Hologram Placement**.</span></span> <span data-ttu-id="1fa4c-207">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-207">Select the search result.</span></span>
* <span data-ttu-id="1fa4c-208">[ **ファイル > [シーンの保存**] を選択してシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-208">Save the scene by selecting **File > Save Scene**.</span></span>

<span data-ttu-id="1fa4c-209">**デプロイと活用**</span><span class="sxs-lookup"><span data-stu-id="1fa4c-209">**Deploy and enjoy**</span></span>

* <span data-ttu-id="1fa4c-210">前の章の指示に従って、HoloLens にビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-210">Build and deploy to your HoloLens, using the instructions from the previous chapter.</span></span>
* <span data-ttu-id="1fa4c-211">HoloLens でアプリが起動したら、頭を動かして、EnergyHub がどのようになっているかをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-211">Once the app launches on your HoloLens, move your head around and notice how the EnergyHub follows your gaze.</span></span>
* <span data-ttu-id="1fa4c-212">ホログラムを見つめたときにカーソルがどのように表示されるかに注目してください。また、ホログラムで見られない場合はポイントライトに変わります。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-212">Notice how the cursor appears when you gaze upon the hologram, and changes to a point light when not gazing at a hologram.</span></span>
* <span data-ttu-id="1fa4c-213">エアタップを実行して、ホログラムを配置します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-213">Perform an air-tap to place the hologram.</span></span> <span data-ttu-id="1fa4c-214">この時点で、このプロジェクトでは、ホログラムを1回だけ配置できます (再デプロイしてもう一度試すことができます)。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-214">At this time in our project, you can only place the hologram once (redeploy to try again).</span></span>

## <a name="chapter-3---shared-coordinates"></a><span data-ttu-id="1fa4c-215">第3章-共有座標</span><span class="sxs-lookup"><span data-stu-id="1fa4c-215">Chapter 3 - Shared Coordinates</span></span>

>[!VIDEO https://www.youtube.com/embed/Ey8yBgWiqtg]

<span data-ttu-id="1fa4c-216">ホログラムを見て操作するのは楽しい作業ですが、さらに詳しく見ていきましょう。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-216">It's fun to see and interact with holograms, but let's go further.</span></span> <span data-ttu-id="1fa4c-217">最初の共有エクスペリエンスを設定します。すべてのユーザーが一緒に見ることができます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-217">We'll set up our first shared experience - a hologram everyone can see together.</span></span>

### <a name="objectives"></a><span data-ttu-id="1fa4c-218">目標</span><span class="sxs-lookup"><span data-stu-id="1fa4c-218">Objectives</span></span>

* <span data-ttu-id="1fa4c-219">共有エクスペリエンスのためにネットワークをセットアップします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-219">Setup a network for a shared experience.</span></span>
* <span data-ttu-id="1fa4c-220">共通の参照ポイントを確立します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-220">Establish a common reference point.</span></span>
* <span data-ttu-id="1fa4c-221">デバイス間で座標系を共有します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-221">Share coordinate systems across devices.</span></span>
* <span data-ttu-id="1fa4c-222">全員が同じホログラムを見ることがあります。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-222">Everyone sees the same hologram!</span></span>

>[!NOTE]
><span data-ttu-id="1fa4c-223">アプリが共有サーバーに接続するには、 **Internetclientserver** と **PrivateNetworkClientServer** の機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-223">The **InternetClientServer** and **PrivateNetworkClientServer** capabilities must be declared for an app to connect to the sharing server.</span></span> <span data-ttu-id="1fa4c-224">これは、既にホログラム240に含まれていますが、独自のプロジェクトでは考慮しておいてください。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-224">This is done for you already in Holograms 240, but keep this in mind for your own projects.</span></span>

>1. <span data-ttu-id="1fa4c-225">Unity エディターで、[Edit > Project Settings > Player] の順に移動して、windows media player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-225">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="1fa4c-226">[Windows ストア] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-226">Click on the "Windows Store" tab</span></span>
>3. <span data-ttu-id="1fa4c-227">[発行の設定 > 機能] セクションで、 **Internetclientserver** の機能と **PrivateNetworkClientServer** 機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-227">In the "Publishing Settings > Capabilities" section, check the **InternetClientServer** capability and the **PrivateNetworkClientServer** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="1fa4c-228">手順</span><span class="sxs-lookup"><span data-stu-id="1fa4c-228">Instructions</span></span>

* <span data-ttu-id="1fa4c-229">[ **プロジェクト] パネル** で、 **HoloToolkit-Sharing-240\Prefabs\Sharing** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-229">In the **Project panel** navigate to the **HoloToolkit-Sharing-240\Prefabs\Sharing** folder.</span></span>
* <span data-ttu-id="1fa4c-230">**共有** prefab を [**階層] パネル** にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-230">Drag and drop the **Sharing** prefab into the **Hierarchy panel**.</span></span>

<span data-ttu-id="1fa4c-231">次に、共有サービスを起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-231">Next we need to launch the sharing service.</span></span> <span data-ttu-id="1fa4c-232">この手順を実行する必要があるのは、共有エクスペリエンス内の **1 台の PC** だけです。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-232">Only **one PC** in the shared experience needs to do this step.</span></span>

* <span data-ttu-id="1fa4c-233">Unity で、上部のメニューの [ **HoloToolkit-240] メニュー** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-233">In Unity - in the top-hand menu - select the **HoloToolkit-Sharing-240 menu**.</span></span>
* <span data-ttu-id="1fa4c-234">ドロップダウンリストで [ **共有サービスの起動** ] 項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-234">Select the **Launch Sharing Service** item in the drop-down.</span></span>
* <span data-ttu-id="1fa4c-235">[ **プライベートネットワーク** ] オプションをオンにし、[ファイアウォールプロンプトが表示されたら **アクセスを許可** する] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-235">Check the **Private Network** option and click **Allow Access** when the firewall prompt appears.</span></span>
* <span data-ttu-id="1fa4c-236">共有サービスコンソールウィンドウに表示されている IPv4 アドレスをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-236">Note down the IPv4 address displayed in the Sharing Service console window.</span></span> <span data-ttu-id="1fa4c-237">これは、サービスが実行されているコンピューターと同じ IP です。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-237">This is the same IP as the machine the service is being run on.</span></span>

<span data-ttu-id="1fa4c-238">共有エクスペリエンスに参加するすべての **pc** で、残りの手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-238">Follow the rest of the instructions on **all PCs** that will join the shared experience.</span></span>

* <span data-ttu-id="1fa4c-239">**階層** で、**共有** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-239">In the **Hierarchy**, select the **Sharing** object.</span></span>
* <span data-ttu-id="1fa4c-240">**インスペクター** の [**共有ステージ**] コンポーネントで、**サーバーアドレス** を ' localhost ' から SharingService.exe を実行しているコンピューターの IPv4 アドレスに変更します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-240">In the **Inspector**, on the **Sharing Stage** component, change the **Server Address** from 'localhost' to the IPv4 address of the machine running SharingService.exe.</span></span>
* <span data-ttu-id="1fa4c-241">**階層** で、 **HologramCollection** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-241">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="1fa4c-242">**インスペクター** で [コンポーネントの **追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-242">In the **Inspector** click the **Add Component** button.</span></span>
* <span data-ttu-id="1fa4c-243">検索ボックスに、「 **Import Export Anchor Manager**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-243">In the search box, type **Import Export Anchor Manager**.</span></span> <span data-ttu-id="1fa4c-244">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-244">Select the search result.</span></span>
* <span data-ttu-id="1fa4c-245">[ **プロジェクト] パネル** で、 **Scripts** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-245">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="1fa4c-246">**HologramPlacement** スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-246">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="1fa4c-247">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-247">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the anchor model.
    /// The anchor model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    private bool animationPlayed = false;

    void Start()
    {
        // We care about getting updates for the anchor transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the anchor transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the anchor if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    void Update()
    {
        if (GotTransform)
        {
            if (ImportExportAnchorManager.Instance.AnchorEstablished &&
                animationPlayed == false)
            {
                // This triggers the animation sequence for the anchor model and 
                // puts the cool materials on the model.
                GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                animationPlayed = true;
            }
        }
        else
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the anchor 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the anchor to do its animation and
        // swap its materials.
        if (GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="1fa4c-248">Unity に戻り、[**階層] パネル** で [ **HologramCollection** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-248">Back in Unity, select the **HologramCollection** in the **Hierarchy panel**.</span></span>
* <span data-ttu-id="1fa4c-249">[ **インスペクター] パネル** で、[ **コンポーネントの追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-249">In the **Inspector panel** click the **Add Component** button.</span></span>
* <span data-ttu-id="1fa4c-250">メニューで、検索ボックスに「 **App State Manager**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-250">In the menu, type in the search box **App State Manager**.</span></span> <span data-ttu-id="1fa4c-251">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-251">Select the search result.</span></span>

<span data-ttu-id="1fa4c-252">**デプロイと活用**</span><span class="sxs-lookup"><span data-stu-id="1fa4c-252">**Deploy and enjoy**</span></span>

* <span data-ttu-id="1fa4c-253">HoloLens デバイス用のプロジェクトをビルドします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-253">Build the project for your HoloLens devices.</span></span>
* <span data-ttu-id="1fa4c-254">1つの HoloLens を最初に展開するように指定します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-254">Designate one HoloLens to deploy to first.</span></span> <span data-ttu-id="1fa4c-255">EnergyHub を配置する前に、アンカーがサービスにアップロードされるまで待機する必要があります (これには約30-60 秒かかることがあります)。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-255">You will need to wait for the Anchor to be uploaded to the service before you can place the EnergyHub (this can take ~30-60 seconds).</span></span> <span data-ttu-id="1fa4c-256">アップロードが完了するまで、タップジェスチャは無視されます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-256">Until the upload is done, your tap gestures will be ignored.</span></span>
* <span data-ttu-id="1fa4c-257">EnergyHub が配置されると、その場所がサービスにアップロードされ、他のすべての HoloLens デバイスに展開できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-257">After the EnergyHub has been placed, its location will be uploaded to the service and you can then deploy to all other HoloLens devices.</span></span>
* <span data-ttu-id="1fa4c-258">新しい HoloLens が最初にセッションに参加したときに、そのデバイスで EnergyHub の場所が正しくない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-258">When a new HoloLens first joins the session, the location of the EnergyHub may not be correct on that device.</span></span> <span data-ttu-id="1fa4c-259">ただし、アンカーと EnergyHub の場所がサービスからダウンロードされるとすぐに、EnergyHub は新しい共有の場所に移動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-259">However, as soon as the anchor and EnergyHub locations have been downloaded from the service, the EnergyHub should jump to the new, shared location.</span></span> <span data-ttu-id="1fa4c-260">これが約30-60 秒以内に行われない場合は、アンカーを設定して、より多くの環境の手掛かりを収集するときに、元の HoloLens がどこにあったかを説明します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-260">If this does not happen within ~30-60 seconds, walk to where the original HoloLens was when setting the anchor to gather more environment clues.</span></span> <span data-ttu-id="1fa4c-261">その場所がまだロックされていない場合は、デバイスに再デプロイします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-261">If the location still does not lock on, redeploy to the device.</span></span>
* <span data-ttu-id="1fa4c-262">デバイスの準備が完了し、アプリを実行している場合は、EnergyHub を探します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-262">When the devices are all ready and running the app, look for the EnergyHub.</span></span> <span data-ttu-id="1fa4c-263">ホログラムの場所とテキストがどの方向に接しているかについては、すべて同意できますか。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-263">Can you all agree on the hologram's location and which direction the text is facing?</span></span>

## <a name="chapter-4---discovery"></a><span data-ttu-id="1fa4c-264">Chapter 4-検出</span><span class="sxs-lookup"><span data-stu-id="1fa4c-264">Chapter 4 - Discovery</span></span>

>[!VIDEO https://www.youtube.com/embed/5NxJWMV4BP8]

<span data-ttu-id="1fa4c-265">全員が同じホログラムを見ることができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-265">Everyone can now see the same hologram!</span></span> <span data-ttu-id="1fa4c-266">それでは、共有 holographic 世界に接続されているすべてのユーザーを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-266">Now let's see everyone else connected to our shared holographic world.</span></span> <span data-ttu-id="1fa4c-267">この章では、同じ共有セッション内の他のすべての HoloLens デバイスの場所とローテーションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-267">In this chapter, we'll grab the head location and rotation of all other HoloLens devices in the same sharing session.</span></span>

### <a name="objectives"></a><span data-ttu-id="1fa4c-268">目標</span><span class="sxs-lookup"><span data-stu-id="1fa4c-268">Objectives</span></span>

* <span data-ttu-id="1fa4c-269">共有エクスペリエンスで互いを検出します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-269">Discover each other in our shared experience.</span></span>
* <span data-ttu-id="1fa4c-270">プレーヤーアバターを選択して共有します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-270">Choose and share a player avatar.</span></span>
* <span data-ttu-id="1fa4c-271">すべてのユーザーのヘッドの横に、プレーヤーアバターを添付します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-271">Attach the player avatar next to everyone's heads.</span></span>

### <a name="instructions"></a><span data-ttu-id="1fa4c-272">手順</span><span class="sxs-lookup"><span data-stu-id="1fa4c-272">Instructions</span></span>

* <span data-ttu-id="1fa4c-273">[ **プロジェクト] パネル** で、[ **ホログラム** ] フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-273">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="1fa4c-274">**PlayerAvatarStore** を **階層** にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-274">Drag and drop the **PlayerAvatarStore** into the **Hierarchy**.</span></span>
* <span data-ttu-id="1fa4c-275">[ **プロジェクト] パネル** で、 **Scripts** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-275">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="1fa4c-276">**AvatarSelector** スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-276">Double-click the **AvatarSelector** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="1fa4c-277">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-277">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Script to handle the user selecting the avatar.
/// </summary>
public class AvatarSelector : MonoBehaviour
{
    /// <summary>
    /// This is the index set by the PlayerAvatarStore for the avatar.
    /// </summary>
    public int AvatarIndex { get; set; }

    /// <summary>
    /// Called when the user is gazing at this avatar and air-taps it.
    /// This sends the user's selection to the rest of the devices in the experience.
    /// </summary>
    void OnSelect()
    {
        PlayerAvatarStore.Instance.DismissAvatarPicker();

        LocalPlayerManager.Instance.SetUserAvatar(AvatarIndex);
    }

    void Start()
    {
        // Add Billboard component so the avatar always faces the user.
        Billboard billboard = gameObject.GetComponent<Billboard>();
        if (billboard == null)
        {
            billboard = gameObject.AddComponent<Billboard>();
        }

        // Lock rotation along the Y axis.
        billboard.PivotAxis = PivotAxis.Y;
    }
}
```

* <span data-ttu-id="1fa4c-278">**階層** で、 **HologramCollection** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-278">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="1fa4c-279">**インスペクター** で [**コンポーネントの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-279">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="1fa4c-280">検索ボックスに、「 **Local Player Manager**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-280">In the search box, type **Local Player Manager**.</span></span> <span data-ttu-id="1fa4c-281">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-281">Select the search result.</span></span>
* <span data-ttu-id="1fa4c-282">**階層** で、 **HologramCollection** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-282">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="1fa4c-283">**インスペクター** で [**コンポーネントの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-283">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="1fa4c-284">検索ボックスに、「 **リモートプレーヤーマネージャー**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-284">In the search box, type **Remote Player Manager**.</span></span> <span data-ttu-id="1fa4c-285">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-285">Select the search result.</span></span>
* <span data-ttu-id="1fa4c-286">Visual Studio で **HologramPlacement** スクリプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-286">Open the **HologramPlacement** script in Visual Studio.</span></span>
* <span data-ttu-id="1fa4c-287">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-287">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        // Put the model 2m in front of the user.
        Vector3 retval = Camera.main.transform.position + Camera.main.transform.forward * 2;

        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    public void ResetStage()
    {
        // We'll use this later.
    }
}
```

* <span data-ttu-id="1fa4c-288">Visual Studio で **AppStateManager** スクリプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-288">Open the **AppStateManager** script in Visual Studio.</span></span>
* <span data-ttu-id="1fa4c-289">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-289">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        WaitingForAnchor,
        WaitingForStageTransform,
        PickingAvatar,
        Ready
    }

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // We start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = null;
                }
                break;
        }
    }
}
```

<span data-ttu-id="1fa4c-290">**デプロイと活用**</span><span class="sxs-lookup"><span data-stu-id="1fa4c-290">**Deploy and Enjoy**</span></span>

* <span data-ttu-id="1fa4c-291">プロジェクトをビルドし、HoloLens デバイスにデプロイします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-291">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="1fa4c-292">Ping 音が聞こえたら、アバター選択メニューを見つけて、エアタップジェスチャでアバターを選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-292">When you hear a pinging sound, find the avatar selection menu and select an avatar with the air-tap gesture.</span></span>
* <span data-ttu-id="1fa4c-293">ホログラムを見ていない場合、カーソルの周囲のポイントライトは、HoloLens がサービスと通信しているときに、(濃い紫の) 初期化、アンカーのダウンロード (緑)、位置データのインポート/エクスポート (黄色)、アンカーのアップロード (青) で異なる色になります。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-293">If you're not looking at any holograms, the point light around your cursor will turn a different color when your HoloLens is communicating with the service: initializing (dark purple), downloading the anchor (green), importing/exporting location data (yellow), uploading the anchor (blue).</span></span> <span data-ttu-id="1fa4c-294">カーソルの周囲のポイントライトが既定の色 (淡い紫) の場合は、セッション内の他のプレーヤーと対話する準備ができています。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-294">If your point light around your cursor is the default color (light purple), then you are ready to interact with other players in your session!</span></span>
* <span data-ttu-id="1fa4c-295">スペースに接続されている他のユーザーを確認します。 holographic ロボットはショルダーの上にフローティングし、頭の動きを模倣しています。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-295">Look at other people connected to your space - there will be a holographic robot floating above their shoulder and mimicking their head motions!</span></span>

## <a name="chapter-5---placement"></a><span data-ttu-id="1fa4c-296">章 5: 配置</span><span class="sxs-lookup"><span data-stu-id="1fa4c-296">Chapter 5 - Placement</span></span>

>[!VIDEO https://www.youtube.com/embed/afFTwHQIw0s]

<span data-ttu-id="1fa4c-297">この章では、アンカーを実際のサーフェイスに配置できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-297">In this chapter, we'll make the anchor able to be placed on real-world surfaces.</span></span> <span data-ttu-id="1fa4c-298">共有座標を使用して、共有エクスペリエンスに接続されているすべてのユーザー間の中間点にアンカーを配置します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-298">We'll use shared coordinates to place that anchor in the middle point between everyone connected to the shared experience.</span></span>

### <a name="objectives"></a><span data-ttu-id="1fa4c-299">目標</span><span class="sxs-lookup"><span data-stu-id="1fa4c-299">Objectives</span></span>

* <span data-ttu-id="1fa4c-300">プレーヤーのヘッド位置に基づいて、空間マッピングメッシュにホログラムを配置します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-300">Place holograms on the spatial mapping mesh based on players’ head position.</span></span>

### <a name="instructions"></a><span data-ttu-id="1fa4c-301">手順</span><span class="sxs-lookup"><span data-stu-id="1fa4c-301">Instructions</span></span>

* <span data-ttu-id="1fa4c-302">[ **プロジェクト] パネル** で、[ **ホログラム** ] フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-302">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="1fa4c-303">**CustomSpatialMapping** Prefab を **階層** にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-303">Drag and drop the **CustomSpatialMapping** prefab onto the **Hierarchy**.</span></span>
* <span data-ttu-id="1fa4c-304">[ **プロジェクト] パネル** で、 **Scripts** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-304">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="1fa4c-305">**AppStateManager** スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-305">Double-click the **AppStateManager** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="1fa4c-306">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-306">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using Academy.HoloToolkit.Unity;

/// <summary>
/// Keeps track of the current state of the experience.
/// </summary>
public class AppStateManager : Singleton<AppStateManager>
{
    /// <summary>
    /// Enum to track progress through the experience.
    /// </summary>
    public enum AppState
    {
        Starting = 0,
        PickingAvatar,
        WaitingForAnchor,
        WaitingForStageTransform,
        Ready
    }

    // The object to call to make a projectile.
    GameObject shootHandler = null;

    /// <summary>
    /// Tracks the current state in the experience.
    /// </summary>
    public AppState CurrentAppState { get; set; }

    void Start()
    {
        // The shootHandler shoots projectiles.
        if (GetComponent<ProjectileLauncher>() != null)
        {
            shootHandler = GetComponent<ProjectileLauncher>().gameObject;
        }

        // We start in the 'picking avatar' mode.
        CurrentAppState = AppState.PickingAvatar;

        // Spatial mapping should be disabled when we start up so as not
        // to distract from the avatar picking.
        SpatialMappingManager.Instance.StopObserver();
        SpatialMappingManager.Instance.gameObject.SetActive(false);

        // On device we start by showing the avatar picker.
        PlayerAvatarStore.Instance.SpawnAvatarPicker();
    }

    public void ResetStage()
    {
        // If we fall back to waiting for anchor, everything needed to
        // get us into setting the target transform state will be setup.
        if (CurrentAppState != AppState.PickingAvatar)
        {
            CurrentAppState = AppState.WaitingForAnchor;
        }

        // Reset the underworld.
        if (UnderworldBase.Instance)
        {
            UnderworldBase.Instance.ResetUnderworld();
        }
    }

    void Update()
    {
        switch (CurrentAppState)
        {
            case AppState.PickingAvatar:
                // Avatar picking is done when the avatar picker has been dismissed.
                if (PlayerAvatarStore.Instance.PickerActive == false)
                {
                    CurrentAppState = AppState.WaitingForAnchor;
                }
                break;
            case AppState.WaitingForAnchor:
                // Once the anchor is established we need to run spatial mapping for a
                // little while to build up some meshes.
                if (ImportExportAnchorManager.Instance.AnchorEstablished)
                {
                    CurrentAppState = AppState.WaitingForStageTransform;
                    GestureManager.Instance.OverrideFocusedObject = HologramPlacement.Instance.gameObject;

                    SpatialMappingManager.Instance.gameObject.SetActive(true);
                    SpatialMappingManager.Instance.DrawVisualMeshes = true;
                    SpatialMappingDeformation.Instance.ResetGlobalRendering();
                    SpatialMappingManager.Instance.StartObserver();
                }
                break;
            case AppState.WaitingForStageTransform:
                // Now if we have the stage transform we are ready to go.
                if (HologramPlacement.Instance.GotTransform)
                {
                    CurrentAppState = AppState.Ready;
                    GestureManager.Instance.OverrideFocusedObject = shootHandler;
                }
                break;
        }
    }
}
```

* <span data-ttu-id="1fa4c-307">[ **プロジェクト] パネル** で、 **Scripts** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-307">In the **Project panel** navigate to the **Scripts** folder.</span></span>
* <span data-ttu-id="1fa4c-308">**HologramPlacement** スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-308">Double-click the **HologramPlacement** script to open it in Visual Studio.</span></span>
* <span data-ttu-id="1fa4c-309">内容を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-309">Replace the contents with the code below.</span></span>

```cs
using UnityEngine;
using System.Collections.Generic;
using UnityEngine.Windows.Speech;
using Academy.HoloToolkit.Unity;
using Academy.HoloToolkit.Sharing;

public class HologramPlacement : Singleton<HologramPlacement>
{
    /// <summary>
    /// Tracks if we have been sent a transform for the model.
    /// The model is rendered relative to the actual anchor.
    /// </summary>
    public bool GotTransform { get; private set; }

    /// <summary>
    /// When the experience starts, we disable all of the rendering of the model.
    /// </summary>
    List<MeshRenderer> disabledRenderers = new List<MeshRenderer>();

    /// <summary>
    /// We use a voice command to enable moving the target.
    /// </summary>
    KeywordRecognizer keywordRecognizer;

    void Start()
    {
        // When we first start, we need to disable the model to avoid it obstructing the user picking a hat.
        DisableModel();

        // We care about getting updates for the model transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.StageTransform] = this.OnStageTransform;

        // And when a new user join we will send the model transform we have.
        SharingSessionTracker.Instance.SessionJoined += Instance_SessionJoined;

        // And if the users want to reset the stage transform.
        CustomMessages.Instance.MessageHandlers[CustomMessages.TestMessageID.ResetStage] = this.OnResetStage;

        // Setup a keyword recognizer to enable resetting the target location.
        List<string> keywords = new List<string>();
        keywords.Add("Reset Target");
        keywordRecognizer = new KeywordRecognizer(keywords.ToArray());
        keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
        keywordRecognizer.Start();
    }

    /// <summary>
    /// When the keyword recognizer hears a command this will be called.  
    /// In this case we only have one keyword, which will re-enable moving the
    /// target.
    /// </summary>
    /// <param name="args">information to help route the voice command.</param>
    private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
    {
        ResetStage();
    }

    /// <summary>
    /// Resets the stage transform, so users can place the target again.
    /// </summary>
    public void ResetStage()
    {
        GotTransform = false;

        // AppStateManager needs to know about this so that
        // the right objects get input routed to them.
        AppStateManager.Instance.ResetStage();

        // Other devices in the experience need to know about this as well.
        CustomMessages.Instance.SendResetStage();

        // And we need to reset the object to its start animation state.
        GetComponent<EnergyHubBase>().ResetAnimation();
    }

    /// <summary>
    /// When a new user joins we want to send them the relative transform for the model if we have it.
    /// </summary>
    /// <param name="sender"></param>
    /// <param name="e"></param>
    private void Instance_SessionJoined(object sender, SharingSessionTracker.SessionJoinedEventArgs e)
    {
        if (GotTransform)
        {
            CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
        }
    }

    /// <summary>
    /// Turns off all renderers for the model.
    /// </summary>
    void DisableModel()
    {
        foreach (MeshRenderer renderer in gameObject.GetComponentsInChildren<MeshRenderer>())
        {
            if (renderer.enabled)
            {
                renderer.enabled = false;
                disabledRenderers.Add(renderer);
            }
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = false;
        }
    }

    /// <summary>
    /// Turns on all renderers that were disabled.
    /// </summary>
    void EnableModel()
    {
        foreach (MeshRenderer renderer in disabledRenderers)
        {
            renderer.enabled = true;
        }

        foreach (MeshCollider collider in gameObject.GetComponentsInChildren<MeshCollider>())
        {
            collider.enabled = true;
        }

        disabledRenderers.Clear();
    }


    void Update()
    {
        // Wait till users pick an avatar to enable renderers.
        if (disabledRenderers.Count > 0)
        {
            if (!PlayerAvatarStore.Instance.PickerActive &&
            ImportExportAnchorManager.Instance.AnchorEstablished)
            {
                // After which we want to start rendering.
                EnableModel();

                // And if we've already been sent the relative transform, we will use it.
                if (GotTransform)
                {
                    // This triggers the animation sequence for the model and
                    // puts the cool materials on the model.
                    GetComponent<EnergyHubBase>().SendMessage("OnSelect");
                }
            }
        }
        else if (GotTransform == false)
        {
            transform.position = Vector3.Lerp(transform.position, ProposeTransformPosition(), 0.2f);
        }
    }

    Vector3 ProposeTransformPosition()
    {
        Vector3 retval;
        // We need to know how many users are in the experience with good transforms.
        Vector3 cumulatedPosition = Camera.main.transform.position;
        int playerCount = 1;
        foreach (RemotePlayerManager.RemoteHeadInfo remoteHead in RemotePlayerManager.Instance.remoteHeadInfos)
        {
            if (remoteHead.Anchored && remoteHead.Active)
            {
                playerCount++;
                cumulatedPosition += remoteHead.HeadObject.transform.position;
            }
        }

        // If we have more than one player ...
        if (playerCount > 1)
        {
            // Put the transform in between the players.
            retval = cumulatedPosition / playerCount;
            RaycastHit hitInfo;

            // And try to put the transform on a surface below the midpoint of the players.
            if (Physics.Raycast(retval, Vector3.down, out hitInfo, 5, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
        }
        // If we are the only player, have the model act as the 'cursor' ...
        else
        {
            // We prefer to put the model on a real world surface.
            RaycastHit hitInfo;

            if (Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, 30, SpatialMappingManager.Instance.LayerMask))
            {
                retval = hitInfo.point;
            }
            else
            {
                // But if we don't have a ray that intersects the real world, just put the model 2m in
                // front of the user.
                retval = Camera.main.transform.position + Camera.main.transform.forward * 2;
            }
        }
        return retval;
    }

    public void OnSelect()
    {
        // Note that we have a transform.
        GotTransform = true;

        // And send it to our friends.
        CustomMessages.Instance.SendStageTransform(transform.localPosition, transform.localRotation);
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    /// <param name="msg"></param>
    void OnStageTransform(NetworkInMessage msg)
    {
        // We read the user ID but we don't use it here.
        msg.ReadInt64();

        transform.localPosition = CustomMessages.Instance.ReadVector3(msg);
        transform.localRotation = CustomMessages.Instance.ReadQuaternion(msg);

        // The first time, we'll want to send the message to the model to do its animation and
        // swap its materials.
        if (disabledRenderers.Count == 0 && GotTransform == false)
        {
            GetComponent<EnergyHubBase>().SendMessage("OnSelect");
        }

        GotTransform = true;
    }

    /// <summary>
    /// When a remote system has a transform for us, we'll get it here.
    /// </summary>
    void OnResetStage(NetworkInMessage msg)
    {
        GotTransform = false;

        GetComponent<EnergyHubBase>().ResetAnimation();
        AppStateManager.Instance.ResetStage();
    }
}
```

<span data-ttu-id="1fa4c-310">**デプロイと活用**</span><span class="sxs-lookup"><span data-stu-id="1fa4c-310">**Deploy and enjoy**</span></span>

* <span data-ttu-id="1fa4c-311">プロジェクトをビルドし、HoloLens デバイスにデプロイします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-311">Build and deploy the project to your HoloLens devices.</span></span>
* <span data-ttu-id="1fa4c-312">アプリの準備が整ったら、サークルに EnergyHub て、すべてのユーザーの中央に表示されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-312">When the app is ready, stand in a circle and notice how the EnergyHub appears in the center of everyone.</span></span>
* <span data-ttu-id="1fa4c-313">タップして、EnergyHub を配置します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-313">Tap to place the EnergyHub.</span></span>
* <span data-ttu-id="1fa4c-314">音声コマンド ' Reset Target ' を使用して EnergyHub バックアップを選択し、グループとして連携して、ホログラムを新しい場所に移動してみてください。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-314">Try the voice command 'Reset Target' to pick the EnergyHub back up and work together as a group to move the hologram to a new location.</span></span>

## <a name="chapter-6---real-world-physics"></a><span data-ttu-id="1fa4c-315">第6章-Real-World の物理</span><span class="sxs-lookup"><span data-stu-id="1fa4c-315">Chapter 6 - Real-World Physics</span></span>

>[!VIDEO https://www.youtube.com/embed/XNpQVSyXwMo]

<span data-ttu-id="1fa4c-316">この章では、現実世界の表面にバウンスするホログラムを追加します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-316">In this chapter we'll add holograms that bounce off real-world surfaces.</span></span> <span data-ttu-id="1fa4c-317">自分と友人の両方によって起動されたプロジェクトで、スペースを埋めることができます。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-317">Watch your space fill up with projects launched by both you and your friends!</span></span>

### <a name="objectives"></a><span data-ttu-id="1fa4c-318">目標</span><span class="sxs-lookup"><span data-stu-id="1fa4c-318">Objectives</span></span>

* <span data-ttu-id="1fa4c-319">現実世界の表面にバウンドする projectiles を起動します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-319">Launch projectiles that bounce off real-world surfaces.</span></span>
* <span data-ttu-id="1fa4c-320">他のプレーヤーが見ることができるように、projectiles を共有します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-320">Share the projectiles so other players can see them.</span></span>

### <a name="instructions"></a><span data-ttu-id="1fa4c-321">手順</span><span class="sxs-lookup"><span data-stu-id="1fa4c-321">Instructions</span></span>

* <span data-ttu-id="1fa4c-322">**階層** で、 **HologramCollection** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-322">In the **Hierarchy** select the **HologramCollection** object.</span></span>
* <span data-ttu-id="1fa4c-323">**インスペクター** で [**コンポーネントの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-323">In the **Inspector** click **Add Component**.</span></span>
* <span data-ttu-id="1fa4c-324">[検索] ボックスに、「"" の種類の表示 **ツール**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-324">In the search box, type **Projectile Launcher**.</span></span> <span data-ttu-id="1fa4c-325">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-325">Select the search result.</span></span>

<span data-ttu-id="1fa4c-326">**デプロイと活用**</span><span class="sxs-lookup"><span data-stu-id="1fa4c-326">**Deploy and enjoy**</span></span>

* <span data-ttu-id="1fa4c-327">HoloLens デバイスにビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-327">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="1fa4c-328">アプリがすべてのデバイスで実行されている場合は、エアタップを実行して、実世界のサーフェイスで航空タイルを起動します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-328">When the app is running on all devices, perform an air-tap to launch projectile at real world surfaces.</span></span>
* <span data-ttu-id="1fa4c-329">他のプレーヤーのアバターと競合している場合はどうなるかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-329">See what happens when your projectile collides with another player's avatar!</span></span>

## <a name="chapter-7---grand-finale"></a><span data-ttu-id="1fa4c-330">第7章-グランドくくり</span><span class="sxs-lookup"><span data-stu-id="1fa4c-330">Chapter 7 - Grand Finale</span></span>

>[!VIDEO https://www.youtube.com/embed/kDUPUvZEqRg]

<span data-ttu-id="1fa4c-331">この章では、コラボレーションによってのみ検出できるポータルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-331">In this chapter, we'll uncover a portal that can only be discovered with collaboration.</span></span>

### <a name="objectives"></a><span data-ttu-id="1fa4c-332">目標</span><span class="sxs-lookup"><span data-stu-id="1fa4c-332">Objectives</span></span>

* <span data-ttu-id="1fa4c-333">連携して、秘密ポータルを見つけるために十分な projectiles をアンカーで立ち上げましょう。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-333">Work together to launch enough projectiles at the anchor to uncover a secret portal!</span></span>

### <a name="instructions"></a><span data-ttu-id="1fa4c-334">手順</span><span class="sxs-lookup"><span data-stu-id="1fa4c-334">Instructions</span></span>

* <span data-ttu-id="1fa4c-335">[ **プロジェクト] パネル** で、[ **ホログラム** ] フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-335">In the **Project panel** navigate to the **Holograms** folder.</span></span>
* <span data-ttu-id="1fa4c-336">**HologramCollection の子** として、**黄泉** の資産をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-336">Drag and drop the **Underworld** asset as a **child of HologramCollection**.</span></span>
* <span data-ttu-id="1fa4c-337">**HologramCollection** を選択した状態で、**インスペクター** の [**コンポーネントの追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-337">With **HologramCollection** selected, click the **Add Component** button in the **Inspector**.</span></span>
* <span data-ttu-id="1fa4c-338">メニューで、検索ボックスに「 **ExplodeTarget**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-338">In the menu, type in the search box **ExplodeTarget**.</span></span> <span data-ttu-id="1fa4c-339">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-339">Select the search result.</span></span>
* <span data-ttu-id="1fa4c-340">**HologramCollection** を選択した状態で、**階層** から、 **EnergyHub** オブジェクトを **インスペクター** の [**ターゲット**] フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-340">With **HologramCollection** selected, from the **Hierarchy** drag the **EnergyHub** object to the **Target** field in the **Inspector**.</span></span>
* <span data-ttu-id="1fa4c-341">**HologramCollection** を選択した状態で、**階層** から、**黄泉** のオブジェクトを **インスペクター** の [**黄泉**] フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-341">With **HologramCollection** selected, from the **Hierarchy** drag the **Underworld** object to the **Underworld** field in the **Inspector**.</span></span>

<span data-ttu-id="1fa4c-342">**デプロイと活用**</span><span class="sxs-lookup"><span data-stu-id="1fa4c-342">**Deploy and enjoy**</span></span>

* <span data-ttu-id="1fa4c-343">HoloLens デバイスにビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-343">Build and deploy to your HoloLens devices.</span></span>
* <span data-ttu-id="1fa4c-344">アプリが起動したら、共同作業を行って、EnergyHub で projectiles を起動します。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-344">When the app has launched, collaborate together to launch projectiles at the EnergyHub.</span></span>
* <span data-ttu-id="1fa4c-345">黄泉の場所にいる場合は、黄泉のロボットロボットで projectiles を起動します (特別に楽しいようにロボットを3回押します)。</span><span class="sxs-lookup"><span data-stu-id="1fa4c-345">When the underworld appears, launch projectiles at underworld robots (hit a robot three times for extra fun).</span></span>