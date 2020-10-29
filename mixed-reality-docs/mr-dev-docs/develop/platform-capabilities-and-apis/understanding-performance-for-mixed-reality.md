---
title: Mixed Reality のパフォーマンスについて
description: Windows Mixed Reality アプリのパフォーマンスの最適化に関する高度なトピックと詳細
author: hferrone
ms.author: v-hferrone
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、パフォーマンス、最適化、CPU、GPU
ms.openlocfilehash: c51f84a9814e946603e6dd750fedf0f6e6e78cc0
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684895"
---
# <a name="understanding-performance-for-mixed-reality"></a><span data-ttu-id="985d8-104">Mixed reality のパフォーマンスについて</span><span class="sxs-lookup"><span data-stu-id="985d8-104">Understanding performance for mixed reality</span></span>

<span data-ttu-id="985d8-105">この記事では、Mixed Reality アプリのパフォーマンスの重要性について説明します。</span><span class="sxs-lookup"><span data-stu-id="985d8-105">This article is an introduction to understanding the significance of performance for your Mixed Reality app.</span></span>  <span data-ttu-id="985d8-106">アプリケーションが最適なフレームレートで実行されない場合、ユーザーエクスペリエンスが大幅に低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="985d8-106">User experience can be greatly degraded if your application does not run at optimal frame rate.</span></span> <span data-ttu-id="985d8-107">ホログラムが不安定になり、環境のヘッドトラッキングが不正確になり、ユーザーのエクスペリエンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="985d8-107">Holograms will appear unstable and head tracking of the environment will be inaccurate, leading to a poor experience for the user.</span></span> <span data-ttu-id="985d8-108">パフォーマンスは、ポーランド語のタスクではなく、混合現実の開発のためのファーストクラスの機能と考える必要があります。</span><span class="sxs-lookup"><span data-stu-id="985d8-108">Performance must be considered a first class feature for mixed reality development and not a polish task.</span></span>

<span data-ttu-id="985d8-109">各ターゲットプラットフォームのパフォーマンスフレームの値の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="985d8-109">The performant framerate values for each target platform are listed below.</span></span>

| <span data-ttu-id="985d8-110">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="985d8-110">Platform</span></span> | <span data-ttu-id="985d8-111">ターゲットフレームレート</span><span class="sxs-lookup"><span data-stu-id="985d8-111">Target Frame Rate</span></span> |
|----------|-------------------|
| [<span data-ttu-id="985d8-112">HoloLens</span><span class="sxs-lookup"><span data-stu-id="985d8-112">HoloLens</span></span>](../../hololens-hardware-details.md) | <span data-ttu-id="985d8-113">60 FPS</span><span class="sxs-lookup"><span data-stu-id="985d8-113">60 FPS</span></span> |
| [<span data-ttu-id="985d8-114">Windows Mixed Reality ウルトラ Pc</span><span class="sxs-lookup"><span data-stu-id="985d8-114">Windows Mixed Reality Ultra PCs</span></span>](../../discover/immersive-headset-hardware-details.md) | <span data-ttu-id="985d8-115">90 FPS</span><span class="sxs-lookup"><span data-stu-id="985d8-115">90 FPS</span></span> |
| [<span data-ttu-id="985d8-116">Windows Mixed Reality Pc</span><span class="sxs-lookup"><span data-stu-id="985d8-116">Windows Mixed Reality PCs</span></span>](../../discover/immersive-headset-hardware-details.md) | <span data-ttu-id="985d8-117">60 FPS</span><span class="sxs-lookup"><span data-stu-id="985d8-117">60 FPS</span></span> |

<span data-ttu-id="985d8-118">次のフレームワークでは、ターゲットフレームレートに到達するためのベストプラクティスについて概説します。</span><span class="sxs-lookup"><span data-stu-id="985d8-118">The framework below outlines best practices for hitting target frame rates.</span></span> <span data-ttu-id="985d8-119">Unity で開発する場合は、unity 環境でのフレームレートの測定と向上に関するヒントについては、 [unity のパフォーマンスに関する推奨事項](../unity/performance-recommendations-for-unity.md) に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="985d8-119">If developing in Unity, consider reading the [performance recommendations for Unity article](../unity/performance-recommendations-for-unity.md) for tips on measuring and improving framerate in the Unity environment.</span></span>

