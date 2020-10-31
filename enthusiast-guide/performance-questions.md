---
title: パフォーマンスに関する FAQ
description: パフォーマンスに関する Windows Mixed Reality のトラブルシューティングは、標準のコンシューマーサポートドキュメントを超えています。
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート、パフォーマンス
appliesto:
- Windows 10
ms.openlocfilehash: d6b37f8f6c964222b90fff57f0ba994c14fcaeab
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131966"
---
# <a name="performance-faqs"></a>パフォーマンスに関する FAQ

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60hz-or-90hz-framerate"></a>Windows Mixed Reality ヘッドセットのレンダリングは、60Hz または90Hz フレームレートで表示されます

HDMI 2.0 ポートを備えた独立した GPU と4つ以上の物理コアを搭載した CPU がある場合は、90 Hz である必要があります。 確認するには、 **デバイスポータル >** の [パフォーマンス] タブを確認します。

注: GPU に HDMI 1.4 出力しかない場合は、回避策として DisplayPort [2.0 アダプター](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) を使用できます。

注: "ヘッドセット表示" のビジュアル品質設定は、Windows Mixed Reality ホームエクスペリエンスのレンダリングにのみ影響します。

## <a name="my-pc-is-running-slowly"></a>PC の動作が遅くなっています

システムは多くの理由で低速である可能性があり、ほとんどの場合、これはわずか数秒で終了します。 長時間にわたってこの問題が発生する場合は、次の手順を実行します。

1. デスクトップ上の未使用のアプリケーションをすべて閉じます。
2. ラップトップが電源に接続されていることを確認します。
3. PC がウォームアップされていないことを確認します。
4. Windows Mixed Reality ホームのビジュアル品質を下げます。
5. PC 用の最新の [グラフィックスドライバー](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) があることを確認します。

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>私の PC は、Mixed Reality エクスペリエンスを実行するとウォームアップしています。 操作方法クールに保つ

1. バッテリが充電され、電源が接続されていることを確認します。
2. PC ファンがブロックされていないことを確認します。
3. 比較的クールな環境で PC を使用します。
4. PC で指されている熱源 (太陽や熱源など) がないことを確認します。

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>視覚エフェクトが途切れている、読み込みに時間がかかる、または適切ではない

* ヘッドセットが PC の正しいグラフィックスカードに接続されていることを確認します。 Pc によっては、統合グラフィックスカードと不連続グラフィックスカードの両方が搭載されています。 通常、不連続カードは最適なパフォーマンスを提供します。 [PC ハードウェアの詳細について](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)は、こちらを参照してください。
* デスクトップで使用していないアプリケーションを閉じます。
* ヘッドセットがしっかり合っていることを確認します (下または右に移動するか、左右に移動します)。
* [設定] で、ヘッドセットの表示設定を調整します。 **> Mixed reality > ヘッドセットの表示** になります。 "視覚品質" が "自動" に設定されている場合、PC の mixed reality エクスペリエンスが自動的に選択されます。 詳細を表示するには、"視覚品質" を "高" に設定します。 ビジュアルが途切れている場合は、下の設定を選択します。
* ヘッドホン調整ノブを調整して、レンズが pupils (IPD) 間の正しい距離に設定されていることを確認します。 IPD がわからない場合は、optometrist で測定するか、IPD を測定するように設計された web サイトを使用することができます。 ヘッドセットに調整ノブがない場合は、[ **設定 > Mixed reality > ヘッドセットの表示** ] を選択し、[調整コントロール] を調整します。
* USB-C または DisplayPort を HDMI アダプターとして使用している場合は、別のアダプターを試してみてください。 [推奨されるアダプターを](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)参照してください。
* PC のグラフィックスカードに接続されている可能性のある追加モニターを切断します。
* Windows ストアからいくつかの異なる mixed reality アプリを試してみてください。コンピューターをセットアップすると、より適切に動作する場合があります。
