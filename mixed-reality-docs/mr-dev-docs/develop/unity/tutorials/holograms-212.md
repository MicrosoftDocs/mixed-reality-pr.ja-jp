---
title: MR 入力 212-音声
description: ここでは、Unity、Visual Studio、および HoloLens を使用したこのコーディングのチュートリアルに従って、音声の概念の詳細について説明します。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、academy、チュートリアル、音声
ms.openlocfilehash: ed37ef6e0c26c3d2a0cd2d51e18d01a258b2fc78
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91686418"
---
# <a name="mr-input-212-voice"></a><span data-ttu-id="1182b-104">MR 入力 212:音声</span><span class="sxs-lookup"><span data-stu-id="1182b-104">MR Input 212: Voice</span></span>

>[!NOTE]
><span data-ttu-id="1182b-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="1182b-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="1182b-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="1182b-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="1182b-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。</span><span class="sxs-lookup"><span data-stu-id="1182b-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="1182b-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="1182b-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="1182b-109">HoloLens 2 向けには、[新しいチュートリアル シリーズ](../../../mr-learning-base-01.md)が投稿されています。</span><span class="sxs-lookup"><span data-stu-id="1182b-109">[A new series of tutorials](../../../mr-learning-base-01.md) has been posted for HoloLens 2.</span></span>

<span data-ttu-id="1182b-110">[音声入力](../../../design/voice-input.md) によって、ホログラムを操作するもう1つの方法が提供されます。</span><span class="sxs-lookup"><span data-stu-id="1182b-110">[Voice input](../../../design/voice-input.md) gives us another way to interact with our holograms.</span></span> <span data-ttu-id="1182b-111">音声コマンドは、非常に自然で簡単な方法で動作します。</span><span class="sxs-lookup"><span data-stu-id="1182b-111">Voice commands work in a very natural and easy way.</span></span> <span data-ttu-id="1182b-112">次のような音声コマンドを設計します。</span><span class="sxs-lookup"><span data-stu-id="1182b-112">Design your voice commands so that they are:</span></span>

* <span data-ttu-id="1182b-113">Natural</span><span class="sxs-lookup"><span data-stu-id="1182b-113">Natural</span></span>
* <span data-ttu-id="1182b-114">覚えやすい</span><span class="sxs-lookup"><span data-stu-id="1182b-114">Easy to remember</span></span>
* <span data-ttu-id="1182b-115">適切なコンテキスト</span><span class="sxs-lookup"><span data-stu-id="1182b-115">Context appropriate</span></span>
* <span data-ttu-id="1182b-116">同じコンテキスト内の他のオプションと十分に異なる</span><span class="sxs-lookup"><span data-stu-id="1182b-116">Sufficiently distinct from other options within the same context</span></span>

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

<span data-ttu-id="1182b-117">[MR 基本 101](../../../develop/unity/tutorials/holograms-101.md)では、KeywordRecognizer を使用して、2つの簡単な音声コマンドを作成していました。</span><span class="sxs-lookup"><span data-stu-id="1182b-117">In [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), we used the KeywordRecognizer to build two simple voice commands.</span></span> <span data-ttu-id="1182b-118">MR 入力212では、次の方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="1182b-118">In MR Input 212, we'll dive deeper and learn how to:</span></span>

* <span data-ttu-id="1182b-119">HoloLens speech エンジン用に最適化された音声コマンドを設計します。</span><span class="sxs-lookup"><span data-stu-id="1182b-119">Design voice commands that are optimized for the HoloLens speech engine.</span></span>
* <span data-ttu-id="1182b-120">使用できる音声コマンドをユーザーが認識できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1182b-120">Make the user aware of what voice commands are available.</span></span>
* <span data-ttu-id="1182b-121">ユーザーの声コマンドを聞いたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="1182b-121">Acknowledge that we've heard the user's voice command.</span></span>
* <span data-ttu-id="1182b-122">ディクテーション認識エンジンを使用して、ユーザーが言っている内容を理解します。</span><span class="sxs-lookup"><span data-stu-id="1182b-122">Understand what the user is saying, using a Dictation Recognizer.</span></span>
* <span data-ttu-id="1182b-123">構文認識エンジンを使用して、SRGS、または音声認識文法仕様 (ファイル) に基づいてコマンドをリッスンします。</span><span class="sxs-lookup"><span data-stu-id="1182b-123">Use a Grammar Recognizer to listen for commands based on an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

<span data-ttu-id="1182b-124">このコースでは、 [Mr 入力 210](holograms-210.md) および [mr 入力 211](holograms-211.md)で構築したモデルエクスプローラーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1182b-124">In this course, we'll revisit Model Explorer, which we built in [MR Input 210](holograms-210.md) and [MR Input 211](holograms-211.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="1182b-125">以下の各章に埋め込まれているビデオは、古いバージョンの Unity と Mixed Reality Toolkit を使用して記録されています。</span><span class="sxs-lookup"><span data-stu-id="1182b-125">The videos embedded in each of the chapters below were recorded using an older version of Unity and the Mixed Reality Toolkit.</span></span> <span data-ttu-id="1182b-126">ステップバイステップの手順は正確であり、最新のものですが、最新ではない対応するビデオにスクリプトとビジュアルが表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="1182b-126">While the step-by-step instructions are accurate and current, you may see scripts and visuals in the corresponding videos that are out-of-date.</span></span> <span data-ttu-id="1182b-127">ビデオはために含まれています。ここで説明する概念は引き続き適用されます。</span><span class="sxs-lookup"><span data-stu-id="1182b-127">The videos remain included for posterity and because the concepts covered still apply.</span></span>


## <a name="device-support"></a><span data-ttu-id="1182b-128">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="1182b-128">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="1182b-129">コース</span><span class="sxs-lookup"><span data-stu-id="1182b-129">Course</span></span></th><th style="width:150px"> <span data-ttu-id="1182b-130"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="1182b-130"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="1182b-131"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="1182b-131"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="1182b-132">MR 入力 212:音声</span><span class="sxs-lookup"><span data-stu-id="1182b-132">MR Input 212: Voice</span></span></td><td style="text-align: center;"> <span data-ttu-id="1182b-133">✔️</span><span class="sxs-lookup"><span data-stu-id="1182b-133">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="1182b-134">✔️</span><span class="sxs-lookup"><span data-stu-id="1182b-134">✔️</span></span></td>
</tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="1182b-135">開始する前に</span><span class="sxs-lookup"><span data-stu-id="1182b-135">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="1182b-136">前提条件</span><span class="sxs-lookup"><span data-stu-id="1182b-136">Prerequisites</span></span>

