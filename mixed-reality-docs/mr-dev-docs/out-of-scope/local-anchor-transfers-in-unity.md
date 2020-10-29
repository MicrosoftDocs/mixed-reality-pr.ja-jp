---
title: Unity でのローカルアンカー転送
description: Unity アプリケーション内の複数の HoloLens デバイス間でアンカーを転送します。
author: fieldsjacksong
ms.author: jacksonf
ms.date: 03/21/2018
ms.topic: article
keywords: 共有、アンカー、WorldAnchor、MR 共有250、WorldAnchorTransferBatch、SpatialPerception、転送、ローカルアンカー転送、アンカーエクスポート、アンカーインポート
ms.openlocfilehash: d6aebfb89d05926b1f773dea58ee65fead57988e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91690762"
---
# <a name="local-anchor-transfers-in-unity"></a>Unity でのローカルアンカー転送

<a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>を使用できない場合、ローカルアンカー転送では、1つの hololens デバイスが2つ目の hololens デバイスによってインポートされるアンカーをエクスポートできるようにします。

>[!NOTE]
>ローカルアンカー転送は、 <a href="https://docs.microsoft.com/azure/spatial-anchors" target="_blank">Azure 空間アンカー</a>よりも堅牢なアンカーの再呼び出しを提供します。この方法では、iOS デバイスと Android デバイスはサポートされていません。

### <a name="setting-the-spatialperception-capability"></a>SpatialPerception 機能の設定

アプリで空間アンカーを転送するには、 *SpatialPerception* 機能を有効にする必要があります。

*SpatialPerception* 機能を有効にする方法:
1. Unity エディターで、 **[プレーヤーの設定** ] ウィンドウを開きます (> プロジェクトの設定を編集し > player)
2. [ **Windows ストア** ] タブをクリックします。
3. [ **発行の設定]** を展開し、 **[機能]** ボックスの一覧の **"SpatialPerception"** 機能を確認します。

>[!NOTE]
>Unity プロジェクトを Visual Studio ソリューションに既にエクスポートしている場合は、新しいフォルダーにエクスポートするか、 [Visual studio の package.appxmanifest でこの機能](local-anchor-transfers-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)を手動で設定する必要があります。

### <a name="anchor-transfer"></a>アンカー転送

**名前空間:** *UNITYENGINE. XR*<br>
**型** : *WorldAnchorTransferBatch*

[WorldAnchor](../develop/unity/coordinate-systems-in-unity.md)を転送するには、転送するアンカーを設定する必要があります。 1つの HoloLens のユーザーが自分の環境をスキャンし、共有エクスペリエンスのアンカーとなるポイントを手動またはプログラムによって選択します。 その後、このポイントを表すデータをシリアル化し、エクスペリエンスで共有している他のデバイスに転送できます。 各デバイスは、アンカーデータを逆シリアル化し、そのポイントの位置を特定しようとします。 アンカー転送を機能させるには、各デバイスが、アンカーで表されるポイントを識別できるように、十分な環境でスキャンする必要があります。

### <a name="setup"></a>セットアップ

このページのサンプルコードには、初期化する必要があるいくつかのフィールドがあります。
1. *WorldAnchor* *オブジェクト* がある場合、このオブジェクトは Unity の *オブジェクト* です。 共有エクスペリエンスの1人のユーザーがこのユーザー *オブジェクト* を配置し、他のユーザーにデータをエクスポートします。
2. *WorldAnchor gameRootAnchor* は、 *root オブジェクト* にある *Unityengine. XR. WorldAnchor* です。
3. *byte [] importedData* は、各クライアントがネットワーク経由で受信するシリアル化されたアンカーのバイト配列です。

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

### <a name="exporting"></a>エクスポート

エクスポートするには、 *WorldAnchor* が必要なだけで、受信側のアプリにとって意味のある情報を知ることができます。 共有操作の1つのクライアントは、次の手順を実行して共有アンカーをエクスポートします。
1. *WorldAnchorTransferBatch* を作成する
2. 転送する *WorldAnchors* を追加する
3. エクスポートを開始します
4. データが使用可能になったときに *OnExportDataAvailable* イベントを処理する
5. *Onexportcomplete* イベントの処理

ここでは、転送する対象をカプセル化してからバイトにエクスポートする *WorldAnchorTransferBatch* を作成します。

```
private void ExportGameRootAnchor()
{
    WorldAnchorTransferBatch transferBatch = new WorldAnchorTransferBatch();
    transferBatch.AddWorldAnchor("gameRoot", this.gameRootAnchor);
    WorldAnchorTransferBatch.ExportAsync(transferBatch, OnExportDataAvailable, OnExportComplete);
}
```

データが使用可能になったら、データのセグメントが使用可能であり、必要な方法で送信されるので、クライアントまたはバッファーにバイトを送信します。

```
private void OnExportDataAvailable(byte[] data)
{
    TransferDataToClient(data);
}
```

エクスポートが完了したら、データを転送し、シリアル化に失敗した場合は、データを破棄するようにクライアントに指示します。 シリアル化が成功した場合は、すべてのデータが転送され、インポートを開始できることをクライアントに通知します。

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

### <a name="importing"></a>インポート

送信元からバイトをすべて受信した後、データを *WorldAnchorTransferBatch* にインポートして、ルートゲームオブジェクトを同じ物理的な場所にロックすることができます。 注: インポートに失敗する場合があり、再試行が必要になることがあります。

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

*WorldAnchor* *オブジェクト* は、 *lockobject* 呼び出しによってロックされた後に、世界の同じ物理的な位置に保持されますが、Unity 座標空間内の他のユーザーとは異なる場所にある可能性があります。

