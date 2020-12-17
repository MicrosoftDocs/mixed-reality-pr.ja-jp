---
title: Unity でサポートされている OpenXR プラグインの機能
description: Unity での mixed reality 開発に OpenXR がサポートする機能について説明します。
author: hferrone
ms.author: alexturn
ms.date: 12/15/2020
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 拡張現実, 仮想現実, mixed reality ヘッドセット, 学習, チュートリアル, 概要
ms.openlocfilehash: 5db08dee6b26de6fa3f44d92709e4903bb90a44c
ms.sourcegitcommit: 7595db7438398b5c78cec41a6f8ab625711bf8ec
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97664420"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="01ce7-104">Unity でサポートされている Mixed Reality OpenXR の機能</span><span class="sxs-lookup"><span data-stu-id="01ce7-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="01ce7-105">**Mixed Reality OpenXR プラグイン** パッケージは Unity の **OpenXR プラグイン** の拡張機能であり、HoloLens 2 および Windows Mixed Reality ヘッドセットの一連の機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="01ce7-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="01ce7-106">続行する前に、 **unity 2020.2** 以降、 **OpenXR プラグインバージョン 0.1.1** 以降がインストールされていること、および unity プロジェクトが [OpenXR 用に構成](openxr-getting-started.md)されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="01ce7-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.1** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="01ce7-107">サポートされる操作</span><span class="sxs-lookup"><span data-stu-id="01ce7-107">What's supported</span></span>

<span data-ttu-id="01ce7-108">現在、次の機能がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="01ce7-108">The following features are currently supported:</span></span>

