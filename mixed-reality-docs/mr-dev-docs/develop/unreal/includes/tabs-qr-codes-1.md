---
ms.openlocfilehash: bcd9ae057f289d85d1f12d5cb79258bc3bb87ace
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96443699"
---
# <a name="425"></a>[<span data-ttu-id="e46de-101">4.25</span><span class="sxs-lookup"><span data-stu-id="e46de-101">4.25</span></span>](#tab/425)

<span data-ttu-id="e46de-102">UE 4.25 に固有の追加の有効化手順はありません。</span><span class="sxs-lookup"><span data-stu-id="e46de-102">There are no additional enabling steps specific to UE 4.25.</span></span>

# <a name="426"></a>[<span data-ttu-id="e46de-103">4.26</span><span class="sxs-lookup"><span data-stu-id="e46de-103">4.26</span></span>](#tab/426)

<span data-ttu-id="e46de-104">UE 4.26 を使用している場合は、AR セッションを開始した後で QR コードの追跡を初期化する必要があるため、次のブループリントの設定を使用して短い遅延を追加することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e46de-104">If you're using UE 4.26, we recommend using the following blueprint setup to add a small delay, because QR code tracking must be initialized AFTER starting an AR Session:</span></span>

![遅延を含む ARCapture 切り替え関数のブループリント](../images/qr-codes-img-01.png)
