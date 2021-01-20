---
title: MR と Azure 312 - ボットの統合
description: このコースでは、Microsoft Bot Framework v4 を使用して bot を作成およびデプロイし、mixed reality アプリケーションでそれと通信する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, コンピュータービジョン, hololens, イマーシブ, vr, microsoft bot framework v4, web アプリボット, bot framework, microsoft bot, Windows 10, Visual Studio
ms.openlocfilehash: 6b8b4624615a3c3f62800b396803572b0b67ad1a
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/20/2021
ms.locfileid: "98582468"
---
# <a name="mr-and-azure-312-bot-integration"></a><span data-ttu-id="3f7a5-104">MR と Azure 312:ボットの統合</span><span class="sxs-lookup"><span data-stu-id="3f7a5-104">MR and Azure 312: Bot integration</span></span>

>[!NOTE]
><span data-ttu-id="3f7a5-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="3f7a5-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="3f7a5-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="3f7a5-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="3f7a5-109">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="3f7a5-110">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<span data-ttu-id="3f7a5-111">このコースでは、Microsoft Bot Framework V4 を使用して bot を作成およびデプロイし、Windows Mixed Reality アプリケーションを介してそれと通信する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-111">In this course, you will learn how to create and deploy a bot using the Microsoft Bot Framework V4 and communicate with it through a Windows Mixed Reality application.</span></span> 

![](images/AzureLabs-Lab312-00.png)

