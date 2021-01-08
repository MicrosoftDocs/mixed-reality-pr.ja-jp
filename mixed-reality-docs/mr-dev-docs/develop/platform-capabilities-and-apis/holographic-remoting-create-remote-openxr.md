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
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>OpenXR API を使用した Holographic リモート処理リモートアプリの作成

>[!IMPORTANT]
>このドキュメントでは、 [OPENXR API](../native/openxr.md)を使用して HoloLens 2 および Windows Mixed Reality ヘッドセット用のリモートアプリケーションを作成する方法について説明します。 HoloLens のリモートアプリケーション **(第1世代)** では、NuGet **パッケージバージョン 1.x** を使用する必要があります。 これは、HoloLens 2 用に作成されたリモートアプリケーションが HoloLens 1 と互換性がないことを意味します。 HoloLens 1 のドキュメントについては、 [こちら](add-holographic-remoting.md)を参照してください。

Holographic リモート処理アプリを使用すると、リモートでレンダリングされたコンテンツを HoloLens 2 および Windows Mixed Reality のイマーシブヘッドセットにストリーミングできます。 また、より多くのシステムリソースにアクセスしたり、既存のデスクトップ PC ソフトウェアにリモートの [イマーシブビュー](../../design/app-views.md) を統合したりすることもできます。 リモートアプリは HoloLens 2 から入力データストリームを受け取り、仮想イマーシブビューでコンテンツをレンダリングし、コンテンツフレームを HoloLens 2 にストリームバックします。 接続は標準の Wi-fi を使用して行われます。 Holographic リモート処理は、NuGet パケット経由でデスクトップまたは UWP アプリに追加されます。 接続を処理し、イマーシブビューでレンダリングする追加のコードが必要です。 一般的なリモート処理接続では、待機時間が50ミリ秒に抑えられます。 プレーヤーアプリは、リアルタイムで待機時間を報告できます。

このページのすべてのコードと作業中のプロジェクトは、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)にあります。

## <a name="prerequisites"></a>前提条件

開始点としては、OpenXR ベースのデスクトップまたは UWP アプリを使用することをお勧めします。 詳細については、「 [OpenXR の概要](../native/openxr-getting-started.md)」を参照してください。

>[!IMPORTANT]
>Holographic リモート処理を使用するすべてのアプリは、 [マルチスレッドアパートメント](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)を使用するように作成する必要があります。 [シングルスレッドアパートメント](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments)の使用はサポートされていますが、パフォーマンスが低下し、再生中に途切れが生じる可能性があります。 C++ を使用している場合、winrt [winrt:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) 、マルチスレッドアパートメントが既定値です。

## <a name="get-the-holographic-remoting-nuget-package"></a>Holographic リモート処理 NuGet パッケージを取得する

Visual Studio で NuGet パッケージをプロジェクトに追加するには、次の手順を実行する必要があります。
1. Visual Studio でプロジェクトを開きます。
2. プロジェクトノードを右クリックし、[ **NuGet パッケージの管理...** ] を選択します。
3. 表示されるパネルで、[ **参照** ] を選択し、"Holographic Remoting" を検索します。
4. [ **Holographic**] を選択して **、最新の** 2.x バージョンを選択し、[ **インストール**] を選択します。
5. [ **プレビュー** ] ダイアログが表示されたら、[ **OK]** を選択します。
6. [使用許諾契約書] ダイアログボックスが表示されたら、[ **同意** する] を選択します。
7. 次の NuGet パッケージに対して手順 3. ~ 6. を繰り返します: OpenXR、OpenXR

>[!NOTE]
>HoloLens 1 を対象とする開発者は、NuGet パッケージ **のバージョン 1.x** を引き続き利用できます。 詳細については、「 [Add Holographic Remoting (HoloLens (第1世代))](add-holographic-remoting.md)」を参照してください。

## <a name="select-the-holographic-remoting-openxr-runtime"></a>Holographic Remoting OpenXR ランタイムを選択します。

