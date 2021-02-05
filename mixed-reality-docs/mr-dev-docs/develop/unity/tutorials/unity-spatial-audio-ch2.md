---
title: 空間オーディオチュートリアル-2. ボタンの対話式操作サウンドの立体化
description: ボタンをプロジェクトに追加し、ボタンの相互作用サウンドを spatialize します。
author: kegodin
ms.author: v-hferrone
ms.date: 02/05/2021
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、ヘッド関連の転送関数、リバーブ、Microsoft Spatializer、prefabs、volume curve
ms.openlocfilehash: 12d159cb162cbf136483f7be94b0d297319a0737
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590764"
---
# <a name="2-spatializing-button-interaction-sounds"></a>2.ボタンの対話式操作サウンドの立体化

## <a name="overview"></a>概要

このチュートリアルでは、ボタンの相互作用音を spatialize する方法と、オーディオクリップを使用して spatialized ボタンの対話をテストする方法について説明します。  

## <a name="objectives"></a>目標

* ボタンのクリック音を追加して Spatialize

## <a name="add-a-button"></a>ボタンを追加する

Prefab ボタンを追加するには、[ **プロジェクト** ] ウィンドウで [ **パッケージ** ] を選択し、検索バーに「PressableButtonHoloLens2」と入力します。

![アセット内のボタンの事前 fab](images/spatial-audio/spatial-audio-02-section1-step1-1.png)

ボタン prefab は、青いアイコンで表されるエントリです。 **PressableButtonHoloLens2** prefab をクリックして階層にドラッグします。 **PressableButtonHoloLens2** オブジェクトを選択した状態で、[インスペクター] ウィンドウで、**変換** コンポーネントを次のように構成します。

* **位置**: X = 0、Y =-0.4、Z = 2
* **回転**:X = 0、Y = 0、Z = 0
* **スケール**:X = 1、Y = 1、Z = 1

![ボタンの変換](images/spatial-audio/spatial-audio-02-section1-step1-2.png)

シーン内のオブジェクトに焦点を当てるには、 **PressableButtonHoloLens2** オブジェクトをダブルクリックして、もう一度少しズームします。

## <a name="spatialize-button-feedback"></a>Spatialize button のフィードバック

この手順では、ボタンの音声フィードバックを spatialize します。 関連する設計の提案については、「 [空間サウンドの設計](../../../design/spatial-sound-design.md)」を参照してください。

オーディオ **ミキサー** ウィンドウでは、**オーディオソース** コンポーネントからのオーディオ再生用に、**ミキサーグループ** と呼ばれる宛先を定義します。

[**オーディオミキサー** ] ウィンドウを開くには、Unity メニューで [ **window**  >  **audio**  >  **audio mixer**: ![ open audio ミキサ window] を選択します。](images/spatial-audio/spatial-audio-02-section2-step1-1.png)

 ミキサーの **横にある**[+] をクリックし、[_空間オーディオミキサー_] などの適切な名前をミキサーに入力して、**ミキサー** を作成します。 新しいミキサーには、 **Master** という名前の既定の **グループ** が含まれます。

![最初のミキサーがあるミキサーパネル](images/spatial-audio/spatial-audio-02-section2-step1-2.png)

> [!NOTE]
> 5番目の章でリバーブが有効になるまで [: リバーブを使用して空間オーディオに距離を追加する](unity-spatial-audio-ch5.md)まで、ミキサーのボリュームメーターには、Microsoft Spatializer で再生されるサウンドのアクティビティが表示されません。

[階層] ウィンドウで **PressableButtonHoloLens2** を選択し、[インスペクター] ウィンドウで **オーディオソース** コンポーネントを見つけて、次のようにオーディオソースコンポーネントを構成します。

1. [ **出力** ] プロパティで、セレクターをクリックし、作成した **ミキサー** を選択します。
2. **Spatialize** チェックボックスをオンにします。
3. [ **空間 Blend** ] スライダーを 3d (1) に移動します。

![ボタンオーディオソース](images/spatial-audio/spatial-audio-02-section2-step1-3.png)

> [!NOTE]
> **Spatialize** チェックボックスをオフにして **空間ブレンド** を 1 (3d) に移動すると、Unity では、 **Microsoft spatializer** と hrtfs ではなく、そのパン spatializer が使用されます。

## <a name="adjust-the-volume-curve"></a>ボリューム曲線を調整する

既定では、Unity はリスナーから遠く離れた spatialized サウンドを減衰します。 この減衰が相互作用フィードバックのサウンドに適用されると、インターフェイスの使用が困難になる可能性があります。

この減衰を無効にするには、**オーディオソース** コンポーネントの **ボリューム** 曲線を調整する必要があります。

[階層] ウィンドウで **PressableButtonHoloLens2** を選択し、[インスペクター] ウィンドウで [**オーディオソース** 3d のサウンド設定] に移動して、次のように  >  構成します。

1. ボリュームの **ロール** アウトプロパティを線形ロールオフに設定します
2. Y 軸の "0" から "1" までの **ボリューム** 曲線 (赤の曲線) のエンドポイントをドラッグします。
3. **ボリューム** 曲線の形状をフラットに調整するには、[白い曲線図形] コントロールを [X 軸] に平行にドラッグします。

![Button 3D サウンド設定](images/spatial-audio/spatial-audio-02-section3-step1-1.png)

## <a name="testing-the-spatialize-audio"></a>Spatialize オーディオのテスト

Unity エディターで spatialize オーディオをテストするには、 **PressableButtonHoloLens2** オブジェクトで [**ループ**] オプションがオンになっているオーディオ **ソース** コンポーネントにオーディオクリップを追加する必要があります。

Play モードでは、 **PressableButtonHoloLens2** オブジェクトを左から右に移動し、ワークステーションで空間オーディオが有効になっているか、使用されていない状態で比較します。 次の方法で、テスト用のオーディオソース設定を変更することもできます。

* 0-1 (2D spatialized と 3D spatialized sound) 間の **空間ブレンド** プロパティの移動
* **Spatialize** プロパティをチェックしてオフにする

HoloLens 2 でアプリを試してみてください。 アプリでは、ボタンをクリックすると、spatialized ボタンの相互作用音が聞こえます。

> [!TIP]
> HoloLens 2 に Unity プロジェクトをビルドして配置する方法を再確認するには、[HoloLens 2 にアプリをビルドする](mr-learning-base-02.md#building-your-application-to-your-hololens-2)手順に関する記事を参照してください。

## <a name="congratulations"></a>結論

このチュートリアルでは、ボタンの相互作用音を spatialize、オーディオクリップを使用して spatialized ボタンの対話をテストする方法について学びました。 次のチュートリアルでは、ビデオソースからオーディオを spatialize する方法について説明します。

> [!div class="nextstepaction"]
> [次のチュートリアル: ビデオからの Spatializing オーディオ](unity-spatial-audio-ch3.md)
