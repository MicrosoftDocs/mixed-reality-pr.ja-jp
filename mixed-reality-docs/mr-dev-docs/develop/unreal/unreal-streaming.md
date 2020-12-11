---
title: Unreal でのストリーミング
description: Unreal での HoloLens 2 へのストリーミングに関するガイド
author: sw5813
ms.author: suwu
ms.date: 7/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, ストリーミング, PC, ホログラフィック アプリのリモート処理, Holographic Remoting Player, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: 9cbde33ce7238d704d4b24b4afbed9d8306d4e4d
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609333"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="cd3e3-104">Unreal でのストリーミング</span><span class="sxs-lookup"><span data-stu-id="cd3e3-104">Streaming in Unreal</span></span>

<span data-ttu-id="cd3e3-105">PC から HoloLens にストリーミングを行うことには、次の 2 つの大きな利点があります。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-105">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="cd3e3-106">Mixed Reality アプリで PC の演算性能を活用できる。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-106">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="cd3e3-107">開発のイテレーション時間を短縮できる。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-107">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="cd3e3-108">最初に、[Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) を HoloLens デバイスにダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-108">To get started, you'll need to download the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="cd3e3-109">Holographic Remoting Player を使用すると、アプリで次のソースから HoloLens 上のリモート処理プレーヤーに直接ストリーミングできるようになります。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-109">The Holographic Remoting Player lets your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="cd3e3-110">Unreal Engine エディター</span><span class="sxs-lookup"><span data-stu-id="cd3e3-110">The Unreal Engine editor</span></span>
* <span data-ttu-id="cd3e3-111">パッケージ化された Windows 実行可能ファイル</span><span class="sxs-lookup"><span data-stu-id="cd3e3-111">A packaged Windows executable</span></span> 

<span data-ttu-id="cd3e3-112">ストリーミング時には、アプリケーションをデバイス上で実行する場合と同じ HoloLens の機能をほぼすべて利用できます。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-112">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="cd3e3-113">これには、[ハンド ジョイント トラッキング](unreal-hand-tracking.md) (HoloLens 2 を使用している場合)、[空間マッピング](unreal-spatial-mapping.md)、[空間アンカー](unreal-spatial-anchors.md)などが含まれます。ただし、こちらの[一覧](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md)に記載されている機能は含まれません。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-113">This includes [hand joint tracking](unreal-hand-tracking.md) if you're on a HoloLens 2, [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="cd3e3-114">ストリーミング品質は、ユーザーの Wi-Fi ネットワークの強度に大きく依存します。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-114">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="cd3e3-115">Holographic Remoting Player では、すべての機能が自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-115">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="cd3e3-116">ユーザーのアクセス許可が必要な機能 (例: 視線追跡) がストリーミングでは機能しているものの、デバイスでの実行では機能していない場合、プロジェクト設定で適切な機能を有効にしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-116">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

## <a name="device-support"></a><span data-ttu-id="cd3e3-117">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="cd3e3-117">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="cd3e3-118"><strong>ソース</strong></span><span class="sxs-lookup"><span data-stu-id="cd3e3-118"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="cd3e3-119"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 第 1 世代</strong></a></span><span class="sxs-lookup"><span data-stu-id="cd3e3-119"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="cd3e3-120"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="cd3e3-120"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="cd3e3-121"><strong>イマーシブ ヘッドセット</strong></span><span class="sxs-lookup"><span data-stu-id="cd3e3-121"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="cd3e3-122">Unreal エディター</span><span class="sxs-lookup"><span data-stu-id="cd3e3-122">Unreal editor</span></span></td>
        <td><span data-ttu-id="cd3e3-123">✔️</span><span class="sxs-lookup"><span data-stu-id="cd3e3-123">✔️</span></span></td>
        <td><span data-ttu-id="cd3e3-124">✔️</span><span class="sxs-lookup"><span data-stu-id="cd3e3-124">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="cd3e3-125">Windows パッケージ</span><span class="sxs-lookup"><span data-stu-id="cd3e3-125">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="cd3e3-126">✔️</span><span class="sxs-lookup"><span data-stu-id="cd3e3-126">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="cd3e3-127">Unreal エディターからのストリーミング</span><span class="sxs-lookup"><span data-stu-id="cd3e3-127">Streaming from the Unreal editor</span></span>

<span data-ttu-id="cd3e3-128">開発者にとって、Unreal エディターから HoloLens デバイスへのストリーミングには、テスト時に大きなメリットがあります。更新プログラムをテストする前に、アプリのビルドとデプロイを待機する必要がなくなるからです。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-128">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides significant benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="cd3e3-129">[ エディターからのストリーミング](tutorials/unreal-uxt-ch6.md#device-only-streaming)の詳細な手順は、チュートリアル シリーズでわかります。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-129">You can find detailed instructions for [streaming from the Unreal editor](tutorials/unreal-uxt-ch6.md#device-only-streaming) in our tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="cd3e3-130">パッケージ化された Windows 実行可能ファイルからのストリーミング</span><span class="sxs-lookup"><span data-stu-id="cd3e3-130">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="cd3e3-131">Unreal 4.25.1 以降では、パッケージ化された Windows 実行可能ファイルから HoloLens 2 デバイスにアプリをストリーミングできます。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-131">In Unreal 4.25.1 and onwards, you can stream your app to a HoloLens 2 device from a packaged Windows executable:</span></span> 

1. <span data-ttu-id="cd3e3-132">エディター メニューで、 **[ファイル] > [パッケージ プロジェクト] > [Windows]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-132">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="cd3e3-133">パッケージを保存する場所を選択し、 **[Select Folder]\(フォルダーの選択\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-133">Choose a location to save your package and select **Select Folder**.</span></span>

2. <span data-ttu-id="cd3e3-134">パッケージのビルドが完了したら、HoloLens 2 で **Holographic Remoting Player** を開き、IP アドレスをメモします。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-134">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="cd3e3-135">**Holographic Remoting Player** を開いたままにして、コマンド ライン プロンプトで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-135">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="cd3e3-136">cd を実行し、パッケージを保存したローカル ディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-136">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="cd3e3-137">次のコマンドを入力します。```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span><span class="sxs-lookup"><span data-stu-id="cd3e3-137">Enter the following command: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span></span>

> [!NOTE]
> <span data-ttu-id="cd3e3-138">プロジェクト設定に含まれるアプリケーション名が、Windows パッケージを作成するために自動的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-138">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="cd3e3-139">何らかの理由でこれらが異なる場合は、コマンド プロンプトで Windows 実行可能ファイル名を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-139">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="cd3e3-140">Enter キーを押すと、アプリケーションのストリーミングが開始します。</span><span class="sxs-lookup"><span data-stu-id="cd3e3-140">Hit enter and watch your application start streaming!</span></span>

## <a name="see-also"></a><span data-ttu-id="cd3e3-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd3e3-141">See also</span></span>

* [<span data-ttu-id="cd3e3-142">Holographic リモート処理のバージョン履歴</span><span class="sxs-lookup"><span data-stu-id="cd3e3-142">Holographic remoting version history</span></span>](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [<span data-ttu-id="cd3e3-143">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="cd3e3-143">Writing a custom Holographic Remoting player app</span></span>](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [<span data-ttu-id="cd3e3-144">Holographic Remoting を使用したセキュリティで保護された接続の確立</span><span class="sxs-lookup"><span data-stu-id="cd3e3-144">Establishing a secure connection with Holographic Remoting</span></span>](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)
