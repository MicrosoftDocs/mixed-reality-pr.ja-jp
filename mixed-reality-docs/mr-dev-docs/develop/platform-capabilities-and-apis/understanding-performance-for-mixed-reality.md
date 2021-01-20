---
title: Mixed Reality のパフォーマンスについて
description: Windows Mixed Reality アプリのパフォーマンスの分析と最適化に関する詳細情報と詳細について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 3/26/2019
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、パフォーマンス、最適化、CPU、GPU
ms.openlocfilehash: 68aae6408a59b197227ab8cd9042e11f8a255d10
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583079"
---
# <a name="understanding-performance-for-mixed-reality"></a><span data-ttu-id="fa084-104">Mixed reality のパフォーマンスについて</span><span class="sxs-lookup"><span data-stu-id="fa084-104">Understanding performance for mixed reality</span></span>

<span data-ttu-id="fa084-105">この記事では、Mixed Reality アプリのパフォーマンスの重要性について説明します。</span><span class="sxs-lookup"><span data-stu-id="fa084-105">This article is an introduction to understanding the significance of performance for your Mixed Reality app.</span></span>  <span data-ttu-id="fa084-106">アプリケーションが最適なフレームレートで実行されない場合、ユーザーエクスペリエンスが大幅に低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fa084-106">User experience can be greatly degraded if your application doesn't run at optimal frame rate.</span></span> <span data-ttu-id="fa084-107">ホログラムが不安定になり、環境のヘッドトラッキングが不正確になり、ユーザーのエクスペリエンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="fa084-107">Holograms will appear unstable and head tracking of the environment will be inaccurate, leading to a poor experience for the user.</span></span> <span data-ttu-id="fa084-108">パフォーマンスは、ポーランド語のタスクではなく、混合現実の開発のためのファーストクラスの機能と考える必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa084-108">Performance must be considered a first class feature for mixed reality development and not a polish task.</span></span>

<span data-ttu-id="fa084-109">各ターゲットプラットフォームのパフォーマンスフレームの値の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="fa084-109">The performant framerate values for each target platform are listed below.</span></span>

| <span data-ttu-id="fa084-110">プラットフォーム</span><span class="sxs-lookup"><span data-stu-id="fa084-110">Platform</span></span> | <span data-ttu-id="fa084-111">ターゲットフレームレート</span><span class="sxs-lookup"><span data-stu-id="fa084-111">Target Frame Rate</span></span> |
|----------|-------------------|
| [<span data-ttu-id="fa084-112">HoloLens</span><span class="sxs-lookup"><span data-stu-id="fa084-112">HoloLens</span></span>](/hololens/hololens1-hardware) | <span data-ttu-id="fa084-113">60 FPS</span><span class="sxs-lookup"><span data-stu-id="fa084-113">60 FPS</span></span> |
| [<span data-ttu-id="fa084-114">Windows Mixed Reality ウルトラ Pc</span><span class="sxs-lookup"><span data-stu-id="fa084-114">Windows Mixed Reality Ultra PCs</span></span>](../../discover/immersive-headset-hardware-details.md) | <span data-ttu-id="fa084-115">90 FPS</span><span class="sxs-lookup"><span data-stu-id="fa084-115">90 FPS</span></span> |
| [<span data-ttu-id="fa084-116">Windows Mixed Reality Pc</span><span class="sxs-lookup"><span data-stu-id="fa084-116">Windows Mixed Reality PCs</span></span>](../../discover/immersive-headset-hardware-details.md) | <span data-ttu-id="fa084-117">60 FPS</span><span class="sxs-lookup"><span data-stu-id="fa084-117">60 FPS</span></span> |

<span data-ttu-id="fa084-118">次のフレームワークでは、ターゲットフレームレートに到達するためのベストプラクティスについて概説します。</span><span class="sxs-lookup"><span data-stu-id="fa084-118">The framework below outlines best practices for hitting target frame rates.</span></span> <span data-ttu-id="fa084-119">Unity 環境でのフレームレートの測定と向上に関するヒントについては、 [unity のパフォーマンスに関する推奨事項](../unity/performance-recommendations-for-unity.md) に関する記事を参照することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fa084-119">We recommend reading the [performance recommendations for Unity article](../unity/performance-recommendations-for-unity.md) for tips on measuring and improving framerate in the Unity environment.</span></span>

