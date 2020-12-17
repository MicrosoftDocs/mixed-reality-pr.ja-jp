---
title: Unity 用入力移植ガイド
description: Unity で Windows Mixed Reality の入力を処理する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 12/9/2020
ms.topic: article
keywords: 入力、unity、移植
ms.openlocfilehash: 97280ff260729bfc2042f7760fa3950e949e27a4
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613266"
---
# <a name="input-porting-guide-for-unity"></a>Unity 用入力移植ガイド

2つの方法のいずれかを使用して、入力ロジックを Windows Mixed Reality に移植できます。 1つ目は、Unity の一般的な入力です。 GetButton/GetAxis Api は複数のプラットフォームにまたがっています。 2つ目は、Windows 固有の XR です。付い.入力 Api は、モーションコントローラーと HoloLens ハンド専用の豊富なデータを提供します。

## <a name="general-inputgetbuttongetaxis-apis"></a>一般的な入力。 GetButton/GetAxis Api

Unity では、現在、一般的な入力である GetButton/GetAxis Api を使用して [、OCULUS sdk](https://docs.unity3d.com/Manual/OculusControllers.html) と [openvr sdk](https://docs.unity3d.com/Manual/OpenVRControllers.html)の入力を公開しています。 アプリが既にこれらの Api を入力に使用している場合は、Windows Mixed Reality でのモーションコントローラーをサポートするための最も簡単なパスは、GetButton/GetAxis Api です。 入力マネージャーでは、ボタンと軸の再マップのみが必要になります。

詳細については、「 [unity のボタン/軸マッピングテーブル](../unity/gestures-and-motion-controllers-in-unity.md#unity-buttonaxis-mapping-table) 」と「 [共通 unity api の概要](../unity/gestures-and-motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis)」を参照してください。

## <a name="windows-specific-xrwsainput-apis"></a>Windows 固有の XR。付い.入力 Api

アプリが各プラットフォームのカスタム入力ロジックを既に作成している場合は、 **Unityengine. XR** 名前空間の Windows 固有の空間入力 api を使用できます。 ここから、位置の精度やソースの種類などの追加情報にアクセスして、HoloLens で両手とコントローラーを区別できるようにします。

詳細については、「 [UnityEngine. XR api の概要](../unity/gestures-and-motion-controllers-in-unity.md#windows-specific-apis-xrwsainput)」を参照してください。

## <a name="grip-pose-vs-pointing-pose"></a>グリップポーズとポインティングポーズ

Windows Mixed Reality では、さまざまなフォームファクターのモーションコントローラーがサポートされています。 各コントローラーの設計は、ユーザーの手の位置と、アプリがコントローラーをレンダリングするときに使用する自然な "転送" の方向との間の関係において異なります。

これらのコントローラーをより適切に表現するために、相互作用ソースごとに調査できる2種類の方法があります。

* **グリップ** は、HoloLens によって検出されたハンドの位置を表します。または、運動コントローラーを持つパームです。
    * イマーシブヘッドセットでは、この方法を使用して、 **ユーザーの手** や、剣や銃などの **ユーザーの手に保持** されているオブジェクトをレンダリングすることをお勧めします。
    * **グリップの位置**: コントローラーを自然に保持するときのパーム重心。グリップ内の位置を中央に配置するように左右に調整されます。
    * **グリップの向きの右軸**: 手を完全に開いて平らな5本の指を作成した場合 (左側のパームから前方、右側のパームから後方)、
    * **グリップの向きの前方軸**: コントローラーを保持している場合と同様に、手を部分的に閉じると、非拇印によって形成されたチューブによって "前方" を指します。
    * **グリップの向きの上位軸**: 右および順方向の定義によって暗黙的に示される上位軸。
    * このグリップには、Unity のクロスベンダ入力 API (XR) を使用してアクセスでき **[ます。InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)。GetLocalPosition/Rotation**) または Windows 固有の API (**TryGetPosition/rotation**) を使用して、グリップを要求します。
* **ポインター** は、前方を指し示すコントローラーの先端を表します。
    * この方法は、コントローラーモデル自体をレンダリングするときに **UI をポイント** するときに raycast するために使用することをお勧めします。
    * 現時点では、ポインターのポーズは、Windows 固有の API (**Sourcestate/Rotation**) を介してのみ使用でき、ポインターのポーズを要求します。

これらの発生座標はすべて Unity のワールド座標で表現されます。

## <a name="see-also"></a>関連項目
* [モーションコントローラー]()../../design/motion-controllers.md)
* [Unity でのジェスチャとモーション コントローラー](../unity/gestures-and-motion-controllers-in-unity.md)
* [UnityEngine. XR](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.html)
* [UnityEngine. XR 追跡](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html)
* [移植ガイド](porting-guides.md)
