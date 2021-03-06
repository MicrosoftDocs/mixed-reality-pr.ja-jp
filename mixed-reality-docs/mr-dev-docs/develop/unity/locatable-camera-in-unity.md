---
title: Unity での場所を特定できるカメラ
description: 写真をファイルまたは Texture2D にキャプチャする方法、写真をキャプチャして生のバイトを操作する方法、ビデオをキャプチャする方法について説明します。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: photo、video、hololens、カメラ、unity、入手、PVC、フォトビデオカメラ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、web カメラ、写真キャプチャ、ビデオキャプチャ
ms.openlocfilehash: ccf0c17a5f419341e64a87fb9ef04ef0a40c2a33
ms.sourcegitcommit: ad1e0c6a31f938a93daa2735cece24d676384f3f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102236903"
---
# <a name="locatable-camera-in-unity"></a><span data-ttu-id="02a03-104">Unity での場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="02a03-104">Locatable camera in Unity</span></span>

## <a name="enabling-the-capability-for-photo-video-camera"></a><span data-ttu-id="02a03-105">フォトビデオカメラの機能を有効にする</span><span class="sxs-lookup"><span data-stu-id="02a03-105">Enabling the capability for Photo Video Camera</span></span>

<span data-ttu-id="02a03-106">アプリで [カメラ](../platform-capabilities-and-apis/locatable-camera.md)を使用するには、"WebCam" 機能を宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="02a03-106">The "WebCam" capability must be declared for an app to use the [camera](../platform-capabilities-and-apis/locatable-camera.md).</span></span>
1. <span data-ttu-id="02a03-107">Unity エディターで、[> プロジェクト > 設定の編集] ページに移動して、プレーヤーの設定に移動します。</span><span class="sxs-lookup"><span data-stu-id="02a03-107">In the Unity Editor, go to the player settings by navigating to the "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="02a03-108">[Windows ストア] タブを選択します。</span><span class="sxs-lookup"><span data-stu-id="02a03-108">Select the "Windows Store" tab</span></span>
3. <span data-ttu-id="02a03-109">[発行設定 > 機能] セクションで、 **Web カメラ** と **マイク** の機能を確認します。</span><span class="sxs-lookup"><span data-stu-id="02a03-109">In the "Publishing Settings > Capabilities" section, check the **WebCam** and **Microphone** capabilities</span></span>

<span data-ttu-id="02a03-110">カメラで一度に実行できる操作は1つだけです。</span><span class="sxs-lookup"><span data-stu-id="02a03-110">Only a single operation can occur with the camera at a time.</span></span> <span data-ttu-id="02a03-111">カメラの現在の状態を、UnityEngine. XR のモードで確認できます。</span><span class="sxs-lookup"><span data-stu-id="02a03-111">You can check with mode the camera is currently in with UnityEngine.XR.WSA.WebCam.Mode.</span></span> <span data-ttu-id="02a03-112">使用可能なモードは、photo、video、または none です。</span><span class="sxs-lookup"><span data-stu-id="02a03-112">Available modes are photo, video, or none.</span></span>

## <a name="photo-capture"></a><span data-ttu-id="02a03-113">写真のキャプチャ</span><span class="sxs-lookup"><span data-stu-id="02a03-113">Photo Capture</span></span>

<span data-ttu-id="02a03-114">**名前空間:**</span><span class="sxs-lookup"><span data-stu-id="02a03-114">**Namespace:**</span></span>  
<span data-ttu-id="02a03-115">*UnityEngine. XR (Unity \~ 2018) unityengine. Windows. Web カメラ (unity 2019 \~ )*</span><span class="sxs-lookup"><span data-stu-id="02a03-115">*UnityEngine.XR.WSA.WebCam(Unity \~2018) UnityEngine.Windows.WebCam(Unity 2019\~)*</span></span><br>
<span data-ttu-id="02a03-116">**種類:** *photocapture*</span><span class="sxs-lookup"><span data-stu-id="02a03-116">**Type:** *PhotoCapture*</span></span>

