---
title: MR と Azure 309-Application insights
description: このコースでは、Azure アプリケーション Insights サービスを使用して、mixed reality アプリケーション内でユーザーの動作に関する分析を収集する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、application insights、hololens、イマーシブ、vr、Windows 10、Visual Studio
ms.openlocfilehash: d663da0e3a0d00532669a122dc95f2089bf08712
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679471"
---
# <a name="mr-and-azure-309-application-insights"></a><span data-ttu-id="18eb1-104">MR と Azure 309:Application Insights</span><span class="sxs-lookup"><span data-stu-id="18eb1-104">MR and Azure 309: Application insights</span></span>

<br>

>[!NOTE]
><span data-ttu-id="18eb1-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="18eb1-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="18eb1-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="18eb1-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="18eb1-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。</span><span class="sxs-lookup"><span data-stu-id="18eb1-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="18eb1-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="18eb1-109">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="18eb1-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="18eb1-110">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

![最終製品-開始](images/AzureLabs-Lab309-00.png)

<span data-ttu-id="18eb1-112">このコースでは、Azure アプリケーション Insights API を使用してユーザーの行動に関する分析を収集することにより、Application Insights 機能を混合の現実アプリケーションに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-112">In this course, you will learn how to add Application Insights capabilities to a mixed reality application, using the Azure Application Insights API to collect analytics regarding user behavior.</span></span>

