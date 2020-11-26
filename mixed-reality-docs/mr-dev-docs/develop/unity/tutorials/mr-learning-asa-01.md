---
title: Azure Spatial Anchors チュートリアル - 1. Azure Spatial Anchors チュートリアルの概要
description: このコースを完了すると、Mixed Reality アプリケーション内に Azure Spatial Anchors を実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー, iOS, Android, Windows 10, ARCore, macOS, Android ビルド サポート, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 005bbf3f9ecb7ed7f15f78d4042b4090f00edca7
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679401"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a><span data-ttu-id="79392-105">1. Azure Spatial Anchors チュートリアルの概要</span><span class="sxs-lookup"><span data-stu-id="79392-105">1. Introduction to the Azure Spatial Anchors tutorials</span></span>

## <a name="overview"></a><span data-ttu-id="79392-106">概要</span><span class="sxs-lookup"><span data-stu-id="79392-106">Overview</span></span>

<span data-ttu-id="79392-107">Azure Spatial Anchors チュートリアルにようこそ。</span><span class="sxs-lookup"><span data-stu-id="79392-107">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="79392-108">このチュートリアル シリーズをとおして、<a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) の基礎と完全な複合現実体験を現実の世界で実現する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="79392-108">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="79392-109">プロジェクトを Android と iOS にデプロイする方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="79392-109">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="79392-110">このシリーズのチュートリアル:</span><span class="sxs-lookup"><span data-stu-id="79392-110">Tutorials in this series:</span></span>

1. <span data-ttu-id="79392-111">[はじめに](mr-learning-asa-01.md) (このページです)</span><span class="sxs-lookup"><span data-stu-id="79392-111">[Introduction](mr-learning-asa-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="79392-112">Azure Spatial Anchors をお使いになる前に</span><span class="sxs-lookup"><span data-stu-id="79392-112">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="79392-113">Azure Spatial Anchors の保存、取得、共有</span><span class="sxs-lookup"><span data-stu-id="79392-113">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="79392-114">Azure Spatial Anchors のフィードバックの表示</span><span class="sxs-lookup"><span data-stu-id="79392-114">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="79392-115">Android と iOS 用の Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="79392-115">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="79392-116">目標</span><span class="sxs-lookup"><span data-stu-id="79392-116">Objectives</span></span>

* <span data-ttu-id="79392-117">空間アンカーを作成し、Azure から取得する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="79392-117">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="79392-118">アプリ セッション間で空間的な位置合わせを実現する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="79392-118">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="79392-119">複数のデバイス間で空間的な位置合わせを実現する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="79392-119">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="79392-120">プロジェクトを準備し、構築し、Android と iOS にデプロイする方法を学習する</span><span class="sxs-lookup"><span data-stu-id="79392-120">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="79392-121">前提条件</span><span class="sxs-lookup"><span data-stu-id="79392-121">Prerequisites</span></span>

* <span data-ttu-id="79392-122">正しい[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 コンピューター</span><span class="sxs-lookup"><span data-stu-id="79392-122">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="79392-123">Windows 10 SDK 10.0.18362.0 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="79392-123">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="79392-124">[開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="79392-124">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="79392-125">Unity 2019.3.15 がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="79392-125"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="79392-126">「[Spatial Anchors リソースを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)」セクション ([クイック スタート:Azure Spatial Anchors を使用する Unity HoloLens アプリを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) チュートリアルにあります) を完了します。</span><span class="sxs-lookup"><span data-stu-id="79392-126">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="79392-127">[入門チュートリアル](mr-learning-base-01.md) シリーズを完了しているか、以前に Unity と MRTK の基本操作を経験していること</span><span class="sxs-lookup"><span data-stu-id="79392-127">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="79392-128">HoloLens に加えて Android にもデプロイする場合</span><span class="sxs-lookup"><span data-stu-id="79392-128">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="79392-129">Windows コンピューターか macOS コンピューターに USB 接続された、<a href="https://developer.android.com/studio/debug/dev-options" target="_blank">開発者向けオプションが有効</a>に設定された <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 対応</a>の Android デバイス</span><span class="sxs-lookup"><span data-stu-id="79392-129">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="79392-130">Unity 2019.3.15 がインストールされ、Android ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="79392-130"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the Android Build Support module added</span></span>
* <span data-ttu-id="79392-131">HoloLens に加えて iOS にもデプロイする場合</span><span class="sxs-lookup"><span data-stu-id="79392-131">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="79392-132"><a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> および <a href="https://cocoapods.org" target="_blank">CocoaPods</a> の最新バージョンがインストールされた macOS コンピューター</span><span class="sxs-lookup"><span data-stu-id="79392-132">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="79392-133">macOS コンピューターに USB 接続された、<a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 互換</a> iOS デバイス</span><span class="sxs-lookup"><span data-stu-id="79392-133">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="79392-134">2019.3.15 がインストールされ、iOS ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="79392-134"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.3.15 installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="79392-135">このチュートリアル シリーズで推奨されている Mixed Reality Toolkit のバージョンは MRTK 2.4.0 です。</span><span class="sxs-lookup"><span data-stu-id="79392-135">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.4.0.</span></span>

> [!CAUTION]
> <span data-ttu-id="79392-136">このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.3.15 です。</span><span class="sxs-lookup"><span data-stu-id="79392-136">The recommended Unity version for this tutorial series is Unity 2019.3.15.</span></span> <span data-ttu-id="79392-137">これは、上のリンクされた前提条件に記載されている Unity のバージョン要件に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="79392-137">This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="79392-138">次のチュートリアル:2.Azure Spatial Anchors をお使いになる前に</span><span class="sxs-lookup"><span data-stu-id="79392-138">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
