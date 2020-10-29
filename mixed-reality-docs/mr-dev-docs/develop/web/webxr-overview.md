---
title: Windows Mixed Reality での WebXR の使用
description: Windows Mixed Reality での WebXR の使用と開発の概要
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: WebXR、WinMR、WebAR、WebVR、WindowsMixedReality、HoloLens、windows mixed reality、web vr、web xr、web mr、web ar、360、360 video、360ビデオ、360 photo、360 photos、360コンテンツ、イマーシブ web、immersiveweb、IW
ms.openlocfilehash: 01e6cd44e9879cd7fd9b11e178134eaf364cc53c
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91691191"
---
# <a name="webxr-overview"></a><span data-ttu-id="754b7-104">WebXR の概要</span><span class="sxs-lookup"><span data-stu-id="754b7-104">WebXR Overview</span></span>

## <a name="what-is-webxr"></a><span data-ttu-id="754b7-105">WebXR とは</span><span class="sxs-lookup"><span data-stu-id="754b7-105">What is WebXR</span></span>

<span data-ttu-id="754b7-106">**WebXR DEVICE API** は、 **Web** 上の **センサー** や **ヘッドマウントされたディスプレイ** など、 **仮想現実 (VR)** デバイスおよび拡張 **現実 (AR)** デバイスにアクセスするためのものです。</span><span class="sxs-lookup"><span data-stu-id="754b7-106">The **WebXR device API** is for accessing **virtual reality (VR)** and **augmented reality (AR)** devices, including **sensors** and **head-mounted displays** on the **Web** .</span></span> <span data-ttu-id="754b7-107">WebXR device API は現在 Microsoft Edge で使用でき、Chrome バージョン79以降では WebXR を既定としてサポートしています。</span><span class="sxs-lookup"><span data-stu-id="754b7-107">WebXR device API is currently available on Microsoft Edge and Chrome version 79 and later versions supports WebXR as a default.</span></span> <span data-ttu-id="754b7-108">WebXR のブラウザーの最新のサポート状態は、 [caniuse.com](https://caniuse.com/#search=webxr)で確認できます。</span><span class="sxs-lookup"><span data-stu-id="754b7-108">You can check the latest browser support status for WebXR at [caniuse.com](https://caniuse.com/#search=webxr).</span></span>

<span data-ttu-id="754b7-109">[Windows Mixed Reality と新しい Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)の詳細については、「新[機能](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="754b7-109">Learn more about the [Windows Mixed Reality and the new Microsoft Edge](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)in [What's new](https://docs.microsoft.com/windows/mixed-reality/mrtk-porting-guide) section.</span></span>

## <a name="viewing-webxr"></a><span data-ttu-id="754b7-110">WebXR の表示</span><span class="sxs-lookup"><span data-stu-id="754b7-110">Viewing WebXR</span></span>

<span data-ttu-id="754b7-111">ブラウザーが WebXR をサポートしているかどうかをテストするには、ブラウザーで [WebXR サンプル](https://immersive-web.github.io/webxr-samples/) に移動します。</span><span class="sxs-lookup"><span data-stu-id="754b7-111">To test if your browser supports WebXR, you can navigate to [WebXR Samples](https://immersive-web.github.io/webxr-samples/) in your browser.</span></span>

## <a name="see-also"></a><span data-ttu-id="754b7-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="754b7-112">See Also</span></span>

* [<span data-ttu-id="754b7-113">WebXR Device API 仕様</span><span class="sxs-lookup"><span data-stu-id="754b7-113">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="754b7-114">WebXR Device API のドキュメント</span><span class="sxs-lookup"><span data-stu-id="754b7-114">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="754b7-115">Immersiveweb</span><span class="sxs-lookup"><span data-stu-id="754b7-115">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="754b7-116">WebXR のサンプル</span><span class="sxs-lookup"><span data-stu-id="754b7-116">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="754b7-117">Windows Mixed Reality と新しい Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="754b7-117">Windows Mixed Reality and the new Microsoft Edge</span></span>](https://docs.microsoft.com/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="754b7-118">イマーシブ Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="754b7-118">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="754b7-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="754b7-119">[WebGL API](https://msdn.microsoft.com/library/bg182648(v=vs.85).aspx)</span></span>
* <span data-ttu-id="754b7-120">[ゲームパッド API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) と [ゲームパッド拡張機能](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="754b7-120">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="754b7-121">WebGL での失われたコンテキストの処理</span><span class="sxs-lookup"><span data-stu-id="754b7-121">Handling Lost Context in WebGL</span></span>](https://www.khronos.org/webgl/wiki/HandlingContextLost)
* [<span data-ttu-id="754b7-122">Pointerlock ロック</span><span class="sxs-lookup"><span data-stu-id="754b7-122">Pointerlock</span></span>](https://www.w3.org/TR/pointerlock/)
* [<span data-ttu-id="754b7-123">glTF</span><span class="sxs-lookup"><span data-stu-id="754b7-123">glTF</span></span>](https://www.khronos.org/gltf)
* [<span data-ttu-id="754b7-124">Babylon.js を使用した WebXR エクスペリエンスの作成</span><span class="sxs-lookup"><span data-stu-id="754b7-124">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="754b7-125">イマーシブ web コミュニティグループ</span><span class="sxs-lookup"><span data-stu-id="754b7-125">Immersive web community group</span></span>](https://www.w3.org/community/immersive-web/)
