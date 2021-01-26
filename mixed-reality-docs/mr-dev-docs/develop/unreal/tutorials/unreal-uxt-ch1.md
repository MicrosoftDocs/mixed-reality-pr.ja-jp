---
title: 1. はじめに
description: Unreal Engine 4 と Mixed Reality ツールキット UX ツール プラグインを使用してチェス アプリを構築するためのチュートリアル シリーズのパート 6 の 1
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, Mixed Reality, チュートリアル, はじめに, mrtk, uxt, UX ツール, ドキュメント, Mixed Reality ヘッドセット, Windows Mixed Reality ヘッドセット, 仮想現実ヘッドセット
ms.openlocfilehash: a46b9fef96f75f3d80b9ebbd5cbd724730374b41
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580560"
---
# <a name="1-getting-started"></a><span data-ttu-id="05b4b-104">1.はじめに</span><span class="sxs-lookup"><span data-stu-id="05b4b-104">1. Getting started</span></span>

<span data-ttu-id="05b4b-105">Mixed Reality を初めて使用する場合でも、経験豊富なプロの方でも、ここは [HoloLens 2](../../../index.yml) と [Unreal Engine](https://www.unrealengine.com/en-US/) の体験を始めるのに適した場所です。</span><span class="sxs-lookup"><span data-stu-id="05b4b-105">Whether you're new to mixed reality or a seasoned pro, you're in the right place to start your [HoloLens 2](../../../index.yml) and [Unreal Engine](https://www.unrealengine.com/en-US/) journey.</span></span> <span data-ttu-id="05b4b-106">このチュートリアル シリーズでは、[Unreal 用 Mixed Reality ツールキット](https://github.com/microsoft/MixedRealityToolkit-Unreal)の一部である [UX Tools プラグイン](https://github.com/microsoft/MixedReality-UXTools-Unreal)を使用してインタラクティブなチェス アプリを構築する方法を、1 ステップずつ説明します。</span><span class="sxs-lookup"><span data-stu-id="05b4b-106">This tutorial series will give you a step-by-step guide on how to build an interactive chess app with the [UX Tools plugin](https://github.com/microsoft/MixedReality-UXTools-Unreal) - part of the [Mixed Reality Toolkit for Unreal](https://github.com/microsoft/MixedRealityToolkit-Unreal).</span></span> <span data-ttu-id="05b4b-107">プラグインは、コード、ブループリント、例を使用してプロジェクトに一般的な UX 機能を追加するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="05b4b-107">The plugin will help you add common UX features to your projects with code, blueprints, and examples.</span></span> 

![ビューポートの終わりのシーン](images/unreal-uxt/5-endscene.PNG)

<span data-ttu-id="05b4b-109">シリーズが完了するまでに、次のことを体験できます。</span><span class="sxs-lookup"><span data-stu-id="05b4b-109">By the end of the series you'll have experience with:</span></span>
* <span data-ttu-id="05b4b-110">新しいプロジェクトの開始</span><span class="sxs-lookup"><span data-stu-id="05b4b-110">Starting a new project</span></span>
* <span data-ttu-id="05b4b-111">Mixed Reality 用の設定</span><span class="sxs-lookup"><span data-stu-id="05b4b-111">Setting up for mixed reality</span></span>
* <span data-ttu-id="05b4b-112">ユーザー入力の操作</span><span class="sxs-lookup"><span data-stu-id="05b4b-112">Working with user input</span></span>
* <span data-ttu-id="05b4b-113">ボタンの追加</span><span class="sxs-lookup"><span data-stu-id="05b4b-113">Adding buttons</span></span>
* <span data-ttu-id="05b4b-114">エミュレーターまたはデバイスでの再生</span><span class="sxs-lookup"><span data-stu-id="05b4b-114">Playing on an emulator or device</span></span>

## <a name="prerequisites"></a><span data-ttu-id="05b4b-115">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="05b4b-115">Prerequisites</span></span>

<span data-ttu-id="05b4b-116">開始する前に、次のものがインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="05b4b-116">Make sure you've installed the following before jumping in:</span></span>
* <span data-ttu-id="05b4b-117">Windows 10 1809 以降</span><span class="sxs-lookup"><span data-stu-id="05b4b-117">Windows 10 1809 or later</span></span>
* <span data-ttu-id="05b4b-118">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="05b4b-118">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="05b4b-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 以降</span><span class="sxs-lookup"><span data-stu-id="05b4b-119">[Unreal Engine](https://www.unrealengine.com/en-US/get-now) 4.25 or later</span></span>
* <span data-ttu-id="05b4b-120">[開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) Microsoft HoloLens 2 デバイスまたは[エミュレーター](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)</span><span class="sxs-lookup"><span data-stu-id="05b4b-120">Microsoft HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) or [Emulator](../../platform-capabilities-and-apis/using-the-hololens-emulator.md#hololens-2-emulator-overview)</span></span>
* <span data-ttu-id="05b4b-121">以下のワークロードを含む Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="05b4b-121">Visual Studio 2019 with the workloads below</span></span>

### <a name="installing-visual-studio-2019"></a><span data-ttu-id="05b4b-122">Visual Studio 2019 のインストール</span><span class="sxs-lookup"><span data-stu-id="05b4b-122">Installing Visual Studio 2019</span></span>

<span data-ttu-id="05b4b-123">最初に、必要な Visual Studio パッケージがすべてセットアップされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="05b4b-123">First, make sure your setup with all the required Visual Studio packages:</span></span>
1. <span data-ttu-id="05b4b-124">[Visual Studio 2019](https://visualstudio.microsoft.com/downloads/) の最新バージョンのインストール</span><span class="sxs-lookup"><span data-stu-id="05b4b-124">Install the latest version of [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/)</span></span>
1. <span data-ttu-id="05b4b-125">次の[ワークロード](/visualstudio/install/modify-visual-studio#modify-workloads)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="05b4b-125">Install the following [workloads](/visualstudio/install/modify-visual-studio#modify-workloads):</span></span>
    * <span data-ttu-id="05b4b-126">C++ によるデスクトップ開発</span><span class="sxs-lookup"><span data-stu-id="05b4b-126">Desktop development with C++</span></span>
    * <span data-ttu-id="05b4b-127">.NET デスクトップ開発</span><span class="sxs-lookup"><span data-stu-id="05b4b-127">.NET desktop development</span></span>
    * <span data-ttu-id="05b4b-128">ユニバーサル Windows プラットフォームの開発</span><span class="sxs-lookup"><span data-stu-id="05b4b-128">Universal Windows Platform development</span></span>
1. <span data-ttu-id="05b4b-129">ユニバーサル Windows プラットフォームの開発を展開し、以下を選択します。</span><span class="sxs-lookup"><span data-stu-id="05b4b-129">Expand Universal Windows Platform development and select:</span></span> 
    * <span data-ttu-id="05b4b-130">USB デバイスの接続</span><span class="sxs-lookup"><span data-stu-id="05b4b-130">USB Device Connectivity</span></span>
    * <span data-ttu-id="05b4b-131">C++ (v142) ユニバーサル Windows プラットフォーム ツール</span><span class="sxs-lookup"><span data-stu-id="05b4b-131">C++ (v142) Universal Windows Platform tools</span></span>

1. <span data-ttu-id="05b4b-132">次の[コンポーネント](/visualstudio/install/modify-visual-studio#modify-individual-components)をインストールします。</span><span class="sxs-lookup"><span data-stu-id="05b4b-132">Install the following [components](/visualstudio/install/modify-visual-studio#modify-individual-components):</span></span>
    * <span data-ttu-id="05b4b-133">コンパイラ、ビルド ツール、ランタイム > MSVC v142 - VS 2019 C++ ARM64 ビルド ツール (最新バージョン)</span><span class="sxs-lookup"><span data-stu-id="05b4b-133">Compilers, build tools, and runtimes > MSVC v142 - VS 2019 C++ ARM64 build tools (latest version)</span></span>

<span data-ttu-id="05b4b-134">次の図を使用して、インストールを確認します。</span><span class="sxs-lookup"><span data-stu-id="05b4b-134">You can confirm the installation with the following picture</span></span>

![VS インストーラーでの重要なティック](images/unreal-uxt/1-install-the-tools.png)

<span data-ttu-id="05b4b-136">以上で作業は終了です。</span><span class="sxs-lookup"><span data-stu-id="05b4b-136">That's it!</span></span> <span data-ttu-id="05b4b-137">これで、チェス プロジェクトを開始するためのすべての設定が完了しました。</span><span class="sxs-lookup"><span data-stu-id="05b4b-137">You're all set to move on to starting the chess project.</span></span>

[<span data-ttu-id="05b4b-138">次のセクション: 2.プロジェクトと最初のアプリケーションの初期化</span><span class="sxs-lookup"><span data-stu-id="05b4b-138">Next section: 2. Initializing your project and first application</span></span>](unreal-uxt-ch2.md)