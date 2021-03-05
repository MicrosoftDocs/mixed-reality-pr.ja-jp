---
title: Unity でサポートされている OpenXR プラグインの機能
description: Unity での mixed reality 開発に OpenXR がサポートする機能について説明します。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 拡張現実, 仮想現実, mixed reality ヘッドセット, 学習, チュートリアル, 概要
ms.openlocfilehash: 0501abe5a417c17283347455ccea8ec6f49a6a45
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230743"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="8afc3-104">Unity でサポートされている Mixed Reality OpenXR の機能</span><span class="sxs-lookup"><span data-stu-id="8afc3-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="8afc3-105">**Mixed Reality OpenXR プラグイン** パッケージは Unity の **OpenXR プラグイン** の拡張機能であり、HoloLens 2 および Windows Mixed Reality ヘッドセットの一連の機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8afc3-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="8afc3-106">続行する前に、 **unity 2020.2** 以降、 **OpenXR プラグインバージョン 0.1.3** 以降がインストールされていること、および unity プロジェクトが [OpenXR 用に構成](openxr-getting-started.md)されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8afc3-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.3** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="8afc3-107">サポートされる操作</span><span class="sxs-lookup"><span data-stu-id="8afc3-107">What's supported</span></span>

<span data-ttu-id="8afc3-108">現在、次の機能がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8afc3-108">The following features are currently supported:</span></span>

