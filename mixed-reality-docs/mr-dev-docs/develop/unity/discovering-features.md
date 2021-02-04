---
title: 機能の検出と取得
description: Mixed Reality の機能について確認し、ダウンロードします。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, ツール, はじめに, 基本, Unity, Visual Studio, ツールキット, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, インストール, Windows, HoloLens, エミュレーター, Unreal, OpenXR
ms.openlocfilehash: 4da6b6fdfc0205d4fa7fb5bf4ae9e48993d7c1e6
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2021
ms.locfileid: "99244026"
---
# <a name="discovering-and-acquiring-features"></a>機能の検出と取得

この記事のセクションでは、Mixed Reality Feature Tool で機能パッケージを見つける方法について概要を説明します。 特定のセクションのリファレンスについては、以下のスクリーンショットを参照してください。

![機能の検出](images/FeatureToolDiscovery.png)

## <a name="available-features"></a>利用可能な機能

### <a name="category"></a>カテゴリ

Mixed Reality Feature Tool には、機能カテゴリのコレクションが表示されるので、目的のものを簡単に見つけられます。 カテゴリのいずれかを展開すると、使用できる機能のコレクションが表示されます。

> [!NOTE]
> 探している機能が見つからない場合は、 **[Other features]\(他の機能\)** を確認します。

![機能カテゴリ](images/FeatureCategory.png)

上のスクリーンショットの左から順に説明すると、カテゴリ ヘッダーには次のプロパティがあります。

- 展開または折りたたみボタン
- カテゴリ名 (例: Mixed Reality Toolkit)
- 選択されている機能の数
- 使用できる機能の数

### <a name="feature"></a>機能

![機能のエントリ](images/FeatureEntry.png)

機能は、該当するカテゴリに一覧表示されます。 上のスクリーンショットの左から順に説明すると、機能エントリには次の項目があります。

- 選択チェックボックス
- 機能名 (例: Mixed Reality Toolkit Foundation)
- 使用できるバージョンの一覧
- [機能パッケージの詳細](viewing-package-details.md)へのリンク

## <a name="refresh-the-feature-catalog"></a>機能カタログを更新する

新機能と更新された機能を確認するには、[更新] をクリックします。 ![[更新] ボタン](images/RefreshButton.png) を追加します。 これにより、カタログ サイトに接続され、最新の情報が取得されます。
* カタログが読み込まれると、最終更新の日時が表示されます。

## <a name="select-features"></a>機能を選択する

機能を選択するには、カテゴリを展開し、バージョンを選択し、チェックボックスをオンにします。

![選択されている機能](images/SelectedFeatures.png)

1 つまたは複数の選択した機能を持つ各カテゴリが更新され、カウントが表示されます。

## <a name="acquiring-features"></a>機能の取得

機能を選択したら、 **[Get features]\(機能の取得\)** を選択して、選択した機能パッケージ ファイルのダウンロードを開始します。

> [!NOTE]
> 既定では、以前に取得した機能パッケージ ファイルは再ダウンロードされません。 この動作を変更するには、[機能ツールの構成](configuring-feature-tool.md)に関するページを参照してください。

ダウンロードが完了すると、Mixed Reality Feature Tool は[機能のインポート](importing-features.md)手順に移動します。

## <a name="going-back-to-the-previous-step"></a>前の手順に戻る

Mixed Reality Feature Tool では、 **[Discover features]\(機能の検出\)** から最初に戻ることができます。 もう一度始めるには、 **[Go back]\(戻る\)** を選択します。

## <a name="see-also"></a>こちらもご覧ください

- [Mixed Reality Feature Tool へようこそ](welcome-to-mr-feature-tool.md)
- [機能ツールの構成](configuring-feature-tool.md)
- [機能パッケージの詳細の確認](viewing-package-details.md)
- [選択したパッケージのインポート](importing-features.md)
