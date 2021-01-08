---
title: Holographic リモート処理リモートアプリの記述 (OpenXR)
description: OpenXR で Holographic リモート処理アプリを使用して、リモートコンピューターでレンダリングされたリモートコンテンツを HoloLens 2 にストリーミングする方法について説明します。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、NuGet
ms.openlocfilehash: 616765143309fe2a4883c1393713133fcbe2a9d5
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006492"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a><span data-ttu-id="49c5d-104">OpenXR API を使用した Holographic リモート処理リモートアプリの作成</span><span class="sxs-lookup"><span data-stu-id="49c5d-104">Writing a Holographic Remoting remote app using the OpenXR API</span></span>

>[!IMPORTANT]
><span data-ttu-id="49c5d-105">このドキュメントでは、 [OPENXR API](../native/openxr.md)を使用して HoloLens 2 および Windows Mixed Reality ヘッドセット用のリモートアプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-105">This document describes the creation of a remote application for HoloLens 2 and Windows Mixed Reality headsets using the [OpenXR API](../native/openxr.md).</span></span> <span data-ttu-id="49c5d-106">HoloLens のリモートアプリケーション **(第1世代)** では、NuGet **パッケージバージョン 1.x** を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49c5d-106">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="49c5d-107">これは、HoloLens 2 用に作成されたリモートアプリケーションが HoloLens 1 と互換性がないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-107">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="49c5d-108">HoloLens 1 のドキュメントについては、 [こちら](add-holographic-remoting.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49c5d-108">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="49c5d-109">Holographic リモート処理アプリを使用すると、リモートでレンダリングされたコンテンツを HoloLens 2 および Windows Mixed Reality のイマーシブヘッドセットにストリーミングできます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-109">Holographic Remoting apps can stream remotely rendered content to HoloLens 2 and Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="49c5d-110">また、より多くのシステムリソースにアクセスしたり、既存のデスクトップ PC ソフトウェアにリモートの [イマーシブビュー](../../design/app-views.md) を統合したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-110">You can also access more system resources and integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="49c5d-111">リモートアプリは HoloLens 2 から入力データストリームを受け取り、仮想イマーシブビューでコンテンツをレンダリングし、コンテンツフレームを HoloLens 2 にストリームバックします。</span><span class="sxs-lookup"><span data-stu-id="49c5d-111">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="49c5d-112">接続は標準の Wi-fi を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="49c5d-113">Holographic リモート処理は、NuGet パケット経由でデスクトップまたは UWP アプリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-113">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="49c5d-114">接続を処理し、イマーシブビューでレンダリングする追加のコードが必要です。</span><span class="sxs-lookup"><span data-stu-id="49c5d-114">Additional code is required which handles the connection and renders in an immersive view.</span></span> <span data-ttu-id="49c5d-115">一般的なリモート処理接続では、待機時間が50ミリ秒に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-115">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="49c5d-116">プレーヤーアプリは、リアルタイムで待機時間を報告できます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-116">The player app can report the latency in real time.</span></span>

<span data-ttu-id="49c5d-117">このページのすべてのコードと作業中のプロジェクトは、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)にあります。</span><span class="sxs-lookup"><span data-stu-id="49c5d-117">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49c5d-118">前提条件</span><span class="sxs-lookup"><span data-stu-id="49c5d-118">Prerequisites</span></span>

