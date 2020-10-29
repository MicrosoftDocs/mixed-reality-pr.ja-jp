---
title: MR 入力 210-宝石
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、宝石の概念の詳細を学習してください。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、academy、チュートリアル、宝石
ms.openlocfilehash: b513d304e78d51b447f0bbba4990fb7df0556707
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686450"
---
# <a name="mr-input-210-gaze"></a><span data-ttu-id="57bbc-104">MR 入力 210:視線入力</span><span class="sxs-lookup"><span data-stu-id="57bbc-104">MR Input 210: Gaze</span></span>

>[!NOTE]
><span data-ttu-id="57bbc-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="57bbc-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="57bbc-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="57bbc-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="57bbc-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。</span><span class="sxs-lookup"><span data-stu-id="57bbc-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="57bbc-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="57bbc-109">HoloLens 2 向けには、[新しいチュートリアル シリーズ](../../../mr-learning-base-01.md)が投稿されています。</span><span class="sxs-lookup"><span data-stu-id="57bbc-109">[A new series of tutorials](../../../mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="57bbc-110">[見つめ](../../../design/gaze-and-commit.md) は入力の最初の形式であり、ユーザーの意図と認識を明らかにします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-110">[Gaze](../../../design/gaze-and-commit.md) is the first form of input and reveals the user's intent and awareness.</span></span> <span data-ttu-id="57bbc-111">MR 入力 210 (プロジェクトエクスプローラーとも呼ばれます) は、Windows Mixed Reality 向けの、宝石に関連する概念について詳しく説明しています。</span><span class="sxs-lookup"><span data-stu-id="57bbc-111">MR Input 210 (aka Project Explorer) is a deep dive into gaze-related concepts for Windows Mixed Reality.</span></span> <span data-ttu-id="57bbc-112">私たちは、カーソルとホログラムにコンテキスト認識を追加し、アプリがユーザーの宝石について認識していることを最大限に活用します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-112">We will be adding contextual awareness to our cursor and holograms, taking full advantage of what your app knows about the user's gaze.</span></span>

