---
title: Windows Mixed Reality における PC の互換性に関するヘルプを表示する
description: Windows Mixed Reality を使用する場合の PC 互換性の問題に関するヘルプリソース。
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、フィードバック、フィードバックハブ、バグ
appliesto:
- Windows 10
ms.openlocfilehash: e55c66599e47abff35b872a494a6afbb48774171
ms.sourcegitcommit: 50d9afae479e418b885dc883ce88771292923f01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2021
ms.locfileid: "97859521"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a><span data-ttu-id="ac517-104">Windows Mixed Reality における PC の互換性に関するヘルプを表示する</span><span class="sxs-lookup"><span data-stu-id="ac517-104">Get help with PC compatibility in Windows Mixed Reality</span></span>

<span data-ttu-id="ac517-105">Windows Mixed Reality を設定している場合、または [Mixed Reality ポータル](install-windows-mixed-reality.md)を使用している場合は、PC がタスクに依存しているかどうかに関するレポートが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ac517-105">When you're setting up Windows Mixed Reality or using the [Mixed Reality Portal](install-windows-mixed-reality.md), you'll get a report on whether your PC is up to the task.</span></span> <span data-ttu-id="ac517-106">以下のセクションでは、特定の詳細について詳しく説明しています。</span><span class="sxs-lookup"><span data-stu-id="ac517-106">We've broken out specific details on what you might see in the sections below.</span></span>

<span data-ttu-id="ac517-107">先に進む前に、以下の最も一般的な修正を試してください。</span><span class="sxs-lookup"><span data-stu-id="ac517-107">Before going any further, try the most common fixes below:</span></span> 

> [!div class="checklist"]
> * <span data-ttu-id="ac517-108">コンピューターが[PC ハードウェアの最小互換性要件](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)を満たしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ac517-108">Make sure your computer meets the [minimum PC hardware compatibility requirements](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)</span></span>
> * <span data-ttu-id="ac517-109">[グラフィックスカードとプロセッサ](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)に互換性があることを確認する</span><span class="sxs-lookup"><span data-stu-id="ac517-109">Check that your [graphics card and processor](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) are compatible</span></span>
> * <span data-ttu-id="ac517-110">推奨される [アダプター](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) の一覧を確認する</span><span class="sxs-lookup"><span data-stu-id="ac517-110">Check the [recommended adapters](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) list</span></span>
> * <span data-ttu-id="ac517-111">[> の設定の開始] を選択してグラフィックドライバーを更新し、 **& セキュリティ > 更新プログラムを確認 >** 更新します。</span><span class="sxs-lookup"><span data-stu-id="ac517-111">Update your graphics driver by selecting **Start > Settings > Update & security > Check for updates**</span></span> 

## <a name="youre-good-to-go"></a><span data-ttu-id="ac517-112">お待ちください</span><span class="sxs-lookup"><span data-stu-id="ac517-112">You're good to go</span></span>

<span data-ttu-id="ac517-113">良いニュースが表示 **された** 場合は、PC で Windows Mixed Reality を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ac517-113">Good news, if you see the **You're good to go** message, your PC can run Windows Mixed Reality!</span></span> <span data-ttu-id="ac517-114">コンピューターのハードウェアと構成の間には変化があるため、すべての PC で Mixed Reality エクスペリエンスが同じであるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="ac517-114">There's still variation among computer hardware and configuration, so the Mixed Reality experience might not be the same on every PC.</span></span>

## <a name="supports-some-features"></a><span data-ttu-id="ac517-115">一部の機能をサポート</span><span class="sxs-lookup"><span data-stu-id="ac517-115">Supports some features</span></span>

<span data-ttu-id="ac517-116">"機能の一部を **サポート** " というメッセージが表示されている場合は、一部の Windows Mixed Reality エクスペリエンスを PC で実行できますが、最適なエクスペリエンスが得られない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-116">If you're seeing the **Supports some features** message, your PC can run some Windows Mixed Reality experiences, but might not provide the best possible experience.</span></span> <span data-ttu-id="ac517-117">欠点としては、遅れているグラフィックス、パフォーマンスヒット、および実行できないアプリケーションやゲームがあります。</span><span class="sxs-lookup"><span data-stu-id="ac517-117">Possible downsides include lagging graphics, performance hits, and some applications and games that you can't run at all.</span></span> <span data-ttu-id="ac517-118">表示される可能性のあるメッセージと、その対処方法を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="ac517-118">We've listed messages you might see and what to do about them below.</span></span>

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a><span data-ttu-id="ac517-119">この PC には、シングルチャネル RAM を備えた統合グラフィックスカードが搭載されています。</span><span class="sxs-lookup"><span data-stu-id="ac517-119">This PC has an integrated graphics card with single-channel RAM</span></span>

