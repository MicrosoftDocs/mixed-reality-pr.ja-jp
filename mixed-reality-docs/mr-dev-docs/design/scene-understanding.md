---
title: シーンの理解
description: SDK、機能、一般的な使用シナリオなど、HoloLens のシーンを理解して開発する方法について説明します。
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: シーンの理解、空間マッピング、Windows Mixed Reality、Unity、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット、HoloLens、遮蔽、SDK
ms.openlocfilehash: c4485c5501300d6ca629f4e587fde1f88eea7ea5
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008872"
---
# <a name="scene-understanding"></a><span data-ttu-id="11c9a-104">シーンの理解</span><span class="sxs-lookup"><span data-stu-id="11c9a-104">Scene understanding</span></span>

<span data-ttu-id="11c9a-105">シーンについて理解することで、さまざまな環境に対応したアプリケーションの開発を直感的に行うことができるように設計された、構造化された高レベルの環境表現を利用できます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-105">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="11c9a-106">シーンを理解することは、これを実現するために、非常に精度が高く、構造化されていない [空間マッピング](spatial-mapping.md) や新しい AI 駆動型ランタイムなど、既存の mixed reality ランタイムの力を組み合わせることによって行われます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-106">Scene understanding does this by combining the power of existing mixed reality runtimes, like the highly accurate but less structured [spatial mapping](spatial-mapping.md) and new AI driven runtimes.</span></span> <span data-ttu-id="11c9a-107">これらのテクノロジを組み合わせることで、シーンの理解によって、Unity や ARKit/Arkit などのフレームワークで使用されているような3D 環境の表現が生成されます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-107">By combining these technologies, Scene understanding generates representations of 3D environments that are similar to those you may have used in frameworks such as Unity or ARKit/ARCore.</span></span> <span data-ttu-id="11c9a-108">シーン認識のエントリポイントは、シーンオブザーバーで始まります。これは、アプリケーションが新しいシーンを計算するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-108">The Scene understanding entry point begins with a Scene Observer, which is called by your application to compute a new scene.</span></span> <span data-ttu-id="11c9a-109">現在、テクノロジでは、次の3つの個別の関連オブジェクトカテゴリを生成できます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-109">Today, the technology can generate 3 distinct but related object categories:</span></span> 

* <span data-ttu-id="11c9a-110">単純化された watertight 環境メッシュ (乱雑されることなく平面の部屋構造を推論する)</span><span class="sxs-lookup"><span data-stu-id="11c9a-110">Simplified watertight environment meshes that infer the planar room structure without clutter</span></span>
* <span data-ttu-id="11c9a-111">四角形を呼び出す位置の平面領域</span><span class="sxs-lookup"><span data-stu-id="11c9a-111">Plane regions for placement that we call Quads</span></span>
* <span data-ttu-id="11c9a-112">サーフェイスに配置される四角形/Watertight データと一致する [空間マッピング](spatial-mapping.md) メッシュのスナップショット</span><span class="sxs-lookup"><span data-stu-id="11c9a-112">A snapshot of the [spatial mapping](spatial-mapping.md) mesh that aligns with the Quads/Watertight data that we surface</span></span>

![空間マッピングメッシュ, ラベル付き平面サーフェス, watertight メッシュ](images/SUScenarios.png)

<span data-ttu-id="11c9a-114">このドキュメントでは、シナリオの概要を説明し、シーンの理解と空間マッピングの共有の関係を明確にすることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="11c9a-114">This document is intended to provide a scenario overview and to clarify the relationship that Scene understanding and Spatial mapping share.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="11c9a-115">シーンの理解による開発</span><span class="sxs-lookup"><span data-stu-id="11c9a-115">Developing with Scene Understanding</span></span>

<span data-ttu-id="11c9a-116">この記事では、シーンの実行時と概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="11c9a-116">This article only serves to introduce the Scene Understanding runtime and concepts.</span></span> <span data-ttu-id="11c9a-117">シーンを理解して開発する方法に関するドキュメントをお探しの場合は、次の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11c9a-117">If you're looking for documentation on how to develop with Scene Understanding, you may be interested in the following articles:</span></span>

