---
title: ビデオからオーディオの立体化
description: ビデオ資産を Unity mixed reality プロジェクトにインポートし、ビデオからオーディオを spatialize する方法について説明します。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、ヘッド関連の転送機能、リバーブ、Microsoft Spatializer、ビデオのインポート、ビデオプレーヤー
ms.openlocfilehash: 211d1e32a8137444d0f33d442a60067dcd77ca36
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007413"
---
# <a name="spatializing-audio-from-a-video"></a><span data-ttu-id="50144-104">ビデオからオーディオの立体化</span><span class="sxs-lookup"><span data-stu-id="50144-104">Spatializing audio from a video</span></span>

<span data-ttu-id="50144-105">HoloLens 2 Unity チュートリアルの空間オーディオモジュールの第3章では、次のことを行います。</span><span class="sxs-lookup"><span data-stu-id="50144-105">In this 3rd chapter of the spatial audio module of the HoloLens 2 Unity tutorials, you'll:</span></span>
* <span data-ttu-id="50144-106">ビデオをインポートしてビデオプレーヤーを追加する</span><span class="sxs-lookup"><span data-stu-id="50144-106">Import a video and add a Video Player</span></span>
* <span data-ttu-id="50144-107">ビデオを quadrangle に再生する</span><span class="sxs-lookup"><span data-stu-id="50144-107">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="50144-108">オーディオをビデオから quadrangle にルーティングし、オーディオを spatialize する</span><span class="sxs-lookup"><span data-stu-id="50144-108">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player"></a><span data-ttu-id="50144-109">ビデオをインポートしてビデオプレーヤーを追加する</span><span class="sxs-lookup"><span data-stu-id="50144-109">Import a video and add a Video Player</span></span>

<span data-ttu-id="50144-110">Unity プロジェクトの **プロジェクト** ウィンドウにビデオファイルをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="50144-110">Drag a video file into the **Project** pane in your Unity project.</span></span> <span data-ttu-id="50144-111">[このビデオ](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true)は、空間オーディオサンプルプロジェクトから使用できます。</span><span class="sxs-lookup"><span data-stu-id="50144-111">You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

![ビデオを含む Assets フォルダー](images/spatial-audio/assets-folder-with-video.png)

<span data-ttu-id="50144-113">ビデオクリップの品質設定を調整すると、HoloLens 2 でスムーズに再生されるようになります。</span><span class="sxs-lookup"><span data-stu-id="50144-113">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="50144-114">**プロジェクト** ウィンドウでビデオファイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="50144-114">Click on the video file in the **Project** pane.</span></span> <span data-ttu-id="50144-115">次に、ビデオファイルの [ **インスペクター** ] ウィンドウで、Windows ストアアプリの設定を上書きし、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="50144-115">Then in the **Inspector** pane for the video file, override the settings for Windows Store Apps, and:</span></span>
* <span data-ttu-id="50144-116">**トランスコード** を有効にする</span><span class="sxs-lookup"><span data-stu-id="50144-116">Enable **Transcode**</span></span>
* <span data-ttu-id="50144-117">**コーデック** を H264 に設定する</span><span class="sxs-lookup"><span data-stu-id="50144-117">Set **Codec** to H264</span></span>
* <span data-ttu-id="50144-118">**ビットレートモード** を低に設定</span><span class="sxs-lookup"><span data-stu-id="50144-118">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="50144-119">**空間品質** を中程度に設定する</span><span class="sxs-lookup"><span data-stu-id="50144-119">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="50144-120">これらの調整が完了すると、ビデオファイルの [ **インスペクター** ] ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="50144-120">After these adjustments, the **Inspector** pane for the video file will look like this:</span></span>

![ビデオのプロパティウィンドウ](images/spatial-audio/video-property-pane.png)

<span data-ttu-id="50144-122">次に、[**階層**] ウィンドウを右クリックし、[**ビデオ > ビデオプレーヤー**] を選択して、**階層** に **video player** オブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="50144-122">Next, add a **Video Player** object to the **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **Video -> Video Player**:</span></span>

