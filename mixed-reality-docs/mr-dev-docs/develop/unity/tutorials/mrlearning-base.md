---
title: 入門チュートリアル - 1.  概要と目標
description: このコースでは、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法について説明します。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: 777203d0051c22b0f249db7d377ab08f92c089b7
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91701589"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="fcb35-105">1.概要と目標</span><span class="sxs-lookup"><span data-stu-id="fcb35-105">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="fcb35-106">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="fcb35-106">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="fcb35-107"><strong>コース</strong></span><span class="sxs-lookup"><span data-stu-id="fcb35-107"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="fcb35-108"><a href="../../../hololens-hardware-details.md"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcb35-108"><a href="../../../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="fcb35-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcb35-109"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="fcb35-110"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="fcb35-110"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="fcb35-111">✔️</span><span class="sxs-lookup"><span data-stu-id="fcb35-111">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="fcb35-112">開始する前に</span><span class="sxs-lookup"><span data-stu-id="fcb35-112">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="fcb35-113">前提条件</span><span class="sxs-lookup"><span data-stu-id="fcb35-113">Prerequisites</span></span>

* <span data-ttu-id="fcb35-114">正しい[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="fcb35-114">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="fcb35-115">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="fcb35-115">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="fcb35-116">基本的な C# プログラミング能力</span><span class="sxs-lookup"><span data-stu-id="fcb35-116">Some basic C# programming ability</span></span>
* <span data-ttu-id="fcb35-117">[開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="fcb35-117">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="fcb35-118">Unity 2019.2.X がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="fcb35-118"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fcb35-119">このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.2.X です。</span><span class="sxs-lookup"><span data-stu-id="fcb35-119">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="fcb35-120">これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="fcb35-120">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="fcb35-121">次のレッスン: 2.プロジェクトと最初のアプリケーションの初期化</span><span class="sxs-lookup"><span data-stu-id="fcb35-121">Next lesson: 2. Initializing your project and first application</span></span>](../../../mrlearning-base-ch1.md)
