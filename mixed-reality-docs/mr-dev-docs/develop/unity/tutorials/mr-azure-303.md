---
title: MR と Azure 303-自然言語の理解 (LUIS)
description: このコースでは、mixed reality アプリケーション内に Azure Language Understanding インテリジェンスサービス (LUIS) を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, 言語を理解するインテリジェンスサービス, luis, hololens, イマーシブ, vr
ms.openlocfilehash: 8477f326de55c11f1c4d17d808a815f01366be0d
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2020
ms.locfileid: "91688058"
---
# <a name="mr-and-azure-303-natural-language-understanding-luis"></a><span data-ttu-id="67397-104">MR と Azure 303: 自然言語について (LUIS)</span><span class="sxs-lookup"><span data-stu-id="67397-104">MR and Azure 303: Natural language understanding (LUIS)</span></span>

<br>

>[!NOTE]
><span data-ttu-id="67397-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="67397-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="67397-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="67397-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="67397-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは " **_ありません_** "。</span><span class="sxs-lookup"><span data-stu-id="67397-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="67397-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="67397-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="67397-109">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="67397-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="67397-110">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="67397-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

<span data-ttu-id="67397-111">このコースでは、Language Understanding を Azure Cognitive Services を使用する mixed reality アプリケーションに Language Understanding API と統合する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="67397-111">In this course, you will learn how to integrate Language Understanding into a mixed reality application using Azure Cognitive Services, with the Language Understanding API.</span></span>

![ラボの結果](images/AzureLabs-Lab3-000.png)

