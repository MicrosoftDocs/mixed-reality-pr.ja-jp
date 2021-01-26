---
title: 6. デバイスまたはエミュレーターへのパッケージ化とデプロイ
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用してチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 6
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 7b706cf2a8685954ed916c825c3617ade190f1e0
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583655"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="5e08b-104">6.デバイスまたはエミュレーターへのパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="5e08b-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="5e08b-105">前のチュートリアルでは、チェスの駒を元の位置にリセットする簡単なボタンを追加しました。</span><span class="sxs-lookup"><span data-stu-id="5e08b-105">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="5e08b-106">この最後のセクションでは、アプリを HoloLens 2 またはエミュレーターで実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5e08b-106">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="5e08b-107">HoloLens 2 をお持ちの場合は、コンピューターからストリーミングするか、アプリをパッケージ化してデバイス上で直接実行することができます。</span><span class="sxs-lookup"><span data-stu-id="5e08b-107">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="5e08b-108">デバイスがない場合は、エミュレーターで実行するアプリをパッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-108">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="5e08b-109">このセクションを完了するまでに、対話式操作と UI を備えた、再生可能な Mixed Reality アプリがデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="5e08b-109">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="5e08b-110">目標</span><span class="sxs-lookup"><span data-stu-id="5e08b-110">Objectives</span></span>

* <span data-ttu-id="5e08b-111">[デバイスのみ] ホログラフィック アプリのリモート処理によって HoloLens 2 にストリーミングする</span><span class="sxs-lookup"><span data-stu-id="5e08b-111">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="5e08b-112">アプリをパッケージ化して HoloLens 2 のデバイスまたはエミュレーターにデプロイする</span><span class="sxs-lookup"><span data-stu-id="5e08b-112">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="5e08b-113">[デバイスのみ] ストリーミング</span><span class="sxs-lookup"><span data-stu-id="5e08b-113">[Device Only] Streaming</span></span>

<span data-ttu-id="5e08b-114">[Holographic Remoting](/windows/mixed-reality/add-holographic-remoting) は、チャネルを切り替えるのではなく、PC またはスタンドアロンの UWP デバイスから HoloLens 2 にデータをストリーミングすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-114">[Holographic Remoting](/windows/mixed-reality/add-holographic-remoting) means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="5e08b-115">HoloLens から入力データ ストリームを受け取ったリモート処理ホスト アプリにより、仮想イマーシブ ビューでコンテンツがレンダリングされ、Wi-Fi 経由でコンテンツ フレームが HoloLens にストリーミングされます。</span><span class="sxs-lookup"><span data-stu-id="5e08b-115">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="5e08b-116">ストリーミングを使用すると、リモートのイマーシブ ビューを既存のデスクトップ PC ソフトウェアに追加し、より多くのシステム リソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5e08b-116">Streaming lets you add remote immersive views into existing desktop PC software and has access to more system resources.</span></span>

<span data-ttu-id="5e08b-117">チェス アプリでこのルートを使用する場合は、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e08b-117">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="5e08b-118">Microsoft Store から **Holographic Remoting Player** を HoloLens 2 にインストールし、アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-118">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span> <span data-ttu-id="5e08b-119">アプリに表示される IP アドレスをメモします。</span><span class="sxs-lookup"><span data-stu-id="5e08b-119">Note your IP address displayed in the app.</span></span>
    * <span data-ttu-id="5e08b-120">**[Edit]\(編集\) > [Project Settings]\(プロジェクトの設定\)** の順に移動し、Windows の **[Default RHI]\(既定の RHI\)** が **[Default]\(既定\)** または **[D3D11]** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-120">Go to **Edit > Project Settings** and sure the Windows **Default RHI** is set to **Default** or **D3D11**:</span></span>

![既定の RHI](../images/unreal/performance-recommendations-img-09.png)

2.  <span data-ttu-id="5e08b-122">Unreal エディターに戻り、 **[編集]、[プロジェクトの設定]** の順に移動し、 **[Holographic Remoting]** セクションで **[リモート処理を有効にする]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="5e08b-122">Back in the Unreal editor, go to **Edit > Project Settings** and check **Enable Remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="5e08b-123">エディターを再起動し、デバイスの IP アドレス (Holographic Remoting Player アプリに表示されるもの) を入力し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e08b-123">Restart the editor, then enter your device's IP address (as displayed in the Holographic Remoting Player app), then click **Connect**.</span></span>