<span data-ttu-id="02a03-117">*Photocapture* の種類を使用すると、写真ビデオカメラで引き続き写真を撮ることができます。</span><span class="sxs-lookup"><span data-stu-id="02a03-117">The *PhotoCapture* type allows you to take still photographs with the Photo Video Camera.</span></span> <span data-ttu-id="02a03-118">*Photocapture* を使用して写真を撮影する一般的なパターンを次に示します。</span><span class="sxs-lookup"><span data-stu-id="02a03-118">The general pattern for using *PhotoCapture* to take a photo is as follows:</span></span>
1. <span data-ttu-id="02a03-119">*Photocapture* オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="02a03-119">Create a *PhotoCapture* object</span></span>
2. <span data-ttu-id="02a03-120">必要な設定を使用して *CameraParameters* オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="02a03-120">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="02a03-121">*Startphotomodeasync* を使用して写真モードを開始する</span><span class="sxs-lookup"><span data-stu-id="02a03-121">Start Photo Mode via *StartPhotoModeAsync*</span></span>
4. <span data-ttu-id="02a03-122">希望の写真を撮影する</span><span class="sxs-lookup"><span data-stu-id="02a03-122">Take the photo you want</span></span>
    * <span data-ttu-id="02a03-123">optionalその画像と対話する</span><span class="sxs-lookup"><span data-stu-id="02a03-123">(optional) Interact with that picture</span></span>
5. <span data-ttu-id="02a03-124">フォトモードを停止してリソースをクリーンアップする</span><span class="sxs-lookup"><span data-stu-id="02a03-124">Stop Photo Mode and clean up resources</span></span>

### <a name="common-set-up-for-photocapture"></a><span data-ttu-id="02a03-125">PhotoCapture 用の一般的な設定</span><span class="sxs-lookup"><span data-stu-id="02a03-125">Common Set Up for PhotoCapture</span></span>

<span data-ttu-id="02a03-126">3つのすべての使用について、上記の最初の3つの手順から開始します。</span><span class="sxs-lookup"><span data-stu-id="02a03-126">For all three uses, start with the same first three steps above</span></span>

<span data-ttu-id="02a03-127">*Photocapture* オブジェクトの作成から開始する</span><span class="sxs-lookup"><span data-stu-id="02a03-127">Start by creating a *PhotoCapture* object</span></span>

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

<span data-ttu-id="02a03-128">次に、オブジェクトを格納し、パラメーターを設定して、写真モードを開始します。</span><span class="sxs-lookup"><span data-stu-id="02a03-128">Next, store your object, set your parameters, and start Photo Mode</span></span>

```cs
void OnPhotoCaptureCreated(PhotoCapture captureObject)
   {
       photoCaptureObject = captureObject;

       Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();

       CameraParameters c = new CameraParameters();
       c.hologramOpacity = 0.0f;
       c.cameraResolutionWidth = cameraResolution.width;
       c.cameraResolutionHeight = cameraResolution.height;
       c.pixelFormat = CapturePixelFormat.BGRA32;

       captureObject.StartPhotoModeAsync(c, false, OnPhotoModeStarted);
   }
```

<span data-ttu-id="02a03-129">最後に、ここに示されているのと同じクリーンアップコードも使用します。</span><span class="sxs-lookup"><span data-stu-id="02a03-129">In the end, you'll also use the same clean-up code presented here</span></span>

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

<span data-ttu-id="02a03-130">これらの手順の後に、キャプチャする写真の種類を選択できます。</span><span class="sxs-lookup"><span data-stu-id="02a03-130">After these steps, you can choose which type of photo to capture.</span></span>

### <a name="capture-a-photo-to-a-file"></a><span data-ttu-id="02a03-131">写真をファイルにキャプチャする</span><span class="sxs-lookup"><span data-stu-id="02a03-131">Capture a Photo to a File</span></span>

<span data-ttu-id="02a03-132">最も簡単な操作は、写真を直接ファイルにキャプチャすることです。</span><span class="sxs-lookup"><span data-stu-id="02a03-132">The simplest operation is to capture a photo directly to a file.</span></span> <span data-ttu-id="02a03-133">写真は、JPG または PNG として保存できます。</span><span class="sxs-lookup"><span data-stu-id="02a03-133">The photo can be saved as a JPG or a PNG.</span></span>

<span data-ttu-id="02a03-134">写真モードを正常に開始した場合は、写真を撮影してディスクに保存します。</span><span class="sxs-lookup"><span data-stu-id="02a03-134">If you successfully started photo mode, take a photo and store it on disk</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format(@"CapturedImage{0}_n.jpg", Time.time);
           string filePath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

