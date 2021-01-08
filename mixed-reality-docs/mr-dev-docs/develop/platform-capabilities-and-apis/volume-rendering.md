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
# <a name="volume-rendering"></a>ボリューム レンダリング

医療 MRI またはエンジニアリングボリュームについては、 [Wikipedia のボリュームレンダリング](https://en.wikipedia.org/wiki/Volume_rendering)を参照してください。 これらの ' 容量 images ' には、 [多角形メッシュ](https://en.wikipedia.org/wiki/Polygon_mesh)などの表面として簡単には表現できない、ボリューム全体の不透明度と色を含む豊富な情報が含まれています。

パフォーマンスを向上させるための主要ソリューション
1. 問題: 単純なアプローチ: ボリューム全体を表示します。一般に、実行速度が低下しています
2. 良好: カットプレーン: ボリュームの1つのスライスのみを表示する
3. 良い: サブボリュームを切る: ボリュームのレイヤーをいくつか表示する
4. 良好: ボリュームレンダリングの解像度を下げます (「混合解像度シーンのレンダリング」を参照してください)。

アプリケーションから特定のフレームの画面に転送できる情報は、メモリ帯域幅の合計である特定の量だけです。 また、プレゼンテーション用にデータを変換するために必要なすべての処理 (または "網掛け") には時間が必要です。 ボリュームレンダリングを行う際の主な考慮事項は次のとおりです。
* Screen-Width * Screen-Height * Screen-Count * ボリュームレイヤー-ピクセルあたりの合計-ボリューム-サンプル-フレームあたり
* 1028 * 720 * 2 * 256 = 378961920 (100%)(フル res ボリューム: サンプル数が多すぎます)
* 1028 * 720 * 2 * 1 = 1480320 (0.3% of full) (シンスライス: 1 ピクセルあたり1サンプル、スムーズに実行)
* 1028 * 720 * 2 * 10 = 14803200 (3.9% of full) (サブボリュームスライス: 1 ピクセルあたり10個のサンプルがスムーズに実行され、3d が見られます)
* 200 * 200 * 2 * 256 = 2048万 (フルの 5%) (小さい方のボリューム: より少ないピクセル、フルボリューム、3d の外観は少しぼやけています)

## <a name="representing-3d-textures"></a>3D テクスチャの表現

CPU:

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

GPU の場合:

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

## <a name="shading-and-gradients"></a>網掛けとグラデーション

便利な視覚化のために、MRI などのボリュームを網掛けする方法。 主要な方法としては、輝度を表示する "濃度ウィンドウ" (最小値と最大値) を設定し、その領域を拡大して、黒と白の輝度を表示します。 次に、"カラーランプ" をその範囲内の値に適用し、テクスチャとして保存することで、照度スペクトルのさまざまな部分に影の異なる色を設定できます。

```
float4 ShadeVol( float intensity ) {
   float unitIntensity = saturate( intensity - IntensityMin / ( IntensityMax - IntensityMin ) );
   // Simple two point black and white intensity:
   color.rgba = unitIntensity;
   // Color ramp method:
   color.rgba = tex2d( ColorRampTexture, float2( unitIntensity, 0 ) );
```

多くのアプリケーションでは、未加工の輝度値と ' セグメンテーションインデックス ' の両方をボリュームに格納しています (スキンやボーンなどのさまざまな部分を分割します。これらのセグメントは、専用ツールの専門家によって作成されます)。 これを上記の方法と組み合わせて、セグメントインデックスごとに異なる色または異なるカラーランプを作成できます。

```
// Change color to match segment index (fade each segment towards black):
 color.rgb = SegmentColors[ segment_index ] * color.a; // brighter alpha gives brighter color
```

## <a name="volume-slicing-in-a-shader"></a>シェーダーでのボリュームスライス

最初の優れた手順は、"スライス平面" を作成することです。これは、ボリューム間を移動し、"スライスする" と、各ポイントでのスキャン値を指定します。 これは、ワールド空間におけるボリュームの場所を表す ' VolumeSpace ' キューブがあることを前提としています。これは、ポイントを配置するための参照として使用できます。

```
// In the vertex shader:
 float4 worldPos = mul(_Object2World, float4(input.vertex.xyz, 1));
 float4 volSpace = mul(_WorldToVolume, float4(worldPos, 1));
```

```
// In the pixel shader:
 float4 color = ShadeVol( SampleVol( volSpace ) );
```

## <a name="volume-tracing-in-shaders"></a>シェーダーのボリュームトレース

GPU を使用して、サブボリュームのトレースを実行する方法 (いくつかの操作について説明します。次に、データのレイヤーをバックエンドから順に見ていきます)。

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

## <a name="whole-volume-rendering"></a>ボリューム全体のレンダリング

上記のサブボリュームコードを変更すると、次のことが得られます。

```
float4 volTraceSubVolume(float3 objPosStart, float3 cameraPosVolSpace) {
   float maxDepth = 1.73; // sqrt(3), max distance from point on cube to any other point on cube
   int maxSamples = 400; // just in case, keep this value within bounds
   // not shown: trim front and back positions to both be within the cube
   int distanceInVoxels = length(UnitVolumeToIntVolume(frontPos - backPos)); // measure distance in voxels
   int numLoops = min( distanceInVoxels, maxSamples ); // put a min on the voxels to sample
```

## <a name="mixed-resolution-scene-rendering"></a>混合解像度シーンのレンダリング

低解像度でシーンの一部をレンダリングして、その場を戻す方法:
1. 2つのスクリーンカメラ (各フレームを更新するために1つずつ) を設定します。
2. カメラがレンダリングされる2つの低解像度のレンダーターゲット (それぞれ 200 x 200) をセットアップします。
3. ユーザーの前に移動するクワッドを設定する

各フレーム:
1. 各視点のレンダーターゲットを低解像度 (ボリュームデータ、負荷の高いシェーダーなど) で描画します。
2. シーンを完全な解像度 (メッシュ、UI など) として通常どおり描画します。
3. ユーザーの前に四角形を描画し、そのシーンに対して低 res のレンダリングを射影します。
4. 結果: 低解像度で高密度ボリュームデータを使用する完全解決要素のビジュアル組み合わせ
