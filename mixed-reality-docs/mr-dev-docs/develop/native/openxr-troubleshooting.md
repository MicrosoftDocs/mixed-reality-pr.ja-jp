---
title: OpenXR トラブルシューティング
description: OpenXR アプリケーションの問題をトラブルシューティングします。
author: thetuvix
ms.author: alexturn
ms.date: 2/28/2020
ms.topic: article
keywords: OpenXR、Khronos、BasicXRApp、DirectX、ネイティブ、ネイティブアプリ、カスタムエンジン、ミドルウェア、トラブルシューティング
ms.openlocfilehash: ddfe548d689d84576ad0ac06bda46d7c2757859c
ms.sourcegitcommit: 2bf79eef6a9b845494484f458443ef4f89d7efc0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97612936"
---
# <a name="openxr-troubleshooting"></a><span data-ttu-id="c82fd-104">OpenXR トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="c82fd-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="c82fd-105">Windows Mixed Reality OpenXR Runtime を使用して OpenXR アプリを開発する際のトラブルシューティングのヒントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="c82fd-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="c82fd-106"><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 の仕様</a>に関して他に質問がある場合は、 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR フォーラム</a>または<a href="https://khr.io/slack" target="_blank">余裕期間 #openxr チャネル</a>にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="c82fd-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="c82fd-107">X86 アプリでの現在の Windows Mixed Reality OpenXR ランタイムには既知の問題があります。</span><span class="sxs-lookup"><span data-stu-id="c82fd-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="c82fd-108">現時点では、x64 用のデスクトップ OpenXR アプリを構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c82fd-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="c82fd-109">OpenXR app が Windows Mixed Reality を開始しない</span><span class="sxs-lookup"><span data-stu-id="c82fd-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="c82fd-110">実行時に OpenXR アプリが Windows Mixed Reality を起動していない場合は、Windows Mixed Reality OpenXR ランタイムがアクティブなランタイムとして設定されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c82fd-110">If your OpenXR app isn't starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span> <span data-ttu-id="c82fd-111">この問題を解決するには、「 [OpenXR For Windows Mixed Reality ヘッドセットの](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 概要」の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="c82fd-111">Follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to fix the issue.</span></span>

<span data-ttu-id="c82fd-112">また、Windows mixed reality [の OpenXR 開発者ツール](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) を実行して、Windows Mixed Reality OpenXR Runtime のシステムの状態に関するトラブルシューティングのヘルプを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="c82fd-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) to get troubleshooting help on the state of your systems Windows Mixed Reality OpenXR Runtime.</span></span>