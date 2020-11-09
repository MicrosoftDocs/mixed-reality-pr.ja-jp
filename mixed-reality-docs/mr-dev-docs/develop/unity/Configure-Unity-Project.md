---
title: Windows Mixed Reality 用の新しい Unity プロジェクトを構成する
description: Windows Mixed Reality の Unity プロジェクトを構成する手順
author: thetuvix
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity, mixed reality, 開発, 作業の開始, 新しいプロジェクト
ms.openlocfilehash: f1465dcb31718b9d3faeb64d24e33d9f9ffeb7cc
ms.sourcegitcommit: 83c9373fe5b2e07cdab921b6cab3fdd418307003
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2020
ms.locfileid: "94386218"
---
# <a name="configure-a-new-unity-project-for-windows-mixed-reality"></a><span data-ttu-id="b2a9f-104">Windows Mixed Reality 用の新しい Unity プロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="b2a9f-104">Configure a New Unity project for Windows Mixed Reality</span></span> 

## <a name="overview"></a><span data-ttu-id="b2a9f-105">概要</span><span class="sxs-lookup"><span data-stu-id="b2a9f-105">Overview</span></span>

<span data-ttu-id="b2a9f-106">Windows Mixed Reality (WMR) は、Windows 10 オペレーティングシステムの一部として導入された Microsoft プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-106">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="b2a9f-107">WMR プラットフォームを使用すると、holographic および VR 表示デバイスでデジタルコンテンツをレンダリングするアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-107">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="b2a9f-108">WMR の設定時に実行できるパスは2つあります。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-108">When setting up for WMR, there are two paths you can take.</span></span> <span data-ttu-id="b2a9f-109">最初のオプションとして、 [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)をインストールします。これにより、wmr 環境が自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-109">Your first option is to install the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html), which will automatically set up the WMR environment.</span></span> <span data-ttu-id="b2a9f-110">2つ目のオプションは、いくつかの Unity 設定を手動で変更して、WMR をロールします。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-110">The second option is to manually change a few Unity settings to get rolling with WMR.</span></span> 

> [!NOTE]
> <span data-ttu-id="b2a9f-111">MRTK は、後でいつでもインポートできます。そのため、最初に手動による処理による影響はありません。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-111">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="b2a9f-112">WMR 手動セットアップを選択した場合、変更する必要がある設定は、プロジェクトごととシーン単位の2つのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-112">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="b2a9f-113">プロジェクトごとの設定</span><span class="sxs-lookup"><span data-stu-id="b2a9f-113">Per-project settings</span></span>