## <a name="understanding-performance-bottlenecks"></a><span data-ttu-id="985d8-120">パフォーマンスのボトルネックについて</span><span class="sxs-lookup"><span data-stu-id="985d8-120">Understanding performance bottlenecks</span></span>

<span data-ttu-id="985d8-121">アプリの不採算事業フレームレートがある場合、最初の手順は、アプリケーションが計算を集中的に使用している場所を分析して理解することです。</span><span class="sxs-lookup"><span data-stu-id="985d8-121">If your app has an underperforming framerate, the first step is to analyze and understand where your application is computationally intensive.</span></span> <span data-ttu-id="985d8-122">シーンをレンダリングする作業には、CPU と GPU の2つの主要なプロセッサがあります。</span><span class="sxs-lookup"><span data-stu-id="985d8-122">There are two primary processors responsible for the work to render your scene: the CPU and the GPU.</span></span> <span data-ttu-id="985d8-123">これらはそれぞれ、混合 Reality アプリのさまざまな側面を処理します。</span><span class="sxs-lookup"><span data-stu-id="985d8-123">Each of these handle different aspects of your Mixed Reality app.</span></span> <span data-ttu-id="985d8-124">ボトルネックが発生する可能性がある主な場所には、次の3つがあります。</span><span class="sxs-lookup"><span data-stu-id="985d8-124">There are three key places where bottlenecks may occur:</span></span> 

1. <span data-ttu-id="985d8-125">**アプリスレッド-CPU** -このスレッドは、アプリロジックを担います。</span><span class="sxs-lookup"><span data-stu-id="985d8-125">**App Thread - CPU** - This thread is responsible for your app logic.</span></span> <span data-ttu-id="985d8-126">これには、入力、アニメーション、物理、およびその他のアプリロジックの処理が含まれます。</span><span class="sxs-lookup"><span data-stu-id="985d8-126">This includes processing input, animations, physics, and other app logic.</span></span>
2. <span data-ttu-id="985d8-127">**スレッドを gpu にレンダリングする** -このスレッドは、gpu への描画呼び出しを送信します。</span><span class="sxs-lookup"><span data-stu-id="985d8-127">**Render Thread - CPU to GPU** - This thread is responsible for submitting your draw calls to the GPU.</span></span> <span data-ttu-id="985d8-128">アプリでキューブやモデルなどのオブジェクトをレンダリングする場合、このスレッドは GPU に要求を送信してこれらの操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="985d8-128">When your app wants to render an object such as a cube or model, this thread sends a request to the GPU to perform these operations.</span></span>
3. <span data-ttu-id="985d8-129">**GPU** -このプロセッサは、通常、3d データ (モデル、テクスチャなど) をピクセルに変換するために、アプリケーションのグラフィックスパイプラインを処理します。</span><span class="sxs-lookup"><span data-stu-id="985d8-129">**GPU** - This processor most commonly handles the graphics pipeline of your application to transform 3D data (models, textures, etc.) into pixels.</span></span> <span data-ttu-id="985d8-130">最終的には、デバイスの画面に送信する2D イメージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="985d8-130">It ultimately produces a 2D image to submit to your device's screen.</span></span>

![フレームの有効期間](images/lifetime-of-a-frame.png)

<span data-ttu-id="985d8-132">一般に、HoloLens アプリケーションは GPU にバインドされますが、常にではありません。</span><span class="sxs-lookup"><span data-stu-id="985d8-132">Generally, HoloLens applications will be GPU bound, but not always.</span></span> <span data-ttu-id="985d8-133">以下のツールと手法を使用して、特定のアプリがボトルネックになっている場所を把握してください。</span><span class="sxs-lookup"><span data-stu-id="985d8-133">Use the tools and techniques below to understand where your particular app is bottlenecked.</span></span>

## <a name="how-to-analyze-your-application"></a><span data-ttu-id="985d8-134">アプリケーションを分析する方法</span><span class="sxs-lookup"><span data-stu-id="985d8-134">How to analyze your application</span></span>

