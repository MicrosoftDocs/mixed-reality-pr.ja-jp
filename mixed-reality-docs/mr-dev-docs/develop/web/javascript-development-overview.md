---
title: JavaScript 開発の概要
description: Web、モバイル、および windows のイマーシブヘッドセットの JavaScript を使用した Mixed Reality 開発の概要。
author: yonet
ms.author: ayyonet
ms.date: 04/10/2020
ms.topic: article
keywords: JavaScript、WebXR、WinMR、WebAR、WebVR、WindowsMixedReality、HoloLens、windows mixed reality、web vr、web xr、web mr、web ar、360、360 video、360ビデオ、360 photo、360 photos、360コンテンツ、イマーシブ web、イマーシブ-web、IW、immersiveweb
ms.openlocfilehash: 573db6f739292b7e67148d260a5ba1880d24fb20
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98580323"
---
# <a name="javascript-development-overview"></a><span data-ttu-id="6595a-104">JavaScript 開発の概要</span><span class="sxs-lookup"><span data-stu-id="6595a-104">JavaScript development overview</span></span>

## <a name="mixed-reality-applications-on-the-web"></a><span data-ttu-id="6595a-105">Web 上の Mixed Reality アプリケーション</span><span class="sxs-lookup"><span data-stu-id="6595a-105">Mixed Reality applications on the web</span></span>

<span data-ttu-id="6595a-106">[WebXR Device api](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)と[非推奨の webvr api](webxr-overview.md)を使用して、Web 上で Mixed Reality 機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6595a-106">Mixed Reality features are available on the web by the use of [WebXR Device APIs](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API) and [deprecated WebVR APIs](webxr-overview.md).</span></span> <span data-ttu-id="6595a-107">WebXR の全機能をサポートしていないブラウザーでは、 [WebXR Polyfills](https://github.com/immersive-web/webxr-polyfill) を web サイトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="6595a-107">For browsers that do not support full WebXR features, you can add [WebXR Polyfills](https://github.com/immersive-web/webxr-polyfill) to your website.</span></span>

## <a name="what-is-webxr-polyfill"></a><span data-ttu-id="6595a-108">WebXR ポリフィルとは</span><span class="sxs-lookup"><span data-stu-id="6595a-108">What is WebXR Polyfill</span></span>

<span data-ttu-id="6595a-109">WebXR Device API の JavaScript 実装と WebXR ゲームパッドモジュール。</span><span class="sxs-lookup"><span data-stu-id="6595a-109">A JavaScript implementation of the WebXR Device API, as well as the WebXR Gamepad Module.</span></span> <span data-ttu-id="6595a-110">このポリフィルを使用すると、開発者は最新の仕様に対する書き込みを行うことができ、WebVR 1.1 仕様を実装するブラウザーで実行する場合はサポートが提供され、WebVR/WebXR をまったくサポートしないモバイルデバイスではサポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="6595a-110">This polyfill allows developers to write against the latest specification, providing support when run on browsers that implement the WebVR 1.1 spec, or on mobile devices with no WebVR/WebXR support at all.</span></span>

## <a name="javascript-libraries-to-build-mixed-reality-applications-on-the-web"></a><span data-ttu-id="6595a-111">Web 上に Mixed Reality アプリケーションを構築するための JavaScript ライブラリ</span><span class="sxs-lookup"><span data-stu-id="6595a-111">JavaScript libraries to build Mixed Reality applications on the web</span></span>

## <a name="babylonjs"></a><span data-ttu-id="6595a-112">Babylon.js</span><span class="sxs-lookup"><span data-stu-id="6595a-112">Babylon.js</span></span>

<span data-ttu-id="6595a-113">Babylon は、3D コンテンツとイマーシブアプリケーションを簡単に開発できるようにする JavaScript 3D エンジンです。</span><span class="sxs-lookup"><span data-stu-id="6595a-113">Babylon is a JavaScript 3D engine that makes developing 3D content and immersive applications easy.</span></span> <span data-ttu-id="6595a-114">イマーシブアプリケーションの使用を開始する前に、Babylon.js 開発の基本について学習することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6595a-114">Before getting started with immersive applications, we recommend to learn the basics of Babylon.js development.</span></span>