<span data-ttu-id="ac517-120">統合グラフィックスカードは、デュアルチャネル RAM を搭載した Pc で、最適な Windows Mixed Reality エクスペリエンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="ac517-120">Integrated graphics cards will provide the best Windows Mixed Reality experience on PCs with dual-channel RAM.</span></span> <span data-ttu-id="ac517-121">パフォーマンスの問題が発生する場合は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="ac517-121">If you run into performance problems:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ac517-122">互換性の[ある独立したグラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)をインストールする</span><span class="sxs-lookup"><span data-stu-id="ac517-122">Install a [compatible discrete graphics card](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)</span></span>
> * <span data-ttu-id="ac517-123">追加の RAM スティックを取り付けてデュアルチャネル RAM を作成する</span><span class="sxs-lookup"><span data-stu-id="ac517-123">Install an additional RAM stick to create dual-channel RAM</span></span>
> * <span data-ttu-id="ac517-124">互換性のある[PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)に切り替える</span><span class="sxs-lookup"><span data-stu-id="ac517-124">Switch to a [compatible PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)</span></span>

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a><span data-ttu-id="ac517-125">この PC には、互換性のない PCIe リンクを備えたハイブリッドグラフィックス構成があります</span><span class="sxs-lookup"><span data-stu-id="ac517-125">This PC has a hybrid graphics configuration with an incompatible PCIe link</span></span>

<span data-ttu-id="ac517-126">PCIe は、PC がグラフィックスカードとの通信に使用する接続である *周辺コンポーネントの相互接続 Express* を表します。</span><span class="sxs-lookup"><span data-stu-id="ac517-126">PCIe stands for *Peripheral Component Interconnect Express*, which is the connection that a PC uses to communicate with a graphics card.</span></span> <span data-ttu-id="ac517-127">構成が機能する場合もありますが、問題が発生した場合は、 [互換性](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)のある PC に切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-127">Your configuration might work, but if you run into problems you'll need to switch to a [compatible PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).</span></span>

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a><span data-ttu-id="ac517-128">この PC のグラフィックドライバーは、Windows Mixed Reality では正しく機能しない可能性があります</span><span class="sxs-lookup"><span data-stu-id="ac517-128">This PC's graphics driver might not work well with Windows Mixed Reality</span></span>

