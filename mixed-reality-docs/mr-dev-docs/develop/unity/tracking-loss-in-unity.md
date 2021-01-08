---
title: Unity での損失の追跡
description: Unity mixed reality アプリ内で、手動および既定の追跡損失を処理する方法について説明します。
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Unity、損失の追跡、損失の画像の追跡、ポーリング、mixed reality ヘッドセット、windows mixed reality ヘッドセット、仮想現実のヘッドセット
ms.openlocfilehash: 39ce4e079886b27ed35c419a3b3913c6700e0d32
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009852"
---
# <a name="tracking-loss-in-unity"></a><span data-ttu-id="a5af1-104">Unity での損失の追跡</span><span class="sxs-lookup"><span data-stu-id="a5af1-104">Tracking loss in Unity</span></span>

<span data-ttu-id="a5af1-105">デバイスが世界中で見つからない場合、アプリでは "損失の追跡" が発生します。</span><span class="sxs-lookup"><span data-stu-id="a5af1-105">When the device can't locate itself in the world, the app experiences "tracking loss".</span></span> <span data-ttu-id="a5af1-106">既定では、Unity は更新ループを一時停止し、追跡が失われるたびにユーザーにスプラッシュイメージを表示します。</span><span class="sxs-lookup"><span data-stu-id="a5af1-106">By default, Unity will pause the update loop and display a splash image to the user anytime tracking is lost.</span></span> <span data-ttu-id="a5af1-107">追跡が再開されると、スプラッシュイメージが消え、update ループが続行します。</span><span class="sxs-lookup"><span data-stu-id="a5af1-107">Once tracking is regained, the splash image goes away and the update loop continues.</span></span>

<span data-ttu-id="a5af1-108">別の方法として、ユーザーは設定から除外することによって、この移行を手動で処理できます。</span><span class="sxs-lookup"><span data-stu-id="a5af1-108">As an alternative, the user can manually handle this transition by opting out of the setting.</span></span> <span data-ttu-id="a5af1-109">コンテンツを処理する処理が何も行われていない場合、追跡が失われても、すべてのコンテンツが本文でロックされているように見えます。</span><span class="sxs-lookup"><span data-stu-id="a5af1-109">All content will seem to become body locked during tracking loss if nothing is done to handle it.</span></span>

## <a name="default-handling"></a><span data-ttu-id="a5af1-110">既定の処理</span><span class="sxs-lookup"><span data-stu-id="a5af1-110">Default Handling</span></span>

<span data-ttu-id="a5af1-111">既定では、更新ループとすべてのメッセージとイベントは、追跡が失われている間停止します。</span><span class="sxs-lookup"><span data-stu-id="a5af1-111">The update loop and all messages and events will stop for the duration of tracking loss by default.</span></span> <span data-ttu-id="a5af1-112">同時に、画像がユーザーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="a5af1-112">At that same time, an image will be displayed to the user.</span></span> <span data-ttu-id="a5af1-113">このイメージをカスタマイズするには、[編集->設定->プレーヤー] に移動し、[スプラッシュイメージ] をクリックして、Holographic Tracking ロスイメージを設定します。</span><span class="sxs-lookup"><span data-stu-id="a5af1-113">You can customize this image by going to Edit->Settings->Player, clicking Splash Image, and setting the Holographic Tracking Loss image.</span></span>

## <a name="manual-handling"></a><span data-ttu-id="a5af1-114">手動処理</span><span class="sxs-lookup"><span data-stu-id="a5af1-114">Manual Handling</span></span>

<span data-ttu-id="a5af1-115">追跡の損失を手動で処理するには、 [  >  **プロジェクト設定** の編集]、[  >    >  **設定] タブの [ユニバーサル Windows プラットフォーム設定] タブ** の [スプラッシュイメージ] [Windows Holographic] の方にアクセスし、[  >    >  追跡損失の一時停止と画像の表示] をオフにします。</span><span class="sxs-lookup"><span data-stu-id="a5af1-115">To manually handle tracking loss, you need to go to **Edit** > **Project Settings** > **Player** > **Universal Windows Platform settings tab** > **Splash Image** > **Windows Holographic** and uncheck "On Tracking Loss Pause and Show Image".</span></span> <span data-ttu-id="a5af1-116">その後、以下で指定した Api を使用して、変更の追跡を処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5af1-116">After which, you need to handle tracking changes with the APIs specified below.</span></span>

