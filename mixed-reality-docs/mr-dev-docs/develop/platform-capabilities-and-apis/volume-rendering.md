---
title: ボリューム レンダリング
description: Windows Mixed Reality の不透明度と色を使用して、リッチ容量イメージを効率的にレンダリングする方法について説明します。
author: kevinkennedy
ms.author: kkennedy
ms.date: 03/21/2018
ms.topic: article
keywords: 容量イメージ, ボリュームレンダリング, パフォーマンス, mixed reality
ms.openlocfilehash: 2a76be80d786aea0c8bc1bd364155fa37d37e151
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008782"
---
# <a name="volume-rendering"></a><span data-ttu-id="4e8b0-104">ボリューム レンダリング</span><span class="sxs-lookup"><span data-stu-id="4e8b0-104">Volume rendering</span></span>

<span data-ttu-id="4e8b0-105">医療 MRI またはエンジニアリングボリュームについては、 [Wikipedia のボリュームレンダリング](https://en.wikipedia.org/wiki/Volume_rendering)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-105">For medical MRI or engineering volumes, see [Volume Rendering on Wikipedia](https://en.wikipedia.org/wiki/Volume_rendering).</span></span> <span data-ttu-id="4e8b0-106">これらの ' 容量 images ' には、 [多角形メッシュ](https://en.wikipedia.org/wiki/Polygon_mesh)などの表面として簡単には表現できない、ボリューム全体の不透明度と色を含む豊富な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-106">These 'volumetric images' contain rich information with opacity and color throughout the volume that cannot be easily expressed as surfaces such as [polygonal meshes](https://en.wikipedia.org/wiki/Polygon_mesh).</span></span>

<span data-ttu-id="4e8b0-107">パフォーマンスを向上させるための主要ソリューション</span><span class="sxs-lookup"><span data-stu-id="4e8b0-107">Key solutions to improve performance</span></span>
1. <span data-ttu-id="4e8b0-108">問題: 単純なアプローチ: ボリューム全体を表示します。一般に、実行速度が低下しています</span><span class="sxs-lookup"><span data-stu-id="4e8b0-108">BAD: Naïve Approach: Show Whole Volume, generally runs too slowly</span></span>
2. <span data-ttu-id="4e8b0-109">良好: カットプレーン: ボリュームの1つのスライスのみを表示する</span><span class="sxs-lookup"><span data-stu-id="4e8b0-109">GOOD: Cutting Plane: Show only a single slice of the volume</span></span>
3. <span data-ttu-id="4e8b0-110">良い: サブボリュームを切る: ボリュームのレイヤーをいくつか表示する</span><span class="sxs-lookup"><span data-stu-id="4e8b0-110">GOOD: Cutting Sub-Volume: Show only a few layers of the volume</span></span>
4. <span data-ttu-id="4e8b0-111">良好: ボリュームレンダリングの解像度を下げます (「混合解像度シーンのレンダリング」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-111">GOOD: Lower the resolution of the volume rendering (see 'Mixed Resolution Scene Rendering')</span></span>

<span data-ttu-id="4e8b0-112">アプリケーションから特定のフレームの画面に転送できる情報は、メモリ帯域幅の合計である特定の量だけです。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-112">There's only a certain amount of information that can be transferred from the application to the screen in any particular frame, which is the total memory bandwidth.</span></span> <span data-ttu-id="4e8b0-113">また、プレゼンテーション用にデータを変換するために必要なすべての処理 (または "網掛け") には時間が必要です。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-113">Also, any processing (or 'shading') required to transform that data for presentation requires time.</span></span> <span data-ttu-id="4e8b0-114">ボリュームレンダリングを行う際の主な考慮事項は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-114">The primary considerations when doing volume rendering are as such:</span></span>
* <span data-ttu-id="4e8b0-115">Screen-Width \* Screen-Height \* Screen-Count \* ボリュームレイヤー-ピクセルあたりの合計-ボリューム-サンプル-フレームあたり</span><span class="sxs-lookup"><span data-stu-id="4e8b0-115">Screen-Width \* Screen-Height \* Screen-Count \* Volume-Layers-On-That-Pixel = Total-Volume-Samples-Per-Frame</span></span>
* <span data-ttu-id="4e8b0-116">1028 \* 720 \* 2 \* 256 = 378961920 (100%)(フル res ボリューム: サンプル数が多すぎます)</span><span class="sxs-lookup"><span data-stu-id="4e8b0-116">1028 \* 720 \* 2 \* 256 = 378961920 (100%) (full res volume: too many samples)</span></span>
* <span data-ttu-id="4e8b0-117">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (シンスライス: 1 ピクセルあたり1サンプル、スムーズに実行)</span><span class="sxs-lookup"><span data-stu-id="4e8b0-117">1028 \* 720 \* 2 \* 1 = 1480320 (0.3% of full) (thin slice: 1 sample per pixel, runs smoothly)</span></span>
* <span data-ttu-id="4e8b0-118">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (サブボリュームスライス: 1 ピクセルあたり10個のサンプルがスムーズに実行され、3d が見られます)</span><span class="sxs-lookup"><span data-stu-id="4e8b0-118">1028 \* 720 \* 2 \* 10 = 14803200 (3.9% of full) (subvolume slice: 10 samples per pixel, runs fairly smoothly, looks 3d)</span></span>
* <span data-ttu-id="4e8b0-119">200 \* 200 \* 2 \* 256 = 2048万 (フルの 5%) (小さい方のボリューム: より少ないピクセル、フルボリューム、3d の外観は少しぼやけています)</span><span class="sxs-lookup"><span data-stu-id="4e8b0-119">200 \* 200 \* 2 \* 256 = 20480000 (5% of full) (lower res volume: fewer pixels, full volume, looks 3d but a bit blurry)</span></span>

## <a name="representing-3d-textures"></a><span data-ttu-id="4e8b0-120">3D テクスチャの表現</span><span class="sxs-lookup"><span data-stu-id="4e8b0-120">Representing 3D Textures</span></span>

<span data-ttu-id="4e8b0-121">CPU:</span><span class="sxs-lookup"><span data-stu-id="4e8b0-121">On the CPU:</span></span>

```
public struct Int3 { public int X, Y, Z; /* ... */ }
 public class VolumeHeader  {
   public readonly Int3 Size;
   public VolumeHeader(Int3 size) { this.Size = size;  }
   public int CubicToLinearIndex(Int3 index) {
     return index.X + (index.Y * (Size.X)) + (index.Z * (Size.X * Size.Y));
   }
   public Int3 LinearToCubicIndex(int linearIndex)
   {
     return new Int3((linearIndex / 1) % Size.X,
       (linearIndex / Size.X) % Size.Y,
       (linearIndex / (Size.X * Size.Y)) % Size.Z);
   }
   /* ... */
 }
 public class VolumeBuffer<T> {
   public readonly VolumeHeader Header;
   public readonly T[] DataArray;
   public T GetVoxel(Int3 pos)        {
     return this.DataArray[this.Header.CubicToLinearIndex(pos)];
   }
   public void SetVoxel(Int3 pos, T val)        {
     this.DataArray[this.Header.CubicToLinearIndex(pos)] = val;
   }
   public T this[Int3 pos] {
     get { return this.GetVoxel(pos); }
     set { this.SetVoxel(pos, value); }
   }
   /* ... */
 }
```

<span data-ttu-id="4e8b0-122">GPU の場合:</span><span class="sxs-lookup"><span data-stu-id="4e8b0-122">On the GPU:</span></span>

```
float3 _VolBufferSize;
 int3 UnitVolumeToIntVolume(float3 coord) {
   return (int3)( coord * _VolBufferSize.xyz );
 }
 int IntVolumeToLinearIndex(int3 coord, int3 size) {
   return coord.x + ( coord.y * size.x ) + ( coord.z * ( size.x * size.y ) );
 }
 uniform StructuredBuffer<float> _VolBuffer;
 float SampleVol(float3 coord3 ) {
   int3 intIndex3 = UnitVolumeToIntVolume( coord3 );
   int index1D = IntVolumeToLinearIndex( intIndex3, _VolBufferSize.xyz);
   return __VolBuffer[index1D];
 }
```

## <a name="shading-and-gradients"></a><span data-ttu-id="4e8b0-123">網掛けとグラデーション</span><span class="sxs-lookup"><span data-stu-id="4e8b0-123">Shading and Gradients</span></span>

<span data-ttu-id="4e8b0-124">便利な視覚化のために、MRI などのボリュームを網掛けする方法。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-124">How to shade a volume, such as MRI, for useful visualization.</span></span> <span data-ttu-id="4e8b0-125">主要な方法としては、輝度を表示する "濃度ウィンドウ" (最小値と最大値) を設定し、その領域を拡大して、黒と白の輝度を表示します。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-125">The primary method is to have an 'intensity window' (a min and max) that you want to see intensities within, and simply scale into that space to see the black and white intensity.</span></span> <span data-ttu-id="4e8b0-126">次に、"カラーランプ" をその範囲内の値に適用し、テクスチャとして保存することで、照度スペクトルのさまざまな部分に影の異なる色を設定できます。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-126">A 'color ramp' can then be applied to the values within that range, and stored as a texture, so that different parts of the intensity spectrum can be shaded different colors:</span></span>

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

<span data-ttu-id="4e8b0-127">多くのアプリケーションでは、未加工の輝度値と ' セグメンテーションインデックス ' の両方をボリュームに格納しています (スキンやボーンなどのさまざまな部分を分割します。これらのセグメントは、専用ツールの専門家によって作成されます)。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-127">In many of our applications, we store in our volume both a raw intensity value and a 'segmentation index' (to segment different parts such as skin and bone; these segments are created by experts in dedicated tools).</span></span> <span data-ttu-id="4e8b0-128">これを上記の方法と組み合わせて、セグメントインデックスごとに異なる色または異なるカラーランプを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-128">This can be combined with the approach above to put a different color, or even different color ramp for each segment index:</span></span>

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a><span data-ttu-id="4e8b0-129">シェーダーでのボリュームスライス</span><span class="sxs-lookup"><span data-stu-id="4e8b0-129">Volume Slicing in a Shader</span></span>

<span data-ttu-id="4e8b0-130">最初の優れた手順は、"スライス平面" を作成することです。これは、ボリューム間を移動し、"スライスする" と、各ポイントでのスキャン値を指定します。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-130">A great first step is to create a "slicing plane" that can move through the volume, 'slicing it', and how the scan values at each point.</span></span> <span data-ttu-id="4e8b0-131">これは、ワールド空間におけるボリュームの場所を表す ' VolumeSpace ' キューブがあることを前提としています。これは、ポイントを配置するための参照として使用できます。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-131">This assumes that there's a 'VolumeSpace' cube, which represents where the volume is in world space, that can be used as a reference for placing the points:</span></span>

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a><span data-ttu-id="4e8b0-132">シェーダーのボリュームトレース</span><span class="sxs-lookup"><span data-stu-id="4e8b0-132">Volume Tracing in Shaders</span></span>

<span data-ttu-id="4e8b0-133">GPU を使用して、サブボリュームのトレースを実行する方法 (いくつかの操作について説明します。次に、データのレイヤーをバックエンドから順に見ていきます)。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-133">How to use the GPU to do subvolume tracing (walks a few voxels deep, then layers on the data from back to front):</span></span>

```
float4 AlphaBlend(float4 dst, float4 src) {
   float4 res = (src * src.a) + (dst - dst * src.a);
   res.a = src.a + (dst.a - dst.a*src.a);
   return res;
 }
 float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 0.15; // depth in volume space, customize!!!
   float numLoops = 10; // can be 400 on nice PC
   float4 curColor = float4(0, 0, 0, 0);
   // Figure out front and back volume coords to walk through:
   float3 frontCoord = objPosStart;
   float3 backCoord = frontPos + (normalize(cameraPosVolSpace - objPosStart) * maxDepth);
   float3 stepCoord = (frontCoord - backCoord) / numLoops;
   float3 curCoord = backCoord;
   // Add per-pixel random offset, avoids layer aliasing:
   curCoord += stepCoord * RandomFromPositionFast(objPosStart);
   // Walk from back to front (to make front appear in-front of back):
   for (float i = 0; i < numLoops; i++) {
     float intensity = SampleVol(curCoord);
     float4 shaded = ShadeVol(intensity);
     curColor = AlphaBlend(curColor, shaded);
     curCoord += stepCoord;
   }
   return curColor;
 }
```

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos.xyz, 1));
 float4 cameraInVolSpace = mul(_WorldToVolume, float4(_WorldSpaceCameraPos.xyz, 1));
