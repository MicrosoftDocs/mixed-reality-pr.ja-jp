---
title: アプリの品質基準
description: このドキュメントでは、mixed reality アプリの品質に影響する上位の要因について説明します。
author: cjdgit
ms.author: crderr
ms.date: 03/21/2018
ms.topic: article
keywords: アプリ品質基準、mixed reality、mixed reality アプリ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
ms.openlocfilehash: 788a2e8ac1a364f8c33e3895992fd99fa220a26a
ms.sourcegitcommit: c41372e0c6ca265f599bff309390982642d628b8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97530289"
---
# <a name="app-quality-criteria"></a>アプリの品質基準

このドキュメントでは、mixed reality アプリの品質に影響する上位の要因について説明します。 各要素について、次の情報が提供されます。
* [概要] –品質要因と重要な理由について簡単に説明します。
* デバイスへの影響-どの種類のウィンドウに Mixed Reality デバイスが影響を受けます。
* 品質基準–品質要因を評価する方法。
* 方法: 問題を測定 (または経験) する方法。
* 推奨事項–より優れたユーザーエクスペリエンスを提供するためのアプローチの概要です。
* リソース–優れたアプリエクスペリエンスを作成するのに役立つ、関連する開発者および設計リソース。

## <a name="frame-rate"></a>フレーム レート

フレームレートは、ホログラムの安定性とユーザーの快適さの第一柱です。 推奨されるターゲットの下にあるフレームレートは、ホログラムがちらつくように見え、エクスペリエンスの believability に悪影響を及ぼし、目に見える疲労が発生する可能性があります。 Windows Mixed Reality のイマーシブヘッドセットでのエクスペリエンスの目標フレームレートは、サポートしている Windows Mixed Reality 互換 Pc に応じて、60 Hz または 90 Hz です。 HoloLens の場合、ターゲットフレームレートは 60 Hz です。

### <a name="device-impact"></a>デバイスへの影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  あっ |  失敗 |
--- | --- | ---
| アプリは、ターゲットデバイスの1秒あたりのフレーム数 (FPS) の目標を一貫して満たしています: HoloLens で 60 fps。ウルトラ Pc で 90 fps。メインストリーム Pc では 60 fps です。 | アプリは、コアエクスペリエンスを妨げるすることなく断続的にフレームが削除されるか、または FPS は望ましい目標よりも一貫して低くなりますが、アプリのエクスペリエンスを妨げることはありません。 | アプリでは、平均で10秒以内にフレームレートが低下しています。 |

### <a name="how-to-measure"></a>測定する方法

