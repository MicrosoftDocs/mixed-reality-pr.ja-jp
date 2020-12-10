---
title: Unity のカメラ
description: Windows Mixed Reality 開発に Unity のメインカメラを使用して holographic のレンダリングを実行する方法について説明します。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、holographic レンダリング、holographic、イマーシブ、フォーカスポイント、深度バッファー、方向専用、位置指定、不透明、透明、クリップ、混合 reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実ヘッドセット
ms.openlocfilehash: 26eb8966004c958c6063d09de891ef835d973a82
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010433"
---
# <a name="camera-in-unity"></a>Unity のカメラ

Mixed reality ヘッドセットを使用すると、holographic 世界の中心になります。 Unity [カメラ](https://docs.unity3d.com/Manual/class-Camera.html) コンポーネントは、ステレオスコピックのレンダリングを自動的に処理し、ヘッドの動きと回転に従います。 ただし、ビジュアルの品質とホログラムの [安定性](../platform-capabilities-and-apis/hologram-stability.md)を完全に最適化するには、以下で説明するカメラの設定を設定する必要があります。

## <a name="setup"></a>セットアップ

1. **Windows ストアプレーヤー設定** の [**その他の設定**] セクションに進む
2. Windows **Mixed Reality** をデバイスとして選択します。これは、以前のバージョンの Unity では **windows Holographic** として一覧表示される場合があります。
3. **サポートされている仮想現実** を選択

>[!NOTE]
>これらの設定は、アプリの各シーンのカメラに適用する必要があります。
>
>既定では、Unity で新しいシーンを作成すると、カメラコンポーネントを含むメインのカメラのユーザーオブジェクトが階層に含まれますが、次の設定は適切に適用されません。

## <a name="holographic-vs-immersive-headsets"></a>Holographic とイマーシブヘッドセット

Unity カメラコンポーネントの既定の設定は、従来の3D アプリケーション用です。実際の環境がないため、スカイボックスのような背景が必要です。

* **[イマーシブヘッドセット](../../discover/immersive-headset-hardware-details.md)** で実行すると、ユーザーに表示されるすべてのものが表示されるため、スカイボックスを保持することをお勧めします。
* ただし、 [HoloLens](../../hololens-hardware-details.md)などの **holographic ヘッドセット** で実行する場合、カメラがレンダリングするすべての要素の背後に実際の世界が表示されます。 スカイボックステクスチャの代わりに、カメラの背景を透明に設定します (HoloLens では、黒は透明としてレンダリングされます)。
    1. [階層] パネルでメインカメラを選択します。
    2. [インスペクター] パネルでカメラコンポーネントを見つけて、[クリアフラグ] ドロップダウンを [スカイボックス] から [純色] に変更します。
    3. 背景色ピッカーを選択し、RGBA 値を (0, 0, 0, 0) に変更します。

スクリプトコードを使用して、HolographicSettings をチェックすることによって、ヘッドセットがイマーシブであるか holographic であるかを実行時に判断することができ[ます。](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.IsDisplayOpaque.html)

## <a name="positioning-the-camera"></a>カメラの配置

ユーザーの開始位置を (X: 0, Y: 0, Z: 0) と考えると、アプリのレイアウトが簡単になります。 メインカメラはユーザーのヘッドの移動を追跡しているため、ユーザーの開始位置を設定することによって、メインカメラの開始位置を設定できます。

1. [階層] パネルの [メインカメラ] を選択します。
2. [インスペクター] パネルで変換コンポーネントを見つけ、位置を (X: 0, Y: 1, Z:-10) から (X: 0, Y: 0, Z: 0) に変更します。

   ![Unity の [インスペクター] ウィンドウの [カメラ]](images/maincamera-350px.png)  
   *Unity の [インスペクター] ウィンドウの [カメラ]*

## <a name="clip-planes"></a>クリッププレーン

ユーザーに近いコンテンツのレンダリングは、mixed reality で不快に感じられる可能性があります。 カメラコンポーネントでは、 [近距離と遠くのクリップ平面](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances) を調整できます。

1. [階層] パネルでメインカメラを選択します。
2. [インスペクター] パネルでカメラコンポーネントのクリッピング平面を見つけ、[Near] ボックスを0.3 から0.85 に変更します。 さらに近いコンテンツは、ユーザーの不快感につながる可能性があります。 [レンダリング距離のガイドライン](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)に従って回避する必要があります。

## <a name="multiple-cameras"></a>複数のカメラ

シーンに複数のカメラコンポーネントがある場合、Unity は、どのステレオスコピックオブジェクトに MainCamera タグがあるかに基づいて、レンダリングとヘッドトラッキングに使用するカメラを認識します。

## <a name="recentering-a-seated-experience"></a>装着済みエクスペリエンスを入力する

[固定スケールのエクスペリエンス](../../design/coordinate-systems.md)を構築している場合は、XR を呼び出すことによって、ユーザーの現在の位置に Unity の recenter を持たせることができ **[ます。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** メソッド。

## <a name="reprojection-modes"></a>再プロジェクションモード

HoloLens とイマーシブヘッドセットはどちらも、photons が出力されたときにユーザーの実際のヘッド位置の misprediction を調整するために、アプリがレンダリングする各フレームを再プロジェクトします。

既定では:

* アプリが特定のフレームに対して深度バッファーを提供する場合、**イマーシブヘッドセット** は位置指定リポジトリを処理します。 また、イマーシブヘッドセットは、位置と向きの両方で misprediction のホログラムを調整します。 深度バッファーが指定されていない場合、システムは mispredictions の向きのみを修正します。
* HoloLens のような **Holographic ヘッドセット** は、アプリが深度バッファーを提供するかどうかに関係なく、位置指定リポジトリを処理します。  レンダリングは、実際には安定した背景でスパースになることが多いため、HoloLens で深度バッファーを使用せずに位置指定リポジトリを使用できます。

固定本文でロックされたコンテンツ (たとえば、360度のビデオコンテンツ) を使用して[向きのみのエクスペリエンス](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)を構築していることがわかっている場合は、HolographicSettings を[HolographicReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)に設定することによってのみ、Reprojection モードを[ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html)に明示的に設定できます。

## <a name="sharing-your-depth-buffers-with-windows"></a>Windows での深度バッファーの共有

アプリの深度バッファーを Windows に共有すると、アプリは、レンダリングするヘッドセットの種類に基づいて、ホログラムの安定性の2つのブーストのうちの1つを提供します。

* **イマーシブヘッドセット** は、深度バッファーが提供されたときに位置指定再投影を処理し、位置と向きの両方で misprediction のホログラムを調整します。
* **Holographic ヘッドセット** には、いくつかの異なる方法があります。 HoloLens 1 は、深度バッファーが指定されると自動的に [フォーカスポイント](focus-point-in-unity.md) を選択し、ほとんどのコンテンツと交差する平面に沿ったホログラムの安定性を最適化します。 HoloLens 2 は、Depth LSR を使用してコンテンツを安定化します [(「解説」を参照してください)](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)。

Unity アプリで Windows に深度バッファーを提供するかどうかを設定するには、次のようにします。

1. [ **Edit**  >  **Project settings**  >  **Player**  >  **] ユニバーサル Windows プラットフォーム tab**  >  **XR settings**] にアクセスします。
2. [ **Windows Mixed REALITY SDK** ] 項目を展開します。
3. [ **深度バッファーの共有を有効にする** ] チェックボックスをオンまたはオフにします。  新しいプロジェクトでは、[深度バッファーの共有を有効にする] が既定でオンになっています。これは、この機能が Unity に追加され、アップグレードされた古いプロジェクトに対して既定ではオフになるためです。

深度バッファーを使用すると、メインカメラで Unity に設定した近距離および遠面を使用して、深度バッファーの正規化されたピクセルごとの深度値をメートル単位の距離に正確にマップできます。  通常の方法でレンダリングがハンドルの深さの値を渡す場合は、通常、ここで問題ありません。ただし、既存のカラーピクセルに対してを使用している間に深度バッファーに書き込む半透明のレンダリングパスは、再プロジェクションを混乱させる可能性があります。  レンダリングパスによって、最終的な深度ピクセルの多くが正確でない深さの値になることがわかっている場合は、[深度バッファーの共有を有効にする] をオフにすると、表示品質が向上する可能性があります。

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit"></a>混合 Reality ツールキットを使用した自動シーンおよびカメラ設定 

ステップ [バイステップ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) ガイドに従って Unity プロジェクトに Mixed Reality Toolkit を追加すると、プロジェクトが自動的に構成されます。 また、次のセクションのガイドを使用して、MRTK なしでプロジェクトを手動で構成することもできます。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

Unity の開発に関する体験に従っている場合は、MRTK コアのビルディングブロックを調べています。 ここから、次のビルディングブロックに進むことができます。

> [!div class="nextstepaction"]
> [視線入力](gaze-in-unity.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [共有エクスペリエンス](shared-experiences-in-unity.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目

* [ホログラムの安定性](../platform-capabilities-and-apis/hologram-stability.md)
* [MixedRealityToolkit メインカメラ。 prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