<span data-ttu-id="ac517-129">Windows Update を使用して新しいグラフィックスドライバーをダウンロードしてみてください。</span><span class="sxs-lookup"><span data-stu-id="ac517-129">Try downloading a new graphics driver using Windows Update by:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ac517-130">[ **> の設定の開始] を選択して & セキュリティ > 更新プログラムを確認** するか、PC またはグラフィックスカードの製造元の web サイトに移動 > ます。</span><span class="sxs-lookup"><span data-stu-id="ac517-130">Selecting **Start > Settings > Update & security > Check for updates** or going to your PC or graphics card manufacturer's website</span></span>
> * [<span data-ttu-id="ac517-131">更新プログラムをチェックする</span><span class="sxs-lookup"><span data-stu-id="ac517-131">Check for updates</span></span>](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

<span data-ttu-id="ac517-132">それでもうまくいかない場合は、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-132">If that doesn't work, you'll need to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ac517-133">互換性の[あるグラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)を追加する</span><span class="sxs-lookup"><span data-stu-id="ac517-133">Add a [compatible graphics card](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)</span></span> 
> * <span data-ttu-id="ac517-134">互換性のある[PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)に切り替える</span><span class="sxs-lookup"><span data-stu-id="ac517-134">Switch to a [compatible PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)</span></span>

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a><span data-ttu-id="ac517-135">この PC のプロセッサは、Windows Mixed Reality では正しく機能しない可能性があります</span><span class="sxs-lookup"><span data-stu-id="ac517-135">This PC's processor might not work well with Windows Mixed Reality</span></span>

<span data-ttu-id="ac517-136">十分なコアがないため、Windows Mixed Reality では PC のプロセッサがうまく機能しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-136">Your PC's processor might not work well with Windows Mixed Reality because it doesn't have enough cores.</span></span> <span data-ttu-id="ac517-137">Windows Mixed Reality が正常に実行されない場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ac517-137">If Windows Mixed Reality doesn't run well:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ac517-138">プロセッサを互換性のある[もの](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ac517-138">Replace the processor with a [compatible one](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)</span></span> 
> * <span data-ttu-id="ac517-139">互換性のある[PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)に切り替える</span><span class="sxs-lookup"><span data-stu-id="ac517-139">Switch to a [compatible PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)</span></span>

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a><span data-ttu-id="ac517-140">この PC は、互換性のある USB 構成を持っていない可能性があります</span><span class="sxs-lookup"><span data-stu-id="ac517-140">This PC might not have a compatible USB configuration</span></span>

<span data-ttu-id="ac517-141">Windows Mixed Reality の実行に関する問題:</span><span class="sxs-lookup"><span data-stu-id="ac517-141">For problems running Windows Mixed Reality:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ac517-142">一般的な互換性の問題の解決策については、 [推奨されるアダプターのドキュメント](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac517-142">Check our [recommended adapters documentation](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) for solutions to common compatibility issues</span></span>
> * <span data-ttu-id="ac517-143">[外部電源 USB ハブ](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)の使用を検討する</span><span class="sxs-lookup"><span data-stu-id="ac517-143">Consider using an [external powered USB hub](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)</span></span>

<span data-ttu-id="ac517-144">問題が引き続き発生する場合:</span><span class="sxs-lookup"><span data-stu-id="ac517-144">If the problems persist:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ac517-145">使用可能な場合は、別の USB ポートにヘッドセットを接続します。</span><span class="sxs-lookup"><span data-stu-id="ac517-145">Plug your headset into a different USB port, if you have one available.</span></span>
> * <span data-ttu-id="ac517-146">それでもうまくいかない場合は、PC の現在の USB ドライバーをアンインストールしてから、Microsoft ドライバーを再インストールします。</span><span class="sxs-lookup"><span data-stu-id="ac517-146">If that doesn't work, uninstall your PC's current USB driver, and then reinstall a Microsoft driver:</span></span>

1. <span data-ttu-id="ac517-147">[ **スタート**] を選択し、 **検索** ボックスに「デバイスマネージャー」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ac517-147">Select **Start**, and then type "device manager" in the **Search** box.</span></span>
2. <span data-ttu-id="ac517-148">結果から [ **デバイスマネージャー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac517-148">Select **Device Manager** from the results.</span></span>
3. <span data-ttu-id="ac517-149">ユニバーサルシリアルバスコントローラーのカテゴリを展開し、一覧表示されているデバイスを確認して、互換性のないドライバーをアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="ac517-149">Expand the category for Universal Serial Bus controllers, look at the devices listed, and uninstall any incompatible drivers.</span></span>
    * <span data-ttu-id="ac517-150">一覧に、デバイス名の末尾に "Microsoft" がない "拡張可能なホストコントローラー" 項目が含まれている場合、そのドライバーは Windows Mixed Reality と互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="ac517-150">If the list includes an “eXtensible Host Controller” item that doesn't have “Microsoft” at the end of the device name, that driver isn't compatible with Windows Mixed Reality.</span></span> <span data-ttu-id="ac517-151">アンインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-151">You’ll need to uninstall it.</span></span> <span data-ttu-id="ac517-152">ドライバーをアンインストールするには、一覧でデバイスを右クリックし、[ **デバイスのアンインストール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac517-152">To uninstall a driver, right-click the device in the list and select **Uninstall device**.</span></span> <span data-ttu-id="ac517-153">[ **このデバイスのドライバーソフトウェアを削除** する] チェックボックスをオンにし、[ **アンインストール**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ac517-153">Select the **Delete the driver software for this device** check box, then select **Uninstall**.</span></span>
    * <span data-ttu-id="ac517-154">名前に "Etron" を含む "拡張可能なホストコントローラー" 項目が一覧に含まれている場合、その USB コントローラーは Windows Mixed Reality と互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="ac517-154">If the list includes an "eXtensible Host Controller" item that includes "Etron" in the name, that USB controller isn't compatible with Windows Mixed Reality.</span></span> <span data-ttu-id="ac517-155">PC で別の USB ポートを使用するか、別の USB 3.0 ホストコントローラーを購入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-155">You'll need to use a different USB port on the PC or purchase a different USB 3.0 host controller.</span></span>
4. <span data-ttu-id="ac517-156">PC を再起動します。</span><span class="sxs-lookup"><span data-stu-id="ac517-156">Restart your PC.</span></span>
5. <span data-ttu-id="ac517-157">デバイスマネージャーに戻り、拡張可能なホストコントローラーの項目をもう一度見つけます。</span><span class="sxs-lookup"><span data-stu-id="ac517-157">Return to Device Manager and locate the eXtensible Host Controller item again.</span></span> <span data-ttu-id="ac517-158">デバイス名の末尾に "Microsoft" が表示されている場合は、これで問題ありません。</span><span class="sxs-lookup"><span data-stu-id="ac517-158">If you now see “Microsoft” at the end of the device name, you’re good to go.</span></span> <span data-ttu-id="ac517-159">インストールされていない場合は、アンインストールの手順を繰り返して、Microsoft 以外のその他のバージョンのドライバーを削除します。</span><span class="sxs-lookup"><span data-stu-id="ac517-159">If not, repeat the uninstall steps to remove any extra non-Microsoft versions of the driver.</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ac517-160">それでもうまくいかない場合は、PCIe USB カードを PC に追加します。</span><span class="sxs-lookup"><span data-stu-id="ac517-160">If that still doesn't work, add a PCIe USB card to your PC.</span></span>

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a><span data-ttu-id="ac517-161">この PC には、コントローラー用の Bluetooth 4.0 がありません</span><span class="sxs-lookup"><span data-stu-id="ac517-161">This PC doesn't have Bluetooth 4.0 for controllers</span></span>

<span data-ttu-id="ac517-162">2018およびそれ以降の Windows Mixed Reality ヘッドセットには既に Bluetooth が組み込まれていますが、古いヘッドセットを使用している場合は、Mixed reality モーションコントローラーに bluetooth 4.0 が必要です。</span><span class="sxs-lookup"><span data-stu-id="ac517-162">2018 and newer Windows Mixed Reality headsets already have the built-in Bluetooth, but if you have older headset, bluetooth 4.0 is required for mixed reality motion controllers.</span></span> <span data-ttu-id="ac517-163">[Windows Mixed Reality を Xbox コントローラー](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset)、[マウス、キーボード](https://docs.microsoft.com/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse)、または[USB Bluetooth アダプター](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology)と共に使用して、モーションコントローラーを PC に接続することもできます。</span><span class="sxs-lookup"><span data-stu-id="ac517-163">You can still [use Windows Mixed Reality with an Xbox controller](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset), a [mouse and keyboard](https://docs.microsoft.com/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse), or a [USB Bluetooth adapter to connect motion controllers](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) to your PC.</span></span> [<span data-ttu-id="ac517-164">推奨されるアダプターの表示</span><span class="sxs-lookup"><span data-stu-id="ac517-164">See recommended adapters</span></span>](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a><span data-ttu-id="ac517-165">ヘッドセットによっては、モーションコントローラーを使用するために Bluetooth アダプターが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-165">Depending on your headset, you may need a Bluetooth adapter to use motion controllers</span></span>

<span data-ttu-id="ac517-166">一部のヘッドセットは Bluetooth を内蔵しているため、コントローラーはヘッドセットに直接ペアリングできます。</span><span class="sxs-lookup"><span data-stu-id="ac517-166">Some headsets have Bluetooth built in so controllers can pair directly to the headsets.</span></span> <span data-ttu-id="ac517-167">また、モーションコントローラーを使用するには、PC (または別のドングル) に Bluetooth ラジオが必要です。</span><span class="sxs-lookup"><span data-stu-id="ac517-167">Others require a Bluetooth radio in the PC (or a separate dongle) to use motion controllers.</span></span> <span data-ttu-id="ac517-168">詳細については、 [推奨されるアダプター](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ac517-168">For more information, see the [recommended adapters](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters) page.</span></span>

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a><span data-ttu-id="ac517-169">この PC には、自己供給型の USB ポートがありません</span><span class="sxs-lookup"><span data-stu-id="ac517-169">This PC doesn't have a self-powered USB port</span></span>

<span data-ttu-id="ac517-170">Windows Mixed Reality ヘッドセットに接続するには、自己供給型の USB 3.0 ポートが必要です。</span><span class="sxs-lookup"><span data-stu-id="ac517-170">A self-powered USB 3.0 port is needed to connect a Windows Mixed Reality headset.</span></span> <span data-ttu-id="ac517-171">電源が [入っている USB 3.0 ハブ](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) を PC に接続し、それを使用してヘッドセットを接続します。</span><span class="sxs-lookup"><span data-stu-id="ac517-171">Connect a [powered USB 3.0 hub](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) to the PC and use that to connect your headset.</span></span>

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a><span data-ttu-id="ac517-172">この PC のグラフィックスカードは Windows Mixed Reality では動作しません</span><span class="sxs-lookup"><span data-stu-id="ac517-172">This PC's graphics card won't work with Windows Mixed Reality</span></span>

<span data-ttu-id="ac517-173">この PC のグラフィックスカードは、Windows Mixed Reality と互換性がありません。</span><span class="sxs-lookup"><span data-stu-id="ac517-173">This PC's graphics card isn't compatible with Windows Mixed Reality.</span></span> <span data-ttu-id="ac517-174">次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-174">You'll need to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ac517-175">互換性の[あるグラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)を追加する</span><span class="sxs-lookup"><span data-stu-id="ac517-175">Add a [compatible graphics card](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)</span></span> 
> * <span data-ttu-id="ac517-176">互換性のある[PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)に切り替える</span><span class="sxs-lookup"><span data-stu-id="ac517-176">Switch to a [compatible PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)</span></span>

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a><span data-ttu-id="ac517-177">この PC のグラフィックドライバーは、Windows Mixed Reality では動作しません。</span><span class="sxs-lookup"><span data-stu-id="ac517-177">This PC's graphics driver won't work with Windows Mixed Reality</span></span>

<span data-ttu-id="ac517-178">この PC のグラフィックドライバーは、Windows Mixed Reality では動作しません。</span><span class="sxs-lookup"><span data-stu-id="ac517-178">This PC's graphics driver won't work with Windows Mixed Reality.</span></span> <span data-ttu-id="ac517-179">Windows Update を使用して新しいグラフィックスドライバーをダウンロードしてみてください。</span><span class="sxs-lookup"><span data-stu-id="ac517-179">Try downloading a new graphics driver using Windows Update by:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ac517-180">[ **> の設定の開始] を選択して & セキュリティ > 更新プログラムを確認** するか、PC またはグラフィックスカードの製造元の web サイトに移動 > ます。</span><span class="sxs-lookup"><span data-stu-id="ac517-180">Selecting **Start > Settings > Update & security > Check for updates** or going to your PC or graphics card manufacturer's website</span></span>
> * [<span data-ttu-id="ac517-181">更新プログラムをチェックする</span><span class="sxs-lookup"><span data-stu-id="ac517-181">Check for updates</span></span>](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

<span data-ttu-id="ac517-182">それでもうまくいかない場合は、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-182">If that doesn't work, you'll need to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ac517-183">互換性の[あるグラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)を追加する</span><span class="sxs-lookup"><span data-stu-id="ac517-183">Add a [compatible graphics card](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)</span></span> 
> * <span data-ttu-id="ac517-184">互換性のある[PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)に切り替える</span><span class="sxs-lookup"><span data-stu-id="ac517-184">Switch to a [compatible PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)</span></span>

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a><span data-ttu-id="ac517-185">この PC のプロセッサは、Windows Mixed Reality では動作しません。</span><span class="sxs-lookup"><span data-stu-id="ac517-185">This PC's processor won't work with Windows Mixed Reality</span></span>

<span data-ttu-id="ac517-186">この PC のプロセッサは、AVX/Popcnt 命令をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="ac517-186">This PC's processor doesn't support AVX/Popcnt instructions.</span></span> <span data-ttu-id="ac517-187">Windows Mixed Reality を実行するには、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-187">To run Windows Mixed Reality, you'll need to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ac517-188">[互換性のあるグラフィックスカード](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)で置き換える</span><span class="sxs-lookup"><span data-stu-id="ac517-188">Replace it with a [compatible graphics card](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)</span></span> 
> * <span data-ttu-id="ac517-189">互換性のある[PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)に切り替える</span><span class="sxs-lookup"><span data-stu-id="ac517-189">Switch to a [compatible PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)</span></span>

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a><span data-ttu-id="ac517-190">この PC には、Windows Mixed Reality を実行するのに十分な空きディスク領域がありません</span><span class="sxs-lookup"><span data-stu-id="ac517-190">This PC doesn't have enough free disk space to run Windows Mixed Reality</span></span>

<span data-ttu-id="ac517-191">Windows Mixed Reality では、セットアップと最高のパフォーマンスを実現するために 10 GB の空きディスク領域が必要です。</span><span class="sxs-lookup"><span data-stu-id="ac517-191">Windows Mixed Reality requires 10 GB of free disk space for setup and best performance.</span></span> <span data-ttu-id="ac517-192">ドライブの空き領域を増やしてから、最初からもう一度セットアップを実行してください。</span><span class="sxs-lookup"><span data-stu-id="ac517-192">Clear some space on your drive and then try setting up again from the beginning.</span></span>

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a><span data-ttu-id="ac517-193">この PC は、Windows Mixed Reality をサポートしていない Windows のエディションを実行しています</span><span class="sxs-lookup"><span data-stu-id="ac517-193">This PC is running an edition of Windows that doesn't support Windows Mixed Reality</span></span>

<span data-ttu-id="ac517-194">Windows Mixed Reality は、 [windows 10 Home](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab) と [windows 10 Pro](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab)で動作します。</span><span class="sxs-lookup"><span data-stu-id="ac517-194">Windows Mixed Reality works on [Windows 10 Home](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab) and [Windows 10 Pro](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab).</span></span> <span data-ttu-id="ac517-195">Windows Mixed Reality を使用するには、これらのエディションのいずれかをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-195">You'll need to install one of those editions to use Windows Mixed Reality.</span></span>

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a><span data-ttu-id="ac517-196">この PC では最新バージョンの Windows 10 が実行されていません</span><span class="sxs-lookup"><span data-stu-id="ac517-196">This PC isn't running the latest version of Windows 10</span></span>

<span data-ttu-id="ac517-197">Windows Mixed Reality では、Windows 10 の秋の作成者の更新プログラムが必要です。</span><span class="sxs-lookup"><span data-stu-id="ac517-197">Windows Mixed Reality requires the Windows 10 Fall Creators Update.</span></span> <span data-ttu-id="ac517-198">[PC を更新](https://support.microsoft.com/help/4028685) して、もう一度やり直してください。</span><span class="sxs-lookup"><span data-stu-id="ac517-198">[Update your PC](https://support.microsoft.com/help/4028685) and try again.</span></span>

### <a name="this-pc-has-no-usb-30-port"></a><span data-ttu-id="ac517-199">この PC には USB 3.0 ポートがありません</span><span class="sxs-lookup"><span data-stu-id="ac517-199">This PC has no USB 3.0 port</span></span>

<span data-ttu-id="ac517-200">Windows Mixed Reality ヘッドセットを接続するには、USB 3.0 ポートが必要です。</span><span class="sxs-lookup"><span data-stu-id="ac517-200">You'll need a USB 3.0 port to connect a Windows Mixed Reality headset.</span></span> <span data-ttu-id="ac517-201">デスクトップ PC を使用している場合は、PCIe USB カードを追加します。</span><span class="sxs-lookup"><span data-stu-id="ac517-201">If you're using a desktop PC, add a PCIe USB card.</span></span> <span data-ttu-id="ac517-202">ラップトップの場合は、互換性のある [PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)に切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-202">For laptops, you'll need to switch to a [compatible PC](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).</span></span>

### <a name="you-cant-run-this-app-via-remote-desktop"></a><span data-ttu-id="ac517-203">リモートデスクトップでこのアプリを実行することはできません</span><span class="sxs-lookup"><span data-stu-id="ac517-203">You can't run this app via remote desktop</span></span>

<span data-ttu-id="ac517-204">Windows Mixed Reality を使用するには、モニターが接続されている PC が必要です。</span><span class="sxs-lookup"><span data-stu-id="ac517-204">To use Windows Mixed Reality, you need a PC with a monitor connected.</span></span> <span data-ttu-id="ac517-205">バーチャルマシンを使用している場合、またはモニターがない場合は、仮想ディスプレイアダプタを使用してみてください。</span><span class="sxs-lookup"><span data-stu-id="ac517-205">If you're using a virtual machine or don't have a monitor, try using a virtual display adapter.</span></span> <span data-ttu-id="ac517-206">これは、PC の DisplayPort に接続し、コンピューターのディスプレイをエミュレートするデバイスです。</span><span class="sxs-lookup"><span data-stu-id="ac517-206">This is a device that plugs into the PC's DisplayPort and emulates a computer display.</span></span>

## <a name="getting-the-best-performance"></a><span data-ttu-id="ac517-207">最高のパフォーマンスを得る</span><span class="sxs-lookup"><span data-stu-id="ac517-207">Getting the best performance</span></span>

<span data-ttu-id="ac517-208">一部のハードウェア構成では、Windows Mixed Reality でパフォーマンスの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-208">Some hardware configurations might cause performance problems with Windows Mixed Reality.</span></span> <span data-ttu-id="ac517-209">読み込み速度の低下、ビジュアルの途切れ、または画質の低下などの問題については、次の一般的な修正を試してください。</span><span class="sxs-lookup"><span data-stu-id="ac517-209">For problems like slow loading, choppy visuals, or poor visual quality, try these common fixes:</span></span>

* <span data-ttu-id="ac517-210">PC デスクトップで実行されている開いているアプリを終了します。</span><span class="sxs-lookup"><span data-stu-id="ac517-210">Close any open apps running on your PC desktop.</span></span>
* <span data-ttu-id="ac517-211">USB-C または DisplayPort を HDMI アダプターとして使用している場合は、別のアダプターを試してみてください。</span><span class="sxs-lookup"><span data-stu-id="ac517-211">If you’re using a USB-C or DisplayPort to HDMI adapter, try a different one.</span></span> <span data-ttu-id="ac517-212">推奨されるアダプターの表示</span><span class="sxs-lookup"><span data-stu-id="ac517-212">See recommended adapters</span></span>
* <span data-ttu-id="ac517-213">PC のグラフィックスカードに追加のモニターが接続されている場合は、切断します。</span><span class="sxs-lookup"><span data-stu-id="ac517-213">If there are extra monitors connected to the PC’s graphics card, disconnect them.</span></span>
* <span data-ttu-id="ac517-214">Windows ストアからいくつかの異なる mixed reality アプリをダウンロードしてみてください。コンピューターのセットアップでは、いくつかの機能が強化される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-214">Try downloading some different mixed reality apps from the Windows Store—some may work better with your computer setup.</span></span>

<span data-ttu-id="ac517-215">パフォーマンスの問題が解決しない場合は、次の [Windows Mixed Reality](set-up-windows-mixed-reality.md) 設定を更新して、最適なユーザーエクスペリエンスを実現します。</span><span class="sxs-lookup"><span data-stu-id="ac517-215">If you're still having performance issues, update the following [Windows Mixed Reality](set-up-windows-mixed-reality.md) settings for an optimal user experience:</span></span>

* <span data-ttu-id="ac517-216">エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="ac517-216">Experience</span></span>
* <span data-ttu-id="ac517-217">解決方法</span><span class="sxs-lookup"><span data-stu-id="ac517-217">Resolution</span></span>
* <span data-ttu-id="ac517-218">フレームレート</span><span class="sxs-lookup"><span data-stu-id="ac517-218">Frame-rate</span></span>
* <span data-ttu-id="ac517-219">調整</span><span class="sxs-lookup"><span data-stu-id="ac517-219">Calibration</span></span>

> [!NOTE]
> <span data-ttu-id="ac517-220">"このハードウェア構成は Windows Mixed Reality で動作する可能性がありますが、まだテストされていません" というメッセージが表示された場合は、Windows Mixed Reality を長時間セッションに対して実行すると、パフォーマンスの問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-220">If you see a message that says, "This hardware configuration might work with Windows Mixed Reality, but it hasn't been tested yet," you could run into some performance issues when running Windows Mixed Reality for long sessions.</span></span>

## <a name="working-with-steamvr"></a><span data-ttu-id="ac517-221">SteamVR の使用</span><span class="sxs-lookup"><span data-stu-id="ac517-221">Working with SteamVR</span></span>

<span data-ttu-id="ac517-222">SteamVR からゲームを楽しむことは、すべての VR が提供するすべての機能を体験するための優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="ac517-222">Enjoying games from SteamVR is a great way to experience everything VR has to offer.</span></span> <span data-ttu-id="ac517-223">ただし、イマーシブデバイスから最適なパフォーマンスを得られるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ac517-223">However, you'll want to make sure that you're getting the best performance out of your immersive device.</span></span> <span data-ttu-id="ac517-224">[ストリーム](https://store.steampowered.com/about)をインストールした後:</span><span class="sxs-lookup"><span data-stu-id="ac517-224">After you've installed [Steam](https://store.steampowered.com/about):</span></span>

* <span data-ttu-id="ac517-225">[Windows Mixed Reality で SteamVR を使用する](using-steamvr-with-windows-mixed-reality.md)手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ac517-225">Follow the instructions for [using SteamVR with Windows Mixed Reality](using-steamvr-with-windows-mixed-reality.md)</span></span>
* <span data-ttu-id="ac517-226">[Steamvr パフォーマンステスト](https://store.steampowered.com/app/323910/SteamVR_Performance_Test)アプリをインストールする</span><span class="sxs-lookup"><span data-stu-id="ac517-226">Install the [SteamVR Performance Test](https://store.steampowered.com/app/323910/SteamVR_Performance_Test) apps</span></span>

## <a name="next-vr-checkpoint"></a><span data-ttu-id="ac517-227">次の VR チェックポイント</span><span class="sxs-lookup"><span data-stu-id="ac517-227">Next VR checkpoint</span></span>

<span data-ttu-id="ac517-228">これまでに説明した VR の旅に従うと、デバイスを購入する準備ができています。</span><span class="sxs-lookup"><span data-stu-id="ac517-228">If you're following the VR journey we've laid out, you're almost ready to buy a device.</span></span> <span data-ttu-id="ac517-229">ここでは、チェックポイントを購入する前に、次の手順に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="ac517-229">From here, you can continue to the last before you buy checkpoint:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ac517-230">購入に関する Faq</span><span class="sxs-lookup"><span data-stu-id="ac517-230">Buying FAQs</span></span>](before-you-buy-faqs.md)

<span data-ttu-id="ac517-231">または、[作業の開始] セクションに直接移動します。</span><span class="sxs-lookup"><span data-stu-id="ac517-231">Or jump right into the getting started section:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ac517-232">Windows Mixed Reality のセットアップ</span><span class="sxs-lookup"><span data-stu-id="ac517-232">Setting up Windows Mixed Reality</span></span>](set-up-windows-mixed-reality.md)

<span data-ttu-id="ac517-233">いつでも、いつでも [VR](vr-journey.md) に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="ac517-233">You can always go back to the [VR journey](vr-journey.md) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac517-234">関連項目</span><span class="sxs-lookup"><span data-stu-id="ac517-234">See also</span></span>

* [<span data-ttu-id="ac517-235">コミュニティへの質問</span><span class="sxs-lookup"><span data-stu-id="ac517-235">Ask the community</span></span>](https://answers.microsoft.com)
* [<span data-ttu-id="ac517-236">サポートについては、お問い合わせください</span><span class="sxs-lookup"><span data-stu-id="ac517-236">Contact us for support</span></span>](https://support.microsoft.com/contactus/)
* [<span data-ttu-id="ac517-237">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="ac517-237">Troubleshooting</span></span>](troubleshooting-windows-mixed-reality.md)