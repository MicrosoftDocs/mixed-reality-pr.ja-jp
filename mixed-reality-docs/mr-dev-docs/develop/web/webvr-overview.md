---
title: WebVR の概要
description: Windows Mixed Reality イマーシブヘッドセットで実行される WebVR アプリケーションの使用と開発の基本について説明します。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebVR, WebXR, WinMR, WebAR, web vr, web xr, web mr, web ar, 360, 360 ビデオ, 360 ビデオ, 360 写真, 360 写真, 360 コンテンツ, イマーシブ web, immersiveweb, IW
ms.openlocfilehash: bf0335c0fa7fd42f60a20690d22b2ef9a4f6859a
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006962"
---
# <a name="webvr-overview"></a><span data-ttu-id="9d7eb-104">WebVR の概要</span><span class="sxs-lookup"><span data-stu-id="9d7eb-104">WebVR Overview</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9d7eb-105">**Webvr 1.1 API** は非推奨となり、 **WebXR デバイス API** s に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="9d7eb-105">**WebVR 1.1 API** s are deprecated and replaced by **WebXR Device API** s.</span></span>

<span data-ttu-id="9d7eb-106">WebVR 1.1 Api は非推奨とされ、Chrome と新しい Microsoft Edge から削除されました。</span><span class="sxs-lookup"><span data-stu-id="9d7eb-106">WebVR 1.1 APIs are deprecated and removed from Chrome and the new Microsoft Edge.</span></span> <span data-ttu-id="9d7eb-107">WebVR Api は、WebXR デバイス Api に置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="9d7eb-107">WebVR APIs are superseded by WebXR Device APIs.</span></span> <span data-ttu-id="9d7eb-108">[Caniuse.com](https://caniuse.com/#search=webvr)で現在 Webvr api をサポートしているブラウザーの一覧を確認できます。</span><span class="sxs-lookup"><span data-stu-id="9d7eb-108">You can check the list of browsers currently supporting WebVR APIs on [caniuse.com](https://caniuse.com/#search=webvr).</span></span>

## <a name="viewing-webvr-content-in-windows-mixed-reality-immersive-headsets"></a><span data-ttu-id="9d7eb-109">Windows Mixed Reality イマーシブヘッドセットの WebVR コンテンツの表示</span><span class="sxs-lookup"><span data-stu-id="9d7eb-109">Viewing WebVR content in Windows Mixed Reality immersive headsets</span></span>

<span data-ttu-id="9d7eb-110">**以前のバージョンの Microsoft Edge (15-18)** でイマーシブヘッドセットの webvr コンテンツにアクセスする手順については、「[ユーザーズガイド](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d7eb-110">Instructions for accessing WebVR content in your immersive headsets with **older versions of Microsoft Edge(15-18)** can be found in the [Enthusiast's Guide](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/webvr).</span></span> <span data-ttu-id="9d7eb-111">Edge ブラウザーの検索バーに「edge://version/」と入力すると、エッジバージョンを確認できます。</span><span class="sxs-lookup"><span data-stu-id="9d7eb-111">You can check your edge version by typing "edge://version/" in your Edge browsers search bar.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d7eb-112">参照</span><span class="sxs-lookup"><span data-stu-id="9d7eb-112">See Also</span></span>

* [<span data-ttu-id="9d7eb-113">WebXR の概要</span><span class="sxs-lookup"><span data-stu-id="9d7eb-113">WebXR Overview</span></span>](webxr-overview.md)
* [<span data-ttu-id="9d7eb-114">WebXR Device API 仕様</span><span class="sxs-lookup"><span data-stu-id="9d7eb-114">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="9d7eb-115">Windows Mixed Reality と新しい Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="9d7eb-115">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge)
* [<span data-ttu-id="9d7eb-116">WebVR 情報</span><span class="sxs-lookup"><span data-stu-id="9d7eb-116">WebVR information</span></span>](https://webvr.info)
* [<span data-ttu-id="9d7eb-117">WebVR 仕様</span><span class="sxs-lookup"><span data-stu-id="9d7eb-117">WebVR specification</span></span>](https://w3c.github.io/webvr/)
* <span data-ttu-id="9d7eb-118">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="9d7eb-118">[WebVR API](https://msdn.microsoft.com/library/mt806281(v=vs.85).aspx)</span></span>
* <span data-ttu-id="9d7eb-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="9d7eb-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="9d7eb-120">[ゲームパッド API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) と [ゲームパッド拡張機能](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="9d7eb-120">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="9d7eb-121">WebGL での失われたコンテキストの処理</span><span class="sxs-lookup"><span data-stu-id="9d7eb-121">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="9d7eb-122">Pointerlock ロック</span><span class="sxs-lookup"><span data-stu-id="9d7eb-122">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="9d7eb-123">glTF</span><span class="sxs-lookup"><span data-stu-id="9d7eb-123">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="9d7eb-124">Babylon.js を使用した WebVR の有効化</span><span class="sxs-lookup"><span data-stu-id="9d7eb-124">Using Babylon.js to enable WebVR</span></span>](https://docs.microsoft.com/windows/uwp/get-started/adding-webvr-to-a-babylonjs-game)
