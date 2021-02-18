---
title: Visual Studio を使用した配置とデバッグ
description: Visual Studio を使用して、HoloLens および Windows Mixed Reality 用のアプリをビルド、デバッグ、配置する方法について説明します。
author: pbarnettms
ms.author: pbarnett
ms.date: 04/13/2020
ms.topic: article
ms.localizationpriority: high
keywords: Visual Studio, HoloLens, Mixed Reality, デバッグ, 配置
ms.openlocfilehash: 2ab89311163a48ee3c14511446a1498ce883a232
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496096"
---
# <a name="using-visual-studio-to-deploy-and-debug"></a><span data-ttu-id="2ab04-104">Visual Studio を使用した配置とデバッグ</span><span class="sxs-lookup"><span data-stu-id="2ab04-104">Using Visual Studio to deploy and debug</span></span>

<span data-ttu-id="2ab04-105">DirectX と Unity のどちらを使用して Mixed Reality アプリを開発する場合でも、デバッグと配置には Visual Studio が役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-105">Whether you're using DirectX or Unity to develop your mixed reality app, Visual Studio is your go-to tool for debugging and deployment.</span></span> <span data-ttu-id="2ab04-106">このセクションでは、次の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-106">In this section, you will learn how to:</span></span>
* <span data-ttu-id="2ab04-107">Visual Studio を使用して、HoloLens または Windows Mixed Reality のイマーシブ ヘッドセットにアプリケーションを配置する。</span><span class="sxs-lookup"><span data-stu-id="2ab04-107">Deploy applications to your HoloLens or Windows Mixed Reality immersive headset through Visual Studio.</span></span>
* <span data-ttu-id="2ab04-108">Visual Studio に組み込まれている HoloLens エミュレーターを使用する。</span><span class="sxs-lookup"><span data-stu-id="2ab04-108">Use the HoloLens emulator built in to Visual Studio.</span></span>
* <span data-ttu-id="2ab04-109">Mixed Reality アプリをデバッグする。</span><span class="sxs-lookup"><span data-stu-id="2ab04-109">Debug mixed reality apps.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ab04-110">前提条件</span><span class="sxs-lookup"><span data-stu-id="2ab04-110">Prerequisites</span></span>