<span data-ttu-id="18eb1-113">Application Insights は Microsoft のサービスであり、開発者はアプリケーションから分析を収集し、使いやすいポータルから管理できます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-113">Application Insights is a Microsoft service, allowing developers to collect analytics from their applications and manage it from an easy-to-use portal.</span></span> <span data-ttu-id="18eb1-114">分析には、パフォーマンスから収集するカスタム情報まで、あらゆるものを選択できます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-114">The analytics can be anything from performance to custom information you would like to collect.</span></span> <span data-ttu-id="18eb1-115">詳細については、 [Application Insights のページ](https://azure.microsoft.com/services/application-insights/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="18eb1-115">For more information, visit the [Application Insights page](https://azure.microsoft.com/services/application-insights/).</span></span>

<span data-ttu-id="18eb1-116">このコースを完了すると、現実のイマーシブヘッドセットアプリケーションが完成し、次のことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="18eb1-117">シーンを見つめて移動することをユーザーに許可します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-117">Allow the user to gaze and move around a scene.</span></span>
2.  <span data-ttu-id="18eb1-118">シーン内オブジェクトとの間での使用を通じて、 *Application Insights サービス* への分析の送信をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-118">Trigger the sending of analytics to the *Application Insights Service*, through the use of Gaze and Proximity to in-scene objects.</span></span>
3.  <span data-ttu-id="18eb1-119">また、アプリはサービスに対してを呼び出し、過去24時間以内にユーザーによって最も頻繁に近づいたオブジェクトに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-119">The app will also call upon the Service, fetching information about which object has been approached the most by the user, within the last 24 hours.</span></span> <span data-ttu-id="18eb1-120">そのオブジェクトの色が緑色に変わります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-120">That object will change its color to green.</span></span>

<span data-ttu-id="18eb1-121">このコースでは、Application Insights サービスから Unity ベースのサンプルアプリケーションに結果を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-121">This course will teach you how to get the results from the Application Insights Service, into a Unity-based sample application.</span></span> <span data-ttu-id="18eb1-122">これらの概念は、構築しているカスタムアプリケーションに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-122">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="18eb1-123">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="18eb1-123">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="18eb1-124">コース</span><span class="sxs-lookup"><span data-stu-id="18eb1-124">Course</span></span></th><th style="width:150px"> <span data-ttu-id="18eb1-125"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="18eb1-125"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="18eb1-126"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="18eb1-126"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="18eb1-127">MR と Azure 309:Application Insights</span><span class="sxs-lookup"><span data-stu-id="18eb1-127">MR and Azure 309: Application insights</span></span></td><td style="text-align: center;"> <span data-ttu-id="18eb1-128">✔️</span><span class="sxs-lookup"><span data-stu-id="18eb1-128">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="18eb1-129">✔️</span><span class="sxs-lookup"><span data-stu-id="18eb1-129">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="18eb1-130">このコースでは主に Windows Mixed Reality イマーシブ (VR) ヘッドセットに焦点を当てていますが、このコースで学習した内容を Microsoft HoloLens に適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-130">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="18eb1-131">このコースに従うと、HoloLens をサポートするために必要となる可能性のある変更に関する注意事項が表示されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-131">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="18eb1-132">HoloLens を使用する場合、音声キャプチャ中にエコーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-132">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="18eb1-133">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="18eb1-133">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="18eb1-134">このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="18eb1-134">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="18eb1-135">また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証された内容 (2018 年7月) を表しています。</span><span class="sxs-lookup"><span data-stu-id="18eb1-135">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="18eb1-136">「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものより新しいソフトウェアの内容と完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="18eb1-136">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="18eb1-137">このコースでは、次のハードウェアとソフトウェアをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-137">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="18eb1-138">開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-138">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="18eb1-139">開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="18eb1-139">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="18eb1-140">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="18eb1-140">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="18eb1-141">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="18eb1-141">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="18eb1-142">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="18eb1-142">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="18eb1-143">[Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](../../../hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="18eb1-143">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](../../../hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="18eb1-144">内蔵マイク付きヘッドホンのセット (ヘッドセットにマイクとスピーカーが組み込まれていない場合)</span><span class="sxs-lookup"><span data-stu-id="18eb1-144">A set of headphones with a built-in microphone (if the headset does not have a built-in mic and speakers)</span></span>
- <span data-ttu-id="18eb1-145">Azure セットアップとデータ取得のためのインターネットアクセス Application Insights</span><span class="sxs-lookup"><span data-stu-id="18eb1-145">Internet access for Azure setup and Application Insights data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="18eb1-146">開始する前に</span><span class="sxs-lookup"><span data-stu-id="18eb1-146">Before you start</span></span>

<span data-ttu-id="18eb1-147">このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="18eb1-147">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

> [!WARNING] 
> <span data-ttu-id="18eb1-148">*Application Insights* するデータには時間がかかるため、しばらくお待ちください。</span><span class="sxs-lookup"><span data-stu-id="18eb1-148">Be aware, data going to *Application Insights* takes time, so be patient.</span></span> <span data-ttu-id="18eb1-149">サービスがデータを受信したかどうかを確認する場合は、 [14 章](#chapter-14---the-application-insights-service-portal)を参照してください。この章では、ポータル内を移動する方法を説明しています。</span><span class="sxs-lookup"><span data-stu-id="18eb1-149">If you want to check if the Service has received your data, check out [Chapter 14](#chapter-14---the-application-insights-service-portal), which will show you how to navigate the portal.</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="18eb1-150">章 1-Azure Portal</span><span class="sxs-lookup"><span data-stu-id="18eb1-150">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="18eb1-151">*Application Insights* を使用するには、Azure portal で *Application Insights サービス* を作成および構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-151">To use *Application Insights*, you will need to create and configure an *Application Insights Service* in the Azure portal.</span></span>

1.  <span data-ttu-id="18eb1-152">[Azure Portal](https://portal.azure.com) にログインします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-152">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="18eb1-153">まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-153">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="18eb1-154">このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。</span><span class="sxs-lookup"><span data-stu-id="18eb1-154">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="18eb1-155">ログインしたら、左上隅にある [ **新規** ] をクリックし、 *Application Insights* を検索して、 **Enter キー** を押します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-155">Once you are logged in, click on **New** in the top left corner, and search for *Application Insights*, and click **Enter**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="18eb1-156">新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="18eb1-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

    ![Azure portal](images/AzureLabs-Lab309-01.png)

3.  <span data-ttu-id="18eb1-158">右側の新しいページには、 *Azure アプリケーション Insights* サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-158">The new page to the right will provide a description of the *Azure Application Insights* Service.</span></span> <span data-ttu-id="18eb1-159">このページの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-159">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure portal](images/AzureLabs-Lab309-02.png)

4.  <span data-ttu-id="18eb1-161">[ **作成**:</span><span class="sxs-lookup"><span data-stu-id="18eb1-161">Once you have clicked on **Create**:</span></span>

    1.  <span data-ttu-id="18eb1-162">このサービスインスタンスに必要な **名前** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-162">Insert your desired **Name** for this Service instance.</span></span>

    2.  <span data-ttu-id="18eb1-163">**アプリケーションの種類** として [**全般**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-163">As **Application Type**, select **General**.</span></span>

    3.  <span data-ttu-id="18eb1-164">適切な **サブスクリプション** を選択します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-164">Select an appropriate **Subscription**.</span></span>

    4.  <span data-ttu-id="18eb1-165">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-165">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="18eb1-166">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-166">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="18eb1-167">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-167">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="18eb1-168">Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="18eb1-168">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5.  <span data-ttu-id="18eb1-169">**[場所]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-169">Select a **Location**.</span></span>

    6.  <span data-ttu-id="18eb1-170">また、このサービスに適用されている使用条件を理解していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-170">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="18eb1-171">**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-171">Select **Create**.</span></span>

        ![Azure portal](images/AzureLabs-Lab309-03.png)

5.  <span data-ttu-id="18eb1-173">[ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-173">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="18eb1-174">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-174">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure portal](images/AzureLabs-Lab309-04.png)

7.  <span data-ttu-id="18eb1-176">通知をクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-176">Click on the notifications to explore your new Service instance.</span></span>

    ![Azure portal](images/AzureLabs-Lab309-05.png)

8.  <span data-ttu-id="18eb1-178">通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-178">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="18eb1-179">新しい *Application Insights サービス* インスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-179">You will be taken to your new *Application Insights Service* instance.</span></span>

    ![Azure portal](images/AzureLabs-Lab309-06.png)

    > [!NOTE]
    >  <span data-ttu-id="18eb1-181">この web ページを開いたまま、簡単にアクセスできるようにします。収集されたデータを確認するために頻繁に使用します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-181">Keep this web page open and easy to access, you will come back here often to see the data collected.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="18eb1-182">Application Insights を実装するには、 **インストルメンテーションキー**、 **アプリケーション ID**、 **API キー** という3つの固有の値を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-182">To implement Application Insights, you will need to use three (3) specific values: **Instrumentation Key**, **Application ID**, and **API Key**.</span></span> <span data-ttu-id="18eb1-183">以下では、これらの値をサービスから取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-183">Below you will see how to retrieve these values from your Service.</span></span> <span data-ttu-id="18eb1-184">これらの値は、コードですぐに使用されるため、空の *メモ帳* ページでメモしておいてください。</span><span class="sxs-lookup"><span data-stu-id="18eb1-184">Make sure to note these values on a blank *Notepad* page, because you will use them soon in your code.</span></span>

9.  <span data-ttu-id="18eb1-185">**インストルメンテーションキー** を検索するには、サービス関数の一覧を下にスクロールし、[**プロパティ**] をクリックする必要があります。表示されるタブに **サービスキー** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-185">To find the **Instrumentation Key**, you will need to scroll down the list of Service functions, and click on **Properties**, the tab displayed will reveal the **Service Key**.</span></span>

    ![Azure portal](images/AzureLabs-Lab309-07.png)

10. <span data-ttu-id="18eb1-187">以下の **プロパティ** を使用すると、クリックする必要がある **API アクセス** がわかります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-187">A little below **Properties**, you will find **API Access**, which you need to click.</span></span> <span data-ttu-id="18eb1-188">右側のパネルに、アプリの **アプリケーション ID** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-188">The panel to the right will provide the **Application ID** of your app.</span></span>

    ![Azure portal](images/AzureLabs-Lab309-08.png)

11. <span data-ttu-id="18eb1-190">[ **アプリケーション ID** ] パネルを開いたまま、[ **Api キーの作成**] をクリックすると、[ *api キーの作成* ] パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-190">With the **Application ID** panel still open, click **Create API Key**, which will open the *Create API key* panel.</span></span>

    ![Azure portal](images/AzureLabs-Lab309-09.png)

12. <span data-ttu-id="18eb1-192">ここで、[ *API キーの作成* ] パネルを開き、説明を入力して、 **3 つのボックスを目盛り** します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-192">Within the now open *Create API key* panel, type a description, and **tick the three boxes**.</span></span>

13. <span data-ttu-id="18eb1-193">[ **キーの生成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-193">Click **Generate Key**.</span></span> <span data-ttu-id="18eb1-194">**API キー** が作成されて表示されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-194">Your **API Key** will be created and displayed.</span></span> 

    ![Azure portal](images/AzureLabs-Lab309-10.png)
        
    > [!WARNING]
    > <span data-ttu-id="18eb1-196">これは、 **サービスキー** が表示される唯一の時間であるため、ここでコピーを作成してください。</span><span class="sxs-lookup"><span data-stu-id="18eb1-196">This is the only time your **Service Key** will be displayed, so ensure you make a copy of it now.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="18eb1-197">Chapter 2-Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="18eb1-197">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="18eb1-198">次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="18eb1-198">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="18eb1-199">*Unity* を開き、[**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-199">Open *Unity* and click **New**.</span></span>

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-11.png)

2.  <span data-ttu-id="18eb1-201">ここで、Unity プロジェクト名を指定し、「 **MR \_ Azure \_ Application \_ Insights**」と入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-201">You will now need to provide a Unity Project name, insert **MR\_Azure\_Application\_Insights**.</span></span> <span data-ttu-id="18eb1-202">*テンプレート* が **3d** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-202">Make sure the *Template* is set to **3D**.</span></span> <span data-ttu-id="18eb1-203">場所を適切な *場所* に設定します (ルートディレクトリの方が適していることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="18eb1-203">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="18eb1-204">次に、[ **プロジェクトの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-204">Then, click **Create project**.</span></span>

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-12.png)

3.  <span data-ttu-id="18eb1-206">Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-206">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="18eb1-207">[ **\> 設定の編集** ] に移動し、新しいウィンドウで [ **外部ツール**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-207">Go to **Edit \> Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="18eb1-208">**外部スクリプトエディター** を **Visual Studio 2017** に変更します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-208">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="18eb1-209">[ **基本設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-209">Close the **Preferences** window.</span></span>

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-13.png)

4.  <span data-ttu-id="18eb1-211">次に、[**ファイル \>** ] [ビルドの設定] の順に移動し、[**プラットフォームの切り替え**] ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-211">Next, go to **File \> Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-14.png)

5.  <span data-ttu-id="18eb1-213">ファイルの **\> ビルド設定** にアクセスして、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="18eb1-213">Go to **File \> Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="18eb1-214">**ターゲットデバイス** が **任意のデバイス** に設定されています</span><span class="sxs-lookup"><span data-stu-id="18eb1-214">**Target Device** is set to **Any device**</span></span>

        > <span data-ttu-id="18eb1-215">Microsoft HoloLens の場合は、 **ターゲットデバイス** を *HoloLens* に設定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-215">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="18eb1-216">**ビルドの種類** が **D3D** に設定されています</span><span class="sxs-lookup"><span data-stu-id="18eb1-216">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="18eb1-217">**SDK** は最新の **インストール** に設定されています</span><span class="sxs-lookup"><span data-stu-id="18eb1-217">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="18eb1-218">**ビルドと実行** は **ローカルコンピューター** に設定されています</span><span class="sxs-lookup"><span data-stu-id="18eb1-218">**Build and Run** is set to **Local Machine**</span></span>

    5.  <span data-ttu-id="18eb1-219">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-219">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="18eb1-220">これを行うには、[開いている **シーンの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-220">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="18eb1-221">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-221">A save window will appear.</span></span>

            ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-15.png)

        2. <span data-ttu-id="18eb1-223">このための新しいフォルダーを作成し、その後のシーンで、[ **新しいフォルダー** ] ボタンをクリックして新しいフォルダーを作成し、その名前を「 **シーン**」にします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-223">Create a new folder for this, and any future scene, then click the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-16.png)

        3. <span data-ttu-id="18eb1-225">新しく作成した [ **シーン** ] フォルダーを開き、[ *ファイル名:* テキスト] フィールドに「 **ApplicationInsightsScene**」と入力し、[ **保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-225">Open your newly created **Scenes** folder, and then in the *File name:* text field, type **ApplicationInsightsScene**, then click **Save**.</span></span>

            ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-17.png)

6.  <span data-ttu-id="18eb1-227">それ以外の設定は、[ **ビルド設定**] の [既定] のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-227">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

7.  <span data-ttu-id="18eb1-228">[ **ビルドの設定** ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 **インスペクター** が配置されている領域の関連パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-228">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span>

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-18.png)

8. <span data-ttu-id="18eb1-230">このパネルでは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-230">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="18eb1-231">[ **その他の設定** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-231">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="18eb1-232">**Scripting** **Runtime のバージョン** は **実験的 (.net 4.6 と同等)** である必要があります。これにより、エディターを再起動する必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-232">**Scripting** **Runtime Version** should be **Experimental (.NET 4.6 Equivalent)**, which will trigger a need to restart the Editor.</span></span>

        2.  <span data-ttu-id="18eb1-233">**バックエンド** は **.net** である必要があります</span><span class="sxs-lookup"><span data-stu-id="18eb1-233">**Scripting Backend** should be **.NET**</span></span>

        3.  <span data-ttu-id="18eb1-234">**API 互換性レベル** は **.net 4.6** である必要があります</span><span class="sxs-lookup"><span data-stu-id="18eb1-234">**API Compatibility Level** should be **.NET 4.6**</span></span>

        ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-19.png)

    2.  <span data-ttu-id="18eb1-236">[ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-236">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="18eb1-237">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="18eb1-237">**InternetClient**</span></span>     

            ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-20.png)

    3.  <span data-ttu-id="18eb1-239">パネルの下にある [ **XR settings** ( **発行設定**] の下にあります) で、[ **Virtual Reality がサポートされている**] をオンにして、 **Windows Mixed reality SDK** が追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-239">Further down the panel, in **XR Settings** (found below **Publishing Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Unity プロジェクトを設定する](images/AzureLabs-Lab309-21.png)

9.  <span data-ttu-id="18eb1-241">**ビルド設定** に戻ると、 **Unity C# プロジェクト** はグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-241">Back in **Build Settings**, **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span>

10.  <span data-ttu-id="18eb1-242">[ビルド設定] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-242">Close the Build Settings window.</span></span>

11.  <span data-ttu-id="18eb1-243">シーンとプロジェクトを保存します (**ファイル**  >  **保存シーン/ファイル**  >  **保存プロジェクト**)。</span><span class="sxs-lookup"><span data-stu-id="18eb1-243">Save your Scene and Project (**FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT**).</span></span>


## <a name="chapter-3---import-the-unity-package"></a><span data-ttu-id="18eb1-244">章 3-Unity パッケージをインポートする</span><span class="sxs-lookup"><span data-stu-id="18eb1-244">Chapter 3 - Import the Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18eb1-245">このコースの *構成要素をスキップし、コード* に直接移動する場合は、この [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage)を無料でダウンロードして、 [**カスタムパッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてください。</span><span class="sxs-lookup"><span data-stu-id="18eb1-245">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to download this [Azure-MR-309.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/Azure-MR-309.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="18eb1-246">これには、次の章の Dll も含まれます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-246">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="18eb1-247">インポート後、 [**第6章**](#chapter-6---create-the-applicationinsightstracker-class)から続行します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-247">After import, continue from [**Chapter 6**](#chapter-6---create-the-applicationinsightstracker-class).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="18eb1-248">Unity 内で Application Insights を使用するには、その DLL を Newtonsoft DLL と共にインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-248">To use Application Insights within Unity, you need to import the DLL for it, along with the Newtonsoft DLL.</span></span> <span data-ttu-id="18eb1-249">現在、Unity には、インポート後にプラグインを再構成する必要がある既知の問題があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-249">There is currently a known issue in Unity which requires plugins to be  reconfigured after import.</span></span> <span data-ttu-id="18eb1-250">バグが解決された後、これらの手順 (このセクションでは 4-7) は不要になりました。</span><span class="sxs-lookup"><span data-stu-id="18eb1-250">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="18eb1-251">Application Insights を独自のプロジェクトにインポートするには、 [プラグインを含む ' unitypackage ' をダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage)していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="18eb1-251">To import Application Insights into your own project, make sure you have [downloaded the '.unitypackage', containing the plugins](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20309%20-%20Application%20insights/AppInsights_LabPlugins.unitypackage).</span></span> <span data-ttu-id="18eb1-252">次に、以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-252">Then, do the following:</span></span>

1.  <span data-ttu-id="18eb1-253">[**アセット \> インポートパッケージの \> カスタムパッケージ**] メニューオプションを使用して、 **unitypackage** を Unity に追加します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-253">Add the **.unitypackage** to Unity by using the **Assets \> Import Package \> Custom Package** menu option.</span></span>

2.  <span data-ttu-id="18eb1-254">ポップアップ表示された [ **Unity パッケージのインポート** ] ボックスで、 **プラグイン** (およびそれを含む) のすべてが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-254">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Unity パッケージのインポート](images/AzureLabs-Lab309-22.png)

3.  <span data-ttu-id="18eb1-256">[ **インポート** ] ボタンをクリックして、プロジェクトに項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-256">Click the **Import** button, to add the items to your project.</span></span>

4.  <span data-ttu-id="18eb1-257">プロジェクトビューの [**プラグイン**] の下にある [ **Insights** ] フォルダーにアクセスし、次のプラグイン *のみ* を選択します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-257">Go to the **Insights** folder under **Plugins** in the Project view and select the following plugins *only*:</span></span>

    -   <span data-ttu-id="18eb1-258">Microsoft.ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="18eb1-258">Microsoft.ApplicationInsights</span></span>

    ![Unity パッケージのインポート](images/AzureLabs-Lab309-23.png)

5.  <span data-ttu-id="18eb1-260">この *プラグイン* を選択した状態で、 **任意のプラットフォーム** が **オフ** になっていることを確認し、[ **wsaplayer** ] も **オフ** になっていることを確認して、[ **適用**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-260">With this *plugin* selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="18eb1-261">これを行うのは、ファイルが正しく構成されていることを確認することだけです。</span><span class="sxs-lookup"><span data-stu-id="18eb1-261">Doing this is just to confirm that the files are configured correctly.</span></span>

    ![Unity パッケージのインポート](images/AzureLabs-Lab309-24.png)

    > [!NOTE]
    > <span data-ttu-id="18eb1-263">このようなプラグインをマークすると、Unity エディターでのみ使用されるように構成されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-263">Marking the plugins like this, configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="18eb1-264">WSA フォルダーには、Unity からプロジェクトがエクスポートされた後に使用される、異なる Dll のセットがあります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-264">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="18eb1-265">次に、[ **Insights** ] フォルダー内の **WSA** フォルダーを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-265">Next, you need to open the **WSA** folder, within the **Insights** folder.</span></span> <span data-ttu-id="18eb1-266">先ほど構成したものと同じファイルのコピーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-266">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="18eb1-267">このファイルを選択し、インスペクターで、**すべてのプラットフォーム** が **オフ** になっていることを確認してから、[ **wsaplayer** ]**のみ** が **オン** になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-267">Select this file, and then in the inspector, ensure that **Any Platform** is **unchecked**, then ensure that **only** **WSAPlayer** is **checked**.</span></span> <span data-ttu-id="18eb1-268">**[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-268">Click **Apply**.</span></span>

    ![Unity パッケージのインポート](images/AzureLabs-Lab309-25.png)

7. <span data-ttu-id="18eb1-270">ここで、 **手順 4-6** に従う必要がありますが、代わりに *newtonsoft* プラグインの場合は、</span><span class="sxs-lookup"><span data-stu-id="18eb1-270">You will now need to follow **steps 4-6**, but for the *Newtonsoft* plugins instead.</span></span> <span data-ttu-id="18eb1-271">結果がどのように表示されるかについては、以下のスクリーンショットを参照してください。</span><span class="sxs-lookup"><span data-stu-id="18eb1-271">See the below screenshot for what the outcome should look like.</span></span>

    ![Unity パッケージのインポート](images/AzureLabs-Lab309-25-5.png)    

## <a name="chapter-4---set-up-the-camera-and-user-controls"></a><span data-ttu-id="18eb1-273">Chapter 4-カメラとユーザーコントロールを設定する</span><span class="sxs-lookup"><span data-stu-id="18eb1-273">Chapter 4 - Set up the camera and user controls</span></span>

<span data-ttu-id="18eb1-274">この章では、カメラとコントロールを設定して、ユーザーがシーン内を表示して移動できるようにします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-274">In this Chapter you will set up the camera and the controls to allow the user to see and move in the scene.</span></span>

1.  <span data-ttu-id="18eb1-275">[階層] パネルの空の領域を右クリックし、[空の **作成**] をクリックし  >  **Empty** ます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-275">Right-click in an empty area in the Hierarchy Panel, then on **Create** > **Empty**.</span></span>

    ![カメラとユーザーコントロールを設定する](images/AzureLabs-Lab309-26.png)

2.  <span data-ttu-id="18eb1-277">新しい空の作成オブジェクトの名前を **Camera Parent** に変更します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-277">Rename the new empty GameObject to **Camera Parent**.</span></span>

    ![カメラとユーザーコントロールを設定する](images/AzureLabs-Lab309-27.png)

3.  <span data-ttu-id="18eb1-279">[階層] パネルの空の領域を右クリックし、[ **3D オブジェクト**]、[ **球**] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-279">Right-click in an empty area in the Hierarchy Panel, then on **3D Object**, then on **Sphere**.</span></span>

4.  <span data-ttu-id="18eb1-280">球の名前を **右** に変更します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-280">Rename the Sphere to **Right Hand**.</span></span>

5.  <span data-ttu-id="18eb1-281">右側の **変換スケール** を **0.1、0.1、0.1** に設定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-281">Set the **Transform Scale** of the Right Hand to **0.1, 0.1, 0.1**</span></span>

    ![カメラとユーザーコントロールを設定する](images/AzureLabs-Lab309-28.png)

6.  <span data-ttu-id="18eb1-283">*球体 collider* コンポーネントの **歯車** をクリックし、[**コンポーネントの削除**] をクリックして、右側から **球の collider** コンポーネントを削除します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-283">Remove the **Sphere Collider** component from the Right Hand by clicking on the **Gear** in the *Sphere Collider* component, and then **Remove Component**.</span></span>

    ![カメラとユーザーコントロールを設定する](images/AzureLabs-Lab309-29.png)

7.  <span data-ttu-id="18eb1-285">[階層] パネルで、 **メインカメラ** と **右側** のオブジェクトをカメラの **親** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-285">In the Hierarchy Panel drag the **Main Camera** and the **Right Hand** objects onto the **Camera Parent** object.</span></span>

    ![カメラとユーザーコントロールを設定する](images/AzureLabs-Lab309-30.png)

8.  <span data-ttu-id="18eb1-287">**メインカメラ** と **右側** のオブジェクトの両方の **変換位置** を **0、0、0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-287">Set the **Transform Position** of both the **Main Camera** and the **Right Hand** object to **0, 0, 0**.</span></span>

    ![カメラとユーザーコントロールを設定する](images/AzureLabs-Lab309-31.png)

    ![カメラとユーザーコントロールを設定する](images/AzureLabs-Lab309-32.png)

## <a name="chapter-5---set-up-the-objects-in-the-unity-scene"></a><span data-ttu-id="18eb1-290">章 5-Unity シーンでのオブジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="18eb1-290">Chapter 5 - Set up the objects in the Unity scene</span></span>

<span data-ttu-id="18eb1-291">ここで、ユーザーが対話できるシーンの基本図形をいくつか作成します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-291">You will now create some basic shapes for your scene, with which the user can interact.</span></span>

1.  <span data-ttu-id="18eb1-292">[ *階層] パネル* の空の領域を右クリックし、[ **3d オブジェクト**] で [ **平面**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-292">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object**, then select **Plane**.</span></span>

2.  <span data-ttu-id="18eb1-293">平面の **変換位置** を **0、-1、0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-293">Set the Plane **Transform Position** to **0, -1, 0**.</span></span>

3.  <span data-ttu-id="18eb1-294">平面の **変換スケール** を **5、1、5** に設定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-294">Set the Plane **Transform Scale** to **5, 1, 5**.</span></span>

    ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-33.png)

4.  <span data-ttu-id="18eb1-296">**平面** オブジェクトと共に使用する基本的な素材を作成して、他の図形が見やすくなるようにします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-296">Create a basic material to use with your **Plane** object, so that the other shapes are easier to see.</span></span> <span data-ttu-id="18eb1-297">*プロジェクトパネル* に移動し、を右クリックして、[**作成**] をクリックします。次に **フォルダー** を作成し、新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-297">Navigate to your *Project Panel*, right-click, then **Create**, followed by **Folder**, to create a new folder.</span></span> <span data-ttu-id="18eb1-298">名前を「 **マテリアル**」にします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-298">Name it **Materials**.</span></span>

    ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-34.png) ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-35.png)

5.  <span data-ttu-id="18eb1-301">[ **素材** ] フォルダーを開き、右クリックして [ **作成**]、[ **素材**] の順にクリックし、新しい素材を作成します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-301">Open the **Materials** folder, then right-click, click **Create**, then **Material**, to create a new material.</span></span> <span data-ttu-id="18eb1-302">**Blue** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-302">Name it **Blue**.</span></span>

    ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-36.png) ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-37.png)

