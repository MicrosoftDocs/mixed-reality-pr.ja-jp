---
title: Holographic リモート処理リモートアプリの作成 (WMR)
description: リモートコンピューター上にレンダリングされる Holographic リモート処理リモートアプリリモートコンテンツを HoloLens 2 にストリーミングできます。 この記事では、これを実現する方法について説明します。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、NuGet
ms.openlocfilehash: 3bbb75d9f1b6db64326f5b429103828266650a52
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96469513"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a>HolographicSpace API を使用した Holographic リモート処理リモートアプリの作成

>[!IMPORTANT]
>このドキュメントでは、 [HOLOGRAPHICSPACE API](../native/getting-a-holographicspace.md)を使用して HoloLens 2 用のリモートアプリケーションを作成する方法について説明します。 HoloLens のリモートアプリケーション **(第1世代)** では、NuGet **パッケージバージョン 1.x** を使用する必要があります。 これは、HoloLens 2 用に作成されたリモートアプリケーションが HoloLens 1 と互換性がないことを意味します。 HoloLens 1 のドキュメントについては、 [こちら](add-holographic-remoting.md)を参照してください。

Holographic リモート処理リモートアプリを作成することによって、リモートコンピューター上でレンダリングされるリモートコンテンツを HoloLens 2 にストリーミングし、Windows Mixed Reality ヘッドセットなどのイマーシブデバイスにストリーミングすることができます。 この記事では、これを実現する方法について説明します。 このページのすべてのコードと作業中のプロジェクトは、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)にあります。

Holographic リモート処理を使用すると、アプリは、デスクトップ PC または、Xbox One などの UWP デバイスでレンダリングされた Holographic コンテンツを使用して、HoloLens 2 および Windows Mixed Reality ヘッドセットを対象にすることができます。これにより、より多くのシステムリソースにアクセスでき、リモートの [イマーシブビュー](../../design/app-views.md) を既存のデスクトップ PC ソフトウェアに統合できます。 リモートアプリは HoloLens 2 から入力データストリームを受け取り、仮想イマーシブビューでコンテンツをレンダリングし、コンテンツフレームを HoloLens 2 にストリームバックします。 接続は標準の Wi-fi を使用して行われます。 Holographic リモート処理は、NuGet パケット経由でデスクトップまたは UWP アプリに追加されます。 接続を処理し、イマーシブビューでレンダリングする追加のコードが必要です。

一般的なリモート処理接続では、待機時間が50ミリ秒に抑えられます。 プレーヤーアプリは、リアルタイムで待機時間を報告できます。

## <a name="prerequisites"></a>前提条件

開始点としては、 [HOLOGRAPHICSPACE API](../native/getting-a-holographicspace.md)を対象とする、動作する DirectX ベースのデスクトップまたは UWP アプリを使用することをお勧めします。 詳細については、「 [DirectX 開発の概要](../native/directx-development-overview.md)」を参照してください。 [C++ holographic プロジェクトテンプレート](../native/creating-a-holographic-directx-project.md)は、出発点として適しています。

>[!IMPORTANT]
>Holographic リモート処理を使用するすべてのアプリは、 [マルチスレッドアパートメント](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)を使用するように作成する必要があります。 [シングルスレッドアパートメント](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments)の使用はサポートされていますが、パフォーマンスが低下し、再生中に途切れが生じる可能性があります。 C++ を使用している場合、winrt [winrt:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) 、マルチスレッドアパートメントが既定値です。



## <a name="get-the-holographic-remoting-nuget-package"></a>Holographic リモート処理 NuGet パッケージを取得する

