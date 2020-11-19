---
title: Unreal での HoloLens 写真/ビデオ カメラ
description: HoloLens 写真/ビデオを Unreal で使用するためのガイド
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, カメラ, PV カメラ, MRC
ms.openlocfilehash: 6302a64fcde2a16b6ae1cb570215629a3e6ea9e5
ms.sourcegitcommit: 8a80613f025b05a83393845d4af4da26a7d3ea9c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2020
ms.locfileid: "94573236"
---
# <a name="hololens-photovideo-camera-in-unreal"></a><span data-ttu-id="04eab-104">Unreal での HoloLens 写真/ビデオ カメラ</span><span class="sxs-lookup"><span data-stu-id="04eab-104">HoloLens Photo/Video Camera in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="04eab-105">概要</span><span class="sxs-lookup"><span data-stu-id="04eab-105">Overview</span></span>

<span data-ttu-id="04eab-106">HoloLens には、Mixed Reality Capture (MRC) に使用される写真/ビデオ (PV) カメラがあり、アプリで実際のビジュアルにアクセスするために使用できます。</span><span class="sxs-lookup"><span data-stu-id="04eab-106">The HoloLens has a Photo/Video (PV) Camera that is used for both Mixed Reality Capture (MRC) and can be used by an app to access real-world visuals.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="04eab-107">Holographic Remoting では PV カメラはサポートされていませんが、お使いの PC に搭載のウェブ カメラを使用して、HoloLens PV カメラの機能をシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="04eab-107">The PV Camera isn't supported with Holographic Remoting, but it's possible to use a webcam attached to your PC to simulate the HoloLens PV Camera functionality.</span></span>

## <a name="render-from-the-pv-camera-for-mrc"></a><span data-ttu-id="04eab-108">MRC 用の PV カメラからのレンダリング</span><span class="sxs-lookup"><span data-stu-id="04eab-108">Render from the PV Camera for MRC</span></span>

> [!NOTE]
> <span data-ttu-id="04eab-109">これには **Unreal Engine 4.25** 以降のバージョンが必要です。</span><span class="sxs-lookup"><span data-stu-id="04eab-109">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="04eab-110">システムとカスタム MRC レコーダーは、PV カメラとイマーシブ アプリによってレンダリングされたホログラムを組み合わせることにより、Mixed Reality キャプチャを作成します。</span><span class="sxs-lookup"><span data-stu-id="04eab-110">The system, and custom MRC recorders, create mixed reality captures by combining the PV Camera with holograms rendered by the immersive app.</span></span>

<span data-ttu-id="04eab-111">既定では、Mixed Reality キャプチャでは、右目のホログラフィック出力が使用されます。</span><span class="sxs-lookup"><span data-stu-id="04eab-111">By default, mixed reality capture uses the right eye's holographic output.</span></span> <span data-ttu-id="04eab-112">イマーシブ アプリが [PV カメラ](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in)からのレンダリングを選択した場合は、それが代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="04eab-112">If an immersive app chooses to [render from the PV Camera](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md#render-from-the-pv-camera-opt-in) then that will be used instead.</span></span> <span data-ttu-id="04eab-113">これにより、現実世界と MRC ビデオのホログラムとの間のマッピングが向上します。</span><span class="sxs-lookup"><span data-stu-id="04eab-113">This improves the mapping between the real world and the holograms in the MRC video.</span></span>

<span data-ttu-id="04eab-114">PV カメラからの表示をオプトインするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="04eab-114">To opt-in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="04eab-115">**SetEnabledMixedRealityCamera** および **ResizeMixedRealityCamera** の呼び出し</span><span class="sxs-lookup"><span data-stu-id="04eab-115">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="04eab-116">**サイズ X** および **サイズ Y** の値を使用して、ビデオのディメンションを設定します。</span><span class="sxs-lookup"><span data-stu-id="04eab-116">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![第 3 のカメラ](../platform-capabilities-and-apis/images/unreal-camera-3rd.PNG)

<span data-ttu-id="04eab-118">その後、Unreal は MRC からのリクエストを処理して、PV カメラの視点からレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="04eab-118">Unreal will then handle requests from MRC to render from the PV Camera's perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="04eab-119">[Mixed Reality キャプチャ](../../mixed-reality-capture.md)がトリガーされた場合にのみ、アプリは写真/ビデオ カメラの視点からレンダリングするよう求められます。</span><span class="sxs-lookup"><span data-stu-id="04eab-119">Only when [Mixed Reality Capture](../../mixed-reality-capture.md) is triggered will the app be asked to render from the photo/video camera's perspective.</span></span>

## <a name="using-the-pv-camera"></a><span data-ttu-id="04eab-120">PV カメラの使用</span><span class="sxs-lookup"><span data-stu-id="04eab-120">Using the PV Camera</span></span>

