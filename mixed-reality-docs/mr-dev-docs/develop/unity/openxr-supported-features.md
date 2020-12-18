---
title: Unity でサポートされている OpenXR プラグインの機能
description: Unity での mixed reality 開発に OpenXR がサポートする機能について説明します。
author: hferrone
ms.author: alexturn
ms.date: 12/15/2020
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, mixed reality, MRTK, Mixed Reality Toolkit, 拡張現実, 仮想現実, mixed reality ヘッドセット, 学習, チュートリアル, 概要
ms.openlocfilehash: 1cbe9dd1ffb493bcc9da76e70dec9720f2d10340
ms.sourcegitcommit: 4bbf2f802117a9a3788b2b0e3b0a2f58e187f6ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2020
ms.locfileid: "97665364"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="2f355-104">Unity でサポートされている Mixed Reality OpenXR の機能</span><span class="sxs-lookup"><span data-stu-id="2f355-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="2f355-105">**Mixed Reality OpenXR プラグイン** パッケージは Unity の **OpenXR プラグイン** の拡張機能であり、HoloLens 2 および Windows Mixed Reality ヘッドセットの一連の機能をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="2f355-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="2f355-106">続行する前に、 **unity 2020.2** 以降、 **OpenXR プラグインバージョン 0.1.1** 以降がインストールされていること、および unity プロジェクトが [OpenXR 用に構成](openxr-getting-started.md)されていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="2f355-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.1** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="2f355-107">サポートされる操作</span><span class="sxs-lookup"><span data-stu-id="2f355-107">What's supported</span></span>

<span data-ttu-id="2f355-108">現在、次の機能がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="2f355-108">The following features are currently supported:</span></span>

