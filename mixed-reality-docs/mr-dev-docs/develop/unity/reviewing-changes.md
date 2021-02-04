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
# <a name="authorizing-project-changes"></a><span data-ttu-id="ba3b3-104">プロジェクトの変更の承認</span><span class="sxs-lookup"><span data-stu-id="ba3b3-104">Authorizing project changes</span></span>

<span data-ttu-id="ba3b3-105">Unity プロジェクトを変更する前に、マニフェスト ファイルとプロジェクト ファイルに対する変更を確認し、承認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba3b3-105">Before modifying the Unity project, changes to the manifest and project files need to be reviewed and approved:</span></span>

![承認の要求](images/FeatureToolApprovalRequest.png)

## <a name="manifest"></a><span data-ttu-id="ba3b3-107">Manifest</span><span class="sxs-lookup"><span data-stu-id="ba3b3-107">Manifest</span></span>

<span data-ttu-id="ba3b3-108">提案されたマニフェストの変更は、左側の **[Manifest]\(マニフェスト\)** 列で確認できます。</span><span class="sxs-lookup"><span data-stu-id="ba3b3-108">The proposed manifest changes can be viewed in the **Manifest** column on the left.</span></span> <span data-ttu-id="ba3b3-109">内容は、プロジェクト マニフェスト (**Packages/manifest.json**) に書き込まれる内容とまったく同じです。</span><span class="sxs-lookup"><span data-stu-id="ba3b3-109">The contents are exactly what will be written to the project manifest (**Packages/manifest.json**):</span></span>

![マニフェストのプレビュー](images/ManifestPreview.png)

## <a name="files-to-be-copied-into-the-project"></a><span data-ttu-id="ba3b3-111">プロジェクトにコピーされるファイル</span><span class="sxs-lookup"><span data-stu-id="ba3b3-111">Files to be copied into the project</span></span>

<span data-ttu-id="ba3b3-112">右側の **[Files to be copied into the project]\(プロジェクトにコピーされるファイル\)** には、Unity プロジェクトにコピーされる特定の機能パッケージ ファイルが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="ba3b3-112">The **Files to be copied into the project** section on the right lists the specific feature package files that will be copied into the Unity project:</span></span>

![コピーされるファイルが表示されたマニフェストのプレビュー](images/FilesToCopy.png)

## <a name="compare-manifests"></a><span data-ttu-id="ba3b3-114">マニフェストを比較する</span><span class="sxs-lookup"><span data-stu-id="ba3b3-114">Compare manifests</span></span>

<span data-ttu-id="ba3b3-115">**[Compare]\(比較\)** を選択すると、提案されたすべての変更を横に表示して比較することができます。</span><span class="sxs-lookup"><span data-stu-id="ba3b3-115">You can see a detailed side-by-side comparison of all proposed changes by selecting **Compare**:</span></span>

![マニフェストを比較する](images/FeatureToolCompareManifest.png)

## <a name="approving-changes"></a><span data-ttu-id="ba3b3-117">変更の承認</span><span class="sxs-lookup"><span data-stu-id="ba3b3-117">Approving changes</span></span>

<span data-ttu-id="ba3b3-118">提案された変更が承認されると、一覧にあるファイルが Unity プロジェクトにコピーされ、これらのファイルを参照してマニフェストが更新されます。</span><span class="sxs-lookup"><span data-stu-id="ba3b3-118">When the proposed changes are approved, the listed files will be copied into the Unity project and the manifest will be updated with references to these files.</span></span>

> [!NOTE]
> <span data-ttu-id="ba3b3-119">機能パッケージ (\*.tgz) ファイルをソース管理に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ba3b3-119">The feature package (\*.tgz) files should be added to source control.</span></span> <span data-ttu-id="ba3b3-120">これらは相対パスを使用して参照されるため、開発チームは機能とマニフェストの変更を簡単に共有できます。</span><span class="sxs-lookup"><span data-stu-id="ba3b3-120">They are referenced using a relative path to enable development teams to easily share features and manifest changes.</span></span>

 <span data-ttu-id="ba3b3-121">変更の過程で、現在の **manifest.json** ファイルがバックアップされます。</span><span class="sxs-lookup"><span data-stu-id="ba3b3-121">As part of the modifications, the current **manifest.json** file will be backed up.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba3b3-122">マニフェストのバックアップを表示すると、最も古いものには **manifest.json.backup** という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="ba3b3-122">When viewing the manifest backups, the oldest will be called **manifest.json.backup**.</span></span> <span data-ttu-id="ba3b3-123">新しいバックアップには、ゼロ (0) から始まる数値が付加されます。</span><span class="sxs-lookup"><span data-stu-id="ba3b3-123">Newer backups will be annotated with a numeric value, beginning with zero (0).</span></span>

## <a name="going-back-to-the-previous-step"></a><span data-ttu-id="ba3b3-124">前の手順に戻る</span><span class="sxs-lookup"><span data-stu-id="ba3b3-124">Going back to the previous step</span></span>

<span data-ttu-id="ba3b3-125">機能の選択を変更する必要がある場合は、 **[Go back]\(戻る\)** を選択して[インポート](importing-features.md)手順に戻ります。</span><span class="sxs-lookup"><span data-stu-id="ba3b3-125">If you need to make changes to your feature selections, use **Go Back** to return to the [import](importing-features.md) step.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba3b3-126">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="ba3b3-126">See also</span></span>

- [<span data-ttu-id="ba3b3-127">Mixed Reality Feature Tool へようこそ</span><span class="sxs-lookup"><span data-stu-id="ba3b3-127">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)
- [<span data-ttu-id="ba3b3-128">選択したパッケージのインポート</span><span class="sxs-lookup"><span data-stu-id="ba3b3-128">Importing selected packages</span></span>](importing-features.md)
