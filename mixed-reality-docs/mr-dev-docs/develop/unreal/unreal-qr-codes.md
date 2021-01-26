---
title: Unreal での QR コード
description: Unreal Mixed Reality アプリケーションで QR コードを設定、使用、追跡する方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, QR コード, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: d9f23bacf31b310da6d49e74de2153b50e642c7d
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582666"
---
# <a name="qr-codes-in-unreal"></a><span data-ttu-id="d4a85-104">Unreal での QR コード</span><span class="sxs-lookup"><span data-stu-id="d4a85-104">QR codes in Unreal</span></span>

<span data-ttu-id="d4a85-105">HoloLens 2 を使用すると、Web カメラを使用してワールド空間の QR コードを表示できます。それらは、各コードの実際の位置にホログラムとしてレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="d4a85-105">The HoloLens 2 can see QR codes in world space using the webcam, which renders them as holograms at each code's real-world position.</span></span> <span data-ttu-id="d4a85-106">HoloLens 2 の場合、複数のデバイスの同じ場所にホログラムをレンダリングして、共有エクスペリエンスを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="d4a85-106">HoloLens 2 can also render holograms in the same location on multiple devices to create a shared experience.</span></span> <span data-ttu-id="d4a85-107">アプリケーションに QR コードを追加するためのベスト プラクティスに従っていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d4a85-107">Make sure you're following the best practices for adding QR codes to your applications:</span></span>

- <span data-ttu-id="d4a85-108">サイレント ゾーン</span><span class="sxs-lookup"><span data-stu-id="d4a85-108">Quiet zones</span></span>
- <span data-ttu-id="d4a85-109">照明と背景</span><span class="sxs-lookup"><span data-stu-id="d4a85-109">Lighting and backdrop</span></span>
- <span data-ttu-id="d4a85-110">サイズ、距離、および角度の位置</span><span class="sxs-lookup"><span data-stu-id="d4a85-110">Size, distance, and angular position</span></span>

<span data-ttu-id="d4a85-111">QR コードがアプリに配置されている場合、[環境への配慮](/hololens/hololens-environment-considerations)に特に注意してください。</span><span class="sxs-lookup"><span data-stu-id="d4a85-111">Pay special attention to the [environment considerations](/hololens/hololens-environment-considerations) when QR codes are being placed in your app.</span></span> <span data-ttu-id="d4a85-112">これらの各トピックの詳細と、必要な NuGet パッケージをダウンロードする方法の手順については、メインの [QR コードの追跡](../platform-capabilities-and-apis/qr-code-tracking.md)ドキュメントをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d4a85-112">You can find more information on each of these topics and instructions on how to download the required NuGet package in the main [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) document.</span></span>

> [!CAUTION]
> <span data-ttu-id="d4a85-113">QR コードは、HoloLens で何も設定せずに追跡できる唯一の画像の種類です。Unreal の **UARTrackedImage** モジュールは、HoloLens ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d4a85-113">QR codes are the only type of images that can be tracked by HoloLens out of the box - Unreal's **UARTrackedImage** module isn't supported on HoloLens.</span></span> <span data-ttu-id="d4a85-114">カスタム画像を追跡する必要がある場合は、デバイスの [Web カメラ](unreal-hololens-camera.md)にアクセスし、サードパーティ製の画像認識ライブラリを使用して画像を処理することができます。</span><span class="sxs-lookup"><span data-stu-id="d4a85-114">If you need to track custom images, you can access the device's [webcam](unreal-hololens-camera.md) and process images using a third party image recognition library.</span></span> 

## <a name="enabling-qr-detection"></a><span data-ttu-id="d4a85-115">QR 検出の有効化</span><span class="sxs-lookup"><span data-stu-id="d4a85-115">Enabling QR detection</span></span>

<span data-ttu-id="d4a85-116">HoloLens 2 で QR コードを表示するには Web カメラを使用する必要があるため、プロジェクトの設定で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4a85-116">Since the HoloLens 2 needs to use the webcam to see QR codes, you'll need to enable it in the project settings:</span></span>
- <span data-ttu-id="d4a85-117">**[Edit]\(編集\) > [Project Settings]\(プロジェクトの設定\)** を開き、 **[Platforms]\(プラットフォーム\)** セクションまでスクロールして、 **[HoloLens]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="d4a85-117">Open **Edit > Project Settings**, scroll to the **Platforms** section, and select **HoloLens**.</span></span>
    + <span data-ttu-id="d4a85-118">**[機能]** セクションを展開し、 **[Web カメラ]** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="d4a85-118">Expand the **Capabilities** section and check **Webcam**.</span></span>  
- <span data-ttu-id="d4a85-119">[ARSessionConfig アセットを追加する](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)ことによって、QR コードの追跡をオプトインする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="d4a85-119">You'll also need to opt into QR code tracking by [adding an ARSessionConfig asset](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a><span data-ttu-id="d4a85-120">追跡対象の QR コードの設定</span><span class="sxs-lookup"><span data-stu-id="d4a85-120">Setting up a tracked QR code</span></span>

<span data-ttu-id="d4a85-121">QR コードは、追跡対象のイメージとして、Unreal の AR で追跡されたジオメトリ システムによって表示されます。</span><span class="sxs-lookup"><span data-stu-id="d4a85-121">QR codes are surfaced through Unreal’s AR tracked geometry system as a tracked image.</span></span> <span data-ttu-id="d4a85-122">これを利用するには、次の操作を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4a85-122">To get this working, you'll need to:</span></span>
1. <span data-ttu-id="d4a85-123">アクター ブループリントを作成し、**ARTrackableNotify** コンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="d4a85-123">Create an Actor Blueprint and add an **ARTrackableNotify** component:</span></span>

