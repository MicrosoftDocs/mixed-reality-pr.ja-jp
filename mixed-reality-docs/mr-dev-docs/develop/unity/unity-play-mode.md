---
title: Unity の再生モード
description: Unity エディターで Play モードを使用して、アプリをデプロイせずにデバイスでのアプリケーションの変更をプレビューする方法について説明します。
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, リモート処理, holographic リモート処理, holographic リモート処理プレーヤー, HoloLens, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット, unity 再生モード
ms.openlocfilehash: 9f6c2cafd08fca8a5d60f3fcf5832ee74762e173
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009842"
---
# <a name="unity-play-mode"></a><span data-ttu-id="0317c-104">Unity の再生モード</span><span class="sxs-lookup"><span data-stu-id="0317c-104">Unity Play Mode</span></span>

<span data-ttu-id="0317c-105">Unity プロジェクトですばやく作業を行うには、"Play Mode" を使用します。これにより、PC の Unity エディターでアプリがローカルで実行されます。</span><span class="sxs-lookup"><span data-stu-id="0317c-105">A fast way to work on your Unity project is to use "Play Mode", which runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="0317c-106">Unity では、Holographic Remoting を使用して、実際の HoloLens デバイスでコンテンツをすばやくプレビューすることができます。</span><span class="sxs-lookup"><span data-stu-id="0317c-106">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="0317c-107">再生モードは、開発用 PC に接続されている Windows Mixed Reality ヘッドセットでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="0317c-107">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="0317c-108">Holographic リモート処理を使用した Unity Play モード</span><span class="sxs-lookup"><span data-stu-id="0317c-108">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="0317c-109">Holographic リモート処理を使用すると、PC の Unity エディターでアプリを実行しながら、HoloLens でアプリを体験できます。</span><span class="sxs-lookup"><span data-stu-id="0317c-109">With Holographic Remoting, you can experience your app on the HoloLens while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="0317c-110">宝石、ジェスチャ、音声、および空間マッピングの入力は、HoloLens から PC に送信されます。</span><span class="sxs-lookup"><span data-stu-id="0317c-110">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="0317c-111">レンダリングされたフレームが HoloLens に返されます。</span><span class="sxs-lookup"><span data-stu-id="0317c-111">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="0317c-112">これは、完全なプロジェクトをビルドして配置することなく、アプリをすばやくデバッグできる優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="0317c-112">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="0317c-113">HoloLens で、 **Microsoft Store** にアクセスし、 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** アプリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="0317c-113">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="0317c-114">HoloLens で、 **Holographic Remoting Player** アプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="0317c-114">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="0317c-115">Unity で、[ **ウィンドウ** ] メニューの [ **XR** ] サブメニューを展開し、[ **Holographic エミュレーション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0317c-115">In Unity, go to the **Window** menu, expand the **XR** submenu, and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="0317c-116">**エミュレーションモード** を **リモートからデバイスに** 設定します。</span><span class="sxs-lookup"><span data-stu-id="0317c-116">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="0317c-117">[ **リモートコンピューター**] には、HOLOLENS の IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="0317c-117">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="0317c-118">**[接続]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0317c-118">Select **Connect**.</span></span> <span data-ttu-id="0317c-119">**接続の状態** が [接続済み] に変わり、HoloLens で画面が空白になって **いる** ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0317c-119">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="0317c-120">[ **再生** ] ボタンを選択して再生モードを開始し、HoloLens でアプリを体験します。</span><span class="sxs-lookup"><span data-stu-id="0317c-120">Select the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="0317c-121">Holographic リモート処理には、高速 PC と Wi-Fi 接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="0317c-121">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="0317c-122">詳細については、 [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="0317c-122">You can find more details in the [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) documentation.</span></span>

<span data-ttu-id="0317c-123">最適な結果を得るには、アプリが [フォーカスポイント](focus-point-in-unity.md)を正しく設定していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0317c-123">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="0317c-124">これにより、Holographic リモート処理によって、ワイヤレス接続の待機時間にシーンを最適に適応させることができます。</span><span class="sxs-lookup"><span data-stu-id="0317c-124">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="0317c-125">参照</span><span class="sxs-lookup"><span data-stu-id="0317c-125">See Also</span></span>
* [<span data-ttu-id="0317c-126">Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="0317c-126">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
