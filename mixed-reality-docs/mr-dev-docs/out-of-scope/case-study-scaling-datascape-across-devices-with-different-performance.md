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
# <a name="case-study---scaling-datascape-across-devices-with-different-performance"></a>ケーススタディ-パフォーマンスが異なるデバイス間での Datascape スケーリング

Datascape は、Microsoft 社内で開発された Windows Mixed Reality アプリケーションで、地形データの上に気象データを表示することに重点を置いています。 このアプリケーションでは、ユーザーを holographic データ可視化で囲むことによって、ユーザーが混合現実のデータを検出することによって得られる一意の洞察について説明します。

Datascape では、さまざまなハードウェア機能を備えたさまざまなプラットフォームを対象にしたいと考えています。これは、Microsoft HoloLens から Windows Mixed Reality のクロスヘッドヘッドセットや、低電力の Pc からハイエンド GPU を搭載した最新の Pc まで多岐にわたります。 主な課題は、高いフレームレートで実行しながら、グラフィックス機能が大幅に異なるデバイスで、視覚的に魅力のあるシーンをレンダリングすることでした。

このケーススタディでは、GPU 集中型のシステムのいくつかを作成するために使用されるプロセスと手法について説明し、発生した問題とその克服について説明します。

## <a name="transparency-and-overdraw"></a>透明度とオーバードロー

GPU では透明度が高くなる可能性があるため、メインレンダリング格闘は透明度で処理されます。

深度バッファーへの書き込み中に、ソリッドジオメトリを前面にレンダリングして、そのピクセルの背後にある今後のピクセルを破棄しないようにすることができます。 これにより、非表示のピクセルがピクセルシェーダーを実行できなくなり、プロセスが大幅に高速化されます。 Geometry が最適に並べ替えられている場合は、画面上の各ピクセルが1回だけ描画されます。

透明なジオメトリは最前面に並べ替える必要があり、ピクセルシェーダーの出力を画面上の現在のピクセルにブレンドすることに依存します。 これにより、画面上の各ピクセルがフレームごとに複数回描画される可能性があります。これは、オーバードローと呼ばれます。

HoloLens およびメインストリーム Pc の場合、画面はほんの数回しか入力できないため、透明なレンダリングの問題が発生します。

## <a name="introduction-to-datascape-scene-components"></a>Datascape コンポーネントの概要

シーンには3つの主要なコンポーネントがありました。 **UI、マップ** 、および **天気** 。 気象効果によって得られる GPU 時間がすべて必要になることが事前にわかっているので、UI や地形を意図的にオーバードローを減らすように設計しました。

UI を何度か作り直すことで、生成されるオーバードローの量を最小限に抑えることができます。 光るボタンやマップの概要などのコンポーネントに対して、透明なアートを互いの上にオーバーレイするのではなく、より複雑なジオメトリの側面に誤りしています。

このマップでは、シャドウや複雑な光源などの標準的な Unity 機能を除去するカスタムシェーダーを使用し、単純な単一の sun 照明モデルとカスタムのフォグ計算で置き換えます。 これにより、単純なピクセルシェーダーが生成され、GPU サイクルが解放されます。

UI とマップを、ハードウェアに応じて変更する必要がない予算でレンダリングするように管理されています。しかし、特にクラウドのレンダリングでは、気象の視覚化は課題の多くになることが実証されています。

## <a name="background-on-cloud-data"></a>クラウドデータの背景

私たちのクラウドデータは、NOAA サーバーからダウンロードされたもので https://nomads.ncep.noaa.gov/) 、3つの異なる2d レイヤー (それぞれがクラウドの最上位および下位の高さを備えています) と、グリッドの各セルのクラウドの密度です。 データは、GPU に簡単にアクセスできるように、各コンポーネントがテクスチャの赤、緑、および青のコンポーネントに格納されているクラウド情報テクスチャに処理されました。

## <a name="geometry-clouds"></a>ジオメトリクラウド

低電力のマシンがクラウドをレンダリングできるようにするために、ソリッドジオメトリを使用してオーバードローを最小化するアプローチから始めることを決定しました。

