---
title: Azure Spatial Anchors チュートリアルの概要
description: このコースを完了すると、Mixed Reality アプリケーション内に Azure Spatial Anchors を実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー, iOS, Android, Windows 10, ARCore, macOS, Android ビルド サポート, ARKit
ms.localizationpriority: high
ms.openlocfilehash: 9529b12968c5cbc985f4af8eb0053d277eb00c03
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699031"
---
# <a name="1-introduction-to-the-azure-spatial-anchors-tutorials"></a><span data-ttu-id="66d6d-104">1. Azure Spatial Anchors チュートリアルの概要</span><span class="sxs-lookup"><span data-stu-id="66d6d-104">1. Introduction to the Azure Spatial Anchors tutorials</span></span>

<span data-ttu-id="66d6d-105">Azure Spatial Anchors チュートリアルにようこそ。</span><span class="sxs-lookup"><span data-stu-id="66d6d-105">Welcome to the Azure Spatial Anchors tutorials!</span></span> <span data-ttu-id="66d6d-106">このチュートリアル シリーズをとおして、<a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) の基礎と完全な複合現実体験を現実の世界で実現する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="66d6d-106">Through this tutorial series, you will learn the fundamentals of <a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) and how to anchor a complete mixed reality experience in the real world.</span></span> <span data-ttu-id="66d6d-107">プロジェクトを Android と iOS にデプロイする方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="66d6d-107">You will also learn how to deploy your project to Android and iOS.</span></span>

<span data-ttu-id="66d6d-108">このシリーズのチュートリアル:</span><span class="sxs-lookup"><span data-stu-id="66d6d-108">Tutorials in this series:</span></span>

