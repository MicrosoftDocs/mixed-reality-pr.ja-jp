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
# <a name="discovering-and-acquiring-features"></a><span data-ttu-id="ed2d4-104">機能の検出と取得</span><span class="sxs-lookup"><span data-stu-id="ed2d4-104">Discovering and acquiring features</span></span>

<span data-ttu-id="ed2d4-105">この記事のセクションでは、Mixed Reality Feature Tool で機能パッケージを見つける方法について概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-105">The sections in this article outline how to find feature packages in the Mixed Reality Feature Tool.</span></span> <span data-ttu-id="ed2d4-106">特定のセクションのリファレンスについては、以下のスクリーンショットを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-106">Refer to the screenshot below if you need a reference for a given section:</span></span>

![機能の検出](images/FeatureToolDiscovery.png)

## <a name="available-features"></a><span data-ttu-id="ed2d4-108">利用可能な機能</span><span class="sxs-lookup"><span data-stu-id="ed2d4-108">Available features</span></span>

### <a name="category"></a><span data-ttu-id="ed2d4-109">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="ed2d4-109">Category</span></span>

<span data-ttu-id="ed2d4-110">Mixed Reality Feature Tool には、機能カテゴリのコレクションが表示されるので、目的のものを簡単に見つけられます。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-110">The Mixed Reality Feature Tool displays a collection of feature categories to make it easy to find what you want.</span></span> <span data-ttu-id="ed2d4-111">カテゴリのいずれかを展開すると、使用できる機能のコレクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-111">Expand any of the categories to display its collection of available features.</span></span>

> [!NOTE]
> <span data-ttu-id="ed2d4-112">探している機能が見つからない場合は、 **[Other features]\(他の機能\)** を確認します。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-112">If you can't find the functionality you're looking for, check **Other features**.</span></span>

![機能カテゴリ](images/FeatureCategory.png)

<span data-ttu-id="ed2d4-114">上のスクリーンショットの左から順に説明すると、カテゴリ ヘッダーには次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-114">The category header in the above screenshot contains the following properties, from left to right:</span></span>

- <span data-ttu-id="ed2d4-115">展開または折りたたみボタン</span><span class="sxs-lookup"><span data-stu-id="ed2d4-115">Expand and collapse button</span></span>
- <span data-ttu-id="ed2d4-116">カテゴリ名 (例: Mixed Reality Toolkit)</span><span class="sxs-lookup"><span data-stu-id="ed2d4-116">Category name (ex: Mixed Reality Toolkit)</span></span>
- <span data-ttu-id="ed2d4-117">選択されている機能の数</span><span class="sxs-lookup"><span data-stu-id="ed2d4-117">Count of selected features</span></span>
- <span data-ttu-id="ed2d4-118">使用できる機能の数</span><span class="sxs-lookup"><span data-stu-id="ed2d4-118">Count of available features</span></span>

### <a name="feature"></a><span data-ttu-id="ed2d4-119">機能</span><span class="sxs-lookup"><span data-stu-id="ed2d4-119">Feature</span></span>

![機能のエントリ](images/FeatureEntry.png)

<span data-ttu-id="ed2d4-121">機能は、該当するカテゴリに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-121">Features are listed in their appropriate category.</span></span> <span data-ttu-id="ed2d4-122">上のスクリーンショットの左から順に説明すると、機能エントリには次の項目があります。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-122">From left to right in the above screenshot, feature entries contain:</span></span>

- <span data-ttu-id="ed2d4-123">選択チェックボックス</span><span class="sxs-lookup"><span data-stu-id="ed2d4-123">Selection check box</span></span>
- <span data-ttu-id="ed2d4-124">機能名 (例: Mixed Reality Toolkit Foundation)</span><span class="sxs-lookup"><span data-stu-id="ed2d4-124">Feature name (ex: Mixed Reality Toolkit Foundation)</span></span>
- <span data-ttu-id="ed2d4-125">使用できるバージョンの一覧</span><span class="sxs-lookup"><span data-stu-id="ed2d4-125">List of available versions</span></span>
- <span data-ttu-id="ed2d4-126">[機能パッケージの詳細](viewing-package-details.md)へのリンク</span><span class="sxs-lookup"><span data-stu-id="ed2d4-126">Link to the [feature package details](viewing-package-details.md)</span></span>

