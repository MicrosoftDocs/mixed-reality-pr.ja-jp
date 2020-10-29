---
title: OpenXR ベスト プラクティス
description: OpenXR アプリケーションのビジュアル品質、安定性、およびパフォーマンスに関するベストプラクティスについて説明します。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア、ベストプラクティス、パフォーマンス、品質、安定性
ms.openlocfilehash: dad4622e4186ecc8b090e2abe2e33d3d39ac7525
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91683882"
---
# <a name="openxr-app-best-practices"></a>OpenXR アプリのベストプラクティス

以下のベストプラクティスの例については、 <a href="https://github.com/microsoft/OpenXR-MixedReality/tree/master/samples/BasicXrApp" target="_blank">BasicXrApp</a>の OpenXRProgram ファイルを参照してください。 最初の Run () 関数は、初期化からイベントおよびレンダリングループへの一般的な OpenXR app コードフローをキャプチャします。

## <a name="best-practices-for-visual-quality-and-stability"></a>ビジュアルの品質と安定性に関するベストプラクティス

このセクションのベストプラクティスでは、OpenXR アプリケーションで最高の画質と安定性を実現する方法について説明します。

HoloLens 2 に固有のパフォーマンスの推奨事項については、後述の「 [hololens 2 のパフォーマンスに関するベストプラクティス](#best-practices-for-performance-on-hololens-2) 」を参照してください。

### <a name="gamma-correct-rendering"></a>ガンマ-正しいレンダリング

レンダリングパイプラインのガンマが正しいことを確認する必要があります。 スワップチェーンにレンダリングする場合、レンダーターゲットビュー形式は、スワップチェーン形式 ( `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` スワップチェーン形式とレンダーターゲットビューの両方など) と一致する必要があります。
例外は、アプリのレンダリングパイプラインがシェーダーコードで手動の srgb 変換を行う場合です。この場合、アプリは srgb スワップチェーン形式を要求する必要がありますが、レンダリングターゲットビューには線形形式を使用しますが、 `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` `DXGI_FORMAT_B8G8R8A8_UNORM` コンテンツが二重にガンマ補正されないようにするために、レンダーターゲットビューとして使用します。

### <a name="submit-depth-buffer-for-projection-layers"></a>プロジェクションレイヤーの深度バッファーを送信します

常に `XR_KHR_composition_layer_depth` 拡張機能を使用し、フレームをに送信するときに、その深度バッファーを投影レイヤーと一緒に送信し `xrEndFrame` ます。
これにより、HoloLens 2 でハードウェアの深さの再投影を有効にすることで、ホログラムの安定性が向上します。

### <a name="choose-a-reasonable-depth-range"></a>適切な深さの範囲を選択してください

HoloLens でのホログラムの安定性を向上させるために、より狭い深さの範囲を使用して仮想コンテンツの範囲を絞り込みます。
たとえば、OpenXrProgram サンプルでは、0.1 ~ 20 メートルが使用されています。
より一貫した深さの解決には、 [逆順-Z](https://developer.nvidia.com/content/depth-precision-visualized) を使用します。
HoloLens 2 では、推奨される深度形式を使用する `DXGI_FORMAT_D16_UNORM` と、フレームレートとパフォーマンスが向上しますが、16ビット深度バッファーでは、24ビット深度バッファーよりも深さの解像度が低くなることに注意してください。
そのため、これらのベストプラクティスに従って、その深さの解決を最大限に活用することが重要になります。

### <a name="prepare-for-different-environment-blend-modes"></a>さまざまな環境の blend モードを準備する

また、世界を完全にブロックしているイマーシブヘッドセットでアプリケーションを実行する場合は、API を使用してサポートされている環境の blend モードを列挙し、それに応じてレンダリングコンテンツを準備してください `xrEnumerateEnvironmentBlendModes` 。
たとえば、HoloLens などのシステムの場合、アプリでは `XR_ENVIRONMENT_BLEND_MODE_ADDITIVE` 透明色として透明を使用する必要があります。一方、を使用しているシステムの場合、 `XR_ENVIRONMENT_BLEND_MODE_OPAQUE` アプリは不透明色または一部の仮想ルームをバックグラウンドでレンダリングする必要があります。

### <a name="choose-unbounded-reference-space-as-applications-root-space"></a>アプリケーションのルート領域として非バインド参照スペースを選択する

通常、アプリケーションは、ビュー、アクション、およびホログラムを連結するために、いくつかのルートワールド座標空間を確立します。
`XR_REFERENCE_SPACE_TYPE_UNBOUNDED_MSFT`拡張機能がサポートされている場合は、を使用して、[ワールドスケールの座標](../../design/coordinate-systems.md#building-a-world-scale-experience)系を確立します。これにより、アプリの開始位置からユーザーが遠く (たとえば、5メートル離れた場所で) 移動したときに望ましくないホログラムのずれを防ぐことができます。
非 `XR_REFERENCE_SPACE_TYPE_LOCAL` バインド領域の拡張機能が存在しない場合は、フォールバックとして使用します。

### <a name="associate-hologram-with-spatial-anchor"></a>ホログラムを空間アンカーに関連付ける

バインドされていない参照空間を使用する場合、その参照空間に直接配置したホログラムは、遠くの部屋に移動した後に戻ったときに、 [ずれを生じる可能性があり](../../design/coordinate-systems.md#building-a-world-scale-experience)ます。
ホログラムユーザーが世界中の個別の場所に配置されるようにするには、拡張機能を使用して [空間アンカーを作成](../../design/spatial-anchors.md#best-practices) `xrCreateSpatialAnchorSpaceMSFT` し、その原点にホログラムを配置します。
これにより、そのホログラムは時間の経過と共に個別に安定した状態に保たれます

### <a name="support-mixed-reality-capture"></a>混合現実のキャプチャをサポートする

HoloLens 2 のプライマリディスプレイは加法の環境ブレンドを使用しますが、ユーザーが [mixed reality キャプチャ](../platform-capabilities-and-apis/mixed-reality-capture-for-developers.md)を開始すると、アプリのレンダリングコンテンツは環境のビデオストリームとアルファブレンドされます。
混合現実のキャプチャビデオで最高の画質を実現するには、投影レイヤーのを設定することをお勧めし `XR_COMPOSITION_LAYER_BLEND_TEXTURE_SOURCE_ALPHA_BIT` `layerFlags` ます。

## <a name="best-practices-for-performance-on-hololens-2"></a>HoloLens 2 でのパフォーマンスに関するベストプラクティス

ハードウェアの再プロジェクションをサポートするモバイルデバイスとして、HoloLens 2 には最適なパフォーマンスを得るための厳しい要件があります。  合成データを送信するには、さまざまな方法があります。これにより、 `xrEndFrame` パフォーマンスが大幅に低下する後処理が発生します。

### <a name="select-a-swapchain-format"></a>スワップチェーン形式を選択してください

常にを使用して、サポートされているピクセル形式を列挙 `xrEnumerateSwapchainFormats` し、アプリがサポートするランタイムから最初の色と深度のピクセル形式を選択します。これは、ランタイムが最適なパフォーマンスのために優先するものであるためです。 HoloLens 2 で `DXGI_FORMAT_B8G8R8A8_UNORM_SRGB` `DXGI_FORMAT_D16_UNORM` は、通常、レンダリングのパフォーマンスを向上させるための最初の選択肢です。 この設定は、デスクトップ PC で実行されている VR ヘッドセットでは異なっていてもかまいません。24ビットの深度バッファーでは、パフォーマンスへの影響が少なくなります。
  
**パフォーマンスの警告:** プライマリスワップチェーンカラー形式以外の形式を使用すると、パフォーマンスが大幅に低下するランタイム後処理が発生します。

### <a name="render-with-recommended-rendering-parameters-and-frame-timing"></a>推奨されるレンダリングパラメーターとフレームタイミングを使用したレンダリング

常に推奨されるビュー構成の幅/高さ (から) を使用してレンダリングし、表示する前に、常に API を使用して推奨されるビューの破棄 `recommendedImageRectWidth` `recommendedImageRectHeight` `XrViewConfigurationView` `xrLocateViews` 、視界、およびその他のレンダリングパラメーターを照会します。
`XrFrameEndInfo.predictedDisplayTime`ポーズとビューに対してクエリを実行するときは、常に最新の呼び出しからを使用し `xrWaitFrame` ます。
これにより、HoloLens は、HoloLens を装着しているユーザーに対してレンダリングを調整し、視覚品質を最適化することができます。

### <a name="use-a-single-projection-layer"></a>1つの投影レイヤーを使用する

HoloLens 2 では、アプリケーションがコンテンツをレンダリングするための GPU 機能が制限されており、単一の投影レイヤー用に最適化されたハードウェアコンポジターが使用されています。
常に1つの投影レイヤーを使用すると、アプリケーションのフレームレート、ホログラムの安定性、およびビジュアルの品質を向上させることができます。  
  
**パフォーマンスの警告:** 1つの保護レイヤーだけを送信すると、パフォーマンスが大幅に低下するランタイム後処理が発生します。

### <a name="render-with-texture-array-and-vprt"></a>テクスチャ配列と VPRT を使用したレンダリング

`xrSwapchain`カラースワップチェーンにはを使用して、左と右の両方に対して1つ作成し `arraySize=2` ます。
スライス0に左側を表示し、スライス1に目を入れます。
VPRT のシェーダーとインスタンス化された描画呼び出しのステレオスコピックレンダリングを使用して、GPU の負荷を最小限に抑えます。
これにより、ランタイムの最適化によって HoloLens 2 で最高のパフォーマンスを実現できます。
2つのテクスチャ配列を使用する代わりに、2倍のレンダリングや個別のスワップチェーンなどを使用する代わりに、パフォーマンスが大幅に低下するランタイム後処理が発生します。

### <a name="avoid-quad-layers"></a>クワッドレイヤーを避ける

では、クワッドレイヤーを合成レイヤーとして送信するのではなく `XrCompositionLayerQuad` 、四角形のコンテンツを射影 swapchain に直接レンダリングします。

**パフォーマンスの警告:** クワッドレイヤーなど、1つの投影レイヤーを超えて追加のレイヤーを提供すると、パフォーマンスが大幅に低下するランタイム後処理が発生します。