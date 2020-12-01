---
title: Unreal の入力を見つめます
description: HoloLens および Unreal Engine 用の宝石入力の設定に関するチュートリアル
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、ホログラム、HoloLens 2、視線追跡、宝石入力、ヘッドマウントディスプレイ、Unreal engine、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット
ms.openlocfilehash: f89638cef6b90e004f097c701c3df13edaf74fac
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354340"
---
# <a name="gaze-input"></a><span data-ttu-id="eaedd-104">見つめ入力</span><span class="sxs-lookup"><span data-stu-id="eaedd-104">Gaze Input</span></span>

<span data-ttu-id="eaedd-105">ユーザーの注目を示すには、宝石を使用します。</span><span class="sxs-lookup"><span data-stu-id="eaedd-105">Gaze is used to indicate what the user is looking at.</span></span>  <span data-ttu-id="eaedd-106">これにより、デバイス上の視線追跡カメラを使用して、ユーザーが現在見ているものと一致する非 Real ワールド空間内の射線を見つけます。</span><span class="sxs-lookup"><span data-stu-id="eaedd-106">This uses the eye tracking cameras on the device to find a ray in Unreal world space matching what the user is currently looking at.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="eaedd-107">目の追跡を有効にする</span><span class="sxs-lookup"><span data-stu-id="eaedd-107">Enabling eye tracking</span></span>

- <span data-ttu-id="eaedd-108">[ **プロジェクトの設定] > HoloLens** で、次のように **見つめ入力** 機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="eaedd-108">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![見つめ入力が強調表示されている HoloLens プロジェクト設定機能のスクリーンショット](images/unreal-gaze-img-01.png)

- <span data-ttu-id="eaedd-110">新しいアクターを作成してシーンに追加する</span><span class="sxs-lookup"><span data-stu-id="eaedd-110">Create a new actor and add it to your scene</span></span>

> [!NOTE] 
> <span data-ttu-id="eaedd-111">ステレオスコピックの追跡に必要な2つの光線はサポートされていないため、Unreal の HoloLens の追跡では、両方の目に1つの宝石があります。</span><span class="sxs-lookup"><span data-stu-id="eaedd-111">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="eaedd-112">視線追跡の使用</span><span class="sxs-lookup"><span data-stu-id="eaedd-112">Using eye tracking</span></span>

<span data-ttu-id="eaedd-113">まず、IsEyeTrackerConnected 関数を使用して、デバイスが視線追跡をサポートしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="eaedd-113">First check that the device supports eye tracking with the IsEyeTrackerConnected function.</span></span>  <span data-ttu-id="eaedd-114">これが true を返す場合は、GetGazeData を呼び出して、現在のフレームでユーザーの目が見ている場所を検索します。</span><span class="sxs-lookup"><span data-stu-id="eaedd-114">If this returns true, call GetGazeData to find where the user’s eyes are looking at during the current frame:</span></span>