1. <span data-ttu-id="2ab04-111">インストール手順については、「[ツールのインストール](../../develop/install-the-tools.md#installation-checklist)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ab04-111">See [Install the Tools](../../develop/install-the-tools.md#installation-checklist) for installation instructions.</span></span>
2. <span data-ttu-id="2ab04-112">Visual Studio で新しいユニバーサル Windows アプリ プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-112">Create a new Universal Windows app project in Visual Studio.</span></span>  <span data-ttu-id="2ab04-113">HoloLens (第 1 世代) の場合は、Visual Studio 2017 以降を使用します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-113">For HoloLens (1st gen), use Visual Studio 2017 or newer.</span></span>  <span data-ttu-id="2ab04-114">HoloLens 2 の場合は、Visual Studio 2019 16.2 以降を使用します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-114">For HoloLens 2, use Visual Studio 2019 16.2 or newer.</span></span> <span data-ttu-id="2ab04-115">C# と C++ がサポートされています </span><span class="sxs-lookup"><span data-stu-id="2ab04-115">C# and C++ are supported.</span></span> <span data-ttu-id="2ab04-116">(または、[Unity でアプリを作成する](../../develop/unity/tutorials/holograms-100.md)ための手順に従ってください)。</span><span class="sxs-lookup"><span data-stu-id="2ab04-116">(Or follow the instructions to [create an app in Unity](../../develop/unity/tutorials/holograms-100.md).)</span></span>

## <a name="enabling-developer-mode"></a><span data-ttu-id="2ab04-117">開発者モードを有効にする</span><span class="sxs-lookup"><span data-stu-id="2ab04-117">Enabling Developer Mode</span></span>

<span data-ttu-id="2ab04-118">まず、デバイスで **開発者モード** を有効にして、Visual Studio から接続できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2ab04-118">Start by enabling **Developer Mode** on your device, so Visual Studio can connect to it.</span></span>

### <a name="hololens"></a><span data-ttu-id="2ab04-119">HoloLens</span><span class="sxs-lookup"><span data-stu-id="2ab04-119">HoloLens</span></span>

1. <span data-ttu-id="2ab04-120">HoloLens の電源を入れ、デバイスを装着します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-120">Turn on your HoloLens and put on the device.</span></span>
2. <span data-ttu-id="2ab04-121">[スタート ジェスチャ](../../design/system-gesture.md)を使用して、メイン メニューを開きます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-121">Use the [start gesture](../../design/system-gesture.md) to launch the main menu.</span></span>
3. <span data-ttu-id="2ab04-122">**[Settings]\(設定\)** タイルを選択して、環境でアプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-122">Select the **Settings** tile to launch the app in your environment.</span></span>
4. <span data-ttu-id="2ab04-123">**[Update]** (更新) メニュー項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-123">Select the **Update** menu item.</span></span>
5. <span data-ttu-id="2ab04-124">**[For developers]** (開発者向け) メニュー項目を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-124">Select the **For developers** menu item.</span></span>
6. <span data-ttu-id="2ab04-125">**[開発者モード]** を有効にして Visual Studio から HoloLens にアプリを配置できるようにします。</span><span class="sxs-lookup"><span data-stu-id="2ab04-125">Enable **Developer Mode** to deploy apps from Visual Studio to your HoloLens.</span></span>
7. <span data-ttu-id="2ab04-126">省略可能: 下にスクロールして **[デバイス ポータル]** も有効にします。これにより、Web ブラウザーから HoloLens 上の [Windows デバイス ポータル](using-the-windows-device-portal.md)に接続できます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-126">Optional: Scroll down and also enable **Device Portal**, which lets you connect to the [Windows Device Portal](using-the-windows-device-portal.md) on your HoloLens from a web browser.</span></span>

### <a name="windows-pc"></a><span data-ttu-id="2ab04-127">Windows PC</span><span class="sxs-lookup"><span data-stu-id="2ab04-127">Windows PC</span></span>

<span data-ttu-id="2ab04-128">PC に接続された Windows Mixed Reality ヘッドセットを使用している場合、PC 上で **[開発者モード]** を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ab04-128">If you're working with a Windows Mixed Reality headset connected to your PC, you must enable **Developer Mode** on the PC.</span></span>
1. <span data-ttu-id="2ab04-129">**[設定]** に移動します</span><span class="sxs-lookup"><span data-stu-id="2ab04-129">Go to **Settings**</span></span>
2. <span data-ttu-id="2ab04-130">**[更新とセキュリティ]** を選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-130">Select **Update and Security**</span></span>
3. <span data-ttu-id="2ab04-131">**[開発者向け]** を選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-131">Select **For developers**</span></span>
4. <span data-ttu-id="2ab04-132">**[開発者モード]** を有効にして、選択した設定の免責事項を読み、[はい] を選択して変更を確定します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-132">Enable **Developer Mode**, read the disclaimer for the setting you chose, then select Yes to accept the change.</span></span>

## <a name="deploying-a-hololens-app-over-wi-fi"></a><span data-ttu-id="2ab04-133">Wi-Fi 経由での HoloLens アプリの配置</span><span class="sxs-lookup"><span data-stu-id="2ab04-133">Deploying a HoloLens app over Wi-Fi</span></span> 

<span data-ttu-id="2ab04-134">次のプロパティを使用して Visual Studio プロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-134">Configure your Visual Studio project with the following properties:</span></span>

1. <span data-ttu-id="2ab04-135">アプリのコンパイル オプションを選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-135">Select your apps compilation options</span></span>
    * <span data-ttu-id="2ab04-136">Unity プロジェクトの場合、 **[Release]\(リリース\)** または **[Master]\(マスター\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-136">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="2ab04-137">それ以外のプロジェクトの場合、 **[Release]\(リリース\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-137">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="2ab04-138">各コンパイル オプションの完全な定義については、[Visual Studio ソリューションのエクスポートとビルド](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ab04-138">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="2ab04-139">お使いのデバイスに基づいて、ビルド構成を選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-139">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="2ab04-140">[配置ターゲット] ドロップダウン メニューで **[リモート マシン]** を選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-140">Select **Remote Machine** in the deployment target drop-down menu</span></span>

![Visual Studio でのリモート マシンの配置ターゲット](images/remotemachinesetting_arm64.png)

<span data-ttu-id="2ab04-142">次に、リモート接続を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ab04-142">Next, you need to set your remote connection.</span></span> <span data-ttu-id="2ab04-143">C++ および JavaScript プロジェクトの場合は、 **[プロジェクト] > [プロパティ] > [構成プロパティ] > [デバッグ]** に移動します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-143">For C++ and JavaScript projects, go to **Project > Properties > Configuration Properties > Debugging**.</span></span> <span data-ttu-id="2ab04-144">C# プロジェクトで作業している場合は、ダイアログが自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-144">If you're working in a C# project, a dialog should automatically appear.</span></span>

> [!NOTE]
> <span data-ttu-id="2ab04-145">リモート接続ダイアログが C# プロジェクトに表示されない場合は、 **[プロパティ] > [デバッグ]** から手動で開けます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-145">If the remote connection dialog doesn't appear in your C# project, you can open it manually from **Properties > Debug**.</span></span>

1. <span data-ttu-id="2ab04-146">**[アドレス]** または **[コンピューター名]** フィールドに、デバイスの IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-146">Enter the IP address of your device in the **Address** or **Machine Name** field.</span></span> 
    * <span data-ttu-id="2ab04-147">IP アドレスは、HoloLens の **[設定] > [ネットワークとインターネット] > [詳細オプション]** で確認できます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-147">You can find the IP address on your HoloLens under **Settings > Network & Internet > Advanced Options**</span></span>
    * <span data-ttu-id="2ab04-148">自動検出機能に頼るのではなく、IP アドレスを常に手動で入力することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2ab04-148">We always recommend manually entering your IP address rather than depending on the Auto Detected feature</span></span>

2. <span data-ttu-id="2ab04-149">**認証モード** を **[ユニバーサル (暗号化されていないプロトコル)]** に設定します</span><span class="sxs-lookup"><span data-stu-id="2ab04-149">Set the **Authentication Mode** to **Universal (Unencrypted protocol)**</span></span>

  ![Visual Studio の [リモート接続] ダイアログ](images/remotedeploy.png)

3. <span data-ttu-id="2ab04-151">必要に応じて、アプリをビルド、配置、デバッグします</span><span class="sxs-lookup"><span data-stu-id="2ab04-151">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="2ab04-152">**[デバッグ] > [デバッグの開始]** を選択して、アプリをデプロイし、デバッグを開始します</span><span class="sxs-lookup"><span data-stu-id="2ab04-152">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="2ab04-153">デバッグを行わずにビルドと配置を行うには、 **[Build]\(ビルド\) > [配置]** を選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-153">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Visual Studio でのデバッグなしの開始](images/deploywithdebugging.png)

4. <span data-ttu-id="2ab04-155">PC から HoloLens にアプリを初めて配置するときは、PIN の入力を求められます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-155">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="2ab04-156">後述する「**デバイスのペアリング**」の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-156">Follow the **Pairing your device** instructions below.</span></span>

## <a name="deploying-a-hololens-app-over-usb"></a><span data-ttu-id="2ab04-157">USB 経由での HoloLens アプリの配置</span><span class="sxs-lookup"><span data-stu-id="2ab04-157">Deploying a HoloLens app over USB</span></span> 

<br>

>[!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Deploying-your-HoloLens-2-application/player?format=ny]

1. <span data-ttu-id="2ab04-158">アプリのコンパイル オプションを選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-158">Select your apps compilation options</span></span>
    * <span data-ttu-id="2ab04-159">Unity プロジェクトの場合、 **[Release]\(リリース\)** または **[Master]\(マスター\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-159">For Unity projects, choose either **Release** or **Master**</span></span> 
    * <span data-ttu-id="2ab04-160">それ以外のプロジェクトの場合、 **[Release]\(リリース\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-160">For all other projects, choose **Release**</span></span>

> [!NOTE]
> <span data-ttu-id="2ab04-161">各コンパイル オプションの完全な定義については、[Visual Studio ソリューションのエクスポートとビルド](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ab04-161">You can find complete definitions for each compilation option in [exporting and building Visual Studio solutions](../unity/exporting-and-building-a-unity-visual-studio-solution.md#building-and-deploying-a-unity-visual-studio-solution).</span></span>

2. <span data-ttu-id="2ab04-162">お使いのデバイスに基づいて、ビルド構成を選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-162">Select your build configuration based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="2ab04-163">[配置ターゲット] ドロップダウン メニューで **[デバイス]** を選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-163">Select **Device** in the deployment target drop-down menu</span></span>

![Visual Studio でのデバイスの配置](images/buildsettingsusbdeploy_arm64.png)

4. <span data-ttu-id="2ab04-165">必要に応じて、アプリをビルド、配置、デバッグします</span><span class="sxs-lookup"><span data-stu-id="2ab04-165">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="2ab04-166">**[デバッグ] > [デバッグの開始]** を選択して、アプリをデプロイし、デバッグを開始します</span><span class="sxs-lookup"><span data-stu-id="2ab04-166">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="2ab04-167">デバッグを行わずにビルドと配置を行うには、 **[Build]\(ビルド\) > [配置]** を選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-167">Select **Build > Deploy** to build and deploy without debugging</span></span>

![Visual Studio でのデバッグなしの開始](images/deploywithdebugging.png)</br>

5. <span data-ttu-id="2ab04-169">PC から HoloLens にアプリを初めて配置するときは、PIN の入力を求められます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-169">The first time you deploy an app to your HoloLens from your PC, you'll be prompted for a PIN.</span></span> <span data-ttu-id="2ab04-170">後述する「**デバイスのペアリング**」の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-170">Follow the **Pairing your device** instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="2ab04-171">アプリを USB 経由で配置することでかなりのラグ タイムが発生する場合は、前のセクションで説明した[リモート コンピューターの手順](#deploying-a-hololens-app-over-wi-fi)に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2ab04-171">If you're seeing considerable lag time with your apps deployment over USB, we recommend using the [remote machine instructions](#deploying-a-hololens-app-over-wi-fi) in the previous section.</span></span>

## <a name="deploying-an-app-to-the-hololens-emulator"></a><span data-ttu-id="2ab04-172">HoloLens エミュレーターへのアプリの配置</span><span class="sxs-lookup"><span data-stu-id="2ab04-172">Deploying an app to the HoloLens Emulator</span></span>

1. <span data-ttu-id="2ab04-173">**[HoloLens 2 または HoloLens (第 1 世代) エミュレーターがインストールされている](../install-the-tools.md#installation-checklist)** ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-173">Make sure you've **[installed either the HoloLens 2 or HoloLens (1st gen) Emulator](../install-the-tools.md#installation-checklist)**</span></span>
2. <span data-ttu-id="2ab04-174">お使いのデバイスに基づいて、ビルド構成とエミュレーターを選択します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-174">Select your build configuration and emulator based on your device</span></span>

[!INCLUDE[](includes/vs-wifi-hl-include.md)]

3. <span data-ttu-id="2ab04-175">必要に応じて、アプリをビルド、配置、デバッグします</span><span class="sxs-lookup"><span data-stu-id="2ab04-175">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="2ab04-176">**[デバッグ] > [デバッグの開始]** を選択して、アプリをデプロイし、デバッグを開始します</span><span class="sxs-lookup"><span data-stu-id="2ab04-176">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="2ab04-177">デバッグを行わずにビルドと配置を行うには、 **[Build]\(ビルド\) > [配置]** を選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-177">Select **Build > Deploy** to build and deploy without debuggingg</span></span>

![Visual Studio でのデバッグなしの開始](images/deploywithdebugging.png)

## <a name="deploying-a-vr-app-to-your-local-pc"></a><span data-ttu-id="2ab04-179">ローカル PC への VR アプリの配置</span><span class="sxs-lookup"><span data-stu-id="2ab04-179">Deploying a VR app to your Local PC</span></span> 

<span data-ttu-id="2ab04-180">PC または [Mixed Reality シミュレーター](using-the-windows-mixed-reality-simulator.md)に接続する Windows Mixed Reality イマーシブ ヘッドセットを使用するには:</span><span class="sxs-lookup"><span data-stu-id="2ab04-180">To use a Windows Mixed Reality immersive headset that connects to your PC or the [Mixed Reality simulator](using-the-windows-mixed-reality-simulator.md):</span></span>
1. <span data-ttu-id="2ab04-181">アプリに合わせて **[x86]** または **[x64]** ビルド構成を選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-181">Select an **x86** or **x64** build configuration for your app</span></span>
2. <span data-ttu-id="2ab04-182">[配置ターゲット] ドロップダウン メニューで **[ローカル コンピューター]** を選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-182">Select **Local Machine** in the deployment target drop-down menu</span></span>
3. <span data-ttu-id="2ab04-183">必要に応じて、アプリをビルド、配置、デバッグします</span><span class="sxs-lookup"><span data-stu-id="2ab04-183">Build, deploy, and debug your app based on your needs</span></span>
    * <span data-ttu-id="2ab04-184">**[デバッグ] > [デバッグの開始]** を選択して、アプリをデプロイし、デバッグを開始します</span><span class="sxs-lookup"><span data-stu-id="2ab04-184">Select **Debug > Start debugging** to deploy your app and start debugging</span></span>
    * <span data-ttu-id="2ab04-185">デバッグを行わずにビルドと配置を行うには、 **[Build]\(ビルド\) > [配置]** を選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-185">Select **Build > Deploy** to build and deploy without debugging</span></span>

## <a name="pairing-your-device"></a><span data-ttu-id="2ab04-186">デバイスのペアリング</span><span class="sxs-lookup"><span data-stu-id="2ab04-186">Pairing your device</span></span>

<span data-ttu-id="2ab04-187">Visual Studio から HoloLens にアプリを初めて配置するときは、PIN の入力を求められます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-187">The first time you deploy an app from Visual Studio to your HoloLens, you'll be prompted for a PIN.</span></span> <span data-ttu-id="2ab04-188">HoloLens 上で、[Settings]\(設定\) アプリを起動して PIN を生成し、 **[Update]\(更新\) > [For Developers]\(開発者向け\)** に移動し、 **[Pair]\(ペアリング\)** をタップします。</span><span class="sxs-lookup"><span data-stu-id="2ab04-188">On the HoloLens, generate a PIN by launching the Settings app, go to **Update > For Developers**, and tap on **Pair**.</span></span> <span data-ttu-id="2ab04-189">HoloLens に PIN が表示されたら、それを Visual Studio に入力します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-189">When the PIN is displayed on your HoloLens, type it into Visual Studio.</span></span> <span data-ttu-id="2ab04-190">ペアリングが完了したら、HoloLens で **[Done]\(完了\)** をタップしてダイアログを閉じます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-190">After pairing is complete, tap **Done** on your HoloLens to dismiss the dialog.</span></span> <span data-ttu-id="2ab04-191">この PC は HoloLens とペアリングされたので、アプリを自動的に配置できます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-191">This PC is now paired with the HoloLens and you can deploy apps automatically.</span></span> <span data-ttu-id="2ab04-192">HoloLens にアプリを配置するために使うすべての PC に対して、これらの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-192">Repeat these steps for every PC that's used to deploy apps to your HoloLens.</span></span>

<span data-ttu-id="2ab04-193">すべてのペアリング済みコンピューターから HoloLens のペアリングを解除するには:</span><span class="sxs-lookup"><span data-stu-id="2ab04-193">To unpair your HoloLens from all paired computers:</span></span>
* <span data-ttu-id="2ab04-194">**[Settings]\(設定\)** アプリを起動し、 **[Update]\(更新\) > [For Developers]\(開発者向け\)** にアクセスして、 **[Clear]\(クリア\)** をタップします。</span><span class="sxs-lookup"><span data-stu-id="2ab04-194">Launch the **Settings** app, go to **Update > For Developers**, and tap on **Clear**.</span></span>

## <a name="graphics-debugger-for-hololens-1st-gen"></a><span data-ttu-id="2ab04-195">HoloLens (第 1 世代) 用グラフィックス デバッガー</span><span class="sxs-lookup"><span data-stu-id="2ab04-195">Graphics Debugger for HoloLens (1st gen)</span></span>

<span data-ttu-id="2ab04-196">Visual Studio グラフィックス診断ツールは、ホログラフィック アプリを作成して最適化するときに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-196">The Visual Studio Graphics Diagnostics tools are helpful when writing and optimizing a Holographic app.</span></span> <span data-ttu-id="2ab04-197">詳細については、[MSDN の「Visual Studio グラフィックス診断」](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ab04-197">See [Visual Studio Graphics Diagnostics on MSDN](/previous-versions/visualstudio/visual-studio-2015/debugger/visual-studio-graphics-diagnostics) for full details.</span></span>

<span data-ttu-id="2ab04-198">**グラフィックス デバッガーを起動するには**</span><span class="sxs-lookup"><span data-stu-id="2ab04-198">**To Start the Graphics Debugger**</span></span>
1. <span data-ttu-id="2ab04-199">上記の手順に従って、デバイスまたはエミュレーターをターゲットにします</span><span class="sxs-lookup"><span data-stu-id="2ab04-199">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="2ab04-200">**[デバッグ] > [グラフィック] > [診断の開始]** に移動します</span><span class="sxs-lookup"><span data-stu-id="2ab04-200">Go to **Debug > Graphics > Start Diagnostics**</span></span>
3. <span data-ttu-id="2ab04-201">HoloLens で診断を初めて開始すると、"アクセス拒否" エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="2ab04-201">The first time you start diagnostics with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="2ab04-202">更新されたアクセス許可が反映されるように HoloLens を再起動してから、もう一度やり直してください。</span><span class="sxs-lookup"><span data-stu-id="2ab04-202">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="profiling"></a><span data-ttu-id="2ab04-203">プロファイリング</span><span class="sxs-lookup"><span data-stu-id="2ab04-203">Profiling</span></span>

<span data-ttu-id="2ab04-204">Visual Studio プロファイリング ツールを使用すると、アプリのパフォーマンスとリソースの使用量を分析できます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-204">The Visual Studio profiling tools allow you to analyze your app's performance and resource use.</span></span> <span data-ttu-id="2ab04-205">これには、CPU、メモリ、グラフィックス、およびネットワークの使用を最適化するツールが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-205">This includes tools to optimize CPU, memory, graphics, and network use.</span></span> <span data-ttu-id="2ab04-206">詳細については、[MSDN のデバッグなしで診断ツールを実行する](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools)方法に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ab04-206">See [Run diagnostic tools without debugging on MSDN](/previous-versions/visualstudio/visual-studio-2015/profiling/profiling-tools) for full details.</span></span>

<span data-ttu-id="2ab04-207">**HoloLens でプロファイリング ツールを開始するには**</span><span class="sxs-lookup"><span data-stu-id="2ab04-207">**To Start the Profiling Tools with HoloLens**</span></span>
1. <span data-ttu-id="2ab04-208">上記の手順に従って、デバイスまたはエミュレーターをターゲットにします</span><span class="sxs-lookup"><span data-stu-id="2ab04-208">Follow the instructions above to target a device or emulator</span></span>
2. <span data-ttu-id="2ab04-209">**[デバッグ] > [デバッグなしで診断ツールを開始]** に移動します</span><span class="sxs-lookup"><span data-stu-id="2ab04-209">Go to **Debug > Start Diagnostic Tools Without Debugging...**</span></span>
3. <span data-ttu-id="2ab04-210">使用するツールを選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-210">Select the tools you want to use</span></span>
4. <span data-ttu-id="2ab04-211">**[スタート]** を選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-211">Select **Start**</span></span>
5. <span data-ttu-id="2ab04-212">HoloLens で診断をデバッグなしで初めて開始すると、"アクセス拒否" エラーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="2ab04-212">The first time you start diagnostics without debugging with a HoloLens, you may get an "access denied" error.</span></span> <span data-ttu-id="2ab04-213">更新されたアクセス許可が反映されるように HoloLens を再起動してから、もう一度やり直してください。</span><span class="sxs-lookup"><span data-stu-id="2ab04-213">Reboot your HoloLens to let the updated permissions take effect and try again.</span></span>

## <a name="debugging-an-installed-or-running-app"></a><span data-ttu-id="2ab04-214">インストール済みまたは実行中のアプリのデバッグ</span><span class="sxs-lookup"><span data-stu-id="2ab04-214">Debugging an installed or running app</span></span>

<span data-ttu-id="2ab04-215">Visual Studio を使用して、Visual Studio プロジェクトから配置せずにインストールされたユニバーサル Windows アプリをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-215">You can use Visual Studio to debug an installed Universal Windows app without deploying from a Visual Studio project.</span></span> <span data-ttu-id="2ab04-216">これは、インストール済みのアプリ パッケージをデバッグしたり、既に実行中のアプリをデバッグしたりする場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="2ab04-216">This is useful if you want to debug an installed app package or debug an app that's already running.</span></span>
1. <span data-ttu-id="2ab04-217">**[デバッグ] -> [その他のデバッグ ターゲット] -> [インストールされているアプリ パッケージのデバッグ]** に移動します</span><span class="sxs-lookup"><span data-stu-id="2ab04-217">Go to **Debug -> Other Debug Targets -> Debug Installed App Package**</span></span>
2. <span data-ttu-id="2ab04-218">HoloLens の場合は **[リモート コンピューター]** ターゲットを選択し、イマーシブ ヘッドセットの場合は **[ローカル コンピューター]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-218">Select the **Remote Machine** target for HoloLens or **Local Machine** for immersive headsets.</span></span>
3. <span data-ttu-id="2ab04-219">デバイスの **[IP アドレス]** を入力します</span><span class="sxs-lookup"><span data-stu-id="2ab04-219">Enter your device’s **IP address**</span></span>
4. <span data-ttu-id="2ab04-220">**[ユニバーサル]** 認証モードを選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-220">Choose the **Universal** Authentication Mode</span></span>
5. <span data-ttu-id="2ab04-221">このウィンドウには、実行中のアプリと非アクティブなアプリの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-221">The window shows both running and inactive apps.</span></span> <span data-ttu-id="2ab04-222">デバッグするものを選択します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-222">Pick the one what you’d like to debug.</span></span>
6. <span data-ttu-id="2ab04-223">デバッグするコードの種類を選択します ([マネージド]、[ネイティブ]、[混合])</span><span class="sxs-lookup"><span data-stu-id="2ab04-223">Choose the type of code to debug (Managed, Native, Mixed)</span></span>
7. <span data-ttu-id="2ab04-224">**[アタッチ]** または **[開始]** を選択します</span><span class="sxs-lookup"><span data-stu-id="2ab04-224">Select **Attach** or **Start**</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="2ab04-225">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="2ab04-225">Next Development Checkpoint</span></span>

<span data-ttu-id="2ab04-226">私たちが用意した Unity 開発チェックポイント体験に従っている場合、読者は配置段階にいます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-226">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="2ab04-227">ここから、次のトピックを続けることができます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-227">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ab04-228">HoloLens エミュレーターへの配置</span><span class="sxs-lookup"><span data-stu-id="2ab04-228">Deploying to HoloLens emulator</span></span>](using-the-hololens-emulator.md)

<span data-ttu-id="2ab04-229">または、高度なサービスの追加操作に直接移動します。</span><span class="sxs-lookup"><span data-stu-id="2ab04-229">Or jump directly to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ab04-230">高度なサービス</span><span class="sxs-lookup"><span data-stu-id="2ab04-230">Advanced services</span></span>](../../develop/unity/unity-development-overview.md#5-adding-services)

<span data-ttu-id="2ab04-231">いつでも [Unity 開発チェックポイント](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="2ab04-231">You can always go back to the [Unity development checkpoints](../../develop/unity/unity-development-overview.md#4-deploying-to-a-device-or-emulator) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ab04-232">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ab04-232">See also</span></span>
* [<span data-ttu-id="2ab04-233">ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="2ab04-233">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="2ab04-234">HoloLens エミュレーターを使用する</span><span class="sxs-lookup"><span data-stu-id="2ab04-234">Using the HoloLens emulator</span></span>](using-the-hololens-emulator.md)
* [<span data-ttu-id="2ab04-235">ユニバーサル Windows プラットフォーム (UWP) アプリのデプロイとデバッグ</span><span class="sxs-lookup"><span data-stu-id="2ab04-235">Deploying and debugging Universal Windows Platform (UWP) apps</span></span>](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)
* [<span data-ttu-id="2ab04-236">デバイスを開発用に有効にする</span><span class="sxs-lookup"><span data-stu-id="2ab04-236">Enable your device for development</span></span>](/windows/uwp/get-started/enable-your-device-for-development)