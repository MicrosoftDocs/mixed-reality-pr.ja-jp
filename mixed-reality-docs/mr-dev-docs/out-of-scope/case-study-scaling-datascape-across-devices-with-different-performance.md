---
title: ケーススタディ-パフォーマンスが異なるデバイス間での Datascape スケーリング
description: このケーススタディでは、Microsoft 開発者が Datascape を最適化して、さまざまなパフォーマンス機能を備えたデバイスで魅力的なエクスペリエンスを提供する方法について説明します。
author: danandersson
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: イマーシブヘッドセット、パフォーマンスの最適化、VR、ケーススタディ
ms.openlocfilehash: 37a40a67dbe41ba9a53fccaff1dee76d56f7b178
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687362"
---
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a><span data-ttu-id="13c58-104">ケーススタディ-パフォーマンスが異なるデバイス間での Datascape スケーリング</span><span class="sxs-lookup"><span data-stu-id="13c58-104">Case study - Scaling Datascape across devices with different performance</span></span>

<span data-ttu-id="13c58-105">Datascape は、Microsoft 社内で開発された Windows Mixed Reality アプリケーションで、地形データの上に気象データを表示することに重点を置いています。</span><span class="sxs-lookup"><span data-stu-id="13c58-105">Datascape is a Windows Mixed Reality application developed internally at Microsoft where we focused on displaying weather data on top of terrain data.</span></span> <span data-ttu-id="13c58-106">このアプリケーションでは、ユーザーを holographic データ可視化で囲むことによって、ユーザーが混合現実のデータを検出することによって得られる一意の洞察について説明します。</span><span class="sxs-lookup"><span data-stu-id="13c58-106">The application explores the unique insights users gain from discovering data in mixed reality by surrounding the user with holographic data visualization.</span></span>

<span data-ttu-id="13c58-107">Datascape では、さまざまなハードウェア機能を備えたさまざまなプラットフォームを対象にしたいと考えています。これは、Microsoft HoloLens から Windows Mixed Reality のクロスヘッドヘッドセットや、低電力の Pc からハイエンド GPU を搭載した最新の Pc まで多岐にわたります。</span><span class="sxs-lookup"><span data-stu-id="13c58-107">For Datascape we wanted to target a variety of platforms with different hardware capabilities ranging from Microsoft HoloLens to Windows Mixed Reality immersive headsets, and from lower-powered PCs to the very latest PCs with high-end GPU.</span></span> <span data-ttu-id="13c58-108">主な課題は、高いフレームレートで実行しながら、グラフィックス機能が大幅に異なるデバイスで、視覚的に魅力のあるシーンをレンダリングすることでした。</span><span class="sxs-lookup"><span data-stu-id="13c58-108">The main challenge was rendering our scene in a visually appealing matter on devices with wildly different graphics capabilities while executing at a high framerate.</span></span>

<span data-ttu-id="13c58-109">このケーススタディでは、GPU 集中型のシステムのいくつかを作成するために使用されるプロセスと手法について説明し、発生した問題とその克服について説明します。</span><span class="sxs-lookup"><span data-stu-id="13c58-109">This case study will walk through the process and techniques used to create some of our more GPU-intensive systems, describing the problems we encountered and how we overcame them.</span></span>

## <a name="transparency-and-overdraw"></a><span data-ttu-id="13c58-110">透明度とオーバードロー</span><span class="sxs-lookup"><span data-stu-id="13c58-110">Transparency and overdraw</span></span>

<span data-ttu-id="13c58-111">GPU では透明度が高くなる可能性があるため、メインレンダリング格闘は透明度で処理されます。</span><span class="sxs-lookup"><span data-stu-id="13c58-111">Our main rendering struggles dealt with transparency, since transparency can be expensive on a GPU.</span></span>

<span data-ttu-id="13c58-112">深度バッファーへの書き込み中に、ソリッドジオメトリを前面にレンダリングして、そのピクセルの背後にある今後のピクセルを破棄しないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="13c58-112">Solid geometry can be rendered front to back while writing to the depth buffer, stopping any future pixels located behind that pixel from being discarded.</span></span> <span data-ttu-id="13c58-113">これにより、非表示のピクセルがピクセルシェーダーを実行できなくなり、プロセスが大幅に高速化されます。</span><span class="sxs-lookup"><span data-stu-id="13c58-113">This prevents hidden pixels from executing the pixel shader, speeding up the process significantly.</span></span> <span data-ttu-id="13c58-114">Geometry が最適に並べ替えられている場合は、画面上の各ピクセルが1回だけ描画されます。</span><span class="sxs-lookup"><span data-stu-id="13c58-114">If geometry is sorted optimally, each pixel on the screen will be drawn only once.</span></span>

<span data-ttu-id="13c58-115">透明なジオメトリは最前面に並べ替える必要があり、ピクセルシェーダーの出力を画面上の現在のピクセルにブレンドすることに依存します。</span><span class="sxs-lookup"><span data-stu-id="13c58-115">Transparent geometry needs to be sorted back to front and relies on blending the output of the pixel shader to the current pixel on the screen.</span></span> <span data-ttu-id="13c58-116">これにより、画面上の各ピクセルがフレームごとに複数回描画される可能性があります。これは、オーバードローと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="13c58-116">This can result in each pixel on the screen being drawn to multiple times per frame, referred to as overdraw.</span></span>

<span data-ttu-id="13c58-117">HoloLens およびメインストリーム Pc の場合、画面はほんの数回しか入力できないため、透明なレンダリングの問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="13c58-117">For HoloLens and mainstream PCs, the screen can only be filled a handful of times, making transparent rendering problematic.</span></span>

