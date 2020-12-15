---
title: Unreal Insights を使用したプロファイリング
description: HoloLens 2 で Unreal Insights を使用する方法について説明します。
author: sajidfarooq
ms.author: v-hferrone
ms.date: 12/10/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、development、プロファイリング、Unreal insights、documentation、ガイド、features、ホログラム、game development、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: 20e620f147f2cf5ee05073467c8ce7335340d59d
ms.sourcegitcommit: 53bde413a174712cb9d3794d02d96363a2d599cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97486377"
---
# <a name="profiling-with-unreal-insights"></a><span data-ttu-id="c145e-104">Unreal Insights を使用したプロファイリング</span><span class="sxs-lookup"><span data-stu-id="c145e-104">Profiling with Unreal Insights</span></span> 

<span data-ttu-id="c145e-105">[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) は、Unreal Engine のデータを収集、分析、視覚化するプロファイルシステムです。</span><span class="sxs-lookup"><span data-stu-id="c145e-105">[Unreal Insights](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Overview/index.html) is a profiling system that collects, analyzes, and visualizes data from Unreal Engine.</span></span> <span data-ttu-id="c145e-106">プロファイリングシステムを使用すると、最適化のボトルネックや、アプリのパフォーマンスが向上する可能性のある領域を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="c145e-106">The profiling system can help you find optimization bottlenecks and areas where you apps performance could use a boost.</span></span> <span data-ttu-id="c145e-107">通常は、エディターから Unreal Insights を有効にしますが、HoloLens 2 の場合はコマンドラインを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c145e-107">Normally, you enable Unreal Insights right from the editor, but for HoloLens 2 you'll need to use the command line.</span></span>  

## <a name="setup"></a><span data-ttu-id="c145e-108">セットアップ</span><span class="sxs-lookup"><span data-stu-id="c145e-108">Setup</span></span>

<span data-ttu-id="c145e-109">Unreal では、HoloLens ランチャーで "カスタムプロファイル" を作成して構成し、コマンドラインパラメーターを使用して Unreal Insights を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c145e-109">Unreal lets you to create and configure a "Custom Profile" in the HoloLens launcher with the command line parameters that enable Unreal Insights.</span></span>

1.  <span data-ttu-id="c145e-110">コマンドプロンプトで **ipconfig** コマンドを使用して、コンピューターの IP アドレスを検索します。</span><span class="sxs-lookup"><span data-stu-id="c145e-110">Find the IP address of your computer using the **ipconfig** command on the command prompt.</span></span> <span data-ttu-id="c145e-111">IP アドレスは、ipconfig によって示される IPv4 アドレスです。</span><span class="sxs-lookup"><span data-stu-id="c145e-111">The IP address is the IPv4 address listed by ipconfig.</span></span> <span data-ttu-id="c145e-112">後でコマンドラインパラメーターを設定するときは、この点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c145e-112">Keep this in mind for later when you set Command Line Parameters.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c145e-113">VPN の背後にいる場合は、代わりに VPN 経由で提供される IP アドレスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c145e-113">If you're behind a VPN, you may need to provide the IP address provided via the VPN instead.</span></span>

![Ipconfig コマンドのコマンドラインの結果のスクリーンショット](images/unreal-insights-img-01.png)

2.  <span data-ttu-id="c145e-115">Unreal Engine パネルの上部に戻り、[Launch] \ (**起動**\) ボタンの下に **デバイスマネージャー** を開きます。</span><span class="sxs-lookup"><span data-stu-id="c145e-115">Go to the top of the Unreal Engine panel and open **Device Manager** under the **Launch** button:</span></span>

![デバイスマネージャーが強調表示されている起動オプションのスクリーンショット](images/unreal-insights-img-02.png)

