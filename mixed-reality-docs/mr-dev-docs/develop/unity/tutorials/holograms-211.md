---
title: MR 入力 211 - ジェスチャ
description: Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、ジェスチャの概念の詳細を確認してください。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、academy、チュートリアル、ジェスチャ、HoloLens、Mixed Reality Academy、unity、mixed reality ヘッドセット、windows Mixed reality ヘッドセット、virtual Reality ヘッドセット、Windows 10
ms.openlocfilehash: 9f83e2f3b02cf8d83b2fb58a3a0d05dc8576b0e8
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678291"
---
# <a name="mr-input-211-gesture"></a><span data-ttu-id="11dcb-104">MR 入力 211:ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="11dcb-104">MR Input 211: Gesture</span></span>

>[!NOTE]
><span data-ttu-id="11dcb-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="11dcb-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="11dcb-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="11dcb-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="11dcb-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。</span><span class="sxs-lookup"><span data-stu-id="11dcb-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="11dcb-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="11dcb-109">HoloLens 2 向けには、[新しいチュートリアル シリーズ](../../../mr-learning-base-01.md)が投稿されています。</span><span class="sxs-lookup"><span data-stu-id="11dcb-109">[A new series of tutorials](../../../mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="11dcb-110">[ジェスチャ](../../../design/gaze-and-commit.md#composite-gestures) によって、ユーザーの意図が動作するようになります。</span><span class="sxs-lookup"><span data-stu-id="11dcb-110">[Gestures](../../../design/gaze-and-commit.md#composite-gestures) turn user intention into action.</span></span> <span data-ttu-id="11dcb-111">ユーザーはジェスチャを使用して、ホログラムを操作できます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-111">With gestures, users can interact with holograms.</span></span> <span data-ttu-id="11dcb-112">このコースでは、ユーザーの手を追跡し、ユーザー入力に応答して、手動による状態と場所に基づいてユーザーにフィードバックを送る方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-112">In this course, we'll learn how to track the user's hands, respond to user input, and give feedback to the user based on hand state and location.</span></span>

>[!VIDEO https://www.youtube.com/embed/c9zlpfFeEtc]

<span data-ttu-id="11dcb-113">[MR 基本 101](../../../develop/unity/tutorials/holograms-101.md)では、単純なエアタップジェスチャを使用して、ホログラムを操作していました。</span><span class="sxs-lookup"><span data-stu-id="11dcb-113">In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), we used a simple air-tap gesture to interact with our holograms.</span></span> <span data-ttu-id="11dcb-114">ここでは、エアタップのジェスチャを超えて、次のような新しい概念を見ていきます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-114">Now, we'll move beyond the air-tap gesture and explore new concepts to:</span></span>

* <span data-ttu-id="11dcb-115">ユーザーの手が追跡されていることを検出し、ユーザーにフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-115">Detect when the user's hand is being tracked and provide feedback to the user.</span></span>
* <span data-ttu-id="11dcb-116">ナビゲーションジェスチャを使用して、ホログラムを回転させます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-116">Use a navigation gesture to rotate our holograms.</span></span>
* <span data-ttu-id="11dcb-117">ユーザーの手が消えようとしているときにフィードバックを提供します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-117">Provide feedback when the user's hand is about to go out of view.</span></span>
* <span data-ttu-id="11dcb-118">操作イベントを使用して、ユーザーが自分でホログラムを移動できるようにします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-118">Use manipulation events to allow users to move holograms with their hands.</span></span>

<span data-ttu-id="11dcb-119">このコースでは、 [MR 入力 210](holograms-210.md)で構築した Unity プロジェクト **モデルエクスプローラー** について説明します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-119">In this course, we'll revisit the Unity project **Model Explorer**, which we built in [MR Input 210](holograms-210.md).</span></span> <span data-ttu-id="11dcb-120">Astronaut の友人は、これらの新しいジェスチャの概念をご紹介します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-120">Our astronaut friend is back to assist us in our exploration of these new gesture concepts.</span></span>

>[!IMPORTANT]
><span data-ttu-id="11dcb-121">以下の各章に埋め込まれているビデオは、古いバージョンの Unity と Mixed Reality Toolkit を使用して記録されています。</span><span class="sxs-lookup"><span data-stu-id="11dcb-121">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="11dcb-122">ステップバイステップの手順は正確であり、最新のものですが、最新ではない対応するビデオにスクリプトとビジュアルが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="11dcb-122">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="11dcb-123">ビデオはために含まれています。ここで説明する概念は引き続き適用されます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-123">The videos remain included for posterity and because the concepts covered still apply.</span></span>

## <a name="device-support"></a><span data-ttu-id="11dcb-124">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="11dcb-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="11dcb-125">コース</span><span class="sxs-lookup"><span data-stu-id="11dcb-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="11dcb-126"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="11dcb-126"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="11dcb-127"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="11dcb-127"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="11dcb-128">MR 入力 211:ジェスチャ</span><span class="sxs-lookup"><span data-stu-id="11dcb-128">MR Input 211: Gesture</span></span></td><td style="text-align: center;"> <span data-ttu-id="11dcb-129">✔️</span><span class="sxs-lookup"><span data-stu-id="11dcb-129">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="11dcb-130">✔️</span><span class="sxs-lookup"><span data-stu-id="11dcb-130">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="11dcb-131">開始する前に</span><span class="sxs-lookup"><span data-stu-id="11dcb-131">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="11dcb-132">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="11dcb-132">Prerequisites</span></span>