## <a name="introduction-to-datascape-scene-components"></a><span data-ttu-id="13c58-118">Datascape コンポーネントの概要</span><span class="sxs-lookup"><span data-stu-id="13c58-118">Introduction to Datascape scene components</span></span>

<span data-ttu-id="13c58-119">シーンには3つの主要なコンポーネントがありました。 **UI、マップ** 、および **天気** 。</span><span class="sxs-lookup"><span data-stu-id="13c58-119">We had three major components to our scene; **the UI, the map** , and **the weather** .</span></span> <span data-ttu-id="13c58-120">気象効果によって得られる GPU 時間がすべて必要になることが事前にわかっているので、UI や地形を意図的にオーバードローを減らすように設計しました。</span><span class="sxs-lookup"><span data-stu-id="13c58-120">We knew early on that our weather effects would require all the GPU time it could get, so we purposely designed the UI and terrain in a way that would reduce any overdraw.</span></span>

<span data-ttu-id="13c58-121">UI を何度か作り直すことで、生成されるオーバードローの量を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="13c58-121">We reworked the UI several times to minimize the amount of overdraw it would produce.</span></span> <span data-ttu-id="13c58-122">光るボタンやマップの概要などのコンポーネントに対して、透明なアートを互いの上にオーバーレイするのではなく、より複雑なジオメトリの側面に誤りしています。</span><span class="sxs-lookup"><span data-stu-id="13c58-122">We erred on the side of more complex geometry rather than overlaying transparent art on top of each other for components like glowing buttons and map overviews.</span></span>

<span data-ttu-id="13c58-123">このマップでは、シャドウや複雑な光源などの標準的な Unity 機能を除去するカスタムシェーダーを使用し、単純な単一の sun 照明モデルとカスタムのフォグ計算で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="13c58-123">For the map, we used a custom shader that would strip out standard Unity features such as shadows and complex lighting, replacing them with a simple single sun lighting model and a custom fog calculation.</span></span> <span data-ttu-id="13c58-124">これにより、単純なピクセルシェーダーが生成され、GPU サイクルが解放されます。</span><span class="sxs-lookup"><span data-stu-id="13c58-124">This produced a simple pixel shader and free up GPU cycles.</span></span>

<span data-ttu-id="13c58-125">UI とマップを、ハードウェアに応じて変更する必要がない予算でレンダリングするように管理されています。しかし、特にクラウドのレンダリングでは、気象の視覚化は課題の多くになることが実証されています。</span><span class="sxs-lookup"><span data-stu-id="13c58-125">We managed to get both the UI and the map to rendering at budget where we did not need any changes to them depending on the hardware; however, the weather visualization, in particular the cloud rendering, proved to be more of a challenge!</span></span>

## <a name="background-on-cloud-data"></a><span data-ttu-id="13c58-126">クラウドデータの背景</span><span class="sxs-lookup"><span data-stu-id="13c58-126">Background on cloud data</span></span>

<span data-ttu-id="13c58-127">私たちのクラウドデータは、NOAA サーバーからダウンロードされたもので https://nomads.ncep.noaa.gov/) 、3つの異なる2d レイヤー (それぞれがクラウドの最上位および下位の高さを備えています) と、グリッドの各セルのクラウドの密度です。</span><span class="sxs-lookup"><span data-stu-id="13c58-127">Our cloud data was downloaded from NOAA servers (https://nomads.ncep.noaa.gov/) and came to us in three distinct 2D layers, each with the top and bottom height of the cloud, as well as the density of the cloud for each cell of the grid.</span></span> <span data-ttu-id="13c58-128">データは、GPU に簡単にアクセスできるように、各コンポーネントがテクスチャの赤、緑、および青のコンポーネントに格納されているクラウド情報テクスチャに処理されました。</span><span class="sxs-lookup"><span data-stu-id="13c58-128">The data got processed into a cloud info texture where each component was stored in the red, green, and blue component of the texture for easy access on the GPU.</span></span>

## <a name="geometry-clouds"></a><span data-ttu-id="13c58-129">ジオメトリクラウド</span><span class="sxs-lookup"><span data-stu-id="13c58-129">Geometry clouds</span></span>

<span data-ttu-id="13c58-130">低電力のマシンがクラウドをレンダリングできるようにするために、ソリッドジオメトリを使用してオーバードローを最小化するアプローチから始めることを決定しました。</span><span class="sxs-lookup"><span data-stu-id="13c58-130">To make sure our lower-powered machines could render our clouds we decided to start with an approach that would use solid geometry to minimize overdraw.</span></span>

<span data-ttu-id="13c58-131">まず、図形を生成するために、頂点ごとにクラウド情報テクスチャの半径を使用して、レイヤーごとにソリッド高度マップメッシュを生成することで、クラウドの生成を試みました。</span><span class="sxs-lookup"><span data-stu-id="13c58-131">We first tried producing clouds by generating a solid heightmap mesh for each layer using the radius of the cloud info texture per vertex to generate the shape.</span></span> <span data-ttu-id="13c58-132">ここでは、ジオメトリシェーダーを使用して、ソリッドクラウドの形状を生成するクラウドの上部と下部の両方で頂点を生成しています。</span><span class="sxs-lookup"><span data-stu-id="13c58-132">We used a geometry shader to produce the vertices both at the top and the bottom of the cloud generating solid cloud shapes.</span></span> <span data-ttu-id="13c58-133">テクスチャの密度値を使用して、より密度の高いクラウドに対して暗い色でクラウドに色を付けています。</span><span class="sxs-lookup"><span data-stu-id="13c58-133">We used the density value from the texture to color the cloud with darker colors for more dense clouds.</span></span>

