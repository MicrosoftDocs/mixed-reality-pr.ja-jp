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
ms.openlocfilehash: 5a001088208106176ae771c2bc684674e6ce37a8
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679781"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="79448-104">Unreal でのストリーミング</span><span class="sxs-lookup"><span data-stu-id="79448-104">Streaming in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="79448-105">概要</span><span class="sxs-lookup"><span data-stu-id="79448-105">Overview</span></span>
<span data-ttu-id="79448-106">PC から HoloLens にストリーミングを行うことには、次の 2 つの大きな利点があります。</span><span class="sxs-lookup"><span data-stu-id="79448-106">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="79448-107">Mixed Reality アプリで PC の演算性能を活用できる。</span><span class="sxs-lookup"><span data-stu-id="79448-107">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="79448-108">開発のイテレーション時間を短縮できる。</span><span class="sxs-lookup"><span data-stu-id="79448-108">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="79448-109">最初に、[Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) を HoloLens デバイスにダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="79448-109">To get started, you'll need to download the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="79448-110">これにより、アプリを使って、次のソースから HoloLens 上のリモート処理プレーヤーに直接ストリーミングできるようになります。</span><span class="sxs-lookup"><span data-stu-id="79448-110">This allows your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="79448-111">Unreal Engine エディター</span><span class="sxs-lookup"><span data-stu-id="79448-111">The Unreal Engine editor</span></span>
* <span data-ttu-id="79448-112">パッケージ化された Windows 実行可能ファイル</span><span class="sxs-lookup"><span data-stu-id="79448-112">A packaged Windows executable</span></span> 

