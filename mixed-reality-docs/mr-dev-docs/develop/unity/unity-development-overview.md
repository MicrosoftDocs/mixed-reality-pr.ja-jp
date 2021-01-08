---
title: HoloLens 向けの Unity の開発
description: Unity と HoloLens で Mixed Reality アプリのビルドを開始します。
author: hferrone
ms.author: kurtie
ms.date: 12/9/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, Mixed Reality, 開発, 作業の開始, 新しいプロジェクト, 移植, 機能, カメラ, シミュレーション, エミュレーション, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 仮想現実とは, 拡張現実とは, MRTK, Mixed Reality Toolkit, 空間マッピング, 音声入力, 場所を特定できるカメラ, エミュレーター, Azure, チュートリアル
ms.openlocfilehash: 150d86d1522f3fa71dd9d9a1fe154baef89496e0
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97613476"
---
# <a name="unity-development-for-hololens"></a>HoloLens 向けの Unity の開発 

![Unity のバナー ロゴ](../images/unity_logo_banner.png)

[Unity](https://unity.com) で HoloLens [Mixed Reality アプリ](../../design/app-views.md)を最速で構築するには、Mixed Reality Toolkit を使用します。 Unity を初めて使用する場合は、続行する前に、Unity Learn プラットフォームで初級レベルの[チュートリアル](https://unity3d.com/learn/tutorials)を確認することをお勧めします。 また、包括的な[資産ストア](https://www.assetstore.unity3d.com/)のほか、Mixed Reality アプリを構築しているオンライン コミュニティとやり取りできる [Unity Mixed Reality フォーラム](https://forum.unity3d.com/forums/hololens.102/)にアクセスすることもお勧めします。 想像を超えたすばらしい資産やソリューションを見つけることができます。 MRTK の使用を開始する準備ができたら、次の開発チェックポイントに進んでください。

> [!IMPORTANT]
> HoloLens 2 に移植する必要がある既存の Unity プロジェクトがある場合は、Microsoft の **[移植ガイド](../porting-apps/porting-overview.md)** を参照してください。 HTK、MRTK v1、SteamVR を使用するプロジェクト向けのガイドや、Reverb G2、Oculus Rift、HTC Vive などのイマーシブ ヘッドセット用に開発されたプロジェクト向けのガイドが用意されています。

## <a name="development-checkpoints"></a>開発チェックポイント

次のチェックポイントを使用して、Unity のゲームやアプリケーションを Mixed Reality の世界に移植することができます。 [Holograms サンプル アプリのデザイン](https://www.microsoft.com/p/designing-holograms/9nxwnjklrzwd) をまだご確認いただいていない場合、それをダウンロードおよび使用して、Mixed Reality UX の基礎を理解しておくことをお勧めします。 

### <a name="1-getting-started"></a>1.はじめに
Unity で開発する場合の最も簡単な方法は、Mixed Reality Toolkit を使用することです。 MRTK は、Mixed Reality 用のプロジェクトの設定を自動化するのに役立ちます。また、開発プロセスを短縮する一連の機能が用意されています。 このセクションの最後まで進めば、Mixed Reality Toolkit、Mixed Reality アプリ用に適切に構成された開発環境、自身で構築した、Unity で実際に動作する MRTK プロジェクトについて、基本的な理解を得ることができます。

|  Checkpoint  |  結果  |
| --- | --- |
| [MSIX とは](mrtk-getting-started.md) | 作業を始めるにあたって、まず Mixed Reality Toolkit とその機能を理解できます |
| [最新のツールをインストールする](../install-the-tools.md) | 最新の Unity パッケージをダウンロードしてインストールし、Mixed Reality 用のプロジェクトをセットアップできます |
| [HoloLens 2 チュートリアル シリーズ](tutorials/mr-learning-base-01.md) | HoloLens 2 ハードウェア向けの初級レベルの MRTK チュートリアルを確認できます |

> [!IMPORTANT]
> Mixed Reality Toolkit をインポートせずに新しい Unity プロジェクトを作成する場合には、Windows Mixed Reality 用に手動で変更する必要がある小規模な Unity 設定のセットがあります。 これらは、プロジェクトごととシーンごとの 2 つのカテゴリに分類されます。 詳細な手順については、構成ガイドを参照してください。

> [!NOTE]
> プロジェクトに MRTK V2 を設定すると、標準の Unity ゲーム オブジェクト (カメラなど) が、座位のエクスペリエンスに対応してすぐに点灯します。 アプリケーションのエクスペリエンス スケールを変更する手順については、座標系に関するページを参照してください。

### <a name="2-core-building-blocks"></a>2. コア構成要素

Mixed Reality アプリケーションのコアな構成要素はすべて、他の Unity API と一貫した手法で公開されています。 これらの構成要素は、スタンドアロンの機能として利用することも、Mixed Reality Toolkit を介して利用することもできます。 そのすべてが一度に必要になるわけではありませんが、事前に確認することをお勧めします。 以下のコア構成要素について確認したら、個別に、または MRTK を介して Mixed Reality プロジェクトに統合できるさまざまな機能が用意されたツールボックスを使用できるようになります。

[!INCLUDE[](../includes/unity-building-blocks.md)]

### <a name="3-platform-capabilities-and-apis"></a>3.プラットフォームの機能と API

Mixed Reality アプリケーションで何らかの役割を果たすその他の主要な機能は、Unity API を通じて利用できます。追加のパッケージやセットアップは不要です。 これらの機能は、MRTK がインストールされているかいないかに関係なく、Unity プロジェクトに追加できます。 Unity によって提供される高度な機能について確認したら、より高度で複雑な Mixed Reality アプリを構築することができるようになります。

|  機能  |  機能  |
| --- | --- |
| [共有エクスペリエンス](shared-experiences-in-unity.md) | 空間アンカー共有を使用して、空間内の固定ポイントに同じホログラムを表示したり、まとめて操作したりできます |
| [場所を特定できるカメラ](locatable-camera-in-unity.md) | Mixed Reality アプリケーションで写真およびビデオ コンテンツをキャプチャできます |
| [フォーカス ポイント](focus-point-in-unity.md) | 現在表示されているホログラムに対して最適な安定化を施す方法に関するヒントを HoloLens に提供します |
| [追跡の損失](tracking-loss-in-unity.md) | アプリケーションのワールド空間でデバイスがそれ自体の位置を特定できなくなった場合のシナリオを処理できます |
| [キーボード入力](keyboard-input-in-unity.md) | アプリで、実際のキーボードや Mixed Reality のキーボードから入力を取得できます |

### <a name="4-deploying-to-a-device-or-emulator"></a>4.デバイスまたはエミュレーターへのデプロイ

ホログラフィック Unity プロジェクトをテストする準備ができたら、次の手順として、Unity Visual Studio ソリューションをエクスポートしてビルドします。 その VS ソリューションがあれば、実際のデバイスまたはシミュレートされたデバイスを使用して、次の 3 つの方法のいずかでアプリケーションを実行できます。 このセクションの最後まで進めば、開発のニーズに合ったデバイスまたはエミュレーターでアプリケーションをデプロイできるようになります。

* [HoloLens または Windows Mixed Reality イマーシブ ヘッドセット](../platform-capabilities-and-apis/using-visual-studio.md)
* [HoloLens エミュレーター](../platform-capabilities-and-apis/using-the-hololens-emulator.md)
* [Windows Mixed Reality イマーシブ ヘッドセット シミュレーター](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="5-adding-services"></a>5。サービスの追加

開発作業のこの時点で、サービスを追加する必要が生じたり、商用環境でのデプロイへの手助けが必要になったりすることがあります。 [Azure Cloud Services](../mixed-reality-cloud-services.md) と Dynamics 365 の機能を統合することで、プロジェクトを大幅にレベルアップできます。 Microsoft では、お客様が Mixed Reality に関する知識を深化、拡充できるように、いくつかの開始点をまとめています。

[!INCLUDE[](../includes/unity-cloud-services-d365.md)]

また、[追加の Azure サービスに関するサポート ドキュメントの包括的な一覧](../mixed-reality-cloud-services.md#standalone-unity-services)も提供しています。これらのサービスは、セルフサービス ベースでお客様の Unity プロジェクトに追加できます。

## <a name="whats-next"></a>次の操作

開発者の仕事に終わりはありません。新しいツールや SDK について学ぶ場合は特にこれが当てはまります。 以降のセクションでは、既に終えた初級レベルの教材からは一歩進んだ領域について説明します。また、行き詰まった場合に役に立つリソースも紹介します。 これらのトピックとリソースは順番に並んでいるわけではないため、お好きなところから自由に参照することができます。

### <a name="porting"></a>移植

移植したい既存のアプリがある場合は、次の記事をご確認ください。

* [HoloToolkit または MRTK から MRTK v2 へ](mrtk-porting-guide.md)
* [イマーシブ アプリの移植ガイド](../porting-apps/porting-guides.md)
* [入力移植ガイド](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

### <a name="tutorials"></a>チュートリアル

特定の Mixed Reality 機能をアプリケーションに追加する場合に、そのプロセスをエンド ツー エンドで説明している精選されたチュートリアルがいくつか用意されています。 最も人気のある HoloLens 2 および HoloLens (第 1 世代) のコンテンツを以下に示しますが、各チュートリアルの概要にアクセスするとコレクション全体を確認することができます。

[!INCLUDE[](../includes/unity-tutorials.md)]

### <a name="additional-resources"></a>その他の技術情報

独自の Mixed Reality の世界に進む前に、以下に示す MRTK 関連のドキュメントを参照することをお勧めします。 これらの記事は、MRTK の機能を詳しく理解するための出発点になると共に、アプリのパフォーマンスを向上させるための情報も掲載されています。

|  トピック  |  説明  |
| --- | --- |
| [MRTK アーキテクチャの概要](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Architecture/Overview.html) | MRTK SDK がプロジェクト内でどのように機能するかについて理解を深めます |
| [設定とパフォーマンス](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Performance/PerfGettingStarted.html) | アプリをプロファイリングし、Unity の設定を更新して、ホログラム安定化のパフォーマンスを最適化します |
| [MRTK および XR の概要](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html) | Unity によって提供される代替の XR パイプラインに転送します |

### <a name="unity-resources"></a>Unity のリソース

このドキュメントは docs.microsoft.com 上で入手できますが、Unity では、Windows Mixed Reality 機能に関するドキュメントが Unity エディターと共にインストールされます。 Unity が提供するドキュメントには、2 つのセクションが含まれます。

|  リソース  |  説明  |
| --- | --- |
| [スクリプト リファレンス](https://docs.unity3d.com/ScriptReference/) | ドキュメントのこのセクションには、Unity が提供している、Unity エディターからオンラインでアクセスできるスクリプト API の詳細が含まれています。アクセスするには、 **[ヘルプ] > [Scripting Reference]\(スクリプト参照\)** をクリックします |
| [手動](https://docs.unity3d.com/Manual/index.html) | このマニュアルは、基本的な手法から高度な手法まで、Unity の使用方法の理解に役立つように作られています。オンラインで、または Unity エディターから **[ヘルプ] > [マニュアル]** をクリックしてアクセスできます |


> [!div class="nextstepaction"]
> [MRTK の詳細](mrtk-getting-started.md)

## <a name="see-also"></a>関連項目
* [Mixed Reality Toolkit v2](mrtk-getting-started.md)
* [MR の基本 100:Unity の概要](tutorials/holograms-100.md)
* [Unity で推奨される設定](recommended-settings-for-unity.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)
* [Unity Visual Studio ソリューションのエクスポートとビルド](exporting-and-building-a-unity-visual-studio-solution.md)
* [Windows 名前空間と HoloLens 用 Unity アプリの使用](using-the-windows-namespace-with-unity-apps-for-hololens.md)
* [Unity と Visual Studio を使用するためのベスト プラクティス](best-practices-for-working-with-unity-and-visual-studio.md)
* [Unity の再生モード](unity-play-mode.md)
* [移植ガイド](../porting-apps/porting-guides.md)