<span data-ttu-id="b2a9f-114">WMR の最初の設定を変更する必要があるのは、プロジェクトプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-114">The first setting you need to change for WMR is the project platform:</span></span> 
1. <span data-ttu-id="b2a9f-115">**ファイル > ビルド設定** を選択してください...</span><span class="sxs-lookup"><span data-stu-id="b2a9f-115">Select **File > Build Settings...**</span></span>
2. <span data-ttu-id="b2a9f-116">[プラットフォーム] ボックスの一覧の [ **ユニバーサル Windows プラットフォーム** を選択し、[ **プラットフォームの切り替え** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-116">Select **Universal Windows Platform** in the Platform list and click **Switch Platform**</span></span>
3. <span data-ttu-id="b2a9f-117">**SDK** を **Universal 10** に設定する</span><span class="sxs-lookup"><span data-stu-id="b2a9f-117">Set **SDK** to **Universal 10**</span></span>
4. <span data-ttu-id="b2a9f-118">イマーシブヘッドセットまたは **HoloLens** への切り替えをサポートするために、 **ターゲットデバイス** を **任意のデバイス** に設定する</span><span class="sxs-lookup"><span data-stu-id="b2a9f-118">Set **Target device** to **Any Device** to support immersive headsets or switch to **HoloLens**</span></span>
5. <span data-ttu-id="b2a9f-119">**ビルドの種類** を **D3D** に設定</span><span class="sxs-lookup"><span data-stu-id="b2a9f-119">Set **Build Type** to **D3D**</span></span>
6. <span data-ttu-id="b2a9f-120">**UWP SDK** を **最新のインストール** に設定する</span><span class="sxs-lookup"><span data-stu-id="b2a9f-120">Set **UWP SDK** to **Latest installed**</span></span>

<img src="images/unity-uwp-settings.png" width="550px" alt="Unity XR Settings">
<span data-ttu-id="b2a9f-121">*Unity XR の設定*</span><span class="sxs-lookup"><span data-stu-id="b2a9f-121">*Unity XR settings*</span></span>

<span data-ttu-id="b2a9f-122">プラットフォームが正しく構成されたら、アプリがエクスポート時に2D ビューではなく、 [イマーシブビュー](../../design/app-views.md) を作成する必要があることを Unity に知らせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-122">After the platform is configured correctly, you need to let Unity know that your app should create an [immersive view](../../design/app-views.md) instead of a 2D view when exported:</span></span>
1. <span data-ttu-id="b2a9f-123">[ **ビルドの設定...** ] ウィンドウで、[プレーヤーの **設定** ] を開きます。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-123">From the **Build Settings...** window, open **Player Settings...**</span></span>
2. <span data-ttu-id="b2a9f-124">ユニバーサル Windows プラットフォーム] タブ **の [設定** ] を選択し、[ **XR settings** ] グループを展開します。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-124">Select the **Settings for Universal Windows Platform** tab and expand the **XR Settings** group</span></span>
3. <span data-ttu-id="b2a9f-125">[ **XR の設定** ] セクションで、[ **仮想現実のサポート** ] チェックボックスをオンにして、[ **仮想現実のデバイス** ] の一覧を追加します。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-125">In the **XR Settings** section, check the **Virtual Reality Supported** checkbox to add the **Virtual Reality Devices** list.</span></span>
4. <span data-ttu-id="b2a9f-126">[ **XR 設定** ] グループで、 **"Windows Mixed Reality"** がサポートされているデバイスとして表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-126">In the **XR Settings** group, confirm that **"Windows Mixed Reality"** is listed as a supported device.</span></span> <span data-ttu-id="b2a9f-127">(このオプションは、旧バージョンの Unity では **Windows Holographic** として表示される場合があります)</span><span class="sxs-lookup"><span data-stu-id="b2a9f-127">(this option may appear as **Windows Holographic** in older versions of Unity)</span></span>

<span data-ttu-id="b2a9f-128">![Unity UWP の設定](images/xrsettings.png)</span><span class="sxs-lookup"><span data-stu-id="b2a9f-128">![Unity UWP settings](images/xrsettings.png)</span></span><br>
<span data-ttu-id="b2a9f-129">*Unity XR の設定*</span><span class="sxs-lookup"><span data-stu-id="b2a9f-129">*Unity XR settings*</span></span>

### <a name="updating-the-manifest"></a><span data-ttu-id="b2a9f-130">マニフェストを更新しています</span><span class="sxs-lookup"><span data-stu-id="b2a9f-130">Updating the manifest</span></span>

<span data-ttu-id="b2a9f-131">これで、アプリで holographic のレンダリングと空間入力を処理できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-131">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="b2a9f-132">ただし、アプリでは、特定の機能を利用するために、マニフェストで適切な機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-132">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="b2a9f-133">プロジェクト機能を検索するには、 **ユニバーサル Windows プラットフォーム > 発行設定 > 機能の > 設定** ] に移動します。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-133">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="b2a9f-134">エクスポートする今後のすべてのプロジェクトにマニフェスト宣言を含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-134">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="b2a9f-135">Mixed Reality で一般的に使用される Unity Api を有効にするための適用可能な機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-135">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="b2a9f-136">機能</span><span class="sxs-lookup"><span data-stu-id="b2a9f-136">Capability</span></span>  |  <span data-ttu-id="b2a9f-137">機能を必要とする Api</span><span class="sxs-lookup"><span data-stu-id="b2a9f-137">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="b2a9f-138">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="b2a9f-138">SpatialPerception</span></span>  |  <span data-ttu-id="b2a9f-139">SurfaceObserver (HoloLens 上の [空間マッピング](../../design/spatial-mapping.md)メッシュへのアクセス) &mdash; *ヘッドセットの一般的な空間追跡に必要な機能はありません*</span><span class="sxs-lookup"><span data-stu-id="b2a9f-139">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="b2a9f-140">WebCam</span><span class="sxs-lookup"><span data-stu-id="b2a9f-140">WebCam</span></span>  |  <span data-ttu-id="b2a9f-141">PhotoCapture と VideoCapture</span><span class="sxs-lookup"><span data-stu-id="b2a9f-141">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="b2a9f-142">PicturesLibrary / VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="b2a9f-142">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="b2a9f-143">PhotoCapture または VideoCapture (キャプチャされたコンテンツを格納する場合)</span><span class="sxs-lookup"><span data-stu-id="b2a9f-143">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="b2a9f-144">Microphone</span><span class="sxs-lookup"><span data-stu-id="b2a9f-144">Microphone</span></span>  |  <span data-ttu-id="b2a9f-145">VideoCapture (オーディオをキャプチャする場合)、DictationRecognizer、GrammarRecognizer、および KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="b2a9f-145">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="b2a9f-146">InternetClient</span><span class="sxs-lookup"><span data-stu-id="b2a9f-146">InternetClient</span></span>  |  <span data-ttu-id="b2a9f-147">DictationRecognizer (および Unity Profiler の使用)</span><span class="sxs-lookup"><span data-stu-id="b2a9f-147">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="b2a9f-148">品質設定</span><span class="sxs-lookup"><span data-stu-id="b2a9f-148">Quality settings</span></span>

