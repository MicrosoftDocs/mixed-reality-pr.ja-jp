---
title: その他の質問
description: 標準のコンシューマーサポートドキュメントを超えている、その他の Windows Mixed Reality トラブルシューティングのヒント。
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート、Windows Mixed Reality のアンインストール、サポートされる言語
appliesto:
- Windows 10
ms.openlocfilehash: cf23d52fc72fa3b499b32d3770151306111afaa4
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726013"
---
# <a name="other-questions"></a><span data-ttu-id="4f127-104">その他の質問</span><span class="sxs-lookup"><span data-stu-id="4f127-104">Other questions</span></span>

## <a name="my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors"></a><span data-ttu-id="4f127-105">グラフィックスドライバーがサポートされていません (グラフィックスドライバーエラーが発生しています)。</span><span class="sxs-lookup"><span data-stu-id="4f127-105">My graphics driver isn't supported (I'm getting graphics driver failure errors).</span></span>

<span data-ttu-id="4f127-106">"Dxdiag" を検索して実行します。</span><span class="sxs-lookup"><span data-stu-id="4f127-106">Search for and run "dxdiag":</span></span>

1.  <span data-ttu-id="4f127-107">結果が "Basic レンダラー" の場合、グラフィックスドライバーはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="4f127-107">If the result is “Basic Renderer”, the graphics driver isn't installed.</span></span> <span data-ttu-id="4f127-108">この問題を解決するには:</span><span class="sxs-lookup"><span data-stu-id="4f127-108">To fix this:</span></span>
    * <span data-ttu-id="4f127-109">デバイスマネージャーにアクセスし **て、ハードウェアの変更をスキャン > > アクション** を実行します。</span><span class="sxs-lookup"><span data-stu-id="4f127-109">Go to **Device Manager > Action > Scan for Hardware Changes**.</span></span>
    * <span data-ttu-id="4f127-110">Windows Update を使用してドライバーを更新します。</span><span class="sxs-lookup"><span data-stu-id="4f127-110">Use Windows Update to update the driver.</span></span>
    * <span data-ttu-id="4f127-111">これで問題が解決しない場合は、製造元の web サイトにアクセスして、最新のドライバー更新プログラムをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="4f127-111">If this doesn't fix the problem, go to the manufacturer’s website and install the latest driver update.</span></span> 
    * <span data-ttu-id="4f127-112">GPU で更新プログラムが利用できない場合、デバイスで WMR がサポートされていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f127-112">If an update isn't available for your GPU, WMR may not be supported on your device.</span></span> <span data-ttu-id="4f127-113">必要な場合は、 [サポート](https://support.microsoft.com)にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="4f127-113">If you think it should be, contact [support](https://support.microsoft.com).</span></span>
2.  <span data-ttu-id="4f127-114">"WDDM 2.1" またはそれより前のバージョンを取得した場合、グラフィックスドライバーはインストールされますが、最新バージョンではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f127-114">If you get a “WDDM 2.1” or lower version, the graphics driver is installed but it might not be the latest version.</span></span> <span data-ttu-id="4f127-115">最新バージョンを取得するには:</span><span class="sxs-lookup"><span data-stu-id="4f127-115">To get the latest version:</span></span>
    * <span data-ttu-id="4f127-116">Windows Update を使用してドライバーを更新します。</span><span class="sxs-lookup"><span data-stu-id="4f127-116">Use Windows Update to update the driver.</span></span>
    * <span data-ttu-id="4f127-117">更新プログラムによって問題が解決されない場合は、製造元の web サイトにアクセスして、最新のドライバー更新プログラムをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="4f127-117">If that update doesn't fix the problem, go to the manufacturer’s website and install the latest driver update.</span></span> 
    * <span data-ttu-id="4f127-118">GPU で更新プログラムが利用できない場合、デバイスで WMR がサポートされていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f127-118">If an update isn't available for your GPU, WMR may not be supported on your device.</span></span> <span data-ttu-id="4f127-119">必要な場合は、 [サポート](https://support.microsoft.com)にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="4f127-119">If you think it should be, contact [support](https://support.microsoft.com).</span></span>

<span data-ttu-id="4f127-120">Windows Mixed Reality セットアップでグラフィックスカードが要件を満たしていないと思われる場合は、ヘッドセットが正しいカードに接続されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="4f127-120">If Windows Mixed Reality setup says your graphics card doesn’t meet the requirements and you think it does, make sure your headset is plugged into the correct card.</span></span>