リモートアプリで行う必要がある最初の手順は、Holographic NuGet パッケージの一部である Holographic Remoting OpenXR runtime を選択することです。 これを行うには、 ```XR_RUNTIME_JSON``` 環境変数を、アプリ内のファイルの RemotingXR.jsのパスに設定します。 この環境変数は、システムの既定の OpenXR ランタイムを使用せずに、代わりに Holographic Remoting OpenXR runtime にリダイレクトするために OpenXR ローダーによって使用されます。 OpenXr NuGet パッケージを使用する場合、ファイルの RemotingXR.jsは、コンパイル時に出力フォルダーに自動的にコピーされます。 OpenXR ランタイムの選択は、通常、次のようになります。

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

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>Holographic Remoting 拡張機能を使用して XrInstance を作成する

一般的な OpenXR アプリの最初の手順は、OpenXR extensions を選択して XrInstance を作成することです。 OpenXR core 仕様では、リモート処理固有の API は提供されません。 そのため、Holographic Remoting では、という名前の独自の OpenXR 拡張機能が導入さ ```XR_MSFT_holographic_remoting``` れています。 XrCreateInstance を呼び出したときに、 ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` が XrInstanceCreateInfo に含まれていることを確認します。

>[!TIP]
>既定では、アプリのレンダリングされたコンテンツは、HoloLens 2 または Windows Mixed Reality ヘッドセットで実行されている Holographic リモート処理プレーヤーにのみストリーミングされます。 また、レンダリングされたコンテンツをリモート PC に表示するために、ウィンドウのスワップチェーンを使用して、Holographic リモート処理には、という名前の2つ目の OpenXR 拡張機能が用意されて ```XR_MSFT_holographic_remoting_frame_mirroring``` います。 また、この機能を使用する場合は、を使用してこの拡張機能を有効にし ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` ます。

>[!IMPORTANT]
>Holographic Remoting OpenXR extension API の詳細については、 [Holographic リモート処理のサンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)に記載されている[仕様](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html)を確認してください。

## <a name="connect-to-the-device"></a>デバイスへの接続

リモートアプリによって XrInstance が作成され、xrGetSystem 経由で XrSystemId に照会された後、プレーヤーデバイスへの接続を確立できます。

>[!WARNING]
> Holographic Remoting OpenXR ランタイムは、接続が確立された後に、ビュー構成や環境 blend モードなどのデバイス固有のデータのみを提供できます。 ```xrEnumerateViewConfigurations```、 ```xrEnumerateViewConfigurationViews``` 、 ```xrGetViewConfigurationProperties``` 、 ```xrEnumerateEnvironmentBlendModes``` 、およびで ```xrGetSystemProperties``` は、既定値が使用されます。これは通常、HoloLens 2 で実行されているプレーヤーに接続してから完全に接続する場合に使用するものと一致します。
接続が確立される前に、これらのメソッドを呼び出さないことを強くお勧めします。 提案は、XrSession が正常に作成され、セッション状態が少なくとも XR_SESSION_STATE_READY になった後に、これらのメソッドで使用されます。

最大ビットレート、オーディオ対応、ビデオコーデック、深度バッファーストリーム解像度などの一般的なプロパティは、次のようにを使用して構成でき ```xrRemotingSetContextPropertiesMSFT``` ます。

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

接続は、次の2つの方法のいずれかで実行できます。
1) リモートアプリは、デバイスで実行されているプレーヤーに接続します。
2) デバイスで実行されているプレーヤーは、リモートアプリに接続します。

リモートアプリからプレーヤーデバイスへの接続を確立するには、 ```xrRemotingConnectMSFT``` 構造体を介してホスト名とポートを指定するメソッドを呼び出し  ```XrRemotingConnectInfoMSFT``` ます。 Holographic リモート処理プレーヤーによって使用されるポートは **8265** です。

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

