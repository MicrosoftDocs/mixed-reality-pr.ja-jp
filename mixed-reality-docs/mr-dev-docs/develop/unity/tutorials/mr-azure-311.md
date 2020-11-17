---
title: MR と Azure 311 - Microsoft Graph
description: このコースでは、Microsoft Graph を活用する方法と、混合の現実アプリケーション内で生産性を向上させるデータに接続する方法について説明します。
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: azure, mixed reality, academy, unity, チュートリアル, api, microsoft graph, hololens, イマーシブ, vr, Windows 10, Visual Studio
ms.openlocfilehash: 341b6fea537fe6001a8f7dcf2e98efea0a0b09b6
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679441"
---
# <a name="mr-and-azure-311---microsoft-graph"></a><span data-ttu-id="24177-104">MR と Azure 311 - Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="24177-104">MR and Azure 311 - Microsoft Graph</span></span>

>[!NOTE]
><span data-ttu-id="24177-105">Mixed Reality Academy のチュートリアルは、HoloLens (第 1 世代) と Mixed Reality イマーシブ ヘッドセットを念頭に置いて編成されています。</span><span class="sxs-lookup"><span data-stu-id="24177-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="24177-106">そのため、それらのデバイスの開発に関するガイダンスを引き続き探している開発者のために、これらのチュートリアルをそのまま残しておくことが重要だと考えています。</span><span class="sxs-lookup"><span data-stu-id="24177-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="24177-107">これらのチュートリアルが、HoloLens 2 に使用されている最新のツールセットや操作に更新されることは "**_ありません_**"。</span><span class="sxs-lookup"><span data-stu-id="24177-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="24177-108">これらは、サポートされているデバイス上で継続して動作するように、保守されます。</span><span class="sxs-lookup"><span data-stu-id="24177-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="24177-109">今後、HoloLens 2 向けの開発方法を示す新しい一連のチュートリアルが掲載されています。</span><span class="sxs-lookup"><span data-stu-id="24177-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="24177-110">この通知は、これらのチュートリアルが投稿されたときのリンクと共に更新されます。</span><span class="sxs-lookup"><span data-stu-id="24177-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<span data-ttu-id="24177-111">このコースでは、 *Microsoft Graph* を使用して、mixed reality アプリケーション内でセキュリティ保護された認証を使用して Microsoft アカウントにログインする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="24177-111">In this course, you will learn how to use *Microsoft Graph* to log in into your Microsoft account using secure authentication within a mixed reality application.</span></span> <span data-ttu-id="24177-112">次に、スケジュールされた会議をアプリケーションインターフェイスで取得して表示します。</span><span class="sxs-lookup"><span data-stu-id="24177-112">You will then retrieve and display your scheduled meetings in the application interface.</span></span>

![](images/AzureLabs-Lab311-00.png)

<span data-ttu-id="24177-113">*Microsoft Graph* は、Microsoft の多くのサービスにアクセスできるように設計された api のセットです。</span><span class="sxs-lookup"><span data-stu-id="24177-113">*Microsoft Graph* is a set of APIs designed to enable access to many of Microsoft's services.</span></span> <span data-ttu-id="24177-114">Microsoft では、リレーションシップによって接続されるリソースのマトリックスとして Microsoft Graph について説明します。これは、アプリケーションが接続されたあらゆる種類のユーザーデータにアクセスできるようにすることを意味します</span><span class="sxs-lookup"><span data-stu-id="24177-114">Microsoft describes Microsoft Graph as being a matrix of resources connected by relationships, meaning it allows an application to access all sorts of connected user data.</span></span> <span data-ttu-id="24177-115">詳細については、 [Microsoft Graph のページ](https://developer.microsoft.com/graph)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24177-115">For more information, visit the [Microsoft Graph page](https://developer.microsoft.com/graph).</span></span>

<span data-ttu-id="24177-116">開発にはアプリの作成が含まれます。このアプリでは、ユーザーが宝石を見つめ、球をタップするように指示され、ユーザーは Microsoft アカウントに安全にログインするように求められます。</span><span class="sxs-lookup"><span data-stu-id="24177-116">Development will include the creation of an app where the user will be instructed to gaze at and then tap a sphere, which will prompt the user to log in safely to a Microsoft account.</span></span> <span data-ttu-id="24177-117">自分のアカウントにログインすると、その日にスケジュールされている会議の一覧を表示できるようになります。</span><span class="sxs-lookup"><span data-stu-id="24177-117">Once logged in to their account, the user will be able to see a list of meetings scheduled for the day.</span></span>

<span data-ttu-id="24177-118">このコースを完了すると、mixed reality HoloLens アプリケーションが完成します。これにより、次のことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="24177-118">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="24177-119">Tap ジェスチャを使用して、オブジェクトをタップします。これにより、ユーザーは Microsoft アカウントにログインするように求められます (アプリの外に移動してログインし、再びアプリに戻す)。</span><span class="sxs-lookup"><span data-stu-id="24177-119">Using the Tap gesture, tap on an object, which will prompt the user to log into a Microsoft Account (moving out of the app to log in, and then back into the app again).</span></span>
2.  <span data-ttu-id="24177-120">その日にスケジュールされている会議の一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="24177-120">View a list of meetings scheduled for the day.</span></span> 

<span data-ttu-id="24177-121">アプリケーションでは、結果をデザインと統合する方法については、お客様のニーズに合わせてください。</span><span class="sxs-lookup"><span data-stu-id="24177-121">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="24177-122">このコースは、Azure サービスを Unity プロジェクトと統合する方法を説明することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="24177-122">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="24177-123">このコースで得られた知識を使用して、mixed reality アプリケーションを強化することができます。</span><span class="sxs-lookup"><span data-stu-id="24177-123">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="24177-124">デバイス サポート</span><span class="sxs-lookup"><span data-stu-id="24177-124">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="24177-125">コース</span><span class="sxs-lookup"><span data-stu-id="24177-125">Course</span></span></th><th style="width:150px"> <span data-ttu-id="24177-126"><a href="../../../hololens-hardware-details.md">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="24177-126"><a href="../../../hololens-hardware-details.md">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="24177-127"><a href="../../../discover/immersive-headset-hardware-details.md">イマーシブ ヘッドセット</a></span><span class="sxs-lookup"><span data-stu-id="24177-127"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="24177-128">MR と Azure 311:Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="24177-128">MR and Azure 311: Microsoft Graph</span></span></td><td style="text-align: center;"> <span data-ttu-id="24177-129">✔️</span><span class="sxs-lookup"><span data-stu-id="24177-129">✔️</span></span></td><td style="text-align: center;"> </td>
</tr>
</table>

## <a name="prerequisites"></a><span data-ttu-id="24177-130">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="24177-130">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="24177-131">このチュートリアルは、Unity と C# の基本的な経験がある開発者向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="24177-131">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="24177-132">また、このドキュメントに記載されている前提条件と記述に記載されている手順は、作成時にテストおよび検証された内容 (2018 年7月) を表しています。</span><span class="sxs-lookup"><span data-stu-id="24177-132">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (July 2018).</span></span> <span data-ttu-id="24177-133">「 [ツールのインストール](../../install-the-tools.md) 」の記事に記載されているように、最新のソフトウェアを自由に使用できます。ただし、このコースの情報は、以下に記載されているものより新しいソフトウェアの内容と完全に一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="24177-133">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you will find in newer software than what is listed below.</span></span>

