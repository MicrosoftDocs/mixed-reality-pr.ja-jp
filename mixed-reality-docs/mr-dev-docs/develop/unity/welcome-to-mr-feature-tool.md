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
# <a name="welcome-to-the-mixed-reality-feature-tool"></a><span data-ttu-id="66fff-104">Mixed Reality Feature Tool へようこそ</span><span class="sxs-lookup"><span data-stu-id="66fff-104">Welcome to the Mixed Reality Feature Tool</span></span>

![Mixed Reality Feature Tool のバナー画像](images/feature-tool-banner.png)

> [!IMPORTANT]
> <span data-ttu-id="66fff-106">Mixed Reality Feature Tool は、現時点では Unity でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="66fff-106">The Mixed Reality Feature Tool is only available for Unity at the moment.</span></span> <span data-ttu-id="66fff-107">Unreal で開発している場合は、[ツールのインストール](../install-the-tools.md)に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="66fff-107">If you're developing in Unreal, refer to the [tools installation](../install-the-tools.md) documentation.</span></span>

<span data-ttu-id="66fff-108">Mixed Reality Feature Tool は、開発者が Mixed Reality 機能パッケージを検出し、更新し、Unity プロジェクトに追加するための新しい方法です。</span><span class="sxs-lookup"><span data-stu-id="66fff-108">The Mixed Reality Feature Tool is a new way for developers to discover, update, and add Mixed Reality feature packages into Unity projects.</span></span> <span data-ttu-id="66fff-109">名前またはカテゴリでパッケージを検索し、それらの依存関係を確認し、インポートする前にプロジェクト マニフェスト ファイルに提案された変更を確認することもできます。</span><span class="sxs-lookup"><span data-stu-id="66fff-109">You can search packages by name or category, see their dependencies, and even view proposed changes to your projects manifest file before importing.</span></span> <span data-ttu-id="66fff-110">これまでマニフェスト ファイルを使用したことがない場合、これはすべてのプロジェクト パッケージを含む JSON ファイルです。</span><span class="sxs-lookup"><span data-stu-id="66fff-110">If you've never worked with a manifest file before, it's a JSON file containing all your projects packages.</span></span> <span data-ttu-id="66fff-111">必要なパッケージを検証すると、Mixed Reality Feature Tool によって、それらが選択したプロジェクトにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="66fff-111">Once you've validated the packages you want, the Mixed Reality Feature tool will download them into the project of your choice.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="66fff-112">システム要件</span><span class="sxs-lookup"><span data-stu-id="66fff-112">System requirements</span></span>

<span data-ttu-id="66fff-113">Mixed Reality Feature Tool を実行するには、次のものが必要です。</span><span class="sxs-lookup"><span data-stu-id="66fff-113">Before you can run the Mixed Reality Feature Tool, you'll need:</span></span>

