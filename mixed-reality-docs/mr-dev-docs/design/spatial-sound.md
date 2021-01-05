---
title: 混合現実のオーディオ
description: 混合現実のオーディオを使用すると、UI インタラクションのユーザーの信頼を高め、ユーザーのエクスペリエンスをこちらことができます。
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: 空間サウンド, サラウンドサウンド, 3d オーディオ, 3d サウンド, 空間オーディオ, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット, HoloLens, MRTK, Mixed Reality ツールキット, ケーススタディ, acoustics
ms.openlocfilehash: b65a4ff3dc64863f02f1459fa0c3adc5d34b0703
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/01/2021
ms.locfileid: "97848174"
---
# <a name="audio-in-mixed-reality"></a><span data-ttu-id="ed2cd-104">混合現実のオーディオ</span><span class="sxs-lookup"><span data-stu-id="ed2cd-104">Audio in mixed reality</span></span>

<span data-ttu-id="ed2cd-105">オーディオは、混合現実の設計と生産性の重要な部分です。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-105">Audio is an essential part of design and productivity in mixed reality.</span></span> <span data-ttu-id="ed2cd-106">サウンドは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-106">Sound can:</span></span>
* <span data-ttu-id="ed2cd-107">ジェスチャと音声のやり取りでユーザーの信頼度を高めます。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-107">Increase user confidence in gesture and voice interactions.</span></span>
* <span data-ttu-id="ed2cd-108">次の手順にユーザーを案内します。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-108">Guide users to next steps.</span></span>
* <span data-ttu-id="ed2cd-109">仮想オブジェクトを実際の環境と効果的に結合します。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-109">Effectively combine virtual objects with the real world.</span></span>

<span data-ttu-id="ed2cd-110">HoloLens を含む mixed reality ヘッドセットの待機時間の短いヘッドトラッキングでは、高品質の HRTF ベースの spatialization がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-110">The low-latency head tracking of mixed reality headsets, including HoloLens, supports high-quality HRTF-based spatialization.</span></span> <span data-ttu-id="ed2cd-111">アプリケーションでオーディオを spatialize するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-111">You can spatialize audio in your application to:</span></span>
* <span data-ttu-id="ed2cd-112">ビジュアル要素に注目します。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-112">Call attention to visual elements.</span></span>
* <span data-ttu-id="ed2cd-113">ユーザーが実際の環境について認識できるようにします。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-113">Help users maintain awareness of their real-world surroundings.</span></span>

<span data-ttu-id="ed2cd-114">Acoustics により深い接続ホログラムが混合現実の世界になります。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-114">Acoustics more deeply connect holograms to the mixed-reality world.</span></span> <span data-ttu-id="ed2cd-115">環境とオブジェクトの状態に関する手掛かりを提供します。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-115">It provides cues about the environment and object state.</span></span>

