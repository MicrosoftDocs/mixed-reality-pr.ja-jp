---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 0509cf6c57067cffd75a0189106e3369e9ecc5c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96855885"
---
# <a name="windows-mixed-reality"></a>[<span data-ttu-id="411e5-101">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="411e5-101">Windows Mixed Reality</span></span>](#tab/wmr)

| <span data-ttu-id="411e5-102">オプション</span><span class="sxs-lookup"><span data-stu-id="411e5-102">Option</span></span> | <span data-ttu-id="411e5-103">説明</span><span class="sxs-lookup"><span data-stu-id="411e5-103">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | <span data-ttu-id="411e5-104">接続先の HoloLens 2 デバイスの IP アドレス (およびオプションのポート) を取得します。</span><span class="sxs-lookup"><span data-stu-id="411e5-104">Takes the IP address (and optional port) of the HoloLens 2 device to connect to.</span></span> <span data-ttu-id="411e5-105">ポートが指定されていない場合、既定値は 8265 です。</span><span class="sxs-lookup"><span data-stu-id="411e5-105">If no port is provided, default to 8265.</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="411e5-106">(省略可能) 既定値は 8000 です。</span><span class="sxs-lookup"><span data-stu-id="411e5-106">(optional) Default 8000.</span></span> <span data-ttu-id="411e5-107">最大ネットワーク転送速度 (kb/秒)。</span><span class="sxs-lookup"><span data-stu-id="411e5-107">Max network transfer rate (kb/s).</span></span> |
| `-HoloLensRemotingListen` | <span data-ttu-id="411e5-108">(省略可能) リッスン サーバーを起動します</span><span class="sxs-lookup"><span data-stu-id="411e5-108">(optional) Start a listen server</span></span> |
| `-HoloLensRemotingListenPort=<port>` | <span data-ttu-id="411e5-109">(省略可能) リッスンするポートを取得します。</span><span class="sxs-lookup"><span data-stu-id="411e5-109">(optional) Takes the port to listen on.</span></span> <span data-ttu-id="411e5-110">HoloLens デバイスから PC または VM に接続するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="411e5-110">Used for connecting to a PC or VM from a HoloLens device.</span></span> |
| `-HoloLens1Remoting=<IP address>` | <span data-ttu-id="411e5-111">(4.26 では非推奨) 接続先の HoloLens 1 デバイスの IP アドレスを取得します</span><span class="sxs-lookup"><span data-stu-id="411e5-111">(deprecated in 4.26) Takes the IP address of the HoloLens 1 device to connect to</span></span> |

# <a name="openxr"></a>[<span data-ttu-id="411e5-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="411e5-112">OpenXR</span></span>](#tab/openxr)

| <span data-ttu-id="411e5-113">オプション</span><span class="sxs-lookup"><span data-stu-id="411e5-113">Option</span></span> | <span data-ttu-id="411e5-114">説明</span><span class="sxs-lookup"><span data-stu-id="411e5-114">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | <span data-ttu-id="411e5-115">接続先の HoloLens 2 デバイスの IP アドレス (およびオプションのポート、既定値は 8265)、またはアプリから接続のためにリッスンするポートを取得します。</span><span class="sxs-lookup"><span data-stu-id="411e5-115">Takes the IP address (and optional port, default 8265) of the HoloLens 2 device to connect to, or the port on which the app should listen on for connections.</span></span> |
| `-EnableAudio` | <span data-ttu-id="411e5-116">(省略可能) リモート処理時に PC からのオーディオを使用します</span><span class="sxs-lookup"><span data-stu-id="411e5-116">(optional) Use audio from PC when remoting</span></span>  |
| `-Listen` | <span data-ttu-id="411e5-117">(省略可能) リッスン サーバーを起動します</span><span class="sxs-lookup"><span data-stu-id="411e5-117">(optional) Start a listen server</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="411e5-118">(省略可能) 既定値は 8000 です。</span><span class="sxs-lookup"><span data-stu-id="411e5-118">(optional) Default 8000.</span></span> <span data-ttu-id="411e5-119">最大ネットワーク転送速度 (kb/秒)。</span><span class="sxs-lookup"><span data-stu-id="411e5-119">Max network transfer rate (kb/s).</span></span> |
| `-RemotingCodec=<codec>` | <span data-ttu-id="411e5-120">(省略可能) 接続コーデック</span><span class="sxs-lookup"><span data-stu-id="411e5-120">(optional) Connection codec</span></span>  |