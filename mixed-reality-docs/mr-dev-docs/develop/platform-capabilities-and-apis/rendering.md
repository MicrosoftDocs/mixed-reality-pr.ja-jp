---
title: レンダリング
description: Holographic のレンダリングを使用すると、アプリは、物理的な世界に配置されている場合でも、作成した仮想領域内にある場合でも、ユーザーを周囲に世界中の正確な場所に置くことができます。
author: thetuvix
ms.author: alexturn
ms.date: 02/24/2019
ms.topic: article
keywords: レンダリング、ホログラム
ms.openlocfilehash: 3bc882df8ec43fc188bae521a95ff91e5a59573c
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684986"
---
# <a name="rendering"></a>レンダリング

Holographic のレンダリングを使用すると、アプリケーションは、物理的に物理的に配置されている場合でも、作成した仮想領域内にある場合でも、ユーザーを中心に世界中の正確な場所にホログラムを描画できます。 [ホログラム](../../discover/hologram.md) は、サウンドとライトで構成されるオブジェクトです。 レンダリングを使用すると、アプリケーションでライトを追加できます。

## <a name="device-support"></a>デバイス サポート

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>機能</strong></td>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>レンダリング</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
</table>

## <a name="holographic-rendering"></a>ホログラフィック レンダリング

Holographic レンダリングは、ユーザーが物理的な世界とホログラムの両方を表示できるようにするための HoloLens のような表示を表示するか、または世界をブロックする Windows Mixed Reality のイマーシブヘッドセットのような不透明なディスプレイを表示するかを認識します。

**「** [HoloLens](../../hololens-hardware-details.md)」などの表示を使用するデバイスでは、世界に光を追加します。 黒いピクセルは完全に透明ですが、より明るいピクセルは徐々に不透明になります。 ディスプレイのライトは現実世界の光に追加されるため、白ピクセルは半透明になっています。

ステレオスコピックのレンダリングでは、ホログラムに対して1つの深さの手掛かりが提供されますが、 [接地効果](../../design/interaction-fundamentals.md) を追加すると、ホログラムの近くにある表面をより簡単に表示できます。 1つの接地方法として、近くの表面にホログラムの周りに光彩を追加し、この光彩に対して影を描画します。 このようにして、影は環境から光を引くように見えます。 [空間サウンド](../../design/spatial-sound.md) は、ユーザーがホログラムの距離と相対位置を理解できるようにするための、非常に重要なもう1つの深さの手掛かりです。

[Windows Mixed Reality イマーシブヘッドセット](../../discover/immersive-headset-hardware-details.md)など、 **不透明なディスプレイ** を持つデバイスは、世界をブロックします。 黒のピクセルは黒で塗りつぶされ、その他の色はユーザーにその色として表示されます。 アプリケーションは、ユーザーに表示されるすべてのものを表示する役割を担います。 これにより、ユーザーに快適なエクスペリエンスを提供するために、一定のリフレッシュレートを維持することがさらに重要になります。

## <a name="predicted-rendering-parameters"></a>予測される表示パラメーター

Mixed reality ヘッドセット (HoloLens とイマーシブヘッドセットの両方) は、ユーザーの周囲に対する相対的な位置と向きを継続的に追跡します。 アプリケーションで次のフレームの準備が開始されると、フレームがディスプレイに表示される瞬間に、ユーザーのヘッドが今後どのようになるかが予測されます。 この予測に基づいて、システムは、そのフレームに使用するビューと射影変換を計算します。 アプリケーションで **正しい結果を得るには、これらの変換を使用する必要があり** ます。システム指定の変換が使用されていない場合、結果として得られるイメージは実際の世界に配置されず、ユーザー不快感が発生します。

新しいフレームがディスプレイに到着するタイミングを正確に予測するために、システムは、アプリケーションのレンダリングパイプラインの有効なエンドツーエンドの待機時間を絶えず測定します。 システムはレンダリングパイプラインの長さに合わせて調整されますが、そのパイプラインをできるだけ短くすることで、ホログラムの安定性を向上させることができます。

