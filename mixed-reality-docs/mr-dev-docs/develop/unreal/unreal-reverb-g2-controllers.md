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
# <a name="hp-reverb-g2-controllers-in-unreal"></a><span data-ttu-id="fa3eb-104">Unreal の HP リバーブ G2 コントローラー</span><span class="sxs-lookup"><span data-stu-id="fa3eb-104">HP Reverb G2 Controllers in Unreal</span></span> 

## <a name="getting-started"></a><span data-ttu-id="fa3eb-105">作業の開始</span><span class="sxs-lookup"><span data-stu-id="fa3eb-105">Getting started</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fa3eb-106">HP Motion Controller プラグインにアクセスするには、unreal Engine 4.26 と OpenXR または SteamVR が必要です。 HP リバーブ G2 コントローラーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa3eb-106">Unreal Engine 4.26 and either OpenXR or SteamVR is required to access the HP Motion Controller plugin you'll need to work with the HP Reverb G2 controllers.</span></span>

[!INCLUDE[](includes/tabs-g2-controllers-in-unreal.md)]

## <a name="porting-an-existing-openxr-app"></a><span data-ttu-id="fa3eb-107">既存の OpenXR アプリの移植</span><span class="sxs-lookup"><span data-stu-id="fa3eb-107">Porting an existing OpenXR app</span></span> 

<span data-ttu-id="fa3eb-108">HP Mixed Reality コントローラーのコントローラーバインドがゲームに存在しない場合、OpenXR ランタイムは、既存のバインドをアクティブコントローラーに再マップしようとします。</span><span class="sxs-lookup"><span data-stu-id="fa3eb-108">If no controller bindings exist in the game for the HP Mixed Reality Controller, the OpenXR runtime will attempt to remap the existing bindings to the active controller.</span></span>  <span data-ttu-id="fa3eb-109">この場合、ゲームには Oculus Touch バインドがあり、HP Mixed Reality コントローラーバインドはありません。</span><span class="sxs-lookup"><span data-stu-id="fa3eb-109">In this case, the game has Oculus Touch bindings and no HP Mixed Reality Controller bindings.</span></span>

![コントローラーバインドが存在しない場合に既存のバインドを再マップする](images/reverb-g2-img-04.png)

<span data-ttu-id="fa3eb-111">イベントは依然として発生しますが、ゲームで適切なメニューボタンなどのコントローラー固有のバインドを使用する必要がある場合は、HP Mixed Reality 対話プロファイルを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fa3eb-111">The events will still fire, but if the game needs to make use of controller specific bindings, like the right menu button, the HP Mixed Reality interaction profile must be used.</span></span>  <span data-ttu-id="fa3eb-112">アクションごとに複数のコントローラーバインドを指定して、さまざまなデバイスのサポートを強化することができます。</span><span class="sxs-lookup"><span data-stu-id="fa3eb-112">Multiple controller bindings can be specified per action to better support different devices.</span></span>
   
![複数のコントローラーバインドの使用](images/reverb-g2-img-05.png)

## <a name="adding-input-action-mappings"></a><span data-ttu-id="fa3eb-114">入力アクションマッピングの追加</span><span class="sxs-lookup"><span data-stu-id="fa3eb-114">Adding input action mappings</span></span> 

<span data-ttu-id="fa3eb-115">新しいアクションを定義し、[HP Mixed Reality Controller] セクションのいずれかのキー押下にマップします。</span><span class="sxs-lookup"><span data-stu-id="fa3eb-115">Define a new action and map to one of the key presses in the HP Mixed Reality Controller section.</span></span>

![新しいアクションとマッピングの定義](images/reverb-g2-img-02.png)

<span data-ttu-id="fa3eb-117">HP リバーブ G2 コントローラーには、"つかみ軸" バインドを持つ軸マッピングで使用できるアナロググリップもあります。</span><span class="sxs-lookup"><span data-stu-id="fa3eb-117">The HP Reverb G2 controller also has an analog grip, which can be used in the axis mappings with the “Squeeze Axis” binding.</span></span>  <span data-ttu-id="fa3eb-118">グリップボタンが完全に押されたときにアクションのマッピングに使用される、別のつかみバインドがあります。</span><span class="sxs-lookup"><span data-stu-id="fa3eb-118">There is a separate Squeeze binding, which should be used for action mappings when the grip button is fully pressed.</span></span> 

![つかみ軸のバインドの使用](images/reverb-g2-img-03.png)

## <a name="adding-input-events"></a><span data-ttu-id="fa3eb-120">入力イベントの追加</span><span class="sxs-lookup"><span data-stu-id="fa3eb-120">Adding input events</span></span>

<span data-ttu-id="fa3eb-121">ブループリントを右クリックし、入力システムから新しいアクション名を検索して、これらのアクションのイベントを追加します。</span><span class="sxs-lookup"><span data-stu-id="fa3eb-121">Right click on a Blueprint and search for the new action names from the input system to add events for these actions.</span></span>  <span data-ttu-id="fa3eb-122">ここでは、ブループリントは、現在のボタンと軸の状態を出力する print 文字列を使用してイベントに応答しています。</span><span class="sxs-lookup"><span data-stu-id="fa3eb-122">Here the Blueprint is responding to the events with a print string outputting the current button and axis state.</span></span>

![イベントに応答し、現在のボタンと軸の状態を出力するブループリント](images/reverb-g2-img-06.png)

### <a name="using-input"></a><span data-ttu-id="fa3eb-124">入力の使用</span><span class="sxs-lookup"><span data-stu-id="fa3eb-124">Using input</span></span> 

[!INCLUDE[](includes/tabs-g2-controller-mapping-in-unreal.md)]

## <a name="see-also"></a><span data-ttu-id="fa3eb-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="fa3eb-125">See also</span></span>
* [<span data-ttu-id="fa3eb-126">SteamVR 入力</span><span class="sxs-lookup"><span data-stu-id="fa3eb-126">SteamVR Input</span></span>](https://docs.unrealengine.com/Platforms/VR/SteamVR/HowTo/SteamVRInput/index.html)
* [<span data-ttu-id="fa3eb-127">Windows Mixed Reality で SteamVR を使用する</span><span class="sxs-lookup"><span data-stu-id="fa3eb-127">Using SteamVR with Windows Mixed Reality</span></span>](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/using-steamvr-with-windows-mixed-reality)
* [<span data-ttu-id="fa3eb-128">Unreal Player カメラ</span><span class="sxs-lookup"><span data-stu-id="fa3eb-128">Unreal Player Camera</span></span>](https://docs.unrealengine.com/Programming/Tutorials/PlayerCamera/3/index.html)