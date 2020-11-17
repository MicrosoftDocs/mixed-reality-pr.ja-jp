---
title: MR と Azure 301 - 言語翻訳
description: このコースでは、mixed reality アプリケーション内で Azure Translator Text API を実装する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, 翻訳テキスト, hololens, イマーシブ, vr, 言語翻訳, Windows 10, Visual Studio
ms.openlocfilehash: 3f7d48df92ae5ed979c6fa8d69d348ce084d3fb9
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679571"
---
# <a name="mr-and-azure-301-language-translation"></a><span data-ttu-id="f28f9-104">MR と Azure 301:言語翻訳</span><span class="sxs-lookup"><span data-stu-id="f28f9-104">MR and Azure 301: Language translation</span></span>

<br>

>[!NOTE]
><span data-ttu-id="f28f9-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="f28f9-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="f28f9-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="f28f9-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="f28f9-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。</span><span class="sxs-lookup"><span data-stu-id="f28f9-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="f28f9-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="f28f9-109">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="f28f9-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="f28f9-110">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

<span data-ttu-id="f28f9-111">このコースでは、Translator Text API と共に Azure Cognitive Services を使用して、混合の現実アプリケーションに翻訳機能を追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-111">In this course, you will learn how to add translation capabilities to a mixed reality application using Azure Cognitive Services, with the Translator Text API.</span></span>

![最終製品](images/AzureLabs-Lab1-00.png)