<span data-ttu-id="49c5d-119">開始点としては、OpenXR ベースのデスクトップまたは UWP アプリを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="49c5d-119">A good starting point is a working OpenXR based Desktop or UWP app.</span></span> <span data-ttu-id="49c5d-120">詳細については、「 [OpenXR の概要](../native/openxr-getting-started.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49c5d-120">For details see [Getting started with OpenXR](../native/openxr-getting-started.md).</span></span>

>[!IMPORTANT]
><span data-ttu-id="49c5d-121">Holographic リモート処理を使用するすべてのアプリは、 [マルチスレッドアパートメント](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)を使用するように作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49c5d-121">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="49c5d-122">[シングルスレッドアパートメント](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments)の使用はサポートされていますが、パフォーマンスが低下し、再生中に途切れが生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="49c5d-122">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="49c5d-123">C++ を使用している場合、winrt [winrt:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) 、マルチスレッドアパートメントが既定値です。</span><span class="sxs-lookup"><span data-stu-id="49c5d-123">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="49c5d-124">Holographic リモート処理 NuGet パッケージを取得する</span><span class="sxs-lookup"><span data-stu-id="49c5d-124">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="49c5d-125">Visual Studio で NuGet パッケージをプロジェクトに追加するには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49c5d-125">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="49c5d-126">Visual Studio でプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-126">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="49c5d-127">プロジェクトノードを右クリックし、[ **NuGet パッケージの管理...** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-127">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="49c5d-128">表示されるパネルで、[ **参照** ] を選択し、"Holographic Remoting" を検索します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-128">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="49c5d-129">[ **Holographic**] を選択して **、最新の** 2.x バージョンを選択し、[ **インストール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-129">Select **Microsoft.Holographic.Remoting.OpenXr**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="49c5d-130">[ **プレビュー** ] ダイアログが表示されたら、[ **OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-130">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="49c5d-131">[使用許諾契約書] ダイアログボックスが表示されたら、[ **同意** する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-131">Select **I Accept** when the license agreement dialog pops up.</span></span>
7. <span data-ttu-id="49c5d-132">次の NuGet パッケージに対して手順 3. ~ 6. を繰り返します: OpenXR、OpenXR</span><span class="sxs-lookup"><span data-stu-id="49c5d-132">Repeat the steps 3 to 6 for the following NuGet Packages: OpenXR.Headers, OpenXR.Loader</span></span>

>[!NOTE]
><span data-ttu-id="49c5d-133">HoloLens 1 を対象とする開発者は、NuGet パッケージ **のバージョン 1.x** を引き続き利用できます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-133">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="49c5d-134">詳細については、「 [Add Holographic Remoting (HoloLens (第1世代))](add-holographic-remoting.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49c5d-134">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="select-the-holographic-remoting-openxr-runtime"></a><span data-ttu-id="49c5d-135">Holographic Remoting OpenXR ランタイムを選択します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-135">Select the Holographic Remoting OpenXR runtime</span></span>

<span data-ttu-id="49c5d-136">リモートアプリで行う必要がある最初の手順は、Holographic NuGet パッケージの一部である Holographic Remoting OpenXR runtime を選択することです。</span><span class="sxs-lookup"><span data-stu-id="49c5d-136">The first step you need to do in your remote app is to select the Holographic Remoting OpenXR runtime, which is part of the Microsoft.Holographic.Remoting.OpenXr NuGet package.</span></span> <span data-ttu-id="49c5d-137">これを行うには、 ```XR_RUNTIME_JSON``` 環境変数を、アプリ内のファイルの RemotingXR.jsのパスに設定します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-137">You can do this by setting the ```XR_RUNTIME_JSON``` environment variable to the path of the RemotingXR.json file within your app.</span></span> <span data-ttu-id="49c5d-138">この環境変数は、システムの既定の OpenXR ランタイムを使用せずに、代わりに Holographic Remoting OpenXR runtime にリダイレクトするために OpenXR ローダーによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-138">This environment variable is used by the OpenXR loader to not use the system default OpenXR runtime but instead redirect to the Holographic Remoting OpenXR runtime.</span></span> <span data-ttu-id="49c5d-139">OpenXr NuGet パッケージを使用する場合、ファイルの RemotingXR.jsは、コンパイル時に出力フォルダーに自動的にコピーされます。 OpenXR ランタイムの選択は、通常、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="49c5d-139">When using the Microsoft.Holographic.Remoting.OpenXr NuGet package the RemotingXR.json file is automatically copied during compilation to the output folder, the OpenXR runtime selection typically looks as follows.</span></span>

```cpp
bool EnableRemotingXR() {
    wchar_t executablePath[MAX_PATH];
    if (GetModuleFileNameW(NULL, executablePath, ARRAYSIZE(executablePath)) == 0) {
        return false;
    }
    
    std::filesystem::path filename(executablePath);
    filename = filename.replace_filename("RemotingXR.json");

    if (std::filesystem::exists(filename)) {
        SetEnvironmentVariableW(L"XR_RUNTIME_JSON", filename.c_str());
            return true;
        }

    return false;
}
```

## <a name="create-xrinstance-with-holographic-remoting-extension"></a><span data-ttu-id="49c5d-140">Holographic Remoting 拡張機能を使用して XrInstance を作成する</span><span class="sxs-lookup"><span data-stu-id="49c5d-140">Create XrInstance with Holographic Remoting Extension</span></span>

<span data-ttu-id="49c5d-141">一般的な OpenXR アプリの最初の手順は、OpenXR extensions を選択して XrInstance を作成することです。</span><span class="sxs-lookup"><span data-stu-id="49c5d-141">The first step a typical OpenXR app is supposed to do is to select OpenXR extensions and create an XrInstance.</span></span> <span data-ttu-id="49c5d-142">OpenXR core 仕様では、リモート処理固有の API は提供されません。</span><span class="sxs-lookup"><span data-stu-id="49c5d-142">The OpenXR core specification doesn't provide any remoting specific API.</span></span> <span data-ttu-id="49c5d-143">そのため、Holographic Remoting では、という名前の独自の OpenXR 拡張機能が導入さ ```XR_MSFT_holographic_remoting``` れています。</span><span class="sxs-lookup"><span data-stu-id="49c5d-143">For that reason Holographic Remoting introduces its own OpenXR extension named ```XR_MSFT_holographic_remoting```.</span></span> <span data-ttu-id="49c5d-144">XrCreateInstance を呼び出したときに、 ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` が XrInstanceCreateInfo に含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-144">Ensure that when you call xrCreateInstance the ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` is included in the XrInstanceCreateInfo.</span></span>

>[!TIP]
><span data-ttu-id="49c5d-145">既定では、アプリのレンダリングされたコンテンツは、HoloLens 2 または Windows Mixed Reality ヘッドセットで実行されている Holographic リモート処理プレーヤーにのみストリーミングされます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-145">By default the rendered content of your app is only streamed to the Holographic Remoting player either running on a HoloLens 2 or on a Windows Mixed Reality headsets.</span></span> <span data-ttu-id="49c5d-146">また、レンダリングされたコンテンツをリモート PC に表示するために、ウィンドウのスワップチェーンを使用して、Holographic リモート処理には、という名前の2つ目の OpenXR 拡張機能が用意されて ```XR_MSFT_holographic_remoting_frame_mirroring``` います。</span><span class="sxs-lookup"><span data-stu-id="49c5d-146">To also display the rendered content on the remote PC, via a swap-chain of a window for instance, Holographic Remoting provides a second OpenXR extension named ```XR_MSFT_holographic_remoting_frame_mirroring```.</span></span> <span data-ttu-id="49c5d-147">また、この機能を使用する場合は、を使用してこの拡張機能を有効にし ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` ます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-147">Ensure to also enable this extension using ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` in case you want to use that functionality.</span></span>

>[!IMPORTANT]
><span data-ttu-id="49c5d-148">Holographic Remoting OpenXR extension API の詳細については、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)に記載されている[仕様](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="49c5d-148">To learn about the Holographic Remoting OpenXR extension API, check out the [specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) which can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="connect-to-the-device"></a><span data-ttu-id="49c5d-149">デバイスへの接続</span><span class="sxs-lookup"><span data-stu-id="49c5d-149">Connect to the device</span></span>

<span data-ttu-id="49c5d-150">リモートアプリによって XrInstance が作成され、xrGetSystem 経由で XrSystemId に照会された後、プレーヤーデバイスへの接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-150">After your remote app has created the XrInstance and queried the XrSystemId via xrGetSystem a connection to the player device can be established.</span></span>

>[!WARNING]
> <span data-ttu-id="49c5d-151">Holographic Remoting OpenXR ランタイムは、接続が確立された後に、ビュー構成や環境 blend モードなどのデバイス固有のデータのみを提供できます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-151">The Holographic Remoting OpenXR runtime is only able to provide device specific data such as view configurations or environment blend modes after a connection has been established.</span></span> <span data-ttu-id="49c5d-152">```xrEnumerateViewConfigurations```、 ```xrEnumerateViewConfigurationViews``` 、 ```xrGetViewConfigurationProperties``` 、 ```xrEnumerateEnvironmentBlendModes``` 、およびで ```xrGetSystemProperties``` は、既定値が使用されます。これは通常、HoloLens 2 で実行されているプレーヤーに接続してから完全に接続する場合に使用するものと一致します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-152">```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews```, ```xrGetViewConfigurationProperties```, ```xrEnumerateEnvironmentBlendModes```, and ```xrGetSystemProperties``` will give you default values, matching what you would typically get if you connect to a player running on a HoloLens 2, before being fully connected.</span></span>
<span data-ttu-id="49c5d-153">接続が確立される前に、これらのメソッドを呼び出さないことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="49c5d-153">It is strongly recommended to not call these methods before a connection has been established.</span></span> <span data-ttu-id="49c5d-154">提案は、XrSession が正常に作成され、セッション状態が少なくとも XR_SESSION_STATE_READY になった後に、これらのメソッドで使用されます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-154">The suggestion is used these methods after the XrSession has been successfully created and the session state is at least XR_SESSION_STATE_READY.</span></span>

<span data-ttu-id="49c5d-155">最大ビットレート、オーディオ対応、ビデオコーデック、深度バッファーストリーム解像度などの一般的なプロパティは、次のようにを使用して構成でき ```xrRemotingSetContextPropertiesMSFT``` ます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-155">General properties such as max bitrate, audio enabled, video codec, or depth buffer stream resolution can be configured via ```xrRemotingSetContextPropertiesMSFT``` as follows.</span></span>

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

<span data-ttu-id="49c5d-156">接続は、次の2つの方法のいずれかで実行できます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-156">The connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="49c5d-157">リモートアプリは、デバイスで実行されているプレーヤーに接続します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-157">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="49c5d-158">デバイスで実行されているプレーヤーは、リモートアプリに接続します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-158">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="49c5d-159">リモートアプリからプレーヤーデバイスへの接続を確立するには、 ```xrRemotingConnectMSFT``` 構造体を介してホスト名とポートを指定するメソッドを呼び出し  ```XrRemotingConnectInfoMSFT``` ます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-159">To establish a connection from the remote app to the player device call the ```xrRemotingConnectMSFT``` method specifying the hostname and port via the  ```XrRemotingConnectInfoMSFT``` structure.</span></span> <span data-ttu-id="49c5d-160">Holographic リモート処理プレーヤーによって使用されるポートは **8265** です。</span><span class="sxs-lookup"><span data-stu-id="49c5d-160">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

<span data-ttu-id="49c5d-161">リモートアプリでの着信接続のリッスンは、メソッドを呼び出すことによって行うことができ ```xrRemotingListenMSFT``` ます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-161">Listening for incoming connections on the remote app can be done by calling the ```xrRemotingListenMSFT``` method.</span></span> <span data-ttu-id="49c5d-162">ハンドシェイクポートとトランスポートポートの両方を構造体を使用して指定でき ```XrRemotingListenInfoMSFT``` ます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-162">Both the handshake port and transport port can be specified via the ```XrRemotingListenInfoMSFT``` structure.</span></span> <span data-ttu-id="49c5d-163">ハンドシェイクポートは、初期ハンドシェイクに使用されます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-163">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="49c5d-164">データは、トランスポートポートを介して送信されます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-164">The data is then sent over the transport port.</span></span> <span data-ttu-id="49c5d-165">既定では、 **8265** および **8266** が使用されます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-165">By default **8265** and **8266** are used.</span></span>

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

<span data-ttu-id="49c5d-166">またはを呼び出すと、接続状態が切断される必要があり ```xrRemotingConnectMSFT``` ```xrRemotingListenMSFT``` ます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-166">The connection state must be disconnected when you call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT```.</span></span> <span data-ttu-id="49c5d-167">XrInstance を作成し、経由で XrSystemId に対してクエリを実行した後、いつでも接続状態を取得でき ```xrRemotingGetConnectionStateMSFT``` ます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-167">You can get the connection state at any point after you have created an XrInstance and queried for the XrSystemId via ```xrRemotingGetConnectionStateMSFT```.</span></span>

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

<span data-ttu-id="49c5d-168">使用できる接続状態は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="49c5d-168">Available connection states are:</span></span>
- <span data-ttu-id="49c5d-169">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="49c5d-169">XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT</span></span>
- <span data-ttu-id="49c5d-170">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span><span class="sxs-lookup"><span data-stu-id="49c5d-170">XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT</span></span>
- <span data-ttu-id="49c5d-171">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span><span class="sxs-lookup"><span data-stu-id="49c5d-171">XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT</span></span>

>[!IMPORTANT]
> <span data-ttu-id="49c5d-172">```xrRemotingConnectMSFT``````xrRemotingListenMSFT```xrCreateSession を介して XrSession を作成する前に、またはを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="49c5d-172">```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` must be called before trying to create a XrSession via xrCreateSession.</span></span> <span data-ttu-id="49c5d-173">接続状態がのときに XrSession を作成しようとすると、 ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` セッションの作成は成功しますが、セッションの状態は直ちに XR_SESSION_STATE_LOSS_PENDING に移行されます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-173">If you try to create a XrSession while the connection state is ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session creation will succeed but the session state will immediately transition to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="49c5d-174">Holographic リモート処理の実装では ```xrCreateSession``` 、接続が確立されるのを待機できます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-174">Holographic Remoting's implementation of ```xrCreateSession``` supports waiting for a connection to be established.</span></span> <span data-ttu-id="49c5d-175">またはを呼び出して、を呼び出すことができ ```xrRemotingConnectMSFT``` ```xrRemotingListenMSFT``` ます。この呼び出しはブロックされ、接続が確立されるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-175">You can call ```xrRemotingConnectMSFT``` or ```xrRemotingListenMSFT``` immediately followed by a call to, which will block and wait for a connection to be established.</span></span> <span data-ttu-id="49c5d-176">タイムアウトは10秒に固定されています。</span><span class="sxs-lookup"><span data-stu-id="49c5d-176">The timeout is fixed to 10 seconds.</span></span> <span data-ttu-id="49c5d-177">この時間内に接続を確立できる場合、XrSession の作成は成功し、セッションの状態は XR_SESSION_STATE_READY に移行されます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-177">If a connection can be established within this time the XrSession creation will succeed and the session state will transition to XR_SESSION_STATE_READY.</span></span> <span data-ttu-id="49c5d-178">接続を確立できない場合は、セッションの作成も成功しますが、直ちに XR_SESSION_STATE_LOSS_PENDING に移行されます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-178">In case no connection can be established the session creation also succeeds but immediately transitions to XR_SESSION_STATE_LOSS_PENDING.</span></span>

<span data-ttu-id="49c5d-179">一般に、接続状態は XrSession 状態になります。</span><span class="sxs-lookup"><span data-stu-id="49c5d-179">In general, the connection state is couple with the XrSession state.</span></span> <span data-ttu-id="49c5d-180">接続状態の変更は、セッションの状態にも影響します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-180">Any change to the connection state also affects the session state.</span></span> <span data-ttu-id="49c5d-181">たとえば、接続状態をからに切り替えた場合、 `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` セッション状態は XR_SESSION_STATE_LOSS_PENDING にも移行します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-181">For instance, if the connection state switches from `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` to ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` the session state will transition to XR_SESSION_STATE_LOSS_PENDING as well.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="49c5d-182">リモート処理固有のイベントの処理</span><span class="sxs-lookup"><span data-stu-id="49c5d-182">Handling Remoting specific events</span></span>

<span data-ttu-id="49c5d-183">Holographic Remoting OpenXR runtime は、接続の状態を監視するために重要な3つのイベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-183">The Holographic Remoting OpenXR runtime exposes three events, which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="49c5d-184">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: デバイスへの接続が正常に確立されたときにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-184">```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Triggered when a connection to the device has been successfully established.</span></span>
2) <span data-ttu-id="49c5d-185">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: 確立された接続が閉じられた場合、または接続が確立できなかった場合にトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-185">```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Triggered if an established connection is closed or a connection couldn't be established.</span></span>
3) <span data-ttu-id="49c5d-186">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: 受信接続のリッスンが開始されたとき。</span><span class="sxs-lookup"><span data-stu-id="49c5d-186">```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: When listening for incoming connections starts.</span></span>

<span data-ttu-id="49c5d-187">これらのイベントはキューに配置され、リモートアプリは定期的 via を使用してキューから読み取る必要があり ```xrPollEvent``` ます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-187">These events are placed in a queue and your remote app must read from the queue with regularity via ```xrPollEvent```.</span></span>

```cpp
auto pollEvent = [&](XrEventDataBuffer& eventData) -> bool {
    eventData.type = XR_TYPE_EVENT_DATA_BUFFER;
    eventData.next = nullptr;
    return CHECK_XRCMD(xrPollEvent(m_instance.Get(), &eventData)) == XR_SUCCESS;
};

XrEventDataBuffer eventData{};
while (pollEvent(eventData)) {
    switch (eventData.type) {
    
    ...
    
    case XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Listening on port %d",
                    reinterpret_cast<const XrRemotingEventDataListeningMSFT*>(&eventData)->listeningPort);
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Connected.");
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Disconnected - Reason: %d",
                    reinterpret_cast<const XrRemotingEventDataDisconnectedMSFT*>(&eventData)->disconnectReason);
        break;
    }
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="49c5d-188">ストリーミングされるコンテンツをローカルでプレビューする</span><span class="sxs-lookup"><span data-stu-id="49c5d-188">Preview streamed content locally</span></span>