<span data-ttu-id="b2a9f-149">HoloLens には、モバイルクラスの GPU があります。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-149">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="b2a9f-150">アプリが HoloLens を対象としている場合は、アプリの品質設定を最適なパフォーマンスのために調整して、完全なフレームレートを維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-150">If your app is targeting HoloLens, you'll want the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate:</span></span>
1. <span data-ttu-id="b2a9f-151">[ **プロジェクト設定の編集 > の > 品質** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-151">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="b2a9f-152">**Windows ストア** のロゴの下にある **ドロップダウン** を選択し、[ **非常に低い** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-152">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="b2a9f-153">[Windows Store]\(Windows ストア\) 列のボックスと **[Very Low]\(非常に低い\)** 行が緑色の場合、設定が適切に適用されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-153">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green.</span></span>

<span data-ttu-id="b2a9f-154">![Unity の品質設定](images/getting-started-unity-quality-settings.jpg)</span><span class="sxs-lookup"><span data-stu-id="b2a9f-154">![Unity quality settings](images/getting-started-unity-quality-settings.jpg)</span></span><br>
<span data-ttu-id="b2a9f-155">*Unity の品質設定*</span><span class="sxs-lookup"><span data-stu-id="b2a9f-155">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="b2a9f-156">シーンごとの設定</span><span class="sxs-lookup"><span data-stu-id="b2a9f-156">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="b2a9f-157">Unity カメラの設定</span><span class="sxs-lookup"><span data-stu-id="b2a9f-157">Unity camera settings</span></span>

<span data-ttu-id="b2a9f-158">[ **サポートされている仮想 Reality** ] チェックボックスをオンにすると、 [Unity カメラ](camera-in-unity.md) コンポーネントは [ヘッド追跡とステレオスコピックレンダリング](../platform-capabilities-and-apis/rendering.md)を処理します。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-158">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="b2a9f-159">つまり、メインのカメラオブジェクトをカスタムカメラに置き換える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-159">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="b2a9f-160">アプリが HoloLens を対象としている場合は、デバイスの透明ディスプレイを最適化するために、いくつかの設定を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-160">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="b2a9f-161">これらの設定により、holographic コンテンツが物理的な世界に表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-161">These settings allow your holographic content to show through to the physical world:</span></span>
1. <span data-ttu-id="b2a9f-162">**階層** で、 **メインカメラ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-162">In the **Hierarchy** , select the **Main Camera**</span></span>
2. <span data-ttu-id="b2a9f-163">[ **インスペクター** ] パネルで、[変換 **位置** ] を **0、0、0** に設定します。これにより、ユーザーのヘッドの位置が Unity の元の場所から開始されます。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-163">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="b2a9f-164">**クリアフラグ** を **純色** に変更します。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-164">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="b2a9f-165">**背景** 色を **RGBA 0、0、0、0** に変更します。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-165">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="b2a9f-166">ブラックは HoloLens では透明としてレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-166">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="b2a9f-167">**クリッププレーン** を [HoloLens の推奨](camera-in-unity.md#clip-planes)0.85 (メーター) に近い場所に変更します。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-167">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="b2a9f-168">![Unity カメラの設定](images/Unitycamerasettings.png)</span><span class="sxs-lookup"><span data-stu-id="b2a9f-168">![Unity camera settings](images/Unitycamerasettings.png)</span></span><br>
<span data-ttu-id="b2a9f-169">*Unity カメラの設定*</span><span class="sxs-lookup"><span data-stu-id="b2a9f-169">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b2a9f-170">新しいカメラを削除して作成する場合は、新しいカメラが **maincamera** としてタグ付けされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b2a9f-170">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2a9f-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2a9f-171">See also</span></span>
* [<span data-ttu-id="b2a9f-172">MRTK-インストールガイド (GitHub)</span><span class="sxs-lookup"><span data-stu-id="b2a9f-172">MRTK - Installation guide (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html)
* [<span data-ttu-id="b2a9f-173">MRTK-ドキュメントホーム (GitHub)</span><span class="sxs-lookup"><span data-stu-id="b2a9f-173">MRTK - Documentation home (GitHub)</span></span>](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [<span data-ttu-id="b2a9f-174">ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="b2a9f-174">Install the tools</span></span>](../install-the-tools.md)
* [<span data-ttu-id="b2a9f-175">Unity 開発の概要</span><span class="sxs-lookup"><span data-stu-id="b2a9f-175">Unity Development Overview</span></span>](unity-development-overview.md)
