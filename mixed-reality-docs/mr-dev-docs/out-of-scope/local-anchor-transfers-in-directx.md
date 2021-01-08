---
title: DirectX でのローカルアンカー転送
description: 空間アンカーを転送、エクスポート、およびシリアル化することで、2つの HoloLens デバイスを同期する方法について説明します。
author: mikeriches
ms.author: mriches
ms.date: 03/21/2018
ms.topic: article
keywords: HoloLens, 同期, 空間アンカー, 転送, マルチプレイヤー, ビュー, シナリオ, チュートリアル, サンプルコード, 転送, ローカルアンカー転送, アンカーエクスポート, アンカーインポート
ms.openlocfilehash: 5007220f480a3093864502e624737e9707bd3952
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009652"
---
# <a name="local-anchor-transfers-in-directx"></a>DirectX でのローカルアンカー転送

<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>を使用できない場合、ローカルアンカー転送では、1つの hololens デバイスが2つ目の hololens デバイスによってインポートされるアンカーをエクスポートできるようにします。

>[!NOTE]
>ローカルアンカー転送は、 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>よりも堅牢なアンカーの再呼び出しを提供します。この方法では、iOS デバイスと Android デバイスはサポートされていません。

>[!NOTE]
>この記事のコードスニペットでは、 [C++ holographic プロジェクトテンプレート](../develop/native/creating-a-holographic-directx-project.md)で使用される c + c++ 17 準拠の c++/WinRT ではなく、c++/cx の使用方法を現在説明しています。  概念は C++/WinRT プロジェクトに相当しますが、コードを変換する必要があります。

## <a name="transferring-spatial-anchors"></a>空間アンカーの転送

[SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)を使用して、Windows Mixed Reality デバイス間で空間アンカーを転送できます。 この API を使用すると、世界中の正確な場所を特定し、そのバンドルを別のデバイスにインポートするために必要なすべてのサポートセンサーデータを使用してアンカーをまとめることができます。 2番目のデバイス上のアプリがアンカーをインポートすると、各アプリは、その共有空間アンカーの座標系を使用してホログラムをレンダリングできます。これは、実際の世界の同じ場所に表示されます。

空間アンカーは異なる種類のデバイス間では転送できないことに注意してください。たとえば、1つの HoloLens 空間アンカーは、イマーシブヘッドセットを使用して指定することはできません。  転送されたアンカーは、iOS または Android デバイスとも互換性がありません。

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a>SpatialPerception 機能を使用するようにアプリを設定する

[SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)を使用するには、アプリに SpatialPerception 機能を使用するためのアクセス許可が付与されている必要があります。 これは、空間アンカーを転送する場合に必要です。これは、そのアンカーの近くで、時間の経過と共に収集されるセンサーイメージを共有することです。

この機能をアプリの package.appxmanifest ファイルで宣言します。 次に例を示します。

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

この機能は、 **uap2** 名前空間から取得されます。 マニフェスト内のこの名前空間へのアクセスを取得するには、パッケージの> 要素に *xlmns* 属性として含め &lt; ます。 次に例を示します。

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

**注:** SpatialAnchor export/import Api にアクセスするには、アプリが実行時に機能を要求する必要があります。 次の例の [Requestaccessasync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) を参照してください。

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a>SpatialAnchorTransferManager を使用してエクスポートすることによってアンカーデータをシリアル化する

ヘルパー関数は、 [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) データをエクスポート (シリアル化) するためのコードサンプルに含まれています。 この export API は、文字列をアンカーに関連付けるキーと値のペアのコレクション内のすべてのアンカーをシリアル化します。

```
// ExportAnchorDataAsync: Exports a byte buffer containing all of the anchors in the given collection.
//
// This function will place data in a buffer using a std::vector<byte>. The ata buffer contains one or more
// Anchors if one or more Anchors were successfully imported; otherwise, it is ot modified.
//
task<bool> SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
    vector<byte>* anchorByteDataOut,
    IMap<String^, SpatialAnchor^>^ anchorsToExport
    )
{
```

