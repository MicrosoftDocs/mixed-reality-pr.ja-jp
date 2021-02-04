---
title: 機能のインポート
description: HoloLens および VR 開発用 MR Feature Tool から機能をインポートしてインストールする方法について説明します。
author: davidkline-ms
ms.author: v-hferrone
ms.date: 01/27/2021
ms.topic: article
ms.localizationpriority: high
keywords: 最新, ツール, はじめに, 基本, Unity, Visual Studio, ツールキット, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット, インストール, Windows, HoloLens, エミュレーター, Unreal, OpenXR
ms.openlocfilehash: a82eea93a07b662314f3a718eef0c1bd18a4ca4e
ms.sourcegitcommit: cef969ffd22dc1e5a1e9c3c32fbf0646206519a1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2021
ms.locfileid: "99243986"
---
# <a name="importing-features"></a><span data-ttu-id="cc329-104">機能のインポート</span><span class="sxs-lookup"><span data-stu-id="cc329-104">Importing features</span></span>

<span data-ttu-id="cc329-105">機能がダウンロードされたら、それらを確認して Unity プロジェクトにインポートできます。</span><span class="sxs-lookup"><span data-stu-id="cc329-105">Once your features have been downloaded, they can be reviewed and imported into the Unity project.</span></span> <span data-ttu-id="cc329-106">この手順では、アプリケーション ウィンドウは次の画像のようになります。</span><span class="sxs-lookup"><span data-stu-id="cc329-106">At this step, your application window should look like the following image:</span></span>

![機能のインポート](images/FeatureToolImport.png)

## <a name="features-list"></a><span data-ttu-id="cc329-108">Features list</span><span class="sxs-lookup"><span data-stu-id="cc329-108">Features list</span></span>

<span data-ttu-id="cc329-109">**[機能]** 一覧には、検出中に選択されたパッケージのコレクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cc329-109">The **Features** list contains the collection of packages selected during discovery.</span></span> 
* <span data-ttu-id="cc329-110">インポートする前に、各機能を選択または選択解除することができます。</span><span class="sxs-lookup"><span data-stu-id="cc329-110">Each feature can be selected or deselected before importing.</span></span> <span data-ttu-id="cc329-111">次に示す **[詳細]** リンクを使用してパッケージの詳細を確認することができます</span><span class="sxs-lookup"><span data-stu-id="cc329-111">Package details can be viewed using the **Details** link shown below</span></span>

![Features list](images/FeaturesList.png)

## <a name="required-dependencies-list"></a><span data-ttu-id="cc329-113">[Required dependencies]\(必要な依存関係\) 一覧</span><span class="sxs-lookup"><span data-stu-id="cc329-113">Required dependencies list</span></span>

<span data-ttu-id="cc329-114">**[Required dependencies]\(必要な依存関係\)** 一覧には、選択した 1 つまたは複数の機能が機能するために必要なパッケージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cc329-114">The **Required dependencies** list contains the packages that one or more of the selected features requires to function.</span></span> <span data-ttu-id="cc329-115">この一覧には、依存関係の依存関係も含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc329-115">This list will also contain dependencies of dependencies.</span></span>
* <span data-ttu-id="cc329-116">各依存関係は、インポートする前に選択または選択解除することができます。</span><span class="sxs-lookup"><span data-stu-id="cc329-116">Each dependency can be selected or deselected before importing.</span></span> <span data-ttu-id="cc329-117">次に示す **[詳細]** リンクを使用してパッケージの詳細を確認することができます</span><span class="sxs-lookup"><span data-stu-id="cc329-117">Package details can be viewed using the **Details** link shown below</span></span>

![依存関係の一覧](images/RequiredDependencyList.png)

> [!NOTE]
> <span data-ttu-id="cc329-119">必要な依存関係をオフにすると、Unity でプロジェクトを読み込むときに依存関係の不足エラーが 1 つ以上発生します。</span><span class="sxs-lookup"><span data-stu-id="cc329-119">Deselecting required dependencies will result in one or more missing dependency errors when loading the project in Unity.</span></span> <span data-ttu-id="cc329-120">このような機能はプロジェクトで使用できません。</span><span class="sxs-lookup"><span data-stu-id="cc329-120">These features won't be usable in the project.</span></span>

## <a name="specifying-the-unity-project-path"></a><span data-ttu-id="cc329-121">Unity プロジェクト パスの指定</span><span class="sxs-lookup"><span data-stu-id="cc329-121">Specifying the Unity project path</span></span>

<span data-ttu-id="cc329-122">プロジェクトに機能をインポートする前に、Mixed Reality Feature Tool にパスを登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc329-122">Before features can be imported into the project, you need to register the path with the Mixed Reality Feature Tool.</span></span>

![プロジェクト パスの設定](images/ProjectPath.png)

## <a name="validating-selections"></a><span data-ttu-id="cc329-124">選択の検証</span><span class="sxs-lookup"><span data-stu-id="cc329-124">Validating selections</span></span>

<span data-ttu-id="cc329-125">インポートする前に、機能の選択を検証することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cc329-125">We highly recommend validating feature selections before importing.</span></span> <span data-ttu-id="cc329-126">この手順で、プロジェクト開発の成功を妨げる可能性のある問題を明らかにします。</span><span class="sxs-lookup"><span data-stu-id="cc329-126">This step will raise any issues that are likely to impede successful project development.</span></span>