6.  <span data-ttu-id="18eb1-305">新しい **青色** のマテリアルを選択した状態で、 *インスペクター* を見て、[ **albedo**] の横にある四角形のウィンドウをクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-305">With the new **Blue** material selected, look at the *Inspector*, and click the rectangular window alongside **Albedo**.</span></span> <span data-ttu-id="18eb1-306">青い色を選択します (下の画像は、 **16 進数の色: \# 3592ffff**)。</span><span class="sxs-lookup"><span data-stu-id="18eb1-306">Select a blue color (the one picture below is **Hex Color: \#3592FFFF**).</span></span> <span data-ttu-id="18eb1-307">選択したら、[閉じる] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-307">Click the close button once you have chosen.</span></span>

    ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-38.png)

7.  <span data-ttu-id="18eb1-309">新しい素材を [**マテリアル**] フォルダーから、新しく作成した **平面** のシーンにドラッグします (または、*階層* 内の [**平面**] オブジェクトにドロップします)。</span><span class="sxs-lookup"><span data-stu-id="18eb1-309">Drag your new material from the **Materials** folder, onto your newly created **Plane**, within your scene (or drop it on the **Plane** object within the *Hierarchy*).</span></span>

    ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-39.png)

8.  <span data-ttu-id="18eb1-311">[ *階層] パネル* の空の領域を右クリックし、[ **3d オブジェクト]** の [カプセル] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-311">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Capsule**.</span></span>

    -  <span data-ttu-id="18eb1-312">**カプセル** を選択した状態で、\**変換\*\*\*位置* を **-10、1、0** に変更します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-312">With the **Capsule** selected, change its **Transform** *Position* to: **-10, 1, 0**.</span></span>