1. <span data-ttu-id="66d6d-109">[はじめに](mr-learning-asa-01.md) (このページです)</span><span class="sxs-lookup"><span data-stu-id="66d6d-109">[Introduction](mr-learning-asa-01.md) (You're already here)</span></span>
2. [<span data-ttu-id="66d6d-110">Azure Spatial Anchors をお使いになる前に</span><span class="sxs-lookup"><span data-stu-id="66d6d-110">Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
3. [<span data-ttu-id="66d6d-111">Azure Spatial Anchors の保存、取得、共有</span><span class="sxs-lookup"><span data-stu-id="66d6d-111">Saving, retrieving, and sharing Azure Spatial Anchors</span></span>](mr-learning-asa-03.md)
4. [<span data-ttu-id="66d6d-112">Azure Spatial Anchors のフィードバックの表示</span><span class="sxs-lookup"><span data-stu-id="66d6d-112">Displaying Azure Spatial Anchor feedback</span></span>](mr-learning-asa-04.md)
5. [<span data-ttu-id="66d6d-113">Android と iOS 用の Azure Spatial Anchors</span><span class="sxs-lookup"><span data-stu-id="66d6d-113">Azure Spatial Anchors for Android and iOS</span></span>](mr-learning-asa-05.md)

## <a name="objectives"></a><span data-ttu-id="66d6d-114">目標</span><span class="sxs-lookup"><span data-stu-id="66d6d-114">Objectives</span></span>

* <span data-ttu-id="66d6d-115">空間アンカーを作成し、Azure から取得する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="66d6d-115">Learn how to create spatial anchors and fetch them from Azure</span></span>
* <span data-ttu-id="66d6d-116">アプリ セッション間で空間的な位置合わせを実現する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="66d6d-116">Learn how to achieve spatial alignment across app sessions</span></span>
* <span data-ttu-id="66d6d-117">複数のデバイス間で空間的な位置合わせを実現する方法を学習する</span><span class="sxs-lookup"><span data-stu-id="66d6d-117">Learn how to achieve spatial alignment between multiple devices</span></span>
* <span data-ttu-id="66d6d-118">プロジェクトを準備し、構築し、Android と iOS にデプロイする方法を学習する</span><span class="sxs-lookup"><span data-stu-id="66d6d-118">Learn how to prepare, build, and deploy your project to Android and iOS</span></span>

## <a name="prerequisites"></a><span data-ttu-id="66d6d-119">前提条件</span><span class="sxs-lookup"><span data-stu-id="66d6d-119">Prerequisites</span></span>

* <span data-ttu-id="66d6d-120">正しい[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 コンピューター</span><span class="sxs-lookup"><span data-stu-id="66d6d-120">A Windows 10 computer configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="66d6d-121">Windows 10 SDK 10.0.18362.0 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="66d6d-121">Windows 10 SDK 10.0.18362.0 or later version</span></span>
* <span data-ttu-id="66d6d-122">[開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="66d6d-122">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="66d6d-123">Unity 2019 LTS がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="66d6d-123"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Universal Windows Platform Build Support module added</span></span>
* <span data-ttu-id="66d6d-124">「[Spatial Anchors リソースを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)」セクション ([クイック スタート:Azure Spatial Anchors を使用する Unity HoloLens アプリを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) チュートリアルにあります) を完了します。</span><span class="sxs-lookup"><span data-stu-id="66d6d-124">Completed the [Create a Spatial Anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource) section of the [Quickstart: Create a Unity HoloLens app that uses Azure Spatial Anchors](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) tutorial</span></span>
* <span data-ttu-id="66d6d-125">[入門チュートリアル](mr-learning-base-01.md) シリーズを完了しているか、以前に Unity と MRTK の基本操作を経験していること</span><span class="sxs-lookup"><span data-stu-id="66d6d-125">Finished the [Getting started tutorials](mr-learning-base-01.md) series or some basic prior experience with Unity and MRTK</span></span>
* <span data-ttu-id="66d6d-126">HoloLens に加えて Android にもデプロイする場合</span><span class="sxs-lookup"><span data-stu-id="66d6d-126">If you intend to deploy to Android as well as HoloLens</span></span>
  * <span data-ttu-id="66d6d-127">Windows コンピューターか macOS コンピューターに USB 接続された、<a href="https://developer.android.com/studio/debug/dev-options" target="_blank">開発者向けオプションが有効</a>に設定された <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 対応</a>の Android デバイス</span><span class="sxs-lookup"><span data-stu-id="66d6d-127">A <a href="https://developer.android.com/studio/debug/dev-options" target="_blank">developer enabled</a> and <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore capable</a> Android device with USB connection to your Windows or macOS computer</span></span>
  * <span data-ttu-id="66d6d-128">Unity 2019 LTS がインストールされ、Android ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="66d6d-128"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the Android Build Support module added</span></span>
* <span data-ttu-id="66d6d-129">HoloLens に加えて iOS にもデプロイする場合</span><span class="sxs-lookup"><span data-stu-id="66d6d-129">If you intend to deploy to iOS as well as HoloLens</span></span>
  * <span data-ttu-id="66d6d-130"><a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> および <a href="https://cocoapods.org" target="_blank">CocoaPods</a> の最新バージョンがインストールされた macOS コンピューター</span><span class="sxs-lookup"><span data-stu-id="66d6d-130">A macOS computer with the latest version of <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> and <a href="https://cocoapods.org" target="_blank">CocoaPods</a> installed</span></span>
  * <span data-ttu-id="66d6d-131">macOS コンピューターに USB 接続された、<a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 互換</a> iOS デバイス</span><span class="sxs-lookup"><span data-stu-id="66d6d-131">An <a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit compatible</a> iOS device with USB connection to your macOS computer</span></span>
  * <span data-ttu-id="66d6d-132">Unity 2019 LTS がインストールされ、iOS ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="66d6d-132"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019 LTS installed and the iOS Build Support module added</span></span>

> [!CAUTION]
> <span data-ttu-id="66d6d-133">このチュートリアル シリーズで推奨されている Mixed Reality Toolkit のバージョンは MRTK 2.5.1 です。</span><span class="sxs-lookup"><span data-stu-id="66d6d-133">The recommended Mixed Reality Toolkit version for this tutorial series is MRTK 2.5.1.</span></span>

> [!CAUTION]
> <span data-ttu-id="66d6d-134">このチュートリアル シリーズで推奨される Unity のバージョンは Unity 2019 LTS です。これは、上のリンク先の前提条件に記載されているすべての Unity のバージョンに代わるものです。</span><span class="sxs-lookup"><span data-stu-id="66d6d-134">The recommended Unity version for this tutorial series is Unity 2019 LTS This supersedes any Unity version requirements stated in the prerequisites linked above.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="66d6d-135">次のチュートリアル:2.Azure Spatial Anchors をお使いになる前に</span><span class="sxs-lookup"><span data-stu-id="66d6d-135">Next Tutorial: 2. Getting started with Azure Spatial Anchors</span></span>](mr-learning-asa-02.md)
