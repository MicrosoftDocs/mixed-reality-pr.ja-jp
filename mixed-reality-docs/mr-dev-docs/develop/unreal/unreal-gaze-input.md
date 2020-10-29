---
title: Unreal の入力を見つめます
description: HoloLens および Unreal Engine 用の宝石入力の設定に関するチュートリアル
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
keywords: Windows Mixed Reality、ホログラム、HoloLens 2、視線追跡、宝石入力、ヘッドマウントディスプレイ、Unreal engine
ms.openlocfilehash: 477fbdc9c7ddb3b4e890e62150651d9227d4c19e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684858"
---
# <a name="gaze-input"></a><span data-ttu-id="b9c93-104">見つめ入力</span><span class="sxs-lookup"><span data-stu-id="b9c93-104">Gaze Input</span></span>

## <a name="overview"></a><span data-ttu-id="b9c93-105">概要</span><span class="sxs-lookup"><span data-stu-id="b9c93-105">Overview</span></span>

<span data-ttu-id="b9c93-106">[Windows Mixed Reality プラグイン](https://docs.unrealengine.com/Platforms/VR/WMR/index.html)には、入力を見つめするための組み込み関数が用意されていませんが、HoloLens 2 では視線追跡がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b9c93-106">The [Windows Mixed Reality plugin](https://docs.unrealengine.com/Platforms/VR/WMR/index.html) doesn’t provide any built-in functions for gaze input, but HoloLens 2 does support eye tracking.</span></span> <span data-ttu-id="b9c93-107">実際の追跡機能は、Unreal のマウントされた **ディスプレイ** と **視点の追跡** api によって提供され、次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="b9c93-107">The actual tracking features are provided by Unreal's **Head Mounted Display** and **Eye Tracking** APIs and include:</span></span>

- <span data-ttu-id="b9c93-108">デバイス情報</span><span class="sxs-lookup"><span data-stu-id="b9c93-108">Device information</span></span>
- <span data-ttu-id="b9c93-109">センサーの追跡</span><span class="sxs-lookup"><span data-stu-id="b9c93-109">Tracking sensors</span></span>
- <span data-ttu-id="b9c93-110">向きと位置</span><span class="sxs-lookup"><span data-stu-id="b9c93-110">Orientation and position</span></span>
- <span data-ttu-id="b9c93-111">クリップペイン</span><span class="sxs-lookup"><span data-stu-id="b9c93-111">Clipping panes</span></span>
- <span data-ttu-id="b9c93-112">データと追跡情報を見つめます</span><span class="sxs-lookup"><span data-stu-id="b9c93-112">Gaze data and tracking information</span></span>

<span data-ttu-id="b9c93-113">機能の完全な一覧については、Unreal の「マウントされた [ディスプレイ](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) と [視点の追跡](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) 」ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9c93-113">You can find the full list of features in Unreal's [Head Mounted Display](https://docs.unrealengine.com/BlueprintAPI/Input/HeadMountedDisplay/index.html) and [Eye Tracking](https://docs.unrealengine.com/BlueprintAPI/EyeTracking/index.html) documentation.</span></span>

<span data-ttu-id="b9c93-114">Unreal Api に加えて、HoloLens 2 の [視線に基づく相互作用](../../design/eye-gaze-interaction.md) に関するドキュメントを参照し、 [hololens 2 の視線追跡](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) がどのように動作するかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b9c93-114">In addition to the Unreal APIs, check out the documentation on [eye-gaze-based interaction](../../design/eye-gaze-interaction.md) for HoloLens 2 and read up on how [eye tracking on HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/eye-tracking) works.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b9c93-115">視線追跡は、HoloLens 2 でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b9c93-115">Eye tracking is only supported on HoloLens 2.</span></span>

## <a name="enabling-eye-tracking"></a><span data-ttu-id="b9c93-116">目の追跡を有効にする</span><span class="sxs-lookup"><span data-stu-id="b9c93-116">Enabling eye tracking</span></span>
<span data-ttu-id="b9c93-117">Unreal の Api を使用するには、HoloLens の入力を HoloLens プロジェクト設定で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9c93-117">Gaze input needs to be enabled in the HoloLens project settings before you can use any of Unreal's APIs.</span></span> <span data-ttu-id="b9c93-118">アプリケーションが起動すると、次のスクリーンショットに同意プロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="b9c93-118">When the application starts you'll see a consent prompt shown in the screenshot below.</span></span>

- <span data-ttu-id="b9c93-119">[ **はい** ] を選択してアクセス許可を設定し、宝石入力のアクセス権を取得します。</span><span class="sxs-lookup"><span data-stu-id="b9c93-119">Select **Yes** to set the permission and get access to gaze input.</span></span> <span data-ttu-id="b9c93-120">この設定をいつでも変更する必要がある場合は、 **設定** アプリで見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="b9c93-120">If you need to change this setting at any time, it can be found in the **Settings** app.</span></span>

![アイ入力のアクセス許可](images/unreal/eye-input-permissions.png)

> [!NOTE] 
> <span data-ttu-id="b9c93-122">ステレオスコピックの追跡に必要な2つの光線はサポートされていないため、Unreal の HoloLens の追跡では、両方の目に1つの宝石があります。</span><span class="sxs-lookup"><span data-stu-id="b9c93-122">HoloLens eye tracking in Unreal only has a single gaze ray for both eyes instead of the two rays needed for stereoscopic tracking, which is not supported.</span></span>

<span data-ttu-id="b9c93-123">これで、HoloLens の入力を HoloLens 2 のアプリに Unreal に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b9c93-123">That's all the setup you'll need to start adding gaze input to your HoloLens 2 apps in Unreal.</span></span> <span data-ttu-id="b9c93-124">より簡単な入力と、それが混合現実のユーザーに与える影響の詳細については、以下のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9c93-124">More information on gaze input and how it affects users in mixed reality can be found at the links below.</span></span> <span data-ttu-id="b9c93-125">対話型エクスペリエンスを構築するときは、これらのことを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="b9c93-125">Be sure to think about these when building your interactive experiences.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="b9c93-126">次回の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="b9c93-126">Next Development Checkpoint</span></span>

<span data-ttu-id="b9c93-127">デプロイされていない実際のチェックポイントの旅に従っている場合、MRTK コアのビルディングブロックを調べています。</span><span class="sxs-lookup"><span data-stu-id="b9c93-127">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="b9c93-128">ここから、次のビルディングブロックに進むことができます。</span><span class="sxs-lookup"><span data-stu-id="b9c93-128">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="b9c93-129">ハンド トラッキング</span><span class="sxs-lookup"><span data-stu-id="b9c93-129">Hand tracking</span></span>](unreal-hand-tracking.md)

<span data-ttu-id="b9c93-130">または、Mixed Reality プラットフォームの機能と Api に移動します。</span><span class="sxs-lookup"><span data-stu-id="b9c93-130">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b9c93-131">HoloLens カメラ</span><span class="sxs-lookup"><span data-stu-id="b9c93-131">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="b9c93-132">いつでも、 [Unreal の開発チェックポイント](unreal-development-overview.md#2-core-building-blocks) に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="b9c93-132">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9c93-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9c93-133">See also</span></span>
* [<span data-ttu-id="b9c93-134">調整</span><span class="sxs-lookup"><span data-stu-id="b9c93-134">Calibration</span></span>](../../calibration.md)
* [<span data-ttu-id="b9c93-135">快適性</span><span class="sxs-lookup"><span data-stu-id="b9c93-135">Comfort</span></span>](../../design/comfort.md)
* [<span data-ttu-id="b9c93-136">視線入力とコミット</span><span class="sxs-lookup"><span data-stu-id="b9c93-136">Gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="b9c93-137">音声入力</span><span class="sxs-lookup"><span data-stu-id="b9c93-137">Voice input</span></span>](../../out-of-scope/voice-design.md)