9.  <span data-ttu-id="18eb1-313">[ *階層] パネル* の空の領域を右クリックし、[ **3d オブジェクト]** の [キューブ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-313">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Cube**.</span></span>

    -  <span data-ttu-id="18eb1-314">**キューブ** を選択した状態で、\**変換\*\*\*位置* を **0、0、10** に変更します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-314">With the **Cube** selected, change its **Transform** *Position* to: **0, 0, 10**.</span></span>

10. <span data-ttu-id="18eb1-315">[ *階層] パネル* の空の領域を右クリックし、[ **3d オブジェクト]、[球**] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-315">Right-click in an empty area in the *Hierarchy Panel*, then on **3D Object, Sphere**.</span></span>

    -  <span data-ttu-id="18eb1-316">**球** を選択した状態で、\**変換\*\*\*位置* を **10、0、0** に変更します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-316">With the **Sphere** selected, change its **Transform** *Position* to: **10, 0, 0**.</span></span>

    ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-40.png)

    > [!NOTE]
    > <span data-ttu-id="18eb1-318">これらの *位置* の値は *提案* です。</span><span class="sxs-lookup"><span data-stu-id="18eb1-318">These *Position* values are *suggestions*.</span></span> <span data-ttu-id="18eb1-319">オブジェクトの位置は自由に設定できますが、オブジェクトの距離がカメラから遠く離れていない場合は、アプリケーションのユーザーにとっても簡単です。</span><span class="sxs-lookup"><span data-stu-id="18eb1-319">You are free to set the positions of the objects to whatever you would like, though it is easier for the user of the application if the objects distances are not too far from the camera.</span></span>

11. <span data-ttu-id="18eb1-320">アプリケーションが実行されている場合は、シーン内のオブジェクトを識別できる必要があります。これを実現するには、そのオブジェクトにタグを付ける必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-320">When your application is running, it needs to be able to identify the objects within the scene, to achieve this, they need to be tagged.</span></span> <span data-ttu-id="18eb1-321">オブジェクトの1つを選択し、[ *インスペクター* ] パネルで [ **タグの追加...**] をクリックします。これにより、 *インスペクター* と **タグ & レイヤー** パネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-321">Select one of the objects, and in the *Inspector* panel, click **Add Tag...**, which will swap the *Inspector* with the **Tags & Layers** panel.</span></span>

    <span data-ttu-id="18eb1-322">![Unity シーン ](images/AzureLabs-Lab309-41.png) でのオブジェクトの設定 ![](images/AzureLabs-Lab309-42.png)</span><span class="sxs-lookup"><span data-stu-id="18eb1-322">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-41.png) ![](images/AzureLabs-Lab309-42.png)</span></span>

12. <span data-ttu-id="18eb1-323">[+] 記号 **(プラス記号)** をクリックし、タグ名を「テキスト」 **として** 入力します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-323">Click the **+ (plus)** symbol, then type the tag name as **ObjectInScene**.</span></span>

    ![Unity シーンでのオブジェクトの設定](images/AzureLabs-Lab309-43.png)

    > [!WARNING]
    > <span data-ttu-id="18eb1-325">タグに別の名前を使用する場合は、シーン内でオブジェクトが検出され、検出されるように、この変更によって *DataFromAnalytics*、 *Objecttrigger*、および *宝石* のスクリプトも後で作成されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-325">If you use a different name for your tag, you will need to ensure this change is also made the *DataFromAnalytics*, *ObjectTrigger*, and *Gaze*, scripts later, so that your objects are found, and detected, within your scene.</span></span>

13. <span data-ttu-id="18eb1-326">タグを作成したら、3つのオブジェクトすべてに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-326">With the tag created, you now need to apply it to all three of your objects.</span></span> <span data-ttu-id="18eb1-327">*階層* から、 **shift** キーを押したまま、[**カプセル**]、[**キューブ**]、[**球**] のオブジェクトをクリックし、次に [*インスペクター*] の下にあるドロップダウン **メニューをクリック** します。次に、作成 *したオブジェクト* をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-327">From the *Hierarchy*, hold the **Shift** key, then click the **Capsule**, **Cube**, and **Sphere**, objects, then in the *Inspector*, click the dropdown menu alongside **Tag**, then click the *ObjectInScene* tag you created.</span></span>

    <span data-ttu-id="18eb1-328">![Unity シーン ](images/AzureLabs-Lab309-44.png) でのオブジェクトの設定 ![](images/AzureLabs-Lab309-45.png)</span><span class="sxs-lookup"><span data-stu-id="18eb1-328">![Set up the objects in the Unity Scene](images/AzureLabs-Lab309-44.png) ![](images/AzureLabs-Lab309-45.png)</span></span>

## <a name="chapter-6---create-the-applicationinsightstracker-class"></a><span data-ttu-id="18eb1-329">Chapter 6-ApplicationInsightsTracker クラスの作成</span><span class="sxs-lookup"><span data-stu-id="18eb1-329">Chapter 6 - Create the ApplicationInsightsTracker class</span></span>

<span data-ttu-id="18eb1-330">作成する必要のある最初のスクリプトは **ApplicationInsightsTracker** です。これは次の役割を担います。</span><span class="sxs-lookup"><span data-stu-id="18eb1-330">The first script you need to create is **ApplicationInsightsTracker**, which is responsible for:</span></span>

1.  <span data-ttu-id="18eb1-331">ユーザーの操作に基づいてイベントを作成し、Azure アプリケーション Insights に送信します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-331">Creating events based on user interactions to submit to Azure Application Insights.</span></span>

2. <span data-ttu-id="18eb1-332">ユーザーの操作に応じて、適切なイベント名を作成します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-332">Creating appropriate Event names, depending on user interaction.</span></span>

3. <span data-ttu-id="18eb1-333">Application Insights サービスインスタンスにイベントを送信しています。</span><span class="sxs-lookup"><span data-stu-id="18eb1-333">Submitting events to the Application Insights Service instance.</span></span>

<span data-ttu-id="18eb1-334">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="18eb1-334">To create this class:</span></span>

1.  <span data-ttu-id="18eb1-335">[*プロジェクト] パネル* 内を右クリックし、[フォルダーの **作成**] をクリックし  >  **Folder** ます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-335">Right-click in the *Project Panel*, then **Create** > **Folder**.</span></span> <span data-ttu-id="18eb1-336">フォルダーに **スクリプト** の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-336">Name the folder **Scripts**.</span></span>

    ![ApplicationInsightsTracker クラスを作成する](images/AzureLabs-Lab309-46.png)  ![ApplicationInsightsTracker クラスを作成する](images/AzureLabs-Lab309-47.png)

2.  <span data-ttu-id="18eb1-339">**Scripts** フォルダーを作成したら、それをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-339">With the **Scripts** folder created, double-click it, to open.</span></span> <span data-ttu-id="18eb1-340">次に、そのフォルダー内で右クリックし **Create**、[  >  **C# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-340">Then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="18eb1-341">スクリプトに **ApplicationInsightsTracker** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-341">Name the script **ApplicationInsightsTracker**.</span></span>

3.  <span data-ttu-id="18eb1-342">新しい **ApplicationInsightsTracker** スクリプトをダブルクリックして、 **Visual Studio** で開きます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-342">Double-click on the new **ApplicationInsightsTracker** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="18eb1-343">スクリプトの先頭にある名前空間を次のように更新します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-343">Update namespaces at the top of the script to be as below:</span></span>

    ```csharp
        using Microsoft.ApplicationInsights;
        using Microsoft.ApplicationInsights.DataContracts;
        using Microsoft.ApplicationInsights.Extensibility;
        using UnityEngine;
    ```

5.  <span data-ttu-id="18eb1-344">クラス内で、次の変数を挿入します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-344">Inside the class insert the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behavior like a singleton
        /// </summary>
        public static ApplicationInsightsTracker Instance;
        
        /// <summary>
        /// Insert your Instrumentation Key here
        /// </summary>
        internal string instrumentationKey = "Insert Instrumentation Key here";

        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        internal string applicationId = "Insert Application Id here";

        /// <summary>
        /// Insert your API Key here
        /// </summary>
        internal string API_Key = "Insert API Key here";

        /// <summary>
        /// Represent the Analytic Custom Event object
        /// </summary>
        private TelemetryClient telemetryClient;

        /// <summary>
        /// Represent the Analytic object able to host gaze duration
        /// </summary>
        private MetricTelemetry metric;
    ```

    > [!NOTE] 
    > <span data-ttu-id="18eb1-345">手順9の [章](#chapter-1---the-azure-portal)で説明したように、Azure Portal の *サービスキー* を使用して、 **instrumentationKey、applicationId、API_Key** の値を適切に設定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-345">Set the **instrumentationKey, applicationId and API_Key** values appropriately, using the *Service Keys* from the Azure Portal as mentioned in [Chapter 1](#chapter-1---the-azure-portal), step 9 onwards.</span></span>

6.  <span data-ttu-id="18eb1-346">次に、クラスが初期化されるときに呼び出される **Start ()** メソッドと起動前 **()** メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-346">Then add the **Start()** and **Awake()** methods, which will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Sets this class instance as a singleton
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Use this for initialization
        /// </summary>
        void Start()
        {
            // Instantiate telemetry and metric
            telemetryClient = new TelemetryClient();

            metric = new MetricTelemetry();

            // Assign the Instrumentation Key to the Event and Metric objects
            TelemetryConfiguration.Active.InstrumentationKey = instrumentationKey;

            telemetryClient.InstrumentationKey = instrumentationKey;
        }
    ```

