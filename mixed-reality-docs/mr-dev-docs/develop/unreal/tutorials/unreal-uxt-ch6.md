---
title: 6. デバイスまたはエミュレーターへのパッケージ化とデプロイ
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用して簡単なチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 6
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, 入門, mrtk, uxt, UX ツール, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: cbdbf87d75dcfc56c8eea52f7dff4a646f3b6a5d
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679821"
---
# <a name="6-packaging--deploying-to-device-or-emulator"></a><span data-ttu-id="228fb-104">6.デバイスまたはエミュレーターへのパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="228fb-104">6. Packaging & deploying to device or emulator</span></span>

## <a name="overview"></a><span data-ttu-id="228fb-105">概要</span><span class="sxs-lookup"><span data-stu-id="228fb-105">Overview</span></span>

<span data-ttu-id="228fb-106">前のチュートリアルでは、チェスの駒を元の位置にリセットする簡単なボタンを追加しました。</span><span class="sxs-lookup"><span data-stu-id="228fb-106">In the previous tutorial, you added a simple button that resets the chess piece to its original position.</span></span> <span data-ttu-id="228fb-107">この最後のセクションでは、アプリを HoloLens 2 またはエミュレーターで実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="228fb-107">In this final section, you'll get the app ready to run on a HoloLens 2 or an Emulator.</span></span> <span data-ttu-id="228fb-108">HoloLens 2 をお持ちの場合は、コンピューターからストリーミングするか、アプリをパッケージ化してデバイス上で直接実行することができます。</span><span class="sxs-lookup"><span data-stu-id="228fb-108">If you have a HoloLens 2, you can either stream from your computer or package the app to run directly on the device.</span></span> <span data-ttu-id="228fb-109">デバイスがない場合は、エミュレーターで実行するアプリをパッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="228fb-109">If you don't have a device, you'll be packaging the app to run on the Emulator.</span></span> <span data-ttu-id="228fb-110">このセクションを完了するまでに、対話式操作と UI を備えた、再生可能な Mixed Reality アプリがデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="228fb-110">By the end of this section, you'll have a deployed mixed reality app that you can play, complete with interactions and UI.</span></span>

## <a name="objectives"></a><span data-ttu-id="228fb-111">目標</span><span class="sxs-lookup"><span data-stu-id="228fb-111">Objectives</span></span>

* <span data-ttu-id="228fb-112">[デバイスのみ] ホログラフィック アプリのリモート処理によって HoloLens 2 にストリーミングする</span><span class="sxs-lookup"><span data-stu-id="228fb-112">[Device only] Streaming to HoloLens 2 with holographic app remoting</span></span>
* <span data-ttu-id="228fb-113">アプリをパッケージ化して HoloLens 2 のデバイスまたはエミュレーターにデプロイする</span><span class="sxs-lookup"><span data-stu-id="228fb-113">Packaging and deploying the app to a HoloLens 2 device or emulator</span></span>