![階層内のビデオプレーヤー](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="50144-124">ビデオを quadrangle に再生する</span><span class="sxs-lookup"><span data-stu-id="50144-124">Play video onto a quadrangle</span></span>

<span data-ttu-id="50144-125">**Video Player** オブジェクトには、ビデオをレンダリングするためのテクスチャを使用するゲームオブジェクトが必要です。</span><span class="sxs-lookup"><span data-stu-id="50144-125">The **Video Player** object needs a textured game object on which to render the video.</span></span> <span data-ttu-id="50144-126">まず、[**階層**] ペインを右クリックし、[ **3d オブジェクト-> クワッド**] を選択して、**階層** に **クワッド** を追加します。</span><span class="sxs-lookup"><span data-stu-id="50144-126">First, add a **Quad** to your **Hierarchy** by right-clicking on the **Hierarchy** pane and choosing **3D Object -> Quad**:</span></span>

![クワッドを階層に追加](images/spatial-audio/add-quad-to-hierarchy.png)

<span data-ttu-id="50144-128">アプリケーションの起動時にユーザーの前に **quad** が表示されるようにするには、 **quad** の **Position** プロパティを (0, 0, 2) に設定し、 **Scale** プロパティを (1.28, 0.72, 1) に設定します。</span><span class="sxs-lookup"><span data-stu-id="50144-128">To ensure the **Quad** appears in front of the user when the application starts, set the **Position** property of the **Quad** to (0, 0, 2), and the **Scale** property to (1.28, 0.72, 1).</span></span> <span data-ttu-id="50144-129">これらの変更が完了すると、 **4** つ目の **インスペクター** ウィンドウの [**変換**] コンポーネントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="50144-129">After these changes, the **Transform** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![クワッド変換](images/spatial-audio/quad-transform.png)

<span data-ttu-id="50144-131">ビデオで **Quad** のテクスチャを作成するには、新しい **レンダリングテクスチャ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="50144-131">To texture the **Quad** with video, create a new **Render Texture**.</span></span> <span data-ttu-id="50144-132">[ **プロジェクト** ] ウィンドウで、右クリックし、[ **作成-> レンダリングテクスチャ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="50144-132">In the **Project** pane, right-click and choose **Create -> Render Texture**:</span></span>

![描画テクスチャを作成する](images/spatial-audio/create-render-texture.png)

<span data-ttu-id="50144-134">**レンダリングテクスチャ** の [**インスペクター** ] ウィンドウで、ビデオのネイティブ解像度である 1280 0x720 と一致するように **Size** プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="50144-134">On the **Inspector** pane of the **Render Texture**, set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="50144-135">次に、HoloLens 2 で適切なレンダリングパフォーマンスを確保するために、[ **深度バッファー** ] プロパティを **16 ビット以上の深さ** に設定します。</span><span class="sxs-lookup"><span data-stu-id="50144-135">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span> <span data-ttu-id="50144-136">これらの設定の後、**レンダリングテクスチャ** の [**インスペクター** ] ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="50144-136">After these settings, the **Inspector** pane for the **Render Texture** will look like this:</span></span>

![テクスチャのプロパティを表示する](images/spatial-audio/render-texture-properties.png)

<span data-ttu-id="50144-138">次に、新しい **レンダリングテクスチャ** を **4** 番目のテクスチャとして使用します。</span><span class="sxs-lookup"><span data-stu-id="50144-138">Next, use your new **Render Texture** as the texture for the **Quad**:</span></span>
1. <span data-ttu-id="50144-139">[**プロジェクト**] ウィンドウから、**階層** 内の **クワッド** に **レンダリングテクスチャ** をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="50144-139">Drag the **Render Texture** from the **Project** pane onto the **Quad** in the **Hierarchy**</span></span>
2. <span data-ttu-id="50144-140">HoloLens 2 で良好なパフォーマンスを得るには、**クワッド** の [**インスペクター** ] ウィンドウで、 **Mixed Reality Toolkit Standard Shader** を選択します。</span><span class="sxs-lookup"><span data-stu-id="50144-140">To ensure good performance on HoloLens 2, on the **Inspector** pane for the **Quad**, select the **Mixed Reality Toolkit Standard Shader**.</span></span>

<span data-ttu-id="50144-141">これらの設定を使用すると、**クワッド** の [**インスペクター** ] ウィンドウの **テクスチャ** コンポーネントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="50144-141">With these settings, the **Texture** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![クワッドテクスチャのプロパティ](images/spatial-audio/quad-texture-properties.png)

<span data-ttu-id="50144-143">新しい **ビデオプレーヤー** を設定し、ビデオクリップを再生するために **テクスチャをレンダリング** するには、**ビデオプレーヤー** の [**インスペクター** ] ウィンドウを開き、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="50144-143">To set your new **Video Player** and **Render Texture** to play your video clip, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="50144-144">ビデオ **クリップ** のプロパティをビデオファイルに設定します。</span><span class="sxs-lookup"><span data-stu-id="50144-144">Set the **Video Clip** property to your video file</span></span>
* <span data-ttu-id="50144-145">**ループ** チェックボックスをオンにする</span><span class="sxs-lookup"><span data-stu-id="50144-145">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="50144-146">**ターゲットテクスチャ** を新しいレンダリングテクスチャに設定する</span><span class="sxs-lookup"><span data-stu-id="50144-146">Set **Target Texture** to your new render texture</span></span>

<span data-ttu-id="50144-147">**ビデオプレーヤー** の [**インスペクター** ] ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="50144-147">The **Inspector** pane for the **Video Player** will now look like this:</span></span>

![ビデオプレーヤーのプロパティ](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="50144-149">ビデオからオーディオを Spatialize</span><span class="sxs-lookup"><span data-stu-id="50144-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="50144-150">**クワッド** の [**インスペクター** ] ウィンドウで、ビデオからオーディオをルーティングする **オーディオソース** を作成します。</span><span class="sxs-lookup"><span data-stu-id="50144-150">In the **Inspector** pane for the **Quad**, create an **Audio Source** to which you'll route the audio from the video:</span></span>
* <span data-ttu-id="50144-151">ペインの下部にある [ **コンポーネントの追加** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="50144-151">Click **Add Component** at the bottom of the pane</span></span>
* <span data-ttu-id="50144-152">**オーディオソース** を追加する</span><span class="sxs-lookup"><span data-stu-id="50144-152">Add an **Audio Source**</span></span>

<span data-ttu-id="50144-153">次に、 **オーディオソース** で次のようにします。</span><span class="sxs-lookup"><span data-stu-id="50144-153">Then, on the **Audio Source**:</span></span>
* <span data-ttu-id="50144-154">ミキサーに **出力** を設定する</span><span class="sxs-lookup"><span data-stu-id="50144-154">Set **Output** to your mixer</span></span>
* <span data-ttu-id="50144-155">[ **Spatialize** ] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="50144-155">Check the **Spatialize** box</span></span>
* <span data-ttu-id="50144-156">[ **空間ブレンド** ] スライダーを 1 (3d) に移動します。</span><span class="sxs-lookup"><span data-stu-id="50144-156">Move the **Spatial Blend** slider to 1 (3D)</span></span>

<span data-ttu-id="50144-157">これらの変更が完了すると、 **diag** ペインの [**インスペクター** ] ウィンドウの [**オーディオソース**] コンポーネントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="50144-157">After these changes, the **Audio Source** component on the **Inspector** pane for the **Quad** will look like this:</span></span>

![クワッドオーディオソースインスペクター](images/spatial-audio/quad-audio-source-inspector.png)

<span data-ttu-id="50144-159">**ビデオプレーヤー** が、そのオーディオを **クワッド** の **オーディオソース** にルーティングするように設定するには、**ビデオプレーヤー** の [**インスペクター** ] ウィンドウを開き、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="50144-159">To set the **Video Player** to route its audio to the **Audio Source** on the **Quad**, open the **Inspector** pane for the **Video Player** and:</span></span>
* <span data-ttu-id="50144-160">**オーディオ出力モード** を ' audio Source ' に設定します</span><span class="sxs-lookup"><span data-stu-id="50144-160">Set the **Audio Output Mode** to 'Audio Source'</span></span>
* <span data-ttu-id="50144-161">[ **オーディオソース** のプロパティを Quad に設定する</span><span class="sxs-lookup"><span data-stu-id="50144-161">Set the **Audio Source** property to your Quad</span></span>

<span data-ttu-id="50144-162">これらの変更が完了すると、**ビデオプレーヤー** の [**インスペクター** ] ウィンドウは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="50144-162">After these changes, the **Inspector** pane for the **Video Player** will look like this:</span></span>

![ビデオプレーヤー設定オーディオソース](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a><span data-ttu-id="50144-164">次のステップ</span><span class="sxs-lookup"><span data-stu-id="50144-164">Next steps</span></span>

<span data-ttu-id="50144-165">HoloLens 2 または Unity エディターでアプリを試してみてください。</span><span class="sxs-lookup"><span data-stu-id="50144-165">Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="50144-166">ビデオが表示され、再生されます。ビデオのオーディオは spatialized になります。</span><span class="sxs-lookup"><span data-stu-id="50144-166">You'll see and hear the video, and the audio from the video will be spatialized.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="50144-167">章4</span><span class="sxs-lookup"><span data-stu-id="50144-167">Chapter 4</span></span>](unity-spatial-audio-ch4.md) 

