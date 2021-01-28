---
title: マルチユーザー機能のチュートリアルの概要
description: このコースを完了すると、HoloLens 2 アプリケーション内で共有マルチユーザー エクスペリエンスを実装する方法を学習できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality, Unity, チュートリアル, Hololens, マルチユーザー機能, Photon, MRTK, Mixed Reality Toolkit, UWP, Azure 空間アンカー
ms.localizationpriority: high
ms.openlocfilehash: c18bd7c10ed042278053a51c2d1894564000dfe2
ms.sourcegitcommit: 3dad2adfdb5bdb8100d8d864f7845e34a3ef912d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2021
ms.locfileid: "98699021"
---
# <a name="1-introduction-to-the-multi-user-capabilities-tutorials"></a>1. マルチユーザー機能のチュートリアルの概要

マルチユーザー機能のチュートリアルへようこそ。 このチュートリアル シリーズでは、<a href="https://www.photonengine.com/PUN" target="_blank">Photon Unity Networking</a> (PUN) を使用したマルチユーザー エクスペリエンスの構築方法の基礎について学習します。 PUN は、Mixed Reality の開発者が共有エクスペリエンスを作成するために使用できるいくつかのネットワーク オプションの 1 つです。

このシリーズのチュートリアル:

* [Photon Unity Networking の設定](mr-learning-sharing-02.md)
* [複数のユーザーの接続](mr-learning-sharing-03.md)
* [複数のユーザーとオブジェクトの移動を共有する](mr-learning-sharing-04.md)
* [Azure Spatial Anchors の共有エクスペリエンスへの統合](mr-learning-sharing-05.md)

## <a name="objectives"></a>目標

* PUN アプリを作成して Unity プロジェクトをそれに接続する方法を学習する
* 共有エクスペリエンスで複数のユーザーを接続する方法を学習する
* 他のユーザーとオブジェクトの移動を共有する方法を学習する
* 複数のデバイス間で空間的な位置合わせを実現する方法を学習する

## <a name="prerequisites"></a>前提条件

* 適切な[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 コンピューター
* Windows 10 SDK 10.0.18362.0 以降
* [開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス
* Unity 2019 LTS がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>
* 「[Spatial Anchors リソースを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)」セクション ([クイック スタート:Azure Spatial Anchors を使用する Unity HoloLens アプリを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) チュートリアルにあります) を完了します。
* [入門チュートリアル](mr-learning-base-01.md) シリーズを完了しているか、Unity および MRTK の基本操作に関する以前の経験
* [Azure Spatial Anchors のチュートリアル](mr-learning-asa-01.md) シリーズを完了しているか、Azure Spatial Anchors アカウントの作成に関する以前の経験
* HoloLens に加えて Android にもデプロイする場合
  * Windows コンピューターか macOS コンピューターに USB 接続された、<a href="https://developer.android.com/studio/debug/dev-options" target="_blank">開発者向けオプションが有効</a>に設定された <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 対応</a>の Android デバイス
  * Unity 2019 LTS がインストールされ、Android ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>
* HoloLens に加えて iOS にもデプロイする場合
  * <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> および <a href="https://cocoapods.org" target="_blank">CocoaPods</a> の最新バージョンがインストールされた macOS コンピューター
  * macOS コンピューターに USB 接続された、<a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 互換</a> iOS デバイス
  * Unity 2019 LTS がインストールされ、iOS ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>

> [!CAUTION]
> このチュートリアル シリーズで推奨されている Mixed Reality Toolkit のバージョンは MRTK 2.5.1 です。

> [!CAUTION]
> このチュートリアル シリーズで推奨される Unity のバージョンは Unity 2019 LTS です。これは、上のリンク先の前提条件に記載されているすべての Unity のバージョンに代わるものです。

> [!div class="nextstepaction"]
> [次のチュートリアル:2.Photon Unity ネットワークの設定](mr-learning-sharing-02.md)
