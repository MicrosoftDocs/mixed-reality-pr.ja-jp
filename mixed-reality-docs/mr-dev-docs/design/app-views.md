---
title: アプリ ビュー
description: Windows Mixed Reality アプリの2種類のビューは、イマーシブビューと2D ビューです。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: イマーシブビュー、2D ビュー、スレート、アプリ
ms.openlocfilehash: e625eca3adb7cd4a9dcd1f971917f008d5daa7d2
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685170"
---
# <a name="app-views"></a>アプリ ビュー

Windows アプリには、2種類のビュー、 **イマーシブビュー** 、および **2d ビュー** を含めることができます。 アプリでは、さまざまなイマーシブビューと2D ビューを切り替えることができます。モニター上の2D ビューは、ウィンドウとして、またはヘッドセットにスレートとして表示されます。 少なくとも1つのイマーシブビューを持つアプリは、 **mixed reality アプリ** として分類されます。 イマーシブビューを持たないアプリは、 **2d アプリ** です。

## <a name="immersive-views"></a>イマーシブビュー

アプリでイマーシブ ビューを使用すると、ユーザーの周囲にホログラムを作成したり、ユーザーを仮想環境に没入させたりすることができます。 アプリがイマーシブビューで描画されている場合、 &mdash; 複数のアプリのホログラムが同時に描画されることはありません。 アプリがユーザーの頭の動きに合わせてシーンを [レンダリング](../develop/platform-capabilities-and-apis/rendering.md) するパースペクティブを継続的に調整することにより、アプリでは、現実世界の固定されたポイントにとどまっている [世界中のロック](coordinate-systems.md) されたホログラムをレンダリングしたり、ユーザーが移動したときにその位置を保持する仮想世界をレンダリングしたりすることができます。

![イマーシブビューでは、ホログラムを世界中に配置できます。](images/designoverview-940px.jpg)<br>
*イマーシブビューでは、ホログラムを世界中に配置できます。*

[HoloLens](https://docs.microsoft.com/hololens/hololens1-hardware)では、アプリはユーザーの実際の環境の上にホログラムをレンダリングします。 [Windows Mixed Reality のイマーシブヘッドセット](../discover/immersive-headset-hardware-details.md)では、ユーザーは実際の世界を見ることができないため、ユーザーに表示されるすべてのものをアプリでレンダリングする必要があります。

[Windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)(環境の周囲に配置した [スタート] メニューとホログラムを含む) は、イマーシブビューでは表示されません。 HoloLens では、イマーシブビューが表示されている間に発生するシステム通知は、Cortana によって音声でリレーされ、ユーザーは音声入力を使用して応答できます。

イマーシブビューでは、すべての入力を処理することもアプリに任されています。 Windows Mixed Reality での入力は、 [宝石](gaze-and-commit.md)、 [ジェスチャ](gaze-and-commit.md#composite-gestures) (HoloLens のみ)、 [音声](voice-input.md) および [モーションコントローラー](motion-controllers.md) (イマーシブヘッドセットのみ) で構成されています。

## <a name="2d-views"></a>2D ビュー

![Windows Mixed Reality ホームの周囲にレイアウトされた複数の2D ビュー](images/teleportation-940px.png)<br>
*Windows Mixed Reality ホームの周囲に2D ビューが配置された複数のアプリ*

2D ビューを使用するアプリは、 [Windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md) ("シェル" とも呼ばれます) に仮想スレートとして表示されます。これは、アプリランチャーと、ユーザーが世界中に配置したその他のホログラムと共にレンダリングされます。 ユーザーは、サイズに関係なく固定された解像度でも、このスレートを調整してスケールすることができます。 アプリの最初のビューが2D ビューの場合、2D コンテンツはアプリを起動するために使用されるものと同じスレートに収まるようになります。

デスクトップヘッドセットでは、現在デスクトップモニター上で実行されている任意のユニバーサル Windows プラットフォーム (UWP) アプリを実行できます。 これらのアプリは既に2D ビューをレンダリングしており、そのコンテンツは、起動時にユーザーの世界のスレートに自動的に表示されます。 2D UWP アプリは、デスクトップヘッドセットと HoloLens on スレートの両方で動作するように **Windows ユニバーサル** デバイスファミリをターゲットにすることができます。

2D ビューの主な用途の1つは、システムキーボードを利用できるテキスト入力フォームを表示することです。 シェルは、イマーシブビューの上にレンダリングできないため、アプリケーションは、システムキーボードを表示するために2D ビューに切り替える必要があります。 テキスト入力を受け入れるアプリでは、テキストボックスを使用して2D ビューに切り替えることができます。 このテキストボックスにフォーカスがあるときは、システムキーボードが表示され、ユーザーはテキストを入力できます。

デスクトップ PC では、アプリはデスクトップモニターと接続されたヘッドセットの両方に2D ビューを持つことができます。 たとえば、メインの2D ビューを使用してデスクトップモニターのエッジを参照し、360度のビデオを見つけることができます。 このビデオを再生すると、Edge は、ヘッドセット内の2次的なイマーシブビューを起動して、イマーシブビデオコンテンツを表示します。

## <a name="see-also"></a>関連項目

* [アプリ モデル](app-model.md)
* [複合現実の 2D UWP アプリを更新する](../develop/porting-apps/building-2d-apps.md)
* [HolographicSpace を入手する](../develop/native/getting-a-holographicspace.md)
* [Windows Mixed Reality ホームのナビゲーション](../discover/navigating-the-windows-mixed-reality-home.md)
* [複合現実アプリの種類](types-of-mixed-reality-apps.md)
