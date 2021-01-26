---
title: Holographic リモート処理リモートアプリの作成 (WMR)
description: HolographicSpace で Holographic リモート処理アプリを使用して、リモートコンピューターでレンダリングされたリモートコンテンツを HoloLens 2 にストリーミングする方法について説明します。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、NuGet
ms.openlocfilehash: 6884c2679b155c36a21bcf89352524e4957a9f20
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810076"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a><span data-ttu-id="3dba7-104">HolographicSpace API を使用した Holographic リモート処理リモートアプリの作成</span><span class="sxs-lookup"><span data-stu-id="3dba7-104">Writing a Holographic Remoting remote app using the HolographicSpace API</span></span>

>[!IMPORTANT]
><span data-ttu-id="3dba7-105">このドキュメントでは、 [HOLOGRAPHICSPACE API](../native/getting-a-holographicspace.md)を使用して HoloLens 2 用のリモートアプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3dba7-105">This document describes the creation of a remote application for HoloLens 2 using the [HolographicSpace API](../native/getting-a-holographicspace.md).</span></span> <span data-ttu-id="3dba7-106">HoloLens のリモートアプリケーション **(第1世代)** では、NuGet **パッケージバージョン 1.x** を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dba7-106">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="3dba7-107">これは、HoloLens 2 用に作成されたリモートアプリケーションが HoloLens 1 と互換性がないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="3dba7-107">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="3dba7-108">HoloLens 1 のドキュメントについては、 [こちら](add-holographic-remoting.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dba7-108">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="3dba7-109">Holographic リモート処理アプリを使用すると、リモートでレンダリングされたコンテンツを HoloLens 2 および Windows Mixed Reality のイマーシブヘッドセットにストリーミングできます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-109">Holographic Remoting apps can stream remotely rendered content to HoloLens 2 and Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="3dba7-110">また、より多くのシステムリソースにアクセスしたり、既存のデスクトップ PC ソフトウェアにリモートの [イマーシブビュー](../../design/app-views.md) を統合したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-110">You can also access more system resources and integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="3dba7-111">リモートアプリは HoloLens 2 から入力データストリームを受け取り、仮想イマーシブビューでコンテンツをレンダリングし、コンテンツフレームを HoloLens 2 にストリームバックします。</span><span class="sxs-lookup"><span data-stu-id="3dba7-111">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="3dba7-112">接続は標準の Wi-fi を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="3dba7-113">Holographic リモート処理は、NuGet パケット経由でデスクトップまたは UWP アプリに追加されます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-113">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="3dba7-114">接続を処理し、イマーシブビューでレンダリングする追加のコードが必要です。</span><span class="sxs-lookup"><span data-stu-id="3dba7-114">Additional code is required which handles the connection and renders in an immersive view.</span></span> <span data-ttu-id="3dba7-115">一般的なリモート処理接続では、待機時間が50ミリ秒に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-115">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="3dba7-116">プレーヤーアプリは、リアルタイムで待機時間を報告できます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-116">The player app can report the latency in real time.</span></span>

<span data-ttu-id="3dba7-117">このページのすべてのコードと作業中のプロジェクトは、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)にあります。</span><span class="sxs-lookup"><span data-stu-id="3dba7-117">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3dba7-118">前提条件</span><span class="sxs-lookup"><span data-stu-id="3dba7-118">Prerequisites</span></span>

