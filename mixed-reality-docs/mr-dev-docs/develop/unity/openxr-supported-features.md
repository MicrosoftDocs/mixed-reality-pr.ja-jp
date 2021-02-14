---
title: Unity でサポートされている OpenXR プラグインの機能
description: Unity での mixed reality 開発に OpenXR がサポートする機能について説明します。
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 拡張現実, 仮想現実, mixed reality ヘッドセット, 学習, チュートリアル, 概要
ms.openlocfilehash: bad18c5f30465120bce370aa91c13ff3f229bef6
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496148"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="d4d1c-104">Unity でサポートされている Mixed Reality OpenXR の機能</span><span class="sxs-lookup"><span data-stu-id="d4d1c-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="d4d1c-105">**Mixed Reality OpenXR プラグイン** パッケージは Unity の **OpenXR プラグイン** の拡張機能であり、HoloLens 2 および Windows Mixed Reality ヘッドセットの一連の機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="d4d1c-106">続行する前に、 **unity 2020.2** 以降、 **OpenXR プラグインバージョン 0.1.3** 以降がインストールされていること、および unity プロジェクトが [OpenXR 用に構成](openxr-getting-started.md)されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.3** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="d4d1c-107">サポートされる操作</span><span class="sxs-lookup"><span data-stu-id="d4d1c-107">What's supported</span></span>

<span data-ttu-id="d4d1c-108">現在、次の機能がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-108">The following features are currently supported:</span></span>