![QR の AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. <span data-ttu-id="d4a85-125">**ARTrackableNotify** を選択し、 **[詳細]** パネルの **[イベント]** セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="d4a85-125">Select **ARTrackableNotify** and expand the **Events** section in the **Details** panel:</span></span>

![QR のイベント](images/unreal-spatialmapping-events.PNG)

3. <span data-ttu-id="d4a85-127">**[On Add Tracked Geometry]** の横にある **+** をクリックして、ノードをイベント グラフに追加します。</span><span class="sxs-lookup"><span data-stu-id="d4a85-127">Click **+** next to **On Add Tracked Geometry** to add the node to the Event Graph.</span></span>
    - <span data-ttu-id="d4a85-128">イベントの完全な一覧については、[UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) コンポーネント API を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d4a85-128">You can find the full list of events in the [UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) component API.</span></span>

![[On Add Tracked Geometry] にノードを追加する](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a><span data-ttu-id="d4a85-130">追跡対象の QR コードの使用</span><span class="sxs-lookup"><span data-stu-id="d4a85-130">Using a tracked QR code</span></span>

<span data-ttu-id="d4a85-131">次の画像のイベント グラフは、QR コードの中心にポイントをレンダリングし、そのデータを出力するために使用される **OnUpdateTrackedImage** イベントを示しています。</span><span class="sxs-lookup"><span data-stu-id="d4a85-131">The Event Graph in the following image shows the **OnUpdateTrackedImage** event being used to render a point in the center of a QR code and print out its data.</span></span>

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

<span data-ttu-id="d4a85-132">流れについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d4a85-132">Here's what's going on:</span></span>
1. <span data-ttu-id="d4a85-133">最初に、追跡したイメージが **ARTrackedQRCode** にキャストされ、現在の更新されたイメージが QR コードであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d4a85-133">First, the tracked image is cast to an **ARTrackedQRCode** to check that the current updated image is a QR code.</span></span>  
2. <span data-ttu-id="d4a85-134">エンコードされたデータは **QRCode** 変数から取得されます。</span><span class="sxs-lookup"><span data-stu-id="d4a85-134">The encoded data is retrieved from the **QRCode** variable.</span></span> <span data-ttu-id="d4a85-135">**GetLocalToWorldTransform** の位置と **GetEstimateSize** のディメンションから QR コードの左上を取得できます。</span><span class="sxs-lookup"><span data-stu-id="d4a85-135">You can get the top-left of the QR code from the location of **GetLocalToWorldTransform** and the dimensions with **GetEstimateSize**.</span></span>

<span data-ttu-id="d4a85-136">また、コードで [QR コードの座標系を取得する](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)こともできます。</span><span class="sxs-lookup"><span data-stu-id="d4a85-136">You can also [get the coordinate system for a QR code](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code) in code.</span></span>

## <a name="finding-the-unique-id"></a><span data-ttu-id="d4a85-137">一意の ID の検索</span><span class="sxs-lookup"><span data-stu-id="d4a85-137">Finding the unique ID</span></span>

<span data-ttu-id="d4a85-138">すべての QR コードには、一意の GUID ID があります。これは、次の方法で見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="d4a85-138">Every QR code has a unique guid ID, which you can find by:</span></span>
- <span data-ttu-id="d4a85-139">**As ARTracked QRCode** ピンをドラッグ アンド ドロップして、**Get Unique ID** を検索します。</span><span class="sxs-lookup"><span data-stu-id="d4a85-139">Dragging and dropping the **As ARTracked QRCode**  pin and searching for **Get Unique ID**.</span></span>

![QR の GUID](images/unreal-qr-guid.PNG)

<span data-ttu-id="d4a85-141">QR コードを使用してバックグラウンドで多くの処理が行われているため、これで終わりというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="d4a85-141">There's a lot going on behind the scenes with QR codes, so you're not at the end of the road.</span></span> <span data-ttu-id="d4a85-142">内部的な処理の詳細については、次のリンクを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d4a85-142">Be sure to check out the following links for more details on what's under the hood.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="d4a85-143">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="d4a85-143">Next Development Checkpoint</span></span>

<span data-ttu-id="d4a85-144">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は Mixed Reality プラットフォームの機能と API を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="d4a85-144">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="d4a85-145">ここから、次のトピックに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="d4a85-145">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d4a85-146">WinRT</span><span class="sxs-lookup"><span data-stu-id="d4a85-146">WinRT</span></span>](unreal-winRT.md)

<span data-ttu-id="d4a85-147">または、デバイスまたはエミュレーターへのアプリの配置操作に直接移動します。</span><span class="sxs-lookup"><span data-stu-id="d4a85-147">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d4a85-148">デバイスへの配置</span><span class="sxs-lookup"><span data-stu-id="d4a85-148">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="d4a85-149">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#3-advanced-features)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="d4a85-149">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4a85-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4a85-150">See also</span></span>
* [<span data-ttu-id="d4a85-151">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="d4a85-151">Spatial mapping</span></span>](../../design/spatial-mapping.md)
* [<span data-ttu-id="d4a85-152">ホログラム</span><span class="sxs-lookup"><span data-stu-id="d4a85-152">Holograms</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="d4a85-153">座標系</span><span class="sxs-lookup"><span data-stu-id="d4a85-153">Coordinate systems</span></span>](../../design/coordinate-systems.md)