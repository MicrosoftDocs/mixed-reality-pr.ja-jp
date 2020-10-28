---
title: Unity でのジェスチャとモーション コントローラー
description: ハンドジェスチャとモーションコントローラーを使用して、Unity での操作を実行する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: ジェスチャ、モーションコントローラー、unity、宝石、入力
ms.openlocfilehash: 6c41de0a0b5d2879b2f3a0be90c9456100599d2b
ms.sourcegitcommit: 8b16945d6a551f174a65fa3980ba392682ca45d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92886275"
---
# <a name="gestures-and-motion-controllers-in-unity"></a>Unity でのジェスチャとモーション コントローラー

[Unity](gaze-in-unity.md)での操作を実行するには、2つの主要な方法があります。 HoloLens では[ハンドジェスチャ](../../design/gaze-and-commit.md#composite-gestures)と、HoloLens では[アニメーションコントローラー](../../design/motion-controllers.md)を使用します。 Unity の同じ Api を使用して、空間入力の両方のソースのデータにアクセスします。

Unity には、Windows Mixed Reality の空間入力データにアクセスするための主な方法が2つあります。複数の Unity XR Sdk 間で動作する common *input. GetButton/GetAxis* api と、使用可能な空間入力データの完全なセットを公開する Windows mixed reality に固有の *Interactionmanager/GestureRecognizer* api です。

## <a name="unity-buttonaxis-mapping-table"></a>Unity ボタン/軸マッピングテーブル

次の表に示すボタンと軸の Id は、Unity の Windows Mixed Reality の入力マネージャーでは、 *入力の GetButton/GetAxis* api を通じてサポートされていますが、"Windows MR 固有" の列では、 *Interactionsourcestate* 型から使用できるプロパティを参照しています。 これらの各 Api の詳細については、以下のセクションで詳しく説明します。

Windows Mixed Reality のボタン/軸 ID マッピングは、通常、Oculus のボタン/軸 Id と一致します。

Windows Mixed Reality のボタン/軸 ID マッピングは、次の2つの方法で OpenVR のマッピングと異なります。
1. このマッピングでは、サムスティックとは異なるタッチパッド Id を使用して、thumbsticks とタッチパッド向けの両方を持つコントローラーをサポートします。
2. このマッピングにより、メニューボタンの A および X ボタン Id のオーバーロードが回避され、物理 ABXY ボタンで使用できるようになります。

<table>
<tr>
<th rowspan="2">入力 </th><th colspan="2"><a href="gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">一般的な Unity API</a><br />(Input. GetButton/GetAxis) </th><th rowspan="2"><a href="gestures-and-motion-controllers-in-unity.md#">Windows MR 固有の入力 API</a><br />XR.付い.代入</th>
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

Windows Mixed Reality では、さまざまなフォームファクターでモーションコントローラーがサポートされています。各コントローラーの設計は、ユーザーの手の位置と、アプリがコントローラーを表示するときに使用する自然な "進む" 方向との間の関係において異なります。

これらのコントローラーをより適切に表現するために、それぞれの相互作用ソース、 **グリップ** の原因、および **ポインター** の種類に対して調査できる2種類の方法があります。 グリップとポインターの両方の座標は、グローバル Unity ワールド座標のすべての Unity Api によって表されます。

### <a name="grip-pose"></a>グリップの原因

**グリップ** は、HoloLens によって検出された、または運動コントローラーを持つパームのいずれかの場所を表します。

イマーシブヘッドセットでは、グリップは、 **ユーザーの手** や、剣や銃など、 **ユーザーの手に保持** されているオブジェクトをレンダリングするために最適です。 また、このグリップは、モーションコントローラーを視覚化するときにも使用されます。これは、モーションコントローラー用に Windows によって提供される **描画モデル** が、グリップを原点と回転の中心として使用するためです。

グリップは、次のように明確に定義されます。
* **グリップの位置** : コントローラーを自然に保持するときのパーム重心。グリップ内の位置を中央に配置するように左右に調整されます。 Windows Mixed Reality モーションコントローラーでは、通常、この位置はボタンをつかみに揃えて配置されます。
* **グリップの向きの右軸** : 手を完全に開いて平らな5本の指を作成した場合 (左側のパームから前方、右側のパームから後方)、
* **グリップの向きの前方軸** : ハンドを部分的に閉じた場合 (コントローラーを保持している場合と同様)、非表示の指で形成されたチューブを通過する光線。
* **グリップの向きの上位軸** : 右および順方向の定義によって暗黙的に示される上位軸。

このグリップには、Unity のクロスベンダ入力 API (XR) を使用してアクセスでき *[ます。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation* ) または WINDOWS MR 固有の API ( *TryGetPosition/rotation* ) を使用して、 **グリップ** ノードのポーズデータを要求します。

### <a name="pointer-pose"></a>ポインターのポーズ

**ポインター** は、前方にあるコントローラーの先端を表します。

システム指定のポインターの raycast は、 **コントローラーモデル自体をレンダリング** するときに最もよく使用されます。 仮想銃など、コントローラーの代わりに他の仮想オブジェクトをレンダリングする場合は、アプリ定義の銃モデルの胴体に沿って移動する射線など、その仮想オブジェクトに最も適した光線をポイントする必要があります。 ユーザーは物理コントローラーではなく仮想オブジェクトを見ることができるため、仮想オブジェクトをポイントすると、アプリを使用している方がより自然な場合があります。

現時点では、ポインターの破壊は、Unity では、Windows MR 固有の API *TryGetPosition/ローテーション* を通じてのみ使用できます。引数として *Interactionsourcenode* を渡します。

## <a name="controller-tracking-state"></a>コントローラー追跡状態

ヘッドセットと同様に、Windows Mixed Reality モーションコントローラーでは、外部の追跡センサーを設定する必要がありません。 代わりに、コントローラーはヘッドセット自体のセンサーによって追跡されます。

ユーザーがヘッドセットのビューのフィールドからコントローラーを移動した場合、ほとんどの場合、Windows はコントローラーの位置を推測してアプリに提供し続けます。 コントローラーのビジュアル追跡が十分に失われた場合、コントローラーの位置はおおよその精度の位置にドロップします。

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
* **高精度:** モーションコントローラーは、ヘッドセットのビューに含まれていますが、通常、ビジュアルの追跡に基づいて高精度の位置を提供します。 ビューまたはのフィールドから瞬間的に見えない移動コントローラーは、(ユーザーの他の手によって) ヘッドセットセンサーから瞬間的に見えなくなっていることに注意してください。これは、コントローラー自体の慣性追跡に基づいて、短時間で高精度のポーズを返します。
* **高精度 (損失のリスク):** ユーザーが、ヘッドセットのビューの端を越えてモーションコントローラーを動かすと、ヘッドセットはすぐにコントローラーの位置を視覚的に追跡できなくなります。 アプリでは、 **SourceLossRisk** が1.0 に到達して、コントローラーがこの視界の境界に達したことを認識します。 その時点で、アプリは、非常に高品質なポーズの安定したストリームを必要とするコントローラージェスチャを一時停止することを選択できます。
* **おおよその精度:** コントローラーのビジュアル追跡が十分に失われた場合、コントローラーの位置はおおよその精度の位置にドロップします。 この時点で、システムはコントローラーをユーザーにボディロックし、ユーザーが移動したときの位置を追跡しながら、内部方向センサーを使用してコントローラーの真向きを公開します。 UI 要素をポイントしてアクティブ化するためにコントローラーを使用する多くのアプリは、ユーザーに気付かずに正確な精度で、通常どおりに動作できます。 入力要件が重いアプリでは、 **positionaccuracy** プロパティを調べることによって、精度が **高い** ことを **意味します** 。たとえば、この期間中にユーザーに対して、オフスクリーンのターゲットに対してより多くのヒットボックスを与えることができます。
* **位置なし:** コントローラーは長時間の精度で実行できますが、本体でロックされている位置が現時点では意味を持たないことをシステムが認識している場合があります。 たとえば、電源が入っていたコントローラーが視覚的に観察されていない場合や、ユーザーがコントローラーを停止した後に他のユーザーが選択した場合などです。 これらのタイミングでは、システムはアプリに位置を提供せず、 *TryGetPosition* は false を返します。

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>共通 Unity Api (Input. GetButton/GetAxis)

**名前空間:** *unityengine* 、 *unityengine XR*<br>
**型** : *Input* 、 *XR。InputTracking*

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
論理ボタンを追加するには、[ **軸** ] の [ **サイズ** ] プロパティを変更します。

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>物理的なボタンの押された状態を直接取得する

*GetKey* を使用して、完全修飾名でボタンに手動でアクセスすることもできます。

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>手や運動コントローラーのポーズ

XR を使用して、コントローラーの位置と回転にアクセスでき *ます。InputTracking* :

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

これはコントローラーのグリップ (ユーザーがコントローラーを保持している場所) を表します。これは、ユーザーの手に剣や銃をレンダリングする場合や、コントローラー自体のモデルをレンダリングする場合に便利です。

このグリップとポインターの (コントローラーの先端が指している) 間のリレーションシップは、コントローラーによって異なる場合があることに注意してください。 現時点では、コントローラーのポインターにアクセスするには、次のセクションで説明する MR 固有の入力 API を使用するしかありません。

## <a name="windows-specific-apis-xrwsainput"></a>Windows 固有の Api (XR。付い.代入

**名前空間:** *UNITYENGINE. XR*<br>
**型** : *interactionmanager* 、 *interactionsourcestate* 、 *interactionmanager* 、 *interactionsourceproperties* 、 *interactionsourcekind* 、 *interactionmanager*

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

* ハンドおよびコントローラーからの相互作用ソースデータをポーリングする場合、取得されるのは、このフレームの photons がユーザーの目に到達する瞬間を予測することです。  これらの前方予測は、コントローラーまたは保持されたオブジェクトを各フレームに **レンダリング** する場合に最適です。  コントローラーで特定のプレスまたはリリースを対象としている場合は、次に説明する履歴イベント Api を使用すると、そのことが最も正確になります。

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

前に説明したポーリング Api を使用すると、アプリが事前に予測されるようになります。  これらの予測される値はコントローラーまたは仮想ハンドヘルドオブジェクトのレンダリングに最適ですが、2つの主な理由から、将来のターゲット設定には最適ではありません。
* ユーザーがコントローラーでボタンを押すと、システムが押される前に、Bluetooth 経由のワイヤレス待ち時間が20ミリ秒になることがあります。
* 次に、前方予測攻撃を使用している場合、現在のフレームの photons がユーザーの目に到着するまでの時間を目標として、前方予測の別の 10 20 ミリ秒が適用されます。

これは、ポーリングによって、ユーザーの頭と針が、プレスまたはリリースが発生したときに実際に戻ってきた、発信元やヘッドが 30 ~ 40 ミリ秒であることを意味します。  HoloLens の入力では、ワイヤレス転送の遅延は発生しませんが、押しを検出するために同様の処理遅延が発生します。

ユーザーが手やコントローラーを押したときの本来の目的に基づいて正確にターゲットを指定するには、その *Interactionsourcepressed* れたイベントまたは *InteractionSourceReleased* 入力イベントからの履歴ソースの発生元またはヘッドポーズを使用する必要があります。

ユーザーのヘッドまたはコントローラーの履歴リーダーデータを使用して、プレスまたはリリースを対象にすることができます。
* ジェスチャまたはコントローラーの押下が発生した時点で、 [ユーザーがどの](../../design/gaze-and-commit.md)ようにしているかを **判断するため** に使用できます。

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

* モーションコントローラーの押下が発生した時点のソースは、ユーザーがコントローラーを指していた **対象を判別するため** に使用できます。  これは、押下を経験したコントローラーの状態になります。  コントローラー自体をレンダリングする場合は、グリップの原因ではなくポインターのポーズを要求できます。これにより、レンダリングされたコントローラーの自然なヒントをユーザーが考慮しているものからターゲットの射線にシュートすることができます。

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

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>高レベル複合ジェスチャ Api (GestureRecognizer)

**名前空間:** *UNITYENGINE. XR*<br>
**型** : *GestureRecognizer* 、 *GestureSettings* 、 *interactionsourcekind*

アプリでは、空間入力ソース、タップ、ホールド、操作、およびナビゲーションジェスチャに対する高レベルの複合ジェスチャを認識することもできます。 GestureRecognizer を使用して、[ハンド](../../design/gaze-and-commit.md#composite-gestures)[コントローラーとモーションコントローラー](../../design/motion-controllers.md)の両方でこれらの複合ジェスチャを認識できます。

GestureRecognizer の各ジェスチャイベントは、イベントの発生時に、入力とターゲットのヘッドレイを提供します。 一部のイベントは、追加のコンテキスト固有の情報を提供します。

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

既定では、 *GestureRecognizer* は、 *Startcapturinggestures ()* が呼び出されるまで、入力を監視しません。 Stopcapturinggestures () が *処理されたフレーム* の前に入力が実行された場合、 *Stopcapturinggestures ()* が呼び出された後にジェスチャイベントが生成される可能性があります。 *GestureRecognizer* は、ジェスチャが実際に発生した前のフレームでオンまたはオフにされたかどうかを記憶します。そのため、このフレームのターゲット設定に基づいてジェスチャの監視を開始および停止することができます。

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
2. はじめにの手順の一部としてカメラを *MixedRealityCameraParent* prefab に置き換えると、お勧めします。  この事前 fab には、モーションコントローラーレンダリングが含まれています。  それ以外の場合は、 *Assets/HoloToolkit/Input/Prefabs/MotionControllers* を [プロジェクト] ウィンドウからシーンに追加します。  この prefab は、シーン内のユーザーが携帯電話に接続しているときに、カメラを移動するために使用する親オブジェクトの子として追加します。これにより、コントローラーはユーザーと共に表示されます。  アプリにテレが含まれていない場合は、シーンのルートに prefab を追加するだけです。

## <a name="throwing-objects"></a>オブジェクトのスロー

仮想現実のオブジェクトをスローすると、問題が発生する可能性があります。 ほとんどの物理的な相互作用と同様に、ゲームでのスローが予期しない方法で動作する場合は、すぐに明らかになり、immersion が壊れることがあります。 私たちは、物理的に正しいスロー動作を表す方法について、少し時間をかけてきました。また、お客様と共有するプラットフォームの更新によって有効になるガイドラインがいくつかあります。

スローを実装する方法の例については、 [こちら](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage)を参照してください。 このサンプルは、次の4つのガイドラインに従います。
* **位置ではなく、コントローラーの *ベロシティ* を使用** します。 Windows の11月の更新プログラムでは、 [' ' 概算 ' ' 位置追跡状態](../../design/motion-controllers.md#controller-tracking-state)での動作の変更が導入されました。 この状態になっている場合、コントローラーに関する速度情報は、高い精度であると考えられている限り、継続的に報告されます。これは、位置が高精度のままである場合もあります。
* **コントローラーの *角速度* を組み込み** ます。 このロジックはすべて、上記の `throwing.cs` リンクされ `GetThrownObjectVelAngVel` たパッケージ内の静的メソッドのファイルに含まれています。
   1. 角速度が節約であるため、スローされたオブジェクトは、スローの時点と同じ角度速度を維持する必要があります。 `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. スローされたオブジェクトの質量の中心がグリップの原因ではない可能性があるため、ユーザーの参照フレーム内のコントローラーの速度が異なる場合があります。 この方法で発生したオブジェクトのベロシティの部分は、コントローラーの原点を中心としてスローされたオブジェクトの質量の中心となる瞬間流速度です。 この接線速度は、コントローラーの原点と、スローされたオブジェクトの質量の中心との距離を表すベクトルを使用して、コントローラーの角速度のクロス積です。

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. したがって、スローされたオブジェクトの合計速度は、コントローラーのベロシティとこの接線速度の合計になります。 `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **速度を適用する *時間* に細心の注意を** 払ってください。 ボタンが押されると、そのイベントが Bluetooth 経由でオペレーティングシステムに20ミリ秒になるまでに最大の時間がかかることがあります。 これは、コントローラーの状態の変化をポーリングしたときに、押されていない状態や押されていない状態の変化をポーリングした場合に、そのコントローラーの状態が変更される前に発生します。 さらに、ポーリング API によって提示されるコントローラーは、フレームが表示されるときに発生する可能性があることを反映するためにフォワード予測が行われます。これは、今後20ミリ秒される可能性があります。 これは、保持されたオブジェクトを *レンダリング* する場合に適していますが、ユーザーがスローをリリースした瞬間の軌道を計算するときに、オブジェクトを *ターゲット* にするための時間の問題が複雑になります。 幸いにも、11月の更新プログラムでは、 *Interactionsourcepressed* または *InteractionSourceReleased* のような Unity イベントが送信されたときに、ボタンが実際に押されたとき、または解放されたときの履歴の表示データが状態に含まれています。  スロー中に正確なコントローラーレンダリングとコントローラーターゲットを取得するには、必要に応じて、ポーリングとイベントを正しく使用する必要があります。
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

[![MR 入力 213-モーションコントローラー](images/mr213-main-600px.jpg)](https://docs.microsoft.com/windows/mixed-reality/mixed-reality-213)<br>
*MR 入力 213-モーションコントローラー*

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

私たちが用意した Unity 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。 ここから、次の構成要素に進むことができます。

> [!div class="nextstepaction"]
> [手と視線の追跡](hand-eye-in-unit.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [共有エクスペリエンス](shared-experiences-in-unity.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目

* [頭の視線入力とコミット](../../design/gaze-and-commit.md)
* [モーション コントローラー](../../design/motion-controllers.md)