<span data-ttu-id="985d8-135">混合現実アプリケーションのパフォーマンスプロファイルを理解できるツールは多数あります。</span><span class="sxs-lookup"><span data-stu-id="985d8-135">There are many tools that allow you to understand the performance profile of your mixed reality application.</span></span> <span data-ttu-id="985d8-136">これらを使用すると、ボトルネックがある場所と理由を見つけることができるため、対処できます。</span><span class="sxs-lookup"><span data-stu-id="985d8-136">These will enable you to find where and why you have bottlenecks, so you can address them.</span></span>

<span data-ttu-id="985d8-137">アプリケーションの詳細なプロファイル情報を取得するための一般的なツールを次に示します。</span><span class="sxs-lookup"><span data-stu-id="985d8-137">Below are some common tools to gain deep profiling information for your application:</span></span>
- [<span data-ttu-id="985d8-138">Intel グラフィックスパフォーマンスアナライザー</span><span class="sxs-lookup"><span data-stu-id="985d8-138">Intel Graphics Performance Analyzers</span></span>](https://software.intel.com/gpa)
- [<span data-ttu-id="985d8-139">Visual Studio のグラフィックスデバッガー</span><span class="sxs-lookup"><span data-stu-id="985d8-139">Visual Studio Graphics Debuggers</span></span>](https://docs.microsoft.com/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [<span data-ttu-id="985d8-140">Unity Profiler</span><span class="sxs-lookup"><span data-stu-id="985d8-140">Unity Profiler</span></span>](https://docs.unity3d.com/Manual/Profiler.html)
- [<span data-ttu-id="985d8-141">Unity フレームデバッガー</span><span class="sxs-lookup"><span data-stu-id="985d8-141">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a><span data-ttu-id="985d8-142">任意の環境でプロファイリングする方法</span><span class="sxs-lookup"><span data-stu-id="985d8-142">How to profile in any environment</span></span>

<span data-ttu-id="985d8-143">アプリケーションで GPU バインドと CPU バインドのどちらを使用しているかを判断する方法の1つは、レンダーターゲットの出力の解像度を下げることです。</span><span class="sxs-lookup"><span data-stu-id="985d8-143">One way to determine if you are GPU bound or CPU bound in your application is to decrease the resolution of the render target output.</span></span> <span data-ttu-id="985d8-144">計算するピクセル数を減らすことにより、GPU の負荷が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="985d8-144">By reducing the number of pixels to calculate, this will reduce your GPU load.</span></span> <span data-ttu-id="985d8-145">デバイスは、小さいテクスチャにレンダリングされ、その後、最後のイメージを表示するためにアップサンプリングされます。</span><span class="sxs-lookup"><span data-stu-id="985d8-145">The device will render to a smaller texture, then up-sample to display your final image.</span></span>

<span data-ttu-id="985d8-146">レンダリングの解像度を下げると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="985d8-146">After decreasing rendering resolution, if:</span></span>
1) <span data-ttu-id="985d8-147">アプリケーションのフレームレートが **増加** し、 **GPU にバインド** されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="985d8-147">Application framerate **increases** , then you are likely **GPU Bound**</span></span>
1) <span data-ttu-id="985d8-148">アプリケーションのフレームレートが **変更** されていないため、 **CPU バインド** されている可能性があります</span><span class="sxs-lookup"><span data-stu-id="985d8-148">Application framerate **unchanged** , then you are likely **CPU Bound**</span></span>

>[!NOTE]
><span data-ttu-id="985d8-149">Unity では、 *[XRSettings](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* プロパティを使用して、実行時にアプリケーションのレンダーターゲットの解像度を簡単に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="985d8-149">Unity provides the ability to easily modify the render target resolution of your application at runtime through the *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property.</span></span> <span data-ttu-id="985d8-150">デバイスに表示される最終的なイメージには、固定された解決策があります。</span><span class="sxs-lookup"><span data-stu-id="985d8-150">The final image presented on device has a fixed resolution.</span></span> <span data-ttu-id="985d8-151">このプラットフォームでは、解像度の低い出力をサンプリングして、ディスプレイに表示する解像度の高いイメージを構築します。</span><span class="sxs-lookup"><span data-stu-id="985d8-151">The platform will sample the lower resolution output to build a higher resolution image for rendering on displays.</span></span> 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a><span data-ttu-id="985d8-152">アプリケーションを改善する方法</span><span class="sxs-lookup"><span data-stu-id="985d8-152">How to improve your application</span></span>

### <a name="cpu-performance-recommendations"></a><span data-ttu-id="985d8-153">CPU のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="985d8-153">CPU performance recommendations</span></span>

<span data-ttu-id="985d8-154">一般に、CPU 上の mixed reality アプリケーションでほとんどの作業を行うには、シーンの "シミュレーション" を実行し、アプリケーションロジックを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="985d8-154">Generally, most work in a mixed reality application on the CPU involves performing the "simulation" of the scene and processing your application logic.</span></span> <span data-ttu-id="985d8-155">通常、最適化の対象となる領域は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="985d8-155">The following areas are usually targeted for optimization:</span></span>

- <span data-ttu-id="985d8-156">Animations</span><span class="sxs-lookup"><span data-stu-id="985d8-156">Animations</span></span>
- <span data-ttu-id="985d8-157">物理計算</span><span class="sxs-lookup"><span data-stu-id="985d8-157">Physics</span></span>
- <span data-ttu-id="985d8-158">メモリの割り当て</span><span class="sxs-lookup"><span data-stu-id="985d8-158">Memory allocations</span></span>
- <span data-ttu-id="985d8-159">複雑なアルゴリズム (</span><span class="sxs-lookup"><span data-stu-id="985d8-159">Complex algorithms (i.e</span></span> <span data-ttu-id="985d8-160">逆のキネマティック、パスの検索)</span><span class="sxs-lookup"><span data-stu-id="985d8-160">inverse kinematics, path-finding)</span></span>

### <a name="gpu-performance-recommendations"></a><span data-ttu-id="985d8-161">GPU のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="985d8-161">GPU performance recommendations</span></span>

#### <a name="understanding-bandwidth-vs-fill-rate"></a><span data-ttu-id="985d8-162">帯域幅とフィルレートを理解する</span><span class="sxs-lookup"><span data-stu-id="985d8-162">Understanding bandwidth vs. fill rate</span></span>
<span data-ttu-id="985d8-163">GPU でフレームをレンダリングする場合、通常、アプリケーションはメモリ帯域幅またはフィルレートによって制限されます。</span><span class="sxs-lookup"><span data-stu-id="985d8-163">When rendering a frame on the GPU, an application is generally either bound by memory bandwidth or fill rate.</span></span>

- <span data-ttu-id="985d8-164">**メモリ帯域幅** は、GPU がメモリから実行できる読み取りと書き込みの比率です。</span><span class="sxs-lookup"><span data-stu-id="985d8-164">**Memory bandwidth** is the rate of reads and writes the GPU can perform from memory</span></span>
    - <span data-ttu-id="985d8-165">帯域幅の制限を特定するには、テクスチャの品質を下げ、フレームレートが改善されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="985d8-165">To identify bandwidth limitations, reduce texture quality and check if the framerate has improved.</span></span>
    - <span data-ttu-id="985d8-166">Unity では、[ **Edit** **Texture Quality**  >  **プロジェクト設定** の  >  **[品質設定](https://docs.unity3d.com/Manual/class-QualitySettings.html)** の編集] で [テクスチャの品質] を変更することによってこれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="985d8-166">In Unity, this can be done by changing **Texture Quality** in **Edit** > **Project Settings** > **[Quality Settings](https://docs.unity3d.com/Manual/class-QualitySettings.html)** .</span></span>
- <span data-ttu-id="985d8-167">**Fill rate** は、GPU によって1秒あたりに描画できるピクセルを表します。</span><span class="sxs-lookup"><span data-stu-id="985d8-167">**Fill rate** refers to the pixels that can be drawn per second by the GPU.</span></span>
    - <span data-ttu-id="985d8-168">フィルレートの制限を特定するには、ディスプレイの解像度を下げ、フレームレートが改善されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="985d8-168">To identify fill rate limitations, decrease the display resolution and check if framerate improved.</span></span> 
    - <span data-ttu-id="985d8-169">Unity では、XRSettings プロパティを使用してこれを行うことができ *[ます。](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)*</span><span class="sxs-lookup"><span data-stu-id="985d8-169">In Unity, this can be done via the  *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property</span></span>

<span data-ttu-id="985d8-170">通常、メモリ帯域幅には次のいずれかの最適化が伴います。</span><span class="sxs-lookup"><span data-stu-id="985d8-170">Memory bandwidth generally involves optimizations to either:</span></span>
1) <span data-ttu-id="985d8-171">テクスチャ解像度を下げる</span><span class="sxs-lookup"><span data-stu-id="985d8-171">Decrease texture resolutions</span></span>
2) <span data-ttu-id="985d8-172">使用するテクスチャ (法線、反射など) を減らす</span><span class="sxs-lookup"><span data-stu-id="985d8-172">Utilize fewer textures (normals, specular, etc.)</span></span>

<span data-ttu-id="985d8-173">Fill rate は、レンダリングされた最終的なピクセルに対して計算する必要がある操作の数を減らすことに焦点を合わせています。</span><span class="sxs-lookup"><span data-stu-id="985d8-173">Fill rate is focused on reducing the number of operations that need to be computed for a final rendered pixel.</span></span> <span data-ttu-id="985d8-174">これには、次の制限が含まれます。</span><span class="sxs-lookup"><span data-stu-id="985d8-174">This includes reducing:</span></span>
1) <span data-ttu-id="985d8-175">表示/処理するオブジェクトの数</span><span class="sxs-lookup"><span data-stu-id="985d8-175">Number of objects to render/process</span></span>
2) <span data-ttu-id="985d8-176">シェーダーあたりの操作数</span><span class="sxs-lookup"><span data-stu-id="985d8-176">Number of operations per shader</span></span>
3) <span data-ttu-id="985d8-177">最終結果に対する GPU ステージの数 (ジオメトリシェーダー、処理後の影響など)</span><span class="sxs-lookup"><span data-stu-id="985d8-177">Number of GPU stages to final result (geometry shaders, post-processing effects, etc.)</span></span>
4) <span data-ttu-id="985d8-178">レンダリングするピクセル数 (表示解像度)</span><span class="sxs-lookup"><span data-stu-id="985d8-178">Number of pixels to render (display resolution)</span></span>