<span data-ttu-id="3f7a5-112">**Microsoft Bot Framework V4** は、拡張可能でスケーラブルな Bot アプリケーションを構築するためのツールを開発者に提供するために設計された api のセットです。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-112">The **Microsoft Bot Framework V4** is a set of APIs designed to provide developers with the tools to build an extensible and scalable bot application.</span></span> <span data-ttu-id="3f7a5-113">詳細については、 [Microsoft Bot Framework のページ](https://dev.botframework.com/) または [V4 Git リポジトリ](https://github.com/Microsoft/botbuilder-dotnet/wiki)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-113">For more information, visit the [Microsoft Bot Framework page](https://dev.botframework.com/) or the [V4 Git Repository](https://github.com/Microsoft/botbuilder-dotnet/wiki).</span></span>

<span data-ttu-id="3f7a5-114">このコースを完了すると、Windows Mixed Reality アプリケーションが構築されます。これにより、次のことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-114">After completing this course, you will have built a Windows Mixed Reality application, which will be able to do the following:</span></span>

1. <span data-ttu-id="3f7a5-115">**Tap ジェスチャ** を使用して、ユーザーの声をリッスンしているボットを開始します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-115">Use a **Tap Gesture** to start the bot listening for the users voice.</span></span>
2. <span data-ttu-id="3f7a5-116">ユーザーが何かを言い、bot は応答の提供を試みます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-116">When the user has said something, the bot will attempt to provide a response.</span></span>
3. <span data-ttu-id="3f7a5-117">ボットの近くに、Unity のシーンで bot の応答をテキストとして表示します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-117">Display the bots reply as text, positioned near the bot, in the Unity Scene.</span></span>

<span data-ttu-id="3f7a5-118">アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-118">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="3f7a5-119">このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-119">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="3f7a5-120">このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-120">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="3f7a5-121">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="3f7a5-121">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="3f7a5-122">コース</span><span class="sxs-lookup"><span data-stu-id="3f7a5-122">Course</span></span></th><th style="width:150px"> <span data-ttu-id="3f7a5-123"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="3f7a5-123"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="3f7a5-124"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="3f7a5-124"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="3f7a5-125">MR と Azure 312:ボットの統合</span><span class="sxs-lookup"><span data-stu-id="3f7a5-125">MR and Azure 312: Bot integration</span></span></td><td style="text-align: center;"> <span data-ttu-id="3f7a5-126">✔️</span><span class="sxs-lookup"><span data-stu-id="3f7a5-126">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="3f7a5-127">✔️</span><span class="sxs-lookup"><span data-stu-id="3f7a5-127">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="3f7a5-128">このコースでは主に HoloLens に焦点を当てていますが、このコースで学習する内容を Windows Mixed Reality イマーシブ (VR) ヘッドセットにも適用できます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-128">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="3f7a5-129">イマーシブ (VR) ヘッドセットにはアクセス可能なカメラがないため、外部カメラが PC に接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-129">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="3f7a5-130">コースを進めると、イマーシブ (VR) ヘッドセットをサポートするために必要な変更についての注意事項が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-130">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3f7a5-131">前提条件</span><span class="sxs-lookup"><span data-stu-id="3f7a5-131">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="3f7a5-132">このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-132">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="3f7a5-133">また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証された内容 (2018 年7月) を表しています。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-133">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="3f7a5-134">「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものより新しいソフトウェアの内容と完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-134">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="3f7a5-135">このコースでは、次のハードウェアとソフトウェアをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-135">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="3f7a5-136">開発用 PC で、 [Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) (VR) ヘッドセット開発と互換性があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-136">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="3f7a5-137">開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="3f7a5-137">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="3f7a5-138">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="3f7a5-138">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="3f7a5-139">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="3f7a5-139">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="3f7a5-140">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3f7a5-140">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="3f7a5-141">[Windows Mixed Reality イマーシブ (VR) ヘッドセット](../../../discover/immersive-headset-hardware-details.md)または開発者モードを有効にした[Microsoft HoloLens](/hololens/hololens1-hardware)</span><span class="sxs-lookup"><span data-stu-id="3f7a5-141">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="3f7a5-142">Azure および Azure Bot の取得のためのインターネットアクセス。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-142">Internet access for Azure, and for Azure Bot retrieval.</span></span> <span data-ttu-id="3f7a5-143">詳細については、こちらのリンクを参照し [てください](https://dev.botframework.com/)。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-143">For more information, [please follow this link](https://dev.botframework.com/).</span></span>

### <a name="before-you-start"></a><span data-ttu-id="3f7a5-144">開始する前に</span><span class="sxs-lookup"><span data-stu-id="3f7a5-144">Before you start</span></span>

1.  <span data-ttu-id="3f7a5-145">このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="3f7a5-146">HoloLens をセットアップしてテストします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="3f7a5-147">HoloLens のセットアップをサポートする必要がある場合は、 [hololens セットアップに関する記事にアクセスして](/hololens/hololens-setup)ください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="3f7a5-148">新しい HoloLens アプリの開発を開始するときは、調整とセンサーのチューニングを実行することをお勧めします (ユーザーごとにこれらのタスクを実行するのに役立つ場合があります)。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens app (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="3f7a5-149">調整の詳細については、 [「HoloLens の調整に関する記事へのリンク」を](/hololens/hololens-calibration#hololens-2)参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](/hololens/hololens-calibration#hololens-2).</span></span>

<span data-ttu-id="3f7a5-150">センサーチューニングの詳細については、 [HoloLens センサーチューニングに関する記事へのリンクを](/hololens/hololens-updates)参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](/hololens/hololens-updates).</span></span>

## <a name="chapter-1--create-the-bot-application"></a><span data-ttu-id="3f7a5-151">第1章: Bot アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="3f7a5-151">Chapter 1 – Create the Bot application</span></span>

<span data-ttu-id="3f7a5-152">最初の手順は、bot をローカル ASP.Net Core Web アプリケーションとして作成することです。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-152">The first step is to create your bot as a local ASP.Net Core Web application.</span></span> <span data-ttu-id="3f7a5-153">完了してテストした後は、Azure Portal に発行します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-153">Once you have finished and tested it, you will publish it to the Azure Portal.</span></span>

1.  <span data-ttu-id="3f7a5-154">Visual Studio を開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-154">Open Visual Studio.</span></span> <span data-ttu-id="3f7a5-155">新しいプロジェクトを作成し、プロジェクトの種類として [ **ASP NET Core Web アプリケーション** ] を選択し (サブセクション .net core の下にあります)、 **mybot** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-155">Create a new project, select **ASP NET Core Web Application** as the project type (you will find it under the subsection .NET Core) and call it **MyBot**.</span></span> <span data-ttu-id="3f7a5-156">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-156">Click **OK**.</span></span>

2.  <span data-ttu-id="3f7a5-157">表示されるウィンドウで、[ **空**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-157">In the Window that will appear select **Empty**.</span></span> <span data-ttu-id="3f7a5-158">また、ターゲットが **ASP NET Core 2.0** に設定されており、認証が [ **認証なし**] に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-158">Also make sure the target is set to **ASP NET Core 2.0** and the Authentication is set to **No Authentication**.</span></span> <span data-ttu-id="3f7a5-159">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-159">Click **OK**.</span></span>  

    ![Bot アプリケーションを作成する](images/AzureLabs-Lab312-01.png)

3.  <span data-ttu-id="3f7a5-161">これで、ソリューションが開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-161">The solution will now open.</span></span> <span data-ttu-id="3f7a5-162">**ソリューションエクスプローラー** でソリューション **mybot** を右クリックし、[**ソリューションの NuGet パッケージの管理**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-162">Right-click on Solution **Mybot** in the **Solution Explorer** and click on **Manage NuGet Packages for Solution**.</span></span> 

    ![Bot アプリケーションを作成する](images/AzureLabs-Lab312-02.png)

4.  <span data-ttu-id="3f7a5-164">[ **参照** ] タブで、「 **Microsoft... Integration. AspNet. Core** 」を検索します ( **プレリリースがオンに** なっていることを確認してください)。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-164">In the **Browse** tab, search for **Microsoft.Bot.Builder.Integration.AspNet.Core** (make sure you have **Include pre-release** checked).</span></span> <span data-ttu-id="3f7a5-165">パッケージバージョン **4.0.1-preview** を選択し、プロジェクトのボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-165">Select the package version **4.0.1-preview**, and tick the project boxes.</span></span> <span data-ttu-id="3f7a5-166">[ **インストール**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-166">Then click on **Install**.</span></span> <span data-ttu-id="3f7a5-167">これで、 **Bot Framework v4** に必要なライブラリがインストールされました。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-167">You have now installed the libraries needed for the **Bot Framework v4**.</span></span> <span data-ttu-id="3f7a5-168">NuGet ページを閉じます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-168">Close the NuGet page.</span></span>

    ![Bot アプリケーションを作成する](images/AzureLabs-Lab312-03.png)

5.  <span data-ttu-id="3f7a5-170">**ソリューションエクスプローラー** で *プロジェクト* の **mybot** を右クリックし、[クラスの **追加**] をクリックし **|** ます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-170">Right-click on your *Project*, **MyBot**, in the **Solution Explorer** and click on **Add** **|** **Class**.</span></span>

    ![Bot アプリケーションを作成する](images/AzureLabs-Lab312-04.png)

6.  <span data-ttu-id="3f7a5-172">クラスに **Mybot** という名前を指定し、[ **追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-172">Name the class **MyBot** and click on **Add**.</span></span>

    ![Bot アプリケーションを作成する](images/AzureLabs-Lab312-05.png)

7.  <span data-ttu-id="3f7a5-174">前の点を繰り返して、 **ConversationContext** という名前の別のクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-174">Repeat the previous point, to create another class named **ConversationContext**.</span></span> 

8.  <span data-ttu-id="3f7a5-175">**ソリューションエクスプローラー** で **wwwroot** を右クリックし、[新しい項目の **追加**] をクリックし **|** ます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-175">Right-click on **wwwroot** in the **Solution Explorer** and click on **Add** **|** **New Item**.</span></span> <span data-ttu-id="3f7a5-176">**HTML ページ** を選択します (サブセクション Web の下にあります)。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-176">Select  **HTML Page** (you will find it under the subsection Web).</span></span> <span data-ttu-id="3f7a5-177">ファイル **default.html** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-177">Name the file **default.html**.</span></span> <span data-ttu-id="3f7a5-178">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-178">Click **Add**.</span></span>

    ![Bot アプリケーションを作成する](images/AzureLabs-Lab312-06.png)

9.  <span data-ttu-id="3f7a5-180">**ソリューションエクスプローラー** 内のクラス/オブジェクトの一覧は次の図のようになります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-180">The list of classes / objects in the **Solution Explorer** should look like the image below.</span></span>

    ![Bot アプリケーションを作成する](images/AzureLabs-Lab312-07.png)

10. <span data-ttu-id="3f7a5-182">**ConversationContext** クラスをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-182">Double-click on the **ConversationContext** class.</span></span> <span data-ttu-id="3f7a5-183">このクラスは、bot が使用する変数を保持して、メッセージ交換のコンテキストを維持する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-183">This class is responsible for holding the variables used by the bot to maintain the context of the conversation.</span></span> <span data-ttu-id="3f7a5-184">これらのメッセージ交換コンテキスト値は、このクラスのインスタンスで保持されます。これは、アクティビティが受信されるたびに **Mybot** クラスのインスタンスが更新されるためです。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-184">These conversation context values are maintained in an instance of this class, because any instance of the **MyBot** class will refresh each time an activity is received.</span></span> <span data-ttu-id="3f7a5-185">このクラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-185">Add the following code to the class:</span></span>

    ```csharp
    namespace MyBot
    {
        public static class ConversationContext
        {
            internal static string userName;

            internal static string userMsg;
        }
    }
    ```

11. <span data-ttu-id="3f7a5-186">**Mybot** クラスをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-186">Double-click on the **MyBot** class.</span></span> <span data-ttu-id="3f7a5-187">このクラスは、顧客からのすべての受信アクティビティによって呼び出されるハンドラーをホストします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-187">This class will host the handlers called by any incoming activity from the customer.</span></span> <span data-ttu-id="3f7a5-188">このクラスでは、bot と顧客の間の会話を構築するために使用されるコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-188">In this class you will add the code used to build the conversation between the bot and the customer.</span></span> <span data-ttu-id="3f7a5-189">既に説明したように、このクラスのインスタンスは、アクティビティが受信されるたびに初期化されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-189">As mentioned earlier, an instance of this class is initialized each time an activity is received.</span></span> <span data-ttu-id="3f7a5-190">このクラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-190">Add the following code to this class:</span></span>

    ```csharp
    using Microsoft.Bot;
    using Microsoft.Bot.Builder;
    using Microsoft.Bot.Schema;
    using System.Threading.Tasks;

    namespace MyBot
    {
        public class MyBot : IBot
        {       
            public async Task OnTurn(ITurnContext context)
            {
                ConversationContext.userMsg = context.Activity.Text;

                if (context.Activity.Type is ActivityTypes.Message)
                {
                    if (string.IsNullOrEmpty(ConversationContext.userName))
                    {
                        ConversationContext.userName = ConversationContext.userMsg;
                        await context.SendActivity($"Hello {ConversationContext.userName}. Looks like today it is going to rain. \nLuckily I have umbrellas and waterproof jackets to sell!");
                    }
                    else
                    {
                        if (ConversationContext.userMsg.Contains("how much"))
                        {
                            if (ConversationContext.userMsg.Contains("umbrella")) await context.SendActivity($"Umbrellas are $13.");
                            else if (ConversationContext.userMsg.Contains("jacket")) await context.SendActivity($"Waterproof jackets are $30.");
                            else await context.SendActivity($"Umbrellas are $13. \nWaterproof jackets are $30.");
                        }
                        else if (ConversationContext.userMsg.Contains("color") || ConversationContext.userMsg.Contains("colour"))
                        {
                            await context.SendActivity($"Umbrellas are black. \nWaterproof jackets are yellow.");
                        }
                        else
                        {
                            await context.SendActivity($"Sorry {ConversationContext.userName}. I did not understand the question");
                        }
                    }
                }
                else
                {

                    ConversationContext.userMsg = string.Empty;
                    ConversationContext.userName = string.Empty;
                    await context.SendActivity($"Welcome! \nI am the Weather Shop Bot \nWhat is your name?");
                }

            }
        }
    }
    ```

12. <span data-ttu-id="3f7a5-191">**Startup** クラスをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-191">Double-click on the **Startup** class.</span></span> <span data-ttu-id="3f7a5-192">このクラスは bot を初期化します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-192">This class will initialize the bot.</span></span> <span data-ttu-id="3f7a5-193">このクラスに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-193">Add the following code to the class:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Bot.Builder.BotFramework;
    using Microsoft.Bot.Builder.Integration.AspNet.Core;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;

    namespace MyBot
    {
    public class Startup
        {
            public IConfiguration Configuration { get; }

            public Startup(IHostingEnvironment env)
            {
                var builder = new ConfigurationBuilder()
                    .SetBasePath(env.ContentRootPath)
                    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
                    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true)
                    .AddEnvironmentVariables();
                Configuration = builder.Build();
            }

            // This method gets called by the runtime. Use this method to add services to the container.
            public void ConfigureServices(IServiceCollection services)
            {
                services.AddSingleton(_ => Configuration);
                services.AddBot<MyBot>(options =>
                {
                    options.CredentialProvider = new ConfigurationCredentialProvider(Configuration);
                });
            }

            // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
            public void Configure(IApplicationBuilder app, IHostingEnvironment env)
            {
                if (env.IsDevelopment())
                {
                    app.UseDeveloperExceptionPage();
                }

                app.UseDefaultFiles();
                app.UseStaticFiles();
                app.UseBotFramework();
            }
        }
    }
    ```

13. <span data-ttu-id="3f7a5-194">**Program** クラスファイルを開き、内のコードが次のコードと同じであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-194">Open the **Program** class file and verify the code in it is the same as the following:</span></span>

    ```csharp
    using Microsoft.AspNetCore;
    using Microsoft.AspNetCore.Hosting;

    namespace MyBot
    {
        public class Program
        {
            public static void Main(string[] args)
            {
                BuildWebHost(args).Run();
            }

            public static IWebHost BuildWebHost(string[] args) =>
                WebHost.CreateDefaultBuilder(args)
                    .UseStartup<Startup>()
                    .Build();
        }
    }
    ```

14. <span data-ttu-id="3f7a5-195">変更内容を保存してください。そのためには、  >  Visual Studio の上部にあるツールバーから [ファイル] [**すべてを保存**] の順に開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-195">Remember to save your changes, to do so, go to **File** > **Save All**, from the toolbar at the top of Visual Studio.</span></span>

## <a name="chapter-2---create-the-azure-bot-service"></a><span data-ttu-id="3f7a5-196">第2章-Azure Bot Service の作成</span><span class="sxs-lookup"><span data-stu-id="3f7a5-196">Chapter 2 - Create the Azure Bot Service</span></span>

<span data-ttu-id="3f7a5-197">Bot 用のコードを作成したので、Azure Portal で *Web アプリボット* サービスのインスタンスに発行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-197">Now that you have built the code for your bot, you have to publish it to an instance of the *Web App Bot* Service, on the Azure Portal.</span></span> <span data-ttu-id="3f7a5-198">この章では、Azure でボットサービスを作成および構成し、そのサービスにコードを発行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-198">This Chapter will show you how to create and configure the Bot Service on Azure and then publish your code to it.</span></span>

1.  <span data-ttu-id="3f7a5-199">まず、Azure ポータル () にログインし https://portal.azure.com) ます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-199">First, log in to the Azure Portal (https://portal.azure.com).</span></span> 

    1. <span data-ttu-id="3f7a5-200">まだ Azure アカウントを持っていない場合は、アカウントを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-200">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="3f7a5-201">このチュートリアルを教室またはラボの状況で行っている場合は、新しいアカウントの設定について、インストラクターまたはそのいずれかの対処を依頼してください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-201">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="3f7a5-202">ログインしたら、左上隅にある [ **リソースの作成** ] をクリックし、[ *Web アプリボット*] を検索して、 **Enter キー** を押します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-202">Once you are logged in, click on **Create a resource** in the top left corner, and search for *Web App bot*, and click **Enter**.</span></span>

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-08.png)
 
3.  <span data-ttu-id="3f7a5-204">新しいページには、 *Web アプリボット* サービスの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-204">The new page will provide a description of the *Web App Bot* Service.</span></span> <span data-ttu-id="3f7a5-205">このページの左下にある [ **作成** ] ボタンを選択して、このサービスとの関連付けを作成します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-205">At the bottom left of this page, select the **Create** button, to create an association with this Service.</span></span>

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-09.png)
 
4.  <span data-ttu-id="3f7a5-207">[ **作成**:</span><span class="sxs-lookup"><span data-stu-id="3f7a5-207">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="3f7a5-208">このサービスインスタンスに必要な **名前** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-208">Insert your desired **Name** for this Service instance.</span></span>
    2. <span data-ttu-id="3f7a5-209">**サブスクリプション** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-209">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="3f7a5-210">リソースグループを選択するか、新しい **リソースグループ** を作成します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-210">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="3f7a5-211">リソースグループは、Azure 資産のコレクションの課金を監視、制御する方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-211">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="3f7a5-212">1つのプロジェクトに関連付けられているすべての Azure サービス (たとえば、これらのコースなど) を共通のリソースグループに保持することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-212">It is recommended to keep all the Azure Services associated with a single project (e.g. such as these courses) under a common resource group).</span></span>

        > <span data-ttu-id="3f7a5-213">Azure リソースグループの詳細については、こちらのリンクを参照 [してください。](/azure/azure-resource-manager/resource-group-portal)</span><span class="sxs-lookup"><span data-stu-id="3f7a5-213">If you wish to read more about Azure Resource Groups, [please follow this link](/azure/azure-resource-manager/resource-group-portal)</span></span>

    4. <span data-ttu-id="3f7a5-214">リソースグループの場所を決定します (新しいリソースグループを作成している場合)。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-214">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="3f7a5-215">この場所は、アプリケーションを実行するリージョンに配置するのが理想的です。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-215">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="3f7a5-216">一部の Azure 資産は、特定のリージョンでのみ利用できます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-216">Some Azure assets are only available in certain regions.</span></span>
    5. <span data-ttu-id="3f7a5-217">適切な **価格レベル** を選択します。これが *Web アプリボット* サービスを初めて作成する場合は、free レベル (F0) をご利用いただけます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-217">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Web App Bot* Service, a free tier (named F0) should be available to you</span></span>
    6. <span data-ttu-id="3f7a5-218">**アプリ名** は *Bot 名* と同じままにすることができます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-218">**App name** can just be left the same as the *Bot name*.</span></span> 
    7. <span data-ttu-id="3f7a5-219">*Bot テンプレート* は **Basic (C#)** のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-219">Leave the *Bot template* as **Basic (C#)**.</span></span>
    8. <span data-ttu-id="3f7a5-220">*App service プラン/場所* は、アカウントに対して自動入力されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-220">*App service plan/Location* should have been auto-filled for your account.</span></span>
    9. <span data-ttu-id="3f7a5-221">Bot をホストするために使用する **Azure Storage** を設定します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-221">Set the **Azure Storage** that you wish to use to host your Bot.</span></span> <span data-ttu-id="3f7a5-222">まだお持ちでない場合は、ここで作成できます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-222">If you dont have one already, you can create it here.</span></span>
    10. <span data-ttu-id="3f7a5-223">また、このサービスに適用されている使用条件を理解していることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-223">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    11. <span data-ttu-id="3f7a5-224">[作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-224">Click Create.</span></span>
 
        ![Azure Bot Service を作成する](images/AzureLabs-Lab312-10.png)

5.  <span data-ttu-id="3f7a5-226">[ **作成**] をクリックした後、サービスが作成されるまで待機する必要があります。これには1分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-226">Once you have clicked on **Create**, you will have to wait for the Service to be created, this might take a minute.</span></span>

6.  <span data-ttu-id="3f7a5-227">サービスインスタンスが作成されると、ポータルに通知が表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-227">A notification will appear in the Portal once the Service instance is created.</span></span>

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-11.png) 
 
7.  <span data-ttu-id="3f7a5-229">通知をクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-229">Click on the notification to explore your new Service instance.</span></span> 

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-12.png)
 
8. <span data-ttu-id="3f7a5-231">通知の [ **リソースへのジャンプ** ] ボタンをクリックして、新しいサービスインスタンスを探索します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-231">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="3f7a5-232">新しい Azure サービスインスタンスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-232">You will be taken to your new Azure Service instance.</span></span> 

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-13.png)
 
9.  <span data-ttu-id="3f7a5-234">この時点で、クライアントアプリケーションがこのボットサービスと通信できるように、 **ダイレクトライン** と呼ばれる機能を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-234">At this point you need to setup a feature called **Direct Line** to allow your client application to communicate with this Bot Service.</span></span> <span data-ttu-id="3f7a5-235">[ **チャンネル**] をクリックし、[ **おすすめチャネルの追加** ] セクションで、[ **ダイレクトラインチャネルの構成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-235">Click on **Channels**, then in the **Add a featured channel** section, click on **Configure Direct Line channel**.</span></span>

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-14.png)

10. <span data-ttu-id="3f7a5-237">このページでは、クライアントアプリが bot で認証できるようにする **秘密キー** を見つけます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-237">In this page you will find the **Secret keys** that will allow your client app to authenticate with the bot.</span></span> <span data-ttu-id="3f7a5-238">[ **表示** ] ボタンをクリックし、表示されているキーの1つをコピーします。これは、プロジェクトの後半で必要になります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-238">Click on the **Show** button and take a copy of one of the displayed Keys, as you will need this later in your project.</span></span> 

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-15.png)

## <a name="chapter-3--publish-the-bot-to-the-azure-web-app-bot-service"></a><span data-ttu-id="3f7a5-240">第3章: Bot を Azure Web アプリボットサービスに発行する</span><span class="sxs-lookup"><span data-stu-id="3f7a5-240">Chapter 3 – Publish the Bot to the Azure Web App Bot Service</span></span>

<span data-ttu-id="3f7a5-241">サービスの準備ができたので、先ほどビルドした Bot コードを、新しく作成した Web アプリボットサービスに発行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-241">Now that your Service is ready, you need to publish your Bot code, that you built previously, to your newly created Web App Bot Service.</span></span>

> [!NOTE] 
> <span data-ttu-id="3f7a5-242">Bot ソリューション/コードに変更を加えるたびに、Bot を Azure サービスに発行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-242">You will have to publish your Bot to the Azure Service every time you make changes to the Bot solution / code.</span></span>

1.  <span data-ttu-id="3f7a5-243">前に作成した Visual Studio ソリューションに戻ります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-243">Go back to your Visual Studio Solution that you created previously.</span></span> 
2.  <span data-ttu-id="3f7a5-244">**ソリューションエクスプローラー** で **mybot** プロジェクトを右クリックし、[**発行**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-244">Right-click on your **MyBot** project, in the **Solution Explorer**, then click on **Publish**.</span></span>

    ![Bot を Azure Web アプリボットサービスに発行する](images/AzureLabs-Lab312-16.png)

3.  <span data-ttu-id="3f7a5-246">[ *発行先の選択* ] ページで、 **[App Service**] をクリックし、[既存] を **選択** します。最後に、[ **プロファイルの作成** ] をクリックします (表示されていない場合は、[ *発行* ] ボタンの横にあるドロップダウンの矢印をクリックする必要があります)。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-246">On the *Pick a publish target* page, click **App Service**, then **Select Existing**, lastly click on **Create Profile** (you may need to click on the dropdown arrow alongside the *Publish* button, if this is not visible).</span></span>

    ![Bot を Azure Web アプリボットサービスに発行する](images/AzureLabs-Lab312-17.png)

4. <span data-ttu-id="3f7a5-248">Microsoft アカウントにまだログインしていない場合は、ここで実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-248">If you are not yet logged in into your Microsoft Account, you have to do it here.</span></span>
5. <span data-ttu-id="3f7a5-249">[**発行**] ページでは、 *Web アプリボット* サービスの作成に使用したものと同じ **サブスクリプション** を設定する必要があることがわかります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-249">On the **Publish** page you will find you have to set the same **Subscription** that you used for the *Web App Bot* Service creation.</span></span> <span data-ttu-id="3f7a5-250">次に、 **ビュー** を **リソースグループ** として設定し、ドロップダウンフォルダー構造で、前に作成した **リソースグループ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-250">Then set the **View** as **Resource Group** and, in the drop down folder structure, select the **Resource Group** you have created previously.</span></span> <span data-ttu-id="3f7a5-251">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-251">Click **OK**.</span></span> 

    ![Bot を Azure Web アプリボットサービスに発行する](images/AzureLabs-Lab312-18.png)

6.  <span data-ttu-id="3f7a5-253">[ **発行** ] ボタンをクリックし、Bot が公開されるまで待ちます (数分かかる場合があります)。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-253">Now click on the **Publish** button, and wait for the Bot to be published (it might take a few minutes).</span></span>

    ![Bot を Azure Web アプリボットサービスに発行する](images/AzureLabs-Lab312-19.png)


## <a name="chapter-4--set-up-the-unity-project"></a><span data-ttu-id="3f7a5-255">章 4-Unity プロジェクトを設定する</span><span class="sxs-lookup"><span data-stu-id="3f7a5-255">Chapter 4 – Set up the Unity project</span></span>

<span data-ttu-id="3f7a5-256">次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-256">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="3f7a5-257">*Unity* を開き、[**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-257">Open *Unity* and click **New**.</span></span> 

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-20.png)

2.  <span data-ttu-id="3f7a5-259">ここで、Unity プロジェクト名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-259">You will now need to provide a Unity project name.</span></span> <span data-ttu-id="3f7a5-260">**HoloLens Bot** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-260">Insert **HoloLens Bot**.</span></span> <span data-ttu-id="3f7a5-261">プロジェクトテンプレートが **3d** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-261">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="3f7a5-262">場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-262">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="3f7a5-263">次に、[ **プロジェクトの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-263">Then, click **Create project**.</span></span>

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-21.png)

3.  <span data-ttu-id="3f7a5-265">Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-265">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="3f7a5-266">[ **> の設定の編集** ] に移動し、新しいウィンドウで [ **外部ツール**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-266">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="3f7a5-267">**外部スクリプトエディター** を **Visual Studio 2017** に変更します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-267">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="3f7a5-268">[ **基本設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-268">Close the **Preferences** window.</span></span>

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-22.png)

4.  <span data-ttu-id="3f7a5-270">次に、[ **ファイル > ビルド設定** ] に移動し、[ **ユニバーサル Windows プラットフォーム**] を選択します。次に、[ **プラットフォームの切り替え** ] ボタンをクリックして選択内容を適用します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-270">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-23.png)

5.  <span data-ttu-id="3f7a5-272">それでも **ファイル > ビルド設定** を行い、次のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-272">While still in **File > Build Settings** and make sure that:</span></span>

    1.  <span data-ttu-id="3f7a5-273">**ターゲットデバイス** が **HoloLens** に設定されています</span><span class="sxs-lookup"><span data-stu-id="3f7a5-273">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="3f7a5-274">イマーシブヘッドセットの場合は、 **ターゲットデバイス** を *任意のデバイス* に設定します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-274">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2.  <span data-ttu-id="3f7a5-275">**ビルドの種類** が **D3D** に設定されています</span><span class="sxs-lookup"><span data-stu-id="3f7a5-275">**Build Type** is set to **D3D**</span></span>

    3.  <span data-ttu-id="3f7a5-276">**SDK** は最新の **インストール** に設定されています</span><span class="sxs-lookup"><span data-stu-id="3f7a5-276">**SDK** is set to **Latest installed**</span></span>

    4.  <span data-ttu-id="3f7a5-277">**Visual Studio のバージョン** が、**インストールされている最新** バージョンに設定されています</span><span class="sxs-lookup"><span data-stu-id="3f7a5-277">**Visual Studio Version** is set to **Latest installed**</span></span>

    5.  <span data-ttu-id="3f7a5-278">**ビルドと実行** は **ローカルコンピューター** に設定されています</span><span class="sxs-lookup"><span data-stu-id="3f7a5-278">**Build and Run** is set to **Local Machine**</span></span>

    6.  <span data-ttu-id="3f7a5-279">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-279">Save the scene and add it to the build.</span></span> 

        1. <span data-ttu-id="3f7a5-280">これを行うには、[開いている **シーンの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-280">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="3f7a5-281">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-281">A save window will appear.</span></span>
        
            ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-24.png)

        2. <span data-ttu-id="3f7a5-283">この新しいフォルダーを作成し、今後のシーンに加えて、[ **新しいフォルダー** ] ボタンを選択します。新しいフォルダーを作成するには、名前を「 **シーン**」にします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-283">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

             ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-25.png)

        3. <span data-ttu-id="3f7a5-285">新しく作成した [ **シーン** ] フォルダーを開き、[ *ファイル名*: テキスト] フィールドに「 **BotScene**」と入力し、[ **保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-285">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **BotScene**, then click on **Save**.</span></span>

            ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-26.png)

    7. <span data-ttu-id="3f7a5-287">それ以外の設定は、[ **ビルド設定**] の [既定] のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-287">The remaining settings, in **Build Settings**, should be left as default for now.</span></span>

6. <span data-ttu-id="3f7a5-288">[ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-288">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-27.png)

7. <span data-ttu-id="3f7a5-290">このパネルでは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-290">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="3f7a5-291">[ **その他の設定** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-291">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="3f7a5-292">**Scripting Runtime のバージョン** は **実験的 (NET 4.6 と同等)** である必要があります。これを変更するには、エディターを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-292">**Scripting Runtime Version** should be **Experimental (NET 4.6 Equivalent)**; changing this will require a restart of the Editor.</span></span>
        2. <span data-ttu-id="3f7a5-293">**バックエンド** は **.net** である必要があります</span><span class="sxs-lookup"><span data-stu-id="3f7a5-293">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="3f7a5-294">**API 互換性レベル** は **.net 4.6** である必要があります</span><span class="sxs-lookup"><span data-stu-id="3f7a5-294">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-28.png)
      
    2. <span data-ttu-id="3f7a5-296">[ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-296">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="3f7a5-297">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="3f7a5-297">**InternetClient**</span></span>
        - <span data-ttu-id="3f7a5-298">**マイク**</span><span class="sxs-lookup"><span data-stu-id="3f7a5-298">**Microphone**</span></span>

            ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-29.png)

    3. <span data-ttu-id="3f7a5-300">パネルの下にある [ **XR settings** (発行の **設定**] の下にあります) で、[ **サポートされている仮想現実**] をティックし、 **Windows Mixed reality SDK** が追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-300">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Unity プロジェクトを設定する](images/AzureLabs-Lab312-30.png)

8.  <span data-ttu-id="3f7a5-302">*ビルド設定* に戻る _Unity C#_ プロジェクトはグレーで表示されなくなりました。このの横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-302">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="3f7a5-303">[ビルド設定] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-303">Close the Build Settings window.</span></span>
10. <span data-ttu-id="3f7a5-304">シーンとプロジェクトを保存します ([**ファイル] > [シーン/ファイルの保存] > [プロジェクトの保存**])。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-304">Save your scene and project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>


## <a name="chapter-5--camera-setup"></a><span data-ttu-id="3f7a5-305">第5章–カメラの設定</span><span class="sxs-lookup"><span data-stu-id="3f7a5-305">Chapter 5 – Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3f7a5-306">このコースの *Unity セットアップ* コンポーネントをスキップし、コードに直接進む場合は、 [312 この unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage)をダウンロードして、 [**カスタムパッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、 [第7章](#chapter-8--create-the-botobjects-class)から続行することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-306">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-312-Package.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/Azure-MR-312.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 7](#chapter-8--create-the-botobjects-class).</span></span>

1.  <span data-ttu-id="3f7a5-307">[ *階層] パネル* で、 **メインカメラ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-307">In the *Hierarchy panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="3f7a5-308">選択すると、 **メインカメラ** のすべてのコンポーネントが [ *インスペクター] パネル* に表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-308">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector panel*.</span></span>

    1. <span data-ttu-id="3f7a5-309">**カメラオブジェクト** は **メインカメラ** という名前にする必要があります (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-309">The **Camera object** must be named **Main Camera** (note the spelling)</span></span>
    2. <span data-ttu-id="3f7a5-310">メインカメラ **タグ** を **maincamera** に設定する必要があります (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-310">The Main Camera **Tag** must be set to **MainCamera** (note the spelling)</span></span>
    3. <span data-ttu-id="3f7a5-311">**変換位置** が **0、0、0** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-311">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="3f7a5-312">**クリアフラグ** を **純色** に設定します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-312">Set **Clear Flags** to **Solid Color**.</span></span>
    5. <span data-ttu-id="3f7a5-313">カメラコンポーネントの **背景** 色を **黒、アルファ 0 (16 進コード: #00000000)** に設定します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-313">Set the **Background** Color of the Camera component to **Black, Alpha 0 (Hex Code: #00000000)**</span></span>

    ![カメラの設定](images/AzureLabs-Lab312-31.png)
 

## <a name="chapter-6--import-the-newtonsoft-library"></a><span data-ttu-id="3f7a5-315">Chapter 6 – Newtonsoft ライブラリをインポートする</span><span class="sxs-lookup"><span data-stu-id="3f7a5-315">Chapter 6 – Import the Newtonsoft library</span></span>

<span data-ttu-id="3f7a5-316">受信して Bot サービスに送信されたオブジェクトを逆シリアル化およびシリアル化できるようにするには、 **Newtonsoft** ライブラリをダウンロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-316">To help you deserialize and serialize objects received and sent to the Bot Service you need to download the **Newtonsoft** library.</span></span> <span data-ttu-id="3f7a5-317">[互換性のあるバージョンが、適切な Unity フォルダー構造で既に構成されている](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage)ことがわかります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-317">You will find a [compatible version already organized with the correct Unity folder structure here](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20312%20-%20Bot%20integration/NewtonsoftDLL.unitypackage).</span></span> 

<span data-ttu-id="3f7a5-318">Newtonsoft ライブラリをプロジェクトにインポートするには、このコースに付属している Unity パッケージを使用します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-318">To import the Newtonsoft library into your project, use the Unity Package which came with this course.</span></span>

1.  <span data-ttu-id="3f7a5-319">[  **アセット**  >  **インポートパッケージ** の  >  **カスタムパッケージ**] メニューオプションを使用して、unitypackage を Unity に追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-319">Add the *.unitypackage* to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span>

    ![Newtonsoft ライブラリをインポートする](images/AzureLabs-Lab312-34.png)

2.  <span data-ttu-id="3f7a5-321">ポップアップ表示された [ **Unity パッケージのインポート** ] ボックスで、 **プラグイン** (およびそれを含む) のすべてが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-321">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![Newtonsoft ライブラリをインポートする](images/AzureLabs-Lab312-35.png)

3.  <span data-ttu-id="3f7a5-323">[ **インポート** ] ボタンをクリックして、プロジェクトに項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-323">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="3f7a5-324">プロジェクトビューの [**プラグイン**] の下にある **newtonsoft** フォルダーにアクセスし、newtonsoft プラグインを選択します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-324">Go to the **Newtonsoft** folder under **Plugins** in the project view and select the Newtonsoft plugin.</span></span>

    ![](images/AzureLabs-Lab312-35b.png)

5.  <span data-ttu-id="3f7a5-325">Newtonsoft プラグインを選択した状態で、 **任意のプラットフォーム** が **オフ** になっていることを確認し、[ **wsaplayer** ] も **オフ** になっていることを確認してから、[ **適用**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-325">With the Newtonsoft plugin selected, ensure that **Any Platform** is **unchecked**, then ensure that **WSAPlayer** is also **unchecked**, then click **Apply**.</span></span> <span data-ttu-id="3f7a5-326">これは、ファイルが正しく構成されていることを確認するためのものです。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-326">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab312-35c.png)

    > [!NOTE]
    > <span data-ttu-id="3f7a5-327">これらのプラグインをマークすると、Unity エディターでのみ使用するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-327">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="3f7a5-328">WSA フォルダーには、Unity からプロジェクトがエクスポートされた後に使用される、異なるセットがあります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-328">There are a different set of them in the WSA folder which will be used after the project is exported from Unity.</span></span>

6.  <span data-ttu-id="3f7a5-329">次に、 **Newtonsoft** フォルダー内の **WSA** フォルダーを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-329">Next, you need to open the **WSA** folder, within the **Newtonsoft** folder.</span></span> <span data-ttu-id="3f7a5-330">先ほど構成したものと同じファイルのコピーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-330">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="3f7a5-331">ファイルを選択し、インスペクターで次のことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-331">Select the file, and then in the inspector, ensure that</span></span>
    -   <span data-ttu-id="3f7a5-332">**すべてのプラットフォーム** が **オフ** になっています</span><span class="sxs-lookup"><span data-stu-id="3f7a5-332">**Any Platform** is **unchecked**</span></span> 
    -   <span data-ttu-id="3f7a5-333"> **wsaplayer** のみが **チェック** されます</span><span class="sxs-lookup"><span data-stu-id="3f7a5-333">**only** **WSAPlayer** is **checked**</span></span>
    -   <span data-ttu-id="3f7a5-334">**処理** されないかどうかを **確認** します</span><span class="sxs-lookup"><span data-stu-id="3f7a5-334">**Dont process** is **checked**</span></span>

    ![](images/AzureLabs-Lab312-35d.png)

## <a name="chapter-7--create-the-bottag"></a><span data-ttu-id="3f7a5-335">第7章– BotTag を作成する</span><span class="sxs-lookup"><span data-stu-id="3f7a5-335">Chapter 7 – Create the BotTag</span></span>

1.  <span data-ttu-id="3f7a5-336">**BotTag** という名前の新しい **タグ** オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-336">Create a new **Tag** object called **BotTag**.</span></span> <span data-ttu-id="3f7a5-337">シーンのメインカメラを選択します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-337">Select the Main Camera in the scene.</span></span> <span data-ttu-id="3f7a5-338">[インスペクター] パネルの [タグ] ドロップダウンメニューをクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-338">Click on the Tag drop down menu in the Inspector panel.</span></span> <span data-ttu-id="3f7a5-339">[ **タグの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-339">Click on **Add Tag**.</span></span>

    ![カメラの設定](images/AzureLabs-Lab312-32.png)
 
2.  <span data-ttu-id="3f7a5-341">シンボルをクリックし **+** ます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-341">Click on the **+** symbol.</span></span> <span data-ttu-id="3f7a5-342">新しい **タグ** に **BotTag** という名前を *付けて保存* します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-342">Name the new **Tag** as **BotTag**, *Save*.</span></span>

    ![カメラの設定](images/AzureLabs-Lab312-33.png)

> [!WARNING] 
> <span data-ttu-id="3f7a5-344">メインカメラに **BotTag** を適用しない **で** ください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-344">**Do not** apply the **BotTag** to the Main Camera.</span></span> <span data-ttu-id="3f7a5-345">この操作を誤って行った場合は、メインカメラのタグを必ず *Maincamera* に戻してください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-345">If you have accidentally done this, make sure to change the Main Camera tag back to *MainCamera*.</span></span>

## <a name="chapter-8--create-the-botobjects-class"></a><span data-ttu-id="3f7a5-346">Chapter 8 – BotObjects クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="3f7a5-346">Chapter 8 – Create the BotObjects class</span></span>

<span data-ttu-id="3f7a5-347">作成する必要のある最初のスクリプトは、 **BotObjects** クラスです。このクラスは、他の一連のクラスオブジェクトを同じスクリプト内に格納し、シーン内の他のスクリプトからアクセスできるようにするために作成された空のクラスです。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-347">The first script you need to create is the **BotObjects** class, which is an empty class created so that a series of other class objects can be stored within the same script and accessed by other scripts in the scene.</span></span>

<span data-ttu-id="3f7a5-348">このクラスの作成は、純粋にアーキテクチャを選択したものです。これらのオブジェクトは、このコースの後半で作成する Bot スクリプトでホストすることができます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-348">The creation of this class is purely an architectural choice, these objects could instead be hosted in the Bot script that you will create later in this course.</span></span>

<span data-ttu-id="3f7a5-349">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="3f7a5-349">To create this class:</span></span> 

1.  <span data-ttu-id="3f7a5-350">[ *プロジェクト] パネル* 内を右クリックし、[ **> フォルダーの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-350">Right-click in the *Project panel*, then **Create > Folder**.</span></span> <span data-ttu-id="3f7a5-351">フォルダーに **スクリプト** の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-351">Name the folder **Scripts**.</span></span> 

    ![Scripts フォルダーを作成します。](images/AzureLabs-Lab312-36.png)

2.  <span data-ttu-id="3f7a5-353">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-353">Double-click on the **Scripts** folder to open it.</span></span> <span data-ttu-id="3f7a5-354">次に、そのフォルダー内でを右クリックし、[ **Create > C# Script**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-354">Then within that folder, right-click, and select **Create > C# Script**.</span></span> <span data-ttu-id="3f7a5-355">スクリプトに **BotObjects** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-355">Name the script **BotObjects**.</span></span> 

3.  <span data-ttu-id="3f7a5-356">新しい **BotObjects** スクリプトをダブルクリックして、 **Visual Studio** で開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-356">Double-click on the new **BotObjects** script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="3f7a5-357">スクリプトの内容を削除し、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-357">Delete the content of the script and replace it with the following code:</span></span>

    ```csharp
    using System;
    using System.Collections;
    using System.Collections.Generic;
    using UnityEngine;

    public class BotObjects : MonoBehaviour{}

    /// <summary>
    /// Object received when first opening a conversation
    /// </summary>
    [Serializable]
    public class ConversationObject
    {
        public string ConversationId;
        public string token;
        public string expires_in;
        public string streamUrl;
        public string referenceGrammarId;
    }

    /// <summary>
    /// Object including all Activities
    /// </summary>
    [Serializable]
    public class ActivitiesRootObject
    {
        public List<Activity> activities { get; set; }
        public string watermark { get; set; }
    }
    [Serializable]
    public class Conversation
    {
        public string id { get; set; }
    }
    [Serializable]
    public class From
    {
        public string id { get; set; }
        public string name { get; set; }
    }
    [Serializable]
    public class Activity
    {
        public string type { get; set; }
        public string channelId { get; set; }
        public Conversation conversation { get; set; }
        public string id { get; set; }
        public From from { get; set; }
        public string text { get; set; }
        public string textFormat { get; set; }
        public DateTime timestamp { get; set; }
        public string serviceUrl { get; set; }
    }
    ```

6.  <span data-ttu-id="3f7a5-358">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-358">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-9--create-the-gazeinput-class"></a><span data-ttu-id="3f7a5-359">第9章: GazeInput クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="3f7a5-359">Chapter 9 – Create the GazeInput class</span></span>

<span data-ttu-id="3f7a5-360">次に作成するクラスは、 **GazeInput** クラスです。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-360">The next class you are going to create is the **GazeInput** class.</span></span> <span data-ttu-id="3f7a5-361">このクラスの役割は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-361">This class is responsible for:</span></span>

- <span data-ttu-id="3f7a5-362">プレーヤーの *宝石* を表すカーソルを作成する。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-362">Creating a cursor that will represent the *gaze* of the player.</span></span>
- <span data-ttu-id="3f7a5-363">プレーヤーの見つめによってヒットしたオブジェクトを検出し、検出されたオブジェクトへの参照を保持します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-363">Detecting objects hit by the gaze of the player, and holding a reference to detected objects.</span></span>

<span data-ttu-id="3f7a5-364">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="3f7a5-364">To create this class:</span></span> 

1.  <span data-ttu-id="3f7a5-365">前に作成した **Scripts** フォルダーにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-365">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="3f7a5-366">フォルダー内を右クリックし、[ **Create > C# Script**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-366">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="3f7a5-367">スクリプト **GazeInput** を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-367">Call the script **GazeInput**.</span></span> 
3.  <span data-ttu-id="3f7a5-368">新しい **GazeInput** スクリプトをダブルクリックして、 **Visual Studio** で開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-368">Double-click on the new **GazeInput** script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="3f7a5-369">クラス名の上に次の行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-369">Insert the following line right on top of the class name:</span></span>

    ```csharp
    /// <summary>
    /// Class responsible for the User's gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    ```

5.  <span data-ttu-id="3f7a5-370">次に、 **Start ()** メソッドの上に、 **GazeInput** クラス内に次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-370">Then add the following variables inside the **GazeInput** class, above the **Start()** method:</span></span>

    ```csharp
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "BotTag";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject _oldFocusedObject { get; private set; }

        internal RaycastHit HitInfo { get; private set; }

        /// <summary>
        /// Cursor object visible in the scene
        /// </summary>
        internal GameObject Cursor { get; private set; }

        internal bool Hit { get; private set; }

        internal Vector3 Position { get; private set; }

        internal Vector3 Normal { get; private set; }

        private Vector3 _gazeOrigin;

        private Vector3 _gazeDirection;
    ```

6.  <span data-ttu-id="3f7a5-371">**Start ()** メソッドのコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-371">Code for **Start()** method should be added.</span></span> <span data-ttu-id="3f7a5-372">このは、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-372">This will be called when the class initializes:</span></span>

    ```csharp
        /// <summary>
        /// Start method used upon initialization.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }
    ```

7.  <span data-ttu-id="3f7a5-373">見つめカーソルをインスタンス化して設定するメソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-373">Implement a method that will instantiate and setup the gaze cursor:</span></span> 

    ```csharp
        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it does not block Raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

8.  <span data-ttu-id="3f7a5-374">メインカメラから Raycast を設定するメソッドを実装します。これにより、現在フォーカスがあるオブジェクトが追跡されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-374">Implement the methods that will setup the Raycast from the Main Camera and will keep track of the current focused object.</span></span>

    ```csharp
        /// <summary>
        /// Called every frame
        /// </summary>
        internal virtual void Update()
        {
            _gazeOrigin = Camera.main.transform.position;

            _gazeDirection = Camera.main.transform.forward;

            UpdateRaycast();
        }


        /// <summary>
        /// Reset the old focused object, stop the gaze timer, and send data if it
        /// is greater than one.
        /// </summary>
        private void ResetFocusedObject()
        {
            // Ensure the old focused object is not null.
            if (_oldFocusedObject != null)
            {
                if (_oldFocusedObject.CompareTag(InteractibleTag))
                {
                    // Provide the OnGazeExited event.
                    _oldFocusedObject.SendMessage("OnGazeExited", 
                        SendMessageOptions.DontRequireReceiver);
                }
            }
        }


        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            _oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialize Raycasting.
            Hit = Physics.Raycast(_gazeOrigin,
                _gazeDirection,
                out hitInfo,
                GazeMaxDistance);
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

            // Check whether the previous focused object is this same. If so, reset the focused object.
            if (FocusedObject != _oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the OnGazeEntered event.
                        FocusedObject.SendMessage("OnGazeEntered",
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```
 
9.  <span data-ttu-id="3f7a5-375">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-375">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-10--create-the-bot-class"></a><span data-ttu-id="3f7a5-376">Chapter 10 – Bot クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="3f7a5-376">Chapter 10 – Create the Bot class</span></span>

<span data-ttu-id="3f7a5-377">ここで作成するスクリプトは **Bot** と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-377">The script you are going to create now is called **Bot**.</span></span> <span data-ttu-id="3f7a5-378">これはアプリケーションのコアクラスであり、次のものが格納されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-378">This is the core class of your application, it stores:</span></span> 

- <span data-ttu-id="3f7a5-379">Web アプリボットの資格情報</span><span class="sxs-lookup"><span data-stu-id="3f7a5-379">Your Web App Bot credentials</span></span>
- <span data-ttu-id="3f7a5-380">ユーザーの音声コマンドを収集するメソッド</span><span class="sxs-lookup"><span data-stu-id="3f7a5-380">The method that collects the user voice commands</span></span>
- <span data-ttu-id="3f7a5-381">Web アプリボットとのメッセージ交換を開始するために必要なメソッド</span><span class="sxs-lookup"><span data-stu-id="3f7a5-381">The method necessary to initiate conversations with your Web App Bot</span></span> 
- <span data-ttu-id="3f7a5-382">Web アプリボットにメッセージを送信するために必要なメソッド</span><span class="sxs-lookup"><span data-stu-id="3f7a5-382">The method necessary to send messages to your Web App Bot</span></span> 

<span data-ttu-id="3f7a5-383">Bot サービスにメッセージを送信するために、 **Sendmessagetobot ()** コルーチンはアクティビティを作成します。これは、bot Framework によってユーザーによって送信されたデータとして認識されるオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-383">To send messages to the Bot Service, the **SendMessageToBot()** coroutine will build an activity, which is an object recognized by the Bot Framework as data sent by the user.</span></span> 
 
<span data-ttu-id="3f7a5-384">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="3f7a5-384">To create this class:</span></span> 

1. <span data-ttu-id="3f7a5-385">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-385">Double-click on the **Scripts** folder, to open it.</span></span> 
2. <span data-ttu-id="3f7a5-386">**Scripts** フォルダー内を右クリックし、[ **Create > C# Script**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-386">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="3f7a5-387">スクリプト **ボット** にという名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-387">Name the script **Bot**.</span></span> 
3. <span data-ttu-id="3f7a5-388">新しいスクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-388">Double-click on the new script to open it with Visual Studio.</span></span>
4. <span data-ttu-id="3f7a5-389">**Bot** クラスの上部で、次の名前空間を更新します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-389">Update the namespaces to be the same as the following, at the top of the **Bot** class:</span></span>

    ```csharp
    using Newtonsoft.Json;
    using System.Collections;
    using System.Text;
    using UnityEngine;
    using UnityEngine.Networking;
    using UnityEngine.Windows.Speech;
    ```
 
5. <span data-ttu-id="3f7a5-390">**Bot** クラス内で、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-390">Inside the **Bot** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static Bot Instance;

        /// <summary>
        /// Material of the sphere representing the Bot in the scene
        /// </summary>
        internal Material botMaterial;

        /// <summary>
        /// Speech recognizer class reference, which will convert speech to text.
        /// </summary>
        private DictationRecognizer dictationRecognizer;

        /// <summary>
        /// Use this variable to identify the Bot Id
        /// Can be any value
        /// </summary>
        private string botId = "MRBotId";

        /// <summary>
        /// Use this variable to identify the Bot Name
        /// Can be any value
        /// </summary>
        private string botName = "MRBotName";

        /// <summary>
        /// The Bot Secret key found on the Web App Bot Service on the Azure Portal
        /// </summary>
        private string botSecret = "-- Add your Secret Key here --"; 

        /// <summary>
        /// Bot Endpoint, v4 Framework uses v3 endpoint at this point in time
        /// </summary>
        private string botEndpoint = "https://directline.botframework.com/v3/directline";

        /// <summary>
        /// The conversation object reference
        /// </summary>
        private ConversationObject conversation;

        /// <summary>
        /// Bot states to regulate the application flow
        /// </summary>
        internal enum BotState {ReadyToListen, Listening, Processing}

        /// <summary>
        /// Flag for the Bot state
        /// </summary>
        internal BotState botState;

        /// <summary>
        /// Flag for the conversation status
        /// </summary>
        internal bool conversationStarted = false;
    ```

    > [!NOTE] 
    > <span data-ttu-id="3f7a5-391">**Bot シークレットキー** を **botSecret** 変数に挿入していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-391">Make sure you insert your **Bot Secret Key** into the **botSecret** variable.</span></span> <span data-ttu-id="3f7a5-392">**Bot の秘密鍵** は、このコースの最初に、 **[第2章](#chapter-2---create-the-azure-bot-service)の手順 10** で説明しました。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-392">You will have noted your **Bot Secret Key** at the beginning of this course, in **[Chapter 2](#chapter-2---create-the-azure-bot-service), step 10**.</span></span>

7. <span data-ttu-id="3f7a5-393">起動可能な **()** と **Start ()** のコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-393">Code for **Awake()** and **Start()** now needs to be added.</span></span> 

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start()
        {
            botState = BotState.ReadyToListen;
        }
    ```

8. <span data-ttu-id="3f7a5-394">音声キャプチャの開始時と終了時に speech ライブラリによって呼び出される2つのハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-394">Add the two handlers that are called by the speech libraries when voice capture begins and ends.</span></span> <span data-ttu-id="3f7a5-395">*DictationRecognizer* は、ユーザーが読み上げを停止したときに、ユーザーの音声のキャプチャを自動的に停止します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-395">The *DictationRecognizer* will automatically stop capturing the user voice when the user stops speaking.</span></span>

    ```csharp
        /// <summary>
        /// Start microphone capture.
        /// </summary>
        public void StartCapturingAudio()
        {
            botState = BotState.Listening;
            botMaterial.color = Color.red;

            // Start dictation
            dictationRecognizer = new DictationRecognizer();
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
            dictationRecognizer.Start();
        }
        

        /// <summary>
        /// Stop microphone capture.
        /// </summary>
        public void StopCapturingAudio()
        {
            botState = BotState.Processing;
            dictationRecognizer.Stop();
        }
        
    ```

1. <span data-ttu-id="3f7a5-396">次のハンドラーは、ユーザーの音声入力の結果を収集し、Web アプリボットサービスへのメッセージの送信を担当するコルーチンを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-396">The following handler collects the result of the user voice input and calls the coroutine responsible for sending the message to the Web App Bot Service.</span></span>

    ```csharp
        /// <summary>
        /// This handler is called every time the Dictation detects a pause in the speech. 
        /// </summary>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // Update UI with dictation captured
            Debug.Log($"User just said: {text}");      

            // Send dictation to Bot
            StartCoroutine(SendMessageToBot(text, botId, botName, "message"));
            StopCapturingAudio();
        }     
    ```

10. <span data-ttu-id="3f7a5-397">Bot とのメッセージ交換を開始するために、次のコルーチンが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-397">The following coroutine is called to begin a conversation with the Bot.</span></span> <span data-ttu-id="3f7a5-398">メッセージ交換の呼び出しが完了すると、Bot サービスに空のメッセージとしてアクティビティが送信されるように設定する一連のパラメーターを渡すことによって、 **SendMessageToCoroutine ()** が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-398">You will notice that once the conversation call is complete, it will call the **SendMessageToCoroutine()** by passing a series of parameters that will set the activity to be sent to the Bot Service as an empty message.</span></span> <span data-ttu-id="3f7a5-399">これは、Bot サービスにダイアログを開始するように求めるメッセージを表示するために行われます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-399">This is done to prompt the Bot Service to initiate the dialogue.</span></span>

    ```csharp
        /// <summary>
        /// Request a conversation with the Bot Service
        /// </summary>
        internal IEnumerator StartConversation()
        {
            string conversationEndpoint = string.Format("{0}/conversations", botEndpoint);

            WWWForm webForm = new WWWForm();

            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(conversationEndpoint, webForm))
            {
                unityWebRequest.SetRequestHeader("Authorization", "Bearer " + botSecret);
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                yield return unityWebRequest.SendWebRequest();
                string jsonResponse = unityWebRequest.downloadHandler.text;
            
                conversation = new ConversationObject();
                conversation = JsonConvert.DeserializeObject<ConversationObject>(jsonResponse);
                Debug.Log($"Start Conversation - Id: {conversation.ConversationId}");
                conversationStarted = true; 
            }

            // The following call is necessary to create and inject an activity of type //"conversationUpdate" to request a first "introduction" from the Bot Service.
            StartCoroutine(SendMessageToBot("", botId, botName, "conversationUpdate"));
        }    
    ```

11. <span data-ttu-id="3f7a5-400">Bot サービスに送信されるアクティビティをビルドするために、次のコルーチンが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-400">The following coroutine is called to build the activity to be sent to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Send the user message to the Bot Service in form of activity
        /// and call for a response
        /// </summary>
        private IEnumerator SendMessageToBot(string message, string fromId, string fromName, string activityType)
        {
            Debug.Log($"SendMessageCoroutine: {conversation.ConversationId}, message: {message} from Id: {fromId} from name: {fromName}");

            // Create a new activity here
            Activity activity = new Activity();
            activity.from = new From();
            activity.conversation = new Conversation();
            activity.from.id = fromId;
            activity.from.name = fromName;
            activity.text = message;
            activity.type = activityType;
            activity.channelId = "DirectLineChannelId";
            activity.conversation.id = conversation.ConversationId;     

            // Serialize the activity
            string json = JsonConvert.SerializeObject(activity);

            string sendActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);
            
            // Send the activity to the Bot
            using (UnityWebRequest www = new UnityWebRequest(sendActivityEndpoint, "POST"))
            {
                www.uploadHandler = new UploadHandlerRaw(Encoding.UTF8.GetBytes(json));

                www.downloadHandler = new DownloadHandlerBuffer();
                www.SetRequestHeader("Authorization", "Bearer " + botSecret);
                www.SetRequestHeader("Content-Type", "application/json");

                yield return www.SendWebRequest();

                // extrapolate the response Id used to keep track of the conversation
                string jsonResponse = www.downloadHandler.text;
                string cleanedJsonResponse = jsonResponse.Replace("\r\n", string.Empty);
                string responseConvId = cleanedJsonResponse.Substring(10, 30);

                // Request a response from the Bot Service
                StartCoroutine(GetResponseFromBot(activity));
            }
        }
    ```

12. <span data-ttu-id="3f7a5-401">次のコルーチンは、Bot サービスにアクティビティを送信した後に応答を要求するために呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-401">The following coroutine is called to request a response after sending an activity to the Bot Service.</span></span> 

    ```csharp
        /// <summary>
        /// Request a response from the Bot by using a previously sent activity
        /// </summary>
        private IEnumerator GetResponseFromBot(Activity activity)
        {
            string getActivityEndpoint = string.Format("{0}/conversations/{1}/activities", botEndpoint, conversation.ConversationId);

            using (UnityWebRequest unityWebRequest1 = UnityWebRequest.Get(getActivityEndpoint))
            {
                unityWebRequest1.downloadHandler = new DownloadHandlerBuffer();
                unityWebRequest1.SetRequestHeader("Authorization", "Bearer " + botSecret);

                yield return unityWebRequest1.SendWebRequest();

                string jsonResponse = unityWebRequest1.downloadHandler.text;

                ActivitiesRootObject root = new ActivitiesRootObject();
                root = JsonConvert.DeserializeObject<ActivitiesRootObject>(jsonResponse);

                foreach (var act in root.activities)
                {
                    Debug.Log($"Bot Response: {act.text}");
                    SetBotResponseText(act.text);
                }

                botState = BotState.ReadyToListen;
                botMaterial.color = Color.blue;
            }
        } 
    ```

13. <span data-ttu-id="3f7a5-402">このクラスに最後に追加されるメソッドは、シーンにメッセージを表示するために必要です。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-402">The last method to be added to this class, is required to display the message in the scene:</span></span>

    ```csharp
        /// <summary>
        /// Set the UI Response Text of the bot
        /// </summary>
        internal void SetBotResponseText(string responseString)
        {        
            SceneOrganiser.Instance.botResponseText.text =  responseString;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="3f7a5-403">Unity エディターコンソールで、 **SceneOrganiser** クラスがないというエラーが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-403">You may see an error within the Unity Editor Console, about missing the **SceneOrganiser** class.</span></span> <span data-ttu-id="3f7a5-404">このメッセージは無視してください。このチュートリアルの後半で、このクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-404">Disregard this message, as you will create this class later in the tutorial.</span></span>

14.  <span data-ttu-id="3f7a5-405">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-405">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-11--create-the-interactions-class"></a><span data-ttu-id="3f7a5-406">第11章–相互作用クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="3f7a5-406">Chapter 11 – Create the Interactions class</span></span>

<span data-ttu-id="3f7a5-407">ここで作成するクラスは、" **相互作用**" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-407">The class you are going to create now is called **Interactions**.</span></span> <span data-ttu-id="3f7a5-408">このクラスは、ユーザーからの HoloLens タップ入力を検出するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-408">This class is used to detect the HoloLens Tap Input from the user.</span></span> 

<span data-ttu-id="3f7a5-409">シーン内の *bot* オブジェクトを見ているときにユーザーがタップしたときに、bot が音声入力をリッスンする準備ができている場合、bot オブジェクトは色を **赤** に変更し、音声入力のリッスンを開始します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-409">If the user taps while looking at the *Bot* object in the scene, and the Bot is ready to listen for voice inputs, the Bot object will change color to **red** and begin listening for voice inputs.</span></span> 

<span data-ttu-id="3f7a5-410">このクラスは、 **GazeInput** クラスから継承されます。したがって、このクラスの **Start ()** メソッドと変数を参照できます。これは、 **base** を使用することによって示されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-410">This class inherits from the **GazeInput** class, and so is able to reference the **Start()** method and variables from that class, denoted by the use of **base**.</span></span> 
 
<span data-ttu-id="3f7a5-411">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="3f7a5-411">To create this class:</span></span>

1.  <span data-ttu-id="3f7a5-412">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-412">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="3f7a5-413">**Scripts** フォルダー内を右クリックし、[ **Create > C# Script**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-413">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="3f7a5-414">スクリプトの **操作** に名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-414">Name the script **Interactions**.</span></span> 
3.  <span data-ttu-id="3f7a5-415">新しいスクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-415">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="3f7a5-416">**相互作用** クラスの上部で、次のように名前空間とクラスの継承を更新します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-416">Update the namespaces and the class inheritance to be the same as the following, at the top of the **Interactions** class:</span></span>

    ```csharp
    using UnityEngine.XR.WSA.Input;

    public class Interactions : GazeInput
    {
    ```

5.  <span data-ttu-id="3f7a5-417">**相互作用** クラス内で、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-417">Inside the **Interactions** class add the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```
6.  <span data-ttu-id="3f7a5-418">次に、 **Start ()** メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-418">Then add the **Start()** method:</span></span>

    ```csharp
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            //Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="3f7a5-419">ユーザーが HoloLens カメラの前で tap ジェスチャを実行したときにトリガーされるハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-419">Add the handler that will be triggered when the user performs the tap gesture in front of the HoloLens camera</span></span>

    ```csharp
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            // Ensure the bot is being gazed upon.
            if(base.FocusedObject != null)
            {
                // If the user is tapping on Bot and the Bot is ready to listen
                if (base.FocusedObject.name == "Bot" && Bot.Instance.botState == Bot.BotState.ReadyToListen)
                {
                    // If a conversation has not started yet, request one
                    if(Bot.Instance.conversationStarted)
                    {
                        Bot.Instance.SetBotResponseText("Listening...");
                        Bot.Instance.StartCapturingAudio();
                    }
                    else
                    {
                        Bot.Instance.SetBotResponseText("Requesting Conversation...");
                        StartCoroutine(Bot.Instance.StartConversation());
                    }                                  
                }
            }
        }
    ```

8. <span data-ttu-id="3f7a5-420">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-420">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>

## <a name="chapter-12--create-the-sceneorganiser-class"></a><span data-ttu-id="3f7a5-421">第12章: SceneOrganiser クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="3f7a5-421">Chapter 12 – Create the SceneOrganiser class</span></span>

<span data-ttu-id="3f7a5-422">このラボに必要な最後のクラスは、 **SceneOrganiser** と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-422">The last class required in this Lab is called **SceneOrganiser**.</span></span> <span data-ttu-id="3f7a5-423">このクラスは、メインカメラにコンポーネントとスクリプトを追加し、シーンに適切なオブジェクトを作成することによって、シーンをプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-423">This class will setup the scene programmatically, by adding components and scripts to the Main Camera, and creating the appropriate objects in the scene.</span></span>
 
<span data-ttu-id="3f7a5-424">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="3f7a5-424">To create this class:</span></span>

1.  <span data-ttu-id="3f7a5-425">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-425">Double-click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="3f7a5-426">**Scripts** フォルダー内を右クリックし、[ **Create > C# Script**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-426">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="3f7a5-427">スクリプトに **SceneOrganiser** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-427">Name the script **SceneOrganiser**.</span></span> 
3.  <span data-ttu-id="3f7a5-428">新しいスクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-428">Double-click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="3f7a5-429">**SceneOrganiser** クラス内で、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-429">Inside the **SceneOrganiser** class add the following variables:</span></span>

    ```csharp
        /// <summary>
        /// Static instance of this class
        /// </summary>
        public static SceneOrganiser Instance;

        /// <summary>
        /// The 3D text representing the Bot response
        /// </summary>
        internal TextMesh botResponseText;
    ```

6.  <span data-ttu-id="3f7a5-430">次に、起動 ( **)** および **開始 ()** の各メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-430">Then add the **Awake()** and **Start()** methods:</span></span>

    ```csharp
        /// <summary>
        /// Called on Initialization
        /// </summary>
        private void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called immediately after Awake method
        /// </summary>
        void Start ()
        {
            // Add the GazeInput class to this object
            gameObject.AddComponent<GazeInput>();

            // Add the Interactions class to this object
            gameObject.AddComponent<Interactions>();

            // Create the Bot in the scene
            CreateBotInScene();
        }
    ```

7.  <span data-ttu-id="3f7a5-431">シーンに Bot オブジェクトを作成し、パラメーターとコンポーネントを設定する次のメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-431">Add the following method, responsible for creating the Bot object in the scene and setting up the parameters and components:</span></span>

    ```csharp
        /// <summary>
        /// Create the Sign In button object in the scene
        /// and sets its properties
        /// </summary>
        private void CreateBotInScene()
        {
            GameObject botObjInScene = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            botObjInScene.name = "Bot";
            
            // Add the Bot class to the Bot GameObject
            botObjInScene.AddComponent<Bot>();

            // Create the Bot UI
            botResponseText = CreateBotResponseText();

            // Set properties of Bot GameObject
            Bot.Instance.botMaterial = new Material(Shader.Find("Diffuse"));
            botObjInScene.GetComponent<Renderer>().material = Bot.Instance.botMaterial;
            Bot.Instance.botMaterial.color = Color.blue;
            botObjInScene.transform.position = new Vector3(0f, 2f, 10f);
            botObjInScene.tag = "BotTag";
        }
    ```

7.  <span data-ttu-id="3f7a5-432">次のメソッドを追加します。これは、Bot からの応答を表す、シーン内の UI オブジェクトの作成を担当します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-432">Add the following method, responsible for creating the UI object in the scene, representing the responses from the Bot:</span></span>

    ```csharp
        /// <summary>
        /// Spawns cursor for the Main Camera
        /// </summary>
        private TextMesh CreateBotResponseText()
        {
            // Create a sphere as new cursor
            GameObject textObject = new GameObject();
            textObject.transform.parent = Bot.Instance.transform;
            textObject.transform.localPosition = new Vector3(0,1,0);

            // Resize the new cursor
            textObject.transform.localScale = new Vector3(0.1f, 0.1f, 0.1f);

            // Creating the text of the Label
            TextMesh textMesh = textObject.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleCenter;
            textMesh.alignment = TextAlignment.Center;
            textMesh.fontSize = 50;
            textMesh.text = "Hi there, tap on me and I will start listening.";
            
            return textMesh;
        }
    ```

8.  <span data-ttu-id="3f7a5-433">*Unity* に戻る前に、変更内容を *Visual Studio* に保存してください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-433">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
9.  <span data-ttu-id="3f7a5-434">Unity エディターで、 **SceneOrganiser** スクリプトを Scripts フォルダーからメインカメラにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-434">In the Unity Editor, drag the **SceneOrganiser** script from the Scripts folder to the Main Camera.</span></span> <span data-ttu-id="3f7a5-435">次の図に示すように、シーン Organiser コンポーネントがメインカメラオブジェクトに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-435">The Scene Organiser component should now appear on the Main Camera object, as shown in the image below.</span></span>

    ![Azure Bot Service を作成する](images/AzureLabs-Lab312-37.png)

## <a name="chapter-13--before-building"></a><span data-ttu-id="3f7a5-437">第13章: ビルド前</span><span class="sxs-lookup"><span data-stu-id="3f7a5-437">Chapter 13 – Before building</span></span>

<span data-ttu-id="3f7a5-438">アプリケーションの徹底的なテストを実行するには、アプリケーションを HoloLens にサイドロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-438">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="3f7a5-439">これを行う前に、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-439">Before you do, ensure that:</span></span>

-   <span data-ttu-id="3f7a5-440">[**章 4**](#chapter-4--set-up-the-unity-project)で説明したすべての設定が正しく設定されています。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-440">All the settings mentioned in the [**Chapter 4**](#chapter-4--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="3f7a5-441">スクリプト **SceneOrganiser** は、 **メインカメラ** オブジェクトにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-441">The script **SceneOrganiser** is attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="3f7a5-442">**Bot** クラスで、 **bot シークレットキー** が **botSecret** 変数に挿入されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-442">In the **Bot** class, make sure you have inserted your **Bot Secret Key** into the **botSecret** variable.</span></span>

## <a name="chapter-14--build-and-sideload-to-the-hololens"></a><span data-ttu-id="3f7a5-443">第14章– HoloLens へのビルドとサイドロード</span><span class="sxs-lookup"><span data-stu-id="3f7a5-443">Chapter 14 – Build and Sideload to the HoloLens</span></span>

<span data-ttu-id="3f7a5-444">このプロジェクトの Unity セクションに必要なものはすべて完了したので、Unity から構築します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-444">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="3f7a5-445">**ビルド設定**、**ファイル > ビルド設定** に移動します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-445">Navigate to **Build Settings**, **File > Build Settings…**.</span></span>
2.  <span data-ttu-id="3f7a5-446">[ **ビルドの設定** ] ウィンドウで、[ **ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-446">From the **Build Settings** window, click **Build**.</span></span>

    ![Unity からアプリをビルドする](images/AzureLabs-Lab312-38.png)

3.  <span data-ttu-id="3f7a5-448">**Unity C# プロジェクト** をまだティックしていない場合は、ティックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-448">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="3f7a5-449">[**ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-449">Click **Build**.</span></span> <span data-ttu-id="3f7a5-450">Unity は **エクスプローラー** ウィンドウを起動します。このウィンドウでは、アプリを作成するフォルダーを作成して選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-450">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="3f7a5-451">ここでそのフォルダーを作成し、「 **App**」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-451">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="3f7a5-452">次に、 **アプリ** フォルダーを選択し、[ **フォルダーの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-452">Then with the **App** folder selected, click **Select Folder**.</span></span> 
5.  <span data-ttu-id="3f7a5-453">Unity は、 **アプリ** フォルダーへのプロジェクトのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-453">Unity will begin building your project to the **App** folder.</span></span> 
6.  <span data-ttu-id="3f7a5-454">Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で **ファイルエクスプローラー** ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-454">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-15--deploy-to-hololens"></a><span data-ttu-id="3f7a5-455">第15章– HoloLens への展開</span><span class="sxs-lookup"><span data-stu-id="3f7a5-455">Chapter 15 – Deploy to HoloLens</span></span>

<span data-ttu-id="3f7a5-456">HoloLens に展開するには:</span><span class="sxs-lookup"><span data-stu-id="3f7a5-456">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="3f7a5-457">Hololens が **開発者モード** になっていることを確認するには、HOLOLENS の IP アドレス (リモートデプロイ用) が必要です。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-457">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="3f7a5-458">これを行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-458">To do this:</span></span>

    1. <span data-ttu-id="3f7a5-459">HoloLens を装着した後、 **設定** を開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-459">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="3f7a5-460">**[Network & Internet > Wi-Fi > 詳細オプション]** にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-460">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="3f7a5-461">**IPv4** アドレスをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-461">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="3f7a5-462">次に、[**設定**] に戻り、**開発者向けの & セキュリティ > を更新** します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-462">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="3f7a5-463">開発者モードをに設定します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-463">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="3f7a5-464">新しい Unity ビルド ( **アプリ** フォルダー) に移動し、 **Visual Studio** でソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-464">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>
3.  <span data-ttu-id="3f7a5-465">**ソリューション構成** で、[**デバッグ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-465">In the **Solution Configuration** select **Debug**.</span></span>
4.  <span data-ttu-id="3f7a5-466">**ソリューションプラットフォーム** で、[ **X86**、**リモートコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-466">In the **Solution Platform**, select **x86**, **Remote Machine**.</span></span> 

    ![Visual Studio からソリューションをデプロイします。](images/AzureLabs-Lab312-39.png)
 
5.  <span data-ttu-id="3f7a5-468">[ **ビルド] メニュー** の [ソリューションの **配置**] をクリックして、アプリケーションを HoloLens にサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-468">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="3f7a5-469">アプリが HoloLens にインストールされているアプリの一覧に表示され、起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-469">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

    > [!NOTE]
    > <span data-ttu-id="3f7a5-470">イマーシブヘッドセットにデプロイするには **、ソリューションプラットフォーム** を *ローカルコンピューター* に設定し、**プラットフォーム** として *x86* を使用して、**構成** を [*デバッグ*] に設定します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-470">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="3f7a5-471">次に、[ **ビルド] メニュー** の [ *ソリューションの配置*] をクリックして、ローカルコンピューターに配置します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-471">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="chapter-16--using-the-application-on-the-hololens"></a><span data-ttu-id="3f7a5-472">Chapter 16 – HoloLens でのアプリケーションの使用</span><span class="sxs-lookup"><span data-stu-id="3f7a5-472">Chapter 16 – Using the application on the HoloLens</span></span>

- <span data-ttu-id="3f7a5-473">アプリケーションを起動すると、その前に Bot が青い球として表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-473">Once you have launched the application, you will see the Bot as a blue sphere in front of you.</span></span>

- <span data-ttu-id="3f7a5-474">メッセージ交換を開始するには、 **タップジェスチャ** を使用します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-474">Use the **Tap Gesture** while you are gazing at the sphere to initiate a conversation.</span></span> 
 
- <span data-ttu-id="3f7a5-475">メッセージ交換が開始されるのを待ちます (UI は、発生したときにメッセージを表示します)。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-475">Wait for the conversation to start (The UI will display a message when it happens).</span></span> <span data-ttu-id="3f7a5-476">Bot からの入門メッセージを受信したら、Bot でもう一度タップして、赤に変わり、音声の聞き取りを開始します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-476">Once you receive the introductory message from the Bot, tap again on the Bot so it will turn red and begin to listen to your voice.</span></span> 

- <span data-ttu-id="3f7a5-477">会話を終了すると、アプリケーションから Bot にメッセージが送信され、UI に表示される応答がすぐに表示されます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-477">Once you stop talking, your application will send your message to the Bot and you will promptly receive a response that will be displayed in the UI.</span></span> 

- <span data-ttu-id="3f7a5-478">プロセスを繰り返して、Bot にさらにメッセージを送信します (メッセージを送信するたびにタップする必要があります)。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-478">Repeat the process to send more messages to your Bot (you have to tap each time you want to sen a message).</span></span>

<span data-ttu-id="3f7a5-479">このメッセージ交換では、Bot が情報 (自分の名前) を保持しながら、既知の情報 (在庫品目など) も提供する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-479">This conversation demonstrates how the Bot can retain information (your name), whilst also providing known information (such as the items that are stocked).</span></span>

#### <a name="some-questions-to-ask-the-bot"></a><span data-ttu-id="3f7a5-480">Bot に質問することができます。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-480">Some questions to ask the Bot:</span></span>

```
what do you sell? 

how much are umbrellas?

how much are raincoats?
```

## <a name="your-finished-web-app-bot-v4-application"></a><span data-ttu-id="3f7a5-481">完成した Web アプリボット (v4) アプリケーション</span><span class="sxs-lookup"><span data-stu-id="3f7a5-481">Your finished Web App Bot (v4) application</span></span>

<span data-ttu-id="3f7a5-482">これで、Azure Web アプリボットである Microsoft Bot Framework v4 を活用する mixed reality アプリが作成されました。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-482">Congratulations, you built a mixed reality app that leverages the Azure Web App Bot, Microsoft Bot Framework v4.</span></span>

![最終製品](images/AzureLabs-Lab312-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="3f7a5-484">ボーナス演習</span><span class="sxs-lookup"><span data-stu-id="3f7a5-484">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="3f7a5-485">演習1</span><span class="sxs-lookup"><span data-stu-id="3f7a5-485">Exercise 1</span></span>

<span data-ttu-id="3f7a5-486">このラボのメッセージ交換の構造は非常に基本的なものです。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-486">The conversation structure in this Lab is very basic.</span></span> <span data-ttu-id="3f7a5-487">Microsoft LUIS を使用して、bot の自然言語に関する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-487">Use Microsoft LUIS to give your bot natural language understanding capabilities.</span></span>

### <a name="exercise-2"></a><span data-ttu-id="3f7a5-488">演習2</span><span class="sxs-lookup"><span data-stu-id="3f7a5-488">Exercise 2</span></span>

<span data-ttu-id="3f7a5-489">この例では、メッセージ交換を終了し、新しいメッセージ交換を再開することはありません。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-489">This example does not include terminating a conversation and restarting a new one.</span></span> <span data-ttu-id="3f7a5-490">Bot 機能を完成させるには、メッセージ交換にクロージャを実装してみてください。</span><span class="sxs-lookup"><span data-stu-id="3f7a5-490">To make the Bot feature complete, try to implement closure to the conversation.</span></span>