7.  <span data-ttu-id="18eb1-347">アプリケーションによって登録されたイベントとメトリックの送信を担当するメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-347">Add the methods responsible for sending the events and metrics registered by your application:</span></span>

    ```csharp
        /// <summary>
        /// Submit the Event to Azure Analytics using the event trigger object
        /// </summary>
        public void RecordProximityEvent(string objectName)
        {
            telemetryClient.TrackEvent(CreateEventName(objectName));
        }

        /// <summary>
        /// Uses the name of the object involved in the event to create 
        /// and return an Event Name convention
        /// </summary>
        public string CreateEventName(string name)
        {
            string eventName = $"User near {name}";
            return eventName;
        }

        /// <summary>
        /// Submit a Metric to Azure Analytics using the metric gazed object
        /// and the time count of the gaze
        /// </summary>
        public void RecordGazeMetrics(string objectName, int time)
        {
            // Output Console information about gaze.
            Debug.Log($"Finished gazing at {objectName}, which went for <b>{time}</b> second{(time != 1 ? "s" : "")}");

            metric.Name = $"Gazed {objectName}";

            metric.Value = time;

            telemetryClient.TrackMetric(metric);
        }
    ```

8.  <span data-ttu-id="18eb1-348">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="18eb1-348">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-7---create-the-gaze-script"></a><span data-ttu-id="18eb1-349">第7章-宝石のスクリプトを作成する</span><span class="sxs-lookup"><span data-stu-id="18eb1-349">Chapter 7 - Create the Gaze script</span></span>

<span data-ttu-id="18eb1-350">次に作成するスクリプトは、 **見つめ** スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="18eb1-350">The next script to create is the **Gaze** script.</span></span> <span data-ttu-id="18eb1-351">このスクリプトは、ユーザーがどのオブジェクトを調べているかを検出するために、*メインカメラ* から投影される *Raycast* を作成する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="18eb1-351">This script is responsible for creating a *Raycast* that will be projected forward from the *Main Camera*, to detect which object the user is looking at.</span></span> <span data-ttu-id="18eb1-352">この場合、 *Raycast* は、ユーザーがオブジェクトでオブジェクトを見ているかどうかを特定 **し、その** オブジェクトに対するユーザーの *gazes* 時間をカウントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-352">In this case, the *Raycast* will need to identify if the user is looking at an object with the **ObjectInScene** tag, and then count how long the user *gazes* at that object.</span></span>

1.  <span data-ttu-id="18eb1-353">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-353">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="18eb1-354">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-354">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="18eb1-355">スクリプトに「」という名前を **指定します**。</span><span class="sxs-lookup"><span data-stu-id="18eb1-355">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="18eb1-356">スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-356">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="18eb1-357">既存のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-357">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {
            /// <summary>
            /// Provides Singleton-like behavior to this class.
            /// </summary>
            public static Gaze Instance;

            /// <summary>
            /// Provides a reference to the object the user is currently looking at.
            /// </summary>
            public GameObject FocusedGameObject { get; private set; }

            /// <summary>
            /// Provides whether an object has been successfully hit by the raycast.
            /// </summary>
            public bool Hit { get; private set; }

            /// <summary>
            /// Provides a reference to compare whether the user is still looking at 
            /// the same object (and has not looked away).
            /// </summary>
            private GameObject _oldFocusedObject = null;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeMaxDistance = 300;

            /// <summary>
            /// Max Ray Distance
            /// </summary>
            private float _gazeTimeCounter = 0;

            /// <summary>
            /// The cursor object will be created when the app is running,
            /// this will store its values. 
            /// </summary>
            private GameObject _cursor;
        }
    ```

5.  <span data-ttu-id="18eb1-358">起動可能な **()** メソッドと **Start ()** メソッドのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-358">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton
            Instance = this;
            _cursor = CreateCursor();
        }

        void Start()
        {
            FocusedGameObject = null;
        }

        /// <summary>
        /// Create a cursor object, to provide what the user
        /// is looking at.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()    
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            // Remove the collider, so it does not block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());

            newCursor.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            newCursor.GetComponent<MeshRenderer>().material.color = 
            Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

            newCursor.SetActive(false);
            return newCursor;
        }
    ```

6.  <span data-ttu-id="18eb1-359">**見つめ** クラス内で、 **Update ()** メソッドに次のコードを追加して *Raycast* を射影し、ターゲットのヒットを検出します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-359">Inside the **Gaze** class, add the following code in the **Update()** method to project a *Raycast* and detect the target hit:</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        void Update()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedGameObject;

            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, _gazeMaxDistance);

            // Check whether raycast has hit.
            if (Hit == true)
            {
                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedGameObject = hitInfo.collider.gameObject;

                    // Lerp the cursor to the hit point, which helps to stabilize the gaze.
                    _cursor.transform.position = Vector3.Lerp(_cursor.transform.position, hitInfo.point, 0.6f);

                    _cursor.SetActive(true);
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedGameObject = null;

                    _cursor.SetActive(false);
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;

                _cursor.SetActive(false);
            }

            // Check whether the previous focused object is this same object. If so, reset the focused object.
            if (FocusedGameObject != _oldFocusedObject)
            {
                ResetFocusedObject();
            }
            // If they are the same, but are null, reset the counter. 
            else if (FocusedGameObject == null && _oldFocusedObject == null)
            {
                _gazeTimeCounter = 0;
            }
            // Count whilst the user continues looking at the same object.
            else
            {
                _gazeTimeCounter += Time.deltaTime;
            }
        }
    ```

7.  <span data-ttu-id="18eb1-360">**ResetFocusedObject ()** メソッドを追加して、ユーザーがオブジェクトを参照したときに **Application Insights** にデータを送信します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-360">Add the **ResetFocusedObject()** method, to send data to **Application Insights** when the user has looked at an object.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        public void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                // Only looking for objects with the correct tag.
                if (_oldFocusedObject.CompareTag("ObjectInScene"))
                {
                    // Turn the timer into an int, and ensure that more than zero time has passed.
                    int gazeAsInt = (int)_gazeTimeCounter;

                    if (gazeAsInt > 0)
                    {
                        //Record the object gazed and duration of gaze for Analytics
                        ApplicationInsightsTracker.Instance.RecordGazeMetrics(_oldFocusedObject.name, gazeAsInt);
                    }
                    //Reset timer
                    _gazeTimeCounter = 0;
                }
            }
        }
    ```

8.  <span data-ttu-id="18eb1-361">これで、 **宝石** スクリプトが完成しました。</span><span class="sxs-lookup"><span data-stu-id="18eb1-361">You have now completed the **Gaze** script.</span></span> <span data-ttu-id="18eb1-362">*Unity* に戻る前に、変更を *Visual Studio* に保存します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-362">Save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8---create-the-objecttrigger-class"></a><span data-ttu-id="18eb1-363">章 8-ObjectTrigger クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="18eb1-363">Chapter 8 - Create the ObjectTrigger class</span></span>

<span data-ttu-id="18eb1-364">次のスクリプトを作成する必要があります。 **Objecttrigger** は次の役割を担います。</span><span class="sxs-lookup"><span data-stu-id="18eb1-364">The next script you need to create is **ObjectTrigger**, which is responsible for:</span></span>

- <span data-ttu-id="18eb1-365">メインカメラとの競合に必要なコンポーネントを追加します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-365">Adding components needed for collision to the Main Camera.</span></span>
- <span data-ttu-id="18eb1-366">カメラがオブジェクトの近くにあるかどうか **を検出** しています。</span><span class="sxs-lookup"><span data-stu-id="18eb1-366">Detecting if the camera is near an object tagged as **ObjectInScene**.</span></span>

<span data-ttu-id="18eb1-367">スクリプトを作成するには:</span><span class="sxs-lookup"><span data-stu-id="18eb1-367">To create the script:</span></span>

1.  <span data-ttu-id="18eb1-368">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-368">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="18eb1-369">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-369">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="18eb1-370">スクリプト **Objecttrigger** にという名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-370">Name the script **ObjectTrigger**.</span></span>

