---
title: プロジェクトの変更の承認
description: HoloLens および VR 開発の MR Feature Tool でプロジェクトの変更を承認する方法について説明します。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, ツール, はじめに, 基本, Unity, Visual Studio, ツールキット, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, インストール, Windows, HoloLens, エミュレーター, Unreal, OpenXR
ms.openlocfilehash: b9e4f53c9a1e5503cfa92a612879be1971422acc
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243971"
---
# <a name="authorizing-project-changes"></a>プロジェクトの変更の承認

Unity プロジェクトを変更する前に、マニフェスト ファイルとプロジェクト ファイルに対する変更を確認し、承認する必要があります。

![承認の要求](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a>Manifest

提案されたマニフェストの変更は、左側の **[Manifest]\(マニフェスト\)** 列で確認できます。 内容は、プロジェクト マニフェスト (**Packages/manifest.json**) に書き込まれる内容とまったく同じです。

![マニフェストのプレビュー](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a>プロジェクトにコピーされるファイル

右側の **[Files to be copied into the project]\(プロジェクトにコピーされるファイル\)** には、Unity プロジェクトにコピーされる特定の機能パッケージ ファイルが一覧表示されます。

![コピーされるファイルが表示されたマニフェストのプレビュー](images/FilesToCopy.png)

## <a name="compare-manifests"></a>マニフェストを比較する

**[Compare]\(比較\)** を選択すると、提案されたすべての変更を横に表示して比較することができます。

![マニフェストを比較する](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a>変更の承認

提案された変更が承認されると、一覧にあるファイルが Unity プロジェクトにコピーされ、これらのファイルを参照してマニフェストが更新されます。

> [!NOTE]
> 機能パッケージ (*.tgz) ファイルをソース管理に追加する必要があります。 これらは相対パスを使用して参照されるため、開発チームは機能とマニフェストの変更を簡単に共有できます。

 変更の過程で、現在の **manifest.json** ファイルがバックアップされます。

> [!IMPORTANT]
> マニフェストのバックアップを表示すると、最も古いものには **manifest.json.backup** という名前が付けられます。 新しいバックアップには、ゼロ (0) から始まる数値が付加されます。

## <a name="going-back-to-the-previous-step"></a>前の手順に戻る

機能の選択を変更する必要がある場合は、 **[Go back]\(戻る\)** を選択して[インポート](importing-features.md)手順に戻ります。

## <a name="see-also"></a>こちらもご覧ください

- [Mixed Reality Feature Tool へようこそ](welcome-to-mr-feature-tool.md)
- [選択したパッケージのインポート](importing-features.md)
