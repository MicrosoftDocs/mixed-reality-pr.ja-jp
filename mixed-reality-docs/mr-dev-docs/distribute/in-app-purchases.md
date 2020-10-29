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
# <a name="in-app-purchases"></a>アプリ内購入

アプリ内購入は HoloLens でサポートされていますが、設定作業がいくつかあります。

アプリ購入機能を活用するためには、次のことを行う必要があります。
* スレートとして表示される XAML [2d ビュー](../design/app-views.md) を作成する
* これに切り替えて配置をアクティブにします。これにより、イマーシブビューが残されます。
* API: await [Currentapp ("DurableItemIAPName")](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)を呼び出します。

この API は、アプリ内購入の名前、説明、価格を表示する Windows OS のストックポップアップを表示します。 ユーザーは購入オプションを選択できます。 アクションが完了したら、アプリはユーザーが [イマーシブビュー](../design/app-views.md)に戻ることができる UI を提示する必要があります。

デスクトップベースの Windows Mixed Reality イマーシブヘッドセットを対象とするアプリでは、RequestProductPurchaseAsync API を呼び出す前に、手動で XAML ビューに切り替える必要はありません。