3.  <span data-ttu-id="18eb1-371">スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-371">Double-click on the script to open it with Visual Studio.</span></span> <span data-ttu-id="18eb1-372">既存のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-372">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;

        public class ObjectTrigger : MonoBehaviour
        {
            private void Start()
            {
                // Add the Collider and Rigidbody components, 
                // and set their respective settings. This allows for collision.
                gameObject.AddComponent<SphereCollider>().radius = 1.5f;

                gameObject.AddComponent<Rigidbody>().useGravity = false;
            }

            /// <summary>
            /// Triggered when an object with a collider enters this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionEnter(Collision collision)
            {
                CompareTriggerEvent(collision, true);
            }

            /// <summary>
            /// Triggered when an object with a collider exits this objects trigger collider.
            /// </summary>
            /// <param name="collision">Collided object</param>
            private void OnCollisionExit(Collision collision)
            {
                CompareTriggerEvent(collision, false);
            }

            /// <summary>
            /// Method for providing debug message, and sending event information to InsightsTracker.
            /// </summary>
            /// <param name="other">Collided object</param>
            /// <param name="enter">Enter = true, Exit = False</param>
            private void CompareTriggerEvent(Collision other, bool enter)
            {
                if (other.collider.CompareTag("ObjectInScene"))
                {
                    string message = $"User is{(enter == true ? " " : " no longer ")}near <b>{other.gameObject.name}</b>";

                    if (enter == true)
                    {
                        ApplicationInsightsTracker.Instance.RecordProximityEvent(other.gameObject.name);
                    }
                    Debug.Log(message);
                }
            }
        }
    ```

4.  <span data-ttu-id="18eb1-373">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="18eb1-373">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9---create-the-datafromanalytics-class"></a><span data-ttu-id="18eb1-374">第9章-DataFromAnalytics クラスの作成</span><span class="sxs-lookup"><span data-stu-id="18eb1-374">Chapter 9 - Create the DataFromAnalytics class</span></span>

<span data-ttu-id="18eb1-375">次の役割を果たす **DataFromAnalytics** スクリプトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-375">You will now need to create the **DataFromAnalytics** script, which is responsible for:</span></span>

- <span data-ttu-id="18eb1-376">カメラによって最もよく使用されているオブジェクトに関する分析データをフェッチしています。</span><span class="sxs-lookup"><span data-stu-id="18eb1-376">Fetching analytics data about which object has been approached by the camera the most.</span></span>
- <span data-ttu-id="18eb1-377">*サービスキー* を使用して、Azure アプリケーション Insights サービスインスタンスと通信できるようにします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-377">Using the *Service Keys*, that allow communication with your Azure Application Insights Service instance.</span></span>
- <span data-ttu-id="18eb1-378">イベント数が最も多いに従って、シーン内のオブジェクトを並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-378">Sorting the objects in scene, according to which has the highest event count.</span></span>
- <span data-ttu-id="18eb1-379">最も近づいたオブジェクトのマテリアルの色を *緑色* に変更します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-379">Changing the material color, of the most approached object, to *green*.</span></span>

<span data-ttu-id="18eb1-380">スクリプトを作成するには:</span><span class="sxs-lookup"><span data-stu-id="18eb1-380">To create the script:</span></span>

1.  <span data-ttu-id="18eb1-381">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-381">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="18eb1-382">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-382">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="18eb1-383">スクリプトに **DataFromAnalytics** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-383">Name the script **DataFromAnalytics**.</span></span>

3.  <span data-ttu-id="18eb1-384">スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-384">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="18eb1-385">次の名前空間を挿入します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-385">Insert the following namespaces:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="18eb1-386">スクリプト内に次の内容を挿入します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-386">Inside the script, insert the following:</span></span>

    ```csharp
        /// <summary>
        /// Number of most recent events to be queried
        /// </summary>
        private int _quantityOfEventsQueried = 10;

        /// <summary>
        /// The timespan with which to query. Needs to be in hours.
        /// </summary>
        private int _timepspanAsHours = 24;

        /// <summary>
        /// A list of the objects in the scene
        /// </summary>
        private List<GameObject> _listOfGameObjectsInScene;

        /// <summary>
        /// Number of queries which have returned, after being sent.
        /// </summary>
        private int _queriesReturned = 0;

        /// <summary>
        /// List of GameObjects, as the Key, with their event count, as the Value.
        /// </summary>
        private List<KeyValuePair<GameObject, int>> _pairedObjectsWithEventCount = new List<KeyValuePair<GameObject, int>>();

        // Use this for initialization
        void Start()
        {
            // Find all objects in scene which have the ObjectInScene tag (as there may be other GameObjects in the scene which you do not want).
            _listOfGameObjectsInScene = GameObject.FindGameObjectsWithTag("ObjectInScene").ToList();

            FetchAnalytics();
        }
    ```

6.  <span data-ttu-id="18eb1-387">**DataFromAnalytics** クラス内で、 **Start ()** メソッドの直後に、 **fetchanalytics ()** という次のメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-387">Within the **DataFromAnalytics** class, right after the **Start()** method, add the following method called **FetchAnalytics()**.</span></span> <span data-ttu-id="18eb1-388">このメソッドは、キーと値のペアのリストを作成します。これには、設定 *オブジェクト* とプレースホルダーイベント数を指定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-388">This method is responsible for populating the list of key value pairs, with a *GameObject* and a placeholder event count number.</span></span> <span data-ttu-id="18eb1-389">次に、 **Getwebrequest ()** コルーチンを初期化します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-389">It then initializes the **GetWebRequest()** coroutine.</span></span> <span data-ttu-id="18eb1-390">*Application Insights* の呼び出しのクエリ構造は、*クエリ URL* エンドポイントとしてもこのメソッド内にあります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-390">The query structure of the call to *Application Insights* can be found within this method also, as the *Query URL* endpoint.</span></span>

    ```csharp
        private void FetchAnalytics()
        {
            // Iterate through the objects in the list
            for (int i = 0; i < _listOfGameObjectsInScene.Count; i++)
            {
                // The current event number is not known, so set it to zero.
                int eventCount = 0;

                // Add new pair to list, as placeholder, until eventCount is known.
                _pairedObjectsWithEventCount.Add(new KeyValuePair<GameObject, int>(_listOfGameObjectsInScene[i], eventCount));

                // Set the renderer of the object to the default color, white
                _listOfGameObjectsInScene[i].GetComponent<Renderer>().material.color = Color.white;

                // Create the appropriate object name using Insights structure
                string objectName = _listOfGameObjectsInScene[i].name;
 
                // Build the queryUrl for this object.
                string queryUrl = Uri.EscapeUriString(string.Format(
                    "https://api.applicationinsights.io/v1/apps/{0}/events/$all?timespan=PT{1}H&$search={2}&$select=customMetric/name&$top={3}&$count=true",
                    ApplicationInsightsTracker.Instance.applicationId, _timepspanAsHours, "Gazed " + objectName, _quantityOfEventsQueried));


                // Send this object away within the WebRequest Coroutine, to determine it is event count.
                StartCoroutine("GetWebRequest", new KeyValuePair<string, int>(queryUrl, i));
            }
        }
    ```

7.  <span data-ttu-id="18eb1-391">**Fetchanalytics ()** メソッドのすぐ下に、 *IEnumerator* を返す **getwebrequest ()** というメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-391">Right below the **FetchAnalytics()** method, add a method called **GetWebRequest()**, which returns an *IEnumerator*.</span></span> <span data-ttu-id="18eb1-392">このメソッドは、特定の *オブジェクト* に対応するイベントが *Application Insights* 内で呼び出された回数を要求します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-392">This method is responsible for requesting the number of times an event, corresponding with a specific *GameObject*, has been called within *Application Insights*.</span></span> <span data-ttu-id="18eb1-393">送信されたすべてのクエリが返されると、決定 **E勝者 ()** メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-393">When all the sent queries have returned, the **DetermineWinner()** method is called.</span></span>

    ```csharp
        /// <summary>
        /// Requests the data count for number of events, according to the
        /// input query URL.
        /// </summary>
        /// <param name="webQueryPair">Query URL and the list number count.</param>
        /// <returns></returns>
        private IEnumerator GetWebRequest(KeyValuePair<string, int> webQueryPair)
        {
            // Set the URL and count as their own variables (for readability).
            string url = webQueryPair.Key;
            int currentCount = webQueryPair.Value;

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(url))
            {
                DownloadHandlerBuffer handlerBuffer = new DownloadHandlerBuffer();

                unityWebRequest.downloadHandler = handlerBuffer;

                unityWebRequest.SetRequestHeader("host", "api.applicationinsights.io");

                unityWebRequest.SetRequestHeader("x-api-key", ApplicationInsightsTracker.Instance.API_Key);

                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError)
                {
                    // Failure with web request.
                    Debug.Log("<color=red>Error Sending:</color> " + unityWebRequest.error);
                }
                else
                {
                    // This query has returned, so add to the current count.
                    _queriesReturned++;

                    // Initialize event count integer.
                    int eventCount = 0;

                    // Deserialize the response with the custom Analytics class.
                    Analytics welcome = JsonConvert.DeserializeObject<Analytics>(unityWebRequest.downloadHandler.text);

                    // Get and return the count for the Event
                    if (int.TryParse(welcome.OdataCount, out eventCount) == false)
                    {
                        // Parsing failed. Can sometimes mean that the Query URL was incorrect.
                        Debug.Log("<color=red>Failure to Parse Data Results. Check Query URL for issues.</color>");
                    }
                    else
                    {
                        // Overwrite the current pair, with its actual values, now that the event count is known.
                        _pairedObjectsWithEventCount[currentCount] = new KeyValuePair<GameObject, int>(_pairedObjectsWithEventCount[currentCount].Key, eventCount);
                    }

                    // If all queries (compared with the number which was sent away) have 
                    // returned, then run the determine winner method. 
                    if (_queriesReturned == _pairedObjectsWithEventCount.Count)
                    {
                        DetermineWinner();
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="18eb1-394">次のメソッドは、最も高いイベント数に従って、判別 *オブジェクト* と *Int* のペアのリストを並べ替える、決定 **e勝者 ()** です。</span><span class="sxs-lookup"><span data-stu-id="18eb1-394">The next method is **DetermineWinner()**, which sorts the list of *GameObject* and *Int* pairs, according to the highest event count.</span></span> <span data-ttu-id="18eb1-395">次に、その *オブジェクト* の素材の色を *緑色* に変更します (最大カウントがあることに関するフィードバックとして)。</span><span class="sxs-lookup"><span data-stu-id="18eb1-395">It then changes the material color of that *GameObject* to *green* (as feedback for it having the highest count).</span></span> <span data-ttu-id="18eb1-396">これにより、分析結果を含むメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-396">This displays a message with the analytics results.</span></span>

    ```csharp
        /// <summary>
        /// Call to determine the keyValue pair, within the objects list, 
        /// with the highest event count.
        /// </summary>
        private void DetermineWinner()
        {
            // Sort the values within the list of pairs.
            _pairedObjectsWithEventCount.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Change its colour to green
            _pairedObjectsWithEventCount.First().Key.GetComponent<Renderer>().material.color = Color.green;

            // Provide the winner, and other results, within the console window. 
            string message = $"<b>Analytics Results:</b>\n " +
                $"<i>{_pairedObjectsWithEventCount.First().Key.name}</i> has the highest event count, " +
                $"with <i>{_pairedObjectsWithEventCount.First().Value.ToString()}</i>.\nFollowed by: ";

            for (int i = 1; i < _pairedObjectsWithEventCount.Count; i++)
            {
                message += $"{_pairedObjectsWithEventCount[i].Key.name}, " +
                    $"with {_pairedObjectsWithEventCount[i].Value.ToString()} events.\n";
            }

            Debug.Log(message);
        }
    ```

9.  <span data-ttu-id="18eb1-397">*Application Insights* から受信した JSON オブジェクトを逆シリアル化するために使用されるクラス構造を追加します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-397">Add the class structure which will be used to deserialize the JSON object, received from *Application Insights*.</span></span> <span data-ttu-id="18eb1-398">これらのクラスは、クラス定義の **外部** にある **DataFromAnalytics** クラスファイルの一番下に追加します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-398">Add these classes at the very bottom of your **DataFromAnalytics** class file, **outside** of the class definition.</span></span>

    ```csharp
        /// <summary>
        /// These classes represent the structure of the JSON response from Azure Insight
        /// </summary>
        [Serializable]
        public class Analytics
        {
            [JsonProperty("@odata.context")]
            public string OdataContext { get; set; }

            [JsonProperty("@odata.count")]
            public string OdataCount { get; set; }

            [JsonProperty("value")]
            public Value[] Value { get; set; }
        }

        [Serializable]
        public class Value
        {
            [JsonProperty("customMetric")]
            public CustomMetric CustomMetric { get; set; }
        }

        [Serializable]
        public class CustomMetric
        {
            [JsonProperty("name")]
            public string Name { get; set; }
        }
    ```

10. <span data-ttu-id="18eb1-399">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="18eb1-399">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10---create-the-movement-class"></a><span data-ttu-id="18eb1-400">Chapter 10-移動クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="18eb1-400">Chapter 10 - Create the Movement class</span></span>

<span data-ttu-id="18eb1-401">**移動** スクリプトは、次に作成する必要があるスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="18eb1-401">The **Movement** script is the next script you will need to create.</span></span> <span data-ttu-id="18eb1-402">以下の処理を担当します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-402">It is responsible for:</span></span>

- <span data-ttu-id="18eb1-403">カメラが見ている方向に従って、メインカメラを移動します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-403">Moving the Main Camera according to the direction the camera is looking towards.</span></span>
- <span data-ttu-id="18eb1-404">シーンオブジェクトに他のすべてのスクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-404">Adding all other scripts to scene objects.</span></span>

<span data-ttu-id="18eb1-405">スクリプトを作成するには:</span><span class="sxs-lookup"><span data-stu-id="18eb1-405">To create the script:</span></span>

1.  <span data-ttu-id="18eb1-406">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-406">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="18eb1-407">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-407">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="18eb1-408">スクリプトの **移動** に名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-408">Name the script **Movement**.</span></span>

3.  <span data-ttu-id="18eb1-409">スクリプトをダブルクリックして、 *Visual Studio* で開きます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-409">Double-click on the script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="18eb1-410">既存のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-410">Replace the existing code with the following:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;

        public class Movement : MonoBehaviour
        {
            /// <summary>
            /// The rendered object representing the right controller.
            /// </summary>
            public GameObject Controller;

            /// <summary>
            /// The movement speed of the user.
            /// </summary>
            public float UserSpeed;

            /// <summary>
            /// Provides whether source updates have been registered.
            /// </summary>
            private bool _isAttached = false;

            /// <summary>
            /// The chosen controller hand to use. 
            /// </summary>
            private InteractionSourceHandedness _handness = InteractionSourceHandedness.Right;

            /// <summary>
            /// Used to calculate and proposes movement translation.
            /// </summary>
            private Vector3 _playerMovementTranslation;

            private void Start()
            {
                // You are now adding components dynamically 
                // to ensure they are existing on the correct object  

                // Add all camera related scripts to the camera. 
                Camera.main.gameObject.AddComponent<Gaze>();
                Camera.main.gameObject.AddComponent<ObjectTrigger>();
        
                // Add all other scripts to this object.
                gameObject.AddComponent<ApplicationInsightsTracker>();
                gameObject.AddComponent<DataFromAnalytics>();
            }

            // Update is called once per frame
            void Update()
            {
            
            }
        }
    ```

5.  <span data-ttu-id="18eb1-411">**移動** クラス内で、空の **Update ()** メソッドの *下* に、ユーザーがハンドコントローラーを使用して仮想空間内を移動できるようにする次のメソッドを挿入します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-411">Within the **Movement** class, *below* the empty **Update()** method, insert the following methods that allow the user to use the hand controller to move in the virtual space:</span></span>

    ```csharp
        /// <summary>
        /// Used for tracking the current position and rotation of the controller.
        /// </summary>
        private void UpdateControllerState()
        {
    #if UNITY_WSA && UNITY_2017_2_OR_NEWER
            // Check for current connected controllers, only if WSA.
            string message = string.Empty;

            if (InteractionManager.GetCurrentReading().Length > 0)
            {
                foreach (var sourceState in InteractionManager.GetCurrentReading())
                {
                    if (sourceState.source.kind == InteractionSourceKind.Controller && sourceState.source.handedness == _handness)
                    {
                        // If a controller source is found, which matches the selected handness, 
                        // check whether interaction source updated events have been registered. 
                        if (_isAttached == false)
                        {
                            // Register events, as not yet registered.
                            message = "<color=green>Source Found: Registering Controller Source Events</color>";
                            _isAttached = true;

                            InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
                        }

                        // Update the position and rotation information for the controller.
                        Vector3 newPosition;
                        if (sourceState.sourcePose.TryGetPosition(out newPosition, InteractionSourceNode.Pointer) && ValidPosition(newPosition))
                        {
                            Controller.transform.localPosition = newPosition;
                        }

                        Quaternion newRotation;

                        if (sourceState.sourcePose.TryGetRotation(out newRotation, InteractionSourceNode.Pointer) && ValidRotation(newRotation))
                        {
                            Controller.transform.localRotation = newRotation;
                        }
                    }
                }
            }
            else
            {
                // Controller source not detected. 
                message = "<color=blue>Trying to detect controller source</color>";

                if (_isAttached == true)
                {
                    // A source was previously connected, however, has been lost. Disconnected
                    // all registered events. 

                    _isAttached = false;

                    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;

                    message = "<color=red>Source Lost: Detaching Controller Source Events</color>";
                }
            }

            if(message != string.Empty)
            {
                Debug.Log(message);
            }
    #endif
        }
    ```

    ```csharp
        /// <summary>
        /// This registered event is triggered when a source state has been updated.
        /// </summary>
        /// <param name="obj"></param>
        private void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs obj)
        {
            if (obj.state.source.handedness == _handness)
            {
                if(obj.state.thumbstickPosition.magnitude > 0.2f)
                {
                    float thumbstickY = obj.state.thumbstickPosition.y;

                    // Vertical Input.
                    if (thumbstickY > 0.3f || thumbstickY < -0.3f)
                    {
                        _playerMovementTranslation = Camera.main.transform.forward;
                        _playerMovementTranslation.y = 0;
                        transform.Translate(_playerMovementTranslation * UserSpeed * Time.deltaTime * thumbstickY, Space.World);
                    }
                }
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Check that controller position is valid. 
        /// </summary>
        /// <param name="inputVector3">The Vector3 to check</param>
        /// <returns>The position is valid</returns>
        private bool ValidPosition(Vector3 inputVector3)
        {
            return !float.IsNaN(inputVector3.x) && !float.IsNaN(inputVector3.y) && !float.IsNaN(inputVector3.z) && !float.IsInfinity(inputVector3.x) && !float.IsInfinity(inputVector3.y) && !float.IsInfinity(inputVector3.z);
        }

        /// <summary>
        /// Check that controller rotation is valid. 
        /// </summary>
        /// <param name="inputQuaternion">The Quaternion to check</param>
        /// <returns>The rotation is valid</returns>
        private bool ValidRotation(Quaternion inputQuaternion)
        {
            return !float.IsNaN(inputQuaternion.x) && !float.IsNaN(inputQuaternion.y) && !float.IsNaN(inputQuaternion.z) && !float.IsNaN(inputQuaternion.w) && !float.IsInfinity(inputQuaternion.x) && !float.IsInfinity(inputQuaternion.y) && !float.IsInfinity(inputQuaternion.z) && !float.IsInfinity(inputQuaternion.w);
        }   
    ```

6.  <span data-ttu-id="18eb1-412">最後に、 **Update ()** メソッド内にメソッド呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-412">Lastly add the method call within the **Update()** method.</span></span>

    ```csharp
        // Update is called once per frame
        void Update()
        {
            UpdateControllerState();
        }
    ```

7.  <span data-ttu-id="18eb1-413">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="18eb1-413">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11---setting-up-the-scripts-references"></a><span data-ttu-id="18eb1-414">Chapter 11-スクリプト参照の設定</span><span class="sxs-lookup"><span data-stu-id="18eb1-414">Chapter 11 - Setting up the scripts references</span></span>

<span data-ttu-id="18eb1-415">この章では、 **移動** スクリプトを **カメラの親** に配置し、その参照ターゲットを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-415">In this Chapter you need to place the **Movement** script onto the **Camera Parent** and set its reference targets.</span></span> <span data-ttu-id="18eb1-416">そのスクリプトは、必要な場所にある他のスクリプトの配置を処理します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-416">That script will then handle placing the other scripts where they need to be.</span></span>

1.  <span data-ttu-id="18eb1-417">[*プロジェクト] パネル* の [**スクリプト**] フォルダーで、[*階層] パネル* にある [**カメラ] 親** オブジェクトに **移動** スクリプトをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-417">From the **Scripts** folder in the *Project Panel*, drag the **Movement** script to the **Camera Parent** object, located in the *Hierarchy Panel*.</span></span>

    ![Unity シーンでのスクリプト参照の設定](images/AzureLabs-Lab309-48.png)

2.  <span data-ttu-id="18eb1-419">**カメラの親** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-419">Click on the **Camera Parent**.</span></span> <span data-ttu-id="18eb1-420">[*階層] パネル* で、[*階層]* パネルの **右側** のオブジェクトを [*インスペクター] パネル* の [参照ターゲット] の [**コントローラー**] にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-420">In the *Hierarchy Panel*, drag the **Right Hand** object from the *Hierarchy Panel* to the reference target, **Controller**, in the *Inspector Panel*.</span></span> <span data-ttu-id="18eb1-421">次の図に示すように、 **ユーザーの速度** を **5** に設定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-421">Set the **User Speed** to **5**, as shown in the image below.</span></span>

    ![Unity シーンでのスクリプト参照の設定](images/AzureLabs-Lab309-49.png)

## <a name="chapter-12---build-the-unity-project"></a><span data-ttu-id="18eb1-423">第12章-Unity プロジェクトのビルド</span><span class="sxs-lookup"><span data-stu-id="18eb1-423">Chapter 12 - Build the Unity project</span></span>

<span data-ttu-id="18eb1-424">このプロジェクトの Unity セクションに必要なものはすべて完了したので、Unity から構築します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-424">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="18eb1-425">[**ビルドの設定**]、([**ファイル**  >  **ビルドの設定**]) の順に移動します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-425">Navigate to **Build Settings**, (**File** > **Build Settings**).</span></span>

2.  <span data-ttu-id="18eb1-426">[ **ビルドの設定** ] ウィンドウで、[ **ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-426">From the **Build Settings** window, click **Build**.</span></span>

    ![Unity プロジェクトを UWP ソリューションにビルドする](images/AzureLabs-Lab309-50.png)

3.  <span data-ttu-id="18eb1-428">**エクスプローラー** ウィンドウがポップアップ表示され、ビルドの場所を入力するように求められます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-428">A **File Explorer** window will pop-up, prompting you for a location for the build.</span></span> <span data-ttu-id="18eb1-429">(左上隅にある [ **新しいフォルダー** ] をクリックして) 新しいフォルダーを作成し、 **ビルド** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-429">Create a new folder (by clicking **New Folder** in the top-left corner), and name it **BUILDS**.</span></span>

    ![Unity プロジェクトを UWP ソリューションにビルドする](images/AzureLabs-Lab309-51.png)

    1.  <span data-ttu-id="18eb1-431">[新しい **ビルド** ] フォルダーを開き、別のフォルダーを作成し ([ **新しいフォルダー** ] をもう一度使用)、「 **MR \_ Azure \_ Application \_ Insights**」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-431">Open the new **BUILDS** folder, and create another folder (using **New Folder** once more), and name it **MR\_Azure\_Application\_Insights**.</span></span>

        ![Unity プロジェクトを UWP ソリューションにビルドする](images/AzureLabs-Lab309-52.png)

    2.  <span data-ttu-id="18eb1-433">**MR \_ Azure \_ Application \_ Insights** フォルダーを選択した状態で、[**フォルダーの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-433">With the **MR\_Azure\_Application\_Insights** folder selected, click **Select Folder**.</span></span> <span data-ttu-id="18eb1-434">プロジェクトがビルドされるまでに1分ほどかかります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-434">The project will take a minute or so to build.</span></span>

4.  <span data-ttu-id="18eb1-435">次の *ビルド* では、新しいプロジェクトの場所を示す **ファイルエクスプローラー** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-435">Following *Build*, **File Explorer** will appear showing you the location of your new project.</span></span>

## <a name="chapter-13---deploy-mr_azure_application_insights-app-to-your-machine"></a><span data-ttu-id="18eb1-436">第13章: MR_Azure_Application_Insights アプリをコンピューターにデプロイする</span><span class="sxs-lookup"><span data-stu-id="18eb1-436">Chapter 13 - Deploy MR_Azure_Application_Insights app to your machine</span></span>

<span data-ttu-id="18eb1-437">ローカルコンピューターに **MR \_ Azure \_ Application \_ Insights** アプリをデプロイするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-437">To deploy the **MR\_Azure\_Application\_Insights** app on your Local Machine:</span></span>

1.  <span data-ttu-id="18eb1-438">**Visual Studio** で **MR \_ Azure \_ Application \_ Insights** アプリのソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-438">Open the solution file of your **MR\_Azure\_Application\_Insights** app in **Visual Studio**.</span></span>

2.  <span data-ttu-id="18eb1-439">**ソリューションプラットフォーム** で、[ **X86, ローカルコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-439">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="18eb1-440">**ソリューション構成** で、[**デバッグ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-440">In the **Solution Configuration** select **Debug**.</span></span>

    ![Unity プロジェクトを UWP ソリューションにビルドする](images/AzureLabs-Lab309-53.png)

4.  <span data-ttu-id="18eb1-442">[ **ビルド] メニュー** の [ **ソリューションの配置** ] をクリックして、アプリケーションをコンピューターにサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-442">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="18eb1-443">アプリがインストール済みのアプリの一覧に表示され、起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-443">Your app should now appear in the list of installed apps, ready to be launched.</span></span>

6. <span data-ttu-id="18eb1-444">Mixed reality アプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-444">Launch the mixed reality application.</span></span>

7. <span data-ttu-id="18eb1-445">シーン内を移動し、オブジェクトに近づいて、それらを確認すると、 *Azure Insights サービス* が十分なイベントデータを収集したときに、最も近いオブジェクトが緑色に設定されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-445">Move around the scene, approaching objects and looking at them, when the *Azure Insight Service* has collected enough event data, it will set the object that has been approached the most to green.</span></span>

> [!IMPORTANT] 
> <span data-ttu-id="18eb1-446">サービスによって収集される *イベントとメトリック* の平均待機時間は約15分かかりますが、場合によっては最大1時間かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-446">While the average waiting time for the *Events and Metrics* to be collected by the Service takes around 15 min, in some occasions it might take up to 1 hour.</span></span>

## <a name="chapter-14---the-application-insights-service-portal"></a><span data-ttu-id="18eb1-447">第14章-Application Insights サービスポータル</span><span class="sxs-lookup"><span data-stu-id="18eb1-447">Chapter 14 - The Application Insights Service portal</span></span>

<span data-ttu-id="18eb1-448">複数のオブジェクトでシーンと gazed を移動すると、 *Application Insights サービス* ポータルで収集されたデータを確認できます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-448">Once you have roamed around the scene and gazed at several objects you can see the data collected in the *Application Insights Service* portal.</span></span>

1.  <span data-ttu-id="18eb1-449">Application Insights サービスポータルに戻ります。</span><span class="sxs-lookup"><span data-stu-id="18eb1-449">Go back to your Application Insights Service portal.</span></span>

2.  <span data-ttu-id="18eb1-450">[ *メトリックスエクスプローラー*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="18eb1-450">Click on *Metrics Explorer*.</span></span>

    ![収集したデータの表示](images/AzureLabs-Lab309-54.png)

3.  <span data-ttu-id="18eb1-452">これは、アプリケーションに関連する *イベントとメトリック* を表すグラフを含むタブで開きます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-452">It will open in a tab containing the graph which represent the *Events and Metrics* related to your application.</span></span> <span data-ttu-id="18eb1-453">前述のように、データがグラフに表示されるまでに時間がかかる場合があります (最大1時間)。</span><span class="sxs-lookup"><span data-stu-id="18eb1-453">As mentioned above, it might take some time (up to 1 hour) for the data to be displayed in the graph</span></span>

    ![収集したデータの表示](images/AzureLabs-Lab309-55.png)

4.  <span data-ttu-id="18eb1-455">[アプリケーションバージョンごとの *イベントの総数*] の *イベントバー* をクリックすると、イベントの詳細な内訳が名前と共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-455">Click on the *Events bar* in the *Total of Events* by Application Version, to see a detailed breakdown of the events with their names.</span></span>

    ![収集したデータの表示](images/AzureLabs-Lab309-56.png)

## <a name="your-finished-your-application-insights-service-application"></a><span data-ttu-id="18eb1-457">Application Insights サービスアプリケーションが完成しました</span><span class="sxs-lookup"><span data-stu-id="18eb1-457">Your finished your Application Insights Service application</span></span>

<span data-ttu-id="18eb1-458">これで、Application Insights サービスを活用してアプリ内でユーザーのアクティビティを監視する、mixed reality アプリが作成されました。</span><span class="sxs-lookup"><span data-stu-id="18eb1-458">Congratulations, you built a mixed reality app that leverages the Application Insights Service to monitor user's activity within your app.</span></span>

![コースの結果](images/AzureLabs-Lab309-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="18eb1-460">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="18eb1-460">Bonus Exercises</span></span>

<span data-ttu-id="18eb1-461">**演習1**</span><span class="sxs-lookup"><span data-stu-id="18eb1-461">**Exercise 1**</span></span>

<span data-ttu-id="18eb1-462">オブジェクトを手動で作成するのではなく、オブジェクトを手動で作成し、スクリプト内の平面上に座標を設定します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-462">Try spawning, rather than manually creating, the ObjectInScene objects and set their coordinates on the plane within your scripts.</span></span> <span data-ttu-id="18eb1-463">このようにして、最も人気のあるオブジェクト (つまり、宝石または近接の結果) を Azure に要求し、それらのオブジェクト *のうちの1つ* を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="18eb1-463">In this way, you could ask Azure what the most popular object was (either from gaze or proximity results) and spawn an *extra* one of those objects.</span></span>

<span data-ttu-id="18eb1-464">**演習2**</span><span class="sxs-lookup"><span data-stu-id="18eb1-464">**Exercise 2**</span></span>

<span data-ttu-id="18eb1-465">Application Insights の結果を時間で並べ替えて、最も関連性の高いデータを取得し、その時間に依存するデータをアプリケーションに実装します。</span><span class="sxs-lookup"><span data-stu-id="18eb1-465">Sort your Application Insights results by time, so that you get the most relevant data, and implement that time sensitive data in your application.</span></span>

