---
title: Unity のモーションコントローラー
description: XR および共通のボタンと軸の Api を使用して、モーショントゥイーンでのモーションコントローラー入力を使用して、その操作を実行する方法について説明します。
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: モーションコントローラー, unity, 入力, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実のヘッドセット, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: db103e674a369f13e62aac5e8c0513b2c2c17f9e
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583506"
---
# <a name="motion-controllers-in-unity"></a>Unity のモーションコントローラー

[Unity](gaze-in-unity.md)での操作を実行するには、2つの主要な方法があります。 HoloLens では[ハンドジェスチャ](../../design/gaze-and-commit.md#composite-gestures)と、HoloLens では[アニメーションコントローラー](../../design/motion-controllers.md)を使用します。 Unity の同じ Api を使用して、空間入力の両方のソースのデータにアクセスします。

Unity には、Windows Mixed Reality の空間入力データにアクセスする主な方法が2つあります。 Common *input. GetButton/GetAxis* api は複数の Unity XR sdk に対して機能しますが、Windows Mixed Reality に固有の *Interactionmanager/GestureRecognizer* api は、空間入力データの完全なセットを公開します。

## <a name="unity-xr-input-apis"></a>Unity XR 入力 Api

新しいプロジェクトの場合は、最初から新しい XR 入力 Api を使用することをお勧めします。 

[XR api](https://docs.unity3d.com/Manual/xr_input.html)の詳細については、こちらを参照してください。

## <a name="unity-buttonaxis-mapping-table"></a>Unity ボタン/軸マッピングテーブル

Unity の Windows Mixed Reality モーションコントローラーの入力マネージャーでは、次に示すボタンと軸の Id を *入力します。 GetButton/GetAxis* api を使用します。 「Windows MR 固有」列では、 *Interactionsourcestate* 型から使用できるプロパティを参照しています。 これらの各 Api の詳細については、以下のセクションで詳しく説明します。

Windows Mixed Reality のボタン/軸 ID マッピングは、通常、Oculus のボタン/軸 Id と一致します。

Windows Mixed Reality のボタン/軸 ID マッピングは、次の2つの方法で OpenVR のマッピングと異なります。
1. このマッピングでは、サムスティックとは異なるタッチパッド Id を使用して、thumbsticks とタッチパッド向けの両方を持つコントローラーをサポートします。
2. このマッピングにより、メニューボタンの A および X ボタン Id のオーバーロードが回避され、物理 ABXY ボタンで使用できるようになります。

<table>
<tr>
<th rowspan="2">入力 </th><th colspan="2"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">一般的な Unity API</a><br />(Input. GetButton/GetAxis) </th><th rowspan="2"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows MR 固有の入力 API</a><br />XR.付い.代入</th>
</tr><tr>
<th> 左側 </th><th> Right</th>
</tr><tr>
<td> 押されたトリガーを選択 </td><td> 軸 9 = 1.0 </td><td> 軸 10 = 1.0 </td><td> selectPressed れた</td>
</tr><tr>
<td> トリガーのアナログ値の選択 </td><td> 軸9 </td><td> 軸10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> 一部押されたトリガーを選択 </td><td> ボタン 14 <i>(ゲームパッド互換)</i> </td><td> ボタン 15 <i>(ゲームパッド互換)</i> </td><td> selectPressedAmount &gt; 0.0</td>
</tr><tr>
<td> 押されたメニューボタン </td><td> ボタン 6 * </td><td> ボタン 7 * </td><td> menuPressed</td>
</tr><tr>
<td> 押されたグリップボタン </td><td> 軸 11 = 1.0 (アナログ値なし)<br />ボタン 4 <i>(ゲームパッド互換)</i> </td><td> 軸 12 = 1.0 (アナログ値なし)<br />ボタン 5 <i>(ゲームパッド互換)</i> </td><td> grasped</td>
</tr><tr>
<td> スティック X <i>(左:-1.0、右: 1.0)</i> </td><td> 軸1 </td><td> 軸4 </td><td> thumbstickPosition</td>
</tr><tr>
<td> サムスティック Y <i>(上:-1.0、下: 1.0)</i> </td><td> 軸2 </td><td> 軸5 </td><td> thumbstickPosition</td>
</tr><tr>
<td> 押したサムスティック </td><td> ボタン8 </td><td> ボタン9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> タッチパッド X <i>(左:-1.0、右: 1.0)</i> </td><td> 軸 17 * </td><td> 軸 19 * </td><td> touchpadPosition</td>
</tr><tr>
<td> タッチパッド Y <i>(上:-1.0、下: 1.0)</i> </td><td> 軸 18 * </td><td> 軸 20 * </td><td> touchpadPosition</td>
</tr><tr>
<td> タッチパッドにタッチ </td><td> ボタン 18 * </td><td> ボタン 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> タッチパッドが押されました </td><td> ボタン 16 * </td><td> ボタン 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> 6自由度グリップまたはポインターのポーズ </td><td colspan="2"> <i>グリップ</i> の発生のみ: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR。InputTracking。 GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR.InputTracking。 GetLocalRotation</a></td><td> <i>グリップ</i>または<i>ポインター</i>を引数として渡す: sourcestate<br />sourceState。 TryGetRotation<br /></td>
</tr><tr>
<td> 状態の追跡 </td><td colspan="2"> <i>位置の精度とソース損失リスクは MR 固有の API を介してのみ利用可能</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">sourceState. Sourcestate の精度</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">sourceState. sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>これらのボタン/軸 Id は、ゲームパッド、Oculus Touch、OpenVR で使用されるマッピングの競合により、Unity が OpenVR に使用する Id とは異なります。

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->


## <a name="grip-pose-vs-pointing-pose"></a>グリップポーズとポインティングポーズ

Windows Mixed Reality では、さまざまなフォームファクターでモーションコントローラーをサポートしています。 各コントローラーの設計は、ユーザーの手の位置と、アプリがコントローラーをレンダリングするときに使用する自然な "転送" の方向との間の関係において異なります。

これらのコントローラーをより適切に表現するために、それぞれの相互作用ソース、 **グリップ** の原因、および **ポインター** の種類に対して調査できる2種類の方法があります。 グリップとポインターの両方の座標は、グローバル Unity ワールド座標のすべての Unity Api によって表されます。

### <a name="grip-pose"></a>グリップの原因

**グリップ** は、HoloLens によって検出されたか、または運動コントローラーを保持しているユーザーの palm の場所を表します。

イマーシブヘッドセットでは、ユーザー **の手** や **ユーザー側に保持** されているオブジェクトをレンダリングするために、グリップが最適です。 グリップは、モーションコントローラーを視覚化するときにも使用されます。 モーションコントローラー用に Windows によって提供される **描画モデル** では、回転の原点と中心としてグリップが使用されます。

グリップは、次のように明確に定義されます。
* **グリップの位置**: コントローラーを自然に保持するときのパーム重心。グリップ内の位置を中央に配置するように左右に調整されます。 Windows Mixed Reality モーションコントローラーでは、通常、この位置はボタンをつかみに揃えて配置されます。
* **グリップの向きの右軸**: 手を完全に開いて平らな5本の指を作成した場合 (左側のパームから前方、右側のパームから後方)、
* **グリップの向きの前方軸**: ハンドを部分的に閉じた場合 (コントローラーを保持している場合と同様)、非表示の指で形成されたチューブを通過する光線。
* **グリップの向きの上位軸**: 右および順方向の定義によって暗黙的に示される上位軸。

このグリップには、Unity のクロスベンダ入力 API (XR) を使用してアクセスでき *[ます。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation*) または WINDOWS MR 固有の API (*TryGetPosition/rotation*) を使用して、 **グリップ** ノードのポーズデータを要求します。

### <a name="pointer-pose"></a>ポインターのポーズ

**ポインター** は、前方にあるコントローラーの先端を表します。

システム指定のポインターの raycast は、 **コントローラーモデル自体をレンダリング** するときに最もよく使用されます。 仮想銃など、コントローラーの代わりに他の仮想オブジェクトをレンダリングする場合は、アプリ定義の銃モデルの胴体に沿って移動する射線など、その仮想オブジェクトに最も適した光線をポイントする必要があります。 ユーザーは物理コントローラーではなく仮想オブジェクトを見ることができるため、仮想オブジェクトをポイントすると、アプリを使用している方がより自然な場合があります。

現時点では、ポインターの破壊は、Unity では、Windows MR 固有の API *TryGetPosition/ローテーション* を通じてのみ使用できます。引数として *Interactionsourcenode* を渡します。

## <a name="controller-tracking-state"></a>コントローラー追跡状態

ヘッドセットと同様に、Windows Mixed Reality モーションコントローラーでは、外部の追跡センサーを設定する必要がありません。 代わりに、コントローラーはヘッドセット自体のセンサーによって追跡されます。

ユーザーがコントローラーをヘッドセットのビューのフィールドから移動した場合、ほとんどの場合、Windows はコントローラーの位置を推測し続けます。 コントローラーのビジュアル追跡が十分に失われた場合、コントローラーの位置はおおよその精度の位置にドロップします。

この時点で、システムはコントローラーをユーザーにボディロックし、ユーザーが移動したときの位置を追跡しながら、内部方向センサーを使用してコントローラーの真向きを公開します。 UI 要素をポイントしてアクティブ化するためにコントローラーを使用する多くのアプリは、ユーザーに気付かなくても、おおよその精度で正常に動作できます。

これを実現する最善の方法は、自分で試してみることです。 次のビデオでは、さまざまな追跡状態におけるモーションコントローラーで動作するイマーシブコンテンツの例を紹介しています。

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g]

### <a name="reasoning-about-tracking-state-explicitly"></a>状態の明示的な追跡に関する推論

追跡の状態に基づいて位置を異なる方法で処理する必要があるアプリは、さらに詳細になり、コントローラーの状態 ( *SourceLossRisk* や *positionaccuracy* など) のプロパティを検査することができます。

<table>
<tr>
<th> 状態の追跡 </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>高精度</b> </td><td style="background-color: green; color: white"> &lt; 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>高精度 (消失のリスク)</b> </td><td style="background-color: orange"> = = 1.0 </td><td style="background-color: green; color: white"> 高 </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>おおよその精度</b> </td><td style="background-color: orange"> = = 1.0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>位置なし</b> </td><td style="background-color: orange"> = = 1.0 </td><td style="background-color: orange"> Approximate </td><td style="background-color: orange"> false</td>
</tr>
</table>

これらのモーションコントローラーの追跡状態は、次のように定義されています。
* **高精度:** モーションコントローラーは、ヘッドセットのビューに含まれていますが、通常、ビジュアルの追跡に基づいて高精度の位置を提供します。 一時的にビューのフィールドから離れるか、ヘッドセットセンサー (ユーザーなど) から瞬間的に見えなくなる移動コントローラーは、コントローラー自体の慣性追跡に基づいて、短時間で高精度のポーズを返します。
* **高精度 (損失のリスク):** ユーザーが、ヘッドセットのビューの端を越えてモーションコントローラーを動かすと、ヘッドセットはすぐにコントローラーの位置を視覚的に追跡できなくなります。 アプリでは、 **SourceLossRisk** が1.0 に到達して、コントローラーがこの視界の境界に達したことを認識します。 その時点で、アプリは、高い品質を備えた安定したストリームを必要とするコントローラージェスチャを一時停止することを選択できます。
* **おおよその精度:** コントローラーのビジュアル追跡が十分に失われた場合、コントローラーの位置はおおよその精度の位置にドロップします。 この時点で、システムはコントローラーをユーザーにボディロックし、ユーザーが移動したときの位置を追跡しながら、内部方向センサーを使用してコントローラーの真向きを公開します。 UI 要素をポイントしてアクティブ化するためにコントローラーを使用する多くのアプリは、ユーザーに気付かずに正確な精度で、通常どおりに動作できます。 入力要件が重いアプリでは、 **positionaccuracy** プロパティを調べることによって、精度が **高い** ことを **意味します**。たとえば、この期間中にユーザーに対して、オフスクリーンのターゲットに対してより多くのヒットボックスを与えることができます。
* **位置なし:** コントローラーは長時間の精度で実行できますが、本体でロックされた位置であっても、その時点では意味がないことをシステムが認識している場合があります。 たとえば、電源がオンにされたコントローラーが視覚的に観察されていない場合や、ユーザーがコントローラーを停止した後に他のユーザーが選択した場合などです。 これらのタイミングでは、システムはアプリに位置を提供せず、 *TryGetPosition* は false を返します。

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>共通 Unity Api (Input. GetButton/GetAxis)

**名前空間:** *unityengine*、 *unityengine XR*<br>
**型**: *Input*、 *XR。InputTracking*

Unity では、現在、一般的な *入力. GetButton/GetAxis* api を使用して、 [Oculus Sdk](https://docs.unity3d.com/Manual/OculusControllers.html)、 [Openvr SDK](https://docs.unity3d.com/Manual/OpenVRControllers.html) 、および Windows Mixed Reality の入力を公開しています。これには、ハンドアンドモーションコントローラーも含まれます。 アプリがこれらの Api を入力に使用する場合、Windows Mixed Reality を含む複数の XR Sdk 間で、モーションコントローラーを簡単にサポートできます。

### <a name="getting-a-logical-buttons-pressed-state"></a>論理ボタンの押された状態の取得

一般的な Unity 入力 Api を使用するには、まず、 [Unity 入力マネージャー](https://docs.unity3d.com/Manual/ConventionalGameInput.html)で論理名にボタンと軸を配線し、ボタンまたは軸 id を各名前にバインドします。 その後、その論理ボタンと軸名を参照するコードを記述できます。

たとえば、左モーションコントローラーの [トリガー] ボタンを [送信] アクションにマップするには、[ **編集 > プロジェクトの設定** ] に移動し、Unity 内の [入力] > て、[軸] の [送信] セクションのプロパティを展開します。 次のように、 **正のボタン** または **Alt 陽性のボタン** プロパティを [ジョイスティックの読み取り **] ボタン 14** に変更します。

![Unity の InputManager](images/unity-input-manager.png)<br>
*Unity InputManager*

スクリプトは、 *Input. GetButton* を使用して送信アクションを確認できます。

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
論理ボタンを追加するには、[**軸**] の [**サイズ**] プロパティを変更します。

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>物理的なボタンの押された状態を直接取得する

*GetKey* を使用して、完全修飾名でボタンに手動でアクセスすることもできます。

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>手や運動コントローラーのポーズ

XR を使用して、コントローラーの位置と回転にアクセスでき *ます。InputTracking*:

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> 上のコードは、コントローラーのグリップの発生 (ユーザーがコントローラーを保持している場所) を表します。これは、ユーザーの手に剣や銃をレンダリングする場合や、コントローラー自体のモデルをレンダリングする場合に便利です。
> 
> このグリップとポインターの (コントローラーの先端が指している) 間のリレーションシップは、コントローラーによって異なる場合があります。 現時点では、コントローラーのポインターにアクセスするには、次のセクションで説明する MR 固有の入力 API を使用するしかありません。

## <a name="windows-specific-apis-xrwsainput"></a>Windows 固有の Api (XR。付い.代入

> [!CAUTION]
> プロジェクトが XR のいずれかを使用している場合。WSA Api は、今後の Unity リリースで XR SDK を優先するように段階的に廃止されています。 新しいプロジェクトの場合は、最初から XR SDK を使用することをお勧めします。 [XR 入力システムと api](https://docs.unity3d.com/Manual/xr_input.html)の詳細については、こちらを参照してください。

**名前空間:** *UNITYENGINE. XR*<br>
**型**: *interactionmanager*、 *interactionsourcestate*、 *interactionmanager*、 *interactionsourceproperties*、 *interactionsourcekind*、 *interactionmanager*

Windows Mixed Reality の入力 (HoloLens) とモーションコントローラーの詳細情報を取得するには、 *XR* 名前空間で windows 固有の空間入力 api を使用することを選択できます。 これにより、位置の精度やソースの種類などの追加情報にアクセスして、ハンドとコントローラーを区別できます。

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>ハンドコントローラーとモーションコントローラーの状態のポーリング

このフレームの状態は、 *GetCurrentReading* メソッドを使用して、相互作用ソース (手動またはモーションコントローラー) ごとにポーリングできます。

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

返される各 *Interactionsourcestate* は、現在の時点の相互作用ソースを表します。 *Interactionsourcestate* は、次のような情報を公開します。
* どのような [種類の押下](../../design/motion-controllers.md) が発生していますか (選択/メニュー/つかみ/タッチパッド/サムスティック)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* タッチパッドやサムスティックの XY 座標とタッチされた状態など、モーションコントローラー固有のその他のデータ

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* ソースがハンドコントローラーであるか、モーションコントローラーであるかを知るための InteractionSourceKind

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>前方予測レンダリングのポーリング

* ハンドおよびコントローラーからの相互作用ソースデータをポーリングする場合、取得されるのは、このフレームの photons がユーザーの目に到達する瞬間を予測することです。  前方予測は、コントローラーまたは保持されたオブジェクトを各フレームに **レンダリング** する場合に最適です。  コントローラーで特定のプレスまたはリリースを対象としている場合は、次に説明する履歴イベント Api を使用すると、そのことが最も正確になります。

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* この現在のフレームの前方予測ヘッドを取得することもできます。  ソースの場合と同様に、これはカーソルを **レンダリング** するときに便利です。ただし、次に説明する履歴イベント api を使用すると、特定のプレスまたはリリースをターゲットにすると最も正確になります。

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>相互作用ソースイベントの処理

正確な履歴データで発生した入力イベントを処理するために、ポーリングではなく相互作用ソースイベントを処理できます。

相互作用ソースイベントを処理するには:
* *Interactionmanager* 入力イベントに登録します。 関心がある相互作用イベントの種類ごとに、サブスクライブする必要があります。

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* イベントを処理します。 相互作用イベントをサブスクライブすると、必要に応じてコールバックが取得されます。 *Sourcepressed* れた例では、ソースが検出されてから解放されるか、または失われる前に、が発生します。

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>イベントの処理を停止する方法

イベントに関心がなくなった場合、またはイベントをサブスクライブしているオブジェクトを破棄する場合は、イベントの処理を停止する必要があります。 イベントの処理を停止するには、イベントのサブスクリプションを解除します。

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>相互作用ソースイベントの一覧

使用可能な相互作用ソースイベントは次のとおりです。
* *Interactionsourcedetected 検出されました* (ソースがアクティブになります)
* *Interactionsourcelost* (非アクティブになります)
* *Interactionsourcepressed* れた (tap、button press、または "Select" 発音)
* *InteractionSourceReleased* (tap の終了、ボタンの解放、または "Select" 発音の最後)
* *Interactionsourceupdated* (移動またはその他の状態の変更)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>プレスまたはリリースと最も正確に一致する履歴ターゲットのイベント

前に説明したポーリング Api を使用すると、アプリが事前に予測されるようになります。  これらの予測される効果はコントローラーまたは仮想ハンドヘルドオブジェクトのレンダリングに最適ですが、次の2つの主な理由から、将来のターゲット設定には最適ではありません。
* ユーザーがコントローラー上のボタンを押すと、Bluetooth 経由のワイヤレス待ち時間は約20ミリ秒になることがあります。
* 次に、前方予測攻撃を使用している場合、現在のフレームの photons がユーザーの目に近づいた時間をターゲットにするために、10-20 ミリ秒の前方予測が適用されます。

これは、ポーリングによって、ユーザーの頭と針が、プレスまたはリリースが発生したときに実際には30-40 ミリ秒後に発生するようにすることを意味します。  HoloLens の入力では、ワイヤレス転送の遅延は発生しませんが、押しを検出するために同様の処理遅延が発生します。

ユーザーが手やコントローラーを押したときの本来の目的に基づいて正確にターゲットを指定するには、その *Interactionsourcepressed* れたイベントまたは *InteractionSourceReleased* 入力イベントからの履歴ソースの発生元またはヘッドポーズを使用する必要があります。

ユーザーのヘッドまたはコントローラーの履歴リーダーデータを使用して、プレスまたはリリースを対象にすることができます。
* ジェスチャまたはコントローラーの押下が発生した時点で、[ユーザーがどの](../../design/gaze-and-commit.md)ようにしているかを **判断するため** に使用できます。

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* モーションコントローラーの押下が発生した時点のソースは、ユーザーがコントローラーを指していた **対象を判別するため** に使用できます。  これは、押下を経験したコントローラーの状態になります。  コントローラー自体をレンダリングする場合は、グリップの原因ではなくポインターのポーズを要求できます。これにより、レンダリングされたコントローラーの自然なヒントをユーザーが考慮する対象から、ターゲットの射線をシュートすることができます。

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>イベントハンドラーの例

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="motion-controllers-in-mrtk-v2"></a>MRTK v2 のモーションコントローラー

入力マネージャーから [ジェスチャとモーションコントローラー](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Input/Controllers.html) にアクセスできます。

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