<span data-ttu-id="6595a-115">[「作業の開始」セクション](https://doc.babylonjs.com/)で、Babylon を使用して mixed reality アプリケーションを構築する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6595a-115">Learn how to build a mixed reality application with Babylon in the [getting started section](https://doc.babylonjs.com/).</span></span> <span data-ttu-id="6595a-116">[Babylon プレイグラウンド](https://doc.babylonjs.com/examples/)を使用して、3d の例とそのソースコードを再生します。</span><span class="sxs-lookup"><span data-stu-id="6595a-116">Play with 3D examples and their source code using [Babylon Playground](https://doc.babylonjs.com/examples/).</span></span> <span data-ttu-id="6595a-117">詳細については、ドキュメントの [「WebXR」セクションを参照](https://doc.babylonjs.com/how_to/introduction_to_webxr) してください。</span><span class="sxs-lookup"><span data-stu-id="6595a-117">Dive into mixed reality development on the [WebXR section](https://doc.babylonjs.com/how_to/introduction_to_webxr) of the documentation.</span></span> 

## <a name="a-frame"></a><span data-ttu-id="6595a-118">A-フレーム</span><span class="sxs-lookup"><span data-stu-id="6595a-118">A-Frame</span></span>

<span data-ttu-id="6595a-119">-Frame は、web で仮想現実を開始するための宣言型の JavaScript フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="6595a-119">A-frame is a declarative JavaScript framework to get started with Virtual Reality in the web.</span></span> <span data-ttu-id="6595a-120">詳細について [は、A フレームのドキュメント](https://aframe.io/) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6595a-120">Check out the [A-Frame documentation](https://aframe.io/) to learn more.</span></span>

## <a name="threejs"></a><span data-ttu-id="6595a-121">Three.js</span><span class="sxs-lookup"><span data-stu-id="6595a-121">Three.js</span></span>

<span data-ttu-id="6595a-122">Three.js は、イマーシブエクスペリエンスを作成するための一般的な3D ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="6595a-122">Three.js is a popular 3D library for creating immersive experiences.</span></span> <span data-ttu-id="6595a-123">[three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene)の詳細については、ドキュメントページと[例](https://threejs.org/examples/#webgl_animation_cloth)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6595a-123">Learn more about [three.js](https://threejs.org/docs/index.html#manual/en/introduction/Creating-a-scene) in documentation page and by exploring [examples](https://threejs.org/examples/#webgl_animation_cloth).</span></span>

## <a name="webgl"></a><span data-ttu-id="6595a-124">WebGL</span><span class="sxs-lookup"><span data-stu-id="6595a-124">WebGL</span></span>

<span data-ttu-id="6595a-125">WebGL Api を使用して、WebXR デバイス Api に直接アクセスできます。</span><span class="sxs-lookup"><span data-stu-id="6595a-125">You can access the WebXR Device APIs directly by using WebGL APIs.</span></span> <span data-ttu-id="6595a-126">WebGL (Web グラフィックスライブラリ) は、プラグインを使用せずに、互換性のある web ブラウザー内に高パフォーマンスの対話型3D グラフィックスおよび2D グラフィックスをレンダリングするための JavaScript API です。 [Webgl api](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)の詳細については、こちらを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6595a-126">WebGL (Web Graphics Library) is a JavaScript API for rendering high-performance interactive 3D and 2D graphics within any compatible web browser without the use of plug-ins. Learn more about the [WebGL APIs](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API).</span></span>

## <a name="mixed-reality-native-mobile-applications-using-javascript"></a><span data-ttu-id="6595a-127">JavaScript を使用した Mixed Reality ネイティブモバイルアプリケーション</span><span class="sxs-lookup"><span data-stu-id="6595a-127">Mixed Reality native mobile applications using JavaScript</span></span>

<span data-ttu-id="6595a-128">JavaScript ライブラリが少ないので、mixed reality エクスペリエンスを一度記述し、web および Windows Mixed Reality ヘッドセット、Android、iOS デバイスなどのネイティブプラットフォームにデプロイすることができます。</span><span class="sxs-lookup"><span data-stu-id="6595a-128">With the help of few JavaScript libraries you can write your mixed reality experiences once and deploy it to web and to native platforms like Windows Mixed Reality headsets, Android and iOS devices.</span></span>

## <a name="babylon-native"></a><span data-ttu-id="6595a-129">Babylon ネイティブ</span><span class="sxs-lookup"><span data-stu-id="6595a-129">Babylon Native</span></span>

<span data-ttu-id="6595a-130">[Babylon ネイティブ](https://www.babylonjs.com/native/) プラットフォームを使用すると、だれでも Babylon.js コードを取得し、それを使用してネイティブアプリケーションを構築し、ネイティブテクノロジの機能のロックを解除することができます。</span><span class="sxs-lookup"><span data-stu-id="6595a-130">[Babylon Native](https://www.babylonjs.com/native/) platform allows anyone to take their Babylon.js code and build a native application with it, unlocking the power of native technologies.</span></span> <span data-ttu-id="6595a-131">[Github で Babylon ネイティブ](https://github.com/BabylonJS/BabylonNative)をダウンロードし、 [Babylon.js のブログ](https://medium.com/@babylonjs/babylon-native-821f1694fffc)で詳細を確認できます。</span><span class="sxs-lookup"><span data-stu-id="6595a-131">You can download [Babylon native on github](https://github.com/BabylonJS/BabylonNative) and read more about it on [Babylon.js blog](https://medium.com/@babylonjs/babylon-native-821f1694fffc).</span></span>

## <a name="react-native"></a><span data-ttu-id="6595a-132">React Native</span><span class="sxs-lookup"><span data-stu-id="6595a-132">React Native</span></span>

<span data-ttu-id="6595a-133">[ネイティブ](https://reactnative.dev/) への対応は、開発者が JavaScript を使用してビルドし、複数のプラットフォームに配置できる、もう1つのオープンソースライブラリです。</span><span class="sxs-lookup"><span data-stu-id="6595a-133">[React Native](https://reactnative.dev/) is another open source library that allows developers to build using JavaScript and deploy to multiple platforms.</span></span> <span data-ttu-id="6595a-134">[Github でのネイティブな応答](https://github.com/facebook/react-native)をダウンロードし、その詳細については、[ネイティブブログの応答](https://reactnative.dev/blog/)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6595a-134">You can download [React Native on Github](https://github.com/facebook/react-native) and learn more about it in [React Native Blog](https://reactnative.dev/blog/).</span></span>

## <a name="see-also"></a><span data-ttu-id="6595a-135">参照</span><span class="sxs-lookup"><span data-stu-id="6595a-135">See Also</span></span>

* [<span data-ttu-id="6595a-136">WebXR の概要</span><span class="sxs-lookup"><span data-stu-id="6595a-136">WebXR Overview</span></span>](webxr-overview.md)
* [<span data-ttu-id="6595a-137">WebXR Device API 仕様</span><span class="sxs-lookup"><span data-stu-id="6595a-137">WebXR Device API specification</span></span>](https://immersive-web.github.io/webxr/)
* [<span data-ttu-id="6595a-138">WebXR Device API のドキュメント</span><span class="sxs-lookup"><span data-stu-id="6595a-138">WebXR Device API documentation</span></span>](https://developer.mozilla.org/en-US/docs/Web/API/WebXR_Device_API)
* [<span data-ttu-id="6595a-139">Immersiveweb</span><span class="sxs-lookup"><span data-stu-id="6595a-139">Immersiveweb.dev</span></span>](https://immersiveweb.dev/)
* [<span data-ttu-id="6595a-140">WebXR のサンプル</span><span class="sxs-lookup"><span data-stu-id="6595a-140">WebXR Samples</span></span>](https://immersive-web.github.io/webxr-samples/)
* [<span data-ttu-id="6595a-141">Babylon.js を使用した WebXR エクスペリエンスの作成</span><span class="sxs-lookup"><span data-stu-id="6595a-141">Using Babylon.js to create WebXR experiences</span></span>](https://doc.babylonjs.com/how_to/introduction_to_webxr)
* [<span data-ttu-id="6595a-142">Windows Mixed Reality と新しい Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="6595a-142">Windows Mixed Reality and the new Microsoft Edge</span></span>](/windows/mixed-reality/new-microsoft-edge#introducing-the-new-microsoft-edge)
* [<span data-ttu-id="6595a-143">イマーシブ Web W3C Github</span><span class="sxs-lookup"><span data-stu-id="6595a-143">Immersive Web W3C Github</span></span>](https://github.com/immersive-web)
* <span data-ttu-id="6595a-144">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="6595a-144">[WebGL API](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182648(v=vs.85))</span></span>
* <span data-ttu-id="6595a-145">[ゲームパッド API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) と [ゲームパッド拡張機能](https://w3c.github.io/gamepad/extensions.html)</span><span class="sxs-lookup"><span data-stu-id="6595a-145">[Gamepad API](https://msdn.microsoft.com/library/dn743630(v=vs.85).aspx) and [Gamepad Extensions](https://w3c.github.io/gamepad/extensions.html)</span></span>
* [<span data-ttu-id="6595a-146">WebVR の概要</span><span class="sxs-lookup"><span data-stu-id="6595a-146">WebVR Overview</span></span>](webvr-overview.md)