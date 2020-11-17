---
title: Holographic リモート処理の追加
description: Holographic Remoting を使用してネットワーク経由で HoloLens にホログラムを表示する方法について説明します。
author: mikeriches
ms.author: mriches
ms.date: 05/24/2019
ms.topic: article
keywords: Windows Mixed Reality, ホログラム, holographic リモート処理, リモートレンダリング, ネットワークレンダリング, HoloLens, リモートホログラム, Mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: ec03a349959f9bde71a2c8a600d513fb21c533a8
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679631"
---
# <a name="add-holographic-remoting-hololens-1st-gen"></a><span data-ttu-id="7d002-104">Holographic リモート処理 (HoloLens (第1世代)) の追加</span><span class="sxs-lookup"><span data-stu-id="7d002-104">Add Holographic Remoting (HoloLens (1st gen))</span></span>

>[!IMPORTANT]
><span data-ttu-id="7d002-105">このドキュメントでは、HoloLens 1 用のホストアプリケーションの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d002-105">This document describes the creation of a host application for HoloLens 1.</span></span> <span data-ttu-id="7d002-106">HoloLens のホストアプリケーション **(第1世代)** では、NuGet **パッケージバージョン 1.x** を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d002-106">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="7d002-107">これは、HoloLens 1 用に作成されたホストアプリケーションが HoloLens 2 との互換性がないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="7d002-107">This implies that host applications written for HoloLens 1 are not compatible with HoloLens 2 and vice versa.</span></span>

## <a name="hololens-2"></a><span data-ttu-id="7d002-108">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="7d002-108">HoloLens 2</span></span>

<span data-ttu-id="7d002-109">Holographic リモート処理を使用する HoloLens 開発者は、HoloLens 2 との互換性を確保するためにアプリを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d002-109">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span> <span data-ttu-id="7d002-110">これには、新しいバージョンの Holographic リモート処理 NuGet パッケージが必要です。</span><span class="sxs-lookup"><span data-stu-id="7d002-110">This requires a new version of the Holographic Remoting NuGet package.</span></span> <span data-ttu-id="7d002-111">バージョン番号が2.0.0.0 より小さい Holographic リモート処理 NuGet パッケージを使用するアプリケーションが、HoloLens 2 の Holographic Remoting プレーヤーに接続しようとすると、接続は失敗します。</span><span class="sxs-lookup"><span data-stu-id="7d002-111">If an application using the Holographic Remoting NuGet package with a version number smaller than 2.0.0.0 attempts to connect to the Holographic Remoting Player on HoloLens 2, the connection will fail.</span></span>