* <span data-ttu-id="8afc3-109">HoloLens 2 の UWP アプリケーションと HoloLens 2 アプリケーションモデルの最適化をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8afc3-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="8afc3-110">は、最新のコントローラープロファイルと holographic app remoting を使用した Windows Mixed Reality ヘッドセット用の Win32 VR アプリケーションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8afc3-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="8afc3-111">アンカーと無制限のスペースを使用したワールドスケールの追跡。</span><span class="sxs-lookup"><span data-stu-id="8afc3-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="8afc3-112">[ストレージ API を固定](#anchors-and-anchor-persistence) して、HoloLens 2 ローカルストレージにアンカーを保持します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="8afc3-113">新しい HP リバーブ G2 コントローラーを含む、[モーションコントローラーと手作業のやり取り](#motion-controller-and-hand-interactions)。</span><span class="sxs-lookup"><span data-stu-id="8afc3-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="8afc3-114">26個の関節と結合半径の入力を使用した、トレーラーを使用したハンドトラッキング。</span><span class="sxs-lookup"><span data-stu-id="8afc3-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="8afc3-115">HoloLens 2 での視線の相互作用。</span><span class="sxs-lookup"><span data-stu-id="8afc3-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="8afc3-116">HoloLens 2 で写真/ビデオ (PV) カメラを検索しています。</span><span class="sxs-lookup"><span data-stu-id="8afc3-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="8afc3-117">PV カメラを使用した第3目のレンダリングを使用した Mixed Reality キャプチャ。</span><span class="sxs-lookup"><span data-stu-id="8afc3-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="8afc3-118">[Holographic リモート処理アプリでの HoloLens 2 への "Play" を](#holographic-remoting-in-unity-editor-play-mode)サポートします。これにより、開発者は、デバイスにビルドしてデプロイすることなく、スクリプトをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="8afc3-119">MRTK Unity 2.5.3 以降の [Mrtk OpenXR プロバイダーのサポート](openxr-getting-started.md#using-mrtk-with-openxr-support)と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="8afc3-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="8afc3-120">Unity [Arfoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 以降と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="8afc3-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="8afc3-121">(0.1.3 で追加)では、Windows スタンドアロンのビルドおよび展開されたアプリから [デスクトップアプリの Holographic リモート処理](#holographic-remoting-in-desktop-app) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="8afc3-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](#holographic-remoting-in-desktop-app) from a built and deployed Windows Standalone app.</span></span>
* <span data-ttu-id="8afc3-122">(0.1.4 で追加)SpatialGraphNode を通じて HoloLens2 で [QR コード追跡](#qr-codes) をサポート</span><span class="sxs-lookup"><span data-stu-id="8afc3-122">(Added in 0.1.4) Supports [QR code tracking](#qr-codes) on HoloLens2 through SpatialGraphNode</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="8afc3-123">Holographic リモート処理のセットアップ</span><span class="sxs-lookup"><span data-stu-id="8afc3-123">Holographic Remoting setup</span></span>

1. <span data-ttu-id="8afc3-124">まず、HoloLens 2 の Microsoft Store から [Holographic Remoting プレーヤーアプリをインストール](https://www.microsoft.com/store/productId/9NBLGGH4SV40) する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8afc3-124">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="8afc3-125">HoloLens 2 で Holographic リモート処理プレーヤーアプリを実行すると、接続先のバージョン番号と IP アドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-125">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="8afc3-126">OpenXR プラグインを使用するには、v2.0 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="8afc3-126">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens で実行されている Holographic リモート処理プレーヤーのスクリーンショット](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="8afc3-128">Unity エディター再生モードでの Holographic リモート処理</span><span class="sxs-lookup"><span data-stu-id="8afc3-128">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="8afc3-129">Visual Studio プロジェクトで UWP Unity プロジェクトをビルドしてから、パッケージ化して HoloLens 2 デバイスに配置すると、時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="8afc3-129">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="8afc3-130">1つの解決策は、Holographic エディターのリモート処理機能を有効にすることです。これにより、ネットワーク上の HoloLens 2 デバイスに対して "Play" モードで直接 C# スクリプトをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-130">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="8afc3-131">このシナリオでは、UWP パッケージをビルドしてリモートデバイスに配置するオーバーヘッドを回避します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-131">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="8afc3-132">[Holographic リモート処理のセットアップ](#holographic-remoting-setup)の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="8afc3-132">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="8afc3-133">[ **編集-> プロジェクトの設定**] を開き、 **XR プラグイン管理** に移動して、[ **Windows Mixed Reality] 機能セット** ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="8afc3-133">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![XR プラグイン管理が強調表示されている Unity エディターで開いているプロジェクト設定パネルのスクリーンショット](images/openxr-features-img-02.png)

3. <span data-ttu-id="8afc3-135">**OpenXR** の [**機能**] セクションを展開し、[**すべて表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-135">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="8afc3-136">[ **Holographic エディターリモート処理** ] チェックボックスをオンにして、Holographic リモート処理アプリから取得した IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-136">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![機能が強調表示されている Unity エディターでプロジェクト設定パネルが開いているスクリーンショット](images/openxr-features-img-03.png)

<span data-ttu-id="8afc3-138">これで、[Play] \ (再生 \) ボタンをクリックして、HoloLens の Holographic リモート処理アプリで Unity アプリを再生できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="8afc3-138">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="8afc3-139">また、 [Visual Studio を Unity にアタッチ](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) して、C# スクリプトを再生モードでデバッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-139">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="8afc3-140">バージョン0.1.0 の場合、Holographic リモート処理ランタイムはアンカーをサポートしておらず、ARAnchorManager 機能はリモート処理では機能しません。</span><span class="sxs-lookup"><span data-stu-id="8afc3-140">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="8afc3-141">この機能は今後のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="8afc3-141">This feature is coming in future releases.</span></span>

## <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="8afc3-142">デスクトップアプリでの Holographic リモート処理</span><span class="sxs-lookup"><span data-stu-id="8afc3-142">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="8afc3-143">Windows スタンドアロンアプリのリモート処理サポートは、0.1.3 パッケージリリースで追加されました。</span><span class="sxs-lookup"><span data-stu-id="8afc3-143">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="8afc3-144">バージョン0.1.3 の場合、この機能は UWP ビルドをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="8afc3-144">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="8afc3-145">[Holographic リモート処理のセットアップ](#holographic-remoting-setup)の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="8afc3-145">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="8afc3-146">[ **編集-> プロジェクトの設定**] を開き、 **XR プラグイン管理** に移動して、[ **Windows Mixed Reality] 機能セット** ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="8afc3-146">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="8afc3-147">また、 **[起動時に XR を初期化** する] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="8afc3-147">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![[スタートアップ時に XR を初期化する] チェックがオフになっている Unity エディターでプロジェクト設定パネルが開いているスクリーンショット](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="8afc3-149">**OpenXR** の [**機能**] セクションを展開し、[**すべて表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-149">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="8afc3-150">[ **Holographic App リモート処理** ] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="8afc3-150">Check the **Holographic App Remoting** checkbox:</span></span>

    ![アプリのリモート処理が有効になっている Unity エディターで開いているプロジェクト設定パネルのスクリーンショット](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="8afc3-152">次に、リモート処理の構成を設定し、XR の初期化をトリガーするコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-152">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="8afc3-153">[Mixed Reality OpenXR プラグイン](openxr-getting-started.md#hololens-2-samples)と共に配布されるサンプルアプリには、AppRemoting.cs が含まれています。これは、実行時に特定の IP アドレスに接続するためのシナリオ例を示しています。</span><span class="sxs-lookup"><span data-stu-id="8afc3-153">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="8afc3-154">この時点でローカルコンピューターにサンプルアプリをデプロイすると、[接続] ボタンを含む [IP アドレス] 入力フィールドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-154">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="8afc3-155">IP アドレスを入力して [接続] をクリックすると、XR が初期化され、ターゲットデバイスへの接続が試行されます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-155">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![アプリのリモート処理の UI の例を表示しているサンプルアプリのスクリーンショット](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="8afc3-157">カスタム接続コードを記述するに `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` は、を入力してを呼び出し `RemotingConfiguration` ます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-157">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="8afc3-158">このサンプルアプリでは、これをインスペクターで公開し、テキストフィールドから IP アドレスを入力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-158">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="8afc3-159">を呼び出す `Connect` と、構成が設定され、XR が自動的に初期化されます。このため、コルーチンとして呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8afc3-159">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="8afc3-160">を実行している間、API を使用して現在の接続状態を取得 `AppRemoting.TryGetConnectionState` し、必要に応じて、を使用して XR を切断または初期化解除でき `AppRemoting.Disconnect()` ます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-160">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="8afc3-161">これは、同じアプリセッション内で別のデバイスを切断して再接続するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-161">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="8afc3-162">サンプルアプリには、tappable キューブが用意されています。このキューブは、タップされた場合にリモート処理セッションを切断します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-162">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="8afc3-163">以前の Api からの移行</span><span class="sxs-lookup"><span data-stu-id="8afc3-163">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="8afc3-164">UnityEngine. XR. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="8afc3-164">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="8afc3-165">[Unity のドキュメント](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)のサンプルコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-165">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="8afc3-166">XR.付い.HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="8afc3-166">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="8afc3-167">OpenXR (AppRemoting)</span><span class="sxs-lookup"><span data-stu-id="8afc3-167">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="8afc3-168">[N/A: の呼び出し時に自動的に発生します `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="8afc3-168">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="8afc3-169">UnityEngine. XR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="8afc3-169">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="8afc3-170">XR.WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="8afc3-170">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="8afc3-171">OpenXR (AppRemoting)</span><span class="sxs-lookup"><span data-stu-id="8afc3-171">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="8afc3-172">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` および `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="8afc3-172">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="8afc3-173">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="8afc3-173">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="8afc3-174">`AppRemoting.Connect`構造体を介してに渡されます。 `RemotingConfiguration`</span><span class="sxs-lookup"><span data-stu-id="8afc3-174">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="8afc3-175">アンカーとアンカーの永続化</span><span class="sxs-lookup"><span data-stu-id="8afc3-175">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="8afc3-176">Mixed Reality OpenXR プラグインは、Unity の ARFoundation **ARAnchorManager** の実装を通じて基本的なアンカー機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-176">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="8afc3-177">Aranchor の **基本につい** ては、ARANCHOR の [AR アンカーマネージャーのマニュアル](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8afc3-177">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="8afc3-178">バージョン0.1.0 以降では、このプラグインは、プレーンにアタッチされたアンカーを作成する以外のすべての ARAnchorManager 機能をサポートしています。これは将来のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="8afc3-178">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="8afc3-179">固定の永続性と XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="8afc3-179">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="8afc3-180">**XRAnchorStore** と呼ばれる追加の API を使用すると、セッション間でアンカーを永続化できます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-180">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="8afc3-181">XRAnchorStore は、デバイスに保存されているアンカーの表現です。</span><span class="sxs-lookup"><span data-stu-id="8afc3-181">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="8afc3-182">アンカーは、Unity シーンの **Aranchors** から永続化したり、ストレージから新しい **aranchors** に読み込んだり、ストレージから削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-182">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="8afc3-183">これらのアンカーは保存され、同じデバイスに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-183">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="8afc3-184">デバイス間のアンカーストレージは、今後のリリースで Azure 空間アンカーを通じてサポートされます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-184">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="8afc3-185">XRAnchorStore を読み込むには、プラグインを使用して、XRAnchorSubsystem のサブシステムである ARAnchorManager の拡張メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-185">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="8afc3-186">この拡張メソッドを使用するには、次のように ARAnchorManager のサブシステムからアクセスします。</span><span class="sxs-lookup"><span data-stu-id="8afc3-186">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="8afc3-187">アンカー > を永続化または非永続化する完全な例については、「 [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples)」の「AnchorsSample.cs script and script」 (アンカーとアンカーの例) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8afc3-187">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![[階層] パネルのスクリーンショット (アンカーのサンプルが強調表示された状態で、Unity エディターで開きます)](images/openxr-features-img-04.png)

![[インスペクター] サンプルスクリプトが強調表示された状態で、Unity エディターで開いているインスペクターパネルのスクリーンショット](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="8afc3-190">モーションコントローラーとハンド作用</span><span class="sxs-lookup"><span data-stu-id="8afc3-190">Motion controller and hand interactions</span></span>

<span data-ttu-id="8afc3-191">Unity での mixed reality の相互作用の基本については、unity の unity の [XR 入力](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8afc3-191">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="8afc3-192">この Unity ドキュメントでは、コントローラー固有の入力から、より汎化された **Inputfeatureusage** へのマッピング、使用可能な XR 入力を識別および分類する方法、これらの入力からデータを読み取る方法などについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-192">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="8afc3-193">Mixed Reality OpenXR プラグインは、次に示すように、標準 **Inputfeatureusage** にマップされた追加の入力相互作用プロファイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-193">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="8afc3-194">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="8afc3-194">InputFeatureUsage</span></span> | <span data-ttu-id="8afc3-195">HP リバーブ G2 コントローラー (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="8afc3-195">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="8afc3-196">HoloLens (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="8afc3-196">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="8afc3-197">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="8afc3-197">primary2DAxis</span></span> | <span data-ttu-id="8afc3-198">ジョイ</span><span class="sxs-lookup"><span data-stu-id="8afc3-198">Joystick</span></span> | |
| <span data-ttu-id="8afc3-199">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="8afc3-199">primary2DAxisClick</span></span> | <span data-ttu-id="8afc3-200">ジョイスティック-クリック</span><span class="sxs-lookup"><span data-stu-id="8afc3-200">Joystick - Click</span></span> | |
| <span data-ttu-id="8afc3-201">トリガー (trigger)</span><span class="sxs-lookup"><span data-stu-id="8afc3-201">trigger</span></span> | <span data-ttu-id="8afc3-202">トリガー</span><span class="sxs-lookup"><span data-stu-id="8afc3-202">Trigger</span></span>  | |
| <span data-ttu-id="8afc3-203">把握</span><span class="sxs-lookup"><span data-stu-id="8afc3-203">grip</span></span> | <span data-ttu-id="8afc3-204">把握</span><span class="sxs-lookup"><span data-stu-id="8afc3-204">Grip</span></span> | <span data-ttu-id="8afc3-205">エアタップまたはつかみ</span><span class="sxs-lookup"><span data-stu-id="8afc3-205">Air tap or squeeze</span></span> |
| <span data-ttu-id="8afc3-206">primaryButton</span><span class="sxs-lookup"><span data-stu-id="8afc3-206">primaryButton</span></span> | <span data-ttu-id="8afc3-207">[X/A]-押します</span><span class="sxs-lookup"><span data-stu-id="8afc3-207">[X/A] - Press</span></span> | <span data-ttu-id="8afc3-208">エアタップ</span><span class="sxs-lookup"><span data-stu-id="8afc3-208">Air tap</span></span> |
| <span data-ttu-id="8afc3-209">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="8afc3-209">secondaryButton</span></span> | <span data-ttu-id="8afc3-210">[Y/B]-押します</span><span class="sxs-lookup"><span data-stu-id="8afc3-210">[Y/B] - Press</span></span> | |
| <span data-ttu-id="8afc3-211">gripButton</span><span class="sxs-lookup"><span data-stu-id="8afc3-211">gripButton</span></span> | <span data-ttu-id="8afc3-212">グリップ-押す</span><span class="sxs-lookup"><span data-stu-id="8afc3-212">Grip - Press</span></span> | |
| <span data-ttu-id="8afc3-213">triggerButton</span><span class="sxs-lookup"><span data-stu-id="8afc3-213">triggerButton</span></span> | <span data-ttu-id="8afc3-214">トリガー-押す</span><span class="sxs-lookup"><span data-stu-id="8afc3-214">Trigger - Press</span></span> | |
| <span data-ttu-id="8afc3-215">menuButton</span><span class="sxs-lookup"><span data-stu-id="8afc3-215">menuButton</span></span> | <span data-ttu-id="8afc3-216">メニュー</span><span class="sxs-lookup"><span data-stu-id="8afc3-216">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="8afc3-217">目標とグリップ</span><span class="sxs-lookup"><span data-stu-id="8afc3-217">Aim and Grip Poses</span></span>

<span data-ttu-id="8afc3-218">OpenXR の入力相互作用を通じて、2組のポーズにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-218">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="8afc3-219">手の形でオブジェクトをレンダリングするためのグリップ</span><span class="sxs-lookup"><span data-stu-id="8afc3-219">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="8afc3-220">目標は、世界を指します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-220">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="8afc3-221">この設計の詳細と、2つの方法の違いについては、「 [OpenXR Specification-Input サブパス](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8afc3-221">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="8afc3-222">InputFeatureUsages **Deviceposition**、 **Devicerotation**、 **devicevelocに** よって指定されたポーズ、およびすべてが OpenXR **グリップ** を表します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-222">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="8afc3-223">グリップの設定に関連する InputFeatureUsages は、Unity の [commonusages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)で定義されています。</span><span class="sxs-lookup"><span data-stu-id="8afc3-223">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="8afc3-224">InputFeatureUsages **ポインター** によって提供されるポーズ、 **ポインターローテーション**、 **ポインター速度**、および **PointerAngularVelocity** all は、OpenXR **aim** を表します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-224">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="8afc3-225">これらの InputFeatureUsages はインクルードされているすべての C# ファイルで定義されていないため、次のように独自の InputFeatureUsages を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8afc3-225">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="8afc3-226">Haptics</span><span class="sxs-lookup"><span data-stu-id="8afc3-226">Haptics</span></span>

<span data-ttu-id="8afc3-227">Unity の XR 入力システムで haptics を使用する方法の詳細については、unity の unity [マニュアルの「UNITY XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8afc3-227">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="qr-codes"></a><span data-ttu-id="8afc3-228">QR コード</span><span class="sxs-lookup"><span data-stu-id="8afc3-228">QR codes</span></span>

<span data-ttu-id="8afc3-229">HoloLens 2 を使用すると、ヘッドセット周辺の環境内の QR コードを検出し、各コードの実際の場所で座標系を確立することができます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-229">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="8afc3-230">詳細については、 [QR コードの追跡](../platform-capabilities-and-apis/qr-code-tracking.md) に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8afc3-230">You can find more details in our [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) documentation.</span></span>  <span data-ttu-id="8afc3-231">OpenXR プラグインを使用する場合は、 [ `SpatialGraphNodeId` qr api から](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference)を取得し、API を使用して `Microsoft.MixedReality.OpenXR.SpatialGraphNode` qr コードを見つけます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-231">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="8afc3-232">参考までに、 [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs)の詳細な使用方法については、 [GitHub の QR 追跡サンプルプロジェクト](https://github.com/yl-msft/QRTracking)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8afc3-232">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="8afc3-233">近日公開予定</span><span class="sxs-lookup"><span data-stu-id="8afc3-233">What's coming soon</span></span>

<span data-ttu-id="8afc3-234">次の問題および不足している機能は、Mixed Reality OpenXR プラグイン **バージョン 0.1.0** で知られています。</span><span class="sxs-lookup"><span data-stu-id="8afc3-234">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="8afc3-235">これらの機能については、今後のリリースで修正と新機能をリリースする予定です。</span><span class="sxs-lookup"><span data-stu-id="8afc3-235">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="8afc3-236">**ARPlaneSubsystem** はまだサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8afc3-236">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="8afc3-237">HoloLens 2 では、 **Arplan emanager**、 **ARRaycastManager**、および ARANCHORMANAGER などの関連 API もサポートされていません **。**</span><span class="sxs-lookup"><span data-stu-id="8afc3-237">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="8afc3-238">**アンカーの永続** 化は、Holographic リモート処理ではまだサポートされていませんが、近い将来に登場します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-238">**Anchor persistence** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="8afc3-239">**手動メッシュ** 追跡と **XRMeshSubsystem** はまだサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8afc3-239">**Hand Mesh** tracking and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="8afc3-240">**Azure 空間アンカー** のサポートは、今後のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="8afc3-240">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="8afc3-241">**ARM64** は、HoloLens 2 アプリで唯一サポートされているプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="8afc3-241">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="8afc3-242">**ARM** プラットフォームは今後のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="8afc3-242">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="8afc3-243">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="8afc3-243">Troubleshooting</span></span>

<span data-ttu-id="8afc3-244">HoloLens 2 で Unity アプリを中断および再開すると、アプリは正しく再開できなくなります。これにより、HoloLens ビューでは、4つのスピン点が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8afc3-244">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="8afc3-245">回避策として、OpenXR プロジェクト設定で [ **深さの送信モード** ] を **[なし** ] に設定します。</span><span class="sxs-lookup"><span data-stu-id="8afc3-245">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
