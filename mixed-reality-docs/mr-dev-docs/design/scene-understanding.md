---
title: シーンの理解
description: HoloLens のシーンと機能の概要
author: szymons
ms.author: szymons
ms.date: 07/08/2019
ms.topic: article
keywords: シーンの理解、空間マッピング、Windows Mixed Reality、Unity、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual Reality ヘッドセット、HoloLens、遮蔽、SDK
ms.openlocfilehash: 80fb01707d3265aa3dac23d75ea92034115d3c94
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703368"
---
# <a name="scene-understanding"></a><span data-ttu-id="e13b0-104">シーンの理解</span><span class="sxs-lookup"><span data-stu-id="e13b0-104">Scene understanding</span></span>

<span data-ttu-id="e13b0-105">シーンについて理解することで、さまざまな環境に対応したアプリケーションの開発を直感的に行うことができるように設計された、構造化された高レベルの環境表現を利用できます。</span><span class="sxs-lookup"><span data-stu-id="e13b0-105">Scene understanding provides Mixed Reality developers with a structured, high-level environment representation designed to make developing for environmentally aware applications intuitive.</span></span> <span data-ttu-id="e13b0-106">シーンを理解することは、これを実現するために、複雑ではない構造化された [空間マッピング](spatial-mapping.md) や新しい AI 駆動型ランタイムなど、既存の mixed reality ランタイムの力を組み合わせることになります。</span><span class="sxs-lookup"><span data-stu-id="e13b0-106">Scene understanding does this by combining the power of existing mixed reality runtimes, such as the highly accurate less structured [spatial mapping](spatial-mapping.md) and new AI driven runtimes.</span></span> <span data-ttu-id="e13b0-107">これらのテクノロジを組み合わせることで、シーンの理解によって、Unity や ARKit/Arkit などのフレームワークで使用されているような3D 環境の表現が生成されます。</span><span class="sxs-lookup"><span data-stu-id="e13b0-107">By combining these technologies, Scene understanding generates representations of 3D environments that are similar to those you may have used in frameworks such as Unity or ARKit/ARCore.</span></span> <span data-ttu-id="e13b0-108">シーン認識のエントリポイントは、シーンオブザーバーで始まります。これは、アプリケーションが新しいシーンを計算するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e13b0-108">The Scene understanding entry point begins with a Scene Observer, which is called by your application to compute a new scene.</span></span> <span data-ttu-id="e13b0-109">現在、このテクノロジは、3つの独立した関連オブジェクトカテゴリを生成することができます。単純化された watertight 環境メッシュでは、複雑な部分を除いて、平面の部屋構造を推測します。また、四角形を呼び出す位置には平面領域を使用し、 [空間マッピング](spatial-mapping.md) メッシュのスナップショットを作成します。</span><span class="sxs-lookup"><span data-stu-id="e13b0-109">Today, the technology is capable of generating 3 distinct but related object categories: simplified watertight environment meshes that infer the planar room structure without clutter, plane regions for placement that we call Quads, and a snapshot of the [spatial mapping](spatial-mapping.md) mesh that aligns with the Quads/Watertight data that we surface.</span></span>

![空間マッピングメッシュ, ラベル付き平面サーフェス, watertight メッシュ](images/SUScenarios.png)

<span data-ttu-id="e13b0-111">このドキュメントでは、シナリオの概要を説明し、シーンの理解と空間マッピングの共有の関係を明確にすることを目的としています。</span><span class="sxs-lookup"><span data-stu-id="e13b0-111">This document is intended to provide a scenario overview and to clarify the relationship that Scene understanding and Spatial mapping share.</span></span>

## <a name="developing-with-scene-understanding"></a><span data-ttu-id="e13b0-112">シーンの理解による開発</span><span class="sxs-lookup"><span data-stu-id="e13b0-112">Developing with Scene Understanding</span></span>

<span data-ttu-id="e13b0-113">この記事では、シーンの実行時と概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="e13b0-113">This article only serves to introduce the Scene Understanding runtime and concepts.</span></span> <span data-ttu-id="e13b0-114">シーンを理解して開発する方法に関するドキュメントをお探しの場合は、次のことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e13b0-114">If you are looking for documentation on how to develop with Scene Understanding, you may be interested in the following:</span></span>

