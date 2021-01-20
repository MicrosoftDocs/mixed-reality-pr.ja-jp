---
title: カスタムの Holographic Remoting データ チャネル
description: カスタムデータチャネルは、既に確立されている Holographic リモート処理接続を介してユーザーデータを送信するために使用できます。
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens、リモート処理、Holographic リモート処理、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実のヘッドセット、データチャネル
ms.openlocfilehash: a11fe0bb023ae34692015585f6e1689db4330ac7
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582611"
---
# <a name="custom-holographic-remoting-data-channels"></a><span data-ttu-id="5d156-104">カスタムの Holographic Remoting データ チャネル</span><span class="sxs-lookup"><span data-stu-id="5d156-104">Custom Holographic Remoting data channels</span></span>

>[!NOTE]
><span data-ttu-id="5d156-105">このガイダンスは、HoloLens 2 の Holographic リモート処理に固有のものです。</span><span class="sxs-lookup"><span data-stu-id="5d156-105">This guidance is specific to Holographic Remoting on HoloLens 2.</span></span>

<span data-ttu-id="5d156-106">カスタムデータチャネルを使用して、確立されたリモート処理接続を介してカスタムデータを送信します。</span><span class="sxs-lookup"><span data-stu-id="5d156-106">Use custom data channels to send custom data over an established remoting connection.</span></span>

>[!IMPORTANT]
><span data-ttu-id="5d156-107">カスタムデータチャネルでは、カスタムのリモートアプリとカスタムプレーヤーアプリが必要です。これは、2つのカスタムアプリ間の通信を可能にするためです。</span><span class="sxs-lookup"><span data-stu-id="5d156-107">Custom data channels require a custom remote app and a custom player app, as it allows for communication between the two custom apps.</span></span>

>[!TIP]
><span data-ttu-id="5d156-108">単純なピンポン方の例については、 [Holographic リモート処理サンプル github リポジトリ](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)内の remote および player サンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5d156-108">A simple ping-pong example can be found in the remote and player samples inside the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span> <span data-ttu-id="5d156-109">```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE```SampleRemoteMain/SamplePlayerMain ファイル内のコメントを解除して、サンプルコードを有効にします。</span><span class="sxs-lookup"><span data-stu-id="5d156-109">Uncomment ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` inside the SampleRemoteMain.h / SamplePlayerMain.h files to enable the sample code.</span></span>


## <a name="create-a-custom-data-channel"></a><span data-ttu-id="5d156-110">カスタムデータチャネルを作成する</span><span class="sxs-lookup"><span data-stu-id="5d156-110">Create a custom data channel</span></span>


<span data-ttu-id="5d156-111">カスタムデータチャネルを作成するには、次のフィールドが必要です。</span><span class="sxs-lookup"><span data-stu-id="5d156-111">To create a custom data channel, the following fields are required:</span></span>
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

<span data-ttu-id="5d156-112">接続が正常に確立されると、リモート側、プレーヤー側、またはその両方から新しいデータチャネルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="5d156-112">After a connection is successfully established, you can create new data channels from either the remote side, the player side, or both.</span></span> <span data-ttu-id="5d156-113">RemoteContext と PlayerContext はどちらも、 ```CreateDataChannel()``` データチャネルを作成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5d156-113">Both the RemoteContext and the PlayerContext provide a ```CreateDataChannel()``` method for creating data channels.</span></span> <span data-ttu-id="5d156-114">最初のパラメーターはチャネル ID で、後続の操作でデータチャネルを識別するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5d156-114">The first parameter is the channel ID, which is used to identify the data channel in subsequent operations.</span></span> <span data-ttu-id="5d156-115">2番目のパラメーターは、このチャネルのデータを相手側に転送する優先度を指定する優先順位です。</span><span class="sxs-lookup"><span data-stu-id="5d156-115">The second parameter is the priority, which specifies the priority with which data of this channel is transferred to the other side.</span></span> <span data-ttu-id="5d156-116">リモート側で有効なチャネル Id は、0から63までの有効なチャネル Id と、プレーヤー側の127までの64を含みます。</span><span class="sxs-lookup"><span data-stu-id="5d156-116">Valid channel IDs on the remote side are from 0 up to and including 63, and 64 up to and including 127 for the player side.</span></span> <span data-ttu-id="5d156-117">有効な優先順位は ```Low``` 、、 ```Medium``` 、または ```High``` (両側) です。</span><span class="sxs-lookup"><span data-stu-id="5d156-117">Valid priorities are ```Low```, ```Medium```, or ```High``` (on both sides).</span></span>

<span data-ttu-id="5d156-118">**リモート** 側でデータチャネルの作成を開始するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="5d156-118">To start the creation of a data channel on the **remote** side:</span></span>
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

<span data-ttu-id="5d156-119">**プレーヤー** 側でデータチャネルの作成を開始するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="5d156-119">To start the creation of a data channel on the **player** side:</span></span>
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
><span data-ttu-id="5d156-120">新しいカスタムデータチャネルを作成するには、1つの側 (リモートまたはプレーヤー) だけがメソッドを呼び出す必要があり ```CreateDataChannel``` ます。</span><span class="sxs-lookup"><span data-stu-id="5d156-120">To create a new custom data channel, only one side (either remote or player) needs to call the ```CreateDataChannel``` method.</span></span>

