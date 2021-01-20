---
title: MR と Azure 306 - ビデオのストリーミング
description: このコースでは、mixed reality アプリケーション内で Azure Media Services を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、media services、streaming video、360、イマーシブ、vr、Windows 10、Visual Studio
ms.openlocfilehash: 3a0401b7503d8a783ba529cf24cdf6cc55c88311
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583458"
---
# <a name="mr-and-azure-306-streaming-video"></a><span data-ttu-id="43699-104">MR と Azure 306:ビデオのストリーム配信</span><span class="sxs-lookup"><span data-stu-id="43699-104">MR and Azure 306: Streaming video</span></span>

<br>

>[!NOTE]
><span data-ttu-id="43699-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="43699-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="43699-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="43699-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="43699-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。</span><span class="sxs-lookup"><span data-stu-id="43699-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="43699-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="43699-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="43699-109">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="43699-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="43699-110">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="43699-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br> 

<span data-ttu-id="43699-111">![最終的な製品の開始- ](images/AzureLabs-Lab6-00.png)
 ![ 開始](images/AzureLabs-Lab6-01.png)</span><span class="sxs-lookup"><span data-stu-id="43699-111">![final product -start](images/AzureLabs-Lab6-00.png)
![final product -start](images/AzureLabs-Lab6-01.png)</span></span>

<span data-ttu-id="43699-112">このコースでは、Azure Media Services を Windows Mixed Reality VR エクスペリエンスに接続して、イマーシブヘッドセットでのストリーミング360度のビデオ再生を許可する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="43699-112">In this course you will learn how connect your Azure Media Services to a Windows Mixed Reality VR experience to allow streaming 360 degree video playback on immersive headsets.</span></span> 

