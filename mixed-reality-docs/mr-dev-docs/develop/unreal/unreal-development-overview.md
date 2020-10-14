---
title: Unreal 開発の概要
description: Unreal Engine 4 を使用した Mixed Reality の開発の概要
author: hferrone
ms.author: v-hferrone
ms.date: 08/04/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, ストリーミング, リモート処理, Mixed Reality, 開発, 入門, 機能, 新しいプロジェクト, エミュレーター, ドキュメント, ガイド, 特徴, ホログラム, ゲームの開発
ms.openlocfilehash: 3b5dc5d0ce1510405960c6effd653acc9c2588b2
ms.sourcegitcommit: 9ab467e36d7d9fad51b0e93a56038a6421a7b09d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/13/2020
ms.locfileid: "91980343"
---
# <a name="unreal-development-overview"></a>Unreal 開発の概要

![Unreal のバナー ロゴ](../images/unreal_logo_banner.png)

<a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="Mixed Reality Docs"> Mixed Reality アプリケーション</a>を使い始めるのは大きなタスクです。 新しい概念、プラットフォーム、最先端のハードウェアは、障壁のように見えるかもしれません。 ただし、Unreal 開発者であれば、ラッキーです。 <a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title=" Windows Mixed Reality のドキュメント">Windows Mixed Reality </a> (VR) および <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="HoloLens 2 のドキュメント">HoloLens 2</a> (AR) のサポートが、Unreal Engine の最新の <a href="https://docs.unrealengine.com/Support/Builds/ReleaseNotes/4_25/index.html" target="_blank" title="Unreal Engine 4.25 リリース ノート">リリース</a>に含まれるようになりました。 この更新には、次が含まれます。
* Mixed Reality UX Tools プラグインのサポート
* OpenXR のサポート
* デスクトップ アプリからのアプリのリモート処理
* パフォーマンスの向上
* 複合現実キャプチャ
* Azure Spatial Anchors の初期サポート

Unreal 開発が初めての場合は、よくわからないまま開始しないでください。 Unreal の<a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">チュートリアル シリーズ</a>を調べて、Unreal の<a href="https://www.unrealengine.com/marketplace/store" target="_blank">マーケットプレイス</a>と Mixed Reality <a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">フォーラム</a>のアセットとサポートをすばやく理解してください。 これらのリソースは、今日の Mixed Reality 市場におけるビルダーや問題ソルバーのコミュニティへのリンクです。

## <a name="development-checkpoints"></a>開発チェックポイント

次のチェックポイントを使用して、Unreal のゲームやアプリケーションを Mixed Reality の世界に移植することができます。 [Holograms サンプル アプリのデザイン](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) をまだご確認いただいていない場合、それをダウンロードおよび使用して、Mixed Reality UX の基礎を理解しておくことをお勧めします。

### <a name="1-getting-started"></a>1.はじめに