<span data-ttu-id="49c5d-189">デバイスに送信されたのと同じコンテンツをリモートアプリで表示するには、 ```XR_MSFT_holographic_remoting_frame_mirroring``` 拡張機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-189">To display the same content in the remote app that is sent to the device the ```XR_MSFT_holographic_remoting_frame_mirroring``` extension can be used.</span></span> <span data-ttu-id="49c5d-190">この拡張機能では、次のように、XrFrameEndInfo にチェーンされていないを使用して、xrEndFrame にテクスチャを送信でき ```XrRemotingFrameMirrorImageInfoMSFT``` ます。</span><span class="sxs-lookup"><span data-stu-id="49c5d-190">With this extension, you can submit a texture to xrEndFrame by using the ```XrRemotingFrameMirrorImageInfoMSFT``` that isn't chained to the XrFrameEndInfo as follows.</span></span>

```cpp
XrFrameEndInfo frameEndInfo{XR_TYPE_FRAME_END_INFO};
...

XrRemotingFrameMirrorImageD3D11MSFT mirrorImageD3D11{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_D3D11_MSFT)};
mirrorImageD3D11.texture = m_window->GetNextSwapchainTexture();

XrRemotingFrameMirrorImageInfoMSFT mirrorImageEndInfo{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_INFO_MSFT)};
mirrorImageEndInfo.image = reinterpret_cast<const XrRemotingFrameMirrorImageBaseHeaderMSFT*>(&mirrorImageD3D11);

frameEndInfo.next = &mirrorImageEndInfo;

xrEndFrame(m_session.Get(), &frameEndInfo);

m_window->PresentSwapchain();
```

