---
title: Azure Spatial Anchors チュートリアル - 1. はじめに
description: このコースを完了すると Mixed Reality アプリケーション内に Azure Spatial Anchors を実装できます。
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 088987e0b43908abecfd66b9dbb0a4de8fcf472e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91702449"
---
# <a name="1-introduction"></a>1.はじめに

## <a name="overview"></a>概要

Azure Spatial Anchors チュートリアルにようこそ。 このチュートリアル シリーズをとおして、<a href="https://azure.microsoft.com/services/spatial-anchors" target="_blank">Azure Spatial Anchors</a> (ASA) の基礎と完全な複合現実体験を現実の世界で実現する方法について説明します。 プロジェクトを Android と iOS にデプロイする方法についても説明します。

このシリーズのチュートリアル:

1. [はじめに](mr-learning-asa-01.md) (このページです)
2. [Azure Spatial Anchors をお使いになる前に](mr-learning-asa-02.md)
3. [Azure Spatial Anchors の保存、取得、共有](mr-learning-asa-03.md)
4. [Azure Spatial Anchors のフィードバックの表示](mr-learning-asa-04.md)
5. [Android と iOS 用の Azure Spatial Anchors](mr-learning-asa-05.md)

## <a name="objectives"></a>目標

* 空間アンカーを作成し、Azure から取得する方法を学習する
* アプリ セッション間で空間的な位置合わせを実現する方法を学習する
* 複数のデバイス間で空間的な位置合わせを実現する方法を学習する
* プロジェクトを準備し、構築し、Android と iOS にデプロイする方法を学習する

## <a name="prerequisites"></a>前提条件

* 正しい[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 コンピューター
* Windows 10 SDK 10.0.18362.0 以降のバージョン
* [開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス
* Unity 2019.3.15 がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>
* 「[Spatial Anchors リソースを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens#create-a-spatial-anchors-resource)」セクション ([クイック スタート:Azure Spatial Anchors を使用する Unity HoloLens アプリを作成する](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-unity-hololens) チュートリアルにあります) を完了します。
* [入門チュートリアル](mr-learning-base-01.md) シリーズを完了しているか、以前に Unity と MRTK の基本操作を経験していること
* HoloLens に加えて Android にもデプロイする場合
  * Windows コンピューターか macOS コンピューターに USB 接続された、<a href="https://developer.android.com/studio/debug/dev-options" target="_blank">開発者向けオプションが有効</a>に設定された <a href="https://developers.google.com/ar/discover/supported-devices" target="_blank">ARCore 対応</a>の Android デバイス
  * Unity 2019.3.15 がインストールされ、Android ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>
* HoloLens に加えて iOS にもデプロイする場合
  * <a href="https://geo.itunes.apple.com/us/app/xcode/id497799835?mt=12" target="_blank">Xcode</a> および <a href="https://cocoapods.org" target="_blank">CocoaPods</a> の最新バージョンがインストールされた macOS コンピューター
  * macOS コンピューターに USB 接続された、<a href="https://developer.apple.com/documentation/arkit/verifying_device_support_and_user_permission" target="_blank">ARKit 互換</a> iOS デバイス
  * 2019.3.15 がインストールされ、iOS ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a>

> [!CAUTION]
> このチュートリアル シリーズで推奨されている Mixed Reality Toolkit のバージョンは MRTK 2.4.0 です。

> [!CAUTION]
> このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.3.15 です。 これは、上のリンクされた前提条件に記載されている Unity のバージョン要件に代わるものです。

> [!div class="nextstepaction"]
> [次のチュートリアル:2.Azure Spatial Anchors をお使いになる前に](mr-learning-asa-02.md)
