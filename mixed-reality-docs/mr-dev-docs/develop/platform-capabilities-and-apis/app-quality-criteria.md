---
title: アプリの品質基準
description: このドキュメントでは、mixed reality アプリの品質に影響する上位の要因について説明します。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: アプリ品質基準、mixed reality、mixed reality アプリ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: 788a2e8ac1a364f8c33e3895992fd99fa220a26a
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530289"
---
# <a name="app-quality-criteria"></a><span data-ttu-id="bcd27-104">アプリの品質基準</span><span class="sxs-lookup"><span data-stu-id="bcd27-104">App quality criteria</span></span>

<span data-ttu-id="bcd27-105">このドキュメントでは、mixed reality アプリの品質に影響する上位の要因について説明します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-105">This document describes the top factors impacting the quality of mixed reality apps.</span></span> <span data-ttu-id="bcd27-106">各要素について、次の情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-106">For each factor, the following information is provided</span></span>
* <span data-ttu-id="bcd27-107">[概要] –品質要因と重要な理由について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-107">Overview – a brief description of the quality factor and why it's important.</span></span>
* <span data-ttu-id="bcd27-108">デバイスへの影響-どの種類のウィンドウに Mixed Reality デバイスが影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-108">Device impact - which type of Window Mixed Reality device is affected.</span></span>
* <span data-ttu-id="bcd27-109">品質基準–品質要因を評価する方法。</span><span class="sxs-lookup"><span data-stu-id="bcd27-109">Quality criteria – how to evaluate the quality factor.</span></span>
* <span data-ttu-id="bcd27-110">方法: 問題を測定 (または経験) する方法。</span><span class="sxs-lookup"><span data-stu-id="bcd27-110">How to measure – methods to measure (or experience) the issue.</span></span>
* <span data-ttu-id="bcd27-111">推奨事項–より優れたユーザーエクスペリエンスを提供するためのアプローチの概要です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-111">Recommendations – summary of approaches to provide a better user experience.</span></span>
* <span data-ttu-id="bcd27-112">リソース–優れたアプリエクスペリエンスを作成するのに役立つ、関連する開発者および設計リソース。</span><span class="sxs-lookup"><span data-stu-id="bcd27-112">Resources – relevant developer and design resources that are useful to create better app experiences.</span></span>

## <a name="frame-rate"></a><span data-ttu-id="bcd27-113">フレーム レート</span><span class="sxs-lookup"><span data-stu-id="bcd27-113">Frame rate</span></span>

<span data-ttu-id="bcd27-114">フレームレートは、ホログラムの安定性とユーザーの快適さの第一柱です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-114">Frame rate is the first pillar of hologram stability and user comfort.</span></span> <span data-ttu-id="bcd27-115">推奨されるターゲットの下にあるフレームレートは、ホログラムがちらつくように見え、エクスペリエンスの believability に悪影響を及ぼし、目に見える疲労が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-115">Frame rate below the recommended targets can cause holograms to appear jittery, negatively impacting the believability of the experience and potentially causing eye fatigue.</span></span> <span data-ttu-id="bcd27-116">Windows Mixed Reality のイマーシブヘッドセットでのエクスペリエンスの目標フレームレートは、サポートしている Windows Mixed Reality 互換 Pc に応じて、60 Hz または 90 Hz です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-116">The target frame rate for your experience on Windows Mixed Reality immersive headsets is either 60 Hz or 90 Hz depending on which Windows Mixed Reality Compatible PCs you're supporting.</span></span> <span data-ttu-id="bcd27-117">HoloLens の場合、ターゲットフレームレートは 60 Hz です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-117">For HoloLens, the target frame rate is 60 Hz.</span></span>

### <a name="device-impact"></a><span data-ttu-id="bcd27-118">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="bcd27-118">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bcd27-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-119"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bcd27-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-120"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bcd27-121">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-121">✔️</span></span></td>
        <td><span data-ttu-id="bcd27-122">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-122">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="bcd27-123">品質基準</span><span class="sxs-lookup"><span data-stu-id="bcd27-123">Quality criteria</span></span>

|  <span data-ttu-id="bcd27-124">最高</span><span class="sxs-lookup"><span data-stu-id="bcd27-124">Best</span></span>  |  <span data-ttu-id="bcd27-125">あっ</span><span class="sxs-lookup"><span data-stu-id="bcd27-125">Meets</span></span> |  <span data-ttu-id="bcd27-126">失敗</span><span class="sxs-lookup"><span data-stu-id="bcd27-126">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="bcd27-127">アプリは、ターゲットデバイスの1秒あたりのフレーム数 (FPS) の目標を一貫して満たしています: HoloLens で 60 fps。ウルトラ Pc で 90 fps。メインストリーム Pc では 60 fps です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-127">The app consistently meets frames per second (FPS) goal for target device: 60 fps on HoloLens; 90 fps on Ultra PCs; and 60 fps on mainstream PCs.</span></span> | <span data-ttu-id="bcd27-128">アプリは、コアエクスペリエンスを妨げるすることなく断続的にフレームが削除されるか、または FPS は望ましい目標よりも一貫して低くなりますが、アプリのエクスペリエンスを妨げることはありません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-128">The app has intermittent frame drops not impeding the core experience, or FPS is consistently lower than desired goal but doesn’t impede the app experience.</span></span> | <span data-ttu-id="bcd27-129">アプリでは、平均で10秒以内にフレームレートが低下しています。</span><span class="sxs-lookup"><span data-stu-id="bcd27-129">The app is experiencing a drop in frame rate on average every 10 seconds or less.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="bcd27-130">測定する方法</span><span class="sxs-lookup"><span data-stu-id="bcd27-130">How to measure</span></span>

