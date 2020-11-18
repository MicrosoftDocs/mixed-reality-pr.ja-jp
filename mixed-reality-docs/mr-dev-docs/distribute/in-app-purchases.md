---
title: アプリ内購入
description: アプリ内購入は mixed reality アプリでサポートされていますが、設定作業がいくつかあります。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: アプリ内購入, hololens, XAML, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実のヘッドセット
ms.openlocfilehash: 07601ab4961e14ff43dbc149f7d8cb5731d24013
ms.sourcegitcommit: 4f3ef057a285be2e260615e5d6c41f00d15d08f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703178"
---
# <a name="in-app-purchases"></a>アプリ内購入

アプリ内購入は HoloLens でサポートされていますが、設定作業がいくつかあります。

アプリ購入機能を活用するためには、次のことを行う必要があります。
* スレートとして表示される XAML [2d ビュー](../design/app-views.md) を作成する
* これに切り替えて配置をアクティブにします。これにより、イマーシブビューが残されます。
* API: await [Currentapp ("DurableItemIAPName")](https://docs.microsoft.com/uwp/api/windows.applicationmodel.store.currentapp#Windows_ApplicationModel_Store_CurrentApp_RequestProductPurchaseAsync_System_String_)を呼び出します。

この API は、アプリ内購入の名前、説明、価格を表示する Windows OS のストックポップアップを表示します。 ユーザーは購入オプションを選択できます。 アクションが完了したら、アプリはユーザーが [イマーシブビュー](../design/app-views.md)に戻ることができる UI を提示する必要があります。

デスクトップベースの Windows Mixed Reality イマーシブヘッドセットを対象とするアプリでは、RequestProductPurchaseAsync API を呼び出す前に、手動で XAML ビューに切り替える必要はありません。
