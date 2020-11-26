---
title: Unreal での QR コード
description: Unreal で QR コードを使用するためのガイド
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, 機能, ドキュメント, ガイド, ホログラム, QR コード, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 68edfdd0dd77b1d00ceeb9c50202abd5d94b95f3
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678891"
---
# <a name="qr-codes-in-unreal"></a>Unreal での QR コード

## <a name="overview"></a>概要

HoloLens 2 では、Web カメラを使用してワールド空間の QR コードを表示できます。これにより、各コードの実際の位置の座標系を使用して、QR コードをホログラムとしてレンダリングします。  HoloLens 2 は、単一の QR コードに加えて、複数のデバイスの同じ場所にホログラムをレンダリングして、エクスペリエンスを共有することもできます。 アプリケーションに QR コードを追加するためのベスト プラクティスに従っていることを確認してください。

- サイレント ゾーン
- 照明と背景
- サイズ、距離、および角度の位置

QR コードがアプリに配置されている場合、[環境への配慮](../../environment-considerations-for-hololens.md)に特に注意してください。 これらの各トピックの詳細と、必要な NuGet パッケージをダウンロードする方法の手順については、メインの [QR コードの追跡](../platform-capabilities-and-apis/qr-code-tracking.md)ドキュメントをご覧ください。

## <a name="enabling-qr-detection"></a>QR 検出の有効化
HoloLens 2 で QR コードを表示するには Web カメラを使用する必要があるため、プロジェクトの設定で有効にする必要があります。
- **[編集] > [プロジェクトの設定]** を開いて、 **[プラットフォーム]** セクションまでスクロールし、 **[HoloLens]** をクリックします。
    + **[機能]** セクションを展開し、 **[Web カメラ]** をオンにします。  

[ARSessionConfig アセットを追加する](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset)ことによって、QR コードの追跡をオプトインする必要もあります。

使用する前に、`UHoloLensARFunctionLibrary::StartCameraCapture()` を呼び出して、追跡を手動で有効にする必要があります。 QR コードの追跡を終了したら、デバイス リソースを保存するために、`UHoloLensARFunctionLibrary::StopCameraCapture()` で追跡を無効にする必要があります。

## <a name="setting-up-a-tracked-image"></a>追跡対象のイメージの設定

QR コードは、追跡対象のイメージとして、Unreal の AR で追跡されたジオメトリ システムによって表示されます。 これを利用するには、次の操作を行う必要があります。
1. ブループリントを作成し、**ARTrackableNotify** コンポーネントを追加します。

![QR の AR Trackable Notify](images/unreal-spatialmapping-artrackablenotify.PNG)

2. **ARTrackableNotify** を選択し、 **[詳細]** パネルの **[イベント]** セクションを展開します。

![QR のイベント](images/unreal-spatialmapping-events.PNG)

3. **[On Add Tracked Geometry]** の横にある **+** をクリックして、ノードをイベント グラフに追加します。
    - イベントの完全な一覧については、[UARTrackableNotify](https://docs.unrealengine.com/API/Runtime/AugmentedReality/UARTrackableNotifyComponent/index.html) コンポーネント API を参照してください。

![[On Add Tracked Geometry] にノードを追加する](images/unreal-qr-codes-tracked-geometry.png)

## <a name="using-a-tracked-image"></a>追跡対象のイメージの使用
次の画像のイベント グラフは、QR コードの中心にポイントをレンダリングし、そのデータを出力するために使用される **OnUpdateTrackedImage** イベントを示しています。

![QR のレンダリングの例](images/unreal-qr-render.PNG)

流れについて説明します。
1. 最初に、追跡したイメージが **ARTrackedQRCode** にキャストされ、現在の更新されたイメージが QR コードであることを確認します。  
2. エンコードされたデータは **QRCode** 変数から取得されます。 **GetLocalToWorldTransform** の位置と **GetEstimateSize** のディメンションから QR コードの左上を取得できます。

また、コードで [QR コードの座標系を取得する](https://docs.microsoft.com/windows/mixed-reality/qr-code-tracking#getting-the-coordinate-system-for-a-qr-code)こともできます。

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

いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#3-platform-capabilities-and-apis)に戻ることができます。

## <a name="see-also"></a>関連項目
* [空間マッピング](../../design/spatial-mapping.md)
* [ホログラム](../../discover/hologram.md)
* [座標系](../../design/coordinate-systems.md)
