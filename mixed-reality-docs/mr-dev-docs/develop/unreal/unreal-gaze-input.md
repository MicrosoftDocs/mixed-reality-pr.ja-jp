---
title: Unreal の入力を見つめます
description: HoloLens および Unreal Engine 用の宝石入力の設定に関するチュートリアル
author: hferrone
ms.author: jacksonf
ms.date: 12/9/2020
ms.topic: article
keywords: Windows Mixed Reality、ホログラム、HoloLens 2、視線追跡、宝石入力、ヘッドマウントディスプレイ、Unreal engine、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット
ms.openlocfilehash: a11573d732e739068dca8c42dd8688c0705fc5bb
ms.sourcegitcommit: f2782d0925b2075fdaa0a4ecdef3dd4f0b4e1e99
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/09/2020
ms.locfileid: "96925987"
---
# <a name="gaze-input"></a><span data-ttu-id="3c407-104">見つめ入力</span><span class="sxs-lookup"><span data-stu-id="3c407-104">Gaze Input</span></span>

<span data-ttu-id="3c407-105">Mixed reality アプリでの入力を見つめているのは、ユーザーがどのようなものを探しているのかを知ることだけです。</span><span class="sxs-lookup"><span data-stu-id="3c407-105">Gaze input in mixed reality apps is all about finding out what your users are looking at.</span></span> <span data-ttu-id="3c407-106">デバイス上の視線追跡カメラが、Unreal のワールド空間にある光線と一致すると、ユーザーのデータの視野が使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3c407-106">When the eye tracking cameras on your device match up with rays in Unreal's world space, your user's line of sight data becomes available.</span></span> <span data-ttu-id="3c407-107">見つめは、ブループリントと C++ の両方で使用できます。また、オブジェクトの対話、方法の検索、カメラのコントロールなどの機構の中核となる機能です。</span><span class="sxs-lookup"><span data-stu-id="3c407-107">Gaze can be used in both blueprints and C++, and is a core feature for mechanics like object interaction, way finding, and camera controls.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="3c407-108">目の追跡を有効にする</span><span class="sxs-lookup"><span data-stu-id="3c407-108">Enabling eye tracking</span></span>

- <span data-ttu-id="3c407-109">[ **プロジェクトの設定] > HoloLens** で、次のように **見つめ入力** 機能を有効にします。</span><span class="sxs-lookup"><span data-stu-id="3c407-109">In **Project Settings > HoloLens**, enable the **Gaze Input** capability:</span></span>

![見つめ入力が強調表示されている HoloLens プロジェクト設定機能のスクリーンショット](images/unreal-gaze-img-01.png)

- <span data-ttu-id="3c407-111">新しいアクターを作成してシーンに追加する</span><span class="sxs-lookup"><span data-stu-id="3c407-111">Create a new actor and add it to your scene</span></span>

> [!NOTE]
> <span data-ttu-id="3c407-112">非 Real の HoloLens 視線の追跡には、両方の目に1つの宝石があります。</span><span class="sxs-lookup"><span data-stu-id="3c407-112">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes.</span></span> <span data-ttu-id="3c407-113">2つの光線を必要とするステレオスコピックの追跡はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="3c407-113">Stereoscopic tracking, which requires two rays, isn't supported.</span></span>

## <a name="using-eye-tracking"></a><span data-ttu-id="3c407-114">視線追跡の使用</span><span class="sxs-lookup"><span data-stu-id="3c407-114">Using eye tracking</span></span>

<span data-ttu-id="3c407-115">まず、デバイスで **IsEyeTrackerConnected** 関数を使用した視線追跡がサポートされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3c407-115">First, check that your device supports eye tracking with the **IsEyeTrackerConnected** function.</span></span>  <span data-ttu-id="3c407-116">関数が true を返す場合は、 **GetGazeData** を呼び出して、現在のフレームでユーザーの目が見ている場所を検索します。</span><span class="sxs-lookup"><span data-stu-id="3c407-116">If the function returns true, call **GetGazeData** to find where the user’s eyes are looking at in the current frame:</span></span>

![接続された関数であることを確認するためのブループリント](images/unreal-gaze-img-02.png)

> [!NOTE]
> <span data-ttu-id="3c407-118">HoloLens では、固定ポイントと信頼の値は使用できません。</span><span class="sxs-lookup"><span data-stu-id="3c407-118">The fixation point and the confidence value are not available on HoloLens.</span></span>

<span data-ttu-id="3c407-119">行トレースで、宝石と向きを使用して、ユーザーが探している場所を正確に確認します。</span><span class="sxs-lookup"><span data-stu-id="3c407-119">Use the gaze origin and direction in a line trace to find out exactly where your users are looking.</span></span>  <span data-ttu-id="3c407-120">宝石の値は、反時計回りに開始し、原点で終了し、次に、行トレース距離を乗算した、宝石の方向に向かうベクトルです。</span><span class="sxs-lookup"><span data-stu-id="3c407-120">The gaze value is a vector, starting at the gaze origin and ending at the origin plus the gaze direction multiplied by the line trace distance:</span></span>

!["宝石データの取得" 機能のブループリント](images/unreal-gaze-img-03.png)

## <a name="getting-head-orientation"></a><span data-ttu-id="3c407-122">ヘッドの向きの取得</span><span class="sxs-lookup"><span data-stu-id="3c407-122">Getting head orientation</span></span>