>[!VIDEO https://www.youtube.com/embed/yKAttGduVp0]

<span data-ttu-id="57bbc-113">ここでは、宝石の概念を理解するのに役立つわかりやすい astronaut を用意しています。</span><span class="sxs-lookup"><span data-stu-id="57bbc-113">We have a friendly astronaut here to help you learn gaze concepts.</span></span> <span data-ttu-id="57bbc-114">[MR 基本 101](../../../develop/unity/tutorials/holograms-101.md)では、簡単なカーソルを使用して、宝石を見つめます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-114">In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), we had a simple cursor that just followed your gaze.</span></span> <span data-ttu-id="57bbc-115">現在、単純なカーソルを超えてステップを移動しています。</span><span class="sxs-lookup"><span data-stu-id="57bbc-115">Today we're moving a step beyond the simple cursor:</span></span>

* <span data-ttu-id="57bbc-116">カーソルとホログラムを見つめています。どちらも、ユーザーが探している場所またはユーザーが探し *ていない* 場所に基づいて変化します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-116">We're making the cursor and our holograms gaze-aware: both will change based on where the user is looking - or where the user is *not* looking.</span></span> <span data-ttu-id="57bbc-117">これにより、コンテキスト対応になります。</span><span class="sxs-lookup"><span data-stu-id="57bbc-117">This makes them context-aware.</span></span>
* <span data-ttu-id="57bbc-118">カーソルとホログラムにフィードバックを追加して、対象となっている内容についてユーザーにより多くのコンテキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-118">We will add feedback to our cursor and holograms to give the user more context on what is being targeted.</span></span> <span data-ttu-id="57bbc-119">このフィードバックは、オーディオとビジュアルにすることができます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-119">This feedback can be audio and visual.</span></span>
* <span data-ttu-id="57bbc-120">ここでは、ユーザーがより小さなターゲットをヒットするのを支援するための手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-120">We'll show you targeting techniques to help users hit smaller targets.</span></span>
* <span data-ttu-id="57bbc-121">方向性のあるインジケーターを使用して、ユーザーの注意をホログラムに描画する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-121">We'll show you how to draw the user's attention to your holograms with a directional indicator.</span></span>
* <span data-ttu-id="57bbc-122">ここでは、ユーザーが世界中に移動するときに、ホログラムを使用する手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-122">We'll teach you techniques to take your holograms with the user as she moves around in your world.</span></span>

>[!IMPORTANT]
><span data-ttu-id="57bbc-123">以下の各章に埋め込まれているビデオは、古いバージョンの Unity と Mixed Reality Toolkit を使用して記録されています。</span><span class="sxs-lookup"><span data-stu-id="57bbc-123">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="57bbc-124">ステップバイステップの手順は正確であり、最新のものですが、最新ではない対応するビデオにスクリプトとビジュアルが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="57bbc-124">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="57bbc-125">ビデオはために含まれています。ここで説明する概念は引き続き適用されます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-125">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="57bbc-126">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="57bbc-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="57bbc-127">コース</span><span class="sxs-lookup"><span data-stu-id="57bbc-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="57bbc-128"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="57bbc-128"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="57bbc-129"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="57bbc-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="57bbc-130">MR 入力 210:視線入力</span><span class="sxs-lookup"><span data-stu-id="57bbc-130">MR Input 210: Gaze</span></span></td><td style="text-align: center;"> <span data-ttu-id="57bbc-131">✔️</span><span class="sxs-lookup"><span data-stu-id="57bbc-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="57bbc-132">✔️</span><span class="sxs-lookup"><span data-stu-id="57bbc-132">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="57bbc-133">開始する前に</span><span class="sxs-lookup"><span data-stu-id="57bbc-133">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="57bbc-134">前提条件</span><span class="sxs-lookup"><span data-stu-id="57bbc-134">Prerequisites</span></span>

* <span data-ttu-id="57bbc-135">適切な [ツールがインストール](../../../develop/install-the-tools.md)された WINDOWS 10 PC。</span><span class="sxs-lookup"><span data-stu-id="57bbc-135">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="57bbc-136">基本的な C# プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="57bbc-136">Some basic C# programming ability.</span></span>
* <span data-ttu-id="57bbc-137">[MR の基本 101](../../../develop/unity/tutorials/holograms-101.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="57bbc-137">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="57bbc-138">[開発用に構成され](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)た HoloLens デバイス。</span><span class="sxs-lookup"><span data-stu-id="57bbc-138">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="57bbc-139">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="57bbc-139">Project files</span></span>

* <span data-ttu-id="57bbc-140">プロジェクトに必要な [ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-140">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-210-Gaze.zip) required by the project.</span></span> <span data-ttu-id="57bbc-141">Unity 2017.2 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="57bbc-141">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="57bbc-142">ファイルをデスクトップまたはその他の簡単な場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-142">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="57bbc-143">ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze)ます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-143">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="57bbc-144">エラッタとメモ</span><span class="sxs-lookup"><span data-stu-id="57bbc-144">Errata and Notes</span></span>

* <span data-ttu-id="57bbc-145">Visual Studio で、コード内のブレークポイントにヒットするには、[ツール]-[>オプション] >-[デバッグ] の下にある [マイコードのみ] を無効 (オフ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="57bbc-145">In Visual Studio, "Just My Code" needs to be disabled (unchecked) under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-1---unity-setup"></a><span data-ttu-id="57bbc-146">章 1-Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="57bbc-146">Chapter 1 - Unity Setup</span></span>

>[!VIDEO https://www.youtube.com/embed/_Ccn6riQ6vU]

### <a name="objectives"></a><span data-ttu-id="57bbc-147">目標</span><span class="sxs-lookup"><span data-stu-id="57bbc-147">Objectives</span></span>

* <span data-ttu-id="57bbc-148">HoloLens 用 Unity の開発を最適化する。</span><span class="sxs-lookup"><span data-stu-id="57bbc-148">Optimize Unity for HoloLens development.</span></span>
* <span data-ttu-id="57bbc-149">アセットをインポートし、シーンをセットアップする。</span><span class="sxs-lookup"><span data-stu-id="57bbc-149">Import assets and setup the scene.</span></span>
* <span data-ttu-id="57bbc-150">HoloLens で astronaut を表示します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-150">View the astronaut in the HoloLens.</span></span>

### <a name="instructions"></a><span data-ttu-id="57bbc-151">Instructions</span><span class="sxs-lookup"><span data-stu-id="57bbc-151">Instructions</span></span>

1. <span data-ttu-id="57bbc-152">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-152">Start Unity.</span></span>
2. <span data-ttu-id="57bbc-153">[ **新しいプロジェクト** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-153">Select **New Project** .</span></span>
3. <span data-ttu-id="57bbc-154">プロジェクトに **Modelexplorer** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-154">Name the project **ModelExplorer** .</span></span>
4. <span data-ttu-id="57bbc-155">以前にアーカイブしていない、場所を **見つめ** フォルダーとして入力します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-155">Enter location as the **Gaze** folder you previously un-archived.</span></span>
5. <span data-ttu-id="57bbc-156">プロジェクトが **[3D]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-156">Make sure the project is set to **3D** .</span></span>
6. <span data-ttu-id="57bbc-157">[ **プロジェクトの作成** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-157">Click **Create Project** .</span></span>

### <a name="unity-settings-for-hololens"></a><span data-ttu-id="57bbc-158">HoloLens の Unity 設定</span><span class="sxs-lookup"><span data-stu-id="57bbc-158">Unity settings for HoloLens</span></span>

<span data-ttu-id="57bbc-159">エクスポートしようとしているアプリが2D ビューではなく [イマーシブビュー](../../../design/app-views.md) を作成する必要があることを Unity に知らせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="57bbc-159">We need to let Unity know that the app we are trying to export should create an [immersive view](../../../design/app-views.md) instead of a 2D view.</span></span> <span data-ttu-id="57bbc-160">これを行うには、HoloLens を仮想現実デバイスとして追加します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-160">We do that by adding HoloLens as a virtual reality device.</span></span>

1. <span data-ttu-id="57bbc-161">[ **Edit > Project Settings > Player** ] にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-161">Go to **Edit > Project Settings > Player** .</span></span>
2. <span data-ttu-id="57bbc-162">[プレーヤー設定] の [ **インスペクター] パネル** で、[ **Windows ストア** ] アイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-162">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="57bbc-163">**[XR Settings]\(XR 設定\)** グループを展開します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-163">Expand the **XR Settings** group.</span></span>
4. <span data-ttu-id="57bbc-164">**[Rendering]\(レンダリング\)** セクションで、 **[Virtual Reality Supported]\(バーチャル リアリティ サポート\)** チェック ボックスをオンにして、新しい **バーチャル リアリティ SDK** の一覧を追加します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-164">In the **Rendering** section, check the **Virtual Reality Supported** checkbox to add a new **Virtual Reality SDKs** list.</span></span>
5. <span data-ttu-id="57bbc-165">**[Windows Mixed Reality]** が一覧に表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-165">Verify that **Windows Mixed Reality** appears in the list.</span></span> <span data-ttu-id="57bbc-166">表示されていない場合は、 **+** 一覧の下部にあるボタンを選択し、[ **Windows Holographic** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-166">If not, select the **+** button at the bottom of the list and choose **Windows Holographic** .</span></span>

<span data-ttu-id="57bbc-167">次に、スクリプトバックエンドを .NET に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57bbc-167">Next, we need to set our scripting backend to .NET.</span></span>

1. <span data-ttu-id="57bbc-168">[ **Edit > Project Settings > Player** (これは前の手順のままである場合があります) に進みます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-168">Go to **Edit > Project Settings > Player** (you may still have this up from the previous step).</span></span>
2. <span data-ttu-id="57bbc-169">[プレーヤー設定] の [ **インスペクター] パネル** で、[ **Windows ストア** ] アイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-169">In the **Inspector Panel** for Player Settings, select the **Windows Store** icon.</span></span>
3. <span data-ttu-id="57bbc-170">[ **その他の設定** ] 構成セクションで、[ **スクリプトバックエンド** ] が [ **.net** ] に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-170">In the **Other Settings** Configuration section, make sure that **Scripting Backend** is set to **.NET**</span></span>

<span data-ttu-id="57bbc-171">最後に、HoloLens で高速なパフォーマンスを実現するために品質設定を更新します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-171">Finally, we'll update our quality settings to achieve a fast performance on HoloLens.</span></span>

1. <span data-ttu-id="57bbc-172">[編集] [ **> プロジェクトの設定** ] [品質] > にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-172">Go to **Edit > Project Settings > Quality** .</span></span>
2. <span data-ttu-id="57bbc-173">Windows ストアアイコンの下の **既定** の行で、下向き矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-173">Click on downward pointing arrow in the **Default** row under the Windows Store icon.</span></span>
3. <span data-ttu-id="57bbc-174">**Windows ストアアプリ** の場合は [ **低** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-174">Select **Very Low** for **Windows Store Apps** .</span></span>

### <a name="import-project-assets"></a><span data-ttu-id="57bbc-175">プロジェクト資産のインポート</span><span class="sxs-lookup"><span data-stu-id="57bbc-175">Import project assets</span></span>

1. <span data-ttu-id="57bbc-176">[ **プロジェクト** ] パネルの [ **アセット** ] フォルダーを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-176">Right click the **Assets** folder in the **Project** panel.</span></span>
2. <span data-ttu-id="57bbc-177">[ **パッケージのインポート > カスタムパッケージ** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-177">Click on **Import Package > Custom Package** .</span></span>
3. <span data-ttu-id="57bbc-178">ダウンロードしたプロジェクトファイルに移動し、 **Modelexplorer. unitypackage** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-178">Navigate to the project files you downloaded and click on **ModelExplorer.unitypackage** .</span></span>
4. <span data-ttu-id="57bbc-179">**[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-179">Click **Open** .</span></span>
5. <span data-ttu-id="57bbc-180">パッケージが読み込まれたら、[ **インポート** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-180">After the package loads, click on the **Import** button.</span></span>

### <a name="setup-the-scene"></a><span data-ttu-id="57bbc-181">シーンを設定する</span><span class="sxs-lookup"><span data-stu-id="57bbc-181">Setup the scene</span></span>

1. <span data-ttu-id="57bbc-182">階層で、 **メインカメラ** を削除します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-182">In the Hierarchy, delete the **Main Camera** .</span></span>
2. <span data-ttu-id="57bbc-183">**HoloToolkit** フォルダーで、 **Input** フォルダーを開き、 **Prefabs** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-183">In the **HoloToolkit** folder, open the **Input** folder, then open the **Prefabs** folder.</span></span>
3. <span data-ttu-id="57bbc-184">**MixedRealityCameraParent** Prefab を **Prefabs** フォルダーから **階層** にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-184">Drag and drop the **MixedRealityCameraParent** prefab from the **Prefabs** folder into the **Hierarchy** .</span></span>
4. <span data-ttu-id="57bbc-185">階層内の **指向性ライト** を右クリックし、[ **削除** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-185">Right-click the **Directional Light** in the Hierarchy and select **Delete** .</span></span>
5. <span data-ttu-id="57bbc-186">[ **ホログラム** ] フォルダーで、次のアセットを **階層** のルートにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-186">In the **Holograms** folder, drag and drop the following assets into the root of the **Hierarchy** :</span></span>
    * <span data-ttu-id="57bbc-187">**AstroMan**</span><span class="sxs-lookup"><span data-stu-id="57bbc-187">**AstroMan**</span></span>
    * <span data-ttu-id="57bbc-188">**照明**</span><span class="sxs-lookup"><span data-stu-id="57bbc-188">**Lights**</span></span>
    * <span data-ttu-id="57bbc-189">**Space Audiosource**</span><span class="sxs-lookup"><span data-stu-id="57bbc-189">**SpaceAudioSource**</span></span>
    * <span data-ttu-id="57bbc-190">**スペースの背景**</span><span class="sxs-lookup"><span data-stu-id="57bbc-190">**SpaceBackground**</span></span>
6. <span data-ttu-id="57bbc-191">Astronaut を表示するには、 **再生モード** を開始▶します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-191">Start **Play Mode** ▶ to view the astronaut.</span></span>
7. <span data-ttu-id="57bbc-192">[ **再生モード** ▶もう一度クリックして **停止** します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-192">Click **Play Mode** ▶ again to **Stop** .</span></span>
8. <span data-ttu-id="57bbc-193">**ホログラム** フォルダーで、[ **fitbox]** 資産を見つけて、 **階層** のルートにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-193">In the **Holograms** folder, find the **Fitbox** asset and drag it to the root of the **Hierarchy** .</span></span>
9. <span data-ttu-id="57bbc-194">[ **階層** ] パネルで [ **Fitbox チェックボックス** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-194">Select the **Fitbox** in the **Hierarchy** panel.</span></span>
10. <span data-ttu-id="57bbc-195">**AstroMan** コレクションを **階層** から、[ **インスペクター** ] パネルの [Fitbox ボックスの [ **ホログラムコレクション** ] プロパティにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-195">Drag the **AstroMan** collection from the **Hierarchy** to the **Hologram Collection** property of the Fitbox in the **Inspector** panel.</span></span>

### <a name="save-the-project"></a><span data-ttu-id="57bbc-196">プロジェクトを保存する</span><span class="sxs-lookup"><span data-stu-id="57bbc-196">Save the project</span></span>

1. <span data-ttu-id="57bbc-197">新しいシーンを保存します。 [ **ファイル > シーンを名前を付けて保存** します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-197">Save the new scene: **File > Save Scene As** .</span></span>
2. <span data-ttu-id="57bbc-198">[ **新しいフォルダー** ] をクリックし、フォルダーに「 **シーン** 」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-198">Click **New Folder** and name the folder **Scenes** .</span></span>
3. <span data-ttu-id="57bbc-199">ファイルに " **Modelexplorer** " という名前を付け、[ **シーン** ] フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-199">Name the file “ **ModelExplorer** ” and save it in the **Scenes** folder.</span></span>

### <a name="build-the-project"></a><span data-ttu-id="57bbc-200">プロジェクトをビルドする</span><span class="sxs-lookup"><span data-stu-id="57bbc-200">Build the project</span></span>

1. <span data-ttu-id="57bbc-201">Unity で、[ **ファイル > ビルド設定** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-201">In Unity, select **File > Build Settings** .</span></span>
2. <span data-ttu-id="57bbc-202">シーンを追加するには、[開いている **シーンの追加** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-202">Click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="57bbc-203">[ **プラットフォーム** ] ボックスの一覧の [ **ユニバーサル Windows プラットフォーム** ] を選択し、[ **プラットフォームの切り替え** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-203">Select **Universal Windows Platform** in the **Platform** list and click **Switch Platform** .</span></span>
4. <span data-ttu-id="57bbc-204">HoloLens 向けに特に開発している場合は、 **ターゲットデバイス** を **hololens** に設定します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-204">If you're specifically developing for HoloLens, set **Target device** to **HoloLens** .</span></span> <span data-ttu-id="57bbc-205">それ以外の場合は、 **任意のデバイス** に残しておきます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-205">Otherwise, leave it on **Any device** .</span></span>
5. <span data-ttu-id="57bbc-206">**ビルドの種類** が [ **D3D** ] に設定され、[ **sdk** ] が [ **最新のインストール済み** ] に設定されていることを確認します (sdk 16299 以降である必要があります)。</span><span class="sxs-lookup"><span data-stu-id="57bbc-206">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
6. <span data-ttu-id="57bbc-207">[ **ビルド** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-207">Click **Build** .</span></span>
7. <span data-ttu-id="57bbc-208">"App" という名前の **新しいフォルダー** を作成します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-208">Create a **New Folder** named "App".</span></span>
8. <span data-ttu-id="57bbc-209">**アプリ** フォルダーをシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-209">Single click the **App** folder.</span></span>
9. <span data-ttu-id="57bbc-210">**[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-210">Press **Select Folder** .</span></span>

<span data-ttu-id="57bbc-211">Unity が完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-211">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="57bbc-212">**アプリ** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-212">Open the **App** folder.</span></span>
2. <span data-ttu-id="57bbc-213">**Modelexplorer Visual Studio ソリューション** を開きます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-213">Open the **ModelExplorer Visual Studio Solution** .</span></span>

<span data-ttu-id="57bbc-214">HoloLens に展開する場合:</span><span class="sxs-lookup"><span data-stu-id="57bbc-214">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="57bbc-215">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に変更し、ARM から **x86** に変更します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-215">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86** .</span></span>
2. <span data-ttu-id="57bbc-216">[ローカルコンピューター] ボタンの横にあるドロップダウン矢印をクリックし、[ **リモートコンピューター** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-216">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine** .</span></span>
3. <span data-ttu-id="57bbc-217">**HoloLens デバイスの IP アドレス** を入力し、[認証モード] を [ **ユニバーサル (暗号化** されていないプロトコル)] に設定します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-217">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)** .</span></span> <span data-ttu-id="57bbc-218">**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-218">Click **Select** .</span></span> <span data-ttu-id="57bbc-219">デバイスの IP アドレスがわからない場合は、[ **設定] [Network & Internet > 詳細オプション >** 確認してください。</span><span class="sxs-lookup"><span data-stu-id="57bbc-219">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** .</span></span>
4. <span data-ttu-id="57bbc-220">上部のメニューバーで、[デバッグ]、[ **デバッグなしで開始** ] の順にクリック >、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-220">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5** .</span></span> <span data-ttu-id="57bbc-221">初めてデバイスをデプロイする場合は、 [Visual Studio とペアリング](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57bbc-221">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="57bbc-222">アプリが展開されたら、 **select ジェスチャ** を使用して、[ **fitbox** ] を閉じます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-222">When the app has deployed, dismiss the **Fitbox** with a **select gesture** .</span></span>

<span data-ttu-id="57bbc-223">イマーシブヘッドセットに展開する場合:</span><span class="sxs-lookup"><span data-stu-id="57bbc-223">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="57bbc-224">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に、ARM から **x64** に変更します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-224">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64** .</span></span>
2. <span data-ttu-id="57bbc-225">配置ターゲットが **ローカルコンピューター** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-225">Make sure the deployment target is set to **Local Machine** .</span></span>
3. <span data-ttu-id="57bbc-226">上部のメニューバーで、[デバッグ]、[ **デバッグなしで開始** ] の順にクリック >、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-226">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5** .</span></span>
4. <span data-ttu-id="57bbc-227">アプリがデプロイされたら、モーションコントローラーでトリガーをプルして、[ **Fitbox ボックス** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-227">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

## <a name="chapter-2---cursor-and-target-feedback"></a><span data-ttu-id="57bbc-228">第2章-カーソルとターゲットのフィードバック</span><span class="sxs-lookup"><span data-stu-id="57bbc-228">Chapter 2 - Cursor and target feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/S24u0V_T7ZI]

### <a name="objectives"></a><span data-ttu-id="57bbc-229">目標</span><span class="sxs-lookup"><span data-stu-id="57bbc-229">Objectives</span></span>

* <span data-ttu-id="57bbc-230">カーソルの視覚的なデザインと動作。</span><span class="sxs-lookup"><span data-stu-id="57bbc-230">Cursor visual design and behavior.</span></span>
* <span data-ttu-id="57bbc-231">見つめ based のカーソルフィードバック。</span><span class="sxs-lookup"><span data-stu-id="57bbc-231">Gaze-based cursor feedback.</span></span>
* <span data-ttu-id="57bbc-232">宝石によるホログラムフィードバック。</span><span class="sxs-lookup"><span data-stu-id="57bbc-232">Gaze-based hologram feedback.</span></span>

<span data-ttu-id="57bbc-233">ここでは、いくつかのカーソルデザインの原則に基づいて作業を行います。</span><span class="sxs-lookup"><span data-stu-id="57bbc-233">We're going to base our work on some cursor design principles, namely:</span></span>

* <span data-ttu-id="57bbc-234">カーソルは常に存在します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-234">The cursor is always present.</span></span>
* <span data-ttu-id="57bbc-235">カーソルが小さすぎるか、または大きくならないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="57bbc-235">Don't let the cursor get too small or big.</span></span>
* <span data-ttu-id="57bbc-236">Obstructing コンテンツは避けてください。</span><span class="sxs-lookup"><span data-stu-id="57bbc-236">Avoid obstructing content.</span></span>

### <a name="instructions"></a><span data-ttu-id="57bbc-237">Instructions</span><span class="sxs-lookup"><span data-stu-id="57bbc-237">Instructions</span></span>

1. <span data-ttu-id="57bbc-238">**HoloToolkit\Input\Prefabs** フォルダーで、 **inputmanager** 資産を見つけます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-238">In the **HoloToolkit\Input\Prefabs** folder, find the **InputManager** asset.</span></span>
2. <span data-ttu-id="57bbc-239">**Inputmanager** を **階層** にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-239">Drag and drop the **InputManager** onto the **Hierarchy** .</span></span>
3. <span data-ttu-id="57bbc-240">**HoloToolkit\Input\Prefabs** フォルダーで、 **カーソル** アセットを見つけます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-240">In the **HoloToolkit\Input\Prefabs** folder, find the **Cursor** asset.</span></span>
4. <span data-ttu-id="57bbc-241">**カーソル** を **階層** にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-241">Drag and drop the **Cursor** onto the **Hierarchy** .</span></span>
5. <span data-ttu-id="57bbc-242">**階層** 内の **inputmanager** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-242">Select the **InputManager** object in the **Hierarchy** .</span></span>
6. <span data-ttu-id="57bbc-243">**インスペクター** の下部にあるカーソルオブジェクトを、 **階層** から Inputmanager の **Simplesingleポインタセレクター** の **cursor** フィールドに **ドラッグします** 。</span><span class="sxs-lookup"><span data-stu-id="57bbc-243">Drag the **Cursor** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector** 's **Cursor** field, at the bottom of the **Inspector** .</span></span>

![単純な単一ポインターセレクターの設定](images/holograms210-ssps.png)

### <a name="build-and-deploy"></a><span data-ttu-id="57bbc-245">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="57bbc-245">Build and Deploy</span></span>

1. <span data-ttu-id="57bbc-246">**ファイル > ビルド設定** からアプリをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-246">Rebuild the app from **File > Build Settings** .</span></span>
2. <span data-ttu-id="57bbc-247">**アプリフォルダー** を開きます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-247">Open the **App folder** .</span></span>
3. <span data-ttu-id="57bbc-248">**Modelexplorer Visual Studio ソリューション** を開きます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-248">Open the **ModelExplorer Visual Studio Solution** .</span></span>
4. <span data-ttu-id="57bbc-249">[ **デバッグ]、[デバッグなしで開始] の順にクリック >** 、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-249">Click **Debug -> Start Without debugging** or press **Ctrl + F5** .</span></span>
5. <span data-ttu-id="57bbc-250">カーソルの描画方法と、ホログラムに触れている場合の外観の変化を確認します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-250">Observe how the cursor is drawn, and how it changes appearance if it is touching a hologram.</span></span>

### <a name="instructions"></a><span data-ttu-id="57bbc-251">Instructions</span><span class="sxs-lookup"><span data-stu-id="57bbc-251">Instructions</span></span>

1. <span data-ttu-id="57bbc-252">[ **階層** ] パネルで、[ **AstroMan** -> **GEO_G** -> **Back_Center** ] オブジェクトを展開します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-252">In the **Hierarchy** panel, expand the **AstroMan**->**GEO_G**->**Back_Center** object.</span></span>
2. <span data-ttu-id="57bbc-253">**Interactible.cs** をダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-253">Double click on **Interactible.cs** to open it in Visual Studio.</span></span>
3. <span data-ttu-id="57bbc-254">**Interactible.cs** の **OnFocusEnter ()** および **OnFocusExit ()** コールバックの行をコメント解除します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-254">Uncomment the lines in the **IFocusable.OnFocusEnter()** and **IFocusable.OnFocusExit()** callbacks in **Interactible.cs** .</span></span> <span data-ttu-id="57bbc-255">これらは、(宝石またはコントローラーをポイントすることによって) フォーカスが特定のオブジェクトの collider を出入りするときに、Mixed Reality Toolkit の InputManager によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-255">These are called by the Mixed Reality Toolkit's InputManager when focus (either by gaze or by controller pointing) enters and exits the specific GameObject's collider.</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 2.d */

void IFocusable.OnFocusEnter()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to highlight the material when gaze enters.
        defaultMaterials[i].EnableKeyword("_ENVIRONMENT_COLORING");
    }
}

void IFocusable.OnFocusExit()
{
    for (int i = 0; i < defaultMaterials.Length; i++)
    {
        // 2.d: Uncomment the below line to remove highlight on material when gaze exits.
        defaultMaterials[i].DisableKeyword("_ENVIRONMENT_COLORING");
    }
}
```

>[!NOTE]
><span data-ttu-id="57bbc-256">以上を使用し `EnableKeyword` て `DisableKeyword` います。</span><span class="sxs-lookup"><span data-stu-id="57bbc-256">We use `EnableKeyword` and `DisableKeyword` above.</span></span> <span data-ttu-id="57bbc-257">ツールキットの標準シェーダーを使用して独自のアプリでこれらを使用するには、スクリプトを使用して [マテリアルにアクセスするための Unity ガイドライン](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html)に従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="57bbc-257">In order to make use of these in your own app with the Toolkit's Standard shader, you'll need to follow the [Unity guidelines for accessing materials via script](https://docs.unity3d.com/Manual/MaterialsAccessingViaScript.html).</span></span> <span data-ttu-id="57bbc-258">この例では、リソースフォルダーに必要な、強調表示された [3 つの素材](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) が既に含まれています (名前に強調表示された3つの素材を探します)。</span><span class="sxs-lookup"><span data-stu-id="57bbc-258">In this case, we've already included the [three variants of highlighted material](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-210-Gaze/Completed/ModelExplorer/Assets/Resources/Models/AstroMan/Materials) needed in the Resources folder (look for the three materials with highlight in the name).</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="57bbc-259">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="57bbc-259">Build and Deploy</span></span>

1. <span data-ttu-id="57bbc-260">前と同様に、プロジェクトをビルドし、HoloLens にデプロイします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-260">As before, build the project and deploy to the HoloLens.</span></span>
2. <span data-ttu-id="57bbc-261">1つのオブジェクトを対象としていて、そうでない場合はどうなるかを観察します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-261">Observe what happens when the gaze is aimed at an object and when it's not.</span></span>

## <a name="chapter-3---targeting-techniques"></a><span data-ttu-id="57bbc-262">章 3-ターゲット手法</span><span class="sxs-lookup"><span data-stu-id="57bbc-262">Chapter 3 - Targeting Techniques</span></span>

>[!VIDEO https://www.youtube.com/embed/TFnuLva4VJ0]

### <a name="objectives"></a><span data-ttu-id="57bbc-263">目標</span><span class="sxs-lookup"><span data-stu-id="57bbc-263">Objectives</span></span>

* <span data-ttu-id="57bbc-264">ホログラムを簡単にターゲット設定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-264">Make it easier to target holograms.</span></span>
* <span data-ttu-id="57bbc-265">自然な移動を安定化します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-265">Stabilize natural head movements.</span></span>

### <a name="instructions"></a><span data-ttu-id="57bbc-266">Instructions</span><span class="sxs-lookup"><span data-stu-id="57bbc-266">Instructions</span></span>

1. <span data-ttu-id="57bbc-267">[ **階層** ] パネルで、 **inputmanager** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-267">In the **Hierarchy** panel, select the **InputManager** object.</span></span>
2. <span data-ttu-id="57bbc-268">[ **インスペクター** ] パネルで、 **宝石** のスクリプトを見つけます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-268">In the **Inspector** panel, find the **Gaze Stabilizer** script.</span></span> <span data-ttu-id="57bbc-269">表示する場合は、これをクリックして Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-269">Click it to open in Visual Studio, if you want to take a look.</span></span>
    * <span data-ttu-id="57bbc-270">このスクリプトは、Raycast データのサンプルに対して反復処理を行い、精度のターゲット設定のためにユーザーの宝石を安定化するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-270">This script iterates over samples of Raycast data and helps stabilize the user's gaze for precision targeting.</span></span>
3. <span data-ttu-id="57bbc-271">**インスペクター** では、[ **保存された安定性のサンプル** ] の値を編集できます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-271">In the **Inspector** , you can edit the **Stored Stability Samples** value.</span></span> <span data-ttu-id="57bbc-272">この値は、安定板が、安定値を計算するために反復処理するサンプルの数を表します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-272">This value represents the number of samples that the stabilizer iterates on to calculate the stabilized value.</span></span>

## <a name="chapter-4---directional-indicator"></a><span data-ttu-id="57bbc-273">Chapter 4 方向インジケーター</span><span class="sxs-lookup"><span data-stu-id="57bbc-273">Chapter 4 - Directional indicator</span></span>

>[!VIDEO https://www.youtube.com/embed/htVbJCMlj64]

### <a name="objectives"></a><span data-ttu-id="57bbc-274">目標</span><span class="sxs-lookup"><span data-stu-id="57bbc-274">Objectives</span></span>

* <span data-ttu-id="57bbc-275">ホログラムの検索に役立つように、カーソルに方向インジケーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-275">Add a directional indicator on the cursor to help find holograms.</span></span>

### <a name="instructions"></a><span data-ttu-id="57bbc-276">Instructions</span><span class="sxs-lookup"><span data-stu-id="57bbc-276">Instructions</span></span>

<span data-ttu-id="57bbc-277">**DirectionIndicator.cs** ファイルを次のように使用します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-277">We're going to use the **DirectionIndicator.cs** file which will:</span></span>

1. <span data-ttu-id="57bbc-278">ユーザーがホログラムを見ていない場合は、方向インジケーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-278">Show the directional indicator if the user is not gazing at the holograms.</span></span>
2. <span data-ttu-id="57bbc-279">ユーザーがホログラムでの表示を切り替えている場合は、方向インジケーターを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-279">Hide the directional indicator if the user is gazing at the holograms.</span></span>
3. <span data-ttu-id="57bbc-280">ホログラムをポイントするように方向インジケーターを更新します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-280">Update the directional indicator to point to the holograms.</span></span>

<span data-ttu-id="57bbc-281">では、始めましょう。</span><span class="sxs-lookup"><span data-stu-id="57bbc-281">Let's get started.</span></span>

1. <span data-ttu-id="57bbc-282">**階層** パネルで **AstroMan** オブジェクトをクリックし、 **矢印をクリック** して展開します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-282">Click on the **AstroMan** object in the **Hierarchy** panel and **click the arrow** to expand it.</span></span>
2. <span data-ttu-id="57bbc-283">[ **階層** ] パネルで、[ **AstroMan** **] の [** 方向] を選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-283">In the **Hierarchy** panel, select the **DirectionalIndicator** object under **AstroMan** .</span></span>
3. <span data-ttu-id="57bbc-284">[ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
4. <span data-ttu-id="57bbc-285">メニューで、検索ボックスの **方向インジケーター** を入力します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-285">In the menu, type in the search box **Direction Indicator** .</span></span> <span data-ttu-id="57bbc-286">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-286">Select the search result.</span></span>
5. <span data-ttu-id="57bbc-287">[ **階層** ] パネルで、 **Cursor** オブジェクトを **インスペクター** の **cursor** プロパティにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-287">In the **Hierarchy** panel, drag and drop the **Cursor** object onto the **Cursor** property in the **Inspector** .</span></span>
6. <span data-ttu-id="57bbc-288">[ **プロジェクト** ] パネルの [ **ホログラム** ] フォルダーで、 **Direction Alindicator** 資産を **インスペクター** の **指向性インジケーター** プロパティにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-288">In the **Project** panel, in the **Holograms** folder, drag and drop the **DirectionalIndicator** asset onto the **Directional Indicator** property in the **Inspector** .</span></span>
7. <span data-ttu-id="57bbc-289">アプリをビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-289">Build and deploy the app.</span></span>
8. <span data-ttu-id="57bbc-290">ディレクショナルインジケーターオブジェクトを使用して astronaut を見つける方法をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="57bbc-290">Watch how the directional indicator object helps you find the astronaut.</span></span>

## <a name="chapter-5---billboarding"></a><span data-ttu-id="57bbc-291">章 5-Billboarding</span><span class="sxs-lookup"><span data-stu-id="57bbc-291">Chapter 5 - Billboarding</span></span>

>[!VIDEO https://www.youtube.com/embed/qFiLr_LUACE]

### <a name="objectives"></a><span data-ttu-id="57bbc-292">目標</span><span class="sxs-lookup"><span data-stu-id="57bbc-292">Objectives</span></span>

* <span data-ttu-id="57bbc-293">Billboarding を使用して、ホログラムが常に直面するようにします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-293">Use billboarding to have holograms always face towards you.</span></span>

<span data-ttu-id="57bbc-294">**Billboard.cs** ファイルを使用して、ユーザーに常に接続されていることを示すために、そのオブジェクトの向きを維持します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-294">We will be using the **Billboard.cs** file to keep a GameObject oriented such that it is facing the user at all times.</span></span>

1. <span data-ttu-id="57bbc-295">[ **階層** ] パネルで、 **AstroMan** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-295">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
2. <span data-ttu-id="57bbc-296">[ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-296">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="57bbc-297">メニューで、[検索] ボックスに「 **ビルボード** 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-297">In the menu, type in the search box **Billboard** .</span></span> <span data-ttu-id="57bbc-298">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-298">Select the search result.</span></span>
4. <span data-ttu-id="57bbc-299">**インスペクター** で、 **ピボット軸** を **Y** に設定します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-299">In the **Inspector** set the **Pivot Axis** to **Y** .</span></span>
5. <span data-ttu-id="57bbc-300">試してみる</span><span class="sxs-lookup"><span data-stu-id="57bbc-300">Try it!</span></span> <span data-ttu-id="57bbc-301">以前と同じように、アプリをビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-301">Build and deploy the app as before.</span></span>
6. <span data-ttu-id="57bbc-302">ビルボードオブジェクトがどのように視点を変更するかに関係なく、どのように表示されるかを確認します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-302">See how the Billboard object faces you no matter how you change the viewpoint.</span></span>
7. <span data-ttu-id="57bbc-303">ここでは、 **AstroMan** からスクリプトを削除します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-303">Delete the script from the **AstroMan** for now.</span></span>

## <a name="chapter-6---tag-along"></a><span data-ttu-id="57bbc-304">Chapter 6-タグに沿って</span><span class="sxs-lookup"><span data-stu-id="57bbc-304">Chapter 6 - Tag-Along</span></span>

>[!VIDEO https://www.youtube.com/embed/Ct8ORZAX5JU]

### <a name="objectives"></a><span data-ttu-id="57bbc-305">目標</span><span class="sxs-lookup"><span data-stu-id="57bbc-305">Objectives</span></span>

* <span data-ttu-id="57bbc-306">タグを使用して、ホログラムが部屋の周りをたどるようにします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-306">Use Tag-Along to have our holograms follow us around the room.</span></span>

<span data-ttu-id="57bbc-307">この問題に対処する際には、次の設計上の制約があります。</span><span class="sxs-lookup"><span data-stu-id="57bbc-307">As we work on this issue, we'll be guided by the following design constraints:</span></span>

* <span data-ttu-id="57bbc-308">コンテンツは常に一目でわかるはずです。</span><span class="sxs-lookup"><span data-stu-id="57bbc-308">Content should always be a glance away.</span></span>
* <span data-ttu-id="57bbc-309">コンテンツは使用できません。</span><span class="sxs-lookup"><span data-stu-id="57bbc-309">Content should not be in the way.</span></span>
* <span data-ttu-id="57bbc-310">ヘッドロックコンテンツは不快になります。</span><span class="sxs-lookup"><span data-stu-id="57bbc-310">Head-locking content is uncomfortable.</span></span>

<span data-ttu-id="57bbc-311">ここで使用するソリューションでは、"タグに沿った" 方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-311">The solution used here is to use a "tag-along" approach.</span></span>

<span data-ttu-id="57bbc-312">タグに沿ったオブジェクトは、ユーザーのビューを完全に離れることができません。</span><span class="sxs-lookup"><span data-stu-id="57bbc-312">A tag-along object never fully leaves the user's view.</span></span> <span data-ttu-id="57bbc-313">タグは、ユーザーの先頭にラバーバンドでアタッチされたオブジェクトであると考えることができます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-313">You can think of the a tag-along as being an object attached to the user's head by rubber bands.</span></span> <span data-ttu-id="57bbc-314">ユーザーが移動すると、完全に離れることなく、ビューの端に向かってスライドします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-314">As the user moves, the content will stay within an easy glance by sliding towards the edge of the view without completely leaving.</span></span> <span data-ttu-id="57bbc-315">ユーザーがタグに沿って gazes すると、より完全に表示されます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-315">When the user gazes towards the tag-along object, it comes more fully into view.</span></span>

<span data-ttu-id="57bbc-316">**SimpleTagalong.cs** ファイルを次のように使用します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-316">We're going to use the **SimpleTagalong.cs** file which will:</span></span>

1. <span data-ttu-id="57bbc-317">タグに沿ったオブジェクトがカメラの境界内にあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-317">Determine if the Tag-Along object is within the camera bounds.</span></span>
2. <span data-ttu-id="57bbc-318">視錐ビュー内にない場合は、タグを、視錐のビュー内で部分的に配置します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-318">If not within the view frustum, position the Tag-Along to partially within the view frustum.</span></span>
3. <span data-ttu-id="57bbc-319">それ以外の場合は、ユーザーからの既定の距離にタグを配置します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-319">Otherwise, position the Tag-Along to a default distance from the user.</span></span>

<span data-ttu-id="57bbc-320">これを行うには、まず、 **Interactible.cs** スクリプトを変更して **TagalongAction** を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="57bbc-320">To do this, we first must change the **Interactible.cs** script to call the **TagalongAction** .</span></span>

1. <span data-ttu-id="57bbc-321">コード演習 6. a (コメント解除行 84 ~ 87) を実行して **Interactible.cs** を編集します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-321">Edit **Interactible.cs** by completing coding exercise 6.a (uncommenting lines 84 to 87).</span></span>

```cs
/* TODO: DEVELOPER CODING EXERCISE 6.a */
// 6.a: Uncomment the lines below to perform a Tagalong action.
if (interactibleAction != null)
{
    interactibleAction.PerformAction();
}
```

<span data-ttu-id="57bbc-322">**InteractibleAction.cs** スクリプトは、 **Interactible.cs** と組み合わせて、ホログラムをタップしたときにカスタムアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-322">The **InteractibleAction.cs** script, paired with **Interactible.cs** performs custom actions when you tap on holograms.</span></span> <span data-ttu-id="57bbc-323">この例では、タグに対して特に使用します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-323">In this case, we'll use one specifically for tag-along.</span></span>

* <span data-ttu-id="57bbc-324">**Scripts** フォルダーで、[ **TagalongAction.cs** asset] をクリックして Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-324">In the **Scripts** folder click on **TagalongAction.cs** asset to open in Visual Studio.</span></span>
* <span data-ttu-id="57bbc-325">コーディングの演習を完了するか、次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-325">Complete the coding exercise or change it to this:</span></span>
  * <span data-ttu-id="57bbc-326">**階層** の最上位にある [検索] バーに **ChestButton_Center** を入力し、結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-326">At the top of the **Hierarchy** , in the search bar type **ChestButton_Center** and select the result.</span></span>
  * <span data-ttu-id="57bbc-327">[ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-327">In the **Inspector** panel, click the **Add Component** button.</span></span>
  * <span data-ttu-id="57bbc-328">メニューの [検索 **] ボックスに** 、「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-328">In the menu, type in the search box **Tagalong Action** .</span></span> <span data-ttu-id="57bbc-329">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-329">Select the search result.</span></span>
  * <span data-ttu-id="57bbc-330">[ **ホログラム** フォルダー] で、資産の **タグ** を検索します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-330">In **Holograms** folder find the **Tagalong** asset.</span></span>
  * <span data-ttu-id="57bbc-331">**階層** 内の **ChestButton_Center** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-331">Select the **ChestButton_Center** object in the **Hierarchy** .</span></span> <span data-ttu-id="57bbc-332">[ **プロジェクト** ] パネルの [ **tagalong** オブジェクトを、[プロパティ] にある [ **オブジェクト** **] にドラッグ** アンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-332">Drag and drop the **TagAlong** object from the **Project** panel onto the **Inspector** into the **Object To Tagalong** property.</span></span>
  * <span data-ttu-id="57bbc-333">**インスペクター** の **tagalong アクション** オブジェクトを、 **Interactible** スクリプトの **Interactible action** フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-333">Drag the **Tagalong Action** object from the **Inspector** into the **Interactible Action** field on the **Interactible** script.</span></span>
* <span data-ttu-id="57bbc-334">**TagalongAction** スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="57bbc-334">Double click the **TagalongAction** script to open it in Visual Studio.</span></span>

![Interactible のセットアップ](images/holograms210-interactible.png)

<span data-ttu-id="57bbc-336">次のものを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57bbc-336">We need to add the following:</span></span>

* <span data-ttu-id="57bbc-337">TagalongAction スクリプトの実行時関数に機能を追加します (InteractibleAction から継承)。</span><span class="sxs-lookup"><span data-stu-id="57bbc-337">Add functionality to the PerformAction function in the TagalongAction script (inherited from InteractibleAction).</span></span>
* <span data-ttu-id="57bbc-338">Billboarding を gazed オブジェクトに追加し、pivot 軸を XY に設定します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-338">Add billboarding to the gazed-upon object, and set the pivot axis to XY.</span></span>
* <span data-ttu-id="57bbc-339">次に、単純なタグをオブジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="57bbc-339">Then add simple Tag-Along to the object.</span></span>

<span data-ttu-id="57bbc-340">**TagalongAction.cs** のソリューションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="57bbc-340">Here's our solution, from **TagalongAction.cs** :</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using HoloToolkit.Unity;
using UnityEngine;

public class TagalongAction : InteractibleAction
{
    [SerializeField]
    [Tooltip("Drag the Tagalong prefab asset you want to display.")]
    private GameObject objectToTagalong;

    private void Awake()
    {
        if (objectToTagalong != null)
        {
            objectToTagalong = Instantiate(objectToTagalong);
            objectToTagalong.SetActive(false);

            /* TODO: DEVELOPER CODING EXERCISE 6.b */

            // 6.b: AddComponent Billboard to objectToTagAlong,
            // so it's always facing the user as they move.
            Billboard billboard = objectToTagalong.AddComponent<Billboard>();

            // 6.b: AddComponent SimpleTagalong to objectToTagAlong,
            // so it's always following the user as they move.
            objectToTagalong.AddComponent<SimpleTagalong>();

            // 6.b: Set any public properties you wish to experiment with.
            billboard.PivotAxis = PivotAxis.XY; // Already the default, but provided in case you want to edit
        }
    }

    public override void PerformAction()
    {
        // Recommend having only one tagalong.
        if (objectToTagalong == null || objectToTagalong.activeSelf)
        {
            return;
        }

        objectToTagalong.SetActive(true);
    }
}
```

* <span data-ttu-id="57bbc-341">試してみる</span><span class="sxs-lookup"><span data-stu-id="57bbc-341">Try it!</span></span> <span data-ttu-id="57bbc-342">アプリをビルドしてデプロイします。</span><span class="sxs-lookup"><span data-stu-id="57bbc-342">Build and deploy the app.</span></span>
* <span data-ttu-id="57bbc-343">コンテンツが注視点の中心に沿っているかどうかを監視しますが、継続的にはブロックしないでください。</span><span class="sxs-lookup"><span data-stu-id="57bbc-343">Watch how the content follows the center of the gaze point, but not continuously and without blocking it.</span></span>