リモートアプリでの着信接続のリッスンは、メソッドを呼び出すことによって行うことができ ```xrRemotingListenMSFT``` ます。 ハンドシェイクポートとトランスポートポートの両方を構造体を使用して指定でき ```XrRemotingListenInfoMSFT``` ます。 ハンドシェイクポートは、初期ハンドシェイクに使用されます。 データは、トランスポートポートを介して送信されます。 既定では、 **8265** および **8266** が使用されます。

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

またはを呼び出すと、接続状態が切断される必要があり ```xrRemotingConnectMSFT``` ```xrRemotingListenMSFT``` ます。 XrInstance を作成し、経由で XrSystemId に対してクエリを実行した後、いつでも接続状態を取得でき ```xrRemotingGetConnectionStateMSFT``` ます。

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

使用できる接続状態は次のとおりです。
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``````xrRemotingListenMSFT```xrCreateSession を介して XrSession を作成する前に、またはを呼び出す必要があります。 接続状態がのときに XrSession を作成しようとすると、 ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` セッションの作成は成功しますが、セッションの状態は直ちに XR_SESSION_STATE_LOSS_PENDING に移行されます。

Holographic リモート処理の実装では ```xrCreateSession``` 、接続が確立されるのを待機できます。 またはを呼び出して、を呼び出すことができ ```xrRemotingConnectMSFT``` ```xrRemotingListenMSFT``` ます。この呼び出しはブロックされ、接続が確立されるまで待機します。 タイムアウトは10秒に固定されています。 この時間内に接続を確立できる場合、XrSession の作成は成功し、セッションの状態は XR_SESSION_STATE_READY に移行されます。 接続を確立できない場合は、セッションの作成も成功しますが、直ちに XR_SESSION_STATE_LOSS_PENDING に移行されます。

一般に、接続状態は XrSession 状態になります。 接続状態の変更は、セッションの状態にも影響します。 たとえば、接続状態をからに切り替えた場合、 `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` セッション状態は XR_SESSION_STATE_LOSS_PENDING にも移行します。

## <a name="handling-remoting-specific-events"></a>リモート処理固有のイベントの処理

Holographic Remoting OpenXR runtime は、接続の状態を監視するために重要な3つのイベントを公開します。
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: デバイスへの接続が正常に確立されたときにトリガーされます。
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: 確立された接続が閉じられた場合、または接続が確立できなかった場合にトリガーされます。
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: 受信接続のリッスンが開始されたとき。

これらのイベントはキューに配置され、リモートアプリは定期的 via を使用してキューから読み取る必要があり ```xrPollEvent``` ます。

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

## <a name="preview-streamed-content-locally"></a>ストリーミングされるコンテンツをローカルでプレビューする

デバイスに送信されたのと同じコンテンツをリモートアプリで表示するには、 ```XR_MSFT_holographic_remoting_frame_mirroring``` 拡張機能を使用できます。 この拡張機能では、次のように、XrFrameEndInfo にチェーンされていないを使用して、xrEndFrame にテクスチャを送信でき ```XrRemotingFrameMirrorImageInfoMSFT``` ます。

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

上の例では、DX11 のスワップチェーンテクスチャを使用して、xrEndFrame の呼び出しの直後にウィンドウを表示します。 使用量はスワップチェーンテクスチャに限定されておらず、追加の GPU 同期は必要ありません。 使用法と制約の詳細については、 [拡張機能の仕様](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring)を確認してください。
リモートアプリで DX12 を使用している場合は、XrRemotingFrameMirrorImageD3D11MSFT ではなく XrRemotingFrameMirrorImageD3D12MSFT を使用します。

## <a name="see-also"></a>参照
* [カスタム Holographic リモート処理プレーヤーアプリの作成](holographic-remoting-create-player.md)
* [Holographic Remoting を使用したセキュリティで保護された接続の確立](holographic-remoting-secure-connection.md)
* [Holographic リモート処理のトラブルシューティングと制限事項](holographic-remoting-troubleshooting.md)
* [Holographic Remoting ソフトウェア ライセンス条項](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