## <a name="understanding-performance-bottlenecks"></a><span data-ttu-id="fa084-120">パフォーマンスのボトルネックについて</span><span class="sxs-lookup"><span data-stu-id="fa084-120">Understanding performance bottlenecks</span></span>

<span data-ttu-id="fa084-121">アプリの不採算事業フレームレートがある場合、最初の手順は、アプリケーションが計算を集中的に使用している場所を分析して理解することです。</span><span class="sxs-lookup"><span data-stu-id="fa084-121">If your app has an underperforming framerate, the first step is to analyze and understand where your application is computationally intensive.</span></span> <span data-ttu-id="fa084-122">シーンをレンダリングする作業には、CPU と GPU の2つの主要なプロセッサがあります。それぞれが混合の現実アプリのさまざまな側面を処理します。</span><span class="sxs-lookup"><span data-stu-id="fa084-122">There are two primary processors responsible for the work to render your scene: the CPU and the GPU, each handling different aspects of your Mixed Reality app.</span></span> <span data-ttu-id="fa084-123">ボトルネックが発生する可能性がある3つの主要な場所は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fa084-123">The three key places where bottlenecks may occur are:</span></span> 

1. <span data-ttu-id="fa084-124">**アプリスレッド-CPU** -
    入力、アニメーション、物理、およびその他のアプリロジックの処理を含む、アプリロジックを担当します。</span><span class="sxs-lookup"><span data-stu-id="fa084-124">**App Thread - CPU** -
 Responsible for your app logic, including processing input, animations, physics, and other app logic.</span></span>
