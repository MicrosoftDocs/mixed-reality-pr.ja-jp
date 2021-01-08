---
title: DirectX での手とモーション コントローラー
description: ネイティブ DirectX アプリでハンドトラッキングとモーションコントローラーを使用するための開発者ガイドを使ってみる。
author: caseymeekhof
ms.author: cmeekhof
ms.date: 08/04/2020
ms.topic: article
keywords: ハンド、モーションコントローラー、directx、入力、ホログラム、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: 43673602b01a1937953d16fcca9b4c4f4d3fd33a
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009542"
---
# <a name="hands-and-motion-controllers-in-directx"></a>DirectX での手とモーション コントローラー

> [!NOTE]
> この記事は、従来の WinRT ネイティブ Api に関連しています。  新しいネイティブアプリプロジェクトの場合は、 **[OPENXR API](openxr-getting-started.md)** を使用することをお勧めします。

Windows Mixed Reality では、ハンドコントローラー入力と [モーションコントローラー](../../design/motion-controllers.md) 入力の両方が、windows の. [UI.](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial) 空間名前空間にある空間入力 api を介して処理されます。 これにより、 **選択** などの一般的なアクションを簡単に処理できるようになります。

## <a name="getting-started"></a>作業の開始

Windows Mixed Reality で空間入力にアクセスするには、SpatialInteractionManager インターフェイスから開始します。  このインターフェイスにアクセスするには、通常はアプリの起動時に  [SpatialInteractionManager:: GetForCurrentView](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getforcurrentview)を呼び出します。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

SpatialInteractionManager interactionManager = SpatialInteractionManager::GetForCurrentView();
```

SpatialInteractionManager の仕事は、入力のソースを表す [SpatialInteractionSources](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)へのアクセスを提供することです。  システムで使用できる SpatialInteractionSources には3種類あります。
* **ハンド** は、ユーザーの検出されたハンドを表します。 手動ソースは、HoloLens の基本的なジェスチャから HoloLens 2 の完全な形の追跡まで、デバイスに基づいてさまざまな機能を提供します。 
* **コントローラー** は、対になっているモーションコントローラーを表します。 モーションコントローラーは、トリガー、メニューボタン、ボタン、タッチパッド向け、thumbsticks など、さまざまな機能を提供できます。
* **音声** は、ユーザーの音声読み上げシステムで検出されたキーワードを表します。 たとえば、このソースでは、ユーザーが "Select" と表示されるたびに、Select press と release が挿入されます。

ソースのフレームごとのデータは、  [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) インターフェイスによって表されます。 アプリケーションでイベントドリブンモデルとポーリングベースのモデルのどちらを使用するかに応じて、このデータにアクセスする2つの方法があります。

### <a name="event-driven-input"></a>イベントドリブン入力
SpatialInteractionManager は、アプリがリッスンできる多数のイベントを提供します。  例として、   [Sourcepressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)れた、[SourceReleased、 [sourcepressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated)などがあります。

たとえば、次のコードは、MyApp イベントに対して MyApp:: OnSourcePressed れたイベントハンドラーをフックします。  これにより、アプリは任意の種類の相互作用ソースの押下を検出できます。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
interactionManager.SourcePressed({ this, &MyApp::OnSourcePressed });

```

この押されたイベントは、キーを押したときの対応する SpatialInteractionSourceState と共に、アプリに非同期的に送信されます。 アプリまたはゲームエンジンは、すぐに処理を開始したり、入力処理ルーチンでイベントデータをキューに入れたりすることができます。 次に、SourcePressed れたイベントのイベントハンドラー関数を示します。この関数は、[選択] ボタンが押されたかどうかを確認します。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

