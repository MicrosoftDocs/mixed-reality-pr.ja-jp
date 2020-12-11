---
title: 1. はじめに
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用してチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 1
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, はじめに, mrtk, uxt, UX ツール, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: 465215efd953c0acb9f2d80a2905ee06963c5f8c
ms.sourcegitcommit: 32cb81eee976e73cd661c2b347691c37865a60bc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/04/2020
ms.locfileid: "96609723"
---
# <a name="1-getting-started"></a><span data-ttu-id="26f18-104">1.はじめに</span><span class="sxs-lookup"><span data-stu-id="26f18-104">1. Getting started</span></span>

<span data-ttu-id="26f18-105">Mixed Reality を初めて使用する場合でも、経験豊富なプロの方でも、ここは [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) と [Unreal Engine](https://www.unrealengine.com/en-US/) の体験を始めるのに適した場所です。</span><span class="sxs-lookup"><span data-stu-id="26f18-105">Whether you're new to mixed reality or a seasoned pro, you're in the right place to start your [HoloLens 2](https://docs.microsoft.com/windows/mixed-reality/) and [Unreal Engine](https://www.unrealengine.com/en-US/) journey.</span></span> <span data-ttu-id="26f18-106">このチュートリアル シリーズでは、[Unreal 用 Mixed Reality ツールキット](https://github.com/microsoft/MixedRealityToolkit-Unreal)の一部である [UX Tools プラグイン](https://github.com/microsoft/MixedReality-UXTools-Unreal)を使用してインタラクティブなチェス アプリを構築する方法を、1 ステップずつ説明します。</span><span class="sxs-lookup"><span data-stu-id="26f18-106">This tutorial series will give you a step-by-step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="26f18-107">プラグインは、コード、ブループリント、例を使用してプロジェクトに一般的な UX 機能を追加するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="26f18-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![ビューポートの終わりのシーン](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="26f18-109">シリーズが完了するまでに、次のことを体験できます。</span><span class="sxs-lookup"><span data-stu-id="26f18-109">By the end of the series you'll have experience with:</span></span>
* <span data-ttu-id="26f18-110">新しいプロジェクトの開始</span><span class="sxs-lookup"><span data-stu-id="26f18-110">Starting a new project</span></span>
* <span data-ttu-id="26f18-111">Mixed Reality 用の設定</span><span class="sxs-lookup"><span data-stu-id="26f18-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="26f18-112">ユーザー入力の操作</span><span class="sxs-lookup"><span data-stu-id="26f18-112">Working with user input</span></span>
* <span data-ttu-id="26f18-113">ボタンの追加</span><span class="sxs-lookup"><span data-stu-id="26f18-113">Adding buttons</span></span>
* <span data-ttu-id="26f18-114">エミュレーターまたはデバイスでの再生</span><span class="sxs-lookup"><span data-stu-id="26f18-114">Playing on an emulator or device</span></span>

## <a name="prerequisites"></a><span data-ttu-id="26f18-115">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="26f18-115">Prerequisites</span></span>

<span data-ttu-id="26f18-116">開始する前に、次のものがインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="26f18-116">Make sure you've installed the following before jumping in:</span></span>
* <span data-ttu-id="26f18-117">Windows 10 1809 以降</span><span class="sxs-lookup"><span data-stu-id="26f18-117">Windows 10 1809 or later</span></span>
* <span data-ttu-id="26f18-118">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="26f18-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="26f18-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 以降</span><span class="sxs-lookup"><span data-stu-id="26f18-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="26f18-120">[開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) Microsoft HoloLens 2 デバイスまたはエミュレーター</span><span class="sxs-lookup"><span data-stu-id="26f18-120">Microsoft HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) or Emulator</span></span>
* <span data-ttu-id="26f18-121">以下のワークロードを含む Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="26f18-121">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="26f18-122">Visual Studio 2019 のインストール</span><span class="sxs-lookup"><span data-stu-id="26f18-122">Installing Visual Studio 2019</span></span>

<span data-ttu-id="26f18-123">最初に、必要な Visual Studio パッケージがすべてセットアップされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="26f18-123">First, make sure your setup with all the required Visual Studio packages:</span></span>
1. <span data-ttu-id="26f18-124">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) の最新バージョンのインストール</span><span class="sxs-lookup"><span data-stu-id="26f18-124">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
2. <span data-ttu-id="26f18-125">次の[ワークロード](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="26f18-125">Install the following [workloads](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-workloads):</span></span>
    * <span data-ttu-id="26f18-126">C++ によるデスクトップ開発</span><span class="sxs-lookup"><span data-stu-id="26f18-126">Desktop development with C++</span></span>
    * <span data-ttu-id="26f18-127">.NET デスクトップ開発</span><span class="sxs-lookup"><span data-stu-id="26f18-127">.NET desktop development</span></span>
    * <span data-ttu-id="26f18-128">ユニバーサル Windows プラットフォームの開発</span><span class="sxs-lookup"><span data-stu-id="26f18-128">Universal Windows Platform development</span></span>

3. <span data-ttu-id="26f18-129">次の[コンポーネント](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="26f18-129">Install the following [components](https://docs.microsoft.com/visualstudio/install/modify-visual-studio?#modify-individual-components):</span></span>
    * <span data-ttu-id="26f18-130">コンパイラ、ビルド ツール、ランタイム > MSVC v142 - VS 2019 C++ ARM64 ビルド ツール (最新バージョン)</span><span class="sxs-lookup"><span data-stu-id="26f18-130">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="26f18-131">以上で作業は終了です。</span><span class="sxs-lookup"><span data-stu-id="26f18-131">That's it!</span></span> <span data-ttu-id="26f18-132">これで、チェス プロジェクトを開始するためのすべての設定が完了しました。</span><span class="sxs-lookup"><span data-stu-id="26f18-132">You're all set to move on to starting the chess project.</span></span>

[<span data-ttu-id="26f18-133">次のセクション: 2.プロジェクトと最初のアプリケーションの初期化</span><span class="sxs-lookup"><span data-stu-id="26f18-133">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)