* [<span data-ttu-id="66fff-114">.NET 5.0 ランタイム</span><span class="sxs-lookup"><span data-stu-id="66fff-114">.NET 5.0 runtime</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
* [<span data-ttu-id="66fff-115">Windows 10</span><span class="sxs-lookup"><span data-stu-id="66fff-115">Windows 10</span></span>](https://www.microsoft.com/software-download/windows10ISO)

> [!NOTE]
> <span data-ttu-id="66fff-116">現在、Mixed Reality Feature Tool は、Windows 上でのみ動作しますが、MacOS のサポートも間もなく始まります。</span><span class="sxs-lookup"><span data-stu-id="66fff-116">The Mixed Reality Feature Tool currently only runs on Windows, but MacOS support is coming soon!</span></span>

<span data-ttu-id="66fff-117">環境を設定したら、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="66fff-117">Once you have your environment set up:</span></span>

* <span data-ttu-id="66fff-118">[Microsoft ダウンロード センター](https://aka.ms/MRFeatureTool)から Mixed Reality Feature Tool の最新バージョンをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="66fff-118">Download the latest version of the Mixed Reality Feature Tool from the [Microsoft Download Center](https://aka.ms/MRFeatureTool).</span></span>
* <span data-ttu-id="66fff-119">ダウンロードが完了したら、ファイルを展開してデスクトップに保存します</span><span class="sxs-lookup"><span data-stu-id="66fff-119">When the download completes, unzip the file and save it to your desktop</span></span>
    * <span data-ttu-id="66fff-120">簡単にアクセスできるように、実行可能ファイルのショートカットを作成することをお勧めします</span><span class="sxs-lookup"><span data-stu-id="66fff-120">We recommend creating a shortcut to the executable file for faster access</span></span>

## <a name="1-getting-started"></a><span data-ttu-id="66fff-121">1.はじめに</span><span class="sxs-lookup"><span data-stu-id="66fff-121">1. Getting started</span></span>

<span data-ttu-id="66fff-122">実行可能ファイルから Mixed Reality Feature Tool を起動します。これにより、初回の起動時にスタート ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="66fff-122">Launch the Mixed Reality Feature Tool from the executable file, which displays the start page on first launch:</span></span>

![作業の開始](images/FeatureToolStart.png)

<span data-ttu-id="66fff-124">スタート ページでは、次のことができます。</span><span class="sxs-lookup"><span data-stu-id="66fff-124">From the start page, you can:</span></span>

* <span data-ttu-id="66fff-125">**歯車アイコン** ボタンを使用してツール設定を[構成](configuring-feature-tool.md)します</span><span class="sxs-lookup"><span data-stu-id="66fff-125">[Configure](configuring-feature-tool.md) tool settings using the **gear icon** button</span></span>
* <span data-ttu-id="66fff-126">**疑問符** ボタンを使用して既定の Web ブラウザーを起動し、ドキュメントを表示します</span><span class="sxs-lookup"><span data-stu-id="66fff-126">Use the **question mark** button to launch the default web browser and display our documentation</span></span>
* <span data-ttu-id="66fff-127">**[開始]** を選択して、機能パッケージの検出を開始します</span><span class="sxs-lookup"><span data-stu-id="66fff-127">Select **Start** to begin discovering feature packages</span></span>

## <a name="2-discovering-and-acquiring-feature-packages"></a><span data-ttu-id="66fff-128">2.機能パッケージの検出と取得</span><span class="sxs-lookup"><span data-stu-id="66fff-128">2. Discovering and acquiring feature packages</span></span>

<span data-ttu-id="66fff-129">[開始] を押すと、すぐに機能パッケージ カタログが取得されます。</span><span class="sxs-lookup"><span data-stu-id="66fff-129">The feature package catalog is retrieved as soon as you press Start.</span></span> <span data-ttu-id="66fff-130">機能は、見つけやすいようにカテゴリ別にグループ化されています。</span><span class="sxs-lookup"><span data-stu-id="66fff-130">Features are grouped by category to make things easier to find.</span></span> <span data-ttu-id="66fff-131">たとえば、**Mixed Reality Toolkit** カテゴリには、次のようないくつかの機能があります。</span><span class="sxs-lookup"><span data-stu-id="66fff-131">For example, the **Mixed Reality Toolkit** category has several features for you to choose from:</span></span>

![検出と取得](images/FeatureToolDiscovery.png)

<span data-ttu-id="66fff-133">選択が完了したら、 **[Get features]\(機能の取得\)** を選択し、カタログから必要なすべてのパッケージをフェッチします。</span><span class="sxs-lookup"><span data-stu-id="66fff-133">Once you've made your choices, select **Get features** to fetch all the required packages from the catalog.</span></span> <span data-ttu-id="66fff-134">詳細については、「[機能の検出と取得](discovering-features.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66fff-134">For more information, please see [discovering and acquiring features](discovering-features.md).</span></span>

## <a name="3-importing-feature-packages"></a><span data-ttu-id="66fff-135">3.機能パッケージのインポート</span><span class="sxs-lookup"><span data-stu-id="66fff-135">3. Importing feature packages</span></span>

<span data-ttu-id="66fff-136">取得後は、パッケージの完全なセットと、必要な依存関係の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="66fff-136">Following acquisition, the complete set of packages is presented, along with a list of required dependencies.</span></span> <span data-ttu-id="66fff-137">機能またはパッケージの選択を変更する必要がある場合は、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="66fff-137">If you need to change any feature or package selections, this is the time:</span></span>

![パッケージをインポートする](images/FeatureToolImport.png)

<span data-ttu-id="66fff-139">選択した機能が Unity プロジェクトによって正常にインポートされるように、 **[検証]** ボタンを使用することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66fff-139">We highly recommend using the **Validate** button to ensure the Unity project can successfully import the selected features.</span></span> <span data-ttu-id="66fff-140">検証後は、成功メッセージまたは特定された問題の一覧を含むポップアップ ダイアログが表示されます。</span><span class="sxs-lookup"><span data-stu-id="66fff-140">After validation, you'll see a pop-up dialog with a success message or a list of identified issues.</span></span>

<span data-ttu-id="66fff-141">インポートする前に、ターゲットの Unity プロジェクトの場所も設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66fff-141">You also need to set the location of the target Unity project before you import.</span></span> <span data-ttu-id="66fff-142">参照するには、プロジェクト パス フィールドの左側にある **省略記号** ボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="66fff-142">Use the **ellipsis** button to the left of the project path field to browse.</span></span> <span data-ttu-id="66fff-143">ファイル システムの操作が完了したら、ターゲットの Unity プロジェクトを含むフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="66fff-143">When you're done navigating your file system, open the folder containing your target Unity project.</span></span>

> [!NOTE]
> <span data-ttu-id="66fff-144">Unity プロジェクト フォルダーを参照するときに表示されるダイアログには、ファイル名として '_' が含まれています。</span><span class="sxs-lookup"><span data-stu-id="66fff-144">The dialog that's displayed when browsing for the Unity project folder contains '_' as the file name.</span></span> <span data-ttu-id="66fff-145">フォルダーを選択できるようにするには、ファイル名に値が必要です。</span><span class="sxs-lookup"><span data-stu-id="66fff-145">There must be a value for the file name to enable the folder to be selected.</span></span>

<span data-ttu-id="66fff-146">**[インポート]** を選択して続行します。</span><span class="sxs-lookup"><span data-stu-id="66fff-146">Select **Import** to continue.</span></span>

> [!NOTE]
> <span data-ttu-id="66fff-147">**[インポート]** ボタンをクリックした後、問題が残っている場合は、簡単なメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="66fff-147">After clicking the **Import** button, if any issues remain a simple message will be displayed.</span></span> <span data-ttu-id="66fff-148">[いいえ] をクリックし、 **[検証]** ボタンを使用して問題を確認し、解決することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="66fff-148">The recommendation is to click No and to use the **Validate** button to view and resolve the issues.</span></span>

<span data-ttu-id="66fff-149">詳細については、[機能のインポート](importing-features.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="66fff-149">For more information, please see [importing features](importing-features.md).</span></span>

## <a name="4-reviewing-and-approving-project-changes"></a><span data-ttu-id="66fff-150">4。プロジェクトの変更点の確認と承認</span><span class="sxs-lookup"><span data-stu-id="66fff-150">4. Reviewing and approving project changes</span></span>

<span data-ttu-id="66fff-151">最後の手順は、マニフェスト ファイルとプロジェクト ファイルに対して提案された変更を確認し、承認することです。</span><span class="sxs-lookup"><span data-stu-id="66fff-151">The final step is reviewing and approving the proposed changes to the manifest and project files:</span></span>

* <span data-ttu-id="66fff-152">マニフェストに対して提案された変更が左側に表示されます</span><span class="sxs-lookup"><span data-stu-id="66fff-152">The proposed changes to the manifest are displayed on the left</span></span>
* <span data-ttu-id="66fff-153">プロジェクトに追加できるファイルは右側に一覧されます</span><span class="sxs-lookup"><span data-stu-id="66fff-153">The files to be added to the project are listed to the right</span></span>
* <span data-ttu-id="66fff-154">**[比較]** ボタンを使用すると、現在のマニフェストと提案された変更を並べて確認できます。</span><span class="sxs-lookup"><span data-stu-id="66fff-154">The **Compare** button allows for side by side viewing of the current manifest and the proposed changes</span></span>

![承認](images/FeatureToolApprovalRequest.png)

<span data-ttu-id="66fff-156">詳細については、[プロジェクトの変更の確認と承認](reviewing-changes.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="66fff-156">For more information, see [reviewing and approving project modifications](reviewing-changes.md).</span></span>

## <a name="5-project-updated"></a><span data-ttu-id="66fff-157">5。プロジェクトの更新</span><span class="sxs-lookup"><span data-stu-id="66fff-157">5. Project updated</span></span>

<span data-ttu-id="66fff-158">提案された変更が承認されると、ターゲットの Unity プロジェクトは、選択した Mixed Reality 機能を参照するように更新されます。</span><span class="sxs-lookup"><span data-stu-id="66fff-158">When the proposed changes are approved, your target Unity project is updated to reference the selected Mixed Reality features:</span></span>

![プロジェクトの更新](images/FeatureToolProjectUpdated.png)

<span data-ttu-id="66fff-160">Unity プロジェクトの **Packages** フォルダーには、機能パッケージ ファイルを含む **MixedReality** サブフォルダーがあり、マニフェストには適切な参照が含まれます。</span><span class="sxs-lookup"><span data-stu-id="66fff-160">The Unity project's **Packages** folder now has a **MixedReality** subfolder with the feature package file(s) and the manifest will contain the appropriate reference(s).</span></span>

<span data-ttu-id="66fff-161">Unity に戻り、新しく選択した機能が読み込まれるまで待ってから、ビルドを開始してください。</span><span class="sxs-lookup"><span data-stu-id="66fff-161">Return to Unity, wait for the new selected features to load, and start building!</span></span>

## <a name="see-also"></a><span data-ttu-id="66fff-162">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="66fff-162">See also</span></span>

- [<span data-ttu-id="66fff-163">機能ツールの構成</span><span class="sxs-lookup"><span data-stu-id="66fff-163">Configuring the feature tool</span></span>](configuring-feature-tool.md)
- [<span data-ttu-id="66fff-164">検出と取得</span><span class="sxs-lookup"><span data-stu-id="66fff-164">Discovery and acquisition</span></span>](discovering-features.md)
- [<span data-ttu-id="66fff-165">機能パッケージの詳細の確認</span><span class="sxs-lookup"><span data-stu-id="66fff-165">Viewing feature package details</span></span>](viewing-package-details.md)
- [<span data-ttu-id="66fff-166">選択したパッケージのインポート</span><span class="sxs-lookup"><span data-stu-id="66fff-166">Importing selected packages</span></span>](importing-features.md)
- [<span data-ttu-id="66fff-167">プロジェクトの変更点の確認と承認</span><span class="sxs-lookup"><span data-stu-id="66fff-167">Reviewing and approving project modifications</span></span>](reviewing-changes.md)