>[!NOTE]
><span data-ttu-id="7d002-112">HoloLens 2 に固有のガイダンスについては、 [こちら](holographic-remoting-create-host.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d002-112">Guidance specific to HoloLens 2 can be found [here](holographic-remoting-create-host.md).</span></span>


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="7d002-113">Holographic remoting をデスクトップまたは UWP アプリに追加する</span><span class="sxs-lookup"><span data-stu-id="7d002-113">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="7d002-114">このページでは、Holographic リモート処理をデスクトップまたは UWP アプリに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7d002-114">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="7d002-115">Holographic remoting を使用すると、アプリはデスクトップ PC または Xbox One などの UWP デバイスでホストされている Holographic コンテンツを使用して HoloLens をターゲットにすることができます。これにより、より多くのシステムリソースへのアクセスが可能になり、リモートの [イマーシブビュー](../../design/app-views.md) を既存のデスクトップ PC ソフトウェアに統合できるようになります。</span><span class="sxs-lookup"><span data-stu-id="7d002-115">Holographic remoting allows your app to target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One, allowing access to more system resources and making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="7d002-116">リモート処理ホストアプリは、HoloLens から入力データストリームを受け取り、仮想イマーシブビューでコンテンツをレンダリングし、コンテンツフレームを HoloLens にストリームバックします。</span><span class="sxs-lookup"><span data-stu-id="7d002-116">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="7d002-117">接続は標準の Wi-fi を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="7d002-117">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="7d002-118">リモート処理を使用するには、NuGet パッケージを使用して、holographic リモート処理をデスクトップまたは UWP アプリに追加し、接続を処理し、イマーシブビューでレンダリングするコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="7d002-118">To use remoting, you will use a NuGet package to add holographic remoting to your desktop or UWP app, and write code to handle the connection and to render in an immersive view.</span></span> <span data-ttu-id="7d002-119">ヘルパーライブラリは、デバイス接続を処理するタスクを簡略化するコードサンプルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d002-119">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="7d002-120">一般的なリモート処理接続では、待機時間が50ミリ秒に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="7d002-120">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="7d002-121">プレーヤーアプリは、リアルタイムで待機時間を報告できます。</span><span class="sxs-lookup"><span data-stu-id="7d002-121">The player app can report the latency in real-time.</span></span>

>[!NOTE]
><span data-ttu-id="7d002-122">この記事のコードスニペットでは、 [C++ holographic プロジェクトテンプレート](../native/creating-a-holographic-directx-project.md)で使用される c + c++ 17 準拠の c++/WinRT ではなく、c++/cx の使用方法を現在説明しています。</span><span class="sxs-lookup"><span data-stu-id="7d002-122">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="7d002-123">概念は C++/WinRT プロジェクトに相当しますが、コードを変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d002-123">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="7d002-124">リモート処理 NuGet パッケージを取得する</span><span class="sxs-lookup"><span data-stu-id="7d002-124">Get the remoting NuGet packages</span></span>

<span data-ttu-id="7d002-125">次の手順に従って、holographic リモート処理用の NuGet パッケージを取得し、プロジェクトから参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="7d002-125">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="7d002-126">Visual Studio でプロジェクトにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="7d002-126">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="7d002-127">プロジェクトノードを右クリックし、[ **NuGet パッケージの管理...** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="7d002-127">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="7d002-128">表示されるパネルで、[ **参照** ] をクリックし、"Holographic Remoting" を検索します。</span><span class="sxs-lookup"><span data-stu-id="7d002-128">In the panel that appears, click **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="7d002-129">**Holographic** を選択し、[**インストール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d002-129">Select **Microsoft.Holographic.Remoting** and click **Install**.</span></span>
5. <span data-ttu-id="7d002-130">[ **プレビュー** ] ダイアログが表示されたら、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d002-130">If the **Preview** dialog appears, click **OK**.</span></span>
6. <span data-ttu-id="7d002-131">次に表示されるダイアログは、使用許諾契約書です。</span><span class="sxs-lookup"><span data-stu-id="7d002-131">The next dialog that appears is the license agreement.</span></span> <span data-ttu-id="7d002-132">[ **同意** する] をクリックして、使用許諾契約書に同意します。</span><span class="sxs-lookup"><span data-stu-id="7d002-132">Click on **I Accept** to accept the license agreement.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="7d002-133">HolographicStreamerHelpers を作成する</span><span class="sxs-lookup"><span data-stu-id="7d002-133">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="7d002-134">まず、HolographicStreamerHelpers のインスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="7d002-134">First, we need an instance of HolographicStreamerHelpers.</span></span> <span data-ttu-id="7d002-135">これをリモート処理を処理するクラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="7d002-135">Add this to the class that will be handling remoting.</span></span>

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="7d002-136">また、接続状態を追跡する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="7d002-136">You'll also need to track connection state.</span></span> <span data-ttu-id="7d002-137">プレビューを表示する場合は、コピー先のテクスチャを用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d002-137">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="7d002-138">また、接続状態のロック、HoloLens の IP アドレスを格納する方法など、いくつかの方法も必要です。</span><span class="sxs-lookup"><span data-stu-id="7d002-138">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

```cpp
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="7d002-139">HolographicStreamerHelpers を初期化して HoloLens に接続する</span><span class="sxs-lookup"><span data-stu-id="7d002-139">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="7d002-140">HoloLens デバイスに接続するには、HolographicStreamerHelpers のインスタンスを作成し、ターゲット IP アドレスに接続します。</span><span class="sxs-lookup"><span data-stu-id="7d002-140">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="7d002-141">Holographic リモート処理ライブラリでは、エンコーダーとデコーダーの解像度が正確に一致することを想定しているため、HoloLens の表示幅と高さに合わせてビデオフレームサイズを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d002-141">You will need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

```cpp
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

<span data-ttu-id="7d002-142">デバイス接続は非同期です。</span><span class="sxs-lookup"><span data-stu-id="7d002-142">The device connection is asynchronous.</span></span> <span data-ttu-id="7d002-143">アプリは、接続、切断、フレーム送信イベントのイベントハンドラーを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d002-143">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="7d002-144">OnConnected イベントは、UI を更新したり、レンダリングを開始したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="7d002-144">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="7d002-145">デスクトップのコードサンプルでは、"connected" メッセージを使用してウィンドウタイトルを更新します。</span><span class="sxs-lookup"><span data-stu-id="7d002-145">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="7d002-146">OnDisconnected イベントは、再接続や UI の更新などを処理できます。</span><span class="sxs-lookup"><span data-stu-id="7d002-146">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="7d002-147">この例では、一時的なエラーが発生した場合に再接続します。</span><span class="sxs-lookup"><span data-stu-id="7d002-147">In this example, we reconnect if there is a transient failure.</span></span>

```cpp
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

<span data-ttu-id="7d002-148">リモート処理コンポーネントがフレームを送信する準備ができたら、アプリは Sendframe イベントにそのコピーを作成する機会を提供します。</span><span class="sxs-lookup"><span data-stu-id="7d002-148">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="7d002-149">ここでは、プレビューウィンドウで表示できるように、フレームをスワップチェーンにコピーします。</span><span class="sxs-lookup"><span data-stu-id="7d002-149">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

```cpp
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a><span data-ttu-id="7d002-150">Holographic コンテンツのレンダリング</span><span class="sxs-lookup"><span data-stu-id="7d002-150">Render holographic content</span></span>

<span data-ttu-id="7d002-151">リモート処理を使用してコンテンツをレンダリングするには、デスクトップまたは UWP アプリ内に仮想 IFrameworkView を設定し、リモート処理から holographic フレームを処理します。</span><span class="sxs-lookup"><span data-stu-id="7d002-151">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="7d002-152">このビューでは、すべての Windows Holographic Api が同じ方法で使用されますが、設定は少し異なります。</span><span class="sxs-lookup"><span data-stu-id="7d002-152">All of the Windows Holographic APIs are uses the same way by this view, but it is set up slightly differently.</span></span>

<span data-ttu-id="7d002-153">自分で作成する代わりに、holographic space および speech コンポーネントは HolographicRemotingHelpers クラスから取得されます。</span><span class="sxs-lookup"><span data-stu-id="7d002-153">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="7d002-154">Run メソッド内で更新ループを使用する代わりに、デスクトップまたは UWP アプリのメインループからティックの更新を提供します。</span><span class="sxs-lookup"><span data-stu-id="7d002-154">Instead of using an update loop inside of a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="7d002-155">これにより、デスクトップや UWP アプリはメッセージ処理を制御できます。</span><span class="sxs-lookup"><span data-stu-id="7d002-155">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="7d002-156">Holographic app ビューの Tick () メソッドは、update、draw、present ループの1回の繰り返しを完了します。</span><span class="sxs-lookup"><span data-stu-id="7d002-156">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

```cpp
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

<span data-ttu-id="7d002-157">Holographic app view update、render、および present loop は、HoloLens で実行する場合とまったく同じです。ただし、デスクトップ PC 上のシステムリソースの量がはるかに多くなります。</span><span class="sxs-lookup"><span data-stu-id="7d002-157">The holographic app view update, render, and present loop is exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="7d002-158">多くの三角形をレンダリングしたり、描画パスを増やしたり、より多くの物理処理を行ったり、x64 プロセスを使用して 2 GB を超える RAM を必要とするコンテンツを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="7d002-158">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="7d002-159">リモートセッションを切断して終了する</span><span class="sxs-lookup"><span data-stu-id="7d002-159">Disconnect and end the remote session</span></span>

<span data-ttu-id="7d002-160">接続を切断する場合 (たとえば、ユーザーが UI ボタンをクリックして HolographicStreamerHelpers の切断 () を呼び出し、オブジェクトを解放する場合など)。</span><span class="sxs-lookup"><span data-stu-id="7d002-160">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

```cpp
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a><span data-ttu-id="7d002-161">リモート処理プレーヤーを取得する</span><span class="sxs-lookup"><span data-stu-id="7d002-161">Get the remoting player</span></span>

<span data-ttu-id="7d002-162">Windows Holographic リモート処理プレーヤーは、接続先のリモートホストアプリのエンドポイントとして Windows アプリストアで提供されます。</span><span class="sxs-lookup"><span data-stu-id="7d002-162">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="7d002-163">Windows Holographic リモート処理プレーヤーを入手するには、HoloLens から Windows アプリストアにアクセスし、リモート処理を検索して、アプリをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="7d002-163">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="7d002-164">リモート処理プレーヤーには、統計を画面に表示する機能が含まれています。これは、リモート処理ホストアプリをデバッグするときに便利です。</span><span class="sxs-lookup"><span data-stu-id="7d002-164">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="7d002-165">メモとリソース</span><span class="sxs-lookup"><span data-stu-id="7d002-165">Notes and resources</span></span>

<span data-ttu-id="7d002-166">Holographic app ビューでは、holographic space を初期化するために使用する必要がある Direct3D デバイスをアプリに提供する方法が必要になります。</span><span class="sxs-lookup"><span data-stu-id="7d002-166">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="7d002-167">アプリでプレビューフレームをコピーして表示するには、この Direct3D デバイスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d002-167">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="7d002-168">**コードサンプル:** 完全な Holographic Remoting コードサンプルが用意されています。これには、デスクトップ Win32、UWP DirectX、および XAML を使用した UWP 用のリモート処理ホストプロジェクトと互換性のある Holographic アプリケーションビューが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d002-168">**Code sample:** A complete Holographic Remoting code sample is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> <span data-ttu-id="7d002-169">取得するには、こちらを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d002-169">To get it, go here:</span></span>
* [<span data-ttu-id="7d002-170">リモート処理のための Windows Holographic のコードサンプル</span><span class="sxs-lookup"><span data-stu-id="7d002-170">Windows Holographic Code Sample for Remoting</span></span>](https://github.com/Microsoft/HoloLensCompanionKit/)

<span data-ttu-id="7d002-171">**デバッグに関する注意:** Holographic リモート処理ライブラリは、初回例外をスローできます。</span><span class="sxs-lookup"><span data-stu-id="7d002-171">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="7d002-172">これらの例外は、その時点でアクティブになっている Visual Studio の例外設定によっては、デバッグセッションで表示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="7d002-172">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="7d002-173">これらの例外は、Holographic リモート処理ライブラリによって内部的にキャッチされ、無視することができます。</span><span class="sxs-lookup"><span data-stu-id="7d002-173">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