* <span data-ttu-id="1182b-137">適切な [ツールがインストール](../../../develop/install-the-tools.md)された WINDOWS 10 PC。</span><span class="sxs-lookup"><span data-stu-id="1182b-137">A Windows 10 PC configured with the correct [tools installed](../../../develop/install-the-tools.md).</span></span>
* <span data-ttu-id="1182b-138">基本的な C# プログラミング機能。</span><span class="sxs-lookup"><span data-stu-id="1182b-138">Some basic C# programming ability.</span></span>
* <span data-ttu-id="1182b-139">[MR の基本 101](../../../develop/unity/tutorials/holograms-101.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="1182b-139">You should have completed [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).</span></span>
* <span data-ttu-id="1182b-140">[MR 入力 210](holograms-210.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="1182b-140">You should have completed [MR Input 210](holograms-210.md).</span></span>
* <span data-ttu-id="1182b-141">[MR 入力 211](holograms-211.md)を完了している必要があります。</span><span class="sxs-lookup"><span data-stu-id="1182b-141">You should have completed [MR Input 211](holograms-211.md).</span></span>
* <span data-ttu-id="1182b-142">[開発用に構成され](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)た HoloLens デバイス。</span><span class="sxs-lookup"><span data-stu-id="1182b-142">A HoloLens device [configured for development](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode).</span></span>

### <a name="project-files"></a><span data-ttu-id="1182b-143">プロジェクト ファイル</span><span class="sxs-lookup"><span data-stu-id="1182b-143">Project files</span></span>

* <span data-ttu-id="1182b-144">プロジェクトに必要な [ファイル](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="1182b-144">Download the [files](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) required by the project.</span></span> <span data-ttu-id="1182b-145">Unity 2017.2 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="1182b-145">Requires Unity 2017.2 or later.</span></span>
* <span data-ttu-id="1182b-146">ファイルをデスクトップまたはその他の簡単な場所に保管します。</span><span class="sxs-lookup"><span data-stu-id="1182b-146">Un-archive the files to your desktop or other easy to reach location.</span></span>

>[!NOTE]
><span data-ttu-id="1182b-147">ダウンロードする前にソースコードを確認する場合は、GitHub から [入手でき](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice)ます。</span><span class="sxs-lookup"><span data-stu-id="1182b-147">If you want to look through the source code before downloading, it's [available on GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).</span></span>

### <a name="errata-and-notes"></a><span data-ttu-id="1182b-148">エラッタとメモ</span><span class="sxs-lookup"><span data-stu-id="1182b-148">Errata and Notes</span></span>

* <span data-ttu-id="1182b-149">コード内のブレークポイントにヒットするには、Visual Studio の [ツール]->オプション->デバッグ] の下にある [マイコードのみを有効にする] を無効 ( *オフ* ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1182b-149">"Enable Just My Code" needs to be disabled ( *unchecked* ) in Visual Studio under Tools->Options->Debugging in order to hit breakpoints in your code.</span></span>

## <a name="unity-setup"></a><span data-ttu-id="1182b-150">Unity のセットアップ</span><span class="sxs-lookup"><span data-stu-id="1182b-150">Unity Setup</span></span>

### <a name="instructions"></a><span data-ttu-id="1182b-151">Instructions</span><span class="sxs-lookup"><span data-stu-id="1182b-151">Instructions</span></span>

1. <span data-ttu-id="1182b-152">Unity を起動します。</span><span class="sxs-lookup"><span data-stu-id="1182b-152">Start Unity.</span></span>
2. <span data-ttu-id="1182b-153">**[Open (開く)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="1182b-153">Select **Open** .</span></span>
3. <span data-ttu-id="1182b-154">以前にアーカイブしていた **HolographicAcademy-212-Voice** フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="1182b-154">Navigate to the **HolographicAcademy-Holograms-212-Voice** folder you previously un-archived.</span></span>
4. <span data-ttu-id="1182b-155">[モデルエクスプローラーの **開始** ] フォルダーを見つけて選択し / **Model Explorer** ます。</span><span class="sxs-lookup"><span data-stu-id="1182b-155">Find and select the **Starting**/**Model Explorer** folder.</span></span>
5. <span data-ttu-id="1182b-156">[ **フォルダーの選択** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1182b-156">Click the **Select Folder** button.</span></span>
6. <span data-ttu-id="1182b-157">[ **プロジェクト** ] パネルで、[ **シーン** ] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="1182b-157">In the **Project** panel, expand the **Scenes** folder.</span></span>
7. <span data-ttu-id="1182b-158">[ **Modelexplorer** シーン] をダブルクリックして Unity に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="1182b-158">Double-click **ModelExplorer** scene to load it in Unity.</span></span>

### <a name="building"></a><span data-ttu-id="1182b-159">ビルド</span><span class="sxs-lookup"><span data-stu-id="1182b-159">Building</span></span>

1. <span data-ttu-id="1182b-160">Unity で、[ **ファイル > ビルド設定** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1182b-160">In Unity, select **File > Build Settings** .</span></span>
2. <span data-ttu-id="1182b-161">シーン **/ModelExplorer** が [ **ビルド] の [シーン** ] に表示されていない場合は、[開いているシーンの **追加** ] をクリックしてシーンを追加します。</span><span class="sxs-lookup"><span data-stu-id="1182b-161">If **Scenes/ModelExplorer** is not listed in **Scenes In Build** , click **Add Open Scenes** to add the scene.</span></span>
3. <span data-ttu-id="1182b-162">HoloLens 向けに特に開発している場合は、 **ターゲットデバイス** を **hololens** に設定します。</span><span class="sxs-lookup"><span data-stu-id="1182b-162">If you're specifically developing for HoloLens, set **Target device** to **HoloLens** .</span></span> <span data-ttu-id="1182b-163">それ以外の場合は、 **任意のデバイス** に残しておきます。</span><span class="sxs-lookup"><span data-stu-id="1182b-163">Otherwise, leave it on **Any device** .</span></span>
4. <span data-ttu-id="1182b-164">**ビルドの種類** が [ **D3D** ] に設定され、[ **sdk** ] が [ **最新のインストール済み** ] に設定されていることを確認します (sdk 16299 以降である必要があります)。</span><span class="sxs-lookup"><span data-stu-id="1182b-164">Ensure **Build Type** is set to **D3D** and **SDK** is set to **Latest installed** (which should be SDK 16299 or newer).</span></span>
5. <span data-ttu-id="1182b-165">[ **ビルド** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1182b-165">Click **Build** .</span></span>
6. <span data-ttu-id="1182b-166">"App" という名前の **新しいフォルダー** を作成します。</span><span class="sxs-lookup"><span data-stu-id="1182b-166">Create a **New Folder** named "App".</span></span>
7. <span data-ttu-id="1182b-167">**アプリ** フォルダーをシングルクリックします。</span><span class="sxs-lookup"><span data-stu-id="1182b-167">Single click the **App** folder.</span></span>
8. <span data-ttu-id="1182b-168">**[フォルダーの選択]** をクリックすると、Unity によって Visual Studio のプロジェクトのビルドが開始されます。</span><span class="sxs-lookup"><span data-stu-id="1182b-168">Press **Select Folder** and Unity will start building the project for Visual Studio.</span></span>

<span data-ttu-id="1182b-169">Unity が完了すると、エクスプローラーウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="1182b-169">When Unity is done, a File Explorer window will appear.</span></span>

1. <span data-ttu-id="1182b-170">**アプリ** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="1182b-170">Open the **App** folder.</span></span>
2. <span data-ttu-id="1182b-171">**Modelexplorer Visual Studio ソリューション** を開きます。</span><span class="sxs-lookup"><span data-stu-id="1182b-171">Open the **ModelExplorer Visual Studio Solution** .</span></span>

<span data-ttu-id="1182b-172">HoloLens に展開する場合:</span><span class="sxs-lookup"><span data-stu-id="1182b-172">If deploying to HoloLens:</span></span>

1. <span data-ttu-id="1182b-173">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に変更し、ARM から **x86** に変更します。</span><span class="sxs-lookup"><span data-stu-id="1182b-173">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x86** .</span></span>
2. <span data-ttu-id="1182b-174">[ローカルコンピューター] ボタンの横にあるドロップダウン矢印をクリックし、[ **リモートコンピューター** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1182b-174">Click on the drop down arrow next to the Local Machine button, and select **Remote Machine** .</span></span>
3. <span data-ttu-id="1182b-175">**HoloLens デバイスの IP アドレス** を入力し、[認証モード] を [ **ユニバーサル (暗号化** されていないプロトコル)] に設定します。</span><span class="sxs-lookup"><span data-stu-id="1182b-175">Enter **your HoloLens device IP address** and set Authentication Mode to **Universal (Unencrypted Protocol)** .</span></span> <span data-ttu-id="1182b-176">**[選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1182b-176">Click **Select** .</span></span> <span data-ttu-id="1182b-177">デバイスの IP アドレスがわからない場合は、[ **設定] [Network & Internet > 詳細オプション >** 確認してください。</span><span class="sxs-lookup"><span data-stu-id="1182b-177">If you do not know your device IP address, look in **Settings > Network & Internet > Advanced Options** .</span></span>
4. <span data-ttu-id="1182b-178">上部のメニューバーで、[デバッグ]、[ **デバッグなしで開始** ] の順にクリック >、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1182b-178">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5** .</span></span> <span data-ttu-id="1182b-179">初めてデバイスをデプロイする場合は、 [Visual Studio とペアリング](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device)する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1182b-179">If this is the first time deploying to your device, you will need to [pair it with Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).</span></span>
5. <span data-ttu-id="1182b-180">アプリが展開されたら、 **select ジェスチャ** を使用して、[ **fitbox** ] を閉じます。</span><span class="sxs-lookup"><span data-stu-id="1182b-180">When the app has deployed, dismiss the **Fitbox** with a **select gesture** .</span></span>

<span data-ttu-id="1182b-181">イマーシブヘッドセットに展開する場合:</span><span class="sxs-lookup"><span data-stu-id="1182b-181">If deploying to an immersive headset:</span></span>

1. <span data-ttu-id="1182b-182">Visual Studio の上部のツールバーを使用して、ターゲットをデバッグから **リリース** に、ARM から **x64** に変更します。</span><span class="sxs-lookup"><span data-stu-id="1182b-182">Using the top toolbar in Visual Studio, change the target from Debug to **Release** and from ARM to **x64** .</span></span>
2. <span data-ttu-id="1182b-183">配置ターゲットが **ローカルコンピューター** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1182b-183">Make sure the deployment target is set to **Local Machine** .</span></span>
3. <span data-ttu-id="1182b-184">上部のメニューバーで、[デバッグ]、[ **デバッグなしで開始** ] の順にクリック >、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1182b-184">In the top menu bar, click **Debug -> Start Without debugging** or press **Ctrl + F5** .</span></span>
4. <span data-ttu-id="1182b-185">アプリがデプロイされたら、モーションコントローラーでトリガーをプルして、[ **Fitbox ボックス** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="1182b-185">When the app has deployed, dismiss the **Fitbox** by pulling the trigger on a motion controller.</span></span>

>[!NOTE]
><span data-ttu-id="1182b-186">Visual Studio の [エラー] パネルに赤色のエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="1182b-186">You might notice some red errors in the Visual Studio Errors panel.</span></span> <span data-ttu-id="1182b-187">無視しても安全です。</span><span class="sxs-lookup"><span data-stu-id="1182b-187">It is safe to ignore them.</span></span> <span data-ttu-id="1182b-188">実際のビルドの進行状況を表示するには、[出力] パネルに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="1182b-188">Switch to the Output panel to view actual build progress.</span></span> <span data-ttu-id="1182b-189">[出力] パネルでエラーが発生した場合は、修正を行う必要があります (多くの場合、スクリプトの間違いが原因です)。</span><span class="sxs-lookup"><span data-stu-id="1182b-189">Errors in the Output panel will require you to make a fix (most often they are caused by a mistake in a script).</span></span>

## <a name="chapter-1---awareness"></a><span data-ttu-id="1182b-190">Chapter 1-認識</span><span class="sxs-lookup"><span data-stu-id="1182b-190">Chapter 1 - Awareness</span></span>

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a><span data-ttu-id="1182b-191">目標</span><span class="sxs-lookup"><span data-stu-id="1182b-191">Objectives</span></span>

* <span data-ttu-id="1182b-192">音声コマンドの設計の **Dos とすべき** について説明します。</span><span class="sxs-lookup"><span data-stu-id="1182b-192">Learn the **Dos and Don'ts** of voice command design.</span></span>
* <span data-ttu-id="1182b-193">**KeywordRecognizer** を使用して、宝石ベースの音声コマンドを追加します。</span><span class="sxs-lookup"><span data-stu-id="1182b-193">Use **KeywordRecognizer** to add gaze based voice commands.</span></span>
* <span data-ttu-id="1182b-194">ユーザーがカーソル **フィードバック** を使用して音声コマンドを認識できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1182b-194">Make users aware of voice commands using cursor **feedback** .</span></span>

### <a name="voice-command-design"></a><span data-ttu-id="1182b-195">音声コマンドのデザイン</span><span class="sxs-lookup"><span data-stu-id="1182b-195">Voice Command Design</span></span>

<span data-ttu-id="1182b-196">この章では、音声コマンドの設計について学習します。</span><span class="sxs-lookup"><span data-stu-id="1182b-196">In this chapter, you'll learn about designing voice commands.</span></span> <span data-ttu-id="1182b-197">音声コマンドを作成する場合:</span><span class="sxs-lookup"><span data-stu-id="1182b-197">When creating voice commands:</span></span>

#### <a name="do"></a><span data-ttu-id="1182b-198">DO</span><span class="sxs-lookup"><span data-stu-id="1182b-198">DO</span></span>

* <span data-ttu-id="1182b-199">簡潔なコマンドを作成します。</span><span class="sxs-lookup"><span data-stu-id="1182b-199">Create concise commands.</span></span> <span data-ttu-id="1182b-200">*"現在選択さ* れているビデオを再生する" を使用しないでください。そのコマンドは簡潔ではなく、ユーザーが簡単に覚えられないからです。</span><span class="sxs-lookup"><span data-stu-id="1182b-200">You don't want to use *"Play the currently selected video"* , because that command is not concise and would easily be forgotten by the user.</span></span> <span data-ttu-id="1182b-201">代わりに、 *"Play Video"* を使用する必要があります。これは簡潔で、複数の音節があるためです。</span><span class="sxs-lookup"><span data-stu-id="1182b-201">Instead, you should use: *"Play Video"* , because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="1182b-202">単純なボキャブラリを使用します。</span><span class="sxs-lookup"><span data-stu-id="1182b-202">Use a simple vocabulary.</span></span> <span data-ttu-id="1182b-203">ユーザーが簡単に見つけて覚えておくことができる一般的な単語と語句を常に使用してください。</span><span class="sxs-lookup"><span data-stu-id="1182b-203">Always try to use common words and phrases that are easy for the user to discover and remember.</span></span> <span data-ttu-id="1182b-204">たとえば、アプリケーションで、表示または非表示にできるノートオブジェクトがある場合、"プラカード" はあまり使用されていないため、コマンド *"Show プラカード"* は使用しません。</span><span class="sxs-lookup"><span data-stu-id="1182b-204">For example, if your application had a note object that could be displayed or hidden from view, you would not use the command *"Show Placard"* , because "placard" is a rarely used term.</span></span> <span data-ttu-id="1182b-205">代わりに、 *"Show note"* コマンドを使用して、アプリケーションでメモを表示します。</span><span class="sxs-lookup"><span data-stu-id="1182b-205">Instead, you would use the command: *"Show Note"* , to reveal the note in your application.</span></span>
* <span data-ttu-id="1182b-206">一貫性を保ちます。</span><span class="sxs-lookup"><span data-stu-id="1182b-206">Be consistent.</span></span> <span data-ttu-id="1182b-207">音声コマンドは、アプリケーション全体で一貫した状態に保つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="1182b-207">Voice commands should be kept consistent across your application.</span></span> <span data-ttu-id="1182b-208">アプリケーションに2つのシーンがあり、両方のシーンにアプリケーションを閉じるためのボタンが含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="1182b-208">Imagine that you have two scenes in your application and both scenes contain a button for closing the application.</span></span> <span data-ttu-id="1182b-209">最初のシーンで *"Exit"* コマンドを使用してボタンをトリガーしたが、2番目のシーンで *"アプリを閉じる"* コマンドを使用した場合、ユーザーは混乱を招きます。</span><span class="sxs-lookup"><span data-stu-id="1182b-209">If the first scene used the command *"Exit"* to trigger the button, but the second scene used the command *"Close App"* , then the user is going to get very confused.</span></span> <span data-ttu-id="1182b-210">同じ機能を複数のシーンで保持する場合は、同じ音声コマンドを使用してトリガーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1182b-210">If the same functionality persists across multiple scenes, then the same voice command should be used to trigger it.</span></span>

#### <a name="dont"></a><span data-ttu-id="1182b-211">できません</span><span class="sxs-lookup"><span data-stu-id="1182b-211">DON'T</span></span>

* <span data-ttu-id="1182b-212">単一の syllable コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1182b-212">Use single syllable commands.</span></span> <span data-ttu-id="1182b-213">たとえば、音声コマンドを作成してビデオを再生する場合は、単純なコマンド *"play"* を使用しないようにする必要があります。これは単一の syllable であり、システムによって簡単に見逃しられる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="1182b-213">As an example, if you were creating a voice command to play a video, you should avoid using the simple command *"Play"* , as it is only a single syllable and could easily be missed by the system.</span></span> <span data-ttu-id="1182b-214">代わりに、 *"Play Video"* を使用する必要があります。これは簡潔で、複数の音節があるためです。</span><span class="sxs-lookup"><span data-stu-id="1182b-214">Instead, you should use: *"Play Video"* , because it is concise and has multiple syllables.</span></span>
* <span data-ttu-id="1182b-215">システムコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1182b-215">Use system commands.</span></span> <span data-ttu-id="1182b-216">*"Select"* コマンドは、現在フォーカスがあるオブジェクトに対して Tap イベントをトリガーするためにシステムによって予約されています。</span><span class="sxs-lookup"><span data-stu-id="1182b-216">The *"Select"* command is reserved by the system to trigger a Tap event for the currently focused object.</span></span> <span data-ttu-id="1182b-217">キーワードまたは語句では、予期したとおりに動作しない可能性があるため、 *"Select"* コマンドを再使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1182b-217">Do not re-use the *"Select"* command in a keyword or phrase, as it might not work as you expect.</span></span> <span data-ttu-id="1182b-218">たとえば、アプリケーションでキューブを選択するための音声コマンドが *"Select cube"* であったのに、ユーザーがコマンドを発音したときに球を見ていた場合、代わりに球が選択されます。</span><span class="sxs-lookup"><span data-stu-id="1182b-218">For example, if the voice command for selecting a cube in your application was *"Select cube"* , but the user was looking at a sphere when they uttered the command, then the sphere would be selected instead.</span></span> <span data-ttu-id="1182b-219">同様に、アプリケーションバーのコマンドも音声に対応しています。</span><span class="sxs-lookup"><span data-stu-id="1182b-219">Similarly app bar commands are voice enabled.</span></span> <span data-ttu-id="1182b-220">CoreWindow ビューでは、次の音声コマンドを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="1182b-220">Don't use the following speech commands in your CoreWindow View:</span></span>
    1. <span data-ttu-id="1182b-221">戻る</span><span class="sxs-lookup"><span data-stu-id="1182b-221">Go Back</span></span>
    2. <span data-ttu-id="1182b-222">スクロールツール</span><span class="sxs-lookup"><span data-stu-id="1182b-222">Scroll Tool</span></span>
    3. <span data-ttu-id="1182b-223">ズームツール</span><span class="sxs-lookup"><span data-stu-id="1182b-223">Zoom Tool</span></span>
    4. <span data-ttu-id="1182b-224">ツールのドラッグ</span><span class="sxs-lookup"><span data-stu-id="1182b-224">Drag Tool</span></span>
    5. <span data-ttu-id="1182b-225">Adjust</span><span class="sxs-lookup"><span data-stu-id="1182b-225">Adjust</span></span>
    6. <span data-ttu-id="1182b-226">[削除]</span><span class="sxs-lookup"><span data-stu-id="1182b-226">Remove</span></span>
* <span data-ttu-id="1182b-227">同様のサウンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="1182b-227">Use similar sounds.</span></span> <span data-ttu-id="1182b-228">Rhyme する音声コマンドを使用しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="1182b-228">Try to avoid using voice commands that rhyme.</span></span> <span data-ttu-id="1182b-229">*"Show Store"* と *"More show More"* がサポートされているショッピングアプリケーションがある場合は、もう一方のコマンドを使用している間に、いずれかのコマンドを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="1182b-229">If you had a shopping application which supported *"Show Store"* and *"Show More"* as voice commands, then you would want to disable one of the commands while the other was in use.</span></span> <span data-ttu-id="1182b-230">たとえば、[ *Show store]* \ (ストアの表示 \) ボタンを使用してストアを開き、ストアが表示されたときにそのコマンドを無効にして、[ *さらに表示]* コマンドを使用して参照することができます。</span><span class="sxs-lookup"><span data-stu-id="1182b-230">For example, you could use the *"Show Store"* button to open the store, and then disable that command when the store was displayed so that the *"Show More"* command could be used for browsing.</span></span>

### <a name="instructions"></a><span data-ttu-id="1182b-231">Instructions</span><span class="sxs-lookup"><span data-stu-id="1182b-231">Instructions</span></span>

* <span data-ttu-id="1182b-232">Unity の [ **階層** ] パネルで、検索ツールを使用して **holoComm_screen_mesh** オブジェクトを検索します。</span><span class="sxs-lookup"><span data-stu-id="1182b-232">In Unity's **Hierarchy** panel, use the search tool to find the **holoComm_screen_mesh** object.</span></span>
* <span data-ttu-id="1182b-233">**HoloComm_screen_mesh** オブジェクトをダブルクリックして、 **シーン** で表示します。</span><span class="sxs-lookup"><span data-stu-id="1182b-233">Double-click on the **holoComm_screen_mesh** object to view it in the **Scene** .</span></span> <span data-ttu-id="1182b-234">これは、音声コマンドに応答する astronaut の watch です。</span><span class="sxs-lookup"><span data-stu-id="1182b-234">This is the astronaut's watch, which will respond to our voice commands.</span></span>
* <span data-ttu-id="1182b-235">[ **インスペクター** ] パネルで、[ **音声入力ソース (スクリプト)** ] コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="1182b-235">In the **Inspector** panel, locate the **Speech Input Source (Script)** component.</span></span>
* <span data-ttu-id="1182b-236">[ **キーワード** ] セクションを展開して、サポートされている音声コマンドを確認します。 **Communicator を開き** ます。</span><span class="sxs-lookup"><span data-stu-id="1182b-236">Expand the **Keywords** section to see the supported voice command: **Open Communicator** .</span></span>
* <span data-ttu-id="1182b-237">右側にある [歯車] をクリックし、[ **スクリプトの編集** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="1182b-237">Click the cog to the right side, then select **Edit Script** .</span></span>
* <span data-ttu-id="1182b-238">**SpeechInputSource.cs** を調べて、 **KeywordRecognizer** を使用して音声コマンドを追加する方法を理解します。</span><span class="sxs-lookup"><span data-stu-id="1182b-238">Explore **SpeechInputSource.cs** to understand how it uses the **KeywordRecognizer** to add voice commands.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="1182b-239">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="1182b-239">Build and Deploy</span></span>

* <span data-ttu-id="1182b-240">Unity では、 **ファイル > ビルド設定** を使用して、アプリケーションをリビルドします。</span><span class="sxs-lookup"><span data-stu-id="1182b-240">In Unity, use **File > Build Settings** to rebuild the application.</span></span>
* <span data-ttu-id="1182b-241">**アプリ** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="1182b-241">Open the **App** folder.</span></span>
* <span data-ttu-id="1182b-242">**Modelexplorer Visual Studio ソリューション** を開きます。</span><span class="sxs-lookup"><span data-stu-id="1182b-242">Open the **ModelExplorer Visual Studio Solution** .</span></span>

<span data-ttu-id="1182b-243">(セットアップ時に Visual Studio でこのプロジェクトを既にビルドまたは展開している場合は、VS のインスタンスを開いて、メッセージが表示されたら [すべて再読み込み] をクリックします)。</span><span class="sxs-lookup"><span data-stu-id="1182b-243">(If you already built/deployed this project in Visual Studio during set-up, then you can open that instance of VS and click 'Reload All' when prompted).</span></span>

* <span data-ttu-id="1182b-244">Visual Studio で、[デバッグ]、[ **デバッグなしで開始** ] の順にクリック >、Ctrl キーを押し **ながら F5** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1182b-244">In Visual Studio, click **Debug -> Start Without debugging** or press **Ctrl + F5** .</span></span>
* <span data-ttu-id="1182b-245">アプリケーションが HoloLens にデプロイされたら、 [エアタップ](../../../design/gaze-and-commit.md#composite-gestures) ジェスチャを使用して [フィット] ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1182b-245">After the application deploys to the HoloLens, dismiss the fit box using the [air-tap](../../../design/gaze-and-commit.md#composite-gestures) gesture.</span></span>
* <span data-ttu-id="1182b-246">Astronaut の watch を見つめます。</span><span class="sxs-lookup"><span data-stu-id="1182b-246">Gaze at the astronaut's watch.</span></span>
* <span data-ttu-id="1182b-247">ウォッチにフォーカスがある場合は、カーソルがマイクに変わっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1182b-247">When the watch has focus, verify that the cursor changes to a microphone.</span></span> <span data-ttu-id="1182b-248">これにより、アプリケーションが音声コマンドをリッスンしていることを示すフィードバックが提供されます。</span><span class="sxs-lookup"><span data-stu-id="1182b-248">This provides feedback that the application is listening for voice commands.</span></span>
* <span data-ttu-id="1182b-249">ウォッチにツールヒントが表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1182b-249">Verify that a tooltip appears on the watch.</span></span> <span data-ttu-id="1182b-250">これにより、ユーザーは *"Open Communicator"* コマンドを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="1182b-250">This helps users discover the *"Open Communicator"* command.</span></span>
* <span data-ttu-id="1182b-251">監視での再生中に、「communicator を *開く」* と言い、communicator パネルを開きます。</span><span class="sxs-lookup"><span data-stu-id="1182b-251">While gazing at the watch, say *"Open Communicator"* to open the communicator panel.</span></span>

## <a name="chapter-2---acknowledgement"></a><span data-ttu-id="1182b-252">Chapter 2-確認</span><span class="sxs-lookup"><span data-stu-id="1182b-252">Chapter 2 - Acknowledgement</span></span>

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a><span data-ttu-id="1182b-253">目標</span><span class="sxs-lookup"><span data-stu-id="1182b-253">Objectives</span></span>

* <span data-ttu-id="1182b-254">マイク入力を使用してメッセージを記録します。</span><span class="sxs-lookup"><span data-stu-id="1182b-254">Record a message using the Microphone input.</span></span>
* <span data-ttu-id="1182b-255">アプリケーションが音声をリッスンしていることをユーザーにフィードバックします。</span><span class="sxs-lookup"><span data-stu-id="1182b-255">Give feedback to the user that the application is listening to their voice.</span></span>

>[!NOTE]
><span data-ttu-id="1182b-256">マイクから録音するアプリの **マイク** 機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1182b-256">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="1182b-257">これは、MR 入力212で既に行われていますが、独自のプロジェクトでは考慮しておいてください。</span><span class="sxs-lookup"><span data-stu-id="1182b-257">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="1182b-258">Unity エディターで、[Edit > Project Settings > Player] の順に移動して、windows media player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="1182b-258">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="1182b-259">[ユニバーサル Windows プラットフォーム] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1182b-259">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="1182b-260">[発行設定 > 機能] セクションで、 **マイク** の機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="1182b-260">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="1182b-261">Instructions</span><span class="sxs-lookup"><span data-stu-id="1182b-261">Instructions</span></span>

* <span data-ttu-id="1182b-262">Unity の [ **階層** ] パネルで、 **holoComm_screen_mesh** オブジェクトが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1182b-262">In Unity's **Hierarchy** panel, verify that the **holoComm_screen_mesh** object is selected.</span></span>
* <span data-ttu-id="1182b-263">[ **インスペクター** ] パネルで、 **Astronaut Watch (スクリプト)** コンポーネントを見つけます。</span><span class="sxs-lookup"><span data-stu-id="1182b-263">In the **Inspector** panel, find the **Astronaut Watch (Script)** component.</span></span>
* <span data-ttu-id="1182b-264">[ **Communicator Prefab** ] プロパティの値として設定されている小さい、blue のキューブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1182b-264">Click on the small, blue cube which is set as the value of the **Communicator Prefab** property.</span></span>
* <span data-ttu-id="1182b-265">[ **プロジェクト** ] パネルで、 **Communicator** prefab にフォーカスがあるはずです。</span><span class="sxs-lookup"><span data-stu-id="1182b-265">In the **Project** panel, the **Communicator** prefab should now have focus.</span></span>
* <span data-ttu-id="1182b-266">[ **プロジェクト** ] パネルの [ **Communicator** prefab] をクリックして、 **インスペクター** でそのコンポーネントを表示します。</span><span class="sxs-lookup"><span data-stu-id="1182b-266">Click on the **Communicator** prefab in the **Project** panel to view its components in the **Inspector** .</span></span>
* <span data-ttu-id="1182b-267">**マイクマネージャー (スクリプト)** コンポーネントを見ると、ユーザーの声を記録することができます。</span><span class="sxs-lookup"><span data-stu-id="1182b-267">Look at the **Microphone Manager (Script)** component, this will allow us to record the user's voice.</span></span>
* <span data-ttu-id="1182b-268">**Communicator** オブジェクトに、[ **メッセージの送信** ] コマンドに応答するための **音声入力ハンドラー (スクリプト)** コンポーネントがあることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1182b-268">Notice that the **Communicator** object has a **Speech Input Handler (Script)** component for responding to the **Send Message** command.</span></span>
* <span data-ttu-id="1182b-269">**Communicator (スクリプト)** コンポーネントを確認し、スクリプトをダブルクリックして Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="1182b-269">Look at the **Communicator (Script)** component and double-click on the script to open it in Visual Studio.</span></span>

<span data-ttu-id="1182b-270">Communicator.cs は、communicator デバイスで適切なボタンの状態を設定する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="1182b-270">Communicator.cs is responsible for setting the proper button states on the communicator device.</span></span> <span data-ttu-id="1182b-271">これにより、ユーザーはメッセージを記録して再生し、astronaut にメッセージを送信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="1182b-271">This will allow our users to record a message, play it back, and send the message to the astronaut.</span></span> <span data-ttu-id="1182b-272">また、アニメーション化された wave フォームを開始および停止して、音声が聞こえたことをユーザーに確認します。</span><span class="sxs-lookup"><span data-stu-id="1182b-272">It will also start and stop an animated wave form, to acknowledge to the user that their voice was heard.</span></span>

* <span data-ttu-id="1182b-273">**Communicator.cs** で、 **Start** メソッドから次の行 (81 と 82) を削除します。</span><span class="sxs-lookup"><span data-stu-id="1182b-273">In **Communicator.cs** , delete the following lines (81 and 82) from the **Start** method.</span></span> <span data-ttu-id="1182b-274">これにより、communicator の [レコード] ボタンが有効になります。</span><span class="sxs-lookup"><span data-stu-id="1182b-274">This will enable the 'Record' button on the communicator.</span></span>

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a><span data-ttu-id="1182b-275">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="1182b-275">Build and Deploy</span></span>

* <span data-ttu-id="1182b-276">Visual Studio で、アプリケーションをリビルドし、デバイスにデプロイします。</span><span class="sxs-lookup"><span data-stu-id="1182b-276">In Visual Studio, rebuild your application and deploy to the device.</span></span>
* <span data-ttu-id="1182b-277">Astronaut の watch を見つめ、 *「Open communicator」* と言うと、communicator が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1182b-277">Gaze at the astronaut's watch and say *"Open Communicator"* to show the communicator.</span></span>
* <span data-ttu-id="1182b-278">[ **録音** ] ボタン (マイク) を押して、astronaut の音声メッセージの録音を開始します。</span><span class="sxs-lookup"><span data-stu-id="1182b-278">Press the **Record** button (microphone) to start recording a verbal message for the astronaut.</span></span>
* <span data-ttu-id="1182b-279">読み上げを開始し、wave アニメーションが communicator で再生されることを確認します。これにより、音声が聞こえたことをユーザーにフィードバックできます。</span><span class="sxs-lookup"><span data-stu-id="1182b-279">Start speaking, and verify that the wave animation plays on the communicator, which provides feedback to the user that their voice is heard.</span></span>
* <span data-ttu-id="1182b-280">[ **停止** ] ボタン (左の四角形) をクリックし、wave アニメーションの実行が停止していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1182b-280">Press the **Stop** button (left square), and verify that the wave animation stops running.</span></span>
* <span data-ttu-id="1182b-281">**再生** ボタン (右三角形) を押して、記録されたメッセージを再生し、デバイスで再生します。</span><span class="sxs-lookup"><span data-stu-id="1182b-281">Press the **Play** button (right triangle) to play back the recorded message and hear it on the device.</span></span>
* <span data-ttu-id="1182b-282">記録されたメッセージの再生を停止するには、[ **停止** ] ボタン (右の四角形) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1182b-282">Press the **Stop** button (right square) to stop playback of the recorded message.</span></span>
* <span data-ttu-id="1182b-283">Communicator を終了し、astronaut から "メッセージを受信しました" という応答を受信するには、 *"メッセージの送信"* と言います。</span><span class="sxs-lookup"><span data-stu-id="1182b-283">Say *"Send Message"* to close the communicator and receive a 'Message Received' response from the astronaut.</span></span>

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a><span data-ttu-id="1182b-284">章 3-およびディクテーション認識エンジンについて</span><span class="sxs-lookup"><span data-stu-id="1182b-284">Chapter 3 - Understanding and the Dictation Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a><span data-ttu-id="1182b-285">目標</span><span class="sxs-lookup"><span data-stu-id="1182b-285">Objectives</span></span>

* <span data-ttu-id="1182b-286">ディクテーション認識エンジンを使用して、ユーザーの音声をテキストに変換します。</span><span class="sxs-lookup"><span data-stu-id="1182b-286">Use the Dictation Recognizer to convert the user's speech to text.</span></span>
* <span data-ttu-id="1182b-287">Communicator でディクテーションエンジンの仮説と最終結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="1182b-287">Show the Dictation Recognizer's hypothesized and final results in the communicator.</span></span>

<span data-ttu-id="1182b-288">この章では、ディクテーション認識エンジンを使用して、astronaut のメッセージを作成します。</span><span class="sxs-lookup"><span data-stu-id="1182b-288">In this chapter, we'll use the Dictation Recognizer to create a message for the astronaut.</span></span> <span data-ttu-id="1182b-289">ディクテーション認識エンジンを使用する場合は、次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="1182b-289">When using the Dictation Recognizer, keep in mind that:</span></span>

* <span data-ttu-id="1182b-290">ディクテーションエンジンが動作するには、WiFi に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1182b-290">You must be connected to WiFi for the Dictation Recognizer to work.</span></span>
* <span data-ttu-id="1182b-291">タイムアウトは、一定の時間が経過すると発生します。</span><span class="sxs-lookup"><span data-stu-id="1182b-291">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="1182b-292">次の2つの点に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1182b-292">There are two timeouts to be aware of:</span></span>
  * <span data-ttu-id="1182b-293">認識エンジンが起動し、最初の5秒間オーディオが聞こえない場合は、タイムアウトします。</span><span class="sxs-lookup"><span data-stu-id="1182b-293">If the recognizer starts and doesn't hear any audio for the first five seconds, it will timeout.</span></span>
  * <span data-ttu-id="1182b-294">認識エンジンが結果を指定した後、20秒間無音の状態になると、タイムアウトします。</span><span class="sxs-lookup"><span data-stu-id="1182b-294">If the recognizer has given a result but then hears silence for twenty seconds, it will timeout.</span></span>
* <span data-ttu-id="1182b-295">一度に実行できるのは、1種類のレコグナイザー (キーワードまたはディクテーション) だけです。</span><span class="sxs-lookup"><span data-stu-id="1182b-295">Only one type of recognizer (Keyword or Dictation) can run at a time.</span></span>

>[!NOTE]
><span data-ttu-id="1182b-296">マイクから録音するアプリの **マイク** 機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1182b-296">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="1182b-297">これは、MR 入力212で既に行われていますが、独自のプロジェクトでは考慮しておいてください。</span><span class="sxs-lookup"><span data-stu-id="1182b-297">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="1182b-298">Unity エディターで、[Edit > Project Settings > Player] の順に移動して、windows media player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="1182b-298">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="1182b-299">[ユニバーサル Windows プラットフォーム] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1182b-299">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="1182b-300">[発行設定 > 機能] セクションで、 **マイク** の機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="1182b-300">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="1182b-301">Instructions</span><span class="sxs-lookup"><span data-stu-id="1182b-301">Instructions</span></span>

<span data-ttu-id="1182b-302">ディクテーション認識エンジンを使用するように **MicrophoneManager.cs** を編集します。</span><span class="sxs-lookup"><span data-stu-id="1182b-302">We're going to edit **MicrophoneManager.cs** to use the Dictation Recognizer.</span></span> <span data-ttu-id="1182b-303">次のように追加します。</span><span class="sxs-lookup"><span data-stu-id="1182b-303">This is what we'll add:</span></span>

1. <span data-ttu-id="1182b-304">[ **レコード] ボタン** が押されると、 **DictationRecognizer が開始** されます。</span><span class="sxs-lookup"><span data-stu-id="1182b-304">When the **Record button** is pressed, we'll **start the DictationRecognizer** .</span></span>
2. <span data-ttu-id="1182b-305">DictationRecognizer が理解したことの **仮説** を示します。</span><span class="sxs-lookup"><span data-stu-id="1182b-305">Show the **hypothesis** of what the DictationRecognizer understood.</span></span>
3. <span data-ttu-id="1182b-306">DictationRecognizer が理解した **結果** をロックします。</span><span class="sxs-lookup"><span data-stu-id="1182b-306">Lock in the **results** of what the DictationRecognizer understood.</span></span>
4. <span data-ttu-id="1182b-307">DictationRecognizer からのタイムアウトを確認します。</span><span class="sxs-lookup"><span data-stu-id="1182b-307">Check for timeouts from the DictationRecognizer.</span></span>
5. <span data-ttu-id="1182b-308">[ **停止] ボタン** が押されたとき、または mic セッションがタイムアウトになった場合は、 **DictationRecognizer を停止** します。</span><span class="sxs-lookup"><span data-stu-id="1182b-308">When the **Stop button** is pressed, or the mic session times out, **stop the DictationRecognizer** .</span></span>
6. <span data-ttu-id="1182b-309">**KeywordRecognizer** を再起動します。これにより、[ **メッセージの送信** ] コマンドがリッスンされます。</span><span class="sxs-lookup"><span data-stu-id="1182b-309">Restart the **KeywordRecognizer** , which will listen for the **Send Message** command.</span></span>

<span data-ttu-id="1182b-310">では、始めましょう。</span><span class="sxs-lookup"><span data-stu-id="1182b-310">Let's get started.</span></span> <span data-ttu-id="1182b-311">**MicrophoneManager.cs** の 3. a のコード演習をすべて完了するか、以下の完成したコードをコピーして貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="1182b-311">Complete all coding exercises for 3.a in **MicrophoneManager.cs** , or copy and paste the finished code found below:</span></span>

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a><span data-ttu-id="1182b-312">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="1182b-312">Build and Deploy</span></span>

* <span data-ttu-id="1182b-313">Visual Studio でリビルドし、デバイスにデプロイします。</span><span class="sxs-lookup"><span data-stu-id="1182b-313">Rebuild in Visual Studio and deploy to your device.</span></span>
* <span data-ttu-id="1182b-314">エアタップジェスチャで [フィット] ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1182b-314">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="1182b-315">Astronaut の watch を見つめ、 *"Open Communicator"* と言います。</span><span class="sxs-lookup"><span data-stu-id="1182b-315">Gaze at the astronaut's watch and say *"Open Communicator"* .</span></span>
* <span data-ttu-id="1182b-316">[ **録音** ] ボタン (マイク) を選択して、メッセージを記録します。</span><span class="sxs-lookup"><span data-stu-id="1182b-316">Select the **Record** button (microphone) to record your message.</span></span>
* <span data-ttu-id="1182b-317">読み上げを開始します。</span><span class="sxs-lookup"><span data-stu-id="1182b-317">Start speaking.</span></span> <span data-ttu-id="1182b-318">**ディクテーションレコグナイザー** は、音声を解釈し、そのテキストを communicator で表示します。</span><span class="sxs-lookup"><span data-stu-id="1182b-318">The **Dictation Recognizer** will interpret your speech and show the hypothesized text in the communicator.</span></span>
* <span data-ttu-id="1182b-319">メッセージを記録しているときに、 *"メッセージの送信"* をお試しください。</span><span class="sxs-lookup"><span data-stu-id="1182b-319">Try saying *"Send Message"* while you are recording a message.</span></span> <span data-ttu-id="1182b-320">**ディクテーションレコグナイザー** がまだアクティブであるため、 **キーワードレコグナイザー** は応答しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1182b-320">Notice that the **Keyword Recognizer** does not respond because the **Dictation Recognizer** is still active.</span></span>
* <span data-ttu-id="1182b-321">数秒間読み上げを停止します。</span><span class="sxs-lookup"><span data-stu-id="1182b-321">Stop speaking for a few seconds.</span></span> <span data-ttu-id="1182b-322">ディクテーションレコグナイザーが仮説を完了し、最終的な結果が表示されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1182b-322">Watch as the Dictation Recognizer completes its hypothesis and shows the final result.</span></span>
* <span data-ttu-id="1182b-323">読み上げを開始し、20秒間一時停止します。</span><span class="sxs-lookup"><span data-stu-id="1182b-323">Begin speaking and then pause for 20 seconds.</span></span> <span data-ttu-id="1182b-324">これにより、 **ディクテーションレコグナイザー** がタイムアウトします。</span><span class="sxs-lookup"><span data-stu-id="1182b-324">This will cause the **Dictation Recognizer** to timeout.</span></span>
* <span data-ttu-id="1182b-325">上記のタイムアウト後に、 **キーワード認識エンジン** が再度有効になっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="1182b-325">Notice that the **Keyword Recognizer** is re-enabled after the above timeout.</span></span> <span data-ttu-id="1182b-326">これで、communicator は音声コマンドに応答します。</span><span class="sxs-lookup"><span data-stu-id="1182b-326">The communicator will now respond to voice commands.</span></span>
* <span data-ttu-id="1182b-327">Astronaut にメッセージを送信するには、 *"メッセージの送信"* と言います。</span><span class="sxs-lookup"><span data-stu-id="1182b-327">Say *"Send Message"* to send the message to the astronaut.</span></span>

## <a name="chapter-4---grammar-recognizer"></a><span data-ttu-id="1182b-328">Chapter 4-文法レコグナイザー</span><span class="sxs-lookup"><span data-stu-id="1182b-328">Chapter 4 - Grammar Recognizer</span></span>

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a><span data-ttu-id="1182b-329">目標</span><span class="sxs-lookup"><span data-stu-id="1182b-329">Objectives</span></span>

* <span data-ttu-id="1182b-330">SRGS、または音声認識の文法指定ファイルに従って、ユーザーの音声を認識するには、文法認識エンジンを使用します。</span><span class="sxs-lookup"><span data-stu-id="1182b-330">Use the Grammar Recognizer to recognize the user's speech according to an SRGS, or Speech Recognition Grammar Specification, file.</span></span>

>[!NOTE]
><span data-ttu-id="1182b-331">マイクから録音するアプリの **マイク** 機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1182b-331">The **Microphone** capability must be declared for an app to record from the microphone.</span></span> <span data-ttu-id="1182b-332">これは、MR 入力212で既に行われていますが、独自のプロジェクトでは考慮しておいてください。</span><span class="sxs-lookup"><span data-stu-id="1182b-332">This is done for you already in MR Input 212, but keep this in mind for your own projects.</span></span>
>
>1. <span data-ttu-id="1182b-333">Unity エディターで、[Edit > Project Settings > Player] の順に移動して、windows media player の設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="1182b-333">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
>2. <span data-ttu-id="1182b-334">[ユニバーサル Windows プラットフォーム] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="1182b-334">Click on the "Universal Windows Platform" tab</span></span>
>3. <span data-ttu-id="1182b-335">[発行設定 > 機能] セクションで、 **マイク** の機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="1182b-335">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

### <a name="instructions"></a><span data-ttu-id="1182b-336">Instructions</span><span class="sxs-lookup"><span data-stu-id="1182b-336">Instructions</span></span>

1. <span data-ttu-id="1182b-337">[ **階層** ] パネルで **Jetpack_Center** を検索して選択します。</span><span class="sxs-lookup"><span data-stu-id="1182b-337">In the **Hierarchy** panel, search for **Jetpack_Center** and select it.</span></span>
2. <span data-ttu-id="1182b-338">[ **インスペクター** ] パネルで **tagalong** スクリプトを探します。</span><span class="sxs-lookup"><span data-stu-id="1182b-338">Look for the **Tagalong Action** script in the **Inspector** panel.</span></span>
3. <span data-ttu-id="1182b-339">オブジェクトの右側にある小さな円をクリックして、フィールド **にタグを付け** ます。</span><span class="sxs-lookup"><span data-stu-id="1182b-339">Click the little circle to the right of the **Object To Tag Along** field.</span></span>
4. <span data-ttu-id="1182b-340">ポップアップ表示されたウィンドウで、[ **Srgstoolbox]** を検索し、一覧から選択します。</span><span class="sxs-lookup"><span data-stu-id="1182b-340">In the window that pops up, search for **SRGSToolbox** and select it from the list.</span></span>
5. <span data-ttu-id="1182b-341">**Streamingassets** フォルダーの **SRGSColor.xml** ファイルを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="1182b-341">Take a look at the **SRGSColor.xml** file in the **StreamingAssets** folder.</span></span>
    1. <span data-ttu-id="1182b-342">SRGS の設計仕様は、W3C [の web サイトにあります](https://www.w3.org/TR/speech-grammar/)。</span><span class="sxs-lookup"><span data-stu-id="1182b-342">The SRGS design spec can be found on the W3C website [here](https://www.w3.org/TR/speech-grammar/).</span></span>

<span data-ttu-id="1182b-343">この SRGS ファイルには、次の3種類のルールがあります。</span><span class="sxs-lookup"><span data-stu-id="1182b-343">In our SRGS file, we have three types of rules:</span></span>

* <span data-ttu-id="1182b-344">12色のリストから1色を指定できるルール。</span><span class="sxs-lookup"><span data-stu-id="1182b-344">A rule which lets you say one color from a list of twelve colors.</span></span>
* <span data-ttu-id="1182b-345">色ルールと3つの図形の組み合わせをリッスンする3つのルール。</span><span class="sxs-lookup"><span data-stu-id="1182b-345">Three rules which listen for a combination of the color rule and one of the three shapes.</span></span>
* <span data-ttu-id="1182b-346">ルートルールである colorChooser は、3つの "カラー + シェイプ" ルールの任意の組み合わせをリッスンします。</span><span class="sxs-lookup"><span data-stu-id="1182b-346">The root rule, colorChooser, which listens for any combination of the three "color + shape" rules.</span></span> <span data-ttu-id="1182b-347">図形は任意の順序で、任意の量の任意の数を3つにすることができます。</span><span class="sxs-lookup"><span data-stu-id="1182b-347">The shapes can be said in any order and in any amount from just one to all three.</span></span> <span data-ttu-id="1182b-348">これは、最初の文法タグのファイルの先頭にルートルールとして指定されているので、でリッスンされる唯一のルールです &lt; &gt; 。</span><span class="sxs-lookup"><span data-stu-id="1182b-348">This is the only rule that is listened for, as it's specified as the root rule at the top of the file in the initial &lt;grammar&gt; tag.</span></span>

### <a name="build-and-deploy"></a><span data-ttu-id="1182b-349">ビルドと配置</span><span class="sxs-lookup"><span data-stu-id="1182b-349">Build and Deploy</span></span>

* <span data-ttu-id="1182b-350">Unity でアプリケーションをリビルドし、Visual Studio からビルドしてデプロイし、HoloLens でアプリを体験します。</span><span class="sxs-lookup"><span data-stu-id="1182b-350">Rebuild the application in Unity, then build and deploy from Visual Studio to experience the app on HoloLens.</span></span>
* <span data-ttu-id="1182b-351">エアタップジェスチャで [フィット] ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1182b-351">Dismiss the fit box with an air-tap gesture.</span></span>
* <span data-ttu-id="1182b-352">Astronaut の jetpack を見つめ、エアタップジェスチャを実行します。</span><span class="sxs-lookup"><span data-stu-id="1182b-352">Gaze at the astronaut's jetpack and perform an air-tap gesture.</span></span>
* <span data-ttu-id="1182b-353">読み上げを開始します。</span><span class="sxs-lookup"><span data-stu-id="1182b-353">Start speaking.</span></span> <span data-ttu-id="1182b-354">**文法認識エンジン** は、音声を解釈し、認識に基づいて図形の色を変更します。</span><span class="sxs-lookup"><span data-stu-id="1182b-354">The **Grammar Recognizer** will interpret your speech and change the colors of the shapes based on the recognition.</span></span> <span data-ttu-id="1182b-355">コマンドの例としては、"blue circle, 黄色い square" などがあります。</span><span class="sxs-lookup"><span data-stu-id="1182b-355">An example command is "blue circle, yellow square".</span></span>
* <span data-ttu-id="1182b-356">別のエアタップジェスチャを実行して、ツールボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="1182b-356">Perform another air-tap gesture to dismiss the toolbox.</span></span>

## <a name="the-end"></a><span data-ttu-id="1182b-357">最後です</span><span class="sxs-lookup"><span data-stu-id="1182b-357">The End</span></span>

<span data-ttu-id="1182b-358">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="1182b-358">Congratulations!</span></span> <span data-ttu-id="1182b-359">これで **MR 入力 212: Voice** が完了しました。</span><span class="sxs-lookup"><span data-stu-id="1182b-359">You have now completed **MR Input 212: Voice** .</span></span>

* <span data-ttu-id="1182b-360">音声コマンドの Dos とすべきがわかっています。</span><span class="sxs-lookup"><span data-stu-id="1182b-360">You know the Dos and Don'ts of voice commands.</span></span>
* <span data-ttu-id="1182b-361">ユーザーが音声コマンドを認識できるように、ツールヒントがどのように使用されたかを見てきました。</span><span class="sxs-lookup"><span data-stu-id="1182b-361">You saw how tooltips were employed to make users aware of voice commands.</span></span>
* <span data-ttu-id="1182b-362">ユーザーの声が聞こえたことを認識するために使用されるフィードバックの種類がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="1182b-362">You saw several types of feedback used to acknowledge that the user's voice was heard.</span></span>
* <span data-ttu-id="1182b-363">キーワードレコグナイザーとディクテーション認識エンジンを切り替える方法と、これら2つの機能が音声を理解し、解釈する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1182b-363">You know how to switch between the Keyword Recognizer and the Dictation Recognizer, and how these two features understand and interpret your voice.</span></span>
* <span data-ttu-id="1182b-364">アプリケーションで、SRGS ファイルと文法認識エンジンを使用して音声認識を行う方法を学習しました。</span><span class="sxs-lookup"><span data-stu-id="1182b-364">You learned how to use an SRGS file and the Grammar Recognizer for speech recognition in your application.</span></span>