* <span data-ttu-id="2f355-109">Windows Mixed Reality ヘッドセット用の HoloLens 2 および Win32 VR アプリケーションの両方の UWP アプリケーションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="2f355-109">Supports both UWP applications for HoloLens 2 and Win32 VR applications for Windows Mixed Reality headsets.</span></span>
* <span data-ttu-id="2f355-110">HoloLens 2 アプリケーションの UWP パッケージと CoreWindow の相互作用を最適化します。</span><span class="sxs-lookup"><span data-stu-id="2f355-110">Optimizes UWP package and CoreWindow interaction for HoloLens 2 applications.</span></span>
* <span data-ttu-id="2f355-111">アンカーと無制限のスペースを使用したワールドスケールの追跡。</span><span class="sxs-lookup"><span data-stu-id="2f355-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="2f355-112">[ストレージ API を固定](#anchors-and-anchor-persistence) して、HoloLens 2 ローカルストレージにアンカーを保持します。</span><span class="sxs-lookup"><span data-stu-id="2f355-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="2f355-113">新しい HP リバーブ G2 コントローラーを含む、[モーションコントローラーと手作業のやり取り](#motion-controller-and-hand-interactions)。</span><span class="sxs-lookup"><span data-stu-id="2f355-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="2f355-114">26個の関節と結合半径の入力を使用した、トレーラーを使用したハンドトラッキング。</span><span class="sxs-lookup"><span data-stu-id="2f355-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="2f355-115">HoloLens 2 での視線の相互作用。</span><span class="sxs-lookup"><span data-stu-id="2f355-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="2f355-116">HoloLens 2 で写真/ビデオ (PV) カメラを検索しています。</span><span class="sxs-lookup"><span data-stu-id="2f355-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="2f355-117">PV カメラを使用した第3目のレンダリングを使用した Mixed Reality キャプチャ。</span><span class="sxs-lookup"><span data-stu-id="2f355-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="2f355-118">[Holographic リモート処理アプリでの HoloLens 2 への "Play" を](#holographic-remoting-in-unity-editor-play-mode)サポートします。これにより、開発者は、デバイスにビルドしてデプロイすることなく、スクリプトをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="2f355-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="2f355-119">Mrtk Unity 2.5.2 から MRTK OpenXR adapter パッケージに準拠しています。</span><span class="sxs-lookup"><span data-stu-id="2f355-119">Compatible with MRTK Unity 2.5.2 through MRTK OpenXR adapter package.</span></span> <missing link>
* <span data-ttu-id="2f355-120">Unity [Arfoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) 以降との互換性</span><span class="sxs-lookup"><span data-stu-id="2f355-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later</span></span>

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="2f355-121">Unity エディター再生モードでの Holographic リモート処理</span><span class="sxs-lookup"><span data-stu-id="2f355-121">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="2f355-122">Visual Studio プロジェクトで UWP Unity プロジェクトをビルドしてから、パッケージ化して HoloLens 2 デバイスに配置すると、時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="2f355-122">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="2f355-123">1つの解決策は、Holographic エディターのリモート処理を有効にすることです。これにより、ネットワーク上の HoloLens 2 デバイスに対して "Play" モードで直接 C# スクリプトをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="2f355-123">One solution is to enable the Holographic Editor Remoting, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="2f355-124">このシナリオでは、UWP パッケージをビルドしてリモートデバイスに配置するオーバーヘッドを回避します。</span><span class="sxs-lookup"><span data-stu-id="2f355-124">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="2f355-125">まず、HoloLens 2 のストアから [Holographic Remoting Player アプリをインストール](https://www.microsoft.com/store/productId/9NBLGGH4SV40) する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f355-125">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from Store on your HoloLens 2</span></span>  
2. <span data-ttu-id="2f355-126">HoloLens 2 で Holographic リモート処理プレーヤーアプリを実行すると、接続先のバージョン番号と IP アドレスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f355-126">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="2f355-127">OpenXR プラグインを使用するには、v2.0 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="2f355-127">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

![HoloLens で実行されている Holographic リモート処理プレーヤーのスクリーンショット](images/openxr-features-img-01.png)

3. <span data-ttu-id="2f355-129">[ **編集-> プロジェクトの設定**] を開き、 **XR プラグイン管理** に移動して、[ **Windows Mixed Reality] 機能セット** ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="2f355-129">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

![XR プラグイン管理が強調表示されている Unity エディターで開いているプロジェクト設定パネルのスクリーンショット](images/openxr-features-img-02.png)

4. <span data-ttu-id="2f355-131">**OpenXR** の [**機能**] セクションを展開し、[**すべて表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2f355-131">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
5. <span data-ttu-id="2f355-132">[ **Holographic エディターリモート処理** ] チェックボックスをオンにして、Holographic リモート処理アプリから取得した IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="2f355-132">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

![機能が強調表示されている Unity エディターでプロジェクト設定パネルが開いているスクリーンショット](images/openxr-features-img-03.png)

<span data-ttu-id="2f355-134">これで、[Play] \ (再生 \) ボタンをクリックして、HoloLens の Holographic リモート処理アプリで Unity アプリを再生できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="2f355-134">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="2f355-135">また、 [Visual Studio を Unity にアタッチ](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) して、C# スクリプトを再生モードでデバッグすることもできます。</span><span class="sxs-lookup"><span data-stu-id="2f355-135">You can also [attach Visual Studio to Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="2f355-136">0.1.0 のバージョンでは、Holographic リモート処理ではアンカー機能がサポートされておらず、ARAnchorManager 機能はリモート処理では機能しません。</span><span class="sxs-lookup"><span data-stu-id="2f355-136">As of version 0.1.0 the Holographic Remoting, runtime doesn’t support Anchor feature, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="2f355-137">この機能は今後のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="2f355-137">This feature is coming in future releases.</span></span>

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="2f355-138">アンカーとアンカーの永続化</span><span class="sxs-lookup"><span data-stu-id="2f355-138">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="2f355-139">Mixed Reality OpenXR プラグインは、Unity の ARFoundation **ARAnchorManager** の実装を通じて基本的なアンカー機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="2f355-139">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="2f355-140">Aranchor の **基本につい** ては、ARANCHOR の [AR アンカーマネージャーのマニュアル](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f355-140">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="2f355-141">バージョン0.1.0 以降では、このプラグインは、プレーンにアタッチされたアンカーを作成する以外のすべての ARAnchorManager 機能をサポートしています。これは将来のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="2f355-141">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="2f355-142">固定の永続性と XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="2f355-142">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="2f355-143">**XRAnchorStore** と呼ばれる追加の API を使用すると、セッション間でアンカーを永続化できます。</span><span class="sxs-lookup"><span data-stu-id="2f355-143">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="2f355-144">XRAnchorStore は、デバイスに保存されているアンカーの表現です。</span><span class="sxs-lookup"><span data-stu-id="2f355-144">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="2f355-145">アンカーは、Unity シーンの **Aranchors** から永続化したり、ストレージから新しい **aranchors** に読み込んだり、ストレージから削除したりできます。</span><span class="sxs-lookup"><span data-stu-id="2f355-145">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="2f355-146">これらのアンカーは保存され、同じデバイスに読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="2f355-146">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="2f355-147">デバイス間のアンカーストレージは、今後のリリースで Azure 空間アンカーを通じてサポートされます。</span><span class="sxs-lookup"><span data-stu-id="2f355-147">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the 
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if 
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="2f355-148">XRAnchorStore を読み込むには、プラグインを使用して、XRAnchorSubsystem のサブシステムである ARAnchorManager の拡張メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="2f355-148">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="2f355-149">この拡張メソッドを使用するには、次のように ARAnchorManager のサブシステムからアクセスします。</span><span class="sxs-lookup"><span data-stu-id="2f355-149">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>
 
``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>(); 
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync(); 
```

<span data-ttu-id="2f355-150">アンカー > を永続化または非永続化する完全な例については、「 [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples)」の「AnchorsSample.cs script and script」 (アンカーとアンカーの例) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2f355-150">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![[階層] パネルのスクリーンショット (アンカーのサンプルが強調表示された状態で、Unity エディターで開きます)](images/openxr-features-img-04.png)

![[インスペクター] サンプルスクリプトが強調表示された状態で、Unity エディターで開いているインスペクターパネルのスクリーンショット](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="2f355-153">モーションコントローラーとハンド作用</span><span class="sxs-lookup"><span data-stu-id="2f355-153">Motion controller and hand interactions</span></span>

<span data-ttu-id="2f355-154">Unity での mixed reality の相互作用の基本については、unity の unity の [XR 入力](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f355-154">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="2f355-155">この Unity ドキュメントでは、コントローラー固有の入力から、より汎化された **Inputfeatureusage** へのマッピング、使用可能な XR 入力を識別および分類する方法、これらの入力からデータを読み取る方法などについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2f355-155">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span> 
 
<span data-ttu-id="2f355-156">Mixed Reality OpenXR プラグインは、次に示すように、標準 **Inputfeatureusage** にマップされた追加の入力相互作用プロファイルを提供します。</span><span class="sxs-lookup"><span data-stu-id="2f355-156">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span> 
 
| <span data-ttu-id="2f355-157">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="2f355-157">InputFeatureUsage</span></span> | <span data-ttu-id="2f355-158">HP リバーブ G2 コントローラー (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="2f355-158">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="2f355-159">HoloLens (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="2f355-159">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="2f355-160">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="2f355-160">primary2DAxis</span></span> | <span data-ttu-id="2f355-161">ジョイ</span><span class="sxs-lookup"><span data-stu-id="2f355-161">Joystick</span></span> | |
| <span data-ttu-id="2f355-162">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="2f355-162">primary2DAxisClick</span></span> | <span data-ttu-id="2f355-163">ジョイスティック-クリック</span><span class="sxs-lookup"><span data-stu-id="2f355-163">Joystick - Click</span></span> | |
| <span data-ttu-id="2f355-164">トリガー (trigger)</span><span class="sxs-lookup"><span data-stu-id="2f355-164">trigger</span></span> | <span data-ttu-id="2f355-165">トリガー</span><span class="sxs-lookup"><span data-stu-id="2f355-165">Trigger</span></span>  | |
| <span data-ttu-id="2f355-166">把握</span><span class="sxs-lookup"><span data-stu-id="2f355-166">grip</span></span> | <span data-ttu-id="2f355-167">把握</span><span class="sxs-lookup"><span data-stu-id="2f355-167">Grip</span></span> | <span data-ttu-id="2f355-168">エアタップまたはつかみ</span><span class="sxs-lookup"><span data-stu-id="2f355-168">Air tap or squeeze</span></span> |
| <span data-ttu-id="2f355-169">primaryButton</span><span class="sxs-lookup"><span data-stu-id="2f355-169">primaryButton</span></span> | <span data-ttu-id="2f355-170">[X/A]-押します</span><span class="sxs-lookup"><span data-stu-id="2f355-170">[X/A] - Press</span></span> | <span data-ttu-id="2f355-171">エアタップ</span><span class="sxs-lookup"><span data-stu-id="2f355-171">Air tap</span></span> |
| <span data-ttu-id="2f355-172">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="2f355-172">secondaryButton</span></span> | <span data-ttu-id="2f355-173">[Y/B]-押します</span><span class="sxs-lookup"><span data-stu-id="2f355-173">[Y/B] - Press</span></span> | |
| <span data-ttu-id="2f355-174">gripButton</span><span class="sxs-lookup"><span data-stu-id="2f355-174">gripButton</span></span> | <span data-ttu-id="2f355-175">グリップ-押す</span><span class="sxs-lookup"><span data-stu-id="2f355-175">Grip - Press</span></span> | |
| <span data-ttu-id="2f355-176">triggerButton</span><span class="sxs-lookup"><span data-stu-id="2f355-176">triggerButton</span></span> | <span data-ttu-id="2f355-177">トリガー-押す</span><span class="sxs-lookup"><span data-stu-id="2f355-177">Trigger - Press</span></span> | |
| <span data-ttu-id="2f355-178">menuButton</span><span class="sxs-lookup"><span data-stu-id="2f355-178">menuButton</span></span> | <span data-ttu-id="2f355-179">メニュー</span><span class="sxs-lookup"><span data-stu-id="2f355-179">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="2f355-180">目標とグリップ</span><span class="sxs-lookup"><span data-stu-id="2f355-180">Aim and Grip Poses</span></span>

<span data-ttu-id="2f355-181">OpenXR の入力相互作用を通じて、2組のポーズにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2f355-181">You have access to two sets of poses through OpenXR input interactions:</span></span> 
* <span data-ttu-id="2f355-182">手の形でオブジェクトをレンダリングするためのグリップ</span><span class="sxs-lookup"><span data-stu-id="2f355-182">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="2f355-183">目標は、世界を指します。</span><span class="sxs-lookup"><span data-stu-id="2f355-183">The aim poses for pointing into the world.</span></span> 

<span data-ttu-id="2f355-184">この設計の詳細と、2つの方法の違いについては、「 [OpenXR Specification-Input サブパス](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f355-184">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="2f355-185">InputFeatureUsages **Deviceposition**、 **Devicerotation**、 **devicevelocに** よって指定されたポーズ、およびすべてが OpenXR **グリップ** を表します。</span><span class="sxs-lookup"><span data-stu-id="2f355-185">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="2f355-186">グリップの設定に関連する InputFeatureUsages は、Unity の [commonusages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)で定義されています。</span><span class="sxs-lookup"><span data-stu-id="2f355-186">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="2f355-187">InputFeatureUsages **ポインター** によって提供されるポーズ、 **ポインターローテーション**、 **ポインター速度**、および **PointerAngularVelocity** all は、OpenXR **aim** を表します。</span><span class="sxs-lookup"><span data-stu-id="2f355-187">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="2f355-188">これらの InputFeatureUsages はインクルードされているすべての C# ファイルで定義されていないため、次のように独自の InputFeatureUsages を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f355-188">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="2f355-189">Haptics</span><span class="sxs-lookup"><span data-stu-id="2f355-189">Haptics</span></span>

<span data-ttu-id="2f355-190">Unity の XR 入力システムで haptics を使用する方法の詳細については、unity の unity [マニュアルの「UNITY XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f355-190">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span> 

## <a name="whats-coming-soon"></a><span data-ttu-id="2f355-191">近日公開予定</span><span class="sxs-lookup"><span data-stu-id="2f355-191">What's coming soon</span></span>

<span data-ttu-id="2f355-192">次の問題および不足している機能は、Mixed Reality OpenXR プラグイン **バージョン 0.1.0** で知られています。</span><span class="sxs-lookup"><span data-stu-id="2f355-192">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="2f355-193">これらの機能については、今後のリリースで修正と新機能をリリースする予定です。</span><span class="sxs-lookup"><span data-stu-id="2f355-193">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="2f355-194">**ARPlaneSubsystem** はまだサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2f355-194">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="2f355-195">HoloLens 2 では、 **Arplan emanager**、 **ARRaycastManager**、および ARANCHORMANAGER などの関連 API もサポートされていません **。**</span><span class="sxs-lookup"><span data-stu-id="2f355-195">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="2f355-196">**アンカー** は Holographic リモート処理ではまだサポートされていませんが、近い将来に登場します。</span><span class="sxs-lookup"><span data-stu-id="2f355-196">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="2f355-197">**手動メッシュ** 追跡、 **QR コード**、 **XRMeshSubsystem** はまだサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="2f355-197">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="2f355-198">**Azure 空間アンカー** のサポートは、今後のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="2f355-198">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="2f355-199">**ARM64** は、HoloLens 2 アプリで唯一サポートされているプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="2f355-199">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="2f355-200">**ARM** プラットフォームは今後のリリースで予定されています。</span><span class="sxs-lookup"><span data-stu-id="2f355-200">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="2f355-201">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="2f355-201">Troubleshooting</span></span> 

<span data-ttu-id="2f355-202">HoloLens 2 で Unity アプリを中断および再開すると、アプリは正しく再開できなくなります。これにより、HoloLens ビューでは、4つのスピン点が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2f355-202">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span> 
* <span data-ttu-id="2f355-203">回避策として、OpenXR プロジェクト設定で [ **深さの送信モード** ] を **[なし** ] に設定します。</span><span class="sxs-lookup"><span data-stu-id="2f355-203">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
