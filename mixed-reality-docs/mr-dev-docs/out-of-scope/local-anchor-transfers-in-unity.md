---
title: Unity でのローカルアンカー転送
description: Unity mixed reality アプリケーションで複数の HoloLens デバイス間でアンカーを転送する方法について説明します。
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: 共有、アンカー、WorldAnchor、MR 共有250、WorldAnchorTransferBatch、SpatialPerception、転送、ローカルアンカー転送、アンカーエクスポート、アンカーインポート
ms.openlocfilehash: 4949dd49817d723729974fb5666d5defb64b72ba
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583874"
---
# <a name="local-anchor-transfers-in-unity"></a><span data-ttu-id="fbf43-104">Unity でのローカルアンカー転送</span><span class="sxs-lookup"><span data-stu-id="fbf43-104">Local anchor transfers in Unity</span></span>

<span data-ttu-id="fbf43-105"><a href="/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>を使用できない場合、ローカルアンカー転送では、1つの hololens デバイスが2つ目の hololens デバイスによってインポートされるアンカーをエクスポートできるようにします。</span><span class="sxs-lookup"><span data-stu-id="fbf43-105">In situations where you cannot use <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, local anchor transfers enable one HoloLens device to export an anchor to be imported by a second HoloLens device.</span></span>

>[!NOTE]
><span data-ttu-id="fbf43-106">ローカルアンカー転送は、 <a href="/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>よりも堅牢なアンカーの再呼び出しを提供します。この方法では、iOS デバイスと Android デバイスはサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="fbf43-106">Local anchor transfers provide less robust anchor recall than <a href="/azure/spatial-anchors" target="_blank">Azure Spatial Anchors</a>, and iOS and Android devices are not supported by this approach.</span></span>

### <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="fbf43-107">SpatialPerception 機能の設定</span><span class="sxs-lookup"><span data-stu-id="fbf43-107">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="fbf43-108">アプリで空間アンカーを転送するには、 *SpatialPerception* 機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbf43-108">In order for an app to transfer spatial anchors, the *SpatialPerception* capability must be enabled.</span></span>

<span data-ttu-id="fbf43-109">*SpatialPerception* 機能を有効にする方法:</span><span class="sxs-lookup"><span data-stu-id="fbf43-109">How to enable the *SpatialPerception* capability:</span></span>
1. <span data-ttu-id="fbf43-110">Unity エディターで、 **[プレーヤーの設定** ] ウィンドウを開きます (> プロジェクトの設定を編集し > player)</span><span class="sxs-lookup"><span data-stu-id="fbf43-110">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="fbf43-111">[ **Windows ストア** ] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fbf43-111">Click on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="fbf43-112">[**発行の設定]** を展開し、 **[機能]** ボックスの一覧の **"SpatialPerception"** 機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="fbf43-112">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

>[!NOTE]
><span data-ttu-id="fbf43-113">Unity プロジェクトを Visual Studio ソリューションに既にエクスポートしている場合は、新しいフォルダーにエクスポートするか、 [Visual studio の package.appxmanifest でこの機能](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)を手動で設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbf43-113">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

### <a name="anchor-transfer"></a><span data-ttu-id="fbf43-114">アンカー転送</span><span class="sxs-lookup"><span data-stu-id="fbf43-114">Anchor Transfer</span></span>

<span data-ttu-id="fbf43-115">**名前空間:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="fbf43-115">**Namespace:** *UnityEngine.XR.WSA.Sharing*</span></span><br>
<span data-ttu-id="fbf43-116">**型**: *WorldAnchorTransferBatch*</span><span class="sxs-lookup"><span data-stu-id="fbf43-116">**Type**: *WorldAnchorTransferBatch*</span></span>

