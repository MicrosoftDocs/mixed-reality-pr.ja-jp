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
# <a name="in-app-purchases"></a>アプリ内購入

アプリ内購入は HoloLens でサポートされていますが、設定作業がいくつかあります。

アプリ購入機能でを使用するには、次のことを行う必要があります。
* スレートとして表示される XAML [2d ビュー](../design/app-views.md) を作成する
* これに切り替えて配置をアクティブにします。これにより、イマーシブビューが残されます。
* API: await [Currentapp ("DurableItemIAPName")](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)を呼び出します。

この API は、アプリ内購入の名前、説明、価格を表示する Windows OS のストックポップアップを表示します。 ユーザーは購入オプションを選択できます。 アクションが完了したら、アプリは UI を提示する必要があります。 UI を使用すると、ユーザーはそのユーザーの [イマーシブビュー](../design/app-views.md)に戻ることができます。

デスクトップベースの Windows Mixed Reality イマーシブヘッドセットを対象とするアプリでは、RequestProductPurchaseAsync API を呼び出す前に、手動で XAML ビューに切り替える必要はありません。
