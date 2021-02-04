---
title: Mixed Reality Feature Tool へようこそ
description: HoloLens および VR 開発用 MR Feature Tool の基本について説明します。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, ツール, はじめに, 基本, Unity, Visual Studio, ツールキット, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, インストール, Windows, HoloLens, エミュレーター, Unreal, OpenXR
ms.openlocfilehash: b9d54edb251cfe22d4f5fbea6fa8c923f6ff2d69
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244067"
---
# <a name="welcome-to-the-mixed-reality-feature-tool"></a>Mixed Reality Feature Tool へようこそ

![Mixed Reality Feature Tool のバナー画像](images/feature-tool-banner.png)

> [!IMPORTANT]
> Mixed Reality Feature Tool は、現時点では Unity でのみ使用できます。 Unreal で開発している場合は、[ツールのインストール](../install-the-tools.md)に関するドキュメントを参照してください。

Mixed Reality Feature Tool は、開発者が Mixed Reality 機能パッケージを検出し、更新し、Unity プロジェクトに追加するための新しい方法です。 名前またはカテゴリでパッケージを検索し、それらの依存関係を確認し、インポートする前にプロジェクト マニフェスト ファイルに提案された変更を確認することもできます。 これまでマニフェスト ファイルを使用したことがない場合、これはすべてのプロジェクト パッケージを含む JSON ファイルです。 必要なパッケージを検証すると、Mixed Reality Feature Tool によって、それらが選択したプロジェクトにダウンロードされます。

## <a name="system-requirements"></a>システム要件

Mixed Reality Feature Tool を実行するには、次のものが必要です。

* [.NET 5.0 ランタイム](https://dotnet.microsoft.com/download/dotnet/5.0)
* [Windows 10](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> 現在、Mixed Reality Feature Tool は、Windows 上でのみ動作しますが、MacOS のサポートも間もなく始まります。

環境を設定したら、次のようにします。

* [Microsoft ダウンロード センター](https://aka.ms/MRFeatureTool)から Mixed Reality Feature Tool の最新バージョンをダウンロードします。
* ダウンロードが完了したら、ファイルを展開してデスクトップに保存します
    * 簡単にアクセスできるように、実行可能ファイルのショートカットを作成することをお勧めします

## <a name="1-getting-started"></a>1.はじめに

実行可能ファイルから Mixed Reality Feature Tool を起動します。これにより、初回の起動時にスタート ページが表示されます。

![作業の開始](images/FeatureToolStart.png)

スタート ページでは、次のことができます。

* **歯車アイコン** ボタンを使用してツール設定を[構成](configuring-feature-tool.md)します
* **疑問符** ボタンを使用して既定の Web ブラウザーを起動し、ドキュメントを表示します
* **[開始]** を選択して、機能パッケージの検出を開始します

## <a name="2-discovering-and-acquiring-feature-packages"></a>2.機能パッケージの検出と取得

[開始] を押すと、すぐに機能パッケージ カタログが取得されます。 機能は、見つけやすいようにカテゴリ別にグループ化されています。 たとえば、**Mixed Reality Toolkit** カテゴリには、次のようないくつかの機能があります。

![検出と取得](images/FeatureToolDiscovery.png)

選択が完了したら、 **[Get features]\(機能の取得\)** を選択し、カタログから必要なすべてのパッケージをフェッチします。 詳細については、「[機能の検出と取得](discovering-features.md)」を参照してください。

## <a name="3-importing-feature-packages"></a>3.機能パッケージのインポート

取得後は、パッケージの完全なセットと、必要な依存関係の一覧が表示されます。 機能またはパッケージの選択を変更する必要がある場合は、次のようにします。

![パッケージをインポートする](images/FeatureToolImport.png)

選択した機能が Unity プロジェクトによって正常にインポートされるように、 **[検証]** ボタンを使用することを強くお勧めします。 検証後は、成功メッセージまたは特定された問題の一覧を含むポップアップ ダイアログが表示されます。

インポートする前に、ターゲットの Unity プロジェクトの場所も設定する必要があります。 参照するには、プロジェクト パス フィールドの左側にある **省略記号** ボタンを使用します。 ファイル システムの操作が完了したら、ターゲットの Unity プロジェクトを含むフォルダーを開きます。

> [!NOTE]
> Unity プロジェクト フォルダーを参照するときに表示されるダイアログには、ファイル名として '_' が含まれています。 フォルダーを選択できるようにするには、ファイル名に値が必要です。

**[インポート]** を選択して続行します。

> [!NOTE]
> **[インポート]** ボタンをクリックした後、問題が残っている場合は、簡単なメッセージが表示されます。 [いいえ] をクリックし、 **[検証]** ボタンを使用して問題を確認し、解決することをお勧めします。

詳細については、[機能のインポート](importing-features.md)に関するページを参照してください。

## <a name="4-reviewing-and-approving-project-changes"></a>4。プロジェクトの変更点の確認と承認

最後の手順は、マニフェスト ファイルとプロジェクト ファイルに対して提案された変更を確認し、承認することです。

* マニフェストに対して提案された変更が左側に表示されます
* プロジェクトに追加できるファイルは右側に一覧されます
* **[比較]** ボタンを使用すると、現在のマニフェストと提案された変更を並べて確認できます。

![承認](images/FeatureToolApprovalRequest.png)

詳細については、[プロジェクトの変更の確認と承認](reviewing-changes.md)に関するページを参照してください。

## <a name="5-project-updated"></a>5。プロジェクトの更新

提案された変更が承認されると、ターゲットの Unity プロジェクトは、選択した Mixed Reality 機能を参照するように更新されます。

![プロジェクトの更新](images/FeatureToolProjectUpdated.png)

Unity プロジェクトの **Packages** フォルダーには、機能パッケージ ファイルを含む **MixedReality** サブフォルダーがあり、マニフェストには適切な参照が含まれます。

Unity に戻り、新しく選択した機能が読み込まれるまで待ってから、ビルドを開始してください。

## <a name="see-also"></a>こちらもご覧ください

- [機能ツールの構成](configuring-feature-tool.md)
- [検出と取得](discovering-features.md)
- [機能パッケージの詳細の確認](viewing-package-details.md)
- [選択したパッケージのインポート](importing-features.md)
- [プロジェクトの変更点の確認と承認](reviewing-changes.md)