まず、図形を生成するために、頂点ごとにクラウド情報テクスチャの半径を使用して、レイヤーごとにソリッド高度マップメッシュを生成することで、クラウドの生成を試みました。 ここでは、ジオメトリシェーダーを使用して、ソリッドクラウドの形状を生成するクラウドの上部と下部の両方で頂点を生成しています。 テクスチャの密度値を使用して、より密度の高いクラウドに対して暗い色でクラウドに色を付けています。

**頂点を作成するためのシェーダー:**

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

実際のデータの上に詳細を表示するために、小さなノイズパターンを導入しました。 ラウンドクラウドのエッジを生成するために、補間半径の値がしきい値に達したときにピクセルシェーダーのピクセルをクリップし、ゼロの値を破棄します。

![ジオメトリクラウド](images/datascape-geometry-clouds-700px.jpg)

雲はソリッドジオメトリなので、地形の前にレンダリングして、低コストのマップピクセルを非表示にして、フレームレートをさらに向上させることができます。 このソリューションは、完全なジオメトリレンダリングアプローチにより、最小仕様からハイエンドグラフィックスカード、または HoloLens で、すべてのグラフィックスカードで適切に実行されています。

## <a name="solid-particle-clouds"></a>ソリッドパーティクルクラウド

これで、クラウドデータの適正な表現を生成したバックアップソリューションが完成しましたが、"wow" 要素には少し lackluster があったので、ハイエンドのコンピューターに必要な容量の感覚が伝達されていませんでした。

次のステップでは、約10万のパーティクルを使ってクラウドを作成し、より自然で容量な外観を生成しました。

パーティクルが手前に表示され、前方に並べ替えられる場合でも、以前にレンダリングされたパーティクルの背後にあるピクセルの深度バッファーカリングを利用して、オーバードローを減らすことができます。 また、パーティクルベースのソリューションを使用すると、さまざまなハードウェアをターゲットにするために使用されるパーティクルの量を変更できます。 ただし、すべてのピクセルを詳細にテストする必要があるため、追加のオーバーヘッドが発生します。

まず、起動時に、エクスペリエンスの中心点を中心にしたパーティクル位置を作成しました。 これらのパーティクルは、距離を中心としてより高密度に分布しています。 最も近いパーティクルが先にレンダリングされるように、中心からすべてのパーティクルを事前に事前に並べ替えています。

コンピューティングシェーダーでは、各パーティクルを正しい高さに配置し、密度に基づいて色を設定するために、クラウド情報テクスチャをサンプリングします。

ここでは、 *Drawprocedural* を使用して、パーティクルごとにクワッドをレンダリングしています。これにより、パーティクルデータを常に GPU に維持できます。

各パーティクルには、高さと半径の両方が含まれていました。 高さは、クラウド情報テクスチャからサンプリングされたクラウドデータに基づいています。半径は、最も近い近隣ノードへの水平方向の距離を格納するために計算される初期分布に基づいていました。 これらの四角形は、このデータを使用して、ユーザーが水平方向に見たときに高さが表示され、ユーザーが上から見たときに、その近くにある領域をカバーします。

![パーティクル図形](images/particle-shape-700px.png)

**分布を示すシェーダーコード:**

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

ここでは、パーティクルを前方から順に並べ替えて、透明なピクセルをクリップ (blend ではない) の透明なピクセルでクリップします。この手法では、驚くほどのパーティクルが処理されるため、低電力のコンピューターであってもコストがかかります。

## <a name="transparent-particle-clouds"></a>透過的なパーティクルクラウド

ソリッドなパーティクルは、雲の形に優れた有機感を与えましたが、クラウドの fluffiness を販売するために何かが必要でした。 ここでは、透明度を導入できるハイエンドグラフィックスカードのカスタムソリューションを試してみます。

これを行うには、単にパーティクルの初期並べ替え順序を切り替え、テクスチャアルファを使用するようにシェーダーを変更します。

![Fluffy クラウド](images/fluffy-clouds-700px.jpg)

これはすばらしいコンピューターであっても、画面に各ピクセルが何回もレンダリングされるようになったため、非常に多くの時間がかかりすぎることがわかっていました。