<span data-ttu-id="5e08b-124">接続後、 **[Play]\(再生\)** ボタンの右側にあるドロップダウン矢印をクリックし、 **[VR Preview]\(VR プレビュー\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-124">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="5e08b-125">VR プレビュー ウィンドウでアプリが実行され、HoloLens ヘッドセットにストリーミングされます。</span><span class="sxs-lookup"><span data-stu-id="5e08b-125">The app will run in the VR Preview window, which is streamed to the HoloLens headset.</span></span>

## <a name="packaging-and-deploying-the-app-via-device-portal"></a><span data-ttu-id="5e08b-126">デバイス ポータル経由でのアプリのパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="5e08b-126">Packaging and deploying the app via device portal</span></span>

>[!NOTE]
><span data-ttu-id="5e08b-127">HoloLens 用の Unreal アプリを初めてパッケージ化する場合は、Epic Launcher からサポート ファイルをダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e08b-127">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span>
>- <span data-ttu-id="5e08b-128">**[Editor Preferences]\(エディターの設定\) > [General]\(全般\) > [Source Code]\(ソース コード\) > [Source Code Editor]\(ソース コード エディター\)** に移動し、Visual Studio 2019 が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-128">Go to **Editor Preferences > General > Source Code > Source Code Editor** and check that Visual Studio 2019 is selected.</span></span>
>- <span data-ttu-id="5e08b-129">Epic Games Launcher の **[ライブラリ]** タブに移動し、 **[起動]** の横にあるドロップダウン矢印を選択して、 **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e08b-129">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span>
>- <span data-ttu-id="5e08b-130">**[対応プラットフォーム]** で、 **[HoloLens 2]** を選択し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e08b-130">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
><span data-ttu-id="5e08b-131">![プロジェクト設定でターゲット プラットフォームを変更する](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="5e08b-131">![Change target platform in project settings](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="5e08b-132">**[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\)** に移動します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-132">Go to **Edit > Project Settings**.</span></span>
    * <span data-ttu-id="5e08b-133">**[Project]\(プロジェクト\) > [Description]\(説明\) > [About]\(情報\) > [Project Name]\(プロジェクト名\)** で、プロジェクト名を追加します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-133">Add a project name under **Project > Description > About > Project Name**.</span></span>
    * <span data-ttu-id="5e08b-134">**[Project]\(プロジェクト\) > [Description]\(説明\) > [Publisher]\(発行元\) > [Company Distinguished Name]\(企業識別名\)** で、「**CN=YourCompanyName**」を追加します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-134">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>
    * <span data-ttu-id="5e08b-135">**[Project]\(プロジェクト\) > [Description]\(説明\) > [Settings]\(設定\)** の **[Start in VR]\(VR で開始\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-135">Select **Start in VR** under **Project > Description > Settings**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e08b-136">これらのフィールドのどちらかを空白のままにすると、手順 3 で新しい証明書を作成するときにエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-136">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e08b-137">発行元の名前は、[LADPv3 識別名形式](https://www.ietf.org/rfc/rfc2253.txt)である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e08b-137">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="5e08b-138">発行元の名前の形式が正しくないと、"署名キーが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="5e08b-138">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="5e08b-139">アプリをデジタル署名できませんでした。"</span><span class="sxs-lookup"><span data-stu-id="5e08b-139">The app could not be digitally signed."</span></span> <span data-ttu-id="5e08b-140">エラーがパッケージ化するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-140">error upon packaging.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e08b-141">[Start in VR]\(VR で開始\) を選択しないと、スレート内でアプリケーションの起動が試行されます。</span><span class="sxs-lookup"><span data-stu-id="5e08b-141">Not selecting "Start in VR" will lead your application trying to start in a slate</span></span>

![プロジェクト設定 - 説明](images/unreal-uxt/6-cn-new.PNG)

2.  <span data-ttu-id="5e08b-143">**[プラットフォーム] > [HoloLens]** で **[HoloLens Emulation 用にビルド]** または **[HoloLens Device 用にビルド]** を有効にします。</span><span class="sxs-lookup"><span data-stu-id="5e08b-143">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="5e08b-144">**[パッケージ化]** セクション ( **[証明書に署名]** の横) の **[新規生成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e08b-144">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e08b-145">既に生成されている証明書を使用している場合、証明書の発行者名はアプリケーションの発行元名と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5e08b-145">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="5e08b-146">同じでない場合は、"署名キーが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="5e08b-146">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="5e08b-147">アプリをデジタル署名できませんでした。"</span><span class="sxs-lookup"><span data-stu-id="5e08b-147">The app could not be digitally signed."</span></span> <span data-ttu-id="5e08b-148">エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-148">error.</span></span>

![プロジェクト設定 - プラットフォーム - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="5e08b-150">秘密キーのパスワードを作成するように求めるメッセージが表示されたら、テスト目的の場合は **[なし]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e08b-150">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![新しい証明書の生成](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="5e08b-152">**[File]\(ファイル\) > [Package Project]\(プロジェクトをパッケージ化\)** に移動し、 **[HoloLens]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-152">Go to **File > Package Project** and select **HoloLens**.</span></span>
    * <span data-ttu-id="5e08b-153">パッケージを保存する新しいフォルダーを作成し、 **[Select Folder]\(フォルダーの選択\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e08b-153">Create a new folder to save your package in and click **Select Folder**.</span></span>

6.  <span data-ttu-id="5e08b-154">アプリがパッケージ化されたら、[Windows デバイス ポータル](/windows/mixed-reality/using-the-windows-device-portal)を開き、 **[ビュー] > [アプリ]** に移動して、 **[Deploy apps]\(アプリのデプロイ\)** セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="5e08b-154">Open the [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="5e08b-155">**[参照...]** をクリックし、**ChessApp.appxbundle** ファイルに移動して **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e08b-155">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span>

    * <span data-ttu-id="5e08b-156">デバイスに初めてアプリをインストールする場合は、 **[Allow me to select framework packages]\(フレームワーク パッケージを選択できるようにする\)** の横のボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="5e08b-156">Check the box next to **Allow me to select framework packages** if you're installing the app on your device for the first time.</span></span>
    * <span data-ttu-id="5e08b-157">次のダイアログで、適切な **VCLibs** および **appx** ファイルを組み込みます (デバイスの場合は **arm64**、エミュレーターの場合は **x64**)。</span><span class="sxs-lookup"><span data-stu-id="5e08b-157">In the next dialogue, include the appropriate **VCLibs** and **appx** files, **arm64** for device and **x64** for emulator.</span></span> <span data-ttu-id="5e08b-158">ファイルは、パッケージを保存したフォルダー内の **HoloLens** にあります。</span><span class="sxs-lookup"><span data-stu-id="5e08b-158">You can find the files under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="5e08b-159">**[Install]** (インストール) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="5e08b-159">Click **Install**</span></span>
    * <span data-ttu-id="5e08b-160">これで、 **[All Apps]\(すべてのアプリ\)** に移動して新しくインストールしたアプリをタップして実行するか、**Windows デバイス ポータル** から直接アプリを起動できます。</span><span class="sxs-lookup"><span data-stu-id="5e08b-160">You can now go to **All Apps** and tap the newly installed app to run it, or start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="5e08b-161">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="5e08b-161">Congratulations!</span></span> <span data-ttu-id="5e08b-162">HoloLens Mixed Reality アプリケーションが完成し、準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="5e08b-162">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="5e08b-163">ただし、これが終点ではありません。</span><span class="sxs-lookup"><span data-stu-id="5e08b-163">However, you're not at the end of the road.</span></span> <span data-ttu-id="5e08b-164">MRTK には、空間マッピング、視線入力および音声入力、さらには QR コードなど、プロジェクトに追加できるスタンドアロン機能が多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="5e08b-164">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="5e08b-165">これらの機能の詳細については、[Unreal 開発の概要](/windows/mixed-reality/unreal-development-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5e08b-165">More information on these features can be found in the [Unreal development overview](/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="5e08b-166">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="5e08b-166">Next Development Checkpoint</span></span>

<span data-ttu-id="5e08b-167">用意されている Unreal 開発体験に従っている場合、MRTK コア構成要素を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="5e08b-167">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="5e08b-168">ここから、次の構成要素を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="5e08b-168">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5e08b-169">視線入力</span><span class="sxs-lookup"><span data-stu-id="5e08b-169">Gaze input</span></span>](../unreal-gaze-input.md)

<span data-ttu-id="5e08b-170">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="5e08b-170">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5e08b-171">HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="5e08b-171">HoloLens camera</span></span>](../unreal-hololens-camera.md)

<span data-ttu-id="5e08b-172">いつでも [Unreal 開発チェックポイント](../unreal-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="5e08b-172">You can always go back to the [Unreal development checkpoints](../unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>