## <a name="handling-custom-data-channel-events"></a><span data-ttu-id="5d156-121">カスタムデータチャネルイベントの処理</span><span class="sxs-lookup"><span data-stu-id="5d156-121">Handling custom data channel events</span></span>

<span data-ttu-id="5d156-122">カスタムデータチャネルを確立するには、 ```OnDataChannelCreated``` (プレーヤーとリモート側の両方で) イベントを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d156-122">To establish a custom data channel, the ```OnDataChannelCreated``` event needs to be handled (on both the player and the remote side).</span></span> <span data-ttu-id="5d156-123">このメソッドは、ユーザーデータチャネルがいずれかの側で作成され、 ```IDataChannel``` このチャネルを介してデータを送受信するために使用できるオブジェクトを提供するときにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="5d156-123">It triggers when a user data channel has been created by either side and provides a ```IDataChannel``` object, which can be used to send and receive data over this channel.</span></span>

<span data-ttu-id="5d156-124">イベントにリスナーを登録するには、次のようにし ```OnDataChannelCreated``` ます。</span><span class="sxs-lookup"><span data-stu-id="5d156-124">To register a listener on the ```OnDataChannelCreated``` event:</span></span>
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

<span data-ttu-id="5d156-125">データを受信したときに通知を受け取るには、 ```OnDataReceived``` ```IDataChannel``` ハンドラーによって提供されるオブジェクトのイベントに登録し ```OnDataChannelCreated``` ます。</span><span class="sxs-lookup"><span data-stu-id="5d156-125">To get notified when data is received, register to the ```OnDataReceived``` event on the ```IDataChannel``` object provided by the ```OnDataChannelCreated``` handler.</span></span> <span data-ttu-id="5d156-126">```OnClosed```データチャネルが閉じられたときに通知を受け取るには、イベントに登録します。</span><span class="sxs-lookup"><span data-stu-id="5d156-126">Register to the ```OnClosed``` event, to get notified when the data channel has been closed.</span></span>

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

## <a name="sending-data"></a><span data-ttu-id="5d156-127">データの送信</span><span class="sxs-lookup"><span data-stu-id="5d156-127">Sending data</span></span>

<span data-ttu-id="5d156-128">カスタムデータチャネルを介してデータを送信するには、メソッドを使用し ```IDataChannel::SendData()``` ます。</span><span class="sxs-lookup"><span data-stu-id="5d156-128">To send data over a custom data channel, use the ```IDataChannel::SendData()``` method.</span></span> <span data-ttu-id="5d156-129">最初のパラメーターは、 ```winrt::array_view<const uint8_t>``` 送信する必要があるデータのです。</span><span class="sxs-lookup"><span data-stu-id="5d156-129">The first parameter is a ```winrt::array_view<const uint8_t>``` to the data that should be send.</span></span> <span data-ttu-id="5d156-130">2番目のパラメーターは、もう一方の側が受信を承認するまで、データを再送信する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="5d156-130">The second parameter specifies where the data should be resend, until the other side acknowledge the reception.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="5d156-131">ネットワークの状態が正しくない場合は、同じデータパケットが複数回到着する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5d156-131">In case of bad network conditions, the same data packet might arrive more than once.</span></span> <span data-ttu-id="5d156-132">受信コードでは、この状況に対処できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d156-132">The receiving code must be able to handle this situation.</span></span>

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a><span data-ttu-id="5d156-133">カスタムデータチャネルを閉じる</span><span class="sxs-lookup"><span data-stu-id="5d156-133">Closing a custom data channel</span></span>

<span data-ttu-id="5d156-134">カスタムデータチャネルを閉じるには、メソッドを使用し ```IDataChannel::Close()``` ます。</span><span class="sxs-lookup"><span data-stu-id="5d156-134">To close a custom data channel, use the ```IDataChannel::Close()``` method.</span></span> <span data-ttu-id="5d156-135">カスタムデータチャネルが閉じられると、イベントによって両方の側に通知され ```OnClosed``` ます。</span><span class="sxs-lookup"><span data-stu-id="5d156-135">Both sides will be notified by the ```OnClosed``` event once the custom data channel has been closed.</span></span>

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a><span data-ttu-id="5d156-136">参照</span><span class="sxs-lookup"><span data-stu-id="5d156-136">See Also</span></span>
* [<span data-ttu-id="5d156-137">Windows Mixed Reality Api を使用した Holographic リモート処理リモートアプリの作成</span><span class="sxs-lookup"><span data-stu-id="5d156-137">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="5d156-138">OpenXR Api を使用した Holographic リモート処理リモートアプリの作成</span><span class="sxs-lookup"><span data-stu-id="5d156-138">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="5d156-139">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="5d156-139">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="5d156-140">Holographic リモート処理のトラブルシューティングと制限事項</span><span class="sxs-lookup"><span data-stu-id="5d156-140">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="5d156-141">Holographic Remoting ソフトウェア ライセンス条項</span><span class="sxs-lookup"><span data-stu-id="5d156-141">Holographic Remoting software license terms</span></span>](//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="5d156-142">Microsoft プライバシーに関する声明</span><span class="sxs-lookup"><span data-stu-id="5d156-142">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)