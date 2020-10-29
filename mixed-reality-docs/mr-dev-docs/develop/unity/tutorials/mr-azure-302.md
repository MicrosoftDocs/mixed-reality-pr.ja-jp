---
title: MR と Azure 302-コンピュータービジョン
description: このコースでは、混合現実アプリケーションで Azure Computer Vision を使用して、提供されたイメージ内のビジュアルコンテンツを認識する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, コンピュータービジョン, hololens, イマーシブ, vr
ms.openlocfilehash: 4c8566a2654eb92a4dab2a933bd8afb0b745cfce
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91688303"
---
# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="c2358-104">MR と Azure 302:コンピューター ビジョン</span><span class="sxs-lookup"><span data-stu-id="c2358-104">MR and Azure 302: Computer vision</span></span>

<br>

>[!NOTE]
><span data-ttu-id="c2358-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="c2358-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c2358-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="c2358-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c2358-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。</span><span class="sxs-lookup"><span data-stu-id="c2358-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c2358-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c2358-109">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="c2358-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c2358-110">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

<span data-ttu-id="c2358-111">このコースでは、混合現実アプリケーションで Azure Computer Vision 機能を使用して、提供されたイメージ内のビジュアルコンテンツを認識する方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="c2358-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="c2358-112">認識結果は、説明的なタグとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="c2358-113">このサービスは、機械学習モデルをトレーニングすることなく使用できます。</span><span class="sxs-lookup"><span data-stu-id="c2358-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="c2358-114">実装に機械学習モデルのトレーニングが必要な場合は、「 [MR」と「Azure 302b](mr-azure-302b.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2358-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![ラボの結果](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="c2358-116">Microsoft Computer Vision は、開発者がクラウドから高度なアルゴリズムを使用して、イメージの処理と分析 (戻り情報を含む) を提供するように設計された Api のセットです。</span><span class="sxs-lookup"><span data-stu-id="c2358-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="c2358-117">開発者がイメージまたはイメージの URL をアップロードすると、Microsoft Computer Vision API アルゴリズムによって、ユーザーが選択した入力に基づいてビジュアルコンテンツが分析されます。これにより、画像の種類と品質の特定、人物顔の検出 (座標の取得)、タグ付け、画像の分類などを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c2358-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="c2358-118">詳細については、 [Azure Computer Vision API のページ](https://azure.microsoft.com/services/cognitive-services/computer-vision/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2358-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="c2358-119">このコースを完了すると、mixed reality HoloLens アプリケーションが完成します。これにより、次のことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="c2358-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="c2358-120">Tap ジェスチャを使用すると、HoloLens のカメラによってイメージがキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="c2358-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="c2358-121">イメージは、Azure Computer Vision API サービスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="c2358-122">認識されたオブジェクトは、Unity シーンに配置された単純な UI グループに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="c2358-123">アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。</span><span class="sxs-lookup"><span data-stu-id="c2358-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="c2358-124">このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="c2358-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="c2358-125">このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。</span><span class="sxs-lookup"><span data-stu-id="c2358-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="c2358-126">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="c2358-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c2358-127">コース</span><span class="sxs-lookup"><span data-stu-id="c2358-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c2358-128"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c2358-128"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c2358-129"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="c2358-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c2358-130">MR と Azure 302:コンピューター ビジョン</span><span class="sxs-lookup"><span data-stu-id="c2358-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="c2358-131">✔️</span><span class="sxs-lookup"><span data-stu-id="c2358-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c2358-132">✔️</span><span class="sxs-lookup"><span data-stu-id="c2358-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="c2358-133">このコースでは主に HoloLens に焦点を当てていますが、このコースで学習する内容を Windows Mixed Reality イマーシブ (VR) ヘッドセットにも適用できます。</span><span class="sxs-lookup"><span data-stu-id="c2358-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="c2358-134">イマーシブ (VR) ヘッドセットにはアクセス可能なカメラがないため、外部カメラが PC に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="c2358-135">コースを進めると、イマーシブ (VR) ヘッドセットをサポートするために必要な変更についての注意事項が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c2358-136">前提条件</span><span class="sxs-lookup"><span data-stu-id="c2358-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="c2358-137">このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="c2358-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="c2358-138">また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証されたものを表します (2018 年5月)。</span><span class="sxs-lookup"><span data-stu-id="c2358-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="c2358-139">「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものよりも新しいソフトウェアで見つかったものと完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="c2358-139">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="c2358-140">このコースでは、次のハードウェアとソフトウェアをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c2358-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="c2358-141">開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="c2358-142">開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="c2358-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c2358-143">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="c2358-143">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c2358-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="c2358-144">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="c2358-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c2358-145">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="c2358-146">[Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](../../../hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="c2358-146">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](../../../hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="c2358-147">PC に接続されているカメラ (イマーシブヘッドセット開発用)</span><span class="sxs-lookup"><span data-stu-id="c2358-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="c2358-148">Azure のセットアップと Computer Vision API の取得のためのインターネットアクセス</span><span class="sxs-lookup"><span data-stu-id="c2358-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c2358-149">開始する前に</span><span class="sxs-lookup"><span data-stu-id="c2358-149">Before you start</span></span>

1.  <span data-ttu-id="c2358-150">このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="c2358-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="c2358-151">HoloLens をセットアップしてテストします。</span><span class="sxs-lookup"><span data-stu-id="c2358-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="c2358-152">HoloLens のセットアップをサポートする必要がある場合は、 [hololens セットアップに関する記事にアクセスして](https://docs.microsoft.com/hololens/hololens-setup)ください。</span><span class="sxs-lookup"><span data-stu-id="c2358-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="c2358-153">新しい HoloLens アプリの開発を開始するときは、調整とセンサーのチューニングを実行することをお勧めします (ユーザーごとにこれらのタスクを実行するのに役立つ場合があります)。</span><span class="sxs-lookup"><span data-stu-id="c2358-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="c2358-154">調整の詳細については、 [「HoloLens の調整に関する記事へのリンク」を](../../../calibration.md#hololens-2)参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2358-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](../../../calibration.md#hololens-2).</span></span>

<span data-ttu-id="c2358-155">センサーチューニングの詳細については、 [HoloLens センサーチューニングに関する記事へのリンクを](../../../sensor-tuning.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2358-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](../../../sensor-tuning.md).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="c2358-156">章 1-Azure Portal</span><span class="sxs-lookup"><span data-stu-id="c2358-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="c2358-157">Azure で *Computer Vision API* サービスを使用するには、アプリケーションで使用できるようにサービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="c2358-158">まず、 [Azure Portal](https://portal.azure.com)にログインします。</span><span class="sxs-lookup"><span data-stu-id="c2358-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="c2358-159">まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="c2358-160">このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。</span><span class="sxs-lookup"><span data-stu-id="c2358-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="c2358-161">ログインしたら、左上隅にある [ **新規** ] をクリックし、 *Computer Vision API* を検索して、 **Enter キー** を押します。</span><span class="sxs-lookup"><span data-stu-id="c2358-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API* , and click **Enter** .</span></span>

    ![Azure での新しいリソースの作成](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="c2358-163">新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="c2358-163">The word **New** may have been replaced with **Create a resource** , in newer portals.</span></span>
 
3.  <span data-ttu-id="c2358-164">新しいページには、 *Computer Vision API* サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="c2358-165">このページの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="c2358-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![コンピュータービジョン api サービスについて](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="c2358-167">[ **作成** :</span><span class="sxs-lookup"><span data-stu-id="c2358-167">Once you have clicked on **Create** :</span></span>

    1. <span data-ttu-id="c2358-168">このサービスインスタンスに必要な **名前** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="c2358-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="c2358-169">**サブスクリプション** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c2358-169">Select a **Subscription** .</span></span>
    3. <span data-ttu-id="c2358-170">適切な **価格レベル** を選択します。これが *Computer Vision API* サービスを初めて作成する場合は、free レベル (F0) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c2358-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="c2358-171">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="c2358-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c2358-172">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="c2358-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c2358-173">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c2358-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="c2358-174">Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c2358-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="c2358-175">リソースグループの場所を決定します (新しいリソースグループを作成している場合)。</span><span class="sxs-lookup"><span data-stu-id="c2358-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="c2358-176">この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="c2358-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="c2358-177">一部の Azure 資産は、特定のリージョンでのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="c2358-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="c2358-178">また、このサービスに適用されている使用条件を理解していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="c2358-179">[作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-179">Click Create.</span></span>

        ![サービスの作成に関する情報](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="c2358-181">[ **作成** ] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="c2358-181">Once you have clicked on **Create** , you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="c2358-182">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![新しいサービスの新しい通知を確認する](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="c2358-184">通知をクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="c2358-184">Click on the notification to explore your new Service instance.</span></span> 

    ![[リソースへの移行] ボタンを選択します。](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="c2358-186">通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="c2358-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="c2358-187">新しい Computer Vision API サービスインスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![新しい Computer Vision API サービスイメージ](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="c2358-189">このチュートリアルでは、アプリケーションがサービスの呼び出しを行う必要があります。サービスは、サービスのサブスクリプションキーを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="c2358-190">*Computer Vision API* サービスの [ *クイックスタート* ] ページで、最初の手順に移動し、 *キーを取得* して、[ **キー** ] をクリックします (これを行うには、[サービス] ナビゲーションメニューにある青いハイパーリンクキーをクリックします。これは、キーアイコンで示されます)。</span><span class="sxs-lookup"><span data-stu-id="c2358-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys* , and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="c2358-191">これにより、サービス *キー* が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-191">This will reveal your service *Keys* .</span></span>
11. <span data-ttu-id="c2358-192">表示されているキーの1つをコピーします。これは、プロジェクトの後半で必要になります。</span><span class="sxs-lookup"><span data-stu-id="c2358-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="c2358-193">[ *クイックスタート* ] ページに戻り、そこからエンドポイントを取得します。</span><span class="sxs-lookup"><span data-stu-id="c2358-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="c2358-194">お客様の地域によっては異なる場合があることに注意してください (その場合は、後でコードを変更する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="c2358-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="c2358-195">後で使用するために、このエンドポイントのコピーを取得します。</span><span class="sxs-lookup"><span data-stu-id="c2358-195">Take a copy of this endpoint for use later:</span></span>

    ![新しい Computer Vision API サービス](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="c2358-197">[ここで](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)は、さまざまなエンドポイントを確認できます。</span><span class="sxs-lookup"><span data-stu-id="c2358-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="c2358-198">第2章: Unity プロジェクトを設定する</span><span class="sxs-lookup"><span data-stu-id="c2358-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="c2358-199">次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="c2358-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="c2358-200">*Unity* を開き、[ **新規** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-200">Open *Unity* and click **New** .</span></span> 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="c2358-202">ここで、Unity プロジェクト名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="c2358-203">**MR_ComputerVision** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="c2358-203">Insert **MR_ComputerVision** .</span></span> <span data-ttu-id="c2358-204">プロジェクトの種類が **3d** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c2358-204">Make sure the project type is set to **3D** .</span></span> <span data-ttu-id="c2358-205">場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="c2358-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="c2358-206">次に、[ **プロジェクトの作成** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-206">Then, click **Create project** .</span></span>

    ![新しい Unity プロジェクトの詳細を指定します。](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="c2358-208">Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio** .</span></span> <span data-ttu-id="c2358-209">[ **> の設定の編集** ] に移動し、新しいウィンドウで [ **外部ツール** ] に移動します。</span><span class="sxs-lookup"><span data-stu-id="c2358-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools** .</span></span> <span data-ttu-id="c2358-210">**外部スクリプトエディター** を **Visual Studio 2017** に変更します。</span><span class="sxs-lookup"><span data-stu-id="c2358-210">Change **External Script Editor** to **Visual Studio 2017** .</span></span> <span data-ttu-id="c2358-211">[ **基本設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c2358-211">Close the **Preferences** window.</span></span>

    ![スクリプトエディターの設定を更新します。](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="c2358-213">次に、[ **ファイル > ビルド設定** ] に移動し、[ **ユニバーサル Windows プラットフォーム** ] を選択します。次に、[ **プラットフォームの切り替え** ] ボタンをクリックして選択内容を適用します。</span><span class="sxs-lookup"><span data-stu-id="c2358-213">Next, go to **File > Build Settings** and select **Universal Windows Platform** , then click on the **Switch Platform** button to apply your selection.</span></span>

    ![[ビルドの設定] ウィンドウで、[プラットフォーム] を [UWP] に切り替えます。](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="c2358-215">それでも **ファイル > ビルド設定** を行い、次のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c2358-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="c2358-216">**ターゲットデバイス** が **HoloLens** に設定されています</span><span class="sxs-lookup"><span data-stu-id="c2358-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="c2358-217">イマーシブヘッドセットの場合は、 **ターゲットデバイス** を *任意のデバイス* に設定します。</span><span class="sxs-lookup"><span data-stu-id="c2358-217">For the immersive headsets, set **Target Device** to *Any Device* .</span></span>

    2. <span data-ttu-id="c2358-218">**ビルドの種類** が **D3D** に設定されています</span><span class="sxs-lookup"><span data-stu-id="c2358-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="c2358-219">**SDK** は最新の **インストール** に設定されています</span><span class="sxs-lookup"><span data-stu-id="c2358-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="c2358-220">**Visual Studio のバージョン** が、 **インストールされている最新** バージョンに設定されています</span><span class="sxs-lookup"><span data-stu-id="c2358-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="c2358-221">**ビルドと実行** は **ローカルコンピューター** に設定されています</span><span class="sxs-lookup"><span data-stu-id="c2358-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="c2358-222">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="c2358-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="c2358-223">これを行うには、[開いている **シーンの追加** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c2358-223">Do this by selecting **Add Open Scenes** .</span></span> <span data-ttu-id="c2358-224">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-224">A save window will appear.</span></span>
        
            ![[開いているシーンを追加] ボタンをクリックする](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="c2358-226">この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン** 」にします。</span><span class="sxs-lookup"><span data-stu-id="c2358-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes** .</span></span>

            ![新しいスクリプトフォルダーの作成](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="c2358-228">新しく作成した [ **シーン** ] フォルダーを開き、[ *ファイル名* : テキスト] フィールドに「 **MR_ComputerVisionScene** 」と入力し、[ **保存** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-228">Open your newly created **Scenes** folder, and then in the *File name* : text field, type **MR_ComputerVisionScene** , then click **Save** .</span></span>

            ![新しいシーンに名前を付けます。](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="c2358-230">Unity プロジェクトに関連付けられている必要があるため、Unity のシーンを *Assets* フォルダー内に保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="c2358-231">Unity プロジェクトを構成する一般的な方法は、シーンフォルダー (およびその他の同様のフォルダー) を作成することです。</span><span class="sxs-lookup"><span data-stu-id="c2358-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="c2358-232">それ以外の設定は、[ *ビルド設定* ] の [既定] のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="c2358-232">The remaining settings, in *Build Settings* , should be left as default for now.</span></span>

6. <span data-ttu-id="c2358-233">[ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="c2358-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![プレーヤーの設定を開きます。](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="c2358-235">このパネルでは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="c2358-236">[ **その他の設定** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="c2358-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="c2358-237">**スクリプトランタイムのバージョン** は **安定** している必要があります (.net 3.5 と同等)。</span><span class="sxs-lookup"><span data-stu-id="c2358-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="c2358-238">**バックエンド** は **.net** である必要があります</span><span class="sxs-lookup"><span data-stu-id="c2358-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="c2358-239">**API 互換性レベル** は **.net 4.6** である必要があります</span><span class="sxs-lookup"><span data-stu-id="c2358-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![その他の設定を更新します。](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="c2358-241">[ **発行の設定** ] タブの [ **機能** ] で、次の項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="c2358-241">Within the **Publishing Settings** tab, under **Capabilities** , check:</span></span>

        1. <span data-ttu-id="c2358-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="c2358-242">**InternetClient**</span></span>
        2. <span data-ttu-id="c2358-243">**Web カメラ**</span><span class="sxs-lookup"><span data-stu-id="c2358-243">**Webcam**</span></span>

            ![発行設定を更新しています。](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="c2358-245">パネルの下にある [ **XR settings** (発行の **設定** ] の下にあります) で、[ **サポートされている仮想現実** ] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c2358-245">Further down the panel, in **XR Settings** (found below **Publish Settings** ), tick **Virtual Reality Supported** , make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![X R の設定を更新します。](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="c2358-247">*ビルド設定* に戻る _Unity C#_ プロジェクトはグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="c2358-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="c2358-248">[ビルド設定] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c2358-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="c2358-249">シーンとプロジェクトを保存します ([ **ファイル] > [シーン/ファイルの保存] > [プロジェクトの保存** ])。</span><span class="sxs-lookup"><span data-stu-id="c2358-249">Save your Scene and Project ( **FILE > SAVE SCENE / FILE > SAVE PROJECT** ).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="c2358-250">第3章–メインカメラの設定</span><span class="sxs-lookup"><span data-stu-id="c2358-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c2358-251">このコースの *Unity セットアップ* コンポーネントをスキップしてコードに直接進む場合は、 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage)をダウンロードし、 [カスタムパッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 [第5章](#chapter-5--create-the-resultslabel-class)から続行してください。</span><span class="sxs-lookup"><span data-stu-id="c2358-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="c2358-252">[ *階層] パネル* で、 **メインカメラ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c2358-252">In the *Hierarchy Panel* , select the **Main Camera** .</span></span> 
2.  <span data-ttu-id="c2358-253">選択すると、 **メインカメラ** のすべてのコンポーネントが [ *インスペクター] パネル* に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel* .</span></span>

    1. <span data-ttu-id="c2358-254">**カメラオブジェクト** は **メインカメラ** という名前にする必要があります (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="c2358-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="c2358-255">メインカメラの **タグ** は、 **maincamera** に設定する必要があります (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="c2358-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="c2358-256">**変換位置** が **0、0、0** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c2358-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="c2358-257">**クリアフラグ** を **純色** に設定します (イマーシブヘッドセットの場合は無視します)。</span><span class="sxs-lookup"><span data-stu-id="c2358-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="c2358-258">カメラコンポーネントの **背景** 色を **黒、アルファ 0 (16 進コード: #00000000)** に設定します (イマーシブヘッドセットの場合は無視します)。</span><span class="sxs-lookup"><span data-stu-id="c2358-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![カメラコンポーネントを更新します。](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="c2358-260">次に、 **メインカメラ** に接続された単純な "Cursor" オブジェクトを作成する必要があります。これは、アプリケーションの実行時にイメージ分析出力を配置するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c2358-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera** , which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="c2358-261">このカーソルによって、カメラフォーカスの中心点が決まります。</span><span class="sxs-lookup"><span data-stu-id="c2358-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="c2358-262">カーソルを作成するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="c2358-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="c2358-263">[ *階層] パネル* で、 **メインカメラ** を右クリックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-263">In the *Hierarchy Panel* , right-click on the **Main Camera** .</span></span> <span data-ttu-id="c2358-264">[ **3D オブジェクト** ] で、[ **球** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-264">Under **3D Object** , click on **Sphere** .</span></span>

    ![Cursor オブジェクトを選択します。](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="c2358-266">**球** の名前を **カーソル** に変更します (カーソルオブジェクトをダブルクリックするか、オブジェクトが選択された状態で F2 キーを押します)。 **メインカメラ** の子として配置されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c2358-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera** .</span></span>

3.  <span data-ttu-id="c2358-267">[ *階層] パネル* で、 **カーソル** を左クリックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-267">In the *Hierarchy Panel* , left click on the **Cursor** .</span></span> <span data-ttu-id="c2358-268">カーソルを選択した状態で、[ *インスペクター] パネル* で次の変数を調整します。</span><span class="sxs-lookup"><span data-stu-id="c2358-268">With the Cursor selected, adjust the following variables in the *Inspector Panel* :</span></span>

    1. <span data-ttu-id="c2358-269">*変換位置* を **0、0、5** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c2358-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="c2358-270">*スケール* を **0.02、0.02、0.02** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c2358-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![変換位置とスケールを更新します。](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="c2358-272">Chapter 4 –ラベルシステムのセットアップ</span><span class="sxs-lookup"><span data-stu-id="c2358-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="c2358-273">HoloLens のカメラを使用してイメージをキャプチャすると、そのイメージが分析のために *Azure Computer Vision API* サービスインスタンスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="c2358-274">この分析の結果は、 **タグ** と呼ばれる認識されたオブジェクトの一覧になります。</span><span class="sxs-lookup"><span data-stu-id="c2358-274">The results of that analysis will be a list of recognized objects called **Tags** .</span></span> 

<span data-ttu-id="c2358-275">これらのタグは、写真が撮影された場所に表示されるように、(ワールド空間の3D テキストとして) 使用します。</span><span class="sxs-lookup"><span data-stu-id="c2358-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="c2358-276">次の手順では、 **Label** オブジェクトを設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c2358-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="c2358-277">[階層] パネル内の任意の場所を右クリックし (この時点では場所は関係ありません)、[ **3D オブジェクト** ] の下に **3d テキスト** を追加します。</span><span class="sxs-lookup"><span data-stu-id="c2358-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object** , add a **3D Text** .</span></span> <span data-ttu-id="c2358-278">**Labeltext** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2358-278">Name it **LabelText** .</span></span>

    ![3D テキストオブジェクトを作成します。](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="c2358-280">[ *階層] パネル* で、 **labeltext** を左クリックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-280">In the *Hierarchy Panel* , left click on the **LabelText** .</span></span> <span data-ttu-id="c2358-281">**Labeltext** を選択した状態で、[ *インスペクター] パネル* で次の変数を調整します。</span><span class="sxs-lookup"><span data-stu-id="c2358-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel* :</span></span>

    1. <span data-ttu-id="c2358-282">**位置** を **0、0、0** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c2358-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="c2358-283">**スケール** を **0.01、0.01、0.01** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c2358-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="c2358-284">コンポーネント **テキストメッシュ** で、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="c2358-284">In the component **Text Mesh** :</span></span>
    4. <span data-ttu-id="c2358-285">**テキスト** 内のすべてのテキストを "..." で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c2358-285">Replace all the text within **Text** , with "..."</span></span>        
    5. <span data-ttu-id="c2358-286">**アンカー** を **中央** 中央に設定する</span><span class="sxs-lookup"><span data-stu-id="c2358-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="c2358-287">**配置** を **中央** に設定する</span><span class="sxs-lookup"><span data-stu-id="c2358-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="c2358-288">**タブサイズ** を **4** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c2358-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="c2358-289">**フォントサイズ** を **50** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c2358-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="c2358-290">**色** を **#FFFFFFFF** に設定します</span><span class="sxs-lookup"><span data-stu-id="c2358-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![テキストコンポーネント](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="c2358-292">[ *プロジェクト] パネル* の内の [ *階層] パネル* から [ *アセット] フォルダー* に **labeltext** をドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c2358-292">Drag the **LabelText** from the *Hierarchy Panel* , into the *Asset Folder* , within in the *Project Panel* .</span></span> <span data-ttu-id="c2358-293">これにより、コードでインスタンス化できるように **Labeltext** が事前 fab になります。</span><span class="sxs-lookup"><span data-stu-id="c2358-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![LabelText オブジェクトの事前 fab を作成します。](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="c2358-295">[ *階層] パネル* から **labeltext** を削除して、開いているシーンには表示されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-295">You should delete the **LabelText** from the *Hierarchy Panel* , so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="c2358-296">現在は、Assets フォルダーから個々のインスタンスに対して呼び出す prefab であるため、シーン内に保持する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c2358-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="c2358-297">*階層パネル* の最終的なオブジェクト構造は、次の図に示すようになります。</span><span class="sxs-lookup"><span data-stu-id="c2358-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![階層パネルの最終構造。](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="c2358-299">第5章–生成されるのは、そのためのラベルクラス</span><span class="sxs-lookup"><span data-stu-id="c2358-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="c2358-300">作成する必要のある最初のスクリプトは、次の処理を行うための、次のような、べき条件の *ラベル* クラスです。</span><span class="sxs-lookup"><span data-stu-id="c2358-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="c2358-301">カメラの位置を基準にして、適切なワールド空間にラベルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c2358-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="c2358-302">イメージ Anaysis のタグを表示します。</span><span class="sxs-lookup"><span data-stu-id="c2358-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="c2358-303">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="c2358-303">To create this class:</span></span> 

1.  <span data-ttu-id="c2358-304">[ *プロジェクト] パネル* 内を右クリックし、[ **> フォルダーの作成** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-304">Right-click in the *Project Panel* , then **Create > Folder** .</span></span> <span data-ttu-id="c2358-305">フォルダーに **スクリプト** の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2358-305">Name the folder **Scripts** .</span></span> 

    ![Scripts フォルダーを作成します。](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="c2358-307">**Scripts** フォルダー create を使用して、ダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="c2358-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="c2358-308">次に、そのフォルダー内でを右クリックし、[ **Create >** Then **C# Script** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c2358-308">Then within that folder, right-click, and select **Create >** then **C# Script** .</span></span> <span data-ttu-id="c2358-309">スクリプトのラベルに「」という名前を *付け* ます。</span><span class="sxs-lookup"><span data-stu-id="c2358-309">Name the script *ResultsLabel* .</span></span> 

3.  <span data-ttu-id="c2358-310">新しいスクリプト *ラベル* スクリプトをダブルクリックして、 **Visual Studio** で開きます。</span><span class="sxs-lookup"><span data-stu-id="c2358-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio** .</span></span>

4.  <span data-ttu-id="c2358-311">クラス内で、次のコードを入力 *します* 。</span><span class="sxs-lookup"><span data-stu-id="c2358-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  <span data-ttu-id="c2358-312">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="c2358-312">Be sure to save your changes in *Visual Studio* before returning to *Unity* .</span></span>
7.  <span data-ttu-id="c2358-313">*Unity エディター* に戻り、[ **スクリプト** ] フォルダーの [の履歴] クラスをクリックし *て、[* *階層] パネル* の [ **メインカメラ** ] オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c2358-313">Back in the *Unity Editor* , click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel* .</span></span>
8.  <span data-ttu-id="c2358-314">**メインカメラ** をクリックし、[ *インスペクター] パネル* を確認します。</span><span class="sxs-lookup"><span data-stu-id="c2358-314">Click on the **Main Camera** and look at the *Inspector Panel* .</span></span>

<span data-ttu-id="c2358-315">カメラにドラッグしたスクリプトから、 **Cursor** と **Label prefab** の2つのフィールドがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="c2358-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab** .</span></span>

9.  <span data-ttu-id="c2358-316">次の図に示すように、[ *階層] パネル\*\*\*から [カーソル]*\* というオブジェクトを [ **カーソル** ] という名前のスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c2358-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor** , as shown in the image below.</span></span>
10. <span data-ttu-id="c2358-317">次の図に示すように、[ *プロジェクト] パネル* の [ *アセット] フォルダー* から **labeltext** という名前のオブジェクトを **label prefab** という名前のスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c2358-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab** , as shown in the image below.</span></span> 

    ![Unity 内で参照ターゲットを設定します。](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="c2358-319">Chapter 6 – ImageCapture クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="c2358-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="c2358-320">次に作成するクラスは、 *Imagecapture* クラスです。</span><span class="sxs-lookup"><span data-stu-id="c2358-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="c2358-321">このクラスの役割は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c2358-321">This class is responsible for:</span></span>

-   <span data-ttu-id="c2358-322">HoloLens カメラを使用してイメージをキャプチャし、アプリフォルダーに格納します。</span><span class="sxs-lookup"><span data-stu-id="c2358-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="c2358-323">ユーザーからタップジェスチャをキャプチャしています。</span><span class="sxs-lookup"><span data-stu-id="c2358-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="c2358-324">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="c2358-324">To create this class:</span></span> 

1.  <span data-ttu-id="c2358-325">前に作成した **Scripts** フォルダーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="c2358-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="c2358-326">フォルダー内を右クリックし、[ **Create > C# Script** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-326">Right-click inside the folder, **Create > C# Script** .</span></span> <span data-ttu-id="c2358-327">スクリプト *Imagecapture* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c2358-327">Call the script *ImageCapture* .</span></span> 
3.  <span data-ttu-id="c2358-328">新しい *Imagecapture* スクリプトをダブルクリックして、 **Visual Studio** で開きます。</span><span class="sxs-lookup"><span data-stu-id="c2358-328">Double click on the new *ImageCapture* script to open it with **Visual Studio** .</span></span>
4.  <span data-ttu-id="c2358-329">ファイルの先頭に次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="c2358-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="c2358-330">次に、 *Start ()* メソッドの上に、 *imagecapture* クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="c2358-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="c2358-331">**TapsCount** 変数には、ユーザーからキャプチャしたタップジェスチャの数が格納されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="c2358-332">この数値は、キャプチャしたイメージの名前付けに使用されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="c2358-333">起動可能な *()* メソッドと *Start ()* メソッドのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="c2358-334">これらは、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="c2358-335">Tap ジェスチャが発生したときに呼び出されるハンドラーを実装します。</span><span class="sxs-lookup"><span data-stu-id="c2358-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
<span data-ttu-id="c2358-336">*TapHandler ()* メソッドは、ユーザーからキャプチャされたタップの数を増やし、現在のカーソル位置を使用して、新しいラベルを配置する場所を決定します。</span><span class="sxs-lookup"><span data-stu-id="c2358-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="c2358-337">次に、このメソッドは、 *Executeimagecapを Andanalysis ()* メソッドを呼び出して、このアプリケーションのコア機能を開始します。</span><span class="sxs-lookup"><span data-stu-id="c2358-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="c2358-338">イメージをキャプチャして保存すると、次のハンドラーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="c2358-339">プロセスが成功した場合、結果は分析のために (まだ作成していない) *VisionManager* に渡されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  <span data-ttu-id="c2358-340">次に、アプリケーションがイメージキャプチャプロセスを開始するために使用するメソッドを追加し、イメージを格納します。</span><span class="sxs-lookup"><span data-stu-id="c2358-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> <span data-ttu-id="c2358-341">この時点で、 *Unity エディターのコンソールパネル* にエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2358-341">At this point you will notice an error appearing in the *Unity Editor Console Panel* .</span></span> <span data-ttu-id="c2358-342">これは、次の章で作成する *VisionManager* クラスをコードが参照するためです。</span><span class="sxs-lookup"><span data-stu-id="c2358-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="c2358-343">第7章-Azure への呼び出しとイメージ分析</span><span class="sxs-lookup"><span data-stu-id="c2358-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="c2358-344">作成する必要がある最後のスクリプトは、 *VisionManager* クラスです。</span><span class="sxs-lookup"><span data-stu-id="c2358-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="c2358-345">このクラスの役割は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="c2358-345">This class is responsible for:</span></span>

-   <span data-ttu-id="c2358-346">バイト配列としてキャプチャされた最新のイメージを読み込んでいます。</span><span class="sxs-lookup"><span data-stu-id="c2358-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="c2358-347">分析のために、バイト配列を *Azure Computer Vision API* サービスインスタンスに送信しています。</span><span class="sxs-lookup"><span data-stu-id="c2358-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="c2358-348">JSON 文字列として応答を受信しています。</span><span class="sxs-lookup"><span data-stu-id="c2358-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="c2358-349">応答を逆シリアル化 *し、結果* として得られるタグを結果のタグに渡します。</span><span class="sxs-lookup"><span data-stu-id="c2358-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="c2358-350">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="c2358-350">To create this class:</span></span>

1.  <span data-ttu-id="c2358-351">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="c2358-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="c2358-352">**Scripts** フォルダー内を右クリックし、[ **Create > C# Script** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-352">Right-click inside the **Scripts** folder, click **Create > C# Script** .</span></span> <span data-ttu-id="c2358-353">スクリプトに *VisionManager* という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2358-353">Name the script *VisionManager* .</span></span> 
3.  <span data-ttu-id="c2358-354">新しいスクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="c2358-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="c2358-355">*VisionManager* クラスの先頭にある次の名前空間を更新します。</span><span class="sxs-lookup"><span data-stu-id="c2358-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="c2358-356">スクリプトの先頭にある *VisionManager* クラス *内* ( *Start ()* メソッドの上) で、Azure からの逆シリアル化された JSON 応答を表す2つの *クラス* を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="c2358-357">*Tagdata* クラスと Analytics *sedobject* クラスでは、Unity ライブラリを使用して逆シリアル化できるようにする前に、 *[system.string]* 属性を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="c2358-358">VisionManager クラスでは、次の変数を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-358">In the VisionManager class, you should add the following variables:</span></span>

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > <span data-ttu-id="c2358-359">**認証キー** が **authorizationkey** 変数に挿入されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c2358-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="c2358-360">**認証キー** については、このコースの [第1章](#chapter-1--the-azure-portal)で説明しました。</span><span class="sxs-lookup"><span data-stu-id="c2358-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="c2358-361">**VisionAnalysisEndpoint** 変数は、この例で指定したものとは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="c2358-362">**米国西部** は、米国西部リージョン用に作成されたサービスインスタンスを厳密に参照します。</span><span class="sxs-lookup"><span data-stu-id="c2358-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="c2358-363">これを [エンドポイント URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)で更新します。次に例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="c2358-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="c2358-364">西ヨーロッパ: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="c2358-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="c2358-365">東南アジア: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="c2358-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="c2358-366">オーストラリア東部: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="c2358-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="c2358-367">起動するためのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="c2358-368">次に、コルーチン (その下に静的ストリームメソッドを含む) を追加します。これにより、 *Imagecapture* クラスによってキャプチャされたイメージの分析結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="c2358-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  <span data-ttu-id="c2358-369">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="c2358-369">Be sure to save your changes in *Visual Studio* before returning to *Unity* .</span></span>
10. <span data-ttu-id="c2358-370">Unity エディターに戻り、[ **スクリプト** ] フォルダーの *VisionManager* および *imagecapture* クラスをクリックして、[ *階層] パネル* の [ **メインカメラ** ] オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c2358-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel* .</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="c2358-371">章 8-ビルド前</span><span class="sxs-lookup"><span data-stu-id="c2358-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="c2358-372">アプリケーションの徹底的なテストを実行するには、アプリケーションを HoloLens にサイドロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="c2358-373">これを行う前に、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c2358-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="c2358-374">[第2章](#chapter-2--set-up-the-unity-project)で説明したすべての設定が正しく設定されています。</span><span class="sxs-lookup"><span data-stu-id="c2358-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="c2358-375">すべてのスクリプトが **メインカメラ** オブジェクトにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="c2358-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="c2358-376">*メインカメラインスペクターパネル* のすべてのフィールドが適切に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="c2358-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="c2358-377">**認証キー** が **authorizationkey** 変数に挿入されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c2358-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="c2358-378">*VisionManager* スクリプトでエンドポイントも確認し、地域に合わせて配置されていることを確認します (このドキュメントで *は、既定* で *米国西部* が使用されています)。</span><span class="sxs-lookup"><span data-stu-id="c2358-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="c2358-379">第9章– UWP ソリューションをビルドし、アプリケーションをサイドロードする</span><span class="sxs-lookup"><span data-stu-id="c2358-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="c2358-380">このプロジェクトの Unity セクションに必要なものはすべて完了したので、Unity から構築します。</span><span class="sxs-lookup"><span data-stu-id="c2358-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="c2358-381">*ビルド設定*  -  **ファイル > ビルド設定** に移動します...</span><span class="sxs-lookup"><span data-stu-id="c2358-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="c2358-382">[ *ビルドの設定* ] ウィンドウで、[ **ビルド** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-382">From the *Build Settings* window, click **Build** .</span></span>

    ![Unity からアプリをビルドする](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="c2358-384">**Unity C# プロジェクト** をまだティックしていない場合は、ティックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-384">If not already, tick **Unity C# Projects** .</span></span>
4.  <span data-ttu-id="c2358-385">[ **ビルド** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-385">Click **Build** .</span></span> <span data-ttu-id="c2358-386">Unity は *エクスプローラー* ウィンドウを起動します。このウィンドウでは、アプリを作成するフォルダーを作成して選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2358-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="c2358-387">ここでそのフォルダーを作成し、「 *App* 」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c2358-387">Create that folder now, and name it *App* .</span></span> <span data-ttu-id="c2358-388">次に、 *アプリ* フォルダーを選択し、 **[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2358-388">Then with the *App* folder selected, press **Select Folder** .</span></span> 
5.  <span data-ttu-id="c2358-389">Unity は、 *アプリ* フォルダーへのプロジェクトのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="c2358-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="c2358-390">Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で *ファイルエクスプローラー* ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。</span><span class="sxs-lookup"><span data-stu-id="c2358-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="c2358-391">第10章– HoloLens へのデプロイ</span><span class="sxs-lookup"><span data-stu-id="c2358-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="c2358-392">HoloLens に展開するには:</span><span class="sxs-lookup"><span data-stu-id="c2358-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="c2358-393">Hololens が **開発者モード** になっていることを確認するには、HOLOLENS の IP アドレス (リモートデプロイ用) が必要です。</span><span class="sxs-lookup"><span data-stu-id="c2358-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode** .</span></span> <span data-ttu-id="c2358-394">これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c2358-394">To do this:</span></span>

    1. <span data-ttu-id="c2358-395">HoloLens を装着した後、 **設定** を開きます。</span><span class="sxs-lookup"><span data-stu-id="c2358-395">Whilst wearing your HoloLens, open the **Settings** .</span></span>
    2. <span data-ttu-id="c2358-396">**[ネットワーク & インターネット > wi-fi > 詳細オプション]** にアクセス</span><span class="sxs-lookup"><span data-stu-id="c2358-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="c2358-397">**IPv4** アドレスをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="c2358-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="c2358-398">次に、[ **設定** ] に戻り、 **開発者向けの & セキュリティ > を更新** します。</span><span class="sxs-lookup"><span data-stu-id="c2358-398">Next, navigate back to **Settings** , and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="c2358-399">開発者モードをに設定します。</span><span class="sxs-lookup"><span data-stu-id="c2358-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="c2358-400">新しい Unity ビルド ( *アプリ* フォルダー) に移動し、 *Visual Studio* でソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="c2358-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio* .</span></span>
3.  <span data-ttu-id="c2358-401">ソリューション構成で、[ **デバッグ** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c2358-401">In the Solution Configuration select **Debug** .</span></span>
4.  <span data-ttu-id="c2358-402">ソリューションプラットフォームで、[ **x86** 、 **リモートコンピューター** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c2358-402">In the Solution Platform, select **x86** , **Remote Machine** .</span></span> 

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="c2358-404">[ **ビルド] メニュー** の [ソリューションの **配置** ] をクリックして、アプリケーションを HoloLens にサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="c2358-404">Go to the **Build menu** and click on **Deploy Solution** , to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="c2358-405">アプリが HoloLens にインストールされているアプリの一覧に表示され、起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="c2358-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="c2358-406">イマーシブヘッドセットにデプロイするには **、ソリューションプラットフォーム** を *ローカルコンピューター* に設定し、 **プラットフォーム** として *x86* を使用して、 **構成** を [ *デバッグ* ] に設定します。</span><span class="sxs-lookup"><span data-stu-id="c2358-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine* , and set the **Configuration** to *Debug* , with *x86* as the **Platform** .</span></span> <span data-ttu-id="c2358-407">次に、[ **ビルド] メニュー** の [ *ソリューションの配置* ] をクリックして、ローカルコンピューターに配置します。</span><span class="sxs-lookup"><span data-stu-id="c2358-407">Then deploy to the local machine, using the **Build menu** , selecting *Deploy Solution* .</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="c2358-408">完成した Computer Vision API アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c2358-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="c2358-409">これで、Azure Computer Vision API を利用して実際のオブジェクトを認識し、表示されている内容の信頼性を表示する、mixed reality アプリを構築しました。</span><span class="sxs-lookup"><span data-stu-id="c2358-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![ラボの結果](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="c2358-411">ボーナス演習</span><span class="sxs-lookup"><span data-stu-id="c2358-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="c2358-412">演習1</span><span class="sxs-lookup"><span data-stu-id="c2358-412">Exercise 1</span></span>

<span data-ttu-id="c2358-413">*Tags* パラメーターを使用したのと同じように ( *VisionManager* 内で使用される *エンドポイント* 内での説明に従って)、他の情報を検出するようにアプリを拡張します。他にアクセスできるパラメーターについては、 [こちら](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2358-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager* ), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="c2358-414">演習2</span><span class="sxs-lookup"><span data-stu-id="c2358-414">Exercise 2</span></span>

<span data-ttu-id="c2358-415">返された Azure データをより多くの会話で表示し、読みやすい方法で表示します (数値を非表示にするなど)。</span><span class="sxs-lookup"><span data-stu-id="c2358-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="c2358-416">Bot はユーザーと話し合っているかもしれません。</span><span class="sxs-lookup"><span data-stu-id="c2358-416">As though a bot might be speaking to the user.</span></span>
