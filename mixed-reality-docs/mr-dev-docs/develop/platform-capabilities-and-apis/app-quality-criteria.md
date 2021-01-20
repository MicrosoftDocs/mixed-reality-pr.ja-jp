---
title: アプリの品質基準
description: このドキュメントでは、mixed reality アプリの品質に影響する上位の要因について説明します。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: アプリ品質基準、mixed reality、mixed reality アプリ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: 3f6752c0a15ae7db21be1f4a6d2843339ab28a5c
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581268"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="2d3bb-104">アプリの品質基準</span><span class="sxs-lookup"><span data-stu-id="2d3bb-104">App quality criteria</span></span>

<span data-ttu-id="2d3bb-105">このドキュメントでは、mixed reality アプリの品質に影響する上位の要因について説明します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="2d3bb-106">各要素について、次の情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-106">For each factor, the following information is provided</span></span>
* <span data-ttu-id="2d3bb-107">[概要] –品質要因と重要な理由について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-107">Overview – a brief description of the quality factor and why it's important.</span></span>
* <span data-ttu-id="2d3bb-108">デバイスへの影響-どの種類のウィンドウに Mixed Reality デバイスが影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-108">Device impact - which type of Window Mixed Reality device is affected.</span></span>
* <span data-ttu-id="2d3bb-109">品質基準–品質要因を評価する方法。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="2d3bb-110">方法: 問題を測定 (または経験) する方法。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="2d3bb-111">推奨事項–より優れたユーザーエクスペリエンスを提供するためのアプローチの概要です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="2d3bb-112">リソース–優れたアプリエクスペリエンスを作成するのに役立つ、関連する開発者および設計リソース。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="2d3bb-113">フレーム レート</span><span class="sxs-lookup"><span data-stu-id="2d3bb-113">Frame rate</span></span>

<span data-ttu-id="2d3bb-114">フレームレートは、ホログラムの安定性とユーザーの快適さの第一柱です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="2d3bb-115">推奨されるターゲットの下にあるフレームレートは、ホログラムがちらつくように見え、エクスペリエンスの believability に悪影響を及ぼし、目に見える疲労が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="2d3bb-116">Windows Mixed Reality のイマーシブヘッドセットでのエクスペリエンスの目標フレームレートは、サポートしている Windows Mixed Reality 互換 Pc に応じて、60 Hz または 90 Hz です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets is either 60 Hz or 90 Hz depending on which Windows Mixed Reality Compatible PCs you're supporting.</span></span> <span data-ttu-id="2d3bb-117">HoloLens の場合、ターゲットフレームレートは 60 Hz です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-117">For HoloLens, the target frame rate is 60 Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="2d3bb-118">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d3bb-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-119"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="2d3bb-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2d3bb-121">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-121">✔️</span></span></td>
        <td><span data-ttu-id="2d3bb-122">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="2d3bb-123">品質基準</span><span class="sxs-lookup"><span data-stu-id="2d3bb-123">Quality criteria</span></span>

|  <span data-ttu-id="2d3bb-124">最高</span><span class="sxs-lookup"><span data-stu-id="2d3bb-124">Best</span></span>  |  <span data-ttu-id="2d3bb-125">あっ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-125">Meets</span></span> |  <span data-ttu-id="2d3bb-126">失敗</span><span class="sxs-lookup"><span data-stu-id="2d3bb-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="2d3bb-127">アプリは、ターゲットデバイスの1秒あたりのフレーム数 (FPS) の目標を一貫して満たしています: HoloLens で 60 fps。ウルトラ Pc で 90 fps。メインストリーム Pc では 60 fps です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-127">The app consistently meets frames per second (FPS) goal for target device: 60 fps on HoloLens; 90 fps on Ultra PCs; and 60 fps on mainstream PCs.</span></span> | <span data-ttu-id="2d3bb-128">アプリは、コアエクスペリエンスを妨げるすることなく断続的にフレームが削除されるか、または FPS は望ましい目標よりも一貫して低くなりますが、アプリのエクスペリエンスを妨げることはありません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-128">The app has intermittent frame drops not impeding the core experience, or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="2d3bb-129">アプリでは、平均で10秒以内にフレームレートが低下しています。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-129">The app is experiencing a drop in frame rate on average every 10 seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="2d3bb-130">測定する方法</span><span class="sxs-lookup"><span data-stu-id="2d3bb-130">How to measure</span></span>

