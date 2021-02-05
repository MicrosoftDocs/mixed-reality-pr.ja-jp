---
title: 空間オーディオチュートリアル-3. ビデオからオーディオの立体化
description: ビデオ資産を Unity プロジェクトにインポートし、ビデオからオーディオを spatialize します。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、ヘッド関連の転送機能、リバーブ、Microsoft Spatializer、ビデオのインポート、ビデオプレーヤー
ms.openlocfilehash: 876918c3e886fae6cd2066d84c55a6e158e4c773
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590054"
---
# <a name="3-spatializing-audio-from-a-video"></a>3.ビデオからオーディオの立体化

## <a name="overview"></a>概要

このチュートリアルでは、ビデオソースからオーディオを spatialize し、unity エディターと HoloLens 2 でこれをテストする方法について説明します。

## <a name="objectives"></a>目標

* ビデオをインポートしてビデオプレーヤーを追加する
* ビデオを quadrangle に再生する
* オーディオをビデオから quadrangle にルーティングし、オーディオを spatialize する

## <a name="import-a-video-and-add-a-video-player-to-the-scene"></a>ビデオをインポートし、ビデオプレーヤーをシーンに追加する

このチュートリアルでは、空間オーディオサンプルプロジェクトの [このビデオ](https://github.com/microsoft/spatialaudio-unity/blob/develop/Samples/MicrosoftSpatializerSample/Assets/Microsoft%20HoloLens%20-%20Spatial%20Sound-PTPvx7mDon4.mp4?raw=true) を使用します。

Unity プロジェクトにビデオをインポートします。 Unity メニューで、[**資産**] [  >  **新しい資産のインポート**] [ 
 ![ 資産のインポート] を選択します。](images/spatial-audio/spatial-audio-03-section1-step1-1.png)

[ **新しい資産のインポート** ] ウィンドウで、ダウンロードした **Microsoft HoloLens の PTPvx7mDon4** ファイルを選択し、[ **開く** ] ボタンをクリックして、プロジェクトにアセットをインポートします。

![資産の選択](images/spatial-audio/spatial-audio-03-section1-step1-2.png)

ビデオクリップの品質設定を調整すると、HoloLens 2 でスムーズに再生されるようになります。 [**プロジェクト**] ウィンドウでビデオファイルを選択し、ビデオファイルの [インスペクター] ウィンドウで、 **Windows ストアアプリ** の設定を **上書き** して、次のようにします。

* **トランスコード** を有効にする
* **コーデック** を H264 に設定する
* **ビットレートモード** を低に設定
* **空間品質** を中程度に設定する

これらの調整が完了したら、[適用] をクリックして、ビデオクリップの品質設定を変更します。

![ビデオのプロパティの変更](images/spatial-audio/spatial-audio-03-section1-step1-3.png)

階層を右クリックし、[ビデオビデオプレーヤー]**を選択し** て、  >  ビデオプレーヤーコンポーネントを追加します。

![ビデオプレーヤーの追加](images/spatial-audio/spatial-audio-03-section1-step1-4.png)

## <a name="play-video-onto-a-quadrangle"></a>ビデオを quadrangle に再生する

ビデオをレンダリングするには、 **ビデオプレーヤー** オブジェクトにテクスチャを表示するゲームオブジェクトが必要です。

階層を右クリックし、[ **3d オブジェクト** quad] を選択し  >  て quad を作成し、**変換** コンポーネントを次のように構成します。

* **位置**: X = 0、Y = 0、Z = 2
* **回転**:X = 0、Y = 0、Z = 0
* **小数点以下桁数**: X = 1.28、Y = 0.72、Z = 1

![クワッドを追加する](images/spatial-audio/spatial-audio-03-section2-step1-1.png)

ここで、ビデオを使用して **クワッド** のテクスチャを **作成** し、[**プロジェクト**] ウィンドウで右クリックして [レンダリングテクスチャの作成] を選択し、レンダリングテクスチャコンポーネントを  >  作成します。次に、レンダリングテクスチャに適切な名前を入力します。たとえば、「_空間オーディオテクスチャ_:

![描画テクスチャを作成する](images/spatial-audio/spatial-audio-03-section2-step1-2.png)

**レンダリングテクスチャ** を選択し、[インスペクター] ウィンドウで、ビデオのネイティブ解像度である 1280 0x720 と一致するように **Size** プロパティを設定します。 次に、HoloLens 2 で適切なレンダリングパフォーマンスを確保するために、[ **深度バッファー** ] プロパティを **16 ビット以上の深さ** に設定します。

![テクスチャのプロパティを表示する](images/spatial-audio/spatial-audio-03-section2-step1-3.png)

次に、作成したレンダーテクスチャ **空間オーディオテクスチャ** を **Quad** のテクスチャとして使用します。

1. **空間オーディオテクスチャ** を [**プロジェクト**] ウィンドウから階層内の **クワッド** にドラッグして、レンダーテクスチャをクワッドに追加します。
2. HoloLens 2 でパフォーマンスを向上させるには、階層で [クワッド] を選択し、[シェーダー] の [インスペクター] ウィンドウで **Mixed Reality Toolkit**  >  **Standard** shader を選択します。

![クワッドテクスチャのプロパティ](images/spatial-audio/spatial-audio-03-section2-step1-4.png)

ビデオ **プレーヤー** を設定し、ビデオ **クリップを再生するに** は、**階層** 内で **ビデオプレーヤー** を選択し、[**インスペクター** ] ウィンドウで

* **ビデオクリップ** のプロパティを、ダウンロードしたビデオファイル ' Microsoft HoloLens-PTPvx7mDon4 ' に設定します
* **ループ** チェックボックスをオンにする
* **ターゲットテクスチャ** を新しいレンダリングテクスチャ **空間オーディオテクスチャ** に設定します

![ビデオプレーヤーのプロパティ](images/spatial-audio/spatial-audio-03-section2-step1-5.png)

## <a name="spatialize-the-audio-from-the-video"></a>ビデオからオーディオを Spatialize

[階層] ウィンドウで [ **Quad** オブジェクト] を選択し、[インスペクター] ウィンドウで [ **コンポーネントの追加** ] ボタンを使用して、ビデオからオーディオをルーティングする **オーディオソース** を追加します。

**オーディオソース**:

* **空間オーディオミキサー** に **出力** を設定する
* [ **Spatialize** ] チェックボックスをオンにします。
* [ **空間ブレンド** ] スライダーを 1 (3d) に移動します。

![クワッドオーディオソースインスペクター](images/spatial-audio/spatial-audio-03-section3-step1-1.png)

オーディオを **オーディオソース** にルーティングするようにビデオプレーヤーを設定するには、[階層] ウィンドウで **ビデオプレーヤー** を選択し、インスペクターのビデオプレーヤーオブジェクトで次の変更を行います。

* オーディオ **出力モード** を **オーディオソース** に設定する
* **Audio Source** プロパティを **クワッド** に設定します。

![ビデオプレーヤー設定オーディオソース](images/spatial-audio/spatial-audio-03-section3-step1-2.png)

> [!TIP]
> HoloLens 2 に Unity プロジェクトをビルドして配置する方法を再確認するには、[HoloLens 2 にアプリをビルドする](mr-learning-base-02.md#building-your-application-to-your-hololens-2)手順に関する記事を参照してください。

## <a name="congratulations"></a>結論

このチュートリアルでは、ビデオソースからオーディオを spatialize して、HoloLens 2 または Unity エディターでアプリを試してみる方法について学習しました。 ビデオが表示されます。ビデオのオーディオは spatialized です。

次のチュートリアルでは、実行時に spatialization を有効または無効にする方法について学習します。

> [!div class="nextstepaction"]
> [次のチュートリアル: 4. 実行時に spatialization を有効または無効にする](unity-spatial-audio-ch4.md)
