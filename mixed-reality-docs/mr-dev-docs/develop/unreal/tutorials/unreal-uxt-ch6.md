---
title: 6. デバイスまたはエミュレーターへのパッケージ化とデプロイ
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用してチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 6
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 7f6f501a5e2cde9fdb6aa3ba1aa973a4ab697fd8
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010549"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="4b29a-104">6.デバイスまたはエミュレーターへのパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="4b29a-104">6. Packaging & deploying to device or emulator</span></span>

<span data-ttu-id="4b29a-105">前のチュートリアルでは、チェスの駒を元の位置にリセットする簡単なボタンを追加しました。</span><span class="sxs-lookup"><span data-stu-id="4b29a-105">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="4b29a-106">この最後のセクションでは、アプリを HoloLens 2 またはエミュレーターで実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="4b29a-106">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="4b29a-107">HoloLens 2 をお持ちの場合は、コンピューターからストリーミングするか、アプリをパッケージ化してデバイス上で直接実行することができます。</span><span class="sxs-lookup"><span data-stu-id="4b29a-107">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="4b29a-108">デバイスがない場合は、エミュレーターで実行するアプリをパッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="4b29a-108">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="4b29a-109">このセクションを完了するまでに、対話式操作と UI を備えた、再生可能な Mixed Reality アプリがデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="4b29a-109">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="4b29a-110">目標</span><span class="sxs-lookup"><span data-stu-id="4b29a-110">Objectives</span></span>

* <span data-ttu-id="4b29a-111">[デバイスのみ] ホログラフィック アプリのリモート処理によって HoloLens 2 にストリーミングする</span><span class="sxs-lookup"><span data-stu-id="4b29a-111">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="4b29a-112">アプリをパッケージ化して HoloLens 2 のデバイスまたはエミュレーターにデプロイする</span><span class="sxs-lookup"><span data-stu-id="4b29a-112">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="4b29a-113">[デバイスのみ] ストリーミング</span><span class="sxs-lookup"><span data-stu-id="4b29a-113">[Device Only] Streaming</span></span>

<span data-ttu-id="4b29a-114">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) は、チャネルを切り替えるのではなく、PC またはスタンドアロンの UWP デバイスから HoloLens 2 にデータをストリーミングすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="4b29a-114">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="4b29a-115">HoloLens から入力データ ストリームを受け取ったリモート処理ホスト アプリにより、仮想イマーシブ ビューでコンテンツがレンダリングされ、Wi-Fi 経由でコンテンツ フレームが HoloLens にストリーミングされます。</span><span class="sxs-lookup"><span data-stu-id="4b29a-115">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="4b29a-116">ストリーミングを使用すると、リモートのイマーシブ ビューを既存のデスクトップ PC ソフトウェアに追加し、より多くのシステム リソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="4b29a-116">Streaming lets you add remote immersive views into existing desktop PC software and has access to more system resources.</span></span>

<span data-ttu-id="4b29a-117">チェス アプリでこのルートを使用する場合は、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b29a-117">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="4b29a-118">Microsoft Store から **Holographic Remoting Player** を HoloLens 2 にインストールし、アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="4b29a-118">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span> <span data-ttu-id="4b29a-119">アプリに表示される IP アドレスをメモします。</span><span class="sxs-lookup"><span data-stu-id="4b29a-119">Note your IP address displayed in the app.</span></span>

2.  <span data-ttu-id="4b29a-120">Unreal エディターに戻り、 **[編集]、[プロジェクトの設定]** の順に移動し、 **[Holographic Remoting]** セクションで **[リモート処理を有効にする]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="4b29a-120">Back in the Unreal editor, go to **Edit > Project Settings** and check **Enable Remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="4b29a-121">エディターを再起動し、デバイスの IP アドレス (Holographic Remoting Player アプリに表示されるもの) を入力し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b29a-121">Restart the editor, then enter your device's IP address (as displayed in the Holographic Remoting Player app), then click **Connect**.</span></span>

