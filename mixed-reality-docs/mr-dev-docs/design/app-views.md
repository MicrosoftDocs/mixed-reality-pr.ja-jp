---
title: アプリ ビュー
description: Windows Mixed Reality アプリでの2種類のビュー (イマーシブビューと2D ビュー) を使用する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: イマーシブビュー、2D ビュー、スレート、アプリ、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット、HoloLens、MRTK、Mixed Reality Toolkit
ms.openlocfilehash: b6a16fc3b1ac45d74874f37ce44a36d3e144fee8
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580101"
---
# <a name="app-views"></a>アプリ ビュー

Windows アプリには、 **イマーシブビュー** と **2d ビュー** の2種類のビューを含めることができます。 アプリでは、さまざまなイマーシブビューと2D ビューを切り替えることができます。モニター上の2D ビューは、ウィンドウとして、またはヘッドセットにスレートとして表示されます。 少なくとも1つのイマーシブビューを持つアプリは、 **mixed reality アプリ** として分類されます。 イマーシブ ビューを持たないアプリは、**2D アプリ** です。

## <a name="immersive-views"></a>イマーシブビュー

アプリでイマーシブ ビューを使用すると、ユーザーの周囲にホログラムを作成したり、ユーザーを仮想環境に没入させたりすることができます。 アプリがイマーシブビューで描画されている場合、複数のアプリからのホログラムが同時に描画されることはありません &mdash; 。 アプリがユーザーのヘッド移動に合わせてシーンを [レンダリング](../develop/platform-capabilities-and-apis/rendering.md) するパースペクティブを継続的に調整することにより、アプリは [世界中にロック](coordinate-systems.md) されたホログラムをレンダリングできます。 世界中にロックされているホログラムは、現実世界の一定の位置にとどまります。また、ユーザーが移動したときの位置を保持する仮想環境をレンダリングすることもできます。

![イマーシブビューでは、ホログラムを世界中に配置できます。](images/designoverview-940px.jpg)<br>
*イマーシブビューでは、ホログラムを世界中に配置できます。*

[HoloLens](/hololens/hololens1-hardware)では、アプリはユーザーの実際の環境の上にホログラムをレンダリングします。 [Windows Mixed Reality のイマーシブヘッドセット](../discover/immersive-headset-hardware-details.md)では、ユーザーは実際の世界を見ることができないため、ユーザーに表示されるすべてのものをアプリでレンダリングする必要があります。

[Windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md)(環境の周囲に配置した [スタート] メニューとホログラムを含む) は、イマーシブビューではレンダリングされません。 HoloLens では、Cortana は、イマーシブビューの表示中に発生したすべてのシステム通知をリレーし、ユーザーが音声入力を使用して応答できるようにします。

イマーシブビューでは、すべての入力を処理することもアプリに任されています。 Windows Mixed Reality での入力は、 [宝石](gaze-and-commit.md)、 [ジェスチャ](gaze-and-commit.md#composite-gestures) (HoloLens のみ)、[音声、および [モーションコントローラー](motion-controllers.md) (イマーシブヘッドセットのみ) で構成されています。

## <a name="2d-views"></a>2D ビュー

![Windows Mixed Reality ホームの周囲にレイアウトされた複数の2D ビュー](images/teleportation-940px.png)<br>
*Windows Mixed Reality ホームの周囲に2D ビューが配置された複数のアプリ*

2D ビューを使用するアプリは、 [Windows Mixed Reality ホーム](../discover/navigating-the-windows-mixed-reality-home.md) ("シェル" とも呼ばれます) に仮想スレートとして表示されます。これは、アプリランチャーと、ユーザーが世界中に配置したその他のホログラムと共にレンダリングされます。 ユーザーは、このスレートを調整してサイズを変更できます。ただし、サイズは固定された解像度のままです。 アプリの最初のビューが2D ビューの場合、2D コンテンツはアプリを起動するために使用されるものと同じスレートに収まるようになります。

デスクトップヘッドセットでは、現在デスクトップモニター上で実行されている任意のユニバーサル Windows プラットフォーム (UWP) アプリを実行できます。 これらのアプリは既に2D ビューをレンダリングしており、そのコンテンツは、起動時にユーザーの世界のスレートに自動的に表示されます。 2D UWP アプリは、デスクトップヘッドセットと HoloLens on スレートの両方で動作するように **Windows ユニバーサル** デバイスファミリをターゲットにすることができます。

2D ビューの1つの主な用途は、システムキーボードを使用するテキスト入力フォームを表示することです。 シェルは、イマーシブビューの上にレンダリングできないため、アプリケーションは、システムキーボードを表示するために2D ビューに切り替える必要があります。 テキスト入力を受け入れるアプリでは、テキストボックスを使用して2D ビューに切り替える必要があります。 このテキストボックスにフォーカスがあるときは、システムキーボードが表示され、ユーザーはテキストを入力できます。

アプリでは、デスクトップモニターと、デスクトップ PC の接続ヘッドセットの両方に2D ビューを含めることができます。 たとえば、メインの2D ビューを使用してデスクトップモニターのエッジを参照し、360度のビデオを見つけることができます。 このビデオを再生すると、Edge は、ヘッドセット内の2次的なイマーシブビューを起動して、イマーシブビデオコンテンツを表示します。

## <a name="see-also"></a>関連項目

* [アプリ モデル](app-model.md)
* [複合現実の 2D UWP アプリを更新する](../develop/porting-apps/building-2d-apps.md)
* [HolographicSpace を入手する](../develop/native/getting-a-holographicspace.md)
* [Windows Mixed Reality ホームのナビゲーション](../discover/navigating-the-windows-mixed-reality-home.md)
* [複合現実アプリの種類](types-of-mixed-reality-apps.md)