![検証の問題](images/ValidationIssues.png)

<span data-ttu-id="cc329-128">Mixed Reality Feature Tool には、次のセクションで説明する 2 つの自動問題解決機能と、問題を手動で取り消して解決するオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="cc329-128">The Mixed Reality Feature Tool provides two automatic issue resolutions, described in the following sections), and the option to cancel and resolve issues manually.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cc329-129">Mixed Reality Feature Tool には、Unity の必要なバージョンに関連する問題を自動的に解決する機能がありません。</span><span class="sxs-lookup"><span data-stu-id="cc329-129">The Mixed Reality Feature Tool cannot automatically resolve issues related to required versions of Unity.</span></span> <span data-ttu-id="cc329-130">このような問題を手動で処理するには、プロジェクトで使用されている Unity のバージョンをアップグレードするか、新しいバージョンを必要とする機能を無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc329-130">These issues must be handled manually by upgrading the version of Unity used by the project or disabling the feature(s) requiring a newer version.</span></span>
>
> <span data-ttu-id="cc329-131">Mixed Reality Feature Tool の今後のリリースでは、プロジェクトで使用されている Unity のバージョンに基づく機能のフィルター処理が改善される予定です。</span><span class="sxs-lookup"><span data-stu-id="cc329-131">A future release of the Mixed Reality Feature Tool will provide better filtering of features based upon the version of Unity being used by the project.</span></span>

### <a name="enable-dependencies"></a><span data-ttu-id="cc329-132">依存関係を有効にする</span><span class="sxs-lookup"><span data-stu-id="cc329-132">Enable dependencies</span></span>

<span data-ttu-id="cc329-133">**[Enable dependencies]\(依存関係を有効にする\)** ボタンをクリックすると、不足している依存関係が自動的に再選択されます。</span><span class="sxs-lookup"><span data-stu-id="cc329-133">The **Enable dependencies** button will automatically re-select the missing dependencies.</span></span> <span data-ttu-id="cc329-134">明示的に選択した依存関係 ( **[機能]** 一覧に表示されます) と、その選択した機能の要件に基づいて暗黙的に選択されたものが対象になります。</span><span class="sxs-lookup"><span data-stu-id="cc329-134">This is true for dependencies that were explicitly selected (appear in the **Features** list) and those that were implicitly selected based on the requirements of the selected features.</span></span>

### <a name="disable-features"></a><span data-ttu-id="cc329-135">機能を無効にする</span><span class="sxs-lookup"><span data-stu-id="cc329-135">Disable features</span></span>

<span data-ttu-id="cc329-136">**[Disable features]\(機能を無効にする\)** を選択すると、オフになっている 1 つ以上の依存関係に依存する機能の選択が自動的に解除されます。</span><span class="sxs-lookup"><span data-stu-id="cc329-136">Selecting **Disable features** will automatically deselect any feature that depends on one or more of the dependencies that have been unchecked.</span></span> <span data-ttu-id="cc329-137">暗黙的に選択された依存関係パッケージと、明示的に選択した機能が対象になります。</span><span class="sxs-lookup"><span data-stu-id="cc329-137">This is true for implicitly selected dependency packages and explicitly selected features.</span></span>

## <a name="importing"></a><span data-ttu-id="cc329-138">インポート</span><span class="sxs-lookup"><span data-stu-id="cc329-138">Importing</span></span>

<span data-ttu-id="cc329-139">**[インポート]** を選択して、選んだ機能を追加します。ターゲット プロジェクトを更新する前に、[最終的な承認](reviewing-changes.md)を行います。</span><span class="sxs-lookup"><span data-stu-id="cc329-139">Select **Import** to add your selected features and give [final approval](reviewing-changes.md) before updating your target project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cc329-140">インポート時に検証の問題が残っている場合は、警告メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="cc329-140">If a validation issue remains when importing, a warning message will be displayed.</span></span> <span data-ttu-id="cc329-141">[いいえ] を選択し、 **[検証]** をクリックして、表示された問題を解決することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cc329-141">It is recommended to select No, click **Validate** and resolve any issues presented.</span></span>
>
> ![検証の問題を続行する](images/ValidationContinueAnyway.png)

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="cc329-143">前の手順に戻る</span><span class="sxs-lookup"><span data-stu-id="cc329-143">Going back to the previous step</span></span>

<span data-ttu-id="cc329-144">Mixed Reality Feature Tool では、 **[Import features]\(機能のインポート\)** から[検出](discovering-features.md)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="cc329-144">From **Import features**, the Mixed Reality Feature Tool allows for navigating back to [discovery](discovering-features.md).</span></span> <span data-ttu-id="cc329-145">他の機能パッケージをダウンロードするには、 **[Go back]\(戻る\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="cc329-145">Select **Go back** to download other feature packages.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc329-146">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="cc329-146">See also</span></span>

- [<span data-ttu-id="cc329-147">Mixed Reality Feature Tool へようこそ</span><span class="sxs-lookup"><span data-stu-id="cc329-147">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="cc329-148">検出と取得</span><span class="sxs-lookup"><span data-stu-id="cc329-148">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="cc329-149">機能パッケージの詳細の確認</span><span class="sxs-lookup"><span data-stu-id="cc329-149">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="cc329-150">プロジェクトの変更点の確認と承認</span><span class="sxs-lookup"><span data-stu-id="cc329-150">Reviewing and approving project modifications</span></span>](reviewing-changes.md)