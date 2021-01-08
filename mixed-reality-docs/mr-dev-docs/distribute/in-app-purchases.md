---
title: アプリ内購入
description: 混合 reality アプリで、2D XAML ビューと stock Windows OS ポップアップを使用してアプリ内購入を使用する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: アプリ内購入, hololens, XAML, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実のヘッドセット
ms.openlocfilehash: a87cc68f67def1d46a3a6ba352e723d356f51fa2
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008672"
---
# <a name="in-app-purchases"></a><span data-ttu-id="30cf3-104">アプリ内購入</span><span class="sxs-lookup"><span data-stu-id="30cf3-104">In-app purchases</span></span>

<span data-ttu-id="30cf3-105">アプリ内購入は HoloLens でサポートされていますが、設定作業がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="30cf3-105">In-app purchases are supported in HoloLens, but there's some work to set them up.</span></span>

<span data-ttu-id="30cf3-106">アプリ購入機能でを使用するには、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="30cf3-106">To use the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="30cf3-107">スレートとして表示される XAML [2d ビュー](../design/app-views.md) を作成する</span><span class="sxs-lookup"><span data-stu-id="30cf3-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="30cf3-108">これに切り替えて配置をアクティブにします。これにより、イマーシブビューが残されます。</span><span class="sxs-lookup"><span data-stu-id="30cf3-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="30cf3-109">API: await [Currentapp ("DurableItemIAPName")](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="30cf3-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="30cf3-110">この API は、アプリ内購入の名前、説明、価格を表示する Windows OS のストックポップアップを表示します。</span><span class="sxs-lookup"><span data-stu-id="30cf3-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="30cf3-111">ユーザーは購入オプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="30cf3-111">The user can then choose purchase options.</span></span> <span data-ttu-id="30cf3-112">アクションが完了したら、アプリは UI を提示する必要があります。 UI を使用すると、ユーザーはそのユーザーの [イマーシブビュー](../design/app-views.md)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="30cf3-112">Once the action is completed, the app will need to present UI, which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="30cf3-113">デスクトップベースの Windows Mixed Reality イマーシブヘッドセットを対象とするアプリでは、RequestProductPurchaseAsync API を呼び出す前に、手動で XAML ビューに切り替える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="30cf3-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it isn't required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
