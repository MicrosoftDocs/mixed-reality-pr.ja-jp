---
title: 開発者向けの Mixed reality キャプチャ
description: 開発者向けの mixed reality キャプチャを有効化、使用、および表示するためのベストプラクティスについて説明します。
author: mattzmsft
ms.author: mazeller
ms.date: 02/24/2019
ms.topic: article
keywords: mrc、写真、ビデオ、キャプチャ、カメラ
ms.openlocfilehash: 2539c8e2a6f26ba1f36cd28502bf8d0f50803657
ms.sourcegitcommit: bd9b2734903652b106db86686428c03acf104707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2021
ms.locfileid: "98763721"
---
# <a name="mixed-reality-capture-for-developers"></a><span data-ttu-id="a0fec-104">開発者向けの Mixed reality キャプチャ</span><span class="sxs-lookup"><span data-stu-id="a0fec-104">Mixed reality capture for developers</span></span>

> [!NOTE]
> <span data-ttu-id="a0fec-105">HoloLens 2 の新しい MRC 機能に関するガイダンスについては、以下の [PV カメラのレンダー](#render-from-the-pv-camera-opt-in) に関する説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0fec-105">See [Render from the PV camera](#render-from-the-pv-camera-opt-in) below for guidance on a new MRC capability for HoloLens 2.</span></span>

<span data-ttu-id="a0fec-106">[Mixed reality キャプチャ](/hololens/holographic-photos-and-videos)(MRC) の写真またはビデオをいつでも実行できますが、アプリケーションの開発時に注意すべき点はほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="a0fec-106">You can take a [mixed reality capture](/hololens/holographic-photos-and-videos) (MRC) photo or video at any time, but there are few things to keep in mind when developing your application.</span></span> <span data-ttu-id="a0fec-107">これには、MRC ビジュアル品質のベストプラクティスと、MRCs のキャプチャ中にシステムの変更に応答するためのベストプラクティスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0fec-107">This includes best practices for MRC visual quality and being responsive to system changes while MRCs are being captured.</span></span>

<span data-ttu-id="a0fec-108">開発者は、混合現実のキャプチャと挿入をシームレスにアプリに統合することもできます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-108">Developers can also seamlessly integrate mixed reality capture and insertion into their apps.</span></span>

<span data-ttu-id="a0fec-109">HoloLens の MRC (最初世代) では、720p までのビデオと写真がサポートされています。 HoloLens 2 の MRC では、最大1080p および最大4K 解像度までのビデオがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a0fec-109">MRC on HoloLens (first-generation) supports videos and photos up to 720p, while MRC on HoloLens 2 supports videos up to 1080p and photos up to 4K resolution.</span></span>

## <a name="the-importance-of-quality-mrc"></a><span data-ttu-id="a0fec-110">品質の MRC の重要性</span><span class="sxs-lookup"><span data-stu-id="a0fec-110">The importance of quality MRC</span></span>

<span data-ttu-id="a0fec-111">Microsoft Store のページ上に mixed reality スクリーンショットがあるか、またはソーシャルネットワークでキャプチャコンテンツを共有する他のユーザーであるかにかかわらず、Mixed Reality キャプチャメディアは多くの場合、ユーザーがアプリに最初にさらされます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-111">Whether it's mixed reality screenshots on your Microsoft Store page or other users sharing capture content on social networks, Mixed Reality Capture media is often a users first exposure to your app.</span></span> <span data-ttu-id="a0fec-112">MRC を使用して、アプリをデモし、ユーザーを教育し、世界中の対話を共有するようユーザーに促すことができます。また、ユーザーの調査や問題の解決にも対応できます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-112">You can use MRC to demo your app, educate users, encourage users to share their mixed world interactions, and for user research and problem solving.</span></span>

## <a name="how-mrc-impacts-your-app"></a><span data-ttu-id="a0fec-113">MRC がアプリに与える影響</span><span class="sxs-lookup"><span data-stu-id="a0fec-113">How MRC impacts your app</span></span>

### <a name="enabling-mrc-in-your-app"></a><span data-ttu-id="a0fec-114">アプリでの MRC の有効化</span><span class="sxs-lookup"><span data-stu-id="a0fec-114">Enabling MRC in your app</span></span>

<span data-ttu-id="a0fec-115">既定では、アプリは、ユーザーが混合現実のキャプチャを実行できるようにするために何も行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="a0fec-115">By default, an app doesn't have to do anything to enable users to take mixed reality captures.</span></span>

### <a name="enabling-improved-alignment-for-mrc-in-your-app"></a><span data-ttu-id="a0fec-116">アプリでの MRC のアラインメントの向上を可能にする</span><span class="sxs-lookup"><span data-stu-id="a0fec-116">Enabling improved alignment for MRC in your app</span></span>

<span data-ttu-id="a0fec-117">既定では、mixed reality キャプチャは、右目の holographic 出力と写真/ビデオ (PV) カメラを結合します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-117">By default, mixed reality capture combines the right eye's holographic output with the photo/video (PV) camera.</span></span> <span data-ttu-id="a0fec-118">この2つのソースは、現在実行中のイマーシブアプリによって設定されたフォーカスポイントを使用して結合されます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-118">These two sources are combined using the focus point set by the currently running immersive app.</span></span>

<span data-ttu-id="a0fec-119">これは、PV カメラと右ディスプレイの間に物理的な距離があるため、フォーカス平面外のホログラムが配置されないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-119">This means that holograms outside the focus plane won't align because of the physical distance between the PV camera and the right display.</span></span>

#### <a name="set-the-focus-point"></a><span data-ttu-id="a0fec-120">フォーカスポイントを設定する</span><span class="sxs-lookup"><span data-stu-id="a0fec-120">Set the focus point</span></span>

<span data-ttu-id="a0fec-121">イマーシブアプリ (HoloLens) では、安定化平面を使用する場所の [フォーカスポイント](../unity/focus-point-in-unity.md) を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-121">Immersive apps (on HoloLens) should set the [focus point](../unity/focus-point-in-unity.md) of where they want their stabilization plane to be.</span></span> <span data-ttu-id="a0fec-122">これにより、ヘッドセットと mixed reality キャプチャの両方で最適なアラインメントが実現されます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-122">This ensures the best alignment in both the headset and in mixed reality capture.</span></span>

<span data-ttu-id="a0fec-123">フォーカスポイントが設定されていない場合、安定化平面の既定値は2メートルになります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-123">If a focus point isn't set, the stabilization plane will default to 2 meters.</span></span>

#### <a name="render-from-the-pv-camera-opt-in"></a><span data-ttu-id="a0fec-124">PV カメラからのレンダリング (オプトイン)</span><span class="sxs-lookup"><span data-stu-id="a0fec-124">Render from the PV camera (opt-in)</span></span>

<span data-ttu-id="a0fec-125">HoloLens 2 では、mixed reality キャプチャが実行されている間に、アプリが **PV カメラからレンダリング** する機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-125">HoloLens 2 adds the ability for an immersive app to **render from the PV camera** while mixed reality capture is running.</span></span> <span data-ttu-id="a0fec-126">アプリで追加のレンダリングが正しくサポートされるようにするには、アプリでこの機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-126">To ensure the app supports the additional render correctly, the app has to opt in to this functionality.</span></span>

<span data-ttu-id="a0fec-127">PV カメラからのレンダリングでは、既定の MRC エクスペリエンスに対して次の点が改善されています。</span><span class="sxs-lookup"><span data-stu-id="a0fec-127">Render from the PV camera offers the following improvements over the default MRC experience:</span></span>
* <span data-ttu-id="a0fec-128">物理的な環境に対するホログラムのアラインメントとほぼ相互作用のための手は、すべての距離で正確である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-128">Hologram alignment to your physical environment and hands for near interactions should be accurate at all distances.</span></span> <span data-ttu-id="a0fec-129">既定の MRC で見られるように、フォーカスポイント以外の距離にオフセットを設定しないようにします。</span><span class="sxs-lookup"><span data-stu-id="a0fec-129">Avoid having an offset at distances other than the focus point as you might see in the default MRC.</span></span>
* <span data-ttu-id="a0fec-130">ヘッドセットの右目は、MRC 出力のホログラムをレンダリングするために使用されないため、侵害されることはありません。</span><span class="sxs-lookup"><span data-stu-id="a0fec-130">The right eye in the headset won't be compromised, as it won't be used to render the holograms for the MRC output.</span></span>

<span data-ttu-id="a0fec-131">PV カメラからのレンダリングを有効にするには、次の3つの手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-131">There are three steps to enable rendering from the PV camera:</span></span>
1. <span data-ttu-id="a0fec-132">PhotoVideoCamera HolographicViewConfiguration を有効にする</span><span class="sxs-lookup"><span data-stu-id="a0fec-132">Enable the PhotoVideoCamera HolographicViewConfiguration</span></span>
2. <span data-ttu-id="a0fec-133">追加の HolographicCamera render を処理する</span><span class="sxs-lookup"><span data-stu-id="a0fec-133">Handle the additional HolographicCamera render</span></span>
3. <span data-ttu-id="a0fec-134">この追加の HolographicCamera からシェーダーとコードが正しくレンダリングされることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-134">Verify your shaders and code render correctly from this additional HolographicCamera</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-directx"></a><span data-ttu-id="a0fec-135">DirectX で PhotoVideoCamera HolographicViewConfiguration を有効にする</span><span class="sxs-lookup"><span data-stu-id="a0fec-135">Enable the PhotoVideoCamera HolographicViewConfiguration in DirectX</span></span>

<span data-ttu-id="a0fec-136">PV カメラからの表示をオプトインするには、アプリで PhotoVideoCamera の [HolographicViewConfiguration](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration)を有効にするだけです。</span><span class="sxs-lookup"><span data-stu-id="a0fec-136">To opt in to rendering from the PV Camera, an app simply enables the PhotoVideoCamera's [HolographicViewConfiguration](/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration):</span></span>
```csharp
var display = Windows.Graphics.Holographic.HolographicDisplay.GetDefault();
var view = display.TryGetViewConfiguration(Windows.Graphics.Holographic.HolographicViewConfigurationKind.PhotoVideoCamera);
if (view != null)
{
    view.IsEnabled = true;
}
```

##### <a name="handle-the-additional-holographiccamera-render-in-directx"></a><span data-ttu-id="a0fec-137">DirectX で追加の HolographicCamera render を処理する</span><span class="sxs-lookup"><span data-stu-id="a0fec-137">Handle the additional HolographicCamera render in DirectX</span></span>

<span data-ttu-id="a0fec-138">アプリが PV カメラから表示するオプトインを持っていて、mixed reality キャプチャが開始される場合:</span><span class="sxs-lookup"><span data-stu-id="a0fec-138">When the app has opt-in to render from the PV camera and mixed reality capture starts:</span></span>
1. <span data-ttu-id="a0fec-139">HolographicSpace の CameraAdded イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-139">HolographicSpace's CameraAdded event will fire.</span></span> <span data-ttu-id="a0fec-140">このイベントは、アプリがこの時点でカメラを処理できない場合に遅延する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-140">This event can be deferred if the app can't handle the camera at this time.</span></span>
2. <span data-ttu-id="a0fec-141">未処理の遅延がない状態でイベントが完了すると、HolographicCamera は次の HolographicFrame の AddedCameras の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-141">Once the event has completed with no outstanding deferrals, the HolographicCamera will appear in the next HolographicFrame's AddedCameras list.</span></span>

<span data-ttu-id="a0fec-142">Mixed reality キャプチャが停止した場合 (または、mixed reality キャプチャが実行されているときにアプリがビューの構成を無効にした場合)、次の HolographicFrame の RemovedCameras の一覧に HolographicCamera が表示され、HolographicSpace の CameraRemoved イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-142">When mixed reality capture stops (or if the app disables the view configuration while mixed reality capture is running): the HolographicCamera will appear in the next HolographicFrame's RemovedCameras list and the HolographicSpace's CameraRemoved event will fire.</span></span>

<span data-ttu-id="a0fec-143">HolographicCamera に [viewconfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) プロパティが追加され、カメラが属している構成を識別できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a0fec-143">A [ViewConfiguration](/uwp/api/windows.graphics.holographic.holographiccamera.viewconfiguration) property has been added to HolographicCamera to help identify the configuration a camera belongs to.</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unity"></a><span data-ttu-id="a0fec-144">Unity で PhotoVideoCamera HolographicViewConfiguration を有効にする</span><span class="sxs-lookup"><span data-stu-id="a0fec-144">Enable the PhotoVideoCamera HolographicViewConfiguration in Unity</span></span>

> [!NOTE]
> <span data-ttu-id="a0fec-145">Unity 2018 を使用している場合は、 **unity 2018.4.13 f1** 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="a0fec-145">If you're using Unity 2018, this requires **Unity 2018.4.13f1** or newer.</span></span> <span data-ttu-id="a0fec-146">Unity 2019 を使用している場合は、 **unity 2019.4** 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="a0fec-146">If you're using Unity 2019, this requires **Unity 2019.4**, or newer.</span></span>

<span data-ttu-id="a0fec-147">[Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)を使用しているときに、pv カメラからの表示をオプトインするには、 [Windows Mixed reality カメラ設定](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/CameraSystem/WindowsMixedRealityCameraSettings.html)プロバイダーを有効にし、 **pv カメラからのレンダー** をオンにします。</span><span class="sxs-lookup"><span data-stu-id="a0fec-147">To opt in to rendering from the PV Camera when using the [Mixed Reality Toolkit](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html), enable the [Windows Mixed Reality Camera Settings](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/CameraSystem/WindowsMixedRealityCameraSettings.html) provider and check **Render from PV Camera**.</span></span>

<span data-ttu-id="a0fec-148">Mixed Reality Toolkit を使用していない場合は、コンポーネントを使用して、DirectX 用に前述したように [手動でオプトイン](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) できます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-148">If you're not using the Mixed Reality Toolkit, you can use a component to [manually opt-in](#enable-the-photovideocamera-holographicviewconfiguration-in-directx) as described above for DirectX.</span></span>

##### <a name="handle-the-additional-holographiccamera-render-in-unity"></a><span data-ttu-id="a0fec-149">Unity で追加の HolographicCamera render を処理する</span><span class="sxs-lookup"><span data-stu-id="a0fec-149">Handle the additional HolographicCamera render in Unity</span></span>

<span data-ttu-id="a0fec-150">これは Unity によって自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-150">This is done for you automatically by Unity.</span></span>

##### <a name="enable-the-photovideocamera-holographicviewconfiguration-in-unreal"></a><span data-ttu-id="a0fec-151">Unreal で PhotoVideoCamera HolographicViewConfiguration を有効にする</span><span class="sxs-lookup"><span data-stu-id="a0fec-151">Enable the PhotoVideoCamera HolographicViewConfiguration in Unreal</span></span>

> [!NOTE]
> <span data-ttu-id="a0fec-152">これには **Unreal Engine 4.25** 以降のバージョンが必要です。</span><span class="sxs-lookup"><span data-stu-id="a0fec-152">This requires **Unreal Engine 4.25** or newer.</span></span>

<span data-ttu-id="a0fec-153">PV カメラからの表示をオプトインするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="a0fec-153">To opt in to rendering from the PV Camera:</span></span>

1. <span data-ttu-id="a0fec-154">**SetEnabledMixedRealityCamera** および **ResizeMixedRealityCamera** の呼び出し</span><span class="sxs-lookup"><span data-stu-id="a0fec-154">Call **SetEnabledMixedRealityCamera** and **ResizeMixedRealityCamera**</span></span>
    * <span data-ttu-id="a0fec-155">**サイズ X** および **サイズ Y** の値を使用して、ビデオのディメンションを設定します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-155">Use the **Size X** and **Size Y** values to set the video dimensions.</span></span>

![第 3 のカメラ](images/unreal-camera-3rd.PNG)

##### <a name="handle-the-additional-holographiccamera-render-in-unreal"></a><span data-ttu-id="a0fec-157">Unreal で追加の HolographicCamera render を処理する</span><span class="sxs-lookup"><span data-stu-id="a0fec-157">Handle the additional HolographicCamera render in Unreal</span></span>

<span data-ttu-id="a0fec-158">これは、Unreal によって自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-158">This is done for you automatically by Unreal.</span></span>

##### <a name="verify-shaders-and-code-support-additional-cameras"></a><span data-ttu-id="a0fec-159">シェーダーとコードがサポートする追加のカメラを確認する</span><span class="sxs-lookup"><span data-stu-id="a0fec-159">Verify shaders and code support additional cameras</span></span>

<span data-ttu-id="a0fec-160">Mixed reality キャプチャを実行し、異常な配置、コンテンツ不足、またはパフォーマンスの問題がないか確認します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-160">Run a mixed reality capture and check for unusual alignment, missing content, or performance issues.</span></span> <span data-ttu-id="a0fec-161">必要に応じてシェーダーとコードを更新します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-161">Update shaders and code as appropriate.</span></span>

<span data-ttu-id="a0fec-162">追加のカメラへのレンダリングをサポートできない特定のシーンがある場合は、PhotoVideoCamera の HolographicViewConfiguration を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-162">If there are certain scenes that can't support rendering to an additional camera, you can disable the PhotoVideoCamera's HolographicViewConfiguration.</span></span>

### <a name="disabling-mrc-in-your-app"></a><span data-ttu-id="a0fec-163">アプリでの MRC の無効化</span><span class="sxs-lookup"><span data-stu-id="a0fec-163">Disabling MRC in your app</span></span>

#### <a name="2d-app"></a><span data-ttu-id="a0fec-164">2D アプリ</span><span class="sxs-lookup"><span data-stu-id="a0fec-164">2D app</span></span>

<span data-ttu-id="a0fec-165">次の方法で混合の現実のキャプチャを実行すると、2D アプリでビジュアルコンテンツを非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-165">2D apps can choose to have their visual content obscured when mixed reality capture is running by:</span></span>
* <span data-ttu-id="a0fec-166">[DXGI_PRESENT_RESTRICT_TO_OUTPUT](/windows/desktop/direct3ddxgi/dxgi-present)フラグと共に存在する</span><span class="sxs-lookup"><span data-stu-id="a0fec-166">Present with the [DXGI_PRESENT_RESTRICT_TO_OUTPUT](/windows/desktop/direct3ddxgi/dxgi-present) flag</span></span>
* <span data-ttu-id="a0fec-167">[DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag)フラグを使用してアプリのスワップチェーンを作成する</span><span class="sxs-lookup"><span data-stu-id="a0fec-167">Create the app's swap chain with the [DXGI_SWAP_CHAIN_FLAG_HW_PROTECTED](/windows/desktop/api/dxgi/ne-dxgi-dxgi_swap_chain_flag) flag</span></span>
* <span data-ttu-id="a0fec-168">Windows 10 5 月2019更新プログラムで、ApplicationView の[IsScreenCaptureEnabled](/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)を設定します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-168">With the Windows 10 May 2019 Update, setting ApplicationView's [IsScreenCaptureEnabled](/uwp/api/windows.ui.viewmanagement.applicationview.isscreencaptureenabled)</span></span>

#### <a name="immersive-app"></a><span data-ttu-id="a0fec-169">イマーシブアプリ</span><span class="sxs-lookup"><span data-stu-id="a0fec-169">Immersive app</span></span>

<span data-ttu-id="a0fec-170">イマーシブアプリでは、複合現実のキャプチャからビジュアルコンテンツを除外することを選択できます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-170">Immersive apps can choose to have their visual content excluded from mixed reality capture by:</span></span>
* <span data-ttu-id="a0fec-171">HolographicCameraRenderingParameter の [Iscontentprotectionenabled](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) を設定して、関連付けられているフレームに対して mixed reality キャプチャを無効にしています</span><span class="sxs-lookup"><span data-stu-id="a0fec-171">Setting HolographicCameraRenderingParameter's [IsContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.iscontentprotectionenabled) to disable mixed reality capture for its associated frame</span></span>
* <span data-ttu-id="a0fec-172">HolographicCamera の [IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) を設定して、関連付けられている holographic カメラの mixed reality キャプチャを無効にする</span><span class="sxs-lookup"><span data-stu-id="a0fec-172">Setting HolographicCamera's [IsHardwareContentProtectionEnabled](/uwp/api/windows.graphics.holographic.holographiccamera.ishardwarecontentprotectionenabled) to disable mixed reality capture for its associated holographic camera</span></span>

#### <a name="password-keyboard"></a><span data-ttu-id="a0fec-173">パスワードキーボード</span><span class="sxs-lookup"><span data-stu-id="a0fec-173">Password Keyboard</span></span>

<span data-ttu-id="a0fec-174">Windows 10 5 月2019更新プログラムでは、パスワードまたは pin キーボードが表示されたときに、ビジュアルコンテンツが mixed reality キャプチャから自動的に除外されます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-174">With the Windows 10 May 2019 Update, visual content is automatically excluded from mixed reality capture when a password or pin keyboard is visible.</span></span>

### <a name="knowing-when-mrc-is-active"></a><span data-ttu-id="a0fec-175">MRC がアクティブであることを把握しています</span><span class="sxs-lookup"><span data-stu-id="a0fec-175">Knowing when MRC is active</span></span>

<span data-ttu-id="a0fec-176">アプリで [Appcapture](/uwp/api/Windows.Media.Capture.AppCapture) クラスを使用すると、システムの混合現実のキャプチャが実行されているかどうかを知ることができます (オーディオまたはビデオのいずれか)。</span><span class="sxs-lookup"><span data-stu-id="a0fec-176">The [AppCapture](/uwp/api/Windows.Media.Capture.AppCapture) class can be used by an app to know when system mixed reality capture is running (for either audio or video).</span></span>

>[!NOTE]
><span data-ttu-id="a0fec-177">デバイスで混合 reality キャプチャを利用できない場合、AppCapture の [GetForCurrentView](/uwp/api/windows.media.capture.appcapture.getforcurrentview) API は null を返すことがあります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-177">AppCapture's [GetForCurrentView](/uwp/api/windows.media.capture.appcapture.getforcurrentview) API can return null if mixed reality capture isn't available on the device.</span></span> <span data-ttu-id="a0fec-178">アプリが中断されたときに CapturingChanged イベントの登録を解除することも重要です。それ以外の場合、MRC はブロックされた状態になります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-178">It's also important to de-register the CapturingChanged event when your app is suspended, otherwise MRC can get into a blocked state.</span></span>

### <a name="best-practices-hololens-specific"></a><span data-ttu-id="a0fec-179">ベストプラクティス (HoloLens 固有)</span><span class="sxs-lookup"><span data-stu-id="a0fec-179">Best practices (HoloLens-specific)</span></span>

<span data-ttu-id="a0fec-180">MRC は開発作業を追加せずに動作することが期待されていますが、最適な mixed reality キャプチャエクスペリエンスを提供するには、いくつかの点に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-180">MRC is expected to work without additional development effort, but there are a few things to be aware of when providing the best mixed reality capture experience.</span></span>

<span data-ttu-id="a0fec-181">**MRC は、ホログラムのアルファチャネルを使用して、 [カメラ](locatable-camera.md) の画像とブレンドします。**</span><span class="sxs-lookup"><span data-stu-id="a0fec-181">**MRC uses the hologram’s alpha channel to blend with the [camera](locatable-camera.md) imagery**</span></span>

<span data-ttu-id="a0fec-182">最も重要な手順は、アプリが不透明な黒にクリアするのではなく、透明な黒にクリアされるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="a0fec-182">The most important step is to make sure your app is clearing to transparent black instead of clearing to opaque black.</span></span> <span data-ttu-id="a0fec-183">Unity では、これは既定で MixedRealityToolkit を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-183">In Unity, this is done by default with the MixedRealityToolkit.</span></span> <span data-ttu-id="a0fec-184">Unity 以外で開発している場合は、1行の変更が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-184">If you're developing in non-Unity, you may need to make a one line change.</span></span>

<span data-ttu-id="a0fec-185">以下は、アプリが透明な黒にクリアされていない場合に、MRC に表示される可能性のあるアイテムの一部です。</span><span class="sxs-lookup"><span data-stu-id="a0fec-185">Here are some of the artifacts you might see in MRC if your app isn't clearing to transparent black:</span></span>

<span data-ttu-id="a0fec-186">**エラーの例**: コンテンツの周囲に黒い端がある (透明な黒にクリアできない)</span><span class="sxs-lookup"><span data-stu-id="a0fec-186">**Example Failures**: Black edges around the content (failing to clear to transparent black)</span></span>

<table>
<tr>
<td>
<img src="images/chessboardblackedges-300px.jpg" alt="Failure to clear to transparent black: black edge artifacts around holograms"/>
</td>
<td>
<img src="images/fieldblackedges-300px.jpg" alt="Failing to clear to transparent black: black edge artifacts around holograms"/>
</td>
</tr>
</table>

<span data-ttu-id="a0fec-187">**失敗の例**: ホログラムの背景シーン全体が黒で表示されます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-187">**Example Failures**: The entire background scene of the hologram appears black.</span></span> <span data-ttu-id="a0fec-188">背景のアルファ値を1つに設定すると、黒の背景になります</span><span class="sxs-lookup"><span data-stu-id="a0fec-188">Setting a background alpha value of one results in a black background</span></span>

![背景のアルファ値1を設定すると、背景が黒になります。](images/clearopaqueblack-300px.png)

<span data-ttu-id="a0fec-190">**期待される結果**: ホログラムが現実の世界と適切にブレンドされている (透明な黒に消去する場合は予期される結果)</span><span class="sxs-lookup"><span data-stu-id="a0fec-190">**Expected Result**: Holograms appear properly blended with the real-world (expected result if clearing to transparent black)</span></span>

![透過的な黒に消去する場合に予期される結果](images/cleartransparentblack-300px.png)

<span data-ttu-id="a0fec-192">**解決策**:</span><span class="sxs-lookup"><span data-stu-id="a0fec-192">**Solution**:</span></span>
* <span data-ttu-id="a0fec-193">アルファ値を0にするために、不透明な黒で表示されているコンテンツを変更します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-193">Change any content that is showing up as opaque black to have an alpha value of 0.</span></span>
* <span data-ttu-id="a0fec-194">アプリが透明な黒にクリアされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-194">Ensure that the app is clearing to transparent black.</span></span>
* <span data-ttu-id="a0fec-195">Unity の既定値は MixedRealityToolkit で自動的にクリアされますが、Unity 以外のアプリの場合は、ID3D11DeiceContext:: ClearRenderTargetView () で使用される色を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-195">Unity defaults to clear automatically with the MixedRealityToolkit, but if it’s a non-Unity app you should modify the color used with ID3D11DeiceContext::ClearRenderTargetView().</span></span> <span data-ttu-id="a0fec-196">不透明な黒 (0、0、0、1) ではなく、透明な黒 (0、0、0、0) であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-196">You want to ensure you clear to transparent black (0,0,0,0) instead of opaque black (0,0,0,1).</span></span>

<span data-ttu-id="a0fec-197">必要に応じてアセットのアルファ値を調整できるようになりましたが、通常は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="a0fec-197">You can now tune the alpha values of your assets if you’d like, but typically don’t need to.</span></span> <span data-ttu-id="a0fec-198">ほとんどの場合、MRCs はすぐに使えるように見えます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-198">Most of the time, MRCs will look good out of the box.</span></span> <span data-ttu-id="a0fec-199">MRC は、前乗算したアルファを前提としています。</span><span class="sxs-lookup"><span data-stu-id="a0fec-199">MRC assumes pre-multiplied alpha.</span></span> <span data-ttu-id="a0fec-200">アルファ値は、MRC キャプチャにのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-200">The alpha values will only affect the MRC capture.</span></span>

### <a name="what-to-expect-when-mrc-is-enabled-on-hololens"></a><span data-ttu-id="a0fec-201">HoloLens が HoloLens で有効になっている場合に予期されること</span><span class="sxs-lookup"><span data-stu-id="a0fec-201">What to expect when MRC is enabled on HoloLens</span></span>

<span data-ttu-id="a0fec-202">以下は、特に明記されていない限り、HoloLens (第1世代) と HoloLens 2 の両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-202">The following apply to both HoloLens (first-generation) and HoloLens 2, unless otherwise noted:</span></span>

* <span data-ttu-id="a0fec-203">システムは、アプリケーションを 30 Hz でレンダリングするように調整します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-203">The system will throttle the application to 30-Hz rendering.</span></span> <span data-ttu-id="a0fec-204">これにより、MRC を実行するためのヘッドルームが作成されるため、アプリは一定の予算予約を維持する必要がなく、30 fps の MRC ビデオレコードレートにも一致します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-204">This creates some headroom for MRC to run so the app doesn’t need to keep a constant budget reserve and also matches the MRC video record framerate of 30 fps</span></span>
* <span data-ttu-id="a0fec-205">デバイスの右上にあるホログラムコンテンツは、録画/ストリーミングの場合、"スパーク" と表示されることがあります。テキストが読みにくくなり、ホログラムの端がより jaggy に見える可能性があります ( **HoloLens 2** で3番目のカメラのレンダリングをオプトインすると、この侵害が回避されます)。</span><span class="sxs-lookup"><span data-stu-id="a0fec-205">Hologram content in the right eye of the device may appear to “sparkle” when recording/streaming MRC: text may become more difficult to read and hologram edges may appear more jaggy (opting in to third camera render on **HoloLens 2** avoids this compromise)</span></span>
* <span data-ttu-id="a0fec-206">アプリケーションで有効になっている場合、MRC の写真やビデオによってアプリケーションの [フォーカスポイント](../unity/focus-point-in-unity.md) が尊重されます。これにより、ホログラムが正確に配置されます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-206">MRC photos and videos will respect the application’s [focus point](../unity/focus-point-in-unity.md) if the application has enabled it, which will help ensure holograms are accurately positioned.</span></span> <span data-ttu-id="a0fec-207">ビデオの場合、フォーカスポイントが滑らかになるため、フォーカスポイントの深さが大幅に変化した場合に、ホログラムが徐々にずれて表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-207">For videos, the Focus Point is smoothed so holograms may appear to slowly drift into place if the Focus Point depth changes significantly.</span></span> <span data-ttu-id="a0fec-208">フォーカスポイントと異なる深さにあるホログラムは、実際の世界からのオフセットとして表示されることがあります (下の例を参照してください。フォーカスポイントが2メートルで設定されていますが、ホログラムは1メーターに配置されています)。</span><span class="sxs-lookup"><span data-stu-id="a0fec-208">Holograms that are at different depths from the focus point may appear offset from the real world (see example below where Focus Point is set at 2 meters but hologram is positioned at 1 meter).</span></span>

![2メートルのホログラムは、世界に完全に登録されます。](images/hologramaccuracydistancemrc-1000px.png)

## <a name="integrating-mrc-functionality-from-within-your-app"></a><span data-ttu-id="a0fec-211">アプリ内からの MRC 機能の統合</span><span class="sxs-lookup"><span data-stu-id="a0fec-211">Integrating MRC functionality from within your app</span></span>

<span data-ttu-id="a0fec-212">混合の現実アプリでは、アプリ内から MRC 写真またはビデオキャプチャを開始できます。キャプチャされたコンテンツは、デバイスの "カメラロール" に格納されていなくてもアプリで利用できます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-212">Your mixed reality app can start MRC photo or video capture from within the app, and the content captured is made available to your app without being stored to the device's "Camera roll."</span></span> <span data-ttu-id="a0fec-213">カスタムの MRC レコーダーを作成することも、組み込みのカメラキャプチャ UI を利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-213">You can create a custom MRC recorder or take advantage of built-in camera capture UI.</span></span> 

### <a name="mrc-with-built-in-camera-ui"></a><span data-ttu-id="a0fec-214">組み込みのカメラ UI を使用した MRC</span><span class="sxs-lookup"><span data-stu-id="a0fec-214">MRC with built-in camera UI</span></span>

<span data-ttu-id="a0fec-215">開発者は、 *[カメラキャプチャ UI API](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* を使用して、わずか数行のコードでユーザーがキャプチャした mixed reality の写真またはビデオを取得できます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-215">Developers can use the *[Camera Capture UI API](/windows/uwp/audio-video-camera/capture-photos-and-video-with-cameracaptureui)* to get a user-captured mixed reality photo or video with just a few lines of code.</span></span>

<span data-ttu-id="a0fec-216">この API は組み込みの MRC カメラ UI を起動します。ユーザーは、写真やビデオを撮影し、結果として得られたキャプチャをアプリに返すことができます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-216">This API launches the built-in MRC camera UI where users can take a photo or video and returns the resulting capture to your app.</span></span> <span data-ttu-id="a0fec-217">独自のカメラ UI または低レベルのアクセスをキャプチャストリームに追加する必要がある場合は、カスタム Mixed Reality キャプチャレコーダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-217">You can create a custom Mixed Reality Capture recorder if you need to add your own camera UI or lower-level access to capture streams.</span></span>

### <a name="creating-a-custom-mrc-recorder"></a><span data-ttu-id="a0fec-218">カスタム MRC レコーダーの作成</span><span class="sxs-lookup"><span data-stu-id="a0fec-218">Creating a custom MRC recorder</span></span>

<span data-ttu-id="a0fec-219">ユーザーは常にシステム MRC キャプチャサービスを使用して写真またはビデオをトリガーできますが、アプリケーションでは、MRC と同様にカメラストリームにホログラムを含むカスタムカメラアプリをビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-219">While the user can always trigger a photo or video using the system MRC capture service, an application may want to build a custom camera app that include holograms in the camera stream just like MRC.</span></span> <span data-ttu-id="a0fec-220">これにより、アプリケーションは、ユーザー入力からキャプチャを開始したり、カスタムの記録 UI を作成したり、MRC 設定をカスタマイズしていくつかの例に名前を設定したりできます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-220">This allows the application to kick off captures from user input, build custom recording UI, or customize MRC settings to name a few examples.</span></span>

<span data-ttu-id="a0fec-221">**HoloStudio は、MRC 効果を使用してカスタム MRC カメラを追加します**</span><span class="sxs-lookup"><span data-stu-id="a0fec-221">**HoloStudio adds a custom MRC camera using MRC effects**</span></span>

![HoloStudio は、MRC 効果を使用してカスタム MRC カメラを追加します](images/cameraiconholostudio-300px.jpg)

<span data-ttu-id="a0fec-223">Unity アプリケーションでは、プロパティの [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) が表示され、ホログラムが有効になります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-223">Unity Applications should see [Locatable_camera_in_Unity](../unity/locatable-camera-in-unity.md) for the property to enable holograms.</span></span>

<span data-ttu-id="a0fec-224">その他のアプリケーションでは、 [Windows Media Capture api](/uwp/api/Windows.Media.Capture.MediaCapture) を使用してカメラを制御し、ビデオとオーディオ効果を追加して、仮想ホログラムとアプリケーションオーディオを静止画やビデオに含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-224">Other applications can do this by using the [Windows Media Capture APIs](/uwp/api/Windows.Media.Capture.MediaCapture) to control the Camera and add an MRC Video and Audio effect to include virtual holograms and application audio in stills and videos.</span></span>

<span data-ttu-id="a0fec-225">アプリケーションには、効果を追加するためのオプションが2つあります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-225">Applications have two options to add the effect:</span></span>
* <span data-ttu-id="a0fec-226">以前の API: [MediaCapture. AddEffectAsync ()](/uwp/api/windows.media.capture.mediacapture.addeffectasync) 。</span><span class="sxs-lookup"><span data-stu-id="a0fec-226">The older API: [Windows.Media.Capture.MediaCapture.AddEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addeffectasync)</span></span>
* <span data-ttu-id="a0fec-227">新しい Microsoft 推奨 API (オブジェクトを返し、動的プロパティを操作できるようにします)。 MediaCapture [MediaCapture](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync)() は、  /  [](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync)アプリが[IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition)と[IAudioEffectDefinition](/uwp/api/windows.media.effects.iaudioeffectdefinition)の独自の実装を作成する必要があることを必要としますが、これに該当します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-227">The new Microsoft recommended API (returns an object, making it possible to manipulate dynamic properties): [Windows.Media.Capture.MediaCapture.AddVideoEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addvideoeffectasync) / [Windows.Media.Capture.MediaCapture.AddAudioEffectAsync()](/uwp/api/windows.media.capture.mediacapture.addaudioeffectasync) which require the app create its own implementation of [IVideoEffectDefinition](/uwp/api/Windows.Media.Effects.IVideoEffectDefinition) and [IAudioEffectDefinition](/uwp/api/windows.media.effects.iaudioeffectdefinition).</span></span> <span data-ttu-id="a0fec-228">例については、 [MRC サンプルアプリ](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0fec-228">See the [MRC sample app](https://github.com/microsoft/Windows-universal-samples/tree/master/Samples/HolographicMixedRealityCapture) for examples.</span></span>

>[!NOTE]
> <span data-ttu-id="a0fec-229">MixedRealityCapture 名前空間は Visual Studio で認識されませんが、文字列はまだ有効です。</span><span class="sxs-lookup"><span data-stu-id="a0fec-229">The Windows.Media.MixedRealityCapture namespace will not be recognized by Visual Studio, but the strings are still valid.</span></span>

<span data-ttu-id="a0fec-230">MRC ビデオ効果 (**MixedRealityCapture. MixedRealityCaptureVideoEffect**)</span><span class="sxs-lookup"><span data-stu-id="a0fec-230">MRC Video Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureVideoEffect**)</span></span>

|  <span data-ttu-id="a0fec-231">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="a0fec-231">Property Name</span></span>  |  <span data-ttu-id="a0fec-232">Type</span><span class="sxs-lookup"><span data-stu-id="a0fec-232">Type</span></span>  |  <span data-ttu-id="a0fec-233">既定値</span><span class="sxs-lookup"><span data-stu-id="a0fec-233">Default Value</span></span>  |  <span data-ttu-id="a0fec-234">[説明]</span><span class="sxs-lookup"><span data-stu-id="a0fec-234">Description</span></span> |
|----------|----------|----------|----------|
|  <span data-ttu-id="a0fec-235">StreamType</span><span class="sxs-lookup"><span data-stu-id="a0fec-235">StreamType</span></span>  |  <span data-ttu-id="a0fec-236">UINT32 ([Mediastreamtype](/uwp/api/Windows.Media.Capture.MediaStreamType))</span><span class="sxs-lookup"><span data-stu-id="a0fec-236">UINT32 ([MediaStreamType](/uwp/api/Windows.Media.Capture.MediaStreamType))</span></span>  |  <span data-ttu-id="a0fec-237">1 (VideoRecord)</span><span class="sxs-lookup"><span data-stu-id="a0fec-237">1 (VideoRecord)</span></span>  |  <span data-ttu-id="a0fec-238">この効果がどのキャプチャストリームに使用されるかを説明します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-238">Describe which capture stream this effect is used for.</span></span> <span data-ttu-id="a0fec-239">オーディオは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a0fec-239">Audio isn't available.</span></span> |
|  <span data-ttu-id="a0fec-240">HologramCompositionEnabled</span><span class="sxs-lookup"><span data-stu-id="a0fec-240">HologramCompositionEnabled</span></span>  |  <span data-ttu-id="a0fec-241">boolean</span><span class="sxs-lookup"><span data-stu-id="a0fec-241">boolean</span></span>  |  <span data-ttu-id="a0fec-242">true</span><span class="sxs-lookup"><span data-stu-id="a0fec-242">TRUE</span></span>  |  <span data-ttu-id="a0fec-243">ビデオキャプチャのホログラムを有効または無効にするフラグ。</span><span class="sxs-lookup"><span data-stu-id="a0fec-243">Flag to enable or disable holograms in video capture.</span></span> |
|  <span data-ttu-id="a0fec-244">RecordingIndicatorEnabled</span><span class="sxs-lookup"><span data-stu-id="a0fec-244">RecordingIndicatorEnabled</span></span>  |  <span data-ttu-id="a0fec-245">boolean</span><span class="sxs-lookup"><span data-stu-id="a0fec-245">boolean</span></span>  |  <span data-ttu-id="a0fec-246">true</span><span class="sxs-lookup"><span data-stu-id="a0fec-246">TRUE</span></span>  |  <span data-ttu-id="a0fec-247">ホログラムのキャプチャ中に画面の記録インジケーターを有効または無効にするフラグ。</span><span class="sxs-lookup"><span data-stu-id="a0fec-247">Flag to enable or disable recording indicator on screen during hologram capturing.</span></span> |
|  <span data-ttu-id="a0fec-248">VideoStabilizationEnabled</span><span class="sxs-lookup"><span data-stu-id="a0fec-248">VideoStabilizationEnabled</span></span>  |  <span data-ttu-id="a0fec-249">boolean</span><span class="sxs-lookup"><span data-stu-id="a0fec-249">boolean</span></span>  |  <span data-ttu-id="a0fec-250">FALSE</span><span class="sxs-lookup"><span data-stu-id="a0fec-250">FALSE</span></span>  |  <span data-ttu-id="a0fec-251">HoloLens トラッカーを使用して、ビデオの安定化を有効または無効にするフラグ。</span><span class="sxs-lookup"><span data-stu-id="a0fec-251">Flag to enable or disable video stabilization powered by the HoloLens tracker.</span></span> |
|  <span data-ttu-id="a0fec-252">VideoStabilizationBufferLength</span><span class="sxs-lookup"><span data-stu-id="a0fec-252">VideoStabilizationBufferLength</span></span>  |  <span data-ttu-id="a0fec-253">UINT32</span><span class="sxs-lookup"><span data-stu-id="a0fec-253">UINT32</span></span>  |  <span data-ttu-id="a0fec-254">0</span><span class="sxs-lookup"><span data-stu-id="a0fec-254">0</span></span>  |  <span data-ttu-id="a0fec-255">ビデオ安定化に使用する履歴フレームの数を設定します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-255">Set how many historical frames are used for video stabilization.</span></span> <span data-ttu-id="a0fec-256">0は待機時間が0で、電源とパフォーマンスの観点からはほぼ "無料" です。</span><span class="sxs-lookup"><span data-stu-id="a0fec-256">0 is 0-latency and nearly "free" from a power and performance perspective.</span></span> <span data-ttu-id="a0fec-257">最大品質には15が推奨されます (待機時間とメモリの15フレームのコスト)。</span><span class="sxs-lookup"><span data-stu-id="a0fec-257">15 is recommended for highest quality (at the cost of 15 frames of latency and memory).</span></span> |
|  <span data-ttu-id="a0fec-258">GlobalOpacityCoefficient</span><span class="sxs-lookup"><span data-stu-id="a0fec-258">GlobalOpacityCoefficient</span></span>  |  <span data-ttu-id="a0fec-259">float</span><span class="sxs-lookup"><span data-stu-id="a0fec-259">float</span></span>  |  <span data-ttu-id="a0fec-260">0.9 (HoloLens) 1.0 (イマーシブヘッドセット)</span><span class="sxs-lookup"><span data-stu-id="a0fec-260">0.9 (HoloLens) 1.0 (Immersive headset)</span></span>  |  <span data-ttu-id="a0fec-261">0.0 (完全に透明) から 1.0 (完全に不透明) までの範囲内のホログラムのグローバル不透明度係数を設定します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-261">Set global opacity coefficient of hologram in range from 0.0 (fully transparent) to 1.0 (fully opaque).</span></span> |
|  <span data-ttu-id="a0fec-262">BlankOnProtectedContent</span><span class="sxs-lookup"><span data-stu-id="a0fec-262">BlankOnProtectedContent</span></span>  |  <span data-ttu-id="a0fec-263">boolean</span><span class="sxs-lookup"><span data-stu-id="a0fec-263">boolean</span></span>  |  <span data-ttu-id="a0fec-264">FALSE</span><span class="sxs-lookup"><span data-stu-id="a0fec-264">FALSE</span></span>  |  <span data-ttu-id="a0fec-265">保護されたコンテンツを示す 2d UWP アプリがある場合に空のフレームを返すことを有効または無効にするフラグ。</span><span class="sxs-lookup"><span data-stu-id="a0fec-265">Flag to enable or disable returning an empty frame if there's a 2d UWP app showing protected content.</span></span> <span data-ttu-id="a0fec-266">このフラグが false で、2d UWP アプリで保護されたコンテンツが表示されている場合、2d UWP アプリはヘッドセットと mixed reality キャプチャの両方で保護されたコンテンツテクスチャに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-266">If this flag is false and a 2d UWP app is showing protected content, the 2d UWP app will be replaced by a protected content texture in both the headset and in the mixed reality capture.</span></span> |
|  <span data-ttu-id="a0fec-267">ShowHiddenMesh</span><span class="sxs-lookup"><span data-stu-id="a0fec-267">ShowHiddenMesh</span></span>  |  <span data-ttu-id="a0fec-268">boolean</span><span class="sxs-lookup"><span data-stu-id="a0fec-268">boolean</span></span>  |  <span data-ttu-id="a0fec-269">FALSE</span><span class="sxs-lookup"><span data-stu-id="a0fec-269">FALSE</span></span>  |  <span data-ttu-id="a0fec-270">Holographic カメラの非表示領域メッシュと隣接するコンテンツの表示を有効または無効にするフラグ。</span><span class="sxs-lookup"><span data-stu-id="a0fec-270">Flag to enable or disable showing the holographic camera's hidden area mesh and neighboring content.</span></span> |
| <span data-ttu-id="a0fec-271">OutputSize</span><span class="sxs-lookup"><span data-stu-id="a0fec-271">OutputSize</span></span> | <span data-ttu-id="a0fec-272">サイズ</span><span class="sxs-lookup"><span data-stu-id="a0fec-272">Size</span></span> | <span data-ttu-id="a0fec-273">0, 0</span><span class="sxs-lookup"><span data-stu-id="a0fec-273">0, 0</span></span> | <span data-ttu-id="a0fec-274">ビデオの安定化のトリミング後に、目的の出力サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-274">Set the desired output size after cropping for video stabilization.</span></span> <span data-ttu-id="a0fec-275">0または無効な出力サイズが指定されている場合は、既定のトリミングサイズが選択されます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-275">A default crop size is chosen if 0 or an invalid output size is specified.</span></span> |
| <span data-ttu-id="a0fec-276">PreferredHologramPerspective</span><span class="sxs-lookup"><span data-stu-id="a0fec-276">PreferredHologramPerspective</span></span> | <span data-ttu-id="a0fec-277">UINT32</span><span class="sxs-lookup"><span data-stu-id="a0fec-277">UINT32</span></span> | <span data-ttu-id="a0fec-278">Windows デバイスポータルでの **カメラ設定からのレンダリング**</span><span class="sxs-lookup"><span data-stu-id="a0fec-278">**Render from Camera** setting in the Windows Device Portal</span></span> | <span data-ttu-id="a0fec-279">キャプチャする holographic カメラビューの構成を示すために使用される列挙: 0 (ディスプレイ) は、アプリが写真/ビデオカメラからのレンダリングを要求されないことを意味します。 1 (PhotoVideoCamera) は、アプリが写真/ビデオカメラからレンダリングするように要求します (アプリがサポートしている場合)。</span><span class="sxs-lookup"><span data-stu-id="a0fec-279">Enum used to indicate which holographic camera view configuration should be captured: 0 (Display) means that the app won't be asked to render from the photo/video camera, 1 (PhotoVideoCamera) will ask the app to render from the photo/video camera (if the app supports it).</span></span> <span data-ttu-id="a0fec-280">HoloLens 2 でのみサポートされます</span><span class="sxs-lookup"><span data-stu-id="a0fec-280">Only supported on HoloLens 2</span></span> |

>[!NOTE]
> <span data-ttu-id="a0fec-281">Windows デバイスポータルで **PreferredHologramPerspective** の既定値を変更するには、[ [Mixed Reality Capture] ページ](using-the-windows-device-portal.md#mixed-reality-capture) に移動し、[ **カメラからのレンダリング**] をオフにします。</span><span class="sxs-lookup"><span data-stu-id="a0fec-281">You can change the default value of **PreferredHologramPerspective** in the Windows Device Portal by going to the [Mixed Reality Capture page](using-the-windows-device-portal.md#mixed-reality-capture) and unchecking **Render from Camera**.</span></span> <span data-ttu-id="a0fec-282">この設定は既定で **1 (PhotoVideoCamera)** に設定されていますが、 **0 (表示)** に設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="a0fec-282">The setting defaults to **1 (PhotoVideoCamera)**, but can be unchecked to set it to **0 (Display)**.</span></span>
>
> <span data-ttu-id="a0fec-283">**PreferredHologramPerspective** の既定値は、2020年6月の更新プログラム (windows Holographic、バージョン2004ビルド19041.1106、windows Holographic、バージョン1903ビルド 18362.1064 **) より前** のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="a0fec-283">The default value of **PreferredHologramPerspective** was **0 (Display)** prior to the June 2020 update (Windows Holographic, version 2004 build 19041.1106 and Windows Holographic, version 1903 build 18362.1064).</span></span>

<span data-ttu-id="a0fec-284">MRC オーディオ効果 (**MixedRealityCapture. MixedRealityCaptureAudioEffect**)</span><span class="sxs-lookup"><span data-stu-id="a0fec-284">MRC Audio Effect (**Windows.Media.MixedRealityCapture.MixedRealityCaptureAudioEffect**)</span></span>

| <span data-ttu-id="a0fec-285">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="a0fec-285">Property Name</span></span> | <span data-ttu-id="a0fec-286">Type</span><span class="sxs-lookup"><span data-stu-id="a0fec-286">Type</span></span> | <span data-ttu-id="a0fec-287">既定値</span><span class="sxs-lookup"><span data-stu-id="a0fec-287">Default Value</span></span> | <span data-ttu-id="a0fec-288">[説明]</span><span class="sxs-lookup"><span data-stu-id="a0fec-288">Description</span></span> |
|----------|----------|----------|----------|
| <span data-ttu-id="a0fec-289">MixerMode</span><span class="sxs-lookup"><span data-stu-id="a0fec-289">MixerMode</span></span> | <span data-ttu-id="a0fec-290">UINT32</span><span class="sxs-lookup"><span data-stu-id="a0fec-290">UINT32</span></span> | <span data-ttu-id="a0fec-291">2 (Mic とシステムオーディオ)</span><span class="sxs-lookup"><span data-stu-id="a0fec-291">2 (Mic and System audio)</span></span> | <span data-ttu-id="a0fec-292">使用するオーディオソースを示すために使用する列挙: 0 (Mic オーディオのみ)、1 (システムオーディオのみ)、2 (Mic およびシステムオーディオ)</span><span class="sxs-lookup"><span data-stu-id="a0fec-292">Enum used to indicate which audio sources should be used: 0 (Mic audio only), 1 (System audio only), 2 (Mic and System audio)</span></span> |
| <span data-ttu-id="a0fec-293">LoopbackGain</span><span class="sxs-lookup"><span data-stu-id="a0fec-293">LoopbackGain</span></span> | <span data-ttu-id="a0fec-294">float</span><span class="sxs-lookup"><span data-stu-id="a0fec-294">float</span></span> | <span data-ttu-id="a0fec-295">Windows デバイスポータルでの **アプリオーディオゲイン** 設定</span><span class="sxs-lookup"><span data-stu-id="a0fec-295">**App Audio Gain** setting in the Windows Device Portal</span></span> | <span data-ttu-id="a0fec-296">システムオーディオボリュームに適用します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-296">Gain to apply to system audio volume.</span></span> <span data-ttu-id="a0fec-297">範囲は 0.0 ~ 5.0 です。</span><span class="sxs-lookup"><span data-stu-id="a0fec-297">Ranges from 0.0 to 5.0.</span></span> <span data-ttu-id="a0fec-298">HoloLens 2 でのみサポートされます</span><span class="sxs-lookup"><span data-stu-id="a0fec-298">Only supported on HoloLens 2</span></span> |
| <span data-ttu-id="a0fec-299">マイクロ電話の獲得</span><span class="sxs-lookup"><span data-stu-id="a0fec-299">MicrophoneGain</span></span> | <span data-ttu-id="a0fec-300">float</span><span class="sxs-lookup"><span data-stu-id="a0fec-300">float</span></span> | <span data-ttu-id="a0fec-301">Windows デバイスポータルでの **Mic オーディオゲイン** 設定</span><span class="sxs-lookup"><span data-stu-id="a0fec-301">**Mic Audio Gain** setting in the Windows Device Portal</span></span> | <span data-ttu-id="a0fec-302">Mic ボリュームに適用します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-302">Gain to apply to mic volume.</span></span> <span data-ttu-id="a0fec-303">範囲は 0.0 ~ 5.0 です。</span><span class="sxs-lookup"><span data-stu-id="a0fec-303">Ranges from 0.0 to 5.0.</span></span> <span data-ttu-id="a0fec-304">HoloLens 2 でのみサポートされます</span><span class="sxs-lookup"><span data-stu-id="a0fec-304">Only supported on HoloLens 2</span></span> |

>[!NOTE]
> <span data-ttu-id="a0fec-305">Windows デバイスポータルでは、[ [Mixed Reality Capture] ページ](using-the-windows-device-portal.md#mixed-reality-capture)に移動し、それぞれの設定の横にあるスライダーを調整することにより、 **LoopbackGain** または **マイクロホップゲイン** の既定値を変更できます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-305">You can change the default value of **LoopbackGain** or **MicrophoneGain** in the Windows Device Portal by going to the [Mixed Reality Capture page](using-the-windows-device-portal.md#mixed-reality-capture) and adjusting the slider next to their respective settings.</span></span> <span data-ttu-id="a0fec-306">どちらの設定も既定で **1.0** に設定されていますが、 **0.0** から **5.0** までの任意の値に設定できます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-306">Both settings default to **1.0**, but can be set to any value between **0.0** and **5.0**.</span></span>
>
> <span data-ttu-id="a0fec-307">Windows デバイスポータルを使用して既定のゲイン値を構成するには、2020年6月の更新プログラム (Windows Holographic、バージョン2004ビルド19041.1106、Windows Holographic、バージョン1903ビルド 18362.1064) が追加されました。</span><span class="sxs-lookup"><span data-stu-id="a0fec-307">Using Windows Device Portal to configure the default gain values was added with the June 2020 update (Windows Holographic, version 2004 build 19041.1106 and Windows Holographic, version 1903 build 18362.1064).</span></span>

### <a name="simultaneous-mrc-limitations"></a><span data-ttu-id="a0fec-308">同時の MRC の制限事項</span><span class="sxs-lookup"><span data-stu-id="a0fec-308">Simultaneous MRC limitations</span></span>

<span data-ttu-id="a0fec-309">複数のアプリが同時に MRC にアクセスする場合は、特定の制限事項に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-309">You need to be aware of certain limitations when multiple apps are accessing MRC at the same time.</span></span>

#### <a name="photovideo-camera-access"></a><span data-ttu-id="a0fec-310">写真/ビデオカメラへのアクセス</span><span class="sxs-lookup"><span data-stu-id="a0fec-310">Photo/video camera access</span></span>

<span data-ttu-id="a0fec-311">HoloLens 1 では、プロセスがビデオを録画したり写真を撮影したりしている間、MRC は写真のキャプチャやビデオのキャプチャに失敗します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-311">On HoloLens 1, MRC will fail to capture a photo or capture video while a process is recording video or taking a photo.</span></span> <span data-ttu-id="a0fec-312">また、この逆も当てはまります。 MRC が実行されている場合、アプリケーションはカメラへのアクセスを取得できません。</span><span class="sxs-lookup"><span data-stu-id="a0fec-312">The reverse is also true: if MRC is running, the application will fail to get access to the camera.</span></span> 

<span data-ttu-id="a0fec-313">HoloLens 2 では、カメラへのアクセスを共有できます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-313">With HoloLens 2, it's possible for you to share access to the camera.</span></span> <span data-ttu-id="a0fec-314">解像度やフレームレートを直接制御する必要がない場合は、 [Sharedmode プロパティ](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) を sharedmode として使用して MediaCapture を初期化できます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-314">If you don't need direct control of the resolution or frame-rate, you can initialize MediaCapture using the [SharedMode property](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041) with SharedReadOnly.</span></span>  

##### <a name="built-in-mrc-photovideo-camera-access"></a><span data-ttu-id="a0fec-315">組み込みの MRC フォト/ビデオカメラアクセス</span><span class="sxs-lookup"><span data-stu-id="a0fec-315">Built-in MRC photo/video camera access</span></span>

<span data-ttu-id="a0fec-316">Windows 10 に組み込まれた MRC 機能 (Cortana、スタートメニュー、ハードウェアショートカット、Miracast、Windows デバイスポータル):</span><span class="sxs-lookup"><span data-stu-id="a0fec-316">MRC functionality built into Windows 10 (via Cortana, Start Menu, hardware shortcuts, Miracast, Windows Device Portal):</span></span>

* <span data-ttu-id="a0fec-317">既定では ExclusiveControl を使用して実行されます</span><span class="sxs-lookup"><span data-stu-id="a0fec-317">Will run with ExclusiveControl by default</span></span>

<span data-ttu-id="a0fec-318">ただし、のサポートは、共有モードで動作するために、MRC サブシステムに追加されています。</span><span class="sxs-lookup"><span data-stu-id="a0fec-318">However, support has been added to MRC subsystem to operate in a shared mode:</span></span> 

* <span data-ttu-id="a0fec-319">アプリが写真/ビデオカメラへの ExclusiveControl アクセスを要求した場合、組み込みの MRC は、アプリの要求が成功するように、写真/ビデオカメラの使用を自動的に停止します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-319">If an app requests ExclusiveControl access to the photo/video camera, built-in MRC will automatically stop using the photo/video camera so the app's request will succeed</span></span> 
* <span data-ttu-id="a0fec-320">アプリの ExclusiveControl 中に作成された MRC が開始された場合、組み込みの MRC は SharedReadOnly モードで実行されます</span><span class="sxs-lookup"><span data-stu-id="a0fec-320">If built in MRC is started while an app has ExclusiveControl, built-in MRC will run in SharedReadOnly mode</span></span> 

<span data-ttu-id="a0fec-321">この共有モード機能には、いくつかの制限があります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-321">This shared mode functionality has certain restrictions:</span></span>

* <span data-ttu-id="a0fec-322">Cortana、ハードウェアショートカット、または [スタート] メニューを使用した写真: Windows 10 April 2018 更新プログラム (またはそれ以降) が必要</span><span class="sxs-lookup"><span data-stu-id="a0fec-322">Photo via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="a0fec-323">Cortana、ハードウェアショートカット、または [スタート] メニューを使用したビデオ: Windows 10 April 2018 更新プログラム (またはそれ以降) が必要です。</span><span class="sxs-lookup"><span data-stu-id="a0fec-323">Video via Cortana, hardware shortcuts, or Start Menu: Requires the Windows 10 April 2018 Update (or later)</span></span>
* <span data-ttu-id="a0fec-324">Miracast 経由のストリーミング MRC: Windows 10 10 月2018更新プログラム (またはそれ以降) が必要です。</span><span class="sxs-lookup"><span data-stu-id="a0fec-324">Streaming MRC over Miracast: Requires the Windows 10 October 2018 Update (or later)</span></span>
* <span data-ttu-id="a0fec-325">Windows デバイスポータルまたは HoloLens コンパニオンアプリを使用したストリーミング MRC: HoloLens 2 が必要です</span><span class="sxs-lookup"><span data-stu-id="a0fec-325">Streaming MRC over Windows Device Portal or via the HoloLens companion app: Requires HoloLens 2</span></span>

>[!NOTE]
> <span data-ttu-id="a0fec-326">別のアプリが写真/ビデオカメラを使用している場合、組み込みの MRC カメラ UI の解像度とフレームレートは通常の値から小さくなることがあります。</span><span class="sxs-lookup"><span data-stu-id="a0fec-326">The resolution and frame-rate of the built-in MRC camera UI might be reduced from its normal values when another app is using the photo/video camera.</span></span>

#### <a name="mrc-access-for-developers"></a><span data-ttu-id="a0fec-327">開発者向けの MRC アクセス</span><span class="sxs-lookup"><span data-stu-id="a0fec-327">MRC access for developers</span></span>

<span data-ttu-id="a0fec-328">MRC を使用する場合は、常にカメラに排他的な制御を要求することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a0fec-328">We recommend you always request Exclusive control for the camera when using MRC.</span></span> <span data-ttu-id="a0fec-329">これにより、上記の制限事項を認識している限り、アプリケーションはカメラの設定を完全に制御できます。</span><span class="sxs-lookup"><span data-stu-id="a0fec-329">This will ensure your application has full control of the settings for the camera as long as you're aware of the limitations listed above.</span></span> 

* <span data-ttu-id="a0fec-330">[初期化設定](/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)を使用してメディアキャプチャオブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="a0fec-330">Create a media capture object using the [initialization settings](/uwp/api/windows.media.capture.mediacaptureinitializationsettings?view=winrt-19041)</span></span>
* <span data-ttu-id="a0fec-331">[Sharingmode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode)プロパティを **exclusive** に設定します。</span><span class="sxs-lookup"><span data-stu-id="a0fec-331">Set the [SharingMode](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#Windows_Media_Capture_MediaCaptureInitializationSettings_SharingMode) property to **exclusive**</span></span>

> [!CAUTION]
> <span data-ttu-id="a0fec-332">続行する前に、 [「Sharingmode の解説」](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) をよくお読みください。</span><span class="sxs-lookup"><span data-stu-id="a0fec-332">Be sure to carefully read the [SharingMode remarks](/uwp/api/windows.media.capture.mediacaptureinitializationsettings.sharingmode?view=winrt-19041#remarks) before continuing.</span></span>

* <span data-ttu-id="a0fec-333">カメラを希望どおりにセットアップする</span><span class="sxs-lookup"><span data-stu-id="a0fec-333">Set up your camera the way you want it</span></span>
* <span data-ttu-id="a0fec-334">アプリを起動し、start API でビデオフレームをキャプチャして、MRC を有効にします</span><span class="sxs-lookup"><span data-stu-id="a0fec-334">Start the app, capture video frames with the start API, then enable MRC</span></span>

> [!CAUTION]
> <span data-ttu-id="a0fec-335">アプリを開始する前に、MRC を開始した場合、機能が期待どおりに動作することを保証できません。</span><span class="sxs-lookup"><span data-stu-id="a0fec-335">If you start MRC before you start your app, we can't guarantee the feature will work as expected.</span></span>

<span data-ttu-id="a0fec-336">上記のプロセスの完全なサンプルについては、 [holographic face tracking サンプル](/samples/microsoft/windows-universal-samples/holographicfacetracking)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0fec-336">You can find a full sample of the above process in the [holographic face tracking sample](/samples/microsoft/windows-universal-samples/holographicfacetracking).</span></span>

> [!NOTE]
> <span data-ttu-id="a0fec-337">Windows 10 の2018年4月に更新される前は、アプリのカスタム MRC レコーダーはシステム MRC と同時に使用できませんでした (写真をキャプチャする、ビデオをキャプチャする、または Windows デバイスポータルからストリーミングする)。</span><span class="sxs-lookup"><span data-stu-id="a0fec-337">Before the Windows 10 April 2018 Update, an app's custom MRC recorder was mutually exclusive with system MRC (capturing photos, capturing videos, or streaming from the Windows Device Portal).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0fec-338">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0fec-338">See also</span></span>

* [<span data-ttu-id="a0fec-339">複合現実キャプチャ</span><span class="sxs-lookup"><span data-stu-id="a0fec-339">Mixed reality capture</span></span>](/hololens/holographic-photos-and-videos)
* [<span data-ttu-id="a0fec-340">Spectator View</span><span class="sxs-lookup"><span data-stu-id="a0fec-340">Spectator view</span></span>](spectator-view.md)
* [<span data-ttu-id="a0fec-341">Unity 開発の概要</span><span class="sxs-lookup"><span data-stu-id="a0fec-341">Unity Development Overview</span></span>](../unity/unity-development-overview.md)
* [<span data-ttu-id="a0fec-342">Unreal 開発の概要</span><span class="sxs-lookup"><span data-stu-id="a0fec-342">Unreal development overview</span></span>](../unreal/unreal-development-overview.md)