void MyApp::OnSourcePressed(SpatialInteractionManager const& sender, SpatialInteractionSourceEventArgs const& args)
{
    if (args.PressKind() == SpatialInteractionPressKind::Select)
    {
        // Select button was pressed, update app state
    }
}
```

上のコードでは、デバイスの主なアクションに対応する ' Select ' の押下だけがチェックされます。 たとえば、HoloLens でのエアタップの実行や、モーションコントローラーでのトリガーの取り出しなどです。  ' Select ' は、ターゲットとしているホログラムをアクティブ化するユーザーの意図を表します。  SourcePressed イベントは、さまざまなボタンとジェスチャに対して起動されます。また、SpatialInteractionSource の他のプロパティを調べて、そのようなケースをテストできます。

### <a name="polling-based-input"></a>ポーリングベースの入力
また、SpatialInteractionManager を使用して、すべてのフレームに対する入力の現在の状態をポーリングすることもできます。  これを行うには、すべてのフレームで [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) を呼び出します。  この関数は、アクティブな[SpatialInteractionSource](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)ごとに1つの[SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)を含む配列を返します。 これは、アクティブなモーションコントローラーごとに1つ、つまり、' select ' コマンドが最近発音された場合は、1つずつ、もう1つは音声用です。 その後、各 SpatialInteractionSourceState のプロパティを調べて、アプリケーションへの入力を実行できます。 

ポーリング方法を使用して ' select ' アクションを確認する方法の例を次に示します。 *予測* 変数は、 [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)から取得できる [HolographicFramePrediction](https://docs.microsoft.com//uwp/api/Windows.Graphics.Holographic.HolographicFramePrediction)オブジェクトを表します。

```cpp
using namespace winrt::Windows::UI::Input::Spatial;

auto interactionManager = SpatialInteractionManager::GetForCurrentView();
auto sourceStates = m_spatialInteractionManager.GetDetectedSourcesAtTimestamp(prediction.Timestamp());