まず、データストリームを設定する必要があります。 これにより、1を使用できるようになります)。TryExportAnchorsAsync を使用して、アプリによって所有されているバッファーにデータを配置します。 2.)エクスポートされたバイトバッファーストリームからデータを読み取ります。これは、WinRT データストリームで、独自のメモリバッファー (std:: vector byte>) に格納され &lt; ます。

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

空間データ (システムによってエクスポートされたアンカーを含む) にアクセスする権限を要求する必要があります。

```
// Request access to spatial data.
auto accessRequestedTask = create_taskSpatialAnchorTransferManager::RequestAccessAsync()).then([anchorsToExport, utputStream](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
        // Export the indicated set of anchors.
        return create_task(SpatialAnchorTransferManager::TryExportAnchorsAsync(
            anchorsToExport,
            outputStream
            ));
    }
    else
    {
        // Access is denied.
        return task_from_result<bool>(false);
    }
});
```

Get アクセス許可とアンカーがエクスポートされた場合は、データストリームを読み取ることができます。 ここでは、データの読み取りに使用する DataReader と InputStream を作成する方法についても説明します。

```
// Get the input stream for the anchor byte stream.
IInputStream^ inputStream = stream->GetInputStreamAt(0);
// Create a DataReader, to get bytes from the anchor byte stream.
DataReader^ reader = ref new DataReader(inputStream);
return accessRequestedTask.then([anchorByteDataOut, stream, reader](bool nchorsExported)
{
    if (anchorsExported)
    {
        // Get the size of the exported anchor byte stream.
        size_t bufferSize = static_cast<size_t>(stream->Size);
        // Resize the output buffer to accept the data from the stream.
        anchorByteDataOut->reserve(bufferSize);
        anchorByteDataOut->resize(bufferSize);
        // Read the exported anchor store into the stream.
        return create_task(reader->LoadAsync(bufferSize));
    }
    else
    {
        return task_from_result<size_t>(0);
    }
```

ストリームからバイトを読み取った後は、そのようなデータを独自のデータバッファーに保存することができます。

```
}).then([anchorByteDataOut, reader](size_t bytesRead)
{
    if (bytesRead > 0)
    {
        // Read the bytes from the stream, into our data output buffer.
        reader->ReadBytes(Platform::ArrayReference<byte>(&(*anchorByteDataOut)[0], bytesRead));
        return true;
    }
    else
    {
        return false;
    }
});
};
```

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a>SpatialAnchorTransferManager を使用してシステムにインポートすることでアンカーデータを逆シリアル化する

前にエクスポートしたデータを読み込むためのコードサンプルには、ヘルパー関数が含まれています。 この逆シリアル化関数は、SpatialAnchorStore が提供するものと同様に、キーと値のペアのコレクションを提供します。ただし、このデータを別のソース (ネットワークソケットなど) から受け取った場合を除きます。 このデータは、オフラインで、アプリ内メモリを使用して、または (該当する場合は) アプリの SpatialAnchorStore を使用して、オフラインで保存する前に処理および理由を確認できます。

```
// ImportAnchorDataAsync: Imports anchors from a byte buffer that was previously exported.
//
// This function will import all anchors from a data buffer into an in-memory ollection of key, value
// pairs that maps String objects to SpatialAnchor objects. The Spatial nchorStore is not affected by
// this function unless you provide it as the target collection for import.
//
task<bool> SpatialAnchorImportExportHelper::ImportAnchorDataAsync(
    std::vector<byte>& anchorByteDataIn,
    IMap<String^, SpatialAnchor^>^ anchorMapOut
    )
{
```

まず、アンカーデータにアクセスするためのストリームオブジェクトを作成する必要があります。 ここでは、バッファーからシステムバッファーにデータを書き込みます。そのため、SpatialAnchors としてバイトバッファーからシステムにアンカーを取得するという目標を達成するために、インメモリデータストリームに書き込む DataWriter を作成します。

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

ここでも、空間アンカーデータをエクスポートするアクセス許可がアプリに付与されていることを確認する必要があります。これには、ユーザーの環境に関する個人情報が含まれる可能性があります。

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

アクセスが許可されている場合は、バッファーからシステムデータストリームにバイトを書き込むことができます。