<span data-ttu-id="43699-113">**Azure Media Services** は、今日の最も人気のあるモバイルデバイスで、より多くのユーザーに配信するためのブロードキャスト品質のビデオストリーミングサービスを提供するサービスのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="43699-113">**Azure Media Services** are a collection of services that gives you broadcast-quality video streaming services to reach larger audiences on today’s most popular mobile devices.</span></span> <span data-ttu-id="43699-114">詳細については、 [Azure Media Services のページ](https://azure.microsoft.com/services/media-services)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43699-114">For more information, visit the [Azure Media Services page](https://azure.microsoft.com/services/media-services).</span></span>

<span data-ttu-id="43699-115">このコースを完了すると、mixed reality イマーシブヘッドセットアプリケーションが完成します。これにより、次のことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="43699-115">Having completed this course, you will have a mixed reality immersive headset application, which will be able to do the following:</span></span>

1. <span data-ttu-id="43699-116">**Azure Media Service** を使用して、 **Azure Storage** から360度のビデオを取得します。</span><span class="sxs-lookup"><span data-stu-id="43699-116">Retrieve a 360 degree video from an **Azure Storage**, through the **Azure Media Service**.</span></span>

2. <span data-ttu-id="43699-117">Unity シーン内で取得した360度ビデオを表示します。</span><span class="sxs-lookup"><span data-stu-id="43699-117">Display the retrieved 360 degree video within a Unity scene.</span></span>

3. <span data-ttu-id="43699-118">2つの異なるビデオを使用して、2つのシーン間を移動します。</span><span class="sxs-lookup"><span data-stu-id="43699-118">Navigate between two scenes, with two different videos.</span></span>

<span data-ttu-id="43699-119">アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。</span><span class="sxs-lookup"><span data-stu-id="43699-119">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="43699-120">このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="43699-120">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="43699-121">このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。</span><span class="sxs-lookup"><span data-stu-id="43699-121">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="43699-122">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="43699-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="43699-123">コース</span><span class="sxs-lookup"><span data-stu-id="43699-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="43699-124"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="43699-124"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="43699-125"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="43699-125"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="43699-126">MR と Azure 306:ビデオのストリーム配信</span><span class="sxs-lookup"><span data-stu-id="43699-126">MR and Azure 306: Streaming video</span></span></td><td style="text-align: center;"> </td><td style="text-align: center;"> <span data-ttu-id="43699-127">✔️</span><span class="sxs-lookup"><span data-stu-id="43699-127">✔️</span></span></td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="43699-128">前提条件</span><span class="sxs-lookup"><span data-stu-id="43699-128">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="43699-129">このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="43699-129">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="43699-130">また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証されたものを表します (2018 年5月)。</span><span class="sxs-lookup"><span data-stu-id="43699-130">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="43699-131">[「ツールのインストール](../../install-the-tools.md)」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものよりも新しいソフトウェアで見つかったものと完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="43699-131">You are free to use the latest software, as listed within the [install the tools article](../../install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="43699-132">このコースでは、次のハードウェアとソフトウェアをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="43699-132">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="43699-133">開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="43699-133">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="43699-134">開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="43699-134">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="43699-135">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="43699-135">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="43699-136">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="43699-136">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="43699-137">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="43699-137">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="43699-138">[Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="43699-138">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md)</span></span>
- <span data-ttu-id="43699-139">Azure のセットアップとデータ取得のためのインターネットアクセス</span><span class="sxs-lookup"><span data-stu-id="43699-139">Internet access for Azure setup and data retrieval</span></span>
- <span data-ttu-id="43699-140">2 360-mp4 形式のビデオ ( [このダウンロードページに](https://www.mettle.com/360vr-master-series-free-360-downloads-page)は、ロイヤリティフリーのビデオが掲載される場合があります)</span><span class="sxs-lookup"><span data-stu-id="43699-140">Two 360-degree videos in mp4 format (you can find some royalty-free videos [at this download page](https://www.mettle.com/360vr-master-series-free-360-downloads-page))</span></span>

## <a name="before-you-start"></a><span data-ttu-id="43699-141">開始する前に</span><span class="sxs-lookup"><span data-stu-id="43699-141">Before you start</span></span>

1.  <span data-ttu-id="43699-142">このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="43699-142">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="43699-143">Mixed Reality のイマーシブヘッドセットをセットアップしてテストします。</span><span class="sxs-lookup"><span data-stu-id="43699-143">Set up and test your Mixed Reality Immersive Headset.</span></span>

    > [!NOTE]
    > <span data-ttu-id="43699-144">このコースでは、モーションコントローラーは必要 **ありません** 。</span><span class="sxs-lookup"><span data-stu-id="43699-144">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="43699-145">イマーシブヘッドセットの設定をサポートする必要がある場合は、 [Windows Mixed Reality のセットアップ方法に関するリンク](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="43699-145">If you need support setting up the Immersive Headset, please click [link on how to set up Windows Mixed Reality](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

## <a name="chapter-1---the-azure-portal-creating-the-azure-storage-account"></a><span data-ttu-id="43699-146">章 1-Azure Portal: Azure Storage アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="43699-146">Chapter 1 - The Azure Portal: creating the Azure Storage Account</span></span>

<span data-ttu-id="43699-147">**Azure Storage サービス** を使用するには、Azure portal で **ストレージアカウント** を作成し、構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-147">To use the **Azure Storage Service**, you will need to create and configure a **Storage Account** in the Azure portal.</span></span>

1.  <span data-ttu-id="43699-148">[Azure Portal](https://portal.azure.com) にログインします。</span><span class="sxs-lookup"><span data-stu-id="43699-148">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="43699-149">まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-149">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="43699-150">このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。</span><span class="sxs-lookup"><span data-stu-id="43699-150">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="43699-151">ログインしたら、左側のメニューの [ **ストレージアカウント** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-151">Once you are logged in, click on **Storage accounts** in the left menu.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-02.png)

3.  <span data-ttu-id="43699-153">[ **ストレージアカウント** ] タブで、[ **追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-153">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-03.png)

4.  <span data-ttu-id="43699-155">[ **ストレージアカウントの作成** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="43699-155">In the **Create storage account** tab:</span></span>

    1.  <span data-ttu-id="43699-156">アカウントの **名前** を挿入します。このフィールドには数字と小文字のみを使用できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="43699-156">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>

    2.  <span data-ttu-id="43699-157">[ **デプロイモデル] で、** [ **リソースマネージャー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="43699-157">For **Deployment model,** select **Resource manager**.</span></span>

    3.  <span data-ttu-id="43699-158">[ **アカウントの種類**] で、[ **ストレージ (汎用 v1)**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="43699-158">For **Account kind**, select **Storage (general purpose v1)**.</span></span>

    4.  <span data-ttu-id="43699-159">[ **パフォーマンス**] で [標準] \* を選択し **ます。**</span><span class="sxs-lookup"><span data-stu-id="43699-159">For **Performance**, select **Standard\*.**</span></span>

    5.  <span data-ttu-id="43699-160">**レプリケーション** の場合は **、[ローカル冗長ストレージ (LRS)**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="43699-160">For **Replication** select **Locally-redundant storage (LRS)**.</span></span>

    6.  <span data-ttu-id="43699-161">**安全な転送** は無効のまま **に** しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-161">Leave **Secure transfer required** as **Disabled**.</span></span>

    7.  <span data-ttu-id="43699-162">**サブスクリプション** を選択します。</span><span class="sxs-lookup"><span data-stu-id="43699-162">Select a **Subscription**.</span></span>

    8.  <span data-ttu-id="43699-163">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="43699-163">Choose a **Resource group** or create a new one.</span></span> <span data-ttu-id="43699-164">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="43699-164">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span>

    9.  <span data-ttu-id="43699-165">リソースグループの **場所** を決定します (新しいリソースグループを作成している場合)。</span><span class="sxs-lookup"><span data-stu-id="43699-165">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="43699-166">この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="43699-166">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="43699-167">一部の Azure 資産は、特定のリージョンでのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="43699-167">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="43699-168">このサービスに適用されている使用条件を理解していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-168">You will need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-04.png)

6.  <span data-ttu-id="43699-170">[ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="43699-170">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="43699-171">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-171">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab6-05.png)

8.  <span data-ttu-id="43699-173">この時点で、リソースに従う必要はありません。次の章に移動するだけです。</span><span class="sxs-lookup"><span data-stu-id="43699-173">At this point you do not need to follow the resource, simply move to the next Chapter.</span></span>

## <a name="chapter-2---the-azure-portal-creating-the-media-service"></a><span data-ttu-id="43699-174">章 2-Azure Portal: メディアサービスの作成</span><span class="sxs-lookup"><span data-stu-id="43699-174">Chapter 2 - The Azure Portal: creating the Media Service</span></span>

<span data-ttu-id="43699-175">Azure Media Service を使用するには、アプリケーションで使用できるようにサービスのインスタンスを構成する必要があります (アカウント所有者は管理者である必要があります)。</span><span class="sxs-lookup"><span data-stu-id="43699-175">To use the Azure Media Service, you will need to configure an instance of the service to be made available to your application (wherein the account holder needs to be an Admin).</span></span>

1.  <span data-ttu-id="43699-176">Azure Portal で、左上隅にある [ **リソースの作成** ] をクリックし、[ **メディアサービス]** を検索して、 **enter** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="43699-176">In the Azure Portal, click on **Create a resource** in the top left corner, and search for **Media Service,** press **Enter**.</span></span> <span data-ttu-id="43699-177">現在必要なリソースにはピンク色のアイコンが付いています。新しいページを表示するには、これをクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-177">The resource you want currently has a pink icon; click this, to show a new page.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-06.png)

2.  <span data-ttu-id="43699-179">新しいページには、 **メディアサービス** の説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-179">The new page will provide a description of the **Media Service**.</span></span> <span data-ttu-id="43699-180">このプロンプトの左下にある [ **作成** ] ボタンをクリックして、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="43699-180">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-07.png)

3.  <span data-ttu-id="43699-182">[ **作成** ] をクリックすると、新しいメディアサービスに関する詳細を指定する必要があるパネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-182">Once you have clicked on **Create** a panel will appear where you need to provide some details about your new Media Service:</span></span>

    1.  <span data-ttu-id="43699-183">このサービスインスタンスに必要な **アカウント名** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="43699-183">Insert your desired **Account Name** for this service instance.</span></span>

    2.  <span data-ttu-id="43699-184">**サブスクリプション** を選択します。</span><span class="sxs-lookup"><span data-stu-id="43699-184">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="43699-185">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="43699-185">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="43699-186">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="43699-186">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="43699-187">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="43699-187">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 
    
    > <span data-ttu-id="43699-188">Azure リソースグループの詳細については、 [Azure リソースグループの管理方法に関するこちらのリンク](/azure/azure-resource-manager/resource-group-portal)先を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43699-188">If you wish to read more about Azure Resource Groups, please follow this [link on how to manage Azure Resource Groups](/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="43699-189">リソースグループの **場所** を決定します (新しいリソースグループを作成している場合)。</span><span class="sxs-lookup"><span data-stu-id="43699-189">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="43699-190">この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="43699-190">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="43699-191">一部の Azure 資産は、特定のリージョンでのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="43699-191">Some Azure assets are only available in certain regions.</span></span>

    5.  <span data-ttu-id="43699-192">[ **ストレージアカウント** ] セクションで、[ **選択...** ] セクションをクリックし、最後の章で作成した **ストレージアカウント** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-192">For the **Storage Account** section, click the **Please select...** section, then click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="43699-193">また、このサービスに適用されている使用条件を理解していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-193">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7.  <span data-ttu-id="43699-194">**Create** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="43699-194">Click **Create**.</span></span>

        ![Azure portal](images/AzureLabs-Lab6-08.png)

4.  <span data-ttu-id="43699-196">[ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="43699-196">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="43699-197">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-197">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-09.png)

6.  <span data-ttu-id="43699-199">通知をクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="43699-199">Click on the notification to explore your new Service instance.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-10.png)

7.  <span data-ttu-id="43699-201">通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="43699-201">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="43699-202">[新しいメディアサービス] ページで、左側のパネルの [ **Assets** ] リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-202">Within the new Media service page, within the panel on the left, click on the **Assets** link, which is about halfway down.</span></span>

9.  <span data-ttu-id="43699-203">次のページで、ページの左上隅にある [ **アップロード**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-203">On the next page, in the top-left corner of the page, click **Upload**.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-11.png)

10. <span data-ttu-id="43699-205">**フォルダー** アイコンをクリックしてファイルを参照し、ストリーミングする最初の360ビデオを選択します。</span><span class="sxs-lookup"><span data-stu-id="43699-205">Click on the **Folder** icon to browse your files and select the first 360 Video that you would like to stream.</span></span> 
    
    > <span data-ttu-id="43699-206">このリンクを使用して [、サンプルビデオをダウンロード](https://vimeo.com/214401712)できます。</span><span class="sxs-lookup"><span data-stu-id="43699-206">You can follow this [link to download a sample video](https://vimeo.com/214401712).</span></span>

    ![Azure portal](images/AzureLabs-Lab6-12.png)

> [!WARNING]
> <span data-ttu-id="43699-208">ファイル名が長いと、エンコーダーで問題が発生する可能性があります。そのため、ビデオに問題がないことを確認するには、ビデオファイル名の長さを短くすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="43699-208">Long filenames may cause an issue with the encoder: so to ensure videos do not have issues, consider shortening the length of your video file names.</span></span>

11. <span data-ttu-id="43699-209">ビデオのアップロードが完了すると、進行状況バーが緑色になります。</span><span class="sxs-lookup"><span data-stu-id="43699-209">The progress bar will turn green when the video has finished uploading.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-13.png)

12. <span data-ttu-id="43699-211">上のテキスト (**servicename-assets**) をクリックして、[ **資産** ] ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="43699-211">Click on the text above (**yourservicename - Assets**) to return to the **Assets** page.</span></span>

13. <span data-ttu-id="43699-212">ビデオが正常にアップロードされたことがわかります。</span><span class="sxs-lookup"><span data-stu-id="43699-212">You will notice that your video has been successfully uploaded.</span></span> <span data-ttu-id="43699-213">そのタイルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-213">Click on it.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-14.png)

14. <span data-ttu-id="43699-215">リダイレクト先のページには、ビデオに関する詳細情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-215">The page you are redirected to will show you detailed information about your video.</span></span> <span data-ttu-id="43699-216">ビデオを使用できるようにするには、ページの左上にある [ **エンコード** ] ボタンをクリックして、ビデオをエンコードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-216">To be able to use your video you need to encode it, by clicking the **Encode** button at the top-left of the page.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-15.png)

15. <span data-ttu-id="43699-218">新しいパネルが右側に表示されます。ここで、ファイルのエンコードオプションを設定することができます。</span><span class="sxs-lookup"><span data-stu-id="43699-218">A new panel will appear to the right, where you will be able to set encoding options for your file.</span></span> <span data-ttu-id="43699-219">次のプロパティを設定します (一部は既に既定で設定されています)。</span><span class="sxs-lookup"><span data-stu-id="43699-219">Set the following properties (some will be already set by default):</span></span>

    1.  <span data-ttu-id="43699-220">**メディアエンコーダー名 *Media Encoder Standard***</span><span class="sxs-lookup"><span data-stu-id="43699-220">**Media encoder name *Media Encoder Standard***</span></span>

    2.  <span data-ttu-id="43699-221">**エンコードプリセット *コンテンツアダプティブマルチビットレート MP4***</span><span class="sxs-lookup"><span data-stu-id="43699-221">**Encoding preset *Content Adaptive Multiple Bitrate MP4***</span></span>

    3.  <span data-ttu-id="43699-222">**ジョブ名 *Media Encoder Standard Video1.mp4の処理***</span><span class="sxs-lookup"><span data-stu-id="43699-222">**Job name *Media Encoder Standard processing of Video1.mp4***</span></span>

    4.  <span data-ttu-id="43699-223">**出力メディアのアセット名 *Video1.mp4--Media Encoder Standard エンコード* されています**</span><span class="sxs-lookup"><span data-stu-id="43699-223">**Output media asset name *Video1.mp4 -- Media Encoder Standard encoded***</span></span>

        ![Azure portal](images/AzureLabs-Lab6-16.png)

16. <span data-ttu-id="43699-225">**[作成]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-225">Click the **Create** button.</span></span>

17. <span data-ttu-id="43699-226">**エンコードジョブが追加さ** れたバーが表示され、そのバーをクリックすると、エンコードの進行状況を示すパネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-226">You will notice a bar with **Encoding job added**, click on that bar and a panel will appear with the Encoding progress displayed in it.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-17.png)

    ![Azure portal](images/AzureLabs-Lab6-18.png)

18. <span data-ttu-id="43699-229">ジョブが完了するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="43699-229">Wait for the Job to be completed.</span></span> <span data-ttu-id="43699-230">完了したら、パネルの右上にある [X] を自由に閉じます。</span><span class="sxs-lookup"><span data-stu-id="43699-230">Once it is done, feel free to close the panel with the 'X' at the top right of that panel.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-19.png)

    ![Azure portal](images/AzureLabs-Lab6-20.png)

    > [!IMPORTANT]
    > <span data-ttu-id="43699-233">これにかかる時間は、ビデオのファイルサイズによって異なります。</span><span class="sxs-lookup"><span data-stu-id="43699-233">The time this takes, depends on the file size of your video.</span></span> <span data-ttu-id="43699-234">このプロセスにはかなりの時間がかかることがあります。</span><span class="sxs-lookup"><span data-stu-id="43699-234">This process can take quite some time.</span></span>

19. <span data-ttu-id="43699-235">エンコードされたバージョンのビデオが作成されたので、それを公開してアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="43699-235">Now that the encoded version of the video has been created, you can publish it to make it accessible.</span></span> <span data-ttu-id="43699-236">これを行うには、青いリンク **アセット** をクリックして [アセット] ページに戻ります。</span><span class="sxs-lookup"><span data-stu-id="43699-236">To do so, click the blue link **Assets** to go back to the assets page.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-21.png)

20. <span data-ttu-id="43699-238">ビデオは、 **資産の種類が _マルチビットレート MP4_** である別のものと共に表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-238">You will see your video along with another, which is of **Asset Type _Multi-Bitrate MP4_**.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-22.png)

    > [!NOTE] 
    > <span data-ttu-id="43699-240">最初のビデオと共に新しい資産は *不明* であり、 **サイズ** が ' 0 ' バイトであることがわかります。更新するには、ウィンドウを更新するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="43699-240">You may notice that the new asset, alongside your initial video, is *Unknown*, and has '0' bytes for it's **Size**, just refresh your window for it to update.</span></span>

21. <span data-ttu-id="43699-241">[この新しい資産] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-241">Click this new asset.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-23.png)

22. <span data-ttu-id="43699-243">以前に使用したものと似たパネルが表示されますが、これは異なる資産です。</span><span class="sxs-lookup"><span data-stu-id="43699-243">You will see a similar panel to the one you used before, just this is a different asset.</span></span> <span data-ttu-id="43699-244">ページの上部中央にある [ **発行** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-244">Click the **Publish** button located at the top-center of the page.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-24.png)

23. <span data-ttu-id="43699-246">資産内の file/s への **ロケーター**(エントリポイント) を設定するように求められます。</span><span class="sxs-lookup"><span data-stu-id="43699-246">You will be prompted to set a **Locator**, which is the entry point, to file/s in your Assets.</span></span> <span data-ttu-id="43699-247">シナリオでは、次のプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="43699-247">For your scenario set the following properties:</span></span>

    1.  <span data-ttu-id="43699-248">**ロケーターの種類**  > **プログレッシブ**。</span><span class="sxs-lookup"><span data-stu-id="43699-248">**Locator type** > **Progressive**.</span></span>

    2.  <span data-ttu-id="43699-249">**日付** と **時刻** は、現在の日付から将来の時刻 (この場合は100年) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="43699-249">The **date** and **time** will be set for you, from your current date, to a time in the future (one hundred years in this case).</span></span> <span data-ttu-id="43699-250">そのままにするか、またはそれに合わせて変更します。</span><span class="sxs-lookup"><span data-stu-id="43699-250">Leave as is or change it to suit.</span></span>

    > [!NOTE]
    > <span data-ttu-id="43699-251">ロケーターの詳細および選択できる内容については、Azure Media Services の [ドキュメント](/azure/media-services/media-services-concepts)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43699-251">For more information about Locators, and what you can choose, visit the [Azure Media Services Documentation](/azure/media-services/media-services-concepts).</span></span>

24. <span data-ttu-id="43699-252">パネルの下部にある [ **追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-252">At the bottom of that panel, click on the **Add** button.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-25.png)

25. <span data-ttu-id="43699-254">ビデオが公開され、エンドポイントを使用してストリームできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="43699-254">Your video is now published and can be streamed by using its endpoint.</span></span> <span data-ttu-id="43699-255">さらに下のページは **ファイル** セクションです。</span><span class="sxs-lookup"><span data-stu-id="43699-255">Further down the page is a **Files** section.</span></span> <span data-ttu-id="43699-256">ここでは、ビデオのエンコードされたさまざまなバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="43699-256">This is where the different encoded versions of your video will be.</span></span> <span data-ttu-id="43699-257">可能な限り最高の解像度を選択すると (下の図の1920x960 ファイル)、右側のパネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-257">Select the highest possible resolution one (in the image below it is the 1920x960 file), and then a panel to the right will appear.</span></span> <span data-ttu-id="43699-258">**ダウンロード URL** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-258">There you will find a **Download URL**.</span></span> <span data-ttu-id="43699-259">この **エンドポイント** は、後でコードで使用するのと同じようにコピーします。</span><span class="sxs-lookup"><span data-stu-id="43699-259">Copy this **Endpoint** as you will use it later in your code.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-26.png)    

    ![Azure portal](images/AzureLabs-Lab6-27.png)

    > [!NOTE] 
    > <span data-ttu-id="43699-262">[ **再生** ] ボタンをクリックしてビデオを再生し、テストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="43699-262">You can also press the **Play** button to play your video and test it.</span></span>

26. <span data-ttu-id="43699-263">ここでは、このラボで使用する2番目のビデオをアップロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-263">You now need to upload the second video that you will use in this Lab.</span></span> <span data-ttu-id="43699-264">上記の手順に従って、2番目のビデオと同じ手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="43699-264">Follow the steps above, repeating the same process for the second video.</span></span> <span data-ttu-id="43699-265">2番目の **エンドポイント** もコピーするようにしてください。</span><span class="sxs-lookup"><span data-stu-id="43699-265">Ensure you copy the second **Endpoint** also.</span></span> <span data-ttu-id="43699-266">[2 番目のビデオをダウンロードするに](https://vimeo.com/214402865)は、次のリンクを使用してください。</span><span class="sxs-lookup"><span data-stu-id="43699-266">Use the following [link to download a second video](https://vimeo.com/214402865).</span></span>

27. <span data-ttu-id="43699-267">両方のビデオが公開されたら、次の章に進むことができます。</span><span class="sxs-lookup"><span data-stu-id="43699-267">Once both videos have been published, you are ready to move to the next Chapter.</span></span>

## <a name="chapter-3---setting-up-the-unity-project"></a><span data-ttu-id="43699-268">章 3-Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="43699-268">Chapter 3 - Setting up the Unity Project</span></span>

<span data-ttu-id="43699-269">次に示すのは、Mixed Reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="43699-269">The following is a typical set up for developing with the Mixed Reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="43699-270">**Unity** を開き、[**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-270">Open **Unity** and click **New**.</span></span> 

    ![Azure portal](images/AzureLabs-Lab6-28.png)

2.  <span data-ttu-id="43699-272">ここで、Unity プロジェクト名を指定する必要があります。挿入 **MR \_ 360videostreaming.**</span><span class="sxs-lookup"><span data-stu-id="43699-272">You will now need to provide a Unity Project name, insert **MR\_360VideoStreaming.**.</span></span> <span data-ttu-id="43699-273">プロジェクトの種類が **3d** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="43699-273">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="43699-274">場所を適切な場所に設定します (ルートディレクトリの方が適していることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="43699-274">Set the Location to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="43699-275">次に、[ **プロジェクトの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-275">Then, click **Create project**.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-29.png)

3.  <span data-ttu-id="43699-277">Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-277">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio.**</span></span> <span data-ttu-id="43699-278">[ ***設定* の編集**] に移動し、新しいウィンドウで [**外部ツール**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="43699-278">Go to **_Edit_ *Preferences*** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="43699-279">**外部スクリプトエディター** を **Visual Studio 2017** に変更します。</span><span class="sxs-lookup"><span data-stu-id="43699-279">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="43699-280">[ **基本設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="43699-280">Close the **Preferences** window.</span></span>

    ![Azure portal](images/AzureLabs-Lab6-30.png)

4.  <span data-ttu-id="43699-282">次に、[ **_ファイル_** ] [ビルドの設定] の順に移動し、[**プラットフォームの切り替え**] ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="43699-282">Next, go to **_File_ *Build Settings*** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

5.  <span data-ttu-id="43699-283">また、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="43699-283">Also make sure that:</span></span>

    1. <span data-ttu-id="43699-284">**ターゲットデバイス** は **、任意のデバイス** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="43699-284">**Target Device** is set to **Any Device.**</span></span>
    
    2.  <span data-ttu-id="43699-285">**ビルドの種類** が D3D に設定されてい **ます。**</span><span class="sxs-lookup"><span data-stu-id="43699-285">**Build Type** is set to **D3D.**</span></span>

    3.  <span data-ttu-id="43699-286">**SDK** は、**インストールされている最新のバージョン** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="43699-286">**SDK** is set to **Latest installed.**</span></span>

    4.  <span data-ttu-id="43699-287">**Visual Studio のバージョン** が、**インストールされている最新** のバージョンに設定されています。</span><span class="sxs-lookup"><span data-stu-id="43699-287">**Visual Studio Version** is set to **Latest installed.**</span></span>

    5.  <span data-ttu-id="43699-288">**ビルドと実行** はローカルコンピューターに設定されて **います。**</span><span class="sxs-lookup"><span data-stu-id="43699-288">**Build and Run** is set to **Local Machine.**</span></span>

    6.  <span data-ttu-id="43699-289">後で設定するため、 **今すぐ設定** することは心配しないでください。</span><span class="sxs-lookup"><span data-stu-id="43699-289">Do not worry about setting up **Scenes** right now, as you will set these up later.</span></span>

    7.  <span data-ttu-id="43699-290">ここでは、残りの設定は既定値のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="43699-290">The remaining settings should be left as default for now.</span></span>

        ![Unity プロジェクトの設定](images/AzureLabs-Lab6-31.png)

6.  <span data-ttu-id="43699-292">[ **ビルドの設定** ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 **インスペクター** が配置されている領域の関連パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="43699-292">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

7. <span data-ttu-id="43699-293">このパネルでは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-293">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="43699-294">[ **その他の設定** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="43699-294">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="43699-295">**スクリプト\*\*\*\*ランタイムのバージョン** は **安定** している必要があります (.net 3.5 と同等)。</span><span class="sxs-lookup"><span data-stu-id="43699-295">**Scripting** **Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>

        2. <span data-ttu-id="43699-296">**スクリプトバックエンド** は .net である必要があり **ます。**</span><span class="sxs-lookup"><span data-stu-id="43699-296">**Scripting Backend** should be **.NET.**</span></span>

        3. <span data-ttu-id="43699-297">**API の互換性レベル** は **.net 4.6** である必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-297">**API Compatibility Level** should be **.NET 4.6.**</span></span>

            ![Unity プロジェクトの設定](images/AzureLabs-Lab6-32.png)

    2.  <span data-ttu-id="43699-299">パネルの下にある [ **XR settings** (発行の **設定**] の下にあります) で、[ **サポートされている仮想現実**] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="43699-299">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Unity プロジェクトの設定](images/AzureLabs-Lab6-33.png)

    3.  <span data-ttu-id="43699-301">[ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="43699-301">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="43699-302">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="43699-302">**InternetClient**</span></span>

            ![Unity プロジェクトの設定](images/AzureLabs-Lab6-34.png)

8.  <span data-ttu-id="43699-304">これらの変更を行ったら、[ **ビルドの設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="43699-304">Once you have made those changes, close the **Build Settings** window.</span></span>

9.  <span data-ttu-id="43699-305">プロジェクトを保存します \**ファイル* \* プロジェクトの保存 \* \*。</span><span class="sxs-lookup"><span data-stu-id="43699-305">Save your Project \**File* \*Save Project\*\*.</span></span>



## <a name="chapter-4---importing-the-insideoutsphere-unity-package"></a><span data-ttu-id="43699-306">Chapter 4-InsideOutSphere Unity パッケージのインポート</span><span class="sxs-lookup"><span data-stu-id="43699-306">Chapter 4 - Importing the InsideOutSphere Unity package</span></span>

> [!IMPORTANT]
> <span data-ttu-id="43699-307">このコースの *Unity セットアップ* コンポーネントをスキップしてコードに直接進む場合は、 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage)をダウンロードし、 [**カスタムパッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 **第5章** から続行してください。</span><span class="sxs-lookup"><span data-stu-id="43699-307">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/Azure-MR-306.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from **Chapter 5**.</span></span> <span data-ttu-id="43699-308">引き続き Unity プロジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-308">You will still need to create a Unity Project.</span></span>

<span data-ttu-id="43699-309">このコースでは、 [**unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage)という名前の Unity アセットパッケージをダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-309">For this course you will need to download a Unity Asset Package called [**InsideOutSphere.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20306%20-%20Streaming%20video/InsideOutSphere.unitypackage).</span></span>

<span data-ttu-id="43699-310">**Unitypackage** をインポートする方法:</span><span class="sxs-lookup"><span data-stu-id="43699-310">How-to import the **unitypackage**:</span></span>

1.  <span data-ttu-id="43699-311">Unity ダッシュボードを使用して、画面の上部にあるメニューの [ **アセット** ] をクリックし、[ **パッケージのインポート > カスタムパッケージ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-311">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package > Custom Package**.</span></span>

    ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-35.png)

2.  <span data-ttu-id="43699-313">ファイルピッカーを使用して **Insideoutsphere** パッケージを選択し、[ **開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-313">Use the file picker to select the **InsideOutSphere.unitypackage** package and click **Open**.</span></span> <span data-ttu-id="43699-314">この資産のコンポーネントの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-314">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="43699-315">インポートを確認するには、[ **インポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-315">Confirm the import by clicking **Import**.</span></span>

    ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-36.png)

3.  <span data-ttu-id="43699-317">インポートが完了すると、3つの新しいフォルダー、 **素材**、 **モデル**、および **Prefabs** が **Assets** フォルダーに追加されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="43699-317">Once it has finished importing, you will notice three new folders, **Materials**, **Models**, and **Prefabs**, have been added to your **Assets** folder.</span></span> <span data-ttu-id="43699-318">この種のフォルダー構造は、Unity プロジェクトで一般的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="43699-318">This kind of folder structure is typical for a Unity project.</span></span>

    ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-37.png)

    1.  <span data-ttu-id="43699-320">[ **モデル** ] フォルダーを開くと、 **Insideoutsphere** モデルがインポートされていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="43699-320">Open the **Models** folder, and you will see that the **InsideOutSphere** model has been imported.</span></span>

    2.  <span data-ttu-id="43699-321">**素材** フォルダー内には、 **Insideoutspheres** マテリアル *lambert1* と、GazeButton によって使用される *buttonmaterial* と呼ばれる素材があります。これは近日中に表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-321">Within the **Materials** folder you will find the **InsideOutSpheres** material  *lambert1*, along with a material called *ButtonMaterial*, which is used by the GazeButton, which you will see soon.</span></span>

    3.  <span data-ttu-id="43699-322">**Prefabs** フォルダーには、 **insideoutsphere** *モデル* と *GazeButton* の両方を含む **insideoutsphere** prefab が含まれています。</span><span class="sxs-lookup"><span data-stu-id="43699-322">The **Prefabs** folder contains the **InsideOutSphere** prefab which contains both the **InsideOutSphere** *model* and the *GazeButton*.</span></span>

    4.  <span data-ttu-id="43699-323">**コードは含ま** れていません。このコースに従ってコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="43699-323">**No code is included**, you will write the code by following this course.</span></span>


4.  <span data-ttu-id="43699-324">**階層** 内で、**メインカメラ** オブジェクトを選択し、次のコンポーネントを更新します。</span><span class="sxs-lookup"><span data-stu-id="43699-324">Within the **Hierarchy**, select the **Main Camera** object, and update the following components:</span></span>

    1.  <span data-ttu-id="43699-325">**変換**</span><span class="sxs-lookup"><span data-stu-id="43699-325">**Transform**</span></span>

        1.  <span data-ttu-id="43699-326">位置 = **X**: 0、 **Y**: 0、 **Z**: 0。</span><span class="sxs-lookup"><span data-stu-id="43699-326">Position = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        2. <span data-ttu-id="43699-327">回転 = **X**: 0、 **Y**: 0、 **Z**: 0。</span><span class="sxs-lookup"><span data-stu-id="43699-327">Rotation = **X**: 0, **Y**: 0, **Z**: 0.</span></span>

        3. <span data-ttu-id="43699-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span><span class="sxs-lookup"><span data-stu-id="43699-328">Scale **X**: 1, **Y**: 1, **Z**: 1.</span></span>

    2.  <span data-ttu-id="43699-329">**カメラ**</span><span class="sxs-lookup"><span data-stu-id="43699-329">**Camera**</span></span>

        1. <span data-ttu-id="43699-330">**クリアフラグ**: 純色。</span><span class="sxs-lookup"><span data-stu-id="43699-330">**Clear Flags**: Solid Color.</span></span>

        2.  <span data-ttu-id="43699-331">**クリッピングプレーン**: Near: 0.1、Far: 6。</span><span class="sxs-lookup"><span data-stu-id="43699-331">**Clipping Planes**: Near: 0.1, Far: 6.</span></span>

            ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-38.png)

5.  <span data-ttu-id="43699-333">**Prefab** フォルダーに移動し、[ **Insideoutsphere** ] を [**階層**] パネルにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="43699-333">Navigate to the **Prefab** folder, and then drag the **InsideOutSphere** prefab into the **Hierarchy** Panel.</span></span>

    ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-39.png)

6.  <span data-ttu-id="43699-335">**階層** 内の **Insideoutsphere** オブジェクトの横にある小さな矢印をクリックして展開します。</span><span class="sxs-lookup"><span data-stu-id="43699-335">Expand the **InsideOutSphere** object within the **Hierarchy** by clicking the little arrow next to it.</span></span> <span data-ttu-id="43699-336">**GazeButton** という名前の **子** オブジェクトがその下に表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-336">You will see a **child** object beneath it called **GazeButton**.</span></span> <span data-ttu-id="43699-337">これは、シーンとビデオを変更するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="43699-337">This will be used to change scenes and thus videos.</span></span>

    ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-40.png)

7.  <span data-ttu-id="43699-339">[インスペクター] ウィンドウで、 **Insideoutsphere** の変換コンポーネントをクリックし、次のプロパティが設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="43699-339">In the Inspector Window click on the **InsideOutSphere**'s Transform component, ensure that the following properties are set:</span></span>

    |            |    <span data-ttu-id="43699-340">変換-位置</span><span class="sxs-lookup"><span data-stu-id="43699-340">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="43699-341">**X** 0</span><span class="sxs-lookup"><span data-stu-id="43699-341">**X** 0</span></span>  |          <span data-ttu-id="43699-342">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="43699-342">**Y** 0</span></span>          |  <span data-ttu-id="43699-343">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="43699-343">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="43699-344">変換-回転</span><span class="sxs-lookup"><span data-stu-id="43699-344">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="43699-345">**X** 0</span><span class="sxs-lookup"><span data-stu-id="43699-345">**X** 0</span></span>  |          <span data-ttu-id="43699-346">**Y** -50</span><span class="sxs-lookup"><span data-stu-id="43699-346">**Y** -50</span></span>        |  <span data-ttu-id="43699-347">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="43699-347">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="43699-348">変換-スケール</span><span class="sxs-lookup"><span data-stu-id="43699-348">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="43699-349">**X** 1</span><span class="sxs-lookup"><span data-stu-id="43699-349">**X** 1</span></span>   |          <span data-ttu-id="43699-350">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="43699-350">**Y** 1</span></span>          |  <span data-ttu-id="43699-351">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="43699-351">**Z** 1</span></span>  |

    ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-41.png)

8.  <span data-ttu-id="43699-353">**GazeButton** 子オブジェクトをクリックし、その **変換** を次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="43699-353">Click on the **GazeButton** child object, and set its **Transform** as follows:</span></span>

    |            |    <span data-ttu-id="43699-354">変換-位置</span><span class="sxs-lookup"><span data-stu-id="43699-354">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="43699-355">**X** 3.6</span><span class="sxs-lookup"><span data-stu-id="43699-355">**X** 3.6</span></span>|          <span data-ttu-id="43699-356">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="43699-356">**Y** 1.3</span></span>        |  <span data-ttu-id="43699-357">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="43699-357">**Z** 0</span></span>  |

    |            |    <span data-ttu-id="43699-358">変換-回転</span><span class="sxs-lookup"><span data-stu-id="43699-358">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="43699-359">**X** 0</span><span class="sxs-lookup"><span data-stu-id="43699-359">**X** 0</span></span>  |          <span data-ttu-id="43699-360">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="43699-360">**Y** 0</span></span>          |  <span data-ttu-id="43699-361">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="43699-361">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="43699-362">変換-スケール</span><span class="sxs-lookup"><span data-stu-id="43699-362">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="43699-363">**X** 1</span><span class="sxs-lookup"><span data-stu-id="43699-363">**X** 1</span></span>   |          <span data-ttu-id="43699-364">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="43699-364">**Y** 1</span></span>          |  <span data-ttu-id="43699-365">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="43699-365">**Z** 1</span></span>  |

    ![InsideOutSphere Unity パッケージをインポートしています](images/AzureLabs-Lab6-42.png)


## <a name="chapter-5---create-the-videocontroller-class"></a><span data-ttu-id="43699-367">第5章-VideoController クラスの作成</span><span class="sxs-lookup"><span data-stu-id="43699-367">Chapter 5 - Create the VideoController class</span></span>

<span data-ttu-id="43699-368">**Videocontroller** クラスは、Azure Media Service からコンテンツをストリーミングするために使用される2つのビデオエンドポイントをホストします。</span><span class="sxs-lookup"><span data-stu-id="43699-368">The **VideoController** class hosts the two video endpoints that will be used to stream the content from the Azure Media Service.</span></span>

<span data-ttu-id="43699-369">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="43699-369">To create this class:</span></span>

1.  <span data-ttu-id="43699-370">[**プロジェクト**] パネルにある **Asset フォルダー** を右クリックし、[ **> フォルダーの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-370">Right-click in the **Asset Folder**, located in the **Project** Panel, and click **Create > Folder**.</span></span> <span data-ttu-id="43699-371">フォルダーに **スクリプト** の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="43699-371">Name the folder **Scripts**.</span></span>

    ![VideoController クラスを作成する](images/AzureLabs-Lab6-43.png)

    ![VideoController クラスを作成する](images/AzureLabs-Lab6-44.png)

2.  <span data-ttu-id="43699-374">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="43699-374">Double click on the **Scripts** folder to open it.</span></span>

3.  <span data-ttu-id="43699-375">フォルダー内を右クリックし、[ **Create > C \# Script**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-375">Right-click inside the folder, then click **Create > C\# Script**.</span></span> <span data-ttu-id="43699-376">スクリプトに「 **Videocontroller**」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="43699-376">Name the script **VideoController**.</span></span>

    ![VideoController クラスを作成する](images/AzureLabs-Lab6-45.png)

4.  <span data-ttu-id="43699-378">新しい **Videocontroller** スクリプトをダブルクリックして、 **Visual Studio 2017 で開きます。**</span><span class="sxs-lookup"><span data-stu-id="43699-378">Double click on the new **VideoController** script to open it with **Visual Studio 2017.**</span></span>

    ![VideoController クラスを作成する](images/AzureLabs-Lab6-46.png)

5.  <span data-ttu-id="43699-380">コードファイルの先頭にある名前空間を次のように更新します。</span><span class="sxs-lookup"><span data-stu-id="43699-380">Update the namespaces at the top of the code file as follows:</span></span>

    ```csharp
    using System.Collections;
    using UnityEngine;
    using UnityEngine.SceneManagement;
    using UnityEngine.Video;
    ```

6.  <span data-ttu-id="43699-381">**Videocontroller** クラスに次の変数を、起動前 **()** メソッドと共に入力します。</span><span class="sxs-lookup"><span data-stu-id="43699-381">Enter the following variables in the **VideoController** class, along with the **Awake()** method:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static VideoController instance; 
        
        /// <summary> 
        /// Reference to the Camera VideoPlayer Component.
        /// </summary> 
        private VideoPlayer videoPlayer; 
        
        /// <summary>
        /// Reference to the Camera AudioSource Component.
        /// </summary> 
        private AudioSource audioSource; 
        
        /// <summary> 
        /// Reference to the texture used to project the video streaming 
        /// </summary> 
        private RenderTexture videoStreamRenderTexture;

        /// <summary>
        /// Insert here the first video endpoint
        /// </summary>
        private string video1endpoint = "-- Insert video 1 Endpoint here --";

        /// <summary>
        /// Insert here the second video endpoint
        /// </summary>
        private string video2endpoint = "-- Insert video 2 Endpoint here --";

        /// <summary> 
        /// Reference to the Inside-Out Sphere. 
        /// </summary> 
        public GameObject sphere;

        void Awake()
        {
            instance = this;
        }
    ```

7.  <span data-ttu-id="43699-382">Azure Media Service のビデオからエンドポイントを入力する時間は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="43699-382">Now is the time to enter the endpoints from your Azure Media Service videos:</span></span>

    1.  <span data-ttu-id="43699-383">最初のを *video1endpoint* 変数に挿入します。</span><span class="sxs-lookup"><span data-stu-id="43699-383">The first into the *video1endpoint* variable.</span></span>
    
    2.  <span data-ttu-id="43699-384">2番目のを *video2endpoint* 変数に挿入します。</span><span class="sxs-lookup"><span data-stu-id="43699-384">The second into the *video2endpoint* variable.</span></span>

    > [!WARNING]
    > <span data-ttu-id="43699-385">Unity での *https* の使用に関する既知の問題があります。バージョン 2017.4.1 f1 を使用します。</span><span class="sxs-lookup"><span data-stu-id="43699-385">There is a known issue with using *https* within Unity, with version 2017.4.1f1.</span></span> <span data-ttu-id="43699-386">ビデオの再生時にエラーが発生した場合は、代わりに ' http ' を使用してみてください。</span><span class="sxs-lookup"><span data-stu-id="43699-386">If the videos provide an error on play, try using 'http' instead.</span></span>

8.  <span data-ttu-id="43699-387">次に、 **Start ()** メソッドを編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-387">Next, the **Start()** method needs to be edited.</span></span> <span data-ttu-id="43699-388">このメソッドは、ユーザーが宝石ボタンを見てシーンを切り替えるたびにトリガーされます (その結果、ビデオが切り替わります)。</span><span class="sxs-lookup"><span data-stu-id="43699-388">This method will be triggered every time the user switches scene (consequently switching the video) by looking at the Gaze Button.</span></span>

    ```csharp
        // Use this for initialization
        void Start()
        {
            Application.runInBackground = true;
            StartCoroutine(PlayVideo());
        }
    ```

9.  <span data-ttu-id="43699-389">**Start ()** メソッドの後に、 **playvideo ()** *IEnumerator* メソッドを挿入します。これは、ビデオをシームレスに開始するために使用されます (そのため、動きが見られません)。</span><span class="sxs-lookup"><span data-stu-id="43699-389">Following the **Start()** method, insert the **PlayVideo()** *IEnumerator* method, which will be used to start videos seamlessly (so no stutter is seen).</span></span>

    ```csharp
        private IEnumerator PlayVideo()
        {
            // create a new render texture to display the video 
            videoStreamRenderTexture = new RenderTexture(2160, 1440, 32, RenderTextureFormat.ARGB32);

            videoStreamRenderTexture.Create();

            // assign the render texture to the object material 
            Material sphereMaterial = sphere.GetComponent<Renderer>().sharedMaterial;

            //create a VideoPlayer component 
            videoPlayer = gameObject.AddComponent<VideoPlayer>();

            // Set the video to loop. 
            videoPlayer.isLooping = true;

            // Set the VideoPlayer component to play the video from the texture 
            videoPlayer.renderMode = VideoRenderMode.RenderTexture;

            videoPlayer.targetTexture = videoStreamRenderTexture;

            // Add AudioSource 
            audioSource = gameObject.AddComponent<AudioSource>();

            // Pause Audio play on Awake 
            audioSource.playOnAwake = true;
            audioSource.Pause();

            // Set Audio Output to AudioSource 
            videoPlayer.audioOutputMode = VideoAudioOutputMode.AudioSource;
            videoPlayer.source = VideoSource.Url;

            // Assign the Audio from Video to AudioSource to be played 
            videoPlayer.EnableAudioTrack(0, true);
            videoPlayer.SetTargetAudioSource(0, audioSource);

            // Assign the video Url depending on the current scene 
            switch (SceneManager.GetActiveScene().name)
            {
                case "VideoScene1":
                    videoPlayer.url = video1endpoint;
                    break;

                case "VideoScene2":
                    videoPlayer.url = video2endpoint;
                    break;

                default:
                    break;
            }

            //Set video To Play then prepare Audio to prevent Buffering 
            videoPlayer.Prepare();

            while (!videoPlayer.isPrepared)
            {
                yield return null;
            }

            sphereMaterial.mainTexture = videoStreamRenderTexture;

            //Play Video 
            videoPlayer.Play();

            //Play Sound 
            audioSource.Play();

            while (videoPlayer.isPlaying)
            {
                yield return null;
            }
        }
    ```

10. <span data-ttu-id="43699-390">このクラスに必要な最後のメソッドは、"設定の切り替え **" メソッドです** 。このメソッドは、シーンの入れ替えに使用されます。</span><span class="sxs-lookup"><span data-stu-id="43699-390">The last method you need for this class is the **ChangeScene()** method, which will be used to swap between scenes.</span></span>

    ```csharp
        public void ChangeScene()
        {
            SceneManager.LoadScene(SceneManager.GetActiveScene().name == "VideoScene1" ? "VideoScene2" : "VideoScene1");
        }
    ```

    > [!TIP] 
    > <span data-ttu-id="43699-391">この **メソッドは** 、 \# *条件演算子* と呼ばれる便利な C 機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="43699-391">The **ChangeScene()** method uses a handy C\# feature called the *Conditional Operator*.</span></span> <span data-ttu-id="43699-392">これにより、条件を確認してから、チェックの結果に基づいて値が返されます。すべて1つのステートメント内になります。</span><span class="sxs-lookup"><span data-stu-id="43699-392">This allows for conditions to be checked, and then values returned based on the outcome of the check, all within a single statement.</span></span> <span data-ttu-id="43699-393">[条件演算子の詳細については、こちらのリンクを参照して](/dotnet/csharp/language-reference/operators/conditional-operator)ください。</span><span class="sxs-lookup"><span data-stu-id="43699-393">Follow this [link to learn more about Conditional Operator](/dotnet/csharp/language-reference/operators/conditional-operator).</span></span>

11. <span data-ttu-id="43699-394">Unity に戻る前に、変更を Visual Studio に保存します。</span><span class="sxs-lookup"><span data-stu-id="43699-394">Save your changes in Visual Studio before returning to Unity.</span></span>

12. <span data-ttu-id="43699-395">Unity エディターに戻り、 **Videocontroller** クラス [from] {. アンダーライン} **Scripts** フォルダーを、[**階層**] パネルの **メインカメラ** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="43699-395">Back in the Unity Editor, click and drag the **VideoController** class [from]{.underline} the **Scripts** folder to the **Main Camera** object in the **Hierarchy** Panel.</span></span>

13. <span data-ttu-id="43699-396">**メインカメラ** をクリックし、[**インスペクター] パネル** を確認します。</span><span class="sxs-lookup"><span data-stu-id="43699-396">Click on the **Main Camera** and look at the **Inspector Panel**.</span></span> <span data-ttu-id="43699-397">新しく追加されたスクリプトコンポーネント内に、空の値を持つフィールドがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="43699-397">You will notice that within the newly added Script component, there is a field with an empty value.</span></span> <span data-ttu-id="43699-398">これは参照フィールドで、コード内のパブリック変数を対象とします。</span><span class="sxs-lookup"><span data-stu-id="43699-398">This is a reference field, which targets the public variables within your code.</span></span>

14. <span data-ttu-id="43699-399">次の図に示すように、[**階層] パネル** の [ **Insideoutsphere** ] オブジェクトを [**球体**] スロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="43699-399">Drag the **InsideOutSphere** object from the **Hierarchy Panel** to the **Sphere** slot, as shown in the image below.</span></span>

    <span data-ttu-id="43699-400">![VideoController クラスを作成する ](images/AzureLabs-Lab6-47.png)
     ![ videocontroller クラスを作成する](images/AzureLabs-Lab6-48.png)</span><span class="sxs-lookup"><span data-stu-id="43699-400">![Create the VideoController class](images/AzureLabs-Lab6-47.png)
![Create the VideoController class](images/AzureLabs-Lab6-48.png)</span></span>

## <a name="chapter-6---create-the-gaze-class"></a><span data-ttu-id="43699-401">Chapter 6-"宝石" クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="43699-401">Chapter 6 - Create the Gaze class</span></span>

<span data-ttu-id="43699-402">このクラスは、ユーザーが参照しているオブジェクトを検出するために、**メインカメラ** から投影される **Raycast** を作成します。</span><span class="sxs-lookup"><span data-stu-id="43699-402">This class is responsible for creating a **Raycast** that will be projected forward from the **Main Camera**, to detect which object the user is looking at.</span></span> <span data-ttu-id="43699-403">この場合、 **Raycast** は、ユーザーがシーン内の **GazeButton** オブジェクトを調べて動作をトリガーするかどうかを識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-403">In this case, the **Raycast** will need to identify if the user is looking at the **GazeButton** object in the scene and trigger a behavior.</span></span>

<span data-ttu-id="43699-404">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="43699-404">To create this Class:</span></span>

1.  <span data-ttu-id="43699-405">前に作成した **Scripts** フォルダーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="43699-405">Go to the **Scripts** folder you created previously.</span></span>

2.  <span data-ttu-id="43699-406">[ **プロジェクト** ] パネル内を右クリックし、\* [\* C スクリプトの *作成* ] \* \* をクリック \# します。</span><span class="sxs-lookup"><span data-stu-id="43699-406">Right-click in the **Project** Panel, \**Create* \*C\# Script\*\*.</span></span> <span data-ttu-id="43699-407">スクリプトに「」という名前を **指定します**。</span><span class="sxs-lookup"><span data-stu-id="43699-407">Name the script **Gaze**.</span></span>

3.  <span data-ttu-id="43699-408">新しい宝石 _ スクリプトをダブルクリックして、 **_ Visual Studio 2017 *で開き* ます。**</span><span class="sxs-lookup"><span data-stu-id="43699-408">Double click on the new **_Gaze_*_ script to open it with _\* Visual Studio 2017.*\*</span></span>

4.  <span data-ttu-id="43699-409">次の名前空間がスクリプトの先頭にあることを確認し、その他の名前空間を削除します。</span><span class="sxs-lookup"><span data-stu-id="43699-409">Ensure the following namespace is at the top of the script, and remove any others:</span></span>

    ```csharp
    using UnityEngine;
    ```

5.  <span data-ttu-id="43699-410">次に、次の変数を、 **宝石** クラス内に追加します。</span><span class="sxs-lookup"><span data-stu-id="43699-410">Then add the following variables inside the **Gaze** class:</span></span>

    ```csharp
        /// <summary> 
        /// Provides Singleton-like behaviour to this class. 
        /// </summary> 
        public static Gaze instance;

        /// <summary> 
        /// Provides a reference to the object the user is currently looking at. 
        /// </summary> 
        public GameObject FocusedGameObject { get; private set; }

        /// <summary> 
        /// Provides a reference to compare whether the user is still looking at 
        /// the same object (and has not looked away). 
        /// </summary> 
        private GameObject oldFocusedObject = null;

        /// <summary> 
        /// Max Ray Distance 
        /// </summary> 
        float gazeMaxDistance = 300;

        /// <summary> 
        /// Provides whether an object has been successfully hit by the raycast. 
        /// </summary> 
        public bool Hit { get; private set; }
    ```

6.  <span data-ttu-id="43699-411">起動可能な **()** メソッドと **Start ()** メソッドのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-411">Code for the **Awake()** and **Start()** methods now needs to be added.</span></span>

    ```csharp
        private void Awake()
        {
            // Set this class to behave similar to singleton 
            instance = this;
        }

        void Start()
        {
            FocusedGameObject = null;
        }
    ```

7.  <span data-ttu-id="43699-412">**Update ()** メソッドに次のコードを追加して、Raycast を射影し、ターゲットのヒットを検出します。</span><span class="sxs-lookup"><span data-stu-id="43699-412">Add the following code in the **Update()** method to project a Raycast and detect the target hit:</span></span>

    ```csharp
        void Update()
        {
            // Set the old focused gameobject. 
            oldFocusedObject = FocusedGameObject;
            RaycastHit hitInfo;

            // Initialise Raycasting. 
            Hit = Physics.Raycast(Camera.main.transform.position, Camera.main.transform.forward, out hitInfo, gazeMaxDistance);

            // Check whether raycast has hit. 
            if (Hit == true)
            {
                // Check whether the hit has a collider. 
                if (hitInfo.collider != null)
                {
                    // Set the focused object with what the user just looked at. 
                    FocusedGameObject = hitInfo.collider.gameObject;
                }
                else
                {
                    // Object looked on is not valid, set focused gameobject to null. 
                    FocusedGameObject = null;
                }
            }
            else
            {
                // No object looked upon, set focused gameobject to null.
                FocusedGameObject = null;
            }

            // Check whether the previous focused object is this same 
            // object (so to stop spamming of function). 
            if (FocusedGameObject != oldFocusedObject)
            {
                // Compare whether the new Focused Object has the desired tag we set previously. 
                if (FocusedGameObject.CompareTag("GazeButton"))
                {
                    FocusedGameObject.SetActive(false);
                    VideoController.instance.ChangeScene();
                }
            }
        }
    ```

8.  <span data-ttu-id="43699-413">Unity に戻る前に、変更を Visual Studio に保存します。</span><span class="sxs-lookup"><span data-stu-id="43699-413">Save your changes in Visual Studio before returning to Unity.</span></span>

9.  <span data-ttu-id="43699-414">[スクリプト] フォルダーから、[**階層**] パネルの [メインカメラ] オブジェクトに、**見つめ** クラスをクリックしてドラッグします。</span><span class="sxs-lookup"><span data-stu-id="43699-414">Click and drag the **Gaze** class from the Scripts folder to the Main Camera object in the **Hierarchy** Panel.</span></span>

## <a name="chapter-7---setup-the-two-unity-scenes"></a><span data-ttu-id="43699-415">第7章-Unity の2つのシーンの設定</span><span class="sxs-lookup"><span data-stu-id="43699-415">Chapter 7 - Setup the two Unity Scenes</span></span>

<span data-ttu-id="43699-416">この章の目的は、ストリーミングするビデオをそれぞれホストする2つのシーンを設定することです。</span><span class="sxs-lookup"><span data-stu-id="43699-416">The purpose of this Chapter is to setup the two scenes, each hosting a video to stream.</span></span> <span data-ttu-id="43699-417">作成済みのシーンを複製して、もう一度設定する必要がないようにします。ただし、 *GazeButton* オブジェクトが別の場所にあり、外観が異なるように、新しいシーンを編集します。</span><span class="sxs-lookup"><span data-stu-id="43699-417">You will duplicate the scene you have already created, so that you do not need to set it up again, though you will then edit the new scene, so that the *GazeButton* object is in a different location and has a different appearance.</span></span> <span data-ttu-id="43699-418">これは、シーン間で変更する方法を示すためのものです。</span><span class="sxs-lookup"><span data-stu-id="43699-418">This is to show how to change between scenes.</span></span>

1.  <span data-ttu-id="43699-419">これを行うには、ファイルに移動し **て、シーンに名前を付けて保存... >** します。保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-419">Do this by going to **File > Save Scene as...**. A save window will appear.</span></span> <span data-ttu-id="43699-420">[ **新しいフォルダー** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-420">Click the **New folder** button.</span></span>

    ![第7章-Unity の2つのシーンの設定](images/AzureLabs-Lab6-49.png)

2.  <span data-ttu-id="43699-422">フォルダーの名前を「 **シーン**」にします。</span><span class="sxs-lookup"><span data-stu-id="43699-422">Name the folder **Scenes**.</span></span>

3.  <span data-ttu-id="43699-423">[ **シーンの保存** ] ウィンドウは開いたままです。</span><span class="sxs-lookup"><span data-stu-id="43699-423">The **Save Scene** window will still be open.</span></span> <span data-ttu-id="43699-424">新しく作成した **シーン** フォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="43699-424">Open your newly created **Scenes** folder.</span></span>

4.  <span data-ttu-id="43699-425">[ **ファイル名:** テキスト] フィールドに「 **VideoScene1**」と入力し、[ **保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-425">In the **File name:** text field, type **VideoScene1**, then press **Save**.</span></span>

5.  <span data-ttu-id="43699-426">Unity に戻り、[ **シーン** ] フォルダーを開き、 **VideoScene1** ファイルを左クリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-426">Back in Unity, open your **Scenes** folder, and left-click your **VideoScene1** file.</span></span> <span data-ttu-id="43699-427">キーボードを使用して Ctrl キーを押し **ながら D** キーを押すと、そのシーンが複製されます。</span><span class="sxs-lookup"><span data-stu-id="43699-427">Use your keyboard, and press **Ctrl + D** you will duplicate that scene</span></span>

    > [!TIP]
    > <span data-ttu-id="43699-428">重複 **するコマンドは** 、[ **編集 > 複製**] に移動して実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="43699-428">The **Duplicate** command can also be performed by navigating to **Edit > Duplicate**.</span></span>

6.  <span data-ttu-id="43699-429">Unity では、シーン名の番号が自動的にインクリメントされますが、それが前に挿入されたコードと一致することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="43699-429">Unity will automatically increment the scene names number, but check it anyway, to ensure it matches the previously inserted code.</span></span>

    >  <span data-ttu-id="43699-430">**VideoScene1** と **VideoScene2** が必要です。</span><span class="sxs-lookup"><span data-stu-id="43699-430">You should have **VideoScene1** and **VideoScene2**.</span></span>

7.  <span data-ttu-id="43699-431">2つのシーンを使用して、[ **ファイル > ビルド設定**] にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="43699-431">With your two scenes, go to **File > Build Settings**.</span></span> <span data-ttu-id="43699-432">[ **ビルドの設定** ] ウィンドウを開いた状態で、[ビルド] セクションの **シーン** にシーンをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="43699-432">With the **Build Settings** window open, drag your scenes to the **Scenes in Build** section.</span></span>

    ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-50.png)

    > [!TIP] 
    > <span data-ttu-id="43699-434">**シーンフォルダーから** 両方のシーンを選択するには、 **Ctrl** ボタンを押しながら各シーンを左クリックし、最後に両方をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="43699-434">You can select both of your scenes from your **Scenes** folder through holding the **Ctrl** button, and then left-clicking each scene, and finally drag both across.</span></span>

8.  <span data-ttu-id="43699-435">[ **ビルドの設定** ] ウィンドウを閉じ、[ **VideoScene2**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-435">Close the **Build Settings** window, and double click on **VideoScene2**.</span></span>

9.  <span data-ttu-id="43699-436">2番目のシーンを開いた状態で、 **Insideoutsphere** の **GazeButton** 子オブジェクトをクリックし、その変換を次のように設定します。</span><span class="sxs-lookup"><span data-stu-id="43699-436">With the second scene open, click on the **GazeButton** child object of the **InsideOutSphere**, and set its Transform as follows:</span></span>

    |            |    <span data-ttu-id="43699-437">変換-位置</span><span class="sxs-lookup"><span data-stu-id="43699-437">TRANSFORM - POSITION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="43699-438">**X** 0</span><span class="sxs-lookup"><span data-stu-id="43699-438">**X** 0</span></span>  |         <span data-ttu-id="43699-439">**Y** 1.3</span><span class="sxs-lookup"><span data-stu-id="43699-439">**Y** 1.3</span></span>         | <span data-ttu-id="43699-440">**Z** 3.6</span><span class="sxs-lookup"><span data-stu-id="43699-440">**Z** 3.6</span></span> |

    |            |    <span data-ttu-id="43699-441">変換-回転</span><span class="sxs-lookup"><span data-stu-id="43699-441">TRANSFORM - ROTATION</span></span>   |           |
    | :---------:| :-----------------------: | :--------:|
    |   <span data-ttu-id="43699-442">**X** 0</span><span class="sxs-lookup"><span data-stu-id="43699-442">**X** 0</span></span>  |          <span data-ttu-id="43699-443">**Y** 0</span><span class="sxs-lookup"><span data-stu-id="43699-443">**Y** 0</span></span>          |  <span data-ttu-id="43699-444">**Z** 0</span><span class="sxs-lookup"><span data-stu-id="43699-444">**Z** 0</span></span>  |

    |            |     <span data-ttu-id="43699-445">変換-スケール</span><span class="sxs-lookup"><span data-stu-id="43699-445">TRANSFORM - SCALE</span></span>     |           |
    | :---------:| :-----------------------: | :--------:|
    |  <span data-ttu-id="43699-446">**X** 1</span><span class="sxs-lookup"><span data-stu-id="43699-446">**X** 1</span></span>   |          <span data-ttu-id="43699-447">**Y** 1</span><span class="sxs-lookup"><span data-stu-id="43699-447">**Y** 1</span></span>          |  <span data-ttu-id="43699-448">**Z** 1</span><span class="sxs-lookup"><span data-stu-id="43699-448">**Z** 1</span></span>  |

10. <span data-ttu-id="43699-449">**GazeButton** 子が選択された状態で、**インスペクター** と **メッシュフィルター** を確認します。</span><span class="sxs-lookup"><span data-stu-id="43699-449">With the **GazeButton** child still selected, look at the **Inspector** and at the **Mesh Filter**.</span></span> <span data-ttu-id="43699-450">[ **メッシュ** 参照] フィールドの横にある小さなターゲットをクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-450">Click the little target next to the **Mesh** reference field:</span></span>

    ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-51.png)

11. <span data-ttu-id="43699-452">**[メッシュの選択**] ポップアップウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-452">A **Select Mesh** popup window will appear.</span></span> <span data-ttu-id="43699-453">**アセット** の一覧から **キューブ** メッシュをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-453">Double click the **Cube** mesh from the list of **Assets**.</span></span>

    ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-52.png)

12. <span data-ttu-id="43699-455">**メッシュフィルター** が更新され、現在は **キューブ** になります。</span><span class="sxs-lookup"><span data-stu-id="43699-455">The **Mesh Filter** will update, and now be a **Cube**.</span></span> <span data-ttu-id="43699-456">ここで、[**球 Collider** ] の横にある **歯車** アイコンをクリックし、[**コンポーネントの削除**] をクリックして、このオブジェクトから Collider を削除します。</span><span class="sxs-lookup"><span data-stu-id="43699-456">Now, click the **Gear** icon next to **Sphere Collider** and click **Remove Component**, to delete the collider from this object.</span></span>

    ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-53.png)

13. <span data-ttu-id="43699-458">**GazeButton** を選択したまま、**インスペクター** の下部にある [**コンポーネントの追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-458">With the **GazeButton** still selected, click the **Add Component** button at the bottom of the **Inspector**.</span></span> <span data-ttu-id="43699-459">検索フィールドに「 **box**」と入力します。 box **collider** がオプションになります。これをクリックすると、 **box collider** が **GazeButton** オブジェクトに追加されます。</span><span class="sxs-lookup"><span data-stu-id="43699-459">In the search field, type **box**, and **Box Collider** will be an option -- click that, to add a **Box Collider** to your **GazeButton** object.</span></span>

    ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-54.png)

14. <span data-ttu-id="43699-461">**GazeButton** が部分的に更新されるようになりました。別の外観になるように、新しい **素材** を作成します。これにより、最初のシーンのオブジェクトとは異なるオブジェクトとして認識しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="43699-461">The **GazeButton** is now partially updated, to look different, however, you will now create a new **Material**, so that it looks completely different, and is easier to recognize as a different object, than the object in the first scene.</span></span>

15. <span data-ttu-id="43699-462">[**プロジェクト] パネル** 内の [**素材**] フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="43699-462">Navigate to your **Materials** folder, within the **Project Panel**.</span></span> <span data-ttu-id="43699-463">**Buttonmaterial** マテリアルを複製します (キーボードの **Ctrl**  +  **D** キーを押すか、**素材** を左クリックし、[ファイルの **編集**] メニューオプションから [**複製**] を選択します)。</span><span class="sxs-lookup"><span data-stu-id="43699-463">Duplicate the **ButtonMaterial** Material (press **Ctrl** + **D** on the keyboard, or left-click the **Material**, then from the **Edit** file menu option, select **Duplicate**).</span></span>

    <span data-ttu-id="43699-464">![第7章--2 つの Unity シーンのセットアップ ](images/AzureLabs-Lab6-55.png)
     ![ 第7章: 2 つの unity シーンの設定](images/AzureLabs-Lab6-56.png)</span><span class="sxs-lookup"><span data-stu-id="43699-464">![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-55.png)
![Chapter 7 -- Setup the two Unity Scenes](images/AzureLabs-Lab6-56.png)</span></span>

16. <span data-ttu-id="43699-465">新しい **buttonmaterial** マテリアル (ここでは **buttonmaterial 1** という名前) を選択し、 **インスペクター** 内で [ **albedo** 色] ウィンドウをクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-465">Select the new **ButtonMaterial** Material (here named **ButtonMaterial 1**), and within the **Inspector**, click the **Albedo** color window.</span></span> <span data-ttu-id="43699-466">ポップアップが表示されます。ここで別の色を選択し (任意のものを選択)、ポップアップを閉じます。</span><span class="sxs-lookup"><span data-stu-id="43699-466">A popup will appear, where you can select another color (choose whichever you like), then close the popup.</span></span> <span data-ttu-id="43699-467">素材は独自のインスタンスであり、元のインスタンスとは異なります。</span><span class="sxs-lookup"><span data-stu-id="43699-467">The Material will be its own instance, and different to the original.</span></span>

    ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-57.png)

17. <span data-ttu-id="43699-469">新しい **素材** を **GazeButton** 子にドラッグして、その外観を完全に更新します。これにより、最初のシーンボタンから簡単に識別できるようになります。</span><span class="sxs-lookup"><span data-stu-id="43699-469">Drag the new **Material** onto the **GazeButton** child, to now completely update its look, so that it is easily distinguishable from the first scenes button.</span></span>

    ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-58.png)

18. <span data-ttu-id="43699-471">この時点で、UWP プロジェクトをビルドする前に、エディターでプロジェクトをテストすることができます。</span><span class="sxs-lookup"><span data-stu-id="43699-471">At this point you can test the project in the Editor before building the UWP project.</span></span>

    -  <span data-ttu-id="43699-472">**エディター** の [**再生**] ボタンを押して、ヘッドセットを磨耗します。</span><span class="sxs-lookup"><span data-stu-id="43699-472">Press the **Play** button in the **Editor** and wear your headset.</span></span>

        ![第7章--2 つの Unity シーンの設定](images/AzureLabs-Lab6-59.png)

19. <span data-ttu-id="43699-474">2つの **GazeButton** オブジェクトを見て、1番目と2番目のビデオを切り替えます。</span><span class="sxs-lookup"><span data-stu-id="43699-474">Look at the two **GazeButton** objects to switch between the first and second video.</span></span>

## <a name="chapter-8---build-the-uwp-solution"></a><span data-ttu-id="43699-475">章 8-UWP ソリューションのビルド</span><span class="sxs-lookup"><span data-stu-id="43699-475">Chapter 8 - Build the UWP Solution</span></span>

<span data-ttu-id="43699-476">エディターにエラーがないことを確認したら、ビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="43699-476">Once you have ensured that the editor has no errors, you are ready to Build.</span></span>

<span data-ttu-id="43699-477">ビルドするには:</span><span class="sxs-lookup"><span data-stu-id="43699-477">To Build:</span></span>

1.  <span data-ttu-id="43699-478">[ **ファイル > 保存**] をクリックして、現在のシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="43699-478">Save the current scene by clicking on **File > Save**.</span></span>

2.  <span data-ttu-id="43699-479">**Unity C \# プロジェクト** と呼ばれるチェックボックスをオンにします (ビルドの完了後にクラスを編集できるため、これは重要です)。</span><span class="sxs-lookup"><span data-stu-id="43699-479">Check the box called **Unity C\# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

3.  <span data-ttu-id="43699-480">[ **ファイル > ビルド設定**] にアクセスし、[ **ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-480">Go to **File > Build Settings**, click on **Build**.</span></span>

4.  <span data-ttu-id="43699-481">ソリューションをビルドするフォルダーを選択するように求められます。</span><span class="sxs-lookup"><span data-stu-id="43699-481">You will be prompted to select the folder where you want to build the Solution.</span></span>

5.  <span data-ttu-id="43699-482">**ビルド** フォルダーを作成し、そのフォルダー内で、適切な名前を指定して別のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="43699-482">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

6.  <span data-ttu-id="43699-483">新しいフォルダーをクリックし、[ **フォルダーの選択**] をクリックします。そのフォルダーを選択して、その場所でビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="43699-483">Click your new folder and then click **Select Folder**, so to choose that folder, to begin the build at that location.</span></span>

    <span data-ttu-id="43699-484">![第8章--UWP ソリューションのビルド ](images/AzureLabs-Lab6-60.png)
     ![ chapter 8--uwp ソリューションのビルド](images/AzureLabs-Lab6-61.png)</span><span class="sxs-lookup"><span data-stu-id="43699-484">![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-60.png)
![Chapter 8 -- Build the UWP Solution](images/AzureLabs-Lab6-61.png)</span></span>

7.  <span data-ttu-id="43699-485">Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で **ファイルエクスプローラー** ウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="43699-485">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build.</span></span>

## <a name="chapter-9---deploy-on-local-machine"></a><span data-ttu-id="43699-486">第9章-ローカルコンピューターへのデプロイ</span><span class="sxs-lookup"><span data-stu-id="43699-486">Chapter 9 - Deploy on Local Machine</span></span>

<span data-ttu-id="43699-487">ビルドが完了すると、ビルドの場所に [ **ファイルエクスプローラー** ] ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="43699-487">Once the build has been completed, a **File Explorer** window will appear at the location of your build.</span></span> <span data-ttu-id="43699-488">という名前で作成したフォルダーを開き、そのフォルダー内のソリューション (.sln) ファイルをダブルクリックして、Visual Studio 2017 でソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="43699-488">Open the Folder you named and built to, then double click on the solution (.sln) file within that folder, to open your solution with Visual Studio 2017.</span></span>

<span data-ttu-id="43699-489">残りの作業は、お使いのコンピューター (または *ローカルコンピューター*) にアプリを配置することだけです。</span><span class="sxs-lookup"><span data-stu-id="43699-489">The only thing left to do is deploy your app to your computer (or *Local Machine*).</span></span>

<span data-ttu-id="43699-490">ローカルコンピューターに配置するには:</span><span class="sxs-lookup"><span data-stu-id="43699-490">To deploy to Local Machine:</span></span>

1.  <span data-ttu-id="43699-491">**Visual Studio 2017** で、先ほど作成したソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="43699-491">In **Visual Studio 2017**, open the solution file that has just been created.</span></span>

2.  <span data-ttu-id="43699-492">**ソリューションプラットフォーム** で、[ **X86, ローカルコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="43699-492">In the **Solution Platform**, select **x86, Local Machine**.</span></span>

3.  <span data-ttu-id="43699-493">**ソリューション構成** で、[**デバッグ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="43699-493">In the **Solution Configuration** select **Debug**.</span></span>

    ![第9章--ローカルコンピューターへのデプロイ](images/AzureLabs-Lab6-62.png)

4.  <span data-ttu-id="43699-495">次に、ソリューションにパッケージを復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="43699-495">You will now need to restore any packages to your solution.</span></span> <span data-ttu-id="43699-496">**ソリューション** を右クリックし、[**ソリューションの NuGet パッケージの復元...** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="43699-496">Right-click on your **Solution**, and click **Restore NuGet Packages for Solution...**</span></span>

    > [!NOTE] 
    > <span data-ttu-id="43699-497">これは、Unity によって構築されたパッケージが、ローカルマシン参照を操作するためにターゲットにする必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="43699-497">This is done because the packages which Unity built need to be targeted to work with your local machines references.</span></span>

5.  <span data-ttu-id="43699-498">[ **ビルド] メニュー** の [ **ソリューションの配置** ] をクリックして、アプリケーションをコンピューターにサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="43699-498">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span> <span data-ttu-id="43699-499">まず、Visual Studio によってアプリケーションがビルドされ、配置されます。</span><span class="sxs-lookup"><span data-stu-id="43699-499">Visual Studio will first build and then deploy your application.</span></span>

6.  <span data-ttu-id="43699-500">アプリがインストール済みのアプリの一覧に表示され、起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="43699-500">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

    ![第9章--ローカルコンピューターへのデプロイ](images/AzureLabs-Lab6-63.png)

<span data-ttu-id="43699-502">Mixed Reality アプリケーションを実行すると、アプリ内で使用した **Insideoutsphere** モデル内に配置されます。</span><span class="sxs-lookup"><span data-stu-id="43699-502">When you run the Mixed Reality application, you will you be within the **InsideOutSphere** model which you used within your app.</span></span> <span data-ttu-id="43699-503">この球は、ビデオがストリーミングされる場所になります。これにより、着信ビデオ (この観点では客席でした) の360度のビューが提供されます。</span><span class="sxs-lookup"><span data-stu-id="43699-503">This sphere will be where the video will be streamed to, providing a 360-degree view, of the incoming video (which was filmed for this kind of perspective).</span></span> <span data-ttu-id="43699-504">ビデオが読み込まれるまでに数秒かかる場合、アプリには、使用可能なインターネット速度が適用されます。ビデオをフェッチしてからダウンロードする必要があるので、アプリにストリーミングします。</span><span class="sxs-lookup"><span data-stu-id="43699-504">Do not be surprised if the video takes a couple of seconds to load, your app is subject to your available Internet speed, as the video needs to be fetched and then downloaded, so to stream into your app.</span></span>
<span data-ttu-id="43699-505">準備ができたら、シーンを変更し、2番目のビデオを開いて、赤い球で整理します。</span><span class="sxs-lookup"><span data-stu-id="43699-505">When you are ready, change scenes and open your second video, by gazing at the red sphere!</span></span> <span data-ttu-id="43699-506">次に、2番目のシーンで blue キューブを使用して、戻ってもかまいません。</span><span class="sxs-lookup"><span data-stu-id="43699-506">Then feel free to go back, using the blue cube in the second scene!</span></span>

## <a name="your-finished-azure-media-service-application"></a><span data-ttu-id="43699-507">完成した Azure Media Service アプリケーション</span><span class="sxs-lookup"><span data-stu-id="43699-507">Your finished Azure Media Service application</span></span>
 
<span data-ttu-id="43699-508">これで、Azure Media Services を利用して360ビデオをストリーミングする mixed reality アプリが作成されました。</span><span class="sxs-lookup"><span data-stu-id="43699-508">Congratulations, you built a mixed reality app that leverages the Azure Media Service to stream 360 videos.</span></span>

![ラボの結果](images/AzureLabs-Lab6-00.png)

![ラボの結果](images/AzureLabs-Lab6-01.png)

## <a name="bonus-exercises"></a><span data-ttu-id="43699-511">ボーナスの演習</span><span class="sxs-lookup"><span data-stu-id="43699-511">Bonus Exercises</span></span>

<span data-ttu-id="43699-512">**演習1**</span><span class="sxs-lookup"><span data-stu-id="43699-512">**Exercise 1**</span></span>

<span data-ttu-id="43699-513">このチュートリアルでは、1つのシーンのみを使用してビデオを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="43699-513">It is entirely possible to only use a single scene to change videos within this tutorial.</span></span> <span data-ttu-id="43699-514">アプリケーションを試し、1つのシーンにします。</span><span class="sxs-lookup"><span data-stu-id="43699-514">Experiment with your application and make it into a single scene!</span></span> <span data-ttu-id="43699-515">場合によっては、ミックスに別のビデオを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="43699-515">Perhaps even add another video to the mix.</span></span>

<span data-ttu-id="43699-516">**演習2**</span><span class="sxs-lookup"><span data-stu-id="43699-516">**Exercise 2**</span></span>

<span data-ttu-id="43699-517">Azure と Unity を試し、インターネット接続の強度に応じて、別のファイルサイズでビデオを自動的に選択するアプリの機能を実装します。</span><span class="sxs-lookup"><span data-stu-id="43699-517">Experiment with Azure and Unity, and attempt to implement the ability for the app to automatically select a video with a different file size, depending on the strength of an Internet connection.</span></span>