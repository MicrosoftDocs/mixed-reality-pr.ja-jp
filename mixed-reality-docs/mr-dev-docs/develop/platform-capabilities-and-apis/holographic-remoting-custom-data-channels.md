---
title: カスタムの Holographic Remoting データ チャネル
description: カスタムデータチャネルは、既に確立されている Holographic リモート処理接続を介してユーザーデータを送信するために使用できます。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実のヘッドセット、データチャネル
ms.openlocfilehash: 119a08a7f0e41aca694184879e33aaf54160220c
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443449"
---
# <a name="custom-holographic-remoting-data-channels"></a>カスタムの Holographic Remoting データ チャネル

>[!NOTE]
>このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。

カスタムデータチャネルを使用して、確立されたリモート処理接続を介してカスタムデータを送信します。

>[!IMPORTANT]
>カスタムデータチャネルでは、カスタムのリモートアプリとカスタムプレーヤーアプリが必要です。これは、2つのカスタムアプリ間の通信を可能にするためです。

>[!TIP]
>単純なピンポン方の例については、 [Holographic リモート処理サンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)内の remote および player サンプルを参照してください。 ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE```SampleRemoteMain/SamplePlayerMain ファイル内のコメントを解除して、サンプルコードを有効にします。


## <a name="create-a-custom-data-channel"></a>カスタムデータチャネルを作成する


カスタムデータチャネルを作成するには、次のフィールドが必要です。
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

接続が正常に確立されると、新しいデータチャネルの作成は、リモート側とプレーヤー側のどちらからでも開始できます。 RemoteContext と PlayerContext はどちらも、 ```CreateDataChannel()``` これを行うための方法を提供します。 最初のパラメーターはチャネル ID で、後続の操作でデータチャネルを識別するために使用されます。 2番目のパラメーターは、このチャネルのデータを相手側に転送する優先度を指定する優先順位です。 チャネル Id の有効な範囲は、リモート64側の場合は63、プレーヤー側の場合は127を含む0になります。 有効な優先順位は ```Low``` 、、 ```Medium``` または ```High``` (両側) です。

**リモート** 側でデータチャネルの作成を開始するには、次のようにします。
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

**プレーヤー** 側でデータチャネルの作成を開始するには、次のようにします。
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>新しいカスタムデータチャネルを作成するには、1つの側 (リモートまたはプレーヤー) だけがメソッドを呼び出す必要があり ```CreateDataChannel``` ます。

## <a name="handling-custom-data-channel-events"></a>カスタムデータチャネルイベントの処理

カスタムデータチャネルを確立するには、 ```OnDataChannelCreated``` (プレーヤーとリモート側の両方で) イベントを処理する必要があります。 このメソッドは、ユーザーデータチャネルがいずれかの側で作成され、 ```IDataChannel``` このチャネルを介してデータを送受信するために使用できるオブジェクトを提供するときにトリガーされます。

イベントにリスナーを登録するには、次のようにし ```OnDataChannelCreated``` ます。
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

データを受信したときに通知を受け取るには、 ```OnDataReceived``` ```IDataChannel``` ハンドラーによって提供されるオブジェクトのイベントに登録し ```OnDataChannelCreated``` ます。 ```OnClosed```データチャネルが閉じられたときに通知を受け取るには、イベントに登録します。

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a>データの送信

カスタムデータチャネルを介してデータを送信するには、メソッドを使用し ```IDataChannel::SendData()``` ます。 最初のパラメーターは、 ```winrt::array_view<const uint8_t>``` 送信する必要があるデータのです。 2番目のパラメーターは、もう一方の側が受信を承認するまで、データを再送信する場所を指定します。 

>[!IMPORTANT]
>ネットワークの状態が正しくない場合は、同じデータパケットが複数回到着する可能性があります。 受信コードでは、この状況に対処できる必要があります。

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>カスタムデータチャネルを閉じる

カスタムデータチャネルを閉じるには、メソッドを使用し ```IDataChannel::Close()``` ます。 カスタムデータチャネルが閉じられると、イベントによって両方の側に通知され ```OnClosed``` ます。

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>参照
* [Windows Mixed Realiy Api を使用した Holographic リモート処理リモートアプリの作成](holographic-remoting-create-remote-wmr.md)
* [OpenXR Api を使用した Holographic リモート処理リモートアプリの作成](holographic-remoting-create-remote-openxr.md)
* [カスタム Holographic リモート処理プレーヤーアプリの作成](holographic-remoting-create-player.md)
* [Holographic リモート処理のトラブルシューティングと制限事項](holographic-remoting-troubleshooting.md)
* [Holographic Remoting ソフトウェア ライセンス条項](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Microsoft プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=521839)