Visual Studio で NuGet パッケージをプロジェクトに追加するには、次の手順を実行する必要があります。
1. Visual Studio でプロジェクトを開きます。
2. プロジェクトノードを右クリックし、[ **NuGet パッケージの管理...** ] を選択します。
3. 表示されるパネルで、[ **参照** ] をクリックし、"Holographic Remoting" を検索します。
4. [ **Holographic**] を選択し **、最新の** 2.x バージョンを選択して [ **インストール**] をクリックします。
5. [ **プレビュー** ] ダイアログが表示されたら、[ **OK**] をクリックします。
6. 次に表示されるダイアログは、使用許諾契約書です。 [ **同意** する] をクリックして、使用許諾契約書に同意します。

>[!NOTE]
>HoloLens 1 を対象とする開発者は、NuGet パッケージ **のバージョン 1.x** を引き続き利用できます。 詳細については、「 [Add Holographic Remoting (HoloLens (第1世代))](add-holographic-remoting.md)」を参照してください。

## <a name="create-the-remote-context"></a>リモートコンテキストを作成する

最初の手順として、アプリケーションでリモートコンテキストを作成する必要があります。

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
>Holographic リモート処理は、Windows の一部である Windows Mixed Reality ランタイムをリモート処理固有のランタイムに置き換えることによって機能します。 これは、リモートコンテキストの作成時に実行されます。 そのため、リモートコンテキストを作成する前に Windows Mixed Reality API を呼び出すと、予期しない動作が発生する可能性があります。 推奨される方法は、混合の現実 API と対話する前に、できるだけ早くリモートコンテキストを作成することです。 Windows Mixed Reality API を使用して作成または取得したオブジェクトを、後で作成または取得したオブジェクトと共に使用することは避けてください。

次に、holographic 領域を作成する必要があります。 CoreWindow の指定は必要ありません。 CoreWindow を持たないデスクトップアプリは、のみを渡すことができ ```nullptr``` ます。

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>デバイスへの接続

リモートアプリがコンテンツを表示できる状態になったら、プレーヤーデバイスへの接続を確立できます。

接続は、次の2つの方法のいずれかで実行できます。
1) リモートアプリは、デバイスで実行されているプレーヤーに接続します。
2) デバイスで実行されているプレーヤーは、リモートアプリに接続します。

リモートアプリからプレーヤーデバイスへの接続を確立するには、 ```Connect``` リモートコンテキストでホスト名とポートを指定してメソッドを呼び出します。 Holographic リモート処理プレーヤーによって使用されるポートは **8265** です。

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
>C++/WinRT API と同様に、 ```Connect``` 処理する必要がある winrt:: hresult_error をスローすることがあります。

