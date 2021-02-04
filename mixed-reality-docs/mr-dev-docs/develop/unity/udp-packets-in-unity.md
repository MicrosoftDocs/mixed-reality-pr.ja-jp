---
title: Unity UWP アプリの UDP パケット
description: セキュリティで保護されたネットワーク経由で UDP パケットを送受信するように Unity UWP アプリを設定する方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP、UWP、Unity、UDP パケット、ソケット、クライアントサーバー、エンドポイント、ネットワーク、リモートコンピューター、datagramsocket、サンプル、.net
ms.openlocfilehash: e4fbdc12a1f7fbca44e14f6ace89ef791a09608f
ms.sourcegitcommit: 8647702638f7600c51df1d89d76c761b52bdf0d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2021
ms.locfileid: "99566979"
---
# <a name="udp-packets-in-unity-uwp-apps"></a>Unity UWP アプリの UDP パケット

Udp ソケットクライアントとサーバーを使用して UDP パケットを受信するようにユニバーサル Windows プラットフォーム (UWP) Unity アプリを設定できます。 UDP ソケットは両方のエンドポイントで接続を維持しないため、リモートコンピューター間のネットワークのための高速でシンプルなソリューションです。 ただし、パケットが宛先に到達したかどうかを確認する必要があります。これは UDP ソケットによって自動的に行われないためです。

## <a name="setup"></a>セットアップ

ファイルでプロジェクト HoloLens manifest.jsを開き、が有効になっていることを確認します。
* **インターネット (クライアント & サーバー)** 
* **プライベートネットワーク (クライアント & サーバー)**。

## <a name="build-your-socket-client-and-server"></a>ソケットのクライアントとサーバーを作成する 

[基本的な UDP ソケットクライアントとサーバーを構築](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server)するための手順に従います。 [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket)クラスを使用して UDP 経由でデータを送受信し、エコークライアントとサーバーを形成します。 また、カスタマイズされた複雑なユースケースに適用されるため、この記事の他のリソースセクションを読むことをお勧めします。 

> [!IMPORTANT]
> PC から PC への UDP パケットの送信に問題がある場合は、ネットワークでこれらの操作が許可されていることを確認してください。 ネットワークが UDP パケットを何らかの方法でブロックしている場合、HoloLens デバイスはそれらをリッスンできません。

次のリンクから、完全な DatagramSocket UDP サンプルアプリをダウンロードできます。

> [!div class="nextstepaction"]
> [ツールのインストール](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>関連項目 
* [共有ホログラムと Azure Blob Storage/UDP マルチキャストを使用した実験](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)