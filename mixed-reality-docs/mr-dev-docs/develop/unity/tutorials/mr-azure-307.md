---
title: MR と Azure 307-Machine learning
description: このコースでは、mixed reality アプリケーション内で Azure Machine Learning Studio (クラシック) を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure、mixed reality、academy、unity、チュートリアル、api、機械学習、ml、machine learning studio、hololens、イマーシブ、vr、Windows 10、Visual Studio
ms.openlocfilehash: 3bb50c146e11a340f4223d71dd401ac2b84dd6d4
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679481"
---
# <a name="mr-and-azure-307-machine-learning"></a><span data-ttu-id="ebb5f-104">MR と Azure 307:機械学習</span><span class="sxs-lookup"><span data-stu-id="ebb5f-104">MR and Azure 307: Machine learning</span></span>

<br>

>[!NOTE]
><span data-ttu-id="ebb5f-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="ebb5f-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="ebb5f-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="ebb5f-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="ebb5f-109">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="ebb5f-110">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

![最終製品-開始](images/AzureLabs-Lab7-0.png)

<span data-ttu-id="ebb5f-112">このコースでは、Azure Machine Learning Studio (クラシック) を使用して Machine Learning (ML) 機能を mixed reality アプリケーションに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-112">In this course, you will learn how to add Machine Learning (ML) capabilities to a mixed reality application using Azure Machine Learning Studio (classic).</span></span>