for (auto& sourceState : sourceStates)
{
    if (sourceState.IsSelectPressed())
    {
        // Select button is down, update app state
    }
}
```

各 SpatialInteractionSource には ID があり、これを使用して新しいソースを識別し、フレーム間の既存のソースを関連付けることができます。  移動するたびに新しい ID を取得して、視界を入力しますが、コントローラー Id はセッションの間は静的のままです。  [Sourcedetected](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcedetected)や[Sourcedetected](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcelost)などの SpatialInteractionManager のイベントを使用して、ユーザーがデバイスのビューを手に入れたり、移動したりしたとき、またはモーションコントローラーがオン/オフになっているとき、またはペア/対になっていないときに反応することができます。

### <a name="predicted-vs-historical-poses"></a>予測と履歴のポーズ
GetDetectedSourcesAtTimestamp にはタイムスタンプパラメーターがあります。 これにより、予測または履歴の状態を要求し、データを供給することができるため、空間の相互作用を他の入力のソースと関連付けることができます。 たとえば、現在のフレームに手の位置を表示する場合は、 [HolographicFrame](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe)によって提供される予測タイムスタンプを渡すことができます。 これにより、システムは、描画されたフレーム出力と密接に一致するようにハンド位置を順方向に予測して、認識される待機時間を最小限に抑えることができます。

ただし、このような予測があると、相互作用ソースをターゲットにするための最適なポイントが生成されません。 たとえば、[モーションコントローラー] ボタンが押されている場合、そのイベントが Bluetooth を通じてオペレーティングシステムにバブルアップされるまでに最大20ミリ秒かかることがあります。 同様に、ユーザーが手の形でジェスチャを実行すると、システムによってジェスチャが検出され、アプリがそのジェスチャをポーリングするまでに、一定の時間がかかることがあります。 アプリが状態の変更をポーリングするまでに、その相互作用をターゲットとするために使用されるヘッドとハンドは、実際には過去に発生しました。 現在の HolographicFrame のタイムスタンプを GetDetectedSourcesAtTimestamp に渡すことによってターゲットを設定した場合は、フレームが表示された時点で、その対象のレイに対して予測が転送されます。これは、今後20ミリ秒を超える可能性があります。 これは、相互作用ソースを *レンダリング* する場合に適していますが、ユーザーの対象が過去に発生したため、相互作用を *対象* とした時間の問題が複雑になります。

幸い、 [Sourcepressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed)れている、[SourceReleased]、および [ [sourcepressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourceupdated) ] イベントは、各入力イベントに関連付けられた履歴 [状態](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) を提供します。  これには、 [Trygetポインター](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose)によって使用可能な履歴のヘッドとハンドのポーズと、他の api に渡してこのイベントと関連付けることができる履歴 [タイムスタンプ](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.timestamp) が含まれます。

次のベストプラクティスに従って、各フレームでハンドおよびコントローラーをレンダリングして対象を設定します。
* 各フレームを **レンダリング** するには、アプリは、現在のフレームの photon 時間における各相互作用ソースの **フォワード予測** を **ポーリング** する必要があります。  各フレーム [GetDetectedSourcesAtTimestamp](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.getdetectedsourcesattimestamp) を呼び出し、 [HolographicFrame:: currentprediction](https://docs.microsoft.com//uwp/api/windows.graphics.holographic.holographicframe.currentprediction)によって提供される予測タイムスタンプを渡すことによって、すべての相互作用ソースをポーリングできます。
* プレスまたはリリースを対象とする手動または **コントローラー** の場合、アプリでは、そのイベントの **履歴** ヘッドまたはハンド raycasting に基づいて、押されたイベントまたは解放された **イベント** を処理する必要があります。 このターゲット設定を取得するには、 [Sourcepressed](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcepressed) れたイベントまたは [SourceReleased](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionmanager.sourcereleased) イベントを処理し、イベント引数から [State](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceeventargs.state) プロパティを取得して、その [trygetポインタポーズ](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygetpointerpose) メソッドを呼び出します。

## <a name="cross-device-input-properties"></a>デバイス間の入力プロパティ
SpatialInteractionSource API では、さまざまな機能を備えたコントローラーおよびハンドトラッキングシステムがサポートされています。 これらの機能の多くは、デバイスの種類によって一般的です。 たとえば、ハンドトラッキングとモーションコントローラーは、どちらも ' select ' アクションと3D 位置を提供します。 可能な限り、API はこれらの共通機能を SpatialInteractionSource の同じプロパティにマップします。  これにより、アプリケーションは幅広い種類の入力をより簡単にサポートできるようになります。 次の表では、サポートされるプロパティと、入力の種類間での比較方法について説明します。

| プロパティ | 説明 | HoloLens (第1世代) ジェスチャ | モーションコントローラー | 手によるハンド|
|--- |--- |--- |--- |--- |
| [SpatialInteractionSource::**きき**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.handedness) | Right または left/controller。 | サポートされていません | サポートされています | サポートされています |
| [SpatialInteractionSourceState::**Isselectpressed** れました](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isselectpressed) | プライマリボタンの現在の状態。 | エアタップ | トリガー | 緩やかに出た空気タップ (垂直ピンチ) |
| [SpatialInteractionSourceState::**IsGrasped**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.isgrasped) | グラブボタンの現在の状態です。 | サポートされていません | グラブボタン | ピンチまたは閉じた手 |
| [SpatialInteractionSourceState::**IsMenuPressed**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.ismenupressed) | メニューボタンの現在の状態。    | サポートされていません | メニューボタン | サポートされていません |
| [SpatialInteractionSourceLocation::**Position**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.position) | コントローラー上の手またはグリップ位置の XYZ 位置。 | パームの場所 | グリップの発生位置 | パームの場所 |
| [SpatialInteractionSourceLocation::**Orientation**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation.orientation) | コントローラー上の手やグリップの向きを表す四元数。 | サポートされていません | グリップの向き | パームの向き |
| [SpatialPointerInteractionSourcePose::**Position**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.position#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_Position) | ポイントの原点。 | サポートされていません | サポートされています | サポートされています |
| [SpatialPointerInteractionSourcePose::**Forwarddirection**](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose.forwarddirection#Windows_UI_Input_Spatial_SpatialPointerInteractionSourcePose_ForwardDirection) | ポイントの方向。 | サポートされていません | サポートされています | サポートされています |

上記の一部のプロパティは、すべてのデバイスで使用できるわけではありません。また、API はこのことをテストする手段を提供します。 たとえば、 [SpatialInteractionSource:: IsGraspSupported](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.isgraspsupported) プロパティを調べて、ソースがつかみアクションを提供するかどうかを判断できます。

### <a name="grip-pose-vs-pointing-pose"></a>グリップポーズとポインティングポーズ

Windows Mixed Reality では、さまざまなフォームファクターのモーションコントローラーがサポートされています。  また、独自の追跡システムもサポートしています。  これらのシステムはすべて、ユーザーの手の中でオブジェクトをポイントまたは表示するためにアプリが使用する必要がある自然な位置と自然な "転送" 方向との間には異なる関係があります。  これらのすべてをサポートするために、ハンドトラッキングとモーションコントローラーの両方に3種類の3D が用意されています。  1つ目は、ユーザーの手の位置を表すグリップです。  2つ目の方法は、ユーザーの手またはコントローラーからのポイントを示すポイントを指します。 そのため、 **ユーザーの手** や、剣や銃などの **ユーザーの手に保持** されているオブジェクトをレンダリングする場合は、グリップを使用します。 たとえば、ユーザーが * * をポイントしているときに、コントローラーまたはハンドから raycast する場合は、ポイントアンドポーズを使用します。

**グリップ** にアクセスするには、 [SpatialInteractionSourceState::P R.:: trygetlocation (...)](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourceproperties.trygetlocation#Windows_UI_Input_Spatial_SpatialInteractionSourceProperties_TryGetLocation_Windows_Perception_Spatial_SpatialCoordinateSystem_)を使用します。次のように定義されています。
* **グリップの位置**: コントローラーを自然に保持するときのパーム重心。グリップ内の位置を中央に配置するように左右に調整されます。
* **グリップの向きの右軸**: 手を完全に開いて平らな5本の指を作成した場合 (左側のパームから前方、右側のパームから後方)、
* **グリップの向きの前方軸**: ハンドを部分的に閉じた場合 (コントローラーを保持している場合と同様)、非表示の指で形成されたチューブを通過する光線。
* **グリップの向きの上位軸**: 右および順方向の定義によって暗黙的に示される上位軸。

**ポインター** の [SpatialInteractionSourceState::P R.:: trygetlocation (...):: sourcepointer ポーズ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractionsourcelocation#Windows_UI_Input_Spatial_SpatialInteractionSourceLocation_SourcePointerPose)または [SpatialInteractionSourceState:: trygetlocation ポーズ (...):: Trygetinteractionsourceポーズ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerpose#Windows_UI_Input_Spatial_SpatialPointerPose_TryGetInteractionSourcePose_Windows_UI_Input_Spatial_SpatialInteractionSource_)にアクセスできます。

## <a name="controller-specific-input-properties"></a>コントローラー固有の入力プロパティ
コントローラーの場合、SpatialInteractionSource には追加機能を持つコントローラープロパティがあります。
* **Hasthumbstick:** True の場合、コントローラーにはサムスティックがあります。 SpatialInteractionSourceState の " [コントローラーのプロパティ](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialinteractioncontrollerproperties) " プロパティを調べて、スティックの x 値と y 値 (ThumbstickX と ThumbstickY) と押された状態 (IsThumbstickPressed) を取得します。
* **HasTouchpad:** True の場合、コントローラーにはタッチパッドがあります。 SpatialInteractionSourceState の "コントローラーのプロパティ" プロパティを調べて、タッチパッドの x 値と y 値 (TouchpadX と TouchpadY) を取得し、ユーザーがパッドにタッチしている (IsTouchpadTouched) かどうかを確認し、タッチパッドを押す (Istouchpadtouched れた) かどうかを確認します。
* **SimpleHapticsController:** コントローラーの SimpleHapticsController API を使用すると、コントローラーの haptics 機能を調べることができます。また、haptic フィードバックを制御することもできます。

タッチパッドとサムスティックの範囲は、両方の軸 (下から上、左から右) に対して-1 ~ 1 です。 SpatialInteractionSourceState:: SelectPressedValue プロパティを使用してアクセスされる、アナログトリガーの範囲には、0 ~ 1 の範囲があります。 値1は、IsSelectPressed れた値が true であると相関します。その他の値は、IsSelectPressed れた値が false と関連付けられます。

## <a name="articulated-hand-tracking"></a>手による追跡
Windows Mixed Reality API は、HoloLens 2 でのように、独自の追跡を完全にサポートしています。 独自の追跡を使用すると、アプリケーションに直接操作やポイントアンドコミット入力モデルを実装できます。 また、完全にカスタムな対話を作成するために使用することもできます。

### <a name="hand-skeleton"></a>手スケルトン
トレーラー型の追跡では、さまざまな種類の相互作用を可能にする25のジョイントスケルトンが提供されます。  スケルトンには、インデックス/中間/リング/リトルフィンガー、4つの関節 (つまみ)、および1つの手首結合に対して5つの関節が用意されています。  この手首は、階層のベースとして機能します。 次の図は、スケルトンのレイアウトを示しています。

![手スケルトン](images/hand-skeleton.png)

ほとんどの場合、各結合には、それが表すボーンに基づいた名前が付けられます。  すべてのジョイントに2つのボーンがあるため、その場所の子ボーンに基づいて各結合に名前を付ける規則を使用します。  子ボーンは、手首からさらにボーンとして定義されます。  たとえば、"Index 位" という結合には、インデックス位ボーンの開始位置とそのボーンの方向が含まれます。  これには、ボーンの終了位置は含まれません。  これが必要な場合は、階層内の次の結合 ("中間インデックス" という結合) から取得します。

25の階層結合に加えて、システムには、パームジョイントが用意されています。  通常、パームはスケルトン構造の一部とは見なされません。 これは、手の形と向きを取得するための便利な方法としてのみ提供されています。

各結合について、次の情報が提供されています。

| Name | 説明 |
|--- |--- |
|[位置] | 要求されたすべての座標系で使用可能な、ジョイントの3D 位置。 |
|Orientation | 要求されたすべての座標系で使用可能な、ボーンの3D の向き。 |
|Radius | ジョイント位置のスキンの表面までの距離。 指の幅に依存する直接の対話や視覚エフェクトをチューニングする場合に便利です。 |
|精度 | この共同の情報についてシステムがどの程度自信を持っているかについてのヒントを提供します。 |

[SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)の関数を使用して、ハンドスケルトンデータにアクセスできます。  関数は [TryGetHandPose](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate.trygethandpose#Windows_UI_Input_Spatial_SpatialInteractionSourceState_TryGetHandPose)と呼ばれ、この関数は、"" と [いう名前の](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose)オブジェクトを返します。  変換元が変換をサポートしていない場合、この関数は null を返します。  準備ができたら、必要な結合の名前を使用して [Trygetjoint](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose.trygetjoint#Windows_Perception_People_HandPose_TryGetJoint_Windows_Perception_Spatial_SpatialCoordinateSystem_Windows_Perception_People_HandJointKind_Windows_Perception_People_JointPose__)を呼び出して、現在のジョイントデータを取得できます。  データは [JointPose](https://docs.microsoft.com//uwp/api/windows.perception.people.jointpose) 構造体として返されます。  次のコードは、インデックスのフィンガーヒントの位置を取得します。 変数は [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)の *インスタンスを表し* ます。

```cpp
using namespace winrt::Windows::Perception::People;
using namespace winrt::Windows::Foundation::Numerics;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    JointPose joint;
    if (handPose.TryGetJoint(desiredCoordinateSystem, HandJointKind::IndexTip, joint))
    {
        float3 indexTipPosition = joint.Position;

        // Do something with the index tip position
    }
}
```

### <a name="hand-mesh"></a>手動メッシュ

修飾されたハンドトラッキング API を使用すると、完全に非フォーム化可能な三角形ハンドメッシュが可能になります。  このメッシュは、ハンドスケルトンと共にリアルタイムで変形でき、視覚エフェクトや高度な物理手法に役立ちます。  手メッシュにアクセスするには、最初に[SpatialInteractionSource](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource)で[TryCreateHandMeshObserverAsync](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsource.trycreatehandmeshobserverasync)を呼び出して[HandMeshObserver](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver)オブジェクトを作成する必要があります。  これは、ソースごとに1回だけ実行する必要があります。通常は、最初に表示されます。  つまり、この関数を呼び出して、手動で視界に入ったときに HandMeshObserver オブジェクトを作成します。  これは非同期関数なので、ここで少しの同時実行を処理する必要があります。  使用できるようになったら、 [GetTriangleIndices](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.gettriangleindices#Windows_Perception_People_HandMeshObserver_GetTriangleIndices_System_UInt16___)を呼び出して、三角形インデックスバッファーの HandMeshObserver オブジェクトに要求できます。  インデックスはフレームに対して変更されないため、これらを一度取得し、ソースの有効期間にわたってキャッシュすることができます。  インデックスは、回転順に指定します。

次のコードは、切り離された std:: thread をスピンアップしてメッシュオブザーバーを作成し、メッシュオブザーバーが使用可能になったときにインデックスバッファーを抽出します。  SpatialInteractionSourceState と呼ばれる変数から開始します。これ *は、追跡* されたハンドを表す、 [](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)のインスタンスです。

```cpp
using namespace Windows::Perception::People;

