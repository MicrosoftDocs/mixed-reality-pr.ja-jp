---
title: Unreal 開発の概要
description: 精選されたチェックポイント体験を通して、Unreal Engine 4 を使用した HoloLens および VR 向けの Mixed Reality の開発を始めます。
author: hferrone
ms.author: v-hferrone
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, ストリーミング, リモート処理, Mixed Reality, 開発, 入門, 機能, 新しいプロジェクト, エミュレーター, ドキュメント, ガイド, 特徴, ホログラム, ゲームの開発, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, OpenXR
ms.openlocfilehash: 99540b9cd3473097896d847943b9736300000305
ms.sourcegitcommit: 1304f8f0a838290c1ae3db34670b67c75ea9bdaa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/02/2021
ms.locfileid: "99421421"
---
# <a name="unreal-development-overview"></a>Unreal 開発の概要

![Unreal のバナー ロゴ](../images/unreal_logo_banner.png)

<a href="https://docs.microsoft.com/windows/mixed-reality" target="_blank" title="Mixed Reality Docs"> Mixed Reality アプリケーション</a>を使い始めるのは大きなタスクです。 新しい概念、プラットフォーム、最先端のハードウェアは、障壁のように見えるかもしれません。 ただし、Unreal 開発者であれば、ラッキーです。 Unreal Engine 4 により、<a href="https://www.microsoft.com/windows/windows-mixed-reality" target="_blank" title=" Windows Mixed Reality のドキュメント">Windows Mixed Reality </a> (VR) および <a href="https://www.microsoft.com/hololens/hardware" target="_blank" title="HoloLens 2 のドキュメント">HoloLens 2</a> (AR) デバイスが、完全にサポートされるようになりました。

[!INCLUDE[](includes/tabs-unreal-features.md)]

Unreal 開発が初めての場合は、よくわからないまま開始しないでください。 Unreal の<a href="https://docs.unrealengine.com/GettingStarted/index.html" target="_blank">チュートリアル シリーズ</a>を参照し、Unreal の<a href="https://www.unrealengine.com/marketplace/store" target="_blank">マーケットプレース</a>で資産を探してください。 また、Mixed Reality の<a href="https://forums.unrealengine.com/development-discussion/vr-ar-development" target="_blank">フォーラム</a>でサポートを探すこともできます。 これらのリソースは、今日の Mixed Reality 市場におけるビルダーや問題ソルバーのコミュニティへのリンクです。

> [!IMPORTANT]
> Reverb G2 などのイマーシブ ヘッドセットに移植する必要がある既存の Unreal プロジェクトがある場合は、 **[移植に関するガイド](unreal-reverb-g2-controllers.md)** を参照してください。

## <a name="development-checkpoints"></a>開発チェックポイント

次のチェックポイントを使用して、Unreal のゲームやアプリケーションを Mixed Reality の世界に移植することができます。 [Holograms サンプル アプリケーションのデザイン](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd)を調べていない場合、それをダウンロードして、Mixed Reality UX の基礎をよく理解しておくことをお勧めします。

### <a name="1-getting-started"></a>1.はじめに

まず、HoloLens 2 開発用のツールをインストールする必要があります。 次に、チュートリアル シリーズに目を通し、Mixed Reality Toolkit、Mixed Reality アプリ用に適切に構成された開発環境、Unreal で実際に動作する MRTK プロジェクトについて、基本的な理解を得ます。 Unreal 4.26 を使用すると、HoloLens 2 用の OpenXR アプリを開発することもできます。

