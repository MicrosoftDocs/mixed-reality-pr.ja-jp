---
title: VR 向けの Unity の開発
description: VR と Windows Mixed Reality イマーシブ ヘッドセットを対象とする Unity での Mixed Reality アプリの構築の概要。
author: hferrone
ms.author: kurtie
ms.date: 12/11/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unity, Mixed Reality, 開発, 作業の開始, 新しいプロジェクト, 移植, 機能, カメラ, シミュレーション, エミュレーション, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, 仮想現実とは, 拡張現実とは, MRTK, Mixed Reality Toolkit, 音声入力, 場所を特定できるカメラ, エミュレーター, Azure, チュートリアル
ms.openlocfilehash: 65b45d448854f8903ed37466ebaa3c427dea3089
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582948"
---
# <a name="unity-development-for-vr-and-windows-mixed-reality"></a>VR と Windows Mixed Reality 向けの Unity 開発

![Unity のバナー ロゴ](../images/unity_logo_banner.png)

Unity を初めて使用する場合は、続行する前に、Unity Learn プラットフォームで初級レベルの[チュートリアル](https://unity3d.com/learn/tutorials)を確認することをお勧めします。 また、[Unity Mixed Reality フォーラム](https://forum.unity3d.com/forums/hololens.102/)にアクセスして、Mixed Reality アプリを構築しているオンライン コミュニティに参加することもお勧めします。 想像を超えたすばらしい資産やソリューションを見つけることができます。 MRTK の使用を開始する準備ができたら、次の開発チェックポイントに進んでください。

> [!IMPORTANT]
> 既存の Unity プロジェクトを Windows Mixed Reality イマーシブ ヘッドセットに移植したい場合は、 **[移植ガイド](../porting-apps/porting-overview.md)** を参照してください。 

## <a name="development-checkpoints"></a>開発チェックポイント

次のチェックポイントを使用して、Unity のゲームやアプリケーションを Mixed Reality の世界に移植することができます。 

### <a name="1-getting-started"></a>1.はじめに

Unity には、Windows Mixed Reality と VR の開発用に手動で変更する必要がある小さな設定のセットがあります。 これらは、プロジェクトごととシーンごとの 2 つのカテゴリに分類されます。 このセクションが済むと、ツールとプロジェクトの設定は独自のアプリの作成を始められるようになっています。

|  Checkpoint  |  結果  |
| --- | --- |
| [最新のツールをインストールする](../install-the-tools.md) | 最新の Unity パッケージをダウンロードしてインストールし、Mixed Reality 用のプロジェクトをセットアップできます |
| [WMR 用のプロジェクトの構成](configure-unity-project.md) | ホログラフィックおよび VR ディスプレイ デバイスにデジタル コンテンツをレンダリングするアプリケーションを構築する方法について説明します |

### <a name="2-core-building-blocks"></a>2. コア構成要素

新しいイマーシブ プロジェクトを開始した後は、イマーシブ アプリを開発するための基本的な構成要素がいくつか必要になります。 Mixed Reality アプリケーションのコアな構成要素はすべて、他の Unity API と一貫した手法で公開されています。 そのすべてが一度に必要になるわけではありませんが、事前に確認することをお勧めします。 以下のコア構成要素について確認したら、VR プロジェクトに統合できるさまざまな機能が用意されたツールボックスを使用できるようになります。

[!INCLUDE[](../includes/unity-building-blocks-wmr.md)]

### <a name="3-advanced-features"></a>3.高度な機能

イマーシブ アプリケーションで役割を果たすその他の主要な機能は、Unity API を通じて利用できます。追加のパッケージやセットアップは不要です。 Unity によって提供される高度な機能について確認したら、より高度で複雑な VR アプリを構築することができるようになります。

|  機能  |  機能  |
| --- | --- |
| [追跡の損失](tracking-loss-in-unity.md) | アプリケーションのワールド空間でデバイスがそれ自体の位置を特定できなくなった場合のシナリオを処理できます |
| [キーボード入力](keyboard-input-in-unity.md) | アプリで、実際のキーボードや Mixed Reality のキーボードから入力を取得できます |

### <a name="4-deploying-to-a-device-or-emulator"></a>4.デバイスまたはエミュレーターへのデプロイ

ホログラフィック Unity プロジェクトをテストする準備ができたら、次の手順として、Unity Visual Studio ソリューションをエクスポートしてビルドします。 その VS ソリューションがあれば、実際のデバイスまたはシミュレートされたデバイスでアプリケーションを実行できます。 このセクションの最後まで進めば、開発のニーズに合ったデバイスまたはエミュレーターでアプリケーションをデプロイできるようになります。

* [Windows Mixed Reality イマーシブ ヘッドセット](../platform-capabilities-and-apis/using-visual-studio.md)
* [Windows Mixed Reality イマーシブ ヘッドセット シミュレーター](../platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)

## <a name="whats-next"></a>次の操作

開発者の仕事に終わりはありません。新しいツールや SDK について学ぶ場合は特にこれが当てはまります。 以降のセクションでは、既に終えた初級レベルの教材からは一歩進んだ領域について説明します。また、行き詰まった場合に役に立つリソースも紹介します。 これらのトピックとリソースは順番に並んでいるわけではないため、お好きなところから自由に参照することができます。

### <a name="porting"></a>移植

移植したい既存のアプリがある場合は、以下の記事を次に確認してください。

* [Windows Mixed Reality に VR アプリを移植する](../porting-apps/porting-guides.md?tabs=project)
* [Windows Mixed Reality 用に SteamVR アプリを更新する](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md)

### <a name="additional-resources"></a>その他のリソース

独自の Mixed Reality の世界に進む前に、さらに以下のドキュメントを参照することをお勧めします。 

* [VR 技術者向けガイド](/windows/mixed-reality/enthusiast-guide/vr-journey)
* [Unity 資産ストア](https://www.assetstore.unity3d.com)

## <a name="see-also"></a>関連項目 

* [Unity で推奨される設定](recommended-settings-for-unity.md)
* [Unity のパフォーマンスに関する推奨事項](performance-recommendations-for-unity.md)
* [Unity Visual Studio ソリューションのエクスポートとビルド](exporting-and-building-a-unity-visual-studio-solution.md)
* [Unity と Visual Studio を使用するためのベスト プラクティス](best-practices-for-working-with-unity-and-visual-studio.md)