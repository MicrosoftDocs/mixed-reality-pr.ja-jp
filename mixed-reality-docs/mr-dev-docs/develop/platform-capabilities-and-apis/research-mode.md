---
title: HoloLens Research モード
description: HoloLens で Research モードを使用すると、アプリケーションは主要なデバイスセンサーストリーム (深さ、環境追跡、および赤外線反射) にアクセスできます。
author: hferrone
ms.author: v-hferrone
ms.date: 07/31/2020
ms.topic: article
keywords: Research モード, cv, rs4, コンピュータービジョン, 研究, HoloLens, HoloLens 2
ms.openlocfilehash: 6c40ac814a5dacfdbb942aec8200f46157bea161
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530090"
---
# <a name="hololens-research-mode"></a><span data-ttu-id="b5f64-104">HoloLens Research モード</span><span class="sxs-lookup"><span data-stu-id="b5f64-104">HoloLens Research Mode</span></span>

<span data-ttu-id="b5f64-105">検索モードは、キーセンサーへのアクセスを提供するために HoloLens (第1世代) デバイスで導入されました。特に、展開を意図していない研究アプリケーションに使用します。</span><span class="sxs-lookup"><span data-stu-id="b5f64-105">Research Mode was introduced on HoloLens (1st Gen) devices to give access to key sensors, specifically for research applications that aren't intended for deployment.</span></span>  <span data-ttu-id="b5f64-106">HoloLens 2 の研究モードでは、HoloLens 1 の機能は維持されますが、次のストリームへのアクセス権が追加されます。</span><span class="sxs-lookup"><span data-stu-id="b5f64-106">Research Mode for HoloLens 2 keeps the capabilities of HoloLens 1 but adds access to the following streams:</span></span>

* <span data-ttu-id="b5f64-107">**可視性の低い環境の追跡カメラ** -ヘッドの追跡とマップの作成にシステムが使用するグレースケールのカメラです。</span><span class="sxs-lookup"><span data-stu-id="b5f64-107">**Visible Light Environment Tracking Cameras** - Gray-scale cameras used by the system for head tracking and map building.</span></span>
* <span data-ttu-id="b5f64-108">**深度カメラ** –2つのモードで動作します。</span><span class="sxs-lookup"><span data-stu-id="b5f64-108">**Depth Camera** – Operates in two modes:</span></span>  
    + <span data-ttu-id="b5f64-109">セルフトラッキングに使用される AHAT、高頻度 (45 FPS) のほぼ深い検出。</span><span class="sxs-lookup"><span data-stu-id="b5f64-109">AHAT, high-frequency (45 FPS) near-depth sensing used for hand tracking.</span></span> <span data-ttu-id="b5f64-110">最初のバージョンの短いスローモードとは別に、AHAT では、1メーターを超えるフェーズラップに擬似的な深さが与えられます。</span><span class="sxs-lookup"><span data-stu-id="b5f64-110">Differently from the first version short-throw mode, AHAT gives pseudo-depth with phase wrap beyond 1 meter.</span></span> 
    + <span data-ttu-id="b5f64-111">Long throw、低頻度 (1-5 FPS)、[空間マッピング](../../design/spatial-mapping.md)で使用される深い深さの検出</span><span class="sxs-lookup"><span data-stu-id="b5f64-111">Long-throw, low-frequency (1-5 FPS) far-depth sensing used by [Spatial Mapping](../../design/spatial-mapping.md)</span></span>

* <span data-ttu-id="b5f64-112">**IR 反射率ストリームの2つのバージョン** 。 HoloLens が計算に使用します。</span><span class="sxs-lookup"><span data-stu-id="b5f64-112">**Two versions of the IR-reflectivity stream** - Used by the HoloLens to compute depth.</span></span> <span data-ttu-id="b5f64-113">これらのイメージは赤外線によって照らされ、アンビエントに見える光の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="b5f64-113">These images are illuminated by infrared and unaffected by ambient visible light.</span></span>

<span data-ttu-id="b5f64-114">HoloLens 2 を使用している場合は、以下の追加入力にもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b5f64-114">If you're using a HoloLens 2, you also have access to the additional inputs below:</span></span>

* <span data-ttu-id="b5f64-115">**加速度計** –システムによって使用され、X 軸、Y 軸、Z 軸、重力に沿った線形加速度を決定します。</span><span class="sxs-lookup"><span data-stu-id="b5f64-115">**Accelerometer** – Used by the system to determine linear acceleration along the X, Y, and Z axes and gravity.</span></span>
* <span data-ttu-id="b5f64-116">**ジャイロ** –回転を決定するためにシステムによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="b5f64-116">**Gyro** – Used by the system to determine rotations.</span></span>
* <span data-ttu-id="b5f64-117">**磁力計** –絶対方向を推定するためにシステムによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="b5f64-117">**Magnetometer** – Used by the system to estimate absolute orientation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5f64-118">リサーチモードは現在パブリックプレビュー段階です。</span><span class="sxs-lookup"><span data-stu-id="b5f64-118">Research Mode is currently in Public Preview.</span></span> 