<span data-ttu-id="67397-113">*Language Understanding (LUIS)* は Microsoft Azure サービスです。これにより、アプリケーションは、ユーザーが必要とするものを抽出するなどして、ユーザーの入力を除外することができます。</span><span class="sxs-lookup"><span data-stu-id="67397-113">*Language Understanding (LUIS)* is a Microsoft Azure service, which provides applications with the ability to make meaning out of user input, such as through extracting what a person might want, in their own words.</span></span> <span data-ttu-id="67397-114">これは機械学習を通じて実現されます。 machine learning では、入力情報を認識して学習した後、詳細な関連情報を返信できます。</span><span class="sxs-lookup"><span data-stu-id="67397-114">This is achieved through machine learning, which understands and learns the input information, and then can reply with detailed, relevant, information.</span></span> <span data-ttu-id="67397-115">詳細については、 [Azure Language Understanding (LUIS) のページ](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67397-115">For more information, visit the [Azure Language Understanding (LUIS) page](https://azure.microsoft.com/services/cognitive-services/language-understanding-intelligent-service/).</span></span>

<span data-ttu-id="67397-116">このコースを完了すると、現実のイマーシブヘッドセットアプリケーションが完成し、次のことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="67397-116">Having completed this course, you will have a mixed reality immersive headset application which will be able to do the following:</span></span>

1.  <span data-ttu-id="67397-117">イマーシブヘッドセットに接続されているマイクを使用して、ユーザー入力音声をキャプチャします。</span><span class="sxs-lookup"><span data-stu-id="67397-117">Capture user input speech, using the Microphone attached to the immersive headset.</span></span> 
2.  <span data-ttu-id="67397-118">キャプチャしたディクテーションを *Azure Language Understanding Intelligent Service* ( *LUIS* ) に送信します。</span><span class="sxs-lookup"><span data-stu-id="67397-118">Send the captured dictation the *Azure Language Understanding Intelligent Service* ( *LUIS* ).</span></span> 
3.  <span data-ttu-id="67397-119">LUIS では、送信情報から意味を抽出して分析し、ユーザーの要求の意図を判断しようとします。</span><span class="sxs-lookup"><span data-stu-id="67397-119">Have LUIS extract meaning from the send information, which will be analyzed, and attempt to determine the intent of the user’s request will be made.</span></span>

<span data-ttu-id="67397-120">開発には、ユーザーが音声や宝石を使用してシーン内のオブジェクトのサイズと色を変更できるアプリの作成が含まれます。</span><span class="sxs-lookup"><span data-stu-id="67397-120">Development will include the creation of an app where the user will be able to use voice and/or gaze to change the size and the color of the objects in the scene.</span></span> <span data-ttu-id="67397-121">モーションコントローラーの使用については説明しません。</span><span class="sxs-lookup"><span data-stu-id="67397-121">The use of motion controllers will not be covered.</span></span>

<span data-ttu-id="67397-122">アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。</span><span class="sxs-lookup"><span data-stu-id="67397-122">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="67397-123">このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="67397-123">This course is designed to teach you how to integrate an Azure Service with your Unity Project.</span></span> <span data-ttu-id="67397-124">このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。</span><span class="sxs-lookup"><span data-stu-id="67397-124">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

<span data-ttu-id="67397-125">LUIS を複数回トレーニングできるように準備します。これについては、 [12 章](#chapter-12--improving-your-luis-service)で説明します。</span><span class="sxs-lookup"><span data-stu-id="67397-125">Be prepared to Train LUIS several times, which is covered in [Chapter 12](#chapter-12--improving-your-luis-service).</span></span> <span data-ttu-id="67397-126">LUIS がトレーニングされると、より多くの結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="67397-126">You will get better results the more times LUIS has been trained.</span></span>

## <a name="device-support"></a><span data-ttu-id="67397-127">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="67397-127">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="67397-128">コース</span><span class="sxs-lookup"><span data-stu-id="67397-128">Course</span></span></th><th style="width:150px"> <span data-ttu-id="67397-129"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="67397-129"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="67397-130"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="67397-130"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td><span data-ttu-id="67397-131">MR と Azure 303: 自然言語について (LUIS)</span><span class="sxs-lookup"><span data-stu-id="67397-131">MR and Azure 303: Natural language understanding (LUIS)</span></span></td><td style="text-align: center;"> <span data-ttu-id="67397-132">✔️</span><span class="sxs-lookup"><span data-stu-id="67397-132">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="67397-133">✔️</span><span class="sxs-lookup"><span data-stu-id="67397-133">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="67397-134">このコースでは主に Windows Mixed Reality イマーシブ (VR) ヘッドセットに焦点を当てていますが、このコースで学習した内容を Microsoft HoloLens に適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="67397-134">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="67397-135">このコースに従うと、HoloLens をサポートするために必要となる可能性のある変更に関する注意事項が表示されます。</span><span class="sxs-lookup"><span data-stu-id="67397-135">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="67397-136">HoloLens を使用する場合、音声キャプチャ中にエコーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="67397-136">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="67397-137">前提条件</span><span class="sxs-lookup"><span data-stu-id="67397-137">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="67397-138">このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="67397-138">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="67397-139">また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証されたものを表します (2018 年5月)。</span><span class="sxs-lookup"><span data-stu-id="67397-139">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="67397-140">「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものよりも新しいソフトウェアで見つかったものと完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="67397-140">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="67397-141">このコースでは、次のハードウェアとソフトウェアをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="67397-141">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="67397-142">開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="67397-142">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="67397-143">開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="67397-143">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md)
- [<span data-ttu-id="67397-144">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="67397-144">The latest Windows 10 SDK</span></span>](../../install-the-tools.md)
- [<span data-ttu-id="67397-145">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="67397-145">Unity 2017.4</span></span>](../../install-the-tools.md)
- [<span data-ttu-id="67397-146">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="67397-146">Visual Studio 2017</span></span>](../../install-the-tools.md)
- <span data-ttu-id="67397-147">[Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](../../../hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="67397-147">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](../../../hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="67397-148">内蔵マイク付きヘッドホンのセット (ヘッドセットにマイクとスピーカーが組み込まれていない場合)</span><span class="sxs-lookup"><span data-stu-id="67397-148">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="67397-149">Azure のセットアップと LUIS の取得のためのインターネットアクセス</span><span class="sxs-lookup"><span data-stu-id="67397-149">Internet access for Azure setup and LUIS retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="67397-150">開始する前に</span><span class="sxs-lookup"><span data-stu-id="67397-150">Before you start</span></span>

1.  <span data-ttu-id="67397-151">このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="67397-151">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span> 
2.  <span data-ttu-id="67397-152">コンピューターがディクテーションを有効にできるようにするには、[ **Windows の設定] > [プライバシー > 音声、インク & 入力** し、[ **音声サービスの有効化** ] をクリックして、[候補] を入力します。</span><span class="sxs-lookup"><span data-stu-id="67397-152">To allow your machine to enable Dictation, go to **Windows Settings > Privacy > Speech, Inking & Typing** and press on the button **Turn On speech services and typing suggestions** .</span></span>
3.  <span data-ttu-id="67397-153">このチュートリアルのコードを使用すると、コンピューターに設定されている **既定のマイクデバイス** から記録できます。</span><span class="sxs-lookup"><span data-stu-id="67397-153">The code in this tutorial will allow you to record from the **Default Microphone Device** set on your machine.</span></span> <span data-ttu-id="67397-154">既定のマイクデバイスが、音声をキャプチャするために使用するものとして設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="67397-154">Make sure the Default Microphone Device is set as the one you wish to use to capture your voice.</span></span>
4.  <span data-ttu-id="67397-155">ヘッドセットにマイクが内蔵されている場合は、 *Mixed Reality ポータル* の設定で *"ヘッドセットを磨耗したときにヘッドセットの mic に切り替える"* オプションがオンになっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="67397-155">If your headset has a built-in microphone, make sure the option *“When I wear my headset, switch to headset mic”* is turned on in the *Mixed Reality Portal* settings.</span></span>

    ![イマーシブヘッドセットの設定](images/AzureLabs-Lab3-00.png)

## <a name="chapter-1--setup-azure-portal"></a><span data-ttu-id="67397-157">第1章: Azure Portal のセットアップ</span><span class="sxs-lookup"><span data-stu-id="67397-157">Chapter 1 – Setup Azure Portal</span></span>

<span data-ttu-id="67397-158">Azure で *Language Understanding* サービスを使用するには、アプリケーションで使用できるようにサービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-158">To use the *Language Understanding* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="67397-159">[Azure Portal](https://portal.azure.com) にログインします。</span><span class="sxs-lookup"><span data-stu-id="67397-159">Log in to the [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="67397-160">まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="67397-161">このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。</span><span class="sxs-lookup"><span data-stu-id="67397-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="67397-162">ログインしたら、左上隅にある [ **新規** ] をクリックし、 *Language Understanding* を検索して、 **Enter キー** を押します。</span><span class="sxs-lookup"><span data-stu-id="67397-162">Once you are logged in, click on **New** in the top left corner, and search for *Language Understanding* , and click **Enter** .</span></span> 

    ![LUIS リソースの作成](images/AzureLabs-Lab3-01.png)

    > [!NOTE]
    > <span data-ttu-id="67397-164">新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="67397-164">The word **New** may have been replaced with **Create a resource** , in newer portals.</span></span>
 
3.  <span data-ttu-id="67397-165">右側の新しいページには、Language Understanding サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="67397-165">The new page to the right will provide a description of the Language Understanding service.</span></span> <span data-ttu-id="67397-166">このページの左下にある [ **作成** ] ボタンを選択して、このサービスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="67397-166">At the bottom left of this page, select the **Create** button, to create an instance of this service.</span></span>

    ![LUIS サービスの作成-法的通知](images/AzureLabs-Lab3-02.png)
 
4.  <span data-ttu-id="67397-168">[作成:</span><span class="sxs-lookup"><span data-stu-id="67397-168">Once you have clicked on Create:</span></span>

    1. <span data-ttu-id="67397-169">このサービスインスタンスに必要な **名前** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="67397-169">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="67397-170">**サブスクリプション** を選択します。</span><span class="sxs-lookup"><span data-stu-id="67397-170">Select a **Subscription** .</span></span>
    3. <span data-ttu-id="67397-171">適切な **価格レベル** を選択します。これが *LUIS サービス* を初めて作成する場合は、free レベル (F0) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="67397-171">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *LUIS Service* , a free tier (named F0) should be available to you.</span></span> <span data-ttu-id="67397-172">このコースでは、無料の割り当ては十分ではありません。</span><span class="sxs-lookup"><span data-stu-id="67397-172">The free allocation should be more than sufficient for this course.</span></span>
    4. <span data-ttu-id="67397-173">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="67397-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="67397-174">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="67397-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="67397-175">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="67397-175">It is recommended to keep all the Azure services associated with a single project (e.g. such as these courses) under a common resource group).</span></span> 

        > <span data-ttu-id="67397-176">Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="67397-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="67397-177">リソースグループの **場所** を決定します (新しいリソースグループを作成している場合)。</span><span class="sxs-lookup"><span data-stu-id="67397-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="67397-178">この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="67397-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="67397-179">一部の Azure 資産は、特定のリージョンでのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="67397-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="67397-180">また、このサービスに適用されている使用条件を理解していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="67397-181">**［作成］** を選択します</span><span class="sxs-lookup"><span data-stu-id="67397-181">Select **Create** .</span></span>

        ![Create LUIS service-ユーザー入力](images/AzureLabs-Lab3-03.png)
 
5.  <span data-ttu-id="67397-183">[ **作成** ] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="67397-183">Once you have clicked on **Create** , you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="67397-184">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="67397-184">A notification will appear in the portal once the Service instance is created.</span></span> 
 
    ![新しい Azure 通知イメージ](images/AzureLabs-Lab3-04.png)

7.  <span data-ttu-id="67397-186">通知をクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="67397-186">Click on the notification to explore your new Service instance.</span></span>

    ![リソース作成の成功通知](images/AzureLabs-Lab3-05.png)
 
8.  <span data-ttu-id="67397-188">通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="67397-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="67397-189">新しい LUIS サービスインスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="67397-189">You will be taken to your new LUIS service instance.</span></span> 
 
    ![LUIS キーへのアクセス](images/AzureLabs-Lab3-06.png)

9.  <span data-ttu-id="67397-191">このチュートリアルでは、アプリケーションがサービスの呼び出しを行う必要があります。サービスは、サービスのサブスクリプションキーを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="67397-191">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="67397-192">*LUIS API* サービスの [ *クイックスタート* ] ページで、最初の手順に移動し、 *キーを取得* して、[ **キー** ] をクリックします (これを行うには、[サービス] ナビゲーションメニューにある、キーアイコンで示されている青いハイパーリンクキーをクリックします)。</span><span class="sxs-lookup"><span data-stu-id="67397-192">From the *Quick start* page, of your *LUIS API* service, navigate to the first step, *Grab your keys* , and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="67397-193">これにより、サービス *キー* が表示されます。</span><span class="sxs-lookup"><span data-stu-id="67397-193">This will reveal your service *Keys* .</span></span>
11. <span data-ttu-id="67397-194">表示されているキーの1つをコピーします。これは、プロジェクトの後半で必要になります。</span><span class="sxs-lookup"><span data-stu-id="67397-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 
12. <span data-ttu-id="67397-195">[ *サービス* ] ページで、[ *Language Understanding ポータル* ] をクリックして、LUIS アプリ内で新しいサービスの作成に使用する web ページにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="67397-195">In the *Service* page, click on *Language Understanding Portal* to be redirected to the webpage which you will use to create your new Service, within the LUIS App.</span></span> 

## <a name="chapter-2--the-language-understanding-portal"></a><span data-ttu-id="67397-196">第2章: Language Understanding ポータル</span><span class="sxs-lookup"><span data-stu-id="67397-196">Chapter 2 – The Language Understanding Portal</span></span>

<span data-ttu-id="67397-197">このセクションでは、LUIS ポータルで LUIS アプリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="67397-197">In this section you will learn how to make a LUIS App on the LUIS Portal.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="67397-198">この章内で *エンティティ* 、 *インテント* 、および *発話* を設定することは、LUIS サービスを構築するための最初の手順であることに注意してください。サービスを再トレーニングして、より正確なものにする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="67397-198">Please be aware, that setting up the *Entities* , *Intents* , and *Utterances* within this chapter is only the first step in building your LUIS service: you will also need to retrain the service, several times, so to make it more accurate.</span></span> <span data-ttu-id="67397-199">サービスの再トレーニングについては、このコースの [最後の章](#chapter-12--improving-your-luis-service) で説明されているため、完了していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="67397-199">Retraining your service is covered in the [last Chapter](#chapter-12--improving-your-luis-service) of this course, so ensure that you complete it.</span></span>

1.  <span data-ttu-id="67397-200">*Language Understanding ポータル* に達したら、Azure portal と同じ資格情報を使用してログインする必要がある場合があります (まだログインしていない場合)。</span><span class="sxs-lookup"><span data-stu-id="67397-200">Upon reaching the *Language Understanding Portal* , you may need to login, if you are not already, with the same credentials as your Azure portal.</span></span> 

    ![LUIS ログインページ](images/AzureLabs-Lab3-07.png)
 
2.  <span data-ttu-id="67397-202">LUIS を初めて使用する場合は、[ようこそ] ページの一番下までスクロールして [ **CREATE LUIS app (アプリの作成** )] ボタンを見つけてクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-202">If this is your first time using LUIS, you will need to scroll down to the bottom of the welcome page, to find and click on the **Create LUIS app** button.</span></span>

    ![LUIS アプリの作成ページ](images/AzureLabs-Lab3-08.png)
 
3.  <span data-ttu-id="67397-204">ログインしたら、[ **マイアプリ** ] をクリックします (現在このセクションにない場合)。</span><span class="sxs-lookup"><span data-stu-id="67397-204">Once logged in, click **My apps** (if you are not in that section currently).</span></span> <span data-ttu-id="67397-205">[ **新しいアプリの作成** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-205">You can then click on **Create new app** .</span></span>

    ![LUIS-マイアプリのイメージ](images/AzureLabs-Lab3-09.png)
 
4.  <span data-ttu-id="67397-207">アプリに *名前* を付けます。</span><span class="sxs-lookup"><span data-stu-id="67397-207">Give your app a *Name* .</span></span>
5.  <span data-ttu-id="67397-208">アプリが英語とは異なる言語を認識する場合は、 *カルチャ* を適切な言語に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-208">If your app is supposed to understand a language different from English, you should change the *Culture* to the appropriate language.</span></span>
6.  <span data-ttu-id="67397-209">ここでは、新しい LUIS アプリの *説明* を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="67397-209">Here you can also add a *Description* of your new LUIS app.</span></span>

    ![LUIS-新しいアプリを作成する](images/AzureLabs-Lab3-10.png)

7.  <span data-ttu-id="67397-211">[ **完了** ] をクリックすると、新しい *LUIS* アプリケーションの [ *ビルド* ] ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="67397-211">Once you press **Done** , you will enter the *Build* page of your new *LUIS* application.</span></span>
8.  <span data-ttu-id="67397-212">ここで理解しておくべき重要な概念がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="67397-212">There are a few important concepts to understand here:</span></span>

    -   <span data-ttu-id="67397-213">*インテント* は、ユーザーからのクエリに従って呼び出されるメソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="67397-213">*Intent* , represents the method that will be called following a query from the user.</span></span> <span data-ttu-id="67397-214">*インテント* には、1つまたは複数の *エンティティ* を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="67397-214">An *INTENT* may have one or more *ENTITIES* .</span></span>
    -   <span data-ttu-id="67397-215">*エンティティ* は、 *インテント* に関連する情報を記述するクエリのコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="67397-215">*Entity* , is a component of the query that describes information relevant to the *INTENT* .</span></span>
    -   <span data-ttu-id="67397-216">*発話* は、開発者によって提供されるクエリの例であり、LUIS は自身をトレーニングするために使用します。</span><span class="sxs-lookup"><span data-stu-id="67397-216">*Utterances* , are examples of queries provided by the developer, that LUIS will use to train itself.</span></span>

<span data-ttu-id="67397-217">これらの概念が完全に明確でない場合は、心配しないでください。この章ではさらに詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="67397-217">If these concepts are not perfectly clear, do not worry, as this course will clarify them further in this chapter.</span></span>

<span data-ttu-id="67397-218">最初に、このコースを構築するために必要な *エンティティ* を作成します。</span><span class="sxs-lookup"><span data-stu-id="67397-218">You will begin by creating the *Entities* needed to build this course.</span></span>

9.  <span data-ttu-id="67397-219">ページの左側にある [ *エンティティ* ] をクリックし、[ **新しいエンティティの作成** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-219">On the left side of the page, click on *Entities* , then click on **Create new entity** .</span></span>

    ![新しいエンティティの作成](images/AzureLabs-Lab3-11.png)

10. <span data-ttu-id="67397-221">新しいエンティティの *色* を呼び出し、その種類を *Simple* に設定して、[ **完了** ] を押します。</span><span class="sxs-lookup"><span data-stu-id="67397-221">Call the new Entity *color* , set its type to *Simple* , then press **Done** .</span></span>

    ![単純なエンティティの作成-色](images/AzureLabs-Lab3-12.png)
 
11. <span data-ttu-id="67397-223">このプロセスを繰り返して、次の3つの単純なエンティティを作成します。</span><span class="sxs-lookup"><span data-stu-id="67397-223">Repeat this process to create three (3) more Simple Entities named:</span></span>

    -   <span data-ttu-id="67397-224">*まま*</span><span class="sxs-lookup"><span data-stu-id="67397-224">*upsize*</span></span>
    -   <span data-ttu-id="67397-225">*ダウンサイズ*</span><span class="sxs-lookup"><span data-stu-id="67397-225">*downsize*</span></span>
    -   <span data-ttu-id="67397-226">*target*</span><span class="sxs-lookup"><span data-stu-id="67397-226">*target*</span></span>

<span data-ttu-id="67397-227">結果は次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="67397-227">The result should look like the image below:</span></span>

![エンティティ作成の結果](images/AzureLabs-Lab3-13.png)
 
<span data-ttu-id="67397-229">この時点で、 *インテント* の作成を開始できます。</span><span class="sxs-lookup"><span data-stu-id="67397-229">At this point you can begin creating *Intents* .</span></span> 

> [!WARNING]
> <span data-ttu-id="67397-230">インテントを削除しない **でください** 。</span><span class="sxs-lookup"><span data-stu-id="67397-230">Do not delete the **None** intent.</span></span>

12. <span data-ttu-id="67397-231">ページの左側にある [ **インテント** ] をクリックし、[ **新しいインテントの作成** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-231">On the left side of the page, click on **Intents** , then click on **Create new intent** .</span></span>

    ![新しいインテントの作成](images/AzureLabs-Lab3-14.png)

13. <span data-ttu-id="67397-233">新しい *インテント* **changeobjectcolor** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="67397-233">Call the new *Intent* **ChangeObjectColor** .</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="67397-234">この *意図* 名は、このコースの後半でコード内で使用されます。したがって、最適な結果を得るために、この名前を指定されたとおりに使用してください。</span><span class="sxs-lookup"><span data-stu-id="67397-234">This *Intent* name is used within the code later in this course, so for best results, use this name exactly as provided.</span></span>

<span data-ttu-id="67397-235">名前を確認すると、インテントページにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="67397-235">Once you confirm the name you will be directed to the Intents Page.</span></span>

![LUIS ページ](images/AzureLabs-Lab3-15.png)

<span data-ttu-id="67397-237">5つ以上の異なる *発話* を入力するよう求めるテキストボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="67397-237">You will notice that there is a textbox asking you to type 5 or more different *Utterances* .</span></span>

> [!NOTE]
> <span data-ttu-id="67397-238">LUIS は、すべての発話を小文字に変換します。</span><span class="sxs-lookup"><span data-stu-id="67397-238">LUIS converts all Utterances to lower case.</span></span>

14. <span data-ttu-id="67397-239">上部のテキストボックスに次の *(発話)* を挿入します (現在、テキストの *種類は約5例です)。*</span><span class="sxs-lookup"><span data-stu-id="67397-239">Insert the following *Utterance* in the top textbox (currently with the text *Type about 5 examples…*</span></span> <span data-ttu-id="67397-240">) を **入力** し、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="67397-240">), and press **Enter** :</span></span>

```
The color of the cylinder must be red
```

<span data-ttu-id="67397-241">新しい *(発話)* は、の下の一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="67397-241">You will notice that the new *Utterance* will appear in a list underneath.</span></span>

<span data-ttu-id="67397-242">同じプロセスに従って、次の6つの発話を挿入します。</span><span class="sxs-lookup"><span data-stu-id="67397-242">Following the same process, insert the following six (6) Utterances:</span></span>

```
make the cube black

make the cylinder color white

change the sphere to red

change it to green

make this yellow

change the color of this object to blue
```

<span data-ttu-id="67397-243">作成した各 (発話) に対して、LUIS がエンティティとして使用する単語を識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-243">For each Utterance you have created, you must identify which words should be used by LUIS as Entities.</span></span> <span data-ttu-id="67397-244">この例では、すべての色に *色* エンティティとしてラベルを付け、 *ターゲットエンティティとしてターゲットに* 使用できるすべての参照を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-244">In this example you need to label all the colors as a *color* Entity, and all the possible reference to a target as a *target* Entity.</span></span>

15. <span data-ttu-id="67397-245">これを行うには、最初の (発話) の " *シリンダー* " をクリックし、[ *ターゲット* ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="67397-245">To do so, try clicking on the word *cylinder* in the first Utterance and select *target* .</span></span>

    ![(発話) ターゲットの識別](images/AzureLabs-Lab3-16.png)
 
16. <span data-ttu-id="67397-247">次に、最初の (発話) の " *red* " という語をクリックして、[ *色* ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="67397-247">Now click on the word *red* in the first Utterance and select *color* .</span></span>

    ![(発話) エンティティの識別](images/AzureLabs-Lab3-17.png)
 
17. <span data-ttu-id="67397-249">次の行にラベルを付けます。ここで、 *キューブ* は *ターゲット* にする必要があり、 *黒* は *色* にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-249">Label the next line also, where *cube* should be a *target* , and *black* should be a *color* .</span></span> <span data-ttu-id="67397-250">また、" *this"* 、 *"it"* 、および *"this object"* という単語を使用しています。これにより、指定されていないターゲット型も使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="67397-250">Notice also the use of the words *‘this’* , *‘it’* , and *‘this object’* , which we are providing, so to have non-specific target types available also.</span></span> 

18. <span data-ttu-id="67397-251">すべての発話がラベル付きのエンティティを持つようになるまで、上記の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="67397-251">Repeat the process above until all the Utterances have the Entities labelled.</span></span> <span data-ttu-id="67397-252">ヘルプが必要な場合は、次の画像を参照してください。</span><span class="sxs-lookup"><span data-stu-id="67397-252">See the below image if you need help.</span></span>

    > [!TIP]
    > <span data-ttu-id="67397-253">エンティティ ラベルを付ける単語を選択するときは:</span><span class="sxs-lookup"><span data-stu-id="67397-253">When selecting words to label them as entities:</span></span>
    > - <span data-ttu-id="67397-254">単一の単語の場合は、単にクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-254">For single words just click them.</span></span>
    > - <span data-ttu-id="67397-255">2つ以上の単語のセットについては、セットの先頭と末尾にあるをクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-255">For a set of two or more words, click at the beginning and then at the end of the set.</span></span>

    > [!NOTE]
    > <span data-ttu-id="67397-256">[ *トークンビュー* ] トグルボタンを使用して、 **エンティティ/トークンビュー** を切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="67397-256">You can use the *Tokens View* toggle button to switch between **Entities / Tokens View** !</span></span>

19. <span data-ttu-id="67397-257">次の図に示すように結果が表示され、 **エンティティ/トークンビュー** が表示されます。</span><span class="sxs-lookup"><span data-stu-id="67397-257">The results should be as seen in the images below, showing the **Entities / Tokens View** :</span></span>

    ![トークン & エンティティビュー](images/AzureLabs-Lab3-18.png)
  
20. <span data-ttu-id="67397-259">この時点で、ページの右上にある [ **Train** ] ボタンをクリックして、小さなラウンドインジケーターが緑色になるまで待ちます。</span><span class="sxs-lookup"><span data-stu-id="67397-259">At this point press the **Train** button at the top-right of the page and wait for the small round indicator on it to turn green.</span></span> <span data-ttu-id="67397-260">これは、この目的を認識するために LUIS が正常にトレーニングされたことを示します。</span><span class="sxs-lookup"><span data-stu-id="67397-260">This indicates that LUIS has been successfully trained to recognize this Intent.</span></span>

    ![LUIS のトレーニング](images/AzureLabs-Lab3-19.png)
 
21. <span data-ttu-id="67397-262">この演習では、 *target* 、 *アップ* サイズ、および *ダウンサイズ* エンティティを使用して、 **changeobjectsize** という新しいインテントを作成します。</span><span class="sxs-lookup"><span data-stu-id="67397-262">As an exercise for you, create a new Intent called **ChangeObjectSize** , using the Entities *target* , *upsize* , and *downsize* .</span></span>
22. <span data-ttu-id="67397-263">前の意図と同じプロセスに従って、 *サイズ* を変更するために、次の8つの発話を挿入します。</span><span class="sxs-lookup"><span data-stu-id="67397-263">Following the same process as the previous Intent, insert the following eight (8) Utterances for *Size* change:</span></span>

    ```
    increase the dimensions of that

    reduce the size of this

    i want the sphere smaller

    make the cylinder bigger

    size down the sphere

    size up the cube

    decrease the size of that object

    increase the size of this object
    ```

23. <span data-ttu-id="67397-264">結果は次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="67397-264">The result should be like the one in the image below:</span></span>

    ![ChangeObjectSize トークン/エンティティの設定](images/AzureLabs-Lab3-20.png) 

24. <span data-ttu-id="67397-266">**Changeobjectcolor** と **changeobjectcolor** の両方の作成とトレーニングが完了したら、ページの上部にある [ **発行** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-266">Once both Intents, **ChangeObjectColor** and **ChangeObjectSize** , have been created and trained, click on the **PUBLISH** button on top of the page.</span></span>

    ![LUIS サービスの発行](images/AzureLabs-Lab3-21.png)

25. <span data-ttu-id="67397-268">[ *発行* ] ページで、LUIS アプリを完成させ、コードからアクセスできるように発行します。</span><span class="sxs-lookup"><span data-stu-id="67397-268">On the *Publish* page you will finalize and publish your LUIS App so that it can be accessed by your code.</span></span>

    1. <span data-ttu-id="67397-269">ドロップダウンを [ **運用環境** ] *に* 設定します。</span><span class="sxs-lookup"><span data-stu-id="67397-269">Set the drop down *Publish To* as **Production** .</span></span>
    2. <span data-ttu-id="67397-270">タイムゾーン *をタイム* ゾーンに設定します。</span><span class="sxs-lookup"><span data-stu-id="67397-270">Set the *Timezone* to your time zone.</span></span>
    3. <span data-ttu-id="67397-271">チェックボックスをオンにして、予測される **すべてのインテントスコアを含め** ます。</span><span class="sxs-lookup"><span data-stu-id="67397-271">Check the box **Include all predicted intent scores** .</span></span>
    4. <span data-ttu-id="67397-272">[ **運用スロットに発行** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-272">Click on **Publish to Production Slot** .</span></span>

        ![発行の設定](images/AzureLabs-Lab3-22.png)

26. <span data-ttu-id="67397-274">[ *リソースとキー* ] セクションで、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="67397-274">In the section *Resources and Keys* :</span></span>

    1.  <span data-ttu-id="67397-275">Azure Portal でサービスインスタンスに設定するリージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="67397-275">Select the region you set for service instance in the Azure Portal.</span></span>
    2.  <span data-ttu-id="67397-276">次の **Starter_Key** 要素があることがわかりますが、無視します。</span><span class="sxs-lookup"><span data-stu-id="67397-276">You will notice a **Starter_Key** element below, ignore it.</span></span>
    3.  <span data-ttu-id="67397-277">[ **キーの追加** ] をクリックし、サービスインスタンスを作成したときに Azure Portal で取得した *キー* を挿入します。</span><span class="sxs-lookup"><span data-stu-id="67397-277">Click on **Add Key** and insert the *Key* that you obtained in the Azure Portal when you created your Service instance.</span></span> <span data-ttu-id="67397-278">Azure と LUIS portal が同じユーザーにログインしている場合は、[ *テナント名* ]、[ *サブスクリプション名* ]、および使用する *キー* のドロップダウンメニューが表示されます (azure portal で以前に指定したものと同じ名前になります)。</span><span class="sxs-lookup"><span data-stu-id="67397-278">If your Azure and the LUIS portal are logged into the same user, you will be provided drop-down menus for *Tenant name* , *Subscription Name* , and the *Key* you wish to use (will have the same name as you provided previously in the Azure Portal.</span></span>

    > [!IMPORTANT] 
    > <span data-ttu-id="67397-279">*エンドポイント* の下で、挿入したキーに対応するエンドポイントのコピーを取得します。これは、すぐにコードで使用します。</span><span class="sxs-lookup"><span data-stu-id="67397-279">Underneath *Endpoint* , take a copy of the endpoint corresponding to the Key you have inserted, you will soon use it in your code.</span></span>
 
## <a name="chapter-3--set-up-the-unity-project"></a><span data-ttu-id="67397-280">第3章: Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="67397-280">Chapter 3 – Set up the Unity project</span></span>

<span data-ttu-id="67397-281">次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="67397-281">The following is a typical set up for developing with the mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="67397-282">*Unity* を開き、[ **新規** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-282">Open *Unity* and click **New** .</span></span> 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab3-24.png)

2.  <span data-ttu-id="67397-284">ここで、Unity プロジェクト名を指定し、 **MR_LUIS** を挿入する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-284">You will now need to provide a Unity Project name, insert **MR_LUIS** .</span></span> <span data-ttu-id="67397-285">プロジェクトの種類が **3d** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="67397-285">Make sure the project type is set to **3D** .</span></span> <span data-ttu-id="67397-286">場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="67397-286">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="67397-287">次に、[ **プロジェクトの作成** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-287">Then, click **Create project** .</span></span>

    ![新しい Unity プロジェクトの詳細を指定します。](images/AzureLabs-Lab3-25.png)
 
3.  <span data-ttu-id="67397-289">Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-289">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio** .</span></span> <span data-ttu-id="67397-290">[> の設定の編集] に移動し、新しいウィンドウで [ **外部ツール** ] に移動します。</span><span class="sxs-lookup"><span data-stu-id="67397-290">Go to Edit > Preferences and then from the new window, navigate to **External Tools** .</span></span> <span data-ttu-id="67397-291">**外部スクリプトエディター** を **Visual Studio 2017** に変更します。</span><span class="sxs-lookup"><span data-stu-id="67397-291">Change **External Script Editor** to **Visual Studio 2017** .</span></span> <span data-ttu-id="67397-292">[ **基本設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="67397-292">Close the **Preferences** window.</span></span>

    ![スクリプトエディターの設定を更新します。](images/AzureLabs-Lab3-26.png)
 
4.  <span data-ttu-id="67397-294">次に、[ **ファイル > ビルド設定** ] に移動し、[プラットフォームの **切り替え** ] ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="67397-294">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform** , by clicking on the **Switch Platform** button.</span></span>

    ![[ビルドの設定] ウィンドウで、[プラットフォーム] を [UWP] に切り替えます。](images/AzureLabs-Lab3-27.png)
 
5.  <span data-ttu-id="67397-296">[ **ファイル > ビルド設定** ] にアクセスし、次のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="67397-296">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="67397-297">**ターゲットデバイス** が **任意のデバイス** に設定されています</span><span class="sxs-lookup"><span data-stu-id="67397-297">**Target Device** is set to **Any Device**</span></span>

        > <span data-ttu-id="67397-298">Microsoft HoloLens の場合は、 **ターゲットデバイス** を *HoloLens* に設定します。</span><span class="sxs-lookup"><span data-stu-id="67397-298">For the Microsoft HoloLens, set **Target Device** to *HoloLens* .</span></span>

    2. <span data-ttu-id="67397-299">**ビルドの種類** が **D3D** に設定されています</span><span class="sxs-lookup"><span data-stu-id="67397-299">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="67397-300">**SDK** は最新の **インストール** に設定されています</span><span class="sxs-lookup"><span data-stu-id="67397-300">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="67397-301">**Visual Studio のバージョン** が、 **インストールされている最新** バージョンに設定されています</span><span class="sxs-lookup"><span data-stu-id="67397-301">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="67397-302">**ビルドと実行** は **ローカルコンピューター** に設定されています</span><span class="sxs-lookup"><span data-stu-id="67397-302">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="67397-303">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="67397-303">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="67397-304">これを行うには、[開いている **シーンの追加** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="67397-304">Do this by selecting **Add Open Scenes** .</span></span> <span data-ttu-id="67397-305">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="67397-305">A save window will appear.</span></span>
        
            ![[開いているシーンを追加] ボタンをクリックする](images/AzureLabs-Lab3-28.png)

        2. <span data-ttu-id="67397-307">この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン** 」にします。</span><span class="sxs-lookup"><span data-stu-id="67397-307">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes** .</span></span>

            ![新しいスクリプトフォルダーの作成](images/AzureLabs-Lab3-29.png)

        3. <span data-ttu-id="67397-309">新しく作成した [ **シーン** ] フォルダーを開き、[ *ファイル名* : テキスト] フィールドに「 **MR_LuisScene** 」と入力して、[ **保存** ] を押します。</span><span class="sxs-lookup"><span data-stu-id="67397-309">Open your newly created **Scenes** folder, and then in the *File name* : text field, type **MR_LuisScene** , then press **Save** .</span></span>

            ![新しいシーンに名前を付けます。](images/AzureLabs-Lab3-30.png)

    7. <span data-ttu-id="67397-311">それ以外の設定は、[ *ビルド設定* ] の [既定] のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="67397-311">The remaining settings, in *Build Settings* , should be left as default for now.</span></span>

6. <span data-ttu-id="67397-312">[ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="67397-312">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![プレーヤーの設定を開きます。](images/AzureLabs-Lab3-31.png) 
 
7. <span data-ttu-id="67397-314">このパネルでは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-314">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="67397-315">[ **その他の設定** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="67397-315">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="67397-316">**スクリプトランタイムのバージョン** は **安定** している必要があります (.net 3.5 と同等)。</span><span class="sxs-lookup"><span data-stu-id="67397-316">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="67397-317">**バックエンド** は **.net** である必要があります</span><span class="sxs-lookup"><span data-stu-id="67397-317">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="67397-318">**API 互換性レベル** は **.net 4.6** である必要があります</span><span class="sxs-lookup"><span data-stu-id="67397-318">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![その他の設定を更新します。](images/AzureLabs-Lab3-32.png)
      
    2. <span data-ttu-id="67397-320">[ **発行の設定** ] タブの [ **機能** ] で、次の項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="67397-320">Within the **Publishing Settings** tab, under **Capabilities** , check:</span></span>

        1. <span data-ttu-id="67397-321">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="67397-321">**InternetClient**</span></span>
        2. <span data-ttu-id="67397-322">**マイク**</span><span class="sxs-lookup"><span data-stu-id="67397-322">**Microphone**</span></span>

            ![発行設定を更新しています。](images/AzureLabs-Lab3-33.png)

    3. <span data-ttu-id="67397-324">パネルの下にある [ **XR settings** (発行の **設定** ] の下にあります) で、[ **サポートされている仮想現実** ] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="67397-324">Further down the panel, in **XR Settings** (found below **Publish Settings** ), tick **Virtual Reality Supported** , make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![X R の設定を更新します。](images/AzureLabs-Lab3-34.png)

8.  <span data-ttu-id="67397-326">*ビルド設定* に戻る _Unity C#_ プロジェクトはグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="67397-326">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="67397-327">[ビルド設定] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="67397-327">Close the Build Settings window.</span></span>
10. <span data-ttu-id="67397-328">シーンとプロジェクトを保存します ([ **ファイル] > [シーン/ファイルの保存] > [プロジェクトの保存** ])。</span><span class="sxs-lookup"><span data-stu-id="67397-328">Save your Scene and Project ( **FILE > SAVE SCENE / FILE > SAVE PROJECT** ).</span></span>

## <a name="chapter-4--create-the-scene"></a><span data-ttu-id="67397-329">章4–シーンを作成する</span><span class="sxs-lookup"><span data-stu-id="67397-329">Chapter 4 – Create the scene</span></span>

> [!IMPORTANT]
> <span data-ttu-id="67397-330">このコースの *Unity セットアップ* コンポーネントをスキップしてコードに直接進む場合は、 [unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage)をダウンロードし、 [カスタムパッケージ](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 [第5章](#chapter-5--create-the-microphonemanager-class)から続行してください。</span><span class="sxs-lookup"><span data-stu-id="67397-330">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20303%20-%20Natural%20language%20understanding/Azure-MR-303.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-microphonemanager-class).</span></span> 

1.  <span data-ttu-id="67397-331">[ *階層] パネル* の空の領域を右クリックし、[ **3d オブジェクト** ] の下に **平面** を追加します。</span><span class="sxs-lookup"><span data-stu-id="67397-331">Right-click in an empty area of the *Hierarchy Panel* , under **3D Object** , add a **Plane** .</span></span>

    ![平面を作成します。](images/AzureLabs-Lab3-35.png)

2.  <span data-ttu-id="67397-333">*階層* 内を右クリックしてさらにオブジェクトを作成した場合、最後のオブジェクトを選択したままにすると、選択したオブジェクトが新しいオブジェクトの親になります。</span><span class="sxs-lookup"><span data-stu-id="67397-333">Be aware that when you right-click within the *Hierarchy* again to create more objects, if you still have the last object selected, the selected object will be the parent of your new object.</span></span> <span data-ttu-id="67397-334">階層内の空いている領域を左クリックし、右クリックしてください。</span><span class="sxs-lookup"><span data-stu-id="67397-334">Avoid this left-clicking in an empty space within the Hierarchy, and then right-clicking.</span></span>

3.  <span data-ttu-id="67397-335">上記の手順を繰り返して、次のオブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="67397-335">Repeat the above procedure to add the following objects:</span></span>

    1. <span data-ttu-id="67397-336">*Sphere*</span><span class="sxs-lookup"><span data-stu-id="67397-336">*Sphere*</span></span>
    2. <span data-ttu-id="67397-337">*シリンダ*</span><span class="sxs-lookup"><span data-stu-id="67397-337">*Cylinder*</span></span>
    3. <span data-ttu-id="67397-338">*Cube*</span><span class="sxs-lookup"><span data-stu-id="67397-338">*Cube*</span></span>
    4. <span data-ttu-id="67397-339">*3D テキスト*</span><span class="sxs-lookup"><span data-stu-id="67397-339">*3D Text*</span></span>

4.  <span data-ttu-id="67397-340">結果として得られるシーン *階層* は、次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="67397-340">The resulting scene *Hierarchy* should be like the one in the image below:</span></span>

    ![シーン階層のセットアップ。](images/AzureLabs-Lab3-36.png)
 
5.  <span data-ttu-id="67397-342">**メインカメラ** をクリックして選択し、[ *インスペクター] パネル* で、すべてのコンポーネントを含むカメラオブジェクトを確認します。</span><span class="sxs-lookup"><span data-stu-id="67397-342">Left click on the **Main Camera** to select it, look at the *Inspector Panel* you will see the Camera object with all the its components.</span></span>
6.  <span data-ttu-id="67397-343">[ *インスペクター] パネル* の下部にある [ **コンポーネントの追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-343">Click on the **Add Component** button located at the very bottom of the *Inspector Panel* .</span></span>

    ![オーディオソースの追加](images/AzureLabs-Lab3-37.png)
 
7.  <span data-ttu-id="67397-345">上記のように、[ *オーディオソース* ] という名前のコンポーネントを検索します。</span><span class="sxs-lookup"><span data-stu-id="67397-345">Search for the component called *Audio Source* , as shown above.</span></span>
8.  <span data-ttu-id="67397-346">また、メインカメラの *変換* コンポーネントが (0, 0, 0) に設定されていることを確認します。これを行うには、カメラの *変換* コンポーネントの横にある **歯車** アイコンを押し、[ **リセット** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="67397-346">Also make sure that the *Transform* component of the Main Camera is set to (0,0,0), this can be done by pressing the **Gear** icon next to the Camera’s *Transform* component and selecting **Reset** .</span></span> <span data-ttu-id="67397-347">*変換* コンポーネントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="67397-347">The *Transform* component should then look like:</span></span>

    1.  <span data-ttu-id="67397-348">*Position* が **0、0、0** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="67397-348">*Position* is set to **0, 0, 0** .</span></span>
    2.  <span data-ttu-id="67397-349">*回転* は **0、0、0** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="67397-349">*Rotation* is set to **0, 0, 0** .</span></span>

    > [!NOTE] 
    > <span data-ttu-id="67397-350">Microsoft HoloLens の場合は、次のものも変更する必要があります。これは、 **メインカメラ** の **カメラ** コンポーネントに含まれています。</span><span class="sxs-lookup"><span data-stu-id="67397-350">For the Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component, which is on your **Main Camera** :</span></span>
    > - <span data-ttu-id="67397-351">**フラグのクリア:** 純色。</span><span class="sxs-lookup"><span data-stu-id="67397-351">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="67397-352">**背景** ' Black, Alpha 0 ' –16進数の色: #00000000。</span><span class="sxs-lookup"><span data-stu-id="67397-352">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

9.  <span data-ttu-id="67397-353">**平面** を左クリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="67397-353">Left click on the **Plane** to select it.</span></span> <span data-ttu-id="67397-354">[ *インスペクター] パネル* で、 *変換* コンポーネントに次の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="67397-354">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |   <span data-ttu-id="67397-355">X 軸</span><span class="sxs-lookup"><span data-stu-id="67397-355">X Axis</span></span>    | <span data-ttu-id="67397-356">Y 軸</span><span class="sxs-lookup"><span data-stu-id="67397-356">Y Axis</span></span> |   <span data-ttu-id="67397-357">Z 軸</span><span class="sxs-lookup"><span data-stu-id="67397-357">Z Axis</span></span>    |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="67397-358">0</span><span class="sxs-lookup"><span data-stu-id="67397-358">0</span></span>     | <span data-ttu-id="67397-359">-1</span><span class="sxs-lookup"><span data-stu-id="67397-359">-1</span></span>                     | <span data-ttu-id="67397-360">0</span><span class="sxs-lookup"><span data-stu-id="67397-360">0</span></span>     |


10. <span data-ttu-id="67397-361">**球** を右クリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="67397-361">Left click on the **Sphere** to select it.</span></span> <span data-ttu-id="67397-362">[ *インスペクター] パネル* で、 *変換* コンポーネントに次の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="67397-362">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |   <span data-ttu-id="67397-363">X 軸</span><span class="sxs-lookup"><span data-stu-id="67397-363">X Axis</span></span>    | <span data-ttu-id="67397-364">Y 軸</span><span class="sxs-lookup"><span data-stu-id="67397-364">Y Axis</span></span> |   <span data-ttu-id="67397-365">Z 軸</span><span class="sxs-lookup"><span data-stu-id="67397-365">Z Axis</span></span>    |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="67397-366">2</span><span class="sxs-lookup"><span data-stu-id="67397-366">2</span></span>     | <span data-ttu-id="67397-367">1</span><span class="sxs-lookup"><span data-stu-id="67397-367">1</span></span>                      | <span data-ttu-id="67397-368">2</span><span class="sxs-lookup"><span data-stu-id="67397-368">2</span></span>     |

11. <span data-ttu-id="67397-369">**円柱** を左クリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="67397-369">Left click on the **Cylinder** to select it.</span></span> <span data-ttu-id="67397-370">[ *インスペクター] パネル* で、 *変換* コンポーネントに次の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="67397-370">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |   <span data-ttu-id="67397-371">X 軸</span><span class="sxs-lookup"><span data-stu-id="67397-371">X Axis</span></span>    | <span data-ttu-id="67397-372">Y 軸</span><span class="sxs-lookup"><span data-stu-id="67397-372">Y Axis</span></span> |   <span data-ttu-id="67397-373">Z 軸</span><span class="sxs-lookup"><span data-stu-id="67397-373">Z Axis</span></span>    |
    |:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="67397-374">-2</span><span class="sxs-lookup"><span data-stu-id="67397-374">-2</span></span>    | <span data-ttu-id="67397-375">1</span><span class="sxs-lookup"><span data-stu-id="67397-375">1</span></span>                      | <span data-ttu-id="67397-376">2</span><span class="sxs-lookup"><span data-stu-id="67397-376">2</span></span>     |

12. <span data-ttu-id="67397-377">**キューブ** を左クリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="67397-377">Left click on the **Cube** to select it.</span></span> <span data-ttu-id="67397-378">[ *インスペクター] パネル* で、 *変換* コンポーネントに次の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="67397-378">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |        | <span data-ttu-id="67397-379">変換- *位置*</span><span class="sxs-lookup"><span data-stu-id="67397-379">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="67397-380">変換- *回転*</span><span class="sxs-lookup"><span data-stu-id="67397-380">Transform - *Rotation*</span></span> |       |
    |:------:|:----------------------:|:-----:|:---:|:-----:|:----------------------:|:-----:|
    | <span data-ttu-id="67397-381">**X**</span><span class="sxs-lookup"><span data-stu-id="67397-381">**X**</span></span> | <span data-ttu-id="67397-382">**Y**</span><span class="sxs-lookup"><span data-stu-id="67397-382">**Y**</span></span>                   | <span data-ttu-id="67397-383">**Z**</span><span class="sxs-lookup"><span data-stu-id="67397-383">**Z**</span></span> |  \| | <span data-ttu-id="67397-384">**X**</span><span class="sxs-lookup"><span data-stu-id="67397-384">**X**</span></span> | <span data-ttu-id="67397-385">**Y**</span><span class="sxs-lookup"><span data-stu-id="67397-385">**Y**</span></span>                  | <span data-ttu-id="67397-386">**Z**</span><span class="sxs-lookup"><span data-stu-id="67397-386">**Z**</span></span> |
    | <span data-ttu-id="67397-387">0</span><span class="sxs-lookup"><span data-stu-id="67397-387">0</span></span>     | <span data-ttu-id="67397-388">1</span><span class="sxs-lookup"><span data-stu-id="67397-388">1</span></span>                       | <span data-ttu-id="67397-389">4</span><span class="sxs-lookup"><span data-stu-id="67397-389">4</span></span>     |  \| | <span data-ttu-id="67397-390">45</span><span class="sxs-lookup"><span data-stu-id="67397-390">45</span></span>    | <span data-ttu-id="67397-391">45</span><span class="sxs-lookup"><span data-stu-id="67397-391">45</span></span>                     | <span data-ttu-id="67397-392">0</span><span class="sxs-lookup"><span data-stu-id="67397-392">0</span></span>     | 

13. <span data-ttu-id="67397-393">**新しいテキスト** オブジェクトを左クリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="67397-393">Left click on the **New Text** object to select it.</span></span> <span data-ttu-id="67397-394">[ *インスペクター] パネル* で、 *変換* コンポーネントに次の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="67397-394">In the *Inspector Panel* set the *Transform* component with the following values:</span></span>

    |       | <span data-ttu-id="67397-395">変換- *位置*</span><span class="sxs-lookup"><span data-stu-id="67397-395">Transform - *Position*</span></span> |       |  \| |       | <span data-ttu-id="67397-396">変換- *スケール*</span><span class="sxs-lookup"><span data-stu-id="67397-396">Transform - *Scale*</span></span> |       |
    |:-----:|:----------------------:|:-----:|:---:|:-----:|:-------------------:|:-----:|
    | <span data-ttu-id="67397-397">**X**</span><span class="sxs-lookup"><span data-stu-id="67397-397">**X**</span></span> | <span data-ttu-id="67397-398">**Y**</span><span class="sxs-lookup"><span data-stu-id="67397-398">**Y**</span></span>                  | <span data-ttu-id="67397-399">**Z**</span><span class="sxs-lookup"><span data-stu-id="67397-399">**Z**</span></span> |  \| | <span data-ttu-id="67397-400">**X**</span><span class="sxs-lookup"><span data-stu-id="67397-400">**X**</span></span> | <span data-ttu-id="67397-401">**Y**</span><span class="sxs-lookup"><span data-stu-id="67397-401">**Y**</span></span>               | <span data-ttu-id="67397-402">**Z**</span><span class="sxs-lookup"><span data-stu-id="67397-402">**Z**</span></span> |
    | <span data-ttu-id="67397-403">-2</span><span class="sxs-lookup"><span data-stu-id="67397-403">-2</span></span>    | <span data-ttu-id="67397-404">6</span><span class="sxs-lookup"><span data-stu-id="67397-404">6</span></span>                      | <span data-ttu-id="67397-405">9</span><span class="sxs-lookup"><span data-stu-id="67397-405">9</span></span>     |  \| | <span data-ttu-id="67397-406">0.1</span><span class="sxs-lookup"><span data-stu-id="67397-406">0.1</span></span>   | <span data-ttu-id="67397-407">0.1</span><span class="sxs-lookup"><span data-stu-id="67397-407">0.1</span></span>                 | <span data-ttu-id="67397-408">0.1</span><span class="sxs-lookup"><span data-stu-id="67397-408">0.1</span></span>   | 

14. <span data-ttu-id="67397-409">**テキストメッシュ** コンポーネントの **フォントサイズ** を **50** に変更します。</span><span class="sxs-lookup"><span data-stu-id="67397-409">Change **Font Size** in the **Text Mesh** component to **50** .</span></span>
15. <span data-ttu-id="67397-410">**テキストメッシュ** オブジェクトの *名前* を **ディクテーションテキスト** に変更します。</span><span class="sxs-lookup"><span data-stu-id="67397-410">Change the *name* of the **Text Mesh** object to **Dictation Text** .</span></span>

    ![3D テキストオブジェクトの作成](images/AzureLabs-Lab3-38.png)
 
16. <span data-ttu-id="67397-412">階層パネルの構造は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="67397-412">Your Hierarchy Panel structure should now look like this:</span></span>

    ![シーンビューのテキストメッシュ](images/AzureLabs-Lab3-38b.png)


17. <span data-ttu-id="67397-414">最終的なシーンは次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="67397-414">The final scene should look like the image below:</span></span>

    ![シーンビュー。](images/AzureLabs-Lab3-39.png)
    
 
## <a name="chapter-5--create-the-microphonemanager-class"></a><span data-ttu-id="67397-416">Chapter 5 – MicrophoneManager クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="67397-416">Chapter 5 – Create the MicrophoneManager class</span></span>

<span data-ttu-id="67397-417">最初に作成するスクリプトは、 *MicrophoneManager* クラスです。</span><span class="sxs-lookup"><span data-stu-id="67397-417">The first Script you are going to create is the *MicrophoneManager* class.</span></span> <span data-ttu-id="67397-418">次に、 *Luismanager* と *ビヘイビアー* クラスを作成します (これら *のクラスを* すべて自由に作成しておきますが、各章で説明します)。</span><span class="sxs-lookup"><span data-stu-id="67397-418">Following this, you will create the *LuisManager* , the *Behaviours* class, and lastly the *Gaze* class (feel free to create all these now, though it will be covered as you reach each Chapter).</span></span>

<span data-ttu-id="67397-419">*MicrophoneManager* クラスは次の役割を担います。</span><span class="sxs-lookup"><span data-stu-id="67397-419">The *MicrophoneManager* class is responsible for:</span></span>

-   <span data-ttu-id="67397-420">ヘッドセットまたはコンピューターに接続されている記録デバイスを検出しています (どちらか一方が既定値です)。</span><span class="sxs-lookup"><span data-stu-id="67397-420">Detecting the recording device attached to the headset or machine (whichever is the default one).</span></span>
-   <span data-ttu-id="67397-421">オーディオ (音声) をキャプチャし、ディクテーションを使用して文字列として格納します。</span><span class="sxs-lookup"><span data-stu-id="67397-421">Capture the audio (voice) and use dictation to store it as a string.</span></span>
-   <span data-ttu-id="67397-422">音声が一時停止したら、そのディクテーションを *Luismanager* クラスに送信します。</span><span class="sxs-lookup"><span data-stu-id="67397-422">Once the voice has paused, submit the dictation to the *LuisManager* class.</span></span> 

<span data-ttu-id="67397-423">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="67397-423">To create this class:</span></span> 

1.  <span data-ttu-id="67397-424">[ *プロジェクト] パネル* 内を右クリックし、 **> フォルダーを作成** します。</span><span class="sxs-lookup"><span data-stu-id="67397-424">Right-click in the *Project Panel* , **Create > Folder** .</span></span> <span data-ttu-id="67397-425">フォルダー **スクリプト** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="67397-425">Call the folder **Scripts** .</span></span> 

    ![Scripts フォルダーを作成します。](images/AzureLabs-Lab3-40.png)
 
2.  <span data-ttu-id="67397-427">**Scripts** フォルダーが作成されたら、それをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="67397-427">With the **Scripts** folder created, double click it, to open.</span></span> <span data-ttu-id="67397-428">次に、そのフォルダー内で右クリックし、[ **> C# スクリプトの作成** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-428">Then, within that folder, right-click, **Create > C# Script** .</span></span> <span data-ttu-id="67397-429">スクリプトに *MicrophoneManager* という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="67397-429">Name the script *MicrophoneManager* .</span></span> 

3.  <span data-ttu-id="67397-430">*MicrophoneManager* をダブルクリックして、 *Visual Studio* で開きます。</span><span class="sxs-lookup"><span data-stu-id="67397-430">Double click on *MicrophoneManager* to open it with *Visual Studio* .</span></span>
4.  <span data-ttu-id="67397-431">ファイルの先頭に次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="67397-431">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using UnityEngine;
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="67397-432">次に、 *MicrophoneManager* クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="67397-432">Then add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        public static MicrophoneManager instance; //help to access instance of this object
        private DictationRecognizer dictationRecognizer;  //Component converting speech to text
        public TextMesh dictationText; //a UI object used to debug dictation result
    ``` 

6.  <span data-ttu-id="67397-433">起動可能な *()* メソッドと *Start ()* メソッドのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-433">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="67397-434">これらは、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="67397-434">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            if (Microphone.devices.Length > 0)
            {
                StartCapturingAudio();
                Debug.Log("Mic Detected");
            }
        }
    ```
 
7.  <span data-ttu-id="67397-435">ここで、音声キャプチャを開始および停止するためにアプリが使用するメソッドが必要であり、間もなくビルドされる *Luismanager* クラスに渡します。</span><span class="sxs-lookup"><span data-stu-id="67397-435">Now you need the method that the App uses to start and stop the voice capture, and pass it to the *LuisManager* class, that you will build soon.</span></span> 

    ```csharp
        /// <summary>
        /// Start microphone capture, by providing the microphone as a continual audio source (looping),
        /// then initialise the DictationRecognizer, which will capture spoken words
        /// </summary>
        public void StartCapturingAudio()
        {
            if (dictationRecognizer == null)
            {
                dictationRecognizer = new DictationRecognizer
                {
                    InitialSilenceTimeoutSeconds = 60,
                    AutoSilenceTimeoutSeconds = 5
                };

                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
                dictationRecognizer.DictationError += DictationRecognizer_DictationError;
            }
            dictationRecognizer.Start();
            Debug.Log("Capturing Audio...");
        }

        /// <summary>
        /// Stop microphone capture
        /// </summary>
        public void StopCapturingAudio()
        {
            dictationRecognizer.Stop();
            Debug.Log("Stop Capturing Audio...");
        }
    ```

8.  <span data-ttu-id="67397-436">音声が一時停止したときに呼び出される *ディクテーションハンドラー* を追加します。</span><span class="sxs-lookup"><span data-stu-id="67397-436">Add a *Dictation Handler* that will be invoked when the voice pauses.</span></span> <span data-ttu-id="67397-437">このメソッドは、ディクテーションテキストを *Luismanager* クラスに渡します。</span><span class="sxs-lookup"><span data-stu-id="67397-437">This method will pass the dictation text to the *LuisManager* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// This method will stop listening for audio, send a request to the LUIS service 
        /// and then start listening again.
        /// </summary>
        private void DictationRecognizer_DictationResult(string dictationCaptured, ConfidenceLevel confidence)
        {
            StopCapturingAudio();
            StartCoroutine(LuisManager.instance.SubmitRequestToLuis(dictationCaptured, StartCapturingAudio));
            Debug.Log("Dictation: " + dictationCaptured);
            dictationText.text = dictationCaptured;
        }

        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            Debug.Log("Dictation exception: " + error);
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="67397-438">*Update ()* メソッドは、このクラスでは使用されないため、削除します。</span><span class="sxs-lookup"><span data-stu-id="67397-438">Delete the *Update()* method since this class will not use it.</span></span>

9.  <span data-ttu-id="67397-439">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="67397-439">Be sure to save your changes in *Visual Studio* before returning to *Unity* .</span></span>

    > [!NOTE]
    > <span data-ttu-id="67397-440">この時点で、 *Unity エディターのコンソールパネル* にエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="67397-440">At this point you will notice an error appearing in the *Unity Editor Console Panel* .</span></span> <span data-ttu-id="67397-441">これは、次の章で作成する *Luismanager* クラスをコードが参照するためです。</span><span class="sxs-lookup"><span data-stu-id="67397-441">This is because the code references the *LuisManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-6--create-the-luismanager-class"></a><span data-ttu-id="67397-442">Chapter 6 – LUISManager クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="67397-442">Chapter 6 – Create the LUISManager class</span></span>

<span data-ttu-id="67397-443">ここで、 *Luismanager* クラスを作成します。これにより、Azure LUIS サービスが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="67397-443">It is time for you to create the *LuisManager* class, which will make the call to the Azure LUIS service.</span></span> 

<span data-ttu-id="67397-444">このクラスの目的は、 *MicrophoneManager* クラスからディクテーションテキストを受け取り、それを分析対象の *Azure Language Understanding API* に送信することです。</span><span class="sxs-lookup"><span data-stu-id="67397-444">The purpose of this class is to receive the dictation text from the *MicrophoneManager* class and send it to the *Azure Language Understanding API* to be analyzed.</span></span>

<span data-ttu-id="67397-445">このクラスは、 *JSON* 応答を逆シリアル化し、 *ビヘイビアー* クラスの適切なメソッドを呼び出してアクションをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="67397-445">This class will deserialize the *JSON* response and call the appropriate methods of the *Behaviours* class to trigger an action.</span></span>

<span data-ttu-id="67397-446">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="67397-446">To create this class:</span></span> 

1.  <span data-ttu-id="67397-447">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="67397-447">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="67397-448">**Scripts** フォルダー内を右クリックし、[ **Create > C# Script** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-448">Right-click inside the **Scripts** folder, click **Create > C# Script** .</span></span> <span data-ttu-id="67397-449">スクリプトに「 *Luismanager* 」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="67397-449">Name the script *LuisManager* .</span></span> 
3.  <span data-ttu-id="67397-450">スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="67397-450">Double click on the script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="67397-451">ファイルの先頭に次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="67397-451">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="67397-452">最初に、 *Luismanager* クラス **内** に3つのクラス ( *Start ()* メソッドの上にある同じスクリプトファイル内) を作成し、Azure からの逆シリアル化された JSON 応答を表します。</span><span class="sxs-lookup"><span data-stu-id="67397-452">You will begin by creating three classes **inside** the *LuisManager* class (within the same script file, above the *Start()* method) that will represent the deserialized JSON response from Azure.</span></span>

    ```csharp
        [Serializable] //this class represents the LUIS response
        public class AnalysedQuery
        {
            public TopScoringIntentData topScoringIntent;
            public EntityData[] entities;
            public string query;
        }

        // This class contains the Intent LUIS determines 
        // to be the most likely
        [Serializable]
        public class TopScoringIntentData
        {
            public string intent;
            public float score;
        }

        // This class contains data for an Entity
        [Serializable]
        public class EntityData
        {
            public string entity;
            public string type;
            public int startIndex;
            public int endIndex;
            public float score;
        }
    ```

6.  <span data-ttu-id="67397-453">次に、 *Luismanager* クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="67397-453">Next, add the following variables inside the *LuisManager* class:</span></span>
 
    ```csharp
        public static LuisManager instance;

        //Substitute the value of luis Endpoint with your own End Point
        string luisEndpoint = "https://westus.api.cognitive... add your endpoint from the Luis Portal";
    ```

7.  <span data-ttu-id="67397-454">LUIS エンドポイントを現在の場所 (LUIS ポータルから取得) に配置してください。</span><span class="sxs-lookup"><span data-stu-id="67397-454">Make sure to place your LUIS endpoint in now (which you will have from your LUIS portal).</span></span>

8.  <span data-ttu-id="67397-455">起動前 *()* メソッドのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-455">Code for the *Awake()* method now needs to be added.</span></span> <span data-ttu-id="67397-456">このメソッドは、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="67397-456">This method will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```

9.  <span data-ttu-id="67397-457">ここで、 *MicrophoneManager* クラスから受け取ったディクテーションを *LUIS* に送信し、応答を受信して逆シリアル化するために、このアプリケーションが使用するメソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="67397-457">Now you need the methods this application uses to send the dictation received from the *MicrophoneManager* class to *LUIS* , and then receive and deserialize the response.</span></span> 
10. <span data-ttu-id="67397-458">インテントの値と関連エンティティが決定されると、 *ビヘイビアー* クラスのインスタンスに渡され、目的のアクションがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="67397-458">Once the value of the Intent, and associated Entities, have been determined, they are passed to the instance of the *Behaviours* class to trigger the intended action.</span></span>

    ```csharp
        /// <summary>
        /// Call LUIS to submit a dictation result.
        /// The done Action is called at the completion of the method.
        /// </summary>
        public IEnumerator SubmitRequestToLuis(string dictationResult, Action done)
        {
            string queryString = string.Concat(Uri.EscapeDataString(dictationResult));

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(luisEndpoint + queryString))
            {
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                }
                else
                {
                    try
                    {
                        AnalysedQuery analysedQuery = JsonUtility.FromJson<AnalysedQuery>(unityWebRequest.downloadHandler.text);

                        //analyse the elements of the response 
                        AnalyseResponseElements(analysedQuery);
                    }
                    catch (Exception exception)
                    {
                        Debug.Log("Luis Request Exception Message: " + exception.Message);
                    }
                }

                done();
                yield return null;
            }
        }
    ```
 
11. <span data-ttu-id="67397-459">結果として得られた *AnalysedQuery* を読み取ってエンティティを決定する、analytics *Ser onseelements ()* という名前の新しいメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="67397-459">Create a new method called *AnalyseResponseElements()* that will read the resulting *AnalysedQuery* and determine the Entities.</span></span> <span data-ttu-id="67397-460">これらのエンティティが決定されると、 *ビヘイビアー* クラスのインスタンスに渡され、アクションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="67397-460">Once those Entities are determined, they will be passed to the instance of the *Behaviours* class to use in the actions.</span></span>

    ```csharp
        private void AnalyseResponseElements(AnalysedQuery aQuery)
        {
            string topIntent = aQuery.topScoringIntent.intent;

            // Create a dictionary of entities associated with their type
            Dictionary<string, string> entityDic = new Dictionary<string, string>();

            foreach (EntityData ed in aQuery.entities)
            {
                entityDic.Add(ed.type, ed.entity);
            }

            // Depending on the topmost recognized intent, read the entities name
            switch (aQuery.topScoringIntent.intent)
            {
                case "ChangeObjectColor":
                    string targetForColor = null;
                    string color = null;

                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForColor = pair.Value;
                        }
                        else if (pair.Key == "color")
                        {
                            color = pair.Value;
                        }
                    }

                    Behaviours.instance.ChangeTargetColor(targetForColor, color);
                    break;

                case "ChangeObjectSize":
                    string targetForSize = null;
                    foreach (var pair in entityDic)
                    {
                        if (pair.Key == "target")
                        {
                            targetForSize = pair.Value;
                        }
                    }

                    if (entityDic.ContainsKey("upsize") == true)
                    {
                        Behaviours.instance.UpSizeTarget(targetForSize);
                    }
                    else if (entityDic.ContainsKey("downsize") == true)
                    {
                        Behaviours.instance.DownSizeTarget(targetForSize);
                    }
                    break;
            }
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="67397-461">*Start ()* および *Update ()* メソッドは、このクラスでは使用されないため、削除します。</span><span class="sxs-lookup"><span data-stu-id="67397-461">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

12. <span data-ttu-id="67397-462">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="67397-462">Be sure to save your changes in *Visual Studio* before returning to *Unity* .</span></span>

> [!NOTE]
> <span data-ttu-id="67397-463">この時点で、 *Unity エディターのコンソールパネル* にいくつかのエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="67397-463">At this point you will notice several errors appearing in the *Unity Editor Console Panel* .</span></span> <span data-ttu-id="67397-464">これは、次の章で作成する *ビヘイビアー* クラスをコードが参照するためです。</span><span class="sxs-lookup"><span data-stu-id="67397-464">This is because the code references the *Behaviours* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--create-the-behaviours-class"></a><span data-ttu-id="67397-465">第7章–ビヘイビアークラスの作成</span><span class="sxs-lookup"><span data-stu-id="67397-465">Chapter 7 – Create the Behaviours class</span></span>

<span data-ttu-id="67397-466">*ビヘイビアー* クラスは、 *luismanager* クラスによって提供されるエンティティを使用してアクションをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="67397-466">The *Behaviours* class will trigger the actions using the Entities provided by the *LuisManager* class.</span></span>

<span data-ttu-id="67397-467">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="67397-467">To create this class:</span></span> 

1.  <span data-ttu-id="67397-468">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="67397-468">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="67397-469">**Scripts** フォルダー内を右クリックし、[ **Create > C# Script** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-469">Right-click inside the **Scripts** folder, click **Create > C# Script** .</span></span> <span data-ttu-id="67397-470">スクリプトに *ビヘイビアー* という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="67397-470">Name the script *Behaviours* .</span></span> 
3.  <span data-ttu-id="67397-471">スクリプトをダブルクリックして、 *Visual Studio* で開きます。</span><span class="sxs-lookup"><span data-stu-id="67397-471">Double click on the script to open it with *Visual Studio* .</span></span>
4.  <span data-ttu-id="67397-472">次に、 *ビヘイビアー* クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="67397-472">Then add the following variables inside the *Behaviours* class:</span></span>

    ```csharp
        public static Behaviours instance;

        // the following variables are references to possible targets
        public GameObject sphere;
        public GameObject cylinder;
        public GameObject cube;
        internal GameObject gazedTarget;
    ```
 
5.  <span data-ttu-id="67397-473">起動前 *()* メソッドのコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="67397-473">Add the *Awake()* method code.</span></span> <span data-ttu-id="67397-474">このメソッドは、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="67397-474">This method will be called when the class initializes:</span></span>

    ```csharp
        void Awake()
        {
            // allows this class instance to behave like a singleton
            instance = this;
        }
    ```
 
6.  <span data-ttu-id="67397-475">次のメソッドは、クエリの対象となるオブジェクトを判別するために、 *Luismanager* クラス (前に作成したもの) によって呼び出され、適切なアクションをトリガーします。</span><span class="sxs-lookup"><span data-stu-id="67397-475">The following methods are called by the *LuisManager* class (which you have created previously) to determine which object is the target of the query and then trigger the appropriate action.</span></span>

    ```csharp
        /// <summary>
        /// Changes the color of the target GameObject by providing the name of the object
        /// and the name of the color
        /// </summary>
        public void ChangeTargetColor(string targetName, string colorName)
        {
            GameObject foundTarget = FindTarget(targetName);
            if (foundTarget != null)
            {
                Debug.Log("Changing color " + colorName + " to target: " + foundTarget.name);

                switch (colorName)
                {
                    case "blue":
                        foundTarget.GetComponent<Renderer>().material.color = Color.blue;
                        break;

                    case "red":
                        foundTarget.GetComponent<Renderer>().material.color = Color.red;
                        break;

                    case "yellow":
                        foundTarget.GetComponent<Renderer>().material.color = Color.yellow;
                        break;

                    case "green":
                        foundTarget.GetComponent<Renderer>().material.color = Color.green;
                        break;

                    case "white":
                        foundTarget.GetComponent<Renderer>().material.color = Color.white;
                        break;

                    case "black":
                        foundTarget.GetComponent<Renderer>().material.color = Color.black;
                        break;
                }          
            }
        }

        /// <summary>
        /// Reduces the size of the target GameObject by providing its name
        /// </summary>
        public void DownSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale -= new Vector3(0.5F, 0.5F, 0.5F);
        }

        /// <summary>
        /// Increases the size of the target GameObject by providing its name
        /// </summary>
        public void UpSizeTarget(string targetName)
        {
            GameObject foundTarget = FindTarget(targetName);
            foundTarget.transform.localScale += new Vector3(0.5F, 0.5F, 0.5F);
        }
    ```
 
7.  <span data-ttu-id="67397-476">*Findtarget ()* メソッドを追加して、現在のインテントの対象となるのはどの *オブジェクト* かを判別します。</span><span class="sxs-lookup"><span data-stu-id="67397-476">Add the *FindTarget()* method to determine which of the *GameObjects* is the target of the current Intent.</span></span> <span data-ttu-id="67397-477">エンティティに明示的なターゲットが定義されていない場合、このメソッドは、ターゲット *オブジェクト* を既定の "gazed" に設定します。</span><span class="sxs-lookup"><span data-stu-id="67397-477">This method defaults the target to the *GameObject* being “gazed” if no explicit target is defined in the Entities.</span></span>

    ```csharp
        /// <summary>
        /// Determines which object reference is the target GameObject by providing its name
        /// </summary>
        private GameObject FindTarget(string name)
        {
            GameObject targetAsGO = null;

            switch (name)
            {
                case "sphere":
                    targetAsGO = sphere;
                    break;

                case "cylinder":
                    targetAsGO = cylinder;
                    break;

                case "cube":
                    targetAsGO = cube;
                    break;

                case "this": // as an example of target words that the user may use when looking at an object
                case "it":  // as this is the default, these are not actually needed in this example
                case "that":
                default: // if the target name is none of those above, check if the user is looking at something
                    if (gazedTarget != null) 
                    {
                        targetAsGO = gazedTarget;
                    }
                    break;
            }
            return targetAsGO;
        }
    ```
 
    > [!IMPORTANT]
    > <span data-ttu-id="67397-478">*Start ()* および *Update ()* メソッドは、このクラスでは使用されないため、削除します。</span><span class="sxs-lookup"><span data-stu-id="67397-478">Delete the *Start()* and *Update()* methods since this class will not use them.</span></span>

8.  <span data-ttu-id="67397-479">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="67397-479">Be sure to save your changes in *Visual Studio* before returning to *Unity* .</span></span>

## <a name="chapter-8--create-the-gaze-class"></a><span data-ttu-id="67397-480">章8–宝石クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="67397-480">Chapter 8 – Create the Gaze Class</span></span>

<span data-ttu-id="67397-481">このアプリを完成させるために必要な最後のクラスは、 *宝石* クラスです。</span><span class="sxs-lookup"><span data-stu-id="67397-481">The last class that you will need to complete this app is the *Gaze* class.</span></span> <span data-ttu-id="67397-482">このクラスは、ユーザーのビジュアルフォーカス内に現在存在する *オブジェクト* への参照を更新します。</span><span class="sxs-lookup"><span data-stu-id="67397-482">This class updates the reference to the *GameObject* currently in the user’s visual focus.</span></span>

<span data-ttu-id="67397-483">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="67397-483">To create this Class:</span></span> 

1.  <span data-ttu-id="67397-484">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="67397-484">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="67397-485">**Scripts** フォルダー内を右クリックし、[ **Create > C# Script** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-485">Right-click inside the **Scripts** folder, click **Create > C# Script** .</span></span> <span data-ttu-id="67397-486">スクリプトに「」という名前を *指定します* 。</span><span class="sxs-lookup"><span data-stu-id="67397-486">Name the script *Gaze* .</span></span> 
3.  <span data-ttu-id="67397-487">スクリプトをダブルクリックして、 *Visual Studio* で開きます。</span><span class="sxs-lookup"><span data-stu-id="67397-487">Double click on the script to open it with *Visual Studio* .</span></span>
4.  <span data-ttu-id="67397-488">このクラスの次のコードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="67397-488">Insert the following code for this class:</span></span>

    ```csharp
        using UnityEngine;

        public class Gaze : MonoBehaviour
        {        
            internal GameObject gazedObject;
            public float gazeMaxDistance = 300;

            void Update()
            {
                // Uses a raycast from the Main Camera to determine which object is gazed upon.
                Vector3 fwd = gameObject.transform.TransformDirection(Vector3.forward);
                Ray ray = new Ray(Camera.main.transform.position, fwd);
                RaycastHit hit;
                Debug.DrawRay(Camera.main.transform.position, fwd);

                if (Physics.Raycast(ray, out hit, gazeMaxDistance) && hit.collider != null)
                {
                    if (gazedObject == null)
                    {
                        gazedObject = hit.transform.gameObject;

                        // Set the gazedTarget in the Behaviours class
                        Behaviours.instance.gazedTarget = gazedObject;
                    }
                }
                else
                {
                    ResetGaze();
                }         
            }

            // Turn the gaze off, reset the gazeObject in the Behaviours class.
            public void ResetGaze()
            {
                if (gazedObject != null)
                {
                    Behaviours.instance.gazedTarget = null;
                    gazedObject = null;
                }
            }
        }
    ```
 
5.  <span data-ttu-id="67397-489">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="67397-489">Be sure to save your changes in *Visual Studio* before returning to *Unity* .</span></span>

## <a name="chapter-9--completing-the-scene-setup"></a><span data-ttu-id="67397-490">第9章: シーンのセットアップの完了</span><span class="sxs-lookup"><span data-stu-id="67397-490">Chapter 9 – Completing the scene setup</span></span>

1.  <span data-ttu-id="67397-491">シーンのセットアップを完了するには、作成した各スクリプトを [スクリプト] フォルダーから、[ *階層] パネル* の [ **メインカメラ** ] オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="67397-491">To complete the setup of the scene, drag each script that you have created from the Scripts Folder to the **Main Camera** object in the *Hierarchy Panel* .</span></span>
2.  <span data-ttu-id="67397-492">**メインカメラ** を選択して [ *インスペクター] パネル* を表示すると、アタッチした各スクリプトを確認できます。また、設定されていない各スクリプトにはパラメーターがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="67397-492">Select the **Main Camera** and look at the *Inspector Panel* , you should be able to see each script that you have attached, and you will notice that there are parameters on each script that are yet to be set.</span></span>

    ![カメラ参照ターゲットを設定しています。](images/AzureLabs-Lab3-41.png)

3.  <span data-ttu-id="67397-494">これらのパラメーターを適切に設定するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="67397-494">To set these parameters correctly, follow these instructions:</span></span>

    1. <span data-ttu-id="67397-495">*MicrophoneManager* :</span><span class="sxs-lookup"><span data-stu-id="67397-495">*MicrophoneManager* :</span></span>

        - <span data-ttu-id="67397-496">[ *階層] パネル* で、[ **ディクテーションテキスト** ] オブジェクトを [ **ディクテーションテキスト** のパラメーター値] ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="67397-496">From the *Hierarchy Panel* , drag the **Dictation Text** object into the **Dictation Text** parameter value box.</span></span>

    2. <span data-ttu-id="67397-497">*ビヘイビアー* 、 *階層パネル* から:</span><span class="sxs-lookup"><span data-stu-id="67397-497">*Behaviours* , from the *Hierarchy Panel* :</span></span>

        - <span data-ttu-id="67397-498">**球体** オブジェクトを [ *球* 参照ターゲット] ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="67397-498">Drag the **Sphere** object into the *Sphere* reference target box.</span></span>
        - <span data-ttu-id="67397-499">**円柱** を [ *シリンダー* 参照ターゲット] ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="67397-499">Drag the **Cylinder** into the *Cylinder* reference target box.</span></span>
        - <span data-ttu-id="67397-500">**キューブ** を [ *キューブ* 参照ターゲット] ボックスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="67397-500">Drag the **Cube** into the *Cube* reference target box.</span></span>

    3. <span data-ttu-id="67397-501">*宝石* :</span><span class="sxs-lookup"><span data-stu-id="67397-501">*Gaze* :</span></span>

        - <span data-ttu-id="67397-502">" *宝石の最大距離* " を **300** に設定します (まだ存在していない場合)。</span><span class="sxs-lookup"><span data-stu-id="67397-502">Set the *Gaze Max Distance* to **300** (if it is not already).</span></span> 

4.  <span data-ttu-id="67397-503">結果は次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="67397-503">The result should look like the image below:</span></span>

    ![カメラ参照ターゲットを表示し、現在設定されています。](images/AzureLabs-Lab3-42.png)
 
## <a name="chapter-10--test-in-the-unity-editor"></a><span data-ttu-id="67397-505">Chapter 10-Unity エディターでのテスト</span><span class="sxs-lookup"><span data-stu-id="67397-505">Chapter 10 – Test in the Unity Editor</span></span>

<span data-ttu-id="67397-506">シーンのセットアップが正しく実装されていることをテストします。</span><span class="sxs-lookup"><span data-stu-id="67397-506">Test that the Scene setup is properly implemented.</span></span>

<span data-ttu-id="67397-507">次のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="67397-507">Ensure that:</span></span>

-   <span data-ttu-id="67397-508">すべてのスクリプトが **メインカメラ** オブジェクトにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="67397-508">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="67397-509">*メインカメラインスペクターパネル* のすべてのフィールドが適切に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="67397-509">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>

1.  <span data-ttu-id="67397-510">*Unity エディター* で [ **再生** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-510">Press the **Play** button in the *Unity Editor* .</span></span> <span data-ttu-id="67397-511">アプリは、接続されているイマーシブヘッドセット内で実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-511">The App should be running within the attached immersive headset.</span></span>

2.  <span data-ttu-id="67397-512">次のように、いくつかの発話を試してみてください。</span><span class="sxs-lookup"><span data-stu-id="67397-512">Try a few utterances, such as:</span></span>

    ```
    make the cylinder red

    change the cube to yellow

    I want the sphere blue

    make this to green

    change it to white
    ```

    > [!NOTE]
    > <span data-ttu-id="67397-513">既定のオーディオデバイスの変更について Unity コンソールにエラーが表示される場合は、シーンが想定どおりに機能しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="67397-513">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="67397-514">これは、mixed reality ポータルが、ヘッドセットを持つヘッドホン用の組み込みマイクを扱う方法に起因します。</span><span class="sxs-lookup"><span data-stu-id="67397-514">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="67397-515">このエラーが表示された場合は、単にシーンを停止してからもう一度開始するだけで、期待どおりに動作するはずです。</span><span class="sxs-lookup"><span data-stu-id="67397-515">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-11--build-and-sideload-the-uwp-solution"></a><span data-ttu-id="67397-516">第11章– UWP ソリューションのビルドとサイドロード</span><span class="sxs-lookup"><span data-stu-id="67397-516">Chapter 11 – Build and sideload the UWP Solution</span></span>

<span data-ttu-id="67397-517">Unity エディターでアプリケーションが動作していることを確認したら、ビルドと配置を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="67397-517">Once you have ensured that the application is working in the Unity Editor, you are ready to Build and Deploy.</span></span>

<span data-ttu-id="67397-518">ビルドするには:</span><span class="sxs-lookup"><span data-stu-id="67397-518">To Build:</span></span>

1.  <span data-ttu-id="67397-519">[ **ファイル > 保存** ] をクリックして、現在のシーンを保存します。</span><span class="sxs-lookup"><span data-stu-id="67397-519">Save the current scene by clicking on **File > Save** .</span></span>
2.  <span data-ttu-id="67397-520">**ファイル > ビルド設定** にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="67397-520">Go to **File > Build Settings** .</span></span>
3.  <span data-ttu-id="67397-521">**Unity C# プロジェクト** と呼ばれるボックスを目盛りします (UWP プロジェクトの作成後にコードを表示してデバッグする場合に便利です)。</span><span class="sxs-lookup"><span data-stu-id="67397-521">Tick the box called **Unity C# Projects** (useful for seeing and debugging your code once the UWP project is created.</span></span>
4.  <span data-ttu-id="67397-522">[開いている **シーンの追加** ] をクリックし、[ **ビルド** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-522">Click on **Add Open Scenes** , then click **Build** .</span></span>

    ![ビルドの設定ウィンドウ](images/AzureLabs-Lab3-43.png)

4.  <span data-ttu-id="67397-524">ソリューションをビルドするフォルダーを選択するように求められます。</span><span class="sxs-lookup"><span data-stu-id="67397-524">You will be prompted to select the folder where you want to build the Solution.</span></span> 

5.  <span data-ttu-id="67397-525">*ビルド* フォルダーを作成し、そのフォルダー内で、適切な名前を指定して別のフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="67397-525">Create a *BUILDS* folder and within that folder create another folder with an appropriate name of your choice.</span></span> 
6.  <span data-ttu-id="67397-526">[ **フォルダーの選択** ] をクリックして、その場所でビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="67397-526">Click **Select Folder** to begin the build at that location.</span></span>
 
    <span data-ttu-id="67397-527">![ビルドフォルダーの作成 ](images/AzureLabs-Lab3-44.png)
     ![ ビルドフォルダーの選択](images/AzureLabs-Lab3-45.png)</span><span class="sxs-lookup"><span data-stu-id="67397-527">![Create Builds Folder](images/AzureLabs-Lab3-44.png)
![Select Builds Folder](images/AzureLabs-Lab3-45.png)</span></span>
 
7.  <span data-ttu-id="67397-528">Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で **ファイルエクスプローラー** ウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="67397-528">Once Unity has finished building (it might take some time), it should open a **File Explorer** window at the location of your build.</span></span>

<span data-ttu-id="67397-529">ローカルコンピューターに配置するには:</span><span class="sxs-lookup"><span data-stu-id="67397-529">To Deploy on Local Machine:</span></span>

1.  <span data-ttu-id="67397-530">*Visual Studio* で、 [前の章](#chapter-10--test-in-the-unity-editor)で作成したソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="67397-530">In *Visual Studio* , open the solution file that has been created in the [previous Chapter](#chapter-10--test-in-the-unity-editor).</span></span>
2.  <span data-ttu-id="67397-531">**ソリューションプラットフォーム** で、[ **X86** , **ローカルコンピューター** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="67397-531">In the **Solution Platform** , select **x86** , **Local Machine** .</span></span>
3.  <span data-ttu-id="67397-532">**ソリューション構成** で、[ **デバッグ** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="67397-532">In the **Solution Configuration** select **Debug** .</span></span>

    > <span data-ttu-id="67397-533">Microsoft HoloLens の場合、これを *リモートコンピューター* に設定する方が簡単な場合があります。これにより、コンピューターにテザリングさされることはありません。</span><span class="sxs-lookup"><span data-stu-id="67397-533">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine* , so that you are not tethered to your computer.</span></span> <span data-ttu-id="67397-534">ただし、次の手順も実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-534">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="67397-535">HoloLens の **IP アドレス** を確認します。これは、 *[設定 > ネットワーク & インターネット > Wi-fi > 詳細オプション]* にあります。IPv4 は、使用するアドレスです。</span><span class="sxs-lookup"><span data-stu-id="67397-535">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options* ; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="67397-536">**開発者モード** が **オンに** なっていることを確認します。 *開発者向けのセキュリティ > の更新プログラム & の > の設定* にあります。</span><span class="sxs-lookup"><span data-stu-id="67397-536">Ensure **Developer Mode** is **On** ; found in *Settings > Update & Security > For developers* .</span></span>

    ![アプリをデプロイする](images/AzureLabs-Lab3-46.png)
 
4.  <span data-ttu-id="67397-538">[ **ビルド] メニュー** の [ソリューションの **配置** ] をクリックして、アプリケーションをコンピューターにサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="67397-538">Go to the **Build menu** and click on **Deploy Solution** to sideload the application to your machine.</span></span>
5.  <span data-ttu-id="67397-539">アプリがインストール済みアプリの一覧に表示され、起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="67397-539">Your App should now appear in the list of installed apps, ready to be launched!</span></span>
6.  <span data-ttu-id="67397-540">アプリを起動すると、 _マイク_ へのアクセスを承認するように求められます。</span><span class="sxs-lookup"><span data-stu-id="67397-540">Once launched, the App will prompt you to authorize access to the _Microphone_ .</span></span> <span data-ttu-id="67397-541">*モーションコントローラー* 、 *音声入力* 、または *キーボード* を使用して、 **[はい** ] ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="67397-541">Use the *Motion Controllers* , or *Voice Input* , or the *Keyboard* to press the **YES** button.</span></span> 

## <a name="chapter-12--improving-your-luis-service"></a><span data-ttu-id="67397-542">第12章: LUIS サービスの向上</span><span class="sxs-lookup"><span data-stu-id="67397-542">Chapter 12 – Improving your LUIS service</span></span>

>[!IMPORTANT] 
> <span data-ttu-id="67397-543">この章は非常に重要であり、LUIS サービスの精度を向上させるために複数回繰り返す必要がある場合があります。これを完了していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="67397-543">This chapter is incredibly important, and may need to be iterated upon several times, as it will help improve the accuracy of your LUIS service: ensure you complete this.</span></span>

<span data-ttu-id="67397-544">LUIS によって提供される理解レベルを向上させるには、新しい発話をキャプチャし、それらを使用して LUIS アプリを再トレーニングする必要があります。</span><span class="sxs-lookup"><span data-stu-id="67397-544">To improve the level of understanding provided by LUIS you need to capture new utterances and use them to re-train your LUIS App.</span></span>

<span data-ttu-id="67397-545">たとえば、"増加" と "アップサイズ" を理解するためにトレーニング済みの LUIS を使用しているとしても、アプリで "拡大" のような単語を理解したいとは思いませんか。</span><span class="sxs-lookup"><span data-stu-id="67397-545">For example, you might have trained LUIS to understand “Increase” and “Upsize”, but wouldn’t you want your app to also understand words like “Enlarge”?</span></span>

<span data-ttu-id="67397-546">アプリケーションを数回使用した後は、前述のすべてのものが LUIS によって収集され、LUIS ポータルで利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="67397-546">Once you have used your application a few times, everything you have said will be collected by LUIS and available in the LUIS PORTAL.</span></span>

1.  <span data-ttu-id="67397-547">この [リンク](https://www.luis.ai/home)に従ってポータルアプリケーションにアクセスし、ログインします。</span><span class="sxs-lookup"><span data-stu-id="67397-547">Go to your portal application following this [LINK](https://www.luis.ai/home), and Log In.</span></span>
2.  <span data-ttu-id="67397-548">MS 資格情報でログインしたら、 *アプリ名* をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-548">Once you are logged in with your MS Credentials, click on your *App name* .</span></span>
3.  <span data-ttu-id="67397-549">ページの左側にある [ **Review endpoint 発話** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-549">Click the **Review endpoint utterances** button on the left of the page.</span></span>

    ![発話の確認](images/AzureLabs-Lab3-47.png)
 
4.  <span data-ttu-id="67397-551">混合した現実のアプリケーションによって LUIS に送信された発話の一覧が表示されます。</span><span class="sxs-lookup"><span data-stu-id="67397-551">You will be shown a list of the Utterances that have been sent to LUIS by your mixed reality Application.</span></span>

    ![発話の一覧](images/AzureLabs-Lab3-48.png)
 
<span data-ttu-id="67397-553">強調表示されている *エンティティ* がいくつかわかります。</span><span class="sxs-lookup"><span data-stu-id="67397-553">You will notice some highlighted *Entities* .</span></span> 

<span data-ttu-id="67397-554">強調表示された各単語の上にマウスポインターを置くと、各 (発話) を確認し、正しく認識されたエンティティ、どのエンティティが間違っているか、どのエンティティが不足しているかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="67397-554">By hovering over each highlighted word, you can review each Utterance and determine which Entity has been recognized correctly, which Entities are wrong and which Entities are missed.</span></span>

<span data-ttu-id="67397-555">上記の例では、"スピアー" という単語はターゲットとして強調表示されているため、誤って修正する必要があります。これを行うには、マウスで単語をポイントし、[ **ラベルの削除** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="67397-555">In the example above, it was found that the word “spear” had been highlighted as a target, so it necessary to correct the mistake, which is done by hovering over the word with the mouse and clicking **Remove Label** .</span></span>

<span data-ttu-id="67397-556">![チェック発話の ](images/AzureLabs-Lab3-49.png)
 ![ ラベルイメージの削除](images/AzureLabs-Lab3-50.png)</span><span class="sxs-lookup"><span data-stu-id="67397-556">![Check utterances](images/AzureLabs-Lab3-49.png)
![Remove Label Image](images/AzureLabs-Lab3-50.png)</span></span>
 
5.  <span data-ttu-id="67397-557">完全に間違った発話が見つかった場合は、画面の右側にある [ **削除** ] ボタンを使用して削除できます。</span><span class="sxs-lookup"><span data-stu-id="67397-557">If you find Utterances that are completely wrong, you can delete them using the **Delete** button on the right side of the screen.</span></span>

    ![間違った発話の削除](images/AzureLabs-Lab3-51.png)

6.  <span data-ttu-id="67397-559">または、LUIS が (発話) を正しく解釈したと思われる場合は、[固定された **インテントに追加** ] ボタンを使用して、その理解を検証することができます。</span><span class="sxs-lookup"><span data-stu-id="67397-559">Or if you feel that LUIS has interpreted the Utterance correctly, you can validate its understanding by using the **Add To Aligned Intent** button.</span></span>

    ![固定されたインテントに追加](images/AzureLabs-Lab3-52.png)

7.  <span data-ttu-id="67397-561">表示されているすべての発話を並べ替えた後、ページを再度読み込んで、使用できるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="67397-561">Once you have sorted all the displayed Utterances, try and reload the page to see if more are available.</span></span>
8.  <span data-ttu-id="67397-562">このプロセスをできるだけ多く繰り返して、アプリケーションの理解を向上させることが非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="67397-562">It is very important to repeat this process as many times as possible to improve your application understanding.</span></span> 

<span data-ttu-id="67397-563">**お楽しみください!**</span><span class="sxs-lookup"><span data-stu-id="67397-563">**Have fun!**</span></span>

## <a name="your-finished-luis-integrated-application"></a><span data-ttu-id="67397-564">完成した LUIS 統合アプリケーション</span><span class="sxs-lookup"><span data-stu-id="67397-564">Your finished LUIS Integrated application</span></span>

<span data-ttu-id="67397-565">これで、Azure Language Understanding インテリジェンスサービスを活用する mixed reality アプリを構築し、ユーザーが何をしているかを把握し、その情報を操作できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="67397-565">Congratulations, you built a mixed reality app that leverages the Azure Language Understanding Intelligence Service, to understand what a user says, and act on that information.</span></span>

![ラボの結果](images/AzureLabs-Lab3-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="67397-567">ボーナス演習</span><span class="sxs-lookup"><span data-stu-id="67397-567">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="67397-568">演習1</span><span class="sxs-lookup"><span data-stu-id="67397-568">Exercise 1</span></span>

<span data-ttu-id="67397-569">このアプリケーションを使用しているときに、Floor オブジェクトを見つめ、その色を変更するように要求すると、そのようになります。</span><span class="sxs-lookup"><span data-stu-id="67397-569">While using this application you might notice that if you gaze at the Floor object and ask to change its color, it will do so.</span></span> <span data-ttu-id="67397-570">アプリケーションでフロアの色を変更できないようにする方法はありますか。</span><span class="sxs-lookup"><span data-stu-id="67397-570">Can you work out how to stop your application from changing the Floor color?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="67397-571">演習2</span><span class="sxs-lookup"><span data-stu-id="67397-571">Exercise 2</span></span>

<span data-ttu-id="67397-572">LUIS とアプリの機能を拡張して、シーンにオブジェクトの機能を追加してみてください。例として、ユーザーの指示に応じて、宝石ヒットポイントに新しいオブジェクトを作成し、既存のコマンドを使用して、それらのオブジェクトを現在のシーンオブジェクトと共に使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="67397-572">Try extending the LUIS and App capabilities, adding additional functionality for objects in scene; as an example, create new objects at the Gaze hit point, depending on what the user says, and then be able to use those objects alongside current scene objects, with the existing commands.</span></span> 
