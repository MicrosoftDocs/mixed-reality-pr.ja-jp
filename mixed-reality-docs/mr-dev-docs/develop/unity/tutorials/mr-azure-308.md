---
title: MR と Azure 308 - クロスデバイス通知
description: このコースでは、Azure Notification Hubs、Azure Functions、および Azure Storage テーブルを mixed reality アプリケーション内に実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, 通知, 関数, テーブル, 通知ハブ, hololens, イマーシブ, vr, Windows 10, Visual Studio
ms.openlocfilehash: 5bf6720fe7be178bf4fb15ae2b87f4ff502afe9b
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581269"
---
# <a name="mr-and-azure-308-cross-device-notifications"></a><span data-ttu-id="0a79c-104">MR と Azure 308:クロスデバイス通知</span><span class="sxs-lookup"><span data-stu-id="0a79c-104">MR and Azure 308: Cross-device notifications</span></span>

<br>

>[!NOTE]
><span data-ttu-id="0a79c-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="0a79c-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="0a79c-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。</span><span class="sxs-lookup"><span data-stu-id="0a79c-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="0a79c-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="0a79c-109">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="0a79c-110">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

![最終製品-開始](images/AzureLabs-Lab8-00.png)

<span data-ttu-id="0a79c-112">このコースでは、Azure Notification Hubs、Azure テーブル、および Azure Functions を使用して、Notification Hubs 機能を mixed reality アプリケーションに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-112">In this course, you will learn how to add Notification Hubs capabilities to a mixed reality application using Azure Notification Hubs, Azure Tables, and Azure Functions.</span></span>