![接続された関数であることを確認するためのブループリント](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="eaedd-116">HoloLens では、固定ポイントと信頼の値は使用できません。</span><span class="sxs-lookup"><span data-stu-id="eaedd-116">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="eaedd-117">ユーザーが見ている内容を検索するには、行トレースで、宝石と向きを使用します。</span><span class="sxs-lookup"><span data-stu-id="eaedd-117">To find what the user is looking at, use the gaze origin and direction in a line trace.</span></span>  <span data-ttu-id="eaedd-118">このベクトルの開始は、宝石の原点で、終点には目的の距離を乗算した値を掛けたものです。</span><span class="sxs-lookup"><span data-stu-id="eaedd-118">The start of this vector is the gaze origin and the end is the origin plus the gaze direction multiplied by the desired distance:</span></span>

!["宝石データの取得" 機能のブループリント](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="eaedd-120">ヘッドの向きの取得</span><span class="sxs-lookup"><span data-stu-id="eaedd-120">Getting head orientation</span></span>

<span data-ttu-id="eaedd-121">または、HMD の回転を使用して、ユーザーの頭の方向を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="eaedd-121">Alternatively, the HMD rotation can be used to represent the direction of the user’s head.</span></span>  <span data-ttu-id="eaedd-122">これには、宝石入力機能は必要ありませんが、目の追跡情報は表示されません。</span><span class="sxs-lookup"><span data-stu-id="eaedd-122">This does not require the Gaze Input capability but won't give you any eye tracking information.</span></span>  <span data-ttu-id="eaedd-123">適切な出力データを取得するには、ブループリントへの参照をワールドコンテキストとして追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eaedd-123">A reference to the blueprint must be added as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="eaedd-124">HMD データの取得は、Unreal 4.26 以降でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="eaedd-124">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Get HMDData 関数のブループリント](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="eaedd-126">C++ の使用</span><span class="sxs-lookup"><span data-stu-id="eaedd-126">Using C++</span></span> 

- <span data-ttu-id="eaedd-127">ゲームの build.cs ファイルで、PublicDependencyModuleNames の一覧に "EyeTracker" を追加します。</span><span class="sxs-lookup"><span data-stu-id="eaedd-127">In your game’s build.cs file, add “EyeTracker” to the PublicDependencyModuleNames list:</span></span>

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

- <span data-ttu-id="eaedd-128">"ファイル/新しい C++ クラス" で、"EyeTracker" という名前の新しい C++ アクターを作成します。</span><span class="sxs-lookup"><span data-stu-id="eaedd-128">In “File/ New C++ Class”, Create a new C++ actor called “EyeTracker”</span></span>
    - <span data-ttu-id="eaedd-129">Visual Studio ソリューションが開き、新しい EyeTracker クラスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="eaedd-129">A Visual Studio solution will open to the new EyeTracker class.</span></span> <span data-ttu-id="eaedd-130">ビルドして実行し、新しい EyeTracker アクターで Unreal のゲームを開きます。</span><span class="sxs-lookup"><span data-stu-id="eaedd-130">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="eaedd-131">[アクターの配置] ウィンドウで "EyeTracker" を検索します。</span><span class="sxs-lookup"><span data-stu-id="eaedd-131">Search for “EyeTracker” in the “Place Actors” window.</span></span>  <span data-ttu-id="eaedd-132">このクラスをゲームウィンドウにドラッグアンドドロップして、プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="eaedd-132">Drag and drop this class into the game window to add it to the project:</span></span>

![プレースアクターウィンドウが開いているアクターのスクリーンショット](images/unreal-gaze-img-06.png)

- <span data-ttu-id="eaedd-134">EyeTracker で、add for EyeTrackerFunctionLibrary および DrawDebugHelpers を追加します。</span><span class="sxs-lookup"><span data-stu-id="eaedd-134">In EyeTracker.cpp, add includes for EyeTrackerFunctionLibrary, and DrawDebugHelpers:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="eaedd-135">ティックで、デバイスが UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected を使用した視線追跡をサポートしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="eaedd-135">In Tick, check that the device supports eye tracking with UEyeTrackerFunctionLibrary::IsEyeTrackerConnected.</span></span>  <span data-ttu-id="eaedd-136">次に、UEyeTrackerFunctionLibrary:: GetGazeData から行トレースの射線の開始と終了を検索します。</span><span class="sxs-lookup"><span data-stu-id="eaedd-136">Then find the start and end of a ray for a line trace from UEyeTrackerFunctionLibrary::GetGazeData:</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="eaedd-137">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="eaedd-137">Next Development Checkpoint</span></span>

<span data-ttu-id="eaedd-138">私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は MRTK コア構成要素を探索している段階にいます。</span><span class="sxs-lookup"><span data-stu-id="eaedd-138">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="eaedd-139">ここから、次の構成要素に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="eaedd-139">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="eaedd-140">ハンド トラッキング</span><span class="sxs-lookup"><span data-stu-id="eaedd-140">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="eaedd-141">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="eaedd-141">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eaedd-142">HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="eaedd-142">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="eaedd-143">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="eaedd-143">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="eaedd-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="eaedd-144">See also</span></span>
* [<span data-ttu-id="eaedd-145">調整</span><span class="sxs-lookup"><span data-stu-id="eaedd-145">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="eaedd-146">快適性</span><span class="sxs-lookup"><span data-stu-id="eaedd-146">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="eaedd-147">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="eaedd-147">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="eaedd-148">音声入力</span><span class="sxs-lookup"><span data-stu-id="eaedd-148">Voice input</span></span>](../../out-of-scope/voice-design.md)
