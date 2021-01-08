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
# <a name="local-anchor-transfers-in-directx"></a><span data-ttu-id="dbfd1-104">DirectX でのローカルアンカー転送</span><span class="sxs-lookup"><span data-stu-id="dbfd1-104">Local anchor transfers in DirectX</span></span>

<span data-ttu-id="dbfd1-105"><a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>を使用できない場合、ローカルアンカー転送では、1つの hololens デバイスが2つ目の hololens デバイスによってインポートされるアンカーをエクスポートできるようにします。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-105">In situations where you cannot use <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="dbfd1-106">ローカルアンカー転送は、 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>よりも堅牢なアンカーの再呼び出しを提供します。この方法では、iOS デバイスと Android デバイスはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-106">Local anchor transfers provide less robust anchor recall than <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

>[!NOTE]
><span data-ttu-id="dbfd1-107">この記事のコードスニペットでは、 [C++ holographic プロジェクトテンプレート](../develop/native/creating-a-holographic-directx-project.md)で使用される c + c++ 17 準拠の c++/WinRT ではなく、c++/cx の使用方法を現在説明しています。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-107">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../develop/native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="dbfd1-108">概念は C++/WinRT プロジェクトに相当しますが、コードを変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-108">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="transferring-spatial-anchors"></a><span data-ttu-id="dbfd1-109">空間アンカーの転送</span><span class="sxs-lookup"><span data-stu-id="dbfd1-109">Transferring spatial anchors</span></span>

<span data-ttu-id="dbfd1-110">[SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)を使用して、Windows Mixed Reality デバイス間で空間アンカーを転送できます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-110">You can transfer spatial anchors between Windows Mixed Reality devices by using the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="dbfd1-111">この API を使用すると、世界中の正確な場所を特定し、そのバンドルを別のデバイスにインポートするために必要なすべてのサポートセンサーデータを使用してアンカーをまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-111">This API lets you bundle up an anchor with all the supporting sensor data needed to find that exact place in the world, and then import that bundle on another device.</span></span> <span data-ttu-id="dbfd1-112">2番目のデバイス上のアプリがアンカーをインポートすると、各アプリは、その共有空間アンカーの座標系を使用してホログラムをレンダリングできます。これは、実際の世界の同じ場所に表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-112">Once the app on the second device has imported that anchor, each app can render holograms using that shared spatial anchor's coordinate system, which will then appear in the same place in the real world.</span></span>

<span data-ttu-id="dbfd1-113">空間アンカーは異なる種類のデバイス間では転送できないことに注意してください。たとえば、1つの HoloLens 空間アンカーは、イマーシブヘッドセットを使用して指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-113">Note that spatial anchors are not able to transfer between different device types, for example a HoloLens spatial anchor may not be locatable using an immersive headset.</span></span>  <span data-ttu-id="dbfd1-114">転送されたアンカーは、iOS または Android デバイスとも互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-114">Transferred anchors are also not compatible with iOS or Android devices.</span></span>

## <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="dbfd1-115">SpatialPerception 機能を使用するようにアプリを設定する</span><span class="sxs-lookup"><span data-stu-id="dbfd1-115">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="dbfd1-116">[SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx)を使用するには、アプリに SpatialPerception 機能を使用するためのアクセス許可が付与されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-116">Your app must be granted permission to use the SpatialPerception capability before it can use the [SpatialAnchorTransferManager](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.aspx).</span></span> <span data-ttu-id="dbfd1-117">これは、空間アンカーを転送する場合に必要です。これは、そのアンカーの近くで、時間の経過と共に収集されるセンサーイメージを共有することです。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-117">This is necessary because transferring a spatial anchor involves sharing sensor images gathered over time in vicinity of that anchor, which might include sensitive information.</span></span>

<span data-ttu-id="dbfd1-118">この機能をアプリの package.appxmanifest ファイルで宣言します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-118">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="dbfd1-119">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-119">Here's an example:</span></span>