## <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-stuck"></a><span data-ttu-id="4f127-121">Samsung Odyssey または Odyssey + ヘッドセットファームウェアの更新がスタックしています。</span><span class="sxs-lookup"><span data-stu-id="4f127-121">My Samsung Odyssey or Odyssey+ headset firmware update is stuck.</span></span>

<span data-ttu-id="4f127-122">Samsung は、"Samsung HMD Odyssey セットアップ" と "Samsung HMD Odyssey + セットアップ" デバイスコンパニオンアプリを通じて配信されるヘッドセットファームウェアの更新プログラムを所有および発行します。</span><span class="sxs-lookup"><span data-stu-id="4f127-122">Samsung owns and publishes headset firmware updates delivered via their "Samsung HMD Odyssey Setup" and "Samsung HMD Odyssey+ Setup" device companion apps.</span></span> <span data-ttu-id="4f127-123">Samsung のファームウェア更新に関する問題の詳細については、Samsung カスタマサービスにお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="4f127-123">For more details and for help with Samsung firmware update issues, contact Samsung customer service.</span></span>

<span data-ttu-id="4f127-124">ファームウェアの更新プロセスがスタックし、5分以上経過していない場合は、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="4f127-124">If the firmware update process is getting stuck, and there has been no progress for more than five minutes:</span></span>

* <span data-ttu-id="4f127-125">他のすべての USB デバイスを一時的に取り外し、ファームウェアの更新を再試行してください。</span><span class="sxs-lookup"><span data-stu-id="4f127-125">Unplug all of your other USB devices temporarily and retry the firmware update.</span></span>
* <span data-ttu-id="4f127-126">Samsung ヘッドセットを PC の別の USB 3.0 ポートに接続します。</span><span class="sxs-lookup"><span data-stu-id="4f127-126">Connect your Samsung headset to a different USB 3.0 port on your PC.</span></span>
* <span data-ttu-id="4f127-127">ギガバイトの AORUS App Center など、ファームウェアの更新に干渉する可能性のあるソフトウェアがインストールされている場合は、無効にするか、アンインストールします。</span><span class="sxs-lookup"><span data-stu-id="4f127-127">Disable or uninstall any software installed that may interfere with firmware updates, like Gigabyte's AORUS App Center.</span></span>
* <span data-ttu-id="4f127-128">別の PC を使用して Samsung ヘッドセットファームウェアを更新します。</span><span class="sxs-lookup"><span data-stu-id="4f127-128">Use a different PC to update the Samsung headset firmware.</span></span>

## <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a><span data-ttu-id="4f127-129">Mixed reality で PC デスクトップにアクセス操作方法には、</span><span class="sxs-lookup"><span data-stu-id="4f127-129">How do I access my PC desktop in mixed reality?</span></span>
<span data-ttu-id="4f127-130">Windows のヘッドセットでデスクトップアプリを起動し、[ **すべてのアプリ] > [デスクトップ] >** て、mixed REALITY で PC デスクトップにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4f127-130">Launch the Desktop app in the headset from **Windows Button > All apps > Desktop** to access your PC desktop in mixed reality.</span></span>

## <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a><span data-ttu-id="4f127-131">Mixed Reality で複数のモニターを表示する方法はありますか</span><span class="sxs-lookup"><span data-stu-id="4f127-131">How can I see multiple monitors in Mixed Reality</span></span>

<span data-ttu-id="4f127-132">既定では、デスクトップアプリが自動的に切り替えられ、フォーカスがあるモニターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4f127-132">By default, Desktop app automatically switches to display the monitor with focus.</span></span> <span data-ttu-id="4f127-133">すべてのモニターを mixed reality で表示するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="4f127-133">If you want to see all of your monitors in mixed reality:</span></span>