#### <a name="reduce-polygon-count"></a><span data-ttu-id="985d8-179">多角形の数を減らす</span><span class="sxs-lookup"><span data-stu-id="985d8-179">Reduce polygon count</span></span>

<span data-ttu-id="985d8-180">ポリゴンの数が多いほど、GPU に対する操作が増えることになります。シーン [の多角形の数を減らす](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) と、レンダリング時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="985d8-180">Higher polygon counts result in more operations for the GPU; [reducing the number of polygons](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) in your scene will reduce the render time.</span></span> <span data-ttu-id="985d8-181">コストがかかる可能性のあるジオメトリの網掛けに関連する要因は他にもありますが、polygon count は、シーンがどの程度高価にレンダリングされるかを判断するための最も簡単なメトリックです。</span><span class="sxs-lookup"><span data-stu-id="985d8-181">There are other factors involved in shading the geometry that can be expensive, but polygon count is the simplest metric to determine how expensive a scene will be to render.</span></span>

#### <a name="limit-overdraw"></a><span data-ttu-id="985d8-182">オーバードローを制限する</span><span class="sxs-lookup"><span data-stu-id="985d8-182">Limit overdraw</span></span>

<span data-ttu-id="985d8-183">Occluding オブジェクトによって非表示になっているため、複数のオブジェクトがレンダリングされても画面に表示されない場合は、高いオーバードローが発生します。</span><span class="sxs-lookup"><span data-stu-id="985d8-183">High overdraw occurs when multiple objects are rendered but not shown on screen as they are hidden by an occluding object.</span></span> <span data-ttu-id="985d8-184">その背後にオブジェクトがある壁を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="985d8-184">Imagine looking at a wall that has objects behind it.</span></span> <span data-ttu-id="985d8-185">すべてのジオメトリはレンダリングのために処理されますが、不透明な壁面だけをレンダリングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="985d8-185">All of the geometry would be processed for rendering, but only the opaque wall needs to be rendered.</span></span> <span data-ttu-id="985d8-186">この結果、不要な操作が発生します。</span><span class="sxs-lookup"><span data-stu-id="985d8-186">This results in unnecessary operations.</span></span>

