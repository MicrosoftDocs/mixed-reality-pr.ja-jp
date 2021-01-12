---
title: Spectator View
description: 外付けデバイスからホログラムを視覚化して、外付けディスプレイで Mixed Reality エクスペリエンスを表示または記録します。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, カメラ, ARKit, HoloLens, 複合現実, MixedRealityToolkit, デモ, 記録
ms.openlocfilehash: 1f61d2094ec2762ab22576d2eac85ed6bf81d5c7
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008612"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>HoloLens および HoloLens 2 向けの Spectator View

![Marker](images/SpecViewPhoneHero.jpg)

HoloLens を装着していると、自分が見ている素晴らしい世界を、装着していない人は体験できないことを忘れがちです。 Spectator View を使用すれば、HoloLens ユーザーが見ているものを他のユーザーが 2D 画面で見ることができます。 これは、モバイル デバイスを使用してホログラムを HD に記録し、ビデオ カメラを使用してホログラムの高品質な記録を取得するための高速で手頃な方法でもあります。

## <a name="key-resources"></a>重要なリソース

* [**Spectator View (GitHub)**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Spectator View のドキュメント**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**Spectator View のサンプル**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>使用事例

* iPhone または Android デバイスを使用して、複合現実エクスペリエンスを記録できます。 フル HD で記録し、ホログラムと影にアンチエイリアシングを適用して、コスト効率に優れた方法でホログラムの動画を迅速にキャプチャできます。
* 複合現実エクスペリエンスを、iPhone または iPad から直接 Apple TV にライブ ストリーミングします。遅延は発生しません。
* ゲストとエクスペリエンスを共有します。非 HoloLens ユーザーが各自の電話やタブレットから直接ホログラムを体験できるようにします。

## <a name="current-features"></a>現在の機能

* ホログラムの空間同期。これにより、すべてのユーザーが同じ場所でホログラムを確認できるようになります。
* iOS (ARKit 対応デバイス) と Android (ARCore 対応デバイス) のサポート。
複数の iOS ゲスト。
動画 + ホログラム + 周囲の音 + ホログラムの音の記録。
シートを共有して、動画を保存したり、電子メールで送信したり、他のサポート アプリと共有したりできるようにします。

![マーカー](images/SpecViewPhoneDemo.jpg)
![マーカー](images/hololensspectatorview-500px.jpg) ![マーカー](images/spectatorview-300px.png)

次の表に、Spectator View のさまざまな機能を示します。 ご自分の録画のニーズに最適なオプションを選択してください。

|      機能                                | モバイル                  |                    ビデオ カメラ              |
|--------------------------------------|:-----------------------:|:-------------------------------------------:|
| HD 品質                           |         フル HD         |        プロ品質の撮影 (ビデオ カメラによって決定される)      |
| カメラの容易な移動                 |            ✔            |                      ✔                      |
| 第三者の視点                    |            ✔            |                      ✔                      |
| 画面にストリーム可能           |            ✔            |                      ✔                      |
| 移植性があります。                             |            ✔            |                                             |
| ワイヤレス                             |            ✔            |                                             |
| 必要な追加のハードウェア         |     Android フォン、iPhone    | HoloLens + リグ + 三脚 + ビデオ カメラ + PC + Unity |
| ハードウェア投資                  |           低            |                     高                    |
| クロスプラットフォーム                       |           Android、iOS   |                                             |
| 同期されるコンテンツ                 |            ✔            |                      ✔                      |
| ランタイムのセットアップ期間               |         即時          |                     遅い                    |
## <a name="see-also"></a>関連項目

* [複合現実キャプチャ](../../mixed-reality-capture.md) 
* [開発者向け複合現実キャプチャ](mixed-reality-capture-for-developers.md)
* [複合現実での共有エクスペリエンス](shared-experiences-in-mixed-reality.md)
