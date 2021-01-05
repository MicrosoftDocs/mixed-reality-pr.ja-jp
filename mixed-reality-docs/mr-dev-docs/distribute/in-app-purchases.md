---
title: アプリ内購入
description: アプリ内購入は mixed reality アプリでサポートされていますが、設定作業がいくつかあります。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: アプリ内購入, hololens, XAML, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実のヘッドセット
ms.openlocfilehash: 905c1be72bf2a3d6fa167cab68a4cb71e6538acc
ms.sourcegitcommit: 8d3b84d2aa01f078ecf92cec001a252e3ea7b24d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2020
ms.locfileid: "97757783"
---
# <a name="in-app-purchases"></a>アプリ内購入

アプリ内購入は HoloLens でサポートされていますが、設定作業がいくつかあります。

アプリ購入機能でを使用するには、次のことを行う必要があります。
* スレートとして表示される XAML [2d ビュー](../design/app-views.md) を作成する
* これに切り替えて配置をアクティブにします。これにより、イマーシブビューが残されます。
* API: await [Currentapp ("DurableItemIAPName")](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)を呼び出します。

この API は、アプリ内購入の名前、説明、価格を表示する Windows OS のストックポップアップを表示します。 ユーザーは購入オプションを選択できます。 アクションが完了したら、アプリは UI を提示する必要があります。 UI を使用すると、ユーザーはそのユーザーの [イマーシブビュー](../design/app-views.md)に戻ることができます。

デスクトップベースの Windows Mixed Reality イマーシブヘッドセットを対象とするアプリでは、RequestProductPurchaseAsync API を呼び出す前に、手動で XAML ビューに切り替える必要はありません。
