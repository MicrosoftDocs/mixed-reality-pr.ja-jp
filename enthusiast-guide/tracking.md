---
title: Faq の追跡
description: Windows Mixed Reality の高度なトラブルシューティングは、標準のコンシューマーサポートドキュメントを超えています。
ms.topic: article
keywords: Windows Mixed Reality、Mixed Reality、Virtual Reality、VR、MR、トラブルシューティング、エラー、ヘルプ、サポート、追跡
ms.openlocfilehash: b29df6f17bed52d3115faede10cdce91a7ea637f
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91685703"
---
# <a name="tracking-faqs"></a><span data-ttu-id="89c9d-104">Faq の追跡</span><span class="sxs-lookup"><span data-stu-id="89c9d-104">Tracking FAQs</span></span>

## <a name="my-headset-has-stopped-tracking"></a><span data-ttu-id="89c9d-105">ヘッドセットの追跡が停止しました。</span><span class="sxs-lookup"><span data-stu-id="89c9d-105">My headset has stopped tracking.</span></span>

<span data-ttu-id="89c9d-106">ライトが点灯していること、およびヘッドセットの前面に obstructing 追跡カメラが何もないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-106">Make sure the lights are on, and that there isn't anything obstructing the inside-out tracking cameras on the front of your headset.</span></span> <span data-ttu-id="89c9d-107">追跡が失われた場合、再開に数秒かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="89c9d-107">If tracking is lost, it can take a few seconds to resume.</span></span> <span data-ttu-id="89c9d-108">再開されない場合は、Windows Mixed Reality ポータルを再起動します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-108">If it doesn't resume, restart the Windows Mixed Reality Portal.</span></span> 

## <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a><span data-ttu-id="89c9d-109">このように見えますが、変換できません (3D で行き詰まっています)。</span><span class="sxs-lookup"><span data-stu-id="89c9d-109">I can look around but I can't translate (I'm stuck in 3DOF).</span></span>

<span data-ttu-id="89c9d-110">これは、追跡システムがポーズを生成できないか、またはアプリケーションが新しいポーズデータを使用してレンダリングを停止したことを意味します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-110">This means that the tracking system cannot generate pose, or the application has stopped using new pose data to render.</span></span> <span data-ttu-id="89c9d-111">次の点を確認します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-111">Check the following:</span></span>
* <span data-ttu-id="89c9d-112">部屋に十分な光があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-112">Make sure the room has enough light.</span></span>
* <span data-ttu-id="89c9d-113">トラックするのに十分な情報がルームにあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-113">Make sure the room has enough details to track.</span></span>
* <span data-ttu-id="89c9d-114">デバイスを取り外し、Windows Mixed Reality を閉じて、デバイスにもう一度接続します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-114">Unplug the device, close Windows Mixed Reality, and plug in the device again.</span></span>
* <span data-ttu-id="89c9d-115">メッセージが引き続き表示される場合は、[カスタマーサポート](https://support.microsoft.com/)にお問い合わせください</span><span class="sxs-lookup"><span data-stu-id="89c9d-115">If the message persists, contact [customer support](https://support.microsoft.com/)</span></span>

## <a name="the-view-in-the-hmd-is-completely-frozen"></a><span data-ttu-id="89c9d-116">HMD のビューは完全に固定されています。</span><span class="sxs-lookup"><span data-stu-id="89c9d-116">The view in the HMD is completely frozen.</span></span>

<span data-ttu-id="89c9d-117">これは通常、アプリケーションまたはシステムレベルのコンポーネントで障害が発生したことを意味します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-117">This usually means the application or a system level component has failed.</span></span> <span data-ttu-id="89c9d-118">試行する操作:</span><span class="sxs-lookup"><span data-stu-id="89c9d-118">Try to:</span></span>
1. <span data-ttu-id="89c9d-119">アプリケーションを終了するには、[ホーム] ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-119">Press the "home" button to leave the application.</span></span>
2. <span data-ttu-id="89c9d-120">デバイスを取り外し、MRP を閉じて、デバイスを再び接続します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-120">Unplug the device, close MRP and plug the device back in.</span></span>
3. <span data-ttu-id="89c9d-121">PC を再起動します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-121">Restart the PC.</span></span>

## <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-down-before-returning-to-normal"></a><span data-ttu-id="89c9d-122">この世界では、通常に戻る前に、froze に傾いたり反転したりしています。</span><span class="sxs-lookup"><span data-stu-id="89c9d-122">The world briefly froze and perhaps tilted or flipped upside down before returning to normal.</span></span>

<span data-ttu-id="89c9d-123">これは、アプリケーションまたはシステムレベルのコンポーネントによって致命的なエラーが発生したか、一時的にメモリまたは CPU リソースが不足していることが原因である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="89c9d-123">This could be caused by an application or system level component hitting a fatal error, or a temporary lack of memory or CPU resources.</span></span> <span data-ttu-id="89c9d-124">確認するには:</span><span class="sxs-lookup"><span data-stu-id="89c9d-124">To check:</span></span>
1. <span data-ttu-id="89c9d-125">タスクマネージャーを開き、少なくとも20% の CPU が空いていることを確認し、400 MB のメモリが使用可能であり、ディスク IO が80% 未満になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-125">Open Task Manager and ensure that at least 20% of the CPU is free, 400MB of memory is available and disk IO should be below 80%.</span></span>
2. <span data-ttu-id="89c9d-126">**イベントビューアー > Windows ログ > アプリケーション** ] に移動して、凍結の時間の前後のエラーを探します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-126">Go to **Event Viewer > Windows Logs > Application** to look for any errors from around the time of the freeze.</span></span> <span data-ttu-id="89c9d-127">HoloLens センサー、Mixed Reality、またはその時間内に実行されていたアプリケーションを指しているものを探します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-127">Look for anything that refers to HoloLens sensors, Mixed Reality, or the application that you were running around that time.</span></span> <span data-ttu-id="89c9d-128">これらのログは、エラーの原因を説明する場合があります。</span><span class="sxs-lookup"><span data-stu-id="89c9d-128">Those logs might explain what caused the failure.</span></span>
3. <span data-ttu-id="89c9d-129">問題が解決しない場合は、PC を再起動します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-129">Restart the PC if the problem persists.</span></span>

