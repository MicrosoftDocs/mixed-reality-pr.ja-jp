---
title: Holographic Remoting プレーヤーの記述
description: リモートコンピューター上にレンダリングされたコンテンツを HoloLens 2 に表示するカスタム Hologaphic リモート処理アプリを作成します。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理、NuGet、アプリケーションマニフェスト、プレーヤーコンテキスト、リモートアプリ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: 391650025398b4bdd89e30db1df7df5e3d6ab5f2
ms.sourcegitcommit: 63b7f6d5237327adc51486afcd92424b79e6118b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/26/2021
ms.locfileid: "98810124"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="2ea0a-104">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="2ea0a-104">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="2ea0a-105">このドキュメントでは、HoloLens 2 用のカスタムプレーヤーアプリケーションの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-105">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="2ea0a-106">HoloLens 2 向けに作成されたカスタムプレーヤーは、HoloLens 1 用に作成されたリモートアプリケーションと互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-106">Custom players written for HoloLens 2 are not compatible with remote applications written for HoloLens 1.</span></span> <span data-ttu-id="2ea0a-107">これは、両方のアプリケーションが NuGet **パッケージバージョン 2.x** を使用する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-107">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="2ea0a-108">カスタム Holographic リモート処理プレーヤーアプリを作成することにより、HoloLens 2 のリモートコンピューター上のから [イマーシブビュー](../../design/app-views.md) を表示できるカスタムアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-108">By creating a custom Holographic Remoting player app, you can create a custom application capable of displaying [immersive views](../../design/app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="2ea0a-109">このページのすべてのコードと作業中のプロジェクトは、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)にあります。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-109">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="2ea0a-110">Holographic リモート処理プレーヤーを使用すると、アプリは、デスクトップ PC または UWP デバイスに [レンダリング](rendering.md) された Holographic コンテンツを、より多くのシステムリソースにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-110">A Holographic Remoting player lets your app display holographic content [rendered](rendering.md) on a desktop PC or UWP device like the Xbox One with access to more system resources.</span></span> <span data-ttu-id="2ea0a-111">Holographic Remoting player アプリは、入力データを Holographic リモート処理リモートアプリケーションにストリーミングし、ビデオとオーディオストリームとしてイマーシブビューを受信します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-111">A Holographic Remoting player app streams input data to a Holographic Remoting remote application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="2ea0a-112">接続は標準の Wi-fi を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="2ea0a-113">プレーヤーアプリを作成するには、NuGet パッケージを使用して Holographic Remoting を UWP アプリに追加します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-113">To create a player app, use a NuGet package to add Holographic Remoting to your UWP app.</span></span> <span data-ttu-id="2ea0a-114">次に、接続を処理し、イマーシブビューを表示するコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-114">Then write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="2ea0a-115">前提条件</span><span class="sxs-lookup"><span data-stu-id="2ea0a-115">Prerequisites</span></span>

