---
title: 空間オーディオチュートリアル-3. ビデオからオーディオの立体化
description: ビデオ資産を Unity プロジェクトにインポートし、ビデオからオーディオを spatialize します。
author: kegodin
ms.author: kegodin
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ
ms.openlocfilehash: cd684944bdd618dcf435ef91566d6d4f18aa87a3
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91689786"
---
# <a name="spatializing-audio-from-a-video"></a>ビデオからオーディオの立体化
HoloLens 2 Unity チュートリアルの空間オーディオモジュールの第3章では、次のことを行います。
* ビデオをインポートしてビデオプレーヤーを追加する
* ビデオを quadrangle に再生する
* オーディオをビデオから quadrangle にルーティングし、オーディオを spatialize する

## <a name="import-a-video-and-add-a-video-player"></a>ビデオをインポートしてビデオプレーヤーを追加する

Unity プロジェクトの **プロジェクト** ウィンドウにビデオファイルをドラッグします。 [このビデオ](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true)は、空間オーディオサンプルプロジェクトから使用できます。

![ビデオを含む Assets フォルダー](images/spatial-audio/assets-folder-with-video.png)

ビデオクリップの品質設定を調整すると、HoloLens 2 でスムーズに再生されるようになります。 **プロジェクト** ウィンドウでビデオファイルをクリックします。 次に、ビデオファイルの [ **インスペクター** ] ウィンドウで、Windows ストアアプリの設定を上書きし、次のようにします。
* **トランスコード** を有効にする
* **コーデック** を H264 に設定する
* **ビットレートモード** を低に設定
* **空間品質** を中程度に設定する

これらの調整が完了すると、ビデオファイルの [ **インスペクター** ] ウィンドウは次のようになります。

![ビデオのプロパティウィンドウ](images/spatial-audio/video-property-pane.png)

次に、[ **階層** ] ウィンドウを右クリックし、[ **ビデオ > ビデオプレーヤー** ] を選択して、 **階層** に **video player** オブジェクトを追加します。

![階層内のビデオプレーヤー](images/spatial-audio/video-player-in-hierarchy.png)

## <a name="play-video-onto-a-quadrangle"></a>ビデオを quadrangle に再生する
**Video Player** オブジェクトには、ビデオをレンダリングするためのテクスチャを使用するゲームオブジェクトが必要です。 まず、[ **階層** ] ペインを右クリックし、[ **3d オブジェクト-> クワッド** ] を選択して、 **階層** に **クワッド** を追加します。

![クワッドを階層に追加](images/spatial-audio/add-quad-to-hierarchy.png)

アプリケーションの起動時にユーザーの前に **quad** が表示されるようにするには、 **quad** の **Position** プロパティを (0, 0, 2) に設定し、 **Scale** プロパティを (1.28, 0.72, 1) に設定します。 これらの変更が完了すると、 **4** つ目の **インスペクター** ウィンドウの [ **変換** ] コンポーネントは次のようになります。

![クワッド変換](images/spatial-audio/quad-transform.png)

ビデオで **Quad** のテクスチャを作成するには、新しい **レンダリングテクスチャ** を作成します。 [ **プロジェクト** ] ウィンドウで、右クリックし、[ **作成-> レンダリングテクスチャ** ] を選択します。

![描画テクスチャを作成する](images/spatial-audio/create-render-texture.png)

**レンダリングテクスチャ** の [ **インスペクター** ] ウィンドウで、ビデオのネイティブ解像度である 1280 0x720 と一致するように **Size** プロパティを設定します。 次に、HoloLens 2 で適切なレンダリングパフォーマンスを確保するために、[ **深度バッファー** ] プロパティを **16 ビット以上の深さ** に設定します。 これらの設定の後、 **レンダリングテクスチャ** の [ **インスペクター** ] ウィンドウは次のようになります。

![テクスチャのプロパティを表示する](images/spatial-audio/render-texture-properties.png)

次に、新しい **レンダリングテクスチャ** を **4** 番目のテクスチャとして使用します。
1. [ **プロジェクト** ] ウィンドウから、 **階層** 内の **クワッド** に **レンダリングテクスチャ** をドラッグします。
2. HoloLens 2 で良好なパフォーマンスを得るには、 **クワッド** の [ **インスペクター** ] ウィンドウで、 **Mixed Reality Toolkit Standard Shader** を選択します。

これらの設定を使用すると、 **クワッド** の [ **インスペクター** ] ウィンドウの **テクスチャ** コンポーネントは次のようになります。

![クワッドテクスチャのプロパティ](images/spatial-audio/quad-texture-properties.png)

新しい **ビデオプレーヤー** を設定し、ビデオクリップを再生するために **テクスチャをレンダリング** するには、 **ビデオプレーヤー** の [ **インスペクター** ] ウィンドウを開き、次のようにします。
* ビデオ **クリップ** のプロパティをビデオファイルに設定します。
* **ループ** チェックボックスをオンにする
* **ターゲットテクスチャ** を新しいレンダリングテクスチャに設定する

**ビデオプレーヤー** の [ **インスペクター** ] ウィンドウは次のようになります。

![ビデオプレーヤーのプロパティ](images/spatial-audio/video-player-properties.png)

## <a name="spatialize-the-audio-from-the-video"></a>ビデオからオーディオを Spatialize
**クワッド** の [ **インスペクター** ] ウィンドウで、ビデオからオーディオをルーティングする **オーディオソース** を作成します。
* ペインの下部にある [ **コンポーネントの追加** ] をクリックします。
* **オーディオソース** を追加する

次に、 **オーディオソース** で次のようにします。
* ミキサーに **出力** を設定する
* [ **Spatialize** ] チェックボックスをオンにします。
* [ **空間ブレンド** ] スライダーを 1 (3d) に移動します。

これらの変更が完了すると、 **diag** ペインの [ **インスペクター** ] ウィンドウの [ **オーディオソース** ] コンポーネントは次のようになります。

![クワッドオーディオソースインスペクター](images/spatial-audio/quad-audio-source-inspector.png)

**ビデオプレーヤー** が、そのオーディオを **クワッド** の **オーディオソース** にルーティングするように設定するには、 **ビデオプレーヤー** の [ **インスペクター** ] ウィンドウを開き、次のようにします。
* **オーディオ出力モード** を ' audio Source ' に設定します
* [ **オーディオソース** のプロパティを Quad に設定する

これらの変更が完了すると、 **ビデオプレーヤー** の [ **インスペクター** ] ウィンドウは次のようになります。

![ビデオプレーヤー設定オーディオソース](images/spatial-audio/video-player-set-audio-source.png)

## <a name="next-steps"></a>次のステップ
HoloLens 2 または Unity エディターでアプリを試してみてください。 ビデオが表示され、再生されます。ビデオのオーディオは spatialized になります。

> [!div class="nextstepaction"]
> [章4](unity-spatial-audio-ch4.md) 