<span data-ttu-id="79448-113">ストリーミング時には、アプリケーションをデバイス上で実行する場合と同じ HoloLens の機能をほぼすべて利用できます。</span><span class="sxs-lookup"><span data-stu-id="79448-113">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="79448-114">これには、[ハンド ジョイント トラッキング](unreal-hand-tracking.md) (HoloLens 2 を使用している場合)、[空間マッピング](unreal-spatial-mapping.md)、[空間アンカー](unreal-spatial-anchors.md)などが含まれます。ただし、この[制限事項の一覧](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md)に記載されている機能は含まれません。</span><span class="sxs-lookup"><span data-stu-id="79448-114">This includes [hand joint tracking](unreal-hand-tracking.md) (if you're on a HoloLens 2), [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list of limitations](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="79448-115">ストリーミング品質は、ユーザーの Wi-Fi ネットワークの強度に大きく依存します。</span><span class="sxs-lookup"><span data-stu-id="79448-115">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="79448-116">Holographic Remoting Player では、すべての機能が自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="79448-116">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="79448-117">ユーザーのアクセス許可が必要な機能 (例: 視線追跡) がストリーミングでは機能しているものの、デバイスでの実行では機能していない場合、プロジェクト設定で適切な機能を有効にしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="79448-117">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

## <a name="device-support"></a><span data-ttu-id="79448-118">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="79448-118">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="79448-119"><strong>ソース</strong></span><span class="sxs-lookup"><span data-stu-id="79448-119"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="79448-120"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="79448-120"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 1st Gen</strong></a></span></span></td>
        <td><span data-ttu-id="79448-121"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="79448-121"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="79448-122"><strong>イマーシブ ヘッドセット</strong></span><span class="sxs-lookup"><span data-stu-id="79448-122"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="79448-123">Unreal エディター</span><span class="sxs-lookup"><span data-stu-id="79448-123">Unreal editor</span></span></td>
        <td><span data-ttu-id="79448-124">✔️</span><span class="sxs-lookup"><span data-stu-id="79448-124">✔️</span></span></td>
        <td><span data-ttu-id="79448-125">✔️</span><span class="sxs-lookup"><span data-stu-id="79448-125">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="79448-126">Windows パッケージ</span><span class="sxs-lookup"><span data-stu-id="79448-126">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="79448-127">✔️</span><span class="sxs-lookup"><span data-stu-id="79448-127">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="79448-128">Unreal エディターからのストリーミング</span><span class="sxs-lookup"><span data-stu-id="79448-128">Streaming from the Unreal editor</span></span>

<span data-ttu-id="79448-129">開発者にとって、Unreal エディターから HoloLens デバイスへのストリーミングには、テスト時に大きなメリットがあります。更新プログラムをテストする前に、アプリのビルドとデプロイを待機する必要がなくなるからです。</span><span class="sxs-lookup"><span data-stu-id="79448-129">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides big benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="79448-130">[Unreal エディターからのストリーミング](tutorials/unreal-uxt-ch6.md#device-only-streaming)については、Unreal の概要に関するチュートリアル シリーズの最後のセクションに詳細な説明があります。</span><span class="sxs-lookup"><span data-stu-id="79448-130">You can find detailed instructions on [streaming from the Unreal editor](tutorials/unreal-uxt-ch6.md#device-only-streaming) in the last section of the Getting Started with Unreal tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="79448-131">パッケージ化された Windows 実行可能ファイルからのストリーミング</span><span class="sxs-lookup"><span data-stu-id="79448-131">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="79448-132">Unreal 4.25.1 では、以下に示す手順で、パッケージ化された Windows 実行可能ファイルから HoloLens 2 デバイスにアプリをストリーミングできます。</span><span class="sxs-lookup"><span data-stu-id="79448-132">As of Unreal 4.25.1, you can stream your app to a HoloLens 2 device from a packaged Windows executable by following the steps below:</span></span> 

1. <span data-ttu-id="79448-133">エディター メニューで、 **[ファイル] > [パッケージ プロジェクト] > [Windows]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="79448-133">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="79448-134">パッケージを保存する場所を選択し、 **[Select Folder]\(フォルダーの選択\)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79448-134">Choose a location to save your package and click **Select Folder**.</span></span>

2. <span data-ttu-id="79448-135">パッケージのビルドが完了したら、HoloLens 2 で **Holographic Remoting Player** を開き、IP アドレスをメモします。</span><span class="sxs-lookup"><span data-stu-id="79448-135">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="79448-136">**Holographic Remoting Player** を開いたままにして、コマンド ライン プロンプトで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="79448-136">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="79448-137">cd を実行し、パッケージを保存したローカル ディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="79448-137">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="79448-138">次のコマンドを入力します。```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span><span class="sxs-lookup"><span data-stu-id="79448-138">Enter the following command: ```<App Name>.exe -vr -HoloLensRemoting=<IP Address>```</span></span>

> [!NOTE]
> <span data-ttu-id="79448-139">プロジェクト設定に含まれるアプリケーション名が、Windows パッケージを作成するために自動的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="79448-139">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="79448-140">何らかの理由でこれらが異なる場合は、コマンド プロンプトで Windows 実行可能ファイル名を使用します。</span><span class="sxs-lookup"><span data-stu-id="79448-140">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="79448-141">Enter キーを押すと、アプリケーションのストリーミングが開始します。</span><span class="sxs-lookup"><span data-stu-id="79448-141">Hit enter and watch your application start streaming!</span></span>

## <a name="see-also"></a><span data-ttu-id="79448-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="79448-142">See also</span></span>
* [<span data-ttu-id="79448-143">Holographic リモート処理のバージョン履歴</span><span class="sxs-lookup"><span data-stu-id="79448-143">Holographic remoting version history</span></span>](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [<span data-ttu-id="79448-144">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="79448-144">Writing a custom Holographic Remoting player app</span></span>](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [<span data-ttu-id="79448-145">Holographic Remoting を使用したセキュリティで保護された接続の確立</span><span class="sxs-lookup"><span data-stu-id="79448-145">Establishing a secure connection with Holographic Remoting</span></span>](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)