|  Checkpoint  |  結果  |
| --- | --- |
| [最新のツールをインストールする](../install-the-tools.md) | 最新のバージョンの Unreal Engine をダウンロードしてインストールし、Mixed Reality 用のプロジェクトをセットアップできます |
| [初めての HoloLens Unreal アプリケーションの作成](unreal-quickstart.md) | 基本的な Mixed Reality アプリケーションを構築して、Unreal と HoloLens の開発体験を始めます |
| [HoloLens 2 チュートリアル シリーズ](tutorials/unreal-uxt-ch1.md) | Unreal での Mixed Reality 開発の準備を整え、MRTK を使用して最初のアプリを作成し、HoloLens 2 にアプリをデプロイします |
| (オプション) Unreal での [OpenXR](../native/openxr.md) の使用を開始します | Unreal で OpenXR アプリを構築する場合は、次のエンジン プラグインを無効にする必要があります。<ul><li>Windows Mixed Reality</li></ul><br>GitHub から次のプラグインをダウンロードし、プロジェクトで有効にします。<ul><li> [Microsoft OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal)</li></ul><br>OpenXR で現在サポートされている機能の完全な一覧については、[後述](#supported-features)します。|

### <a name="2-core-building-blocks"></a>2. コア構成要素

チュートリアル シリーズでは取り上げられていない Mixed Reality の主要な機能がいくつかあります。 これらの構成要素は、スタンドアロンの機能として利用することも、Mixed Reality Toolkit を介して利用することもできます。 そのすべてが一度に必要になるわけではありませんが、事前に確認することをお勧めします。 以下のコア構成要素について確認したら、Mixed Reality プロジェクトに統合できるさまざまな機能が用意されたツールボックスを使用できるようになります。

[Unreal 用 Mixed Reality ツールキット](https://github.com/microsoft/MixedRealityToolkit-Unreal)は、Unreal での開発を高速化するために設計されたプラグインのセットです。 各プラグインには、イマーシブ エクスペリエンスをセットアップするためのコンポーネント、サンプル、ドキュメントが含まれています。

* [Unreal 用 UX Tools](https://www.unrealengine.com/marketplace/en-US/product/mixed-reality-ux-tools) はリリースされる最初のプラグインあり、現在 HoloLens 2 でのみサポートされています。 このプラグインには、入力シミュレーション、ハンド インタラクション、表面吸着などの一般的な UX 機能の C++ コード、ブループリント、サンプル資産が含まれています。

* [Unreal 用 Graphics Tools](https://github.com/microsoft/MixedReality-GraphicsTools-Unreal/) は、パフォーマンス バジェットを維持しながら Mixed Reality アプリケーションの視覚的な忠実性を向上させるために作成されたコード、ブループリント、サンプルの資産が含まれる、UE ゲーム プラグインです。

[!INCLUDE[](../includes/unreal-building-blocks.md)]

> [!NOTE]
> 詳細については、 **[Unreal GitHub リポジトリの UX ツール](https://github.com/microsoft/MixedReality-UXTools-Unreal)** をご確認ください。

### <a name="3-advanced-features"></a>3.高度な機能

Mixed Reality アプリケーションで何らかの役割を果たすその他の主要な機能は、追加のパッケージやセットアップなしで利用できます。 これらの機能は、MRTK がインストールされているかいないかに関係なく、Unreal プロジェクトに追加できます。 これらの高度な機能について確認したら、より複雑な Mixed Reality アプリを構築できるようになります。

|  機能  |  機能  |
| --- | --- |
| [HoloLens カメラ](unreal-hololens-camera.md) | HoloLens デバイスで実行されているアプリから、Mixed Reality と現実世界のビジュアル コンテンツをキャプチャします |
| [QR コード](unreal-qr-codes.md) | 各コードの実際の位置の座標系を使用して、QR コードをホログラムとしてレンダリングします |
| [WinRT](unreal-winrt.md) | Unreal のビルド システムで使用できる WinRT コードを使って、個別のバイナリを作成します |

### <a name="4-streaming-and-deploying-to-a-device"></a>4。デバイスへのストリーミングと配置

まだ開発している間に HoloLens デバイスでアプリケーションをテストしたい場合は、Unreal エディターまたはパッケージ化された Windows 実行可能ファイルを使用して、[PC から直接ストリーミングする](unreal-streaming.md)ことができます。

HoloLens 2 に Unreal アプリを初めて配置する場合は、Epic Launcher から[サポート ファイルをダウンロードする](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)必要があります。 これらのファイルをインストールしたら、[Unreal エディター](unreal-deploying.md)または[デバイス ポータル](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)からデプロイする準備が整います。

### <a name="5-adding-services"></a>5。サービスの追加

開発作業のこの時点で、商用の配置に関してサービスの追加や手助けが必要になることがあります。 [Azure Cloud Services](../mixed-reality-cloud-services.md) と Dynamics 365 の機能を統合することで、プロジェクトを大幅にレベルアップできます。 Microsoft では、お客様が Mixed Reality に関する知識を深化、拡充できるように、いくつかの開始点をまとめています。

[!INCLUDE[](../includes/unreal-cloud-services-d365.md)]

## <a name="whats-next"></a>次の操作

開発者の仕事に終わりはありません。新しいツールや SDK について学ぶ場合は特にこれが当てはまります。 以降のセクションでは、既に終えた初級レベルの教材からは一歩進んだ領域について説明します。また、行き詰まった場合に役に立つリソースも紹介します。 これらのトピックとリソースは順番に並んでいるわけではないため、お好きなところから自由に参照することができます。

### <a name="debugging"></a>デバッグ

Visual Studio を使用してデバイスで実行しながらアプリケーションをデバッグする場合は、こちらの[手順](/visualstudio/debugger/debug-installed-app-package#remote)にしたがってください。

### <a name="performance"></a>[パフォーマンス]

Mixed Reality 向けの開発には、プラットフォームに依存するパフォーマンス チェックポイントが含まれます。 安定した応答性の高いホログラムを表示するには、HoloLens 2 アプリを 1 秒あたり 60 フレームで実行する必要があります。 さいわい、Unreal アプリケーションでパフォーマンスをアップグレードするための[パフォーマンスに関する推奨事項](performance-recommendations-for-unreal.md)が用意されています。

## <a name="supported-features"></a>サポートされている機能

| HoloLens 2 の機能 | サポートする最も古い Unreal Engine のバージョン | OpenXR でのサポート (4.26) |
| ----------- | ----------- | ----------- |
| ARM64 のサポート | 4.23 | ✔️ |
| PC からのストリーミング | 4.23 | ✔️ |
| 空間マッピング | 4.23 | ✔️ |
| 手と関節の追跡 | 4.23 | ✔️ |
| 視線追跡 | 4.23 | ✔️ |
| 音声入力 | 4.23 | ✔️ |
| 空間アンカー | 4.23 | ✔️ |
| カメラへのアクセス | 4.23 |
| QR コード | 4.23 | ✔️ |
| 空間オーディオ | 4.23 | ✔️ |
| ストリーミング用の観戦スクリーンのサポート | 4.24 |
| ストリーミングに対する Planar LSR | 4.24 |
| [サンプル アプリ](../features-and-samples.md) | 4.24 | ✔️ |
| モバイル マルチビュー: パフォーマンス ヒット 60 fps | 4.25 | ✔️ |
| 3 番目のカメラのレンダリング | 4.25 |
| パッケージ化されたデスクトップ アプリからのストリーミング | 4.25.1 | ✔️ |
| Azure Spatial Anchors for HoloLens 2 (ベータ版) | 4.25 |
| Mixed Reality UX Tools のサポート | 4.25 | ✔️ |
| 開発者向けドキュメントおよびチュートリアル | 4.25 | ✔️ |
| システム キーボード | 4.26 | ✔️ |
| HoloLens Media Player プラグイン | 4.26 | ✔️ |
| iOS および Android 用の Azure Spatial Anchors (ベータ) | 4.26 |
| Microsoft ベンダー固有の OpenXR 拡張機能を備えた Microsoft OpenXR プラグイン | 4.26 | ✔️ |
| Azure から HoloLens 2 へのストリーミング | 4.26 | ✔️ |
| パッケージ アプリの Windows アプリ認定キット コンプライアンス | 4.26 | ✔️ |
| HP Reverb G2 コントローラーのサポート | 4.26 | ✔️ |

> [!div class="nextstepaction"]
> [ツールのインストール](../install-the-tools.md)

## <a name="see-also"></a>関連項目
* <a href="https://docs.unrealengine.com/Platforms/AR/HoloLens2/index.html" target="_blank">ストリーミング、エミュレーターとデバイスへのデプロイに関する Unreal ドキュメント</a>
* <a href="https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html" target="_blank">モバイル デバイスのパフォーマンス ガイドライン (Unreal)</a>