<span data-ttu-id="3dba7-119">開始点としては、 [HOLOGRAPHICSPACE API](../native/getting-a-holographicspace.md)を対象とする、動作する DirectX ベースのデスクトップまたは UWP アプリを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3dba7-119">A good starting point is a working DirectX based Desktop or UWP app, which targets the [HolographicSpace API](../native/getting-a-holographicspace.md).</span></span> <span data-ttu-id="3dba7-120">詳細については、「 [DirectX 開発の概要](../native/directx-development-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dba7-120">For details see [DirectX development overview](../native/directx-development-overview.md).</span></span> <span data-ttu-id="3dba7-121">[C++ holographic プロジェクトテンプレート](../native/creating-a-holographic-directx-project.md)は、出発点として適しています。</span><span class="sxs-lookup"><span data-stu-id="3dba7-121">The [C++ holographic project template](../native/creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="3dba7-122">Holographic リモート処理を使用するすべてのアプリは、 [マルチスレッドアパートメント](/windows/win32/com/multithreaded-apartments)を使用するように作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dba7-122">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](/windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="3dba7-123">[シングルスレッドアパートメント](/windows/win32/com/single-threaded-apartments)の使用はサポートされていますが、パフォーマンスが低下し、再生中に途切れが生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3dba7-123">The use of a [single-threaded apartment](/windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="3dba7-124">C++ を使用している場合、winrt [winrt:: init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) 、マルチスレッドアパートメントが既定値です。</span><span class="sxs-lookup"><span data-stu-id="3dba7-124">When using C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="3dba7-125">Holographic リモート処理 NuGet パッケージを取得する</span><span class="sxs-lookup"><span data-stu-id="3dba7-125">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="3dba7-126">Visual Studio で NuGet パッケージをプロジェクトに追加するには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dba7-126">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="3dba7-127">Visual Studio でプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-127">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="3dba7-128">プロジェクトノードを右クリックし、[ **NuGet パッケージの管理...** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dba7-128">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="3dba7-129">表示されるパネルで、[ **参照** ] を選択し、"Holographic Remoting" を検索します。</span><span class="sxs-lookup"><span data-stu-id="3dba7-129">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="3dba7-130">[ **Holographic**] を選択し、最新の2.x バージョンを選択して [**インストール**] を選択 **します。**</span><span class="sxs-lookup"><span data-stu-id="3dba7-130">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="3dba7-131">[ **プレビュー** ] ダイアログが表示されたら、[ **OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dba7-131">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="3dba7-132">[使用許諾契約書] ダイアログボックスが表示されたら、[ **同意** する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3dba7-132">Select **I Accept** when the license agreement dialog pops up.</span></span>

>[!NOTE]
><span data-ttu-id="3dba7-133">HoloLens 1 を対象とする開発者は、NuGet パッケージ **のバージョン 1.x** を引き続き利用できます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-133">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="3dba7-134">詳細については、「 [Add Holographic Remoting (HoloLens (第1世代))](add-holographic-remoting.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dba7-134">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="3dba7-135">リモートコンテキストを作成する</span><span class="sxs-lookup"><span data-stu-id="3dba7-135">Create the remote context</span></span>

<span data-ttu-id="3dba7-136">最初の手順として、アプリケーションでリモートコンテキストを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dba7-136">As a first step the application should create a remote context.</span></span>

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
><span data-ttu-id="3dba7-137">Holographic リモート処理は、Windows の一部である Windows Mixed Reality ランタイムをリモート処理固有のランタイムに置き換えることによって機能します。</span><span class="sxs-lookup"><span data-stu-id="3dba7-137">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="3dba7-138">これは、リモートコンテキストの作成時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-138">This is done during the creation of the remote context.</span></span> <span data-ttu-id="3dba7-139">そのため、リモートコンテキストを作成する前に Windows Mixed Reality API を呼び出すと、予期しない動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3dba7-139">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="3dba7-140">推奨される方法は、混合の現実 API と対話する前に、できるだけ早くリモートコンテキストを作成することです。</span><span class="sxs-lookup"><span data-stu-id="3dba7-140">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="3dba7-141">Windows Mixed Reality API を使用して作成または取得したオブジェクトを、後で作成または取得したオブジェクトと共に使用することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="3dba7-141">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="3dba7-142">次に、holographic 領域を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dba7-142">Next the holographic space needs to be created.</span></span> <span data-ttu-id="3dba7-143">CoreWindow の指定は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="3dba7-143">Specifying a CoreWindow isn't required.</span></span> <span data-ttu-id="3dba7-144">CoreWindow を持たないデスクトップアプリは、のみを渡すことができ ```nullptr``` ます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-144">Desktop apps that don't have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="3dba7-145">デバイスへの接続</span><span class="sxs-lookup"><span data-stu-id="3dba7-145">Connect to the device</span></span>

<span data-ttu-id="3dba7-146">リモートアプリがコンテンツを表示できる状態になったら、windows media player デバイスへの接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-146">When the remote app is ready for rendering content a connection to the player device can be established.</span></span>

<span data-ttu-id="3dba7-147">接続は、次の2つの方法のいずれかで実行できます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-147">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="3dba7-148">リモートアプリは、デバイスで実行されているプレーヤーに接続します。</span><span class="sxs-lookup"><span data-stu-id="3dba7-148">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="3dba7-149">デバイスで実行されているプレーヤーは、リモートアプリに接続します。</span><span class="sxs-lookup"><span data-stu-id="3dba7-149">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="3dba7-150">リモートアプリからプレーヤーデバイスへの接続を確立するには、 ```Connect``` リモートコンテキストでホスト名とポートを指定してメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3dba7-150">To establish a connection from the remote app to the player device call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="3dba7-151">Holographic リモート処理プレーヤーによって使用されるポートは **8265** です。</span><span class="sxs-lookup"><span data-stu-id="3dba7-151">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="3dba7-152">C++/WinRT API と同様に、 ```Connect``` 処理する必要がある winrt:: hresult_error をスローすることがあります。</span><span class="sxs-lookup"><span data-stu-id="3dba7-152">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="3dba7-153">[C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)言語のプロジェクションを使用しないようにするには、 ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` Holographic リモート処理 NuGet パッケージ内にあるファイルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-153">To avoid using [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="3dba7-154">これには、基になる COM インターフェイスの宣言が含まれます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-154">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="3dba7-155">ただし、C++/WinRT を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3dba7-155">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="3dba7-156">リモートアプリでの着信接続のリッスンは、メソッドを呼び出すことによって行うことができ ```Listen``` ます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-156">Listening for incoming connections on the remote app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="3dba7-157">この呼び出しでは、ハンドシェイクポートとトランスポートポートの両方を指定できます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-157">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="3dba7-158">ハンドシェイクポートは、初期ハンドシェイクに使用されます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-158">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="3dba7-159">データは、トランスポートポートを介して送信されます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-159">The data is then sent over the transport port.</span></span> <span data-ttu-id="3dba7-160">既定では、 **8265** および **8266** が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-160">By default **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="3dba7-161">```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet パッケージ内には、Holographic Remoting によって公開される API に関する詳細なドキュメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3dba7-161">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="3dba7-162">リモート処理固有のイベントの処理</span><span class="sxs-lookup"><span data-stu-id="3dba7-162">Handling Remoting specific events</span></span>

<span data-ttu-id="3dba7-163">リモートコンテキストは、接続の状態を監視するために重要な3つのイベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="3dba7-163">The remote context exposes three events, which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="3dba7-164">OnConnected: デバイスへの接続が正常に確立されたときにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-164">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="3dba7-165">OnDisconnected: 確立された接続が閉じられたか、接続が確立できなかった場合にトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-165">OnDisconnected: Triggered if an established connection is closed or a connection couldn't be established.</span></span>
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) <span data-ttu-id="3dba7-166">OnListening: 受信接続のリッスンが開始されます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-166">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="3dba7-167">さらに、リモートコンテキストのプロパティを使用して接続状態を照会することもでき ```ConnectionState``` ます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-167">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="3dba7-168">音声イベントの処理</span><span class="sxs-lookup"><span data-stu-id="3dba7-168">Handling speech events</span></span>

<span data-ttu-id="3dba7-169">リモート音声インターフェイスを使用すると、音声トリガーを HoloLens 2 に登録し、リモートアプリケーションにリモート処理することができます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-169">Using the remote speech interface it's possible to register speech triggers with HoloLens 2 and have them remoted to the remote application.</span></span>

<span data-ttu-id="3dba7-170">この追加のメンバーは、リモート音声の状態を追跡するために必要です。</span><span class="sxs-lookup"><span data-stu-id="3dba7-170">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="3dba7-171">まず、リモート音声インターフェイスを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dba7-171">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="3dba7-172">非同期ヘルパーメソッドを使用すると、リモート音声を初期化できます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-172">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="3dba7-173">初期化にはかなりの時間がかかる場合があるため、非同期的に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dba7-173">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="3dba7-174">C++ での[同時実行と非同期操作](/windows/uwp/cpp-and-winrt-apis/concurrency)c++/winrtで非同期関数を作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3dba7-174">[Concurrency and asynchronous operations with C++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

<span data-ttu-id="3dba7-175">認識する語句を指定する方法は2つあります。</span><span class="sxs-lookup"><span data-stu-id="3dba7-175">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="3dba7-176">音声文法 xml ファイル内の仕様。</span><span class="sxs-lookup"><span data-stu-id="3dba7-176">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="3dba7-177">詳細について [は、「基本的な XML 文法を作成する方法](/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dba7-177">See [How to create a basic XML Grammar](/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="3dba7-178">を指定するには、をディクショナリベクター内に渡し ```ApplyParameters``` ます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-178">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="3dba7-179">次に、On認識された音声コールバック内で、speech イベントを処理できます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-179">Inside the OnRecognizedSpeech callback, the speech events can then be processed:</span></span>

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="3dba7-180">ストリーミングされるコンテンツをローカルでプレビューする</span><span class="sxs-lookup"><span data-stu-id="3dba7-180">Preview streamed content locally</span></span>

<span data-ttu-id="3dba7-181">デバイスに送信されるのと同じコンテンツをリモートアプリで表示するには、 ```OnSendFrame``` リモートコンテキストのイベントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-181">To display the same content in the remote app that is sent to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="3dba7-182">```OnSendFrame```イベントは、Holographic リモート処理ライブラリが現在のフレームをリモートデバイスに送信するたびにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-182">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="3dba7-183">これは、コンテンツを撮影し、デスクトップや UWP ウィンドウに array.blit するのに最適な時間です。</span><span class="sxs-lookup"><span data-stu-id="3dba7-183">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a><span data-ttu-id="3dba7-184">深さの再投影</span><span class="sxs-lookup"><span data-stu-id="3dba7-184">Depth Reprojection</span></span>

<span data-ttu-id="3dba7-185">バージョン [2.1.0](holographic-remoting-version-history.md#v2.1.0)以降では、Holographic Remoting は [深さの reprojection](hologram-stability.md#reprojection)をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3dba7-185">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0), Holographic Remoting supports [Depth Reprojection](hologram-stability.md#reprojection).</span></span> <span data-ttu-id="3dba7-186">これには、カラーバッファーと深度バッファーの両方をリモートアプリケーションから HoloLens 2 にストリーミングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3dba7-186">This requires both the color buffer and depth buffer to be streamed from the Remote application to the HoloLens 2.</span></span> <span data-ttu-id="3dba7-187">既定では、深度バッファーストリーミングが有効になり、カラーバッファーの半分の解像度を使用するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-187">By default depth buffer streaming is enabled and configured to use half the resolution of the color buffer.</span></span> <span data-ttu-id="3dba7-188">これは、次のように変更できます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-188">This can be changed as follows:</span></span>

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

<span data-ttu-id="3dba7-189">```ConfigureDepthVideoStream```HoloLens 2 への接続を確立する前に、既定値を使用しないようにする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3dba7-189">Note, if default values should not be used ```ConfigureDepthVideoStream``` must be called before establishing a connection to the HoloLens 2.</span></span> <span data-ttu-id="3dba7-190">最適な場所は、リモートコンテキストを作成した直後です。</span><span class="sxs-lookup"><span data-stu-id="3dba7-190">The best place is right after you have created the remote context.</span></span> <span data-ttu-id="3dba7-191">DepthBufferStreamResolution に指定できる値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3dba7-191">Possible values for DepthBufferStreamResolution are:</span></span>

* <span data-ttu-id="3dba7-192">Full_Resolution</span><span class="sxs-lookup"><span data-stu-id="3dba7-192">Full_Resolution</span></span>
* <span data-ttu-id="3dba7-193">Half_Resolution</span><span class="sxs-lookup"><span data-stu-id="3dba7-193">Half_Resolution</span></span>
* <span data-ttu-id="3dba7-194">Quarter_Resolution</span><span class="sxs-lookup"><span data-stu-id="3dba7-194">Quarter_Resolution</span></span>
* <span data-ttu-id="3dba7-195">無効 (バージョン [2.1.3](holographic-remoting-version-history.md#v2.1.3) を使用して追加され、追加の深度ビデオストリームが作成されない場合)</span><span class="sxs-lookup"><span data-stu-id="3dba7-195">Disabled (added with version [2.1.3](holographic-remoting-version-history.md#v2.1.3) and if used no additional depth video stream is created)</span></span>

<span data-ttu-id="3dba7-196">完全な解像度の深度バッファーを使用することは、帯域幅の要件にも影響し、指定した最大帯域幅の値について考慮する必要があることに注意してください ```CreateRemoteContext``` 。</span><span class="sxs-lookup"><span data-stu-id="3dba7-196">Keep in mind that using a full resolution depth buffer also affects bandwidth requirements and needs to be accounted for in the maximum bandwidth value you provide to ```CreateRemoteContext```.</span></span>

<span data-ttu-id="3dba7-197">解像度を構成した後、HolographicCameraRenderingParameters を使用して深度バッファーをコミットする必要もあります [。 CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)を使用します。</span><span class="sxs-lookup"><span data-stu-id="3dba7-197">Beside configuring the resolution, you also have to commit a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

<span data-ttu-id="3dba7-198">高度な再プロジェクションが HoloLens 2 で正しく動作しているかどうかを確認するには、デバイスポータルを使用して深度ビジュアライザーを有効にします。</span><span class="sxs-lookup"><span data-stu-id="3dba7-198">To verify if depth reprojection is correctly working on HoloLens 2, you can enable a depth visualizer via the Device Portal.</span></span> <span data-ttu-id="3dba7-199">詳細については、「 [奥行が正しく設定されている](hologram-stability.md#verifying-depth-is-set-correctly) ことを確認しています</span><span class="sxs-lookup"><span data-stu-id="3dba7-199">See [Verifying Depth is Set Correctly](hologram-stability.md#verifying-depth-is-set-correctly) for details.</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="3dba7-200">省略可能: カスタムデータチャネル</span><span class="sxs-lookup"><span data-stu-id="3dba7-200">Optional: Custom data channels</span></span>

<span data-ttu-id="3dba7-201">カスタムデータチャネルは、既に確立されているリモート処理接続を介してユーザーデータを送信するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="3dba7-201">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="3dba7-202">詳細については、「 [カスタムデータチャネル](holographic-remoting-custom-data-channels.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3dba7-202">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="3dba7-203">参照</span><span class="sxs-lookup"><span data-stu-id="3dba7-203">See Also</span></span>
* [<span data-ttu-id="3dba7-204">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="3dba7-204">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="3dba7-205">カスタムの Holographic Remoting データ チャネル</span><span class="sxs-lookup"><span data-stu-id="3dba7-205">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="3dba7-206">Holographic Remoting を使用したセキュリティで保護された接続の確立</span><span class="sxs-lookup"><span data-stu-id="3dba7-206">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="3dba7-207">Holographic リモート処理のトラブルシューティングと制限事項</span><span class="sxs-lookup"><span data-stu-id="3dba7-207">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="3dba7-208">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="3dba7-208">Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="3dba7-209">Microsoft プライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="3dba7-209">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)