* <span data-ttu-id="bcd27-131">リアルタイムのフレームレートグラフは、 [Windows デバイスポータル](using-the-windows-device-portal.md#system-performance) によって "システムパフォーマンス" によって提供されます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-131">A real-time frame rate graph is provided through by the [Windows Device Portal](using-the-windows-device-portal.md#system-performance) under "System Performance".</span></span>
* <span data-ttu-id="bcd27-132">開発用デバッグでは、フレームレート診断カウンターをアプリに追加します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-132">For development debugging, add a frame rate diagnostic counter into the app.</span></span> <span data-ttu-id="bcd27-133">「サンプルカウンターのリソース」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bcd27-133">See Resources for a sample counter.</span></span>
* <span data-ttu-id="bcd27-134">フレームレートが低下するのは、アプリの実行中に、ヘッドを左右に移動して、デバイスで発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-134">Frame rate drops can be experienced in device while the app is running by moving your head from side to side.</span></span> <span data-ttu-id="bcd27-135">ホログラムが予期しないちらつきの動きを示している場合、フレームレートが低いか、安定性平面が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-135">If the hologram shows unexpected jittery movement, then low frame rate or the stability plane is likely the cause.</span></span>

### <a name="recommendations"></a><span data-ttu-id="bcd27-136">推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-136">Recommendations</span></span>

* <span data-ttu-id="bcd27-137">開発作業の開始時にフレームレートカウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-137">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="bcd27-138">フレームレートが低下した変更は、パフォーマンスバグとして評価され、適切に解決される必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-138">Changes that incur a drop in frame rate should be evaluated and appropriately resolved as a performance bug.</span></span>

### <a name="resources"></a><span data-ttu-id="bcd27-139">リソース</span><span class="sxs-lookup"><span data-stu-id="bcd27-139">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="bcd27-140">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="bcd27-140">Documentation</span></span>

* [<span data-ttu-id="bcd27-141">Mixed Reality のパフォーマンスについて</span><span class="sxs-lookup"><span data-stu-id="bcd27-141">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="bcd27-142">ホログラムの安定性とフレームレート</span><span class="sxs-lookup"><span data-stu-id="bcd27-142">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="bcd27-143">資産のパフォーマンスの予算</span><span class="sxs-lookup"><span data-stu-id="bcd27-143">Asset performance budget</span></span>](../../design/asset-creation-process.md)
* [<span data-ttu-id="bcd27-144">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-144">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="bcd27-145">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="bcd27-145">Tools and tutorials</span></span>

* [<span data-ttu-id="bcd27-146">混合 Reality ツールキット、FPS カウンターの表示</span><span class="sxs-lookup"><span data-stu-id="bcd27-146">Mixed Reality Toolkit, FPS counter display</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [<span data-ttu-id="bcd27-147">混合現実ツールキット、シェーダー</span><span class="sxs-lookup"><span data-stu-id="bcd27-147">Mixed Reality Toolkit, Shaders</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a><span data-ttu-id="bcd27-148">外部参照</span><span class="sxs-lookup"><span data-stu-id="bcd27-148">External references</span></span>

* [<span data-ttu-id="bcd27-149">Unity, モバイルアプリケーションの最適化</span><span class="sxs-lookup"><span data-stu-id="bcd27-149">Unity, Optimizing mobile applications</span></span>](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a><span data-ttu-id="bcd27-150">ホログラムの安定性</span><span class="sxs-lookup"><span data-stu-id="bcd27-150">Hologram stability</span></span>

<span data-ttu-id="bcd27-151">安定したホログラムは、アプリの使いやすさと believability を向上させ、ユーザーにより快適な表示エクスペリエンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-151">Stable holograms will increase the usability and believability of your app, and create a more comfortable viewing experience for the user.</span></span> <span data-ttu-id="bcd27-152">ホログラムの安定性の質は、優れたアプリ開発と、その環境を理解 (追跡) するデバイスの機能によって得られます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-152">The quality of hologram stability is a result of good app development and the device's ability to understand (track) its environment.</span></span> <span data-ttu-id="bcd27-153">フレームレートは安定性の最初の柱ですが、その他の要因は次のような安定性に影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-153">While frame rate is the first pillar of stability, other factors can impact stability including:</span></span>

* <span data-ttu-id="bcd27-154">安定化平面の使用</span><span class="sxs-lookup"><span data-stu-id="bcd27-154">Use of the stabilization plane</span></span>
* <span data-ttu-id="bcd27-155">空間アンカーへの距離</span><span class="sxs-lookup"><span data-stu-id="bcd27-155">Distance to spatial anchors</span></span>
* <span data-ttu-id="bcd27-156">追跡</span><span class="sxs-lookup"><span data-stu-id="bcd27-156">Tracking</span></span>

### <a name="device-impact"></a><span data-ttu-id="bcd27-157">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="bcd27-157">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bcd27-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-158"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bcd27-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-159"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bcd27-160">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-160">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="bcd27-161">品質基準</span><span class="sxs-lookup"><span data-stu-id="bcd27-161">Quality criteria</span></span>

|  <span data-ttu-id="bcd27-162">最高</span><span class="sxs-lookup"><span data-stu-id="bcd27-162">Best</span></span>  |  <span data-ttu-id="bcd27-163">あっ</span><span class="sxs-lookup"><span data-stu-id="bcd27-163">Meets</span></span> |  <span data-ttu-id="bcd27-164">失敗</span><span class="sxs-lookup"><span data-stu-id="bcd27-164">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="bcd27-165">ホログラムは常に安定した状態で表示されます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-165">Holograms consistently appear stable.</span></span> | <span data-ttu-id="bcd27-166">セカンダリコンテンツは予期しない移動を示しています。または、予期しない移動はアプリ全体のエクスペリエンスを妨げることはありません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-166">Secondary content shows unexpected movement; or unexpected movement doesn't impede overall app experience.</span></span> | <span data-ttu-id="bcd27-167">フレーム内のプライマリコンテンツは、予期しない移動を示しています。</span><span class="sxs-lookup"><span data-stu-id="bcd27-167">Primary content in frame shows unexpected movement.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="bcd27-168">測定する方法</span><span class="sxs-lookup"><span data-stu-id="bcd27-168">How to measure</span></span>

<span data-ttu-id="bcd27-169">デバイスを装着し、エクスペリエンスを表示しています。</span><span class="sxs-lookup"><span data-stu-id="bcd27-169">While wearing the device and viewing the experience:</span></span>

* <span data-ttu-id="bcd27-170">ヘッドを左右に移動します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-170">Move your head from side to side.</span></span> <span data-ttu-id="bcd27-171">ホログラムが予期しない動きを示している場合、フレームレートが低いか、または安定平面が焦点平面に正しく配置されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-171">If the holograms show unexpected movement then low frame rate or improper alignment of the stability plane to the focal plane is the likely cause.</span></span>
* <span data-ttu-id="bcd27-172">ホログラムと環境内を移動し、スイム・ jumpiness などの動作を探します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-172">Move around the holograms and environment, look for behaviors such as swim and jumpiness.</span></span> <span data-ttu-id="bcd27-173">この種類のモーションは、デバイスが環境を追跡していない、または空間アンカーへの距離が原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-173">This type of motion is likely caused by the device not tracking the environment, or the distance to the spatial anchor.</span></span>
* <span data-ttu-id="bcd27-174">フレーム内に複数のホログラムがある場合は、さまざまな深度でのホログラムの動作を観察し、揺れるが表示されている場合は、安定化平面によって発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-174">If large or multiple holograms are in the frame, observe hologram behavior at various depths while moving your head position from side to side, if shakiness appears this is likely caused by the stabilization plane.</span></span>

### <a name="recommendations"></a><span data-ttu-id="bcd27-175">推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-175">Recommendations</span></span>

* <span data-ttu-id="bcd27-176">開発作業の開始時にフレームレートカウンターを追加します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-176">Add a frame rate counter at the beginning of the development work.</span></span>
* <span data-ttu-id="bcd27-177">安定化平面を使用します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-177">Use the stabilization plane.</span></span>
* <span data-ttu-id="bcd27-178">アンカーの3メートル以内に固定したホログラムを常にレンダリングします。</span><span class="sxs-lookup"><span data-stu-id="bcd27-178">Always render anchored holograms within 3 meters of their anchor.</span></span>
* <span data-ttu-id="bcd27-179">適切な追跡のために環境がセットアップされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-179">Make sure your environment is set up for proper tracking.</span></span>
* <span data-ttu-id="bcd27-180">フレーム内のさまざまな焦点深度レベルでホログラムを使用しないように、エクスペリエンスを設計します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-180">Design your experience to avoid holograms at various focal depth levels within the frame.</span></span>

### <a name="resources"></a><span data-ttu-id="bcd27-181">リソース</span><span class="sxs-lookup"><span data-stu-id="bcd27-181">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="bcd27-182">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="bcd27-182">Documentation</span></span>

* [<span data-ttu-id="bcd27-183">ホログラムの安定性とフレームレート</span><span class="sxs-lookup"><span data-stu-id="bcd27-183">Hologram stability and framerate</span></span>](hologram-stability.md#frame-rate)
* [<span data-ttu-id="bcd27-184">安定化平面を使用したケーススタディ</span><span class="sxs-lookup"><span data-stu-id="bcd27-184">Case study, Using the stabilization plane</span></span>](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [<span data-ttu-id="bcd27-185">Mixed Reality のパフォーマンスについて</span><span class="sxs-lookup"><span data-stu-id="bcd27-185">Understanding Performance for Mixed Reality</span></span>](understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="bcd27-186">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-186">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
* [<span data-ttu-id="bcd27-187">空間アンカー</span><span class="sxs-lookup"><span data-stu-id="bcd27-187">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="bcd27-188">追跡エラーの処理</span><span class="sxs-lookup"><span data-stu-id="bcd27-188">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="bcd27-189">静止フレーム (参照)</span><span class="sxs-lookup"><span data-stu-id="bcd27-189">Stationary frame of reference</span></span>](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="bcd27-190">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="bcd27-190">Tools and tutorials</span></span>

* [<span data-ttu-id="bcd27-191">MR コンパニオンキット、Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="bcd27-191">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a><span data-ttu-id="bcd27-192">実際のサーフェイス上のホログラムの位置</span><span class="sxs-lookup"><span data-stu-id="bcd27-192">Holograms position on real surfaces</span></span>

<span data-ttu-id="bcd27-193">物理的なオブジェクトを使用したホログラムの間違った配置 (相互に関係するように設計されている場合) は、ホログラムと現実世界の非共用体を明確に示しています。</span><span class="sxs-lookup"><span data-stu-id="bcd27-193">Misalignments of holograms with physical objects (if intended to be placed in relation to one another) are a clear indication of the non-union of holograms and real-world.</span></span> <span data-ttu-id="bcd27-194">配置の精度は、シナリオのニーズに対して相対的である必要があります。たとえば、一般的な表面配置では空間マップを使用できますが、正確に配置するには、マーカーと調整を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-194">Accuracy of the placement should be relative to the needs of the scenario; for example, general surface placement can use the spatial map, but more accurate placement will require some use of markers and calibration.</span></span>

### <a name="device-impact"></a><span data-ttu-id="bcd27-195">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="bcd27-195">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bcd27-196"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-196"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bcd27-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-197"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bcd27-198">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-198">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="bcd27-199">品質基準</span><span class="sxs-lookup"><span data-stu-id="bcd27-199">Quality criteria</span></span>

|  <span data-ttu-id="bcd27-200">最高</span><span class="sxs-lookup"><span data-stu-id="bcd27-200">Best</span></span>  |  <span data-ttu-id="bcd27-201">あっ</span><span class="sxs-lookup"><span data-stu-id="bcd27-201">Meets</span></span> |  <span data-ttu-id="bcd27-202">失敗</span><span class="sxs-lookup"><span data-stu-id="bcd27-202">Fail</span></span> |
--- | --- | ---
| <span data-ttu-id="bcd27-203">ホログラムは、通常、センチメートル ~ インチの範囲内のサーフェイスに配置されます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-203">Holograms align to the surface typically in the centimeters to inches range.</span></span> <span data-ttu-id="bcd27-204">より正確な精度が必要な場合は、アプリの仕様内でコラボレーションのための効率的な手段を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-204">If you need more accuracy, the app should provide an efficient means for collaboration within the app spec.</span></span> | <span data-ttu-id="bcd27-205">N/A</span><span class="sxs-lookup"><span data-stu-id="bcd27-205">NA</span></span> | <span data-ttu-id="bcd27-206">サーフェイスを分割するか、表面から離れた場所に表示することによって、ホログラムが物理的なターゲットオブジェクトと共に配置されていないことを認識します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-206">The holograms appear unaligned with the physical target object by either breaking the surface plane or appearing to float away from the surface.</span></span> <span data-ttu-id="bcd27-207">精度が必要な場合は、ホログラムがシナリオの近接仕様を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-207">If accuracy is required, Holograms should meet the proximity spec of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="bcd27-208">測定する方法</span><span class="sxs-lookup"><span data-stu-id="bcd27-208">How to measure</span></span>

* <span data-ttu-id="bcd27-209">空間マップに配置されているホログラムは、サーフェイスの上または下に劇的に浮動小数点型で表示されないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="bcd27-209">Holograms that are placed on spatial map shouldn't appear to dramatically float above or below the surface.</span></span>
* <span data-ttu-id="bcd27-210">正確な配置を必要とするホログラムには、シナリオの要件に対して正確な何らかの形式のマーカーと調整システムが必要です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-210">Holograms that require accurate placement should have some form of marker and calibration system that is accurate to the scenario's requirement.</span></span>

### <a name="recommendations"></a><span data-ttu-id="bcd27-211">推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-211">Recommendations</span></span>

* <span data-ttu-id="bcd27-212">空間マップは、精度が不要な場合にオブジェクトをサーフェイスに配置する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-212">Spatial map is useful for placing objects on surfaces when precision isn’t required.</span></span>
* <span data-ttu-id="bcd27-213">最適な精度を得るには、マーカーまたはポスターを使用して、ホログラムと Xbox コントローラー (または手動配置機構) を最終的な調整用に設定します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-213">For the best precision, use markers or posters to set the holograms and an Xbox controller (or some manual alignment mechanism) for final calibration.</span></span>
* <span data-ttu-id="bcd27-214">特大の大きなホログラムを論理部分に分割し、各部分をサーフェイスに配置することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="bcd27-214">Consider breaking extra-large holograms into logical parts and aligning each part to the surface.</span></span>
* <span data-ttu-id="bcd27-215">不適切に設定した interpupillary distance (IPD) は、ホログラムのアラインメントにも影響を与えることがあります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-215">Improperly set interpupillary distance (IPD) can also effect hologram alignment.</span></span> <span data-ttu-id="bcd27-216">常に HoloLens をユーザーの IPD に構成します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-216">Always configure HoloLens to the user's IPD.</span></span>

### <a name="resources"></a><span data-ttu-id="bcd27-217">リソース</span><span class="sxs-lookup"><span data-stu-id="bcd27-217">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="bcd27-218">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="bcd27-218">Documentation</span></span>

* [<span data-ttu-id="bcd27-219">空間マッピングの配置</span><span class="sxs-lookup"><span data-stu-id="bcd27-219">Spatial mapping placement</span></span>](../../design/spatial-mapping.md#placement)
* [<span data-ttu-id="bcd27-220">ルームスキャンプロセス</span><span class="sxs-lookup"><span data-stu-id="bcd27-220">Room scanning process</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="bcd27-221">空間アンカーのベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="bcd27-221">Spatial anchors best practices</span></span>](../../design/spatial-anchors.md#best-practices)
* [<span data-ttu-id="bcd27-222">追跡エラーの処理</span><span class="sxs-lookup"><span data-stu-id="bcd27-222">Handling tracking errors</span></span>](../../design/coordinate-systems.md#handling-tracking-errors)
* [<span data-ttu-id="bcd27-223">Unity の空間マッピング</span><span class="sxs-lookup"><span data-stu-id="bcd27-223">Spatial mapping in Unity</span></span>](../unity/spatial-mapping-in-unity.md)
* [<span data-ttu-id="bcd27-224">Vuforia 開発の概要</span><span class="sxs-lookup"><span data-stu-id="bcd27-224">Vuforia development overview</span></span>](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="bcd27-225">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="bcd27-225">Tools and tutorials</span></span>

* [<span data-ttu-id="bcd27-226">MR ツールキット, 空間マッピングライブラリ</span><span class="sxs-lookup"><span data-stu-id="bcd27-226">MR Toolkit, Spatial Mapping Libraries</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [<span data-ttu-id="bcd27-227">MR コンパニオンキット、ポスター調整のサンプル</span><span class="sxs-lookup"><span data-stu-id="bcd27-227">MR Companion Kit, Poster Calibration Sample</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [<span data-ttu-id="bcd27-228">MR コンパニオンキット、Kinect IPD</span><span class="sxs-lookup"><span data-stu-id="bcd27-228">MR Companion Kit, Kinect IPD</span></span>](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a><span data-ttu-id="bcd27-229">外部参照</span><span class="sxs-lookup"><span data-stu-id="bcd27-229">External references</span></span>

* [<span data-ttu-id="bcd27-230">Lowes のケーススタディ、有効桁数のアラインメント</span><span class="sxs-lookup"><span data-stu-id="bcd27-230">Lowes Case Study, Precision alignment</span></span>](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a><span data-ttu-id="bcd27-231">快適なゾーンの表示</span><span class="sxs-lookup"><span data-stu-id="bcd27-231">Viewing zone of comfort</span></span>

<span data-ttu-id="bcd27-232">アプリ開発者は、さまざまな深度でコンテンツとホログラムを配置することで、ユーザーの目がどのようになるかを制御します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-232">App developers control where users' eyes converge by placing content and holograms at various depths.</span></span> <span data-ttu-id="bcd27-233">Hololens のディスプレイは、ユーザーから約 2.0 m 離れた光の距離で固定されているため、HoloLens を装着しているユーザーは、常に 2.0 m に対応して明確なイメージを維持します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-233">Users wearing HoloLens will always accommodate to 2.0 m to maintain a clear image because HoloLens displays are fixed at an optical distance approximately 2.0 m away from the user.</span></span> <span data-ttu-id="bcd27-234">不適切なコンテンツの深さは、視覚不快感や疲労につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-234">Improper content depth can lead to visual discomfort or fatigue.</span></span>

### <a name="device-impact"></a><span data-ttu-id="bcd27-235">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="bcd27-235">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bcd27-236"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-236"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bcd27-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-237"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bcd27-238">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-238">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="bcd27-239">品質基準</span><span class="sxs-lookup"><span data-stu-id="bcd27-239">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="bcd27-240">最高</span><span class="sxs-lookup"><span data-stu-id="bcd27-240">Best</span></span> </td><td><ul>
<li><span data-ttu-id="bcd27-241">2 m にコンテンツを配置します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-241">Place content at 2 m.</span></span></li><li><span data-ttu-id="bcd27-242">ホログラムを 2 m に配置できず、収束と宿泊の間の競合を回避できない場合、ホログラムの配置に最適なゾーンは 1.25 m ~ 5 m です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-242">When holograms cannot be placed at 2 m and conflicts between convergence and accommodation cannot be avoided, the optimal zone for hologram placement is between 1.25 m and 5 m.</span></span></li><li><span data-ttu-id="bcd27-243">どのような場合でも、デザイナーは、ユーザーが 1 + m を操作できるようにコンテンツを構成する必要があります (たとえば、コンテンツサイズと既定の配置パラメーターを調整します)。</span><span class="sxs-lookup"><span data-stu-id="bcd27-243">In every case, designers should structure content to encourage users to interact 1+ m away (e.g. adjust content size and default placement parameters).</span></span></li><li><span data-ttu-id="bcd27-244">シナリオで必要とされない限り、1 m から始まるフェードアウトを使用してクリッピング平面を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-244">Unless not required by the scenario, a clipping plane should be implement with fade out starting at 1 m.</span></span></li><li><span data-ttu-id="bcd27-245">Motionless ホログラムの詳細な監視が必要な場合は、コンテンツが 50 cm を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-245">In cases where closer observation of a motionless hologram is required, the content shouldn't be closer than 50 cm.</span></span></li>
</ul></td>
</tr><tr>
<td> <span data-ttu-id="bcd27-246">あっ</span><span class="sxs-lookup"><span data-stu-id="bcd27-246">Meets</span></span></td><td> <span data-ttu-id="bcd27-247">コンテンツは、表示およびモーションのガイダンスに含まれていますが、不適切な使用またはクリッピング平面の使用はありません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-247">Content is within the viewing and motion guidance, but improper use or no use of the clipping plane.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bcd27-248">失敗</span><span class="sxs-lookup"><span data-stu-id="bcd27-248">Fail</span></span> </td><td> <span data-ttu-id="bcd27-249">コンテンツが非常に近い場所に表示されます (通常は &lt; 1.25 m、またはより &lt; 詳細な監視を必要とする固定のホログラムの場合は 50 cm です)。</span><span class="sxs-lookup"><span data-stu-id="bcd27-249">Content is presented too close (typically &lt;1.25 m, or &lt;50 cm for stationary holograms requiring closer observation.)</span></span></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="bcd27-250">測定する方法</span><span class="sxs-lookup"><span data-stu-id="bcd27-250">How to measure</span></span>

* <span data-ttu-id="bcd27-251">通常、コンテンツは 2 m 離れている必要がありますが、1.25 を超える、または 5 m を超えることはできません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-251">Content should typically be 2 m away, but no closer than 1.25 or further than 5 m.</span></span>
* <span data-ttu-id="bcd27-252">例外がいくつかある場合は、1 m からコンテンツをフェードアウトして、HoloLens クリッピングのレンダリング距離を85CM に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-252">With few exceptions, the HoloLens clipping render distance should be set to 85CM with fade out of content starting at 1 m.</span></span> <span data-ttu-id="bcd27-253">コンテンツにアプローチし、クリッピング平面効果を確認します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-253">Approach the content and note the clipping plane effect.</span></span>
* <span data-ttu-id="bcd27-254">静止コンテンツは、50 cm を超えないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-254">Stationary content should not be closer than 50 cm away.</span></span>

### <a name="recommendations"></a><span data-ttu-id="bcd27-255">推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-255">Recommendations</span></span>

* <span data-ttu-id="bcd27-256">最適な表示距離が 2 m になるようにコンテンツをデザインします。</span><span class="sxs-lookup"><span data-stu-id="bcd27-256">Design content for the optimal viewing distance of 2 m.</span></span>
* <span data-ttu-id="bcd27-257">クリッピングレンダリング距離を 85 cm に設定し、1 m からコンテンツをフェードアウトします。</span><span class="sxs-lookup"><span data-stu-id="bcd27-257">Set the clipping render distance to 85 cm with fade out of content starting at 1 m.</span></span>
* <span data-ttu-id="bcd27-258">近くに表示する必要がある固定のホログラムの場合、クリッピング平面は 30 cm 以下であり、フェードアウトがクリッピング平面から少なくとも 10 cm 離れて開始される必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-258">For stationary holograms that need closer viewing, the clipping plane should be no closer than 30 cm and fade out should start at least 10 cm away from the clipping plane.</span></span>

### <a name="resources"></a><span data-ttu-id="bcd27-259">リソース</span><span class="sxs-lookup"><span data-stu-id="bcd27-259">Resources</span></span>

* [<span data-ttu-id="bcd27-260">レンダリング距離</span><span class="sxs-lookup"><span data-stu-id="bcd27-260">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="bcd27-261">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="bcd27-261">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)
* [<span data-ttu-id="bcd27-262">スケールを試してみる</span><span class="sxs-lookup"><span data-stu-id="bcd27-262">Experimenting with scale</span></span>](../../design/scale.md#experimenting-with-scale)
* [<span data-ttu-id="bcd27-263">テキスト、推奨されるフォントサイズ</span><span class="sxs-lookup"><span data-stu-id="bcd27-263">Text, Recommended font size</span></span>](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a><span data-ttu-id="bcd27-264">深度の切り替え</span><span class="sxs-lookup"><span data-stu-id="bcd27-264">Depth switching</span></span>

<span data-ttu-id="bcd27-265">快適な問題のゾーンが表示されているかどうかに関係なく、ユーザーに対して頻繁にまたは迅速に (ホログラムや実際のコンテンツを含む) 近接するオブジェクトを切り替えることによって、oculomotor と general 不快感が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-265">Regardless of viewing zone of comfort issues, demands for the user to switch frequently or quickly between near and far focal objects (including holograms and real-world content) can lead to oculomotor fatigue, and general discomfort.</span></span>

### <a name="device-impact"></a><span data-ttu-id="bcd27-266">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="bcd27-266">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bcd27-267"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-267"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bcd27-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-268"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bcd27-269">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-269">✔️</span></span></td>
        <td><span data-ttu-id="bcd27-270">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-270">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="bcd27-271">品質基準</span><span class="sxs-lookup"><span data-stu-id="bcd27-271">Quality criteria</span></span>

|  <span data-ttu-id="bcd27-272">最高</span><span class="sxs-lookup"><span data-stu-id="bcd27-272">Best</span></span>  |  <span data-ttu-id="bcd27-273">あっ</span><span class="sxs-lookup"><span data-stu-id="bcd27-273">Meets</span></span> |  <span data-ttu-id="bcd27-274">失敗</span><span class="sxs-lookup"><span data-stu-id="bcd27-274">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="bcd27-275">ユーザーが自然に refocus しないようにする、限定的または自然な深さの切り替え。</span><span class="sxs-lookup"><span data-stu-id="bcd27-275">Limited or natural depth switching that doesn’t cause the user to unnaturally refocus.</span></span> | <span data-ttu-id="bcd27-276">[突然の深さ] スイッチこれはコアであり、アプリケーションエクスペリエンスに設計されています。または、予期しない実際のコンテンツによって発生した、突然の深さスイッチです。</span><span class="sxs-lookup"><span data-stu-id="bcd27-276">Abrupt depth switch this is core and designed into the app experience, or abrupt depth switch that is caused by unexpected real-world content.</span></span> | <span data-ttu-id="bcd27-277">一貫した深さスイッチ、またはアプリエクスペリエンスの中核とならない、急激な深さの切り替え。</span><span class="sxs-lookup"><span data-stu-id="bcd27-277">Consistent depth switch, or abrupt depth switching that isn’t necessary or core to the app experience.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="bcd27-278">測定する方法</span><span class="sxs-lookup"><span data-stu-id="bcd27-278">How to measure</span></span>

* <span data-ttu-id="bcd27-279">アプリケーションで、深さのフォーカスを一貫して変更する必要がある場合は、深さの切り替えに問題があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-279">If the app requires the user to consistently and/or abruptly change depth focus, there is depth switching problem.</span></span>

### <a name="recommendations"></a><span data-ttu-id="bcd27-280">推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-280">Recommendations</span></span>

* <span data-ttu-id="bcd27-281">一貫した中心面でプライマリコンテンツを保持し、安定化平面が焦点平面と一致していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-281">Keep primary content at a consistent focal plane and make sure the stabilization plane matches the focal plane.</span></span> <span data-ttu-id="bcd27-282">これにより、oculomotor の疲労と予期しないホログラムの動きが軽減されます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-282">This will alleviate oculomotor fatigue and unexpected hologram movement.</span></span>

### <a name="resources"></a><span data-ttu-id="bcd27-283">リソース</span><span class="sxs-lookup"><span data-stu-id="bcd27-283">Resources</span></span>

* [<span data-ttu-id="bcd27-284">レンダリング距離</span><span class="sxs-lookup"><span data-stu-id="bcd27-284">Render distance</span></span>](hologram-stability.md#hologram-render-distances)
* [<span data-ttu-id="bcd27-285">Unity でのフォーカス ポイント</span><span class="sxs-lookup"><span data-stu-id="bcd27-285">Focus point in Unity</span></span>](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a><span data-ttu-id="bcd27-286">空間サウンドの使用</span><span class="sxs-lookup"><span data-stu-id="bcd27-286">Use of spatial sound</span></span>

<span data-ttu-id="bcd27-287">Windows Mixed Reality では、音声エンジンは、方向、距離、および環境シミュレーションを使用して3D サウンドをシミュレートすることによって、混合した現実のエクスペリエンスの aural コンポーネントを提供します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-287">In Windows Mixed Reality, the audio engine provides the aural component of the mixed reality experience by simulating 3D sound using direction, distance, and environmental simulations.</span></span> <span data-ttu-id="bcd27-288">アプリケーションで空間サウンドを使用すると、開発者はユーザーに対して3次元空間 (球) にサウンドを convincingly ことができます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-288">Using spatial sound in an application allows developers to convincingly place sounds in a 3-dimensional space (sphere) all around the user.</span></span> <span data-ttu-id="bcd27-289">これらのサウンドは、実際の物理オブジェクトまたはユーザーの周囲の混合現実ホログラムからのものであるように見えます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-289">Those sounds will then seem as if they were coming from real physical objects or the mixed reality holograms in the user's surroundings.</span></span> <span data-ttu-id="bcd27-290">空間サウンドは、mixed reality アプリケーションでの immersion、アクセシビリティ、UX の設計を行うための強力なツールです。</span><span class="sxs-lookup"><span data-stu-id="bcd27-290">Spatial sound is a powerful tool for immersion, accessibility, and UX design in mixed reality applications.</span></span>

### <a name="device-impact"></a><span data-ttu-id="bcd27-291">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="bcd27-291">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bcd27-292"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-292"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bcd27-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-293"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bcd27-294">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-294">✔️</span></span></td>
        <td><span data-ttu-id="bcd27-295">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-295">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="bcd27-296">品質基準</span><span class="sxs-lookup"><span data-stu-id="bcd27-296">Quality criteria</span></span>

|  <span data-ttu-id="bcd27-297">最高</span><span class="sxs-lookup"><span data-stu-id="bcd27-297">Best</span></span>  |  <span data-ttu-id="bcd27-298">あっ</span><span class="sxs-lookup"><span data-stu-id="bcd27-298">Meets</span></span> |  <span data-ttu-id="bcd27-299">失敗</span><span class="sxs-lookup"><span data-stu-id="bcd27-299">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="bcd27-300">サウンドは論理的には spatialized であり、UX は適切にサウンドを使用して、オブジェクトの検出とユーザーフィードバックを支援します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-300">Sound is logically spatialized, and the UX appropriately uses sound to assist with object discovery and user feedback.</span></span> <span data-ttu-id="bcd27-301">サウンドは、自然で、オブジェクトに関連し、シナリオ全体で正規化されます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-301">Sound is natural and relevant to objects and normalized across the scenario.</span></span> | <span data-ttu-id="bcd27-302">空間オーディオは believability に対して適切に使用されますが、ユーザーのフィードバックと検索可能性を高めるための手段としては欠けています。</span><span class="sxs-lookup"><span data-stu-id="bcd27-302">Spatial audio is used appropriately for believability but missing as means to help with user feedback and discoverability.</span></span> | <span data-ttu-id="bcd27-303">サウンドが予期したとおりに spatialized されていないか、UX 内でユーザーを支援する音がありません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-303">Sound is not spatialized as expected, and/or lack of sound to assist user within the UX.</span></span> <span data-ttu-id="bcd27-304">または、空間オーディオがシナリオの設計で検討されていないか、使用されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="bcd27-304">Or spatial audio was not considered or used in the design of the scenario.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="bcd27-305">測定する方法</span><span class="sxs-lookup"><span data-stu-id="bcd27-305">How to measure</span></span>

* <span data-ttu-id="bcd27-306">一般に、関連するサウンドは、ターゲットホログラムから出力する必要があります (たとえば、holographic dog からほえサウンドが生成されます)。</span><span class="sxs-lookup"><span data-stu-id="bcd27-306">In general, relevant sounds should emit from target holograms (eg., bark sound coming from holographic dog.)</span></span>
* <span data-ttu-id="bcd27-307">サウンドキューは、ユーザーが holographic フレーム外のアクションをフィードバックまたは認識するのを支援するために、UX 全体で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-307">Sound cues should be used throughout the UX to assist the user with feedback or awareness of actions outside the holographic frame.</span></span>

### <a name="recommendations"></a><span data-ttu-id="bcd27-308">推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-308">Recommendations</span></span>

* <span data-ttu-id="bcd27-309">オブジェクト検出とユーザーインターフェイスをサポートするには、空間オーディオを使用します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-309">Use spatial audio to assist with object discovery and user interfaces.</span></span>
* <span data-ttu-id="bcd27-310">実際のサウンドは、合成や不自然な音よりも優れています。</span><span class="sxs-lookup"><span data-stu-id="bcd27-310">Real sounds work better than synthesize or unnatural sound.</span></span>
* <span data-ttu-id="bcd27-311">ほとんどのサウンドは spatialized にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-311">Most sounds should be spatialized.</span></span>
* <span data-ttu-id="bcd27-312">非表示の発信器は避けてください。</span><span class="sxs-lookup"><span data-stu-id="bcd27-312">Avoid invisible emitters.</span></span>
* <span data-ttu-id="bcd27-313">空間マスクは避けてください。</span><span class="sxs-lookup"><span data-stu-id="bcd27-313">Avoid spatial masking.</span></span>
* <span data-ttu-id="bcd27-314">すべてのサウンドを正規化します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-314">Normalize all sounds.</span></span>

### <a name="resources"></a><span data-ttu-id="bcd27-315">リソース</span><span class="sxs-lookup"><span data-stu-id="bcd27-315">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="bcd27-316">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="bcd27-316">Documentation</span></span>

* [<span data-ttu-id="bcd27-317">立体音響</span><span class="sxs-lookup"><span data-stu-id="bcd27-317">Spatial sound</span></span>](../../design/spatial-sound.md)
* [<span data-ttu-id="bcd27-318">立体音響の設計</span><span class="sxs-lookup"><span data-stu-id="bcd27-318">Spatial sound design</span></span>](../../design/spatial-sound-design.md)
* [<span data-ttu-id="bcd27-319">Unity の立体音響</span><span class="sxs-lookup"><span data-stu-id="bcd27-319">Spatial sound in Unity</span></span>](../unity/spatial-sound-in-unity.md)
* [<span data-ttu-id="bcd27-320">ケーススタディ、HoloTour の空間サウンド</span><span class="sxs-lookup"><span data-stu-id="bcd27-320">Case study, Spatial sound for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="bcd27-321">RoboRaid の空間サウンドを使用したケーススタディ</span><span class="sxs-lookup"><span data-stu-id="bcd27-321">Case study, Using spatial sound in RoboRaid</span></span>](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="bcd27-322">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="bcd27-322">Tools and tutorials</span></span>

* [<span data-ttu-id="bcd27-323">Mixed Reality Toolkit-空間オーディオ</span><span class="sxs-lookup"><span data-stu-id="bcd27-323">Mixed Reality Toolkit - Spatial Audio</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a><span data-ttu-id="bcd27-324">Holographic frame (視界) の境界にフォーカス</span><span class="sxs-lookup"><span data-stu-id="bcd27-324">Focus on holographic frame (FOV) boundaries</span></span>

<span data-ttu-id="bcd27-325">適切に設計されたユーザーエクスペリエンスでは、ユーザーを中心とした仮想環境の有用なコンテキストを作成し、維持することができます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-325">Well-designed user experiences can create and maintain useful context of the virtual environment that extends around the users.</span></span> <span data-ttu-id="bcd27-326">視界の境界の影響を軽減するには、コンテンツのスケールとコンテキスト、空間オーディオの使用、ガイダンスシステム、ユーザーの位置をよく設計する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-326">Mitigating the effect of the FOV boundaries involves a thoughtful design of content scale and context, use of spatial audio, guidance systems, and the user's position.</span></span> <span data-ttu-id="bcd27-327">そうすれば、ユーザーは快適なアプリエクスペリエンスを実現しながら、視界の境界によって損なわれることはなくなります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-327">If done right, the user will feel less impaired by the FOV boundaries while having a comfortable app experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="bcd27-328">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="bcd27-328">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bcd27-329"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-329"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bcd27-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-330"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bcd27-331">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-331">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="bcd27-332">品質基準</span><span class="sxs-lookup"><span data-stu-id="bcd27-332">Quality criteria</span></span>

|  <span data-ttu-id="bcd27-333">最高</span><span class="sxs-lookup"><span data-stu-id="bcd27-333">Best</span></span>  |  <span data-ttu-id="bcd27-334">あっ</span><span class="sxs-lookup"><span data-stu-id="bcd27-334">Meets</span></span> |  <span data-ttu-id="bcd27-335">失敗</span><span class="sxs-lookup"><span data-stu-id="bcd27-335">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="bcd27-336">ユーザーはコンテキストを失うことはなく、表示も快適です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-336">User never loses context and viewing is comfortable.</span></span> <span data-ttu-id="bcd27-337">ラージオブジェクトのコンテキストに関するサポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-337">Context assistance is provided for large objects.</span></span> <span data-ttu-id="bcd27-338">フレームの外部にあるオブジェクトについて、見つけやすさと表示に関するガイダンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-338">Discoverability and viewing guidance is provided for objects outside the frame.</span></span> <span data-ttu-id="bcd27-339">一般に、見やすさを向上させるには、ホログラムのモーションデザインとスケールが適しています。</span><span class="sxs-lookup"><span data-stu-id="bcd27-339">In general, motion design and scale of the holograms are appropriate for a comfortable viewing experience.</span></span> | <span data-ttu-id="bcd27-340">ユーザーはコンテキストを失うことはありませんが、限られた状況では追加のネックモーションが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-340">User never loses context, but extra neck motion may be required in limited situations.</span></span> <span data-ttu-id="bcd27-341">限られた状況では、ホログラムによって、ネックの動きが見られる垂直方向または水平方向のフレームが壊れることがあります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-341">In limited situations scale causes holograms to break either the vertical or horizontal frame causing some neck motion to view holograms.</span></span> | <span data-ttu-id="bcd27-342">ホログラムを表示するには、コンテキストや一貫したネック運動が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-342">User likely to lose context and/or consistent neck motion is required to view holograms.</span></span> <span data-ttu-id="bcd27-343">大規模な holographic オブジェクトに関するコンテキストガイダンスはありません。オブジェクトを移動しても、発見可能なガイダンスがなくても、オブジェクトを簡単に失うことがあります。また、広いホログラムでは、通常のネックモーションが必要になります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-343">No context guidance for large holographic objects, moving objects easy to lose outside the frame with no discoverability guidance, or tall holograms requires regular neck motion to view.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="bcd27-344">測定する方法</span><span class="sxs-lookup"><span data-stu-id="bcd27-344">How to measure</span></span>

* <span data-ttu-id="bcd27-345">境界でクリップされているため、(大きい) ホログラムのコンテキストが失われているか、認識されていません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-345">Context for a (large) hologram is lost or not understood due to being clipped at the boundaries.</span></span>
* <span data-ttu-id="bcd27-346">ホログラムの場所は、holographic フレームとの間で急速に移動される、要注意のダイレクタやコンテンツがないため、見つけるのが困難です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-346">Locations of holograms are hard to find due to the lack of attention directors or content that rapidly moves in and out of the holographic frame.</span></span>
* <span data-ttu-id="bcd27-347">シナリオでは、ネックの疲労を完全に確認するために、定期的かつ反復的に反復的に動きが必要です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-347">Scenario requires regular and repetitive up and down head motion to fully see a hologram resulting in neck fatigue.</span></span>

### <a name="recommendations"></a><span data-ttu-id="bcd27-348">推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-348">Recommendations</span></span>

* <span data-ttu-id="bcd27-349">視界に合った小さなオブジェクトを使用して操作を開始し、視覚的な手掛かりを使用して大きなバージョンに移行します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-349">Start the experience with small objects that fit the FOV, then transition with visual cues to larger versions.</span></span>
* <span data-ttu-id="bcd27-350">空間オーディオとアテンションダイレクタを使用すると、ユーザーが視界の外にあるコンテンツを見つけやすくなります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-350">Use spatial audio and attention directors to help the user find content that is outside the FOV.</span></span>
* <span data-ttu-id="bcd27-351">可能な限り、視界を垂直方向にクリップするホログラムは避けてください。</span><span class="sxs-lookup"><span data-stu-id="bcd27-351">As much as possible, avoid holograms that vertically clip the FOV.</span></span>
* <span data-ttu-id="bcd27-352">ユーザーにアプリ内のガイダンスを提供して、最適な表示場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-352">Provide the user with in-app guidance for best viewing location.</span></span>

### <a name="resources"></a><span data-ttu-id="bcd27-353">リソース</span><span class="sxs-lookup"><span data-stu-id="bcd27-353">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="bcd27-354">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="bcd27-354">Documentation</span></span>

* [<span data-ttu-id="bcd27-355">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="bcd27-355">Holographic frame</span></span>](../../design/holographic-frame.md)
* [<span data-ttu-id="bcd27-356">ケーススタディ、HoloStudio UI、相互作用設計学習</span><span class="sxs-lookup"><span data-stu-id="bcd27-356">Case Study, HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [<span data-ttu-id="bcd27-357">オブジェクトと環境のスケール</span><span class="sxs-lookup"><span data-stu-id="bcd27-357">Scale of objects and environments</span></span>](../../design/scale.md)
* [<span data-ttu-id="bcd27-358">カーソル、ビジュアルキュー</span><span class="sxs-lookup"><span data-stu-id="bcd27-358">Cursors, Visual cues</span></span>](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a><span data-ttu-id="bcd27-359">外部参照</span><span class="sxs-lookup"><span data-stu-id="bcd27-359">External references</span></span>

* [<span data-ttu-id="bcd27-360">視界に関する多くの ado</span><span class="sxs-lookup"><span data-stu-id="bcd27-360">Much ado about the FOV</span></span>](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a><span data-ttu-id="bcd27-361">ユーザーの位置に反応するコンテンツ</span><span class="sxs-lookup"><span data-stu-id="bcd27-361">Content reacts to user position</span></span>

<span data-ttu-id="bcd27-362">ホログラムは、"real" オブジェクトとほぼ同じ方法で、ユーザーの位置に反応する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-362">Holograms should react to the user position in roughly the same ways that "real" objects do.</span></span> <span data-ttu-id="bcd27-363">注目すべき設計上の考慮事項は、ユーザーの位置が固定されていて、ユーザーの動きに合わせて調整できるとは限らない UI 要素です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-363">A notable design consideration is UI elements that can't necessarily assume a user's position is stationary and adapt to the user's motion.</span></span> <span data-ttu-id="bcd27-364">ユーザーの位置に適切に適合するようにアプリを設計すると、believable エクスペリエンスが向上し、使いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-364">Designing an app that correctly adapts to user position will create a more believable experience and make it easier to use.</span></span>

### <a name="device-impact"></a><span data-ttu-id="bcd27-365">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="bcd27-365">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bcd27-366"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-366"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bcd27-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-367"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bcd27-368">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-368">✔️</span></span></td>
        <td><span data-ttu-id="bcd27-369">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-369">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="bcd27-370">品質基準</span><span class="sxs-lookup"><span data-stu-id="bcd27-370">Quality criteria</span></span>

<table>
<tr>
<td> <span data-ttu-id="bcd27-371">最高</span><span class="sxs-lookup"><span data-stu-id="bcd27-371">Best</span></span> </td><td> <span data-ttu-id="bcd27-372">コンテンツと UI はユーザーの位置に適合するため、ユーザーは、予期されるユーザー移動の範囲内でコンテンツと自然に対話できます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-372">Content and UI adapt to user positions allowing user to naturally interact with content within the scope of expected user movement.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bcd27-373">あっ</span><span class="sxs-lookup"><span data-stu-id="bcd27-373">Meets</span></span> </td><td> <span data-ttu-id="bcd27-374">UI はユーザーの位置に適合しますが、ユーザーが位置を調整する必要があるキーコンテンツのビューが妨げられる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-374">UI adapts to the user position, but may impede the view of key content requiring the user to adjust their position.</span></span></td>
</tr><tr>
<td> <span data-ttu-id="bcd27-375">失敗</span><span class="sxs-lookup"><span data-stu-id="bcd27-375">Fail</span></span> </td><td><ol>
<li><span data-ttu-id="bcd27-376">UI 要素は移動中に失われるかロックされ、ユーザーはコントロールを自然に返す (または検索する) ことができません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-376">UI elements are lost or locked during movement causing user to unnaturally return to (or find) controls.</span></span></li><li><span data-ttu-id="bcd27-377">UI 要素は、プライマリコンテンツのビューを制限します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-377">UI elements limit the view of primary content.</span></span></li><li><span data-ttu-id="bcd27-378">UI の移動は、特に <a href="../../design/billboarding-and-tag-along.md">タグに沿っ</a> た ui 要素によって、距離や勢いを表示するためには最適化されていません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-378">UI movement isn't optimized for viewing distance and momentum particularly with <a href="../../design/billboarding-and-tag-along.md">tag-along</a> UI elements.</span></span></li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a><span data-ttu-id="bcd27-379">測定する方法</span><span class="sxs-lookup"><span data-stu-id="bcd27-379">How to measure</span></span>

* <span data-ttu-id="bcd27-380">すべての測定値は、シナリオの妥当な範囲内で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-380">All measurements should be done within a reasonable scope of the scenario.</span></span> <span data-ttu-id="bcd27-381">ユーザーの移動は変化しますが、ユーザーの操作を極端に行うことなくアプリにトリックをかけることは避けてください。</span><span class="sxs-lookup"><span data-stu-id="bcd27-381">While user movement will vary, don’t try to trick the app with extreme user movement.</span></span>
* <span data-ttu-id="bcd27-382">UI 要素の場合、ユーザーの移動に関係なく、関連するコントロールを使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-382">For UI elements, relevant controls should be available regardless of user movement.</span></span> <span data-ttu-id="bcd27-383">たとえば、ユーザーが zoom を使用して3D マップを表示しているときに、場所に関係なく、ユーザーがズームコントロールをすぐに使用できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-383">For example, if the user is viewing and walking around a 3D map with zoom, the zoom control should be readily available to the user regardless of location.</span></span>

### <a name="recommendations"></a><span data-ttu-id="bcd27-384">推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-384">Recommendations</span></span>

* <span data-ttu-id="bcd27-385">ユーザーはカメラで、動きを制御します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-385">The user is the camera and they control the movement.</span></span> <span data-ttu-id="bcd27-386">これらのドライブを使用します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-386">Let them drive.</span></span>
* <span data-ttu-id="bcd27-387">テキストと menuing システムの billboarding を検討してください。これは、ユーザーが移動した場合に、ワールドロックまたは非表示になります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-387">Consider billboarding for text and menuing systems that would otherwise be world-locked or obscured if a user were to move around.</span></span>
* <span data-ttu-id="bcd27-388">ユーザーが前に何をしているかをユーザーが確認できるようにしながら、ユーザーに従う必要があるコンテンツにはタグを使用します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-388">Use tag-along for content that needs to follow the user while still allowing the user to see what is in front of them.</span></span>

### <a name="resources"></a><span data-ttu-id="bcd27-389">リソース</span><span class="sxs-lookup"><span data-stu-id="bcd27-389">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="bcd27-390">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="bcd27-390">Documentation</span></span>

* [<span data-ttu-id="bcd27-391">操作の設計</span><span class="sxs-lookup"><span data-stu-id="bcd27-391">Interaction design</span></span>](../../discover/hologram.md)
* [<span data-ttu-id="bcd27-392">色、光、素材</span><span class="sxs-lookup"><span data-stu-id="bcd27-392">Color, light, and material</span></span>](../../color,-light-and-materials.md)
* [<span data-ttu-id="bcd27-393">Billboard と Tag-along</span><span class="sxs-lookup"><span data-stu-id="bcd27-393">Billboarding and tag-along</span></span>](../../design/billboarding-and-tag-along.md)
* [<span data-ttu-id="bcd27-394">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="bcd27-394">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="bcd27-395">自発運動とユーザー移動</span><span class="sxs-lookup"><span data-stu-id="bcd27-395">Self-motion and user locomotion</span></span>](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a><span data-ttu-id="bcd27-396">入力の相互作用のわかりやすさ</span><span class="sxs-lookup"><span data-stu-id="bcd27-396">Input interaction clarity</span></span>

<span data-ttu-id="bcd27-397">入力の相互作用の明確さは、アプリのユーザビリティにとって重要であり、入力の一貫性、approachability、相互作用メソッドの発見性などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-397">Input interaction clarity is critical to an app's usability and includes input consistency, approachability, discoverability of interaction methods.</span></span> <span data-ttu-id="bcd27-398">ユーザーは、relearning なしでプラットフォーム全体の共通の対話を使用できます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-398">User can use platform-wide common interactions without relearning.</span></span> <span data-ttu-id="bcd27-399">アプリにカスタム入力がある場合は、それを明確に伝えることができます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-399">If the app has custom input, it should be clearly communicated and demonstrated.</span></span>

### <a name="device-impact"></a><span data-ttu-id="bcd27-400">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="bcd27-400">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bcd27-401"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-401"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bcd27-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-402"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bcd27-403">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-403">✔️</span></span></td>
        <td><span data-ttu-id="bcd27-404">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-404">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="bcd27-405">品質基準</span><span class="sxs-lookup"><span data-stu-id="bcd27-405">Quality criteria</span></span>

|  <span data-ttu-id="bcd27-406">最高</span><span class="sxs-lookup"><span data-stu-id="bcd27-406">Best</span></span>  |  <span data-ttu-id="bcd27-407">あっ</span><span class="sxs-lookup"><span data-stu-id="bcd27-407">Meets</span></span> |  <span data-ttu-id="bcd27-408">失敗</span><span class="sxs-lookup"><span data-stu-id="bcd27-408">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="bcd27-409">入力の相互作用メソッドは、Windows Mixed Reality に用意されている [ガイダンス](../../design/interaction-fundamentals.md)と一貫性があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-409">Input interaction methods are consistent with Windows Mixed Reality provided [guidance](../../design/interaction-fundamentals.md).</span></span> <span data-ttu-id="bcd27-410">任意のカスタム入力を標準入力と重複させることはできません (標準の相互作用を使用する必要があります)。また、ユーザーに明確に通知してデモンストレーションする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-410">Any custom input shouldn't be redundant with standard input (rather use standard interaction) and must be clearly communicated and demonstrated to the user.</span></span> | <span data-ttu-id="bcd27-411">"最適" に似ていますが、カスタム入力は標準の入力方式では冗長です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-411">Similar to best, but custom inputs are redundant with standard input methods.</span></span> <span data-ttu-id="bcd27-412">ユーザーは引き続き、アプリのエクスペリエンスの目標と進行状況を達成できます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-412">User can still achieve the goal and progress through the app experience.</span></span> | <span data-ttu-id="bcd27-413">入力方法またはボタンのマッピングを理解するのが困難です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-413">Difficult to understand input method or button mapping.</span></span> <span data-ttu-id="bcd27-414">入力は大幅にカスタマイズされており、標準入力、命令なし、または疲労や快適な問題を引き起こす可能性がありません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-414">Input is heavily customized, doesn't support standard input, no instructions, or likely to cause fatigue and comfort issues.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="bcd27-415">測定する方法</span><span class="sxs-lookup"><span data-stu-id="bcd27-415">How to measure</span></span>

* <span data-ttu-id="bcd27-416">アプリでは、一貫 [した標準の入力方法が使用されます。](../../design/interaction-fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="bcd27-416">The app uses consistent [standard input methods.](../../design/interaction-fundamentals.md)</span></span>
* <span data-ttu-id="bcd27-417">アプリにカスタム入力がある場合は、次の方法で明確に伝達されます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-417">If the app has custom input, it's clearly communicated through:</span></span>
* <span data-ttu-id="bcd27-418">最初の実行エクスペリエンス</span><span class="sxs-lookup"><span data-stu-id="bcd27-418">First-run experience</span></span>
* <span data-ttu-id="bcd27-419">入門画面</span><span class="sxs-lookup"><span data-stu-id="bcd27-419">Introductory screens</span></span>
* <span data-ttu-id="bcd27-420">ヒント</span><span class="sxs-lookup"><span data-stu-id="bcd27-420">Tooltips</span></span>
* <span data-ttu-id="bcd27-421">ハンド コーチ</span><span class="sxs-lookup"><span data-stu-id="bcd27-421">Hand coach</span></span>
* <span data-ttu-id="bcd27-422">ヘルプセクション</span><span class="sxs-lookup"><span data-stu-id="bcd27-422">Help section</span></span>
* <span data-ttu-id="bcd27-423">ボイス オーバー</span><span class="sxs-lookup"><span data-stu-id="bcd27-423">Voice over</span></span>

### <a name="recommendations"></a><span data-ttu-id="bcd27-424">推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-424">Recommendations</span></span>

* <span data-ttu-id="bcd27-425">可能な場合は常に標準の入力方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-425">Use standard input methods whenever possible.</span></span>
* <span data-ttu-id="bcd27-426">標準以外の入力方法については、デモ、チュートリアル、およびツールヒントを提供します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-426">Provide demonstrations, tutorials, and tooltips for non-standard input methods.</span></span>
* <span data-ttu-id="bcd27-427">アプリ全体で一貫した相互作用モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-427">Use a consistent interaction model throughout the app.</span></span>

### <a name="resources"></a><span data-ttu-id="bcd27-428">リソース</span><span class="sxs-lookup"><span data-stu-id="bcd27-428">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="bcd27-429">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="bcd27-429">Documentation</span></span>

* [<span data-ttu-id="bcd27-430">本能的な操作</span><span class="sxs-lookup"><span data-stu-id="bcd27-430">Instinctual interactions</span></span>](../../design/interaction-fundamentals.md)
* [<span data-ttu-id="bcd27-431">対話型オブジェクト</span><span class="sxs-lookup"><span data-stu-id="bcd27-431">Interactable objects</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="bcd27-432">ヘッド視線入力とドウェル</span><span class="sxs-lookup"><span data-stu-id="bcd27-432">Head-gaze and dwell</span></span>](../../design/gaze-and-dwell.md)
* [<span data-ttu-id="bcd27-433">カーソル</span><span class="sxs-lookup"><span data-stu-id="bcd27-433">Cursors</span></span>](../../design/cursors.md)
* [<span data-ttu-id="bcd27-434">快適で見つめ</span><span class="sxs-lookup"><span data-stu-id="bcd27-434">Comfort and gaze</span></span>](../../design/comfort.md#gaze-direction)
* [<span data-ttu-id="bcd27-435">音声入力</span><span class="sxs-lookup"><span data-stu-id="bcd27-435">Voice input</span></span>](../../design/voice-input.md)
* [<span data-ttu-id="bcd27-436">モーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="bcd27-436">Motion controllers</span></span>](../../design/motion-controllers.md)
* [<span data-ttu-id="bcd27-437">Unity 用入力移植ガイド</span><span class="sxs-lookup"><span data-stu-id="bcd27-437">Input porting guide for Unity</span></span>](../porting-apps/input-porting-guide-for-unity.md)
* [<span data-ttu-id="bcd27-438">Unity でのキーボード入力</span><span class="sxs-lookup"><span data-stu-id="bcd27-438">Keyboard input in Unity</span></span>](../unity/keyboard-input-in-unity.md)
* [<span data-ttu-id="bcd27-439">Unity の視線入力</span><span class="sxs-lookup"><span data-stu-id="bcd27-439">Gaze in Unity</span></span>](../unity/gaze-in-unity.md)
* [<span data-ttu-id="bcd27-440">Unity でのジェスチャとモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="bcd27-440">Gestures and motion controllers in Unity</span></span>](../unity/gestures-and-motion-controllers-in-unity.md)
* [<span data-ttu-id="bcd27-441">Unity の音声入力</span><span class="sxs-lookup"><span data-stu-id="bcd27-441">Voice input in Unity</span></span>](../unity/voice-input-in-unity.md)
* [<span data-ttu-id="bcd27-442">DirectX でのキーボード、マウス、およびコントローラー入力</span><span class="sxs-lookup"><span data-stu-id="bcd27-442">Keyboard, mouse, and controller input in DirectX</span></span>](../../keyboard,-mouse,-and-controller-input-in-directx.md)
* [<span data-ttu-id="bcd27-443">DirectX でのヘッド視線入力とアイ視線入力</span><span class="sxs-lookup"><span data-stu-id="bcd27-443">Head and eye gaze in DirectX</span></span>](../native/gaze-in-directx.md)
* [<span data-ttu-id="bcd27-444">DirectX での手とモーション コントローラー</span><span class="sxs-lookup"><span data-stu-id="bcd27-444">Hands and motion controllers in DirectX</span></span>](../native/hands-and-motion-controllers-in-directx.md)
* [<span data-ttu-id="bcd27-445">DirectX の音声入力</span><span class="sxs-lookup"><span data-stu-id="bcd27-445">Voice input in DirectX</span></span>](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="bcd27-446">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="bcd27-446">Tools and tutorials</span></span>

* [<span data-ttu-id="bcd27-447">ケーススタディ: よりパーソナルコンピューティングの追求</span><span class="sxs-lookup"><span data-stu-id="bcd27-447">Case study: The pursuit of more personal computing</span></span>](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [<span data-ttu-id="bcd27-448">キャストスタディ: HoloStudio UI と相互作用設計学習</span><span class="sxs-lookup"><span data-stu-id="bcd27-448">Cast study: HoloStudio UI and interaction design learnings</span></span>](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [<span data-ttu-id="bcd27-449">サンプルアプリ: 要素の周期テーブル</span><span class="sxs-lookup"><span data-stu-id="bcd27-449">Sample app: Periodic table of the elements</span></span>](../unity/periodic-table-of-the-elements.md)
* [<span data-ttu-id="bcd27-450">サンプルアプリ: 旧暦モジュール</span><span class="sxs-lookup"><span data-stu-id="bcd27-450">Sample app: Lunar module</span></span>](../unity/lunar-module.md)

## <a name="interactable-objects"></a><span data-ttu-id="bcd27-451">対話型オブジェクト</span><span class="sxs-lookup"><span data-stu-id="bcd27-451">Interactable objects</span></span>

<span data-ttu-id="bcd27-452">ボタンは、2D 抽象ワールドでイベントをトリガーするために使用される比喩です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-452">A button has long been a metaphor used for triggering an event in the 2D abstract world.</span></span> <span data-ttu-id="bcd27-453">3次元混合の現実世界では、この抽象化の世界に限定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-453">In the three-dimensional mixed reality world, we don’t have to be confined to this world of abstraction anymore.</span></span> <span data-ttu-id="bcd27-454">イベントをトリガーする対話型オブジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-454">Anything can be an Interactable object that triggers an event.</span></span> <span data-ttu-id="bcd27-455">対話型オブジェクトは、テーブル上のコーヒーカップの任意のものとして、無線でバルーンに表示できます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-455">An interactable object can be represented as anything from a coffee cup on the table to a balloon floating in the air.</span></span> <span data-ttu-id="bcd27-456">フォームに関係なく、対話型オブジェクトは、ユーザーがビジュアルおよびオーディオキューを使用して明確に認識できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-456">Regardless of the form, interactable objects should be clearly recognizable by the user through visual and audio cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="bcd27-457">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="bcd27-457">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bcd27-458"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-458"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bcd27-459"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-459"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bcd27-460">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-460">✔️</span></span></td>
        <td><span data-ttu-id="bcd27-461">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-461">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="bcd27-462">品質基準</span><span class="sxs-lookup"><span data-stu-id="bcd27-462">Quality criteria</span></span>

|  <span data-ttu-id="bcd27-463">最高</span><span class="sxs-lookup"><span data-stu-id="bcd27-463">Best</span></span>  |  <span data-ttu-id="bcd27-464">あっ</span><span class="sxs-lookup"><span data-stu-id="bcd27-464">Meets</span></span> |  <span data-ttu-id="bcd27-465">失敗</span><span class="sxs-lookup"><span data-stu-id="bcd27-465">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="bcd27-466">フォームに関係なく、対話型オブジェクトは、アイドル、ターゲット、および選択された3つの状態にわたって、ビジュアルおよびオーディオのキューを介して認識されます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-466">Regardless of form, interactable objects are recognizable through visual and audio cues across three states: idle, targeted, and selected.</span></span> <span data-ttu-id="bcd27-467">"ご覧のように、エクスペリエンス全体で一貫して使用されています。</span><span class="sxs-lookup"><span data-stu-id="bcd27-467">"See it, say it" is clear and consistently used throughout the experience.</span></span> <span data-ttu-id="bcd27-468">オブジェクトは、フリーターゲットのエラーを許容するようにスケーリングおよび配布されます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-468">Objects are scaled and distributed to allow for error free targeting.</span></span> | <span data-ttu-id="bcd27-469">ユーザーは、オーディオまたはビジュアルフィードバックによってオブジェクトを対話型として認識し、オブジェクトをターゲットにしてアクティブ化することができます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-469">User can recognize object as interactable through audio or visual feedback, and can target and activate the object.</span></span> | <span data-ttu-id="bcd27-470">ビジュアルまたはオーディオのキューがない場合、ユーザーは対話型オブジェクトを認識できません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-470">Given no visual or audio cues, user can't recognize an interactable object.</span></span> <span data-ttu-id="bcd27-471">オブジェクトのスケールやオブジェクト間の距離により、相互作用がエラーを起こしやすくなります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-471">Interactions are error prone due to object scale or distance between objects.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="bcd27-472">測定する方法</span><span class="sxs-lookup"><span data-stu-id="bcd27-472">How to measure</span></span>

* <span data-ttu-id="bcd27-473">対話型オブジェクトは ' 対話型 ' として認識されます。ボタン、メニュー、アプリ固有のコンテンツを含む。</span><span class="sxs-lookup"><span data-stu-id="bcd27-473">Interactable objects are recognizable as 'interactable'; including buttons, menus, and app-specific content.</span></span> <span data-ttu-id="bcd27-474">経験則として、対話型オブジェクトを対象とする場合は、ビジュアルとオーディオの手掛かりが必要です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-474">As a rule of thumb there should be a visual and audio cue when targeting interactable objects.</span></span>

### <a name="recommendations"></a><span data-ttu-id="bcd27-475">推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-475">Recommendations</span></span>

* <span data-ttu-id="bcd27-476">対話のためにビジュアルとオーディオフィードバックを使用します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-476">Use visual and audio feedback for interactions.</span></span>
* <span data-ttu-id="bcd27-477">視覚的なフィードバックは、入力状態 (アイドル、ターゲット、選択) ごとに区別される必要があります</span><span class="sxs-lookup"><span data-stu-id="bcd27-477">Visual feedback should be differentiated for each input state (idle, targeted, selected)</span></span>
* <span data-ttu-id="bcd27-478">対話型オブジェクトは、エラーをターゲットにするためにスケーリングして配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-478">Interactable objects should be scaled and placed for error free targeting.</span></span>
* <span data-ttu-id="bcd27-479">グループ化された対話型オブジェクト (メニューバーやリストなど) には、ターゲットを設定するための適切なスペースが必要です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-479">Grouped interactable objects (such as a menu bar or list) should have proper spacing for targeting.</span></span>
* <span data-ttu-id="bcd27-480">音声コマンドをサポートするボタンとメニューでは、command キーワードにテキストラベルを指定する必要があります (「参照してください」と言います)。</span><span class="sxs-lookup"><span data-stu-id="bcd27-480">Buttons and menus that support voice command should provide text labels for the command keyword ("See it, say it")</span></span>

### <a name="resources"></a><span data-ttu-id="bcd27-481">リソース</span><span class="sxs-lookup"><span data-stu-id="bcd27-481">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="bcd27-482">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="bcd27-482">Documentation</span></span>

* [<span data-ttu-id="bcd27-483">対話可能なオブジェクト</span><span class="sxs-lookup"><span data-stu-id="bcd27-483">Interactable object</span></span>](../../design/interactable-object.md)
* [<span data-ttu-id="bcd27-484">Unity のテキスト</span><span class="sxs-lookup"><span data-stu-id="bcd27-484">Text in Unity</span></span>](../unity/text-in-unity.md)
* [<span data-ttu-id="bcd27-485">境界ボックスとアプリ バー</span><span class="sxs-lookup"><span data-stu-id="bcd27-485">Bounding box and App bar</span></span>](../../design/app-bar-and-bounding-box.md)
* [<span data-ttu-id="bcd27-486">音声入力</span><span class="sxs-lookup"><span data-stu-id="bcd27-486">Voice input</span></span>](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="bcd27-487">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="bcd27-487">Tools and tutorials</span></span>

* [<span data-ttu-id="bcd27-488">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="bcd27-488">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a><span data-ttu-id="bcd27-489">部屋のスキャン</span><span class="sxs-lookup"><span data-stu-id="bcd27-489">Room scanning</span></span>

<span data-ttu-id="bcd27-490">空間マッピングデータを必要とするアプリは、ユーザーがデバイスをアクティブにして環境を探索するときに、このデータを時間の経過と共に自動的に収集するためにデバイスに依存します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-490">Apps that require spatial mapping data rely on the device to automatically collect this data over time and across sessions as the user explores their environment with the device active.</span></span> <span data-ttu-id="bcd27-491">このデータの完全性と品質は、ユーザーが実行した探索の量、探索から経過した時間、家具やドアなどのオブジェクトが領域をスキャンした後に移動されたかどうかなど、さまざまな要因によって異なります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-491">The completeness and quality of this data depends on a number of factors including the amount of exploration the user has done, how much time has passed since the exploration and whether objects such as furniture and doors have moved since the device scanned the area.</span></span> <span data-ttu-id="bcd27-492">多くのアプリは、エクスペリエンスの開始時に空間マッピングデータを分析して、ユーザーが空間マップの完全性と品質を向上させるために追加の手順を実行する必要があるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-492">Many apps will analyze the spatial mapping data at the start of the experience to judge whether the user should perform additional steps to improve the completeness and quality of the spatial map.</span></span> <span data-ttu-id="bcd27-493">ユーザーが環境をスキャンする必要がある場合は、スキャンの実行中に [ガイダンスのクリア] を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-493">If the user is required to scan the environment, clear guidance should be provided during the scanning experience.</span></span>

### <a name="device-impact"></a><span data-ttu-id="bcd27-494">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="bcd27-494">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bcd27-495"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-495"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bcd27-496"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-496"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bcd27-497">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-497">✔️</span></span></td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="bcd27-498">品質基準</span><span class="sxs-lookup"><span data-stu-id="bcd27-498">Quality criteria</span></span>

|  <span data-ttu-id="bcd27-499">最高</span><span class="sxs-lookup"><span data-stu-id="bcd27-499">Best</span></span>  |  <span data-ttu-id="bcd27-500">あっ</span><span class="sxs-lookup"><span data-stu-id="bcd27-500">Meets</span></span> |  <span data-ttu-id="bcd27-501">失敗</span><span class="sxs-lookup"><span data-stu-id="bcd27-501">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="bcd27-502">ユーザーによるスキャンを通知する空間メッシュの視覚化が進行中です。</span><span class="sxs-lookup"><span data-stu-id="bcd27-502">Visualization of the spatial mesh tell users scanning is in progress.</span></span> <span data-ttu-id="bcd27-503">ユーザーは、何を行うか、およびスキャンが開始および停止するタイミングを明確に把握します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-503">User clearly knows what to do and when the scan starts and stops.</span></span> | <span data-ttu-id="bcd27-504">空間メッシュの視覚化が提供されていますが、ユーザーが何をしているかを明確に把握しておらず、進行状況に関する情報が提供されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-504">Visualization of the spatial mesh is provided, but the user may not clearly know what to do and no progress information is provided.</span></span> | <span data-ttu-id="bcd27-505">メッシュの視覚化がありません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-505">No visualization of mesh.</span></span> <span data-ttu-id="bcd27-506">検索する場所、またはスキャンの開始/停止時に関するガイダンス情報はユーザーに提供されません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-506">No guidance information provided to the user regarding where to look, or when the scan starts/stops.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="bcd27-507">測定する方法</span><span class="sxs-lookup"><span data-stu-id="bcd27-507">How to measure</span></span>

* <span data-ttu-id="bcd27-508">必要な部屋のスキャン中に、検索する場所と、スキャンを開始および停止するタイミングを示すビジュアルおよびオーディオのガイダンスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-508">During a required room scan, visual and audio guidance are provided indicating where to look, and when to start and stop scanning.</span></span>

### <a name="recommendations"></a><span data-ttu-id="bcd27-509">推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-509">Recommendations</span></span>

* <span data-ttu-id="bcd27-510">ユーザーの近くにあるユーザーの合計ボリュームがエクスペリエンスの一部である必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-510">Indicate how much of the total volume in the users vicinity needs to be part of the experience.</span></span>
* <span data-ttu-id="bcd27-511">スキャンが開始され、進行状況インジケーターなどの停止時に通信します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-511">Communicate when the scan starts and stops such as a progress indicator.</span></span>
* <span data-ttu-id="bcd27-512">スキャン中にメッシュの視覚エフェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-512">Use a visualization of the mesh during the scan.</span></span>
* <span data-ttu-id="bcd27-513">ユーザーが部屋を見たり、移動したりすることを奨励するために、ビジュアルとオーディオの手掛かりを提供します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-513">Provide visual and audio cues to encourage the user to look and move around the room.</span></span>
* <span data-ttu-id="bcd27-514">データを改善するための場所をユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-514">Inform the user where to go to improve the data.</span></span> <span data-ttu-id="bcd27-515">多くの場合、必要なスキャン品質を得るために、ユーザーに対して実行する必要があること (たとえば、天井、家具を見てみてください) を伝えることが最適な場合があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-515">In many cases, it may be best to tell the user what they need to do (e.g. look at the ceiling, look behind furniture), in order to get the necessary scan quality.</span></span>

### <a name="resources"></a><span data-ttu-id="bcd27-516">リソース</span><span class="sxs-lookup"><span data-stu-id="bcd27-516">Resources</span></span>

#### <a name="documentation"></a><span data-ttu-id="bcd27-517">ドキュメント</span><span class="sxs-lookup"><span data-stu-id="bcd27-517">Documentation</span></span>

* [<span data-ttu-id="bcd27-518">部屋のスキャンの可視化</span><span class="sxs-lookup"><span data-stu-id="bcd27-518">Room scan visualization</span></span>](../../design/room-scan-visualization.md)
* [<span data-ttu-id="bcd27-519">ケーススタディ: HoloLens の空間マッピング機能の拡張</span><span class="sxs-lookup"><span data-stu-id="bcd27-519">Case study: Expanding the spatial mapping capabilities of HoloLens</span></span>](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [<span data-ttu-id="bcd27-520">ケーススタディ: HoloTour の空間サウンド設計</span><span class="sxs-lookup"><span data-stu-id="bcd27-520">Case study: Spatial sound design for HoloTour</span></span>](../../design/case-study-spatial-sound-design-for-holotour.md)
* [<span data-ttu-id="bcd27-521">ケーススタディ: フラグメントでのイマーシブエクスペリエンスの作成</span><span class="sxs-lookup"><span data-stu-id="bcd27-521">Case study: Creating an immersive experience in Fragments</span></span>](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a><span data-ttu-id="bcd27-522">ツールとチュートリアル</span><span class="sxs-lookup"><span data-stu-id="bcd27-522">Tools and tutorials</span></span>

* [<span data-ttu-id="bcd27-523">Mixed Reality Toolkit-UX</span><span class="sxs-lookup"><span data-stu-id="bcd27-523">Mixed Reality Toolkit - UX</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a><span data-ttu-id="bcd27-524">方向インジケーター</span><span class="sxs-lookup"><span data-stu-id="bcd27-524">Directional indicators</span></span>

<span data-ttu-id="bcd27-525">Mixed reality アプリでは、コンテンツは、実際のオブジェクトによって view または occluded のフィールドの外部にある場合があります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-525">In a mixed reality app, content may be outside the field of view or occluded by real-world objects.</span></span> <span data-ttu-id="bcd27-526">適切にデザインされたアプリを使用すると、ユーザーが非表示のコンテンツを簡単に見つけられるようになります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-526">A well-designed app will make it easier for the user to find non-visible content.</span></span> <span data-ttu-id="bcd27-527">ディレクショナルインジケーターは、ユーザーに重要なコンテンツを通知し、ユーザーの位置を基準にしてコンテンツに関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-527">Directional indicators alert a user to important content and provide guidance to the content relative to the user's position.</span></span> <span data-ttu-id="bcd27-528">非表示コンテンツに関するガイダンスは、サウンドの発信器、方向矢印、または直接視覚的な合図の形式になります。</span><span class="sxs-lookup"><span data-stu-id="bcd27-528">Guidance to non-visible content can take the form of sound emitters, directional arrows, or direct visual cues.</span></span>

### <a name="device-impact"></a><span data-ttu-id="bcd27-529">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="bcd27-529">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bcd27-530"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-530"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bcd27-531"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-531"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bcd27-532">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-532">✔️</span></span></td>
        <td><span data-ttu-id="bcd27-533">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-533">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="bcd27-534">品質基準</span><span class="sxs-lookup"><span data-stu-id="bcd27-534">Quality criteria</span></span>

|  <span data-ttu-id="bcd27-535">最高</span><span class="sxs-lookup"><span data-stu-id="bcd27-535">Best</span></span>  |  <span data-ttu-id="bcd27-536">あっ</span><span class="sxs-lookup"><span data-stu-id="bcd27-536">Meets</span></span> |  <span data-ttu-id="bcd27-537">失敗</span><span class="sxs-lookup"><span data-stu-id="bcd27-537">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="bcd27-538">ビジュアルおよびオーディオキューは、ビューのフィールドの外部にある関連するコンテンツをユーザーに直接案内します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-538">Visual and audio cues directly guide the user to relevant content outside the field of view.</span></span> | <span data-ttu-id="bcd27-539">コンテンツの一般的な方向にユーザーを示す矢印またはインジケーター。</span><span class="sxs-lookup"><span data-stu-id="bcd27-539">An arrow or some indicator that points the user in the general direction of the content.</span></span> | <span data-ttu-id="bcd27-540">関連するコンテンツはビューのフィールドの外部にあり、ユーザーには不適切または場所のガイダンスは提供されません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-540">Relevant content is outside of the field of view, and poor or no location guidance is provided to the user.</span></span> | 

### <a name="how-to-measure"></a><span data-ttu-id="bcd27-541">測定する方法</span><span class="sxs-lookup"><span data-stu-id="bcd27-541">How to measure</span></span>

* <span data-ttu-id="bcd27-542">ビューの [ユーザー] フィールド以外の関連するコンテンツは、ビジュアルまたはオーディオキューを使用して検出できます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-542">Relevant content outside of the user field of view is discoverable through visual and/or audio cues.</span></span>

### <a name="recommendations"></a><span data-ttu-id="bcd27-543">推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-543">Recommendations</span></span>

* <span data-ttu-id="bcd27-544">関連するコンテンツがユーザーのビューの外部にある場合は、方向インジケーターとオーディオキューを使用して、ユーザーをコンテンツに案内します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-544">When relevant content is outside the user's field of view, use directional indicators and audio cues to guide the user to the content.</span></span> <span data-ttu-id="bcd27-545">多くの場合、方向性のある矢印よりも直接の視覚的なガイドをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bcd27-545">In many cases, a direct visual guide is preferred over directional arrows.</span></span>
* <span data-ttu-id="bcd27-546">方向インジケーターをカーソルに組み込むことはできません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-546">Directional indicators should not be built into the cursor.</span></span>

### <a name="resources"></a><span data-ttu-id="bcd27-547">リソース</span><span class="sxs-lookup"><span data-stu-id="bcd27-547">Resources</span></span>

* [<span data-ttu-id="bcd27-548">ホログラフィック フレーム</span><span class="sxs-lookup"><span data-stu-id="bcd27-548">Holographic frame</span></span>](../../design/holographic-frame.md)

## <a name="data-loading"></a><span data-ttu-id="bcd27-549">データの読み込み</span><span class="sxs-lookup"><span data-stu-id="bcd27-549">Data loading</span></span>

<span data-ttu-id="bcd27-550">プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-550">A progress control provides feedback to the user that a long-running operation is underway.</span></span> <span data-ttu-id="bcd27-551">これは、進行状況インジケーターが表示されているときにユーザーがアプリと対話できないことを意味し、待機時間がどの程度かかるかを示すこともできます。</span><span class="sxs-lookup"><span data-stu-id="bcd27-551">It can mean that the user can't interact with the app when the progress indicator is visible and can also indicate how long the wait time might be.</span></span>

### <a name="device-impact"></a><span data-ttu-id="bcd27-552">デバイスへの影響</span><span class="sxs-lookup"><span data-stu-id="bcd27-552">Device impact</span></span>

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="bcd27-553"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-553"><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></span></span></td>
        <td><span data-ttu-id="bcd27-554"><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="bcd27-554"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
        <td></td>
    </tr>
     <tr>
        <td><span data-ttu-id="bcd27-555">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-555">✔️</span></span></td>
        <td><span data-ttu-id="bcd27-556">✔️</span><span class="sxs-lookup"><span data-stu-id="bcd27-556">✔️</span></span></td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a><span data-ttu-id="bcd27-557">品質基準</span><span class="sxs-lookup"><span data-stu-id="bcd27-557">Quality criteria</span></span>

|  <span data-ttu-id="bcd27-558">最高</span><span class="sxs-lookup"><span data-stu-id="bcd27-558">Best</span></span>  |  <span data-ttu-id="bcd27-559">あっ</span><span class="sxs-lookup"><span data-stu-id="bcd27-559">Meets</span></span> |  <span data-ttu-id="bcd27-560">失敗</span><span class="sxs-lookup"><span data-stu-id="bcd27-560">Fail</span></span> |
--- | --- | ---
|  <span data-ttu-id="bcd27-561">データの読み込み中または処理中の進行状況を示す進行状況バーまたはリングの形式でのアニメーション化されたビジュアルインジケーター。</span><span class="sxs-lookup"><span data-stu-id="bcd27-561">Animated visual indicator, in the form of a progress bar or ring, showing progress during any data loading or processing.</span></span> <span data-ttu-id="bcd27-562">ビジュアルインジケーターは、待機時間の長さに関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-562">The visual indicator provides guidance on how long the wait could be.</span></span> | <span data-ttu-id="bcd27-563">ユーザーには、データの読み込みが進行中であることが通知されますが、待機時間を示すことはできません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-563">User is informed that data loading is in progress, but there is no indication of how long the wait could be.</span></span> | <span data-ttu-id="bcd27-564">タスクのデータ読み込みまたはプロセスインジケーターが5秒より長くかかっていません。</span><span class="sxs-lookup"><span data-stu-id="bcd27-564">No data loading or process indicators for task taking longer than 5 seconds.</span></span> |

### <a name="how-to-measure"></a><span data-ttu-id="bcd27-565">測定する方法</span><span class="sxs-lookup"><span data-stu-id="bcd27-565">How to measure</span></span>

* <span data-ttu-id="bcd27-566">データの読み込み中に、5秒を超える空の状態がないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-566">During data loading verify there is no blank state for more than 5 seconds.</span></span>

### <a name="recommendations"></a><span data-ttu-id="bcd27-567">推奨事項</span><span class="sxs-lookup"><span data-stu-id="bcd27-567">Recommendations</span></span>

* <span data-ttu-id="bcd27-568">ユーザーがこのアプリを停止またはクラッシュしていると認識した場合に、進行状況を示すデータ読み込みのアニメーターを提供します。</span><span class="sxs-lookup"><span data-stu-id="bcd27-568">Provide a data loading animator showing progress in any situation when the user may perceive this app to have stalled or crashed.</span></span> <span data-ttu-id="bcd27-569">目安として合理的なのは、5秒以上かかる可能性のある "読み込み" アクティビティです。</span><span class="sxs-lookup"><span data-stu-id="bcd27-569">A reasonable rule of thumb is any 'loading' activity that could take more than 5 seconds.</span></span>

### <a name="resources"></a><span data-ttu-id="bcd27-570">リソース</span><span class="sxs-lookup"><span data-stu-id="bcd27-570">Resources</span></span>

* [<span data-ttu-id="bcd27-571">進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="bcd27-571">Displaying progress</span></span>](../../design/progress.md)