#### <a name="shaders"></a><span data-ttu-id="985d8-187">シェーダー</span><span class="sxs-lookup"><span data-stu-id="985d8-187">Shaders</span></span>

<span data-ttu-id="985d8-188">シェーダーは、GPU 上で実行され、レンダリングの2つの重要な手順を実行する小さなプログラムです。</span><span class="sxs-lookup"><span data-stu-id="985d8-188">Shaders are small programs that run on the GPU and perform two important steps in rendering:</span></span>
1) <span data-ttu-id="985d8-189">描画する頂点と画面空間内の位置を決定する (頂点シェーダー)</span><span class="sxs-lookup"><span data-stu-id="985d8-189">Determining which vertices should be drawn and where they are in screen space (the Vertex shader)</span></span>
    - <span data-ttu-id="985d8-190">頂点シェーダーは、通常、各メッシュの頂点ごとに実行されます。</span><span class="sxs-lookup"><span data-stu-id="985d8-190">The Vertex shader is generally executed per vertex for every mesh.</span></span>
2) <span data-ttu-id="985d8-191">各ピクセルの色を決定する (ピクセルシェーダー)</span><span class="sxs-lookup"><span data-stu-id="985d8-191">Determining the color of each pixel (the Pixel shader)</span></span>
    - <span data-ttu-id="985d8-192">ピクセルシェーダーは、描画されるテクスチャに対してジオメトリによってレンダリングされるピクセルごとに実行されます。</span><span class="sxs-lookup"><span data-stu-id="985d8-192">The Pixel shader is executed per pixel rendered by the geometry to the texture being rendered to.</span></span>