3.  <span data-ttu-id="c145e-117">[デバイスマネージャーで、[ **一覧** にないデバイスの追加] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c145e-117">In the Device Manager, select **Add an Unlisted Device**:</span></span>

![Unreal engine で開かれるデバイスマネージャーのスクリーンショット](images/unreal-insights-img-03.png)

4. <span data-ttu-id="c145e-119">[ **プラットフォームの選択** ] をクリックし、[ **HoloLens**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c145e-119">Click **Select a platform** and choose **HoloLens**:</span></span>

![HoloLens が強調表示された [一覧にないデバイスの追加] ドロップダウンのスクリーンショット](images/unreal-insights-img-04.png)

5.  <span data-ttu-id="c145e-121">IPoverUSB を使用している場合は、デバイス Id として 127.0.0.1: 10080 を入力します。</span><span class="sxs-lookup"><span data-stu-id="c145e-121">If you're using IPoverUSB, enter 127.0.0.1:10080 as the Device Identifier.</span></span> <span data-ttu-id="c145e-122">HoloLens のユーザーとパスワードをそれぞれのフィールドに入力し、必要に応じて **表示名** を入力します。</span><span class="sxs-lookup"><span data-stu-id="c145e-122">Enter your HoloLens user and password in their respective fields and fill **Display Name** as you wish.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c145e-123">デバイス Id は HoloLens の IP アドレスであり、手順 1. で見つかった Unreal Insights を実行しているコンピューターではありません。</span><span class="sxs-lookup"><span data-stu-id="c145e-123">The Device Identifier is the IP address of the HoloLens, NOT of the computer running Unreal Insights you found in step 1.</span></span>

![デバイスマネージャーでの HoloLens デバイスの詳細のスクリーンショット](images/unreal-insights-img-05.png)

6.  <span data-ttu-id="c145e-125">[ **追加** ] を選択すると、デバイスマネージャーのデバイスの一覧に HoloLens が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c145e-125">Select **Add** and your HoloLens should appear in the device list of the device manager:</span></span>

![デバイス一覧に追加された HoloLens のスクリーンショット](images/unreal-insights-img-06.png)

## <a name="launch"></a><span data-ttu-id="c145e-127">Launch</span><span class="sxs-lookup"><span data-stu-id="c145e-127">Launch</span></span>

1. <span data-ttu-id="c145e-128">[**起動**] ボタンの下にある [UE4] パネルから **プロジェクトランチャー** を開きます。</span><span class="sxs-lookup"><span data-stu-id="c145e-128">Open **Project Launcher** from the UE4 panel under the **Launch** button:</span></span>

![プロジェクトランチャーが強調表示されている起動オプションのスクリーンショット](images/unreal-insights-img-07.png)

2. <span data-ttu-id="c145e-130">カスタム **+** **起動プロファイル** にカスタムプロファイルを作成するには、このボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="c145e-130">Select the **+** button to create a custom profile under **Custom Launch Profiles**.</span></span> <span data-ttu-id="c145e-131">作成した後は、いつでもこのプロファイルを編集できます。</span><span class="sxs-lookup"><span data-stu-id="c145e-131">Once created, you can always edit this profile later:</span></span>

![カスタム起動プロファイルが強調表示されているプロジェクトランチャーのスクリーンショット](images/unreal-insights-img-08.png)

3. <span data-ttu-id="c145e-133">HoloLens カスタム起動プロファイルの [ **プロファイルの編集** ] ボタンを選択し、次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="c145e-133">Select **edit profile** button on the HoloLens custom launch profile and configure:</span></span>
    * <span data-ttu-id="c145e-134">デバイスへのコピーを有効にするに **は、ブックで**[**クック**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c145e-134">Select **Cook** to **By the Book** to enable copying to device</span></span>
    * <span data-ttu-id="c145e-135">[**アーカイブ**] セクションの [アーカイブします **か?** ] をオンにして、削除するのではなく、生成された .appxbundle を保持し、ディスク領域を節約することができます。</span><span class="sxs-lookup"><span data-stu-id="c145e-135">You may want to check **Do you wish to archive?** in the **Archive** section to retain the generated .appxbundle rather than deleting to save disk space.</span></span> <span data-ttu-id="c145e-136">.Appxbundle の場所を指定し、必要に応じて開発ビルドに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="c145e-136">Specify a location for the .appxbundle and switch to a development build if you wish</span></span>

![書籍と HoloLens が強調表示されているプロファイル構成のクックオプションのスクリーンショット](images/unreal-insights-img-09.png)

4. <span data-ttu-id="c145e-138">**ビルドを展開する方法** を設定しますか? [**デバイスにコピー** ] を選択して、UI の **起動** セクションをアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="c145e-138">Set **How would you like to deploy the build?** to **Copy to device** to activate the **Launch** section of the UI:</span></span>

![デバイスへのコピーが強調表示されている配置オプションを使用したプロジェクトランチャーのスクリーンショット](images/unreal-insights-img-10.png)

5. <span data-ttu-id="c145e-140">[**起動**] セクションで、**追加のコマンドラインパラメーター** を設定します。</span><span class="sxs-lookup"><span data-stu-id="c145e-140">Set **Additional Command Line Parameters** in the **Launch** section.</span></span> <span data-ttu-id="c145e-141">パラメーターは ue4commandline.txt ファイルに書き込まれ、バンドルにパッケージ化されて、起動時に使用されます。</span><span class="sxs-lookup"><span data-stu-id="c145e-141">The parameters will be written into a ue4commandline.txt file, packaged into the bundle, and used at launch.</span></span> 
    <!-- TODO: Need more detail on what this parameter does and where to find others. -->
    * <span data-ttu-id="c145e-142">次のことを試してみてください。 **-tracehost = IP_OF_YOUR_PC-trace = Log、Bookmark、Frame、CPU、GPU、LoadTime、File、Net**</span><span class="sxs-lookup"><span data-stu-id="c145e-142">Try these for starters: **-tracehost=IP_OF_YOUR_PC -trace=Log,Bookmark,Frame,CPU,GPU,LoadTime,File,Net**</span></span>
    * <span data-ttu-id="c145e-143">使用可能な起動パラメーターの完全な一覧については、 [Unreal Insights のリファレンスドキュメントを参照](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html)してください。</span><span class="sxs-lookup"><span data-stu-id="c145e-143">You can find a complete list of available launch parameters in the [Unreal Insights reference documentation](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/Reference/index.html).</span></span>

> [!NOTE]
> <span data-ttu-id="c145e-144">"IP_OF_YOUR_PC" は、手順 1. で見つかった IP アドレスです。</span><span class="sxs-lookup"><span data-stu-id="c145e-144">"IP_OF_YOUR_PC" is the IP address we found in step 1.</span></span> <span data-ttu-id="c145e-145">これは、HoloLens の IP アドレスではなく、Unreal Insights を実行しているコンピューターの IP アドレスです。</span><span class="sxs-lookup"><span data-stu-id="c145e-145">This is the IP address of the computer running Unreal Insights, NOT the IP address of the HoloLens.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c145e-146">トレースが非常に高速になります。</span><span class="sxs-lookup"><span data-stu-id="c145e-146">Traces can get large very quickly.</span></span> <span data-ttu-id="c145e-147">トレースサイズを低く保つために必要なチャネルのみを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c145e-147">Enable only those channels you need to keep trace size low.</span></span>

![起動構成オプションのスクリーンショット](images/unreal-insights-img-11.png)

6. <span data-ttu-id="c145e-149">アプリを起動する前に、Unreal insights を起動します。そうしないと、アプリの前に実際の情報を適切に初期化できません。</span><span class="sxs-lookup"><span data-stu-id="c145e-149">Launch Unreal Insights BEFORE app launch, otherwise Unreal Insights wont be able to initialize appropriately before the app:</span></span>
    * <span data-ttu-id="c145e-150">Unreal Insights の実行可能ファイルは、通常は次のように、バイナリエンジンフォルダーに格納されます。 "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span><span class="sxs-lookup"><span data-stu-id="c145e-150">The Unreal Insights executable is stored in the binaries engine folder, usually as follows: "C:\Program Files\Epic Games\UE_4.26\Engine\Binaries\Win64\UnrealInsights.exe"</span></span>

![実行中の unreal insights 実行可能ファイルのスクリーンショット](images/unreal-insights-img-12.png)

6.  <span data-ttu-id="c145e-152">[ **戻る** ] を選択して、 **プロジェクトランチャー** ダイアログのルートに戻ります。</span><span class="sxs-lookup"><span data-stu-id="c145e-152">Select **Back** to return to the root of the **Project Launcher** dialog</span></span>
7.  <span data-ttu-id="c145e-153">エディターに戻り、カスタム起動プロファイルで [ **起動** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c145e-153">Back in the editor, Click **Launch** on your custom launch profile</span></span>

![カスタム起動プロファイルのスクリーンショット](images/unreal-insights-img-13.png)

8.  <span data-ttu-id="c145e-155">プロジェクトがパッケージ化され、デバイスにインストールされ、起動します。</span><span class="sxs-lookup"><span data-stu-id="c145e-155">Watch as your project is packaged up, installed on your device, and launched</span></span>

## <a name="profiling"></a><span data-ttu-id="c145e-156">プロファイル</span><span class="sxs-lookup"><span data-stu-id="c145e-156">Profiling</span></span>

<span data-ttu-id="c145e-157">Unreal Insights に戻り、デバイスへの **ライブ** 接続を選択してプロファイリングを開始します</span><span class="sxs-lookup"><span data-stu-id="c145e-157">Back in Unreal Insights, select the **Live** connection to your device to start profiling</span></span>

<span data-ttu-id="c145e-158">カスタムプロファイルは、プロジェクト間で共有されます。</span><span class="sxs-lookup"><span data-stu-id="c145e-158">The custom profile is shared between projects.</span></span> <span data-ttu-id="c145e-159">ここからは、毎回作成したカスタムプロファイルを使用できます。これを毎回行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c145e-159">From here on out, you can use the custom profile you created instead of having to do this every time.</span></span> <span data-ttu-id="c145e-160">[セットアップセクション](#setup)で手順 3. ~ 6. を実行するたびに、デバイスへの接続を再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c145e-160">You only need to recreate the connection to the device every time you start Unreal with steps 3 to 6 in the [setup section](#setup).</span></span>

## <a name="see-also"></a><span data-ttu-id="c145e-161">関連項目</span><span class="sxs-lookup"><span data-stu-id="c145e-161">See also</span></span>
* [<span data-ttu-id="c145e-162">Unreal Insights のドキュメント</span><span class="sxs-lookup"><span data-stu-id="c145e-162">Unreal Insights documentation</span></span>](https://docs.unrealengine.com/TestingAndOptimization/PerformanceAndProfiling/UnrealInsights/index.html)

