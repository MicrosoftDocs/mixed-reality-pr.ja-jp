---
title: チュートリアルの概要と目的
description: このコースを完了すると、Mixed Reality アプリケーション内で Azure 顔認識を実装する方法を学習することができます。
author: jessemcculloch
ms.author: jemccull
ms.date: 02/26/2019
ms.topic: article
keywords: Mixed Reality、Unity、チュートリアル、Hololens
ms.localizationpriority: high
ms.openlocfilehash: b7e04a03f01beb1438f6f723c3938d05a60c9131
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581165"
---
# <a name="1-overview-and-objectives"></a><span data-ttu-id="9ddf0-104">1.概要と目標</span><span class="sxs-lookup"><span data-stu-id="9ddf0-104">1. Overview and objectives</span></span>

## <a name="device-support"></a><span data-ttu-id="9ddf0-105">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="9ddf0-105">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="9ddf0-106"><strong>コース</strong></span><span class="sxs-lookup"><span data-stu-id="9ddf0-106"><strong>Course</strong></span></span></td>
        <td><span data-ttu-id="9ddf0-107"><a href="/hololens/hololens1-hardware"><strong>HoloLens (第 1 世代)</strong></a></span><span class="sxs-lookup"><span data-stu-id="9ddf0-107"><a href="/hololens/hololens1-hardware"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="9ddf0-108"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span><span class="sxs-lookup"><span data-stu-id="9ddf0-108"><a href="https://www.microsoft.com//hololens/hardware"><strong>HoloLens 2</strong></a></span></span></td>
        <td><span data-ttu-id="9ddf0-109"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>イマーシブ ヘッドセット</strong></a></span><span class="sxs-lookup"><span data-stu-id="9ddf0-109"><a href="../../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td></td>
        <td>❌</td>
        <td><span data-ttu-id="9ddf0-110">✔️</span><span class="sxs-lookup"><span data-stu-id="9ddf0-110">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="before-you-start"></a><span data-ttu-id="9ddf0-111">開始する前に</span><span class="sxs-lookup"><span data-stu-id="9ddf0-111">Before you start</span></span>

### <a name="prerequisites"></a><span data-ttu-id="9ddf0-112">前提条件</span><span class="sxs-lookup"><span data-stu-id="9ddf0-112">Prerequisites</span></span>

* <span data-ttu-id="9ddf0-113">正しい[ツールがインストールされている](../../install-the-tools.md)構成済みの Windows 10 PC</span><span class="sxs-lookup"><span data-stu-id="9ddf0-113">A Windows 10 PC configured with the correct [tools installed](../../install-the-tools.md)</span></span>
* <span data-ttu-id="9ddf0-114">Windows 10 SDK 10.0.18362.0 以降</span><span class="sxs-lookup"><span data-stu-id="9ddf0-114">Windows 10 SDK 10.0.18362.0 or later</span></span>
* <span data-ttu-id="9ddf0-115">基本的な C# プログラミング能力</span><span class="sxs-lookup"><span data-stu-id="9ddf0-115">Some basic C# programming ability</span></span>
* <span data-ttu-id="9ddf0-116">[開発用に構成された](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode) HoloLens 2 デバイス</span><span class="sxs-lookup"><span data-stu-id="9ddf0-116">A HoloLens 2 device [configured for development](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)</span></span>
* <span data-ttu-id="9ddf0-117">Unity 2019.2.X がインストールされ、ユニバーサル Windows プラットフォーム ビルド サポート モジュールが追加された <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a></span><span class="sxs-lookup"><span data-stu-id="9ddf0-117"><a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Unity Hub</a> with Unity 2019.2.X installed and the Universal Windows Platform Build Support module added</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ddf0-118">このチュートリアル シリーズで推奨されている Unity バージョンは Unity 2019.2.X です。</span><span class="sxs-lookup"><span data-stu-id="9ddf0-118">The recommended Unity version for this tutorial series is Unity 2019.2.X.</span></span> <span data-ttu-id="9ddf0-119">これは、上のリンクされた前提条件に記載されている Unity のバージョン要件または推奨事項に代わるものです。</span><span class="sxs-lookup"><span data-stu-id="9ddf0-119">This supersedes any Unity version requirements or recommendations stated in the prerequisites linked above.</span></span>

[<span data-ttu-id="9ddf0-120">次のレッスン: 2. プロジェクトと最初のアプリケーションの初期化</span><span class="sxs-lookup"><span data-stu-id="9ddf0-120">Next lesson: 2. Initializing your project and first application</span></span>](./mr-learning-base-02.md)