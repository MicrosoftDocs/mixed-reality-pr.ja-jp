---
title: Unreal でのストリーミング
description: ストリーミングの制限やコマンド ライン オプションなど、Unreal アプリを HoloLens 2 にストリーム配信する方法について説明します。
author: sw5813
ms.author: suwu
ms.date: 12/7/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, ストリーミング, PC, ホログラフィック アプリのリモート処理, Holographic Remoting Player, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
appliesto:
- HoloLens
- HoloLens 2
ms.openlocfilehash: bbae1170850ec4bbb41bc9274223d19102adddae
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580333"
---
# <a name="streaming-in-unreal"></a><span data-ttu-id="91451-104">Unreal でのストリーミング</span><span class="sxs-lookup"><span data-stu-id="91451-104">Streaming in Unreal</span></span>

<span data-ttu-id="91451-105">PC から HoloLens にストリーミングを行うことには、次の 2 つの大きな利点があります。</span><span class="sxs-lookup"><span data-stu-id="91451-105">Streaming from a PC to HoloLens provides two major advantages:</span></span> 
* <span data-ttu-id="91451-106">Mixed Reality アプリで PC の演算性能を活用できる。</span><span class="sxs-lookup"><span data-stu-id="91451-106">It lets your mixed reality app take advantage of your PCs computational power.</span></span> 
* <span data-ttu-id="91451-107">開発のイテレーション時間を短縮できる。</span><span class="sxs-lookup"><span data-stu-id="91451-107">It helps speed up development iteration time.</span></span> 

<span data-ttu-id="91451-108">最初に、[Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) を HoloLens デバイスにダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="91451-108">To get started, you'll need to download the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) to your HoloLens device.</span></span> <span data-ttu-id="91451-109">Holographic Remoting Player を使用すると、アプリで次のソースから HoloLens 上のリモート処理プレーヤーに直接ストリーミングできるようになります。</span><span class="sxs-lookup"><span data-stu-id="91451-109">The Holographic Remoting Player lets your app to stream  directly to the remoting player on your HoloLens from the following sources:</span></span>

* <span data-ttu-id="91451-110">Unreal Engine エディター</span><span class="sxs-lookup"><span data-stu-id="91451-110">The Unreal Engine editor</span></span>
* <span data-ttu-id="91451-111">パッケージ化された Windows 実行可能ファイル</span><span class="sxs-lookup"><span data-stu-id="91451-111">A packaged Windows executable</span></span> 

<span data-ttu-id="91451-112">ストリーミング時には、アプリケーションをデバイス上で実行する場合と同じ HoloLens の機能をほぼすべて利用できます。</span><span class="sxs-lookup"><span data-stu-id="91451-112">When streaming, you have access to almost all of the same HoloLens capabilities as you would when running an application on a device.</span></span> <span data-ttu-id="91451-113">これには、[ハンド ジョイント トラッキング](unreal-hand-tracking.md) (HoloLens 2 を使用している場合)、[空間マッピング](unreal-spatial-mapping.md)、[空間アンカー](unreal-spatial-anchors.md)などが含まれます。ただし、こちらの[一覧](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md)に記載されている機能は含まれません。</span><span class="sxs-lookup"><span data-stu-id="91451-113">This includes [hand joint tracking](unreal-hand-tracking.md) if you're on a HoloLens 2, [spatial mapping](unreal-spatial-mapping.md), and [spatial anchors](unreal-spatial-anchors.md), but leaves out the features on this [list](../platform-capabilities-and-apis/holographic-remoting-troubleshooting.md).</span></span> 

> [!NOTE]
> * <span data-ttu-id="91451-114">ストリーミング品質は、ユーザーの Wi-Fi ネットワークの強度に大きく依存します。</span><span class="sxs-lookup"><span data-stu-id="91451-114">Streaming quality is highly dependent on the strength of your wifi network.</span></span>
> * <span data-ttu-id="91451-115">Holographic Remoting Player では、すべての機能が自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="91451-115">All capabilities are automatically enabled for the holographic remoting player.</span></span> <span data-ttu-id="91451-116">ユーザーのアクセス許可が必要な機能 (例: 視線追跡) がストリーミングでは機能しているものの、デバイスでの実行では機能していない場合、プロジェクト設定で適切な機能を有効にしていることをご確認ください。</span><span class="sxs-lookup"><span data-stu-id="91451-116">If you find a capability that requires user permission (ex: eye tracking) to be working over streaming but not when running on device, check to ensure you've enabled the proper capabilities under your project settings.</span></span>