<span data-ttu-id="ed2cd-116">[オーディオを使用するデザインの詳細な例を](spatial-sound-design.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-116">See detailed [examples of design that uses audio](spatial-sound-design.md).</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="device-support"></a><span data-ttu-id="ed2cd-117">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="ed2cd-117">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="ed2cd-118"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="ed2cd-118"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="ed2cd-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (最初の世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="ed2cd-119"><a href="../hololens-hardware-details.md"><strong>HoloLens (first gen)</strong></a></span></span></td>
        <td><span data-ttu-id="ed2cd-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="ed2cd-120"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="ed2cd-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="ed2cd-121"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ed2cd-122">空間化</span><span class="sxs-lookup"><span data-stu-id="ed2cd-122">Spatialization</span></span></td>
        <td><span data-ttu-id="ed2cd-123">✔️</span><span class="sxs-lookup"><span data-stu-id="ed2cd-123">✔️</span></span></td>
        <td><span data-ttu-id="ed2cd-124">✔️</span><span class="sxs-lookup"><span data-stu-id="ed2cd-124">✔️</span></span></td>
        <td><span data-ttu-id="ed2cd-125">✔️</span><span class="sxs-lookup"><span data-stu-id="ed2cd-125">✔️</span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="ed2cd-126">Spatialization ハードウェアアクセラレーション</span><span class="sxs-lookup"><span data-stu-id="ed2cd-126">Spatialization hardware acceleration</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="ed2cd-127">✔️</span><span class="sxs-lookup"><span data-stu-id="ed2cd-127">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a><span data-ttu-id="ed2cd-128">Mixed reality でのサウンドの使用</span><span class="sxs-lookup"><span data-stu-id="ed2cd-128">Use of sounds in mixed reality</span></span>

<span data-ttu-id="ed2cd-129">[Mixed reality でサウンドを使用する](spatial-sound-design.md) には、タッチおよびキーボードおよびマウスアプリケーションとは異なるアプローチが必要です。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-129">[Use of sounds in mixed reality](spatial-sound-design.md) requires a different approach than in touch and keyboard-and-mouse applications.</span></span> <span data-ttu-id="ed2cd-130">サウンド設計の主な決定事項には、どのようなサウンドを spatialize し、どのような対話を sonify にするかが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-130">Key sound design decisions include which sounds to spatialize and which interactions to sonify.</span></span> <span data-ttu-id="ed2cd-131">これらの決定は、ユーザーの自信、生産性、学習曲線に大きな影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-131">These decisions strongly effect user confidence, productivity, and learning curve.</span></span>

### <a name="case-studies"></a><span data-ttu-id="ed2cd-132">ケース スタディ</span><span class="sxs-lookup"><span data-stu-id="ed2cd-132">Case studies</span></span>

<span data-ttu-id="ed2cd-133">HoloTour は事実上、世界中の tourist と歴史的なサイトにユーザーを移動させることになります。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-133">HoloTour virtually takes users to tourist and historical sites around the world.</span></span> <span data-ttu-id="ed2cd-134">HoloTour のケーススタディについては、「 [サウンドのデザイン」を](case-study-spatial-sound-design-for-holotour.md) 参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-134">See the [Sound design for HoloTour](case-study-spatial-sound-design-for-holotour.md) case study.</span></span> <span data-ttu-id="ed2cd-135">特殊なマイクとレンダリングのセットアップを使用して、サブジェクトスペースがキャプチャされました。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-135">A special microphone and rendering setup were used to capture the subject spaces.</span></span>

<span data-ttu-id="ed2cd-136">RoboRaid は、HoloLens の高エネルギー shooter です。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-136">RoboRaid is a high-energy shooter for HoloLens.</span></span> <span data-ttu-id="ed2cd-137">RoboRaid ケーススタディ [のサウンド設計](case-study-using-spatial-sound-in-roboraid.md) では、空間オーディオが最大限効果を得るために使用された設計上の選択肢について説明します。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-137">The [Sound design for RoboRaid](case-study-using-spatial-sound-in-roboraid.md) case study describes the design choices that were made to ensure spatial audio was used to the fullest dramatic effect.</span></span>

## <a name="spatialization"></a><span data-ttu-id="ed2cd-138">空間化</span><span class="sxs-lookup"><span data-stu-id="ed2cd-138">Spatialization</span></span>

<span data-ttu-id="ed2cd-139">Spatialization は、空間オーディオの方向コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-139">Spatialization is the directional component of spatial audio.</span></span> <span data-ttu-id="ed2cd-140">7.1 home シアターセットアップの場合、spatialization は loudspeakers 間のパンと同様に簡単です。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-140">For a 7.1 home theater setup, spatialization is as simple as panning between loudspeakers.</span></span> <span data-ttu-id="ed2cd-141">しかし、混合現実のヘッドホンでは、精度と快適さを実現するために HRTF ベースのテクノロジを使用することが不可欠です。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-141">But for headphones in mixed reality, it's essential to use an HRTF-based technology for accuracy and comfort.</span></span> <span data-ttu-id="ed2cd-142">Windows には HRTF ベースの spatialization が用意されており、このサポートは HoloLens 2 でハードウェアアクセラレータを利用しています。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-142">Windows offers HRTF-based spatialization, and this support is hardware-accelerated on HoloLens 2.</span></span>

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a><span data-ttu-id="ed2cd-143">Spatialize ですか。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-143">Should I spatialize?</span></span>

<span data-ttu-id="ed2cd-144">Spatialization は、mixed reality アプリケーションの多くのサウンドを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-144">Spatialization can improve many sounds in mixed-reality applications.</span></span> <span data-ttu-id="ed2cd-145">Spatialization はリスナーの頭から音を受け取り、世界に置きます。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-145">Spatialization takes a sound out of the listener's head and places it in the world.</span></span> <span data-ttu-id="ed2cd-146">アプリケーションで spatialization を効果的に使用するための推奨事項については、「 [空間サウンドの設計](spatial-sound-design.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-146">For suggestions on effective use of spatialization in your application, see [Spatial sound design](spatial-sound-design.md).</span></span>

### <a name="spatializer-personalization"></a><span data-ttu-id="ed2cd-147">Spatializer のパーソナル化</span><span class="sxs-lookup"><span data-stu-id="ed2cd-147">Spatializer personalization</span></span>

<span data-ttu-id="ed2cd-148">HRTFs は、頻度の範囲内の耳間のレベルとフェーズの差を操作します。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-148">HRTFs manipulate the level and phase differences between ears across the frequency spectrum.</span></span> <span data-ttu-id="ed2cd-149">これらは、物理的なモデルと、人間の頭、torso および ear 図形 (pinnae) の測定値に基づいています。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-149">They're based on physical models and measurements of human head, torso, and ear shapes (pinnae).</span></span> <span data-ttu-id="ed2cd-150">脳は、これらの違いに反応して、認識された方向にサウンドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-150">Our brains respond to these differences to provide perceived direction in sound.</span></span>

<span data-ttu-id="ed2cd-151">各個人には、独自の ear 図形、ヘッドサイズ、および耳の位置があります。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-151">Every individual has a unique ear shape, head size, and ear position.</span></span> <span data-ttu-id="ed2cd-152">したがって、最適な HRTFs が準拠しています。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-152">So the best HRTFs conform to you.</span></span> <span data-ttu-id="ed2cd-153">Spatialization の精度を高めるために、HoloLens はヘッドセット表示の pupilary 距離 (IPD) を使用して、ヘッドサイズに対して HRTFs を調整します。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-153">To increase spatialization accuracy, HoloLens uses your inter-pupilary distance (IPD) from the headset displays to adjust the HRTFs for your head size.</span></span>

### <a name="spatializer-platform-support"></a><span data-ttu-id="ed2cd-154">Spatializer プラットフォームのサポート</span><span class="sxs-lookup"><span data-stu-id="ed2cd-154">Spatializer platform support</span></span>

<span data-ttu-id="ed2cd-155">Windows では、 [ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)を使用して、hrtfs などの spatialization を提供しています。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-155">Windows offers spatialization, including HRTFs, via the [ISpatialAudioClient API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound).</span></span> <span data-ttu-id="ed2cd-156">この API は、HoloLens 2 HRTF ハードウェアアクセラレーションをアプリケーションに公開します。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-156">This API exposes the HoloLens 2 HRTF hardware acceleration to applications.</span></span>

### <a name="spatializer-middleware-support"></a><span data-ttu-id="ed2cd-157">Spatializer ミドルウェアのサポート</span><span class="sxs-lookup"><span data-stu-id="ed2cd-157">Spatializer middleware support</span></span>

<span data-ttu-id="ed2cd-158">Windows の HRTFs のサポートは、次のサードパーティのオーディオエンジンで利用できます。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-158">Support for Windows' HRTFs is available for the following third-party audio engines.</span></span>
* <span data-ttu-id="ed2cd-159">[Unity オーディオエンジンプラグイン](../develop/unity/spatial-sound-in-unity.md)</span><span class="sxs-lookup"><span data-stu-id="ed2cd-159">A [Unity audio engine plugin](../develop/unity/spatial-sound-in-unity.md)</span></span>
* <span data-ttu-id="ed2cd-160">[Wwise なオーディオエンジンプラグイン](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span><span class="sxs-lookup"><span data-stu-id="ed2cd-160">A [Wwise audio engine plugin](https://www.audiokinetic.com/products/plug-ins/msspatial/)</span></span>

## <a name="acoustics"></a><span data-ttu-id="ed2cd-161">音響</span><span class="sxs-lookup"><span data-stu-id="ed2cd-161">Acoustics</span></span>

<span data-ttu-id="ed2cd-162">空間オーディオは、方向よりも大きくなります。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-162">Spatial audio is about more than direction.</span></span> <span data-ttu-id="ed2cd-163">その他のディメンションには、遮蔽、障害、リバーブ、portaling、ソースモデリングなどがあります。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-163">Other dimensions include occlusion, obstruction, reverb, portaling, and source modeling.</span></span> <span data-ttu-id="ed2cd-164">これらのディメンションをまとめて、 *acoustics* と呼びます。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-164">Collectively these dimensions are referred to as *acoustics*.</span></span> <span data-ttu-id="ed2cd-165">Acoustics を使用しない場合、spatialized は認識できない距離になります。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-165">Without acoustics, spatialized sounds lack perceived distance.</span></span>

<span data-ttu-id="ed2cd-166">Acoustics は単純なものから複雑なものまでの範囲です。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-166">Acoustics treatments range from simple to complex.</span></span> <span data-ttu-id="ed2cd-167">任意のオーディオエンジンでサポートされているリバーブを使用して、spatialized サウンドをリスナーの環境にプッシュできます。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-167">You can use a reverb that's supported by any audio engine to push spatialized sounds into the environment of the listener.</span></span> <span data-ttu-id="ed2cd-168">[Project Acoustics](https://aka.ms/acoustics)などの Acoustics システムでは、より豊富で説得力の高い Acoustics 処理が提供されています。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-168">Acoustics systems such as [Project Acoustics](https://aka.ms/acoustics)  provide richer and more compelling acoustics treatment.</span></span> <span data-ttu-id="ed2cd-169">プロジェクト Acoustics は、壁、ドア、およびその他のシーンジオメトリの効果をサウンドでモデル化できます。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-169">Project Acoustics can model the effect of walls, doors, and other scene geometry on a sound.</span></span> <span data-ttu-id="ed2cd-170">これは、開発時に関連するシーンジオメトリが既知の場合に有効なオプションです。</span><span class="sxs-lookup"><span data-stu-id="ed2cd-170">It's an effective option for cases where the relevant scene geometry is known at development time.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ed2cd-171">次のステップ</span><span class="sxs-lookup"><span data-stu-id="ed2cd-171">Next steps</span></span>

- [<span data-ttu-id="ed2cd-172">Unity の立体音響</span><span class="sxs-lookup"><span data-stu-id="ed2cd-172">Spatial sound in Unity</span></span>](../develop/unity/spatial-sound-in-unity.md)
- [<span data-ttu-id="ed2cd-173">Mixed reality アプリケーションでサウンドを使用する方法</span><span class="sxs-lookup"><span data-stu-id="ed2cd-173">How to use sound in mixed-reality applications</span></span>](spatial-sound-design.md)