* <span data-ttu-id="2d3bb-131">リアルタイムのフレームレートグラフは、 [Windows デバイスポータル](using-the-windows-device-portal.md#system-performance) によって "システムパフォーマンス" によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="2d3bb-132">開発用デバッグでは、フレームレート診断カウンターをアプリに追加します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="2d3bb-133">「サンプルカウンターのリソース」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="2d3bb-134">フレームレートが低下するのは、アプリの実行中に、ヘッドを左右に移動して、デバイスで発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="2d3bb-135">ホログラムが予期しないちらつきの動きを示している場合、フレームレートが低いか、安定性平面が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="2d3bb-136">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-136">Recommendations</span></span>

* <span data-ttu-id="2d3bb-137">開発作業の開始時にフレームレートカウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="2d3bb-138">フレームレートが低下した変更は、パフォーマンスバグとして評価され、適切に解決される必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="2d3bb-139">リソース</span><span class="sxs-lookup"><span data-stu-id="2d3bb-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="2d3bb-140">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="2d3bb-140">Documentation</span></span>

* [<span data-ttu-id="2d3bb-141">Mixed Reality のパフォーマンスについて</span><span class="sxs-lookup"><span data-stu-id="2d3bb-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="2d3bb-142">ホログラムの安定性とフレームレート</span><span class="sxs-lookup"><span data-stu-id="2d3bb-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="2d3bb-143">資産のパフォーマンスの予算</span><span class="sxs-lookup"><span data-stu-id="2d3bb-143">Asset performance budget</span></span>](../../design/asset-creation-process.md)
* [<span data-ttu-id="2d3bb-144">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-144">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="2d3bb-145">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="2d3bb-145">Tools and tutorials</span></span>

* [<span data-ttu-id="2d3bb-146">混合 Reality ツールキット、FPS カウンターの表示</span><span class="sxs-lookup"><span data-stu-id="2d3bb-146">Mixed Reality Toolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="2d3bb-147">混合現実ツールキット、シェーダー</span><span class="sxs-lookup"><span data-stu-id="2d3bb-147">Mixed Reality Toolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="2d3bb-148">外部参照</span><span class="sxs-lookup"><span data-stu-id="2d3bb-148">External references</span></span>

* [<span data-ttu-id="2d3bb-149">Unity, モバイルアプリケーションの最適化</span><span class="sxs-lookup"><span data-stu-id="2d3bb-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="2d3bb-150">ホログラムの安定性</span><span class="sxs-lookup"><span data-stu-id="2d3bb-150">Hologram stability</span></span>

<span data-ttu-id="2d3bb-151">安定したホログラムは、アプリの使いやすさと believability を向上させ、ユーザーにより快適な表示エクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="2d3bb-152">ホログラムの安定性の質は、優れたアプリ開発と、その環境を理解 (追跡) するデバイスの機能によって得られます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="2d3bb-153">フレームレートは安定性の最初の柱ですが、その他の要因は次のような安定性に影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="2d3bb-154">安定化平面の使用</span><span class="sxs-lookup"><span data-stu-id="2d3bb-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="2d3bb-155">空間アンカーへの距離</span><span class="sxs-lookup"><span data-stu-id="2d3bb-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="2d3bb-156">追跡</span><span class="sxs-lookup"><span data-stu-id="2d3bb-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="2d3bb-157">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d3bb-158"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-158"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="2d3bb-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2d3bb-160">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="2d3bb-161">品質基準</span><span class="sxs-lookup"><span data-stu-id="2d3bb-161">Quality criteria</span></span>

|  <span data-ttu-id="2d3bb-162">最高</span><span class="sxs-lookup"><span data-stu-id="2d3bb-162">Best</span></span>  |  <span data-ttu-id="2d3bb-163">あっ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-163">Meets</span></span> |  <span data-ttu-id="2d3bb-164">失敗</span><span class="sxs-lookup"><span data-stu-id="2d3bb-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="2d3bb-165">ホログラムは常に安定した状態で表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="2d3bb-166">セカンダリコンテンツは予期しない移動を示しています。または、予期しない移動はアプリ全体のエクスペリエンスを妨げることはありません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-166">Secondary content shows unexpected movement; or unexpected movement doesn't impede overall app experience.</span></span> | <span data-ttu-id="2d3bb-167">フレーム内のプライマリコンテンツは、予期しない移動を示しています。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-167">Primary content in frame shows unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="2d3bb-168">測定する方法</span><span class="sxs-lookup"><span data-stu-id="2d3bb-168">How to measure</span></span>

<span data-ttu-id="2d3bb-169">デバイスを装着し、エクスペリエンスを表示しています。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="2d3bb-170">ヘッドを左右に移動します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-170">Move your head from side to side.</span></span> <span data-ttu-id="2d3bb-171">ホログラムが予期しない動きを示している場合、フレームレートが低いか、または安定平面が焦点平面に正しく配置されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-171">If the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="2d3bb-172">ホログラムと環境内を移動し、スイム・ jumpiness などの動作を探します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="2d3bb-173">この種類のモーションは、デバイスが環境を追跡していない、または空間アンカーへの距離が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="2d3bb-174">フレーム内に複数のホログラムがある場合は、さまざまな深度でのホログラムの動作を観察し、揺れるが表示されている場合は、安定化平面によって発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="2d3bb-175">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-175">Recommendations</span></span>

* <span data-ttu-id="2d3bb-176">開発作業の開始時にフレームレートカウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-176">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="2d3bb-177">安定化平面を使用します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="2d3bb-178">アンカーの3メートル以内に固定したホログラムを常にレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="2d3bb-179">適切な追跡のために環境がセットアップされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-179">Make sure your environment is set up for proper tracking.</span></span>
* <span data-ttu-id="2d3bb-180">フレーム内のさまざまな焦点深度レベルでホログラムを使用しないように、エクスペリエンスを設計します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="2d3bb-181">リソース</span><span class="sxs-lookup"><span data-stu-id="2d3bb-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="2d3bb-182">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="2d3bb-182">Documentation</span></span>

* [<span data-ttu-id="2d3bb-183">ホログラムの安定性とフレームレート</span><span class="sxs-lookup"><span data-stu-id="2d3bb-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="2d3bb-184">安定化平面を使用したケーススタディ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="2d3bb-185">Mixed Reality のパフォーマンスについて</span><span class="sxs-lookup"><span data-stu-id="2d3bb-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="2d3bb-186">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-186">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="2d3bb-187">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="2d3bb-187">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="2d3bb-188">追跡エラーの処理</span><span class="sxs-lookup"><span data-stu-id="2d3bb-188">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="2d3bb-189">静止フレーム (参照)</span><span class="sxs-lookup"><span data-stu-id="2d3bb-189">Stationary frame of reference</span></span>](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="2d3bb-190">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="2d3bb-190">Tools and tutorials</span></span>

* [<span data-ttu-id="2d3bb-191">MR コンパニオンキット、Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="2d3bb-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="2d3bb-192">実際のサーフェイス上のホログラムの位置</span><span class="sxs-lookup"><span data-stu-id="2d3bb-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="2d3bb-193">物理的なオブジェクトを使用したホログラムの間違った配置 (相互に関係するように設計されている場合) は、ホログラムと現実世界の非共用体を明確に示しています。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) are a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="2d3bb-194">配置の精度は、シナリオのニーズに対して相対的である必要があります。たとえば、一般的な表面配置では空間マップを使用できますが、正確に配置するには、マーカーと調整を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="2d3bb-195">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d3bb-196"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-196"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="2d3bb-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2d3bb-198">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-198">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="2d3bb-199">品質基準</span><span class="sxs-lookup"><span data-stu-id="2d3bb-199">Quality criteria</span></span>

|  <span data-ttu-id="2d3bb-200">最高</span><span class="sxs-lookup"><span data-stu-id="2d3bb-200">Best</span></span>  |  <span data-ttu-id="2d3bb-201">あっ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-201">Meets</span></span> |  <span data-ttu-id="2d3bb-202">失敗</span><span class="sxs-lookup"><span data-stu-id="2d3bb-202">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="2d3bb-203">ホログラムは、通常、センチメートル ~ インチの範囲内のサーフェイスに配置されます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-203">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="2d3bb-204">より正確な精度が必要な場合は、アプリの仕様内でコラボレーションのための効率的な手段を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-204">If you need more accuracy, the app should provide an efficient means for collaboration within the app spec.</span></span> | <span data-ttu-id="2d3bb-205">NA</span><span class="sxs-lookup"><span data-stu-id="2d3bb-205">NA</span></span> | <span data-ttu-id="2d3bb-206">サーフェイスを分割するか、表面から離れた場所に表示することによって、ホログラムが物理的なターゲットオブジェクトと共に配置されていないことを認識します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-206">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="2d3bb-207">精度が必要な場合は、ホログラムがシナリオの近接仕様を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-207">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="2d3bb-208">測定する方法</span><span class="sxs-lookup"><span data-stu-id="2d3bb-208">How to measure</span></span>

* <span data-ttu-id="2d3bb-209">空間マップに配置されているホログラムは、サーフェイスの上または下に劇的に浮動小数点型で表示されないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-209">Holograms that are placed on spatial map shouldn't appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="2d3bb-210">正確な配置を必要とするホログラムには、シナリオの要件に対して正確な何らかの形式のマーカーと調整システムが必要です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-210">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="2d3bb-211">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-211">Recommendations</span></span>

* <span data-ttu-id="2d3bb-212">空間マップは、精度が不要な場合にオブジェクトをサーフェイスに配置する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-212">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="2d3bb-213">最適な精度を得るには、マーカーまたはポスターを使用して、ホログラムと Xbox コントローラー (または手動配置機構) を最終的な調整用に設定します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-213">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="2d3bb-214">特大の大きなホログラムを論理部分に分割し、各部分をサーフェイスに配置することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-214">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="2d3bb-215">不適切に設定した interpupillary distance (IPD) は、ホログラムのアラインメントにも影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-215">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="2d3bb-216">常に HoloLens をユーザーの IPD に構成します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-216">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="2d3bb-217">リソース</span><span class="sxs-lookup"><span data-stu-id="2d3bb-217">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="2d3bb-218">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="2d3bb-218">Documentation</span></span>

* [<span data-ttu-id="2d3bb-219">空間マッピングの配置</span><span class="sxs-lookup"><span data-stu-id="2d3bb-219">Spatial mapping placement</span></span>](../../design/spatial-mapping.md#placement)
* [<span data-ttu-id="2d3bb-220">ルームスキャンプロセス</span><span class="sxs-lookup"><span data-stu-id="2d3bb-220">Room scanning process</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="2d3bb-221">空間アンカーのベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="2d3bb-221">Spatial anchors best practices</span></span>](../../design/spatial-anchors.md#best-practices)
* [<span data-ttu-id="2d3bb-222">追跡エラーの処理</span><span class="sxs-lookup"><span data-stu-id="2d3bb-222">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="2d3bb-223">Unity の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="2d3bb-223">Spatial mapping in Unity</span></span>](../unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="2d3bb-224">Vuforia 開発の概要</span><span class="sxs-lookup"><span data-stu-id="2d3bb-224">Vuforia development overview</span></span>](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="2d3bb-225">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="2d3bb-225">Tools and tutorials</span></span>

* [<span data-ttu-id="2d3bb-226">MR ツールキット, 空間マッピングライブラリ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="2d3bb-227">MR コンパニオンキット、ポスター調整のサンプル</span><span class="sxs-lookup"><span data-stu-id="2d3bb-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="2d3bb-228">MR コンパニオンキット、Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="2d3bb-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="2d3bb-229">外部参照</span><span class="sxs-lookup"><span data-stu-id="2d3bb-229">External references</span></span>

* [<span data-ttu-id="2d3bb-230">Lowes のケーススタディ、有効桁数のアラインメント</span><span class="sxs-lookup"><span data-stu-id="2d3bb-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="2d3bb-231">快適なゾーンの表示</span><span class="sxs-lookup"><span data-stu-id="2d3bb-231">Viewing zone of comfort</span></span>

<span data-ttu-id="2d3bb-232">アプリ開発者は、さまざまな深度でコンテンツとホログラムを配置することで、ユーザーの目がどのようになるかを制御します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="2d3bb-233">Hololens のディスプレイは、ユーザーから約 2.0 m 離れた光の距離で固定されているため、HoloLens を装着しているユーザーは、常に 2.0 m に対応して明確なイメージを維持します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-233">Users wearing HoloLens will always accommodate to 2.0 m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0 m away from the user.</span></span> <span data-ttu-id="2d3bb-234">不適切なコンテンツの深さは、視覚不快感や疲労につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="2d3bb-235">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d3bb-236"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-236"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="2d3bb-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2d3bb-238">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="2d3bb-239">品質基準</span><span class="sxs-lookup"><span data-stu-id="2d3bb-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="2d3bb-240">最高</span><span class="sxs-lookup"><span data-stu-id="2d3bb-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="2d3bb-241">2 m にコンテンツを配置します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-241">Place content at 2 m.</span></span></li><li><span data-ttu-id="2d3bb-242">ホログラムを 2 m に配置できず、収束と宿泊の間の競合を回避できない場合、ホログラムの配置に最適なゾーンは 1.25 m ~ 5 m です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-242">When holograms cannot be placed at 2 m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25 m and 5 m.</span></span></li><li><span data-ttu-id="2d3bb-243">どのような場合でも、デザイナーは、ユーザーが 1 + m を操作できるようにコンテンツを構成する必要があります (たとえば、コンテンツサイズと既定の配置パラメーターを調整します)。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="2d3bb-244">シナリオで必要とされない限り、1 m から始まるフェードアウトを使用してクリッピング平面を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-244">Unless not required by the scenario, a clipping plane should be implement with fade out starting at 1 m.</span></span></li><li><span data-ttu-id="2d3bb-245">Motionless ホログラムの詳細な監視が必要な場合は、コンテンツが 50 cm を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-245">In cases where closer observation of a motionless hologram is required, the content shouldn't be closer than 50 cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="2d3bb-246">あっ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-246">Meets</span></span></td><td> <span data-ttu-id="2d3bb-247">コンテンツは、表示およびモーションのガイダンスに含まれていますが、不適切な使用またはクリッピング平面の使用はありません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2d3bb-248">失敗</span><span class="sxs-lookup"><span data-stu-id="2d3bb-248">Fail</span></span> </td><td> <span data-ttu-id="2d3bb-249">コンテンツが非常に近い場所に表示されます (通常は &lt; 1.25 m、またはより &lt; 詳細な監視を必要とする固定のホログラムの場合は 50 cm です)。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-249">Content is presented too close (typically &lt;1.25 m, or &lt;50 cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="2d3bb-250">測定する方法</span><span class="sxs-lookup"><span data-stu-id="2d3bb-250">How to measure</span></span>

* <span data-ttu-id="2d3bb-251">通常、コンテンツは 2 m 離れている必要がありますが、1.25 を超える、または 5 m を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-251">Content should typically be 2 m away, but no closer than 1.25 or further than 5 m.</span></span>
* <span data-ttu-id="2d3bb-252">例外がいくつかある場合は、1 m からコンテンツをフェードアウトして、HoloLens クリッピングのレンダリング距離を85CM に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-252">With few exceptions, the HoloLens clipping render distance should be set to 85CM with fade out of content starting at 1 m.</span></span> <span data-ttu-id="2d3bb-253">コンテンツにアプローチし、クリッピング平面効果を確認します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="2d3bb-254">静止コンテンツは、50 cm を超えないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-254">Stationary content should not be closer than 50 cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="2d3bb-255">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-255">Recommendations</span></span>

* <span data-ttu-id="2d3bb-256">最適な表示距離が 2 m になるようにコンテンツをデザインします。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-256">Design content for the optimal viewing distance of 2 m.</span></span>
* <span data-ttu-id="2d3bb-257">クリッピングレンダリング距離を 85 cm に設定し、1 m からコンテンツをフェードアウトします。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-257">Set the clipping render distance to 85 cm with fade out of content starting at 1 m.</span></span>
* <span data-ttu-id="2d3bb-258">近くに表示する必要がある固定のホログラムの場合、クリッピング平面は 30 cm 以下であり、フェードアウトがクリッピング平面から少なくとも 10 cm 離れて開始される必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30 cm and fade out should start at least 10 cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="2d3bb-259">リソース</span><span class="sxs-lookup"><span data-stu-id="2d3bb-259">Resources</span></span>

* [<span data-ttu-id="2d3bb-260">レンダリング距離</span><span class="sxs-lookup"><span data-stu-id="2d3bb-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="2d3bb-261">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="2d3bb-261">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="2d3bb-262">スケールを試してみる</span><span class="sxs-lookup"><span data-stu-id="2d3bb-262">Experimenting with scale</span></span>](../../design/scale.md#experimenting-with-scale)
* [<span data-ttu-id="2d3bb-263">テキスト、推奨されるフォントサイズ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-263">Text, Recommended font size</span></span>](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="2d3bb-264">深度の切り替え</span><span class="sxs-lookup"><span data-stu-id="2d3bb-264">Depth switching</span></span>

<span data-ttu-id="2d3bb-265">快適な問題のゾーンが表示されているかどうかに関係なく、ユーザーに対して頻繁にまたは迅速に (ホログラムや実際のコンテンツを含む) 近接するオブジェクトを切り替えることによって、oculomotor と general 不快感が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="2d3bb-266">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d3bb-267"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-267"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="2d3bb-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2d3bb-269">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-269">✔️</span></span></td>
        <td><span data-ttu-id="2d3bb-270">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="2d3bb-271">品質基準</span><span class="sxs-lookup"><span data-stu-id="2d3bb-271">Quality criteria</span></span>

|  <span data-ttu-id="2d3bb-272">最高</span><span class="sxs-lookup"><span data-stu-id="2d3bb-272">Best</span></span>  |  <span data-ttu-id="2d3bb-273">あっ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-273">Meets</span></span> |  <span data-ttu-id="2d3bb-274">失敗</span><span class="sxs-lookup"><span data-stu-id="2d3bb-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="2d3bb-275">ユーザーが自然に refocus しないようにする、限定的または自然な深さの切り替え。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="2d3bb-276">[突然の深さ] スイッチこれはコアであり、アプリケーションエクスペリエンスに設計されています。または、予期しない実際のコンテンツによって発生した、突然の深さスイッチです。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="2d3bb-277">一貫した深さスイッチ、またはアプリエクスペリエンスの中核とならない、急激な深さの切り替え。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="2d3bb-278">測定する方法</span><span class="sxs-lookup"><span data-stu-id="2d3bb-278">How to measure</span></span>

* <span data-ttu-id="2d3bb-279">アプリケーションで、深さのフォーカスを一貫して変更する必要がある場合は、深さの切り替えに問題があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="2d3bb-280">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-280">Recommendations</span></span>

* <span data-ttu-id="2d3bb-281">一貫した中心面でプライマリコンテンツを保持し、安定化平面が焦点平面と一致していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="2d3bb-282">これにより、oculomotor の疲労と予期しないホログラムの動きが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="2d3bb-283">リソース</span><span class="sxs-lookup"><span data-stu-id="2d3bb-283">Resources</span></span>

* [<span data-ttu-id="2d3bb-284">レンダリング距離</span><span class="sxs-lookup"><span data-stu-id="2d3bb-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="2d3bb-285">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="2d3bb-285">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="2d3bb-286">空間サウンドの使用</span><span class="sxs-lookup"><span data-stu-id="2d3bb-286">Use of spatial sound</span></span>

<span data-ttu-id="2d3bb-287">Windows Mixed Reality では、音声エンジンは、方向、距離、および環境シミュレーションを使用して3D サウンドをシミュレートすることによって、混合した現実のエクスペリエンスの aural コンポーネントを提供します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="2d3bb-288">アプリケーションで空間サウンドを使用すると、開発者はユーザーに対して3次元空間 (球) にサウンドを convincingly ことができます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3-dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="2d3bb-289">これらのサウンドは、実際の物理オブジェクトまたはユーザーの周囲の混合現実ホログラムからのものであるように見えます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="2d3bb-290">空間サウンドは、mixed reality アプリケーションでの immersion、アクセシビリティ、UX の設計を行うための強力なツールです。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="2d3bb-291">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d3bb-292"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-292"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="2d3bb-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2d3bb-294">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-294">✔️</span></span></td>
        <td><span data-ttu-id="2d3bb-295">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="2d3bb-296">品質基準</span><span class="sxs-lookup"><span data-stu-id="2d3bb-296">Quality criteria</span></span>

|  <span data-ttu-id="2d3bb-297">最高</span><span class="sxs-lookup"><span data-stu-id="2d3bb-297">Best</span></span>  |  <span data-ttu-id="2d3bb-298">あっ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-298">Meets</span></span> |  <span data-ttu-id="2d3bb-299">失敗</span><span class="sxs-lookup"><span data-stu-id="2d3bb-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="2d3bb-300">サウンドは論理的には spatialized であり、UX は適切にサウンドを使用して、オブジェクトの検出とユーザーフィードバックを支援します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="2d3bb-301">サウンドは、自然で、オブジェクトに関連し、シナリオ全体で正規化されます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="2d3bb-302">空間オーディオは believability に対して適切に使用されますが、ユーザーのフィードバックと検索可能性を高めるための手段としては欠けています。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="2d3bb-303">サウンドが予期したとおりに spatialized されていないか、UX 内でユーザーを支援する音がありません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="2d3bb-304">または、空間オーディオがシナリオの設計で検討されていないか、使用されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="2d3bb-305">測定する方法</span><span class="sxs-lookup"><span data-stu-id="2d3bb-305">How to measure</span></span>

* <span data-ttu-id="2d3bb-306">一般に、関連するサウンドは、ターゲットホログラムから出力する必要があります (たとえば、holographic dog からほえサウンドが生成されます)。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="2d3bb-307">サウンドキューは、ユーザーが holographic フレーム外のアクションをフィードバックまたは認識するのを支援するために、UX 全体で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="2d3bb-308">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-308">Recommendations</span></span>

* <span data-ttu-id="2d3bb-309">オブジェクト検出とユーザーインターフェイスをサポートするには、空間オーディオを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="2d3bb-310">実際のサウンドは、合成や不自然な音よりも優れています。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="2d3bb-311">ほとんどのサウンドは spatialized にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="2d3bb-312">非表示の発信器は避けてください。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="2d3bb-313">空間マスクは避けてください。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="2d3bb-314">すべてのサウンドを正規化します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="2d3bb-315">リソース</span><span class="sxs-lookup"><span data-stu-id="2d3bb-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="2d3bb-316">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="2d3bb-316">Documentation</span></span>

* [<span data-ttu-id="2d3bb-317">立体音響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-317">Spatial sound</span></span>](../../design/spatial-sound.md)
* [<span data-ttu-id="2d3bb-318">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="2d3bb-318">Spatial sound design</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="2d3bb-319">Unity の立体音響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-319">Spatial sound in Unity</span></span>](../unity/spatial-sound-in-unity.md)
* [<span data-ttu-id="2d3bb-320">ケーススタディ、HoloTour の空間サウンド</span><span class="sxs-lookup"><span data-stu-id="2d3bb-320">Case study, Spatial sound for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="2d3bb-321">RoboRaid の空間サウンドを使用したケーススタディ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-321">Case study, Using spatial sound in RoboRaid</span></span>](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="2d3bb-322">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="2d3bb-322">Tools and tutorials</span></span>

* [<span data-ttu-id="2d3bb-323">Mixed Reality Toolkit-空間オーディオ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-323">Mixed Reality Toolkit - Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="2d3bb-324">Holographic frame (視界) の境界にフォーカス</span><span class="sxs-lookup"><span data-stu-id="2d3bb-324">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="2d3bb-325">適切に設計されたユーザーエクスペリエンスでは、ユーザーを中心とした仮想環境の有用なコンテキストを作成し、維持することができます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-325">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="2d3bb-326">視界の境界の影響を軽減するには、コンテンツのスケールとコンテキスト、空間オーディオの使用、ガイダンスシステム、ユーザーの位置をよく設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-326">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="2d3bb-327">そうすれば、ユーザーは快適なアプリエクスペリエンスを実現しながら、視界の境界によって損なわれることはなくなります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-327">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="2d3bb-328">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-328">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d3bb-329"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-329"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="2d3bb-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2d3bb-331">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-331">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="2d3bb-332">品質基準</span><span class="sxs-lookup"><span data-stu-id="2d3bb-332">Quality criteria</span></span>

|  <span data-ttu-id="2d3bb-333">最高</span><span class="sxs-lookup"><span data-stu-id="2d3bb-333">Best</span></span>  |  <span data-ttu-id="2d3bb-334">あっ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-334">Meets</span></span> |  <span data-ttu-id="2d3bb-335">失敗</span><span class="sxs-lookup"><span data-stu-id="2d3bb-335">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="2d3bb-336">ユーザーはコンテキストを失うことはなく、表示も快適です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-336">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="2d3bb-337">ラージオブジェクトのコンテキストに関するサポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-337">Context assistance is provided for large objects.</span></span> <span data-ttu-id="2d3bb-338">フレームの外部にあるオブジェクトについて、見つけやすさと表示に関するガイダンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-338">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="2d3bb-339">一般に、見やすさを向上させるには、ホログラムのモーションデザインとスケールが適しています。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-339">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="2d3bb-340">ユーザーはコンテキストを失うことはありませんが、限られた状況では追加のネックモーションが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-340">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="2d3bb-341">限られた状況では、ホログラムによって、ネックの動きが見られる垂直方向または水平方向のフレームが壊れることがあります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-341">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="2d3bb-342">ホログラムを表示するには、コンテキストや一貫したネック運動が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-342">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="2d3bb-343">大規模な holographic オブジェクトに関するコンテキストガイダンスはありません。オブジェクトを移動しても、発見可能なガイダンスがなくても、オブジェクトを簡単に失うことがあります。また、広いホログラムでは、通常のネックモーションが必要になります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-343">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="2d3bb-344">測定する方法</span><span class="sxs-lookup"><span data-stu-id="2d3bb-344">How to measure</span></span>

* <span data-ttu-id="2d3bb-345">境界でクリップされているため、(大きい) ホログラムのコンテキストが失われているか、認識されていません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-345">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="2d3bb-346">ホログラムの場所は、holographic フレームとの間で急速に移動される、要注意のダイレクタやコンテンツがないため、見つけるのが困難です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-346">Locations of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="2d3bb-347">シナリオでは、ネックの疲労を完全に確認するために、定期的かつ反復的に反復的に動きが必要です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-347">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="2d3bb-348">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-348">Recommendations</span></span>

* <span data-ttu-id="2d3bb-349">視界に合った小さなオブジェクトを使用して操作を開始し、視覚的な手掛かりを使用して大きなバージョンに移行します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-349">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="2d3bb-350">空間オーディオとアテンションダイレクタを使用すると、ユーザーが視界の外にあるコンテンツを見つけやすくなります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-350">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="2d3bb-351">可能な限り、視界を垂直方向にクリップするホログラムは避けてください。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-351">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="2d3bb-352">ユーザーにアプリ内のガイダンスを提供して、最適な表示場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-352">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="2d3bb-353">リソース</span><span class="sxs-lookup"><span data-stu-id="2d3bb-353">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="2d3bb-354">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="2d3bb-354">Documentation</span></span>

* [<span data-ttu-id="2d3bb-355">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="2d3bb-355">Holographic frame</span></span>](../../design/holographic-frame.md)
* [<span data-ttu-id="2d3bb-356">ケーススタディ、HoloStudio UI、相互作用設計学習</span><span class="sxs-lookup"><span data-stu-id="2d3bb-356">Case Study, HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="2d3bb-357">オブジェクトと環境のスケール</span><span class="sxs-lookup"><span data-stu-id="2d3bb-357">Scale of objects and environments</span></span>](../../design/scale.md)
* [<span data-ttu-id="2d3bb-358">カーソル、ビジュアルキュー</span><span class="sxs-lookup"><span data-stu-id="2d3bb-358">Cursors, Visual cues</span></span>](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="2d3bb-359">外部参照</span><span class="sxs-lookup"><span data-stu-id="2d3bb-359">External references</span></span>

* [<span data-ttu-id="2d3bb-360">視界に関する多くの ado</span><span class="sxs-lookup"><span data-stu-id="2d3bb-360">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="2d3bb-361">ユーザーの位置に反応するコンテンツ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-361">Content reacts to user position</span></span>

<span data-ttu-id="2d3bb-362">ホログラムは、"real" オブジェクトとほぼ同じ方法で、ユーザーの位置に反応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-362">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="2d3bb-363">注目すべき設計上の考慮事項は、ユーザーの位置が固定されていて、ユーザーの動きに合わせて調整できるとは限らない UI 要素です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-363">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="2d3bb-364">ユーザーの位置に適切に適合するようにアプリを設計すると、believable エクスペリエンスが向上し、使いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-364">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="2d3bb-365">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-365">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d3bb-366"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-366"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="2d3bb-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2d3bb-368">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-368">✔️</span></span></td>
        <td><span data-ttu-id="2d3bb-369">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-369">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="2d3bb-370">品質基準</span><span class="sxs-lookup"><span data-stu-id="2d3bb-370">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="2d3bb-371">最高</span><span class="sxs-lookup"><span data-stu-id="2d3bb-371">Best</span></span> </td><td> <span data-ttu-id="2d3bb-372">コンテンツと UI はユーザーの位置に適合するため、ユーザーは、予期されるユーザー移動の範囲内でコンテンツと自然に対話できます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-372">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2d3bb-373">あっ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-373">Meets</span></span> </td><td> <span data-ttu-id="2d3bb-374">UI はユーザーの位置に適合しますが、ユーザーが位置を調整する必要があるキーコンテンツのビューが妨げられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-374">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="2d3bb-375">失敗</span><span class="sxs-lookup"><span data-stu-id="2d3bb-375">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="2d3bb-376">UI 要素は移動中に失われるかロックされ、ユーザーはコントロールを自然に返す (または検索する) ことができません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-376">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="2d3bb-377">UI 要素は、プライマリコンテンツのビューを制限します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-377">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="2d3bb-378">UI の移動は、特に <a href="../../design/billboarding-and-tag-along.md">タグに沿っ</a> た ui 要素によって、距離や勢いを表示するためには最適化されていません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-378">UI movement isn't optimized for viewing distance and momentum particularly with <a href="../../design/billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="2d3bb-379">測定する方法</span><span class="sxs-lookup"><span data-stu-id="2d3bb-379">How to measure</span></span>

* <span data-ttu-id="2d3bb-380">すべての測定値は、シナリオの妥当な範囲内で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-380">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="2d3bb-381">ユーザーの移動は変化しますが、ユーザーの操作を極端に行うことなくアプリにトリックをかけることは避けてください。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-381">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="2d3bb-382">UI 要素の場合、ユーザーの移動に関係なく、関連するコントロールを使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-382">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="2d3bb-383">たとえば、ユーザーが zoom を使用して3D マップを表示しているときに、場所に関係なく、ユーザーがズームコントロールをすぐに使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-383">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="2d3bb-384">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-384">Recommendations</span></span>

* <span data-ttu-id="2d3bb-385">ユーザーはカメラで、動きを制御します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-385">The user is the camera and they control the movement.</span></span> <span data-ttu-id="2d3bb-386">これらのドライブを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-386">Let them drive.</span></span>
* <span data-ttu-id="2d3bb-387">テキストと menuing システムの billboarding を検討してください。これは、ユーザーが移動した場合に、ワールドロックまたは非表示になります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-387">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="2d3bb-388">ユーザーが前に何をしているかをユーザーが確認できるようにしながら、ユーザーに従う必要があるコンテンツにはタグを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-388">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="2d3bb-389">リソース</span><span class="sxs-lookup"><span data-stu-id="2d3bb-389">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="2d3bb-390">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="2d3bb-390">Documentation</span></span>

* [<span data-ttu-id="2d3bb-391">操作の設計</span><span class="sxs-lookup"><span data-stu-id="2d3bb-391">Interaction design</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="2d3bb-392">色、光、素材</span><span class="sxs-lookup"><span data-stu-id="2d3bb-392">Color, light, and material</span></span>](../../design/color-light-and-materials.md)
* [<span data-ttu-id="2d3bb-393">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="2d3bb-393">Billboarding and tag-along</span></span>](../../design/billboarding-and-tag-along.md)
* [<span data-ttu-id="2d3bb-394">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="2d3bb-394">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="2d3bb-395">自発運動とユーザー移動</span><span class="sxs-lookup"><span data-stu-id="2d3bb-395">Self-motion and user locomotion</span></span>](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a><span data-ttu-id="2d3bb-396">入力の相互作用のわかりやすさ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-396">Input interaction clarity</span></span>

<span data-ttu-id="2d3bb-397">入力の相互作用の明確さは、アプリのユーザビリティにとって重要であり、入力の一貫性、approachability、相互作用メソッドの発見性などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-397">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="2d3bb-398">ユーザーは、relearning なしでプラットフォーム全体の共通の対話を使用できます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-398">User can use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="2d3bb-399">アプリにカスタム入力がある場合は、それを明確に伝えることができます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-399">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="2d3bb-400">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-400">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d3bb-401"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-401"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="2d3bb-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2d3bb-403">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-403">✔️</span></span></td>
        <td><span data-ttu-id="2d3bb-404">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-404">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="2d3bb-405">品質基準</span><span class="sxs-lookup"><span data-stu-id="2d3bb-405">Quality criteria</span></span>

|  <span data-ttu-id="2d3bb-406">最高</span><span class="sxs-lookup"><span data-stu-id="2d3bb-406">Best</span></span>  |  <span data-ttu-id="2d3bb-407">あっ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-407">Meets</span></span> |  <span data-ttu-id="2d3bb-408">失敗</span><span class="sxs-lookup"><span data-stu-id="2d3bb-408">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="2d3bb-409">入力の相互作用メソッドは、Windows Mixed Reality に用意されている [ガイダンス](../../design/interaction-fundamentals.md)と一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-409">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](../../design/interaction-fundamentals.md).</span></span> <span data-ttu-id="2d3bb-410">任意のカスタム入力を標準入力と重複させることはできません (標準の相互作用を使用する必要があります)。また、ユーザーに明確に通知してデモンストレーションする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-410">Any custom input shouldn't be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="2d3bb-411">"最適" に似ていますが、カスタム入力は標準の入力方式では冗長です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-411">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="2d3bb-412">ユーザーは引き続き、アプリのエクスペリエンスの目標と進行状況を達成できます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-412">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="2d3bb-413">入力方法またはボタンのマッピングを理解するのが困難です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-413">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="2d3bb-414">入力は大幅にカスタマイズされており、標準入力、命令なし、または疲労や快適な問題を引き起こす可能性がありません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-414">Input is heavily customized, doesn't support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="2d3bb-415">測定する方法</span><span class="sxs-lookup"><span data-stu-id="2d3bb-415">How to measure</span></span>

* <span data-ttu-id="2d3bb-416">アプリでは、一貫 [した標準の入力方法が使用されます。](../../design/interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="2d3bb-416">The app uses consistent [standard input methods.](../../design/interaction-fundamentals.md)</span></span>
* <span data-ttu-id="2d3bb-417">アプリにカスタム入力がある場合は、次の方法で明確に伝達されます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-417">If the app has custom input, it's clearly communicated through:</span></span>
* <span data-ttu-id="2d3bb-418">最初の実行エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="2d3bb-418">First-run experience</span></span>
* <span data-ttu-id="2d3bb-419">入門画面</span><span class="sxs-lookup"><span data-stu-id="2d3bb-419">Introductory screens</span></span>
* <span data-ttu-id="2d3bb-420">ツールヒント</span><span class="sxs-lookup"><span data-stu-id="2d3bb-420">Tooltips</span></span>
* <span data-ttu-id="2d3bb-421">ハンド コーチ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-421">Hand coach</span></span>
* <span data-ttu-id="2d3bb-422">ヘルプセクション</span><span class="sxs-lookup"><span data-stu-id="2d3bb-422">Help section</span></span>
* <span data-ttu-id="2d3bb-423">ボイス オーバー</span><span class="sxs-lookup"><span data-stu-id="2d3bb-423">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="2d3bb-424">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-424">Recommendations</span></span>

* <span data-ttu-id="2d3bb-425">可能な場合は常に標準の入力方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-425">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="2d3bb-426">標準以外の入力方法については、デモ、チュートリアル、およびツールヒントを提供します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-426">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="2d3bb-427">アプリ全体で一貫した相互作用モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-427">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="2d3bb-428">リソース</span><span class="sxs-lookup"><span data-stu-id="2d3bb-428">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="2d3bb-429">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="2d3bb-429">Documentation</span></span>

* [<span data-ttu-id="2d3bb-430">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="2d3bb-430">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="2d3bb-431">対話型オブジェクト</span><span class="sxs-lookup"><span data-stu-id="2d3bb-431">Interactable objects</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="2d3bb-432">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="2d3bb-432">Head-gaze and dwell</span></span>](../../design/gaze-and-dwell.md)
* [<span data-ttu-id="2d3bb-433">カーソル</span><span class="sxs-lookup"><span data-stu-id="2d3bb-433">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="2d3bb-434">快適で見つめ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-434">Comfort and gaze</span></span>](../../design/comfort.md#gaze-direction)
* [<span data-ttu-id="2d3bb-435">音声入力</span><span class="sxs-lookup"><span data-stu-id="2d3bb-435">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="2d3bb-436">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="2d3bb-436">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="2d3bb-437">Unity 用入力移植ガイド</span><span class="sxs-lookup"><span data-stu-id="2d3bb-437">Input porting guide for Unity</span></span>](../porting-apps/input-porting-guide-for-unity.md)
* [<span data-ttu-id="2d3bb-438">Unity でのキーボード入力</span><span class="sxs-lookup"><span data-stu-id="2d3bb-438">Keyboard input in Unity</span></span>](../unity/keyboard-input-in-unity.md)
* [<span data-ttu-id="2d3bb-439">Unity の視線入力</span><span class="sxs-lookup"><span data-stu-id="2d3bb-439">Gaze in Unity</span></span>](../unity/gaze-in-unity.md)
* [<span data-ttu-id="2d3bb-440">Unity のモーションコントローラー</span><span class="sxs-lookup"><span data-stu-id="2d3bb-440">Motion controllers in Unity</span></span>](../unity/motion-controllers-in-unity.md)
* [<span data-ttu-id="2d3bb-441">Unity でのジェスチャ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-441">Gestures in Unity</span></span>](../unity/gestures-in-unity.md)
* [<span data-ttu-id="2d3bb-442">Unity の音声入力</span><span class="sxs-lookup"><span data-stu-id="2d3bb-442">Voice input in Unity</span></span>](../unity/voice-input-in-unity.md)
* [<span data-ttu-id="2d3bb-443">DirectX でのキーボード、マウス、およびコントローラー入力</span><span class="sxs-lookup"><span data-stu-id="2d3bb-443">Keyboard, mouse, and controller input in DirectX</span></span>](./keyboard-mouse-and-controller-input-in-directx.md)
* [<span data-ttu-id="2d3bb-444">DirectX でのヘッド視線入力とアイ視線入力</span><span class="sxs-lookup"><span data-stu-id="2d3bb-444">Head and eye gaze in DirectX</span></span>](../native/gaze-in-directx.md)
* [<span data-ttu-id="2d3bb-445">DirectX での手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="2d3bb-445">Hands and motion controllers in DirectX</span></span>](../native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="2d3bb-446">DirectX の音声入力</span><span class="sxs-lookup"><span data-stu-id="2d3bb-446">Voice input in DirectX</span></span>](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="2d3bb-447">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="2d3bb-447">Tools and tutorials</span></span>

* [<span data-ttu-id="2d3bb-448">ケーススタディ: よりパーソナルコンピューティングの追求</span><span class="sxs-lookup"><span data-stu-id="2d3bb-448">Case study: The pursuit of more personal computing</span></span>](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="2d3bb-449">キャストスタディ: HoloStudio UI と相互作用設計学習</span><span class="sxs-lookup"><span data-stu-id="2d3bb-449">Cast study: HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="2d3bb-450">サンプルアプリ: 要素の周期テーブル</span><span class="sxs-lookup"><span data-stu-id="2d3bb-450">Sample app: Periodic table of the elements</span></span>](../unity/periodic-table-of-the-elements.md)
* [<span data-ttu-id="2d3bb-451">サンプルアプリ: 旧暦モジュール</span><span class="sxs-lookup"><span data-stu-id="2d3bb-451">Sample app: Lunar module</span></span>](../unity/lunar-module.md)

## <a name="interactable-objects"></a><span data-ttu-id="2d3bb-452">対話型オブジェクト</span><span class="sxs-lookup"><span data-stu-id="2d3bb-452">Interactable objects</span></span>

<span data-ttu-id="2d3bb-453">ボタンは、2D 抽象ワールドでイベントをトリガーするために使用される比喩です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-453">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="2d3bb-454">3次元混合の現実世界では、この抽象化の世界に限定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-454">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="2d3bb-455">イベントをトリガーする対話型オブジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-455">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="2d3bb-456">対話型オブジェクトは、テーブル上のコーヒーカップの任意のものとして、無線でバルーンに表示できます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-456">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="2d3bb-457">フォームに関係なく、対話型オブジェクトは、ユーザーがビジュアルおよびオーディオキューを使用して明確に認識できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-457">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="2d3bb-458">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-458">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d3bb-459"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-459"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="2d3bb-460"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-460"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2d3bb-461">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-461">✔️</span></span></td>
        <td><span data-ttu-id="2d3bb-462">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-462">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="2d3bb-463">品質基準</span><span class="sxs-lookup"><span data-stu-id="2d3bb-463">Quality criteria</span></span>

|  <span data-ttu-id="2d3bb-464">最高</span><span class="sxs-lookup"><span data-stu-id="2d3bb-464">Best</span></span>  |  <span data-ttu-id="2d3bb-465">あっ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-465">Meets</span></span> |  <span data-ttu-id="2d3bb-466">失敗</span><span class="sxs-lookup"><span data-stu-id="2d3bb-466">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="2d3bb-467">フォームに関係なく、対話型オブジェクトは、アイドル、ターゲット、および選択された3つの状態にわたって、ビジュアルおよびオーディオのキューを介して認識されます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-467">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="2d3bb-468">"ご覧のように、エクスペリエンス全体で一貫して使用されています。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-468">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="2d3bb-469">オブジェクトは、フリーターゲットのエラーを許容するようにスケーリングおよび配布されます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-469">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="2d3bb-470">ユーザーは、オーディオまたはビジュアルフィードバックによってオブジェクトを対話型として認識し、オブジェクトをターゲットにしてアクティブ化することができます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-470">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="2d3bb-471">ビジュアルまたはオーディオのキューがない場合、ユーザーは対話型オブジェクトを認識できません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-471">Given no visual or audio cues, user can't recognize an interactable object.</span></span> <span data-ttu-id="2d3bb-472">オブジェクトのスケールやオブジェクト間の距離により、相互作用がエラーを起こしやすくなります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-472">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="2d3bb-473">測定する方法</span><span class="sxs-lookup"><span data-stu-id="2d3bb-473">How to measure</span></span>

* <span data-ttu-id="2d3bb-474">対話型オブジェクトは ' 対話型 ' として認識されます。ボタン、メニュー、アプリ固有のコンテンツを含む。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-474">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app-specific content.</span></span> <span data-ttu-id="2d3bb-475">経験則として、対話型オブジェクトを対象とする場合は、ビジュアルとオーディオの手掛かりが必要です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-475">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="2d3bb-476">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-476">Recommendations</span></span>

* <span data-ttu-id="2d3bb-477">対話のためにビジュアルとオーディオフィードバックを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-477">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="2d3bb-478">視覚的なフィードバックは、入力状態 (アイドル、ターゲット、選択) ごとに区別される必要があります</span><span class="sxs-lookup"><span data-stu-id="2d3bb-478">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="2d3bb-479">対話型オブジェクトは、エラーをターゲットにするためにスケーリングして配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-479">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="2d3bb-480">グループ化された対話型オブジェクト (メニューバーやリストなど) には、ターゲットを設定するための適切なスペースが必要です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-480">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="2d3bb-481">音声コマンドをサポートするボタンとメニューでは、command キーワードにテキストラベルを指定する必要があります (「参照してください」と言います)。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-481">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="2d3bb-482">リソース</span><span class="sxs-lookup"><span data-stu-id="2d3bb-482">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="2d3bb-483">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="2d3bb-483">Documentation</span></span>

* [<span data-ttu-id="2d3bb-484">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="2d3bb-484">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="2d3bb-485">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="2d3bb-485">Text in Unity</span></span>](../unity/text-in-unity.md)
* [<span data-ttu-id="2d3bb-486">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="2d3bb-486">Bounding box and App bar</span></span>](../../design/app-bar-and-bounding-box.md)
* [<span data-ttu-id="2d3bb-487">音声入力</span><span class="sxs-lookup"><span data-stu-id="2d3bb-487">Voice input</span></span>](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="2d3bb-488">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="2d3bb-488">Tools and tutorials</span></span>

* [<span data-ttu-id="2d3bb-489">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="2d3bb-489">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="2d3bb-490">部屋のスキャン</span><span class="sxs-lookup"><span data-stu-id="2d3bb-490">Room scanning</span></span>

<span data-ttu-id="2d3bb-491">空間マッピングデータを必要とするアプリは、ユーザーがデバイスをアクティブにして環境を探索するときに、このデータを時間の経過と共に自動的に収集するためにデバイスに依存します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-491">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="2d3bb-492">このデータの完全性と品質は、ユーザーが実行した探索の量、探索から経過した時間、家具やドアなどのオブジェクトが領域をスキャンした後に移動されたかどうかなど、さまざまな要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-492">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="2d3bb-493">多くのアプリは、エクスペリエンスの開始時に空間マッピングデータを分析して、ユーザーが空間マップの完全性と品質を向上させるために追加の手順を実行する必要があるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-493">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="2d3bb-494">ユーザーが環境をスキャンする必要がある場合は、スキャンの実行中に [ガイダンスのクリア] を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-494">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="2d3bb-495">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-495">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d3bb-496"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-496"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="2d3bb-497"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-497"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2d3bb-498">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-498">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="2d3bb-499">品質基準</span><span class="sxs-lookup"><span data-stu-id="2d3bb-499">Quality criteria</span></span>

|  <span data-ttu-id="2d3bb-500">最高</span><span class="sxs-lookup"><span data-stu-id="2d3bb-500">Best</span></span>  |  <span data-ttu-id="2d3bb-501">あっ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-501">Meets</span></span> |  <span data-ttu-id="2d3bb-502">失敗</span><span class="sxs-lookup"><span data-stu-id="2d3bb-502">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="2d3bb-503">ユーザーによるスキャンを通知する空間メッシュの視覚化が進行中です。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-503">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="2d3bb-504">ユーザーは、何を行うか、およびスキャンが開始および停止するタイミングを明確に把握します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-504">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="2d3bb-505">空間メッシュの視覚化が提供されていますが、ユーザーが何をしているかを明確に把握しておらず、進行状況に関する情報が提供されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-505">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="2d3bb-506">メッシュの視覚化がありません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-506">No visualization of mesh.</span></span> <span data-ttu-id="2d3bb-507">検索する場所、またはスキャンの開始/停止時に関するガイダンス情報はユーザーに提供されません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-507">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="2d3bb-508">測定する方法</span><span class="sxs-lookup"><span data-stu-id="2d3bb-508">How to measure</span></span>

* <span data-ttu-id="2d3bb-509">必要な部屋のスキャン中に、検索する場所と、スキャンを開始および停止するタイミングを示すビジュアルおよびオーディオのガイダンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-509">During a required room scan, visual and audio guidance are provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="2d3bb-510">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-510">Recommendations</span></span>

* <span data-ttu-id="2d3bb-511">ユーザーの近くにあるユーザーの合計ボリュームがエクスペリエンスの一部である必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-511">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="2d3bb-512">スキャンが開始され、進行状況インジケーターなどの停止時に通信します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-512">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="2d3bb-513">スキャン中にメッシュの視覚エフェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-513">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="2d3bb-514">ユーザーが部屋を見たり、移動したりすることを奨励するために、ビジュアルとオーディオの手掛かりを提供します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-514">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="2d3bb-515">データを改善するための場所をユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-515">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="2d3bb-516">多くの場合、必要なスキャン品質を得るために、ユーザーに対して実行する必要があること (たとえば、天井、家具を見てみてください) を伝えることが最適な場合があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-516">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="2d3bb-517">リソース</span><span class="sxs-lookup"><span data-stu-id="2d3bb-517">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="2d3bb-518">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="2d3bb-518">Documentation</span></span>

* [<span data-ttu-id="2d3bb-519">部屋のスキャンの可視化</span><span class="sxs-lookup"><span data-stu-id="2d3bb-519">Room scan visualization</span></span>](../../design/room-scan-visualization.md)
* [<span data-ttu-id="2d3bb-520">ケーススタディ: HoloLens の空間マッピング機能の拡張</span><span class="sxs-lookup"><span data-stu-id="2d3bb-520">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="2d3bb-521">ケーススタディ: HoloTour の空間サウンド設計</span><span class="sxs-lookup"><span data-stu-id="2d3bb-521">Case study: Spatial sound design for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="2d3bb-522">ケーススタディ: フラグメントでのイマーシブエクスペリエンスの作成</span><span class="sxs-lookup"><span data-stu-id="2d3bb-522">Case study: Creating an immersive experience in Fragments</span></span>](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="2d3bb-523">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="2d3bb-523">Tools and tutorials</span></span>

* [<span data-ttu-id="2d3bb-524">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="2d3bb-524">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="2d3bb-525">方向インジケーター</span><span class="sxs-lookup"><span data-stu-id="2d3bb-525">Directional indicators</span></span>

<span data-ttu-id="2d3bb-526">Mixed reality アプリでは、コンテンツは、実際のオブジェクトによって view または occluded のフィールドの外部にある場合があります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-526">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="2d3bb-527">適切にデザインされたアプリを使用すると、ユーザーが非表示のコンテンツを簡単に見つけられるようになります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-527">A well-designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="2d3bb-528">ディレクショナルインジケーターは、ユーザーに重要なコンテンツを通知し、ユーザーの位置を基準にしてコンテンツに関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-528">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="2d3bb-529">非表示コンテンツに関するガイダンスは、サウンドの発信器、方向矢印、または直接視覚的な合図の形式になります。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-529">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="2d3bb-530">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-530">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d3bb-531"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-531"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="2d3bb-532"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-532"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2d3bb-533">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-533">✔️</span></span></td>
        <td><span data-ttu-id="2d3bb-534">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-534">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="2d3bb-535">品質基準</span><span class="sxs-lookup"><span data-stu-id="2d3bb-535">Quality criteria</span></span>

|  <span data-ttu-id="2d3bb-536">最高</span><span class="sxs-lookup"><span data-stu-id="2d3bb-536">Best</span></span>  |  <span data-ttu-id="2d3bb-537">あっ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-537">Meets</span></span> |  <span data-ttu-id="2d3bb-538">失敗</span><span class="sxs-lookup"><span data-stu-id="2d3bb-538">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="2d3bb-539">ビジュアルおよびオーディオキューは、ビューのフィールドの外部にある関連するコンテンツをユーザーに直接案内します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-539">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="2d3bb-540">コンテンツの一般的な方向にユーザーを示す矢印またはインジケーター。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-540">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="2d3bb-541">関連するコンテンツはビューのフィールドの外部にあり、ユーザーには不適切または場所のガイダンスは提供されません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-541">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="2d3bb-542">測定する方法</span><span class="sxs-lookup"><span data-stu-id="2d3bb-542">How to measure</span></span>

* <span data-ttu-id="2d3bb-543">ビューの [ユーザー] フィールド以外の関連するコンテンツは、ビジュアルまたはオーディオキューを使用して検出できます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-543">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="2d3bb-544">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-544">Recommendations</span></span>

* <span data-ttu-id="2d3bb-545">関連するコンテンツがユーザーのビューの外部にある場合は、方向インジケーターとオーディオキューを使用して、ユーザーをコンテンツに案内します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-545">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="2d3bb-546">多くの場合、方向性のある矢印よりも直接の視覚的なガイドをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-546">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="2d3bb-547">方向インジケーターをカーソルに組み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-547">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="2d3bb-548">リソース</span><span class="sxs-lookup"><span data-stu-id="2d3bb-548">Resources</span></span>

* [<span data-ttu-id="2d3bb-549">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="2d3bb-549">Holographic frame</span></span>](../../design/holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="2d3bb-550">データの読み込み</span><span class="sxs-lookup"><span data-stu-id="2d3bb-550">Data loading</span></span>

<span data-ttu-id="2d3bb-551">プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-551">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="2d3bb-552">これは、進行状況インジケーターが表示されているときにユーザーがアプリと対話できないことを意味し、待機時間がどの程度かかるかを示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-552">It can mean that the user can't interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="2d3bb-553">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="2d3bb-553">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="2d3bb-554"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-554"><a href="/hololens/hololens1-hardware"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="2d3bb-555"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="2d3bb-555"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="2d3bb-556">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-556">✔️</span></span></td>
        <td><span data-ttu-id="2d3bb-557">✔️</span><span class="sxs-lookup"><span data-stu-id="2d3bb-557">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="2d3bb-558">品質基準</span><span class="sxs-lookup"><span data-stu-id="2d3bb-558">Quality criteria</span></span>

|  <span data-ttu-id="2d3bb-559">最高</span><span class="sxs-lookup"><span data-stu-id="2d3bb-559">Best</span></span>  |  <span data-ttu-id="2d3bb-560">あっ</span><span class="sxs-lookup"><span data-stu-id="2d3bb-560">Meets</span></span> |  <span data-ttu-id="2d3bb-561">失敗</span><span class="sxs-lookup"><span data-stu-id="2d3bb-561">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="2d3bb-562">データの読み込み中または処理中の進行状況を示す進行状況バーまたはリングの形式でのアニメーション化されたビジュアルインジケーター。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-562">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="2d3bb-563">ビジュアルインジケーターは、待機時間の長さに関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-563">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="2d3bb-564">ユーザーには、データの読み込みが進行中であることが通知されますが、待機時間を示すことはできません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-564">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="2d3bb-565">タスクのデータ読み込みまたはプロセスインジケーターが5秒より長くかかっていません。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-565">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="2d3bb-566">測定する方法</span><span class="sxs-lookup"><span data-stu-id="2d3bb-566">How to measure</span></span>

* <span data-ttu-id="2d3bb-567">データの読み込み中に、5秒を超える空の状態がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-567">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="2d3bb-568">推奨事項</span><span class="sxs-lookup"><span data-stu-id="2d3bb-568">Recommendations</span></span>

* <span data-ttu-id="2d3bb-569">ユーザーがこのアプリを停止またはクラッシュしていると認識した場合に、進行状況を示すデータ読み込みのアニメーターを提供します。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-569">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="2d3bb-570">目安として合理的なのは、5秒以上かかる可能性のある "読み込み" アクティビティです。</span><span class="sxs-lookup"><span data-stu-id="2d3bb-570">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="2d3bb-571">リソース</span><span class="sxs-lookup"><span data-stu-id="2d3bb-571">Resources</span></span>

* [<span data-ttu-id="2d3bb-572">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="2d3bb-572">Displaying progress</span></span>](../../design/progress.md)