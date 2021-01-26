---
title: Unreal での QR コード
description: Unreal Mixed Reality アプリケーションで QR コードを設定、使用、追跡する方法について説明します。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, QR コード, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: d9f23bacf31b310da6d49e74de2153b50e642c7d
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582666"
---
# <a name="qr-codes-in-unreal"></a>Unreal での QR コード

HoloLens 2 を使用すると、Web カメラを使用してワールド空間の QR コードを表示できます。それらは、各コードの実際の位置にホログラムとしてレンダリングされます。 HoloLens 2 の場合、複数のデバイスの同じ場所にホログラムをレンダリングして、共有エクスペリエンスを作成することもできます。 アプリケーションに QR コードを追加するためのベスト プラクティスに従っていることを確認してください。

- サイレント ゾーン
- 照明と背景
- サイズ、距離、および角度の位置

QR コードがアプリに配置されている場合、[環境への配慮](/hololens/hololens-environment-considerations)に特に注意してください。 これらの各トピックの詳細と、必要な NuGet パッケージをダウンロードする方法の手順については、メインの [QR コードの追跡](../platform-capabilities-and-apis/qr-code-tracking.md)ドキュメントをご覧ください。

> [!CAUTION]
> QR コードは、HoloLens で何も設定せずに追跡できる唯一の画像の種類です。Unreal の **UARTrackedImage** モジュールは、HoloLens ではサポートされていません。 カスタム画像を追跡する必要がある場合は、デバイスの [Web カメラ](unreal-hololens-camera.md)にアクセスし、サードパーティ製の画像認識ライブラリを使用して画像を処理することができます。 

## <a name="enabling-qr-detection"></a>QR 検出の有効化

HoloLens 2 で QR コードを表示するには Web カメラを使用する必要があるため、プロジェクトの設定で有効にする必要があります。
- **[Edit]\(編集\) > [Project Settings]\(プロジェクトの設定\)** を開き、 **[Platforms]\(プラットフォーム\)** セクションまでスクロールして、 **[HoloLens]** を選択します。
    + **[機能]** セクションを展開し、 **[Web カメラ]** をオンにします。  
- [ARSessionConfig アセットを追加する](/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)ことによって、QR コードの追跡をオプトインする必要もあります。

[!INCLUDE[](includes/tabs-qr-codes-1.md)]

## <a name="setting-up-a-tracked-qr-code"></a>追跡対象の QR コードの設定

QR コードは、追跡対象のイメージとして、Unreal の AR で追跡されたジオメトリ システムによって表示されます。 これを利用するには、次の操作を行う必要があります。
1. アクター ブループリントを作成し、**ARTrackableNotify** コンポーネントを追加します。

![QR の AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. **ARTrackableNotify** を選択し、 **[詳細]** パネルの **[イベント]** セクションを展開します。

![QR のイベント](images/unreal-spatialmapping-events.PNG)

3. **[On Add Tracked Geometry]** の横にある **+** をクリックして、ノードをイベント グラフに追加します。
    - イベントの完全な一覧については、[UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) コンポーネント API を参照してください。

![[On Add Tracked Geometry] にノードを追加する](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-qr-code"></a>追跡対象の QR コードの使用

次の画像のイベント グラフは、QR コードの中心にポイントをレンダリングし、そのデータを出力するために使用される **OnUpdateTrackedImage** イベントを示しています。

[!INCLUDE[](includes/tabs-qr-codes-2.md)]

流れについて説明します。
1. 最初に、追跡したイメージが **ARTrackedQRCode** にキャストされ、現在の更新されたイメージが QR コードであることを確認します。  
2. エンコードされたデータは **QRCode** 変数から取得されます。 **GetLocalToWorldTransform** の位置と **GetEstimateSize** のディメンションから QR コードの左上を取得できます。

また、コードで [QR コードの座標系を取得する](/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)こともできます。

## <a name="finding-the-unique-id"></a>一意の ID の検索

すべての QR コードには、一意の GUID ID があります。これは、次の方法で見つけることができます。
- **As ARTracked QRCode** ピンをドラッグ アンド ドロップして、**Get Unique ID** を検索します。

![QR の GUID](images/unreal-qr-guid.PNG)

QR コードを使用してバックグラウンドで多くの処理が行われているため、これで終わりというわけではありません。 内部的な処理の詳細については、次のリンクを確認してください。

## <a name="next-development-checkpoint"></a>次の開発チェックポイント

私たちが用意した Unreal 開発チェックポイント体験に従っている場合、読者は Mixed Reality プラットフォームの機能と API を探索している段階にいます。 ここから、次のトピックに進むことができます。

> [!div class="nextstepaction"]
> [WinRT](unreal-winRT.md)

または、デバイスまたはエミュレーターへのアプリの配置操作に直接移動します。

> [!div class="nextstepaction"]
> [デバイスへの配置](unreal-deploying.md)

いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#3-advanced-features)に戻ることができます。

## <a name="see-also"></a>関連項目
* [空間マッピング](../../design/spatial-mapping.md)
* [ホログラム](../../discover/hologram.md)
* [座標系](../../design/coordinate-systems.md)