[<span data-ttu-id="11c9a-118">シーンについて SDK の概要</span><span class="sxs-lookup"><span data-stu-id="11c9a-118">Scene Understanding SDK overview</span></span>](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

<span data-ttu-id="11c9a-119">サンプルの GitHub サイトから、シーンについてのサンプルアプリをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-119">You can download the Scene Understanding Sample app from the sample GitHub site:</span></span>

[<span data-ttu-id="11c9a-120">シーンの理解のサンプル</span><span class="sxs-lookup"><span data-stu-id="11c9a-120">Scene Understanding Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

<span data-ttu-id="11c9a-121">デバイスがなく、サンプルシーンにアクセスしてシーンの理解を試す必要がある場合は、サンプルアセットフォルダーにシーンがあります。</span><span class="sxs-lookup"><span data-stu-id="11c9a-121">If you don't have a device and wish to access sample scenes to try Scene Understanding out, there are scenes in the sample asset folder:</span></span>

[<span data-ttu-id="11c9a-122">シーンについてのサンプルシーン</span><span class="sxs-lookup"><span data-stu-id="11c9a-122">Scene Understanding Sample Scenes</span></span>](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a><span data-ttu-id="11c9a-123">SDK</span><span class="sxs-lookup"><span data-stu-id="11c9a-123">SDK</span></span>

<span data-ttu-id="11c9a-124">シーンの理解による開発に関する具体的な詳細については、「シーンについての [SDK の概要](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11c9a-124">If you're looking for specific details on developing with Scene Understanding, see the [Scene Understanding SDK overview](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) documentation.</span></span>

### <a name="sample"></a><span data-ttu-id="11c9a-125">サンプル</span><span class="sxs-lookup"><span data-stu-id="11c9a-125">Sample</span></span>

## <a name="device-support"></a><span data-ttu-id="11c9a-126">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="11c9a-126">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="11c9a-127"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="11c9a-127"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="11c9a-128"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="11c9a-128"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="11c9a-129"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="11c9a-129"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="11c9a-130"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="11c9a-130"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="11c9a-131">シーンの理解</span><span class="sxs-lookup"><span data-stu-id="11c9a-131">Scene understanding</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="11c9a-132">✔️</span><span class="sxs-lookup"><span data-stu-id="11c9a-132">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a><span data-ttu-id="11c9a-133">一般的な利用シナリオ</span><span class="sxs-lookup"><span data-stu-id="11c9a-133">Common usage scenarios</span></span>

<span data-ttu-id="11c9a-134">![一般的な空間マッピングの使用シナリオの図: 配置、閉鎖、物理、およびナビゲーション](images/sm-concepts-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="11c9a-134">![Illustrations of common Spatial mapping usage scenarios: Placement, Occlusion, Physics and Navigation](images/sm-concepts-1000px.png)</span></span><br>
<span data-ttu-id="11c9a-135">*一般的な空間マッピングの使用シナリオ: 配置、遮蔽、物理、およびナビゲーション。*</span><span class="sxs-lookup"><span data-stu-id="11c9a-135">*Common spatial mapping usage scenarios: placement, occlusion, physics, and navigation.*</span></span>

<br>

<span data-ttu-id="11c9a-136">環境対応アプリケーションの主要なシナリオの多くは、空間マッピングとシーンの理解の両方で対処できます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-136">Many of the core scenarios for environmentally aware applications can be addressed by both Spatial mapping and Scene understanding.</span></span> <span data-ttu-id="11c9a-137">これらの主要なシナリオには、配置、閉鎖、物理などがあります。</span><span class="sxs-lookup"><span data-stu-id="11c9a-137">These core scenarios include placement, occlusion, physics, and so on.</span></span> <span data-ttu-id="11c9a-138">シーンの理解と空間マッピングの主な違いは、構造と簡潔さの最大の精度と待機時間のトレードオフです。</span><span class="sxs-lookup"><span data-stu-id="11c9a-138">A core difference between Scene understanding and Spatial mapping is a tradeoff of maximal accuracy and latency to structure and simplicity.</span></span> <span data-ttu-id="11c9a-139">アプリケーションで、可能な限り最短の待機時間とメッシュのトライアングルを必要とする場合は、空間マッピングを直接使用します。</span><span class="sxs-lookup"><span data-stu-id="11c9a-139">If your application requires the lowest-latency possible and mesh triangles that only you'll want to access, use Spatial Mapping directly.</span></span> <span data-ttu-id="11c9a-140">上位レベルの処理を実行している場合は、機能のスーパーセットを提供する必要があるため、シーンを理解するモデルに切り替えることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="11c9a-140">If you're doing higher-level processing, you may consider switching to the Scene understanding model as it should provide you with a superset of functionality.</span></span> <span data-ttu-id="11c9a-141">シーンの理解により、空間マッピングメッシュのスナップショットが表現の一部として提供されるため、可能な限り完全かつ正確な空間マッピングデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-141">You'll always have access to the most complete and accurate spatial mapping data possible because Scene understanding provides a snapshot of the spatial mapping mesh as part of its representation.</span></span>

<span data-ttu-id="11c9a-142">次のセクションでは、新しいシーンの概要 SDK のコンテキストでの主要な空間マッピングのシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="11c9a-142">The following sections revisit the core spatial mapping scenarios in the context of the new Scene understanding SDK.</span></span>

### <a name="placement"></a><span data-ttu-id="11c9a-143">配置</span><span class="sxs-lookup"><span data-stu-id="11c9a-143">Placement</span></span>

<span data-ttu-id="11c9a-144">シーンの理解により、配置シナリオを簡略化するための新しい構成要素が提供されます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-144">Scene understanding provides new constructs designed to simplify placement scenarios.</span></span> <span data-ttu-id="11c9a-145">シーンでは、SceneQuads と呼ばれるプリミティブを計算できます。これは、ホログラムを配置できるフラットなサーフェスを表します。</span><span class="sxs-lookup"><span data-stu-id="11c9a-145">A scene can compute primitives called SceneQuads, which describe flat surfaces on which holograms can be placed.</span></span> <span data-ttu-id="11c9a-146">SceneQuads は、配置を中心に設計され、2D サーフェイスを記述し、そのサーフェイス上に配置するための API を提供しています。</span><span class="sxs-lookup"><span data-stu-id="11c9a-146">SceneQuads have been designed around placement and describe a 2D surface and provide an API for placement on that surface.</span></span> <span data-ttu-id="11c9a-147">以前は、トライアングルメッシュを使用して配置を行う場合、4つの部分をスキャンし、穴の塗りつぶし/後処理を実行して、オブジェクトの配置の適切な場所を識別する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="11c9a-147">Previously, when using the triangle mesh to do placement, one had to scan all areas of the quad and do hole filling/post-processing to identify good locations for object placement.</span></span> <span data-ttu-id="11c9a-148">これは、四角形では常に必要ではありません。シーンを理解すると、スキャンされていないクワッド領域が推測され、サーフェイスの一部ではない領域が無効になります。</span><span class="sxs-lookup"><span data-stu-id="11c9a-148">This isn't always necessary with Quads, as the Scene understanding runtime infers which quad areas weren't scanned, and invalidate areas that aren't part of the surface.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="11c9a-149">![推定が無効になっている SceneQuads。スキャンされたリージョンの配置領域をキャプチャします。](images/SUQuads.png)</span><span class="sxs-lookup"><span data-stu-id="11c9a-149">![SceneQuads with inference disabled, capturing placement areas for scanned regions.](images/SUQuads.png)</span></span><br>
       <span data-ttu-id="11c9a-150">**イメージ #1** -推定を無効にし、スキャンされたリージョンの配置領域をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="11c9a-150">**Image #1** - SceneQuads with inference disabled, capturing placement areas for scanned regions.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="11c9a-151">![推論が有効になっている四角形は、スキャンされた領域に限定されなくなりました。](images/SUWatertight.png)</span><span class="sxs-lookup"><span data-stu-id="11c9a-151">![Quads with inference enabled, placement is no longer limited to scanned areas.](images/SUWatertight.png)</span></span><br>
        <span data-ttu-id="11c9a-152">**イメージ #2** -推論が有効になっている四角形、配置はスキャンされた領域に限定されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="11c9a-152">**Image #2** - Quads with inference enabled, placement is no longer limited to scanned areas.</span></span>
    :::column-end:::
:::row-end:::

<br>


<span data-ttu-id="11c9a-153">アプリケーションで、環境の固定構造に2D または3D のホログラムを配置する場合は、 [空間マッピング](spatial-mapping.md) メッシュからこの情報を計算することをお勧めします。これにより、配置のための SceneQuads の簡略化と利便性が向上します。</span><span class="sxs-lookup"><span data-stu-id="11c9a-153">If your application intends to place 2D or 3D holograms on rigid structures of your environment, the simplicity and convenience of SceneQuads for placement is preferable to computing this information from the [spatial mapping](spatial-mapping.md) mesh.</span></span> <span data-ttu-id="11c9a-154">このトピックの詳細については、「シーンについての[SDK リファレンス](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="11c9a-154">For more information on this topic, see the [Scene understanding SDK reference](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)</span></span>

<span data-ttu-id="11c9a-155">**メモ** 空間マッピングメッシュに依存するレガシ配置コードの場合、EnableWorldMesh 設定を設定することによって、空間マッピングメッシュを SceneQuads と共に計算できます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-155">**Note** For legacy placement code that depends on the spatial mapping mesh, the spatial mapping mesh can be computed along with SceneQuads by setting EnableWorldMesh setting.</span></span> <span data-ttu-id="11c9a-156">シーン認識 API がアプリケーションの待機時間の要件を満たしていない場合は、引き続き [空間マッピング api](spatial-mapping.md#placement)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="11c9a-156">If Scene understanding API doesn't satisfy your application's latency requirements, we recommend you continue to use the [Spatial mapping API](spatial-mapping.md#placement).</span></span>

### <a name="occlusion"></a><span data-ttu-id="11c9a-157">オクルージョン</span><span class="sxs-lookup"><span data-stu-id="11c9a-157">Occlusion</span></span>

<span data-ttu-id="11c9a-158">[空間マッピングオクルージョン](spatial-mapping.md#occlusion) は、環境のリアルタイム状態をキャプチャするための最も低い方法にとどまります。</span><span class="sxs-lookup"><span data-stu-id="11c9a-158">[Spatial mapping occlusion](spatial-mapping.md#occlusion) remains the least latent way to capture the real-time state of the environment.</span></span> <span data-ttu-id="11c9a-159">これは、高度に動的なシーンで遮蔽を提供するのに便利な場合がありますが、いくつかの理由から、遮蔽のシーンの理解を考慮することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="11c9a-159">Though this may be useful to provide occlusion in highly dynamic scenes, you may wish to consider Scene understanding for occlusion for several reasons.</span></span> <span data-ttu-id="11c9a-160">シーンの理解によって生成された空間マッピングメッシュを使用する場合は、ローカルキャッシュに格納されておらず、認識 Api からは使用できない空間マッピングからデータを要求できます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-160">If you use the spatial mapping mesh generated by Scene Understanding, you can request data from spatial mapping that wouldn't be stored in the local cache and isn't available from the perception APIs.</span></span> <span data-ttu-id="11c9a-161">Watertight メッシュと共にオクルージョンに空間マッピングを使用すると、余分な値が提供され、特に unscanned 室構造が完成します。</span><span class="sxs-lookup"><span data-stu-id="11c9a-161">Using Spatial Mapping for occlusion alongside watertight meshes will provide extra value, specifically completion of unscanned room structure.</span></span>

<span data-ttu-id="11c9a-162">シーンの理解の待機時間の増加に合わせて要件が許容される場合、アプリケーション開発者は、シーンについて理解する watertight メッシュと、空間マッピングメッシュを平面表現と連携させることを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11c9a-162">If your requirements can tolerate the increased latency of Scene understanding, application developers should consider using the Scene understanding watertight mesh, and the spatial mapping mesh in unison with planar representations.</span></span> <span data-ttu-id="11c9a-163">これにより、簡略化された watertight オクルージョンが最も現実的なオクルージョンマップを提供する、より細かい nonplanar geometry を持つ、"両方のワールドに最適" のシナリオが提供されます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-163">This would provide a "best of both worlds" scenario where simplified watertight occlusion is married with finer nonplanar geometry providing the most realistic occlusion maps possible.</span></span>

### <a name="physics"></a><span data-ttu-id="11c9a-164">物理計算</span><span class="sxs-lookup"><span data-stu-id="11c9a-164">Physics</span></span>

<span data-ttu-id="11c9a-165">シーンの理解によって、空間がセマンティクスで分解される watertight メッシュが生成されます。特に、空間マッピングのメッシュによって適用される物理的な多くの制限に対処します。</span><span class="sxs-lookup"><span data-stu-id="11c9a-165">Scene understanding generates watertight meshes that decompose space with semantics, specifically to address many limitations to physics that spatial mapping meshes impose.</span></span> <span data-ttu-id="11c9a-166">Watertight 構造体は、物理的な光のキャストを常にヒットさせると共に、セマンティック分解によって、室内ナビゲーションのナビゲーションメッシュをより簡単に生成できます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-166">Watertight structures ensure physics ray casts always hit, and semantic decomposition allows for simpler generation of nav meshes for indoor navigation.</span></span> <span data-ttu-id="11c9a-167">[オクルージョン](#occlusion)のセクションで説明したように、EnableSceneObjectMeshes と EnableWorldMesh を使用してシーンを作成すると、最も物理的に完全なメッシュが可能になります。</span><span class="sxs-lookup"><span data-stu-id="11c9a-167">As described in the section on [occlusion](#occlusion), creating a scene with EnableSceneObjectMeshes and EnableWorldMesh will produce the most physically complete mesh possible.</span></span> <span data-ttu-id="11c9a-168">環境メッシュの watertight プロパティによって、ヒットテストがサーフェイスのヒットに失敗するのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-168">The watertight property of the environment mesh prevents hit tests from failing to hit surfaces.</span></span> <span data-ttu-id="11c9a-169">メッシュデータを使用すると、物理的なものは、部屋構造だけでなく、シーン内のすべてのオブジェクトと対話します。</span><span class="sxs-lookup"><span data-stu-id="11c9a-169">The mesh data will ensure physics are interacting with all objects in the scene and not just the room structure.</span></span>

### <a name="navigation"></a><span data-ttu-id="11c9a-170">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="11c9a-170">Navigation</span></span>

<span data-ttu-id="11c9a-171">セマンティッククラスによって分解された平面メッシュは、ナビゲーションとパスの計画に最適な構成要素であり、「 [空間マッピングのナビゲーション](spatial-mapping.md#navigation) の概要」で説明されている多くの問題を緩和します。</span><span class="sxs-lookup"><span data-stu-id="11c9a-171">Planar meshes decomposed by semantic class are ideal constructs for navigation and path planning, easing many of the issues described in the [Spatial mapping navigation](spatial-mapping.md#navigation) overview.</span></span> <span data-ttu-id="11c9a-172">シーンで計算された SceneMesh オブジェクトは、表面の種類によって構成解除されます。これにより、ナビゲーションメッシュの生成が、ウォーク可能なサーフェイスに限定されます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-172">The SceneMesh objects computed in the scene are de-composed by surface type ensuring that nav-mesh generation is limited to surfaces that can be walked on.</span></span> <span data-ttu-id="11c9a-173">フロア構造の単純さにより、Unity などの3d エンジンでの動的なナビゲーションメッシュの生成は、リアルタイムの要件に応じて達成できます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-173">Because of the floor structures' simplicity, dynamic nav-mesh generation in 3d engines such as Unity are attainable depending on real-time requirements.</span></span>

<span data-ttu-id="11c9a-174">現在のところ、正確な nav メッシュを生成するには後処理が必要です。つまり、アプリケーションでは、occluders をフロアに射影して、移動が乱雑な/テーブルを通過しないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="11c9a-174">Generating accurate nav-meshes currently still requires post-processing, namely applications must still project occluders on to the floor to ensure that navigation doesn't pass through clutter/tables and so on.</span></span> <span data-ttu-id="11c9a-175">これを実現する最も正確な方法は、ワールドメッシュデータを投影することです。これは、EnableWorldMesh フラグを使用してシーンが計算された場合に提供されます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-175">The most accurate way to accomplish this is to project the world mesh data, which is provided if the scene is computed with the EnableWorldMesh flag.</span></span>

### <a name="visualization"></a><span data-ttu-id="11c9a-176">視覚化</span><span class="sxs-lookup"><span data-stu-id="11c9a-176">Visualization</span></span>

<span data-ttu-id="11c9a-177">[空間マッピングの視覚化](spatial-mapping.md#visualization)を使用して、環境のリアルタイムのフィードバックを行うことができますが、平面オブジェクトと watertight オブジェクトの単純化によってパフォーマンスや視覚品質が向上する多くのシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="11c9a-177">While [spatial mapping visualization](spatial-mapping.md#visualization) can be used for real-time feedback of the environment, there are many scenarios where the simplicity of planar and watertight objects provides more performance or visual quality.</span></span> <span data-ttu-id="11c9a-178">四角形または平面 watertight メッシュによって提供される平面サーフェスに射影した場合、空間マッピングを使用して記述されているシャドウプロジェクションとアース手法は、より見栄えが良い場合があります。</span><span class="sxs-lookup"><span data-stu-id="11c9a-178">Shadow projection and grounding techniques that are described using spatial mapping may be more pleasing if projected on the planar surfaces provided by Quads or the planar watertight mesh.</span></span> <span data-ttu-id="11c9a-179">これは、シーンが推測されるため、完全な事前スキャンが最適ではない環境やシナリオでは特に当てはまり、完全な環境と平面の前提条件によって成果物が最小化されます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-179">This is especially true for environments/scenarios where thorough pre-scanning isn't optimal because the scene will infer, and complete environments and planar assumptions will minimize artifacts.</span></span>

<span data-ttu-id="11c9a-180">さらに、空間マッピングによって返されるサーフェスの合計数は、内部空間キャッシュによって制限されます。一方、シーン認識のバージョンの空間マッピングメッシュは、キャッシュされていない空間マッピングデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="11c9a-180">Additionally, the total number of surfaces returned by Spatial Mapping is limited by the internal spatial cache, while Scene understanding's version of the Spatial Mapping mesh can access spatial mapping data that isn't cached.</span></span> <span data-ttu-id="11c9a-181">このため、シーンを理解することは、視覚エフェクトやさらにメッシュ処理を行うために、より大きなスペース (たとえば、1つの部屋を超える) のメッシュ表現をキャプチャする場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="11c9a-181">Because of this, Scene understanding is more suited to capturing mesh representations for larger spaces (for example, larger than a single room) for visualization or further mesh processing.</span></span> <span data-ttu-id="11c9a-182">EnableWorldMesh で返されるワールドメッシュの詳細レベルは、全体にわたって一貫しています。これにより、ワイヤーフレームとしてレンダリングした場合により良い視覚化が得られる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="11c9a-182">The world mesh returned with EnableWorldMesh will have a consistent level of detail throughout, which may yield a more pleasing visualization if rendered as wireframe.</span></span>

### <a name="see-also"></a><span data-ttu-id="11c9a-183">参照</span><span class="sxs-lookup"><span data-stu-id="11c9a-183">See Also</span></span>

* [<span data-ttu-id="11c9a-184">シーンを理解する SDK</span><span class="sxs-lookup"><span data-stu-id="11c9a-184">Scene understanding SDK</span></span>](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [<span data-ttu-id="11c9a-185">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="11c9a-185">Spatial mapping</span></span>](spatial-mapping.md)