[Unreal 用 Mixed Reality ツールキット](https://github.com/microsoft/MixedRealityToolkit-Unreal)は、Unreal での開発を高速化するために設計されたコンポーネントのセットです。 各コンポーネントには、イマーシブ エクスペリエンスをセットアップするためのプラグイン、サンプル、およびドキュメントが含まれています。

* [Unreal 用 UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) はリリースされる最初のコンポーネントであり、現在 HoloLens 2 でのみサポートされています。 コンポーネント プラグインには、入力シミュレーション、ハンド インタラクション アクター、押しボタン コンポーネント、マニピュレーター コンポーネント、動作追従コンポーネントに対応した一般的な UX 機能のコード、ブループリント、サンプル資産が含まれています。

このセクションの最後まで進めば、Mixed Reality Toolkit、Mixed Reality アプリ用に適切に構成された開発環境、Unreal で実際に動作する MRTK プロジェクトについて、基本的な理解を得ることができます。

|  Checkpoint  |  結果  |
| --- | --- |
| [最新のツールをインストールする](../install-the-tools.md) | 最新の Unity パッケージをダウンロードしてインストールし、Mixed Reality 用のプロジェクトをセットアップできます |
| [HoloLens 2 チュートリアル シリーズ](tutorials/unreal-uxt-ch1.md) | HoloLens 2 ハードウェア向けの初級レベルの MRTK チュートリアルを確認できます |

### <a name="2-core-building-blocks"></a>2. コア構成要素

このチュートリアル シリーズで取り上げられていない Mixed Reality 開発の主要な機能がいくつかあります。 これらの構成要素は、スタンドアロンの機能として利用することも、Mixed Reality Toolkit を介して利用することもできます。 そのすべてが一度に必要になるわけではありませんが、事前に確認することをお勧めします。 以下のコア構成要素について確認したら、Mixed Reality プロジェクトに統合できるさまざまな機能が用意されたツールボックスを使用できるようになります。

[!INCLUDE[](../includes/unreal-building-blocks.md)]

> [!NOTE]
> 詳細については、 **[Unreal GitHub リポジトリの UX ツール](https://github.com/microsoft/MixedReality-UXTools-Unreal)** をご確認ください。

### <a name="3-platform-capabilities-and-apis"></a>3.プラットフォームの機能と API

Mixed Reality アプリケーションで何らかの役割を果たすその他の主要な機能は、追加のパッケージやセットアップなしで利用できます。 これらの機能は、MRTK がインストールされているかいないかに関係なく、Unreal プロジェクトに追加できます。 これらの高度な機能について確認したら、より複雑な Mixed Reality アプリを構築できるようになります。

|  機能  |  機能  |
| --- | --- |
| [HoloLens カメラ](unreal-hololens-camera.md) | HoloLens デバイスで実行されているアプリから、Mixed Reality と現実世界のビジュアル コンテンツをキャプチャします |
| [QR コード](unreal-qr-codes.md) | 各コードの実際の位置の座標系を使用して、QR コードをホログラムとしてレンダリングします |
| [WinRT](unreal-winrt.md) | Unreal のビルド システムで使用できる WinRT コードを使って、個別のバイナリを作成します |

### <a name="4-deploying-to-a-device"></a>4.デバイスへのデプロイ

HoloLens 用の Unreal アプリを初めて作成またはデプロイする場合は、Epic Launcher から[サポート ファイルをダウンロードする](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)必要があります。 これらのファイルをインストールしたら、[Unreal エディター](unreal-deploying.md)または[デバイス ポータル](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)からデプロイする準備が整います。

### <a name="5-adding-services"></a>5。サービスの追加

開発作業のこの時点で、サービスを追加する必要が生じたり、商用環境でのデプロイへの手助けが必要になったりすることがあります。 [Azure Cloud Services](../mixed-reality-cloud-services.md) と Dynamics 365 の機能を統合することで、プロジェクトを大幅にレベルアップできます。 Microsoft では、お客様が Mixed Reality に関する知識を深化、拡充できるように、いくつかの開始点をまとめています。

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

## <a name="whats-next"></a>次の操作

開発者の仕事に終わりはありません。新しいツールや SDK について学ぶ場合は特にこれが当てはまります。 以降のセクションでは、既に終えた初級レベルの教材からは一歩進んだ領域について説明します。また、行き詰まった場合に役に立つリソースも紹介します。 これらのトピックとリソースは順番に並んでいるわけではないため、お好きなところから自由に参照することができます。

### <a name="streaming--debugging"></a>ストリーミングとデバッグ

開発している最中に HoloLens デバイスでアプリケーションをテストしたい場合は、Unreal エディターまたはパッケージ化された Windows 実行可能ファイルを使用して、[お使いの PC から直接ストリーム配信](unreal-streaming.md)できます。

Visual Studio を使用してアプリケーションをデバッグする場合は、こちらの[手順](https://docs.microsoft.com/visualstudio/debugger/debug-installed-app-package#remote)にしたがってください。

### <a name="performance"></a>[パフォーマンス]

Mixed Reality 向けの開発には、プラットフォームに依存するパフォーマンス チェックポイントが含まれます。 安定した応答性の高いホログラムを表示するには、HoloLens 2 アプリを 1 秒あたり 60 フレームで実行する必要があります。 さいわい、Unreal アプリケーションでこれを実現するための[パフォーマンスの推奨事項](performance-recommendations-for-unreal.md)を提供しています。

## <a name="supported-features"></a>サポートされている機能

| HoloLens 2 の機能 | サポートする最も古い Unreal Engine のバージョン |
| ----------- | ----------- |
| ARM64 のサポート | 4.23 |
| PC からのストリーミング | 4.23 |
| 空間マッピング | 4.23 |
| 手と関節の追跡 | 4.23 |
| 視線追跡 | 4.23 |
| 音声入力 | 4.23 |
| 空間アンカー | 4.23 |
| カメラへのアクセス | 4.23 |
| QR コード | 4.23 |
| 空間オーディオ | 4.23 |
| ストリーミング用の観戦スクリーンのサポート | 4.24 |
| ストリーミングに対する Planar LSR | 4.24 |
| サンプル アプリ ([HoloLens2Example](https://github.com/microsoft/MixedReality-Unreal-Samples) および [Mission AR](https://docs.unrealengine.com/Resources/Showcases/MissionAR/index.html)) | 4.24 |
| モバイル マルチビュー: パフォーマンス ヒット 60 fps | 4.25 |
| 3 番目のカメラのレンダリング | 4.25 |
| パッケージ化されたデスクトップ アプリからのストリーミング | 4.25.1 |
| Azure Spatial Anchors for HoloLens 2 (ベータ版) | 4.25 |
| OpenXR のサポート (ベータ版) | 4.25 |
| UX Tools のサポート (0.8) | 4.25 |
| 開発者向けドキュメントおよびチュートリアル | 4.25 |

> [!div class="nextstepaction"]
> [ツールのインストール](../install-the-tools.md)

## <a name="see-also"></a>関連項目
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">ストリーミング、エミュレーターとデバイスへのデプロイに関する Unreal ドキュメント</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">モバイル デバイスのパフォーマンス ガイドライン (Unreal)</a>