<span data-ttu-id="02a03-135">写真をディスクにキャプチャしたら、フォトモードを終了し、オブジェクトをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="02a03-135">After capturing the photo to disk, exit photo mode and then clean up your objects</span></span>

```cs
void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           Debug.Log("Saved Photo to disk!");
           photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
       }
       else
       {
           Debug.Log("Failed to save Photo to disk");
       }
   }
```

### <a name="capture-a-photo-to-a-texture2d"></a><span data-ttu-id="02a03-136">写真を Texture2D に取り込む</span><span class="sxs-lookup"><span data-stu-id="02a03-136">Capture a Photo to a Texture2D</span></span>

<span data-ttu-id="02a03-137">Texture2D にデータをキャプチャするときのプロセスは、ディスクへのキャプチャと似ています。</span><span class="sxs-lookup"><span data-stu-id="02a03-137">When capturing data to a Texture2D, the process is similar to capturing to disk.</span></span>

<span data-ttu-id="02a03-138">上記のセットアッププロセスに従います。</span><span class="sxs-lookup"><span data-stu-id="02a03-138">Follow the setup process above.</span></span>

<span data-ttu-id="02a03-139">*Onphotomodestarted 開始* し、フレームをメモリにキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="02a03-139">In *OnPhotoModeStarted*, capture a frame to memory.</span></span>

```cs
private void OnPhotoModeStarted(PhotoCapture.PhotoCaptureResult result)
   {
       if (result.success)
       {
           photoCaptureObject.TakePhotoAsync(OnCapturedPhotoToMemory);
       }
       else
       {
           Debug.LogError("Unable to start photo mode!");
       }
   }
```

<span data-ttu-id="02a03-140">次に、結果をテクスチャに適用し、上記の一般的なクリーンアップコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="02a03-140">You'll then apply your result to a texture and use the common clean-up code above.</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           // Create our Texture2D for use and set the correct resolution
           Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
           // Copy the raw image data into our target texture
           photoCaptureFrame.UploadImageDataToTexture(targetTexture);
           // Do as we wish with the texture such as apply it to a material, etc.
       }
       // Clean up
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a><span data-ttu-id="02a03-141">写真をキャプチャし、生のバイトを操作する</span><span class="sxs-lookup"><span data-stu-id="02a03-141">Capture a Photo and Interact with the Raw bytes</span></span>

<span data-ttu-id="02a03-142">インメモリフレームの生バイトを操作するには、上記と同じセットアップ手順に従い、Texture2D への写真のキャプチャと同様に *Onphotomodestarted 開始* します。</span><span class="sxs-lookup"><span data-stu-id="02a03-142">To interact with the raw bytes of an in memory frame, follow the same setup steps as above and *OnPhotoModeStarted* as in capturing a photo to a Texture2D.</span></span> <span data-ttu-id="02a03-143">違いは、生のバイトを取得して操作できる *OnCapturedPhotoToMemory* です。</span><span class="sxs-lookup"><span data-stu-id="02a03-143">The difference is in *OnCapturedPhotoToMemory* where you can get the raw bytes and interact with them.</span></span>

<span data-ttu-id="02a03-144">この例では、 *Setpixels ()* を使用してさらに処理またはテクスチャに適用する *リスト <Color>* を作成します。</span><span class="sxs-lookup"><span data-stu-id="02a03-144">In this example, you'll create a *List<Color>* to be further processed or applied to a texture via *SetPixels()*</span></span>

```cs
void OnCapturedPhotoToMemory(PhotoCapture.PhotoCaptureResult result, PhotoCaptureFrame photoCaptureFrame)
   {
       if (result.success)
       {
           List<byte> imageBufferList = new List<byte>();
           // Copy the raw IMFMediaBuffer data into our empty byte list.
           photoCaptureFrame.CopyRawImageDataIntoBuffer(imageBufferList);

           // In this example, we captured the image using the BGRA32 format.
           // So our stride will be 4 since we have a byte for each rgba channel.
           // The raw image data will also be flipped so we access our pixel data
           // in the reverse order.
           int stride = 4;
           float denominator = 1.0f / 255.0f;
           List<Color> colorArray = new List<Color>();
           for (int i = imageBufferList.Count - 1; i >= 0; i -= stride)
           {
               float a = (int)(imageBufferList[i - 0]) * denominator;
               float r = (int)(imageBufferList[i - 1]) * denominator;
               float g = (int)(imageBufferList[i - 2]) * denominator;
               float b = (int)(imageBufferList[i - 3]) * denominator;

               colorArray.Add(new Color(r, g, b, a));
           }
           // Now we could do something with the array such as texture.SetPixels() or run image processing on the list
       }
       photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
   }
```

