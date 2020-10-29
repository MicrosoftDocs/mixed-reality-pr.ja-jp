---
title: MR と Azure 304-顔認識
description: このコースでは、mixed reality アプリケーション内で Azure 顔認識を実装する方法について学習します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, 顔認識, hololens, イマーシブ, vr
ms.openlocfilehash: 266f51a829d919f8b0f24e80589fd8ab21bb3694
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91687906"
---
# <a name="mr-and-azure-304-face-recognition"></a><span data-ttu-id="c497a-104">MR と Azure 304:顔認識</span><span class="sxs-lookup"><span data-stu-id="c497a-104">MR and Azure 304: Face recognition</span></span>

<br>

>[!NOTE]
><span data-ttu-id="c497a-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="c497a-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="c497a-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="c497a-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="c497a-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。</span><span class="sxs-lookup"><span data-stu-id="c497a-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="c497a-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="c497a-109">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="c497a-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="c497a-110">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

![このコースの完了の結果](images/AzureLabs-Lab4-00.png)

<span data-ttu-id="c497a-112">このコースでは、Microsoft Face API と共に Azure Cognitive Services を使用して、mixed reality アプリケーションに顔認識機能を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c497a-112">In this course you will learn how to add face recognition capabilities to a mixed reality application, using Azure Cognitive Services, with the Microsoft Face API.</span></span>

