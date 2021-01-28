---
title: MRTK チュートリアルの概要
description: このコースでは、Mixed Reality ツールキット (MRTK) を使用して Mixed Reality アプリケーションを最初から作成する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, ソルバー, 視線追跡, 音声コマンド
ms.localizationpriority: high
ms.openlocfilehash: a917aea812c262e3589110a29e2399da4c1e5348
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2021
ms.locfileid: "98579271"
---
# <a name="1-introduction-to-the-mrtk-tutorials"></a><span data-ttu-id="e0cb4-104">1.MRTK チュートリアルの概要</span><span class="sxs-lookup"><span data-stu-id="e0cb4-104">1. Introduction to the MRTK tutorials</span></span>

<span data-ttu-id="e0cb4-105">入門チュートリアル シリーズへようこそ。</span><span class="sxs-lookup"><span data-stu-id="e0cb4-105">Welcome to the Getting Started tutorial series!</span></span> <span data-ttu-id="e0cb4-106">これらのチュートリアルでは、Mixed Reality Toolkit (MRTK) と、それらの一部の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="e0cb4-106">Over the course of these tutorials, you'll learn about the Mixed Reality Toolkit (MRTK) and some of the features it has to offer.</span></span> <span data-ttu-id="e0cb4-107">NASA の火星探査ローバーをモデルとするホログラムをユーザーが探ることができる、複合現実のエクスペリエンスも構築します。</span><span class="sxs-lookup"><span data-stu-id="e0cb4-107">You'll also build a mixed reality experience where the user can explore a hologram modeled after NASA's Mars Curiosity Rover.</span></span> <span data-ttu-id="e0cb4-108">このシリーズの終わりには、MRTK について、およびこれでどのようにご自分の開発プロセスをスピード化できるかについて深く理解できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e0cb4-108">By the end of this series, you'll have a firm grasp of MRTK and how it can speed up your development process.</span></span>

<span data-ttu-id="e0cb4-109">このシリーズのチュートリアルは連続してものであるため、正しい順序で進めてください。</span><span class="sxs-lookup"><span data-stu-id="e0cb4-109">Tutorials in this series are meant to be sequential, so please go through them in the correct order:</span></span>

1. <span data-ttu-id="e0cb4-110">[はじめに](mr-learning-base-01.md) (このページです)</span><span class="sxs-lookup"><span data-stu-id="e0cb4-110">[Introduction](mr-learning-base-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="e0cb4-111">プロジェクトの初期化と最初のアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="e0cb4-111">Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
3. [<span data-ttu-id="e0cb4-112">MRTK プロファイルの構成</span><span class="sxs-lookup"><span data-stu-id="e0cb4-112">Configuring the MRTK profiles</span></span>](mr-learning-base-03.md)
4. [<span data-ttu-id="e0cb4-113">シーンへのオブジェクトの配置</span><span class="sxs-lookup"><span data-stu-id="e0cb4-113">Positioning objects in the scene</span></span>](mr-learning-base-04.md)
5. [<span data-ttu-id="e0cb4-114">ソルバーを使用した動的なコンテンツの作成</span><span class="sxs-lookup"><span data-stu-id="e0cb4-114">Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
6. [<span data-ttu-id="e0cb4-115">ユーザー インターフェイスの作成</span><span class="sxs-lookup"><span data-stu-id="e0cb4-115">Creating user interfaces</span></span>](mr-learning-base-06.md)
7. [<span data-ttu-id="e0cb4-116">3D オブジェクトの操作</span><span class="sxs-lookup"><span data-stu-id="e0cb4-116">Interacting with 3D objects</span></span>](mr-learning-base-07.md)
8. [<span data-ttu-id="e0cb4-117">視線追跡の使用</span><span class="sxs-lookup"><span data-stu-id="e0cb4-117">Using eye-tracking</span></span>](mr-learning-base-08.md)
9. [<span data-ttu-id="e0cb4-118">音声コマンドの使用</span><span class="sxs-lookup"><span data-stu-id="e0cb4-118">Using voice commands</span></span>](mr-learning-base-09.md)

## <a name="objectives"></a><span data-ttu-id="e0cb4-119">目標</span><span class="sxs-lookup"><span data-stu-id="e0cb4-119">Objectives</span></span>

* <span data-ttu-id="e0cb4-120">MRTK 用に Unity を構成する方法について学ぶ</span><span class="sxs-lookup"><span data-stu-id="e0cb4-120">Learn how to configure Unity for MRTK</span></span>
* <span data-ttu-id="e0cb4-121">ご自分のデバイスの構築および展開方法について学習する</span><span class="sxs-lookup"><span data-stu-id="e0cb4-121">Learn how to build and deploy to your device</span></span>
* <span data-ttu-id="e0cb4-122">MRTK の一部の主要機能の使用方法について学習する</span><span class="sxs-lookup"><span data-stu-id="e0cb4-122">Learn how to use some of MRTK's key features</span></span>
* <span data-ttu-id="e0cb4-123">完全な複合現実エクスペリエンスを構築する</span><span class="sxs-lookup"><span data-stu-id="e0cb4-123">Create a complete mixed reality experience</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e0cb4-124">前提条件</span><span class="sxs-lookup"><span data-stu-id="e0cb4-124">Prerequisites</span></span>

* <span data-ttu-id="e0cb4-125">正しい[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="e0cb4-125">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="e0cb4-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="e0cb4-126">[Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk/) 10.0.18362.0 or later</span></span>
* <span data-ttu-id="e0cb4-127">[開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="e0cb4-127">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>

* <span data-ttu-id="e0cb4-128">Unity 2019 LTS がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="e0cb4-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="e0cb4-129">このチュートリアル シリーズで推奨される MRTK のバージョンは MRTK 2.5.1 です。</span><span class="sxs-lookup"><span data-stu-id="e0cb4-129">The recommended MRTK version for this tutorial series is MRTK 2.5.1.</span></span>

> [!CAUTION]
> <span data-ttu-id="e0cb4-130">このチュートリアル シリーズで推奨されている Unity バージョンは、Unity 2019 LTS です。</span><span class="sxs-lookup"><span data-stu-id="e0cb4-130">The recommended Unity version for this tutorial series is Unity 2019 LTS.</span></span> <span data-ttu-id="e0cb4-131">これは、上の前提条件のリンクに記載されているすべての Unity のバージョンに優先されます。</span><span class="sxs-lookup"><span data-stu-id="e0cb4-131">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e0cb4-132">次のチュートリアル:2.プロジェクトの初期化と最初のアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="e0cb4-132">Next Tutorial: 2. Initializing your project and deploying your first application</span></span>](mr-learning-base-02.md)