## <a name="refresh-the-feature-catalog"></a><span data-ttu-id="ed2d4-127">機能カタログを更新する</span><span class="sxs-lookup"><span data-stu-id="ed2d4-127">Refresh the feature catalog</span></span>

<span data-ttu-id="ed2d4-128">新機能と更新された機能を確認するには、[更新] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-128">To check for new and updated features, click the refresh</span></span> ![[更新] ボタン](images/RefreshButton.png) <span data-ttu-id="ed2d4-130">を追加します。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-130">button.</span></span> <span data-ttu-id="ed2d4-131">これにより、カタログ サイトに接続され、最新の情報が取得されます。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-131">This will connect to the catalog site and retrieve the latest information.</span></span>
* <span data-ttu-id="ed2d4-132">カタログが読み込まれると、最終更新の日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-132">Once the catalog has been read, the date and time of the last update will be displayed.</span></span>

## <a name="select-features"></a><span data-ttu-id="ed2d4-133">機能を選択する</span><span class="sxs-lookup"><span data-stu-id="ed2d4-133">Select features</span></span>

<span data-ttu-id="ed2d4-134">機能を選択するには、カテゴリを展開し、バージョンを選択し、チェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-134">Features are selected by expanding a category, selecting a version, and clicking the check box:</span></span>

![選択されている機能](images/SelectedFeatures.png)

<span data-ttu-id="ed2d4-136">1 つまたは複数の選択した機能を持つ各カテゴリが更新され、カウントが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-136">Each category with one or more selected features will update to display the count.</span></span>

## <a name="acquiring-features"></a><span data-ttu-id="ed2d4-137">機能の取得</span><span class="sxs-lookup"><span data-stu-id="ed2d4-137">Acquiring features</span></span>

<span data-ttu-id="ed2d4-138">機能を選択したら、 **[Get features]\(機能の取得\)** を選択して、選択した機能パッケージ ファイルのダウンロードを開始します。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-138">Once you've chosen your features, select **Get features** to start downloading the selected feature package files.</span></span>

> [!NOTE]
> <span data-ttu-id="ed2d4-139">既定では、以前に取得した機能パッケージ ファイルは再ダウンロードされません。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-139">By default, previously acquired feature package files won't be re-downloaded.</span></span> <span data-ttu-id="ed2d4-140">この動作を変更するには、[機能ツールの構成](configuring-feature-tool.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-140">To change this behavior please see [configuring the feature tool](configuring-feature-tool.md).</span></span>

<span data-ttu-id="ed2d4-141">ダウンロードが完了すると、Mixed Reality Feature Tool は[機能のインポート](importing-features.md)手順に移動します。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-141">Once downloading is complete, the Mixed Reality Feature Tool will move to the [importing features](importing-features.md) step.</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="ed2d4-142">前の手順に戻る</span><span class="sxs-lookup"><span data-stu-id="ed2d4-142">Going back to the previous step</span></span>

<span data-ttu-id="ed2d4-143">Mixed Reality Feature Tool では、 **[Discover features]\(機能の検出\)** から最初に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-143">From **Discover features**, the Mixed Reality Feature Tool allows for navigating back to the beginning.</span></span> <span data-ttu-id="ed2d4-144">もう一度始めるには、 **[Go back]\(戻る\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ed2d4-144">Select **Go back** to start again.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed2d4-145">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="ed2d4-145">See also</span></span>

- [<span data-ttu-id="ed2d4-146">Mixed Reality Feature Tool へようこそ</span><span class="sxs-lookup"><span data-stu-id="ed2d4-146">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="ed2d4-147">機能ツールの構成</span><span class="sxs-lookup"><span data-stu-id="ed2d4-147">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="ed2d4-148">機能パッケージの詳細の確認</span><span class="sxs-lookup"><span data-stu-id="ed2d4-148">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="ed2d4-149">選択したパッケージのインポート</span><span class="sxs-lookup"><span data-stu-id="ed2d4-149">Importing selected packages</span></span>](importing-features.md)