<span data-ttu-id="f28f9-113">Translator Text API は、ほぼリアルタイムで動作する翻訳サービスです。</span><span class="sxs-lookup"><span data-stu-id="f28f9-113">The Translator Text API is a translation Service which works in near real-time.</span></span> <span data-ttu-id="f28f9-114">サービスはクラウドベースであり、REST API 呼び出しを使用して、アプリはニューラル機械翻訳テクノロジを利用してテキストを別の言語に変換できます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-114">The Service is cloud-based, and, using a REST API call, an app can make use of the neural machine translation technology to translate text to another language.</span></span> <span data-ttu-id="f28f9-115">詳細については、 [Azure Translator Text API のページ](https://azure.microsoft.com/services/cognitive-services/translator-text-api/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f28f9-115">For more information, visit the [Azure Translator Text API page](https://azure.microsoft.com/services/cognitive-services/translator-text-api/).</span></span>

<span data-ttu-id="f28f9-116">このコースが完了すると、mixed reality アプリケーションが完成し、次のことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-116">Upon completion of this course, you will have a mixed reality application which will be able to do the following:</span></span>

1.  <span data-ttu-id="f28f9-117">ユーザーは、イマーシブ (VR) ヘッドセット (または HoloLens の内蔵マイク) に接続されているマイクに接続します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-117">The user will speak into a microphone connected to an immersive (VR) headset (or the built-in microphone of HoloLens).</span></span>
2.  <span data-ttu-id="f28f9-118">アプリはディクテーションをキャプチャし、Azure Translator Text API に送信します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-118">The app will capture the dictation and send it to the Azure Translator Text API.</span></span>
3.  <span data-ttu-id="f28f9-119">翻訳結果は、Unity シーンの単純な UI グループに表示されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-119">The translation result will be displayed in a simple UI group in the Unity Scene.</span></span>

<span data-ttu-id="f28f9-120">このコースでは、翻訳サービスから Unity ベースのサンプルアプリケーションに結果を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-120">This course will teach you how to get the results from the Translator Service into a Unity-based sample application.</span></span> <span data-ttu-id="f28f9-121">これらの概念は、構築しているカスタムアプリケーションに適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-121">It will be up to you to apply these concepts to a custom application you might be building.</span></span>

## <a name="device-support"></a><span data-ttu-id="f28f9-122">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="f28f9-122">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="f28f9-123">コース</span><span class="sxs-lookup"><span data-stu-id="f28f9-123">Course</span></span></th><th style="width:150px"> <span data-ttu-id="f28f9-124"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="f28f9-124"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="f28f9-125"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="f28f9-125"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="f28f9-126">MR と Azure 301:言語翻訳</span><span class="sxs-lookup"><span data-stu-id="f28f9-126">MR and Azure 301: Language translation</span></span></td><td style="text-align: center;"> <span data-ttu-id="f28f9-127">✔️</span><span class="sxs-lookup"><span data-stu-id="f28f9-127">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="f28f9-128">✔️</span><span class="sxs-lookup"><span data-stu-id="f28f9-128">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="f28f9-129">このコースでは主に Windows Mixed Reality イマーシブ (VR) ヘッドセットに焦点を当てていますが、このコースで学習した内容を Microsoft HoloLens に適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-129">While this course primarily focuses on Windows Mixed Reality immersive (VR) headsets, you can also apply what you learn in this course to Microsoft HoloLens.</span></span> <span data-ttu-id="f28f9-130">このコースに従うと、HoloLens をサポートするために必要となる可能性のある変更に関する注意事項が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-130">As you follow along with the course, you will see notes on any changes you might need to employ to support HoloLens.</span></span> <span data-ttu-id="f28f9-131">HoloLens を使用する場合、音声キャプチャ中にエコーが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-131">When using HoloLens, you may notice some echo during voice capture.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f28f9-132">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="f28f9-132">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="f28f9-133">このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="f28f9-133">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="f28f9-134">また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証されたものを表します (2018 年5月)。</span><span class="sxs-lookup"><span data-stu-id="f28f9-134">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="f28f9-135">「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものよりも新しいソフトウェアで見つかったものと完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="f28f9-135">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="f28f9-136">このコースでは、次のハードウェアとソフトウェアをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-136">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="f28f9-137">開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-137">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="f28f9-138">開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="f28f9-138">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f28f9-139">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="f28f9-139">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f28f9-140">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="f28f9-140">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="f28f9-141">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="f28f9-141">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="f28f9-142">[Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](../../../hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="f28f9-142">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](../../../hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="f28f9-143">内蔵マイク付きヘッドホンのセット (ヘッドセットにマイクとスピーカーが組み込まれていない場合)</span><span class="sxs-lookup"><span data-stu-id="f28f9-143">A set of headphones with a built-in microphone (if the headset doesn't have a built-in mic and speakers)</span></span>
- <span data-ttu-id="f28f9-144">Azure のセットアップと翻訳の取得のためのインターネットアクセス</span><span class="sxs-lookup"><span data-stu-id="f28f9-144">Internet access for Azure setup and translation retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="f28f9-145">開始する前に</span><span class="sxs-lookup"><span data-stu-id="f28f9-145">Before you start</span></span>

- <span data-ttu-id="f28f9-146">このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="f28f9-146">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
- <span data-ttu-id="f28f9-147">このチュートリアルのコードを使用すると、PC に接続されている既定のマイクデバイスから録音できます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-147">The code in this tutorial will allow you to record from the default microphone device connected to your PC.</span></span> <span data-ttu-id="f28f9-148">既定のマイクデバイスが、音声のキャプチャに使用する予定のデバイスに設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-148">Make sure the default microphone device is set to the device you plan to use to capture your voice.</span></span>
- <span data-ttu-id="f28f9-149">PC がディクテーションを有効にできるようにするには、[ **設定] > [プライバシー > 音声、インク & 入力** し、[ **音声サービスをオンに** する] ボタンを選択して、「候補」と入力します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-149">To allow your PC to enable dictation, go to **Settings > Privacy > Speech, inking & typing** and select the button **Turn On speech services and typing suggestions**.</span></span>
- <span data-ttu-id="f28f9-150">ヘッドセットに接続されている (または内蔵されている) マイクとヘッドホンを使用している場合は、[ **オーディオと音声を > Mixed reality > 設定**] で "ヘッドセットを磨耗したときにヘッドセットのマイクに切り替える" オプションがオンになっていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f28f9-150">If you're using a microphone and headphones connected to (or built-in to) your headset, make sure the option “When I wear my headset, switch to headset mic” is turned on in **Settings > Mixed reality > Audio and speech**.</span></span>

   ![Mixed reality の設定](images/AzureLabs-Lab1-00-5.png)

   ![マイクの設定](images/AzureLabs-Lab1-01.png)

> [!WARNING]
> <span data-ttu-id="f28f9-153">このラボ用にイマーシブヘッドセットを開発している場合は、オーディオ出力デバイスの問題が発生する可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f28f9-153">Be aware that if you are developing for an immersive headset for this lab, you may experience audio output device issues.</span></span> <span data-ttu-id="f28f9-154">これは、unity の新しいバージョン (Unity 2018.2) で修正された Unity の問題に起因します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-154">This is due to an issue with Unity, which is fixed in later versions of Unity (Unity 2018.2).</span></span> <span data-ttu-id="f28f9-155">この問題により、Unity は実行時に既定のオーディオ出力デバイスを変更できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-155">The issue prevents Unity from changing the default audio output device at run time.</span></span> <span data-ttu-id="f28f9-156">回避策として、上記の手順を完了していることを確認し、この問題が発生したときにエディターを閉じて再度開きます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-156">As a work around, ensure you have completed the above steps, and close and re-open the Editor, when this issue presents itself.</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="f28f9-157">章 1-Azure Portal</span><span class="sxs-lookup"><span data-stu-id="f28f9-157">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="f28f9-158">Azure Translator API を使用するには、アプリケーションで使用できるようにサービスのインスタンスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-158">To use the Azure Translator API, you will need to configure an instance of the Service to be made available to your application.</span></span>

1.  <span data-ttu-id="f28f9-159">[Azure Portal](https://portal.azure.com)にログインします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-159">Log in to the  [Azure Portal](https://portal.azure.com).</span></span>

    > [!NOTE]
    > <span data-ttu-id="f28f9-160">まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-160">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="f28f9-161">このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。</span><span class="sxs-lookup"><span data-stu-id="f28f9-161">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="f28f9-162">ログインしたら、左上隅にある [ **新規** ] をクリックし、"Translator Text API" を検索します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-162">Once you are logged in, click on **New** in the top left corner and search for "Translator Text API."</span></span> <span data-ttu-id="f28f9-163">**[Enter]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-163">Select **Enter**.</span></span>

    ![新しいリソース](images/AzureLabs-Lab1-02.png)

    > [!NOTE]
    > <span data-ttu-id="f28f9-165">新しいポータルで、 **New** という単語が **リソースの作成** に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="f28f9-165">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>

3.  <span data-ttu-id="f28f9-166">新しいページには、 *Translator Text API* サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-166">The new page will provide a description of the *Translator Text API* Service.</span></span> <span data-ttu-id="f28f9-167">このページの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-167">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Translator Text API サービスの作成](images/AzureLabs-Lab1-03.png)

4.  <span data-ttu-id="f28f9-169">[ **作成**:</span><span class="sxs-lookup"><span data-stu-id="f28f9-169">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="f28f9-170">このサービスインスタンスに必要な **名前** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-170">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="f28f9-171">適切な **サブスクリプション** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-171">Select an appropriate **Subscription**.</span></span>
    3. <span data-ttu-id="f28f9-172">適切な **価格レベル** を選択します。これが *Translator Text サービス* を初めて作成する場合は、free レベル (F0) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-172">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Translator Text Service*, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="f28f9-173">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-173">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="f28f9-174">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-174">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="f28f9-175">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのラボなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-175">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these labs) under a common resource group).</span></span>

        > <span data-ttu-id="f28f9-176">Azure リソースグループの詳細については、 [リソースグループ](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f28f9-176">If you wish to read more about Azure Resource Groups, please [visit the resource group article](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="f28f9-177">リソースグループの **場所** を決定します (新しいリソースグループを作成している場合)。</span><span class="sxs-lookup"><span data-stu-id="f28f9-177">Determine the **Location** for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="f28f9-178">この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="f28f9-178">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="f28f9-179">一部の Azure 資産は、特定のリージョンでのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-179">Some Azure assets are only available in certain regions.</span></span>
    6. <span data-ttu-id="f28f9-180">また、このサービスに適用されている使用条件を理解していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-180">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="f28f9-181">**[作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-181">Select **Create**.</span></span>

        ![[作成] ボタンを選択します。](images/AzureLabs-Lab1-04.png)

5.  <span data-ttu-id="f28f9-183">[ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-183">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="f28f9-184">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-184">A notification will appear in the portal once the Service instance is created.</span></span> 

    ![Azure サービスの作成に関する通知](images/AzureLabs-Lab1-05.png)

7.  <span data-ttu-id="f28f9-186">通知をクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-186">Click on the notification to explore your new Service instance.</span></span> 

    ![リソースポップアップにアクセスします。](images/AzureLabs-Lab1-06.png)

8.  <span data-ttu-id="f28f9-188">通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-188">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="f28f9-189">新しい Translator Text API サービスインスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-189">You will be taken to your new Translator Text API Service instance.</span></span> 

    ![Translator Text API サービス] ページ](images/AzureLabs-Lab1-07.png)

9.  <span data-ttu-id="f28f9-191">このチュートリアルでは、アプリケーションがサービスの呼び出しを行う必要があります。サービスは、サービスのサブスクリプションキーを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-191">Within this tutorial, your application will need to make calls to your Service, which is done through using your Service’s Subscription Key.</span></span> 
10. <span data-ttu-id="f28f9-192">*Translator Text* サービスの [*クイックスタート*] ページで、最初の手順に移動し、*キーを取得* して [**キー** ] をクリックします (これを行うには、[サービス] ナビゲーションメニューにある青いハイパーリンクキーをクリックします。これは、キーアイコンで示されます)。</span><span class="sxs-lookup"><span data-stu-id="f28f9-192">From the *Quick start* page of your *Translator Text* Service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the Services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="f28f9-193">これにより、サービス *キー* が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-193">This will reveal your Service *Keys*.</span></span>
11. <span data-ttu-id="f28f9-194">表示されているキーの1つをコピーします。これは、プロジェクトの後半で必要になります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-194">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="f28f9-195">第2章: Unity プロジェクトを設定する</span><span class="sxs-lookup"><span data-stu-id="f28f9-195">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="f28f9-196">Mixed reality のイマーシブヘッドセットをセットアップしてテストします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-196">Set up and test your mixed reality immersive headset.</span></span>

> [!NOTE]
> <span data-ttu-id="f28f9-197">このコースでは、モーションコントローラーは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="f28f9-197">You will not need motion controllers for this course.</span></span> <span data-ttu-id="f28f9-198">イマーシブヘッドセットの設定をサポートする必要がある場合は、 [次の手順に従っ](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality)てください。</span><span class="sxs-lookup"><span data-stu-id="f28f9-198">If you need support setting up an immersive headset, please [follow these steps](https://support.microsoft.com/help/4043101/windows-10-set-up-windows-mixed-reality).</span></span>

<span data-ttu-id="f28f9-199">次に示すのは、mixed reality で開発するための一般的な設定であり、他のプロジェクトに適したテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="f28f9-199">The following is a typical set up for developing with mixed reality and, as such, is a good template for other projects:</span></span>

1.  <span data-ttu-id="f28f9-200">*Unity* を開き、[**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-200">Open *Unity* and click **New**.</span></span> 

    ![新しい Unity プロジェクトを開始します。](images/AzureLabs-Lab1-08.png)

2.  <span data-ttu-id="f28f9-202">ここで、Unity プロジェクト名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="f28f9-203">**MR_Translation** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-203">Insert **MR_Translation**.</span></span> <span data-ttu-id="f28f9-204">プロジェクトの種類が **3d** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="f28f9-205">場所を適切な *場所* に設定します (ルートディレクトリの方が適していることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="f28f9-205">Set the *Location* to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="f28f9-206">次に、[ **プロジェクトの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-206">Then, click **Create project**.</span></span>

    ![新しい Unity プロジェクトの詳細を指定します。](images/AzureLabs-Lab1-09.png)

3.  <span data-ttu-id="f28f9-208">Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="f28f9-209">[ **> の設定の編集** ] に移動し、新しいウィンドウで [ **外部ツール**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="f28f9-210">**外部スクリプトエディター** を **Visual Studio 2017** に変更します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="f28f9-211">[ **基本設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-211">Close the **Preferences** window.</span></span>

    ![スクリプトエディターの設定を更新します。](images/AzureLabs-Lab1-10.png)

4.  <span data-ttu-id="f28f9-213">次に、[**ファイル > ビルド設定**] に移動し、[プラットフォームの **切り替え**] ボタンをクリックして、プラットフォームを **ユニバーサル Windows プラットフォーム** に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-213">Next, go to **File > Build Settings** and switch the platform to **Universal Windows Platform**, by clicking on the **Switch Platform** button.</span></span>

    ![[ビルドの設定] ウィンドウで、[プラットフォーム] を [UWP] に切り替えます。](images/AzureLabs-Lab1-11.png)

5.  <span data-ttu-id="f28f9-215">[ **ファイル > ビルド設定** ] にアクセスし、次のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-215">Go to **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="f28f9-216">**ターゲットデバイス** は **、任意のデバイス** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-216">**Target Device** is set to **Any Device**.</span></span>

        > <span data-ttu-id="f28f9-217">Microsoft HoloLens の場合は、 **ターゲットデバイス** を *HoloLens* に設定します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-217">For Microsoft HoloLens, set **Target Device** to *HoloLens*.</span></span>

    2. <span data-ttu-id="f28f9-218">**ビルドの種類** が **D3D** に設定されています</span><span class="sxs-lookup"><span data-stu-id="f28f9-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="f28f9-219">**SDK** は最新の **インストール** に設定されています</span><span class="sxs-lookup"><span data-stu-id="f28f9-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="f28f9-220">**Visual Studio のバージョン** が、**インストールされている最新** バージョンに設定されています</span><span class="sxs-lookup"><span data-stu-id="f28f9-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="f28f9-221">**ビルドと実行** は **ローカルコンピューター** に設定されています</span><span class="sxs-lookup"><span data-stu-id="f28f9-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="f28f9-222">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="f28f9-223">これを行うには、[開いている **シーンの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="f28f9-224">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-224">A save window will appear.</span></span>

            ![[開いているシーンを追加] ボタンをクリックする](images/AzureLabs-Lab1-12.png)

        2. <span data-ttu-id="f28f9-226">この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン**」にします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![新しいスクリプトフォルダーの作成](images/AzureLabs-Lab1-13.png)

        3. <span data-ttu-id="f28f9-228">新しく作成した [ **シーン** ] フォルダーを開き、[ *ファイル名*: テキスト] フィールドに「 **MR_TranslationScene**」と入力して、[ **保存**] を押します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_TranslationScene**, then press **Save**.</span></span>

            ![新しいシーンに名前を付けます。](images/AzureLabs-Lab1-14.png)

            > <span data-ttu-id="f28f9-230">Unity プロジェクトに関連付けられている必要があるため、Unity のシーンを *Assets* フォルダー内に保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="f28f9-231">Unity プロジェクトを構成する一般的な方法は、シーンフォルダー (およびその他の同様のフォルダー) を作成することです。</span><span class="sxs-lookup"><span data-stu-id="f28f9-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="f28f9-232">それ以外の設定は、[ *ビルド設定*] の [既定] のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="f28f9-233">[ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![プレーヤーの設定を開きます。](images/AzureLabs-Lab1-15.png)

7. <span data-ttu-id="f28f9-235">このパネルでは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="f28f9-236">[ **その他の設定** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="f28f9-237">**スクリプトランタイムのバージョン** は **安定** している必要があります (.net 3.5 と同等)。</span><span class="sxs-lookup"><span data-stu-id="f28f9-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="f28f9-238">**バックエンド** は **.net** である必要があります</span><span class="sxs-lookup"><span data-stu-id="f28f9-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="f28f9-239">**API 互換性レベル** は **.net 4.6** である必要があります</span><span class="sxs-lookup"><span data-stu-id="f28f9-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![その他の設定を更新します。](images/AzureLabs-Lab1-16.png)
      
    2. <span data-ttu-id="f28f9-241">[ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="f28f9-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="f28f9-242">**InternetClient**</span></span>
        2. <span data-ttu-id="f28f9-243">**マイク**</span><span class="sxs-lookup"><span data-stu-id="f28f9-243">**Microphone**</span></span>

            ![発行設定を更新しています。](images/AzureLabs-Lab1-17.png)

    3. <span data-ttu-id="f28f9-245">パネルの下にある [ **XR settings** (発行の **設定**] の下にあります) で、[ **サポートされている仮想現実**] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![X R の設定を更新します。](images/AzureLabs-Lab1-18.png)

8.  <span data-ttu-id="f28f9-247">**ビルド設定** に戻ると、 *Unity C# プロジェクト* はグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-247">Back in **Build Settings**, *Unity C# Projects* is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="f28f9-248">[ビルド設定] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="f28f9-249">シーンとプロジェクトを保存します ([**ファイル] > [シーン/ファイルの保存] > [プロジェクトの保存**])。</span><span class="sxs-lookup"><span data-stu-id="f28f9-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="f28f9-250">第3章–メインカメラの設定</span><span class="sxs-lookup"><span data-stu-id="f28f9-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f28f9-251">このコースの *Unity セットアップ* コンポーネントをスキップしてコードに直接進む場合は、 [unitypackage をダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage)し、 [*カスタムパッケージ*](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 [第5章](#chapter-5--create-the-results-class)から続行してください。</span><span class="sxs-lookup"><span data-stu-id="f28f9-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to [download this .unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20301%20-%20Language%20translation/Azure-MR-301.unitypackage), import it into your project as a [*Custom Package*](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-results-class).</span></span> <span data-ttu-id="f28f9-252">引き続き Unity プロジェクトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-252">You will still need to create a Unity Project.</span></span>

1.  <span data-ttu-id="f28f9-253">[ *階層] パネル* には、 **メインカメラ** と呼ばれるオブジェクトが表示されます。このオブジェクトは、アプリケーションの "内側" にある "ヘッド" ポイントを表します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-253">In the *Hierarchy Panel*, you will find an object called **Main Camera**, this object represents your “head” point of view once you are “inside” your application.</span></span>
2.  <span data-ttu-id="f28f9-254">Unity ダッシュボードを前面に表示し、 **カメラのメイン** のユーザーオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-254">With the Unity Dashboard in front of you, select the **Main Camera GameObject**.</span></span> <span data-ttu-id="f28f9-255">[ *インスペクター] パネル* (通常はダッシュボード内の右側にあります) には、そのユーザーの *オブジェクト* のさまざまなコンポーネントが表示されます。これには、上部にある [ *変換* ]、[ *カメラ*]、および他のコンポーネントがあります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-255">You will notice that the *Inspector Panel* (generally found to the right, within the Dashboard) will show the various components of that *GameObject*, with *Transform* at the top, followed by *Camera*, and some other components.</span></span> <span data-ttu-id="f28f9-256">メインカメラの変換をリセットして、正しく配置されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-256">You will need to reset the Transform of the Main Camera, so it is positioned correctly.</span></span>
3.  <span data-ttu-id="f28f9-257">これを行うには、カメラの *変換* コンポーネントの横にある **歯車** アイコンを選択し、[**リセット**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-257">To do this, select the **Gear** icon next to the Camera’s *Transform* component, and selecting **Reset**.</span></span> 

    ![メインカメラの変換をリセットします。](images/AzureLabs-Lab1-19.png)
 
4.  <span data-ttu-id="f28f9-259">*変換* コンポーネントは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-259">The *Transform* component should then look like:</span></span>

    1. <span data-ttu-id="f28f9-260">*位置* が **0、0、0** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="f28f9-260">The *Position* is set to **0, 0, 0**</span></span>
    2. <span data-ttu-id="f28f9-261">*回転* は **0、0、0** に設定されています</span><span class="sxs-lookup"><span data-stu-id="f28f9-261">*Rotation* is set to **0, 0, 0**</span></span>
    3. <span data-ttu-id="f28f9-262">と *Scale* が **1、1、1** に設定されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-262">And *Scale* is set to **1, 1, 1**</span></span>

        ![カメラの変換情報](images/AzureLabs-Lab1-20.png)

5.  <span data-ttu-id="f28f9-264">次に、**メインカメラ** オブジェクトを選択した状態で、[*インスペクター] パネル* の一番下にある [**コンポーネントの追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-264">Next, with the **Main Camera** object selected, see the **Add Component** button located at the very bottom of the *Inspector Panel*.</span></span> 
6.  <span data-ttu-id="f28f9-265">そのボタンを選択し、次に示すように、**オーディオソース** と呼ばれるコンポーネントの [検索] フィールドに「 *audio source* 」と入力するか、セクションを移動して検索します (enter キーを押すことによっても動作します)。</span><span class="sxs-lookup"><span data-stu-id="f28f9-265">Select that button, and search (by either typing *Audio Source* into the search field or navigating the sections) for the component called **Audio Source** as shown below and select it (pressing enter on it also works).</span></span>
7.  <span data-ttu-id="f28f9-266">次に示すように、 *オーディオソース* コンポーネントが **メインカメラ** に追加されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-266">An *Audio Source* component will be added to the **Main Camera**, as demonstrated below.</span></span>

    ![オーディオソースコンポーネントを追加します。](images/AzureLabs-Lab1-21.png)

    > [!NOTE]
    > <span data-ttu-id="f28f9-268">Microsoft HoloLens の場合は、次の項目も変更する必要があります。これは、**メインカメラ** の **カメラ** コンポーネントに含まれています。</span><span class="sxs-lookup"><span data-stu-id="f28f9-268">For Microsoft HoloLens, you will need to also change the following, which are part of the **Camera** component on your **Main Camera**:</span></span>
    > - <span data-ttu-id="f28f9-269">**フラグのクリア:** 純色。</span><span class="sxs-lookup"><span data-stu-id="f28f9-269">**Clear Flags:** Solid Color.</span></span>
    > - <span data-ttu-id="f28f9-270">**背景** ' Black, Alpha 0 ' –16進数の色: #00000000。</span><span class="sxs-lookup"><span data-stu-id="f28f9-270">**Background** ‘Black, Alpha 0’ – Hex color: #00000000.</span></span>

## <a name="chapter-4--setup-debug-canvas"></a><span data-ttu-id="f28f9-271">第4章–セットアップのデバッグキャンバス</span><span class="sxs-lookup"><span data-stu-id="f28f9-271">Chapter 4 – Setup Debug Canvas</span></span>

<span data-ttu-id="f28f9-272">翻訳の入力と出力を表示するには、基本的な UI を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-272">To show the input and output of the translation, a basic UI needs to be created.</span></span> <span data-ttu-id="f28f9-273">このコースでは、データを表示する複数の ' テキスト ' オブジェクトを含む Canvas UI オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-273">For this course, you will create a Canvas UI object, with several ‘Text’ objects to show the data.</span></span>

1.  <span data-ttu-id="f28f9-274">[ *階層] パネル* の空の領域を右クリックし、[ **UI**] の下に **キャンバス** を追加します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-274">Right-click in an empty area of the *Hierarchy Panel*, under **UI**, add a **Canvas**.</span></span>

    ![新しいキャンバス UI オブジェクトを追加します。](images/AzureLabs-Lab1-22.png)

2.  <span data-ttu-id="f28f9-276">キャンバスオブジェクトを選択した状態で、[ *インスペクター] パネル* (' canvas ' コンポーネント内) で、[ **レンダリングモード** ] を [ **ワールド空間**] に変更します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-276">With the Canvas object selected, in the *Inspector Panel* (within the ‘Canvas’ component), change **Render Mode** to **World Space**.</span></span> 
3.  <span data-ttu-id="f28f9-277">次に、 *インスペクターパネルの Rect 変換* で次のパラメーターを変更します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-277">Next, change the following parameters in the *Inspector Panel’s Rect Transform*:</span></span>

    1. <span data-ttu-id="f28f9-278">*POS*  -  **X** 0 **Y** 0 **Z** 40</span><span class="sxs-lookup"><span data-stu-id="f28f9-278">*POS* -  **X** 0 **Y** 0 **Z** 40</span></span>
    2. <span data-ttu-id="f28f9-279">*幅* -500</span><span class="sxs-lookup"><span data-stu-id="f28f9-279">*Width* -    500</span></span>
    3. <span data-ttu-id="f28f9-280">*高さ* -300</span><span class="sxs-lookup"><span data-stu-id="f28f9-280">*Height* -   300</span></span>
    4. <span data-ttu-id="f28f9-281">*スケール*  - **X** 0.13 **Y** 0.13 **Z** 0.13</span><span class="sxs-lookup"><span data-stu-id="f28f9-281">*Scale* - **X** 0.13 **Y** 0.13  **Z** 0.13</span></span>

        ![キャンバスの rect 変換を更新します。](images/AzureLabs-Lab1-23.png)
 
4.  <span data-ttu-id="f28f9-283">[*階層] パネル* の **キャンバス** を右クリックし、[ **UI**] をクリックして、**パネル** を追加します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-283">Right click on the **Canvas** in the *Hierarchy Panel*, under **UI**, and add a **Panel**.</span></span> <span data-ttu-id="f28f9-284">この **パネル** には、シーンに表示されるテキストの背景が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-284">This **Panel** will provide a background to the text that you will be displaying in the scene.</span></span>
5.  <span data-ttu-id="f28f9-285">[*階層] パネル* の [ **UI**] の下にある **パネル** を右クリックし、[**テキスト] オブジェクト** を追加します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-285">Right click on the **Panel** in the *Hierarchy Panel*, under **UI**, and add a **Text object**.</span></span> <span data-ttu-id="f28f9-286">合計で4つの UI テキストオブジェクトを作成した場合は、同じプロセスを繰り返します (ヒント: 最初の "テキスト" オブジェクトを選択している場合は、Ctrl キーを押し **ながら d** キーを押すだけで、合計4つまで)。</span><span class="sxs-lookup"><span data-stu-id="f28f9-286">Repeat the same process until you have created four UI Text objects in total (Hint: if you have the first ‘Text’ object selected, you can simply press **‘Ctrl’ + ‘D’**, to duplicate it, until you have four in total).</span></span> 
6.  <span data-ttu-id="f28f9-287">各 **テキストオブジェクト** を選択し、以下の表を使用して、[ *インスペクター] パネル* でパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-287">For each **Text Object**, select it and use the below tables to set the parameters in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="f28f9-288">*Rect 変換* コンポーネントの場合:</span><span class="sxs-lookup"><span data-stu-id="f28f9-288">For the *Rect Transform* component:</span></span>

        | <span data-ttu-id="f28f9-289">名前</span><span class="sxs-lookup"><span data-stu-id="f28f9-289">Name</span></span>                   | <span data-ttu-id="f28f9-290">変換- *位置*</span><span class="sxs-lookup"><span data-stu-id="f28f9-290">Transform - *Position*</span></span>             | <span data-ttu-id="f28f9-291">幅</span><span class="sxs-lookup"><span data-stu-id="f28f9-291">Width</span></span>      | <span data-ttu-id="f28f9-292">[高さ]</span><span class="sxs-lookup"><span data-stu-id="f28f9-292">Height</span></span>    |
        |:----------------------:|:----------------------------------:|:----------:|:---------:|
        | <span data-ttu-id="f28f9-293">マイクロ電話の Statuslabel</span><span class="sxs-lookup"><span data-stu-id="f28f9-293">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="f28f9-294">**X** -80 **Y** 90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="f28f9-294">**X** -80 **Y** 90 **Z** 0</span></span>         | <span data-ttu-id="f28f9-295">300</span><span class="sxs-lookup"><span data-stu-id="f28f9-295">300</span></span>        | <span data-ttu-id="f28f9-296">30</span><span class="sxs-lookup"><span data-stu-id="f28f9-296">30</span></span>        |
        | <span data-ttu-id="f28f9-297">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="f28f9-297">AzureResponseLabel</span></span>     | <span data-ttu-id="f28f9-298">**X** -80 **Y** 30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="f28f9-298">**X** -80 **Y** 30 **Z** 0</span></span>         | <span data-ttu-id="f28f9-299">300</span><span class="sxs-lookup"><span data-stu-id="f28f9-299">300</span></span>        | <span data-ttu-id="f28f9-300">30</span><span class="sxs-lookup"><span data-stu-id="f28f9-300">30</span></span>        |
        | <span data-ttu-id="f28f9-301">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="f28f9-301">DictationLabel</span></span>         | <span data-ttu-id="f28f9-302">**X** -80 **Y** -30 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="f28f9-302">**X** -80 **Y** -30 **Z** 0</span></span>        | <span data-ttu-id="f28f9-303">300</span><span class="sxs-lookup"><span data-stu-id="f28f9-303">300</span></span>        | <span data-ttu-id="f28f9-304">30</span><span class="sxs-lookup"><span data-stu-id="f28f9-304">30</span></span>        |
        | <span data-ttu-id="f28f9-305">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="f28f9-305">TranslationResultLabel</span></span> | <span data-ttu-id="f28f9-306">**X** -80 **Y** -90 **Z** 0</span><span class="sxs-lookup"><span data-stu-id="f28f9-306">**X** -80 **Y** -90 **Z** 0</span></span>        | <span data-ttu-id="f28f9-307">300</span><span class="sxs-lookup"><span data-stu-id="f28f9-307">300</span></span>        | <span data-ttu-id="f28f9-308">30</span><span class="sxs-lookup"><span data-stu-id="f28f9-308">30</span></span>        |


    2. <span data-ttu-id="f28f9-309">**テキスト (スクリプト)** コンポーネントの場合:</span><span class="sxs-lookup"><span data-stu-id="f28f9-309">For the **Text (Script)** component:</span></span>


        | <span data-ttu-id="f28f9-310">名前</span><span class="sxs-lookup"><span data-stu-id="f28f9-310">Name</span></span>                   | <span data-ttu-id="f28f9-311">テキスト</span><span class="sxs-lookup"><span data-stu-id="f28f9-311">Text</span></span>               | <span data-ttu-id="f28f9-312">フォント サイズ</span><span class="sxs-lookup"><span data-stu-id="f28f9-312">Font Size</span></span>    |
        |:----------------------:|:------------------:|:------------:|
        | <span data-ttu-id="f28f9-313">マイクロ電話の Statuslabel</span><span class="sxs-lookup"><span data-stu-id="f28f9-313">MicrophoneStatusLabel</span></span>  | <span data-ttu-id="f28f9-314">マイクの状態:</span><span class="sxs-lookup"><span data-stu-id="f28f9-314">Microphone Status:</span></span> | <span data-ttu-id="f28f9-315">20</span><span class="sxs-lookup"><span data-stu-id="f28f9-315">20</span></span>           |
        | <span data-ttu-id="f28f9-316">AzureResponseLabel</span><span class="sxs-lookup"><span data-stu-id="f28f9-316">AzureResponseLabel</span></span>     | <span data-ttu-id="f28f9-317">Azure Web 応答</span><span class="sxs-lookup"><span data-stu-id="f28f9-317">Azure Web Response</span></span> | <span data-ttu-id="f28f9-318">20</span><span class="sxs-lookup"><span data-stu-id="f28f9-318">20</span></span>           |
        | <span data-ttu-id="f28f9-319">DictationLabel</span><span class="sxs-lookup"><span data-stu-id="f28f9-319">DictationLabel</span></span>         |   <span data-ttu-id="f28f9-320">先ほど言ったことは、</span><span class="sxs-lookup"><span data-stu-id="f28f9-320">You just said:</span></span>   | <span data-ttu-id="f28f9-321">20</span><span class="sxs-lookup"><span data-stu-id="f28f9-321">20</span></span>           |
        | <span data-ttu-id="f28f9-322">TranslationResultLabel</span><span class="sxs-lookup"><span data-stu-id="f28f9-322">TranslationResultLabel</span></span> |    <span data-ttu-id="f28f9-323">変換:</span><span class="sxs-lookup"><span data-stu-id="f28f9-323">Translation:</span></span>    | <span data-ttu-id="f28f9-324">20</span><span class="sxs-lookup"><span data-stu-id="f28f9-324">20</span></span>           |

        ![UI ラベルに対応する値を入力します。](images/AzureLabs-Lab1-24.png)

    3. <span data-ttu-id="f28f9-326">また、フォントスタイルを **太字** にします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-326">Also, make the Font Style **Bold**.</span></span> <span data-ttu-id="f28f9-327">これにより、テキストが読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-327">This will make the text easier to read.</span></span>

        ![太字のフォント。](images/AzureLabs-Lab1-25.png)

7.  <span data-ttu-id="f28f9-329">[第5章](#chapter-5--create-the-results-class)で作成された各 *ui テキストオブジェクト* に対して、新しい *子* **ui テキストオブジェクト** を作成します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-329">For each *UI Text object* created in [Chapter 5](#chapter-5--create-the-results-class), create a new *child* **UI Text object**.</span></span> <span data-ttu-id="f28f9-330">これらの子は、アプリケーションの出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-330">These children will display the output of the application.</span></span> <span data-ttu-id="f28f9-331">*子* オブジェクトを作成するには、目的の親を右クリックし (例:*マイクロラベル statuslabel*)、[ **UI** ] を選択し、[**テキスト**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-331">Create *child* objects through right-clicking your intended parent (e.g. *MicrophoneStatusLabel*) and then select **UI** and then select **Text**.</span></span>
8.  <span data-ttu-id="f28f9-332">これらの各子を選択し、以下の表を使用して、[インスペクター] パネルでパラメーターを設定します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-332">For each of these children, select it and use the below tables to set the parameters in the Inspector Panel.</span></span>

    1. <span data-ttu-id="f28f9-333">**Rect 変換** コンポーネントの場合:</span><span class="sxs-lookup"><span data-stu-id="f28f9-333">For the **Rect Transform** component:</span></span>

        | <span data-ttu-id="f28f9-334">名前</span><span class="sxs-lookup"><span data-stu-id="f28f9-334">Name</span></span>                  | <span data-ttu-id="f28f9-335">変換- *位置*</span><span class="sxs-lookup"><span data-stu-id="f28f9-335">Transform - *Position*</span></span> | <span data-ttu-id="f28f9-336">幅</span><span class="sxs-lookup"><span data-stu-id="f28f9-336">Width</span></span>      | <span data-ttu-id="f28f9-337">[高さ]</span><span class="sxs-lookup"><span data-stu-id="f28f9-337">Height</span></span>    |
        |:---------------------:|:----------------------:|:----------:|:---------:|
        | <span data-ttu-id="f28f9-338">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="f28f9-338">MicrophoneStatusText</span></span>  | <span data-ttu-id="f28f9-339">X 0 Y ~ 30 Z 0</span><span class="sxs-lookup"><span data-stu-id="f28f9-339">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="f28f9-340">300</span><span class="sxs-lookup"><span data-stu-id="f28f9-340">300</span></span>        | <span data-ttu-id="f28f9-341">30</span><span class="sxs-lookup"><span data-stu-id="f28f9-341">30</span></span>        |
        | <span data-ttu-id="f28f9-342">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="f28f9-342">AzureResponseText</span></span>     | <span data-ttu-id="f28f9-343">X 0 Y ~ 30 Z 0</span><span class="sxs-lookup"><span data-stu-id="f28f9-343">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="f28f9-344">300</span><span class="sxs-lookup"><span data-stu-id="f28f9-344">300</span></span>        | <span data-ttu-id="f28f9-345">30</span><span class="sxs-lookup"><span data-stu-id="f28f9-345">30</span></span>        |
        | <span data-ttu-id="f28f9-346">DictationText</span><span class="sxs-lookup"><span data-stu-id="f28f9-346">DictationText</span></span>         | <span data-ttu-id="f28f9-347">X 0 Y ~ 30 Z 0</span><span class="sxs-lookup"><span data-stu-id="f28f9-347">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="f28f9-348">300</span><span class="sxs-lookup"><span data-stu-id="f28f9-348">300</span></span>        | <span data-ttu-id="f28f9-349">30</span><span class="sxs-lookup"><span data-stu-id="f28f9-349">30</span></span>        |
        | <span data-ttu-id="f28f9-350">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="f28f9-350">TranslationResultText</span></span> | <span data-ttu-id="f28f9-351">X 0 Y ~ 30 Z 0</span><span class="sxs-lookup"><span data-stu-id="f28f9-351">X 0 Y -30 Z 0</span></span>          | <span data-ttu-id="f28f9-352">300</span><span class="sxs-lookup"><span data-stu-id="f28f9-352">300</span></span>        | <span data-ttu-id="f28f9-353">30</span><span class="sxs-lookup"><span data-stu-id="f28f9-353">30</span></span>        |

    2. <span data-ttu-id="f28f9-354">**テキスト (スクリプト)** コンポーネントの場合:</span><span class="sxs-lookup"><span data-stu-id="f28f9-354">For the **Text (Script)** component:</span></span>

        | <span data-ttu-id="f28f9-355">名前</span><span class="sxs-lookup"><span data-stu-id="f28f9-355">Name</span></span>                  | <span data-ttu-id="f28f9-356">テキスト</span><span class="sxs-lookup"><span data-stu-id="f28f9-356">Text</span></span>          | <span data-ttu-id="f28f9-357">フォント サイズ</span><span class="sxs-lookup"><span data-stu-id="f28f9-357">Font Size</span></span>    |
        |:---------------------:|:-------------:|:------------:|
        | <span data-ttu-id="f28f9-358">MicrophoneStatusText</span><span class="sxs-lookup"><span data-stu-id="f28f9-358">MicrophoneStatusText</span></span>  |      <span data-ttu-id="f28f9-359">??</span><span class="sxs-lookup"><span data-stu-id="f28f9-359">??</span></span>       | <span data-ttu-id="f28f9-360">20</span><span class="sxs-lookup"><span data-stu-id="f28f9-360">20</span></span>           |
        | <span data-ttu-id="f28f9-361">AzureResponseText</span><span class="sxs-lookup"><span data-stu-id="f28f9-361">AzureResponseText</span></span>     |      <span data-ttu-id="f28f9-362">??</span><span class="sxs-lookup"><span data-stu-id="f28f9-362">??</span></span>       | <span data-ttu-id="f28f9-363">20</span><span class="sxs-lookup"><span data-stu-id="f28f9-363">20</span></span>           |
        | <span data-ttu-id="f28f9-364">DictationText</span><span class="sxs-lookup"><span data-stu-id="f28f9-364">DictationText</span></span>         |      <span data-ttu-id="f28f9-365">??</span><span class="sxs-lookup"><span data-stu-id="f28f9-365">??</span></span>       | <span data-ttu-id="f28f9-366">20</span><span class="sxs-lookup"><span data-stu-id="f28f9-366">20</span></span>           |
        | <span data-ttu-id="f28f9-367">TranslationResultText</span><span class="sxs-lookup"><span data-stu-id="f28f9-367">TranslationResultText</span></span> |      <span data-ttu-id="f28f9-368">??</span><span class="sxs-lookup"><span data-stu-id="f28f9-368">??</span></span>       | <span data-ttu-id="f28f9-369">20</span><span class="sxs-lookup"><span data-stu-id="f28f9-369">20</span></span>           |

9. <span data-ttu-id="f28f9-370">次に、各テキストコンポーネントの [中央揃え] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-370">Next, select the 'centre' alignment option for each text component:</span></span>

    ![テキストを整列します。](images/AzureLabs-Lab1-26.png)

10. <span data-ttu-id="f28f9-372">**子 UI テキスト** オブジェクトが簡単に読み取れるようにするには、*色* を変更します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-372">To ensure the **child UI Text** objects are easily readable, change their *Color*.</span></span> <span data-ttu-id="f28f9-373">これを行うには、[ *色*] の横にあるバー (現在は "Black") をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-373">Do this by clicking on the bar (currently ‘Black’) next to *Color*.</span></span> 

    ![UI テキストの出力に対応する値を入力します。](images/AzureLabs-Lab1-27.png)
 
11. <span data-ttu-id="f28f9-375">次に、新しい小さな *色* のウィンドウで、 *16 進数の色* を **0032EAFF** に変更します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-375">Then, in the new, little, *Color* window, change the *Hex Color* to: **0032EAFF**</span></span>

    ![色を青に更新します。](images/AzureLabs-Lab1-28.png)
 
12. <span data-ttu-id="f28f9-377">**UI** の表示方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-377">Below is how the **UI** should look.</span></span>
    1.  <span data-ttu-id="f28f9-378">[ *階層] パネル* で、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-378">In the *Hierarchy Panel*:</span></span>

        ![指定された構造に階層があること。](images/AzureLabs-Lab1-29.png)

    2.  <span data-ttu-id="f28f9-380">*シーン\*\*ビューとゲームビュー* で、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-380">In the *Scene* and *Game Views*:</span></span>

        ![シーンビューとゲームビューを同じ構造にします。](images/AzureLabs-Lab1-30.png)

## <a name="chapter-5--create-the-results-class"></a><span data-ttu-id="f28f9-382">Chapter 5 – Results クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="f28f9-382">Chapter 5 – Create the Results class</span></span>

<span data-ttu-id="f28f9-383">作成する必要のある最初のスクリプトは、 *results* クラスです。このクラスは、翻訳の結果を確認する手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-383">The first script you need to create is the *Results* class, which is responsible for providing a way to see the results of translation.</span></span> <span data-ttu-id="f28f9-384">クラスは、次のものを格納して表示します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-384">The Class stores and displays the following:</span></span> 

- <span data-ttu-id="f28f9-385">Azure からの応答結果。</span><span class="sxs-lookup"><span data-stu-id="f28f9-385">The response result from Azure.</span></span>
- <span data-ttu-id="f28f9-386">マイクの状態。</span><span class="sxs-lookup"><span data-stu-id="f28f9-386">The microphone status.</span></span> 
- <span data-ttu-id="f28f9-387">ディクテーションの結果 (音声テキスト)。</span><span class="sxs-lookup"><span data-stu-id="f28f9-387">The result of the dictation (voice to text).</span></span>
- <span data-ttu-id="f28f9-388">変換の結果。</span><span class="sxs-lookup"><span data-stu-id="f28f9-388">The result of the translation.</span></span>

<span data-ttu-id="f28f9-389">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="f28f9-389">To create this class:</span></span> 

1.  <span data-ttu-id="f28f9-390">[ *プロジェクト] パネル* 内を右クリックし、[ **> フォルダーの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-390">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="f28f9-391">フォルダーに **スクリプト** の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-391">Name the folder **Scripts**.</span></span> 
 
    ![Scripts フォルダーを作成します。](images/AzureLabs-Lab1-31.png)

    ![Scripts フォルダーを開きます。](images/AzureLabs-Lab1-32.png)
 
2.  <span data-ttu-id="f28f9-394">**Scripts** フォルダー create を使用して、ダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-394">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="f28f9-395">次に、そのフォルダー内でを右クリックし、[ **Create >** Then **C# Script**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-395">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="f28f9-396">スクリプトの *結果* に名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-396">Name the script *Results*.</span></span> 

    ![最初のスクリプトを作成します。](images/AzureLabs-Lab1-33.png)
 
3.  <span data-ttu-id="f28f9-398">新しい *結果* スクリプトをダブルクリックして、 **Visual Studio** で開きます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-398">Double click on the new *Results* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="f28f9-399">次の名前空間を挿入します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-399">Insert the following namespaces:</span></span>

    ```cs
        using UnityEngine;
        using UnityEngine.UI;
    ```

5.  <span data-ttu-id="f28f9-400">クラス内で、次の変数を挿入します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-400">Inside the Class insert the following variables:</span></span>

    ```cs
        public static Results instance;
   
        [HideInInspector] 
        public string azureResponseCode;
   
        [HideInInspector] 
        public string translationResult;
   
        [HideInInspector] 
        public string dictationResult;
   
        [HideInInspector] 
        public string micStatus;
   
        public Text microphoneStatusText;
   
        public Text azureResponseText;
   
        public Text dictationText;
   
        public Text translationResultText;
    ```

6.  <span data-ttu-id="f28f9-401">次に、起動される *()* メソッドを追加します。このメソッドは、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-401">Then add the *Awake()* method, which will be called when the class initializes.</span></span> 

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this;           
        } 
    ```

7.  <span data-ttu-id="f28f9-402">最後に、さまざまな結果情報を UI に出力するメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-402">Finally, add the methods which are responsible for outputting the various results information to the UI.</span></span> 

    ```csharp
        /// <summary>
        /// Stores the Azure response value in the static instance of Result class.
        /// </summary>
        public void SetAzureResponse(string result)
        {
            azureResponseCode = result;
            azureResponseText.text = azureResponseCode;
        }
   
        /// <summary>
        /// Stores the translated result from dictation in the static instance of Result class. 
        /// </summary>
        public void SetDictationResult(string result)
        {
            dictationResult = result;
            dictationText.text = dictationResult;
        }
   
        /// <summary>
        /// Stores the translated result from Azure Service in the static instance of Result class. 
        /// </summary>
        public void SetTranslatedResult(string result)
        {
            translationResult = result;
            translationResultText.text = translationResult;
        }
   
        /// <summary>
        /// Stores the status of the Microphone in the static instance of Result class. 
        /// </summary>
        public void SetMicrophoneStatus(string result)
        {
            micStatus = result;
            microphoneStatusText.text = micStatus;
        }
    ```

8.  <span data-ttu-id="f28f9-403">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="f28f9-403">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-6--create-the-microphonemanager-class"></a><span data-ttu-id="f28f9-404">Chapter 6 – *MicrophoneManager* クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="f28f9-404">Chapter 6 – Create the *MicrophoneManager* class</span></span>

<span data-ttu-id="f28f9-405">2番目に作成するクラスは、 *MicrophoneManager* です。</span><span class="sxs-lookup"><span data-stu-id="f28f9-405">The second class you are going to create is the *MicrophoneManager*.</span></span>

<span data-ttu-id="f28f9-406">このクラスの役割は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f28f9-406">This class is responsible for:</span></span>

- <span data-ttu-id="f28f9-407">ヘッドセットまたはコンピューターに接続されている記録デバイスを検出する (どちらかの既定値)。</span><span class="sxs-lookup"><span data-stu-id="f28f9-407">Detecting the recording device attached to the headset or machine (whichever is the default).</span></span>
- <span data-ttu-id="f28f9-408">オーディオ (音声) をキャプチャし、ディクテーションを使用して文字列として格納します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-408">Capture the audio (voice) and use dictation to store it as a string.</span></span>
- <span data-ttu-id="f28f9-409">音声が一時停止したら、ディクテーションを Translator クラスに送信します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-409">Once the voice has paused, submit the dictation to the Translator class.</span></span>
- <span data-ttu-id="f28f9-410">必要に応じて、音声キャプチャを停止できるメソッドをホストします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-410">Host a method that can stop the voice capture if desired.</span></span>

<span data-ttu-id="f28f9-411">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="f28f9-411">To create this class:</span></span> 
1.  <span data-ttu-id="f28f9-412">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-412">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="f28f9-413">**Scripts** フォルダー内を右クリックし、[ **Create > C# Script**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="f28f9-414">スクリプトに *MicrophoneManager* という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-414">Name the script *MicrophoneManager*.</span></span> 
3.  <span data-ttu-id="f28f9-415">新しいスクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-415">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="f28f9-416">*MicrophoneManager* クラスの先頭にある次の名前空間を更新します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-416">Update the namespaces to be the same as the following, at the top of the *MicrophoneManager* class:</span></span>

    ```csharp
        using UnityEngine; 
        using UnityEngine.Windows.Speech;
    ```

5.  <span data-ttu-id="f28f9-417">次に、 *MicrophoneManager* クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-417">Then, add the following variables inside the *MicrophoneManager* class:</span></span>

    ```csharp
        // Help to access instance of this object 
        public static MicrophoneManager instance; 
     
        // AudioSource component, provides access to mic 
        private AudioSource audioSource; 
   
        // Flag indicating mic detection 
        private bool microphoneDetected; 
   
        // Component converting speech to text 
        private DictationRecognizer dictationRecognizer; 
    ```

6.  <span data-ttu-id="f28f9-418">起動可能な *()* メソッドと *Start ()* メソッドのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-418">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="f28f9-419">これらは、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-419">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton 
            instance = this; 
        } 
    
        void Start() 
        { 
            //Use Unity Microphone class to detect devices and setup AudioSource 
            if(Microphone.devices.Length > 0) 
            { 
                Results.instance.SetMicrophoneStatus("Initialising..."); 
                audioSource = GetComponent<AudioSource>(); 
                microphoneDetected = true; 
            } 
            else 
            { 
                Results.instance.SetMicrophoneStatus("No Microphone detected"); 
            } 
        } 
    ```

7.  <span data-ttu-id="f28f9-420">*Update ()* メソッドは、このクラスでは使用されないため、*削除* できます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-420">You can *delete* the *Update()* method since this class will not use it.</span></span>
8.  <span data-ttu-id="f28f9-421">次に、アプリが音声キャプチャを開始および停止するために使用するメソッドと、間もなくビルドする *Translator* クラスに渡すメソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="f28f9-421">Now you need the methods that the App uses to start and stop the voice capture, and pass it to the *Translator* class, that you will build soon.</span></span> <span data-ttu-id="f28f9-422">次のコードをコピーし、 *Start ()* メソッドの下に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-422">Copy the following code and paste it beneath the *Start()* method.</span></span>

    ```csharp
        /// <summary> 
        /// Start microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StartCapturingAudio() 
        { 
            if(microphoneDetected) 
            {               
                // Start dictation 
                dictationRecognizer = new DictationRecognizer(); 
                dictationRecognizer.DictationResult += DictationRecognizer_DictationResult; 
                dictationRecognizer.Start(); 
    
                // Update UI with mic status 
                Results.instance.SetMicrophoneStatus("Capturing..."); 
            }      
        } 
 
        /// <summary> 
        /// Stop microphone capture. Debugging message is delivered to the Results class. 
        /// </summary> 
        public void StopCapturingAudio() 
        { 
            Results.instance.SetMicrophoneStatus("Mic sleeping"); 
            Microphone.End(null); 
            dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult; 
            dictationRecognizer.Dispose(); 
        }
    ```

    > [!TIP]
    > <span data-ttu-id="f28f9-423">このアプリケーションではこれを使用しませんが、アプリケーションでのオーディオのキャプチャを停止する機能を実装する場合は、 *Stopcapturingaudio ()* メソッドもここで提供されています。</span><span class="sxs-lookup"><span data-stu-id="f28f9-423">Though this application will not make use of it, the *StopCapturingAudio()* method has also been provided here, should you want to implement the ability to stop capturing audio in your application.</span></span>

9.  <span data-ttu-id="f28f9-424">次に、音声が停止したときに呼び出されるディクテーションハンドラーを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-424">You now need to add a Dictation Handler that will be invoked when the voice stops.</span></span> <span data-ttu-id="f28f9-425">このメソッドは、ディクテーションされたテキストを *Translator* クラスに渡します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-425">This method will then pass the dictated text to the *Translator* class.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// Debugging message is delivered to the Results class.
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Results.instance.SetDictationResult(text);
   
            // Start the coroutine that process the dictation through Azure 
            StartCoroutine(Translator.instance.TranslateWithUnityNetworking(text));   
        }
    ```

10. <span data-ttu-id="f28f9-426">Unity に戻る前に、変更内容を Visual Studio に保存してください。</span><span class="sxs-lookup"><span data-stu-id="f28f9-426">Be sure to save your changes in Visual Studio before returning to Unity.</span></span>

> [!WARNING]  
> <span data-ttu-id="f28f9-427">この時点で、 *Unity エディターのコンソール* パネルにエラーが表示されます ("Translator ' という名前は存在しません...")。</span><span class="sxs-lookup"><span data-stu-id="f28f9-427">At this point you will notice an error appearing in the *Unity Editor Console* Panel (“The name ‘Translator’ does not exist...”).</span></span> <span data-ttu-id="f28f9-428">これは、コードが *トランスレーター* クラスを参照するためです。このクラスは、次の章で作成します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-428">This is because the code references the *Translator* class, which you will create in the next chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-translator-service"></a><span data-ttu-id="f28f9-429">第7章– Azure と translator サービスへの呼び出し</span><span class="sxs-lookup"><span data-stu-id="f28f9-429">Chapter 7 – Call to Azure and translator service</span></span>

<span data-ttu-id="f28f9-430">作成する必要がある最後のスクリプトは、 *Translator* クラスです。</span><span class="sxs-lookup"><span data-stu-id="f28f9-430">The last script you need to create is the *Translator* class.</span></span> 

<span data-ttu-id="f28f9-431">このクラスの役割は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f28f9-431">This class is responsible for:</span></span>

-   <span data-ttu-id="f28f9-432">*Azure* を使用したアプリの認証 (**認証トークン** の交換)。</span><span class="sxs-lookup"><span data-stu-id="f28f9-432">Authenticating the App with *Azure*, in exchange for an **Auth Token**.</span></span>
-   <span data-ttu-id="f28f9-433">**認証トークン** を使用して、翻訳するテキスト ( *MicrophoneManager* クラスから受信) を送信します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-433">Use the **Auth Token** to submit text (received from the *MicrophoneManager* Class) to be translated.</span></span>
-   <span data-ttu-id="f28f9-434">変換された結果を受け取り、それを *結果* クラスに渡して UI で視覚化されるようにします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-434">Receive the translated result and pass it to the *Results* Class to be visualized in the UI.</span></span>

<span data-ttu-id="f28f9-435">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="f28f9-435">To create this Class:</span></span> 
1.  <span data-ttu-id="f28f9-436">前に作成した **Scripts** フォルダーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-436">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="f28f9-437">[ **プロジェクト] パネル** を右クリックし、[ **> C# スクリプト**] を作成します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-437">Right-click in the **Project Panel**, **Create > C# Script**.</span></span> <span data-ttu-id="f28f9-438">スクリプト *変換* プログラムを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-438">Call the script *Translator*.</span></span>
3.  <span data-ttu-id="f28f9-439">新しい *Translator* スクリプトをダブルクリックして、 **Visual Studio で** 開きます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-439">Double click on the new *Translator* script to open it **with Visual Studio**.</span></span>
4.  <span data-ttu-id="f28f9-440">ファイルの先頭に次の名前空間を追加します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-440">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Xml.Linq;
        using UnityEngine;
        using UnityEngine.Networking;
    ```

5.  <span data-ttu-id="f28f9-441">次に、 *Translator* クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-441">Then add the following variables inside the *Translator* class:</span></span>

    ```csharp
        public static Translator instance; 
        private string translationTokenEndpoint = "https://api.cognitive.microsoft.com/sts/v1.0/issueToken"; 
        private string translationTextEndpoint = "https://api.microsofttranslator.com/v2/http.svc/Translate?"; 
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key"; 
    
        //Substitute the value of authorizationKey with your own Key 
        private const string authorizationKey = "-InsertYourAuthKeyHere-"; 
        private string authorizationToken; 
    
        // languages set below are: 
        // English 
        // French 
        // Italian 
        // Japanese 
        // Korean 
        public enum Languages { en, fr, it, ja, ko }; 
        public Languages from = Languages.en; 
        public Languages to = Languages.it; 
    ```

    > [!NOTE]
    > - <span data-ttu-id="f28f9-442">言語の **列挙** に挿入される言語は、単純な例です。</span><span class="sxs-lookup"><span data-stu-id="f28f9-442">The languages inserted into the languages **enum** are just examples.</span></span> <span data-ttu-id="f28f9-443">必要に応じて、さらに自由に追加できます。API は、 [60 を超える言語](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (Klingon を含む) をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f28f9-443">Feel free to add more if you wish; the [API supports over 60 languages](https://docs.microsoft.com/azure/cognitive-services/translator/languages) (including Klingon)!</span></span>
    > - <span data-ttu-id="f28f9-444">[使用可能な言語についてはより対話的なページ](https://www.microsoft.com/translator/business/languages/)がありますが、サイトの言語が ' ' に設定されている場合にのみページが動作しているように見えますが、Microsoft サイトではネイティブ言語にリダイレクトされる可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f28f9-444">There is a [more interactive page covering available languages](https://www.microsoft.com/translator/business/languages/), though be aware the page only appears to work when the site language is set to '' (and the Microsoft site will likely redirect to your native language).</span></span> <span data-ttu-id="f28f9-445">ページの下部にあるサイトの言語を変更するか、URL を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-445">You can change site language at the bottom of the page or by altering the URL.</span></span>
    > - <span data-ttu-id="f28f9-446">上記のコードスニペットの **Authorizationkey** 値は、 *Azure Translator Text API* をサブスクライブしたときに受け取った **キー** である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-446">The **authorizationKey** value, in the above code snippet, must be the **Key**  you received when you subscribed to the *Azure Translator Text API*.</span></span> <span data-ttu-id="f28f9-447">これについては、 [第1章](#chapter-1--the-azure-portal)で説明しました。</span><span class="sxs-lookup"><span data-stu-id="f28f9-447">This was covered in [Chapter 1](#chapter-1--the-azure-portal).</span></span>

6.  <span data-ttu-id="f28f9-448">起動可能な *()* メソッドと *Start ()* メソッドのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-448">Code for the *Awake()* and *Start()* methods now needs to be added.</span></span> 
7.  <span data-ttu-id="f28f9-449">この場合、コードは、*トークン* を取得するために、承認キーを使用して *Azure* を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-449">In this case, the code will make a call to *Azure* using the authorization Key, to get a *Token*.</span></span>

    ```csharp
        private void Awake() 
        { 
            // Set this class to behave similar to singleton  
            instance = this; 
        } 
    
        // Use this for initialization  
        void Start() 
        { 
            // When the application starts, request an auth token 
            StartCoroutine("GetTokenCoroutine", authorizationKey); 
        }
    ```

    > [!NOTE]
    > <span data-ttu-id="f28f9-450">トークンは10分後に期限切れになります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-450">The token will expire after 10 minutes.</span></span> <span data-ttu-id="f28f9-451">アプリのシナリオによっては、同じコルーチン呼び出しを複数回行うことが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-451">Depending on the scenario for your app, you might have to make the same coroutine call multiple times.</span></span>

8.  <span data-ttu-id="f28f9-452">トークンを取得するコルーチンは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f28f9-452">The coroutine to obtain the Token is the following:</span></span>

    ```csharp
        /// <summary> 
        /// Request a Token from Azure Translation Service by providing the access key. 
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        private IEnumerator GetTokenCoroutine(string key)
        {
            if (string.IsNullOrEmpty(key))
            {
                throw new InvalidOperationException("Authorization key not set.");
            }

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(translationTokenEndpoint, string.Empty))
            {
                unityWebRequest.SetRequestHeader("Ocp-Apim-Subscription-Key", key);
                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;

                // Update the UI with the response code 
                Results.instance.SetAzureResponse(responseCode.ToString());

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Results.instance.azureResponseText.text = unityWebRequest.error;
                    yield return null;
                }
                else
                {
                    authorizationToken = unityWebRequest.downloadHandler.text;
                }
            }

            // After receiving the token, begin capturing Audio with the MicrophoneManager Class 
            MicrophoneManager.instance.StartCapturingAudio();
        }
    ```

    > [!WARNING]
    > <span data-ttu-id="f28f9-453">IEnumerator メソッド **GetTokenCoroutine ()** の名前を編集する場合は、上記のコードの *StartCoroutine* と *StopCoroutine* の呼び出し文字列値を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-453">If you edit the name of the IEnumerator method **GetTokenCoroutine()**, you need to update the *StartCoroutine* and *StopCoroutine* call string values in the above code.</span></span> <span data-ttu-id="f28f9-454">[Unity のドキュメントに従って](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html)、特定の *コルーチン* を停止するには、文字列値メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-454">[As per Unity documentation](https://docs.unity3d.com/ScriptReference/MonoBehaviour.StartCoroutine.html), to Stop a specific *Coroutine*, you need to use the string value method.</span></span>

9.  <span data-ttu-id="f28f9-455">次に、 *MicrophoneManager* クラスによって受信されたテキストの翻訳を取得するために、("サポート" ストリームメソッドを含む) コルーチンを追加します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-455">Next, add the coroutine (with a “support” stream method right below it) to obtain the translation of the text received by the *MicrophoneManager* class.</span></span> <span data-ttu-id="f28f9-456">このコードは、 *Azure Translator Text API* に送信するクエリ文字列を作成し、内部 Unity UnityWebRequest クラスを使用して、クエリ文字列を使用してエンドポイントへの ' Get ' 呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="f28f9-456">This code creates a query string to send to the *Azure Translator Text API*, and then uses the internal Unity UnityWebRequest class to make a ‘Get’ call to the endpoint with the query string.</span></span> <span data-ttu-id="f28f9-457">結果を使用して、結果オブジェクトの翻訳を設定します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-457">The result is then used to set the translation in your Results object.</span></span> <span data-ttu-id="f28f9-458">次のコードは、の実装を示しています。</span><span class="sxs-lookup"><span data-stu-id="f28f9-458">The code below shows the implementation:</span></span>

    ```csharp
        /// <summary> 
        /// Request a translation from Azure Translation Service by providing a string.  
        /// Debugging result is delivered to the Results class. 
        /// </summary> 
        public IEnumerator TranslateWithUnityNetworking(string text)
        {
            // This query string will contain the parameters for the translation 
            string queryString = string.Concat("text=", Uri.EscapeDataString(text), "&from=", from, "&to=", to);

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Get(translationTextEndpoint + queryString))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + authorizationToken);
                unityWebRequest.SetRequestHeader("Accept", "application/xml");
                yield return unityWebRequest.SendWebRequest();

                if (unityWebRequest.isNetworkError || unityWebRequest.isHttpError)
                {
                    Debug.Log(unityWebRequest.error);
                    yield return null;
                }

                // Parse out the response text from the returned Xml
                string result = XElement.Parse(unityWebRequest.downloadHandler.text).Value;
                Results.instance.SetTranslatedResult(result);
            }
        }
    ```

10. <span data-ttu-id="f28f9-459">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="f28f9-459">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-8--configure-the-unity-scene"></a><span data-ttu-id="f28f9-460">Chapter 8 – Unity シーンの構成</span><span class="sxs-lookup"><span data-stu-id="f28f9-460">Chapter 8 – Configure the Unity Scene</span></span>

1.  <span data-ttu-id="f28f9-461">Unity エディターに戻り、[**スクリプト**] フォルダーの [ *Results* *] クラスを* クリックして、[*階層] パネル* の [**メインカメラ**] オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-461">Back in the Unity Editor, click and drag the *Results* class *from* the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
2.  <span data-ttu-id="f28f9-462">**メインカメラ** をクリックし、[*インスペクター] パネル* を確認します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-462">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="f28f9-463">新しく追加された *スクリプト* コンポーネント内には、空の値を持つ4つのフィールドがあることがわかります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-463">You will notice that within the newly added *Script* component, there are four fields with empty values.</span></span> <span data-ttu-id="f28f9-464">これらは、コード内のプロパティへの出力参照です。</span><span class="sxs-lookup"><span data-stu-id="f28f9-464">These are the output references to the properties in the code.</span></span> 
3.  <span data-ttu-id="f28f9-465">次の図に示すように、該当する **テキスト** オブジェクトを [ *階層] パネル* から4つのスロットにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-465">Drag the appropriate **Text** objects from the *Hierarchy Panel* to those four slots, as shown in the image below.</span></span>

    ![指定された値でターゲット参照を更新します。](images/AzureLabs-Lab1-34.png)
  
4.  <span data-ttu-id="f28f9-467">次に、[**スクリプト**] フォルダーの *Translator* クラスをクリックして、[*階層] パネル* の [**メインカメラ**] オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-467">Next, click and drag the *Translator* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
5.  <span data-ttu-id="f28f9-468">次に、[**スクリプト**] フォルダーの *MicrophoneManager* クラスをクリックして、[*階層] パネル* の [**メインカメラ**] オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-468">Then, click and drag the *MicrophoneManager* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 
6.  <span data-ttu-id="f28f9-469">最後に、 **メインカメラ** をクリックし、[ *インスペクター] パネル* を確認します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-469">Lastly, click on the **Main Camera** and look at the *Inspector Panel*.</span></span> <span data-ttu-id="f28f9-470">ドラッグしたスクリプトには、2つのドロップダウンボックスがあり、それらを使用して言語を設定できることがわかります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-470">You will notice that in the script you dragged on, there are two drop down boxes that will allow you to set the languages.</span></span>
 
    ![目的の翻訳言語が入力されていることを確認します。](images/AzureLabs-Lab1-35.png)

## <a name="chapter-9--test-in-mixed-reality"></a><span data-ttu-id="f28f9-472">第9章– mixed reality でのテスト</span><span class="sxs-lookup"><span data-stu-id="f28f9-472">Chapter 9 – Test in mixed reality</span></span>

<span data-ttu-id="f28f9-473">この時点で、シーンが正しく実装されていることをテストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-473">At this point you need to test that the Scene has been properly implemented.</span></span>

<span data-ttu-id="f28f9-474">次のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-474">Ensure that:</span></span>

- <span data-ttu-id="f28f9-475">[章 1](#chapter-1--the-azure-portal)で説明したすべての設定が正しく設定されています。</span><span class="sxs-lookup"><span data-stu-id="f28f9-475">All the settings mentioned in [Chapter 1](#chapter-1--the-azure-portal) are set correctly.</span></span> 
- <span data-ttu-id="f28f9-476">*Results*、 *Translator*、および *MicrophoneManager* の各スクリプトは、**メインカメラ** オブジェクトにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-476">The *Results*, *Translator*, and *MicrophoneManager*, scripts are attached to the **Main Camera** object.</span></span> 
- <span data-ttu-id="f28f9-477">*Azure Translator Text API* サービス **キー** は、 *Translator* スクリプト内の **authorizationkey** 変数内に配置しました。</span><span class="sxs-lookup"><span data-stu-id="f28f9-477">You have placed your *Azure Translator Text API* Service **Key** within the **authorizationKey** variable within the *Translator* Script.</span></span>  
- <span data-ttu-id="f28f9-478">*メインカメラインスペクターパネル* のすべてのフィールドが適切に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-478">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
- <span data-ttu-id="f28f9-479">マイクがシーンの実行中に機能している (そうでない場合、接続されているマイクが *既定* のデバイスであること、および [Windows 内で正しく設定](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)されていることを確認してください)。</span><span class="sxs-lookup"><span data-stu-id="f28f9-479">Your microphone is working when running your scene (if not, check that your attached microphone is the *default* device, and that you have [set it up correctly within Windows](https://support.microsoft.com/help/4027981/windows-how-to-set-up-and-test-microphones-in-windows-10)).</span></span>

<span data-ttu-id="f28f9-480">イマーシブヘッドセットをテストするには、 *Unity エディター* の [**再生**] ボタンを押します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-480">You can test the immersive headset by pressing the **Play** button in the *Unity Editor*.</span></span>
<span data-ttu-id="f28f9-481">アプリは、接続されているイマーシブヘッドセットを介して機能している必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-481">The App should be functioning through the attached immersive headset.</span></span>

> [!WARNING]  
> <span data-ttu-id="f28f9-482">既定のオーディオデバイスの変更について Unity コンソールにエラーが表示される場合は、シーンが想定どおりに機能しない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-482">If you see an error in the Unity console about the default audio device changing, the scene may not function as expected.</span></span> <span data-ttu-id="f28f9-483">これは、mixed reality ポータルが、ヘッドセットを持つヘッドホン用の組み込みマイクを扱う方法に起因します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-483">This is due to the way the mixed reality portal deals with built-in microphones for headsets that have them.</span></span> <span data-ttu-id="f28f9-484">このエラーが表示された場合は、単にシーンを停止してからもう一度開始するだけで、期待どおりに動作するはずです。</span><span class="sxs-lookup"><span data-stu-id="f28f9-484">If you see this error, simply stop the scene and start it again and things should work as expected.</span></span>

## <a name="chapter-10--build-the-uwp-solution-and-sideload-on-local-machine"></a><span data-ttu-id="f28f9-485">Chapter 10 –ローカルコンピューターに UWP ソリューションとサイドロードを構築する</span><span class="sxs-lookup"><span data-stu-id="f28f9-485">Chapter 10 – Build the UWP solution and sideload on local machine</span></span>

<span data-ttu-id="f28f9-486">このプロジェクトの Unity セクションに必要なものはすべて完了したので、Unity から構築します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-486">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="f28f9-487">**ビルド設定** に移動します:**ファイル > ビルド設定...**</span><span class="sxs-lookup"><span data-stu-id="f28f9-487">Navigate to **Build Settings**: **File > Build Settings...**</span></span>
2.  <span data-ttu-id="f28f9-488">[ **ビルドの設定** ] ウィンドウで、[ **ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-488">From the **Build Settings** window, click **Build**.</span></span>

    ![Unity シーンをビルドします。](images/AzureLabs-Lab1-36.png)
  
3.  <span data-ttu-id="f28f9-490">**Unity C# プロジェクト** をまだティックしていない場合は、ティックします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-490">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="f28f9-491">[**ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-491">Click **Build**.</span></span> <span data-ttu-id="f28f9-492">Unity は *エクスプローラー* ウィンドウを起動します。このウィンドウでは、アプリを作成するフォルダーを作成して選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-492">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="f28f9-493">ここでそのフォルダーを作成し、「 *App*」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-493">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="f28f9-494">次に、 *アプリ* フォルダーを選択し、 **[フォルダーの選択]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-494">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="f28f9-495">Unity は、 *アプリ* フォルダーへのプロジェクトのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-495">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="f28f9-496">Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で *ファイルエクスプローラー* ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。</span><span class="sxs-lookup"><span data-stu-id="f28f9-496">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-11--deploy-your-application"></a><span data-ttu-id="f28f9-497">第11章–アプリケーションのデプロイ</span><span class="sxs-lookup"><span data-stu-id="f28f9-497">Chapter 11 – Deploy your application</span></span>

<span data-ttu-id="f28f9-498">アプリケーションをデプロイするには:</span><span class="sxs-lookup"><span data-stu-id="f28f9-498">To deploy your application:</span></span>

1.  <span data-ttu-id="f28f9-499">新しい Unity ビルド ( *アプリ* フォルダー) に移動し、 *Visual Studio* でソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-499">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
2.  <span data-ttu-id="f28f9-500">ソリューション構成で、[ **デバッグ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-500">In the Solution Configuration select **Debug**.</span></span>
3.  <span data-ttu-id="f28f9-501">ソリューションプラットフォームで、[ **x86**, **ローカルコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="f28f9-501">In the Solution Platform, select **x86**, **Local Machine**.</span></span> 

    > <span data-ttu-id="f28f9-502">Microsoft HoloLens の場合、これを *リモートコンピューター* に設定する方が簡単な場合があります。これにより、コンピューターにテザリングさされることはありません。</span><span class="sxs-lookup"><span data-stu-id="f28f9-502">For the Microsoft HoloLens, you may find it easier to set this to *Remote Machine*, so that you are not tethered to your computer.</span></span> <span data-ttu-id="f28f9-503">ただし、次の手順も実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-503">Though, you will need to also do the following:</span></span>
    > - <span data-ttu-id="f28f9-504">HoloLens の **IP アドレス** を確認します。これは、 *[設定 > ネットワーク & インターネット > Wi-Fi > 詳細オプション]* にあります。IPv4 は、使用するアドレスです。</span><span class="sxs-lookup"><span data-stu-id="f28f9-504">Know the **IP Address** of your HoloLens, which can be found within the *Settings > Network & Internet > Wi-Fi > Advanced Options*; the IPv4 is the address you should use.</span></span> 
    > - <span data-ttu-id="f28f9-505">*開発者モード* が **オンに** なっていることを確認します。*開発者向けのセキュリティ > の更新プログラム & の > の設定* にあります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-505">Ensure *Developer Mode* is **On**; found in *Settings > Update & Security > For developers*.</span></span>

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab1-37.png)
    
 
4.  <span data-ttu-id="f28f9-507">[ **ビルド] メニュー** の [ **ソリューションの配置** ] をクリックして、アプリケーションを PC にサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-507">Go to **Build menu** and click on **Deploy Solution** to sideload the application to your PC.</span></span>
5.  <span data-ttu-id="f28f9-508">アプリがインストール済みのアプリの一覧に表示され、起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="f28f9-508">Your App should now appear in the list of installed apps, ready to be launched.</span></span>
6.  <span data-ttu-id="f28f9-509">アプリを起動すると、マイクへのアクセスを承認するように求められます。</span><span class="sxs-lookup"><span data-stu-id="f28f9-509">Once launched, the App will prompt you to authorize access to the Microphone.</span></span> <span data-ttu-id="f28f9-510">[ **はい** ] ボタンをクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="f28f9-510">Make sure to click the **YES** button.</span></span>
7.  <span data-ttu-id="f28f9-511">これで、翻訳を開始する準備ができました。</span><span class="sxs-lookup"><span data-stu-id="f28f9-511">You are now ready to start translating!</span></span>

## <a name="your-finished-translation-text-api-application"></a><span data-ttu-id="f28f9-512">完成した翻訳テキスト API アプリケーション</span><span class="sxs-lookup"><span data-stu-id="f28f9-512">Your finished Translation Text API application</span></span>

<span data-ttu-id="f28f9-513">これで、Azure Translation Text API を活用して音声を翻訳されたテキストに変換する、mixed reality アプリを構築しました。</span><span class="sxs-lookup"><span data-stu-id="f28f9-513">Congratulations, you built a mixed reality app that leverages the Azure Translation Text API to convert speech to translated text.</span></span>

![最終的な製品。](images/AzureLabs-Lab1-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="f28f9-515">ボーナス演習</span><span class="sxs-lookup"><span data-stu-id="f28f9-515">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="f28f9-516">演習1</span><span class="sxs-lookup"><span data-stu-id="f28f9-516">Exercise 1</span></span>

<span data-ttu-id="f28f9-517">音声合成機能をアプリに追加して、返されたテキストが読み上げられるようにすることができますか。</span><span class="sxs-lookup"><span data-stu-id="f28f9-517">Can you add text-to-speech functionality to the app, so that the returned text is spoken?</span></span>

### <a name="exercise-2"></a><span data-ttu-id="f28f9-518">演習2</span><span class="sxs-lookup"><span data-stu-id="f28f9-518">Exercise 2</span></span>

<span data-ttu-id="f28f9-519">言語を変更するたびに、アプリを再構築する必要がないように、ユーザーがアプリ自体でソースと出力の言語 (' from ' と ' to ') を変更できるようにします。</span><span class="sxs-lookup"><span data-stu-id="f28f9-519">Make it possible for the user to change the source and output languages ('from' and 'to') within the app itself, so the app does not need to be rebuilt every time you want to change languages.</span></span>
