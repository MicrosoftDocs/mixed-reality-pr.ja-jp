---
title: Unity のカメラ
description: Windows Mixed Reality 開発に Unity のメインカメラを使用して holographic のレンダリングを実行する方法について説明します。
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit、mixedrealitytoolkit、mixedrealitytoolkit、holographic レンダリング、holographic、イマーシブ、フォーカスポイント、深度バッファー、方向専用、位置指定、不透明、透明、クリップ、混合 reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実ヘッドセット
ms.openlocfilehash: c3c470634e2c5c9445ae8c0a29621971de22a92b
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677621"
---
# <a name="camera-in-unity"></a>Unity のカメラ

Mixed reality ヘッドセットを使用すると、holographic 世界の中心になります。 Unity [カメラ](https://docs.unity3d.com/Manual/class-Camera.html) コンポーネントは、ステレオスコピックレンダリングを自動的に処理します。プロジェクトで "Windows Mixed reality" がデバイスとして選択されている場合 (Windows ストアプレーヤー設定の [その他の設定] セクション)、ヘッドの移動とローテーションに従います。 以前のバージョンの Unity では、"Windows Holographic" として表示される場合があります。

ただし、ビジュアルの品質とホログラムの [安定性](../platform-capabilities-and-apis/hologram-stability.md)を完全に最適化するには、以下で説明するカメラの設定を設定する必要があります。

>[!NOTE]
>これらの設定は、アプリの各シーンのカメラに適用する必要があります。
>
>既定では、Unity で新しいシーンを作成すると、カメラコンポーネントを含むメインのカメラのユーザーオブジェクトが階層に含まれますが、次の設定は適切に適用されません。

## <a name="holographic-vs-immersive-headsets"></a>Holographic とイマーシブヘッドセット

Unity カメラコンポーネントの既定の設定は、従来の3D アプリケーション用であり、実際の環境がないため、スカイボックスのような背景が必要です。

* **[イマーシブヘッドセット](../../discover/immersive-headset-hardware-details.md)** で実行すると、ユーザーに表示されるすべてのものが表示されるため、スカイボックスを保持することをお勧めします。
* ただし、 [HoloLens](../../hololens-hardware-details.md)などの **holographic ヘッドセット** で実行する場合、カメラがレンダリングするすべての要素の背後に実際の世界が表示されます。 これを行うには、スカイボックステクスチャではなく、カメラの背景を透明に設定します (HoloLens では、黒は透明としてレンダリングされます)。
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
2. [インスペクター] パネルでカメラコンポーネントのクリッピング平面を見つけ、[Near] ボックスを0.3 から. 85 に変更します。 さらに近いコンテンツは、ユーザーの不快感につながる可能性があります。 [レンダリング距離のガイドライン](../platform-capabilities-and-apis/hologram-stability.md#hologram-render-distances)に従って回避する必要があります。

## <a name="multiple-cameras"></a>複数のカメラ

シーンに複数のカメラコンポーネントがある場合、Unity は、どのステレオスコピックオブジェクトに MainCamera タグがあるかを確認することによって、レンダリングとヘッドトラッキングに使用するカメラを認識します。

## <a name="recentering-a-seated-experience"></a>装着済みエクスペリエンスを入力する

[固定スケールのエクスペリエンス](../../design/coordinate-systems.md)を構築している場合は、XR を呼び出すことによって、ユーザーの現在の位置に Unity の recenter を持たせることができ **[ます。InputTracking. Recenter](https://docs.unity3d.com/ScriptReference/XR.InputTracking.Recenter.html)** メソッド。

## <a name="reprojection-modes"></a>再プロジェクションモード

HoloLens とイマーシブヘッドセットはどちらも、photons が出力されたときにユーザーの実際のヘッド位置の misprediction を調整するために、アプリがレンダリングする各フレームを再プロジェクトします。

既定では:

* アプリが特定のフレームに対して深度バッファーを提供する場合、**イマーシブヘッドセット** は位置の再プロジェクションを実行し、位置と向きの両方で misprediction のホログラムを調整します。  深度バッファーが指定されていない場合、システムは mispredictions の向きのみを修正します。
* HoloLens のような **Holographic ヘッドセット** は、アプリが深度バッファーを提供するかどうかに関係なく、位置指定再プロジェクションを実行します。  レンダリングは、実際には安定した背景でスパースになることが多いため、HoloLens で深度バッファーを使用せずに位置指定リポジトリを使用できます。

固定本文でロックされたコンテンツ (360 度のビデオコンテンツなど) を使用して[向きのみのエクスペリエンス](coordinate-systems-in-unity.md#building-an-orientation-only-or-seated-scale-experience)を構築していることがわかっている場合は、HolographicSettings を[HolographicReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.HolographicReprojectionMode.html)に設定することによってのみ、Reprojection モードを[ReprojectionMode](https://docs.unity3d.com/ScriptReference/XR.WSA.HolographicSettings.ReprojectionMode.html)に明示的に設定できます。

## <a name="sharing-your-depth-buffers-with-windows"></a>Windows での深度バッファーの共有

アプリの深度バッファーを Windows に共有すると、アプリは、レンダリングするヘッドセットの種類に基づいて、ホログラムの安定性の2つのブーストのうちの1つを提供します。

* **イマーシブヘッドセット** は、深度バッファーが指定されている場合に位置指定再投影を実行でき、位置と向きの両方で misprediction のホログラムを調整します。
* **Holographic ヘッドセット** には、いくつかの異なる方法があります。 HoloLens 1 は、深度バッファーが指定されると自動的に [フォーカスポイント](focus-point-in-unity.md) を選択し、ほとんどのコンテンツと交差する平面に沿ったホログラムの安定性を最適化します。 HoloLens 2 は、Depth LSR を使用してコンテンツを安定化します [(「解説」を参照してください)](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)。

Unity アプリで Windows に深度バッファーを提供するかどうかを設定するには、次のようにします。

1. [ **Edit**  >  **Project settings**  >  **Player**  >  **] ユニバーサル Windows プラットフォーム tab**  >  **XR settings**] にアクセスします。
2. [ **Windows Mixed REALITY SDK** ] 項目を展開します。
3. [ **深度バッファーの共有を有効にする** ] チェックボックスをオンまたはオフにします。  この機能は Unity に追加された後に作成された新しいプロジェクトでは既定でチェックされ、アップグレードされた以前のプロジェクトでは既定でオフになります。

Windows に深度バッファーを指定すると、Windows がメインカメラで Unity に設定した近距離および遠方を使用して、深度バッファー内の正規化されたピクセルごとの深度値をメートル単位の距離に正確にマップできる限り、視覚品質が向上します。  通常の方法でレンダリングがハンドルの深さの値を渡す場合は、通常、ここで問題ありません。ただし、既存のカラーピクセルに対してを使用している間に深度バッファーに書き込む半透明のレンダリングパスは、再プロジェクションを混乱させる可能性があります。  レンダリングパスによって、最終的な深度ピクセルの多くが正確な深度値で保持されていることがわかっている場合は、[深度バッファーの共有を有効にする] をオフにすると、視覚品質が向上する可能性があります。 # # 次の開発チェックポイント

## <a name="automatic-scene-and-camera-setup-with-mixed-reality-toolkit-v2"></a>混合 Reality Toolkit v2 を使用した自動シーンおよびカメラ設定

ステップ [バイステップ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html) ガイドに従って Unity プロジェクトに Mixed Reality Toolkit v2 を追加すると、プロジェクトが自動的に構成されます。 また、次のセクションのガイドを使用して、MRTK なしでプロジェクトを手動で構成することもできます。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

私たちが用意した Unity 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。 ここから、次の構成要素に進むことができます。

> [!div class="nextstepaction"]
> [視線入力](gaze-in-unity.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [共有エクスペリエンス](shared-experiences-in-unity.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目

* [ホログラムの安定性](../platform-capabilities-and-apis/hologram-stability.md)
* [MixedRealityToolkit メインカメラ。 prefab](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Input/Prefabs)
