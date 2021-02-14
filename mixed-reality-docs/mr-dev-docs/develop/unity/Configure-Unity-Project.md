---
title: MRTK を使用せずにプロジェクトを構成する
description: Mixed Reality Toolkit を使用せずに、Windows Mixed Reality 用の新しい Unity プロジェクトを構成する方法について説明します。
author: hferrone
ms.author: alexturn
ms.date: 07/29/2020
ms.topic: article
keywords: Unity、mixed reality、開発、作業の開始、新しいプロジェクト、Windows Mixed Reality、UWP、XR、パフォーマンス
ms.openlocfilehash: 6a9bc0d9a565de1d25e1906c439e39773cb99244
ms.sourcegitcommit: 029f247a6c33068360d3a06f2a473a12586017e1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2021
ms.locfileid: "100496080"
---
# <a name="configuring-your-project-without-mrtk"></a><span data-ttu-id="35729-104">MRTK を使用しないプロジェクトを構成する</span><span class="sxs-lookup"><span data-stu-id="35729-104">Configuring your project without MRTK</span></span>

<span data-ttu-id="35729-105">Windows Mixed Reality (WMR) は、Windows 10 オペレーティングシステムの一部として導入された Microsoft プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="35729-105">Windows Mixed Reality (WMR) is a Microsoft platform introduced as part of the Windows 10 operating system.</span></span> <span data-ttu-id="35729-106">WMR プラットフォームを使用すると、holographic および VR 表示デバイスでデジタルコンテンツをレンダリングするアプリケーションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="35729-106">The WMR platform lets you build applications that render digital content on holographic and VR display devices.</span></span>

<span data-ttu-id="35729-107">Microsoft とコミュニティは、wmr 環境を自動的に設定する [Mixed Reality Toolkit (mrtk)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) などのオープンソースツールを作成していますが、多くの開発者は、経験をゼロから構築することを望んでいます。</span><span class="sxs-lookup"><span data-stu-id="35729-107">While Microsoft and the community have created opensource tools such as the [Mixed Reality Toolkit (MRTK)](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Installation.html) that will automatically set up the WMR environment, many developers wish to build their experiences from the ground up.</span></span>  <span data-ttu-id="35729-108">次のドキュメントでは、MRTK を使用しているかどうかにかかわらず、Mixed Reality 開発用のプロジェクトを適切に設定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="35729-108">The following documentation will demonstrate how to properly set up a project for Mixed Reality development whether you are using MRTK or not.</span></span>  <span data-ttu-id="35729-109">変更が必要な設定は、プロジェクトごとの設定とシーンごとの設定という2つのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="35729-109">The settings you need to change are broken down into two categories: per-project settings and per-scene settings.</span></span>

> [!NOTE]
> <span data-ttu-id="35729-110">MRTK は、後でいつでもインポートできます。そのため、最初に手動による処理による影響はありません。</span><span class="sxs-lookup"><span data-stu-id="35729-110">You can always import MRTK later on, so there's no penalty for going the manual route first.</span></span>

<span data-ttu-id="35729-111">WMR 手動セットアップを選択した場合、変更する必要がある設定は、プロジェクトごととシーン単位の2つのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="35729-111">If you choose the WMR manual setup, the settings you need to change are broken-down into two categories: per-project and per-scene.</span></span>

## <a name="per-project-settings"></a><span data-ttu-id="35729-112">プロジェクトごとの設定</span><span class="sxs-lookup"><span data-stu-id="35729-112">Per-project settings</span></span>

<span data-ttu-id="35729-113">Desktop VR を対象としている場合は、新しい Unity プロジェクトで既定で選択されている PC スタンドアロンプラットフォームを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="35729-113">If you're targeting Desktop VR, we suggest using the PC Standalone Platform selected by default on a new Unity project:</span></span>

![[ビルドの設定] ウィンドウのスクリーンショット PC、Mac & スタンドアロンプラットフォームが強調表示されている unity エディターで開く](images/wmr-config-img-3.png)

<span data-ttu-id="35729-115">HoloLens 2 を対象としている場合は、ユニバーサル Windows プラットフォームに切り替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="35729-115">If you're targeting HoloLens 2, you need to switch to the Universal Windows Platform:</span></span>