<span data-ttu-id="04eab-121">Web カメラ テクスチャは実行時にゲームで入手できますが、エディターの **[編集] > [プロジェクトの設定]** で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="04eab-121">The webcam texture can be retrieved in the game at runtime, but it needs to be enabled in the editor's **Edit > Project Settings**:</span></span>
1. <span data-ttu-id="04eab-122">**[プラットフォーム] > [HoloLens] > [機能]** に移動し、**Web カメラ** を確認します。</span><span class="sxs-lookup"><span data-stu-id="04eab-122">Go to **Platforms > HoloLens > Capabilities** and check **Webcam**.</span></span>
    * <span data-ttu-id="04eab-123">実行時に Web カメラを使用するには、**StartCameraCapture** 関数を使用し、記録を停止するには、**StopCameraCapture** 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="04eab-123">Use the **StartCameraCapture** function to use the webcam at runtime and the **StopCameraCapture** function to stop recording.</span></span>

![カメラの開始と停止](images/unreal-camera-startstop.PNG)

## <a name="rendering-an-image"></a><span data-ttu-id="04eab-125">イメージのレンダリング</span><span class="sxs-lookup"><span data-stu-id="04eab-125">Rendering an image</span></span>
<span data-ttu-id="04eab-126">カメラ イメージをレンダリングするには次のようにします。</span><span class="sxs-lookup"><span data-stu-id="04eab-126">To render the camera image:</span></span>
1. <span data-ttu-id="04eab-127">以下のスクリーンショットでは **PVCamMat** という名前のプロジェクトのマテリアルに基づいて、ダイナミック マテリアル インスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="04eab-127">Create a dynamic material instance based on a material in the project, which is named **PVCamMat** in the screenshot below.</span></span>  
2. <span data-ttu-id="04eab-128">ダイナミック マテリアル インスタンスを **Material Instance Dynamic Object Reference** 変数に設定します。</span><span class="sxs-lookup"><span data-stu-id="04eab-128">Set the dynamic material instance to a **Material Instance Dynamic Object Reference** variable.</span></span>  
3. <span data-ttu-id="04eab-129">カメラ フィードをレンダリングするシーン内のオブジェクトのマテリアルを、この新しいダイナミック マテリアル インスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="04eab-129">Set the material of the object in the scene that will render the camera feed to this new dynamic material instance.</span></span>
    * <span data-ttu-id="04eab-130">カメラ イメージをマテリアルにバインドするために使用されるタイマーを開始します。</span><span class="sxs-lookup"><span data-stu-id="04eab-130">Start a timer that will be used to bind the camera image to the material.</span></span>

![カメラのレンダリング](images/unreal-camera-render.PNG)

4. <span data-ttu-id="04eab-132">このタイマーに新しい関数 (この場合は **MaterialTimer**) を作成し、**GetARCameraImage** を呼び出して、Web カメラからテクスチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="04eab-132">Create a new function for this timer, in this case **MaterialTimer**, and call **GetARCameraImage** to get the texture from the webcam.</span></span>  
5. <span data-ttu-id="04eab-133">このテクスチャが有効な場合は、シェーダーのテクスチャ パラメーターをこのイメージに設定します。</span><span class="sxs-lookup"><span data-stu-id="04eab-133">If the texture is valid, set a texture parameter in the shader to the image.</span></span>  <span data-ttu-id="04eab-134">そうでない場合は、もう一度素材のタイマーを開始します。</span><span class="sxs-lookup"><span data-stu-id="04eab-134">Otherwise, start the material timer again.</span></span>

![Web カメラからのカメラ テクスチャ](images/unreal-camera-texture.PNG)

5. <span data-ttu-id="04eab-136">マテリアルに、カラー エントリにバインドされている **SetTextureParameterValue** の名前と一致するパラメータがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="04eab-136">Make sure the material has a parameter matching the name in **SetTextureParameterValue** that's bound to a color entry.</span></span> <span data-ttu-id="04eab-137">これを行わないと、カメラ イメージを正しく表示できません。</span><span class="sxs-lookup"><span data-stu-id="04eab-137">Without this, the camera image can't be properly displayed.</span></span>

![カメラのテクスチャ](images/unreal-camera-material.PNG)

## <a name="next-development-checkpoint"></a><span data-ttu-id="04eab-139">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="04eab-139">Next Development Checkpoint</span></span>

<span data-ttu-id="04eab-140">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は Mixed Reality プラットフォームの機能と API を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="04eab-140">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="04eab-141">ここから、次のトピックに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="04eab-141">From here, you can proceed to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="04eab-142">QR コード</span><span class="sxs-lookup"><span data-stu-id="04eab-142">QR codes</span></span>](unreal-qr-codes.md)

<span data-ttu-id="04eab-143">または、デバイスまたはエミュレーターへのアプリの配置操作に直接移動します。</span><span class="sxs-lookup"><span data-stu-id="04eab-143">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="04eab-144">デバイスへの配置</span><span class="sxs-lookup"><span data-stu-id="04eab-144">Deploying to device</span></span>](unreal-deploying.md)

<span data-ttu-id="04eab-145">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#3-platform-capabilities-and-apis)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="04eab-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#3-platform-capabilities-and-apis) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="04eab-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="04eab-146">See also</span></span>
* [<span data-ttu-id="04eab-147">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="04eab-147">Locatable camera</span></span>](../platform-capabilities-and-apis/locatable-camera.md)
* [<span data-ttu-id="04eab-148">開発者向け複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="04eab-148">Mixed reality capture for developers</span></span>](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)