<span data-ttu-id="b5f64-119">![Research モードアプリのスクリーンショット](images/sensor-stream-viewer.jpg)</span><span class="sxs-lookup"><span data-stu-id="b5f64-119">![Research Mode app screenshot](images/sensor-stream-viewer.jpg)</span></span><br>
<span data-ttu-id="b5f64-120">*リサーチモードで使用可能な8個のセンサーストリームを表示するテストアプリケーションの mixed reality キャプチャ*</span><span class="sxs-lookup"><span data-stu-id="b5f64-120">*A mixed reality capture of a test application that displays the eight sensor streams available in Research Mode*</span></span>

## <a name="usage"></a><span data-ttu-id="b5f64-121">使用</span><span class="sxs-lookup"><span data-stu-id="b5f64-121">Usage</span></span>

<span data-ttu-id="b5f64-122">研究モードは、Computer Vision およびロボットのフィールドの新しいアイデアを調査する教育機関および産業用の研究者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="b5f64-122">Research Mode is designed for academic and industrial researchers exploring new ideas in the fields of Computer Vision and Robotics.</span></span>  <span data-ttu-id="b5f64-123">これは、エンタープライズ環境に配置されているアプリケーションや、Microsoft Store またはその他の配布チャネルを通じて利用できるアプリケーションを対象としていません。</span><span class="sxs-lookup"><span data-stu-id="b5f64-123">It's not intended for applications deployed in enterprise environments or available through the Microsoft Store or other distribution channels.</span></span>

<span data-ttu-id="b5f64-124">さらに、Microsoft は、今後のハードウェアまたは OS の更新で、リサーチモードまたは同等の機能がサポートされることを保証しません。</span><span class="sxs-lookup"><span data-stu-id="b5f64-124">Additionally, Microsoft doesn't provide assurances that Research Mode or equivalent functionality is going to be supported in future hardware or OS updates.</span></span> <span data-ttu-id="b5f64-125">しかし、それを使用して新しいアイデアを開発し、テストすることをやめてください。</span><span class="sxs-lookup"><span data-stu-id="b5f64-125">However, don't let that stop you from using it to develop and test new ideas!</span></span>

## <a name="security-and-performance"></a><span data-ttu-id="b5f64-126">セキュリティとパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="b5f64-126">Security and performance</span></span>