```
// Write the bytes to the stream.
        byte* anchorDataFirst = &anchorByteDataIn[0];
        size_t anchorDataSize = anchorByteDataIn.size();
        writer->WriteBytes(Platform::ArrayReference<byte>(anchorDataFirst, anchorDataSize));
        // Store the stream.
        return create_task(writer->StoreAsync());
    }
    else
    {
        // Access is denied.
        return task_from_result<size_t>(0);
    }
```

データストリームへのバイトの格納に成功した場合は、SpatialAnchorTransferManager を使用してそのデータをインポートできます。

```
}).then([writer, stream](unsigned int bytesWritten)
{
    if (bytesWritten > 0)
    {
        // Try to import anchors from the byte stream.
        return create_task(writer->FlushAsync())
            .then([stream](bool dataWasFlushed)
        {
            if (dataWasFlushed)
            {
                // Get the input stream for the anchor data.
                IInputStream^ inputStream = stream->GetInputStreamAt(0);
                return create_task(SpatialAnchorTransferManager::TryImportAnchorsAsync(inputStream));
            }
            else
            {
                return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
            }
        });
    }
    else
    {
        return task_from_result<IMapView<String^, SpatialAnchor^>^>(nullptr);
    }
```

データをインポートできる場合は、文字列をアンカーに関連付けるキーと値のペアのマップビューが表示されます。 これを独自のメモリ内データコレクションに読み込んで、そのコレクションを使用して、興味のあるアンカーを探すことができます。

```
}).then([anchorMapOut](task<Windows::Foundation::Collections::IMapView<String^, SpatialAnchor^>^>  previousTask)
{
    try
    {
        auto importedAnchorsMap = previousTask.get();
        // If the operation was successful, we get a set of imported anchors.
        if (importedAnchorsMap != nullptr)
        {
            for each (auto& pair in importedAnchorsMap)
            {
                // Note that you could look for specific anchors here, if you know their key values.
                auto const& id = pair->Key;
                auto const& anchor = pair->Value;
                // Append "Remote" to the end of the anchor name for disambiguation.
                std::wstring idRemote(id->Data());
                idRemote += L"Remote";
                String^ idRemoteConst = ref new String (idRemote.c_str());
                // Store the anchor in the current in-memory anchor map.
                anchorMapOut->Insert(idRemoteConst, anchor);
            }
            return true;
        }
    }
    catch (Exception^ exception)
    {
        OutputDebugString(L"Error: Unable to import the anchor data buffer bytes into the in-memory anchor collection.\n");
    }
    return false;
});
}
```

**注:** アンカーをインポートできるだけなので、すぐに使用できるとは限りません。 アンカーは、別の部屋、または物理的に別の場所にある場合があります。アンカーは、そのデバイスを受信したデバイスに、アンカーが作成された環境についての十分な視覚的情報があることを確認します。これにより、既知の現在の環境を基準としてアンカーの位置を復元できます。 クライアントの実装では、実際のコンテンツに使用する前に、ローカルの座標系または参照フレームに対してアンカーの位置を特定する必要があります。 たとえば、アンカーが特定可能になるまで、現在の座標系を基準としてアンカーを定期的に検索してみてください。

## <a name="special-considerations"></a>特別な考慮事項

[TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API を使用すると、複数の[SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)を同じ不透明なバイナリ blob にエクスポートできます。 ただし、単一の SpatialAnchor または複数の SpatialAnchors が1回の呼び出しでエクスポートされるかどうかによって、blob に含まれるデータには微妙な違いがあります。

### <a name="export-of-a-single-spatialanchor"></a>1つの SpatialAnchor のエクスポート

Blob には、SpatialAnchor をインポートするデバイスで環境を認識できるように、SpatialAnchor の近傍に環境の表現が含まれています。 インポートが完了すると、新しい SpatialAnchor がデバイスで使用できるようになります。 ユーザーが最近アンカーの近くにいたことを前提として、SpatialAnchor にアタッチされているホログラムをレンダリングできます。 これらのホログラムは、SpatialAnchor をエクスポートした元のデバイスで行ったのと同じ物理的な場所に表示されます。

![1つの SpatialAnchor のエクスポート](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a>複数の SpatialAnchors のエクスポート

1つの SpatialAnchor のエクスポートと同様に、blob には、指定されたすべての SpatialAnchors の近接部分にある環境の表現が含まれます。 また、blob には、含まれている SpatialAnchors との間の接続に関する情報が含まれています (同じ物理領域に存在する場合)。 これは、隣接する2つの SpatialAnchors がインポートされた場合、2つの SpatialAnchors 間の変換を計算するのに十分なデータが blob に含まれていたため、2 *番目* の SpatialAnchor にアタッチされたホログラムが、デバイスが *最初* の SpatialAnchor の周囲の環境を認識している場合でも、このようになります。 2つの SpatialAnchors が個別にエクスポートされた場合 (TryExportSpatialAnchors の2つの個別の呼び出し)、最初の SpatialAnchor に接続されている、2番目のにアタッチされているホログラムの blob に十分なデータが含まれていない可能性があります。

![1つの TryExportAnchorsAsync 呼び出しを使用してエクスポートされた複数のアンカー](images/multipleanchors.png) ![アンカーごとに個別の TryExportAnchorsAsync 呼び出しを使用してエクスポートされた複数のアンカー](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a>例: Windows:: Network:: StreamSocket を使用してアンカーデータを送信する

ここでは、エクスポートされたアンカーデータを TCP ネットワーク経由で送信することによって使用する方法の例を示します。 これは、HolographicSpatialAnchorTransferSample からのものです。

WinRT StreamSocket クラスは、PPL タスクライブラリを使用します。 ネットワークエラーが発生した場合、再スローされた例外を使用して、チェーン内の次のタスクにエラーが返されます。 例外には、エラーの状態を示す HRESULT が含まれています。

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a>Windows:: Network:: StreamSocketListener と TCP を使用して、エクスポートされたアンカーデータを送信する

接続をリッスンするサーバーインスタンスを作成します。

```
void SampleAnchorTcpServer::ListenForConnection()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocketListener^ streamSocketListener = m_socketServer;
    if (streamSocketListener == nullptr)
    {
        OutputDebugString(L"Server listening for client.\n");
        // Create the web socket connection.
        streamSocketListener = ref new StreamSocketListener();
        streamSocketListener->Control->KeepAlive = true;
        streamSocketListener->BindEndpointAsync(
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        streamSocketListener->ConnectionReceived +=
            ref new Windows::Foundation::TypedEventHandler<StreamSocketListener^, StreamSocketListenerConnectionReceivedEventArgs^>(
                std::bind(&SampleAnchorTcpServer::OnConnectionReceived, this, _1, _2)
                );
        m_socketServer = streamSocketListener;
    }
    else
    {
        OutputDebugString(L"Error: Stream socket listener not created.\n");
    }
}
```

接続を受信したら、クライアントソケット接続を使用してアンカーデータを送信します。

```
void SampleAnchorTcpServer::OnConnectionReceived(StreamSocketListener^ listener, StreamSocketListenerConnectionReceivedEventArgs^ args)
{
    m_socketForClient = args->Socket;
    if (m_socketForClient != nullptr)
    {
        // In this example, when the client first connects, we catch it up to the current state of our anchor set.
        OutputToClientSocket(m_spatialAnchorHelper->GetAnchorMap());
    }
}
```

ここで、エクスポートしたアンカーデータを含むデータストリームの送信を開始できます。

```
void SampleAnchorTcpServer::OutputToClientSocket(IMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    m_anchorTcpSocketStreamWriter = ref new DataWriter(m_socketForClient->OutputStream);
    OutputDebugString(L"Sending stream to client.\n");
    SendAnchorDataStream(anchorsToSend).then([this](task<bool> previousTask)
    {
        try
        {
            bool success = previousTask.get();
            if (success)
            {
                OutputDebugString(L"Anchor data sent!\n");
            }
            else
            {
                OutputDebugString(L"Error: Anchor data not sent.\n");
            }
        }
        catch (Exception^ exception)
        {
            HandleException(exception);
            OutputDebugString(L"Error: Anchor data was not sent.\n");
        }
    });
}
```

ストリーム自体を送信する前に、まずヘッダーパケットを送信する必要があります。 このヘッダーパケットは固定長である必要があり、また、アンカーデータストリームであるバイトの変数配列の長さも示す必要があります。この例では、送信するヘッダーデータが他にないため、ヘッダーは長さが4バイトで、32ビットの符号なし整数が含まれています。

```
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataLengthMessage(size_t dataStreamLength)
{
    unsigned int arrayLength = dataStreamLength;
    byte* data = reinterpret_cast<byte*>(&arrayLength);
    m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    return create_task(m_anchorTcpSocketStreamWriter->StoreAsync()).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            OutputDebugString(L"Anchor data length stored in stream; Flushing stream.\n");
            return create_task(m_anchorTcpSocketStreamWriter->FlushAsync());
        }
        else
        {
            OutputDebugString(L"Error: Anchor data length not stored in stream.\n");
            return task_from_result<bool>(false);
        }
    });
}
Concurrency::task<bool> SampleAnchorTcpServer::SendAnchorDataStreamIMap<String^, SpatialAnchor^>^ anchorsToSend)
{
    return SpatialAnchorImportExportHelper::ExportAnchorDataAsync(
        &m_exportedAnchorStoreBytes,
        anchorsToSend
        ).then([this](bool anchorDataExported)
    {
        if (anchorDataExported)
        {
            const size_t arrayLength = m_exportedAnchorStoreBytes.size();
            if (arrayLength > 0)
            {
                OutputDebugString(L"Anchor data was exported; sending data stream length message.\n");
                return SendAnchorDataLengthMessage(arrayLength);
            }
        }
        OutputDebugString(L"Error: Anchor data was not exported.\n");
        // No data to send.
        return task_from_result<bool>(false);
```

ストリームの長さ (バイト単位) がクライアントに送信されると、データストリーム自体をソケットストリームに書き込むことができます。 これにより、アンカーストアのバイトがクライアントに送信されます。

```
}).then([this](bool dataLengthSent)
    {
        if (dataLengthSent)
        {
            OutputDebugString(L"Data stream length message sent; writing exported anchor store bytes to stream.\n");
            m_anchorTcpSocketStreamWriter->WriteBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0], m_exportedAnchorStoreBytes.size()));
            return create_task(m_anchorTcpSocketStreamWriter->StoreAsync());
        }
        else
        {
            OutputDebugString(L"Error: Data stream length message not sent.\n");
            return task_from_result<size_t>(0);
        }
    }).then([this](unsigned int bytesStored)
    {
        if (bytesStored > 0)
        {
            PrintWstringToDebugConsole(
                std::to_wstring(bytesStored) +
                L" bytes of anchor data written and stored to stream; flushing stream.\n"
                );
        }
        else
        {
            OutputDebugString(L"Error: No anchor data bytes were written to the stream.\n");
        }
        return task_from_result<bool>(false);
    });
}
```

このトピックで既に説明したように、ネットワークエラーステータスメッセージを含む例外を処理できるように準備する必要があります。 予期しないエラーの場合は、などのように、デバッグコンソールに例外情報を書き込むことができます。 これにより、コードサンプルが接続を完了できない場合、またはアンカーデータの送信を完了できない場合に何が起こったかについての手掛かりが得られます。

```
void SampleAnchorTcpServer::HandleException(Exception^ exception)
{
    PrintWstringToDebugConsole(
        std::wstring(L"Connection error: ") +
        exception->ToString()->Data() +
        L"\n"
        );
}
```

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a>Windows:: Network:: StreamSocket と TCP を使用して、エクスポートされたアンカーデータを受信する

まず、サーバーに接続する必要があります。 このコードサンプルでは、StreamSocket を作成して構成する方法と、ソケット接続を使用してネットワークデータを取得するために使用できる DataReader を作成する方法を示します。

**注:** このサンプルコードを実行する場合は、クライアントを起動する前にサーバーを構成して起動していることを確認してください。

```
task<bool> SampleAnchorTcpClient::ConnectToServer()
{
    // Make a local copy to avoid races with Closed events.
    StreamSocket^ streamSocket = m_socketClient;
    // Have we connected yet?
    if (m_socketClient == nullptr)
    {
        OutputDebugString(L"Client is attempting to connect to server.\n");
        EndpointPair^ endpointPair = ref new EndpointPair(
            SampleAnchorTcpCommon::m_clientHost,
            SampleAnchorTcpCommon::m_tcpPort,
            SampleAnchorTcpCommon::m_serverHost,
            SampleAnchorTcpCommon::m_tcpPort
            );
        // Create the web socket connection.
        m_socketClient = ref new StreamSocket();
        // The client connects to the server.
        return create_task(m_socketClient->ConnectAsync(endpointPair, SocketProtectionLevel::PlainSocket)).then([this](task<void> previousTask)
        {
            try
            {
                // Try getting all exceptions from the continuation chain above this point.
                previousTask.get();
                m_anchorTcpSocketStreamReader = ref new DataReader(m_socketClient->InputStream);
                OutputDebugString(L"Client connected!\n");
                m_anchorTcpSocketStreamReader->InputStreamOptions = InputStreamOptions::ReadAhead;
                WaitForAnchorDataStream();
                return true;
            }
            catch (Exception^ exception)
            {
                if (exception->HResult == 0x80072741)
                {
                    // This code sample includes a very simple implementation of client/server
                    // endpoint detection: if the current instance tries to connect to itself,
                    // it is determined to be the server.
                    OutputDebugString(L"Starting up the server instance.\n");
                    // When we return false, we'll start up the server instead.
                    return false;
                }
                else if ((exception->HResult == 0x8007274c) || // connection timed out
                    (exception->HResult == 0x80072740)) // connection maxed at server end
                {
                    // If the connection timed out, try again.
                    ConnectToServer();
                }
                else if (exception->HResult == 0x80072741)
                {
                    // No connection is possible.
                }
                HandleException(exception);
                return true;
            }
        });
    }
    else
    {
        OutputDebugString(L"A StreamSocket connection to a server already exists.\n");
        return task_from_result<bool>(true);
    }
}
```

接続が完了すると、サーバーがデータを送信するのを待ちます。 これを行うには、ストリームデータリーダーで LoadAsync を呼び出します。

最初に受け取るバイトのセットは常にヘッダーパケットである必要があります。これは、前のセクションで説明したように、アンカーデータストリームのバイト長を示します。

```
void SampleAnchorTcpClient::WaitForAnchorDataStream()
{
    if (m_anchorTcpSocketStreamReader == nullptr)
    {
        // We have not connected yet.
        return;
    }
    OutputDebugString(L"Waiting for server message.\n");
    // Wait for the first message, which specifies the byte length of the string data.
    create_task(m_anchorTcpSocketStreamReader->LoadAsync(SampleAnchorTcpCommon::c_streamHeaderByteArrayLength)).then([this](unsigned int numberOfBytes)
    {
        if (numberOfBytes > 0)
        {
            OutputDebugString(L"Server message incoming.\n");
            return ReceiveAnchorDataLengthMessage();
        }
        else
        {
            OutputDebugString(L"0-byte async task received, awaiting server message again.\n");
            WaitForAnchorDataStream();
            return task_from_result<size_t>(0);
        }
```

...

```
task<size_t> SampleAnchorTcpClient::ReceiveAnchorDataLengthMessage()
{
    byte data[4];
    m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(data, SampleAnchorTcpCommon::c_streamHeaderByteArrayLength));
    unsigned int lengthMessageSize = *reinterpret_cast<unsigned int*>(data);
    if (lengthMessageSize > 0)
    {
        OutputDebugString(L"One or more anchors to be received.\n");
        return task_from_result<size_t>(lengthMessageSize);
    }
    else
    {
        OutputDebugString(L"No anchors to be received.\n");
        ConnectToServer();
    }
    return task_from_result<size_t>(0);
}
```

ヘッダーパケットを受信すると、予想されるアンカーデータのバイト数がわかります。 ストリームからそれらのバイトを読み取ることができます。

```
}).then([this](size_t dataStreamLength)
    {
        if (dataStreamLength > 0)
        {
            std::wstring debugMessage = std::to_wstring(dataStreamLength);
            debugMessage += L" bytes of anchor data incoming.\n";
            OutputDebugString(debugMessage.c_str());
            // Prepare to receive the data stream in one or more pieces.
            m_anchorStreamLength = dataStreamLength;
            m_exportedAnchorStoreBytes.clear();
            m_exportedAnchorStoreBytes.resize(m_anchorStreamLength);
            OutputDebugString(L"Loading byte stream.\n");
            return ReceiveAnchorDataStream();
        }
        else
        {
            OutputDebugString(L"Error: Anchor data size not received.\n");
            ConnectToServer();
            return task_from_result<bool>(false);
        }
    });
}
```

アンカーデータストリームを受信するためのコードを次に示します。 ここでも、最初にストリームからバイトを読み込みます。この操作は、StreamSocket がネットワークからそのバイト数を受信するのを待機するため、完了するまでに時間がかかることがあります。

読み込み操作が完了すると、そのバイト数を読み取ることができます。 アンカーデータストリームに予想されるバイト数を受け取った場合は、アンカーデータをインポートできます。それ以外の場合は、何らかのエラーが発生している必要があります。 たとえば、データストリームの送信を完了する前にサーバーインスタンスが終了した場合や、データストリーム全体をクライアントが受信する前にネットワークがダウンした場合に発生することがあります。

```
task<bool> SampleAnchorTcpClient::ReceiveAnchorDataStream()
{
    if (m_anchorStreamLength > 0)
    {
        // First, we load the bytes from the network socket.
        return create_task(m_anchorTcpSocketStreamReader->LoadAsync(m_anchorStreamLength)).then([this](size_t bytesLoadedByStreamReader)
        {
            if (bytesLoadedByStreamReader > 0)
            {
                // Once the bytes are loaded, we can read them from the stream.
                m_anchorTcpSocketStreamReader->ReadBytes(Platform::ArrayReference<byte>(&m_exportedAnchorStoreBytes[0],
                    bytesLoadedByStreamReader));
                // Check status.
                if (bytesLoadedByStreamReader == m_anchorStreamLength)
                {
                    // The whole stream has arrived. We can process the data.
                    // Informational message of progress complete.
                    std::wstring infoMessage = std::to_wstring(bytesLoadedByStreamReader);
                    infoMessage += L" bytes read out of ";
                    infoMessage += std::to_wstring(m_anchorStreamLength);
                    infoMessage += L" total bytes; importing the data.\n";
                    OutputDebugStringW(infoMessage.c_str());
                    // Kick off a thread to wait for a new message indicating another incoming anchor data stream.
                    WaitForAnchorDataStream();
                    // Process the data for the stream we just received.
                    return SpatialAnchorImportExportHelper::ImportAnchorDataAsync(m_exportedAnchorStoreBytes, m_spatialAnchorHelper->GetAnchorMap());
                }
                else
                {
                    OutputDebugString(L"Error: Fewer than expected anchor data bytes were received.\n");
                }
            }
            else
            {
                OutputDebugString(L"Error: No anchor bytes were received.\n");
            }
            return task_from_result<bool>(false);
        });
    }
    else
    {
        OutputDebugString(L"Warning: A zero-length data buffer was sent.\n");
        return task_from_result<bool>(false);
    }
}
```

ここでも、不明なネットワークエラーを処理できるように準備する必要があります。

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

以上で作業は終了です。 これで、ネットワーク経由で受信したアンカーを特定するための十分な情報が得られます。 ここでも、クライアントがアンカーを正常に見つけるために十分な数のビジュアル追跡データが必要であることに注意してください。すぐに機能しない場合は、しばらく試してみてください。 それでもうまくいかない場合は、サーバーがより多くのアンカーを送信するようにし、ネットワーク通信を使用してクライアントに対して機能するものに同意してください。 これを試すには、HolographicSpatialAnchorTransferSample をダウンロードし、クライアントとサーバーの Ip アドレスを構成して、クライアントとサーバーの HoloLens デバイスに展開します。

## <a name="see-also"></a>関連項目
* [並列パターン ライブラリ (PPL)](https://msdn.microsoft.com/library/dd492418.aspx)
* [Windows. ネットワーク. StreamSocket](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [Windows. ネットワーク. StreamSocketListener](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