<span data-ttu-id="13c58-134">**頂点を作成するためのシェーダー:**</span><span class="sxs-lookup"><span data-stu-id="13c58-134">**Shader for creating the vertices:**</span></span>

```
v2g vert (appdata v)
{
    v2g o;
    o.height = tex2Dlod(_MainTex, float4(v.uv, 0, 0)).x;
    o.vertex = v.vertex;
    return o;
}
 
g2f GetOutput(v2g input, float heightDirection)
{
    g2f ret;
    float4 newBaseVert = input.vertex;
    newBaseVert.y += input.height * heightDirection * _HeigthScale;
    ret.vertex = UnityObjectToClipPos(newBaseVert);
    ret.height = input.height;
    return ret;
}
 
[maxvertexcount(6)]
void geo(triangle v2g p[3], inout TriangleStream<g2f> triStream)
{
    float heightTotal = p[0].height + p[1].height + p[2].height;
    if (heightTotal > 0)
    {
        triStream.Append(GetOutput(p[0], 1));
        triStream.Append(GetOutput(p[1], 1));
        triStream.Append(GetOutput(p[2], 1));
 
        triStream.RestartStrip();
 
        triStream.Append(GetOutput(p[2], -1));
        triStream.Append(GetOutput(p[1], -1));
        triStream.Append(GetOutput(p[0], -1));
    }
}
fixed4 frag (g2f i) : SV_Target
{
    clip(i.height - 0.1f);
 
    float3 finalColor = lerp(_LowColor, _HighColor, i.height);
    return float4(finalColor, 1);
}
```

<span data-ttu-id="13c58-135">実際のデータの上に詳細を表示するために、小さなノイズパターンを導入しました。</span><span class="sxs-lookup"><span data-stu-id="13c58-135">We introduced a small noise pattern to get more detail on top of the real data.</span></span> <span data-ttu-id="13c58-136">ラウンドクラウドのエッジを生成するために、補間半径の値がしきい値に達したときにピクセルシェーダーのピクセルをクリップし、ゼロの値を破棄します。</span><span class="sxs-lookup"><span data-stu-id="13c58-136">To produce round cloud edges, we clipped the pixels in the pixel shader when the interpolated radius value hit a threshold to discard near-zero values.</span></span>

![ジオメトリクラウド](images/datascape-geometry-clouds-700px.jpg)

<span data-ttu-id="13c58-138">雲はソリッドジオメトリなので、地形の前にレンダリングして、低コストのマップピクセルを非表示にして、フレームレートをさらに向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="13c58-138">Since the clouds are solid geometry, they can be rendered before the terrain to hide any expensive map pixels underneath to further improve framerate.</span></span> <span data-ttu-id="13c58-139">このソリューションは、完全なジオメトリレンダリングアプローチにより、最小仕様からハイエンドグラフィックスカード、または HoloLens で、すべてのグラフィックスカードで適切に実行されています。</span><span class="sxs-lookup"><span data-stu-id="13c58-139">This solution ran well on all graphics cards from min-spec to high-end graphics cards, as well as on HoloLens, because of the solid geometry rendering approach.</span></span>

## <a name="solid-particle-clouds"></a><span data-ttu-id="13c58-140">ソリッドパーティクルクラウド</span><span class="sxs-lookup"><span data-stu-id="13c58-140">Solid particle clouds</span></span>

<span data-ttu-id="13c58-141">これで、クラウドデータの適正な表現を生成したバックアップソリューションが完成しましたが、"wow" 要素には少し lackluster があったので、ハイエンドのコンピューターに必要な容量の感覚が伝達されていませんでした。</span><span class="sxs-lookup"><span data-stu-id="13c58-141">We now had a backup solution that produced a decent representation of our cloud data, but was a bit lackluster in the “wow” factor and did not convey the volumetric feel that we wanted for our high-end machines.</span></span>

<span data-ttu-id="13c58-142">次のステップでは、約10万のパーティクルを使ってクラウドを作成し、より自然で容量な外観を生成しました。</span><span class="sxs-lookup"><span data-stu-id="13c58-142">Our next step was creating the clouds by representing them with approximately 100,000 particles to produce a more organic and volumetric look.</span></span>

<span data-ttu-id="13c58-143">パーティクルが手前に表示され、前方に並べ替えられる場合でも、以前にレンダリングされたパーティクルの背後にあるピクセルの深度バッファーカリングを利用して、オーバードローを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="13c58-143">If particles stay solid and sort front-to-back, we can still benefit from depth buffer culling of the pixels behind previously rendered particles, reducing the overdraw.</span></span> <span data-ttu-id="13c58-144">また、パーティクルベースのソリューションを使用すると、さまざまなハードウェアをターゲットにするために使用されるパーティクルの量を変更できます。</span><span class="sxs-lookup"><span data-stu-id="13c58-144">Also, with a particle-based solution, we can alter the amount of particles used to target different hardware.</span></span> <span data-ttu-id="13c58-145">ただし、すべてのピクセルを詳細にテストする必要があるため、追加のオーバーヘッドが発生します。</span><span class="sxs-lookup"><span data-stu-id="13c58-145">However, all pixels still need to be depth tested, which results in some additional overhead.</span></span>

