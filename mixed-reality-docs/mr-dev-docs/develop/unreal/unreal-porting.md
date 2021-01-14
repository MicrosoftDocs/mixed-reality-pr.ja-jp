---
title: Unreal でのプロジェクトのアップグレード
description: Unreal プロジェクトのためのバージョン アップグレード手順、API の変更、廃止で最新の状態に保ちます。
author: hferrone
ms.author: jacksonf
ms.date: 11/23/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, 開発, ドキュメント, ガイド, 機能, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 移植, アップグレード
ms.openlocfilehash: 27fb726bc0ca9c51b4e7b68ad28b76f89312262e
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010052"
---
# <a name="upgrading-projects-in-unreal"></a>Unreal でのプロジェクトのアップグレード

Unreal が新しいバージョンに更新されると、非推奨になった関数は、ブループリントをコンパイルするとき、またはプロジェクトをパッケージ化するときに、警告として表示されます。  関数は、代わりに使用する必要がある新しい関数が追加されると非推奨になります。 

## <a name="426-upgrades"></a>4.26 のアップグレード
 
4\.26 では、AR と VR のすべてのプラットフォームがリファクタリングされ、共通のインターフェイスが追加されて、アプリケーションのコードはプラットフォームに依存しなくなったため、通常より多くの警告が表示される可能性があります。  プロジェクトを他のプラットフォームにいっそう簡単に移植できるよう、新しい API に更新することをお勧めします。

非推奨になった関数と、代わりに使用する関数が、警告メッセージで示されます。  非推奨のすべての関数は、このリリースでは引き続き動作しますが、今後のリリースでは動作しない可能性があります。  また、非推奨の関数は、ブループリントで関数を検索したときの一覧にも表示されなくなります。

![名前付き ARPin 作成関数のブループリント](images/unreal-porting-img-01.png)

### <a name="425-deprecations"></a>4.25 で非推奨になったもの

| 非推奨になった関数 | 新しい関数 |
| --- | --- |
| CreateNamedARPin | ![ピン コンポーネント関数のブループリント](images/unreal-porting-img-02.png) |
| LoadWMRAnchorStoreARPins | ![ローカル ストアから ARPins を読み込む関数のブループリント](images/unreal-porting-img-03.png) |
| LoadWMRAnchorSaveARPinToWMRAnchorStoreStoreARPins | ![ローカル ストアに ARPin を保存する関数のブループリント](images/unreal-porting-img-04.png) |
| RemoveARPinFromWMRAnchorStore | ![ローカル ストアから ARPin を削除する関数のブループリント](images/unreal-porting-img-05.png) |
| SetEnabledMixedRealityCamera | ![有効な XRCamera を設定する関数のブループリント](images/unreal-porting-img-06.png) |
| ResizeMixedRealityCamera | ![XRCamera のサイズを変更する関数のブループリント](images/unreal-porting-img-07.png) |
| StartCameraCapture | ![カメラ キャプチャ開始のために ARCapture を切り替える関数のブループリント](images/unreal-porting-img-08.png) |
| StopCameraCapture | ![カメラ キャプチャ停止のために ARCapture を切り替える関数のブループリント](images/unreal-porting-img-09.png) |
| StartQRCodeCapture | ![QRコード キャプチャ開始のために ARCapture を切り替える関数のブループリント](images/unreal-porting-img-10.png) |
| StopQRCodeCapture | ![QRコード キャプチャ停止のために ARCapture を切り替える関数のブループリント](images/unreal-porting-img-11.png) |
| 空間マッピングは、以前の 4.25 では自動的に開始されましたが、現在の 4.26 では切り替える必要があります。 | ![空間マッピングを有効にするために ARCapture を切り替える関数のブループリント](images/unreal-porting-img-12.png) |
| ShowKeyboard | キーボードはテキスト ウィジェットにフォーカスが設定されると自動的に表示されるため、4.26 では削除されました。 |
| HideKeyboard | キーボードはテキスト ウィジェットがフォーカスを失うと自動的に非表示になるため、4.26 では削除されました。 |
| SupportsHandTracking | ![ハンド トラッキング サポート プロパティのブループリント](images/unreal-porting-img-13.png) |
| IsDisplayOpaque | ![IsDisplayOpaque プロパティのブループリント](images/unreal-porting-img-14.png) |
| GetHandJointTransform、GetPointerPoseInfo、GetControllerTrackingStatus | ![モーション コントローラーのデータを取得する関数のブループリント](images/unreal-porting-img-15.png) |
| GetVersionString | ![バージョン文字列を取得する関数のブループリント](images/unreal-porting-img-16.png) |
| IsTrackingAvailable | ![IsTrackingAvailable プロパティのブループリント](images/unreal-porting-img-17.png) |
| IsButtonClicked、IsButtonDown、IsGrasped、IsSelectPressed | Unreal の入力アクション システムを使用します。 |
| SetFocusPointForFrame | 4\.26 では削除されました。  以前はリモート処理のときの再投影に使用されていましたが、現在は深度の再投影がサポートされています。 |

## <a name="426-changes"></a>4.26 の変更点

重要な変更点は、Windows Mixed Reality プラグインを起動する場合に、 **[Edit]\(編集\) > [Project Settings]\(プロジェクトの設定\) > [Project]\(プロジェクト\) > [Description]\(説明\) > [Settings]\(設定\)** の **[Start in VR]\(VR で開始\)** が必須であることです。 このパラメーターを指定しない場合、デバイスにホログラムは表示されません。
