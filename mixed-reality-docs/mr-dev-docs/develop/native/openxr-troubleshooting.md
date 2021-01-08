---
title: OpenXR トラブルシューティング
description: Windows Mixed Reality OpenXR アプリケーションでの一般的なトラブルシューティングに関するリソースと回答を紹介します。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア、トラブルシューティング
ms.openlocfilehash: 6e1696bca4f31f70af10c32087400ed56efa3c11
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006732"
---
# <a name="openxr-troubleshooting"></a>OpenXR トラブルシューティング

Windows Mixed Reality OpenXR Runtime を使用して OpenXR アプリを開発する際のトラブルシューティングのヒントを次に示します。  <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 の仕様</a>に関して他に質問がある場合は、 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR フォーラム</a>または<a href="https://khr.io/slack" target="_blank">余裕期間 #openxr チャネル</a>にアクセスしてください。

>[!NOTE]
>X86 アプリでの現在の Windows Mixed Reality OpenXR ランタイムには既知の問題があります。  現時点では、x64 用のデスクトップ OpenXR アプリを構築する必要があります。

### <a name="openxr-app-not-starting-windows-mixed-reality"></a>OpenXR app が Windows Mixed Reality を開始しない

実行時に OpenXR アプリが Windows Mixed Reality を起動していない場合は、Windows Mixed Reality OpenXR ランタイムがアクティブなランタイムとして設定されていない可能性があります。 この問題を解決するには、「 [OpenXR For Windows Mixed Reality ヘッドセットの](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 概要」の手順に従ってください。

また、Windows mixed reality [の OpenXR 開発者ツール](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) を実行して、Windows Mixed Reality OpenXR Runtime のシステムの状態に関するトラブルシューティングのヘルプを取得することもできます。