<span data-ttu-id="985d8-193">通常、シェーダーでは、多くの変換と照明計算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="985d8-193">Typically, shaders perform many transformations and lighting calculations.</span></span> <span data-ttu-id="985d8-194">複雑な照明モデル、影、およびその他の操作によって、優れた結果が得られる場合もありますが、価格もあります。</span><span class="sxs-lookup"><span data-stu-id="985d8-194">Although complex lighting models, shadows, and other operations can generate fantastic results, they also come with a price.</span></span> <span data-ttu-id="985d8-195">シェーダーで計算される操作の数を減らすと、フレームあたりの GPU に必要な作業が大幅に減少します。</span><span class="sxs-lookup"><span data-stu-id="985d8-195">Reducing the number of operations computed in shaders can greatly reduce the work needed for the GPU per frame.</span></span>

##### <a name="shader-coding-recommendations"></a><span data-ttu-id="985d8-196">シェーダーのコーディングに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="985d8-196">Shader coding recommendations</span></span>

- <span data-ttu-id="985d8-197">可能な限り、バイリニアフィルタリングを使用する</span><span class="sxs-lookup"><span data-stu-id="985d8-197">Use bilinear filtering, whenever possible</span></span>
- <span data-ttu-id="985d8-198">同時に乗算と加算を行うために、MAD 組み込みを使用するように式を再配置します。</span><span class="sxs-lookup"><span data-stu-id="985d8-198">Rearrange expressions to use MAD intrinsics in order to do a multiply and an add at the same time</span></span>
- <span data-ttu-id="985d8-199">CPU で可能な限り Precalculate し、素材に定数として渡します。</span><span class="sxs-lookup"><span data-stu-id="985d8-199">Precalculate as much as possible on the CPU and pass as constants to the material</span></span>
- <span data-ttu-id="985d8-200">**ピクセルシェーダーから頂点シェーダーへの移動操作を優先する**</span><span class="sxs-lookup"><span data-stu-id="985d8-200">**Favor moving operations from the pixel shader to the vertex shader**</span></span>
    - <span data-ttu-id="985d8-201">一般に、頂点の数は、ピクセル数よりもはるかに小さくなっています (720p は921600ピクセル、1080p は2073600ピクセル、など)。</span><span class="sxs-lookup"><span data-stu-id="985d8-201">Generally, the number of vertices is much smaller than the number of pixels (720p is 921,600 pixels, 1080p is 2,073,600 pixels, etc.)</span></span>