### <a name="streaming-limitations"></a><span data-ttu-id="91451-117">ストリーミングの制限事項</span><span class="sxs-lookup"><span data-stu-id="91451-117">Streaming limitations</span></span>

<span data-ttu-id="91451-118">ストリーミングには、ハンド メッシュ、HoloLens カメラ、およびシステム キーボードを使用できません。</span><span class="sxs-lookup"><span data-stu-id="91451-118">Hand meshes, the HoloLens camera, and the system keyboard are unavailable over streaming.</span></span> <span data-ttu-id="91451-119">ストリーミングされたアプリの音声入力は、ストリーミング元の PC のマイクを介して取得できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="91451-119">Note that speech input for streamed apps can be acquired via the microphone of the PC you are streaming from.</span></span>

#### <a name="openxr"></a><span data-ttu-id="91451-120">OpenXR</span><span class="sxs-lookup"><span data-stu-id="91451-120">OpenXR</span></span>

<span data-ttu-id="91451-121">OpenXR で実行されている Unreal 4.26 では、Holographic Remoting Player のバージョン 2.4.0 以降へのストリーミングがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="91451-121">Unreal 4.26 running on OpenXR supports streaming to versions 2.4.0+ of the Holographic Remoting Player.</span></span> <span data-ttu-id="91451-122">2\.4.0 の OpenXR ストリーミングの場合、空間マッピングと空間アンカーがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="91451-122">OpenXR streaming in 2.4.0 is missing support for spatial mapping and spatial anchors.</span></span> 

## <a name="device-support"></a><span data-ttu-id="91451-123">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="91451-123">Device support</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="91451-124"><strong>ソース</strong></span><span class="sxs-lookup"><span data-stu-id="91451-124"><strong>Source</strong></span></span></td>
        <td><span data-ttu-id="91451-125"><a href="/hololens/hololens1-hardware"><strong>HoloLens 第 1 世代</strong></a></span><span class="sxs-lookup"><span data-stu-id="91451-125"><a href="/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="91451-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="91451-126"><a href="https://www.microsoft.com/hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="91451-127"><strong>イマーシブ ヘッドセット</strong></span><span class="sxs-lookup"><span data-stu-id="91451-127"><strong>Immersive Headsets</strong></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="91451-128">Unreal エディター</span><span class="sxs-lookup"><span data-stu-id="91451-128">Unreal editor</span></span></td>
        <td><span data-ttu-id="91451-129">✔️</span><span class="sxs-lookup"><span data-stu-id="91451-129">✔️</span></span></td>
        <td><span data-ttu-id="91451-130">✔️</span><span class="sxs-lookup"><span data-stu-id="91451-130">✔️</span></span></td>
        <td>❌</td>
    </tr>
    <tr>
        <td><span data-ttu-id="91451-131">Windows パッケージ</span><span class="sxs-lookup"><span data-stu-id="91451-131">Windows package</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="91451-132">✔️</span><span class="sxs-lookup"><span data-stu-id="91451-132">✔️</span></span></td>
        <td>❌</td>
    </tr>

</table>

## <a name="streaming-from-the-unreal-editor"></a><span data-ttu-id="91451-133">Unreal エディターからのストリーミング</span><span class="sxs-lookup"><span data-stu-id="91451-133">Streaming from the Unreal editor</span></span>

<span data-ttu-id="91451-134">開発者にとって、Unreal エディターから HoloLens デバイスへのストリーミングには、テスト時に大きなメリットがあります。更新プログラムをテストする前に、アプリのビルドとデプロイを待機する必要がなくなるからです。</span><span class="sxs-lookup"><span data-stu-id="91451-134">As a developer, you'll find that streaming from the Unreal editor to your HoloLens device provides significant benefits when testing, namely that you no longer have to wait for your app to build and deploy before trying out your updates.</span></span>

