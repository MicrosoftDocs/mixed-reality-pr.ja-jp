---
title: MRTK 101 - 基本的な対話式操作に Mixed Reality Toolkit Unity を使用する方法 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)
description: 基本的な対話式操作に Mixed Reality Toolkit Unity を使用する方法 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)
author: cre8ivepark
ms.author: dongpark
ms.date: 08/27/2019
ms.topic: article
keywords: HoloLens, MRTK, Mixed Reality Toolkit, Windows Mixed Reality, 設計, サンプル アプリ, コントロール
ms.localizationpriority: high
ms.openlocfilehash: bd0b3104d48ce3fbd836e7294ab5b816a486847a
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91701039"
---
# <a name="mrtk-101-how-to-use-mixed-reality-toolkit-unity-for-basic-interactions-hololens-2-hololens-windows-mixed-reality-openvr"></a>MRTK 101: 基本的な対話式操作に Mixed Reality Toolkit Unity を使用する方法 (HoloLens 2、HoloLens、Windows Mixed Reality、Open VR)

![MRTK](images/MRTK101/MRTK101Cover.png)

MRTK を使用して、Mixed Reality で最も広く使用されている一般的な対話式操作パターンを実現する方法について説明します。

- Unity エディターで入力の対話式操作をシミュレートする方法
- オブジェクトをつかんで動かす方法
- オブジェクトのサイズを変更する方法
- 正確にオブジェクトを動かしたり回転させたりする方法
- オブジェクトを入力イベントに応答させる方法
- 視覚的なフィードバックを追加する方法
- 音声によるフィードバックを追加する方法
- HoloLens 2 のスタイル ボタン プレハブを使用する方法
- オブジェクトが自分の後をついてくるようにする方法
- オブジェクトが自分の方を向くようにする方法

## <a name="how-to-simulate-input-interactions-in-unityeditor"></a>Unity エディターで入力の対話式操作をシミュレートする方法
MRTK では、エディター内入力シミュレーションがサポートされています。 単に、Unity の [Play]\(再生\) ボタンをクリックして、シーンを実行します。 入力をシミュレートするには、次のキーを使用します。
カメラを動かすには、W、A、S、D のキーを押します。
周囲を見回すには、マウスの右ボタンを押したまま、マウスを動かします。
シミュレートされたハンドを表示するには、スペース キー (右手) または左側の Shift キー (左手) を押します。シミュレートされたハンドを表示したままにするには、T または Y キーを押します。シミュレートされたハンドを回転させるには、Q または E (水平方向)/R または F (垂直方向) を押します。

- [入力シミュレーションの詳細については、MRTK のドキュメントを参照してください](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/InputSimulation/InputSimulationService.html)


## <a name="how-to-grab-and-move-anobject"></a>オブジェクトをつかんで動かす方法
オブジェクトをつかめるようにするには、次の 2 つのスクリプトを割り当てます。ManipulationHandler.cs と NearInteractionGrabbable.cs(多関節ハンド トラッキング入力を使用して直接つかむ)。ManipulationHandler では、近くと遠くの両方の対話式操作がサポートされています。 オブジェクトをつかんで動かすには、HoloLens 2 の多関節ハンド トラッキング入力 (近く)、ハンド レイ (遠く)、モーション コントローラーのビーム (遠く)、HoloLens の視線カーソルとエアタップ (遠く) を使用できます。

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_ManipulationHandler.png">

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object for grab and move" width="800" src="images/MRTK101/MRTK_GrabMove.gif">


## <a name="how-to-resize-anobject"></a>オブジェクトのサイズを変更する方法
ManipulationHandler.cs では、両手のスケーリング/回転がサポートされています。 これは、HoloLens 2 の多関節ハンド入力、HoloLens 1 の視線入力とジェスチャ入力、Windows Mixed Reality のイマーシブ ヘッドセットのモーション コントローラー入力など、さまざまな入力の種類で機能します。

- [操作ハンドラーの詳細については、MRTK のドキュメントを参照してください](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ManipulationHandler.html)