<span data-ttu-id="2ea0a-116">開始点としては、既に Windows Mixed Reality API を対象としている、動作する DirectX ベースの UWP アプリを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-116">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="2ea0a-117">詳細については、「 [DirectX 開発の概要](../native/directx-development-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-117">For details see [DirectX development overview](../native/directx-development-overview.md).</span></span> <span data-ttu-id="2ea0a-118">既存のアプリがなく、最初から開始する場合は、 [C++ holographic プロジェクトテンプレート](../native/creating-a-holographic-directx-project.md) を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-118">If you don't have an existing app and want to start from scratch the [C++ holographic project template](../native/creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="2ea0a-119">Holographic リモート処理を使用するすべてのアプリは、 [マルチスレッドアパートメント](/windows/win32/com/multithreaded-apartments)を使用するように作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-119">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](/windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="2ea0a-120">[シングルスレッドアパートメント](/windows/win32/com/single-threaded-apartments)の使用はサポートされていますが、パフォーマンスが低下し、再生中に途切れが生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-120">The use of a [single-threaded apartment](/windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="2ea0a-121">C++ を使用している場合、winrt [winrt:: init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) 、マルチスレッドアパートメントが既定値です。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-121">When using C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="2ea0a-122">Holographic リモート処理 NuGet パッケージを取得する</span><span class="sxs-lookup"><span data-stu-id="2ea0a-122">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="2ea0a-123">Visual Studio で NuGet パッケージをプロジェクトに追加するには、次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-123">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="2ea0a-124">Visual Studio でプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-124">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="2ea0a-125">プロジェクトノードを右クリックし、[ **NuGet パッケージの管理...** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-125">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="2ea0a-126">表示されるパネルで、[ **参照** ] を選択し、"Holographic Remoting" を検索します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-126">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="2ea0a-127">[ **Holographic**] を選択し、最新の2.x バージョンを選択して [**インストール**] を選択 **します。**</span><span class="sxs-lookup"><span data-stu-id="2ea0a-127">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="2ea0a-128">[ **プレビュー** ] ダイアログが表示されたら、[ **OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-128">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="2ea0a-129">[使用許諾契約書が表示されたら **同意** する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-129">Select **I Accept** when the license agreement dialog appears.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="2ea0a-130">```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet パッケージ内には、Holographic Remoting によって公開される API に関する詳細なドキュメントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-130">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="2ea0a-131">アプリケーションの package.appxmanifest を変更する</span><span class="sxs-lookup"><span data-stu-id="2ea0a-131">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="2ea0a-132">NuGet パッケージによって追加された Microsoft.Holographic.AppRemoting.dll をアプリケーションが認識できるようにするには、次の手順をプロジェクトで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-132">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="2ea0a-133">ソリューションエクスプローラーで **package.appxmanifest** ファイルを右クリックし、[**プログラムから開く**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-133">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="2ea0a-134">**XML (テキスト) エディター** を選択し、[ **OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-134">Select **XML (Text) Editor** and select **OK**</span></span>
3. <span data-ttu-id="2ea0a-135">次の行をファイルに追加して保存します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-135">Add the following lines to the file and save</span></span>
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a><span data-ttu-id="2ea0a-136">プレーヤーのコンテキストを作成する</span><span class="sxs-lookup"><span data-stu-id="2ea0a-136">Create the player context</span></span>

<span data-ttu-id="2ea0a-137">最初の手順として、アプリケーションでプレーヤーコンテキストを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-137">As a first step the application should create a player context.</span></span>

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
><span data-ttu-id="2ea0a-138">Holographic リモート処理は、Windows の一部である Windows Mixed Reality ランタイムをリモート処理固有のランタイムに置き換えることによって機能します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-138">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="2ea0a-139">これは、プレーヤーのコンテキストの作成時に実行されます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-139">This is done during the creation of the player context.</span></span> <span data-ttu-id="2ea0a-140">そのため、プレーヤーコンテキストを作成する前に Windows Mixed Reality API を呼び出すと、予期しない動作が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-140">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="2ea0a-141">推奨される方法は、任意の混合 Reality API と対話する前に、可能な限り早くプレーヤーコンテキストを作成することです。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-141">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="2ea0a-142">Windows Mixed Reality API を使用して作成または取得したオブジェクトを、 ```PlayerContext::Create``` 後で作成または取得したオブジェクトで混在させないでください。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-142">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="2ea0a-143">次に、 [HolographicSpace](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow)を呼び出して、HolographicSpace を作成します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-143">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](/uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a><span data-ttu-id="2ea0a-144">リモートアプリに接続する</span><span class="sxs-lookup"><span data-stu-id="2ea0a-144">Connect to the remote app</span></span>

<span data-ttu-id="2ea0a-145">プレーヤーアプリがコンテンツを表示できる状態になったら、リモートアプリへの接続を確立できます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-145">Once the player app is ready for rendering content a connection to the remote app can be established.</span></span>

<span data-ttu-id="2ea0a-146">接続は、次のいずれかの方法で確立できます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-146">The connection can be established in one of the following ways:</span></span>
1) <span data-ttu-id="2ea0a-147">HoloLens 2 で実行されているプレーヤーアプリは、リモートアプリに接続します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-147">The player app running on HoloLens 2 connects to the remote app.</span></span>
2) <span data-ttu-id="2ea0a-148">リモートアプリは、HoloLens 2 で実行されているプレーヤーアプリに接続します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-148">The remote app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="2ea0a-149">プレーヤーアプリからリモートアプリに接続するには、 ```Connect``` ホスト名とポートを指定して、プレーヤーのコンテキストでメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-149">To connect from the player app to the remote app call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="2ea0a-150">既定のポートは **8265** です。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-150">The default port is **8265**.</span></span>

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
><span data-ttu-id="2ea0a-151">C++/WinRT API と同様に、 ```Connect``` 処理する必要がある winrt:: hresult_error をスローすることがあります。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-151">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="2ea0a-152">プレーヤーアプリで着信接続をリッスンするには、メソッドを呼び出し ```Listen``` ます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-152">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="2ea0a-153">この呼び出しでは、ハンドシェイクポートとトランスポートポートの両方を指定できます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-153">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="2ea0a-154">ハンドシェイクポートは、初期ハンドシェイクに使用されます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-154">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="2ea0a-155">データは、トランスポートポートを介して送信されます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-155">The data is then sent over the transport port.</span></span> <span data-ttu-id="2ea0a-156">既定では、ポート番号 **8265** と **8266** が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-156">By default port number **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a><span data-ttu-id="2ea0a-157">接続関連のイベントの処理</span><span class="sxs-lookup"><span data-stu-id="2ea0a-157">Handling connection-related events</span></span>

<span data-ttu-id="2ea0a-158">は、 ```PlayerContext``` 接続の状態を監視するために3つのイベントを公開します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-158">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="2ea0a-159">OnConnected: リモートアプリへの接続が正常に確立されたときにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-159">OnConnected: Triggered when a connection to the remote app has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="2ea0a-160">OnDisconnected: 確立された接続が終了した場合、または接続が確立できなかった場合にトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-160">OnDisconnected: Triggered if an established connection is terminated or a connection couldn't be established.</span></span>
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
><span data-ttu-id="2ea0a-161">指定できる ```ConnectionFailureReason``` 値は、ファイルに記載されてい ```Microsoft.Holographic.AppRemoting.idl``` [](#idl)ます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-161">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="2ea0a-162">OnListening: 受信接続のリッスンが開始されます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-162">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="2ea0a-163">さらに、プレーヤーのコンテキストでプロパティを使用して接続状態を照会することもでき ```ConnectionState``` ます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-163">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="2ea0a-164">リモートで描画されたフレームを表示する</span><span class="sxs-lookup"><span data-stu-id="2ea0a-164">Display the remotely rendered frame</span></span>

<span data-ttu-id="2ea0a-165">リモートでレンダリングされるコンテンツを表示するには、 ```PlayerContext::BlitRemoteFrame``` [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe)のレンダリング中にを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-165">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame``` while rendering a [HolographicFrame](/uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="2ea0a-166">```BlitRemoteFrame``` 現在の HolographicFrame のバックバッファーがレンダーターゲットとしてバインドされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-166">```BlitRemoteFrame``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="2ea0a-167">バックバッファーは、 [Direct3D11BackBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer)プロパティを介して[HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters)から受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-167">The back buffer can be received from the [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="2ea0a-168">呼び出されると、 ```BlitRemoteFrame``` リモートアプリケーションから最後に受信したフレームを HolographicFrame の BackBuffer にコピーします。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-168">When called, ```BlitRemoteFrame``` copies the latest received frame from the remote application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="2ea0a-169">さらに、リモートアプリケーションがリモートフレームのレンダリング中にフォーカスポイントを指定している場合は、フォーカスポイントが設定されます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-169">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="2ea0a-170">```PlayerContext::BlitRemoteFrame``` 現在のフレームのフォーカスポイントを上書きする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-170">```PlayerContext::BlitRemoteFrame``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="2ea0a-171">フォールバックフォーカスポイントを指定するには、前に [HolographicCameraRenderingParameters:: SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) を呼び出し ```PlayerContext::BlitRemoteFrame``` ます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-171">To specify a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame```.</span></span> 
>- <span data-ttu-id="2ea0a-172">リモートフォーカスポイントを上書きするには、 [HolographicCameraRenderingParameters:: SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  を呼び出し ```PlayerContext::BlitRemoteFrame``` ます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-172">To overwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame```.</span></span>

<span data-ttu-id="2ea0a-173">成功した場合、は ```BlitRemoteFrame``` を返し ```BlitResult::Success_Color``` ます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-173">On success, ```BlitRemoteFrame``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="2ea0a-174">それ以外の場合は、エラーの理由を返します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-174">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="2ea0a-175">```BlitResult::Failed_NoRemoteFrameAvailable```: 使用可能なリモートフレームがないため、失敗しました。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-175">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="2ea0a-176">```BlitResult::Failed_NoCamera```: カメラが存在しないために失敗しました。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-176">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>
- <span data-ttu-id="2ea0a-177">```BlitResult::Failed_RemoteFrameTooOld```: リモートフレームが古すぎるため失敗しました (PlayerContext:: BlitRemoteFrameTimeout プロパティを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-177">```BlitResult::Failed_RemoteFrameTooOld```: Failed because remote frame is too old (see PlayerContext::BlitRemoteFrameTimeout property).</span></span>

>[!IMPORTANT]
> <span data-ttu-id="2ea0a-178">バージョン [2.1.0](holographic-remoting-version-history.md#v2.1.0) 以降では、カスタムプレーヤーが Holographic リモート処理を介して深さの再投影を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-178">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) it is possible with a custom player to use depth reprojection via Holographic Remoting.</span></span>

<span data-ttu-id="2ea0a-179">```BlitResult``` は ```BlitResult::Success_Color_Depth``` 、次の条件下でもを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-179">```BlitResult``` can also return ```BlitResult::Success_Color_Depth``` under the following conditions:</span></span>

- <span data-ttu-id="2ea0a-180">リモートアプリは、HolographicCameraRenderingParameters を使用して深度バッファーをコミットしました。 [CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-180">The remote app has committed a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>
- <span data-ttu-id="2ea0a-181">カスタムプレーヤーアプリは、を呼び出す前に有効な深度バッファーをバインドしました ```BlitRemoteFrame``` 。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-181">The custom player app has bound a valid depth buffer before calling ```BlitRemoteFrame```.</span></span>

<span data-ttu-id="2ea0a-182">これらの条件が満たされる ```BlitRemoteFrame``` と、リモートの深さが現在バインドされているローカルの深度バッファーに array.blit ます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-182">If these conditions are met ```BlitRemoteFrame``` will blit the remote depth into the currently bound local depth buffer.</span></span> <span data-ttu-id="2ea0a-183">その後、追加のローカルコンテンツをレンダリングできます。これには、リモートでレンダリングされるコンテンツとの深さの積集合があります。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-183">You can then render additional local content, which will have depth intersection with the remote rendered content.</span></span> <span data-ttu-id="2ea0a-184">さらに、カスタムプレーヤーで [HolographicCameraRenderingParameters](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) を使用してローカル深度バッファーをコミットし、リモートおよびローカルでレンダリングされるコンテンツの深さを再予測することもできます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-184">Additionally you can commit the local depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) in your custom player to have depth reprojection for remote and local rendered content.</span></span> <span data-ttu-id="2ea0a-185">詳細については、「 [深度 Reprojection](hologram-stability.md#reprojection) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-185">See [Depth Reprojection](hologram-stability.md#reprojection) for details.</span></span>

### <a name="projection-transform-mode"></a><span data-ttu-id="2ea0a-186">プロジェクション変換モード</span><span class="sxs-lookup"><span data-stu-id="2ea0a-186">Projection Transform Mode</span></span>

<span data-ttu-id="2ea0a-187">問題の1つは、Holographic リモート処理を使用して深さの reprojection を使用しているときに、カスタムプレーヤーアプリによって直接レンダリングされるローカルコンテンツとは別のプロジェクション変換を使用してリモートコンテンツをレンダリングできることです。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-187">One problem, which surfaces when using depth reprojection via Holographic Remoting is that the remote content can be rendered with a different projection transform than local content directly rendered by your custom player app.</span></span> <span data-ttu-id="2ea0a-188">一般的なユースケースでは、プレーヤー側とリモート側で ( [HolographicCamera:: SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) と [HolographicCamera:: SetFarPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)を使用して) 近距離および遠平面に対して異なる値を指定します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-188">A common use-case is to specify different values for near and far plane (via [HolographicCamera::SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) and [HolographicCamera::SetFarPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) on the player side and the remote side.</span></span> <span data-ttu-id="2ea0a-189">この場合、プレーヤー側の射影変換にリモートの近距離/遠距離またはローカルの距離が反映されているかどうかは明確ではありません。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-189">In this case, it's not clear if the projection transform on the player side should reflect the remote near/far plane distances or the local ones.</span></span>

<span data-ttu-id="2ea0a-190">バージョン [2.1.0](holographic-remoting-version-history.md#v2.1.0) 以降では、を使用して投影変換モードを制御でき ```PlayerContext::ProjectionTransformConfig``` ます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-190">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) you can control the projection transform mode via ```PlayerContext::ProjectionTransformConfig```.</span></span> <span data-ttu-id="2ea0a-191">サポートされる値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-191">Supported values are:</span></span>

- <span data-ttu-id="2ea0a-192">```Local``` - [HolographicCameraPose::P rojectiontransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) は、HolographicCamera 上のカスタムプレーヤーアプリによって設定された近距離/遠平面距離を反映する射影変換を返します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-192">```Local``` - [HolographicCameraPose::ProjectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) returns a projection transform, which reflects the near/far plane distances set by your custom player app on the HolographicCamera.</span></span>
- <span data-ttu-id="2ea0a-193">```Remote``` -射影変換は、リモートアプリによって指定された近距離距離と遠距離を反映します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-193">```Remote``` - Projection transform reflects the near/far plane distances specified by the remote app.</span></span>
- <span data-ttu-id="2ea0a-194">```Merged``` -リモートアプリとカスタムプレーヤーアプリとの間の距離が近い場合は、統合されます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-194">```Merged``` - Near/Far plane distances from your remote app and your custom player app are merged.</span></span> <span data-ttu-id="2ea0a-195">既定では、これを行うには、近距離距離の最小値と、遠くの平面距離の最大値を取得します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-195">By default this is done by taking the minimum of the near plane distances and the maximum of the far plane distances.</span></span> <span data-ttu-id="2ea0a-196">リモート側またはローカル側のどちらか一方が反転している場合は、遠く < 近くにあるとしても、遠くと遠くに離れた距離の距離が反転します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-196">In case either the remote or local side are inverted, say far < near, the remote near/far plane distances are flipped.</span></span>

## <a name="optional-set-blitremoteframetimeout"></a><span data-ttu-id="2ea0a-197">省略可能: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span><span class="sxs-lookup"><span data-stu-id="2ea0a-197">Optional: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span></span>
>[!IMPORTANT]
> <span data-ttu-id="2ea0a-198">```PlayerContext::BlitRemoteFrameTimeout``` は、バージョン [2.0.9](holographic-remoting-version-history.md#v2.0.9)以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-198">```PlayerContext::BlitRemoteFrameTimeout``` is supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 

<span data-ttu-id="2ea0a-199">プロパティは、 ```PlayerContext::BlitRemoteFrameTimeout``` 新しいリモートフレームが受信されなかった場合に、リモートフレームが再利用される時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-199">The ```PlayerContext::BlitRemoteFrameTimeout``` property specifies the amount of time a remote frame is reused if no new remote frame is received.</span></span> 

<span data-ttu-id="2ea0a-200">一般的なユースケースでは、一定の時間、新しいフレームが受信されなかった場合に、BlitRemoteFrame timeout で空の画面が表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-200">A common use-case is to enable the BlitRemoteFrame timeout to display a blank screen if no new frames are received for a certain amount of time.</span></span> <span data-ttu-id="2ea0a-201">有効にすると、メソッドの戻り値の型を使用して、 ```BlitRemoteFrame``` ローカルに表示されるフォールバックコンテンツに切り替えることもできます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-201">When enabled the return type of the ```BlitRemoteFrame``` method can also be used to switch to a locally rendered fallback content.</span></span> 

<span data-ttu-id="2ea0a-202">タイムアウトを有効にするには、プロパティ値を100ミリ秒以上の期間に設定します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-202">To enable the timeout, set the property value to a duration equal or greater than 100 ms.</span></span> <span data-ttu-id="2ea0a-203">タイムアウトを無効にするには、プロパティをゼロ期間に設定します。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-203">To disable the timeout, set the property to zero duration.</span></span> <span data-ttu-id="2ea0a-204">タイムアウトが有効になっていて、set duration のリモートフレームが受信されなかった場合、BlitRemoteFrame は失敗し、 ```Failed_RemoteFrameTooOld``` 新しいリモートフレームが受信されるまで戻ります。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-204">If the timeout is enabled and no remote frame is received for the set duration, BlitRemoteFrame will fail and return ```Failed_RemoteFrameTooOld``` until a new remote frame is received.</span></span>

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="2ea0a-205">省略可能: 最後のリモートフレームに関する統計を取得する</span><span class="sxs-lookup"><span data-stu-id="2ea0a-205">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="2ea0a-206">パフォーマンスまたはネットワークの問題を診断するために、プロパティを使用して最後のリモートフレームに関する統計を取得でき ```PlayerContext::LastFrameStatistics``` ます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-206">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="2ea0a-207">統計は [HolographicFrame::P](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction)の呼び出し中に更新されます。 current予測。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-207">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](/uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="2ea0a-208">詳細については、ファイルのドキュメントを参照してください ```PlayerFrameStatistics``` ```Microsoft.Holographic.AppRemoting.idl``` [](#idl)。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-208">For more information, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="2ea0a-209">省略可能: カスタムデータチャネル</span><span class="sxs-lookup"><span data-stu-id="2ea0a-209">Optional: Custom data channels</span></span>

<span data-ttu-id="2ea0a-210">カスタムデータチャネルは、既に確立されているリモート処理接続を介してユーザーデータを送信するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-210">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="2ea0a-211">詳細については、「 [カスタムデータチャネル](holographic-remoting-custom-data-channels.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2ea0a-211">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ea0a-212">参照</span><span class="sxs-lookup"><span data-stu-id="2ea0a-212">See Also</span></span>
* [<span data-ttu-id="2ea0a-213">Windows Mixed Reality Api を使用した Holographic リモート処理リモートアプリの作成</span><span class="sxs-lookup"><span data-stu-id="2ea0a-213">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="2ea0a-214">OpenXR Api を使用した Holographic リモート処理リモートアプリの作成</span><span class="sxs-lookup"><span data-stu-id="2ea0a-214">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="2ea0a-215">カスタムの Holographic Remoting データ チャネル</span><span class="sxs-lookup"><span data-stu-id="2ea0a-215">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="2ea0a-216">Holographic Remoting を使用したセキュリティで保護された接続の確立</span><span class="sxs-lookup"><span data-stu-id="2ea0a-216">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="2ea0a-217">Holographic リモート処理のトラブルシューティングと制限事項</span><span class="sxs-lookup"><span data-stu-id="2ea0a-217">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="2ea0a-218">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="2ea0a-218">Holographic Remoting software license terms</span></span>](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="2ea0a-219">Microsoft プライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="2ea0a-219">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)