<span data-ttu-id="49c5d-191">上の例では、DX11 のスワップチェーンテクスチャを使用して、xrEndFrame の呼び出しの直後にウィンドウを表示します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-191">The example above uses a DX11 swap-chain texture and presents the window immediately after the call to xrEndFrame.</span></span> <span data-ttu-id="49c5d-192">使用量はスワップチェーンテクスチャに限定されておらず、追加の GPU 同期は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="49c5d-192">The usage isn't restricted to swap-chain textures and no additional GPU synchronization is required.</span></span> <span data-ttu-id="49c5d-193">使用法と制約の詳細については、 [拡張機能の仕様](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="49c5d-193">For details on usage and constraints check out the [extension specification](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).</span></span>
<span data-ttu-id="49c5d-194">リモートアプリで DX12 を使用している場合は、XrRemotingFrameMirrorImageD3D11MSFT ではなく XrRemotingFrameMirrorImageD3D12MSFT を使用します。</span><span class="sxs-lookup"><span data-stu-id="49c5d-194">If your remote app is using DX12 use XrRemotingFrameMirrorImageD3D12MSFT instead of XrRemotingFrameMirrorImageD3D11MSFT.</span></span>

## <a name="see-also"></a><span data-ttu-id="49c5d-195">参照</span><span class="sxs-lookup"><span data-stu-id="49c5d-195">See Also</span></span>
* [<span data-ttu-id="49c5d-196">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="49c5d-196">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="49c5d-197">Holographic Remoting を使用したセキュリティで保護された接続の確立</span><span class="sxs-lookup"><span data-stu-id="49c5d-197">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="49c5d-198">Holographic リモート処理のトラブルシューティングと制限事項</span><span class="sxs-lookup"><span data-stu-id="49c5d-198">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="49c5d-199">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="49c5d-199">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="49c5d-200">Microsoft プライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="49c5d-200">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
