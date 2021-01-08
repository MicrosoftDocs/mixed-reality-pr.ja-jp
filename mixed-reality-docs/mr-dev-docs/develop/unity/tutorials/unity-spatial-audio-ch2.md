---
title: ボタンの対話式操作サウンドの立体化
description: ボタンを追加し、混合現実アプリケーションでボタンの相互作用音を spatialize する方法について説明します。
author: kegodin
ms.author: v-hferrone
ms.date: 12/01/2019
ms.topic: article
keywords: mixed reality、unity、チュートリアル、hololens2、空間オーディオ、MRTK、mixed reality toolkit、UWP、Windows 10、HRTF、ヘッド関連の転送関数、リバーブ、Microsoft Spatializer、prefabs、volume curve
ms.openlocfilehash: 1f54ba8cab55ba375a6b1499796761ae02b03a02
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007362"
---
# <a name="spatializing-button-interaction-sounds"></a>ボタンの対話式操作サウンドの立体化

## <a name="objectives"></a>目標

HoloLens 2 チュートリアルの空間オーディオモジュールの2番目の章では、次のことを行います。
* ボタンを追加する
* ボタンのクリック音を Spatialize

## <a name="add-a-button"></a>ボタンを追加する

[ **プロジェクト** ] ウィンドウで、[ **資産** ] を選択し、検索バーに「PressableButtonHoloLens2」と入力します。

![アセット内のボタンの事前 fab](images/spatial-audio/button-prefab-in-assets.png)

ボタン prefab は、白いアイコンではなく、青いアイコンで表されるエントリです。 **PressableButtonHoloLens2** という名前の prefab を [**階層**] ペインにドラッグします。 新しいボタンの [ **インスペクター** ] ウィンドウで、[ **Position** ] プロパティを (0,-0.4, 2) に設定して、アプリケーションの起動時にユーザーの前に表示されるようにします。 ボタンの **変換** コンポーネントは次のようになります。

![ボタンの変換](images/spatial-audio/button-transform.png)

## <a name="spatialize-button-feedback"></a>Spatialize button のフィードバック

この手順では、ボタンの音声フィードバックを spatialize します。 関連する設計の提案については、「 [空間サウンドの設計](../../../design/spatial-sound-design.md)」を参照してください。 

オーディオ **ミキサー** ウィンドウでは、**オーディオソース** コンポーネントからのオーディオ再生用に **ミキサーグループ** と呼ばれる宛先を定義します。 
* メニューバーの [audio **> Audio ミキサー] >** を使用して、[**オーディオミキサー** ] ウィンドウを開きます。
* **ミキサー** の横にある [+] をクリックして、ミキサーを作成 **します。** 新しいミキサーには、 **Master** という名前の既定の **グループ** が含まれます。

**ミキサー** ウィンドウは次のようになります。

![最初のミキサーがあるミキサーパネル](images/spatial-audio/mixer-panel-with-first-mixer.png)

> [!NOTE]
> [5 章](unity-spatial-audio-ch5.md)のリバーブが有効になるまで、ミキサーのボリュームメーターには、Microsoft Spatializer で再生されるサウンドのアクティビティが表示されません。

[**階層**] ペインで **PressableButtonHoloLens2** をクリックします。 [ **インスペクター** ] ウィンドウで次のようにします。
1. **オーディオソース** コンポーネントを検索する
2. [ **出力** ] プロパティで、セレクターをクリックし、ミキサーを選択します。
3. **Spatialize** チェックボックスをオンにする
4. [ **空間 Blend** ] スライダーを 3d (1) に移動します。

> [!NOTE]
> 2019より前のバージョンの Unity では、[Spatialize] チェックボックスは、**オーディオソース** の [**インスペクター** ] ウィンドウの下部にあります。

これらの変更が完了すると、 **PressableButtonHoloLens2** の **オーディオソース** コンポーネントは次のようになります。

![ボタンオーディオソース](images/spatial-audio/button-audio-source.png)

> [!NOTE]
> **Spatialize** チェックボックスをオフにして **空間ブレンド** を 1 (3d) に移動すると、Unity では、 **Microsoft spatializer** と hrtfs ではなく、そのパン spatializer が使用されます。

## <a name="adjust-the-volume-curve"></a>ボリューム曲線を調整する

既定では、Unity はリスナーから遠く離れた spatialized サウンドを減衰します。 この減衰が相互作用フィードバックのサウンドに適用されると、インターフェイスの使用が困難になる可能性があります。

この減衰を無効にするには、 **ボリューム** 曲線を調整します。 **PressableButtonHoloLens2** の [**インスペクター** ] ウィンドウの [**オーディオソース**] コンポーネントには、[ **3d サウンド設定**] というセクションがあります。 そのセクション内:
1. ボリュームの **ロールロール** のプロパティを線形に設定する
2. Y 軸の "0" から "1" までの **ボリューム** 曲線 (赤の曲線) のエンドポイントをドラッグします。
3. **ボリューム** 曲線の形状をフラットに調整するには、[白い曲線図形] コントロールを [X 軸] に平行にドラッグします。

これらの変更が完了すると、 **PressableButtonHoloLens2** の **オーディオソース** プロパティの **3d サウンド設定** セクションは次のようになります。

![Button 3D サウンド設定](images/spatial-audio/button-3d-sound-settings.png)

## <a name="testing-the-spatialize-audio"></a>Spatialize オーディオのテスト

新しい spatialized ボタンの相互作用音を自由に試してください。

* Unity エディターでゲームモードに入る (理想的にはシーンのループオーディオサンプルを使用する)
* オーディオソースを持つオブジェクトを左から右へ移動し、空間オーディオを有効にした場合と比較した場合の比較を行います。 テストのオーディオソース設定を変更するには、次の方法があります。
    * 0-1 (2D spatialized と 3D spatialized sound) 間の空間ブレンドプロパティの移動
    * Spatialize プロパティをチェックしてオフにする

## <a name="next-steps"></a>次のステップ

HoloLens 2 または Unity エディターでアプリを試してみてください。 アプリでは、ボタンをタッチして、spatialized ボタンの相互作用音を聞くことができます。

Unity エディターでテストする場合は、スペースバーを押し、スクロールホイールを使用してスクロールし、ハンドシミュレーションをアクティブにします。 詳細については、 [Mrtk のドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene)を参照してください。

> [!div class="nextstepaction"]
> [章3](unity-spatial-audio-ch3.md)