1.  <span data-ttu-id="35729-116">**ファイル > ビルド設定** を選択してください...</span><span class="sxs-lookup"><span data-stu-id="35729-116">Select **File > Build Settings...**</span></span>
2.  <span data-ttu-id="35729-117">[プラットフォーム] ボックスの一覧で [**ユニバーサル Windows プラットフォーム** を選択し、[**プラットフォームの切り替え**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="35729-117">Select **Universal Windows Platform** in the Platform list and select **Switch Platform**</span></span>
3.  <span data-ttu-id="35729-118">**アーキテクチャ** を **ARM 64** に設定する</span><span class="sxs-lookup"><span data-stu-id="35729-118">Set **Architecture** to **ARM 64**</span></span>
4.  <span data-ttu-id="35729-119">**ターゲットデバイス** を **HoloLens** に設定する</span><span class="sxs-lookup"><span data-stu-id="35729-119">Set **Target device** to **HoloLens**</span></span>
5.  <span data-ttu-id="35729-120">**ビルドの種類** を **D3D** に設定</span><span class="sxs-lookup"><span data-stu-id="35729-120">Set **Build Type** to **D3D**</span></span>
6.  <span data-ttu-id="35729-121">**UWP SDK** を **最新のインストール** に設定する</span><span class="sxs-lookup"><span data-stu-id="35729-121">Set **UWP SDK** to **Latest installed**</span></span>
7.  <span data-ttu-id="35729-122">デバッグに関する既知のパフォーマンスの問題があるため、 **ビルド構成** を **リリース** に設定します</span><span class="sxs-lookup"><span data-stu-id="35729-122">Set **Build configuration** to **Release** because there are known performance issues with Debug</span></span>

![ユニバーサル Windows プラットフォーム強調表示された [ビルド設定] ウィンドウのスクリーンショット (unity エディターで開く)](images/wmr-config-img-4.png)

<span data-ttu-id="35729-124">プラットフォームを設定した後は、エクスポート時に2D ビューではなく、 [イマーシブビュー](../../design/app-views.md) を作成するよう Unity に知らせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="35729-124">After setting your platform, you need to let Unity know to create an [immersive view](../../design/app-views.md) instead of a 2D view when exported.</span></span>

### <a name="for-xrsdk"></a><span data-ttu-id="35729-125">XRSDK の場合</span><span class="sxs-lookup"><span data-stu-id="35729-125">For XRSDK</span></span> 

1. <span data-ttu-id="35729-126">Unity エディターで、[ **Edit > プロジェクトの設定**] に移動し、[ **XR Plugin Management** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="35729-126">In the Unity Editor, navigate to **Edit > Project settings** and select **XR Plugin Management**</span></span>

2. <span data-ttu-id="35729-127">[ **INSTALL XR Plugin Management** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="35729-127">Select **Install XR Plugin Management**</span></span>

![XR Plugin management が強調表示されている unity エディターで開き、[プロジェクトの設定] ウィンドウのスクリーンショット](images/wmr-config-img-5.png)

3. <span data-ttu-id="35729-129">[スタートアップと **Windows Mixed Reality** **で XR を初期化** する] を選択します。</span><span class="sxs-lookup"><span data-stu-id="35729-129">Select **Initialize XR on Startup** and **Windows Mixed Reality**</span></span>

![XR Plugin management が強調表示されている unity エディターで開き、[プロジェクトの設定] ウィンドウのスクリーンショット](images/wmr-config-img-7.png)

4. <span data-ttu-id="35729-131">[ **XR プラグイン管理**] セクションを展開し、[ **Windows Mixed Reality** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="35729-131">Expand the **XR Plug-in Management** section and select **Windows Mixed Reality**</span></span>
5. <span data-ttu-id="35729-132">すべてのチェックボックスをオンにし、**深さの送信モード** を **深さ16ビット** に設定します</span><span class="sxs-lookup"><span data-stu-id="35729-132">Check all boxes and set **Depth Submission Mode** to **Depth 16 Bit**</span></span>

![Windows Mixed Reality セクションが強調表示されている unity エディターで開いているプロジェクト設定ウィンドウのスクリーンショット](images/wmr-config-img-8.png)

### <a name="for-legacy-xr"></a><span data-ttu-id="35729-134">レガシ XR の場合</span><span class="sxs-lookup"><span data-stu-id="35729-134">For Legacy XR</span></span> 

> [!CAUTION]
> <span data-ttu-id="35729-135">従来の XR は Unity 2019 で非推奨とされ、Unity 2020 では削除されています。</span><span class="sxs-lookup"><span data-stu-id="35729-135">Legacy XR is deprecated in Unity 2019 and removed in Unity 2020.</span></span>

1. <span data-ttu-id="35729-136">ビルド設定から **プレーヤー設定** を開く... **ウィンドウ** を開き、 **XR 設定** グループを展開します。</span><span class="sxs-lookup"><span data-stu-id="35729-136">Open **Player Settings...** from the **Build Settings... window** and expand the **XR Settings** group</span></span>
2. <span data-ttu-id="35729-137">[ **XR の設定** ] セクションで、[virtual Reality のサポート] を選択し **て** 、仮想現実のデバイスの一覧を追加します。</span><span class="sxs-lookup"><span data-stu-id="35729-137">In the **XR Settings** section, select **Virtual Reality Supported** to add the Virtual Reality Devices list</span></span>
3. <span data-ttu-id="35729-138">**深さの形式** を **16 ビット深度** に設定し、**深度バッファーの共有** を有効にします</span><span class="sxs-lookup"><span data-stu-id="35729-138">Set **Depth Format** to **16-bit Depth** and enable **Depth Buffer Sharing**</span></span>
4. <span data-ttu-id="35729-139">**ステレオレンダリングモード** を **シングルパスインスタンス** に設定する</span><span class="sxs-lookup"><span data-stu-id="35729-139">Set **Stereo Rendering Mode** to **Single Pass Instance**</span></span>
5. <span data-ttu-id="35729-140">Holographic リモート処理を使用する場合は、[ **WSA Holographic リモート処理がサポートされてい** ます] を選択します。</span><span class="sxs-lookup"><span data-stu-id="35729-140">Select **WSA Holographic Remoting Supported** if you'd like to use Holographic remoting</span></span> 

![[プレーヤーの設定] セクションが強調表示されている unity エディターで開いているプロジェクト設定ウィンドウのスクリーンショット](images/wmr-config-img-9.png)

### <a name="updating-the-manifest"></a><span data-ttu-id="35729-142">マニフェストを更新しています</span><span class="sxs-lookup"><span data-stu-id="35729-142">Updating the manifest</span></span>

<span data-ttu-id="35729-143">これで、アプリで holographic のレンダリングと空間入力を処理できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="35729-143">Your app can now handle holographic rendering and spatial input.</span></span> <span data-ttu-id="35729-144">ただし、アプリでは、特定の機能を利用するために、マニフェストで適切な機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35729-144">However, your app needs to declare the appropriate capabilities in its manifest to take advantage of certain functionality.</span></span> <span data-ttu-id="35729-145">プロジェクト機能を検索するには、 **ユニバーサル Windows プラットフォーム > 発行設定 > 機能の > 設定**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="35729-145">You can find your projects capabilities by going to **Player Settings > Settings for Universal Windows Platform > Publishing Settings > Capabilities**.</span></span> 

<span data-ttu-id="35729-146">エクスポートする今後のすべてのプロジェクトにマニフェスト宣言を含めることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="35729-146">It's recommended that you make the manifest declarations in Unity to include them in all future projects that you export.</span></span> <span data-ttu-id="35729-147">Mixed Reality で一般的に使用される Unity Api を有効にするための適用可能な機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="35729-147">The applicable capabilities for enabling commonly used Unity APIs for Mixed Reality are:</span></span>

|  <span data-ttu-id="35729-148">機能</span><span class="sxs-lookup"><span data-stu-id="35729-148">Capability</span></span>  |  <span data-ttu-id="35729-149">機能を必要とする Api</span><span class="sxs-lookup"><span data-stu-id="35729-149">APIs requiring capability</span></span> | 
|----------|----------|
|  <span data-ttu-id="35729-150">SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="35729-150">SpatialPerception</span></span>  |  <span data-ttu-id="35729-151">SurfaceObserver (HoloLens 上の [空間マッピング](../../design/spatial-mapping.md)メッシュへのアクセス) &mdash; *ヘッドセットの一般的な空間追跡に必要な機能はありません*</span><span class="sxs-lookup"><span data-stu-id="35729-151">SurfaceObserver (access to [spatial mapping](../../design/spatial-mapping.md) meshes on HoloLens)&mdash;*No capability needed for general spatial tracking of the headset*</span></span> | 
|  <span data-ttu-id="35729-152">WebCam</span><span class="sxs-lookup"><span data-stu-id="35729-152">WebCam</span></span>  |  <span data-ttu-id="35729-153">PhotoCapture と VideoCapture</span><span class="sxs-lookup"><span data-stu-id="35729-153">PhotoCapture and VideoCapture</span></span> | 
|  <span data-ttu-id="35729-154">PicturesLibrary / VideosLibrary</span><span class="sxs-lookup"><span data-stu-id="35729-154">PicturesLibrary / VideosLibrary</span></span>  |  <span data-ttu-id="35729-155">PhotoCapture または VideoCapture (キャプチャされたコンテンツを格納する場合)</span><span class="sxs-lookup"><span data-stu-id="35729-155">PhotoCapture or VideoCapture, respectively (when storing the captured content)</span></span> | 
|  <span data-ttu-id="35729-156">マイク</span><span class="sxs-lookup"><span data-stu-id="35729-156">Microphone</span></span>  |  <span data-ttu-id="35729-157">VideoCapture (オーディオをキャプチャする場合)、DictationRecognizer、GrammarRecognizer、および KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="35729-157">VideoCapture (when capturing audio), DictationRecognizer, GrammarRecognizer, and KeywordRecognizer</span></span> | 
|  <span data-ttu-id="35729-158">InternetClient</span><span class="sxs-lookup"><span data-stu-id="35729-158">InternetClient</span></span>  |  <span data-ttu-id="35729-159">DictationRecognizer (および Unity Profiler の使用)</span><span class="sxs-lookup"><span data-stu-id="35729-159">DictationRecognizer (and to use the Unity Profiler)</span></span> | 

### <a name="quality-settings"></a><span data-ttu-id="35729-160">品質設定</span><span class="sxs-lookup"><span data-stu-id="35729-160">Quality settings</span></span>

<span data-ttu-id="35729-161">HoloLens には、モバイルクラスの GPU があります。</span><span class="sxs-lookup"><span data-stu-id="35729-161">HoloLens has a mobile-class GPU.</span></span> <span data-ttu-id="35729-162">アプリが HoloLens を対象としている場合は、アプリの品質設定を最適なパフォーマンスのために調整して、完全なフレームレートを維持する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35729-162">If your app is targeting HoloLens, you'll want the quality settings in your app tuned for fastest performance to ensure it maintains full frame-rate:</span></span>

1. <span data-ttu-id="35729-163">[**プロジェクト設定の編集 > の > 品質**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="35729-163">Select **Edit > Project Settings > Quality**</span></span>
2. <span data-ttu-id="35729-164">**Windows ストア** のロゴの下にある **ドロップダウン** を選択し、[**非常に低い**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="35729-164">Select the **dropdown** under the **Windows Store** logo and select **Very Low**.</span></span> <span data-ttu-id="35729-165">Windows ストアの列のボックスと **非常に少ない** 行が緑色になっていると、設定が正しく適用されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="35729-165">You'll know the setting is applied correctly when the box in the Windows Store column and **Very Low** row is green</span></span>
3. <span data-ttu-id="35729-166">[**影**] セクションで、[**影を無効にする**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="35729-166">In the **Shadows** section, select **Disable Shadows**</span></span>

<span data-ttu-id="35729-167">![[品質設定] セクションが強調表示されている unity エディターで開いているプロジェクト設定ウィンドウのスクリーンショット](images/wmr-config-img-10.png)</span><span class="sxs-lookup"><span data-stu-id="35729-167">![Screenshot of Project settings window open in unity editor with quality settings section highlighted](images/wmr-config-img-10.png)</span></span><br>
<span data-ttu-id="35729-168">*Unity の品質設定*</span><span class="sxs-lookup"><span data-stu-id="35729-168">*Unity quality settings*</span></span>

## <a name="per-scene-settings"></a><span data-ttu-id="35729-169">シーンごとの設定</span><span class="sxs-lookup"><span data-stu-id="35729-169">Per-scene settings</span></span>

### <a name="unity-camera-settings"></a><span data-ttu-id="35729-170">Unity カメラの設定</span><span class="sxs-lookup"><span data-stu-id="35729-170">Unity camera settings</span></span>

<span data-ttu-id="35729-171">[ **サポートされている仮想 Reality** ] チェックボックスをオンにすると、 [Unity カメラ](camera-in-unity.md) コンポーネントは [ヘッド追跡とステレオスコピックレンダリング](../platform-capabilities-and-apis/rendering.md)を処理します。</span><span class="sxs-lookup"><span data-stu-id="35729-171">With **Virtual Reality Supported** checked, the [Unity Camera](camera-in-unity.md) component handles [head tracking and stereoscopic rendering](../platform-capabilities-and-apis/rendering.md).</span></span> <span data-ttu-id="35729-172">つまり、メインのカメラオブジェクトをカスタムカメラに置き換える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="35729-172">That means there's no need for you to replace the Main Camera object with a custom camera.</span></span>

<span data-ttu-id="35729-173">アプリが HoloLens を対象としている場合は、デバイスの透明ディスプレイを最適化するために、いくつかの設定を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="35729-173">If your app is targeting HoloLens specifically, you need to change a few settings to optimize for the device's transparent displays.</span></span> <span data-ttu-id="35729-174">これらの設定により、holographic コンテンツが物理的な世界に表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="35729-174">These settings allow your holographic content to show through to the physical world:</span></span>

1. <span data-ttu-id="35729-175">**階層** で、**メインカメラ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="35729-175">In the **Hierarchy**, select the **Main Camera**</span></span>
2. <span data-ttu-id="35729-176">[ **インスペクター** ] パネルで、[変換 **位置** ] を **0、0、0** に設定します。これにより、ユーザーのヘッドの位置が Unity の元の場所から開始されます。</span><span class="sxs-lookup"><span data-stu-id="35729-176">In the **Inspector** panel, set the transform **position** to **0, 0, 0** so the location of the user's head starts at the Unity world origin.</span></span>
3. <span data-ttu-id="35729-177">**クリアフラグ** を **純色** に変更します。</span><span class="sxs-lookup"><span data-stu-id="35729-177">Change **Clear Flags** to **Solid Color**.</span></span>
4. <span data-ttu-id="35729-178">**背景** 色を **RGBA 0、0、0、0** に変更します。</span><span class="sxs-lookup"><span data-stu-id="35729-178">Change the **Background** color to **RGBA 0,0,0,0**.</span></span> <span data-ttu-id="35729-179">ブラックは HoloLens では透明としてレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="35729-179">Black renders as transparent in HoloLens.</span></span>
5. <span data-ttu-id="35729-180">**クリッププレーン** を [HoloLens の推奨](camera-in-unity.md#clip-planes)0.85 (メーター) に近い場所に変更します。</span><span class="sxs-lookup"><span data-stu-id="35729-180">Change **Clipping Planes - Near** to the [HoloLens recommended](camera-in-unity.md#clip-planes) 0.85 (meters).</span></span>

<span data-ttu-id="35729-181">![Unity エディターで開いている [インスペクター] タブのスクリーンショット](images/wmr-config-img-11.png)</span><span class="sxs-lookup"><span data-stu-id="35729-181">![Screenshot of the inspector tab open in the Unity editor](images/wmr-config-img-11.png)</span></span><br>
<span data-ttu-id="35729-182">*Unity カメラの設定*</span><span class="sxs-lookup"><span data-stu-id="35729-182">*Unity camera settings*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="35729-183">新しいカメラを削除して作成する場合は、新しいカメラが **maincamera** としてタグ付けされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="35729-183">If you delete and create a new camera, make sure your new camera is tagged as **MainCamera**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="35729-184">次のステップ</span><span class="sxs-lookup"><span data-stu-id="35729-184">Next steps</span></span>

<span data-ttu-id="35729-185">プロジェクトの準備ができたので、次のように Mixed Reality エクスペリエンスの開発を開始できます。</span><span class="sxs-lookup"><span data-stu-id="35729-185">Now that your project is ready, you can start developing your Mixed Reality experience:</span></span>

* <span data-ttu-id="35729-186">[コア構成要素](unity-development-overview.md#2-core-building-blocks)の追加</span><span class="sxs-lookup"><span data-stu-id="35729-186">Add [core building blocks](unity-development-overview.md#2-core-building-blocks)</span></span>
* <span data-ttu-id="35729-187">使用可能な[プラットフォーム機能と api を](unity-development-overview.md#3-advanced-features)確認する</span><span class="sxs-lookup"><span data-stu-id="35729-187">Check out available [platform capabilities and APIs](unity-development-overview.md#3-advanced-features)</span></span>
* <span data-ttu-id="35729-188">[アプリをデプロイ](../platform-capabilities-and-apis/using-visual-studio.md#)する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="35729-188">Learn how to [deploy your app](../platform-capabilities-and-apis/using-visual-studio.md#)</span></span>
* <span data-ttu-id="35729-189">[Mixed Reality シミュレーター](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)を使用する</span><span class="sxs-lookup"><span data-stu-id="35729-189">Use the [Mixed Reality simulator](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="35729-190">関連項目</span><span class="sxs-lookup"><span data-stu-id="35729-190">See also</span></span>
* [<span data-ttu-id="35729-191">ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="35729-191">Install the tools</span></span>](../install-the-tools.md)