## <a name="video-capture"></a><span data-ttu-id="02a03-145">ビデオキャプチャ</span><span class="sxs-lookup"><span data-stu-id="02a03-145">Video Capture</span></span>

<span data-ttu-id="02a03-146">**名前空間:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="02a03-146">**Namespace:** *UnityEngine.XR.WSA.WebCam*</span></span><br>
<span data-ttu-id="02a03-147">**型:** *VideoCapture*</span><span class="sxs-lookup"><span data-stu-id="02a03-147">**Type:** *VideoCapture*</span></span>

<span data-ttu-id="02a03-148">*VideoCapture* は *photocapture* と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="02a03-148">*VideoCapture* functions similarly to *PhotoCapture*.</span></span> <span data-ttu-id="02a03-149">2つの違いは、1秒あたりのフレーム数 (FPS) の値を指定する必要があり、mp4 ファイルとして直接ディスクに保存できることだけです。</span><span class="sxs-lookup"><span data-stu-id="02a03-149">The only two differences are that you must specify a Frames Per Second (FPS) value and you can only save directly to disk as a .mp4 file.</span></span> <span data-ttu-id="02a03-150">*VideoCapture* を使用する手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="02a03-150">The steps to use *VideoCapture* are as follows:</span></span>
1. <span data-ttu-id="02a03-151">*VideoCapture* オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="02a03-151">Create a *VideoCapture* object</span></span>
2. <span data-ttu-id="02a03-152">必要な設定を使用して *CameraParameters* オブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="02a03-152">Create a *CameraParameters* object with the settings you want</span></span>
3. <span data-ttu-id="02a03-153">*Startvideomodeasync* を使用してビデオモードを開始する</span><span class="sxs-lookup"><span data-stu-id="02a03-153">Start Video Mode via *StartVideoModeAsync*</span></span>
4. <span data-ttu-id="02a03-154">ビデオの録画を開始する</span><span class="sxs-lookup"><span data-stu-id="02a03-154">Start recording video</span></span>
5. <span data-ttu-id="02a03-155">ビデオ記録の停止</span><span class="sxs-lookup"><span data-stu-id="02a03-155">Stop recording video</span></span>
6. <span data-ttu-id="02a03-156">ビデオモードを停止してリソースをクリーンアップする</span><span class="sxs-lookup"><span data-stu-id="02a03-156">Stop Video Mode and clean up resources</span></span>

<span data-ttu-id="02a03-157">まず、 *VideoCapture* オブジェクト VideoCapture m_VideoCapture を作成し *ます。*</span><span class="sxs-lookup"><span data-stu-id="02a03-157">Start by creating our *VideoCapture* object *VideoCapture m_VideoCapture = null;*</span></span>

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

<span data-ttu-id="02a03-158">次に、記録に使用するパラメーターを設定し、を開始します。</span><span class="sxs-lookup"><span data-stu-id="02a03-158">Next, set up the parameters you'll want for the recording and start.</span></span>

```cs
void OnVideoCaptureCreated (VideoCapture videoCapture)
   {
       if (videoCapture != null)
       {
           m_VideoCapture = videoCapture;

           Resolution cameraResolution = VideoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();
           float cameraFramerate = VideoCapture.GetSupportedFrameRatesForResolution(cameraResolution).OrderByDescending((fps) => fps).First();

           CameraParameters cameraParameters = new CameraParameters();
           cameraParameters.hologramOpacity = 0.0f;
           cameraParameters.frameRate = cameraFramerate;
           cameraParameters.cameraResolutionWidth = cameraResolution.width;
           cameraParameters.cameraResolutionHeight = cameraResolution.height;
           cameraParameters.pixelFormat = CapturePixelFormat.BGRA32;

           m_VideoCapture.StartVideoModeAsync(cameraParameters,
                                               VideoCapture.AudioState.None,
                                               OnStartedVideoCaptureMode);
       }
       else
       {
           Debug.LogError("Failed to create VideoCapture Instance!");
       }
   }
```