<span data-ttu-id="ebb5f-113">*Azure Machine Learning Studio (クラシック)* は Microsoft のサービスであり、開発者は大量の機械学習アルゴリズムを使用できます。これは、データの入力、出力、準備、および視覚化に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-113">*Azure Machine Learning Studio (classic)* is a Microsoft service, which provides developers with a large number of machine learning algorithms, which can help with data input, output, preparation, and visualization.</span></span> <span data-ttu-id="ebb5f-114">これらのコンポーネントから、予測分析実験を開発し、それを反復処理して、モデルのトレーニングに使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-114">From these components, it is then possible to develop a predictive analytics experiment, iterate on it, and use it to train your model.</span></span> <span data-ttu-id="ebb5f-115">次のトレーニングでは、Azure クラウド内でモデルを操作できるようになり、新しいデータをスコア付けできるようになります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-115">Following training, you can make your model operational within the Azure cloud, so that it can then score new data.</span></span> <span data-ttu-id="ebb5f-116">詳細については、 [Azure Machine Learning Studio (クラシック) のページ](https://azure.microsoft.com/services/machine-learning-studio/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-116">For more information, visit the [Azure Machine Learning Studio (classic) page](https://azure.microsoft.com/services/machine-learning-studio/).</span></span>

<span data-ttu-id="ebb5f-117">このコースを完了すると、現実のイマーシブヘッドセットアプリケーションが完成し、次の操作方法を学習できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-117">Having completed this course, you will have a mixed reality immersive headset application, and will have learned how do the following:</span></span>

1.  <span data-ttu-id="ebb5f-118">*Azure Machine Learning Studio (クラシック)* ポータルに売上データのテーブルを提供し、人気のあるアイテムの将来の売上を予測するためのアルゴリズムを設計します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-118">Provide a table of sales data to the *Azure Machine Learning Studio (classic)* portal, and design an algorithm to predict future sales of popular items.</span></span>
2.  <span data-ttu-id="ebb5f-119">ML サービスから予測データを受信して解釈できる **Unity プロジェクト** を作成します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-119">Create a **Unity Project**, which can receive and interpret prediction data from the ML service.</span></span>
3.  <span data-ttu-id="ebb5f-120">Predication データを **Unity プロジェクト** 内に視覚的に表示し、最も人気のある販売品目を棚に提供します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-120">Display the predication data visually within the **Unity Project**, through providing the most popular sales items, on a shelf.</span></span>

<span data-ttu-id="ebb5f-121">アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="ebb5f-122">このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-122">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="ebb5f-123">このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="ebb5f-124">このコースは自己完結型のチュートリアルであり、他の Mixed Reality ラボに直接は関与しません。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-124">This course is a self-contained tutorial, which does not directly involve any other Mixed Reality Labs.</span></span>

## <a name="device-support"></a><span data-ttu-id="ebb5f-125">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="ebb5f-125">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="ebb5f-126">コース</span><span class="sxs-lookup"><span data-stu-id="ebb5f-126">Course</span></span></th><th style="width:150px"> <span data-ttu-id="ebb5f-127"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="ebb5f-127"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="ebb5f-128"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="ebb5f-128"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="ebb5f-129">MR と Azure 307:機械学習</span><span class="sxs-lookup"><span data-stu-id="ebb5f-129">MR and Azure 307: Machine learning</span></span></td><td style="text-align: center;"> <span data-ttu-id="ebb5f-130">✔️</span><span class="sxs-lookup"><span data-stu-id="ebb5f-130">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="ebb5f-131">✔️</span><span class="sxs-lookup"><span data-stu-id="ebb5f-131">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="ebb5f-132">このコースでは主に Windows Mixed Reality イマーシブ (VR) ヘッドセットに焦点を当てていますが、このコースで学習した内容を Microsoft HoloLens に適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-132">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="ebb5f-133">このコースに従うと、HoloLens をサポートするために必要となる可能性のある変更に関する注意事項が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-133">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="ebb5f-134">HoloLens を使用する場合、音声キャプチャ中にエコーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-134">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ebb5f-135">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ebb5f-135">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="ebb5f-136">このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-136">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="ebb5f-137">また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証されたものを表します (2018 年5月)。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-137">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="ebb5f-138">[「ツールのインストール](../../install-the-tools.md)」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものよりも新しいソフトウェアで見つかったものと完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-138">You are free to use the latest software, as listed within the [install the tools article](../../install-the-tools.md), though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="ebb5f-139">このコースでは、次のハードウェアとソフトウェアをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-139">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="ebb5f-140">開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-140">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="ebb5f-141">開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="ebb5f-141">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ebb5f-142">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="ebb5f-142">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ebb5f-143">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="ebb5f-143">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="ebb5f-144">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ebb5f-144">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="ebb5f-145">[Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](../../../hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="ebb5f-145">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](../../../hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="ebb5f-146">Azure のセットアップと ML のデータ取得のためのインターネットアクセス</span><span class="sxs-lookup"><span data-stu-id="ebb5f-146">Internet access for Azure setup and ML data retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="ebb5f-147">開始する前に</span><span class="sxs-lookup"><span data-stu-id="ebb5f-147">Before you start</span></span>

<span data-ttu-id="ebb5f-148">このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-148">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 

## <a name="chapter-1---azure-storage-account-setup"></a><span data-ttu-id="ebb5f-149">章 1-Azure Storage アカウントのセットアップ</span><span class="sxs-lookup"><span data-stu-id="ebb5f-149">Chapter 1 - Azure Storage Account setup</span></span>

<span data-ttu-id="ebb5f-150">Azure Translator API を使用するには、アプリケーションで使用できるようにサービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-150">To use the Azure Translator API, you will need to configure an instance of the service to be made available to your application.</span></span>
1.  <span data-ttu-id="ebb5f-151">[Azure Portal](https://portal.azure.com)にログインします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-151">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="ebb5f-152">まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-152">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="ebb5f-153">このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-153">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="ebb5f-154">ログインしたら、左側のメニューの [ **ストレージアカウント** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-154">Once you are logged in, click on **Storage Accounts** in the left menu.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-1.png)

    > [!NOTE]
    > <span data-ttu-id="ebb5f-156">新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-156">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="ebb5f-157">[ **ストレージアカウント** ] タブで、[ **追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-157">On the **Storage Accounts** tab, click on **Add**.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-2.png)

4.  <span data-ttu-id="ebb5f-159">[ **ストレージアカウントの作成** ] パネルで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-159">In the **Create Storage Account** panel:</span></span>

    1.  <span data-ttu-id="ebb5f-160">アカウントの **名前** を挿入します。このフィールドには数字と小文字のみを使用できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-160">Insert a **Name** for your account, be aware this field only accepts numbers, and lowercase letters.</span></span>
    2.  <span data-ttu-id="ebb5f-161">[ **デプロイモデル] で、** [ **リソースマネージャー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-161">For **Deployment model,** select **Resource manager**.</span></span>
    3.  <span data-ttu-id="ebb5f-162">[ **アカウントの種類**] で、[ **ストレージ (汎用 v1)**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-162">For **Account kind**, select **Storage (general purpose v1)**.</span></span>
    4.  <span data-ttu-id="ebb5f-163">**[パフォーマンス]** には **[Standard]** を選択します</span><span class="sxs-lookup"><span data-stu-id="ebb5f-163">For **Performance**, select **Standard**.</span></span>
    5.  <span data-ttu-id="ebb5f-164">**レプリケーション** の場合は、[**読み取りアクセス-geo 冗長ストレージ (RA-GRS)**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-164">For **Replication** select **Read-access-geo-redundant storage (RA-GRS)**.</span></span>
    6.  <span data-ttu-id="ebb5f-165">**安全な転送** は無効のまま **に** しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-165">Leave **Secure transfer required** as **Disabled**.</span></span>
    7.  <span data-ttu-id="ebb5f-166">**サブスクリプション** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-166">Select a **Subscription**.</span></span>
    4. <span data-ttu-id="ebb5f-167">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-167">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ebb5f-168">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-168">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ebb5f-169">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-169">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="ebb5f-170">Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-170">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>
    
    5.  <span data-ttu-id="ebb5f-171">リソースグループの **場所** を決定します (新しいリソースグループを作成している場合)。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-171">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ebb5f-172">この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-172">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ebb5f-173">一部の Azure 資産は、特定のリージョンでのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-173">Some Azure assets are only available in certain regions.</span></span>

5.  <span data-ttu-id="ebb5f-174">また、このサービスに適用されている使用条件を理解していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-174">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-3.png)

6.  <span data-ttu-id="ebb5f-176">[ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-176">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

7.  <span data-ttu-id="ebb5f-177">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-177">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Storage アカウントのセットアップ](images/AzureLabs-Lab7-4.png)

## <a name="chapter-2---the-azure-machine-learning-studio--classic"></a><span data-ttu-id="ebb5f-179">Chapter 2-Azure Machine Learning Studio (クラシック)</span><span class="sxs-lookup"><span data-stu-id="ebb5f-179">Chapter 2 - The Azure Machine Learning Studio  (classic)</span></span>

<span data-ttu-id="ebb5f-180">*Azure Machine Learning* を使用するには、アプリケーションで使用できるように Machine Learning サービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-180">To use the *Azure Machine Learning*, you will need to configure an instance of the Machine Learning service to be made available to your application.</span></span>

1.  <span data-ttu-id="ebb5f-181">Azure Portal で、左上隅にある [ **新規** ] をクリックし、 **Machine Learning Studio ワークスペース** を検索して **、enter キーを押します**。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-181">In the Azure Portal, click on **New** in the top left corner, and search for **Machine Learning Studio Workspace**, press **Enter**.</span></span>

    ![Azure Machine Learning Studio (クラシック)](images/AzureLabs-Lab7-5.png)

2.  <span data-ttu-id="ebb5f-183">新しいページには、 **Machine Learning Studio ワークスペース**  サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-183">The new page will provide a description of the **Machine Learning Studio Workspace**  service.</span></span> <span data-ttu-id="ebb5f-184">このプロンプトの左下にある [ **作成** ] ボタンをクリックして、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-184">At the bottom left of this prompt, click the **Create** button, to create an association with this service.</span></span>

3.  <span data-ttu-id="ebb5f-185">[ **作成**] をクリックすると、新しい **Machine Learning Studio サービス** に関する詳細を指定する必要があるパネルが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-185">Once you have clicked on **Create**, a panel will appear where you need to provide some details about your new **Machine Learning Studio service**:</span></span>

    1.  <span data-ttu-id="ebb5f-186">このサービスインスタンスに必要な **ワークスペース名** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-186">Insert your desired **Workspace name** for this service instance.</span></span>

    2.  <span data-ttu-id="ebb5f-187">**サブスクリプション** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-187">Select a **Subscription**.</span></span>

    3. <span data-ttu-id="ebb5f-188">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-188">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="ebb5f-189">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-189">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="ebb5f-190">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-190">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="ebb5f-191">Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-191">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    4.  <span data-ttu-id="ebb5f-192">リソースグループの **場所** を決定します (新しいリソースグループを作成している場合)。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-192">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="ebb5f-193">この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-193">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="ebb5f-194">一部の Azure 資産は、特定のリージョンでのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-194">Some Azure assets are only available in certain regions.</span></span> <span data-ttu-id="ebb5f-195">前の章で Azure Storage の作成に使用したものと同じリソースグループを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-195">You should use the same resource group that you used for creating the Azure Storage in the previous Chapter.</span></span>

    5.  <span data-ttu-id="ebb5f-196">[ **ストレージアカウント** ] セクションで、[既存のものを **使用**] をクリックし、ドロップダウンメニューをクリックします。そこから、最後の章で作成した **ストレージアカウント** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-196">For the **Storage account** section, click **Use existing**, then click the dropdown menu, and from there, click the **Storage Account** you created in the last Chapter.</span></span>

    6.  <span data-ttu-id="ebb5f-197">ドロップダウンメニューから適切な **ワークスペースの価格レベル** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-197">Select the appropriate **Workspace pricing tier** for you, from the dropdown menu.</span></span>

    7.  <span data-ttu-id="ebb5f-198">[ **Web サービスプラン** ] セクションで、[新規 **作成**] **を** クリックし、テキストフィールドに名前を挿入します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-198">Within the **Web service plan** section, click **Create** **new,** then insert a name for it in the text field.</span></span>

    8.  <span data-ttu-id="ebb5f-199">[ **Web サービスプランの価格レベル** ] セクションで、選択した価格レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-199">From the **Web service plan pricing tier** section, select the price tier of your choice.</span></span> <span data-ttu-id="ebb5f-200">**DEVTEST Standard** という開発テストレベルは、無料でご利用いただけます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-200">A development testing tier called **DEVTEST Standard** should be available to you at no charge.</span></span>

    9.  <span data-ttu-id="ebb5f-201">また、このサービスに適用されている使用条件を理解していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-201">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    10. <span data-ttu-id="ebb5f-202">**[作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-202">Click **Create**.</span></span>

        ![Azure Machine Learning Studio (クラシック)](images/AzureLabs-Lab7-6.png)

4.  <span data-ttu-id="ebb5f-204">[ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-204">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>

5.  <span data-ttu-id="ebb5f-205">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-205">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Azure Machine Learning Studio (クラシック)](images/AzureLabs-Lab7-7.png)

6.  <span data-ttu-id="ebb5f-207">通知をクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-207">Click on the notification to explore your new Service instance.</span></span>

    ![Azure Machine Learning Studio (クラシック)](images/AzureLabs-Lab7-8.png)

7.  <span data-ttu-id="ebb5f-209">通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-209">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span>

8.  <span data-ttu-id="ebb5f-210">表示されたページの [ **追加リンク** ] セクションで [ **Machine Learning Studio の起動**] をクリックすると、ブラウザーが **Machine Learning Studio** ポータルに送信されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-210">In the page displayed, under the **Additional Links** section, click **Launch Machine Learning Studio**, which will direct your browser to the **Machine Learning Studio** portal.</span></span>

    ![Azure Machine Learning Studio (クラシック)](images/AzureLabs-Lab7-9.png)

9.  <span data-ttu-id="ebb5f-212">右上または中央にある [ **サインイン** ] ボタンを使用して、Machine Learning Studio (クラシック) にログインします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-212">Use the **Sign In** button, at the top right or in the center, to log into your Machine Learning Studio (classic).</span></span>

    ![Azure Machine Learning Studio (クラシック)](images/AzureLabs-Lab7-10.png)


## <a name="chapter-3---the-machine-learning-studio-classic-dataset-setup"></a><span data-ttu-id="ebb5f-214">第3章-Machine Learning Studio (クラシック): データセットのセットアップ</span><span class="sxs-lookup"><span data-stu-id="ebb5f-214">Chapter 3 - The Machine Learning Studio (classic): Dataset setup</span></span>

<span data-ttu-id="ebb5f-215">Machine Learning アルゴリズムが動作する方法の1つは、既存のデータを分析し、既存のデータセットに基づいて将来の結果を予測することです。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-215">One of the ways Machine Learning algorithms work is by analyzing existing data and then attempting to predict future results based on the existing data set.</span></span> <span data-ttu-id="ebb5f-216">これは一般に、既存のデータが多いほど、将来の結果を予測するアルゴリズムの方が優れていることを意味します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-216">This generally means that the more existing data you have, the better the algorithm will be at predicting future results.</span></span>

<span data-ttu-id="ebb5f-217">このコースでは、 [Productstablecsv と](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip)いうサンプルテーブルが提供されており、ここでダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-217">A sample table is provided to you, for this course, called [ProductsTableCSV and can be downloaded here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/MR%20and%20Azure%20307%20-%20Machine%20learning.zip).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ebb5f-218">上記の .zip ファイルには、 **Productstablecsv** と **unitypackage** の両方が含まれています。これについては、 [第6章](#chapter-6---importing-the-mlproducts-unity-package)で必要になります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-218">The above .zip file contains both the **ProductsTableCSV** and the **.unitypackage**, which you will need in [Chapter 6](#chapter-6---importing-the-mlproducts-unity-package).</span></span> <span data-ttu-id="ebb5f-219">このパッケージは、この章にも記載されていますが、csv ファイルとは別のものです。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-219">This package is also provided within that Chapter, though separate to the csv file.</span></span>

<span data-ttu-id="ebb5f-220">このサンプルデータセットには、2017年の各日の1時間ごとに最適な販売オブジェクトのレコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-220">This sample data set contains a record of the best-selling objects at every hour of each day of the year 2017.</span></span>
        
![Machine Learning Studio (クラシック): データセットのセットアップ](images/AzureLabs-Lab7-11.png)

<span data-ttu-id="ebb5f-222">たとえば、2017年の午前1時に、1pm (時間 13) では、最も売れた項目がソルトと胡椒になりました。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-222">For example, on day 1 of 2017, at 1pm (hour 13), the best-selling item was salt and pepper.</span></span>

<span data-ttu-id="ebb5f-223">このサンプルテーブルには、9998のエントリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-223">This sample table contains 9998 entries.</span></span>

1.  <span data-ttu-id="ebb5f-224">**Machine Learning Studio (クラシック)** ポータルに戻り、このテーブルを ML の **データセット** として追加します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-224">Head back to the **Machine Learning Studio (classic)** portal, and add this table as a **Dataset** for your ML.</span></span> <span data-ttu-id="ebb5f-225">これを行うには、画面の左下隅にある [ **+ 新規** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-225">Do this by clicking the **+ New** button in the bottom left corner of the screen.</span></span>

    ![Machine Learning Studio (クラシック): データセットのセットアップ](images/AzureLabs-Lab7-12.png)

2.  <span data-ttu-id="ebb5f-227">セクションは下部に表示され、左側にナビゲーションパネルがあります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-227">A section will come up from the bottom, and within that there is navigation panel on the left.</span></span> <span data-ttu-id="ebb5f-228">[ **データセット**] をクリックし、右側の [ **ローカルファイル**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-228">Click **Dataset**, then to the right of that, **From Local File**.</span></span>

    ![Machine Learning Studio (クラシック): データセットのセットアップ](images/AzureLabs-Lab7-13.png)

3.  <span data-ttu-id="ebb5f-230">新しい **データセット** をアップロードするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-230">Upload the new **Dataset** by following these steps:</span></span>

    1. <span data-ttu-id="ebb5f-231">[アップロード] ウィンドウが表示されます。このウィンドウで、新しいデータセットのハードドライブを **参照** できます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-231">The upload window will appear, where you can **Browse** your hard drive for the new dataset.</span></span>

        ![Machine Learning Studio (クラシック): データセットのセットアップ](images/AzureLabs-Lab7-14.png)

    2.  <span data-ttu-id="ebb5f-233">選択してアップロードウィンドウに戻ると、チェックボックスはオンのままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-233">Once selected, and back in the upload window, leave the checkbox unticked.</span></span>

    3.  <span data-ttu-id="ebb5f-234">下のテキストフィールドで、データセットの名前として「 **ProductsTableCSV.csv** 」と入力します (ただし、自動的に追加されます)。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-234">In the text field below, enter **ProductsTableCSV.csv** as the name for the dataset (though should automatically be added).</span></span>

    4.  <span data-ttu-id="ebb5f-235">[ **種類**] のドロップダウンメニューを使用して、 **ヘッダー (.csv) を含む汎用 CSV ファイル** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-235">Using the dropdown menu for **Type**, select **Generic CSV File with a header (.csv)**.</span></span>

    5.  <span data-ttu-id="ebb5f-236">アップロードウィンドウの右下にあるティックを押すと、 **データセット** がアップロードされます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-236">Press the tick in the bottom right of the upload window, and your **Dataset** will be uploaded.</span></span>

## <a name="chapter-4---the-machine-learning-studio-classic-the-experiment"></a><span data-ttu-id="ebb5f-237">Chapter 4-Machine Learning Studio (クラシック): 実験</span><span class="sxs-lookup"><span data-stu-id="ebb5f-237">Chapter 4 - The Machine Learning Studio (classic): The Experiment</span></span>

<span data-ttu-id="ebb5f-238">機械学習システムを構築する前に、実験を作成して、データに関する理論を検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-238">Before you can build your machine learning system, you will need to build an experiment, to validate your theory about your data.</span></span> <span data-ttu-id="ebb5f-239">結果によって、さらに多くのデータが必要かどうか、またはデータと考えられる結果の間に相関関係がないかどうかがわかります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-239">With the results, you will know whether you need more data, or if there is no correlation between the data and a possible outcome.</span></span>

<span data-ttu-id="ebb5f-240">実験の作成を開始するには:</span><span class="sxs-lookup"><span data-stu-id="ebb5f-240">To start creating an experiment:</span></span>

1.  <span data-ttu-id="ebb5f-241">ページの左下にある [ **+ 新規**] ボタンをもう一度クリックし、[**実験** 用の空の実験] をクリックし  >  **Blank Experiment** ます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-241">Click again on the **+ New** button on the bottom left of the page, then click on **Experiment** > **Blank Experiment**.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-15.png)

2.  <span data-ttu-id="ebb5f-243">空の実験で新しいページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-243">A new page will be displayed with a blank Experiment:</span></span>

3.  <span data-ttu-id="ebb5f-244">左側のパネルで、[**保存されたデータセット**  >  **マイデータセット**] を展開し、[ **productstablecsv** ] を **実験キャンバス** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-244">From the panel on the left expand **Saved Datasets** > **My Datasets** and drag the  **ProductsTableCSV** on to the **Experiment Canvas**.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-16.png)

4.  <span data-ttu-id="ebb5f-246">左側のパネルで、[**データ変換** の  >  **サンプルと分割**] を展開します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-246">In the panel on the left, expand **Data Transformation** > **Sample and Split**.</span></span> <span data-ttu-id="ebb5f-247">次に、[ **データの分割** ] 項目を **実験キャンバス** にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-247">Then drag the **Split Data** item in to the **Experiment Canvas**.</span></span> <span data-ttu-id="ebb5f-248">データの分割項目によって、データセットが2つの部分に分割されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-248">The Split Data item will split the data set into two parts.</span></span> <span data-ttu-id="ebb5f-249">機械学習アルゴリズムのトレーニングに使用する1つのパート。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-249">One part you will use for training the machine learning algorithm.</span></span> <span data-ttu-id="ebb5f-250">2番目の部分は、生成されたアルゴリズムの精度を評価するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-250">The second part will be used to evaluate the accuracy of the algorithm generated.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-17.png)

5.  <span data-ttu-id="ebb5f-252">右側のパネル (キャンバスの [データの分割] 項目が選択されている状態) で、 **最初の出力データセットの行の割合** を **0.7** に変更します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-252">In the right panel (while the Split Data item on the canvas is selected), edit the **Fraction of rows in the first output dataset** to **0.7**.</span></span> <span data-ttu-id="ebb5f-253">これにより、データは2つの部分に分割され、最初の部分はデータの70% になり、2番目の部分は残りの30% になります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-253">This will split the data into two parts, the first part will be 70% of the data, and the second part will be the remaining 30%.</span></span> <span data-ttu-id="ebb5f-254">データがランダムに分割されるようにするには、[ **ランダム分割** ] チェックボックスがオンのままになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-254">To ensure that the data is split randomly, make sure the **Randomized split** checkbox remains checked.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-18.png)

6.  <span data-ttu-id="ebb5f-256">キャンバスの **Productstablecsv** 項目のベースから分割データ項目の一番上に接続をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-256">Drag a connection from the base of the **ProductsTableCSV** item on the canvas to the top of the Split Data item.</span></span> <span data-ttu-id="ebb5f-257">これにより、項目が接続され、 **Productstablecsv** データセットの出力 (データ) が分割データ入力に送信されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-257">This will connect the items and send the **ProductsTableCSV** dataset output (the data) to the Split Data input.</span></span>  

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-19.png)

7.  <span data-ttu-id="ebb5f-259">左側の **実験** パネルで、[ **Machine Learning** トレーニング] を展開し  >  **Train** ます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-259">In the **Experiments** panel on the left side, expand **Machine Learning** > **Train**.</span></span> <span data-ttu-id="ebb5f-260">[ **モデルのトレーニング** ] 項目を実験キャンバスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-260">Drag the **Train Model** item out in to the Experiment canvas.</span></span> <span data-ttu-id="ebb5f-261">キャンバスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-261">Your canvas should look the same as the below.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-20.png)

8.  <span data-ttu-id="ebb5f-263">**_ 分割データ項目 *の* _bottom left_** 左下の [**モデルのトレーニング**] 項目の **右上** にある [接続] をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-263">From the **_bottom left_*_ of the _\* Split Data*\* item drag a connection to the **top right** of the **Train Model** item.</span></span> <span data-ttu-id="ebb5f-264">データセットからの最初の70% の分割は、アルゴリズムをトレーニングするために Train モデルによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-264">The first 70% split from the dataset will be used by the Train Model to train the algorithm.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-21.png)

9.  <span data-ttu-id="ebb5f-266">キャンバスで [ **モデルのトレーニング** ] 項目を選択し、[ **プロパティ** ] パネル (ブラウザーウィンドウの右側) で、[ **列セレクターの起動** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-266">Select the **Train Model** item on the canvas, and in the **Properties** panel (on the right-hand side of your browser window) click the **Launch column selector** button.</span></span>

10. <span data-ttu-id="ebb5f-267">テキストボックスに「 **product** 」と入力し、 **enter** キーを押します。 *製品* は、予測をトレーニングするための列として設定されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-267">In the text box type **product** and then press **Enter**, *product* will be set as a column to train predictions.</span></span> <span data-ttu-id="ebb5f-268">次に、右下隅にある **目盛り** をクリックして、選択ダイアログを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-268">Following this, click on the **tick** in the bottom-right corner to close the selection dialog.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-22.png)

11. <span data-ttu-id="ebb5f-270">**多クラスロジスティック回帰** アルゴリズムをトレーニングして、その日の時間と日付に基づいて販売された **製品** を予測します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-270">You are going to train a **Multiclass Logistic Regression** algorithm to predict the most sold **product** based on the hour of the day and the date.</span></span> <span data-ttu-id="ebb5f-271">Azure Machine Learning studio によって提供されるさまざまなアルゴリズムの詳細については、このドキュメントでは説明しません。ただし、 [Machine Learning アルゴリズム](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)の詳細については、「」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-271">It is beyond the scope of this document to explain the details of the different algorithms provided by the Azure Machine Learning studio, though, you can find out more from the [Machine Learning Algorithm Cheat Sheet](https://docs.microsoft.com/azure/machine-learning/studio/algorithm-cheat-sheet)</span></span>

12. <span data-ttu-id="ebb5f-272">左側の [実験項目] パネルで [ **Machine Learning**  >  のモデル分類の **初期化**] を展開  >  **Classification** し、**多クラスロジスティック回帰** 項目を実験キャンバスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-272">From the experiment items panel on the left, expand **Machine Learning** > **Initialize Model** > **Classification**, and drag the **Multiclass Logistic Regression** item on to the experiment canvas.</span></span>

13. <span data-ttu-id="ebb5f-273">**多クラスロジスティック回帰** の一番下にある出力を、[**モデルのトレーニング**] 項目の左上の入力に接続します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-273">Connect the output, from the bottom of the **Multiclass Logistic Regression**, to the top-left input of the **Train Model** item.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-23.png)

14. <span data-ttu-id="ebb5f-275">左側のパネルにある実験項目の一覧で [ **Machine Learning**  >  **スコア**] を展開し、[**モデルのスコア** 付け] 項目をキャンバスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-275">In list of experiment items in the panel on the left, expand **Machine Learning** > **Score**, and drag the **Score Model** item on to the canvas.</span></span>

15. <span data-ttu-id="ebb5f-276">**トレーニングモデル** の下部にある出力を、**スコアモデル** の左上の入力に接続します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-276">Connect the output, from the bottom of the **Train Model**, to the top-left input of the **Score Model**.</span></span>

16. <span data-ttu-id="ebb5f-277">分割された **データ** から、 **モデルのスコア** 付け項目の右上の入力に、右下の出力を接続します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-277">Connect the bottom-right output from **Split Data**, to the top-right input of the **Score Model** item.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-24.png)

17. <span data-ttu-id="ebb5f-279">左側のパネルにある **実験** 項目の一覧で、[ **Machine Learning**  >  **評価**] を展開し、[**モデルの評価**] 項目をキャンバスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-279">In the list of **Experiment** items in the panel on the left, expand **Machine Learning** > **Evaluate**, and drag the **Evaluate Model** item onto the canvas.</span></span>

18. <span data-ttu-id="ebb5f-280">**スコアモデル** の出力を、**評価モデル** の左上の入力に接続します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-280">Connect the output from the **Score Model** to the top-left input of the **Evaluate Model**.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-25.png)

19. <span data-ttu-id="ebb5f-282">最初の Machine Learning 実験を作成しました。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-282">You have built your first Machine Learning Experiment.</span></span> <span data-ttu-id="ebb5f-283">これで、実験を保存して実行できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-283">You can now save and run the experiment.</span></span> <span data-ttu-id="ebb5f-284">ページの下部にあるメニューで、[ **保存** ] ボタンをクリックして実験を保存し、[ **実行** ] をクリックして実験を開始します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-284">In the menu at the bottom of the page, click on the **Save** button to save your experiment and then click **Run** to the start the experiment.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-26.png)

20. <span data-ttu-id="ebb5f-286">キャンバスの右上にある実験の **状態** を確認できます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-286">You can see the **status** of the experiment in the top-right of the canvas.</span></span> <span data-ttu-id="ebb5f-287">実験が終了するまでしばらく待ちます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-287">Wait a few moments for the experiment to finish.</span></span>

    > <span data-ttu-id="ebb5f-288">ビッグ (実際の) データセットがある場合は、実験の実行に時間がかかる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-288">If you have a big (real world) dataset it is likely that the experiment could take hours to run.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-27.png)

21. <span data-ttu-id="ebb5f-290">キャンバスで [ **モデルの評価** ] 項目を右クリックし、コンテキストメニューから、 **評価結果** にマウスポインターを移動して、[ **視覚化**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-290">Right click on the **Evaluate Model** item in the canvas and from the context menu hover the mouse over **Evaluation Results**, then select **Visualize**.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-28.png)

22. <span data-ttu-id="ebb5f-292">予測された結果と実際の結果を示す評価結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-292">The evaluation results will be displayed showing the predicted outcomes versus the actual outcomes.</span></span> <span data-ttu-id="ebb5f-293">これにより、前に分割した元のデータセットの30% がモデルの評価に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-293">This uses the 30% of the original dataset, that was split earlier, for evaluating the model.</span></span> <span data-ttu-id="ebb5f-294">結果が最適ではないことがわかります。各行の最大数が列の強調表示された項目になるのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-294">You can see the results are not great, ideally you would have the highest number in each row be the highlighted item in the columns.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-29.png)

23. <span data-ttu-id="ebb5f-296">**結果** を閉じます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-296">Close the **Results**.</span></span>

24. <span data-ttu-id="ebb5f-297">新しくトレーニングされた Machine Learning モデルを使用するには、 **Web サービス** として公開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-297">To use your newly trained Machine Learning model you need to expose it as a **Web Service**.</span></span> <span data-ttu-id="ebb5f-298">これを行うには、ページの下部にあるメニューの [ **Web サービスの設定** ] メニュー項目をクリックし、[ **予測 Web サービス**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-298">To do this, click on the **Set Up Web Service** menu item in the menu at the bottom of the page, and click on **Predictive Web Service**.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-30.png)

25. <span data-ttu-id="ebb5f-300">新しいタブが作成され、新しい web サービスを作成するためにトレーニングモデルが結合されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-300">A new tab will be created, and the train model merged to create the new web service.</span></span> 

26. <span data-ttu-id="ebb5f-301">ページの下部にあるメニューで [ **保存**] をクリックし、[ **実行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-301">In the menu at the bottom of the page click **Save**, then click **Run**.</span></span> <span data-ttu-id="ebb5f-302">実験キャンバスの右上隅に更新された状態が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-302">You will see the status updated in the top-right corner of the experiment canvas.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-31.png)

27. <span data-ttu-id="ebb5f-304">実行が完了すると、[ **Web サービスのデプロイ** ] ボタンがページの下部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-304">Once it has finished running, a **Deploy Web Service** button will appear at the bottom of the page.</span></span> <span data-ttu-id="ebb5f-305">これで、web サービスをデプロイする準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-305">You are ready to deploy the web service.</span></span> <span data-ttu-id="ebb5f-306">ページの下部にあるメニューで、[ **Deploy Web Service** (クラシック)] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-306">Click **Deploy Web Service** (Classic) in the menu at the bottom of the page.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-32.png)

    > <span data-ttu-id="ebb5f-308">ブラウザーでポップアップ **を許可する** ように求められる場合があります。ただし、[デプロイ] ページが表示されない場合は、[ **Web サービスのデプロイ** ] をもう一度クリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-308">Your browser may prompt to allow a pop-up, which you should **allow**, though you may need to press **Deploy Web Service** again, if the deploy page does not show.</span></span> 

28. <span data-ttu-id="ebb5f-309">実験が作成されると、 **API キー** が表示される **ダッシュボード** ページにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-309">Once the Experiment has been created you will be redirected to a **Dashboard** page where you will have your **API Key** displayed.</span></span> <span data-ttu-id="ebb5f-310">その時点でメモ帳にコピーします。コードですぐに必要になります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-310">Copy it into a notepad for the moment, you will need it in your code very soon.</span></span> <span data-ttu-id="ebb5f-311">API キーを書き留めたら、キーの下にある [**既定のエンドポイント**] セクションの [**要求/応答**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-311">Once you have noted your API Key, click on the **REQUEST/RESPONSE** button in the **Default Endpoint** section underneath the Key.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-33.png)

    > [!NOTE] 
    > <span data-ttu-id="ebb5f-313">このページで [テスト] をクリックすると、入力データを入力して出力を表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-313">If you click Test in this page, you will be able to enter input data and view the output.</span></span> <span data-ttu-id="ebb5f-314">**日付** と **時刻** を入力します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-314">Enter the **day** and **hour**.</span></span> <span data-ttu-id="ebb5f-315">**製品** エントリを空白のままにします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-315">Leave the **product** entry blank.</span></span> <span data-ttu-id="ebb5f-316">次に、[ **確認** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-316">Then click the **Confirm** button.</span></span> <span data-ttu-id="ebb5f-317">ページの下部にある出力には、各製品が選択されている可能性を表す JSON が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-317">The output on the bottom of the page will show the JSON representing the likelihood of each product being the choice.</span></span>

29. <span data-ttu-id="ebb5f-318">新しい web ページが開き、Machine Learning Studio (クラシック) で必要とされる要求構造に関する指示といくつかの例が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-318">A new web page will open up, displaying the instructions and some examples about the Request structure required by the Machine Learning Studio (classic).</span></span> <span data-ttu-id="ebb5f-319">このページに表示されている **要求 URI** をメモ帳にコピーします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-319">Copy the **Request URI** displayed in this page, into your notepad.</span></span>

    ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-34.png)

<span data-ttu-id="ebb5f-321">これで、過去の購入データに基づいて販売される可能性の高い製品を提供する機械学習システムが構築されました。これは、その年の日付と時刻に関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-321">You have now built a machine learning system that provides the most likely product to be sold based on historical purchasing data, correlated with the time of the day and day of the year.</span></span>

<span data-ttu-id="ebb5f-322">Web サービスを呼び出すには、サービスエンドポイントの URL とサービスの API キーが必要です。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-322">To call the web service, you will need the URL for the service endpoint and an API Key for the service.</span></span> <span data-ttu-id="ebb5f-323">上部のメニューから [ **使用** ] タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-323">Click on the **Consume** tab, from the top menu.</span></span>

<span data-ttu-id="ebb5f-324">[ **従量課金** 情報] ページには、コードから web サービスを呼び出すために必要な情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-324">The **Consumption** Info page will display the information you will need to call the web service from your code.</span></span> <span data-ttu-id="ebb5f-325">**プライマリキー** と **要求-応答** URL のコピーを取得します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-325">Take a copy of the **Primary Key** and the **Request-Response** URL.</span></span> <span data-ttu-id="ebb5f-326">これらは、次の章で必要になります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-326">You will need these in the next Chapter.</span></span>

## <a name="chapter-5---setting-up-the-unity-project"></a><span data-ttu-id="ebb5f-327">章 5-Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="ebb5f-327">Chapter 5 - Setting up the Unity Project</span></span>

<span data-ttu-id="ebb5f-328">Mixed Reality のイマーシブヘッドセットをセットアップしてテストします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-328">Set up and test your Mixed Reality Immersive Headset.</span></span>

> [!NOTE]
>  <span data-ttu-id="ebb5f-329">このコースでは、モーションコントローラーは必要 **ありません** 。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-329">You will **not** require Motion Controllers for this course.</span></span> <span data-ttu-id="ebb5f-330">イマーシブヘッドセットの設定をサポートする必要がある場合は、 [ここ](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-330">If you need support setting up the Immersive Headset, please click [HERE](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

1.  <span data-ttu-id="ebb5f-331">**Unity** を開き、MR の "e" という名前の新しい unity プロジェクトを作成し **\_ ます。**</span><span class="sxs-lookup"><span data-stu-id="ebb5f-331">Open **Unity** and create a new Unity Project called **MR\_MachineLearning.**</span></span> <span data-ttu-id="ebb5f-332">プロジェクトの種類が **3d** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-332">Make sure the project type is set to **3D**.</span></span>

2.  <span data-ttu-id="ebb5f-333">Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-333">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="ebb5f-334">[設定の **編集**] に移動し、  >  **Preferences** 新しいウィンドウで [**外部ツール**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-334">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="ebb5f-335">**外部スクリプトエディター** を **Visual Studio 2017** に変更します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-335">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="ebb5f-336">[ **基本設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-336">Close the **Preferences** window.</span></span>

3.  <span data-ttu-id="ebb5f-337">次に、[**ファイル**  >  ] [**ビルドの設定**] に移動し、[プラットフォームの *_切り替え_*] _ ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-337">Next, go to **File** > **Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the \**_Switch Platform_* _ button.</span></span>

4.  <span data-ttu-id="ebb5f-338">また、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-338">Also make sure that:</span></span>

    1.  <span data-ttu-id="ebb5f-339">_ *ターゲットデバイス*\* は **任意のデバイス** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-339">_ *Target Device*\* is set to **Any Device**.</span></span>

        > <span data-ttu-id="ebb5f-340">Microsoft HoloLens の場合は、 **ターゲットデバイス** を *HoloLens* に設定します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-340">For the Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2.  <span data-ttu-id="ebb5f-341">**ビルドの種類** が **D3D** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-341">**Build Type** is set to **D3D**.</span></span>

    3.  <span data-ttu-id="ebb5f-342">**SDK** は、 **インストールされている最新のバージョン** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-342">**SDK** is set to **Latest installed**.</span></span>

    4.  <span data-ttu-id="ebb5f-343">**Visual Studio のバージョン** が、 **インストールされている最新** のバージョンに設定されています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-343">**Visual Studio Version** is set to **Latest installed**.</span></span>

    5.  <span data-ttu-id="ebb5f-344">**ビルドと実行** は **ローカルコンピューター** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-344">**Build and Run** is set to **Local Machine**.</span></span>

    6.  <span data-ttu-id="ebb5f-345">後で提供されているように、現時点で **は設定に** ついて心配しないでください。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-345">Do not worry about setting up **Scenes** right now, as these are provided later.</span></span>

    7.  <span data-ttu-id="ebb5f-346">ここでは、残りの設定は既定値のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-346">The remaining settings should be left as default for now.</span></span>

        ![Unity プロジェクトの設定](images/AzureLabs-Lab7-35.png)

5.  <span data-ttu-id="ebb5f-348">[ **ビルドの設定** ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 **インスペクター** が配置されている領域の関連パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-348">In the **Build Settings** window, click on the **Player Settings** button, this will open the related panel in the space where the **Inspector** is located.</span></span> 

6. <span data-ttu-id="ebb5f-349">このパネルでは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-349">In this panel, a few settings need to be verified:</span></span>

    1.  <span data-ttu-id="ebb5f-350">[ **その他の設定** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-350">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="ebb5f-351">**Scripting** **Runtime のバージョン** は **実験的** である必要があります (.net 4.6 と同等)</span><span class="sxs-lookup"><span data-stu-id="ebb5f-351">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent)</span></span>

        2. <span data-ttu-id="ebb5f-352">**スクリプトバックエンド** は \**_.net_* _ である必要があります</span><span class="sxs-lookup"><span data-stu-id="ebb5f-352">**Scripting Backend** should be \**_.NET_* _</span></span>

        3. <span data-ttu-id="ebb5f-353">_ *API 互換性レベル*\* は **.net 4.6** である必要があります</span><span class="sxs-lookup"><span data-stu-id="ebb5f-353">_ *API Compatibility Level*\* should be **.NET 4.6**</span></span>

            ![Unity プロジェクトの設定](images/AzureLabs-Lab7-36.png)

    2.  <span data-ttu-id="ebb5f-355">[ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-355">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="ebb5f-356">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="ebb5f-356">**InternetClient**</span></span>

            ![Unity プロジェクトの設定](images/AzureLabs-Lab7-37.png)

    3.  <span data-ttu-id="ebb5f-358">パネルの下の [ **XR settings** ( **発行の設定**] の下にあります) で、[ **サポートされている仮想現実**] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-358">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added</span></span>

        ![Unity プロジェクトの設定](images/AzureLabs-Lab7-38.png)

    

6.  <span data-ttu-id="ebb5f-360">**ビルド設定** に戻る *Unity C#* プロジェクトはグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-360">Back in **Build Settings** *Unity C#* Projects is no longer greyed out; tick the checkbox next to this.</span></span> 

7.  <span data-ttu-id="ebb5f-361">[ビルド設定] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-361">Close the Build Settings window.</span></span>

8.  <span data-ttu-id="ebb5f-362">プロジェクトを保存します (**ファイル > プロジェクトに保存** します)。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-362">Save your Project (**FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-6---importing-the-mlproducts-unity-package"></a><span data-ttu-id="ebb5f-363">第6章-MLProducts Unity パッケージのインポート</span><span class="sxs-lookup"><span data-stu-id="ebb5f-363">Chapter 6 - Importing the MLProducts Unity Package</span></span>

<span data-ttu-id="ebb5f-364">このコースでは、 [**unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage)という名前の Unity アセットパッケージをダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-364">For this course, you will need to download a Unity Asset Package called [**Azure-MR-307.unitypackage**](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20307%20-%20Machine%20learning/307-Scene-Setup.unitypackage).</span></span> <span data-ttu-id="ebb5f-365">このパッケージは、すべてのオブジェクトがあらかじめ構築されているシーンで完成しているので、すべての作業に専念できます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-365">This package comes complete with a scene, with all objects in that prebuilt, so you can focus on getting it all working.</span></span> <span data-ttu-id="ebb5f-366">**ShelfKeeper** スクリプトが用意されていますが、シーンのセットアップ構造ではパブリック変数のみが保持されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-366">The **ShelfKeeper** script is provided, though only holds the public variables, for the purpose of scene setup structure.</span></span> <span data-ttu-id="ebb5f-367">他のすべてのセクションを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-367">You will need to do all other sections.</span></span> 

<span data-ttu-id="ebb5f-368">このパッケージをインポートするには:</span><span class="sxs-lookup"><span data-stu-id="ebb5f-368">To import this package:</span></span>

1.  <span data-ttu-id="ebb5f-369">Unity ダッシュボードを使用して、画面の上部にあるメニューの [ **アセット** ] をクリックし、[ **パッケージのインポート, カスタムパッケージ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-369">With the Unity dashboard in front of you, click on **Assets** in the menu at the top of the screen, then click on **Import Package, Custom Package**.</span></span>

    ![MLProducts Unity パッケージをインポートしています](images/AzureLabs-Lab7-39.png)

2.  <span data-ttu-id="ebb5f-371">ファイルピッカーを使用して **unitypackage** パッケージを選択し、[ **開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-371">Use the file picker to select the **Azure-MR-307.unitypackage** package and click **Open**.</span></span>

3.  <span data-ttu-id="ebb5f-372">この資産のコンポーネントの一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-372">A list of components for this asset will be displayed to you.</span></span> <span data-ttu-id="ebb5f-373">インポートを確認するには、[ **インポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-373">Confirm the import by clicking **Import**.</span></span>

    ![MLProducts Unity パッケージをインポートしています](images/AzureLabs-Lab7-40.png)

4.  <span data-ttu-id="ebb5f-375">インポートが完了すると、一部の新しいフォルダーが Unity の [ **プロジェクト] パネル** に表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-375">Once it has finished importing, you will notice that some new folders have appeared in your Unity **Project Panel**.</span></span> <span data-ttu-id="ebb5f-376">これらは、3D モデルと、作業する事前に作成されたシーンの一部であるそれぞれのマテリアルです。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-376">Those are the 3D models and the respective materials that are part of the pre-made scene you will work on.</span></span> <span data-ttu-id="ebb5f-377">このコースでは、大部分のコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-377">You will write the majority of the code in this course.</span></span>

    ![MLProducts Unity パッケージをインポートしています](images/AzureLabs-Lab7-41.png)

5.  <span data-ttu-id="ebb5f-379">[ **プロジェクトパネル]** フォルダー内の [ **シーン** ] フォルダーをクリックし、内部のシーン ( **MR_MachineLearningScene**) をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-379">Within the **Project Panel** folder, click on the **Scenes** folder and double click on the scene inside (called **MR_MachineLearningScene**).</span></span> <span data-ttu-id="ebb5f-380">シーンが開きます (下図を参照)。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-380">The scene will open (see image below).</span></span> <span data-ttu-id="ebb5f-381">赤いひし形が欠けている場合は、[**ゲーム] パネル** の右上にある [**ギズモ**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-381">If the red diamonds are missing, simply click the **Gizmos** button, at the top right of the **Game Panel**.</span></span>

    ![MLProducts Unity パッケージをインポートしています](images/AzureLabs-Lab7-44.png)

## <a name="chapter-7---checking-the-dlls-in-unity"></a><span data-ttu-id="ebb5f-383">第7章-Unity での Dll のチェック</span><span class="sxs-lookup"><span data-stu-id="ebb5f-383">Chapter 7 - Checking the DLLs in Unity</span></span>

<span data-ttu-id="ebb5f-384">(シリアル化と逆シリアル化に使用される) JSON ライブラリの使用を活用するために、作成したパッケージに Newtonsoft DLL が実装されています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-384">To leverage the use of JSON libraries (used for serializing and deserializing), a Newtonsoft DLL has been implemented with the package you brought in.</span></span> <span data-ttu-id="ebb5f-385">ライブラリには適切な構成が必要です (特に、コードが動作していない問題が発生している場合)。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-385">The library should have the correct configuration, though it is worth checking (particularly if you are having issues with code not working).</span></span> 

<span data-ttu-id="ebb5f-386">そのためには次を行います。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-386">To do so:</span></span>

-  <span data-ttu-id="ebb5f-387">プラグインフォルダー内の Newtonsoft ファイルを左クリックし、[ **インスペクター] パネル** を確認します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-387">Left-click on the Newtonsoft file inside the Plugins folder and look at the **Inspector panel**.</span></span> <span data-ttu-id="ebb5f-388">**プラットフォーム** があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-388">Make sure **Any Platform** is ticked.</span></span> <span data-ttu-id="ebb5f-389">[ **UWP] タブ** にアクセスし、[ **処理が行われない** ようにする] もオンにします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-389">Go to the **UWP tab** and also ensure **Don't process** is ticked.</span></span>

    ![Unity での Dll のインポート](images/AzureLabs-Lab7-48.png)

## <a name="chapter-8---create-the-shelfkeeper-class"></a><span data-ttu-id="ebb5f-391">章 8-ShelfKeeper クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="ebb5f-391">Chapter 8 - Create the ShelfKeeper class</span></span>

<span data-ttu-id="ebb5f-392">**ShelfKeeper** クラスは、シーンで生成された UI と製品を制御するメソッドをホストします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-392">The **ShelfKeeper** class hosts methods that control the UI and products spawned in the scene.</span></span>

<span data-ttu-id="ebb5f-393">インポートされたパッケージの一部として、このクラスは不完全ですが、指定されています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-393">As part of the imported package, you will have been given this class, though it is incomplete.</span></span> <span data-ttu-id="ebb5f-394">このクラスは、次のように完了します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-394">It is now time to complete that class:</span></span>

1.  <span data-ttu-id="ebb5f-395">**ShelfKeeper** スクリプトを **Scripts** フォルダー内でダブルクリックして、 **Visual Studio 2017** で開きます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-395">Double click on the **ShelfKeeper** script, within the **Scripts** folder, to open it with **Visual Studio 2017**.</span></span>

2.  <span data-ttu-id="ebb5f-396">スクリプト内の既存のすべてのコードを次のコードに置き換えます。このコードは、時刻と日付を設定し、製品を表示するメソッドを持っています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-396">Replace all the code existing in the script with the following code, which sets the time and date and has a method to show a product.</span></span>

    ```csharp
    using UnityEngine;

    public class ShelfKeeper : MonoBehaviour
    {
        /// <summary>
        /// Provides this class Singleton-like behavior
        /// </summary>
        public static ShelfKeeper instance;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for data
        /// </summary>
        public TextMesh dateText;

        /// <summary>
        /// Unity Inspector accessible Reference to the Text Mesh object needed for time
        /// </summary>
        public TextMesh timeText;

        /// <summary>
        /// Provides references to the spawn locations for the products prefabs
        /// </summary>
        public Transform[] spawnPoint;

        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Set the text of the date in the scene
        /// </summary>
        public void SetDate(string day, string month)
        {
            dateText.text = day + " " + month;
        }

        /// <summary>
        /// Set the text of the time in the scene
        /// </summary>
        public void SetTime(string hour)
        {
            timeText.text = hour + ":00";
        }

        /// <summary>
        /// Spawn a product on the shelf by providing the name and selling grade
        /// </summary>
        /// <param name="name"></param>
        /// <param name="sellingGrade">0 being the best seller</param>
        public void SpawnProduct(string name, int sellingGrade)
        {
            Instantiate(Resources.Load(name),
                spawnPoint[sellingGrade].transform.position, spawnPoint[sellingGrade].transform.rotation);
        }
    }
    ```

3.  <span data-ttu-id="ebb5f-397">**Unity** に戻る前に、変更内容を **Visual Studio** に保存してください。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-397">Be sure to save your changes in **Visual Studio** before returning to **Unity**.</span></span>

4.  <span data-ttu-id="ebb5f-398">Unity エディターに戻り、 **ShelfKeeper** クラスが次のようになっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-398">Back in the Unity Editor, check that the **ShelfKeeper** class looks like the below:</span></span>

    ![ShelfKeeper クラスを作成する](images/AzureLabs-Lab7-51.png)

    > [!IMPORTANT]
    > <span data-ttu-id="ebb5f-400">スクリプトに参照ターゲット (つまり *Date (テキストメッシュ)*) がない場合は、対応するオブジェクトを **階層パネル** からターゲットフィールドにドラッグするだけです。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-400">If your script does not have the reference targets (i.e. *Date (Text Mesh)*), simply drag the corresponding objects from the **Hierarchy Panel**, into the target fields.</span></span> <span data-ttu-id="ebb5f-401">必要に応じて、以下の説明を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-401">See below for explanation, if needed:</span></span>
    > 
    > 1.  <span data-ttu-id="ebb5f-402">**ShelfKeeper** コンポーネントスクリプト内の **生成ポイント** の配列を、左クリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-402">Open the **Spawn Point** array within the **ShelfKeeper** component script by left-clicking it.</span></span> <span data-ttu-id="ebb5f-403">サブセクションは、配列のサイズを示す **size** という名前で表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-403">A sub-section will appear called **Size**, which indicates the size of the array.</span></span> <span data-ttu-id="ebb5f-404">[**サイズ**] の横にあるテキストボックスに「 **3** 」と入力し、 **enter** キーを押すと、3つのスロットが下に作成されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-404">Type **3** into the textbox next to **Size** and press **Enter**, and three slots will be created beneath.</span></span>
    > 2. <span data-ttu-id="ebb5f-405">**階層** 内で、**時間表示** オブジェクトを展開します (横にある矢印を左クリックします)。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-405">Within the **Hierarchy** expand the **Time Display** object (by left-clicking the arrow beside it).</span></span> <span data-ttu-id="ebb5f-406">次に、 ***_ 階層内から\*_メインカメラ_ _** をクリックして、\*\*インスペクター*\* にその情報が表示されるようにします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-406">Next click the \**_Main Camera_*_ from within the _\* Hierarchy\*\*, so that the **Inspector** shows its information.</span></span>
    > 3. <span data-ttu-id="ebb5f-407">[**階層] パネル** で **メインカメラ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-407">Select the **Main Camera** in the **Hierarchy Panel**.</span></span> <span data-ttu-id="ebb5f-408">[**階層] パネル** の **日付** と **時刻** のオブジェクトを、 **ShelfKeeper** コンポーネントの **メインカメラ** の **インスペクター** 内の [ **date text** ] および [ **time] テキスト** スロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-408">Drag the **Date** and **Time** objects from the **Hierarchy Panel** to the **Date Text** and **Time Text** slots within the **Inspector** of the **Main Camera** in the **ShelfKeeper** component.</span></span>
    > 4. <span data-ttu-id="ebb5f-409">イメージに示されているように、[**階層] パネル**(*棚* オブジェクトの下) から、**生成ポイント** の配列の下にある **3** **要素** 参照ターゲットに **生成ポイント** をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-409">Drag the **Spawn Points** from the **Hierarchy Panel** (beneath the *Shelf* object) to the **3** **Element** reference targets beneath the **Spawn Point** array, as shown in the image.</span></span>
    > 
    >     ![ShelfKeeper クラスを作成する](images/AzureLabs-Lab7-52.png)

## <a name="chapter-9---create-the-productprediction-class"></a><span data-ttu-id="ebb5f-411">第9章-ProductPrediction クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="ebb5f-411">Chapter 9 - Create the ProductPrediction class</span></span>

<span data-ttu-id="ebb5f-412">次に作成するクラスは、 **Productprediction** クラスです。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-412">The next class you are going to create is the **ProductPrediction** class.</span></span>

<span data-ttu-id="ebb5f-413">このクラスの役割は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-413">This class is responsible for:</span></span>

-   <span data-ttu-id="ebb5f-414">現在の日付と時刻を指定して、 **Machine Learning サービス** インスタンスを照会しています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-414">Querying the **Machine Learning Service** instance, providing the current date and time.</span></span>

-   <span data-ttu-id="ebb5f-415">JSON 応答を使用可能なデータに逆シリアル化しています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-415">Deserializing the JSON response into usable data.</span></span>

-   <span data-ttu-id="ebb5f-416">データを解釈し、3つの推奨される製品を取得します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-416">Interpreting the data, retrieving the 3 recommended products.</span></span>

-   <span data-ttu-id="ebb5f-417">**ShelfKeeper** クラスのメソッドを呼び出して、シーンにデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-417">Calling the **ShelfKeeper** class methods to display the data in the Scene.</span></span>

<span data-ttu-id="ebb5f-418">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="ebb5f-418">To create this class:</span></span>

1.  <span data-ttu-id="ebb5f-419">[**プロジェクト] パネル** の [**スクリプト**] フォルダーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-419">Go to the **Scripts** folder, in the **Project Panel**.</span></span>

2.  <span data-ttu-id="ebb5f-420">フォルダー内を右クリックし、[C# スクリプトの **作成**] をクリック  >  **C# Script** します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-420">Right-click inside the folder, **Create** > **C# Script**.</span></span> <span data-ttu-id="ebb5f-421">**Productprediction** のスクリプトを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-421">Call the script **ProductPrediction**.</span></span>

3.  <span data-ttu-id="ebb5f-422">新しい **Productprediction** スクリプトをダブルクリックして、 **Visual Studio 2017** で開きます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-422">Double click on the new **ProductPrediction** script to open it with **Visual Studio 2017**.</span></span>

4.  <span data-ttu-id="ebb5f-423">[ **ファイルの変更が検出されまし** た] ダイアログボックスが表示されたら、[ソリューションの *_再読み込み_*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-423">If the **File Modification Detected** dialog pops up, click \**_Reload Solution_*.</span></span>

5.  <span data-ttu-id="ebb5f-424">ProductPrediction クラスの先頭に次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-424">Add the following namespaces to the top of the ProductPrediction class:</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using UnityEngine;
    using System.Linq;
    using Newtonsoft.Json;
    using UnityEngine.Networking;
    using System.Runtime.Serialization;
    using System.Collections;
    ```

6.  <span data-ttu-id="ebb5f-425">**Productprediction** クラス内で、複数の入れ子になったクラスで構成される次の2つのオブジェクトを挿入します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-425">Inside the **ProductPrediction** class insert the following two objects which are composed of a number of nested classes.</span></span> <span data-ttu-id="ebb5f-426">これらのクラスは、Machine Learning サービスの JSON をシリアル化および逆シリアル化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-426">These classes are used to serialize and deserialize the JSON for the Machine Learning Service.</span></span>

    ```csharp
        /// <summary>
        /// This object represents the Prediction request
        /// It host the day of the year and hour of the day
        /// The product must be left blank when serialising
        /// </summary>
        public class RootObject
        {
            public Inputs Inputs { get; set; }
        }

        public class Inputs
        {
            public Input1 input1 { get; set; }
        }

        public class Input1
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

    ```csharp
        /// <summary>
        /// This object containing the deserialised Prediction result
        /// It host the list of the products
        /// and the likelihood of them being sold at current date and time
        /// </summary>
        public class Prediction
        {
            public Results Results { get; set; }
        }

        public class Results
        {
            public Output1 output1;
        }

        public class Output1
        {
            public string type;
            public Value value;
        }

        public class Value
        {
            public List<string> ColumnNames { get; set; }
            public List<List<string>> Values { get; set; }
        }
    ```

7.  <span data-ttu-id="ebb5f-427">次に、前のコードの上に次の変数を追加します (JSON 関連のコードは、スクリプトの一番下にあり、他のすべてのコードの下にあります)。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-427">Then add the following variables above the previous code (so that the JSON related code is at the bottom of the script, below all other code, and out of the way):</span></span>

    ```csharp
        /// <summary>
        /// The 'Primary Key' from your Machine Learning Portal
        /// </summary>
        private string authKey = "-- Insert your service authentication key here --";

        /// <summary>
        /// The 'Request-Response' Service Endpoint from your Machine Learning Portal
        /// </summary>
        private string serviceEndpoint = "-- Insert your service endpoint here --";

        /// <summary>
        /// The Hour as set in Windows
        /// </summary>
        private string thisHour;

        /// <summary>
        /// The Day, as set in Windows
        /// </summary>
        private string thisDay;

        /// <summary>
        /// The Month, as set in Windows
        /// </summary>
        private string thisMonth;

        /// <summary>
        /// The Numeric Day from current Date Conversion
        /// </summary>
        private string dayOfTheYear;

        /// <summary>
        /// Dictionary for holding the first (or default) provided prediction 
        /// from the Machine Learning Experiment
        /// </summary>    
        private Dictionary<string, string> predictionDictionary;

        /// <summary>
        /// List for holding product prediction with name and scores
        /// </summary>
        private List<KeyValuePair<string, double>> keyValueList;
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="ebb5f-428">Machine Learning ポータルから、 **主キー** と **要求-応答のエンドポイント** を、ここでの変数に挿入してください。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-428">Make sure to insert the **primary key** and **request-response endpoint**, from the Machine Learning Portal, into the variables here.</span></span> <span data-ttu-id="ebb5f-429">次の画像は、キーとエンドポイントを取得した場所を示しています。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-429">The below images show where you would have taken the key and endpoint from.</span></span> 
    >  
    > ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-53-1.png)
    >
    > ![Machine Learning Studio (クラシック): 実験](images/AzureLabs-Lab7-53-2.png)

8.  <span data-ttu-id="ebb5f-432">このコードを **Start ()** メソッド内に挿入します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-432">Insert this code within the **Start()** method.</span></span> <span data-ttu-id="ebb5f-433">**Start ()** メソッドは、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-433">The **Start()** method is called when the class initializes:</span></span>

    ```csharp
        void Start()
        {
            // Call to get the current date and time as set in Windows
            GetTodayDateAndTime();

            // Call to set the HOUR in the UI
            ShelfKeeper.instance.SetTime(thisHour);

            // Call to set the DATE in the UI
            ShelfKeeper.instance.SetDate(thisDay, thisMonth);

            // Run the method to Get Predication from Azure Machine Learning
            StartCoroutine(GetPrediction(thisHour, dayOfTheYear));
        }
    ```

9.  <span data-ttu-id="ebb5f-434">Windows から日付と時刻を収集し、Machine Learning 実験でテーブルに格納されているデータと比較するために使用できる形式に変換するメソッドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-434">The following is the method that collects the date and time from Windows and converts it into a format that our Machine Learning Experiment can use to compare with the data stored in the table.</span></span>

    ```csharp
        /// <summary>
        /// Get current date and hour
        /// </summary>
        private void GetTodayDateAndTime()
        {
            // Get today date and time
            DateTime todayDate = DateTime.Now;

            // Extrapolate the HOUR
            thisHour = todayDate.Hour.ToString();

            // Extrapolate the DATE
            thisDay = todayDate.Day.ToString();
            thisMonth = todayDate.ToString("MMM");

            // Extrapolate the day of the year
            dayOfTheYear = todayDate.DayOfYear.ToString();
        }
    ```

10. <span data-ttu-id="ebb5f-435">**Update ()** メソッドは、このクラスでは使用されないため、**削除** できます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-435">You can **delete** the **Update()** method since this class will not use it.</span></span>

11. <span data-ttu-id="ebb5f-436">次のメソッドを追加します。このメソッドは、現在の日付と時刻を Machine Learning エンドポイントに伝え、JSON 形式で応答を受信します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-436">Add the following method which will communicate the current date and time to the Machine Learning endpoint and receive a response in JSON format.</span></span>

    ```csharp
        private IEnumerator GetPrediction(string timeOfDay, string dayOfYear)
        {
            // Populate the request object 
            // Using current day of the year and hour of the day
            RootObject ro = new RootObject
            {
                Inputs = new Inputs
                {
                    input1 = new Input1
                    {
                        ColumnNames = new List<string>
                        {
                            "day",
                            "hour",
                        "product"
                        },
                        Values = new List<List<string>>()
                    }
                }
            };

            List<string> l = new List<string>
            {
                dayOfYear,
                timeOfDay,
                ""
            };

            ro.Inputs.input1.Values.Add(l);

            Debug.LogFormat("Score request built");

            // Serialize the request
            string json = JsonConvert.SerializeObject(ro);

            using (UnityWebRequest www = UnityWebRequest.Post(serviceEndpoint, "POST"))
            {
                byte[] jsonToSend = new System.Text.UTF8Encoding().GetBytes(json);
                www.uploadHandler = new UploadHandlerRaw(jsonToSend);

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + authKey);
                www.SetRequestHeader("Content-Type", "application/json");
                www.SetRequestHeader("Accept", "application/json");

                yield return www.SendWebRequest();
                string response = www.downloadHandler.text;

                // Deserialize the response
                DataContractSerializer serializer;
                serializer = new DataContractSerializer(typeof(string));
                DeserialiseJsonResponse(response);
            }
        }
    ```

12. <span data-ttu-id="ebb5f-437">次のメソッドを追加します。このメソッドは、JSON 応答を逆シリアル化し、逆シリアル化の結果を **ShelfKeeper** クラスに伝達します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-437">Add the following method, which is responsible for deserializing the JSON response, and communicating the result of the deserialization to the **ShelfKeeper** class.</span></span> <span data-ttu-id="ebb5f-438">この結果は、現在の日付と時刻を最も多く販売するために予測される3つの項目の名前になります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-438">This result will be the names of the three items predicted to sell the most at current date and time.</span></span> <span data-ttu-id="ebb5f-439">次のコードを **Productprediction** クラスの前のメソッドの下に挿入します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-439">Insert the code below into the **ProductPrediction** class, below the previous method.</span></span>

    ```csharp
        /// <summary>
        /// Deserialize the response received from the Machine Learning portal
        /// </summary>
        public void DeserialiseJsonResponse(string jsonResponse)
        {
            // Deserialize JSON
            Prediction prediction = JsonConvert.DeserializeObject<Prediction>(jsonResponse);
            predictionDictionary = new Dictionary<string, string>();

            for (int i = 0; i < prediction.Results.output1.value.ColumnNames.Count; i++)
            {
                if (prediction.Results.output1.value.Values[0][i] != null)
                {
                    predictionDictionary.Add(prediction.Results.output1.value.ColumnNames[i], prediction.Results.output1.value.Values[0][i]);
                }
            }

            keyValueList = new List<KeyValuePair<string, double>>();

            // Strip all non-results, by adding only items of interest to the scoreList
            for (int i = 0; i < predictionDictionary.Count; i++)
            {
                KeyValuePair<string, string> pair = predictionDictionary.ElementAt(i);
                if (pair.Key.StartsWith("Scored Probabilities"))
                {
                    // Parse string as double then simplify the string key so to only have the item name
                    double scorefloat = 0f;
                    double.TryParse(pair.Value, out scorefloat);
                    string simplifiedName =
                        pair.Key.Replace("\"", "").Replace("Scored Probabilities for Class", "").Trim();
                    keyValueList.Add(new KeyValuePair<string, double>(simplifiedName, scorefloat));
                }
            }

            // Sort Predictions (results will be lowest to highest)
            keyValueList.Sort((x, y) => y.Value.CompareTo(x.Value));

            // Spawn the top three items, from the keyValueList, which we have sorted
            for (int i = 0; i < 3; i++)
            {
                ShelfKeeper.instance.SpawnProduct(keyValueList[i].Key, i);
            }

            // Clear lists in case of reuse
            keyValueList.Clear();
            predictionDictionary.Clear();
        }
    ```

13. <span data-ttu-id="ebb5f-440">**Visual Studio** を保存し、 **Unity** に戻ります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-440">Save **Visual Studio** and head back to **Unity**.</span></span>

14. <span data-ttu-id="ebb5f-441">**Productprediction** クラススクリプトを **Script** フォルダーから **メインカメラ** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-441">Drag the **ProductPrediction** class script from the **Script** folder, onto the **Main Camera** object.</span></span>

15. <span data-ttu-id="ebb5f-442">シーンとプロジェクト **ファイル** の保存  >  **シーン/ファイル**  >  **保存プロジェクト** を保存します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-442">Save your scene and project **File** > **Save Scene/File** > **Save Project**.</span></span>

## <a name="chapter-10---build-the-uwp-solution"></a><span data-ttu-id="ebb5f-443">第10章-UWP ソリューションのビルド</span><span class="sxs-lookup"><span data-stu-id="ebb5f-443">Chapter 10 - Build the UWP Solution</span></span>

<span data-ttu-id="ebb5f-444">この時点で、プロジェクトを UWP ソリューションとしてビルドし、スタンドアロンアプリケーションとして実行できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-444">It is now time to build your project as a UWP solution, so that it can run as a standalone application.</span></span>

<span data-ttu-id="ebb5f-445">ビルドするには:</span><span class="sxs-lookup"><span data-stu-id="ebb5f-445">To Build:</span></span>

1.  <span data-ttu-id="ebb5f-446">[**ファイル**] [保存] [シーン] をクリックして、現在のシーンを保存  >  **Save Scenes** します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-446">Save the current scene by clicking on **File** > **Save Scenes**.</span></span>

2.  <span data-ttu-id="ebb5f-447">ファイルの **File**  >  **ビルド設定** に進む</span><span class="sxs-lookup"><span data-stu-id="ebb5f-447">Go to **File** > **Build Settings**</span></span>

3.  <span data-ttu-id="ebb5f-448">**Unity C# プロジェクト** と呼ばれるチェックボックスをオンにします (ビルドの完了後にクラスを編集できるため、これは重要です)。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-448">Check the box called **Unity C# Projects** (this is important because it will allow you to edit the classes after build is completed).</span></span>

4.  <span data-ttu-id="ebb5f-449">[開いている **シーンの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-449">Click on **Add Open Scenes**,</span></span>

5.  <span data-ttu-id="ebb5f-450">[**ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-450">Click **Build**.</span></span>

    ![UWP ソリューションを構築する](images/AzureLabs-Lab7-54.png)

6.  <span data-ttu-id="ebb5f-452">ソリューションをビルドするフォルダーを選択するように求められます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-452">You will be prompted to select the folder where you want to build the Solution.</span></span>

7.  <span data-ttu-id="ebb5f-453">**ビルド** フォルダーを作成し、そのフォルダー内で、適切な名前を指定して別のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-453">Create a **BUILDS** folder and within that folder create another folder with an appropriate name of your choice.</span></span>

8.  <span data-ttu-id="ebb5f-454">新しいフォルダーをクリックし、[ **フォルダーの選択**] をクリックして、その場所でビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-454">Click your new folder and then click **Select Folder**, to begin the build at that location.</span></span>

    ![UWP ソリューションを構築する](images/AzureLabs-Lab7-55.png)

    ![UWP ソリューションを構築する](images/AzureLabs-Lab7-56.png)

9.  <span data-ttu-id="ebb5f-457">Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で **ファイルエクスプローラー** ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-457">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11---deploy-your-application"></a><span data-ttu-id="ebb5f-458">第11章-アプリケーションのデプロイ</span><span class="sxs-lookup"><span data-stu-id="ebb5f-458">Chapter 11 - Deploy your Application</span></span>

<span data-ttu-id="ebb5f-459">アプリケーションをデプロイするには:</span><span class="sxs-lookup"><span data-stu-id="ebb5f-459">To deploy your application:</span></span>

1.  <span data-ttu-id="ebb5f-460">新しい Unity ビルド ( **アプリ** フォルダー) に移動し、 **Visual Studio** でソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-460">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

2.  <span data-ttu-id="ebb5f-461">Visual Studio を開いた状態で、NuGet パッケージを復元する必要があります。これを行うには、MachineLearningLab_Build ソリューションを右クリックし、(Visual Studio の右側にある) ソリューションエクスプローラーから [NuGet パッケージの復元] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-461">With Visual Studio open, you need to Restore NuGet Packages, which can be done through right-clicking your MachineLearningLab_Build solution, from the Solution Explorer (found to the right of Visual Studio), and then clicking Restore NuGet Packages:</span></span>

    ![NuGet パッケージの追加](images/AzureLabs-Lab7-57.png)

3.  <span data-ttu-id="ebb5f-463">ソリューション構成で、[ **デバッグ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-463">In the Solution Configuration select **Debug**.</span></span>

4.  <span data-ttu-id="ebb5f-464">ソリューションプラットフォームで、[ **x86**, **ローカルコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-464">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="ebb5f-465">Microsoft HoloLens の場合、これを *リモートコンピューター* に設定する方が簡単な場合があります。これにより、コンピューターにテザリングさされることはありません。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-465">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="ebb5f-466">ただし、次の手順も実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-466">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="ebb5f-467">HoloLens の **IP アドレス** を確認します。これは、 *[設定 > ネットワーク & インターネット > Wi-Fi > 詳細オプション]* にあります。IPv4 は、使用するアドレスです。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-467">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="ebb5f-468">**開発者モード** が **オンに** なっていることを確認します。*開発者向けのセキュリティ > の更新プログラム & の > の設定* にあります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-468">Ensure **Developer Mode** is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![NuGet パッケージの追加](images/AzureLabs-Lab7-58.png)

5.  <span data-ttu-id="ebb5f-470">[ **ビルド] メニュー** の [ **ソリューションの配置** ] をクリックして、アプリケーションを PC にサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-470">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>

6.  <span data-ttu-id="ebb5f-471">アプリがインストール済みのアプリの一覧に表示され、起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-471">Your App should now appear in the list of installed apps, ready to be launched.</span></span>

<span data-ttu-id="ebb5f-472">Mixed Reality アプリケーションを実行すると、Unity シーンで設定されたベンチが表示されます。また、初期化時に、Azure 内に設定したデータがフェッチされます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-472">When you run the Mixed Reality application, you will see the bench that was set up in your Unity scene, and from initialization, the data you set up within Azure will be fetched.</span></span> <span data-ttu-id="ebb5f-473">データはアプリケーション内で逆シリアル化され、現在の日付と時刻の上位3つの結果が、ベンチに3つのモデルとして視覚的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-473">The data will be deserialized within your application, and the three top results for your current date and time will be provided visually, as three models on the bench.</span></span>


## <a name="your-finished-machine-learning-application"></a><span data-ttu-id="ebb5f-474">完成した Machine Learning アプリケーション</span><span class="sxs-lookup"><span data-stu-id="ebb5f-474">Your finished Machine Learning application</span></span>
 
<span data-ttu-id="ebb5f-475">これで、Azure Machine Learning を活用してデータ予測を行い、シーンに表示する mixed reality アプリを構築しました。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-475">Congratulations, you built a mixed reality app that leverages the Azure Machine Learning to make data predictions and display it on your scene.</span></span>

![NuGet パッケージの追加](images/AzureLabs-Lab7-0.png)

## <a name="exercise"></a><span data-ttu-id="ebb5f-477">演習</span><span class="sxs-lookup"><span data-stu-id="ebb5f-477">Exercise</span></span>

<span data-ttu-id="ebb5f-478">**演習1**</span><span class="sxs-lookup"><span data-stu-id="ebb5f-478">**Exercise 1**</span></span>

<span data-ttu-id="ebb5f-479">アプリケーションの並べ替え順序を試して、3つの下位予測がシェルフに表示されるようにします。このデータも役に立つ可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-479">Experiment with the sort order of your application and have the three bottom predictions appear on the shelf, as this data would potentially be useful also.</span></span>

<span data-ttu-id="ebb5f-480">**演習2**</span><span class="sxs-lookup"><span data-stu-id="ebb5f-480">**Exercise 2**</span></span>

<span data-ttu-id="ebb5f-481">**Azure テーブル** を使用すると、新しいテーブルに気象情報が挿入され、データを使用して新しい実験が作成されます。</span><span class="sxs-lookup"><span data-stu-id="ebb5f-481">Using **Azure Tables** populate a new table with weather information and create a new experiment using the data.</span></span>