システム予測を強化する高度な手法を使用するアプリケーションでは、システムビューと射影変換をオーバーライドできます。 これらのアプリケーションは、意味のある結果を生成するために、カスタム変換の基礎としてシステム提供の変換を使用する必要があります。

## <a name="other-rendering-parameters"></a>その他の表示パラメーター

フレームをレンダリングする場合、システムは、アプリケーションが描画する必要があるバックバッファービューポートを指定します。 このビューポートは、多くの場合、フレームバッファーの最大サイズよりも小さくなります。 ビューポートのサイズに関係なく、アプリケーションによってフレームがレンダリングされると、システムによってイメージが拡張され、ディスプレイ全体がいっぱいになります。

必要なリフレッシュレートでレンダリングできないアプリケーションの場合、 [システムレンダリングパラメーターを構成して](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration) 、メモリ負荷とレンダリングコストを削減できます。これは、ピクセルの別名が高くなります。 バックバッファー形式を変更することもできます。この場合、一部のアプリでは、メモリ帯域幅とピクセルスループットの向上に役立ちます。

アプリがレンダリングするように求められている表示の視錐、解像度、フレームレートは、フレームごとに変化する可能性があり、左右に異なる場合があります。 たとえば、 [mixed reality キャプチャ](../../mixed-reality-capture.md) (MRC) がアクティブで、 [フォト/ビデオカメラビューの構成](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind) がオプトインされていない場合、1つ目の目がより大きな視界や解像度でレンダリングされる可能性があります。