<img alt="NearInteractionGrabbable and ManipulationHandler.cs assigned to an object for manipulation" width="800" src="images/MRTK101/MRTK_ManipulationHandler.gif">

## <a name="how-to-move-or-rotate-an-object-with-precision"></a>正確にオブジェクトを動かしたり回転させたりする方法
オブジェクトをスケーリングしたり回転させたりするためのインターフェイスである境界ボックスを使用するには、BoundingBox.cs をオブジェクトに割り当てます。 既定では、HoloLens 1 スタイルの青いハンドルとワイヤが表示されます。 HoloLens 2 スタイルの近接度に基づくアニメーション ハンドルを使用するには、プレハブとマテリアルを割り当てる必要があります。 構成の詳細については、[境界ボックスのドキュメント](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)と BoundingBoxExamples.unity シーンを参照してください。

<img alt="BoundingBox.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_BoundingBox.png">

<img alt="BoundingBox.cs assigned to an object gif" width="800" src="images/MRTK101/MRTK_BoundingBox.gif">


- [境界ボックスの詳細については、MRTK のドキュメントを参照してください](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)

## <a name="how-to-make-an-object-respond-to-inputevents"></a>オブジェクトを入力イベントに応答させる方法
PointerHandler.cs をオブジェクトに割り当てます。 インスペクターでは、OnPointerDown()、OnPointerUp()、OnPointerClicked()、OnPointerDragged() のイベントを使用できます。これらのイベントをスクリプトで使用するには、IMixedRealityPointerHandler を実装します。

<img alt="PointerHandler.cs assigned to an object image" width="800" src="images/MRTK101/MRTK_PointerHandler.png">

- [入力システムの詳細については、MRTK のドキュメントを参照してください](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Overview.html)

## <a name="how-to-add-visual-feedback"></a>視覚的なフィードバックを追加する方法
Interactable.cs をオブジェクトに割り当てます。 インスペクターで、新しいテーマを作成します。 Interactable のテーマ プロファイルを使用すると、利用可能なすべての入力対話式操作状態に視覚的なフィードバックを簡単に追加できます。

<img alt="Image of PointerHandler.cs assigned to an object" width="800" src="images/MRTK101/MRTK_Interactable.png">

<img alt="Interactable gif" width="800" src="images/MRTK101/MRTK_Interactable.gif">


Interactable には、対話式操作状態ごとにシェーダーのプロパティを制御できるようにするシェーダー テーマを含め、さまざまな種類のテーマが用意されています。

- [Interactable の詳細については、MRTK のドキュメントを参照してください](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html)

視覚的なフィードバックのもう 1 つの重要な構成要素は、MRTK 標準シェーダーです。 MRTK 標準シェーダーを使用すると、ホバー ライトや近接ライトなどの視覚的なフィードバック効果を簡単に追加できます。 MRTK 標準シェーダーで実行される計算は、Unity 標準シェーダーより大幅に少ないため、効率の良いエクスペリエンスを作成できます。

新しいマテリアルを作成し、[Shader]\(シェーダー\) で [Mixed Reality Toolkit] > [Standard]\(標準\) の順に選択します。 あるいは、MRTK 標準シェーダーを使用する既存のマテリアルのいずれかを選択することもできます。

<img alt="MRTK Standard Shader image 1" width="400" src="images/MRTK101/MRTK_Shader0.png">
<br/><br/>
<img alt="MRTK Standard Shader image 2" width="800" src="images/MRTK101/MRTK_Shader1.png">

<img alt="MRTK Standard Shader image 3" width="800" src="images/MRTK101/MRTK_Shader.gif">


- [MRTK 標準シェーダーの詳細については、MRTK のドキュメントを参照してください](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_MRTKStandardShader.html)

## <a name="how-to-add-audio-feedback"></a>音声によるフィードバックを追加する方法
AudioSource をオブジェクトに追加します。 次に、入力イベントを公開するスクリプト (例: Interactable.cs や PointerHandler.cs) で、オブジェクトをイベントに割り当て、AudioSource.PlayOneShot() を選択します。 自分のオーディオ クリップを使用することも、MRTK のオーディオ アセットのいずれかを選択することもできます。

