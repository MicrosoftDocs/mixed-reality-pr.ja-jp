---
title: マルチユーザー機能のチュートリアルの概要
description: このコースを完了すると、HoloLens 2 アプリケーション内で共有マルチユーザー エクスペリエンスを実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, マルチユーザー機能, Photon, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー
ms.localizationpriority: high
ms.openlocfilehash: 90c5b2ee3f25c39fc644aee0fbbf49643f7d2a59
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590174"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a><span data-ttu-id="d2891-104">1. マルチユーザー機能のチュートリアルの概要</span><span class="sxs-lookup"><span data-stu-id="d2891-104">1. Introduction to the Multi-user capabilities tutorials</span></span>

<span data-ttu-id="d2891-105">マルチユーザー機能のチュートリアルへようこそ。</span><span class="sxs-lookup"><span data-stu-id="d2891-105">Welcome to the Multi-User Capabilities tutorials!</span></span> <span data-ttu-id="d2891-106">このチュートリアル シリーズでは、<a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN) を使用したマルチユーザー エクスペリエンスの構築方法の基礎について学習します。</span><span class="sxs-lookup"><span data-stu-id="d2891-106">Through this tutorial series, you will learn the fundamentals of building a multi-user experience using <a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN).</span></span> <span data-ttu-id="d2891-107">PUN は、Mixed Reality の開発者が共有エクスペリエンスを作成するために使用できるいくつかのネットワーク オプションの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="d2891-107">PUN is one of several networking options available to mixed reality developers to create shared experiences.</span></span>

<span data-ttu-id="d2891-108">このシリーズのチュートリアル:</span><span class="sxs-lookup"><span data-stu-id="d2891-108">Tutorials in this series:</span></span>

* [<span data-ttu-id="d2891-109">Photon Unity Networking の設定</span><span class="sxs-lookup"><span data-stu-id="d2891-109">Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
* [<span data-ttu-id="d2891-110">複数のユーザーの接続</span><span class="sxs-lookup"><span data-stu-id="d2891-110">Connecting multiple users</span></span>](mr-learning-sharing-03.md)
* [<span data-ttu-id="d2891-111">複数のユーザーとオブジェクトの移動を共有する</span><span class="sxs-lookup"><span data-stu-id="d2891-111">Sharing object movements with multiple users</span></span>](mr-learning-sharing-04.md)
* [<span data-ttu-id="d2891-112">Azure Spatial Anchors の共有エクスペリエンスへの統合</span><span class="sxs-lookup"><span data-stu-id="d2891-112">Integrating Azure Spatial Anchors into a shared experience</span></span>](mr-learning-sharing-05.md)

## <a name="objectives"></a><span data-ttu-id="d2891-113">目標</span><span class="sxs-lookup"><span data-stu-id="d2891-113">Objectives</span></span>

* <span data-ttu-id="d2891-114">PUN アプリを作成して Unity プロジェクトをそれに接続する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="d2891-114">Learn how to create a PUN app and connect your Unity project to it</span></span>
* <span data-ttu-id="d2891-115">共有エクスペリエンスで複数のユーザーを接続する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="d2891-115">Learn how to connect multiple users in a shared experience</span></span>
* <span data-ttu-id="d2891-116">他のユーザーとオブジェクトの移動を共有する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="d2891-116">Learn how to share the object movements with other users</span></span>
* <span data-ttu-id="d2891-117">複数のデバイス間で空間的な位置合わせを実現する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="d2891-117">Learn how to achieve spatial alignment between multiple devices</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d2891-118">前提条件</span><span class="sxs-lookup"><span data-stu-id="d2891-118">Prerequisites</span></span>

* <span data-ttu-id="d2891-119">適切な[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 コンピューター</span><span class="sxs-lookup"><span data-stu-id="d2891-119">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="d2891-120">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="d2891-120">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="d2891-121">[開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="d2891-121">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="d2891-122">Unity 2019 LTS がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="d2891-122"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="d2891-123">「[Spatial Anchors リソースを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)」セクション ([クイック スタート:Azure Spatial Anchors を使用する Unity HoloLens アプリを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) チュートリアルにあります) を完了します。</span><span class="sxs-lookup"><span data-stu-id="d2891-123">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="d2891-124">[入門チュートリアル](mr-learning-base-01.md) シリーズを完了しているか、Unity および MRTK の基本操作に関する以前の経験</span><span class="sxs-lookup"><span data-stu-id="d2891-124">Completed the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="d2891-125">[Azure Spatial Anchors のチュートリアル](mr-learning-asa-01.md) シリーズを完了しているか、Azure Spatial Anchors アカウントの作成に関する以前の経験</span><span class="sxs-lookup"><span data-stu-id="d2891-125">Completed the [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) series or prior experience creating an Azure Spatial Anchors Account</span></span>
* <span data-ttu-id="d2891-126">HoloLens に加えて Android にもデプロイする場合</span><span class="sxs-lookup"><span data-stu-id="d2891-126">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="d2891-127">Windows コンピューターか macOS コンピューターに USB 接続された、<a href="https://developer.android.com/studio/debug/dev-options" target="_blank">開発者向けオプションが有効</a>に設定された <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 対応</a>の Android デバイス</span><span class="sxs-lookup"><span data-stu-id="d2891-127">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="d2891-128">Unity 2019 LTS がインストールされ、Android ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="d2891-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Android Build Support module added</span></span>
* <span data-ttu-id="d2891-129">HoloLens に加えて iOS にもデプロイする場合</span><span class="sxs-lookup"><span data-stu-id="d2891-129">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="d2891-130"><a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> および <a href="https://cocoapods.org" target="_blank">CocoaPods</a> の最新バージョンがインストールされた macOS コンピューター</span><span class="sxs-lookup"><span data-stu-id="d2891-130">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="d2891-131">macOS コンピューターに USB 接続された、<a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 互換</a> iOS デバイス</span><span class="sxs-lookup"><span data-stu-id="d2891-131">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="d2891-132">Unity 2019 LTS がインストールされ、iOS ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="d2891-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="d2891-133">このチュートリアル シリーズで推奨されている Mixed Reality Toolkit のバージョンは MRTK 2.5.3 です。</span><span class="sxs-lookup"><span data-stu-id="d2891-133">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.5.3.</span></span>

> [!CAUTION]
> <span data-ttu-id="d2891-134">このチュートリアル シリーズで推奨される Unity のバージョンは Unity 2019 LTS です。これは、上のリンク先の前提条件に記載されているすべての Unity のバージョンに代わるものです。</span><span class="sxs-lookup"><span data-stu-id="d2891-134">The recommended Unity version for this tutorial series is Unity 2019 LTS This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d2891-135">次のチュートリアル:2.Photon Unity ネットワークの設定</span><span class="sxs-lookup"><span data-stu-id="d2891-135">Next Tutorial: 2. Setting up Photon Unity Networking</span></span>](mr-learning-sharing-02.md)