<span data-ttu-id="13c58-146">まず、起動時に、エクスペリエンスの中心点を中心にしたパーティクル位置を作成しました。</span><span class="sxs-lookup"><span data-stu-id="13c58-146">First, we created particle positions around the center point of the experience at startup.</span></span> <span data-ttu-id="13c58-147">これらのパーティクルは、距離を中心としてより高密度に分布しています。</span><span class="sxs-lookup"><span data-stu-id="13c58-147">We distributed the particles more densely around the center and less so in the distance.</span></span> <span data-ttu-id="13c58-148">最も近いパーティクルが先にレンダリングされるように、中心からすべてのパーティクルを事前に事前に並べ替えています。</span><span class="sxs-lookup"><span data-stu-id="13c58-148">We pre-sorted all particles from the center to the back so that the closest particles would render first.</span></span>

<span data-ttu-id="13c58-149">コンピューティングシェーダーでは、各パーティクルを正しい高さに配置し、密度に基づいて色を設定するために、クラウド情報テクスチャをサンプリングします。</span><span class="sxs-lookup"><span data-stu-id="13c58-149">A compute shader would sample the cloud info texture to position each particle at a correct height and color it based on the density.</span></span>

<span data-ttu-id="13c58-150">ここでは、 *Drawprocedural* を使用して、パーティクルごとにクワッドをレンダリングしています。これにより、パーティクルデータを常に GPU に維持できます。</span><span class="sxs-lookup"><span data-stu-id="13c58-150">We used *DrawProcedural* to render a quad per particle allowing the particle data to stay on the GPU at all times.</span></span>

<span data-ttu-id="13c58-151">各パーティクルには、高さと半径の両方が含まれていました。</span><span class="sxs-lookup"><span data-stu-id="13c58-151">Each particle contained both a height and a radius.</span></span> <span data-ttu-id="13c58-152">高さは、クラウド情報テクスチャからサンプリングされたクラウドデータに基づいています。半径は、最も近い近隣ノードへの水平方向の距離を格納するために計算される初期分布に基づいていました。</span><span class="sxs-lookup"><span data-stu-id="13c58-152">The height was based on the cloud data sampled from the cloud info texture, and the radius was based on the initial distribution where it would be calculated to store the horizontal distance to its closest neighbor.</span></span> <span data-ttu-id="13c58-153">これらの四角形は、このデータを使用して、ユーザーが水平方向に見たときに高さが表示され、ユーザーが上から見たときに、その近くにある領域をカバーします。</span><span class="sxs-lookup"><span data-stu-id="13c58-153">The quads would use this data to orient itself angled by the height so that when users look at it horizontally, the height would be shown, and when users looked at it top-down, the area between its neighbors would be covered.</span></span>

![パーティクル図形](images/particle-shape-700px.png)

<span data-ttu-id="13c58-155">**分布を示すシェーダーコード:**</span><span class="sxs-lookup"><span data-stu-id="13c58-155">**Shader code showing the distribution:**</span></span>

```
ComputeBuffer cloudPointBuffer = new ComputeBuffer(6, quadPointsStride);
cloudPointBuffer.SetData(new[]
{
    new Vector2(-.5f, .5f),
    new Vector2(.5f, .5f),
    new Vector2(.5f, -.5f),
    new Vector2(.5f, -.5f),
    new Vector2(-.5f, -.5f),
    new Vector2(-.5f, .5f)
});
 
StructuredBuffer<float2> quadPoints;
StructuredBuffer<float3> particlePositions;
v2f vert(uint id : SV_VertexID, uint inst : SV_InstanceID)
{
    // Find the center of the quad, from local to world space
    float4 centerPoint = mul(unity_ObjectToWorld, float4(particlePositions[inst], 1));
 
    // Calculate y offset for each quad point
    float3 cameraForward = normalize(centerPoint - _WorldSpaceCameraPos);
    float y = dot(quadPoints[id].xy, cameraForward.xz);
 
    // Read out the particle data
    float radius = ...;
    float height = ...;
 
    // Set the position of the vert
    float4 finalPos = centerPoint + float4(quadPoints[id].x, y * height, quadPoints[id].y, 0) * radius;
    o.pos = mul(UNITY_MATRIX_VP, float4(finalPos.xyz, 1));
    o.uv = quadPoints[id].xy + 0.5;
 
    return o;
}
```

<span data-ttu-id="13c58-156">ここでは、パーティクルを前方から順に並べ替えて、透明なピクセルをクリップ (blend ではない) の透明なピクセルでクリップします。この手法では、驚くほどのパーティクルが処理されるため、低電力のコンピューターであってもコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="13c58-156">Since we sort the particles front-to-back and we still used a solid style shader to clip (not blend) transparent pixels, this technique handles a surprising amount of particles, avoiding costly over-draw even on the lower-powered machines.</span></span>

## <a name="transparent-particle-clouds"></a><span data-ttu-id="13c58-157">透過的なパーティクルクラウド</span><span class="sxs-lookup"><span data-stu-id="13c58-157">Transparent particle clouds</span></span>

<span data-ttu-id="13c58-158">ソリッドなパーティクルは、雲の形に優れた有機感を与えましたが、クラウドの fluffiness を販売するために何かが必要でした。</span><span class="sxs-lookup"><span data-stu-id="13c58-158">The solid particles provided a good organic feel to the shape of the clouds but still needed something to sell the fluffiness of clouds.</span></span> <span data-ttu-id="13c58-159">ここでは、透明度を導入できるハイエンドグラフィックスカードのカスタムソリューションを試してみます。</span><span class="sxs-lookup"><span data-stu-id="13c58-159">We decided to try a custom solution for the high-end graphics cards where we can introduce transparency.</span></span>

<span data-ttu-id="13c58-160">これを行うには、単にパーティクルの初期並べ替え順序を切り替え、テクスチャアルファを使用するようにシェーダーを変更します。</span><span class="sxs-lookup"><span data-stu-id="13c58-160">To do this we simply switched the initial sorting order of the particles and changed the shader to use the textures alpha.</span></span>