## <a name="render-off-screen-with-lower-resolution"></a>解像度を低くして画面を表示しない

クラウドによってレンダリングされるピクセル数を減らすために、(画面と比較して) 四半期ごとの解像度のバッファーにレンダリングを開始し、すべてのパーティクルが描画された後に、最終的な結果を画面上に拡大します。 これにより、約4倍の高速化が得られましたが、いくつかの注意事項がありました。

**画面外に表示するコード:**

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

まず、画面以外のバッファーにレンダリングすると、メインシーンからすべての深度情報が失われ、その結果、山の上に粒子が表示されます。

2つ目の方法として、バッファーを拡張することで、解決の変化が明らかになったクラウドの端にも成果物が導入されました。 次の2つのセクションでは、これらの問題の解決方法について説明します。

## <a name="particle-depth-buffer"></a>パーティクル深度バッファー

粒子をワールドジオメトリと共存させ、マウンテンまたはオブジェクトがその背後にあるパーティクルに対応できるようにするために、スクリーンバッファーにメインシーンのジオメトリを含む深度バッファーを設定しました。 このような深度バッファーを生成するために、2つ目のカメラを作成しました。これにより、シーンのソリッドジオメトリと深度のみがレンダリングされます。

次に、クラウドのピクセルシェーダーの新しいテクスチャを occlude ピクセルに使用します。 同じテクスチャを使用して、クラウドピクセルの背後にあるジオメトリへの距離を計算しています。 その距離を使用して、ピクセルのアルファに適用することで、雲の近くに近づいたときに、パーティクルや地形があるハードカットを取り除くことで、雲の効果が得られるようになりました。

![地形にブレンドされる雲](images/clouds-blended-to-terrain-700px.jpg)

## <a name="sharpening-the-edges"></a>枠をシャープにする

拡張されたクラウドは、パーティクルの中心にある通常のサイズのクラウドとほぼ同じで、クラウドのエッジにいくつかのアーティファクトが示されていました。 そうしないと、カメラの移動時にシャープの端がぼやけて表示されます。

これを解決するには、画面以外のバッファーで単純なシェーダーを実行して、大きな変化が発生した箇所を特定します (1)。 大きな変化を持つピクセルを新しいステンシルバッファー (2) に配置します。 次に、スクリーンバッファーを画面に戻すときに、ステンシルバッファーを使用してこれらのハイコントラスト領域をマスクし、クラウドに穴を入れます (3)。

その後、すべてのパーティクルを全画面表示モードで再びレンダリングしましたが、今回はステンシルバッファーを使用してすべての辺をマスクしています。これにより、最小限のピクセルセット (4) が返されます。 コマンドバッファーは既にパーティクル用に作成されているため、単に新しいカメラにレンダリングする必要がありました。

![レンダリングクラウドのエッジの進行状況](images/cloud-steps-1-4-700px.jpg)

最終的な結果は、クラウドの安価なセンターセクションで鋭いエッジでした。

すべてのパーティクルを全画面表示でレンダリングするよりもはるかに高速ですが、ステンシルバッファーに対するピクセルのテストにもコストがかかります。そのため、大量のオーバースペースには依然としてコストがかかります。

## <a name="culling-particles"></a>パーティクルをカリングする

この風の効果のために、コンピューティングシェーダーに長い三角形ストリップを生成して、世界中に多くの wisps を作成しました。 Skinny ストリップが生成されたため、風の効果は塗りつぶしの速度に重いものではありませんが、数百から数千の頂点が生成され、頂点シェーダーの負荷が高くなります。

ここでは、描画する風力ストリップのサブセットをフィードするために、コンピューティングシェーダーに追加バッファーを導入しました。 コンピューティングシェーダー内の単純なビューでの視錐のあるロジックを使用すると、ストリップがカメラビューの外部にあり、そのストリップがプッシュバッファーに追加されないようにすることができます。 これにより、ストリップの量が大幅に削減され、GPU で必要なサイクルが解放されます。

**追加バッファーを示すコード:**

*計算シェーダー:*