## <a name="device-only-streaming"></a><span data-ttu-id="228fb-114">[デバイスのみ] ストリーミング</span><span class="sxs-lookup"><span data-stu-id="228fb-114">[Device Only] Streaming</span></span>
<span data-ttu-id="228fb-115">この場合、[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) は、チャネルを切り替えるのではなく、PC またはスタンドアロンの UWP デバイスから HoloLens 2 にデータをストリーミングすることを意味します。</span><span class="sxs-lookup"><span data-stu-id="228fb-115">[Holographic Remoting](https://docs.microsoft.com/windows/mixed-reality/add-holographic-remoting) in this case means streaming data from a PC or standalone UWP device to the HoloLens 2, not switching the channel.</span></span> <span data-ttu-id="228fb-116">これは、リモート処理ホスト アプリが HoloLens から入力データ ストリームを受け取り、仮想イマーシブ ビューでコンテンツをレンダリングし、Wi-Fi 経由でコンテンツ フレームを HoloLens にストリームするという仕組みになっています。</span><span class="sxs-lookup"><span data-stu-id="228fb-116">The way this works is a remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens over Wi-Fi.</span></span> <span data-ttu-id="228fb-117">ストリーミングを使用すると、リモートのイマーシブ ビューを既存のデスクトップ PC ソフトウェアに追加し、より多くのシステム リソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="228fb-117">Streaming allows you to add remote immersive views into existing desktop PC software and has access to more system resources.</span></span>

<span data-ttu-id="228fb-118">チェス アプリでこのルートを使用する場合は、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="228fb-118">If you're going this route with the chess app, you'll need a few things:</span></span>

1.  <span data-ttu-id="228fb-119">Microsoft Store から **Holographic Remoting Player** を HoloLens 2 にインストールし、アプリを実行します。</span><span class="sxs-lookup"><span data-stu-id="228fb-119">Install the **Holographic Remoting Player** from the Microsoft Store on your HoloLens 2 and run the app.</span></span> <span data-ttu-id="228fb-120">アプリに表示される IP アドレスをメモします。</span><span class="sxs-lookup"><span data-stu-id="228fb-120">Note your IP address displayed in the app.</span></span>

2.  <span data-ttu-id="228fb-121">Unreal エディターに戻り、 **[編集]、[プロジェクトの設定]** の順に移動し、 **[Holographic Remoting]** セクションで **[リモート処理を有効にする]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="228fb-121">Back in the Unreal editor, go to **Edit > Project Settings** and check **Enable Remoting** in the **Holographic Remoting** section.</span></span>

3.  <span data-ttu-id="228fb-122">エディターを再起動し、デバイスの IP アドレス (Holographic Remoting Player アプリに表示されるもの) を入力し、 **[接続]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="228fb-122">Restart the editor, then enter your device's IP address (as displayed in the Holographic Remoting Player app), then click **Connect**.</span></span>

<span data-ttu-id="228fb-123">接続後、 **[Play]\(再生\)** ボタンの右側にあるドロップダウン矢印をクリックし、 **[VR Preview]\(VR プレビュー\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="228fb-123">Once you’re connected, click the drop-down arrow to the right of the **Play** button and select **VR Preview**.</span></span> <span data-ttu-id="228fb-124">これにより、VR プレビュー ウィンドウでアプリが実行され、HoloLens ヘッドセットにストリーミングされます。</span><span class="sxs-lookup"><span data-stu-id="228fb-124">This will run the app in the VR Preview window, which is streamed to the HoloLens headset.</span></span>

## <a name="packaging-and-deploying-the-app-via-device-portal"></a><span data-ttu-id="228fb-125">デバイス ポータル経由でのアプリのパッケージ化とデプロイ</span><span class="sxs-lookup"><span data-stu-id="228fb-125">Packaging and deploying the app via device portal</span></span>

>[!NOTE]
><span data-ttu-id="228fb-126">HoloLens 用の Unreal アプリを初めてパッケージ化する場合は、Epic Launcher からサポート ファイルをダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="228fb-126">If this is your first time packaging an Unreal app for HoloLens, you'll need to download supporting files from the Epic Launcher.</span></span>
>- <span data-ttu-id="228fb-127">**[Editor Preferences]\(エディターの設定\) > [General]\(全般\) > [Source Code]\(ソース コード\) > [Source Code Editor]\(ソース コード エディター\)** に移動し、Visual Studio 2019 が選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="228fb-127">Go to **Editor Preferences > General > Source Code > Source Code Editor** and check that Visual Studio 2019 is selected.</span></span>
>- <span data-ttu-id="228fb-128">Epic Games Launcher の **[ライブラリ]** タブに移動し、 **[起動]** の横にあるドロップダウン矢印を選択して、 **[オプション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="228fb-128">Go to the **Library** tab in the Epic Games Launcher, select the dropdown arrow next to **Launch** >and click **Options**.</span></span>
>- <span data-ttu-id="228fb-129">**[対応プラットフォーム]** で、 **[HoloLens 2]** を選択し、 **[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="228fb-129">Under **Target Platforms**, select **HoloLens 2** and click **Apply**.</span></span>
><span data-ttu-id="228fb-130">![プロジェクト設定でターゲット プラットフォームを変更する](images/unreal-uxt/6-installationoptions.PNG)</span><span class="sxs-lookup"><span data-stu-id="228fb-130">![Change target platform in project settings](images/unreal-uxt/6-installationoptions.PNG)</span></span>

1.  <span data-ttu-id="228fb-131">**[Edit]\(編集\) > [Project Settings]\(プロジェクト設定\)** に移動します。</span><span class="sxs-lookup"><span data-stu-id="228fb-131">Go to **Edit > Project Settings**.</span></span>
    * <span data-ttu-id="228fb-132">**[Project]\(プロジェクト\) > [Description]\(説明\) > [About]\(情報\) > [Project Name]\(プロジェクト名\)** で、プロジェクト名を追加します。</span><span class="sxs-lookup"><span data-stu-id="228fb-132">Add a project name under **Project > Description > About > Project Name**.</span></span>
    * <span data-ttu-id="228fb-133">**[Project]\(プロジェクト\) > [Description]\(説明\) > [Publisher]\(発行元\) > [Company Distinguished Name]\(企業識別名\)** で、「**CN=YourCompanyName**」を追加します。</span><span class="sxs-lookup"><span data-stu-id="228fb-133">Add **CN=YourCompanyName** under **Project > Description > Publisher > Company Distinguished Name**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="228fb-134">これらのフィールドのどちらかを空白のままにすると、手順 3 で新しい証明書を作成するときにエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="228fb-134">Leaving either of these fields blank will result in an error when you try and generate a new certificate in step 3.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="228fb-135">発行元の名前は、[LADPv3 識別名形式](https://www.ietf.org/rfc/rfc2253.txt)である必要があります。</span><span class="sxs-lookup"><span data-stu-id="228fb-135">The publisher's name must be in [LADPv3 Distinguished Names Format](https://www.ietf.org/rfc/rfc2253.txt).</span></span> <span data-ttu-id="228fb-136">発行元の名前の形式が正しくないと、"署名キーが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="228fb-136">A malformed publisher's name leads to the "Signing key not found.</span></span> <span data-ttu-id="228fb-137">アプリをデジタル署名できませんでした。"</span><span class="sxs-lookup"><span data-stu-id="228fb-137">The app could not be digitally signed."</span></span> <span data-ttu-id="228fb-138">エラーがパッケージ化するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="228fb-138">error upon packaging.</span></span>

![プロジェクト設定 - 説明](images/unreal-uxt/6-cn.PNG)

2.  <span data-ttu-id="228fb-140">**[プラットフォーム] > [HoloLens]** で **[HoloLens Emulation 用にビルド]** または **[HoloLens Device 用にビルド]** を有効にします。</span><span class="sxs-lookup"><span data-stu-id="228fb-140">Enable **Build for HoloLens Emulation** and/or **Build for HoloLens Device** under **Platforms > HoloLens**.</span></span>

3.  <span data-ttu-id="228fb-141">**[パッケージ化]** セクション ( **[証明書に署名]** の横) の **[新規生成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="228fb-141">Click **Generate new** in the **Packaging** section (next to **Signing Certificate**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="228fb-142">既に生成されている証明書を使用している場合、証明書の発行者名はアプリケーションの発行元名と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="228fb-142">If you're using an already generated certificate, then the certificate's publisher name must be the same as the application's publisher name.</span></span> <span data-ttu-id="228fb-143">同じでない場合は、"署名キーが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="228fb-143">Otherwise it leads to the "Signing key not found.</span></span> <span data-ttu-id="228fb-144">アプリをデジタル署名できませんでした。"</span><span class="sxs-lookup"><span data-stu-id="228fb-144">The app could not be digitally signed."</span></span> <span data-ttu-id="228fb-145">エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="228fb-145">error.</span></span>

![プロジェクト設定 - プラットフォーム - HoloLens](images/unreal-uxt/6-packaging.PNG)

4. <span data-ttu-id="228fb-147">秘密キーのパスワードを作成するように求めるメッセージが表示されたら、テスト目的の場合は **[なし]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="228fb-147">Click **None** for testing purposes when you're prompted to create a Private Key Password.</span></span>

![新しい証明書の生成](images/unreal-uxt/6-private-key-testing.png)

5. <span data-ttu-id="228fb-149">**[File]\(ファイル\) > [Package Project]\(プロジェクトをパッケージ化\)** に移動し、 **[HoloLens]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="228fb-149">Go to **File > Package Project** and select **HoloLens**.</span></span>
    * <span data-ttu-id="228fb-150">パッケージを保存する新しいフォルダーを作成し、 **[Select Folder]\(フォルダーの選択\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="228fb-150">Create a new folder to save your package in and click **Select Folder**.</span></span>

6.  <span data-ttu-id="228fb-151">アプリがパッケージ化されたら、[Windows デバイス ポータル](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal)を開き、 **[ビュー] > [アプリ]** に移動して、 **[Deploy apps]\(アプリのデプロイ\)** セクションを見つけます。</span><span class="sxs-lookup"><span data-stu-id="228fb-151">Open the [Windows Device Portal](https://docs.microsoft.com/windows/mixed-reality/using-the-windows-device-portal) once the app is packaged, go to **Views > Apps** and find the **Deploy apps** section.</span></span>

7.  <span data-ttu-id="228fb-152">**[参照...]** をクリックし、**ChessApp.appxbundle** ファイルに移動して **[開く]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="228fb-152">Click **Browse...**, go to your **ChessApp.appxbundle** file and click **Open**.</span></span>

    * <span data-ttu-id="228fb-153">デバイスに初めてアプリをインストールする場合は、 **[Allow me to select framework packages]\(フレームワーク パッケージを選択できるようにする\)** の横のボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="228fb-153">Check the box next to **Allow me to select framework packages** if this is the first time you're installing the app on your device.</span></span>
    * <span data-ttu-id="228fb-154">次のダイアログで、適切な **VCLibs** および **appx** ファイルを組み込みます (デバイスの場合は arm64、エミュレーターの場合は x64)。</span><span class="sxs-lookup"><span data-stu-id="228fb-154">In the next dialogue, include the appropriate **VCLibs** and **appx** files (arm64 for device, x64 for emulator).</span></span> <span data-ttu-id="228fb-155">これらのファイルは、パッケージを保存したフォルダー内の **HoloLens** にあります。</span><span class="sxs-lookup"><span data-stu-id="228fb-155">You can find these under **HoloLens** inside the folder where you saved your package.</span></span>

8.  <span data-ttu-id="228fb-156">**[Install]** (インストール) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="228fb-156">Click **Install**</span></span>
    * <span data-ttu-id="228fb-157">これで、**すべてのアプリ** に移動して新しくインストールしたアプリをタップして実行するか、**Windows デバイス ポータル** から直接アプリを起動できます。</span><span class="sxs-lookup"><span data-stu-id="228fb-157">You can now go to **All Apps** and tap the newly installed app to run it, or you can start the app directly from the **Windows Device Portal**.</span></span> 

<span data-ttu-id="228fb-158">お疲れさまでした。</span><span class="sxs-lookup"><span data-stu-id="228fb-158">Congratulations!</span></span> <span data-ttu-id="228fb-159">HoloLens Mixed Reality アプリケーションが完成し、準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="228fb-159">Your HoloLens mixed reality application is finished and ready to go.</span></span> <span data-ttu-id="228fb-160">ただし、これは目的地ではありません。</span><span class="sxs-lookup"><span data-stu-id="228fb-160">However, this isn't the end of the road.</span></span> <span data-ttu-id="228fb-161">MRTK には、空間マッピング、視線入力および音声入力、さらには QR コードなど、プロジェクトに追加できるスタンドアロン機能が多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="228fb-161">MRTK has lots of standalone features that you can add to your projects, including spatial mapping, gaze and voice input, and even QR codes.</span></span> <span data-ttu-id="228fb-162">これらの機能の詳細については、[Unreal 開発の概要](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="228fb-162">More information on these features can be found in the [Unreal development overview](https://docs.microsoft.com/windows/mixed-reality/unreal-development-overview).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="228fb-163">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="228fb-163">Next Development Checkpoint</span></span>

<span data-ttu-id="228fb-164">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="228fb-164">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="228fb-165">ここから、次の構成要素に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="228fb-165">From here, you can proceed to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="228fb-166">視線入力</span><span class="sxs-lookup"><span data-stu-id="228fb-166">Gaze input</span></span>](../unreal-gaze-input.md)

<span data-ttu-id="228fb-167">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="228fb-167">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="228fb-168">HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="228fb-168">HoloLens camera</span></span>](../unreal-hololens-camera.md)

<span data-ttu-id="228fb-169">いつでも [Unreal 開発チェックポイント](../unreal-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="228fb-169">You can always go back to the [Unreal development checkpoints](../unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>
