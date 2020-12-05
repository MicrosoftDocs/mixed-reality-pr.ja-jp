---
title: HoloLens 2 用 PIX のインストール
description: HoloLens 2 デバイス用の PIX をインストールする方法について説明します。
author: hferrone
ms.author: flbagar
ms.date: 12/02/2020
ms.topic: article
keywords: HoloLens、HoloLens 2、PIX、capture、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: 4554600414784b2644006e6e891f16f8ce3a79f5
ms.sourcegitcommit: 924f8c1ceb93c378f800cf88d82944cf80f092bc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96615362"
---
# <a name="installing-pix-for-hololens-2"></a><span data-ttu-id="f5634-104">HoloLens 2 用 PIX のインストール</span><span class="sxs-lookup"><span data-stu-id="f5634-104">Installing PIX for HoloLens 2</span></span>

<span data-ttu-id="f5634-105">[PIX](https://devblogs.microsoft.com/pix) は、Windows 上の DirectX 12 アプリケーション用のパフォーマンスチューニングおよびデバッグツールです。</span><span class="sxs-lookup"><span data-stu-id="f5634-105">[PIX](https://devblogs.microsoft.com/pix) is a performance tuning and debugging tool for DirectX 12 applications on Windows.</span></span> 

## <a name="setup"></a><span data-ttu-id="f5634-106">セットアップ</span><span class="sxs-lookup"><span data-stu-id="f5634-106">Setup</span></span>

1. <span data-ttu-id="f5634-107">ホスト PC から最新の PIX [リリース]( https://devblogs.microsoft.com/pix/download) を入手し、USB ケーブル経由で HoloLens 2 を PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="f5634-107">Grab the latest PIX [release]( https://devblogs.microsoft.com/pix/download) from your host PC and connect your HoloLens 2 to your PC via a USB cable.</span></span>

2. <span data-ttu-id="f5634-108">HoloLens 2 が [Windows Insider ビルド](https://insider.windows.com) にある場合、または PIX を中断する構成がある場合は、  [デバイスを再フラッシュ](https://docs.microsoft.com/hololens/hololens-recovery) してすべてのデータを消去します。</span><span class="sxs-lookup"><span data-stu-id="f5634-108">If your HoloLens 2 is on a [Windows Insider build](https://insider.windows.com) or has a configuration that breaks PIX,  [re-flash your device](https://docs.microsoft.com/hololens/hololens-recovery) to erase all data.</span></span>

3. <span data-ttu-id="f5634-109">**開発者モード** と **デバイスポータル** を有効にする:</span><span class="sxs-lookup"><span data-stu-id="f5634-109">Enable **Developer Mode** and **Device Portal**:</span></span>

* <span data-ttu-id="f5634-110">シェルから **設定** を開く:</span><span class="sxs-lookup"><span data-stu-id="f5634-110">Open **Settings** from Shell:</span></span>

![[設定] ボタンが強調表示されている HoloLens メニューのスクリーンショット](images/pix-img-01.jpg)

* <span data-ttu-id="f5634-112">[ **Update & Security**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f5634-112">Select **Update & Security**:</span></span>

![[更新とセキュリティ] ボタンが強調表示されている HoloLens で開かれている [設定] ウィンドウのスクリーンショット](images/pix-img-02.jpg)

* <span data-ttu-id="f5634-114">[ **開発者] を** クリックします。</span><span class="sxs-lookup"><span data-stu-id="f5634-114">Click **For Developers**:</span></span>

![[開発者用に開く] ボタンが強調表示されている [セキュリティと更新プログラム] ウィンドウのスクリーンショット](images/pix-img-03.jpg)

* <span data-ttu-id="f5634-116">**開発者機能を使用** して **デバイスポータルを有効** にする</span><span class="sxs-lookup"><span data-stu-id="f5634-116">Turn on **Use Developer Features** and **Enable Device Portal**</span></span>

![[デバイスポータルを有効にする] ボタンが強調表示されている [設定] で開いている開発者ウィンドウのスクリーンショット](images/pix-img-04.jpg)

![[開発機能を使用して設定] で開いている開発者ウィンドウのスクリーンショットの表示/非表示](images/pix-img-05.jpg)

* <span data-ttu-id="f5634-119">デバイスが接続された状態で、ユーザーがログインした状態で、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="f5634-119">With the device still connected, awake, and with the user logged in, launch Visual Studio.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5634-120">デバイスがスタンバイモードまたはスリープ状態になっていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f5634-120">Make sure your device isn't in standby mode or asleep.</span></span> <span data-ttu-id="f5634-121">この手順で問題が発生した場合は、 [Windows デバイスポータルの手順](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5634-121">If you're having trouble with this step, refer to the [Windows Device Portal instructions](https://docs.microsoft.com/windows/mixed-reality/develop/platform-capabilities-and-apis/using-the-windows-device-portal).</span></span>

## <a name="preparing-for-deployment"></a><span data-ttu-id="f5634-122">展開の準備</span><span class="sxs-lookup"><span data-stu-id="f5634-122">Preparing for deployment</span></span>

1. <span data-ttu-id="f5634-123">Visual Studio で、 **ARM64** をデバイスとしてプラットフォームと **デバイス** として設定します。</span><span class="sxs-lookup"><span data-stu-id="f5634-123">In Visual Studio, set **ARM64** as the platform and **Device** as the device:</span></span>

![プラットフォームとデバイスの設定が強調表示されている visual studio ソリューションのスクリーンショット](images/pix-img-06.png)

2. <span data-ttu-id="f5634-125">Visual Studio によって、デバイスからの **PIN** の入力が求められます。</span><span class="sxs-lookup"><span data-stu-id="f5634-125">When Visual Studio prompts you for a **PIN** from the device:</span></span>

![PIN を要求する visual studio ポップアップのスクリーンショット](images/pix-img-07.png)

* <span data-ttu-id="f5634-127">シェルから **設定** を選択する</span><span class="sxs-lookup"><span data-stu-id="f5634-127">Select **Settings** from Shell</span></span>
* <span data-ttu-id="f5634-128">**更新プログラム & セキュリティ** を選択する</span><span class="sxs-lookup"><span data-stu-id="f5634-128">Select **Update & Security**</span></span>
* <span data-ttu-id="f5634-129">[**デバイスの検出**] の下にある [**開発者**] をクリックしてペアを押す</span><span class="sxs-lookup"><span data-stu-id="f5634-129">Click **For Developers** and press Pair under **Device Discovery**</span></span> 

![デバイス検出が強調表示されている [設定] で開いている開発者ウィンドウのスクリーンショット](images/pix-img-08.jpg)

![登録コードが強調表示されている、有料デバイスのポップアップのスクリーンショット](images/pix-img-09.jpg)

* <span data-ttu-id="f5634-132">Visual Studio で生成された PIN 番号を入力します</span><span class="sxs-lookup"><span data-stu-id="f5634-132">Enter the generated PIN number in Visual Studio</span></span>

3. <span data-ttu-id="f5634-133">Visual Studio は接続されている HoloLens 2 にアプリをデプロイします。アプリによっては数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5634-133">Visual Studio will deploy the app to the connected HoloLens 2, which may take a few minutes depending on the app.</span></span>

## <a name="launching-pix"></a><span data-ttu-id="f5634-134">PIX の起動</span><span class="sxs-lookup"><span data-stu-id="f5634-134">Launching PIX</span></span>

<span data-ttu-id="f5634-135">まず、デバイスポータルを使用して、HoloLens 2 でアプリが実行されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f5634-135">First, use Device Portal to verify the app is not running on the HoloLens 2.</span></span> <span data-ttu-id="f5634-136">次に、PIX を起動してデバイスに接続し、[ **ホーム**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5634-136">Then, launch PIX, connect to your device, and click **Home**:</span></span>

![PIX アプリケーションのホーム画面のスクリーンショット](images/pix-img-10.png)

* <span data-ttu-id="f5634-138">左側のメニューから [ **接続** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f5634-138">Select **Connect** from the left-side menu:</span></span>

![[接続] ボタンが強調表示されている、PIX アプリケーションの左側のメニューのスクリーンショット](images/pix-img-11.png)

2. <span data-ttu-id="f5634-140">[ **コンピューター** ] タブで [ **追加** ] をクリックし、次の資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="f5634-140">From the **Computer** tab, click **Add** and enter the following credentials:</span></span>
    * <span data-ttu-id="f5634-141">エイリアス: ユーザーの裁量</span><span class="sxs-lookup"><span data-stu-id="f5634-141">Alias: Up to user’s discretion</span></span>
    * <span data-ttu-id="f5634-142">ホスト名または IP アドレス: 127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="f5634-142">Host Name or IP Address: 127.0.0.1</span></span>

3. <span data-ttu-id="f5634-143">[**コンピューター** ] タブの右下にある [**接続**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5634-143">Click **Connect** in the lower-right of the **Computer** tab:</span></span>

![[エイリアス]、[ホスト名]、[IP アドレス]、[追加] ボタンが強調表示されている PIX アプリケーション接続ウィンドウのスクリーンショット](images/pix-img-12.png)

> [!NOTE]
> <span data-ttu-id="f5634-145">バイナリがコピーされるため、最初の接続は常に低速です。</span><span class="sxs-lookup"><span data-stu-id="f5634-145">The first connection is always slower because binaries are being copied.</span></span>

4. <span data-ttu-id="f5634-146">PIX が HoloLens 2 に接続されている場合は、[UWP の起動] タブの [ **ターゲットプロセスの選択** ] セクションでアプリを見つけ、[ **起動**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f5634-146">When PIX has connected to the HoloLens 2, find your app in the **Select Target Process** section in the Launch UWP tab, and click **Launch**:</span></span>

![[ターゲットプロセスの選択] ウィンドウと [起動] ボタンが強調表示されている PIX アプリケーションのスクリーンショット](images/pix-img-13.png)

## <a name="gpu-captured"></a><span data-ttu-id="f5634-148">キャプチャされた GPU</span><span class="sxs-lookup"><span data-stu-id="f5634-148">GPU captured</span></span>

1. <span data-ttu-id="f5634-149">Gpu **キャプチャ** セクションの [**写真**] をクリックして、gpu キャプチャを開始します。</span><span class="sxs-lookup"><span data-stu-id="f5634-149">Start the GPU capture by clicking **Photo** in the **GPU Capture** section:</span></span>

![GPU キャプチャが強調表示された状態で、PC 接続パネルが開いている PIX アプリケーションのスクリーンショット](images/pix-img-14.png)

2. <span data-ttu-id="f5634-151">**GPU キャプチャ** パネルで生成されたスクリーンショットをクリックして、分析用のキャプチャを開きます。</span><span class="sxs-lookup"><span data-stu-id="f5634-151">Open the capture for analysis by clicking on the generated screen shot in the **GPU Capture** panel:</span></span>

![[Gpu キャプチャ] パネルが強調表示されている GPU キャプチャセクションがある PIX アプリケーションのスクリーンショット](images/pix-img-15.png)

3. <span data-ttu-id="f5634-153">[ **Start (開始** ) を押して分析を開始します。</span><span class="sxs-lookup"><span data-stu-id="f5634-153">Press **Start** to begin the analysis:</span></span>

![[スタート] ボタンが強調表示されている PIX アプリケーションのスクリーンショット](images/pix-img-16.png)

> [!IMPORTANT]
> <span data-ttu-id="f5634-155">GPU キャプチャを行った後でタイミングデータを収集する場合は、ヘッドセットを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5634-155">If you collect timing data after taking a GPU capture, you'll be required to reboot the headset.</span></span> <span data-ttu-id="f5634-156">これはデバイスの1回限りの再起動であり、タイミングデータの収集に必要です。</span><span class="sxs-lookup"><span data-stu-id="f5634-156">This is a one-time restart of the device and is required for timing data collection.</span></span>

<span data-ttu-id="f5634-157">PIX が使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="f5634-157">PIX is now ready for use!</span></span>

## <a name="see-also"></a><span data-ttu-id="f5634-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5634-158">See also</span></span>
* [<span data-ttu-id="f5634-159">PIX ホームページ</span><span class="sxs-lookup"><span data-stu-id="f5634-159">PIX homepage</span></span>](https://devblogs.microsoft.com/pix)