[<span data-ttu-id="e13b0-115">シーンについて SDK の概要</span><span class="sxs-lookup"><span data-stu-id="e13b0-115">Scene Understanding SDK overview</span></span>](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)

<span data-ttu-id="e13b0-116">サンプルの GitHub サイトから、シーンについてのサンプルアプリをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="e13b0-116">You can download the Scene Understanding Sample app from the sample GitHub site:</span></span>

[<span data-ttu-id="e13b0-117">シーンの理解のサンプル</span><span class="sxs-lookup"><span data-stu-id="e13b0-117">Scene Understanding Sample</span></span>](https://github.com/microsoft/MixedReality-SceneUnderstanding-Samples)

<span data-ttu-id="e13b0-118">デバイスがなく、サンプルシーンにアクセスしてシーンの理解を試す必要がある場合は、サンプルアセットフォルダーにシーンがあります。</span><span class="sxs-lookup"><span data-stu-id="e13b0-118">If you do not have a device and wish to access sample scenes to try Scene Understanding out, there are scenes in the sample asset folder:</span></span>

[<span data-ttu-id="e13b0-119">シーンについてのサンプルシーン</span><span class="sxs-lookup"><span data-stu-id="e13b0-119">Scene Understanding Sample Scenes</span></span>](https://github.com/sceneunderstanding-microsoft/unitysample/tree/master/Assets/Resources/SerializedScenesForPCPath)

### <a name="sdk"></a><span data-ttu-id="e13b0-120">SDK</span><span class="sxs-lookup"><span data-stu-id="e13b0-120">SDK</span></span>

<span data-ttu-id="e13b0-121">シーンを理解するための開発方法や、シーンの理解のしくみとその開発方法の詳細については、「 [シーンについて SDK の概要](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e13b0-121">If you are looking for specific details on how to develop for Scene Understanding or details on how Scene understanding works and how to develop for it, see the [Scene Understanding SDK overview](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md) documentation.</span></span>


### <a name="sample"></a><span data-ttu-id="e13b0-122">サンプル</span><span class="sxs-lookup"><span data-stu-id="e13b0-122">Sample</span></span>


## <a name="device-support"></a><span data-ttu-id="e13b0-123">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="e13b0-123">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="e13b0-124"><strong>機能</strong></span><span class="sxs-lookup"><span data-stu-id="e13b0-124"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="e13b0-125"><a href="../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="e13b0-125"><a href="../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="e13b0-126"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="e13b0-126"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="e13b0-127"><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="e13b0-127"><a href="../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="e13b0-128">シーンの理解</span><span class="sxs-lookup"><span data-stu-id="e13b0-128">Scene understanding</span></span></td>
        <td>❌</td>
        <td><span data-ttu-id="e13b0-129">✔️</span><span class="sxs-lookup"><span data-stu-id="e13b0-129">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="common-usage-scenarios"></a><span data-ttu-id="e13b0-130">一般的な利用シナリオ</span><span class="sxs-lookup"><span data-stu-id="e13b0-130">Common usage scenarios</span></span>

<span data-ttu-id="e13b0-131">![一般的な空間マッピングの使用シナリオの図: 配置、閉鎖、物理、およびナビゲーション](images/sm-concepts-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="e13b0-131">![Illustrations of common Spatial mapping usage scenarios: Placement, Occlusion, Physics and Navigation](images/sm-concepts-1000px.png)</span></span><br>
<span data-ttu-id="e13b0-132">*一般的な空間マッピングの使用シナリオ: 配置、遮蔽、物理、およびナビゲーション。*</span><span class="sxs-lookup"><span data-stu-id="e13b0-132">*Common spatial mapping usage scenarios: placement, occlusion, physics and navigation.*</span></span>

<br>

<span data-ttu-id="e13b0-133">環境に対応するアプリケーション (配置、閉鎖、物理など) の主要なシナリオの多くは、空間マッピングとシーンの理解の両方でアドレス指定できます。このセクションでは、これらの違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e13b0-133">Many of the core scenarios for environment aware applications (placement, occlusion, physics, etc.) are addressable by both Spatial mapping and Scene understanding, and this section highlights these differences.</span></span> <span data-ttu-id="e13b0-134">シーンの理解と空間マッピングの主な違いは、構造と簡潔さの最大の精度と待機時間のトレードオフです。</span><span class="sxs-lookup"><span data-stu-id="e13b0-134">A core difference between Scene understanding and Spatial mapping is a tradeoff of maximal accuracy and latency to structure and simplicity.</span></span> <span data-ttu-id="e13b0-135">アプリケーションで、可能な限り最短の待機時間とメッシュトライアングルを必要とする場合は、空間マッピングを直接使用します。</span><span class="sxs-lookup"><span data-stu-id="e13b0-135">If your application requires the lowest-latency possible and mesh triangles that only you will want to access, use Spatial Mapping directly.</span></span> <span data-ttu-id="e13b0-136">より高いレベルの処理を実行している場合は、機能のスーパーセットを提供する必要があるため、シーンを理解するモデルに切り替えることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="e13b0-136">If you are performing higher level processing, you may consider switching to the Scene understanding model as it should provide you with a superset of functionality.</span></span> <span data-ttu-id="e13b0-137">また、シーンの理解により、空間マッピングメッシュのスナップショットが表現の一部として提供されるため、可能な限り完全かつ正確な空間マッピングデータに常にアクセスできることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e13b0-137">Also note that because Scene understanding provides a snapshot of the spatial mapping mesh as part of its representation, you will always have access to the most complete and accurate spatial mapping data possible.</span></span>

<span data-ttu-id="e13b0-138">次のセクションでは、新しいシーンの概要 SDK のコンテキストにおける主要な空間マッピングのシナリオについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e13b0-138">The following sections re-visit the core spatial mapping scenarios in the context of the new Scene understanding SDK.</span></span>

### <a name="placement"></a><span data-ttu-id="e13b0-139">配置</span><span class="sxs-lookup"><span data-stu-id="e13b0-139">Placement</span></span>

<span data-ttu-id="e13b0-140">シーンの理解は、配置シナリオを簡略化するために特別に設計された新しい構造を提供します。</span><span class="sxs-lookup"><span data-stu-id="e13b0-140">Scene understanding provides new constructs specifically designed to simplify placement scenarios.</span></span> <span data-ttu-id="e13b0-141">シーンでは、ホログラムを配置できるフラットサーフェスを記述する SceneQuads と呼ばれるプリミティブを計算できます。</span><span class="sxs-lookup"><span data-stu-id="e13b0-141">A scene can compute primitives called SceneQuads which describe flat surfaces on which holograms can be placed.</span></span> <span data-ttu-id="e13b0-142">SceneQuads は、特に配置を中心に設計されており、2D サーフェイスを記述し、そのサーフェイス上に配置するための API を提供しています。</span><span class="sxs-lookup"><span data-stu-id="e13b0-142">SceneQuads have specifically been designed around placement and describe a 2D surface and provide an API for placement on that surface.</span></span> <span data-ttu-id="e13b0-143">以前は、トライアングルメッシュを使用して配置を実行する場合、オブジェクトの配置の適切な場所を識別するために、クワッドのすべての領域をスキャンし、穴の塗りつぶし/後処理を実行する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="e13b0-143">Previously, when using the triangle mesh to perform placement, one had to scan all areas of the quad and perform hole filling/post-processing to identify good locations for object placement.</span></span> <span data-ttu-id="e13b0-144">これは、四角形では常に必要となるわけではありません。これは、実行時には、スキャンされなかったクワッドの領域を推定することができ、サーフェイスの一部ではない四角形の領域を無効にすることができるためです。</span><span class="sxs-lookup"><span data-stu-id="e13b0-144">This is not always necessary with Quads, as the Scene understanding runtime is capable of inferring which areas of the quad that were not scanned, and invalidate areas of the quad that are not part of the surface.</span></span>

:::row:::
    :::column:::
       <span data-ttu-id="e13b0-145">![推定が無効になっている SceneQuads。スキャンされたリージョンの配置領域をキャプチャします。](images/SUQuads.png)</span><span class="sxs-lookup"><span data-stu-id="e13b0-145">![SceneQuads with inference disabled, capturing placement areas for scanned regions.](images/SUQuads.png)</span></span><br>
       <span data-ttu-id="e13b0-146">**イメージ #1** -推定を無効にし、スキャンされたリージョンの配置領域をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="e13b0-146">**Image #1** - SceneQuads with inference disabled, capturing placement areas for scanned regions.</span></span>
    :::column-end:::
        :::column:::
       <span data-ttu-id="e13b0-147">![推論が有効になっている四角形は、スキャンされた領域に限定されなくなりました。](images/SUWatertight.png)</span><span class="sxs-lookup"><span data-stu-id="e13b0-147">![Quads with inference enabled, placement is no longer limited to scanned areas.](images/SUWatertight.png)</span></span><br>
        <span data-ttu-id="e13b0-148">**イメージ #2** -推論が有効になっている四角形、配置はスキャンされた領域に限定されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="e13b0-148">**Image #2** - Quads with inference enabled, placement is no longer limited to scanned areas.</span></span>
    :::column-end:::
:::row-end:::

<br>


<span data-ttu-id="e13b0-149">アプリケーションで、環境の固定構造に2D または3D のホログラムを配置する場合は、 [空間マッピング](spatial-mapping.md) メッシュからこの情報を計算することをお勧めします。これにより、配置のための SceneQuads の簡略化と利便性が向上します。</span><span class="sxs-lookup"><span data-stu-id="e13b0-149">If your application intends to place 2D or 3D holograms on rigid structures of your environment, the simplicity and convenience of SceneQuads for placement is preferable to computing this information from the [spatial mapping](spatial-mapping.md) mesh.</span></span> <span data-ttu-id="e13b0-150">このトピックの詳細については、「[シーンについての SDK リファレンス](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e13b0-150">For more details on this topic, please see the [Scene understanding SDK reference](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)</span></span>

<span data-ttu-id="e13b0-151">**メモ** 空間マッピングメッシュに依存するレガシ配置コードの場合、EnableWorldMesh 設定を設定することによって、空間マッピングメッシュを SceneQuads と共に計算できます。</span><span class="sxs-lookup"><span data-stu-id="e13b0-151">**Note** For legacy placement code that depends on the spatial mapping mesh, the spatial mapping mesh can be computed along with SceneQuads by setting EnableWorldMesh setting.</span></span> <span data-ttu-id="e13b0-152">シーンを理解する API がアプリケーションの待機時間の要件を満たしていない場合は、引き続き [空間マッピング api](spatial-mapping.md#placement)を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e13b0-152">If Scene understanding API does not satisfy your application's latency requirements, we recommend you continue to use the [Spatial mapping API](spatial-mapping.md#placement).</span></span>

### <a name="occlusion"></a><span data-ttu-id="e13b0-153">オクルージョン</span><span class="sxs-lookup"><span data-stu-id="e13b0-153">Occlusion</span></span>

<span data-ttu-id="e13b0-154">[空間マッピングオクルージョン](spatial-mapping.md#occlusion) は、環境のリアルタイム状態をキャプチャするための最も低い方法にとどまります。</span><span class="sxs-lookup"><span data-stu-id="e13b0-154">[Spatial mapping occlusion](spatial-mapping.md#occlusion) remains the least latent way to capture the real-time state of the environment.</span></span> <span data-ttu-id="e13b0-155">これは、高度に動的なシーンで遮蔽を提供するのに便利な場合がありますが、いくつかの理由から、遮蔽のシーンの理解を考慮することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e13b0-155">Though this may be useful to provide occlusion in highly dynamic scenes, you may wish to consider Scene understanding for occlusion for several reasons.</span></span> <span data-ttu-id="e13b0-156">シーンの理解によって生成された空間マッピングメッシュを使用する場合は、ローカルキャッシュに格納されないため、認識 Api からは使用できない空間マッピングからデータを要求できます。</span><span class="sxs-lookup"><span data-stu-id="e13b0-156">If you use the spatial mapping mesh generated by Scene Understanding, you can request data from spatial mapping that would not be stored in the local cache and therefore not available to you from the perception APIs.</span></span> <span data-ttu-id="e13b0-157">Watertight メッシュと共に遮蔽に空間マッピングを使用すると、追加の値が提供されます。特に、スキャンされていない部屋の構造が完了します。</span><span class="sxs-lookup"><span data-stu-id="e13b0-157">Using Spatial Mapping for occlusion alongside watertight meshes will provide additional value, specifically completion of un-scanned room structure.</span></span>

<span data-ttu-id="e13b0-158">シーンの理解の待機時間の増加に合わせて要件が許容できる場合、アプリケーション開発者は、シーンについて理解する watertight メッシュを使用することを検討する必要があります。また、空間マッピングメッシュは平面表現と連携していると考えられます。</span><span class="sxs-lookup"><span data-stu-id="e13b0-158">If your requirements can tolerate the increased latency of Scene understanding, application developers should consider using the Scene understanding watertight mesh, and presumably the spatial mapping mesh in unison with planar representations.</span></span> <span data-ttu-id="e13b0-159">これにより、簡略化された watertight オクルージョンが最も現実的なオクルージョンマップを提供する、より細かい nonplanar geometry を持つ、"両方のワールドに最適" のシナリオが提供されます。</span><span class="sxs-lookup"><span data-stu-id="e13b0-159">This would provide a "best of both worlds" scenario where simplified watertight occlusion is married with finer nonplanar geometry providing the most realistic occlusion maps possible.</span></span>

### <a name="physics"></a><span data-ttu-id="e13b0-160">物理計算</span><span class="sxs-lookup"><span data-stu-id="e13b0-160">Physics</span></span>

<span data-ttu-id="e13b0-161">シーンの理解によって、空間がセマンティクスで分解される watertight メッシュが生成されます。特に、空間マッピングのメッシュによって適用される物理的な多くの制限に対処します。</span><span class="sxs-lookup"><span data-stu-id="e13b0-161">Scene understanding generates watertight meshes that decompose space with semantics, specifically to address many limitations to physics that spatial mapping meshes impose.</span></span> <span data-ttu-id="e13b0-162">Watertight 構造体は、物理的な光のキャストを常にヒットさせると共に、セマンティック分解によって、室内ナビゲーションのナビゲーションメッシュをより簡単に生成できます。</span><span class="sxs-lookup"><span data-stu-id="e13b0-162">Watertight structures ensure physics ray casts always hit, and semantic decomposition allows for simpler generation of nav meshes for indoor navigation.</span></span> <span data-ttu-id="e13b0-163">[オクルージョン](#occlusion)のセクションで説明したように、EnableSceneObjectMeshes と EnableWorldMesh を使用してシーンを作成すると、最も物理的に完全なメッシュが可能になります。</span><span class="sxs-lookup"><span data-stu-id="e13b0-163">As described in the section on [occlusion](#occlusion), creating a scene with EnableSceneObjectMeshes and EnableWorldMesh will produce the most physically complete mesh possible.</span></span> <span data-ttu-id="e13b0-164">環境メッシュの watertight プロパティを使用すると、ヒットテストがサーフェイスのヒットに失敗するのを防ぐことができます。また、メッシュデータは、領域構造だけでなく、シーン内のすべてのオブジェクトと対話することを保証します。</span><span class="sxs-lookup"><span data-stu-id="e13b0-164">The watertight property of the environment mesh will prevent hit tests from failing to hit surfaces and the mesh data will ensure that physics are interacting with all objects in the scene and not just the room structure.</span></span>

### <a name="navigation"></a><span data-ttu-id="e13b0-165">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="e13b0-165">Navigation</span></span>

<span data-ttu-id="e13b0-166">セマンティッククラスによって分解された平面メッシュは、ナビゲーションとパスの計画に最適な構成要素であり、「 [空間マッピングのナビゲーション](spatial-mapping.md#navigation) の概要」で説明されている多くの問題を緩和します。</span><span class="sxs-lookup"><span data-stu-id="e13b0-166">Planar meshes decomposed by semantic class are ideal constructs for navigation and path planning, easing many of the issues described in the [Spatial mapping navigation](spatial-mapping.md#navigation) overview.</span></span> <span data-ttu-id="e13b0-167">シーンで計算された SceneMesh オブジェクトは、既に表面の種類によって構成解除されており、ナビゲーションメッシュの生成が、ウォーク可能なサーフェイスに限定されます。</span><span class="sxs-lookup"><span data-stu-id="e13b0-167">The SceneMesh objects computed in the scene are already de-composed by surface type ensuring that nav-mesh generation is limited to surfaces that can be walked on.</span></span> <span data-ttu-id="e13b0-168">フロア構造は単純であるため、Unity などの3d エンジンでの動的ナビゲーションメッシュ生成は、リアルタイムの要件に応じて達成できます。</span><span class="sxs-lookup"><span data-stu-id="e13b0-168">Due to the simplicity of the floor structure, dynamic nav-mesh generation in 3d engines such as Unity are attainable depending on real-time requirements.</span></span>

<span data-ttu-id="e13b0-169">現在でも正確なナビゲーションメッシュを生成するには後処理が必要です。つまり、アプリケーションでは、移動が乱雑またはテーブルを通過しないように、フロアに occluders を投影する必要があります。これを実現する最も正確な方法は、EnableWorldMesh フラグを使用してシーンが計算された場合に提供される世界のメッシュデータを射影することです。</span><span class="sxs-lookup"><span data-stu-id="e13b0-169">Generating accurate nav-meshes currently still requires post-processing, namely applications must still project occluders on to the floor to ensure that navigation does not pass through clutter/tables etc... The most accurate way to accomplish this is to project the world mesh data which is provided if the scene is computed with the EnableWorldMesh flag.</span></span>

### <a name="visualization"></a><span data-ttu-id="e13b0-170">視覚化</span><span class="sxs-lookup"><span data-stu-id="e13b0-170">Visualization</span></span>

<span data-ttu-id="e13b0-171">[空間マッピングの視覚化](spatial-mapping.md#visualization)を使用して、環境のリアルタイムのフィードバックを行うことができますが、平面オブジェクトと watertight オブジェクトの単純化によってパフォーマンスや視覚品質が向上する多くのシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="e13b0-171">While [spatial mapping visualization](spatial-mapping.md#visualization) can be used for real-time feedback of the environment, there are many scenarios where the simplicity of planar and watertight objects provides more performance or visual quality.</span></span> <span data-ttu-id="e13b0-172">四角形または平面 watertight メッシュによって提供される平面サーフェスに射影した場合、空間マッピングを使用して記述されているシャドウプロジェクションとアース手法は、より見栄えが良い場合があります。</span><span class="sxs-lookup"><span data-stu-id="e13b0-172">Shadow projection and grounding techniques that are described using spatial mapping may be more pleasing if projected on the planar surfaces provided by Quads or the planar watertight mesh.</span></span> <span data-ttu-id="e13b0-173">これは、シーンが推測されることが原因で完全な事前スキャンが最適ではない環境やシナリオでは特に当てはまり、完全な環境と平面の前提条件によって成果物が最小化されます。</span><span class="sxs-lookup"><span data-stu-id="e13b0-173">This is especially true for environments/scenarios where thorough pre-scanning is not optimal due to the fact that the scene will infer, and complete environments and planar assumptions will minimize artifacts.</span></span>

<span data-ttu-id="e13b0-174">さらに、空間マッピングによって返されるサーフェスの合計数は、内部空間キャッシュによって制限されます。一方、シーン認識のバージョンの空間マッピングメッシュは、キャッシュされていない空間マッピングデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="e13b0-174">Additionally, the total number of surfaces returned by Spatial Mapping is limited by the internal spatial cache, while Scene understanding's version of the Spatial Mapping mesh is able to access spatial mapping data that is not cached.</span></span> <span data-ttu-id="e13b0-175">このため、シーンを理解することは、視覚エフェクトやさらにメッシュ処理を行うために、より大きなスペース (たとえば、1つの部屋を超える) のメッシュ表現をキャプチャする場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="e13b0-175">Because of this, Scene understanding is more suited to capturing mesh representations for larger spaces (for example, larger than a single room) for visualization or further mesh processing.</span></span> <span data-ttu-id="e13b0-176">EnableWorldMesh で返されるワールドメッシュの詳細レベルは、全体にわたって一貫しています。これにより、ワイヤーフレームとしてレンダリングした場合により良い視覚化が得られる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e13b0-176">The world mesh returned with EnableWorldMesh will have a consistent level of detail throughout, which may yield a more pleasing visualization if rendered as wireframe.</span></span>

### <a name="see-also"></a><span data-ttu-id="e13b0-177">参照</span><span class="sxs-lookup"><span data-stu-id="e13b0-177">See Also</span></span>

* [<span data-ttu-id="e13b0-178">シーンを理解する SDK</span><span class="sxs-lookup"><span data-stu-id="e13b0-178">Scene understanding SDK</span></span>](../develop/platform-capabilities-and-apis/scene-understanding-SDK.md)
* [<span data-ttu-id="e13b0-179">空間マッピング</span><span class="sxs-lookup"><span data-stu-id="e13b0-179">Spatial mapping</span></span>](spatial-mapping.md)
