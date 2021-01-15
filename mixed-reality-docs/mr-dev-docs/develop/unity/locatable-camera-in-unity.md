---
title: Unity での場所を特定できるカメラ
description: 写真をファイルまたは Texture2D にキャプチャする方法、写真をキャプチャして生のバイトを操作する方法、ビデオをキャプチャする方法について説明します。
author: wguyman
ms.author: wguyman
ms.date: 03/21/2018
ms.topic: article
keywords: photo、video、hololens、カメラ、unity、入手、PVC、フォトビデオカメラ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、web カメラ、写真キャプチャ、ビデオキャプチャ
ms.openlocfilehash: 8916b332774185e4453b514ca7b6916947bdcd81
ms.sourcegitcommit: be7473bbebc1872d8c9df6f2da837efd3279dee6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/15/2021
ms.locfileid: "98226421"
---
# <a name="locatable-camera-in-unity"></a>Unity での場所を特定できるカメラ

## <a name="enabling-the-capability-for-photo-video-camera"></a>フォトビデオカメラの機能を有効にする

アプリで [カメラ](../platform-capabilities-and-apis/locatable-camera.md)を使用するには、"WebCam" 機能を宣言する必要があります。
1. Unity エディターで、[> プロジェクト > 設定の編集] ページに移動して、プレーヤーの設定に移動します。
2. [Windows ストア] タブを選択します。
3. [発行設定 > 機能] セクションで、 **Web カメラ** と **マイク** の機能を確認します。

カメラで一度に実行できる操作は1つだけです。 カメラの現在の状態を、UnityEngine. XR のモードで確認できます。 使用可能なモードは、photo、video、または none です。

## <a name="photo-capture"></a>写真のキャプチャ

**名前空間:** *UNITYENGINE. XR*<br>
**種類:** *photocapture*

*Photocapture* の種類を使用すると、写真ビデオカメラで引き続き写真を撮ることができます。 *Photocapture* を使用して写真を撮影する一般的なパターンを次に示します。
1. *Photocapture* オブジェクトを作成する
2. 必要な設定を使用して *CameraParameters* オブジェクトを作成する
3. *Startphotomodeasync* を使用して写真モードを開始する
4. 希望の写真を撮影する
    * optionalその画像と対話する
5. フォトモードを停止してリソースをクリーンアップする

### <a name="common-set-up-for-photocapture"></a>PhotoCapture 用の一般的な設定

3つのすべての使用について、上記の最初の3つの手順から開始します。

*Photocapture* オブジェクトの作成から開始する

```cs
PhotoCapture photoCaptureObject = null;
   void Start()
   {
       PhotoCapture.CreateAsync(false, OnPhotoCaptureCreated);
   }
```

次に、オブジェクトを格納し、パラメーターを設定して、写真モードを開始します。

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

最後に、ここに示されているのと同じクリーンアップコードも使用します。

```cs
void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
   {
       photoCaptureObject.Dispose();
       photoCaptureObject = null;
   }
```

これらの手順の後に、キャプチャする写真の種類を選択できます。

### <a name="capture-a-photo-to-a-file"></a>写真をファイルにキャプチャする

最も簡単な操作は、写真を直接ファイルにキャプチャすることです。 写真は、JPG または PNG として保存できます。

写真モードを正常に開始した場合は、写真を撮影してディスクに保存します。

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

写真をディスクにキャプチャしたら、フォトモードを終了し、オブジェクトをクリーンアップします。

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

### <a name="capture-a-photo-to-a-texture2d"></a>写真を Texture2D に取り込む

Texture2D にデータをキャプチャするときのプロセスは、ディスクへのキャプチャと似ています。

上記のセットアッププロセスに従います。

*Onphotomodestarted 開始* し、フレームをメモリにキャプチャします。

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

次に、結果をテクスチャに適用し、上記の一般的なクリーンアップコードを使用します。

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

### <a name="capture-a-photo-and-interact-with-the-raw-bytes"></a>写真をキャプチャし、生のバイトを操作する

インメモリフレームの生バイトを操作するには、上記と同じセットアップ手順に従い、Texture2D への写真のキャプチャと同様に *Onphotomodestarted 開始* します。 違いは、生のバイトを取得して操作できる *OnCapturedPhotoToMemory* です。

この例では、 *Setpixels ()* を使用してさらに処理またはテクスチャに適用する *リスト <Color>* を作成します。

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

## <a name="video-capture"></a>ビデオキャプチャ

**名前空間:** *UNITYENGINE. XR*<br>
**型:** *VideoCapture*

*VideoCapture* は *photocapture* と同様に機能します。 2つの違いは、1秒あたりのフレーム数 (FPS) の値を指定する必要があり、mp4 ファイルとして直接ディスクに保存できることだけです。 *VideoCapture* を使用する手順は次のとおりです。
1. *VideoCapture* オブジェクトを作成する
2. 必要な設定を使用して *CameraParameters* オブジェクトを作成する
3. *Startvideomodeasync* を使用してビデオモードを開始する
4. ビデオの録画を開始する
5. ビデオ記録の停止
6. ビデオモードを停止してリソースをクリーンアップする

まず、 *VideoCapture* オブジェクト VideoCapture m_VideoCapture を作成し *ます。*

```cs
void Start ()
   {
       VideoCapture.CreateAsync(false, OnVideoCaptureCreated);
   }
```

次に、記録に使用するパラメーターを設定し、を開始します。

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

開始したら、記録を開始します。

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

記録が開始されたら、UI または動作を更新して停止を有効にすることができます。 ここでは、ログを記録するだけです。

```cs
void OnStartedRecordingVideo(VideoCapture.VideoCaptureResult result)
   {
       Debug.Log("Started Recording Video!");
       // We will stop the video from recording via other input such as a timer or a tap, etc.
   }
```

後で、タイマーまたはユーザー入力を使用して記録を停止します。たとえば、のようにします。

```cs
// The user has indicated to stop recording
   void StopRecordingVideo()
   {
       m_VideoCapture.StopRecordingAsync(OnStoppedRecordingVideo);
   }
```

記録が停止したら、ビデオモードを停止し、リソースをクリーンアップします。

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

## <a name="troubleshooting"></a>トラブルシューティング
* 解決策はありません
    * **Web カメラ** 機能がプロジェクトで指定されていることを確認します。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

ここまでに説明した Unity 開発チェックポイントの旅に従っている場合は、Mixed Reality プラットフォームの機能と Api の調査が途中で終了しています。 ここから、次のトピックを続けることができます。

> [!div class="nextstepaction"]
> [フォーカス ポイント](focus-point-in-unity.md)

または、デバイスまたはエミュレーターへのアプリの配置操作に直接移動します。

> [!div class="nextstepaction"]
> [HoloLens または Windows Mixed Reality イマーシブヘッドセットへのデプロイ](../platform-capabilities-and-apis/using-visual-studio.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#3-advanced-features)に戻ることができます。

## <a name="see-also"></a>参照
* [場所を特定できるカメラ](../platform-capab ilities-and-apis/locatable-camera.md)
