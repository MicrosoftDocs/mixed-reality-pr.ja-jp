---
title: Spectator View
description: 複合現実エクスペリエンスを外部ディスプレイでデモンストレーションしたり録画したりする手段として、外部デバイスからのホログラムを視覚化します。
author: chrisfromwork
ms.author: chriba
ms.date: 02/11/2019
ms.topic: article
ms.localizationpriority: high
keywords: Spectator View, iPhone, iOS, iPad, OpenCV, カメラ, ARKit, HoloLens, 複合現実, MixedRealityToolkit, デモ, 記録
ms.openlocfilehash: 7b48315753ada0ae7a94abca5377a083ac659a34
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91700539"
---
# <a name="spectator-view-for-hololens-and-hololens-2"></a>HoloLens および HoloLens 2 向けの Spectator View

![Marker](images/SpecViewPhoneHero.jpg)

## <a name="overview"></a>概要

HoloLens を装着していると、自分が体験している素晴らしい世界を、HoloLens を装着していない人は見ることができないことをしばしば忘れてしまいます。 Spectator View を使用すれば、HoloLens ユーザーが見ている世界を他のユーザーが 2D 画面で見ることができます。
Spectator View は、モバイル デバイスを使用して HD でホログラムを記録するための高速で手頃な方法を提供します。 さらに、ビデオ カメラを使用したホログラムのプロ品質の録画も提供します。

## <a name="key-resources"></a>重要なリソース

* [**Spectator View (GitHub)**](https://github.com/microsoft/MixedReality-SpectatorView)
* [**Spectator View のドキュメント**](https://microsoft.github.io/MixedReality-SpectatorView/README.html)
* [**Spectator View のサンプル**](https://github.com/microsoft/MixedReality-SpectatorView/tree/master/samples)

## <a name="use-cases"></a>使用事例
* iPhone または Android デバイスを使用して、複合現実エクスペリエンスを記録できます。 フル HD で記録し、ホログラムだけでなく、影にもアンチエイリアシングを適用します。 それは、ホログラムの動画をキャプチャするための費用対効果が高く、簡単に実行できる方法です。
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
