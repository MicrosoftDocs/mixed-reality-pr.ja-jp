---
title: Unreal の入力を見つめます
description: HoloLens および Unreal Engine 用の宝石入力の設定に関するチュートリアル
author: hferrone
ms.author: jacksonf
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、ホログラム、HoloLens 2、視線追跡、宝石入力、ヘッドマウントディスプレイ、Unreal engine、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット
ms.openlocfilehash: d0470c5abbefce797254aa9f2030519d3347aaab
ms.sourcegitcommit: 9c640c96e2270ef69edd46f1b12acb00b373554d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96578891"
---
# <a name="gaze-input"></a>見つめ入力

ユーザーの注目を示すには、宝石を使用します。  これにより、デバイス上の視線追跡カメラを使用して、ユーザーが現在見ているものと一致する非 Real ワールド空間内の射線を見つけます。

## <a name="enabling-eye-tracking"></a>目の追跡を有効にする

- [ **プロジェクトの設定] > HoloLens** で、次のように **見つめ入力** 機能を有効にします。

![見つめ入力が強調表示されている HoloLens プロジェクト設定機能のスクリーンショット](images/unreal-gaze-img-01.png)

- 新しいアクターを作成してシーンに追加する

> [!NOTE] 
> ステレオスコピックの追跡に必要な2つの光線はサポートされていないため、Unreal の HoloLens の追跡では、両方の目に1つの宝石があります。

## <a name="using-eye-tracking"></a>視線追跡の使用

まず、IsEyeTrackerConnected 関数を使用して、デバイスが視線追跡をサポートしていることを確認します。  これが true を返す場合は、GetGazeData を呼び出して、現在のフレームでユーザーの目が見ている場所を検索します。

![接続された関数であることを確認するためのブループリント](images/unreal-gaze-img-02.png)

> [!NOTE]
> HoloLens では、固定ポイントと信頼の値は使用できません。

ユーザーが見ている内容を検索するには、行トレースで、宝石と向きを使用します。  このベクトルの開始は、宝石の原点で、終点には目的の距離を乗算した値を掛けたものです。

!["宝石データの取得" 機能のブループリント](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a>ヘッドの向きの取得

または、HMD の回転を使用して、ユーザーの頭の方向を表すことができます。  これには、宝石入力機能は必要ありませんが、目の追跡情報は表示されません。  適切な出力データを取得するには、ブループリントへの参照をワールドコンテキストとして追加する必要があります。

> [!NOTE]
> HMD データの取得は、Unreal 4.26 以降でのみ使用できます。

![Get HMDData 関数のブループリント](images/unreal-gaze-img-04.png)

## <a name="using-c"></a>C++ の使用 

- ゲームの build.cs ファイルで、PublicDependencyModuleNames の一覧に "EyeTracker" を追加します。

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

- "ファイル/新しい C++ クラス" で、"EyeTracker" という名前の新しい C++ アクターを作成します。
    - Visual Studio ソリューションが開き、新しい EyeTracker クラスが表示されます。 ビルドして実行し、新しい EyeTracker アクターで Unreal のゲームを開きます。  [アクターの配置] ウィンドウで "EyeTracker" を検索します。  このクラスをゲームウィンドウにドラッグアンドドロップして、プロジェクトに追加します。

![プレースアクターウィンドウが開いているアクターのスクリーンショット](images/unreal-gaze-img-06.png)

- EyeTracker で、add for EyeTrackerFunctionLibrary および DrawDebugHelpers を追加します。

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

ティックで、デバイスが UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected を使用した視線追跡をサポートしていることを確認します。  次に、UEyeTrackerFunctionLibrary:: GetGazeData から行トレースの射線の開始と終了を検索します。

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

私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。 ここから、次の構成要素に進むことができます。 

> [!div class="nextstepaction"]
> [ハンド トラッキング](unreal-hand-tracking.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [HoloLens カメラ](unreal-hololens-camera.md)

いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目
* [調整](../../calibration.md)
* [快適性](../../design/comfort.md)
* [視線入力とコミット](../../design/gaze-and-commit.md)
* [音声入力](../../out-of-scope/voice-design.md)
