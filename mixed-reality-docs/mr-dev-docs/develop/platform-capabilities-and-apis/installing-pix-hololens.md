---
title: HoloLens 2 用の PIX をインストールする
description: HoloLens 2 デバイス用の PIX をインストールする方法について説明します。
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens、HoloLens 2、PIX、capture、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: 5dfc16f97790b47af3c24ca44c060a9a2495a320
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530449"
---
# <a name="installing-pix-for-hololens-2"></a><span data-ttu-id="ea7fd-104">HoloLens 2 用の PIX をインストールする</span><span class="sxs-lookup"><span data-stu-id="ea7fd-104">Installing PIX for HoloLens 2</span></span>

<span data-ttu-id="ea7fd-105">[PIX](https://devblogs.microsoft.com/pix) は、Windows 上の DirectX 12 アプリケーション用のパフォーマンスチューニングおよびデバッグツールです。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-105">[PIX](https://devblogs.microsoft.com/pix) is a performance tuning and debugging tool for DirectX 12 applications on Windows.</span></span> 

## <a name="setup"></a><span data-ttu-id="ea7fd-106">セットアップ</span><span class="sxs-lookup"><span data-stu-id="ea7fd-106">Setup</span></span>

1. <span data-ttu-id="ea7fd-107">ホスト PC から最新の PIX [リリース]( https://devblogs.microsoft.com/pix/download) を入手し、USB ケーブル経由で HoloLens 2 を PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-107">Grab the latest PIX [release]( https://devblogs.microsoft.com/pix/download) from your host PC and connect your HoloLens 2 to your PC via a USB cable.</span></span>

2. <span data-ttu-id="ea7fd-108">HoloLens 2 が [Windows Insider ビルド](https://insider.windows.com) にある場合、または PIX を中断する構成がある場合は、  [デバイスを更新](https://docs.microsoft.com/hololens/hololens-recovery) してすべてのデータを消去します。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-108">If your HoloLens 2 is on a [Windows Insider build](https://insider.windows.com) or has a configuration that breaks PIX,  [reflash your device](https://docs.microsoft.com/hololens/hololens-recovery) to erase all data.</span></span>

3. <span data-ttu-id="ea7fd-109">**開発者モード** と **デバイスポータル** を有効にする:</span><span class="sxs-lookup"><span data-stu-id="ea7fd-109">Enable **Developer Mode** and **Device Portal**:</span></span>

* <span data-ttu-id="ea7fd-110">シェルから **設定** を開く:</span><span class="sxs-lookup"><span data-stu-id="ea7fd-110">Open **Settings** from Shell:</span></span>

![[設定] ボタンが強調表示されている HoloLens メニューのスクリーンショット](images/pix-img-01.jpg)

* <span data-ttu-id="ea7fd-112">[ **Update & Security**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-112">Select **Update & Security**:</span></span>

![[更新とセキュリティ] ボタンが強調表示されている HoloLens で開かれている [設定] ウィンドウのスクリーンショット](images/pix-img-02.jpg)

* <span data-ttu-id="ea7fd-114">**開発者向けの** 選択:</span><span class="sxs-lookup"><span data-stu-id="ea7fd-114">Select **For Developers**:</span></span>

![[開発者用に開く] ボタンが強調表示されている [セキュリティと更新プログラム] ウィンドウのスクリーンショット](images/pix-img-03.jpg)

* <span data-ttu-id="ea7fd-116">**開発者機能を使用** して **デバイスポータルを有効** にする</span><span class="sxs-lookup"><span data-stu-id="ea7fd-116">Turn on **Use Developer Features** and **Enable Device Portal**</span></span>

![[デバイスポータルを有効にする] ボタンが強調表示されている [設定] で開いている開発者ウィンドウのスクリーンショット](images/pix-img-04.jpg)

![[開発機能を使用して設定] で開いている開発者ウィンドウのスクリーンショットの表示/非表示](images/pix-img-05.jpg)

* <span data-ttu-id="ea7fd-119">デバイスが接続された状態で、ユーザーがログインした状態で、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-119">With the device still connected, awake, and with the user logged in, launch Visual Studio.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ea7fd-120">デバイスがスタンバイモードまたはスリープ状態になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-120">Make sure your device isn't in standby mode or asleep.</span></span> <span data-ttu-id="ea7fd-121">この手順で問題が発生した場合は、 [Windows デバイスポータルの手順](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-121">If you're having trouble with this step, refer to the [Windows Device Portal instructions](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span></span>

## <a name="preparing-for-deployment"></a><span data-ttu-id="ea7fd-122">展開の準備</span><span class="sxs-lookup"><span data-stu-id="ea7fd-122">Preparing for deployment</span></span>

1. <span data-ttu-id="ea7fd-123">Visual Studio で、 **ARM64** をデバイスとしてプラットフォームと **デバイス** として設定します。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-123">In Visual Studio, set **ARM64** as the platform and **Device** as the device:</span></span>

![プラットフォームとデバイスの設定が強調表示されている visual studio ソリューションのスクリーンショット](images/pix-img-06.png)

2. <span data-ttu-id="ea7fd-125">Visual Studio によって、デバイスからの **PIN** の入力が求められます。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-125">When Visual Studio prompts you for a **PIN** from the device:</span></span>

![PIN を要求する visual studio ポップアップのスクリーンショット](images/pix-img-07.png)

* <span data-ttu-id="ea7fd-127">シェルから **設定** を選択する</span><span class="sxs-lookup"><span data-stu-id="ea7fd-127">Select **Settings** from Shell</span></span>
* <span data-ttu-id="ea7fd-128">**更新プログラム & セキュリティ** を選択する</span><span class="sxs-lookup"><span data-stu-id="ea7fd-128">Select **Update & Security**</span></span>
* <span data-ttu-id="ea7fd-129">[**デバイスの検出**] で [**開発者**] を選択し、[ペア] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-129">Select **For Developers** and press Pair under **Device Discovery**</span></span> 

![デバイス検出が強調表示されている [設定] で開いている開発者ウィンドウのスクリーンショット](images/pix-img-08.jpg)

![登録コードが強調表示されている、有料デバイスのポップアップのスクリーンショット](images/pix-img-09.jpg)

* <span data-ttu-id="ea7fd-132">Visual Studio で生成された PIN 番号を入力します</span><span class="sxs-lookup"><span data-stu-id="ea7fd-132">Enter the generated PIN number in Visual Studio</span></span>

3. <span data-ttu-id="ea7fd-133">Visual Studio は接続されている HoloLens 2 にアプリをデプロイします。アプリによっては数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-133">Visual Studio will deploy the app to the connected HoloLens 2, which may take a few minutes depending on the app.</span></span>

## <a name="launching-pix"></a><span data-ttu-id="ea7fd-134">PIX の起動</span><span class="sxs-lookup"><span data-stu-id="ea7fd-134">Launching PIX</span></span>

<span data-ttu-id="ea7fd-135">まず、デバイスポータルを使用して、HoloLens 2 でアプリが実行されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-135">First, use Device Portal to verify the app isn't running on the HoloLens 2.</span></span> <span data-ttu-id="ea7fd-136">次に、PIX を起動してデバイスに接続し、[ **ホーム**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-136">Then, launch PIX, connect to your device, and select **Home**:</span></span>

![PIX アプリケーションのホーム画面のスクリーンショット](images/pix-img-10.png)

* <span data-ttu-id="ea7fd-138">左側のメニューから [ **接続** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-138">Select **Connect** from the left-side menu:</span></span>

![[接続] ボタンが強調表示されている、PIX アプリケーションの左側のメニューのスクリーンショット](images/pix-img-11.png)

2. <span data-ttu-id="ea7fd-140">[ **コンピューター** ] タブで [ **追加**] を選択し、次の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-140">From the **Computer** tab, select **Add**, and enter the following credentials:</span></span>
    * <span data-ttu-id="ea7fd-141">エイリアス: ユーザーの裁量</span><span class="sxs-lookup"><span data-stu-id="ea7fd-141">Alias: Up to user’s discretion</span></span>
    * <span data-ttu-id="ea7fd-142">ホスト名または IP アドレス: 127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="ea7fd-142">Host Name or IP Address: 127.0.0.1</span></span>

3. <span data-ttu-id="ea7fd-143">[**コンピューター** ] タブの右下にある [**接続**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-143">Select **Connect** in the lower right of the **Computer** tab:</span></span>

![[エイリアス]、[ホスト名]、[IP アドレス]、[追加] ボタンが強調表示されている PIX アプリケーション接続ウィンドウのスクリーンショット](images/pix-img-12.png)

> [!NOTE]
> <span data-ttu-id="ea7fd-145">バイナリがコピーされるため、最初の接続は常に低速です。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-145">The first connection is always slower because binaries are being copied.</span></span>

4. <span data-ttu-id="ea7fd-146">PIX が HoloLens 2 に接続されている場合は、[UWP の起動] タブの [ **ターゲットプロセスの選択** ] セクションでアプリを見つけ、[ **起動**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-146">When PIX has connected to the HoloLens 2, find your app in the **Select Target Process** section in the Launch UWP tab, and select **Launch**:</span></span>

![[ターゲットプロセスの選択] ウィンドウと [起動] ボタンが強調表示されている PIX アプリケーションのスクリーンショット](images/pix-img-13.png)

## <a name="gpu-captured"></a><span data-ttu-id="ea7fd-148">キャプチャされた GPU</span><span class="sxs-lookup"><span data-stu-id="ea7fd-148">GPU captured</span></span>

1. <span data-ttu-id="ea7fd-149">Gpu **キャプチャ** セクションの [**写真**] をクリックして、gpu キャプチャを開始します。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-149">Start the GPU capture by clicking **Photo** in the **GPU Capture** section:</span></span>

![GPU キャプチャが強調表示された状態で、PC 接続パネルが開いている PIX アプリケーションのスクリーンショット](images/pix-img-14.png)

2. <span data-ttu-id="ea7fd-151">**GPU キャプチャ** パネルで生成されたスクリーンショットをクリックして、分析用のキャプチャを開きます。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-151">Open the capture for analysis by clicking on the generated screenshot in the **GPU Capture** panel:</span></span>

![[Gpu キャプチャ] パネルが強調表示されている GPU キャプチャセクションがある PIX アプリケーションのスクリーンショット](images/pix-img-15.png)

3. <span data-ttu-id="ea7fd-153">[ **Start (開始** ) を押して分析を開始します。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-153">Press **Start** to begin the analysis:</span></span>

![[スタート] ボタンが強調表示されている PIX アプリケーションのスクリーンショット](images/pix-img-16.png)

> [!IMPORTANT]
> <span data-ttu-id="ea7fd-155">GPU キャプチャを行った後でタイミングデータを収集する場合は、ヘッドセットを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-155">If you collect timing data after taking a GPU capture, you'll be required to reboot the headset.</span></span> <span data-ttu-id="ea7fd-156">これはデバイスの1回限りの再起動であり、タイミングデータの収集に必要です。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-156">This is a one-time restart of the device and is required for timing data collection.</span></span>

<span data-ttu-id="ea7fd-157">PIX が使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ea7fd-157">PIX is now ready for use!</span></span>

## <a name="see-also"></a><span data-ttu-id="ea7fd-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea7fd-158">See also</span></span>
* [<span data-ttu-id="ea7fd-159">PIX ホームページ</span><span class="sxs-lookup"><span data-stu-id="ea7fd-159">PIX homepage</span></span>](https://devblogs.microsoft.com/pix)