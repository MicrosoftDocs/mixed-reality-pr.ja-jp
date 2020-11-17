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
# <a name="add-holographic-remoting-hololens-1st-gen"></a>Holographic リモート処理 (HoloLens (第1世代)) の追加

>[!IMPORTANT]
>このドキュメントでは、HoloLens 1 用のホストアプリケーションの作成について説明します。 HoloLens のホストアプリケーション **(第1世代)** では、NuGet **パッケージバージョン 1.x** を使用する必要があります。 これは、HoloLens 1 用に作成されたホストアプリケーションが HoloLens 2 との互換性がないことを意味します。

## <a name="hololens-2"></a>HoloLens 2

Holographic リモート処理を使用する HoloLens 開発者は、HoloLens 2 との互換性を確保するためにアプリを更新する必要があります。 これには、新しいバージョンの Holographic リモート処理 NuGet パッケージが必要です。 バージョン番号が2.0.0.0 より小さい Holographic リモート処理 NuGet パッケージを使用するアプリケーションが、HoloLens 2 の Holographic Remoting プレーヤーに接続しようとすると、接続は失敗します。

>[!NOTE]
>HoloLens 2 に固有のガイダンスについては、 [こちら](holographic-remoting-create-host.md)を参照してください。


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Holographic remoting をデスクトップまたは UWP アプリに追加する

このページでは、Holographic リモート処理をデスクトップまたは UWP アプリに追加する方法について説明します。

Holographic remoting を使用すると、アプリはデスクトップ PC または Xbox One などの UWP デバイスでホストされている Holographic コンテンツを使用して HoloLens をターゲットにすることができます。これにより、より多くのシステムリソースへのアクセスが可能になり、リモートの [イマーシブビュー](../../design/app-views.md) を既存のデスクトップ PC ソフトウェアに統合できるようになります。 リモート処理ホストアプリは、HoloLens から入力データストリームを受け取り、仮想イマーシブビューでコンテンツをレンダリングし、コンテンツフレームを HoloLens にストリームバックします。 接続は標準の Wi-fi を使用して行われます。 リモート処理を使用するには、NuGet パッケージを使用して、holographic リモート処理をデスクトップまたは UWP アプリに追加し、接続を処理し、イマーシブビューでレンダリングするコードを記述します。 ヘルパーライブラリは、デバイス接続を処理するタスクを簡略化するコードサンプルに含まれています。

一般的なリモート処理接続では、待機時間が50ミリ秒に抑えられます。 プレーヤーアプリは、リアルタイムで待機時間を報告できます。

>[!NOTE]
>この記事のコードスニペットでは、 [C++ holographic プロジェクトテンプレート](../native/creating-a-holographic-directx-project.md)で使用される c + c++ 17 準拠の c++/WinRT ではなく、c++/cx の使用方法を現在説明しています。  概念は C++/WinRT プロジェクトに相当しますが、コードを変換する必要があります。

### <a name="get-the-remoting-nuget-packages"></a>リモート処理 NuGet パッケージを取得する

次の手順に従って、holographic リモート処理用の NuGet パッケージを取得し、プロジェクトから参照を追加します。
1. Visual Studio でプロジェクトにアクセスします。
2. プロジェクトノードを右クリックし、[ **NuGet パッケージの管理...** ] を選択します。
3. 表示されるパネルで、[ **参照** ] をクリックし、"Holographic Remoting" を検索します。
4. **Holographic** を選択し、[**インストール**] をクリックします。
5. [ **プレビュー** ] ダイアログが表示されたら、[ **OK**] をクリックします。
6. 次に表示されるダイアログは、使用許諾契約書です。 [ **同意** する] をクリックして、使用許諾契約書に同意します。

### <a name="create-the-holographicstreamerhelpers"></a>HolographicStreamerHelpers を作成する

まず、HolographicStreamerHelpers のインスタンスが必要です。 これをリモート処理を処理するクラスに追加します。

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

また、接続状態を追跡する必要もあります。 プレビューを表示する場合は、コピー先のテクスチャを用意する必要があります。 また、接続状態のロック、HoloLens の IP アドレスを格納する方法など、いくつかの方法も必要です。

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>HolographicStreamerHelpers を初期化して HoloLens に接続する