<img alt="Audio Source assigned to an object. AudioSource.PlayOneShot configured in the Interactable's OnPress() and OnRelease() events." width="800" src="images/MRTK101/MRTK_Audio.png">

## <a name="how-to-use-hololens-2-style-buttonprefabs"></a>HoloLens 2 のスタイル ボタン プレハブを使用する方法
MRTK には、さまざまな種類の HoloLens 2 のシェル (OS) スタイル ボタンが用意されています。 これは、近接ライト、圧縮ボックス、リップル効果などの洗練されたビジュアル フィードバックをボタン表面に提供します。

<img alt="Interactable button" width="800" src="images/MRTK101/MRTK_Button.gif">

単純に、HoloLens 2 スタイル押しボタン プレハブをシーンにドラッグ アンド ドロップします。 プレハブでは、上記で導入された Interactable.cs が使用されます。 Interactable で OnClick() などの公開されたイベントを使用してアクションをトリガーできます。

<img alt="HoloLens 2 Button Prefab" width="800" src="images/MRTK101/MRTK_Button.png">

- [Button プレハブの詳細については、MRTK のドキュメントを参照してください](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Button.html)

## <a name="how-to-make-an-object-followyou"></a>オブジェクトが自分の後をついてくるようにする方法
RadialView.cs スクリプトをオブジェクトに割り当てます。 これは、Solver スクリプト シリーズの一部です。これを使用すると、3D 空間に配置されているさまざまな種類のオブジェクトを実現することができます。 SolverHandler.cs は自動的に追加されます。
次に示すのは、HoloLens シェルの [スタート] メニューと同様に、"lazy follow" Tag-along 動作を実現する RadialView 構成の例です。 最小/最大の距離と最小/最大の表示角度を指定できます。 次の例は、0.4m と 0.8m の範囲で 15°以内のオブジェクトの配置を示しています。 Lerp 時間の値を調整して、位置指定の更新を速くしたり遅くしたりします。

<img alt="MRTK Standard Shader for solver" width="400" src="images/MRTK101/MRTK_SolverRadialView.png">

<img alt="Interactable radial solver" width="800" src="images/MRTK101/MRTK_RadialViewSolver.gif">

- [ソルバーの詳細については、MRTK のドキュメントを参照してください](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html)

## <a name="how-to-make-an-object-faceyou"></a>オブジェクトが自分の方を向くようにする方法
Billboard.cs スクリプトをオブジェクトに割り当てます。 これは、ユーザーの位置に関係なく、常にユーザーの方を向きます。 ピボット軸オプションを指定できます。

<img alt="Image of Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.png">

<img alt="Billboard.cs script assigned to an object with Pivot Axis option Y" width="800" src="images/MRTK101/MRTK_Billboard.gif">


Mixed Reality の素晴らしいエクスペリエンスを作成する準備はできましたか。 MRTK と Mixed Reality の詳細については、以下のページをご覧ください。

## <a name="about-the-author"></a>筆者について

<table style="border-collapse:collapse" padding-left="0px">
<tr>
<td style="border-style: none" width="60px"><img alt="Picture of Dong Yoon Park" width="60" height="60" src="images/dongyoonpark.jpg"></td>
<td style="border-style: none"><b>Dong Yoon Park</b><br>UX デザイナー @Microsoft</td>
</tr>
</table>

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

私たちが用意した Unity 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。 ここから、次の構成要素に進むことができます。 

> [!div class="nextstepaction"]
> [カメラ](camera-in-unity.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [共有エクスペリエンス](shared-experiences-in-unity.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目

* [Mixed Reality Toolkit-Unity (MRTK) GitHub](https://github.com/Microsoft/MixedRealityToolkit-Unity)
* [MRTK ドキュメント ポータル](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html)
* [MRTK の概要](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html)
* [HoloToolkit から MRTK への移植ガイドライン](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/HTKToMRTKPortingGuide.html)
