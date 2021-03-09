---
title: 機能のインポート
description: HoloLens および VR 開発用 MR Feature Tool から機能をインポートしてインストールする方法について説明します。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 03/04/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, ツール, はじめに, 基本, Unity, Visual Studio, ツールキット, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, インストール, Windows, HoloLens, エミュレーター, Unreal, OpenXR
ms.openlocfilehash: 0d9139835b9eb4e3e5ce3d1f378c56a4724bfa55
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230823"
---
# <a name="importing-features"></a>機能のインポート

機能がダウンロードされたら、それらを確認して Unity プロジェクトにインポートできます。 この手順では、アプリケーション ウィンドウは次の画像のようになります。

![機能のインポート](images/FeatureToolImport.png)

## <a name="features-list"></a>Features list

**[機能]** 一覧には、検出中に選択されたパッケージのコレクションが表示されます。 インポートする前に、各機能を選択または選択解除することができます。 次に示す **[詳細]** リンクを使用してパッケージの詳細を確認することができます

![Features list](images/FeaturesList.png)

## <a name="required-dependencies-list"></a>[Required dependencies]\(必要な依存関係\) 一覧

**[Required dependencies]\(必要な依存関係\)** 一覧には、選択した 1 つまたは複数の機能が機能するために必要なパッケージが表示されます。 この一覧には、依存関係の依存関係も含まれます。 各依存関係は、インポートする前に選択または選択解除することができます。 次に示す **[詳細]** リンクを使用してパッケージの詳細を確認することができます

![依存関係の一覧](images/RequiredDependencyList.png)

> [!NOTE]
> 必要な依存関係をオフにすると、Unity でプロジェクトを読み込むときに依存関係の不足エラーが 1 つ以上発生します。 このような機能はプロジェクトで使用できません。

## <a name="validating-selections"></a>選択の検証

インポートする前に、機能の選択を検証することを強くお勧めします。 この手順で、プロジェクト開発の成功を妨げる可能性のある問題を明らかにします。

![検証の問題](images/ValidationIssues.png)

Mixed Reality Feature Tool には、次のセクションで説明する 2 つの自動問題解決機能と、問題を手動で取り消して解決するオプションが用意されています。

### <a name="enable-dependencies"></a>依存関係を有効にする

**[Enable dependencies]\(依存関係を有効にする\)** ボタンをクリックすると、不足している依存関係が自動的に再選択されます。 明示的に選択した依存関係 ( **[機能]** 一覧に表示されます) と、その選択した機能の要件に基づいて暗黙的に選択されたものが対象になります。

### <a name="disable-features"></a>機能を無効にする

**[Disable features]\(機能を無効にする\)** を選択すると、オフになっている 1 つ以上の依存関係に依存する機能の選択が自動的に解除されます。 暗黙的に選択された依存関係パッケージと、明示的に選択した機能が対象になります。

## <a name="importing"></a>インポート

**[インポート]** を選択して、選んだ機能を追加します。ターゲット プロジェクトを更新する前に、[最終的な承認](reviewing-changes.md)を行います。

> [!IMPORTANT]
> インポート時に検証の問題が残っている場合は、警告メッセージが表示されます。 [いいえ] を選択し、 **[検証]** をクリックして、表示された問題を解決することをお勧めします。
>
> ![検証の問題を続行する](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a>前の手順に戻る

Mixed Reality Feature Tool では、 **[Import features]\(機能のインポート\)** から [検出](discovering-features.md)に戻ることができます。 他の機能パッケージをダウンロードするには、 **[Go back]\(戻る\)** を選択します。

## <a name="see-also"></a>こちらもご覧ください

- [Mixed Reality Feature Tool へようこそ](welcome-to-mr-feature-tool.md)
- [検出と取得](discovering-features.md)
- [機能パッケージの詳細の確認](viewing-package-details.md)
- [プロジェクトの変更点の確認と承認](reviewing-changes.md)