## <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a><span data-ttu-id="89c9d-130">少し反転して、通常の状態に戻ります。</span><span class="sxs-lookup"><span data-stu-id="89c9d-130">The world flipped upside down momentarily and returned to normal.</span></span>

<span data-ttu-id="89c9d-131">これは通常、ヘッドセットからセンサーデータを取得して追跡アルゴリズムに通知するときのエラーが原因で発生します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-131">This is typically caused by errors in obtaining sensor data from the headset to inform the tracking algorithms.</span></span> <span data-ttu-id="89c9d-132">頻繁に発生する場合:</span><span class="sxs-lookup"><span data-stu-id="89c9d-132">If this happens frequently:</span></span>
1. <span data-ttu-id="89c9d-133">ヘッドセットを別の USB 3.0 ポートに接続します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-133">Plug the headset into a different USB 3.0 port.</span></span>
2. <span data-ttu-id="89c9d-134">ヘッドホンを USB 3.0 ハブではなく PC に直接接続します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-134">Plug the headset directly into the PC rather than into a USB 3.0 hub.</span></span>
3. <span data-ttu-id="89c9d-135">問題が解決しない場合は、 [カスタマーサポート](https://support.microsoft.com/)にお問い合わせください。</span><span class="sxs-lookup"><span data-stu-id="89c9d-135">If the problem persists, contact [customer support](https://support.microsoft.com/).</span></span>

## <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-in-windows-mixed-reality"></a><span data-ttu-id="89c9d-136">世界は傾いていますが、Windows Mixed Reality 内で移動したり、話したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="89c9d-136">The world is tilted but I can navigate and walk around in Windows Mixed Reality.</span></span>

<span data-ttu-id="89c9d-137">センサーデータエラーが PC 上の環境データに記録された場合、Windows Mixed Reality が傾いている場合があります。</span><span class="sxs-lookup"><span data-stu-id="89c9d-137">If sensor data errors are recorded into the environment data on your PC, it can cause Windows Mixed Reality to appear tilted, sometimes permanently.</span></span> <span data-ttu-id="89c9d-138">この問題を解決するには:</span><span class="sxs-lookup"><span data-stu-id="89c9d-138">To fix this:</span></span>
1. <span data-ttu-id="89c9d-139">ヘッドセットを取り外し、Windows Mixed Reality を閉じて、ヘッドセットを再び接続します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-139">Unplug the headset, close Windows Mixed Reality and plug the headset back in.</span></span>
2. <span data-ttu-id="89c9d-140">PC を再起動します。</span><span class="sxs-lookup"><span data-stu-id="89c9d-140">Restart the PC.</span></span>
3. <span data-ttu-id="89c9d-141">環境データをクリアします。</span><span class="sxs-lookup"><span data-stu-id="89c9d-141">Clear your environment data.</span></span>

