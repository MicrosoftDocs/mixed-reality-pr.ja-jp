---
title: ツールのインストール
description: ここでは、最新バージョンの Unity、Visual Studio、および HoloLens と VR の開発に推奨されるツールの使用を始めます。
author: thetuvix
ms.author: alexturn
ms.date: 01/13/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, ツール, はじめに, 基本, Unity, Visual Studio, ツールキット, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, インストール, Windows, HoloLens, エミュレーター, Unreal, OpenXR
ms.openlocfilehash: c45fa347768e5d35441f2c1fd59da815a80ec707
ms.sourcegitcommit: 4b6815605e2ea3830052baed38df21af354d2f9b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2021
ms.locfileid: "98166777"
---
# <a name="install-the-tools"></a>ツールのインストール

Microsoft HoloLens および Windows Mixed Reality イマーシブ (VR) ヘッドセット用のアプリケーションを構築するために必要なツールを取得します。 Windows Mixed Reality 開発用の別個の SDK はありません。Windows 10 SDK と一緒に Visual Studio をご使用ください。

Mixed Reality デバイスをお持ちでない場合はどのようにしたらよいでしょうか。 HoloLens なしで Mixed Reality アプリの機能をテストするために、[HoloLens エミュレーター](platform-capabilities-and-apis/using-the-hololens-emulator.md)をインストールすることができます。 [Windows Mixed Reality シミュレーター](platform-capabilities-and-apis/using-the-windows-mixed-reality-simulator.md)を使用して、イマーシブ ヘッドセット用の Mixed Reality アプリをテストすることもできます。 Unity を使用している場合は、[Mixed Reality Toolkit (MRTK)](https://github.com/Microsoft/MixedRealityToolkit-Unity) の入力シミュレーションを使用して、ハンドトラッキングや視線追跡入力などのさまざまな種類の入力操作をテストできます。

Mixed Reality アプリの作成を開始する最も簡単な方法として、Unity ゲーム エンジンをインストールすることをお勧めします。 ただし、カスタム エンジンを使用する場合は、DirectX に対してビルドすることもできます。

>[!TIP]
>このページをブックマークに登録して定期的にチェックし、Mixed Reality 開発に推奨される各ツールの最新バージョンを常に最新の状態に保ってください。

<br>

## <a name="installation-checklist"></a>インストールのチェックリスト


| ツール | メモ |
|---------|---------|
| ![Windows ロゴ](images/Windows10_logo.png)<br><br><a href="https://www.microsoft.com/software-download/windows10" target="_blank">**Windows 10** (手動インストールのリンク)</a><br><br>お使いの PC のオペレーティング システムが、Mixed Reality アプリケーションの構築対象プラットフォームと一致するように、Windows 10 の最新バージョンをインストールしてください。  | **Windows 10 のインストール** <br> [設定] の [Windows Update] を利用するか、インストール メディアを作成して (左の列のリンクを使用して)、Windows 10 の最新バージョンをインストールできます。 <br><br>Windows 10 の各リリースで使用可能な最新の Mixed Reality 機能については、[最新のリリース ノート](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/release-notes-october-2018.md)を参照してください。 [設定] > [更新とセキュリティ] > [開発者向け] から、**PC で開発者モードを有効にします**。 <br><br> **エンタープライズ管理および会社管理の PC の場合の注意事項**<br>お使いの PC が組織の IT 部門によって管理されている場合、更新するために管理者への連絡が必要な場合があります。 <br><br> **Windows の 'N' バージョン**<br> Windows Mixed Reality イマーシブ (VR) ヘッドセットは、Windows の 'N' バージョンではサポートされていません。 |
| ![Visual Studio のロゴ画像](images/visualstudio_logo.png)<br><br><a href="https://visualstudio.microsoft.com/downloads/" target="_blank">**Visual Studio 2019 (16.8 以降)** (インストールのリンク)</a> <br><br>完全な機能を備えた Windows などの統合開発環境 (IDE) です。 コードの記述、デバッグ、テスト、配置には、Visual Studio を使用します。 | **Visual Studio 2019 のインストール** <br> 次のワークロードをインストールします。 <br><br>*● C++ によるデスクトップ開発*<br>*● ユニバーサル Windows プラットフォーム (UWP) の開発*<br><br>HoloLens 向けの開発を行う場合は、UWP ワークロード内に次のオプションのコンポーネントがあることを確認してください。<br><br>*● USB デバイスの接続*<br><br>**Unity に関する注意事項**<br>特定の目的のために意図的により新しいバージョンの (LTS 以外の) Unity をインストールしようとしているのでなければ、Visual Studio のインストールの一部として Unity ワークロードをインストールする "*のではなく*"、下記のように **Unity 2019 LTS** ストリームをインストールすることをお勧めします。<br><br>**既知の問題**<br>Visual Studio 2019 バージョン 16.0 での Mixed Reality アプリのデバッグに関して既知の問題がいくつかあります。  必ず、**Visual Studio 2019 バージョン 16.8 以降** に更新してください。 |
| ![Windows ロゴ](images/Windows10_logo.png)<br><br><a href="https://developer.microsoft.com//windows/downloads/windows-10-sdk" target="_blank">**Windows 10 SDK (10.0.18362.0)** (手動インストールのリンク)</a> <br><br>HoloLens 2 で Windows 10 アプリを作成するための最新のヘッダー、ライブラリ、メタデータ、ツールが用意されています。 | **HoloLens 2 アプリを構築するには、ビルド 18362 以降の Windows SDK をインストールする必要があります。**<br> <br> デスクトップの Windows Mixed Reality ヘッドセットまたは HoloLens (第 1 世代) 用のアプリケーションのみを開発している場合は、Visual Studio 2017 によってインストールされた Windows SDK を使用することができます。 |
| ![Visual Studio のロゴ](images/HoloLensIcon.jpg)<br><br><a href="https://go.microsoft.com/fwlink/?linkid=2152389" target="_blank">**HoloLens 2 エミュレーター (Windows Holographic バージョン 20H2、2021 年 1 月の更新プログラム)** (インストール リンク:10.0.19041.1134)</a><br> <br><a href="https://go.microsoft.com/fwlink/?linkid=2065980" target="_blank">**HoloLens (第 1 世代) エミュレーター** (インストールのリンク:10.0.17763.134)</a> <br><br>エミュレーターを使用すると、物理的な HoloLens を使用せずに、HoloLens 仮想マシン イメージ上でアプリケーションを実行できます。<br> <br> | エミュレーターの使用を開始する方法については、「[Using the HoloLens emulator (HoloLens エミュレーターを使用する)](../develop/platform-capabilities-and-apis/using-the-hololens-emulator.md)」を参照してください。<br> <br> エミュレーターのインストールを成功させるには、**ご使用のシステムが Hyper-V をサポートしている必要があります**。 詳細については、以下の「システム要件」セクションを参照してください。 <br> <br> **HoloLens (第 1 世代) エミュレーターに関する注意** <br>  インストールを正常に完了するには、Visual Studio 2017 が必要です。 Visual Studio 2019 を使用して HoloLens (第1世代) エミュレーターをインストールする場合は、VS テンプレートの選択を解除し、[Visual Studio Marketplace からそれらをインストールする](https://marketplace.visualstudio.com/items?itemName=WindowsMixedRealityteam.WindowsMixedRealityAppTemplatesVSIX)必要があります。 |

## <a name="choose-your-engine"></a>エンジンの選択

これで、Windows 10、Visual Studio、Windows 10 SDK の準備ができました。次に、構築の基盤となるエンジンを選択します。

[!INCLUDE[](includes/tools-overview.md)]

