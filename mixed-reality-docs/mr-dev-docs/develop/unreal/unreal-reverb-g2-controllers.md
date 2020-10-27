---
title: Unreal の HP リバーブ G2 コントローラー
description: OpenXR と SteamVR で HP リバーブ G2 Controller を使用する手順
author: hferrone
ms.author: jacksonf
ms.date: 10/9/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、リバーブ、リバーブ G2、HP リバーブ G2、mixed reality、development、motion controller、user input、features、new project、emulator、documentation、ガイド、features、ホログラム、game development
ms.openlocfilehash: c9d3ea3a8dd52ed0712f9df5c1a789121a68fd35
ms.sourcegitcommit: 4bb5544a0c74ac4e9766bab3401c9b30ee170a71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2020
ms.locfileid: "92638722"
---
# <a name="hp-reverb-g2-controllers-in-unreal"></a>Unreal の HP リバーブ G2 コントローラー 

## <a name="getting-started"></a>作業の開始

> [!IMPORTANT]
> HP Motion Controller プラグインにアクセスするには、unreal Engine 4.26 と OpenXR または SteamVR が必要です。 HP リバーブ G2 コントローラーを使用する必要があります。

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a>既存の OpenXR アプリの移植 

HP Mixed Reality コントローラーのコントローラーバインドがゲームに存在しない場合、OpenXR ランタイムは、既存のバインドをアクティブコントローラーに再マップしようとします。  この場合、ゲームには Oculus Touch バインドがあり、HP Mixed Reality コントローラーバインドはありません。

![コントローラーバインドが存在しない場合に既存のバインドを再マップする](images/reverb-g2-img-04.png)

イベントは依然として発生しますが、ゲームで適切なメニューボタンなどのコントローラー固有のバインドを使用する必要がある場合は、HP Mixed Reality 対話プロファイルを使用する必要があります。  アクションごとに複数のコントローラーバインドを指定して、さまざまなデバイスのサポートを強化することができます。
   
![複数のコントローラーバインドの使用](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a>入力アクションマッピングの追加 

新しいアクションを定義し、[HP Mixed Reality Controller] セクションのいずれかのキー押下にマップします。

![新しいアクションとマッピングの定義](images/reverb-g2-img-02.png)

HP リバーブ G2 コントローラーには、"つかみ軸" バインドを持つ軸マッピングで使用できるアナロググリップもあります。  グリップボタンが完全に押されたときにアクションのマッピングに使用される、別のつかみバインドがあります。 

![つかみ軸のバインドの使用](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a>入力イベントの追加

ブループリントを右クリックし、入力システムから新しいアクション名を検索して、これらのアクションのイベントを追加します。  ここでは、ブループリントは、現在のボタンと軸の状態を出力する print 文字列を使用してイベントに応答しています。

![イベントに応答し、現在のボタンと軸の状態を出力するブループリント](images/reverb-g2-img-06.png)

### <a name="using-input"></a>入力の使用 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a>関連項目
* [SteamVR 入力](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [Windows Mixed Reality で SteamVR を使用する](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [Unreal Player カメラ](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)