<span data-ttu-id="02a03-159">開始したら、記録を開始します。</span><span class="sxs-lookup"><span data-stu-id="02a03-159">Once started, begin the recording</span></span>

```cs
void OnStartedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       if (result.success)
       {
           string filename = string.Format("MyVideo_{0}.mp4", Time.time);
           string filepath = System.IO.Path.Combine(Application.persistentDataPath, filename);

           m_VideoCapture.StartRecordingAsync(filepath, OnStartedRecordingVideo);
       }
   }
```

<span data-ttu-id="02a03-160">記録が開始されたら、UI または動作を更新して停止を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="02a03-160">After recording has started, you could update your UI or behaviors to enable stopping.</span></span> <span data-ttu-id="02a03-161">ここでは、ログを記録するだけです。</span><span class="sxs-lookup"><span data-stu-id="02a03-161">Here you just log.</span></span>

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

<span data-ttu-id="02a03-162">後で、タイマーまたはユーザー入力を使用して記録を停止します。たとえば、のようにします。</span><span class="sxs-lookup"><span data-stu-id="02a03-162">At a later point, you'll want to stop the recording using a timer or user input, for instance.</span></span>

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

<span data-ttu-id="02a03-163">記録が停止したら、ビデオモードを停止し、リソースをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="02a03-163">Once the recording has stopped, stop video mode and clean up your resources.</span></span>

```cs
void OnStoppedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Stopped Recording Video!");
       m_VideoCapture.StopVideoModeAsync(OnStoppedVideoCaptureMode);
   }

   void OnStoppedVideoCaptureMode(VideoCapture.VideoCaptureResult result)
   {
       m_VideoCapture.Dispose();
       m_VideoCapture = null;
   }
```

## <a name="troubleshooting"></a><span data-ttu-id="02a03-164">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="02a03-164">Troubleshooting</span></span>
* <span data-ttu-id="02a03-165">解決策はありません</span><span class="sxs-lookup"><span data-stu-id="02a03-165">No resolutions are available</span></span>
    * <span data-ttu-id="02a03-166">**Web カメラ** 機能がプロジェクトで指定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="02a03-166">Ensure the **WebCam** capability is specified in your project.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="02a03-167">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="02a03-167">Next Development Checkpoint</span></span>

<span data-ttu-id="02a03-168">ここまでに説明した Unity 開発チェックポイントの旅に従っている場合は、Mixed Reality プラットフォームの機能と Api の調査が途中で終了しています。</span><span class="sxs-lookup"><span data-stu-id="02a03-168">If you're following the Unity development checkpoint journey we've laid out, you're in the midst of exploring the Mixed Reality platform capabilities and APIs.</span></span> <span data-ttu-id="02a03-169">ここから、次のトピックを続けることができます。</span><span class="sxs-lookup"><span data-stu-id="02a03-169">From here, you can continue to the next topic:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="02a03-170">フォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="02a03-170">Focus point</span></span>](focus-point-in-unity.md)

<span data-ttu-id="02a03-171">または、デバイスまたはエミュレーターへのアプリの配置操作に直接移動します。</span><span class="sxs-lookup"><span data-stu-id="02a03-171">Or jump directly to deploying your app on a device or emulator:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="02a03-172">HoloLens または Windows Mixed Reality イマーシブヘッドセットへのデプロイ</span><span class="sxs-lookup"><span data-stu-id="02a03-172">Deploy to HoloLens or Windows Mixed Reality immersive headsets</span></span>](../platform-capabilities-and-apis/using-visual-studio.md)

<span data-ttu-id="02a03-173">いつでも [Unity 開発チェックポイント](unity-development-overview.md#3-advanced-features)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="02a03-173">You can always go back to the [Unity development checkpoints](unity-development-overview.md#3-advanced-features) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="02a03-174">関連項目</span><span class="sxs-lookup"><span data-stu-id="02a03-174">See Also</span></span>
* [<span data-ttu-id="02a03-175">場所を特定できるカメラ</span><span class="sxs-lookup"><span data-stu-id="02a03-175">Locatable camera</span></span>](../platform-capab ilities-and-apis/locatable-camera.md)