* <span data-ttu-id="4f127-134">アプリの左上隅にある [モニター] アイコンを選択します。</span><span class="sxs-lookup"><span data-stu-id="4f127-134">Select the monitor icon on the top-left corner of the app.</span></span>
* <span data-ttu-id="4f127-135">[モニターを自動的に切り替える] を無効にします。</span><span class="sxs-lookup"><span data-stu-id="4f127-135">Disable "Automatically Switch Monitor".</span></span>
* <span data-ttu-id="4f127-136">表示するモニターを選択します。</span><span class="sxs-lookup"><span data-stu-id="4f127-136">Pick the monitor you want to see.</span></span>
* <span data-ttu-id="4f127-137">デスクトップアプリの別のインスタンスを起動します。</span><span class="sxs-lookup"><span data-stu-id="4f127-137">Launch another instance of the Desktop app.</span></span>
* <span data-ttu-id="4f127-138">そのインスタンスに表示するモニターを選択します。</span><span class="sxs-lookup"><span data-stu-id="4f127-138">Pick the monitor you want to see on that instance.</span></span>
* <span data-ttu-id="4f127-139">すべての物理モニターについて、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="4f127-139">Repeat for all of your physical monitors.</span></span>
<span data-ttu-id="4f127-140">混合現実を再起動するたびに、各デスクトップアプリに表示するモニターを再選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f127-140">You'll have to reselect the monitor to show on each Desktop app every time you restart mixed reality.</span></span>

## <a name="my-desktop-app-only-shows-a-black-screen"></a><span data-ttu-id="4f127-141">デスクトップアプリが黒い画面のみを表示する</span><span class="sxs-lookup"><span data-stu-id="4f127-141">My Desktop app only shows a black screen</span></span>

<span data-ttu-id="4f127-142">PC に Nvidia ハイブリッド GPU が搭載されている場合、統合された GPU ではなく、個別の GPU で runtimebroker.exe を実行する Nvidia デバイスが原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f127-142">If your PC has a Nvidia hybrid GPU, the Nvidia device running the runtimebroker.exe on the discrete GPU instead of the integrated one may be the culprit.</span></span> <span data-ttu-id="4f127-143">この問題を解決するには、「[新しいプログラムに対して最適な設定を作成操作方法](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)には」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4f127-143">To fix this issue, follow these instructions under "[How do I create Optimus settings for a new program?](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)"</span></span> <span data-ttu-id="4f127-144">C:\windows\system32\runtimebroker.exe を追加し、それを "統合グラフィックス" プロセッサ上で強制的に実行します。</span><span class="sxs-lookup"><span data-stu-id="4f127-144">to add C:\windows\system32\runtimebroker.exe and force it to run on the "Integrated graphics" processor.</span></span> 

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a><span data-ttu-id="4f127-145">Windows Mixed Reality を使用すると Wi-Fi 速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="4f127-145">My Wi-Fi slows down when I'm using Windows Mixed Reality.</span></span>

<span data-ttu-id="4f127-146">2.4 GHz の Wi-Fi 接続を使用している場合、動作コントローラーは Wi-fi を遅くする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f127-146">If you're using a 2.4-GHz Wi-Fi connection, your motion controllers might slow down your Wi-Fi:</span></span>

