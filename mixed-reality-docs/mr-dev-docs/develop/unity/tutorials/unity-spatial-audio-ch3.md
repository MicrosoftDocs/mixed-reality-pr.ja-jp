---
title: 空間オーディオチュートリアル-3. ビデオからオーディオの立体化
description: ビデオ資産を Unity プロジェクトにインポートし、ビデオからオーディオを spatialize します。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、ヘッド関連の転送機能、リバーブ、Microsoft Spatializer、ビデオのインポート、ビデオプレーヤー
ms.openlocfilehash: 6474da522e650d23349a21c3deeac00222b8ce93
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2021
ms.locfileid: "98578574"
---
# <a name="3-spatializing-audio-from-a-video"></a><span data-ttu-id="24364-105">3.ビデオからオーディオの立体化</span><span class="sxs-lookup"><span data-stu-id="24364-105">3. Spatializing audio from a video</span></span>

## <a name="overview"></a><span data-ttu-id="24364-106">概要</span><span class="sxs-lookup"><span data-stu-id="24364-106">Overview</span></span>

<span data-ttu-id="24364-107">このチュートリアルでは、ビデオソースからオーディオを spatialize し、unity エディターと HoloLens 2 でこれをテストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="24364-107">In this tutorial, you will learn how to spatialize audio from an video source and test this in the unity editor and HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="24364-108">目標</span><span class="sxs-lookup"><span data-stu-id="24364-108">Objectives</span></span>

* <span data-ttu-id="24364-109">ビデオをインポートしてビデオプレーヤーを追加する</span><span class="sxs-lookup"><span data-stu-id="24364-109">Import a video and add a Video Player</span></span>
* <span data-ttu-id="24364-110">ビデオを quadrangle に再生する</span><span class="sxs-lookup"><span data-stu-id="24364-110">Play the video onto a quadrangle</span></span>
* <span data-ttu-id="24364-111">オーディオをビデオから quadrangle にルーティングし、オーディオを spatialize する</span><span class="sxs-lookup"><span data-stu-id="24364-111">Route audio from the video to the quadrangle, and spatialize the audio</span></span>

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a><span data-ttu-id="24364-112">ビデオをインポートし、ビデオプレーヤーをシーンに追加する</span><span class="sxs-lookup"><span data-stu-id="24364-112">Import a video and add a Video Player to the Scene</span></span>

<span data-ttu-id="24364-113">このチュートリアルでは、空間オーディオサンプルプロジェクトの [このビデオ](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) を使用します。</span><span class="sxs-lookup"><span data-stu-id="24364-113">For this tutorial use You can use [this video](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) from the spatial audio sample project.</span></span>

