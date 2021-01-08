---
title: Unity の立体音響
description: 例を使用して、Unity シーン内の特定の3D ポイントから空間サウンドを再生し、減衰する方法について説明します。
author: kegodin
ms.author: v-hferrone
ms.date: 11/07/2019
ms.topic: article
keywords: Unity、空間サウンド、HRTF、部屋サイズ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、MRTK、Mixed Reality Toolkit、spatializer、リバーブ
ms.openlocfilehash: ec2703aa89925cb68860670f574a1e43f672e247
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009272"
---
# <a name="spatial-sound-in-unity"></a>Unity の立体音響

このページでは、Unity の空間サウンドのリソースにリンクしています。

## <a name="spatializer-options"></a>Spatializer オプション

Mixed reality アプリケーションの Spatializer オプションは次のとおりです。
* Unity では、 *Windows Mixed Reality* のオプションパッケージの一部として *MS HRTF Spatializer* を提供しています。
  * 高コストの ' 単一ソース ' アーキテクチャで CPU 上で実行されます。
  * 元の HoloLens アプリケーションとの下位互換性のために用意されています。
* Microsoft *Spatializer* は、 [microsoft Spatializer GitHub リポジトリ](https://github.com/microsoft/spatialaudio-unity)から入手できます。
  * 低コストの ' マルチソース ' アーキテクチャを使用します。
  * HoloLens 2 のハードウェアアクセラレータにオフロードされます。 

新しいアプリケーションの場合は、 *Microsoft Spatializer* をお勧めします。

## <a name="enable-spatialization"></a>Spatialization を有効にする

[Unity の NuGet](https://github.com/GlitchEnzo/NuGetForUnity/releases/latest)を使用して _SpatialAudio_ をインストールし、プロジェクトのオーディオ設定で **microsoft Spatializer** を選択します。 その後、以下を実行します。
* 階層内のオブジェクトに **オーディオソース** をアタッチする
* [ **Enable spatialization** ] チェックボックスをオンにします。
* **空間ブレンド** スライダーを ' 1 ' に移動します
* 開発者ワークステーションで空間オーディオが有効になっていることを確認します。 
    * タスクバーのボリュームアイコンを右クリックし、[空間サウンド] が [オフ] 以外に設定されていることを確認します。 
    * **Windows Sonic For ヘッドホン** を選択すると、HoloLens 2 で聞く内容を最適に表示できます。

>[!NOTE]
>Unity で、その依存関係の1つが見つからないために SpatialAudio を読み込めないというエラーが表示される場合は、最新バージョンの [Microsoft Visual C++ 再頒布可能パッケージ](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) が PC にインストールされていることを確認します。

   詳細については、次を参照してください。
* [Microsoft spatializer GitHub リポジトリ](https://github.com/microsoft/spatialaudio-unity)
* [Microsoft の spatializer チュートリアル](tutorials/unity-spatial-audio-ch1.md)
* [Unity のオーディオソースドキュメント](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)
* [Unity の spatializer のドキュメント](https://docs.unity3d.com/Manual/VRAudioSpatializer.html)

## <a name="distance-based-attenuation"></a>距離ベースの減衰

Unity の既定の距離ベースの減衰には、最小距離は1メーター、最大距離は500メートル、対数のロールアウトがあります。 これらの設定は、シナリオによっては機能する場合があります。また、ソースが急激に増加したり、遅くなったりする場合もあります。    詳細については、次を参照してください。
* 推奨設定のための[混合現実のサウンドデザイン](../../design/spatial-sound-design.md)。
* これらの曲線を設定する方法については、 [Unity のオーディオソースドキュメント](https://docs.unity3d.com/2019.3/Documentation/Manual/class-AudioSource.html)を参照してください。

## <a name="reverb"></a>ほど

_Microsoft Spatializer_ は、既定で Spatializer 効果を無効にします。 Spatialized ソースに対してリバーブとその他の効果を有効にするには:
* 各ソースに **Room 効果の送信レベル** コンポーネントをアタッチする
* 各ソースの送信レベル曲線を調整して、エフェクト処理のためにグラフに返されるオーディオのゲインを制御します。

詳細について [は、spatializer チュートリアルの第5章](tutorials/unity-spatial-audio-ch5.md) を参照してください。

## <a name="unity-spatial-sound-examples"></a>Unity の空間サウンドの例

Unity の空間サウンドの例については、次を参照してください。
* [MRTK デモ](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_release/Assets/MixedRealityToolkit.Examples/Demos/Audio)
* [Microsoft Spatializer サンプルプロジェクト](https://github.com/microsoft/spatialaudio-unity/tree/master/Samples/MicrosoftSpatializerSample)

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

Unity の開発について説明した経験がある場合は、Mixed Reality コアの構成要素を調査しています。 ここから、次の構成要素を続けることができます。

> [!div class="nextstepaction"]
> [テキスト](text-in-unity.md)

または、Mixed Reality プラットフォームの機能と API に移動します。

> [!div class="nextstepaction"]
> [共有エクスペリエンス](shared-experiences-in-unity.md)

いつでも [Unity 開発チェックポイント](unity-development-overview.md#2-core-building-blocks)に戻ることができます。

## <a name="see-also"></a>関連項目

* [混合現実におけるサウンドのデザイン](../../design/spatial-sound-design.md)
* [Microsoft の spatializer チュートリアル](tutorials/unity-spatial-audio-ch1.md)
