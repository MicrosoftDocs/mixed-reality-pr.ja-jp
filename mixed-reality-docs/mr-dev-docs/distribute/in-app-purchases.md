---
title: アプリ内購入
description: アプリ内購入は mixed reality アプリでサポートされていますが、設定作業がいくつかあります。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: アプリ内購入, hololens
ms.openlocfilehash: 7174fe555322216b7e547055aaaf7879c01d8f23
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91684847"
---
# <a name="in-app-purchases"></a><span data-ttu-id="f6f4d-104">アプリ内購入</span><span class="sxs-lookup"><span data-stu-id="f6f4d-104">In-app purchases</span></span>

<span data-ttu-id="f6f4d-105">アプリ内購入は HoloLens でサポートされていますが、設定作業がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="f6f4d-105">In-app purchases are supported in HoloLens, but there is some work to set them up.</span></span>

<span data-ttu-id="f6f4d-106">アプリ購入機能を活用するためには、次のことを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6f4d-106">In order to leverage the in app-purchase functionality, you must:</span></span>
* <span data-ttu-id="f6f4d-107">スレートとして表示される XAML [2d ビュー](../design/app-views.md) を作成する</span><span class="sxs-lookup"><span data-stu-id="f6f4d-107">Create a XAML [2D view](../design/app-views.md) to appear as a slate</span></span>
* <span data-ttu-id="f6f4d-108">これに切り替えて配置をアクティブにします。これにより、イマーシブビューが残されます。</span><span class="sxs-lookup"><span data-stu-id="f6f4d-108">Switch to it to activate placement, which leaves the immersive view</span></span>
* <span data-ttu-id="f6f4d-109">API: await [Currentapp ("DurableItemIAPName")](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f6f4d-109">Call the API: await [CurrentApp.RequestProductPurchaseAsync("DurableItemIAPName");](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)</span></span>

<span data-ttu-id="f6f4d-110">この API は、アプリ内購入の名前、説明、価格を表示する Windows OS のストックポップアップを表示します。</span><span class="sxs-lookup"><span data-stu-id="f6f4d-110">This API will bring up the stock Windows OS popup that shows the in-app purchase name, description, and price.</span></span> <span data-ttu-id="f6f4d-111">ユーザーは購入オプションを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f6f4d-111">The user can then choose purchase options.</span></span> <span data-ttu-id="f6f4d-112">アクションが完了したら、アプリはユーザーが [イマーシブビュー](../design/app-views.md)に戻ることができる UI を提示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f6f4d-112">Once the action is completed, the app will need to present UI which allows the user to switch back to its [immersive view](../design/app-views.md).</span></span>

<span data-ttu-id="f6f4d-113">デスクトップベースの Windows Mixed Reality イマーシブヘッドセットを対象とするアプリでは、RequestProductPurchaseAsync API を呼び出す前に、手動で XAML ビューに切り替える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f6f4d-113">For apps targeting desktop-based Windows Mixed Reality immersive headsets, it is not required to manually switch to a XAML view before calling the RequestProductPurchaseAsync API.</span></span>
