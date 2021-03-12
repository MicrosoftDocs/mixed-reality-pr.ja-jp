---
title: ScreenshotUtility
description: MRTK でスクリーンショット ツールを使用する方法に関するドキュメント
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
ms.localizationpriority: high
keywords: Unity, HoloLens, HoloLens 2, Mixed Reality, 開発, MRTK,
ms.openlocfilehash: a1f5e6503244852d79abaf143f8e922ceb1b489c
ms.sourcegitcommit: 97815006c09be0a43b3d9b33c1674150cdfecf2b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/03/2021
ms.locfileid: "101770741"
---
# <a name="screenshot-utility"></a>スクリーンショット ユーティリティ

多くの場合、ドキュメントやプロモーション用の画像のために Unity でスクリーンショットを撮ることは煩雑であり、出力は望ましいものとは言えません。 ここで、`ScreenshotUtility` (xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.ScreenshotUtility) クラスが機能します。

ScreenshotUtility クラスは、Unity エディター内のメニュー項目とパブリック API を使用したスクリーンショットの撮影を支援します。 スクリーンショットをさまざまな解像度および無色透明でキャプチャして、画像の合成のポスト処理に簡単に使用できます。 スタンドアロン ビルドからスクリーンショットを撮ることは、このツールではサポートされていません。

## <a name="taking-screenshots"></a>スクリーンショットを撮る

スクリーンショットを簡単にキャプチャするには、エディターで、 *[Mixed Reality Toolkit] -> [ユーティリティ] -> [スクリーンショットを撮る]* を選択し、目的のオプションを選択します。 再生していないときにキャプチャする場合、ゲーム ウィンドウ タブが表示されていることを確認します。そうしないと、スクリーンショットが保存されない場合があります。

既定では、すべてのスクリーンショットが[一時キャッシュ パス](https://docs.unity3d.com/ScriptReference/Application-temporaryCachePath.html)に保存され、スクリーンショットへのパスが Unity コンソールに表示されます。

![スクリーンショット ユーティリティのメニュー項目](../images/screenshot-utility/MRTK_ScreenshotUtility_Menu_Item.png)

## <a name="example-screenshot-capture"></a>スクリーンショットのキャプチャの例

下のスクリーンショットは、"*4 倍の解像度 (透明な背景)* " オプションを使用してキャプチャされました。 これにより、透明ピクセルとして保存されたクリア カラーで通常表されるピクセルにより高解像度の画像が出力されます。 この手法を使用すると、開発者はこの画像を他の画像の上に重ねて、ストアやその他のメディア発信源にアプリケーションを展示できます。

![スクリーンショット ユーティリティのキャプチャ例](../images/screenshot-utility/MRTK_ScreenshotUtility_Example_Capture.png)