```
AppendStructuredBuffer<int> culledParticleIdx;
 
if (show)
    culledParticleIdx.Append(id.x);
```

*C# コード:*

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

クラウドのパーティクルで同じ手法を使用しようとしました。ここでは、コンピューティングシェーダーでそれらをカリングし、レンダリングされる表示されるパーティクルだけをプッシュします。 この手法では、最大のボトルネックが画面にレンダリングされる量ピクセルであり、頂点を計算するコストではないため、GPU ではあまり多くのことを行いませんでした。

この手法のもう1つの問題は、パーティクルの計算が並列化されているため、追加バッファーにランダムな順序で値が設定され、並べ替えられたパーティクルが並べ替えられないため、クラウドパーティクルがちらつくことでした。

プッシュバッファーを並べ替える方法はありますが、カリングを使用した場合に得られるパフォーマンスの上限は、追加の並べ替えによって相殺される可能性があるため、この最適化を追求しないことにしました。

## <a name="adaptive-rendering"></a>アダプティブレンダリング

曇りと明瞭なビューのようなさまざまなレンダリング条件でアプリのフレームレートを安定させるには、アプリにアダプティブレンダリングを導入しました。

アダプティブレンダリングの最初の手順は、GPU を測定することです。 これを行うには、レンダリングされたフレームの先頭および末尾にある GPU コマンドバッファーにカスタムコードを挿入し、左右両方の画面時間をキャプチャします。

レンダリングに費やされた時間を測定し、目的のリフレッシュレートと比較することにより、フレームを破棄する方法がわかりました。

フレームのドロップに近づいたときに、レンダリングをより速くするように調整します。 簡単に適応する方法の1つは、画面のビューポートのサイズを変更することです。これにより、レンダリングに必要なピクセル数が少なくなります。

*Unityengine. XR* を使用すると、対象のビューポートが縮小され、結果が画面に合わせて自動的に拡大されます。 小数点以下桁数の小さな変化は、ワールドジオメトリではほとんどわかりません。また、0.7 のスケールファクターでは、レンダリングするピクセルの量が半分になります。

![70% のスケール、ピクセルの半分](images/datascape-scaling-700px.jpg)

フレームを削除しようとしていることが検出された場合は、スケールを固定数だけ小さくし、実行している時間を十分に増やしてください。

起動時にハードウェアのグラフィックス機能に基づいて使用するクラウド手法を決定しましたが、GPU 測定値のデータを基にして、システムの解像度が低くなることがないようにすることができます。ただし、これは Datascape での調査に時間がかかっていないことです。

## <a name="final-thoughts"></a>最後に

さまざまなハードウェアをターゲットにすることは困難であり、いくつかの計画が必要です。

低電力のマシンを対象として、問題の領域を把握し、すべてのコンピューターで実行されるバックアップソリューションを開発することをお勧めします。 ピクセルが最も貴重なリソースであるため、fill rate を念頭に置いてソリューションを設計します。 透明度のあるターゲットのソリッドジオメトリ。

バックアップソリューションを使用すると、ハイエンドのコンピューターの複雑さをさらに高めることができます。または、バックアップソリューションの解決を強化することもできます。

最悪のシナリオに対応するように設計されており、多くの場合、アダプティブレンダリングの使用を検討してください。

## <a name="about-the-authors"></a>著者について

<table style="border:0">
<tr>
<td style="border:0" width="60px"><img alt="Picture of Robert Ferrese" width="60" height="60" src="images/robert-ferrese-60px.jpg"></td>
<td style="border:0"><b>Robert は、</b><br>ソフトウェアエンジニア @Microsoft</td>
</tr>
<tr>
<td style="border:0" width="60px"><img alt="Picture of Dan Andersson" width="60" height="60" src="images/dan-andersson-60px.jpg"></td>
<td style="border:0"><b>Dan Andersson</b><br>ソフトウェアエンジニア @Microsoft</td>
</tr>
</table>


## <a name="see-also"></a>関連項目
* [Mixed Reality のパフォーマンスについて](../develop/platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md)
* [Unity のパフォーマンスに関する推奨事項](../develop/unity/performance-recommendations-for-unity.md)

 