<span data-ttu-id="fbf43-117">[WorldAnchor](../develop/unity/coordinate-systems-in-unity.md)を転送するには、転送するアンカーを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbf43-117">To transfer a [WorldAnchor](../develop/unity/coordinate-systems-in-unity.md), one must establish the anchor to be transferred.</span></span> <span data-ttu-id="fbf43-118">1つの HoloLens のユーザーが自分の環境をスキャンし、共有エクスペリエンスのアンカーとなるポイントを手動またはプログラムによって選択します。</span><span class="sxs-lookup"><span data-stu-id="fbf43-118">The user of one HoloLens scans their environment and either manually or programmatically chooses a point in space to be the Anchor for the shared experience.</span></span> <span data-ttu-id="fbf43-119">その後、このポイントを表すデータをシリアル化し、エクスペリエンスで共有している他のデバイスに転送できます。</span><span class="sxs-lookup"><span data-stu-id="fbf43-119">The data that represents this point can then be serialized and transmitted to the other devices that are sharing in the experience.</span></span> <span data-ttu-id="fbf43-120">各デバイスは、アンカーデータを逆シリアル化し、そのポイントの位置を特定しようとします。</span><span class="sxs-lookup"><span data-stu-id="fbf43-120">Each device then de-serializes the anchor data and attempts to locate that point in space.</span></span> <span data-ttu-id="fbf43-121">アンカー転送を機能させるには、各デバイスが、アンカーで表されるポイントを識別できるように、十分な環境でスキャンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbf43-121">In order for Anchor Transfer to work, each device must have scanned in enough of the environment such that the point represented by the anchor can be identified.</span></span>

### <a name="setup"></a><span data-ttu-id="fbf43-122">セットアップ</span><span class="sxs-lookup"><span data-stu-id="fbf43-122">Setup</span></span>

<span data-ttu-id="fbf43-123">このページのサンプルコードには、初期化する必要があるいくつかのフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="fbf43-123">The sample code on this page has a few fields that will need to be initialized:</span></span>
1. <span data-ttu-id="fbf43-124">*WorldAnchor* *オブジェクト* がある場合、このオブジェクトは Unity の *オブジェクト* です。</span><span class="sxs-lookup"><span data-stu-id="fbf43-124">*GameObject rootGameObject* is a *GameObject* in Unity that has a *WorldAnchor* Component on it.</span></span> <span data-ttu-id="fbf43-125">共有エクスペリエンスの1人のユーザーがこのユーザー *オブジェクト* を配置し、他のユーザーにデータをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="fbf43-125">One user in the shared experience will place this *GameObject* and export the data to the other users.</span></span>
2. <span data-ttu-id="fbf43-126">*WorldAnchor gameRootAnchor* は、 *root オブジェクト* にある *Unityengine. XR. WorldAnchor* です。</span><span class="sxs-lookup"><span data-stu-id="fbf43-126">*WorldAnchor gameRootAnchor* is the *UnityEngine.XR.WSA.WorldAnchor* that is on *rootGameObject*.</span></span>
3. <span data-ttu-id="fbf43-127">*byte [] importedData* は、各クライアントがネットワーク経由で受信するシリアル化されたアンカーのバイト配列です。</span><span class="sxs-lookup"><span data-stu-id="fbf43-127">*byte[] importedData* is a byte array for the serialized anchor each client is receiving over the network.</span></span>

```
public GameObject rootGameObject;
private UnityEngine.XR.WSA.WorldAnchor gameRootAnchor;

void Start ()
{
    gameRootAnchor = rootGameObject.GetComponent<UnityEngine.XR.WSA.WorldAnchor>();

    if (gameRootAnchor == null)
    {
        gameRootAnchor = rootGameObject.AddComponent<UnityEngine.XR.WSA.WorldAnchor>();
    }
}
```

### <a name="exporting"></a><span data-ttu-id="fbf43-128">エクスポート</span><span class="sxs-lookup"><span data-stu-id="fbf43-128">Exporting</span></span>

<span data-ttu-id="fbf43-129">エクスポートするには、 *WorldAnchor* が必要なだけで、受信側のアプリにとって意味のある情報を知ることができます。</span><span class="sxs-lookup"><span data-stu-id="fbf43-129">To export, we just need a *WorldAnchor* and to know what we will call it such that it makes sense for the receiving app.</span></span> <span data-ttu-id="fbf43-130">共有操作の1つのクライアントは、次の手順を実行して共有アンカーをエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="fbf43-130">One client in the shared experience will perform these steps to export the shared anchor:</span></span>
1. <span data-ttu-id="fbf43-131">*WorldAnchorTransferBatch* を作成する</span><span class="sxs-lookup"><span data-stu-id="fbf43-131">Create a *WorldAnchorTransferBatch*</span></span>
2. <span data-ttu-id="fbf43-132">転送する *WorldAnchors* を追加する</span><span class="sxs-lookup"><span data-stu-id="fbf43-132">Add the *WorldAnchors* to transfer</span></span>
3. <span data-ttu-id="fbf43-133">エクスポートを開始します</span><span class="sxs-lookup"><span data-stu-id="fbf43-133">Begin the export</span></span>
4. <span data-ttu-id="fbf43-134">データが使用可能になったときに *OnExportDataAvailable* イベントを処理する</span><span class="sxs-lookup"><span data-stu-id="fbf43-134">Handle the *OnExportDataAvailable* event as data becomes available</span></span>
5. <span data-ttu-id="fbf43-135">*Onexportcomplete* イベントの処理</span><span class="sxs-lookup"><span data-stu-id="fbf43-135">Handle the *OnExportComplete* event</span></span>

