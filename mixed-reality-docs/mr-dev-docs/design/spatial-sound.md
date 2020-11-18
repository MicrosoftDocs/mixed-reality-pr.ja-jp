---
title: 混合現実のオーディオ
description: 混合現実のオーディオを使用すると、UI インタラクションのユーザーの信頼を高め、ユーザーのエクスペリエンスをこちらことができます。
author: kegodin
ms.author: kegodin
ms.date: 11/07/2019
ms.topic: article
keywords: 空間サウンド, サラウンドサウンド, 3d オーディオ, 3d サウンド, 空間オーディオ, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット, HoloLens, MRTK, Mixed Reality ツールキット, ケーススタディ, acoustics
ms.openlocfilehash: 50a5b4a634eec5a326158975f70fa385ce7af6a8
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703258"
---
# <a name="audio-in-mixed-reality"></a>混合現実のオーディオ
オーディオは、混合現実の設計と生産性の重要な部分です。 サウンドは次のとおりです。
* ジェスチャと音声のやり取りでユーザーの信頼度を高めます。
* 次の手順にユーザーを案内します。
* 仮想オブジェクトを実際の環境と効果的に結合します。

HoloLens を含む mixed reality ヘッドセットの待機時間の短いヘッドトラッキングでは、高品質の HRTF ベースの spatialization がサポートされます。 アプリケーションでオーディオを spatialize するには、次のようにします。
* ビジュアル要素に注目します。
* ユーザーが実際の環境について認識できるようにします。

Acoustics により深い接続ホログラムが混合現実の世界になります。 環境とオブジェクトの状態に関する手掛かりを提供します。

[オーディオを使用するデザインの詳細な例を](spatial-sound-design.md)参照してください。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/PTPvx7mDon4" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

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
        <td><a href="../hololens-hardware-details.md"><strong>HoloLens (最初の世代)</strong></a></td>
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></td>
    </tr>
     <tr>
        <td>空間化</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️</td>
    </tr>
     <tr>
        <td>Spatialization ハードウェアアクセラレーション</td>
        <td>❌</td>
        <td>✔️</td>
        <td>❌</td>
    </tr>
</table>

## <a name="use-of-sounds-in-mixed-reality"></a>Mixed reality でのサウンドの使用
[Mixed reality でサウンドを使用する](spatial-sound-design.md) には、タッチおよびキーボードおよびマウスアプリケーションとは異なるアプローチが必要です。 サウンド設計の主な決定事項には、どのようなサウンドを spatialize し、どのような対話を sonify にするかが含まれます。 これらの決定は、ユーザーの自信、生産性、学習曲線に大きな影響を与えます。

### <a name="case-studies"></a>ケース スタディ
HoloTour は事実上、世界中の tourist と歴史的なサイトにユーザーを移動させることになります。 HoloTour のケーススタディについては、「 [サウンドのデザイン」を](case-study-spatial-sound-design-for-holotour.md) 参照してください。 特殊なマイクとレンダリングのセットアップを使用して、サブジェクトスペースがキャプチャされました。

RoboRaid は、HoloLens の高エネルギー shooter です。 RoboRaid ケーススタディ [のサウンド設計](case-study-using-spatial-sound-in-roboraid.md) では、空間オーディオが最大限効果を得るために使用された設計上の選択肢について説明します。

## <a name="spatialization"></a>空間化
Spatialization は、空間オーディオの方向コンポーネントです。 7.1 home シアターセットアップの場合、spatialization は loudspeakers 間のパンと同様に簡単です。 しかし、混合現実のヘッドホンでは、精度と快適さを実現するために HRTF ベースのテクノロジを使用することが不可欠です。 Windows には HRTF ベースの spatialization が用意されており、このサポートは HoloLens 2 でハードウェアアクセラレータを利用しています。

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/aB3TDjYklmo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="should-i-spatialize"></a>Spatialize ですか。
Spatialization は、mixed reality アプリケーションの多くのサウンドを向上させることができます。 Spatialization はリスナーの頭から音を受け取り、世界に置きます。 アプリケーションで spatialization を効果的に使用するための推奨事項については、「 [空間サウンドの設計](spatial-sound-design.md)」を参照してください。

### <a name="spatializer-personalization"></a>Spatializer のパーソナル化
HRTFs は、頻度の範囲内の耳間のレベルとフェーズの差を操作します。 これらは、物理的なモデルと、人間の頭、torso および ear 図形 (pinnae) の測定値に基づいています。 脳は、これらの違いに反応して、認識された方向にサウンドを提供します。

各個人には、独自の ear 図形、ヘッドサイズ、および耳の位置があります。 したがって、最適な HRTFs が準拠しています。 Spatialization の精度を高めるために、HoloLens はヘッドセット表示の pupilary 距離 (IPD) を使用して、ヘッドサイズに対して HRTFs を調整します。

### <a name="spatializer-platform-support"></a>Spatializer プラットフォームのサポート
Windows では、 [ISPATIALAUDIOCLIENT API](https://docs.microsoft.com/windows/win32/coreaudio/spatial-sound)を使用して、hrtfs などの spatialization を提供しています。 この API は、HoloLens 2 HRTF ハードウェアアクセラレーションをアプリケーションに公開します。

### <a name="spatializer-middleware-support"></a>Spatializer ミドルウェアのサポート
Windows の HRTFs のサポートは、次のサードパーティのオーディオエンジンで利用できます。
* [Unity オーディオエンジンプラグイン](../develop/unity/spatial-sound-in-unity.md)
* [Wwise なオーディオエンジンプラグイン](https://www.audiokinetic.com/products/plug-ins/msspatial/)

## <a name="acoustics"></a>音響
空間オーディオは、方向よりも大きくなります。 その他のディメンションには、遮蔽、障害、リバーブ、portalling、ソースモデリングなどがあります。 これらのディメンションをまとめて、 *acoustics* と呼びます。 Acoustics を使用しない場合、spatialized は認識できない距離になります。

Acoustics は単純なものから非常に複雑なものまでの範囲です。 任意のオーディオエンジンでサポートされている簡単なリバーブを使用して、spatialized サウンドをリスナーの環境にプッシュできます。 [Project Acoustics](https://aka.ms/acoustics)などの Acoustics システムでは、より豊富で説得力の高い Acoustics 処理が提供されています。 プロジェクト Acoustics は、壁、ドア、およびその他のシーンジオメトリの効果をサウンドでモデル化できます。 これは、開発時に関連するシーンジオメトリが既知の場合に有効なオプションです。

## <a name="next-steps"></a>次のステップ
- [Unity の立体音響](../develop/unity/spatial-sound-in-unity.md)
- [Mixed reality アプリケーションでサウンドを使用する方法](spatial-sound-design.md)
