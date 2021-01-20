---
title: Unreal の入力を見つめます
description: アプリの監視機能とヘッドの向きを使用して、非 Real の HoloLens アプリを設定して使用する方法について説明します。
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality、ホログラム、HoloLens 2、視線追跡、宝石入力、ヘッドマウントディスプレイ、Unreal engine、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット
ms.openlocfilehash: 0c5191534313b94a5382d1065f5a5dd1a208bb49
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98579982"
---
# <a name="gaze-input"></a>見つめ入力

Mixed reality アプリでの入力を見つめているのは、ユーザーがどのようなものを探しているのかを知ることだけです。 デバイス上の視線追跡カメラが、Unreal のワールド空間にある光線と一致すると、ユーザーのデータの視野が使用できるようになります。 見つめは、ブループリントと C++ の両方で使用できます。また、オブジェクトの対話、方法の検索、カメラのコントロールなどの機構の中核となる機能です。

## <a name="enabling-eye-tracking"></a>目の追跡を有効にする

- [ **プロジェクトの設定] > HoloLens** で、次のように **見つめ入力** 機能を有効にします。

![見つめ入力が強調表示されている HoloLens プロジェクト設定機能のスクリーンショット](images/unreal-gaze-img-01.png)

- 新しいアクターを作成してシーンに追加する

> [!NOTE]
> 非 Real の HoloLens 視線の追跡には、両方の目に1つの宝石があります。 2つの光線を必要とするステレオスコピックの追跡はサポートされていません。

## <a name="using-eye-tracking"></a>視線追跡の使用

まず、デバイスで **IsEyeTrackerConnected** 関数を使用した視線追跡がサポートされていることを確認します。  関数が true を返す場合は、 **GetGazeData** を呼び出して、現在のフレームでユーザーの目が見ている場所を検索します。

![接続された関数であることを確認するためのブループリント](images/unreal-gaze-img-02.png)

> [!NOTE]
> HoloLens では、固定ポイントと信頼の値は使用できません。

行トレースで、宝石と向きを使用して、ユーザーが探している場所を正確に確認します。  宝石の値は、反時計回りに開始し、原点で終了し、次に、行トレース距離を乗算した、宝石の方向に向かうベクトルです。

!["宝石データの取得" 機能のブループリント](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>ヘッドの向きの取得

また、ヘッドマウントされたディスプレイ (HMD) の回転を使用して、ユーザーの頭の方向を表すこともできます。 ユーザーは、宝石の入力機能を有効にしなくても、ユーザーの頭を手にすることができますが、目の追跡情報は表示されません。  正しい出力データを取得するために、ブループリントへの参照をワールドコンテキストとして追加します。

> [!NOTE]
> HMD データの取得は、Unreal 4.26 以降でのみ使用できます。

![Get HMDData 関数のブループリント](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>C++ の使用

- ゲームの **build.cs** ファイルで、 **EyeTracker** を **publicdependencymodulenames** 一覧に追加します。

```cpp
PublicDependencyModuleNames.AddRange(
    new string[] {
        "Core",
        "CoreUObject",
        "Engine",
        "InputCore",
        "EyeTracker"
});
```

- [**ファイル/新しい C++ クラス**] で、 **EyeTracker** という名前の新しい c++ アクターを作成します。
    - Visual Studio ソリューションによって、新しい EyeTracker クラスが開きます。 ビルドして実行し、新しい EyeTracker アクターで Unreal のゲームを開きます。  [ **アクターの配置** ] ウィンドウで "EyeTracker" を検索し、クラスをゲームウィンドウにドラッグアンドドロップして、プロジェクトに追加します。

![プレースアクターウィンドウが開いているアクターのスクリーンショット](images/unreal-gaze-img-06.png)

- **EyeTracker** で、Add for **EyeTrackerFunctionLibrary** および **drawdebughelpers** を追加します。

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

デバイスが、 **UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected** での視線追跡をサポートしていることを確認してから、宝石データを取得します。  視線追跡がサポートされている場合は、 **UEyeTrackerFunctionLibrary:: GetGazeData** から行トレースの射線の始点と終点を探します。 そこから、宝石ベクトルを構築し、その内容を **LineTraceSingleByChannel** に渡して、光のヒット結果をデバッグできます。

```cpp
void AEyeTracker::Tick(float DeltaTime)
{
    Super::Tick(DeltaTime);

    if(UEyeTrackerFunctionLibrary::IsEyeTrackerConnected())
    {
        FEyeTrackerGazeData GazeData;
        if(UEyeTrackerFunctionLibrary::GetGazeData(GazeData))
        {
            FVector Start = GazeData.GazeOrigin;
            FVector End = GazeData.GazeOrigin + GazeData.GazeDirection * 100;

            FHitResult Hit Result;
            if (GWorld->LineTraceSingleByChannel(HitResult, Start, End, ECollisionChannel::ECC_Visiblity))
            {
                DrawDebugCoordinateSystem(GWorld, HitResult.Location, FQuat::Identity.Rotator(), 10);
            }
        }
    }
}
```

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

用意されている Unreal 開発体験に従っている場合、MRTK コア構成要素を探索している段階にいます。 ここから、次の構成要素を続けることができます。

> [!div class="nextstepaction"]
> [ハンド トラッキング](unreal-hand-tracking.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [HoloLens カメラ](unreal-hololens-camera.md)

いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目
* [調整](/hololens/hololens-calibration)
* [快適性](../../design/comfort.md)
* [視線入力とコミット](../../design/gaze-and-commit.md)
* [音声入力](../../out-of-scope/voice-design.md)