2. <span data-ttu-id="fa084-125">[**スレッドのレンダリング-CPU** -gpu に描画呼び出しを送信します。</span><span class="sxs-lookup"><span data-stu-id="fa084-125">**Render Thread - CPU to GPU** - Responsible for submitting your draw calls to the GPU.</span></span> <span data-ttu-id="fa084-126">アプリでキューブやモデルなどのオブジェクトをレンダリングする場合、このスレッドは GPU に要求を送信して操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="fa084-126">When your app wants to render an object such as a cube or model, this thread sends a request to the GPU to do the operations.</span></span>
3. <span data-ttu-id="fa084-127">**GPU** -通常、3d データ (モデル、テクスチャなど) をピクセルに変換するために、アプリケーションのグラフィックスパイプラインが処理されます。</span><span class="sxs-lookup"><span data-stu-id="fa084-127">**GPU** - Most commonly handles the graphics pipeline of your application to transform 3D data (models, textures, and so on) into pixels.</span></span> <span data-ttu-id="fa084-128">最終的には、デバイスの画面に送信する2D イメージが生成されます。</span><span class="sxs-lookup"><span data-stu-id="fa084-128">It ultimately produces a 2D image to submit to your device's screen.</span></span>

![フレームの有効期間](images/lifetime-of-a-frame.png)

<span data-ttu-id="fa084-130">一般に、HoloLens アプリケーションは GPU にバインドされますが、常にではありません。</span><span class="sxs-lookup"><span data-stu-id="fa084-130">Generally, HoloLens applications will be GPU bound, but not always.</span></span> <span data-ttu-id="fa084-131">以下のツールと手法を使用して、特定のアプリがボトルネックになっている場所を把握してください。</span><span class="sxs-lookup"><span data-stu-id="fa084-131">Use the tools and techniques below to understand where your particular app is bottlenecked.</span></span>

## <a name="how-to-analyze-your-application"></a><span data-ttu-id="fa084-132">アプリケーションを分析する方法</span><span class="sxs-lookup"><span data-stu-id="fa084-132">How to analyze your application</span></span>

<span data-ttu-id="fa084-133">混合の現実アプリケーションでパフォーマンスプロファイルと潜在的なボトルネックを理解できるツールは多数あります。</span><span class="sxs-lookup"><span data-stu-id="fa084-133">There are many tools that allow you to understand the performance profile and potential bottlenecks in your mixed reality application.</span></span> 

<span data-ttu-id="fa084-134">アプリケーションの詳細なプロファイル情報を収集するための一般的なツールを次に示します。</span><span class="sxs-lookup"><span data-stu-id="fa084-134">Below are some common tools to help you gather deep profiling information for your application:</span></span>
- [<span data-ttu-id="fa084-135">Intel グラフィックスパフォーマンスアナライザー</span><span class="sxs-lookup"><span data-stu-id="fa084-135">Intel Graphics Performance Analyzers</span></span>](https://software.intel.com/gpa)
- [<span data-ttu-id="fa084-136">Visual Studio のグラフィックスデバッガー</span><span class="sxs-lookup"><span data-stu-id="fa084-136">Visual Studio Graphics Debuggers</span></span>](/visualstudio/debugger/graphics/visual-studio-graphics-diagnostics)
- [<span data-ttu-id="fa084-137">Unity Profiler</span><span class="sxs-lookup"><span data-stu-id="fa084-137">Unity Profiler</span></span>](https://docs.unity3d.com/Manual/Profiler.html)
- [<span data-ttu-id="fa084-138">Unity フレームデバッガー</span><span class="sxs-lookup"><span data-stu-id="fa084-138">Unity Frame Debugger</span></span>](https://docs.unity3d.com/Manual/FrameDebugger.html)

### <a name="how-to-profile-in-any-environment"></a><span data-ttu-id="fa084-139">任意の環境でプロファイリングする方法</span><span class="sxs-lookup"><span data-stu-id="fa084-139">How to profile in any environment</span></span>

<span data-ttu-id="fa084-140">アプリが GPU であるか CPU にバインドされているかを判断する方法の1つは、レンダーターゲットの出力の解像度を下げることです。</span><span class="sxs-lookup"><span data-stu-id="fa084-140">One way to determine if your app is GPU or CPU bound is to lower the resolution of the render target output.</span></span> <span data-ttu-id="fa084-141">計算するピクセル数を減らすことにより、GPU の負荷が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="fa084-141">By reducing the number of pixels to calculate, you'll reduce your GPU load.</span></span> <span data-ttu-id="fa084-142">デバイスは、小さいテクスチャにレンダリングされ、その後、最後のイメージを表示するためにアップサンプリングされます。</span><span class="sxs-lookup"><span data-stu-id="fa084-142">The device will render to a smaller texture, then up-sample to display your final image.</span></span>

<span data-ttu-id="fa084-143">レンダリングの解像度を下げると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="fa084-143">After lowering rendering resolution, if:</span></span>
1) <span data-ttu-id="fa084-144">アプリケーションのフレームレートが **増加** し、 **GPU にバインド** されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fa084-144">Application framerate **increases**, then you're likely **GPU Bound**</span></span>
1) <span data-ttu-id="fa084-145">アプリケーションのフレームレートが **変更** されていないため、 **CPU バインド** されている可能性があります</span><span class="sxs-lookup"><span data-stu-id="fa084-145">Application framerate **unchanged**, then you're likely **CPU Bound**</span></span>

>[!NOTE]
><span data-ttu-id="fa084-146">Unity では、 *[XRSettings](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* プロパティを使用して、実行時にアプリケーションのレンダーターゲットの解像度を簡単に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="fa084-146">Unity provides the ability to easily modify the render target resolution of your application at runtime through the *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property.</span></span> <span data-ttu-id="fa084-147">デバイスに表示される最終的なイメージには、固定された解決策があります。</span><span class="sxs-lookup"><span data-stu-id="fa084-147">The final image presented on device has a fixed resolution.</span></span> <span data-ttu-id="fa084-148">このプラットフォームでは、解像度の低い出力をサンプリングして、ディスプレイに表示する解像度の高いイメージを構築します。</span><span class="sxs-lookup"><span data-stu-id="fa084-148">The platform will sample the lower resolution output to build a higher resolution image for rendering on displays.</span></span> 
>
>```CS
>UnityEngine.XR.XRSettings.renderScale = 0.7f;
>```

## <a name="how-to-improve-your-application"></a><span data-ttu-id="fa084-149">アプリケーションを改善する方法</span><span class="sxs-lookup"><span data-stu-id="fa084-149">How to improve your application</span></span>

### <a name="cpu-performance-recommendations"></a><span data-ttu-id="fa084-150">CPU のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="fa084-150">CPU performance recommendations</span></span>

<span data-ttu-id="fa084-151">一般に、CPU 上の mixed reality アプリケーションでほとんどの作業を行うには、シーンの "シミュレーション" を実行し、アプリケーションロジックを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa084-151">Generally, most work in a mixed reality application on the CPU involves doing the "simulation" of the scene and processing your application logic.</span></span> <span data-ttu-id="fa084-152">最適化の対象となる領域は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fa084-152">The following areas are targeted for optimization:</span></span>

- <span data-ttu-id="fa084-153">アニメーション</span><span class="sxs-lookup"><span data-stu-id="fa084-153">Animations</span></span>
- <span data-ttu-id="fa084-154">物理計算</span><span class="sxs-lookup"><span data-stu-id="fa084-154">Physics</span></span>
- <span data-ttu-id="fa084-155">メモリの割り当て</span><span class="sxs-lookup"><span data-stu-id="fa084-155">Memory allocations</span></span>
- <span data-ttu-id="fa084-156">複雑なアルゴリズム (</span><span class="sxs-lookup"><span data-stu-id="fa084-156">Complex algorithms (i.e</span></span> <span data-ttu-id="fa084-157">逆のキネマティック、パスの検索)</span><span class="sxs-lookup"><span data-stu-id="fa084-157">inverse kinematics, path-finding)</span></span>

### <a name="gpu-performance-recommendations"></a><span data-ttu-id="fa084-158">GPU のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="fa084-158">GPU performance recommendations</span></span>

#### <a name="understanding-bandwidth-vs-fill-rate"></a><span data-ttu-id="fa084-159">帯域幅とフィルレートを理解する</span><span class="sxs-lookup"><span data-stu-id="fa084-159">Understanding bandwidth vs. fill rate</span></span>
<span data-ttu-id="fa084-160">GPU でフレームをレンダリングする場合、アプリケーションはメモリ帯域幅またはフィルレートによって制限されます。</span><span class="sxs-lookup"><span data-stu-id="fa084-160">When rendering a frame on the GPU, an application is either bound by memory bandwidth or fill rate.</span></span>

- <span data-ttu-id="fa084-161">**メモリ帯域幅** は、GPU がメモリから実行できる読み取りと書き込みの比率です。</span><span class="sxs-lookup"><span data-stu-id="fa084-161">**Memory bandwidth** is the rate of reads and writes the GPU can do from memory</span></span>
    - <span data-ttu-id="fa084-162">帯域幅の制限を特定するには、テクスチャの品質を下げ、フレームレートが改善されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="fa084-162">To identify bandwidth limitations, reduce texture quality and check if the framerate has improved.</span></span>
    - <span data-ttu-id="fa084-163">Unity では、[プロジェクト設定の品質設定の **編集**] の [**テクスチャ品質**] を変更  >    >  **[](https://docs.unity3d.com/Manual/class-QualitySettings.html)** します。</span><span class="sxs-lookup"><span data-stu-id="fa084-163">In Unity, change **Texture Quality** in **Edit** > **Project Settings** > **[Quality Settings](https://docs.unity3d.com/Manual/class-QualitySettings.html)**.</span></span>
- <span data-ttu-id="fa084-164">**Fill rate** は、GPU によって1秒あたりに描画できるピクセルを表します。</span><span class="sxs-lookup"><span data-stu-id="fa084-164">**Fill rate** refers to the pixels that can be drawn per second by the GPU.</span></span>
    - <span data-ttu-id="fa084-165">フィルレートの制限を特定するには、表示解像度を下げ、フレームレートが改善されたかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="fa084-165">To identify fill rate limitations, lower the display resolution and check if framerate improved.</span></span> 
    - <span data-ttu-id="fa084-166">Unity では、renderViewportScale プロパティを使用し *[ます。 XRSettings](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)*</span><span class="sxs-lookup"><span data-stu-id="fa084-166">In Unity, use the  *[XRSettings.renderViewportScale](https://docs.unity3d.com/ScriptReference/XR.XRSettings-renderViewportScale.html)* property</span></span>

<span data-ttu-id="fa084-167">通常、メモリ帯域幅には次のいずれかの最適化が伴います。</span><span class="sxs-lookup"><span data-stu-id="fa084-167">Memory bandwidth generally involves optimizations to either:</span></span>
1) <span data-ttu-id="fa084-168">テクスチャ解像度を下げる</span><span class="sxs-lookup"><span data-stu-id="fa084-168">Lower texture resolutions</span></span>
2) <span data-ttu-id="fa084-169">使用するテクスチャ (法線、反射など) を減らす</span><span class="sxs-lookup"><span data-stu-id="fa084-169">Use fewer textures (normals, specular, and so on)</span></span>

<span data-ttu-id="fa084-170">Fill rate は、次のように、最終的に表示されるピクセルに対して計算する必要がある操作の数を減らすことに焦点を合わせています。</span><span class="sxs-lookup"><span data-stu-id="fa084-170">Fill rate is focused on reducing the number of operations that need to be computed for a final rendered pixel, including:</span></span>
1) <span data-ttu-id="fa084-171">表示/処理するオブジェクトの数</span><span class="sxs-lookup"><span data-stu-id="fa084-171">Number of objects to render/process</span></span>
2) <span data-ttu-id="fa084-172">シェーダーあたりの操作数</span><span class="sxs-lookup"><span data-stu-id="fa084-172">Number of operations per shader</span></span>
3) <span data-ttu-id="fa084-173">最終的な結果に対する GPU ステージの数 (ジオメトリシェーダー、処理後の効果など)</span><span class="sxs-lookup"><span data-stu-id="fa084-173">Number of GPU stages to final result (geometry shaders, post-processing effects, and so on)</span></span>
4) <span data-ttu-id="fa084-174">レンダリングするピクセル数 (表示解像度)</span><span class="sxs-lookup"><span data-stu-id="fa084-174">Number of pixels to render (display resolution)</span></span>