![Fluffy クラウド](images/fluffy-clouds-700px.jpg)

<span data-ttu-id="13c58-162">これはすばらしいコンピューターであっても、画面に各ピクセルが何回もレンダリングされるようになったため、非常に多くの時間がかかりすぎることがわかっていました。</span><span class="sxs-lookup"><span data-stu-id="13c58-162">It looked great but proved to be too heavy for even the toughest machines since it would result in rendering each pixel on the screen hundreds of times!</span></span>

## <a name="render-off-screen-with-lower-resolution"></a><span data-ttu-id="13c58-163">解像度を低くして画面を表示しない</span><span class="sxs-lookup"><span data-stu-id="13c58-163">Render off-screen with lower resolution</span></span>

<span data-ttu-id="13c58-164">クラウドによってレンダリングされるピクセル数を減らすために、(画面と比較して) 四半期ごとの解像度のバッファーにレンダリングを開始し、すべてのパーティクルが描画された後に、最終的な結果を画面上に拡大します。</span><span class="sxs-lookup"><span data-stu-id="13c58-164">To reduce the number of pixels rendered by the clouds, we started rendering them in a quarter resolution buffer (compared to the screen) and stretching the end result back up onto the screen after all the particles had been drawn.</span></span> <span data-ttu-id="13c58-165">これにより、約4倍の高速化が得られましたが、いくつかの注意事項がありました。</span><span class="sxs-lookup"><span data-stu-id="13c58-165">This gave us roughly a 4x speedup, but came with a couple of caveats.</span></span>

<span data-ttu-id="13c58-166">**画面外に表示するコード:**</span><span class="sxs-lookup"><span data-stu-id="13c58-166">**Code for rendering off-screen:**</span></span>

```
cloudBlendingCommand = new CommandBuffer();
Camera.main.AddCommandBuffer(whenToComposite, cloudBlendingCommand);
 
cloudCamera.CopyFrom(Camera.main);
cloudCamera.rect = new Rect(0, 0, 1, 1);    //Adaptive rendering can set the main camera to a smaller rect
cloudCamera.clearFlags = CameraClearFlags.Color;
cloudCamera.backgroundColor = new Color(0, 0, 0, 1);
 
currentCloudTexture = RenderTexture.GetTemporary(Camera.main.pixelWidth / 2, Camera.main.pixelHeight / 2, 0);
cloudCamera.targetTexture = currentCloudTexture;
 
// Render clouds to the offscreen buffer
cloudCamera.Render();
cloudCamera.targetTexture = null;
 
// Blend low-res clouds to the main target
cloudBlendingCommand.Blit(currentCloudTexture, new RenderTargetIdentifier(BuiltinRenderTextureType.CurrentActive), blitMaterial);
```

<span data-ttu-id="13c58-167">まず、画面以外のバッファーにレンダリングすると、メインシーンからすべての深度情報が失われ、その結果、山の上に粒子が表示されます。</span><span class="sxs-lookup"><span data-stu-id="13c58-167">First, when rendering into an off-screen buffer, we lost all depth information from our main scene, resulting in particles behind mountains rendering on top of the mountain.</span></span>

<span data-ttu-id="13c58-168">2つ目の方法として、バッファーを拡張することで、解決の変化が明らかになったクラウドの端にも成果物が導入されました。</span><span class="sxs-lookup"><span data-stu-id="13c58-168">Second, stretching the buffer also introduced artifacts on the edges of our clouds where the resolution change was noticeable.</span></span> <span data-ttu-id="13c58-169">次の2つのセクションでは、これらの問題の解決方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="13c58-169">The next two sections talk about how we resolved these issues.</span></span>

## <a name="particle-depth-buffer"></a><span data-ttu-id="13c58-170">パーティクル深度バッファー</span><span class="sxs-lookup"><span data-stu-id="13c58-170">Particle depth buffer</span></span>

<span data-ttu-id="13c58-171">粒子をワールドジオメトリと共存させ、マウンテンまたはオブジェクトがその背後にあるパーティクルに対応できるようにするために、スクリーンバッファーにメインシーンのジオメトリを含む深度バッファーを設定しました。</span><span class="sxs-lookup"><span data-stu-id="13c58-171">To make the particles co-exist with the world geometry where a mountain or object could cover particles behind it, we populated the off-screen buffer with a depth buffer containing the geometry of the main scene.</span></span> <span data-ttu-id="13c58-172">このような深度バッファーを生成するために、2つ目のカメラを作成しました。これにより、シーンのソリッドジオメトリと深度のみがレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="13c58-172">To produce such depth buffer, we created a second camera, rendering only the solid geometry and depth of the scene.</span></span>

<span data-ttu-id="13c58-173">次に、クラウドのピクセルシェーダーの新しいテクスチャを occlude ピクセルに使用します。</span><span class="sxs-lookup"><span data-stu-id="13c58-173">We then used the new texture in the pixel shader of the clouds to occlude pixels.</span></span> <span data-ttu-id="13c58-174">同じテクスチャを使用して、クラウドピクセルの背後にあるジオメトリへの距離を計算しています。</span><span class="sxs-lookup"><span data-stu-id="13c58-174">We used the same texture to calculate the distance to the geometry behind a cloud pixel.</span></span> <span data-ttu-id="13c58-175">その距離を使用して、ピクセルのアルファに適用することで、雲の近くに近づいたときに、パーティクルや地形があるハードカットを取り除くことで、雲の効果が得られるようになりました。</span><span class="sxs-lookup"><span data-stu-id="13c58-175">By using that distance and applying it to the alpha of the pixel, we now had the effect of clouds fading out as they get close to terrain, removing any hard cuts where particles and terrain meet.</span></span>

