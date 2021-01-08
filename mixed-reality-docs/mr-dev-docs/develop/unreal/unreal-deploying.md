---
title: Unreal でのデバイスへのデプロイ
description: エディターまたはデバイスポータルを使用して、mixed reality のアプリを HoloLens 2 にデプロイするために必要なすべての事項について説明します。
author: sw5813
ms.author: suwu
ms.date: 12/9/2020
ms.topic: article
keywords: Unreal、Unreal Engine 4、UE4、HoloLens、HoloLens 2、mixed reality、デバイスへの展開、PC、ドキュメント、mixed reality ヘッドセット、windows mixed reality ヘッドセット、virtual reality ヘッドセット
appliesto:
- HoloLens 2
ms.openlocfilehash: 24b2c013e1c9f25f54be9a6fefec8a86846c1746
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009752"
---
# <a name="deploy-to-device-in-unreal"></a><span data-ttu-id="68400-104">Unreal でのデバイスへのデプロイ</span><span class="sxs-lookup"><span data-stu-id="68400-104">Deploy to device in Unreal</span></span>

<span data-ttu-id="68400-105">HoloLens 2 に Unreal アプリケーションを展開するには、次の2つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="68400-105">There are two ways to deploy an Unreal application to HoloLens 2:</span></span>
* <span data-ttu-id="68400-106">Unreal エディターから直接</span><span class="sxs-lookup"><span data-stu-id="68400-106">Directly from the Unreal editor</span></span>
* <span data-ttu-id="68400-107">デバイスポータルを使用してアップロードされたパッケージとして</span><span class="sxs-lookup"><span data-stu-id="68400-107">As a package uploaded via the device portal</span></span>

<span data-ttu-id="68400-108">どちらのオプションでも、開発用の [デバイスポータル](../platform-capabilities-and-apis/using-the-windows-device-portal.md) を使用するように HoloLens を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="68400-108">Both options require you to set up your HoloLens to use the [device portal](../platform-capabilities-and-apis/using-the-windows-device-portal.md) for development.</span></span>

## <a name="deploying-to-device-from-the-unreal-editor"></a><span data-ttu-id="68400-109">Unreal エディターからデバイスへの配置</span><span class="sxs-lookup"><span data-stu-id="68400-109">Deploying to device from the Unreal editor</span></span>

1. <span data-ttu-id="68400-110">[ **起動** ] ボタンの横にあるドロップダウン矢印を選択します。</span><span class="sxs-lookup"><span data-stu-id="68400-110">Select the dropdown arrow next to the **Launch** button.</span></span> <span data-ttu-id="68400-111">最初は、HoloLens デバイスオプションが淡色表示になります。</span><span class="sxs-lookup"><span data-stu-id="68400-111">Initially, the HoloLens device option will be grayed out.</span></span>

![起動ドロップダウンオプション](images/unreal/launch-dropdown.png)

2. <span data-ttu-id="68400-113">**デバイスマネージャー** を開くと、HoloLens がデバイスの一覧に自動的に表示されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="68400-113">Open the **Device Manager** and note that your HoloLens won't automatically appear in the device list.</span></span>

3. <span data-ttu-id="68400-114">[ **一覧にないデバイスの追加** ] セクションを展開します。</span><span class="sxs-lookup"><span data-stu-id="68400-114">Expand the **Add An Unlisted Device** section.</span></span>

4. <span data-ttu-id="68400-115">**プラットフォーム** として **HoloLens** を選択します。</span><span class="sxs-lookup"><span data-stu-id="68400-115">Select **HoloLens** as your **Platform**.</span></span>