#### <a name="reduce-polygon-count"></a><span data-ttu-id="fa084-175">多角形の数を減らす</span><span class="sxs-lookup"><span data-stu-id="fa084-175">Reduce polygon count</span></span>

<span data-ttu-id="fa084-176">多角形の数が多いほど GPU に対する操作が多くなります。そのため、シーン [の多角形の数を減らす](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) とレンダリング時間が短縮されます。</span><span class="sxs-lookup"><span data-stu-id="fa084-176">Higher polygon counts result in more operations for the GPU, so [reducing the number of polygons](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets) in your scene reduces the render time.</span></span> <span data-ttu-id="fa084-177">ジオメトリの負荷が高くなる要因は他にもありますが、polygon count は、シーンをレンダリングするために必要な作業量を決定するための最も簡単なメトリックです。</span><span class="sxs-lookup"><span data-stu-id="fa084-177">There are other factors that make shading the geometry expensive, but polygon count is the simplest metric to determine how much work it will take to render a scene.</span></span>

#### <a name="limit-overdraw"></a><span data-ttu-id="fa084-178">オーバードローを制限する</span><span class="sxs-lookup"><span data-stu-id="fa084-178">Limit overdraw</span></span>

<span data-ttu-id="fa084-179">Occluding オブジェクトによって非表示になっているため、複数のオブジェクトがレンダリングされても画面に表示されない場合は、高いオーバードローが発生します。</span><span class="sxs-lookup"><span data-stu-id="fa084-179">High overdraw occurs when multiple objects are rendered but not shown on screen as they're hidden by an occluding object.</span></span> <span data-ttu-id="fa084-180">その背後にオブジェクトがある壁を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="fa084-180">Imagine looking at a wall that has objects behind it.</span></span> <span data-ttu-id="fa084-181">すべてのジオメトリはレンダリングのために処理されますが、不透明なウォールだけをレンダリングする必要があるため、不要な操作になります。</span><span class="sxs-lookup"><span data-stu-id="fa084-181">All of the geometry would be processed for rendering, but only the opaque wall needs to be rendered, which results in unnecessary operations.</span></span>