![地形にブレンドされる雲](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a><span data-ttu-id="13c58-177">枠をシャープにする</span><span class="sxs-lookup"><span data-stu-id="13c58-177">Sharpening the edges</span></span>

<span data-ttu-id="13c58-178">拡張されたクラウドは、パーティクルの中心にある通常のサイズのクラウドとほぼ同じで、クラウドのエッジにいくつかのアーティファクトが示されていました。</span><span class="sxs-lookup"><span data-stu-id="13c58-178">The stretched-up clouds looked almost identical to the normal size clouds at the center of the particles or where they overlapped, but showed some artifacts at the cloud edges.</span></span> <span data-ttu-id="13c58-179">そうしないと、カメラの移動時にシャープの端がぼやけて表示されます。</span><span class="sxs-lookup"><span data-stu-id="13c58-179">Otherwise sharp edges would appear blurry and alias effects were introduced when the camera moved.</span></span>

<span data-ttu-id="13c58-180">これを解決するには、画面以外のバッファーで単純なシェーダーを実行して、大きな変化が発生した箇所を特定します (1)。</span><span class="sxs-lookup"><span data-stu-id="13c58-180">We solved this by running a simple shader on the off-screen buffer to determine where big changes in contrast occurred (1).</span></span> <span data-ttu-id="13c58-181">大きな変化を持つピクセルを新しいステンシルバッファー (2) に配置します。</span><span class="sxs-lookup"><span data-stu-id="13c58-181">We put the pixels with big changes into a new stencil buffer (2).</span></span> <span data-ttu-id="13c58-182">次に、スクリーンバッファーを画面に戻すときに、ステンシルバッファーを使用してこれらのハイコントラスト領域をマスクし、クラウドに穴を入れます (3)。</span><span class="sxs-lookup"><span data-stu-id="13c58-182">We then used the stencil buffer to mask out these high contrast areas when applying the off-screen buffer back to the screen, resulting in holes in and around the clouds (3).</span></span>

<span data-ttu-id="13c58-183">その後、すべてのパーティクルを全画面表示モードで再びレンダリングしましたが、今回はステンシルバッファーを使用してすべての辺をマスクしています。これにより、最小限のピクセルセット (4) が返されます。</span><span class="sxs-lookup"><span data-stu-id="13c58-183">We then rendered all the particles again in full-screen mode, but this time used the stencil buffer to mask out everything but the edges, resulting in a minimal set of pixels touched (4).</span></span> <span data-ttu-id="13c58-184">コマンドバッファーは既にパーティクル用に作成されているため、単に新しいカメラにレンダリングする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="13c58-184">Since the command buffer was already created for the particles, we simply had to render it again to the new camera.</span></span>

![レンダリングクラウドのエッジの進行状況](images/cloud-steps-1-4-700px.jpg)

<span data-ttu-id="13c58-186">最終的な結果は、クラウドの安価なセンターセクションで鋭いエッジでした。</span><span class="sxs-lookup"><span data-stu-id="13c58-186">The end result was sharp edges with cheap center sections of the clouds.</span></span>

<span data-ttu-id="13c58-187">すべてのパーティクルを全画面表示でレンダリングするよりもはるかに高速ですが、ステンシルバッファーに対するピクセルのテストにもコストがかかります。そのため、大量のオーバースペースには依然としてコストがかかります。</span><span class="sxs-lookup"><span data-stu-id="13c58-187">While this was much faster than rendering all particles in full screen, there is still a cost associated with testing a pixel against the stencil buffer, so a massive amount of overdraw still came with a cost.</span></span>

## <a name="culling-particles"></a><span data-ttu-id="13c58-188">パーティクルをカリングする</span><span class="sxs-lookup"><span data-stu-id="13c58-188">Culling particles</span></span>

<span data-ttu-id="13c58-189">この風の効果のために、コンピューティングシェーダーに長い三角形ストリップを生成して、世界中に多くの wisps を作成しました。</span><span class="sxs-lookup"><span data-stu-id="13c58-189">For our wind effect, we generated long triangle strips in a compute shader, creating many wisps of wind in the world.</span></span> <span data-ttu-id="13c58-190">Skinny ストリップが生成されたため、風の効果は塗りつぶしの速度に重いものではありませんが、数百から数千の頂点が生成され、頂点シェーダーの負荷が高くなります。</span><span class="sxs-lookup"><span data-stu-id="13c58-190">While the wind effect was not heavy on fill rate due to skinny strips generated, it produced many hundreds of thousands of vertices resulting in a heavy load for the vertex shader.</span></span>

<span data-ttu-id="13c58-191">ここでは、描画する風力ストリップのサブセットをフィードするために、コンピューティングシェーダーに追加バッファーを導入しました。</span><span class="sxs-lookup"><span data-stu-id="13c58-191">We introduced append buffers on the compute shader to feed a subset of the wind strips to be drawn.</span></span> <span data-ttu-id="13c58-192">コンピューティングシェーダー内の単純なビューでの視錐のあるロジックを使用すると、ストリップがカメラビューの外部にあり、そのストリップがプッシュバッファーに追加されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="13c58-192">With some simple view frustum culling logic in the compute shader, we could determine if a strip was outside of camera view and prevent it from being added to the push buffer.</span></span> <span data-ttu-id="13c58-193">これにより、ストリップの量が大幅に削減され、GPU で必要なサイクルが解放されます。</span><span class="sxs-lookup"><span data-stu-id="13c58-193">This reduced the amount of strips significantly, freeing up some needed cycles on the GPU.</span></span>

<span data-ttu-id="13c58-194">**追加バッファーを示すコード:**</span><span class="sxs-lookup"><span data-stu-id="13c58-194">**Code demonstrating an append buffer:**</span></span>

<span data-ttu-id="13c58-195">*計算シェーダー:*</span><span class="sxs-lookup"><span data-stu-id="13c58-195">*Compute shader:*</span></span>

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

<span data-ttu-id="13c58-196">*C# コード:*</span><span class="sxs-lookup"><span data-stu-id="13c58-196">*C# code:*</span></span>

```
protected void Awake() 
{
    // Create an append buffer, setting the maximum size and the contents stride length
    culledParticlesIdxBuffer = new ComputeBuffer(ParticleCount, sizeof(int), ComputeBufferType.Append);
 
    // Set up Args Buffer for Draw Procedural Indirect
    argsBuffer = new ComputeBuffer(4, sizeof(int), ComputeBufferType.IndirectArguments);
    argsBuffer.SetData(new int[] { DataVertCount, 0, 0, 0 });
}
 
protected void Update()
{
    // Reset the append buffer, and dispatch the compute shader normally
    culledParticlesIdxBuffer.SetCounterValue(0);
 
    computer.Dispatch(...)
 
    // Copy the append buffer count into the args buffer used by the Draw Procedural Indirect call
    ComputeBuffer.CopyCount(culledParticlesIdxBuffer, argsBuffer, dstOffset: 1);
    ribbonRenderCommand.DrawProceduralIndirect(Matrix4x4.identity, renderMaterial, 0, MeshTopology.Triangles, dataBuffer);
}
```

<span data-ttu-id="13c58-197">クラウドのパーティクルで同じ手法を使用しようとしました。ここでは、コンピューティングシェーダーでそれらをカリングし、レンダリングされる表示されるパーティクルだけをプッシュします。</span><span class="sxs-lookup"><span data-stu-id="13c58-197">We tried using the same technique on the cloud particles, where we would cull them on the compute shader and only push the visible particles to be rendered.</span></span> <span data-ttu-id="13c58-198">この手法では、最大のボトルネックが画面にレンダリングされる量ピクセルであり、頂点を計算するコストではないため、GPU ではあまり多くのことを行いませんでした。</span><span class="sxs-lookup"><span data-stu-id="13c58-198">This technique actually did not save us much on the GPU since the biggest bottleneck was the amount pixels rendered on the screen, and not the cost of calculating the vertices.</span></span>

<span data-ttu-id="13c58-199">この手法のもう1つの問題は、パーティクルの計算が並列化されているため、追加バッファーにランダムな順序で値が設定され、並べ替えられたパーティクルが並べ替えられないため、クラウドパーティクルがちらつくことでした。</span><span class="sxs-lookup"><span data-stu-id="13c58-199">The other problem with this technique was that the append buffer populated in random order due to its parallelized nature of computing the particles, causing the sorted particles to be un-sorted, resulting in flickering cloud particles.</span></span>

<span data-ttu-id="13c58-200">プッシュバッファーを並べ替える方法はありますが、カリングを使用した場合に得られるパフォーマンスの上限は、追加の並べ替えによって相殺される可能性があるため、この最適化を追求しないことにしました。</span><span class="sxs-lookup"><span data-stu-id="13c58-200">There are techniques to sort the push buffer, but the limited amount of performance gain we got out of culling particles would likely be offset with an additional sort, so we decided to not pursue this optimization.</span></span>

## <a name="adaptive-rendering"></a><span data-ttu-id="13c58-201">アダプティブレンダリング</span><span class="sxs-lookup"><span data-stu-id="13c58-201">Adaptive rendering</span></span>

<span data-ttu-id="13c58-202">曇りと明瞭なビューのようなさまざまなレンダリング条件でアプリのフレームレートを安定させるには、アプリにアダプティブレンダリングを導入しました。</span><span class="sxs-lookup"><span data-stu-id="13c58-202">To ensure a steady framerate on an app with varying rendering conditions like a cloudy vs a clear view, we introduced adaptive rendering to our app.</span></span>

<span data-ttu-id="13c58-203">アダプティブレンダリングの最初の手順は、GPU を測定することです。</span><span class="sxs-lookup"><span data-stu-id="13c58-203">The first step of adaptive rendering is to measure GPU.</span></span> <span data-ttu-id="13c58-204">これを行うには、レンダリングされたフレームの先頭および末尾にある GPU コマンドバッファーにカスタムコードを挿入し、左右両方の画面時間をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="13c58-204">We did this by inserting custom code into the GPU command buffer at the beginning and the end of a rendered frame, capturing both the left and right eye screen time.</span></span>

<span data-ttu-id="13c58-205">レンダリングに費やされた時間を測定し、目的のリフレッシュレートと比較することにより、フレームを破棄する方法がわかりました。</span><span class="sxs-lookup"><span data-stu-id="13c58-205">By measuring the time spent rendering and comparing it to our desired refresh-rate we got a sense of how close we were to dropping frames.</span></span>

<span data-ttu-id="13c58-206">フレームのドロップに近づいたときに、レンダリングをより速くするように調整します。</span><span class="sxs-lookup"><span data-stu-id="13c58-206">When close to dropping frames, we adapt our rendering to make it faster.</span></span> <span data-ttu-id="13c58-207">簡単に適応する方法の1つは、画面のビューポートのサイズを変更することです。これにより、レンダリングに必要なピクセル数が少なくなります。</span><span class="sxs-lookup"><span data-stu-id="13c58-207">One simple way of adapting is changing the viewport size of the screen, requiring less pixels to get rendered.</span></span>

<span data-ttu-id="13c58-208">*Unityengine. XR* を使用すると、対象のビューポートが縮小され、結果が画面に合わせて自動的に拡大されます。</span><span class="sxs-lookup"><span data-stu-id="13c58-208">By using *UnityEngine.XR.XRSettings.renderViewportScale* the system shrinks the targeted viewport and automatically stretches the result back up to fit the screen.</span></span> <span data-ttu-id="13c58-209">小数点以下桁数の小さな変化は、ワールドジオメトリではほとんどわかりません。また、0.7 のスケールファクターでは、レンダリングするピクセルの量が半分になります。</span><span class="sxs-lookup"><span data-stu-id="13c58-209">A small change in scale is barely noticeable on world geometry, and a scale factor of 0.7 requires half the amount of pixels to be rendered.</span></span>

![70% のスケール、ピクセルの半分](images/datascape-scaling-700px.jpg)

<span data-ttu-id="13c58-211">フレームを削除しようとしていることが検出された場合は、スケールを固定数だけ小さくし、実行している時間を十分に増やしてください。</span><span class="sxs-lookup"><span data-stu-id="13c58-211">When we detect that we are about to drop frames we lower the scale by a fixed number, and increase it back when we are running fast enough again.</span></span>

<span data-ttu-id="13c58-212">起動時にハードウェアのグラフィックス機能に基づいて使用するクラウド手法を決定しましたが、GPU 測定値のデータを基にして、システムの解像度が低くなることがないようにすることができます。ただし、これは Datascape での調査に時間がかかっていないことです。</span><span class="sxs-lookup"><span data-stu-id="13c58-212">While we decided what cloud technique to use based on graphics capabilities of the hardware at startup, it is possible to base it on data from the GPU measurement to prevent the system from staying at low resolution for a long time, but this is something we did not have time to explore in Datascape.</span></span>

## <a name="final-thoughts"></a><span data-ttu-id="13c58-213">最後に</span><span class="sxs-lookup"><span data-stu-id="13c58-213">Final thoughts</span></span>

<span data-ttu-id="13c58-214">さまざまなハードウェアをターゲットにすることは困難であり、いくつかの計画が必要です。</span><span class="sxs-lookup"><span data-stu-id="13c58-214">Targeting a variety of hardware is challenging and requires some planning.</span></span>

<span data-ttu-id="13c58-215">低電力のマシンを対象として、問題の領域を把握し、すべてのコンピューターで実行されるバックアップソリューションを開発することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="13c58-215">We recommend that you start targeting lower-powered machines to get familiar with the problem space and develop a backup solution that will run on all your machines.</span></span> <span data-ttu-id="13c58-216">ピクセルが最も貴重なリソースであるため、fill rate を念頭に置いてソリューションを設計します。</span><span class="sxs-lookup"><span data-stu-id="13c58-216">Design your solution with fill rate in mind, since pixels will be your most precious resource.</span></span> <span data-ttu-id="13c58-217">透明度のあるターゲットのソリッドジオメトリ。</span><span class="sxs-lookup"><span data-stu-id="13c58-217">Target solid geometry over transparency.</span></span>

<span data-ttu-id="13c58-218">バックアップソリューションを使用すると、ハイエンドのコンピューターの複雑さをさらに高めることができます。または、バックアップソリューションの解決を強化することもできます。</span><span class="sxs-lookup"><span data-stu-id="13c58-218">With a backup solution, you can then start layering in more complexity for high end machines or maybe just enhance resolution of your backup solution.</span></span>

<span data-ttu-id="13c58-219">最悪のシナリオに対応するように設計されており、多くの場合、アダプティブレンダリングの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="13c58-219">Design for worst case scenarios, and maybe consider using adaptive rendering for heavy situations.</span></span>

## <a name="about-the-authors"></a><span data-ttu-id="13c58-220">著者について</span><span class="sxs-lookup"><span data-stu-id="13c58-220">About the authors</span></span>

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="13c58-221"><b>Robert は、</b></span><span class="sxs-lookup"><span data-stu-id="13c58-221"><b>Robert Ferrese</b></span></span><br><span data-ttu-id="13c58-222">ソフトウェアエンジニア @Microsoft</span><span class="sxs-lookup"><span data-stu-id="13c58-222">Software engineer @Microsoft</span></span></td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><span data-ttu-id="13c58-223"><b>Dan Andersson</b></span><span class="sxs-lookup"><span data-stu-id="13c58-223"><b>Dan Andersson</b></span></span><br><span data-ttu-id="13c58-224">ソフトウェアエンジニア @Microsoft</span><span class="sxs-lookup"><span data-stu-id="13c58-224">Software engineer @Microsoft</span></span></td>
</tr>
</table>


## <a name="see-also"></a><span data-ttu-id="13c58-225">関連項目</span><span class="sxs-lookup"><span data-stu-id="13c58-225">See also</span></span>
* [<span data-ttu-id="13c58-226">Mixed Reality のパフォーマンスについて</span><span class="sxs-lookup"><span data-stu-id="13c58-226">Understanding Performance for Mixed Reality</span></span>](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [<span data-ttu-id="13c58-227">Unity のパフォーマンスに関する推奨事項</span><span class="sxs-lookup"><span data-stu-id="13c58-227">Performance Recommendations for Unity</span></span>](../develop/unity/performance-recommendations-for-unity.md)

 
