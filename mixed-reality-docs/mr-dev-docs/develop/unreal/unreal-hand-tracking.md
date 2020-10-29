---
title: Unreal での手の追跡
description: Unreal でハンドトラッキングを使用する方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、手動追跡、Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、Mixed Reality、開発、機能、ドキュメント、ガイド、ホログラム、ゲーム開発
ms.openlocfilehash: 5bc120f802c2160282befd1ce6cb8025be21cbaa
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683082"
---
# <a name="hand-tracking-in-unreal"></a>Unreal での手の追跡

## <a name="overview"></a>概要

ハンドトラッキングシステムは、ユーザーのてのひらとフィンガーを入力として使用します。 コード内で使用するすべての指、パーム全体、およびハンドジェスチャの位置と回転を取得できます。 

## <a name="hand-pose"></a>手の形

手の形で、アクティブなユーザーの手と指を追跡し、それを入力として使用できます。これは、ブループリントと C++ を通じてアクセスできます。 詳細な技術情報については、Unreal の「 [Windows.](https://docs.microsoft.com/uwp/api/windows.perception.people.handpose) ..」 API を参照してください。 Unreal API は、Unreal エンジンとの間で同期されたティックを使用して、データを座標系として送信します。

### <a name="understanding-the-bone-hierarchy"></a>ボーン階層について

この `EWMRHandKeypoint` 列挙型は、手のボーン階層を記述します。 ブループリントに記載されている各ハンドキーポイントを見つけることができます。

![ハンドキーポイント BP](images/hand-keypoint-bp.png)

完全な C++ 列挙型を以下に示します。
```cpp
enum class EWMRHandKeypoint : uint8
{
    Palm,
    Wrist,
    ThumbMetacarpal,
    ThumbProximal,
    ThumbDistal,
    ThumbTip,
    IndexMetacarpal,
    IndexProximal,
    IndexIntermediate,
    IndexDistal,
    IndexTip,
    MiddleMetacarpal,
    MiddleProximal,
    MiddleIntermediate,
    MiddleDistal,
    MiddleTip,
    RingMetacarpal,
    RingProximal,
    RingIntermediate,
    RingDistal,
    RingTip,
    LittleMetacarpal,
    LittleProximal,
    LittleIntermediate,
    LittleDistal,
    LittleTip
};
```

各列挙型のケースの数値は、 [HandJointKind](https://docs.microsoft.com/uwp/api/windows.perception.people.handjointkind) テーブルで確認できます。 次の図は、一致する列挙型のケースを持つ完全なレイアウトを示しています。

![手スケルトン](../native/images/hand-skeleton.png)
 
### <a name="supporting-hand-tracking"></a>ハンドトラッキングのサポート

手動追跡機能を追加することによって、ブループリントで **手動追跡を** 使用することができます **> Windows Mixed Reality** :

![ハンドトラッキング BP](images/unreal/hand-tracking-bp.png)

この関数は `true` 、デバイスでハンドトラッキングがサポートされている場合、および `false` ハンドトラッキングが使用できない場合にを返します。

![ハンドトラッキング BP のサポート](images/unreal/supports-hand-tracking-bp.png)

C++: 

`WindowsMixedRealityHandTrackingFunctionLibrary.h` を含めます。

```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::SupportsHandTracking()
```

### <a name="getting-hand-tracking"></a>ハンドトラッキングの取得
**GetHandJointTransform** を使用して、空間データを手動で返すことができます。 データはすべてのフレームを更新しますが、フレーム内にいる場合は、返された値がキャッシュされます。 パフォーマンス上の理由から、この関数では大きなロジックを使用しないことをお勧めします。 

![ハンドジョイント変換の取得](images/unreal/get-hand-joint-transform.png)
 
C++:
```cpp
static bool UWindowsMixedRealityHandTrackingFunctionLibrary::GetHandJointTransform(EControllerHand Hand, EWMRHandKeypoint Keypoint, FTransform& OutTransform, float& OutRadius)
```

関数パラメーターの内訳:

* **手** : ユーザーの左側または右側
* **Keypoint** –ハンドのボーンです。 
* **Transform** –ボーンの基本の座標と向きを調整します。 次のボーンのベースを要求して、ボーンの終点の変換データを取得できます。 特別なヒントのボーンは、distal の終わりを示します。 
* **Radius** : ボーンのベースの半径。
* **戻り値** -ボーンがこのフレームを追跡している場合は true、ボーンが追跡されていない場合は false。

## <a name="hand-live-link-animation"></a>ハンドライブリンクアニメーション
[Live Link プラグイン](https://docs.unrealengine.com/Engine/Animation/LiveLinkPlugin/index.html)を使用して、手の形でアニメーションに公開されます。

Windows Mixed Reality とライブリンクプラグインが有効になっている場合: 
1. [ **ウィンドウ > ライブリンク** ] を選択して、ライブリンクエディターウィンドウを開きます。 
2. [ **ソース** ] をクリックし、[ **Windows Mixed Reality ハンドトラッキングソース** を有効にする]

![ライブリンクのソース](images/unreal/live-link-source.png)
 
ソースを有効にし、アニメーションのアセットを開くと、[ **プレビューシーン** ] タブの [ **アニメーション** ] セクションが表示されなくなります (詳細については、「ライブリンクのドキュメント」を参照してください。プラグインがベータ版であるため、プロセスは後で変更される可能性があります)。

![ライブリンクアニメーション](images/unreal/live-link-animation.png)
 
ハンドアニメーション階層は、の場合と同じ `EWMRHandKeypoint` です。 アニメーションは、 **WindowsMixedRealityHandTrackingLiveLinkRemapAsset** を使用して再ターゲットできます。

![ライブリンクアニメーション2](images/unreal/live-link-animation2.png)
 
また、エディターでサブクラス化することもできます。

![ライブリンクの再マップ](images/unreal/live-link-remap.png)
 
## <a name="accessing-hand-mesh-data"></a>手メッシュデータへのアクセス

![手動メッシュ](images/unreal/hand-mesh.png)

手作業のメッシュデータにアクセスするには、次のことを行う必要があります。
- **Arsessionconfig** 資産を選択し、 **AR の設定-> 世界のマッピング** 設定を展開して、[追跡された **ジオメトリからメッシュデータを生成** する] チェックボックスをオンにします。 

既定のメッシュパラメーターを次に示します。

1.  遮蔽にメッシュデータを使用する
2.  メッシュデータの競合を生成する
3.  メッシュデータの Nav メッシュを生成します
4.  ワイヤーフレームでメッシュデータをレンダリングする–生成されたメッシュを示すデバッグパラメーター

これらのパラメーター値は、空間マッピングメッシュと手動メッシュの既定値として使用されます。 これらは、任意のメッシュのブループリントまたはコードでいつでも変更できます。

### <a name="c-api-reference"></a>C++ API リファレンス 
`EEARObjectClassification`を使用すると、すべての追跡可能なオブジェクトで手動メッシュ値を検索できます。
```cpp
enum class EARObjectClassification : uint8
{
    // Other types 
    HandMesh,
};
```

システムによって追跡可能なオブジェクト (手メッシュを含む) が検出されると、次のデリゲートが呼び出されます。 

```cpp
class FARSupportInterface 
{
    public:
    // Other params 
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableAdded)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableUpdated)
    DECLARE_AR_SI_DELEGATE_FUNCS(OnTrackableRemoved)
};
```

デリゲートハンドラーが以下の関数シグネチャに従うことを確認します。

```cpp
void UARHandMeshComponent::OnTrackableAdded(UARTrackedGeometry* Added)
```

メッシュデータには、を使用してアクセスでき  `UARTrackedGeometry::GetUnderlyingMesh` ます。

```cpp
UMRMeshComponent* UARTrackedGeometry::GetUnderlyingMesh()
```


### <a name="blueprint-api-reference"></a>ブループリント API リファレンス

ブループリントを使用するには、次のようにします。
1. **ARTrackableNotify** コンポーネントをブループリントアクターに追加する

![ARTrackable 通知](images/unreal/ar-trackable-notify.png)
 
2. [ **詳細** ] パネルにアクセスし、[ **イベント** ] セクションを展開します。 

![ARTrackable 通知2](images/unreal/ar-trackable-notify2.png)
 
3. イベントグラフ内の次のノードを使用して、追跡したジオメトリの追加/更新/削除を上書きします。

![ARTrackable 通知で](images/unreal/on-artrackable-notify.png)
 
## <a name="hand-rays"></a>手の線

[SpatialPointerInteractionSourcePose](https://docs.microsoft.com/uwp/api/windows.ui.input.spatial.spatialpointerinteractionsourcepose) API を公開する C++ とブループリントの両方で、ポインティングデバイスとしてハンドレイを使用できます。

すべての関数の結果がすべてのフレームに変更されるため、すべての関数が呼び出し可能になることに注意してください。 純粋関数と純粋でない関数、または呼び出し可能関数の詳細については、「[関数](https://docs.unrealengine.com/en-US/Engine/Blueprints/UserGuide/Functions/index.html#purevs.impure)のブループリントユーザー guid」を参照してください。

ブループリントを使用するには、 **Windows Mixed Reality HMD** で任意のアクションを検索します。

![ハンド光線 BP](images/unreal/hand-rays-bp.png)
 
C++ でこれらのファイルにアクセスするには、 `WindowsMixedRealityFunctionLibrary.h` 呼び出し元のコードファイルの先頭にを含めます。

### <a name="enum"></a>列挙型
また、[ **Ehmdinputコントローラー** ] の下にある入力ケースにアクセスできます。このボタンは、ブループリントで使用できます。

![入力コントローラーボタン](images/unreal/input-controller-buttons.png)

C++ でのアクセスには、 `EHMDInputControllerButtons` 列挙型クラスを使用します。
```cpp
enum class EHMDInputControllerButtons : uint8
{
    Select,
    Grasp,
//......
};
```

次に、該当する2つの列挙型ケースの内訳を示します。
* **Select** -ユーザーがトリガーした選択イベント。 
    * このイベントは、外気タップ、宝石、およびコミットによって HoloLens 2 でトリガーされます。または、 [音声入力](unreal-voice-input.md) を有効にした "選択" を言います。 
* ユーザーによってトリガーされるイベントを **把握** します。 
    * このイベントは、ホログラムでユーザーの指を閉じることで、HoloLens 2 でトリガーできます。 

次に示す列挙体を使用して、C++ でのハンドメッシュの追跡状態にアクセスでき `EHMDTrackingStatus` ます。

```cpp
enum class EHMDTrackingStatus : uint8
{
    NotTracked,
    //......
    Tracked
};
```

次に、該当する2つの列挙型ケースの内訳を示します。
* **Nottracked** –-ハンドは表示されません
* **追跡** –ハンドは完全に追跡されます。

### <a name="struct"></a>構造体
PointerPoseInfo 構造体は、次のような手作業のデータに関する情報を提供します。
* **Origin** –ハンドオリジン
* **方向** –ハンドの方向
* **アップ** (手動)
* **方向** -方向の四元数 
* **ステータスの追跡** -現在の追跡状態

これには、次に示すように、ブループリントを使用してアクセスできます。

![ポインターのポーズ情報 BP](images/unreal/pointer-pose-info-bp.png)

C++ の場合:

```cpp
struct FPointerPoseInfo
{
    FVector Origin;
    FVector Direction;
    FVector Up;
    FQuat Orientation;
    EHMDTrackingStatus TrackingStatus;
};
```

### <a name="functions"></a>関数

次に示すすべての関数は、継続的な監視を可能にするすべてのフレームに対して呼び出すことができます。 

1. **ポインターの取得の詳細** 情報は、現在のフレームにおけるハンドレイの方向に関する完全な情報を返します。 

建築

![ポインターの表示情報の取得](images/unreal/get-pointer-pose-info.png)

C++: 
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Grasped** は、現在のフレームに Grasped がある場合に true を返します。

建築

![Grasped BP](images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```
 
3. **Select 押さ** れた場合、ユーザーが現在のフレームで select をトリガーした場合は true を返します。

建築

![選択された BP (BP)](images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. 現在のフレームでイベントまたはボタンがトリガーされた場合、 **ボタンがクリックされる** と true が返されます。

建築

![ボタンが BP をクリックしました](images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **コントローラー追跡状態の取得** は、現在のフレームの追跡状態を返します。

建築

![コントローラー追跡ステータス BP の取得](images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```

## <a name="gestures"></a>ジェスチャ

Hololens 2 では、空間ジェスチャを追跡できます。これは、これらのジェスチャを入力としてキャプチャできることを意味します。 ジェスチャの詳細については、「 [HoloLens 2 の基本的な使用方法](https://docs.microsoft.com/hololens/hololens2-basic-usage) 」を参照してください。

のブループリント関数は、呼び出し元のコードファイルにを追加することで、 **Windows Mixed Reality 空間入力** と C++ 関数の下に `WindowsMixedRealitySpatialInputFunctionLibrary.h` あります。

![キャプチャジェスチャ](images/unreal/capture-gestures.png)

### <a name="enum"></a>列挙型
<!-- Deprecated
The `ESPatialInputAxisGestureType` enum describes spatial axis gestures and are [fully documented](../../out-of-scope/deprecated/holograms-211.md).
-->
建築 

![ジェスチャの種類](images/unreal/gesture-type.png)

C++:
```cpp
enum class ESpatialInputAxisGestureType : uint8
{
    None = 0,
    Manipulation = 1,
    Navigation = 2,
    NavigationRails = 3
};
```

### <a name="function"></a>機能
ジェスチャのキャプチャを有効または無効にするには、関数を使用 `CaptureGestures` します。 有効なジェスチャによって入力イベントが発生した場合、この関数はジェスチャキャプチャが成功した場合はを返し、エラーが発生した場合はを返し `true` `false` ます。

建築

![キャプチャジェスチャ BP](images/unreal/capture-gestures-bp.png)

C++:
```cpp
static bool UWindowsMixedRealitySpatialInputFunctionLibrary::CaptureGestures(
    bool Tap = false, 
    bool Hold = false, 
    ESpatialInputAxisGestureType AxisGesture = ESpatialInputAxisGestureType::None, 
    bool NavigationAxisX = true, 
    bool NavigationAxisY = true, 
    bool NavigationAxisZ = true);
```

次に示すのは、[ブループリント] と [C++: キーイベント] で確認できる主要なイベントです。 ![](images/unreal/key-events.png)

![主要イベント2](images/unreal/key-events2.png)
```cpp
const FKey FSpatialInputKeys::TapGesture(TapGestureName);
const FKey FSpatialInputKeys::DoubleTapGesture(DoubleTapGestureName);
const FKey FSpatialInputKeys::HoldGesture(HoldGestureName);

const FKey FSpatialInputKeys::LeftTapGesture(LeftTapGestureName);
const FKey FSpatialInputKeys::LeftDoubleTapGesture(LeftDoubleTapGestureName);
const FKey FSpatialInputKeys::LeftHoldGesture(LeftHoldGestureName);

const FKey FSpatialInputKeys::RightTapGesture(RightTapGestureName);
const FKey FSpatialInputKeys::RightDoubleTapGesture(RightDoubleTapGestureName);
const FKey FSpatialInputKeys::RightHoldGesture(RightHoldGestureName);

const FKey FSpatialInputKeys::LeftManipulationGesture(LeftManipulationGestureName);
const FKey FSpatialInputKeys::LeftManipulationXGesture(LeftManipulationXGestureName);
const FKey FSpatialInputKeys::LeftManipulationYGesture(LeftManipulationYGestureName);
const FKey FSpatialInputKeys::LeftManipulationZGesture(LeftManipulationZGestureName);

const FKey FSpatialInputKeys::LeftNavigationGesture(LeftNavigationGestureName);
const FKey FSpatialInputKeys::LeftNavigationXGesture(LeftNavigationXGestureName);
const FKey FSpatialInputKeys::LeftNavigationYGesture(LeftNavigationYGestureName);
const FKey FSpatialInputKeys::LeftNavigationZGesture(LeftNavigationZGestureName);


const FKey FSpatialInputKeys::RightManipulationGesture(RightManipulationGestureName);
const FKey FSpatialInputKeys::RightManipulationXGesture(RightManipulationXGestureName);
const FKey FSpatialInputKeys::RightManipulationYGesture(RightManipulationYGestureName);
const FKey FSpatialInputKeys::RightManipulationZGesture(RightManipulationZGestureName);

const FKey FSpatialInputKeys::RightNavigationGesture(RightNavigationGestureName);
const FKey FSpatialInputKeys::RightNavigationXGesture(RightNavigationXGestureName);
const FKey FSpatialInputKeys::RightNavigationYGesture(RightNavigationYGestureName);
const FKey FSpatialInputKeys::RightNavigationZGesture(RightNavigationZGestureName);
```

## <a name="next-development-checkpoint"></a>次回の開発チェックポイント

デプロイされていない実際のチェックポイントの旅に従っている場合、MRTK コアのビルディングブロックを調べています。 ここから、次のビルディングブロックに進むことができます。 

> [!div class="nextstepaction"]
> [ローカル空間アンカー](unreal-spatial-anchors.md)

または、Mixed Reality プラットフォームの機能と Api に移動します。

> [!div class="nextstepaction"]
> [HoloLens カメラ](unreal-hololens-camera.md)

いつでも、 [Unreal の開発チェックポイント](unreal-development-overview.md#2-core-building-blocks) に戻ることができます。