#### <a name="shaders"></a><span data-ttu-id="fa084-182">シェーダー</span><span class="sxs-lookup"><span data-stu-id="fa084-182">Shaders</span></span>

<span data-ttu-id="fa084-183">シェーダーは、GPU 上で実行され、レンダリングの2つの重要な手順を実行する小さなプログラムです。</span><span class="sxs-lookup"><span data-stu-id="fa084-183">Shaders are small programs that run on the GPU and do two important steps in rendering:</span></span>
1) <span data-ttu-id="fa084-184">描画する頂点と画面空間内の位置を決定する (頂点シェーダー)</span><span class="sxs-lookup"><span data-stu-id="fa084-184">Determining which vertices should be drawn and where they are in screen space (the Vertex shader)</span></span>
    - <span data-ttu-id="fa084-185">頂点シェーダーは、メッシュごとに頂点ごとに実行されます。</span><span class="sxs-lookup"><span data-stu-id="fa084-185">The Vertex shader is executed per vertex for every mesh.</span></span>
2) <span data-ttu-id="fa084-186">各ピクセルの色を決定する (ピクセルシェーダー)</span><span class="sxs-lookup"><span data-stu-id="fa084-186">Determining the color of each pixel (the Pixel shader)</span></span>
    - <span data-ttu-id="fa084-187">ピクセルシェーダーはピクセルごとに実行され、ターゲットのレンダリングテクスチャに対してジオメトリによってレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="fa084-187">The Pixel shader is executed per pixel and rendered by the geometry to the target render texture.</span></span>