<span data-ttu-id="c497a-113">*Azure Face API* は Microsoft のサービスであり、開発者が最も高度な顔アルゴリズムをクラウドで利用できます。</span><span class="sxs-lookup"><span data-stu-id="c497a-113">*Azure Face API* is a Microsoft service, which provides developers with the most advanced face algorithms, all in the cloud.</span></span> <span data-ttu-id="c497a-114">*Face API* には、属性付きの顔検出と顔認識の2つの主な機能があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-114">The *Face API* has two main functions: face detection with attributes, and face recognition.</span></span> <span data-ttu-id="c497a-115">これにより、開発者は、顔のグループのセットを設定し、後でクエリイメージをサービスに送信して、顔が属するユーザーを特定することができます。</span><span class="sxs-lookup"><span data-stu-id="c497a-115">This allows developers to simply set a set of groups for faces, and then, send query images to the service later, to determine to whom a face belongs.</span></span> <span data-ttu-id="c497a-116">詳細については、 [Azure の顔認識](https://azure.microsoft.com/services/cognitive-services/face/)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c497a-116">For more information, visit the [Azure Face Recognition page](https://azure.microsoft.com/services/cognitive-services/face/).</span></span>

<span data-ttu-id="c497a-117">このコースを完了すると、mixed reality HoloLens アプリケーションが完成します。これにより、次のことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="c497a-117">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1. <span data-ttu-id="c497a-118">**タップジェスチャ** を使用して、ボード HoloLens カメラを使用してイメージのキャプチャを開始します。</span><span class="sxs-lookup"><span data-stu-id="c497a-118">Use a **Tap Gesture** to initiate the capture of an image using the on-board HoloLens camera.</span></span> 
2. <span data-ttu-id="c497a-119">キャプチャしたイメージを *Azure Face API* サービスに送信します。</span><span class="sxs-lookup"><span data-stu-id="c497a-119">Send the captured image to the *Azure Face API* service.</span></span>
3. <span data-ttu-id="c497a-120">*Face API* アルゴリズムの結果を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="c497a-120">Receive the results of the *Face API* algorithm.</span></span>
4. <span data-ttu-id="c497a-121">単純なユーザーインターフェイスを使用して、一致するユーザーの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="c497a-121">Use a simple User Interface, to display the name of matched people.</span></span>

<span data-ttu-id="c497a-122">ここでは、Face API サービスから Unity ベースの mixed reality アプリケーションに結果を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c497a-122">This will teach you how to get the results from the Face API Service into your Unity-based mixed reality application.</span></span>

<span data-ttu-id="c497a-123">アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。</span><span class="sxs-lookup"><span data-stu-id="c497a-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="c497a-124">このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="c497a-124">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="c497a-125">このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。</span><span class="sxs-lookup"><span data-stu-id="c497a-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="c497a-126">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="c497a-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="c497a-127">コース</span><span class="sxs-lookup"><span data-stu-id="c497a-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="c497a-128"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="c497a-128"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="c497a-129"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="c497a-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="c497a-130">MR と Azure 304:顔認識</span><span class="sxs-lookup"><span data-stu-id="c497a-130">MR and Azure 304: Face recognition</span></span></td><td style="text-align: center;"> <span data-ttu-id="c497a-131">✔️</span><span class="sxs-lookup"><span data-stu-id="c497a-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="c497a-132">✔️</span><span class="sxs-lookup"><span data-stu-id="c497a-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="c497a-133">このコースでは主に HoloLens に焦点を当てていますが、このコースで学習する内容を Windows Mixed Reality イマーシブ (VR) ヘッドセットにも適用できます。</span><span class="sxs-lookup"><span data-stu-id="c497a-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="c497a-134">イマーシブ (VR) ヘッドセットにはアクセス可能なカメラがないため、外部カメラが PC に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="c497a-135">コースを進めると、イマーシブ (VR) ヘッドセットをサポートするために必要な変更についての注意事項が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c497a-136">前提条件</span><span class="sxs-lookup"><span data-stu-id="c497a-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="c497a-137">このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="c497a-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="c497a-138">また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証されたものを表します (2018 年5月)。</span><span class="sxs-lookup"><span data-stu-id="c497a-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="c497a-139">「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものよりも新しいソフトウェアで見つかったものと完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="c497a-139">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="c497a-140">このコースでは、次のハードウェアとソフトウェアをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c497a-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="c497a-141">開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="c497a-142">開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="c497a-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md)
- [<span data-ttu-id="c497a-143">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="c497a-143">The latest Windows 10 SDK</span></span>](../../install-the-tools.md)
- [<span data-ttu-id="c497a-144">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="c497a-144">Unity 2017.4</span></span>](../../install-the-tools.md)
- [<span data-ttu-id="c497a-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c497a-145">Visual Studio 2017</span></span>](../../install-the-tools.md)
- <span data-ttu-id="c497a-146">[Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](../../../hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="c497a-146">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](../../../hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="c497a-147">PC に接続されているカメラ (イマーシブヘッドセット開発用)</span><span class="sxs-lookup"><span data-stu-id="c497a-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="c497a-148">Azure のセットアップと Face API の取得のためのインターネットアクセス</span><span class="sxs-lookup"><span data-stu-id="c497a-148">Internet access for Azure setup and Face API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c497a-149">開始する前に</span><span class="sxs-lookup"><span data-stu-id="c497a-149">Before you start</span></span>

1.  <span data-ttu-id="c497a-150">このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="c497a-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="c497a-151">HoloLens をセットアップしてテストします。</span><span class="sxs-lookup"><span data-stu-id="c497a-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="c497a-152">HoloLens のセットアップをサポートする必要がある場合は、 [hololens セットアップに関する記事にアクセスして](https://docs.microsoft.com/hololens/hololens-setup)ください。</span><span class="sxs-lookup"><span data-stu-id="c497a-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="c497a-153">新しい HoloLens アプリの開発を開始するときは、調整とセンサーのチューニングを実行することをお勧めします (ユーザーごとにこれらのタスクを実行するのに役立つ場合があります)。</span><span class="sxs-lookup"><span data-stu-id="c497a-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="c497a-154">調整の詳細については、 [「HoloLens の調整に関する記事へのリンク」を](../../../calibration.md#hololens-2)参照してください。</span><span class="sxs-lookup"><span data-stu-id="c497a-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](../../../calibration.md#hololens-2).</span></span>

<span data-ttu-id="c497a-155">センサーチューニングの詳細については、 [HoloLens センサーチューニングに関する記事へのリンクを](../../../sensor-tuning.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="c497a-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](../../../sensor-tuning.md).</span></span>

## <a name="chapter-1---the-azure-portal"></a><span data-ttu-id="c497a-156">章 1-Azure Portal</span><span class="sxs-lookup"><span data-stu-id="c497a-156">Chapter 1 - The Azure Portal</span></span>

<span data-ttu-id="c497a-157">Azure で *Face API* サービスを使用するには、アプリケーションで使用できるようにサービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-157">To use the *Face API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="c497a-158">まず、 [Azure Portal](https://portal.azure.com)にログインします。</span><span class="sxs-lookup"><span data-stu-id="c497a-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="c497a-159">まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="c497a-160">このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。</span><span class="sxs-lookup"><span data-stu-id="c497a-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="c497a-161">ログインしたら、左上隅にある [ **新規** ] をクリックし、 *Face API* を検索して、 **enter キーを** 押します。</span><span class="sxs-lookup"><span data-stu-id="c497a-161">Once you are logged in, click on **New** in the top left corner, and search for *Face API* , press **Enter** .</span></span>

    ![face api の検索](images/AzureLabs-Lab4-01.png)

    > [!NOTE]
    > <span data-ttu-id="c497a-163">新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="c497a-163">The word **New** may have been replaced with **Create a resource** , in newer portals.</span></span>

3.  <span data-ttu-id="c497a-164">新しいページには、 *Face API* サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-164">The new page will provide a description of the *Face API* service.</span></span> <span data-ttu-id="c497a-165">このプロンプトの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="c497a-165">At the bottom left of this prompt, select the **Create** button, to create an association with this service.</span></span>

    ![face api 情報](images/AzureLabs-Lab4-02.png)

4.  <span data-ttu-id="c497a-167">[ **作成** :</span><span class="sxs-lookup"><span data-stu-id="c497a-167">Once you have clicked on **Create** :</span></span>

    1. <span data-ttu-id="c497a-168">このサービスインスタンスに必要な名前を挿入します。</span><span class="sxs-lookup"><span data-stu-id="c497a-168">Insert your desired name for this service instance.</span></span>

    2. <span data-ttu-id="c497a-169">サブスクリプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="c497a-169">Select a subscription.</span></span>

    3. <span data-ttu-id="c497a-170">適切な価格レベルを選択します。これが *Face API サービス* を初めて作成する場合は、free レベル (F0) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="c497a-170">Select the pricing tier appropriate for you, if this is the first time creating a *Face API Service* , a free tier (named F0) should be available to you.</span></span>

    4. <span data-ttu-id="c497a-171">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="c497a-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="c497a-172">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="c497a-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="c497a-173">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c497a-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="c497a-174">Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="c497a-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="c497a-175">後で使用する UWP **アプリでは、場所** として "米国西部" を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-175">The UWP app, **Person Maker** , which you use later, requires the use of 'West US' for location.</span></span>

    6. <span data-ttu-id="c497a-176">また、このサービスに適用されている使用条件を理解していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-176">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>

    7. <span data-ttu-id="c497a-177">[作成] \* を選択し **ます。**</span><span class="sxs-lookup"><span data-stu-id="c497a-177">Select **Create\*.**</span></span>

        ![face api サービスの作成](images/AzureLabs-Lab4-03.png)

5.  <span data-ttu-id="c497a-179">[ \*\*作成] \*\*\* をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="c497a-179">Once you have clicked on **Create\*,** you will have to wait for the service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="c497a-180">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-180">A notification will appear in the portal once the Service instance is created.</span></span>

    ![サービス作成の通知](images/AzureLabs-Lab4-04.png)

7.  <span data-ttu-id="c497a-182">通知をクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="c497a-182">Click on the notifications to explore your new Service instance.</span></span>

    ![リソース通知にアクセス](images/AzureLabs-Lab4-05.png)

8.  <span data-ttu-id="c497a-184">準備ができたら、通知の [ **リソースにアクセス** ] ボタンをクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="c497a-184">When you are ready, click **Go to resource** button in the notification to explore your new Service instance.</span></span>

    ![顔の api キーにアクセスする](images/AzureLabs-Lab4-06.png)

9.  <span data-ttu-id="c497a-186">このチュートリアルでは、アプリケーションがサービスの呼び出しを行う必要があります。サービスは、サービスのサブスクリプション ' key ' を使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-186">Within this tutorial, your application will need to make calls to your service, which is done through using your service's subscription 'key'.</span></span> <span data-ttu-id="c497a-187">*Face API* サービスの [ *クイックスタート* ] ページでは、最初のポイントは番号1で、 *キーを取得します。*</span><span class="sxs-lookup"><span data-stu-id="c497a-187">From the *Quick start* page, of your *Face API* service, the first point is number 1, to *Grab your keys.*</span></span>

10. <span data-ttu-id="c497a-188">[ *サービス* ] ページで、[青い **キー** ] ハイパーリンク ([クイックスタート] ページの場合)、または [サービス] ナビゲーションメニューの **[キー] リンク (** 左側にある [キー] アイコンで示されます) を選択して、キーを表示します。</span><span class="sxs-lookup"><span data-stu-id="c497a-188">On the *Service* page select either the blue **Keys** hyperlink (if on the Quick start page), or the **Keys** link in the services navigation menu (to the left, denoted by the 'key' icon), to reveal your keys.</span></span>

    > [!NOTE] 
    > <span data-ttu-id="c497a-189">後で必要になるので、いずれかのキーを書き留め、保護します。</span><span class="sxs-lookup"><span data-stu-id="c497a-189">Take note of either one of the keys and safeguard it, as you will need it later.</span></span>

## <a name="chapter-2---using-the-person-maker-uwp-application"></a><span data-ttu-id="c497a-190">Chapter 2-"Person Maker" UWP アプリケーションの使用</span><span class="sxs-lookup"><span data-stu-id="c497a-190">Chapter 2 - Using the 'Person Maker' UWP application</span></span>

<span data-ttu-id="c497a-191">「 [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip)」というビルド済みの UWP アプリケーションをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="c497a-191">Make sure to download the prebuilt UWP Application called [Person Maker](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/PersonMaker.zip).</span></span> <span data-ttu-id="c497a-192">このアプリは、このコースの最終的な製品ではなく、Azure エントリを作成するためのツールです。これは、それ以降のプロジェクトで利用されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-192">This app is not the end product for this course, just a tool to help you create your Azure entries, which the later project will rely upon.</span></span>

<span data-ttu-id="c497a-193">**個人のメーカー** では、ユーザーとグループに関連付けられている Azure エントリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c497a-193">**Person Maker** allows you to create Azure entries, which are associated with people, and groups of people.</span></span> <span data-ttu-id="c497a-194">アプリケーションは、必要なすべての情報を、後で FaceAPI が使用できる形式で配置します。これにより、追加したユーザーの顔を認識することができます。</span><span class="sxs-lookup"><span data-stu-id="c497a-194">The application will place all the needed information in a format which can then later be used by the FaceAPI, in order to recognize the faces of people whom you have added.</span></span> 

> <span data-ttu-id="c497a-195">: **個人所有者** は、いくつかの基本的な調整を使用して、 **無料サブスクリプションレベル** で1分あたりのサービス呼び出し数を超えないようにします。</span><span class="sxs-lookup"><span data-stu-id="c497a-195">[IMPORTANT] **Person Maker** uses some basic throttling, to help ensure that you do not exceed the number of service calls per minute for the **free subscription tier** .</span></span> <span data-ttu-id="c497a-196">調整が行われると、上部の緑色のテキストが赤に変わり、' アクティブ ' として更新されます。この場合は、アプリケーションを待機するだけです (これは、次に顔サービスへのアクセスが続行されるまで待機し、再度使用できるように "IN-アクティブ" として更新します)。</span><span class="sxs-lookup"><span data-stu-id="c497a-196">The green text at the top will change to red and update as 'ACTIVE' when throttling is happening; if this is the case, simply wait for the application (it will wait until it can next continue accessing the face service, updating as 'IN-ACTIVE' when you can use it again).</span></span>

<span data-ttu-id="c497a-197">このアプリケーションでは、 *ProjectOxford* ライブラリを使用します。これにより、Face API を最大限に活用することができます。</span><span class="sxs-lookup"><span data-stu-id="c497a-197">This application uses the *Microsoft.ProjectOxford.Face* libraries, which will allow you to make full use of the Face API.</span></span> <span data-ttu-id="c497a-198">このライブラリは、NuGet パッケージとして無料で利用できます。</span><span class="sxs-lookup"><span data-stu-id="c497a-198">This library is available for free as a NuGet Package.</span></span> <span data-ttu-id="c497a-199">これと同様の Api の詳細については、 [api リファレンスの記事を参照して](https://docs.microsoft.com/azure/cognitive-services/face/apireference)ください。</span><span class="sxs-lookup"><span data-stu-id="c497a-199">For more information about this, and similar, APIs [make sure to visit the API reference article](https://docs.microsoft.com/azure/cognitive-services/face/apireference).</span></span>

> [!NOTE] 
> <span data-ttu-id="c497a-200">これらの手順は、必要な手順にすぎません。これらを実行する手順については、ドキュメントの後半で説明します。</span><span class="sxs-lookup"><span data-stu-id="c497a-200">These are just the steps required, instructions for how to do these things is further down the document.</span></span> <span data-ttu-id="c497a-201">**個人のメーカー** アプリでは、次のことが可能です。</span><span class="sxs-lookup"><span data-stu-id="c497a-201">The **Person Maker** app will allow you to:</span></span>
>
> - <span data-ttu-id="c497a-202">*ユーザーグループ* を作成します。これは、関連付ける複数のユーザーで構成されるグループです。</span><span class="sxs-lookup"><span data-stu-id="c497a-202">Create a *Person Group* , which is a group composed of several people which you want to associate with it.</span></span> <span data-ttu-id="c497a-203">Azure アカウントを使用すると、複数のユーザーグループをホストできます。</span><span class="sxs-lookup"><span data-stu-id="c497a-203">With your Azure account you can host multiple Person Groups.</span></span>
>
> - <span data-ttu-id="c497a-204">Person グループのメンバーである *ユーザー* を作成します。</span><span class="sxs-lookup"><span data-stu-id="c497a-204">Create a *Person* , which is a member of a Person Group.</span></span> <span data-ttu-id="c497a-205">各ユーザーには、多数の *顔* イメージが関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="c497a-205">Each person has a number of *Face* images associated with it.</span></span>
>
> -  <span data-ttu-id="c497a-206">*顔イメージ* を *担当者* に割り当てて、Azure Face API サービスが対応する *顔* によって *個人* を認識できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c497a-206">Assign *face images* to a *Person* , to allow your Azure Face API Service to recognize a *Person* by the corresponding *face* .</span></span>
>
> -  <span data-ttu-id="c497a-207">*Azure Face API サービス* を *トレーニング* します。</span><span class="sxs-lookup"><span data-stu-id="c497a-207">*Train* your *Azure Face API Service* .</span></span>

<span data-ttu-id="c497a-208">このため、このアプリをトレーニングしてユーザーを認識させるには、個人グループに追加する各ユーザーの 10 (10) の写真が必要です。</span><span class="sxs-lookup"><span data-stu-id="c497a-208">Be aware, so to train this app to recognize people, you will need ten (10) close-up photos of each person which you would like to add to your Person Group.</span></span> <span data-ttu-id="c497a-209">Windows 10 Cam アプリを使用すると、これらのアプリを簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="c497a-209">The Windows 10 Cam App can help you to take these.</span></span> <span data-ttu-id="c497a-210">各写真が明確になっていることを確認する必要があります (ぼかし、覆い、または大きすぎないようにしてください)。また、画像ファイルのサイズが **4 MB** 以下で、 **1 KB** 未満の画像を jpg または png ファイル形式にしてください。</span><span class="sxs-lookup"><span data-stu-id="c497a-210">You must ensure that each photo is clear (avoid blurring, obscuring, or being too far, from the subject), have the photo in jpg or png file format, with the image file size being no larger **4 MB** , and no less than **1 KB** .</span></span>

> [!NOTE]
> <span data-ttu-id="c497a-211">このチュートリアルに従う場合は、お客様のトレーニングに独自の顔を使用しないでください。 HoloLens をオンにした場合は、自分で確認することはできません。</span><span class="sxs-lookup"><span data-stu-id="c497a-211">If you are following this tutorial, do not use your own face for training, as when you put the HoloLens on, you cannot look at yourself.</span></span> <span data-ttu-id="c497a-212">同僚や同僚の顔を使用します。</span><span class="sxs-lookup"><span data-stu-id="c497a-212">Use the face of a colleague or fellow student.</span></span>

<span data-ttu-id="c497a-213">実行中の **ユーザーのメーカー** :</span><span class="sxs-lookup"><span data-stu-id="c497a-213">Running **Person Maker** :</span></span>

1.  <span data-ttu-id="c497a-214">[ **個人** ] フォルダーを開き、[個人] *ソリューション* をダブルクリックして *Visual Studio* で開きます。</span><span class="sxs-lookup"><span data-stu-id="c497a-214">Open the **PersonMaker** folder and double click on the *PersonMaker solution* to open it with *Visual Studio* .</span></span>

2.  <span data-ttu-id="c497a-215">*個人メーカーソリューション* が開いたら、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c497a-215">Once the *PersonMaker solution* is open, make sure that:</span></span>

    1. <span data-ttu-id="c497a-216">*ソリューション構成* が **デバッグ** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="c497a-216">The *Solution Configuration* is set to **Debug** .</span></span>

    2. <span data-ttu-id="c497a-217">*ソリューションプラットフォーム* が **x86** に設定されている</span><span class="sxs-lookup"><span data-stu-id="c497a-217">The *Solution Platform* is set to **x86**</span></span>

    3. <span data-ttu-id="c497a-218">*ターゲットプラットフォーム* は **ローカルコンピューター** です。</span><span class="sxs-lookup"><span data-stu-id="c497a-218">The *Target Platform* is **Local Machine** .</span></span>

    4.  <span data-ttu-id="c497a-219">また、 *Nuget パッケージの復元* が必要になる場合もあります ( *ソリューション* を右クリックし、[ **nuget パッケージの復元** ] を選択します)。</span><span class="sxs-lookup"><span data-stu-id="c497a-219">You also may need to *Restore NuGet Packages* (right-click the *Solution* and select **Restore NuGet Packages** ).</span></span>

3.  <span data-ttu-id="c497a-220">[ *ローカルコンピューター* ] をクリックすると、アプリケーションが起動します。</span><span class="sxs-lookup"><span data-stu-id="c497a-220">Click *Local Machine* and the application will start.</span></span> <span data-ttu-id="c497a-221">小さい画面では、すべてのコンテンツが表示されない場合があることに注意してください。ただし、下にスクロールして表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="c497a-221">Be aware, on smaller screens, all content may not be visible, though you can scroll further down to view it.</span></span>

    ![個人のメーカーのユーザーインターフェイス](images/AzureLabs-Lab4-07.png)

4.  <span data-ttu-id="c497a-223">Azure 内の *Face API* サービスから、必要な **azure 認証キー** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="c497a-223">Insert your **Azure Authentication Key** , which you should have, from your *Face API* service within Azure.</span></span>

5.  <span data-ttu-id="c497a-224">挿入: </span><span class="sxs-lookup"><span data-stu-id="c497a-224">Insert:</span></span>

    1. <span data-ttu-id="c497a-225">*Person グループ* に割り当てる *ID* を指定します。</span><span class="sxs-lookup"><span data-stu-id="c497a-225">The *ID* you want to assign to the *Person Group* .</span></span> <span data-ttu-id="c497a-226">ID は小文字で指定する必要があります。スペースは使用できません。</span><span class="sxs-lookup"><span data-stu-id="c497a-226">The ID must be lowercase, with no spaces.</span></span> <span data-ttu-id="c497a-227">この ID は、後で Unity プロジェクトで必要になるため、メモしておいてください。</span><span class="sxs-lookup"><span data-stu-id="c497a-227">Make note of this ID, as it will be required later in your Unity project.</span></span>
    2. <span data-ttu-id="c497a-228">*Person グループ* に割り当てる *名前* (スペースを含めることができます)。</span><span class="sxs-lookup"><span data-stu-id="c497a-228">The *Name* you want to assign to the *Person Group* (can have spaces).</span></span>


6.  <span data-ttu-id="c497a-229">[ **Person Group を作成** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c497a-229">Press **Create Person Group** button.</span></span> <span data-ttu-id="c497a-230">ボタンの下に確認メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-230">A confirmation message should appear underneath the button.</span></span>

> [!NOTE]
> <span data-ttu-id="c497a-231">"アクセスが拒否されました" というエラーが発生する場合は、Azure サービス用に設定した場所を確認します。</span><span class="sxs-lookup"><span data-stu-id="c497a-231">If you have an 'Access Denied' error, check the location you set for your Azure service.</span></span> <span data-ttu-id="c497a-232">前述のように、このアプリは "米国西部" 向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="c497a-232">As stated above, this app is designed for 'West US'.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c497a-233">[ **既知のグループをフェッチ** ] ボタンをクリックすることもできます。これは、ユーザーグループを既に作成していて、新しいものを作成するのではなく、そのグループを使用する必要がある場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="c497a-233">You will notice that you can also click the **Fetch a Known Group** button: this is for if you have already created a person group, and wish to use that, rather than create a new one.</span></span> <span data-ttu-id="c497a-234">ただし、[既知のグループを持つ *ユーザーグループを作成* する] をクリックすると、グループもフェッチされます。</span><span class="sxs-lookup"><span data-stu-id="c497a-234">Be aware, if you click *Create a Person Group* with a known group, this will also fetch a group.</span></span>

7.  <span data-ttu-id="c497a-235">作成する *ユーザー* の *名前* を挿入します。</span><span class="sxs-lookup"><span data-stu-id="c497a-235">Insert the *Name* of the *Person* you want to create.</span></span>

    1. <span data-ttu-id="c497a-236">[ **Create Person** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c497a-236">Click the **Create Person** button.</span></span>

    2. <span data-ttu-id="c497a-237">ボタンの下に確認メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-237">A confirmation message should appear underneath the button.</span></span>

    3. <span data-ttu-id="c497a-238">以前に作成したユーザーを削除する場合は、名前をテキストボックスに入力し、del **person** キーを押します。</span><span class="sxs-lookup"><span data-stu-id="c497a-238">If you wish to delete a person you have previously created, you can write the name into the textbox and press **Delete Person**</span></span>

8.  <span data-ttu-id="c497a-239">グループに追加するユーザーの10枚の写真の場所がわかっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c497a-239">Make sure you know the location of ten (10) photos of the person you would like to add to your group.</span></span>

9.  <span data-ttu-id="c497a-240">[ **作成** ] をクリックしてフォルダーを開き、ユーザーに関連付けられているフォルダーにエクスプローラーを開きます。</span><span class="sxs-lookup"><span data-stu-id="c497a-240">Press **Create and Open Folder** to open Windows Explorer to the folder associated to the person.</span></span> <span data-ttu-id="c497a-241">10個のイメージをフォルダーに追加します。</span><span class="sxs-lookup"><span data-stu-id="c497a-241">Add the ten (10) images in the folder.</span></span> <span data-ttu-id="c497a-242">これらは、 *JPG* または *PNG* ファイル形式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-242">These must be of *JPG* or *PNG* file format.</span></span>

10. <span data-ttu-id="c497a-243">[ **Azure への送信** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c497a-243">Click on **Submit To Azure** .</span></span> <span data-ttu-id="c497a-244">カウンターには、送信の状態が表示され、その後、完了時にメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-244">A counter will show you the state of the submission, followed by a message when it has completed.</span></span>

11. <span data-ttu-id="c497a-245">カウンターが終了し、確認メッセージが表示されたら、[ **トレーニング** ] をクリックしてサービスをトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="c497a-245">Once the counter has finished and a confirmation message has been displayed click on **Train** to train your Service.</span></span>

<span data-ttu-id="c497a-246">プロセスが完了すると、Unity に移行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c497a-246">Once the process has completed, you are ready to move into Unity.</span></span>

## <a name="chapter-3---set-up-the-unity-project"></a><span data-ttu-id="c497a-247">章 3-Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="c497a-247">Chapter 3 - Set up the Unity project</span></span>

<span data-ttu-id="c497a-248">次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="c497a-248">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="c497a-249">*Unity* を開き、[ **新規** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c497a-249">Open *Unity* and click **New** .</span></span> 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab4-08.png)

2.  <span data-ttu-id="c497a-251">ここで、Unity プロジェクト名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-251">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="c497a-252">**MR_FaceRecognition** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="c497a-252">Insert **MR_FaceRecognition** .</span></span> <span data-ttu-id="c497a-253">プロジェクトの種類が **3d** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c497a-253">Make sure the project type is set to **3D** .</span></span> <span data-ttu-id="c497a-254">場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="c497a-254">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="c497a-255">次に、[ **プロジェクトの作成** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c497a-255">Then, click **Create project** .</span></span>

    ![新しい Unity プロジェクトの詳細を指定します。](images/AzureLabs-Lab4-09.png)

3.  <span data-ttu-id="c497a-257">Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-257">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio** .</span></span> <span data-ttu-id="c497a-258">[ **> の設定の編集** ] に移動し、新しいウィンドウで [ **外部ツール** ] に移動します。</span><span class="sxs-lookup"><span data-stu-id="c497a-258">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools** .</span></span> <span data-ttu-id="c497a-259">**外部スクリプトエディター** を **Visual Studio 2017** に変更します。</span><span class="sxs-lookup"><span data-stu-id="c497a-259">Change **External Script Editor** to **Visual Studio 2017** .</span></span> <span data-ttu-id="c497a-260">[ **基本設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c497a-260">Close the **Preferences** window.</span></span>

    ![スクリプトエディターの設定を更新します。](images/AzureLabs-Lab4-10.png)

4.  <span data-ttu-id="c497a-262">次に、[ **ファイル > ビルド設定** ] に移動し、[プラットフォームの **切り替え** ] ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="c497a-262">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform** , by clicking on the **Switch Platform** button.</span></span>

    ![[ビルドの設定] ウィンドウで、[プラットフォーム] を [UWP] に切り替えます。](images/AzureLabs-Lab4-11.png)

5.  <span data-ttu-id="c497a-264">[ **ファイル > ビルド設定** ] にアクセスし、次のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c497a-264">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="c497a-265">**ターゲットデバイス** が **HoloLens** に設定されています</span><span class="sxs-lookup"><span data-stu-id="c497a-265">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="c497a-266">イマーシブヘッドセットの場合は、 **ターゲットデバイス** を *任意のデバイス* に設定します。</span><span class="sxs-lookup"><span data-stu-id="c497a-266">For the immersive headsets, set **Target Device** to *Any Device* .</span></span>

    2. <span data-ttu-id="c497a-267">**ビルドの種類** が **D3D** に設定されています</span><span class="sxs-lookup"><span data-stu-id="c497a-267">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="c497a-268">**SDK** は最新の **インストール** に設定されています</span><span class="sxs-lookup"><span data-stu-id="c497a-268">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="c497a-269">**Visual Studio のバージョン** が、 **インストールされている最新** バージョンに設定されています</span><span class="sxs-lookup"><span data-stu-id="c497a-269">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="c497a-270">**ビルドと実行** は **ローカルコンピューター** に設定されています</span><span class="sxs-lookup"><span data-stu-id="c497a-270">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="c497a-271">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="c497a-271">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="c497a-272">これを行うには、[開いている **シーンの追加** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c497a-272">Do this by selecting **Add Open Scenes** .</span></span> <span data-ttu-id="c497a-273">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-273">A save window will appear.</span></span>

            ![[開いているシーンを追加] ボタンをクリックする](images/AzureLabs-Lab4-12.png)

        2. <span data-ttu-id="c497a-275">[ **新しいフォルダー** ] ボタンを選択し、新しいフォルダーを作成するには、「 **シーン** 」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c497a-275">Select the **New folder** button, to create a new folder, name it **Scenes** .</span></span>

            ![新しいスクリプトフォルダーの作成](images/AzureLabs-Lab4-13.png)

        3. <span data-ttu-id="c497a-277">新しく作成した [ **シーン** ] フォルダーを開き、[ **ファイル名** : テキスト] フィールドに「 **FaceRecScene** 」と入力し、[ **保存** ] を押します。</span><span class="sxs-lookup"><span data-stu-id="c497a-277">Open your newly created **Scenes** folder, and then in the **File name** : text field, type **FaceRecScene** , then press **Save** .</span></span>

            ![新しいシーンに名前を付けます。](images/AzureLabs-Lab4-14.png)

    7. <span data-ttu-id="c497a-279">それ以外の設定は、[ *ビルド設定* ] の [既定] のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="c497a-279">The remaining settings, in *Build Settings* , should be left as default for now.</span></span>

6. <span data-ttu-id="c497a-280">[ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="c497a-280">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![プレーヤーの設定を開きます。](images/AzureLabs-Lab4-15.png)

7. <span data-ttu-id="c497a-282">このパネルでは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-282">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="c497a-283">[ **その他の設定** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="c497a-283">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="c497a-284">**Scripting** **Runtime のバージョン** は **実験的** である必要があります (.net 4.6 と同等)。</span><span class="sxs-lookup"><span data-stu-id="c497a-284">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent).</span></span> <span data-ttu-id="c497a-285">これを変更すると、エディターを再起動する必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="c497a-285">Changing this will trigger a need to restart the Editor.</span></span>
        2. <span data-ttu-id="c497a-286">**バックエンド** は **.net** である必要があります</span><span class="sxs-lookup"><span data-stu-id="c497a-286">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="c497a-287">**API 互換性レベル** は **.net 4.6** である必要があります</span><span class="sxs-lookup"><span data-stu-id="c497a-287">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![その他の設定を更新します。](images/AzureLabs-Lab4-16.png)
      
    2. <span data-ttu-id="c497a-289">[ **発行の設定** ] タブの [ **機能** ] で、次の項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="c497a-289">Within the **Publishing Settings** tab, under **Capabilities** , check:</span></span>

        - <span data-ttu-id="c497a-290">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="c497a-290">**InternetClient**</span></span>
        - <span data-ttu-id="c497a-291">**Web カメラ**</span><span class="sxs-lookup"><span data-stu-id="c497a-291">**Webcam**</span></span>

            ![発行設定を更新しています。](images/AzureLabs-Lab4-17.png)

    3. <span data-ttu-id="c497a-293">パネルの下にある [ **XR settings** (発行の **設定** ] の下にあります) で、[ **サポートされている仮想現実** ] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c497a-293">Further down the panel, in **XR Settings** (found below **Publish Settings** ), tick **Virtual Reality Supported** , make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![X R の設定を更新します。](images/AzureLabs-Lab4-18.png)

8.  <span data-ttu-id="c497a-295">*ビルド設定* に戻ると、 **Unity C# プロジェクト** はグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="c497a-295">Back in *Build Settings* , **Unity C# Projects** is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="c497a-296">[ビルド設定] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="c497a-296">Close the Build Settings window.</span></span>
10. <span data-ttu-id="c497a-297">シーンとプロジェクトを保存します ([ **ファイル] > [シーン/ファイルの保存] > [プロジェクトの保存** ])。</span><span class="sxs-lookup"><span data-stu-id="c497a-297">Save your Scene and Project ( **FILE > SAVE SCENE / FILE > SAVE PROJECT** ).</span></span>

## <a name="chapter-4---main-camera-setup"></a><span data-ttu-id="c497a-298">第4章-メインカメラのセットアップ</span><span class="sxs-lookup"><span data-stu-id="c497a-298">Chapter 4 - Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c497a-299">このコースの *Unity セットアップ* コンポーネントをスキップし、コードに直接進む場合は、 [unitypackage をダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage)して、 [カスタムパッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてください。</span><span class="sxs-lookup"><span data-stu-id="c497a-299">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/Azure-MR-304.unitypackage), and import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html).</span></span> <span data-ttu-id="c497a-300">このパッケージには、 [5 章](#chapter-5--import-the-newtonsoftjson-library)で説明されている *NEWTONSOFT DLL* のインポートも含まれることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c497a-300">Be aware that this package also includes the import of the *Newtonsoft DLL* , covered in [Chapter 5](#chapter-5--import-the-newtonsoftjson-library).</span></span> <span data-ttu-id="c497a-301">インポートされたを使用して、 [6 章](#chapter-6---create-the-faceanalysis-class)から続行することができます。</span><span class="sxs-lookup"><span data-stu-id="c497a-301">With this imported, you can continue from [Chapter 6](#chapter-6---create-the-faceanalysis-class).</span></span>

1.  <span data-ttu-id="c497a-302">[ *階層* ] パネルで、 **メインカメラ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c497a-302">In the *Hierarchy* Panel, select the **Main Camera** .</span></span>

2.  <span data-ttu-id="c497a-303">選択すると、 **メインカメラ** のすべてのコンポーネントが [ *インスペクター] パネル* に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-303">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel* .</span></span>

    1. <span data-ttu-id="c497a-304">**カメラオブジェクト** は **メインカメラ** という名前にする必要があります (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="c497a-304">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2. <span data-ttu-id="c497a-305">メインカメラの **タグ** は、 **maincamera** に設定する必要があります (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="c497a-305">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3. <span data-ttu-id="c497a-306">**変換位置** が **0、0、0** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c497a-306">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4. <span data-ttu-id="c497a-307">**クリアフラグ** を **純色** に設定する</span><span class="sxs-lookup"><span data-stu-id="c497a-307">Set **Clear Flags** to **Solid Color**</span></span>

    5. <span data-ttu-id="c497a-308">カメラコンポーネントの **背景** 色を **黒、アルファ 0 (16 進コード: #00000000)** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c497a-308">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

        ![カメラコンポーネントの設定](images/AzureLabs-Lab4-19.png) 

## <a name="chapter-5--import-the-newtonsoftjson-library"></a><span data-ttu-id="c497a-310">Chapter 5 –ライブラリに Newtonsoft.Jsをインポートする</span><span class="sxs-lookup"><span data-stu-id="c497a-310">Chapter 5 – Import the Newtonsoft.Json library</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c497a-311">[最後の章](#chapter-4---main-camera-setup)で "unitypackage" をインポートした場合は、この章をスキップできます。</span><span class="sxs-lookup"><span data-stu-id="c497a-311">If you imported the '.unitypackage' in the [last Chapter](#chapter-4---main-camera-setup), you can skip this Chapter.</span></span>

<span data-ttu-id="c497a-312">受信して Bot サービスに送信されたオブジェクトを逆シリアル化およびシリアル化するには、ライブラリ *にNewtonsoft.Js* をダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-312">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the *Newtonsoft.Json* library.</span></span> <span data-ttu-id="c497a-313">この [unity パッケージファイル](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage)には、適切な unity フォルダー構造が既に構成されている互換性のあるバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="c497a-313">You will find a compatible version already organized with the correct Unity folder structure in this [Unity package file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20304%20-%20Face%20recognition/newtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="c497a-314">ライブラリをインポートするには:</span><span class="sxs-lookup"><span data-stu-id="c497a-314">To import the library:</span></span>

1.  <span data-ttu-id="c497a-315">Unity パッケージをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="c497a-315">Download the Unity Package.</span></span>
2.  <span data-ttu-id="c497a-316">[ **資産** ]、[ **パッケージのインポート** ]、[ **カスタムパッケージ** ] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="c497a-316">Click on **Assets** , **Import Package** , **Custom Package** .</span></span>

    ![Newtonsoft.Jsのインポート](images/AzureLabs-Lab4-20.png)

3.  <span data-ttu-id="c497a-318">ダウンロードした Unity パッケージを探し、[開く] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c497a-318">Look for the Unity Package you have downloaded, and click Open.</span></span>
4.  <span data-ttu-id="c497a-319">パッケージのすべてのコンポーネントが解除されていることを確認し、[ **インポート** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c497a-319">Make sure all the components of the package are ticked and click **Import** .</span></span>

    ![資産に Newtonsoft.Jsをインポートする](images/AzureLabs-Lab4-21.png)

## <a name="chapter-6---create-the-faceanalysis-class"></a><span data-ttu-id="c497a-321">Chapter 6-FaceAnalysis クラスの作成</span><span class="sxs-lookup"><span data-stu-id="c497a-321">Chapter 6 - Create the FaceAnalysis class</span></span>

<span data-ttu-id="c497a-322">FaceAnalysis クラスの目的は、Azure Face 認識サービスとの通信に必要なメソッドをホストすることです。</span><span class="sxs-lookup"><span data-stu-id="c497a-322">The purpose of the FaceAnalysis class is to host the methods necessary to communicate with your Azure Face Recognition Service.</span></span> 

- <span data-ttu-id="c497a-323">サービスは、キャプチャイメージを送信した後、それを分析して内の顔を識別し、既知のユーザーに属しているかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="c497a-323">After sending the service a capture image, it will analyse it and identify the faces within, and determine if any belong to a known person.</span></span> 
- <span data-ttu-id="c497a-324">既知の人が見つかると、このクラスの名前が UI テキストとしてシーンに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-324">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="c497a-325">*FaceAnalysis* クラスを作成するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="c497a-325">To create the *FaceAnalysis* class:</span></span>

 1. <span data-ttu-id="c497a-326">[プロジェクト] パネルにある [ *アセット] フォルダー* を右クリックし、[フォルダーの **作成** ] をクリックし  >  **Folder** ます。</span><span class="sxs-lookup"><span data-stu-id="c497a-326">Right-click in the *Assets Folder* located in the Project Panel, then click on **Create** > **Folder** .</span></span> <span data-ttu-id="c497a-327">フォルダー **スクリプト** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c497a-327">Call the folder **Scripts** .</span></span> 

    ![FaceAnalysis クラスを作成します。](images/AzureLabs-Lab4-22.png)

2.  <span data-ttu-id="c497a-329">先ほど作成したフォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="c497a-329">Double click on the folder just created, to open it.</span></span> 
3.  <span data-ttu-id="c497a-330">フォルダー内を右クリックし、[ **Create**  >  **C# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c497a-330">Right-click inside the folder, then click on **Create** > **C# Script** .</span></span> <span data-ttu-id="c497a-331">スクリプト *FaceAnalysis* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c497a-331">Call the script *FaceAnalysis* .</span></span> 
4.  <span data-ttu-id="c497a-332">新しい *FaceAnalysis* スクリプトをダブルクリックして、Visual Studio 2017 で開きます。</span><span class="sxs-lookup"><span data-stu-id="c497a-332">Double click on the new *FaceAnalysis* script to open it with Visual Studio 2017.</span></span>
5.  <span data-ttu-id="c497a-333">*FaceAnalysis* クラスの上に次の名前空間を入力します。</span><span class="sxs-lookup"><span data-stu-id="c497a-333">Enter the following namespaces above the *FaceAnalysis* class:</span></span>

    ```csharp
        using Newtonsoft.Json;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using System.Text;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

6.  <span data-ttu-id="c497a-334">次に、deserialising に使用されるすべてのオブジェクトを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-334">You now need to add all of the objects which are used for deserialising.</span></span> <span data-ttu-id="c497a-335">これらのオブジェクトは、 *FaceAnalysis* スクリプトの **外側** (下かっこの下) に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-335">These objects need to be added **outside** of the *FaceAnalysis* script (beneath the bottom curly bracket).</span></span> 

    ```csharp
        /// <summary>
        /// The Person Group object
        /// </summary>
        public class Group_RootObject
        {
            public string personGroupId { get; set; }
            public string name { get; set; }
            public object userData { get; set; }
        }

        /// <summary>
        /// The Person Face object
        /// </summary>
        public class Face_RootObject
        {
            public string faceId { get; set; }
        }

        /// <summary>
        /// Collection of faces that needs to be identified
        /// </summary>
        public class FacesToIdentify_RootObject
        {
            public string personGroupId { get; set; }
            public List<string> faceIds { get; set; }
            public int maxNumOfCandidatesReturned { get; set; }
            public double confidenceThreshold { get; set; }
        }

        /// <summary>
        /// Collection of Candidates for the face
        /// </summary>
        public class Candidate_RootObject
        {
            public string faceId { get; set; }
            public List<Candidate> candidates { get; set; }
        }

        public class Candidate
        {
            public string personId { get; set; }
            public double confidence { get; set; }
        }

        /// <summary>
        /// Name and Id of the identified Person
        /// </summary>
        public class IdentifiedPerson_RootObject
        {
            public string personId { get; set; }
            public string name { get; set; }
        }
    ```
7. <span data-ttu-id="c497a-336">*Start ()* および *Update ()* メソッドは使用されないため、ここで削除します。</span><span class="sxs-lookup"><span data-stu-id="c497a-336">The *Start()* and *Update()* methods will not be used, so delete them now.</span></span> 

8.  <span data-ttu-id="c497a-337">*FaceAnalysis* クラス内で、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="c497a-337">Inside the *FaceAnalysis* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static FaceAnalysis Instance;

        /// <summary>
        /// The analysis result text
        /// </summary>
        private TextMesh labelText;

        /// <summary>
        /// Bytes of the image captured with camera
        /// </summary>
        internal byte[] imageBytes;

        /// <summary>
        /// Path of the image captured with camera
        /// </summary>
        internal string imagePath;

        /// <summary>
        /// Base endpoint of Face Recognition Service
        /// </summary>
        const string baseEndpoint = "https://westus.api.cognitive.microsoft.com/face/v1.0/";

        /// <summary>
        /// Auth key of Face Recognition Service
        /// </summary>
        private const string key = "- Insert your key here -";

        /// <summary>
        /// Id (name) of the created person group 
        /// </summary>
        private const string personGroupId = "- Insert your group Id here -";
    ```

    > [!NOTE]
    > <span data-ttu-id="c497a-338">**キー** および **ユーザーをサービスキーで置き換え** 、前に作成したグループの Id に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c497a-338">Replace the **key** and the **personGroupId** with your Service Key and the Id of the group that you created previously.</span></span>

9.  <span data-ttu-id="c497a-339">Initialises *()* メソッドを追加します。このメソッドは、クラスを作成し、 *Imagecapture* クラスをメインカメラに追加して、ラベルの作成メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c497a-339">Add the *Awake()* method, which initialises the class, adding the *ImageCapture* class to the Main Camera and calls the Label creation method:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            Instance = this;

            // Add the ImageCapture Class to this Game Object
            gameObject.AddComponent<ImageCapture>();

            // Create the text label in the scene
            CreateLabel();
        }
    ```

10. <span data-ttu-id="c497a-340">*CreateLabel ()* メソッドを追加します。このメソッドは、分析結果を表示する *Label* オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="c497a-340">Add the *CreateLabel()* method, which creates the *Label* object to display the analysis result:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private void CreateLabel()
        {
            // Create a sphere as new cursor
            GameObject newLabel = new GameObject();

            // Attach the label to the Main Camera
            newLabel.transform.parent = gameObject.transform;
            
            // Resize and position the new cursor
            newLabel.transform.localScale = new Vector3(0.4f, 0.4f, 0.4f);
            newLabel.transform.position = new Vector3(0f, 3f, 60f);

            // Creating the text of the Label
            labelText = newLabel.AddComponent<TextMesh>();
            labelText.anchor = TextAnchor.MiddleCenter;
            labelText.alignment = TextAlignment.Center;
            labelText.tabSize = 4;
            labelText.fontSize = 50;
            labelText.text = ".";       
        }
    ```

11. <span data-ttu-id="c497a-341">検出さ *れた* *GetImageAsByteArray ()* メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="c497a-341">Add the *DetectFacesFromImage()* and *GetImageAsByteArray()* method.</span></span> <span data-ttu-id="c497a-342">前者は、送信されたイメージで考えられる顔を検出するように顔認識サービスに要求します。後者の場合、キャプチャしたイメージをバイト配列に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-342">The former will request the Face Recognition Service to detect any possible face in the submitted image, while the latter is necessary to convert the captured image into a bytes array:</span></span>

    ```csharp
        /// <summary>
        /// Detect faces from a submitted image
        /// </summary>
        internal IEnumerator DetectFacesFromImage()
        {
            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}detect";

            // Change the image into a bytes array
            imageBytes = GetImageAsByteArray(imagePath);

            using (UnityWebRequest www = 
                UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/octet-stream");
                www.uploadHandler.contentType = "application/octet-stream";
                www.uploadHandler = new UploadHandlerRaw(imageBytes);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Face_RootObject[] face_RootObject = 
                    JsonConvert.DeserializeObject<Face_RootObject[]>(jsonResponse);

                List<string> facesIdList = new List<string>();
                // Create a list with the face Ids of faces detected in image
                foreach (Face_RootObject faceRO in face_RootObject)
                {
                    facesIdList.Add(faceRO.faceId);
                    Debug.Log($"Detected face - Id: {faceRO.faceId}");
                }
                
                StartCoroutine(IdentifyFaces(facesIdList));
            }
        }

        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }
    ```

12. <span data-ttu-id="c497a-343">*IdentifyFaces ()* メソッドを追加します。このメソッドは、送信されたイメージで以前に検出された既知の顔を識別するように *顔認識サービス* に要求します。</span><span class="sxs-lookup"><span data-stu-id="c497a-343">Add the *IdentifyFaces()* method, which requests the *Face Recognition Service* to identify any known face previously detected in the submitted image.</span></span> <span data-ttu-id="c497a-344">この要求は、識別されたユーザーの id を返しますが、名前は返しません。</span><span class="sxs-lookup"><span data-stu-id="c497a-344">The request will return an id of the identified person but not the name:</span></span>

    ```csharp
        /// <summary>
        /// Identify the faces found in the image within the person group
        /// </summary>
        internal IEnumerator IdentifyFaces(List<string> listOfFacesIdToIdentify)
        {
            // Create the object hosting the faces to identify
            FacesToIdentify_RootObject facesToIdentify = new FacesToIdentify_RootObject();
            facesToIdentify.faceIds = new List<string>();
            facesToIdentify.personGroupId = personGroupId;
            foreach (string facesId in listOfFacesIdToIdentify)
            {
                facesToIdentify.faceIds.Add(facesId);
            }
            facesToIdentify.maxNumOfCandidatesReturned = 1;
            facesToIdentify.confidenceThreshold = 0.5;

            // Serialize to Json format
            string facesToIdentifyJson = JsonConvert.SerializeObject(facesToIdentify);
            // Change the object into a bytes array
            byte[] facesData = Encoding.UTF8.GetBytes(facesToIdentifyJson);

            WWWForm webForm = new WWWForm();
            string detectFacesEndpoint = $"{baseEndpoint}identify";

            using (UnityWebRequest www = UnityWebRequest.Post(detectFacesEndpoint, webForm))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.SetRequestHeader("Content-Type", "application/json");
                www.uploadHandler.contentType = "application/json";
                www.uploadHandler = new UploadHandlerRaw(facesData);
                www.downloadHandler = new DownloadHandlerBuffer();

                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;
                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                Candidate_RootObject [] candidate_RootObject = JsonConvert.DeserializeObject<Candidate_RootObject[]>(jsonResponse);

                // For each face to identify that ahs been submitted, display its candidate
                foreach (Candidate_RootObject candidateRO in candidate_RootObject)
                {
                    StartCoroutine(GetPerson(candidateRO.candidates[0].personId));
                    
                    // Delay the next "GetPerson" call, so all faces candidate are displayed properly
                    yield return new WaitForSeconds(3);
                }           
            }
        }
    ```

13. <span data-ttu-id="c497a-345">*Getperson ()* メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="c497a-345">Add the *GetPerson()* method.</span></span> <span data-ttu-id="c497a-346">このメソッドは、person id を指定することで、 *顔認識サービス* に対して、識別された人物の名前を返すよう要求します。</span><span class="sxs-lookup"><span data-stu-id="c497a-346">By providing the person id, this method then requests for the *Face Recognition Service* to return the name of the identified person:</span></span>

    ```csharp
        /// <summary>
        /// Provided a personId, retrieve the person name associated with it
        /// </summary>
        internal IEnumerator GetPerson(string personId)
        {
            string getGroupEndpoint = $"{baseEndpoint}persongroups/{personGroupId}/persons/{personId}?";
            WWWForm webForm = new WWWForm();

            using (UnityWebRequest www = UnityWebRequest.Get(getGroupEndpoint))
            {
                www.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                www.downloadHandler = new DownloadHandlerBuffer();
                yield return www.SendWebRequest();
                string jsonResponse = www.downloadHandler.text;

                Debug.Log($"Get Person - jsonResponse: {jsonResponse}");
                IdentifiedPerson_RootObject identifiedPerson_RootObject = JsonConvert.DeserializeObject<IdentifiedPerson_RootObject>(jsonResponse);

                // Display the name of the person in the UI
                labelText.text = identifiedPerson_RootObject.name;
            }
        }
    ```

14.  <span data-ttu-id="c497a-347">Unity エディターに戻る前に、変更を **保存** してください。</span><span class="sxs-lookup"><span data-stu-id="c497a-347">Remember to **Save** the changes before going back to the Unity Editor.</span></span>
15.  <span data-ttu-id="c497a-348">Unity エディターで、[プロジェクト] パネルの [スクリプト] フォルダーから、[ *階層] パネル* のメインカメラオブジェクトに FaceAnalysis スクリプトをドラッグします。</span><span class="sxs-lookup"><span data-stu-id="c497a-348">In the Unity Editor, drag the FaceAnalysis script from the Scripts folder in Project panel to the Main Camera object in the *Hierarchy panel* .</span></span> <span data-ttu-id="c497a-349">新しいスクリプトコンポーネントがメインカメラに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-349">The new script component will be so added to the Main Camera.</span></span> 

![FaceAnalysis をメインカメラに配置する](images/AzureLabs-Lab4-23.png)


## <a name="chapter-7---create-the-imagecapture-class"></a><span data-ttu-id="c497a-351">第7章-ImageCapture クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="c497a-351">Chapter 7 - Create the ImageCapture class</span></span>

<span data-ttu-id="c497a-352">*Imagecapture* クラスの目的は、 *Azure 顔認識サービス* との通信に必要なメソッドをホストして、キャプチャするイメージを分析し、そこで顔を特定し、既知のユーザーに属しているかどうかを判断することです。</span><span class="sxs-lookup"><span data-stu-id="c497a-352">The purpose of the *ImageCapture* class is to host the methods necessary to communicate with your *Azure Face Recognition Service* to analyse the image you will capture, identifying faces in it and determining if it belongs to a known person.</span></span> <span data-ttu-id="c497a-353">既知の人が見つかると、このクラスの名前が UI テキストとしてシーンに表示されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-353">If a known person is found, this class will display its name as UI text in the scene.</span></span>

<span data-ttu-id="c497a-354">*Imagecapture* クラスを作成するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="c497a-354">To create the *ImageCapture* class:</span></span>
 
1.  <span data-ttu-id="c497a-355">先ほど作成した **Scripts** フォルダー内を右クリックし、[ **作成** ]、[ **C# スクリプト** ] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="c497a-355">Right-click inside the **Scripts** folder you have created previously, then click on **Create** , **C# Script** .</span></span> <span data-ttu-id="c497a-356">スクリプト *Imagecapture* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c497a-356">Call the script *ImageCapture* .</span></span> 
2.  <span data-ttu-id="c497a-357">新しい *Imagecapture* スクリプトをダブルクリックして、Visual Studio 2017 で開きます。</span><span class="sxs-lookup"><span data-stu-id="c497a-357">Double click on the new *ImageCapture* script to open it with Visual Studio 2017.</span></span>
3.  <span data-ttu-id="c497a-358">ImageCapture クラスの上に次の名前空間を入力します。</span><span class="sxs-lookup"><span data-stu-id="c497a-358">Enter the following namespaces above the ImageCapture class:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

4.  <span data-ttu-id="c497a-359">*Imagecapture* クラス内で、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="c497a-359">Inside the *ImageCapture* class, add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static ImageCapture instance;

        /// <summary>
        /// Keeps track of tapCounts to name the captured images 
        /// </summary>
        private int tapsCount;

        /// <summary>
        /// PhotoCapture object used to capture images on HoloLens 
        /// </summary>
        private PhotoCapture photoCaptureObject = null;

        /// <summary>
        /// HoloLens class to capture user gestures
        /// </summary>
        private GestureRecognizer recognizer;
    ```

5.  <span data-ttu-id="c497a-360">クラスを初期化するために必要な起動前 *()* および *開始 ()* メソッドを追加し、HoloLens がユーザーのジェスチャをキャプチャできるようにします。</span><span class="sxs-lookup"><span data-stu-id="c497a-360">Add the *Awake()* and *Start()* methods necessary to initialise the class and allow the HoloLens to capture the user's gestures:</span></span>

    ```csharp
        /// <summary>
        /// Initialises this class
        /// </summary>
        private void Awake()
        {
            instance = this;
        }

        /// <summary>
        /// Called right after Awake
        /// </summary>
        void Start()
        {
            // Initialises user gestures capture 
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

6.  <span data-ttu-id="c497a-361">ユーザーが *Tap* ジェスチャを実行したときに呼び出される *TapHandler ()* を追加します。</span><span class="sxs-lookup"><span data-stu-id="c497a-361">Add the *TapHandler()* which is called when the user performs a *Tap* gesture:</span></span>

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            tapsCount++;
            ExecuteImageCaptureAndAnalysis();
        }
    ```

7.  <span data-ttu-id="c497a-362">次のように、 *Executeimagecapの Andanalysis ()* メソッドを追加します。これにより、イメージキャプチャのプロセスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-362">Add the *ExecuteImageCaptureAndAnalysis()* method, which will begin the process of Image Capturing:</span></span>

    ```csharp
        /// <summary>
        /// Begin process of Image Capturing and send To Azure Computer Vision service.
        /// </summary>
        private void ExecuteImageCaptureAndAnalysis()
        {
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending
                ((res) => res.width * res.height).First();
            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);

            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)
            {
                photoCaptureObject = captureObject;

                CameraParameters c = new CameraParameters();
                c.hologramOpacity = 0.0f;
                c.cameraResolutionWidth = targetTexture.width;
                c.cameraResolutionHeight = targetTexture.height;
                c.pixelFormat = CapturePixelFormat.BGRA32;

                captureObject.StartPhotoModeAsync(c, delegate (PhotoCapture.PhotoCaptureResult result)
                {
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    // Set the image path on the FaceAnalysis class
                    FaceAnalysis.Instance.imagePath = filePath;

                    photoCaptureObject.TakePhotoAsync
                    (filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);
                });
            });
        }
    ```

8.  <span data-ttu-id="c497a-363">写真キャプチャプロセスが完了したときに呼び出されるハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="c497a-363">Add the handlers that are called when the photo capture process has been completed:</span></span>

    ```csharp
        /// <summary>
        /// Called right after the photo capture process has concluded
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin the Image Analysis process.
        /// </summary>
        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            photoCaptureObject.Dispose();
            photoCaptureObject = null;

            // Request image caputer analysis
            StartCoroutine(FaceAnalysis.Instance.DetectFacesFromImage());
        }
    ```

9. <span data-ttu-id="c497a-364">Unity エディターに戻る前に、変更を **保存** してください。</span><span class="sxs-lookup"><span data-stu-id="c497a-364">Remember to **Save** the changes before going back to the Unity Editor.</span></span>

## <a name="chapter-8---building-the-solution"></a><span data-ttu-id="c497a-365">第8章-ソリューションのビルド</span><span class="sxs-lookup"><span data-stu-id="c497a-365">Chapter 8 - Building the solution</span></span>

<span data-ttu-id="c497a-366">アプリケーションの徹底的なテストを実行するには、アプリケーションを HoloLens にサイドロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-366">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>

<span data-ttu-id="c497a-367">これを行う前に、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c497a-367">Before you do, ensure that:</span></span>

-   <span data-ttu-id="c497a-368">章3で説明したすべての設定が正しく設定されています。</span><span class="sxs-lookup"><span data-stu-id="c497a-368">All the settings mentioned in the Chapter 3 are set correctly.</span></span> 
-   <span data-ttu-id="c497a-369">スクリプト *FaceAnalysis* は、メインカメラオブジェクトにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="c497a-369">The script *FaceAnalysis* is attached to the Main Camera object.</span></span> 
-   <span data-ttu-id="c497a-370">**認証キー** と **グループ Id** の両方が *FaceAnalysis* スクリプト内で設定されています。</span><span class="sxs-lookup"><span data-stu-id="c497a-370">Both the **Auth Key** and **Group Id** have been set within the *FaceAnalysis* script.</span></span>

<span data-ttu-id="c497a-371">この時点で、ソリューションをビルドする準備ができました。</span><span class="sxs-lookup"><span data-stu-id="c497a-371">A this point you are ready to build the Solution.</span></span> <span data-ttu-id="c497a-372">ソリューションがビルドされると、アプリケーションをデプロイする準備が整います。</span><span class="sxs-lookup"><span data-stu-id="c497a-372">Once the Solution has been built, you will be ready to deploy your application.</span></span>

<span data-ttu-id="c497a-373">ビルドプロセスを開始するには:</span><span class="sxs-lookup"><span data-stu-id="c497a-373">To begin the Build process:</span></span>

1.  <span data-ttu-id="c497a-374">[ファイル]、[保存] の順にクリックして、現在のシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="c497a-374">Save the current scene by clicking on File, Save.</span></span>
2.  <span data-ttu-id="c497a-375">[ファイル]、[ビルドの設定]、[開いているシーンの追加] の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="c497a-375">Go to File, Build Settings, click on Add Open Scenes.</span></span>
3.  <span data-ttu-id="c497a-376">Unity C# プロジェクトをティックするようにしてください。</span><span class="sxs-lookup"><span data-stu-id="c497a-376">Make sure to tick Unity C# Projects.</span></span>

    ![Visual Studio ソリューションをデプロイする](images/AzureLabs-Lab4-24.png)

4.  <span data-ttu-id="c497a-378">ビルドを押します。</span><span class="sxs-lookup"><span data-stu-id="c497a-378">Press Build.</span></span> <span data-ttu-id="c497a-379">これにより、Unity はエクスプローラーウィンドウを起動します。このウィンドウでは、アプリをビルドするフォルダーを作成して選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-379">Upon doing so, Unity will launch a File Explorer window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="c497a-380">Unity プロジェクト内でこのフォルダーを作成し、アプリを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c497a-380">Create that folder now, within the Unity project, and call it App.</span></span> <span data-ttu-id="c497a-381">次に、アプリフォルダーを選択し、[フォルダーの選択] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c497a-381">Then with the App folder selected, press Select Folder.</span></span> 
5.  <span data-ttu-id="c497a-382">Unity は、アプリフォルダーにプロジェクトのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="c497a-382">Unity will begin building your project, out to the App folder.</span></span> 
6.  <span data-ttu-id="c497a-383">Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所でファイルエクスプローラーウィンドウが開きます。</span><span class="sxs-lookup"><span data-stu-id="c497a-383">Once Unity has finished building (it might take some time), it will open a File Explorer window at the location of your build.</span></span>

    ![Visual Studio からソリューションをデプロイする](images/AzureLabs-Lab4-25.png)

7.  <span data-ttu-id="c497a-385">アプリフォルダーを開き、新しいプロジェクトソリューションを開きます (前述のように、MR_FaceRecognition .sln)。</span><span class="sxs-lookup"><span data-stu-id="c497a-385">Open your App folder, and then open the new Project Solution (as seen above, MR_FaceRecognition.sln).</span></span>


## <a name="chapter-9---deploying-your-application"></a><span data-ttu-id="c497a-386">第9章-アプリケーションのデプロイ</span><span class="sxs-lookup"><span data-stu-id="c497a-386">Chapter 9 - Deploying your application</span></span>

<span data-ttu-id="c497a-387">HoloLens に展開するには:</span><span class="sxs-lookup"><span data-stu-id="c497a-387">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="c497a-388">Hololens が **開発者モード** になっていることを確認するには、HOLOLENS の IP アドレス (リモートデプロイ用) が必要です。</span><span class="sxs-lookup"><span data-stu-id="c497a-388">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode** .</span></span> <span data-ttu-id="c497a-389">これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="c497a-389">To do this:</span></span>

    1. <span data-ttu-id="c497a-390">HoloLens を装着した後、 **設定** を開きます。</span><span class="sxs-lookup"><span data-stu-id="c497a-390">Whilst wearing your HoloLens, open the **Settings** .</span></span>
    2. <span data-ttu-id="c497a-391">**[ネットワーク & インターネット > wi-fi > 詳細オプション]** にアクセス</span><span class="sxs-lookup"><span data-stu-id="c497a-391">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="c497a-392">**IPv4** アドレスをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="c497a-392">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="c497a-393">次に、[ **設定** ] に戻り、 **開発者向けの & セキュリティ > を更新** します。</span><span class="sxs-lookup"><span data-stu-id="c497a-393">Next, navigate back to **Settings** , and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="c497a-394">開発者モードをに設定します。</span><span class="sxs-lookup"><span data-stu-id="c497a-394">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="c497a-395">新しい Unity ビルド ( *アプリ* フォルダー) に移動し、 *Visual Studio* でソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="c497a-395">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio* .</span></span>
3.  <span data-ttu-id="c497a-396">ソリューション構成で、[ **デバッグ** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c497a-396">In the Solution Configuration select **Debug** .</span></span>
4.  <span data-ttu-id="c497a-397">ソリューションプラットフォームで、[ **x86** 、 **リモートコンピューター** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="c497a-397">In the Solution Platform, select **x86** , **Remote Machine** .</span></span> 

    ![ソリューション構成の変更](images/AzureLabs-Lab4-26.png)
 
5.  <span data-ttu-id="c497a-399">[ **ビルド] メニュー** の [ソリューションの **配置** ] をクリックして、アプリケーションを HoloLens にサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="c497a-399">Go to the **Build menu** and click on **Deploy Solution** , to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="c497a-400">アプリが HoloLens にインストールされているアプリの一覧に表示され、起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="c497a-400">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="c497a-401">イマーシブヘッドセットにデプロイするには **、ソリューションプラットフォーム** を *ローカルコンピューター* に設定し、 **プラットフォーム** として *x86* を使用して、 **構成** を [ *デバッグ* ] に設定します。</span><span class="sxs-lookup"><span data-stu-id="c497a-401">To deploy to immersive headset, set the **Solution Platform** to *Local Machine* , and set the **Configuration** to *Debug* , with *x86* as the **Platform** .</span></span> <span data-ttu-id="c497a-402">次に、[ **ビルド] メニュー** の [ *ソリューションの配置* ] をクリックして、ローカルコンピューターに配置します。</span><span class="sxs-lookup"><span data-stu-id="c497a-402">Then deploy to the local machine, using the **Build menu** , selecting *Deploy Solution* .</span></span> 


## <a name="chapter-10---using-the-application"></a><span data-ttu-id="c497a-403">章 10-アプリケーションの使用</span><span class="sxs-lookup"><span data-stu-id="c497a-403">Chapter 10 - Using the application</span></span>

1.  <span data-ttu-id="c497a-404">HoloLens を装着し、アプリを起動します。</span><span class="sxs-lookup"><span data-stu-id="c497a-404">Wearing the HoloLens, launch the app.</span></span>
2.  <span data-ttu-id="c497a-405">*Face API* に登録したユーザーを確認します。</span><span class="sxs-lookup"><span data-stu-id="c497a-405">Look at the person that you have registered with the *Face API* .</span></span> <span data-ttu-id="c497a-406">次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c497a-406">Make sure that:</span></span>

    -  <span data-ttu-id="c497a-407">人の顔は遠くすぎて明確に見えません。</span><span class="sxs-lookup"><span data-stu-id="c497a-407">The person's face is not too distant and clearly visible</span></span>
    -  <span data-ttu-id="c497a-408">環境の光源が暗すぎません</span><span class="sxs-lookup"><span data-stu-id="c497a-408">The environment lighting is not too dark</span></span>

3.  <span data-ttu-id="c497a-409">Tap ジェスチャを使用して、人物の写真をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="c497a-409">Use the tap gesture to capture the person's picture.</span></span>
4.  <span data-ttu-id="c497a-410">アプリが分析要求を送信し、応答を受信するまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="c497a-410">Wait for the App to send the analysis request and receive a response.</span></span>
5.  <span data-ttu-id="c497a-411">人が正常に認識された場合、ユーザー名は UI テキストとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="c497a-411">If the person has been successfully recognized, the person's name will appear as UI text.</span></span>
6.  <span data-ttu-id="c497a-412">数秒ごとに tap ジェスチャを使用して、キャプチャプロセスを繰り返すことができます。</span><span class="sxs-lookup"><span data-stu-id="c497a-412">You can repeat the capture process using the tap gesture every few seconds.</span></span>

## <a name="your-finished-azure-face-api-application"></a><span data-ttu-id="c497a-413">完成した Azure Face API アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c497a-413">Your finished Azure Face API Application</span></span>

<span data-ttu-id="c497a-414">これで、Azure Face 認識サービスを活用してイメージ内の顔を検出し、既知の顔を識別する、mixed reality アプリを構築しました。</span><span class="sxs-lookup"><span data-stu-id="c497a-414">Congratulations, you built a mixed reality app that leverages the Azure Face Recognition service to detect faces within an image, and identify any known faces.</span></span>

![このコースの完了の結果](images/AzureLabs-Lab4-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="c497a-416">ボーナス演習</span><span class="sxs-lookup"><span data-stu-id="c497a-416">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="c497a-417">演習1</span><span class="sxs-lookup"><span data-stu-id="c497a-417">Exercise 1</span></span>

<span data-ttu-id="c497a-418">**Azure Face API** は、1つのイメージで最大64の顔を検出するのに十分な性能を備えています。</span><span class="sxs-lookup"><span data-stu-id="c497a-418">The **Azure Face API** is powerful enough to detect up to 64 faces in a single image.</span></span> <span data-ttu-id="c497a-419">アプリケーションを拡張して、他の多くの人の間で2つまたは3つの顔を認識できるようにします。</span><span class="sxs-lookup"><span data-stu-id="c497a-419">Extend the application, so that it could recognize two or three faces, amongst many other people.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="c497a-420">演習2</span><span class="sxs-lookup"><span data-stu-id="c497a-420">Exercise 2</span></span>

<span data-ttu-id="c497a-421">**Azure Face API** では、すべての種類の属性情報を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="c497a-421">The **Azure Face API** is also able to provide back all kinds of attribute information.</span></span> <span data-ttu-id="c497a-422">これをアプリケーションに統合します。</span><span class="sxs-lookup"><span data-stu-id="c497a-422">Integrate this into the application.</span></span> <span data-ttu-id="c497a-423">これは、 [Emotion API](https://azure.microsoft.com/services/cognitive-services/emotion/)と組み合わせると、さらに興味深いものになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c497a-423">This could be even more interesting, when combined with the [Emotion API](https://azure.microsoft.com/services/cognitive-services/emotion/).</span></span>