<span data-ttu-id="91451-135">[ エディターからのストリーミング](tutorials/unreal-uxt-ch6.md#device-only-streaming)の詳細な手順は、チュートリアル シリーズでわかります。</span><span class="sxs-lookup"><span data-stu-id="91451-135">You can find detailed instructions for [streaming from the Unreal editor](tutorials/unreal-uxt-ch6.md#device-only-streaming) in our tutorial series.</span></span>

## <a name="streaming-from-a-packaged-windows-executable"></a><span data-ttu-id="91451-136">パッケージ化された Windows 実行可能ファイルからのストリーミング</span><span class="sxs-lookup"><span data-stu-id="91451-136">Streaming from a packaged Windows executable</span></span>

<span data-ttu-id="91451-137">Unreal 4.25.1 以降では、パッケージ化された Windows 実行可能ファイルから HoloLens 2 デバイスにアプリをストリーミングできます。</span><span class="sxs-lookup"><span data-stu-id="91451-137">In Unreal 4.25.1 and onwards, you can stream your app to a HoloLens 2 device from a packaged Windows executable:</span></span> 

1. <span data-ttu-id="91451-138">エディター メニューで、 **[ファイル] > [パッケージ プロジェクト] > [Windows]** の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="91451-138">Go to **File > Package Project > Windows** in the editor menu.</span></span> 
    * <span data-ttu-id="91451-139">パッケージを保存する場所を選択し、 **[Select Folder]\(フォルダーの選択\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="91451-139">Choose a location to save your package and select **Select Folder**.</span></span>

2. <span data-ttu-id="91451-140">パッケージのビルドが完了したら、HoloLens 2 で **Holographic Remoting Player** を開き、IP アドレスをメモします。</span><span class="sxs-lookup"><span data-stu-id="91451-140">Once the package has finished building, open the **Holographic Remoting Player** on your HoloLens 2 and make note of the IP Address.</span></span> 
3. <span data-ttu-id="91451-141">**Holographic Remoting Player** を開いたままにして、コマンド ライン プロンプトで次を実行します。</span><span class="sxs-lookup"><span data-stu-id="91451-141">Leave the **Holographic Remoting Player** open and use the command line prompt to:</span></span> 
    * <span data-ttu-id="91451-142">cd を実行し、パッケージを保存したローカル ディレクトリに移動します。</span><span class="sxs-lookup"><span data-stu-id="91451-142">cd into the local directory where you saved your package.</span></span>
    * <span data-ttu-id="91451-143">次のコマンドを入力します。`<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span><span class="sxs-lookup"><span data-stu-id="91451-143">Enter the following command: `<App Name>.exe -vr -HoloLensRemoting=<IP Address>`</span></span>

> [!NOTE]
> <span data-ttu-id="91451-144">プロジェクト設定に含まれるアプリケーション名が、Windows パッケージを作成するために自動的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="91451-144">The application name in your project settings should be automatically used to create the Windows package.</span></span> <span data-ttu-id="91451-145">何らかの理由でこれらが異なる場合は、コマンド プロンプトで Windows 実行可能ファイル名を使用します。</span><span class="sxs-lookup"><span data-stu-id="91451-145">If these are different for some reason, use the Windows executable name in the command prompt.</span></span>

<span data-ttu-id="91451-146">Enter キーを押すと、アプリケーションのストリーミングが開始します。</span><span class="sxs-lookup"><span data-stu-id="91451-146">Hit enter and watch your application start streaming!</span></span>

### <a name="command-line-options"></a><span data-ttu-id="91451-147">コマンド ライン オプション</span><span class="sxs-lookup"><span data-stu-id="91451-147">Command line options</span></span>

<span data-ttu-id="91451-148">Unreal Engine 4.26 以降の各プラットフォームからストリーミングする場合のその他のコマンド ライン オプションを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="91451-148">Additional command line options for streaming from each platform in Unreal Engine 4.26+ can be found in the table below.</span></span> 

[!INCLUDE[](includes/tabs-streaming-args.md)]

## <a name="see-also"></a><span data-ttu-id="91451-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="91451-149">See also</span></span>

* [<span data-ttu-id="91451-150">Holographic リモート処理のバージョン履歴</span><span class="sxs-lookup"><span data-stu-id="91451-150">Holographic remoting version history</span></span>](../platform-capabilities-and-apis/holographic-remoting-version-history.md)
* [<span data-ttu-id="91451-151">カスタム Holographic リモート処理プレーヤーアプリの作成</span><span class="sxs-lookup"><span data-stu-id="91451-151">Writing a custom Holographic Remoting player app</span></span>](../platform-capabilities-and-apis/holographic-remoting-create-player.md)
* [<span data-ttu-id="91451-152">Holographic Remoting を使用したセキュリティで保護された接続の確立</span><span class="sxs-lookup"><span data-stu-id="91451-152">Establishing a secure connection with Holographic Remoting</span></span>](../platform-capabilities-and-apis/holographic-remoting-secure-connection.md)