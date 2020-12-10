---
ms.openlocfilehash: 23bba22801f61f6b4814991c8b3bde68d2c5f6b7
ms.sourcegitcommit: fbeff51cae92add88d2b960c9b7bbfb04d5a0291
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97002743"
---
# <a name="425"></a>[4.25](#tab/425)

ブループリントを使用するには、 **Windows Mixed Reality HMD** で任意のアクションを検索します。

![ハンド光線 BP](../images/unreal/hand-rays-bp.png)

C++ でこれらのファイルにアクセスするには、 `WindowsMixedRealityFunctionLibrary.h` 呼び出し元のコードファイルの先頭にを含めます。

### <a name="enum"></a>列挙型

また、[ **Ehmdinputコントローラー**] の下にある入力ケースにアクセスできます。このボタンは、ブループリントで使用できます。

![入力コントローラーボタン](../images/unreal/input-controller-buttons.png)

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
    * HoloLens 2 で、エアタップ、宝石、およびコミットによってトリガーされます。または、 [音声入力](../unreal-voice-input.md) を有効にした "選択" を言います。
* ユーザーによってトリガーされるイベントを **把握** します。
    * ホログラムでユーザーの指を閉じることによって、HoloLens 2 でトリガーされます。

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

次のように、ブループリントを使用して PointerPoseInfo 構造体にアクセスできます。

![ポインターのポーズ情報 BP](../images/unreal/pointer-pose-info-bp.png)

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

### <a name="functions"></a>機能

次に示すすべての関数は、継続的な監視を可能にするすべてのフレームに対して呼び出すことができます。

1. **ポインターの取得の詳細** 情報は、現在のフレームにおけるハンドレイの方向に関する完全な情報を返します。

建築

![ポインターの表示情報の取得](../images/unreal/get-pointer-pose-info.png)

C++:
```cpp
static FPointerPoseInfo UWindowsMixedRealityFunctionLibrary::GetPointerPoseInfo(EControllerHand hand);
```

2. **Grasped** は、現在のフレームに Grasped がある場合に true を返します。

建築

![Grasped BP](../images/unreal/is-grasped-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsGrasped(EControllerHand hand);
```

3. **Select 押さ** れた場合、ユーザーが現在のフレームで select をトリガーした場合は true を返します。

建築

![選択された BP (BP)](../images/unreal/is-select-pressed-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsSelectPressed(EControllerHand hand);
```

4. 現在のフレームでイベントまたはボタンがトリガーされた場合、**ボタンがクリックされる** と true が返されます。

建築

![ボタンが BP をクリックしました](../images/unreal/is-button-clicked-bp.png)

C++:
```cpp
static bool UWindowsMixedRealityFunctionLibrary::IsButtonClicked(EControllerHand hand, EHMDInputControllerButtons button);
```

5. **コントローラー追跡状態の取得** は、現在のフレームの追跡状態を返します。

建築

![コントローラー追跡ステータス BP の取得](../images/unreal/get-controller-tracking-status-bp.png)

C++:
```cpp
static EHMDTrackingStatus UWindowsMixedRealityFunctionLibrary::GetControllerTrackingStatus(EControllerHand hand);
```
# <a name="426"></a>[4.26](#tab/426)

手の形のデータを取得するには、前のセクションの「Get Motion Controller Data 関数」を使用する必要があります。 返される構造体には、ハンドレイを作成するために使用できる2つのパラメーター ( **目標位置** と **目標の回転**) が含まれています。 これらのパラメーターは、エルボウによって送られる射線を形成します。 これらを取得して、指されているホログラムを見つける必要があります。

次に示すのは、ハンドレイがウィジェットをヒットし、カスタムヒット結果を設定するかどうかを判断する例です。

![Get motion controller データ関数のブループリント](../images/unreal-hand-tracking-img-04.png) 