>[!TIP]
>[C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/)言語のプロジェクションを使用しないようにするには、 ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` Holographic リモート処理 NuGet パッケージ内にあるファイルを含めることができます。 これには、基になる COM インターフェイスの宣言が含まれます。 ただし、C++/WinRT を使用することをお勧めします。

リモートアプリでの着信接続のリッスンは、メソッドを呼び出すことによって行うことができ ```Listen``` ます。 この呼び出しでは、ハンドシェイクポートとトランスポートポートの両方を指定できます。 ハンドシェイクポートは、初期ハンドシェイクに使用されます。 データは、トランスポートポートを介して送信されます。 既定では、 **8265** および **8266** が使用されます。

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
>```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl```NuGet パッケージ内には、Holographic Remoting によって公開される API に関する詳細なドキュメントが含まれています。

## <a name="handling-remoting-specific-events"></a>リモート処理固有のイベントの処理

リモートコンテキストは、接続の状態を監視するために重要な3つのイベントを公開します。
1) OnConnected: デバイスへの接続が正常に確立されたときにトリガーされます。
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) OnDisconnected: 確立された接続が閉じられた場合、または接続を確立できなかった場合にトリガーされます。
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
3) OnListening: 受信接続のリッスンが開始されます。
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

さらに、リモートコンテキストのプロパティを使用して接続状態を照会することもでき ```ConnectionState``` ます。
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>音声イベントの処理

リモート音声インターフェイスを使用すると、音声トリガーを HoloLens 2 に登録し、リモートアプリケーションにリモート処理することができます。

この追加のメンバーは、リモート音声の状態を追跡するために必要です。

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

まず、リモート音声インターフェイスを取得する必要があります。

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

非同期ヘルパーメソッドを使用すると、リモート音声を初期化できます。 初期化にはかなりの時間がかかる場合があるため、非同期的に実行する必要があります。 C++ での[同時実行と非同期操作](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency)c++/winrtで非同期関数を作成する方法について説明します。

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

認識する語句を指定する方法は2つあります。
1) 音声文法 xml ファイル内の仕様。 詳細について [は、「基本的な XML 文法を作成する方法](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) 」を参照してください。
2) を指定するには、をディクショナリベクター内に渡し ```ApplyParameters``` ます。

On認識された音声コールバック内で、音声イベントを処理できます。

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

## <a name="preview-streamed-content-locally"></a>ストリーミングされるコンテンツをローカルでプレビューする

デバイスに送信されるリモートアプリで同じコンテンツを表示するには、 ```OnSendFrame``` リモートコンテキストのイベントを使用できます。 ```OnSendFrame```イベントは、Holographic リモート処理ライブラリが現在のフレームをリモートデバイスに送信するたびにトリガーされます。 これは、コンテンツを撮影し、デスクトップや UWP ウィンドウに array.blit するのに最適な時間です。

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

## <a name="depth-reprojection"></a>深さの再投影

バージョン [2.1.0](holographic-remoting-version-history.md#v2.1.0)以降では、Holographic Remoting は [深さの reprojection](hologram-stability.md#reprojection)をサポートしています。 そのためには、カラーバッファーに加えて、リモートアプリケーションから HoloLens 2 に深度バッファーをストリーム転送する必要があります。 既定では、深度バッファーストリーミングが有効になり、カラーバッファーの半分の解像度を使用するように構成されます。 これは、次のように変更できます。

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

```ConfigureDepthVideoStream```HoloLens 2 への接続を確立する前に、既定値を使用しないようにする必要があることに注意してください。 最適な場所は、リモートコンテキストを作成した直後です。 DepthBufferStreamResolution に指定できる値は次のとおりです。

* Full_Resolution
* Half_Resolution
* Quarter_Resolution
* 無効 (バージョン [2.1.3](holographic-remoting-version-history.md#v2.1.3) を使用して追加され、追加の深度ビデオストリームが作成されない場合)

完全な解像度の深度バッファーを使用することは、帯域幅の要件にも影響し、指定した最大帯域幅の値について考慮する必要があることに注意してください ```CreateRemoteContext``` 。

解決を構成すると、HolographicCameraRenderingParameters を使用して深度バッファーをコミットする必要もあります [。 CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_)を使用します。

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

HoloLens 2 で深度の再プロジェクションが正しく動作しているかどうかを確認するには、デバイスポータルを使用して深度ビジュアライザーを有効にします。 詳細については、「 [奥行が正しく設定されている](hologram-stability.md#verifying-depth-is-set-correctly) ことを確認しています

## <a name="optional-custom-data-channels"></a>省略可能: カスタムデータチャネル

カスタムデータチャネルは、既に確立されているリモート処理接続を介してユーザーデータを送信するために使用できます。 詳細については、「 [カスタムデータチャネル](holographic-remoting-custom-data-channels.md) 」を参照してください。

## <a name="see-also"></a>参照
* [カスタム Holographic リモート処理プレーヤーアプリの作成](holographic-remoting-create-player.md)
* [カスタムの Holographic Remoting データ チャネル](holographic-remoting-custom-data-channels.md)
* [Holographic Remoting を使用したセキュリティで保護された接続の確立](holographic-remoting-secure-connection.md)
* [Holographic リモート処理のトラブルシューティングと制限事項](holographic-remoting-troubleshooting.md)
* [Holographic Remoting ソフトウェア ライセンス条項](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