```
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="dbfd1-120">この機能は、 **uap2** 名前空間から取得されます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-120">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="dbfd1-121">マニフェスト内のこの名前空間へのアクセスを取得するには、パッケージの> 要素に *xlmns* 属性として含め &lt; ます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-121">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="dbfd1-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-122">Here's an example:</span></span>

```
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap mp"
    >
```

<span data-ttu-id="dbfd1-123">**注:** SpatialAnchor export/import Api にアクセスするには、アプリが実行時に機能を要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-123">**NOTE:** Your app will need to request the capability at runtime before it can access SpatialAnchor export/import APIs.</span></span> <span data-ttu-id="dbfd1-124">次の例の [Requestaccessasync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-124">See [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchortransfermanager.requestaccessasync.aspx) in the examples below.</span></span>

## <a name="serialize-anchor-data-by-exporting-it-with-the-spatialanchortransfermanager"></a><span data-ttu-id="dbfd1-125">SpatialAnchorTransferManager を使用してエクスポートすることによってアンカーデータをシリアル化する</span><span class="sxs-lookup"><span data-stu-id="dbfd1-125">Serialize anchor data by exporting it with the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="dbfd1-126">ヘルパー関数は、 [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) データをエクスポート (シリアル化) するためのコードサンプルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-126">A helper function is included in the code sample to export (serialize) [SpatialAnchor](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) data.</span></span> <span data-ttu-id="dbfd1-127">この export API は、文字列をアンカーに関連付けるキーと値のペアのコレクション内のすべてのアンカーをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-127">This export API serializes all anchors in a collection of key-value pairs associating strings with anchors.</span></span>

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

<span data-ttu-id="dbfd1-128">まず、データストリームを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-128">First, we need to set up the data stream.</span></span> <span data-ttu-id="dbfd1-129">これにより、1を使用できるようになります)。TryExportAnchorsAsync を使用して、アプリによって所有されているバッファーにデータを配置します。 2.)エクスポートされたバイトバッファーストリームからデータを読み取ります。これは、WinRT データストリームで、独自のメモリバッファー (std:: vector byte>) に格納され &lt; ます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-129">This will allow us to 1.) use TryExportAnchorsAsync to put the data in a buffer owned by the app, and 2.) read data from the exported byte buffer stream - which is a WinRT data stream - into our own memory buffer, which is a std::vector&lt;byte>.</span></span>

```
// Create a random access stream to process the anchor byte data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor byte stream.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
```

<span data-ttu-id="dbfd1-130">空間データ (システムによってエクスポートされたアンカーを含む) にアクセスする権限を要求する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-130">We need to ask permission to access spatial data, including anchors that are exported by the system.</span></span>

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

<span data-ttu-id="dbfd1-131">Get アクセス許可とアンカーがエクスポートされた場合は、データストリームを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-131">If we do get permission and anchors are exported, we can read the data stream.</span></span> <span data-ttu-id="dbfd1-132">ここでは、データの読み取りに使用する DataReader と InputStream を作成する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-132">Here, we also show how to create the DataReader and InputStream we will use to read the data.</span></span>

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

<span data-ttu-id="dbfd1-133">ストリームからバイトを読み取った後は、そのようなデータを独自のデータバッファーに保存することができます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-133">After we read bytes from the stream, we can save them to our own data buffer like so.</span></span>

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

## <a name="deserialize-anchor-data-by-importing-it-into-the-system-using-the-spatialanchortransfermanager"></a><span data-ttu-id="dbfd1-134">SpatialAnchorTransferManager を使用してシステムにインポートすることでアンカーデータを逆シリアル化する</span><span class="sxs-lookup"><span data-stu-id="dbfd1-134">Deserialize anchor data by importing it into the system using the SpatialAnchorTransferManager</span></span>

<span data-ttu-id="dbfd1-135">前にエクスポートしたデータを読み込むためのコードサンプルには、ヘルパー関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-135">A helper function is included in the code sample to load previously exported data.</span></span> <span data-ttu-id="dbfd1-136">この逆シリアル化関数は、SpatialAnchorStore が提供するものと同様に、キーと値のペアのコレクションを提供します。ただし、このデータを別のソース (ネットワークソケットなど) から受け取った場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-136">This deserialization function provides a collection of key-value pairs, similar to what the SpatialAnchorStore provides - except that we got this data from another source, such as a network socket.</span></span> <span data-ttu-id="dbfd1-137">このデータは、オフラインで、アプリ内メモリを使用して、または (該当する場合は) アプリの SpatialAnchorStore を使用して、オフラインで保存する前に処理および理由を確認できます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-137">You can process and reason about this data before storing it offline, using in-app memory, or (if applicable) your app's SpatialAnchorStore.</span></span>

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

<span data-ttu-id="dbfd1-138">まず、アンカーデータにアクセスするためのストリームオブジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-138">First, we need to create stream objects to access the anchor data.</span></span> <span data-ttu-id="dbfd1-139">ここでは、バッファーからシステムバッファーにデータを書き込みます。そのため、SpatialAnchors としてバイトバッファーからシステムにアンカーを取得するという目標を達成するために、インメモリデータストリームに書き込む DataWriter を作成します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-139">We will be writing the data from our buffer to a system buffer, so we will create a DataWriter that writes to an in-memory data stream in order to accomplish our goal of getting anchors from a byte buffer into the system as SpatialAnchors.</span></span>

```
// Create a random access stream for the anchor data.
InMemoryRandomAccessStream^ stream = ref new InMemoryRandomAccessStream();
// Get an output stream for the anchor data.
IOutputStream^ outputStream = stream->GetOutputStreamAt(0);
// Create a writer, to put the bytes in the stream.
DataWriter^ writer = ref new DataWriter(outputStream);
```

<span data-ttu-id="dbfd1-140">ここでも、空間アンカーデータをエクスポートするアクセス許可がアプリに付与されていることを確認する必要があります。これには、ユーザーの環境に関する個人情報が含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-140">Once again, we need to ensure the app has permission to export spatial anchor data, which could include private information about the user's environment.</span></span>

```
// Request access to transfer spatial anchors.
return create_task(SpatialAnchorTransferManager::RequestAccessAsync()).then(
    [&anchorByteDataIn, writer](SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Access is allowed.
```

<span data-ttu-id="dbfd1-141">アクセスが許可されている場合は、バッファーからシステムデータストリームにバイトを書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-141">If access is allowed, we can write bytes from the buffer to a system data stream.</span></span>

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

<span data-ttu-id="dbfd1-142">データストリームへのバイトの格納に成功した場合は、SpatialAnchorTransferManager を使用してそのデータをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-142">If we were successful in storing bytes in the data stream, we can try to import that data using the SpatialAnchorTransferManager.</span></span>

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

<span data-ttu-id="dbfd1-143">データをインポートできる場合は、文字列をアンカーに関連付けるキーと値のペアのマップビューが表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-143">If the data is able to be imported, we get a map view of key-value pairs associating strings with anchors.</span></span> <span data-ttu-id="dbfd1-144">これを独自のメモリ内データコレクションに読み込んで、そのコレクションを使用して、興味のあるアンカーを探すことができます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-144">We can load this into our own in-memory data collection, and use that collection to look for anchors that we are interested in using.</span></span>

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

<span data-ttu-id="dbfd1-145">**注:** アンカーをインポートできるだけなので、すぐに使用できるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-145">**NOTE:** Just because you can import an anchor, doesn't necessarily mean that you can use it right away.</span></span> <span data-ttu-id="dbfd1-146">アンカーは、別の部屋、または物理的に別の場所にある場合があります。アンカーは、そのデバイスを受信したデバイスに、アンカーが作成された環境についての十分な視覚的情報があることを確認します。これにより、既知の現在の環境を基準としてアンカーの位置を復元できます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-146">The anchor might be in a different room, or another physical location entirely; the anchor won't be locatable until the device that received it has enough visual information about the environment the anchor was created in, to restore the anchor's position relative to the known current environment.</span></span> <span data-ttu-id="dbfd1-147">クライアントの実装では、実際のコンテンツに使用する前に、ローカルの座標系または参照フレームに対してアンカーの位置を特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-147">The client implementation should try locating the anchor relative to your local coordinate system or reference frame before continuing on to try to use it for live content.</span></span> <span data-ttu-id="dbfd1-148">たとえば、アンカーが特定可能になるまで、現在の座標系を基準としてアンカーを定期的に検索してみてください。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-148">For example, try locating the anchor relative to a current coordinate system periodically until the anchor begins to be locatable.</span></span>

## <a name="special-considerations"></a><span data-ttu-id="dbfd1-149">特別な考慮事項</span><span class="sxs-lookup"><span data-stu-id="dbfd1-149">Special Considerations</span></span>

<span data-ttu-id="dbfd1-150">[TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API を使用すると、複数の[SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx)を同じ不透明なバイナリ blob にエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-150">The [TryExportAnchorsAsync](https://msdn.microsoft.com/library/windows/apps/mt592763.aspx) API allows multiple [SpatialAnchors](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialanchor.aspx) to be exported into the same opaque binary blob.</span></span> <span data-ttu-id="dbfd1-151">ただし、単一の SpatialAnchor または複数の SpatialAnchors が1回の呼び出しでエクスポートされるかどうかによって、blob に含まれるデータには微妙な違いがあります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-151">However, there is a subtle difference in what data the blob will include, depending on whether a single SpatialAnchor or multiple SpatialAnchors are exported in a single call.</span></span>

### <a name="export-of-a-single-spatialanchor"></a><span data-ttu-id="dbfd1-152">1つの SpatialAnchor のエクスポート</span><span class="sxs-lookup"><span data-stu-id="dbfd1-152">Export of a single SpatialAnchor</span></span>

<span data-ttu-id="dbfd1-153">Blob には、SpatialAnchor をインポートするデバイスで環境を認識できるように、SpatialAnchor の近傍に環境の表現が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-153">The blob contains a representation of the environment in the vicinity of the SpatialAnchor so that the environment can be recognized on the device that imports the SpatialAnchor.</span></span> <span data-ttu-id="dbfd1-154">インポートが完了すると、新しい SpatialAnchor がデバイスで使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-154">After the import completes, the new SpatialAnchor will be available to the device.</span></span> <span data-ttu-id="dbfd1-155">ユーザーが最近アンカーの近くにいたことを前提として、SpatialAnchor にアタッチされているホログラムをレンダリングできます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-155">Assuming the user has recently been in vicinity of the anchor, it will be locatable and holograms attached to the SpatialAnchor can be rendered.</span></span> <span data-ttu-id="dbfd1-156">これらのホログラムは、SpatialAnchor をエクスポートした元のデバイスで行ったのと同じ物理的な場所に表示されます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-156">These holograms will show up in the same physical location that they did on the original device which exported the SpatialAnchor.</span></span>

![1つの SpatialAnchor のエクスポート](images/singleanchor.png)

### <a name="export-of-multiple-spatialanchors"></a><span data-ttu-id="dbfd1-158">複数の SpatialAnchors のエクスポート</span><span class="sxs-lookup"><span data-stu-id="dbfd1-158">Export of multiple SpatialAnchors</span></span>

<span data-ttu-id="dbfd1-159">1つの SpatialAnchor のエクスポートと同様に、blob には、指定されたすべての SpatialAnchors の近接部分にある環境の表現が含まれます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-159">Like the export of a single SpatialAnchor, the blob contains a representation of the environment in the vicinity of all the specified SpatialAnchors.</span></span> <span data-ttu-id="dbfd1-160">また、blob には、含まれている SpatialAnchors との間の接続に関する情報が含まれています (同じ物理領域に存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-160">In addition, the blob contains information about the connections between the included SpatialAnchors, if they are located in the same physical space.</span></span> <span data-ttu-id="dbfd1-161">これは、隣接する2つの SpatialAnchors がインポートされた場合、2つの SpatialAnchors 間の変換を計算するのに十分なデータが blob に含まれていたため、2 *番目* の SpatialAnchor にアタッチされたホログラムが、デバイスが *最初* の SpatialAnchor の周囲の環境を認識している場合でも、このようになります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-161">This means that if two nearby SpatialAnchors are imported, then a hologram attached to the *second* SpatialAnchor would be locatable even if the device only recognizes the environment around the *first* SpatialAnchor, because enough data to compute transform between the two SpatialAnchors was included in the blob.</span></span> <span data-ttu-id="dbfd1-162">2つの SpatialAnchors が個別にエクスポートされた場合 (TryExportSpatialAnchors の2つの個別の呼び出し)、最初の SpatialAnchor に接続されている、2番目のにアタッチされているホログラムの blob に十分なデータが含まれていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-162">If the two SpatialAnchors were exported individually (two separate calls to TryExportSpatialAnchors) then there may not be enough data included in the blob for holograms attached to the second SpatialAnchor to be locatable when the first one is located.</span></span>

![1つの TryExportAnchorsAsync 呼び出しを使用してエクスポートされた複数のアンカー](images/multipleanchors.png) ![アンカーごとに個別の TryExportAnchorsAsync 呼び出しを使用してエクスポートされた複数のアンカー](images/separateanchors.png)

## <a name="example-send-anchor-data-using-a-windowsnetworkingstreamsocket"></a><span data-ttu-id="dbfd1-165">例: Windows:: Network:: StreamSocket を使用してアンカーデータを送信する</span><span class="sxs-lookup"><span data-stu-id="dbfd1-165">Example: Send anchor data using a Windows::Networking::StreamSocket</span></span>

<span data-ttu-id="dbfd1-166">ここでは、エクスポートされたアンカーデータを TCP ネットワーク経由で送信することによって使用する方法の例を示します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-166">Here, we provide an example of how to use exported anchor data by sending it across a TCP network.</span></span> <span data-ttu-id="dbfd1-167">これは、HolographicSpatialAnchorTransferSample からのものです。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-167">This is from the HolographicSpatialAnchorTransferSample.</span></span>

<span data-ttu-id="dbfd1-168">WinRT StreamSocket クラスは、PPL タスクライブラリを使用します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-168">The WinRT StreamSocket class uses the PPL task library.</span></span> <span data-ttu-id="dbfd1-169">ネットワークエラーが発生した場合、再スローされた例外を使用して、チェーン内の次のタスクにエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-169">In the case of network errors, the error is returned to the next task in the chain using an exception that is re-thrown.</span></span> <span data-ttu-id="dbfd1-170">例外には、エラーの状態を示す HRESULT が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-170">The exception contains an HRESULT indicating the error status.</span></span>

### <a name="use-a-windowsnetworkingstreamsocketlistener-with-tcp-to-send-exported-anchor-data"></a><span data-ttu-id="dbfd1-171">Windows:: Network:: StreamSocketListener と TCP を使用して、エクスポートされたアンカーデータを送信する</span><span class="sxs-lookup"><span data-stu-id="dbfd1-171">Use a Windows::Networking::StreamSocketListener with TCP to send exported anchor data</span></span>

<span data-ttu-id="dbfd1-172">接続をリッスンするサーバーインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-172">Create a server instance that listens for a connection.</span></span>

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

<span data-ttu-id="dbfd1-173">接続を受信したら、クライアントソケット接続を使用してアンカーデータを送信します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-173">When a connection is received, use the client socket connection to send anchor data.</span></span>

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

<span data-ttu-id="dbfd1-174">ここで、エクスポートしたアンカーデータを含むデータストリームの送信を開始できます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-174">Now, we can begin to send a data stream that contains the exported anchor data.</span></span>

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

<span data-ttu-id="dbfd1-175">ストリーム自体を送信する前に、まずヘッダーパケットを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-175">Before we can send the stream itself, we must first send a header packet.</span></span> <span data-ttu-id="dbfd1-176">このヘッダーパケットは固定長である必要があり、また、アンカーデータストリームであるバイトの変数配列の長さも示す必要があります。この例では、送信するヘッダーデータが他にないため、ヘッダーは長さが4バイトで、32ビットの符号なし整数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-176">This header packet must be of fixed length, and it must also indicate the length of the variable array of bytes that is the anchor data stream; in the case of this example we have no other header data to send, so our header is 4 bytes long and contains a 32-bit unsigned integer.</span></span>

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

<span data-ttu-id="dbfd1-177">ストリームの長さ (バイト単位) がクライアントに送信されると、データストリーム自体をソケットストリームに書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-177">Once the stream length, in bytes, has been sent to the client, we can proceed to write the data stream itself to the socket stream.</span></span> <span data-ttu-id="dbfd1-178">これにより、アンカーストアのバイトがクライアントに送信されます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-178">This will cause the anchor store bytes to get sent to the client.</span></span>

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

<span data-ttu-id="dbfd1-179">このトピックで既に説明したように、ネットワークエラーステータスメッセージを含む例外を処理できるように準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-179">As noted earlier in this topic, we must be prepared to handle exceptions containing network error status messages.</span></span> <span data-ttu-id="dbfd1-180">予期しないエラーの場合は、などのように、デバッグコンソールに例外情報を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-180">For errors that are not expected, we can write the exception info to the debug console like so.</span></span> <span data-ttu-id="dbfd1-181">これにより、コードサンプルが接続を完了できない場合、またはアンカーデータの送信を完了できない場合に何が起こったかについての手掛かりが得られます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-181">This will give us a clue as to what happened if our code sample is unable to complete the connection, or if it is unable to finish sending the anchor data.</span></span>

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

### <a name="use-a-windowsnetworkingstreamsocket-with-tcp-to-receive-exported-anchor-data"></a><span data-ttu-id="dbfd1-182">Windows:: Network:: StreamSocket と TCP を使用して、エクスポートされたアンカーデータを受信する</span><span class="sxs-lookup"><span data-stu-id="dbfd1-182">Use a Windows::Networking::StreamSocket with TCP to receive exported anchor data</span></span>

<span data-ttu-id="dbfd1-183">まず、サーバーに接続する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-183">First, we have to connect to the server.</span></span> <span data-ttu-id="dbfd1-184">このコードサンプルでは、StreamSocket を作成して構成する方法と、ソケット接続を使用してネットワークデータを取得するために使用できる DataReader を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-184">This code sample shows how to create and configure a StreamSocket, and create a DataReader that you can use to acquire network data using the socket connection.</span></span>

<span data-ttu-id="dbfd1-185">**注:** このサンプルコードを実行する場合は、クライアントを起動する前にサーバーを構成して起動していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-185">**NOTE:** If you run this sample code, ensure that you configure and launch the server before starting the client.</span></span>

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

<span data-ttu-id="dbfd1-186">接続が完了すると、サーバーがデータを送信するのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-186">Once we have a connection, we can wait for the server to send data.</span></span> <span data-ttu-id="dbfd1-187">これを行うには、ストリームデータリーダーで LoadAsync を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-187">We do this by calling LoadAsync on the stream data reader.</span></span>

<span data-ttu-id="dbfd1-188">最初に受け取るバイトのセットは常にヘッダーパケットである必要があります。これは、前のセクションで説明したように、アンカーデータストリームのバイト長を示します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-188">The first set of bytes we receive should always be the header packet, which indicates the anchor data stream byte length as described in the previous section.</span></span>

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

<span data-ttu-id="dbfd1-189">...</span><span class="sxs-lookup"><span data-stu-id="dbfd1-189">...</span></span>

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

<span data-ttu-id="dbfd1-190">ヘッダーパケットを受信すると、予想されるアンカーデータのバイト数がわかります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-190">After we have received the header packet, we know how many bytes of anchor data we should expect.</span></span> <span data-ttu-id="dbfd1-191">ストリームからそれらのバイトを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-191">We can proceed to read those bytes from the stream.</span></span>

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

<span data-ttu-id="dbfd1-192">アンカーデータストリームを受信するためのコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-192">Here's our code for receiving the anchor data stream.</span></span> <span data-ttu-id="dbfd1-193">ここでも、最初にストリームからバイトを読み込みます。この操作は、StreamSocket がネットワークからそのバイト数を受信するのを待機するため、完了するまでに時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-193">Again, we will first load the bytes from the stream; this operation may take some time to complete as the StreamSocket waits to receive that amount of bytes from the network.</span></span>

<span data-ttu-id="dbfd1-194">読み込み操作が完了すると、そのバイト数を読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-194">When the loading operation is complete, we can read that number of bytes.</span></span> <span data-ttu-id="dbfd1-195">アンカーデータストリームに予想されるバイト数を受け取った場合は、アンカーデータをインポートできます。それ以外の場合は、何らかのエラーが発生している必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-195">If we received the number of bytes that we expect for the anchor data stream, we can go ahead and import the anchor data; if not, there must have been some sort of error.</span></span> <span data-ttu-id="dbfd1-196">たとえば、データストリームの送信を完了する前にサーバーインスタンスが終了した場合や、データストリーム全体をクライアントが受信する前にネットワークがダウンした場合に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-196">For example, this can happen when the server instance terminates before it can finish sending the data stream, or the network goes down before the entire data stream can be received by the client.</span></span>

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

<span data-ttu-id="dbfd1-197">ここでも、不明なネットワークエラーを処理できるように準備する必要があります。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-197">Again, we must be prepared to handle unknown network errors.</span></span>

```
void SampleAnchorTcpClient::HandleException(Exception^ exception)
{
    std::wstring error = L"Connection error: ";
    error += exception->ToString()->Data();
    error += L"\n";
    OutputDebugString(error.c_str());
}
```

<span data-ttu-id="dbfd1-198">以上で作業は終了です。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-198">That's it!</span></span> <span data-ttu-id="dbfd1-199">これで、ネットワーク経由で受信したアンカーを特定するための十分な情報が得られます。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-199">Now, you should have enough information to try locating the anchors received over the network.</span></span> <span data-ttu-id="dbfd1-200">ここでも、クライアントがアンカーを正常に見つけるために十分な数のビジュアル追跡データが必要であることに注意してください。すぐに機能しない場合は、しばらく試してみてください。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-200">Again, note that the client must have enough visual tracking data for the space to successfully locate the anchor; if it doesn't work right away, try walking around for a while.</span></span> <span data-ttu-id="dbfd1-201">それでもうまくいかない場合は、サーバーがより多くのアンカーを送信するようにし、ネットワーク通信を使用してクライアントに対して機能するものに同意してください。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-201">If it still doesn't work, have the server send more anchors, and use network communications to agree on one that works for the client.</span></span> <span data-ttu-id="dbfd1-202">これを試すには、HolographicSpatialAnchorTransferSample をダウンロードし、クライアントとサーバーの Ip アドレスを構成して、クライアントとサーバーの HoloLens デバイスに展開します。</span><span class="sxs-lookup"><span data-stu-id="dbfd1-202">You can try this out by downloading the HolographicSpatialAnchorTransferSample, configuring your client and server IPs, and deploying it to client and server HoloLens devices.</span></span>

## <a name="see-also"></a><span data-ttu-id="dbfd1-203">関連項目</span><span class="sxs-lookup"><span data-stu-id="dbfd1-203">See also</span></span>
* [<span data-ttu-id="dbfd1-204">並列パターン ライブラリ (PPL)</span><span class="sxs-lookup"><span data-stu-id="dbfd1-204">Parallel Patterns Library (PPL)</span></span>](https://msdn.microsoft.com/library/dd492418.aspx)
* [<span data-ttu-id="dbfd1-205">Windows. ネットワーク. StreamSocket</span><span class="sxs-lookup"><span data-stu-id="dbfd1-205">Windows.Networking.StreamSocket</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocket.aspx)
* [<span data-ttu-id="dbfd1-206">Windows. ネットワーク. StreamSocketListener</span><span class="sxs-lookup"><span data-stu-id="dbfd1-206">Windows.Networking.StreamSocketListener</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.networking.sockets.streamsocketlistener.aspx)
