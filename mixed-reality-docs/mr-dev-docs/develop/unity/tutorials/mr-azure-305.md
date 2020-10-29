---
title: MR と Azure 305-Functions と storage
description: このコースでは、mixed reality アプリケーション内で Azure Storage と関数を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, 関数, ストレージ, hololens, イマーシブ, vr
ms.openlocfilehash: 83da419fe780368962af9e4d833ebe86d46f1b81
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687847"
---
# <a name="mr-and-azure-305-functions-and-storage"></a><span data-ttu-id="56d5b-104">MR と Azure 305:機能とストレージ</span><span class="sxs-lookup"><span data-stu-id="56d5b-104">MR and Azure 305: Functions and storage</span></span>

<br>

>[!NOTE]
><span data-ttu-id="56d5b-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="56d5b-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="56d5b-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="56d5b-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="56d5b-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。</span><span class="sxs-lookup"><span data-stu-id="56d5b-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="56d5b-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="56d5b-109">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="56d5b-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="56d5b-110">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

![最終製品-開始](images/AzureLabs-Lab5-00.png)

<span data-ttu-id="56d5b-112">このコースでは、Azure Functions を作成して使用し、混合の現実アプリケーション内で Azure Storage リソースを使用してデータを格納する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-112">In this course, you will learn how to create and use Azure Functions and store data with an Azure Storage resource, within a mixed reality application.</span></span>

<span data-ttu-id="56d5b-113">*Azure Functions* は Microsoft のサービスであり、開発者は Azure で小さなコードである "Functions" を実行できます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-113">*Azure Functions* is a Microsoft service, which allows developers to run small pieces of code, 'functions', in Azure.</span></span> <span data-ttu-id="56d5b-114">これにより、ローカルアプリケーションではなく、クラウドに作業を委任することができます。これには多くのメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-114">This provides a way to delegate work to the cloud, rather than your local application, which can have many benefits.</span></span> <span data-ttu-id="56d5b-115">*Azure Functions* は、C \# 、F \# 、Node.js、Java、PHP など、いくつかの開発言語をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="56d5b-115">*Azure Functions* supports several development languages, including C\#, F\#, Node.js, Java, and PHP.</span></span> <span data-ttu-id="56d5b-116">詳細については、 [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-116">For more information, visit the [Azure Functions article](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="56d5b-117">*Azure Storage* は Microsoft のクラウドサービスであり、開発者はデータを格納できます。このサービスは、高可用性、セキュリティ、耐久性、拡張性、および冗長性を備えています。</span><span class="sxs-lookup"><span data-stu-id="56d5b-117">*Azure Storage* is a Microsoft cloud service, which allows developers to store data, with the insurance that it will be highly available, secure, durable, scalable, and redundant.</span></span> <span data-ttu-id="56d5b-118">これは、Microsoft がすべてのメンテナンスと重大な問題を処理することを意味します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-118">This means Microsoft will handle all maintenance, and critical problems for you.</span></span> <span data-ttu-id="56d5b-119">詳細については、 [Azure Storage](https://docs.microsoft.com/azure/storage/common/storage-introduction)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-119">For more information, visit the [Azure Storage article](https://docs.microsoft.com/azure/storage/common/storage-introduction).</span></span>

<span data-ttu-id="56d5b-120">このコースを完了すると、現実のイマーシブヘッドセットアプリケーションが完成し、次のことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-120">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="56d5b-121">ユーザーがシーンを見つめていることを許可します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-121">Allow the user to gaze around a scene.</span></span>
2.  <span data-ttu-id="56d5b-122">ユーザーが 3D ' ボタン ' で gazes たときにオブジェクトの生成をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-122">Trigger the spawning of objects when the user gazes at a 3D 'button'.</span></span>
3.  <span data-ttu-id="56d5b-123">生成されたオブジェクトは、Azure 関数によって選択されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-123">The spawned objects will be chosen by an Azure Function.</span></span>
4.  <span data-ttu-id="56d5b-124">各オブジェクトが生成されると、アプリケーションは *Azure Storage* にある *Azure ファイル* にオブジェクトの種類を格納します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-124">As each object is spawned, the application will store the object type in an *Azure File* , located in *Azure Storage* .</span></span>
5.  <span data-ttu-id="56d5b-125">もう一度読み込むと、 *Azure ファイル* データが取得され、アプリケーションの前のインスタンスから生成されたアクションの再生に使用されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-125">Upon loading a second time, the *Azure File* data will be retrieved, and used to replay the spawning actions from the previous instance of the application.</span></span>

<span data-ttu-id="56d5b-126">アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-126">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="56d5b-127">このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="56d5b-127">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="56d5b-128">このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-128">It is your job to use the knowledge you gain from this course to enhance your mixed reality Application.</span></span>

## <a name="device-support"></a><span data-ttu-id="56d5b-129">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="56d5b-129">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="56d5b-130">コース</span><span class="sxs-lookup"><span data-stu-id="56d5b-130">Course</span></span></th><th style="width:150px"> <span data-ttu-id="56d5b-131"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="56d5b-131"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="56d5b-132"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="56d5b-132"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="56d5b-133">MR と Azure 305:機能とストレージ</span><span class="sxs-lookup"><span data-stu-id="56d5b-133">MR and Azure 305: Functions and storage</span></span></td><td style="text-align: center;"> <span data-ttu-id="56d5b-134">✔️</span><span class="sxs-lookup"><span data-stu-id="56d5b-134">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="56d5b-135">✔️</span><span class="sxs-lookup"><span data-stu-id="56d5b-135">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="56d5b-136">このコースでは主に Windows Mixed Reality イマーシブ (VR) ヘッドセットに焦点を当てていますが、このコースで学習した内容を Microsoft HoloLens に適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-136">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="56d5b-137">このコースに従うと、HoloLens をサポートするために必要となる可能性のある変更に関する注意事項が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-137">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="56d5b-138">前提条件</span><span class="sxs-lookup"><span data-stu-id="56d5b-138">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="56d5b-139">このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="56d5b-139">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="56d5b-140">また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証されたものを表します (2018 年5月)。</span><span class="sxs-lookup"><span data-stu-id="56d5b-140">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="56d5b-141">「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものよりも新しいソフトウェアで見つかったものと完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="56d5b-141">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="56d5b-142">このコースでは、次のハードウェアとソフトウェアをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-142">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="56d5b-143">開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-143">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="56d5b-144">開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="56d5b-144">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="56d5b-145">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="56d5b-145">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="56d5b-146">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="56d5b-146">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="56d5b-147">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="56d5b-147">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="56d5b-148">[Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](../../../hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="56d5b-148">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](../../../hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="56d5b-149">Azure リソースを作成するための Azure アカウントへのサブスクリプション</span><span class="sxs-lookup"><span data-stu-id="56d5b-149">A subscription to an Azure account for creating Azure resources</span></span>
- <span data-ttu-id="56d5b-150">Azure のセットアップとデータ取得のためのインターネットアクセス</span><span class="sxs-lookup"><span data-stu-id="56d5b-150">Internet access for Azure setup and data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="56d5b-151">開始する前に</span><span class="sxs-lookup"><span data-stu-id="56d5b-151">Before you start</span></span>

<span data-ttu-id="56d5b-152">このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="56d5b-152">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="56d5b-153">章 1-Azure Portal</span><span class="sxs-lookup"><span data-stu-id="56d5b-153">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="56d5b-154">**Azure Storage サービス** を使用するには、Azure portal で **ストレージアカウント** を作成し、構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-154">To use the **Azure Storage Service** , you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="56d5b-155">[Azure Portal](https://portal.azure.com)にログインします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-155">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="56d5b-156">まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-156">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="56d5b-157">このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-157">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="56d5b-158">ログインしたら、左上隅にある [ **新規** ] をクリックし、[ *ストレージアカウント* ] を検索して、 **Enter キー** を押します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-158">Once you are logged in, click on **New** in the top left corner, and search for *Storage account* , and click **Enter** .</span></span>

    ![azure storage の検索](images/AzureLabs-Lab5-01.png)

    > [!NOTE]
    > <span data-ttu-id="56d5b-160">新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="56d5b-160">The word **New** may have been replaced with **Create a resource** , in newer portals.</span></span>

3.  <span data-ttu-id="56d5b-161">新しいページには、 *Azure Storage アカウント* サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-161">The new page will provide a description of the *Azure Storage account* service.</span></span> <span data-ttu-id="56d5b-162">このプロンプトの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-162">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![サービスの作成](images/AzureLabs-Lab5-02.png)

