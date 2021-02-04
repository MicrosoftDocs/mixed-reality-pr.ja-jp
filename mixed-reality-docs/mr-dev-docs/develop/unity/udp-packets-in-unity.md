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
# <a name="udp-packets-in-unity-uwp-apps"></a><span data-ttu-id="ae09f-104">Unity UWP アプリの UDP パケット</span><span class="sxs-lookup"><span data-stu-id="ae09f-104">UDP packets in Unity UWP apps</span></span>

<span data-ttu-id="ae09f-105">Udp ソケットクライアントとサーバーを使用して UDP パケットを受信するようにユニバーサル Windows プラットフォーム (UWP) Unity アプリを設定できます。</span><span class="sxs-lookup"><span data-stu-id="ae09f-105">You can setup your Universal Windows Platform (UWP) Unity apps to receive UDP packets with the help of a UDP socket client and server.</span></span> <span data-ttu-id="ae09f-106">UDP ソケットは両方のエンドポイントで接続を維持しないため、リモートコンピューター間のネットワークのための高速でシンプルなソリューションです。</span><span class="sxs-lookup"><span data-stu-id="ae09f-106">UDP sockets don't maintain connection on both endpoints, so they're a fast and simple solution for networking between remote machines.</span></span> <span data-ttu-id="ae09f-107">ただし、パケットが宛先に到達したかどうかを確認する必要があります。これは UDP ソケットによって自動的に行われないためです。</span><span class="sxs-lookup"><span data-stu-id="ae09f-107">However, you'll be responsible for checking if the packets get to their destination, as UDP sockets don't do that automatically.</span></span>

## <a name="setup"></a><span data-ttu-id="ae09f-108">セットアップ</span><span class="sxs-lookup"><span data-stu-id="ae09f-108">Setup</span></span>

<span data-ttu-id="ae09f-109">ファイルでプロジェクト HoloLens manifest.jsを開き、が有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ae09f-109">Open your projects HoloLens manifest.json file and make sure you've enabled:</span></span>
* <span data-ttu-id="ae09f-110">**インターネット (クライアント & サーバー)**</span><span class="sxs-lookup"><span data-stu-id="ae09f-110">**Internet (Client & Server)**</span></span> 
* <span data-ttu-id="ae09f-111">**プライベートネットワーク (クライアント & サーバー)**。</span><span class="sxs-lookup"><span data-stu-id="ae09f-111">**Private Networks (Client & Server)**.</span></span>

## <a name="build-your-socket-client-and-server"></a><span data-ttu-id="ae09f-112">ソケットのクライアントとサーバーを作成する</span><span class="sxs-lookup"><span data-stu-id="ae09f-112">Build your socket client and server</span></span> 

<span data-ttu-id="ae09f-113">[基本的な UDP ソケットクライアントとサーバーを構築](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server)するための手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ae09f-113">Follow the instructions for [building a basic UDP socket client and server](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span></span> <span data-ttu-id="ae09f-114">[DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket)クラスを使用して UDP 経由でデータを送受信し、エコークライアントとサーバーを形成します。</span><span class="sxs-lookup"><span data-stu-id="ae09f-114">You'll be using the [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) class to send and receive data over UDP and form an echo client and server.</span></span> <span data-ttu-id="ae09f-115">また、カスタマイズされた複雑なユースケースに適用されるため、この記事の他のリソースセクションを読むことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ae09f-115">We also recommend reading through the other resource sections in this article, as they apply to more customized and complex use cases.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="ae09f-116">PC から PC への UDP パケットの送信に問題がある場合は、ネットワークでこれらの操作が許可されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ae09f-116">If you're having trouble sending UDP packets from PC to PC, check that your network allows these operations.</span></span> <span data-ttu-id="ae09f-117">ネットワークが UDP パケットを何らかの方法でブロックしている場合、HoloLens デバイスはそれらをリッスンできません。</span><span class="sxs-lookup"><span data-stu-id="ae09f-117">If your network is blocking the UDP packets in any way, your HoloLens device won't be able to listen for them.</span></span>

<span data-ttu-id="ae09f-118">次のリンクから、完全な DatagramSocket UDP サンプルアプリをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="ae09f-118">You can download a complete DatagramSocket UDP sample app from the link below:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ae09f-119">ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="ae09f-119">Install the tools</span></span>](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a><span data-ttu-id="ae09f-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae09f-120">See also</span></span> 
* [<span data-ttu-id="ae09f-121">共有ホログラムと Azure Blob Storage/UDP マルチキャストを使用した実験</span><span class="sxs-lookup"><span data-stu-id="ae09f-121">Experiments with Shared Holograms and Azure Blob Storage/UDP Multicasting</span></span>](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)