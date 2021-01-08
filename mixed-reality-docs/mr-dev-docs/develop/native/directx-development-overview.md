---
title: ネイティブ開発の概要
description: Windows Mixed Reality Api を直接使用して DirectX ベースの mixed reality エンジンを構築する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 08/04/2020
ms.topic: article
keywords: DirectX, holographic レンダリング, ネイティブ, ネイティブアプリ, WinRT, WinRT アプリ, プラットフォーム Api, カスタムエンジン, ミドルウェア, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 764cbe0a37501cc176e9bb05a9a7771b03666f0c
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006852"
---
# <a name="native-development-overview"></a>ネイティブ開発の概要

![ネイティブバナーロゴ](../images/native_logo_banner.png)

[Unity](../unity/unity-development-overview.md)や[unreal](../unreal/unreal-development-overview.md)のような3d エンジンは、自分が開いている唯一の Mixed Reality 開発パスではありません。 Windows Mixed Reality Api と DirectX 11 または DirectX 12 を使用して、Mixed Reality アプリを作成することもできます。 プラットフォームソースにアクセスすることによって、基本的に独自のミドルウェアまたはフレームワークを構築しています。 

> [!IMPORTANT]
> 管理する既存の WinRT プロジェクトがある場合は、主な [winrt ドキュメント](creating-a-holographic-directx-project.md)に進んでください。 

## <a name="development-checkpoints"></a>開発チェックポイント

次のチェックポイントを使用して、Unity のゲームやアプリケーションを Mixed Reality の世界に移植することができます。

### <a name="1-getting-started"></a>1.はじめに

Windows Mixed Reality は [、次の2種類のアプリを](../../design/app-views.md)サポートしています。
* [HOLOGRAPHICSPACE api](getting-a-holographicspace.md)または [OpenXR api](openxr.md)を使用して、ヘッドセットの表示を埋める [イマーシブビュー](../../design/app-views.md)をレンダリングする UWP または Win32 **Mixed Reality アプリケーション**
* DirectX、XAML、または別のフレームワークを使用して、Windows Mixed Reality ホームのスレートに [2d ビュー](../../design/app-views.md#2d-views)をレンダリングする **2d アプリ**(UWP)

[2d ビューとイマーシブビュー](../../design/app-views.md)の DirectX 開発の違いは、主に holographic のレンダリングと空間入力に関係しています。 UWP アプリケーションの [IFrameworkView](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.core.iframeworkview.aspx) または Win32 アプリケーションの HWND が必要であり、ほぼ同じです。 アプリで使用できる WinRT Api にも同じことが当てはまります。 ただし、holographic 機能を利用するには、これらの Api の異なるサブセットを使用する必要があります。 たとえば、holographic アプリケーションのシステムでは、発生しているスワップチェーンとフレームを管理して、予測可能なフレームループを有効にします。

[!INCLUDE[](../includes/native-getting-started.md)]

### <a name="2-core-building-blocks"></a>2. コア構成要素

Windows Mixed Reality アプリケーションは、次の Api を使用して、HoloLens とその他のイマーシブヘッドセットの [Mixed Reality](../../discover/mixed-reality.md) エクスペリエンスを構築します。

|  機能  |  説明  |
| --- | --- |
| [視線入力](../../design/gaze-and-commit.md) | ホログラムを見ることによってユーザーがホログラムを対象とすることができるようにします |
| [ジェスチャ](../../design/gaze-and-commit.md#composite-gestures) | アプリに空間アクションを追加する |
| [ホログラフィック レンダリング](../platform-capabilities-and-apis/rendering.md) | ユーザーに対して世界中の正確な場所にホログラムを描画します |
| [モーションコントローラー](../../design/motion-controllers.md) | ユーザーが Mixed Reality 環境でアクションを実行できるようにする |
| [空間マッピング](../../design/spatial-mapping.md) | 仮想メッシュ オーバーレイを使用して物理領域をマップし、環境の境界をマークします |
| [音声](../../design/voice-input.md) | ユーザーが話したキーワード、フレーズ、ディクテーションをキャプチャします |
 
> [!NOTE]
> OpenXR の [ロードマップ](openxr.md#roadmap) のドキュメントで、近日中および開発中のコア機能を確認できます。

### <a name="3-deploying-and-testing"></a>3. 配置とテスト

HoloLens 2 または Windows Mixed Reality イマーシブヘッドセットで OpenXR を使用してデスクトップで開発できます。  ヘッドセットへのアクセス権がない場合は、代わりに [HoloLens 2 エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md) または [Windows Mixed Reality シミュレーター](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md) を使用できます。

## <a name="whats-next"></a>次の操作

開発者の仕事に終わりはありません。新しいツールや SDK について学ぶ場合は特にこれが当てはまります。 次のセクションでは、既に完了している初心者レベルの資料以外の領域について説明します。 これらのトピックとリソースは順番には記載されていないため、先に進んで調査してください。

### <a name="additional-resources"></a>その他のリソース

OpenXR ゲームのレベルアップを検討している場合は、以下のリンクを確認してください。

* [OpenXR ベスト プラクティス](openxr-best-practices.md)
* [OpenXR パフォーマンス](openxr-performance.md)
* [OpenXR トラブルシューティング](openxr-troubleshooting.md)

## <a name="see-also"></a>関連項目
* [アプリ モデル](../../design/app-model.md)
* [アプリ ビュー](../../design/app-views.md)