<span data-ttu-id="fa084-188">通常、シェーダーでは、多くの変換と照明計算が行われます。</span><span class="sxs-lookup"><span data-stu-id="fa084-188">Typically, shaders do many transformations and lighting calculations.</span></span> <span data-ttu-id="fa084-189">複雑な照明モデル、影、およびその他の操作によって、優れた結果が得られる場合もありますが、価格もあります。</span><span class="sxs-lookup"><span data-stu-id="fa084-189">Although complex lighting models, shadows, and other operations can generate fantastic results, they also come with a price.</span></span> <span data-ttu-id="fa084-190">シェーダーで計算される操作の数を減らすと、フレームあたりの GPU に必要な作業が大幅に減少します。</span><span class="sxs-lookup"><span data-stu-id="fa084-190">Reducing the number of operations computed in shaders can greatly reduce the work needed for the GPU per frame.</span></span>

##### <a name="shader-coding-recommendations"></a><span data-ttu-id="fa084-191">シェーダーのコーディングに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="fa084-191">Shader coding recommendations</span></span>

- <span data-ttu-id="fa084-192">可能な限り、バイリニアフィルタリングを使用する</span><span class="sxs-lookup"><span data-stu-id="fa084-192">Use bilinear filtering, whenever possible</span></span>
- <span data-ttu-id="fa084-193">MAD 組み込みを使用して乗算と加算を同時に行うように、式を再配置します。</span><span class="sxs-lookup"><span data-stu-id="fa084-193">Rearrange expressions to use MAD intrinsics to do a multiply and an add at the same time</span></span>
- <span data-ttu-id="fa084-194">CPU で可能な限り Precalculate し、素材に定数として渡します。</span><span class="sxs-lookup"><span data-stu-id="fa084-194">Precalculate as much as possible on the CPU and pass as constants to the material</span></span>
- <span data-ttu-id="fa084-195">**ピクセルシェーダーから頂点シェーダーへの移動操作を優先する**</span><span class="sxs-lookup"><span data-stu-id="fa084-195">**Favor moving operations from the pixel shader to the vertex shader**</span></span>
    - <span data-ttu-id="fa084-196">一般に、頂点の数はピクセル数よりもはるかに小さくなります (720p は921600ピクセル、1080p は2073600ピクセル、など)。</span><span class="sxs-lookup"><span data-stu-id="fa084-196">Generally, the number of vertices is much smaller than the number of pixels (720p is 921,600 pixels, 1080p is 2,073,600 pixels, and so on)</span></span>