<span data-ttu-id="0a79c-113">**Azure Notification Hubs** は Microsoft のサービスであり、開発者は、クラウド内のすべてのプラットフォームにおいて、対象となるパーソナライズされたプッシュ通知を任意のプラットフォームに送信できます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-113">**Azure Notification Hubs** is a Microsoft service, which allows developers to send targeted and personalized push notifications to any platform, all powered within the cloud.</span></span> <span data-ttu-id="0a79c-114">これにより、開発者はシナリオに応じて、エンドユーザーと通信したり、さまざまなアプリケーション間で通信したりできるようになります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-114">This can effectively allow developers to communicate with end users, or even communicate between various applications, depending on the scenario.</span></span> <span data-ttu-id="0a79c-115">詳細については、 **Azure Notification Hubs** の [ページ](/azure/notification-hubs/notification-hubs-push-notification-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-115">For more information, visit the **Azure Notification Hubs** [page](/azure/notification-hubs/notification-hubs-push-notification-overview).</span></span>

<span data-ttu-id="0a79c-116">**Azure Functions** は Microsoft のサービスであり、開発者は Azure で小さなコードである "Functions" を実行できます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-116">**Azure Functions** is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="0a79c-117">これにより、ローカルアプリケーションではなく、クラウドに作業を委任することができます。これには多くのメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-117">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="0a79c-118">**Azure Functions** は、C \# 、F \# 、Node.js、Java、PHP など、いくつかの開発言語をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-118">**Azure Functions** supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="0a79c-119">詳細については、 **Azure Functions** の [ページ](/azure/azure-functions/functions-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-119">For more information, visit the **Azure Functions** [page](/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="0a79c-120">**Azure テーブル** は Microsoft のクラウドサービスであり、開発者は構造化されていない SQL データをクラウドに保存できるため、どこからでも簡単にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-120">**Azure Tables** is a Microsoft cloud service, which allows developers to store structured non-SQL data in the cloud, making it easily accessible anywhere.</span></span> <span data-ttu-id="0a79c-121">このサービスでは、必要に応じてテーブルを進化させることができるため、スキーマなしの設計が非常に優れているため、非常に柔軟性があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-121">The service boasts a schemaless design, allowing for the evolution of tables as needed, and thus is very flexible.</span></span> <span data-ttu-id="0a79c-122">詳細については、 **Azure のテーブル** に関する [ページ](/azure/cosmos-db/table-storage-overview)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-122">For more information, visit the **Azure Tables** [page](/azure/cosmos-db/table-storage-overview)</span></span>

<span data-ttu-id="0a79c-123">このコースを完了すると、現実のイマーシブヘッドセットアプリケーションと、次のようなデスクトップ PC アプリケーションを使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-123">Having completed this course, you will have a mixed reality immersive headset application, and a Desktop PC application, which will be able to do the following:</span></span>

1. <span data-ttu-id="0a79c-124">デスクトップ PC アプリを使用すると、ユーザーはマウスを使用して、2D 空間 (X および Y) 内のオブジェクトを移動できます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-124">The Desktop PC app will allow the user to move an object in 2D space (X and Y), using the mouse.</span></span>

2. <span data-ttu-id="0a79c-125">PC アプリ内のオブジェクトの移動は、JSON を使用してクラウドに送信されます。 JSON は、オブジェクト ID、型、および変換情報 (X および Y 座標) を含む文字列の形式になります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-125">The movement of objects within the PC app will be sent to the cloud using JSON, which will be in the form of a string, containing an object ID, type, and transform information (X and Y coordinates).</span></span> 

3. <span data-ttu-id="0a79c-126">デスクトップアプリと同一のシーンを持つ mixed reality アプリは、Notification Hubs サービス (デスクトップ PC アプリによって更新されたばかり) から、オブジェクトの移動に関する通知を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-126">The mixed reality app, which has an identical scene to the desktop app, will receive notifications regarding object movement, from the Notification Hubs service (which has just been updated by the Desktop PC app).</span></span> 

4. <span data-ttu-id="0a79c-127">オブジェクト ID、種類、および変換情報が含まれる通知を受け取ると、mixed reality アプリによって、受信した情報が独自のシーンに適用されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-127">Upon receiving a notification, which will contain the object ID, type, and transform information, the mixed reality app will apply the received information to its own scene.</span></span>

<span data-ttu-id="0a79c-128">アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-128">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="0a79c-129">このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-129">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="0a79c-130">このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-130">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span> <span data-ttu-id="0a79c-131">このコースは自己完結型のチュートリアルであり、他の Mixed Reality ラボに直接は関与しません。</span><span class="sxs-lookup"><span data-stu-id="0a79c-131">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="0a79c-132">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="0a79c-132">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="0a79c-133">コース</span><span class="sxs-lookup"><span data-stu-id="0a79c-133">Course</span></span></th><th style="width:150px"> <span data-ttu-id="0a79c-134"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="0a79c-134"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="0a79c-135"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="0a79c-135"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="0a79c-136">MR と Azure 308:クロスデバイス通知</span><span class="sxs-lookup"><span data-stu-id="0a79c-136">MR and Azure 308: Cross-device notifications</span></span></td><td style="text-align: center;"> <span data-ttu-id="0a79c-137">✔️</span><span class="sxs-lookup"><span data-stu-id="0a79c-137">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="0a79c-138">✔️</span><span class="sxs-lookup"><span data-stu-id="0a79c-138">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="0a79c-139">このコースでは主に Windows Mixed Reality イマーシブ (VR) ヘッドセットに焦点を当てていますが、このコースで学習した内容を Microsoft HoloLens に適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-139">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="0a79c-140">このコースに従うと、HoloLens をサポートするために必要となる可能性のある変更に関する注意事項が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-140">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="0a79c-141">HoloLens を使用する場合、音声キャプチャ中にエコーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-141">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0a79c-142">前提条件</span><span class="sxs-lookup"><span data-stu-id="0a79c-142">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="0a79c-143">このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-143">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="0a79c-144">また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証されたものを表します (2018 年5月)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-144">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="0a79c-145">「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものよりも新しいソフトウェアで見つかったものと完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="0a79c-145">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="0a79c-146">このコースでは、次のハードウェアとソフトウェアをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-146">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="0a79c-147">開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-147">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="0a79c-148">開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="0a79c-148">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0a79c-149">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="0a79c-149">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0a79c-150">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="0a79c-150">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="0a79c-151">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0a79c-151">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="0a79c-152">[Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](/hololens/hololens1-hardware)</span><span class="sxs-lookup"><span data-stu-id="0a79c-152">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="0a79c-153">Azure セットアップのインターネットアクセスと Notification Hubs へのアクセス</span><span class="sxs-lookup"><span data-stu-id="0a79c-153">Internet access for Azure setup and to access Notification Hubs</span></span>

## <a name="before-you-start"></a><span data-ttu-id="0a79c-154">開始する前に</span><span class="sxs-lookup"><span data-stu-id="0a79c-154">Before you start</span></span>

- <span data-ttu-id="0a79c-155">このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-155">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="0a79c-156">Microsoft 開発者ポータルとアプリケーション登録ポータルの所有者である必要があります。そうしないと、 [第2章](#chapter-2---retrieve-your-new-apps-credentials)でアプリにアクセスするためのアクセス許可が付与されません。</span><span class="sxs-lookup"><span data-stu-id="0a79c-156">You must be the owner of your Microsoft Developer Portal and your Application Registration Portal, otherwise you will not have permission to access the app in [Chapter 2](#chapter-2---retrieve-your-new-apps-credentials).</span></span>

## <a name="chapter-1---create-an-application-on-the-microsoft-developer-portal"></a><span data-ttu-id="0a79c-157">章 1-Microsoft 開発者ポータルでアプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="0a79c-157">Chapter 1 - Create an application on the Microsoft Developer Portal</span></span>

<span data-ttu-id="0a79c-158">**Azure Notification Hubs** サービスを使用するには、アプリケーションを登録する必要があるため、Microsoft 開発者ポータルでアプリケーションを作成する必要があります。これにより、アプリケーションは通知を送受信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-158">To use the **Azure Notification Hubs** Service, you will need to create an Application on the Microsoft Developer Portal, as your application will need to be registered, so that it can send and receive notifications.</span></span>

1.  <span data-ttu-id="0a79c-159">[Microsoft 開発者ポータル](https://developer.microsoft.com/dashboard)にログインします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-159">Log in to the [Microsoft Developer Portal](https://developer.microsoft.com/dashboard).</span></span>

    > <span data-ttu-id="0a79c-160">Microsoft アカウントにログインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-160">You will need to log in to your Microsoft Account.</span></span>

2.  <span data-ttu-id="0a79c-161">ダッシュボードで、[ **新しいアプリの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-161">From the Dashboard, click **Create a new app**.</span></span>

    ![アプリを作成する](images/AzureLabs-Lab8-01.png)

3.  <span data-ttu-id="0a79c-163">ポップアップが表示され、新しいアプリの名前を予約する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-163">A popup will appear, wherein you need to reserve a name for your new app.</span></span> <span data-ttu-id="0a79c-164">テキストボックスに、適切な名前を挿入します。選択した名前が使用可能な場合は、テキストボックスの右側にティックが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-164">In the textbox, insert an appropriate name; if the chosen name is available, a tick will appear to the right of the textbox.</span></span> <span data-ttu-id="0a79c-165">使用可能な名前が挿入されたら、ポップアップの下左側にある [ **製品名の予約** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-165">Once you have an available name inserted, click the **Reserve product name** button to the bottom left of the popup.</span></span>

    ![名前を反転する](images/AzureLabs-Lab8-02.png)

4.  <span data-ttu-id="0a79c-167">これでアプリが作成されたので、次の章に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-167">With the app now created, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-2---retrieve-your-new-apps-credentials"></a><span data-ttu-id="0a79c-168">Chapter 2-新しいアプリの資格情報を取得する</span><span class="sxs-lookup"><span data-stu-id="0a79c-168">Chapter 2 - Retrieve your new apps credentials</span></span>

<span data-ttu-id="0a79c-169">新しいアプリが一覧表示されるアプリケーション登録ポータルにログインし、 **Azure Portal** 内で **Notification Hubs サービス** をセットアップするために使用される資格情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-169">Log into the Application Registration Portal, where your new app will be listed, and retrieve the credentials which will be used to setup the **Notification Hubs Service** within the **Azure Portal**.</span></span>

1.  <span data-ttu-id="0a79c-170">[アプリケーション登録ポータル](https://apps.dev.microsoft.com)に移動します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-170">Navigate to the [Application Registration Portal](https://apps.dev.microsoft.com).</span></span>

    ![アプリケーション登録ポータル](images/AzureLabs-Lab8-03.png)

    > [!WARNING] 
    > <span data-ttu-id="0a79c-172">ログインするには、Microsoft アカウントを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-172">You will need to use your Microsoft Account to Login.</span></span>  
    > <span data-ttu-id="0a79c-173">これは、Windows ストア開発者ポータルを使用して、前の [章](#chapter-1---create-an-application-on-the-microsoft-developer-portal)で使用した Microsoft アカウントである **必要があり** ます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-173">This **must** be the Microsoft Account which you used in the previous [Chapter](#chapter-1---create-an-application-on-the-microsoft-developer-portal), with the Windows Store Developer portal.</span></span>

2.  <span data-ttu-id="0a79c-174">アプリは [ **マイアプリケーション** ] セクションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-174">You will find your app under the **My applications** section.</span></span> <span data-ttu-id="0a79c-175">見つかったら、それをクリックすると、アプリ名と **登録** を含む新しいページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-175">Once you have found it, click on it and you will be taken to a new page which has the app name plus **Registration**.</span></span>

    ![新しく登録されたアプリ](images/AzureLabs-Lab8-04.png)

3.  <span data-ttu-id="0a79c-177">登録ページを下にスクロールして、 **アプリケーションのシークレット** セクションとアプリの **パッケージ SID** を探します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-177">Scroll down the registration page to find your **Application Secrets** section and the **Package SID** for your app.</span></span> <span data-ttu-id="0a79c-178">次の章の **Azure Notification Hubs サービス** の設定で使用するために両方をコピーします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-178">Copy both for use with setting up the **Azure Notification Hubs Service** in the next Chapter.</span></span>

    ![アプリケーションシークレット](images/AzureLabs-Lab8-05.png)

## <a name="chapter-3---setup-azure-portal-create-notification-hubs-service"></a><span data-ttu-id="0a79c-180">章 3-Azure Portal のセットアップ: Notification Hubs サービスの作成</span><span class="sxs-lookup"><span data-stu-id="0a79c-180">Chapter 3 - Setup Azure Portal: create Notification Hubs Service</span></span>

<span data-ttu-id="0a79c-181">アプリの資格情報を取得したら、azure ポータルに移動する必要があります。ここでは、Azure Notification Hubs サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-181">With your apps credentials retrieved, you will need to go to the Azure Portal, where you will create an Azure Notification Hubs Service.</span></span>

1.  <span data-ttu-id="0a79c-182">[Azure Portal](https://portal.azure.com) にログインします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-182">Log into the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="0a79c-183">まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-183">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="0a79c-184">このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-184">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="0a79c-185">ログインしたら、左上隅にある [ **新規** ] をクリックし、[ **Notification Hub**] を検索して、[\**_Enter_* _] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-185">Once you are logged in, click on **New** in the top left corner, and search for **Notification Hub**, and click \**_Enter_* _.</span></span>

    ![notification hub の検索](images/AzureLabs-Lab8-06.png)

    > [!NOTE] 
    > <span data-ttu-id="0a79c-187">新しいポータルで、 _*_New_*_ という単語が _ \* [リソースの作成] \* \* に置き換えられています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-187">The word _*_New_*_ may have been replaced with _\*Create a resource\*\*, in newer portals.</span></span>

3.  <span data-ttu-id="0a79c-188">新しいページには、 *Notification Hubs* サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-188">The new page will provide a description of the *Notification Hubs* service.</span></span> <span data-ttu-id="0a79c-189">このプロンプトの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-189">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![notification hub インスタンスの作成](images/AzureLabs-Lab8-07.png)

4.  <span data-ttu-id="0a79c-191">[\**_作成_* _:</span><span class="sxs-lookup"><span data-stu-id="0a79c-191">Once you have clicked on \**_Create_* _:</span></span>

    1.  <span data-ttu-id="0a79c-192">このサービスインスタンスに必要な名前を挿入します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-192">Insert your desired name for this service instance.</span></span>

    2.  <span data-ttu-id="0a79c-193">このアプリに関連付けることができる _ *名前空間*\* を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-193">Provide a _ *namespace*\* which you will be able to associate with this app.</span></span>

    3.  <span data-ttu-id="0a79c-194">場所を選択し **ます。**</span><span class="sxs-lookup"><span data-stu-id="0a79c-194">Select a **Location.**</span></span>

    4.  <span data-ttu-id="0a79c-195">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-195">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="0a79c-196">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-196">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="0a79c-197">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-197">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="0a79c-198">Azure リソースグループの詳細については、 [リソースグループの管理方法に関するリンク](/azure/azure-resource-manager/resource-group-portal)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-198">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](/azure/azure-resource-manager/resource-group-portal).</span></span> 

    5.  <span data-ttu-id="0a79c-199">適切な **サブスクリプション** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-199">Select an appropriate **Subscription**.</span></span>

    6.  <span data-ttu-id="0a79c-200">また、このサービスに適用されている使用条件を理解していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-200">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="0a79c-201">**［作成］** を選択します</span><span class="sxs-lookup"><span data-stu-id="0a79c-201">Select **Create**.</span></span>

        ![サービスの詳細を入力](images/AzureLabs-Lab8-08.png)

5.  <span data-ttu-id="0a79c-203">[ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-203">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="0a79c-204">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-204">A notification will appear in the portal once the Service instance is created.</span></span>

    ![通知 (notification)](images/AzureLabs-Lab8-09.png)

7.  <span data-ttu-id="0a79c-206">通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-206">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="0a79c-207">新しい **Notification Hub** サービスインスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-207">You will be taken to your new **Notification Hub** service instance.</span></span>

    ![リソースにアクセス](images/AzureLabs-Lab8-10.png)
    
8.  <span data-ttu-id="0a79c-209">ページの中央にある [概要] ページで、[ **Windows (WNS)** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-209">From the overview page, halfway down the page, click **Windows (WNS).**</span></span> <span data-ttu-id="0a79c-210">右側のパネルが変更され、以前に設定したアプリから、 **パッケージ SID** と **セキュリティキー** を必要とする2つのテキストフィールドが表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-210">The panel on the right will change to show two text fields, which require your **Package SID** and **Security Key**, from the app you set up previously.</span></span>

    ![新しく作成されたハブサービス](images/AzureLabs-Lab8-11.png)

9. <span data-ttu-id="0a79c-212">詳細を正しいフィールドにコピーしたら、[ **保存**] をクリックすると、通知ハブが正常に更新されたときに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-212">Once you have copied the details into the correct fields, click **Save**, and you will receive a notification when the Notification Hub has been successfully updated.</span></span>

    ![セキュリティの詳細をコピーする](images/AzureLabs-Lab8-12.png)

## <a name="chapter-4---setup-azure-portal-create-table-service"></a><span data-ttu-id="0a79c-214">第4章-Azure Portal のセットアップ: create Table Service</span><span class="sxs-lookup"><span data-stu-id="0a79c-214">Chapter 4 - Setup Azure Portal: create Table Service</span></span>

<span data-ttu-id="0a79c-215">Notification Hubs サービスインスタンスを作成したら、Azure Portal に戻ります。ここでは、ストレージリソースを作成して Azure Tables Service を作成します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-215">After creating your Notification Hubs Service instance, navigate back to your Azure Portal, where you will create an Azure Tables Service by creating a Storage Resource.</span></span>

1.  <span data-ttu-id="0a79c-216">まだサインインしていない場合は、 [Azure Portal](https://portal.azure.com)にログインします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-216">If not already signed in, log into the [Azure Portal](https://portal.azure.com).</span></span>

2.  <span data-ttu-id="0a79c-217">ログインしたら、左上隅にある [ **新規** ] をクリックし、[ **ストレージアカウント**] を検索して、 **Enter キー** を押します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-217">Once logged in, click on **New** in the top left corner, and search for **Storage account**, and click **Enter**.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="0a79c-218">新しいポータルでは、New _ という語が **_ リソースの作成に *置き換えられている可能性があり*** ます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-218">The word \**_New_*_ may have been replaced with _\* Create a resource\*\*, in newer portals.</span></span>

3.  <span data-ttu-id="0a79c-219">一覧から [ **ストレージアカウント-blob、file、table、queue** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-219">Select **Storage account - blob, file, table, queue** from the list.</span></span>

    ![ストレージアカウントの検索](images/AzureLabs-Lab8-13.png)

4.  <span data-ttu-id="0a79c-221">新しいページには、 **ストレージアカウント** サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-221">The new page will provide a description of the **Storage account** service.</span></span> <span data-ttu-id="0a79c-222">このプロンプトの左下にある [ **作成** ] ボタンを選択して、このサービスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-222">At the bottom left of this prompt, select the **Create** button, to create an instance of this service.</span></span>

    ![ストレージインスタンスの作成](images/AzureLabs-Lab8-14.png)

5.  <span data-ttu-id="0a79c-224">[ **作成**] をクリックすると、パネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-224">Once you have clicked on **Create**, a panel will appear:</span></span>

    1. <span data-ttu-id="0a79c-225">このサービスインスタンスに必要な **名前** を挿入します (すべて小文字にする必要があります)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-225">Insert your desired **Name** for this service instance (must be all lowercase).</span></span>

    2. <span data-ttu-id="0a79c-226">[ **デプロイモデル**] で、[ **リソースマネージャー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-226">For **Deployment model**, click **Resource manager**.</span></span>

    3.  <span data-ttu-id="0a79c-227">[ **アカウントの種類**] で、ドロップダウンメニューを使用して、[ **ストレージ (汎用 v1)**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-227">For **Account kind**, using the dropdown menu, select **Storage (general purpose v1)**.</span></span>

    4. <span data-ttu-id="0a79c-228">適切な **場所** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-228">Select an appropriate **Location**.</span></span>
    
    5.  <span data-ttu-id="0a79c-229">[ **レプリケーション** ] ドロップダウンメニューで、[ **読み取りアクセス-geo 冗長ストレージ (RA-GRS)**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-229">For the **Replication** dropdown menu, select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>

    6.  <span data-ttu-id="0a79c-230">[ **パフォーマンス**] で [ **標準**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-230">For **Performance**, click **Standard**.</span></span>

    7.  <span data-ttu-id="0a79c-231">[ **安全な転送が必要** ] セクションで、[ **無効**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-231">Within the **Secure transfer required** section, select **Disabled**.</span></span>

    8.  <span data-ttu-id="0a79c-232">[ **サブスクリプション** ] ドロップダウンメニューから、適切なサブスクリプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-232">From the **Subscription** dropdown menu, select an appropriate subscription.</span></span>

    9.  <span data-ttu-id="0a79c-233">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-233">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="0a79c-234">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-234">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="0a79c-235">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-235">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="0a79c-236">Azure リソースグループの詳細については、 [リソースグループの管理方法に関するリンク](/azure/azure-resource-manager/resource-group-portal)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-236">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="0a79c-237">このオプションが選択されている場合は、[ **仮想ネットワーク** ] を [無効] のまま **に** します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-237">Leave **Virtual networks** as **Disabled** if this is an option for you.</span></span>

    11. <span data-ttu-id="0a79c-238">**Create** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-238">Click **Create**.</span></span>

        ![ストレージの詳細の入力](images/AzureLabs-Lab8-15.png)

6.  <span data-ttu-id="0a79c-240">[ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-240">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="0a79c-241">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-241">A notification will appear in the portal once the Service instance is created.</span></span> <span data-ttu-id="0a79c-242">通知をクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-242">Click on the notifications to explore your new Service instance.</span></span>

    ![新しいストレージ通知](images/AzureLabs-Lab8-16.png)

8.  <span data-ttu-id="0a79c-244">通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-244">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="0a79c-245">新しいストレージサービスインスタンスの概要ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-245">You will be taken to your new Storage Service instance overview page.</span></span>

    ![リソースにアクセス](images/AzureLabs-Lab8-17.PNG)

9. <span data-ttu-id="0a79c-247">[概要] ページで、右側にある [ **テーブル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-247">From the overview page, to the right-hand side, click **Tables**.</span></span>
    
    ![](images/AzureLabs-Lab8-18.PNG)

10. <span data-ttu-id="0a79c-248">右側のパネルが変化し、 **Table service** 情報が表示されます。新しいテーブルを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-248">The panel on the right will change to show the **Table service** information, wherein you need to add a new table.</span></span> <span data-ttu-id="0a79c-249">これを行うには、左上隅にある [ **+** **テーブル** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-249">Do this by clicking the **+** **Table** button to the top-left corner.</span></span>

    ![テーブルを開く](images/AzureLabs-Lab8-19.png)

11. <span data-ttu-id="0a79c-251">新しいページが表示されます。ここには、 **テーブル名** を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-251">A new page will be shown, wherein you need to enter a **Table name**.</span></span> <span data-ttu-id="0a79c-252">これは、後の章でアプリケーション内のデータを参照するために使用する名前です。</span><span class="sxs-lookup"><span data-stu-id="0a79c-252">This is the name you will use to refer to the data in your application in later Chapters.</span></span> <span data-ttu-id="0a79c-253">適切な名前を挿入し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-253">Insert an appropriate name and click **OK**.</span></span>

    ![新しいテーブルの作成](images/AzureLabs-Lab8-20.png)    

12. <span data-ttu-id="0a79c-255">新しいテーブルが作成されると、[ **Table service** ] ページ (下部) に表示されるようになります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-255">Once the new table has been created, you will be able to see it within the **Table service** page (at the bottom).</span></span>

    ![新しいテーブルが作成されました](images/AzureLabs-Lab8-21.png)
    

## <a name="chapter-5---completing-the-azure-table-in-visual-studio"></a><span data-ttu-id="0a79c-257">第5章-Visual Studio での Azure テーブルの完成</span><span class="sxs-lookup"><span data-stu-id="0a79c-257">Chapter 5 - Completing the Azure Table in Visual Studio</span></span>

<span data-ttu-id="0a79c-258">**Table service** ストレージアカウントがセットアップされたので、それにデータを追加します。これは、情報の格納と取得に使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-258">Now that your **Table service** storage account has been setup, it is time to add data to it, which will be used to store and retrieve information.</span></span> <span data-ttu-id="0a79c-259">テーブルの編集は、 **Visual Studio** を使用して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-259">The editing of your Tables can be done through **Visual Studio**.</span></span>

1.  <span data-ttu-id="0a79c-260">**Visual Studio** を開きます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-260">Open **Visual Studio**.</span></span>

2.  <span data-ttu-id="0a79c-261">メニューの [Cloud Explorer の **表示**] をクリックし  >  ます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-261">From the menu, click **View** > **Cloud Explorer**.</span></span>

    ![cloud explorer を開く](images/AzureLabs-Lab8-22.png)

3.  <span data-ttu-id="0a79c-263">**Cloud Explorer** がドッキングされたアイテムとして開きます (読み込みに時間がかかる場合があります)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-263">The **Cloud Explorer** will open as a docked item (be patient, as loading may take time).</span></span>

    > [!NOTE] 
    > <span data-ttu-id="0a79c-264">*ストレージアカウント* の作成に使用したサブスクリプションが表示されない場合は、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-264">If the Subscription you used to create your *Storage Accounts* is not visible, ensure that you have:</span></span> 
    > - <span data-ttu-id="0a79c-265">Azure Portal で使用したものと同じアカウントにログインします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-265">Logged in to the same account as the one you used for the Azure Portal.</span></span>
    > - <span data-ttu-id="0a79c-266">[アカウント管理] ページからサブスクリプションを選択しました (アカウントの設定からフィルターを適用する必要がある場合があります)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-266">Selected your Subscription from the Account Management Page (you may need to apply a filter from your account settings):</span></span>  
    >
    >   ![サブスクリプションの検索](images/AzureLabs-Lab8-22-5.png)

4.  <span data-ttu-id="0a79c-268">Azure cloud services が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-268">Your Azure cloud services will be shown.</span></span> <span data-ttu-id="0a79c-269">**ストレージアカウント** を検索し、左側の矢印をクリックしてアカウントを展開します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-269">Find **Storage Accounts** and click the arrow to the left of that to expand your accounts.</span></span>

    ![ストレージアカウントを開く](images/AzureLabs-Lab8-23.png)

5.  <span data-ttu-id="0a79c-271">展開されると、新しく作成された **ストレージアカウント** を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-271">Once expanded, your newly created **Storage account** should be available.</span></span> <span data-ttu-id="0a79c-272">ストレージの左側にある矢印をクリックし、展開された後、[ **テーブル** ] を見つけて、その横にある矢印をクリックし、最後の章で作成した **テーブル** を表示します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-272">Click the arrow to the left of your storage, and then once that is expanded, find **Tables** and click the arrow next to that, to reveal the **Table** you created in the last Chapter.</span></span> <span data-ttu-id="0a79c-273">**テーブル** をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-273">Double click your **Table**.</span></span>

    ![シーンオブジェクトテーブルを開く](images/AzureLabs-Lab8-24.png)

6.  <span data-ttu-id="0a79c-275">テーブルが Visual Studio ウィンドウの中央に開きます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-275">Your table will be opened in the center of your Visual Studio window.</span></span> <span data-ttu-id="0a79c-276">[テーブル] アイコンをクリックし **+** ます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-276">Click the table icon with the **+** (plus) on it.</span></span>

    ![新しいテーブルの追加](images/AzureLabs-Lab8-25.png)

7.  <span data-ttu-id="0a79c-278">*エンティティの追加* を求めるウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-278">A window will appear prompting for you to *Add Entity*.</span></span> <span data-ttu-id="0a79c-279">合計3つのエンティティを作成し、それぞれに複数のプロパティを付けます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-279">You will create three entities in total, each with several properties.</span></span> <span data-ttu-id="0a79c-280">*Partitionkey* と *RowKey* は既に提供されています。これは、テーブルがデータを検索するために使用されるためです。</span><span class="sxs-lookup"><span data-stu-id="0a79c-280">You will notice that *PartitionKey* and *RowKey* are already provided, as these are used by the table to find your data.</span></span> 

    ![パーティションキーと行キー](images/AzureLabs-Lab8-26.png)

8. <span data-ttu-id="0a79c-282">**Partitionkey** と **RowKey** の *値* を次のように更新します (追加する行プロパティごとにこの操作を行ってください。ただし、RowKey は毎回インクリメントします)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-282">Update the *Value* of the **PartitionKey** and **RowKey** as follows (remember to do this for each row property you add, though increment the RowKey each time):</span></span>

    ![正しい値の追加](images/AzureLabs-Lab8-26-5.png)

9.  <span data-ttu-id="0a79c-284">[ **プロパティの追加** ] をクリックして、余分な行のデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-284">Click **Add property** to add extra rows of data.</span></span> <span data-ttu-id="0a79c-285">最初の空のテーブルを次の表のようにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-285">Make your first empty table match the below table.</span></span>

10. <span data-ttu-id="0a79c-286">完了したら [ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-286">Click **OK** when you are finished.</span></span>

    ![完了したら [ok] をクリックします。](images/AzureLabs-Lab8-27.png)

    > [!WARNING] 
    > <span data-ttu-id="0a79c-288">**X**、 **Y**、 **Z** の各エントリの **種類** を **Double** に変更したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-288">Ensure that you have changed the **Type** of the **X**, **Y**, and **Z**, entries to **Double**.</span></span> 

11. <span data-ttu-id="0a79c-289">テーブルにデータ行があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-289">You will notice your table now has a row of data.</span></span> <span data-ttu-id="0a79c-290">**+**(プラス) アイコンをもう一度クリックして、別のエンティティを追加します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-290">Click the **+** (plus) icon again to add another entity.</span></span>

    ![最初の行](images/AzureLabs-Lab8-27-5.png)

12. <span data-ttu-id="0a79c-292">追加のプロパティを作成し、次に示すように新しいエンティティの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-292">Create an additional property, and then set the values of the new entity to match those shown below.</span></span>

    ![キューブの追加](images/AzureLabs-Lab8-28.png)

13. <span data-ttu-id="0a79c-294">別のエンティティを追加するには、最後の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-294">Repeat the last step to add another entity.</span></span> <span data-ttu-id="0a79c-295">このエンティティの値を次に示すように設定します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-295">Set the values for this entity to those shown below.</span></span>

    ![円柱の追加](images/AzureLabs-Lab8-29.png)

14. <span data-ttu-id="0a79c-297">テーブルは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-297">Your table should now look like the one below.</span></span>

    ![テーブルの完了](images/AzureLabs-Lab8-30.png)

15. <span data-ttu-id="0a79c-299">これで、この章は終了です。</span><span class="sxs-lookup"><span data-stu-id="0a79c-299">You have completed this Chapter.</span></span> <span data-ttu-id="0a79c-300">必ず保存してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-300">Make sure to save.</span></span>

## <a name="chapter-6---create-an-azure-function-app"></a><span data-ttu-id="0a79c-301">第6章-Azure Function App の作成</span><span class="sxs-lookup"><span data-stu-id="0a79c-301">Chapter 6 - Create an Azure Function App</span></span>

<span data-ttu-id="0a79c-302">Azure Function App を作成します。これは、デスクトップアプリケーションによって呼び出され、 **テーブル** サービスを更新し、通知 **ハブ** を介して通知を送信します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-302">Create an Azure Function App, which will be called by the Desktop application to update the **Table** service and send a notification through the **Notification Hub**.</span></span>

<span data-ttu-id="0a79c-303">まず、必要なライブラリを Azure 関数で読み込むことができるファイルを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-303">First, you need to create a file that will allow your Azure Function to load the libraries you need.</span></span>

1.  <span data-ttu-id="0a79c-304">**メモ帳** を開きます (Windows キーを押し、メモ帳を入力します)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-304">Open **Notepad** (press Windows Key and type notepad).</span></span>

    ![メモ帳を開く](images/AzureLabs-Lab8-31.png)

2.  <span data-ttu-id="0a79c-306">メモ帳を開いた状態で、次の JSON 構造を挿入します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-306">With Notepad open, insert the JSON structure below into it.</span></span> <span data-ttu-id="0a79c-307">これが完了したら、 **project.js** としてデスクトップに保存します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-307">Once you have done that, save it on your desktop as **project.json**.</span></span> <span data-ttu-id="0a79c-308">名前が .txt ファイル拡張子 **を持たない** ことを確認することが重要です。</span><span class="sxs-lookup"><span data-stu-id="0a79c-308">It is important that the naming is correct: ensure it does **NOT have a .txt** file extension.</span></span> <span data-ttu-id="0a79c-309">このファイルは、関数が使用するライブラリを定義します。 NuGet を使用している場合は、見慣れたものになります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-309">This file defines the libraries your function will use, if you have used NuGet it will look familiar.</span></span>

    ```json
    {
    "frameworks": {
        "net46":{
        "dependencies": {
            "WindowsAzure.Storage": "7.0.0",
            "Microsoft.Azure.NotificationHubs" : "1.0.9",
            "Microsoft.Azure.WebJobs.Extensions.NotificationHubs" :"1.1.0"
        }
        }
    }
    }
    ```

3.  <span data-ttu-id="0a79c-310">[Azure Portal](https://portal.azure.com) にログインします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-310">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

4.  <span data-ttu-id="0a79c-311">ログインしたら、左上隅にある [ **新規** ] をクリックし、 **Function App** を検索して、 **enter キーを** 押します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-311">Once you are logged in, click on **New** in the top left corner, and search for **Function App**, press **Enter**.</span></span>

    ![function app の検索](images/AzureLabs-Lab8-32.png)

    > [!NOTE] 
    > <span data-ttu-id="0a79c-313">新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="0a79c-313">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

5.  <span data-ttu-id="0a79c-314">新しいページには、 **Function App** サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-314">The new page will provide a description of the **Function App** service.</span></span> <span data-ttu-id="0a79c-315">このプロンプトの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-315">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![function app インスタンス](images/AzureLabs-Lab8-33.png)

6.  <span data-ttu-id="0a79c-317">[ **作成**] をクリックしたら、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-317">Once you have clicked on **Create**, fill in the following:</span></span>

    1. <span data-ttu-id="0a79c-318">[ **アプリ名**] に、このサービスインスタンスに必要な名前を挿入します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-318">For **App name**, insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="0a79c-319">**サブスクリプション** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-319">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="0a79c-320">適切な価格レベルを選択してください。 **Function App サービス** を初めて作成する場合は、free レベルをご利用いただけます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-320">Select the pricing tier appropriate for you, if this is the first time creating a **Function App Service**, a free tier should be available to you.</span></span>

    4. <span data-ttu-id="0a79c-321">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-321">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="0a79c-322">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-322">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="0a79c-323">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-323">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="0a79c-324">Azure リソースグループの詳細については、 [リソースグループの管理方法に関するリンク](/azure/azure-resource-manager/resource-group-portal)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-324">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage a Resource Group](/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="0a79c-325">**OS** の場合は、[Windows] をクリックします。これは目的のプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="0a79c-325">For **OS**, click Windows, as that is the intended platform.</span></span>

    6. <span data-ttu-id="0a79c-326">**ホスティングプラン** を選択します (このチュートリアルでは、**従量課金プラン** を使用しています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-326">Select a **Hosting Plan** (this tutorial is using a **Consumption Plan**.</span></span>

    7. <span data-ttu-id="0a79c-327">**場所** を選択します **(前の手順で作成したストレージと同じ場所を選択します)。**</span><span class="sxs-lookup"><span data-stu-id="0a79c-327">Select a **Location** **(choose the same location as the storage you have built in the previous step)**</span></span>

    8. <span data-ttu-id="0a79c-328">[ **ストレージ** ] セクションでは、 **前の手順で作成したストレージサービスを選択する必要があり** ます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-328">For the **Storage** section, **you must select the Storage Service you created in the previous step**.</span></span>

    9. <span data-ttu-id="0a79c-329">このアプリで *Application Insights* は必要ありませ **ん。そのままにして** おいてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="0a79c-329">You will not need *Application Insights* in this app, so feel free to leave it **Off**.</span></span>

    10. <span data-ttu-id="0a79c-330">**Create** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-330">Click **Create**.</span></span>

        ![新しいインスタンスの作成](images/AzureLabs-Lab8-34.png)

7.  <span data-ttu-id="0a79c-332">[ **作成** ] をクリックすると、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-332">Once you have clicked on **Create** you will have to wait for the service to be created, this might take a minute.</span></span>

8.  <span data-ttu-id="0a79c-333">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-333">A notification will appear in the portal once the Service instance is created.</span></span>

    ![新しい通知](images/AzureLabs-Lab8-35.png)

9.  <span data-ttu-id="0a79c-335">通知をクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-335">Click on the notifications to explore your new Service instance.</span></span>

10. <span data-ttu-id="0a79c-336">通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-336">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> 

    ![リソースにアクセス](images/AzureLabs-Lab8-36.png)

11. <span data-ttu-id="0a79c-338">[ **+** *関数*] の横にある (プラス記号) アイコンをクリックして、 *新しいを作成* します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-338">Click the **+** (plus) icon next to *Functions*, to *Create new*.</span></span>

    ![新しい関数の追加](images/AzureLabs-Lab8-37.png)

12. <span data-ttu-id="0a79c-340">中央のパネル内に [ **関数** の作成] ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-340">Within the central panel, the **Function** creation window will appear.</span></span> <span data-ttu-id="0a79c-341">パネルの上半分にある情報を無視し、[カスタム関数] をクリックします。 [ **カスタム関数**] は、下部 (青い領域) の近くにあります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-341">Ignore the information in the upper half of the panel, and click **Custom function**, which is located near the bottom (in the blue area, as below).</span></span>

    ![カスタム関数](images/AzureLabs-Lab8-38.png)

13. <span data-ttu-id="0a79c-343">ウィンドウ内の新しいページには、さまざまな関数の種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-343">The new page within the window will show various function types.</span></span> <span data-ttu-id="0a79c-344">下にスクロールして紫色の種類を表示し、[ **HTTP PUT** 要素] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-344">Scroll down to view the purple types, and click **HTTP PUT** element.</span></span>

    ![http put リンク](images/AzureLabs-Lab8-39.png)

    > [!IMPORTANT]
    > <span data-ttu-id="0a79c-346">ページの下にスクロールする必要がある場合があります (Azure Portal の更新が実行されている場合、このイメージは正確には見えない可能性があります)。ただし、 *HTTP PUT* という要素を探している場合もあります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-346">You may have to scroll further the down the page (and this image may not look exactly the same, if Azure Portal updates have taken place), however, you are looking for an element called *HTTP PUT*.</span></span>

14. <span data-ttu-id="0a79c-347">[ **HTTP PUT** ] ウィンドウが表示されます。ここで、関数を構成する必要があります (イメージについては以下を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-347">The **HTTP PUT** window will appear, where you need to configure the function (see below for image).</span></span>

    1.  <span data-ttu-id="0a79c-348">[ **言語] で** 、ドロップダウンメニューを使用して [C] を選択し \# ます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-348">For **Language,** using the dropdown menu, select C\#.</span></span>

    2.  <span data-ttu-id="0a79c-349">**[名前]** には、適切な名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-349">For **Name,** input an appropriate name.</span></span>

    3.  <span data-ttu-id="0a79c-350">[ **認証レベル** ] ドロップダウンメニューで、[ **関数**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-350">In the **Authentication level** dropdown menu, select **Function**.</span></span>

    4.  <span data-ttu-id="0a79c-351">[ **テーブル名** ] セクションでは、以前に **テーブル** サービスの作成に使用したのと同じ名前を使用する必要があります (同じ大文字小文字を含む)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-351">For the **Table name** section, you need to use the exact name you used to create your **Table** service previously (including the same letter case).</span></span>

    5.  <span data-ttu-id="0a79c-352">[ **ストレージアカウント接続** ] セクションで、ドロップダウンメニューを使用して、そこからストレージアカウントを選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-352">Within the **Storage account connection** section, use the dropdown menu, and select your storage account from there.</span></span> <span data-ttu-id="0a79c-353">表示されていない場合は、セクションタイトルと共に **新しい** ハイパーリンクをクリックして、ストレージアカウントが表示される別のパネルを表示します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-353">If it is not there, click the **New** hyperlink alongside the section title, to show another panel, where your storage account should be listed.</span></span>

        ![新しいストレージ](images/AzureLabs-Lab8-40.png)

15. <span data-ttu-id="0a79c-355">[ **作成** ] をクリックすると、設定が正常に更新されたことを示す通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-355">Click **Create** and you will receive a notification that your settings have been updated successfully.</span></span>

    ![関数の作成](images/AzureLabs-Lab8-41.png)

16. <span data-ttu-id="0a79c-357">[ **作成**] をクリックすると、関数エディターにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-357">After clicking **Create**, you will be redirected to the function editor.</span></span>

    ![関数コードの更新](images/AzureLabs-Lab8-42.png)

17. <span data-ttu-id="0a79c-359">関数エディターに次のコードを挿入します (関数内のコードを置き換えます)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-359">Insert the following code into the function editor (replacing the code in the function):</span></span>

    ```csharp
    #r "Microsoft.WindowsAzure.Storage"

    using System;
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Table;
    using Microsoft.Azure.NotificationHubs;
    using Newtonsoft.Json;

    public static async Task Run(UnityGameObject gameObj, CloudTable table, IAsyncCollector<Notification> notification, TraceWriter log)
    {
        //RowKey of the table object to be changed
        string rowKey = gameObj.RowKey;

        //Retrieve the table object by its RowKey
        TableOperation operation = TableOperation.Retrieve<UnityGameObject>("UnityPartitionKey", rowKey); 

        TableResult result = table.Execute(operation);

        //Create a UnityGameObject so to set its parameters
        UnityGameObject existingGameObj = (UnityGameObject)result.Result; 

        existingGameObj.RowKey = rowKey;
        existingGameObj.X = gameObj.X;
        existingGameObj.Y = gameObj.Y;
        existingGameObj.Z = gameObj.Z;

        //Replace the table appropriate table Entity with the value of the UnityGameObject
        operation = TableOperation.Replace(existingGameObj); 

        table.Execute(operation);

        log.Verbose($"Updated object position");

        //Serialize the UnityGameObject
        string wnsNotificationPayload = JsonConvert.SerializeObject(existingGameObj);
        
        log.Info($"{wnsNotificationPayload}");

        var headers = new Dictionary<string, string>();

        headers["X-WNS-Type"] = @"wns/raw";

        //Send the raw notification to subscribed devices
        await notification.AddAsync(new WindowsNotification(wnsNotificationPayload, headers)); 

        log.Verbose($"Sent notification");
    }

    // This UnityGameObject represent a Table Entity
    public class UnityGameObject : TableEntity
    {
        public string Type { get; set; }
        public double X { get; set; }
        public double Y { get; set; }
        public double Z { get; set; }
        public string RowKey { get; set; }
    }
    ```

    > [!NOTE]
    > <span data-ttu-id="0a79c-360">関数は、含まれているライブラリを使用して、Unity シーン内で移動されたオブジェクトの名前と場所を受け取ります ( **Unityのオブジェクト** と呼ばれる C# オブジェクトとして)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-360">Using the included libraries, the function receives the name and location of the object which was moved in the Unity scene (as a C# object, called **UnityGameObject**).</span></span> <span data-ttu-id="0a79c-361">このオブジェクトは、作成されたテーブル内のオブジェクトパラメーターを更新するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-361">This object is then used to update the object parameters within the created table.</span></span> <span data-ttu-id="0a79c-362">次に、この関数は、作成された通知ハブサービスを呼び出します。これにより、すべてのサブスクライブ済みアプリケーションが通知されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-362">Following this, the function makes a call to your created Notification Hub service, which notifies all subscribed applications.</span></span>

18. <span data-ttu-id="0a79c-363">コードを配置したら、[ **保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-363">With the code in place, click **Save**.</span></span>

19. <span data-ttu-id="0a79c-364">次に、 **\<** ページの右側にある (矢印) アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-364">Next, click the **\<** (arrow) icon, on the right-hand side of the page.</span></span>

    ![アップロードパネルを開く](images/AzureLabs-Lab8-43.png)

20. <span data-ttu-id="0a79c-366">パネルが右側からスライドします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-366">A panel will slide in from the right.</span></span> <span data-ttu-id="0a79c-367">そのパネルで [ **アップロード**] をクリックすると、ファイルブラウザーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-367">In that panel, click **Upload**, and a File Browser will appear.</span></span>

21. <span data-ttu-id="0a79c-368">に移動して、**メモ帳** で作成したファイルの **project.js** をクリックし、[**開く**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-368">Navigate to, and click, the **project.json** file, which you created in **Notepad** previously, and then click the **Open** button.</span></span> <span data-ttu-id="0a79c-369">このファイルは、関数が使用するライブラリを定義します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-369">This file defines the libraries that your function will use.</span></span>

    ![json のアップロード](images/AzureLabs-Lab8-44.png)

22. <span data-ttu-id="0a79c-371">ファイルがアップロードされると、右側のパネルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-371">When the file has uploaded, it will appear in the panel on the right.</span></span> <span data-ttu-id="0a79c-372">このボタンをクリックすると、 **関数** エディター内で開かれます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-372">Clicking it will open it within the **Function** editor.</span></span> <span data-ttu-id="0a79c-373">この値は、次のイメージと **まったく** 同じである必要があります (手順23以降)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-373">It must look **exactly** the same as the next image (below step 23).</span></span>

23. <span data-ttu-id="0a79c-374">次に、左側のパネルの [ **Functions**] の下にある [ **統合** ] リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-374">Then, in the panel on the left, beneath **Functions**, click the **Integrate** link.</span></span>

    ![integration 関数](images/AzureLabs-Lab8-45.png)

24. <span data-ttu-id="0a79c-376">次のページの右上隅にある [ **詳細エディター** ] (次の手順を参照) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-376">On the next page, in the top right corner, click **Advanced editor** (as below).</span></span>

    ![詳細エディターの起動](images/AzureLabs-Lab8-46.png)

25. <span data-ttu-id="0a79c-378">ファイル **のfunction.js** が中央のパネルに開き、次のコードスニペットで置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-378">A **function.json** file will be opened in the center panel, which needs to be replaced with the following code snippet.</span></span> <span data-ttu-id="0a79c-379">これにより、ビルドする関数と、関数に渡されるパラメーターが定義されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-379">This defines the function you are building and the parameters passed into the function.</span></span>

    ```json
    {
    "bindings": [
        {
        "authLevel": "function",
        "type": "httpTrigger",
        "methods": [
            "get",
            "post"
        ],
        "name": "gameObj",
        "direction": "in"
        },
        {
        "type": "table",
        "name": "table",
        "tableName": "SceneObjectsTable",
        "connection": "mrnothubstorage_STORAGE",
        "direction": "in"
        },
        {
        "type": "notificationHub",
        "direction": "out",
        "name": "notification",
        "hubName": "MR_NotHub_ServiceInstance",
        "connection": "MRNotHubNS_DefaultFullSharedAccessSignature_NH",
        "platform": "wns"
        }
    ]
    }
    ```

26. <span data-ttu-id="0a79c-380">エディターは次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-380">Your editor should now look like the image below:</span></span>

    ![標準エディターに戻る](images/AzureLabs-Lab8-47.png)

27. <span data-ttu-id="0a79c-382">先ほど挿入した入力パラメーターがテーブルとストレージの詳細と一致しないため、情報を更新する必要があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-382">You may notice the input parameters that you have just inserted might not match your table and storage details and therefore will need to be updated with your information.</span></span> <span data-ttu-id="0a79c-383">次に説明するように、ここでは **この操作** を行わないでください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-383">**Do not do this here**, as it is covered next.</span></span> <span data-ttu-id="0a79c-384">ページの右上隅にある **標準のエディター** のリンクをクリックするだけで、戻ることができます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-384">Simply click the **Standard editor** link, in the top-right corner of the page, to go back.</span></span>

28. <span data-ttu-id="0a79c-385">**標準エディター** に戻り、[**入力**] の下にある [ **Azure Table Storage (テーブル)**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-385">Back in the **Standard editor**, click **Azure Table Storage (table)**, under **Inputs**.</span></span> 
    
    ![テーブルの入力](images/AzureLabs-Lab8-47-5.png)

29. <span data-ttu-id="0a79c-387">次の手順に従って、異なる可能性があるため、情報に対して次の一致がある **ことを確認** します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-387">Ensure the following match to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="0a79c-388">**テーブル名**: Azure Storage テーブルサービス内で作成したテーブルの名前。</span><span class="sxs-lookup"><span data-stu-id="0a79c-388">**Table name**: the name of the table you created within your Azure Storage, Tables service.</span></span>

    2.  <span data-ttu-id="0a79c-389">[**ストレージアカウント接続]:** ドロップダウンメニューと共に表示される [**新規**] をクリックすると、ウィンドウの右側にパネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-389">**Storage account connection:** click **new**, which appears alongside the dropdown menu, and a panel will appear to the right of the window.</span></span>

        ![新しいストレージ](images/AzureLabs-Lab8-48.png)

        1.  <span data-ttu-id="0a79c-391">以前に関数アプリをホストするために作成した **ストレージアカウント** を選択し **ます。**</span><span class="sxs-lookup"><span data-stu-id="0a79c-391">Select your **Storage Account**, which you created previously to host the **Function Apps.**</span></span>

        2. <span data-ttu-id="0a79c-392">**ストレージアカウント** の接続値が作成されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-392">You will notice that the **Storage Account** connection value has been created.</span></span>

        3. <span data-ttu-id="0a79c-393">完了したら、必ず [ **保存** してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-393">Make sure to press **Save** once you are done.</span></span>

    3.  <span data-ttu-id="0a79c-394">**入力** ページが次のようになり **、情報が** 表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-394">The **Inputs** page should now match the below, showing **your** information.</span></span>

        ![入力の完了](images/AzureLabs-Lab8-49.png)

30. <span data-ttu-id="0a79c-396">次に、[**出力**] の [ **Azure notification Hub (通知)** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-396">Next, click **Azure Notification Hub (notification)** - under **Outputs**.</span></span> <span data-ttu-id="0a79c-397">次のものが異なる可能性があるため、以下 **の内容が情報と** 一致していることを確認してください (次の手順の下に画像があります)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-397">Ensure the following are matched to **your** information, as they may be different (there is an image below the following steps):</span></span>

    1.  <span data-ttu-id="0a79c-398">[ **Notification Hub 名**]: これは、前に作成した **notification hub** サービスインスタンスの名前です。</span><span class="sxs-lookup"><span data-stu-id="0a79c-398">**Notification Hub Name**: this is the name of your **Notification Hub** service instance, which you created previously.</span></span>

    2.  <span data-ttu-id="0a79c-399">**Notification Hubs 名前空間接続**]: ドロップダウンメニューと共に表示される [ **新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-399">**Notification Hubs namespace connection**: click **new**, which appears alongside the dropdown menu.</span></span>

        ![出力の確認](images/AzureLabs-Lab8-50.png)

    3. <span data-ttu-id="0a79c-401">**接続** ポップアップが表示されます (下図を参照)。ここでは、以前に設定した **通知ハブ** の **名前空間** を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-401">The **Connection** popup will appear (see image below), where you need to select the **Namespace** of the **Notification Hub**, which you set up previously.</span></span>

    4. <span data-ttu-id="0a79c-402">中央のドロップダウンメニューから **通知ハブ** 名を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-402">Select your **Notification Hub** name from the middle dropdown menu.</span></span>

    5.  <span data-ttu-id="0a79c-403">[ **ポリシー** ] ドロップダウンメニューを **Defaultfullsharedaccesssignature** に設定します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-403">Set the **Policy** dropdown menu to **DefaultFullSharedAccessSignature**.</span></span>

    6. <span data-ttu-id="0a79c-404">戻るには、[ **選択** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-404">Click the **Select** button to go back.</span></span>

        ![出力の更新](images/AzureLabs-Lab8-51.png)

31.  <span data-ttu-id="0a79c-406">**出力** ページは次のようになりますが、**情報が代わりに使用** されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-406">The **Outputs** page should now match the below, but with **your** information instead.</span></span> <span data-ttu-id="0a79c-407">必ず [ **保存** してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-407">Make sure to press **Save**.</span></span>

> [!WARNING]
> <span data-ttu-id="0a79c-408">*通知ハブ名を直接編集しない* でください (これは、前の手順に正しく従っていれば、 **詳細エディター** を使用して行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-408">*Do not edit the Notification Hub name directly* (this should all be done using the **Advanced Editor**, provided you followed the previous steps correctly.</span></span>

![出力の完了](images/AzureLabs-Lab8-50.png)

32. <span data-ttu-id="0a79c-410">この時点で、関数が動作していることを確認するために、関数をテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-410">At this point, you should test the function, to ensure it is working.</span></span> <span data-ttu-id="0a79c-411">これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-411">To do this:</span></span> 

    1. <span data-ttu-id="0a79c-412">関数のページにもう一度移動します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-412">Navigate to the function page once more:</span></span>

        ![出力の完了](images/AzureLabs-Lab8-50-1.png)

    2. <span data-ttu-id="0a79c-414">関数のページに戻り、ページの右端にある [ **テスト** ] タブをクリックして、[ *テスト* ] ブレードを開きます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-414">Back on the function page, click the **Test** tab on the far right side of the page, to open the *Test* blade:</span></span>

        ![出力の完了](images/AzureLabs-Lab8-50-2.png)

    3. <span data-ttu-id="0a79c-416">ブレードの [ **要求本文** ] ボックスに、次のコードを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-416">Within the **Request body** textbox of the blade, paste the below code:</span></span>

        ```
        {  
            "Type":null,
            "X":3,
            "Y":0,
            "Z":1,
            "PartitionKey":null,
            "RowKey":"Obj2",
            "Timestamp":"0001-01-01T00:00:00+00:00",
            "ETag":null
        }
        ```

    4. <span data-ttu-id="0a79c-417">テストコードを配置した状態で、右下にある [ **実行** ] ボタンをクリックすると、テストが実行されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-417">With the test code in place, click the **Run** button at the bottom right, and the test will be run.</span></span> <span data-ttu-id="0a79c-418">テストの出力ログは、関数コードの下のコンソール領域に表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-418">The output logs of the test will appear in the console area, below your function code.</span></span>

        ![出力の完了](images/AzureLabs-Lab8-50-3.png)

    > [!WARNING]
    > <span data-ttu-id="0a79c-420">上記のテストが失敗した場合は、上記の手順に厳密に従っていること、特に [ **統合] パネル** 内の設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-420">If the above test fails, you will need to double check that you have followed the above steps exactly, particularly the settings within the **integrate panel**.</span></span> 

## <a name="chapter-7---set-up-desktop-unity-project"></a><span data-ttu-id="0a79c-421">第7章-デスクトップ Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="0a79c-421">Chapter 7 - Set up Desktop Unity Project</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0a79c-422">現在作成中のデスクトップアプリケーションは、Unity エディターでは動作し **ません** 。</span><span class="sxs-lookup"><span data-stu-id="0a79c-422">The Desktop application which you are now creating, **will not** work in the Unity Editor.</span></span> <span data-ttu-id="0a79c-423">これは、Visual Studio (またはデプロイされたアプリケーション) を使用して、アプリケーションのビルド後に、エディターの外部で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-423">It needs to be run outside of the Editor, following the Building of the application, using Visual Studio (or the deployed application).</span></span> 

<span data-ttu-id="0a79c-424">次に示すのは、Unity と mixed reality で開発するための一般的な設定であり、そのため、他のプロジェクトに適したテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="0a79c-424">The following is a typical set up for developing with Unity and mixed reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="0a79c-425">Mixed reality のイマーシブヘッドセットをセットアップしてテストします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-425">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE] 
> <span data-ttu-id="0a79c-426">このコースでは、モーションコントローラーは必要 **ありません** 。</span><span class="sxs-lookup"><span data-stu-id="0a79c-426">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="0a79c-427">イマーシブヘッドセットの設定をサポートする必要がある場合は、 [Windows Mixed Reality のセットアップ方法に関するリンク](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-427">If you need support setting up the immersive headset, please follow this [link on how to set up Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="0a79c-428">**Unity** を開き、[**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-428">Open **Unity** and click **New**.</span></span>

    ![新しい unity プロジェクト](images/AzureLabs-Lab8-52.png)

2.  <span data-ttu-id="0a79c-430">Unity プロジェクト名を指定する必要があります。 **UnityDesktopNotifHub** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-430">You need to provide a Unity Project name, insert **UnityDesktopNotifHub**.</span></span> <span data-ttu-id="0a79c-431">プロジェクトの種類が **3d** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-431">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="0a79c-432">場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-432">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="0a79c-433">次に、[ **プロジェクトの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-433">Then, click **Create project**.</span></span>

    ![プロジェクトの作成](images/AzureLabs-Lab8-53.png)

3.  <span data-ttu-id="0a79c-435">Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-435">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="0a79c-436">[設定の **編集**] に移動し、  >  新しいウィンドウで [**外部ツール**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-436">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="0a79c-437">**外部スクリプトエディター** を **Visual Studio 2017** に変更します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-437">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="0a79c-438">[ **基本設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-438">Close the **Preferences** window.</span></span>

    ![外部 VS ツールの設定](images/AzureLabs-Lab8-54.png)

4.  <span data-ttu-id="0a79c-440">次に、[**ファイル**] [ビルドの設定] に移動して [ユニバーサル Windows プラットフォーム] を選択し、[  >   **プラットフォームの切り替え**] ボタンをクリックして選択内容を適用します。 </span><span class="sxs-lookup"><span data-stu-id="0a79c-440">Next, go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![プラットフォームの切り替え](images/AzureLabs-Lab8-55.png)

5.  <span data-ttu-id="0a79c-442">**ファイル** の  >  **ビルド設定** でも、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-442">While still in **File** > **Build Settings**, make sure that:</span></span>

    1.  <span data-ttu-id="0a79c-443">**ターゲットデバイス** が **任意のデバイス** に設定されています</span><span class="sxs-lookup"><span data-stu-id="0a79c-443">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="0a79c-444">このアプリケーションはデスクトップ用であるため、**任意のデバイス** にする必要があります</span><span class="sxs-lookup"><span data-stu-id="0a79c-444">This Application will be for your desktop, so must be **Any Device**</span></span>

    2.  <span data-ttu-id="0a79c-445">**ビルドの種類** が **D3D** に設定されています</span><span class="sxs-lookup"><span data-stu-id="0a79c-445">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="0a79c-446">**SDK** は最新の **インストール** に設定されています</span><span class="sxs-lookup"><span data-stu-id="0a79c-446">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="0a79c-447">**Visual Studio のバージョン** が、**インストールされている最新** バージョンに設定されています</span><span class="sxs-lookup"><span data-stu-id="0a79c-447">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="0a79c-448">**ビルドと実行** は **ローカルコンピューター** に設定されています</span><span class="sxs-lookup"><span data-stu-id="0a79c-448">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="0a79c-449">ここでは、シーンを保存し、ビルドに追加する価値があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-449">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="0a79c-450">これを行うには、[開いている **シーンの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-450">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="0a79c-451">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-451">A save window will appear.</span></span>

            ![オープンシーンを追加する](images/AzureLabs-Lab8-56.png)

        2. <span data-ttu-id="0a79c-453">この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン**」にします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-453">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新しいシーンフォルダー](images/AzureLabs-Lab8-57.png)

        3. <span data-ttu-id="0a79c-455">新しく作成した [ **シーン** ] フォルダーを開き、[ **ファイル名:** テキスト] フィールドに「 **NH \_ Desktop \_ Scene**」と入力し、[ **保存**] を押します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-455">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_Desktop\_Scene**, then press **Save**.</span></span>

            ![新しい NH_Desktop_Scene](images/AzureLabs-Lab8-58.png)

    7.  <span data-ttu-id="0a79c-457">それ以外の設定は、[ **ビルド設定**] の [既定] のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-457">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="0a79c-458">同じウィンドウで、[プレーヤーの **設定** ] ボタンをクリックすると、 **インスペクター** が配置されている領域の関連パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-458">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

7.  <span data-ttu-id="0a79c-459">このパネルでは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-459">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="0a79c-460">[ **その他の設定** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-460">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="0a79c-461">**Scripting Runtime のバージョン** は実験的である必要があります **(.Net 4.6 と同等)**</span><span class="sxs-lookup"><span data-stu-id="0a79c-461">**Scripting Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**</span></span>

        2. <span data-ttu-id="0a79c-462">**バックエンド** は **.net** である必要があります</span><span class="sxs-lookup"><span data-stu-id="0a79c-462">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="0a79c-463">**API 互換性レベル** は **.net 4.6** である必要があります</span><span class="sxs-lookup"><span data-stu-id="0a79c-463">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![4.6 net バージョン](images/AzureLabs-Lab8-59.png)

    2.  <span data-ttu-id="0a79c-465">[ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-465">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="0a79c-466">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="0a79c-466">**InternetClient**</span></span>

            ![インターネットクライアントを刻む](images/AzureLabs-Lab8-60.png)

8.  <span data-ttu-id="0a79c-468">**ビルド設定** に戻る *Unity C \# プロジェクト* はグレーで表示されなくなりました。この横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-468">Back in **Build Settings** *Unity C\# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="0a79c-469">**[ビルド設定]** ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-469">Close the **Build Settings** window.</span></span>

10. <span data-ttu-id="0a79c-470">シーンとプロジェクト **ファイル** の保存  >  **シーン/ファイル**  >  **保存プロジェクト** を保存します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-470">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0a79c-471">このプロジェクトの *Unity セットアップ* コンポーネント (デスクトップアプリ) をスキップし、コードに直接進む場合は、 [unitypackage をダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage)して、 [**カスタムパッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 [9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)の手順を続行してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-471">If you wish to skip the *Unity Set up* component for this project (Desktop App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-Desktop.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>  <span data-ttu-id="0a79c-472">その場合でも、スクリプトコンポーネントを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-472">You will still need to add the script components.</span></span>

## <a name="chapter-8---importing-the-dlls-in-unity"></a><span data-ttu-id="0a79c-473">章 8-Unity での Dll のインポート</span><span class="sxs-lookup"><span data-stu-id="0a79c-473">Chapter 8 - Importing the DLLs in Unity</span></span>

<span data-ttu-id="0a79c-474">Azure Storage for Unity を使用します (これ自体が .Net SDK for Azure を利用します)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-474">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="0a79c-475">詳細については [、Unity の Azure Storage に関する](/sandbox/gamedev/unity/azure-storage-unity)次のリンク先を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-475">For more information follow this [link about Azure Storage for Unity](/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="0a79c-476">現在、Unity には、インポート後にプラグインを再構成する必要がある既知の問題があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-476">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="0a79c-477">バグが解決された後、これらの手順 (このセクションでは 4-7) は不要になりました。</span><span class="sxs-lookup"><span data-stu-id="0a79c-477">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="0a79c-478">SDK を独自のプロジェクトにインポートするには、GitHub から最新の [**unitypackage**](https://aka.ms/azstorage-unitysdk) をダウンロードしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-478">To import the SDK into your own project, make sure you have downloaded the latest [**.unitypackage**](https://aka.ms/azstorage-unitysdk) from GitHub.</span></span> <span data-ttu-id="0a79c-479">次に、以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-479">Then, do the following:</span></span>

1.  <span data-ttu-id="0a79c-480">[**アセット \> インポートパッケージの \> カスタムパッケージ**] メニューオプションを使用して、 **unitypackage** を Unity に追加します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-480">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="0a79c-481">ポップアップ表示された [ **Unity パッケージのインポート** ] ボックスで、\* \* [_プラグイン_\* ストレージ] \* \* \* の下にあるすべてを選択でき \> ます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-481">In the **Import Unity Package** box that pops up, you can select everything under \*\*_Plugin_ \> \*Storage\*\*\*.</span></span>  <span data-ttu-id="0a79c-482">このコースでは不要なため、他のすべてをオフにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-482">Uncheck everything else, as it is not needed for this course.</span></span>

    ![パッケージへのインポート](images/AzureLabs-Lab8-61.png)

3.  <span data-ttu-id="0a79c-484">[\**_インポート_* _] ボタンをクリックして、プロジェクトに項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-484">Click the \**_Import_* _ button to add the items to your project.</span></span>

4.  <span data-ttu-id="0a79c-485">プロジェクトビューの [**プラグイン**] にある _ *ストレージ*\* フォルダーにアクセスし、次のプラグイン *のみ* を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-485">Go to the _ *Storage*\* folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="0a79c-486">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="0a79c-486">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="0a79c-487">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="0a79c-487">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="0a79c-488">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="0a79c-488">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="0a79c-489">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="0a79c-489">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="0a79c-490">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="0a79c-490">System.Spatial</span></span>

![プラットフォームをすべてオフにする](images/AzureLabs-Lab8-62.png)

5.  <span data-ttu-id="0a79c-492">*これらの特定のプラグイン* を選択した状態で、任意の **プラットフォーム** を **オフ\*\*\*\*にし、** [ **wsaplayer** ]、[**適用**] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-492">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![プラットフォーム dll を適用する](images/AzureLabs-Lab8-63.png)

    > [!NOTE] 
    > <span data-ttu-id="0a79c-494">これらの特定のプラグインを Unity エディターでのみ使用するようにマークしています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-494">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="0a79c-495">これは、プロジェクトが Unity からエクスポートされた後に使用される、WSA フォルダー内に同じプラグインの異なるバージョンがあるためです。</span><span class="sxs-lookup"><span data-stu-id="0a79c-495">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="0a79c-496">[ **ストレージ** プラグイン] フォルダーで、[のみ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-496">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="0a79c-497">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="0a79c-497">Microsoft.Data.Services.Client</span></span>

        ![dll のプロセスを設定しない](images/AzureLabs-Lab8-64.png)

7.  <span data-ttu-id="0a79c-499">[**プラットフォームの設定**] の [**処理しない**] チェックボックスをオンにして、[\**_適用_*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-499">Check the **Don't Process** box under **Platform Settings** and click \**_Apply_* _.</span></span>

    ![処理を適用しない](images/AzureLabs-Lab8-65.png)

    > [!NOTE] 
    > <span data-ttu-id="0a79c-501">Unity アセンブリ patcher はこのプラグインを処理するのが困難であるため、このプラグインを "処理しない" としてマークしています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-501">We are marking this plugin "Don't process", because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="0a79c-502">このプラグインは、処理されていなくても動作します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-502">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="0a79c-503">第9章-Desktop Unity プロジェクトで TableToScene クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="0a79c-503">Chapter 9 - Create the TableToScene class in the Desktop Unity project</span></span>

<span data-ttu-id="0a79c-504">ここで、このアプリケーションを実行するコードを含むスクリプトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-504">You now need to create the scripts containing the code to run this application.</span></span>

<span data-ttu-id="0a79c-505">作成する必要のある最初のスクリプトは、_ \* TableToScene \* \* です。これは次の役割を担います。</span><span class="sxs-lookup"><span data-stu-id="0a79c-505">The first script you need to create is _\*TableToScene\*\*, which is responsible for:</span></span>

-   <span data-ttu-id="0a79c-506">Azure テーブル内のエンティティを読み取っています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-506">Reading entities within the Azure Table.</span></span>
-   <span data-ttu-id="0a79c-507">テーブルデータを使用して、生成するオブジェクトとその位置を決定します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-507">Using the Table data, determine which objects to spawn, and in which position.</span></span>

<span data-ttu-id="0a79c-508">作成する必要がある2番目のスクリプトは **Cloudscene** です。これは次の役割を担います。</span><span class="sxs-lookup"><span data-stu-id="0a79c-508">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="0a79c-509">左クリックイベントを登録して、ユーザーがシーンの周りをドラッグできるようにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-509">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>
-   <span data-ttu-id="0a79c-510">この Unity シーンからオブジェクトデータをシリアル化し、それを Azure Function App に送信します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-510">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="0a79c-511">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="0a79c-511">To create this class:</span></span>

1.  <span data-ttu-id="0a79c-512">[プロジェクト] パネルにある [**アセット**] フォルダーを右クリックし、[フォルダーの **作成**] をクリックし  >  ます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-512">Right-click in the **Asset** Folder located in the Project Panel, **Create** > **Folder**.</span></span> <span data-ttu-id="0a79c-513">フォルダーに **スクリプト** の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-513">Name the folder **Scripts**.</span></span>

    ![スクリプトフォルダーの作成](images/AzureLabs-Lab8-66.png)

    ![スクリプト作成フォルダー2](images/AzureLabs-Lab8-67.png)

2.  <span data-ttu-id="0a79c-516">先ほど作成したフォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-516">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="0a79c-517">**Scripts** フォルダー内を右クリックし、[   >  **C# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-517">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="0a79c-518">スクリプト **Tabletoscene** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-518">Name the script **TableToScene**.</span></span>

    <span data-ttu-id="0a79c-519">![新しい c# スクリプト ](images/AzureLabs-Lab8-68.png)
     ![ tabletoscene の名前変更](images/AzureLabs-Lab8-69.png)</span><span class="sxs-lookup"><span data-stu-id="0a79c-519">![new c# script](images/AzureLabs-Lab8-68.png)
![TableToScene rename](images/AzureLabs-Lab8-69.png)</span></span>

4.  <span data-ttu-id="0a79c-520">スクリプトをダブルクリックして、Visual Studio 2017 で開きます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-520">Double-click on the script to open it in Visual Studio 2017.</span></span>

5.  <span data-ttu-id="0a79c-521">次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-521">Add the following namespaces:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Storage;
    using Microsoft.WindowsAzure.Storage.Auth;
    using Microsoft.WindowsAzure.Storage.Table;
    using UnityEngine;
    ```

6.  <span data-ttu-id="0a79c-522">クラス内に、次の変数を挿入します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-522">Within the class, insert the following variables:</span></span>

    ```csharp
        /// <summary>    
        /// allows this class to behave like a singleton
        /// </summary>    
        public static TableToScene instance;

        /// <summary>    
        /// Insert here you Azure Storage name     
        /// </summary>    
        private string accountName = " -- Insert your Azure Storage name -- ";

        /// <summary>    
        /// Insert here you Azure Storage key    
        /// </summary>    
        private string accountKey = " -- Insert your Azure Storage key -- ";
    ```
    
    > [!NOTE] 
    > <span data-ttu-id="0a79c-523">**AccountName** 値を Azure Storage サービス名と **accountKey** 値に置き換え、Azure Storage サービスのキー値を Azure Portal (次の図を参照) に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-523">Substitute the **accountName** value with your Azure Storage Service name and **accountKey** value with the key value found in the Azure Storage Service, in the Azure Portal (See Image below).</span></span> 
    >
    > ![アカウントキーを取得する](images/AzureLabs-Lab8-70.png)

7.  <span data-ttu-id="0a79c-525">ここで、クラスを初期化する **Start () および起動** 前 **()** の各メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-525">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {  
            // Call method to populate the scene with new objects as 
            // pecified in the Azure Table
            PopulateSceneFromTableAsync();
        }
    ```

8.  <span data-ttu-id="0a79c-526">**Tabletoscene** クラス内で、Azure テーブルから値を取得し、それを使用してシーン内の適切なプリミティブを生成するメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-526">Within the **TableToScene** class, add the method that will retrieve the values from the Azure Table and use them to spawn the appropriate primitives in the scene.</span></span>

    ```csharp
        /// <summary>    
        /// Populate the scene with new objects as specified in the Azure Table    
        /// </summary>    
        private async void PopulateSceneFromTableAsync()
        {
            // Obtain credentials for the Azure Storage
            StorageCredentials creds = new StorageCredentials(accountName, accountKey);

            // Storage account
            CloudStorageAccount account = new CloudStorageAccount(creds, useHttps: true);
            
            // Storage client
            CloudTableClient client = account.CreateCloudTableClient(); 
            
            // Table reference
            CloudTable table = client.GetTableReference("SceneObjectsTable");

            TableContinuationToken token = null;

            // Query the table for every existing Entity
            do
            {
                // Queries the whole table by breaking it into segments
                // (would happen only if the table had huge number of Entities)
                TableQuerySegment<AzureTableEntity> queryResult = await table.ExecuteQuerySegmentedAsync(new TableQuery<AzureTableEntity>(), token); 

                foreach (AzureTableEntity entity in queryResult.Results)
                {
                    GameObject newSceneGameObject = null;
                    Color newColor;

                    // check for the Entity Type and spawn in the scene the appropriate Primitive
                    switch (entity.Type)
                    {
                        case "Cube":
                            // Create a Cube in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                            newColor = Color.blue;
                            break;

                        case "Sphere":
                            // Create a Sphere in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                            newColor = Color.red;
                            break;

                        case "Cylinder":
                            // Create a Cylinder in the scene
                            newSceneGameObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                            newColor = Color.yellow;
                            break;
                        default:
                            newColor = Color.white;
                            break;
                    }

                    newSceneGameObject.name = entity.RowKey;

                    newSceneGameObject.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
                    {
                        color = newColor
                    };

                    //check for the Entity X,Y,Z and move the Primitive at those coordinates
                    newSceneGameObject.transform.position = new Vector3((float)entity.X, (float)entity.Y, (float)entity.Z);
                }

                // if the token is null, it means there are no more segments left to query
                token = queryResult.ContinuationToken;
            }

            while (token != null);
        }
    ```

9.  <span data-ttu-id="0a79c-527">**Tabletoscene** クラスの外部では、**テーブルエンティティ** をシリアル化および逆シリアル化するためにアプリケーションによって使用されるクラスを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-527">Outside the **TableToScene** class, you need to define the class used by the application to serialize and deserialize the **Table Entities**.</span></span>

    ```csharp
        /// <summary>
        /// This objects is used to serialize and deserialize the Azure Table Entity
        /// </summary>
        [System.Serializable]
        public class AzureTableEntity : TableEntity
        {
            public AzureTableEntity(string partitionKey, string rowKey)
                : base(partitionKey, rowKey) { }

            public AzureTableEntity() { }
            public string Type { get; set; }
            public double X { get; set; }
            public double Y { get; set; }
            public double Z { get; set; }
        }
    ```

10. <span data-ttu-id="0a79c-528">Unity エディターに戻る前に、必ず **保存** してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-528">Make sure you **Save** before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="0a79c-529">[**階層**] パネルから **メインカメラ** をクリックして、そのプロパティが **インスペクター** に表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-529">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="0a79c-530">**Scripts** フォルダーを開いた状態で、 **tabletoscene** のスクリプトファイルを選択し、**メインカメラ** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-530">With the **Scripts** folder open, select the script **TableToScene file** and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="0a79c-531">結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-531">The result should be as below:</span></span>

    ![メインカメラにスクリプトを追加する](images/AzureLabs-Lab8-71.png)

## <a name="chapter-10---create-the-cloudscene-class-in-the-desktop-unity-project"></a><span data-ttu-id="0a79c-533">Chapter 10-Desktop Unity プロジェクトで CloudScene クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="0a79c-533">Chapter 10 - Create the CloudScene class in the Desktop Unity Project</span></span>

<span data-ttu-id="0a79c-534">作成する必要がある2番目のスクリプトは **Cloudscene** です。これは次の役割を担います。</span><span class="sxs-lookup"><span data-stu-id="0a79c-534">The second script you need to create is **CloudScene**, which is responsible for:</span></span>

-   <span data-ttu-id="0a79c-535">左クリックイベントを登録して、ユーザーがシーンの周りをドラッグできるようにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-535">Registering the left-click event, to allow the user to drag objects around the scene.</span></span>

-   <span data-ttu-id="0a79c-536">この Unity シーンからオブジェクトデータをシリアル化し、それを Azure Function App に送信します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-536">Serializing the object data from this Unity scene, and sending it to the Azure Function App.</span></span>

<span data-ttu-id="0a79c-537">2番目のスクリプトを作成するには:</span><span class="sxs-lookup"><span data-stu-id="0a79c-537">To create the second script:</span></span>

1.  <span data-ttu-id="0a79c-538">**Scripts** フォルダー内を右クリックし、[**作成**]、[ **C \# スクリプト**] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-538">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="0a79c-539">スクリプトに **Cloudscene** という名前を指定します</span><span class="sxs-lookup"><span data-stu-id="0a79c-539">Name the script **CloudScene**</span></span>
    
    <span data-ttu-id="0a79c-540">![新しい c# スクリプトの ](images/AzureLabs-Lab8-72.png)
     ![ 名前変更 cloudscene](images/AzureLabs-Lab8-73.png)</span><span class="sxs-lookup"><span data-stu-id="0a79c-540">![new c# script](images/AzureLabs-Lab8-72.png)
![rename CloudScene](images/AzureLabs-Lab8-73.png)</span></span>

2.  <span data-ttu-id="0a79c-541">次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-541">Add the following namespaces:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using System.Threading.Tasks;
    using UnityEngine;
    using UnityEngine.Networking;
    ```

3.  <span data-ttu-id="0a79c-542">次の変数を挿入します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-542">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static CloudScene instance;

        /// <summary>
        /// Insert here you Azure Function Url
        /// </summary>
        private string azureFunctionEndpoint = "--Insert here you Azure Function Endpoint--";

        /// <summary>
        /// Flag for object being moved
        /// </summary>
        private bool gameObjHasMoved;

        /// <summary>
        /// Transform of the object being dragged by the mouse
        /// </summary>
        private Transform gameObjHeld;

        /// <summary>
        /// Class hosted in the TableToScene script
        /// </summary>
        private AzureTableEntity azureTableEntity;
    ```

4.  <span data-ttu-id="0a79c-543">次の図に示すように、azure Portal の azure Function App サービスで見つかった Azure Function App URL で **azureFunctionEndpoint** 値を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-543">Substitute the **azureFunctionEndpoint** value with your Azure Function App URL found in the Azure Function App Service, in the Azure Portal, as shown in the image below:</span></span>

    ![関数の URL の取得](images/AzureLabs-Lab8-74.png)

5.  <span data-ttu-id="0a79c-545">ここで、クラスを初期化する **Start () および起動** 前 **()** の各メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-545">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // initialise an AzureTableEntity
            azureTableEntity = new AzureTableEntity();
        }
    ```

6.  <span data-ttu-id="0a79c-546">**Update ()** メソッド内に次のコードを追加します。このコードは、マウス入力を検出してドラッグします。これにより、シーン内のオブジェクトが移動されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-546">Within the **Update()** method, add the following code that will detect the mouse input and drag, which will in turn move GameObjects in the scene.</span></span> <span data-ttu-id="0a79c-547">オブジェクトをドラッグアンドドロップした場合、オブジェクトの名前と座標がメソッド **UpdateCloudScene ()** に渡されます。このメソッドは azure Function App サービスを呼び出します。これにより、azure テーブルが更新され、通知がトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-547">If the user has dragged and dropped an object, it will pass the name and coordinates of the object to the method **UpdateCloudScene()**, which will call the Azure Function App service, which will update the Azure table and trigger the notification.</span></span>

    ```csharp
        /// <summary>
        /// Update is called once per frame
        /// </summary>
        void Update()
        {
            //Enable Drag if button is held down
            if (Input.GetMouseButton(0))
            {
                // Get the mouse position
                Vector3 mousePosition = new Vector3(Input.mousePosition.x, Input.mousePosition.y, 10);

                Vector3 objPos = Camera.main.ScreenToWorldPoint(mousePosition);

                Ray ray = Camera.main.ScreenPointToRay(Input.mousePosition);

                RaycastHit hit;

                // Raycast from the current mouse position to the object overlapped by the mouse
                if (Physics.Raycast(ray, out hit))
                {
                    // update the position of the object "hit" by the mouse
                    hit.transform.position = objPos;

                    gameObjHasMoved = true;

                    gameObjHeld = hit.transform;
                }
            }

            // check if the left button mouse is released while holding an object
            if (Input.GetMouseButtonUp(0) && gameObjHasMoved)
            {
                gameObjHasMoved = false;

                // Call the Azure Function that will update the appropriate Entity in the Azure Table
                // and send a Notification to all subscribed Apps
                Debug.Log("Calling Azure Function");

                StartCoroutine(UpdateCloudScene(gameObjHeld.name, gameObjHeld.position.x, gameObjHeld.position.y, gameObjHeld.position.z));
            }
        }
    ```

7.  <span data-ttu-id="0a79c-548">次のように、 **UpdateCloudScene ()** メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-548">Now add the **UpdateCloudScene()** method, as below:</span></span>

    ```csharp
        private IEnumerator UpdateCloudScene(string objName, double xPos, double yPos, double zPos)
        {
            WWWForm form = new WWWForm();

            // set the properties of the AzureTableEntity
            azureTableEntity.RowKey = objName;

            azureTableEntity.X = xPos;

            azureTableEntity.Y = yPos;

            azureTableEntity.Z = zPos;

            // Serialize the AzureTableEntity object to be sent to Azure
            string jsonObject = JsonConvert.SerializeObject(azureTableEntity);

            using (UnityWebRequest www = UnityWebRequest.Post(azureFunctionEndpoint, jsonObject))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(jsonObject);

                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.uploadHandler.contentType = "application/json";

                www.downloadHandler = new DownloadHandlerBuffer();

                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                string response = www.responseCode.ToString();
            }
        }
    ```

8.  <span data-ttu-id="0a79c-549">コードを保存して Unity に戻る</span><span class="sxs-lookup"><span data-stu-id="0a79c-549">Save the code and return to Unity</span></span>

9.  <span data-ttu-id="0a79c-550">**Cloudscene** スクリプトを **メインカメラ** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-550">Drag the **CloudScene** script onto the **Main Camera**.</span></span> 

    1. <span data-ttu-id="0a79c-551">[**階層**] パネルから **メインカメラ** をクリックして、そのプロパティが **インスペクター** に表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-551">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span> 

    2. <span data-ttu-id="0a79c-552">**Scripts** フォルダーを開いた状態で **cloudscene** スクリプトを選択し、**メインカメラ** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-552">With the **Scripts** folder open, select the **CloudScene** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="0a79c-553">結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-553">The result should be as below:</span></span>

        > ![メインカメラにクラウドスクリプトをドラッグする](images/AzureLabs-Lab8-75.png)

## <a name="chapter-11---build-the-desktop-project-to-uwp"></a><span data-ttu-id="0a79c-555">第11章-UWP へのデスクトッププロジェクトのビルド</span><span class="sxs-lookup"><span data-stu-id="0a79c-555">Chapter 11 - Build the Desktop Project to UWP</span></span>

<span data-ttu-id="0a79c-556">このプロジェクトの Unity セクションに必要なすべてが完了しました。</span><span class="sxs-lookup"><span data-stu-id="0a79c-556">Everything needed for the Unity section of this project has now been completed.</span></span>

1.  <span data-ttu-id="0a79c-557">[**ビルドの設定**] ([**ファイル**  >  **ビルドの設定**]) に移動します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-557">Navigate to **Build Settings** (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="0a79c-558">[ **ビルドの設定** ] ウィンドウで、[ **ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-558">From the **Build Settings** window, click **Build**.</span></span>

    ![プロジェクトのビルド](images/AzureLabs-Lab8-76.png)

3.  <span data-ttu-id="0a79c-560">**ファイルエクスプローラー** ウィンドウがポップアップ表示され、ビルドする場所を入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-560">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="0a79c-561">(左上隅にある [ **新しいフォルダー** ] をクリックして) 新しいフォルダーを作成し、 **ビルド** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-561">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![ビルド用の新しいフォルダー](images/AzureLabs-Lab8-77.png)

    1.  <span data-ttu-id="0a79c-563">[新しい **ビルド** ] フォルダーを開き、別のフォルダーを作成し ( **新しいフォルダー** をもう一度使用)、 **NH \_ Desktop \_ App** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-563">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_Desktop\_App**.</span></span>

        ![フォルダー名 NH_Desktop_App](images/AzureLabs-Lab8-78.png)

    2.  <span data-ttu-id="0a79c-565">**NH \_ デスクトップ \_ アプリ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-565">With the **NH\_Desktop\_App** selected.</span></span> <span data-ttu-id="0a79c-566">[ **フォルダーの選択] を** クリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-566">click **Select Folder**.</span></span> <span data-ttu-id="0a79c-567">プロジェクトがビルドされるまでに1分ほどかかります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-567">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="0a79c-568">次のビルドでは、新しいプロジェクトの場所を示す **ファイルエクスプローラー** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-568">Following build, **File Explorer** will appear showing you the location of your new project.</span></span> <span data-ttu-id="0a79c-569">ただし、次のいくつかの章では、最初に他の Unity プロジェクトを作成する必要があるため、このファイルを開く必要はありません。</span><span class="sxs-lookup"><span data-stu-id="0a79c-569">No need to open it, though, as you need to create the other Unity project first, in the next few Chapters.</span></span>


## <a name="chapter-12---set-up-mixed-reality-unity-project"></a><span data-ttu-id="0a79c-570">第12章-Mixed Reality Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="0a79c-570">Chapter 12 - Set up Mixed Reality Unity Project</span></span>

<span data-ttu-id="0a79c-571">次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="0a79c-571">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="0a79c-572">**Unity** を開き、[**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-572">Open **Unity** and click **New**.</span></span>

    ![新しい unity プロジェクト](images/AzureLabs-Lab8-79.png)

2.  <span data-ttu-id="0a79c-574">ここで、Unity プロジェクト名を入力し、 **UnityMRNotifHub** を挿入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-574">You will now need to provide a Unity Project name, insert **UnityMRNotifHub**.</span></span> <span data-ttu-id="0a79c-575">プロジェクトの種類が **3d** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-575">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="0a79c-576">場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-576">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="0a79c-577">次に、[ **プロジェクトの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-577">Then, click **Create project**.</span></span>

    ![名前 UnityMRNotifHub](images/AzureLabs-Lab8-80.png)

3.  <span data-ttu-id="0a79c-579">Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-579">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="0a79c-580">[設定の **編集**] に移動し、  >  新しいウィンドウで [**外部ツール**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-580">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="0a79c-581">**外部スクリプトエディター** を **Visual Studio 2017** に変更します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-581">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="0a79c-582">[ **基本設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-582">Close the **Preferences** window.</span></span>

    ![外部エディターを VS に設定する](images/AzureLabs-Lab8-81.png)

4.  <span data-ttu-id="0a79c-584">次に、[**ファイル**  >  ] [**ビルドの設定**] の順に移動し、[**プラットフォームの切り替え**] ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-584">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![プラットフォームを UWP に切り替える](images/AzureLabs-Lab8-82.png)

5.  <span data-ttu-id="0a79c-586">**ファイル**  >  の **ビルド設定** にアクセスして、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-586">Go to **File** > **Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="0a79c-587">**ターゲットデバイス** が **任意のデバイス** に設定されています</span><span class="sxs-lookup"><span data-stu-id="0a79c-587">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="0a79c-588">Microsoft HoloLens の場合は、 **ターゲットデバイス** を *HoloLens* に設定します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-588">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="0a79c-589">**ビルドの種類** が **D3D** に設定されています</span><span class="sxs-lookup"><span data-stu-id="0a79c-589">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="0a79c-590">**SDK** は最新の **インストール** に設定されています</span><span class="sxs-lookup"><span data-stu-id="0a79c-590">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="0a79c-591">**Visual Studio のバージョン** が、**インストールされている最新** バージョンに設定されています</span><span class="sxs-lookup"><span data-stu-id="0a79c-591">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="0a79c-592">**ビルドと実行** は **ローカルコンピューター** に設定されています</span><span class="sxs-lookup"><span data-stu-id="0a79c-592">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="0a79c-593">ここでは、シーンを保存し、ビルドに追加する価値があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-593">While here, it is worth saving the scene, and adding it to the build.</span></span>

        1. <span data-ttu-id="0a79c-594">これを行うには、[開いている **シーンの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-594">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="0a79c-595">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-595">A save window will appear.</span></span>

            ![オープンシーンを追加する](images/AzureLabs-Lab8-83.png)

        2. <span data-ttu-id="0a79c-597">この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン**」にします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-597">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新しいシーンフォルダー](images/AzureLabs-Lab8-84.png)

        3. <span data-ttu-id="0a79c-599">新しく作成した [ **シーン** ] フォルダーを開き、[ **ファイル名:** テキスト] フィールドに「 **NH \_ MR \_ シーン**」と入力し、[ **保存**] を押します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-599">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **NH\_MR\_Scene**, then press **Save**.</span></span>

            ![新しいシーン-NH_MR_Scene](images/AzureLabs-Lab8-85.png)

    7.  <span data-ttu-id="0a79c-601">それ以外の設定は、[ **ビルド設定**] の [既定] のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-601">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6.  <span data-ttu-id="0a79c-602">同じウィンドウで、[プレーヤーの **設定** ] ボタンをクリックすると、 **インスペクター** が配置されている領域の関連パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-602">In the same window click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>    

    ![プレーヤーの設定を開く](images/AzureLabs-Lab8-86.png)

7.  <span data-ttu-id="0a79c-604">このパネルでは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-604">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="0a79c-605">[ **その他の設定** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-605">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="0a79c-606">**Scripting Runtime のバージョン** は **実験的** である必要があります (.net 4.6 と同等)</span><span class="sxs-lookup"><span data-stu-id="0a79c-606">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>
        2.  <span data-ttu-id="0a79c-607">**スクリプトバックエンド** は \**_.net_* _ である必要があります</span><span class="sxs-lookup"><span data-stu-id="0a79c-607">**Scripting Backend** should be \**_.NET_* _</span></span>
        3.  <span data-ttu-id="0a79c-608">_ *API 互換性レベル*\* は **.net 4.6** である必要があります</span><span class="sxs-lookup"><span data-stu-id="0a79c-608">_ *API Compatibility Level*\* should be **.NET 4.6**</span></span>

            ![api の互換性](images/AzureLabs-Lab8-87.png)

    2.  <span data-ttu-id="0a79c-610">パネルの下の [ **XR settings** ( **発行の設定**] の下にあります) で、[ **サポートされている仮想現実**] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-610">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![xr 設定の更新](images/AzureLabs-Lab8-88.png)        

    3.  <span data-ttu-id="0a79c-612">[ **発行の設定** ] タブの [ **機能**] で、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-612">Within the **Publishing Settings** tab, under **Capabilities**, heck:</span></span>

        - <span data-ttu-id="0a79c-613">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="0a79c-613">**InternetClient**</span></span>           

            ![インターネットクライアントを刻む](images/AzureLabs-Lab8-89.png)

8.  <span data-ttu-id="0a79c-615">**ビルド設定** に戻ると、 **Unity C# プロジェクト** はグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-615">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out: tick the checkbox next to this.</span></span>

9.  <span data-ttu-id="0a79c-616">これらの変更が完了したら、[ビルドの設定] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-616">With these changes done, close the Build Settings window.</span></span>

10. <span data-ttu-id="0a79c-617">シーンとプロジェクト **ファイル** の保存  >  **シーン/ファイル**  >  **保存プロジェクト** を保存します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-617">Save your Scene and Project **File** > **Save Scene / File** > **Save Project**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="0a79c-618">このプロジェクトの *Unity セットアップ* コンポーネント (Mixed reality アプリ) をスキップしてコードに直接進む場合は、 [unitypackage をダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage)し、 [**カスタムパッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 [14 章](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project)から続行してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-618">If you wish to skip the *Unity Set up* component for this project (mixed reality App), and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20308%20-%20Cross-device%20notifications/Azure-MR-308-MR.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 14](#chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project).</span></span> <span data-ttu-id="0a79c-619">その場合でも、スクリプトコンポーネントを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-619">You will still need to add the script components.</span></span>

### <a name="chapter-13---importing-the-dlls-in-the-mixed-reality-unity-project"></a><span data-ttu-id="0a79c-620">第13章: Mixed Reality Unity プロジェクトでの Dll のインポート</span><span class="sxs-lookup"><span data-stu-id="0a79c-620">Chapter 13 - Importing the DLLs in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="0a79c-621">Azure Storage for Unity library (.Net SDK for Azure を使用) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-621">You will be using Azure Storage for Unity library (which uses the .Net SDK for Azure).</span></span> <span data-ttu-id="0a79c-622">[Unity で Azure Storage を使用する方法については、こちらのリンクを](/sandbox/gamedev/unity/azure-storage-unity)参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-622">Please follow this [link on how to use Azure Storage with Unity](/sandbox/gamedev/unity/azure-storage-unity).</span></span>
<span data-ttu-id="0a79c-623">現在、Unity には、インポート後にプラグインを再構成する必要がある既知の問題があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-623">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="0a79c-624">バグが解決された後、これらの手順 (このセクションでは 4-7) は不要になりました。</span><span class="sxs-lookup"><span data-stu-id="0a79c-624">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="0a79c-625">SDK を独自のプロジェクトにインポートするには、 [unitypackage](https://aka.ms/azstorage-unitysdk)がダウンロードされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-625">To import the SDK into your own project, make sure you have downloaded the latest [.unitypackage](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="0a79c-626">次に、以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-626">Then, do the following:</span></span>

1.  <span data-ttu-id="0a79c-627">[**アセット**  >  **インポートパッケージ**  >  **カスタムパッケージ**] メニューオプションを使用して、上記からダウンロードした unitypackage を Unity に追加します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-627">Add the .unitypackage you downloaded from the above, to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="0a79c-628">ポップアップ表示される [ **Unity パッケージのインポート**] ボックスで、[**プラグイン** ストレージ] の下のすべてを選択でき  >  ます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-628">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage**.</span></span>

    ![パッケージのインポート](images/AzureLabs-Lab8-90.png)

3.  <span data-ttu-id="0a79c-630">[ **インポート** ] ボタンをクリックして、プロジェクトに項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-630">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="0a79c-631">プロジェクトビューの [**プラグイン**] の下にある **ストレージ** フォルダーにアクセスし、次のプラグイン *のみ* を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-631">Go to the **Storage** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="0a79c-632">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="0a79c-632">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="0a79c-633">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="0a79c-633">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="0a79c-634">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="0a79c-634">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="0a79c-635">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="0a79c-635">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="0a79c-636">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="0a79c-636">System.Spatial</span></span>

    ![プラグインの選択](images/AzureLabs-Lab8-91.png)

5.  <span data-ttu-id="0a79c-638">*これらの特定のプラグイン* を選択した状態で、任意の **プラットフォーム** を **オフ\*\*\*\*にし、** [ **wsaplayer** ]、[**適用**] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-638">With *these specific plugins* selected, **uncheck** **Any Platform** and **uncheck** **WSAPlayer** then click **Apply**.</span></span>

    ![プラットフォームの変更の適用](images/AzureLabs-Lab8-92.png)

    > [!NOTE] 
    > <span data-ttu-id="0a79c-640">これらの特定のプラグインを Unity エディターでのみ使用するようにマークしています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-640">You are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="0a79c-641">これは、プロジェクトが Unity からエクスポートされた後に使用される、WSA フォルダー内に同じプラグインの異なるバージョンがあるためです。</span><span class="sxs-lookup"><span data-stu-id="0a79c-641">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="0a79c-642">[ **ストレージ** プラグイン] フォルダーで、[のみ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-642">In the **Storage** plugin folder, select only:</span></span>

    -   <span data-ttu-id="0a79c-643">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="0a79c-643">Microsoft.Data.Services.Client</span></span>

        ![データサービスクライアントの選択](images/AzureLabs-Lab8-93.png)

7.  <span data-ttu-id="0a79c-645">[**プラットフォームの設定**] の [**処理しない**] チェックボックスをオンにし、[**適用**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-645">Check the **Don't Process** box under **Platform Settings** and click **Apply**.</span></span>

    ![処理しない](images/AzureLabs-Lab8-94.png)

    > [!NOTE] 
    > <span data-ttu-id="0a79c-647">Unity アセンブリ patcher がこのプラグインを処理するのが困難であるため、このプラグインを "処理しない" とマークしています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-647">You are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="0a79c-648">プラグインは処理されていなくても機能します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-648">The plugin will still work even though it isn't processed.</span></span>

## <a name="chapter-14---creating-the-tabletoscene-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="0a79c-649">第14章: mixed reality Unity プロジェクトでの TableToScene クラスの作成</span><span class="sxs-lookup"><span data-stu-id="0a79c-649">Chapter 14 - Creating the TableToScene class in the mixed reality Unity project</span></span>

<span data-ttu-id="0a79c-650">**Tabletoscene** クラスは、「 [9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)」で説明したものと同じです。</span><span class="sxs-lookup"><span data-stu-id="0a79c-650">The **TableToScene** class is identical to the one explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span> <span data-ttu-id="0a79c-651">「 [9 章](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project)」で説明されている手順に従って、Mixed Reality Unity プロジェクトに同じクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-651">Create the same class in the mixed reality Unity Project following the same procedure explained in [Chapter 9](#chapter-9---create-the-tabletoscene-class-in-the-desktop-unity-project).</span></span>

<span data-ttu-id="0a79c-652">この章を完了すると、両方の **Unity プロジェクト** のメインカメラにこのクラスが設定されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-652">Once you have completed this Chapter, both of your **Unity Projects** will have this class set up on the Main Camera.</span></span>

## <a name="chapter-15---creating-the-notificationreceiver-class-in-the-mixed-reality-unity-project"></a><span data-ttu-id="0a79c-653">第15章: Mixed Reality Unity プロジェクトで NotificationReceiver クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="0a79c-653">Chapter 15 - Creating the NotificationReceiver class in the Mixed Reality Unity Project</span></span>

<span data-ttu-id="0a79c-654">作成する必要がある2番目のスクリプトは **Notificationreceiver** で、次の役割があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-654">The second script you need to create is **NotificationReceiver**, which is responsible for:</span></span>

-   <span data-ttu-id="0a79c-655">初期化時にアプリを通知ハブに登録しています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-655">Registering the app with the Notification Hub at initialization.</span></span>
-   <span data-ttu-id="0a79c-656">通知ハブからの通知をリッスンしています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-656">Listening to notifications coming from the Notification Hub.</span></span>
-   <span data-ttu-id="0a79c-657">受信した通知からオブジェクトデータを逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-657">Deserializing the object data from received notifications.</span></span>
-   <span data-ttu-id="0a79c-658">逆シリアル化されたデータに基づいて、シーン内のオブジェクトを移動します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-658">Move the GameObjects in the scene, based on the deserialized data.</span></span>

<span data-ttu-id="0a79c-659">**Notificationreceiver** スクリプトを作成するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-659">To create the **NotificationReceiver** script:</span></span>

1.  <span data-ttu-id="0a79c-660">**Scripts** フォルダー内を右クリックし、[**作成**]、[ **C \# スクリプト**] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-660">Right-click inside the **Scripts** folder, click **Create**, **C\# Script**.</span></span> <span data-ttu-id="0a79c-661">スクリプトに **Notificationreceiver** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-661">Name the script **NotificationReceiver**.</span></span>

    <span data-ttu-id="0a79c-662">![新しい c# スクリプト名の作成 ](images/AzureLabs-Lab8-95.png)
     ![ notificationreceiver](images/AzureLabs-Lab8-96.png)</span><span class="sxs-lookup"><span data-stu-id="0a79c-662">![create new c# script](images/AzureLabs-Lab8-95.png)
![name it NotificationReceiver](images/AzureLabs-Lab8-96.png)</span></span>

2.  <span data-ttu-id="0a79c-663">スクリプトをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-663">Double click on the script to open it.</span></span>

3.  <span data-ttu-id="0a79c-664">次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-664">Add the following namespaces:</span></span>

    ```csharp
    //using Microsoft.WindowsAzure.Messaging;
    using Newtonsoft.Json;
    using System;
    using System.Collections;
    using UnityEngine;

    #if UNITY_WSA_10_0 && !UNITY_EDITOR
    using Windows.Networking.PushNotifications;
    #endif
    ```

4.  <span data-ttu-id="0a79c-665">次の変数を挿入します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-665">Insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// allows this class to behave like a singleton
        /// </summary>
        public static NotificationReceiver instance;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        Vector3 newObjPosition;

        /// <summary>
        /// Value set by the notification, object name
        /// </summary>
        string gameObjectName;

        /// <summary>
        /// Value set by the notification, new object position
        /// </summary>
        bool notifReceived;

        /// <summary>
        /// Insert here your Notification Hub Service name 
        /// </summary>
        private string hubName = " -- Insert the name of your service -- ";

        /// <summary>
        /// Insert here your Notification Hub Service "Listen endpoint"
        /// </summary>
        private string hubListenEndpoint = "-Insert your Notification Hub Service Listen endpoint-";
    ```

5.  <span data-ttu-id="0a79c-666">**HubName** 値を通知ハブのサービス名に置き換え、 **hubListenEndpoint** の値を、Azure Portal の azure notification Hub サービスの [アクセスポリシー] タブにある [エンドポイント] の値に置き換えます (下の図を参照)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-666">Substitute the **hubName** value with your Notification Hub Service name, and **hubListenEndpoint** value with the endpoint value found in the Access Policies tab, Azure Notification Hub Service, in the Azure Portal (see image below).</span></span>

    ![notification hub ポリシーエンドポイントの挿入](images/AzureLabs-Lab8-97.png)

6.  <span data-ttu-id="0a79c-668">ここで、クラスを初期化する **Start () および起動** 前 **()** の各メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-668">Now add the **Start()** and **Awake()** methods to initialize the class.</span></span>

    ```csharp
        /// <summary>
        /// Triggers before initialization
        /// </summary>
        void Awake()
        {
            // static instance of this class
            instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Register the App at launch
            InitNotificationsAsync();

            // Begin listening for notifications
            StartCoroutine(WaitForNotification());
        }
    ```

7.  <span data-ttu-id="0a79c-669">次のように、 **waitfornotification** メソッドを追加して、アプリがメインスレッドで競合するを使用せずに Notification Hub ライブラリから通知を受け取ることができるようにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-669">Add the **WaitForNotification** method to allow the app to receive notifications from the Notification Hub Library without clashing with the Main Thread:</span></span>

    ```csharp
        /// <summary>
        /// This notification listener is necessary to avoid clashes 
        /// between the notification hub and the main thread   
        /// </summary>
        private IEnumerator WaitForNotification()
        {
            while (true)
            {
                // Checks for notifications each second
                yield return new WaitForSeconds(1f);

                if (notifReceived)
                {
                    // If a notification is arrived, moved the appropriate object to the new position
                    GameObject.Find(gameObjectName).transform.position = newObjPosition;

                    // Reset the flag
                    notifReceived = false;
                }
            }
        }
    ```

8.  <span data-ttu-id="0a79c-670">次のメソッド **Initnotificationasync ()** を実行すると、初期化時にアプリケーションが Notification Hub サービスに登録されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-670">The following method, **InitNotificationAsync()**, will register the application with the notification Hub Service at initialization.</span></span> <span data-ttu-id="0a79c-671">Unity がプロジェクトをビルドできないため、コードはコメントアウトされています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-671">The code is commented out as Unity will not be able to Build the project.</span></span> <span data-ttu-id="0a79c-672">Visual Studio で Azure メッセージング Nuget パッケージをインポートすると、コメントが削除されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-672">You will remove the comments when you import the Azure Messaging Nuget package in Visual Studio.</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            // PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            // NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            // Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            // if (result.RegistrationId != null)
            // {
            //     Debug.Log($"Registration Successful: {result.RegistrationId}");
            //     channel.PushNotificationReceived += Channel_PushNotificationReceived;
            // }
        }
    ```

9.  <span data-ttu-id="0a79c-673">次のハンドラー ( **Channel \_ pushnotificationreceived ())** は、通知が受信されるたびにトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-673">The following handler, **Channel\_PushNotificationReceived()**, will be triggered every time a notification is received.</span></span> <span data-ttu-id="0a79c-674">通知が逆シリアル化されます。これは、デスクトップアプリケーションで移動された Azure Table エンティティであり、MR シーン内の対応するオブジェクトを同じ位置に移動します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-674">It will deserialize the notification, which will be the Azure Table Entity that has been moved on the Desktop Application, and then move the corresponding GameObject in the MR scene to the same position.</span></span> 
    
    > [!IMPORTANT]
    > <span data-ttu-id="0a79c-675">コードがコメントアウトされるのは、Visual Studio 内で Nuget パッケージマネージャーを使用して Unity プロジェクトをビルドした後に追加する Azure メッセージングライブラリをコードが参照するためです。</span><span class="sxs-lookup"><span data-stu-id="0a79c-675">The code is commented out because the code references the Azure Messaging library, which you will add after building the Unity project using the Nuget Package Manager, within Visual Studio.</span></span> <span data-ttu-id="0a79c-676">そのため、Unity プロジェクトは、コメントアウトされていない限り、ビルドできません。プロジェクトをビルドし、Unity に戻る場合は、そのコードに **コメントを再** 記述する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-676">As such, the Unity project will not be able to build, unless it is commented out. Be aware, that should you build your project, and then wish to return to Unity, you will need to **re-comment** that code.</span></span>

    ```csharp
        ///// <summary>
        ///// Handler called when a Push Notification is received
        ///// </summary>
        //private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)    
        //{
        //    Debug.Log("New Push Notification Received");
        //
        //    if (args.NotificationType == PushNotificationType.Raw)
        //    {
        //        //  Raw content of the Notification
        //        string jsonContent = args.RawNotification.Content;
        //
        //        // Deserialise the Raw content into an AzureTableEntity object
        //        AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);
        //
        //        // The name of the Game Object to be moved
        //        gameObjectName = ate.RowKey;          
        //
        //        // The position where the Game Object has to be moved
        //        newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);
        //
        //        // Flag thats a notification has been received
        //        notifReceived = true;
        //    }
        //}
    ```

10. <span data-ttu-id="0a79c-677">Unity エディターに戻る前に、変更内容を保存しておいてください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-677">Remember to save your changes before going back to the Unity Editor.</span></span>

11. <span data-ttu-id="0a79c-678">[**階層**] パネルから **メインカメラ** をクリックして、そのプロパティが **インスペクター** に表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-678">Click the **Main Camera** from the **Hierarchy** panel, so that its properties appear in the **Inspector**.</span></span>

12. <span data-ttu-id="0a79c-679">**Scripts** フォルダーを開いた状態で、 **notificationreceiver** スクリプトを選択し、**メインカメラ** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-679">With the **Scripts** folder open, select the **NotificationReceiver** script and drag it onto the **Main Camera**.</span></span> <span data-ttu-id="0a79c-680">結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-680">The result should be as below:</span></span>

    ![通知レシーバースクリプトをカメラにドラッグ](images/AzureLabs-Lab8-98.png)

    > [!NOTE]
    > <span data-ttu-id="0a79c-682">Microsoft HoloLens 用にこれを開発している場合は、次のように、 **メインカメラ** の *カメラ* コンポーネントを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-682">If you are developing this for the Microsoft HoloLens, you will need to update the **Main Camera**'s *Camera* component, so that:</span></span>
    > - <span data-ttu-id="0a79c-683">クリアフラグ: 純色</span><span class="sxs-lookup"><span data-stu-id="0a79c-683">Clear Flags: Solid Color</span></span>
    > - <span data-ttu-id="0a79c-684">背景:Black</span><span class="sxs-lookup"><span data-stu-id="0a79c-684">Background: Black</span></span>

## <a name="chapter-16---build-the-mixed-reality-project-to-uwp"></a><span data-ttu-id="0a79c-685">Chapter 16-UWP に対する Mixed Reality プロジェクトの構築</span><span class="sxs-lookup"><span data-stu-id="0a79c-685">Chapter 16 - Build the Mixed Reality Project to UWP</span></span>

<span data-ttu-id="0a79c-686">この章は、前のプロジェクトのビルドプロセスと同じです。</span><span class="sxs-lookup"><span data-stu-id="0a79c-686">This Chapter is identical to build process for the previous project.</span></span> <span data-ttu-id="0a79c-687">このプロジェクトの Unity セクションに必要なものはすべて完了したので、Unity から構築します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-687">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="0a79c-688">[**ビルドの設定**] ([**ファイル**  >  **ビルドの設定**]) に移動します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-688">Navigate to **Build Settings** ( **File** > **Build Settings** ).</span></span>

2.  <span data-ttu-id="0a79c-689">[ **ビルドの設定** ] メニューで、 **Unity C# プロジェクト** _ が表示されていることを確認します (このプロジェクトでは、ビルド後にこのプロジェクトのスクリプトを編集できます)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-689">From the **Build Settings** menu, ensure **Unity C# Projects** _ is ticked (which will allow you to edit the scripts in this project, after build).</span></span>

3.  <span data-ttu-id="0a79c-690">この操作が完了したら、[_ \* ビルド] \* \* をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-690">After this is done, click _\*Build\*\*.</span></span>

    ![プロジェクトのビルド](images/AzureLabs-Lab8-99.png)

4.  <span data-ttu-id="0a79c-692">**ファイルエクスプローラー** ウィンドウがポップアップ表示され、ビルドする場所を入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-692">A **File Explorer** window will popup, prompting you for a location to Build.</span></span> <span data-ttu-id="0a79c-693">(左上隅にある [ **新しいフォルダー** ] をクリックして) 新しいフォルダーを作成し、 **ビルド** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-693">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![ビルドフォルダーの作成](images/AzureLabs-Lab8-100.png)

    1.  <span data-ttu-id="0a79c-695">[新しい **ビルド** ] フォルダーを開き、別のフォルダーを作成し ([ **新しいフォルダー** ] をもう一度使用)、「 **NH \_ MR \_ App**」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-695">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **NH\_MR\_App**.</span></span>

        ![NH_MR_Apps フォルダーの作成](images/AzureLabs-Lab8-101.png)

    2.  <span data-ttu-id="0a79c-697">**NH \_ MR \_ アプリ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-697">With the **NH\_MR\_App** selected.</span></span> <span data-ttu-id="0a79c-698">[ **フォルダーの選択] を** クリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-698">click **Select Folder**.</span></span> <span data-ttu-id="0a79c-699">プロジェクトがビルドされるまでに1分ほどかかります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-699">The project will take a minute or so to build.</span></span>

5.  <span data-ttu-id="0a79c-700">ビルドの後に、新しいプロジェクトの場所で **ファイルエクスプローラー** ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-700">Following the build, a **File Explorer** window will open at the location of your new project.</span></span>



## <a name="chapter-17---add-nuget-packages-to-the-unitymrnotifhub-solution"></a><span data-ttu-id="0a79c-701">Chapter 17-NuGet パッケージを UnityMRNotifHub ソリューションに追加する</span><span class="sxs-lookup"><span data-stu-id="0a79c-701">Chapter 17 - Add NuGet packages to the UnityMRNotifHub Solution</span></span>

> [!WARNING] 
> <span data-ttu-id="0a79c-702">次の NuGet パッケージを追加し (次の [章](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)のコードのコメントを解除すると)、Unity プロジェクト内で再度開いたときに、エラーが表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0a79c-702">Please remember that, once you add the following NuGet Packages (and uncomment the code in the next [Chapter](#chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class)), the Code, when reopened within the Unity Project, will present errors.</span></span> <span data-ttu-id="0a79c-703">引き続き Unity エディターで編集を続行する場合は、Visual Studio に戻ると、コードの一部をコメントにして、後で再度コメントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-703">If you wish to go back and continue editing in the Unity Editor, you will need comment that errosome code, and then uncomment again later, once you are back in Visual Studio.</span></span> 

<span data-ttu-id="0a79c-704">Mixed reality ビルドが完了したら、ビルドした mixed reality プロジェクトに移動し、そのフォルダー内のソリューション (.sln) ファイルをダブルクリックして、Visual Studio 2017 でソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-704">Once the mixed reality build has been completed, navigate to the mixed reality project, which you built, and double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>
<span data-ttu-id="0a79c-705">次に、 **Windowsazure.servicebus** NuGet パッケージを追加する必要があります。これは、通知ハブから通知を受信するために使用されるライブラリです。</span><span class="sxs-lookup"><span data-stu-id="0a79c-705">You will now need to add the **WindowsAzure.Messaging.managed** NuGet package; this is a library that is used to receive Notifications from the Notification Hub.</span></span>

<span data-ttu-id="0a79c-706">NuGet パッケージをインポートするには:</span><span class="sxs-lookup"><span data-stu-id="0a79c-706">To import the NuGet package:</span></span>

1.  <span data-ttu-id="0a79c-707">**ソリューションエクスプローラー** で、ソリューションを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-707">In the **Solution Explorer**, right click on your Solution</span></span>

2.  <span data-ttu-id="0a79c-708">[ **NuGet パッケージの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-708">Click on **Manage NuGet Packages**.</span></span>

    ![nuget マネージャーを開く](images/AzureLabs-Lab8-102.png)

3.  <span data-ttu-id="0a79c-710">[ **_参照_\*_] タブを選択し、_ windowsazure.servicebus を検索**\* します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-710">Select the \**_Browse_*_ tab and search for _\* WindowsAzure.Messaging.managed\*\*.</span></span>

    ![windows azure メッセージングパッケージの検索](images/AzureLabs-Lab8-103.png)

4.  <span data-ttu-id="0a79c-712">次に示すように結果を選択し、右側のウィンドウで [ **Project**] の横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-712">Select the result (as shown below), and in the window to the right, select the checkbox next to **Project**.</span></span> <span data-ttu-id="0a79c-713">これにより、[**プロジェクト**] の横にあるチェックボックスと、 **UnityMRNotifHub** **プロジェクトの横** のチェックボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-713">This will place a tick in the checkbox next to **Project**, along with the checkbox next to the **Assembly-CSharp** and **UnityMRNotifHub** project.</span></span>

    ![すべてのプロジェクトを目盛りする](images/AzureLabs-Lab8-104.png)

5.  <span data-ttu-id="0a79c-715">最初に指定されたバージョンは、このプロジェクトと互換性が **ない可能性があり** ます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-715">The version initially provided **may not** be compatible with this project.</span></span> <span data-ttu-id="0a79c-716">そのため、[ **バージョン**] の横にあるドロップダウンメニューをクリックし、[ **バージョン 0.1.7.9**]、[ **インストール**] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-716">Therefore, click on the dropdown menu next to **Version**, and click **Version 0.1.7.9**, then click **Install**.</span></span>

6.  <span data-ttu-id="0a79c-717">これで、NuGet パッケージのインストールが完了しました。</span><span class="sxs-lookup"><span data-stu-id="0a79c-717">You have now finished installing the NuGet package.</span></span> <span data-ttu-id="0a79c-718">**Notificationreceiver** クラスに入力したコメントが付いているコードを見つけて、コメントを削除します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-718">Find the commented code you entered in the **NotificationReceiver** class and remove the comments..</span></span>



## <a name="chapter-18---edit-unitymrnotifhub-application-notificationreceiver-class"></a><span data-ttu-id="0a79c-719">第18章-Edit UnityMRNotifHub application, NotificationReceiver クラス</span><span class="sxs-lookup"><span data-stu-id="0a79c-719">Chapter 18 - Edit UnityMRNotifHub application, NotificationReceiver class</span></span>

<span data-ttu-id="0a79c-720">**NuGet パッケージ** を追加した後、 **notificationreceiver** クラス内のコードの一部を *コメント* 解除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-720">Following having added the **NuGet Packages**, you will need to *uncomment* some of the code within the **NotificationReceiver** class.</span></span>

<span data-ttu-id="0a79c-721">これには次のものが含まれます</span><span class="sxs-lookup"><span data-stu-id="0a79c-721">This includes:</span></span>

1. <span data-ttu-id="0a79c-722">先頭にある名前空間:</span><span class="sxs-lookup"><span data-stu-id="0a79c-722">The namespace at the top:</span></span>

    ```csharp
    using Microsoft.WindowsAzure.Messaging;
    ```

2. <span data-ttu-id="0a79c-723">**InitNotificationsAsync ()** メソッド内のすべてのコード:</span><span class="sxs-lookup"><span data-stu-id="0a79c-723">All the code within the **InitNotificationsAsync()** method:</span></span>

    ```csharp
        /// <summary>
        /// Register this application to the Notification Hub Service
        /// </summary>
        private async void InitNotificationsAsync()
        {
            PushNotificationChannel channel = await PushNotificationChannelManager.CreatePushNotificationChannelForApplicationAsync();

            NotificationHub hub = new NotificationHub(hubName, hubListenEndpoint);

            Registration result = await hub.RegisterNativeAsync(channel.Uri);

            // If registration was successful, subscribe to Push Notifications
            if (result.RegistrationId != null)
            {
                Debug.Log($"Registration Successful: {result.RegistrationId}");
                channel.PushNotificationReceived += Channel_PushNotificationReceived;
            }
        }
    ```

> [!WARNING]
> <span data-ttu-id="0a79c-724">上記のコードにはコメントが含まれています。コメントが *誤って* コメント解除されていないことを確認してください (コードがを持っている場合はコンパイルされません)。</span><span class="sxs-lookup"><span data-stu-id="0a79c-724">The code above has a comment in it: ensure that you have not accidentally *uncommented* that comment (as the code will not compile if you have!).</span></span>

3. <span data-ttu-id="0a79c-725">最後に、 **Channel_PushNotificationReceived** イベントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-725">And, lastly, the **Channel_PushNotificationReceived** event:</span></span>

    ```csharp
        /// <summary>
        /// Handler called when a Push Notification is received
        /// </summary>
        private void Channel_PushNotificationReceived(PushNotificationChannel sender, PushNotificationReceivedEventArgs args)
        {
            Debug.Log("New Push Notification Received");

            if (args.NotificationType == PushNotificationType.Raw)
            {
                //  Raw content of the Notification
                string jsonContent = args.RawNotification.Content;

                // Deserialize the Raw content into an AzureTableEntity object
                AzureTableEntity ate = JsonConvert.DeserializeObject<AzureTableEntity>(jsonContent);

                // The name of the Game Object to be moved
                gameObjectName = ate.RowKey;

                // The position where the Game Object has to be moved
                newObjPosition = new Vector3((float)ate.X, (float)ate.Y, (float)ate.Z);

                // Flag thats a notification has been received
                notifReceived = true;
            }
        }
    ```

<span data-ttu-id="0a79c-726">これらのコメントを解除したら、必ず保存し、次の章に進みます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-726">With these uncommented, ensure that you save, and then proceed to the next Chapter.</span></span>

## <a name="chapter-19---associate-the-mixed-reality-project-to-the-store-app"></a><span data-ttu-id="0a79c-727">第19章-mixed reality プロジェクトをストアアプリに関連付ける</span><span class="sxs-lookup"><span data-stu-id="0a79c-727">Chapter 19 - Associate the mixed reality project to the Store app</span></span>

<span data-ttu-id="0a79c-728">ここで、ラボの開始時にで作成したストアアプリに **mixed reality** プロジェクトを関連付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-728">You now need to associate the **mixed reality** project to the Store App you created in at the start of the lab.</span></span>

1.  <span data-ttu-id="0a79c-729">ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-729">Open the solution.</span></span>

2.  <span data-ttu-id="0a79c-730">ソリューションエクスプローラーパネルで UWP アプリプロジェクトを右クリックし、[ **ストア** に移行] をクリックして、 **アプリをストアに関連付け** ます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-730">Right click on the UWP app Project in the Solution Explorer panel, the go to **Store**, and **Associate App with the Store...**.</span></span>

    ![ストアの関連付けを開く](images/AzureLabs-Lab8-105.png)

3.  <span data-ttu-id="0a79c-732">**[アプリを Windows ストアと関連付ける**] という新しいウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-732">A new window will appear called **Associate Your App with the Windows Store**.</span></span> <span data-ttu-id="0a79c-733">**[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-733">Click **Next**.</span></span>

    ![次の画面に進む](images/AzureLabs-Lab8-106.png)

4.  <span data-ttu-id="0a79c-735">これにより、ログインしたアカウントに関連付けられているすべてのアプリケーションが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-735">It will load up all the Applications associated with the Account which you have logged in.</span></span> <span data-ttu-id="0a79c-736">アカウントにログインしていない場合は、このページで **ログイン** できます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-736">If you are not logged in to your account, you can **Log In** on this page.</span></span>

5.  <span data-ttu-id="0a79c-737">このチュートリアルの開始時に作成した **ストアアプリの名前** を探し、それを選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-737">Find the **Store App name** that you created at the start of this tutorial and select it.</span></span> <span data-ttu-id="0a79c-738">続けて、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-738">Then click **Next**.</span></span>

    ![ストア名を検索して選択します](images/AzureLabs-Lab8-107.png)

6.  <span data-ttu-id="0a79c-740">**[関連付け]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-740">Click **Associate**.</span></span>

    ![アプリを関連付ける](images/AzureLabs-Lab8-108.png)

7.  <span data-ttu-id="0a79c-742">これで、アプリがストアアプリに **関連付けら** れました。</span><span class="sxs-lookup"><span data-stu-id="0a79c-742">Your App is now **Associated** with the Store App.</span></span> <span data-ttu-id="0a79c-743">これは、通知を有効にするために必要です。</span><span class="sxs-lookup"><span data-stu-id="0a79c-743">This is necessary for enabling Notifications.</span></span>

## <a name="chapter-20---deploy-unitymrnotifhub-and-unitydesktopnotifhub-applications"></a><span data-ttu-id="0a79c-744">第20章-UnityMRNotifHub アプリケーションと UnityDesktopNotifHub アプリケーションのデプロイ</span><span class="sxs-lookup"><span data-stu-id="0a79c-744">Chapter 20 - Deploy UnityMRNotifHub and UnityDesktopNotifHub applications</span></span>

<span data-ttu-id="0a79c-745">この章では、2人の方で簡単に実行できます。これは、実行中のアプリと、コンピューターのデスクトップで実行されているアプリと、イマーシブヘッドセット内のアプリの両方が含まれるためです。</span><span class="sxs-lookup"><span data-stu-id="0a79c-745">This Chapter may be easier with two people, as the result will include both apps running, one running on your computer Desktop, and the other within your immersive headset.</span></span>

<span data-ttu-id="0a79c-746">イマーシブヘッドセットアプリは、シーンへの変更を受信するのを待機しています (ローカルのユーザーオブジェクトの位置の変更)。デスクトップアプリは、ローカルシーン (位置の変更) に変更を加えます。これは MR アプリに共有されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-746">The immersive headset app is waiting to receive changes to the scene (position changes of the local GameObjects), and the Desktop app will be making changes to their local scene (position changes), which will be shared to the MR app.</span></span> <span data-ttu-id="0a79c-747">最初に MR アプリをデプロイし、次にデスクトップアプリを展開して、受信側がリッスンを開始できるようにすることが理にかなっています。</span><span class="sxs-lookup"><span data-stu-id="0a79c-747">It makes sense to deploy the MR app first, followed by the Desktop app, so that the receiver can begin listening.</span></span>

<span data-ttu-id="0a79c-748">ローカルコンピューターに **UnityMRNotifHub** アプリをデプロイするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-748">To deploy the **UnityMRNotifHub** app on your Local Machine:</span></span>

1.  <span data-ttu-id="0a79c-749">**Visual Studio 2017** で **UnityMRNotifHub** アプリのソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-749">Open the solution file of your **UnityMRNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="0a79c-750">**ソリューションプラットフォーム** で、[ **X86, ローカルコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-750">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="0a79c-751">**ソリューション構成** で、[**デバッグ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-751">In the **Solution Configuration** select **Debug**.</span></span>

    ![プロジェクト構成の設定](images/AzureLabs-Lab8-109.png)

4.  <span data-ttu-id="0a79c-753">[ **ビルド] メニュー** の [ **ソリューションの配置** ] をクリックして、アプリケーションをコンピューターにサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-753">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="0a79c-754">アプリがインストール済みのアプリの一覧に表示され、起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-754">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="0a79c-755">ローカルコンピューターに **UnityDesktopNotifHub** アプリをデプロイするには:</span><span class="sxs-lookup"><span data-stu-id="0a79c-755">To deploy the **UnityDesktopNotifHub** app on Local Machine:</span></span>

1.  <span data-ttu-id="0a79c-756">**Visual Studio 2017** で **UnityDesktopNotifHub** アプリのソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-756">Open the solution file of your **UnityDesktopNotifHub** app in **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="0a79c-757">**ソリューションプラットフォーム** で、[ **X86, ローカルコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-757">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="0a79c-758">**ソリューション構成** で、[**デバッグ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-758">In the **Solution Configuration** select **Debug**.</span></span>

    ![プロジェクト構成の設定](images/AzureLabs-Lab8-110.png)

4.  <span data-ttu-id="0a79c-760">[ **ビルド] メニュー** の [ **ソリューションの配置** ] をクリックして、アプリケーションをコンピューターにサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="0a79c-760">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="0a79c-761">アプリがインストール済みのアプリの一覧に表示され、起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="0a79c-761">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

6.  <span data-ttu-id="0a79c-762">Mixed reality アプリケーションを起動し、その後にデスクトップアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-762">Launch the mixed reality application, followed by the Desktop application.</span></span>

<span data-ttu-id="0a79c-763">両方のアプリケーションを実行している状態で、(マウスの左ボタンを使用して) デスクトップシーンでオブジェクトを移動します。</span><span class="sxs-lookup"><span data-stu-id="0a79c-763">With both applications running, move an object in the desktop scene (using the Left Mouse Button).</span></span> <span data-ttu-id="0a79c-764">これらの位置指定の変更は、ローカルでシリアル化され、Function App サービスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-764">These positional changes will be made locally, serialized, and sent to the Function App service.</span></span> <span data-ttu-id="0a79c-765">その後、Function App サービスによって、通知ハブと共にテーブルが更新されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-765">The Function App service will then update the Table along with the Notification Hub.</span></span> <span data-ttu-id="0a79c-766">更新を受信すると、通知ハブは、更新されたデータをすべての登録済みアプリケーション (この場合はイマーシブヘッドセットアプリ) に直接送信します。この場合、受信データが逆シリアル化され、ローカルオブジェクトに新しい位置指定データが適用され、シーン内で移動されます。</span><span class="sxs-lookup"><span data-stu-id="0a79c-766">Having received an update, the Notification Hub will send the updated data directly to all the registered applications (in this case the immersive headset app), which will then deserialize the incoming data, and apply the new positional data to the local objects, moving them in scene.</span></span>


## <a name="your-finished-your-azure-notification-hubs-application"></a><span data-ttu-id="0a79c-767">Azure Notification Hubs アプリケーションが完成しました</span><span class="sxs-lookup"><span data-stu-id="0a79c-767">Your finished your Azure Notification Hubs application</span></span>
 
<span data-ttu-id="0a79c-768">これで、Azure Notification Hubs サービスを活用し、アプリ間の通信を可能にする mixed reality アプリを構築しました。</span><span class="sxs-lookup"><span data-stu-id="0a79c-768">Congratulations, you built a mixed reality app that leverages the Azure Notification Hubs Service and allow communication between apps.</span></span>
 
![最終製品-終了](images/AzureLabs-Lab8-00.png)
 
## <a name="bonus-exercises"></a><span data-ttu-id="0a79c-770">ボーナス演習</span><span class="sxs-lookup"><span data-stu-id="0a79c-770">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="0a79c-771">演習1</span><span class="sxs-lookup"><span data-stu-id="0a79c-771">Exercise 1</span></span>

<span data-ttu-id="0a79c-772">再生オブジェクトの色を変更し、その通知をシーンを表示している他のアプリに送信する方法はありますか。</span><span class="sxs-lookup"><span data-stu-id="0a79c-772">Can you work out how to change the color of the GameObjects and send that notification to other apps viewing the scene?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="0a79c-773">演習2</span><span class="sxs-lookup"><span data-stu-id="0a79c-773">Exercise 2</span></span>

<span data-ttu-id="0a79c-774">MR アプリへのユーザーの移動を追加して、デスクトップアプリで更新されたシーンを表示できますか。</span><span class="sxs-lookup"><span data-stu-id="0a79c-774">Can you add movement of the GameObjects to your MR app and see the updated scene in your desktop app?</span></span>