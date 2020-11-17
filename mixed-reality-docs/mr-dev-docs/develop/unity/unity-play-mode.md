---
title: Unity の再生モード
description: Unity エディターの再生モードを使用して、アプリをデプロイせずにデバイスでの変更をプレビューします。
author: jonmlyons
ms.author: jlyons
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, リモート処理, holographic リモート処理, holographic リモート処理プレーヤー, HoloLens, mixed reality ヘッドセット, windows mixed reality ヘッドセット, 仮想現実ヘッドセット, unity 再生モード
ms.openlocfilehash: 88ffa172c03dea6544ce8475612426e126415908
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679061"
---
# <a name="unity-play-mode"></a><span data-ttu-id="f64cf-104">Unity の再生モード</span><span class="sxs-lookup"><span data-stu-id="f64cf-104">Unity Play Mode</span></span>

<span data-ttu-id="f64cf-105">Unity プロジェクトですばやく作業を行うには、"Play Mode" を使用します。</span><span class="sxs-lookup"><span data-stu-id="f64cf-105">A fast way to work on your Unity project is to use "Play Mode".</span></span> <span data-ttu-id="f64cf-106">これにより、PC の Unity エディターでアプリがローカルで実行されます。</span><span class="sxs-lookup"><span data-stu-id="f64cf-106">This runs your app locally in the Unity editor on your PC.</span></span> <span data-ttu-id="f64cf-107">Unity では、Holographic Remoting を使用して、実際の HoloLens デバイスでコンテンツをすばやくプレビューすることができます。</span><span class="sxs-lookup"><span data-stu-id="f64cf-107">Unity uses Holographic Remoting to provide a fast way to preview your content on a real HoloLens device.</span></span> <span data-ttu-id="f64cf-108">再生モードは、開発用 PC に接続されている Windows Mixed Reality ヘッドセットでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="f64cf-108">Play Mode can also be used with a Windows Mixed Reality headset attached to your development PC.</span></span>

## <a name="unity-play-mode-with-holographic-remoting"></a><span data-ttu-id="f64cf-109">Holographic リモート処理を使用した Unity Play モード</span><span class="sxs-lookup"><span data-stu-id="f64cf-109">Unity Play Mode with Holographic Remoting</span></span>

<span data-ttu-id="f64cf-110">Holographic リモート処理を使用すると、PC の Unity エディターでアプリを実行しながら、HoloLens でアプリを体験できます。</span><span class="sxs-lookup"><span data-stu-id="f64cf-110">With Holographic Remoting, you can experience your app on the HoloLens, while it runs in the Unity editor on your PC.</span></span> <span data-ttu-id="f64cf-111">宝石、ジェスチャ、音声、および空間マッピングの入力は、HoloLens から PC に送信されます。</span><span class="sxs-lookup"><span data-stu-id="f64cf-111">Gaze, gesture, voice, and spatial mapping input is sent from your HoloLens to your PC.</span></span> <span data-ttu-id="f64cf-112">レンダリングされたフレームが HoloLens に返されます。</span><span class="sxs-lookup"><span data-stu-id="f64cf-112">Rendered frames are then sent back to your HoloLens.</span></span> <span data-ttu-id="f64cf-113">これは、完全なプロジェクトをビルドして配置することなく、アプリをすばやくデバッグできる優れた方法です。</span><span class="sxs-lookup"><span data-stu-id="f64cf-113">This is a great way to quickly debug your app without building and deploying a full project.</span></span>
1. <span data-ttu-id="f64cf-114">HoloLens で、 **Microsoft Store** にアクセスし、 **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** アプリをインストールします。</span><span class="sxs-lookup"><span data-stu-id="f64cf-114">On your HoloLens, go to the **Microsoft Store** and install the **[Holographic Remoting Player](https://www.microsoft.com/store/p/holographic-remoting-player/9nblggh4sv40)** app.</span></span>
2. <span data-ttu-id="f64cf-115">HoloLens で、 **Holographic Remoting Player** アプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="f64cf-115">On your HoloLens, start the **Holographic Remoting Player** app.</span></span>
3. <span data-ttu-id="f64cf-116">Unity で、[ **ウィンドウ** ] メニューの [ **XR** ] サブメニューを展開し、[ **Holographic エミュレーション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f64cf-116">In Unity, go to the **Window** menu, expand the **XR** sub-menu, and select **Holographic Emulation**.</span></span>
4. <span data-ttu-id="f64cf-117">**エミュレーションモード** を **リモートからデバイスに** 設定します。</span><span class="sxs-lookup"><span data-stu-id="f64cf-117">Set **Emulation Mode** to **Remote to Device**.</span></span>
5. <span data-ttu-id="f64cf-118">[ **リモートコンピューター**] には、HOLOLENS の IP アドレスを入力します。</span><span class="sxs-lookup"><span data-stu-id="f64cf-118">For **Remote Machine**, enter the IP address of your HoloLens.</span></span>
6. <span data-ttu-id="f64cf-119">**[Connect]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f64cf-119">Click **Connect**.</span></span> <span data-ttu-id="f64cf-120">**接続の状態** が [接続済み] に変わり、HoloLens で画面が空白になって **いる** ことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f64cf-120">You should see **Connection Status** change to **Connected** and see the screen go blank in the HoloLens.</span></span>
7. <span data-ttu-id="f64cf-121">[ **再生** ] ボタンをクリックして再生モードを開始し、HoloLens でアプリを体験します。</span><span class="sxs-lookup"><span data-stu-id="f64cf-121">Click the **Play** button to start Play Mode and experience the app on your HoloLens.</span></span>

<span data-ttu-id="f64cf-122">Holographic リモート処理には、高速 PC と Wi-Fi 接続が必要です。</span><span class="sxs-lookup"><span data-stu-id="f64cf-122">Holographic Remoting requires a fast PC and Wi-Fi connection.</span></span> <span data-ttu-id="f64cf-123">詳細については、「 [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f64cf-123">See [Holographic Remoting Player](../platform-capabilities-and-apis/holographic-remoting-player.md) for full details.</span></span>

<span data-ttu-id="f64cf-124">最適な結果を得るには、アプリが [フォーカスポイント](focus-point-in-unity.md)を正しく設定していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f64cf-124">For best results, make sure your app properly sets the [focus point](focus-point-in-unity.md).</span></span> <span data-ttu-id="f64cf-125">これにより、Holographic リモート処理によって、ワイヤレス接続の待機時間にシーンを最適に適応させることができます。</span><span class="sxs-lookup"><span data-stu-id="f64cf-125">This helps Holographic Remoting to best adapt your scene to the latency of your wireless connection.</span></span>

## <a name="see-also"></a><span data-ttu-id="f64cf-126">参照</span><span class="sxs-lookup"><span data-stu-id="f64cf-126">See Also</span></span>
* [<span data-ttu-id="f64cf-127">Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="f64cf-127">Holographic Remoting Player</span></span>](../platform-capabilities-and-apis/holographic-remoting-player.md)