* <span data-ttu-id="d4d1c-109">HoloLens 2 の UWP アプリケーションと HoloLens 2 アプリケーションモデルの最適化をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="d4d1c-110">は、最新のコントローラープロファイルと holographic app remoting を使用した Windows Mixed Reality ヘッドセット用の Win32 VR アプリケーションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="d4d1c-111">アンカーと無制限のスペースを使用したワールドスケールの追跡。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="d4d1c-112">[ストレージ API を固定](#anchors-and-anchor-persistence) して、HoloLens 2 ローカルストレージにアンカーを保持します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="d4d1c-113">新しい HP リバーブ G2 コントローラーを含む、[モーションコントローラーと手作業のやり取り](#motion-controller-and-hand-interactions)。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="d4d1c-114">26個の関節と結合半径の入力を使用した、トレーラーを使用したハンドトラッキング。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="d4d1c-115">HoloLens 2 での視線の相互作用。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="d4d1c-116">HoloLens 2 で写真/ビデオ (PV) カメラを検索しています。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="d4d1c-117">PV カメラを使用した第3目のレンダリングを使用した Mixed Reality キャプチャ。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="d4d1c-118">[Holographic リモート処理アプリでの HoloLens 2 への "Play" を](#holographic-remoting-in-unity-editor-play-mode)サポートします。これにより、開発者は、デバイスにビルドしてデプロイすることなく、スクリプトをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="d4d1c-119">MRTK Unity 2.5.3 以降の [Mrtk OpenXR プロバイダーのサポート](openxr-getting-started.md#using-mrtk-with-openxr-support)と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="d4d1c-120">Unity [Arfoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 以降と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="d4d1c-121">(0.1.3 で追加)では、Windows スタンドアロンのビルドおよび展開されたアプリから [デスクトップアプリの Holographic リモート処理](#holographic-remoting-in-desktop-app) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](#holographic-remoting-in-desktop-app) from a built and deployed Windows Standalone app.</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="d4d1c-122">Holographic リモート処理のセットアップ</span><span class="sxs-lookup"><span data-stu-id="d4d1c-122">Holographic Remoting setup</span></span>

1. <span data-ttu-id="d4d1c-123">まず、HoloLens 2 の Microsoft Store から [Holographic Remoting プレーヤーアプリをインストール](https://www.microsoft.com/store/productId/9NBLGGH4SV40) する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-123">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="d4d1c-124">HoloLens 2 で Holographic リモート処理プレーヤーアプリを実行すると、接続先のバージョン番号と IP アドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-124">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="d4d1c-125">OpenXR プラグインを使用するには、v2.0 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-125">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![HoloLens で実行されている Holographic リモート処理プレーヤーのスクリーンショット](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="d4d1c-127">Unity エディター再生モードでの Holographic リモート処理</span><span class="sxs-lookup"><span data-stu-id="d4d1c-127">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="d4d1c-128">Visual Studio プロジェクトで UWP Unity プロジェクトをビルドしてから、パッケージ化して HoloLens 2 デバイスに配置すると、時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-128">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="d4d1c-129">1つの解決策は、Holographic エディターのリモート処理機能を有効にすることです。これにより、ネットワーク上の HoloLens 2 デバイスに対して "Play" モードで直接 C# スクリプトをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-129">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="d4d1c-130">このシナリオでは、UWP パッケージをビルドしてリモートデバイスに配置するオーバーヘッドを回避します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-130">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="d4d1c-131">[Holographic リモート処理のセットアップ](#holographic-remoting-setup)の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-131">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="d4d1c-132">[ **編集-> プロジェクトの設定**] を開き、 **XR プラグイン管理** に移動して、[ **Windows Mixed Reality] 機能セット** ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-132">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![XR プラグイン管理が強調表示されている Unity エディターで開いているプロジェクト設定パネルのスクリーンショット](images/openxr-features-img-02.png)

3. <span data-ttu-id="d4d1c-134">**OpenXR** の [**機能**] セクションを展開し、[**すべて表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-134">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="d4d1c-135">[ **Holographic エディターリモート処理** ] チェックボックスをオンにして、Holographic リモート処理アプリから取得した IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-135">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![機能が強調表示されている Unity エディターでプロジェクト設定パネルが開いているスクリーンショット](images/openxr-features-img-03.png)

<span data-ttu-id="d4d1c-137">これで、[Play] \ (再生 \) ボタンをクリックして、HoloLens の Holographic リモート処理アプリで Unity アプリを再生できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-137">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="d4d1c-138">また、 [Visual Studio を Unity にアタッチ](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) して、C# スクリプトを再生モードでデバッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-138">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="d4d1c-139">バージョン0.1.0 の場合、Holographic リモート処理ランタイムはアンカーをサポートしておらず、ARAnchorManager 機能はリモート処理では機能しません。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-139">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="d4d1c-140">この機能は今後のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-140">This feature is coming in future releases.</span></span>

## <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="d4d1c-141">デスクトップアプリでの Holographic リモート処理</span><span class="sxs-lookup"><span data-stu-id="d4d1c-141">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="d4d1c-142">Windows スタンドアロンアプリのリモート処理サポートは、0.1.3 パッケージリリースで追加されました。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-142">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="d4d1c-143">バージョン0.1.3 の場合、この機能は UWP ビルドをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-143">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="d4d1c-144">[Holographic リモート処理のセットアップ](#holographic-remoting-setup)の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-144">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="d4d1c-145">[ **編集-> プロジェクトの設定**] を開き、 **XR プラグイン管理** に移動して、[ **Windows Mixed Reality] 機能セット** ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-145">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="d4d1c-146">また、 **[起動時に XR を初期化** する] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-146">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![[スタートアップ時に XR を初期化する] チェックがオフになっている Unity エディターでプロジェクト設定パネルが開いているスクリーンショット](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="d4d1c-148">**OpenXR** の [**機能**] セクションを展開し、[**すべて表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-148">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="d4d1c-149">[ **Holographic App リモート処理** ] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-149">Check the **Holographic App Remoting** checkbox:</span></span>

    ![アプリのリモート処理が有効になっている Unity エディターで開いているプロジェクト設定パネルのスクリーンショット](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="d4d1c-151">次に、リモート処理の構成を設定し、XR の初期化をトリガーするコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-151">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="d4d1c-152">[Mixed Reality OpenXR プラグイン](openxr-getting-started.md#hololens-2-samples)と共に配布されるサンプルアプリには、AppRemoting.cs が含まれています。これは、実行時に特定の IP アドレスに接続するためのシナリオ例を示しています。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-152">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="d4d1c-153">この時点でローカルコンピューターにサンプルアプリをデプロイすると、[接続] ボタンを含む [IP アドレス] 入力フィールドが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-153">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="d4d1c-154">IP アドレスを入力して [接続] をクリックすると、XR が初期化され、ターゲットデバイスへの接続が試行されます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-154">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![アプリのリモート処理の UI の例を表示しているサンプルアプリのスクリーンショット](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="d4d1c-156">カスタム接続コードを記述するに `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` は、を入力してを呼び出し `RemotingConfiguration` ます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-156">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="d4d1c-157">このサンプルアプリでは、これをインスペクターで公開し、テキストフィールドから IP アドレスを入力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-157">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="d4d1c-158">を呼び出す `Connect` と、構成が設定され、XR が自動的に初期化されます。このため、コルーチンとして呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-158">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="d4d1c-159">を実行している間、API を使用して現在の接続状態を取得 `AppRemoting.TryGetConnectionState` し、必要に応じて、を使用して XR を切断または初期化解除でき `AppRemoting.Disconnect()` ます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-159">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="d4d1c-160">これは、同じアプリセッション内で別のデバイスを切断して再接続するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-160">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="d4d1c-161">サンプルアプリには、tappable キューブが用意されています。このキューブは、タップされた場合にリモート処理セッションを切断します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-161">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="d4d1c-162">以前の Api からの移行</span><span class="sxs-lookup"><span data-stu-id="d4d1c-162">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="d4d1c-163">UnityEngine. XR. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="d4d1c-163">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="d4d1c-164">[Unity のドキュメント](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html)のサンプルコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-164">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="d4d1c-165">XR.付い.HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="d4d1c-165">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="d4d1c-166">OpenXR (AppRemoting)</span><span class="sxs-lookup"><span data-stu-id="d4d1c-166">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="d4d1c-167">[N/A: の呼び出し時に自動的に発生します `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="d4d1c-167">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="d4d1c-168">UnityEngine. XR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="d4d1c-168">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="d4d1c-169">XR.WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="d4d1c-169">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="d4d1c-170">OpenXR (AppRemoting)</span><span class="sxs-lookup"><span data-stu-id="d4d1c-170">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="d4d1c-171">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` および `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="d4d1c-171">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="d4d1c-172">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="d4d1c-172">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="d4d1c-173">`AppRemoting.Connect`構造体を介してに渡されます。 `RemotingConfiguration`</span><span class="sxs-lookup"><span data-stu-id="d4d1c-173">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="d4d1c-174">アンカーとアンカーの永続化</span><span class="sxs-lookup"><span data-stu-id="d4d1c-174">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="d4d1c-175">Mixed Reality OpenXR プラグインは、Unity の ARFoundation **ARAnchorManager** の実装を通じて基本的なアンカー機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-175">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="d4d1c-176">Aranchor の **基本につい** ては、ARANCHOR の [AR アンカーマネージャーのマニュアル](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-176">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="d4d1c-177">バージョン0.1.0 以降では、このプラグインは、プレーンにアタッチされたアンカーを作成する以外のすべての ARAnchorManager 機能をサポートしています。これは将来のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-177">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="d4d1c-178">固定の永続性と XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="d4d1c-178">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="d4d1c-179">**XRAnchorStore** と呼ばれる追加の API を使用すると、セッション間でアンカーを永続化できます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-179">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="d4d1c-180">XRAnchorStore は、デバイスに保存されているアンカーの表現です。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-180">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="d4d1c-181">アンカーは、Unity シーンの **Aranchors** から永続化したり、ストレージから新しい **aranchors** に読み込んだり、ストレージから削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-181">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="d4d1c-182">これらのアンカーは保存され、同じデバイスに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-182">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="d4d1c-183">デバイス間のアンカーストレージは、今後のリリースで Azure 空間アンカーを通じてサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-183">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="d4d1c-184">XRAnchorStore を読み込むには、プラグインを使用して、XRAnchorSubsystem のサブシステムである ARAnchorManager の拡張メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-184">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="d4d1c-185">この拡張メソッドを使用するには、次のように ARAnchorManager のサブシステムからアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-185">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="d4d1c-186">アンカー > を永続化または非永続化する完全な例については、「 [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples)」の「AnchorsSample.cs script and script」 (アンカーとアンカーの例) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-186">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![[階層] パネルのスクリーンショット (アンカーのサンプルが強調表示された状態で、Unity エディターで開きます)](images/openxr-features-img-04.png)

![[インスペクター] サンプルスクリプトが強調表示された状態で、Unity エディターで開いているインスペクターパネルのスクリーンショット](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="d4d1c-189">モーションコントローラーとハンド作用</span><span class="sxs-lookup"><span data-stu-id="d4d1c-189">Motion controller and hand interactions</span></span>

<span data-ttu-id="d4d1c-190">Unity での mixed reality の相互作用の基本については、unity の unity の [XR 入力](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-190">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="d4d1c-191">この Unity ドキュメントでは、コントローラー固有の入力から、より汎化された **Inputfeatureusage** へのマッピング、使用可能な XR 入力を識別および分類する方法、これらの入力からデータを読み取る方法などについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-191">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="d4d1c-192">Mixed Reality OpenXR プラグインは、次に示すように、標準 **Inputfeatureusage** にマップされた追加の入力相互作用プロファイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-192">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="d4d1c-193">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="d4d1c-193">InputFeatureUsage</span></span> | <span data-ttu-id="d4d1c-194">HP リバーブ G2 コントローラー (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="d4d1c-194">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="d4d1c-195">HoloLens (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="d4d1c-195">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="d4d1c-196">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="d4d1c-196">primary2DAxis</span></span> | <span data-ttu-id="d4d1c-197">ジョイ</span><span class="sxs-lookup"><span data-stu-id="d4d1c-197">Joystick</span></span> | |
| <span data-ttu-id="d4d1c-198">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="d4d1c-198">primary2DAxisClick</span></span> | <span data-ttu-id="d4d1c-199">ジョイスティック-クリック</span><span class="sxs-lookup"><span data-stu-id="d4d1c-199">Joystick - Click</span></span> | |
| <span data-ttu-id="d4d1c-200">トリガー (trigger)</span><span class="sxs-lookup"><span data-stu-id="d4d1c-200">trigger</span></span> | <span data-ttu-id="d4d1c-201">トリガー</span><span class="sxs-lookup"><span data-stu-id="d4d1c-201">Trigger</span></span>  | |
| <span data-ttu-id="d4d1c-202">把握</span><span class="sxs-lookup"><span data-stu-id="d4d1c-202">grip</span></span> | <span data-ttu-id="d4d1c-203">把握</span><span class="sxs-lookup"><span data-stu-id="d4d1c-203">Grip</span></span> | <span data-ttu-id="d4d1c-204">エアタップまたはつかみ</span><span class="sxs-lookup"><span data-stu-id="d4d1c-204">Air tap or squeeze</span></span> |
| <span data-ttu-id="d4d1c-205">primaryButton</span><span class="sxs-lookup"><span data-stu-id="d4d1c-205">primaryButton</span></span> | <span data-ttu-id="d4d1c-206">[X/A]-押します</span><span class="sxs-lookup"><span data-stu-id="d4d1c-206">[X/A] - Press</span></span> | <span data-ttu-id="d4d1c-207">エアタップ</span><span class="sxs-lookup"><span data-stu-id="d4d1c-207">Air tap</span></span> |
| <span data-ttu-id="d4d1c-208">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="d4d1c-208">secondaryButton</span></span> | <span data-ttu-id="d4d1c-209">[Y/B]-押します</span><span class="sxs-lookup"><span data-stu-id="d4d1c-209">[Y/B] - Press</span></span> | |
| <span data-ttu-id="d4d1c-210">gripButton</span><span class="sxs-lookup"><span data-stu-id="d4d1c-210">gripButton</span></span> | <span data-ttu-id="d4d1c-211">グリップ-押す</span><span class="sxs-lookup"><span data-stu-id="d4d1c-211">Grip - Press</span></span> | |
| <span data-ttu-id="d4d1c-212">triggerButton</span><span class="sxs-lookup"><span data-stu-id="d4d1c-212">triggerButton</span></span> | <span data-ttu-id="d4d1c-213">トリガー-押す</span><span class="sxs-lookup"><span data-stu-id="d4d1c-213">Trigger - Press</span></span> | |
| <span data-ttu-id="d4d1c-214">menuButton</span><span class="sxs-lookup"><span data-stu-id="d4d1c-214">menuButton</span></span> | <span data-ttu-id="d4d1c-215">メニュー</span><span class="sxs-lookup"><span data-stu-id="d4d1c-215">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="d4d1c-216">目標とグリップ</span><span class="sxs-lookup"><span data-stu-id="d4d1c-216">Aim and Grip Poses</span></span>

<span data-ttu-id="d4d1c-217">OpenXR の入力相互作用を通じて、2組のポーズにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-217">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="d4d1c-218">手の形でオブジェクトをレンダリングするためのグリップ</span><span class="sxs-lookup"><span data-stu-id="d4d1c-218">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="d4d1c-219">目標は、世界を指します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-219">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="d4d1c-220">この設計の詳細と、2つの方法の違いについては、「 [OpenXR Specification-Input サブパス](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-220">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="d4d1c-221">InputFeatureUsages **Deviceposition**、 **Devicerotation**、 **devicevelocに** よって指定されたポーズ、およびすべてが OpenXR **グリップ** を表します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-221">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="d4d1c-222">グリップの設定に関連する InputFeatureUsages は、Unity の [commonusages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)で定義されています。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-222">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="d4d1c-223">InputFeatureUsages **ポインター** によって提供されるポーズ、 **ポインターローテーション**、 **ポインター速度**、および **PointerAngularVelocity** all は、OpenXR **aim** を表します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-223">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="d4d1c-224">これらの InputFeatureUsages はインクルードされているすべての C# ファイルで定義されていないため、次のように独自の InputFeatureUsages を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-224">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="d4d1c-225">Haptics</span><span class="sxs-lookup"><span data-stu-id="d4d1c-225">Haptics</span></span>

<span data-ttu-id="d4d1c-226">Unity の XR 入力システムで haptics を使用する方法の詳細については、unity の unity [マニュアルの「UNITY XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-226">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="d4d1c-227">近日公開予定</span><span class="sxs-lookup"><span data-stu-id="d4d1c-227">What's coming soon</span></span>

<span data-ttu-id="d4d1c-228">次の問題および不足している機能は、Mixed Reality OpenXR プラグイン **バージョン 0.1.0** で知られています。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-228">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="d4d1c-229">これらの機能については、今後のリリースで修正と新機能をリリースする予定です。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-229">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="d4d1c-230">**ARPlaneSubsystem** はまだサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-230">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="d4d1c-231">HoloLens 2 では、 **Arplan emanager**、 **ARRaycastManager**、および ARANCHORMANAGER などの関連 API もサポートされていません **。**</span><span class="sxs-lookup"><span data-stu-id="d4d1c-231">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="d4d1c-232">**アンカー** は Holographic リモート処理ではまだサポートされていませんが、近い将来に登場します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-232">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="d4d1c-233">**手動メッシュ** 追跡、 **QR コード**、 **XRMeshSubsystem** はまだサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-233">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="d4d1c-234">**Azure 空間アンカー** のサポートは、今後のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-234">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="d4d1c-235">**ARM64** は、HoloLens 2 アプリで唯一サポートされているプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-235">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="d4d1c-236">**ARM** プラットフォームは今後のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-236">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="d4d1c-237">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d4d1c-237">Troubleshooting</span></span>

<span data-ttu-id="d4d1c-238">HoloLens 2 で Unity アプリを中断および再開すると、アプリは正しく再開できなくなります。これにより、HoloLens ビューでは、4つのスピン点が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-238">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="d4d1c-239">回避策として、OpenXR プロジェクト設定で [ **深さの送信モード** ] を **[なし** ] に設定します。</span><span class="sxs-lookup"><span data-stu-id="d4d1c-239">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
