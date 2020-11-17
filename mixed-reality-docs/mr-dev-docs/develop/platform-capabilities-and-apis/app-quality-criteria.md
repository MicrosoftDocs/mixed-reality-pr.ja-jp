---
title: アプリの品質基準
description: このドキュメントでは、mixed reality アプリの品質に影響する上位の要因について説明します。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: アプリ品質基準、mixed reality、mixed reality アプリ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: c18f4e8470f7f183fdf250472fd3a977f925dfbf
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94677991"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="c5dac-104">アプリの品質基準</span><span class="sxs-lookup"><span data-stu-id="c5dac-104">App quality criteria</span></span>

<span data-ttu-id="c5dac-105">このドキュメントでは、mixed reality アプリの品質に影響する上位の要因について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="c5dac-106">各要素について、次の情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-106">For each factor the following information is provided</span></span>
* <span data-ttu-id="c5dac-107">[概要] –品質要因とそれが重要な理由について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-107">Overview – a brief description of the quality factor and why it is important.</span></span>
* <span data-ttu-id="c5dac-108">デバイスの影響: Mixed Reality デバイスに影響を与えるウィンドウの種類。</span><span class="sxs-lookup"><span data-stu-id="c5dac-108">Device impact - which type of Window Mixed Reality device is impacted.</span></span>
* <span data-ttu-id="c5dac-109">品質基準–品質要因を評価する方法。</span><span class="sxs-lookup"><span data-stu-id="c5dac-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="c5dac-110">方法: 問題を測定 (または経験) する方法。</span><span class="sxs-lookup"><span data-stu-id="c5dac-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="c5dac-111">推奨事項–より優れたユーザーエクスペリエンスを提供するためのアプローチの概要です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="c5dac-112">リソース–優れたアプリエクスペリエンスを作成するのに役立つ、関連する開発者および設計リソース。</span><span class="sxs-lookup"><span data-stu-id="c5dac-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="c5dac-113">フレーム レート</span><span class="sxs-lookup"><span data-stu-id="c5dac-113">Frame rate</span></span>

<span data-ttu-id="c5dac-114">フレームレートは、ホログラムの安定性とユーザーの快適さの第一柱です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="c5dac-115">推奨されるターゲットの下にあるフレームレートは、ホログラムがちらつくように見え、エクスペリエンスの believability に悪影響を及ぼし、目に見える疲労が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="c5dac-116">Windows Mixed Reality イマーシブヘッドセットのエクスペリエンスの目標フレームレートは、サポートする Windows Mixed Reality 互換 Pc に応じて、60Hz または90Hz になります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets will be either 60Hz or 90Hz depending on which Windows Mixed Reality Compatible PCs you wish to support.</span></span> <span data-ttu-id="c5dac-117">HoloLens の場合、ターゲットフレームレートは60Hz です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-117">For HoloLens the target frame rate is 60Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5dac-118">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="c5dac-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5dac-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5dac-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5dac-121">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-121">✔️</span></span></td>
        <td><span data-ttu-id="c5dac-122">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5dac-123">品質基準</span><span class="sxs-lookup"><span data-stu-id="c5dac-123">Quality criteria</span></span>

|  <span data-ttu-id="c5dac-124">最高</span><span class="sxs-lookup"><span data-stu-id="c5dac-124">Best</span></span>  |  <span data-ttu-id="c5dac-125">あっ</span><span class="sxs-lookup"><span data-stu-id="c5dac-125">Meets</span></span> |  <span data-ttu-id="c5dac-126">失敗</span><span class="sxs-lookup"><span data-stu-id="c5dac-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="c5dac-127">アプリは、ターゲットデバイスの1秒あたりのフレーム数 (FPS) の目標を一貫して満たしています: HoloLens の60fpsウルトラ Pc 上の90fpsメインストリーム Pc では60fps。</span><span class="sxs-lookup"><span data-stu-id="c5dac-127">The app consistently meets frames per second (FPS) goal for target device: 60fps on HoloLens; 90fps on Ultra PCs; and 60fps on mainstream PCs.</span></span> | <span data-ttu-id="c5dac-128">アプリは、コアエクスペリエンスを妨げるすることなく、断続的にフレームを削除します。または FPS は、必要な目標よりも一貫して低くなりますが、アプリのエクスペリエンスを妨げることはありません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-128">The app has intermittent frame drops not impeding the core experience; or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="c5dac-129">アプリでは、平均で10秒以内にフレームレートのドロップが発生しています。</span><span class="sxs-lookup"><span data-stu-id="c5dac-129">The app is experiencing a drop in frame rate on average every ten seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="c5dac-130">測定する方法</span><span class="sxs-lookup"><span data-stu-id="c5dac-130">How to measure</span></span>

