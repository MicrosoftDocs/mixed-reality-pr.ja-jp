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
# <a name="configuring-the-mixed-reality-feature-tool"></a><span data-ttu-id="0c76c-104">Mixed Reality Feature Tool の構成</span><span class="sxs-lookup"><span data-stu-id="0c76c-104">Configuring the Mixed Reality Feature Tool</span></span>

<span data-ttu-id="0c76c-105">Mixed Reality Feature Tool を使用すると、自由にカスタマイズできる 3 つの異なる設定カテゴリにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0c76c-105">When using the Mixed Reality Feature Tool, you have access to three different settings categories that you can customize at will:</span></span>

* <span data-ttu-id="0c76c-106">[[Download settings]\(ダウンロードの設定\)](#download-settings)</span><span class="sxs-lookup"><span data-stu-id="0c76c-106">[Download settings](#download-settings)</span></span>
* <span data-ttu-id="0c76c-107">[[Feature settings]\(機能の設定\)](#feature-settings)</span><span class="sxs-lookup"><span data-stu-id="0c76c-107">[Feature settings](#feature-settings)</span></span>
* [<span data-ttu-id="0c76c-108">設定のインポート</span><span class="sxs-lookup"><span data-stu-id="0c76c-108">Import settings</span></span>](#import-settings)

![設定](images/FeatureToolSettings.png)

## <a name="download-settings"></a><span data-ttu-id="0c76c-110">［ダウンロードの設定］</span><span class="sxs-lookup"><span data-stu-id="0c76c-110">Download settings</span></span>

### <a name="overwrite-existing-package-files"></a><span data-ttu-id="0c76c-111">[既存のパッケージ ファイルを上書き]</span><span class="sxs-lookup"><span data-stu-id="0c76c-111">Overwrite existing package files</span></span>

<span data-ttu-id="0c76c-112">この設定を有効にすると、パッケージ ファイルが取得されるたびにダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="0c76c-112">Enabling this setting causes package files to be downloaded every time they're acquired.</span></span> 
* <span data-ttu-id="0c76c-113">**ネットワーク帯域幅の使用量を減らすために、このオプションを無効にしておくことをお勧めします**</span><span class="sxs-lookup"><span data-stu-id="0c76c-113">**We recommend leaving this option disabled to reduce network bandwidth usage**</span></span>
* <span data-ttu-id="0c76c-114">既定では、以前に取得したパッケージ ファイルは再ダウンロードされません</span><span class="sxs-lookup"><span data-stu-id="0c76c-114">By default, previously acquired package files aren't re-downloaded</span></span>

### <a name="package-cache"></a><span data-ttu-id="0c76c-115">[Package cache]\(パッケージのキャッシュ\)</span><span class="sxs-lookup"><span data-stu-id="0c76c-115">Package cache</span></span>

<span data-ttu-id="0c76c-116">機能パッケージがダウンロードされる場所を更新するには、この設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="0c76c-116">Change this setting to update the location where feature packages are downloaded.</span></span>

> [!NOTE]
> <span data-ttu-id="0c76c-117">このリリースでは、この設定は **読み取り専用** です。</span><span class="sxs-lookup"><span data-stu-id="0c76c-117">This setting is **read-only** in this release.</span></span> <span data-ttu-id="0c76c-118">今後のリリースでは、この設定を構成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0c76c-118">Future releases may make this setting configurable.</span></span>

## <a name="feature-settings"></a><span data-ttu-id="0c76c-119">[Feature settings]\(機能の設定\)</span><span class="sxs-lookup"><span data-stu-id="0c76c-119">Feature settings</span></span>

### <a name="include-preview-releases"></a><span data-ttu-id="0c76c-120">[Include preview releases]\(プレビュー リリースを含める\)</span><span class="sxs-lookup"><span data-stu-id="0c76c-120">Include preview releases</span></span>

<span data-ttu-id="0c76c-121">プレビュー リリースを取得するには、この設定を有効にします。</span><span class="sxs-lookup"><span data-stu-id="0c76c-121">Enable this setting to acquire preview releases.</span></span>
* <span data-ttu-id="0c76c-122">既定では、プレビュー リリースは Mixed Reality Feature Tool に表示されません。</span><span class="sxs-lookup"><span data-stu-id="0c76c-122">By default, preview releases aren't shown in the Mixed Reality Feature Tool</span></span> 

> [!NOTE]
> <span data-ttu-id="0c76c-123">プレビュー リリースは、パッケージ バージョンに **"-preview"** の指定が含まれているものと定義されています。</span><span class="sxs-lookup"><span data-stu-id="0c76c-123">A preview release is defined as containing the **"-preview"** designation in the package version.</span></span>

## <a name="import-settings"></a><span data-ttu-id="0c76c-124">設定のインポート</span><span class="sxs-lookup"><span data-stu-id="0c76c-124">Import settings</span></span>

### <a name="replace-existing-package-files"></a><span data-ttu-id="0c76c-125">[Replace existing package files]\(既存のパッケージ ファイルを置き換える\)</span><span class="sxs-lookup"><span data-stu-id="0c76c-125">Replace existing package files</span></span>

<span data-ttu-id="0c76c-126">Mixed Reality Feature Tool の既定では、ファイル サイズと不要な計算を減らすために、インポートされているパッケージの以前のコピーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="0c76c-126">By default, the Mixed Reality Feature Tool removes previous copies of the packages being imported to reduce the file size and unnecessary computations.</span></span> 
* <span data-ttu-id="0c76c-127">すべてのバージョンを保持するには、この設定をオフにします</span><span class="sxs-lookup"><span data-stu-id="0c76c-127">Uncheck this setting to keep all versions</span></span>

### <a name="project-relative-import-path"></a><span data-ttu-id="0c76c-128">[Project relative import path]\(プロジェクトの相対インポート パス\)</span><span class="sxs-lookup"><span data-stu-id="0c76c-128">Project relative import path</span></span>

<span data-ttu-id="0c76c-129">インポート時に機能パッケージがコピーされるプロジェクト フォルダーのパスを更新するには、この設定を変更します。</span><span class="sxs-lookup"><span data-stu-id="0c76c-129">Change this setting to update project folder path where feature packages are copied on import.</span></span> 
* <span data-ttu-id="0c76c-130">たとえば、プロジェクト フォルダーが **C:\GalaxyExplorer** の場合、完全修飾インポート パスは **C:\GalaxyExplorer\Packages\MixedReality** になります。</span><span class="sxs-lookup"><span data-stu-id="0c76c-130">For example, if the project folder is **C:\GalaxyExplorer**, the fully qualified import path will be **C:\GalaxyExplorer\Packages\MixedReality**.</span></span>

> [!NOTE]
> <span data-ttu-id="0c76c-131">このリリースでは、この設定は **読み取り専用** です。</span><span class="sxs-lookup"><span data-stu-id="0c76c-131">This setting is **read-only** in this release.</span></span> <span data-ttu-id="0c76c-132">今後のリリースでは、この設定を構成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0c76c-132">Future releases may make this setting configurable.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c76c-133">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="0c76c-133">See also</span></span>

- [<span data-ttu-id="0c76c-134">Mixed Reality Feature Tool へようこそ</span><span class="sxs-lookup"><span data-stu-id="0c76c-134">Welcome to the Mixed Reality Feature Tool</span></span>](welcome-to-mr-feature-tool.md)