<span data-ttu-id="b5f64-127">リサーチモードを有効にすると、通常の条件下で HoloLens 2 を使用した場合よりも多くのバッテリ電源が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b5f64-127">Enabling Research Mode uses more battery power than using the HoloLens 2 under normal conditions, even if the application using the Research Mode features isn't running.</span></span>  <span data-ttu-id="b5f64-128">このモードを有効にすると、アプリケーションがセンサーデータを誤用する可能性があるため、デバイスの全体的なセキュリティを低下させることもできます。</span><span class="sxs-lookup"><span data-stu-id="b5f64-128">Enabling this mode can also lower the overall security of your device because applications may misuse sensor data.</span></span>  <span data-ttu-id="b5f64-129">デバイスのセキュリティの詳細については、「 [HoloLens のセキュリティ](https://docs.microsoft.com/hololens/hololens-faq-security)に関する FAQ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5f64-129">You can find more information on device security in the [HoloLens security FAQ](https://docs.microsoft.com/hololens/hololens-faq-security).</span></span>  

## <a name="device-support"></a><span data-ttu-id="b5f64-130">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="b5f64-130">Device support</span></span>
<table><span data-ttu-id="b5f64-131">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span><span class="sxs-lookup"><span data-stu-id="b5f64-131">
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" /> </colgroup>
    </span></span><tr>
        <td><span data-ttu-id="b5f64-132"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="b5f64-132"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="b5f64-133"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens 第 1 世代</strong></a></span><span class="sxs-lookup"><span data-stu-id="b5f64-133"><a href="https://docs.microsoft.com/hololens/hololens1-hardware"><strong>HoloLens first Gen</strong></a></span></span></td>
        <td><span data-ttu-id="b5f64-134"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="b5f64-134"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="b5f64-135">ヘッドトラッキングカメラ</span><span class="sxs-lookup"><span data-stu-id="b5f64-135">Head Tracking Cameras</span></span></td>
        <td><span data-ttu-id="b5f64-136">✔️</span><span class="sxs-lookup"><span data-stu-id="b5f64-136">✔️</span></span></td>
        <td><span data-ttu-id="b5f64-137">✔️</span><span class="sxs-lookup"><span data-stu-id="b5f64-137">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b5f64-138">IR カメラ & 深度</span><span class="sxs-lookup"><span data-stu-id="b5f64-138">Depth & IR Camera</span></span></td>
        <td><span data-ttu-id="b5f64-139">✔️</span><span class="sxs-lookup"><span data-stu-id="b5f64-139">✔️</span></span></td>
        <td><span data-ttu-id="b5f64-140">✔️</span><span class="sxs-lookup"><span data-stu-id="b5f64-140">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b5f64-141">加速度計</span><span class="sxs-lookup"><span data-stu-id="b5f64-141">Accelerometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="b5f64-142">✔️</span><span class="sxs-lookup"><span data-stu-id="b5f64-142">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b5f64-143">ジャイロスコープ</span><span class="sxs-lookup"><span data-stu-id="b5f64-143">Gyroscope</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="b5f64-144">✔️</span><span class="sxs-lookup"><span data-stu-id="b5f64-144">✔️</span></span></td>
    </tr>
    <tr>
        <td><span data-ttu-id="b5f64-145">磁力計</span><span class="sxs-lookup"><span data-stu-id="b5f64-145">Magnetometer</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="b5f64-146">✔️</span><span class="sxs-lookup"><span data-stu-id="b5f64-146">✔️</span></span></td>
    </tr>
</table>

## <a name="enabling-research-mode-hololens-first-gen-and-hololens-2"></a><span data-ttu-id="b5f64-147">リサーチモードの有効化 (HoloLens first Gen および HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="b5f64-147">Enabling Research Mode (HoloLens first Gen and HoloLens 2)</span></span>

<span data-ttu-id="b5f64-148">リサーチモードは、開発者モードの拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="b5f64-148">Research Mode is an extension of Developer Mode.</span></span> <span data-ttu-id="b5f64-149">開始する前に、デバイスの開発機能を有効にして、リサーチモードの設定にアクセスできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5f64-149">Before starting, the developer features of the device need to be enabled to access the Research Mode settings:</span></span> 

* <span data-ttu-id="b5f64-150">[ **スタート] メニューを開き > 設定** を開き、[ **更新プログラム**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b5f64-150">Open **Start Menu > Settings** and select **Updates**.</span></span>
* <span data-ttu-id="b5f64-151">**開発者向けに** 選択し、**開発者モード** を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b5f64-151">Select **For Developers** and enable **Developer Mode**.</span></span>
* <span data-ttu-id="b5f64-152">下へスクロールし、**デバイス ポータル** を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b5f64-152">Scroll down and enable **Device Portal**.</span></span>

<span data-ttu-id="b5f64-153">開発者向け機能が有効になったら、 [デバイスポータルに接続](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) して、リサーチモードの機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b5f64-153">After the developer features  are enabled, [connect to the device portal](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-hololens) to enable the Research Mode features:</span></span>

* <span data-ttu-id="b5f64-154">**デバイスポータル** で、**システム > リサーチモード** に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="b5f64-154">Go to **System > Research Mode** in the **Device Portal**.</span></span>
* <span data-ttu-id="b5f64-155">[ **センサーストリームへのアクセスを許可する**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b5f64-155">Select **Allow access to sensor stream**.</span></span>
* <span data-ttu-id="b5f64-156">ページの上部にある **電源** メニュー項目からデバイスを再起動します。</span><span class="sxs-lookup"><span data-stu-id="b5f64-156">Restart the device from the **Power** menu item at the top of the page.</span></span>

<span data-ttu-id="b5f64-157">デバイスを再起動すると、 **デバイスポータル** から読み込まれたアプリケーションは、リサーチモードのストリームにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="b5f64-157">Once you've restarted the device, the applications loaded through the **Device Portal** can access Research Mode streams.</span></span>

<span data-ttu-id="b5f64-158">![HoloLens デバイスポータルの [リサーチモード] タブ](images/ResearchModeDevPortal.png)</span><span class="sxs-lookup"><span data-stu-id="b5f64-158">![Research Mode tab of HoloLens Device Portal](images/ResearchModeDevPortal.png)</span></span><br>
<span data-ttu-id="b5f64-159">*HoloLens デバイスポータルの [リサーチモード] ウィンドウ*</span><span class="sxs-lookup"><span data-stu-id="b5f64-159">*Research Mode window in the HoloLens Device Portal*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5f64-160">HoloLens 2 の研究モードは、ビルド19041.1356 以降で使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5f64-160">Research Mode for HoloLens 2 is available beginning with build 19041.1356.</span></span> <span data-ttu-id="b5f64-161">以前のビルドでアクセスする必要がある場合は、 [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) プログラムにサインアップしてください。</span><span class="sxs-lookup"><span data-stu-id="b5f64-161">If you need access in an earlier build, sign up for our [Insider Preview](https://docs.microsoft.com/hololens/hololens-insider) program.</span></span>

### <a name="using-sensor-data-in-your-apps"></a><span data-ttu-id="b5f64-162">アプリでセンサーデータを使用する</span><span class="sxs-lookup"><span data-stu-id="b5f64-162">Using sensor data in your apps</span></span>

<span data-ttu-id="b5f64-163">アプリケーションは、写真やビデオのカメラストリームにアクセス [メディアファンデーション](https://msdn.microsoft.com/library/windows/desktop/ms694197) するのと同じ方法でセンサーストリームデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b5f64-163">Applications can access the sensor stream data in the same way that [Media Foundation](https://msdn.microsoft.com/library/windows/desktop/ms694197) accesses photo and video camera streams.</span></span> 

<span data-ttu-id="b5f64-164">HoloLens 開発に使用できるすべての Api は、リサーチモードでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5f64-164">All APIs that work for HoloLens development are also available in Research Mode.</span></span> <span data-ttu-id="b5f64-165">具体的には、アプリケーションは、各センサーフレームのキャプチャ時間で HoloLens が6つの領域にあることを正確に把握しています。</span><span class="sxs-lookup"><span data-stu-id="b5f64-165">In particular, the application  knows precisely where HoloLens is in 6DoF space at each sensor frame capture time.</span></span>

<span data-ttu-id="b5f64-166">サンプルアプリケーションを使用して、リサーチモードのストリームアクセス、 [組み込みと extrを](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world)使用した ics、およびストリームの記録を示しています。</span><span class="sxs-lookup"><span data-stu-id="b5f64-166">We have sample applications showing Research Mode stream access, using the [intrinsics and extrinsics](https://docs.microsoft.com/windows/mixed-reality/locatable-camera#locating-the-device-camera-in-the-world), and recording streams:</span></span>
* [<span data-ttu-id="b5f64-167">HoloLens (最初の世代)</span><span class="sxs-lookup"><span data-stu-id="b5f64-167">HoloLens (first gen)</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="b5f64-168">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="b5f64-168">HoloLens 2</span></span>](https://github.com/microsoft/HoloLens2ForCV)

## <a name="support"></a><span data-ttu-id="b5f64-169">サポート</span><span class="sxs-lookup"><span data-stu-id="b5f64-169">Support</span></span>

<span data-ttu-id="b5f64-170">HoloLens (最初の世代) の場合は、HoloLensForCV リポジトリの [issue tracker](https://github.com/Microsoft/HololensForCV/issues) を使用してフィードバックを投稿し、既知の問題を追跡します。</span><span class="sxs-lookup"><span data-stu-id="b5f64-170">For HoloLens (first gen), use the [issue tracker](https://github.com/Microsoft/HololensForCV/issues) in the HoloLensForCV repository to post feedback and track known issues.</span></span>

<span data-ttu-id="b5f64-171">HoloLens 2 の場合は、HoloLens2ForCV リポジトリの [問題トラッカー](https://github.com/microsoft/HoloLens2ForCV/issues) を使用してフィードバックを投稿し、既知の問題を追跡します。</span><span class="sxs-lookup"><span data-stu-id="b5f64-171">For HoloLens 2, use the [issue tracker](https://github.com/microsoft/HoloLens2ForCV/issues) in the HoloLens2ForCV repository to post feedback and track known issues.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5f64-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5f64-172">See also</span></span>

* [<span data-ttu-id="b5f64-173">Microsoft メディア ファンデーション</span><span class="sxs-lookup"><span data-stu-id="b5f64-173">Microsoft Media Foundation</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms694197)
* [<span data-ttu-id="b5f64-174">HoloLensForCV GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="b5f64-174">HoloLensForCV GitHub repo</span></span>](https://github.com/Microsoft/HoloLensForCV)
* [<span data-ttu-id="b5f64-175">HoloLens2ForCV GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="b5f64-175">HoloLens2ForCV GitHub repo</span></span>](https://github.com/microsoft/HoloLens2ForCV)
* [<span data-ttu-id="b5f64-176">Windows Device Portal を使用する</span><span class="sxs-lookup"><span data-stu-id="b5f64-176">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
