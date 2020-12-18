---
title: 1. はじめに
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用してチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 1
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, はじめに, mrtk, uxt, UX ツール, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 71a3edbc00c315ca68ac56985c54faee2492d74d
ms.sourcegitcommit: 87b54c75044f433cfadda68ca71c1165608e2f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97010530"
---
# <a name="1-getting-started"></a>1.はじめに

Mixed Reality を初めて使用する場合でも、経験豊富なプロの方でも、ここは [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) と [Unreal Engine](https://www.unrealengine.com/en-US/) の体験を始めるのに適した場所です。 このチュートリアル シリーズでは、[Unreal 用 Mixed Reality ツールキット](https://github.com/microsoft/MixedRealityToolkit-Unreal)の一部である [UX Tools プラグイン](https://github.com/microsoft/MixedReality-UXTools-Unreal)を使用してインタラクティブなチェス アプリを構築する方法を、1 ステップずつ説明します。 プラグインは、コード、ブループリント、例を使用してプロジェクトに一般的な UX 機能を追加するのに役立ちます。 

![ビューポートの終わりのシーン](images/unreal-uxt/5-endscene.PNG)

シリーズが完了するまでに、次のことを体験できます。
* 新しいプロジェクトの開始
* Mixed Reality 用の設定
* ユーザー入力の操作
* ボタンの追加
* エミュレーターまたはデバイスでの再生

## <a name="prerequisites"></a>必須コンポーネント

開始する前に、次のものがインストールされていることを確認してください。
* Windows 10 1809 以降
* Windows 10 SDK 10.0.18362.0 以降
* [Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 以降
* [開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) Microsoft HoloLens 2 デバイスまたは[エミュレーター](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)
* 以下のワークロードを含む Visual Studio 2019

### <a name="installing-visual-studio-2019"></a>Visual Studio 2019 のインストール

最初に、必要な Visual Studio パッケージがすべてセットアップされていることを確認します。
1. [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) の最新バージョンのインストール
1. 次の[ワークロード](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads)をインストールします。
    * C++ によるデスクトップ開発
    * .NET デスクトップ開発
    * ユニバーサル Windows プラットフォームの開発
1. ユニバーサル Windows プラットフォームの開発を展開し、以下を選択します。 
    * USB デバイスの接続
    * C++ (v142) ユニバーサル Windows プラットフォーム ツール

1. 次の[コンポーネント](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components)をインストールします。
    * コンパイラ、ビルド ツール、ランタイム > MSVC v142 - VS 2019 C++ ARM64 ビルド ツール (最新バージョン)

次の図を使用して、インストールを確認します。

![VS インストーラーでの重要なティック](images/unreal-uxt/1-install-the-tools.png)

以上で作業は終了です。 これで、チェス プロジェクトを開始するためのすべての設定が完了しました。

[次のセクション: 2.プロジェクトと最初のアプリケーションの初期化](unreal-uxt-ch2.md)