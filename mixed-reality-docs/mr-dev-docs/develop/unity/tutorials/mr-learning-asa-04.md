---
title: Azure Spatial Anchors フィードバックの表示
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure Spatial Anchors からのフィードバックを表示する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー, セッション, フィードバック要素
ms.localizationpriority: high
ms.openlocfilehash: f5f92d8b19da6a449b8630d7f87e0719e438b4ab
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590674"
---
# <a name="4-displaying-feedback-from-azure-spatial-anchors"></a>4.Azure Spatial Anchors からのフィードバックを表示する

このチュートリアルでは、Azure Spatial Anchors (ASA) を使用したアンカーの検出、イベント、状態に関するフィードバックをユーザーに提供する方法について説明します。

## <a name="objectives"></a>目標

* 現在の ASA セッションに関する不可欠な情報を表示する UI パネルを設定する方法を理解する
* ASA SDK によってユーザーに提供されるフィードバック要素を理解し、確認する

## <a name="setting-up-asa-feedback-panel"></a>ASA フィードバック パネルの設定

[階層] ウィンドウで、 **[手順]** の **[TextContent]** オブジェクトを右クリックします。 **[3D オブジェクト]** 、 **[テキスト - TextMeshPro]** の順に選択し、[指示] の [TextContent] オブジェクトの子として TextMeshPro テキスト オブジェクトを作成します。

![新しく作成された TextMeshPro オブジェクトが選択されている Unity](images/mr-learning-asa/asa-04-section1-step1-1.png)

> [!TIP]
> シーンを簡単に操作できるようにするには、ParentAnchor オブジェクトの左側にある目のアイコンをクリックして、そのオブジェクトの<a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">シーンの可視性</a>をオフに設定します。 これにより、ゲーム中の可視性を変更することなく、[Scene]\(シーン\) ウィンドウ内のオブジェクトが非表示になります。

新しく作成した [テキスト (TMP)] オブジェクトに **Feedback** という名前を付け、[Inspector]\(インスペクター\) ウィンドウでその位置とサイズを変更して、指示テキストの下に配置されるようにします。次に例を示します。

* [Rect Transform]\(四角形の変換\) コンポーネントの **[Pos Y]\(位置 Y\)** を -0.24 に変更します。
* [Rect Transform]\(四角形の変換\) コンポーネントの **[幅]** を 0.555 に変更します。
* [Rect Transform]\(四角形の変換\) コンポーネントの **[高さ]** を 0.1 に変更します。

次に、テキスト領域内にテキストがうまく適合するように、フォントのプロパティを選択します。次に例を示します。

* [TextMeshPro - テキスト] コンポーネントの **[フォント スタイル]** を [ボールド] に変更します。
* [TextMeshPro - テキスト] コンポーネントの **[フォント サイズ]** を 0.17 に変更します。
* [TextMeshPro - テキスト] コンポーネントの **[配置]** を中央揃えに変更します。

![Feedback オブジェクトが構成された Unity](images/mr-learning-asa/asa-04-section1-step1-2.png)

[階層] ウィンドウで、 **[フィードバック]** オブジェクトを選択します。次に、[Inspector]\(インスペクター\) ウィンドウで **[コンポーネントの追加]** ボタンを使用し、 **[Anchor Feedback Script (Script)]\(Anchor フィードバック スクリプト (スクリプト)\)** コンポーネントを配置して、次のように構成します。

* **Feedback** オブジェクト自体を **Anchor Feedback Script (Script)** コンポーネントの **[Feedback Text]\(フィードバック テキスト\)** フィールドに割り当てます。

![Anchor Feedback Script コンポーネントが構成された Unity](images/mr-learning-asa/asa-04-section1-step1-3.png)

## <a name="congratulations"></a>結論

このチュートリアルでは、UI パネルを作成する方法を学習しました。 リアルタイム フィードバックをユーザーに提供する Azure Spatial Anchors 体験の現在の状態が表示されます。

> [!div class="nextstepaction"]
> [次のチュートリアル:5.Android と iOS 用の Azure Spatial Anchors](mr-learning-asa-05.md)