#### <a name="remove-gpu-stages"></a><span data-ttu-id="985d8-202">GPU ステージの削除</span><span class="sxs-lookup"><span data-stu-id="985d8-202">Remove GPU stages</span></span>

<span data-ttu-id="985d8-203">処理後の影響は非常に高額であり、アプリケーションの塗りつぶしレートが高くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="985d8-203">Post-processing effects can be very expensive and increase the fill rate of your application.</span></span> <span data-ttu-id="985d8-204">これには、MSAA などのアンチエイリアシング技法が含まれます。</span><span class="sxs-lookup"><span data-stu-id="985d8-204">This includes anti-aliasing techniques such as MSAA.</span></span> <span data-ttu-id="985d8-205">HoloLens では、これらの手法を完全に回避することをお勧めします。また、geometry、ハル、compute シェーダーなどの追加のシェーダーステージを回避することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="985d8-205">On HoloLens, it is recommended to avoid these techniques entirely, as well as additional shader stages such as geometry, hull, and compute shaders.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="985d8-206">メモリに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="985d8-206">Memory recommendations</span></span>

<span data-ttu-id="985d8-207">過剰なメモリの割り当ておよび解放操作を行うと、パフォーマンスが低下したり、フレームがフリーズしたり、その他の有害な動作が発生したりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="985d8-207">Excessive memory allocation and deallocation operations can result in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="985d8-208">メモリ管理はガベージコレクターによって制御されるため、Unity で開発するときは、メモリに関する考慮事項を理解することが特に重要です。</span><span class="sxs-lookup"><span data-stu-id="985d8-208">It is especially important to understand memory considerations when developing in Unity, since memory management is controlled by the garbage collector.</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="985d8-209">オブジェクト プーリング</span><span class="sxs-lookup"><span data-stu-id="985d8-209">Object pooling</span></span>

<span data-ttu-id="985d8-210">オブジェクトプールは、オブジェクトの継続的な割り当てと割り当て解除のコストを削減するための一般的な手法です。</span><span class="sxs-lookup"><span data-stu-id="985d8-210">Object pooling is a popular technique to reduce the cost of continuous allocations and deallocations of objects.</span></span> <span data-ttu-id="985d8-211">これを行うには、同一のオブジェクトの大規模なプールを割り当て、時間の経過と共にオブジェクトを絶えず生成して破棄するのではなく、このプールの非アクティブで使用可能なインスタンスを再利用します。</span><span class="sxs-lookup"><span data-stu-id="985d8-211">This is done by allocating a large pool of identical objects and re-using inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="985d8-212">オブジェクト プールは、アプリの間の有効期間が一定ではない再使用可能なコンポーネントに最適です。</span><span class="sxs-lookup"><span data-stu-id="985d8-212">Object pools are great for re-useable components that have variable lifetime during an app.</span></span>

## <a name="see-also"></a><span data-ttu-id="985d8-213">関連項目</span><span class="sxs-lookup"><span data-stu-id="985d8-213">See also</span></span>
- [<span data-ttu-id="985d8-214">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="985d8-214">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
- [<span data-ttu-id="985d8-215">Unity で推奨される設定</span><span class="sxs-lookup"><span data-stu-id="985d8-215">Recommended settings for Unity</span></span>](../unity/recommended-settings-for-unity.md)
- [<span data-ttu-id="985d8-216">3D モデルの最適化</span><span class="sxs-lookup"><span data-stu-id="985d8-216">Optimize 3D models</span></span>](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [<span data-ttu-id="985d8-217">リアルタイム3D モデルの変換と最適化に関するベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="985d8-217">Best practices for converting and optimizing real-time 3D Models</span></span>](https://docs.microsoft.com/dynamics365/mixed-reality/import-tool/best-practices)