* リアルタイムのフレームレートグラフは、 [Windows デバイスポータル](using-the-windows-device-portal.md#system-performance) によって "システムパフォーマンス" によって提供されます。
* 開発用デバッグでは、フレームレート診断カウンターをアプリに追加します。 「サンプルカウンターのリソース」を参照してください。
* フレームレートが低下するのは、アプリの実行中に、ヘッドを左右に移動して、デバイスで発生する可能性があります。 ホログラムが予期しないちらつきの動きを示している場合、フレームレートが低いか、安定性平面が原因である可能性があります。

### <a name="recommendations"></a>推奨事項

* 開発作業の開始時にフレームレートカウンターを追加します。
* フレームレートが低下した変更は、パフォーマンスバグとして評価され、適切に解決される必要があります。

### <a name="resources"></a>リソース

#### <a name="documentation"></a>ドキュメント

* [Mixed Reality のパフォーマンスについて](understanding-performance-for-mixed-reality.md)
* [ホログラムの安定性とフレームレート](hologram-stability.md#frame-rate)
* [資産のパフォーマンスの予算](../../design/asset-creation-process.md)
* [Unity のパフォーマンスに関する推奨事項](../unity/performance-recommendations-for-unity.md)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [混合 Reality ツールキット、FPS カウンターの表示](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Utilities/README.md)
* [混合現実ツールキット、シェーダー](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/Utilities/Shaders)

#### <a name="external-references"></a>外部参照

* [Unity, モバイルアプリケーションの最適化](https://www.youtube.com/watch?v=j4YAY36xjwE)

## <a name="hologram-stability"></a>ホログラムの安定性

安定したホログラムは、アプリの使いやすさと believability を向上させ、ユーザーにより快適な表示エクスペリエンスを作成します。 ホログラムの安定性の質は、優れたアプリ開発と、その環境を理解 (追跡) するデバイスの機能によって得られます。 フレームレートは安定性の最初の柱ですが、その他の要因は次のような安定性に影響を与える可能性があります。

* 安定化平面の使用
* 空間アンカーへの距離
* 追跡

### <a name="device-impact"></a>デバイスへの影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  あっ |  失敗 |
--- | --- | ---
|  ホログラムは常に安定した状態で表示されます。 | セカンダリコンテンツは予期しない移動を示しています。または、予期しない移動はアプリ全体のエクスペリエンスを妨げることはありません。 | フレーム内のプライマリコンテンツは、予期しない移動を示しています。 |

### <a name="how-to-measure"></a>測定する方法

デバイスを装着し、エクスペリエンスを表示しています。

* ヘッドを左右に移動します。 ホログラムが予期しない動きを示している場合、フレームレートが低いか、または安定平面が焦点平面に正しく配置されていない可能性があります。
* ホログラムと環境内を移動し、スイム・ jumpiness などの動作を探します。 この種類のモーションは、デバイスが環境を追跡していない、または空間アンカーへの距離が原因である可能性があります。
* フレーム内に複数のホログラムがある場合は、さまざまな深度でのホログラムの動作を観察し、揺れるが表示されている場合は、安定化平面によって発生する可能性があります。

### <a name="recommendations"></a>推奨事項

* 開発作業の開始時にフレームレートカウンターを追加します。
* 安定化平面を使用します。
* アンカーの3メートル以内に固定したホログラムを常にレンダリングします。
* 適切な追跡のために環境がセットアップされていることを確認します。
* フレーム内のさまざまな焦点深度レベルでホログラムを使用しないように、エクスペリエンスを設計します。

### <a name="resources"></a>リソース

#### <a name="documentation"></a>ドキュメント

* [ホログラムの安定性とフレームレート](hologram-stability.md#frame-rate)
* [安定化平面を使用したケーススタディ](case-study-using-the-stabilization-plane-to-reduce-holographic-turbulence.md)
* [Mixed Reality のパフォーマンスについて](understanding-performance-for-mixed-reality.md)
* [Unity のパフォーマンスに関する推奨事項](../unity/performance-recommendations-for-unity.md)
* [空間アンカー](../../design/spatial-anchors.md)
* [追跡エラーの処理](../../design/coordinate-systems.md#handling-tracking-errors)
* [静止フレーム (参照)](../../design/coordinate-systems.md#stationary-frame-of-reference)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [MR コンパニオンキット、Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

## <a name="holograms-position-on-real-surfaces"></a>実際のサーフェイス上のホログラムの位置

物理的なオブジェクトを使用したホログラムの間違った配置 (相互に関係するように設計されている場合) は、ホログラムと現実世界の非共用体を明確に示しています。 配置の精度は、シナリオのニーズに対して相対的である必要があります。たとえば、一般的な表面配置では空間マップを使用できますが、正確に配置するには、マーカーと調整を使用する必要があります。

### <a name="device-impact"></a>デバイスへの影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  あっ |  失敗 |
--- | --- | ---
| ホログラムは、通常、センチメートル ~ インチの範囲内のサーフェイスに配置されます。 より正確な精度が必要な場合は、アプリの仕様内でコラボレーションのための効率的な手段を提供する必要があります。 | N/A | サーフェイスを分割するか、表面から離れた場所に表示することによって、ホログラムが物理的なターゲットオブジェクトと共に配置されていないことを認識します。 精度が必要な場合は、ホログラムがシナリオの近接仕様を満たしている必要があります。 | 

### <a name="how-to-measure"></a>測定する方法

* 空間マップに配置されているホログラムは、サーフェイスの上または下に劇的に浮動小数点型で表示されないようにしてください。
* 正確な配置を必要とするホログラムには、シナリオの要件に対して正確な何らかの形式のマーカーと調整システムが必要です。

### <a name="recommendations"></a>推奨事項

* 空間マップは、精度が不要な場合にオブジェクトをサーフェイスに配置する場合に便利です。
* 最適な精度を得るには、マーカーまたはポスターを使用して、ホログラムと Xbox コントローラー (または手動配置機構) を最終的な調整用に設定します。
* 特大の大きなホログラムを論理部分に分割し、各部分をサーフェイスに配置することを検討してください。
* 不適切に設定した interpupillary distance (IPD) は、ホログラムのアラインメントにも影響を与えることがあります。 常に HoloLens をユーザーの IPD に構成します。

### <a name="resources"></a>リソース

#### <a name="documentation"></a>ドキュメント

* [空間マッピングの配置](../../design/spatial-mapping.md#placement)
* [ルームスキャンプロセス](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [空間アンカーのベストプラクティス](../../design/spatial-anchors.md#best-practices)
* [追跡エラーの処理](../../design/coordinate-systems.md#handling-tracking-errors)
* [Unity の空間マッピング](../unity/spatial-mapping-in-unity.md)
* [Vuforia 開発の概要](../unity/vuforia-development-overview.md)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [MR ツールキット, 空間マッピングライブラリ](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialMapping/README.md)
* [MR コンパニオンキット、ポスター調整のサンプル](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/PosterCalibrationSample)
* [MR コンパニオンキット、Kinect IPD](https://github.com/Microsoft/MixedRealityCompanionKit/tree/master/KinectIPD)

#### <a name="external-references"></a>外部参照

* [Lowes のケーススタディ、有効桁数のアラインメント](https://www.youtube.com/watch?v=LceMdyKZ4PI)

## <a name="viewing-zone-of-comfort"></a>快適なゾーンの表示

アプリ開発者は、さまざまな深度でコンテンツとホログラムを配置することで、ユーザーの目がどのようになるかを制御します。 Hololens のディスプレイは、ユーザーから約 2.0 m 離れた光の距離で固定されているため、HoloLens を装着しているユーザーは、常に 2.0 m に対応して明確なイメージを維持します。 不適切なコンテンツの深さは、視覚不快感や疲労につながる可能性があります。

### <a name="device-impact"></a>デバイスへの影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質基準

<table>
<tr>
<td> 最高 </td><td><ul>
<li>2 m にコンテンツを配置します。</li><li>ホログラムを 2 m に配置できず、収束と宿泊の間の競合を回避できない場合、ホログラムの配置に最適なゾーンは 1.25 m ~ 5 m です。</li><li>どのような場合でも、デザイナーは、ユーザーが 1 + m を操作できるようにコンテンツを構成する必要があります (たとえば、コンテンツサイズと既定の配置パラメーターを調整します)。</li><li>シナリオで必要とされない限り、1 m から始まるフェードアウトを使用してクリッピング平面を実装する必要があります。</li><li>Motionless ホログラムの詳細な監視が必要な場合は、コンテンツが 50 cm を超えることはできません。</li>
</ul></td>
</tr><tr>
<td> あっ</td><td> コンテンツは、表示およびモーションのガイダンスに含まれていますが、不適切な使用またはクリッピング平面の使用はありません。</td>
</tr><tr>
<td> 失敗 </td><td> コンテンツが非常に近い場所に表示されます (通常は &lt; 1.25 m、またはより &lt; 詳細な監視を必要とする固定のホログラムの場合は 50 cm です)。</td>
</tr>
</table>

### <a name="how-to-measure"></a>測定する方法

* 通常、コンテンツは 2 m 離れている必要がありますが、1.25 を超える、または 5 m を超えることはできません。
* 例外がいくつかある場合は、1 m からコンテンツをフェードアウトして、HoloLens クリッピングのレンダリング距離を85CM に設定する必要があります。 コンテンツにアプローチし、クリッピング平面効果を確認します。
* 静止コンテンツは、50 cm を超えないようにする必要があります。

### <a name="recommendations"></a>推奨事項

* 最適な表示距離が 2 m になるようにコンテンツをデザインします。
* クリッピングレンダリング距離を 85 cm に設定し、1 m からコンテンツをフェードアウトします。
* 近くに表示する必要がある固定のホログラムの場合、クリッピング平面は 30 cm 以下であり、フェードアウトがクリッピング平面から少なくとも 10 cm 離れて開始される必要があります。

### <a name="resources"></a>リソース

* [レンダリング距離](hologram-stability.md#hologram-render-distances)
* [Unity でのフォーカス ポイント](../unity/focus-point-in-unity.md)
* [スケールを試してみる](../../design/scale.md#experimenting-with-scale)
* [テキスト、推奨されるフォントサイズ](../../design/typography.md#recommended-font-size)

## <a name="depth-switching"></a>深度の切り替え

快適な問題のゾーンが表示されているかどうかに関係なく、ユーザーに対して頻繁にまたは迅速に (ホログラムや実際のコンテンツを含む) 近接するオブジェクトを切り替えることによって、oculomotor と general 不快感が発生する可能性があります。

### <a name="device-impact"></a>デバイスへの影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  あっ |  失敗 |
--- | --- | ---
|  ユーザーが自然に refocus しないようにする、限定的または自然な深さの切り替え。 | [突然の深さ] スイッチこれはコアであり、アプリケーションエクスペリエンスに設計されています。または、予期しない実際のコンテンツによって発生した、突然の深さスイッチです。 | 一貫した深さスイッチ、またはアプリエクスペリエンスの中核とならない、急激な深さの切り替え。 | 

### <a name="how-to-measure"></a>測定する方法

* アプリケーションで、深さのフォーカスを一貫して変更する必要がある場合は、深さの切り替えに問題があります。

### <a name="recommendations"></a>推奨事項

* 一貫した中心面でプライマリコンテンツを保持し、安定化平面が焦点平面と一致していることを確認します。 これにより、oculomotor の疲労と予期しないホログラムの動きが軽減されます。

### <a name="resources"></a>リソース

* [レンダリング距離](hologram-stability.md#hologram-render-distances)
* [Unity でのフォーカス ポイント](../unity/focus-point-in-unity.md)

## <a name="use-of-spatial-sound"></a>空間サウンドの使用

Windows Mixed Reality では、音声エンジンは、方向、距離、および環境シミュレーションを使用して3D サウンドをシミュレートすることによって、混合した現実のエクスペリエンスの aural コンポーネントを提供します。 アプリケーションで空間サウンドを使用すると、開発者はユーザーに対して3次元空間 (球) にサウンドを convincingly ことができます。 これらのサウンドは、実際の物理オブジェクトまたはユーザーの周囲の混合現実ホログラムからのものであるように見えます。 空間サウンドは、mixed reality アプリケーションでの immersion、アクセシビリティ、UX の設計を行うための強力なツールです。

### <a name="device-impact"></a>デバイスへの影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  あっ |  失敗 |
--- | --- | ---
|  サウンドは論理的には spatialized であり、UX は適切にサウンドを使用して、オブジェクトの検出とユーザーフィードバックを支援します。 サウンドは、自然で、オブジェクトに関連し、シナリオ全体で正規化されます。 | 空間オーディオは believability に対して適切に使用されますが、ユーザーのフィードバックと検索可能性を高めるための手段としては欠けています。 | サウンドが予期したとおりに spatialized されていないか、UX 内でユーザーを支援する音がありません。 または、空間オーディオがシナリオの設計で検討されていないか、使用されていませんでした。 | 

### <a name="how-to-measure"></a>測定する方法

* 一般に、関連するサウンドは、ターゲットホログラムから出力する必要があります (たとえば、holographic dog からほえサウンドが生成されます)。
* サウンドキューは、ユーザーが holographic フレーム外のアクションをフィードバックまたは認識するのを支援するために、UX 全体で使用する必要があります。

### <a name="recommendations"></a>推奨事項

* オブジェクト検出とユーザーインターフェイスをサポートするには、空間オーディオを使用します。
* 実際のサウンドは、合成や不自然な音よりも優れています。
* ほとんどのサウンドは spatialized にする必要があります。
* 非表示の発信器は避けてください。
* 空間マスクは避けてください。
* すべてのサウンドを正規化します。

### <a name="resources"></a>リソース

#### <a name="documentation"></a>ドキュメント

* [立体音響](../../design/spatial-sound.md)
* [立体音響の設計](../../design/spatial-sound-design.md)
* [Unity の立体音響](../unity/spatial-sound-in-unity.md)
* [ケーススタディ、HoloTour の空間サウンド](../../design/case-study-spatial-sound-design-for-holotour.md)
* [RoboRaid の空間サウンドを使用したケーススタディ](../../design/case-study-using-spatial-sound-in-roboraid.md)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [Mixed Reality Toolkit-空間オーディオ](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/SpatialSound/README.md)

## <a name="focus-on-holographic-frame-fov-boundaries"></a>Holographic frame (視界) の境界にフォーカス

適切に設計されたユーザーエクスペリエンスでは、ユーザーを中心とした仮想環境の有用なコンテキストを作成し、維持することができます。 視界の境界の影響を軽減するには、コンテンツのスケールとコンテキスト、空間オーディオの使用、ガイダンスシステム、ユーザーの位置をよく設計する必要があります。 そうすれば、ユーザーは快適なアプリエクスペリエンスを実現しながら、視界の境界によって損なわれることはなくなります。

### <a name="device-impact"></a>デバイスへの影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  あっ |  失敗 |
--- | --- | ---
|  ユーザーはコンテキストを失うことはなく、表示も快適です。 ラージオブジェクトのコンテキストに関するサポートが提供されます。 フレームの外部にあるオブジェクトについて、見つけやすさと表示に関するガイダンスが提供されます。 一般に、見やすさを向上させるには、ホログラムのモーションデザインとスケールが適しています。 | ユーザーはコンテキストを失うことはありませんが、限られた状況では追加のネックモーションが必要になることがあります。 限られた状況では、ホログラムによって、ネックの動きが見られる垂直方向または水平方向のフレームが壊れることがあります。 | ホログラムを表示するには、コンテキストや一貫したネック運動が失われる可能性があります。 大規模な holographic オブジェクトに関するコンテキストガイダンスはありません。オブジェクトを移動しても、発見可能なガイダンスがなくても、オブジェクトを簡単に失うことがあります。また、広いホログラムでは、通常のネックモーションが必要になります。 | 

### <a name="how-to-measure"></a>測定する方法

* 境界でクリップされているため、(大きい) ホログラムのコンテキストが失われているか、認識されていません。
* ホログラムの場所は、holographic フレームとの間で急速に移動される、要注意のダイレクタやコンテンツがないため、見つけるのが困難です。
* シナリオでは、ネックの疲労を完全に確認するために、定期的かつ反復的に反復的に動きが必要です。

### <a name="recommendations"></a>推奨事項

* 視界に合った小さなオブジェクトを使用して操作を開始し、視覚的な手掛かりを使用して大きなバージョンに移行します。
* 空間オーディオとアテンションダイレクタを使用すると、ユーザーが視界の外にあるコンテンツを見つけやすくなります。
* 可能な限り、視界を垂直方向にクリップするホログラムは避けてください。
* ユーザーにアプリ内のガイダンスを提供して、最適な表示場所を指定します。

### <a name="resources"></a>リソース

#### <a name="documentation"></a>ドキュメント

* [ホログラフィック フレーム](../../design/holographic-frame.md)
* [ケーススタディ、HoloStudio UI、相互作用設計学習](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md?#problem-2-modal-dialogs-are-sometimes-out-of-the-holographic-frame)
* [オブジェクトと環境のスケール](../../design/scale.md)
* [カーソル、ビジュアルキュー](../../design/cursors.md#visual-cues)

#### <a name="external-references"></a>外部参照

* [視界に関する多くの ado](https://www.linkedin.com/pulse/hololens-much-ado-field-of-view-michael-hoffman?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3B6iQ%2FbTevLDU93w3I2ewLJw%3D%3D)

## <a name="content-reacts-to-user-position"></a>ユーザーの位置に反応するコンテンツ

ホログラムは、"real" オブジェクトとほぼ同じ方法で、ユーザーの位置に反応する必要があります。 注目すべき設計上の考慮事項は、ユーザーの位置が固定されていて、ユーザーの動きに合わせて調整できるとは限らない UI 要素です。 ユーザーの位置に適切に適合するようにアプリを設計すると、believable エクスペリエンスが向上し、使いやすくなります。

### <a name="device-impact"></a>デバイスへの影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質基準

<table>
<tr>
<td> 最高 </td><td> コンテンツと UI はユーザーの位置に適合するため、ユーザーは、予期されるユーザー移動の範囲内でコンテンツと自然に対話できます。</td>
</tr><tr>
<td> あっ </td><td> UI はユーザーの位置に適合しますが、ユーザーが位置を調整する必要があるキーコンテンツのビューが妨げられる可能性があります。</td>
</tr><tr>
<td> 失敗 </td><td><ol>
<li>UI 要素は移動中に失われるかロックされ、ユーザーはコントロールを自然に返す (または検索する) ことができません。</li><li>UI 要素は、プライマリコンテンツのビューを制限します。</li><li>UI の移動は、特に <a href="../../design/billboarding-and-tag-along.md">タグに沿っ</a> た ui 要素によって、距離や勢いを表示するためには最適化されていません。</li>
</ol></td>
</tr>
</table>

### <a name="how-to-measure"></a>測定する方法

* すべての測定値は、シナリオの妥当な範囲内で実行する必要があります。 ユーザーの移動は変化しますが、ユーザーの操作を極端に行うことなくアプリにトリックをかけることは避けてください。
* UI 要素の場合、ユーザーの移動に関係なく、関連するコントロールを使用できるようにする必要があります。 たとえば、ユーザーが zoom を使用して3D マップを表示しているときに、場所に関係なく、ユーザーがズームコントロールをすぐに使用できるようにする必要があります。

### <a name="recommendations"></a>推奨事項

* ユーザーはカメラで、動きを制御します。 これらのドライブを使用します。
* テキストと menuing システムの billboarding を検討してください。これは、ユーザーが移動した場合に、ワールドロックまたは非表示になります。
* ユーザーが前に何をしているかをユーザーが確認できるようにしながら、ユーザーに従う必要があるコンテンツにはタグを使用します。

### <a name="resources"></a>リソース

#### <a name="documentation"></a>ドキュメント

* [操作の設計](../../discover/hologram.md)
* [色、光、素材](../../color,-light-and-materials.md)
* [Billboard と Tag-along](../../design/billboarding-and-tag-along.md)
* [本能的な操作](../../design/interaction-fundamentals.md)
* [自発運動とユーザー移動](../../design/comfort.md#self-motion-and-user-locomotion)

## <a name="input-interaction-clarity"></a>入力の相互作用のわかりやすさ

入力の相互作用の明確さは、アプリのユーザビリティにとって重要であり、入力の一貫性、approachability、相互作用メソッドの発見性などが含まれます。 ユーザーは、relearning なしでプラットフォーム全体の共通の対話を使用できます。 アプリにカスタム入力がある場合は、それを明確に伝えることができます。

### <a name="device-impact"></a>デバイスへの影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  あっ |  失敗 |
--- | --- | ---
|  入力の相互作用メソッドは、Windows Mixed Reality に用意されている [ガイダンス](../../design/interaction-fundamentals.md)と一貫性があります。 任意のカスタム入力を標準入力と重複させることはできません (標準の相互作用を使用する必要があります)。また、ユーザーに明確に通知してデモンストレーションする必要があります。 | "最適" に似ていますが、カスタム入力は標準の入力方式では冗長です。 ユーザーは引き続き、アプリのエクスペリエンスの目標と進行状況を達成できます。 | 入力方法またはボタンのマッピングを理解するのが困難です。 入力は大幅にカスタマイズされており、標準入力、命令なし、または疲労や快適な問題を引き起こす可能性がありません。 | 

### <a name="how-to-measure"></a>測定する方法

* アプリでは、一貫 [した標準の入力方法が使用されます。](../../design/interaction-fundamentals.md)
* アプリにカスタム入力がある場合は、次の方法で明確に伝達されます。
* 最初の実行エクスペリエンス
* 入門画面
* ヒント
* ハンド コーチ
* ヘルプセクション
* ボイス オーバー

### <a name="recommendations"></a>推奨事項

* 可能な場合は常に標準の入力方法を使用します。
* 標準以外の入力方法については、デモ、チュートリアル、およびツールヒントを提供します。
* アプリ全体で一貫した相互作用モデルを使用します。

### <a name="resources"></a>リソース

#### <a name="documentation"></a>ドキュメント

* [本能的な操作](../../design/interaction-fundamentals.md)
* [対話型オブジェクト](../../design/interactable-object.md)
* [ヘッド視線入力とドウェル](../../design/gaze-and-dwell.md)
* [カーソル](../../design/cursors.md)
* [快適で見つめ](../../design/comfort.md#gaze-direction)
* [音声入力](../../design/voice-input.md)
* [モーション コントローラー](../../design/motion-controllers.md)
* [Unity 用入力移植ガイド](../porting-apps/input-porting-guide-for-unity.md)
* [Unity でのキーボード入力](../unity/keyboard-input-in-unity.md)
* [Unity の視線入力](../unity/gaze-in-unity.md)
* [Unity でのジェスチャとモーション コントローラー](../unity/gestures-and-motion-controllers-in-unity.md)
* [Unity の音声入力](../unity/voice-input-in-unity.md)
* [DirectX でのキーボード、マウス、およびコントローラー入力](../../keyboard,-mouse,-and-controller-input-in-directx.md)
* [DirectX でのヘッド視線入力とアイ視線入力](../native/gaze-in-directx.md)
* [DirectX での手とモーション コントローラー](../native/hands-and-motion-controllers-in-directx.md)
* [DirectX の音声入力](../native/voice-input-in-directx.md)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [ケーススタディ: よりパーソナルコンピューティングの追求](../../out-of-scope/case-study-the-pursuit-of-more-personal-computing.md#less-interface-in-your-face)
* [キャストスタディ: HoloStudio UI と相互作用設計学習](../../out-of-scope/case-study-3-holostudio-ui-and-interaction-design-learnings.md)
* [サンプルアプリ: 要素の周期テーブル](../unity/periodic-table-of-the-elements.md)
* [サンプルアプリ: 旧暦モジュール](../unity/lunar-module.md)

## <a name="interactable-objects"></a>対話型オブジェクト

ボタンは、2D 抽象ワールドでイベントをトリガーするために使用される比喩です。 3次元混合の現実世界では、この抽象化の世界に限定する必要はありません。 イベントをトリガーする対話型オブジェクトを指定できます。 対話型オブジェクトは、テーブル上のコーヒーカップの任意のものとして、無線でバルーンに表示できます。 フォームに関係なく、対話型オブジェクトは、ユーザーがビジュアルおよびオーディオキューを使用して明確に認識できるようにする必要があります。

### <a name="device-impact"></a>デバイスへの影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  あっ |  失敗 |
--- | --- | ---
|  フォームに関係なく、対話型オブジェクトは、アイドル、ターゲット、および選択された3つの状態にわたって、ビジュアルおよびオーディオのキューを介して認識されます。 "ご覧のように、エクスペリエンス全体で一貫して使用されています。 オブジェクトは、フリーターゲットのエラーを許容するようにスケーリングおよび配布されます。 | ユーザーは、オーディオまたはビジュアルフィードバックによってオブジェクトを対話型として認識し、オブジェクトをターゲットにしてアクティブ化することができます。 | ビジュアルまたはオーディオのキューがない場合、ユーザーは対話型オブジェクトを認識できません。 オブジェクトのスケールやオブジェクト間の距離により、相互作用がエラーを起こしやすくなります。 | 

### <a name="how-to-measure"></a>測定する方法

* 対話型オブジェクトは ' 対話型 ' として認識されます。ボタン、メニュー、アプリ固有のコンテンツを含む。 経験則として、対話型オブジェクトを対象とする場合は、ビジュアルとオーディオの手掛かりが必要です。

### <a name="recommendations"></a>推奨事項

* 対話のためにビジュアルとオーディオフィードバックを使用します。
* 視覚的なフィードバックは、入力状態 (アイドル、ターゲット、選択) ごとに区別される必要があります
* 対話型オブジェクトは、エラーをターゲットにするためにスケーリングして配置する必要があります。
* グループ化された対話型オブジェクト (メニューバーやリストなど) には、ターゲットを設定するための適切なスペースが必要です。
* 音声コマンドをサポートするボタンとメニューでは、command キーワードにテキストラベルを指定する必要があります (「参照してください」と言います)。

### <a name="resources"></a>リソース

#### <a name="documentation"></a>ドキュメント

* [対話可能なオブジェクト](../../design/interactable-object.md)
* [Unity のテキスト](../unity/text-in-unity.md)
* [境界ボックスとアプリ バー](../../design/app-bar-and-bounding-box.md)
* [音声入力](../../design/voice-input.md)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [Mixed Reality Toolkit-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="room-scanning"></a>部屋のスキャン

空間マッピングデータを必要とするアプリは、ユーザーがデバイスをアクティブにして環境を探索するときに、このデータを時間の経過と共に自動的に収集するためにデバイスに依存します。 このデータの完全性と品質は、ユーザーが実行した探索の量、探索から経過した時間、家具やドアなどのオブジェクトが領域をスキャンした後に移動されたかどうかなど、さまざまな要因によって異なります。 多くのアプリは、エクスペリエンスの開始時に空間マッピングデータを分析して、ユーザーが空間マップの完全性と品質を向上させるために追加の手順を実行する必要があるかどうかを判断します。 ユーザーが環境をスキャンする必要がある場合は、スキャンの実行中に [ガイダンスのクリア] を指定する必要があります。

### <a name="device-impact"></a>デバイスへの影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>❌</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  あっ |  失敗 |
--- | --- | ---
|  ユーザーによるスキャンを通知する空間メッシュの視覚化が進行中です。 ユーザーは、何を行うか、およびスキャンが開始および停止するタイミングを明確に把握します。 | 空間メッシュの視覚化が提供されていますが、ユーザーが何をしているかを明確に把握しておらず、進行状況に関する情報が提供されていない可能性があります。 | メッシュの視覚化がありません。 検索する場所、またはスキャンの開始/停止時に関するガイダンス情報はユーザーに提供されません。 |

### <a name="how-to-measure"></a>測定する方法

* 必要な部屋のスキャン中に、検索する場所と、スキャンを開始および停止するタイミングを示すビジュアルおよびオーディオのガイダンスが提供されます。

### <a name="recommendations"></a>推奨事項

* ユーザーの近くにあるユーザーの合計ボリュームがエクスペリエンスの一部である必要があるかどうかを示します。
* スキャンが開始され、進行状況インジケーターなどの停止時に通信します。
* スキャン中にメッシュの視覚エフェクトを使用します。
* ユーザーが部屋を見たり、移動したりすることを奨励するために、ビジュアルとオーディオの手掛かりを提供します。
* データを改善するための場所をユーザーに通知します。 多くの場合、必要なスキャン品質を得るために、ユーザーに対して実行する必要があること (たとえば、天井、家具を見てみてください) を伝えることが最適な場合があります。

### <a name="resources"></a>リソース

#### <a name="documentation"></a>ドキュメント

* [部屋のスキャンの可視化](../../design/room-scan-visualization.md)
* [ケーススタディ: HoloLens の空間マッピング機能の拡張](../../out-of-scope/case-study-expanding-the-spatial-mapping-capabilities-of-hololens.md)
* [ケーススタディ: HoloTour の空間サウンド設計](../../design/case-study-spatial-sound-design-for-holotour.md)
* [ケーススタディ: フラグメントでのイマーシブエクスペリエンスの作成](../../out-of-scope/case-study-creating-an-immersive-experience-in-fragments.md)

#### <a name="tools-and-tutorials"></a>ツールとチュートリアル

* [Mixed Reality Toolkit-UX](https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit-Examples/UX)

## <a name="directional-indicators"></a>方向インジケーター

Mixed reality アプリでは、コンテンツは、実際のオブジェクトによって view または occluded のフィールドの外部にある場合があります。 適切にデザインされたアプリを使用すると、ユーザーが非表示のコンテンツを簡単に見つけられるようになります。 ディレクショナルインジケーターは、ユーザーに重要なコンテンツを通知し、ユーザーの位置を基準にしてコンテンツに関するガイダンスを提供します。 非表示コンテンツに関するガイダンスは、サウンドの発信器、方向矢印、または直接視覚的な合図の形式になります。

### <a name="device-impact"></a>デバイスへの影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  あっ |  失敗 |
--- | --- | ---
|  ビジュアルおよびオーディオキューは、ビューのフィールドの外部にある関連するコンテンツをユーザーに直接案内します。 | コンテンツの一般的な方向にユーザーを示す矢印またはインジケーター。 | 関連するコンテンツはビューのフィールドの外部にあり、ユーザーには不適切または場所のガイダンスは提供されません。 | 

### <a name="how-to-measure"></a>測定する方法

* ビューの [ユーザー] フィールド以外の関連するコンテンツは、ビジュアルまたはオーディオキューを使用して検出できます。

### <a name="recommendations"></a>推奨事項

* 関連するコンテンツがユーザーのビューの外部にある場合は、方向インジケーターとオーディオキューを使用して、ユーザーをコンテンツに案内します。 多くの場合、方向性のある矢印よりも直接の視覚的なガイドをお勧めします。
* 方向インジケーターをカーソルに組み込むことはできません。

### <a name="resources"></a>リソース

* [ホログラフィック フレーム](../../design/holographic-frame.md)

## <a name="data-loading"></a>データの読み込み

プログレス コントロールは、時間のかかる操作が進行中であることを示すフィードバックをユーザーに返します。 これは、進行状況インジケーターが表示されているときにユーザーがアプリと対話できないことを意味し、待機時間がどの程度かかるかを示すこともできます。

### <a name="device-impact"></a>デバイスへの影響

<table>
    <colgroup>
    <col width="33%" />
    <col width="33%" />
    <col width="33%" />
    </colgroup>
    <tr>
        <td><a href="../../hololens-hardware-details.md"><strong>HoloLens</strong></a></td>
        <td><a href="../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
        <td></td>
    </tr>
     <tr>
        <td>✔️</td>
        <td>✔️</td>
        <td></td>
    </tr>
</table>

### <a name="quality-criteria"></a>品質基準

|  最高  |  あっ |  失敗 |
--- | --- | ---
|  データの読み込み中または処理中の進行状況を示す進行状況バーまたはリングの形式でのアニメーション化されたビジュアルインジケーター。 ビジュアルインジケーターは、待機時間の長さに関するガイダンスを提供します。 | ユーザーには、データの読み込みが進行中であることが通知されますが、待機時間を示すことはできません。 | タスクのデータ読み込みまたはプロセスインジケーターが5秒より長くかかっていません。 |

### <a name="how-to-measure"></a>測定する方法

* データの読み込み中に、5秒を超える空の状態がないことを確認します。

### <a name="recommendations"></a>推奨事項

* ユーザーがこのアプリを停止またはクラッシュしていると認識した場合に、進行状況を示すデータ読み込みのアニメーターを提供します。 目安として合理的なのは、5秒以上かかる可能性のある "読み込み" アクティビティです。

### <a name="resources"></a>リソース

* [進行状況を表示する](../../design/progress.md)