4.  <span data-ttu-id="56d5b-164">[ **作成** :</span><span class="sxs-lookup"><span data-stu-id="56d5b-164">Once you have clicked on **Create** :</span></span>

    1.  <span data-ttu-id="56d5b-165">アカウントの *名前* を挿入します。このフィールドには数字と小文字のみを使用できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-165">Insert a *Name* for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="56d5b-166">[ *デプロイモデル* ] で、[ **リソースマネージャー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-166">For *Deployment model* , select **Resource manager** .</span></span>

    3.  <span data-ttu-id="56d5b-167">[ *アカウントの種類* ] で、[ **ストレージ (汎用 v1)** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-167">For *Account kind* , select **Storage (general purpose v1)** .</span></span>

    4.  <span data-ttu-id="56d5b-168">リソースグループの *場所* を決定します (新しいリソースグループを作成している場合)。</span><span class="sxs-lookup"><span data-stu-id="56d5b-168">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="56d5b-169">この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="56d5b-169">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="56d5b-170">一部の Azure 資産は、特定のリージョンでのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-170">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="56d5b-171">*レプリケーション* の場合は、[ **読み取りアクセス-geo 冗長ストレージ (RA-GRS)** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-171">For *Replication* select **Read-access-geo-redundant storage (RA-GRS)** .</span></span>

    6.  <span data-ttu-id="56d5b-172">*[パフォーマンス]* には **[Standard]** を選択します</span><span class="sxs-lookup"><span data-stu-id="56d5b-172">For *Performance* , select **Standard** .</span></span>

    7.  <span data-ttu-id="56d5b-173">*安全な転送* は無効のまま **に** しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-173">Leave *Secure transfer required* as **Disabled** .</span></span>

    8.  <span data-ttu-id="56d5b-174">*サブスクリプション* を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-174">Select a *Subscription* .</span></span>

    9. <span data-ttu-id="56d5b-175">リソースグループを選択するか、新しい *リソースグループ* を作成します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-175">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="56d5b-176">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-176">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="56d5b-177">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-177">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="56d5b-178">Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-178">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    10. <span data-ttu-id="56d5b-179">また、このサービスに適用されている使用条件を理解していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-179">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    11. <span data-ttu-id="56d5b-180">**［作成］** を選択します</span><span class="sxs-lookup"><span data-stu-id="56d5b-180">Select **Create** .</span></span>

        ![入力サービス情報](images/AzureLabs-Lab5-03.png)

5.  <span data-ttu-id="56d5b-182">[ **作成** ] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-182">Once you have clicked on **Create** , you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="56d5b-183">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-183">A notification will appear in the portal once the Service instance is created.</span></span>

    ![azure ポータルでの新しい通知](images/AzureLabs-Lab5-04.png)

7.  <span data-ttu-id="56d5b-185">通知をクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-185">Click on the notifications to explore your new Service instance.</span></span>

    ![リソースにアクセス](images/AzureLabs-Lab5-05.png)

8.  <span data-ttu-id="56d5b-187">通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-187">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="56d5b-188">新しい *ストレージアカウント* のサービスインスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-188">You will be taken to your new *Storage account* service instance.</span></span>

    ![アクセス キー](images/AzureLabs-Lab5-06.png)

9.  <span data-ttu-id="56d5b-190">[ *アクセスキー* ] をクリックして、このクラウドサービスのエンドポイントを表示します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-190">Click *Access keys* , to reveal the endpoints for this cloud service.</span></span> <span data-ttu-id="56d5b-191">*メモ帳* または同様の方法を使用して、後で使用するためにいずれかのキーをコピーします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-191">Use *Notepad* or similar, to copy one of your keys for use later.</span></span> <span data-ttu-id="56d5b-192">また、 *接続文字列* の値もメモしておいてください。これは、後で作成する *azureservices* クラスで使用されるためです。</span><span class="sxs-lookup"><span data-stu-id="56d5b-192">Also, note the *Connection string* value, as it will be used in the *AzureServices* class, which you will create later.</span></span>

    ![接続文字列のコピー](images/AzureLabs-Lab5-07.png)

## <a name="chapter-2---setting-up-an-azure-function"></a><span data-ttu-id="56d5b-194">Chapter 2-Azure 関数の設定</span><span class="sxs-lookup"><span data-stu-id="56d5b-194">Chapter 2 - Setting up an Azure Function</span></span>

<span data-ttu-id="56d5b-195">次に、azure サービスで **azure** **関数** を作成します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-195">You will now write an **Azure** **Function** in the Azure Service.</span></span>

<span data-ttu-id="56d5b-196">**Azure 関数** を使用すると、コード内で従来の関数を使用した場合とほぼ同じ処理を行うことができます。これは、azure アカウントにアクセスするための資格情報を持つ任意のアプリケーションからこの関数にアクセスできるという点です。</span><span class="sxs-lookup"><span data-stu-id="56d5b-196">You can use an **Azure Function** to do nearly anything that you would do with a classic function in your code, the difference being that this function can be accessed by any application that has credentials to access your Azure Account.</span></span>

<span data-ttu-id="56d5b-197">Azure 関数を作成するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-197">To create an Azure Function:</span></span>

1.  <span data-ttu-id="56d5b-198">*Azure Portal* で、左上隅にある [ **新規** ] をクリックし、 *Function App* を検索して、 **Enter キー** を押します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-198">From your *Azure Portal* , click on **New** in the top left corner, and search for *Function App* , and click **Enter** .</span></span>

    ![function app の作成](images/AzureLabs-Lab5-08.png)

    > [!NOTE]
    > <span data-ttu-id="56d5b-200">新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="56d5b-200">The word **New** may have been replaced with **Create a resource** , in newer portals.</span></span>

2.  <span data-ttu-id="56d5b-201">新しいページには、 *Azure Function App* サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-201">The new page will provide a description of the *Azure Function App* service.</span></span> <span data-ttu-id="56d5b-202">このプロンプトの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-202">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![関数アプリの情報](images/AzureLabs-Lab5-09.png)

3.  <span data-ttu-id="56d5b-204">[ **作成** :</span><span class="sxs-lookup"><span data-stu-id="56d5b-204">Once you have clicked on **Create** :</span></span>

    1.  <span data-ttu-id="56d5b-205">*アプリ名* を指定します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-205">Provide an *App name* .</span></span> <span data-ttu-id="56d5b-206">ここでは、文字と数字のみを使用できます (大文字または小文字を使用できます)。</span><span class="sxs-lookup"><span data-stu-id="56d5b-206">Only letters and numbers can be used here (either upper or lower case is allowed).</span></span>

    2.  <span data-ttu-id="56d5b-207">任意の *サブスクリプション* を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-207">Select your preferred *Subscription* .</span></span>

    3. <span data-ttu-id="56d5b-208">リソースグループを選択するか、新しい *リソースグループ* を作成します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-208">Choose a *Resource Group* or create a new one.</span></span> <span data-ttu-id="56d5b-209">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-209">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="56d5b-210">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-210">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="56d5b-211">Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-211">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="56d5b-212">この演習では、選択した **OS** として [ *Windows* ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-212">For this exercise, select *Windows* as the chosen **OS** .</span></span>

    5.  <span data-ttu-id="56d5b-213">**ホスティングプラン** の *従量課金プラン* を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-213">Select *Consumption Plan* for the **Hosting Plan** .</span></span>

    6.  <span data-ttu-id="56d5b-214">リソースグループの *場所* を決定します (新しいリソースグループを作成している場合)。</span><span class="sxs-lookup"><span data-stu-id="56d5b-214">Determine the *Location* for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="56d5b-215">この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="56d5b-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="56d5b-216">一部の Azure 資産は、特定のリージョンでのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-216">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="56d5b-217">最適なパフォーマンスを得るには、ストレージアカウントと同じリージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-217">For optimal performance, select the same region as the storage account.</span></span>

    7.  <span data-ttu-id="56d5b-218">[ *ストレージ* ] で、[既存のものを **使用** ] を選択し、ドロップダウンメニューを使用して、以前に作成したストレージを検索します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-218">For *Storage* , select **Use existing** , and then using the dropdown menu, find your previously created storage.</span></span>

    8.  <span data-ttu-id="56d5b-219">この演習では、 *Application Insights* オフのままにします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-219">Leave *Application Insights* off for this exercise.</span></span>

        ![入力関数アプリの詳細](images/AzureLabs-Lab5-10.png)

4.  <span data-ttu-id="56d5b-221">**[作成]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-221">Click the **Create** button.</span></span>

5.  <span data-ttu-id="56d5b-222">[ **作成** ] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-222">Once you have clicked on **Create** , you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="56d5b-223">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-223">A notification will appear in the portal once the Service instance is created.</span></span>

    ![新しい azure portal の通知](images/AzureLabs-Lab5-11.png)

7.  <span data-ttu-id="56d5b-225">通知をクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-225">Click on the notifications to explore your new Service instance.</span></span> 

    ![リソース関数アプリにアクセス](images/AzureLabs-Lab5-12.png)

8.  <span data-ttu-id="56d5b-227">通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-227">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="56d5b-228">新しい *Function App* サービスインスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-228">You will be taken to your new *Function App* service instance.</span></span>

9.  <span data-ttu-id="56d5b-229">*Function App* ダッシュボードで、左側のパネルにある *関数* の上にマウスポインターを置き、 **プラス記号 (+)** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-229">On the *Function App* dashboard, hover your mouse over *Functions* , found within the panel on the left, and then click the **+ (plus)** symbol.</span></span>

    ![新しい関数の作成](images/AzureLabs-Lab5-13.png)

10. <span data-ttu-id="56d5b-231">次のページで、[ **Webhook + API** ] が選択されていることを確認し、[ *言語の選択]* で [ **CSharp** ] を選択します。このチュートリアルで使用する言語です。</span><span class="sxs-lookup"><span data-stu-id="56d5b-231">On the next page, ensure **Webhook + API** is selected, and for *Choose a language,* select **CSharp** , as this will be the language used for this tutorial.</span></span> <span data-ttu-id="56d5b-232">最後に、[ **この関数を作成** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-232">Lastly, click the **Create this function** button.</span></span>

    ![web フック csharp を選択します](images/AzureLabs-Lab5-14.png)

11. <span data-ttu-id="56d5b-234">コードページ (csx を実行します) に移動します (ただし、それ以外の場合は、左側のパネル内の [関数] ボックスの一覧で新しく作成した関数をクリックします)。</span><span class="sxs-lookup"><span data-stu-id="56d5b-234">You should be taken to the code page (run.csx), if not though, click on the newly created Function in the Functions list within the panel on the left.</span></span>

    ![新しい関数を開く](images/AzureLabs-Lab5-15.png)

12. <span data-ttu-id="56d5b-236">関数に次のコードをコピーします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-236">Copy the following code into your function.</span></span> <span data-ttu-id="56d5b-237">この関数は、呼び出されたときに、0から2までのランダムな整数を返します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-237">This function will simply return a random integer between 0 and 2 when called.</span></span> <span data-ttu-id="56d5b-238">既存のコードについて心配しないでください。一番上に貼り付けてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="56d5b-238">Do not worry about the existing code, feel free to paste over the top of it.</span></span>

    ```csharp
        using System.Net;
        using System.Threading.Tasks;

        public static int Run(CustomObject req, TraceWriter log)
        {
            Random rnd = new Random();
            int randomInt = rnd.Next(0, 3);
            return randomInt;
        }

        public class CustomObject
        {
            public String name {get; set;}
        }
    ```

13. <span data-ttu-id="56d5b-239">**[保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-239">Select **Save** .</span></span>

14. <span data-ttu-id="56d5b-240">結果は次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-240">The result should look like the image below.</span></span>

15. <span data-ttu-id="56d5b-241">[ **関数の URL の取得** ] をクリックし、表示されている *エンドポイント* を書き留めます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-241">Click on **Get function URL** and take note of the *endpoint* displayed.</span></span> <span data-ttu-id="56d5b-242">このコースの後半で作成する *Azureservices* クラスに挿入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-242">You will need to insert it into the *AzureServices* class that you will create later in this course.</span></span>

    ![関数エンドポイントを取得する](images/AzureLabs-Lab5-16.png)

    ![関数エンドポイントの挿入](images/AzureLabs-Lab5-16-5.png)

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="56d5b-245">章 3-Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="56d5b-245">Chapter 3 - Setting up the Unity project</span></span>

<span data-ttu-id="56d5b-246">次に示すのは、Mixed Reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="56d5b-246">The following is a typical set up for developing with Mixed Reality, and as such, is a good template for other projects.</span></span>

<span data-ttu-id="56d5b-247">Mixed reality のイマーシブヘッドセットをセットアップしてテストします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-247">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="56d5b-248">このコースでは、モーションコントローラーは必要 **ありません** 。</span><span class="sxs-lookup"><span data-stu-id="56d5b-248">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="56d5b-249">イマーシブヘッドセットの設定をサポートする必要がある場合は、 [mixed reality のセットアップ](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-249">If you need support setting up the immersive headset, please [visit the mixed reality set up article](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="56d5b-250">Unity を開き、[ **新規** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-250">Open Unity and click **New** .</span></span>

    ![新しい unity プロジェクトの作成](images/AzureLabs-Lab5-17.png)

2.  <span data-ttu-id="56d5b-252">ここで、Unity プロジェクト名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-252">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="56d5b-253">**MR_Azure_Functions** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-253">Insert **MR_Azure_Functions** .</span></span> <span data-ttu-id="56d5b-254">プロジェクトの種類が **3d** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-254">Make sure the project type is set to **3D** .</span></span> <span data-ttu-id="56d5b-255">場所を適切な *場所* に設定します (ルートディレクトリの方が適していることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="56d5b-255">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="56d5b-256">次に、[ **プロジェクトの作成** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-256">Then, click **Create project** .</span></span>

    ![新しい unity プロジェクトに名前を付ける](images/AzureLabs-Lab5-18.png)

3.  <span data-ttu-id="56d5b-258">Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-258">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio** .</span></span> <span data-ttu-id="56d5b-259">[設定の **編集** ] に移動し、  >  **Preferences** 新しいウィンドウで [ **外部ツール** ] に移動します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-259">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools** .</span></span> <span data-ttu-id="56d5b-260">**外部スクリプトエディター** を **Visual Studio 2017** に変更します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-260">Change **External Script Editor** to **Visual Studio 2017** .</span></span> <span data-ttu-id="56d5b-261">[ **基本設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-261">Close the **Preferences** window.</span></span>

    ![visual studio をスクリプトエディターとして設定する](images/AzureLabs-Lab5-19.png)

4.  <span data-ttu-id="56d5b-263">次に、[ **ファイル**  >  ] [ **ビルドの設定** ] の順に移動し、[ **プラットフォームの切り替え** ] ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-263">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform** , by clicking on the **Switch Platform** button.</span></span>

    ![プラットフォームを uwp に切り替える](images/AzureLabs-Lab5-20.png)

5.  <span data-ttu-id="56d5b-265">**ファイル**  >  の **ビルド設定** にアクセスして、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-265">Go to **File** > **Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="56d5b-266">**ターゲットデバイス** は **、任意のデバイス** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-266">**Target Device** is set to **Any Device** .</span></span>

        > <span data-ttu-id="56d5b-267">Microsoft HoloLens の場合は、 **ターゲットデバイス** を *HoloLens* に設定します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-267">For Microsoft HoloLens, set **Target Device** to *HoloLens* .</span></span>

    2. <span data-ttu-id="56d5b-268">**ビルドの種類** が **D3D** に設定されています</span><span class="sxs-lookup"><span data-stu-id="56d5b-268">**Build Type** is set to **D3D**</span></span>

    3. <span data-ttu-id="56d5b-269">**SDK** は最新の **インストール** に設定されています</span><span class="sxs-lookup"><span data-stu-id="56d5b-269">**SDK** is set to **Latest installed**</span></span>

    4. <span data-ttu-id="56d5b-270">**Visual Studio のバージョン** が、 **インストールされている最新** バージョンに設定されています</span><span class="sxs-lookup"><span data-stu-id="56d5b-270">**Visual Studio Version** is set to **Latest installed**</span></span>

    5. <span data-ttu-id="56d5b-271">**ビルドと実行** は **ローカルコンピューター** に設定されています</span><span class="sxs-lookup"><span data-stu-id="56d5b-271">**Build and Run** is set to **Local Machine**</span></span>

    6. <span data-ttu-id="56d5b-272">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-272">Save the scene and add it to the build.</span></span>

        1.  <span data-ttu-id="56d5b-273">これを行うには、[開いている **シーンの追加** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-273">Do this by selecting **Add Open Scenes** .</span></span> <span data-ttu-id="56d5b-274">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-274">A save window will appear.</span></span>

            ![オープンシーンを追加する](images/AzureLabs-Lab5-21.png)

        2.  <span data-ttu-id="56d5b-276">この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン** 」にします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-276">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes** .</span></span>

            ![シーンフォルダーの作成](images/AzureLabs-Lab5-22.png)

        3.  <span data-ttu-id="56d5b-278">新しく作成された [ **シーン** ] フォルダーを開き、[ **ファイル名:** テキスト] フィールドに「[アプリケーション]」 **と入力し、[\*\*\*\*保存** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-278">Open your newly created **Scenes** folder, and then in the **File name:** text field, type **FunctionsScene** , then press **Save** .</span></span>

            ![関数シーンの保存](images/AzureLabs-Lab5-23.png)

6.  <span data-ttu-id="56d5b-280">それ以外の設定は、[ **ビルド設定** ] の [既定] のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-280">The remaining settings, in **Build Settings** , should be left as default for now.</span></span>

    ![既定のビルド設定をそのまま使用する](images/AzureLabs-Lab5-24.png)

7.  <span data-ttu-id="56d5b-282">[ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-282">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span>

    ![インスペクターのプレーヤー設定](images/AzureLabs-Lab5-25.png)

8.  <span data-ttu-id="56d5b-284">このパネルでは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-284">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="56d5b-285">[ **その他の設定** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-285">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="56d5b-286">**Scripting Runtime のバージョン** は **実験的** (.net 4.6 と同等) である必要があります。これにより、エディターを再起動する必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-286">**Scripting Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>
        2.  <span data-ttu-id="56d5b-287">**バックエンド** は **.net** である必要があります</span><span class="sxs-lookup"><span data-stu-id="56d5b-287">**Scripting Backend** should be **.NET**</span></span>
        3.  <span data-ttu-id="56d5b-288">**API 互換性レベル** は **.net 4.6** である必要があります</span><span class="sxs-lookup"><span data-stu-id="56d5b-288">**API Compatibility Level** should be **.NET 4.6**</span></span>

    2.  <span data-ttu-id="56d5b-289">[ **発行の設定** ] タブの [ **機能** ] で、次の項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-289">Within the **Publishing Settings** tab, under **Capabilities** , check:</span></span>
        
        -  <span data-ttu-id="56d5b-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="56d5b-290">**InternetClient**</span></span>

            ![機能の設定](images/AzureLabs-Lab5-26.png)

    3.  <span data-ttu-id="56d5b-292">パネルの下にある [ **XR settings** ( **発行設定** ] の下にあります) で、[ **Virtual Reality がサポートされている** ] をオンにして、 **Windows Mixed reality SDK** が追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-292">Further down the panel, in **XR Settings** (found below **Publishing Settings** ), tick **Virtual Reality Supported** , make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![XR 設定の設定](images/AzureLabs-Lab5-27.png)

9.  <span data-ttu-id="56d5b-294">*ビルド設定* に戻る *Unity C# プロジェクト* はグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-294">Back in *Build Settings* *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span>

    ![c# プロジェクトの tick](images/AzureLabs-Lab5-28.png)

10.  <span data-ttu-id="56d5b-296">[ビルド設定] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-296">Close the Build Settings window.</span></span>

11. <span data-ttu-id="56d5b-297">シーンとプロジェクトを保存します ( **ファイル**  >  **保存シーン/ファイル**  >  **保存プロジェクト** )。</span><span class="sxs-lookup"><span data-stu-id="56d5b-297">Save your Scene and Project ( **FILE** > **SAVE SCENE / FILE** > **SAVE PROJECT** ).</span></span>

## <a name="chapter-4---setup-main-camera"></a><span data-ttu-id="56d5b-298">第4章-セットアップのメインカメラ</span><span class="sxs-lookup"><span data-stu-id="56d5b-298">Chapter 4 - Setup Main Camera</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56d5b-299">このコースの構成要素をスキップし *て、コード* に直接進む場合は、unitypackage を [ダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage)して、 [カスタムパッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-299">If you wish to skip the *Unity Set up* components of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20305%20-%20Functions%20and%20storage/Azure-MR-305.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="56d5b-300">これには、次の章の Dll も含まれます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-300">This will also contain the DLLs from the next Chapter.</span></span> <span data-ttu-id="56d5b-301">インポート後、 [第7章](#chapter-7---create-the-azureservices-class)から続行します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-301">After import, continue from [Chapter 7](#chapter-7---create-the-azureservices-class).</span></span> 

1.  <span data-ttu-id="56d5b-302">[ *階層] パネル* には、 **メインカメラ** と呼ばれるオブジェクトが表示されます。このオブジェクトは、アプリケーションの "内側" にある "ヘッド" ポイントを表します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-302">In the *Hierarchy Panel* , you will find an object called **Main Camera** , this object represents your "head" point of view once you are "inside" your application.</span></span>

2.  <span data-ttu-id="56d5b-303">Unity ダッシュボードを前面に表示し、 **カメラのメイン** のユーザーオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-303">With the Unity Dashboard in front of you, select the **Main Camera GameObject** .</span></span> <span data-ttu-id="56d5b-304">[ *インスペクター] パネル* (通常はダッシュボード内の右側にあります) には、そのユーザーの *オブジェクト* のさまざまなコンポーネントが表示されます。これには、上部にある [ *変換* ]、[ *カメラ* ]、および他のコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-304">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject* , with *Transform* at the top, followed by *Camera* , and some other components.</span></span> <span data-ttu-id="56d5b-305">メインカメラの変換をリセットして、正しく配置されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-305">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>

3.  <span data-ttu-id="56d5b-306">これを行うには、カメラの *変換* コンポーネントの横にある **歯車** アイコンを選択し、[ **リセット** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-306">To do this, select the **Gear** icon next to the Camera's *Transform* component, and select **Reset** .</span></span>

    ![変換のリセット](images/AzureLabs-Lab5-29.png)

4.  <span data-ttu-id="56d5b-308">次に、 **変換** コンポーネントを次のように更新します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-308">Then update the **Transform** component to look like:</span></span>

    |         |    <span data-ttu-id="56d5b-309">変換-位置</span><span class="sxs-lookup"><span data-stu-id="56d5b-309">TRANSFORM - POSITION</span></span>   |       |
    | :-----: | :-----------------------: | :----:|
    | <span data-ttu-id="56d5b-310">**X**</span><span class="sxs-lookup"><span data-stu-id="56d5b-310">**X**</span></span>   | <span data-ttu-id="56d5b-311">**Y**</span><span class="sxs-lookup"><span data-stu-id="56d5b-311">**Y**</span></span>                     | <span data-ttu-id="56d5b-312">**Z**</span><span class="sxs-lookup"><span data-stu-id="56d5b-312">**Z**</span></span> |
    | <span data-ttu-id="56d5b-313">0</span><span class="sxs-lookup"><span data-stu-id="56d5b-313">0</span></span>       | <span data-ttu-id="56d5b-314">1</span><span class="sxs-lookup"><span data-stu-id="56d5b-314">1</span></span>                         | <span data-ttu-id="56d5b-315">0</span><span class="sxs-lookup"><span data-stu-id="56d5b-315">0</span></span>     |    

    |       | <span data-ttu-id="56d5b-316">変換-回転</span><span class="sxs-lookup"><span data-stu-id="56d5b-316">TRANSFORM - ROTATION</span></span> |       |
    | :---: | :------------------: | :----:|
    | <span data-ttu-id="56d5b-317">**X**</span><span class="sxs-lookup"><span data-stu-id="56d5b-317">**X**</span></span> | <span data-ttu-id="56d5b-318">**Y**</span><span class="sxs-lookup"><span data-stu-id="56d5b-318">**Y**</span></span>                | <span data-ttu-id="56d5b-319">**Z**</span><span class="sxs-lookup"><span data-stu-id="56d5b-319">**Z**</span></span> |
    | <span data-ttu-id="56d5b-320">0</span><span class="sxs-lookup"><span data-stu-id="56d5b-320">0</span></span>     | <span data-ttu-id="56d5b-321">0</span><span class="sxs-lookup"><span data-stu-id="56d5b-321">0</span></span>                    | <span data-ttu-id="56d5b-322">0</span><span class="sxs-lookup"><span data-stu-id="56d5b-322">0</span></span>     |

    |       | <span data-ttu-id="56d5b-323">変換-スケール</span><span class="sxs-lookup"><span data-stu-id="56d5b-323">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="56d5b-324">**X**</span><span class="sxs-lookup"><span data-stu-id="56d5b-324">**X**</span></span> | <span data-ttu-id="56d5b-325">**Y**</span><span class="sxs-lookup"><span data-stu-id="56d5b-325">**Y**</span></span>             | <span data-ttu-id="56d5b-326">**Z**</span><span class="sxs-lookup"><span data-stu-id="56d5b-326">**Z**</span></span> |
    | <span data-ttu-id="56d5b-327">1</span><span class="sxs-lookup"><span data-stu-id="56d5b-327">1</span></span>     | <span data-ttu-id="56d5b-328">1</span><span class="sxs-lookup"><span data-stu-id="56d5b-328">1</span></span>                 | <span data-ttu-id="56d5b-329">1</span><span class="sxs-lookup"><span data-stu-id="56d5b-329">1</span></span>     |

    ![カメラの変換の設定](images/AzureLabs-Lab5-30.png)

## <a name="chapter-5---setting-up-the-unity-scene"></a><span data-ttu-id="56d5b-331">章 5-Unity シーンの設定</span><span class="sxs-lookup"><span data-stu-id="56d5b-331">Chapter 5 - Setting up the Unity scene</span></span>

1.  <span data-ttu-id="56d5b-332">[ *階層] パネル* の空の領域を右クリックし、[ **3d オブジェクト** ] の下に **平面** を追加します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-332">Right-click in an empty area of the *Hierarchy Panel* , under **3D  Object** , add a **Plane** .</span></span>

    ![新しい平面の作成](images/AzureLabs-Lab5-31.png)

2.  <span data-ttu-id="56d5b-334">[ **平面** ] オブジェクトを選択した状態で、[ *インスペクター] パネル* の次のパラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-334">With the **Plane** object selected, change the following parameters in the *Inspector Panel* :</span></span>

    |       | <span data-ttu-id="56d5b-335">変換-位置</span><span class="sxs-lookup"><span data-stu-id="56d5b-335">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="56d5b-336">**X**</span><span class="sxs-lookup"><span data-stu-id="56d5b-336">**X**</span></span> | <span data-ttu-id="56d5b-337">**Y**</span><span class="sxs-lookup"><span data-stu-id="56d5b-337">**Y**</span></span>                | <span data-ttu-id="56d5b-338">**Z**</span><span class="sxs-lookup"><span data-stu-id="56d5b-338">**Z**</span></span> |
    | <span data-ttu-id="56d5b-339">0</span><span class="sxs-lookup"><span data-stu-id="56d5b-339">0</span></span>     | <span data-ttu-id="56d5b-340">0</span><span class="sxs-lookup"><span data-stu-id="56d5b-340">0</span></span>                    | <span data-ttu-id="56d5b-341">4</span><span class="sxs-lookup"><span data-stu-id="56d5b-341">4</span></span>     |

    |       | <span data-ttu-id="56d5b-342">変換-スケール</span><span class="sxs-lookup"><span data-stu-id="56d5b-342">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="56d5b-343">**X**</span><span class="sxs-lookup"><span data-stu-id="56d5b-343">**X**</span></span> | <span data-ttu-id="56d5b-344">**Y**</span><span class="sxs-lookup"><span data-stu-id="56d5b-344">**Y**</span></span>             | <span data-ttu-id="56d5b-345">**Z**</span><span class="sxs-lookup"><span data-stu-id="56d5b-345">**Z**</span></span> |
    | <span data-ttu-id="56d5b-346">10</span><span class="sxs-lookup"><span data-stu-id="56d5b-346">10</span></span>    | <span data-ttu-id="56d5b-347">1</span><span class="sxs-lookup"><span data-stu-id="56d5b-347">1</span></span>                 | <span data-ttu-id="56d5b-348">10</span><span class="sxs-lookup"><span data-stu-id="56d5b-348">10</span></span>    |

    ![平面の位置とスケールの設定](images/AzureLabs-Lab5-32.png)

    ![平面のシーンビュー](images/AzureLabs-Lab5-33.png)

3.  <span data-ttu-id="56d5b-351">[ *階層] パネル* の空の領域を右クリックし、[ **3d オブジェクト** ] の下に **キューブ** を追加します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-351">Right-click in an empty area of the *Hierarchy Panel* , under **3D Object** , add a **Cube** .</span></span>

    1.  <span data-ttu-id="56d5b-352">キューブの名前を **GazeButton** に変更します (キューブが選択されている状態で、[F2] を押します)。</span><span class="sxs-lookup"><span data-stu-id="56d5b-352">Rename the Cube to **GazeButton** (with the Cube selected, press 'F2').</span></span>

    2.  <span data-ttu-id="56d5b-353">[ *インスペクター] パネル* で、次のパラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-353">Change the following parameters in the *Inspector Panel* :</span></span>

        |       | <span data-ttu-id="56d5b-354">変換-位置</span><span class="sxs-lookup"><span data-stu-id="56d5b-354">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:-----:|
        | <span data-ttu-id="56d5b-355">**X**</span><span class="sxs-lookup"><span data-stu-id="56d5b-355">**X**</span></span> | <span data-ttu-id="56d5b-356">**Y**</span><span class="sxs-lookup"><span data-stu-id="56d5b-356">**Y**</span></span>                | <span data-ttu-id="56d5b-357">**Z**</span><span class="sxs-lookup"><span data-stu-id="56d5b-357">**Z**</span></span> |
        | <span data-ttu-id="56d5b-358">0</span><span class="sxs-lookup"><span data-stu-id="56d5b-358">0</span></span>     | <span data-ttu-id="56d5b-359">3</span><span class="sxs-lookup"><span data-stu-id="56d5b-359">3</span></span>                    | <span data-ttu-id="56d5b-360">5</span><span class="sxs-lookup"><span data-stu-id="56d5b-360">5</span></span>     |


        ![宝石ボタンの変換の設定](images/AzureLabs-Lab5-34.png)

        ![宝石ボタンシーンビュー](images/AzureLabs-Lab5-35.png)

    3.  <span data-ttu-id="56d5b-363">[ **タグ] ドロップダウン** ボタンをクリックし、[ **タグの追加** ] をクリックして [ *タグ & レイヤー] ペイン* を開きます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-363">Click on the **Tag** drop-down button and click on **Add Tag** to open the *Tags & Layers Pane* .</span></span>

        ![新しいタグの追加](images/AzureLabs-Lab5-36.png)

        ![プラスを選択](images/AzureLabs-Lab5-37.png)

    4.  <span data-ttu-id="56d5b-366">**+ (正符号)** ボタンを選択し、[ *新しいタグ名* ] フィールドに「 **GazeButton** 」と入力して、[ **保存** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-366">Select the **+ (plus)** button, and in the *New Tag Name* field, enter **GazeButton** , and press **Save** .</span></span>

        ![新しいタグに名前を付ける](images/AzureLabs-Lab5-38.png)

    5.  <span data-ttu-id="56d5b-368">*階層パネル* で **GazeButton** オブジェクトをクリックし、[ *インスペクター] パネル* で新しく作成された **GazeButton** タグを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-368">Click on the **GazeButton** object in the *Hierarchy Panel* , and in the *Inspector Panel* , assign the newly created **GazeButton** tag.</span></span>

        ![新しいタグを宝石ボタンに割り当てる](images/AzureLabs-Lab5-39.png)

4.  <span data-ttu-id="56d5b-370">[ *階層] パネル* で **GazeButton** オブジェクトを右クリックし、[ **空** のオブジェクト] ( *子* オブジェクトとして追加される) を追加します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-370">Right-click on the **GazeButton** object, in the *Hierarchy Panel* , and add an **Empty GameObject** (which will be added as a *child* object).</span></span>

5.  <span data-ttu-id="56d5b-371">新しいオブジェクトを選択し、名前を **ShapeSpawnPoint** に変更します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-371">Select the new object and rename it **ShapeSpawnPoint** .</span></span>

    1.  <span data-ttu-id="56d5b-372">[ *インスペクター] パネル* で、次のパラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-372">Change the following parameters in the *Inspector Panel* :</span></span>

        |       | <span data-ttu-id="56d5b-373">変換-位置</span><span class="sxs-lookup"><span data-stu-id="56d5b-373">TRANSFORM - POSITION</span></span> |       |
        | :---: | :------------------: |:----: |
        | <span data-ttu-id="56d5b-374">**X**</span><span class="sxs-lookup"><span data-stu-id="56d5b-374">**X**</span></span> |<span data-ttu-id="56d5b-375">**Y**</span><span class="sxs-lookup"><span data-stu-id="56d5b-375">**Y**</span></span>                 | <span data-ttu-id="56d5b-376">**Z**</span><span class="sxs-lookup"><span data-stu-id="56d5b-376">**Z**</span></span> |
        | <span data-ttu-id="56d5b-377">0</span><span class="sxs-lookup"><span data-stu-id="56d5b-377">0</span></span>     | <span data-ttu-id="56d5b-378">-1</span><span class="sxs-lookup"><span data-stu-id="56d5b-378">-1</span></span>                   | <span data-ttu-id="56d5b-379">0</span><span class="sxs-lookup"><span data-stu-id="56d5b-379">0</span></span>     |

        ![図形生成ポイント変換の更新](images/AzureLabs-Lab5-40.png)

        ![シェイプ生成ポイントシーンビュー](images/AzureLabs-Lab5-41.png)

6.  <span data-ttu-id="56d5b-382">次に、Azure サービスの状態に関するフィードバックを提供する **3D テキスト** オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-382">Next you will create a **3D Text** object to provide feedback on the status of the Azure service.</span></span>

    <span data-ttu-id="56d5b-383">階層パネルで **GazeButton** をもう一度右クリックし、 **3d オブジェクト**  >  **3d テキスト** オブジェクトを *子* として追加します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-383">Right click on the **GazeButton** in the Hierarchy Panel again and add a **3D Object** > **3D Text** object as a *child* .</span></span>

    ![新しい3D テキストオブジェクトの作成](images/AzureLabs-Lab5-42.png)

7.  <span data-ttu-id="56d5b-385">**3D テキスト** オブジェクトの名前を **AzureStatusText** に変更します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-385">Rename the **3D Text** object to **AzureStatusText** .</span></span>

8.  <span data-ttu-id="56d5b-386">**AzureStatusText** オブジェクトの変換を次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-386">Change the **AzureStatusText** object Transform as follows:</span></span>

    |       | <span data-ttu-id="56d5b-387">変換-位置</span><span class="sxs-lookup"><span data-stu-id="56d5b-387">TRANSFORM - POSITION</span></span> |       |
    | :---: | :------------------: | :---: |
    | <span data-ttu-id="56d5b-388">**X**</span><span class="sxs-lookup"><span data-stu-id="56d5b-388">**X**</span></span> | <span data-ttu-id="56d5b-389">**Y**</span><span class="sxs-lookup"><span data-stu-id="56d5b-389">**Y**</span></span>                | <span data-ttu-id="56d5b-390">**Z**</span><span class="sxs-lookup"><span data-stu-id="56d5b-390">**Z**</span></span> |
    | <span data-ttu-id="56d5b-391">0</span><span class="sxs-lookup"><span data-stu-id="56d5b-391">0</span></span>     | <span data-ttu-id="56d5b-392">0</span><span class="sxs-lookup"><span data-stu-id="56d5b-392">0</span></span>                    | <span data-ttu-id="56d5b-393">-0.6</span><span class="sxs-lookup"><span data-stu-id="56d5b-393">-0.6</span></span>  |

    |       | <span data-ttu-id="56d5b-394">変換-スケール</span><span class="sxs-lookup"><span data-stu-id="56d5b-394">TRANSFORM - SCALE</span></span> |       |
    | :---: | :---------------: | :---: |
    | <span data-ttu-id="56d5b-395">**X**</span><span class="sxs-lookup"><span data-stu-id="56d5b-395">**X**</span></span> | <span data-ttu-id="56d5b-396">**Y**</span><span class="sxs-lookup"><span data-stu-id="56d5b-396">**Y**</span></span>             | <span data-ttu-id="56d5b-397">**Z**</span><span class="sxs-lookup"><span data-stu-id="56d5b-397">**Z**</span></span> |
    | <span data-ttu-id="56d5b-398">0.1</span><span class="sxs-lookup"><span data-stu-id="56d5b-398">0.1</span></span>   | <span data-ttu-id="56d5b-399">0.1</span><span class="sxs-lookup"><span data-stu-id="56d5b-399">0.1</span></span>               | <span data-ttu-id="56d5b-400">0.1</span><span class="sxs-lookup"><span data-stu-id="56d5b-400">0.1</span></span>   |


    > [!NOTE]
    > <span data-ttu-id="56d5b-401">次のテキストメッシュコンポーネントが更新されたときに修正されるため、センター外であるように見える場合は心配しないでください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-401">Do not worry if it appears to be off-centre, as this will be fixed when the below Text Mesh component is updated.</span></span>

9.  <span data-ttu-id="56d5b-402">次のように **テキストメッシュ** コンポーネントを変更します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-402">Change the **Text Mesh** component to match the below:</span></span>

    ![テキストメッシュコンポーネントの設定](images/AzureLabs-Lab5-43.png)

    > [!TIP]
    > <span data-ttu-id="56d5b-404">ここで選択した色は、16進数の色です。 **000000Ff** でも自由に選択できますが、読み取り可能であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-404">The selected color here is Hex color: **000000FF** , though feel free to choose your own, just ensure it is readable.</span></span>

10. <span data-ttu-id="56d5b-405">階層パネルの構造は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-405">Your Hierarchy Panel structure should now look like this:</span></span>

    ![階層内のテキストメッシュ](images/AzureLabs-Lab5-43b.png)

10. <span data-ttu-id="56d5b-407">シーンは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-407">Your scene should now look like this:</span></span>

    ![シーンビューのテキストメッシュ](images/AzureLabs-Lab5-44.png)


## <a name="chapter-6---import-azure-storage-for-unity"></a><span data-ttu-id="56d5b-409">Chapter 6-Unity 用の Azure Storage のインポート</span><span class="sxs-lookup"><span data-stu-id="56d5b-409">Chapter 6 - Import Azure Storage for Unity</span></span>

<span data-ttu-id="56d5b-410">Azure Storage for Unity を使用します (これ自体が .Net SDK for Azure を利用します)。</span><span class="sxs-lookup"><span data-stu-id="56d5b-410">You will be using Azure Storage for Unity (which itself leverages the .Net SDK for Azure).</span></span> <span data-ttu-id="56d5b-411">詳細については、 [「Unity の Azure Storage](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-411">You can read more about this at the [Azure Storage for Unity article](https://docs.microsoft.com/sandbox/gamedev/unity/azure-storage-unity).</span></span>

<span data-ttu-id="56d5b-412">現在、Unity には、インポート後にプラグインを再構成する必要がある既知の問題があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-412">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="56d5b-413">バグが解決された後、これらの手順 (このセクションでは 4-7) は不要になりました。</span><span class="sxs-lookup"><span data-stu-id="56d5b-413">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="56d5b-414">SDK を独自のプロジェクトにインポートするには、最新の [". unitypackage" を GitHub から](https://aka.ms/azstorage-unitysdk)ダウンロードしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-414">To import the SDK into your own project, make sure you have downloaded the latest ['.unitypackage' from GitHub](https://aka.ms/azstorage-unitysdk).</span></span> <span data-ttu-id="56d5b-415">次に、以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-415">Then, do the following:</span></span>

1.  <span data-ttu-id="56d5b-416">[ **.unitypackage** **Assets**  >  **Import package**  >  **Custom package (カスタムパッケージ** のインポート)] メニューオプションを使用して、unitypackage ファイルを Unity に追加します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-416">Add the **.unitypackage** file to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

2.  <span data-ttu-id="56d5b-417">ポップアップ表示される [ **Unity パッケージのインポート** ] ボックスで、[ **プラグイン** ストレージ] の下のすべてを選択でき  >  **Storage** ます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-417">In the **Import Unity Package** box that pops up, you can select everything under **Plugin** > **Storage** .</span></span> <span data-ttu-id="56d5b-418">このコースでは不要なため、他のすべてをオフにします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-418">Uncheck everything else, as it is not needed for this course.</span></span>

    ![パッケージへのインポート](images/AzureLabs-Lab5-45.png)

3.  <span data-ttu-id="56d5b-420">[ **インポート** ] ボタンをクリックして、プロジェクトに項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-420">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="56d5b-421">[プロジェクト] ビューの [ *プラグイン* ] の下にある *ストレージ* フォルダーにアクセスし、次のプラグイン *のみ* を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-421">Go to the *Storage* folder under *Plugins* , in the Project view, and select the following plugins *only* :</span></span>

    -   <span data-ttu-id="56d5b-422">Microsoft.Data.Edm</span><span class="sxs-lookup"><span data-stu-id="56d5b-422">Microsoft.Data.Edm</span></span>
    -   <span data-ttu-id="56d5b-423">Microsoft.Data.OData</span><span class="sxs-lookup"><span data-stu-id="56d5b-423">Microsoft.Data.OData</span></span>
    -   <span data-ttu-id="56d5b-424">Microsoft.WindowsAzure.Storage</span><span class="sxs-lookup"><span data-stu-id="56d5b-424">Microsoft.WindowsAzure.Storage</span></span>
    -   <span data-ttu-id="56d5b-425">Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="56d5b-425">Newtonsoft.Json</span></span>
    -   <span data-ttu-id="56d5b-426">System.Spatial</span><span class="sxs-lookup"><span data-stu-id="56d5b-426">System.Spatial</span></span>

        ![プラットフォームをすべてオフにする](images/AzureLabs-Lab5-46.png)

5.  <span data-ttu-id="56d5b-428">*これらの特定のプラグイン* を選択した状態で、任意の *プラットフォーム* を **オフ\*\*\*\*にし、** [ *wsaplayer* ]、[ **適用** ] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-428">With *these specific plugins* selected, **uncheck** *Any Platform* and **uncheck** *WSAPlayer* then click **Apply** .</span></span>

    ![プラットフォーム dll を適用する](images/AzureLabs-Lab5-47.png)

    > [!NOTE]
    > <span data-ttu-id="56d5b-430">これらの特定のプラグインを Unity エディターでのみ使用するようにマークしています。</span><span class="sxs-lookup"><span data-stu-id="56d5b-430">We are marking these particular plugins to only be used in the Unity Editor.</span></span> <span data-ttu-id="56d5b-431">これは、プロジェクトが Unity からエクスポートされた後に使用される、WSA フォルダー内に同じプラグインの異なるバージョンがあるためです。</span><span class="sxs-lookup"><span data-stu-id="56d5b-431">This is because there are different versions of the same plugins in the WSA folder that will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="56d5b-432">[ *ストレージ* プラグイン] フォルダーで、[のみ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-432">In the *Storage* plugin folder, select only:</span></span>

    -   <span data-ttu-id="56d5b-433">Microsoft.Data.Services.Client</span><span class="sxs-lookup"><span data-stu-id="56d5b-433">Microsoft.Data.Services.Client</span></span>

        ![dll のプロセスを設定しない](images/AzureLabs-Lab5-48.png)

7.  <span data-ttu-id="56d5b-435">[ *プラットフォームの設定* ] の [ **処理しない** ] チェックボックスをオンにし、[ **適用** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-435">Check the **Don't Process** box under *Platform Settings* and click **Apply** .</span></span>

    ![処理を適用しない](images/AzureLabs-Lab5-49.png)

    > [!NOTE]
    > <span data-ttu-id="56d5b-437">Unity アセンブリ patcher がこのプラグインを処理するのが困難であるため、このプラグインを "処理しない" としてマークしています。</span><span class="sxs-lookup"><span data-stu-id="56d5b-437">We are marking this plugin "Don't process" because the Unity assembly patcher has difficulty processing this plugin.</span></span> <span data-ttu-id="56d5b-438">このプラグインは、処理されていなくても動作します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-438">The plugin will still work even though it is not processed.</span></span>

## <a name="chapter-7---create-the-azureservices-class"></a><span data-ttu-id="56d5b-439">第7章-AzureServices クラスの作成</span><span class="sxs-lookup"><span data-stu-id="56d5b-439">Chapter 7 - Create the AzureServices class</span></span>

<span data-ttu-id="56d5b-440">最初に作成するクラスは、 *Azureservices* クラスです。</span><span class="sxs-lookup"><span data-stu-id="56d5b-440">The first class you are going to create is the *AzureServices* class.</span></span>

<span data-ttu-id="56d5b-441">*Azureservices* クラスは次のことを担当します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-441">The *AzureServices* class will be responsible for:</span></span>

-   <span data-ttu-id="56d5b-442">Azure アカウントの資格情報を保存しています。</span><span class="sxs-lookup"><span data-stu-id="56d5b-442">Storing Azure Account credentials.</span></span>

-   <span data-ttu-id="56d5b-443">Azure アプリ関数を呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="56d5b-443">Calling your Azure App Function.</span></span>

-   <span data-ttu-id="56d5b-444">Azure クラウドストレージ内のデータファイルのアップロードとダウンロード。</span><span class="sxs-lookup"><span data-stu-id="56d5b-444">The upload and download of the data file in your Azure Cloud Storage.</span></span>

<span data-ttu-id="56d5b-445">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="56d5b-445">To create this Class:</span></span>

1.  <span data-ttu-id="56d5b-446">[プロジェクト] パネルの [フォルダーの **作成** ] で、 *アセット* フォルダーを右クリックし  >  **Folder** ます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-446">Right-click in the *Asset* Folder, located in the Project Panel, **Create** > **Folder** .</span></span> <span data-ttu-id="56d5b-447">フォルダーに **スクリプト** の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-447">Name the folder **Scripts** .</span></span>

    ![新しいフォルダーの作成](images/AzureLabs-Lab5-50.png)

    ![呼び出しフォルダー-スクリプト](images/AzureLabs-Lab5-51.png)

2.  <span data-ttu-id="56d5b-450">先ほど作成したフォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-450">Double click on the folder just created, to open it.</span></span>

3.  <span data-ttu-id="56d5b-451">フォルダー内を右クリックし、[C# スクリプトの **作成** ] をクリック  >  **C# Script** します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-451">Right-click inside the folder, **Create** > **C# Script** .</span></span> <span data-ttu-id="56d5b-452">*Azureservices* スクリプトを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-452">Call the script *AzureServices* .</span></span>

4.  <span data-ttu-id="56d5b-453">新しい *Azureservices* クラスをダブルクリックして、 *Visual Studio* で開きます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-453">Double click on the new *AzureServices* class to open it with *Visual Studio* .</span></span>

5.  <span data-ttu-id="56d5b-454">*Azureservices* の先頭に次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-454">Add the following namespaces to the top of the *AzureServices* :</span></span>

    ```csharp
        using System;
        using System.Threading.Tasks;
        using UnityEngine;
        using Microsoft.WindowsAzure.Storage;
        using Microsoft.WindowsAzure.Storage.File;
        using System.IO;
        using System.Net;
    ```

6.  <span data-ttu-id="56d5b-455">*Azureservices* クラス内に次のインスペクターフィールドを追加します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-455">Add the following Inspector Fields inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static AzureServices instance;

        /// <summary>
        /// Reference Target for AzureStatusText Text Mesh object
        /// </summary>
        public TextMesh azureStatusText;
    ```

7.  <span data-ttu-id="56d5b-456">次に、 *Azureservices* クラス内に次のメンバー変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-456">Then add the following member variables inside the *AzureServices* class:</span></span>

    ```csharp
        /// <summary>
        /// Holds the Azure Function endpoint - Insert your Azure Function
        /// Connection String here.
        /// </summary>

        private readonly string azureFunctionEndpoint = "--Insert here you AzureFunction Endpoint--";

        /// <summary>
        /// Holds the Storage Connection String - Insert your Azure Storage
        /// Connection String here.
        /// </summary>
        private readonly string storageConnectionString = "--Insert here you AzureStorage Connection String--";

        /// <summary>
        /// Name of the Cloud Share - Hosts directories.
        /// </summary>
        private const string fileShare = "fileshare";

        /// <summary>
        /// Name of a Directory within the Share
        /// </summary>
        private const string storageDirectory = "storagedirectory";

        /// <summary>
        /// The Cloud File
        /// </summary>
        private CloudFile shapeIndexCloudFile;

        /// <summary>
        /// The Linked Storage Account
        /// </summary>
        private CloudStorageAccount storageAccount;

        /// <summary>
        /// The Cloud Client
        /// </summary>
        private CloudFileClient fileClient;

        /// <summary>
        /// The Cloud Share - Hosts Directories
        /// </summary>
        private CloudFileShare share;

        /// <summary>
        /// The Directory in the share that will host the Cloud file
        /// </summary>
        private CloudFileDirectory dir;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="56d5b-457">*エンドポイント* と *接続文字列* の値は、azure Portal の azure storage の値に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-457">Make sure you replace the *endpoint* and *connection string* values with the values from your Azure storage, found in the Azure Portal</span></span>

8.  <span data-ttu-id="56d5b-458">起動可能な *()* メソッドと *Start ()* メソッドのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-458">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="56d5b-459">これらのメソッドは、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-459">These methods will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            instance = this;
        }

        // Use this for initialization
        private void Start()
        {
            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";
        }

        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {

        }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="56d5b-460">*CallAzureFunctionForNextShape ()* のコードについては、今後の [章](#chapter-10---completing-the-azureservices-class)で説明します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-460">We will fill in the code for *CallAzureFunctionForNextShape()* in a [future Chapter](#chapter-10---completing-the-azureservices-class).</span></span>

9.  <span data-ttu-id="56d5b-461">*Update ()* メソッドは、このクラスでは使用されないため、削除します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-461">Delete the *Update()* method since this class will not use it.</span></span>

10. <span data-ttu-id="56d5b-462">変更内容を Visual Studio に保存し、Unity に戻ります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-462">Save your changes in Visual Studio, and then return to Unity.</span></span>

11. <span data-ttu-id="56d5b-463">[スクリプト] フォルダーの [ *Azureservices* ] クラスをクリックし、[ *階層] パネル* の [メインカメラ] オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-463">Click and drag the *AzureServices* class from the Scripts folder to the Main Camera object in the *Hierarchy Panel* .</span></span>

12. <span data-ttu-id="56d5b-464">メインカメラを選択し、 **GazeButton** オブジェクトの下にある **AzureStatusText** 子オブジェクトを取得します。次に、このオブジェクトを *インスペクター* の **AzureStatusText** reference Target フィールド内に配置して、 *azureservices* スクリプトへの参照を指定します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-464">Select the Main Camera, then grab the **AzureStatusText** child object from beneath the **GazeButton** object, and place it within the **AzureStatusText** reference target field, in the *Inspector* , to provide the reference to the *AzureServices* script.</span></span>

    ![azure 状態テキスト参照ターゲットの割り当て](images/AzureLabs-Lab5-52.png)

## <a name="chapter-8---create-the-shapefactory-class"></a><span data-ttu-id="56d5b-466">章 8-図形ファクトリクラスを作成する</span><span class="sxs-lookup"><span data-stu-id="56d5b-466">Chapter 8 - Create the ShapeFactory class</span></span>

<span data-ttu-id="56d5b-467">次に作成するスクリプトは、 *図形ファクトリ* クラスです。</span><span class="sxs-lookup"><span data-stu-id="56d5b-467">The next script to create, is the *ShapeFactory* class.</span></span> <span data-ttu-id="56d5b-468">このクラスの役割は、要求されたときに新しい図形を作成し、 *図形の履歴リスト* に作成された図形の履歴を保持することです。</span><span class="sxs-lookup"><span data-stu-id="56d5b-468">The role of this class is to create a new shape, when requested, and keep a history of the shapes created in a *Shape History List* .</span></span> <span data-ttu-id="56d5b-469">図形が作成されるたびに、 *Azureservice* クラスで *図形の履歴リスト* が更新され、 *Azure Storage* に格納されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-469">Every time a shape is created, the *Shape History list* is updated in the *AzureService* class, and then stored in your *Azure Storage* .</span></span> <span data-ttu-id="56d5b-470">アプリケーションの起動時に、 *Azure Storage* に格納されているファイルが見つかった場合は、 *図形の履歴リスト* が取得され、再生されます。これには、生成された図形がストレージからのものであるか、新しいものであるかを示す **3d テキスト** オブジェクトがあります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-470">When the application starts, if a stored file is found in your *Azure Storage* , the *Shape History list* is retrieved and replayed, with the **3D Text** object providing whether the generated shape is from storage, or new.</span></span>

<span data-ttu-id="56d5b-471">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="56d5b-471">To create this class:</span></span>

1.  <span data-ttu-id="56d5b-472">前に作成した **Scripts** フォルダーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-472">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="56d5b-473">フォルダー内を右クリックし、[C# スクリプトの **作成** ] をクリック  >  **C# Script** します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-473">Right-click inside the folder, **Create** > **C# Script** .</span></span> <span data-ttu-id="56d5b-474">スクリプト *図形ファクトリ* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-474">Call the script *ShapeFactory* .</span></span>

3.  <span data-ttu-id="56d5b-475">新しい [ *図形ファクトリ* ] スクリプトをダブルクリックして、 *Visual Studio* で開きます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-475">Double click on the new *ShapeFactory* script to open it with *Visual Studio* .</span></span>

4.  <span data-ttu-id="56d5b-476">*図形ファクトリ* クラスに次の名前空間が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-476">Ensure the *ShapeFactory* class includes the following namespaces:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;
    ```

5.  <span data-ttu-id="56d5b-477">次に示す変数を [ *図形ファクトリ* ] クラスに追加し、 *Start ()* 関数と [起動前 *(* )] 関数を次の関数に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-477">Add the variables shown below to the *ShapeFactory* class, and replace the *Start()* and *Awake()* functions with those below:</span></span>

    ```csharp
        /// <summary>
        /// Provide this class Singleton-like behaviour
        /// </summary>
        [HideInInspector]
        public static ShapeFactory instance;

        /// <summary>
        /// Provides an Inspector exposed reference to ShapeSpawnPoint
        /// </summary>
        [SerializeField]
        public Transform spawnPoint;

        /// <summary>
        /// Shape History Index
        /// </summary>
        [HideInInspector]
        public List<int> shapeHistoryList;

        /// <summary>
        /// Shapes Enum for selecting required shape
        /// </summary>
        private enum Shapes { Cube, Sphere, Cylinder }

        private void Awake()
        {
            instance = this;
        }

        private void Start()
        {
            shapeHistoryList = new List<int>();
        }
    ```

6.  <span data-ttu-id="56d5b-478">*CreateShape ()* メソッドは、指定された *整数* パラメーターに基づいて、プリミティブ形状を生成します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-478">The *CreateShape()* method generates the primitive shapes, based upon the provided *integer* parameter.</span></span> <span data-ttu-id="56d5b-479">ブール型パラメーターを使用して、現在作成されている図形がストレージからのものであるか、または新しいものであるかを指定します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-479">The Boolean parameter is used to specify whether the currently created shape is from storage, or new.</span></span> <span data-ttu-id="56d5b-480">次のコードを、前のメソッドの下にある *図形ファクトリ* クラスに配置します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-480">Place the following code in your *ShapeFactory* class, below the previous methods:</span></span>

    ```csharp
        /// <summary>
        /// Use the Shape Enum to spawn a new Primitive object in the scene
        /// </summary>
        /// <param name="shape">Enumerator Number for Shape</param>
        /// <param name="storageShape">Provides whether this is new or old</param>
        internal void CreateShape(int shape, bool storageSpace)
        {
            Shapes primitive = (Shapes)shape;
            GameObject newObject = null;
            string shapeText = storageSpace == true ? "Storage: " : "New: ";

            AzureServices.instance.azureStatusText.text = string.Format("{0}{1}", shapeText, primitive.ToString());

            switch (primitive)
            {
                case Shapes.Cube:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cube);
                break;

                case Shapes.Sphere:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Sphere);
                break;

                case Shapes.Cylinder:
                newObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
                break;
            }

            if (newObject != null)
            {
                newObject.transform.position = spawnPoint.position;

                newObject.transform.localScale = new Vector3(0.5f, 0.5f, 0.5f);

                newObject.AddComponent<Rigidbody>().useGravity = true;

                newObject.GetComponent<Renderer>().material.color = UnityEngine.Random.ColorHSV(0f, 1f, 1f, 1f, 0.5f, 1f);
            }
        }
    ```

7.  <span data-ttu-id="56d5b-481">Unity に戻る前に、変更内容を Visual Studio に保存してください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-481">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

8.  <span data-ttu-id="56d5b-482">Unity エディターに戻り、[ **スクリプト** ] フォルダーの [ *図形ファクトリ* ] クラスをクリックして、[ *階層] パネル* の [ **メインカメラ** ] オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-482">Back in the Unity Editor, click and drag the *ShapeFactory* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel* .</span></span>

9. <span data-ttu-id="56d5b-483">メインカメラを選択すると、[ *図形ファクトリ* スクリプトコンポーネントに *生成ポイント* 参照がありません。</span><span class="sxs-lookup"><span data-stu-id="56d5b-483">With the Main Camera selected you will notice the *ShapeFactory* script component is missing the *Spawn Point* reference.</span></span> <span data-ttu-id="56d5b-484">この問題を解決するには、 **ShapeSpawnPoint** オブジェクトを [ *階層] パネル* から [ **生成ポイント** 参照] ターゲットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-484">To fix it, drag the **ShapeSpawnPoint** object from the *Hierarchy Panel* to the **Spawn Point** reference target.</span></span>

    ![図形ファクトリ参照ターゲットの設定](images/AzureLabs-Lab5-53.png)

## <a name="chapter-9---create-the-gaze-class"></a><span data-ttu-id="56d5b-486">第9章-宝石クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="56d5b-486">Chapter 9 - Create the Gaze class</span></span>

<span data-ttu-id="56d5b-487">作成する必要がある最後のスクリプトは、 *宝石* クラスです。</span><span class="sxs-lookup"><span data-stu-id="56d5b-487">The last script you need to create is the *Gaze* class.</span></span>

<span data-ttu-id="56d5b-488">このクラスは、ユーザーが参照しているオブジェクトを検出するために、メインカメラから投影される **Raycast** を作成します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-488">This class is responsible for creating a **Raycast** that will be projected forward from the Main Camera, to detect which object the user is looking at.</span></span> <span data-ttu-id="56d5b-489">この場合、Raycast は、ユーザーがシーン内の **GazeButton** オブジェクトを調べて動作をトリガーするかどうかを識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-489">In this case, the Raycast will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="56d5b-490">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="56d5b-490">To create this Class:</span></span>

1.  <span data-ttu-id="56d5b-491">前に作成した **Scripts** フォルダーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-491">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="56d5b-492">[プロジェクト] パネル内を右クリック **Create** し、[  >  **C# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-492">Right-click in the Project Panel, **Create** > **C# Script** .</span></span> <span data-ttu-id="56d5b-493">スクリプトを *見つめ* て呼び出します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-493">Call the script *Gaze* .</span></span>

3.  <span data-ttu-id="56d5b-494">新しい *宝石* のスクリプトをダブルクリックして、 *Visual Studio で開きます。*</span><span class="sxs-lookup"><span data-stu-id="56d5b-494">Double click on the new *Gaze* script to open it with *Visual Studio.*</span></span>

4.  <span data-ttu-id="56d5b-495">スクリプトの先頭に次の名前空間が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-495">Ensure the following namespace is included at the top of the script:</span></span>

    ```csharp
        using UnityEngine;
    ```

5.  <span data-ttu-id="56d5b-496">次に、次の変数を、 *宝石* クラス内に追加します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-496">Then add the following variables inside the *Gaze* class:</span></span>

    ```csharp
        /// <summary>
        /// Provides Singleton-like behavior to this class.
        /// </summary>
        public static Gaze instance;

        /// <summary>
        /// The Tag which the Gaze will use to interact with objects. Can also be set in editor.
        /// </summary>
        public string InteractibleTag = "GazeButton";

        /// <summary>
        /// The layer which will be detected by the Gaze ('~0' equals everything).
        /// </summary>
        public LayerMask LayerMask = ~0;

        /// <summary>
        /// The Max Distance the gaze should travel, if it has not hit anything.
        /// </summary>
        public float GazeMaxDistance = 300;

        /// <summary>
        /// The size of the cursor, which will be created.
        /// </summary>
        public Vector3 CursorSize = new Vector3(0.05f, 0.05f, 0.05f);

        /// <summary>
        /// The color of the cursor - can be set in editor.
        /// </summary>
        public Color CursorColour = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);

        /// <summary>
        /// Provides when the gaze is ready to start working (based upon whether
        /// Azure connects successfully).
        /// </summary>
        internal bool GazeEnabled = false;

        /// <summary>
        /// The currently focused object.
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        /// <summary>
        /// The object which was last focused on.
        /// </summary>
        internal GameObject _oldFocusedObject { get; private set; }

        /// <summary>
        /// The info taken from the last hit.
        /// </summary>
        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// The cursor object.
        /// </summary>
        internal GameObject Cursor { get; private set; }

        /// <summary>
        /// Provides whether the raycast has hit something.
        /// </summary>
        internal bool Hit { get; private set; }

        /// <summary>
        /// This will store the position which the ray last hit.
        /// </summary>
        internal Vector3 Position { get; private set; }

        /// <summary>
        /// This will store the normal, of the ray from its last hit.
        /// </summary>
        internal Vector3 Normal { get; private set; }

        /// <summary>
        /// The start point of the gaze ray cast.
        /// </summary>
        private Vector3 _gazeOrigin;

        /// <summary>
        /// The direction in which the gaze should be.
        /// </summary>
        private Vector3 _gazeDirection;
    ```

> [!IMPORTANT]
> <span data-ttu-id="56d5b-497">これらの変数のいくつかは、 *エディター* で編集できます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-497">Some of these variables will be able to be edited in the *Editor* .</span></span>

6.  <span data-ttu-id="56d5b-498">起動可能な *()* メソッドと *Start ()* メソッドのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-498">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span>

    ```csharp
        /// <summary>
        /// The method used after initialization of the scene, though before Start().
        /// </summary>
        private void Awake()
        {
            // Set this class to behave similar to singleton
            instance = this;
        }

        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        private void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="56d5b-499">次のコードを追加します。このコードは、start に cursor オブジェクトを作成し、 *Update ()* メソッドを実行します。このメソッドは、Raycast メソッドを実行します。このメソッドは、GazeEnabled ブール値が切り替えられる場所になります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-499">Add the following code, which will create a cursor object at start, along with the *Update()* method, which will run the Raycast method, along with being where the GazeEnabled boolean is toggled:</span></span>

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        /// <returns></returns>
        private GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);

            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = CursorSize;

            newCursor.GetComponent<MeshRenderer>().material = new Material(Shader.Find("Diffuse"))
            {
                color = CursorColour
            };

            newCursor.name = "Cursor";

            newCursor.SetActive(true);

            return newCursor;
        }

        /// <summary>
        /// Called every frame
        /// </summary>
        private void Update()
        {
            if(GazeEnabled == true)
            {
                _gazeOrigin = Camera.main.transform.position;

                _gazeDirection = Camera.main.transform.forward;

                UpdateRaycast();
            }
        }
    ```

8. <span data-ttu-id="56d5b-500">次に、 *UpdateRaycast ()* メソッドを追加します。これにより、Raycast が射影され、ヒットターゲットが検出されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-500">Next add the *UpdateRaycast()* method, which will project a Raycast and detect the hit target.</span></span>

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;

            RaycastHit hitInfo;

            // Initialise Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance, LayerMask);

            HitInfo = hitInfo;

            // Check whether raycast has hit.
            if (Hit == true)
            {
                Position = hitInfo.point;

                Normal = hitInfo.normal;

                // Check whether the hit has a collider.
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at.
                    FocusedObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null.
                    FocusedObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedObject = null;

                // Provide default position for cursor.
                Position = _gazeOrigin + (_gazeDirection * GazeMaxDistance);

                // Provide a default normal.
                Normal = _gazeDirection;
            }

            // Lerp the cursor to the given position, which helps to stabilize the gaze.
            Cursor.transform.position = Vector3.Lerp(Cursor.transform.position, Position, 0.6f);

            // Check whether the previous focused object is this same 
            //    object. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();

                if (FocusedObject != null)
                {
                if (FocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                        // Set the Focused object to green - success!
                        FocusedObject.GetComponent<Renderer>().material.color = Color.green;

                        // Start the Azure Function, to provide the next shape!
                        AzureServices.instance.CallAzureFunctionForNextShape();
                    }
                }
            }
        }
    ```

9. <span data-ttu-id="56d5b-501">最後に、 *ResetFocusedObject ()* メソッドを追加します。これにより、新しい図形を作成しているかどうかを示す、GazeButton オブジェクトの現在の色が切り替わります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-501">Lastly, add the *ResetFocusedObject()* method, which will toggle the GazeButton objects current color, indicating whether it is creating a new shape or not.</span></span>

    ```csharp
        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag.ToString()))
                {
                    // Set the old focused object to red - its original state.
                    _oldFocusedObject.GetComponent<Renderer>().material.color = Color.red;
                }
            }
        }
    ```

10.  <span data-ttu-id="56d5b-502">Unity に戻る前に、変更を Visual Studio に保存します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-502">Save your changes in Visual Studio before returning to Unity.</span></span>

11.  <span data-ttu-id="56d5b-503">[スクリプト] フォルダーから、[ *階層] パネル* の [ **メインカメラ** ] オブジェクトに、 *見つめ* クラスをクリックしてドラッグします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-503">Click and drag the *Gaze* class from the Scripts folder to the **Main Camera** object in the *Hierarchy Panel* .</span></span>

## <a name="chapter-10---completing-the-azureservices-class"></a><span data-ttu-id="56d5b-504">第10章-AzureServices クラスの完成</span><span class="sxs-lookup"><span data-stu-id="56d5b-504">Chapter 10 - Completing the AzureServices class</span></span>

<span data-ttu-id="56d5b-505">他のスクリプトが配置されたので、 *Azureservices* クラスを *完了* できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="56d5b-505">With the other scripts in place, it is now possible to *complete* the *AzureServices* class.</span></span> <span data-ttu-id="56d5b-506">これは、次の方法で実現されます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-506">This will be achieved through:</span></span>

1.  <span data-ttu-id="56d5b-507">*CreateCloudIdentityAsync ()* という名前の新しいメソッドを追加して、Azure との通信に必要な認証変数を設定します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-507">Adding a new method named *CreateCloudIdentityAsync()* , to set up the authentication variables needed for communicating with Azure.</span></span>

    > <span data-ttu-id="56d5b-508">また、このメソッドは、シェイプリストを含む以前に格納されたファイルの存在を確認します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-508">This method will also check for the existence of a previously stored File containing the Shape List.</span></span>
    >
    > <span data-ttu-id="56d5b-509">**ファイルが見つかった場合** は、 **Azure Storage ファイル** に格納されている図形のパターンに従って、ユーザーが *宝石* を無効にし、図形の作成をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-509">**If the file is found** , it will disable the user *Gaze* , and trigger Shape creation, according to the pattern of shapes, as stored in the **Azure Storage file** .</span></span> <span data-ttu-id="56d5b-510">**テキストメッシュ** によって ' Storage ' または ' New ' と表示されるのは、図形の原点によって異なります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-510">The user can see this, as the **Text Mesh** will provide display 'Storage' or 'New', depending on the shapes origin.</span></span>
    >
    > <span data-ttu-id="56d5b-511">**ファイルが見つからない場合** は、ユーザーがシーン内の **GazeButton** オブジェクトを見ているときに図形を作成できるよう *にします* 。</span><span class="sxs-lookup"><span data-stu-id="56d5b-511">**If no file is found** , it will enable the *Gaze* , enabling the user to create shapes when looking at the **GazeButton** object in the scene.</span></span>

    ```csharp
        /// <summary>
        /// Create the references necessary to log into Azure
        /// </summary>
        private async void CreateCloudIdentityAsync()
        {
            // Retrieve storage account information from connection string
            storageAccount = CloudStorageAccount.Parse(storageConnectionString);

            // Create a file client for interacting with the file service.
            fileClient = storageAccount.CreateCloudFileClient();

            // Create a share for organizing files and directories within the storage account.
            share = fileClient.GetShareReference(fileShare);

            await share.CreateIfNotExistsAsync();

            // Get a reference to the root directory of the share.
            CloudFileDirectory root = share.GetRootDirectoryReference();

            // Create a directory under the root directory
            dir = root.GetDirectoryReference(storageDirectory);

            await dir.CreateIfNotExistsAsync();

            //Check if the there is a stored text file containing the list
            shapeIndexCloudFile = dir.GetFileReference("TextShapeFile");

            if (!await shapeIndexCloudFile.ExistsAsync())
            {
                // File not found, enable gaze for shapes creation
                Gaze.instance.GazeEnabled = true;

                azureStatusText.text = "No Shape\nFile!";
            }
            else
            {
                // The file has been found, disable gaze and get the list from the file
                Gaze.instance.GazeEnabled = false;

                azureStatusText.text = "Shape File\nFound!";

                await ReplicateListFromAzureAsync();
            }
        }
    ```

2.  <span data-ttu-id="56d5b-512">次のコードスニペットは、 *Start ()* メソッド内からのものです。 *CreateCloudIdentityAsync ()* メソッドに対して呼び出しが行われます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-512">The next code snippet is from within the *Start()* method; wherein a call will be made to the *CreateCloudIdentityAsync()* method.</span></span> <span data-ttu-id="56d5b-513">次のようにして、現在の *Start ()* メソッドを自由にコピーしてください。</span><span class="sxs-lookup"><span data-stu-id="56d5b-513">Feel free to copy over your current *Start()* method, with the below:</span></span>

    ```csharp
        private void Start()
        {
            // Disable TLS cert checks only while in Unity Editor (until Unity adds support for TLS)
    #if UNITY_EDITOR
            ServicePointManager.ServerCertificateValidationCallback = delegate { return true; };
    #endif

            // Set the Status text to loading, whilst attempting connection to Azure.
            azureStatusText.text = "Loading...";

            //Creating the references necessary to log into Azure and check if the Storage Directory is empty
            CreateCloudIdentityAsync();
        }
    ```

3.  <span data-ttu-id="56d5b-514">*CallAzureFunctionForNextShape ()* メソッドのコードを入力します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-514">Fill in the code for the method *CallAzureFunctionForNextShape()* .</span></span> <span data-ttu-id="56d5b-515">以前に作成した *Azure Function App* を使用して、図形のインデックスを要求します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-515">You will use the previously created *Azure Function App* to request a shape index.</span></span> <span data-ttu-id="56d5b-516">新しい図形を受け取ると、このメソッドは図形をシェイプトゥイーン *ファクトリ* クラスに送信して、シーンに新しい図形を作成します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-516">Once the new shape is received, this method will send the shape to the *ShapeFactory* class to create the new shape in the scene.</span></span> <span data-ttu-id="56d5b-517">次のコードを使用して、 *CallAzureFunctionForNextShape ()* の本文を完成させます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-517">Use the code below to complete the body of *CallAzureFunctionForNextShape()* .</span></span>

    ```csharp
        /// <summary>
        /// Call to the Azure Function App to request a Shape.
        /// </summary>
        public async void CallAzureFunctionForNextShape()
        {
            int azureRandomInt = 0;

            // Call Azure function
            HttpWebRequest webRequest = WebRequest.CreateHttp(azureFunctionEndpoint);

            WebResponse response = await webRequest.GetResponseAsync();

            // Read response as string
            using (Stream stream = response.GetResponseStream())
            {
                StreamReader reader = new StreamReader(stream);

                String responseString = reader.ReadToEnd();

                //parse result as integer
                Int32.TryParse(responseString, out azureRandomInt);
            }

            //add random int from Azure to the ShapeIndexList
            ShapeFactory.instance.shapeHistoryList.Add(azureRandomInt);

            ShapeFactory.instance.CreateShape(azureRandomInt, false);

            //Save to Azure storage
            await UploadListToAzureAsync();
        }
    ```

4.  <span data-ttu-id="56d5b-518">図形の履歴リストに格納されている整数を連結して、 *Azure Storage ファイル* に保存することにより、文字列を作成するメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-518">Add a method to create a string, by concatenating the integers stored in the shape history list, and saving it in your *Azure Storage File* .</span></span>

    ```csharp
        /// <summary>
        /// Upload the locally stored List to Azure
        /// </summary>
        private async Task UploadListToAzureAsync()
        {
            // Uploading a local file to the directory created above
            string listToString = string.Join(",", ShapeFactory.instance.shapeHistoryList.ToArray());

            await shapeIndexCloudFile.UploadTextAsync(listToString);
        }
    ```

5.  <span data-ttu-id="56d5b-519">*Azure Storage ファイル* にあるファイルに格納されているテキストを取得し、それをリストに *逆シリアル* 化するメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-519">Add a method to retrieve the text stored in the file located in your *Azure Storage File* and *deserialize* it into a list.</span></span>

6.  <span data-ttu-id="56d5b-520">このプロセスが完了すると、メソッドは、ユーザーがシーンに図形を追加できるように、宝石を再び有効にします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-520">Once this process is completed, the method re-enables the gaze so that the user can add more shapes to the scene.</span></span>

    ```csharp
        ///<summary>
        /// Get the List stored in Azure and use the data retrieved to replicate 
        /// a Shape creation pattern
        ///</summary>
        private async Task ReplicateListFromAzureAsync()
        {
            string azureTextFileContent = await shapeIndexCloudFile.DownloadTextAsync();

            string[] shapes = azureTextFileContent.Split(new char[] { ',' });

            foreach (string shape in shapes)
            {
                int i;

                Int32.TryParse(shape.ToString(), out i);

                ShapeFactory.instance.shapeHistoryList.Add(i);

                ShapeFactory.instance.CreateShape(i, true);

                await Task.Delay(500);
            }

            Gaze.instance.GazeEnabled = true;

            azureStatusText.text = "Load Complete!";
        }
    ```

7.  <span data-ttu-id="56d5b-521">Unity に戻る前に、変更を Visual Studio に保存します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-521">Save your changes in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-11---build-the-uwp-solution"></a><span data-ttu-id="56d5b-522">第11章-UWP ソリューションのビルド</span><span class="sxs-lookup"><span data-stu-id="56d5b-522">Chapter 11 - Build the UWP Solution</span></span>

<span data-ttu-id="56d5b-523">ビルドプロセスを開始するには:</span><span class="sxs-lookup"><span data-stu-id="56d5b-523">To begin the Build process:</span></span>

1.  <span data-ttu-id="56d5b-524">ファイルの **File**  >  **ビルド設定** にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-524">Go to **File** > **Build Settings** .</span></span>

    ![アプリをビルドする](images/AzureLabs-Lab5-54.png)

2.  <span data-ttu-id="56d5b-526">[ **ビルド** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-526">Click **Build** .</span></span> <span data-ttu-id="56d5b-527">Unity は *エクスプローラー* ウィンドウを起動します。このウィンドウでは、アプリを作成するフォルダーを作成して選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-527">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="56d5b-528">ここでそのフォルダーを作成し、「 *App* 」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-528">Create that folder now, and name it *App* .</span></span> <span data-ttu-id="56d5b-529">次に、 *アプリ* フォルダーを選択し、 **[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-529">Then with the *App* folder selected, press **Select Folder** .</span></span>

3.  <span data-ttu-id="56d5b-530">Unity は、 *アプリ* フォルダーへのプロジェクトのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-530">Unity will begin building your project to the *App* folder.</span></span>

4.  <span data-ttu-id="56d5b-531">Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で *ファイルエクスプローラー* ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。</span><span class="sxs-lookup"><span data-stu-id="56d5b-531">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploying-your-application"></a><span data-ttu-id="56d5b-532">第12章-アプリケーションのデプロイ</span><span class="sxs-lookup"><span data-stu-id="56d5b-532">Chapter 12 - Deploying your application</span></span>

<span data-ttu-id="56d5b-533">アプリケーションをデプロイするには:</span><span class="sxs-lookup"><span data-stu-id="56d5b-533">To deploy your application:</span></span>

1.  <span data-ttu-id="56d5b-534">[最後の章](#chapter-11---build-the-uwp-solution)で作成した *アプリ* フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-534">Navigate to the *App* folder which was created in the [last Chapter](#chapter-11---build-the-uwp-solution).</span></span> <span data-ttu-id="56d5b-535">アプリ名を含むファイルが表示されます。この拡張子は ".sln" で、ダブルクリックして *Visual Studio* 内で開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-535">You will see a file with your apps name, with the '.sln' extension, which you should double-click, so to open it within *Visual Studio* .</span></span>

2.  <span data-ttu-id="56d5b-536">**ソリューションプラットフォーム** で、[ **X86, ローカルコンピューター** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-536">In the **Solution Platform** , select **x86, Local Machine** .</span></span>

3.  <span data-ttu-id="56d5b-537">**ソリューション構成** で、[ **デバッグ** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-537">In the **Solution Configuration** select **Debug** .</span></span>

    > <span data-ttu-id="56d5b-538">Microsoft HoloLens の場合、これを *リモートコンピューター* に設定する方が簡単な場合があります。これにより、コンピューターにテザリングさされることはありません。</span><span class="sxs-lookup"><span data-stu-id="56d5b-538">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine* , so that you are not tethered to your computer.</span></span> <span data-ttu-id="56d5b-539">ただし、次の手順も実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-539">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="56d5b-540">HoloLens の **IP アドレス** を確認します。これは、[ **設定**  >  ] [ **ネットワーク & [インターネット**  >  **wi-fi**  >  **詳細オプション]** にあります。 IPv4 は使用するアドレスです。</span><span class="sxs-lookup"><span data-stu-id="56d5b-540">Know the **IP Address** of your HoloLens, which can be found within the **Settings** > **Network & Internet** > **Wi-Fi** > **Advanced Options** ; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="56d5b-541">**開発者モード** が **オンに** なっていることを確認します。「 **設定** の更新」で、  >  開発者向けの **セキュリティ & セキュリティ** が見つかりました  >  **For developers** 。</span><span class="sxs-lookup"><span data-stu-id="56d5b-541">Ensure **Developer Mode** is **On** ; found in **Settings** > **Update & Security** > **For developers** .</span></span>

    ![ソリューションの配置](images/AzureLabs-Lab5-55.png)

4.  <span data-ttu-id="56d5b-543">[ **ビルド** ] メニューの [ソリューションの **配置** ] をクリックして、アプリケーションをコンピューターにサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-543">Go to the **Build** menu and click on **Deploy Solution** to sideload the application to your machine.</span></span>

5.  <span data-ttu-id="56d5b-544">インストールされているアプリの一覧にアプリが表示され、起動してテストできる状態になります。</span><span class="sxs-lookup"><span data-stu-id="56d5b-544">Your App should now appear in the list of installed apps, ready to be launched and tested!</span></span>

## <a name="your-finished-azure-functions-and-storage-application"></a><span data-ttu-id="56d5b-545">完成した Azure Functions およびストレージアプリケーション</span><span class="sxs-lookup"><span data-stu-id="56d5b-545">Your finished Azure Functions and Storage Application</span></span>

<span data-ttu-id="56d5b-546">これで、Azure Functions と Azure Storage の両方のサービスを活用する mixed reality アプリが作成されました。</span><span class="sxs-lookup"><span data-stu-id="56d5b-546">Congratulations, you built a mixed reality app that leverages both the Azure Functions and Azure Storage services.</span></span> <span data-ttu-id="56d5b-547">アプリは、格納されているデータを描画し、そのデータに基づいてアクションを提供できます。</span><span class="sxs-lookup"><span data-stu-id="56d5b-547">Your app will be able to draw on stored data, and provide an action based on that data.</span></span>

![最終製品-終了](images/AzureLabs-Lab5-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="56d5b-549">ボーナス演習</span><span class="sxs-lookup"><span data-stu-id="56d5b-549">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="56d5b-550">演習1</span><span class="sxs-lookup"><span data-stu-id="56d5b-550">Exercise 1</span></span>

<span data-ttu-id="56d5b-551">オブジェクトが作成されたポイントを生成する2番目の生成ポイントとレコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-551">Create a second spawn point and record which spawn point an object was created from.</span></span> <span data-ttu-id="56d5b-552">データファイルを読み込むときに、最初に作成された場所から生成された図形を再生します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-552">When you load the data file, replay the shapes being spawned from the location they originally were created.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="56d5b-553">演習2</span><span class="sxs-lookup"><span data-stu-id="56d5b-553">Exercise 2</span></span>

<span data-ttu-id="56d5b-554">毎回アプリケーションを再起動するのではなく、アプリを再起動する方法を作成します。</span><span class="sxs-lookup"><span data-stu-id="56d5b-554">Create a way to restart the app, rather than having to re-open it each time.</span></span> <span data-ttu-id="56d5b-555">**読み込みシーン** は、開始するのに適しています。</span><span class="sxs-lookup"><span data-stu-id="56d5b-555">**Loading Scenes** is a good spot to start.</span></span> <span data-ttu-id="56d5b-556">その後、 *Azure Storage* で格納されている一覧をクリアする方法を作成して、アプリから簡単にリセットできるようにします。</span><span class="sxs-lookup"><span data-stu-id="56d5b-556">After doing that, create a way to clear the stored list in *Azure Storage* , so that it can be easily reset from your app.</span></span> 
