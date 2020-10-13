---
title: Unreal での QR コード
description: Unreal で QR コードを使用するためのガイド
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, QR コード
ms.openlocfilehash: 0f0507e2f726830cef27c190083363b3607379ee
ms.sourcegitcommit: 8e91ff47ef70e80a41137f80aa1093e711d27bf7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "91957822"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="9fdea-104">Unreal での QR コード</span><span class="sxs-lookup"><span data-stu-id="9fdea-104">QR codes in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="9fdea-105">概要</span><span class="sxs-lookup"><span data-stu-id="9fdea-105">Overview</span></span>

<span data-ttu-id="9fdea-106">HoloLens 2 では、Web カメラを使用してワールド空間の QR コードを表示できます。これにより、各コードの実際の位置の座標系を使用して、QR コードをホログラムとしてレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="9fdea-106">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms using a coordinate system at each code's real-world position.</span></span>  <span data-ttu-id="9fdea-107">HoloLens 2 は、単一の QR コードに加えて、複数のデバイスの同じ場所にホログラムをレンダリングして、エクスペリエンスを共有することもできます。</span><span class="sxs-lookup"><span data-stu-id="9fdea-107">In addition to single QR codes, HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="9fdea-108">アプリケーションに QR コードを追加するためのベスト プラクティスに従っていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9fdea-108">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="9fdea-109">サイレント ゾーン</span><span class="sxs-lookup"><span data-stu-id="9fdea-109">Quiet zones</span></span>
- <span data-ttu-id="9fdea-110">照明と背景</span><span class="sxs-lookup"><span data-stu-id="9fdea-110">Lighting and backdrop</span></span>
- <span data-ttu-id="9fdea-111">サイズ、距離、および角度の位置</span><span class="sxs-lookup"><span data-stu-id="9fdea-111">Size, distance, and angular position</span></span>

<span data-ttu-id="9fdea-112">QR コードがアプリに配置されている場合、[環境への配慮](../../environment-considerations-for-hololens.md)に特に注意してください。</span><span class="sxs-lookup"><span data-stu-id="9fdea-112">Pay special attention to the [environment considerations](../../environment-considerations-for-hololens.md) when QR codes are being placed in your app.</span></span> <span data-ttu-id="9fdea-113">これらの各トピックの詳細と、必要な NuGet パッケージをダウンロードする方法の手順については、メインの [QR コードの追跡](../platform-capabilities-and-apis/qr-code-tracking.md)ドキュメントをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9fdea-113">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

## <a name="enabling-qr-detection"></a><span data-ttu-id="9fdea-114">QR 検出の有効化</span><span class="sxs-lookup"><span data-stu-id="9fdea-114">Enabling QR detection</span></span>
<span data-ttu-id="9fdea-115">HoloLens 2 で QR コードを表示するには Web カメラを使用する必要があるため、プロジェクトの設定で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fdea-115">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="9fdea-116">**[編集] > [プロジェクトの設定]** を開いて、 **[プラットフォーム]** セクションまでスクロールし、 **[HoloLens]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9fdea-116">Open **Edit > Project Settings**, scroll to the **Platforms** section and click **HoloLens**.</span></span>
    + <span data-ttu-id="9fdea-117">**[機能]** セクションを展開し、 **[Web カメラ]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="9fdea-117">Expand the **Capabilities** section and check **Webcam**.</span></span>  

<span data-ttu-id="9fdea-118">[ARSessionConfig アセットを追加する](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)ことによって、QR コードの追跡をオプトインする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="9fdea-118">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

<span data-ttu-id="9fdea-119">使用する前に、`UHoloLensARFunctionLibrary::StartCameraCapture()` を呼び出して、追跡を手動で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fdea-119">Right before the usage, you should manually enable the tracking by calling `UHoloLensARFunctionLibrary::StartCameraCapture()`.</span></span> <span data-ttu-id="9fdea-120">QR コードの追跡を終了したら、デバイス リソースを保存するために、`UHoloLensARFunctionLibrary::StopCameraCapture()` で追跡を無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fdea-120">After ending the QR code tracking, you should disable it by `UHoloLensARFunctionLibrary::StopCameraCapture()` to save the device resources.</span></span>

## <a name="setting-up-a-tracked-image"></a><span data-ttu-id="9fdea-121">追跡対象のイメージの設定</span><span class="sxs-lookup"><span data-stu-id="9fdea-121">Setting up a tracked image</span></span>

