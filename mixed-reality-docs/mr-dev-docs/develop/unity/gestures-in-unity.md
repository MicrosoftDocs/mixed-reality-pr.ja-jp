---
title: Unity でのジェスチャ
description: XR および共通のボタンと軸の Api を使用して手書きのジェスチャ入力を使用して、Unity での操作を実行する方法について説明します。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: ジェスチャ, unity, 宝石, 入力, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実のヘッドセット, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: 44c42abdd4628cacd6af334a916fb725da8bb022
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583894"
---
# <a name="gestures-in-unity"></a>Unity でのジェスチャ

[Unity](gaze-in-unity.md)での操作を実行するには、2つの主要な方法があります。 HoloLens では[ハンドジェスチャ](../../design/gaze-and-commit.md#composite-gestures)と、HoloLens では[アニメーションコントローラー](../../design/motion-controllers.md)を使用します。 Unity の同じ Api を使用して、空間入力の両方のソースのデータにアクセスします。

Unity には、Windows Mixed Reality の空間入力データにアクセスする主な方法が2つあります。 Common *input. GetButton/GetAxis* api は複数の Unity XR sdk に対して機能しますが、Windows Mixed Reality に固有の *Interactionmanager/GestureRecognizer* api は、空間入力データの完全なセットを公開します。

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>高レベル複合ジェスチャ Api (GestureRecognizer)

**名前空間:** *UNITYENGINE. XR*<br>
**型**: *GestureRecognizer*、 *GestureSettings*、 *interactionsourcekind*

アプリでは、空間入力ソース、タップ、ホールド、操作、およびナビゲーションジェスチャに対する高レベルの複合ジェスチャを認識することもできます。 GestureRecognizer を使用して、[ハンド](../../design/gaze-and-commit.md#composite-gestures)[コントローラーとモーションコントローラー](../../design/motion-controllers.md)の両方でこれらの複合ジェスチャを認識できます。

GestureRecognizer の各ジェスチャイベントは、イベントの発生時に、入力とターゲットのヘッドレイを提供します。 一部のイベントは、コンテキスト固有の追加情報を提供します。

ジェスチャ認識エンジンを使用してジェスチャをキャプチャするには、いくつかの手順を実行する必要があります。
1. 新しいジェスチャ認識エンジンを作成する
2. 監視するジェスチャを指定する
3. これらのジェスチャのイベントをサブスクライブする
4. ジェスチャのキャプチャを開始する

### <a name="create-a-new-gesture-recognizer"></a>新しいジェスチャ認識エンジンを作成する

*GestureRecognizer* を使用するには、 *GestureRecognizer* を作成しておく必要があります。

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>監視するジェスチャを指定する

*Set認識 Izableジェスチャー ()* を使用して、興味のあるジェスチャを指定します。

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>これらのジェスチャのイベントをサブスクライブする

関心のあるジェスチャのイベントをサブスクライブします。

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>ナビゲーションと操作のジェスチャは、 *GestureRecognizer* のインスタンスで相互に排他的です。

### <a name="start-capturing-gestures"></a>ジェスチャのキャプチャを開始する

既定では、 *GestureRecognizer* は、 *Startcapturinggestures ()* が呼び出されるまで、入力を監視しません。 Stopcapturinggestures () が *処理されたフレーム* の前に入力が実行された場合、 *Stopcapturinggestures ()* が呼び出された後にジェスチャイベントが生成される可能性があります。 *GestureRecognizer* は、ジェスチャが実際に発生した前のフレームでオンまたはオフになっていたかどうかを記憶します。そのため、このフレームのターゲット設定に基づいてジェスチャの監視を開始および停止するのは安全です。

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>ジェスチャのキャプチャを停止します

ジェスチャ認識を停止するには:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>ジェスチャ認識エンジンの削除

*GestureRecognizer* オブジェクトを破棄する前に、サブスクライブされたイベントのサブスクリプションを解除してください。

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Unity でのモーションコントローラーモデルのレンダリング

![モーションコントローラーモデルとテレ](images/motioncontrollertest-teleport-1000px.png)<br>
*モーションコントローラーモデルとテレ*

ユーザーが保持している物理コントローラーに一致するモーションコントローラーをアプリでレンダリングし、さまざまなボタンが押されていることを明確にするために、 [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/)で **motioncontroller prefab** を使用できます。  この prefab は、システムのインストールされている motion controller ドライバーから、実行時に正しい glTF モデルを動的に読み込みます。  これらのモデルは、エディターで手動でインポートするのではなく、動的に読み込むことが重要です。これにより、ユーザーが現在使用しているコントローラーと将来のコントローラーに対して、アプリケーションで物理的に正確な3D モデルが表示されるようになります。

1. [はじめに](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md)の手順に従って、Mixed Reality Toolkit をダウンロードし、Unity プロジェクトに追加します。
2. はじめにの手順の一部としてカメラを *MixedRealityCameraParent* prefab に置き換えると、お勧めします。  この事前 fab には、モーションコントローラーレンダリングが含まれています。  それ以外の場合は、 *Assets/HoloToolkit/Input/Prefabs/MotionControllers* を [プロジェクト] ウィンドウからシーンに追加します。  この prefab は、シーン内のユーザーが携帯電話に接続しているときに、カメラを移動するために使用する親オブジェクトの子として追加します。これにより、コントローラーはユーザーと共に表示されます。  アプリに電話移植が含まれていない場合は、シーンのルートに prefab を追加するだけです。

## <a name="throwing-objects"></a>オブジェクトのスロー

仮想現実のオブジェクトをスローすることは、最初に考えられるよりも難しい問題です。 ほとんどの物理的な相互作用と同様に、ゲームでのスローは予期しない方法で動作しますが、immersion はすぐに明らかになり、壊れることがあります。 私たちは、物理的に正しいスロー動作を表す方法について、少し時間をかけてきました。また、お客様と共有するプラットフォームの更新によって有効になるガイドラインがいくつかあります。

スローを実装する方法の例については、 [こちら](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)を参照してください。 このサンプルは、次の4つのガイドラインに従います。
* **位置ではなく、コントローラーの *ベロシティ* を使用** します。 Windows の11月の更新プログラムでは、 [' ' 概算 ' ' 位置追跡状態](../../design/motion-controllers.md#controller-tracking-state)での動作の変更が導入されました。 この状態になると、高い精度を維持している限り、コントローラーに関する速度に関する情報が引き続き報告されます。
* **コントローラーの *角速度* を組み込み** ます。 このロジックはすべて、上記の `throwing.cs` リンクされ `GetThrownObjectVelAngVel` たパッケージ内の静的メソッドのファイルに含まれています。
   1. 角速度が節約であるため、スローされたオブジェクトは、スローの時点と同じ角度速度を維持する必要があります。 `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. スローされたオブジェクトの質量の中心がグリップの原因ではない可能性があるため、ユーザーの参照フレーム内のコントローラーの速度とは、ベロシティが異なる可能性があります。 この方法で発生したオブジェクトのベロシティの部分は、コントローラーの原点を中心としてスローされたオブジェクトの質量の中心となる瞬間流速度です。 この接線速度は、コントローラーの原点と、スローされたオブジェクトの質量の中心との距離を表すベクトルを使用して、コントローラーの角速度のクロス積です。

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. スローされたオブジェクトの合計速度は、コントローラーのベロシティとこの接線速度の合計です。 `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **速度を適用する *時間* に細心の注意を** 払ってください。 ボタンを押すと、そのイベントが Bluetooth 経由でオペレーティングシステムに対してバブルアップされるまでに最大20ミリ秒かかることがあります。 これは、コントローラーの状態の変化をポーリングしたときに、押された状態または押されていない状態の変化をポーリングした場合に、そのコントローラーの状態が変更される前に発生します。 さらに、ポーリング API によって提示されるコントローラーは、フレームが表示されるときに発生する可能性があることを反映するためにフォワード予測が行われます。これは、今後20ミリ秒を超える可能性があります。 これは、保持されているオブジェクトを *レンダリング* する場合に適していますが、ユーザーがスローを解放した瞬間の軌道を計算するときに、オブジェクトを *ターゲット* にするための時間の問題が複雑になります。 幸いにも、11月の更新プログラムでは、 *Interactionsourcepressed* れた、 *InteractionSourceReleased* などの Unity イベントが送信されたときに、ボタンが押されたとき、または解放されたときに、状態に履歴情報が含まれています。  スロー中に正確なコントローラーレンダリングとコントローラーターゲットを取得するには、必要に応じて、ポーリングとイベントを正しく使用する必要があります。
   * コントローラーが各フレームを **レンダリング** する場合、アプリは、現在のフレームの photon 時間に合わせて、コントローラーの *オブジェクト* を前方予測コントローラーに配置する必要があります。  このデータは、XR のような Unity ポーリング Api から取得し *[ます。InputTracking。 GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* または *[XR。付い.GetCurrentReading を入力し](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)* ます。
   * プレスまたはリリースを対象とする **コントローラー** の場合、アプリは、そのプレスまたはリリースイベントのコントローラーの履歴に基づいて、軌道を raycast して計算する必要があります。  このデータは、Interactionmanager と同様に Unity イベント Api から取得し *[ます。 Interactionsource押さ](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)* れています。
* **グリップを使用** します。 角速度とベロシティは、ポインターではなく、グリップによって報告されます。

今後の Windows 更新プログラムでは、のスローが引き続き改善され、詳細についてはここで確認できます。

## <a name="gesture-and-motion-controllers-in-mrtk-v2"></a>MRTK v2 のジェスチャとモーションコントローラー

入力マネージャーからジェスチャとモーションコントローラーにアクセスできます。
* [MRTK v2 でのジェスチャ](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Gestures.html)
* [MRTK v2 のモーションコントローラー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html)


## <a name="follow-along-with-tutorials"></a>チュートリアルに従う

詳細なカスタマイズ例が記載されたステップバイステップのチュートリアルは、Mixed Reality Academy でご利用いただけます。

- [MR 入力 211:ジェスチャ](tutorials/holograms-211.md)
- [MR 入力 213:モーション コントローラー](../../deprecated/mixed-reality-213.md)

[![MR 入力 213-モーションコントローラー](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*MR 入力 213-モーションコントローラー*

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

Unity の開発に関する体験に従っている場合は、MRTK コアのビルディングブロックを調べています。 ここから、次の構成要素を続けることができます。

> [!div class="nextstepaction"]
> [手と視線の追跡](./hand-eye-in-unity.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [共有エクスペリエンス](shared-experiences-in-unity.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目

* [頭の視線入力とコミット](../../design/gaze-and-commit.md)
* [モーション コントローラー](../../design/motion-controllers.md)