特定のフレームに対して、アプリケーションは、システムによって提供されるビュー変換、プロジェクション変換、およびビューポートの解決を使用してレンダリング *する必要があり* ます。 また、アプリケーションでは、レンダリングまたは表示パラメーターがフレーム間で固定されたままであると想定することはできません。 Unity のようなエンジンは、これらすべての変換を独自のカメラオブジェクトで処理するので、ユーザーの物理的な動きとシステムの状態が常に尊重されます。 アプリケーションで世界中のユーザーの仮想移動が許可されている場合 (ゲームパッドでのサムスティックの使用など)、そのオブジェクトを移動する、カメラの上に親のリモート処理オブジェクトを追加できます。 これにより、カメラにユーザーの仮想と物理の両方の動きが反映されます。 アプリケーションで、システムによって提供されるビュー変換、プロジェクション変換、またはビューポートの各ディメンションを変更する場合は、適切な [OVERRIDE API](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicCameraPose#Windows_Graphics_Holographic_HolographicCameraPose)を呼び出すことによってシステムに通知する必要があります。

Holographic レンダリングの安定性を向上させるには、アプリで、レンダリングに使用した深度バッファーを各フレームに Windows に提供する必要があります。 アプリが深度バッファーを提供している場合は、カメラからの深さをメートル単位で表した、一貫した深さの値を持つ必要があります。 これにより、ユーザーのヘッドが予測された位置から少しずれている場合に、システムがピクセルごとの深度データを使用して、コンテンツの安定化を向上させることができます。 深度バッファーを提供できない場合は、フォーカスポイントと法線を提供して、コンテンツの大部分を切削する平面を定義することができます。 深度バッファーとフォーカスプレーンの両方が指定されている場合、システムは両方を使用する可能性があります。 特に、アプリケーションで動きがあるホログラムを表示する場合は、深度バッファーと、速度ベクトルを含むフォーカスポイントの両方を提供すると便利です。

トピックの下位レベルの詳細については、 [DirectX でのレンダリング](../native/rendering-in-directx.md) に関する記事をご覧ください。

## <a name="holographic-cameras"></a>Holographic カメラ

Windows Mixed Reality では、 **holographic カメラ** の概念が導入されています。 Holographic カメラは、3D グラフィックステキストにある従来のカメラに似ています。外部 (位置と向き) と固有のカメラプロパティの両方を定義します。 (例: ビューのフィールドは、仮想3D シーンを表示するために使用されます)。従来の3D カメラとは異なり、アプリケーションはカメラの位置、向き、および組み込みプロパティを制御していません。 代わりに、holographic カメラの位置と向きは、ユーザーの移動によって暗黙的に制御されます。 ユーザーの移動は、ビュー変換を使用してフレーム単位でアプリケーションにリレーされます。 同様に、カメラの組み込みプロパティはデバイスの調整された光によって定義され、射影変換を介してフレーム単位でリレーされます。

一般に、1つのステレオカメラ用にアプリケーションがレンダリングされます。 ただし、堅牢なレンダリングループでは、複数のカメラがサポートされ、mono カメラとステレオカメラの両方がサポートされます。 たとえば、問題のヘッドセットの形状に応じて、ユーザーが [mixed reality capture](../../mixed-reality-capture.md) (MRC) などの機能をアクティブ化した場合に、別の観点からアプリケーションを表示するように要求することがあります。 複数のカメラをサポートするアプリケーションでは、サポートできるカメラの[種類](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfigurationKind#Windows_Graphics_Holographic_HolographicViewConfigurationKind)を[オプトイン](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)することによって、それらを取得できます。

## <a name="volume-rendering"></a>ボリューム レンダリング

3D で医療 Mri やエンジニアリングボリュームをレンダリングする場合、多くの場合、 [ボリュームレンダリング](volume-rendering.md) 手法が使用されます。 これらの手法は、特に、ユーザーが頭を移動するだけで、キーの角度からそのようなボリュームを自然に表示できる mixed reality で特に興味深いものです。

## <a name="supported-resolutions-on-hololens-1st-gen"></a>HoloLens でサポートされている解像度 (第1世代)

* ビューポートの最大サイズは、 [HolographicDisplay](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographicdisplay)のプロパティです。 HoloLens は、既定では、ビューポートの最大サイズ (720p (1268x720)) に設定されています。
* ビューポートのサイズは、HolographicCamera で ViewportScaleFactor を設定することによって変更できます。 このスケール係数は 0 ~ 1 の範囲内です。
* HoloLens (第1世代) でサポートされる最も低いビューポートのサイズは、720p の50% です。これは 360p (634x360) です。 これは0.5 の ViewportScaleFactor です。
* 視覚の劣化によって540p より低いものは推奨されませんが、ピクセルフィルレートのボトルネックを特定するために使用できます。

## <a name="supported-resolutions-on-hololens-2"></a>HoloLens 2 でサポートされている解像度

* サポートされているレンダーターゲットの最大サイズは、 [ビュー構成](https://docs.microsoft.com/uwp/api/Windows.Graphics.Holographic.HolographicViewConfiguration#Windows_Graphics_Holographic_HolographicViewConfiguration)のプロパティです。 HoloLens 2 は、既定では1440x936 という最大レンダーターゲットサイズに設定されています。
* アプリでは、RequestRenderTargetSize メソッドを呼び出して新しいレンダーターゲットサイズを要求することによって、レンダーターゲットバッファーのサイズを変更できます。 新しいレンダーターゲットサイズが選択されます。これは、要求されたレンダーターゲットサイズ以上になります。 この API はレンダーターゲットバッファーのサイズを変更します。これにより、GPU でのメモリの再割り当てが必要になります。 この場合の影響: レンダーターゲットのサイズをスケールダウンして GPU のメモリ不足を減らすことができます。また、このメソッドを高頻度で呼び出すことはできません。
* アプリでは、HoloLens 1 と同じ方法でビューポートのサイズを変更することもできます。 これにより、GPU でのメモリの再割り当ては発生しません。そのため、高い頻度で変更できますが、GPU のメモリ負荷を軽減するために使用することはできません。
* HoloLens 2 でサポートされている最も低いビューポートのサイズは634x412 です。 これは、既定のレンダーターゲットサイズが使用されている場合、約0.44 の ViewportScaleFactor になります。
* サポートされている最も低いビューポートのサイズよりも少ないレンダーターゲットサイズが指定されている場合、ビューポートのスケールファクターは無視されます。
* 視覚の劣化によって540p より低いものは推奨されませんが、ピクセルフィルレートのボトルネックを特定するために使用できます。



## <a name="see-also"></a>関連項目
* [ホログラムの安定性](hologram-stability.md)
* [DirectX でのレンダリング](../native/rendering-in-directx.md)