5. <span data-ttu-id="68400-116">デバイスの IP アドレスとポート情報を、デバイス id としてコロンで区切って入力します。</span><span class="sxs-lookup"><span data-stu-id="68400-116">Enter your devices' IP address and port information separated by a colon as the device identifier.</span></span> <span data-ttu-id="68400-117">たとえば、"127.0.0.1: 10080" (USB 経由で接続されている場合) などです。</span><span class="sxs-lookup"><span data-stu-id="68400-117">For example, "127.0.0.1:10080" (when connected via USB).</span></span> <span data-ttu-id="68400-118">デバイスポータルのユーザー名とパスワードの資格情報を使用します。</span><span class="sxs-lookup"><span data-stu-id="68400-118">Use your Device Portal username and password credentials.</span></span>

6. <span data-ttu-id="68400-119">[ **追加** ] をクリックし、デバイスマネージャーを閉じます。</span><span class="sxs-lookup"><span data-stu-id="68400-119">Hit **Add** and close the device manager.</span></span>
    * <span data-ttu-id="68400-120">間違ったアドレスやユーザー資格情報などのエラーが発生すると、メッセージが出力ログに出力されます。</span><span class="sxs-lookup"><span data-stu-id="68400-120">If there's an error, such as wrong address or user credentials, a message will print to the Output Log.</span></span>

![一覧にないデバイスの追加](images/unreal/add-unlisted-device.png)

7. <span data-ttu-id="68400-122">[ **起動** ] ボタンの横にあるドロップダウン矢印をクリックすると、追加した HoloLens デバイスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="68400-122">Select the dropdown arrow next to the **Launch** button again - this time you should see the HoloLens device you just added.</span></span> <span data-ttu-id="68400-123">Hololens にビルドしてデプロイする HoloLens デバイスを選択します。</span><span class="sxs-lookup"><span data-stu-id="68400-123">Select the HoloLens device to build and deploy to your HoloLens.</span></span>

>[!NOTE]
><span data-ttu-id="68400-124">デバイスのビルドには、シェーダーの再コンパイルが含まれる場合があります (特に最初の実行時)。これには時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="68400-124">Building for the device may involve recompiling shaders (especially on the first run)- this can take a while.</span></span> <span data-ttu-id="68400-125">デバイスは、アプリが実行されるまでスリープ状態にならないようにしてください (磨耗が必要な場合があります)。</span><span class="sxs-lookup"><span data-stu-id="68400-125">Don't let the device go to sleep until the app is running (you may have to wear it).</span></span> <span data-ttu-id="68400-126">それ以外の場合、シェーダーのコンパイルは失敗します。</span><span class="sxs-lookup"><span data-stu-id="68400-126">Otherwise shader compilation will fail!</span></span>

## <a name="deploying-to-device-via-device-portal"></a><span data-ttu-id="68400-127">デバイスポータルを使用したデバイスへの展開</span><span class="sxs-lookup"><span data-stu-id="68400-127">Deploying to device via device portal</span></span>

<span data-ttu-id="68400-128">アプリのパッケージ化とデプロイに関する詳細な手順については、 [Unreal チュートリアルシリーズ](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68400-128">You can find detailed instructions on packaging and deploying an app in the [Unreal tutorial series](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal).</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="68400-129">次の開発チェックポイント</span><span class="sxs-lookup"><span data-stu-id="68400-129">Next Development Checkpoint</span></span>

<span data-ttu-id="68400-130">デプロイの準備が完了していない場合は、デプロイ段階の途中で作業しています。</span><span class="sxs-lookup"><span data-stu-id="68400-130">If you're following the Unreal development journey we've laid out, you're in the midst of the deployment stage.</span></span> <span data-ttu-id="68400-131">ここから、高度なサービスの追加を続けることができます。</span><span class="sxs-lookup"><span data-stu-id="68400-131">From here, you can continue to adding advanced services:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="68400-132">高度なサービス</span><span class="sxs-lookup"><span data-stu-id="68400-132">Advanced services</span></span>](unreal-development-overview.md#5-adding-services)

<span data-ttu-id="68400-133">いつでも [Unreal 開発チェックポイント](unreal-development-overview.md#4-streaming-and-deploying-to-a-device)に戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="68400-133">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#4-streaming-and-deploying-to-a-device) at any time.</span></span>