* <span data-ttu-id="c5dac-131">リアルタイムのフレームレートグラフは、 [Windows デバイスポータル](using-the-windows-device-portal.md#system-performance) によって "システムパフォーマンス" によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="c5dac-132">開発用デバッグでは、フレームレート診断カウンターをアプリに追加します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="c5dac-133">「サンプルカウンターのリソース」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5dac-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="c5dac-134">フレームレートが低下するのは、アプリの実行中に、ヘッドを左右に移動して、デバイスで発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="c5dac-135">ホログラムが予期しないちらつきの動きを示している場合、フレームレートが低いか、安定性平面が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5dac-136">Recommendations</span><span class="sxs-lookup"><span data-stu-id="c5dac-136">Recommendations</span></span>

* <span data-ttu-id="c5dac-137">開発作業の開始時にフレームレートカウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="c5dac-138">フレームレートが低下した変更は、パフォーマンスバグとして評価され、適切に解決される必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="c5dac-139">リソース</span><span class="sxs-lookup"><span data-stu-id="c5dac-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5dac-140">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="c5dac-140">Documentation</span></span>

* [<span data-ttu-id="c5dac-141">Mixed Reality のパフォーマンスについて</span><span class="sxs-lookup"><span data-stu-id="c5dac-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="c5dac-142">ホログラムの安定性とフレームレート</span><span class="sxs-lookup"><span data-stu-id="c5dac-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="c5dac-143">資産のパフォーマンスの予算</span><span class="sxs-lookup"><span data-stu-id="c5dac-143">Asset performance budget</span></span>](../../design/asset-creation-process.md)
* [<span data-ttu-id="c5dac-144">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="c5dac-144">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5dac-145">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="c5dac-145">Tools and tutorials</span></span>

* [<span data-ttu-id="c5dac-146">MRToolkit、FPS カウンターの表示</span><span class="sxs-lookup"><span data-stu-id="c5dac-146">MRToolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="c5dac-147">MRToolkit、シェーダー</span><span class="sxs-lookup"><span data-stu-id="c5dac-147">MRToolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="c5dac-148">外部参照</span><span class="sxs-lookup"><span data-stu-id="c5dac-148">External references</span></span>

* [<span data-ttu-id="c5dac-149">Unity, モバイルアプリケーションの最適化</span><span class="sxs-lookup"><span data-stu-id="c5dac-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="c5dac-150">ホログラムの安定性</span><span class="sxs-lookup"><span data-stu-id="c5dac-150">Hologram stability</span></span>

<span data-ttu-id="c5dac-151">安定したホログラムは、アプリの使いやすさと believability を向上させ、ユーザーにより快適な表示エクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="c5dac-152">ホログラムの安定性の質は、優れたアプリ開発と、その環境を理解 (追跡) するデバイスの機能によって得られます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="c5dac-153">フレームレートは安定性の最初の柱ですが、その他の要因は次のような安定性に影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="c5dac-154">安定化平面の使用</span><span class="sxs-lookup"><span data-stu-id="c5dac-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="c5dac-155">空間アンカーへの距離</span><span class="sxs-lookup"><span data-stu-id="c5dac-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="c5dac-156">追跡</span><span class="sxs-lookup"><span data-stu-id="c5dac-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5dac-157">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="c5dac-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5dac-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5dac-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5dac-160">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5dac-161">品質基準</span><span class="sxs-lookup"><span data-stu-id="c5dac-161">Quality criteria</span></span>

|  <span data-ttu-id="c5dac-162">最高</span><span class="sxs-lookup"><span data-stu-id="c5dac-162">Best</span></span>  |  <span data-ttu-id="c5dac-163">あっ</span><span class="sxs-lookup"><span data-stu-id="c5dac-163">Meets</span></span> |  <span data-ttu-id="c5dac-164">失敗</span><span class="sxs-lookup"><span data-stu-id="c5dac-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5dac-165">ホログラムは常に安定した状態で表示されます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="c5dac-166">セカンダリコンテンツは予期しない移動を示すまたは、予期しない移動はアプリ全体のエクスペリエンスを妨げることはありません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-166">Secondary content exhibits unexpected movement; or unexpected movement does not impede overall app experience.</span></span> | <span data-ttu-id="c5dac-167">フレーム内のプライマリコンテンツは、予期しない移動を示すことがあります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-167">Primary content in frame exhibits unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="c5dac-168">測定する方法</span><span class="sxs-lookup"><span data-stu-id="c5dac-168">How to measure</span></span>

<span data-ttu-id="c5dac-169">デバイスを装着し、エクスペリエンスを表示しています。</span><span class="sxs-lookup"><span data-stu-id="c5dac-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="c5dac-170">ヘッドを左右に移動します。ホログラムが予期しない動きを示している場合は、フレームレートが低いか、または安定性平面が焦点平面に正しく配置されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-170">Move your head from side to side, if the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="c5dac-171">ホログラムと環境内を移動し、スイム・ jumpiness などの動作を探します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-171">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="c5dac-172">この種類のモーションは、デバイスが環境を追跡していない、または空間アンカーへの距離が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-172">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="c5dac-173">フレーム内に複数のホログラムがある場合は、さまざまな深度でのホログラムの動作を観察し、揺れるが表示されている場合は、安定化平面によって発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-173">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5dac-174">Recommendations</span><span class="sxs-lookup"><span data-stu-id="c5dac-174">Recommendations</span></span>

* <span data-ttu-id="c5dac-175">開発作業の開始時にフレームレートカウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-175">Add an frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="c5dac-176">安定化平面を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-176">Use the stabilization plane.</span></span>
* <span data-ttu-id="c5dac-177">アンカーの3メートル以内に固定したホログラムを常にレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="c5dac-177">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="c5dac-178">環境が適切に追跡できるようにセットアップされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-178">Make sure your environment is setup for proper tracking.</span></span>
* <span data-ttu-id="c5dac-179">フレーム内のさまざまな焦点深度レベルでホログラムを使用しないように、エクスペリエンスを設計します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-179">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="c5dac-180">リソース</span><span class="sxs-lookup"><span data-stu-id="c5dac-180">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5dac-181">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="c5dac-181">Documentation</span></span>

* [<span data-ttu-id="c5dac-182">ホログラムの安定性とフレームレート</span><span class="sxs-lookup"><span data-stu-id="c5dac-182">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="c5dac-183">安定化平面を使用したケーススタディ</span><span class="sxs-lookup"><span data-stu-id="c5dac-183">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="c5dac-184">Mixed Reality のパフォーマンスについて</span><span class="sxs-lookup"><span data-stu-id="c5dac-184">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="c5dac-185">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="c5dac-185">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="c5dac-186">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="c5dac-186">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="c5dac-187">追跡エラーの処理</span><span class="sxs-lookup"><span data-stu-id="c5dac-187">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="c5dac-188">静止フレーム (参照)</span><span class="sxs-lookup"><span data-stu-id="c5dac-188">Stationary frame of reference</span></span>](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5dac-189">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="c5dac-189">Tools and tutorials</span></span>

* [<span data-ttu-id="c5dac-190">MR コンパニオンキット、Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="c5dac-190">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="c5dac-191">実際のサーフェイス上のホログラムの位置</span><span class="sxs-lookup"><span data-stu-id="c5dac-191">Holograms position on real surfaces</span></span>

<span data-ttu-id="c5dac-192">物理的なオブジェクトを使用したホログラムの間違った配置 (相互に関係するように設計されている場合) は、ホログラムと現実世界の非共用体を明確に示しています。</span><span class="sxs-lookup"><span data-stu-id="c5dac-192">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) is a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="c5dac-193">配置の精度は、シナリオのニーズに対して相対的である必要があります。たとえば、一般的な表面配置では空間マップを使用できますが、正確に配置するには、マーカーと調整を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-193">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5dac-194">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="c5dac-194">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5dac-195"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-195"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5dac-196"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-196"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5dac-197">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-197">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5dac-198">品質基準</span><span class="sxs-lookup"><span data-stu-id="c5dac-198">Quality criteria</span></span>

|  <span data-ttu-id="c5dac-199">最高</span><span class="sxs-lookup"><span data-stu-id="c5dac-199">Best</span></span>  |  <span data-ttu-id="c5dac-200">あっ</span><span class="sxs-lookup"><span data-stu-id="c5dac-200">Meets</span></span> |  <span data-ttu-id="c5dac-201">失敗</span><span class="sxs-lookup"><span data-stu-id="c5dac-201">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="c5dac-202">ホログラムは、通常、センチメートル ~ インチの範囲内のサーフェイスに配置されます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-202">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="c5dac-203">より正確な要件が必要な場合は、アプリが目的のアプリ仕様内でコラボレーションのための効率的な手段を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-203">If more accuracy is required, the app should provide an efficient means for collaboration within the desired app spec.</span></span> | <span data-ttu-id="c5dac-204">N/A</span><span class="sxs-lookup"><span data-stu-id="c5dac-204">NA</span></span> | <span data-ttu-id="c5dac-205">サーフェイスを分割するか、表面から離れた場所に表示することによって、ホログラムが物理的なターゲットオブジェクトと共に配置されていないことを認識します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-205">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="c5dac-206">精度が必要な場合は、ホログラムがシナリオの近接仕様を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-206">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="c5dac-207">測定する方法</span><span class="sxs-lookup"><span data-stu-id="c5dac-207">How to measure</span></span>

* <span data-ttu-id="c5dac-208">空間マップに配置されているホログラムは、サーフェイスの上または下に劇的に浮動小数点型で表示されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-208">Holograms that are placed on spatial map should not appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="c5dac-209">正確な配置を必要とするホログラムには、シナリオの要件に対して正確な何らかの形式のマーカーと調整システムが必要です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-209">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5dac-210">Recommendations</span><span class="sxs-lookup"><span data-stu-id="c5dac-210">Recommendations</span></span>

* <span data-ttu-id="c5dac-211">空間マップは、精度が不要な場合にオブジェクトをサーフェイスに配置する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-211">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="c5dac-212">最適な精度を得るには、マーカーまたはポスターを使用して、ホログラムと Xbox コントローラー (または手動配置機構) を最終的な調整用に設定します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-212">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="c5dac-213">特大の大きなホログラムを論理部分に分割し、各部分をサーフェイスに配置することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="c5dac-213">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="c5dac-214">不適切に設定した interpupillary distance (IPD) は、ホログラムのアラインメントにも影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-214">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="c5dac-215">常に HoloLens をユーザーの IPD に構成します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-215">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="c5dac-216">リソース</span><span class="sxs-lookup"><span data-stu-id="c5dac-216">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5dac-217">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="c5dac-217">Documentation</span></span>

* [<span data-ttu-id="c5dac-218">空間マッピングの配置</span><span class="sxs-lookup"><span data-stu-id="c5dac-218">Spatial mapping placement</span></span>](../../design/spatial-mapping.md#placement)
* [<span data-ttu-id="c5dac-219">ルームスキャンプロセス</span><span class="sxs-lookup"><span data-stu-id="c5dac-219">Room scanning process</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="c5dac-220">空間アンカーのベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="c5dac-220">Spatial anchors best practices</span></span>](../../design/spatial-anchors.md#best-practices)
* [<span data-ttu-id="c5dac-221">追跡エラーの処理</span><span class="sxs-lookup"><span data-stu-id="c5dac-221">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="c5dac-222">Unity の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="c5dac-222">Spatial mapping in Unity</span></span>](../unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="c5dac-223">Vuforia 開発の概要</span><span class="sxs-lookup"><span data-stu-id="c5dac-223">Vuforia development overview</span></span>](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5dac-224">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="c5dac-224">Tools and tutorials</span></span>

* [<span data-ttu-id="c5dac-225">MR ツールキット, 空間マッピングライブラリ</span><span class="sxs-lookup"><span data-stu-id="c5dac-225">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="c5dac-226">MR コンパニオンキット、ポスター調整のサンプル</span><span class="sxs-lookup"><span data-stu-id="c5dac-226">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="c5dac-227">MR コンパニオンキット、Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="c5dac-227">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="c5dac-228">外部参照</span><span class="sxs-lookup"><span data-stu-id="c5dac-228">External references</span></span>

* [<span data-ttu-id="c5dac-229">Lowes のケーススタディ、有効桁数のアラインメント</span><span class="sxs-lookup"><span data-stu-id="c5dac-229">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="c5dac-230">快適なゾーンの表示</span><span class="sxs-lookup"><span data-stu-id="c5dac-230">Viewing zone of comfort</span></span>

<span data-ttu-id="c5dac-231">アプリ開発者は、さまざまな深度でコンテンツとホログラムを配置することで、ユーザーの目がどのようになるかを制御します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-231">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="c5dac-232">Hololens のディスプレイは、ユーザーから約2.0 分離れた光学距離で固定されているため、HoloLens を装着したユーザーは常に 2.0 m に対応して明確なイメージを維持します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-232">Users wearing HoloLens will always accommodate to 2.0m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0m away from the user.</span></span> <span data-ttu-id="c5dac-233">不適切なコンテンツの深さは、視覚不快感や疲労につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-233">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5dac-234">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="c5dac-234">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5dac-235"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-235"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5dac-236"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-236"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5dac-237">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-237">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5dac-238">品質基準</span><span class="sxs-lookup"><span data-stu-id="c5dac-238">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="c5dac-239">最高</span><span class="sxs-lookup"><span data-stu-id="c5dac-239">Best</span></span> </td><td><ul>
<li><span data-ttu-id="c5dac-240">コンテンツを2m に配置します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-240">Place content at 2m.</span></span></li><li><span data-ttu-id="c5dac-241">ホログラムを2m に配置できず、収束と設備の間の競合を回避できない場合、ホログラムの配置に最適なゾーンは 1.25 m と5分の間になります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-241">When holograms cannot be placed at 2m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25m and 5m.</span></span></li><li><span data-ttu-id="c5dac-242">どのような場合でも、デザイナーは、ユーザーが 1 + m を操作できるようにコンテンツを構成する必要があります (たとえば、コンテンツサイズと既定の配置パラメーターを調整します)。</span><span class="sxs-lookup"><span data-stu-id="c5dac-242">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="c5dac-243">シナリオで特に要求されていない限り、クリッププレーンは1m から始まる fadeout で実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-243">Unless specifically not required by the scenario, a clipping plane should be implement with fadeout starting at 1m.</span></span></li><li><span data-ttu-id="c5dac-244">Motionless ホログラムの詳細な監視が必要な場合は、コンテンツを50cm より近くにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-244">In cases where closer observation of a motionless hologram is required, the content should not be closer than 50cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="c5dac-245">あっ</span><span class="sxs-lookup"><span data-stu-id="c5dac-245">Meets</span></span></td><td> <span data-ttu-id="c5dac-246">コンテンツは、表示およびモーションのガイダンスに含まれていますが、不適切な使用またはクリッピング平面の使用はありません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-246">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c5dac-247">失敗</span><span class="sxs-lookup"><span data-stu-id="c5dac-247">Fail</span></span> </td><td> <span data-ttu-id="c5dac-248">コンテンツが非常に近い場所に表示されます (通常は &lt; 1.25 m、またはより &lt; 詳細な監視が必要な固定のホログラムの場合は 50cm)。</span><span class="sxs-lookup"><span data-stu-id="c5dac-248">Content is presented too close (typically &lt;1.25m, or &lt;50cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="c5dac-249">測定する方法</span><span class="sxs-lookup"><span data-stu-id="c5dac-249">How to measure</span></span>

* <span data-ttu-id="c5dac-250">通常、コンテンツは2m である必要がありますが、1.25 以上、5分を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-250">Content should typically be 2m away, but no closer than 1.25 or further than 5m.</span></span>
* <span data-ttu-id="c5dac-251">例外がいくつかある場合は、1 m から開始したコンテンツの fadeout を使用して、HoloLens クリッピングのレンダリング距離を85CM に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-251">With few exceptions, the HoloLens clipping render distance should be set to .85CM with fadeout of content starting at 1m.</span></span> <span data-ttu-id="c5dac-252">コンテンツにアプローチし、クリッピング平面効果を確認します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-252">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="c5dac-253">静止コンテンツは、50cm を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-253">Stationary content should not be closer than 50cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5dac-254">Recommendations</span><span class="sxs-lookup"><span data-stu-id="c5dac-254">Recommendations</span></span>

* <span data-ttu-id="c5dac-255">最適な表示距離が2m のコンテンツをデザインします。</span><span class="sxs-lookup"><span data-stu-id="c5dac-255">Design content for the optimal viewing distance of 2m.</span></span>
* <span data-ttu-id="c5dac-256">1m からのコンテンツの fadeout を使用して、クリッピングレンダリング距離を85cm に設定します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-256">Set the clipping render distance to 85cm with fadeout of content starting at 1m.</span></span>
* <span data-ttu-id="c5dac-257">近くに表示する必要がある固定のホログラムの場合、クリッピングプレーンは30cm 以下で、fadeout はクリッピング平面から少なくとも10cm 離れた位置にある必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-257">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30cm and fadeout should start at least 10cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="c5dac-258">リソース</span><span class="sxs-lookup"><span data-stu-id="c5dac-258">Resources</span></span>

* [<span data-ttu-id="c5dac-259">レンダリング距離</span><span class="sxs-lookup"><span data-stu-id="c5dac-259">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="c5dac-260">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="c5dac-260">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="c5dac-261">スケールを試してみる</span><span class="sxs-lookup"><span data-stu-id="c5dac-261">Experimenting with scale</span></span>](../../design/scale.md#experimenting-with-scale)
* [<span data-ttu-id="c5dac-262">テキスト、推奨されるフォントサイズ</span><span class="sxs-lookup"><span data-stu-id="c5dac-262">Text, Recommended font size</span></span>](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="c5dac-263">深度の切り替え</span><span class="sxs-lookup"><span data-stu-id="c5dac-263">Depth switching</span></span>

<span data-ttu-id="c5dac-264">快適な問題のゾーンが表示されているかどうかに関係なく、ユーザーに対して頻繁にまたは迅速に (ホログラムや実際のコンテンツを含む) 近接するオブジェクトを切り替えることによって、oculomotor と general 不快感が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-264">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5dac-265">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="c5dac-265">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5dac-266"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-266"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5dac-267"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-267"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5dac-268">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-268">✔️</span></span></td>
        <td><span data-ttu-id="c5dac-269">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-269">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5dac-270">品質基準</span><span class="sxs-lookup"><span data-stu-id="c5dac-270">Quality criteria</span></span>

|  <span data-ttu-id="c5dac-271">最高</span><span class="sxs-lookup"><span data-stu-id="c5dac-271">Best</span></span>  |  <span data-ttu-id="c5dac-272">あっ</span><span class="sxs-lookup"><span data-stu-id="c5dac-272">Meets</span></span> |  <span data-ttu-id="c5dac-273">失敗</span><span class="sxs-lookup"><span data-stu-id="c5dac-273">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5dac-274">ユーザーが自然に refocus しないようにする、限定的または自然な深さの切り替え。</span><span class="sxs-lookup"><span data-stu-id="c5dac-274">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="c5dac-275">[突然の深さ] スイッチこれはコアであり、アプリケーションエクスペリエンスに設計されています。または、予期しない実際のコンテンツによって発生した、突然の深さスイッチです。</span><span class="sxs-lookup"><span data-stu-id="c5dac-275">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="c5dac-276">一貫した深さスイッチ、またはアプリエクスペリエンスの中核とならない、急激な深さの切り替え。</span><span class="sxs-lookup"><span data-stu-id="c5dac-276">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="c5dac-277">測定する方法</span><span class="sxs-lookup"><span data-stu-id="c5dac-277">How to measure</span></span>

* <span data-ttu-id="c5dac-278">アプリケーションで、深さのフォーカスを一貫して変更する必要がある場合は、深さの切り替えに問題があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-278">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5dac-279">Recommendations</span><span class="sxs-lookup"><span data-stu-id="c5dac-279">Recommendations</span></span>

* <span data-ttu-id="c5dac-280">一貫した中心面でプライマリコンテンツを保持し、安定化平面が焦点平面と一致していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-280">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="c5dac-281">これにより、oculomotor の疲労と予期しないホログラムの動きが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-281">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="c5dac-282">リソース</span><span class="sxs-lookup"><span data-stu-id="c5dac-282">Resources</span></span>

* [<span data-ttu-id="c5dac-283">レンダリング距離</span><span class="sxs-lookup"><span data-stu-id="c5dac-283">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="c5dac-284">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="c5dac-284">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="c5dac-285">空間サウンドの使用</span><span class="sxs-lookup"><span data-stu-id="c5dac-285">Use of spatial sound</span></span>

<span data-ttu-id="c5dac-286">Windows Mixed Reality では、音声エンジンは、方向、距離、および環境シミュレーションを使用して3D サウンドをシミュレートすることによって、混合した現実のエクスペリエンスの aural コンポーネントを提供します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-286">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="c5dac-287">アプリケーションで空間サウンドを使用すると、開発者はユーザーに対して3次元空間 (球) でサウンドを convincingly ことができます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-287">Using spatial sound in an application allows developers to convincingly place sounds in a 3 dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="c5dac-288">これらのサウンドは、実際の物理オブジェクトまたはユーザーの周囲の混合現実ホログラムからのものであるように見えます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-288">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="c5dac-289">空間サウンドは、mixed reality アプリケーションでの immersion、アクセシビリティ、UX の設計を行うための強力なツールです。</span><span class="sxs-lookup"><span data-stu-id="c5dac-289">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5dac-290">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="c5dac-290">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5dac-291"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-291"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5dac-292"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-292"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5dac-293">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-293">✔️</span></span></td>
        <td><span data-ttu-id="c5dac-294">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-294">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5dac-295">品質基準</span><span class="sxs-lookup"><span data-stu-id="c5dac-295">Quality criteria</span></span>

|  <span data-ttu-id="c5dac-296">最高</span><span class="sxs-lookup"><span data-stu-id="c5dac-296">Best</span></span>  |  <span data-ttu-id="c5dac-297">あっ</span><span class="sxs-lookup"><span data-stu-id="c5dac-297">Meets</span></span> |  <span data-ttu-id="c5dac-298">失敗</span><span class="sxs-lookup"><span data-stu-id="c5dac-298">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5dac-299">サウンドは論理的には spatialized であり、UX は適切にサウンドを使用して、オブジェクトの検出とユーザーフィードバックを支援します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-299">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="c5dac-300">サウンドは、自然で、オブジェクトに関連し、シナリオ全体で正規化されます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-300">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="c5dac-301">空間オーディオは believability に対して適切に使用されますが、ユーザーのフィードバックと検索可能性を高めるための手段としては欠けています。</span><span class="sxs-lookup"><span data-stu-id="c5dac-301">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="c5dac-302">サウンドが予期したとおりに spatialized されていないか、UX 内でユーザーを支援する音がありません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-302">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="c5dac-303">または、空間オーディオがシナリオの設計で検討されていないか、使用されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="c5dac-303">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="c5dac-304">測定する方法</span><span class="sxs-lookup"><span data-stu-id="c5dac-304">How to measure</span></span>

* <span data-ttu-id="c5dac-305">一般に、関連するサウンドは、ターゲットホログラムから出力する必要があります (たとえば、holographic dog からほえサウンドが生成されます)。</span><span class="sxs-lookup"><span data-stu-id="c5dac-305">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="c5dac-306">サウンドキューは、ユーザーが holographic フレーム外のアクションをフィードバックまたは認識するのを支援するために、UX 全体で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-306">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5dac-307">Recommendations</span><span class="sxs-lookup"><span data-stu-id="c5dac-307">Recommendations</span></span>

* <span data-ttu-id="c5dac-308">オブジェクト検出とユーザーインターフェイスをサポートするには、空間オーディオを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-308">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="c5dac-309">実際のサウンドは、合成や不自然な音よりも優れています。</span><span class="sxs-lookup"><span data-stu-id="c5dac-309">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="c5dac-310">ほとんどのサウンドは spatialized にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-310">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="c5dac-311">非表示の発信器は避けてください。</span><span class="sxs-lookup"><span data-stu-id="c5dac-311">Avoid invisible emitters.</span></span>
* <span data-ttu-id="c5dac-312">空間マスクは避けてください。</span><span class="sxs-lookup"><span data-stu-id="c5dac-312">Avoid spatial masking.</span></span>
* <span data-ttu-id="c5dac-313">すべてのサウンドを正規化します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-313">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="c5dac-314">リソース</span><span class="sxs-lookup"><span data-stu-id="c5dac-314">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5dac-315">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="c5dac-315">Documentation</span></span>

* [<span data-ttu-id="c5dac-316">立体音響</span><span class="sxs-lookup"><span data-stu-id="c5dac-316">Spatial sound</span></span>](../../design/spatial-sound.md)
* [<span data-ttu-id="c5dac-317">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="c5dac-317">Spatial sound design</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="c5dac-318">Unity の立体音響</span><span class="sxs-lookup"><span data-stu-id="c5dac-318">Spatial sound in Unity</span></span>](../unity/spatial-sound-in-unity.md)
* [<span data-ttu-id="c5dac-319">ケーススタディ、HoloTour の空間サウンド</span><span class="sxs-lookup"><span data-stu-id="c5dac-319">Case study, Spatial sound for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="c5dac-320">RoboRaid の空間サウンドを使用したケーススタディ</span><span class="sxs-lookup"><span data-stu-id="c5dac-320">Case study, Using spatial sound in RoboRaid</span></span>](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5dac-321">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="c5dac-321">Tools and tutorials</span></span>

* [<span data-ttu-id="c5dac-322">MRToolkit、空間オーディオ</span><span class="sxs-lookup"><span data-stu-id="c5dac-322">MRToolkit, Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="c5dac-323">Holographic frame (視界) の境界にフォーカス</span><span class="sxs-lookup"><span data-stu-id="c5dac-323">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="c5dac-324">適切に設計されたユーザーエクスペリエンスでは、ユーザーを中心とした仮想環境の有用なコンテキストを作成し、維持することができます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-324">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="c5dac-325">視界の境界の影響を軽減するには、コンテンツのスケールとコンテキスト、空間オーディオの使用、ガイダンスシステム、ユーザーの位置をよく設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-325">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="c5dac-326">そうすれば、ユーザーは快適なアプリエクスペリエンスを実現しながら、視界の境界によって損なわれることはなくなります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-326">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5dac-327">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="c5dac-327">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5dac-328"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-328"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5dac-329"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-329"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5dac-330">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-330">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5dac-331">品質基準</span><span class="sxs-lookup"><span data-stu-id="c5dac-331">Quality criteria</span></span>

|  <span data-ttu-id="c5dac-332">最高</span><span class="sxs-lookup"><span data-stu-id="c5dac-332">Best</span></span>  |  <span data-ttu-id="c5dac-333">あっ</span><span class="sxs-lookup"><span data-stu-id="c5dac-333">Meets</span></span> |  <span data-ttu-id="c5dac-334">失敗</span><span class="sxs-lookup"><span data-stu-id="c5dac-334">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5dac-335">ユーザーはコンテキストを失うことはなく、表示も快適です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-335">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="c5dac-336">ラージオブジェクトのコンテキストに関するサポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-336">Context assistance is provided for large objects.</span></span> <span data-ttu-id="c5dac-337">フレームの外部にあるオブジェクトについて、見つけやすさと表示に関するガイダンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-337">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="c5dac-338">一般に、見やすさを向上させるには、ホログラムのモーションデザインとスケールが適しています。</span><span class="sxs-lookup"><span data-stu-id="c5dac-338">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="c5dac-339">ユーザーはコンテキストを失うことはありませんが、限られた状況では追加のネックモーションが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-339">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="c5dac-340">限られた状況では、ホログラムによって、ネックの動きが見られる垂直方向または水平方向のフレームが壊れることがあります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-340">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="c5dac-341">ホログラムを表示するには、コンテキストや一貫したネック運動が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-341">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="c5dac-342">大規模な holographic オブジェクトに関するコンテキストガイダンスはありません。オブジェクトを移動しても、発見可能なガイダンスがなくても、オブジェクトを簡単に失うことがあります。また、広いホログラムでは、通常のネックモーションが必要になります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-342">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="c5dac-343">測定する方法</span><span class="sxs-lookup"><span data-stu-id="c5dac-343">How to measure</span></span>

* <span data-ttu-id="c5dac-344">境界でクリップされているため、(大きい) ホログラムのコンテキストが失われているか、認識されていません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-344">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="c5dac-345">ホログラムの場所は、holographic フレームとの間で急速に移動される、要注意のダイレクタやコンテンツがないため、見つけるのが困難です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-345">Location of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="c5dac-346">シナリオでは、ネックの疲労を完全に確認するために、定期的かつ反復的に反復的に動きが必要です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-346">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5dac-347">Recommendations</span><span class="sxs-lookup"><span data-stu-id="c5dac-347">Recommendations</span></span>

* <span data-ttu-id="c5dac-348">視界に合った小さなオブジェクトを使用して操作を開始し、視覚的な手掛かりを使用して大きなバージョンに移行します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-348">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="c5dac-349">空間オーディオとアテンションダイレクタを使用すると、ユーザーが視界の外にあるコンテンツを見つけやすくなります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-349">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="c5dac-350">可能な限り、視界を垂直方向にクリップするホログラムは避けてください。</span><span class="sxs-lookup"><span data-stu-id="c5dac-350">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="c5dac-351">ユーザーにアプリ内のガイダンスを提供して、最適な表示場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-351">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="c5dac-352">リソース</span><span class="sxs-lookup"><span data-stu-id="c5dac-352">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5dac-353">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="c5dac-353">Documentation</span></span>

* [<span data-ttu-id="c5dac-354">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="c5dac-354">Holographic frame</span></span>](../../design/holographic-frame.md)
* [<span data-ttu-id="c5dac-355">ケーススタディ、HoloStudio UI、相互作用設計学習</span><span class="sxs-lookup"><span data-stu-id="c5dac-355">Case Study, HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="c5dac-356">オブジェクトと環境のスケール</span><span class="sxs-lookup"><span data-stu-id="c5dac-356">Scale of objects and environments</span></span>](../../design/scale.md)
* [<span data-ttu-id="c5dac-357">カーソル、ビジュアルキュー</span><span class="sxs-lookup"><span data-stu-id="c5dac-357">Cursors, Visual cues</span></span>](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="c5dac-358">外部参照</span><span class="sxs-lookup"><span data-stu-id="c5dac-358">External references</span></span>

* [<span data-ttu-id="c5dac-359">視界に関する多くの ado</span><span class="sxs-lookup"><span data-stu-id="c5dac-359">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="c5dac-360">ユーザーの位置に反応するコンテンツ</span><span class="sxs-lookup"><span data-stu-id="c5dac-360">Content reacts to user position</span></span>

<span data-ttu-id="c5dac-361">ホログラムは、"real" オブジェクトとほぼ同じ方法で、ユーザーの位置に反応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-361">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="c5dac-362">注目すべき設計上の考慮事項は、ユーザーの位置が固定されていて、ユーザーの動きに合わせて調整できるとは限らない UI 要素です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-362">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="c5dac-363">ユーザーの位置に適切に適合するようにアプリを設計すると、believable エクスペリエンスが向上し、使いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-363">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5dac-364">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="c5dac-364">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5dac-365"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-365"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5dac-366"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-366"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5dac-367">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-367">✔️</span></span></td>
        <td><span data-ttu-id="c5dac-368">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-368">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5dac-369">品質基準</span><span class="sxs-lookup"><span data-stu-id="c5dac-369">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="c5dac-370">最高</span><span class="sxs-lookup"><span data-stu-id="c5dac-370">Best</span></span> </td><td> <span data-ttu-id="c5dac-371">コンテンツと UI はユーザーの位置に適合するため、ユーザーは、予期されるユーザー移動の範囲内でコンテンツと自然に対話できます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-371">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c5dac-372">あっ</span><span class="sxs-lookup"><span data-stu-id="c5dac-372">Meets</span></span> </td><td> <span data-ttu-id="c5dac-373">UI はユーザーの位置に適合しますが、ユーザーが位置を調整する必要があるキーコンテンツのビューが妨げられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-373">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="c5dac-374">失敗</span><span class="sxs-lookup"><span data-stu-id="c5dac-374">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="c5dac-375">UI 要素は移動中に失われるかロックされ、ユーザーはコントロールを自然に返す (または検索する) ことができません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-375">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="c5dac-376">UI 要素は、プライマリコンテンツのビューを制限します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-376">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="c5dac-377">UI の移動は、特に <a href="../../design/billboarding-and-tag-along.md">タグに沿っ</a> た ui 要素によって、距離や勢いを表示するために最適化されていません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-377">UI movement is not optimized for viewing distance and momentum particularly with <a href="../../design/billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="c5dac-378">測定する方法</span><span class="sxs-lookup"><span data-stu-id="c5dac-378">How to measure</span></span>

* <span data-ttu-id="c5dac-379">すべての測定値は、シナリオの妥当な範囲内で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-379">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="c5dac-380">ユーザーの移動は変化しますが、ユーザーの操作を極端に行うことなくアプリにトリックをかけることは避けてください。</span><span class="sxs-lookup"><span data-stu-id="c5dac-380">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="c5dac-381">UI 要素の場合、ユーザーの移動に関係なく、関連するコントロールを使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-381">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="c5dac-382">たとえば、ユーザーが zoom を使用して3D マップを表示しているときに、場所に関係なく、ユーザーがズームコントロールをすぐに使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-382">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5dac-383">Recommendations</span><span class="sxs-lookup"><span data-stu-id="c5dac-383">Recommendations</span></span>

* <span data-ttu-id="c5dac-384">ユーザーはカメラで、動きを制御します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-384">The user is the camera and they control the movement.</span></span> <span data-ttu-id="c5dac-385">これらのドライブを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-385">Let them drive.</span></span>
* <span data-ttu-id="c5dac-386">テキストと menuing システムの billboarding を検討してください。これは、ユーザーが移動した場合に、ワールドロックまたは非表示になります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-386">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="c5dac-387">ユーザーが前に何をしているかをユーザーが確認できるようにしながら、ユーザーに従う必要があるコンテンツにはタグを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-387">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="c5dac-388">リソース</span><span class="sxs-lookup"><span data-stu-id="c5dac-388">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5dac-389">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="c5dac-389">Documentation</span></span>

* [<span data-ttu-id="c5dac-390">操作の設計</span><span class="sxs-lookup"><span data-stu-id="c5dac-390">Interaction design</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="c5dac-391">色、光、素材</span><span class="sxs-lookup"><span data-stu-id="c5dac-391">Color, light, and material</span></span>](../../color,-light-and-materials.md)
* [<span data-ttu-id="c5dac-392">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="c5dac-392">Billboarding and tag-along</span></span>](../../design/billboarding-and-tag-along.md)
* [<span data-ttu-id="c5dac-393">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="c5dac-393">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="c5dac-394">自発運動とユーザー移動</span><span class="sxs-lookup"><span data-stu-id="c5dac-394">Self-motion and user locomotion</span></span>](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a><span data-ttu-id="c5dac-395">入力の相互作用のわかりやすさ</span><span class="sxs-lookup"><span data-stu-id="c5dac-395">Input interaction clarity</span></span>

<span data-ttu-id="c5dac-396">入力の相互作用の明確さは、アプリのユーザビリティにとって重要であり、入力の一貫性、approachability、相互作用メソッドの発見性などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-396">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="c5dac-397">ユーザーは、relearning なしでプラットフォーム全体の共通の対話を使用できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-397">User should be able to use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="c5dac-398">アプリにカスタム入力がある場合は、それを明確に伝えることができます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-398">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5dac-399">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="c5dac-399">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5dac-400"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-400"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5dac-401"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-401"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5dac-402">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-402">✔️</span></span></td>
        <td><span data-ttu-id="c5dac-403">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-403">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5dac-404">品質基準</span><span class="sxs-lookup"><span data-stu-id="c5dac-404">Quality criteria</span></span>

|  <span data-ttu-id="c5dac-405">最高</span><span class="sxs-lookup"><span data-stu-id="c5dac-405">Best</span></span>  |  <span data-ttu-id="c5dac-406">あっ</span><span class="sxs-lookup"><span data-stu-id="c5dac-406">Meets</span></span> |  <span data-ttu-id="c5dac-407">失敗</span><span class="sxs-lookup"><span data-stu-id="c5dac-407">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5dac-408">入力の相互作用メソッドは、Windows Mixed Reality に用意されている [ガイダンス](../../design/interaction-fundamentals.md)と一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-408">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](../../design/interaction-fundamentals.md).</span></span> <span data-ttu-id="c5dac-409">任意のカスタム入力を標準入力で冗長にする (標準の対話を使用する) ことはできません。また、ユーザーに明確に通知してデモンストレーションする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-409">Any custom input should not be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="c5dac-410">"最適" に似ていますが、カスタム入力は標準の入力方式では冗長です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-410">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="c5dac-411">ユーザーは引き続き、アプリのエクスペリエンスの目標と進行状況を達成できます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-411">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="c5dac-412">入力方法またはボタンのマッピングを理解するのが困難です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-412">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="c5dac-413">入力は大幅にカスタマイズされており、標準入力、命令なし、または疲労や快適な問題を引き起こす可能性がありません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-413">Input is heavily customized, does not support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="c5dac-414">測定する方法</span><span class="sxs-lookup"><span data-stu-id="c5dac-414">How to measure</span></span>

* <span data-ttu-id="c5dac-415">アプリでは、一貫 [した標準の入力方法が使用されます。](../../design/interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="c5dac-415">The app uses consistent [standard input methods.](../../design/interaction-fundamentals.md)</span></span>
* <span data-ttu-id="c5dac-416">アプリにカスタム入力がある場合は、次の方法で明確に伝達されます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-416">If the app has custom input, it is clearly communicated through:</span></span>
* <span data-ttu-id="c5dac-417">最初の実行エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="c5dac-417">First-run experience</span></span>
* <span data-ttu-id="c5dac-418">入門画面</span><span class="sxs-lookup"><span data-stu-id="c5dac-418">Introductory screens</span></span>
* <span data-ttu-id="c5dac-419">ヒント</span><span class="sxs-lookup"><span data-stu-id="c5dac-419">Tooltips</span></span>
* <span data-ttu-id="c5dac-420">ハンド コーチ</span><span class="sxs-lookup"><span data-stu-id="c5dac-420">Hand coach</span></span>
* <span data-ttu-id="c5dac-421">ヘルプセクション</span><span class="sxs-lookup"><span data-stu-id="c5dac-421">Help section</span></span>
* <span data-ttu-id="c5dac-422">ボイス オーバー</span><span class="sxs-lookup"><span data-stu-id="c5dac-422">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5dac-423">Recommendations</span><span class="sxs-lookup"><span data-stu-id="c5dac-423">Recommendations</span></span>

* <span data-ttu-id="c5dac-424">可能な場合は常に標準の入力方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-424">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="c5dac-425">標準以外の入力方法については、デモ、チュートリアル、およびツールヒントを提供します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-425">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="c5dac-426">アプリ全体で一貫した相互作用モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-426">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="c5dac-427">リソース</span><span class="sxs-lookup"><span data-stu-id="c5dac-427">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5dac-428">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="c5dac-428">Documentation</span></span>

* [<span data-ttu-id="c5dac-429">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="c5dac-429">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="c5dac-430">対話型オブジェクト</span><span class="sxs-lookup"><span data-stu-id="c5dac-430">Interactable objects</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="c5dac-431">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="c5dac-431">Head-gaze and dwell</span></span>](../../design/gaze-and-dwell.md)
* [<span data-ttu-id="c5dac-432">カーソル</span><span class="sxs-lookup"><span data-stu-id="c5dac-432">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="c5dac-433">快適で見つめ</span><span class="sxs-lookup"><span data-stu-id="c5dac-433">Comfort and gaze</span></span>](../../design/comfort.md#gaze-direction)
* [<span data-ttu-id="c5dac-434">音声入力</span><span class="sxs-lookup"><span data-stu-id="c5dac-434">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="c5dac-435">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="c5dac-435">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="c5dac-436">Unity 用入力移植ガイド</span><span class="sxs-lookup"><span data-stu-id="c5dac-436">Input porting guide for Unity</span></span>](../porting-apps/input-porting-guide-for-unity.md)
* [<span data-ttu-id="c5dac-437">Unity でのキーボード入力</span><span class="sxs-lookup"><span data-stu-id="c5dac-437">Keyboard input in Unity</span></span>](../unity/keyboard-input-in-unity.md)
* [<span data-ttu-id="c5dac-438">Unity の視線入力</span><span class="sxs-lookup"><span data-stu-id="c5dac-438">Gaze in Unity</span></span>](../unity/gaze-in-unity.md)
* [<span data-ttu-id="c5dac-439">Unity でのジェスチャとモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="c5dac-439">Gestures and motion controllers in Unity</span></span>](../unity/gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="c5dac-440">Unity の音声入力</span><span class="sxs-lookup"><span data-stu-id="c5dac-440">Voice input in Unity</span></span>](../unity/voice-input-in-unity.md)
* [<span data-ttu-id="c5dac-441">DirectX でのキーボード、マウス、およびコントローラー入力</span><span class="sxs-lookup"><span data-stu-id="c5dac-441">Keyboard, mouse, and controller input in DirectX</span></span>](../../keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="c5dac-442">DirectX でのヘッド視線入力とアイ視線入力</span><span class="sxs-lookup"><span data-stu-id="c5dac-442">Head and eye gaze in DirectX</span></span>](../native/gaze-in-directx.md)
* [<span data-ttu-id="c5dac-443">DirectX での手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="c5dac-443">Hands and motion controllers in DirectX</span></span>](../native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="c5dac-444">DirectX の音声入力</span><span class="sxs-lookup"><span data-stu-id="c5dac-444">Voice input in DirectX</span></span>](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5dac-445">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="c5dac-445">Tools and tutorials</span></span>

* [<span data-ttu-id="c5dac-446">ケーススタディ: よりパーソナルコンピューティングの追求</span><span class="sxs-lookup"><span data-stu-id="c5dac-446">Case study: The pursuit of more personal computing</span></span>](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="c5dac-447">キャストスタディ: HoloStudio UI と相互作用設計学習</span><span class="sxs-lookup"><span data-stu-id="c5dac-447">Cast study: HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="c5dac-448">サンプルアプリ: 要素の周期テーブル</span><span class="sxs-lookup"><span data-stu-id="c5dac-448">Sample app: Periodic table of the elements</span></span>](../unity/periodic-table-of-the-elements.md)
* [<span data-ttu-id="c5dac-449">サンプルアプリ: 旧暦モジュール</span><span class="sxs-lookup"><span data-stu-id="c5dac-449">Sample app: Lunar module</span></span>](../unity/lunar-module.md)

## <a name="interactable-objects"></a><span data-ttu-id="c5dac-450">対話型オブジェクト</span><span class="sxs-lookup"><span data-stu-id="c5dac-450">Interactable objects</span></span>

<span data-ttu-id="c5dac-451">ボタンは、2D 抽象ワールドでイベントをトリガーするために使用される比喩です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-451">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="c5dac-452">3次元混合の現実世界では、この抽象化の世界に限定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-452">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="c5dac-453">イベントをトリガーする対話型オブジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-453">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="c5dac-454">対話型オブジェクトは、テーブル上のコーヒーカップの任意のものとして、無線でバルーンに表示できます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-454">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="c5dac-455">フォームに関係なく、対話型オブジェクトは、ユーザーがビジュアルおよびオーディオキューを使用して明確に認識できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-455">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5dac-456">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="c5dac-456">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5dac-457"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-457"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5dac-458"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-458"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5dac-459">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-459">✔️</span></span></td>
        <td><span data-ttu-id="c5dac-460">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-460">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5dac-461">品質基準</span><span class="sxs-lookup"><span data-stu-id="c5dac-461">Quality criteria</span></span>

|  <span data-ttu-id="c5dac-462">最高</span><span class="sxs-lookup"><span data-stu-id="c5dac-462">Best</span></span>  |  <span data-ttu-id="c5dac-463">あっ</span><span class="sxs-lookup"><span data-stu-id="c5dac-463">Meets</span></span> |  <span data-ttu-id="c5dac-464">失敗</span><span class="sxs-lookup"><span data-stu-id="c5dac-464">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5dac-465">フォームに関係なく、対話型オブジェクトは、アイドル、ターゲット、および選択された3つの状態にわたって、ビジュアルおよびオーディオのキューを介して認識されます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-465">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="c5dac-466">"ご覧のように、エクスペリエンス全体で一貫して使用されています。</span><span class="sxs-lookup"><span data-stu-id="c5dac-466">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="c5dac-467">オブジェクトは、フリーターゲットのエラーを許容するようにスケーリングおよび配布されます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-467">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="c5dac-468">ユーザーは、オーディオまたはビジュアルフィードバックによってオブジェクトを対話型として認識し、オブジェクトをターゲットにしてアクティブ化することができます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-468">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="c5dac-469">ビジュアルまたはオーディオのキューがない場合、ユーザーは対話型オブジェクトを認識できません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-469">Given no visual or audio cues, user cannot recognize an interactable object.</span></span> <span data-ttu-id="c5dac-470">オブジェクトのスケールやオブジェクト間の距離により、相互作用がエラーを起こしやすくなります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-470">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="c5dac-471">測定する方法</span><span class="sxs-lookup"><span data-stu-id="c5dac-471">How to measure</span></span>

* <span data-ttu-id="c5dac-472">対話型オブジェクトは ' 対話型 ' として認識されます。ボタン、メニュー、アプリ固有のコンテンツを含む。</span><span class="sxs-lookup"><span data-stu-id="c5dac-472">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app specific content.</span></span> <span data-ttu-id="c5dac-473">経験則として、対話型オブジェクトを対象とする場合は、ビジュアルとオーディオの手掛かりが必要です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-473">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5dac-474">Recommendations</span><span class="sxs-lookup"><span data-stu-id="c5dac-474">Recommendations</span></span>

* <span data-ttu-id="c5dac-475">対話のためにビジュアルとオーディオフィードバックを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-475">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="c5dac-476">視覚的なフィードバックは、入力状態 (アイドル、ターゲット、選択) ごとに区別される必要があります</span><span class="sxs-lookup"><span data-stu-id="c5dac-476">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="c5dac-477">対話型オブジェクトは、エラーをターゲットにするためにスケーリングして配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-477">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="c5dac-478">グループ化された対話型オブジェクト (メニューバーやリストなど) には、ターゲットを設定するための適切なスペースが必要です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-478">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="c5dac-479">音声コマンドをサポートするボタンとメニューでは、command キーワードにテキストラベルを指定する必要があります (「参照してください」と言います)。</span><span class="sxs-lookup"><span data-stu-id="c5dac-479">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="c5dac-480">リソース</span><span class="sxs-lookup"><span data-stu-id="c5dac-480">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5dac-481">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="c5dac-481">Documentation</span></span>

* [<span data-ttu-id="c5dac-482">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="c5dac-482">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="c5dac-483">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="c5dac-483">Text in Unity</span></span>](../unity/text-in-unity.md)
* [<span data-ttu-id="c5dac-484">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="c5dac-484">Bounding box and App bar</span></span>](../../design/app-bar-and-bounding-box.md)
* [<span data-ttu-id="c5dac-485">音声入力</span><span class="sxs-lookup"><span data-stu-id="c5dac-485">Voice input</span></span>](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5dac-486">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="c5dac-486">Tools and tutorials</span></span>

* [<span data-ttu-id="c5dac-487">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="c5dac-487">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="c5dac-488">部屋のスキャン</span><span class="sxs-lookup"><span data-stu-id="c5dac-488">Room scanning</span></span>

<span data-ttu-id="c5dac-489">空間マッピングデータを必要とするアプリは、ユーザーがデバイスをアクティブにして環境を探索するときに、このデータを時間の経過と共に自動的に収集するためにデバイスに依存します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-489">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="c5dac-490">このデータの完全性と品質は、ユーザーが実行した探索の量、探索から経過した時間、家具やドアなどのオブジェクトが領域をスキャンした後に移動されたかどうかなど、さまざまな要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-490">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="c5dac-491">多くのアプリは、エクスペリエンスの開始時に空間マッピングデータを分析して、ユーザーが空間マップの完全性と品質を向上させるために追加の手順を実行する必要があるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-491">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="c5dac-492">ユーザーが環境をスキャンする必要がある場合は、スキャンの実行中に [ガイダンスのクリア] を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-492">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5dac-493">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="c5dac-493">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5dac-494"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-494"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5dac-495"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-495"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5dac-496">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-496">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5dac-497">品質基準</span><span class="sxs-lookup"><span data-stu-id="c5dac-497">Quality criteria</span></span>

|  <span data-ttu-id="c5dac-498">最高</span><span class="sxs-lookup"><span data-stu-id="c5dac-498">Best</span></span>  |  <span data-ttu-id="c5dac-499">あっ</span><span class="sxs-lookup"><span data-stu-id="c5dac-499">Meets</span></span> |  <span data-ttu-id="c5dac-500">失敗</span><span class="sxs-lookup"><span data-stu-id="c5dac-500">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5dac-501">ユーザーによるスキャンを通知する空間メッシュの視覚化が進行中です。</span><span class="sxs-lookup"><span data-stu-id="c5dac-501">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="c5dac-502">ユーザーは、何を行うか、およびスキャンが開始および停止するタイミングを明確に把握します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-502">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="c5dac-503">空間メッシュの視覚化が提供されていますが、ユーザーが何をしているかを明確に把握しておらず、進行状況に関する情報が提供されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-503">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="c5dac-504">メッシュの視覚化がありません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-504">No visualization of mesh.</span></span> <span data-ttu-id="c5dac-505">検索する場所、またはスキャンの開始/停止時に関するガイダンス情報はユーザーに提供されません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-505">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="c5dac-506">測定する方法</span><span class="sxs-lookup"><span data-stu-id="c5dac-506">How to measure</span></span>

* <span data-ttu-id="c5dac-507">必要なルームスキャン中に、検索する場所と、スキャンを開始および停止するタイミングを示すビジュアルおよびオーディオのガイダンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-507">During a required room scan, visual and audio guidance is provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5dac-508">Recommendations</span><span class="sxs-lookup"><span data-stu-id="c5dac-508">Recommendations</span></span>

* <span data-ttu-id="c5dac-509">ユーザーの近くにあるユーザーの合計ボリュームがエクスペリエンスの一部である必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-509">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="c5dac-510">スキャンが開始され、進行状況インジケーターなどの停止時に通信します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-510">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="c5dac-511">スキャン中にメッシュの視覚エフェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-511">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="c5dac-512">ユーザーが部屋を見たり、移動したりすることを奨励するために、ビジュアルとオーディオの手掛かりを提供します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-512">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="c5dac-513">データを改善するための場所をユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-513">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="c5dac-514">多くの場合、必要なスキャン品質を得るために、ユーザーに対して実行する必要があること (たとえば、天井、家具を見てみてください) を伝えることが最適な場合があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-514">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="c5dac-515">リソース</span><span class="sxs-lookup"><span data-stu-id="c5dac-515">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="c5dac-516">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="c5dac-516">Documentation</span></span>

* [<span data-ttu-id="c5dac-517">部屋のスキャンの可視化</span><span class="sxs-lookup"><span data-stu-id="c5dac-517">Room scan visualization</span></span>](../../design/room-scan-visualization.md)
* [<span data-ttu-id="c5dac-518">ケーススタディ: HoloLens の空間マッピング機能の拡張</span><span class="sxs-lookup"><span data-stu-id="c5dac-518">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="c5dac-519">ケーススタディ: HoloTour の空間サウンド設計</span><span class="sxs-lookup"><span data-stu-id="c5dac-519">Case study: Spatial sound design for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="c5dac-520">ケーススタディ: フラグメントでのイマーシブエクスペリエンスの作成</span><span class="sxs-lookup"><span data-stu-id="c5dac-520">Case study: Creating an immersive experience in Fragments</span></span>](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="c5dac-521">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="c5dac-521">Tools and tutorials</span></span>

* [<span data-ttu-id="c5dac-522">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="c5dac-522">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="c5dac-523">方向インジケーター</span><span class="sxs-lookup"><span data-stu-id="c5dac-523">Directional indicators</span></span>

<span data-ttu-id="c5dac-524">Mixed reality アプリでは、コンテンツは、実際のオブジェクトによって view または occluded のフィールドの外部にある場合があります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-524">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="c5dac-525">適切にデザインされたアプリを使用すると、ユーザーが非表示のコンテンツを簡単に見つけられるようになります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-525">A well designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="c5dac-526">ディレクショナルインジケーターは、ユーザーに重要なコンテンツを通知し、ユーザーの位置を基準にしてコンテンツに関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-526">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="c5dac-527">非表示コンテンツに関するガイダンスは、サウンドの発信器、方向矢印、または直接視覚的な合図の形式になります。</span><span class="sxs-lookup"><span data-stu-id="c5dac-527">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5dac-528">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="c5dac-528">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5dac-529"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-529"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5dac-530"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-530"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5dac-531">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-531">✔️</span></span></td>
        <td><span data-ttu-id="c5dac-532">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-532">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5dac-533">品質基準</span><span class="sxs-lookup"><span data-stu-id="c5dac-533">Quality criteria</span></span>

|  <span data-ttu-id="c5dac-534">最高</span><span class="sxs-lookup"><span data-stu-id="c5dac-534">Best</span></span>  |  <span data-ttu-id="c5dac-535">あっ</span><span class="sxs-lookup"><span data-stu-id="c5dac-535">Meets</span></span> |  <span data-ttu-id="c5dac-536">失敗</span><span class="sxs-lookup"><span data-stu-id="c5dac-536">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5dac-537">ビジュアルおよびオーディオキューは、ビューのフィールドの外部にある関連するコンテンツをユーザーに直接案内します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-537">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="c5dac-538">コンテンツの一般的な方向にユーザーを示す矢印またはインジケーター。</span><span class="sxs-lookup"><span data-stu-id="c5dac-538">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="c5dac-539">関連するコンテンツはビューのフィールドの外部にあり、ユーザーには不適切または場所のガイダンスは提供されません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-539">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="c5dac-540">測定する方法</span><span class="sxs-lookup"><span data-stu-id="c5dac-540">How to measure</span></span>

* <span data-ttu-id="c5dac-541">ビューの [ユーザー] フィールド以外の関連するコンテンツは、ビジュアルまたはオーディオキューを使用して検出できます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-541">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5dac-542">Recommendations</span><span class="sxs-lookup"><span data-stu-id="c5dac-542">Recommendations</span></span>

* <span data-ttu-id="c5dac-543">関連するコンテンツがユーザーのビューの外部にある場合は、方向インジケーターとオーディオキューを使用して、ユーザーをコンテンツに案内します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-543">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="c5dac-544">多くの場合、方向性のある矢印よりも直接の視覚的なガイドをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c5dac-544">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="c5dac-545">方向インジケーターをカーソルに組み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-545">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="c5dac-546">リソース</span><span class="sxs-lookup"><span data-stu-id="c5dac-546">Resources</span></span>

* [<span data-ttu-id="c5dac-547">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="c5dac-547">Holographic frame</span></span>](../../design/holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="c5dac-548">データの読み込み</span><span class="sxs-lookup"><span data-stu-id="c5dac-548">Data loading</span></span>

<span data-ttu-id="c5dac-549">プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-549">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="c5dac-550">これは、進行状況インジケーターが表示されているときにユーザーがアプリと対話できないことを意味し、待機時間がどの程度かかるかを示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="c5dac-550">It can mean that the user cannot interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="c5dac-551">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="c5dac-551">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="c5dac-552"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-552"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="c5dac-553"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="c5dac-553"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="c5dac-554">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-554">✔️</span></span></td>
        <td><span data-ttu-id="c5dac-555">✔️</span><span class="sxs-lookup"><span data-stu-id="c5dac-555">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="c5dac-556">品質基準</span><span class="sxs-lookup"><span data-stu-id="c5dac-556">Quality criteria</span></span>

|  <span data-ttu-id="c5dac-557">最高</span><span class="sxs-lookup"><span data-stu-id="c5dac-557">Best</span></span>  |  <span data-ttu-id="c5dac-558">あっ</span><span class="sxs-lookup"><span data-stu-id="c5dac-558">Meets</span></span> |  <span data-ttu-id="c5dac-559">失敗</span><span class="sxs-lookup"><span data-stu-id="c5dac-559">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="c5dac-560">データの読み込み中または処理中の進行状況を示す進行状況バーまたはリングの形式でのアニメーション化されたビジュアルインジケーター。</span><span class="sxs-lookup"><span data-stu-id="c5dac-560">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="c5dac-561">ビジュアルインジケーターは、待機時間の長さに関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-561">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="c5dac-562">ユーザーには、データの読み込みが進行中であることが通知されますが、待機時間を示すことはできません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-562">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="c5dac-563">タスクのデータ読み込みまたはプロセスインジケーターが5秒より長くかかっていません。</span><span class="sxs-lookup"><span data-stu-id="c5dac-563">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="c5dac-564">測定する方法</span><span class="sxs-lookup"><span data-stu-id="c5dac-564">How to measure</span></span>

* <span data-ttu-id="c5dac-565">データの読み込み中に、5秒を超える空の状態がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-565">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="c5dac-566">Recommendations</span><span class="sxs-lookup"><span data-stu-id="c5dac-566">Recommendations</span></span>

* <span data-ttu-id="c5dac-567">ユーザーがこのアプリを停止またはクラッシュしていると認識した場合に、進行状況を示すデータ読み込みのアニメーターを提供します。</span><span class="sxs-lookup"><span data-stu-id="c5dac-567">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="c5dac-568">目安として合理的なのは、5秒以上かかる可能性のある "読み込み" アクティビティです。</span><span class="sxs-lookup"><span data-stu-id="c5dac-568">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="c5dac-569">リソース</span><span class="sxs-lookup"><span data-stu-id="c5dac-569">Resources</span></span>

* [<span data-ttu-id="c5dac-570">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="c5dac-570">Displaying progress</span></span>](../../design/progress.md)