<span data-ttu-id="24364-114">Unity プロジェクトにビデオをインポートします。</span><span class="sxs-lookup"><span data-stu-id="24364-114">To import Video into the unity project.</span></span> <span data-ttu-id="24364-115">Unity メニューで、[**資産**] [  >  **新しい資産のインポート**] [ 
 ![ 資産のインポート] を選択します。](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span><span class="sxs-lookup"><span data-stu-id="24364-115">in the Unity menu select **Asset** > **Import New Asset**
![Importing Asset](images/spatial-audio/spatial-audio-03-section1-step1-1.png)</span></span>

<span data-ttu-id="24364-116">[ **新しい資産のインポート** ] ウィンドウで、ダウンロードした **Microsoft HoloLens の PTPvx7mDon4** ファイルを選択し、[ **開く** ] ボタンをクリックして、プロジェクトにアセットをインポートします。</span><span class="sxs-lookup"><span data-stu-id="24364-116">In the **Import New Asset...** window, select the **Microsoft HoloLens - Spatial Sound-PTPvx7mDon4** file you downloaded and click the **Open** button to import the asset into the project:</span></span>

![資産の選択](images/spatial-audio/spatial-audio-03-section1-step1-2.png)

<span data-ttu-id="24364-118">ビデオクリップの品質設定を調整すると、HoloLens 2 でスムーズに再生されるようになります。</span><span class="sxs-lookup"><span data-stu-id="24364-118">Adjusting the quality settings on the video clip can ensure smooth playback on HoloLens 2.</span></span> <span data-ttu-id="24364-119">[**プロジェクト**] ウィンドウでビデオファイルを選択し、ビデオファイルの [インスペクター] ウィンドウで、 **Windows ストアアプリ** の設定を **上書き** して、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="24364-119">Select the video file in the **Project** window and in the Inspector window of the video file, **override** the settings for **Windows Store Apps**, and:</span></span>

* <span data-ttu-id="24364-120">**トランスコード** を有効にする</span><span class="sxs-lookup"><span data-stu-id="24364-120">Enable **Transcode**</span></span>
* <span data-ttu-id="24364-121">**コーデック** を H264 に設定する</span><span class="sxs-lookup"><span data-stu-id="24364-121">Set **Codec** to H264</span></span>
* <span data-ttu-id="24364-122">**ビットレートモード** を低に設定</span><span class="sxs-lookup"><span data-stu-id="24364-122">Set **Bitrate Mode** to Low</span></span>
* <span data-ttu-id="24364-123">**空間品質** を中程度に設定する</span><span class="sxs-lookup"><span data-stu-id="24364-123">Set **Spatial Quality** to Medium Spatial Quality</span></span>

<span data-ttu-id="24364-124">これらの調整が完了したら、[適用] をクリックして、ビデオクリップの品質設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="24364-124">After these adjustments, click on Apply to change the quality setting on the video clip.</span></span>

![ビデオのプロパティの変更](images/spatial-audio/spatial-audio-03-section1-step1-3.png)

<span data-ttu-id="24364-126">階層を右クリックし、[ビデオビデオプレーヤー]**を選択し** て、  >  ビデオプレーヤーコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="24364-126">Right click on the Hierarchy, Select **Video** > **Video Player** to add Video player component.</span></span>

![ビデオプレーヤーの追加](images/spatial-audio/spatial-audio-03-section1-step1-4.png)

## <a name="play-video-onto-a-quadrangle"></a><span data-ttu-id="24364-128">ビデオを quadrangle に再生する</span><span class="sxs-lookup"><span data-stu-id="24364-128">Play video onto a quadrangle</span></span>

<span data-ttu-id="24364-129">ビデオをレンダリングするには、 **ビデオプレーヤー** オブジェクトにテクスチャを表示するゲームオブジェクトが必要です。</span><span class="sxs-lookup"><span data-stu-id="24364-129">The **Video Player** object needs a textured game object to render the video.</span></span>

<span data-ttu-id="24364-130">階層を右クリックし、[ **3d オブジェクト** quad] を選択し  >  て quad を作成し、**変換** コンポーネントを次のように構成します。</span><span class="sxs-lookup"><span data-stu-id="24364-130">Right click the Hierarchy , Select **3D Object** > **Quad** to create a quad and configure its **Transform** component as follows:</span></span>

* <span data-ttu-id="24364-131">**位置**: X = 0、Y = 0、Z = 2</span><span class="sxs-lookup"><span data-stu-id="24364-131">**Position**: X = 0, Y = 0, Z = 2</span></span>
* <span data-ttu-id="24364-132">**回転**:X = 0、Y = 0、Z = 0</span><span class="sxs-lookup"><span data-stu-id="24364-132">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="24364-133">**小数点以下桁数**: X = 1.28、Y = 0.72、Z = 1</span><span class="sxs-lookup"><span data-stu-id="24364-133">**Scale**: X = 1.28, Y = 0.72, Z = 1</span></span>

![クワッドを追加する](images/spatial-audio/spatial-audio-03-section2-step1-1.png)

<span data-ttu-id="24364-135">ここで、ビデオを使用して **クワッド** のテクスチャを **作成** し、[**プロジェクト**] ウィンドウで右クリックして [レンダリングテクスチャの作成] を選択し、レンダリングテクスチャコンポーネントを  >  作成します。次に、レンダリングテクスチャに適切な名前を入力します。たとえば、「_空間オーディオテクスチャ_:</span><span class="sxs-lookup"><span data-stu-id="24364-135">Now you need to texture the **Quad** with the video, In the **Project** window, right-click and choose **Create** > **Render Texture** to create a Render Texture component, enter a suitable name to the Render Texture for example, _Spatial Audio Texture_:</span></span>

![描画テクスチャを作成する](images/spatial-audio/spatial-audio-03-section2-step1-2.png)

<span data-ttu-id="24364-137">**レンダリングテクスチャ** を選択し、[インスペクター] ウィンドウで、ビデオのネイティブ解像度である 1280 0x720 と一致するように **Size** プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="24364-137">Select the **Render Texture** and in the Inspector window set the **Size** property to match the video's native resolution of 1280x720.</span></span> <span data-ttu-id="24364-138">次に、HoloLens 2 で適切なレンダリングパフォーマンスを確保するために、[ **深度バッファー** ] プロパティを **16 ビット以上の深さ** に設定します。</span><span class="sxs-lookup"><span data-stu-id="24364-138">Then, to ensure good rendering performance on HoloLens 2, set the **Depth Buffer** property to **At least 16 bits depth**.</span></span>

![テクスチャのプロパティを表示する](images/spatial-audio/spatial-audio-03-section2-step1-3.png)

<span data-ttu-id="24364-140">次に、作成したレンダーテクスチャ **空間オーディオテクスチャ** を **Quad** のテクスチャとして使用します。</span><span class="sxs-lookup"><span data-stu-id="24364-140">Next, use the created Render Texture **Spatial Audio Texture** as the texture for the **Quad**:</span></span>

1. <span data-ttu-id="24364-141">**空間オーディオテクスチャ** を [**プロジェクト**] ウィンドウから階層内の **クワッド** にドラッグして、レンダーテクスチャをクワッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="24364-141">Drag the **Spatial Audio Texture** from the **Project** window onto the **Quad** in the Hierarchy to add the Render Texture to the Quad</span></span>
2. <span data-ttu-id="24364-142">HoloLens 2 でパフォーマンスを向上させるには、階層で [クワッド] を選択し、[シェーダー] の [インスペクター] ウィンドウで **Mixed Reality Toolkit**  >  **Standard** shader を選択します。</span><span class="sxs-lookup"><span data-stu-id="24364-142">To ensure good performance on HoloLens 2, select Quad in the Hierarchy and in the Inspector window for shader select the **Mixed Reality Toolkit** > **Standard** Shader.</span></span>

![クワッドテクスチャのプロパティ](images/spatial-audio/spatial-audio-03-section2-step1-4.png)

<span data-ttu-id="24364-144">ビデオ **プレーヤー** を設定し、ビデオ **クリップを再生するに** は、**階層** 内で **ビデオプレーヤー** を選択し、[**インスペクター** ] ウィンドウで</span><span class="sxs-lookup"><span data-stu-id="24364-144">To set **Video Player** and **Render Texture** to play the video clip, select the **Video Player** in the **Hierarchy** and in the **Inspector** window,</span></span>

* <span data-ttu-id="24364-145">**ビデオクリップ** のプロパティを、ダウンロードしたビデオファイル ' Microsoft HoloLens-PTPvx7mDon4 ' に設定します</span><span class="sxs-lookup"><span data-stu-id="24364-145">Set the **Video Clip** property to the downloaded video file 'Microsoft HoloLens - Spatial Sound-PTPvx7mDon4'</span></span>
* <span data-ttu-id="24364-146">**ループ** チェックボックスをオンにする</span><span class="sxs-lookup"><span data-stu-id="24364-146">Check the **Loop** checkbox</span></span>
* <span data-ttu-id="24364-147">**ターゲットテクスチャ** を新しいレンダリングテクスチャ **空間オーディオテクスチャ** に設定します</span><span class="sxs-lookup"><span data-stu-id="24364-147">Set **Target Texture** to your new render texture **Spatial Audio Texture**</span></span>

![ビデオプレーヤーのプロパティ](images/spatial-audio/spatial-audio-03-section2-step1-5.png)

## <a name="spatialize-the-audio-from-the-video"></a><span data-ttu-id="24364-149">ビデオからオーディオを Spatialize</span><span class="sxs-lookup"><span data-stu-id="24364-149">Spatialize the audio from the video</span></span>

<span data-ttu-id="24364-150">[階層] ウィンドウで [ **Quad** オブジェクト] を選択し、[インスペクター] ウィンドウで [ **コンポーネントの追加** ] ボタンを使用して、ビデオからオーディオをルーティングする **オーディオソース** を追加します。</span><span class="sxs-lookup"><span data-stu-id="24364-150">In the Hierarchy window, select **Quad** object, then in the Inspector window, use the **Add Component** button to add **Audio Source** to which you'll route the audio from the video.</span></span>

<span data-ttu-id="24364-151">**オーディオソース**:</span><span class="sxs-lookup"><span data-stu-id="24364-151">In the **Audio Source**:</span></span>

* <span data-ttu-id="24364-152">**空間オーディオミキサー** に **出力** を設定する</span><span class="sxs-lookup"><span data-stu-id="24364-152">Set **Output** to the **Spatial Audio Mixer**</span></span>
* <span data-ttu-id="24364-153">[ **Spatialize** ] チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="24364-153">Check the **Spatialize** box</span></span>
* <span data-ttu-id="24364-154">[ **空間ブレンド** ] スライダーを 1 (3d) に移動します。</span><span class="sxs-lookup"><span data-stu-id="24364-154">Move the **Spatial Blend** slider to 1 (3D)</span></span>

![クワッドオーディオソースインスペクター](images/spatial-audio/spatial-audio-03-section3-step1-1.png)

<span data-ttu-id="24364-156">オーディオを **オーディオソース** にルーティングするようにビデオプレーヤーを設定するには、[階層] ウィンドウで **ビデオプレーヤー** を選択し、インスペクターのビデオプレーヤーオブジェクトで次の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="24364-156">To set the Video Player to route its audio to the **Audio Source**, select the **Video Player** In the Hierarchy window, and in Video Player object in the Inspector do the following changes.</span></span>

* <span data-ttu-id="24364-157">オーディオ **出力モード** を **オーディオソース** に設定する</span><span class="sxs-lookup"><span data-stu-id="24364-157">Set the **Audio Output Mode** to **Audio Source**</span></span>
* <span data-ttu-id="24364-158">**Audio Source** プロパティを **クワッド** に設定します。</span><span class="sxs-lookup"><span data-stu-id="24364-158">Set the **Audio Source** property to the **Quad**</span></span>

![ビデオプレーヤー設定オーディオソース](images/spatial-audio/spatial-audio-03-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="24364-160">HoloLens 2 に Unity プロジェクトをビルドして配置する方法を再確認するには、[HoloLens 2 にアプリをビルドする](mr-learning-base-02.md#building-your-application-to-your-hololens-2)手順に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24364-160">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your app to your HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2) instructions.</span></span>

## <a name="congratulations"></a><span data-ttu-id="24364-161">結論</span><span class="sxs-lookup"><span data-stu-id="24364-161">Congratulations</span></span>

<span data-ttu-id="24364-162">このチュートリアルでは、ビデオソースからオーディオを spatialize して、HoloLens 2 または Unity エディターでアプリを試してみる方法について学習しました。</span><span class="sxs-lookup"><span data-stu-id="24364-162">In this tutorial, you have learned how to spatialize audio from an video source Try out your app on a HoloLens 2 or in the Unity editor.</span></span> <span data-ttu-id="24364-163">ビデオが表示されます。ビデオのオーディオは spatialized です。</span><span class="sxs-lookup"><span data-stu-id="24364-163">You'll see and hear the video, and the audio from the video is spatialized.</span></span>

<span data-ttu-id="24364-164">次のチュートリアルでは、実行時に spatialization を有効または無効にする方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="24364-164">In the next tutorial you will learn how to Enable and disable spatialization at run time</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="24364-165">次のチュートリアル: 4. 実行時に spatialization を有効または無効にする</span><span class="sxs-lookup"><span data-stu-id="24364-165">Next Tutorial: 4. Enabling and disabling spatialization at run time</span></span>](unity-spatial-audio-ch4.md)