#### <a name="remove-gpu-stages"></a><span data-ttu-id="fa084-197">GPU ステージの削除</span><span class="sxs-lookup"><span data-stu-id="fa084-197">Remove GPU stages</span></span>

<span data-ttu-id="fa084-198">処理後の影響はコストが高く、MSAA のようなアンチエイリアシング手法を含むアプリケーションのフィルレートが高くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fa084-198">Post-processing effects can be expensive and increase the fill rate of your application, including anti-aliasing techniques like MSAA.</span></span> <span data-ttu-id="fa084-199">HoloLens では、これらの手法や、geometry、ハル、コンピューティングシェーダーなどの追加のシェーダーステージを回避することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="fa084-199">On HoloLens, we recommended avoiding these techniques and additional shader stages such as geometry, hull, and compute shaders.</span></span>

## <a name="memory-recommendations"></a><span data-ttu-id="fa084-200">メモリに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="fa084-200">Memory recommendations</span></span>

<span data-ttu-id="fa084-201">過剰なメモリの割り当ておよび解放操作を行うと、パフォーマンスが低下したり、フレームがフリーズしたり、その他の有害な動作が発生したりする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fa084-201">Excessive memory allocation and deallocation operations can result in inconsistent performance, frozen frames, and other detrimental behavior.</span></span> <span data-ttu-id="fa084-202">メモリ管理はガベージコレクターによって制御されるため、Unity で開発するときは、メモリに関する考慮事項を理解することが特に重要です。</span><span class="sxs-lookup"><span data-stu-id="fa084-202">It's especially important to understand memory considerations when developing in Unity, since memory management is controlled by the garbage collector.</span></span>

#### <a name="object-pooling"></a><span data-ttu-id="fa084-203">オブジェクト プーリング</span><span class="sxs-lookup"><span data-stu-id="fa084-203">Object pooling</span></span>

<span data-ttu-id="fa084-204">オブジェクトプールは、オブジェクトの継続的な割り当てと割り当て解除のコストを削減するための一般的な手法です。</span><span class="sxs-lookup"><span data-stu-id="fa084-204">Object pooling is a popular technique to reduce the cost of continuous allocations and deallocations of objects.</span></span> <span data-ttu-id="fa084-205">これを行うには、同一のオブジェクトの大規模なプールを割り当て、時間の経過と共にオブジェクトを絶えず生成して破棄するのではなく、このプールの非アクティブで使用可能なインスタンスを再利用します。</span><span class="sxs-lookup"><span data-stu-id="fa084-205">This is done by allocating a large pool of identical objects and reusing inactive, available instances from this pool instead of constantly spawning and destroying objects over time.</span></span> <span data-ttu-id="fa084-206">オブジェクト プールは、アプリの間の有効期間が一定ではない再使用可能なコンポーネントに最適です。</span><span class="sxs-lookup"><span data-stu-id="fa084-206">Object pools are great for reuseable components that have variable lifetime during an app.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa084-207">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa084-207">See also</span></span>
- [<span data-ttu-id="fa084-208">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="fa084-208">Performance recommendations for Unity</span></span>](../unity/performance-recommendations-for-unity.md)
- [<span data-ttu-id="fa084-209">Unity で推奨される設定</span><span class="sxs-lookup"><span data-stu-id="fa084-209">Recommended settings for Unity</span></span>](../unity/recommended-settings-for-unity.md)
- [<span data-ttu-id="fa084-210">3D モデルの最適化</span><span class="sxs-lookup"><span data-stu-id="fa084-210">Optimize 3D models</span></span>](/dynamics365/mixed-reality/import-tool/optimize-models#performance-targets)
- [<span data-ttu-id="fa084-211">リアルタイム3D モデルの変換と最適化に関するベストプラクティス</span><span class="sxs-lookup"><span data-stu-id="fa084-211">Best practices for converting and optimizing real-time 3D Models</span></span>](/dynamics365/mixed-reality/import-tool/best-practices)