* <span data-ttu-id="01ce7-109">Windows Mixed Reality ヘッドセット用の HoloLens 2 および Win32 VR アプリケーションの両方の UWP アプリケーションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="01ce7-109">Supports both UWP applications for HoloLens 2 and Win32 VR applications for Windows Mixed Reality headsets.</span></span>
* <span data-ttu-id="01ce7-110">HoloLens 2 アプリケーションの UWP パッケージと CoreWindow の相互作用を最適化します。</span><span class="sxs-lookup"><span data-stu-id="01ce7-110">Optimizes UWP package and CoreWindow interaction for HoloLens 2 applications.</span></span>
* <span data-ttu-id="01ce7-111">アンカーと無制限のスペースを使用したワールドスケールの追跡。</span><span class="sxs-lookup"><span data-stu-id="01ce7-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="01ce7-112">ストレージ API を固定して、HoloLens 2 ローカルストレージにアンカーを保持します。</span><span class="sxs-lookup"><span data-stu-id="01ce7-112">Anchor storage API to persist anchors to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="01ce7-113">新しい HP リバーブ G2 コントローラーを含む、[モーションコントローラーと手作業のやり取り](#motion-controller-and-hand-interactions)。</span><span class="sxs-lookup"><span data-stu-id="01ce7-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="01ce7-114">26個の関節と結合半径の入力を使用した、トレーラーを使用したハンドトラッキング。</span><span class="sxs-lookup"><span data-stu-id="01ce7-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="01ce7-115">HoloLens 2 での視線の相互作用。</span><span class="sxs-lookup"><span data-stu-id="01ce7-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="01ce7-116">HoloLens 2 で写真/ビデオ (PV) カメラを検索しています。</span><span class="sxs-lookup"><span data-stu-id="01ce7-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="01ce7-117">PV カメラを使用した第3目のレンダリングを使用した Mixed Reality キャプチャ。</span><span class="sxs-lookup"><span data-stu-id="01ce7-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="01ce7-118">[Holographic リモート処理アプリでの HoloLens 2 への "Play" を](#holographic-remoting-in-unity-editor-play-mode)サポートします。これにより、開発者は、デバイスにビルドしてデプロイすることなく、スクリプトをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="01ce7-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="01ce7-119">Mrtk Unity 2.5.2 から MRTK OpenXR adapter パッケージに準拠しています。</span><span class="sxs-lookup"><span data-stu-id="01ce7-119">Compatible with MRTK Unity 2.5.2 through MRTK OpenXR adapter package.</span></span> <missing link>
* <span data-ttu-id="01ce7-120">Unity [Arfoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 以降との互換性</span><span class="sxs-lookup"><span data-stu-id="01ce7-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later</span></span>

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="01ce7-121">Unity エディター再生モードでの Holographic リモート処理</span><span class="sxs-lookup"><span data-stu-id="01ce7-121">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="01ce7-122">Visual Studio プロジェクトで UWP Unity プロジェクトをビルドしてから、パッケージ化して HoloLens 2 デバイスに配置すると、時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="01ce7-122">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="01ce7-123">1つの解決策は、Holographic エディターのリモート処理を有効にすることです。これにより、ネットワーク上の HoloLens 2 デバイスに対して "Play" モードで直接 C# スクリプトをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="01ce7-123">One solution is to enable the Holographic Editor Remoting, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="01ce7-124">このシナリオでは、UWP パッケージをビルドしてリモートデバイスに配置するオーバーヘッドを回避します。</span><span class="sxs-lookup"><span data-stu-id="01ce7-124">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="01ce7-125">まず、HoloLens 2 のストアから [Holographic Remoting Player アプリをインストール](https://www.microsoft.com/store/productId/9NBLGGH4SV40) する必要があります。</span><span class="sxs-lookup"><span data-stu-id="01ce7-125">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from Store on your HoloLens 2</span></span>  
2. <span data-ttu-id="01ce7-126">HoloLens 2 で Holographic リモート処理プレーヤーアプリを実行すると、接続先のバージョン番号と IP アドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="01ce7-126">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="01ce7-127">OpenXR プラグインを使用するには、v2.0 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="01ce7-127">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

![HoloLens で実行されている Holographic リモート処理プレーヤーのスクリーンショット](images/openxr-features-img-01.png)

3. <span data-ttu-id="01ce7-129">[ **編集-> プロジェクトの設定**] を開き、 **XR プラグイン管理** に移動して、[ **Windows Mixed Reality] 機能セット** ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="01ce7-129">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

![XR プラグイン管理が強調表示されている Unity エディターで開いているプロジェクト設定パネルのスクリーンショット](images/openxr-features-img-02.png)

4. <span data-ttu-id="01ce7-131">**OpenXR** の [**機能**] セクションを展開し、[**すべて表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="01ce7-131">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
5. <span data-ttu-id="01ce7-132">[ **Holographic エディターリモート処理** ] チェックボックスをオンにして、Holographic リモート処理アプリから取得した IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="01ce7-132">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

![機能が強調表示されている Unity エディターでプロジェクト設定パネルが開いているスクリーンショット](images/openxr-features-img-03.png)

<span data-ttu-id="01ce7-134">これで、[Play] \ (再生 \) ボタンをクリックして、HoloLens の Holographic リモート処理アプリで Unity アプリを再生できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="01ce7-134">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="01ce7-135">また、 [Visual Studio を Unity にアタッチ](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) して、C# スクリプトを再生モードでデバッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="01ce7-135">You can also [attach Visual Studio to Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="01ce7-136">0.1.0 のバージョンでは、Holographic リモート処理ではアンカー機能がサポートされておらず、ARAnchorManager 機能はリモート処理では機能しません。</span><span class="sxs-lookup"><span data-stu-id="01ce7-136">As of version 0.1.0 the Holographic Remoting, runtime doesn’t support Anchor feature, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="01ce7-137">この機能は今後のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="01ce7-137">This feature is coming in future releases.</span></span>

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="01ce7-138">モーションコントローラーとハンド作用</span><span class="sxs-lookup"><span data-stu-id="01ce7-138">Motion controller and hand interactions</span></span>
<span data-ttu-id="01ce7-139">Unity での mixed reality の相互作用の基本については、unity の unity の [XR 入力](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="01ce7-139">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="01ce7-140">この Unity ドキュメントでは、コントローラー固有の入力からより多くの汎化に対するマッピング、 `InputFeatureUsage` 使用可能な XR 入力を識別および分類する方法、これらの入力からデータを読み取る方法などについて説明します。</span><span class="sxs-lookup"><span data-stu-id="01ce7-140">This Unity documentation covers the mappings from controller-specific inputs to more generalizable `InputFeatureUsage`s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span> 
 
<span data-ttu-id="01ce7-141">Mixed Reality OpenXR プラグインは、次に示すように、標準のにマップされている追加の入力インタラクションプロファイルを提供し `InputFeatureUsage` ます。</span><span class="sxs-lookup"><span data-stu-id="01ce7-141">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard `InputFeatureUsage`s as detailed below:</span></span> 
 
| `InputFeatureUsage` | <span data-ttu-id="01ce7-142">HP リバーブ G2 コントローラー (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="01ce7-142">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="01ce7-143">HoloLens (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="01ce7-143">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="01ce7-144">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="01ce7-144">primary2DAxis</span></span> | <span data-ttu-id="01ce7-145">ジョイ</span><span class="sxs-lookup"><span data-stu-id="01ce7-145">Joystick</span></span> | |
| <span data-ttu-id="01ce7-146">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="01ce7-146">primary2DAxisClick</span></span> | <span data-ttu-id="01ce7-147">ジョイスティック-クリック</span><span class="sxs-lookup"><span data-stu-id="01ce7-147">Joystick - Click</span></span> | |
| <span data-ttu-id="01ce7-148">トリガー (trigger)</span><span class="sxs-lookup"><span data-stu-id="01ce7-148">trigger</span></span> | <span data-ttu-id="01ce7-149">トリガー</span><span class="sxs-lookup"><span data-stu-id="01ce7-149">Trigger</span></span>  | |
| <span data-ttu-id="01ce7-150">把握</span><span class="sxs-lookup"><span data-stu-id="01ce7-150">grip</span></span> | <span data-ttu-id="01ce7-151">把握</span><span class="sxs-lookup"><span data-stu-id="01ce7-151">Grip</span></span> | <span data-ttu-id="01ce7-152">エアタップまたはつかみ</span><span class="sxs-lookup"><span data-stu-id="01ce7-152">Air tap or squeeze</span></span> |
| <span data-ttu-id="01ce7-153">primaryButton</span><span class="sxs-lookup"><span data-stu-id="01ce7-153">primaryButton</span></span> | <span data-ttu-id="01ce7-154">[X/A]-押します</span><span class="sxs-lookup"><span data-stu-id="01ce7-154">[X/A] - Press</span></span> | <span data-ttu-id="01ce7-155">エアタップ</span><span class="sxs-lookup"><span data-stu-id="01ce7-155">Air tap</span></span> |
| <span data-ttu-id="01ce7-156">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="01ce7-156">secondaryButton</span></span> | <span data-ttu-id="01ce7-157">[Y/B]-押します</span><span class="sxs-lookup"><span data-stu-id="01ce7-157">[Y/B] - Press</span></span> | |
| <span data-ttu-id="01ce7-158">gripButton</span><span class="sxs-lookup"><span data-stu-id="01ce7-158">gripButton</span></span> | <span data-ttu-id="01ce7-159">グリップ-押す</span><span class="sxs-lookup"><span data-stu-id="01ce7-159">Grip - Press</span></span> | |
| <span data-ttu-id="01ce7-160">triggerButton</span><span class="sxs-lookup"><span data-stu-id="01ce7-160">triggerButton</span></span> | <span data-ttu-id="01ce7-161">トリガー-押す</span><span class="sxs-lookup"><span data-stu-id="01ce7-161">Trigger - Press</span></span> | |
| <span data-ttu-id="01ce7-162">menuButton</span><span class="sxs-lookup"><span data-stu-id="01ce7-162">menuButton</span></span> | <span data-ttu-id="01ce7-163">メニュー</span><span class="sxs-lookup"><span data-stu-id="01ce7-163">Menu</span></span> | |

#### <a name="haptics"></a><span data-ttu-id="01ce7-164">Haptics</span><span class="sxs-lookup"><span data-stu-id="01ce7-164">Haptics</span></span>
<span data-ttu-id="01ce7-165">Unity の XR 入力システムで haptics を使用する方法の詳細については、unity の unity [マニュアルの「UNITY XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="01ce7-165">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span> 


## <a name="whats-coming-soon"></a><span data-ttu-id="01ce7-166">近日公開予定</span><span class="sxs-lookup"><span data-stu-id="01ce7-166">What's coming soon</span></span>

<span data-ttu-id="01ce7-167">次の問題および不足している機能は、Mixed Reality OpenXR プラグイン **バージョン 0.1.0** で知られています。</span><span class="sxs-lookup"><span data-stu-id="01ce7-167">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="01ce7-168">これらの機能については、今後のリリースで修正と新機能をリリースする予定です。</span><span class="sxs-lookup"><span data-stu-id="01ce7-168">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="01ce7-169">**ARPlaneSubsystem** はまだサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="01ce7-169">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="01ce7-170">HoloLens 2 では、 **Arplan emanager**、 **ARRaycastManager**、および ARANCHORMANAGER などの関連 API もサポートされていません **。**</span><span class="sxs-lookup"><span data-stu-id="01ce7-170">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="01ce7-171">**アンカー** は Holographic リモート処理ではまだサポートされていませんが、近い将来に登場します。</span><span class="sxs-lookup"><span data-stu-id="01ce7-171">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="01ce7-172">**手動メッシュ** 追跡、 **QR コード**、 **XRMeshSubsystem** はまだサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="01ce7-172">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="01ce7-173">**Azure 空間アンカー** のサポートは、今後のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="01ce7-173">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="01ce7-174">**ARM64** は、HoloLens 2 アプリで唯一サポートされているプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="01ce7-174">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="01ce7-175">**ARM** プラットフォームは今後のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="01ce7-175">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="01ce7-176">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="01ce7-176">Troubleshooting</span></span> 

<span data-ttu-id="01ce7-177">HoloLens 2 で Unity アプリを中断および再開すると、アプリは正しく再開できなくなります。これにより、HoloLens ビューでは、4つのスピン点が表示されます。</span><span class="sxs-lookup"><span data-stu-id="01ce7-177">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span> 
* <span data-ttu-id="01ce7-178">回避策として、OpenXR プロジェクト設定で [ **深さの送信モード** ] を **[なし** ] に設定します。</span><span class="sxs-lookup"><span data-stu-id="01ce7-178">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