<span data-ttu-id="24177-134">このコースでは、次のハードウェアとソフトウェアをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="24177-134">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="24177-135">開発用 PC</span><span class="sxs-lookup"><span data-stu-id="24177-135">A development PC</span></span>
- [<span data-ttu-id="24177-136">開発者モードが有効になっている Windows 10 の作成者の更新プログラム (またはそれ以降)</span><span class="sxs-lookup"><span data-stu-id="24177-136">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="24177-137">最新の Windows 10 SDK</span><span class="sxs-lookup"><span data-stu-id="24177-137">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="24177-138">Unity 2017.4</span><span class="sxs-lookup"><span data-stu-id="24177-138">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="24177-139">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="24177-139">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="24177-140">開発者モードが有効になっている[Microsoft HoloLens](../../../hololens-hardware-details.md)</span><span class="sxs-lookup"><span data-stu-id="24177-140">A [Microsoft HoloLens](../../../hololens-hardware-details.md) with Developer mode enabled</span></span>
- <span data-ttu-id="24177-141">Azure セットアップとデータ取得のためのインターネットアクセス Microsoft Graph</span><span class="sxs-lookup"><span data-stu-id="24177-141">Internet access for Azure setup and Microsoft Graph data retrieval</span></span>
- <span data-ttu-id="24177-142">有効な **Microsoft アカウント** (個人または職場/学校)</span><span class="sxs-lookup"><span data-stu-id="24177-142">A valid **Microsoft Account** (either personal or work/school)</span></span>
- <span data-ttu-id="24177-143">同じ Microsoft アカウントを使用して、現在の日にスケジュールされているいくつかの会議</span><span class="sxs-lookup"><span data-stu-id="24177-143">A few meetings scheduled for the current day, using the same Microsoft Account</span></span>

### <a name="before-you-start"></a><span data-ttu-id="24177-144">開始する前に</span><span class="sxs-lookup"><span data-stu-id="24177-144">Before you start</span></span>

1.  <span data-ttu-id="24177-145">このプロジェクトのビルドで問題が発生しないように、このチュートリアルで説明されているプロジェクトをルートまたはほぼルートフォルダーに作成することを強くお勧めします (長いフォルダーパスはビルド時に問題を引き起こす可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="24177-145">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="24177-146">HoloLens をセットアップしてテストします。</span><span class="sxs-lookup"><span data-stu-id="24177-146">Set up and test your HoloLens.</span></span> <span data-ttu-id="24177-147">HoloLens のセットアップをサポートする必要がある場合は、 [hololens セットアップに関する記事にアクセスして](https://docs.microsoft.com/hololens/hololens-setup)ください。</span><span class="sxs-lookup"><span data-stu-id="24177-147">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](https://docs.microsoft.com/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="24177-148">新しい HoloLens アプリの開発を開始するときは、調整とセンサーのチューニングを実行することをお勧めします (ユーザーごとにこれらのタスクを実行するのに役立つ場合があります)。</span><span class="sxs-lookup"><span data-stu-id="24177-148">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="24177-149">調整の詳細については、 [「HoloLens の調整に関する記事へのリンク」を](../../../calibration.md#hololens-2)参照してください。</span><span class="sxs-lookup"><span data-stu-id="24177-149">For help on Calibration, please follow this [link to the HoloLens Calibration article](../../../calibration.md#hololens-2).</span></span>

<span data-ttu-id="24177-150">センサーチューニングの詳細については、 [HoloLens センサーチューニングに関する記事へのリンクを](../../../sensor-tuning.md)参照してください。</span><span class="sxs-lookup"><span data-stu-id="24177-150">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](../../../sensor-tuning.md).</span></span>

## <a name="chapter-1---create-your-app-in-the-application-registration-portal"></a><span data-ttu-id="24177-151">第1章-アプリケーション登録ポータルでのアプリの作成</span><span class="sxs-lookup"><span data-stu-id="24177-151">Chapter 1 - Create your app in the Application Registration Portal</span></span>

<span data-ttu-id="24177-152">まず、アプリケーション **登録ポータル** でアプリケーションを作成し、登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24177-152">To begin with, you will need to create and register your application in the **Application Registration Portal**.</span></span>

<span data-ttu-id="24177-153">この章では、アカウントコンテンツにアクセスするために *Microsoft Graph* を呼び出すことができるサービスキーについても説明します。</span><span class="sxs-lookup"><span data-stu-id="24177-153">In this Chapter you will also find the Service Key that will allow you to make calls to *Microsoft Graph* to access your account content.</span></span>

1.  <span data-ttu-id="24177-154">[Microsoft アプリケーション登録ポータル](https://apps.dev.microsoft.com)に移動し、microsoft アカウントでログインします。</span><span class="sxs-lookup"><span data-stu-id="24177-154">Navigate to the [Microsoft Application Registration Portal](https://apps.dev.microsoft.com) and login with your Microsoft Account.</span></span> <span data-ttu-id="24177-155">ログインすると、 **アプリケーション登録ポータル** にリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="24177-155">Once you have logged in, you will be redirected to the **Application Registration Portal**.</span></span>

2.  <span data-ttu-id="24177-156">**[マイアプリケーション**] セクションで、[アプリの **追加**] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-156">In the **My applications** section, click on the button **Add an app**.</span></span>

    ![](images/AzureLabs-Lab311-01.png)![](images/AzureLabs-Lab311-02.png)

    > [!IMPORTANT]
    > <span data-ttu-id="24177-157">以前に *Microsoft Graph* を操作したかどうかによって、**アプリケーション登録ポータル** が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="24177-157">The **Application Registration Portal** can look different, depending on whether you have previously worked with *Microsoft Graph*.</span></span> <span data-ttu-id="24177-158">以下のスクリーンショットには、これらの異なるバージョンが表示されています。</span><span class="sxs-lookup"><span data-stu-id="24177-158">The below screenshots display these different versions.</span></span>

3.  <span data-ttu-id="24177-159">アプリケーションの名前を追加し、[ **作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-159">Add a name for your application and click **Create**.</span></span>

    ![](images/AzureLabs-Lab311-03.png)

4.  <span data-ttu-id="24177-160">アプリケーションが作成されると、アプリケーションのメインページにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="24177-160">Once the application has been created, you will be redirected to the application main page.</span></span> <span data-ttu-id="24177-161">**アプリケーション Id** をコピーし、この値が安全な場所にあることを確認してください。コードですぐに使用します。</span><span class="sxs-lookup"><span data-stu-id="24177-161">Copy the **Application Id** and make sure to note this value somewhere safe, you will use it soon in your code.</span></span>

    ![](images/AzureLabs-Lab311-04.png)

5.  <span data-ttu-id="24177-162">[ **プラットフォーム** ] セクションで、[ **ネイティブアプリケーション** ] が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="24177-162">In the **Platforms** section, make sure **Native Application** is displayed.</span></span> <span data-ttu-id="24177-163">それ *以外* の場合は、[ **プラットフォームの追加** ] をクリックし、[ **ネイティブアプリケーション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="24177-163">If *not* click on **Add Platform** and select **Native Application**.</span></span>

    ![](images/AzureLabs-Lab311-05.png)

6.  <span data-ttu-id="24177-164">同じページを下にスクロールし、[Microsoft Graph の **アクセス許可** ] というセクションで、アプリケーションに対する追加のアクセス許可を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24177-164">Scroll down in the same page and in the section called **Microsoft Graph Permissions** you will need to add additional permissions for the application.</span></span> <span data-ttu-id="24177-165">[委任された **アクセス許可**] の横にある [**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-165">Click on **Add** next to **Delegated Permissions**.</span></span>

    ![](images/AzureLabs-Lab311-06.png)

7.  <span data-ttu-id="24177-166">アプリケーションでユーザーの予定表にアクセスできるようにするには、[カレンダー] というボックスをオンにし **ます。 [読み取り** ] をクリックし、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-166">Since you want your application to access the user's Calendar, check the box called **Calendars.Read** and click **OK**.</span></span>

    ![](images/AzureLabs-Lab311-07.png)

8.  <span data-ttu-id="24177-167">一番下までスクロールし、[ **保存** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-167">Scroll to the bottom and click the **Save** button.</span></span>

    ![](images/AzureLabs-Lab311-08.png)

9.  <span data-ttu-id="24177-168">保存が確認され、 **アプリケーション登録ポータル** からログアウトできます。</span><span class="sxs-lookup"><span data-stu-id="24177-168">Your save will be confirmed, and you can log out from the **Application Registration Portal**.</span></span>

## <a name="chapter-2---set-up-the-unity-project"></a><span data-ttu-id="24177-169">Chapter 2-Unity プロジェクトの設定</span><span class="sxs-lookup"><span data-stu-id="24177-169">Chapter 2 - Set up the Unity project</span></span>

<span data-ttu-id="24177-170">次に示すのは、mixed reality で開発するための一般的な設定です。そのため、他のプロジェクトに適したテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="24177-170">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="24177-171">*Unity* を開き、[**新規**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-171">Open *Unity* and click **New**.</span></span>

    ![](images/AzureLabs-Lab311-09.png)

2.  <span data-ttu-id="24177-172">Unity プロジェクト名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24177-172">You need to provide a Unity project name.</span></span> <span data-ttu-id="24177-173">**Msgraphmr** を挿入します。</span><span class="sxs-lookup"><span data-stu-id="24177-173">Insert **MSGraphMR**.</span></span> <span data-ttu-id="24177-174">プロジェクトテンプレートが **3d** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="24177-174">Make sure the project template is set to **3D**.</span></span> <span data-ttu-id="24177-175">場所を適切な **場所** に設定します (ルートディレクトリの方が適していることに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="24177-175">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="24177-176">次に、[ **プロジェクトの作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-176">Then, click **Create project**.</span></span>

    ![](images/AzureLabs-Lab311-10.png)

3.  <span data-ttu-id="24177-177">Unity を開いている場合は、[既定の **スクリプトエディター** ] が **Visual Studio** に設定されていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24177-177">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="24177-178">[設定の **編集**] に移動し、  >  **Preferences** 新しいウィンドウで [**外部ツール**] に移動します。</span><span class="sxs-lookup"><span data-stu-id="24177-178">Go to **Edit** > **Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="24177-179">**外部スクリプトエディター** を **Visual Studio 2017** に変更します。</span><span class="sxs-lookup"><span data-stu-id="24177-179">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="24177-180">[ **基本設定** ] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="24177-180">Close the **Preferences** window.</span></span>

    ![](images/AzureLabs-Lab311-11.png)

4.  <span data-ttu-id="24177-181">ファイルの **File**  >  **ビルド設定** に移動して [**ユニバーサル Windows プラットフォーム**] を選択し、[**プラットフォームの切り替え**] ボタンをクリックして選択内容を適用します。</span><span class="sxs-lookup"><span data-stu-id="24177-181">Go to **File** > **Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![](images/AzureLabs-Lab311-12.png)

5.  <span data-ttu-id="24177-182">**ファイル** の  >  **ビルド設定** でも、次のことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="24177-182">While still in **File** > **Build Settings**, make sure that:</span></span>

    1. <span data-ttu-id="24177-183">**ターゲットデバイス** が **HoloLens** に設定されています</span><span class="sxs-lookup"><span data-stu-id="24177-183">**Target Device** is set to **HoloLens**</span></span>
    2. <span data-ttu-id="24177-184">**ビルドの種類** が **D3D** に設定されています</span><span class="sxs-lookup"><span data-stu-id="24177-184">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="24177-185">**SDK** は最新の **インストール** に設定されています</span><span class="sxs-lookup"><span data-stu-id="24177-185">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="24177-186">**Visual Studio のバージョン** が、**インストールされている最新** バージョンに設定されています</span><span class="sxs-lookup"><span data-stu-id="24177-186">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="24177-187">**ビルドと実行** は **ローカルコンピューター** に設定されています</span><span class="sxs-lookup"><span data-stu-id="24177-187">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="24177-188">シーンを保存し、ビルドに追加します。</span><span class="sxs-lookup"><span data-stu-id="24177-188">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="24177-189">これを行うには、[開いている **シーンの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="24177-189">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="24177-190">保存ウィンドウが表示されます。</span><span class="sxs-lookup"><span data-stu-id="24177-190">A save window will appear.</span></span>

            ![](images/AzureLabs-Lab311-13.png)

        2. <span data-ttu-id="24177-191">この、および将来のシーン用に新しいフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="24177-191">Create a new folder for this, and any future, scene.</span></span> <span data-ttu-id="24177-192">[ **新しいフォルダー** ] ボタンを選択し、新しいフォルダーを作成するには、「 **シーン**」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="24177-192">Select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![](images/AzureLabs-Lab311-14.png)

        3. <span data-ttu-id="24177-193">新しく作成した [ **シーン** ] フォルダーを開き、[ *ファイル名*: テキスト] フィールドに「 **MR_ComputerVisionScene**」と入力し、[ **保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-193">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![](images/AzureLabs-Lab311-15.png)

            > [!IMPORTANT] 
            > <span data-ttu-id="24177-194">Unity プロジェクトに関連付けられている必要があるため、Unity のシーンを *Assets* フォルダー内に保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24177-194">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity project.</span></span> <span data-ttu-id="24177-195">Unity プロジェクトを構成する一般的な方法は、シーンフォルダー (およびその他の同様のフォルダー) を作成することです。</span><span class="sxs-lookup"><span data-stu-id="24177-195">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7.  <span data-ttu-id="24177-196">それ以外の設定は、[ *ビルド設定*] の [既定] のままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="24177-196">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6.  <span data-ttu-id="24177-197">[ *ビルドの設定* ] ウィンドウで、[ **プレーヤーの設定** ] ボタンをクリックします。これにより、 *インスペクター* が配置されている領域の関連パネルが開きます。</span><span class="sxs-lookup"><span data-stu-id="24177-197">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![](images/AzureLabs-Lab311-16.png)

7. <span data-ttu-id="24177-198">このパネルでは、いくつかの設定を確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24177-198">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="24177-199">[ **その他の設定** ] タブで、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="24177-199">In the **Other Settings** tab:</span></span>

        1.  <span data-ttu-id="24177-200">**Scripting** **Runtime のバージョン** は **実験的** (.net 4.6 と同等) である必要があります。これにより、エディターを再起動する必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="24177-200">**Scripting** **Runtime Version** should be **Experimental** (.NET 4.6 Equivalent), which will trigger a need to restart the Editor.</span></span>

        2. <span data-ttu-id="24177-201">**バックエンド** は **.net** である必要があります</span><span class="sxs-lookup"><span data-stu-id="24177-201">**Scripting Backend** should be **.NET**</span></span>

        3. <span data-ttu-id="24177-202">**API 互換性レベル** は **.net 4.6** である必要があります</span><span class="sxs-lookup"><span data-stu-id="24177-202">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![](images/AzureLabs-Lab311-17.png)

    2.  <span data-ttu-id="24177-203">[ **発行の設定** ] タブの [ **機能**] で、次の項目を確認します。</span><span class="sxs-lookup"><span data-stu-id="24177-203">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        - <span data-ttu-id="24177-204">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="24177-204">**InternetClient**</span></span>

            ![](images/AzureLabs-Lab311-18.png)

    3.  <span data-ttu-id="24177-205">パネルの下にある [ **XR settings** ( **発行設定**] の下にあります) で、[ **Virtual reality がサポートさ** れる] をオンにして、 **Windows Mixed reality SDK** が追加されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="24177-205">Further down the panel, in **XR Settings** (found below **Publish Settings**), check **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![](images/AzureLabs-Lab311-19.png)

8.  <span data-ttu-id="24177-206">*ビルド設定* に戻ると、 *Unity C# プロジェクト* はグレーで表示されなくなりました。この横にあるチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="24177-206">Back in *Build Settings*, *Unity C# Projects* is no longer greyed out; check the checkbox next to this.</span></span>

9.  <span data-ttu-id="24177-207">*[ビルド設定]* ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="24177-207">Close the *Build Settings* window.</span></span>

10.  <span data-ttu-id="24177-208">シーンとプロジェクトを保存します (**ファイル**  >  **保存シーン/ファイル**  >  **保存プロジェクト**)。</span><span class="sxs-lookup"><span data-stu-id="24177-208">Save your scene and project (**FILE** > **SAVE SCENES / FILE** > **SAVE PROJECT**).</span></span>

## <a name="chapter-3---import-libraries-in-unity"></a><span data-ttu-id="24177-209">章 3-Unity でライブラリをインポートする</span><span class="sxs-lookup"><span data-stu-id="24177-209">Chapter 3 - Import Libraries in Unity</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24177-210">このコースの *Unity セットアップ* コンポーネントをスキップしてコードに直接進む場合は、unitypackage をダウンロードして、[**カスタムパッケージ**](https://docs.unity3d.com/Manual/AssetPackages.html)としてプロジェクトにインポートしてから、[第5章](#chapter-5---create-meetingsui-class)から続行することをお勧めします [。](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage)</span><span class="sxs-lookup"><span data-stu-id="24177-210">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [Azure-MR-311.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/Azure-MR-311.unitypackage), import it into your project as a [**Custom Package**](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5---create-meetingsui-class).</span></span>

<span data-ttu-id="24177-211">Unity 内で *Microsoft Graph* を使用するには、  **Microsoft Identity. Client** DLL を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24177-211">To use *Microsoft Graph* within Unity you need to make use of the  **Microsoft.Identity.Client** DLL.</span></span> <span data-ttu-id="24177-212">Microsoft Graph SDK を使用することもできますが、Unity プロジェクトをビルドした後に NuGet パッケージを追加する必要があります (つまり、プロジェクトのビルド後に編集することになります)。</span><span class="sxs-lookup"><span data-stu-id="24177-212">It is possible to use the Microsoft Graph SDK, however, it will require the addition of a NuGet package after you build the Unity project (meaning editing the project post-build).</span></span> <span data-ttu-id="24177-213">必要な Dll を Unity に直接インポートする方が簡単であると考えられます。</span><span class="sxs-lookup"><span data-stu-id="24177-213">It is considered simpler to import the required DLLs directly into Unity.</span></span>

> [!NOTE]
> <span data-ttu-id="24177-214">現在、Unity には、インポート後にプラグインを再構成する必要がある既知の問題があります。</span><span class="sxs-lookup"><span data-stu-id="24177-214">There is currently a known issue in Unity which requires plugins to be reconfigured after import.</span></span> <span data-ttu-id="24177-215">バグが解決された後、これらの手順 (このセクションでは 4-7) は不要になりました。</span><span class="sxs-lookup"><span data-stu-id="24177-215">These steps (4 - 7 in this section) will no longer be required after the bug has been resolved.</span></span>

<span data-ttu-id="24177-216">*Microsoft Graph* を独自のプロジェクトにインポートするには、 [MSGraph_LabPlugins.zip ファイルをダウンロード](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage)します。</span><span class="sxs-lookup"><span data-stu-id="24177-216">To import *Microsoft Graph* into your own project, [download the MSGraph_LabPlugins.zip file](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20311%20-%20Microsoft%20Graph/MSGraph_LabPlugins.unitypackage).</span></span> <span data-ttu-id="24177-217">このパッケージは、テスト済みのライブラリのバージョンで作成されています。</span><span class="sxs-lookup"><span data-stu-id="24177-217">This package has been created with versions of the libraries that have been tested.</span></span>

<span data-ttu-id="24177-218">カスタム Dll を Unity プロジェクトに追加する方法の詳細については、次の [リンク](https://docs.unity3d.com/Manual/UsingDLL.html)先を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24177-218">If you wish to know more about how to add custom DLLs to your Unity project, [follow this link](https://docs.unity3d.com/Manual/UsingDLL.html).</span></span>

<span data-ttu-id="24177-219">パッケージをインポートするには:</span><span class="sxs-lookup"><span data-stu-id="24177-219">To import the package:</span></span>

1.  <span data-ttu-id="24177-220">[**アセット**  >  **インポートパッケージ**  >  **カスタムパッケージ**] メニューオプションを使用して unity に unity パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="24177-220">Add the Unity Package to Unity by using the **Assets** > **Import Package** > **Custom Package** menu option.</span></span> <span data-ttu-id="24177-221">ダウンロードしたパッケージを選択します。</span><span class="sxs-lookup"><span data-stu-id="24177-221">Select the package you just downloaded.</span></span>

2.  <span data-ttu-id="24177-222">ポップアップ表示された [ **Unity パッケージのインポート** ] ボックスで、 **プラグイン** (およびそれを含む) のすべてが選択されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="24177-222">In the **Import Unity Package** box that pops up, ensure everything under (and including) **Plugins** is selected.</span></span>

    ![](images/AzureLabs-Lab311-20.png)

3.  <span data-ttu-id="24177-223">[ **インポート** ] ボタンをクリックして、プロジェクトに項目を追加します。</span><span class="sxs-lookup"><span data-stu-id="24177-223">Click the **Import** button to add the items to your project.</span></span>

4.  <span data-ttu-id="24177-224">[*プロジェクト] パネル* の [**プラグイン**] の下にある **msgraph** フォルダーにアクセスし、[ **Microsoft. Identity. Client**] という名前のプラグインを選択します。</span><span class="sxs-lookup"><span data-stu-id="24177-224">Go to the **MSGraph** folder under **Plugins** in the *Project Panel* and select the plugin called **Microsoft.Identity.Client**.</span></span>

    ![](images/AzureLabs-Lab311-21.png)

5.  <span data-ttu-id="24177-225">*プラグイン* を選択した状態で、**任意のプラットフォーム** がオフになっていることを確認し、[ **wsaplayer** ] もオフになっていることを確認してから、[**適用**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-225">With the *plugin* selected, ensure that **Any Platform** is unchecked, then ensure that **WSAPlayer** is also unchecked, then click **Apply**.</span></span> <span data-ttu-id="24177-226">これは、ファイルが正しく構成されていることを確認するためのものです。</span><span class="sxs-lookup"><span data-stu-id="24177-226">This is just to confirm that the files are configured correctly.</span></span>

    ![](images/AzureLabs-Lab311-22.png)

    > [!NOTE] 
    > <span data-ttu-id="24177-227">これらのプラグインをマークすると、Unity エディターでのみ使用するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="24177-227">Marking these plugins configures them to only be used in the Unity Editor.</span></span> <span data-ttu-id="24177-228">WSA フォルダーには、プロジェクトが Unity からユニバーサル Windows アプリケーションとしてエクスポートされた後に使用される、異なる Dll のセットがあります。</span><span class="sxs-lookup"><span data-stu-id="24177-228">There are a different set of DLLs in the WSA folder which will be used after the project is exported from Unity as a Universal Windows Application.</span></span>

6.  <span data-ttu-id="24177-229">次に、 **Msgraph** フォルダー内の **WSA** フォルダーを開く必要があります。</span><span class="sxs-lookup"><span data-stu-id="24177-229">Next, you need to open the **WSA** folder, within the **MSGraph** folder.</span></span> <span data-ttu-id="24177-230">先ほど構成したものと同じファイルのコピーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="24177-230">You will see a copy of the same file you just configured.</span></span> <span data-ttu-id="24177-231">ファイルを選択し、次にインスペクターで次のようにします。</span><span class="sxs-lookup"><span data-stu-id="24177-231">Select the file, and then in the inspector:</span></span>

    -   <span data-ttu-id="24177-232">すべての **プラットフォーム** が **オフ** になっていて、 **wsaplayer** **のみ** が **チェック** されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="24177-232">ensure that **Any Platform** is **unchecked**, and that **only** **WSAPlayer** is **checked**.</span></span>

    -   <span data-ttu-id="24177-233">**SDK** が **UWP** に設定され、**スクリプトバックエンド** が **ドット Net** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="24177-233">Ensure **SDK** is set to **UWP**, and **Scripting Backend** is set to **Dot Net**</span></span>

    -   <span data-ttu-id="24177-234">" **処理しない** " が **オン** になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="24177-234">Ensure that **Don't process** is **checked**.</span></span>

        ![](images/AzureLabs-Lab311-23.png)

7.  <span data-ttu-id="24177-235">**[適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-235">Click **Apply**.</span></span>

## <a name="chapter-4---camera-setup"></a><span data-ttu-id="24177-236">第4章-カメラの設定</span><span class="sxs-lookup"><span data-stu-id="24177-236">Chapter 4 - Camera Setup</span></span>

<span data-ttu-id="24177-237">この章では、シーンのメインカメラを設定します。</span><span class="sxs-lookup"><span data-stu-id="24177-237">During this Chapter you will set up the Main Camera of your scene:</span></span>

1.  <span data-ttu-id="24177-238">[ *階層] パネル* で、 **メインカメラ** を選択します。</span><span class="sxs-lookup"><span data-stu-id="24177-238">In the *Hierarchy Panel*, select the **Main Camera**.</span></span>

2.  <span data-ttu-id="24177-239">選択すると、 **メインカメラ** のすべてのコンポーネントが [ *インスペクター* ] パネルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="24177-239">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector* panel.</span></span>

    1.  <span data-ttu-id="24177-240">**カメラオブジェクト** は **メインカメラ** という名前にする必要があります (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="24177-240">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>

    2.  <span data-ttu-id="24177-241">メインカメラの **タグ** は、 **maincamera** に設定する必要があります (スペルに注意してください)。</span><span class="sxs-lookup"><span data-stu-id="24177-241">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>

    3.  <span data-ttu-id="24177-242">**変換位置** が **0、0、0** に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="24177-242">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>

    4.  <span data-ttu-id="24177-243">**クリアフラグ** を **純色** に設定する</span><span class="sxs-lookup"><span data-stu-id="24177-243">Set **Clear Flags** to **Solid Color**</span></span>

    5.  <span data-ttu-id="24177-244">カメラコンポーネントの **背景色** を **黒、アルファ 0** **(16 進コード: #00000000)** に設定します。</span><span class="sxs-lookup"><span data-stu-id="24177-244">Set the **Background Color** of the Camera Component to **Black, Alpha 0** **(Hex Code: #00000000)**</span></span>

        ![](images/AzureLabs-Lab311-24.png)

3.  <span data-ttu-id="24177-245">*階層パネル* の最終的なオブジェクト構造は、次の図に示すようになります。</span><span class="sxs-lookup"><span data-stu-id="24177-245">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![](images/AzureLabs-Lab311-25.png)

## <a name="chapter-5---create-meetingsui-class"></a><span data-ttu-id="24177-246">Chapter 5-MeetingsUI クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="24177-246">Chapter 5 - Create MeetingsUI class</span></span>

<span data-ttu-id="24177-247">作成する必要のある最初のスクリプトは **MeetingsUI** です。これは、アプリケーションの UI (ウェルカムメッセージ、指示、および会議の詳細) をホストおよび設定する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="24177-247">The first script you need to create is **MeetingsUI**, which is responsible for hosting and populating the UI of the application (welcome message, instructions and the meetings details).</span></span>

<span data-ttu-id="24177-248">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="24177-248">To create this class:</span></span>

1.  <span data-ttu-id="24177-249">[*プロジェクト] パネル* の [**アセット**] フォルダーを右クリックし、[フォルダーの **作成**] を選択し  >  **Folder** ます。</span><span class="sxs-lookup"><span data-stu-id="24177-249">Right-click on the **Assets** folder in the *Project Panel*, then select **Create** > **Folder**.</span></span> <span data-ttu-id="24177-250">フォルダーに **スクリプト** の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="24177-250">Name the folder **Scripts**.</span></span>

    ![](images/AzureLabs-Lab311-26.png)
    ![](images/AzureLabs-Lab311-27.png)

2.  <span data-ttu-id="24177-251">**Scripts** フォルダーを開き、そのフォルダー内で右クリックして、 **Create**[  >  **C# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-251">Open the **Scripts** folder then, within that folder, right-click, **Create** > **C# Script**.</span></span> <span data-ttu-id="24177-252">スクリプトに MeetingsUI という名前を指定 **します。**</span><span class="sxs-lookup"><span data-stu-id="24177-252">Name the script **MeetingsUI.**</span></span>

    ![](images/AzureLabs-Lab311-28.png)

3.  <span data-ttu-id="24177-253">新しい **MeetingsUI** スクリプトをダブルクリックして、 *Visual Studio* で開きます。</span><span class="sxs-lookup"><span data-stu-id="24177-253">Double-click on the new **MeetingsUI** script to open it with *Visual Studio*.</span></span>

4.  <span data-ttu-id="24177-254">次の名前空間を挿入します。</span><span class="sxs-lookup"><span data-stu-id="24177-254">Insert the following namespaces:</span></span>

    ```csharp
    using System;
    using UnityEngine;
    ```

5.  <span data-ttu-id="24177-255">クラス内で、次の変数を挿入します。</span><span class="sxs-lookup"><span data-stu-id="24177-255">Inside the class insert the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Allows this class to behave like a singleton
        /// </summary>
        public static MeetingsUI Instance;

        /// <summary>
        /// The 3D text of the scene
        /// </summary>
        private TextMesh _meetingDisplayTextMesh;
    ```

6.  <span data-ttu-id="24177-256">次に、 **Start ()** メソッドを置き換え、起動前 **()** メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="24177-256">Then replace the **Start()** method and add an **Awake()** method.</span></span> <span data-ttu-id="24177-257">これらは、クラスの初期化時に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="24177-257">These will be called when the class initializes:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization
        /// </summary>
        void Awake()
        {
            Instance = this;
        }

        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        void Start ()
        {
            // Creating the text mesh within the scene
            _meetingDisplayTextMesh = CreateMeetingsDisplay();
        }
    ```

7.  <span data-ttu-id="24177-258">*ミーティング UI* を作成し、要求されたときに現在の会議に設定するためのメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="24177-258">Add the methods responsible for creating the *Meetings UI* and populate it with the current meetings when requested:</span></span>

    ```csharp    
        /// <summary>
        /// Set the welcome message for the user
        /// </summary>
        internal void WelcomeUser(string userName)
        {
            if(!string.IsNullOrEmpty(userName))
            {
                _meetingDisplayTextMesh.text = $"Welcome {userName}";
            }
            else 
            {
                _meetingDisplayTextMesh.text = "Welcome";
            }
        }

        /// <summary>
        /// Set up the parameters for the UI text
        /// </summary>
        /// <returns>Returns the 3D text in the scene</returns>
        private TextMesh CreateMeetingsDisplay()
        {
            GameObject display = new GameObject();
            display.transform.localScale = new Vector3(0.03f, 0.03f, 0.03f);
            display.transform.position = new Vector3(-3.5f, 2f, 9f);
            TextMesh textMesh = display.AddComponent<TextMesh>();
            textMesh.anchor = TextAnchor.MiddleLeft;
            textMesh.alignment = TextAlignment.Left;
            textMesh.fontSize = 80;
            textMesh.text = "Welcome! \nPlease gaze at the button" +
                "\nand use the Tap Gesture to display your meetings";

            return textMesh;
        }

        /// <summary>
        /// Adds a new Meeting in the UI by chaining the existing UI text
        /// </summary>
        internal void AddMeeting(string subject, DateTime dateTime, string location)
        {
            string newText = $"\n{_meetingDisplayTextMesh.text}\n\n Meeting,\nSubject: {subject},\nToday at {dateTime},\nLocation: {location}";

            _meetingDisplayTextMesh.text = newText;
        }
    ```

8. <span data-ttu-id="24177-259">**Update ()** メソッドを **削除** し、Unity に戻る前に変更を Visual Studio に **保存** します。</span><span class="sxs-lookup"><span data-stu-id="24177-259">**Delete** the **Update()** method, and **save your changes** in Visual Studio before returning to Unity.</span></span> 

## <a name="chapter-6---create-the-graph-class"></a><span data-ttu-id="24177-260">Chapter 6-Graph クラスの作成</span><span class="sxs-lookup"><span data-stu-id="24177-260">Chapter 6 - Create the Graph class</span></span>

<span data-ttu-id="24177-261">次に作成するスクリプトは、 **グラフ** スクリプトです。</span><span class="sxs-lookup"><span data-stu-id="24177-261">The next script to create is the **Graph** script.</span></span> <span data-ttu-id="24177-262">このスクリプトは、ユーザーを認証し、現在の日のスケジュールされた会議をユーザーの予定表から取得するための呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="24177-262">This script is responsible for making the calls to authenticate the user and retrieve the scheduled meetings for the current day from the user's calendar.</span></span>

<span data-ttu-id="24177-263">このクラスを作成するには:</span><span class="sxs-lookup"><span data-stu-id="24177-263">To create this class:</span></span>

1.  <span data-ttu-id="24177-264">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="24177-264">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="24177-265">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-265">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="24177-266">スクリプト **グラフ** にという名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="24177-266">Name the script **Graph**.</span></span>

3.  <span data-ttu-id="24177-267">スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="24177-267">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="24177-268">次の名前空間を挿入します。</span><span class="sxs-lookup"><span data-stu-id="24177-268">Insert the following namespaces:</span></span>

    ```csharp
    using System.Collections.Generic;
    using UnityEngine;
    using Microsoft.Identity.Client;
    using System;
    using System.Threading.Tasks;
    
    #if !UNITY_EDITOR && UNITY_WSA
    using System.Net.Http;
    using System.Net.Http.Headers;
    using Windows.Storage;
    #endif
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="24177-269">このスクリプトのコードの一部は、 [プリコンパイルディレクティブ](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html)にラップされていることに注意してください。これは、Visual Studio ソリューションをビルドするときにライブラリの問題を回避するためです。</span><span class="sxs-lookup"><span data-stu-id="24177-269">You will notice that parts of the code in this script are wrapped around [Precompile Directives](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html), this is to avoid issues with the libraries when building the Visual Studio Solution.</span></span>

5.  <span data-ttu-id="24177-270">**Start ()** および **Update ()** メソッドは使用されないため、削除します。</span><span class="sxs-lookup"><span data-stu-id="24177-270">Delete the **Start()** and **Update()** methods, as they will not be used.</span></span>

6.  <span data-ttu-id="24177-271">**Graph** クラスの外部で、次のオブジェクトを挿入します。これは、毎日スケジュールされた会議を表す JSON オブジェクトを逆シリアル化するために必要です。</span><span class="sxs-lookup"><span data-stu-id="24177-271">Outside the **Graph** class, insert the following objects, which are necessary to deserialize the JSON object representing the daily scheduled meetings:</span></span>

    ```csharp
    /// <summary>
    /// The object hosting the scheduled meetings
    /// </summary>
    [Serializable]
    public class Rootobject
    {
        public List<Value> value;
    }

    [Serializable]
    public class Value
    {
        public string subject { get; set; }
        public StartTime start { get; set; }
        public Location location { get; set; }
    }

    [Serializable]
    public class StartTime
    {
        public string dateTime;

        private DateTime? _startDateTime;
        public DateTime StartDateTime
        {
            get
            {
                if (_startDateTime != null)
                    return _startDateTime.Value;
                DateTime dt;
                DateTime.TryParse(dateTime, out dt);
                _startDateTime = dt;
                return _startDateTime.Value;
            }
        }
    }

    [Serializable]
    public class Location
    {
        public string displayName { get; set; }
    }
    ```

7.  <span data-ttu-id="24177-272">**Graph** クラス内に、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="24177-272">Inside the **Graph** class, add the following variables:</span></span>

    ```csharp    
        /// <summary>
        /// Insert your Application Id here
        /// </summary>
        private string _appId = "-- Insert your Application Id here --";

        /// <summary>
        /// Application scopes, determine Microsoft Graph accessibility level to user account
        /// </summary>
        private IEnumerable<string> _scopes = new List<string>() { "User.Read", "Calendars.Read" };

        /// <summary>
        /// Microsoft Graph API, user reference
        /// </summary>
        private PublicClientApplication _client;

        /// <summary>
        /// Microsoft Graph API, authentication
        /// </summary>
        private AuthenticationResult _authResult;

    ```

    > [!NOTE]
    > <span data-ttu-id="24177-273">**AppId** の値を、 **[第1章](#chapter-1---create-your-app-in-the-application-registration-portal)の手順 4**. でメモした **アプリ Id** に変更します。</span><span class="sxs-lookup"><span data-stu-id="24177-273">Change the **appId** value to be the **App Id** that you have noted in **[Chapter 1](#chapter-1---create-your-app-in-the-application-registration-portal), step 4**.</span></span> <span data-ttu-id="24177-274">この値は、アプリケーション登録 **ポータル** のアプリケーション登録ページに表示される値と同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="24177-274">This value should be the same as that displayed in the **Application Registration Portal,** in your application registration page.</span></span>

8.  <span data-ttu-id="24177-275">**Graph** クラス内で、 **SignInAsync ()** メソッドと **AquireTokenAsync ()** メソッドを追加します。これにより、ユーザーはログイン資格情報を挿入するように求められます。</span><span class="sxs-lookup"><span data-stu-id="24177-275">Within the **Graph** class, add the methods **SignInAsync()** and **AquireTokenAsync()**, that will prompt the user to insert the log-in credentials.</span></span>

    ```csharp
        /// <summary>
        /// Begin the Sign In process using Microsoft Graph Library
        /// </summary>
        internal async void SignInAsync()
        {
    #if !UNITY_EDITOR && UNITY_WSA
            // Set up Grap user settings, determine if needs auth
            ApplicationDataContainer localSettings = ApplicationData.Current.LocalSettings;
            string userId = localSettings.Values["UserId"] as string;
            _client = new PublicClientApplication(_appId);

            // Attempt authentication
            _authResult = await AcquireTokenAsync(_client, _scopes, userId);

            // If authentication is successful, retrieve the meetings
            if (!string.IsNullOrEmpty(_authResult.AccessToken))
            {
                // Once Auth as been completed, find the meetings for the day
                await ListMeetingsAsync(_authResult.AccessToken);
            }
    #endif
        }

        /// <summary>
        /// Attempt to retrieve the Access Token by either retrieving
        /// previously stored credentials or by prompting user to Login
        /// </summary>
        private async Task<AuthenticationResult> AcquireTokenAsync(
            IPublicClientApplication app, IEnumerable<string> scopes, string userId)
        {
            IUser user = !string.IsNullOrEmpty(userId) ? app.GetUser(userId) : null;
            string userName = user != null ? user.Name : "null";

            // Once the User name is found, display it as a welcome message
            MeetingsUI.Instance.WelcomeUser(userName);

            // Attempt to Log In the user with a pre-stored token. Only happens
            // in case the user Logged In with this app on this device previously
            try
            {
                _authResult = await app.AcquireTokenSilentAsync(scopes, user);
            }
            catch (MsalUiRequiredException)
            {
                // Pre-stored token not found, prompt the user to log-in 
                try
                {
                    _authResult = await app.AcquireTokenAsync(scopes);
                }
                catch (MsalException msalex)
                {
                    Debug.Log($"Error Acquiring Token: {msalex.Message}");
                    return _authResult;
                }
            }
            
            MeetingsUI.Instance.WelcomeUser(_authResult.User.Name);

    #if !UNITY_EDITOR && UNITY_WSA
            ApplicationData.Current.LocalSettings.Values["UserId"] = 
            _authResult.User.Identifier;
    #endif
            return _authResult;
        }
    ```

9.  <span data-ttu-id="24177-276">次の2つのメソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="24177-276">Add the following two methods:</span></span>

    1.  <span data-ttu-id="24177-277">**BuildTodayCalendarEndpoint ()**。スケジュールされた会議を取得する日付と期間を指定する URI を作成します。</span><span class="sxs-lookup"><span data-stu-id="24177-277">**BuildTodayCalendarEndpoint()**, which builds the URI specifying the day, and time span, in which the scheduled meetings are retrieved.</span></span>

    2.  <span data-ttu-id="24177-278">**List面会 Sasync ()** は、スケジュールされた会議を *Microsoft Graph* から要求します。</span><span class="sxs-lookup"><span data-stu-id="24177-278">**ListMeetingsAsync()**, which requests the scheduled meetings from *Microsoft Graph*.</span></span>

    ```csharp
        /// <summary>
        /// Build the endpoint to retrieve the meetings for the current day.
        /// </summary>
        /// <returns>Returns the Calendar Endpoint</returns>
        public string BuildTodayCalendarEndpoint()
        {
            DateTime startOfTheDay = DateTime.Today.AddDays(0);
            DateTime endOfTheDay = DateTime.Today.AddDays(1);
            DateTime startOfTheDayUTC = startOfTheDay.ToUniversalTime();
            DateTime endOfTheDayUTC = endOfTheDay.ToUniversalTime();

            string todayDate = startOfTheDayUTC.ToString("o");
            string tomorrowDate = endOfTheDayUTC.ToString("o");
            string todayCalendarEndpoint = string.Format(
                "https://graph.microsoft.com/v1.0/me/calendarview?startdatetime={0}&enddatetime={1}",
                todayDate,
                tomorrowDate);

            return todayCalendarEndpoint;
        }

        /// <summary>
        /// Request all the scheduled meetings for the current day.
        /// </summary>
        private async Task ListMeetingsAsync(string accessToken)
        {
    #if !UNITY_EDITOR && UNITY_WSA
            var http = new HttpClient();

            http.DefaultRequestHeaders.Authorization = 
            new AuthenticationHeaderValue("Bearer", accessToken);
            var response = await http.GetAsync(BuildTodayCalendarEndpoint());

            var jsonResponse = await response.Content.ReadAsStringAsync();

            Rootobject rootObject = new Rootobject();
            try
            {
                // Parse the JSON response.
                rootObject = JsonUtility.FromJson<Rootobject>(jsonResponse);

                // Sort the meeting list by starting time.
                rootObject.value.Sort((x, y) => DateTime.Compare(x.start.StartDateTime, y.start.StartDateTime));

                // Populate the UI with the meetings.
                for (int i = 0; i < rootObject.value.Count; i++)
                {
                    MeetingsUI.Instance.AddMeeting(rootObject.value[i].subject,
                                                rootObject.value[i].start.StartDateTime.ToLocalTime(),
                                                rootObject.value[i].location.displayName);
                }
            }
            catch (Exception ex)
            {
                Debug.Log($"Error = {ex.Message}");
                return;
            }
    #endif
        }
    ```

10. <span data-ttu-id="24177-279">これで、 **グラフ** スクリプトが完成しました。</span><span class="sxs-lookup"><span data-stu-id="24177-279">You have now completed the **Graph** script.</span></span> <span data-ttu-id="24177-280">Unity に戻る前に **、変更** を Visual Studio に保存します。</span><span class="sxs-lookup"><span data-stu-id="24177-280">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-7---create-the-gazeinput-script"></a><span data-ttu-id="24177-281">第7章-GazeInput スクリプトの作成</span><span class="sxs-lookup"><span data-stu-id="24177-281">Chapter 7 - Create the GazeInput script</span></span>

<span data-ttu-id="24177-282">次に、 **GazeInput** を作成します。</span><span class="sxs-lookup"><span data-stu-id="24177-282">You will now create the **GazeInput**.</span></span> <span data-ttu-id="24177-283">このクラスは、**メインカメラ** からの **Raycast** を使用して、前に射影したユーザーの宝石を処理し、追跡します。</span><span class="sxs-lookup"><span data-stu-id="24177-283">This class handles and keeps track of the user's gaze, using a **Raycast** coming from the **Main Camera**, projecting forward.</span></span>

<span data-ttu-id="24177-284">スクリプトを作成するには:</span><span class="sxs-lookup"><span data-stu-id="24177-284">To create the script:</span></span>

1.  <span data-ttu-id="24177-285">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="24177-285">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="24177-286">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-286">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="24177-287">スクリプトに **GazeInput** という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="24177-287">Name the script **GazeInput**.</span></span>

3.  <span data-ttu-id="24177-288">スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="24177-288">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="24177-289">シリアル化できるように、次のいずれかに一致するように名前空間コードを変更し、 **GazeInput** クラスの上に "**\[ Serializable \]**" タグを追加します。</span><span class="sxs-lookup"><span data-stu-id="24177-289">Change the namespaces code to match the one below, along with adding the '**\[System.Serializable\]**' tag above your **GazeInput** class, so that it can be serialized:</span></span>

    ```csharp
    using UnityEngine;

    /// <summary>
    /// Class responsible for the User's Gaze interactions
    /// </summary>
    [System.Serializable]
    public class GazeInput : MonoBehaviour
    {
    ```

5.  <span data-ttu-id="24177-290">**GazeInput** クラス内で、次の変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="24177-290">Inside the **GazeInput** class, add the following variables:</span></span>

    ```csharp    
        [Tooltip("Used to compare whether an object is to be interacted with.")]
        internal string InteractibleTag = "SignInButton";

        /// <summary>
        /// Length of the gaze
        /// </summary>
        internal float GazeMaxDistance = 300;

        /// <summary>
        /// Object currently gazed
        /// </summary>
        internal GameObject FocusedObject { get; private set; }

        internal GameObject oldFocusedObject { get; private set; }

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

6.  <span data-ttu-id="24177-291">**CreateCursor ()** メソッドを追加し、シーンに HoloLens カーソルを作成し、 **Start ()** メソッドからメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="24177-291">Add the **CreateCursor()** method to create the HoloLens cursor in the scene, and call the method from the **Start()** method:</span></span>

    ```csharp    
        /// <summary>
        /// Start method used upon initialisation.
        /// </summary>
        internal virtual void Start()
        {
            FocusedObject = null;
            Cursor = CreateCursor();
        }

        /// <summary>
        /// Method to create a cursor object.
        /// </summary>
        internal GameObject CreateCursor()
        {
            GameObject newCursor = GameObject.CreatePrimitive(PrimitiveType.Sphere);
            newCursor.SetActive(false);
            // Remove the collider, so it doesn't block raycast.
            Destroy(newCursor.GetComponent<SphereCollider>());
            newCursor.transform.localScale = new Vector3(0.05f, 0.05f, 0.05f);
            Material mat = new Material(Shader.Find("Diffuse"));
            newCursor.GetComponent<MeshRenderer>().material = mat;
            mat.color = Color.HSVToRGB(0.0223f, 0.7922f, 1.000f);
            newCursor.SetActive(true);

            return newCursor;
        }
    ```

7.  <span data-ttu-id="24177-292">次のメソッドを使用すると、Raycast を有効にし、フォーカスのあるオブジェクトを追跡できます。</span><span class="sxs-lookup"><span data-stu-id="24177-292">The following methods enable the gaze Raycast and keep track of the focused objects.</span></span>

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
        if (oldFocusedObject != null)
        {
            if (oldFocusedObject.CompareTag(InteractibleTag))
            {
                // Provide the 'Gaze Exited' event.
                oldFocusedObject.SendMessage("OnGazeExited", SendMessageOptions.DontRequireReceiver);
            }
        }
    }
    ```

    ```csharp
        private void UpdateRaycast()
        {
            // Set the old focused gameobject.
            oldFocusedObject = FocusedObject;
            RaycastHit hitInfo;

            // Initialise Raycasting.
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
            if (FocusedObject != oldFocusedObject)
            {
                ResetFocusedObject();
                if (FocusedObject != null)
                {
                    if (FocusedObject.CompareTag(InteractibleTag))
                    {
                        // Provide the 'Gaze Entered' event.
                        FocusedObject.SendMessage("OnGazeEntered", 
                            SendMessageOptions.DontRequireReceiver);
                    }
                }
            }
        }
    ```

8.  <span data-ttu-id="24177-293">Unity に戻る前に **、変更** を Visual Studio に保存します。</span><span class="sxs-lookup"><span data-stu-id="24177-293">**Save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-8---create-the-interactions-class"></a><span data-ttu-id="24177-294">章 8-相互作用クラスを作成する</span><span class="sxs-lookup"><span data-stu-id="24177-294">Chapter 8 - Create the Interactions class</span></span>

<span data-ttu-id="24177-295">ここで、次の操作を行う **相互作用** スクリプトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24177-295">You will now need to create the **Interactions** script, which is responsible for:</span></span>

-   <span data-ttu-id="24177-296">**タップ** 操作と **カメラを見つめ** て処理します。これにより、ユーザーはシーン内のログイン "ボタン" と対話できます。</span><span class="sxs-lookup"><span data-stu-id="24177-296">Handling the **Tap** interaction and the **Camera Gaze**, which enables the user to interact with the log in "button" in the scene.</span></span>

-   <span data-ttu-id="24177-297">ユーザーが操作を行うためのシーンに "button" オブジェクトのログインを作成します。</span><span class="sxs-lookup"><span data-stu-id="24177-297">Creating the log in "button" object in the scene for the user to interact with.</span></span>

<span data-ttu-id="24177-298">スクリプトを作成するには:</span><span class="sxs-lookup"><span data-stu-id="24177-298">To create the script:</span></span>

1.  <span data-ttu-id="24177-299">[ **Scripts** ] フォルダーをダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="24177-299">Double-click on the **Scripts** folder, to open it.</span></span>

2.  <span data-ttu-id="24177-300">**Scripts** フォルダー内を右クリックし、[ **Create**  >  **C# スクリプト** の作成] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-300">Right-click inside the **Scripts** folder, click **Create** > **C# Script**.</span></span> <span data-ttu-id="24177-301">スクリプトの **操作** に名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="24177-301">Name the script **Interactions**.</span></span>

3.  <span data-ttu-id="24177-302">スクリプトをダブルクリックして、Visual Studio で開きます。</span><span class="sxs-lookup"><span data-stu-id="24177-302">Double-click on the script to open it with Visual Studio.</span></span>

4.  <span data-ttu-id="24177-303">次の名前空間を挿入します。</span><span class="sxs-lookup"><span data-stu-id="24177-303">Insert the following namespaces:</span></span>

    ```csharp
    using UnityEngine;
    using UnityEngine.XR.WSA.Input;
    ```

5.  <span data-ttu-id="24177-304">**相互作用** クラスの継承を、GazeInput *に変更* し **GazeInput** ます。</span><span class="sxs-lookup"><span data-stu-id="24177-304">Change the inheritance of the **Interaction** class from *MonoBehaviour* to **GazeInput**.</span></span>

    <span data-ttu-id="24177-305">~~パブリッククラスの相互作用: モノの動作~~</span><span class="sxs-lookup"><span data-stu-id="24177-305">~~public class Interactions : MonoBehaviour~~</span></span>

    ```csharp
    public class Interactions : GazeInput
    ```

6.  <span data-ttu-id="24177-306">**相互作用** クラス内で、次の変数を挿入します。</span><span class="sxs-lookup"><span data-stu-id="24177-306">Inside the **Interaction** class insert the following variable:</span></span>

    ```csharp
        /// <summary>
        /// Allows input recognition with the HoloLens
        /// </summary>
        private GestureRecognizer _gestureRecognizer;
    ```

7.  <span data-ttu-id="24177-307">**Start** メソッドを置き換えます。これはオーバーライドメソッドであることに注意してください。このメソッドは、"base" を使用して、"このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="24177-307">Replace the **Start** method; notice it is an override method, which calls the 'base' Gaze class method.</span></span> <span data-ttu-id="24177-308">**Start ()** は、クラスが初期化され、入力認識に登録され、シーンに [サインイン *] ボタン* が作成されるときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="24177-308">**Start()** will be called when the class initializes, registering for input recognition and creating the sign in *button* in the scene:</span></span>

    ```csharp    
        /// <summary>
        /// Called on initialization, after Awake
        /// </summary>
        internal override void Start()
        {
            base.Start();

            // Register the application to recognize HoloLens user inputs
            _gestureRecognizer = new GestureRecognizer();
            _gestureRecognizer.SetRecognizableGestures(GestureSettings.Tap);
            _gestureRecognizer.Tapped += GestureRecognizer_Tapped;
            _gestureRecognizer.StartCapturingGestures();

            // Add the Graph script to this object
            gameObject.AddComponent<MeetingsUI>();
            CreateSignInButton();
        }
    ```

8.  <span data-ttu-id="24177-309">次のように、シーンの [サインイン *] ボタン* をインスタンス化し、そのプロパティを設定する、/**ボタン ()** メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="24177-309">Add the **CreateSignInButton()** method, which will instantiate the sign in *button* in the scene and set its properties:</span></span>

    ```csharp    
        /// <summary>
        /// Create the sign in button object in the scene
        /// and sets its properties
        /// </summary>
        void CreateSignInButton()
        {
            GameObject signInButton = GameObject.CreatePrimitive(PrimitiveType.Sphere);

            Material mat = new Material(Shader.Find("Diffuse"));
            signInButton.GetComponent<Renderer>().material = mat;
            mat.color = Color.blue;

            signInButton.transform.position = new Vector3(3.5f, 2f, 9f);
            signInButton.tag = "SignInButton";
            signInButton.AddComponent<Graph>();
        }
    ```

9.  <span data-ttu-id="24177-310">*Tap* ユーザーイベントに対応する **GestureRecognizer_Tapped ()** メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="24177-310">Add the **GestureRecognizer_Tapped()** method, which be respond for the *Tap* user event.</span></span>

    ```csharp   
        /// <summary>
        /// Detects the User Tap Input
        /// </summary>
        private void GestureRecognizer_Tapped(TappedEventArgs obj)
        {
            if(base.FocusedObject != null)
            {
                Debug.Log($"TAP on {base.FocusedObject.name}");
                base.FocusedObject.SendMessage("SignInAsync", SendMessageOptions.RequireReceiver);
            }
        }
    ```

10. <span data-ttu-id="24177-311">**Update ()** メソッドを **削除** してから、Unity に戻る前に Visual Studio に **変更を保存** します。</span><span class="sxs-lookup"><span data-stu-id="24177-311">**Delete** the **Update()** method, and then **save your changes** in Visual Studio before returning to Unity.</span></span>

## <a name="chapter-9---set-up-the-script-references"></a><span data-ttu-id="24177-312">章 9-スクリプト参照の設定</span><span class="sxs-lookup"><span data-stu-id="24177-312">Chapter 9 - Set up the script references</span></span>

<span data-ttu-id="24177-313">この章では、 **対話** スクリプトを **メインカメラ** に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24177-313">In this Chapter you need to place the **Interactions** script onto the **Main Camera**.</span></span> <span data-ttu-id="24177-314">そのスクリプトは、必要な場所にある他のスクリプトの配置を処理します。</span><span class="sxs-lookup"><span data-stu-id="24177-314">That script will then handle placing the other scripts where they need to be.</span></span>

-  <span data-ttu-id="24177-315">次の図に示すように、[*プロジェクト] パネル* の [**スクリプト**] フォルダーで、スクリプトの **対話** を **メインカメラ** オブジェクトにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="24177-315">From the **Scripts** folder in the *Project Panel*, drag the script **Interactions** to the **Main Camera** object, as pictured below.</span></span>

    ![](images/AzureLabs-Lab311-29.png)

## <a name="chapter-10---setting-up-the-tag"></a><span data-ttu-id="24177-316">Chapter 10-タグの設定</span><span class="sxs-lookup"><span data-stu-id="24177-316">Chapter 10 - Setting up the Tag</span></span>

<span data-ttu-id="24177-317">宝石を処理するコードは、タグ **SignInButton** を使用して、ユーザーが *Microsoft Graph* にサインインするために対話するオブジェクトを識別します。</span><span class="sxs-lookup"><span data-stu-id="24177-317">The code handling the gaze will make use of the Tag **SignInButton** to identify which object the user will interact with to sign-in to *Microsoft Graph*.</span></span>

<span data-ttu-id="24177-318">タグを作成するには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="24177-318">To create the Tag:</span></span>

1.  <span data-ttu-id="24177-319">Unity エディターで、[*階層] パネル* の **メインカメラ** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-319">In the Unity Editor click on the **Main Camera** in the *Hierarchy Panel*.</span></span>

2.  <span data-ttu-id="24177-320">[ *インスペクター] パネル* の [ **maincamera** ] *タグ* をクリックして、ドロップダウンリストを開きます。</span><span class="sxs-lookup"><span data-stu-id="24177-320">In the *Inspector Panel* click on the **MainCamera** *Tag* to open a drop-down list.</span></span> <span data-ttu-id="24177-321">[**タグの追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-321">Click on **Add Tag...**</span></span>

    ![](images/AzureLabs-Lab311-30.png)

3.  <span data-ttu-id="24177-322">ボタンをクリックし **+** ます。</span><span class="sxs-lookup"><span data-stu-id="24177-322">Click on the **+** button.</span></span>

    ![](images/AzureLabs-Lab311-31.png)

4.  <span data-ttu-id="24177-323">タグ名を **SignInButton** として書き込み、[保存] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-323">Write the Tag name as **SignInButton** and click Save.</span></span>

    ![](images/AzureLabs-Lab311-32.png)

## <a name="chapter-11---build-the-unity-project-to-uwp"></a><span data-ttu-id="24177-324">第11章-UWP に Unity プロジェクトをビルドする</span><span class="sxs-lookup"><span data-stu-id="24177-324">Chapter 11 - Build the Unity project to UWP</span></span>

<span data-ttu-id="24177-325">このプロジェクトの Unity セクションに必要なものはすべて完了したので、Unity から構築します。</span><span class="sxs-lookup"><span data-stu-id="24177-325">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="24177-326">[ *ビルドの設定* ] (\* [*ファイル* > \* [ビルドの設定] \* \*) に移動します。</span><span class="sxs-lookup"><span data-stu-id="24177-326">Navigate to *Build Settings* (\**File* > \*Build Settings\*\*).</span></span>

    ![](images/AzureLabs-Lab311-33.png)

2.  <span data-ttu-id="24177-327">まだ存在しない場合は、 **Unity C \# プロジェクト** をティックします。</span><span class="sxs-lookup"><span data-stu-id="24177-327">If not already, tick **Unity C\# Projects**.</span></span>

3.  <span data-ttu-id="24177-328">[**ビルド**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-328">Click **Build**.</span></span> <span data-ttu-id="24177-329">Unity は **エクスプローラー** ウィンドウを起動します。このウィンドウでは、アプリを作成するフォルダーを作成して選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24177-329">Unity will launch a **File Explorer** window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="24177-330">ここでそのフォルダーを作成し、「 **App**」という名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="24177-330">Create that folder now, and name it **App**.</span></span> <span data-ttu-id="24177-331">次に、 **アプリ** フォルダーを選択し、[ **フォルダーの選択**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="24177-331">Then with the **App** folder selected, click **Select Folder**.</span></span>

4.  <span data-ttu-id="24177-332">Unity は、 **アプリ** フォルダーへのプロジェクトのビルドを開始します。</span><span class="sxs-lookup"><span data-stu-id="24177-332">Unity will begin building your project to the **App** folder.</span></span>

5.  <span data-ttu-id="24177-333">Unity のビルドが完了すると (時間がかかる場合があります)、ビルドの場所で **ファイルエクスプローラー** ウィンドウを開きます (ウィンドウの上に常に表示されるとは限りませんが、新しいウィンドウが追加されたことが通知されます)。</span><span class="sxs-lookup"><span data-stu-id="24177-333">Once Unity has finished building (it might take some time), it will open a **File Explorer** window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-12---deploy-to-hololens"></a><span data-ttu-id="24177-334">第12章-HoloLens へのデプロイ</span><span class="sxs-lookup"><span data-stu-id="24177-334">Chapter 12 - Deploy to HoloLens</span></span>

<span data-ttu-id="24177-335">HoloLens に展開するには:</span><span class="sxs-lookup"><span data-stu-id="24177-335">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="24177-336">Hololens が **開発者モード** になっていることを確認するには、HOLOLENS の IP アドレス (リモートデプロイ用) が必要です。</span><span class="sxs-lookup"><span data-stu-id="24177-336">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode.**</span></span> <span data-ttu-id="24177-337">この操作を行うには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="24177-337">To do this:</span></span>

    1.  <span data-ttu-id="24177-338">HoloLens を装着した後、 **設定** を開きます。</span><span class="sxs-lookup"><span data-stu-id="24177-338">Whilst wearing your HoloLens, open the **Settings**.</span></span>

    2.  <span data-ttu-id="24177-339">[**ネットワーク & インターネット**  >  **wi-fi**  >  **詳細オプション]** にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="24177-339">Go to **Network & Internet** > **Wi-Fi** > **Advanced Options**</span></span>

    3.  <span data-ttu-id="24177-340">**IPv4** アドレスをメモしておきます。</span><span class="sxs-lookup"><span data-stu-id="24177-340">Note the **IPv4** address.</span></span>

    4.  <span data-ttu-id="24177-341">次に、[**設定**] に戻り、 **Update & Security**  >  **開発者の**& セキュリティを更新します。</span><span class="sxs-lookup"><span data-stu-id="24177-341">Next, navigate back to **Settings**, and then to **Update & Security** > **For Developers**</span></span>

    5.  <span data-ttu-id="24177-342">**開発者モードをに** 設定します。</span><span class="sxs-lookup"><span data-stu-id="24177-342">Set **Developer Mode On**.</span></span>

2.  <span data-ttu-id="24177-343">新しい Unity ビルド ( **アプリ** フォルダー) に移動し、 **Visual Studio** でソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="24177-343">Navigate to your new Unity build (the **App** folder) and open the solution file with **Visual Studio**.</span></span>

3.  <span data-ttu-id="24177-344">**ソリューション構成** で、[**デバッグ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="24177-344">In the **Solution Configuration** select **Debug**.</span></span>

4.  <span data-ttu-id="24177-345">**ソリューションプラットフォーム** で、[ **X86、リモートコンピューター**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="24177-345">In the **Solution Platform**, select **x86, Remote Machine**.</span></span> <span data-ttu-id="24177-346">リモートデバイスの **IP アドレス** (この場合は、ここでメモした HoloLens) を挿入するように求められます。</span><span class="sxs-lookup"><span data-stu-id="24177-346">You will be prompted to insert the **IP address** of a remote device (the HoloLens, in this case, which you noted).</span></span>

    ![](images/AzureLabs-Lab311-34.png)

5.  <span data-ttu-id="24177-347">[ **ビルド** ] メニューの [ **ソリューションの配置** ] をクリックして、アプリケーションを HoloLens にサイドロードします。</span><span class="sxs-lookup"><span data-stu-id="24177-347">Go to **Build** menu and click on **Deploy Solution** to sideload the application to your HoloLens.</span></span>

6.  <span data-ttu-id="24177-348">アプリが HoloLens にインストールされているアプリの一覧に表示され、起動できる状態になります。</span><span class="sxs-lookup"><span data-stu-id="24177-348">Your app should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

## <a name="your-microsoft-graph-hololens-application"></a><span data-ttu-id="24177-349">Microsoft Graph HoloLens アプリケーション</span><span class="sxs-lookup"><span data-stu-id="24177-349">Your Microsoft Graph HoloLens application</span></span>

<span data-ttu-id="24177-350">これで、Microsoft Graph を利用してユーザーカレンダーデータを読み取り、表示する mixed reality アプリが作成されました。</span><span class="sxs-lookup"><span data-stu-id="24177-350">Congratulations, you built a mixed reality app that leverages the Microsoft Graph, to read and display user Calendar data.</span></span>

![](images/AzureLabs-Lab311-00.png)

## <a name="bonus-exercises"></a><span data-ttu-id="24177-351">ボーナス演習</span><span class="sxs-lookup"><span data-stu-id="24177-351">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="24177-352">演習1</span><span class="sxs-lookup"><span data-stu-id="24177-352">Exercise 1</span></span>

<span data-ttu-id="24177-353">Microsoft Graph を使用して、ユーザーに関するその他の情報を表示する</span><span class="sxs-lookup"><span data-stu-id="24177-353">Use Microsoft Graph to display other information about the user</span></span>

-   <span data-ttu-id="24177-354">ユーザーの電子メール/電話番号/プロファイルの画像</span><span class="sxs-lookup"><span data-stu-id="24177-354">User email / phone number / profile picture</span></span>

### <a name="exercise-1"></a><span data-ttu-id="24177-355">演習1</span><span class="sxs-lookup"><span data-stu-id="24177-355">Exercise 1</span></span>

<span data-ttu-id="24177-356">音声制御を実装して、Microsoft Graph UI に移動します。</span><span class="sxs-lookup"><span data-stu-id="24177-356">Implement voice control to navigate the Microsoft Graph UI.</span></span>