<span data-ttu-id="3c407-123">また、ヘッドマウントされたディスプレイ (HMD) の回転を使用して、ユーザーの頭の方向を表すこともできます。</span><span class="sxs-lookup"><span data-stu-id="3c407-123">You can also use the rotation of the Head Mounted Display (HMD) to represent the direction of the user’s head.</span></span> <span data-ttu-id="3c407-124">ユーザーは、宝石の入力機能を有効にしなくても、ユーザーの頭を手にすることができますが、目の追跡情報は表示されません。</span><span class="sxs-lookup"><span data-stu-id="3c407-124">You can get the users head direction without enabling the Gaze Input capability, but you won't get you any eye tracking information.</span></span>  <span data-ttu-id="3c407-125">正しい出力データを取得するために、ブループリントへの参照をワールドコンテキストとして追加します。</span><span class="sxs-lookup"><span data-stu-id="3c407-125">Add a reference to the blueprint as the world context to get the correct output data:</span></span>

> [!NOTE]
> <span data-ttu-id="3c407-126">HMD データの取得は、Unreal 4.26 以降でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3c407-126">Getting HMD Data is only available in Unreal 4.26 and onwards.</span></span>

![Get HMDData 関数のブループリント](images/unreal-gaze-img-04.png)

## <a name="using-c"></a><span data-ttu-id="3c407-128">C++ の使用</span><span class="sxs-lookup"><span data-stu-id="3c407-128">Using C++</span></span>

- <span data-ttu-id="3c407-129">ゲームの **build.cs** ファイルで、 **EyeTracker** を **publicdependencymodulenames** 一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="3c407-129">In your game’s **build.cs** file, add **EyeTracker** to the **PublicDependencyModuleNames** list:</span></span>

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

- <span data-ttu-id="3c407-130">[**ファイル/新しい C++ クラス**] で、 **EyeTracker** という名前の新しい c++ アクターを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c407-130">In **File/ New C++ Class**, create a new C++ actor called **EyeTracker**</span></span>
    - <span data-ttu-id="3c407-131">Visual Studio ソリューションによって、新しい EyeTracker クラスが開きます。</span><span class="sxs-lookup"><span data-stu-id="3c407-131">A Visual Studio solution will open up the new EyeTracker class.</span></span> <span data-ttu-id="3c407-132">ビルドして実行し、新しい EyeTracker アクターで Unreal のゲームを開きます。</span><span class="sxs-lookup"><span data-stu-id="3c407-132">Build and run to open the Unreal game with the new EyeTracker actor.</span></span>  <span data-ttu-id="3c407-133">[ **アクターの配置** ] ウィンドウで "EyeTracker" を検索し、クラスをゲームウィンドウにドラッグアンドドロップして、プロジェクトに追加します。</span><span class="sxs-lookup"><span data-stu-id="3c407-133">Search for “EyeTracker” in the **Place Actors** window and drag and drop the class into the game window to add it to the project:</span></span>

![プレースアクターウィンドウが開いているアクターのスクリーンショット](images/unreal-gaze-img-06.png)

- <span data-ttu-id="3c407-135">**EyeTracker** で、Add for **EyeTrackerFunctionLibrary** および **drawdebughelpers** を追加します。</span><span class="sxs-lookup"><span data-stu-id="3c407-135">In **EyeTracker.cpp**, add includes for **EyeTrackerFunctionLibrary**, and **DrawDebugHelpers**:</span></span>

```cpp
#include "EyeTrackerFunctionLibrary.h"
#include "DrawDebugHelpers.h"
```

<span data-ttu-id="3c407-136">デバイスが、 **UEyeTrackerFunctionLibrary:: IsEyeTrackerConnected** での視線追跡をサポートしていることを確認してから、宝石データを取得します。</span><span class="sxs-lookup"><span data-stu-id="3c407-136">Check that your device supports eye tracking with **UEyeTrackerFunctionLibrary::IsEyeTrackerConnected** before trying to get any gaze data.</span></span>  <span data-ttu-id="3c407-137">視線追跡がサポートされている場合は、 **UEyeTrackerFunctionLibrary:: GetGazeData** から行トレースの射線の始点と終点を探します。</span><span class="sxs-lookup"><span data-stu-id="3c407-137">If eye tracking is supported, find the start and end of a ray for a line trace from **UEyeTrackerFunctionLibrary::GetGazeData**.</span></span> <span data-ttu-id="3c407-138">そこから、宝石ベクトルを構築し、その内容を **LineTraceSingleByChannel** に渡して、光のヒット結果をデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="3c407-138">From there, you can construct a gaze vector and pass its contents to **LineTraceSingleByChannel** to debug any ray hit results:</span></span>

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

## <a name="next-development-checkpoint"></a><span data-ttu-id="3c407-139">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="3c407-139">Next Development Checkpoint</span></span>

<span data-ttu-id="3c407-140">このガイドで説明されていない実際の開発については、MRTK コアのビルディングブロックを調べています。</span><span class="sxs-lookup"><span data-stu-id="3c407-140">If you're following the Unreal development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="3c407-141">ここから、次のビルディングブロックに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="3c407-141">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3c407-142">ハンド トラッキング</span><span class="sxs-lookup"><span data-stu-id="3c407-142">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="3c407-143">または、Mixed Reality プラットフォームの機能と API に移動します。</span><span class="sxs-lookup"><span data-stu-id="3c407-143">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3c407-144">HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="3c407-144">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="3c407-145">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#2-core-building-blocks)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="3c407-145">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c407-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c407-146">See also</span></span>
* [<span data-ttu-id="3c407-147">調整</span><span class="sxs-lookup"><span data-stu-id="3c407-147">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="3c407-148">快適性</span><span class="sxs-lookup"><span data-stu-id="3c407-148">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="3c407-149">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="3c407-149">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="3c407-150">音声入力</span><span class="sxs-lookup"><span data-stu-id="3c407-150">Voice input</span></span>](../../out-of-scope/voice-design.md)