* <span data-ttu-id="11dcb-133">適切な [ツールがインストール](../../../develop/install-the-tools.md)された WINDOWS 10 PC。</span><span class="sxs-lookup"><span data-stu-id="11dcb-133">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="11dcb-134">基本的な C# プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="11dcb-134">Some basic C# programming ability.</span></span>
* <span data-ttu-id="11dcb-135">[MR の基本 101](../../../develop/unity/tutorials/holograms-101.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="11dcb-135">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="11dcb-136">[MR 入力 210](holograms-210.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="11dcb-136">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="11dcb-137">[開発用に構成され](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)た HoloLens デバイス。</span><span class="sxs-lookup"><span data-stu-id="11dcb-137">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="11dcb-138">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="11dcb-138">Project files</span></span>

* <span data-ttu-id="11dcb-139">プロジェクトに必要な [ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-139">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-211-Gesture.zip) required by the project.</span></span> <span data-ttu-id="11dcb-140">Unity 2017.2 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="11dcb-140">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="11dcb-141">ファイルをデスクトップまたはその他の簡単な場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-141">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="11dcb-142">ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture)ます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-142">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-211-Gesture).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="11dcb-143">エラッタとメモ</span><span class="sxs-lookup"><span data-stu-id="11dcb-143">Errata and Notes</span></span>

* <span data-ttu-id="11dcb-144">コード内のブレークポイントにヒットするには、Visual Studio の [ツール]->オプション->デバッグ] の下にある [マイコードのみを有効にする] を無効 (*オフ*) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="11dcb-144">"Enable Just My Code" needs to be disabled (*unchecked*) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="chapter-0---unity-setup"></a><span data-ttu-id="11dcb-145">章 0-Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="11dcb-145">Chapter 0 - Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="11dcb-146">手順</span><span class="sxs-lookup"><span data-stu-id="11dcb-146">Instructions</span></span>

1. <span data-ttu-id="11dcb-147">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-147">Start Unity.</span></span>
2. <span data-ttu-id="11dcb-148">**[Open (開く)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-148">Select **Open**.</span></span>
3. <span data-ttu-id="11dcb-149">以前にアーカイブしていない **ジェスチャ** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-149">Navigate to the **Gesture** folder you previously un-archived.</span></span>
4. <span data-ttu-id="11dcb-150">[モデルエクスプローラーの **開始**] フォルダーを見つけて選択し / **Model Explorer** ます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-150">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="11dcb-151">[ **フォルダーの選択** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-151">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="11dcb-152">[ **プロジェクト** ] パネルで、[ **シーン** ] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-152">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="11dcb-153">[ **Modelexplorer** シーン] をダブルクリックして Unity に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-153">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="11dcb-154">ビルド</span><span class="sxs-lookup"><span data-stu-id="11dcb-154">Building</span></span>

1. <span data-ttu-id="11dcb-155">Unity で、[ **ファイル > ビルド設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-155">In Unity, select **File > Build Settings**.</span></span>
2. <span data-ttu-id="11dcb-156">シーン **/ModelExplorer** が [ **ビルド] の [シーン**] に表示されていない場合は、[開いているシーンの **追加** ] をクリックしてシーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-156">If **Scenes/ModelExplorer** is not listed in **Scenes In Build**, click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="11dcb-157">HoloLens 向けに特に開発している場合は、 **ターゲットデバイス** を **hololens** に設定します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-157">If you're specifically developing for HoloLens, set **Target device** to **HoloLens**.</span></span> <span data-ttu-id="11dcb-158">それ以外の場合は、 **任意のデバイス** に残しておきます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-158">Otherwise, leave it on **Any device**.</span></span>
4. <span data-ttu-id="11dcb-159">**ビルドの種類** が [ **D3D** ] に設定され、[ **sdk** ] が [**最新のインストール済み**] に設定されていることを確認します (sdk 16299 以降である必要があります)。</span><span class="sxs-lookup"><span data-stu-id="11dcb-159">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="11dcb-160">[**ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-160">Click **Build**.</span></span>
6. <span data-ttu-id="11dcb-161">"App" という名前の **新しいフォルダー** を作成します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-161">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="11dcb-162">**アプリ** フォルダーをシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-162">Single click the **App** folder.</span></span>
8. <span data-ttu-id="11dcb-163">**[フォルダーの選択]** をクリックすると、Unity によって Visual Studio のプロジェクトのビルドが開始されます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-163">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="11dcb-164">Unity が完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-164">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="11dcb-165">**アプリ** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-165">Open the **App** folder.</span></span>
2. <span data-ttu-id="11dcb-166">**Modelexplorer Visual Studio ソリューション** を開きます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-166">Open the **ModelExplorer Visual Studio Solution**.</span></span>

<span data-ttu-id="11dcb-167">HoloLens に展開する場合:</span><span class="sxs-lookup"><span data-stu-id="11dcb-167">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="11dcb-168">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に変更し、ARM から **x86** に変更します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-168">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86**.</span></span>
2. <span data-ttu-id="11dcb-169">[ローカルコンピューター] ボタンの横にあるドロップダウン矢印をクリックし、[ **リモートコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-169">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine**.</span></span>
3. <span data-ttu-id="11dcb-170">**HoloLens デバイスの IP アドレス** を入力し、[認証モード] を [**ユニバーサル (暗号化** されていないプロトコル)] に設定します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-170">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)**.</span></span> <span data-ttu-id="11dcb-171">**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-171">Click **Select**.</span></span> <span data-ttu-id="11dcb-172">デバイスの IP アドレスがわからない場合は、[ **設定] [Network & Internet > 詳細オプション >** 確認してください。</span><span class="sxs-lookup"><span data-stu-id="11dcb-172">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options**.</span></span>
4. <span data-ttu-id="11dcb-173">上部のメニューバーで、[デバッグ]、[ **デバッグなしで開始** ] の順にクリック >、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-173">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span> <span data-ttu-id="11dcb-174">初めてデバイスをデプロイする場合は、 [Visual Studio とペアリング](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11dcb-174">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="11dcb-175">アプリが展開されたら、 **select ジェスチャ** を使用して、[ **fitbox** ] を閉じます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-175">When the app has deployed, dismiss the **Fitbox** with a **select gesture**.</span></span>

<span data-ttu-id="11dcb-176">イマーシブヘッドセットに展開する場合:</span><span class="sxs-lookup"><span data-stu-id="11dcb-176">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="11dcb-177">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に、ARM から **x64** に変更します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-177">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64**.</span></span>
2. <span data-ttu-id="11dcb-178">配置ターゲットが **ローカルコンピューター** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-178">Make sure the deployment target is set to **Local Machine**.</span></span>
3. <span data-ttu-id="11dcb-179">上部のメニューバーで、[デバッグ]、[ **デバッグなしで開始** ] の順にクリック >、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-179">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
4. <span data-ttu-id="11dcb-180">アプリがデプロイされたら、モーションコントローラーでトリガーをプルして、[ **Fitbox ボックス** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-180">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="11dcb-181">Visual Studio の [エラー] パネルに赤色のエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="11dcb-181">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="11dcb-182">無視しても安全です。</span><span class="sxs-lookup"><span data-stu-id="11dcb-182">It is safe to ignore them.</span></span> <span data-ttu-id="11dcb-183">実際のビルドの進行状況を表示するには、[出力] パネルに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-183">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="11dcb-184">[出力] パネルでエラーが発生した場合は、修正を行う必要があります (多くの場合、スクリプトの間違いが原因です)。</span><span class="sxs-lookup"><span data-stu-id="11dcb-184">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---hand-detected-feedback"></a><span data-ttu-id="11dcb-185">第1章でのフィードバックの検出</span><span class="sxs-lookup"><span data-stu-id="11dcb-185">Chapter 1 - Hand detected feedback</span></span>

>[!VIDEO https://www.youtube.com/embed/D1FcIyuFTZQ]

### <a name="objectives"></a><span data-ttu-id="11dcb-186">目標</span><span class="sxs-lookup"><span data-stu-id="11dcb-186">Objectives</span></span>

* <span data-ttu-id="11dcb-187">ハンドトラッキングイベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-187">Subscribe to hand tracking events.</span></span>
* <span data-ttu-id="11dcb-188">カーソルのフィードバックを使用して、ユーザーを追跡しているときにユーザーを表示します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-188">Use cursor feedback to show users when a hand is being tracked.</span></span>

>[!NOTE]
><span data-ttu-id="11dcb-189">HoloLens 2 では、両手が表示されると (指が指されているときだけではなく)、ハンド検出が発生します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-189">On HoloLens 2 , hands detected fires whenever hands are visible (not just when a finger is pointing up).</span></span>

### <a name="instructions"></a><span data-ttu-id="11dcb-190">手順</span><span class="sxs-lookup"><span data-stu-id="11dcb-190">Instructions</span></span>

* <span data-ttu-id="11dcb-191">[ **階層** ] パネルで、[ **inputmanager** ] オブジェクトを展開します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-191">In the **Hierarchy** panel, expand the **InputManager** object.</span></span>
* <span data-ttu-id="11dcb-192">**GesturesInput** オブジェクトを探して選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-192">Look for and select the **GesturesInput** object.</span></span>

<span data-ttu-id="11dcb-193">**InteractionInputSource.cs** スクリプトは、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-193">The **InteractionInputSource.cs** script performs these steps:</span></span>

1. <span data-ttu-id="11dcb-194">Interactionsourcedetected イベントと Interactionsourcedetected イベントをサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-194">Subscribes to the InteractionSourceDetected and InteractionSourceLost events.</span></span>
2. <span data-ttu-id="11dcb-195">"ハンドラー検出" 状態を設定します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-195">Sets the HandDetected state.</span></span>
3. <span data-ttu-id="11dcb-196">Interactionsourcedetected イベントと Interactionsourcedetected イベントからアンサブスクライブします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-196">Unsubscribes from the InteractionSourceDetected and InteractionSourceLost events.</span></span>

<span data-ttu-id="11dcb-197">次に、ユーザーの操作に応じてフィードバックが表示されるように、 [MR 入力 210](holograms-210.md) からカーソルをアップグレードします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-197">Next, we'll upgrade our cursor from [MR Input 210](holograms-210.md) into one that shows feedback depending on the user's actions.</span></span>

1. <span data-ttu-id="11dcb-198">[ **階層** ] パネルで、 **カーソル** オブジェクトを選択して削除します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-198">In the **Hierarchy** panel, select the **Cursor** object and delete it.</span></span>
2. <span data-ttu-id="11dcb-199">[ **プロジェクト** ] パネルで、[ **カーソルとフィードバック** ] を検索し、[ **階層** ] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-199">In the **Project** panel, search for **CursorWithFeedback** and drag it into the **Hierarchy** panel.</span></span>
3. <span data-ttu-id="11dcb-200">[**階層**] パネルの [ **inputmanager** ] をクリックし、[カーソル] の下 **にある [** カーソル] フィールドを、**階層** から Inputmanager の **simplesingleポインターセレクター** の **カーソル** フィールドにドラッグし **ます。**</span><span class="sxs-lookup"><span data-stu-id="11dcb-200">Click on **InputManager** in the **Hierarchy** panel, then drag the **CursorWithFeedback** object from the **Hierarchy** into the InputManager's **SimpleSinglePointerSelector**'s **Cursor** field, at the bottom of the **Inspector**.</span></span>
4. <span data-ttu-id="11dcb-201">**階層** 内の **カーソル** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-201">Click on the **CursorWithFeedback** in the **Hierarchy**.</span></span>
5. <span data-ttu-id="11dcb-202">[**インスペクター** ] パネルで、**オブジェクトカーソル** スクリプトの [**カーソル状態データ**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-202">In the **Inspector** panel, expand **Cursor State Data** on the **Object Cursor** script.</span></span>

<span data-ttu-id="11dcb-203">**カーソル状態データ** は次のように動作します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-203">The **Cursor State Data** works like this:</span></span>

* <span data-ttu-id="11dcb-204">**観察** 状態は、何も検出されず、ユーザーが単に見ていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-204">Any **Observe** state means that no hand is detected and the user is simply looking around.</span></span>
* <span data-ttu-id="11dcb-205">**対話** 状態とは、手動またはコントローラーが検出されたことを意味します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-205">Any **Interact** state means that a hand or controller is detected.</span></span>
* <span data-ttu-id="11dcb-206">**ホバー** 状態は、ユーザーがホログラムを見ていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-206">Any **Hover** state means the user is looking at a hologram.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="11dcb-207">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="11dcb-207">Build and Deploy</span></span>

* <span data-ttu-id="11dcb-208">Unity では、 **ファイル > ビルド設定** を使用して、アプリケーションをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-208">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="11dcb-209">**アプリ** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-209">Open the **App** folder.</span></span>
* <span data-ttu-id="11dcb-210">まだ開いていない場合は、 **Modelexplorer Visual Studio ソリューション** を開きます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-210">If it's not already open, open the **ModelExplorer Visual Studio Solution**.</span></span>
  * <span data-ttu-id="11dcb-211">(セットアップ時に Visual Studio でこのプロジェクトを既にビルドまたは展開している場合は、VS のインスタンスを開いて、メッセージが表示されたら [すべて再読み込み] をクリックします)。</span><span class="sxs-lookup"><span data-stu-id="11dcb-211">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>
* <span data-ttu-id="11dcb-212">Visual Studio で、[デバッグ]、[ **デバッグなしで開始** ] の順にクリック >、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-212">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5**.</span></span>
* <span data-ttu-id="11dcb-213">アプリケーションが HoloLens にデプロイされたら、エアタップジェスチャを使用して、[fitbox ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-213">After the application deploys to the HoloLens, dismiss the fitbox using the air-tap gesture.</span></span>
* <span data-ttu-id="11dcb-214">手動での追跡を開始するには、自分をビューに移動して、インデックスの指を空にします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-214">Move your hand into view and point your index finger to the sky to start hand tracking.</span></span>
* <span data-ttu-id="11dcb-215">左、右、下へ移動します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-215">Move your hand left, right, up and down.</span></span>
* <span data-ttu-id="11dcb-216">ハンドが検出され、ビューから失われたときに、カーソルがどのように変化するかを見てください。</span><span class="sxs-lookup"><span data-stu-id="11dcb-216">Watch how the cursor changes when your hand is detected and then lost from view.</span></span>
* <span data-ttu-id="11dcb-217">イマーシブヘッドセットを使用している場合は、コントローラーに接続して接続を切断する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11dcb-217">If you're on an immersive headset, you'll have to connect and disconnect your controller.</span></span> <span data-ttu-id="11dcb-218">接続されたコントローラーは常に "利用可能" になるため、このフィードバックはイマーシブデバイスではあまり興味がありません。</span><span class="sxs-lookup"><span data-stu-id="11dcb-218">This feedback becomes less interesting on an immersive device, as a connected controller will always be "available".</span></span>

## <a name="chapter-2---navigation"></a><span data-ttu-id="11dcb-219">第2章-ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="11dcb-219">Chapter 2 - Navigation</span></span>

>[!VIDEO https://www.youtube.com/embed/sm-kxtKksSo]

### <a name="objectives"></a><span data-ttu-id="11dcb-220">目標</span><span class="sxs-lookup"><span data-stu-id="11dcb-220">Objectives</span></span>

* <span data-ttu-id="11dcb-221">Astronaut を回転させるには、ナビゲーションジェスチャイベントを使用します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-221">Use Navigation gesture events to rotate the astronaut.</span></span>

### <a name="instructions"></a><span data-ttu-id="11dcb-222">手順</span><span class="sxs-lookup"><span data-stu-id="11dcb-222">Instructions</span></span>

<span data-ttu-id="11dcb-223">アプリでナビゲーションジェスチャを使用するには、 **GestureAction.cs** を編集して、ナビゲーションジェスチャが発生したときにオブジェクトを回転させます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-223">To use Navigation gestures in our app, we are going to edit **GestureAction.cs** to rotate objects when the Navigation gesture occurs.</span></span> <span data-ttu-id="11dcb-224">また、ナビゲーションが利用可能になったときに表示されるように、カーソルにフィードバックを追加します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-224">Additionally, we'll add feedback to the cursor to display when Navigation is available.</span></span>

1. <span data-ttu-id="11dcb-225">[ **階層** ] パネルで、[ **カーソルとフィードバック**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-225">In the **Hierarchy** panel, expand **CursorWithFeedback**.</span></span>
2. <span data-ttu-id="11dcb-226">**ホログラム** フォルダーで、 **scrollfeedback** 資産を見つけます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-226">In the **Holograms** folder, find the **ScrollFeedback** asset.</span></span>
3. <span data-ttu-id="11dcb-227">**スクロールフィードバック** の Prefab を **階層** 内の **カーソル** にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-227">Drag and drop the **ScrollFeedback** prefab onto the **CursorWithFeedback** GameObject in the **Hierarchy**.</span></span>
4. <span data-ttu-id="11dcb-228">[ **カーソル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-228">Click on **CursorWithFeedback**.</span></span>
5. <span data-ttu-id="11dcb-229">[ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-229">In the **Inspector** panel, click the **Add Component** button.</span></span>
6. <span data-ttu-id="11dcb-230">メニューで、検索ボックスに「カーソルの **フィードバック**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-230">In the menu, type in the search box **CursorFeedback**.</span></span> <span data-ttu-id="11dcb-231">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-231">Select the search result.</span></span>
7. <span data-ttu-id="11dcb-232">**インスペクター** の [ **Cursor フィードバック**] コンポーネントの [**検出されたゲームオブジェクトをスクロール**] プロパティに、**階層** から **scrollfeedback** オブジェクトをドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-232">Drag and drop the **ScrollFeedback** object from the **Hierarchy** onto the **Scroll Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>
8. <span data-ttu-id="11dcb-233">[ **階層** ] パネルで、 **AstroMan** オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-233">In the **Hierarchy** panel, select the **AstroMan** object.</span></span>
9. <span data-ttu-id="11dcb-234">[ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-234">In the **Inspector** panel, click the **Add Component** button.</span></span>
10. <span data-ttu-id="11dcb-235">メニューで、[検索ボックスのジェスチャ] **アクション** を入力します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-235">In the menu, type in the search box **Gesture Action**.</span></span> <span data-ttu-id="11dcb-236">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-236">Select the search result.</span></span>

<span data-ttu-id="11dcb-237">次に、Visual Studio で **GestureAction.cs** を開きます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-237">Next, open **GestureAction.cs** in Visual Studio.</span></span> <span data-ttu-id="11dcb-238">演習 2. c のコーディングで、スクリプトを編集して次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-238">In coding exercise 2.c, edit the script to do the following:</span></span>

1. <span data-ttu-id="11dcb-239">ナビゲーションジェスチャが実行されるたび **に、AstroMan オブジェクトを回転** します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-239">**Rotate the AstroMan** object whenever a Navigation gesture is performed.</span></span>
2. <span data-ttu-id="11dcb-240">**RotationFactor** を計算して、オブジェクトに適用される回転の量を制御します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-240">Calculate the **rotationFactor** to control the amount of rotation applied to the object.</span></span>
3. <span data-ttu-id="11dcb-241">ユーザーが手を左または右に移動したときに y 軸を中心に **オブジェクトを回転** します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-241">**Rotate the object** around the y-axis when the user moves their hand left or right.</span></span>

<span data-ttu-id="11dcb-242">スクリプトで演習 2. c のコーディングを完了するか、以下の完成したソリューションでコードを置き換えます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-242">Complete coding exercises 2.c in the script, or replace the code with the completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

<span data-ttu-id="11dcb-243">他のナビゲーションイベントには、何らかの情報が既に入力されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="11dcb-243">You'll notice that the other navigation events are already filled in with some info.</span></span> <span data-ttu-id="11dcb-244">ユーザーは、ローテーションが開始されたときに、ユーザーが Astronaut にフォーカスを保持する必要がないように、このオブジェクトを Toolkit の InputSystem's モーダルスタックにプッシュします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-244">We push the GameObject onto the Toolkit's InputSystem's modal stack, so the user doesn't have to maintain focus on the Astronaut once rotation has begun.</span></span> <span data-ttu-id="11dcb-245">同様に、ジェスチャが完了すると、そのオブジェクトはスタックからポップされます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-245">Correspondingly, we pop the GameObject off the stack once the gesture is completed.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="11dcb-246">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="11dcb-246">Build and Deploy</span></span>

1. <span data-ttu-id="11dcb-247">Unity でアプリケーションをリビルドし、Visual Studio からビルドしてデプロイし、HoloLens で実行します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-247">Rebuild the application in Unity and then build and deploy from Visual Studio to run it in the HoloLens.</span></span>
2. <span data-ttu-id="11dcb-248">Astronaut を見つめて、カーソルの両側に2つの矢印が表示されます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-248">Gaze at the astronaut, two arrows should appear on either side of the cursor.</span></span> <span data-ttu-id="11dcb-249">この新しいビジュアルは、astronaut を回転できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="11dcb-249">This new visual indicates that the astronaut can be rotated.</span></span>
3. <span data-ttu-id="11dcb-250">HoloLens がハンドの追跡を開始するように、自分を準備完了の位置 (インデックスは空の指) に置きます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-250">Place your hand in the ready position (index finger pointed towards the sky) so the HoloLens will start tracking your hand.</span></span>
4. <span data-ttu-id="11dcb-251">Astronaut を回転させるには、インデックスの指をピンチの位置に下げ、手を左または右に移動して NavigationX ジェスチャをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-251">To rotate the astronaut, lower your index finger to a pinch position, and then move your hand left or right to trigger the NavigationX gesture.</span></span>

## <a name="chapter-3---hand-guidance"></a><span data-ttu-id="11dcb-252">第3章-ガイダンス</span><span class="sxs-lookup"><span data-stu-id="11dcb-252">Chapter 3 - Hand Guidance</span></span>

>[!VIDEO https://www.youtube.com/embed/ULzlVw4e14I]

### <a name="objectives"></a><span data-ttu-id="11dcb-253">目標</span><span class="sxs-lookup"><span data-stu-id="11dcb-253">Objectives</span></span>

* <span data-ttu-id="11dcb-254">ハンド **ガイダンススコア** を使用して、ハンドトラッキングがいつ失われるかを予測できます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-254">Use **hand guidance score** to help predict when hand tracking will be lost.</span></span>
* <span data-ttu-id="11dcb-255">ユーザーがカメラのビューの端に近づいたときに表示されるように **、カーソルに関するフィードバック** を提供します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-255">Provide **feedback on the cursor** to show when the user's hand nears the camera's edge of view.</span></span>

### <a name="instructions"></a><span data-ttu-id="11dcb-256">手順</span><span class="sxs-lookup"><span data-stu-id="11dcb-256">Instructions</span></span>

1. <span data-ttu-id="11dcb-257">[ **階層** ] パネルで、[ **カーソルとフィードバック** ] オブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-257">In the **Hierarchy** panel, select the **CursorWithFeedback** object.</span></span>
2. <span data-ttu-id="11dcb-258">[ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-258">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="11dcb-259">メニューの [検索] ボックスに「」と **入力します。**</span><span class="sxs-lookup"><span data-stu-id="11dcb-259">In the menu, type in the search box **Hand Guidance**.</span></span> <span data-ttu-id="11dcb-260">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-260">Select the search result.</span></span>
4. <span data-ttu-id="11dcb-261">[ **プロジェクト** ] パネルの [ **ホログラム** ] フォルダーで、[ファイル] [ **guidguid] [フィードバック** ] 資産を見つけます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-261">In the **Project** panel **Holograms** folder, find the **HandGuidanceFeedback** asset.</span></span>
5. <span data-ttu-id="11dcb-262">[**インスペクター** ] パネルの [**ハンドガイダンスインジケーター** ] プロパティに、[ハンドラー] の [配布の **フィードバック**] 資産をドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-262">Drag and drop the **HandGuidanceFeedback** asset onto the **Hand Guidance Indicator** property in the **Inspector** panel.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="11dcb-263">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="11dcb-263">Build and Deploy</span></span>

* <span data-ttu-id="11dcb-264">Unity でアプリケーションをリビルドし、Visual Studio からビルドしてデプロイし、HoloLens でアプリを体験します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-264">Rebuild the application in Unity and then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="11dcb-265">手の形にして、インデックスの指を見て追跡します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-265">Bring your hand into view and raise your index finger to get tracked.</span></span>
* <span data-ttu-id="11dcb-266">ナビゲーションジェスチャを使用して astronaut の回転を開始します (インデックスの指とつまみを一緒にピンチします)。</span><span class="sxs-lookup"><span data-stu-id="11dcb-266">Start rotating the astronaut with the Navigation gesture (pinch your index finger and thumb together).</span></span>
* <span data-ttu-id="11dcb-267">左、右、上、下へ移動します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-267">Move your hand far left, right, up, and down.</span></span>
* <span data-ttu-id="11dcb-268">ジェスチャフレームの端に近づくと、カーソルの横に矢印が表示され、ハンドトラッキングが失われることを警告します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-268">As your hand nears the edge of the gesture frame, an arrow should appear next to the cursor to warn you that hand tracking will be lost.</span></span> <span data-ttu-id="11dcb-269">矢印は、追跡が失われないようにするために、どの方向にハンドを移動するかを示します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-269">The arrow indicates which direction to move your hand in order to prevent tracking from being lost.</span></span>

## <a name="chapter-4---manipulation"></a><span data-ttu-id="11dcb-270">章 4-操作</span><span class="sxs-lookup"><span data-stu-id="11dcb-270">Chapter 4 - Manipulation</span></span>

>[!VIDEO https://www.youtube.com/embed/f3m8MvU60-I]

### <a name="objectives"></a><span data-ttu-id="11dcb-271">目標</span><span class="sxs-lookup"><span data-stu-id="11dcb-271">Objectives</span></span>

* <span data-ttu-id="11dcb-272">操作イベントを使用して、astronaut を自分の手に移動します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-272">Use Manipulation events to move the astronaut with your hands.</span></span>
* <span data-ttu-id="11dcb-273">カーソルに関するフィードバックを提供して、操作を使用できるタイミングをユーザーに知らせます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-273">Provide feedback on the cursor to let the user know when Manipulation can be used.</span></span>

### <a name="instructions"></a><span data-ttu-id="11dcb-274">手順</span><span class="sxs-lookup"><span data-stu-id="11dcb-274">Instructions</span></span>

<span data-ttu-id="11dcb-275">GestureManager.cs と AstronautManager.cs では、次のことを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-275">GestureManager.cs and AstronautManager.cs will allow us to do the following:</span></span>

1. <span data-ttu-id="11dcb-276">Speech キーワード "**Move Astronaut**" を使用して **操作** ジェスチャを有効にし、"**Rotate Astronaut**" を使用して無効にします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-276">Use the speech keyword "**Move Astronaut**" to enable **Manipulation** gestures and "**Rotate Astronaut**" to disable them.</span></span>
2. <span data-ttu-id="11dcb-277">**操作ジェスチャレコグナイザー** に応答するように切り替えます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-277">Switch to responding to the **Manipulation Gesture Recognizer**.</span></span>

<span data-ttu-id="11dcb-278">始めましょう。</span><span class="sxs-lookup"><span data-stu-id="11dcb-278">Let's get started.</span></span>

1. <span data-ttu-id="11dcb-279">[ **階層** ] パネルで、新しい空の作成オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-279">In the **Hierarchy** panel, create a new empty GameObject.</span></span> <span data-ttu-id="11dcb-280">"**AstronautManager**" という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-280">Name it "**AstronautManager**".</span></span>
2. <span data-ttu-id="11dcb-281">[ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-281">In the **Inspector** panel, click the **Add Component** button.</span></span>
3. <span data-ttu-id="11dcb-282">メニューで、検索ボックスに「 **Astronaut Manager**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-282">In the menu, type in the search box **Astronaut Manager**.</span></span> <span data-ttu-id="11dcb-283">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-283">Select the search result.</span></span>
4. <span data-ttu-id="11dcb-284">[ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-284">In the **Inspector** panel, click the **Add Component** button.</span></span>
5. <span data-ttu-id="11dcb-285">メニューで、[検索] ボックスに「 **音声入力ソース**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-285">In the menu, type in the search box **Speech Input Source**.</span></span> <span data-ttu-id="11dcb-286">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-286">Select the search result.</span></span>

<span data-ttu-id="11dcb-287">ここで、astronaut の相互作用の状態を制御するために必要な音声コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-287">We'll now add the speech commands required to control the interaction state of the astronaut.</span></span>

1. <span data-ttu-id="11dcb-288">**インスペクター** の [**キーワード**] セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-288">Expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="11dcb-289">右側にあるをクリックして、 **+** 新しいキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-289">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="11dcb-290">「 **Move Astronaut**」というキーワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-290">Type the Keyword as **Move Astronaut**.</span></span> <span data-ttu-id="11dcb-291">必要に応じて、キーのショートカットを自由に追加できます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-291">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="11dcb-292">右側にあるをクリックして、 **+** 新しいキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-292">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="11dcb-293">「 **Rotate Astronaut**」というキーワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-293">Type the Keyword as **Rotate Astronaut**.</span></span> <span data-ttu-id="11dcb-294">必要に応じて、キーのショートカットを自由に追加できます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-294">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="11dcb-295">対応するハンドラーコードは、 **GestureAction.cs** の **ISpeechHandler** ハンドラーにあります。</span><span class="sxs-lookup"><span data-stu-id="11dcb-295">The corresponding handler code can be found in **GestureAction.cs**, in the **ISpeechHandler.OnSpeechKeywordRecognized** handler.</span></span>

![第4章の音声入力ソースを設定する方法](images/holograms211-speech.png)

<span data-ttu-id="11dcb-297">次に、カーソルに対する操作に関するフィードバックを設定します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-297">Next, we'll setup the manipulation feedback on the cursor.</span></span>

1. <span data-ttu-id="11dcb-298">[ **プロジェクト** パネル] の [ **ホログラム** ] フォルダーで、 **pathingfeedback** 資産を見つけます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-298">In the **Project** panel **Holograms** folder, find the **PathingFeedback** asset.</span></span>
2. <span data-ttu-id="11dcb-299">**Pathingfeedback** の Prefab を **階層** 内の **カーソル** にドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-299">Drag and drop the **PathingFeedback** prefab onto the **CursorWithFeedback** object in the **Hierarchy**.</span></span>
3. <span data-ttu-id="11dcb-300">[ **階層** ] パネルで、[ **カーソル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-300">In the **Hierarchy** panel, click on **CursorWithFeedback**.</span></span>
4. <span data-ttu-id="11dcb-301">**Pathingfeedback** オブジェクトを **階層** から、**インスペクター** の [ **Cursor フィードバック**] コンポーネントの [**パス検出されたゲームオブジェクト**] プロパティにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-301">Drag and drop the **PathingFeedback** object from the **Hierarchy** onto the **Pathing Detected Game Object** property in the **Cursor Feedback** component in the **Inspector**.</span></span>

<span data-ttu-id="11dcb-302">次のように、 **GestureAction.cs** にコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11dcb-302">Now we need to add code to **GestureAction.cs** to enable the following:</span></span>

1. <span data-ttu-id="11dcb-303">**IManipulationHandler** 関数にコードを追加します。この関数は、**操作** ジェスチャが検出されたときに astronaut を移動します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-303">Add code to the **IManipulationHandler.OnManipulationUpdated** function, which will move the astronaut when a **Manipulation** gesture is detected.</span></span>
2. <span data-ttu-id="11dcb-304">**移動ベクター** を計算して、astronaut が手の位置に基づいて移動される場所を決定します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-304">Calculate the **movement vector** to determine where the astronaut should be moved to based on hand position.</span></span>
3. <span data-ttu-id="11dcb-305">Astronaut を新しい位置に **移動** します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-305">**Move** the astronaut to the new position.</span></span>

<span data-ttu-id="11dcb-306">**GestureAction.cs** のコードを完全にコーディングするか、以下の完成したソリューションを使用します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-306">Complete coding exercise 4.a in **GestureAction.cs**, or use our completed solution below:</span></span>

```cs
using HoloToolkit.Unity.InputModule;
using UnityEngine;

/// <summary>
/// GestureAction performs custom actions based on
/// which gesture is being performed.
/// </summary>
public class GestureAction : MonoBehaviour, INavigationHandler, IManipulationHandler, ISpeechHandler
{
    [Tooltip("Rotation max speed controls amount of rotation.")]
    [SerializeField]
    private float RotationSensitivity = 10.0f;

    private bool isNavigationEnabled = true;
    public bool IsNavigationEnabled
    {
        get { return isNavigationEnabled; }
        set { isNavigationEnabled = value; }
    }

    private Vector3 manipulationOriginalPosition = Vector3.zero;

    void INavigationHandler.OnNavigationStarted(NavigationEventData eventData)
    {
        InputManager.Instance.PushModalInputHandler(gameObject);
    }

    void INavigationHandler.OnNavigationUpdated(NavigationEventData eventData)
    {
        if (isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 2.c */

            // 2.c: Calculate a float rotationFactor based on eventData's NormalizedOffset.x multiplied by RotationSensitivity.
            // This will help control the amount of rotation.
            float rotationFactor = eventData.NormalizedOffset.x * RotationSensitivity;

            // 2.c: transform.Rotate around the Y axis using rotationFactor.
            transform.Rotate(new Vector3(0, -1 * rotationFactor, 0));
        }
    }

    void INavigationHandler.OnNavigationCompleted(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void INavigationHandler.OnNavigationCanceled(NavigationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationStarted(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            InputManager.Instance.PushModalInputHandler(gameObject);

            manipulationOriginalPosition = transform.position;
        }
    }

    void IManipulationHandler.OnManipulationUpdated(ManipulationEventData eventData)
    {
        if (!isNavigationEnabled)
        {
            /* TODO: DEVELOPER CODING EXERCISE 4.a */

            // 4.a: Make this transform's position be the manipulationOriginalPosition + eventData.CumulativeDelta
            transform.position = manipulationOriginalPosition + eventData.CumulativeDelta;
        }
    }

    void IManipulationHandler.OnManipulationCompleted(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void IManipulationHandler.OnManipulationCanceled(ManipulationEventData eventData)
    {
        InputManager.Instance.PopModalInputHandler();
    }

    void ISpeechHandler.OnSpeechKeywordRecognized(SpeechEventData eventData)
    {
        if (eventData.RecognizedText.Equals("Move Astronaut"))
        {
            isNavigationEnabled = false;
        }
        else if (eventData.RecognizedText.Equals("Rotate Astronaut"))
        {
            isNavigationEnabled = true;
        }
        else
        {
            return;
        }

        eventData.Use();
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="11dcb-307">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="11dcb-307">Build and Deploy</span></span>

* <span data-ttu-id="11dcb-308">Unity でリビルドし、Visual Studio からビルドしてデプロイし、HoloLens でアプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-308">Rebuild in Unity and then build and deploy from Visual Studio to run the app in HoloLens.</span></span>
* <span data-ttu-id="11dcb-309">HoloLens の前に手を置き、インデックスの指を上げて追跡できるようにします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-309">Move your hand in front of the HoloLens and raise your index finger so that it can be tracked.</span></span>
* <span data-ttu-id="11dcb-310">Astronaut の上にカーソルを置きます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-310">Focus the cursor over the astronaut.</span></span>
* <span data-ttu-id="11dcb-311">操作ジェスチャを使用して Astronaut を移動するには、「Move Astronaut」と言います。</span><span class="sxs-lookup"><span data-stu-id="11dcb-311">Say 'Move Astronaut' to move the astronaut with a Manipulation gesture.</span></span>
* <span data-ttu-id="11dcb-312">カーソルの周囲に4つの矢印が表示され、プログラムが操作イベントに応答するようになったことを示します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-312">Four arrows should appear around the cursor to indicate that the program will now respond to Manipulation events.</span></span>
* <span data-ttu-id="11dcb-313">インデックスを親指に下げて、pinched にしておきます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-313">Lower your index finger down to your thumb, and keep them pinched together.</span></span>
* <span data-ttu-id="11dcb-314">お客様の手を移動すると、astronaut も移動します (これは操作です)。</span><span class="sxs-lookup"><span data-stu-id="11dcb-314">As you move your hand around, the astronaut will move too (this is Manipulation).</span></span>
* <span data-ttu-id="11dcb-315">Astronaut の操作を停止するには、インデックスの指を上げます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-315">Raise your index finger to stop manipulating the astronaut.</span></span>
* <span data-ttu-id="11dcb-316">注: 移動前に "Move Astronaut" と表示されない場合は、代わりにナビゲーションジェスチャが使用されます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-316">Note: If you do not say 'Move Astronaut' before moving your hand, then the Navigation gesture will be used instead.</span></span>
* <span data-ttu-id="11dcb-317">"Rotate Astronaut" と言い、rotatable 状態に戻ります。</span><span class="sxs-lookup"><span data-stu-id="11dcb-317">Say 'Rotate Astronaut' to return to the rotatable state.</span></span>

## <a name="chapter-5---model-expansion"></a><span data-ttu-id="11dcb-318">第5章-モデルの拡張</span><span class="sxs-lookup"><span data-stu-id="11dcb-318">Chapter 5 - Model expansion</span></span>

>[!VIDEO https://www.youtube.com/embed/dA11P4P0VO8]

### <a name="objectives"></a><span data-ttu-id="11dcb-319">目標</span><span class="sxs-lookup"><span data-stu-id="11dcb-319">Objectives</span></span>

* <span data-ttu-id="11dcb-320">Astronaut モデルを、ユーザーが対話できる複数の小さなピースに拡張します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-320">Expand the Astronaut model into multiple, smaller pieces that the user can interact with.</span></span>
* <span data-ttu-id="11dcb-321">ナビゲーションと操作のジェスチャを使用して、各部分を個別に移動します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-321">Move each piece individually using Navigation and Manipulation gestures.</span></span>

### <a name="instructions"></a><span data-ttu-id="11dcb-322">手順</span><span class="sxs-lookup"><span data-stu-id="11dcb-322">Instructions</span></span>

<span data-ttu-id="11dcb-323">このセクションでは、次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-323">In this section, we will accomplish the following tasks:</span></span>

1. <span data-ttu-id="11dcb-324">新しいキーワード "**Expand model**" を追加して、astronaut モデルを展開します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-324">Add a new keyword "**Expand Model**" to expand the astronaut model.</span></span>
2. <span data-ttu-id="11dcb-325">新しいキーワード "**Reset model**" を追加して、モデルを元の形式に戻します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-325">Add a new Keyword "**Reset Model**" to return the model to its original form.</span></span>

<span data-ttu-id="11dcb-326">これを行うには、前の章で説明した音声入力ソースに2つのキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-326">We'll do this by adding two more keywords to the Speech Input Source from the previous chapter.</span></span> <span data-ttu-id="11dcb-327">また、認識イベントを処理する別の方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-327">We'll also demonstrate another way to handle recognition events.</span></span>

1. <span data-ttu-id="11dcb-328">**インスペクター** の [Back on **AstronautManager** ] をクリックし、**インスペクター** の [**キーワード**] セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-328">Click back on **AstronautManager** in the **Inspector** and expand the **Keywords** section in the **Inspector**.</span></span>
2. <span data-ttu-id="11dcb-329">右側にあるをクリックして、 **+** 新しいキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-329">Click the **+** on the right hand side to add a new keyword.</span></span>
3. <span data-ttu-id="11dcb-330">[ **モデルの展開**] としてキーワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-330">Type the Keyword as **Expand Model**.</span></span> <span data-ttu-id="11dcb-331">必要に応じて、キーのショートカットを自由に追加できます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-331">Feel free to add a Key Shortcut if desired.</span></span>
4. <span data-ttu-id="11dcb-332">右側にあるをクリックして、 **+** 新しいキーワードを追加します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-332">Click the **+** on the right hand side to add a new keyword.</span></span>
5. <span data-ttu-id="11dcb-333">「 **Reset Model**」というキーワードを入力します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-333">Type the Keyword as **Reset Model**.</span></span> <span data-ttu-id="11dcb-334">必要に応じて、キーのショートカットを自由に追加できます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-334">Feel free to add a Key Shortcut if desired.</span></span>
6. <span data-ttu-id="11dcb-335">[ **インスペクター** ] パネルで、[ **コンポーネントの追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-335">In the **Inspector** panel, click the **Add Component** button.</span></span>
7. <span data-ttu-id="11dcb-336">メニューで、[検索] ボックスに「 **音声入力ハンドラー**」と入力します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-336">In the menu, type in the search box **Speech Input Handler**.</span></span> <span data-ttu-id="11dcb-337">検索結果を選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-337">Select the search result.</span></span>
8. <span data-ttu-id="11dcb-338">これらのコマンドは、注目しているすべてのオブジェクトに関係なく動作するようにするため、 **グローバルリスナーである** ことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="11dcb-338">Check **Is Global Listener**, since we want these commands to work regardless of the GameObject we're focusing.</span></span>
9. <span data-ttu-id="11dcb-339">ボタンをクリックし、[ **+** キーワード] ドロップダウンから [ **モデルの展開** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-339">Click the **+** button and select **Expand Model** from the Keyword dropdown.</span></span>
10. <span data-ttu-id="11dcb-340">[応答] の下をクリック **+** し、 **AstronautManager** を **階層** から [ **なし] (オブジェクト)** フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-340">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
11. <span data-ttu-id="11dcb-341">次に、[ **関数なし** ] ドロップダウンをクリックし、[ **AstronautManager**]、[ **expandmodelcommand**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-341">Now, click the **No Function** dropdown, select **AstronautManager**, then **ExpandModelCommand**.</span></span>
12. <span data-ttu-id="11dcb-342">音声入力ハンドラーの **+** ボタンをクリックし、[キーワード] ドロップダウンから [ **モデルのリセット** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-342">Click the Speech Input Handler's **+** button and select **Reset Model** from the Keyword dropdown.</span></span>
13. <span data-ttu-id="11dcb-343">[応答] の下をクリック **+** し、 **AstronautManager** を **階層** から [ **なし] (オブジェクト)** フィールドにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-343">Click the **+** under Response, and drag the **AstronautManager** from the **Hierarchy** into the **None (Object)** field.</span></span>
14. <span data-ttu-id="11dcb-344">次に、[ **関数なし** ] ドロップダウンをクリックし、[ **AstronautManager**]、[ **resetmodelcommand**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-344">Now, click the **No Function** dropdown, select **AstronautManager**, then **ResetModelCommand**.</span></span>

![第5章の音声入力ソースとハンドラーを設定する方法](images/holograms211-speechhandler.png)

### <a name="build-and-deploy"></a><span data-ttu-id="11dcb-346">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="11dcb-346">Build and Deploy</span></span>

* <span data-ttu-id="11dcb-347">試してみる</span><span class="sxs-lookup"><span data-stu-id="11dcb-347">Try it!</span></span> <span data-ttu-id="11dcb-348">アプリをビルドして HoloLens にデプロイします。</span><span class="sxs-lookup"><span data-stu-id="11dcb-348">Build and deploy the app to the HoloLens.</span></span>
* <span data-ttu-id="11dcb-349">拡張された astronaut モデルを表示するには、[ **モデルの展開** ] を言います。</span><span class="sxs-lookup"><span data-stu-id="11dcb-349">Say **Expand Model** to see the expanded astronaut model.</span></span>
* <span data-ttu-id="11dcb-350">**ナビゲーション** を使用して、astronaut スーツの個々の要素を回転します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-350">Use **Navigation** to rotate individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="11dcb-351">たとえば、 **Astronaut を移動** してから、 **操作** を使用して Astronaut スーツの各部分を移動します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-351">Say **Move Astronaut** and then use **Manipulation** to move individual pieces of the astronaut suit.</span></span>
* <span data-ttu-id="11dcb-352">**Astronaut を回転** させて、ピースを再び回転させます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-352">Say **Rotate Astronaut** to rotate the pieces again.</span></span>
* <span data-ttu-id="11dcb-353">Astronaut を元の形式に戻すには、 **Model をリセット** します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-353">Say **Reset Model** to return the astronaut to its original form.</span></span>

## <a name="the-end"></a><span data-ttu-id="11dcb-354">最後です</span><span class="sxs-lookup"><span data-stu-id="11dcb-354">The End</span></span>

<span data-ttu-id="11dcb-355">おめでとうございます。</span><span class="sxs-lookup"><span data-stu-id="11dcb-355">Congratulations!</span></span> <span data-ttu-id="11dcb-356">これで **MR 入力 211: ジェスチャ** が完了しました。</span><span class="sxs-lookup"><span data-stu-id="11dcb-356">You have now completed **MR Input 211: Gesture**.</span></span>

* <span data-ttu-id="11dcb-357">ハンドトラッキング、ナビゲーション、操作のイベントを検出して対応する方法がわかります。</span><span class="sxs-lookup"><span data-stu-id="11dcb-357">You know how to detect and respond to hand tracking, navigation and manipulation events.</span></span>
* <span data-ttu-id="11dcb-358">ナビゲーションジェスチャと操作ジェスチャの違いを理解します。</span><span class="sxs-lookup"><span data-stu-id="11dcb-358">You understand the difference between Navigation and Manipulation gestures.</span></span>
* <span data-ttu-id="11dcb-359">カーソルを変更して、ハンドが検出されたとき、ハンドが失われるタイミング、およびオブジェクトが異なる相互作用 (ナビゲーションと操作) をサポートするタイミングについて視覚的にフィードバックを提供する方法を理解している。</span><span class="sxs-lookup"><span data-stu-id="11dcb-359">You know how to change the cursor to provide visual feedback for when a hand is detected, when a hand is about to be lost, and for when an object supports different interactions (Navigation vs Manipulation).</span></span>