<span data-ttu-id="4b29a-122">接続後、 **[Play]\(再生\)** ボタンの右側にあるドロップダウン矢印をクリックし、 **[VR Preview]\(VR プレビュー\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4b29a-122">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="4b29a-123">VR プレビュー ウィンドウでアプリが実行され、HoloLens ヘッドセットにストリーミングされます。</span><span class="sxs-lookup"><span data-stu-id="4b29a-123">The app will run in the VR Preview window, which is streamed to the HoloLens headset.</span></span>

## <a name="packaging-and-deploying-the-app-via-device-portal"></a><span data-ttu-id="4b29a-124">デバイス ポータル経由でのアプリのパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="4b29a-124">Packaging and deploying the app via device portal</span></span>

>[!NOTE]
><span data-ttu-id="4b29a-125">HoloLens 用の Unreal アプリを初めてパッケージ化する場合は、Epic Launcher からサポート ファイルをダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b29a-125">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span>
>- <span data-ttu-id="4b29a-126">**[Editor Preferences]\(エディターの設定\) > [General]\(全般\) > [Source Code]\(ソース コード\) > [Source Code Editor]\(ソース コード エディター\)** に移動し、Visual Studio 2019 が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4b29a-126">Go to **Editor Preferences > General > Source Code > Source Code Editor** and check that Visual Studio 2019 is selected.</span></span>
>- <span data-ttu-id="4b29a-127">Epic Games Launcher の **[ライブラリ]** タブに移動し、 **[起動]** の横にあるドロップダウン矢印を選択して、 **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b29a-127">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span>
>- <span data-ttu-id="4b29a-128">**[対応プラットフォーム]** で、 **[HoloLens 2]** を選択し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b29a-128">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
><span data-ttu-id="4b29a-129">![プロジェクト設定でターゲット プラットフォームを変更する](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="4b29a-129">![Change target platform in project settings](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="4b29a-130">**[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\)** に移動します。</span><span class="sxs-lookup"><span data-stu-id="4b29a-130">Go to **Edit > Project Settings**.</span></span>
    * <span data-ttu-id="4b29a-131">**[Project]\(プロジェクト\) > [Description]\(説明\) > [About]\(情報\) > [Project Name]\(プロジェクト名\)** で、プロジェクト名を追加します。</span><span class="sxs-lookup"><span data-stu-id="4b29a-131">Add a project name under **Project > Description > About > Project Name**.</span></span>
    * <span data-ttu-id="4b29a-132">**[Project]\(プロジェクト\) > [Description]\(説明\) > [Publisher]\(発行元\) > [Company Distinguished Name]\(企業識別名\)** で、「**CN=YourCompanyName**」を追加します。</span><span class="sxs-lookup"><span data-stu-id="4b29a-132">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>
    * <span data-ttu-id="4b29a-133">**[Project]\(プロジェクト\) > [Description]\(説明\) > [Settings]\(設定\)** の **[Start in VR]\(VR で開始\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4b29a-133">Select **Start in VR** under **Project > Description > Settings**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4b29a-134">これらのフィールドのどちらかを空白のままにすると、手順 3 で新しい証明書を作成するときにエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="4b29a-134">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4b29a-135">発行元の名前は、[LADPv3 識別名形式](https://www.ietf.org/rfc/rfc2253.txt)である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b29a-135">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="4b29a-136">発行元の名前の形式が正しくないと、"署名キーが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="4b29a-136">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="4b29a-137">アプリをデジタル署名できませんでした。"</span><span class="sxs-lookup"><span data-stu-id="4b29a-137">The app could not be digitally signed."</span></span> <span data-ttu-id="4b29a-138">エラーがパッケージ化するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="4b29a-138">error upon packaging.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4b29a-139">[Start in VR]\(VR で開始\) を選択しないと、スレート内でアプリケーションの起動が試行されます。</span><span class="sxs-lookup"><span data-stu-id="4b29a-139">Not selecting "Start in VR" will lead your application trying to start in a slate</span></span>

![プロジェクト設定 - 説明](images/unreal-uxt/6-cn-new.PNG)

2.  <span data-ttu-id="4b29a-141">**[プラットフォーム] > [HoloLens]** で **[HoloLens Emulation 用にビルド]** または **[HoloLens Device 用にビルド]** を有効にします。</span><span class="sxs-lookup"><span data-stu-id="4b29a-141">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="4b29a-142">**[パッケージ化]** セクション ( **[証明書に署名]** の横) の **[新規生成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b29a-142">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4b29a-143">既に生成されている証明書を使用している場合、証明書の発行者名はアプリケーションの発行元名と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="4b29a-143">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="4b29a-144">同じでない場合は、"署名キーが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="4b29a-144">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="4b29a-145">アプリをデジタル署名できませんでした。"</span><span class="sxs-lookup"><span data-stu-id="4b29a-145">The app could not be digitally signed."</span></span> <span data-ttu-id="4b29a-146">エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="4b29a-146">error.</span></span>

![プロジェクト設定 - プラットフォーム - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="4b29a-148">秘密キーのパスワードを作成するように求めるメッセージが表示されたら、テスト目的の場合は **[なし]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b29a-148">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![新しい証明書の生成](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="4b29a-150">**[File]\(ファイル\) > [Package Project]\(プロジェクトをパッケージ化\)** に移動し、 **[HoloLens]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4b29a-150">Go to **File > Package Project** and select **HoloLens**.</span></span>
    * <span data-ttu-id="4b29a-151">パッケージを保存する新しいフォルダーを作成し、 **[Select Folder]\(フォルダーの選択\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b29a-151">Create a new folder to save your package in and click **Select Folder**.</span></span>

6.  <span data-ttu-id="4b29a-152">アプリがパッケージ化されたら、[Windows デバイス ポータル](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)を開き、 **[ビュー] > [アプリ]** に移動して、 **[Deploy apps]\(アプリのデプロイ\)** セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="4b29a-152">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="4b29a-153">**[参照...]** をクリックし、**ChessApp.appxbundle** ファイルに移動して **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b29a-153">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span>

    * <span data-ttu-id="4b29a-154">デバイスに初めてアプリをインストールする場合は、 **[Allow me to select framework packages]\(フレームワーク パッケージを選択できるようにする\)** の横のボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="4b29a-154">Check the box next to **Allow me to select framework packages** if you're installing the app on your device for the first time.</span></span>
    * <span data-ttu-id="4b29a-155">次のダイアログで、適切な **VCLibs** および **appx** ファイルを組み込みます (デバイスの場合は **arm64**、エミュレーターの場合は **x64**)。</span><span class="sxs-lookup"><span data-stu-id="4b29a-155">In the next dialogue, include the appropriate **VCLibs** and **appx** files, **arm64** for device and **x64** for emulator.</span></span> <span data-ttu-id="4b29a-156">ファイルは、パッケージを保存したフォルダー内の **HoloLens** にあります。</span><span class="sxs-lookup"><span data-stu-id="4b29a-156">You can find the files under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="4b29a-157">**[Install]** (インストール) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4b29a-157">Click **Install**</span></span>
    * <span data-ttu-id="4b29a-158">これで、 **[All Apps]\(すべてのアプリ\)** に移動して新しくインストールしたアプリをタップして実行するか、**Windows デバイス ポータル** から直接アプリを起動できます。</span><span class="sxs-lookup"><span data-stu-id="4b29a-158">You can now go to **All Apps** and tap the newly installed app to run it, or start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="4b29a-159">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="4b29a-159">Congratulations!</span></span> <span data-ttu-id="4b29a-160">HoloLens Mixed Reality アプリケーションが完成し、準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="4b29a-160">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="4b29a-161">ただし、これが終点ではありません。</span><span class="sxs-lookup"><span data-stu-id="4b29a-161">However, you're not at the end of the road.</span></span> <span data-ttu-id="4b29a-162">MRTK には、空間マッピング、視線入力および音声入力、さらには QR コードなど、プロジェクトに追加できるスタンドアロン機能が多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="4b29a-162">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="4b29a-163">これらの機能の詳細については、[Unreal 開発の概要](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b29a-163">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="4b29a-164">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="4b29a-164">Next Development Checkpoint</span></span>

<span data-ttu-id="4b29a-165">用意されている Unreal 開発体験に従っている場合、MRTK コア構成要素を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="4b29a-165">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="4b29a-166">ここから、次の構成要素を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="4b29a-166">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4b29a-167">視線入力</span><span class="sxs-lookup"><span data-stu-id="4b29a-167">Gaze input</span></span>](../unreal-gaze-input.md)

<span data-ttu-id="4b29a-168">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="4b29a-168">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4b29a-169">HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="4b29a-169">HoloLens camera</span></span>](../unreal-hololens-camera.md)

<span data-ttu-id="4b29a-170">いつでも [Unreal 開発チェックポイント](../unreal-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="4b29a-170">You can always go back to the [Unreal development checkpoints](../unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
