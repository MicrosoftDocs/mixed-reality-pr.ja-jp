---
title: Mixed Reality Feature Tool の構成
description: HoloLens および VR 開発用 MR Feature Tool から Mixed Reality Unity パッケージをダウンロードしてインストールする方法について説明します。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, ツール, はじめに, 基本, Unity, Visual Studio, ツールキット, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, インストール, Windows, HoloLens, エミュレーター, Unreal, OpenXR
ms.openlocfilehash: 4201f96ac87a6e9ab33607072c0d8f5f50df38a1
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244018"
---
# <a name="configuring-the-mixed-reality-feature-tool"></a>Mixed Reality Feature Tool の構成

Mixed Reality Feature Tool を使用すると、自由にカスタマイズできる 3 つの異なる設定カテゴリにアクセスできます。

* [[Download settings]\(ダウンロードの設定\)](#download-settings)
* [[Feature settings]\(機能の設定\)](#feature-settings)
* [設定のインポート](#import-settings)

![設定](images/FeatureToolSettings.png)

## <a name="download-settings"></a>［ダウンロードの設定］

### <a name="overwrite-existing-package-files"></a>[既存のパッケージ ファイルを上書き]

この設定を有効にすると、パッケージ ファイルが取得されるたびにダウンロードされます。 
* **ネットワーク帯域幅の使用量を減らすために、このオプションを無効にしておくことをお勧めします**
* 既定では、以前に取得したパッケージ ファイルは再ダウンロードされません

### <a name="package-cache"></a>[Package cache]\(パッケージのキャッシュ\)

機能パッケージがダウンロードされる場所を更新するには、この設定を変更します。

> [!NOTE]
> このリリースでは、この設定は **読み取り専用** です。 今後のリリースでは、この設定を構成できるようになります。

## <a name="feature-settings"></a>[Feature settings]\(機能の設定\)

### <a name="include-preview-releases"></a>[Include preview releases]\(プレビュー リリースを含める\)

プレビュー リリースを取得するには、この設定を有効にします。
* 既定では、プレビュー リリースは Mixed Reality Feature Tool に表示されません。 

> [!NOTE]
> プレビュー リリースは、パッケージ バージョンに **"-preview"** の指定が含まれているものと定義されています。

## <a name="import-settings"></a>設定のインポート

### <a name="replace-existing-package-files"></a>[Replace existing package files]\(既存のパッケージ ファイルを置き換える\)

Mixed Reality Feature Tool の既定では、ファイル サイズと不要な計算を減らすために、インポートされているパッケージの以前のコピーが削除されます。 
* すべてのバージョンを保持するには、この設定をオフにします

### <a name="project-relative-import-path"></a>[Project relative import path]\(プロジェクトの相対インポート パス\)

インポート時に機能パッケージがコピーされるプロジェクト フォルダーのパスを更新するには、この設定を変更します。 
* たとえば、プロジェクト フォルダーが **C:\GalaxyExplorer** の場合、完全修飾インポート パスは **C:\GalaxyExplorer\Packages\MixedReality** になります。

> [!NOTE]
> このリリースでは、この設定は **読み取り専用** です。 今後のリリースでは、この設定を構成できるようになります。

## <a name="see-also"></a>こちらもご覧ください

- [Mixed Reality Feature Tool へようこそ](welcome-to-mr-feature-tool.md)