<span data-ttu-id="a5af1-117">**名前空間:** *UNITYENGINE. XR*</span><span class="sxs-lookup"><span data-stu-id="a5af1-117">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="a5af1-118">**型:** *WorldManager*</span><span class="sxs-lookup"><span data-stu-id="a5af1-118">**Type:** *WorldManager*</span></span>

* <span data-ttu-id="a5af1-119">World Manager は、紛失/獲得された追跡 (*WorldManager OnPositionalLocatorStateChanged*) を検出するイベントを公開し、プロパティを表示して現在の状態 (WorldManager) を照会し *ます。*</span><span class="sxs-lookup"><span data-stu-id="a5af1-119">World Manager exposes an event to detect tracking lost/gained (*WorldManager.OnPositionalLocatorStateChanged*) and a property to query the current state (*WorldManager.state*)</span></span>
* <span data-ttu-id="a5af1-120">追跡状態がアクティブでない場合、ユーザーが変換した場合でも、カメラは仮想世界では変換されないように見えます。</span><span class="sxs-lookup"><span data-stu-id="a5af1-120">When the tracking state isn't active, the camera won't appear to translate in the virtual world even as the user translates.</span></span> <span data-ttu-id="a5af1-121">オブジェクトは、物理的な場所に対応しなくなり、すべての本文がロックされて表示されます。</span><span class="sxs-lookup"><span data-stu-id="a5af1-121">Objects will no longer correspond to any physical location and all will appear body locked.</span></span>

<span data-ttu-id="a5af1-122">変更の追跡を独自に処理する場合は、各フレームの状態プロパティをポーリングするか、 *OnPositionalLocatorStateChanged* イベントを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a5af1-122">When handling tracking changes on your own, you either need to poll for the state property each frame or handle the *OnPositionalLocatorStateChanged* event.</span></span>

### <a name="polling"></a><span data-ttu-id="a5af1-123">ポーリング</span><span class="sxs-lookup"><span data-stu-id="a5af1-123">Polling</span></span>

<span data-ttu-id="a5af1-124">最も重要な状態は、 *Positionallocatorstate. Active です。* これは、追跡が完全に機能していることを意味します。</span><span class="sxs-lookup"><span data-stu-id="a5af1-124">The most important state is *PositionalLocatorState.Active*, which means tracking is fully functional.</span></span> <span data-ttu-id="a5af1-125">その他の状態では、メインカメラへの回転デルタのみが発生します。</span><span class="sxs-lookup"><span data-stu-id="a5af1-125">Any other state will result in only rotational deltas to the main camera.</span></span> <span data-ttu-id="a5af1-126">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="a5af1-126">For example:</span></span>

```cs
void Update()
{
    switch (UnityEngine.XR.WSA.WorldManager.state)
    {
        case PositionalLocatorState.Active:
            // handle active
            break;
        case PositionalLocatorState.Activating:
        case PositionalLocatorState.Inhibited:
        case PositionalLocatorState.OrientationOnly:
        case PositionalLocatorState.Unavailable:
        default:
            // only rotational information is available
            break;
    }
}
```

### <a name="handling-the-onpositionallocatorstatechanged-event"></a><span data-ttu-id="a5af1-127">OnPositionalLocatorStateChanged イベントの処理</span><span class="sxs-lookup"><span data-stu-id="a5af1-127">Handling the OnPositionalLocatorStateChanged event</span></span>

<span data-ttu-id="a5af1-128">さらに便利で、 *OnPositionalLocatorStateChanged* にサブスクライブして遷移を処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="a5af1-128">More conveniently, you can also subscribe to *OnPositionalLocatorStateChanged* to handle the transitions:</span></span>

```cs
void Start()
{
    UnityEngine.XR.WSA.WorldManager.OnPositionalLocatorStateChanged += WorldManager_OnPositionalLocatorStateChanged;
}

private void WorldManager_OnPositionalLocatorStateChanged(PositionalLocatorState oldState, PositionalLocatorState newState)
{
    if (newState == PositionalLocatorState.Active)
    {
        // Handle becoming active
    }
    else
    {
        // Handle becoming rotational only
    }
}
```

## <a name="see-also"></a><span data-ttu-id="a5af1-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a5af1-129">See also</span></span>

* [<span data-ttu-id="a5af1-130">DirectX での追跡損失の処理</span><span class="sxs-lookup"><span data-stu-id="a5af1-130">Handling tracking loss in DirectX</span></span>](../native/coordinate-systems-in-directx.md#handling-tracking-loss)
