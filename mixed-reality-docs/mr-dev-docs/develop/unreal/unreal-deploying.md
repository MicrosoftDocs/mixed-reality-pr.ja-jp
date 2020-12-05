---
title: Unreal でのデバイスへのデプロイ
description: 非 Real から HoloLens 2 にデバイスを展開するためのガイド
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、mixed reality、デバイスへの展開、PC、ドキュメント、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
appliesto:
- HoloLens 2
ms.openlocfilehash: e811bc1b82aa40e658f9c855b65446483dd8bef2
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609433"
---
# <a name="deploy-to-device-in-unreal"></a>Unreal でのデバイスへのデプロイ

HoloLens 2 に Unreal アプリケーションを展開するには、次の2つの方法があります。
* Unreal エディターから直接
* デバイスポータルを使用してアップロードされたパッケージとして

どちらのオプションでも、開発用の [デバイスポータル](../platform-capabilities-and-apis/using-the-windows-device-portal.md) を使用するように HoloLens を設定する必要があります。

## <a name="deploying-to-device-from-the-unreal-editor"></a>Unreal エディターからデバイスへの配置

1. [ **起動** ] ボタンの横にあるドロップダウン矢印を選択します。 最初は、HoloLens デバイスオプションが淡色表示になります。

![起動ドロップダウンオプション](images/unreal/launch-dropdown.png)

2. **デバイスマネージャー** を開くと、HoloLens がデバイスの一覧に自動的に表示されないことに注意してください。

3. [ **一覧にないデバイスの追加** ] セクションを展開します。

4. **プラットフォーム** として **HoloLens** を選択します。

5. デバイスの IP アドレスとポート情報を、デバイス id としてコロンで区切って入力します。 たとえば、"127.0.0.1: 10080" (USB 経由で接続されている場合) などです。 デバイスポータルのユーザー名とパスワードの資格情報を使用します。

6. [ **追加** ] をクリックし、デバイスマネージャーを閉じます。
    * 間違ったアドレスやユーザー資格情報などのエラーが発生すると、メッセージが出力ログに出力されます。

![一覧にないデバイスの追加](images/unreal/add-unlisted-device.png)

7. [ **起動** ] ボタンの横にあるドロップダウン矢印をクリックすると、追加した HoloLens デバイスが表示されます。 Hololens にビルドしてデプロイする HoloLens デバイスを選択します。

>[!NOTE]
>デバイスのビルドには、シェーダーの再コンパイルが含まれる場合があります (特に最初の実行時)。これには時間がかかることがあります。 デバイスは、アプリが実行されるまでスリープ状態にならないようにしてください (磨耗が必要な場合があります)。 それ以外の場合、シェーダーのコンパイルは失敗します。

## <a name="deploying-to-device-via-device-portal"></a>デバイスポータルを使用したデバイスへの展開

アプリのパッケージ化とデプロイに関する詳細な手順については、 [Unreal チュートリアルシリーズ](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)を参照してください。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

デプロイの準備が完了していない場合は、デプロイ段階の途中で作業しています。 ここから、高度なサービスの追加を続けることができます。

> [!div class="nextstepaction"]
> [高度なサービス](unreal-development-overview.md#5-adding-services)

いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#4-streaming-and-deploying-to-a-device)に戻ることができます。
