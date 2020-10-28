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
# <a name="openxr-troubleshooting"></a><span data-ttu-id="358b1-104">OpenXR トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="358b1-104">OpenXR troubleshooting</span></span>

<span data-ttu-id="358b1-105">Windows Mixed Reality OpenXR Runtime を使用して OpenXR アプリを開発する際のトラブルシューティングのヒントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="358b1-105">Here are some troubleshooting tips when developing an OpenXR app using the Windows Mixed Reality OpenXR Runtime.</span></span>  <span data-ttu-id="358b1-106"><a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 の仕様</a>に関して他に質問がある場合は、 <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR フォーラム</a>または<a href="https://khr.io/slack" target="_blank">余裕期間 #openxr チャネル</a>にアクセスしてください。</span><span class="sxs-lookup"><span data-stu-id="358b1-106">If you have any other questions about the <a href="https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html" target="_blank">OpenXR 1.0 specification</a>, please visit the <a href="https://community.khronos.org/c/openxr" target="_blank">Khronos OpenXR Forums</a> or <a href="https://khr.io/slack" target="_blank">Slack #openxr channel</a>.</span></span>

>[!NOTE]
><span data-ttu-id="358b1-107">X86 アプリでの現在の Windows Mixed Reality OpenXR ランタイムには既知の問題があります。</span><span class="sxs-lookup"><span data-stu-id="358b1-107">There are known issues in the current Windows Mixed Reality OpenXR runtime with x86 apps.</span></span>  <span data-ttu-id="358b1-108">現時点では、x64 用のデスクトップ OpenXR アプリを構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="358b1-108">You should build desktop OpenXR apps for x64 at the moment.</span></span>

### <a name="openxr-app-not-starting-windows-mixed-reality"></a><span data-ttu-id="358b1-109">OpenXR app が Windows Mixed Reality を開始しない</span><span class="sxs-lookup"><span data-stu-id="358b1-109">OpenXR app not starting Windows Mixed Reality</span></span>

<span data-ttu-id="358b1-110">実行時に OpenXR アプリが Windows Mixed Reality を起動していない場合は、Windows Mixed Reality OpenXR ランタイムがアクティブなランタイムとして設定されていない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="358b1-110">If your OpenXR app is not starting Windows Mixed Reality when you run it, the Windows Mixed Reality OpenXR Runtime may not be set as the active runtime.</span></span>  <span data-ttu-id="358b1-111">「 [OpenXR For Windows Mixed Reality ヘッドセットの](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) 概要」の手順に従って、ランタイムをアクティブにしてください。</span><span class="sxs-lookup"><span data-stu-id="358b1-111">Be sure to follow the instructions for [getting started with OpenXR for Windows Mixed Reality headsets](openxr-getting-started.md#getting-started-with-openxr-for-windows-mixed-reality-headsets) to make the runtime active.</span></span>

<span data-ttu-id="358b1-112">また、windows mixed reality [の OpenXR 開発者ツール](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) を実行して、システム上の Windows Mixed Reality OpenXR ランタイムの状態に関する追加のトラブルシューティングを行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="358b1-112">You can also run the [OpenXR Developer Tools for Windows Mixed Reality](openxr-getting-started.md#getting-the-openxr-developer-tools-for-windows-mixed-reality) for additional troubleshooting help around the state of the Windows Mixed Reality OpenXR Runtime on your system.</span></span>