std::thread createObserverThread([this, currentState]()
{
    HandMeshObserver newHandMeshObserver = currentState.Source().TryCreateHandMeshObserverAsync().get();
    if (newHandMeshObserver)
    {
        unsigned indexCount = newHandMeshObserver.TriangleIndexCount();
        vector<unsigned short> indices(indexCount);
        newHandMeshObserver.GetTriangleIndices(indices);

        // Save the indices and handMeshObserver for later use - and use a mutex to synchronize access if needed!
     }
});
createObserverThread.detach();
```
デタッチされたスレッドの開始は、非同期呼び出しを処理するためのオプションの1つにすぎません。  または、C++/winrtでサポートされている新しい [co_await](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) 機能を使用することもできます。

HandMeshObserver オブジェクトを作成したら、それに対応する SpatialInteractionSource がアクティブになるまで、そのオブジェクトを保持する必要があります。  次に、各フレームに対して、 [Getvertexstateforpose](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshobserver.getvertexstateforpose) を呼び出して、頂点の対象と [なるポーズを](https://docs.microsoft.com//uwp/api/windows.perception.people.handpose) 表すのに渡すことによって、ハンドを表す最新の頂点バッファーを要求できます。  バッファー内の各頂点は、位置と法線を持ちます。  手メッシュの頂点の現在のセットを取得する方法の例を次に示します。  前と同様に、 [SpatialInteractionSourceState](https://docs.microsoft.com//uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate)*変数は、の* インスタンスを表します。

```cpp
using namespace winrt::Windows::Perception::People;

