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
# <a name="openxr-troubleshooting"></a><span data-ttu-id="97e0b-104">OpenXR トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="97e0b-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="97e0b-105">Windows Mixed Reality OpenXR Runtime を使用して OpenXR アプリを開発する際のトラブルシューティングのヒントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="97e0b-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="97e0b-106"><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 の仕様</a>に関して他に質問がある場合は、 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR フォーラム</a>または<a href="https://khr.io/slack" target="_blank">余裕期間 #openxr チャネル</a>にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="97e0b-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="97e0b-107">X86 アプリでの現在の Windows Mixed Reality OpenXR ランタイムには既知の問題があります。</span><span class="sxs-lookup"><span data-stu-id="97e0b-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="97e0b-108">現時点では、x64 用のデスクトップ OpenXR アプリを構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97e0b-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="97e0b-109">OpenXR app が Windows Mixed Reality を開始しない</span><span class="sxs-lookup"><span data-stu-id="97e0b-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="97e0b-110">実行時に OpenXR アプリが Windows Mixed Reality を起動していない場合は、Windows Mixed Reality OpenXR ランタイムがアクティブなランタイムとして設定されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="97e0b-110">If your OpenXR app isn't starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span> <span data-ttu-id="97e0b-111">この問題を解決するには、「 [OpenXR For Windows Mixed Reality ヘッドセットの](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 概要」の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="97e0b-111">Follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to fix the issue.</span></span>

<span data-ttu-id="97e0b-112">また、Windows mixed reality [の OpenXR 開発者ツール](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) を実行して、Windows Mixed Reality OpenXR Runtime のシステムの状態に関するトラブルシューティングのヘルプを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="97e0b-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) to get troubleshooting help on the state of your systems Windows Mixed Reality OpenXR Runtime.</span></span>