HoloLens デバイスに接続するには、HolographicStreamerHelpers のインスタンスを作成し、ターゲット IP アドレスに接続します。 Holographic リモート処理ライブラリでは、エンコーダーとデコーダーの解像度が正確に一致することを想定しているため、HoloLens の表示幅と高さに合わせてビデオフレームサイズを設定する必要があります。

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

デバイス接続は非同期です。 アプリは、接続、切断、フレーム送信イベントのイベントハンドラーを提供する必要があります。

OnConnected イベントは、UI を更新したり、レンダリングを開始したりすることができます。 デスクトップのコードサンプルでは、"connected" メッセージを使用してウィンドウタイトルを更新します。

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

OnDisconnected イベントは、再接続や UI の更新などを処理できます。 この例では、一時的なエラーが発生した場合に再接続します。

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

リモート処理コンポーネントがフレームを送信する準備ができたら、アプリは Sendframe イベントにそのコピーを作成する機会を提供します。 ここでは、プレビューウィンドウで表示できるように、フレームをスワップチェーンにコピーします。

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

### <a name="render-holographic-content"></a>Holographic コンテンツのレンダリング

リモート処理を使用してコンテンツをレンダリングするには、デスクトップまたは UWP アプリ内に仮想 IFrameworkView を設定し、リモート処理から holographic フレームを処理します。 このビューでは、すべての Windows Holographic Api が同じ方法で使用されますが、設定は少し異なります。

自分で作成する代わりに、holographic space および speech コンポーネントは HolographicRemotingHelpers クラスから取得されます。

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Run メソッド内で更新ループを使用する代わりに、デスクトップまたは UWP アプリのメインループからティックの更新を提供します。 これにより、デスクトップや UWP アプリはメッセージ処理を制御できます。

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

Holographic app ビューの Tick () メソッドは、update、draw、present ループの1回の繰り返しを完了します。

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

Holographic app view update、render、および present loop は、HoloLens で実行する場合とまったく同じです。ただし、デスクトップ PC 上のシステムリソースの量がはるかに多くなります。 多くの三角形をレンダリングしたり、描画パスを増やしたり、より多くの物理処理を行ったり、x64 プロセスを使用して 2 GB を超える RAM を必要とするコンテンツを読み込むことができます。

### <a name="disconnect-and-end-the-remote-session"></a>リモートセッションを切断して終了する

接続を切断する場合 (たとえば、ユーザーが UI ボタンをクリックして HolographicStreamerHelpers の切断 () を呼び出し、オブジェクトを解放する場合など)。

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

## <a name="get-the-remoting-player"></a>リモート処理プレーヤーを取得する

Windows Holographic リモート処理プレーヤーは、接続先のリモートホストアプリのエンドポイントとして Windows アプリストアで提供されます。 Windows Holographic リモート処理プレーヤーを入手するには、HoloLens から Windows アプリストアにアクセスし、リモート処理を検索して、アプリをダウンロードします。 リモート処理プレーヤーには、統計を画面に表示する機能が含まれています。これは、リモート処理ホストアプリをデバッグするときに便利です。

## <a name="notes-and-resources"></a>メモとリソース

Holographic app ビューでは、holographic space を初期化するために使用する必要がある Direct3D デバイスをアプリに提供する方法が必要になります。 アプリでプレビューフレームをコピーして表示するには、この Direct3D デバイスを使用する必要があります。

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**コードサンプル:** 完全な Holographic Remoting コードサンプルが用意されています。これには、デスクトップ Win32、UWP DirectX、および XAML を使用した UWP 用のリモート処理ホストプロジェクトと互換性のある Holographic アプリケーションビューが含まれています。 取得するには、こちらを参照してください。
* [リモート処理のための Windows Holographic のコードサンプル](https://github.com/Microsoft/HoloLensCompanionKit/)

**デバッグに関する注意:** Holographic リモート処理ライブラリは、初回例外をスローできます。 これらの例外は、その時点でアクティブになっている Visual Studio の例外設定によっては、デバッグセッションで表示される場合があります。 これらの例外は、Holographic リモート処理ライブラリによって内部的にキャッチされ、無視することができます。