* <span data-ttu-id="4f127-147">5 GHz の Wi-Fi 接続 (使用可能な場合) に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="4f127-147">Switch to a 5-GHz Wi-Fi connection, if one is available.</span></span> <span data-ttu-id="4f127-148">[詳細については、こちらを参照してください](https://support.microsoft.com/help/4000461)。</span><span class="sxs-lookup"><span data-stu-id="4f127-148">[Learn more](https://support.microsoft.com/help/4000461).</span></span>
* <span data-ttu-id="4f127-149">別の Bluetooth アダプターを使用して、動きコントローラーを PC に接続します。</span><span class="sxs-lookup"><span data-stu-id="4f127-149">Use a separate Bluetooth adapter to connect your motion controllers to your PC.</span></span> <span data-ttu-id="4f127-150">[推奨されるアダプター](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f127-150">See [recommended adapters](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).</span></span>

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a><span data-ttu-id="4f127-151">「PC に接続して充電する」というメッセージが表示されていました。</span><span class="sxs-lookup"><span data-stu-id="4f127-151">I got a message that said to plug in and charge my PC.</span></span> <span data-ttu-id="4f127-152">なぜでしょうか。</span><span class="sxs-lookup"><span data-stu-id="4f127-152">Why?</span></span>

<span data-ttu-id="4f127-153">ラップトップを使用している場合、Windows Mixed Reality は、PC が完全に充電され、電源が接続されている場合に最適に動作します。</span><span class="sxs-lookup"><span data-stu-id="4f127-153">If you're using a laptop, Windows Mixed Reality works best when the PC is both fully charged and plugged in.</span></span>

## <a name="what-is-the-experience-options-setting"></a><span data-ttu-id="4f127-154">エクスペリエンスオプションの設定は何ですか?</span><span class="sxs-lookup"><span data-stu-id="4f127-154">What is the Experience options setting?</span></span>

<span data-ttu-id="4f127-155">**設定 > mixed reality > ヘッドセットの表示 > エクスペリエンスのオプション** では、Windows Mixed reality のパフォーマンス設定を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4f127-155">**Settings > Mixed reality > Headset display > Experience options** allows you to change the Windows Mixed Reality performance settings.</span></span> <span data-ttu-id="4f127-156">これにより、さまざまなコンテンツにわたるハードウェア構成に最適なエクスペリエンスを選択できます。</span><span class="sxs-lookup"><span data-stu-id="4f127-156">This enables you to choose the best experience for your hardware configuration across a range of content.</span></span> <span data-ttu-id="4f127-157">次の3つのエクスペリエンスオプションから選択できます。</span><span class="sxs-lookup"><span data-stu-id="4f127-157">You have three experience options to choose from:</span></span>
* <span data-ttu-id="4f127-158">自動: Windows Mixed Reality は、ハードウェア構成に最適なエクスペリエンスを決定します。</span><span class="sxs-lookup"><span data-stu-id="4f127-158">Automatic: Windows Mixed Reality will determine the best experience for your hardware configuration.</span></span> <span data-ttu-id="4f127-159">ほとんどの場合、この方法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="4f127-159">For most people, this is the best choice to start with.</span></span>
* <span data-ttu-id="4f127-160">60 Hz: 更新間隔を 60 Hz に設定し、Mixed Reality ポータルでのビデオキャプチャやプレビューなどの特定の機能をオフにします。</span><span class="sxs-lookup"><span data-stu-id="4f127-160">60 Hz: Sets the refresh rate to 60 Hz and turns off certain features, such as video capture and preview in Mixed Reality Portal.</span></span>
* <span data-ttu-id="4f127-161">90 hz: リフレッシュレートを 90 Hz に設定します。</span><span class="sxs-lookup"><span data-stu-id="4f127-161">90 Hz: Sets the refresh rate to 90 Hz.</span></span>

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a><span data-ttu-id="4f127-162">Windows Mixed Reality でサポートされる言語</span><span class="sxs-lookup"><span data-stu-id="4f127-162">What languages are supported in Windows Mixed Reality</span></span>

<span data-ttu-id="4f127-163">Windows Mixed Reality は、次の言語で使用できます。</span><span class="sxs-lookup"><span data-stu-id="4f127-163">Windows Mixed Reality is available in the following languages:</span></span>

* <span data-ttu-id="4f127-164">簡体字中国語 (中国)</span><span class="sxs-lookup"><span data-stu-id="4f127-164">Chinese Simplified (China)</span></span>
* <span data-ttu-id="4f127-165">英語 (オーストラリア)</span><span class="sxs-lookup"><span data-stu-id="4f127-165">English (Australia)</span></span>
* <span data-ttu-id="4f127-166">英語 (カナダ)</span><span class="sxs-lookup"><span data-stu-id="4f127-166">English (Canada)</span></span>
* <span data-ttu-id="4f127-167">英語 (英国)</span><span class="sxs-lookup"><span data-stu-id="4f127-167">English (Great Britain)</span></span>
* <span data-ttu-id="4f127-168">英語 (米国)</span><span class="sxs-lookup"><span data-stu-id="4f127-168">English (United States)</span></span>
* <span data-ttu-id="4f127-169">フランス語 (カナダ)</span><span class="sxs-lookup"><span data-stu-id="4f127-169">French (Canada)</span></span>
* <span data-ttu-id="4f127-170">フランス語 (フランス)</span><span class="sxs-lookup"><span data-stu-id="4f127-170">French (France)</span></span>
* <span data-ttu-id="4f127-171">ドイツ語 (ドイツ)</span><span class="sxs-lookup"><span data-stu-id="4f127-171">German (Germany)</span></span>
* <span data-ttu-id="4f127-172">イタリア語 (イタリア)</span><span class="sxs-lookup"><span data-stu-id="4f127-172">Italian (Italy)</span></span>
* <span data-ttu-id="4f127-173">日本語 (日本)</span><span class="sxs-lookup"><span data-stu-id="4f127-173">Japanese (Japan)</span></span>
* <span data-ttu-id="4f127-174">スペイン語 (メキシコ)</span><span class="sxs-lookup"><span data-stu-id="4f127-174">Spanish (Mexico)</span></span>
* <span data-ttu-id="4f127-175">スペイン語 (スペイン)</span><span class="sxs-lookup"><span data-stu-id="4f127-175">Spanish (Spain)</span></span>

<span data-ttu-id="4f127-176">PC が別の言語に設定されている場合は、Windows Mixed Reality を使用できます。</span><span class="sxs-lookup"><span data-stu-id="4f127-176">You can use Windows Mixed Reality if your PC is set to a different language.</span></span> <span data-ttu-id="4f127-177">ただし、インターフェイスは英語 (米国) で表示され、音声コマンドやディクテーションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="4f127-177">However, the interface will appear in English (United States), and speech commands and dictation won't be available.</span></span> <span data-ttu-id="4f127-178">Windows Mixed Reality のスクリーンキーボードは英語 (米国) のみです。</span><span class="sxs-lookup"><span data-stu-id="4f127-178">The Windows Mixed Reality onscreen keyboard is English (United States) only.</span></span> <span data-ttu-id="4f127-179">別の言語でテキストを入力するには、PC に接続されている物理キーボードを使用します。</span><span class="sxs-lookup"><span data-stu-id="4f127-179">To enter text in another language, use a physical keyboard connected to your PC.</span></span> <span data-ttu-id="4f127-180">また、上記のサポートされている Windows Mixed Reality 言語のいずれかでディクテーションを使用することもできます。スクリーンキーボードで [マイク] を選択するだけです。</span><span class="sxs-lookup"><span data-stu-id="4f127-180">You can also use dictation in one of the supported Windows Mixed Reality languages listed above—just select microphone on the onscreen keyboard.</span></span>

<span data-ttu-id="4f127-181">Windows Mixed Reality は、次の言語でも使用できます。音声コマンドやディクテーション機能は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4f127-181">Windows Mixed Reality is also available in the following languages without speech commands or dictation features:</span></span>
* <span data-ttu-id="4f127-182">繁体字中国語 (台湾および香港)</span><span class="sxs-lookup"><span data-stu-id="4f127-182">Chinese Traditional (Taiwan and Hong Kong)</span></span>
* <span data-ttu-id="4f127-183">オランダ語 (オランダ)</span><span class="sxs-lookup"><span data-stu-id="4f127-183">Dutch (Netherlands)</span></span>
* <span data-ttu-id="4f127-184">韓国語 (韓国)</span><span class="sxs-lookup"><span data-stu-id="4f127-184">Korean (Korea)</span></span>
* <span data-ttu-id="4f127-185">ロシア語 (ロシア)</span><span class="sxs-lookup"><span data-stu-id="4f127-185">Russian (Russia)</span></span>

## <a name="i-have-questions-about-my-headset-hardware"></a><span data-ttu-id="4f127-186">ヘッドセットハードウェアに関する質問があります。</span><span class="sxs-lookup"><span data-stu-id="4f127-186">I have questions about my headset hardware.</span></span>

<span data-ttu-id="4f127-187">ヘッドセットの詳細については、製造元に確認してください。</span><span class="sxs-lookup"><span data-stu-id="4f127-187">For details about your headset, check with the manufacturer.</span></span> <span data-ttu-id="4f127-188">箱に製品ガイドがあるか、製造元の web サイトを試すことができます。</span><span class="sxs-lookup"><span data-stu-id="4f127-188">There may be a product guide in the box, or you can try the manufacturer’s website.</span></span>

## <a name="how-do-i-uninstall-windows-mixed-reality"></a><span data-ttu-id="4f127-189">Windows Mixed Reality をアンインストール操作方法には</span><span class="sxs-lookup"><span data-stu-id="4f127-189">How do I uninstall Windows Mixed Reality?</span></span>

1. <span data-ttu-id="4f127-190">ヘッドセットを PC から切断します。</span><span class="sxs-lookup"><span data-stu-id="4f127-190">Disconnect your headset from your PC.</span></span>
2. <span data-ttu-id="4f127-191">Windows Mixed Reality ポータルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="4f127-191">Close Windows Mixed Reality Portal.</span></span>
2. <span data-ttu-id="4f127-192">[> の設定の開始] を選択し  **> Mixed Reality** ] を選択し、[アンインストール] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4f127-192">Go to  **Start > Settings > Mixed Reality** and select "Uninstall".</span></span>

<span data-ttu-id="4f127-193">ヘッドセットの使用をもう一度開始する準備ができたら、プラグインに接続し、Windows Mixed Reality ポータルでセットアップを実行します。</span><span class="sxs-lookup"><span data-stu-id="4f127-193">When you're ready to start using your headset again, plug it in, and Windows Mixed Reality Portal will take you through setup.</span></span>

## <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a><span data-ttu-id="4f127-194">「Windows Mixed Reality のアンインストールを完了できませんでした」というメッセージが表示できました。</span><span class="sxs-lookup"><span data-stu-id="4f127-194">I got a "We couldn't finish uninstalling Windows Mixed Reality" message.</span></span>

<span data-ttu-id="4f127-195">お使いの環境に関する情報など、一部のファイルは依然としてコンピューターに存在している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f127-195">Some files, including information about your environment, might still be on your computer.</span></span> <span data-ttu-id="4f127-196">Windows Mixed Reality を後で再インストールする場合は、問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f127-196">This can cause problems if you decide to reinstall Windows Mixed Reality later.</span></span> <span data-ttu-id="4f127-197">レジストリを変更し、Windows PowerShell を使用してコマンドを実行することで、残りの Windows Mixed Reality 情報を PC から手動で削除できます。</span><span class="sxs-lookup"><span data-stu-id="4f127-197">You can manually remove any remaining Windows Mixed Reality info from your PC by modifying the registry and using Windows PowerShell to run commands.</span></span> <span data-ttu-id="4f127-198">_レジストリを正しく変更しないと、重大な問題が発生する可能性があります。必ずこれらの手順に従ってください。保護を強化するために、レジストリを変更する前にバックアップし、問題が発生した場合に復元できるようにします。_</span><span class="sxs-lookup"><span data-stu-id="4f127-198">_If you modify the registry incorrectly, serious problems might occur. Make sure to follow these steps carefully. For added protection, back up your registry before you modify it so you can restore it if a problem occurs._</span></span> <span data-ttu-id="4f127-199">詳細については、「 [Windows でレジストリをバックアップして再構築する方法](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f127-199">For more information, see [How to back up and restory the registry in Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows).</span></span> 

<span data-ttu-id="4f127-200">Windows mixed reality をアンインストールするには、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="4f127-200">To uninstall Windows mixed reality using these commands:</span></span>
1. <span data-ttu-id="4f127-201">PC を再起動します。</span><span class="sxs-lookup"><span data-stu-id="4f127-201">Restart your PC.</span></span>
2. <span data-ttu-id="4f127-202">**検索** ボックスに「regedit」と入力し、[はい] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4f127-202">In the **Search** box, type "regedit" and then select "Yes".</span></span>
3. <span data-ttu-id="4f127-203">次のレジストリ値を削除します。</span><span class="sxs-lookup"><span data-stu-id="4f127-203">Remove these registry values:</span></span>
   <ul>
    <li><span data-ttu-id="4f127-204"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>し、"" を削除します。</span><span class="sxs-lookup"><span data-stu-id="4f127-204"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, then delete "FirstRunSucceeded".</span></span></li> 
    <li><span data-ttu-id="4f127-205"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>、"PreferDesktopSpeaker" と "PreferDesktopMic" を削除します。</span><span class="sxs-lookup"><span data-stu-id="4f127-205"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic\SpeechAndAudio</b>, then delete "PreferDesktopSpeaker" and "PreferDesktopMic".</span></span></li> 
    <li><span data-ttu-id="4f127-206"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>をクリックし、次に "DisableSpeechInput" を削除します。</span><span class="sxs-lookup"><span data-stu-id="4f127-206"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore&gt; Settings\Holographic</b>, then delete "DisableSpeechInput".</span></span> <span data-ttu-id="4f127-207">注: HHKEY_CURRENT_USER のレジストリ項目は、Windows Mixed Reality を使用している PC 上のすべてのユーザーアカウントに対して削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f127-207">Note: The registry items in HHKEY_CURRENT_USER must be deleted for every user account on the PC that has used Windows Mixed Reality.</span></span></li> 
    <li><span data-ttu-id="4f127-208"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>、"DeviceID" と "Mode" を削除します。</span><span class="sxs-lookup"><span data-stu-id="4f127-208"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\PerceptionSimulationExtensions</b>, then delete "DeviceID" and "Mode".</span></span></li> 
    <li><span data-ttu-id="4f127-209"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>、"OnDeviceLearningCompleted" を削除します。</span><span class="sxs-lookup"><span data-stu-id="4f127-209"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Holographic</b>, then delete "OnDeviceLearningCompleted".</span></span></li> 
   </ul><span data-ttu-id="4f127-210">
4. 次のレジストリキーを削除します。</span><span class="sxs-lookup"><span data-stu-id="4f127-210">
4. Remove the following registry keys:</span></span> <ul>
   <li> <span data-ttu-id="4f127-211"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span><span class="sxs-lookup"><span data-stu-id="4f127-211"><b>HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span></span></li> 
   <li> <span data-ttu-id="4f127-212"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span><span class="sxs-lookup"><span data-stu-id="4f127-212"><b>HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\HoloSI</b></span></span></li> 
   <li> <span data-ttu-id="4f127-213"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></span><span class="sxs-lookup"><span data-stu-id="4f127-213"><b>HKEY_CURRENT_USER\Software\Microsoft\Speech_OneCore\Settings\HolographicPreferences</b></span></span></li><br/></ul><span data-ttu-id="4f127-214">
5. レジストリエディターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="4f127-214">
5. Close the Registry Editor.</span></span>
<span data-ttu-id="4f127-215">6.**C:\Users\user name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \ localstate** にアクセスし、"RoomBounds.json" を削除します。</span><span class="sxs-lookup"><span data-stu-id="4f127-215">6. Go to **C:\Users\user name\AppData\Local\Packages\Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy\LocalState** and delete "RoomBounds.json".</span></span> <span data-ttu-id="4f127-216">Windows Mixed Reality を使用したユーザーごとに、この手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="4f127-216">Repeat this for each user who has used Windows Mixed Reality.</span></span>
<span data-ttu-id="4f127-217">7. 管理者コマンドプロンプトを開き、 **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="4f127-217">7. Open admin cmd prompt and go to **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors**.</span></span> <span data-ttu-id="4f127-218">"ヘッド追跡データ" フォルダーの内容を削除します (フォルダー自体は削除しません)。</span><span class="sxs-lookup"><span data-stu-id="4f127-218">Delete the contents of the "HeadTracking data" folder (but not the folder itself).</span></span>
<span data-ttu-id="4f127-219">8. [検索] ボックスに「powershell」と入力し、[Windows PowerShell] を右クリックして、[管理者として実行] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4f127-219">8. Type "powershell" in the "Search box", right-click "Windows PowerShell", and then select "Run as administrator".</span></span>
<span data-ttu-id="4f127-220">9. Windows PowerShell の場合:</span><span class="sxs-lookup"><span data-stu-id="4f127-220">9. In Windows PowerShell:</span></span> <ul>
   <li><span data-ttu-id="4f127-221">コマンドプロンプトで、 <b>Dism/Online/Get-Capabilities</b>をコピーして貼り付け、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="4f127-221">At the command prompt, copy and paste <b>Dism /online /Get-Capabilities</b>, then press Enter.</span></span></b></li> 
   <li><span data-ttu-id="4f127-222">Holographic で始まる機能 Id をコピーします。</span><span class="sxs-lookup"><span data-stu-id="4f127-222">Copy the Capability Identity that begins with Analog.Holographic.Desktop.</span></span> <span data-ttu-id="4f127-223">存在しない場合は、項目がインストールされていないので、手順10に進みます。</span><span class="sxs-lookup"><span data-stu-id="4f127-223">If it isn't there, the item isn't installed and you can skip to step 10).</span></span></li> 
   <li><span data-ttu-id="4f127-224">次のコマンドプロンプトをコピーして貼り付け、enter キーを押します。 <b>Dism/Online/Remove-Capability/CapabilityName: 最後の手順でコピーされた機能 id</b></span><span class="sxs-lookup"><span data-stu-id="4f127-224">Copy and paste the following command prompt, then press Enter: <b>Dism /online /Remove-Capability /CapabilityName: the Capability Identity copied in the last step</b></span></span></li>
   </ul><span data-ttu-id="4f127-225">
10. PC を再起動します。</span><span class="sxs-lookup"><span data-stu-id="4f127-225">
10. Restart your PC.</span></span>

