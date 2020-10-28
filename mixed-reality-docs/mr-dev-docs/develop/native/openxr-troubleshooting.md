---
title: OpenXR トラブルシューティング
description: OpenXR アプリケーションの問題をトラブルシューティングします。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア、トラブルシューティング
ms.openlocfilehash: 174c115b86e62d5c52051a7363a59e383e503a95
ms.sourcegitcommit: c199872c11adae7de24929ed043ea90dea087b3e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903089"
---
# <a name="openxr-troubleshooting"></a>OpenXR トラブルシューティング

Windows Mixed Reality OpenXR Runtime を使用して OpenXR アプリを開発する際のトラブルシューティングのヒントを次に示します。  <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 の仕様</a>に関して他に質問がある場合は、 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR フォーラム</a>または<a href="https://khr.io/slack" target="_blank">余裕期間 #openxr チャネル</a>にアクセスしてください。

>[!NOTE]
>X86 アプリでの現在の Windows Mixed Reality OpenXR ランタイムには既知の問題があります。  現時点では、x64 用のデスクトップ OpenXR アプリを構築する必要があります。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR app が Windows Mixed Reality を開始しない

実行時に OpenXR アプリが Windows Mixed Reality を起動していない場合は、Windows Mixed Reality OpenXR ランタイムがアクティブなランタイムとして設定されていない可能性があります。  「 [OpenXR For Windows Mixed Reality ヘッドセットの](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 概要」の手順に従って、ランタイムをアクティブにしてください。

また、windows mixed reality [の OpenXR 開発者ツール](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) を実行して、システム上の Windows Mixed Reality OpenXR ランタイムの状態に関する追加のトラブルシューティングを行うこともできます。