<span data-ttu-id="fbf43-136">ここでは、転送する対象をカプセル化してからバイトにエクスポートする *WorldAnchorTransferBatch* を作成します。</span><span class="sxs-lookup"><span data-stu-id="fbf43-136">We create a *WorldAnchorTransferBatch* to encapsulate what we will be transferring and then export that into bytes:</span></span>

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

<span data-ttu-id="fbf43-137">データが使用可能になったら、データのセグメントが使用可能であり、必要な方法で送信されるので、クライアントまたはバッファーにバイトを送信します。</span><span class="sxs-lookup"><span data-stu-id="fbf43-137">As data becomes available, send the bytes to the client or buffer as segments of data is available and send through whatever means desired:</span></span>

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

<span data-ttu-id="fbf43-138">エクスポートが完了したら、データを転送し、シリアル化に失敗した場合は、データを破棄するようにクライアントに指示します。</span><span class="sxs-lookup"><span data-stu-id="fbf43-138">Once the export is complete, if we have been transferring data and serialization failed, tell the client to discard the data.</span></span> <span data-ttu-id="fbf43-139">シリアル化が成功した場合は、すべてのデータが転送され、インポートを開始できることをクライアントに通知します。</span><span class="sxs-lookup"><span data-stu-id="fbf43-139">If the serialization succeeded, tell the client that all data has been transferred and importing can start:</span></span>

```
private void OnExportComplete(SerializationCompletionReason completionReason)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        SendExportFailedToClient();
    }
    else
    {
        SendExportSucceededToClient();
    }
}
```

### <a name="importing"></a><span data-ttu-id="fbf43-140">インポート</span><span class="sxs-lookup"><span data-stu-id="fbf43-140">Importing</span></span>

<span data-ttu-id="fbf43-141">送信元からバイトをすべて受信した後、データを *WorldAnchorTransferBatch* にインポートして、ルートゲームオブジェクトを同じ物理的な場所にロックすることができます。</span><span class="sxs-lookup"><span data-stu-id="fbf43-141">After receiving all of the bytes from the sender, we can import the data back into a *WorldAnchorTransferBatch* and lock our root game object into the same physical location.</span></span> <span data-ttu-id="fbf43-142">注: インポートに失敗する場合があり、再試行が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="fbf43-142">Note: import will sometimes transiently fail and needs to be retried:</span></span>

```
// This byte array should have been updated over the network from TransferDataToClient
private byte[] importedData;
private int retryCount = 3;

private void ImportRootGameObject()
{
    WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
}

private void OnImportComplete(SerializationCompletionReason completionReason, WorldAnchorTransferBatch deserializedTransferBatch)
{
    if (completionReason != SerializationCompletionReason.Succeeded)
    {
        Debug.Log("Failed to import: " + completionReason.ToString());
        if (retryCount > 0)
        {
            retryCount--;
            WorldAnchorTransferBatch.ImportAsync(importedData, OnImportComplete);
        }
        return;
    }

    this.gameRootAnchor = deserializedTransferBatch.LockObject("gameRoot", this.rootGameObject);
}
```

<span data-ttu-id="fbf43-143">*WorldAnchor* *オブジェクト* は、 *lockobject* 呼び出しによってロックされた後に、世界の同じ物理的な位置に保持されますが、Unity 座標空間内の他のユーザーとは異なる場所にある可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fbf43-143">After a *GameObject* is locked via the *LockObject* call, it will have a *WorldAnchor* which will keep it in the same physical position in the world, but it may be at a different location in the Unity coordinate space than other users.</span></span>