<span data-ttu-id="9fdea-122">QR コードは、追跡対象のイメージとして、Unreal の AR で追跡されたジオメトリ システムによって表示されます。</span><span class="sxs-lookup"><span data-stu-id="9fdea-122">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="9fdea-123">これを利用するには、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="9fdea-123">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="9fdea-124">ブループリントを作成し、**ARTrackableNotify** コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="9fdea-124">Create a Blueprint and add an **ARTrackableNotify** component.</span></span>

![QR の AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="9fdea-126">**ARTrackableNotify** を選択し、 **[詳細]** パネルの **[イベント]** セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="9fdea-126">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel.</span></span>

![QR のイベント](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="9fdea-128">**[On Add Tracked Geometry]** の横にある **+** をクリックして、ノードをイベント グラフに追加します。</span><span class="sxs-lookup"><span data-stu-id="9fdea-128">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="9fdea-129">イベントの完全な一覧については、[UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) コンポーネント API を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9fdea-129">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![[On Add Tracked Geometry] にノードを追加する](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a><span data-ttu-id="9fdea-131">追跡対象のイメージの使用</span><span class="sxs-lookup"><span data-stu-id="9fdea-131">Using a tracked image</span></span>
<span data-ttu-id="9fdea-132">次の画像のイベント グラフは、QR コードの中心にポイントをレンダリングし、そのデータを出力するために使用される **OnUpdateTrackedImage** イベントを示しています。</span><span class="sxs-lookup"><span data-stu-id="9fdea-132">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

![QR のレンダリングの例](images/unreal-qr-render.PNG)

<span data-ttu-id="9fdea-134">流れについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9fdea-134">Here's what's going on:</span></span>
1. <span data-ttu-id="9fdea-135">最初に、追跡したイメージが **ARTrackedQRCode** にキャストされ、現在の更新されたイメージが QR コードであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9fdea-135">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="9fdea-136">エンコードされたデータは **QRCode** 変数から取得されます。</span><span class="sxs-lookup"><span data-stu-id="9fdea-136">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="9fdea-137">**GetLocalToWorldTransform** の位置と **GetEstimateSize** のディメンションから QR コードの左上を取得できます。</span><span class="sxs-lookup"><span data-stu-id="9fdea-137">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="9fdea-138">また、コードで [QR コードの座標系を取得する](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)こともできます。</span><span class="sxs-lookup"><span data-stu-id="9fdea-138">You can also [get the coordinate system for a QR code](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="9fdea-139">一意の ID の検索</span><span class="sxs-lookup"><span data-stu-id="9fdea-139">Finding the unique ID</span></span>
<span data-ttu-id="9fdea-140">すべての QR コードには、一意の GUID ID があります。これは、次の方法で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="9fdea-140">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="9fdea-141">**As ARTracked QRCode** ピンをドラッグ アンド ドロップして、**Get Unique ID** を検索します。</span><span class="sxs-lookup"><span data-stu-id="9fdea-141">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![QR の GUID](images/unreal-qr-guid.PNG)

<span data-ttu-id="9fdea-143">QR コードを使用してバックグラウンドで多くの処理が行われているため、これで終わりというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="9fdea-143">There's a lot going on behind the scenes with QR codes, so this isn't the end of the road.</span></span> <span data-ttu-id="9fdea-144">内部的な処理の詳細については、次のリンクを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9fdea-144">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="9fdea-145">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="9fdea-145">Next Development Checkpoint</span></span>

<span data-ttu-id="9fdea-146">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は Mixed Reality プラットフォームの機能と API を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="9fdea-146">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="9fdea-147">ここから、次のトピックに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="9fdea-147">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9fdea-148">WinRT</span><span class="sxs-lookup"><span data-stu-id="9fdea-148">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="9fdea-149">または、デバイスまたはエミュレーターへのアプリの配置操作に直接移動します。</span><span class="sxs-lookup"><span data-stu-id="9fdea-149">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9fdea-150">デバイスへの配置</span><span class="sxs-lookup"><span data-stu-id="9fdea-150">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="9fdea-151">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#3-platform-capabilities-and-apis)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="9fdea-151">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="9fdea-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="9fdea-152">See also</span></span>
* [<span data-ttu-id="9fdea-153">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="9fdea-153">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="9fdea-154">ホログラム</span><span class="sxs-lookup"><span data-stu-id="9fdea-154">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="9fdea-155">座標系</span><span class="sxs-lookup"><span data-stu-id="9fdea-155">Coordinate systems</span></span>](../../design/coordinate-systems.md)