auto handPose = currentState.TryGetHandPose();
if (handPose)
{
    std::vector<HandMeshVertex> vertices(handMeshObserver.VertexCount());
    auto vertexState = handMeshObserver.GetVertexStateForPose(handPose);
    vertexState.GetVertices(vertices);

    auto meshTransform = vertexState.CoordinateSystem().TryGetTransformTo(desiredCoordinateSystem);
    if (meshTransform != nullptr)
    {
        // Do something with the vertices and mesh transform, along with the indices that you saved earlier
    }
}
```

スケルトンジョイントとは対照的に、ハンドメッシュ API では、頂点の座標系を指定することはできません。  代わりに、 [HandMeshVertexState](https://docs.microsoft.com//uwp/api/windows.perception.people.handmeshvertexstate) は、頂点が提供される座標系を指定します。  次 [に、Trygettransformto](https://docs.microsoft.com//uwp/api/windows.perception.spatial.spatialcoordinatesystem.trygettransformto#Windows_Perception_Spatial_SpatialCoordinateSystem_TryGetTransformTo_Windows_Perception_Spatial_SpatialCoordinateSystem_) 呼び出して、必要な座標系を指定することで、メッシュ変換を取得できます。  頂点を操作するときは常に、このメッシュ変換を使用する必要があります。  この方法では、特にレンダリング専用のメッシュを使用している場合に、CPU のオーバーヘッドが軽減されます。

## <a name="gaze-and-commit-composite-gestures"></a>複合ジェスチャを見つめてコミットする
特に HoloLens (最初の gen) で、SpatialGestureRecognizer 入力モデルを使用するアプリケーションでは、"select" イベントの上に構築された複合ジェスチャを有効にするために使用できるオプションの[](https://msdn.microsoft.com/library/windows/apps/windows.ui.input.spatial.spatialgesturerecognizer.aspx)が用意されています。  アプリでは、SpatialInteractionManager からホログラムの SpatialGestureRecognizer に対する相互作用をルーティングすることにより、手動での押下と解放を処理することなく、両手、音声、および空間入力デバイス全体で、タップ、ホールド、操作、およびナビゲーションイベントを一貫して検出できます。

SpatialGestureRecognizer は、要求するジェスチャのセット間で最小限のあいまいさを排除するだけです。 たとえば、Tap を要求した場合、ユーザーは指を好きな限り下に置くことができ、タップが引き続き発生する可能性があります。 タップとホールドの両方を要求した場合、指を押したままにすると、ジェスチャがホールドに昇格し、Tap が発生しなくなります。

SpatialGestureRecognizer を使用するには、SpatialInteractionManager の [Interactiondetected](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialInteractionManager.InteractionDetected) イベントを処理し、そこで公開されている SpatialPointerPose を取得します。 ユーザーの周囲のホログラムとサーフェスメッシュとの交差部分を使用して、ユーザーがどのような操作を行っているかを判断するには、この攻撃からのユーザーの頭を見つめます。 次に、 [CaptureInteraction](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.CaptureInteraction) メソッドを使用して、イベント引数の SpatialInteraction をターゲットホログラムの SpatialGestureRecognizer にルーティングします。 これにより、作成時に、または[TrySetGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureRecognizer.TrySetGestureSettings)によって、その認識エンジンで設定された[SpatialGestureSettings](https://msdn.microsoft.com/library/windows/apps/xaml/Windows.UI.Input.Spatial.SpatialGestureSettings)に従って、その相互作用の解釈が開始されます。

HoloLens (最初のジェネレーション) では、相互作用とジェスチャは、ユーザーの位置でレンダリングや対話を行うのではなく、ユーザーの頭を見つめてターゲットを導き出す必要があります。 相互作用が開始されたら、操作やナビゲーションジェスチャと同様に、ハンドの相対的な動きを使ってジェスチャを制御できます。

## <a name="see-also"></a>関連項目
* [DirectX でのヘッド視線入力とアイ視線入力](gaze-in-directx.md)
* [直接操作入力モデル](../../design/direct-manipulation.md)
* [ポイントアンドコミット入力モデル](../../design/point-and-commit.md)
* [入力モデルの宝石とコミット](../../design/gaze-and-commit.md)
* [モーション コントローラー](../../design/motion-controllers.md)