```

```
// In the pixel shader:
 float4 color = volTraceSubVolume( volSpace, cameraInVolSpace );
```

## <a name="whole-volume-rendering"></a><span data-ttu-id="4e8b0-134">ボリューム全体のレンダリング</span><span class="sxs-lookup"><span data-stu-id="4e8b0-134">Whole Volume Rendering</span></span>

<span data-ttu-id="4e8b0-135">上記のサブボリュームコードを変更すると、次のことが得られます。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-135">Modifying the subvolume code above, we get:</span></span>

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a><span data-ttu-id="4e8b0-136">混合解像度シーンのレンダリング</span><span class="sxs-lookup"><span data-stu-id="4e8b0-136">Mixed Resolution Scene Rendering</span></span>

<span data-ttu-id="4e8b0-137">低解像度でシーンの一部をレンダリングして、その場を戻す方法:</span><span class="sxs-lookup"><span data-stu-id="4e8b0-137">How to render a part of the scene with a low resolution and put it back in place:</span></span>
1. <span data-ttu-id="4e8b0-138">2つのスクリーンカメラ (各フレームを更新するために1つずつ) を設定します。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-138">Setup two off-screen cameras, one to follow each eye that update each frame</span></span>
2. <span data-ttu-id="4e8b0-139">カメラがレンダリングされる2つの低解像度のレンダーターゲット (それぞれ 200 x 200) をセットアップします。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-139">Setup two low-resolution render targets (that is, 200x200 each) that the cameras render into</span></span>
3. <span data-ttu-id="4e8b0-140">ユーザーの前に移動するクワッドを設定する</span><span class="sxs-lookup"><span data-stu-id="4e8b0-140">Set up a quad that moves in front of the user</span></span>

<span data-ttu-id="4e8b0-141">各フレーム:</span><span class="sxs-lookup"><span data-stu-id="4e8b0-141">Each Frame:</span></span>
1. <span data-ttu-id="4e8b0-142">各視点のレンダーターゲットを低解像度 (ボリュームデータ、負荷の高いシェーダーなど) で描画します。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-142">Draw the render targets for each eye at low-resolution (volume data, expensive shaders, and so on)</span></span>
2. <span data-ttu-id="4e8b0-143">シーンを完全な解像度 (メッシュ、UI など) として通常どおり描画します。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-143">Draw the scene normally as full resolution (meshes, UI, and so on)</span></span>
3. <span data-ttu-id="4e8b0-144">ユーザーの前に四角形を描画し、そのシーンに対して低 res のレンダリングを射影します。</span><span class="sxs-lookup"><span data-stu-id="4e8b0-144">Draw a quad in front of the user, over the scene, and project the low-res renders onto that</span></span>
4. <span data-ttu-id="4e8b0-145">結果: 低解像度で高密度ボリュームデータを使用する完全解決要素のビジュアル組み合わせ</span><span class="sxs-lookup"><span data-stu-id="4e8b0-145">Result: visual combination of full-resolution elements with low-resolution but high-density volume data</span></span>
